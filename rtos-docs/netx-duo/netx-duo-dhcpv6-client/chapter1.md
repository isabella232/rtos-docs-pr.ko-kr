---
title: 챕터 1 - Azure RTOS NetX Duo DHCPv6 클라이언트 소개
description: IPv6 네트워크에서 DHCPv6는 DHCP 대신 DHCPv6 서버에서 동적 글로벌 IP 주소를 할당받고, 대부분의 동일한 기능과 여러 향상 기능을 제공합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f938be404c121f3080cfed1a81aa356f698538c4f557387009d951df40496a6d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791315"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-client"></a>챕터 1 - Azure RTOS NetX Duo DHCPv6 클라이언트 소개

IPv6 네트워크에서 DHCPv6는 DHCP 대신 DHCPv6 서버에서 동적 글로벌 IP 주소를 할당받고, 대부분의 동일한 기능과 여러 향상 기능을 제공합니다. 이 문서에서는 Azure RTOS NetX Duo DHCPv6 클라이언트 API를 사용하여 IPv6 주소를 얻는 방법에 대해 자세히 설명합니다.

## <a name="dhcpv6-communication"></a>DHCPv6 통신

DHCPv6 프로토콜은 UDP를 사용합니다. 클라이언트는 546 포트를 사용하고, 서버는 547 포트를 사용하여 DHCPv6 메시지를 교환합니다. 클라이언트는 원본 주소에 대한 링크 로컬 주소를 사용하여 사용 가능한 DHCPv6 서버에 대한 DHCPv6 요청을 시작합니다. 클라이언트는 네트워크의 모든 DHCPv6 서버에 메시지를 보낼 때 *All_DHCP_Relay_Agents_and_Servers* 멀티 캐스트 주소 *FF02::01:02* 를 사용합니다. 이는 예약된 링크 범위의 멀티 캐스트 주소입니다.

## <a name="dhcpv6-process-of-requesting-an-ipv6-address"></a>DHCPv6의 IPv6 주소 요청 프로세스

클라이언트는 글로벌 IPv6 주소 할당을 요청하는 프로세스를 시작하기 위해 먼저 *nx_dhcpv6_send_solicit* 서비스를 사용하여 SOLICIT 메시지를 보냅니다.

**UINT nx_dhcpv6_request_solicit(NX_DHCPV6 \*dhcpv6_ptr)**

이 메시지는 *All_DHCP_Relay_Agents_and_Servers* 주소를 사용하여 모든 서버에 전송됩니다. SOLICIT 요청에서 클라이언트는 서버에 대한 힌트로 특정 IPv6 주소 할당을 요청할 수 있습니다. 또한 SOLICIT 메시지의 옵션 요청에서 DNS 서버, NTP 서버 및 기타 옵션과 같은 서버의 다른 네트워크 구성 정보를 요청할 수 있습니다.

클라이언트 요청을 처리할 수 있는 DHCPv6 서버는 클라이언트에 할당할 수 있는 IPv6 주소, IPv6 주소 임대 시간 및 클라이언트가 요청한 추가 정보가 포함된 ADVERTISE 메시지를 사용하여 응답합니다. DHCPv6 클라이언트 프로토콜은 클라이언트가 네트워크의 모든 DHCPv6 서버에서 ADVERTISE 메시지를 받을 때까지 일정 시간을 기다릴 것을 요구합니다. 각 ADVERTISE 메시지를 유효한 메시지로 미리 처리하고, 다양한 DHCPv6 매개 변수의 옵션 데이터를 검색합니다. 또한 서버에서 제공하는 경우 기본 설정 옵션의 기본 설정 값을 확인합니다. 둘 이상의 ADVERTISE 메시지가 수신될 경우 NetX DHCPv6 클라이언트가 대기 기간이 끝날 때 수신된 기본 설정 값이 가장 높은 서버를 선택합니다.

클라이언트에서 기본 설정 값이 255인 ADVERTISE 메시지를 수신하는 경우는 예외입니다. 클라이언트는 이 메시지를 즉시 수락하고 모든 후속 ADVERTISE 메시지를 무시합니다.

