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
# <a name="overview-of-azure-rtos-netx"></a>Azure RTOS NetX 개요

Azure RTOS NetX는 특별히 긴밀하게 포함된 실시간 및 IoT 애플리케이션용으로 설계된 산업용 TCP/IP IPv4 포함 네트워크 스택입니다. Azure RTOS NetX는 Microsoft의 원래 IPv4 네트워크 스택으로, 기본적으로 Azure RTOS의 하위 집합입니다. NetX는 IPv4, TCP, UDP 등의 핵심 네트워크 프로토콜과 함께 포함된 애플리케이션을 제공하고 더 높은 수준의 추가 기능 프로토콜을 완벽하게 제공합니다. Azure RTOS NetX는 적은 공간, 빠른 실행 및 뛰어난 사용 편의성을 제공하므로 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.

## <a name="api-protocols"></a>API 프로토콜

### <a name="telnet"></a>TELNET

* 최소 0.5KB 및 0.3KB의 RAM 공간
* 클라이언트 및 서버 지원
* 직관적인 Telnet API: *nx_telnet_\**

### <a name="auto-ip"></a>자동 IP

* 자동 IPv4 주소 할당
* 최소 1.2KB, 300바이트의 RAM
* 직관적인 AutoIP API: *nx_autoip_\**

### <a name="http---hypertext-transfer-protocolhttp"></a>HTTP - HTTP(Hypertext Transfer Protocol)

* 최소 2.8KB ~ 4.8KB FLASH, 0.4KB ~ 1.0KB RAM 공간
* 클라이언트 및 서버 지원
* 직관적인 HTTP API: *nx_http_\**

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a>SMTP - SMTP(Simple Mail Transfer Protocol)

* 최소 4.1KB 및 0.6KB의 RAM 공간
* 클라이언트 지원
* 직관적인 SMTP API: *nx_smtp_\**

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a>DHCP - DHCP(Dynamic Host Configuration Protocol)

* 최소 3.6KB ~ 4.6KB FLASH, 2.7KB RAM 공간
* 클라이언트 및 서버 지원
* IPv4 지원
* 직관적인 DHCP API: *nx_dhcp_\**

### <a name="p0p3---post-office-protocol-version-3-pop3"></a>P0P3 - POP3(Post Office Protocol Version 3)

* 최소 8.1KB 및 1.4KB의 RAM 공간
* 클라이언트 지원
* 직관적인 P0P3 API: *nx_pop3_\**

### <a name="snmp---simple-network-management-protocol-snmp"></a>SNMP - SNMP(Simple Network Management Protocol)

* 최소 10.9KB 및 2.6KB의 RAM 공간
* VI, V2 및 V3에 대한 에이전트 지원
* 직관적인 SNMP API: *nx_snmp_\**

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a>FTP, TFTP - FTP(파일 전송 프로토콜), TFTP(Trivial File Transfer Protocol)

* FTP 최소 1.8KB ~ 7.2KB FLASH, 0.6KB ~ 2.1KB RAM 공간
* TFTP 최소 1.7KB ~ 2.4KB FLASH, 0.3KB ~ 1.8KB RAM 공간
* 클라이언트 및 서버 지원
* 직관적인 FTP 및 TFTP API: <i>nx_ftp_ *</i> 또는 <i>nx_tftp_* </i>

### <a name="ppp---polnt-to-point-protocol-ppp"></a>PPP - PPP(지점 간 프로토콜)

* 최소 7.1KB 및 3.8KB의 RAM 공간
* 직관적인 PPP API: *nx_ppp_\**

### <a name="sntp---simple-network-time-protocol-sntp"></a>SNTP - SNTP(Simple Network Time Protocol)

* 최소 4KB 및 0.5KB RAM
* 클라이언트 지원
* 직관적인 SNTP API: *nx_sntp_\**

### <a name="azure-rtos-netx-api"></a>Azure RTOS NetX API

* 직관적이고 일관적인 API
* 명사-동사 명명 규칙
* 빠르고 복사 없는 API 구현
* 모든 API 함수에는 Azure RTOS NetX로 쉽게 식별할 수 있도록 <i>nx_*</i>가 앞에 옵니다.
* API 함수 차단에는 선택적 스레드 시간 제한이 있습니다.
* 레거시 소켓 코드 포팅을 위한 선택적 BSD 계층

### <a name="igmp---internet-group-management-protocol-igmp"></a>IGMP - IGMP(Internet Group Management Protocol)

* 최소 2.5KB FLASH
* IPv4 멀티캐스트 그룹 지원
* IXIA IxANVL 유효성 검사 완료
* 선택적 IGMP 통계
* Azure RTOS TraceX를 통한 시스템 수준 추적
* 직관적인 IGMP API: *nx_igmp_\**

### <a name="udp---user-datagram-protocol-udp"></a>UDP - UDP(사용자 데이터그램 프로토콜)

