---
title: 1장 - NAT(Network Address Translation) 소개
description: IP NAT(Network Address Translation)는 원래 제한된 수의 인터넷 IPv4 주소 문제를 해결하기 위해 개발되었습니다.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3d01aa6f68e21ea82f65a59a19c4f5c7958a6b92
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810686"
---
# <a name="chapter-1---an-introduction-to-network-address-translation"></a>1장 - NAT(Network Address Translation) 소개

## <a name="the-need-for-network-address-translation"></a>NAT(Network Address Translation)의 필요성

IP NAT(Network Address Translation)는 원래 제한된 수의 인터넷 IPv4 주소 문제를 해결하기 위해 개발되었습니다. 여러 디바이스에서 인터넷에 액세스해야 하지만 하나의 IPv4 인터넷 주소만 ISP(인터넷 서비스 공급자)에 의해 할당되는 경우 NAT가 필요합니다.

또한 NAT를 사용할 경우 다른 이점도 있습니다. 로컬 도메인 외부의 네트워크 토폴로지는 다양한 방식으로 변경될 수 있습니다. 고객이 공급자를 변경하거나, 회사 백본이 재구성되거나, 공급자가 합병 또는 분할될 수 있습니다. 외부 토폴로지가 변경될 때마다 로컬 도메인 내의 호스트에 대한 주소 할당도 이러한 외부 변경 내용을 반영하도록 변경해야 합니다. 단일 주소 변환 라우터의 변경 내용을 중앙 집중식으로 관리하여 도메인 내의 사용자에게 이 유형의 변경 내용을 숨길 수 있습니다. NAT는 로컬 호스트가 공용 인터넷에 액세스할 수 있게 하고 외부에서는 직접 액세스할 수 없도록 보호합니다. 네트워크를 주로 내부용으로 사용하는 조직에서는 이 체계를 사용하는 경우에도 가끔 외부 액세스가 필요합니다.

## <a name="basic-nat-and-network-address-port-translation"></a>기본 NAT 및 네트워크 주소 포트 변환

NAT 지원 라우터는 공용 네트워크와 개인 네트워크 사이에 설치됩니다. NAT 지원 라우터의 역할은 내부 비공개 IPv4 주소와 할당된 공용 IPv4 주소 간에 변환하는 것이므로 개인 네트워크의 모든 디바이스는 동일한 공용 IPv4 주소를 공유할 수 있습니다.

NAT의 기본 구현에서 NAT 라우터는 자체 IP 주소와 다른 전역적으로 등록된 IP 주소를 하나 이상 ‘소유’합니다. 이러한 전역 주소는 고정적으로 또는 동적으로 개인 네트워크의 호스트에 할당할 수 있습니다. NAPT 또는 네트워크 주소 포트 변환은 기본 NAT의 변형입니다. 여기에서 NAT(Network Address Translation)는 'transport' 식별자를 포함하도록 확장됩니다. 일반적으로 TCP 및 UDP 패킷에 대한 포트 번호와 ICMP 패킷에 대한 쿼리 ID가 여기에 해당합니다.

NAT 경계에 걸친 연결은 일반적으로 외부 호스트로 아웃바운드 패킷을 보내는 개인 네트워크의 호스트에 의해 시작됩니다. 이러한 호스트는 일반적으로 이 용도로 *동적*(임시) IP 주소를 할당합니다. 그러나 개인 네트워크에 외부 네트워크의 클라이언트 요청을 수락하는 '서버'(예: HTTP 또는 FTP 서버)가 있는 경우에는 연결이 반대 방향으로 시작될 수도 있습니다. 일반적으로 NAT는 이러한 로컬 호스트에 *고정*(영구) IP address:port를 할당합니다.

## <a name="how-network-address-translation-works"></a>NAT(Network Address Translation)의 작동 방식

일반적으로 NAT 지원 라우터를 사용하는 네트워크 설정은 그림 1에 나와 있습니다.

![NAT 지원 라우터를 사용하는 일반적인 네트워크 설정](media/image2.png)

**그림 1 - NAT 지원 라우터를 사용하는 일반적인 네트워크 설정**

일반적으로 NAT 지원 라우터에는 두 개의 네트워크 인터페이스가 있습니다. 한 인터페이스는 공용 인터넷에 연결되고 다른 인터페이스는 개인 네트워크에 연결됩니다. 이 설치 프로그램의 일반적인 라우터는 대상 IP 주소를 기반으로 하는 공용 네트워크와 개인 네트워크 간에 IP 데이터그램을 라우팅하는 역할을 합니다. NAT 지원 라우터는 공용 인터페이스와 개인 인터페이스 간에 IPv4 데이터그램을 라우팅하기 전에 주소 변환을 수행합니다. 내부 원본 주소, 원본 포트 번호, 외부 대상 주소, 대상 포트 번호를 기반으로 각 TCP 또는 UDP 세션에 대해 변환이 설정됩니다. ICMP 에코 요청 및 응답 데이터그램의 경우 포트 번호 대신 ICMP 쿼리 ID가 사용됩니다.

