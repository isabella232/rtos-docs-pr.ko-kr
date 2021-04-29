---
title: 2장 - Azure RTOS NetX Duo Telnet의 설치 및 사용
description: 이 장에서는 Azure RTOS NetX Duo Telnet 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5b24690db6ccbc582387dd9dba5b0471e6f278d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810542"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-telnet"></a><span data-ttu-id="5b3f5-103">2장 - Azure RTOS NetX Duo Telnet의 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="5b3f5-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo Telnet</span></span>

<span data-ttu-id="5b3f5-104">이 장에서는 Azure RTOS NetX Duo Telnet 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo Telnet component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="5b3f5-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="5b3f5-105">Product Distribution</span></span>

<span data-ttu-id="5b3f5-106">Azure RTOS NetX Duo Telnet 패키지는 <https://github.com/azure-rtos/netxduo>에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-106">The Azure RTOS NetX Duo Telnet package is available at <https://github.com/azure-rtos/netxduo>.</span></span> <span data-ttu-id="5b3f5-107">패키지에는 다음과 같은 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-107">The package includes the following files:</span></span>

- <span data-ttu-id="5b3f5-108">**nxd_telnet_client.h**: NetX Duo용 텔넷 클라이언트의 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="5b3f5-108">**nxd_telnet_client.h**: Header file for Telnet Client for NetX Duo</span></span>
- <span data-ttu-id="5b3f5-109">**nxd_telnet_client.c**: NetX Duo용 텔넷 클라이언트의 C 소스 파일</span><span class="sxs-lookup"><span data-stu-id="5b3f5-109">**nxd_telnet_client.c**: C Source file for Telnet Client for NetX Duo</span></span>
- <span data-ttu-id="5b3f5-110">**nxd_telnet_server.h**: NetX Duo용 텔넷 서버의 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="5b3f5-110">**nxd_telnet_server.h**: Header file for Telnet Server for NetX Duo</span></span>
- <span data-ttu-id="5b3f5-111">**nxd_telnet_server.c**: NetX Duo용 텔넷 서버의 C 소스 파일</span><span class="sxs-lookup"><span data-stu-id="5b3f5-111">**nxd_telnet_server.c**: C Source file for Telnet Server for NetX Duo</span></span>
- <span data-ttu-id="5b3f5-112">**nxd_telnet.pdf**: NetX Duo용 텔넷의 PDF 설명</span><span class="sxs-lookup"><span data-stu-id="5b3f5-112">**nxd_telnet.pdf**: PDF description of Telnet for NetX Duo</span></span>
- <span data-ttu-id="5b3f5-113">**demo_netxduo_telnet. c**: NetX Duo 텔넷 데모</span><span class="sxs-lookup"><span data-stu-id="5b3f5-113">**demo_netxduo_telnet.c**: NetX Duo Telnet demonstration</span></span>

## <a name="telnet-installation"></a><span data-ttu-id="5b3f5-114">텔넷 설치</span><span class="sxs-lookup"><span data-stu-id="5b3f5-114">Telnet Installation</span></span>

<span data-ttu-id="5b3f5-115">NetX Duo용 텔넷을 사용하려면 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-115">In order to use Telnet for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="5b3f5-116">예를 들어 NetX Duo가 “ *\threadx\arm7\green*” 디렉터리에 설치된 경우 *nxd_telnet_client.h*, *nxd_telnet_client.c*, *nxd_telnet_server.c, nxd_telnet_server.h* 파일을 이 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-116">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_telnet_client.h*, *nxd_telnet_client.c*, *nxd_telnet_server.c and nxd_telnet_server.h* files should be copied into this directory.</span></span>

## <a name="using-telnet"></a><span data-ttu-id="5b3f5-117">텔넷 사용</span><span class="sxs-lookup"><span data-stu-id="5b3f5-117">Using Telnet</span></span>

