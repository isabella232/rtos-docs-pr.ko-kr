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
# <a name="overview-of-azure-rtos-netx-duo"></a>Azure RTOS NetX Duo 개요

Azure RTOS NetX Duo 임베디드 TCP/IP 네트워크 스택은 긴밀하게 포함된 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 Microsoft의 고급, 산업용 이중 IPv4 및 IPv6 TCP/IP 네트워크 스택입니다. NetX Duo는 IPv4, IPv6, TCP, UDP 등의 핵심 네트워크 프로토콜과 함께 포함된 애플리케이션을 제공하고 더 높은 수준의 추가 기능 프로토콜을 완벽하게 제공합니다. Azure RTOS NetX Duo는 Azure RTOS NetX Secure IPsec 및 Azure RTOS NetX Secure SSL/TLS/DTLS를 비롯한 추가 기능형 추가 보안 제품을 통해 보안을 제공합니다. 이뿐 아니라 Azure RTOS NetX Duo는 적은 메모리 공간, 빠른 실행 및 뛰어난 사용 편의성을 제공하므로 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.

## <a name="api-protocols"></a>API 프로토콜

### <a name="mqtt"></a>MQTT

* MQTT(메시징 큐 원격 분석 전송)
* 최소 2.7KB FLASH
* 직관적인 MQTT API: *nx_mqtt_* \*

### <a name="auto-ip"></a>자동 IP

* 자동 IPv4 주소 할당
* 최소 1.2KB, 300바이트의 RAM
* 직관적인 AutoIP API: *nx_autoip_\**

### <a name="http-https"></a>HTTP, HTTPS

#### <a name="http-10"></a>HTTP 1.0

* HTTP(Hypertext Transfer Protocol)
* 최소 2.8KB~4.8KB 플래시/0.4KB~1.0KB RAM
* 클라이언트 및 서버 지원
* 직관적인 API: *nx_http_\**

#### <a name="httphttps-11"></a>HTTP/HTTPS 1.1

* HTTP(Hypertext Transfer Protocol)
* 최소 3.0KB~9.5KB 플래시/0.5KB~2KB RAM
* 클라이언트 및 서버 지원
* 다중 수신 클라이언트 세션
* 일반 텍스트 및 암호화된 HTTPS
* 영구 연결 지원
* 다중 파트 파일 업로드
* Azure RTOS NetX Secure TLS와 완전히 통합
* 직관적인 API: *nx_web_http\**

### <a name="smtp"></a>SMTP

* SMTP(Simple Mail Transfer Protocol)
* 최소 4.1KB 및 0.6KB의 RAM 공간
* 클라이언트 지원
* 직관적인 SMTP API: *nx_smtp_\**

### <a name="dhcp"></a>DHCP

* DHCP(Dynamic Host Configuration Protocol)
* 최소 3.6KB~4.6KB FLASH, 2.7KB RAM 공간
* 클라이언트 및 서버 지원
* IPv4 및 IPv6 지원
* 직관적인 DHCP API: *nx_dhcp_\**

### <a name="nat"></a>NAT

* NAT(Network Address Translation)
* 최소 3.5KB 및 0.6KB의 RAM 공간
* IPv4 주소 지원
* 직관적인 NAT API: *nx_nat_\**
* NAT는 Azure RTOS NetX Duo에서만 사용할 수 있습니다.

### <a name="snmp"></a>SNMP

* SNMP(Simple Network Management Protocol)
* 최소 10.9KB 및 2.6KB의 RAM 공간
* VI, V2 및 V3에 대한 에이전트 지원
* 직관적인 SNMP API: *nx_snmp_\**

### <a name="dns-mdns-dns-sd"></a>DNS, mDNS, DNS-SD

* DNS(Domain Name System)
* mDNS(Multicast Domain Name System)
* DNS-SD(DNS 기반 서비스 검색)
* DNS 최소 2.4KB~3KB FLASH, 1KB의 RAM 공간
* 클라이언트 지원
* 직관적인 API: *nx_dns_\**
* mDNS 및 DNS-SD는 Azure RTOS NetX Duo에서만 사용할 수 있습니다.

