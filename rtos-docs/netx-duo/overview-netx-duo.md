---
title: Azure RTOS NetX Duo 이해
description: Azure RTOS NetX Duo는 긴밀하게 포함된 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 고급, 산업용 TCP/IP 네트워크 스택입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 2339da391e52b437a2111ae439cccf41e038bdcf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811742"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="dfb28-103">Azure RTOS NetX Duo 개요</span><span class="sxs-lookup"><span data-stu-id="dfb28-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="dfb28-104">Azure RTOS NetX Duo 임베디드 TCP/IP 네트워크 스택은 긴밀하게 포함된 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 Microsoft의 고급, 산업용 이중 IPv4 및 IPv6 TCP/IP 네트워크 스택입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="dfb28-105">NetX Duo는 IPv4, IPv6, TCP, UDP 등의 핵심 네트워크 프로토콜과 함께 포함된 애플리케이션을 제공하고 더 높은 수준의 추가 기능 프로토콜을 완벽하게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="dfb28-106">Azure RTOS NetX Duo는 Azure RTOS NetX Secure IPsec 및 Azure RTOS NetX Secure SSL/TLS/DTLS를 비롯한 추가 기능형 추가 보안 제품을 통해 보안을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="dfb28-107">이뿐 아니라 Azure RTOS NetX Duo는 적은 메모리 공간, 빠른 실행 및 뛰어난 사용 편의성을 제공하므로 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="dfb28-108">API 프로토콜</span><span class="sxs-lookup"><span data-stu-id="dfb28-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="dfb28-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="dfb28-109">MQTT</span></span>

* <span data-ttu-id="dfb28-110">MQTT(메시징 큐 원격 분석 전송)</span><span class="sxs-lookup"><span data-stu-id="dfb28-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="dfb28-111">최소 2.7KB FLASH</span><span class="sxs-lookup"><span data-stu-id="dfb28-111">Minimal 2.7 KB FLASH</span></span>
* <span data-ttu-id="dfb28-112">직관적인 MQTT API: *nx_mqtt_* \*</span><span class="sxs-lookup"><span data-stu-id="dfb28-112">Intuitive MQTT APIs: *nx_mqtt_*\*</span></span>

### <a name="auto-ip"></a><span data-ttu-id="dfb28-113">자동 IP</span><span class="sxs-lookup"><span data-stu-id="dfb28-113">Auto IP</span></span>

* <span data-ttu-id="dfb28-114">자동 IPv4 주소 할당</span><span class="sxs-lookup"><span data-stu-id="dfb28-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="dfb28-115">최소 1.2KB, 300바이트의 RAM</span><span class="sxs-lookup"><span data-stu-id="dfb28-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="dfb28-116">직관적인 AutoIP API: *nx_autoip_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http-https"></a><span data-ttu-id="dfb28-117">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="dfb28-117">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="dfb28-118">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="dfb28-118">HTTP 1.0</span></span>