대기 기간은 DHCPv6 클라이언트가 서버에서 응답을 받지 못한 경우 다른 SOLICIT 메시지를 보내기 전에 대기하는 재전송 기간으로 정의됩니다. SOLICIT 상태에서 초기 재전송 시간 제한은 RFC 3315에 설명된 DHCPv6 프로토콜에서 1초로 정의합니다. 이후 재전송 간격은 DHCPv6 클라이언트가 유효한 서버 응답을 받지 못할 경우 최대 120초까지 증가합니다.

서버를 선택하면 클라이언트가 ADVERTISE 메시지에서 데이터를 추출한 후 다시 서버로 REQUEST 메시지를 보내 할당된 주소 정보와 임대 시간을 수락합니다. 서버에서 REPLY 메시지를 사용하여 클라이언트에 할당된 클라이언트 IPv6 주소가 서버에 등록되었음을 확인하는 응답을 보냅니다.

DHCPv6 클라이언트가 할당된 IPv6 주소를 IP 인스턴스(예: NetX Duo)에 등록합니다. DAD(중복 주소 검색) 프로토콜(기본적으로 사용하도록 설정됨)이 구성된 경우, NetX Duo는 할당된 주소가 네트워크에서 고유한지 확인하기 위해 Neighbor Solicit 메시지를 자동으로 보냅니다. 고유한 것으로 확인되면 할당된 각 주소가 TENTATIVE에서 VALID로 승격되었을 때 DHCPv6 클라이언트에 알립니다. DHCPv6 클라이언트는 BOUND 상태로 승격되고, 디바이스는 해당 IPv6 주소를 사용하여 메시지를 보낼 수 있습니다. DAD 프로토콜이 실패하면 NetX Duo가 DHCPv6 클라이언트에 알리고, DHCPv6 클라이언트는 서버에 다시 할당된 IPv6 주소에 대한 DECLINE 메시지를 보내고, DHCPv6 클라이언트 상태를 다시 INIT 상태로 설정합니다.

### <a name="notification-of-successful-address-assignment-and-validation"></a>성공한 주소 할당 및 유효성 검사 알림

DHCPv6 클라이언트의 *nx_dhcpv6_client_create* 서비스에 상태 변경 콜백이 구성된 경우, 애플리케이션은 상태 변경을 통해 DHCPv6 클라이언트 주소 요청 결과를 확인할 수 있습니다. 서버에서 응답을 받지 못한 경우에는 SOLICIT에서 INIT로의 상태 변경이 관찰됩니다. 서버에서 응답을 받았지만 서버가 주소를 할당할 수 없는 경우, 이 애플리케이션은 DHCPv6 클라이언트 서버 오류 콜백의 알림을 받습니다(*nx_dhcpv6_client_create* 에 구성된 경우). 클라이언트가 BOUND 상태를 달성했지만 DAD 확인에 실패한 경우 상태가 BOUND에서 INIT로 변경되는 것을 볼 수 있습니다. DAD가 설정된 애플리케이션은 요청 프로세스를 시작한 후에 DAD 확인 시간 동안 대기해야 합니다. 일반적으로 이는 약 400~500틱(대부분의 경우 4-5초)입니다.

### <a name="relinquishing-an-ipv6-address"></a>IPv6 주소 포기

클라이언트는 할당된 IPv6 주소를 해제해야 하는 경우에 *nx_dhcpv6_request_release* 서비스를 호출하여 DHCPv6 서버에 알립니다.

### <a name="uint-nx_dhcpv6_request_releasenx_dhcpv6-dhcpv6_ptr"></a>UINT nx_dhcpv6_request_release(NX_DHCPV6 \*dhcpv6_ptr)

DHCPv6 클라이언트는 주소를 할당해 준 서버로 할당된 주소가 포함된 유니캐스트 RELEASE 메시지를 보내고, 서버에서 메시지 수신을 확인하는 REPLY를 보내 줄 때까지 기다립니다.

참고: 전원이 꺼지는 중이지만 다시 부팅된 후 할당된 IPv6 주소를 계속 사용할 예정인 클라이언트에는 다른 프로세스가 있습니다. 전원을 켤 때 새 주소를 요청하지 않을 예정인 경우에는 전원이 꺼지는 동안 RELEASE 메시지를 보내지 않습니다. 이러한 상황에 대한 설명은 "비휘발성 메모리 요구 사항"을 참조하세요.

