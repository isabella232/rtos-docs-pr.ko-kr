---
title: 챕터 2 - Azure RTOS NetX Duo BSD 설치 및 사용
description: 이 챕터에서는 Azure RTOS NetX Duo BSD 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 582661bc66c51341fc098de9ff7b6fa2a7d746de
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810969"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="48834-103">챕터 2 - Azure RTOS NetX Duo BSD 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="48834-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="48834-104">이 챕터에서는 Azure RTOS NetX Duo BSD 구성 요소의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo BSD component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="48834-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="48834-105">Product Distribution</span></span>

<span data-ttu-id="48834-106">Azure RTOS NetX Duo BSD는 [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/)에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-106">Azure RTOS NetX Duo BSD can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="48834-107">이 패키지에는 다음과 같이 두 개의 원본 파일과 이 문서가 포함된 PDF 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="48834-108">**nxd_bsd.h**: NetX Duo BSD용 헤더 파일</span><span class="sxs-lookup"><span data-stu-id="48834-108">**nxd_bsd.h**: Header file for NetX Duo BSD</span></span>
- <span data-ttu-id="48834-109">**nxd_bsd.c**: NetX Duo BSD용 C 원본 파일</span><span class="sxs-lookup"><span data-stu-id="48834-109">**nxd_bsd.c**: C Source file for NetX Duo BSD</span></span>
- <span data-ttu-id="48834-110">**nxd_bsd.pdf**: NetX Duo BSD 사용자 가이드</span><span class="sxs-lookup"><span data-stu-id="48834-110">**nxd_bsd.pdf**: User Guide for NetX Duo BSD</span></span>

<span data-ttu-id="48834-111">데모 파일:</span><span class="sxs-lookup"><span data-stu-id="48834-111">Demo files:</span></span>

- <span data-ttu-id="48834-112">**bsd_demo_udp.c**</span><span class="sxs-lookup"><span data-stu-id="48834-112">**bsd_demo_udp.c**</span></span>
- <span data-ttu-id="48834-113">**bsd_demo_tcp.c**</span><span class="sxs-lookup"><span data-stu-id="48834-113">**bsd_demo_tcp.c**</span></span>
- <span data-ttu-id="48834-114">**bsd_demo_raw.c**</span><span class="sxs-lookup"><span data-stu-id="48834-114">**bsd_demo_raw.c**</span></span>

## <a name="netx-duo-bsd-installation"></a><span data-ttu-id="48834-115">NetX Duo BSD 설치</span><span class="sxs-lookup"><span data-stu-id="48834-115">NetX Duo BSD Installation</span></span>

<span data-ttu-id="48834-116">NetX Duo BSD를 사용하려면 이전에 언급한 전체 배포판을 NetX Duo가 설치된 동일한 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-116">In order to use NetX Duo BSD the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="48834-117">예를 들어 NetX Duo가 " *\threadx\arm7\green*" 디렉터리에 설치된 경우 *nxd_bsd.h* 및 *nxd_bsd.c* 파일을 이 디렉터리에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-117">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_bsd.h* and *nxd_bsd.c* files should be copied into this directory.</span></span>

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a><span data-ttu-id="48834-118">BSD 애플리케이션의 ThreadX 및 NetX Duo 구성 요소 빌드</span><span class="sxs-lookup"><span data-stu-id="48834-118">Building the ThreadX and NetX Duo components of a BSD Application</span></span>

### <a name="threadx"></a><span data-ttu-id="48834-119">ThreadX</span><span class="sxs-lookup"><span data-stu-id="48834-119">ThreadX</span></span>

<span data-ttu-id="48834-120">ThreadX 라이브러리는 `bsd_errno`를 스레드 로컬 스토리지에 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-120">The ThreadX library must define `bsd_errno` in the thread local storage.</span></span> <span data-ttu-id="48834-121">다음 절차를 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-121">We recommend the following procedure:</span></span>

1. <span data-ttu-id="48834-122">*tx_port.h* 에서 TX_THREAD_EXTENSION 매크로 중 하나를 다음과 같이 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-122">In *tx_port.h*, set one of the TX_THREAD_EXTENSION macros as follows:</span></span>
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. <span data-ttu-id="48834-123">ThreadX 라이브러리를 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-123">Rebuild the ThreadX library.</span></span>

> [!NOTE]
> <span data-ttu-id="48834-124">TX_THREAD_EXTENSION_3이 이미 사용되는 경우 사용자는 다른 TX_THREAD_EXTENSION 매크로 중 하나를 자유롭게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-124">If TX_THREAD_EXTENSION_3 is already used, the user is free to use one of the other TX_THREAD_EXTENSION macros.</span></span>

### <a name="netx-duo"></a><span data-ttu-id="48834-125">NetX Duo</span><span class="sxs-lookup"><span data-stu-id="48834-125">NetX Duo</span></span>

<span data-ttu-id="48834-126">NetX Duo BSD 서비스를 사용하기 전에 NX_ENABLE_EXTENDED_NOTIFY_SUPPORT가 정의된 NetX Duo 라이브러리를 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-126">Before using NetX Duo BSD Services, the NetX Duo library must be built with NX_ENABLE_EXTENDED_NOTIFY_SUPPORT defined.</span></span> <span data-ttu-id="48834-127">기본적으로 정의되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-127">By default it is not defined.</span></span> <span data-ttu-id="48834-128">BSD 원시 소켓을 사용하려면 정의된 NX_ENABLE_IP_RAW_PACKET_FILTER가 정의된 NetX Duo 라이브러리를 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-128">If the BSD raw sockets are to be used, the NetX Duo library must be built with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span>

## <a name="using-netx-duo-bsd"></a><span data-ttu-id="48834-129">NetX Duo BSD 사용</span><span class="sxs-lookup"><span data-stu-id="48834-129">Using NetX Duo BSD</span></span>

<span data-ttu-id="48834-130">NetX Duo BSD 애플리케이션 프로젝트는 이 가이드의 뒷부분에 지정된 BSD 서비스를 사용할 수 있도록 *tx_api.h* 및 *nx_api.h* 를 포함한 후에 *nxd_bsd.h* 를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-130">A NetX Duo BSD application project must include *nxd_bsd.h* after it includes *tx_api.h* and *nx_api.h* to be able to use BSD services specified later in this guide.</span></span> <span data-ttu-id="48834-131">애플리케이션에서도 *nxd_bsd.c* 를 빌드 프로세스에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-131">The application must also include *nxd_bsd.c* in the build process.</span></span> <span data-ttu-id="48834-132">이 파일은 다른 애플리케이션 파일과 동일한 방식으로 컴파일해야 하며, 해당 개체 형식은 애플리케이션의 파일과 함께 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-132">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="48834-133">이것이 NetX BSD를 사용하는 데 필요한 모든 것입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-133">This is all that is required to use NetX Duo BSD.</span></span>

<span data-ttu-id="48834-134">NetX Duo BSD 서비스를 활용하려면 애플리케이션에서 IP 인스턴스를 만들고, BSD 계층에 대해 패킷을 할당할 패킷 풀을 만들고, 내부 BSD 스레드 스택에 대한 메모리 공간을 할당하고, 내부 BSD 스레드의 우선 순위를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-134">To utilize NetX Duo BSD services, the application must create an IP instance, create a packet pool for the BSD layer to allocate packets from, allocate memory space for the internal BSD thread stack, and specify the priority of the internal BSD thread.</span></span> <span data-ttu-id="48834-135">BSD 계층은 *bsd_initialize* 를 호출하고 매개 변수를 전달하여 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-135">The BSD layer is initialized by calling *bsd_initialize* and passing in the parameters.</span></span> <span data-ttu-id="48834-136">이는 이 문서의 뒷부분에 있는 "간단한 예제"에서 설명되지만 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-136">This is demonstrated in the "Small Examples" later in this document but the prototype is shown below:</span></span>

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

<span data-ttu-id="48834-137">default_ip는 BSD 계층이 작동하는 IP 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-137">The default_ip is the IP instance the BSD layer operates on.</span></span> <span data-ttu-id="48834-138">default_pool은 BSD 서비스에서 패킷을 할당하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-138">The default_pool is used by the BSD services to allocate packets from.</span></span> <span data-ttu-id="48834-139">bsd_thread_stack_area 및 bsd_thread_stack_size의 두 매개 변수는 내부 BSD 스레드에서 사용하는 스택 영역을 정의하고, 마지막 bsd_thread_priority 매개 변수는 스레드의 우선 순위를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-139">The next two parameters: bsd_thread_stack_area, bsd_thread_stack_size defines the stack area used by the internal BSD thread, and the last parameter, bsd_thread_priority, sets the priority of the thread.</span></span>

## <a name="netx-duo-bsd-raw-socket-support"></a><span data-ttu-id="48834-140">NetX Duo BSD 원시 소켓 지원</span><span class="sxs-lookup"><span data-stu-id="48834-140">NetX Duo BSD Raw Socket Support</span></span>

<span data-ttu-id="48834-141">NetX Duo BSD는 원시 소켓도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-141">NetX Duo BSD also supports raw sockets.</span></span> <span data-ttu-id="48834-142">NetX Duo BSD에서 원시 소켓을 사용하려면 NX_ENABLE_IP_RAW_PACKET_FILTER가 정의된 NetX Duo 라이브러리를 컴파일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-142">To use raw sockets in NetX Duo BSD, the NetX Duo library must be compiled with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span> <span data-ttu-id="48834-143">기본적으로 정의되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-143">By default it is not defined.</span></span> <span data-ttu-id="48834-144">그런 다음, 애플리케이션에서 *nx_ip_raw_packet_enable* 을 호출하여 원시 소켓 처리를 이전에 만든 IP 인스턴스에 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-144">The application must then enable raw socket processing for a previously created IP instance by calling *nx_ip_raw_packet_enable.*</span></span>

