---
title: 5장 - Azure RTOS NetX 네트워크 드라이버
description: 이 장에서는 Azure RTOS NetX의 네트워크 드라이버에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 09/11/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ccc55111d785d84cdb193c387830abbc03a15e7c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811670"
---
# <a name="chapter-5---netx-network-drivers"></a>5장 - NetX 네트워크 드라이버

이 장에서는 NetX의 네트워크 드라이버에 대해 설명합니다. 제공된 정보는 개발자가 Azure RTOS NetX용 애플리케이션별 네트워크 드라이버를 작성하는 데 도움이 되도록 설계되었습니다.

## <a name="driver-introduction"></a>드라이버 소개

NX_IP 구조에는 단일 IP 인스턴스를 관리하는 모든 항목이 포함됩니다. 여기에는 일반적인 TCP/IP 프로토콜 정보뿐만 아니라 애플리케이션별 실제 네트워크 드라이버의 항목 루틴이 포함됩니다. 드라이버의 진입 루틴은 ****nx_ip_create*** _ 서비스 중에 정의됩니다. ***nx_ip_interface_attach*** 서비스를 통해 IP 인스턴스에 추가 디바이스를 추가할 수 있습니다.

NetX와 애플리케이션의 네트워크 드라이버 간의 통신은 **NX_IP_DRIVER** 요청 구조를 통해 수행됩니다. 이 구조는 대부분 호출자의 스택에서 로컬로 정의되므로 드라이버 및 호출 함수가 반환된 후에 릴리스됩니다. 구조는 다음과 같이 정의됩니다.

```C
typedef struct NX_IP_DRIVER_STRUCT
{
    UINT nx_ip_driver_command;
    UINT nx_ip_driver_status;
    ULONG nx_ip_driver_physical_address_msw;
    ULONG nx_ip_driver_physical_address_lsw;
    NX_PACKET *nx_ip_driver_packet;
    ULONG *nx_ip_driver_return_ptr;
    NX_IP *nx_ip_driver_ptr;
    NX_INTERFACE *nx_ip_driver_interface;
} NX_IP_DRIVER;
```

## <a name="driver-entry"></a>드라이버 진입

NetX는 드라이버 초기화 및 패킷 전송, 네트워크 디바이스 초기화 및 활성화를 포함한 다양한 제어 및 상태 작업을 위해 네트워크 드라이버 진입 함수를 호출합니다. NetX는 _ *NX_IP_DRIVER** 요청 구조에서 ***nx_ip_driver_command** _ 필드를 설정하여 네트워크 드라이버에 명령을 실행합니다. 드라이버 진입 함수의 형식은 다음과 같습니다.

```C
VOID my_driver_entry(NX_IP_DRIVER *request);
```

## <a name="driver-requests"></a>드라이버 요청

NetX는 특정 명령을 사용하여 드라이버 요청을 만들고 드라이버 진입 함수를 호출하여 명령을 실행합니다. 각 네트워크 드라이버에는 단일 진입 함수가 있으므로 NetX는 드라이버 요청 데이터 구조를 통해 모든 요청을 수행합니다. 드라이버 요청 데이터 구조체(**NX_IP_DRIVER**)의 ***nx_ip_driver_command*** 멤버가 요청을 정의합니다. 상태 정보는 ***nx_ip_driver_status*** 멤버의 호출자에게 다시 보고됩니다. 이 필드가 **NX_SUCCESS** 인 경우 드라이버 요청이 성공적으로 완료된 것입니다.

NetX는 드라이버에 대한 모든 액세스를 직렬화합니다. 따라서 드라이버는 진입 함수를 호출하는 여러 스레드를 비동기적으로 처리할 필요가 없습니다. 디바이스 드라이버 함수는 IP 뮤텍스가 잠긴 상태에서 실행됩니다. 따라서 디바이스 드라이버 내부 함수는 스스로 차단하지 않아야 합니다.

일반적으로 디바이스 드라이버는 인터럽트도 처리합니다. 따라서 모든 드라이버 함수는 인터럽트로부터 안전해야 합니다.

### <a name="driver-initialization"></a>드라이버 초기화

실제 드라이버 초기화 프로세스는 애플리케이션마다 다르지만, 일반적으로 데이터 구조와 실제 하드웨어 초기화로 구성됩니다. 드라이버 초기화를 위해 NetX에 필요한 정보는 IP MTU(최대 전송 단위)이며, 이는 IP 헤더 등 IP 계층 페이로드에 사용할 수 있는 바이트 수이고 실제 인터페이스에 논리적/물리적 매핑이 필요한 경우입니다. 드라이버 요구 사항

_ *NX_INTERFACE** 구조체의 ***nx_interface_ip_mtu_size** _에서 해당 값을 설정하여 인터페이스 MTU를 구성합니다.

또한 디바이스 드라이버는 인터페이스 주소 매핑이 필요한지 여부를 NetX에 알리기 위해 ***nx_ip_interface_address_mapping_needed***

(**NX_INTERFACE** 구조체에 있음)에서도 해당 값을 설정해야 합니다. 주소 매핑이 필요한 경우 드라이버는 유효한 MAC 주소를 사용하여 인터페이스를 구성하고 NetX에 MAC 주소를 제공해야 합니다.

네트워크 드라이버가 NetX에서 NX_LINK INITIALIZE 요청을 수신하면 위에 표시된 NX_IP_DRIVER 요청 제어 블록의 일부로 IP 제어 블록에 대한 포인터를 받습니다.