### <a name="dhcpv6-lease-timeouts"></a>DHCPv6 임대 시간 제한

서버에서 할당하는 IPv6 임대에는 각 ID 연결, 즉 비임시(IANA) 블록에 T1과 T2라는 두 개의 시간 제한 매개 변수가 포함되어 있습니다. IANA는 이 사용자 가이드의 다른 부분에서 설명합니다. DHCPv6 클라이언트가 할당된 IPv6 주소에 바인딩된 시점부터 경과한 시간이 T1과 같으면 DHCPv6 클라이언트는 RENEW 메시지를 전송하여 IPv6 주소 갱신을 자동으로 시작합니다. 경과된 시간이 T2와 같으면 DHCPv6 클라이언트는 RENEW 요청에 대한 응답을 받지 못한 경우 REBIND 메시지를 자동으로 보냅니다.

다른 두 IPv6 임대 매개 변수(기본 및 유효 수명)는 IANA 블록에 포함된 각 IA(ID 연결) 블록을 사용하여 할당됩니다. 기본 및 유효 수명은 할당된 IPv6 주소가 각각 사용되지 않거나 유효하지 않게 되는 시점을 말합니다. T1은 기본 수명보다 작아야 합니다. T2는 유효 수명보다 작아야 합니다.

### <a name="ip-thread-task-requirements"></a>IP 스레드 작업 요구 사항

NetX Duo DHCPv6 클라이언트에서 DHCPv6 클라이언트 서비스를 사용하려면 DHCPv6 클라이언트를 만들기 전에 NetX Duo IP 인스턴스를 만들어야 합니다.

DHCPv6 클라이언트를 사용하기 전에 IP 인스턴스에서 UDP, IPv6 및 ICMPv6를 사용하도록 설정해야 합니다.

  - *nx_udp_enable*

  - *nxd_ipv6_enable*

  - *nxd_icmp_enable*

### <a name="packet-pool-requirements"></a>패킷 풀 요구 사항

NetX Duo DHCPv6 클라이언트를 만들기 전에 먼저 DHCPv6 메시지를 보내는 데 사용되는 패킷 풀부터 만들어야 합니다. 패킷 페이로드 및 사용 가능한 패킷 수와 관련된 패킷 풀의 크기는 사용자가 구성할 수 있으며, 애플리케이션에서 보내는 DHCPv6 메시지 및 기타 전송의 예상 양에 따라 달라집니다.

일반적인 DHCPv6 메시지는 클라이언트에서 요청하는 IA 주소 및 DHCPv6 옵션 수에 따라 약 200바이트입니다.

### <a name="network-requirements"></a>네트워크 요구 사항

NetX Duo DHCPv6 클라이언트를 사용하려면 포트 546에 바인딩된 UDP 소켓을 만들어야 합니다. 이 소켓은 DHCPv6 클라이언트 작업을 만들 때 생성됩니다.

### <a name="non-volatile-memory-requirements"></a>비휘발성 메모리 요구 사항

DHCPv6 클라이언트가 전원이 꺼질 때 DHCPv6 서버와 관련된 IPv6 임대를 해제하고 다시 부팅될 때 새 IPv6 주소를 요청하는 경우에는 비휘발성 메모리 스토리지가 필요하지 않습니다. 클라이언트에서 할당된 임대를 계속 사용하려면 다시 부팅하는 동안 DHCPv6 클라이언트에 대한 특정 정보를 비휘발성 메모리에 저장해야 합니다.

비휘발성 메모리 요구 사항과 DHCPv6 클라이언트 API는 챕터 2의 **NetX Duo DHCPv6 클라이언트 사용** 에 자세히 설명되어 있습니다.

### <a name="netx-duo-dhcpv6-client-limitations"></a>NetX Duo DHCPv6 클라이언트 제한 사항

