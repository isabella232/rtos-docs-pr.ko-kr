---
title: 2장 - Azure RTOS NetX AutoIP 설치 및 사용
description: 이 장에서는 Azure RTOS NetX AutoIP 구성 요소의 설치, 설정, 사용과 관련된 다양한 문제를 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 269a3b4e9754fdc19e2cf1482d483fad2b841de9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810428"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-autoip"></a><span data-ttu-id="4f290-103">2장 - Azure RTOS NetX AutoIP 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="4f290-103">Chapter 2 - Installation and use of Azure RTOS NetX AutoIP</span></span>

<span data-ttu-id="4f290-104">이 장에서는 Azure RTOS NetX AutoIP 구성 요소의 설치, 설정, 사용과 관련된 다양한 문제를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX AutoIP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="4f290-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="4f290-105">Product Distribution</span></span>

<span data-ttu-id="4f290-106">NetX AutoIP는 [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-106">AutoIP for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="4f290-107">패키지에는 다음과 같이 3개의 원본 파일과 하나의 포함 파일, 이 문서가 포함된 PDF 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="4f290-108">**nx_auto_ip.h**: NetX AutoIP의 헤더 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-108">**nx_auto_ip.h**: Header file for NetX AutoIP</span></span>
- <span data-ttu-id="4f290-109">**nx_auto_ip.c**: NetX AutoIP의 C 원본 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-109">**nx_auto_ip.c**: C Source file for NetX AutoIP</span></span>
- <span data-ttu-id="4f290-110">**demo_netx_auto_ip.c**: NetX AutoIP 데모의 C 원본 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-110">**demo_netx_auto_ip.c**: C Source file for NetX AutoIP Demo</span></span>
- <span data-ttu-id="4f290-111">**nx_auto_ip.pdf**: NetX AutoIP에 대한 PDF 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-111">**nx_auto_ip.pdf**: PDF description of NetX AutoIP</span></span>

## <a name="autoip-installation"></a><span data-ttu-id="4f290-112">AutoIP 설치</span><span class="sxs-lookup"><span data-stu-id="4f290-112">AutoIP Installation</span></span>

<span data-ttu-id="4f290-113">NetX AutoIP를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-113">In order to use NetX AutoIP, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="4f290-114">예를 들어 NetX가 “ *\threadx\arm7\green*” 디렉터리에 설치된 경우 *nx_auto_ip.h*, *nx_auto_ip.c*, *demo_netx_auto_ip.c* 파일을 이 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_auto_ip.h*, *nx_auto_ip.c*, and *demo_netx_auto_ip.c* files should be copied into this directory.</span></span>

## <a name="using-autoip"></a><span data-ttu-id="4f290-115">AutoIP 사용</span><span class="sxs-lookup"><span data-stu-id="4f290-115">Using AutoIP</span></span>

<span data-ttu-id="4f290-116">NetX AutoIP를 사용하는 것은 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-116">Using NetX AutoIP is easy.</span></span> <span data-ttu-id="4f290-117">기본적으로 애플리케이션 코드는 ThreadX 및 NetX를 사용하기 위해 *tx_api.h* 및 *nx_api.h* 를 포함한 후 *nx_auto_ip.h* 를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-117">Basically, the application code must include *nx_auto_ip.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="4f290-118">*nx_auto_ip.h* 를 포함하면 애플리케이션 코드가 이 가이드의 뒷부분에 지정된 AutoIP 함수를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-118">Once *nx_auto_ip.h* is included, the application code is then able to make the AutoIP function calls specified later in this guide.</span></span> <span data-ttu-id="4f290-119">애플리케이션은 *nx_auto_ip.c* 도 빌드 프로세스에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-119">The application must also include *nx_auto_ip.c* in the build process.</span></span> <span data-ttu-id="4f290-120">이러한 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일되어야 하며 개체 양식이 애플리케이션의 파일과 함께 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="4f290-121">이렇게 간단하게 NetX AutoIP를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-121">This is all that is required to use NetX AutoIP.</span></span>

> [!NOTE]
> <span data-ttu-id="4f290-122">AutoIP는 NetX ARP 서비스를 활용하므로 AutoIP를 사용하기 전에 *nx_arp_enable* 호출로 ARP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-122">Since AutoIP utilizes NetX ARP services, ARP must be enabled with the *nx_arp_enable* call prior to using AutoIP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="4f290-123">간단한 예제 시스템</span><span class="sxs-lookup"><span data-stu-id="4f290-123">Small Example System</span></span>

<span data-ttu-id="4f290-124">NetX AutoIP를 사용하는 것이 얼마나 쉬운지 보여 주는 예가 아래에 표시된 그림 1.1에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-124">An example of how easy it is to use NetX AutoIP is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="4f290-125">이 예에서는 002 줄에서 AutoIP 포함 파일 *nx_auto_ip.h* 를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-125">In this example, the AutoIP include file *nx_auto_ip.h* is brought in at line 002.</span></span> <span data-ttu-id="4f290-126">그런 다음, 090 줄에서 “*tx_application_define*”에 NetX AutoIP 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-126">Next, the NetX AutoIP instance is created in "*tx_application_define*" at line 090.</span></span> <span data-ttu-id="4f290-127">NetX AutoIP 제어 블록 “auto_ip_0”은 이전에 015 줄에서 전역 변수로 정의되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-127">Note that the NetX AutoIP control block "auto_ip_0" was defined previously as a global variable at line 015.</span></span> <span data-ttu-id="4f290-128">인스턴스가 성공적으로 생성되면 098 줄에서 NetX AutoIP가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-128">After successful creation, an NetX AutoIP is started at line 098.</span></span> <span data-ttu-id="4f290-129">IP 주소 변경 콜백 함수 처리는 105 줄에서 시작되며, 이후 충돌 또는 가능한 DHCP 주소 확인을 처리하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-129">The IP address change callback function processing starts at line 105, which is used to handle subsequent conflicts or possible DHCP address resolution.</span></span>

> [!NOTE]
> <span data-ttu-id="4f290-130">아래 예에서는 호스트 디바이스가 단일 홈 디바이스인 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-130">The example below assumes the host device is a single-homed device.</span></span> <span data-ttu-id="4f290-131">멀티홈 디바이스의 경우 호스트 애플리케이션은 NetX AutoIP 서비스 *nx_auto_ip_interface_* set을 사용하여 IP 주소를 검색할 보조 네트워크 인터페이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-131">For a multihomed device, the host application can use the NetX AutoIP service *nx_auto_ip_interface_* set to specify a secondary network interface to probe for an IP address.</span></span> <span data-ttu-id="4f290-132">멀티홈 애플리케이션 설정에 대한 자세한 내용은 **NetX 사용자 가이드** 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4f290-132">See the **NetX User Guide** for more details on setting up multihomed applications.</span></span> <span data-ttu-id="4f290-133">호스트 애플리케이션에서 NetX API *nx_status_ip_interface_check* 를 사용하여 AutoIP가 IP 주소를 얻었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-133">Note further that the host application should use the NetX API *nx_status_ip_interface_check* to verify AutoIP has obtained an IP address.</span></span>

## <a name="example-of-autoip-use-with-netx"></a><span data-ttu-id="4f290-134">NetX에서의 AutoIP 사용 예</span><span class="sxs-lookup"><span data-stu-id="4f290-134">Example of AutoIP use with NetX</span></span>

```c
000 #include "tx_api.h"
001 #include "nx_api.h"
002 #include "nx_auto_ip.h"
003
004 #define         DEMO_STACK_SIZE         4096
005
006 /* Define the ThreadX and NetX object control blocks... */
007
008 TX_THREAD         thread_0;
009 NX_PACKET_POOL    pool_0;
010 NX_IP             ip_0;
011
012
013 /* Define the AUTO IP structures for the IP instance. */
014
015 NX_AUTO_IP         auto_ip_0;
016
017
018 /* Define the counters used in the demo application... */
019
020 ULONG             thread_0_counter;
021 ULONG             address_changes;
022 ULONG             error_counter;
023
024
025 /* Define thread prototypes. */
026
027 void     thread_0_entry(ULONG thread_input);
028 void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
029 void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
030
031
032 /* Define main entry point. */
033
034 int main()
035 {
036
037     /* Enter the ThreadX kernel. */
038     tx_kernel_enter();
039 }
040
041
042 /* Define what the initial system looks like. */
043
044 void     tx_application_define(void *first_unused_memory)
045 {
046
047 CHAR     *pointer;
048 UINT     status;
049
050
051     /* Setup the working pointer. */
052     pointer = (CHAR *) first_unused_memory;
053
054     /* Create the main thread. */
055     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
056                     pointer, DEMO_STACK_SIZE,
057                     16, 16, 1, TX_AUTO_START);
058
059     pointer = pointer + DEMO_STACK_SIZE;
060
061     /* Initialize the NetX system. */
062     nx_system_initialize();
063
064     /* Create a packet pool. */
065     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
066                                     pointer, 4096);
067                                     pointer = pointer + 4096;
068
069     if (status)
070         error_counter++;
071
072     /* Create an IP instance. */
073     status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
074                             0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
075                             pointer, 4096, 1);
076                             pointer = pointer + 4096;
077
078     if (status)
079         error_counter++;
080
081     /* Enable ARP and supply ARP cache memory for IP Instance 0. */
082     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
083     pointer = pointer + 1024;
084
085     /* Check ARP enable status. */
086     if (status)
087         error_counter++;
088
089     /* Create the AutoIP instance for IP Instance 0. */
090     status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
091     pointer = pointer + 4096;
092
093     /* Check AutoIP create status. */
094     if (status)
095         error_counter++;
096
097     /* Start AutoIP instances. */
098     status = nx_auto_ip_start(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);
099
100     /* Check AutoIP start status. */
101     if (status)
102         error_counter++;
103
104     /* Register an IP address change function for IP Instance 0. */
105     status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
106                                         (void *) &auto_ip_0);
107
108     /* Check IP address change notify status. */
109     if (status)
110         error_counter++;
111     }
112
113
114     /* Define the test thread. */
115
116     void thread_0_entry(ULONG thread_input)
117     {
118
119     UINT      status;
120     ULONG     actual_status;
121
122
123          /* Wait for IP address to be resolved. */
124         do
125         {
126
127             /* Call IP status check routine. */
128             status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
129                                         &actual_status, 10000);
130
131         } while (status != NX_SUCCESS);
132
133         /* Since the IP address is resolved at this point, the application
134         can now fully utilize NetX! */
135
136         while(1)
137         {
138
139
140
141             /* Increment thread 0's counter. */
142             thread_0_counter++;
143
144             /* Sleep... */
145             tx_thread_sleep(10);
146         }
147     }
148
149
150     void ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
151     {
152
153     ULONG         ip_address;
154     ULONG         network_mask;
155     NX_AUTO_IP    *auto_ip_ptr;
156
157
158     /* Setup pointer to auto IP instance. */
159     auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;
160
161     /* Pickup the current IP address. */
162     nx_ip_address_get(ip_ptr, &ip_address, &network_mask);
163
164     /* Determine if the IP address has changed back to zero. If so,
165     make sure the AutoIP instance is started. */
166     if (ip_address == 0)
167     {
168
169         /* Get the last AutoIP address for this node. */
170         nx_auto_ip_get_address(auto_ip_ptr, &ip_address);
171
172         /* Start this AutoIP instance. */
173         nx_auto_ip_start(auto_ip_ptr, ip_address);
174     }
175
176     /* Determine if IP address has transitioned to a non local IP address. */
177     else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
178     {
179
180         /* Stop the AutoIP processing. */
181         nx_auto_ip_stop(auto_ip_ptr);
182     }
183
184     /* Increment a counter. */
185     address_changes++;
186 }
```

## <a name="configuration-options"></a><span data-ttu-id="4f290-135">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="4f290-135">Configuration Options</span></span>

<span data-ttu-id="4f290-136">NetX AutoIP를 빌드하는 데 사용되는 여러 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-136">There are several configuration options for building NetX AutoIP.</span></span> <span data-ttu-id="4f290-137">다음은 각 옵션에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-137">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="4f290-138">**NX_DISABLE_ERROR_CHECKING**: 이 옵션을 정의하면 기본 AutoIP 오류 검사를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-138">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic AutoIP error checking.</span></span> <span data-ttu-id="4f290-139">일반적으로 애플리케이션이 디버그된 후에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-139">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="4f290-140">**NX_AUTO_IP_PROBE_WAIT**: 첫 번째 프로브 송신 전 대기 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-140">**NX_AUTO_IP_PROBE_WAIT**: The number of seconds to wait before sending first probe.</span></span> <span data-ttu-id="4f290-141">기본적으로 이 값은 1로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-141">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="4f290-142">**NX_AUTO_IP_PROBE_NUM**: 송신할 ARP 프로브 수입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-142">**NX_AUTO_IP_PROBE_NUM**: The number of ARP probes to send.</span></span> <span data-ttu-id="4f290-143">기본적으로 이 값은 3으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-143">By default, this value is defined as 3.</span></span>
- <span data-ttu-id="4f290-144">**NX_AUTO_IP_PROBE_MIN**: 프로브 송신 간 최소 대기 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-144">**NX_AUTO_IP_PROBE_MIN**: The minimum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="4f290-145">기본적으로 이 값은 1로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-145">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="4f290-146">**NX_AUTO_IP_PROBE_MAX**: 프로브 송신 간 최대 대기 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-146">**NX_AUTO_IP_PROBE_MAX**: The maximum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="4f290-147">기본적으로 이 값은 2로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-147">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="4f290-148">**NX_AUTO_IP_MAX_CONFLICTS**: 처리 지연을 늘리기 전 AutoIP 충돌 수입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-148">**NX_AUTO_IP_MAX_CONFLICTS**: The number of AutoIP conflicts before increasing processing delays.</span></span> <span data-ttu-id="4f290-149">기본적으로 이 값은 10으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-149">By default, this value is defined as 10.</span></span>
- <span data-ttu-id="4f290-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: 총 충돌 수를 초과하는 경우 연장할 대기 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: The number of seconds to extend the wait period when the total number of conflicts is exceeded.</span></span> <span data-ttu-id="4f290-151">기본적으로 이 값은 60으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-151">By default, this value is defined as 60.</span></span>
- <span data-ttu-id="4f290-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: 알림 송신 전 대기 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: The number of seconds to wait before sending announcement.</span></span> <span data-ttu-id="4f290-153">기본적으로 이 값은 2로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-153">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="4f290-154">**NX_AUTO_IP_ANNOUNCE_NUM**: 송신할 ARP 알림 수입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-154">**NX_AUTO_IP_ANNOUNCE_NUM**: The number of ARP announces to send.</span></span> <span data-ttu-id="4f290-155">기본적으로 이 값은 2로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-155">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="4f290-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: 알림 송신 간 대기 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: The number of seconds to wait between sending announces.</span></span> <span data-ttu-id="4f290-157">기본적으로 이 값은 2로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-157">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="4f290-158">**NX_AUTO_IP_DEFEND_INTERVAL**: 방어 알림 간 대기 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-158">**NX_AUTO_IP_DEFEND_INTERVAL**: The number of seconds to wait between defense announces.</span></span> <span data-ttu-id="4f290-159">기본적으로 이 값은 10으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f290-159">By default, this value is defined as 10.</span></span>