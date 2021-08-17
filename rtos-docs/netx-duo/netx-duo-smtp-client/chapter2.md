---
title: 2장 - NetX Duo SMTP 클라이언트 설치 및 사용
description: 이 장에서는 NetX Duo SMTP 클라이언트 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ba4d50048adba4ac992f6bbe90d236445546a5929ace74899833c686a90dadd9
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797843"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a>2장 - NetX Duo SMTP 클라이언트 설치 및 사용

이 장에서는 NetX Duo SMTP 클라이언트 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="netx-duo-smtp-client-installation"></a>NetX Duo SMTP 클라이언트 설치

NetX Duo SMTP 클라이언트는 [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo)에서 확인할 수 있습니다. 패키지에는 다음과 같은 파일이 포함되어 있습니다.

- NetX Duo SMTP 클라이언트 API용 **nxd_smtp_client. c** C 소스 파일
- NetX Duo SMTP 클라이언트 API용 **nxd_smtp_client. h** C 헤더 파일
- NetX Duo SMTP 클라이언트용 **demo_netxduo_smtp_client. c** 데모
- NetX Duo SMTP 클라이언트 API용 **nxd_smtp_client.pdf 사용자 가이드**

NetX Duo SMTP 클라이언트 API를 사용하려면 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사해야 합니다. 예를 들어 NetX Duo가 “c: *\myproject*” 디렉터리에 설치된 경우 그다음 *nxd_smtp_client.h, and nxd_smtp_client.c* 파일을 이 디렉터리에 복사해야 합니다.

## <a name="using-netx-duo-smtp-client"></a>NetX Duo SMTP 클라이언트 사용

NetX Duo SMTP 클라이언트 애플리케이션을 만들려면 먼저 ThreadX 및 NetX Duo 라이브러리를 빌드하여 빌드 프로젝트에 포함해야 합니다. 그런 다음, 애플리케이션은 애플리케이션 소스 코드에 tx *_api.h* 및 *nx_api.h* 를 포함해야 합니다. 이를 통해 ThreadX 및 NetX Duo 서비스를 사용할 수 있습니다. 또한 SMTP 클라이언트 서비스를 사용하려면 *tx_api.h* 및 *nx_api.h* 뒤에 *nxd_smtp_client.c* 및 *nxd_smtp_client.h* 를 포함해야 합니다.

이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 개체 코드가 애플리케이션의 파일과 함께 연결되어야 합니다. 이는 NetX Duo SMTP 클라이언트 애플리케이션을 만드는 데 필요한 전부입니다.

## <a name="small-example-system"></a>간단한 예제 시스템

NetX Duo SMTP 클라이언트를 사용하는 예제는 아래에 표시된 그림 1에 설명되어 있습니다. IP 인스턴스의 패킷 풀은 68번째 줄에서 nx_packet_pool_create 서비스를 사용하여 만들어지고 매우 작은 패킷 페이로드를 포함합니다. 이는 IP 인스턴스가 많은 페이로드를 필요로 하지 않는 제어 패킷만 전송하기 때문입니다. 84번째 줄에서 만들어진 SMTP 클라이언트 패킷 풀은 SMTP 클라이언트 메시지를 서버 및 메시지 데이터에 전송하는 데 사용됩니다. 패킷 페이로드가 훨씬 더 큽니다. IP 인스턴스는 동일한 패킷 풀을 사용하여 118번째 줄에서 만들어집니다. SMTP 프로토콜에 필요한 TCP는 130번째 줄의 IP 인스턴스에서 사용됩니다.

애플리케이션 스레드에서 SMTP 클라이언트는 170번째 줄의 *nxd_smtp_client_create* 서비스를 사용하여 만들어집니다. 이 예제는 IPv4로 제한되지만 *nxd_smtp_client_create* 서비스는 IPv4 및 IPv6 SMTP 서버 연결을 모두 지원합니다. 그런 다음, 메일 메시지는 *nx_smtp_mail_send* 서비스를 사용하여 184번째 줄에서 SMTP 클라이언트에 전송되도록 제출됩니다. 메일 콘텐츠 헤더가 있는 제목 줄은 메시지 본문과 별도로 만들어집니다. 또한 메일 전송 요청은 구문상 올바른 것으로 간주되는 수신자 메일 주소를 하나만 허용합니다.

