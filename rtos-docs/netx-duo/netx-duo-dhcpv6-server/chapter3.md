---
title: 3장 - Azure RTOS NetX Duo DHCPv6 서버 구성 옵션
description: 이 장에는 Azure RTOS NetX Duo DHCPv6 서버 구성 옵션에 대한 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1dc0d6e41118a2f67fe98758f1f31f84d074d7af342b9db93162ffe6354077ea
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792131"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-server-configuration-options"></a>3장 - Azure RTOS NetX Duo DHCPv6 서버 구성 옵션

NetX Duo DHCPv6 서버 애플리케이션을 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음 목록에서 각각에 대해 자세히 설명합니다.
  
- **NX_DISABLE_ERROR_CHECKING** 이 옵션은 DHCPv6 오류 검사를 제거합니다. 일반적으로 애플리케이션을 디버그할 때 사용하도록 설정됩니다.  
  
- **NX_DHCPV6_SERVER_THREAD_STACK_SIZE** 이는 DHCPv6 스레드 스택의 크기를 정의합니다. 기본적으로 4096바이트 크기로 되어 있으며, 대부분의 NetX Duo 애플리케이션에 대해 충분한 크기입니다.

- **NX_DHCPV6_SERVER_THREAD_PRIORITY** DHCPv6 서버 스레드 우선 순위를 정의합니다. 이는 DHCPv6 서버의 IP 스레드 작업 우선 순위보다 낮아야 합니다. 기본값은 2입니다.

- **NX_DHCPV6_IP_LEASE_TIMER_INTERVAL** ThreadX 스케줄러에서 임대 타이머 항목 함수를 호출할 때의 타이머 간격(초)입니다. 항목 함수는 DHCPv6 서버에 대한 플래그를 설정하여 타이머 간격에 따라 임대에 대한 모든 클라이언트의 경과 시간을 증가시킵니다. 기본적으로 이 값은 60입니다.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL** ThreadX 스케줄러에서 세션 타이머 항목 함수를 호출할 때의 타이머 간격(초)입니다. 항목 함수는 DHCPv6 서버에 대한 플래그를 설정하여 타이머 간격에 따라 발생한 모든 활성 클라이언트 세션 시간을 증가시킵니다. 기본적으로 이 값은 3입니다.

다음은 상태 옵션 메시지 유형 및 사용자 구성 가능 메시지에 적용되는 정의입니다. 상태 옵션은 다음과 같은 클라이언트 요청의 결과를 나타냅니다.

- **NX_DHCPV6_STATUS_MESSAGE_SUCCESS** *“IA 옵션 허용됨”*

- **NX_DHCPV6_STATUS_NO_ADDRS_AVAILABLE** *“IA 옵션 허용되지 않음 - 사용할 수 있는 주소 없음”*

- **NX_DHCPV6_STATUS_MESSAGE_NO_BINDING** *“IA 옵션 허용되지 않음 - 잘못된 클라이언트 요청”*

- **NX_DHCPV6_STATUS_MESSAGE_NOT_ON_LINK** *“IA 옵션 허용되지 않음 - 클라이언트가 연결되지 않음”*

- **NX_DHCPV6_STATUS_MESSAGE_USE_MULTICAST** *“IA 옵션 허용되지 않음 - 클라이언트가 멀티캐스트를 사용해야 함”*

- **NX_DHCPV6_STATUS_MESSAGE_NO_ADDRS_AVAILABLE** *IA 옵션 허용되지 않음 - 사용할 수 있는 주소 없음*

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID** 공급 업체 할당 ID로 서버 DUID를 만듭니다. DUID 형식은 NX_DHCPV6_DUID_TYPE_VENDOR_ASSIGNED로 설정해야 합니다.

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_LENGTH** 공급 업체 할당 ID의 상한을 설정합니다. 기본값은 48입니다.

- **NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID** DUID의 엔터프라이즈 유형을 프라이빗 공급 업체 유형으로 설정합니다.

- **NX_DHCPV6_PACKET_WAIT_OPTION** 서버 *nx_udp_socket_receive* 호출에 대한 대기 옵션을 정의합니다. 이는 소켓이 NetX Duo에서 수신 알림 콜백을 포함하므로 형식적입니다. 따라서 DHCPv6 서버에서 수신 함수를 호출할 때 패킷이 이미 큐에 배치되었습니다. 기본값은 1초(1 * NX_IP_PERIODIC_RATE)입니다.

- **NX_DHCPV6_SERVER_DUID_TYPE** 서버에서 클라이언트에 대한 모든 메시지에 포함되는 서버 DUID 유형을 정의합니다. 기본값은 링크 계층에 시간(NX_DHCPV6_SERVER_DUID_TYPE_LINK_TIME)을 더한 값입니다.

- **NX_DHCPV6_SERVER_HW_TYPE** DUID 링크 계층 및 링크 계층 더하기 시간 옵션에서 하드웨어 유형이 정의됩니다. 기본값은 NX_DHCPV6_SERVER_HARDWARE_TYPE_ETHERNET입니다.