애플리케이션이 ***nx_ip_create*** 를 호출하고 나면 IP 도우미 스레드는 명령이 NX_LINK_INITIALIZE로 설정된 드라이버 요청을 드라이버로 보내 실제 네트워크 인터페이스를 초기화합니다. 초기화 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버    | 의미 |
|------------------------|-----------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INITIALIZE |
| nx_ip_driver_ptr       | IP 인스턴스에 대한 포인터입니다. 드라이버 함수에서 작동할 IP 인스턴스를 찾을 수 있도록 이 값을 드라이버에서 저장해야 합니다. |
| nx_ip_driver_interface | IP 인스턴스 내의 네트워크 인터페이스 구조에 대한 포인터입니다. 이 정보는 드라이버에서 저장해야 합니다. 패킷 수신 시, 스택 위로 패킷을 전송하는 경우 드라이버는 인터페이스 구조 정보를 사용해야 합니다. |
| nx_ip_driver_status    | 완료 상태입니다. 드라이버가 지정된 인터페이스를 IP 인스턴스로 초기화할 수 없는 경우 0이 아닌 오류 상태를 반환합니다.                                                                                           |


> [!IMPORTANT]
> 대부분의 드라이버 명령은 IP 인스턴스를 위해 만들어진 IP 도우미 스레드에서 호출됩니다. 따라서 드라이버 루틴은 차단 작업을 수행하지 않아야 합니다. 그러지 않으면 IP 도우미 스레드가 중단되어 IP 스레드에 의존하는 애플리케이션에 무한 지연이 발생할 수 있습니다.

### <a name="enable-link"></a>링크 사용  

그런 다음, IP 도우미 스레드는 드라이버 요청에서 드라이버 명령을 NX_LINK_ENABLE로 설정하고 네트워크 드라이버로 요청을 전송하여 실제 네트워크를 사용하도록 설정합니다. 이는 IP 도우미 스레드가 초기화 요청을 완료한 직후에 발생합니다. 링크를 사용하도록 설정하는 것은 인터페이스 인스턴스에서 nx_interface_link_up 필드를 설정하는 것만큼 간단합니다. 그러나 실제 하드웨어 조작도 포함될 수 있습니다. 링크 사용 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버    | 의미 |
|------------------------|------------------------------------------|
| nx_ip_driver_command   | NX_LINK_ENABLE                                                                                                          |
| nx_ip_driver_ptr       | IP 인스턴스에 대한 포인터                                                                                                  |
| nx_ip_driver_interface | 인터페이스 인스턴스에 대한 포인터                                                                                       |
| nx_ip_driver_status    | 완료 상태입니다. 드라이버에서 지정된 인터페이스를 사용하도록 설정할 수 없는 경우 0이 아닌 오류 상태를 반환합니다. |



### <a name="disable-link"></a>링크 사용 안 함  

이 요청은 ***nx_ip_delete** _ 서비스에서 IP 인스턴스를 삭제하는 동안 NetX에서 수행됩니다. 또는 애플리케이션에서 전원을 절약할 목적으로 임시로 링크를 사용하지 않도록 설정하기 위해 이 명령을 실행할 수 있습니다. 이 서비스는 IP 인스턴스에서 실제 네트워크 인터페이스를 사용하지 않도록 설정합니다. 링크를 사용하지 않도록 설정하는 프로세스는 인터페이스 인스턴스에서 _nx_interface_link_up* 플래그를 지우는 것만큼 간단할 수 있습니다. 그러나 실제 하드웨어 조작을 포함할 수도 있습니다. 일반적으로 ***링크 사용**_ 작업의 반대 작업입니다. 링크를 사용하지 않도록 설정한 후 애플리케이션은 _ *_링크 사용_** 작업을 요청하여 인터페이스를 사용하도록 설정합니다. 링크를 사용하지 않도록 설정하는 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버    | 의미 |
|------------------------|--------------------------------------|
| nx_ip_driver_command   | NX_LINK_DISABLE |
| nx_ip_driver_ptr       | IP 인스턴스에 대한 포인터 |
| nx_ip_driver_interface | 인터페이스 인스턴스에 대한 포인터 |
| nx_ip_driver_status    | 완료 상태입니다. 드라이버가 IP 인스턴스에서 지정된 인터페이스를 사용하지 않도록 설정할 수 없는 경우 0이 아닌 오류 상태를 반환합니다. |


### <a name="uninitialize-link"></a>링크 초기화 취소  

이 요청은 ***nx_ip_delete*** 서비스에서 IP 인스턴스를 삭제하는 동안 NetX에서 수행됩니다. 이 요청은 인터페이스의 초기화를 취소하고 초기화 단계에서 만들어진 모든 리소스를 릴리스합니다. 일반적으로 ***링크 초기화*** 작업의 반대 작업입니다. 인터페이스 초기화를 취소한 후에는 인터페이스를 다시 초기화할 때까지 디바이스를 사용할 수 없습니다.

링크를 사용하지 않도록 설정하는 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버  | 의미                |
|----------------------|------------------------|
| nx_ip_driver_command | NX_LINK_UNINITIALZE    |
| nx_ip_driver_ptr     | IP 인스턴스에 대한 포인터 |
| nx_ip_driver_interface | 인터페이스 인스턴스에 대한 포인터 |
| nx_ip_driver_status    | 완료 상태입니다. 드라이버가 지정된 인터페이스를 IP 인스턴스에 대한 초기화를 취소할 수 없는 경우 0이 아닌 오류 상태를 반환합니다. |


### <a name="packet-send"></a>패킷 송신  

