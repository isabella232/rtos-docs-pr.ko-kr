---
title: 챕터 2 - Azure RTOS NetX DHCP 서버 설치 및 사용
description: 이 챕터에서는 Azure RTOS NetX DHCP 서버 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 034a4d74c566fbfe94981a42b7e06e7f2ee79d25
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811605"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-dhcp-server"></a>챕터 2 - Azure RTOS NetX DHCP 서버 설치 및 사용

이 챕터에서는 Azure RTOS NetX DHCP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS NetX DHCP 서버는 [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/)에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다. 이 패키지에는 다음과 같이 두 개의 원본 파일과 이 문서가 포함된 PDF 파일이 포함되어 있습니다.

- **nx_dhcp_server.h**: NetX DHCP 서버용 헤더 파일
- **nx_dhcp_server.c**: NetX DHCP 서버용 C 원본 파일
- **nx_dhcp_server.pdf**: NetX DHCP 서버의 PDF 설명
- **demo_netx_dhcp_server.c**: NetX DHCP 서버 데모

## <a name="dhcp-installation"></a>DHCP 설치

NetX DHCP 서버를 사용하려면 이전에 언급한 전체 배포를 NetX가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX가 " *\threadx\arm7\green*" 디렉터리에 설치된 경우 *nx_dhcp_server.h* 및 *nx_dhpc_server.c* 파일을 이 디렉터리에 복사해야 합니다.

## <a name="using-netx-dhcp-server"></a>NetX DHCP 서버 사용