<span data-ttu-id="48834-145">NetX Duo BSD에서 원시 소켓을 만들기 위해 애플리케이션에서 소켓 만들기 서비스인 *socket* 을 사용하고 프로토콜 패밀리, 소켓 유형 및 프로토콜을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-145">To create a raw socket in NetX Duo BSD, the application uses the socket create service *socket* and specifies the protocol family, socket type and protocol:</span></span>

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

<span data-ttu-id="48834-146">protocolFamily는 IPv4 소켓의 경우 AF_INET이고, IPv6 소켓의 경우 AF_INET6입니다(IP 인스턴스에서 IPv6가 사용하도록 설정되어 있다고 가정).</span><span class="sxs-lookup"><span data-stu-id="48834-146">protocolFamily is AF_INET for IPv4 sockets, or AF_INET6 for IPv6 sockets, assuming IPv6 is enabled on the IP instance.</span></span> <span data-ttu-id="48834-147">socket_type은 SOCK_RAW로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-147">The socket_type must be set to SOCK_RAW.</span></span> <span data-ttu-id="48834-148">protocol은 애플리케이션에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="48834-148">protocol is application specific.</span></span>

<span data-ttu-id="48834-149">원시 패킷을 보내고 받고 원시 소켓을 닫기 위해 애플리케이션에서 일반적으로 UDP와 동일한 BSD 서비스(예: *sendto, recvfrom, select* 및 *soc_close*)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-149">To send and receive raw packets as well as close a raw socket, the application typically uses the same BSD services as for UDP e.g. *sendto, recvfrom, select* and *soc_close*.</span></span> <span data-ttu-id="48834-150">원시 소켓은 *accept* 또는 *listen* BSD 서비스를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-150">Raw sockets do not support either *accept* or *listen* BSD services.</span></span>

- <span data-ttu-id="48834-151">기본적으로 수신된 IPv4 원시 데이터에는 IPv4 헤더가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-151">By default, received IPv4 raw data includes the IPv4 header.</span></span>  <span data-ttu-id="48834-152">이와 반대로, 수신된 IPv6 원시 데이터에는 IPv6 헤더가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-152">Conversely, received IPv6 raw data does not include the IPv6 header.</span></span>

- <span data-ttu-id="48834-153">기본적으로 원시 IPv6 또는 IPv4 패킷을 보낼 때 BSD 래퍼 계층은 데이터를 보내기 전에 IPv6 또는 IPv4 헤더를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-153">By default, when sending either raw IPv6 or IPv4 packets, the BSD wrapper layer adds the IPv6 or IPv4 header before sending the data.</span></span>

<span data-ttu-id="48834-154">NetX Duo BSD는 IP_RAW_RX_NO_HEADER, IP_HDRINCL 및 IP_RAW_IPV6_HDRINCL을 포함하여 추가 원시 소켓 옵션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-154">NetX Duo BSD supports additional raw socket options, including IP_RAW_RX_NO_HEADER, IP_HDRINCL and IP_RAW_IPV6_HDRINCL.</span></span>

<span data-ttu-id="48834-155">IP_RAW_RX_NO_HEADER를 설정하면 수신된 데이터와 보고된 메시지 길이에 IPv4 헤더가 포함되지 않도록 IPv4 헤더가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-155">If IP_RAW_RX_NO_HEADER is set, the IPv4 header is removed so that the received data does not contain the IPv4 header, and the reported message length does not include the IPv4 header.</span></span>  <span data-ttu-id="48834-156">IPv6 소켓의 경우 기본적으로 원시 소켓 수신에는 IPv6 헤더가 포함되지 않으며, 이는 IP_RAW_RX_NO_HEADER 옵션이 설정된 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-156">For IPv6 sockets, by default the raw socket receive does not include IPv6 header, equivalent to having the IP_RAW_RX_NO_HEADER option set.</span></span> <span data-ttu-id="48834-157">애플리케이션에서 *setsockopt* 서비스를 사용하여 IP_RAW_RX_NO_HEADER 옵션을 지울 수 있습니다. IP_RAW_RX_NO_HEADER 옵션을 지우면 수신된 IPv6 원시 데이터와 보고된 메시지 길이에 IPv6 헤더가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-157">Application may use the *setsockopt* service to clear the IP_RAW_RX_NO_HEADER option, Once the IP_RAW_RX_NO_HEADER option is cleared, the received IPv6 raw data would include the IPv6 header, and the reported message length includes the IPv6 header.</span></span>

<span data-ttu-id="48834-158">이 옵션은 IPv4 또는 IPv6 전송 데이터에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-158">This option has no effect on IPv4 or IPv6 transmitted data.</span></span>

<span data-ttu-id="48834-159">IP_HDRINCL을 설정하면 데이터를 보낼 때 IPv4 헤더가 애플리케이션에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-159">If IP_HDRINCL is set, the application includes the IPv4 header when sending data.</span></span>  <span data-ttu-id="48834-160">이 옵션은 IPv6 전송에는 영향을 주지 않으며 기본적으로 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-160">This option has no effect on IPv6 transmission and is not defined by default.</span></span> <span data-ttu-id="48834-161">IP_RAW_IPV6_HDRINCL을 설정하면 데이터를 보낼 때 IPv6 헤더가 애플리케이션에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-161">If IP_RAW_IPV6_HDRINCL is set, the application includes the IPv6 header when sending data.</span></span>  <span data-ttu-id="48834-162">이 옵션은 IPv4 전송에는 영향을 주지 않으며 기본적으로 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-162">This option has no effect on IPv4 transmission and is not defined by default.</span></span>

<span data-ttu-id="48834-163">IP_HDRINCL 및 IP_RAW_IPV6_HDRINCL은 IPv4 또는 IPv6 수신에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-163">IP_HDRINCL and IP_RAW_IPV6_HDRINCL have no effect on IPv4 or IPv6 reception.</span></span>

> [!NOTE]
> <span data-ttu-id="48834-164">BSD 4.3 소켓 사양은 커널이 원시 패킷을 각 소켓 수신 버퍼에 복사해야 한다고 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-164">The BSD 4.3 Socket specification specifies that the kernel must copy the raw packet to each socket receive buffer.</span></span> <span data-ttu-id="48834-165">그러나 NetX Duo BSD에서 동일한 프로토콜을 공유하는 여러 소켓이 만들어지면 동작이 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-165">However in NetX Duo BSD, if multiple sockets are created sharing the same protocol, the behavior is undefined.</span></span>

## <a name="netx-duo-bsd-raw-packet-support"></a><span data-ttu-id="48834-166">NetX Duo BSD 원시 패킷 지원</span><span class="sxs-lookup"><span data-stu-id="48834-166">NetX Duo BSD Raw Packet Support</span></span>

<span data-ttu-id="48834-167">PPPoE에 대한 원시 패킷 지원을 사용하도록 설정하려면 NX_BSD_RAW_PPPOE_SUPPORT가 사용하도록 설정된 NetX Duo BSD 래퍼를 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-167">To enable the raw packet support for PPPoE, NetX Duo BSD wrapper needs to be built with NX_BSD_RAW_PPPOE_SUPPORT enabled.</span></span>

<span data-ttu-id="48834-168">다음 명령에서는 PPPoE 원시 패킷을 처리하는 BSD 소켓을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="48834-168">The following command creates a BSD socket to handle PPPoE raw packets:</span></span>

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

<span data-ttu-id="48834-169">현재 BSD 구현은 AF_PACKET 패밀리에서 두 가지 프로토콜 유형만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-169">The current BSD implementation only supports two protocol types in AF_PACKET family</span></span>

- <span data-ttu-id="48834-170">`ETHERTYPE_PPPOE_DISC`: PPPoE 검색 패킷.</span><span class="sxs-lookup"><span data-stu-id="48834-170">`ETHERTYPE_PPPOE_DISC`: PPPoE Discovery packets.</span></span> <span data-ttu-id="48834-171">MAC 데이터 프레임에서 검색 패킷의 이더넷 프레임 유형은 0x8863입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-171">In the MAC data frame, the Discovery packets have the Ethernet frame type 0x8863.</span></span>

- <span data-ttu-id="48834-172">`ETHERTYPE_PPPOE_SESS`: PPP 세션 패킷.</span><span class="sxs-lookup"><span data-stu-id="48834-172">`ETHERTYPE_PPPOE_SESS`: PPP Session packets.</span></span> <span data-ttu-id="48834-173">MAC 데이터 프레임에서 세션 패킷의 이더넷 프레임 유형은 0x8864입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-173">In the MAC data frame, the Session packets have the Ethernet frame type 0x8864.</span></span>

<span data-ttu-id="48834-174">`sockaddr_ll` 구조체는 PPPoE 프레임을 보내거나 받을 때 매개 변수를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-174">The structure `sockaddr_ll` is used to specify parameters when sending or receiving PPPoE frames.</span></span>

<span data-ttu-id="48834-175">`struct sockaddr_ll`은 다음과 같이 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-175">`struct sockaddr_ll` is declared as:</span></span>

```c
struct sockaddr_ll
{
    USHORT  sll_family;     /* Must be AF_PACKET */
    USHORT  sll_protocol;   /* LL frame type */
    INT     sll_ifindex;    /* Interface Index. */
    USHORT  sll_hatype;     /* Header type */
    UCHAR   sll_pkttype;    /* Packet type */
    UCHAR   sll_halen;      /* Length of address */
    UCHAR   sll_addr[8];    /* Physical layer address */
};
```

> [!NOTE]
> <span data-ttu-id="48834-176">구조체의 모든 필드가 `sendto()` 또는 `recvfrom()`에서 사용되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="48834-176">Not every field in the structure is used by `sendto()` or `recvfrom()`.</span></span> <span data-ttu-id="48834-177">PPPoE 패킷을 보내고 받기 위해 `sockaddr_ll`을 설정하는 방법은 아래 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="48834-177">See the description below on how to set up the `sockaddr_ll` for sending and receiving PPPoE packets.</span></span>