NAT(Network Address Translation)의 일반적인 구현을 보여 주기 위해 그림 2의 네트워크 설정을 살펴보겠습니다.

![NAT(Network Address Translation)의 일반적인 구현](media/image3.png)

**그림 2 - NAT(Network Address Translation)의 일반적인 구현**

이 시나리오에서 NAT 라우터는 개인 네트워크를 왼쪽에 연결하고 공용 네트워크는 오른쪽에 연결합니다. 공용 네트워크 쪽의 NAT 라우터 인터페이스 IP 주소를 202.151.25.14라고 가정하겠습니다. 개인 네트워크 인터페이스에서 NAT 라우터는 IP 주소 192.168.1.254를 사용합니다. 개인 네트워크의 노드는 인터넷에서 웹 서버와의 TCP 연결을 시작합니다.

그림 3에서는 NAT(Network Address Translation) 프로세스에 대한 개략적인 보기를 보여 줍니다.

![NAT(Network Address Translation) 프로세스의 개략적인 보기](media/image4.png)

**그림 3 - NAT(Network Address Translation) 프로세스의 개략적인 보기**

1. 클라이언트에서 TCP SYN 메시지를 웹 서버로 보냅니다. 발신자 주소는 192.168.1.15이고 포트 번호는 6732입니다. 대상 주소는 128.15.54.3이고 포트 번호는 80입니다.
1. 클라이언트의 패킷은 NAT 라우터에 의해 개인 네트워크 인터페이스에서 수신됩니다. 아웃바운드 트래픽 규칙이 패킷에 적용됩니다. 즉, 발신자(클라이언트)의 주소는 NAT 라우터의 공용 IP 주소 202.15.25.14로 변환되고 발신자(클라이언트) 원본 포트 번호는 공용 인터페이스의 TCP 포트 번호 2015로 변환됩니다.
1. 그러면 패킷이 인터넷을 통해 전송되고 궁극적으로 대상 호스트인 128.15.54.3에 도달합니다. 수신 쪽에서는 IP 계층 원본 주소와 TCP 계층 포트 번호를 기반으로, 패킷이 202.151.24.14, 포트 번호 2015에서 시작된 것으로 나타납니다.
   그림 4에서는 반환 경로에 대한 NAT 프로세스를 보여 줍니다.

   ![반환 경로에 대한 NAT 프로세스](media/image5.png)

   **그림 4 - 반환 경로에 대한 NAT 프로세스**
1. 이 시나리오에서 인터넷 호스트 128.15.54.3은 NAT 라우터의 인터넷 주소를 대상으로 하는 응답 패킷을 보냅니다.
1. 패킷이 NAT 라우터에 도달합니다. 이는 인바운드 패킷이므로 바인딩된 변환 규칙이 적용됩니다. 대상 주소가 원래 발신자(클라이언트)의 IP 주소(192.168.1.15, 대상 포트 번호 6732)로 다시 변경됩니다.
1. 그러면 패킷이 내부 네트워크에 연결된 인터페이스를 통해 클라이언트에 전달됩니다.

이러한 방식으로 인터넷 네트워크 주소와 발신자의 포트 번호는 공용 인터넷의 다른 호스트에 노출되지 않습니다.

## <a name="netx-duo-nat-features"></a>NetX Duo NAT 기능

*Nx_nat_create* 호출을 사용하여 NAT 인스턴스를 만들면 NAT 변환 테이블이 생성됩니다.

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

로컬 네트워크와 외부 네트워크 간의 모든 활성 연결에 대한 NAT(Network Address Translation)를 추적하기 위해 NetX Duo NAT 지원 라우터는 변환 테이블을 유지 관리하며, 이 테이블에는 원본 및 대상 IP 주소와 포트 번호를 포함하는 각 비공개 호스트 연결에 대한 정보가 들어 있습니다.

이 변환 테이블("cache")의 위치는 dynamic_cache_memory 포인터를 사용하여 설정됩니다. 이 영역은 4바이트의 정렬된 버퍼 공간이어야 합니다. 테이블 크기(또는 항목 수)는 캐시 크기인 dynamic_cache_size를 NAT 테이블 항목으로 나눠서 결정됩니다. 테이블은 ***nx_nat.h* 에 정의된 NX_NAT_MIN_ENTRY_COUNT로 지정된 항목의 최소 수만큼 충분히 커야 합니다. 기본값은 3입니다.**

NetX Duo NAT 변환 테이블의 모든 동적 항목에 대한 시간 제한은 *nx_nat. h* 에 정의된 NX_NAT_ENTRY_RESPONSE_TIMEOUT으로 초기화됩니다. RFC 2663에서 권장하는 대로 기본값은 4분(또는 100mHz 프로세서의 경우 240 시스템 틱)입니다. NetX Duo NAT는 테이블의 동적 항목과 일치하는 패킷을 받거나 보낼 때마다 해당 항목의 시간 제한이 NX_NAT_ENTRY_RESPONSE_TIMEOUT으로 다시 설정됩니다. 테이블을 검색할 때 NetX Duo NAT는 테이블에서 만료된 항목을 확인하고 삭제합니다.