이 요청은 모든 NetX 프로토콜이 패킷을 전송하는 데 사용하는 내부 IP 전송 처리 중에 수행됩니다(ARP, RARP 제외). 패킷 전송 명령이 수신되면 *nx_packet_prepend_ptr* 은 전송할 패킷의 시작, 즉 IP 헤더의 시작 부분을 가리킵니다.
*nx_packet_length* 는 전송되는 데이터의 전체 크기(바이트)를 나타냅니다. *nx_packet_next* 가 유효하면 나가는 IP 데이터그램은 여러 패킷에 저장되므로 드라이버는 연결된 패킷을 따르고 전체 프레임을 전송해야 합니다. 연결된 각 패킷의 유효한 데이터 영역은 *nx_packet_prepend_ptr* 과 *nx_packet_append_ptr* 사이에 저장됩니다.

드라이버는 실제 헤더를 구성해야 합니다. IP 주소 매핑에 대한 실제 주소가 필요한 경우(예: 이더넷) IP 계층에서 MAC 주소를 이미 확인했습니다. 대상 MAC 주소는 nx_ip_driver_physical_address_msw 및 nx_ip_driver_physical_address_lsw에 저장된 IP 인스턴스에서 전달됩니다.

실제 헤더를 추가한 후 패킷 전송 처리는 드라이버의 출력 함수를 호출하여 패킷을 전송합니다.

다음 NX_IP_DRIVER 멤버는 패킷 전송 요청에 사용됩니다.

| NX_IP_DRIVER 멤버               | 의미 |
|-----------------------------------|---------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_PACKET_SEND |
| nx_ip_driver_ptr                  | IP 인스턴스에 대한 포인터 |
| nx_ip_driver_packet               | 전송할 패킷에 대한 포인터 |
| nx_ip_driver_interface            | 인터페이스 인스턴스에 대한 포인터             |
| nx_ip_driver_physical_address_msw | 가장 중요한 32비트 실제 주소(실제 매핑이 필요한 경우에만) |
| nx_ip_driver_physical_address_lsw | 가장 덜 중요한 32비트 실제 주소(실제 매핑이 필요한 경우에만)    |
| nx_ip_driver_status               | 완료 상태입니다. 드라이버가 패킷을 보낼 수 없으면 0이 아닌 오류 상태를 반환합니다.  |

### <a name="packet-broadcast"></a>패킷 브로드캐스트  
이 요청은 전송 패킷 요청과 거의 동일합니다. 유일한 차이점은 대상 실제 주소 필드가 이더넷 브로드캐스트 MAC 주소로 설정된다는 것입니다. 패킷 브로드캐스트 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버                | 의미          |
|------------------------------------|--------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_PACKET_BROADCAST |
| nx_ip_driver_ptr                   | IP 인스턴스에 대한 포인터  |
| nx_ip_driver_packet                | 전송할 패킷에 대한 포인터 |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF(브로드캐스트) |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF(브로드캐스트) |
| nx_ip_driver_interface             | 인터페이스 인스턴스에 대한 포인터 |
| nx_ip_driver_status                | 완료 상태입니다. 드라이버가 패킷을 보낼 수 없으면 0이 아닌 오류 상태를 반환합니다. |

### <a name="arp-send"></a>ARP 전송  

이 요청은 IP 패킷 전송 요청과도 유사합니다.
유일한 차이점은 이더넷 헤더는 IP 패킷 대신 ARP 패킷을 지정하고 대상 실제 주소 필드는 MAC 브로드캐스트 주소로 설정한다는 것입니다. 다음 NX_IP_DRIVER 멤버는 ARP 전송 요청에 사용됩니다.

| **NX_IP_DRIVER 멤버** | **의미** |
| --- | --- |
| nx_ip_driver_command | NX_LINK_ARP_SEND |
| nx_ip_driver_ptr | IP 인스턴스에 대한 포인터 |
| nx_ip_driver_packet | 전송할 패킷에 대한 포인터 |
| nx_ip_driver_physical_address_msw | 0x0000FFFF(브로드캐스트) |
| nx_ip_driver_physical_address_lsw | 0xFFFFFFFF(브로드캐스트) |
| nx_ip_driver_interface | 인터페이스 인스턴스에 대한 포인터 |
| nx_ip_driver_status | 완료 상태입니다. 드라이버가 ARP 패킷을 전송할 수 없으면 0이 아닌 오류 상태를 반환합니다. |

실제 매핑이 필요하지 않은 경우에는 이 요청을 구현할 필요가 없습니다.

### <a name="arp-response-send"></a>ARP 응답 전송  

이 요청은 ARP 전송 패킷 요청과 거의 동일합니다. 유일한 차이점은 대상 실제 주소 필드가 IP 인스턴스에서 전달된다는 것입니다. 다음 NX_IP_DRIVER 멤버는 ARP 응답 전송 요청에 사용됩니다.

| NX_IP_DRIVER 멤버               | 의미 |
|-----------------------------------| ------------------------------------|
| nx_ip_driver_command              | NX_LINK_ARP_RESPONSE_SEND |
| nx_ip_driver_ptr                  | IP 인스턴스에 대한 포인터 |
| nx_ip_driver_packet               | 전송할 패킷에 대한 포인터|
| nx_ip_driver_physical_address_msw | 가장 중요한 32비트 실제 주소 |
| nx_ip_driver_physical_address_lsw | 가장 덜 중요한 32비트 실제 주소                     |
| nx_ip_driver_interface            | 인터페이스 인스턴스에 대한 포인터 |
| nx_ip_driver_status               | 완료 상태입니다. 드라이버가 ARP 패킷을 전송할 수 없으면 0이 아닌 오류 상태를 반환합니다. |