<span data-ttu-id="48834-178">AF_PACKET 패밀리에서 만든 소켓은 지정된 프로토콜에 관계없이 PPPoE 검색 패킷 또는 PPP 세션 패킷을 보내는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-178">Socket created in the AF_PACKET family can be used to send either PPPoE Discovery packets or PPP session packets, regardless of the protocol specified.</span></span> <span data-ttu-id="48834-179">PPPoE 패킷을 전송할 때 애플리케이션은 MAC 헤더(대상 MAC 주소, 원본 MAC 주소 및 프레임 유형)를 포함하여 적절한 형식의 PPPoE 프레임을 포함하는 버퍼를 준비해야 합니다. 버퍼 크기에는 14바이트 이더넷 헤더가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-179">When transmitting a PPPoE packet, application must prepare the buffer that includes properly formatted PPPoE frame, including the MAC headers (Destination MAC address, source MAC address, and frame type.) The size of the buffer includes the 14-byte Ethernet header.</span></span>

<span data-ttu-id="48834-180">`sockaddr_ll` 구조체인 `sll_ifindex`는 이 패킷을 보내는 데 사용하는 실제 인터페이스를 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-180">The `sockaddr_ll` struct, the `sll_ifindex` is used to indicate the physical interface to be used for sending this packet.</span></span> <span data-ttu-id="48834-181">구조체의 나머지 필드는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-181">The rest of the fields in the structure are not used.</span></span> <span data-ttu-id="48834-182">사용되지 않은 필드로 설정된 값은 BSD 내부 프로세스에서 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-182">Values set to the unused fields are ignored by the BSD internal process.</span></span>

<span data-ttu-id="48834-183">다음 코드 블록에서는 PPPoE 패킷을 전송하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="48834-183">The following code block illustrates how to transmit a PPPoE packet:</span></span>

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

<span data-ttu-id="48834-184">반환 값은 전송된 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="48834-184">The return value indicates the number of bytes transmitted.</span></span> <span data-ttu-id="48834-185">PPPoE 패킷은 메시지 기반이므로 성공적으로 전송되면 전송된 바이트 수가 14바이트 이더넷 헤더를 포함하여 패킷 크기와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-185">Since PPPoE packets are message-based, on a successful transmission, the number of bytes sent matches the size of the packet, including the 14-byte Ethernet header.</span></span>

<span data-ttu-id="48834-186">PPPoE 패킷은 `recvfrom()`을 사용하여 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-186">PPPoE packets can be received using `recvfrom()`.</span></span> <span data-ttu-id="48834-187">수신 버퍼는 이더넷 MTU 크기의 메시지를 수용할 수 있을 만큼 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-187">The receive buffer must be big enough to accommodate message of Ethernet MTU size.</span></span> <span data-ttu-id="48834-188">수신된 PPPoE 패킷에는 14바이트 이더넷 헤더가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-188">The received PPPoE packet includes 14-byte Ethernet header.</span></span> <span data-ttu-id="48834-189">PPPoE 패킷을 받는 경우 PPPoE 검색 패킷은 `ETHERTYPE_PPPOE_DISC` 프로토콜을 사용하여 만든 소켓에서만 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-189">On receiving PPPoE packets, PPPoE Discovery packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_DISC`.</span></span> <span data-ttu-id="48834-190">마찬가지로 PPP 세션 패킷은 `ETHERTYPE_PPPOE_SESS` 프로토콜을 사용하여 만든 소켓에서만 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-190">Similarly, PPP session packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_SESS`.</span></span> <span data-ttu-id="48834-191">동일한 프로토콜 유형에 대해 여러 소켓이 만들어지면 도착하는 PPPoE 패킷이 먼저 만들어진 소켓으로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-191">If multiple sockets are created for the same protocol type, arriving PPPoE packets are forwarded to the socket created first.</span></span> <span data-ttu-id="48834-192">프로토콜에 대해 만든 첫 번째 소켓이 닫히면 만든 순서의 다음 소켓이 이러한 패킷을 받는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-192">If the first socket created for the protocol is closed, the next socket in the order of creation is used for receiving these packets.</span></span>

<span data-ttu-id="48834-193">PPPoE 패킷을 받으면 `sockaddr_ll` 구조체의 다음 필드가 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-193">After a PPPoE packet is received, the following fields in the `sockaddr_ll` struct are valid:</span></span>
- <span data-ttu-id="48834-194">**sll_family**: BSD 내부에서 AF_PACKET으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-194">**sll_family**: Set by the BSD internal to be AF_PACKET</span></span>
- <span data-ttu-id="48834-195">**sll_ifindex**: 패킷을 보낸 인터페이스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="48834-195">**sll_ifindex**: Indicates the interface from which the packet is received</span></span>
- <span data-ttu-id="48834-196">**sll_protocol**: 받은 패킷 형식(`ETHERTYPE_PPPOE_DISC` 또는 `ETHERTYPE_PPPOE_SESS`)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-196">**sll_protocol**: Set to the type of packet received: `ETHERTYPE_PPPOE_DISC` or `ETHERTYPE_PPPOE_SESS`</span></span>

## <a name="eliminating-internal-bsd-thread"></a><span data-ttu-id="48834-197">내부 BSD 스레드 제거</span><span class="sxs-lookup"><span data-stu-id="48834-197">Eliminating Internal BSD Thread</span></span>

<span data-ttu-id="48834-198">기본적으로 BSD는 내부 스레드를 활용하여 일부 처리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-198">By default, BSD utilizes an internal thread to perform some of its processing.</span></span> <span data-ttu-id="48834-199">메모리 제약 조건이 엄격한 시스템에서는 NX_BSD_TIMEOUT_PROCESS_IN_TIMER가 정의된 BSD를 빌드할 수 있습니다. 이는 내부 BSD 스레드를 제거하고 내부 타이머를 대신 사용하여 동일한 처리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-199">In systems with tight memory constraints, BSD can be built with NX_BSD_TIMEOUT_PROCESS_IN_TIMER defined, which eliminates the internal BSD thread and instead uses an internal timer to perform the same processing.</span></span> <span data-ttu-id="48834-200">이렇게 하면 내부 BSD 스레드 제어 블록 및 스택에 필요한 메모리가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-200">This eliminates the memory required for the internal BSD thread control block and stack.</span></span> <span data-ttu-id="48834-201">그러나 전체 타이머 처리가 크게 증가하고 BSD 처리가 필요한 것보다 더 높은 우선 순위로 실행될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-201">However, overall timer processing is significantly increased and the BSD processing may also execute at a higher priority than needed.</span></span>

<span data-ttu-id="48834-202">ThreadX 타이머 컨텍스트에서 실행되도록 BSD 소켓을 구성하려면 *nxd_bsd.h* 에서 NX_BSD_TIMEOUT_PROCESS_IN_TIMER를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-202">To configure BSD sockets to run in the ThreadX timer context, define NX_BSD_TIMEOUT_PROCESS_IN_TIMER in *nxd_bsd.h*.</span></span> <span data-ttu-id="48834-203">BSD 계층이 타이머 컨텍스트에서 BSD 작업을 실행하도록 구성된 경우 *bsd_initialize* 호출에서 다음 세 가지 매개 변수가 무시되며 NULL로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-203">If the BSD layer is configured to execute the BSD tasks in the timer context, in the call to *bsd_initialize*, the following three parameters are ignored, and should be set to NULL:</span></span>

- <span data-ttu-id="48834-204">**bsd_thread_stack_area**</span><span class="sxs-lookup"><span data-stu-id="48834-204">**bsd_thread_stack_area**</span></span>
- <span data-ttu-id="48834-205">**bsd_thread_stack_size**</span><span class="sxs-lookup"><span data-stu-id="48834-205">**bsd_thread_stack_size**</span></span>
- <span data-ttu-id="48834-206">**bsd_thread_priority**</span><span class="sxs-lookup"><span data-stu-id="48834-206">**bsd_thread_priority**</span></span>

## <a name="netx-duo-bsd-with-dns-support"></a><span data-ttu-id="48834-207">DNS를 지원하는 NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="48834-207">NetX Duo BSD with DNS Support</span></span>

<span data-ttu-id="48834-208">NX_BSD_ENABLE_DNS가 정의되면 NetX Duo BSD에서 DNS 쿼리를 보내 호스트 이름 또는 호스트 IP 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-208">If NX_BSD_ENABLE_DNS is defined, NetX Duo BSD can send DNS queries to obtain hostname or host IP information.</span></span> <span data-ttu-id="48834-209">이 기능을 사용하려면 이전에 *nx_dns_create* 서비스를 사용하여 만든 NetX DNS 클라이언트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-209">This feature requires a NetX DNS Client to be previously created using the *nx_dns_create* service.</span></span> <span data-ttu-id="48834-210">IPv4 서버 주소를 추가하기 위해 *nx_dns_server_add* 서비스를 사용하거나 IPv4 또는 IPv6 서버 주소를 추가하기 위해 *nxd_dns_server_add* 를 사용하여 하나 이상의 알려진 DNS 서버 IP 주소를 DNS 인스턴스에 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-210">One or more known DNS server IP addresses must be registered with the DNS instance using the *nx_dns_server_add* service for adding IPv4 server addresses, or using the *nxd_dns_server_add* service for adding either IPv4 or IPv6 server addresses.</span></span>

<span data-ttu-id="48834-211">DNS 서비스 및 메모리 할당은 *getaddrinfo* 및 *getnameinfo* 서비스에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-211">DNS services and memory allocation are used by *getaddrinfo* and *getnameinfo* services:</span></span>

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

<span data-ttu-id="48834-212">BSD 애플리케이션에서 호스트 이름을 사용하여 *getaddrinfo* 를 호출하면 NetX BSD는 아래 서비스 중 하나를 호출하여 IP 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="48834-212">When the BSD application calls *getaddrinfo* with a hostname, NetX BSD will call any of the below services to obtain the IP address:</span></span>

