---
title: 1장 - NAT(Network Address Translation) 소개
description: IP NAT(Network Address Translation)는 원래 제한된 수의 인터넷 IPv4 주소 문제를 해결하기 위해 개발되었습니다.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3d01aa6f68e21ea82f65a59a19c4f5c7958a6b92
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810686"
---
# <a name="chapter-1---an-introduction-to-network-address-translation"></a><span data-ttu-id="66d80-103">1장 - NAT(Network Address Translation) 소개</span><span class="sxs-lookup"><span data-stu-id="66d80-103">Chapter 1 - An introduction to Network Address Translation</span></span>

## <a name="the-need-for-network-address-translation"></a><span data-ttu-id="66d80-104">NAT(Network Address Translation)의 필요성</span><span class="sxs-lookup"><span data-stu-id="66d80-104">The Need for Network Address Translation</span></span>

<span data-ttu-id="66d80-105">IP NAT(Network Address Translation)는 원래 제한된 수의 인터넷 IPv4 주소 문제를 해결하기 위해 개발되었습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-105">IP Network Address Translation (NAT) was originally developed to solve the problem of a limited number of Internet IPv4 addresses.</span></span> <span data-ttu-id="66d80-106">여러 디바이스에서 인터넷에 액세스해야 하지만 하나의 IPv4 인터넷 주소만 ISP(인터넷 서비스 공급자)에 의해 할당되는 경우 NAT가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-106">The need for NAT arises when multiple devices need to access the Internet but only one IPv4 Internet address is assigned by the Internet Service Provider (ISP).</span></span>

<span data-ttu-id="66d80-107">또한 NAT를 사용할 경우 다른 이점도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-107">There are other benefits of using NAT as well.</span></span> <span data-ttu-id="66d80-108">로컬 도메인 외부의 네트워크 토폴로지는 다양한 방식으로 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-108">Network topology outside the local domain can change in many ways.</span></span> <span data-ttu-id="66d80-109">고객이 공급자를 변경하거나, 회사 백본이 재구성되거나, 공급자가 합병 또는 분할될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-109">Customers may change providers, company backbones may be reorganized, or providers may merge or split.</span></span> <span data-ttu-id="66d80-110">외부 토폴로지가 변경될 때마다 로컬 도메인 내의 호스트에 대한 주소 할당도 이러한 외부 변경 내용을 반영하도록 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-110">Whenever the external topology changes, address assignments for hosts within the local domain must also change to reflect these external changes.</span></span> <span data-ttu-id="66d80-111">단일 주소 변환 라우터의 변경 내용을 중앙 집중식으로 관리하여 도메인 내의 사용자에게 이 유형의 변경 내용을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-111">Changes of this type can be hidden from users within the domain by centralizing changes to a single address translation router.</span></span> <span data-ttu-id="66d80-112">NAT는 로컬 호스트가 공용 인터넷에 액세스할 수 있게 하고 외부에서는 직접 액세스할 수 없도록 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-112">NAT enables access for local hosts to the public Internet and protects them from direct access from the outside.</span></span> <span data-ttu-id="66d80-113">네트워크를 주로 내부용으로 사용하는 조직에서는 이 체계를 사용하는 경우에도 가끔 외부 액세스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-113">Organizations with a network setup predominantly for internal use, with a need for occasional external access are good candidates for this scheme.</span></span>

## <a name="basic-nat-and-network-address-port-translation"></a><span data-ttu-id="66d80-114">기본 NAT 및 네트워크 주소 포트 변환</span><span class="sxs-lookup"><span data-stu-id="66d80-114">Basic NAT and Network Address Port Translation</span></span>

<span data-ttu-id="66d80-115">NAT 지원 라우터는 공용 네트워크와 개인 네트워크 사이에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-115">A NAT-enabled router is installed between the public network and the private network.</span></span> <span data-ttu-id="66d80-116">NAT 지원 라우터의 역할은 내부 비공개 IPv4 주소와 할당된 공용 IPv4 주소 간에 변환하는 것이므로 개인 네트워크의 모든 디바이스는 동일한 공용 IPv4 주소를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-116">The role of the NAT-enabled router is to translate between the internal private IPv4 addresses and the assigned public IPv4 address, so all the devices on the private network are able to share the same public IPv4 address.</span></span>

