---
title: Azure RTOS NetX 이해
description: Azure RTOS NetX는 고성능으로 구현된 TCP/IP 프로토콜 표준으로, Azure RTOS ThreadX와 완전히 통합되며 지원되는 모든 프로세서에 사용할 수 있습니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 7c864c23f019e4841ddb3096fde663c8039baf44
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171321"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="d76d4-103">Azure RTOS NetX 개요</span><span class="sxs-lookup"><span data-stu-id="d76d4-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="d76d4-104">Azure RTOS NetX는 특별히 긴밀하게 포함된 실시간 및 IoT 애플리케이션용으로 설계된 산업용 TCP/IP IPv4 포함 네트워크 스택입니다.</span><span class="sxs-lookup"><span data-stu-id="d76d4-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="d76d4-105">Azure RTOS NetX는 Microsoft의 원래 IPv4 네트워크 스택으로, 기본적으로 Azure RTOS의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="d76d4-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="d76d4-106">NetX는 IPv4, TCP, UDP 등의 핵심 네트워크 프로토콜과 함께 포함된 애플리케이션을 제공하고 더 높은 수준의 추가 기능 프로토콜을 완벽하게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d76d4-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="d76d4-107">Azure RTOS NetX는 적은 공간, 빠른 실행 및 뛰어난 사용 편의성을 제공하므로 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="d76d4-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="d76d4-108">API 프로토콜</span><span class="sxs-lookup"><span data-stu-id="d76d4-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="d76d4-109">TELNET</span><span class="sxs-lookup"><span data-stu-id="d76d4-109">TELNET</span></span>

* <span data-ttu-id="d76d4-110">최소 0.5KB 및 0.3KB의 RAM 공간.</span><span class="sxs-lookup"><span data-stu-id="d76d4-110">Minimal 0.5 KB and 0.3 KB RAM footprint.</span></span>
* <span data-ttu-id="d76d4-111">클라이언트 및 서버 지원.</span><span class="sxs-lookup"><span data-stu-id="d76d4-111">Client and server support.</span></span>

### <a name="auto-ip"></a><span data-ttu-id="d76d4-112">자동 IP</span><span class="sxs-lookup"><span data-stu-id="d76d4-112">Auto IP</span></span>

