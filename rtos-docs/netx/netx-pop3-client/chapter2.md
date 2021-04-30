---
title: 2장 - Azure RTOS NetX POP3 클라이언트 설치 및 사용
description: NetX POP3 클라이언트에는 하나의 원본 파일, 하나의 헤더 파일 및 데모 파일이 포함되어 있습니다. MD5 다이제스트 서비스에는 두 개의 추가 파일이 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24de396c69d458866f9423fd995bcb8d905f29c8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811479"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pop3-client"></a>2장 - Azure RTOS NetX POP3 클라이언트 설치 및 사용

NetX POP3 클라이언트에는 하나의 원본 파일, 하나의 헤더 파일 및 데모 파일이 포함되어 있습니다. MD5 다이제스트 서비스에는 두 개의 추가 파일이 있습니다. 사용자 가이드 PDF 파일(이 문서)도 있습니다.

- **nx_pop3_client.c**: NetX POP3 클라이언트 API용 C 원본 파일
- **nx_pop3_client.h**: NetX POP3 클라이언트 API용 C 헤더 파일
- **demo_netxduo_pop3_client.c**: POP3 클라이언트 생성 및 세션 시작을 위한 데모 파일
- **nx_md5.c**: MD5 다이제스트 서비스를 정의하는 C 원본 파일
- **nx_md5.h**: MD5 다이제스트 서비스를 정의하는 C 헤더 파일
- **nx_pop3_client.pdf**: NetX POP3 클라이언트 사용자 가이드

NetX POP3 클라이언트를 사용하기 위해 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리에 복사할 수 있습니다. 예를 들어 NetX가 “ *\threadx\mcf5272\green*” 디렉터리에 설치된 경우 *nx_md5.h*, *nx_md5.c,* *nx_pop3_client.h 및 nx_pop3_client.c* 파일을 이 디렉터리에 복사해야 합니다.

## <a name="using-netx-pop3-client"></a>NetX POP3 클라이언트 사용

NetX POP3 클라이언트 서비스를 사용하려면 애플리케이션에서 해당 빌드 프로젝트에 *nx_pop3_client.c* 를 추가해야 합니다. ThreadX 및 NetX를 사용하려면 애플리케이션 코드에서 *tx_api.h* 및 *nx_api.h* 다음에 *nx_md5.h, nx_pop3.h 및 nx_pop3_client.h* 가 포함되어 있어야 합니다.

이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 개체 코드는 애플리케이션의 파일과 함께 연결되어야 합니다. 이렇게 간단하게 NetX POP3 클라이언트를 사용할 수 있습니다.

## <a name="small-example-of-the-netx-pop3-client"></a>NetX POP3 클라이언트의 작은 예제

NetX POP3 클라이언트 서비스를 사용하는 방법의 예제가 아래에 나온 그림 1에 설명되어 있습니다. 이 데모에서는 37 및 38줄에서 메일 다운로드와 세션 완료 알림에 대한 두 개의 콜백을 설정합니다. POP3 클라이언트 패킷 풀이 76줄에 생성됩니다. IP 스레드 작업은 88줄에 생성됩니다. 이 패킷 풀은 POP3 클라이언트 패킷 풀에도 사용됩니다. TCP는 107줄의 IP 작업에서 사용하도록 설정됩니다.

POP3 클라이언트는 애플리케이션 스레드 입력 함수 *demo_thread_entry* 내에 133줄에 생성됩니다. 이는 *nx_pop3_client_create* 서비스가 POP3 서버와의 TCP 연결도 시도하기 때문입니다. 성공하면 애플리케이션은 *nx_pop3_client_mail_items_get* 서비스를 사용하여 149줄의 maildrop에 있는 항목 수를 POP3 서버에 쿼리합니다.

