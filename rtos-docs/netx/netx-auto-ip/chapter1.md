---
title: 1장 - Azure RTOS NetX AutoIP 소개
description: Azure RTOS NetX AutoIP 프로토콜은 로컬 네트워크에서 IPv4 주소를 동적으로 구성하기 위해 설계된 프로토콜입니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd41a50a8591426b4c32cf2105132d92bbe487d9f91860d05c65f1a65e6d1d1c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797010"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-autoip"></a>1장 - Azure RTOS NetX AutoIP 소개
  
Azure RTOS NetX AutoIP 프로토콜은 로컬 네트워크에서 IPv4 주소를 동적으로 구성하기 위해 설계된 프로토콜입니다. AutoIP는 ARP 기능을 활용하여 자동 IP 주소 할당 기능을 수행하는 간단한 프로토콜입니다. AutoIP는 169.254.1.0 ~ 169.254.254.255 범위의 주소를 할당합니다.

## <a name="autoip-requirements"></a>AutoIP 요구 사항

NetX AutoIP 패키지를 제대로 작동하려면 NetX IP 인스턴스가 이미 생성되어 있어야 합니다. 또한 동일한 IP 인스턴스에서 ARP를 사용하도록 설정해야 합니다. NetX AutoIP 패키지에는 추가 요구 사항이 없습니다.

## <a name="autoip-constraints"></a>AutoIP 제약 조건 

NetX AutoIP 프로토콜은 RFC3927 표준의 요구 사항을 구현합니다. 그러나 다음과 같은 제약 조건이 있습니다.

1. NetX DHCP를 사용하는 경우 NetX IP 인스턴스 스레드와 AutoIP 스레드보다 우선 순위가 높은 DHCP 스레드를 만들어야 합니다.
1. NetX AutoIP는 기존 IP 주소를 계속 사용할 수 있는 메커니즘을 제공하지 않습니다.
1. IP 주소가 변경되면 애플리케이션은 기존 TCP 연결을 해제하고 새 IP 주소에 다시 설정해야 합니다.

## <a name="autoip-protocol-implementation"></a>AutoIP 프로토콜 구현

NetX AutoIP 프로토콜은 먼저 169.254.1.0 ~ 169.254.254.255의 AutoIP IPv4 주소 범위 내에서 임의 주소를 선택합니다. 또는 애플리케이션에서 ***nx_auto_ip_start*** 함수에 제공하여 시작 IP 주소를 강제로 적용할 수 있습니다. 이는 AutoIP 주소가 이전 실행에서 성공적으로 사용된 경우에 유용합니다.

AutoIP 주소가 선택되면 NetX AutoIP는 선택한 주소에 대해 일련의 ARP 프로브를 보냅니다. ARP 프로브는 보낸 사람 주소가 0.0.0.0으로 설정되고 대상 주소가 원하는 AutoIP 주소로 설정된 ARP 요청 메시지로 구성됩니다. 이러한 일련의 ARP 프로브가 전송됩니다(실제 숫자는 정의된 NX_AUTO_IP_PROBE_NUM에 의해 결정됨). 다른 네트워크 노드가 이 프로브에 응답하거나 동일한 주소에 대해 동일한 프로브를 보내면 AutoIP IPv4 주소 범위 내에서 새 AutoIP 주소가 임의로 선택되고 프로브 처리가 반복됩니다.

NX_AUTO_IP_PROBE_NUM 프로브가 응답 없이 전송되면 NetX AutoIP는 선택한 주소에 대해 일련의 ARP 알림을 발급합니다. ARP 알림은 AutoIP 주소로 설정된 ARP 메시지의 보낸 사람 및 대상 주소가 모두 포함된 ARP 요청 메시지로 구성됩니다. NX_AUTO_IP_ANNOUNCE_NUM 정의에 해당하는 일련의 ARP 알림 메시지가 전송됩니다. 다른 네트워크 노드가 알림 메시지에 응답하거나 동일한 주소에 대해 동일한 알림을 보내는 경우 AutoIP IPv4 주소 범위 내에서 새 AutoIP 주소가 임의로 선택되고 프로브 처리가 시작됩니다.

검색된 충돌 없이 프로브 및 알림이 완료되면 선택한 AutoIP 주소가 유효한 것으로 간주되고 연결된 IP 인스턴스는 이 주소로 설정됩니다.

## <a name="autoip-address-change"></a>AutoIP 주소 변경

앞서 언급했듯이 NetX AutoIP는 프로브 및 알림 처리가 성공한 후 IP 인스턴스 주소를 변경합니다. 이 경우 모니터링은 그다지 중요하지 않습니다. 그러나 나중에 AutoIP 주소를 변경할 수 있습니다. 잠재적인 원인에는 DHCP 주소 확인뿐만 아니라 향후 AutoIP 주소 충돌이 포함됩니다. 이러한 잠재적 상황을 적절히 처리하기 위해 애플리케이션은 다음 NetX API를 사용하여 모든 IP 주소 변경을 경고해야 합니다.

```c
nx_ip_address_change_notify(NX_IP *ip_ptr,
                            VOID (*ip_address_change_notify)(NX_IP *,VOID*),
                            VOID *additional_info);
```

제공된 *ip_address_change_notify* 함수의 처리는 NetX AutoIP 프로세서를 다시 시작하거나 DHCP가 나중에 IP 주소를 확인한 경우 비활성화해야 합니다. 샘플 처리는 *간단한 예제 시스템* 섹션을 참조하세요.

## <a name="autoip-rfcs"></a>AutoIP RFC

NetX AutoIP는 RFC3927 및 관련 RFC와 호환됩니다.