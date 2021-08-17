---
title: 1장 - Azure RTOS NetX DHCP 클라이언트 소개
description: NetX에서 애플리케이션의 IP 주소는 nx_ip_create 서비스 호출에 제공된 매개 변수 중 하나입니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 54853fd3677b8d60b7fbe1445ca67c7e7a4a6e832683f65cbfca86158cb7fbd3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788814"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-dhcp-client"></a>1장 - Azure RTOS NetX DHCP 클라이언트 소개

NetX에서 애플리케이션의 IP 주소는 *nx_ip_create* 서비스 호출에 제공된 매개 변수 중 하나입니다. IP 주소를 정적 또는 사용자 구성을 통해 애플리케이션에 알려진 경우 IP 주소를 제공해도 문제가 발생하지 않습니다. 그러나 애플리케이션이 해당 IP 주소를 인식하지 못하거나 담당하지 않는 경우가 있습니다. 이러한 경우 *nx_ip_create* 함수에 제로 IP 주소를 제공해야 하고 Azure RTOS DHCP 클라이언트 프로토콜을 사용하여 IP 주소를 동적으로 가져와야 합니다.

## <a name="dynamic-ip-address-assignment"></a>동적 IP 주소 할당

네트워크에서 동적 IP 주소를 가져오는 데 사용되는 기본 서비스는 RARP(역방향 주소 확인 프로토콜)입니다. 이 프로토콜은 다른 네트워크 노드의 MAC 주소를 찾는 대신 자체 IP 주소를 가져오도록 설계되었다는 점을 제외하면, ARP와 유사합니다. 하위 수준 RARP 메시지는 로컬 네트워크에서 브로드캐스트되며 동적으로 할당된 IP 주소를 포함하는 RARP 응답으로 응답하는 것은 네트워크 상의 서버가 담당합니다.

RARP는 IP 주소를 동적으로 할당하는 서비스를 제공하지만, 몇 가지 단점이 있습니다. 가장 두드러진 결점은 RARP가 IP 주소의 동적 할당만 제공한다는 것입니다. 대부분의 경우 디바이스가 네트워크에 제대로 참여하려면 추가 정보가 필요합니다. 대부분의 디바이스에는 IP 주소 외에도 네트워크 마스크와 게이트웨이 IP 주소가 필요합니다. DNS 서버의 IP 주소 및 기타 네트워크 정보도 필요할 수 있습니다. RARP에는 이 정보를 제공하는 기능이 없습니다.

## <a name="rarp-alternatives"></a>RARP 대안

연구원들은 RARP의 결함을 극복하기 위해 BOOTP(부트 스트랩 프로토콜)라고 하는 더 포괄적인 IP 주소 할당 메커니즘을 개발했습니다. 이 프로토콜에는 IP 주소를 동적으로 할당하고 중요한 추가 네트워크 정보도 제공하는 기능이 있습니다. 그러나 BOOTP는 정적 네트워크 구성을 위해 설계된다는 단점이 있습니다. 빠른 주소 할당 또는 자동 주소 할당을 허용하지 않습니다.

여기서 DHCP(Dynamic Host Configuration Protocol)가 매우 유용합니다. DHCP는 지정된 기간 동안 클라이언트에 IP 주소를 “임대”하여 완전히 자동화된 IP 서버 할당과 완전한 동적 IP 주소 할당을 포함하도록 BOOTP의 기본 기능을 확장하도록 설계되었습니다. DHCP는 BOOTP와 같은 정적 방식으로 IP 주소를 할당하도록 구성할 수도 있습니다.

## <a name="dhcp-messages"></a>DHCP 메시지

DHCP는 BOOTP의 기능을 크게 향상시키지만, DHCP는 BOOTP와 동일한 메시지 형식을 사용하며 BOOTP와 동일한 공급 업체 옵션을 지원합니다. DHCP는 해당 기능을 수행하기 위해 다음과 같은 7개의 새로운 DHCP 관련 옵션을 도입했습니다.

- DISCOVER(1) (DHCP 클라이언트에서 보냄)

- OFFER(2) (DHCP 서버에서 보냄)

- REQUEST(3) (DHCP 클라이언트에서 보냄)