NetX DHCP 서버는 사용하기 쉽습니다. 기본적으로 ThreadX와 NetX를 각각 사용하기 위해서는 애플리케이션 코드에 *tx_api.h* 및 *nx_api.h* 가 포함된 후 *nx_dhcp_server.h* 가 포함되어야 합니다. *nx_dhcp_server.h* 가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 DHCP 함수 호출을 수행할 수 있습니다. 애플리케이션은 빌드 프로세스에 *nx_dhcp_server.c* 도 포함해야 합니다. 이 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일해야 하며, 해당 개체 형식은 애플리케이션의 파일과 함께 연결해야 합니다. NetX DHCP 서버 사용에 대한 자세한 내용은 다음 섹션 [NetX DHCP의 요구 사항](#requirements-of-the-netx-dhcp-server) [NetX DHCP 서버의 제약 조건](#constraints-of-the-netx-dhcp-server)을 참조하세요.

> [!NOTE]
> DHCP는 NetX UDP 서비스를 사용하므로 DHCP를 사용하기 전에 *nx_udp_enable* 을 호출하여 UDP를 사용해야 합니다.

## <a name="requirements-of-the-netx-dhcp-server"></a>NetX DHCP 서버의 요구 사항

NetX DHCP 서버는 잘 알려진 DHCP 포트 67에 UDP 소켓 포트가 할당되어야 합니다. DHCP 서버를 만들려면 애플리케이션이 최소 548바이트의 패킷 페이로드와 IP, UDP 및 이더넷 헤더(총 44바이트, 4바이트 정렬)가 포함된 패킷 풀을 만들어야 합니다.

서버와 클라이언트 모두 이더넷 하드웨어 주소 설정을 사용한다고 가정합니다.

- **하드웨어 종류**: 1
- **하드웨어 길이**: 6
- **Hops**: 0

### <a name="multiple-client-sessions"></a>여러 클라이언트 세션

NetX DHCP 서버는 활성 DHCP 클라이언트의 테이블과 클라이언트의 '상태'를 유지하여 여러 클라이언트 세션을 처리 할 수 있습니다. DHCP 상태는 INIT, BOOT, SELECTING, REQUESTING, RENEWING 등입니다. 다음 클라이언트 메시지를 받기 전에 세션 제한 시간이 만료되면 해당 클라이언트가 IP 임대에 바인딩되지 않은 경우 서버는 클라이언트 세션 데이터를 지우고 할당된 IP 주소를 사용 가능한 풀로 다시 반환합니다. 서버가 동일한 클라이언트로부터 여러 DISCOVER 메시지를 수신하는 경우, 서버는 세션 제한 시간을 재설정하고 후속 REQUEST 메시지를 수락하도록 클라이언트용 IP 주소를 유지합니다.

NetX DHCP 서버는 또한 단일 상태 클라이언트 DHCP 요청을 수락합니다. 예를 들어, 클라이언트는 REQUEST 메시지만 보냅니다. 이는 클라이언트가 이전에 DHCP 서버에서 IP 임대를 할당받았다고 가정합니다.

### <a name="setting-interface-specific-network-parameters-server-responses"></a>인터페이스별 네트워크 매개 변수 서버 응답 설정

애플리케이션은 *nx_dhcp_set_interface_network_parameters* 서비스를 사용하여 DHCP 클라이언트 요청을 처리하는 각 인터페이스에 대해 라우터, 서브넷 마스크 및 DNS 서버 매개 변수를 설정할 수 있습니다. 그렇지 않으면 이러한 매개 변수는 각각 서버의 기본 인터페이스, DHCP 네트워크 서브넷 및 DHCP 서버 IP 주소에 있는 IP 게이트웨이로 기본 설정됩니다.

DHCP 서버는 DHCP 클라이언트에 보내는 DHCP 메시지의 옵션 데이터에 이러한 매개 변수를 포함합니다.

### <a name="assigning-ip-addresses-to-the-client"></a>클라이언트에 IP 주소 할당

클라이언트 DISCOVER 메시지가 요청된 IP 주소를 지정하지 않으면 DHCP 서버가 자체 풀의 IP 주소를 사용할 수 있습니다. 서버가 사용 가능한 IP 주소가 없는 경우 클라이언트에게 NACK 메시지를 보냅니다.

NetX DHCP 서버는 IP 주소를 사용할 수 있고 서버 IP 주소 데이터베이스에서 찾을 수 있는 한 클라이언트 REQUEST 메시지에서 요청된 IP 주소를 부여합니다. 애플리케이션은 *nx_dhcp_create_server_ip_address_list* 서비스를 사용하여 DHCP 클라이언트에 할당할 수 있는 서버의 사용 가능한 IP 주소 목록을 만듭니다. 서버에 요청된 IP 주소가 없거나 다른 호스트에 할당된 경우 클라이언트에게 NACK 메시지를 보냅니다.

DHCP 서버가 클라이언트 요청을 수신하면 DHCP 메시지의 클라이언트 MAC 주소 필드에 있는 클라이언트 MAC 주소를 사용하여 클라이언트를 고유하게 식별합니다. 클라이언트가 MAC 주소를 변경하거나 다른 서브넷으로 이동하면 RELEASE 메시지를 서버로 보내 IP 주소를 사용 가능한 풀로 다시 반환하고 INIT 상태의 새 IP 주소를 요청해야 합니다.

자세한 내용은 **간단한 예제 시스템** 섹션의 그림 1.1을 참조하세요. DHCP 서버 인스턴스에 저장되는 IP 주소의 수는 DHCP 서버 제어 블록의 서버 주소 배열 크기로 제한되며 구성 가능한 옵션 NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE에 의해 정의됩니다.

### <a name="ip-address-lease-times"></a>IP 주소 임대 시간

DHCP 서버는 또한 해당 임대 시간이 구성 가능한 옵션 NX_DHCP_DEFAULT_LEASE_TIME에 정의된 서버 기본 임대 시간보다 작은 경우 요청 클라이언트 임대 시간을 수락합니다. 임대 시간이 무한대(0xFFFFFFFF)가 아닌 경우 클라이언트에 할당된 갱신 및 리바인딩 시간은 각각 임대 시간의 50% 및 85%이며, 이 경우 갱신 및 리바인딩 시간도 무한대로 설정됩니다.

### <a name="dhcp-server-timeouts"></a>DHCP 서버 시간 제한

DHCP 서버에는 세션이 완료되지 않은 경우 다음 DHCP 클라이언트 메시지를 기다리기 위해 사용자가 구성할 수 있는 세션 시간 제한인 NX_DHCP_CLIENT_SESSION_TIMEOUT이 있습니다. 제한 시간은 이전에 보낸 메시지와 동일한 메시지에 관계없이 서버가 클라이언트로부터 다음 메시지를 수신할 때 초기화됩니다.

### <a name="internal-error-handling"></a>내부 오류 처리

DHCP 서버는 *nx_dhcp_listen_for_messages* 함수에서 DHCP 클라이언트 패킷을 수신하고 처리합니다. 패킷이 잘못되었거나 DHCP 서버에 내부 오류가 발생하는 경우 이 함수는 현재 DHCP 클라이언트 패킷 처리를 중단합니다. n *x_dhcp_listen_for_messages* 는 오류 상태를 반환합니다. DHCP 서버 스레드는 다음 DHCP 클라이언트 메시지를 수신하기 위해 이 함수를 호출하기 전에 ThreadX 스케줄러의 제어를 잠시 포기합니다. 현재 릴리스에는 *nx_dhcp_listen_for_messages* 의 오류 상태 반환에 대한 로깅 지원이 없습니다.

### <a name="option-55-parameter-request-list"></a>옵션 55: 매개 변수 요청 목록

NetX DHCP 서버는 클라이언트에 다시 전송하는 OFFER 및 DHCPACK 메시지에서 매개 변수 요청 옵션(55) 목록에 로드하는 옵션 세트를 사용하여 구성해야 합니다. 이러한 옵션에는 클라이언트 네트워크에 대한 네트워크 중요 구성 데이터가 포함되어야 하며 기본적으로 라우터 IP 주소, 서브넷 마스크 및 DNS 서버로 정의됩니다. 옵션 목록은 공백으로 구분된 목록이며 사용자 구성 가능한 NX_DHCP_DEFAULT_SERVER_OPTION_LIST에 정의되어 있습니다. 이 목록에 지정된 옵션의 수는 사용자 정의된 NX_DHCP_DEFAULT_OPTION_LIST_SIZE와 동일해야 합니다.

## <a name="constraints-of-the-netx-dhcp-server"></a>NetX DHCP 서버의 제약 조건

### <a name="dhcp-messages"></a>DHCP 메시지

NetX DHCP 서버는 클라이언트에 IP 주소를 부여하기 전에 IP 주소가 네트워크의 다른 곳에서 할당되지 않았는지 확인하지 않습니다. DHCP 서버가 여러 개 있는 경우 실제로 그럴 수 있습니다. *RFC 2131에 따라 IP 주소가 네트워크에서 고유한지 확인하는 것은 클라이언트의 책임입니다*(예: 주소 ping). 그렇지 않은 경우 서버는 클라이언트에서 데이터베이스를 업데이트하기 위해 IP 주소와 함께 DECLINE 메시지를 받아야 합니다.

NetX DHCP 서버는 FORCE_RENEW 메시지를 발행하지 않습니다. IP 주소 임대를 갱신하는 것은 DHCP 클라이언트에 달려 있습니다. 그러나 DHCP 서버는 데이터베이스에 할당된 모든 IP 주소의 남은 시간을 모니터링합니다. IP 주소 임대가 만료되는 경우 IP 주소는 사용 가능한 IP 주소의 풀로 반환됩니다. 따라서 클라이언트는 IP 주소 임대를 적극적으로 갱신/리바인딩하는 것은 클라이언트에 달려 있습니다.

클라이언트가 IP 임대에 부여("바인딩")되거나 기존 임대가 갱신되는 즉시 세션 데이터가 지워집니다. 클라이언트 패킷이 위조를 증명하거나 클라이언트에서 응답 간에 시간이 초과되면 세션 데이터가 지워집니다.

### <a name="saving-data-between-reboots"></a>재부팅 사이 데이터 저장

NetX DHCP 서버는 클라이언트 레코드 테이블에 DHCP 요청 매개 변수를 포함한 클라이언트 데이터를 저장합니다. 이 테이블은 비휘발성 메모리에 저장되지 않으므로, DHCP 서버 호스트를 다시 부팅해야 하는 경우 재부팅하는 사이 해당 정보는 저장되지 않습니다.

NetX DHCP 서버는 IP 주소 임대 데이터를 IP 주소 테이블에 저장합니다. 이 테이블은 비휘발성 메모리에 저장되지 않으므로, DHCP 서버 호스트를 다시 부팅해야 하는 경우 재부팅하는 사이 해당 정보는 저장되지 않습니다.

### <a name="relay-agents"></a>릴레이 에이전트

NetX DHCP 서버는 네트워크 외부 DHCP 요청을 지원하지 않으므로 '릴레이 에이전트' 필드의 IP 주소가 0으로 구성됩니다.

## <a name="small-example-system"></a>간단한 예제 시스템

NetX DHCP 서버를 사용하는 것이 얼마나 쉬운지 보여주는 예제가 아래에 표시된 그림 1.1에 설명되어 있습니다. 이 예제에서는 5행에 있는 DHCP 포함 파일 *nx_dhcp_server.h* 를 가져옵니다. DHCP 서버 스레드 스택 크기, IP 스레드 스택 크기 및 테스트 스레드 스택 크기는 모두 7-13행에 정의되어 있습니다.

먼저 57행의 "*test_thread_entry*" 함수를 사용하여 DHCP 서버를 중지, 다시 시작 그리고 최종적으로 삭제하기 위한 선택적 테스트 스레드 작업을 만듭니다. DHCP 서버 제어 블록 "*dhcp_server*"는 20행에서 전역 변수로 정의됩니다. 서버 패킷 풀은 최소한 표준 DHCP 메시지(548바이트 + IP 및 UDP 헤더 바이트) 정도의 페이로드가 있는 패킷으로 생성됩니다. DHCP 서버용 IP 인스턴스를 성공적으로 만든 후 애플리케이션은 96행에 DHCP 서버를 만듭니다. 그 다음, 애플리케이션은 서버 IP 인스턴스가 UDP를 사용하도록 설정합니다. DHCP 서버를 시작하기 전에 사용 가능한 IP 주소 목록은 *nx_dhcp_create_server_ip_address_list* 서비스를 사용하여 137행에 만들어집니다. 네트워크 구성 매개 변수는 *nx_dhcp_set_interface_network_parameters* 서비스를 사용하여 다음 138행에 설정됩니다. 애플리케이션이 141행에서 *nx_dhcp_server_start* 를 호출하면 DHCP 서버 서비스를 사용할 수 있습니다. 테스트 스레드 작업은 DHCP 서버를 중지하고 다시 시작하는 방법을 보여줍니다.

```c
/* This is a small demo of NetX DHCP Server for the high-performance NetX TCP/IP stack. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE       2048
#define     DEMO_SERVER_STACK_SIZE     2048
#define     SERVER_IP_ADDRESS_LIST     "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD             1000
#define     PACKET_POOL_SIZE           (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK     2048

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD          test_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_DHCP_SERVER     dhcp_server;

/* Define the counters used in the demo application... */

ULONG             state_changes;

/* Define thread prototypes. */

void     test_thread_entry(ULONG thread_input);
void     nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the test thread. */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
                pointer, TEST_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the DHCP Server packet pool. */
    status = nx_packet_pool_create(&server_pool, "NetX Main Packet Pool",
                                PACKET_PAYLOAD, pointer, PACKET_POOL_SIZE);
                                pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance. */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
                        0xFFFFFF00UL, &server_pool, nx_etherDriver_mcf5485, pointer,
                        SERVER_IP_THREAD_STACK, 1);

    pointer = pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors. */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance. */
    status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic. */
    status = nx_udp_enable(&server_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility. */
    status = nx_icmp_enable(&server_ip);

    /* Check for errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

    status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);
    status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                        NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                        IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server. */
    status = nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread. */
void     test_thread_entry(ULONG thread_input)
{

UINT     status;
UINT     keep_spinning;

    /* Just let the test thread be idle till we're ready to shut things down. */
    keep_spinning = 1;
    while(keep_spinning)
    {
        tx_thread_sleep(300);
    }

    printf("Stopping the server...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(500);

    printf("Starting the server...\n");
    status = nx_dhcp_server_start(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server start. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(600);

    printf("Stopping the server for good...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(200);

    printf("Deleting the server...\n");
    status = nx_dhcp_server_delete(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server delete. Status 0x%x\r\n", status);
        return;
    }
}
```

그림 1.1 NetX DHCP 서버 애플리케이션 예

## <a name="configuration-options"></a>구성 옵션

NetX DHCP 서버를 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음 목록에서 각각에 대해 자세히 설명합니다.  
  
- **NX_DISABLE_ERROR_CHECKING**: 이 옵션은 기본 DHCP 오류 검사를 제거합니다. 일반적으로 애플리케이션이 디버깅된 후에 사용됩니다.  
- **NX_DHCP_SERVER_THREAD_PRIORITY**:이 옵션은 DHCP 서버 스레드의 우선 순위를 지정합니다. 기본적으로 이 값은 DHCP 스레드가 우선 순위 2에서 실행되도록 지정합니다.
- **NX_DHCP_TYPE_OF_SERVICE**:이 옵션은 DHCP UDP 요청에 필요한 서비스 유형을 지정합니다. 기본적으로 이 값은 일반 IP 패킷 서비스를 나타내는 NX_IP_NORMAL로 정의됩니다.
- **NX_DHCP_FRAGMENT_OPTION**: DHCP UDP 요청에 대한 조각을 사용하도록 설정합니다. 기본적으로 이 값은 UDP 조각화를 사용하지 않도록 설정하는 NX_DONT_FRAGMENT로 설정됩니다.
- **NX_DHCP_TIME_TO_LIVE**: 패킷이 삭제되기 전에 통과할 수 있는 라우터 수를 지정합니다. 기본값은 0x80입니다.
- **NX_DHCP_QUEUE_DEPTH**: 큐를 플러시하기 전에 DHCP 서버 소켓이 보관하는 패킷 수를 지정합니다. 기본값은 5입니다.
- **NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: NetX DHCP 서버가 패킷 풀에서 패킷을 할당할 때까지 대기하는 타이머 틱의 시간 제한을 지정합니다. 기본값은 NX_IP_PERIODIC_RATE로 설정됩니다.
- **NX_DHCP_SUBNET_MASK**: DHCP 클라이언트를 구성해야 하는 서브넷 마스크입니다. 기본값은 0xFFFFFF00으로 설정됩니다.
- **NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: DHCP 서버 빠른 타이머가 남은 세션 시간을 확인하고 시간이 초과된 세션을 처리하기 위한 타이머 틱의 시간 초과 기간입니다.
- **NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: DHCP 서버 느린 타이머가 남은 IP 주소 임대 시간을 확인하고 시간이 초과된 임대를 처리하기 위한 타이머 틱의 시간 초과 기간입니다.
- **NX_DHCP_CLIENT_SESSION_TIMEOUT**: DHCP 서버가 다음 DHCP 클라이언트 메시지를 수신하기 위해 대기하는 타이머 틱의 시간 초과 기간입니다.
- **NX_DHCP_DEFAULT_LEASE_TIME**: DHCP 클라이언트에 할당된 IP 주소 임대 시간(초)이며 클라이언트에도 할당된 갱신 및 리바인딩 시간을 계산하는 기준입니다. 기본값은 0xFFFFFFFF(infinity)로 설정됩니다.
- **NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: 클라이언트에 할당하기 위해 사용 가능한 IP 주소를 보관하기 위한 DHCP 서버 배열의 크기입니다. 기본값은 20입니다.
- **NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: 클라이언트 레코드를 보관하기 위한 DHCP 서버 배열의 크기입니다. 기본값은 50입니다.
- **NX_DHCP_CLIENT_OPTIONS_MAX**: 현재 세션의 매개 변수 요청 목록에 요청된 모든 옵션을 보관하기 위한 DHCP 클라이언트 인스턴스의 배열 크기입니다. 기본값은 12입니다.
- **NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: 매개 변수 요청 목록에서 현재 DHCP 클라이언트에 제공할 DHCP 서버의 기본 옵션 목록을 보관하는 버퍼입니다. 기본값은 "1 3 6"입니다.
- **NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: DHCP 서버의 기본 옵션 목록을 보관할 배열의 크기입니다. 기본값은 3입니다.
- **NX_DHCP_SERVER_HOSTNAME_MAX**: 서버 호스트 이름을 보관하는 버퍼의 크기입니다. 기본값은 32입니다.
- **NX_DHCP_CLIENT_HOSTNAME_MAX**: 현재 DHCP 서버 클라이언트 세션에서 클라이언트 호스트 이름을 보관하는 버퍼의 크기입니다. 기본값은 32입니다.