> [!NOTE]
> 실제 매핑이 필요하지 않은 경우에는 이 요청을 구현할 필요가 없습니다.

### <a name="rarp-send"></a>RARP 전송  

이 요청은 ARP 전송 패킷 요청과 거의 동일합니다. 유일한 차이점은 패킷 헤더의 형식이며 실제 대상은 항상 브로드캐스트 주소이기 때문에 실제 주소 필드는 필요하지 않습니다.

RARP 전송 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버               | 의미 |
|-----------------------------------|---------------------------------|
| nx_ip_driver_command              |NX_LINK_RARP_SEND |
| nx_ip_driver_ptr                  | IP 인스턴스에 대한 포인터 |
| nx_ip_driver_packet               | 전송할 패킷에 대한 포인터 |
| nx_ip_driver_physical_address_msw | 0x0000FFFF(브로드캐스트) |
| nx_ip_driver_physical_address_lsw | 0xFFFFFFFF(브로드캐스트) |
| NX_IP_DRIVER 멤버               | 의미 |
| nx_ip_driver_interface            | 인터페이스 인스턴스에 대한 포인터 |
| nx_ip_driver_status               | 완료 상태입니다. 드라이버가 RARP 패킷을 전송할 수 없으면 0이 아닌 오류 상태를 반환합니다.  |

> [!NOTE]
> RARP 서비스가 필요한 애플리케이션은 이 명령을 구현해야 합니다.

### <a name="multicast-group-join"></a>멀티캐스트 그룹 조인  

이 요청은 ***nx_igmp_multicast_interface join*** 서비스를 사용하여 수행됩니다. 네트워크 드라이버는 제공된 멀티캐스트 그룹 주소를 사용하고 해당 멀티캐스트 그룹 주소에서 들어오는 패킷을 허용하도록 실제 미디어를 설정합니다. 멀티캐스트 필터를 지원하지 않는 드라이버의 경우 드라이버 수신 로직은 비규칙(Promiscuous) 모드여야 합니다. 이 경우 드라이버는 대상 MAC 주소를 기반으로 들어오는 프레임을 필터링하여 IP 인스턴스에 전달되는 트래픽의 양이 줄여야 할 수 있습니다. 멀티캐스트 그룹 조인 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버               | 의미 |
|-----------------------------------|-----------------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_MULTICAST_JOIN                                                |
| nx_ip_driver_ptr                  | IP 인스턴스에 대한 포인터                                                |
| nx_ip_driver_physical_address_msw | 가장 중요한 32비트 실제 멀티캐스트 주소                |
| nx_ip_driver_physical_address_lsw | 가장 덜 중요한 32비트 실제 멀티캐스트 주소               |
| nx_ip_driver_interface            | 인터페이스 인스턴스에 대한 포인터                                     |
| nx_ip_driver_status               | 완료 상태입니다. 드라이버가 멀티캐스트 그룹에 조인할 수 없는 경우 0이 아닌 오류 상태를 반환합니다. |


### <a name="multicast-group-leave"></a>멀티캐스트 그룹 나가기  

이 요청은 ***nx_igmp_multicast_leave*** 서비스를 명시적으로 호출하여 호출됩니다. 드라이버가 제공된 이더넷 멀티캐스트 주소를 멀티캐스트 목록에서 제거합니다. 호스트가 멀티캐스트 그룹을 나간 후, 이 이더넷 멀티캐스트 주소를 사용하는 네트워크의 패킷은 더 이상 이 IP 인스턴스에서 수신되지 않습니다. 다음 NX_IP_DRIVER 멤버는 멀티캐스트 그룹 나가기 요청에 사용됩니다.

| NX_IP_DRIVER 멤버               | 의미 |
|-----------------------------------|-----------------------------------------------------------------|
| nx_ip_driver_command              | NX_LINK_MULTICAST_LEAVE |
| nx_ip_driver_ptr                  | IP 인스턴스에 대한 포인터 |
| nx_ip_driver_physical_address_msw | 가장 중요한 32비트 실제 멀티캐스트 주소 |
| nx_ip_driver_physical_address_lsw | 가장 덜 중요한 32비트 실제 멀티캐스트 주소 |
| nx_ip_driver_interface            | 인터페이스 인스턴스에 대한 포인터 |
| nx_ip_driver_status               | 완료 상태입니다. 드라이버가 멀티캐스트 그룹을 나갈 수 없는 경우 0이 아닌 오류 상태를 반환합니다. |


### <a name="attach-interface"></a>인터페이스 연결  

이 요청은 NetX에서 디바이스 드라이버로 호출되므로 드라이버에서 드라이버 인스턴스를 해당 IP 인스턴스와 IP 내의 실제 인터페이스 인스턴스와 연결할 수 있습니다. 인터페이스 연결 요청에 사용되는 NX_IP_DRIVER 멤버는 다음과 같습니다.

| NX_IP_DRIVER 멤버    | 의미 |
|------------------------|-------------------------------------------------|
| nx_ip_driver_command   | X_LINK_INTERFACE_ATTACH |
| nx_ip_driver_ptr       | IP 인스턴스에 대한 포인터 |
| nx_ip_driver_interface | 인터페이스 인스턴스에 대한 포인터 |
| nx_ip_driver_status    | 완료 상태입니다. 드라이버가 지정된 인터페이스를 IP 인스턴스로 분리할 수 없는 경우 0이 아닌 오류 상태를 반환합니다.  |


