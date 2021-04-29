---
title: 2장 - NetX Duo SMTP 클라이언트 설치 및 사용
description: 이 장에서는 NetX Duo SMTP 클라이언트 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86f324935ba32aab010b81f825be0a6564983a2e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810602"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a><span data-ttu-id="d8334-103">2장 - NetX Duo SMTP 클라이언트 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="d8334-103">Chapter 2 - Installation and use of NetX Duo SMTP client</span></span>

<span data-ttu-id="d8334-104">이 장에서는 NetX Duo SMTP 클라이언트 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Duo SMTP Client component.</span></span>

## <a name="netx-duo-smtp-client-installation"></a><span data-ttu-id="d8334-105">NetX Duo SMTP 클라이언트 설치</span><span class="sxs-lookup"><span data-stu-id="d8334-105">NetX Duo SMTP Client Installation</span></span>

<span data-ttu-id="d8334-106">NetX Duo SMTP 클라이언트는 [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-106">The NetX Duo SMTP Client is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="d8334-107">패키지에는 다음과 같은 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-107">The package includes the following files:</span></span>

- <span data-ttu-id="d8334-108">NetX Duo SMTP 클라이언트 API용 **nxd_smtp_client. c** C 소스 파일</span><span class="sxs-lookup"><span data-stu-id="d8334-108">**nxd_smtp_client.c** C Source file for NetX Duo SMTP Client API</span></span>
- <span data-ttu-id="d8334-109">NetX Duo SMTP 클라이언트 API용 **nxd_smtp_client. h** C 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="d8334-109">**nxd_smtp_client.h** C Header file for NetX Duo SMTP Client API</span></span>
- <span data-ttu-id="d8334-110">NetX Duo SMTP 클라이언트용 **demo_netxduo_smtp_client. c** 데모</span><span class="sxs-lookup"><span data-stu-id="d8334-110">**demo_netxduo_smtp_client.c** Demo for NetX Duo SMTP Client</span></span>
- <span data-ttu-id="d8334-111">NetX Duo SMTP 클라이언트 API용 **nxd_smtp_client.pdf 사용자 가이드**</span><span class="sxs-lookup"><span data-stu-id="d8334-111">**nxd_smtp_client.pdf User Guide for** NetX Duo SMTP Client API</span></span>

<span data-ttu-id="d8334-112">NetX Duo SMTP 클라이언트 API를 사용하려면 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-112">To use the NetX Duo SMTP Client API, the entire distribution mentioned previously may be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="d8334-113">예를 들어 NetX Duo가 “c: *\myproject*” 디렉터리에 설치된 경우 그다음 *nxd_smtp_client.h, and nxd_smtp_client.c* 파일을 이 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-113">For example, if NetX Duo is installed in the directory “c:*\myproject*” then the *nxd_smtp_client.h, and nxd_smtp_client.c* files should be copied into this directory.</span></span>

## <a name="using-netx-duo-smtp-client"></a><span data-ttu-id="d8334-114">NetX Duo SMTP 클라이언트 사용</span><span class="sxs-lookup"><span data-stu-id="d8334-114">Using NetX Duo SMTP Client</span></span>

<span data-ttu-id="d8334-115">NetX Duo SMTP 클라이언트 애플리케이션을 만들려면 먼저 ThreadX 및 NetX Duo 라이브러리를 빌드하여 빌드 프로젝트에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-115">To create the NetX Duo SMTP Client application, it must first build the ThreadX and NetX Duo libraries and include them in the build project.</span></span> <span data-ttu-id="d8334-116">그런 다음, 애플리케이션은 애플리케이션 소스 코드에 tx *_api.h* 및 *nx_api.h* 를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-116">The application must then include tx *_api.h* and *nx_api.h in its application source code*.</span></span> <span data-ttu-id="d8334-117">이를 통해 ThreadX 및 NetX Duo 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-117">This will enable ThreadX and NetX Duo services.</span></span> <span data-ttu-id="d8334-118">또한 SMTP 클라이언트 서비스를 사용하려면 *tx_api.h* 및 *nx_api.h* 뒤에 *nxd_smtp_client.c* 및 *nxd_smtp_client.h* 를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-118">It must also include *nxd_smtp_client.c* and *nxd_smtp_client.h* after *tx_api.h* and *nx_api.h to use SMTP Client services.*</span></span>

<span data-ttu-id="d8334-119">이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 개체 코드가 애플리케이션의 파일과 함께 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-119">These files must be compiled in the same manner as other application files and the object code must be linked along with the files of the application.</span></span> <span data-ttu-id="d8334-120">이는 NetX Duo SMTP 클라이언트 애플리케이션을 만드는 데 필요한 전부입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-120">This is all that is required to create a NetX Duo SMTP Client application.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="d8334-121">간단한 예제 시스템</span><span class="sxs-lookup"><span data-stu-id="d8334-121">Small Example System</span></span>

<span data-ttu-id="d8334-122">NetX Duo SMTP 클라이언트를 사용하는 예제는 아래에 표시된 그림 1에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-122">An example of using the NetX Duo SMTP Client is described in Figure 1 that appears below.</span></span> <span data-ttu-id="d8334-123">IP 인스턴스의 패킷 풀은 68번째 줄에서 nx_packet_pool_create 서비스를 사용하여 만들어지고 매우 작은 패킷 페이로드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-123">The packet pool for the IP instance is created using the nx_packet_pool_create service, on line 68 and has a very small packet payload.</span></span> <span data-ttu-id="d8334-124">이는 IP 인스턴스가 많은 페이로드를 필요로 하지 않는 제어 패킷만 전송하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-124">This is because the IP instance only sends control packets which don’t require much payload.</span></span> <span data-ttu-id="d8334-125">84번째 줄에서 만들어진 SMTP 클라이언트 패킷 풀은 SMTP 클라이언트 메시지를 서버 및 메시지 데이터에 전송하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-125">The SMTP Client packet pool created on line 84 and is used for transmitting SMTP Client messages to the server and message data.</span></span> <span data-ttu-id="d8334-126">패킷 페이로드가 훨씬 더 큽니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-126">Its packet payload is much larger.</span></span> <span data-ttu-id="d8334-127">IP 인스턴스는 동일한 패킷 풀을 사용하여 118번째 줄에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-127">The IP instance is created in line 118 using the same packet pool.</span></span> <span data-ttu-id="d8334-128">SMTP 프로토콜에 필요한 TCP는 130번째 줄의 IP 인스턴스에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-128">TCP, required for the SMTP protocol, is enabled on the IP instance in line 130.</span></span>

<span data-ttu-id="d8334-129">애플리케이션 스레드에서 SMTP 클라이언트는 170번째 줄의 *nxd_smtp_client_create* 서비스를 사용하여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-129">In the application thread, the SMTP Client is created using the *nxd_smtp_client_create* service, in line 170.</span></span> <span data-ttu-id="d8334-130">이 예제는 IPv4로 제한되지만 *nxd_smtp_client_create* 서비스는 IPv4 및 IPv6 SMTP 서버 연결을 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-130">The *nxd_smtp_client_create* service supports both IPv4 and IPv6 SMTP server connections although this example is limited to IPv4.</span></span> <span data-ttu-id="d8334-131">그런 다음, 메일 메시지는 *nx_smtp_mail_send* 서비스를 사용하여 184번째 줄에서 SMTP 클라이언트에 전송되도록 제출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-131">Then the mail message is submitted to the SMTP Client for transmission on line 184 using the *nx_smtp_mail_send* service.</span></span> <span data-ttu-id="d8334-132">메일 콘텐츠 헤더가 있는 제목 줄은 메시지 본문과 별도로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-132">Note that the subject line with the mail content header is created separately from the message body.</span></span> <span data-ttu-id="d8334-133">또한 메일 전송 요청은 구문상 올바른 것으로 간주되는 수신자 메일 주소를 하나만 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-133">Also note that the send mail request accepts only one recipient mail address which is assumed to be syntactically correct.</span></span>

<span data-ttu-id="d8334-134">그런 다음, 애플리케이션은 200번째 줄에서 SMTP 클라이언트를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-134">Then the application terminates the SMTP Client on line 200.</span></span> <span data-ttu-id="d8334-135">*Nx_smtp_client_delete* 서비스는 소켓 연결이 닫혀 있고 포트가 바인딩되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-135">The *nx_smtp_client_delete* service checks that the socket connection is closed and the port is unbound.</span></span> <span data-ttu-id="d8334-136">패킷 풀을 더 이상 사용하지 않는 경우 SMTP 클라이언트 애플리케이션에서 패킷 풀을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-136">Note that it is up to the SMTP Client application to delete the packet pool if it no longer has use for it.</span></span>

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

<span data-ttu-id="d8334-137">**그림 1. NetX Duo에서 SMTP 클라이언트 사용 예제**</span><span class="sxs-lookup"><span data-stu-id="d8334-137">**Figure 1. Example of SMTP Client use with NetX Duo**</span></span>

## <a name="client-configuration-options"></a><span data-ttu-id="d8334-138">클라이언트 작업 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="d8334-138">Client Configuration Options</span></span>

<span data-ttu-id="d8334-139">NetX Duo SMTP 클라이언트 API에는 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-139">There are several configuration options with the NetX Duo SMTP Client API.</span></span> <span data-ttu-id="d8334-140">다음은 모든 옵션의 목록에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-140">Following is a list of all options described in detail:</span></span>

- <span data-ttu-id="d8334-141">**NX_SMTP_CLIENT_TCP_WINDOW_SIZE** 이 옵션은 클라이언트 TCP 수신 창의 크기를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-141">**NX_SMTP_CLIENT_TCP_WINDOW_SIZE** This option sets the size of the Client TCP receive window.</span></span> <span data-ttu-id="d8334-142">이는 기본 이더넷 하드웨어의 MTU 크기 미만으로 설정하고 IP 및 TCP 헤더를 위한 공간을 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-142">This should be set to below the MTU size of the underlying Ethernet hardware and allow room for IP and TCP headers.</span></span> <span data-ttu-id="d8334-143">기본 NetX Duo SMTP 클라이언트 TCP 창 크기는 1460입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-143">The default NetX Duo SMTP Client TCP window size is 1460.</span></span>
- <span data-ttu-id="d8334-144">**NX_SMTP_CLIENT_PACKET_TIMEOUT** 이 옵션은 NetX 패킷 할당에 대한 시간 제한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-144">**NX_SMTP_CLIENT_PACKET_TIMEOUT** This option sets the timeout on NetX packet allocation.</span></span> <span data-ttu-id="d8334-145">기본 NetX Duo SMTP 클라이언트 패킷 시간 제한은 2초입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-145">The default NetX Duo SMTP Client packet timeout is 2 seconds.</span></span>
- <span data-ttu-id="d8334-146">**NX_SMTP_CLIENT_CONNECTION_TIMEOUT** 이 옵션은 클라이언트 TCP 소켓 연결 시간 제한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-146">**NX_SMTP_CLIENT_CONNECTION_TIMEOUT** This option sets the Client TCP socket connect timeout.</span></span> <span data-ttu-id="d8334-147">기본 NetX Duo SMTP 클라이언트 연결 시간 제한은 10초입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-147">The default NetX Duo SMTP Client connect timeout is 10 seconds.</span></span>
- <span data-ttu-id="d8334-148">**NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** 이 옵션은 클라이언트 TCP 소켓 연결 끊기 시간 제한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-148">**NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** This option sets the Client TCP socket disconnect timeout.</span></span> <span data-ttu-id="d8334-149">기본 NetX Duo SMTP 클라이언트 연결 끊기 시간 제한은 5초입니다\*.</span><span class="sxs-lookup"><span data-stu-id="d8334-149">The default NetX Duo SMTP Client disconnect timeout is 5 seconds\*.</span></span> <span data-ttu-id="d8334-150">SMTP 클라이언트에서 연결 끊김과 같은 내부 오류가 발생하는 경우 대기 시간 제한 없이 연결이 종료될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-150">Note that if the SMTP Client encounters an internal error such as a broken connection it may terminate the connection with a zero wait timeout.</span></span>
- <span data-ttu-id="d8334-151">**NX_SMTP_GREETING_TIMEOUT** 이 옵션은 클라이언트가 인사말에 대한 서버 응답을 수신하는 시간 제한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-151">**NX_SMTP_GREETING_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to its greeting.</span></span> <span data-ttu-id="d8334-152">기본 NetX Duo SMTP 클라이언트 값은 10초입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-152">The default NetX Duo SMTP Client value is 10 seconds.</span></span>
- <span data-ttu-id="d8334-153">**NX_SMTP_ENVELOPE_TIMEOUT** 이 옵션은 클라이언트가 클라이언트 명령에 대한 서버 응답을 수신하는 시간 제한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-153">**NX_SMTP_ENVELOPE_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to a Client command.</span></span> <span data-ttu-id="d8334-154">기본 NetX Duo SMTP 클라이언트 값은 10초입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-154">The default NetX Duo SMTP Client value is 10 seconds.</span></span>
- <span data-ttu-id="d8334-155">**NX_SMTP_MESSAGE_TIMEOUT** 이 옵션은 클라이언트가 메일 메시지 데이터를 수신하기 위해 서버 응답을 수신하는 시간 제한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-155">**NX_SMTP_MESSAGE_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to receiving the mail message data.</span></span> <span data-ttu-id="d8334-156">기본 NetX Duo SMTP 클라이언트 값은 30초입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-156">The default NetX Duo SMTP Client value is 30 seconds.</span></span>
- <span data-ttu-id="d8334-157">**NX_SMTP_CLIENT_SEND_TIMEOUT** 이 옵션은 서버와 SMTP 인증 중에 사용자 암호를 저장할 버퍼의 대기 옵션을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-157">**NX_SMTP_CLIENT_SEND_TIMEOUT** This option defines the wait option of the buffer to store the user password during SMTP authentication with the Server.</span></span> <span data-ttu-id="d8334-158">기본값은 20바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-158">The default value is 20 bytes.</span></span>
- <span data-ttu-id="d8334-159">**NX_SMTP_SERVER_CHALLENGE_MAX_STRING** 이 옵션은 SMTP 인증 중에 서버 챌린지를 추출하기 위한 버퍼 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-159">**NX_SMTP_SERVER_CHALLENGE_MAX_STRING** This option defines the size of the buffer for extracting the Server challenge during SMTP authentication.</span></span> <span data-ttu-id="d8334-160">기본값은 200바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-160">The default value is 200 bytes.</span></span> <span data-ttu-id="d8334-161">로그인 및 일반 인증의 경우 SMTP 클라이언트에서 더 작은 버퍼를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-161">For LOGIN and PLAIN authentication, the SMTP Client can probably use a smaller buffer.</span></span>
- <span data-ttu-id="d8334-162">**NX_SMTP_CLIENT_MAX_PASSWORD** 이 옵션은 서버와 SMTP 인증 중에 사용자 암호를 저장할 버퍼 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-162">**NX_SMTP_CLIENT_MAX_PASSWORD** This option defines the size of the buffer to store the user password during SMTP authentication with the Server.</span></span> <span data-ttu-id="d8334-163">기본값은 20바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-163">The default value is 20 bytes.</span></span> 
- <span data-ttu-id="d8334-164">**NX_SMTP_CLIENT_MAX_USERNAME** 이 옵션은 서버와 SMTP 인증 중에 호스트 사용자 이름을 저장할 버퍼 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-164">**NX_SMTP_CLIENT_MAX_USERNAME** This option defines the size of the buffer to store the host username during SMTP authentication with the Server.</span></span> <span data-ttu-id="d8334-165">기본값은 40바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="d8334-165">The default value is 40 bytes.</span></span> 