- DECLINE(4) (DHCP 클라이언트에서 보냄)

- ACK(5) (DHCP 서버에서 보냄)

- NACK(6) (DHCP 서버에서 보냄)

- RELEASE(7) (DHCP 클라이언트에서 보냄)

- INFORM(8) (DHCP 클라이언트에서 보냄)

- FORCERENEW(9) (DHCP 클라이언트에서 보냄)

## <a name="dhcp-communication"></a>DHCP 통신

DHCP는 UDP 프로토콜을 활용하여 요청 및 필드 응답을 보냅니다. IP 주소를 유지하기 전에 DHCP 정보를 전달하는 UDP 메시지는 255.255.255.255의 IP 브로드캐스트 주소를 활용하여 송수신됩니다.

## <a name="dhcp-client-state-machine"></a>DHCP 클라이언트 상태 시스템

DHCP 클라이언트는 상태 시스템으로 구현됩니다. 상태 시스템은 *nx_dhcp_create* 를 처리하는 동안 생성된 내부 DHCP 스레드에 의해 처리됩니다. DHCP 클라이언트의 주요 상태는 다음과 같습니다.


- **NX_DHCP_STATE_BOOT** 이전 IP 주소로 시작

- **NX_DHCP_STATE_INIT** 이전 IP 주소 값 없이 시작

- **NX_DHCP_STATE_SELECTING** DHCP 서버의 응답을 기다리는 중

- **NX_DHCP_STATE_REQUESTING** DHCP 서버가 식별됨, IP 주소 요청 전송됨

- **NX_DHCP_STATE_BOUND** DHCP IP 주소 임대가 설정됨

- **NX_DHCP_STATE_RENEWING** DHCP IP 주소 임대 갱신 시간이 경과됨, 갱신이 요청됨

- **NX_DHCP_STATE_REBINDING** DHCP IP 주소 임대 리바인딩 시간이 경과됨, 갱신이 요청됨

- **NX_DHCP_STATE_FORCERENEW** DHCP IP 주소 임대가 설정됨, 서버(현재 지원되지 않음) 또는 nx_dhcp_force_renew를 호출하는 애플리케이션에 의해 강제 갱신됨

- **NX_DHCP_STATE_ADDRESS_PROBING** DHCP IP 주소 검색, ARP 프로브를 보내 IP 주소 충돌을 감지합니다.

## <a name="dhcp-client-multiple-interface-support"></a>DHCP 클라이언트 다중 인터페이스 지원

DHCP 클라이언트는 이전에 단일 네트워크 인터페이스에서만 실행되도록 구현되었습니다. 기본 동작은 DHCP 클라이언트를 기본 인터페이스에서 실행하기 위한 것입니다. 애플리케이션은 *nx_dhcp_set_interface_index* 를 호출하여 기본 인터페이스 대신 보조 네트워크 인터페이스에서 DHCP를 실행할 수 있습니다.

이제 여러 인터페이스에서 병렬로 실행되는 DHCP를 지원합니다. 둘 이상의 물리적 인터페이스에서 DHCP 클라이언트를 동시에 실행하는 방법에 대한 자세한 내용은 2장의 **동시에 여러 인터페이스의 DHCP 클라이언트** 를 참조하세요.

## <a name="dhcp-user-request"></a>DHCP 사용자 요청

DHCP 서버에서 IP 주소를 부여하면 *nx_dhcp_user_option_request* 서비스를 사용하여 DHCP 클라이언트 처리에서 한 번에 하나씩 추가 매개 변수를 요청할 수 있습니다.

## <a name="dhcp-client-socket-queue"></a>DHCP 클라이언트 소켓 큐 

DHCP 클라이언트는 서버가 자체 응답을 기다리는 동안 소켓 수신 큐에서 다른 DHCP 클라이언트용으로 지정된 DHCP 서버에서 브로드캐스트 패킷을 자동으로 지웁니다. 사용 중인 네트워크에서 이 작업을 수행하지 않으면 클라이언트용 패킷이 삭제될 수 있습니다.

## <a name="dhcp-rfcs"></a>DHCP RFC

NetX DHCP는 RFC2132, RFC2131 및 관련 RFC와 호환됩니다.