<span data-ttu-id="66d80-117">NAT의 기본 구현에서 NAT 라우터는 자체 IP 주소와 다른 전역적으로 등록된 IP 주소를 하나 이상 ‘소유’합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-117">In the basic implementation of NAT, the NAT router ‘owns’ one or more globally registered IP addresses different from its own IP address.</span></span> <span data-ttu-id="66d80-118">이러한 전역 주소는 고정적으로 또는 동적으로 개인 네트워크의 호스트에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-118">These global addresses are available to assign to hosts on its private network either statically or dynamically.</span></span> <span data-ttu-id="66d80-119">NAPT 또는 네트워크 주소 포트 변환은 기본 NAT의 변형입니다. 여기에서 NAT(Network Address Translation)는 'transport' 식별자를 포함하도록 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-119">NAPT, or Network Address Port Translation, is a variation of basic NAT, where network address translation is extended to include a ‘transport’ identifier.</span></span> <span data-ttu-id="66d80-120">일반적으로 TCP 및 UDP 패킷에 대한 포트 번호와 ICMP 패킷에 대한 쿼리 ID가 여기에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-120">Most typically this is the port number for TCP and UDP packets, and the Query ID for ICMP packets.</span></span>

<span data-ttu-id="66d80-121">NAT 경계에 걸친 연결은 일반적으로 외부 호스트로 아웃바운드 패킷을 보내는 개인 네트워크의 호스트에 의해 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-121">Connections across the NAT boundary are typically initiated by hosts on the private network sending outbound packets to an external host.</span></span> <span data-ttu-id="66d80-122">이러한 호스트는 일반적으로 이 용도로 *동적*(임시) IP 주소를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-122">These hosts are usually assigned *dynamic* (temporary) IP addresses for this purpose.</span></span> <span data-ttu-id="66d80-123">그러나 개인 네트워크에 외부 네트워크의 클라이언트 요청을 수락하는 '서버'(예: HTTP 또는 FTP 서버)가 있는 경우에는 연결이 반대 방향으로 시작될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-123">However, it is also possible to have connections initiated in the opposite direction if the private network has ‘servers’ e.g. HTTP or FTP servers that will accept Client requests from the external network.</span></span> <span data-ttu-id="66d80-124">일반적으로 NAT는 이러한 로컬 호스트에 *고정*(영구) IP address:port를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-124">NAT will typically assign these local hosts a *static* (permanent) IP address:port.</span></span>

## <a name="how-network-address-translation-works"></a><span data-ttu-id="66d80-125">NAT(Network Address Translation)의 작동 방식</span><span class="sxs-lookup"><span data-stu-id="66d80-125">How Network Address Translation Works</span></span>

<span data-ttu-id="66d80-126">일반적으로 NAT 지원 라우터를 사용하는 네트워크 설정은 그림 1에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-126">A typical network setup with a NAT-enabled router is illustrated in Figure 1.</span></span>

![NAT 지원 라우터를 사용하는 일반적인 네트워크 설정](media/image2.png)

<span data-ttu-id="66d80-128">**그림 1 - NAT 지원 라우터를 사용하는 일반적인 네트워크 설정**</span><span class="sxs-lookup"><span data-stu-id="66d80-128">**Figure 1 - A typical network setup with a NAT-enabled router**</span></span>