- <span data-ttu-id="48834-213">**nx_dns_ipv4_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="48834-213">**nx_dns_ipv4_address_by_name_get**</span></span>
- <span data-ttu-id="48834-214">**nxd_dns_ipv6_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="48834-214">**nxd_dns_ipv6_address_by_name_get**</span></span>
- <span data-ttu-id="48834-215">**nx_dns_cname_get**</span><span class="sxs-lookup"><span data-stu-id="48834-215">**nx_dns_cname_get**</span></span>

<span data-ttu-id="48834-216">*nx_dns_ipv4_address_by_name_get* 및 *nxd_dns_ipv6_address_by_name_get* 의 경우 NetX BSD는 각각 ipv4_addr_buffer 및 ipv6_addr_buffer 메모리 영역을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-216">For *nx_dns_ipv4_address_by_name_get* and *nxd_dns_ipv6_address_by_name_get*, NetX BSD uses the ipv4_addr_buffer and ipv6_addr_buffer memory areas respectively.</span></span> <span data-ttu-id="48834-217">이러한 버퍼의 크기는 각각 (NX_BSD_IPV4_ADDR_PER_HOST \* 4) 및 (NX_BSD_IPV6_ADDR_PER_HOST \* 16)으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-217">The size of these buffers are defined by (NX_BSD_IPV4_ADDR_PER_HOST \* 4) and (NX_BSD_IPV6_ADDR_PER_HOST \* 16) respectively.</span></span>

<span data-ttu-id="48834-218">*getaddrinfo* 에서 주소 정보를 반환하기 위해 NetX BSD는 nx_bsd_addrinfo_pool_memory ThreadX 블록 메모리 테이블을 사용합니다. 이 테이블의 메모리 영역은 구성 가능한 다른 옵션 세트인 NX_BSD_IPV4_ADDR_MAX_NUM 및 NX_BSD_IPV6_ADDR_MAX_NUM에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-218">For returning address information from *getaddrinfo*, NetX BSD uses the ThreadX block memory table nx_bsd_addrinfo_pool_memory, whose memory area is defined by another set of configurable options, NX_BSD_IPV4_ADDR_MAX_NUM and NX_BSD_IPV6_ADDR_MAX_NUM.</span></span>

<span data-ttu-id="48834-219">위의 구성 옵션에 대한 자세한 내용은 **일반 구성 옵션** 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="48834-219">See **General Configuration Options** for more details on the above configuration options.</span></span>

