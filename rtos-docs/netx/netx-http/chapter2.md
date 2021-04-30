---
title: 2장 - NetX HTTP 설치 및 사용
description: 이 장에서는 NetX HTTP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db621e38e9d2324ca3ce2398aee9f729b05886ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811532"
---
# <a name="chapter-2---installation-and-use-of-netx-http"></a>2장 - NetX HTTP 설치 및 사용

이 장에서는 NetX HTTP 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS NetX는 [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx)에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다.

- **nx_http_client.h** NetX용 HTTP 클라이언트의 헤더 파일
- **nx_http_server.h** NetX용 HTTP 서버의 헤더 파일
- **nx_http_client.c** NetX용 HTTP 클라이언트의 C 원본 파일
- **nx_http_server.c** NetX용 HTTP 서버의 C 원본 파일
- **nx_md5.c** MD5 다이제스트 알고리즘
- **filex_stub.h** FileX가 없는 경우 스텁 파일
- **nx_http.pdf** NetX용 HTTP의 설명
- **demo_netx_http.c** NetX HTTP 데모

## <a name="http-installation"></a>HTTP 설치

NetX용 HTTP를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX가 “ *\threadx\arm7\green*” 디렉터리에 설치된 경우 NetX HTTP 클라이언트 애플리케이션에 대해서는 *nx_http_client.h* 및 *nx_http_client.c* 이며, NetX HTTP 서버 애플리케이션에 대해서는 *nx_http_server.h* 및 *nx_http_server.c* 입니다. *nx_md5.c* 를 이 디렉터리에 복사해야 합니다. 데모 ‘ram 드라이버’ 애플리케이션 NetX HTTP 클라이언트와 서버 파일을 동일한 디렉터리에 복사해야 합니다.

## <a name="using-http"></a>HTTP 사용

NetX용 HTTP를 사용하는 것은 쉽습니다. 기본적으로 ThreadX, FileX 및 NetX를 각각 사용하기 위해서는 애플리케이션 코드에 *nx_http_client.h* 및/또는 *nx_http_server.h* 가 포함된 후 *tx_api.h, fx_api.h* 및 *nx_api.h* 가 포함되어야 합니다. HTTP 헤더 파일이 포함되면 애플리케이션 코드는 이 가이드의 뒷부분에 지정된 HTTP 함수 호출을 만들 수 있습니다. 또한 애플리케이션에는 빌드 프로세스에 *nx_http_client.c*, *nx_http_server.c* 및 *md5.c* 를 포함해야 합니다. 이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 해당 개체 형식을 애플리케이션의 파일에 연결해야 합니다. 이것이 NetX HTTP를 사용하는 데 필요한 모든 것입니다.

>[!NOTE] 
> 빌드 프로세스에 NX_HTTP_DIGEST_ENABLE이 지정되지 않은 경우에는 *md5.c* 파일을 애플리케이션에 추가할 필요가 없습니다. 마찬가지로, HTTP 클라이언트 기능이 필요하지 않은 경우에는 *nx_http_client.c* 파일을 생략할 수 있습니다.

>[!NOTE] 
> HTTP는 NetX TCP 서비스를 활용하므로 HTTP를 사용하기 전에 *nx_tcp_enable* 호출을 통해 TCP를 사용하도록 설정해야 합니다.

## <a name="small-example-system"></a>간단한 예제 시스템

NetX HTTP를 사용하는 것이 얼마나 쉬운지 보여 주는 예제가 아래에 표시된 그림 1.1에 설명되어 있습니다. 이 예제에서 HTTP 포함 파일 *nx_http_client.h 및 nx_http_server.h는* 8줄에서 가져옵니다. 다음으로, HTTP 서버는 131줄의 “*tx_application_define*”에서 만들어집니다.

>[!NOTE] 
> HTTP 서버 제어 블록 “*Server*”가 이전에 25줄에서 전역 변수로 정의되었습니다.

성공적으로 만든 후에는 HTTP 서버가 136줄에서 시작됩니다. 149줄에 HTTP 클라이언트가 만들어집니다. 마지막으로 클라이언트는 157줄에서 파일을 기록하고 195줄에서 다시 파일을 읽습니다.