<span data-ttu-id="5b3f5-118">NetX Duo용 텔넷은 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-118">Using Telnet for NetX Duo is easy.</span></span> <span data-ttu-id="5b3f5-119">기본적으로 애플리케이션 코드는 ThreadX 및 NetX Duo를 사용하기 위해 *tx_api.h* 와 *nx_api.h* 를 포함한 후 텔넷 서버 애플리케이션에 *nxd_telnet_server.h* 를 포함하고, 텔넷 클라이언트 애플리케이션에 *nxd_telnet_client.h* 를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-119">Basically, the application code must include *nxd_telnet_server.h* for Telnet Server applications and *nxd_telnet_client.h* for Telnet Client applications after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo.</span></span> <span data-ttu-id="5b3f5-120">‘헤더’가 포함되면 애플리케이션 코드는 이 가이드의 뒷부분에 지정된 텔넷 함수 호출을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-120">Once *the header* is included, the application code is then able to make the Telnet function calls specified later in this guide.</span></span> <span data-ttu-id="5b3f5-121">또한 애플리케이션에서는 *nxd_telnet_client. c* 및 *nxd_telnet_server* 를 빌드 프로세스에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-121">The application must also include *nxd_telnet_client.c* and *nxd_telnet_server.c* in the build process.</span></span> <span data-ttu-id="5b3f5-122">이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 개체 양식이 애플리케이션의 파일과 함께 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-122">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="5b3f5-123">이것이 NetX Duo Telnet을 사용하는 데 필요한 전부입니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-123">This is all that is required to use NetX Duo Telnet.</span></span>

<span data-ttu-id="5b3f5-124">텔넷 클라이언트 기능이 필요하지 않은 경우 *nxd_telnet_client.c* 파일을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-124">If no Telnet Client capabilities are required, the *nxd_telnet_client.c* file may be omitted.</span></span>

<span data-ttu-id="5b3f5-125">또한 텔넷은 NetX Duo TCP 서비스를 활용하므로 텔넷을 사용하기 전에 *nx_tcp_enable* 호출을 통해 TCP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-125">Note also that because Telnet utilizes NetX Duo TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using Telnet.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="5b3f5-126">간단한 예제 시스템</span><span class="sxs-lookup"><span data-stu-id="5b3f5-126">Small Example System</span></span>

<span data-ttu-id="5b3f5-127">NetX Duo Telnet을 사용하는 방법에 대한 예제는 아래 그림 1.1에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-127">An example of how to use NetX Duo Telnet is shown in Figure 1.1 below.</span></span> <span data-ttu-id="5b3f5-128">이 예제에서 텔넷 포함 파일은 7~8번째 줄에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-128">In this example, the Telnet include files *are* brought in at line 7 and 8.</span></span> <span data-ttu-id="5b3f5-129">다음으로, 텔넷 서버는 146번째 줄의 “*tx_application_define*”에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-129">Next, the Telnet Server is created in “*tx_application_define*” at line 146.</span></span> <span data-ttu-id="5b3f5-130">텔넷 서버 및 클라이언트 제어 블록은 이전의 23~24번째 줄에서 전역 변수로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-130">Note that the Telnet Server and Client control blocks are defined as global variables at line 23-24 previously.</span></span>

<span data-ttu-id="5b3f5-131">텔넷 서버 또는 클라이언트를 시작하기 전에 NetX Duo에서 IP 주소의 유효성을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-131">Before the Telnet Server or Client can be started they must validate their IP address with NetX Duo.</span></span> <span data-ttu-id="5b3f5-132">IPv4 연결의 경우 NetX 드라이버가 166번째 줄에서 시스템을 초기화하도록 잠시 기다리면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-132">For IPv4 connections this is accomplished by simply waiting briefly to let the NetX driver initialize the system on line 166.</span></span> <span data-ttu-id="5b3f5-133">IPv6 연결의 경우 171~172번째 줄에서 IPv6 및 ICMPv6를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-133">For IPv6 connections, this requires enabling IPv6 and ICMPv6 which it does in lines 171-172.</span></span> <span data-ttu-id="5b3f5-134">클라이언트는 181~186번째 줄의 기본 인터페이스에 글로벌 및 링크 로컬 IPv6 주소를 설정하고 NetX Duo 유효성 검사가 백그라운드에서 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-134">The Client sets its global and link local IPv6 addresses on the primary interface on lines 181-186 and waits for NetX Duo validation to complete in the background.</span></span> <span data-ttu-id="5b3f5-135">또한 서버는 192~198번째 줄의 기본 인터페이스에 글로벌 및 링크 로컬 주소를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-135">The Server also sets its global and link local addresses on its primary interface in lines 192 – 198.</span></span> <span data-ttu-id="5b3f5-136">*nxd_ipv6_global_address_set* 및 *nxd_ipv6_linklocal_address_set* 서비스는 *nxd_ipv6_address_set* 서비스로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-136">Note that the two services, *nxd_ipv6_global_address_set* and *nxd_ipv6_linklocal_address_set* are replaced with *nxd_ipv6_address_set service*.</span></span> <span data-ttu-id="5b3f5-137">전자의 두 서비스는 레거시 NetX Duo 애플리케이션에서 계속 사용할 수 있지만, 결국에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-137">The former two services are still available for legacy NetX Duo applications but are eventually deprecated.</span></span> <span data-ttu-id="5b3f5-138">개발자는 *nxd_ipv6_address_set* 을 대신 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-138">Developers are encouraged to use *nxd_ipv6_address_set* instead.</span></span>

