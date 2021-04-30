---
title: 2장 - Azure RTOS NetX PPP(지점 간 프로토콜) 설치 및 사용
description: 이 장에서는 Azure RTOS NetX PPP(지점 간 프로토콜) 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40f09da31f5541208c3b2cc0eeb54850b3d71f7c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811472"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-point-to-point-protocol-ppp"></a>2장 - Azure RTOS NetX PPP(지점 간 프로토콜) 설치 및 사용

이 장에서는 Azure RTOS NetX PPP(지점 간 프로토콜) 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS NetX PPP(지점 간 프로토콜) 패키지는 <https://github.com/azure-rtos/netx>에서 사용할 수 있습니다. 패키지에는 다음 파일이 포함되어 있습니다.

- **nx_ppp.h**: NetX용 PPP에 대한 헤더 파일
- **nx_ppp.c**: NetX용 PPP에 대한 C 원본 파일
- **nx_ppp.pdf**: NetX용 PPP에 대한 PDF 설명
- **demo_netx_ppp.c**: NetX PPP 데모

## <a name="ppp-installation"></a>PPP 설치

NetX용 PPP를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX가 “ *\threadx\arm7\green*” 디렉터리에 설치된 경우 *nx_ppp.h* 및 *nx_ppp.c* 파일을 이 디렉터리에 복사해야 합니다.

## <a name="using-ppp"></a>PPP 사용

NetX용 PPP를 사용하는 것은 쉽습니다. 기본적으로 애플리케이션 코드는 ThreadX 및 NetX를 각각 사용하기 위해 *tx_api.h* 및 *nx_api.h* 를 포함한 후 *nx_ppp.h* 를 포함해야 합니다. *nx_ppp.h* 가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 PPP 함수 호출을 수행할 수 있습니다. 애플리케이션은 빌드 프로세스에 *nx_ppp.c* 도 포함해야 합니다. 이 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 해당 개체 형식은 애플리케이션의 파일과 함께 연결되어야 합니다. 이는 NetX PPP를 사용하는 데 필요합니다.

## <a name="using-modems"></a>모뎀 사용

인터넷에 연결하는 데 모뎀이 필요한 경우 NetX PPP 제품을 사용하기 위해 몇 가지 특별한 고려 사항이 있습니다. 기본적으로 모뎀을 사용하면 통신 손실에 대한 추가 초기화 논리가 도입됩니다. 또한 대부분의 추가 모뎀 논리는 NetX PPP의 컨텍스트 외부에서 수행됩니다. 모뎀과 함께 NetX PPP를 사용하는 기본 흐름은 다음과 같습니다.

1. 모뎀 초기화

1. ISP(인터넷 서비스 공급자)에 전화 걸기

1. 연결 대기

1. UserID 프롬프트 대기

1. NetX PPP 시작[PPP 작동 중]

1. 통신 손실

1. NetX PPP 중지(또는 nx_ppp_restart를 통해 다시 시작)

### <a name="initialize-modem"></a>모뎀 초기화

애플리케이션의 하위 수준 직렬 출력 루틴을 사용하여 모뎀은 일련의 ASCII 문자 명령을 통해 초기화됩니다(자세한 내용은 모뎀 설명서 참조).

### <a name="dial-internet-service-provider"></a>인터넷 서비스 공급자에 전화 걸기

애플리케이션의 하위 수준 직렬 출력 루틴을 사용하여 모뎀은 ISP에 전화를 걸도록 지시합니다. 예를 들어, 다음은 123-4567 번호로 ISP에 전화를 거는 데 사용되는 ASCII 문자열의 일반적인 예입니다.

“ATDT123456\r”

### <a name="wait-for-connection"></a>연결 대기

이 때 애플리케이션은 모뎀에서 연결이 설정되었다는 표시를 받을 때까지 기다립니다. 이는 애플리케이션의 하위 수준 직렬 입력 루틴에서 문자를 검색하여 수행됩니다. 일반적으로 모뎀은 연결이 설정되면 ASCII 문자열 "CONNECT"를 반환합니다.

