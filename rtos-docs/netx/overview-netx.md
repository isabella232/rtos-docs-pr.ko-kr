---
title: Azure RTOS NetX 이해
description: Azure RTOS NetX는 고성능으로 구현된 TCP/IP 프로토콜 표준으로, Azure RTOS ThreadX와 완전히 통합되며 지원되는 모든 프로세서에 사용할 수 있습니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 63fd212249da6154926684f9bc844d2c2a78e84e
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754848"
---
# <a name="overview-of-azure-rtos-netx"></a>Azure RTOS NetX 개요

Azure RTOS NetX는 특별히 긴밀하게 포함된 실시간 및 IoT 애플리케이션용으로 설계된 산업용 TCP/IP IPv4 포함 네트워크 스택입니다. Azure RTOS NetX는 Microsoft의 원래 IPv4 네트워크 스택으로, 기본적으로 Azure RTOS의 하위 집합입니다. NetX는 IPv4, TCP, UDP 등의 핵심 네트워크 프로토콜과 함께 포함된 애플리케이션을 제공하고 더 높은 수준의 추가 기능 프로토콜을 완벽하게 제공합니다. Azure RTOS NetX는 적은 공간, 빠른 실행 및 뛰어난 사용 편의성을 제공하므로 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.

## <a name="api-protocols"></a>API 프로토콜
Azure RTOS NetX는 다음을 지원합니다.

### <a name="telnet"></a>TELNET

* 최소 0.5KB 및 0.3KB의 RAM 공간.
* 클라이언트 및 서버 지원.

### <a name="auto-ip"></a>자동 IP

* 자동 IPv4 주소 할당.
* 최소 1.2KB, 300바이트의 RAM.

### <a name="http---hypertext-transfer-protocolhttp"></a>HTTP - HTTP(Hypertext Transfer Protocol)

* 최소 2.8KB~4.8KB FLASH, 0.4KB~1.0KB RAM 공간.
* 클라이언트 및 서버 지원.

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a>SMTP - SMTP(Simple Mail Transfer Protocol)

* 최소 4.1KB 및 0.6KB의 RAM 공간
* 클라이언트 지원

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a>DHCP - DHCP(Dynamic Host Configuration Protocol)

* 최소 3.6KB ~ 4.6KB FLASH, 2.7KB RAM 공간
* 클라이언트 및 서버 지원
* IPv4 지원

### <a name="p0p3---post-office-protocol-version-3-pop3"></a>P0P3 - POP3(Post Office Protocol Version 3)

* 최소 8.1KB 및 1.4KB의 RAM 공간
* 클라이언트 지원

### <a name="snmp---simple-network-management-protocol-snmp"></a>SNMP - SNMP(Simple Network Management Protocol)

* 최소 10.9KB 및 2.6KB의 RAM 공간
* VI, V2 및 V3에 대한 에이전트 지원

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a>FTP, TFTP - FTP(파일 전송 프로토콜), TFTP(Trivial File Transfer Protocol)

* FTP 최소 1.8KB ~ 7.2KB FLASH, 0.6KB ~ 2.1KB RAM 공간
* TFTP 최소 1.7KB ~ 2.4KB FLASH, 0.3KB ~ 1.8KB RAM 공간
* 클라이언트 및 서버 지원

### <a name="ppp---polnt-to-point-protocol-ppp"></a>PPP - PPP(지점 간 프로토콜)

* 최소 7.1KB 및 3.8KB의 RAM 공간
* 안정적이고 신뢰할 수 있습니다.

### <a name="sntp---simple-network-time-protocol-sntp"></a>SNTP - SNTP(Simple Network Time Protocol)

* 최소 4KB 및 0.5KB RAM
* 클라이언트 지원

### <a name="azure-rtos-netx-api"></a>Azure RTOS NetX API

* 빠르고 복사 없는 API 구현
* 레거시 소켓 코드 포팅을 위한 선택적 BSD 계층

### <a name="igmp---internet-group-management-protocol-igmp"></a>IGMP - IGMP(Internet Group Management Protocol)

* 최소 2.5KB FLASH
* IPv4 멀티캐스트 그룹 지원
* IXIA IxANVL 유효성 검사 완료
* 선택적 IGMP 통계
* Azure RTOS TraceX를 통한 시스템 수준 추적

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

### <a name="icmp---internet-control-message-protocol-icmp"></a>ICMP - ICMP(Internet Control Message Protocol)

* 최소 2.5KB FLASH
* IPv4 지원
* IXIA IxANVL 유효성 검사 완료
* Ping 요청 및 Ping 응답
* Ping 요청 시 선택적 스레드 일시 중단
* 모든 일시 중단 시 선택적 시간 제한
* 선택적 ICMP 통계
* Azure RTOS TraceX를 통한 시스템 수준 추적

### <a name="ipv4---internet-protocol-ip"></a>IPv4 - IP(인터넷 프로토콜)

* 최소 3.5KB~8.5KB FLASH, 2KB~3KB의 RAM 공간.
* Piconet™ 아키텍처.
* 빠른 근거리 통신 속도 성능.
* 여러 인터페이스 지원.
* 다중 홈 지원.
* 정적 라우팅 지원.
* IP 조각화/리어셈블리 지원.
* IPv4 지원.
* IXIA IxANVL 유효성 검사 완료.
* 단계 II 준비 로고 인증.
* 선택적 IP 통계.
* 잘 정의된 직관적인 물리적 계층 드라이버 인터페이스.
* Azure RTOS TraceX를 통한 시스템 수준 추적.

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a>ARP/RARP - ARP(주소 확인 프로토콜), RARP(역주소 확인 프로토콜)

* 최소 1.7KB FLASH, RAM 크기.
* 32비트의 동적 확인 IPv4 및 48비트 MAC 주소.
* IXIA IxANVL 유효성 검사 완료.
* 유연한 사용자 정의 ARP 캐시.
* 무상 ARP 지원.
* 애플리케이션에 의해 결정되는 선택적 ARP/RARP 통계.
* Azure RTOS TraceX를 통한 시스템 수준 추적.

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a>이더넷, WiFi, Bluetooth LE, 15.4 등

## <a name="interoperability-verification"></a>상호 운용성 확인

Azure RTOS NetX는 RFC 표준을 준수하며 대부분의 공급 업체의 디바이스와 완벽한 상호 운용성을 제공합니다. 또한 Azure RTOS NetX는 Azure RTOS NetX 코어 TCP/IP 프로토콜 구현에 업계 표준 IxANVL(자동화된 네트워크 유효성 검사 라이브러리)을 활용합니다.

## <a name="advanced-technology"></a>고급 기술

Azure RTOS NetX는 다음을 포함하는 고급 기술입니다.
* Piconet™ 아키텍처.
* 자동 크기 조정
* UDP Fast-Path Technology™.
* 유연한 패킷 관리.
* 복사 없는 API 및 구현.
* 다중 홈 지원.
* 모든 일시 중단 시 선택적 시간 제한.
* 정적 라우팅 지원.
* Azure RTOS TraceX 시스템 분석 지원.