```c
/* This is a small demo of HTTP on the high-performance NetX TCP/IP stack.
This demo relies on ThreadX, NetX, and FileX to show a simple HTML
transfer from the client and then back from the server. */

#include "tx_api.h"
#include "fx_api.h"
#include "nx_api.h"
#include "nx_http_client.h"
#include "nx_http_server.h"
#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_0;
TX_THREAD         thread_1;
NX_PACKET_POOL    pool_0;
NX_PACKET_POOL    pool_1;
NX_IP             ip_0;
NX_IP             ip_1;
FX_MEDIA          ram_disk;

/* Define HTTP objects. */

NX_HTTP_SERVER    my_server;
NX_HTTP_CLIENT    my_client;

/* Define the counters used in the demo application... */

ULONG             error_counter;

/* Define the RAM disk memory. */

UCHAR             ram_disk_memory[32000];

/* Define function prototypes. */

void     thread_0_entry(ULONG thread_input);
VOID     _fx_ram_driver(FX_MEDIA *media_ptr) ;
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT     authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, CHAR **name, CHAR **password, 
                              CHAR **realm);

/* Define the application's authentication check. This is called by
the HTTP server whenever a new request is received. */
UINT authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, CHAR **name, CHAR **password, 
                         CHAR **realm);
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */
    *name = "name";
    *password = "password";
    *realm = "NetX HTTP demo";

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create packet pool. */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
                         600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create an IP instance. */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
                0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create another IP instance. */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
                0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances. */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk. */
                 _fx_ram_driver, ram_disk_memory, pointer, 4096) ;
                 pointer += 4096;

    /* Create the NetX HTTP Server. */
    nx_http_server_create(&my_server, "My HTTP Server", &ip_1, &ram_disk,
                         pointer, 4096, &pool_1, authentication_check, NX_NULL);
                         pointer = pointer + 4096;

    /* Start the HTTP Server. */
    nx_http_server_start(&my_server);
}

/* Define the test thread. */
void     thread_0_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Create an HTTP client instance. */
    status = nx_http_client_create(&my_client, "My Client", &ip_0,
                                  &pool_0, 600);

    /* Check status. */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server. */
    status = nx_http_client_put_start(&my_client, IP_ADDRESS(1,2,3,5),
                                      "/test.htm", "name", "password", 103, 50);
    /* Check status. */
    if (status)
        error_counter++;

    /* Allocate a packet. */
    status = nx_packet_allocate(&pool_0, &my_packet, NX_TCP_PACKET,
                               NX_WAIT_FOREVER);
    /* Check status. */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page. */
    nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet,
                         "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<H1>NetX Test Page</H1>\r\n", 25,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
                         &pool_0, NX_WAIT_FOREVER);

    /* Complete the PUT by writing the total length. */
    status = **nx_http_client_put_packet**(&my_client, my_packet, 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Now GET the file back! */
    status = nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
                                     "/test.htm", NX_NULL, 0, "name", 
                                     "password", 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Get a packet. */
    status = nx_http_client_get_packet(&my_client, &my_packet, 20);

    /* Check for an error. */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet. */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it! */
        nx_packet_release(my_packet);
    }

    /* Flush the media. */
     fx_media_flush(&ram_disk);
 }
```

그림 1.1 NetX에서의 HTTP 사용 예제

## <a name="configuration-options"></a>구성 옵션

NetX용 HTTP를 빌드하기 위한 몇 가지 구성 옵션이 있습니다. 다음은 각각에 대해 자세히 설명된 모든 옵션의 목록입니다. 기본값은 나열되지만 *nx_http_client.h 및 nx_http_server.h* 를 포함하기 전에 다시 정의할 수 있습니다.

