---
title: Azure RTOS NetX Duo 이해
description: Azure RTOS NetX Duo는 긴밀하게 포함된 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 고급, 산업용 TCP/IP 네트워크 스택입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 6112ab5cb711ca1a5c83fd5cd4b43abc0302c6c5
ms.sourcegitcommit: f9d8cf23becf96d5bd6d31dd54f89c48962fd09b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549336"
---
# <a name="overview-of-azure-rtos-netx-duo"></a>Azure RTOS NetX Duo 개요

Azure RTOS NetX Duo 임베디드 TCP/IP 네트워크 스택은 긴밀하게 포함된 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 Microsoft의 고급, 산업용 이중 IPv4 및 IPv6 TCP/IP 네트워크 스택입니다. NetX Duo는 IPv4, IPv6, TCP, UDP 등의 핵심 네트워크 프로토콜과 함께 포함된 애플리케이션을 제공하고 더 높은 수준의 추가 기능 프로토콜을 완벽하게 제공합니다. Azure RTOS NetX Duo는 Azure RTOS NetX Secure IPsec 및 Azure RTOS NetX Secure SSL/TLS/DTLS를 비롯한 추가 기능형 추가 보안 제품을 통해 보안을 제공합니다. 이뿐 아니라 Azure RTOS NetX Duo는 적은 메모리 공간, 빠른 실행 및 뛰어난 사용 편의성을 제공하므로 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.

## <a name="api-protocols"></a>API 프로토콜

### <a name="mqtt"></a>MQTT

* MQTT(메시징 큐 원격 분석 전송)
* 최소 2.7KB FLASH

### <a name="auto-ip"></a>자동 IP

* 자동 IPv4 주소 할당
* 최소 1.2KB, 300바이트의 RAM

### <a name="http-https"></a>HTTP, HTTPS

#### <a name="http-10"></a>HTTP 1.0

* HTTP(Hypertext Transfer Protocol)
* 최소 2.8KB~4.8KB 플래시/0.4KB~1.0KB RAM
* 클라이언트 및 서버 지원

#### <a name="httphttps-11"></a>HTTP/HTTPS 1.1

* HTTP(Hypertext Transfer Protocol)
* 최소 3.0KB~9.5KB 플래시/0.5KB~2KB RAM
* 클라이언트 및 서버 지원
* 다중 수신 클라이언트 세션
* 일반 텍스트 및 암호화된 HTTPS
* 영구 연결 지원
* 다중 파트 파일 업로드
* Azure RTOS NetX Secure TLS와 완전히 통합

### <a name="smtp"></a>SMTP

* SMTP(Simple Mail Transfer Protocol)
* 최소 4.1KB 및 0.6KB의 RAM 공간
* 클라이언트 지원

### <a name="dhcp"></a>DHCP

* DHCP(Dynamic Host Configuration Protocol)
* 최소 3.6KB~4.6KB FLASH, 2.7KB RAM 공간
* 클라이언트 및 서버 지원
* IPv4 및 IPv6 지원

### <a name="nat"></a>NAT

* NAT(Network Address Translation)
* 최소 3.5KB 및 0.6KB의 RAM 공간
* IPv4 주소 지원
* NAT는 Azure RTOS NetX Duo에서만 사용할 수 있습니다.

### <a name="snmp"></a>SNMP

* SNMP(Simple Network Management Protocol)
* 최소 10.9KB 및 2.6KB의 RAM 공간
* VI, V2 및 V3에 대한 에이전트 지원

### <a name="dns-mdns-dns-sd"></a>DNS, mDNS, DNS-SD

* DNS(Domain Name System)
* mDNS(Multicast Domain Name System)
* DNS-SD(DNS 기반 서비스 검색)
* DNS 최소 2.4KB~3KB FLASH, 1KB의 RAM 공간
* 클라이언트 지원
* mDNS 및 DNS-SD는 Azure RTOS NetX Duo에서만 사용할 수 있습니다.

### <a name="pop3"></a>POP3

* POP3(Post Office Protocol 버전 3)
* 최소 8.1KB 및 1.4KB의 RAM 공간
* 클라이언트 지원

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

## <a name="safe-and-secure"></a>안전 및 보안 유지

Azure RTOS NetX Duo는 안전합니다. 이 보안은 IPsec, SSL, TLS 및 DTLS를 비롯한 추가 기능형 보안 제품을 통해 제공됩니다. 또한 애플리케이션은 Azure RTOS NetX Duo에 대한 모든 외부 액세스를 완벽하게 제어하여 보안 위험을 훨씬 더 쉽게 파악할 수 있도록 합니다.

