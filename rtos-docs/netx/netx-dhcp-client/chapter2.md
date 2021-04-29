---
title: 2장 - Azure RTOS NetX DHCP 클라이언트 설치 및 사용
description: 이 장에서는 Azure RTOS NetX DHCP 클라이언트 구성 요소의 설치, 설정, 사용과 관련된 다양한 문제를 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9224a4df70b8199032066e30108250a3baeb65f5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811616"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dhcp-client"></a><span data-ttu-id="6c359-103">2장 - Azure RTOS NetX DHCP 클라이언트 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="6c359-103">Chapter 2 - Installation and use of Azure RTOS NetX DHCP Client</span></span>

<span data-ttu-id="6c359-104">이 장에서는 Azure RTOS NetX DHCP 구성 요소의 설치, 설정, 사용과 관련된 다양한 문제를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX DHCP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="6c359-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="6c359-105">Product Distribution</span></span>

<span data-ttu-id="6c359-106">NetX용 DHCP는 [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-106">DHCP for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="6c359-107">이 패키지에는 다음과 같이 소스 파일 두 개와 이 문서가 포함된 PDF 파일이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="6c359-108">**nx_dhcp.h** NetX용 DHCP의 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="6c359-108">**nx_dhcp.h** Header file for DHCP for NetX</span></span>

- <span data-ttu-id="6c359-109">**nx_dhcp.c** NetX용 DHCP의 C 소스 파일</span><span class="sxs-lookup"><span data-stu-id="6c359-109">**nx_dhcp.c** C Source file for DHCP for NetX</span></span>

- <span data-ttu-id="6c359-110">**nx_dhcp.pdf** NetX용 DHCP의 PDF 설명서</span><span class="sxs-lookup"><span data-stu-id="6c359-110">**nx_dhcp.pdf** PDF description of DHCP for NetX</span></span>

- <span data-ttu-id="6c359-111">**demo_netx_dhcp.c** NetX DHCP 데모</span><span class="sxs-lookup"><span data-stu-id="6c359-111">**demo_netx_dhcp.c** NetX DHCP demonstration</span></span>

- <span data-ttu-id="6c359-112">**demo_netx_multihome_dhcp_client.c** 여러 인터페이스에서 DHCP의 NetX DHCP 클라이언트 데모</span><span class="sxs-lookup"><span data-stu-id="6c359-112">**demo_netx_multihome_dhcp_client.c** NetX DHCP Client demonstration of DHCP on multiple interfaces</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="6c359-113">DHCP 설치</span><span class="sxs-lookup"><span data-stu-id="6c359-113">DHCP Installation</span></span>

<span data-ttu-id="6c359-114">NetX용 DHCP를 사용하려면 이전에 언급한 전체 배포판을 NetX가 설치된 동일한 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-114">To use DHCP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="6c359-115">예를 들어, NetX가 “ *\threadx\arm7\green*” 디렉터리에 설치된 경우 *nx_dhcp.h* 와 *nx_dhcp.c* 파일을 이 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-115">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_dhcp.h* and *nx_dhcp.c* files should be copied into this directory.</span></span>

## <a name="using-dhcp"></a><span data-ttu-id="6c359-116">DHCP 사용</span><span class="sxs-lookup"><span data-stu-id="6c359-116">Using DHCP</span></span>

<span data-ttu-id="6c359-117">NetX용 DHCP는 간편하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-117">Using DHCP for NetX is easy.</span></span> <span data-ttu-id="6c359-118">기본적으로 ThreadX와 NetX를 사용하려면 애플리케이션 코드에 *tx_api.h* 와 *nx_api.h* 를 각각 포함한 다음, *nx_dhcp.h* 를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-118">Basically, the application code must include *nx_dhcp.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="6c359-119">*nx_dhcp.h* 가 포함되면 애플리케이션 코드가 이 가이드의 뒷부분에 나오는 DHCP 함수를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-119">Once *nx_dhcp.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="6c359-120">애플리케이션은 빌드 프로세스에 *nx_dhcp.c* 도 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-120">The application must also include *nx_dhcp.c* in the build process.</span></span> <span data-ttu-id="6c359-121">이 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일해야 하며, 해당 개체 형식은 애플리케이션의 파일과 함께 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-121">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="6c359-122">여기까지가 NetX DHCP를 사용하기 위해 필요한 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-122">This is all that is required to use NetX DHCP.</span></span>

<span data-ttu-id="6c359-123">DHCP는 NetX UDP 서비스를 활용하므로 DHCP를 사용하기 전에 *nx_udp_enable* 호출을 사용하여 UDP를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-123">Note that since DHCP utilizes NetX UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

<span data-ttu-id="6c359-124">이전에 할당된 IP 주소를 가져오기 위해 DHCP 클라이언트에서 DHCP 서버에 대한 요청 메시지와 50 “요청된 IP 주소” 옵션을 사용하여 DHCP 프로세스를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-124">To obtain a previously assigned IP address, the DHCP Client can initiate the DHCP process with the Request message and Option 50 “Requested IP Address” to the DHCP Server.</span></span> <span data-ttu-id="6c359-125">DHCP 서버는 IP 주소를 클라이언트에 부여하면 ACK 메시지를 사용하여 응답하고, 거부하면 NACK를 사용하여 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-125">The DHCP Server will respond with either an ACK message if it grants the IP address to the Client or a NACK if it refuses.</span></span> <span data-ttu-id="6c359-126">NACK를 사용하여 응답하는 경우 DHCP 클라이언트가 요청된 IP 주소 없이 검색 메시지를 사용하여 Init 상태에서 DHCP 프로세스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-126">In the latter case, the DHCP Client restarts the DHCP process at the Init state with a Discover message and no requested IP address.</span></span> <span data-ttu-id="6c359-127">호스트 애플리케이션은 먼저 DHCP 클라이언트를 만든 다음, *nx_dhcp_request_client_ip* API 서비스를 호출하여 요청된 IP 주소를 설정한 후에 *nx_dhcp_start* 를 사용하여 DHCP 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-127">The host application first creates the DHCP Client, then calls the *nx_dhcp_request_client_ip* API service to set the requested IP address before starting the DHCP process with *nx_dhcp_start*.</span></span> <span data-ttu-id="6c359-128">자세한 내용은 이 문서의 다른 부분에 나와 있는 DHCP 애플리케이션 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c359-128">An example DHCP application is provided elsewhere in this document for more details.</span></span>

## <a name="in-the-bound-state"></a><span data-ttu-id="6c359-129">바인딩된 상태에서 처리</span><span class="sxs-lookup"><span data-stu-id="6c359-129">In the Bound State</span></span>

<span data-ttu-id="6c359-130">DHCP 클라이언트가 바인딩 상태에 있는 동안 DHCP 클라이언트 스레드에서 간격(NX_DHCP_TIME_INTERVAL에서 지정한)당 한 번씩 클라이언트 상태를 처리하고 클라이언트에 할당된 IP 임대에 남은 시간을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-130">While the DHCP Client is in the bound state, the DHCP Client thread processes the Client state once per interval (as specified by NX_DHCP_TIME_INTERVAL) and decrements the time remaining on the IP lease assigned to the Client.</span></span> <span data-ttu-id="6c359-131">갱신 시간이 지나면 DHCP 클라이언트 상태가 클라이언트에서 DHCP 서버에 갱신을 요청하는 RENEW 상태로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-131">When the renewal time has elapsed the DHCP Client state is updated to the RENEW state where the Client will request a renewal from the DHCP Server.</span></span>


## <a name="sending-dhcp-messages-to-the-server"></a><span data-ttu-id="6c359-132">서버에 DHCP 메시지 보내기</span><span class="sxs-lookup"><span data-stu-id="6c359-132">Sending DHCP Messages To The Server</span></span>

<span data-ttu-id="6c359-133">DHCP 클라이언트에는 호스트 애플리케이션이 DHCP 서버에 메시지를 보내도록 하는 API 서비스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-133">The DHCP Client has API services that allow the host application to send a message to the DHCP Server.</span></span> <span data-ttu-id="6c359-134">API 서비스는 DHCP 클라이언트 내부 상태를 업데이트하지 않은 상태에서 주로 메시지를 보내기 때문에 호스트 애플리케이션에서 DHCP 클라이언트 프로토콜을 수동으로 실행하도록 하는 데 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-134">Note these services are NOT intended for the host application to manually run the DHCP Client protocol as they primarily send the message without necessarily updating the DHCP Client internal state.</span></span>

  - <span data-ttu-id="6c359-135">*nx_dhcp_release*: 호스트 애플리케이션이 네트워크에서 나가거나 IP 주소를 포기해야 하는 경우 RELEASE 메시지를 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-135">*nx_dhcp_release*: this sends a RELEASE message to the Server when the host application is either leaving the network or needs relinquish its IP address.</span></span>

  - <span data-ttu-id="6c359-136">*nx_dhcp_decline*: 호스트 애플리케이션이 DHCP 클라이언트와 독립적으로 IP 주소를 이미 사용하고 있음을 확인하는 경우 DECLINE 메시지를 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-136">*nx_dhcp_decline*: this sends a DECLINE message to the Server if the host application determines independently of the DHCP Client that its IP address is already in use.</span></span>

  - <span data-ttu-id="6c359-137">*nx_dhcp_forcerenew*: FORCERENEW 메시지를 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-137">*nx_dhcp_forcerenew*: this sends a FORCERENEW message to the Server</span></span>

  - <span data-ttu-id="6c359-138">*nx_dhcp_send_request*: *nx_dhcp.h* 에 지정된 DHCP 메시지 유형을 인수로 사용하여 메시지를 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-138">*nx_dhcp_send_request*: This takes as an argument a DHCP message type, as specified in *nx_dhcp.h*, and sends the message to the Server.</span></span> <span data-ttu-id="6c359-139">주로 DHCP INFORM 메시지를 보내기 위한 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-139">This is intended primarily for sending the DHCP INFORM message.</span></span>

<span data-ttu-id="6c359-140">이 문서의 다른 부분에서 해당 서비스에 대한 자세한 내용을 살펴보려면 “*DHCP 서비스 설명*”을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c359-140">See “*Description of DHCP Services*” for more information about these services elsewhere in this document.</span></span>

## <a name="starting-and-stopping-the-dhcp-client"></a><span data-ttu-id="6c359-141">DHCP 클라이언트 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="6c359-141">Starting and Stopping the DHCP Client</span></span>

<span data-ttu-id="6c359-142">DHCP 클라이언트가 바인딩된 상태에 도달했는지 여부와 관계없이 DHCP 클라이언트를 중지하려면 호스트 애플리케이션에서 *nx_dhcp_stop* 을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-142">To stop the DHCP Client, regardless if it has achieved a bound state, the host application calls *nx_dhcp_stop*.</span></span>

<span data-ttu-id="6c359-143">DHCP 클라이언트를 다시 시작하려면 먼저 호스트 애플리케이션에서 위에서 설명한 *nx_dhcp_stop* 서비스를 사용하여 DHCP 클라이언트를 중지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-143">To restart a DHCP client, the host application must first stop the DHCP Client using the *nx_dhcp_stop* service described above.</span></span> <span data-ttu-id="6c359-144">그러면 호스트에서 *nx_dhcp_start* 를 호출하여 DHCP 클라이언트를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-144">Then the host can call *nx_dhcp_start* to resume the DHCP Client.</span></span> <span data-ttu-id="6c359-145">예를 들어 호스트 애플리케이션이 이전 DHCP 클라이언트 프로필(예: 다른 네트워크의 이전 DHCP 서버에서 가져온 프로필)을 지우려는 경우 호스트 애플리케이션에서 nx_dhcp_start를 호출하기 전에 내부적으로 이 작업을 수행하기 위해 *nx_dhcp_reinitialize* 를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-145">If the host application wishes to clear a previous DHCP Client profile, for example, one obtained from a previous DHCP Server on another network, the host application should call *nx_dhcp_reinitialize* to perform this task internally before calling nx_dhcp_start.</span></span>

<span data-ttu-id="6c359-146">일반적인 시퀀스는 다음과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-146">A typical sequence might be:</span></span>

```C
nx_dhcp_stop(&my_dhcp);

nx_dhcp_reinitialize(&my_dhcp);

nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="6c359-147">단일 DHCP 인터페이스에서만 실행되는 DHCP 애플리케이션의 경우 DHCP 클라이언트를 중지하면 DHCP 클라이언트 타이머도 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-147">For DHCP applications running on only a single DHCP interface, stopping the DHCP Client also inactivates the DHCP CLIENT timer.</span></span> <span data-ttu-id="6c359-148">따라서 IP 임대에 남아 있는 시간을 더 이상 추적하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-148">Thus it is no longer keeping track of the time remaining on the IP lease.</span></span> <span data-ttu-id="6c359-149">특정 인터페이스에서 DHCP 클라이언트를 중지하면 DHCP 클라이언트 타이머가 비활성화되지 않지만, 해당 인터페이스의 IP 임대에 남아 있는 시간에 대한 타이머 업데이트가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-149">Stopping DHCP Client on a particular interface will not inactivate the DHCP Client timer but will stop timer updates to the time remaining on the IP lease on that interface.</span></span>

<span data-ttu-id="6c359-150">따라서 호스트 애플리케이션에서 네트워크를 다시 부팅하거나 전환해야 하는 경우가 아니면 DHCP 클라이언트를 중지하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-150">Therefore, stopping the DHCP Client is not advised unless the host application requires rebooting or switching networks.</span></span>

## <a name="using-the-dhcp-client-with-auto-ip"></a><span data-ttu-id="6c359-151">자동 IP를 통해 DHCP 클라이언트 사용</span><span class="sxs-lookup"><span data-stu-id="6c359-151">Using the DHCP Client with Auto IP</span></span>

<span data-ttu-id="6c359-152">NetX DHCP 클라이언트는 DHCP 서버를 사용할 수 있거나 DHCP 서버가 응답할 수 있다는 보장이 없는 주소를 DHCP와 자동 IP를 통해 보장하는 애플리케이션의 자동 IP 프로토콜과 동시에 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-152">The NetX DHCP Client works concurrently with the Auto IP protocol in applications where DHCP and Auto IP guarantee an address where a DHCP Server is not guaranteed to be available or responding.</span></span> <span data-ttu-id="6c359-153">그러나 호스트에서 서버를 검색하거나 IP 주소를 할당받을 수 없는 경우 로컬 IP 주소에 대해 자동 IP 프로토콜로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-153">However, If the host is unable to detect a Server or get an IP address assigned, it can switch to the Auto IP protocol for a local IP address.</span></span> <span data-ttu-id="6c359-154">이렇게 하려면 먼저 자동 IP가 “프로브”와 “방어” 단계를 거치는 동안 DHCP 클라이언트를 일시적으로 중지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-154">However before doing so, it is advisable to stop the DHCP Client temporarily while Auto IP goes through the “probe” and “defense” stages.</span></span> <span data-ttu-id="6c359-155">자동 IP 주소가 호스트에 할당되면 DHCP 클라이언트를 다시 시작할 수 있고, DHCP 서버를 사용할 수 있게 되면 애플리케이션이 실행되는 동안 DHCP 서버에서 제공하는 IP 주소를 호스트 IP 주소에서 수락할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-155">Once an Auto IP address is assigned to the host, the DHCP Client can be restarted and if a DHCP Server does become available, the host IP address can accept the IP address offered by the DHCP Server while the application is running.</span></span>

<span data-ttu-id="6c359-156">NetX 자동 IP에는 IP 주소가 변경되는 경우 호스트에서 해당 작업을 모니터링할 수 있는 주소 변경 알림이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-156">The NetX Auto IP has an address change notification for the host to monitor its activities in the event of an IP address change.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="6c359-157">간단한 예제 시스템</span><span class="sxs-lookup"><span data-stu-id="6c359-157">Small Example System</span></span>

<span data-ttu-id="6c359-158">NetX 사용 방법의 예는 아래 그림 1.1에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-158">An example of how use NetX is described in Figure 1.1 below.</span></span> <span data-ttu-id="6c359-159">DHCP 클라이언트는 줄 101에서 “*my_thread_entry*”로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-159">The DHCP Client is created “*my_thread_entry*” at line 101.</span></span> <span data-ttu-id="6c359-160">생성된 후에는 줄 108에서 *nx_dhcp_start* 호출 시 DHCP 프로세스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-160">After successful creation, the DHCP process is initiated at the call to *nx_dhcp_start* at line 108.</span></span> <span data-ttu-id="6c359-161">이때 DHCP 클라이언트는 DHCP 서버에 접속을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-161">At this point the DHCP Client attempts are initiated to contact the DHCP server.</span></span> <span data-ttu-id="6c359-162">이 프로세스를 진행하는 동안 애플리케이션 코드는 줄 95부터 *nx_ip_status_check* 서비스(또는 보조 인터페이스의 경우 *nx_ip_interface_status_check*)를 사용하여 유효한 IP 주소가 IP 인스턴스에 등록될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-162">During this process, the application code waits for a valid IP address to be registered with the IP instance using the *nx_ip_status_check* service (or *nx_ip_interface_status_check* for a secondary interface) starting at line 95.</span></span> <span data-ttu-id="6c359-163">이는 일반적으로 대기 옵션이 짧은 루프에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-163">This is more commonly done in a loop with a shorter wait option.</span></span>

<span data-ttu-id="6c359-164">줄 127 이후 DHCP는 유효한 IP 주소를 받고 NetX Duo TCP/IP 서비스를 원하는 대로 활용하여 애플리케이션을 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-164">After line 127, DHCP has received a valid IP address and the application can then proceed, utilizing NetX TCP/IP services as desired.</span></span>

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
      0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
      DEMO_STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


/* Define my thread. */

void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    actual_status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                            &actual_status, 100);

  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

<span data-ttu-id="6c359-165">그림 1.1 NetX에서 DHCP 사용 예제</span><span class="sxs-lookup"><span data-stu-id="6c359-165">Figure 1.1 Example of DHCP use with NetX</span></span>

## <a name="multi-server-environments"></a><span data-ttu-id="6c359-166">다중 서버 환경</span><span class="sxs-lookup"><span data-stu-id="6c359-166">Multi-Server Environments</span></span>

<span data-ttu-id="6c359-167">둘 이상의 DHCP 서버가 있는 네트워크에서 DHCP 클라이언트는 처음 받은 DHCP 서버 제안 메시지를 수락하고, 요청 상태로 이동하며, 받은 다른 모든 제안을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-167">On networks where there is more than one DHCP Server, the DHCP Client accepts the first received DHCP Server Offer message, advances to the Request state, and ignores any other received offers.</span></span>

## <a name="arp-probes"></a><span data-ttu-id="6c359-168">ARP 프로브</span><span class="sxs-lookup"><span data-stu-id="6c359-168">ARP Probes</span></span>

<span data-ttu-id="6c359-169">DHCP 클라이언트는 DHCP 서버에서 IP 주소를 할당한 후에 하나 이상의 ARP 프로브를 보내 IP 주소가 이미 사용되고 있지 않은지 확인하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-169">The DHCP Client can be configured to send one or more ARP probes after IP address assignment from the DHCP Server to verify the IP address is not already in use.</span></span> <span data-ttu-id="6c359-170">ARP 프로브 단계는 RFC 2131에서 권장하며, 둘 이상의 DHCP 서버가 있는 환경에서 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-170">The ARP probe step is recommended by RFC 2131 and is particularly important in environments with more than one DHCP Server.</span></span> <span data-ttu-id="6c359-171">호스트 애플리케이션에서 NX_DHCP_CLIENT_SEND_ARP_PROBE 옵션을 사용하도록 설정하면(추가 ARP 프로브 옵션은 2장의 **구성 옵션** 참조) DHCP 클라이언트는 ‘자체 주소가 지정된’ ARP 프로브를 보내고 응답을 위해 지정된 시간 동안 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-171">If the host application enables the NX_DHCP_CLIENT_SEND_ARP_PROBE option (see **Configuration Options** in Chapter Two for additional ARP probe options), the DHCP Client will send a ‘self addressed’ ARP probe and wait for the specified time for a response.</span></span> <span data-ttu-id="6c359-172">받은 항목이 없으면 DHCP 클라이언트가 바인딩됨 상태로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-172">If none is received, the DHCP Client advances to the Bound state.</span></span> <span data-ttu-id="6c359-173">응답을 받으면 DHCP 클라이언트에서 주소가 이미 사용 중이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-173">If a response is received, the DHCP Client assumes the address is already in use.</span></span> <span data-ttu-id="6c359-174">자동으로 DECLINE 메시지를 서버에 보내고, 클라이언트를 다시 초기화하여 INIT 상태에서 DHCP 프로브를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-174">It automatically sends a DECLINE message to the Server, and reinitializes the Client to restart the DHCP probes again from the INIT state.</span></span> <span data-ttu-id="6c359-175">그러면 DHCP 상태 시스템이 다시 시작되고 클라이언트에서 다른 DISCOVER 메시지를 서버에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-175">This restarts the DHCP state machine and the Client sends another DISCOVER message to the Server.</span></span>

## <a name="bootp-protocol"></a><span data-ttu-id="6c359-176">BOOTP 프로토콜</span><span class="sxs-lookup"><span data-stu-id="6c359-176">BOOTP Protocol</span></span>

<span data-ttu-id="6c359-177">DHCP 클라이언트는 BOOTP 프로토콜과 DHCP 프로토콜도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-177">The DHCP Client also supports the BOOTP protocol as well the DHCP protocol.</span></span> <span data-ttu-id="6c359-178">이 옵션을 사용하도록 설정하고 DHCP 대신 BOOTP를 사용하려면 호스트 애플리케이션에서 NX_DHCP_BOOTP_ENABLE 구성 옵션을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-178">To enable this option and use BOOTP instead of DHCP, the host application must set the NX_DHCP_BOOTP_ENABLE configuration option.</span></span> <span data-ttu-id="6c359-179">호스트 애플리케이션은 BOOTP 프로토콜에서 특정 IP 주소를 계속 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-179">The host application can still request specific IP addresses in the BOOTP protocol.</span></span> <span data-ttu-id="6c359-180">그러나 BOOTP가 때때로 사용되므로 DHCP 클라이언트는 호스트 운영 체제 로드를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-180">However, the DHCP Client does not support loading the host operating system as BOOTP is sometimes used to do.</span></span>

## <a name="dhcp-on-a-secondary-interface"></a><span data-ttu-id="6c359-181">보조 인터페이스의 DHCP</span><span class="sxs-lookup"><span data-stu-id="6c359-181">DHCP on a Secondary Interface</span></span>

<span data-ttu-id="6c359-182">NetX DHCP 클라이언트는 기본 인터페이스가 아닌 보조 인터페이스에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-182">The NetX DHCP Client can run on secondary interfaces rather than the default primary interface.</span></span>

<span data-ttu-id="6c359-183">보조 네트워크 인터페이스에서 NetX DHCP 클라이언트를 실행하려면 호스트 애플리케이션에서 *nx_dhcp_set_interface_index* API 서비스를 사용하여 DHCP 클라이언트의 인터페이스 인덱스를 보조 인터페이스로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-183">To run NetX DHCP Client on a secondary network interface, the host application must set the interface index of the DHCP Client to the secondary interface using the *nx_dhcp_set_interface_index* API service.</span></span> <span data-ttu-id="6c359-184">인터페이스는 *nx_ip_interface_attach* 서비스를 사용하여 기본 네트워크 인터페이스에 이미 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-184">The interface must already be attached to the primary network interface using the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="6c359-185">보조 인터페이스를 연결하는 방법에 대한 자세한 내용은 NetX 사용자 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c359-185">See the NetX User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="6c359-186">아래 그림 1.2는 호스트 애플리케이션이 보조 인터페이스에서 DHCP 서버에 연결하는 예제 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-186">Below in Figure 1.2 is an example system on which the host application connects to the DHCP server on its secondary interface.</span></span> <span data-ttu-id="6c359-187">줄 65에서 보조 인터페이스는 null IP 주소를 사용하여 IP 작업에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-187">On line 65, the secondary interface is attached to the IP task with a null IP address.</span></span> <span data-ttu-id="6c359-188">줄 104에서 DHCP 클라이언트 인스턴스가 만들어지면 후에 *nx_dhcp_set_interface_index* 를 호출하여 DHCP 클라이언트 인터페이스 인덱스가 1(예: 자체가 인덱스 0인 기본 인터페이스의 오프셋)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-188">On line 104, after the DHCP Client instance is created, the DHCP Client interface index is set to 1 (e.g. the offset from the primary interface which itself is index 0) by calling *nx_dhcp_set_interface_index*.</span></span> <span data-ttu-id="6c359-189">그러면 줄 108에서 DHCP 클라이언트를 시작할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-189">Then the DHCP Client is ready to be started in line 108.</span></span>

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
       0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  status = _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                            0xFFFFFF00UL, my_netx_driver);
                            
  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Set the DHCP client interface to the secondary interface. 
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

<span data-ttu-id="6c359-190">그림 1.2 멀티홈을 지원하는 NetX용 DHCP의 예</span><span class="sxs-lookup"><span data-stu-id="6c359-190">Figure 1.2 Example of DHCP for NetX with multihome support</span></span>

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a><span data-ttu-id="6c359-191">동시에 여러 인터페이스의 DHCP 클라이언트</span><span class="sxs-lookup"><span data-stu-id="6c359-191">DHCP Client on Multiple Interfaces Simultaneously</span></span>

<span data-ttu-id="6c359-192">여러 인터페이스에서 DHCP 클라이언트를 실행하려면 *nx_api.h* 의 NX_MAX_PHYSICAL_INTERFACES를 디바이스에 연결된 실제 인터페이스 수로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-192">To run DHCP Client on multiple interfaces, NX_MAX_PHYSICAL_INTERFACES in *nx_api.h* must be set to the number of physical interfaces connected to the device.</span></span> <span data-ttu-id="6c359-193">기본적으로 이 값은 1입니다(예: 기본 인터페이스).</span><span class="sxs-lookup"><span data-stu-id="6c359-193">By default, this value is 1 (e.g. the primary interface).</span></span> <span data-ttu-id="6c359-194">추가 인터페이스를 IP 인스턴스에 등록하려면 *nx_ip_interface_attach* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-194">To register an additional interface to the IP instance use the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="6c359-195">보조 인터페이스를 연결하는 방법에 대한 자세한 내용은 NetX 사용자 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c359-195">See the NetX User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="6c359-196">다음 단계는 *nx_dhcp.h* 의 NX_DHCP_CLIENT_MAX_RECORDS를 동시에 DHCP를 실행하는 데 필요한 최대 인터페이스 수로 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-196">The next step is to set the NX_DHCP_CLIENT_MAX_RECORDS in *nx_dhcp.h* to the maximum number of interfaces expected to run DHCP simultaneously.</span></span> <span data-ttu-id="6c359-197">NX_DHCP_CLIENT_MAX_RECORDS는 NX_MAX_PHYSICAL_INTERFACES와 같을 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-197">Note that NX_DHCP_CLIENT_MAX_RECORDS does not have to equal NX_MAX_PHYSICAL_INTERFACES.</span></span> <span data-ttu-id="6c359-198">예를 들어 NX_MAX_PHYSICAL_INTERFACES는 3이고, NX_DHCP_CLIENT_MAX_RECORDS는 2일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-198">For example, NX_MAX_PHYSICAL_INTERFACES can be 3 and NX_DHCP_CLIENT_MAX_RECORDS equal to 2.</span></span> <span data-ttu-id="6c359-199">이 구성에서는 세 개의 실제 인터페이스 중 두 개의 인터페이스(그리고 언제든지 세 개의 물리적 인터페이스 중 두 개가 될 수 있음)만 DHCP를 한 번에 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-199">In this configuration, only two interfaces (and they can be any two of the three physical interfaces at any time) of the three physical interfaces can run DHCP at any one time.</span></span> <span data-ttu-id="6c359-200">DHCP 클라이언트 레코드에는 네트워크 인터페이스에 대한 일대일 매핑이 없습니다. 예를 들어 클라이언트 레코드 1은 실제 인터페이스 인덱스 1과 자동으로 상호 연결되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-200">DHCP Client Records do not have a one to one mapping to network interfaces e.g. Client Record 1 does not automatically correlate to physical interface index 1.</span></span>

<span data-ttu-id="6c359-201">NX_DHCP_CLIENT_MAX_RECORDS를 NX_MAX_PHYSICAL_INTERFACES보다 더 크게 설정할 수도 있지만, 이렇게 하면 사용되지 않는 클라이언트 레코드를 만들고 메모리를 비효율적으로 사용하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-201">NX_DHCP_CLIENT_MAX_RECORDS can also be set to greater than NX_MAX_PHYSICAL_INTERFACES but this would create unused client records and be an inefficient use of memory.</span></span>

<span data-ttu-id="6c359-202">인터페이스에서 DHCP를 시작하려면 먼저 애플리케이션에서 *nx_dhcp_interface_enable* 을 호출하여 해당 인터페이스를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-202">Before it can start DHCP on any interface, the application must enable those interfaces by calling *nx_dhcp_interface_enable*.</span></span> <span data-ttu-id="6c359-203">예외는 *nx_dhcp_create* 호출에서 자동으로 사용하도록 설정되는 기본 인터페이스입니다. 이는 아래에서 설명하는 *nx_dhcp_interface_disable* 서비스를 사용하여 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-203">Note that the exception is the primary interface which is automatically enabled in the *nx_dhcp_create* call (and which can be disabled using the *nx_dhcp_interface_disable* service discussed below).</span></span>

<span data-ttu-id="6c359-204">언제든지 DHCP에 대해 인터페이스를 사용하지 않도록 설정하거나 DHCP를 실행하는 다른 인터페이스와 독립적으로 해당 인터페이스에서 DHCP를 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-204">At any time, an interface can be disabled for DHCP or DHCP can be stopped on that interface independently of other interfaces running DHCP.</span></span>

<span data-ttu-id="6c359-205">위에서 설명한 대로 특정 인터페이스를 DHCP에 사용하도록 설정하려면 *nx_dhcp_interface_enable* 서비스를 사용하고 입력 인수에서 실제 인터페이스 인덱스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-205">As mentioned above, to enable a specific interface for DHCP, use the *nx_dhcp_interface_enable* service and specify the physical interface index in the input argument.</span></span> <span data-ttu-id="6c359-206">인터페이스 인덱스 입력 인수가 NX_MAX_PHYSICAL_INTERFACES 인터페이스보다 작다는 유일한 제한을 사용하여 최대 NX_DHCP_CLIENT_MAX_RECORDS 인터페이스를 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-206">Up to NX_DHCP_CLIENT_MAX_RECORDS interfaces can be enabled with the only limitation that the interface index input argument be less than NX_MAX_PHYSICAL_INTERFACES.</span></span>

<span data-ttu-id="6c359-207">특정 인터페이스에서 DHCP를 시작하려면 *nx_dhcp_interface_start* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-207">To start DHCP on a specific interface, use the *nx_dhcp_interface_start* service.</span></span> <span data-ttu-id="6c359-208">사용하도록 설정된 모든 인터페이스에서 DHCP를 시작하려면 *nx_dhcp_start* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-208">To start DHCP on all enabled interfaces, use the *nx_dhcp_start* service.</span></span> <span data-ttu-id="6c359-209">(이미 DHCP를 시작한 인터페이스는 *nx_dhcp_start* 의 영향을 받지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="6c359-209">(Interfaces that have already started DHCP will not be affected by *nx_dhcp_start*.)</span></span>

<span data-ttu-id="6c359-210">인터페이스에서 DHCP를 중지하려면 *nx_dhcp_interface_stop* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-210">To stop DHCP on an interface, use the *nx_dhcp_interface_stop* service.</span></span> <span data-ttu-id="6c359-211">DHCP가 해당 인터페이스에서 이미 시작되어 있어야 합니다. 그러지 않으면 오류 상태가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-211">DHCP must already have started on that interface or an error status is returned.</span></span> <span data-ttu-id="6c359-212">사용하도록 설정된 모든 인터페이스에서 DHCP를 중지하려면 *nx_dhcp_stop* 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-212">To stop DHCP on all enabled interfaces, use the *nx_dhcp_stop* service.</span></span> <span data-ttu-id="6c359-213">DHCP는 언제든지 다른 인터페이스와 독립적으로 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-213">DHCP can be stopped independently of other interfaces at any time.</span></span>

<span data-ttu-id="6c359-214">대부분의 기존 DHCP 클라이언트 서비스에는 ‘interface’와 동일한 항목이 있습니다. 예를 들어 *nx_dhcp_interface_release* 는 *nx_dhcp_release* 와 동일한 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-214">Most of the existing DHCP Client services have an ‘interface’ equivalent e.g. *nx_dhcp_interface_release* is the interface specific equivalent of *nx_dhcp_release.*</span></span> <span data-ttu-id="6c359-215">DHCP 클라이언트가 단일 인터페이스에 대해 구성된 경우 동일한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-215">If DHCP Client is configured for a single interface, they perform the same action.</span></span>

<span data-ttu-id="6c359-216">일반적으로 인터페이스가 아닌 특정 DHCP 클라이언트 서비스는 모든 인터페이스에 적용되지만 전부는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-216">Note that non-interface specific DHCP Client services typically apply to all interfaces but not all.</span></span> <span data-ttu-id="6c359-217">후자의 경우 인터페이스가 아닌 특정 서비스가 인터페이스 레코드의 DHCP 클라이언트 목록을 검색할 때 찾은 첫 번째 DHCP 사용 인터페이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-217">In the latter case, the non-interface specific service applies to the first DHCP enabled interface found in searching the DHCP Client list of interface records.</span></span> <span data-ttu-id="6c359-218">DHCP에 대해 여러 인터페이스가 사용하도록 설정되는 경우 인터페이스가 아닌 특정 서비스에서 수행하는 방법은 3장의 **서비스 설명** 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c359-218">See **Description of Services** in Chapter Three for how a non-interface specific service performs when multiple interfaces are enabled for DHCP.</span></span>

<span data-ttu-id="6c359-219">아래 예제 시퀀스에서 IP 인스턴스는 두 개의 네트워크 인터페이스를 포함하고 먼저 보조 인터페이스에서 DHCP를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-219">In the example sequence below, the IP instance has two network interfaces and first runs DHCP on the secondary interface.</span></span> <span data-ttu-id="6c359-220">잠시 후 기본 인터페이스에서 DHCP를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-220">At some time later, it starts DHCP on the primary interface.</span></span> <span data-ttu-id="6c359-221">그런 다음, 기본 인터페이스에서 IP 주소를 해제하고, 기본 인터페이스에서 DHCP를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-221">Then it releases the IP address on the primary interface and restarts DHCP on the primary interface:</span></span>

```C
nx_dhcp_create(&my_dhcp_client);
/* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); 
/* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); 
/* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); 

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is restarted on primary interface. */
```

<span data-ttu-id="6c359-222">인터페이스 관련 서비스의 전체 목록은 3장의 **서비스 설명** 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c359-222">For a complete list of interface specific services see **Description of Services** in Chapter Three.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="6c359-223">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="6c359-223">Configuration Options</span></span>

<span data-ttu-id="6c359-224">*nx_dhcp.h* 의 사용자 구성 가능한 DHCP 옵션을 사용하면 호스트 애플리케이션에서 특정 요구 사항에 맞게 DHCP 클라이언트를 미세 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-224">User configurable DHCP options in *nx_dhcp.h* allow the host application to fine tune DHCP Client for its particular requirements.</span></span> <span data-ttu-id="6c359-225">해당 매개 변수의 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-225">The following is a list of these parameters:</span></span>  
  
- <span data-ttu-id="6c359-226">**NX_DHCP_ENABLE_BOOTP**: 정의되면 이 옵션을 통해 DHCP 대신 BOOTP 프로토콜을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-226">**NX_DHCP_ENABLE_BOOTP** Defined, this option enables the BOOTP protocol instead of DHCP.</span></span> <span data-ttu-id="6c359-227">이 옵션은 기본적으로 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-227">By default this option is disabled.</span></span>

- <span data-ttu-id="6c359-228">**NX_DHCP_CLIENT_RESTORE_STATE**: 정의되면 DHCP 클라이언트에서 임대에 남아 있는 시간을 포함하여 현재 DHCP 클라이언트 라이선스 ‘상태’를 저장하고 DHCP 클라이언트 애플리케이션 다시 부팅 간에 이 상태를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-228">**NX_DHCP_CLIENT_RESTORE_STATE** If defined, this enables the DHCP Client to save its current DHCP Client license ‘state’ including time remaining on the lease, and restore this state between DHCP Client application reboots.</span></span> <span data-ttu-id="6c359-229">기본값은 사용 안 함입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-229">The default value is disabled.</span></span>

- <span data-ttu-id="6c359-230">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL**: 설정되면 DHCP 클라이언트에서 자체 패킷 풀을 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-230">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** If set, the DHCP Client will not create its own packet pool.</span></span> <span data-ttu-id="6c359-231">호스트 애플리케이션에서 nx_dhcp_packet_pool_set 서비스를 사용하여 DHCP 클라이언트 패킷 풀을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-231">The host application must use the nx_dhcp_packet_pool_set service to set the DHCP Client packet pool.</span></span> <span data-ttu-id="6c359-232">기본값은 사용 안 함입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-232">The default value is disabled.</span></span>

- <span data-ttu-id="6c359-233">**NX_DHCP_CLIENT_SEND_ARP_PROBE**: 정의되면 IP 주소 할당 후 DHCP 클라이언트에서 ARP 프로브를 보내 할당된 DHCP 주소를 다른 호스트에서 소유하고 있지 않은지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-233">**NX_DHCP_CLIENT_SEND_ARP_PROBE** Defined, this enables the DHCP Client to send an ARP probe after IP address assignment to verify the assigned DHCP address is not owned by another host.</span></span> <span data-ttu-id="6c359-234">이 옵션은 기본적으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-234">By default, this option is disabled.</span></span>

- <span data-ttu-id="6c359-235">**NX_DHCP_ARP_PROBE_WAIT**: ARP 프로브를 보낸 후 DHCP 클라이언트에서 응답을 기다리는 기간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-235">**NX_DHCP_ARP_PROBE_WAIT** Defines the length of time the DHCP Client waits for a response after sending an ARP probe.</span></span> <span data-ttu-id="6c359-236">기본값은 1초입니다(1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="6c359-236">The default value is one second (1 \* NX_IP_PERIODIC_RATE)</span></span>

- <span data-ttu-id="6c359-237">**NX_DHCP_ARP_PROBE_MIN**: ARP 프로브 전송 간격의 최소 변동을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-237">**NX_DHCP_ARP_PROBE_MIN** Defines the minimum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="6c359-238">기본값은 1초입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-238">The value is defaulted to 1 second.</span></span>

- <span data-ttu-id="6c359-239">**NX_DHCP_ARP_PROBE_MAX**: ARP 프로브 전송 간격의 최대 변동을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-239">**NX_DHCP_ARP_PROBE_MAX** Defines the maximum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="6c359-240">기본값은 2초입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-240">The value is defaulted to 2 seconds.</span></span>

- <span data-ttu-id="6c359-241">**NX_DHCP_ARP_PROBE_NUM**: DHCP 서버에서 할당한 IP 주소를 이미 사용하고 있는지 확인하기 위해 보내는 ARP 프로브 수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-241">**NX_DHCP_ARP_PROBE_NUM** Defines the number of ARP probes sent for determining if the IP address assigned by the DHCP server is already in use.</span></span> <span data-ttu-id="6c359-242">기본값은 3개 프로브입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-242">The value is defaulted to 3 probes.</span></span>

- <span data-ttu-id="6c359-243">**NX_DHCP_RESTART_WAIT**: DHCP 클라이언트에 할당된 IP 주소를 이미 사용하고 있는 경우 DHCP 클라이언트에서 DHCP를 다시 시작하기 위해 기다리는 시간을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-243">**NX_DHCP_RESTART_WAIT** Defines the length of time the DHCP Client waits to restart DHCP if the IP address assigned to the DHCP Client is already in use.</span></span> <span data-ttu-id="6c359-244">기본값은 10초입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-244">The value is defaulted to 10 seconds.</span></span>

- <span data-ttu-id="6c359-245">**NX_DHCP_CLIENT_MAX_RECORDS**: DHCP 클라이언트 인스턴스에 저장하는 최대 인터페이스 레코드 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-245">**NX_DHCP_CLIENT_MAX_RECORDS** Specifies the maximum number of interface records to save to the DHCP Client instance.</span></span> <span data-ttu-id="6c359-246">DHCP 클라이언트 인터페이스 레코드는 특정 인터페이스에서 실행되는 DHCP 클라이언트의 레코드입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-246">A DHCP Client interface record is a record of the DHCP Client running on a specific interface.</span></span> <span data-ttu-id="6c359-247">기본값은 실제 인터페이스 수(NX_MAX_PHYSICAL_INTERFACES)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-247">The default value is set as physical interfaces count(NX_MAX_PHYSICAL_INTERFACES).</span></span>

- <span data-ttu-id="6c359-248">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION**: 정의되면 DHCP 클라이언트에서 최대 DHCP 메시지 크기 옵션을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-248">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Defined, this enables the DHCP Client to send maximum DHCP message size option.</span></span> <span data-ttu-id="6c359-249">이 옵션은 기본적으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-249">By default, this option is disabled.</span></span>

- <span data-ttu-id="6c359-250">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK**: 정의되면 DHCP 클라이언트에서 nx_dhcp_create 호출의 입력 호스트 이름에 잘못된 문자 또는 길이가 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-250">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Defined, this enables the DHCP Client to check the input host name in the nx_dhcp_create call for invalid characters or length.</span></span> <span data-ttu-id="6c359-251">이 옵션은 기본적으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-251">By default, this option is disabled.</span></span>

- <span data-ttu-id="6c359-252">**NX_DHCP_THREAD_PRIORITY**: DHCP 스레드의 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-252">**NX_DHCP_THREAD_PRIORITY** Priority of the DHCP thread.</span></span> <span data-ttu-id="6c359-253">기본적으로 이 값은 DHCP 스레드가 우선 순위 3에서 실행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-253">By default, this value specifies that the DHCP thread runs at priority 3.</span></span>

- <span data-ttu-id="6c359-254">**NX_DHCP_THREAD_STACK_SIZE**: DHCP 스레드 스택의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-254">**NX_DHCP_THREAD_STACK_SIZE** Size of the DHCP thread stack.</span></span> <span data-ttu-id="6c359-255">기본값은 2,048바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-255">By default, the size is 2048 bytes.</span></span>

- <span data-ttu-id="6c359-256">**NX_DHCP_TIME_INTERVAL**: DHCP 클라이언트 타이머 만료 함수가 실행되는 간격(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-256">**NX_DHCP_TIME_INTERVAL** Interval in seconds when the DHCP Client timer expiration function executes.</span></span> <span data-ttu-id="6c359-257">이 함수는 DHCP 프로세스의 모든 간 제한을 업데이트합니다(예: 메시지를 다시 전송해야 하거나 DHCP 클라이언트 상태를 변경해야 하는 경우).</span><span class="sxs-lookup"><span data-stu-id="6c359-257">This function updates all the timeouts in the DHCP process e.g. if messages should be retransmitted or DHCP Client state changed.</span></span> <span data-ttu-id="6c359-258">기본값은 1초입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-258">By default, this value is 1 second.</span></span>

- <span data-ttu-id="6c359-259">**NX_DHCP_OPTIONS_BUFFER_SIZE**: DHCP 옵션 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-259">**NX_DHCP_OPTIONS_BUFFER_SIZE** Size of DHCP options buffer.</span></span> <span data-ttu-id="6c359-260">기본적으로 이 값은 312입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-260">By default, this value is 312.</span></span>

- <span data-ttu-id="6c359-261">**NX_DHCP_PACKET_PAYLOAD**: DHCP 클라이언트 패킷 페이로드의 크기(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-261">**NX_DHCP_PACKET_PAYLOAD** Specifies the size in bytes of the DHCP Client packet payload.</span></span> <span data-ttu-id="6c359-262">기본값은 NX_DHCP_MINIMUM_IP_DATAGRAM + 실제 헤더 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-262">The default value is NX_DHCP_MINIMUM_IP_DATAGRAM + physical header size.</span></span> <span data-ttu-id="6c359-263">유선 네트워크의 실제 헤더 크기는 일반적으로 이더넷 프레임 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-263">The physical header size in a wireline network is usually the Ethernet frame size.</span></span>

- <span data-ttu-id="6c359-264">**NX_DHCP_PACKET_POOL_SIZE**: DHCP 클라이언트 패킷 풀의 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-264">**NX_DHCP_PACKET_POOL_SIZE** Specifies the size of the DHCP Client packet pool.</span></span> <span data-ttu-id="6c359-265">기본값은 (5 \* NX_DHCP_PACKET_PAYLOAD)이며, 4개의 패킷과 내부 패킷 풀 오버헤드를 위한 공간을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-265">The default value is (5 \*NX_DHCP_PACKET_PAYLOAD) which will provide four packets plus room for internal packet pool overhead.</span></span>

- <span data-ttu-id="6c359-266">**NX_DHCP_MIN_RETRANS_TIMEOUT**: 메시지를 다시 전송하기 전에 클라이언트 메시지에 대한 DHCP 서버 회신을 받기 위한 최소 대기 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-266">**NX_DHCP_MIN_RETRANS_TIMEOUT** Specifies the minimum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="6c359-267">기본값은 4초(RFC 2131 권장)입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-267">The default value is the RFC 2131 recommended 4 seconds.</span></span>

- <span data-ttu-id="6c359-268">**NX_DHCP_MAX_RETRANS_TIMEOUT**: 메시지를 다시 전송하기 전에 클라이언트 메시지에 대한 DHCP 서버 회신을 받기 위한 최대 대기 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-268">**NX_DHCP_MAX_RETRANS_TIMEOUT** Specifies the maximum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="6c359-269">기본값은 64초(RFC 2131 권장)입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-269">The default value is the RFC 2131 recommended 64 seconds.</span></span>

- <span data-ttu-id="6c359-270">**NX_DHCP_MIN_RENEW_TIMEOUT**: DHCP 클라이언트가 IP 주소에 바인딩된 후 DHCP 서버 메시지를 받고 갱신 요청을 보내기 위한 최소 대기 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-270">**NX_DHCP_MIN_RENEW_TIMEOUT** Specifies minimum wait option for receiving a DHCP Server message and sending a renewal request after the DHCP Client is bound to an IP address.</span></span> <span data-ttu-id="6c359-271">기본값은 60초입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-271">The default value is 60 seconds.</span></span> <span data-ttu-id="6c359-272">그러나 DHCP 클라이언트는 최소 갱신 시간 제한을 기본값으로 설정하기 전에 DHCP 서버 메시지의 갱신과 리바인딩 만료 시간을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-272">However, the DHCP Client uses the Renew and Rebind expiration times from the DHCP server message before defaulting to the minimum renew timeout.</span></span>

- <span data-ttu-id="6c359-273">**NX_DHCP_TYPE_OF_SERVICE**: DHCP UDP 요청에 필요한 서비스 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-273">**NX_DHCP_TYPE_OF_SERVICE** Type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="6c359-274">기본적으로 이 값은 NX_IP_NORMAL로 정의되어 정상적인 IP 패킷 서비스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-274">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>

- <span data-ttu-id="6c359-275">**NX_DHCP_FRAGMENT_OPTION**: DHCP UDP 요청에 대한 조각을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-275">**NX_DHCP_FRAGMENT_OPTION** Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="6c359-276">기본적으로 이 값은 DHCP UDP 조각화를 사용하지 않도록 설정하는 NX_DONT_FRAGMENT입니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-276">By default, this value is NX_DONT_FRAGMENT to disable DHCP UDP fragmenting.</span></span>

- <span data-ttu-id="6c359-277">**NX_DHCP_TIME_TO_LIVE**: 이 패킷이 삭제되기 전에 통과할 수 있는 라우터 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-277">**NX_DHCP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="6c359-278">기본값은 0x80으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-278">The default value is set to 0x80.</span></span>

- <span data-ttu-id="6c359-279">**NX_DHCP_QUEUE_DEPTH**: 수신 큐의 최대 깊이 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-279">**NX_DHCP_QUEUE_DEPTH** Specifies the number of maximum depth of receive queue.</span></span> <span data-ttu-id="6c359-280">기본값은 4로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c359-280">The default value is set to 4.</span></span>