### <a name="detach-interface"></a>인터페이스 분리  

이 요청은 디바이스 드라이버에 대한 NetX에서 호출되며, 드라이버에서 해당 IP 인스턴스 및 IP 내의 실제 인터페이스 인스턴스와 드라이버 인스턴스의 연결을 끊을 수 있습니다. 인터페이스 연결 요청에 사용되는 NX_IP_DRIVER 멤버는 다음과 같습니다.

| NX_IP_DRIVER 멤버    | 의미 |
|------------------------|---------------------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_DETACH |
| nx_ip_driver_ptr       | IP 인스턴스에 대한 포인터 |
| nx_ip_driver_interface | 인터페이스 인스턴스에 대한 포인터 |
| nx_ip_driver_status    | 완료 상태입니다. 드라이버가 지정된 인터페이스를 IP 인스턴스에 연결할 수 없는 경우 0이 아닌 오류 상태를 반환합니다. |

### <a name="get-link-status"></a>링크 상태 가져오기  

애플리케이션은 호스트의 모든 인터페이스에 대해 NetX 서비스 ***nx_ip_interface_status_check*** 서비스를 사용하여 네트워크 인터페이스 링크 상태를 쿼리할 수 있습니다. 해당 서비스에 대한 자세한 내용은 107페이지의 4장 "NetX 서비스 설명"을 참조하세요.

링크 상태는 *nx_ip_driver_interface* 포인터가 가리키는 NX_INTERFACE 구조의 *nx_interface_link_up* 필드에 포함됩니다. 링크 상태 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버     | 의미                                                                                                      |
|-------------------------|--------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_STATUS                                                                                           |
| nx_ip_driver_ptr        | IP 인스턴스에 대한 포인터                                                                                       |
| nx_ip_driver_return_ptr | 상태를 배치할 대상에 대한 포인터                                                              |
| nx_ip_driver_interface  | 인터페이스 인스턴스에 대한 포인터                                                                            |
| nx_ip_driver_status     | 완료 상태입니다. 드라이버가 특정 상태를 가져올 수 없는 경우 0이 아닌 오류 상태를 반환합니다. |
|                         |                                                                                                              |

> [!NOTE]
> 기본 인터페이스의 상태를 확인하는 데도 **nx_ip_status_check** 을 사용할 수 있습니다. 그러나 애플리케이션 개발자는 인터페이스 관련 서비스인 **nx_ip_interface_status_check** 를 사용하는 것이 좋습니다.

### <a name="get-link-speed"></a>링크 속도 가져오기  

이 요청은 ***nx_ip_driver_direct_command*** 서비스 내에서 수행됩니다. 드라이버는 제공된 대상에서 링크의 회선 속도를 저장합니다. 링크 회선 속도 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버     | 의미 |
|-------------------------|---------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_SPEED |
| nx_ip_driver_ptr        | IP 인스턴스에 대한 포인터 |
| nx_ip_driver_return_ptr | 회선 속도를 배치할 대상에 대한 포인터 |
| nx_ip_driver_interface  | 인터페이스 인스턴스에 대한 포인터 |
| nx_ip_driver_status     | 완료 상태입니다. 드라이버에서 속도 정보를 가져올 수 없는 경우 0이 아닌 오류 상태를 반환합니다.
 |


> [!NOTE]
> 이 요청은 NetX에서 내부적으로 사용되지 않으므로 해당 구현은 선택 사항입니다.

### <a name="get-duplex-type"></a>이중 형식 가져오기  

이 요청은 ***nx_ip_driver_direct_command*** 서비스 내에서 수행됩니다. 드라이버는 제공된 대상에 링크의 이중 형식을 저장합니다. 이중 형식 요청에 사용되는 NX_IP_DRIVER 멤버는 다음과 같습니다.

| NX_IP_DRIVER 멤버     | 의미 |
|-------------------------|-----------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_DUPLEX_TYPE |
| nx_ip_driver_ptr        | IP 인스턴스에 대한 포인터 |
| nx_ip_driver_return_ptr | 이중 형식을 배치할 대상에 대한 포인터 |
| nx_ip_driver_interface  | 인터페이스 인스턴스에 대한 포인터 |
| nx_ip_driver_status     | 완료 상태입니다. 드라이버에서 이중 정보를 가져올 수 없는 경우 0이 아닌 오류 상태를 반환합니다.
 |


> [!NOTE]
> 이 요청은 NetX에서 내부적으로 사용되지 않으므로 해당 구현은 선택 사항입니다.

### <a name="get-error-count"></a>오류 개수 가져오기  

이 요청은 ***nx_ip_driver_direct_command*** 서비스 내에서 수행됩니다. 드라이버는 제공된 대상에 링크의 오류 개수를 저장합니다. 이 기능을 지원하려면 드라이버에서 작업 오류를 추적해야 합니다. 링크 오류 개수 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버     | 의미                                                                                                  |
|-------------------------|----------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_ERROR_COUNT                                                                                  |
| nx_ip_driver_ptr        | IP 인스턴스에 대한 포인터                                                                                   |
| nx_ip_driver_return_ptr | 오류 개수를 배치할 대상에 대한 포인터                                                      |
| nx_ip_driver_interface  | 인터페이스 인스턴스에 대한 포인터                                                                        |
| nx_ip_driver_status     | 완료 상태입니다. 드라이버가 오류 개수를 가져올 수 없는 경우 0이 아닌 오류 상태를 반환합니다. |


> [!NOTE]
> 이 요청은 NetX에서 내부적으로 사용되지 않으므로 해당 구현은 선택 사항입니다.