하나 이상의 항목이 있는 경우 애플리케이션은 각 메일 항목에 대해 while 루프를 반복하여 메일 메시지를 다운로드합니다. RETR 요청이 *nx_pop3_client_mail_item_get* 호출의 149줄에 생성됩니다. 성공하면 애플리케이션은 196줄에서 받은 메시지의 마지막 패킷을 검색할 때까지 177줄에서 *nx_pop3_client_mail_item_message_get* 서비스를 사용하여 패킷을 다운로드합니다. 마지막으로, 애플리케이션은 *nx_pop3_client_mail_item_delete* 호출의 199줄에서 성공적으로 다운로드되었다고 가정하여 메일 항목을 삭제합니다. RFC 1939에서는 POP3 클라이언트가 클라이언트의 maildrop에 메일이 누적되는 것을 방지하기 위해 다운로드된 메일 항목을 삭제하도록 서버에 지시할 것을 권장합니다. 서버에서 자동으로 이 작업을 수행할 수 있습니다.

모든 메일 항목이 다운로드되거나 POP3 클라이언트 서비스 호출이 실패하면 애플리케이션은 루프를 종료하고 *nx_pop3_client_delete* 서비스를 사용하여 217줄에서 POP3 클라이언트를 삭제합니다.

```c
/*
    demo_netxduo_pop3.c

    This is a small demo of POP3 Client on the NetX TCP/IP stack.
    This demo relies on Thread, NetX and POP3 Client API to conduct
    a POP3 mail session.
*/

#include "tx_api.h"
#include "nx_api.h"
#include "nx_pop3_client.h"

#define DEMO_STACK_SIZE        4096
#define CLIENT_ADDRESS         IP_ADDRESS(192,2,2,61)
#define SERVER_ADDRESS         IP_ADDRESS(192,2,2,89)
#define SERVER_PORT            110

/* Replace the 'ram' driver with your own Ethernet driver. */
void _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Set up the POP3 Client. */

TX_THREAD          demo_client_thread;
NX_POP3_CLIENT     demo_client;
NX_PACKET_POOL     client_packet_pool;
NX_IP              client_ip;

#define PAYLOAD_SIZE 500

/* Set up Client thread entry point. */
void     demo_thread_entry(ULONG info);

/* Shared secret is the same as password. */

#define LOCALHOST              "recipient@domain.com"
#define LOCALHOST_PASSWORD     "testpwd"

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *free_memory_pointer;

    /* Setup the working pointer. */
    free_memory_pointer = first_unused_memory;

    /* Create a client thread. */
    tx_thread_create(&demo_client_thread, "Client", demo_thread_entry, 0,
                    free_memory_pointer, DEMO_STACK_SIZE, 1, 1,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    free_memory_pointer = free_memory_pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* The demo client username and password is the authentication
    data used when the server attempts to authentication the client. */

    /* Create Client packet pool. */
    status = nx_packet_pool_create(&client_packet_pool,"POP3 Client Packet Pool",
                        PAYLOAD_SIZE, free_memory_pointer, (PAYLOAD_SIZE * 10));
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (PAYLOAD_SIZE * 10);

    /* Create IP instance for demo Client */
    status = nx_ip_create(&client_ip, "POP3 Client IP Instance",
                            CLIENT_ADDRESS, 0xFFFFFF00UL, &client_packet_pool,
                            _nx_ram_network_driver, free_memory_pointer,
                            2048, 1);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1024);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1024;

    /* Enable TCP and ICMP for Client IP. */
    nx_tcp_enable(&client_ip);
    nx_icmp_enable(&client_ip);

    return;
}

/* Define the application thread entry function. */

void demo_thread_entry(ULONG info)
{

UINT          status;
UINT          mail_item, number_mail_items;
UINT          bytes_downloaded = 0;
UINT          final_packet = NX_FALSE;
ULONG         total_size, mail_item_size, bytes_retrieved;
NX_PACKET     *packet_ptr;

    /* Let the IP instance get initialized with driver parameters. */
    tx_thread_sleep(40);

    /* Create a NetX POP3 Client instance with no byte or block memory pools.
    Note that it uses its password for its APOP shared secret. */
    status = nx_pop3_client_create(&demo_client,
                        NX_TRUE,
                        &client_ip, &client_packet_pool, SERVER_ADDRESS,
                        SERVER_PORT, LOCALHOST, LOCALHOST_PASSWORD);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        status = nx_pop3_client_delete(&demo_client);

        /* Abort. */
        return;
    }

    /* Find out how many items are in our mailbox. */
    status = nx_pop3_client_mail_items_get(&demo_client, &number_mail_items, &total_size);

    printf("Got %d mail items, total size%d \n", number_mail_items, total_size);

    /* If nothing in the mailbox, disconnect. */
    if (number_mail_items == 0)
    {
        nx_pop3_client_delete(&demo_client);

        return;
    }

    /* Download all mail items. */
    mail_item = 1;

    while (mail_item <= number_mail_items)
    {

        /* This submits a RETR request and gets the mail message size. */
        status = nx_pop3_client_mail_item_get(&demo_client, mail_item, &mail_item_size);

        /* Loop to get all mail message packets until the mail item is completely downloaded. */

        while((final_packet == NX_FALSE) && (status == NX_SUCCESS))
        {
            status = nx_pop3_client_mail_item_message_get(&demo_client, &packet_ptr,
                                                        &bytes_retrieved,
                                                        &final_packet);

            if (status != NX_SUCCESS)
            {
                break;
            }

            if (bytes_retrieved != 0)
            {

            printf("Received %d bytes of data for item %d: %s\n",
                    packet_ptr -> nx_packet_length,
                    mail_item, packet_ptr -> nx_packet_prepend_ptr);
            }

            nx_packet_release(packet_ptr);

            /* Determine if this is the last data packet. */
            if (final_packet)
            {
                /* It is. Let the server know it can delete this mail item. */
                status = nx_pop3_client_mail_item_delete(&demo_client, mail_item);
            }

            /* Keep track of how much mail message data is left. */
            bytes_downloaded += bytes_retrieved;
        }

        /* Get the next mail item. */
        mail_item++;

        tx_thread_sleep(100);
    }

    /* Disconnect from the POP3 server. */
    status = nx_pop3_client_quit(&demo_client);

    /* Delete the POP3 Client. This will not delete the Client packet pool. */
    status = nx_pop3_client_delete(&demo_client);

}
```