### <a name="p0p3"></a>P0P3

* POP3(Post Office Protocol 버전 3)
* 최소 8.1KB 및 1.4KB의 RAM 공간
* 클라이언트 지원
* 직관적인 P0P3 API: *nx_pop3_\**

### <a name="telnet"></a>TELNET

* 최소 0.5KB 및 0.3KB의 RAM 공간
* 클라이언트 및 서버 지원
* 직관적인 Telnet API: *nx_telnet_\**

### <a name="ftp-tftp"></a>FTP, TFTP

* FTP(파일 전송 프로토콜)
* TFTP(Trivial File Transfer Protocol)
* FTP 최소 1.8KB~7.2KB FLASH, 0.6KB~2.1KB의 RAM 공간
* TFTP 최소 1.7KB~2.4KB FLASH, 0.3KB~1.8KB의 RAM 공간
* 클라이언트 및 서버 지원
* 직관적인 FTP 및 TFTP API: *nx_ftp_\** 또는 *nx_tftp_\**

### <a name="ppp-pppoe"></a>PPP, PPPoE

* PPP(지점 간 프로토콜)
* PPPoE(이더넷을 통한 지점 간 프로토콜)
* 최소 7.1KB 및 3.8KB의 RAM 공간
* 직관적인 PPP API: *nx_ppp_\**

* PPPoE는 Azure RTOS NetX Duo에서만 사용할 수 있습니다.

### <a name="sntp"></a>SNTP

* SNTP(Simple Network Time Protocol)
* 최소 4KB 및 0.5KB RAM
* 클라이언트 지원
* 직관적인 SNTP API: *nx_sntp_\**

### <a name="azure-rtos-netx-duo-api"></a>Azure RTOS NetX Duo API

* 직관적이고 일관성 있는 API
* 명사-동사 명명 규칙
* 빠르고 복사 없는 API 구현
* 모든 API에는 Azure RTOS NetX로 쉽게 식별할 수 있도록 <i>nx_*</i>가 앞에 옵니다.
* 차단 API에 선택적 스레드 시간 제한 적용
* 자세한 내용은 [Azure RTOS NetX Duo 사용자 가이드](about-this-guide.md)를 참조하세요.
* 레거시 소켓 코드 포팅을 위한 선택적 BSD 계층

### <a name="igmp"></a>IGMP

* IGMP(Internet Group Management Protocol)
* 최소 2.5KB FLASH
* IPv4 멀티캐스트 그룹 지원
* IXIA IxANVL 유효성 검사 완료
* 선택적 IGMP 통계
* Azure RTOS ThreadX를 통한 시스템 수준 추적
* 직관적인 IGMP API: *nx_igmp_\**

### <a name="azure-rtos-netx-secure-dtls"></a>Azure RTOS NetX Secure DTLS

* DTLS(데이터그램 전송 계층 보안) 1.0 및 1.2
* 최소 11KB FLASH
* 고속, 소프트웨어 RSA 2048비트 키 크기 ~1초 @120MHz
* 간소화된 X.509 구현
* Azure RTOS NetX Duo UDP 소켓과 완전히 통합
* 하드웨어 암호화 지원
* 소프트웨어 암호화 지원: RSA(모든 키 크기), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2(SHA-224, SHA-256, SHA-384, SHA-512)
* ECDSA(서명) 및 ECDH(암호화)를 사용하는 ECC(Elliptic Curve Cryptography)(P-곡선 192/224/256/384/521 포함)
* 암호화된 키 지원(하드웨어 종속)

### <a name="azure-rtos-netx-secure-tls"></a>Azure RTOS NetX Secure TLS

* TLS(전송 계층 보안) 1.0, 1.1 및 1.2
* 최소 8.8KB FLASH
* 고속, 소프트웨어 RSA 2048비트 키 크기 ~1초 @120MHz
* 간소화된 X.509 구현
* Azure RTOS NetX Duo TCP 소켓과 완전히 통합
* 하드웨어 암호화 지원
* 소프트웨어 암호화 지원: RSA(모든 키 크기), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2(SHA-224, SHA-256, SHA-384, SHA-512)
* ECDSA(서명) 및 ECDH(암호화)를 사용하는 ECC(Elliptic Curve Cryptography)(P-곡선 192/224/256/384/521 포함)
* 암호화된 키 지원(하드웨어 종속)