### <a name="get-receive-packet-count"></a>수신 패킷 개수 가져오기  

이 요청은 ***nx_ip_driver_direct_command*** 서비스 내에서 수행됩니다. 드라이버는 제공된 대상에 링크의 수신 패킷 개수를 저장합니다. 이 기능을 지원하려면 드라이버가 수신된 패킷 개수를 추적해야 합니다. 링크 수신 패킷 개수 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버     | 의미                                                                                                    |
|-------------------------|------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_RX_COUNT                                                                                       |
| nx_ip_driver_ptr        | IP 인스턴스에 대한 포인터                                                                                     |
| nx_ip_driver_return_ptr | 수신 패킷 개수를 배치할 대상에 대한 포인터                                               |
| nx_ip_driver_interface  | 실제 네트워크 인터페이스에 대한 포인터                                                                  |
| nx_ip_driver_status     | 완료 상태입니다. 드라이버가 수신 개수를 가져올 수 없는 경우 0이 아닌 오류 상태를 반환합니다. |


> [!NOTE]
> 이 요청은 NetX에서 내부적으로 사용되지 않으므로 해당 구현은 선택 사항입니다.

### <a name="get-transmit-packet-count"></a>전송 패킷 개수 가져오기  

이 요청은 ***nx_ip_driver_direct_command*** 서비스 내에서 수행됩니다. 드라이버는 제공된 대상에 링크의 전송 패킷 개수를 저장합니다. 이 기능을 지원하려면 드라이버가 각 인터페이스에서 전송하는 각 패킷을 추적해야 합니다. 링크 전송 패킷 개수 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버     | 의미                                                                                                     |
|-------------------------|-------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_GET_TX_COUNT                                                                                        |
| nx_ip_driver_ptr        | IP 인스턴스에 대한 포인터                                                                                      |
| nx_ip_driver_return_ptr | 전송 패킷 개수를 배치할 대상에 대한 포인터                                               |
| nx_ip_driver_interface  | 인터페이스 인스턴스에 대한 포인터                                                                           |
| nx_ip_driver_status     | 완료 상태입니다. 드라이버가 전송 개수를 가져올 수 없는 경우 0이 아닌 오류 상태를 반환합니다. |


> [!NOTE]
> 이 요청은 NetX에서 내부적으로 사용되지 않으므로 해당 구현은 선택 사항입니다.

### <a name="get-allocation-errors"></a>할당 오류 가져오기  

이 요청은 ***nx_ip_driver_direct_command*** 서비스 내에서 수행됩니다. 드라이버는 제공된 대상에 링크의 패킷 풀 할당 오류 개수를 저장합니다. 링크 할당 오류 개수 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| **NX_IP_DRIVER 멤버** | **의미** |
| --- | ---|
| nx_ip_driver_command | NX_LINK_GET_ALLOC_ERRORS |
| nx_ip_driver_ptr | IP 인스턴스에 대한 포인터 |

| NX_IP_DRIVER 멤버     | 의미                                                                                                        |
|-------------------------|----------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_return_ptr | 할당 오류 개수를 배치할 대상에 대한 포인터                                                 |
| nx_ip_driver_interface  | 인터페이스 인스턴스에 대한 포인터                                                                              |
| nx_ip_driver_status     | 완료 상태입니다. 드라이버가 할당 오류를 가져올 수 없는 경우 0이 아닌 오류 상태를 반환합니다. |


이 요청은 NetX에서 내부적으로 사용되지 않으므로 해당 구현은 선택 사항입니다.

### <a name="driver-deferred-processing"></a>드라이버 지연된 처리  

이 요청은 전송 또는 수신 ISR에서 ***nx_ip_driver_deferred_processing*** 루틴을 호출하는 드라이버에 대한 응답으로 IP 도우미 스레드에서 수행됩니다. 이렇게 하면 드라이버 ISR에서 패킷 수신 및 IP 도우미 스레드로 전송 처리를 지연시켜 ISR에서 처리할 양을 줄일 수 있습니다.  nx_ip_driver_interface에서 가리키는 NX_INTERFACE 구조의 _nx_interface_additional_link_info* 필드는 드라이버에서 IP 도우미 스레드 컨텍스트의 지연된 처리 이벤트에 대한 정보를 저장하는 데 사용할 수 있습니다. 지연 처리 이벤트에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

**NX_IP_DRIVER**

| 멤버                 | 의미                           |
|------------------------|-----------------------------------|
| nx_ip_driver_command   | NX_LINK_DEFERRED_PROCESSING       |
| nx_ip_driver_ptr       | IP 인스턴스에 대한 포인터            |
| nx_ip_driver_interface | 인터페이스 인스턴스에 대한 포인터 |


### <a name="user-commands"></a>사용자 명령  

이 요청은 ***nx_ip_driver_direct_command*** 서비스 내에서 수행됩니다. 드라이버는 애플리케이션별 사용자 명령을 처리합니다. 사용자 명령 요청에는 다음과 같은 NX_IP_DRIVER 멤버가 사용됩니다.

| NX_IP_DRIVER 멤버     | 의미                                                                                                        |
|-------------------------|----------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command    | NX_LINK_USER_COMMAND                                                                                           |
| nx_ip_driver_ptr        | IP 인스턴스에 대한 포인터                                                                                         |
| nx_ip_driver_return_ptr | 사용자 정의                                                                                                   |
| nx_ip_driver_interface  | 인터페이스 인스턴스에 대한 포인터                                                                              |
| nx_ip_driver_status     | 완료 상태입니다. 드라이버가 사용자 명령을 실행할 수 없는 경우 0이 아닌 오류 상태를 반환합니다. |