<span data-ttu-id="48834-220">또한 NX_DNS_ENABLE_EXTENDED_RR_TYPES가 정의되고 호스트 입력이 정식 이름인 경우 NetX Duo BSD는 이전에 만든 \`_nx_bsd_cname_block_pool 블록 풀에서 메모리를 동적으로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-220">Additionally, if NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, and the host input is a canonical name, NetX Duo BSD will allocate memory dynamically from a previously created block pool \`_nx_bsd_cname_block_pool</span></span>

> [!NOTE]
> <span data-ttu-id="48834-221">*getaddrinfo* 가 호출되면 BSD 애플리케이션에서 *freeaddrinfo* 서비스를 사용하여 res 인수에서 가리키는 메모리를 블록 테이블로 다시 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-221">After calling *getaddrinfo* the BSD application is responsible for releasing the memory pointed to by the res argument back to the block table using the *freeaddrinfo* service.</span></span>

## <a name="netx-duo-bsd-limitations"></a><span data-ttu-id="48834-222">NetX Duo BSD 제한 사항</span><span class="sxs-lookup"><span data-stu-id="48834-222">NetX Duo BSD Limitations</span></span>

<span data-ttu-id="48834-223">성능 및 아키텍처 문제로 인해 NetX Duo BSD는 모든 BSD 4.3 소켓 기능을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-223">Due to performance and architecture issues, NetX Duo BSD does not support all the BSD 4.3 socket features:</span></span>

<span data-ttu-id="48834-224">INT 플래그는 *send, recv, sendto* 및 *recvfrom* 호출에 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-224">INT flags are not supported for *send, recv, sendto* and *recvfrom* calls.</span></span>

## <a name="general-configuration-options"></a><span data-ttu-id="48834-225">일반 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="48834-225">General Configuration Options</span></span>

<span data-ttu-id="48834-226">*nxd_bsd.h* 의 사용자 구성 가능한 옵션을 사용하면 애플리케이션에서 특정 애플리케이션 요구 사항에 맞게 NetX Duo BSD 소켓을 미세 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-226">User configurable options in *nxd_bsd.h* allow the application to fine tune NetX Duo BSD sockets for its particular application requirements.</span></span>

<span data-ttu-id="48834-227">컴파일 시간에 설정되는 구성 가능한 옵션의 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-227">The following is the list of configurable options that are set at compile time:</span></span>

- <span data-ttu-id="48834-228">**NX_BSD_TCP_WINDOW**: TCP 소켓 만들기 호출에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-228">**NX_BSD_TCP_WINDOW**: Used in TCP socket create calls.</span></span> <span data-ttu-id="48834-229">64k는 100Mb 이더넷의 일반적인 창 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-229">64k is typical window size for 100Mb Ethernet.</span></span> <span data-ttu-id="48834-230">기본값은 65535입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-230">The default value is 65535.</span></span>

- <span data-ttu-id="48834-231">**NX_BSD_SOCKFD_START**: BSD 소켓 파일 설명자 시작 값에 대한 논리적 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-231">**NX_BSD_SOCKFD_START**: This is the logical index for the BSD socket file descriptor start value.</span></span> <span data-ttu-id="48834-232">기본적으로 이 옵션은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-232">By default this option is 32.</span></span>

- <span data-ttu-id="48834-233">**NX_BSD_MAX_SOCKETS**: BSD 계층에서 사용할 수 있는 총 소켓의 최대 수를 지정하며, 32의 배수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-233">**NX_BSD_MAX_SOCKETS**: Specifies the maximum number of total sockets available in the BSD layer and must be a multiple of 32.</span></span> <span data-ttu-id="48834-234">기본값은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-234">The value is defaulted to 32.</span></span>

- <span data-ttu-id="48834-235">**NX_BSD_SOCKET_QUEUE_MAX**: 수신 소켓 큐에 저장되는 최대 UDP 패킷 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-235">**NX_BSD_SOCKET_QUEUE_MAX**: Specifies the maximum number of UDP packets stored on the receive socket queue.</span></span> <span data-ttu-id="48834-236">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-236">The value is defaulted to 5.</span></span>

- <span data-ttu-id="48834-237">**NX_BSD_MAX_LISTEN_BACKLOG**: BSD TCP 소켓에 대한 수신 대기 큐('백로그')의 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-237">**NX_BSD_MAX_LISTEN_BACKLOG**: This specifies the size of the listen queue ('backlog') for BSD TCP sockets.</span></span> <span data-ttu-id="48834-238">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-238">The default value is 5.</span></span>

- <span data-ttu-id="48834-239">**NX_MICROSECOND_PER_CPU_TICK**: 스케줄러 타이머 틱당 마이크로초 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-239">**NX_MICROSECOND_PER_CPU_TICK**: Specifies the number of microseconds per scheduler timer tick.</span></span>

- <span data-ttu-id="48834-240">**NX_BSD_TIMEOUT**: BSD에 필요한 NetX Duo 내부 호출에 대한 시간 제한(타이머 틱 수)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-240">**NX_BSD_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo internal calls required by BSD.</span></span> <span data-ttu-id="48834-241">기본값은 (20 \* NX_IP_PERIODIC_RATE)입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-241">The default value is (20 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="48834-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: NetX Duo 연결 끊기 호출에 대한 시간 제한(타이머 틱 수)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo disconnect call.</span></span> <span data-ttu-id="48834-243">기본값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-243">The default value is 1.</span></span>

- <span data-ttu-id="48834-244">**NX_BSD_PRINT_ERRORS**: 설정되면 BSD 함수의 오류 상태 반환에서 줄 번호 및 오류 유형(예: 오류가 발생하는 NX_SOC_ERROR)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-244">**NX_BSD_PRINT_ERRORS**: If set, the error status return of a BSD function returns a line number and type of error e.g. NX_SOC_ERROR where the error occurs.</span></span> <span data-ttu-id="48834-245">이렇게 하려면 애플리케이션 개발자가 디버그 출력을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-245">This requires the application developer to define the debug output.</span></span> <span data-ttu-id="48834-246">기본 설정이 사용하지 않도록 설정되고 *nxd_bsd.h* 에 디버그 출력이 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-246">The default setting is disabled and no debug output is specified in *nxd_bsd.h*.</span></span>

- <span data-ttu-id="48834-247">**NX_BSD_TIMER_RATE**: BSD 주기적 타이머 작업이 실행되는 간격입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-247">**NX_BSD_TIMER_RATE**: Interval after which BSD periodic timer task runs.</span></span> <span data-ttu-id="48834-248">기본값은 1초(1 \* NX_IP_PERIODIC_RATE)입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-248">The default value is 1 second (1 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="48834-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: 설정되면 이 옵션을 통해 BSD 시간 제한 프로세스를 시스템 타이머 컨텍스트에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: If set, this option allows the BSD timeout process to execute in the system timer context.</span></span> <span data-ttu-id="48834-250">기본 동작은 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-250">The default behavior is disabled.</span></span> <span data-ttu-id="48834-251">이 기능은 챕터 2 "NetX Duo BSD 설치 및 사용"에서 자세히 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-251">This feature is described in more detail in Chapter 2 "Installation and Use of NetX Duo BSD".</span></span>

- <span data-ttu-id="48834-252">**NX_BSD_RAW_PPPOE_SUPPORT**: PPPoE 원시 패킷 지원을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-252">**NX_BSD_RAW_PPPOE_SUPPORT**: Enable PPPoE raw packet support.</span></span> <span data-ttu-id="48834-253">기본적으로 이 옵션은 사용하도록 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-253">By default this option is not enabled.</span></span>

- <span data-ttu-id="48834-254">**NX_BSD_ENABLE_DNS**: 사용하도록 설정되면 NetX Duo BSD에서 호스트 이름 또는 호스트 IP 주소에 대한 DNS 쿼리를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="48834-254">**NX_BSD_ENABLE_DNS**: If enabled, NetX Duo BSD will send a DNS query for a hostname or host IP address.</span></span> <span data-ttu-id="48834-255">이전에 DNS 클라이언트 인스턴스를 만들고 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-255">Requires a DNS Client instance to be previously created and started.</span></span> <span data-ttu-id="48834-256">기본적으로 사용하도록 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-256">By default it is not enabled.</span></span>

- <span data-ttu-id="48834-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: 원시 소켓 테이블의 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: Defines the size of the raw socket table.</span></span> <span data-ttu-id="48834-258">값은 2의 거듭제곱이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-258">The value must be a power of two.</span></span> <span data-ttu-id="48834-259">NetX BSD에서 원시 패킷을 보내고 받기 위해 NX_BSD_SOCKETS 형식의 소켓 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="48834-259">NetX BSD creates an array of sockets of type NX_BSD_SOCKETS for sending and receiving raw packets.</span></span> <span data-ttu-id="48834-260">NX_ENABLE_IP_RAW_PACKET_FILTER를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-260">NX_ENABLE_IP_RAW_PACKET_FILTER must be enabled.</span></span> <span data-ttu-id="48834-261">기본값은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-261">By default it is 32.</span></span>

- <span data-ttu-id="48834-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: *getaddrinfo* 에서 반환하는 최대 IPv4 주소 수입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: Maximum number of IPv4 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="48834-263">이는 NX_BSD_IPV6_ADDR_MAX_NUM과 함께 메모리를 *getaddrinfo* 의 주소 정보 스토리지에 동적으로 할당하기 위한 nx_bsd_addrinfo_block_pool NetX BSD 블록 풀의 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-263">This along with NX_BSD_IPV6_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span> <span data-ttu-id="48834-264">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-264">The default value is 5.</span></span>

- <span data-ttu-id="48834-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: *getaddrinfo* 에서 반환하는 최대 IPv6 주소 수입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: Maximum number of IPv6 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="48834-266">이는 NX_BSD_IPV4_ADDR_MAX_NUM과 함께 메모리를 *getaddrinfo* 의 주소 정보 스토리지에 동적으로 할당하기 위한 nx_bsd_addrinfo_block_pool NetX BSD 블록 풀의 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-266">This along with NX_BSD_IPV4_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span>

- <span data-ttu-id="48834-267">**NX_BSD_IPV4_ADDR_PER_HOST**: DNS 쿼리당 저장되는 최대 IPv4 주소를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-267">**NX_BSD_IPV4_ADDR_PER_HOST**: Defines maximum IPv4 addresses stored per DNS query.</span></span> <span data-ttu-id="48834-268">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-268">The default value is 5.</span></span>

- <span data-ttu-id="48834-269">**NX_BSD_IPV6_ADDR_PER_HOST**: DNS 쿼리당 저장되는 최대 IPv6 주소를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-269">**NX_BSD_IPV6_ADDR_PER_HOST**: Defines maximum IPv6 addresses stored per DNS query.</span></span> <span data-ttu-id="48834-270">기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-270">The default value is 2.</span></span>

## <a name="bsd-socket-options"></a><span data-ttu-id="48834-271">BSD 소켓 옵션</span><span class="sxs-lookup"><span data-stu-id="48834-271">BSD Socket Options</span></span>

<span data-ttu-id="48834-272">*setsockopt* 서비스를 사용하여 런타임에 소켓 단위로 사용하거나 사용하지 않도록 설정할 수 있는 NetX Duo BSD 소켓 옵션의 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-272">The following list of NetX Duo BSD socket options can be enabled (or disabled) at run time on a per socket basis using the *setsockopt* service:</span></span>

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

<span data-ttu-id="48834-273">option_level에는 두 가지 다른 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-273">There are two different settings for option_level.</span></span>

<span data-ttu-id="48834-274">런타임 소켓 옵션의 첫 번째 형식은 소켓 수준 옵션에 대한 SOL_SOCKET입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-274">The first type of run time socket options is SOL_SOCKET for socket level options.</span></span> <span data-ttu-id="48834-275">소켓 수준 옵션을 사용하도록 설정하려면 option_level이 SOL_SOCKET으로 설정되고 option_name이 특정 옵션(예: SO_BROADCAST)으로 설정된 *setsockopt* 를 호출합니다 *.*</span><span class="sxs-lookup"><span data-stu-id="48834-275">To enable a socket level option, call *setsockopt* with option_level set to SOL_SOCKET and option_name set to the specific option e.g. SO_BROADCAST *.*</span></span> <span data-ttu-id="48834-276">옵션 설정을 검색하려면 option_level이 SOL_SOCKET으로 다시 설정된 option_name에 대해 *getsockopt* 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-276">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to SOL_SOCKET.</span></span>

<span data-ttu-id="48834-277">런타임 소켓 수준 옵션의 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-277">The list of run time socket level options is shown below.</span></span>

- <span data-ttu-id="48834-278">**SO_BROADCAST**: 설정되면 NetX 소켓에서 브로드캐스트 패킷을 보내고 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-278">**SO_BROADCAST**:  If set, this enables sending and receiving broadcast packets from Netx sockets.</span></span> <span data-ttu-id="48834-279">이는 NetX Duo의 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-279">This is the default behavior for NetX Duo.</span></span> <span data-ttu-id="48834-280">모든 소켓에는 이 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-280">All sockets have this capability.</span></span>

- <span data-ttu-id="48834-281">**SO_ERROR**: *getsockopt* 서비스를 사용하여 지정된 소켓의 이전 소켓 작업에 대한 소켓 상태를 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-281">**SO_ERROR**:  Used to obtain socket status on the previous socket operation of the specified socket, using the *getsockopt* service.</span></span> <span data-ttu-id="48834-282">모든 소켓에는 이 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-282">All sockets have this capability.</span></span>

- <span data-ttu-id="48834-283">**SO_KEEPALIVE**: 설정되면 TCP 연결 유지 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-283">**SO_KEEPALIVE**:  If set, this enables the TCP Keep Alive feature.</span></span> <span data-ttu-id="48834-284">이렇게 하려면 *nx_user.h* 에 NX_TCP_ENABLE_KEEPALIVE가 정의된 NetX Duo 라이브러리를 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-284">This requires the NetX Duo library to be built with NX_TCP_ENABLE_KEEPALIVE defined in *nx_user.h*.</span></span> <span data-ttu-id="48834-285">기본적으로 이 기능은 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-285">By default this feature is disabled.</span></span>

- <span data-ttu-id="48834-286">**SO_RCVTIMEO**: NetX Duo BSD 소켓에서 패킷을 받기 위한 대기 옵션(초)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-286">**SO_RCVTIMEO**:  This sets the wait option in seconds for receiving packets on NetX Duo BSD sockets.</span></span> <span data-ttu-id="48834-287">기본값은 NX_WAIT_FOREVER (0xFFFFFFFF) 또는 비차단이 사용하도록 설정된 경우 NX_NO_WAIT (0x0)입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-287">The default value is the NX_WAIT_FOREVER (0xFFFFFFFF) or, if non-blocking is enabled, NX_NO_WAIT (0x0).</span></span>

- <span data-ttu-id="48834-288">**SO_RCVBUF**: TCP 소켓의 창 크기를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-288">**SO_RCVBUF**:  This sets the window size of the TCP socket.</span></span> <span data-ttu-id="48834-289">기본값인 NX_BSD_TCP_WINDOW는 BSD TCP 소켓에 대해 64k로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-289">The default value, NX_BSD_TCP_WINDOW, is set to 64k for BSD TCP sockets.</span></span> <span data-ttu-id="48834-290">65535보다 큰 크기를 설정하려면 NX_TCP_ENABLE_WINDOW_SCALING이 정의된 NetX Duo 라이브러리를 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-290">To set the size over 65535 requires the NetX Duo library to be built with the NX_TCP_ENABLE_WINDOW_SCALING be defined.</span></span>

- <span data-ttu-id="48834-291">**SO_REUSEADDR**: 설정되면 여러 소켓을 하나의 포트에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-291">**SO_REUSEADDR**:  If set, this enables multiple sockets to be mapped to one port.</span></span> <span data-ttu-id="48834-292">일반적으로 TCP 서버 소켓에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-292">The typical usage is for the TCP Server socket.</span></span> <span data-ttu-id="48834-293">이는 NetX Duo 소켓의 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-293">This is the default behavior of NetX Duo sockets.</span></span>

<span data-ttu-id="48834-294">두 번째 형식의 런타임 소켓 옵션은 IP 옵션 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-294">The second type of run time socket options is the IP option level.</span></span> <span data-ttu-id="48834-295">IP 수준 옵션을 사용하도록 설정하려면 option_level이 IP_PROTO로 설정되고 option_name이 옵션(예: IP_MULTICAST_TTL)으로 설정된 *setsockopt* 를 호출합니다 *.*</span><span class="sxs-lookup"><span data-stu-id="48834-295">To enable an IP level option, call *setsockopt* with option_level set to IP_PROTO and option_name set to the option e.g. IP_MULTICAST_TTL *.*</span></span> <span data-ttu-id="48834-296">옵션 설정을 검색하려면 option_level이 IP_PROTO로 다시 설정된 option_name에 대해 *getsockopt* 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-296">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to IP_PROTO.</span></span>

<span data-ttu-id="48834-297">런타임 IP 수준 옵션의 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-297">The list of run time IP level options is shown below.</span></span>

- <span data-ttu-id="48834-298">**IP_MULTICAST_TTL**: UDP 소켓의 TTL(Time to Live)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-298">**IP_MULTICAST_TTL**:  This sets the time to live for UDP sockets.</span></span> <span data-ttu-id="48834-299">소켓이 만들어질 때 기본값은 NX_IP_TIME_TO_LIVE (0x80)입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-299">The default value is NX_IP_TIME_TO_LIVE (0x80) when the socket is created.</span></span> <span data-ttu-id="48834-300">이 값은 이 소켓 옵션으로 *setsockopt* 를 호출하여 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-300">This value can be overridden by calling *setsockopt* with this socket option.</span></span>

- <span data-ttu-id="48834-301">**IP_RAW_IPV6_HDRINCL**: 이 옵션이 설정되면 호출 애플리케이션에서 IPv6 헤더 및 필요에 따라 애플리케이션 헤더를 BSD에서 만든 원시 IPv6 소켓에서 전송되는 데이터에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-301">**IP_RAW_IPV6_HDRINCL**:  If this option is set, the calling application must append an IPv6 header and optionally application headers to data being transmitted on raw IPv6 sockets created by BSD.</span></span> <span data-ttu-id="48834-302">이 옵션을 사용하려면 IP 작업에서 원시 소켓 처리를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-302">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="48834-303">**IP_ADD_MEMBERSHIP**: 설정되면 이 옵션을 통해 BSD 소켓(UDP 소켓에만 적용)이 지정된 IGMP 그룹에 조인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-303">**IP_ADD_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to join the specified IGMP group.</span></span>

- <span data-ttu-id="48834-304">**IP_DROP_MEMBERSHIP**: 설정되면 이 옵션을 통해 BSD 소켓(UDP 소켓에만 적용)이 지정된 IGMP 그룹에서 나갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-304">**IP_DROP_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to leave the specified IGMP group.</span></span>

- <span data-ttu-id="48834-305">**IP_HDRINCL**: 이 옵션이 설정되면 호출 애플리케이션에서 IP 헤더 및 필요에 따라 애플리케이션 헤더를 BSD에서 만든 원시 IPv4 소켓에서 전송되는 데이터에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-305">**IP_HDRINCL**:  If this option is set, the calling application must append the IP header and optionally application headers to data being transmitted on raw IPv4 sockets created in BSD.</span></span> <span data-ttu-id="48834-306">이 옵션을 사용하려면 IP 작업에서 원시 소켓 처리를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-306">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="48834-307">**IP_RAW_RX_NO_HEADER**: 선택 취소하면 BSD에서 만든 원시 IPv6 소켓에 대해 수신된 데이터에 IPv6 헤더가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-307">**IP_RAW_RX_NO_HEADER**:  If cleared, the IPv6 header is included with the received data for raw IPv6 sockets created in BSD.</span></span> <span data-ttu-id="48834-308">IPv6 헤더는 기본적으로 BSD 원시 IPv6 소켓에서 제거되며, 패킷 길이에는 IPv6 헤더가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-308">IPv6 headers are removed by default in BSD raw IPv6 sockets, and the packet length does not include the IPv6 header.</span></span>

<span data-ttu-id="48834-309">설정되면 IPv4 유형의 BSD 원시 소켓에서 수신된 데이터에서 IPv4 헤더가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-309">If set, the IPv4 header is removed from received data on BSD raw sockets of type IPv4.</span></span> <span data-ttu-id="48834-310">IPv4 헤더는 기본적으로 BSD 원시 IPv4 소켓에 포함되며, 패킷 길이에는 IPv4 헤더가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-310">IPv4 headers are included by default in BSD raw IPv4 sockets and packet length includes the IPv4 header.</span></span>

<span data-ttu-id="48834-311">이 옵션은 IPv4 또는 IPv6 전송 데이터에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-311">This option has no effect on either IPv4 or IPv6 transmission data.</span></span>

## <a name="small-ipv4-example"></a><span data-ttu-id="48834-312">간단한 IPv4 예제</span><span class="sxs-lookup"><span data-stu-id="48834-312">Small IPv4 Example</span></span>

<span data-ttu-id="48834-313">NetX Duo BSD 서비스를 IPv4 네트워크에 사용하는 방법에 대한 예제는 아래에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-313">An example of how to use NetX Duo BSD services for IPv4 networks is described below.</span></span> <span data-ttu-id="48834-314">이 예제에서 포함 파일 *nxd_bsd.h* 는 줄 8에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="48834-314">In this example, the include file *nxd_bsd.h* is brought in at line 8.</span></span> <span data-ttu-id="48834-315">다음으로 *bsd_ip* IP 인스턴스 및 *bsd_pool* 패킷 풀은 줄 20 및 21에서 전역 변수로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="48834-315">Next, the IP instance *bsd_ip* and packet pool *bsd_pool* are created as global variables at line 20 and 21.</span></span> <span data-ttu-id="48834-316">이 데모에서는 *_nx_ram_network_driver* RAM(가상) 네트워크 드라이버를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-316">Note that this demo uses a ram (virtual) network driver *, _nx_ram_network_driver*.</span></span> <span data-ttu-id="48834-317">이 예제에서 클라이언트와 서버는 단일 IP 인스턴스에서 동일한 IP 주소를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-317">The client and server will share the same IP address on single IP instance in this example.</span></span>

<span data-ttu-id="48834-318">클라이언트 및 서버 스레드는 줄 62 및 68에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="48834-318">The client and server threads are created on lines 62 and 68.</span></span> <span data-ttu-id="48834-319">패킷을 전송하기 위한 BSD 패킷 풀은 줄 78에서 만들어지며, 줄 87에서 IP 인스턴스를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-319">The BSD packet pool for transmitting packets is created on line 78 and used in the IP instance creation on line 87.</span></span> <span data-ttu-id="48834-320">IP 스레드 작업에는 *nx_ip_create* 호출에서 우선 순위가 1로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-320">Note that the IP thread task is given priority 1 in the *nx_ip_create* call.</span></span> <span data-ttu-id="48834-321">이 스레드는 최적의 NetX 성능을 위해 프로그램에 정의된 가장 높은 우선 순위 작업이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-321">This thread should be the highest priority task defined in the program for optimal NetX performance.</span></span>

<span data-ttu-id="48834-322">IP 인스턴스는 각각 줄 88 및 줄 110의 ARP 및 TCP 서비스에 대해 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-322">The IP instance is enabled for ARP and TCP services on lines 88 and 110 respectively.</span></span> <span data-ttu-id="48834-323">BSD 서비스를 사용하기 전의 마지막 요구 사항은 줄 120에서 *bsd_initialize* 를 호출하여 BSD에 필요한 모든 데이터 구조와 NetX 및 ThreadX 리소스를 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-323">The last requirement before BSD services can be used is to call *bsd_initialize* on line 120 to set up all data structures and NetX and ThreadX resources needed by BSD.</span></span>

<span data-ttu-id="48834-324">서버 스레드 입력 함수는 다음에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-324">The server thread entry function is defined next.</span></span> <span data-ttu-id="48834-325">BSD TCP 소켓은 줄 149에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="48834-325">The BSD TCP socket is created on line 149.</span></span> <span data-ttu-id="48834-326">서버 IP 주소와 포트는 줄 160-163에 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-326">The server IP address and port are set on lines 160-163.</span></span> <span data-ttu-id="48834-327">IP 주소 및 포트에 적용되는 *htonl* 및 *htons* 호스트-네트워크 바이트 순서 매크로를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-327">Note the use of host to network byte order macros *htonl* and *htons* applied to the IP address and port.</span></span> <span data-ttu-id="48834-328">이는 멀티바이트 데이터가 네트워크 바이트 순서로 BSD 서비스에 제출된다는 BSD 소켓 사양을 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-328">This is in compliance with BSD socket specification that multi byte data is submitted to the BSD services in network byte order.</span></span>

<span data-ttu-id="48834-329">다음으로, 마스터 서버 소켓은 줄 166에서 *bind* 서비스를 사용하여 포트에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-329">Next, the master server socket is bound to the port using the *bind* service on line 166.</span></span> <span data-ttu-id="48834-330">이는 줄 180에서 *listen* 서비스를 사용하는 TCP 연결 요청에 대한 수신 대기 소켓입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-330">This is the listening socket for TCP connection requests using the *listen* service on line 180.</span></span> <span data-ttu-id="48834-331">여기서 *thread_server_entry* 서버 스레드 함수는 줄 202에서 *select* 호출을 사용하여 수신 이벤트를 확인하기 위해 루프를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-331">From here the server thread function, *thread_server_entry*, loops to check for receive events using the *select* call on line 202.</span></span> <span data-ttu-id="48834-332">수신 이벤트가 읽기 준비 목록을 비교하여 결정되는 연결 요청인 경우 줄 213에서 *accept* 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-332">If a receive event is a connection request, which is determined by comparing the read ready list, it calls *accept* on line 213.</span></span> <span data-ttu-id="48834-333">연결 요청을 처리하기 위해 자식 서버 소켓이 할당되고 줄 223에서 클라이언트에 연결된 TCP 서버 소켓의 마스터 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-333">A child server socket is assigned to handle the connection request and added to the master list of TCP server sockets connected to a Client on line 223.</span></span> <span data-ttu-id="48834-334">새 연결 요청이 없는 경우 서버 스레드는 줄 236에서 시작하는 for 루프에서 수신 이벤트에 대해 현재 연결된 모든 소켓을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-334">If there are no new connection requests, the server thread then checks all the currently connected sockets for receive events in the for loop starting on line 236.</span></span> <span data-ttu-id="48834-335">수신 이벤트 대기가 검색되면 데이터가 수신되지 않고(다른 쪽에서는 연결이 닫힘) 소켓이 줄 277에서 *soc_close* 서비스를 사용하여 닫힐 때까지 해당 소켓에서 *send* 및 *recv* 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-335">When a receive event waiting is detected, it calls *send* and *recv* on that socket until no data is received (connection closed on the other side) and the socket is closed using the *soc_close* service on line 277.</span></span>

<span data-ttu-id="48834-336">서버 스레드가 설정되면 *thread_client_entry* 클라이언트 스레드 입력 함수가 줄 326에서 소켓을 만들고 줄 337에서 *connect* 호출을 사용하여 TCP 서버 소켓에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-336">After the server thread sets up, the Client thread entry function, *thread_client_entry,* creates a socket on line 326 and connects with the TCP server socket using the *connect* call on line 337.</span></span> <span data-ttu-id="48834-337">그런 다음, 각각 *send* 및 *recv* 서비스를 사용하여 패킷을 보내고 받는 루프를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-337">It then loops to send and receive packets using the *send* and *recv* services respectively.</span></span> <span data-ttu-id="48834-338">데이터가 더 이상 수신되지 않으면 줄 398에서 *soc_close* 서비스를 사용하여 소켓을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-338">When no more data is received, it closes the socket on line 398 using the *soc_close* service.</span></span> <span data-ttu-id="48834-339">연결이 끊긴 후 클라이언트 스레드 입력 함수는 새 TCP 소켓을 만들고, 줄 321에서 시작되는 while 루프에서 다른 연결 요청을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-339">After disconnection, the client thread entry function creates a new TCP socket and makes another connection request in the while loop started on line 321.</span></span>

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection, sending,
and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQR
    STUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */

ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */

VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */
int     main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool", 128,
                                pointer, 16384);

    pointer = pointer + 16384;
    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                    0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                    pointer, 2048, 1);
                    pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable ARP \n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize (&bsd_ip, &bsd_pool,pointer, 2048, 2);
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT       status, sock, sock_tcp_server;
ULONG     actual_status;
INT       Clientlen;
INT       i;
UINT      is_set = NX_FALSE;
struct    sockaddr_in serverAddr;
struct    sockaddr_in ClientAddr;

    tx_thread_sleep(100);

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
        &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("Error on Server socket %d create \n", sock_tcp_server);
        return;
    }

    printf("Server socket %d created\n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    serverAddr.sin_port = htons(SERVER_PORT);

    /* Bind this server socket */
    status = bind (sock_tcp_server, (struct sockaddr *) &serverAddr,
                sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error on Server Socket %d Bind \n", sock_tcp_server);
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen (sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error on Server Socket %d Listen\n", sock_tcp_server);
        return;
    }
    else
        printf("Server socket %d listen complete\n", sock_tcp_server);

    /* All set to accept client connections */

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ((status == 0xFFFFFFFF) || (status == 0))
        {

            printf("Error with select. Status 0x%x\n", status);

            continue;
        }

        /* Check for a connection request. */
        is_set = FD_ISSET(sock_tcp_server, &read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,(struct sockaddr*)&ClientAddr,
                        &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i , &master_list)) &&
                (FD_ISSET(i , &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server received no data from Client on
                            socket %d)\n", i);
                        break;
                    }
                    else if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server receiving data from Client on
                            socket %d\n", i);
                        break;
                    }
                    if(status == SERVER_RCV_BUFFER_SIZE) status--;
                    Server_Rcv_Buffer[status] = 0;
                    printf("Server socket %d received %d bytes: %s\n ",
                            i, (ULONG)status, Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                        Client\n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                        Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != NX_SOC_ERROR)
                {
                    printf("Server socket %d closed \n", i);
                }
                else
                {
                    printf("Error on closing Server socket %d \n", i);
                }
            }
        }

    /* Loop back to check any next client connection */
    }
}

CHAR     Client_Rcv_Buffer[100];

VOID     thread_client_entry(ULONG thread_input)
{

INT        status;
INT        sock_tcp_client, length;
struct     sockaddr_in echoServAddr;
struct     sockaddr_in localAddr; /

    /* Let the server side get set up. */
    tx_thread_sleep(200);

    /* Set local port for displaying IP address and port. */
    memset(&localAddr, 0, sizeof(localAddr));
    localAddr.sin_family = AF_INET;
    localAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    localAddr.sin_port = htons(CLIENT_PORT);

    /* Set server port and IP address which we need to connect. */
    memset(&echoServAddr, 0, sizeof(echoServAddr));
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    echoServAddr.sin_port = htons(SERVER_PORT);

    /* Now make client connections with the server. */
    while (1)
    {

        printf("\n");

        /* Create BSD TCP Socket */
        sock_tcp_client = socket( AF_INET, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n", sock_tcp_client);
            return;
        }

        printf("Client socket %d created\n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr,
                        sizeof(echoServAddr));

        /* Check for error. */
        if (status != OK)
        {
            printf("Error on Client socket %d connect\n", sock_tcp_client);
                    soc_close(sock_tcp_client);
            return;
        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr,
                            &length);

        printf("Client port = %lu , Client = 0x%x,",
            htonl(localAddr.sin_port), htonl(localAddr.sin_addr.s_addr));

        length = sizeof(struct sockaddr_in);

        status = getpeername( sock_tcp_client, (struct sockaddr *)
                            &echoServAddr, &length);

        printf("Remote port = %lu, Remote IP = 0x%x \n",
                htonl(echoServAddr.sin_port),
                htonl(echoServAddr.sin_addr.s_addr));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
            sock_tcp_client);

            status = send(sock_tcp_client, "Hello", (sizeof("Hello")), 0);

            if (status == ERROR)
            {
                printf("Error: Client Socket (%d) send \n", sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,100,0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    380 printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Nothing received by Client on socket %d\n",
                            sock_tcp_client);
                }

                break;
            }
            else
            {
                printf("Client socket %d received %d bytes: %s\n",
                        sock_tcp_client,
                        status, Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = soc_close(sock_tcp_client);

        if (status != ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```