### <a name="icmp"></a>ICMP

* ICMP(Internet Control Message Protocol)
* 최소 2.5KB FLASH
* IPv4 및 IPv6 지원
* IXIA IxANVL 유효성 검사 완료
* Ping 요청 및 Ping 응답
* Ping 요청 시 선택적 스레드 일시 중단
* 모든 일시 중단 시 선택적 시간 제한
* 선택적 ICMP 통계
* Azure RTOS TraceX를 통한 시스템 수준 추적
* 직관적인 ICMP API: *nx_icmp_\**

### <a name="udp"></a>UDP

* UDP(사용자 데이터그램 프로토콜)
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

### <a name="tcp"></a>TCP

* TCP(Transmission Control Protocol)
* 최소 10.5KB~12.5KB FLASH, 소켓당 280바이트의 RAM
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

### <a name="arprarp"></a>ARP/RARP

* ARP(주소 확인 프로토콜)
* RARP(역주소 확인 프로토콜)
* 최소 1.7KB FLASH, RAM 크기
* 32비트의 동적 확인 IPv4 및 48비트 MAC 주소
* IXIA IxANVL 유효성 검사 완료
* 유연한 사용자 정의 ARP 캐시
* 무상 ARP 지원
* 애플리케이션에 의해 결정되는 선택적 ARP/RARP 통계
* Azure RTOS TraceX를 통한 시스템 수준 추적
* 직관적인 ARP/RARP API: *nx_arp_\** , *nx_rarp_\**

### <a name="ipv4-amp-ipv6"></a>IPv4 &amp; IPv6

* IP(인터넷 프로토콜)
* 최소 3.5KB~8.5KB FLASH, 2KB~3KB의 RAM 공간
* Piconet™ 아키텍처
* 빠른 근거리 통신 속도 성능
* 여러 인터페이스 지원
* 멀티홈 지원
* 정적 라우팅 지원
* IP 조각화/리어셈블리 지원
* IPv4 및 IPv6 주소 지원
* IXIA IxANVL 유효성 검사 완료
* 단계 II IPv6 준비 로고 인증
* 선택적 IP 통계
* 잘 정의된 직관적인 물리적 계층 드라이버 인터페이스
* Azure RTOS TraceX를 통한 시스템 수준 추적
* 직관적인 IP 계층 API: *nx_ip_\** , *nxd_ip_\** , *nxd_ipv6_\**
* TUV 및 UL에서 IEC 61508 SIL 4, IEC 62304 클래스 C, ISO 26262 ASIL D 및 EN 50128 SW-SIL4로 사전 인증

### <a name="azure-rtos-netx-secure-ipsec"></a>Azure RTOS NetX Secure IPSEC

* IPSEC(인터넷 프로토콜 보안)
* IP 계층
* 하드웨어 암호화 지원
* 다음을 포함한 소프트웨어 암호화 지원
    * DES, 3DES
    * AES
    * HMAC-MD5
    * HMAC-SHA1
* IKE(Internet Key Exchange) 버전 2 지원
* 직관적인 IPsec API: *nx_ipsec_\**
* IPsec은 Azure RTOS NetX Duo에서만 사용할 수 있습니다.

## <a name="small-footprint"></a>적은 메모리 공간

Azure RTOS NetX Duo는 기본 IP 및 UDP 지원에 대한 공간이 9KB ~ 15KB로 매우 적습니다. TCP 기능을 위해서는 추가적으로 10KB ~ 13KB의 명령 영역 메모리가 필요합니다. Azure RTOS NetX Duo RAM 사용량은 일반적으로 2.6KB에서 3.6KB까지이며, 애플리케이션에 의해 정의되는 패킷 풀 메모리를 포함합니다. Azure RTOS ThreadX와 같이 Azure RTOS NetX Duo의 크기는 애플리케이션에서 사용하는 서비스에 따라 자동으로 조정됩니다. 이렇게 하면 사실상 복잡한 구성 및 빌드 매개 변수가 제거되어 개발자가 더 쉽게 작업을 수행할 수 있습니다.

