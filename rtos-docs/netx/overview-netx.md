---
title: Azure RTOS NetX 이해
description: Azure RTOS NetX는 고성능으로 구현된 TCP/IP 프로토콜 표준으로, Azure RTOS ThreadX와 완전히 통합되며 지원되는 모든 프로세서에 사용할 수 있습니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 029f73b755d5c40279125fb010ec35baaaf7f38d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810399"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="e7cd0-103">Azure RTOS NetX 개요</span><span class="sxs-lookup"><span data-stu-id="e7cd0-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="e7cd0-104">Azure RTOS NetX는 특별히 긴밀하게 포함된 실시간 및 IoT 애플리케이션용으로 설계된 산업용 TCP/IP IPv4 포함 네트워크 스택입니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="e7cd0-105">Azure RTOS NetX는 Microsoft의 원래 IPv4 네트워크 스택으로, 기본적으로 Azure RTOS의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="e7cd0-106">NetX는 IPv4, TCP, UDP 등의 핵심 네트워크 프로토콜과 함께 포함된 애플리케이션을 제공하고 더 높은 수준의 추가 기능 프로토콜을 완벽하게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="e7cd0-107">Azure RTOS NetX는 적은 공간, 빠른 실행 및 뛰어난 사용 편의성을 제공하므로 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="e7cd0-108">API 프로토콜</span><span class="sxs-lookup"><span data-stu-id="e7cd0-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="e7cd0-109">TELNET</span><span class="sxs-lookup"><span data-stu-id="e7cd0-109">TELNET</span></span>

* <span data-ttu-id="e7cd0-110">최소 0.5KB 및 0.3KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="e7cd0-110">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="e7cd0-111">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-111">Client and server support</span></span>
* <span data-ttu-id="e7cd0-112">직관적인 Telnet API: *nx_telnet_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-112">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="auto-ip"></a><span data-ttu-id="e7cd0-113">자동 IP</span><span class="sxs-lookup"><span data-stu-id="e7cd0-113">Auto IP</span></span>