Microsoft Azure RTOS는 기본 MCU/MPU 하드웨어 보호 메커니즘을 사용하여 통신을 보호하고 코드 및 데이터 격리를 만드는 구성 요소를 OEM에 제공합니다. 디바이스가 특정 사용 사례에 따른 변화하는 보안 요구 사항을 완벽하게 충족하는지 확인하는 것은 궁극적으로 디바이스 빌더의 책임입니다.


## <a name="interoperability-verification"></a>상호 운용성 확인

NetX Duo는 RFC 표준을 준수하며 대부분의 공급 업체에 대해 디바이스와의 완벽한 상호 운용성을 제공합니다.

![IPv6 준비 로고](./media/overview-netx-duo/ipv6-ready-logo.png)

Azure RTOS NetX Duo는 규정 준수 및 상호 운용성 테스트를 통과했으며 IPv6 포럼에서 관리 및 검증되었음을 입증하는 엄격한 IPv6 준비 로고 인증을 얻은 유일한 임베디드 TCP/IP 스택 중 하나입니다. 또한 NetX Duo는 NetX Duo 코어 TCP/IP 프로토콜 구현에 업계 표준 IxANVL(자동화된 네트워크 유효성 검사 라이브러리)을 활용합니다.

## <a name="comprehensive-iot-solution"></a>포괄적인 IoT 솔루션

NetX Duo는 긴밀하게 포함된 IoT 애플리케이션을 위한 가장 포괄적인 TCP/IP 네트워킹 중 하나입니다. 이 지원에는 다음과 같은 추가 기능형 프로토콜 제품이 포함됩니다.

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

## <a name="related-services"></a>관련 서비스

### <a name="azure-iot"></a>Azure IoT

NetX Duo에는 Azure IoT 서비스에 쉽게 연결할 수 있도록 Azure RTOS와 Embedded C용 Azure SDK 사이의 바인딩 계층 역할을 하는 플랫폼별 라이브러리인 [ Azure RTOS용 Azure IoT 미들웨어](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md)가 포함되어 있습니다. Azure IoT 미들웨어의 목표는 다음과 같습니다.
* 개발자가 애플리케이션에 필요한 스마트 클라이언트 인터페이스(IoTHub_Client, DeviceProvisioning_Client)를 제공합니다.
* Embedded C SDK와 플랫폼 간의 상호 작용을 오케스트레이션합니다.
* Azure RTOS 플랫폼 초기화를 제공합니다.
* IoT 플러그 앤 플레이 지원.
* 보안 기능.
* 리소스 제한 인식.
* 프로토콜 지원.

![Azure RTOS NetX Duo 관련 서비스](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a>Azure Defender

Azure Defender for IoT 보안 모듈은 Azure RTOS 디바이스에 대한 포괄적인 보안 솔루션을 제공합니다. Azure RTOS용 보안 모듈은 악의적인 네트워크 활동 검색, 사용자 지정 경고 기반 디바이스 동작 기준 지정을 제공하고 디바이스 보안을 강화하는 데 도움이 됩니다. [Azure RTOS용 보안 모듈](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos)에 대해 자세히 알아보거나 [Azure RTOS용 보안 모듈 구성](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) 빠른 시작을 진행하세요.

### <a name="device-update-for-iot-hub"></a>IoT Hub용 디바이스 업데이트 문서

[Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update)는 IoT 디바이스에 대한 무선(OTA) 업데이트를 배포할 수 있도록 하는 서비스입니다. Device Update for IoT Hub 모듈은 Azure RTOS NetX Duo에서 Device Update for IoT Hub를 구현한 것입니다. 디바이스 빌더가 애플리케이션에서 디바이스 업데이트 기능을 통합할 수 있도록 간단한 API를 제공합니다.

시작 가이드가 포함된 주요 반도체 평가 보드의 샘플을 참조하여 디바이스에 무선(OTA) 업데이트를 구성, 빌드 및 배포하는 방법을 알아봅니다.

또한 [Azure RTOS가 있는 Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system) 사용에 대해 자세히 알아볼 수 있습니다.

## <a name="next-steps"></a>다음 단계

NetX Duo에 대해 자세히 알아보려면 [Azure RTOS NetX Duo 사용자 가이드](about-this-guide.md)를 참조하세요.