<span data-ttu-id="5b3f5-139">NetX Duo에서 IP 주소 유효성 검사가 완료되면 *nxd_telnet_server_start* 서비스를 사용하여 215번째 줄에서 텔넷 서버가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-139">After successful IP address validation with NetX Duo, the Telnet Server is started at line 215 using the *nxd_telnet_server_start* service.</span></span> <span data-ttu-id="5b3f5-140">226번째 줄에서 텔넷 클라이언트는 *nx_telnet_client_create* 서비스를 사용하여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-140">At line 226 the Telnet Client is created using the *nx_telnet_client_create* service.</span></span> <span data-ttu-id="5b3f5-141">그런 다음, *nxd_telnet_client_connect* 및 *nx_telnet_client_connect* 서비스를 각각 사용하여 242번째 줄(IPv4 애플리케이션의 경우) 및 238번째 줄(IPv6 애플리케이션의 경우)에서 텔넷 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-141">It then connects with the Telnet Server on line 242 for IPv4 applications and line 238 for IPv6 applications using the *nxd_telnet_client_connect* and *nx_telnet_client_connect* services respectively.</span></span> <span data-ttu-id="5b3f5-142">서버와의 유효성 검사 및 연결이 완료되면 연결을 끊기 전에 몇 가지 교환이 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-142">After successful validation and connection with the server, it makes a few exchanges before disconnecting.</span></span>