* 최소 2.5KB FLASH, 소켓당 124 소켓 바이트의 RAM
* 빠른 근거리 통신 속도 TCP 패킷 처리:
* 100Mbps 이더넷의 RX 95Mbps, MCU @100MHz, 14% MCU 사용률
* 100Mbps 이더넷의 TX 94Mbps, MCU @100MHz, 10% MCU 사용률
* UDP Fast Path™ 기술
* UDP 수 제한 없음
* IXIA IxANVL 유효성 검사 완료
* 소켓 수신 시 선택적 일시 중단
* 모든 일시 중단 시 선택적 시간 제한
* 선택적 UDP 통계
* Azure RTOS TraceX를 통한 시스템 수준 추적
* 직관적인 UDP API: *nx_udp_\**

### <a name="tcp---transmission-control-protocol-tcp"></a>TCP - TCP(Transmission Control Protocol)

* 최소 10.5KB ~ 12.5KB FLASH, 소켓당 280바이트의 RAM
* 빠른 근거리 통신 속도 TCP 패킷 처리:
* 100Mbps 이더넷의 RX 93Mbps, MCU @100MHz, 20% MCU 사용률
* 100Mbps 이더넷의 TX 94Mbps, MCU @100MHz, 27% MCU 사용률
* 안정적인 연결
* TCP 소켓 수 제한 없음
* IXIA IxANVL 유효성 검사 완료
* 소켓 수신/전송 시 선택적 일시 중단
* 모든 일시 중단 시 선택적 시간 제한
* 선택적 TCP 통계
* Azure RTOS TraceX를 통한 시스템 수준 추적
* 직관적인 TCP API: *nx_tcp_\**

### <a name="icmp---internet-control-message-protocol-icmp"></a>ICMP - ICMP(Internet Control Message Protocol)

* 최소 2.5KB FLASH
* IPv4 지원
* IXIA IxANVL 유효성 검사 완료
* Ping 요청 및 Ping 응답
* Ping 요청 시 선택적 스레드 일시 중단
* 모든 일시 중단 시 선택적 시간 제한
* 선택적 ICMP 통계
* Azure RTOS TraceX를 통한 시스템 수준 추적
* 직관적인 ICMP API: *nx_icmp_\**

### <a name="ipv4---internet-protocol-ip"></a>IPv4 - IP(인터넷 프로토콜)

* 최소 3.5KB ~ 8.5KB FLASH, 2KB ~ 3KB RAM 공간
* Piconet™ 아키텍처
* 빠른 근거리 통신 속도 성능
* 여러 인터페이스 지원
* 멀티홈 지원
* 정적 라우팅 지원
* IP 조각화/리어셈블리 지원
* IPv4 지원
* IXIA IxANVL 유효성 검사 완료
* 단계 II 준비 로고 인증
* 선택적 IP 통계
* 잘 정의된 직관적인 물리적 계층 드라이버 인터페이스
* Azure RTOS TraceX를 통한 시스템 수준 추적
* 직관적인 IP 계층 API: *nx_ip_\** , *nxd_ip_\**
* TUV 및 UL에서 IEC 61508 SIL 4, IEC 62304 클래스 C, ISO 26262 ASIL D 및 EN 50128 SW-SIL4로 사전 인증

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a>ARP/RARP - ARP(주소 확인 프로토콜), RARP(역주소 확인 프로토콜)

* 최소 1.7KB FLASH, RAM 크기
* 32비트의 동적 확인 IPv4 및 48비트 MAC 주소
* IXIA IxANVL 유효성 검사 완료
* 유연한 사용자 정의 ARP 캐시
* 무상 ARP 지원
* 애플리케이션에 의해 결정되는 선택적 ARP/RARP 통계
* Azure RTOS TraceX를 통한 시스템 수준 추적
* 직관적인 ARP/RARP API: *nx_arp_\** , *nx_rarp_\**

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a>이더넷, WiFi, Bluetooth LE, 15.4 등

## <a name="small-footprint"></a>적은 공간

Azure RTOS NetX는 기본 IP 및 UDP 지원에 대한 공간이 9KB ~ 15KB로 매우 적습니다. TCP 기능을 위해서는 추가적으로 10KB ~ 13KB의 명령 영역 메모리가 필요합니다. Azure RTOS NetX RAM 사용량은 일반적으로 2.6KB에서 3.6KB까지이며, 애플리케이션에 의해 정의되는 패킷 풀 메모리를 포함합니다. Azure RTOS ThreadX와 같이 Azure RTOS NetX의 크기는 애플리케이션에서 사용하는 서비스에 따라 자동으로 조정됩니다. 이렇게 하면 사실상 복잡한 구성 및 빌드 매개 변수가 제거되어 개발자가 더 쉽게 작업을 수행할 수 있습니다.