## <a name="small-ipv6-example-system"></a><span data-ttu-id="48834-340">간단한 IPv6 예제 시스템</span><span class="sxs-lookup"><span data-stu-id="48834-340">Small IPv6 Example System</span></span>

<span data-ttu-id="48834-341">NetX Duo BSD 서비스를 IPv6 네트워크에 사용하는 방법에 대한 예제는 아래 프로그램에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-341">An example of how to use NetX Duo BSD services for IPv6 networks is described in the program below.</span></span> <span data-ttu-id="48834-342">이 예제는 몇 가지 중요한 차이점을 제외하고 앞에서 설명한 IPv4 데모 프로그램과 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-342">This example is very similar to the IPv4 demo program previously described with a few important differences.</span></span>

<span data-ttu-id="48834-343">클라이언트 및 서버 스레드, BSD 패킷 풀, IP 인스턴스 및 BSD 초기화는 IPv4 BSD 소켓과 마찬가지로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-343">The client and server threads, BSD packet pool, IP instance and BSD initialization happens as it does for IPv4 BSD sockets.</span></span>

<span data-ttu-id="48834-344">*thread_server_entry* 서버 스레드 입력 함수는 줄 145-148에서 *sockaddr_in6* 및 *NXD_ADDRESS* 데이터 형식을 사용하여 두 개의 IPv6 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-344">In the server thread entry function, *thread_server_entry*, defines a couple IPv6 variables using *sockaddr_in6* and *NXD_ADDRESS* data types on lines 145-148.</span></span> <span data-ttu-id="48834-345">NXD_ADDRESS 데이터 형식은 실제로 IPv4 및 IPv6 주소 형식을 모두 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-345">The NXD_ADDRESS data type can actually store both IPv4 and IPv6 address types.</span></span>

