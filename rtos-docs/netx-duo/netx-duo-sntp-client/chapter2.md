---
title: 2장 - Azure RTOS NetX Duo SNTP 클라이언트 설치 및 사용
description: 이 장에서는 NetX Duo SNTP 클라이언트의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd917e7e70ce21dbff6c8081c2ff115c0acad8a8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810566"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-sntp-client"></a><span data-ttu-id="daa76-103">2장 - Azure RTOS NetX Duo SNTP 클라이언트 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="daa76-103">Chapter 2 - Installation and Use of Azure RTOS NetX Duo SNTP Client</span></span>

<span data-ttu-id="daa76-104">이 장에서는 Azure RTOS NetX Duo SNTP 클라이언트의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo SNTP Client.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="daa76-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="daa76-105">Product Distribution</span></span>

<span data-ttu-id="daa76-106">NetX Duo용 SNTP는 [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-106">SNTP for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="daa76-107">이 패키지에는 다음과 같이 두 개의 소스 파일과 이 문서가 포함된 PDF 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="daa76-108">**nxd_sntp_client.c** SNTP 클라이언트 C 소스 파일</span><span class="sxs-lookup"><span data-stu-id="daa76-108">**nxd_sntp_client.c** SNTP Client C source file</span></span>  
- <span data-ttu-id="daa76-109">**nxd_sntp_client.h** SNTP 클라이언트 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="daa76-109">**nxd_sntp_client.h** SNTP Client Header file</span></span>  
- <span data-ttu-id="daa76-110">**demo_netxduo_sntp_client.c** 데모 SNTP 클라이언트 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="daa76-110">**demo_netxduo_sntp_client.c** Demonstration SNTP Client application</span></span>  
- <span data-ttu-id="daa76-111">**nxd_sntp_client.pdf** NetX Duo SNTP 클라이언트 사용자 가이드</span><span class="sxs-lookup"><span data-stu-id="daa76-111">**nxd_sntp_client.pdf** NetX Duo SNTP Client User Guide</span></span>  

## <a name="netx-duo-sntp-client-installation"></a><span data-ttu-id="daa76-112">NetX Duo SNTP 클라이언트 설치</span><span class="sxs-lookup"><span data-stu-id="daa76-112">NetX Duo SNTP Client Installation</span></span>

<span data-ttu-id="daa76-113">NetX Duo용 SNTP를 사용하려면 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-113">In order to use SNTP for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="daa76-114">예를 들어 NetX Duo가 "\threadx\arm7\green" 디렉터리에 설치된 경우 NETX Duo SNTP 클라이언트 파일 nxd_sntp_client.c 및 nxd_sntp_client.h(NetX의 nx_sntp_client.c 및 nx_sntp_client.h)를 이 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-114">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the NetX Duo SNTP Client files *nxd_sntp_client.c* and *nxd_sntp_client.h* (*nx_sntp_client.c* and *nx_sntp_client.h* in NetX) should be copied into this directory.</span></span>

## <a name="using-netx-duo-sntp-client"></a><span data-ttu-id="daa76-115">NetX Duo SNTP 클라이언트 사용</span><span class="sxs-lookup"><span data-stu-id="daa76-115">Using NetX Duo SNTP Client</span></span>

<span data-ttu-id="daa76-116">NetX Duo SNTP 클라이언트를 사용하는 것은 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-116">Using NetX Duo SNTP Client is easy.</span></span> <span data-ttu-id="daa76-117">기본적으로 ThreadX 및 NetX Duo를 각각 사용하기 위해서는 애플리케이션 코드에  tx_api.h, fx_api.h 및 nx_api.h가 포함된 후 nxd_sntp_client.h가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-117">Basically, the application code must include *nxd_sntp_client.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="daa76-118">nxd_sntp_client.h가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 SNTP 함수 호출을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-118">Once *nxd_sntp_client.h* is included, the application code is then able to make the SNTP function calls specified later in this guide.</span></span> <span data-ttu-id="daa76-119">애플리케이션은 빌드 프로세스에 nxd_sntp_client.c도 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-119">The application must also include *nxd_sntp_client.c* in the build process.</span></span> <span data-ttu-id="daa76-120">이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 해당 개체 형식을 애플리케이션의 파일에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="daa76-121">이 작업은 NetX Duo SNTP 클라이언트를 사용하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-121">This is all that is required to use NetX Duo SNTP Client.</span></span>

> [!NOTE]
> <span data-ttu-id="daa76-122">NetX Duo SNTP 클라이언트는 NetX Duo UDP 서비스를 활용하므로, SNTP 서비스를 사용 하기 전에 nx_udp_enable 호출을 통해 UDP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-122">Since the NetX Duo SNTP Client utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using SNTP services.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="daa76-123">간단한 예제 시스템</span><span class="sxs-lookup"><span data-stu-id="daa76-123">Small Example System</span></span>

<span data-ttu-id="daa76-124">NetX Duo SNTP를 사용하는 방법의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-124">An example of how to use NetX Duo SNTP is shown below.</span></span> <span data-ttu-id="daa76-125">이 예제가 사용자 시스템에서도 그대로 작동될 것으로 보장할 수는 **없습니다**.</span><span class="sxs-lookup"><span data-stu-id="daa76-125">Note that this example is **not** guaranteed to work as is on your system.</span></span> <span data-ttu-id="daa76-126">특정 시스템 및 하드웨어를 조정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-126">You may need to make adjustments for your particular system and hardware.</span></span> <span data-ttu-id="daa76-127">예를 들어, NetX ram 드라이버를 실제 드라이버 함수로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-127">For example you will have to replace the NetX ram driver with your actual driver function.</span></span> <span data-ttu-id="daa76-128">이 예제는 예시 목적으로만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-128">This example is intended strictly for demonstration purposes.</span></span>

<span data-ttu-id="daa76-129">이 예제에는 SNTP 헤더 파일 nxd_sntp_client.h가  포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-129">In this example, the SNTP header file *nxd_sntp_client.h* is included.</span></span> <span data-ttu-id="daa76-130">SNTP 클라이언트는 "tx_application_define"에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-130">The SNTP Client is created in “*tx_application_define*”.</span></span> <span data-ttu-id="daa76-131">소멸(kiss of death) 및 윤초 처리기 함수는 SNTP 클라이언트를 만들 때 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-131">Note that the kiss of death and leap second handler functions are optional when creating the SNTP Client.</span></span>

<span data-ttu-id="daa76-132">이 데모는 IPv6 또는 IPv4에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-132">This demo can be used with IPv6 or IPv4.</span></span> <span data-ttu-id="daa76-133">IPv6을 통해 SNTP 클라이언트를 실행하려면 USE_IPV6를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-133">To run the SNTP Client over IPv6, define USE_IPV6.</span></span> <span data-ttu-id="daa76-134">IPv6을 NetX Duo에서도 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-134">IPv6 must be enabled in NetX Duo as well.</span></span> <span data-ttu-id="daa76-135">SNTP 클라이언트 호스트는 IPv6 주소 유효성 검사와 NetX Duo의 ICMPv6 및 IPv6 서비스에 대해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-135">The SNTP Client host is set up for IPv6 address validation and ICMPv6 and IPv6 services in NetX Duo.</span></span> <span data-ttu-id="daa76-136">NetX Duo의 IPv6 지원에 대한 자세한 내용은 NetX Duo 사용자 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="daa76-136">See the NetX Duo User Guide for more details on IPv6 support in NetX Duo.</span></span>

<span data-ttu-id="daa76-137">그런 후 유니캐스트 또는 브로드캐스트 모드에 대해 SNTP 클라이언트를 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-137">Then the SNTP Client must be initialized for either unicast or broadcast mode.</span></span>

<span data-ttu-id="daa76-138">SNTP 클라이언트는 초기에 서버 시간 업데이트를 자체 내부 데이터 구조에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-138">SNTP Client initially writes Server time updates to its own internal data structure.</span></span> <span data-ttu-id="daa76-139">이 시간은 디바이스 현지 시간과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-139">This is not the same as the device local time.</span></span> <span data-ttu-id="daa76-140">디바이스 현지 시간은 SNTP 클라이언트 스레드를 시작하기 전에 SNTP 클라이언트에서 기준 시간으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-140">The device local time can be set as a baseline time in the SNTP Client before starting the SNTP Client thread.</span></span> <span data-ttu-id="daa76-141">첫 번째 서버 업데이트를 NX_SNTP_CLIENT_MAX_ADJUSTMENT(기본값 180밀리초)와 비교하도록 SNTP 클라이언트를 구성하는 경우(NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP을 NX_FALSE로 설정)에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-141">This is useful if the SNTP Client is configured (NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP set to NX_FALSE) to compare the first Server update to the NX_SNTP_CLIENT_MAX_ADJUSTMENT (default value 180 milliseconds).</span></span> <span data-ttu-id="daa76-142">그러지 않으면 SNTP 클라이언트는 서버에서 첫 번째 업데이트를 가져오는 경우 초기 현지 시간을 직접 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-142">Otherwise the SNTP Client will set the initial local time directly when it gets the first update from the Server.</span></span>

<span data-ttu-id="daa76-143">기준 시간은 *nx_sntp_client_set_local_time* 서비스를 사용하여 SNTP 클라이언트에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-143">A baseline time is applied to the SNTP Client using the *nx_sntp_client_set_local_time* service.</span></span>

<span data-ttu-id="daa76-144">SNTP 클라이언트는 유니캐스트 및 브로드캐스트 모드에 대해 별도로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-144">The SNTP Client is started on for unicast and broadcast mode respectively.</span></span> <span data-ttu-id="daa76-145">특정 간격(유니캐스트 폴링 간격보다 약간 작음) 동안 애플리케이션은 현재 시간(초 및 밀리초)을 증가시켜 시뮬레이트하는 "실시간 클럭"에서 *nx_sntp_client_set_local_time* 을 사용하여 SNTP 클라이언트 현지 시간을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-145">For a certain interval (slightly less than the unicast polling interval) the application updates the SNTP Client local time, using the *nx_sntp_client_set_local_time*, from the “real time clock” which we simulate by just incrementing the seconds and milliseconds of the current time.</span></span> <span data-ttu-id="daa76-146">각 간격 후 애플리케이션은 주기적으로 SNTP 서버에서 업데이트를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-146">After each interval, the application then periodically checks for updates from the SNTP server.</span></span> <span data-ttu-id="daa76-147">*nx_sntp_client_receiving _updates* 서비스는 SNTP 클라이언트가 현재 유효한 업데이트를 수신하고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-147">The *nx_sntp_client_receiving _updates* service verifies that the SNTP Client is currently receiving valid updates.</span></span> <span data-ttu-id="daa76-148">이 경우 *nx_sntp_client_get_local_time_extended* 서비스를 사용하여 최신 업데이트 시간을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-148">If so, it will retrieve the latest update time using the *nx_sntp_client_get_local_time_extended* service.</span></span>

<span data-ttu-id="daa76-149">예를 들어, SNTP 클라이언트가 더 이상 유효한 업데이트를 받지 못하는 것이 확인될 경우 *nx_sntp_client_stop* 서비스를 사용하여 언제든지 SNTP 클라이언트를 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-149">The SNTP Client can be stopped at any time using the *nx_sntp_client_stop* service if for example it detects the SNTP Client is no longer receiving valid updates..</span></span> <span data-ttu-id="daa76-150">클라이언트를 다시 시작하려면 애플리케이션은 유니캐스트 또는 브로드캐스트 초기화 서비스 중 하나를 호출한 다음, 유니캐스트 또는 브로드캐스트 실행 서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-150">To restart the Client, the application must call either the unicast or broadcast initialize service and then call either unicast or broadcast run services.</span></span> <span data-ttu-id="daa76-151">SNTP 클라이언트 스레드 작업이 중지된 동안 필요한 경우 SNTP 클라이언트는 SNTP 서버 및 모드(유니캐스트 또는 브로드캐스트)를 전환할 수 있습니다. 예를 들어, 이전 SNTP 서버는 중단된 것처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-151">While the SNTP Client thread task is stopped, the SNTP Client can switch SNTP servers and modes (unicast or broadcast) if needed e.g. the previous SNTP server appears to be down.</span></span>

```c
/* 
   This is a small demo of the NetX SNTP Client on the high-performance NetX
   TCP/IP stack. This demo relies on Thread, NetX and NetX SNTP Client API to
   execute the Simple Network Time Protocol in unicast and broadcast modes.  
 */

#include <stdio.h>
#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_sntp_client.h"
                
/* Define SNTP packet size. */
#define NX_SNTP_CLIENT_PACKET_SIZE      (NX_UDP_PACKET + 100)

/* Define SNTP packet pool size. */
#define NX_SNTP_CLIENT_PACKET_POOL_SIZE      (4 * (NX_SNTP_CLIENT_PACKET_SIZE + 
                                                            sizeof(NX_PACKET)))

/* Define how often the demo checks for SNTP updates. */
#define DEMO_PERIODIC_CHECK_INTERVAL      (1 * NX_IP_PERIODIC_RATE) 

/* Define how often we check on SNTP server status. 
   We expect updates from the SNTP server about every hour using 
   the SNTP Client defaults. For testing
   make this (much) shorter. */
#define CHECK_SNTP_UPDATES_TIMEOUT       (180 * NX_IP_PERIODIC_RATE) 

/* Set up generic network driver for demo program. */
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Application defined services of the NetX SNTP Client. */

UINT leap_second_handler(NX_SNTP_CLIENT *client_ptr, 
                                UINT leap_indicator);
UINT kiss_of_death_handler(NX_SNTP_CLIENT *client_ptr, 
                                        UINT KOD_code);
VOID time_update_callback(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                       NX_SNTP_TIME *local_time);


/* Set up client thread and network resources. */

NX_PACKET_POOL      client_packet_pool;
NX_IP               client_ip;
TX_THREAD           demo_client_thread;
NX_SNTP_CLIENT      demo_sntp_client;
TX_EVENT_FLAGS_GROUP sntp_flags;

#define DEMO_SNTP_UPDATE_EVENT  1

/* Configure the SNTP Client to use IPv6. If not enabled, the 
   Client will use IPv4.  Note: IPv6 must be enabled in NetX Duo
   for the Client to communicate over IPv6.    */
#ifdef FEATURE_NX_IPV6
/* #define USE_IPV6 */
#endif /* FEATURE_NX_IPV6 */


/* Configure the SNTP Client to use unicast SNTP. */
#define USE_UNICAST


#define CLIENT_IP_ADDRESS       IP_ADDRESS(192,2,2,66)
#define SERVER_IP_ADDRESS       IP_ADDRESS(192,2,2,92)
#define SERVER_IP_ADDRESS_2     SERVER_IP_ADDRESS

/* Set up the SNTP network and address index; */
UINT     iface_index =0;
UINT     prefix = 64;   
UINT     address_index;

/* Set up client thread entry point. */
void    demo_client_thread_entry(ULONG info);

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return 0;
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UINT     status;
UCHAR    *free_memory_pointer;


    free_memory_pointer = (UCHAR *)first_unused_memory;

    /* Create client packet pool. */
    status =  nx_packet_pool_create(&client_packet_pool, 
                                "SNTP Client Packet Pool",
                                NX_SNTP_CLIENT_PACKET_SIZE, 
                                free_memory_pointer, 
                                NX_SNTP_CLIENT_PACKET_POOL_SIZE);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        return;
    }

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + NX_SNTP_CLIENT_PACKET_POOL_SIZE;

    /* Create Client IP instances */
    status = nx_ip_create(&client_ip, "SNTP IP Instance", 
                                        CLIENT_IP_ADDRESS, 
                                        0xFFFFFF00UL, 
                                        &client_packet_pool, 
                                       _nx_ram_network_driver, 
                                       free_memory_pointer, 2048, 1);
    
    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }

    free_memory_pointer =  free_memory_pointer + 2048;

#ifndef NX_DISABLE_IPV4
    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 2048);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }
#endif /* NX_DISABLE_IPV4  */

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;
    
    /* Enable UDP for client. */
    status =  nx_udp_enable(&client_ip);
    
    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }

#ifndef NX_DISABLE_IPV4
    status = nx_icmp_enable(&client_ip);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }
#endif /* NX_DISABLE_IPV4  */

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "SNTP Client Thread", 
                                                demo_client_thread_entry, 
                                              (ULONG)(&demo_sntp_client), 
                                                free_memory_pointer, 2048, 
                                                  4, 4, TX_NO_TIME_SLICE, 
                                                        TX_DONT_START);

    /* Check for errors */
    if (status != TX_SUCCESS)
    {

        return;
    }

    /* Create the event flags. */
    status = tx_event_flags_create(&sntp_flags, "SNTP event flags");

    /* Check for errors */
    if (status != TX_SUCCESS)
    {

        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* set the SNTP network interface to the primary interface. */
    iface_index = 0;

    /* Create the SNTP Client to run in broadcast mode.. */
status =  nx_sntp_client_create(&demo_sntp_client, &client_ip,
                           iface_index, &client_packet_pool,  
                               leap_second_handler, 
                               kiss_of_death_handler, 
                               NULL /* no random_number_generator callback */);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        /* Bail out!*/
        return;
    }

    tx_thread_resume(&demo_client_thread);

    return;
}

/* Define size of buffer to display client's local time. */
#define BUFSIZE 50

/* Define the client thread.  */
void    demo_client_thread_entry(ULONG info)
{

UINT   status;
UINT   spin;
UINT   server_status;
ULONG  base_seconds;
ULONG  base_fraction;
ULONG  seconds, milliseconds, microseconds, fraction;
UINT   wait = 0;
UINT   error_counter = 0;
ULONG  events = 0;
#ifdef USE_IPV6
NXD_ADDRESS sntp_server_address;
NXD_ADDRESS client_ip_address;
#endif

    NX_PARAMETER_NOT_USED(info);

    /* Give other threads (IP instance) initialize first. */
    tx_thread_sleep(NX_IP_PERIODIC_RATE); 

#ifdef USE_IPV6
    /* Set up IPv6 services. */
    status = nxd_ipv6_enable(&client_ip);

    status += nxd_icmp_enable(&client_ip);

    if (status  != NX_SUCCESS)
        return;

    client_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Set the IPv6 server address. */
    sntp_server_address.nxd_ip_address.v6[0] = 0x20010db8;  
    sntp_server_address.nxd_ip_address.v6[1] = 0x0000f101;
    sntp_server_address.nxd_ip_address.v6[2] = 0x0;
    sntp_server_address.nxd_ip_address.v6[3] = 0x00000106;
    sntp_server_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address. */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, NULL);

    /* Check for link local address set error.  */
    if (status != NX_SUCCESS) 
    {
        return;
    }

     /* Set the host global IP address. We are assuming a 64 
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, 
                                        &client_ip_address, 
                                    prefix, &address_index);

    /* Check for global address set error.  */
    if (status != NX_SUCCESS) 
    {
        return;
    }

    /* Wait while NetX Duo validates the global and link local addresses. */
    tx_thread_sleep(5 * NX_IP_PERIODIC_RATE);

#endif

    /* Setup time update callback function. */
    nx_sntp_client_set_time_update_notify(&demo_sntp_client, 
                                        time_update_callback);

    /* Set up client time updates depending on mode. */
#ifdef USE_UNICAST

    /* Initialize the Client for unicast mode to 
       poll the SNTP server once an hour. */
#ifdef USE_IPV6
/* Use the duo service to set up the Client and set the IPv6 SNTP server.
   Note: this can take either an IPv4 or IPv6 address. */
    status = nxd_sntp_client_initialize_unicast(&demo_sntp_client, 
                                            &sntp_server_address);
#else
    /* Use the IPv4 service to set up the Client and set the IPv4 SNTP server. */
    status = nx_sntp_client_initialize_unicast(&demo_sntp_client, 
                                                SERVER_IP_ADDRESS);
#endif  /* USE_IPV6 */


#else   /* Broadcast mode */

/* Initialize the Client for broadcast mode, no roundtrip calculation
   required and a broadcast SNTP service. */
#ifdef USE_IPV6
    /* Use the duo service to initialize the Client 
       and set IPv6 SNTP all hosts multicast address. 
       (Note: This can take either an IPv4 or IPv6 address.)*/
    status = nxd_sntp_client_initialize_broadcast(&demo_sntp_client, 
                                                &sntp_server_address, 
                                                            NX_NULL);
#else

    /* Use the IPv4 service to initialize the Client and set 
       IPv4 SNTP broadcast address. */
    status = nx_sntp_client_initialize_broadcast(&demo_sntp_client,  
                                                NX_NULL, 
                                                SERVER_IP_ADDRESS);
#endif  /* USE_IPV6 */
#endif  /* USE_UNICAST */

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Set the base time which is approximately the number of seconds since
       the turn of the last century. If this is not available in SNTP format,
       the nx_sntp_client_utility_add_msecs_to_ntp_time service can convert
       milliseconds to fraction.  For how to compute NTP seconds from real
   time, read the NetX SNTP User Guide. Otherwise set the base time to 
   zero and set NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP to NX_TRUE for
       the SNTP CLient to accept the first time update without applying a
       minimum or maximum adjustment parameters
      (NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT and
       NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT). */

    base_seconds =  0xd2c96b90;  /* Jan 24, 2012 UTC */
    base_fraction = 0xa132db1e;

    /* Apply to the SNTP Client local time.  */
status = nx_sntp_client_set_local_time(&demo_sntp_client, base_seconds,
                                base_fraction);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Run whichever service the client is configured for. */
#ifdef USE_UNICAST
    status = nx_sntp_client_run_unicast(&demo_sntp_client);
#else
    status = nx_sntp_client_run_broadcast(&demo_sntp_client);
#endif  /* USE_UNICAST */

    if (status != NX_SUCCESS)
    {
        return;
    }

    spin = NX_TRUE;

    /* Now check periodically for time changes. */
    while(spin)
    {
        /* Wait for a server update event. */
        tx_event_flags_get(&sntp_flags, DEMO_SNTP_UPDATE_EVENT, 
                                          TX_OR_CLEAR, &events, 
                                 DEMO_PERIODIC_CHECK_INTERVAL);

        if (events == DEMO_SNTP_UPDATE_EVENT)
        {

            /* Check for valid SNTP server status. */
            status = nx_sntp_client_receiving_updates(&demo_sntp_client,
                                               &server_status);

            if ((status != NX_SUCCESS) || (server_status == NX_FALSE))
            {

                /* We do not have a valid update. Skip processing any time
                   data. If this happens repeatedly, consider stopping the
                   SNTP Client thread, picking another SNTP server and
                   resuming the SNTP Client thread task (more details about
                   that in the comments at the end of this function).
                 
                   If SNTP Client configurable parameters are too restrictive,
                   such as Max Adjustment, that may also cause valid server
                   updates to be rejected. Configurable parameters, however,
                   cannot be changed at run time.
                 */
                 
                continue;
            }

            /* We have a valid update.  Get the SNTP Client time.  */
            status = nx_sntp_client_get_local_time_extended(&demo_sntp_client, 
                                                    &seconds, &fraction,  
                                                    NX_NULL, 0); 

            /* Convert fraction to microseconds. */
            nx_sntp_client_utility_fraction_to_usecs(fraction, &microseconds);

            milliseconds = ((microseconds + 500) / 1000);

            if (status != NX_SUCCESS)
            {
                printf("Internal error with getting local time 0x%x\n", 
                       status);
                error_counter++;
            }
            else
            {
                printf("\nSNTP updated\n");
                printf("Time: %lu.%03lu sec.\r\n", seconds, milliseconds);
            }

            /* Clear all events in our event flag. */
            events = 0;
        }
        else
        {

            /* No SNTP update event.             
               In the meantime, if we have an RTC we might want to check
               its notion of time. In this demo, we simulate the passage of 
               time on our 'RTC' really just the CPU counter, assuming that 
               seconds and milliseconds have previously been set to a base 
              (starting) time (as was the SNTP Client before running it) 
             */

            seconds += 1;
            milliseconds += 1;

            /* Update our timer. */
            wait += DEMO_PERIODIC_CHECK_INTERVAL;

            /* Check if it is time to display the local 'RTC' time. */
            if (wait >= CHECK_SNTP_UPDATES_TIMEOUT)
            {
                /* It is. Reset the timeout and print local time. */
                wait = 0;

                printf("Time: %lu.%03lu sec.\r\n", seconds, milliseconds);
            }           
        }
    }

/* We can stop the SNTP service if for example we think the SNTP server 
   has stopped sending updates.
     
       To restart the SNTP Client, simply call the
       nx_sntp_client_initialize_unicast or
       nx_sntp_client_initialize_broadcast using another SNTP server IP
       address as input, and resume the SNTP Client by calling
       nx_sntp_client_run_unicast or
       nx_sntp_client_run_braodcast. */
    status = nx_sntp_client_stop(&demo_sntp_client);

    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* When done with the SNTP Client, we delete it */
    status = nx_sntp_client_delete(&demo_sntp_client);

    return;
}


/* This application defined handler for handling an 
   impending leap second is not required by 
   the SNTP Client. The default handler below only logs the
   event for every time stamp received with the 
   leap indicator set.  */

UINT leap_second_handler(NX_SNTP_CLIENT *client_ptr, 
                                UINT leap_indicator)
{
    NX_PARAMETER_NOT_USED(client_ptr);
    NX_PARAMETER_NOT_USED(leap_indicator);

    /* Handle the leap second handler... */

    return NX_SUCCESS;
}

/* This application defined handler for handling 
   a Kiss of Death packet is not required by the SNTP Client. 
   A KOD handler should determine if the Client task should continue vs. 
   abort sending/receiving time data from its current time server, 
   and if aborting if it should remove
   the server from its active server list. 

   Note that the KOD list of codes is subject to change. The list
   below is current at the time of this software release. */

UINT kiss_of_death_handler(NX_SNTP_CLIENT *client_ptr, UINT KOD_code)
{

UINT    remove_server_from_list = NX_FALSE;
UINT    status = NX_SUCCESS;

    NX_PARAMETER_NOT_USED(client_ptr);

    /* Handle kiss of death by code group. */
    switch (KOD_code)
    {

        case NX_SNTP_KOD_RATE:
        case NX_SNTP_KOD_NOT_INIT:
        case NX_SNTP_KOD_STEP:

            /* Find another server while this one 
               is temporarily out of service.  */
            status =  NX_SNTP_KOD_SERVER_NOT_AVAILABLE;

        break;

        case NX_SNTP_KOD_AUTH_FAIL:
        case NX_SNTP_KOD_NO_KEY:
        case NX_SNTP_KOD_CRYP_FAIL:

            /* These indicate the server will not 
               service client with time updates
               without successful authentication. */


            remove_server_from_list =  NX_TRUE;

        break;


        default:

            /* All other codes. Remove server 
               before resuming time updates. */

            remove_server_from_list =  NX_TRUE;
        break;
    }

    /* Removing the server from the active server list? */
    if (remove_server_from_list)
    {

        /* Let the caller know it has to bail on 
           this server before resuming service. */
        status = NX_SNTP_KOD_REMOVE_SERVER;
    }

    return status;
}


/* This application defined handler for notifying SNTP time update event.  */

VOID time_update_callback(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                       NX_SNTP_TIME *local_time)
{
    tx_event_flags_set(&sntp_flags, DEMO_SNTP_UPDATE_EVENT, TX_OR);
}

```

<span data-ttu-id="daa76-152">그림 1 NetX Duo에서 SNTP 클라이언트를 사용하는 예제</span><span class="sxs-lookup"><span data-stu-id="daa76-152">Figure 1 Example of using SNTP Client with NetX Duo</span></span>

## <a name="configuration-options"></a><span data-ttu-id="daa76-153">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="daa76-153">Configuration Options</span></span>

<span data-ttu-id="daa76-154">NetX Duo SNTP 클라이언트를 정의하는 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-154">There are several configuration options for defining the NetX Duo SNTP Client.</span></span> <span data-ttu-id="daa76-155">다음 목록에서 각각에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-155">The following list describes each in detail:</span></span>  
  

<span data-ttu-id="daa76-156">**NX_SNTP_CLIENT_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="daa76-156">**NX_SNTP_CLIENT_THREAD_STACK_SIZE**</span></span>  
<span data-ttu-id="daa76-157">이 옵션은 클라이언트 스레드 스택의 크기를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-157">This option sets the size of the Client thread stack.</span></span> <span data-ttu-id="daa76-158">기본 NetX Duo SNTP 클라이언트 크기는 2048입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-158">The default NetX Duo SNTP Client size is 2048.</span></span>

<span data-ttu-id="daa76-159">**NX_SNTP_CLIENT_THREAD_TIME_SLICE**</span><span class="sxs-lookup"><span data-stu-id="daa76-159">**NX_SNTP_CLIENT_THREAD_TIME_SLICE**</span></span>  
<span data-ttu-id="daa76-160">이 옵션은 스케줄러의 시간 조각을 설정하여 클라이언트 스레드를 실행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-160">This option sets the time slice of the scheduler allows for Client thread execution.</span></span> <span data-ttu-id="daa76-161">기본 NetX Duo SNTP 클라이언트 크기는 TX_NO_TIME_SLICE입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-161">The default NetX Duo SNTP Client size is TX_NO_TIME_SLICE.</span></span>

<span data-ttu-id="daa76-162">**NX_SNTP_CLIENT_ THREAD_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="daa76-162">**NX_SNTP_CLIENT_ THREAD_PRIORITY**</span></span>  
<span data-ttu-id="daa76-163">이 옵션은 클라이언트 스레드 우선 순위를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-163">This option sets the Client thread priority.</span></span> <span data-ttu-id="daa76-164">NetX Duo SNTP 클라이언트 기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-164">The NetX Duo SNTP Client default value is 2.</span></span>

<span data-ttu-id="daa76-165">**NX_SNTP_CLIENT_PREEMPTION_THRESHOLD**</span><span class="sxs-lookup"><span data-stu-id="daa76-165">**NX_SNTP_CLIENT_PREEMPTION_THRESHOLD**</span></span>  
<span data-ttu-id="daa76-166">이 옵션은 클라이언트 스레드가 선점을 허용하는 우선 순위 수준을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-166">This option sets the sets the level of priority at which the Client thread allows preemption.</span></span> <span data-ttu-id="daa76-167">기본 NetX Duo SNTP 클라이언트 값은 `NX_SNTP_CLIENT_ THREAD_PRIORITY`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-167">The default NetX Duo SNTP Client value is set to `NX_SNTP_CLIENT_ THREAD_PRIORITY`.</span></span>

<span data-ttu-id="daa76-168">**NX_SNTP_CLIENT_UDP_SOCKET_NAME**</span><span class="sxs-lookup"><span data-stu-id="daa76-168">**NX_SNTP_CLIENT_UDP_SOCKET_NAME**</span></span>  
<span data-ttu-id="daa76-169">이 옵션은 UDP 소켓 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-169">This option sets the UDP socket name.</span></span> <span data-ttu-id="daa76-170">NetX Duo SNTP 클라이언트 UDP 소켓 이름 기본값은 "SNTP 클라이언트 소켓"입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-170">The NetX Duo SNTP Client UDP socket name default is “SNTP Client socket.”</span></span>

<span data-ttu-id="daa76-171">**NX_SNTP_CLIENT_UDP_PORT**</span><span class="sxs-lookup"><span data-stu-id="daa76-171">**NX_SNTP_CLIENT_UDP_PORT**</span></span>  
<span data-ttu-id="daa76-172">클라이언트 소켓이 바인딩된 포트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-172">This sets the port which the Client socket is bound to.</span></span> <span data-ttu-id="daa76-173">기본 NetX Duo SNTP 클라이언트 포트는 123입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-173">The default NetX Duo SNTP Client port is 123.</span></span>

<span data-ttu-id="daa76-174">**NX_SNTP_SERVER_UDP_PORT**</span><span class="sxs-lookup"><span data-stu-id="daa76-174">**NX_SNTP_SERVER_UDP_PORT**</span></span>  
<span data-ttu-id="daa76-175">클라이언트에서 SNTP 서버에 SNTP 메시지를 보내는 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-175">This is port which the Client sends SNTP messages to the SNTP Server on.</span></span> <span data-ttu-id="daa76-176">기본 NetX SNTP 서버 포트는 123입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-176">The default NetX SNTP Server port is 123.</span></span>

<span data-ttu-id="daa76-177">**NX_SNTP_CLIENT_TIME_TO_LIVE**</span><span class="sxs-lookup"><span data-stu-id="daa76-177">**NX_SNTP_CLIENT_TIME_TO_LIVE**</span></span>  
<span data-ttu-id="daa76-178">클라이언트 패킷이 삭제되기 전에 통과할 수 있는 라우터 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-178">Specifies the number of routers a Client packet can pass before it is discarded.</span></span> <span data-ttu-id="daa76-179">기본 NetX Duo SNTP 클라이언트는 0x80으로 설정됩니다 *.*</span><span class="sxs-lookup"><span data-stu-id="daa76-179">The default NetX Duo SNTP Client is set to 0x80 *.*</span></span>

<span data-ttu-id="daa76-180">**NX_SNTP_CLIENT_MAX_QUEUE_DEPTH**</span><span class="sxs-lookup"><span data-stu-id="daa76-180">**NX_SNTP_CLIENT_MAX_QUEUE_DEPTH**</span></span>  
<span data-ttu-id="daa76-181">NetX Duo SNTP 클라이언트 소켓에서 큐에 대기할 수 있는 최대 UDP 패킷(데이터그램) 수입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-181">Maximum number of UDP packets (datagrams) that can be queued in the NetX Duo SNTP Client socket.</span></span> <span data-ttu-id="daa76-182">추가 패킷이 수신된다는 것은 가장 오래된 패킷이 해제됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-182">Additional packets received mean the oldest packets are released.</span></span> <span data-ttu-id="daa76-183">기본 NetX Duo SNTP 클라이언트는 5로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-183">The default NetX Duo SNTP Client is set to 5.</span></span>

<span data-ttu-id="daa76-184">**NX_SNTP_CLIENT_PACKET_TIMEOUT**</span><span class="sxs-lookup"><span data-stu-id="daa76-184">**NX_SNTP_CLIENT_PACKET_TIMEOUT**</span></span>  
<span data-ttu-id="daa76-185">NetX Duo 패킷 할당에 대한 제한 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-185">Time out for NetX Duo packet allocation.</span></span> <span data-ttu-id="daa76-186">기본 NetX Duo SNTP 클라이언트 패킷 제한 시간은 1초입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-186">The default NetX Duo SNTP Client packet timeout is 1 second.</span></span>

<span data-ttu-id="daa76-187">**NX_SNTP_CLIENT_NTP_VERSION**</span><span class="sxs-lookup"><span data-stu-id="daa76-187">**NX_SNTP_CLIENT_NTP_VERSION**</span></span>  
<span data-ttu-id="daa76-188">NetX Duo SNTP 클라이언트 API가 사용하는 SNTP 버전은 버전 4를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-188">SNTP version used by the Client The NetX Duo SNTP Client API was based on Version 4.</span></span> <span data-ttu-id="daa76-189">기본값은 3입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-189">The default value is 3.</span></span>

<span data-ttu-id="daa76-190">**NX_SNTP_CLIENT_MIN_NTP_VERSION**</span><span class="sxs-lookup"><span data-stu-id="daa76-190">**NX_SNTP_CLIENT_MIN_NTP_VERSION**</span></span>  
<span data-ttu-id="daa76-191">클라이언트에서 사용할 수 있는 가장 오래된 SNTP 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-191">Oldest SNTP version the Client will be able to work with.</span></span> <span data-ttu-id="daa76-192">NetX Duo SNTP 클라이언트 기본값은 버전 3입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-192">The NetX Duo SNTP Client default is Version 3.</span></span>

<span data-ttu-id="daa76-193">**NX_SNTP_CLIENT_MIN_SERVER_STRATUM**</span><span class="sxs-lookup"><span data-stu-id="daa76-193">**NX_SNTP_CLIENT_MIN_SERVER_STRATUM**</span></span>  
<span data-ttu-id="daa76-194">클라이언트에서 허용하는 가장 낮은 수준(가장 높은 Stratum 수준) SNTP 서버 Stratum입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-194">The lowest level (highest numeric stratum level) SNTP Server stratum the Client will accept.</span></span> <span data-ttu-id="daa76-195">NetX Duo SNTP 클라이언트 기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-195">The NetX Duo SNTP Client default is 2.</span></span>

<span data-ttu-id="daa76-196">**NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT**</span><span class="sxs-lookup"><span data-stu-id="daa76-196">**NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT**</span></span>  
<span data-ttu-id="daa76-197">클라이언트가 로컬 클록 시간에 대해 수행하는 최소 시간 조정(밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-197">The minimum time adjustment in milliseconds the Client will make to its local clock time.</span></span> <span data-ttu-id="daa76-198">아래의 시간 조정은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-198">Time adjustments below this will be ignored.</span></span> <span data-ttu-id="daa76-199">NetX Duo SNTP 클라이언트 기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-199">The NetX Duo SNTP Client default is 10.</span></span>

<span data-ttu-id="daa76-200">**NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT**</span><span class="sxs-lookup"><span data-stu-id="daa76-200">**NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT**</span></span>  
<span data-ttu-id="daa76-201">클라이언트가 로컬 클록 시간에 대해 수행하는 최대 시간 조정(밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-201">The maximum time adjustment in milliseconds the Client will make to its local clock time.</span></span> <span data-ttu-id="daa76-202">이 크기를 초과하는 시간의 경우 로컬 클록 조정을 최대 시간 조정으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-202">For time adjustments above this amount, the local clock adjustment is limited to the maximum time adjustment.</span></span> <span data-ttu-id="daa76-203">NetX Duo SNTP 클라이언트 기본값은 180000(3분)입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-203">The NetX Duo SNTP Client default is 180000 (3 minutes).</span></span>

<span data-ttu-id="daa76-204">**NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP**</span><span class="sxs-lookup"><span data-stu-id="daa76-204">**NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP**</span></span>  
<span data-ttu-id="daa76-205">이렇게 하면 클라이언트가 시간 서버에서 첫 번째 업데이트를 받을 때 최대 시간 조정이 면제될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-205">This enables the maximum time adjustment to be waived when the Client receives the first update from its time server.</span></span> <span data-ttu-id="daa76-206">그 후에는 최대 시간 조정이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-206">Thereafter, the maximum time adjustment is enforced.</span></span> <span data-ttu-id="daa76-207">클라이언트를 가능한 한 빨리 서버 클럭과 동기화하는 것이 목적입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-207">The intention is to get the Client in synch with the server clock as soon as possible.</span></span> <span data-ttu-id="daa76-208">NetX Duo SNTP 클라이언트 기본값은 NX_TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-208">The NetX Duo SNTP Client default is NX_TRUE.</span></span>

<span data-ttu-id="daa76-209">**NX_SNTP_CLIENT_MAX_TIME_LAPSE**</span><span class="sxs-lookup"><span data-stu-id="daa76-209">**NX_SNTP_CLIENT_MAX_TIME_LAPSE**</span></span>  
<span data-ttu-id="daa76-210">SNTP 클라이언트에서 유효 시간 업데이트를 받지 못한 상태로 경과될 수 있는 최대 허용 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-210">Maximum allowable amount of time (seconds) elapsed without a valid time update received by the SNTP Client.</span></span> <span data-ttu-id="daa76-211">SNTP 클라이언트는 계속 작동하지만 SNTP 서버 상태는 NX_FALSE로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-211">The SNTP Client will continue in operation but the SNTP Server status is set to NX_FALSE.</span></span> <span data-ttu-id="daa76-212">기본값은 7200입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-212">The default value is 7200.</span></span>


<span data-ttu-id="daa76-213">**NX_SNTP_UPDATE_TIMEOUT_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="daa76-213">**NX_SNTP_UPDATE_TIMEOUT_INTERVAL**</span></span>  
<span data-ttu-id="daa76-214">SNTP 클라이언트 타이머가 마지막으로 유효 업데이트를 받은 후에 남은 SNTP 클라이언트 시간을 업데이트하고, 유니캐스트 클라이언트가 다음 SNTP 업데이트 요청을 보내기 전에 남은 폴링 간격 시간을 업데이트하는 간격(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-214">The interval (seconds) at which the SNTP Client timer updates the SNTP Client time remaining since the last valid update received, and the unicast Client updates the poll interval time remaining before sending the next SNTP update request.</span></span> <span data-ttu-id="daa76-215">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-215">The default value is 1.</span></span>

<span data-ttu-id="daa76-216">**NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="daa76-216">**NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL**</span></span>  
<span data-ttu-id="daa76-217">클라이언트가 SNTP 서버에 유니캐스트 요청을 보내는 시작 폴링 간격(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-217">The starting poll interval (seconds) on which the Client sends a unicast request to its SNTP server.</span></span> <span data-ttu-id="daa76-218">NetX Duo SNTP 클라이언트 기본값은 3600입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-218">The NetX Duo SNTP Client default is 3600.</span></span>

<span data-ttu-id="daa76-219">**NX_SNTP_CLIENT_EXP_BACKOFF_RATE**</span><span class="sxs-lookup"><span data-stu-id="daa76-219">**NX_SNTP_CLIENT_EXP_BACKOFF_RATE**</span></span>  
<span data-ttu-id="daa76-220">현재 클라이언트 유니캐스트 폴링 간격이 증가하는 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-220">The factor by which the current Client unicast poll interval is increased.</span></span> <span data-ttu-id="daa76-221">클라이언트에서 서버 시간 업데이트를 받지 못하거나 시간 업데이트 서비스에서 일시적으로 사용할 수 없다는(예: 아직 동기화되지 않음) 서버의 알림이 수신되면 이 비율만큼 현재 폴링 간격이 늘어나지만 NX_SNTP_CLIENT_MAX_TIME_LAPSE를 초과하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-221">When the Client fails to receive a server time update, or receiving indications from the server that it is temporarily unavailable (e.g. not synchronized yet) for time update service, it will increase the current poll interval by this rate up to but not exceeding NX_SNTP_CLIENT_MAX_TIME_LAPSE.</span></span> <span data-ttu-id="daa76-222">기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-222">The default is 2.</span></span>

<span data-ttu-id="daa76-223">**NX_SNTP_CLIENT_RTT_REQUIRED**</span><span class="sxs-lookup"><span data-stu-id="daa76-223">**NX_SNTP_CLIENT_RTT_REQUIRED**</span></span>  
<span data-ttu-id="daa76-224">이 옵션을 사용하도록 설정하면 서버 업데이트를 로컬 클록에 적용할 때 SNTP 클라이언트가 SNTP 메시지의 라운드트립 시간을 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-224">This option if enabled requires that the SNTP Client calculate round trip time of SNTP messages when applying Server updates to the local clock.</span></span> <span data-ttu-id="daa76-225">기본값은 NX_FALSE(사용 안 함)입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-225">The default value is NX_FALSE (disabled).</span></span>

<span data-ttu-id="daa76-226">**NX_SNTP_CLIENT_MAX_ROOT_DISPERSION**</span><span class="sxs-lookup"><span data-stu-id="daa76-226">**NX_SNTP_CLIENT_MAX_ROOT_DISPERSION**</span></span>  
<span data-ttu-id="daa76-227">클라이언트에서 허용하는 서버 클록 정밀도 측정값인 최대 서버 클록 분산(마이크로초)입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-227">The maximum server clock dispersion (microseconds), which is a measure of server clock precision, the Client will accept.</span></span> <span data-ttu-id="daa76-228">이 요구 사항을 사용하지 않도록 설정하려면 최대 루트 분산를 0x0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-228">To disable this requirement, set the maximum root dispersion to 0x0.</span></span> <span data-ttu-id="daa76-229">NetX Duo SNTP 클라이언트 기본값은 50000으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-229">The NetX Duo SNTP Client default is set to 50000.</span></span>

<span data-ttu-id="daa76-230">**NX_SNTP_CLIENT_INVALID_UPDATE_LIMIT**</span><span class="sxs-lookup"><span data-stu-id="daa76-230">**NX_SNTP_CLIENT_INVALID_UPDATE_LIMIT**</span></span>  
<span data-ttu-id="daa76-231">브로드캐스트 또는 유니캐스트 모드로 클라이언트 서버에서 수신되는 잘못된 업데이트의 연속 횟수 제한을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-231">The limit on the number of consecutive invalid updates received from the Client server in either broadcast or unicast mode.</span></span> <span data-ttu-id="daa76-232">이 제한에 도달하면 클라이언트는 서버에서 업데이트를 계속 수신하려고 하지만 현재 SNTP 서버 상태를 유효하지 않음(NX_FALSE)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-232">When this limit is reached, the Client sets the current SNTP Server status to invalid (NX_FALSE) although it will continue to try to receive updates from the Server.</span></span> <span data-ttu-id="daa76-233">NetX Duo SNTP 클라이언트 기본값은 3입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-233">The NetX Duo SNTP Client default is 3.</span></span>

<span data-ttu-id="daa76-234">**NX_SNTP_CLIENT_RANDOMIZE_ON_STARTUP**</span><span class="sxs-lookup"><span data-stu-id="daa76-234">**NX_SNTP_CLIENT_RANDOMIZE_ON_STARTUP**</span></span>  
<span data-ttu-id="daa76-235">유니캐스트 모드의 SNTP 클라이언트가 임의 대기 간격 후에 현재 SNTP 서버를 사용하여 첫 번째 SNTP 요청을 보내야 하는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-235">This determines if the SNTP Client in unicast mode should send its first SNTP request with the current SNTP server after a random wait interval.</span></span> <span data-ttu-id="daa76-236">이 옵션은 많은 수의 SNTP 클라이언트가 SNTP 서버의 트래픽 정체를 제한하기 위해 동시에 시작되는 경우에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-236">It is used in cases where significant numbers of SNTP Clients are starting up simultaneously to limit traffic congestion on the SNTP Server.</span></span> <span data-ttu-id="daa76-237">기본값은 NX_FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-237">The default value is NX_FALSE.</span></span>

<span data-ttu-id="daa76-238">**NX_SNTP_CLIENT_SLEEP_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="daa76-238">**NX_SNTP_CLIENT_SLEEP_INTERVAL**</span></span>  
<span data-ttu-id="daa76-239">SNTP 클라이언트 작업이 절전 모드를 유지하는 시간 간격입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-239">The time interval during which the SNTP Client task sleeps.</span></span> <span data-ttu-id="daa76-240">이를 통해 SNTP 클라이언트에서 애플리케이션 API 호출을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-240">This allows the application API calls to be executed by the SNTP Client.</span></span> <span data-ttu-id="daa76-241">기본값은 1번의 타이머 틱입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-241">The default value is 1 timer tick.</span></span>

<span data-ttu-id="daa76-242">**NX_SNTP_CURRENT_YEAR**</span><span class="sxs-lookup"><span data-stu-id="daa76-242">**NX_SNTP_CURRENT_YEAR**</span></span>  
<span data-ttu-id="daa76-243">년/월/날짜 형식으로 날짜를 표시하려면 이 값을 현재 연도보다 작거나 같은 값으로 설정합니다(계산하려는 NTP 시간의 연도와 같은 필요는 없음).</span><span class="sxs-lookup"><span data-stu-id="daa76-243">To display date in year/month/date format, set this value to equal or less than current year (need not be same year as in NTP time being evaluated).</span></span> <span data-ttu-id="daa76-244">기본값은 2015입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-244">The default value is 2015.</span></span>

<span data-ttu-id="daa76-245">**NTP_SECONDS_AT_01011999**</span><span class="sxs-lookup"><span data-stu-id="daa76-245">**NTP_SECONDS_AT_01011999**</span></span>  
<span data-ttu-id="daa76-246">마스터 NTP 클록의 첫 번째 NTP Epoch까지의 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-246">This is the number of seconds into the first NTP Epoch on the master NTP clock.</span></span> <span data-ttu-id="daa76-247">0xBA368E80으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-247">It is defined as 0xBA368E80.</span></span> <span data-ttu-id="daa76-248">날짜 및 시간으로의 NTP 초 표시를 사용하지 않도록 설정하려면 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="daa76-248">To disable display of NTP seconds into date and time, set to zero.</span></span>