테이블에서 인바운드 항목을 고정 항목으로 만들기 위해(예: 로컬 네트워크의 서버에 대해) NetX Duo NAT는 *nx_nat_inbound_entry_create* 서비스를 제공합니다. 테이블 항목에서 로컬 호스트 연결을 고정으로 정의하는 경우에는 만료되지 않습니다.

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr,
    ULONG local_ip_address, USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

이 서비스는 [4장 - 서비스 설명](chapter4.md)에 자세히 설명되어 있습니다.

런타임 중에 변환 테이블이 가득 차서 더 이상 항목을 추가할 수 없는 경우 NetX Duo NAT는 항목이 NAT 인스턴스에 등록될 때 NAT 애플리케이션에 캐시 가득 참 콜백을 알립니다. 이는 *nx_nat_cache_notify_set* 서비스를 사용하여 수행됩니다.

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)(NX_NAT_DEVICE *nat_ptr));
```

이 서비스에 대한 자세한 내용은 [4장 - 서비스 설명](chapter4.md)을 참조하세요.

## <a name="nat-packet-processing-in-netx-duo"></a>NetX Duo의 NAT 패킷 처리

NetX Duo NAT는 IPv4 라우터에서 사용하기 위한 것입니다. NAT가 작동하려면 NAT 서버에 패킷을 전달하도록 NetX Duo를 구성해야 합니다. 이 작업을 수행하는 방법은 NetX Duo NAT 설치의 2장을 참조하세요. 그런 다음, NAT 서버는 네트워크의 호스트에 대해 패킷을 '사용'(전달 시도)하는지 여부를 나타냅니다. 패킷을 사용하지 않을 경우 패킷은 일반적으로 패킷을 처리하는 NetX Duo에 '반환'됩니다.

NAT 서버가 NetX Duo에서 전달되는 패킷을 받으면 패킷이 인바운드인지 또는 아웃바운드인지를 확인합니다.

아웃바운드 패킷의 경우 NAT 서버는 패킷 IP 헤더 원본 주소와 포트를 확인합니다. 이전에 이 호스트에서 동일한 대상에 대해 보낸 패킷의 항목이 변환 테이블에 포함되지 않은 경우 NAT는 고유한 전역 원본 IP 주소를 포함하는 새 항목(연결에 대한 포트)을 만들고 이 새 IP address:port를 사용하여 패킷 헤더를 외부 네트워크에 전송하기 전에 수정합니다.

인바운드 패킷의 경우 NAT 서버는 패킷 대상 IP address:port와 일치하는 외부 IP address:port를 사용하여 변환 테이블에서 이전 항목을 찾습니다. 일치하는 항목이 없는 경우 대상 address:port가 로컬 네트워크의 서버에 대한 외부 주소인 경우를 제외하고는 패킷을 삭제합니다. 일치하는 항목을 찾으면 패킷 헤더의 외부 대상 IP address:port를 개인 IP address:port로 바꾸고 패킷을 로컬 네트워크를 통해 의도된 비공개 호스트로 보냅니다.

NetX Duo NAT는 외부 호스트와 연결되는 로컬 호스트를 위해 고유한 로컬 address:port 연결을 만드는 데 다양한 TCP, UDP 및 ICMP 변환 포트를 사용합니다. *nx_nat.h* 에 정의된 다음과 같은 사용자 구성 가능한 옵션이 각 프로토콜에 대한 범위를 정의합니다.

```C
NX_NAT_START_TCP_PORT

NX_NAT_END_TCP_PORT

NX_NAT_START_UDP_PORT

NX_NAT_END_UDP_PORT

NX_NAT_START_ICMP_QUERY_ID

NX_NAT_END_ICMP_QUERY_ID
```

## <a name="nat-requirements-and-constraints"></a>NAT 요구 사항 및 제약 조건

NetX Duo NAT에는 NetX Duo 5.8 이상이 필요합니다. NAT 애플리케이션을 사용하려면 단일 IP 인스턴스와 내부 및 외부 실제 네트워크에 대한 인터페이스를 만들어야 합니다.

제약 조건:

- NetX Duo NAT는 TCP, UDP 및 ICMP를 지원합니다. IGMP는 지원되지 않습니다.
- NetX Duo NAT는 IPv6 주소 지정을 지원하지 않습니다.
- NetX Duo NAT는 DNS 또는 DHCP 서비스를 포함하지 않습니다. 단, NetX Duo NAT가 해당 서비스를 NAT 작업과 통합할 수는 있습니다.

## <a name="rfcs-supported-by-netx-duo-nat"></a>NetX Duo NAT에서 지원되는 RFC

NetX Duo NAT 구현은 다음 RFC에 제공된 정보를 기반으로 합니다.

- RFC 2663: IP NAT(Network Address Translator) 용어 및 고려 사항
- RFC 3022: 기존 IP NAT(Network Address Translation)
- RFC 4787: 유니캐스트 UDP의 NAT(Network Address Translation) 동작 요구 사항
