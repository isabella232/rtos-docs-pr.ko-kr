---
title: 2장 - Azure RTOS NetX Duo SNMP 에이전트 설치 및 사용
description: 이 장에서는 NetX Duo SNMP 에이전트 구성 요소의 설치, 설정, 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f011b73217c7f413dd19c555e9c2d40dace305ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810579"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-snmp-agent"></a><span data-ttu-id="91f3b-103">2장 - Azure RTOS NetX Duo SNMP 에이전트 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="91f3b-103">Chapter 2 - Installation and use of the Azure RTOS NetX Duo SNMP agent</span></span>

<span data-ttu-id="91f3b-104">이 장에서는 Azure RTOS NetX Duo SNMP 에이전트 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo SNMP agent component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="91f3b-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="91f3b-105">Product Distribution</span></span>

<span data-ttu-id="91f3b-106">NetX Duo용 SNMP 에이전트는 [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-106">SNMP Agent for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="91f3b-107">패키지에는 다음과 같이 4개의 소스 파일, 하나의 포함 파일 및 이 문서를 포함하는 PDF 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-107">The package includes four source files, one include file, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="91f3b-108">**nxd_snmp.h** NetX Duo용 SNMP의 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="91f3b-108">**nxd_snmp.h** Header file for SNMP for NetX Duo</span></span>
- <span data-ttu-id="91f3b-109">**demo_snmp_helper.h** SNMP MIB 데이터의 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="91f3b-109">**demo_snmp_helper.h** Header file for SNMP MIB data</span></span>
- <span data-ttu-id="91f3b-110">**nxd_snmp.c** NetX Duo용 SNMP 에이전트의 C 소스 파일</span><span class="sxs-lookup"><span data-stu-id="91f3b-110">**nxd_snmp.c** C Source file for SNMP Agent for NetX Duo</span></span>
- <span data-ttu-id="91f3b-111">**nx_md5.c** MD5 다이제스트 알고리즘</span><span class="sxs-lookup"><span data-stu-id="91f3b-111">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="91f3b-112">**nx_sha.c** SHA 다이제스트 알고리즘</span><span class="sxs-lookup"><span data-stu-id="91f3b-112">**nx_sha.c** SHA digest algorithms</span></span>
- <span data-ttu-id="91f3b-113">**nx_des.c** DES 암호화 알고리즘</span><span class="sxs-lookup"><span data-stu-id="91f3b-113">**nx_des.c** DES encryption algorithms</span></span>
- <span data-ttu-id="91f3b-114">**nxd_snmp.pdf** NetX Duo용 SNMP 에이전트 사용자 가이드</span><span class="sxs-lookup"><span data-stu-id="91f3b-114">**nxd_snmp.pdf** User Guide for SNMP Agent for NetX Duo</span></span>
- <span data-ttu-id="91f3b-115">**demo_netxduo_snmp.c** 기본 SNMP 데모</span><span class="sxs-lookup"><span data-stu-id="91f3b-115">**demo_netxduo_snmp.c** Simple SNMP demonstration</span></span>
- <span data-ttu-id="91f3b-116">**demo_netxduo_mib2.c** 기본 MIB2 데모(MIB에 IPv6 주소 요소 포함)</span><span class="sxs-lookup"><span data-stu-id="91f3b-116">**demo_netxduo_mib2.c** Simple MIB2 demonstration (MIB has IPv6 address elements)</span></span>
- <span data-ttu-id="91f3b-117">**demo_snmp_helper.h** MIB 요소를 정의하는 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="91f3b-117">**demo_snmp_helper.h** Header file defining MIB elements</span></span>

## <a name="netx-duo-snmp-agent-installation"></a><span data-ttu-id="91f3b-118">NetX Duo SNMP 에이전트 설치</span><span class="sxs-lookup"><span data-stu-id="91f3b-118">NetX Duo SNMP Agent Installation</span></span>

<span data-ttu-id="91f3b-119">NetX Duo SNMP를 사용하려면 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-119">In order to use NetX Duo SNMP, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="91f3b-120">예를 들어 NetX Duo가 “ *\threadx\arm7\green*” 디렉터리에 설치된 경우 *nxd_snmp.h*, *nxd_snmp.c*, *nx_md5.c, nx_sha.c* 및 nx_ *des.c* 파일을 이 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-120">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_snmp.h*, *nxd_snmp.c*, *nx_md5.c, nx_sha.c* and nx_ *des.c* files should be copied into this directory.</span></span>

## <a name="using-the-netx-duo-snmp-agent"></a><span data-ttu-id="91f3b-121">NetX Duo SNMP 에이전트 사용</span><span class="sxs-lookup"><span data-stu-id="91f3b-121">Using the NetX Duo SNMP Agent</span></span>

<span data-ttu-id="91f3b-122">애플리케이션은 *nxd_snmp.* c, *nx_md5, nx_sha.* c 및 *nx_des* 를 빌드 프로젝트에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-122">The application must have *nxd_snmp.c*, *nx_md5.c, nx_sha.c*, and *nx_des.c* in the build project.</span></span> <span data-ttu-id="91f3b-123">애플리케이션 코드는 SNMP 서비스를 호출할 수 있는 *nx_api.h to be* 를 포함한 다음 *nxd_snmp* 또한 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-123">The application code must also include *nxd_snmp.h* after it includes *nx_api.h to be* able to invoke SNMP services.</span></span> <span data-ttu-id="91f3b-124">이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 개체 양식이 NetX Duo 라이브러리에 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-124">These files must be compiled in the same manner as other application files and its object form must be linked to the NetX Duo library.</span></span> <span data-ttu-id="91f3b-125">이것이 NetX Duo SNMP를 사용하는 데 필요한 전부입니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-125">This is all that is required to use NetX Duo SNMP.</span></span>

> [!NOTE]
> <span data-ttu-id="91f3b-126">빌드 프로세스에서 **NX_SNMP_NO_SECURITY** 를 지정한 경우 nx_md5.c, nx_sha.c 및 nx_des.c 파일은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-126">*If **NX_SNMP_NO_SECURITY** is specified in the build process, the nx_md5.c, nx_sha.c, and nx_des.c files are not needed.*</span></span>

> [!NOTE]
> <span data-ttu-id="91f3b-127">NetX Duo SNMP는 UDP 서비스를 활용하므로 SNMP를 사용하기 전에 *nx_udp_enable* 호출을 통해 UDP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-127">That since NetX Duo SNMP utilizes UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using SNMP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="91f3b-128">간단한 예제 시스템</span><span class="sxs-lookup"><span data-stu-id="91f3b-128">Small Example System</span></span>

<span data-ttu-id="91f3b-129">NetX Duo SNMP 에이전트를 사용하는 방법에 대한 예제는 아래 그림 1.0에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-129">An example of how to use NetX Duo SNMP Agent is described in Figure 1.0 that appears below.</span></span> <span data-ttu-id="91f3b-130">이 예제에서 SNMP 포함 파일 *nxd_snmp.h* 는 6번째 줄에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-130">In this example, the SNMP include file *nxd_snmp.h* is brought in at line 6.</span></span> <span data-ttu-id="91f3b-131">MIB 데이터베이스 요소를 정의하는 헤더 파일 *demo_snmp_helper* 가 8번째 줄에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-131">The header file that defines the MIB database elements, *demo_snmp_helper.h,* is brought in at line 8.</span></span> <span data-ttu-id="91f3b-132">MIB는 32번째 줄부터 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-132">The MIB is defined starting on line 32.</span></span> <span data-ttu-id="91f3b-133">다음으로, SNMP 에이전트는 129번째 줄의 “*tx_application_define*”에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-133">Next, the SNMP Agent is created in “*tx_application_define*” at line 129.</span></span> <span data-ttu-id="91f3b-134">SNMP 에이전트 제어 블록 “*my_agent*”는 이전에 18번째 줄에서 전역 변수로 정의되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-134">Note that the SNMP Agent control block “*my_agent*” was defined as a global variable at line 18 previously.</span></span> <span data-ttu-id="91f3b-135">IPv6를 사용하도록 설정하면 IPv6 주소는 166~223번째 줄의 IP 인스턴스에 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-135">If IPv6 is enabled, the IPv6 addresses are registered with the IP instance in lines 166-223.</span></span> <span data-ttu-id="91f3b-136">SNMP 에이전트는 229번째 줄에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-136">SNMP Agent is started at line 229.</span></span> <span data-ttu-id="91f3b-137">SNMP 관리자 GET, GETNEXT 및 SET 요청과 사용자 이름 및 MIB 업데이트 요청에 대한 SNMP 개체 콜백 정의는 250번째 줄에서부터 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-137">SNMP object callback definitions for SNMP manager GET, GETNEXT and SET requests, as well as username and MIB update requests, are processed starting at line 250.</span></span> <span data-ttu-id="91f3b-138">이 예제에서는 인증을 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-138">For this example, no authenticate is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="91f3b-139">아래에 표시된 MIB2 테이블은 예제일 뿐입니다. 애플리케이션은 다른 MIB를 사용하여 별도의 파일에 포함하고 애플리케이션 요구 사항에 따라 GET, GETNEXT 또는 SET 처리를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-139">*The MIB2 table shown below is simply an example. The application may use a different MIB and include it in separate files, as well as define GET, GETNEXT, or SET processing as per their application requirements.*</span></span>

```c
/* This is a small demo of the NetX SNMP Agent on the high-performance NetX TCP/IP  
   stack. This demo relies on ThreadX and NetX to show simple SNMP the SNMP
   GET/GETNEXT/SET requests on MIB-2 objects.  */

#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_snmp.h"
#include  "demo_snmp_helper.h"

#define     DEMO_STACK_SIZE         4096
#define     AGENT_PRIMARY_ADDRESS   IP_ADDRESS(192, 2, 2, 66)

/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_SNMP_AGENT           my_agent;


/* Indicate if using IPv6 to communicate with SNMP servers. Note that
   IPv6 must be enabled in the NetX Duo library first. Further, IPv6
   and ICMPv6 services are enabled before starting the SNMP agent. */
#define USE_IPV6


/* Define authentication and privacy keys.  */

#ifdef AUTHENTICATION_REQUIRED
NX_SNMP_SECURITY_KEY    my_authentication_key;
#endif

#ifdef PRIVACY_REQUIRED
NX_SNMP_SECURITY_KEY    my_privacy_key;
#endif

/* Define an error counter variable. */
UINT error_counter = 0;

/* This binds a secondary interfaces to the primary IP network interface 
   if SNMP is required for required for that interface. */
/* #define  MULTI_HOMED_DEVICE */

/* Define function prototypes.  A generic ram driver is used in this demo.  However
   to properly run an SNMP agent demo, a real driver should be substituted. */

VOID    thread_agent_entry(ULONG thread_input);
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
UINT    mib2_get_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_getnext_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_set_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_username_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *username);
VOID    mib2_variable_update(NX_IP *ip_ptr, NX_SNMP_AGENT *agent_ptr);


UCHAR context_engine_id[] = {0x80, 0x00, 0x0d, 0xfe, 0x03, 0x00, 0x11, 0x23, 0x23, 
                             0x44, 0x55};
UINT  context_engine_size = 11;
UCHAR context_name[] = {0x69, 0x6e, 0x69, 0x74, 0x69, 0x61, 0x6c};
UINT  context_name_size = 7;

/* Define main entry point.  */

int main()
{

   /* Enter the ThreadX kernel.  */
   tx_kernel_enter();
}


/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UCHAR   *pointer;
UINT    status;


   /* Setup the working pointer.  */
   pointer =  (UCHAR *) first_unused_memory;

   status = tx_thread_create(&thread_0, "agent thread", thread_agent_entry, 0,  
            pointer, DEMO_STACK_SIZE, 
            4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
   if (status != NX_SUCCESS)
   {
      return;
   }

   pointer =  pointer + DEMO_STACK_SIZE;


   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create packet pool.  */
   status = nx_packet_pool_create(&pool_0, "NetX Packet Pool 0", 2048, 
                                   pointer, 20000);

   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer = pointer + 20000;
  
   /* Create an IP instance.  */
   status = nx_ip_create(&ip_0, "SNMP Agent IP Instance", AGENT_PRIMARY_ADDRESS, 
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);

   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer =  pointer + 4096;
  
   /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
   nx_arp_enable(&ip_0, (void *) pointer, 1024);
   pointer = pointer + 1024;

   /* Enable UPD processing for IP instance.  */
   nx_udp_enable(&ip_0);
  
   /* Enable ICMP for ping.  */
   nx_icmp_enable(&ip_0);
  
   /* Create an SNMP agent instance.  */
   status = nx_snmp_agent_create(&my_agent, "SNMP Agent", &ip_0, pointer, 4096, 
                                 &pool_0, 
                                 mib2_username_processing, mib2_get_processing, 
                                 mib2_getnext_processing, 
                                 mib2_set_processing);


  
   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer =  pointer + 4096;
  
   status = nx_snmp_agent_context_engine_set(&my_agent, context_engine_id, 
                                             context_engine_size);
  
   if (status != NX_SUCCESS)
   {
      error_counter++;
   }
  
   return;
}
  
VOID thread_agent_entry(ULONG thread_input)
{
  
#ifdef USE_IPV6
UINT        iface_index, address_index;
UINT        status;
NXD_ADDRESS agent_ipv6_address;
#endif
  
  
      /* Allow NetX time to get initialized. */
      tx_thread_sleep(100);
  
      /* If using IPv6, enable IPv6 and ICMPv6 services and get IPv6 addresses 
         registered with NetX Dou. */
  
#ifdef USE_IPV6
  
      /* Enable IPv6 on the IP instance. */
      status = nxd_ipv6_enable(&ip_0);
   
      /* Check for enable errors.  */
      if (status)
      {
  
         error_counter++;
         return;
      }
      /* Enable ICMPv6 on the IP instance. */
      status = nxd_icmp_enable(&ip_0);
  
      /* Check for enable errors.  */
      if (status)
      {
  
         error_counter++;
         return;
      }
  
      agent_ipv6_address.nxd_ip_address.v6[3] = 0x101;
      agent_ipv6_address.nxd_ip_address.v6[2] = 0x0;
      agent_ipv6_address.nxd_ip_address.v6[1] = 0x0000f101;
      agent_ipv6_address.nxd_ip_address.v6[0] = 0x20010db8;
      agent_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
  
      /* Set the primary interface for our DNS IPv6 addresses. */
      iface_index = 0;
  
      /* This assumes we are using the primary network interface (index 0). */
      status = nxd_ipv6_address_set(&ip_0, iface_index, NX_NULL, 10, &address_index);
  
      /* Check for link local address set error.  */
      if (status) 
      {
  
         error_counter++;
         return;
      }
  
      /* Set the host global IP address. We are assuming a 64 
         bit prefix here but this can be any value (< 128). */
      status = nxd_ipv6_address_set(&ip_0, iface_index, &agent_ipv6_address, 64, 
                                    &address_index);
  
      /* Check for global address set error.  */
      if (status) 
      {
  
         error_counter++;
         return;
      }

      /* Wait while NetX Duo validates the link local and global address. */
      tx_thread_sleep(500);
#endif
  
#ifdef AUTHENTICATION_REQUIRED

      /* Create an authentication key.  */
      nx_snmp_agent_md5_key_create(&my_agent, "authpassword", &my_authentication_key);
  
      /* Use the authentication key.  */
      nx_snmp_agent_authenticate_key_use(&my_agent, &my_authentication_key);
#endif
  
#ifdef PRIVACY_REQUIRED
  
      /* Create a privacy key.  */
      nx_snmp_agent_md5_key_create(&my_agent, "privpassword", &my_privacy_key);
  
      /* Use the privacy key.  */
      nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);
#endif
  
      /* Start the SNMP instance.  */
      nx_snmp_agent_start(&my_agent);
  
}
  
/* Define the application's GET processing routine.  */
  
UINT    mib2_get_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
      printf("SNMP Manager GET Request For:  %s", object_requested);
  
      /* Loop through the sample MIB to see if we have information for the supplied 
         variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the matching entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Was it found?  */
         if (status == NX_SUCCESS)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SUCCESS)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
      /* Determine if the entry has a get function.  */
      if (mib2_mib[i].object_get_callback)
      {
  
         /* Yes, call the get function.  */
         status =  (mib2_mib[i].object_get_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
      }
      else
      {
  
         printf(" NO GET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's GETNEXT processing routine.  */
  
UINT    mib2_getnext_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                                NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
   printf("SNMP Manager GETNEXT Request For:  %s", object_requested);
  
   /* Loop through the sample MIB to see if we have information for the supplied 
      variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the next entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Is the next entry the mib greater?  */
         if (status == NX_SNMP_NEXT_ENTRY)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SNMP_NEXT_ENTRY)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
  
      /* Copy the new name into the object.  */
      nx_snmp_object_copy(mib2_mib[i].object_name, object_requested);
  
      printf(" Next Name is: %s", object_requested);
  
      /* Determine if the entry has a get function.  */
      if (mib2_mib[i].object_get_callback)
      {
  
         /* Yes, call the get function.  */
         status =  (mib2_mib[i].object_get_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
  
         /* Determine if the object data indicates an end-of-mib condition.  */
         if (object_data -> nx_snmp_object_data_type == NX_SNMP_END_OF_MIB_VIEW)
         {
  
            /* Copy the name supplied in the mib table.  */
            nx_snmp_object_copy(mib2_mib[i].object_value_ptr, object_requested);
         }
      }
      else
      {
  
         printf(" NO GET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's SET processing routine.  */
  
UINT    mib2_set_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
   printf("SNMP Manager SET Request For:  %s", object_requested);
  
   /* Loop through the sample MIB to see if we have information for the supplied variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the matching entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Was it found?  */
         if (status == NX_SUCCESS)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SUCCESS)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
  
      /* Determine if the entry has a set function.  */
      if (mib2_mib[i].object_set_callback)
      {
  
         /* Yes, call the set function.  */
         status =  (mib2_mib[i].object_set_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
      }
      else
      {
  
         printf(" NO SET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's authentication routine.  */
  
UINT  mib2_username_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *username)
{
  
      printf("Username is:  %s\n", username);
  
      /* Update MIB-2 objects. In this example, it is only the SNMP objects.  */
      mib2_variable_update(&ip_0, &my_agent);
  
      /* No authentication is done, just return success!  */
      return(NX_SUCCESS);
}
  
  
/* Define the application's update routine.  */ 
  
VOID  mib2_variable_update(NX_IP *ip_ptr, NX_SNMP_AGENT *agent_ptr)
{
  
      /* Update the snmp parameters.  */
      snmpInPkts =                agent_ptr -> nx_snmp_agent_packets_received;
      snmpOutPkts =               agent_ptr -> nx_snmp_agent_packets_sent;
      snmpInBadVersions =         agent_ptr -> nx_snmp_agent_invalid_version;
      snmpInBadCommunityNames =   agent_ptr -> nx_snmp_agent_authentication_errors;
      snmpInBadCommunityUsers =   agent_ptr -> nx_snmp_agent_username_errors; 
      snmpInASNParseErrs =        agent_ptr -> nx_snmp_agent_internal_errors;
      snmpInTotalReqVars =        agent_ptr -> nx_snmp_agent_total_get_variables;
      snmpInTotalSetVars =        agent_ptr -> nx_snmp_agent_total_set_variables;
      snmpInGetRequests =         agent_ptr -> nx_snmp_agent_get_requests;
      snmpInGetNexts =            agent_ptr -> nx_snmp_agent_getnext_requests;
      snmpInSetRequests =         agent_ptr -> nx_snmp_agent_set_requests;
      snmpOutTooBigs =            agent_ptr -> nx_snmp_agent_too_big_errors;
      snmpOutNoSuchNames =        agent_ptr -> nx_snmp_agent_no_such_name_errors;
      snmpOutBadValues =          agent_ptr -> nx_snmp_agent_bad_value_errors;
      snmpOutGenErrs =            agent_ptr -> nx_snmp_agent_general_errors;
      snmpOutTraps =              agent_ptr -> nx_snmp_agent_traps_sent;
}   
```
<span data-ttu-id="91f3b-140">그림 1.0 NetX Duo에서 SNMP 에이전트 사용 예제</span><span class="sxs-lookup"><span data-stu-id="91f3b-140">Figure 1.0 Example of SNMP Agent use with NetX Duo</span></span>

## <a name="configuration-options"></a><span data-ttu-id="91f3b-141">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="91f3b-141">Configuration Options</span></span>

<span data-ttu-id="91f3b-142">NetX Duo용 SNMP를 빌드하기 위한 몇 가지 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-142">There are several configuration options for building SNMP for NetX Duo.</span></span> <span data-ttu-id="91f3b-143">다음은 각 옵션에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-143">Following is a list of all options, where each is described in detail:</span></span>  
  
| <span data-ttu-id="91f3b-144">정의</span><span class="sxs-lookup"><span data-stu-id="91f3b-144">Define</span></span>                     | <span data-ttu-id="91f3b-145">의미</span><span class="sxs-lookup"><span data-stu-id="91f3b-145">Meaning</span></span>                                                                                                                                                                                                                                                                        |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="91f3b-146">**NX_SNMP_AGENT_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="91f3b-146">**NX_SNMP_AGENT_PRIORITY**</span></span>     | <span data-ttu-id="91f3b-147">SNMP 에이전트 스레드의 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-147">The priority of the SNMP AGENT thread.</span></span> <span data-ttu-id="91f3b-148">기본적으로 이 값은 16으로 정의되어 우선 순위 16을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-148">By default, this value is defined as 16 to specify priority 16.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="91f3b-149">**NX_SNMP_TYPE_OF_SERVICE**</span><span class="sxs-lookup"><span data-stu-id="91f3b-149">**NX_SNMP_TYPE_OF_SERVICE**</span></span>    | <span data-ttu-id="91f3b-150">SNMP UDP 응답에 필요한 서비스 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-150">Type of service required for the SNMP UDP responses.</span></span> <span data-ttu-id="91f3b-151">기본적으로 이 값은 NX_IP_NORMAL로 정의되어 정상적인 IP 패킷 서비스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-151">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span> <span data-ttu-id="91f3b-152">이 정의는 *nxd_snmp.h.* 를 포함하기 전에 애플리케이션에서 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-152">This define can be set by the application prior to inclusion of *nxd_snmp.h.*</span></span>                                                       |
| <span data-ttu-id="91f3b-153">**NX_SNMP_FRAGMENT_OPTION**</span><span class="sxs-lookup"><span data-stu-id="91f3b-153">**NX_SNMP_FRAGMENT_OPTION**</span></span>    | <span data-ttu-id="91f3b-154">SNMP UDP 요청에 조각을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-154">Fragment enable for SNMP UDP requests.</span></span> <span data-ttu-id="91f3b-155">기본적으로 이 값은 SNMP UDP 조각화를 사용하지 않도록 설정하는 NX_DONT_FRAGMENT입니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-155">By default, this value is NX_DONT_FRAGMENT to disable SNMP UDP fragmenting.</span></span> <span data-ttu-id="91f3b-156">이 정의는 *nxd_snmp.h.* 를 포함하기 전에 애플리케이션에서 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-156">This define can be set by the application prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                 |
| <span data-ttu-id="91f3b-157">**NX_SNMP_TIME_TO_LIVE**</span><span class="sxs-lookup"><span data-stu-id="91f3b-157">**NX_SNMP_TIME_TO_LIVE**</span></span>       | <span data-ttu-id="91f3b-158">만료되기 전까지의 TTL(Time to live)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-158">Specifies the time to live before it expires.</span></span> <span data-ttu-id="91f3b-159">기본값은 0x80으로 설정되지만 *nxd_snmp.h.* 를 포함하기 전에 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-159">The default value is set to 0x80, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                                                         |
| <span data-ttu-id="91f3b-160">**NX_SNMP_AGENT_TIMEOUT**</span><span class="sxs-lookup"><span data-stu-id="91f3b-160">**NX_SNMP_AGENT_TIMEOUT**</span></span>      | <span data-ttu-id="91f3b-161">내부 서비스가 일시 중단될 ThreadX 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-161">Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="91f3b-162">기본값은 100으로 설정되지만 *nxd_snmp.h.* 를 포함하기 전에 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-162">The default value is set to 100, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                         |
| <span data-ttu-id="91f3b-163">**NX_SNMP_MAX_OCTET_STRING**</span><span class="sxs-lookup"><span data-stu-id="91f3b-163">**NX_SNMP_MAX_OCTET_STRING**</span></span>   | <span data-ttu-id="91f3b-164">SNMP 에이전트에서 옥텟 문자열에 허용되는 최대 바이트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-164">Specifies the maximum number of bytes allowed in an octet string in the SNMP Agent.</span></span> <span data-ttu-id="91f3b-165">기본값은 255로 설정되지만 *nxd_snmp.h.* 를 포함하기 전에 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-165">The default value is set to 255, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                    |
| <span data-ttu-id="91f3b-166">**NX_SNMP_MAX_CONTEXT_STRING**</span><span class="sxs-lookup"><span data-stu-id="91f3b-166">**NX_SNMP_MAX_CONTEXT_STRING**</span></span> | <span data-ttu-id="91f3b-167">SNMP 에이전트에서 컨텍스트 엔진 문자열의 최대 바이트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-167">Specifies the maximum number of bytes for a context engine string in the SNMP Agent.</span></span> <span data-ttu-id="91f3b-168">기본값은 32로 설정되지만 *nxd_snmp.h.* 를 포함하기 전에 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-168">The default value is set to 32, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                    |
| <span data-ttu-id="91f3b-169">**NX_SNMP_MAX_USER_NAME**</span><span class="sxs-lookup"><span data-stu-id="91f3b-169">**NX_SNMP_MAX_USER_NAME**</span></span>      | <span data-ttu-id="91f3b-170">사용자 이름(커뮤니티 문자열 포함)의 최대 바이트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-170">Specifies the maximum number of bytes in a username (including community strings).</span></span> <span data-ttu-id="91f3b-171">기본값은 64로 설정되지만 *nxd_snmp.h.* 를 포함하기 전에 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-171">The default value is set to 64, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                      |
| <span data-ttu-id="91f3b-172">**NX_SNMP_MAX_SECURITY_KEY**</span><span class="sxs-lookup"><span data-stu-id="91f3b-172">**NX_SNMP_MAX_SECURITY_KEY**</span></span>   | <span data-ttu-id="91f3b-173">보안 키 문자열에 허용되는 바이트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-173">Specifies the number of bytes allowed in a security key string.</span></span> <span data-ttu-id="91f3b-174">기본값은 64로 설정되지만 *nxd_snmp.h.* 를 포함하기 이전에 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-174">The default value is set to 64, but can be redefined prior to nclusion of *nxd_snmp.h.*</span></span>                                                                                                                          |
| <span data-ttu-id="91f3b-175">**NX_SNMP_PACKET_SIZE**</span><span class="sxs-lookup"><span data-stu-id="91f3b-175">**NX_SNMP_PACKET_SIZE**</span></span>        | <span data-ttu-id="91f3b-176">SNMP 에이전트를 만들 때 지정된 풀의 최소 패킷 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-176">Specifies the minimum size of the packets in the pool specified at SNMP Agent creation.</span></span> <span data-ttu-id="91f3b-177">전체 SNMP 페이로드를 하나의 패킷에 포함될 수 있도록 하려면 최소 크기가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-177">The minimum size is needed to ensure the complete SNMP payload can be contained in one packet.</span></span> <span data-ttu-id="91f3b-178">기본값은 560으로 설정되지만 *nxd_snmp.h.* 를 포함하기 전에 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-178">The default value is set to 560, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span> |
| <span data-ttu-id="91f3b-179">**NX_SNMP_AGENT_PORT**</span><span class="sxs-lookup"><span data-stu-id="91f3b-179">**NX_SNMP_AGENT_PORT**</span></span>         | <span data-ttu-id="91f3b-180">SNMP 관리자 요청을 처리할 UDP 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-180">Specifies the UDP port to field SNMP Manager requests on.</span></span> <span data-ttu-id="91f3b-181">기본 포트는 UDP 포트 161이지만 *nxd_snmp.h.* 를 포함하기 전에 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-181">The default port is UDP port 161, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                                             |
| <span data-ttu-id="91f3b-182">**NX_SNMP_MANAGER_TRAP_PORT**</span><span class="sxs-lookup"><span data-stu-id="91f3b-182">**NX_SNMP_MANAGER_TRAP_PORT**</span></span>  | <span data-ttu-id="91f3b-183">SNMP 에이전트 트랩 요청을 보낼 UDP 포트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-183">Specifies the UDP port to send SNMP Agent trap requests to.</span></span> <span data-ttu-id="91f3b-184">기본 포트는 UDP 포트 162이지만 *nxd_snmp.h.* 를 포함하기 전에 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-184">The default port is UDP port 162, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                                           |
| <span data-ttu-id="91f3b-185">**NX_SNMP_MAX_TRAP_NAME**</span><span class="sxs-lookup"><span data-stu-id="91f3b-185">**NX_SNMP_MAX_TRAP_NAME**</span></span>      | <span data-ttu-id="91f3b-186">트랩 메시지로 보낸 사용자 이름을 저장할 배열의 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-186">Specifies the size of the array to hold the username sent with trap messages.</span></span> <span data-ttu-id="91f3b-187">기본값은 64입니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-187">The default value is 64.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="91f3b-188">**NX_SNMP_MAX_TRAP_KEY**</span><span class="sxs-lookup"><span data-stu-id="91f3b-188">**NX_SNMP_MAX_TRAP_KEY**</span></span>       | <span data-ttu-id="91f3b-189">트랩 메시지의 인증 및 개인 키의 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-189">Specifies the size of the authentication and privacy keys for trap messages.</span></span> <span data-ttu-id="91f3b-190">기본값은 64입니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-190">The default value is 64.</span></span>                                                                                                                                                                          |
| <span data-ttu-id="91f3b-191">**NX_SNMP_TIME_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="91f3b-191">**NX_SNMP_TIME_INTERVAL**</span></span>      | <span data-ttu-id="91f3b-192">이렇게 하면 수신된 SNMP 패킷을 처리하는 동안 SNMP 스레드 작업에서 수행한 타이머 틱의 절전 모드 간격이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-192">This determines the sleep interval in timer ticks taken by the SNMP thread task between processing received SNMP packets.</span></span> <span data-ttu-id="91f3b-193">기본값은 100입니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-193">The default value is 100.</span></span> <span data-ttu-id="91f3b-194">절전 모드 간격 동안 호스트 애플리케이션은 SNMP API 서비스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-194">During this sleep interval the host application has access to SNMP API services.</span></span>                                           |
| <span data-ttu-id="91f3b-195">**NX_SNMP_DISABLE_V1**</span><span class="sxs-lookup"><span data-stu-id="91f3b-195">**NX_SNMP_DISABLE_V1**</span></span>         | <span data-ttu-id="91f3b-196">정의된 바와 같이 *nxd_snmp.c.* 의 모든 SNMP 버전 1 처리를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-196">Defined, this removes all the SNMP Version 1 processing in *nxd_snmp.c.*</span></span> <span data-ttu-id="91f3b-197">기본적으로 이는 정의되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-197">By default this is not defined.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="91f3b-198">**NX_SNMP_DISABLE_V2**</span><span class="sxs-lookup"><span data-stu-id="91f3b-198">**NX_SNMP_DISABLE_V2**</span></span>         | <span data-ttu-id="91f3b-199">정의된 바와 같이 *nxd_snmp.c.* 의 모든 SNMP 버전 2 처리를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-199">Defined, this removes all the SNMP Version 2 processing in *nxd_snmp.c.*</span></span> <span data-ttu-id="91f3b-200">기본적으로 이는 정의되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-200">By default this is not defined.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="91f3b-201">**NX_SNMP_DISABLE_V3**</span><span class="sxs-lookup"><span data-stu-id="91f3b-201">**NX_SNMP_DISABLE_V3**</span></span>         | <span data-ttu-id="91f3b-202">정의된 바와 같이 *nxd_snmp.c.* 의 모든 SNMP 버전 3 처리를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-202">Defined, this removes all the SNMPv3 processing in *nxd_snmp.c.*</span></span> <span data-ttu-id="91f3b-203">기본적으로 이는 정의되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="91f3b-203">By default this is not defined.</span></span>                                                                                                                                                                                 |