<span data-ttu-id="66d80-129">일반적으로 NAT 지원 라우터에는 두 개의 네트워크 인터페이스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-129">A NAT-enabled router typically has two network interfaces.</span></span> <span data-ttu-id="66d80-130">한 인터페이스는 공용 인터넷에 연결되고 다른 인터페이스는 개인 네트워크에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-130">One interface is connected to the public Internet; the other is connected to the private network.</span></span> <span data-ttu-id="66d80-131">이 설치 프로그램의 일반적인 라우터는 대상 IP 주소를 기반으로 하는 공용 네트워크와 개인 네트워크 간에 IP 데이터그램을 라우팅하는 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-131">A typical router in this setup is responsible for routing IP datagrams between the private network and the public network based on destination IP address.</span></span> <span data-ttu-id="66d80-132">NAT 지원 라우터는 공용 인터페이스와 개인 인터페이스 간에 IPv4 데이터그램을 라우팅하기 전에 주소 변환을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-132">A NAT-enabled router performs address translation before routing an IPv4 datagram between the public and the private interface.</span></span> <span data-ttu-id="66d80-133">내부 원본 주소, 원본 포트 번호, 외부 대상 주소, 대상 포트 번호를 기반으로 각 TCP 또는 UDP 세션에 대해 변환이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-133">A translation is established for each TCP or UDP session, based the internal source address, source port number, and external destination address and destination port number.</span></span> <span data-ttu-id="66d80-134">ICMP 에코 요청 및 응답 데이터그램의 경우 포트 번호 대신 ICMP 쿼리 ID가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-134">For ICMP echo request and response datagram, the ICMP query ID is used instead of the port number.</span></span>

<span data-ttu-id="66d80-135">NAT(Network Address Translation)의 일반적인 구현을 보여 주기 위해 그림 2의 네트워크 설정을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-135">To illustrate a typical implementation of Network Address Translation, let us consider a network setup in Figure 2.</span></span>

![NAT(Network Address Translation)의 일반적인 구현](media/image3.png)

<span data-ttu-id="66d80-137">**그림 2 - NAT(Network Address Translation)의 일반적인 구현**</span><span class="sxs-lookup"><span data-stu-id="66d80-137">**Figure 2 - A typical implementation of Network Address Translation**</span></span>

<span data-ttu-id="66d80-138">이 시나리오에서 NAT 라우터는 개인 네트워크를 왼쪽에 연결하고 공용 네트워크는 오른쪽에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-138">In this scenario, the NAT router connects the private network to the left, and the public network to the right.</span></span> <span data-ttu-id="66d80-139">공용 네트워크 쪽의 NAT 라우터 인터페이스 IP 주소를 202.151.25.14라고 가정하겠습니다. 개인 네트워크 인터페이스에서 NAT 라우터는 IP 주소 192.168.1.254를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-139">Let’s assume on the public network side, the NAT router interface IP address is 202.151.25.14; on the private network interface, the NAT router uses the IP address 192.168.1.254.</span></span> <span data-ttu-id="66d80-140">개인 네트워크의 노드는 인터넷에서 웹 서버와의 TCP 연결을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-140">A node on the private network initiates a TCP connection with a web server on the Internet.</span></span>

<span data-ttu-id="66d80-141">그림 3에서는 NAT(Network Address Translation) 프로세스에 대한 개략적인 보기를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-141">Figure 3 shows a high-level view of the Network Address Translation process.</span></span>

![NAT(Network Address Translation) 프로세스의 개략적인 보기](media/image4.png)

<span data-ttu-id="66d80-143">**그림 3 - NAT(Network Address Translation) 프로세스의 개략적인 보기**</span><span class="sxs-lookup"><span data-stu-id="66d80-143">**Figure 3 - A high-level view of the Network Address Translation process**</span></span>