<span data-ttu-id="48834-346">다음으로, 서버 스레드는 줄 161 및 줄 169에서 각각 *nxd_ipv6_enable* 및 *nxd_icmpv6_enable* 서비스를 사용하여 IP 인스턴스에서 IPv6 및 ICMPv6을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-346">Next, the server thread enables IPv6 and ICMPv6 on the IP instance using the *nxd_ipv6_enable* and *nxd_icmpv6_enable* service respectively on line 161 and 169.</span></span> <span data-ttu-id="48834-347">다음으로 링크 로컬 및 전역 IP 주소가 IP 인스턴스에 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-347">Next, the link local and global IP addresses are registered with the IP instance.</span></span> <span data-ttu-id="48834-348">이는 줄 180 및 줄 195에서 *nxd_ipv6_address_set* 서비스를 사용하여 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-348">This is done using the *nxd_ipv6_address_set* service on lines 180 and 195.</span></span> <span data-ttu-id="48834-349">그런 다음, IP 스레드 작업이 중복 주소 검색 프로토콜을 완료하고, 이러한 주소를 줄 201의 *tx_thread_sleep* 호출에 유효한 주소로 등록할 수 있을 만큼 충분히 오래 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-349">It then sleeps long enough for the IP thread task to complete the Duplicate Address Detection protocol and register these addresses as valid addresses on the *tx_thread_sleep* call on line 201.</span></span>

<span data-ttu-id="48834-350">다음으로, TCP 서버 소켓은 줄 204에서 AF_INET6 소켓 유형 입력 인수를 사용하여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="48834-350">Next, the TCP server socket is created with the AF_INET6 socket type input argument on line 204.</span></span> <span data-ttu-id="48834-351">소켓 IPv6 주소와 포트는 줄 216-221에서 설정되며, BSD 소켓 서비스에 대한 데이터를 네트워크 바이트 순서로 배치하기 위해 *htonl* 및 *htons* 매크로를 다시 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-351">The socket IPv6 address and port are set on lines 216-221, again noting the use of *htonl* and *htons* macros to put data in network byte order for BSD socket services.</span></span> <span data-ttu-id="48834-352">여기서부터 서버 스레드 입력 함수는 IPv4 예제와 거의 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-352">From here on, the server thread entry function is virtually identical to the IPv4 example.</span></span>