- **NX_DHCPV6_PREFERENCE_VALUE** 기본 설정 옵션 값을 0에서 255 사이의 값으로 정의합니다. 여기서 값이 높을수록 동일한 이름의 DHCPv6 옵션의 기본 설정이 높습니다. 그러면 여러 DHCPv6 서버에서 IP 주소를 할당하는 데 사용할 수 있는 이 서버에서 제공하는 기본 설정에 어떤 기본 설정을 지정할지 클라이언트에 알려 줍니다. 255 값은 이 서버를 선택하도록 클라이언트에 지시합니다. 값이 0이면 클라이언트를 자유롭게 선택할 수 있습니다. 기본값은 영입니다.

- **NX_DHCPV6_MAX_OPTION_REQUEST_OPTIONS** 클라이언트 레코드에 저장할 수 있는 클라이언트 요청에서 최대 옵션 요청 수를 정의합니다. 기본값은 6입니다.

- **NX_DHCPV6_DEFAULT_T1_TIME** 클라이언트에서 IP 주소 갱신을 시작해야 하는 경우 클라이언트 주소 임대에서 서버에 의해 할당된 시간(초)입니다. 기본값은 2000초입니다.

- **NX_DHCPV6_DEFAULT_T2_TIME** 갱신 시도가 실패했다고 가정하여 클라이언트에서 해당 IP 주소 리바인딩을 시작해야 하는 경우 클라이언트 주소 임대에서 서버에 의해 할당된 시간(초)입니다. 기본값은 3000초입니다.

- **NX_DHCPV6_DEFAULT_PREFERRED_TIME** 할당된 클라이언트 IP 주소 임대가 사용되지 않는 경우 서버에 의해 할당된 시간(초)을 정의합니다. 기본값은 2 NX_DHCPV6_DEFAULT_T1_TIME입니다.

- **NX_DHCPV6_DEFAULT_VALID_TIME** 할당된 클라이언트 IP 주소 임대에서 서버에 의해 할당된 시간 만료 기간(초)을 정의합니다. 이 시간이 만료된 후에는 클라이언트 IP 주소가 올바르지 않습니다. 기본값은 2 NX_DHCPV6_DEFAULT_PREFERRED_TIME입니다.

- **NX_DHCPV6_STATUS_MESSAGE_MAX** 상태 옵션 메시지 필드에서 서버 메시지의 최대 크기를 정의합니다. 기본값은 100바이트입니다.

- **NX_DHCPV6_MAX_LEASES** 서버의 IP 임대 테이블의 크기를 정의합니다(예: 저장 가능한 임대할 수 있는 IPv6 주소의 최대 수). 기본적으로 이 값은 100입니다.

- **NX_DHCPV6_MAX_CLIENTS** 서버의 클라이언트 레코드 테이블 크기(예: 저장할 수 있는 최대 클라이언트 수)를 정의합니다. 이 값은 NX_DHCPV6_MAX_LEASES 값보다 작거나 같아야 합니다. 기본적으로 이 값은 120입니다.

- **NX_DHCPV6_PACKET_TIME_OUT** 패킷 할당 시 DHCPv6 서버 대기에 대한 타이머 틱의 대기 옵션을 정의합니다. 기본값은 3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND입니다.

- **NX_DHCPV6_PACKET_RECEIVE_WAIT** 서버 패킷 풀의 패킷 할당 호출에서 대기 옵션을 정의합니다. 기본값은 (3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND) 또는 3초입니다.

- **NX_DHCPV6_PACKET_SIZE** 서버 패킷 풀 패킷의 패킷 페이로드를 정의합니다. 기본값은 500바이트입니다.

- **NX_DHCPV6_PACKET_POOL_SIZE** 서버가 DHCPv6 메시지를 전송하기 위해 할당하는 패킷에 대한 서버 패킷 풀 크기를 정의합니다. 기본값은 (10 * NX_DHCPV6_PACKET_SIZE)입니다.

- **NX_DHCPV6_TYPE_OF_SERVICE** 이는 UDP 소켓 전송에 대한 서비스의 유형을 정의합니다. 이 값은 기본적으로 NX_IP_NORMAL입니다.

- **NX_DHCPV6_FRAGMENT_OPTION** 서버 소켓 조각화 옵션을 정의합니다. 기본값은 NX_DON’T_FRAGMENT입니다.

- **NX_DHCPV6_TIME_TO_LIVE** 패킷이 삭제되기 전에 서버의 DHCPv6 패킷이 '홉' 통과될 수 있는 라우터 수를 지정합니다. 기본값은 0x80으로 설정됩니다.

- **NX_DHCPV6_QUEUE_DEPTH** NetX Duo가 패킷을 삭제하기 전에 서버 UDP 소켓 수신 큐에 유지할 패킷 수를 지정합니다.