NetX Duo DHCPv6 클라이언트의 현재 릴리스에는 다음과 같은 제한 사항이 있습니다.

  - NetX Duo DHCPv6 클라이언트는 서버에서 허용한다고 표시하더라도 유니캐스트 DHCPv6 메시지를 DHCPv6 서버로 보내기 위한 서버 유니캐스트 옵션을 지원하지 않습니다.

  - NetX Duo DHCPv6 클라이언트는 서버에서 네트워크의 클라이언트에 대한 IPv6 주소 변경을 시작하는 다시 구성 요청을 지원하지 않습니다.

  - NetX Duo DHCPv6 클라이언트는 DHCPv6 고유 식별자 제어 블록에 대한 엔터프라이즈 형식을 지원하지 않습니다. 링크 계층 및 링크 계층+시간 형식만 지원합니다.

  - NetX Duo DHCPv6 클라이언트는 TA(임시 연결) 주소 요청을 지원하지 않지만 비임시(IANA) 옵션 요청은 지원합니다.

## <a name="multihome-and-multiple-address-support"></a>멀티홈 및 다중 주소 지원

DHCPv6 클라이언트는 인터페이스마다 다중 인터페이스와 다중 주소를 지원합니다. 클라이언트 애플리케이션은 DHCPv6 클라이언트 서비스 *nx_dhcpv6_client_set_interface* 를 사용하여 DHCPv6 서버와 통신하는 데 사용할 네트워크 인터페이스를 설정할 수 있습니다. DHCPv6 클라이언트는 기본 인터페이스(인덱스 0)로 기본 설정됩니다.

인터페이스별 다중 주소의 경우, DHCPv6 클라이언트는 인덱스 0부터 시작하는 주소의 내부 목록을 유지합니다. DHCPv6 클라이언트에 등록된 것과 동일한 주소가 인터페이스 주소에 대한 IP 테이블의 동일한 인덱스에 반드시 있어야 하는 것은 아닙니다.

클라이언트 IPv6 주소 임대에 대한 정보를 검색하는 DHCPv6 클라이언트 서비스의 경우, 일부는 주소 인덱스를 지정해야 합니다. 기본 및 유효 수명을 가져오는 예는 다음과 같습니다.

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                              UINT address_index, 
                                              NXD_ADDRESS *ip_address,
                                              ULONG preferred_lifetime, 
                                              ULONG *valid_lifetime)
```

클라이언트 애플리케이션은 *nx_dhcpv6_get_valid_ip_address_count* 서비스에서 할당된 유효한 IPv6 주소 수를 검색할 수도 있습니다.

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count)
```

NetX Duo에서 다중 주소가 지원되기 전에 생성된 레거시 DHCPv6 클라이언트 서비스는 주소 인덱스를 허용하지 않습니다. 따라서 이러한 서비스를 사용하면 클라이언트에 할당된 IA 주소 수에 관계없이 기본 글로벌 IA 주소에서 요청된 데이터를 가져옵니다. 아래에 예가 나와 있습니다.

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address)
```

## <a name="netx-duo-dhcpv6-client-callback-functions"></a>NetX Duo DHCPv6 클라이언트 콜백 함수

*nx_dhcpv6_state_change_callback*

DHCPv6 클라이언트가 DHCPv6 요청 처리의 결과로 새 DHCPv6 상태로 변경될 때 이 콜백 함수를 사용하여 애플리케이션에 알립니다.

*nx_dhcpv6_server_error_handler*

DHCPv6 클라이언트가 0(성공)이 아닌 상태의 *Status* 옵션을 포함하는 서버 회신을 받으면 이 콜백을 사용하여 애플리케이션에 알립니다(서버 오류 상태 코드 포함).

참고: 이러한 콜백 함수는 DHCPv6 클라이언트 스레드 작업에서 호출되므로, 클라이언트 애플리케이션은 *nx_dhcpv6_start, nx_dhcpv6_stop* 과 같은 DHCPv6 클라이언트의 뮤텍스 제어를 요구하는 NetX Duo DHCPv6 클라이언트 서비스와 콜백에서 직접 메시지를 전송하는 API(예: *nx_dhcpv6_request_release*)를 호출하면 안 됩니다.

## <a name="dhcpv6-rfcs"></a>DHCPv6 RFC

NetX Duo DHCP는 RFC3315, RFC3646 및 관련 RFC를 준수합니다.