- **NX_DISABLE_ERROR_CHECKING**: 정의된 경우 이 옵션은 기본 HTTP 오류 검사를 제거합니다. 일반적으로 애플리케이션이 디버깅된 후에 사용됩니다.
- **NX_HTTP_SERVER_PRIORITY** HTTP 서버 스레드의 우선 순위입니다. 기본적으로 이 값은 우선 순위 16을 지정하는 16으로 정의되어 있습니다.
- **NX_HTTP_NO_FILEX** 정의된 경우 이 옵션은 FileX 종속성에 대한 스텁을 제공합니다. 이 옵션이 정의된 경우 HTTP 클라이언트는 변경 없이 작동합니다. HTTP 서버는 제대로 작동하기 위해 수정되거나 사용자가 몇 가지 FileX 서비스를 만들어야 합니다.
- **NX_HTTP_TYPE_OF_SERVICE**: HTTP TCP 요청에 필요한 서비스 유형입니다. 기본적으로 이 값은 일반 IP 패킷 서비스를 나타내는 NX_IP_NORMAL로 정의됩니다.
- **NX_HTTP_SERVER_THREAD_TIME_SLICE** 동일한 우선 순위의 스레드에 발생하기 전에 서버 스레드를 실행할 수 있는 타이머 틱 수입니다. 기본값은 2입니다.
- **NX_HTTP_FRAGMENT_OPTION** HTTP TCP 요청에 대해 조각을 사용합니다. 기본적으로 이 값은 HTTP TCP 조각화를 사용하지 않도록 설정하는 NX_DONT_FRAGMENT입니다.
- **NX_HTTP_SERVER_WINDOW_SIZE** 서버 소켓 창 크기입니다. 기본적으로 이 값은 2048바이트입니다.
- **NX_HTTP_TIME_TO_LIVE** 이 패킷이 삭제되기 전에 통과할 수 있는 라우터 수를 지정합니다. 기본값은 0x80으로 설정됩니다.
- **NX_HTTP_SERVER_TIMEOUT** 내부 서비스가 일시 중단할 ThreadX 틱 수를 지정합니다. 기본값은 10초(10 * NX_IP_PERIODIC_RATE)로 설정됩니다.
- **NX_HTTP_SERVER_TIMEOUT_ACCEPT** 내부 *nx_tcp_server_socket_accept* 호출에서 내부 서비스가 일시 중단되는 ThreadX 틱 수를 지정합니다. 기본값은 10 * NX_IP_PERIODIC_RATE로 설정됩니다.
- **NX_HTTP_SERVER_TIMEOUT_DISCONNECT** 내부 *nx_tcp_socket_disconnect* 호출에서 내부 서비스가 일시 중단되는 ThreadX 틱 수를 지정합니다. 기본값은 10초(10 * NX_IP_PERIODIC_RATE)로 설정됩니다.
- **NX_HTTP_SERVER_TIMEOUT_RECEIVE** 내부 *nx_tcp_socket_receive* 호출에서 내부 서비스가 일시 중단되는 ThreadX 틱 수를 지정합니다. 기본값은 10초(10 * NX_IP_PERIODIC_RATE)로 설정됩니다.
- **NX_HTTP_SERVER_TIMEOUT_SEND** 내부 *nx_tcp_socket_send* 호출에서 내부 서비스가 일시 중단되는 ThreadX 틱 수를 지정합니다. 기본값은 10초(10 * NX_IP_PERIODIC_RATE)로 설정됩니다.
- **NX_HTTP_MAX_HEADER_FIELD** HTTP 헤더 필드의 최대 크기를 지정합니다. 기본값은 256입니다.
- **NX_HTTP_MULTIPART_ENABLE** 정의된 경우 HTTP 서버가 다중 파트 HTTP 요청을 지원할 수 있습니다.
- **NX_HTTP_SERVER_MAX_PENDING** HTTP 서버에 대해 큐에 대기할 수 있는 연결 수를 지정합니다. 기본값은 5로 설정됩니다.
- **NX_HTTP_MAX_RESOURCE** 클라이언트에서 제공하는 *리소스 이름* 에 허용되는 바이트 수를 지정합니다. 기본값은 40으로 설정됩니다.
- **NX_HTTP_MAX_NAME** 클라이언트에서 제공하는 *사용자 이름* 에 허용되는 바이트 수를 지정합니다. 기본값은 20으로 설정됩니다.
- **NX_HTTP_MAX_PASSWORD** 클라이언트에서 제공하는 *암호* 에 허용되는 바이트 수를 지정합니다. 기본값은 20으로 설정됩니다.
- **NX_HTTP_SERVER_MIN_PACKET_SIZE** 서버를 만들 때 지정된 풀에 있는 패킷의 최소 크기를 지정합니다. 전체 HTTP 헤더를 하나의 패킷에 포함될 수 있도록 하려면 최소 크기가 필요합니다. 기본값은 600으로 설정됩니다.
- **NX_HTTP_CLIENT_MIN_PACKET_SIZE** 클라이언트를 만들 때 지정된 풀에 있는 패킷의 최소 크기를 지정합니다. 전체 HTTP 헤더를 하나의 패킷에 포함될 수 있도록 하려면 최소 크기가 필요합니다. 기본값은 300으로 설정됩니다.
- **NX_HTTP_SERVER_RETRY_SECONDS** *서버 소켓 재전송 시간 제한(초)을 설정합니다.* 기본값은 2로 설정됩니다.
- **NX_HTTP_SERVER_RETRY_MAX** 서버 소켓의 최대 재전송 수를 설정합니다. 기본값은 10으로 설정됩니다.
- **NX_HTTP_SERVER_RETRY_SHIFT** 이 값은 다음 재전송 시간 제한을 설정하는 데 사용됩니다. 현재 시간 제한에는 소켓 제한 시간 이동의 값으로 이동하여 지금까지의 재전송 횟수를 곱합니다. 제한 시간을 두 배로 설정하기 위해 기본값은 1로 설정됩니다.
- **NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** 서버 소켓 재전송 큐에서 큐에 넣을 수 있는 최대 패킷 수를 지정합니다. 큐에 넣은 패킷 수가 이 수에 도달하면 하나 이상의 큐에 넣은 패킷을 해제할 때까지 더 이상 패킷을 전송할 수 없습니다. 기본값은 20으로 설정됩니다.