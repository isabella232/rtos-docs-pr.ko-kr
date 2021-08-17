---
title: 3장 - Azure RTOS NetX Duo DHCPv6 구성 옵션
description: Azure RTOS NetX Duo DHCPv6을 빌드하기 위한 몇 가지 구성 옵션이 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 129d1421215452448b1de4626fdeda530a5466bd63ed0c758676c3ad60f9d6fb
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782424"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a>3장 - Azure RTOS NetX Duo DHCPv6 구성 옵션

Azure RTOS NetX Duo DHCPv6을 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음 목록에서 각각에 대해 자세히 설명합니다.  
  
  
- **NX_DHCPV6_THREAD_PRIORITY** 클라이언트 스레드의 우선 순위입니다. 기본적으로 이 값은 클라이언트 스레드가 우선 순위 2에서 실행되도록 지정합니다.

- **NX_DHCPV6_MUTEX_WAIT** DHCPv6 클라이언트 뮤텍스의 배타적 잠금을 얻기 위한 제한 시간 옵션입니다. 기본값은 TX_WAIT_FOREVER입니다.

- **NX_DHCPV6_TICKS_PER_SECOND** 틱 비율(초)입니다. 이는 프로세서에 따라 다릅니다. 기본값은 100입니다.

- **NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL** IP 수명 타이머가 현재 IP 주소를 클라이언트에 할당한 시간을 업데이트하는 시간 간격(초)입니다. 기본적으로 이 값은 1입니다.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL** 세션 타이머에서 클라이언트가 서버와 통신하는 세션의 시간을 업데이트하는 시간 간격(초)입니다. 기본적으로 이 값은 1입니다.

- **NX_DHCPV6_MAX_IA_ADDRESS** 클라이언트 레코드에 추가할 수 있는 최대 IA 주소 수입니다. 기본값은 1입니다. 

- **NX_DHCPV6_NUM_DNS_SERVERS** 클라이언트 레코드에 저장할 DNS 서버 수입니다. 기본값은 2입니다.

- **NX_DHCPV6_NUM_TIME_SERVERS** 클라이언트 레코드에 저장할 시간 서버 수입니다. 기본값은 1입니다.

- **NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE** 클라이언트의 네트워크 도메인 이름을 보관할 클라이언트 레코드의 버퍼 크기입니다. 기본값은 30입니다.

- **NX_DHCPV6_TIME_ZONE_BUFFER_SIZE** 클라이언트의 표준 시간대를 보관할 클라이언트 레코드의 버퍼 크기입니다. 기본값은 10입니다.

- **NX_DHCPV6_MAX_MESSAGE_SIZE** 서버 회신의 옵션 상태 메시지를 보관할 클라이언트 레코드의 버퍼 크기입니다. 기본값은 100바이트입니다.

- **NX_DHCPV6_PACKET_TIME_OUT** 클라이언트 패킷 풀에서 패킷을 할당하는 제한 시간(초)입니다. 기본값은 3초입니다.

- **NX_DHCPV6_TYPE_OF_SERVICE** 이는 DHCPv6 클라이언트 소켓에서 UDP 패킷 전송에 대한 서비스의 유형을 정의합니다. 기본값은 **NX_IP_NORMAL** 입니다.

- **NX_DHCPV6_TIME_TO_LIVE** 패킷이 삭제되기 전에 네트워크 라우터에서 클라이언트 패킷이 전달되는 횟수입니다. 기본값은 0x80입니다.

- **NX_DHCPV6_QUEUE_DEPTH** NetX Duo가 패킷을 삭제하기 전에 클라이언트 UDP 소켓 수신 큐에 유지할 패킷 수를 지정합니다. 기본값은 5입니다.

## <a name="dhcpv6-message-transmission"></a>DHCPv6 메시지 전송

DHCPv6 메시지 전송에 매개 변수를 설정하기 위한 DHCPv6 클라이언트 옵션 세트가 있습니다. 이러한 항목은 다음과 같습니다. 

  - 초기 시간 제한

  - 첫 번째 전송에 대한 최대 지연

  - 최대 재전송 시간 제한 

  - 최대 재전송 횟수 

  - 서버 응답을 대기하는 최대 기간

이러한 매개 변수는 각 DHCPv6 클라이언트 메시지에 적용됩니다.

- SOLICIT

- REQUEST

- RENEW

- REBIND

- RELEASE

- DECLINE

- 확인

- INFORM

다음은 이러한 구성 가능한 옵션과 해당 기본값의 전체 목록입니다. 

values:

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

재전송 제한 시간에 제한이 없으면 메시지 재전송 횟수를 0으로 설정합니다. DHCPv6 클라이언트 메시지를 다시 전송하는 횟수에 제한이 없는 경우(다시 시도) 메시지 재전송 횟수를 0으로 설정합니다.

> [!NOTE]
> 제한 시간 또는 다시 시도 횟수에 관계 없이, IPv6 주소 유효 수명이 만료되면 IP 주소 테이블에서 제거되고 더 이상 클라이언트에서 사용할 수 없습니다. NetX Duo DHCPv6 클라이언트는 새 IPv6 주소를 요청하는 SOLICIT 메시지 요청 전송을 자동으로 시작합니다.