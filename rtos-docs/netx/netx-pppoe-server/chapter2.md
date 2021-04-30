---
title: 2장 - Azure RTOS NetX PPPoE 서버 설치 및 사용
description: 이 장에서는 Azure RTOS NetX PPPoE 서버 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5b52164911676b68c67da01d698e41c02730e45a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810404"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-server"></a><span data-ttu-id="2276c-103">2장 - Azure RTOS NetX PPPoE 서버 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="2276c-103">Chapter 2 - Installation and use of Azure RTOS NetX PPPoE Server</span></span>

<span data-ttu-id="2276c-104">이 장에서는 Azure RTOS NetX PPPoE 서버 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX PPPoE Server component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="2276c-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="2276c-105">Product Distribution</span></span>

<span data-ttu-id="2276c-106">NetX용 PPPoE 서버는 [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-106">PPPoE Server for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="2276c-107">패키지에는 다음과 같이 이 문서를 포함하는 두 개의 원본 파일과 PDF 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="2276c-108">**nx_pppoe_server.h**: NetX용 PPPoE 서버에 대한 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="2276c-108">**nx_pppoe_server.h**: Header file for PPPoE Server for NetX</span></span>
- <span data-ttu-id="2276c-109">**nx_pppoe_server.c**: NetX용 PPPoE 서버에 대한 C 원본 파일</span><span class="sxs-lookup"><span data-stu-id="2276c-109">**nx_pppoe_server.c**: C Source file for PPPoE Server for NetX</span></span>
- <span data-ttu-id="2276c-110">**nx_pppoe_server.pdf**: NetX용 PPPoE 서버에 대한 PDF 설명</span><span class="sxs-lookup"><span data-stu-id="2276c-110">**nx_pppoe_server.pdf**: PDF description of PPPoE Server for NetX</span></span>
- <span data-ttu-id="2276c-111">**demo_netx_pppoe_server.c**: NetX PPPoE 서버 데모</span><span class="sxs-lookup"><span data-stu-id="2276c-111">**demo_netx_pppoe_server.c**: NetX PPPoE Server demonstration</span></span>

## <a name="pppoe-server-installation"></a><span data-ttu-id="2276c-112">PPPoE 서버 설치</span><span class="sxs-lookup"><span data-stu-id="2276c-112">PPPoE Server Installation</span></span>

<span data-ttu-id="2276c-113">NetX용 PPPoE 서버를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-113">In order to use PPPoE Server for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="2276c-114">예를 들어 NetX가 “ *\threadx\arm7\green*” 디렉터리에 설치된 경우 *nx_pppoe_server.h* 및 *nx_pppoe_server.c* 파일을 이 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_pppoe_server.h* and *nx_pppoe_server.c* files should be copied into this directory.</span></span>

## <a name="using-pppoe-server"></a><span data-ttu-id="2276c-115">PPPoE 서버 사용</span><span class="sxs-lookup"><span data-stu-id="2276c-115">Using PPPoE Server</span></span>

<span data-ttu-id="2276c-116">NetX용 PPPoE 서버는 사용이 간편합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-116">Using PPPoE Server for NetX is easy.</span></span> <span data-ttu-id="2276c-117">기본적으로 애플리케이션 코드는 ThreadX 및 NetX를 각각 사용하기 위해 *tx_api.h* 및 *nx_api.h* 를 포함한 후 *nx_pppoe_server.h* 를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-117">Basically, the application code must include *nx_pppoe_server.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="2276c-118">*nx_pppoe_server.h* 가 포함되면 애플리케이션 코드에서 이 가이드의 뒷부분에 지정된 PPPoE 서버 함수 호출을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-118">Once *nx_pppoe_server.h* is included, the application code is then able to make the PPPoE Server function calls specified later in this guide.</span></span> <span data-ttu-id="2276c-119">애플리케이션은 빌드 프로세스에 *nx_pppoe_server.c* 도 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-119">The application must also include *nx_pppoe_server.c* in the build process.</span></span> <span data-ttu-id="2276c-120">이 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일해야 하며, 해당 개체 형식은 애플리케이션의 파일과 함께 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="2276c-121">이렇게 간단하게 NetX PPPoE 서버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-121">This is all that is required to use NetX PPPoE Server.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="2276c-122">작은 예제 시스템</span><span class="sxs-lookup"><span data-stu-id="2276c-122">Small Example System</span></span>

<span data-ttu-id="2276c-123">다음은 NetX PPPoE 서버를 사용하는 방법을 보여 주는 예제로 그림 1.1에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-123">The following is an example that illustrates how to use NetX PPPoE Server is described in Figure 1.1.</span></span> <span data-ttu-id="2276c-124">이 예제에서 PPPoE 서버 포함 파일 *nx_pppoe_server.h* 는 50줄에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-124">In this example, the PPPoE Server include file *nx_pppoe_server.h* is brought in at line 50.</span></span> <span data-ttu-id="2276c-125">다음으로, PPPoE 서버는 248줄에서 *“thread_0_entry*”에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-125">Next, PPPoE Server is created in *"thread_0_entry*" at line 248.</span></span> <span data-ttu-id="2276c-126">IP 인스턴스를 만든 후에는 PPPoE 서버를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-126">Note that PPPoE Server should be created after create the IP instance.</span></span> <span data-ttu-id="2276c-127">IP 인스턴스가 생성되고 165줄에서 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-127">The IP instance is created and initialized line165.</span></span> <span data-ttu-id="2276c-128">PPPoE 서버 제어 블록 “*pppoe_server*”가 이전에 79줄에서 전역 변수로 정의되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-128">The PPPoE Server control block "*pppoe_server*" was defined as a global variable at line 79 previously.</span></span> <span data-ttu-id="2276c-129">notify 함수는 257줄에서 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-129">The notify functions are set at line 257.</span></span> <span data-ttu-id="2276c-130">pppoe_session_data_receive notify 함수를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-130">Note that pppoe_session_data_receive notify function must be set.</span></span> <span data-ttu-id="2276c-131">IP 및 PPPoE 서버를 성공적으로 만든 후에 PPPoE 서버는 272줄의 nx_pppoe_server_enable로 호출 시 PPPoE 세션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-131">After successful creation of IP and PPPoE Server, the PPPoE Server process of establishing a PPPoE session at the call to nx_pppoe_server_enable at line 272.</span></span>

<span data-ttu-id="2276c-132">일반적으로 PPPoE 모듈은 PPP 모듈과 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-132">In general, PPPoE module should be used with PPP module.</span></span> <span data-ttu-id="2276c-133">이 예제에서 PPP 서버 포함 파일 *nx_ppp.h* 는 49줄에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-133">In this example, the PPP Server include file *nx_ppp.h* is brought in at line 49.</span></span> <span data-ttu-id="2276c-134">다음으로, PPP 서버가 174줄에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-134">Next, PPP Server is created at line 174.</span></span> <span data-ttu-id="2276c-135">182줄은 PPP 패킷을 보내도록 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-135">Line 182 setup the function to send PPP packet.</span></span> <span data-ttu-id="2276c-136">188-200줄은 IP 주소를 설정하고 pap 프로토콜을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-136">Line 188-200 setup the IP addresses and define the pap protocol.</span></span> <span data-ttu-id="2276c-137">115-139줄은 pap 프로토콜에 대한 사용자 이름 및 암호를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-137">Line 115-139 setup the user name and password for pap protocol.</span></span>

<span data-ttu-id="2276c-138">PPPoE 세션이 설정된 후.</span><span class="sxs-lookup"><span data-stu-id="2276c-138">After the PPPoE session established.</span></span> <span data-ttu-id="2276c-139">애플리케이션은 nx_pppoe_server_session_get을 호출하여 281줄에서 세션 정보(클라이언트 MAC 주소 및 세션 ID)를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-139">The application can call nx_pppoe_server_session_get to get the session information (client MAC address and session id) at line 281.</span></span>

<span data-ttu-id="2276c-140">애플리케이션이 더 이상 PPP 트래픽을 처리하지 않을 경우 애플리케이션은 PppCloseInd 또는 nx_pppoe_server_session_terminate를 호출하여 PPPoE 세션을 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-140">When the application no longer process PPP traffic, the application PppCloseInd or nx_pppoe_server_session_terminate to terminate the PPPoE session.</span></span>

> [!NOTE]
> <span data-ttu-id="2276c-141">이 예제에서 PPPoE 서버는 동시에 일반 IP 스택에서 작업하고 하나의 이더넷 드라이버를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-141">In this example, PPPoE Server work with normal IP stack at the same time, and share one Ethernet driver.</span></span> <span data-ttu-id="2276c-142">165줄의 일반 IP 인스턴스와 248줄의 PPPoE 서버 인스턴스에 대해 동일한 이더넷 드라이버를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-142">Pass the same Ethernet driver for normal IP instance at line 165 and PPPoE Server instance at line 248.</span></span>

> [!NOTE]
> <span data-ttu-id="2276c-143">이 함수는 정의된 NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE에서 소프트웨어에 의한 호출을 위한 PPPoE 구현에 의해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-143">The functions are provided by the PPPoE implementation for calling by the software under defined NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE.</span></span>

<span data-ttu-id="2276c-144">정의된 경우 PPPoE 세션을 제어하는 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-144">If defined, enables the feature that controls the PPPoE session.</span></span>

<span data-ttu-id="2276c-145">PPPoE 서버는 애플리케이션이 특정 API를 호출할 때까지 요청에 자동으로 응답하지 않습니다. 정의되지 않은 경우 PPPoE 서버는 요청에 자동으로 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-145">PPPoE server does not automatically response to the request until application call specific API, if not defined, PPPoE Server automatically responses to the request.</span></span> <span data-ttu-id="2276c-146">nx_pppoe_server.h에서 기본적으로 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-146">It enables by default in nx_pppoe_server.h.</span></span>

<span data-ttu-id="2276c-147">실제 헤더를 채우는 데 충분한 공간을 확보하기 위해 **NX_PHYSICAL_HEADER** 를 24로 다시 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-147">Note, redefine **NX_PHYSICAL_HEADER** to 24 to ensure enough space for filling in physical header.</span></span> <span data-ttu-id="2276c-148">실제 헤더: 14(이더넷 헤더) + 6(PPPoE 헤더) + 2(PPP 헤더) + 2(4바이트 정렬).</span><span class="sxs-lookup"><span data-stu-id="2276c-148">Physical header:14(Ethernet header) + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment).</span></span>

```c
/**************************************************************************/
/**************************************************************************/
/**                                                                       */
/** NetX PPPoE Server stack Component                                     */
/**                                                                       */
/** This is a small demo of the high-performance NetX PPPoE Server        */
/** stack. This demo includes IP instance, PPPoE Server and PPP Server    */
/** stack. Create one IP instance includes two interfaces to support      */
/** for normal IP stack and PPPoE Server, PPPoE Server can use the        */
/** mutex of IP instance to send PPPoE message when share one Ethernet    */
/** driver. PPPoE Server work with normal IP instance at the same time.   */
/**                                                                       */
/** Note1: Substitute your Ethernet driver instead of                     */
/** _nx_ram_network_driver before run this demo                           */
/**                                                                       */
/** Note2: Prerequisite for using PPPoE.                                  */
/** Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling  */
/** in physical header. Physical header:14(Ethernet header)               */
/** + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)             */
/**                                                                       */
/**************************************************************************/
/**************************************************************************/


/*****************************************************************/
/*                            NetX Stack                         */
/*****************************************************************/

                                      /***************************/
                                      /* PPP Server              */
                                      /***************************/

                                      /***************************/
                                      /* PPPoE Server            */
                                      /***************************/
/***************************/         /***************************/
/* Normal Ethernet Type    */         /* PPPoE Ethernet Type     */
/***************************/         /***************************/
/***************************/         /***************************/
/* Interface 0             */         /* Interface 1             */
/***************************/         /***************************/

/*****************************************************************/
/*                     Ethernet Dirver                           */
/*****************************************************************/

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_ppp.h"
#include     "nx_pppoe_server.h"

/* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified to match PPPoE moduler under this definition. */
#ifdef NX_PPP_PPPOE_ENABLE

/*   If the driver is not initialized in other module, define */
/*   NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE to initialize the driver in PPPoE module. */
/*   In this demo, the driver has been initialized in IP module. */

#ifdef NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE

/*   NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE: If defined, enables the feature that */
/*   controls the PPPoE session. PPPoE server does not automatically response to the */
/*   request until application call specific API. */

/* Define the block size. */
#define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
#define     DEMO_STACK_SIZE         2048
#define     PPPOE_THREAD_SIZE       2048

/* Define the ThreadX and NetX object control blocks... */
TX_THREAD           thread_0;

/* Define the packet pool and IP instance for normal IP instnace. */
NX_PACKET_POOL      pool_0;
NX_IP               ip_0;

/* Define the PPP Server instance. */
NX_PPP              ppp_server;

/* Define the PPPoE Server instance. */
NX_PPPOE_SERVER     pppoe_server;

/* Define the counters. */
CHAR                *pointer;
ULONG               error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);

/***** Substitute your PPP driver entry function here *********/
extern void     _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);

/***** Substitute your Ethernet driver entry function here *********/
extern void     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define the callback functions. */
void     PppDiscoverReq(UINT interfaceHandle);
void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data);
void     PppCloseRsp(UINT interfaceHandle);
void     PppCloseReq(UINT interfaceHandle);
void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id);
void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data);

/* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP. */
/* Functions to be provided by PPP for calling by the PPPoE Stack. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

UINT verify_login(CHAR *name, CHAR *password)
{

    if ((name[0] == 'm') &&
        (name[1] == 'y') &&
        (name[2] == 'n') &&
        (name[3] == 'a') &&
        (name[4] == 'm') &&
        (name[5] == 'e') &&
        (name[6] == (CHAR) 0) &&
        (password[0] == 'm') &&
        (password[1] == 'y') &&
        (password[2] == 'p') &&
        (password[3] == 'a') &&
        (password[4] == 's') &&
        (password[5] == 's') &&
        (password[6] == 'w') &&
        (password[7] == 'o') &&
        (password[8] == 'r') &&
        (password[9] == 'd') &&
        (password[10] == (CHAR) 0))
            return(NX_SUCCESS);
    else
        return(NX_PPP_ERROR);
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{

    UINT status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool for normal IP instance. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
                                    (1536 + sizeof(NX_PACKET)),
                                    pointer, NX_PACKET_POOL_SIZE);
                                    pointer = pointer + NX_PACKET_POOL_SIZE;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create an normal IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 43),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create the PPP instance. */
    status = nx_ppp_create(&ppp_server, "PPP Instance", &ip_0, pointer, 2048, 1,
                            &pool_0, NX_NULL, NX_NULL);
    pointer = pointer + 2048;

    /* Check for PPP create error. */
    if (status)
        error_counter++;

    /* Set the PPP packet send function. */
    status = nx_ppp_packet_send_set(&ppp_server, ppp_server_packet_send);

    /* Check for PPP packet send function set error. */
    if (status)
        error_counter++;

    /* Define IP address. This PPP instance is effectively the server since it has both IP addresses. */
    status = nx_ppp_ip_address_assign(&ppp_server, IP_ADDRESS(192, 168, 10, 43),                                         IP_ADDRESS(192, 168, 10, 44));

    /* Check for PPP IP address assign error. */
    if (status)
        error_counter++;

    /* Setup PAP, this PPP instance is effectively the server since it will verify the name and password. */
    status = nx_ppp_pap_enable(&ppp_server, NX_NULL, verify_login);

    /* Check for PPP PAP enable error. */
    if (status)
        error_counter++;

    /* Attach an interface for PPP. */
    status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", 
                            IP_ADDRESS(0, 0, 0, 0), 0, nx_ppp_driver);

    /* Check for error. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for Normal IP Instance. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
        error_counter++;

    /* Enable ICMP */
    status = nx_icmp_enable(&ip_0);
    if(status)
        error_counter++;

    /* Enable UDP traffic. */
    status = nx_udp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Enable TCP traffic. */
    status = nx_tcp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;
}

/* Define the test threads. */

void     thread_0_entry(ULONG thread_input)
{
UINT     status;
ULONG    ip_status;

    /* Create the PPPoE instance. */
    status = nx_pppoe_server_create(&pppoe_server, (UCHAR *)"PPPoE Server", &ip_0, 0,
                    _nx_ram_network_driver, &pool_0, pointer, PPPOE_THREAD_SIZE, 4);
    pointer = pointer + PPPOE_THREAD_SIZE;
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the callback notify function. */
    status = nx_pppoe_server_callback_notify_set(&pppoe_server, PppDiscoverReq,
        PppOpenReq, PppCloseRsp, PppCloseReq, PppTransmitDataReq, PppReceiveDataRsp);

    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call function function to set the default service Name. */
        /* PppInitInd(length, aData); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

    /* Enable PPPoE Server. */
    status = nx_pppoe_server_enable(&pppoe_server);
    if (status)
    {
        error_counter++;
        return;
    }

    /* Get the PPPoE Client physical address and Session ID after establish PPPoE Session. */
    /*
        status = nx_pppoe_server_session_get(&pppoe_server, interfaceHandle, &client_mac_msw, &client_mac_lsw, &session_id);
        if (status)
            error_counter++;
    */

    /* Wait for the link to come up. */
    status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                            &ip_status, NX_WAIT_FOREVER);
    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to terminate the PPPoE Session. */
        /* PppCloseInd(interfaceHandle, causeCode); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

}

void     PppDiscoverReq(UINT interfaceHandle)
{

    /* Receive the PPPoE Discovery Initiation Message. */
    
    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to define the Service Name field of the PADO packet. */
        PppDiscoverCnf(0, NX_NULL, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data)
{

    /* Get the notify that receive the PPPoE Discovery Request Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to accept the PPPoE session. */
        PppOpenCnf(NX_TRUE, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseRsp(UINT interfaceHandle)
{

    /* Get the notify that receive the PPPoE Discovery Terminate Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to confirm that the handle has been freed. */
        PppCloseCnf(interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseReq(UINT interfaceHandle)
{

    /* Get the notify that PPPoE Discovery Terminate Message has been sent. */

}

void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id)
{

    NX_PACKET *packet_ptr;

    /* Get the notify that receive the PPPoE Session data. */

    /* Call PPP Server to receive the PPP data fame. */
    packet_ptr = (NX_PACKET *)(packet_id);
    nx_ppp_packet_receive(&ppp_server, packet_ptr);

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to confirm that the data has been processed. */
        PppTransmitDataCnf(interfaceHandle, data, packet_id);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data)
{

    /* Get the notify that the PPPoE Session data has been sent. */

}

/* PPP Server send function. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr)
{

    /* For Express Logic's PPP test, the session should be the first session, so set interfaceHandle as 0. */
    UINT interfaceHandle = 0;

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        while(packet_ptr)
        {

            /* Call functions to be provided by PPPoE for TTP. */
            PppReceiveDataInd(interfaceHandle, (packet_ptr -> nx_packet_append_ptr -
            packet_ptr -> nx_packet_prepend_ptr), packet_ptr -> nx_packet_prepend_ptr);

            /* Move to the next packet structure. */
            packet_ptr = packet_ptr -> nx_packet_next;
        }
    #else
        /* Directly Call PPPoE send function to send out the data through PPPoE module. */
        nx_pppoe_server_session_packet_send(&pppoe_server, interfaceHandle, packet_ptr);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}
#endif /* NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE */

#endif /* NX_PPP_PPPOE_ENABLE */
```

<span data-ttu-id="2276c-149">그림 1.1 NetX에서의 PPPoE 서버 사용 예제</span><span class="sxs-lookup"><span data-stu-id="2276c-149">Figure 1.1 Example of PPPoE Server use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="2276c-150">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="2276c-150">Configuration Options</span></span>

<span data-ttu-id="2276c-151">NetX용 PPPoE 서버를 빌드하기 위한 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-151">There are several configuration options for building PPPoE Server for NetX.</span></span> <span data-ttu-id="2276c-152">다음 목록에서 각각에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-152">The following list describes each in detail:</span></span>

- <span data-ttu-id="2276c-153">**NX_DISABLE_ERROR_CHECKING**: 정의된 경우 이 옵션은 기본 PPPoE 서버 오류 검사를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-153">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic PPPoE Server error checking.</span></span> <span data-ttu-id="2276c-154">일반적으로 애플리케이션이 디버깅된 후에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-154">It is typically used after the application has been debugged.</span></span>

- <span data-ttu-id="2276c-155">**NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: 정의된 경우 PPPoE 세션을 제어하는 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-155">**NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: If defined, enables the feature that controls the PPPoE session.</span></span> <span data-ttu-id="2276c-156">PPPoE 서버는 애플리케이션에서 특정 API를 호출할 때까지 요청에 자동으로 응답하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-156">PPPoE server does not automatically response to the request until application call specific API.</span></span>

- <span data-ttu-id="2276c-157">**NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: 정의된 경우 PPPoE 모듈의 이더넷 드라이버를 초기화하는 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-157">**NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: If defined, enables the feature to initialize the Ethernet driver in PPPoE module.</span></span> <span data-ttu-id="2276c-158">기본적으로는 사용하지 않도록 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-158">It disables by default.</span></span>

- <span data-ttu-id="2276c-159">**NX_PPPOE_SERVER_THREAD_TIME_SLICE**: PPPoE 서버 스레드에 대한 시간 조각 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-159">**NX_PPPOE_SERVER_THREAD_TIME_SLICE**: Time-slice option for PPPoE Server thread.</span></span> <span data-ttu-id="2276c-160">기본적으로 이 값은 TX_NO_TIME_SLICE입니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-160">By default, this value is TX_NO_TIME_SLICE.</span></span>

- <span data-ttu-id="2276c-161">**NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: 이는 동시 클라이언트 세션의 최대 수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-161">**NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: This defines the max number of concurrent client sessions.</span></span> <span data-ttu-id="2276c-162">기본적으로 이 값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-162">By default, this value is 10.</span></span>

- <span data-ttu-id="2276c-163">**NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: Host-Uniq의 최대 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-163">**NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: This defines the max size of Host-Uniq.</span></span> <span data-ttu-id="2276c-164">기본적으로 이 값은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-164">By default, this value is 32.</span></span>

- <span data-ttu-id="2276c-165">**NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: 릴레이 세션 ID의 최대 크기를 정의합니다. 기본적으로 이 값은 12입니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-165">**NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: This defines the max size of Relay-Session-Id. By default, this value is 12.</span></span>

- <span data-ttu-id="2276c-166">**NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: PPPoE 서버에 대한 최소 패킷 페이로드 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-166">**NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: Specifies the Minimum packet payload size for PPPoE Server.</span></span> <span data-ttu-id="2276c-167">패킷 페이로드 크기가 이 값보다 크면, 연결된 패킷을 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-167">If the packet payload size is greater than this value, can avoid packet chained.</span></span> <span data-ttu-id="2276c-168">기본적으로 이 값은 1520(이더넷 1500, 이더넷 헤더 14, CRC 2 및 4바이트 정렬 4의 최대 페이로드 크기)입니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-168">By default, this value is 1520 (Maximum Payload Size of Ethernet 1500, Ethernet Header 14, CRC 2 and Four-byte alignment 4).</span></span>

- <span data-ttu-id="2276c-169">**NX_PPPOE_SERVER_PACKET_TIMEOUT**: 패킷을 할당하거나 패킷에 데이터를 추가하는 대기 시간(타이머 틱)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-169">**NX_PPPOE_SERVER_PACKET_TIMEOUT**: This defines the wait potion(in timer ticks) for allocating packets or appending data into packets.</span></span> <span data-ttu-id="2276c-170">기본적으로 이 값은 **NX_IP_PERIODIC_RATE**(100 틱)입니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-170">By default, this value is **NX_IP_PERIODIC_RATE** (100 ticks).</span></span>

- <span data-ttu-id="2276c-171">**NX_PPPOE_SERVER_START_SESSION_ID**: PPPoE 세션에 할당할 시작 세션 ID를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-171">**NX_PPPOE_SERVER_START_SESSION_ID**: This defines the start Session ID for assigning to the PPPoE Session.</span></span> <span data-ttu-id="2276c-172">기본적으로 이 값은 0X4944(ID의 ASCII 값)입니다.</span><span class="sxs-lookup"><span data-stu-id="2276c-172">By default, this value is 0X4944(ASCII value for ID).</span></span>