이 요청은 NetX에서 내부적으로 사용되지 않으므로 해당 구현은 선택 사항입니다.

### <a name="unimplemented-commands"></a>구현되지 않은 명령  

네트워크 드라이버에서 구현되지 않은 명령에는 반환 상태 필드가 NX_UNHANDLED_COMMAND로 설정되어 있어야 합니다.

## <a name="driver-output"></a>드라이버 출력  

이전에 언급한 모든 패킷 전송 요청에는 드라이버에 구현된 출력 함수가 필요합니다. 특정 전송 논리는 하드웨어마다 다르지만 일반적으로 패킷을 즉시 전송할 하드웨어 용량을 확인하는 것으로 구성됩니다. 가능하면 패킷 페이로드(및 패킷 체인의 추가 페이로드)가 하나 이상의 하드웨어 전송 버퍼에 로드되고 전송 작업이 시작됩니다. 패킷이 사용 가능한 전송 버퍼에 맞지 않으면 패킷은 큐에 대기되고 전송 버퍼를 사용할 수 있게 되면 전송되어야 합니다.

권장 전송 큐는 head 포인터와 tail 포인터가 모두 있는 단독으로 연결된 목록입니다. 새 패킷이 큐의 끝에 추가되고 가장 오래된 패킷을 맨 앞에 유지합니다. nx_packet_queue_next 필드는 큐에서 패킷의 다음 링크로 사용됩니다. 드라이버는 전송 큐의 head 및 tail 포인터를 정의합니다.

이 큐는 드라이버의 스레드 및 인터럽트 부분에서 액세스되기 때문에 큐 조작 주위에 인터럽트 보호를 배치해야 합니다.

대부분의 실제 하드웨어 구현은 패킷 전송 완료 시 인터럽트를 생성합니다.
이러한 인터럽트를 수신하는 드라이버는 일반적으로 전송중인 패킷과 연결된 리소스를 릴리스합니다. 전송 논리가 NX_PACKET 버퍼에서 직접 데이터를 읽는 경우 드라이버는 ***nx_packet_transmit_release*** 서비스를 사용하여 전송 완료 인터럽트와 연결된 패킷을 사용 가능한 패킷 풀로 다시 릴리스해야 합니다. 그런 다음, 드라이버는 전송 대기 중인 추가 패킷의 전송 큐를 검사합니다. 하드웨어 전송 버퍼에 적합한 대기 중인 많은 전송 패킷이 큐에서 제거되고 버퍼에 로드됩니다. 그다음에는 다른 전송 작업이 시작됩니다.

NX_PACKET의 데이터가 전송기 FIFO로 이동되는 즉시(또는 드라이버가 제로 복사 작업을 지원하는 경우 NX_PACKET의 데이터가 전송됨), ***nx_packet_transmit_release*** 를 호출하기 전에 드라이버는 nx_packet_prepend_ptr를 IP 헤더의 시작 부분으로 이동해야 합니다. 이에 따라 *nx_packet_length* 필드를 조정해야 합니다. IP 프레임이 여러 패킷으로 구성된 경우 패킷 체인의 헤드만 릴리스하면 됩니다.

## <a name="driver-input"></a>드라이버 입력  

수신된 패킷 인터럽트가 수신되면 네트워크 드라이버가 실제 하드웨어 수신 버퍼에서 패킷을 검색하고 유효한 NetX 패킷을 빌드합니다. 유효한 NetX 패킷을 빌드하려면 적절한 길이 필드를 설정하고 들어오는 패킷의 크기가 단일 패킷 페이로드보다 큰 경우 여러 패킷을 함께 연결해야 합니다. 제대로 빌드되면 prepend_ptr이 실제 계층 헤더 다음으로 이동되고 수신 패킷은 NetX로 발송됩니다.

NetX는 IP 및 ARP 헤더를 ULONG 경계에 맞춘다고 가정합니다. 따라서 NetX 드라이버는 이 맞춤을 확인해야 합니다. 이더넷 환경에서는 패킷의 시작부터 이더넷 헤더를 2바이트씩 시작하여 이 작업을 수행합니다. *nx_packet_prepend_ptr* 가 이더넷 헤더를 넘어 이동하는 경우 기본 IP 또는 ARP 헤더를 4바이트로 맞춥니다.

NetX에서 사용할 수 있는 몇 가지 수신 패킷 함수가 있습니다. 수신된 패킷이 ARP 패킷이면 _***nx_arp_packet_deferred_receive**_ 가 호출됩니다. 수신 패킷이 RARP 패킷이면 _ _*_nx_rarp_packet_deferred_receive_*_ 가 호출됩니다. 들어오는 IP 패킷을 처리하는 몇 가지 옵션이 있습니다. IP 패킷을 가장 빠르게 처리할 수 있도록 _ __nx_ip_packet_receive__ 를 호출합니다. 이러한 방식은 오버헤드가 가장 적지만 드라이버의 수신 인터럽트 서비스 처리기(ISR)에서 더 많은 처리를 해야 합니다. 최소 ISR 처리의 경우 _ *_nx_ip_packet_deferred_receive_**를 호출합니다.

새 수신 패킷이 올바르게 빌드되면 실제 하드웨어의 수신 버퍼가 더 많은 데이터를 수신하도록 설정됩니다. 이 경우 NetX 패킷을 할당하고 하드웨어 수신 버퍼에 페이로드 주소를 배치해야 하거나 하드웨어 수신 버퍼에서 설정을 변경하기만 하면 됩니다. 오버런 가능성을 최소화하려면 패킷을 받은 후 최대한 빨리 하드웨어의 수신 버퍼에 사용할 수 있는 버퍼를 포함하는 것이 중요합니다.