### <a name="wait-for-user-id-prompt"></a>사용자 ID 프롬프트 대기

연결이 설정되면 애플리케이션은 ISP의 초기 로그인 요청을 기다려야 합니다. 일반적으로 “Login?”과 같은 ASCII 문자열의 형식을 사용합니다.

### <a name="start-netx-ppp"></a>NetX PPP 시작

이 때 NetX PPP를 시작할 수 있습니다. 이 작업은 *nx_ppp_create* 서비스에 이어 *nx_ip_create* 서비스를 호출하여 수행됩니다. PAP를 사용하도록 설정하고 PPP IP 주소를 설정하는 추가 서비스가 필요할 수도 있습니다. 자세한 내용은 이 가이드의 다음 섹션을 검토하세요.

### <a name="loss-of-communication"></a>통신 손실

PPP가 시작되면 PPP가 아닌 정보는 *nx_ppp_create* 서비스에 지정된 애플리케이션의 "잘못된 패킷 처리" 루틴으로 전달됩니다. 일반적으로 모뎀은 ISP와의 통신이 끊어지면 “NO CARRIER”와 같은 ASCII 문자열을 보냅니다. 애플리케이션이 이러한 정보가 포함된 비 PPP 패킷을 수신하는 경우 NetX PPP 인스턴스를 중지하거나 *nx_ppp_restart* API를 통해 PPP 상태 시스템을 다시 시작해야 합니다.

### <a name="stop-netx-ppp"></a>NetX PPP 중지

NetX PPP를 중지하는 것은 매우 간단합니다. 기본적으로 생성된 모든 소켓은 바인딩 해제되고 삭제되어야 합니다. 다음으로, *nx_ip_delete* 서비스를 통해 IP 인스턴스를 삭제합니다. IP 인스턴스가 삭제되면 *nx_ppp_delete* 서비스를 호출하여 PPP 중지 프로세스를 완료해야 합니다. 이 때 애플리케이션은 ISP와의 통신을 다시 설정하려고 할 수 있습니다.

## <a name="small-example-system"></a>작은 예제 시스템

NetX PPP를 사용하는 것이 얼마나 쉬운지 보여주는 예제는 아래에 표시된 그림 1.1에 설명되어 있습니다. 이 예제에서는 PPP 포함 파일 *nx_ppp.h* 를 3줄에서 가져옵니다. 다음으로, PPP는 56줄의 *”tx_application_define*”에 만들어집니다. PPP 제어 블록 “*my_ppp*”는 이전에 9줄에서 전역 변수로 정의되었습니다. 

>[!NOTE]
>IP 인스턴스를 만들기 전에 PPP를 만들어야 합니다. PPP와 IP를 성공적으로 만든 후 스레드 "*my_thread*"는 PPP 링크가 98줄에서 활성화될 때까지 대기합니다. 104줄에서 PPP와 NetX는 모두 완전히 작동합니다.

이 예제에 표시되지 않은 항목 중 하나는 애플리케이션의 직렬 바이트 수신 ISR입니다. “*my_ppp*” 및 입력 매개 변수로 수신된 바이트를 사용하여 *nx_ppp_byte_receive* 를 호출해야 합니다.

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nx_ppp.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_PPP                  my_ppp;

/* Define function prototypes. */

void    my_thread_entry(ULONG thread_input);
void    my_serial_driver_byte_output(UCHAR byte);
void    my_invalid_packet_handler(NX_PACKET *packet_ptr);
 
/* Define main entry point. */
intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
 }


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

/* Setup the working pointer. */
pointer =  (CHAR *) first_unused_memory;

/* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                  pointer, DEMO_STACK_SIZE, 
                  2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                    1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error. */
    if (status)
        error_counter++;

    /* Create a PPP instance. */
    status = nx_ppp_create(&my_ppp, “My PPP”, &my_ip, pointer, 1024, 2, 
                           &my_pool, my_invalid_packet_handler, my_serial_driver_byte_output);
    pointer =  pointer + 1024;
    /* Check for PPP creation pool. */
    if (status)
        error_counter++;

    /* Create an IP instance with the PPP driver. */
    status = nx_ip_create(&my_ip,"My NetX IP Instance", 
                           IP_ADDRESS(216,2,3,1), 0xFFFFFF00, &my_pool, 
                           nx_ppp_driver, pointer, DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors. */
    if (status)
        error_counter++;

    /* Enable ICMP for my IP Instance. */
    status =  nx_icmp_enable(&my_ip);

    /* Check for ICMP enable errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}

/* Define my thread. */
void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       ip_status;
NX_PACKET   *my_packet;

/* Wait for the PPP link in my_ip to become enabled. */
    status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,&ip_status,3000);

    /* Check for IP status error. */
    if (status) 
        return;

    /* Link is fully up and operational. All NetX activities 
    are now available. */

}
```
## <a name="configuration-options"></a>구성 옵션

NetX용 PPP를 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음 목록에서는 각각에 대해 자세히 설명합니다.

- **NX_DISABLE_ERROR_CHECKING**: 정의된 이 옵션은 기본 PPP 오류 검사를 제거합니다. 일반적으로 애플리케이션이 디버깅된 후에 사용됩니다.
- **NX_PPP_PPPOE_ENABLE**: 정의된 경우 PPP는 이더넷을 통해 패킷을 전송할 수 있습니다.
- **NX_PPP_BASE_TIMEOUT**: PPP 이벤트를 확인할 때 PPP 스레드 작업이 활성화되는 기간의 비율(타이머 틱 단위)을 정의합니다. 기본값은 1*NX_IP_PERIODIC_RATE(100틱)입니다.
- **NX_PPP_DISABLE_INFO**: 정의된 경우 내부 PPP 정보 수집을 사용할 수 없습니다.
- **NX_PPP_DEBUG_LOG_ENABLE**: 정의된 경우 내부 PPP 디버그 로그가 활성화됩니다.
- **NX_PPP_DEBUG_LOG_PRINT_ENABLE**: 정의된 경우 *stdio* 에 대한 내부 PPP 디버그 로그 *printf* 가 활성화됩니다. 디버그 로그도 활성화된 경우에만 유효합니다.
- **NX_PPP_DEBUG_LOG_SIZE**: 디버그 로그의 크기(디버그 로그의 항목 수)입니다. 마지막 항목에 도달하면 디버그 캡처가 첫 번째 항목으로 래핑하고 이전에 캡처된 모든 데이터를 덮어씁니다. 기본값은 50입니다.
- **NX_PPP_DEBUG_FRAME_SIZE**: 수신된 패킷 페이로드에서 캡처되어 디버그 출력에 저장된 최대 데이터 양입니다. 기본값은 50입니다.
- **NX_PPP_DISABLE_CHAP**: 정의된 경우 MD5 다이제스트 논리를 포함하여 내부 PPP CHAP 논리가 제거됩니다.
- **NX_PPP_DISABLE_PAP**: 정의된 경우 내부 PPP PAP 논리가 제거됩니다.
- **NX_PPP_DNS_OPTION_DISABLE**: 정의된 경우 IPCP 응답에서 기본 DNS 서버 옵션이 비활성화됩니다.  기본적으로 이 옵션은 정의되지 않습니다(DNS 옵션이 설정됨).
- **NX_PPP_DNS_ADDRESS_MAX_RETRIES**: PPP 호스트가 IPCP 상태의 피어에서 DNS 서버 주소를 요청하는 횟수를 지정합니다. NX_PPP_DNS_OPTION_DISABLE이 정의된 경우에는 영향을 주지 않습니다. 기본값은 2입니다.
- **NX_PPP_HASHED_VALUE_SIZE**: CHAP 인증에 사용되는 "해시된 값" 문자열의 크기를 지정합니다. 기본값은 16바이트로 설정되지만 *nx_ppp.h* 를 포함하기 전에 다시 정의할 수 있습니다.
- **NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: 다른 LCP 구성 요청 메시지를 보내기 전에 PPP가 제한 시간을 초과하는 경우 최대 재시도 횟수를 정의합니다. 이 숫자에 도달하면 PPP 핸드셰이크가 중단되고 링크 상태가 중단됩니다. 기본값은 20입니다.
- **NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: 다른 PAP 인증 요청 메시지를 보내기 전에 PPP가 제한 시간을 초과하는 경우 최대 재시도 횟수를 정의합니다. 이 숫자에 도달하면 PPP 핸드셰이크가 중단되고 링크 상태가 중단됩니다. 기본값은 20입니다.
- **NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: 다른 CHAP 챌린지 메시지를 보내기 전에 PPP가 제한 시간을 초과하는 경우 최대 재시도 횟수를 정의합니다. 이 숫자에 도달하면 PPP 핸드셰이크가 중단되고 링크 상태가 중단됩니다. 기본값은 20입니다.
- **NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: 다른 IPCP 구성 요청 메시지를 보내기 전에 PPP가 제한 시간을 초과하는 경우 최대 재시도 횟수를 정의합니다. 이 숫자에 도달하면 PPP 핸드셰이크가 중단되고 링크 상태가 중단됩니다. 기본값은 20입니다.
- **NX_PPP_MRU**: PPP의 최대 수신 단위(MRU)를 지정합니다. 기본적으로 이 값은 1,500바이트(최솟값)입니다. 이 정의는 *nx_ppp.h* 를 포함하기 전에 애플리케이션에서 설정할 수 있습니다.
- **NX_PPP_MINIMUM_MRU**: LCP 구성 요청 메시지에서 받은 최소 MRU를 지정합니다. 기본적으로 이 값은 1,500바이트(최솟값)입니다. 이 정의는 *nx_ppp.h* 를 포함하기 전에 애플리케이션에서 설정할 수 있습니다.
- **NX_PPP_NAME_SIZE**: 인증에 사용되는 "이름" 문자열의 크기를 지정합니다. 기본값은 32바이트로 설정되지만 *nx_ppp.h를 포함하기 전에 다시 정의할 수 있습니다.
- **NX_PPP_PASSWORD_SIZE**: 인증에 사용되는 "암호" 문자열의 크기를 지정합니다. 기본값은 32바이트로 설정되지만 *nx_ppp.h* 를 포함하기 전에 다시 정의할 수 있습니다.
- **NX_PPP_PROTOCOL_TIMEOUT**: PPP 작업이 PPP 프로토콜 요청 메시지에 대한 응답을 수신하는 대기 옵션(초)을 정의합니다. 기본값은 4초입니다.
- **NX_PPP_RECEIVE_TIMEOUTS**: PPP 메시지 스트림에서 다음 문자를 받기 위해 대기하는 PPP 스레드 작업의 시간 초과 횟수를 정의합니다. 이후에는 PPP가 패킷을 해제하고 다음 PPP 메시지를 받기 위해 대기를 시작합니다. 기본값은 4입니다.
- **NX_PPP_SERIAL_BUFFER_SIZE**: 수신 문자 직렬 버퍼의 크기를 지정합니다. 기본적으로 이 값은 3,000바이트입니다. 이 정의는 *nx_ppp.h* 를 포함하기 전에 애플리케이션에서 설정할 수 있습니다.
- **NX_PPP_TIMEOUT**: 데이터를 전송하는 패킷과 IP 계층에 보낼 패킷에 PPP 직렬 데이터를 할당하는 대기 옵션(타이머 틱 단위)을 정의합니다. 기본값은 4*NX_IP_PERIODIC_RATE(400틱)입니다.
- **NX_PPP_THREAD_TIME_SLICE**: PPP 스레드에 대한 시간 조각 옵션입니다. 기본적으로 이 값은 TX_NO_TIME_SLICE입니다. 이 정의는 *nx_ppp.h* 를 포함하기 전에 애플리케이션에서 설정할 수 있습니다.
- **NX_PPP_VALUE_SIZE**: CHAP 인증에 사용되는 "값" 문자열의 크기를 지정합니다. 기본값은 32바이트로 설정되지만 nx_ppp.h를 포함하기 전에 다시 정의할 수 있습니다.