* <span data-ttu-id="e7cd0-114">자동 IPv4 주소 할당</span><span class="sxs-lookup"><span data-stu-id="e7cd0-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="e7cd0-115">최소 1.2KB, 300바이트의 RAM</span><span class="sxs-lookup"><span data-stu-id="e7cd0-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="e7cd0-116">직관적인 AutoIP API: *nx_autoip_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="e7cd0-117">HTTP - HTTP(Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-117">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="e7cd0-118">최소 2.8KB ~ 4.8KB FLASH, 0.4KB ~ 1.0KB RAM 공간</span><span class="sxs-lookup"><span data-stu-id="e7cd0-118">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint</span></span>
* <span data-ttu-id="e7cd0-119">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-119">Client and server support</span></span>
* <span data-ttu-id="e7cd0-120">직관적인 HTTP API: *nx_http_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-120">Intuitive HTTP APIs: *nx_http_\**</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="e7cd0-121">SMTP - SMTP(Simple Mail Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-121">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="e7cd0-122">최소 4.1KB 및 0.6KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="e7cd0-122">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="e7cd0-123">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-123">Client support</span></span>
* <span data-ttu-id="e7cd0-124">직관적인 SMTP API: *nx_smtp_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-124">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="e7cd0-125">DHCP - DHCP(Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-125">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="e7cd0-126">최소 3.6KB ~ 4.6KB FLASH, 2.7KB RAM 공간</span><span class="sxs-lookup"><span data-stu-id="e7cd0-126">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="e7cd0-127">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-127">Client and server support</span></span>
* <span data-ttu-id="e7cd0-128">IPv4 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-128">IPv4 support</span></span>
* <span data-ttu-id="e7cd0-129">직관적인 DHCP API: *nx_dhcp_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-129">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="e7cd0-130">P0P3 - POP3(Post Office Protocol Version 3)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-130">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="e7cd0-131">최소 8.1KB 및 1.4KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="e7cd0-131">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="e7cd0-132">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-132">Client support</span></span>
* <span data-ttu-id="e7cd0-133">직관적인 P0P3 API: *nx_pop3_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-133">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="e7cd0-134">SNMP - SNMP(Simple Network Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-134">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="e7cd0-135">최소 10.9KB 및 2.6KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="e7cd0-135">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="e7cd0-136">VI, V2 및 V3에 대한 에이전트 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-136">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="e7cd0-137">직관적인 SNMP API: *nx_snmp_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-137">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="e7cd0-138">FTP, TFTP - FTP(파일 전송 프로토콜), TFTP(Trivial File Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-138">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="e7cd0-139">FTP 최소 1.8KB ~ 7.2KB FLASH, 0.6KB ~ 2.1KB RAM 공간</span><span class="sxs-lookup"><span data-stu-id="e7cd0-139">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="e7cd0-140">TFTP 최소 1.7KB ~ 2.4KB FLASH, 0.3KB ~ 1.8KB RAM 공간</span><span class="sxs-lookup"><span data-stu-id="e7cd0-140">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="e7cd0-141">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-141">Client and server support</span></span>
* <span data-ttu-id="e7cd0-142">직관적인 FTP 및 TFTP API: <i>nx_ftp_ *</i> 또는 <i>nx_tftp_* </i></span><span class="sxs-lookup"><span data-stu-id="e7cd0-142">Intuitive FTP and TFTP APIs: <i>nx_ftp_ *</i> or <i>nx_tftp_*</i></span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="e7cd0-143">PPP - PPP(지점 간 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-143">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="e7cd0-144">최소 7.1KB 및 3.8KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="e7cd0-144">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="e7cd0-145">직관적인 PPP API: *nx_ppp_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-145">Intuitive PPP APIs: *nx_ppp_\**</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="e7cd0-146">SNTP - SNTP(Simple Network Time Protocol)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-146">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="e7cd0-147">최소 4KB 및 0.5KB RAM</span><span class="sxs-lookup"><span data-stu-id="e7cd0-147">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="e7cd0-148">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-148">Client support</span></span>
* <span data-ttu-id="e7cd0-149">직관적인 SNTP API: *nx_sntp_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-149">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="e7cd0-150">Azure RTOS NetX API</span><span class="sxs-lookup"><span data-stu-id="e7cd0-150">Azure RTOS NetX API</span></span>

* <span data-ttu-id="e7cd0-151">직관적이고 일관적인 API</span><span class="sxs-lookup"><span data-stu-id="e7cd0-151">Intuitive and consistent API</span></span>
* <span data-ttu-id="e7cd0-152">명사-동사 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="e7cd0-152">Noun-verb naming convention</span></span>
* <span data-ttu-id="e7cd0-153">빠르고 복사 없는 API 구현</span><span class="sxs-lookup"><span data-stu-id="e7cd0-153">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="e7cd0-154">모든 API 함수에는 Azure RTOS NetX로 쉽게 식별할 수 있도록 <i>nx_\*</i>가 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-154">All API functions have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="e7cd0-155">API 함수 차단에는 선택적 스레드 시간 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-155">Blocking API functions have an optional thread timeout</span></span>
* <span data-ttu-id="e7cd0-156">레거시 소켓 코드 포팅을 위한 선택적 BSD 계층</span><span class="sxs-lookup"><span data-stu-id="e7cd0-156">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="e7cd0-157">IGMP - IGMP(Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-157">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="e7cd0-158">최소 2.5KB FLASH</span><span class="sxs-lookup"><span data-stu-id="e7cd0-158">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="e7cd0-159">IPv4 멀티캐스트 그룹 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-159">IPv4 multicast group support</span></span>
* <span data-ttu-id="e7cd0-160">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="e7cd0-160">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="e7cd0-161">선택적 IGMP 통계</span><span class="sxs-lookup"><span data-stu-id="e7cd0-161">Optional IGMP statistics</span></span>
* <span data-ttu-id="e7cd0-162">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="e7cd0-162">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="e7cd0-163">직관적인 IGMP API: *nx_igmp_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-163">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="e7cd0-164">UDP - UDP(사용자 데이터그램 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-164">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="e7cd0-165">최소 2.5KB FLASH, 소켓당 124 소켓 바이트의 RAM</span><span class="sxs-lookup"><span data-stu-id="e7cd0-165">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="e7cd0-166">빠른 근거리 통신 속도 TCP 패킷 처리:</span><span class="sxs-lookup"><span data-stu-id="e7cd0-166">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="e7cd0-167">100Mbps 이더넷의 RX 95Mbps, MCU @100MHz, 14% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="e7cd0-167">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="e7cd0-168">100Mbps 이더넷의 TX 94Mbps, MCU @100MHz, 10% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="e7cd0-168">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="e7cd0-169">UDP Fast Path™ 기술</span><span class="sxs-lookup"><span data-stu-id="e7cd0-169">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="e7cd0-170">UDP 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="e7cd0-170">No limits on the number of UDP</span></span>
* <span data-ttu-id="e7cd0-171">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="e7cd0-171">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="e7cd0-172">소켓 수신 시 선택적 일시 중단</span><span class="sxs-lookup"><span data-stu-id="e7cd0-172">Optional suspension on socket receive</span></span>
* <span data-ttu-id="e7cd0-173">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="e7cd0-173">Optional timeout on all suspension</span></span>
* <span data-ttu-id="e7cd0-174">선택적 UDP 통계</span><span class="sxs-lookup"><span data-stu-id="e7cd0-174">Optional UDP statistics</span></span>
* <span data-ttu-id="e7cd0-175">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="e7cd0-175">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="e7cd0-176">직관적인 UDP API: *nx_udp_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-176">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="e7cd0-177">TCP - TCP(Transmission Control Protocol)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-177">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="e7cd0-178">최소 10.5KB ~ 12.5KB FLASH, 소켓당 280바이트의 RAM</span><span class="sxs-lookup"><span data-stu-id="e7cd0-178">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="e7cd0-179">빠른 근거리 통신 속도 TCP 패킷 처리:</span><span class="sxs-lookup"><span data-stu-id="e7cd0-179">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="e7cd0-180">100Mbps 이더넷의 RX 93Mbps, MCU @100MHz, 20% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="e7cd0-180">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="e7cd0-181">100Mbps 이더넷의 TX 94Mbps, MCU @100MHz, 27% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="e7cd0-181">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="e7cd0-182">안정적인 연결</span><span class="sxs-lookup"><span data-stu-id="e7cd0-182">Reliable connection</span></span>
* <span data-ttu-id="e7cd0-183">TCP 소켓 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="e7cd0-183">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="e7cd0-184">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="e7cd0-184">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="e7cd0-185">소켓 수신/전송 시 선택적 일시 중단</span><span class="sxs-lookup"><span data-stu-id="e7cd0-185">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="e7cd0-186">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="e7cd0-186">Optional timeout on all suspension</span></span>
* <span data-ttu-id="e7cd0-187">선택적 TCP 통계</span><span class="sxs-lookup"><span data-stu-id="e7cd0-187">Optional TCP statistics</span></span>
* <span data-ttu-id="e7cd0-188">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="e7cd0-188">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="e7cd0-189">직관적인 TCP API: *nx_tcp_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-189">Intuitive TCP APIs:  *nx_tcp_\**</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="e7cd0-190">ICMP - ICMP(Internet Control Message Protocol)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-190">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="e7cd0-191">최소 2.5KB FLASH</span><span class="sxs-lookup"><span data-stu-id="e7cd0-191">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="e7cd0-192">IPv4 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-192">IPv4 support</span></span>
* <span data-ttu-id="e7cd0-193">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="e7cd0-193">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="e7cd0-194">Ping 요청 및 Ping 응답</span><span class="sxs-lookup"><span data-stu-id="e7cd0-194">Ping request and ping response</span></span>
* <span data-ttu-id="e7cd0-195">Ping 요청 시 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="e7cd0-195">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="e7cd0-196">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="e7cd0-196">Optional timeout on all suspension</span></span>
* <span data-ttu-id="e7cd0-197">선택적 ICMP 통계</span><span class="sxs-lookup"><span data-stu-id="e7cd0-197">Optional ICMP statistics</span></span>
* <span data-ttu-id="e7cd0-198">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="e7cd0-198">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="e7cd0-199">직관적인 ICMP API: *nx_icmp_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-199">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="e7cd0-200">IPv4 - IP(인터넷 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-200">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="e7cd0-201">최소 3.5KB ~ 8.5KB FLASH, 2KB ~ 3KB RAM 공간</span><span class="sxs-lookup"><span data-stu-id="e7cd0-201">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="e7cd0-202">Piconet™ 아키텍처</span><span class="sxs-lookup"><span data-stu-id="e7cd0-202">Piconet™ Architecture</span></span>
* <span data-ttu-id="e7cd0-203">빠른 근거리 통신 속도 성능</span><span class="sxs-lookup"><span data-stu-id="e7cd0-203">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="e7cd0-204">여러 인터페이스 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-204">Multiple interface support</span></span>
* <span data-ttu-id="e7cd0-205">멀티홈 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-205">Multihomed support</span></span>
* <span data-ttu-id="e7cd0-206">정적 라우팅 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-206">Static routing support</span></span>
* <span data-ttu-id="e7cd0-207">IP 조각화/리어셈블리 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-207">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="e7cd0-208">IPv4 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-208">IPv4 Support</span></span>
* <span data-ttu-id="e7cd0-209">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="e7cd0-209">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="e7cd0-210">단계 II 준비 로고 인증</span><span class="sxs-lookup"><span data-stu-id="e7cd0-210">Phase II Ready Logo Certification</span></span>
* <span data-ttu-id="e7cd0-211">선택적 IP 통계</span><span class="sxs-lookup"><span data-stu-id="e7cd0-211">Optional IP statistics</span></span>
* <span data-ttu-id="e7cd0-212">잘 정의된 직관적인 물리적 계층 드라이버 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e7cd0-212">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="e7cd0-213">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="e7cd0-213">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="e7cd0-214">직관적인 IP 계층 API: *nx_ip_\** , *nxd_ip_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-214">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**</span></span>
* <span data-ttu-id="e7cd0-215">TUV 및 UL에서 IEC 61508 SIL 4, IEC 62304 클래스 C, ISO 26262 ASIL D 및 EN 50128 SW-SIL4로 사전 인증</span><span class="sxs-lookup"><span data-stu-id="e7cd0-215">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="e7cd0-216">ARP/RARP - ARP(주소 확인 프로토콜), RARP(역주소 확인 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="e7cd0-216">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="e7cd0-217">최소 1.7KB FLASH, RAM 크기</span><span class="sxs-lookup"><span data-stu-id="e7cd0-217">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="e7cd0-218">32비트의 동적 확인 IPv4 및 48비트 MAC 주소</span><span class="sxs-lookup"><span data-stu-id="e7cd0-218">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="e7cd0-219">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="e7cd0-219">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="e7cd0-220">유연한 사용자 정의 ARP 캐시</span><span class="sxs-lookup"><span data-stu-id="e7cd0-220">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="e7cd0-221">무상 ARP 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-221">Gratuitous ARP support</span></span>
* <span data-ttu-id="e7cd0-222">애플리케이션에 의해 결정되는 선택적 ARP/RARP 통계</span><span class="sxs-lookup"><span data-stu-id="e7cd0-222">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="e7cd0-223">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="e7cd0-223">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="e7cd0-224">직관적인 ARP/RARP API: *nx_arp_\** , *nx_rarp_\**</span><span class="sxs-lookup"><span data-stu-id="e7cd0-224">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="e7cd0-225">이더넷, WiFi, Bluetooth LE, 15.4 등</span><span class="sxs-lookup"><span data-stu-id="e7cd0-225">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="small-footprint"></a><span data-ttu-id="e7cd0-226">적은 공간</span><span class="sxs-lookup"><span data-stu-id="e7cd0-226">Small-footprint</span></span>

<span data-ttu-id="e7cd0-227">Azure RTOS NetX는 기본 IP 및 UDP 지원에 대한 공간이 9KB ~ 15KB로 매우 적습니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-227">Azure RTOS NetX has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="e7cd0-228">TCP 기능을 위해서는 추가적으로 10KB ~ 13KB의 명령 영역 메모리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-228">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="e7cd0-229">Azure RTOS NetX RAM 사용량은 일반적으로 2.6KB에서 3.6KB까지이며, 애플리케이션에 의해 정의되는 패킷 풀 메모리를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-229">Azure RTOS NetX RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="e7cd0-230">Azure RTOS ThreadX와 같이 Azure RTOS NetX의 크기는 애플리케이션에서 사용하는 서비스에 따라 자동으로 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-230">Like Azure RTOS ThreadX, the size of Azure RTOS NetX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="e7cd0-231">이렇게 하면 사실상 복잡한 구성 및 빌드 매개 변수가 제거되어 개발자가 더 쉽게 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-231">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="e7cd0-232">고속 실행</span><span class="sxs-lookup"><span data-stu-id="e7cd0-232">Fast execution</span></span>

<span data-ttu-id="e7cd0-233">Azure RTOS NetX는 복사 없는 패킷 송신/수신 구현을 제공하며 Azure RTOS ThreadX와 고도로 통합되어 가장 빠른 성능을 실현합니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-233">Azure RTOS NetX provides a zero-copy packet send/receive implementation and is highly integrated with Azure RTOS ThreadX to achieve the fastest possible performance.</span></span> <span data-ttu-id="e7cd0-234">예를 들어 Azure RTOS NetX는 일반적으로 프로세서 주기 중 일부만 사용하면서 80MHz 프로세서(또는 이하)에서 근거리 통신 속도 데이터 전송을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-234">For example, Azure RTOS NetX can typically achieve near wirespeed data transfers on an 80-MHz processor (or less), while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="e7cd0-235">간단하고 손쉬운 사용</span><span class="sxs-lookup"><span data-stu-id="e7cd0-235">Simple, easy-to-use</span></span>

<span data-ttu-id="e7cd0-236">Azure RTOS NetX는 사용이 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-236">Azure RTOS NetX is simple to use.</span></span> <span data-ttu-id="e7cd0-237">Azure RTOS NetX API는 직관적이고 매우 기능적입니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-237">The Azure RTOS NetX API is both intuitive and highly functional.</span></span> <span data-ttu-id="e7cd0-238">API 이름은 “대단히 이해하기 어려운” 것이 아니며, 다른 네트워킹 제품에 매우 흔한 고도로 축약된 이름도 아닌 실제 단어로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-238">The API names are made of real words and not “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="e7cd0-239">모든 Azure RTOS NetX API에는 선행 *nx_* 가 있으며 명사-동사 명명 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-239">All Azure RTOS NetX APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="e7cd0-240">또한 API 전체에 걸쳐 기능적 일관성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-240">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="e7cd0-241">예를 들어 일시 중단된 모든 API 함수는 동일한 방식으로 작동하는 선택적 시간 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-241">For example, all API functions that suspend have an optional timeout that functions in an identical manner.</span></span> <span data-ttu-id="e7cd0-242">레거시 애플리케이션의 경우 Azure RTOS NetX는 추가 BSD 소켓 호환 계층을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-242">For legacy applications, Azure RTOS NetX offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="e7cd0-243">이 계층을 통해 개발자는 수많은 네트워킹 애플리케이션을 쉽게 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-243">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="e7cd0-244">상호 운용성 확인</span><span class="sxs-lookup"><span data-stu-id="e7cd0-244">Interoperability verification</span></span>

<span data-ttu-id="e7cd0-245">Azure RTOS NetX는 RFC 표준을 준수하며 대부분의 공급 업체에 대해 디바이스와의 완벽한 상호 운용성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-245">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="e7cd0-246">또한 Azure RTOS NetX는 Azure RTOS NetX 코어 TCP/IP 프로토콜 구현에 업계 표준 IxANVL(자동화된 네트워크 유효성 검사 라이브러리)을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-246">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="e7cd0-247">고급 기술</span><span class="sxs-lookup"><span data-stu-id="e7cd0-247">Advanced technology</span></span>

<span data-ttu-id="e7cd0-248">Azure RTOS NetX는 다음을 포함하는 고급 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-248">Azure RTOS NetX is advanced technology that includes:</span></span>

* <span data-ttu-id="e7cd0-249">Piconet™ 아키텍처</span><span class="sxs-lookup"><span data-stu-id="e7cd0-249">Piconet™ architecture</span></span>
* <span data-ttu-id="e7cd0-250">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="e7cd0-250">automatic scaling</span></span>
* <span data-ttu-id="e7cd0-251">UDP Fast-Path Technology™</span><span class="sxs-lookup"><span data-stu-id="e7cd0-251">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="e7cd0-252">유연한 패킷 관리</span><span class="sxs-lookup"><span data-stu-id="e7cd0-252">flexible packet management</span></span>
* <span data-ttu-id="e7cd0-253">복사 없는 API 및 구현</span><span class="sxs-lookup"><span data-stu-id="e7cd0-253">zero-copy API and implementation</span></span>
* <span data-ttu-id="e7cd0-254">멀티홈 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-254">multihomed support</span></span>
* <span data-ttu-id="e7cd0-255">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="e7cd0-255">optional timeout on all suspension</span></span>
* <span data-ttu-id="e7cd0-256">정적 라우팅 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-256">static routing support</span></span>
* <span data-ttu-id="e7cd0-257">Azure RTOS TraceX 시스템 분석 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-257">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="e7cd0-258">가장 빠른 출시 시간</span><span class="sxs-lookup"><span data-stu-id="e7cd0-258">Fastest time-to-market</span></span>

<span data-ttu-id="e7cd0-259">Azure RTOS NetX는 설치, 학습, 사용, 디버그, 확인, 인증 및 유지 관리를 손쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-259">Azure RTOS NetX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="e7cd0-260">결과적으로 Azure RTOS NetX는 Broadcom, Gainspan 등의 많은 SoC를 포함하여 임베디드 IoT 디바이스에 가장 많이 사용되는 TCP/IP 스택 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-260">As a result, Azure RTOS NetX is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, and so forth.</span></span> <span data-ttu-id="e7cd0-261">일관적인 출시 시간 이점은 다음을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-261">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="e7cd0-262">품질 설명서 – [Azure RTOS NetX 사용자 가이드](about-this-guide.md)를 검토하고 직접 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-262">quality documentation – please review our [Azure RTOS NetX User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="e7cd0-263">전체 소스 코드 가용성</span><span class="sxs-lookup"><span data-stu-id="e7cd0-263">complete source code availability</span></span>
* <span data-ttu-id="e7cd0-264">사용하기 쉬운 API</span><span class="sxs-lookup"><span data-stu-id="e7cd0-264">easy-to-use API</span></span>
* <span data-ttu-id="e7cd0-265">포괄적인 고급 기능 세트</span><span class="sxs-lookup"><span data-stu-id="e7cd0-265">comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="e7cd0-266">하나의 간단한 라이선스</span><span class="sxs-lookup"><span data-stu-id="e7cd0-266">One Simple License</span></span>

<span data-ttu-id="e7cd0-267">사전에 사용이 허가된 디바이스에 배포하는 경우에는 소스 코드를 사용 및 테스트하는 데 비용이 들지 않으며 프로덕션 라이선스에 대한 비용도 부과되지 않습니다. 다른 모든 디바이스에는 간단한 연간 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-267">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="e7cd0-268">최고 품질의 전체 소스 코드</span><span class="sxs-lookup"><span data-stu-id="e7cd0-268">Full, highest-quality source code</span></span>

<span data-ttu-id="e7cd0-269">여러 해에 걸쳐 Azure RTOS NetX 소스 코드는 품질 및 이해 용이성의 기준을 확립했습니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-269">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="e7cd0-270">또한 파일당 하나의 함수를 포함하는 규칙을 통해 손쉬운 소스 탐색을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-270">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="e7cd0-271">가장 인기 있는 아키텍처 지원</span><span class="sxs-lookup"><span data-stu-id="e7cd0-271">Supports most popular architectures</span></span>

<span data-ttu-id="e7cd0-272">Azure RTOS NetX는 다음과 같은 고급 아키텍처를 포함하여 완벽하게 테스트되고 완전히 지원되는 가장 인기 있는 32/64비트 마이크로프로세서에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7cd0-272">Azure RTOS NetX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="e7cd0-273">**Analog Devices**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="e7cd0-273">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="e7cd0-274">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="e7cd0-274">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="e7cd0-275">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="e7cd0-275">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="e7cd0-276">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="e7cd0-276">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="e7cd0-277">**Cadence**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="e7cd0-277">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="e7cd0-278">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="e7cd0-278">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="e7cd0-279">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="e7cd0-279">**Cypress**: RISC-V</span></span>

<span data-ttu-id="e7cd0-280">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="e7cd0-280">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="e7cd0-281">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="e7cd0-281">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="e7cd0-282">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="e7cd0-282">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="e7cd0-283">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="e7cd0-283">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="e7cd0-284">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="e7cd0-284">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="e7cd0-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="e7cd0-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="e7cd0-286">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span><span class="sxs-lookup"><span data-stu-id="e7cd0-286">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="e7cd0-287">**Silicon Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="e7cd0-287">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="e7cd0-288">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="e7cd0-288">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="e7cd0-289">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="e7cd0-289">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="e7cd0-290">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="e7cd0-290">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="e7cd0-291">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="e7cd0-291">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="e7cd0-292">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="e7cd0-292">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="e7cd0-293">*나열된 모든 타이밍 및 크기 수치는 예상치이며, 개발 플랫폼에 따라 다를 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="e7cd0-293">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