초기 수신 버퍼는 드라이버 초기화 중에 설정됩니다.

### <a name="deferred-receive-packet-handling"></a>지연된 수신 패킷 처리  

드라이버는 NetX IP 도우미 스레드로 수신 패킷 처리를 연기할 수 있습니다. 일부 애플리케이션의 경우 이는 삭제된 패킷뿐만 아니라 ISR 처리를 최소화하는 데 필요할 수 있습니다. 지연된 패킷 처리를 사용하려면 먼저 NetX 라이브러리를 ***NX_DRIVER_DEFERRED_PROCESSING** _으로 정의하여 컴파일해야 합니다. 그러면 NetX IP 도우미 스레드에 지연된 패킷 논리가 추가됩니다. 그런 다음, 데이터 패킷을 받으면 드라이버는 __nx_ip_packet_deferred_receive():*를 호출해야 합니다.

```C
_nx_ip_packet_deferred_receive(ip_ptr, packet_ptr);
```

지연된 수신 함수는 *packet_ptr* 로 표시되는 수신 패킷을 FIFO(연결된 목록)에 배치하고 IP 도우미 스레드에 알립니다. 실행 후, IP 도우미는 지연된 처리 함수를 반복적으로 호출하여 지연된 각 패킷을 처리합니다. 지연된 처리기 처리에는 일반적으로 패킷의 실제 계층 헤더(일반적으로 이더넷)를 제거하고 NetX 수신 함수 중 하나로 발송하는 작업이 포함됩니다.  

***_nx_ip_packet_deferred_receive***  
***_nx_arp_packet_deferred_receive***  
***_nx_rarp_packet_deferred_receive*** 


## <a name="example-ram-ethernet-network-driver"></a>예제 RAM 이더넷 네트워크 드라이버  

NetX 데모 시스템은 ***nx_ram_network_driver.c.*** 파일에 정의된 작은 RAM 기반 네트워크 드라이버와 함께 제공됩니다.
이 드라이버는 IP 인스턴스가 모두 동일한 네트워크에 있다고 가정하고 가상 하드웨어 주소(MAC 주소)를 만들 때마다 각 디바이스 인스턴스에 할당합니다. 이 파일은 NetX 실제 네트워크 드라이버의 기본 구조에 대한 모범 예제를 제공합니다. 사용자는 이 예제에 나와 있는 드라이버 프레임워크를 사용하여 고유한 네트워크 드라이버를 개발할 수 있습니다.

네트워크 드라이버의 진입 함수는 IP 인스턴스 만들기 호출에 전달되는 * **_nx_ram_network_driver,** _입니다. 추가 네트워크 인터페이스에 대한 진입 함수를 __nx_ip_interface_attach__ 서비스에 전달할 수 있습니다. IP 인스턴스가 실행되기 시작하면 드라이버 진입 함수를 호출하여 디바이스를 초기화하고 사용하도록 설정합니다(_NX_LINK_INITIALIZE* 및 **NX_LINK_ENABLE** 참조). **NX_LINK_ENABLE** 명령을 실행한 후 디바이스는 패킷을 전송하고 수신할 준비가 되어 있어야 합니다. 

IP 인스턴스는 다음 명령 중 하나를 통해 네트워크 패킷을 전송합니다.

| ***NX_LINK_PACKET_SEND***    | IP 패킷이 전송되고 있습니다.                             |
| ------------------------------- | -------------------------------------------------------------- |
| ***NX_LINK_ARP_SEND***       | ARP 요청 또는 ARP 응답 패킷이 전송되고 있습니다.    |
| ***NX_LINK_ARP_RARP_SEND*** | 역방향 ARP 요청 또는 응답 패킷이 전송되고 있습니다. |

이러한 명령을 처리할 때 네트워크 드라이버는 적절한 이더넷 프레임 헤더를 미리 추가한 다음 전송을 위한 기본 하드웨어로 보내야 합니다. 전송 프로세스 중에 네트워크 드라이버에는 패킷 버퍼 영역의 단독 소유권이 있습니다. 따라서 데이터가 전송되고 있는 경우(또는 데이터가 드라이버 내부 전송 버퍼로 복사된 후) 네트워크 드라이버는 먼저 앞에 있는 포인터를 이더넷 헤더를 지나 IP 헤더로 이동하고(그에 따라 패킷 길이 조정), ***nx_packet_transmit_release*** 서비스를 호출하여 패킷 버퍼를 릴리스해야 합니다. 데이터 전송 후 패킷을 해제하지 않으면 패킷이 누출됩니다.

네트워크 디바이스 드라이버는 들어오는 데이터 패킷도 처리해야 합니다. RAM 드라이버 예제에서 수신된 패킷은 ***_nx_ram_network_driver_receive*** 함수에서 처리됩니다.

디바이스가 이더넷 프레임을 수신하면 드라이버는

NX_PACKET 구조체에서 데이터를 저장해야 합니다. NetX는 IP 헤더가 4바이트 맞춤 주소에서 시작한다고 가정합니다. 이더넷 헤더의 길이가 14바이트이기 때문에 드라이버는 IP 헤더가 4바이트 맞춤 주소에서 시작하도록 하기 위해 이더넷 헤더의 시작 부분을 2바이트 맞춤 주소로 저장해야 합니다.