## <a name="fast-execution"></a>고속 실행

Azure RTOS NetX Duo는 복사 없는 패킷 송신/수신 구현을 제공하며 Azure RTOS ThreadX와 고도로 통합되어 가장 빠른 성능을 실현합니다. 예를 들어 Azure RTOS NetX Duo는 일반적으로 프로세서 주기 중 일부만 사용하면서 80MHz(또는 이하) 프로세서에서 근거리 통신 속도 데이터 전송을 수행할 수 있습니다.

## <a name="simple-easy-to-use"></a>간단하고 손쉬운 사용

Azure RTOS NetX Duo API는 직관적이고 간단하며 기능이 뛰어납니다.

API 이름은 “대단히 이해하기 어려운” 것이 아니며, 다른 네트워킹 제품에 매우 흔한 고도로 축약된 이름도 아닌 실제 단어로 구성됩니다. 모든 Azure RTOS NetX Duo API에는 선행 *nx_* 가 있으며 명사-동사 명명 규칙을 따릅니다. 또한 API 전체에 걸쳐 기능적 일관성이 있습니다. 예를 들어 일시 중단된 모든 API 함수는 동일한 방식으로 작동하는 선택적 시간 제한이 있습니다.

레거시 애플리케이션의 경우 Azure RTOS NetX Duo는 추가 BSD 소켓 호환 계층을 제공합니다. 이 계층을 통해 개발자는 수많은 네트워킹 애플리케이션을 쉽게 마이그레이션할 수 있습니다.

## <a name="safe-and-secure"></a>안전 및 보안 유지

Azure RTOS NetX Duo는 안전합니다. 이 보안은 IPsec, SSL, TLS 및 DTLS를 비롯한 추가 기능형 보안 제품을 통해 제공됩니다. 또한 애플리케이션은 Azure RTOS NetX Duo에 대한 모든 외부 액세스를 완벽하게 제어하여 보안 위험을 훨씬 더 쉽게 파악할 수 있도록 합니다.

Microsoft Azure RTOS는 기본 MCU/MPU 하드웨어 보호 메커니즘을 사용하여 통신을 보호하고 코드 및 데이터 격리를 만드는 구성 요소를 OEM에 제공합니다. 디바이스가 특정 사용 사례에 따른 변화하는 보안 요구 사항을 완벽하게 충족하는지 확인하는 것은 궁극적으로 디바이스 빌더의 책임입니다.

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a>TUV 및 UL을 비롯한 여러 안전 표준의 사전 인증

Azure RTOS NetX Duo는 안전이 매우 중요한 시스템에서의 사용을 위해, IEC-61508 SIL 4, IEC-62304  SW 안전 등급 C, ISO 26262 ASIL D 및 EN 50128에 따라 SGS-TUV Saar 인증을 받았습니다. 이 인증은 "전기, 전자 및 프로그램 가능한 전자 안전 관련 시스템의 기능적 안전”에 대한 최고 수준의 IEC-61508, IEC-62304, ISO 26262 and EN 50128의 안전 무결성 등급에 따라, Azure RTOS NetX Duo를 보안 관련 소프트웨어의 개발에 사용할 수 있음을 확인합니다. 독일 SGS-Group 및 TUV Saarland의 공동 벤처인 SGS-TUV Saar는 세계적으로 안전 관련 시스템용 포함 소프트웨어를 테스트, 감사, 확인 및 검증하는 최고 권위의 독립 기업으로 자리했습니다. 산업 보안 표준 IEC 61508과, 거기에서 파생된 모든 표준(IEC-62304, ISO 26262 및 EN 50128 포함)은 전기, 전자 및 프로그래밍 가능한 전자 안전 관련 의료 장비, 공정 제어 시스템, 산업용 기계, 자동차, 철도 제어 시스템의 기능 안전을 보장하는 데 사용됩니다.

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="인증":::