1. <span data-ttu-id="66d80-144">클라이언트에서 TCP SYN 메시지를 웹 서버로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-144">Client transmits a TCP SYN message to the web server.</span></span> <span data-ttu-id="66d80-145">발신자 주소는 192.168.1.15이고 포트 번호는 6732입니다. 대상 주소는 128.15.54.3이고 포트 번호는 80입니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-145">The sender address is 192.168.1.15, port number 6732; the destination address is 128.15.54.3, port number 80.</span></span>
1. <span data-ttu-id="66d80-146">클라이언트의 패킷은 NAT 라우터에 의해 개인 네트워크 인터페이스에서 수신됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-146">The packet from the Client is received on the private network interface by the NAT router.</span></span> <span data-ttu-id="66d80-147">아웃바운드 트래픽 규칙이 패킷에 적용됩니다. 즉, 발신자(클라이언트)의 주소는 NAT 라우터의 공용 IP 주소 202.15.25.14로 변환되고 발신자(클라이언트) 원본 포트 번호는 공용 인터페이스의 TCP 포트 번호 2015로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-147">The outbound traffic rule applies to the packet: the sender’s (Client’s) address is translated to the NAT router’s public IP address 202.15.25.14, and sender (Client) source port number is translated to the TCP port number 2015 on the public interface.</span></span>
1. <span data-ttu-id="66d80-148">그러면 패킷이 인터넷을 통해 전송되고 궁극적으로 대상 호스트인 128.15.54.3에 도달합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-148">The packet is then transmitted over the Internet and ultimately reaches its destination host 128.15.54.3.</span></span> <span data-ttu-id="66d80-149">수신 쪽에서는 IP 계층 원본 주소와 TCP 계층 포트 번호를 기반으로, 패킷이 202.151.24.14, 포트 번호 2015에서 시작된 것으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-149">Notice that on the receiving side, based on the IP layer source address and TCP layer port number, the packet appears to have originated from 202.151.24.14, port number 2015.</span></span>
   <span data-ttu-id="66d80-150">그림 4에서는 반환 경로에 대한 NAT 프로세스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-150">Figure 4 shows the NAT process on the return path.</span></span>

   ![반환 경로에 대한 NAT 프로세스](media/image5.png)

   <span data-ttu-id="66d80-152">**그림 4 - 반환 경로에 대한 NAT 프로세스**</span><span class="sxs-lookup"><span data-stu-id="66d80-152">**Figure 4 - NAT process on the return path**</span></span>
1. <span data-ttu-id="66d80-153">이 시나리오에서 인터넷 호스트 128.15.54.3은 NAT 라우터의 인터넷 주소를 대상으로 하는 응답 패킷을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-153">In this scenario, the Internet host 128.15.54.3 sends a response packet with the NAT router’s Internet address as its destination.</span></span>
1. <span data-ttu-id="66d80-154">패킷이 NAT 라우터에 도달합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-154">The packet reaches the NAT router.</span></span> <span data-ttu-id="66d80-155">이는 인바운드 패킷이므로 바인딩된 변환 규칙이 적용됩니다. 대상 주소가 원래 발신자(클라이언트)의 IP 주소(192.168.1.15, 대상 포트 번호 6732)로 다시 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-155">Since this is an in-bound packet, the in-bound translation rules apply: the destination address is changed back to the original sender’s (Client’s) IP address: 192.168.1.15, destination port number 6732.</span></span>
1. <span data-ttu-id="66d80-156">그러면 패킷이 내부 네트워크에 연결된 인터페이스를 통해 클라이언트에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-156">The packet is then forwarded to the Client through the interface that is connected to the internal network.</span></span>

<span data-ttu-id="66d80-157">이러한 방식으로 인터넷 네트워크 주소와 발신자의 포트 번호는 공용 인터넷의 다른 호스트에 노출되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-157">In this manner the internet network address and port number of the sender is not exposed to other hosts on the public Internet.</span></span>

## <a name="netx-duo-nat-features"></a><span data-ttu-id="66d80-158">NetX Duo NAT 기능</span><span class="sxs-lookup"><span data-stu-id="66d80-158">NetX Duo NAT Features</span></span>

<span data-ttu-id="66d80-159">*Nx_nat_create* 호출을 사용하여 NAT 인스턴스를 만들면 NAT 변환 테이블이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-159">When the NAT instance is created using *nx_nat_create* call, the NAT translation table is created.</span></span>

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

<span data-ttu-id="66d80-160">로컬 네트워크와 외부 네트워크 간의 모든 활성 연결에 대한 NAT(Network Address Translation)를 추적하기 위해 NetX Duo NAT 지원 라우터는 변환 테이블을 유지 관리하며, 이 테이블에는 원본 및 대상 IP 주소와 포트 번호를 포함하는 각 비공개 호스트 연결에 대한 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-160">To keep track of the network address translations for all active connections between local and external networks, the NetX Duo NAT-enabled router maintains a translation table with information about each private host connection which includes source and destination IP address and port number.</span></span>