그런 다음, 애플리케이션은 200번째 줄에서 SMTP 클라이언트를 종료합니다. *Nx_smtp_client_delete* 서비스는 소켓 연결이 닫혀 있고 포트가 바인딩되지 않았는지 확인합니다. 패킷 풀을 더 이상 사용하지 않는 경우 SMTP 클라이언트 애플리케이션에서 패킷 풀을 삭제합니다.

```c
/*
   demo_netxduo_smtp_client.c

   This is a small demo of the NetX Duo SMTP Client on the high-performance NetX
   Duo TCP/IP stack.  This demo relies on Thread, NetX Duo and SMTP Client API to
   perform simple SMTP mail transfers in an SMTP client application to an SMTP mail
   server.   */

#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_smtp_client.h"


/* Define the host user name and mail box parameters */
#define USERNAME               "myusername"
#define PASSWORD               "mypassword"
#define FROM_ADDRESS           "my@mycompany.com"
#define RECIPIENT_ADDRESS      "your@yourcompany.com"
#define LOCAL_DOMAIN           "mycompany.com"

#define SUBJECT_LINE           "NetX Duo SMTP Client Demo"
#define MAIL_BODY              "NetX Duo SMTP client is an SMTP client \r\n" \
                               “implementation for embedded devices to send  \r\n" \
                               "email to SMTP servers. This feature is \r\n" \
                               "intended to allow a device to send simple \r\n " \
                               "status reports using the most universal \r\n " \
                               “Internet application, email.\r\n"

/* See the NetX Duo SMTP Client User Guide for how to set the authentication type.
   The most common authentication type is PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE 3


#define CLIENT_IP_ADDRESS  IP_ADDRESS(1,2,3,5)
#define SERVER_IP_ADDRESS  IP_ADDRESS(1,2,3,4)
#define SERVER_PORT        25


/* Define the NetX Duo and ThreadX structures for the SMTP client appliciation. */
NX_PACKET_POOL                  ip_packet_pool;
NX_PACKET_POOL                  client_packet_pool;
NX_IP                           client_ip;
TX_THREAD                       demo_client_thread;
static NX_SMTP_CLIENT           demo_client;


void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
void    demo_client_thread_entry(ULONG info);

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    UINT    status;
    CHAR    *free_memory_pointer;


    /* Setup the pointer to unallocated memory.  */
    free_memory_pointer =  (CHAR *) first_unused_memory;

    /* Create IP default packet pool. */
    status =  nx_packet_pool_create(&ip_packet_pool, "Default IP Packet Pool",
                                    128, free_memory_pointer, 2048);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Create SMTP Client packet pool. This is only for transmitting packets to the
       server. It need not be a separate packet pool than the IP default packet pool
       but for more efficient resource use, we use two different packet pools
       because the CLient SMTP messages generally require more payload than IP
       control packets.

       Packet payload depends on the SMTP Client application requirements.  Size of
       packet payload must include IP and TCP headers. For IPv6 connections, IP and
       TCP header data is 60 bytes. For IPv4 IP and TCP header data is 40 bytes (not
       including TCP options). */
    status |=  nx_packet_pool_create(&client_packet_pool, "SMTP Client Packet Pool",
                                     800, free_memory_pointer, (10*800));

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (10*800);

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "client_thread",
                              demo_client_thread_entry, 0, free_memory_pointer,
                              2048, 16, 16,
                              TX_NO_TIME_SLICE, TX_DONT_START);

    if (status != NX_SUCCESS)
    {

        printf("Error creating Client thread. Status 0x%x\r\n", status);
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + 4096;


    /* Create Client IP instance. Remember to replace the generic driver
       with a real ethernet driver to actually run this demo! */

    status = nx_ip_create(&client_ip, "SMTP Client IP Instance", CLIENT_IP_ADDRESS,
                          0xFFFFFF00UL, &ip_packet_pool, _nx_ram_network_driver,
                          free_memory_pointer, 2048, 1);


    free_memory_pointer =  free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1040);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1040;

    /* Enable TCP for client. */
    status =  nx_tcp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable ICMP for client. */
    status =  nx_icmp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Start the client thread. */
    tx_thread_resume(&demo_client_thread);

    return;
}


/* Define the smtp application thread task.   */
void    demo_client_thread_entry(ULONG info)
{

    UINT        status;
    UINT        error_counter = 0;
    NXD_ADDRESS server_ip_address;


    tx_thread_sleep(100);

    /* Set up the server IP address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;

    /* The demo client username and password is the authentication
       data used when the server attempts to authentication the client. */

    status =  nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
                                     USERNAME,
                                     PASSWORD,
                                     FROM_ADDRESS,
                                     LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
                                     &server_ip_address, SERVER_PORT);

    if (status != NX_SUCCESS)
    {
        printf("Error creating the client. Status: 0x%x.\n\r", status);
        return;
    }

    /* Create a mail instance with the above text message and recipient info. */
    status =  nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
                                TP_MAIL_PRIORITY_NORMAL,
                                SUBJECT_LINE, MAIL_BODY, sizeof(MAIL_BODY) - 1);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        /* Mail item was not sent. Note that we need not delete the client. The
           error status may be a failed authentication check or a broken connection.
           We can simply call nx_smtp_mail_send again.  */
        error_counter++;
    }

    /* Release resources used by client. Note that the transmit packet
       pool must be deleted by the application if it no longer has use for it.*/
    status = nx_smtp_client_delete(&demo_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    return;
}
```