<span data-ttu-id="48834-353">*thread_client_entry* 클라이언트 스레드 입력 함수는 다음에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-353">The client thread entry function, *thread_client_entry*, is defined next.</span></span> <span data-ttu-id="48834-354">이 예제의 TCP 클라이언트는 TCP 서버와 동일한 IP 인스턴스 및 IPv6 주소를 공유하므로 IP 인스턴스에서 IPv6 또는 ICMPv6 서비스를 다시 사용하도록 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-354">Note that because the TCP client in this example shares the same IP instance and IPv6 address as the TCP server, we do not need to enable IPv6 or ICMPv6 services on the IP instance again.</span></span> <span data-ttu-id="48834-355">또한 IPv6 주소도 이미 IP 인스턴스에 등록되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-355">Further, the IPv6 address is also already registered with the IP instance.</span></span> <span data-ttu-id="48834-356">대신 클라이언트 스레드 입력 함수는 서버가 설정될 때까지 줄 368에서 대기하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-356">Instead, the client thread entry function simply waits on line 368 for the server to set up.</span></span> <span data-ttu-id="48834-357">서버 주소와 포트가 줄 387-392에서 호스트-네트워크 바이트 순서 매크로를 사용하여 설정된 다음, 줄 412에서 클라이언트가 TCP 서버에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48834-357">The server address and port are set, using the host to network byte order macros on lines 387-392, and then the Client can connect with the TCP server on line 412.</span></span> <span data-ttu-id="48834-358">줄 378-383의 로컬 IP 주소 데이터 형식은 줄 425 및 줄 434에서 각각 *getsockname* 및 *getpeername* 서비스를 설명하는 데만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-358">Note that the local IP address data types in lines 378-383 are used only to demonstrate the *getsockname* and *getpeername* services on lines 425 and 434 respectively.</span></span> <span data-ttu-id="48834-359">데이터가 네트워크에서 제공되므로 줄 378-383에서 네트워크-호스트 바이트 순서 매크로가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="48834-359">Because the data is coming from the network, the network to host byte order macros as used in lines 378-383.</span></span>

<span data-ttu-id="48834-360">다음으로, 클라이언트 스레드 입력 함수는 TCP 소켓을 만들고, TCP 연결을 설정하고, IPv4 예제와 거의 동일한 데이터가 더 이상 수신되지 않을 때까지 TCP 서버와 데이터를 보내고 받는 루프에 진입합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-360">Next the client thread entry function enters a loop in which it creates a TCP socket, makes a TCP connection and sends and receives data with the TCP server until no more data is received virtually the same as the IPv4 example.</span></span> <span data-ttu-id="48834-361">그런 다음, 줄 483에서 소켓을 닫고, 잠시 일시 중지하고, 다른 TCP 소켓을 만들고, TCP 서버 연결을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="48834-361">It then closes the socket on line 483, pauses briefly and creates another TCP socket and requests a TCP server connection.</span></span>

<span data-ttu-id="48834-362">IPv4 예제와의 한 가지 중요한 차이점은 *socket* 호출에서 AF_INET6 입력 인수를 사용하여 IPv6 소켓을 지정한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-362">One important difference with the IPv4 example is the *socket* calls specify an IPv6 socket using the AF_INET6 input argument.</span></span> <span data-ttu-id="48834-363">또 다른 중요한 차이점은 TCP 클라이언트 *connect* 호출에서 *sockaddr_in6* 데이터 형식 및 *sockaddr_in6* 데이터 형식의 크기로 설정된 길이 인수를 사용한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="48834-363">Another important difference is that the TCP Client *connect* call takes an *sockaddr_in6* data type and a length argument set to the size of the *sockaddr_in6* data type.</span></span>

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection,
disconnection, sending, and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */
ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */
VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int     main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool",
    128, pointer, 16384);

    pointer = pointer + 16384;

    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                        0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in enable ARP on BSD IP instance\n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 2);

    /* Check BSD initialize status. */
    if (status)
    {
        error_counter++;
        printf("Error in BSD initialize \n");
    }

    pointer = pointer + 2048;
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT             status, sock, sock_tcp_server;
ULONG           actual_status;
INT             Clientlen;
INT             i;
UINT            is_set = NX_FALSE;
NXD_ADDRESS     ip_address;
struct          sockaddr_in6 serverAddr;
struct          sockaddr_in6 ClientAddr;
UINT            iface_index, address_index;

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
            &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 */
    status = nxd_ipv6_enable(&bsd_ip);
    if((status != NX_SUCCESS) && (status != NX_ALREADY_ENABLED))
    {
        printf("Error with IPv6 enable 0x%x\n", status);
        return;
    }

    /* Enable ICMPv6 */
    status = nxd_icmp_enable(&bsd_ip);

    if(status)
    {
        printf("Error with ECMPv6 enable 0x%x\n", status);
        return;
    }

    /* Set the primary interface for our DNS IPv6 addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, NX_NULL, 10,
                                &address_index);

    if (status)
        return;

    /* Set ip_0 interface address. */
    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    ip_address.nxd_ip_address.v6[0] = htonl(0x20010db8);
    ip_address.nxd_ip_address.v6[1] = htonl(0x0000f101);
    ip_address.nxd_ip_address.v6[2] = 0;
    ip_address.nxd_ip_address.v6[3] = htonl(0x101);

    /* Set the host global IP address. We are assuming a 64
    bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, &ip_address, 64,
                                &address_index);

    if (status)
        return;

    /* Wait for IPv6 stack to finish DAD process. */
    tx_thread_sleep(400);

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET6, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("\nError: BSD TCP Server socket create \n");
        return;
    }

    printf("\nBSD TCP Server socket created %lu \n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    serverAddr.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    serverAddr.sin6_addr._S6_un._S6_u32[2] = 0x0;
    serverAddr.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    serverAddr.sin6_port = htons(SERVER_PORT);
    serverAddr.sin6_family = AF_INET6;

    /* Bind this server socket */
    status = bind(sock_tcp_server, (struct sockaddr *) &serverAddr,
                    sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error: Server Socket Bind \n");
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen(sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error: Server Socket Listen\n");
        return;
    }
    else
        printf("Server Listen complete\n");

    /* All set to accept client connections */
    printf("Now accepting client connections\n");

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ( (status == 0xFFFFFFFF) || (status == 0) )
        {
            printf("Error with select? Status 0x%x. Try again\n", status);

            continue;
        }

        /* Detected a connection request. */
        is_set = FD_ISSET(sock_tcp_server,&read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,
            (struct sockaddr*)&ClientAddr,
            &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {
                printf("New connection %d\n", sock);

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i, &master_list)) &&
                (FD_ISSET(i, &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server socket %d received no data from
                                Client)\n", i);

                        break;
                    }
                    else if (status == 0xFFFFFFFF)
                    {
                        printf("Error on Server socket %d receiving data from
                                Client\n", i);

                        break;
                    }

                    printf("Server socket %d received from Client %lu bytes:
                            %s\n ", i, (ULONG)status,
                            Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                                Client \n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                                Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != ERROR)
                {
                    printf("Server socket %d closing\n", i);
                }
                else
                {

                    printf("Error on Server socket %d closing\n", i);
                }
            }
        }

        /* Loop back to check any next client connection */
    }
}

#define     CLIENT_BUFFER_SIZE 100
CHAR        Client_Rcv_Buffer[CLIENT_BUFFER_SIZE];

VOID        thread_client_entry(ULONG thread_input)
{

INT         status;
INT         sock_tcp_client, length;
struct      sockaddr_in6 echoServAddr6;
struct      sockaddr_in6 localAddr6; address */

    /* Wait for the server side to get set up, including the DAD process. */
    tx_thread_sleep(500);

    /* ICMPv6 and IPv6 should already be enabled on the IP instance
    by the server thread entry function. */

    /* Further the IPv6 address is already established with the IP instance.
    so no need to wait for DAD completion. */

    /* Set local port and IP address (used only for getsockname call). */
    memset(&localAddr6, 0, sizeof(localAddr6));
    localAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    localAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    localAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    localAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    localAddr6.sin6_port = htons(CLIENT_PORT);
    localAddr6.sin6_family = AF_INET6;

    /* Set Server port and IP address to connect to the TCP server. */
    memset(&echoServAddr6, 0, sizeof(echoServAddr6));
    echoServAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    echoServAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    echoServAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    echoServAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    echoServAddr6.sin6_port = htons(SERVER_PORT);
    echoServAddr6.sin6_family = AF_INET6;

    /* Now make client connections with the server. */
    while (1)
    {
        printf("\n");

        /* Create BSD TCP Socket */

        sock_tcp_client = socket(AF_INET6, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n");
            return;
        }

        printf("Client socket %d created \n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr6,
                sizeof(echoServAddr6));

        /* Check for error. */
        if (status != NX_SOC_OK)
        {
            printf("Error on Client socket %d connect\n");
            soc_close(sock_tcp_client);
            return;

        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr6,
        &length);

        printf("Client port = %lu , Client = 0x%x 0x%x 0x%x 0x%x,",
                ntohs(localAddr6.sin6_port),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[3]));

        length = sizeof(struct sockaddr_in6);

        status = getpeername(sock_tcp_client, (struct sockaddr *)
                            &echoServAddr6, &length);

        printf("Remote port = %lu, Remote IP = 0x%x 0x%x 0x%x 0x%x \n",
                ntohs(echoServAddr6.sin6_port),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[3]));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
                sock_tcp_client);

            status = send(sock_tcp_client, "Hello", sizeof("Hello"), 0);

            if (status == NX_SOC_ERROR)
            {
                printf("Error on Client Socket (%d) send \n",
                        sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message: Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,
                        CLIENT_BUFFER_SIZE, 0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Client received no data on socket %d\n",
                            sock_tcp_client);
                }

            break;
            }
            else
            {
                printf("Client socket %d received %d bytes and this message:
                        %s\n", sock_tcp_client, status,
                        Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = oc_close(sock_tcp_client);

        if (status != NX_SOC_ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```