<span data-ttu-id="66d80-161">이 변환 테이블("cache")의 위치는 dynamic_cache_memory 포인터를 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-161">The location of this translation table (“cache”) is set with the dynamic_cache_memory pointer.</span></span> <span data-ttu-id="66d80-162">이 영역은 4바이트의 정렬된 버퍼 공간이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-162">This area must be a 4 byte aligned buffer space.</span></span> <span data-ttu-id="66d80-163">테이블 크기(또는 항목 수)는 캐시 크기인 dynamic_cache_size를 NAT 테이블 항목으로 나눠서 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-163">The size of the table (or number of entries) is determined by dividing the cache size dynamic_cache_size by the size of a NAT table entry.</span></span> <span data-ttu-id="66d80-164">테이블은 ***nx_nat.h* 에 정의된 NX_NAT_MIN_ENTRY_COUNT로 지정된 항목의 최소 수만큼 충분히 커야 합니다. 기본값은 3입니다.**</span><span class="sxs-lookup"><span data-stu-id="66d80-164">The table must be large enough for the minimal number of entries specified by **NX_NAT_MIN_ENTRY_COUNT which is defined in *nx_nat.h*. The default value is 3.**</span></span>

<span data-ttu-id="66d80-165">NetX Duo NAT 변환 테이블의 모든 동적 항목에 대한 시간 제한은 *nx_nat. h* 에 정의된 NX_NAT_ENTRY_RESPONSE_TIMEOUT으로 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-165">The timeout for all dynamic entries in the NetX Duo NAT translation table are initialized to NX_NAT_ENTRY_RESPONSE_TIMEOUT which is defined in *nx_nat.h*.</span></span> <span data-ttu-id="66d80-166">RFC 2663에서 권장하는 대로 기본값은 4분(또는 100mHz 프로세서의 경우 240 시스템 틱)입니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-166">The default value is 4 minutes (or 240 system ticks for a 100 mHz processor) as recommended by RFC 2663.</span></span> <span data-ttu-id="66d80-167">NetX Duo NAT는 테이블의 동적 항목과 일치하는 패킷을 받거나 보낼 때마다 해당 항목의 시간 제한이 NX_NAT_ENTRY_RESPONSE_TIMEOUT으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-167">Each time NetX Duo NAT receives or sends a packet matching a dynamic entry in the table it resets that entry’s time out to NX_NAT_ENTRY_RESPONSE_TIMEOUT.</span></span> <span data-ttu-id="66d80-168">테이블을 검색할 때 NetX Duo NAT는 테이블에서 만료된 항목을 확인하고 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-168">When searching the table, NetX Duo NAT will also check the table for expired entries and delete them.</span></span>

<span data-ttu-id="66d80-169">테이블에서 인바운드 항목을 고정 항목으로 만들기 위해(예: 로컬 네트워크의 서버에 대해) NetX Duo NAT는 *nx_nat_inbound_entry_create* 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-169">To create inbound entries as static in the table e.g. for servers on the local network, NetX Duo NAT provides the *nx_nat_inbound_entry_create* service.</span></span> <span data-ttu-id="66d80-170">테이블 항목에서 로컬 호스트 연결을 고정으로 정의하는 경우에는 만료되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-170">If a table entry defines the local host connection as static, it never expires.</span></span>

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr,
    ULONG local_ip_address, USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

<span data-ttu-id="66d80-171">이 서비스는 [4장 - 서비스 설명](chapter4.md)에 자세히 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-171">This service is described in more detail in [Chapter 4 - Description of Services](chapter4.md)</span></span>