* <span data-ttu-id="dfb28-119">HTTP(Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="dfb28-119">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="dfb28-120">최소 2.8KB~4.8KB 플래시/0.4KB~1.0KB RAM</span><span class="sxs-lookup"><span data-stu-id="dfb28-120">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="dfb28-121">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-121">Client and server support</span></span>
* <span data-ttu-id="dfb28-122">직관적인 API: *nx_http_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-122">Intuitive APIs: *nx_http_\**</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="dfb28-123">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="dfb28-123">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="dfb28-124">HTTP(Hypertext Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="dfb28-124">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="dfb28-125">최소 3.0KB~9.5KB 플래시/0.5KB~2KB RAM</span><span class="sxs-lookup"><span data-stu-id="dfb28-125">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="dfb28-126">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-126">Client and server support</span></span>
* <span data-ttu-id="dfb28-127">다중 수신 클라이언트 세션</span><span class="sxs-lookup"><span data-stu-id="dfb28-127">Multiple incoming client sessions</span></span>
* <span data-ttu-id="dfb28-128">일반 텍스트 및 암호화된 HTTPS</span><span class="sxs-lookup"><span data-stu-id="dfb28-128">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="dfb28-129">영구 연결 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-129">Persistent connection support</span></span>
* <span data-ttu-id="dfb28-130">다중 파트 파일 업로드</span><span class="sxs-lookup"><span data-stu-id="dfb28-130">Multipart file upload</span></span>
* <span data-ttu-id="dfb28-131">Azure RTOS NetX Secure TLS와 완전히 통합</span><span class="sxs-lookup"><span data-stu-id="dfb28-131">Fully integrated with Azure RTOS NetX Secure TLS</span></span>
* <span data-ttu-id="dfb28-132">직관적인 API: *nx_web_http\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-132">Intuitive APIs: *nx_web_http\**</span></span>

### <a name="smtp"></a><span data-ttu-id="dfb28-133">SMTP</span><span class="sxs-lookup"><span data-stu-id="dfb28-133">SMTP</span></span>

* <span data-ttu-id="dfb28-134">SMTP(Simple Mail Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="dfb28-134">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="dfb28-135">최소 4.1KB 및 0.6KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="dfb28-135">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="dfb28-136">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-136">Client support</span></span>
* <span data-ttu-id="dfb28-137">직관적인 SMTP API: *nx_smtp_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-137">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp"></a><span data-ttu-id="dfb28-138">DHCP</span><span class="sxs-lookup"><span data-stu-id="dfb28-138">DHCP</span></span>

* <span data-ttu-id="dfb28-139">DHCP(Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="dfb28-139">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="dfb28-140">최소 3.6KB~4.6KB FLASH, 2.7KB RAM 공간</span><span class="sxs-lookup"><span data-stu-id="dfb28-140">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="dfb28-141">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-141">Client and server support</span></span>
* <span data-ttu-id="dfb28-142">IPv4 및 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-142">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="dfb28-143">직관적인 DHCP API: *nx_dhcp_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-143">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="nat"></a><span data-ttu-id="dfb28-144">NAT</span><span class="sxs-lookup"><span data-stu-id="dfb28-144">NAT</span></span>

* <span data-ttu-id="dfb28-145">NAT(Network Address Translation)</span><span class="sxs-lookup"><span data-stu-id="dfb28-145">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="dfb28-146">최소 3.5KB 및 0.6KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="dfb28-146">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="dfb28-147">IPv4 주소 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-147">IPv4 address support</span></span>
* <span data-ttu-id="dfb28-148">직관적인 NAT API: *nx_nat_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-148">Intuitive NAT APIs: *nx_nat_\**</span></span>
* <span data-ttu-id="dfb28-149">NAT는 Azure RTOS NetX Duo에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-149">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="dfb28-150">SNMP</span><span class="sxs-lookup"><span data-stu-id="dfb28-150">SNMP</span></span>

* <span data-ttu-id="dfb28-151">SNMP(Simple Network Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="dfb28-151">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="dfb28-152">최소 10.9KB 및 2.6KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="dfb28-152">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="dfb28-153">VI, V2 및 V3에 대한 에이전트 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-153">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="dfb28-154">직관적인 SNMP API: *nx_snmp_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-154">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="dfb28-155">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="dfb28-155">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="dfb28-156">DNS(Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="dfb28-156">Domain Name System (DNS)</span></span>
* <span data-ttu-id="dfb28-157">mDNS(Multicast Domain Name System)</span><span class="sxs-lookup"><span data-stu-id="dfb28-157">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="dfb28-158">DNS-SD(DNS 기반 서비스 검색)</span><span class="sxs-lookup"><span data-stu-id="dfb28-158">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="dfb28-159">DNS 최소 2.4KB~3KB FLASH, 1KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="dfb28-159">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="dfb28-160">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-160">Client support</span></span>
* <span data-ttu-id="dfb28-161">직관적인 API: *nx_dns_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-161">Intuitive APIs: *nx_dns_\**</span></span>
* <span data-ttu-id="dfb28-162">mDNS 및 DNS-SD는 Azure RTOS NetX Duo에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-162">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="p0p3"></a><span data-ttu-id="dfb28-163">P0P3</span><span class="sxs-lookup"><span data-stu-id="dfb28-163">P0P3</span></span>

* <span data-ttu-id="dfb28-164">POP3(Post Office Protocol 버전 3)</span><span class="sxs-lookup"><span data-stu-id="dfb28-164">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="dfb28-165">최소 8.1KB 및 1.4KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="dfb28-165">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="dfb28-166">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-166">Client support</span></span>
* <span data-ttu-id="dfb28-167">직관적인 P0P3 API: *nx_pop3_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-167">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="telnet"></a><span data-ttu-id="dfb28-168">TELNET</span><span class="sxs-lookup"><span data-stu-id="dfb28-168">TELNET</span></span>

* <span data-ttu-id="dfb28-169">최소 0.5KB 및 0.3KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="dfb28-169">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="dfb28-170">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-170">Client and server support</span></span>
* <span data-ttu-id="dfb28-171">직관적인 Telnet API: *nx_telnet_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-171">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="dfb28-172">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="dfb28-172">FTP, TFTP</span></span>

* <span data-ttu-id="dfb28-173">FTP(파일 전송 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="dfb28-173">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="dfb28-174">TFTP(Trivial File Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="dfb28-174">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="dfb28-175">FTP 최소 1.8KB~7.2KB FLASH, 0.6KB~2.1KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="dfb28-175">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="dfb28-176">TFTP 최소 1.7KB~2.4KB FLASH, 0.3KB~1.8KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="dfb28-176">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="dfb28-177">클라이언트 및 서버 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-177">Client and server support</span></span>
* <span data-ttu-id="dfb28-178">직관적인 FTP 및 TFTP API: *nx_ftp_\** 또는 *nx_tftp_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-178">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="dfb28-179">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="dfb28-179">PPP, PPPoE</span></span>

* <span data-ttu-id="dfb28-180">PPP(지점 간 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="dfb28-180">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="dfb28-181">PPPoE(이더넷을 통한 지점 간 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="dfb28-181">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="dfb28-182">최소 7.1KB 및 3.8KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="dfb28-182">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="dfb28-183">직관적인 PPP API: *nx_ppp_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-183">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="dfb28-184">PPPoE는 Azure RTOS NetX Duo에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-184">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="dfb28-185">SNTP</span><span class="sxs-lookup"><span data-stu-id="dfb28-185">SNTP</span></span>

* <span data-ttu-id="dfb28-186">SNTP(Simple Network Time Protocol)</span><span class="sxs-lookup"><span data-stu-id="dfb28-186">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="dfb28-187">최소 4KB 및 0.5KB RAM</span><span class="sxs-lookup"><span data-stu-id="dfb28-187">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="dfb28-188">클라이언트 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-188">Client support</span></span>
* <span data-ttu-id="dfb28-189">직관적인 SNTP API: *nx_sntp_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-189">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="dfb28-190">Azure RTOS NetX Duo API</span><span class="sxs-lookup"><span data-stu-id="dfb28-190">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="dfb28-191">직관적이고 일관성 있는 API</span><span class="sxs-lookup"><span data-stu-id="dfb28-191">Intuitive and consistent API</span></span>
* <span data-ttu-id="dfb28-192">명사-동사 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="dfb28-192">Noun-verb naming convention</span></span>
* <span data-ttu-id="dfb28-193">빠르고 복사 없는 API 구현</span><span class="sxs-lookup"><span data-stu-id="dfb28-193">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="dfb28-194">모든 API에는 Azure RTOS NetX로 쉽게 식별할 수 있도록 <i>nx_\*</i>가 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-194">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="dfb28-195">차단 API에 선택적 스레드 시간 제한 적용</span><span class="sxs-lookup"><span data-stu-id="dfb28-195">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="dfb28-196">자세한 내용은 [Azure RTOS NetX Duo 사용자 가이드](about-this-guide.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dfb28-196">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="dfb28-197">레거시 소켓 코드 포팅을 위한 선택적 BSD 계층</span><span class="sxs-lookup"><span data-stu-id="dfb28-197">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="dfb28-198">IGMP</span><span class="sxs-lookup"><span data-stu-id="dfb28-198">IGMP</span></span>

* <span data-ttu-id="dfb28-199">IGMP(Internet Group Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="dfb28-199">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="dfb28-200">최소 2.5KB FLASH</span><span class="sxs-lookup"><span data-stu-id="dfb28-200">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="dfb28-201">IPv4 멀티캐스트 그룹 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-201">IPv4 multicast group support</span></span>
* <span data-ttu-id="dfb28-202">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="dfb28-202">IXIA IxANVL validated</span></span>
* <span data-ttu-id="dfb28-203">선택적 IGMP 통계</span><span class="sxs-lookup"><span data-stu-id="dfb28-203">Optional IGMP statistics</span></span>
* <span data-ttu-id="dfb28-204">Azure RTOS ThreadX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="dfb28-204">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="dfb28-205">직관적인 IGMP API: *nx_igmp_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-205">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="dfb28-206">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="dfb28-206">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="dfb28-207">DTLS(데이터그램 전송 계층 보안) 1.0 및 1.2</span><span class="sxs-lookup"><span data-stu-id="dfb28-207">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="dfb28-208">최소 11KB FLASH</span><span class="sxs-lookup"><span data-stu-id="dfb28-208">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="dfb28-209">고속, 소프트웨어 RSA 2048비트 키 크기 ~1초 @120MHz</span><span class="sxs-lookup"><span data-stu-id="dfb28-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="dfb28-210">간소화된 X.509 구현</span><span class="sxs-lookup"><span data-stu-id="dfb28-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="dfb28-211">Azure RTOS NetX Duo UDP 소켓과 완전히 통합</span><span class="sxs-lookup"><span data-stu-id="dfb28-211">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="dfb28-212">하드웨어 암호화 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="dfb28-213">소프트웨어 암호화 지원: RSA(모든 키 크기), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2(SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="dfb28-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="dfb28-214">ECDSA(서명) 및 ECDH(암호화)를 사용하는 ECC(Elliptic Curve Cryptography)(P-곡선 192/224/256/384/521 포함)</span><span class="sxs-lookup"><span data-stu-id="dfb28-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="dfb28-215">암호화된 키 지원(하드웨어 종속)</span><span class="sxs-lookup"><span data-stu-id="dfb28-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="dfb28-216">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="dfb28-216">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="dfb28-217">TLS(전송 계층 보안) 1.0, 1.1 및 1.2</span><span class="sxs-lookup"><span data-stu-id="dfb28-217">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="dfb28-218">최소 8.8KB FLASH</span><span class="sxs-lookup"><span data-stu-id="dfb28-218">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="dfb28-219">고속, 소프트웨어 RSA 2048비트 키 크기 ~1초 @120MHz</span><span class="sxs-lookup"><span data-stu-id="dfb28-219">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="dfb28-220">간소화된 X.509 구현</span><span class="sxs-lookup"><span data-stu-id="dfb28-220">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="dfb28-221">Azure RTOS NetX Duo TCP 소켓과 완전히 통합</span><span class="sxs-lookup"><span data-stu-id="dfb28-221">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="dfb28-222">하드웨어 암호화 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-222">Hardware Crypto Support</span></span>
* <span data-ttu-id="dfb28-223">소프트웨어 암호화 지원: RSA(모든 키 크기), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2(SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="dfb28-223">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="dfb28-224">ECDSA(서명) 및 ECDH(암호화)를 사용하는 ECC(Elliptic Curve Cryptography)(P-곡선 192/224/256/384/521 포함)</span><span class="sxs-lookup"><span data-stu-id="dfb28-224">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="dfb28-225">암호화된 키 지원(하드웨어 종속)</span><span class="sxs-lookup"><span data-stu-id="dfb28-225">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="dfb28-226">ICMP</span><span class="sxs-lookup"><span data-stu-id="dfb28-226">ICMP</span></span>

* <span data-ttu-id="dfb28-227">ICMP(Internet Control Message Protocol)</span><span class="sxs-lookup"><span data-stu-id="dfb28-227">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="dfb28-228">최소 2.5KB FLASH</span><span class="sxs-lookup"><span data-stu-id="dfb28-228">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="dfb28-229">IPv4 및 IPv6 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-229">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="dfb28-230">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="dfb28-230">IXIA IxANVL validated</span></span>
* <span data-ttu-id="dfb28-231">Ping 요청 및 Ping 응답</span><span class="sxs-lookup"><span data-stu-id="dfb28-231">Ping request and ping response</span></span>
* <span data-ttu-id="dfb28-232">Ping 요청 시 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="dfb28-232">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="dfb28-233">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="dfb28-233">Optional timeout on all suspension</span></span>
* <span data-ttu-id="dfb28-234">선택적 ICMP 통계</span><span class="sxs-lookup"><span data-stu-id="dfb28-234">Optional ICMP statistics</span></span>
* <span data-ttu-id="dfb28-235">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="dfb28-235">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="dfb28-236">직관적인 ICMP API: *nx_icmp_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-236">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="dfb28-237">UDP</span><span class="sxs-lookup"><span data-stu-id="dfb28-237">UDP</span></span>

* <span data-ttu-id="dfb28-238">UDP(사용자 데이터그램 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="dfb28-238">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="dfb28-239">최소 2.5KB FLASH, 소켓당 124 소켓 바이트의 RAM</span><span class="sxs-lookup"><span data-stu-id="dfb28-239">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="dfb28-240">빠른 근거리 통신 속도 TCP 패킷 처리:</span><span class="sxs-lookup"><span data-stu-id="dfb28-240">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="dfb28-241">100Mbps 이더넷의 RX 95Mbps, MCU @100MHz, 14% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="dfb28-241">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="dfb28-242">100Mbps 이더넷의 TX 94Mbps, MCU @100MHz, 10% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="dfb28-242">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="dfb28-243">UDP Fast Path™ 기술</span><span class="sxs-lookup"><span data-stu-id="dfb28-243">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="dfb28-244">UDP 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="dfb28-244">No limits on the number of UDP</span></span>
* <span data-ttu-id="dfb28-245">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="dfb28-245">IXIA IxANVL validated</span></span>
* <span data-ttu-id="dfb28-246">소켓 수신 시 선택적 일시 중단</span><span class="sxs-lookup"><span data-stu-id="dfb28-246">Optional suspension on socket receive</span></span>
* <span data-ttu-id="dfb28-247">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="dfb28-247">Optional timeout on all suspension</span></span>
* <span data-ttu-id="dfb28-248">선택적 UDP 통계</span><span class="sxs-lookup"><span data-stu-id="dfb28-248">Optional UDP statistics</span></span>
* <span data-ttu-id="dfb28-249">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="dfb28-249">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="dfb28-250">직관적인 UDP API: *nx_udp_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-250">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="dfb28-251">TCP</span><span class="sxs-lookup"><span data-stu-id="dfb28-251">TCP</span></span>

* <span data-ttu-id="dfb28-252">TCP(Transmission Control Protocol)</span><span class="sxs-lookup"><span data-stu-id="dfb28-252">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="dfb28-253">최소 10.5KB~12.5KB FLASH, 소켓당 280바이트의 RAM</span><span class="sxs-lookup"><span data-stu-id="dfb28-253">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="dfb28-254">빠른 근거리 통신 속도 TCP 패킷 처리:</span><span class="sxs-lookup"><span data-stu-id="dfb28-254">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="dfb28-255">100Mbps 이더넷의 RX 93Mbps, MCU @100MHz, 20% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="dfb28-255">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="dfb28-256">100Mbps 이더넷의 TX 94Mbps, MCU @100MHz, 27% MCU 사용률</span><span class="sxs-lookup"><span data-stu-id="dfb28-256">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="dfb28-257">안정적인 연결</span><span class="sxs-lookup"><span data-stu-id="dfb28-257">Reliable connection</span></span>
* <span data-ttu-id="dfb28-258">TCP 소켓 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="dfb28-258">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="dfb28-259">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="dfb28-259">IXIA IxANVL validated</span></span>
* <span data-ttu-id="dfb28-260">소켓 수신/전송 시 선택적 일시 중단</span><span class="sxs-lookup"><span data-stu-id="dfb28-260">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="dfb28-261">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="dfb28-261">Optional timeout on all suspension</span></span>
* <span data-ttu-id="dfb28-262">선택적 TCP 통계</span><span class="sxs-lookup"><span data-stu-id="dfb28-262">Optional TCP statistics</span></span>
* <span data-ttu-id="dfb28-263">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="dfb28-263">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="dfb28-264">직관적인 TCP API: *nx_tcp_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-264">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="dfb28-265">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="dfb28-265">ARP/RARP</span></span>

* <span data-ttu-id="dfb28-266">ARP(주소 확인 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="dfb28-266">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="dfb28-267">RARP(역주소 확인 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="dfb28-267">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="dfb28-268">최소 1.7KB FLASH, RAM 크기</span><span class="sxs-lookup"><span data-stu-id="dfb28-268">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="dfb28-269">32비트의 동적 확인 IPv4 및 48비트 MAC 주소</span><span class="sxs-lookup"><span data-stu-id="dfb28-269">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="dfb28-270">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="dfb28-270">IXIA IxANVL validated</span></span>
* <span data-ttu-id="dfb28-271">유연한 사용자 정의 ARP 캐시</span><span class="sxs-lookup"><span data-stu-id="dfb28-271">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="dfb28-272">무상 ARP 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-272">Gratuitous ARP support</span></span>
* <span data-ttu-id="dfb28-273">애플리케이션에 의해 결정되는 선택적 ARP/RARP 통계</span><span class="sxs-lookup"><span data-stu-id="dfb28-273">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="dfb28-274">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="dfb28-274">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="dfb28-275">직관적인 ARP/RARP API: *nx_arp_\** , *nx_rarp_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-275">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="dfb28-276">IPv4 &amp; IPv6</span><span class="sxs-lookup"><span data-stu-id="dfb28-276">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="dfb28-277">IP(인터넷 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="dfb28-277">Internet Protocol (IP)</span></span>
* <span data-ttu-id="dfb28-278">최소 3.5KB~8.5KB FLASH, 2KB~3KB의 RAM 공간</span><span class="sxs-lookup"><span data-stu-id="dfb28-278">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="dfb28-279">Piconet™ 아키텍처</span><span class="sxs-lookup"><span data-stu-id="dfb28-279">Piconet™ architecture</span></span>
* <span data-ttu-id="dfb28-280">빠른 근거리 통신 속도 성능</span><span class="sxs-lookup"><span data-stu-id="dfb28-280">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="dfb28-281">여러 인터페이스 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-281">Multiple interface support</span></span>
* <span data-ttu-id="dfb28-282">멀티홈 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-282">Multihomed support</span></span>
* <span data-ttu-id="dfb28-283">정적 라우팅 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-283">Static routing support</span></span>
* <span data-ttu-id="dfb28-284">IP 조각화/리어셈블리 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-284">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="dfb28-285">IPv4 및 IPv6 주소 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-285">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="dfb28-286">IXIA IxANVL 유효성 검사 완료</span><span class="sxs-lookup"><span data-stu-id="dfb28-286">IXIA IxANVL validated</span></span>
* <span data-ttu-id="dfb28-287">단계 II IPv6 준비 로고 인증</span><span class="sxs-lookup"><span data-stu-id="dfb28-287">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="dfb28-288">선택적 IP 통계</span><span class="sxs-lookup"><span data-stu-id="dfb28-288">Optional IP statistics</span></span>
* <span data-ttu-id="dfb28-289">잘 정의된 직관적인 물리적 계층 드라이버 인터페이스</span><span class="sxs-lookup"><span data-stu-id="dfb28-289">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="dfb28-290">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="dfb28-290">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="dfb28-291">직관적인 IP 계층 API: *nx_ip_\** , *nxd_ip_\** , *nxd_ipv6_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-291">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="dfb28-292">TUV 및 UL에서 IEC 61508 SIL 4, IEC 62304 클래스 C, ISO 26262 ASIL D 및 EN 50128 SW-SIL4로 사전 인증</span><span class="sxs-lookup"><span data-stu-id="dfb28-292">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="dfb28-293">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="dfb28-293">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="dfb28-294">IPSEC(인터넷 프로토콜 보안)</span><span class="sxs-lookup"><span data-stu-id="dfb28-294">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="dfb28-295">IP 계층</span><span class="sxs-lookup"><span data-stu-id="dfb28-295">IP layer</span></span>
* <span data-ttu-id="dfb28-296">하드웨어 암호화 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-296">Hardware crypto support</span></span>
* <span data-ttu-id="dfb28-297">다음을 포함한 소프트웨어 암호화 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-297">Software crypto support, including:</span></span>
    * <span data-ttu-id="dfb28-298">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="dfb28-298">DES, 3DES</span></span>
    * <span data-ttu-id="dfb28-299">AES</span><span class="sxs-lookup"><span data-stu-id="dfb28-299">AES</span></span>
    * <span data-ttu-id="dfb28-300">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="dfb28-300">HMAC-MD5</span></span>
    * <span data-ttu-id="dfb28-301">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="dfb28-301">HMAC-SHA1</span></span>
* <span data-ttu-id="dfb28-302">IKE(Internet Key Exchange) 버전 2 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-302">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="dfb28-303">직관적인 IPsec API: *nx_ipsec_\**</span><span class="sxs-lookup"><span data-stu-id="dfb28-303">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="dfb28-304">IPsec은 Azure RTOS NetX Duo에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-304">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="small-footprint"></a><span data-ttu-id="dfb28-305">적은 메모리 공간</span><span class="sxs-lookup"><span data-stu-id="dfb28-305">Small-footprint</span></span>

<span data-ttu-id="dfb28-306">Azure RTOS NetX Duo는 기본 IP 및 UDP 지원에 대한 공간이 9KB ~ 15KB로 매우 적습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-306">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="dfb28-307">TCP 기능을 위해서는 추가적으로 10KB ~ 13KB의 명령 영역 메모리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-307">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="dfb28-308">Azure RTOS NetX Duo RAM 사용량은 일반적으로 2.6KB에서 3.6KB까지이며, 애플리케이션에 의해 정의되는 패킷 풀 메모리를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-308">Azure RTOS NetX Duo RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="dfb28-309">Azure RTOS ThreadX와 같이 Azure RTOS NetX Duo의 크기는 애플리케이션에서 사용하는 서비스에 따라 자동으로 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-309">Like Azure RTOS ThreadX, the size of Azure RTOS NetX Duo automatically scales based on the services used by the application.</span></span> <span data-ttu-id="dfb28-310">이렇게 하면 사실상 복잡한 구성 및 빌드 매개 변수가 제거되어 개발자가 더 쉽게 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-310">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="dfb28-311">고속 실행</span><span class="sxs-lookup"><span data-stu-id="dfb28-311">Fast execution</span></span>

<span data-ttu-id="dfb28-312">Azure RTOS NetX Duo는 복사 없는 패킷 송신/수신 구현을 제공하며 Azure RTOS ThreadX와 고도로 통합되어 가장 빠른 성능을 실현합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-312">Azure RTOS NetX Duo provides a zero-copy packet send/receive implementation, highly integrated with Azure RTOS ThreadX, to achieve the fastest possible performance.</span></span> <span data-ttu-id="dfb28-313">예를 들어 Azure RTOS NetX Duo는 일반적으로 프로세서 주기 중 일부만 사용하면서 80MHz(또는 이하) 프로세서에서 근거리 통신 속도 데이터 전송을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-313">For example, Azure RTOS NetX Duo can typically achieve near wirespeed data transfers on an 80 MHz (or less) processor, while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="dfb28-314">간단하고 손쉬운 사용</span><span class="sxs-lookup"><span data-stu-id="dfb28-314">Simple, easy-to-use</span></span>

<span data-ttu-id="dfb28-315">Azure RTOS NetX Duo API는 직관적이고 간단하며 기능이 뛰어납니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-315">The Azure RTOS NetX Duo API is intuitive, straightforward,  and highly functional.</span></span>

<span data-ttu-id="dfb28-316">API 이름은 “대단히 이해하기 어려운” 것이 아니며, 다른 네트워킹 제품에 매우 흔한 고도로 축약된 이름도 아닌 실제 단어로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-316">The API names are made of real words and not the “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="dfb28-317">모든 Azure RTOS NetX Duo API에는 선행 *nx_* 가 있으며 명사-동사 명명 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-317">All Azure RTOS NetX Duo APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="dfb28-318">또한 API 전체에 걸쳐 기능적 일관성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-318">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="dfb28-319">예를 들어 일시 중단된 모든 API 함수는 동일한 방식으로 작동하는 선택적 시간 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-319">For example, all API functions that suspend have an optional timeout that operates in an identical manner.</span></span>

<span data-ttu-id="dfb28-320">레거시 애플리케이션의 경우 Azure RTOS NetX Duo는 추가 BSD 소켓 호환 계층을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-320">For legacy applications, Azure RTOS NetX Duo offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="dfb28-321">이 계층을 통해 개발자는 수많은 네트워킹 애플리케이션을 쉽게 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-321">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="dfb28-322">안전 및 보안 유지</span><span class="sxs-lookup"><span data-stu-id="dfb28-322">Safe and secure</span></span>

<span data-ttu-id="dfb28-323">Azure RTOS NetX Duo는 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-323">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="dfb28-324">이 보안은 IPsec, SSL, TLS 및 DTLS를 비롯한 추가 기능형 보안 제품을 통해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-324">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="dfb28-325">또한 애플리케이션은 Azure RTOS NetX Duo에 대한 모든 외부 액세스를 완벽하게 제어하여 보안 위험을 훨씬 더 쉽게 파악할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-325">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="dfb28-326">Microsoft Azure RTOS는 기본 MCU/MPU 하드웨어 보호 메커니즘을 사용하여 통신을 보호하고 코드 및 데이터 격리를 만드는 구성 요소를 OEM에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-326">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="dfb28-327">디바이스가 특정 사용 사례에 따른 변화하는 보안 요구 사항을 완벽하게 충족하는지 확인하는 것은 궁극적으로 디바이스 빌더의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-327">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="dfb28-328">TUV 및 UL을 비롯한 여러 안전 표준의 사전 인증</span><span class="sxs-lookup"><span data-stu-id="dfb28-328">Pre-certified  by TUV and UL to many safety standards</span></span>

<span data-ttu-id="dfb28-329">Azure RTOS NetX Duo는 안전이 매우 중요한 시스템에서의 사용을 위해, IEC-61508 SIL 4, IEC-62304  SW 안전 등급 C, ISO 26262 ASIL D 및 EN 50128에 따라 SGS-TUV Saar 인증을 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-329">Azure RTOS NetX Duo has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="dfb28-330">이 인증은 "전기, 전자 및 프로그램 가능한 전자 안전 관련 시스템의 기능적 안전”에 대한 최고 수준의 IEC-61508, IEC-62304, ISO 26262 and EN 50128의 안전 무결성 등급에 따라, Azure RTOS NetX Duo를 보안 관련 소프트웨어의 개발에 사용할 수 있음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-330">The certification confirms that Azure RTOS NetX Duo can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="dfb28-331">독일 SGS-Group 및 TUV Saarland의 공동 벤처인 SGS-TUV Saar는 세계적으로 안전 관련 시스템용 포함 소프트웨어를 테스트, 감사, 확인 및 검증하는 최고 권위의 독립 기업으로 자리했습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-331">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="dfb28-332">산업 보안 표준 IEC 61508과, 거기에서 파생된 모든 표준(IEC-62304, ISO 26262 및 EN 50128 포함)은 전기, 전자 및 프로그래밍 가능한 전자 안전 관련 의료 장비, 공정 제어 시스템, 산업용 기계, 자동차, 철도 제어 시스템의 기능 안전을 보장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-332">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="인증":::

<span data-ttu-id="dfb28-334">UL은 Azure RTOS NetX Duo가 프로그래밍 가능한 구성 요소에서의 소프트웨어에 대한 UL 60730-1 부칙 H, CSA E60730-1 부칙 H, IEC 60730-1 부칙 H, UL 60335-1 부칙 R, IEC 60335-1 부칙 R 및 UL 1998 안전 표준을 준수한다고 인정했습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-334">Azure RTOS NetX Duo has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="dfb28-335">UL은 공공 에너지 도입, 첨단 지속 가능성 기술, 재생 에너지, 나노 기술 등을 망라하는 안전 솔루션 혁신 분야에서 백년이 넘는 전문 기술을 갖춘 글로벌 독립 안전 과학 기업입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-335">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="CRU UL 인증":::

<span data-ttu-id="dfb28-337">TUV 및 UL 인증과 관련한 아티팩트(인증서, 안전 매뉴얼, 테스트 보고서 등)는 판매 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-337">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="dfb28-338">애플리케이션에 추가 인증이 필요한 경우, 실제 하드웨어 플랫폼을 사용한 다양한 표준에 대한 턴키 방식의 인증을 제공하고 애플리케이션 코드까지도 다루는 인증 서비스를 Microsoft를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-338">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span> <span data-ttu-id="dfb28-339">인증 서비스에 대한 자세한 내용은 Microsoft에 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="dfb28-339">Contact us for more details on our certification service.</span></span>

## <a name="eal4-common-criteria-security-certification"></a><span data-ttu-id="dfb28-340">EAL4+ Common Criteria 보안 인증</span><span class="sxs-lookup"><span data-stu-id="dfb28-340">EAL4+ Common Criteria security certification</span></span>

<span data-ttu-id="dfb28-341">Azure RTOS는 EAL4+ Common Criteria 보안 인증을 달성했습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-341">Azure RTOS has achieved EAL4+ Common Criteria security certification.</span></span> <span data-ttu-id="dfb28-342">TOE(평가 대상)은 Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS 및 Azure RTOS NetX MQTT를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-342">The Target of Evalution (TOE) covers Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS, and Azure RTOS NetX MQTT.</span></span> <span data-ttu-id="dfb28-343">이는 긴밀하게 포함된 센서, 디바이스, 에지 라우터 및 게이트웨이에 필요한 가장 일반적인 IoT 프로토콜을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-343">This represents the most typical IoT protocols required by deeply embedded sensors, devices, edge routers, and gateways.</span></span>

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="EAL 인증":::

<span data-ttu-id="dfb28-345">Microsoft Azure RTOS SC 보안 인증에 사용되는 IT 보안 평가 시설은 Brightsight BV이고 인증 기관은 SERTIT입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-345">The IT Security Evaluation Facility used for the Microsoft Azure RTOS SC security certification is Brightsight BV and the Certification Authority is SERTIT.</span></span>

## <a name="fips-140-2-validated"></a><span data-ttu-id="dfb28-346">FIPS 140-2 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="dfb28-346">FIPS 140-2 Validated</span></span>

<span data-ttu-id="dfb28-347">Azure RTOS NetX 암호화 라이브러리는 암호화 모듈에 대한 요구 사항을 지정하는 소프트웨어용 FIPS 140-2(Federal Information Processing Standard 140-2) 인증을 획득했습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-347">Azure RTOS NetX Crypto libraries have achieved Federal Information Processing Standardization 140-2 (FIPS 140-2) Certification for software, which specifies requirements for cryptography modules.</span></span> <span data-ttu-id="dfb28-348">FIPS 140-2에 따르면 암호화 기반 보안을 사용하는 모든 연방 정부 기관 및 부서는 암호화 강도 및 기능과 관련된 특정 표준을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-348">FIPS 140-2 requires all federal government agencies and departments that use cryptographic-based security to meet specific standards related to encryption strength and capabilities.</span></span> <span data-ttu-id="dfb28-349">이러한 암호화 기반 보안 표준은 캐나다 및 유럽 연합에서도 인정되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-349">These cryptographic-based security standards are also recognized in Canada and the European Union.</span></span>

<span data-ttu-id="dfb28-350">Azure RTOS NetX 암호화 라이브러리에 사용되는 정보 보안 평가 랩은 atsec이었으며 인증 기관은 NIST(National Institute of Standards and Technology)입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-350">The Information Security evaluation lab used for Azure RTOS NetX Crypto libraries was atsec and the certification authority is The National Institute of Standards and Technology (NIST).</span></span> <span data-ttu-id="dfb28-351">자세한 내용은 [NIST 웹 사이트](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dfb28-351">Review the [NIST website](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) for additional details.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="dfb28-352">상호 운용성 확인</span><span class="sxs-lookup"><span data-stu-id="dfb28-352">Interoperability verification</span></span>

<span data-ttu-id="dfb28-353">NetX Duo는 RFC 표준을 준수하며 대부분의 공급 업체에 대해 디바이스와의 완벽한 상호 운용성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-353">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![IPv6 준비 로고](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="dfb28-355">Azure RTOS NetX Duo는 규정 준수 및 상호 운용성 테스트를 통과했으며 IPv6 포럼에서 관리 및 검증되었음을 입증하는 엄격한 IPv6 준비 로고 인증을 얻은 유일한 임베디드 TCP/IP 스택 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-355">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="dfb28-356">또한 NetX Duo는 NetX Duo 코어 TCP/IP 프로토콜 구현에 업계 표준 IxANVL(자동화된 네트워크 유효성 검사 라이브러리)을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-356">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="dfb28-357">포괄적인 IoT 솔루션</span><span class="sxs-lookup"><span data-stu-id="dfb28-357">Comprehensive IoT solution</span></span>

<span data-ttu-id="dfb28-358">Azure RTOS NetX Duo는 기본 IP 및 UDP 지원에 대한 공간이 9KB ~ 15KB로 매우 적습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-358">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="dfb28-359">NetX Duo는 긴밀하게 포함된 IoT 애플리케이션을 위한 가장 포괄적인 TCP/IP 네트워킹 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-359">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="dfb28-360">이 지원에는 다음과 같은 추가 기능형 프로토콜 제품이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-360">This support includes the following add-on protocol products:</span></span>

<span data-ttu-id="dfb28-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="dfb28-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="dfb28-362">고급 기술</span><span class="sxs-lookup"><span data-stu-id="dfb28-362">Advanced technology</span></span>

<span data-ttu-id="dfb28-363">Azure RTOS NetX Duo는 다음을 포함하는 고급 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-363">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="dfb28-364">Piconet™ 아키텍처</span><span class="sxs-lookup"><span data-stu-id="dfb28-364">Piconet™ architecture</span></span>
* <span data-ttu-id="dfb28-365">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="dfb28-365">Automatic scaling</span></span>
* <span data-ttu-id="dfb28-366">UDP Fast-Path Technology™</span><span class="sxs-lookup"><span data-stu-id="dfb28-366">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="dfb28-367">유연한 패킷 관리</span><span class="sxs-lookup"><span data-stu-id="dfb28-367">Flexible packet management</span></span>
* <span data-ttu-id="dfb28-368">복사 없는 API 및 구현</span><span class="sxs-lookup"><span data-stu-id="dfb28-368">Zero-copy API and implementation</span></span>
* <span data-ttu-id="dfb28-369">멀티홈 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-369">Multihomed support</span></span>
* <span data-ttu-id="dfb28-370">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="dfb28-370">Optional timeout on all suspension</span></span>
* <span data-ttu-id="dfb28-371">정적 라우팅 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-371">Static routing support</span></span>
* <span data-ttu-id="dfb28-372">IPsec</span><span class="sxs-lookup"><span data-stu-id="dfb28-372">IPsec</span></span>
* <span data-ttu-id="dfb28-373">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="dfb28-373">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="dfb28-374">Azure RTOS TraceX 시스템 분석 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-374">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="dfb28-375">가장 빠른 출시 시간</span><span class="sxs-lookup"><span data-stu-id="dfb28-375">Fastest time-to-market</span></span>

<span data-ttu-id="dfb28-376">Azure RTOS NetX Duo는 설치, 학습, 사용, 디버그, 확인, 인증 및 유지 관리를 손쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-376">Azure RTOS NetX Duo is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="dfb28-377">결과적으로 NetX Duo는 Broadcom, Gainspan 등의 많은 Soc를 비롯한 임베디드 IoT 디바이스에서 가장 많이 사용되는 TCP/IP 스택 중 하나로 자리잡았습니다. 일관적인 출시 기간 단축은 다음을 토대로 가능해졌습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-377">As a result, NetX Duo is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, etc. Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="dfb28-378">품질 설명서 – [Azure RTOS NetX Duo 사용자 가이드](about-this-guide.md)를 검토하고 직접 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="dfb28-378">Quality documentation – please review our [Azure RTOS NetX Duo User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="dfb28-379">전체 소스 코드 가용성</span><span class="sxs-lookup"><span data-stu-id="dfb28-379">Complete source code availability</span></span>
* <span data-ttu-id="dfb28-380">사용하기 쉬운 API</span><span class="sxs-lookup"><span data-stu-id="dfb28-380">Easy-to-use API</span></span>
* <span data-ttu-id="dfb28-381">포괄적인 고급 기능 세트</span><span class="sxs-lookup"><span data-stu-id="dfb28-381">Comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="dfb28-382">하나의 간단한 라이선스</span><span class="sxs-lookup"><span data-stu-id="dfb28-382">One Simple License</span></span>

<span data-ttu-id="dfb28-383">사전에 사용이 허가된 디바이스에 배포하는 경우에는 소스 코드를 사용 및 테스트하는 데 비용이 들지 않으며 프로덕션 라이선스에 대한 비용도 부과되지 않습니다. 다른 모든 디바이스에는 간단한 연간 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-383">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="dfb28-384">최고 품질의 전체 소스 코드</span><span class="sxs-lookup"><span data-stu-id="dfb28-384">Full, highest-quality source code</span></span>

<span data-ttu-id="dfb28-385">오랜 시간을 통해 Azure RTOS NetX Duo 소스 코드는 품질 및 이해 용이성의 기준을 정립했습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-385">Throughout the years, Azure RTOS NetX Duo source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="dfb28-386">또한 파일당 하나의 함수를 포함하는 규칙을 통해 손쉬운 소스 탐색을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-386">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="dfb28-387">대부분의 주요 아키텍처 지원</span><span class="sxs-lookup"><span data-stu-id="dfb28-387">Supports most popular architectures</span></span>

<span data-ttu-id="dfb28-388">Azure RTOS NetX Duo는 다음과 같은 고급 아키텍처를 포함하여 완벽하게 테스트되고 완전히 지원되는 가장 인기 있는 32/64비트 마이크로프로세서에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-388">Azure RTOS NetX Duo runs on most popular 32/64-bit microprocessors out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="dfb28-389">**아날로그 디바이스**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="dfb28-389">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="dfb28-390">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="dfb28-390">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="dfb28-391">**Ambiqmicro**: pollo MCU</span><span class="sxs-lookup"><span data-stu-id="dfb28-391">**Ambiqmicro**: pollo MCUs</span></span>

<span data-ttu-id="dfb28-392">**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64비트/A7x 64비트/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="dfb28-392">**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="dfb28-393">**Cadence**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="dfb28-393">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="dfb28-394">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="dfb28-394">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="dfb28-395">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="dfb28-395">**Cypress**: RISC-V</span></span>

<span data-ttu-id="dfb28-396">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="dfb28-396">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="dfb28-397">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="dfb28-397">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="dfb28-398">**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="dfb28-398">**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="dfb28-399">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="dfb28-399">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="dfb28-400">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="dfb28-400">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="dfb28-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="dfb28-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="dfb28-402">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span><span class="sxs-lookup"><span data-stu-id="dfb28-402">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="dfb28-403">**Silicon** Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="dfb28-403">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="dfb28-404">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="dfb28-404">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="dfb28-405">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="dfb28-405">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="dfb28-406">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="dfb28-406">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="dfb28-407">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="dfb28-407">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="dfb28-408">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="dfb28-408">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="dfb28-409">*나열된 모든 타이밍 및 크기 수치는 예상치이며, 개발 플랫폼에 따라 다를 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="dfb28-409">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>

## <a name="related-services"></a><span data-ttu-id="dfb28-410">관련 서비스</span><span class="sxs-lookup"><span data-stu-id="dfb28-410">Related services</span></span>

<span data-ttu-id="dfb28-411">IoT RTOS용 Azure Security Center 보안 모듈은 Azure RTOS 디바이스에 포괄적인 보안 솔루션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-411">The Azure Security Center for IoT RTOS security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="dfb28-412">Azure RTOS용 보안 모듈은 악의적인 네트워크 활동 검색, 사용자 지정 경고 기반 디바이스 동작 기준 지정을 제공하고 디바이스 보안을 강화하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfb28-412">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="dfb28-413">[Azure RTOS용 보안 모듈](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos)에 대해 자세히 알아보거나 [Azure RTOS용 보안 모듈 구성](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) 빠른 시작을 진행하세요.</span><span class="sxs-lookup"><span data-stu-id="dfb28-413">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dfb28-414">다음 단계</span><span class="sxs-lookup"><span data-stu-id="dfb28-414">Next steps</span></span>

<span data-ttu-id="dfb28-415">NetX Duo에 대해 자세히 알아보려면 [Azure RTOS NetX Duo 사용자 가이드](about-this-guide.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dfb28-415">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