## <a name="fast-execution"></a>고속 실행

Azure RTOS NetX는 복사 없는 패킷 송신/수신 구현을 제공하며 Azure RTOS ThreadX와 고도로 통합되어 가장 빠른 성능을 실현합니다. 예를 들어 Azure RTOS NetX는 일반적으로 프로세서 주기 중 일부만 사용하면서 80MHz 프로세서(또는 이하)에서 근거리 통신 속도 데이터 전송을 수행할 수 있습니다.

## <a name="simple-easy-to-use"></a>간단하고 손쉬운 사용

Azure RTOS NetX는 사용이 간단합니다. Azure RTOS NetX API는 직관적이고 매우 기능적입니다. API 이름은 “대단히 이해하기 어려운” 것이 아니며, 다른 네트워킹 제품에 매우 흔한 고도로 축약된 이름도 아닌 실제 단어로 구성됩니다. 모든 Azure RTOS NetX API에는 선행 *nx_* 가 있으며 명사-동사 명명 규칙을 따릅니다. 또한 API 전체에 걸쳐 기능적 일관성이 있습니다. 예를 들어 일시 중단된 모든 API 함수는 동일한 방식으로 작동하는 선택적 시간 제한이 있습니다. 레거시 애플리케이션의 경우 Azure RTOS NetX는 추가 BSD 소켓 호환 계층을 제공합니다. 이 계층을 통해 개발자는 수많은 네트워킹 애플리케이션을 쉽게 마이그레이션할 수 있습니다.

## <a name="interoperability-verification"></a>상호 운용성 확인

Azure RTOS NetX는 RFC 표준을 준수하며 대부분의 공급 업체에 대해 디바이스와의 완벽한 상호 운용성을 제공합니다. 또한 Azure RTOS NetX는 Azure RTOS NetX 코어 TCP/IP 프로토콜 구현에 업계 표준 IxANVL(자동화된 네트워크 유효성 검사 라이브러리)을 활용합니다.

## <a name="advanced-technology"></a>고급 기술

Azure RTOS NetX는 다음을 포함하는 고급 기술입니다.

* Piconet™ 아키텍처
* 자동 크기 조정
* UDP Fast-Path Technology™
* 유연한 패킷 관리
* 복사 없는 API 및 구현
* 멀티홈 지원
* 모든 일시 중단 시 선택적 시간 제한
* 정적 라우팅 지원
* Azure RTOS TraceX 시스템 분석 지원

## <a name="fastest-time-to-market"></a>가장 빠른 출시 시간

Azure RTOS NetX는 설치, 학습, 사용, 디버그, 확인, 인증 및 유지 관리를 손쉽게 수행할 수 있습니다. 결과적으로 Azure RTOS NetX는 Broadcom, Gainspan 등의 많은 SoC를 포함하여 임베디드 IoT 디바이스에 가장 많이 사용되는 TCP/IP 스택 중 하나입니다. 일관적인 출시 시간 이점은 다음을 기반으로 합니다.

* 품질 설명서 – [Azure RTOS NetX 사용자 가이드](about-this-guide.md)를 검토하고 직접 확인하세요.
* 전체 소스 코드 가용성
* 사용하기 쉬운 API
* 포괄적인 고급 기능 세트

## <a name="one-simple-license"></a>하나의 간단한 라이선스

사전에 사용이 허가된 디바이스에 배포하는 경우에는 소스 코드를 사용 및 테스트하는 데 비용이 들지 않으며 프로덕션 라이선스에 대한 비용도 부과되지 않습니다. 다른 모든 디바이스에는 간단한 연간 라이선스가 필요합니다.

## <a name="full-highest-quality-source-code"></a>최고 품질의 전체 소스 코드

여러 해에 걸쳐 Azure RTOS NetX 소스 코드는 품질 및 이해 용이성의 기준을 확립했습니다. 또한 파일당 하나의 함수를 포함하는 규칙을 통해 손쉬운 소스 탐색을 제공합니다.

## <a name="supports-most-popular-architectures"></a>가장 인기 있는 아키텍처 지원

Azure RTOS NetX는 다음과 같은 고급 아키텍처를 포함하여 완벽하게 테스트되고 완전히 지원되는 가장 인기 있는 32/64비트 마이크로프로세서에서 실행됩니다.

**Analog Devices**: SHARC, Blackfin, CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: Apollo MCU

**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M

**Cadence**: Xtensa, Diamond

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi

**Cypress**: RISC-V

**EnSilica**: eSi-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10

**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

**Microsemi**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, Synergy

**Silicon Labs**: EFM32

**Synopsys**: ARC 600, 700, ARC EM, ARC HS

**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7

**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C

**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*나열된 모든 타이밍 및 크기 수치는 예상치이며, 개발 플랫폼에 따라 다를 수 있습니다.*