* <span data-ttu-id="d76d4-113">자동 IPv4 주소 할당.</span><span class="sxs-lookup"><span data-stu-id="d76d4-113">Automatic IPv4 address assignment.</span></span>
* <span data-ttu-id="d76d4-114">최소 1.2KB, 300바이트의 RAM.</span><span class="sxs-lookup"><span data-stu-id="d76d4-114">Minimal 1.2 KB, 300 bytes of RAM.</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="d76d4-115">HTTP - HTTP(Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="d76d4-115">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="d76d4-116">최소 2.8KB~4.8KB FLASH, 0.4KB~1.0KB RAM 공간.</span><span class="sxs-lookup"><span data-stu-id="d76d4-116">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint.</span></span>
* <span data-ttu-id="d76d4-117">클라이언트 및 서버 지원.</span><span class="sxs-lookup"><span data-stu-id="d76d4-117">Client and server support.</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="d76d4-118">SMTP - SMTP(Simple Mail Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="d76d4-118">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="d76d4-119">최소 4.1KB 및 0.6KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="d76d4-119">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="d76d4-120">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="d76d4-120">Client support</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="d76d4-121">DHCP - DHCP(Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="d76d4-121">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="d76d4-122">최소 3.6KB ~ 4.6KB FLASH, 2.7KB RAM 공간</span><span class="sxs-lookup"><span data-stu-id="d76d4-122">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="d76d4-123">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="d76d4-123">Client and server support</span></span>
* <span data-ttu-id="d76d4-124">IPv4 지원</span><span class="sxs-lookup"><span data-stu-id="d76d4-124">IPv4 support</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="d76d4-125">P0P3 - POP3(Post Office Protocol Version 3)</span><span class="sxs-lookup"><span data-stu-id="d76d4-125">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="d76d4-126">최소 8.1KB 및 1.4KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="d76d4-126">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="d76d4-127">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="d76d4-127">Client support</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="d76d4-128">SNMP - SNMP(Simple Network Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="d76d4-128">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="d76d4-129">최소 10.9KB 및 2.6KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="d76d4-129">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="d76d4-130">VI, V2 및 V3에 대한 에이전트 지원</span><span class="sxs-lookup"><span data-stu-id="d76d4-130">Agent support for VI, V2, and V3</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="d76d4-131">FTP, TFTP - FTP(파일 전송 프로토콜), TFTP(Trivial File Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="d76d4-131">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="d76d4-132">FTP 최소 1.8KB ~ 7.2KB FLASH, 0.6KB ~ 2.1KB RAM 공간</span><span class="sxs-lookup"><span data-stu-id="d76d4-132">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="d76d4-133">TFTP 최소 1.7KB ~ 2.4KB FLASH, 0.3KB ~ 1.8KB RAM 공간</span><span class="sxs-lookup"><span data-stu-id="d76d4-133">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="d76d4-134">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="d76d4-134">Client and server support</span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="d76d4-135">PPP - PPP(지점 간 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="d76d4-135">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="d76d4-136">최소 7.1KB 및 3.8KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="d76d4-136">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="d76d4-137">안정적이고 신뢰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d76d4-137">Dependable and reliable.</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="d76d4-138">SNTP - SNTP(Simple Network Time Protocol)</span><span class="sxs-lookup"><span data-stu-id="d76d4-138">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="d76d4-139">최소 4KB 및 0.5KB RAM</span><span class="sxs-lookup"><span data-stu-id="d76d4-139">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="d76d4-140">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="d76d4-140">Client support</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="d76d4-141">Azure RTOS NetX API</span><span class="sxs-lookup"><span data-stu-id="d76d4-141">Azure RTOS NetX API</span></span>

* <span data-ttu-id="d76d4-142">빠르고 복사 없는 API 구현</span><span class="sxs-lookup"><span data-stu-id="d76d4-142">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="d76d4-143">레거시 소켓 코드 포팅을 위한 선택적 BSD 계층</span><span class="sxs-lookup"><span data-stu-id="d76d4-143">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="d76d4-144">IGMP - IGMP(Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="d76d4-144">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="d76d4-145">최소 2.5KB FLASH</span><span class="sxs-lookup"><span data-stu-id="d76d4-145">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="d76d4-146">IPv4 멀티캐스트 그룹 지원</span><span class="sxs-lookup"><span data-stu-id="d76d4-146">IPv4 multicast group support</span></span>
* <span data-ttu-id="d76d4-147">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="d76d4-147">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="d76d4-148">선택적 IGMP 통계</span><span class="sxs-lookup"><span data-stu-id="d76d4-148">Optional IGMP statistics</span></span>
* <span data-ttu-id="d76d4-149">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="d76d4-149">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="d76d4-150">UDP - UDP(사용자 데이터그램 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="d76d4-150">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="d76d4-151">최소 2.5KB FLASH, 소켓당 124 소켓 바이트의 RAM</span><span class="sxs-lookup"><span data-stu-id="d76d4-151">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="d76d4-152">빠른 근거리 통신 속도 TCP 패킷 처리:</span><span class="sxs-lookup"><span data-stu-id="d76d4-152">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="d76d4-153">100Mbps 이더넷의 RX 95Mbps, MCU @100MHz, 14% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="d76d4-153">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="d76d4-154">100Mbps 이더넷의 TX 94Mbps, MCU @100MHz, 10% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="d76d4-154">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="d76d4-155">UDP Fast Path™ 기술</span><span class="sxs-lookup"><span data-stu-id="d76d4-155">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="d76d4-156">UDP 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="d76d4-156">No limits on the number of UDP</span></span>
* <span data-ttu-id="d76d4-157">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="d76d4-157">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="d76d4-158">소켓 수신 시 선택적 일시 중단</span><span class="sxs-lookup"><span data-stu-id="d76d4-158">Optional suspension on socket receive</span></span>
* <span data-ttu-id="d76d4-159">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="d76d4-159">Optional timeout on all suspension</span></span>
* <span data-ttu-id="d76d4-160">선택적 UDP 통계</span><span class="sxs-lookup"><span data-stu-id="d76d4-160">Optional UDP statistics</span></span>
* <span data-ttu-id="d76d4-161">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="d76d4-161">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="d76d4-162">TCP - TCP(Transmission Control Protocol)</span><span class="sxs-lookup"><span data-stu-id="d76d4-162">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="d76d4-163">최소 10.5KB ~ 12.5KB FLASH, 소켓당 280바이트의 RAM</span><span class="sxs-lookup"><span data-stu-id="d76d4-163">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="d76d4-164">빠른 근거리 통신 속도 TCP 패킷 처리:</span><span class="sxs-lookup"><span data-stu-id="d76d4-164">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="d76d4-165">100Mbps 이더넷의 RX 93Mbps, MCU @100MHz, 20% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="d76d4-165">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="d76d4-166">100Mbps 이더넷의 TX 94Mbps, MCU @100MHz, 27% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="d76d4-166">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="d76d4-167">안정적인 연결</span><span class="sxs-lookup"><span data-stu-id="d76d4-167">Reliable connection</span></span>
* <span data-ttu-id="d76d4-168">TCP 소켓 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="d76d4-168">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="d76d4-169">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="d76d4-169">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="d76d4-170">소켓 수신/전송 시 선택적 일시 중단</span><span class="sxs-lookup"><span data-stu-id="d76d4-170">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="d76d4-171">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="d76d4-171">Optional timeout on all suspension</span></span>
* <span data-ttu-id="d76d4-172">선택적 TCP 통계</span><span class="sxs-lookup"><span data-stu-id="d76d4-172">Optional TCP statistics</span></span>
* <span data-ttu-id="d76d4-173">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="d76d4-173">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="d76d4-174">ICMP - ICMP(Internet Control Message Protocol)</span><span class="sxs-lookup"><span data-stu-id="d76d4-174">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="d76d4-175">최소 2.5KB FLASH</span><span class="sxs-lookup"><span data-stu-id="d76d4-175">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="d76d4-176">IPv4 지원</span><span class="sxs-lookup"><span data-stu-id="d76d4-176">IPv4 support</span></span>
* <span data-ttu-id="d76d4-177">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="d76d4-177">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="d76d4-178">Ping 요청 및 Ping 응답</span><span class="sxs-lookup"><span data-stu-id="d76d4-178">Ping request and ping response</span></span>
* <span data-ttu-id="d76d4-179">Ping 요청 시 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="d76d4-179">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="d76d4-180">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="d76d4-180">Optional timeout on all suspension</span></span>
* <span data-ttu-id="d76d4-181">선택적 ICMP 통계</span><span class="sxs-lookup"><span data-stu-id="d76d4-181">Optional ICMP statistics</span></span>
* <span data-ttu-id="d76d4-182">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="d76d4-182">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="d76d4-183">IPv4 - IP(인터넷 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="d76d4-183">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="d76d4-184">최소 3.5KB~8.5KB FLASH, 2KB~3KB의 RAM 공간.</span><span class="sxs-lookup"><span data-stu-id="d76d4-184">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint.</span></span>
* <span data-ttu-id="d76d4-185">Piconet™ 아키텍처.</span><span class="sxs-lookup"><span data-stu-id="d76d4-185">Piconet™ Architecture.</span></span>
* <span data-ttu-id="d76d4-186">빠른 근거리 통신 속도 성능.</span><span class="sxs-lookup"><span data-stu-id="d76d4-186">Fast, near wirespeed performance.</span></span>
* <span data-ttu-id="d76d4-187">여러 인터페이스 지원.</span><span class="sxs-lookup"><span data-stu-id="d76d4-187">Multiple interface support.</span></span>
* <span data-ttu-id="d76d4-188">다중 홈 지원.</span><span class="sxs-lookup"><span data-stu-id="d76d4-188">Multi-homed support.</span></span>
* <span data-ttu-id="d76d4-189">정적 라우팅 지원.</span><span class="sxs-lookup"><span data-stu-id="d76d4-189">Static routing support.</span></span>
* <span data-ttu-id="d76d4-190">IP 조각화/리어셈블리 지원.</span><span class="sxs-lookup"><span data-stu-id="d76d4-190">IP fragmentation/reassembly support.</span></span>
* <span data-ttu-id="d76d4-191">IPv4 지원.</span><span class="sxs-lookup"><span data-stu-id="d76d4-191">IPv4 Support.</span></span>
* <span data-ttu-id="d76d4-192">IXIA IxANVL 유효성 검사 완료.</span><span class="sxs-lookup"><span data-stu-id="d76d4-192">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="d76d4-193">단계 II 준비 로고 인증.</span><span class="sxs-lookup"><span data-stu-id="d76d4-193">Phase II Ready Logo Certification.</span></span>
* <span data-ttu-id="d76d4-194">선택적 IP 통계.</span><span class="sxs-lookup"><span data-stu-id="d76d4-194">Optional IP statistics.</span></span>
* <span data-ttu-id="d76d4-195">잘 정의된 직관적인 물리적 계층 드라이버 인터페이스.</span><span class="sxs-lookup"><span data-stu-id="d76d4-195">Well defined, intuitive physical layer driver interface.</span></span>
* <span data-ttu-id="d76d4-196">Azure RTOS TraceX를 통한 시스템 수준 추적.</span><span class="sxs-lookup"><span data-stu-id="d76d4-196">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="d76d4-197">ARP/RARP - ARP(주소 확인 프로토콜), RARP(역주소 확인 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="d76d4-197">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="d76d4-198">최소 1.7KB FLASH, RAM 크기.</span><span class="sxs-lookup"><span data-stu-id="d76d4-198">Minimal 1.7 KB FLASH, RAM size.</span></span>
* <span data-ttu-id="d76d4-199">32비트의 동적 확인 IPv4 및 48비트 MAC 주소.</span><span class="sxs-lookup"><span data-stu-id="d76d4-199">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses.</span></span>
* <span data-ttu-id="d76d4-200">IXIA IxANVL 유효성 검사 완료.</span><span class="sxs-lookup"><span data-stu-id="d76d4-200">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="d76d4-201">유연한 사용자 정의 ARP 캐시.</span><span class="sxs-lookup"><span data-stu-id="d76d4-201">Flexible, user-defined ARP cache.</span></span>
* <span data-ttu-id="d76d4-202">무상 ARP 지원.</span><span class="sxs-lookup"><span data-stu-id="d76d4-202">Gratuitous ARP support.</span></span>
* <span data-ttu-id="d76d4-203">애플리케이션에 의해 결정되는 선택적 ARP/RARP 통계.</span><span class="sxs-lookup"><span data-stu-id="d76d4-203">Optional ARP/RARP statistics determined by application.</span></span>
* <span data-ttu-id="d76d4-204">Azure RTOS TraceX를 통한 시스템 수준 추적.</span><span class="sxs-lookup"><span data-stu-id="d76d4-204">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="d76d4-205">이더넷, WiFi, Bluetooth LE, 15.4 등</span><span class="sxs-lookup"><span data-stu-id="d76d4-205">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="d76d4-206">상호 운용성 확인</span><span class="sxs-lookup"><span data-stu-id="d76d4-206">Interoperability verification</span></span>

<span data-ttu-id="d76d4-207">Azure RTOS NetX는 RFC 표준을 준수하며 대부분의 공급 업체에 대해 디바이스와의 완벽한 상호 운용성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d76d4-207">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="d76d4-208">또한 Azure RTOS NetX는 Azure RTOS NetX 코어 TCP/IP 프로토콜 구현에 업계 표준 IxANVL(자동화된 네트워크 유효성 검사 라이브러리)을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="d76d4-208">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="d76d4-209">고급 기술</span><span class="sxs-lookup"><span data-stu-id="d76d4-209">Advanced technology</span></span>

<span data-ttu-id="d76d4-210">Azure RTOS NetX는 다음을 포함하는 고급 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="d76d4-210">Azure RTOS NetX is advanced technology that includes the following.</span></span>
* <span data-ttu-id="d76d4-211">Piconet™ 아키텍처.</span><span class="sxs-lookup"><span data-stu-id="d76d4-211">Piconet™ architecture.</span></span>
* <span data-ttu-id="d76d4-212">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="d76d4-212">Automatic scaling.</span></span>
* <span data-ttu-id="d76d4-213">UDP Fast-Path Technology™.</span><span class="sxs-lookup"><span data-stu-id="d76d4-213">UDP Fast-Path Technology™.</span></span>
* <span data-ttu-id="d76d4-214">유연한 패킷 관리.</span><span class="sxs-lookup"><span data-stu-id="d76d4-214">Flexible packet management.</span></span>
* <span data-ttu-id="d76d4-215">복사 없는 API 및 구현.</span><span class="sxs-lookup"><span data-stu-id="d76d4-215">Zero-copy API and implementation.</span></span>
* <span data-ttu-id="d76d4-216">다중 홈 지원.</span><span class="sxs-lookup"><span data-stu-id="d76d4-216">Multi-homed support.</span></span>
* <span data-ttu-id="d76d4-217">모든 일시 중단 시 선택적 시간 제한.</span><span class="sxs-lookup"><span data-stu-id="d76d4-217">Optional timeout on all suspension.</span></span>
* <span data-ttu-id="d76d4-218">정적 라우팅 지원.</span><span class="sxs-lookup"><span data-stu-id="d76d4-218">Static routing support.</span></span>
* <span data-ttu-id="d76d4-219">Azure RTOS TraceX 시스템 분석 지원.</span><span class="sxs-lookup"><span data-stu-id="d76d4-219">Azure RTOS TraceX system analysis support.</span></span>