<span data-ttu-id="66d80-172">런타임 중에 변환 테이블이 가득 차서 더 이상 항목을 추가할 수 없는 경우 NetX Duo NAT는 항목이 NAT 인스턴스에 등록될 때 NAT 애플리케이션에 캐시 가득 참 콜백을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-172">During runtime, if the translation table is full and no more entries can be added, NetX Duo NAT will notify the NAT application with a cache full callback if one is registered with the NAT instance.</span></span> <span data-ttu-id="66d80-173">이는 *nx_nat_cache_notify_set* 서비스를 사용하여 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-173">This is done using the *nx_nat_cache_notify_set* service:</span></span>

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)(NX_NAT_DEVICE *nat_ptr));
```

<span data-ttu-id="66d80-174">이 서비스에 대한 자세한 내용은 [4장 - 서비스 설명](chapter4.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66d80-174">See [Chapter 4 - Description of Services](chapter4.md) for more details about this service.</span></span>

## <a name="nat-packet-processing-in-netx-duo"></a><span data-ttu-id="66d80-175">NetX Duo의 NAT 패킷 처리</span><span class="sxs-lookup"><span data-stu-id="66d80-175">NAT Packet Processing in NetX Duo</span></span>

<span data-ttu-id="66d80-176">NetX Duo NAT는 IPv4 라우터에서 사용하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-176">NetX Duo NAT is intended for use on an IPv4 router.</span></span> <span data-ttu-id="66d80-177">NAT가 작동하려면 NAT 서버에 패킷을 전달하도록 NetX Duo를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-177">For NAT to work, NetX Duo must be configured for forwarding packets to the NAT server.</span></span> <span data-ttu-id="66d80-178">이 작업을 수행하는 방법은 NetX Duo NAT 설치의 2장을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66d80-178">See Chapter 2 on NetX Duo NAT installation for how to do so.</span></span> <span data-ttu-id="66d80-179">그런 다음, NAT 서버는 네트워크의 호스트에 대해 패킷을 '사용'(전달 시도)하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-179">The NAT server then indicates if it will ‘consume’ (attempt to forward) the packet to a host on either of its networks.</span></span> <span data-ttu-id="66d80-180">패킷을 사용하지 않을 경우 패킷은 일반적으로 패킷을 처리하는 NetX Duo에 '반환'됩니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-180">If it will not consume the packet, the packet is ‘returned’ to NetX Duo to process the packet as it normally would.</span></span>

<span data-ttu-id="66d80-181">NAT 서버가 NetX Duo에서 전달되는 패킷을 받으면 패킷이 인바운드인지 또는 아웃바운드인지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-181">When the NAT server receives a packet to forward from NetX Duo, it determines if the packet is inbound or outbound.</span></span>

<span data-ttu-id="66d80-182">아웃바운드 패킷의 경우 NAT 서버는 패킷 IP 헤더 원본 주소와 포트를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-182">For outbound packets, the NAT server checks the packet IP header source address and port.</span></span> <span data-ttu-id="66d80-183">이전에 이 호스트에서 동일한 대상에 대해 보낸 패킷의 항목이 변환 테이블에 포함되지 않은 경우 NAT는 고유한 전역 원본 IP 주소를 포함하는 새 항목(연결에 대한 포트)을 만들고 이 새 IP address:port를 사용하여 패킷 헤더를 외부 네트워크에 전송하기 전에 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-183">If the translation table does not contain an entry for a packet previously sent by this host for the same destination, NAT will create a new entry which will contain a unique global source IP address:port for the connection, and modify the packet headers with this new IP address:port before sending it onto the external network.</span></span>

<span data-ttu-id="66d80-184">인바운드 패킷의 경우 NAT 서버는 패킷 대상 IP address:port와 일치하는 외부 IP address:port를 사용하여 변환 테이블에서 이전 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-184">For inbound packets, the NAT server looks for a previous entry in its translation table with an external IP address: port matching the packet destination IP address: port.</span></span> <span data-ttu-id="66d80-185">일치하는 항목이 없는 경우 대상 address:port가 로컬 네트워크의 서버에 대한 외부 주소인 경우를 제외하고는 패킷을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-185">If no match is found, it will discard the packet unless the destination address: port is the external address for server on the local network.</span></span> <span data-ttu-id="66d80-186">일치하는 항목을 찾으면 패킷 헤더의 외부 대상 IP address:port를 개인 IP address:port로 바꾸고 패킷을 로컬 네트워크를 통해 의도된 비공개 호스트로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-186">If it does find a match, it will replace the packet header’s external destination IP address: port with the private IP address: port and send the packet onto the local network to the intended private host.</span></span>

<span data-ttu-id="66d80-187">NetX Duo NAT는 외부 호스트와 연결되는 로컬 호스트를 위해 고유한 로컬 address:port 연결을 만드는 데 다양한 TCP, UDP 및 ICMP 변환 포트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-187">NetX Duo NAT uses a range of TCP, UDP and ICMP translation ports for creating unique local address: port connections for local hosts connecting with outside hosts.</span></span> <span data-ttu-id="66d80-188">*nx_nat.h* 에 정의된 다음과 같은 사용자 구성 가능한 옵션이 각 프로토콜에 대한 범위를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-188">The following user configurable options, defined in *nx_nat.h,* define the range for each protocol:</span></span>

```C
NX_NAT_START_TCP_PORT