```c
/* This is a small demo of TELNET on the high-performance NetX Duo TCP/IP stack.  
       This demo relies on ThreadX and NetX Duo to show a simple TELNET connection,
       send, server echo, and then disconnection from the TELNET server.  */
    
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_telnet_client.h"
#include  "nxd_telnet_server.h"
#define     DEMO_STACK_SIZE         4096    
   
/* Define the ThreadX and NetX object control blocks...  */
TX_THREAD               test_thread;
NX_PACKET_POOL          pool_server;
NX_PACKET_POOL          pool_client;
NX_IP                   ip_server;
NX_IP                   ip_client;
   
/* Define TELNET objects.  */

NX_TELNET_SERVER        my_server;
NX_TELNET_CLIENT        my_client;


#ifdef FEATURE_NX_IPV6

/* Define NetX Duo IP address for the NetX Duo Telnet Server and Client. */

NXD_ADDRESS     server_ip_address;
NXD_ADDRESS     client_ip_address;

#endif

#define         SERVER_ADDRESS          IP_ADDRESS(1,2,3,4)
#define         CLIENT_ADDRESS          IP_ADDRESS(1,2,3,5)

/* Define the counters used in the demo application...  */
ULONG                   error_counter;

/* Define timeout in ticks for connecting and sending/receiving data. */

#define                 TELNET_TIMEOUT  200

/* Define function prototypes.  */

void    thread_test_entry(ULONG thread_input);
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);


/* Define the application's TELNET Server callback routines.  */

void    telnet_new_connection(NX_TELNET_SERVER *server_ptr, UINT 
                              logical_connection); 
void    telnet_receive_data(NX_TELNET_SERVER *server_ptr, UINT logical_connection, 
                            NX_PACKET *packet_ptr);
void    telnet_connection_end(NX_TELNET_SERVER *server_ptr, UINT 
                              logical_connection);

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
CHAR    *pointer;
UINT    iface_index, address_index;
    
    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;
    
    /* Create the main thread.  */
    tx_thread_create(&test_thread, "test thread", thread_test_entry, 0,  
                     pointer, DEMO_STACK_SIZE, 
                     2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;
    
    /* Initialize the NetX system.  */
    nx_system_initialize();
    
    /* Create packet pool.  */
    nx_packet_pool_create(&pool_server, "Server NetX Packet Pool", 600, pointer, 8192);
    pointer = pointer + 8192;
    
    /* Create an IP instance.  */
    nx_ip_create(&ip_server, "Server NetX IP Instance", SERVER_ADDRESS, 
                 0xFFFFFF00UL, &pool_server, _nx_ram_network_driver,
                 pointer, 4096, 1);
    
    pointer =  pointer + 4096;
    
    /* Create another packet pool. */
    nx_packet_pool_create(&pool_client, "Client NetX Packet Pool", 600, 
                          pointer, 8192);
    pointer = pointer + 8192;
    
    /* Create another IP instance.  */
    nx_ip_create(&ip_client, "Client NetX IP Instance", CLIENT_ADDRESS, 
                 0xFFFFFF00UL, &pool_client, _nx_ram_network_driver, 
                 pointer, 4096, 1);
    
    pointer = pointer + 4096;
    
    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_server, (void *) pointer, 1024);
    pointer = pointer + 1024;
    
    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_client, (void *) pointer, 1024);
    pointer = pointer + 1024;
    
    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_server);
    nx_tcp_enable(&ip_client);

#ifdef FEATURE_NX_IPV6

    /* Next set the NetX Duo Telnet Server and Client addresses. */
    server_ip_address.nxd_ip_address.v6[3] = 0x105;
    server_ip_address.nxd_ip_address.v6[2] = 0x0;
    server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

#endif

    /* Create the NetX Duo TELNET Server.  */
    status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_server, 
                                      pointer, 2048, telnet_new_connection, telnet_receive_data, 
                                      telnet_connection_end);
    
    /* Check for errors.  */
    if (status)
        error_counter++;
    
    return;
}

/* Define the test thread.  */
void    thread_test_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;
    
    /* Allow other threads (e.g. IP thread task) to run first. */
    tx_thread_sleep(100);
    
    #ifdef FEATURE_NX_IPV6
    /* Here's where we make the Telnet Client IPv6 enabled. */
    nxd_ipv6_enable(&ip_client);
    nxd_icmp_enable(&ip_client);     
    
    /* Wait till the IP task thread initializes the system. */
    tx_thread_sleep(100);
        
    /* Set up the Client addresses on the Client IP for the primary interface. */
    if_index = 0;
    
    status = nxd_ipv6_address_set(&ip_ client, iface_index, NX_NULL, 10, 
                                  &address_index);
    status = nxd_ipv6_address_set(&ip_ client, iface_index, & client _ip_address, 
                                   64, &address_index);
        
    /* Allow NetX Duo time to validate addresses. */
    tx_thread_sleep(400);
    
    /* Set up the Server addresses on the Client IP. */
    iface_index = 0;
    status = nxd_ipv6_address_set (&ip_server, iface_index, NX_NULL, 10, 
                                   &address_index);
    
    status = nxd_ ipv6_address _set(&ip_server, iface_index, & server _ip_address, 
                                     64, &address_index);
        
    /* Allow NetX Duo time to validate addresses. */     
    tx_thread_sleep(400);
    
    #endif
    
    /* Start the TELNET Server.  */
    status =  nx_telnet_server_start(&my_server);
    
    /* Check for errors.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Create a TELENT client instance.  */
    status =  nx_telnet_client_create(&my_client, "My TELNET Client", 
                                      &ip_client, 600);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    #ifdef FEATURE_NX_IPV6
    
        /* Connect the TELNET client to the TELNET Server at port 23.  */
        status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 
                                             TELNET_TIMEOUT);
    
    #else
        /* Connect the TELNET client to the TELNET Server at port 23.  */
        status =  nx_telnet_client_connect(&my_client, SERVER_ADDRESS, 23,
                                            TELNET_TIMEOUT);
    #endif
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Allocate a packet.  */
    status =  nx_packet_allocate(&pool_client, &my_packet, NX_TCP_PACKET, 
                                  NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Build a simple 1-byte message.  */
    nx_packet_data_append(my_packet, "a", 1, &pool_client, NX_WAIT_FOREVER);
    
    /* Send the packet to the TELNET Server.  */
    status =  nx_telnet_client_packet_send(&my_client, my_packet, TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Pickup the Server header.  */
    status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 
                                               TELNET_TIMEOUT);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* At this point the packet should contain the Server's banner
        message sent by the Server callback function below.  Just
        release it for this demo.  */
    nx_packet_release(my_packet);
    
    /* Pickup the Server echo of the character.  */
    status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 
                                               TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* At this point the packet should contain the character 'a' that
        we sent earlier.  Just release the packet for now.  */
    nx_packet_release(my_packet);
    
    /* Now disconnect form the TELNET Server.  */
    status =  nx_telnet_client_disconnect(&my_client, TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Delete the TELNET Client.  */
    status =  nx_telnet_client_delete(&my_client);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
}

/* This routine is called by the NetX Telnet Server whenever a new Telnet client 
    connection is established.  */
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, UINT logical_connection)
{

UINT        status;
NX_PACKET   *packet_ptr;

    /* Allocate a packet for client greeting. */
    status =  nx_packet_allocate(&pool_server, &packet_ptr, NX_TCP_PACKET, 
                                  NX_NO_WAIT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Build a banner message and a prompt.  */
    nx_packet_data_append(packet_ptr,"**** Welcome to NetX TELNET Server ****\r\n\r\n\r\n", 45,                            
                         &pool_server, NX_NO_WAIT);

    nx_packet_data_append(packet_ptr, "NETX> ", 6, &pool_server, NX_NO_WAIT);
    
    /* Send the packet to the client.  */
    status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                           packet_ptr, TELNET_TIMEOUT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        nx_packet_release(packet_ptr);
    }
    return;
}

/* This routine is called by the NetX Telnet Server whenever data is present on a 
    Telnet client connection.  */          
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, UINT logical_connection,
                          NX_PACKET *packet_ptr)
{

UINT    status;
UCHAR   alpha;

    /* This demo echoes the character back; on <cr,lf> sends a new prompt back to 
        the client.  A real system would likely buffer the character(s) received in a 
        buffer associated with the supplied logical connection and process it.  */

    /* Just throw away carriage returns.  */
    if ((packet_ptr -> nx_packet_prepend_ptr[0] == '\r') && (packet_ptr -> nx_packet_length == 1))
    {
        printf("telnet server received just a CRLF\n");

        nx_packet_release(packet_ptr);
        return;
    }

    /* Setup new line on line feed.  */
    if ((packet_ptr -> nx_packet_prepend_ptr[0] == '\n') || (packet_ptr -> nx_packet_prepend_ptr[1] == '\n'))
    {
        /* Clean up the packet.  */
        packet_ptr -> nx_packet_length =  0;
        packet_ptr -> nx_packet_prepend_ptr =  packet_ptr -> nx_packet_data_start + NX_TCP_PACKET;
        packet_ptr -> nx_packet_append_ptr =   packet_ptr -> nx_packet_data_start + NX_TCP_PACKET;

        /* Build the next prompt.  */
        nx_packet_data_append(packet_ptr, "\r\nNETX> ", 8, &pool_server, 
                              NX_NO_WAIT);

        /* Send the packet to the client.  */
        status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                               packet_ptr, TELNET_TIMEOUT);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            nx_packet_release(packet_ptr);
        }
        return;
    }

    /* Pickup first character (usually only one from client).  */
    alpha =  packet_ptr -> nx_packet_prepend_ptr[0];

    /* Echo character.  */
    status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                           packet_ptr, TELNET_TIMEOUT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        nx_packet_release(packet_ptr);
    }

    /* Check for a disconnection.  */
    if (alpha == 'q')
    {
        /* Initiate server disconnection.  */
        nx_telnet_server_disconnect(server_ptr, logical_connection);
    }
}


/* This routine is called by the NetX Telnet Server when the client disconnects.  */
void  telnet_connection_end(NX_TELNET_SERVER *server_ptr, UINT logical_connection)
{
    /* Cleanup any application specific connection or buffer information.  */
    return;
}
```

