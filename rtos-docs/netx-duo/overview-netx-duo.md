---
title: Azure RTOS NetX Duo 이해
description: Azure RTOS NetX Duo는 긴밀하게 포함된 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 고급, 산업용 TCP/IP 네트워크 스택입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: e3fe3bcc602f409cc76f3be47aca865bf8116697
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171338"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="74aea-103">Azure RTOS NetX Duo 개요</span><span class="sxs-lookup"><span data-stu-id="74aea-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="74aea-104">Azure RTOS NetX Duo 임베디드 TCP/IP 네트워크 스택은 긴밀하게 포함된 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 Microsoft의 고급, 산업용 이중 IPv4 및 IPv6 TCP/IP 네트워크 스택입니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="74aea-105">NetX Duo는 IPv4, IPv6, TCP, UDP 등의 핵심 네트워크 프로토콜과 함께 포함된 애플리케이션을 제공하고 더 높은 수준의 추가 기능 프로토콜을 완벽하게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="74aea-106">Azure RTOS NetX Duo는 Azure RTOS NetX Secure IPsec 및 Azure RTOS NetX Secure SSL/TLS/DTLS를 비롯한 추가 기능형 추가 보안 제품을 통해 보안을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="74aea-107">이뿐 아니라 Azure RTOS NetX Duo는 적은 메모리 공간, 빠른 실행 및 뛰어난 사용 편의성을 제공하므로 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="74aea-108">API 프로토콜</span><span class="sxs-lookup"><span data-stu-id="74aea-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="74aea-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="74aea-109">MQTT</span></span>

* <span data-ttu-id="74aea-110">MQTT(메시징 큐 원격 분석 전송)</span><span class="sxs-lookup"><span data-stu-id="74aea-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="74aea-111">최소 2.7KB FLASH</span><span class="sxs-lookup"><span data-stu-id="74aea-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="74aea-112">자동 IP</span><span class="sxs-lookup"><span data-stu-id="74aea-112">Auto IP</span></span>

* <span data-ttu-id="74aea-113">자동 IPv4 주소 할당</span><span class="sxs-lookup"><span data-stu-id="74aea-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="74aea-114">최소 1.2KB, 300바이트의 RAM</span><span class="sxs-lookup"><span data-stu-id="74aea-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="74aea-115">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="74aea-115">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="74aea-116">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="74aea-116">HTTP 1.0</span></span>