NX_NAT_END_TCP_PORT

NX_NAT_START_UDP_PORT

NX_NAT_END_UDP_PORT

NX_NAT_START_ICMP_QUERY_ID

NX_NAT_END_ICMP_QUERY_ID
```

## <a name="nat-requirements-and-constraints"></a><span data-ttu-id="66d80-189">NAT 요구 사항 및 제약 조건</span><span class="sxs-lookup"><span data-stu-id="66d80-189">NAT Requirements and Constraints</span></span>

<span data-ttu-id="66d80-190">NetX Duo NAT에는 NetX Duo 5.8 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-190">NetX Duo NAT requires NetX Duo 5.8 or later.</span></span> <span data-ttu-id="66d80-191">NAT 애플리케이션을 사용하려면 단일 IP 인스턴스와 내부 및 외부 실제 네트워크에 대한 인터페이스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-191">The NAT application requires creation of a single IP instance and an interface to the internal and external physical network.</span></span>

<span data-ttu-id="66d80-192">제약 조건:</span><span class="sxs-lookup"><span data-stu-id="66d80-192">Constraints:</span></span>

- <span data-ttu-id="66d80-193">NetX Duo NAT는 TCP, UDP 및 ICMP를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-193">NetX Duo NAT supports TCP, UDP and ICMP.</span></span> <span data-ttu-id="66d80-194">IGMP는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-194">IGMP is not supported.</span></span>
- <span data-ttu-id="66d80-195">NetX Duo NAT는 IPv6 주소 지정을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-195">NetX Duo NAT does not support IPv6 addressing.</span></span>
- <span data-ttu-id="66d80-196">NetX Duo NAT는 DNS 또는 DHCP 서비스를 포함하지 않습니다. 단, NetX Duo NAT가 해당 서비스를 NAT 작업과 통합할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-196">NetX Duo NAT does not include DNS or DHCP services, although NetX Duo NAT can integrate those services with its NAT operations.</span></span>

## <a name="rfcs-supported-by-netx-duo-nat"></a><span data-ttu-id="66d80-197">NetX Duo NAT에서 지원되는 RFC</span><span class="sxs-lookup"><span data-stu-id="66d80-197">RFCs Supported by NetX Duo NAT</span></span>

<span data-ttu-id="66d80-198">NetX Duo NAT 구현은 다음 RFC에 제공된 정보를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="66d80-198">NetX Duo NAT implementation is based on information presented in the following RFCs:</span></span>

- <span data-ttu-id="66d80-199">RFC 2663: IP NAT(Network Address Translator) 용어 및 고려 사항</span><span class="sxs-lookup"><span data-stu-id="66d80-199">RFC 2663: IP Network Address Translator (NAT) Terminology and Considerations</span></span>
- <span data-ttu-id="66d80-200">RFC 3022: 기존 IP NAT(Network Address Translation)</span><span class="sxs-lookup"><span data-stu-id="66d80-200">RFC 3022: Traditional IP Netowrk Address Translator (Traditional NAT)</span></span>
- <span data-ttu-id="66d80-201">RFC 4787: 유니캐스트 UDP의 NAT(Network Address Translation) 동작 요구 사항</span><span class="sxs-lookup"><span data-stu-id="66d80-201">RFC 4787: Network Address Translation (NAT) Behavioral Requirements for Unicast UDP</span></span>