## <a name="configuration-options"></a><span data-ttu-id="5b3f5-143">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="5b3f5-143">Configuration Options</span></span>

<span data-ttu-id="5b3f5-144">NetX Duo용 텔넷을 빌드하기 위한 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-144">There are several configuration options for building Telnet for NetX Duo.</span></span> <span data-ttu-id="5b3f5-145">해당 #defines는 *nxd_telnet_server.h* 및 *nxd_telnet_client.h* 를 포함하기 전에 애플리케이션에서 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-145">These #defines can be set by the application prior to inclusion of *nxd_telnet_server.h*.and *nxd_telnet_client.h.*</span></span>

<span data-ttu-id="5b3f5-146">다음은 각 옵션에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-146">Following is a list of all options, where each is described in detail:</span></span>  
  
- <span data-ttu-id="5b3f5-147">**NX_DISABLE_ERROR_CHECKING**: 정의된 이 옵션은 기본 텔넷 오류 검사를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-147">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic Telnet error checking.</span></span> <span data-ttu-id="5b3f5-148">일반적으로 애플리케이션이 디버그된 후에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-148">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="5b3f5-149">**NX_TELNET_MAX_CLIENTS**: 서버 스레드에서 지원하는 최대 텔넷 클라이언트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-149">**NX_TELNET_MAX_CLIENTS**: The maximum number of Telnet Clients supported by the Server thread.</span></span> <span data-ttu-id="5b3f5-150">기본적으로 이 값은 4로 정의되어 한 번에 최대 4개의 클라이언트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-150">By default, this value is defined as 4 to specify a maximum of 4 clients at a time.</span></span>
- <span data-ttu-id="5b3f5-151">**NX_TELNET_SERVER_PRIORITY**: 텔넷 서버 스레드의 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-151">**NX_TELNET_SERVER_PRIORITY**: The priority of the Telnet Server thread.</span></span> <span data-ttu-id="5b3f5-152">기본적으로 이 값은 16으로 정의되어 우선 순위 16을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-152">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="5b3f5-153">**NX_TELNET_TOS**: 텔넷 TCP 요청에 필요한 서비스 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-153">**NX_TELNET_TOS**: Type of service required for the Telnet TCP requests.</span></span> <span data-ttu-id="5b3f5-154">기본적으로 이 값은 NX_IP_NORMAL로 정의되어</span><span class="sxs-lookup"><span data-stu-id="5b3f5-154">By default, this value is defined as NX_IP_NORMAL to indicate</span></span>  
<span data-ttu-id="5b3f5-155">일반 IP 패킷 서비스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-155">normal IP packet service.</span></span>
- <span data-ttu-id="5b3f5-156">**NX_TELNET_FRAGMENT_OPTION**: 텔넷 TCP 요청에 조각을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-156">**NX_TELNET_FRAGMENT_OPTION**: Fragment enable for Telnet TCP requests.</span></span> <span data-ttu-id="5b3f5-157">기본적으로 이 값은 텔넷 TCP 조각화를 사용하지 않도록 설정하는 NX_DONT_FRAGMENT입니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-157">By default, this value is NX_DONT_FRAGMENT to disable Telnet TCP fragmenting.</span></span>
- <span data-ttu-id="5b3f5-158">**NX_TELNET_SERVER_WINDOW_SIZE**: 서버 소켓 창 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-158">**NX_TELNET_SERVER_WINDOW_SIZE**: Server socket window size.</span></span> <span data-ttu-id="5b3f5-159">기본적으로 이 값은 2048바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-159">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="5b3f5-160">**NX_TELNET_TIME_TO_LIVE**: 이 패킷이 삭제되기 전에 통과할 수 있는 라우터 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-160">**NX_TELNET_TIME_TO_LIVE**: Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="5b3f5-161">기본값은 0x80으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-161">The default value is set to 0x80.</span></span>
- <span data-ttu-id="5b3f5-162">**NX_TELNET_SERVER_TIMEOUT**: 내부 서비스가 일시 중단될 ThreadX 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-162">**NX_TELNET_SERVER_TIMEOUT**: Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="5b3f5-163">기본값은 10초로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-163">The default value is set to 10 seconds.</span></span>
- <span data-ttu-id="5b3f5-164">**NX_TELNET_ACTIVITY_TIMEOUT**: 서버가 클라이언트 연결을 끊기 전에 작업 없이 경과될 수 있는 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-164">**NX_TELNET_ACTIVITY_TIMEOUT**: Specifies the number of seconds that can elapse without any activity before the Server disconnects the Client connection.</span></span> <span data-ttu-id="5b3f5-165">기본값은 600초로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-165">The default value is set to 600 seconds.</span></span>
- <span data-ttu-id="5b3f5-166">**NX_TELNET_TIMEOUT_PERIOD**: 클라이언트 작업 시간 초과를 확인하는 간격(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-166">**NX_TELNET_TIMEOUT_PERIOD**: Specifies the number of seconds between checking for Client activity timeouts.</span></span> <span data-ttu-id="5b3f5-167">기본값은 60초로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-167">The default value is set to 60 seconds.</span></span>
- <span data-ttu-id="5b3f5-168">**NX_TELNET_SERVER_OPTION_DISABLE**: 정의된 텔넷 옵션 협상을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-168">**NX_TELNET_SERVER_OPTION_DISABLE**: Defined, Telnet option negotiation is disabled.</span></span> <span data-ttu-id="5b3f5-169">이 옵션은 기본적으로 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-169">By default this option is not defined.</span></span>
- <span data-ttu-id="5b3f5-170">**NX_TELNET_SERVER_USER_CREATE_PACKET_POOL**: 정의된 경우 텔넷 서버 패킷 풀을 외부에서 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-170">**NX_TELNET_SERVER_USER_CREATE_PACKET_POOL**: If defined, the Telnet Server packet pool must be created externally.</span></span> <span data-ttu-id="5b3f5-171">NX_TELNET_SERVER_OPTION_DISABLE이 정의되지 않은 경우에만 의미가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-171">This is only meaningful if NX_TELNET_SERVER_OPTION_DISABLE is not defined.</span></span> <span data-ttu-id="5b3f5-172">기본적으로 이 옵션은 정의되어 있지 않으며 텔넷 서버 스레드는 자체의 패킷 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-172">By default this option is not defined and the Telnet Server thread creates its own packet pool.</span></span>
- <span data-ttu-id="5b3f5-173">**NX_TELNET_SERVER_PACKET_PAYLOAD**: 옵션 협상을 위해 텔넷 서버에서 만든 패킷 페이로드의 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-173">**NX_TELNET_SERVER_PACKET_PAYLOAD**: Defines the size of the packet payload created by the Telnet Server for option negotiation.</span></span> <span data-ttu-id="5b3f5-174">텔넷 서버는 NX_TELNET_SERVER_OPTION_DISABLE이 정의되지 않은 경우에만 이 패킷 풀을 만듭니다(텔넷 옵션 사용).</span><span class="sxs-lookup"><span data-stu-id="5b3f5-174">Note that the Telnet Server only creates this packet pool if NX_TELNET_SERVER _OPTION_DISABLE is not defined (Telnet options are enabled).</span></span> <span data-ttu-id="5b3f5-175">이 옵션의 기본값은 300입니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-175">The default value of this option is 300.</span></span>
- <span data-ttu-id="5b3f5-176">**NX_TELNET_SERVER_PACKET_POOL_SIZE**: 텔넷 협상에 사용되는 텔넷 서버 패킷 풀의 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-176">**NX_TELNET_SERVER_PACKET_POOL_SIZE**: Defines the size of the Telnet Server packet pool used for Telnet negotiations.</span></span> <span data-ttu-id="5b3f5-177">텔넷 서버는 NX_TELNET_SERVER_OPTION_DISABLE이 정의되지 않은 경우에만 이 패킷 풀을 만듭니다(텔넷 옵션 사용).</span><span class="sxs-lookup"><span data-stu-id="5b3f5-177">Note that the Telnet Server only creates this packet pool if NX_TELNET_SERVER _OPTION_DISABLE is not defined (Telnet options are enabled).</span></span> <span data-ttu-id="5b3f5-178">이 옵션의 기본값은 2048(약 5~6개 패킷)입니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f5-178">The default value of this option is 2048 (\~5-6 packets).</span></span>