**그림 1. NetX Duo에서 SMTP 클라이언트 사용 예제**

## <a name="client-configuration-options"></a>클라이언트 작업 구성 옵션

NetX Duo SMTP 클라이언트 API에는 몇 가지 구성 옵션이 있습니다. 다음은 모든 옵션의 목록에 대한 자세한 설명입니다.

- **NX_SMTP_CLIENT_TCP_WINDOW_SIZE** 이 옵션은 클라이언트 TCP 수신 창의 크기를 설정합니다. 이는 기본 이더넷 하드웨어의 MTU 크기 미만으로 설정하고 IP 및 TCP 헤더를 위한 공간을 허용해야 합니다. 기본 NetX Duo SMTP 클라이언트 TCP 창 크기는 1460입니다.
- **NX_SMTP_CLIENT_PACKET_TIMEOUT** 이 옵션은 NetX 패킷 할당에 대한 시간 제한을 설정합니다. 기본 NetX Duo SMTP 클라이언트 패킷 시간 제한은 2초입니다.
- **NX_SMTP_CLIENT_CONNECTION_TIMEOUT** 이 옵션은 클라이언트 TCP 소켓 연결 시간 제한을 설정합니다. 기본 NetX Duo SMTP 클라이언트 연결 시간 제한은 10초입니다.
- **NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** 이 옵션은 클라이언트 TCP 소켓 연결 끊기 시간 제한을 설정합니다. 기본 NetX Duo SMTP 클라이언트 연결 끊기 시간 제한은 5초입니다*. SMTP 클라이언트에서 연결 끊김과 같은 내부 오류가 발생하는 경우 대기 시간 제한 없이 연결이 종료될 수 있습니다.
- **NX_SMTP_GREETING_TIMEOUT** 이 옵션은 클라이언트가 인사말에 대한 서버 응답을 수신하는 시간 제한을 설정합니다. 기본 NetX Duo SMTP 클라이언트 값은 10초입니다.
- **NX_SMTP_ENVELOPE_TIMEOUT** 이 옵션은 클라이언트가 클라이언트 명령에 대한 서버 응답을 수신하는 시간 제한을 설정합니다. 기본 NetX Duo SMTP 클라이언트 값은 10초입니다.
- **NX_SMTP_MESSAGE_TIMEOUT** 이 옵션은 클라이언트가 메일 메시지 데이터를 수신하기 위해 서버 응답을 수신하는 시간 제한을 설정합니다. 기본 NetX Duo SMTP 클라이언트 값은 30초입니다.
- **NX_SMTP_CLIENT_SEND_TIMEOUT** 이 옵션은 서버와 SMTP 인증 중에 사용자 암호를 저장할 버퍼의 대기 옵션을 정의합니다. 기본값은 20바이트입니다.
- **NX_SMTP_SERVER_CHALLENGE_MAX_STRING** 이 옵션은 SMTP 인증 중에 서버 챌린지를 추출하기 위한 버퍼 크기를 정의합니다. 기본값은 200바이트입니다. 로그인 및 일반 인증의 경우 SMTP 클라이언트에서 더 작은 버퍼를 사용할 수도 있습니다.
- **NX_SMTP_CLIENT_MAX_PASSWORD** 이 옵션은 서버와 SMTP 인증 중에 사용자 암호를 저장할 버퍼 크기를 정의합니다. 기본값은 20바이트입니다. 
- **NX_SMTP_CLIENT_MAX_USERNAME** 이 옵션은 서버와 SMTP 인증 중에 호스트 사용자 이름을 저장할 버퍼 크기를 정의합니다. 기본값은 40바이트입니다. 