그림 1. NetX POP3 클라이언트 애플리케이션의 예제

## <a name="pop3-client-configuration-options"></a>POP3 클라이언트 구성 옵션

NetX POP3 클라이언트에는 몇 가지 구성 옵션이 있습니다. 다음은 자세히 설명된 모든 옵션의 목록입니다.

- **NX_POP3_CLIENT_PACKET_TIMEOUT**: POP3 클라이언트가 패킷을 할당하는 대기 옵션을 초 단위로 정의합니다. 기본값은 1초입니다.

- **NX_POP3_CLIENT_CONNECTION_TIMEOUT**: POP3 클라이언트가 POP3 서버와 연결하는 대기 옵션을 초 단위로 정의합니다. 기본값은 30초입니다.

- **NX_POP3_CLIENT_DISCONNECT_TIMEOUT**: POP3 클라이언트가 POP3 서버에서 연결을 끊을 때까지의 대기 옵션을 초 단위로 정의합니다. 기본값은 2 초입니다.

- **NX_POP3_TCP_SOCKET_SEND_WAIT**: 이 옵션은 *nx_tcp_socket_send* 서비스 호출에서 대기 옵션을 초 단위로 설정합니다. 기본값은 2 초입니다.

- **NX_POP3_SERVER_REPLY_TIMEOUT**: 이 옵션은 서버가 클라이언트 요청에 응답하는 *nx_tcp_socket_receive* 서비스 호출의 대기 옵션을 설정합니다. 기본값은 10초입니다.

- **NX_POP3_CLIENT_TCP_WINDOW_SIZE**: 이 옵션은 클라이언트 TCP 수신 창의 크기를 설정합니다. IP 인스턴스 MTU 크기에서 IP 및 TCP 헤더를 뺀 값으로 설정해야 합니다. 기본값은 1460입니다.

- **NX_POP3_MAX_USERNAME**: 이 옵션은 POP3 클라이언트 사용자 이름의 버퍼 크기를 설정합니다. 기본값은 40바이트입니다.

- **NX_POP3_MAX_PASSWORD**: 이 옵션은 POP3 클라이언트 암호의 버퍼 크기를 설정합니다. 기본값은 20바이트입니다.