UL은 Azure RTOS NetX Duo가 프로그래밍 가능한 구성 요소에서의 소프트웨어에 대한 UL 60730-1 부칙 H, CSA E60730-1 부칙 H, IEC 60730-1 부칙 H, UL 60335-1 부칙 R, IEC 60335-1 부칙 R 및 UL 1998 안전 표준을 준수한다고 인정했습니다. UL은 공공 에너지 도입, 첨단 지속 가능성 기술, 재생 에너지, 나노 기술 등을 망라하는 안전 솔루션 혁신 분야에서 백년이 넘는 전문 기술을 갖춘 글로벌 독립 안전 과학 기업입니다.

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="CRU UL 인증":::

TUV 및 UL 인증과 관련한 아티팩트(인증서, 안전 매뉴얼, 테스트 보고서 등)는 판매 가능합니다.

애플리케이션에 추가 인증이 필요한 경우, 실제 하드웨어 플랫폼을 사용한 다양한 표준에 대한 턴키 방식의 인증을 제공하고 애플리케이션 코드까지도 다루는 인증 서비스를 Microsoft를 통해 사용할 수 있습니다. 인증 서비스에 대한 자세한 내용은 Microsoft에 문의하세요.

## <a name="eal4-common-criteria-security-certification"></a>EAL4+ Common Criteria 보안 인증

Azure RTOS는 EAL4+ Common Criteria 보안 인증을 달성했습니다. TOE(평가 대상)은 Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS 및 Azure RTOS NetX MQTT를 포함합니다. 이는 긴밀하게 포함된 센서, 디바이스, 에지 라우터 및 게이트웨이에 필요한 가장 일반적인 IoT 프로토콜을 나타냅니다.

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="EAL 인증":::

Microsoft Azure RTOS SC 보안 인증에 사용되는 IT 보안 평가 시설은 Brightsight BV이고 인증 기관은 SERTIT입니다.

## <a name="fips-140-2-validated"></a>FIPS 140-2 유효성 검사

Azure RTOS NetX 암호화 라이브러리는 암호화 모듈에 대한 요구 사항을 지정하는 소프트웨어용 FIPS 140-2(Federal Information Processing Standard 140-2) 인증을 획득했습니다. FIPS 140-2에 따르면 암호화 기반 보안을 사용하는 모든 연방 정부 기관 및 부서는 암호화 강도 및 기능과 관련된 특정 표준을 충족해야 합니다. 이러한 암호화 기반 보안 표준은 캐나다 및 유럽 연합에서도 인정되고 있습니다.

Azure RTOS NetX 암호화 라이브러리에 사용되는 정보 보안 평가 랩은 atsec이었으며 인증 기관은 NIST(National Institute of Standards and Technology)입니다. 자세한 내용은 [NIST 웹 사이트](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394)를 참조하세요.

## <a name="interoperability-verification"></a>상호 운용성 확인

NetX Duo는 RFC 표준을 준수하며 대부분의 공급 업체에 대해 디바이스와의 완벽한 상호 운용성을 제공합니다.

![IPv6 준비 로고](./media/overview-netx-duo/ipv6-ready-logo.png)

Azure RTOS NetX Duo는 규정 준수 및 상호 운용성 테스트를 통과했으며 IPv6 포럼에서 관리 및 검증되었음을 입증하는 엄격한 IPv6 준비 로고 인증을 얻은 유일한 임베디드 TCP/IP 스택 중 하나입니다. 또한 NetX Duo는 NetX Duo 코어 TCP/IP 프로토콜 구현에 업계 표준 IxANVL(자동화된 네트워크 유효성 검사 라이브러리)을 활용합니다.

## <a name="comprehensive-iot-solution"></a>포괄적인 IoT 솔루션

Azure RTOS NetX Duo는 기본 IP 및 UDP 지원에 대한 공간이 9KB ~ 15KB로 매우 적습니다. NetX Duo는 긴밀하게 포함된 IoT 애플리케이션을 위한 가장 포괄적인 TCP/IP 네트워킹 중 하나입니다. 이 지원에는 다음과 같은 추가 기능형 프로토콜 제품이 포함됩니다.

MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP

## <a name="advanced-technology"></a>고급 기술

Azure RTOS NetX Duo는 다음을 포함하는 고급 기술입니다.

* Piconet™ 아키텍처
* 자동 크기 조정
* UDP Fast-Path Technology™
* 유연한 패킷 관리
* 복사 없는 API 및 구현
* 멀티홈 지원
* 모든 일시 중단 시 선택적 시간 제한
* 정적 라우팅 지원
* IPsec
* SSL/TLS/DTLS
* Azure RTOS TraceX 시스템 분석 지원

## <a name="fastest-time-to-market"></a>가장 빠른 출시 시간

Azure RTOS NetX Duo는 설치, 학습, 사용, 디버그, 확인, 인증 및 유지 관리를 손쉽게 수행할 수 있습니다. 결과적으로 NetX Duo는 Broadcom, Gainspan 등의 많은 Soc를 비롯한 임베디드 IoT 디바이스에서 가장 많이 사용되는 TCP/IP 스택 중 하나로 자리잡았습니다. 일관적인 출시 기간 단축은 다음을 토대로 가능해졌습니다.

* 품질 설명서 – [Azure RTOS NetX Duo 사용자 가이드](about-this-guide.md)를 검토하고 직접 확인하세요.
* 전체 소스 코드 가용성
* 사용하기 쉬운 API
* 포괄적인 고급 기능 세트

## <a name="one-simple-license"></a>하나의 간단한 라이선스

사전에 사용이 허가된 디바이스에 배포하는 경우에는 소스 코드를 사용 및 테스트하는 데 비용이 들지 않으며 프로덕션 라이선스에 대한 비용도 부과되지 않습니다. 다른 모든 디바이스에는 간단한 연간 라이선스가 필요합니다.

## <a name="full-highest-quality-source-code"></a>최고 품질의 전체 소스 코드

오랜 시간을 통해 Azure RTOS NetX Duo 소스 코드는 품질 및 이해 용이성의 기준을 정립했습니다. 또한 파일당 하나의 함수를 포함하는 규칙을 통해 손쉬운 소스 탐색을 제공합니다.

## <a name="supports-most-popular-architectures"></a>대부분의 주요 아키텍처 지원

Azure RTOS NetX Duo는 다음과 같은 고급 아키텍처를 포함하여 완벽하게 테스트되고 완전히 지원되는 가장 인기 있는 32/64비트 마이크로프로세서에서 실행됩니다.

**아날로그 디바이스**: SHARC, Blackfin, CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: pollo MCU

**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64비트/A7x 64비트/R4/R5, TrustZone ARMv8-M

**Cadence**: Xtensa, Diamond

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi

**Cypress**: RISC-V

**EnSilica**: eSi-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10

**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

**Microsemi**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, Synergy

**Silicon** Labs: EFM32

**Synopsys**: ARC 600, 700, ARC EM, ARC HS

**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7

**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C

**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*나열된 모든 타이밍 및 크기 수치는 예상치이며, 개발 플랫폼에 따라 다를 수 있습니다.*

## <a name="related-services"></a>관련 서비스

IoT RTOS용 Azure Security Center 보안 모듈은 Azure RTOS 디바이스에 포괄적인 보안 솔루션을 제공합니다. Azure RTOS용 보안 모듈은 악의적인 네트워크 활동 검색, 사용자 지정 경고 기반 디바이스 동작 기준 지정을 제공하고 디바이스 보안을 강화하는 데 도움이 됩니다. [Azure RTOS용 보안 모듈](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos)에 대해 자세히 알아보거나 [Azure RTOS용 보안 모듈 구성](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) 빠른 시작을 진행하세요.

## <a name="next-steps"></a>다음 단계

NetX Duo에 대해 자세히 알아보려면 [Azure RTOS NetX Duo 사용자 가이드](about-this-guide.md)를 참조하세요.