* <span data-ttu-id="74aea-117">HTTP(Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="74aea-117">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="74aea-118">최소 2.8KB~4.8KB 플래시/0.4KB~1.0KB RAM</span><span class="sxs-lookup"><span data-stu-id="74aea-118">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="74aea-119">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-119">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="74aea-120">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="74aea-120">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="74aea-121">HTTP(Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="74aea-121">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="74aea-122">최소 3.0KB~9.5KB 플래시/0.5KB~2KB RAM</span><span class="sxs-lookup"><span data-stu-id="74aea-122">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="74aea-123">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-123">Client and server support</span></span>
* <span data-ttu-id="74aea-124">다중 수신 클라이언트 세션</span><span class="sxs-lookup"><span data-stu-id="74aea-124">Multiple incoming client sessions</span></span>
* <span data-ttu-id="74aea-125">일반 텍스트 및 암호화된 HTTPS</span><span class="sxs-lookup"><span data-stu-id="74aea-125">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="74aea-126">영구 연결 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-126">Persistent connection support</span></span>
* <span data-ttu-id="74aea-127">다중 파트 파일 업로드</span><span class="sxs-lookup"><span data-stu-id="74aea-127">Multipart file upload</span></span>
* <span data-ttu-id="74aea-128">Azure RTOS NetX Secure TLS와 완전히 통합</span><span class="sxs-lookup"><span data-stu-id="74aea-128">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="74aea-129">SMTP</span><span class="sxs-lookup"><span data-stu-id="74aea-129">SMTP</span></span>

* <span data-ttu-id="74aea-130">SMTP(Simple Mail Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="74aea-130">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="74aea-131">최소 4.1KB 및 0.6KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="74aea-131">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="74aea-132">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-132">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="74aea-133">DHCP</span><span class="sxs-lookup"><span data-stu-id="74aea-133">DHCP</span></span>

* <span data-ttu-id="74aea-134">DHCP(Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="74aea-134">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="74aea-135">최소 3.6KB~4.6KB FLASH, 2.7KB RAM 공간</span><span class="sxs-lookup"><span data-stu-id="74aea-135">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="74aea-136">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-136">Client and server support</span></span>
* <span data-ttu-id="74aea-137">IPv4 및 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-137">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="74aea-138">NAT</span><span class="sxs-lookup"><span data-stu-id="74aea-138">NAT</span></span>

* <span data-ttu-id="74aea-139">NAT(Network Address Translation)</span><span class="sxs-lookup"><span data-stu-id="74aea-139">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="74aea-140">최소 3.5KB 및 0.6KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="74aea-140">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="74aea-141">IPv4 주소 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-141">IPv4 address support</span></span>
* <span data-ttu-id="74aea-142">NAT는 Azure RTOS NetX Duo에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-142">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="74aea-143">SNMP</span><span class="sxs-lookup"><span data-stu-id="74aea-143">SNMP</span></span>

* <span data-ttu-id="74aea-144">SNMP(Simple Network Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="74aea-144">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="74aea-145">최소 10.9KB 및 2.6KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="74aea-145">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="74aea-146">VI, V2 및 V3에 대한 에이전트 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-146">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="74aea-147">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="74aea-147">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="74aea-148">DNS(Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="74aea-148">Domain Name System (DNS)</span></span>
* <span data-ttu-id="74aea-149">mDNS(Multicast Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="74aea-149">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="74aea-150">DNS-SD(DNS 기반 서비스 검색)</span><span class="sxs-lookup"><span data-stu-id="74aea-150">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="74aea-151">DNS 최소 2.4KB~3KB FLASH, 1KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="74aea-151">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="74aea-152">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-152">Client support</span></span>
* <span data-ttu-id="74aea-153">mDNS 및 DNS-SD는 Azure RTOS NetX Duo에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-153">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="p0p3"></a><span data-ttu-id="74aea-154">P0P3</span><span class="sxs-lookup"><span data-stu-id="74aea-154">P0P3</span></span>

* <span data-ttu-id="74aea-155">POP3(Post Office Protocol 버전 3)</span><span class="sxs-lookup"><span data-stu-id="74aea-155">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="74aea-156">최소 8.1KB 및 1.4KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="74aea-156">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="74aea-157">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-157">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="74aea-158">TELNET</span><span class="sxs-lookup"><span data-stu-id="74aea-158">TELNET</span></span>

* <span data-ttu-id="74aea-159">최소 0.5KB 및 0.3KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="74aea-159">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="74aea-160">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-160">Client and server support</span></span>
* <span data-ttu-id="74aea-161">직관적인 Telnet API: *nx_telnet_\**</span><span class="sxs-lookup"><span data-stu-id="74aea-161">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="74aea-162">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="74aea-162">FTP, TFTP</span></span>

* <span data-ttu-id="74aea-163">FTP(파일 전송 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="74aea-163">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="74aea-164">TFTP(Trivial File Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="74aea-164">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="74aea-165">FTP 최소 1.8KB~7.2KB FLASH, 0.6KB~2.1KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="74aea-165">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="74aea-166">TFTP 최소 1.7KB~2.4KB FLASH, 0.3KB~1.8KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="74aea-166">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="74aea-167">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-167">Client and server support</span></span>
* <span data-ttu-id="74aea-168">직관적인 FTP 및 TFTP API: *nx_ftp_\** 또는 *nx_tftp_\**</span><span class="sxs-lookup"><span data-stu-id="74aea-168">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="74aea-169">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="74aea-169">PPP, PPPoE</span></span>

* <span data-ttu-id="74aea-170">PPP(지점 간 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="74aea-170">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="74aea-171">PPPoE(이더넷을 통한 지점 간 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="74aea-171">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="74aea-172">최소 7.1KB 및 3.8KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="74aea-172">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="74aea-173">직관적인 PPP API: *nx_ppp_\**</span><span class="sxs-lookup"><span data-stu-id="74aea-173">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="74aea-174">PPPoE는 Azure RTOS NetX Duo에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-174">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="74aea-175">SNTP</span><span class="sxs-lookup"><span data-stu-id="74aea-175">SNTP</span></span>

* <span data-ttu-id="74aea-176">SNTP(Simple Network Time Protocol)</span><span class="sxs-lookup"><span data-stu-id="74aea-176">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="74aea-177">최소 4KB 및 0.5KB RAM</span><span class="sxs-lookup"><span data-stu-id="74aea-177">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="74aea-178">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-178">Client support</span></span>
* <span data-ttu-id="74aea-179">직관적인 SNTP API: *nx_sntp_\**</span><span class="sxs-lookup"><span data-stu-id="74aea-179">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="74aea-180">Azure RTOS NetX Duo API</span><span class="sxs-lookup"><span data-stu-id="74aea-180">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="74aea-181">직관적이고 일관성 있는 API</span><span class="sxs-lookup"><span data-stu-id="74aea-181">Intuitive and consistent API</span></span>
* <span data-ttu-id="74aea-182">명사-동사 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="74aea-182">Noun-verb naming convention</span></span>
* <span data-ttu-id="74aea-183">빠르고 복사 없는 API 구현</span><span class="sxs-lookup"><span data-stu-id="74aea-183">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="74aea-184">모든 API에는 Azure RTOS NetX로 쉽게 식별할 수 있도록 <i>nx_\*</i>가 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-184">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="74aea-185">차단 API에 선택적 스레드 시간 제한 적용</span><span class="sxs-lookup"><span data-stu-id="74aea-185">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="74aea-186">자세한 내용은 [Azure RTOS NetX Duo 사용자 가이드](about-this-guide.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74aea-186">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="74aea-187">레거시 소켓 코드 포팅을 위한 선택적 BSD 계층</span><span class="sxs-lookup"><span data-stu-id="74aea-187">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="74aea-188">IGMP</span><span class="sxs-lookup"><span data-stu-id="74aea-188">IGMP</span></span>

* <span data-ttu-id="74aea-189">IGMP(Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="74aea-189">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="74aea-190">최소 2.5KB FLASH</span><span class="sxs-lookup"><span data-stu-id="74aea-190">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="74aea-191">IPv4 멀티캐스트 그룹 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-191">IPv4 multicast group support</span></span>
* <span data-ttu-id="74aea-192">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="74aea-192">IXIA IxANVL validated</span></span>
* <span data-ttu-id="74aea-193">선택적 IGMP 통계</span><span class="sxs-lookup"><span data-stu-id="74aea-193">Optional IGMP statistics</span></span>
* <span data-ttu-id="74aea-194">Azure RTOS ThreadX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="74aea-194">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="74aea-195">직관적인 IGMP API: *nx_igmp_\**</span><span class="sxs-lookup"><span data-stu-id="74aea-195">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="74aea-196">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="74aea-196">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="74aea-197">DTLS(데이터그램 전송 계층 보안) 1.0 및 1.2</span><span class="sxs-lookup"><span data-stu-id="74aea-197">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="74aea-198">최소 11KB FLASH</span><span class="sxs-lookup"><span data-stu-id="74aea-198">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="74aea-199">고속, 소프트웨어 RSA 2048비트 키 크기 ~1초 @120MHz</span><span class="sxs-lookup"><span data-stu-id="74aea-199">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="74aea-200">간소화된 X.509 구현</span><span class="sxs-lookup"><span data-stu-id="74aea-200">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="74aea-201">Azure RTOS NetX Duo UDP 소켓과 완전히 통합</span><span class="sxs-lookup"><span data-stu-id="74aea-201">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="74aea-202">하드웨어 암호화 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-202">Hardware Crypto Support</span></span>
* <span data-ttu-id="74aea-203">소프트웨어 암호화 지원: RSA(모든 키 크기), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2(SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="74aea-203">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="74aea-204">ECDSA(서명) 및 ECDH(암호화)를 사용하는 ECC(Elliptic Curve Cryptography)(P-곡선 192/224/256/384/521 포함)</span><span class="sxs-lookup"><span data-stu-id="74aea-204">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="74aea-205">암호화된 키 지원(하드웨어 종속)</span><span class="sxs-lookup"><span data-stu-id="74aea-205">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="74aea-206">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="74aea-206">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="74aea-207">TLS(전송 계층 보안) 1.0, 1.1 및 1.2</span><span class="sxs-lookup"><span data-stu-id="74aea-207">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="74aea-208">최소 8.8KB FLASH</span><span class="sxs-lookup"><span data-stu-id="74aea-208">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="74aea-209">고속, 소프트웨어 RSA 2048비트 키 크기 ~1초 @120MHz</span><span class="sxs-lookup"><span data-stu-id="74aea-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="74aea-210">간소화된 X.509 구현</span><span class="sxs-lookup"><span data-stu-id="74aea-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="74aea-211">Azure RTOS NetX Duo TCP 소켓과 완전히 통합</span><span class="sxs-lookup"><span data-stu-id="74aea-211">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="74aea-212">하드웨어 암호화 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="74aea-213">소프트웨어 암호화 지원: RSA(모든 키 크기), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2(SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="74aea-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="74aea-214">ECDSA(서명) 및 ECDH(암호화)를 사용하는 ECC(Elliptic Curve Cryptography)(P-곡선 192/224/256/384/521 포함)</span><span class="sxs-lookup"><span data-stu-id="74aea-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="74aea-215">암호화된 키 지원(하드웨어 종속)</span><span class="sxs-lookup"><span data-stu-id="74aea-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="74aea-216">ICMP</span><span class="sxs-lookup"><span data-stu-id="74aea-216">ICMP</span></span>

* <span data-ttu-id="74aea-217">ICMP(Internet Control Message Protocol)</span><span class="sxs-lookup"><span data-stu-id="74aea-217">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="74aea-218">최소 2.5KB FLASH</span><span class="sxs-lookup"><span data-stu-id="74aea-218">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="74aea-219">IPv4 및 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-219">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="74aea-220">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="74aea-220">IXIA IxANVL validated</span></span>
* <span data-ttu-id="74aea-221">Ping 요청 및 Ping 응답</span><span class="sxs-lookup"><span data-stu-id="74aea-221">Ping request and ping response</span></span>
* <span data-ttu-id="74aea-222">Ping 요청 시 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="74aea-222">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="74aea-223">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="74aea-223">Optional timeout on all suspension</span></span>
* <span data-ttu-id="74aea-224">선택적 ICMP 통계</span><span class="sxs-lookup"><span data-stu-id="74aea-224">Optional ICMP statistics</span></span>
* <span data-ttu-id="74aea-225">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="74aea-225">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="74aea-226">직관적인 ICMP API: *nx_icmp_\**</span><span class="sxs-lookup"><span data-stu-id="74aea-226">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="74aea-227">UDP</span><span class="sxs-lookup"><span data-stu-id="74aea-227">UDP</span></span>

* <span data-ttu-id="74aea-228">UDP(사용자 데이터그램 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="74aea-228">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="74aea-229">최소 2.5KB FLASH, 소켓당 124 소켓 바이트의 RAM</span><span class="sxs-lookup"><span data-stu-id="74aea-229">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="74aea-230">빠른 근거리 통신 속도 TCP 패킷 처리:</span><span class="sxs-lookup"><span data-stu-id="74aea-230">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="74aea-231">100Mbps 이더넷의 RX 95Mbps, MCU @100MHz, 14% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="74aea-231">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="74aea-232">100Mbps 이더넷의 TX 94Mbps, MCU @100MHz, 10% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="74aea-232">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="74aea-233">UDP Fast Path™ 기술</span><span class="sxs-lookup"><span data-stu-id="74aea-233">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="74aea-234">UDP 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="74aea-234">No limits on the number of UDP</span></span>
* <span data-ttu-id="74aea-235">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="74aea-235">IXIA IxANVL validated</span></span>
* <span data-ttu-id="74aea-236">소켓 수신 시 선택적 일시 중단</span><span class="sxs-lookup"><span data-stu-id="74aea-236">Optional suspension on socket receive</span></span>
* <span data-ttu-id="74aea-237">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="74aea-237">Optional timeout on all suspension</span></span>
* <span data-ttu-id="74aea-238">선택적 UDP 통계</span><span class="sxs-lookup"><span data-stu-id="74aea-238">Optional UDP statistics</span></span>
* <span data-ttu-id="74aea-239">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="74aea-239">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="74aea-240">직관적인 UDP API: *nx_udp_\**</span><span class="sxs-lookup"><span data-stu-id="74aea-240">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="74aea-241">TCP</span><span class="sxs-lookup"><span data-stu-id="74aea-241">TCP</span></span>

* <span data-ttu-id="74aea-242">TCP(Transmission Control Protocol)</span><span class="sxs-lookup"><span data-stu-id="74aea-242">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="74aea-243">최소 10.5KB~12.5KB FLASH, 소켓당 280바이트의 RAM</span><span class="sxs-lookup"><span data-stu-id="74aea-243">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="74aea-244">빠른 근거리 통신 속도 TCP 패킷 처리:</span><span class="sxs-lookup"><span data-stu-id="74aea-244">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="74aea-245">100Mbps 이더넷의 RX 93Mbps, MCU @100MHz, 20% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="74aea-245">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="74aea-246">100Mbps 이더넷의 TX 94Mbps, MCU @100MHz, 27% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="74aea-246">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="74aea-247">안정적인 연결</span><span class="sxs-lookup"><span data-stu-id="74aea-247">Reliable connection</span></span>
* <span data-ttu-id="74aea-248">TCP 소켓 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="74aea-248">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="74aea-249">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="74aea-249">IXIA IxANVL validated</span></span>
* <span data-ttu-id="74aea-250">소켓 수신/전송 시 선택적 일시 중단</span><span class="sxs-lookup"><span data-stu-id="74aea-250">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="74aea-251">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="74aea-251">Optional timeout on all suspension</span></span>
* <span data-ttu-id="74aea-252">선택적 TCP 통계</span><span class="sxs-lookup"><span data-stu-id="74aea-252">Optional TCP statistics</span></span>
* <span data-ttu-id="74aea-253">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="74aea-253">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="74aea-254">직관적인 TCP API: *nx_tcp_\**</span><span class="sxs-lookup"><span data-stu-id="74aea-254">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="74aea-255">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="74aea-255">ARP/RARP</span></span>

* <span data-ttu-id="74aea-256">ARP(주소 확인 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="74aea-256">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="74aea-257">RARP(역주소 확인 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="74aea-257">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="74aea-258">최소 1.7KB FLASH, RAM 크기</span><span class="sxs-lookup"><span data-stu-id="74aea-258">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="74aea-259">32비트의 동적 확인 IPv4 및 48비트 MAC 주소</span><span class="sxs-lookup"><span data-stu-id="74aea-259">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="74aea-260">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="74aea-260">IXIA IxANVL validated</span></span>
* <span data-ttu-id="74aea-261">유연한 사용자 정의 ARP 캐시</span><span class="sxs-lookup"><span data-stu-id="74aea-261">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="74aea-262">무상 ARP 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-262">Gratuitous ARP support</span></span>
* <span data-ttu-id="74aea-263">애플리케이션에 의해 결정되는 선택적 ARP/RARP 통계</span><span class="sxs-lookup"><span data-stu-id="74aea-263">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="74aea-264">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="74aea-264">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="74aea-265">직관적인 ARP/RARP API: *nx_arp_\** , *nx_rarp_\**</span><span class="sxs-lookup"><span data-stu-id="74aea-265">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="74aea-266">IPv4 &amp; IPv6</span><span class="sxs-lookup"><span data-stu-id="74aea-266">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="74aea-267">IP(인터넷 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="74aea-267">Internet Protocol (IP)</span></span>
* <span data-ttu-id="74aea-268">최소 3.5KB~8.5KB FLASH, 2KB~3KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="74aea-268">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="74aea-269">Piconet™ 아키텍처</span><span class="sxs-lookup"><span data-stu-id="74aea-269">Piconet™ architecture</span></span>
* <span data-ttu-id="74aea-270">빠른 근거리 통신 속도 성능</span><span class="sxs-lookup"><span data-stu-id="74aea-270">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="74aea-271">여러 인터페이스 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-271">Multiple interface support</span></span>
* <span data-ttu-id="74aea-272">멀티홈 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-272">Multihomed support</span></span>
* <span data-ttu-id="74aea-273">정적 라우팅 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-273">Static routing support</span></span>
* <span data-ttu-id="74aea-274">IP 조각화/리어셈블리 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-274">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="74aea-275">IPv4 및 IPv6 주소 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-275">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="74aea-276">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="74aea-276">IXIA IxANVL validated</span></span>
* <span data-ttu-id="74aea-277">단계 II IPv6 준비 로고 인증</span><span class="sxs-lookup"><span data-stu-id="74aea-277">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="74aea-278">선택적 IP 통계</span><span class="sxs-lookup"><span data-stu-id="74aea-278">Optional IP statistics</span></span>
* <span data-ttu-id="74aea-279">잘 정의된 직관적인 물리적 계층 드라이버 인터페이스</span><span class="sxs-lookup"><span data-stu-id="74aea-279">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="74aea-280">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="74aea-280">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="74aea-281">직관적인 IP 계층 API: *nx_ip_\** , *nxd_ip_\** , *nxd_ipv6_\**</span><span class="sxs-lookup"><span data-stu-id="74aea-281">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="74aea-282">TUV 및 UL에서 IEC 61508 SIL 4, IEC 62304 클래스 C, ISO 26262 ASIL D 및 EN 50128 SW-SIL4로 사전 인증</span><span class="sxs-lookup"><span data-stu-id="74aea-282">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="74aea-283">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="74aea-283">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="74aea-284">IPSEC(인터넷 프로토콜 보안)</span><span class="sxs-lookup"><span data-stu-id="74aea-284">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="74aea-285">IP 계층</span><span class="sxs-lookup"><span data-stu-id="74aea-285">IP layer</span></span>
* <span data-ttu-id="74aea-286">하드웨어 암호화 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-286">Hardware crypto support</span></span>
* <span data-ttu-id="74aea-287">다음을 포함한 소프트웨어 암호화 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-287">Software crypto support, including:</span></span>
    * <span data-ttu-id="74aea-288">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="74aea-288">DES, 3DES</span></span>
    * <span data-ttu-id="74aea-289">AES</span><span class="sxs-lookup"><span data-stu-id="74aea-289">AES</span></span>
    * <span data-ttu-id="74aea-290">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="74aea-290">HMAC-MD5</span></span>
    * <span data-ttu-id="74aea-291">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="74aea-291">HMAC-SHA1</span></span>
* <span data-ttu-id="74aea-292">IKE(Internet Key Exchange) 버전 2 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-292">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="74aea-293">직관적인 IPsec API: *nx_ipsec_\**</span><span class="sxs-lookup"><span data-stu-id="74aea-293">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="74aea-294">IPsec은 Azure RTOS NetX Duo에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-294">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="74aea-295">안전 및 보안 유지</span><span class="sxs-lookup"><span data-stu-id="74aea-295">Safe and secure</span></span>

<span data-ttu-id="74aea-296">Azure RTOS NetX Duo는 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-296">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="74aea-297">이 보안은 IPsec, SSL, TLS 및 DTLS를 비롯한 추가 기능형 보안 제품을 통해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-297">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="74aea-298">또한 애플리케이션은 Azure RTOS NetX Duo에 대한 모든 외부 액세스를 완벽하게 제어하여 보안 위험을 훨씬 더 쉽게 파악할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-298">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="74aea-299">Microsoft Azure RTOS는 기본 MCU/MPU 하드웨어 보호 메커니즘을 사용하여 통신을 보호하고 코드 및 데이터 격리를 만드는 구성 요소를 OEM에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-299">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="74aea-300">디바이스가 특정 사용 사례에 따른 변화하는 보안 요구 사항을 완벽하게 충족하는지 확인하는 것은 궁극적으로 디바이스 빌더의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-300">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>


## <a name="interoperability-verification"></a><span data-ttu-id="74aea-301">상호 운용성 확인</span><span class="sxs-lookup"><span data-stu-id="74aea-301">Interoperability verification</span></span>

<span data-ttu-id="74aea-302">NetX Duo는 RFC 표준을 준수하며 대부분의 공급 업체에 대해 디바이스와의 완벽한 상호 운용성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-302">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![IPv6 준비 로고](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="74aea-304">Azure RTOS NetX Duo는 규정 준수 및 상호 운용성 테스트를 통과했으며 IPv6 포럼에서 관리 및 검증되었음을 입증하는 엄격한 IPv6 준비 로고 인증을 얻은 유일한 임베디드 TCP/IP 스택 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-304">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="74aea-305">또한 NetX Duo는 NetX Duo 코어 TCP/IP 프로토콜 구현에 업계 표준 IxANVL(자동화된 네트워크 유효성 검사 라이브러리)을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-305">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="74aea-306">포괄적인 IoT 솔루션</span><span class="sxs-lookup"><span data-stu-id="74aea-306">Comprehensive IoT solution</span></span>

<span data-ttu-id="74aea-307">NetX Duo는 긴밀하게 포함된 IoT 애플리케이션을 위한 가장 포괄적인 TCP/IP 네트워킹 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-307">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="74aea-308">이 지원에는 다음과 같은 추가 기능형 프로토콜 제품이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-308">This support includes the following add-on protocol products.</span></span>

<span data-ttu-id="74aea-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="74aea-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="74aea-310">고급 기술</span><span class="sxs-lookup"><span data-stu-id="74aea-310">Advanced technology</span></span>

<span data-ttu-id="74aea-311">Azure RTOS NetX Duo는 다음을 포함하는 고급 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-311">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="74aea-312">Piconet™ 아키텍처</span><span class="sxs-lookup"><span data-stu-id="74aea-312">Piconet™ architecture</span></span>
* <span data-ttu-id="74aea-313">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="74aea-313">Automatic scaling</span></span>
* <span data-ttu-id="74aea-314">UDP Fast-Path Technology™</span><span class="sxs-lookup"><span data-stu-id="74aea-314">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="74aea-315">유연한 패킷 관리</span><span class="sxs-lookup"><span data-stu-id="74aea-315">Flexible packet management</span></span>
* <span data-ttu-id="74aea-316">복사 없는 API 및 구현</span><span class="sxs-lookup"><span data-stu-id="74aea-316">Zero-copy API and implementation</span></span>
* <span data-ttu-id="74aea-317">멀티홈 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-317">Multihomed support</span></span>
* <span data-ttu-id="74aea-318">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="74aea-318">Optional timeout on all suspension</span></span>
* <span data-ttu-id="74aea-319">정적 라우팅 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-319">Static routing support</span></span>
* <span data-ttu-id="74aea-320">IPsec</span><span class="sxs-lookup"><span data-stu-id="74aea-320">IPsec</span></span>
* <span data-ttu-id="74aea-321">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="74aea-321">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="74aea-322">Azure RTOS TraceX 시스템 분석 지원</span><span class="sxs-lookup"><span data-stu-id="74aea-322">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="74aea-323">관련 서비스</span><span class="sxs-lookup"><span data-stu-id="74aea-323">Related services</span></span>

<span data-ttu-id="74aea-324">IoT RTOS용 Azure Security Center 보안 모듈은 Azure RTOS 디바이스에 포괄적인 보안 솔루션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-324">The Azure Security Center for IoT RTOS security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="74aea-325">Azure RTOS용 보안 모듈은 악의적인 네트워크 활동 검색, 사용자 지정 경고 기반 디바이스 동작 기준 지정을 제공하고 디바이스 보안을 강화하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74aea-325">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="74aea-326">[Azure RTOS용 보안 모듈](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos)에 대해 자세히 알아보거나 [Azure RTOS용 보안 모듈 구성](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) 빠른 시작을 진행하세요.</span><span class="sxs-lookup"><span data-stu-id="74aea-326">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

## <a name="next-steps"></a><span data-ttu-id="74aea-327">다음 단계</span><span class="sxs-lookup"><span data-stu-id="74aea-327">Next steps</span></span>

<span data-ttu-id="74aea-328">NetX Duo에 대해 자세히 알아보려면 [Azure RTOS NetX Duo 사용자 가이드](about-this-guide.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74aea-328">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
