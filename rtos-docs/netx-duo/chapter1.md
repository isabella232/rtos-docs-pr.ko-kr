---
title: 1장 - Azure RTOS NetX Duo 소개
description: 이 장에는 Azure RTOS NetX Duo에 대한 소개와 해당 애플리케이션 및 혜택에 대한 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c9b5e0ea82319bd369318cca753cf1db222ca29b0b4db3da150642ca007f1191
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789868"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo"></a>1장 - Azure RTOS NetX Duo 소개

Azure RTOS NetX Duo는 포함된 Azure RTOS ThreadX 기반 애플리케이션 전용으로 설계된 TCP/IP 표준의 고성능 실시간 구현입니다. 이 장에는 NetX Duo에 대한 소개와 해당 애플리케이션 및 혜택에 대한 설명이 포함되어 있습니다. 

## <a name="netx-duo-unique-features"></a>NetX Duo 고유 기능

다른 TCP/IP 구현과 달리 NetX Duo는 다용도로 설계되어 소규모 마이크로 컨트롤러 기반 애플리케이션에서 강력한 RISC와 DSP 프로세서를 사용하는 애플리케이션으로 쉽게 스케일링할 수 있습니다. 이는 원래 워크스테이션 환경에 맞춰 고안된 후 포함된 설계에 갇혀 버린 퍼블릭 도메인 또는 기타 상용 구현과는 확실히 대비됩니다.

### <a name="piconettrade-architecture"></a>Piconet&trade; 아키텍처

NetX Duo의 뛰어난 스케일링과 성능의 기반에는 포함된 시스템용으로 특별히 설계된 소프트웨어인 <em>Piconet</em>이 있습니다. Piconet 아키텍처는 NetX Duo 서비스를 C 라이브러리로 구현하여 스케일링을 극대화합니다. 이러한 방식으로 애플리케이션에서 사용하는 서비스만 최종 런타임 이미지로 가져옵니다. 따라서 NetX Duo의 실제 크기는 애플리케이션에 의해 결정됩니다. 대부분의 애플리케이션의 경우 NetX Duo의 명령 이미지 요구 사항은 5KB~30KB 사이로 크기입니다. IPv6 주소 구성 및 네트워크 환경 검색 프로토콜에 대해 IPv6 및 ICMPv6를 사용하도록 설정한 경우 NetX Duo 크기 범위는 30KB~45KB 사이입니다.

NetX Duo는 필요한 경우에만 내부 구성 요소 함수 호출을 계층화하여 뛰어난 네트워크 성능을 얻습니다. 또한 대부분의 NetX Duo 처리는 온라인으로 직접 수행되므로 과거에 임베디드 디자인에서 사용되던 워크스테이션 네트워크 소프트웨어보다 더 나은 성능상의 이점이 있습니다.

### <a name="zero-copy-implementation"></a>복사 없는 구현

NetX Duo는 TCP/IP의 패킷 기반의 복사 없는 구현을 제공합니다. 복사 없는 구현은 애플리케이션의 패킷 버퍼에 있는 데이터가 NetX Duo 내에 절대 복사되지 않는다는 것을 의미합니다. 이렇게 하면 성능이 크게 향상되고 포함된 애플리케이션에 매우 가치 있는 프로세서 주기가 확보됩니다.

### <a name="udp-fast-pathtrade-technology"></a>UDP Fast Path&trade; Technology

<em>UDP Fast Path Technology</em>을 사용하여 NetX Duo는 가능한 가장 빠른 UDP 처리를 제공합니다. 송신 측에서는 선택적 UDP 체크섬을 비롯한 UDP 처리가 <em>**nx_udp_socket_send**</em> 서비스에 포함되어 있습니다. 내부 NetX Duo IP 전송 루틴을 통해 패킷을 전송할 준비가 될 때까지 추가 함수 호출이 수행되지 않습니다. 이 루틴은 또한 플랫이므로(즉, 함수 호출 중첩이 최소임) 패킷이 애플리케이션의 네트워크 드라이버로 신속하게 디스패치됩니다. UDP 패킷이 수신되면 NetX Duo 패킷 수신 처리는 해당 UDP 소켓의 수신 큐에 직접 패킷을 배치하거나 일시 중단되어 UDP 소켓의 수신 큐에서 수신 패킷을 대기하는 첫 번째 스레드에 제공합니다. 추가 ThreadX 컨텍스트 전환은 필요하지 않습니다.

### <a name="ansi-c-source-cod"></a>ANSI C 소스 코드

NetX Duo는 완전히 ANSI C로 작성되었으며 ANSI C 컴파일러와 ThreadX를 지원하는 모든 프로세서 아키텍처에 실제로 즉시 이식할 수 있습니다. 

### <a name="not-a-black-box"></a>블랙 박스가 아님

대부분의 NetX Duo 배포판에는 전체 C 소스 코드가 포함됩니다. 따라서 많은 상용 네트워크 스택에서 발생하는 “블랙 박스” 문제를 없앨 수 있습니다. 애플리케이션 개발자는 NetX Duo를 사용하여 네트워크 스택이 수행하는 작업을 정확하게 파악할 수 있기 때문에 모든 것이 명확합니다!

소스 코드가 있기 때문에 애플리케이션 관련 수정이 가능합니다. 권장되지는 않지만 필요한 경우 네트워크 스택을 수정하는 기능을 제공한 것은 유용합니다.

해당 특징은 사내 또는 퍼블릭 도메인 네트워크 스택으로 작업하는 데 익숙한 개발자에게 특히 유용합니다. 이들에게는 소스 코드와 소스 코드를 수정할 수 있는 기능이 필요합니다. NetX Duo는 이러한 개발자를 위한 최종 네트워크 소프트웨어입니다.

### <a name="bsd-compatible-socket-api"></a>BSD 호환 소켓 API

레거시 애플리케이션의 경우 NetX Duo는 아래의 고성능 NetX Duo API를 호출하는 BSD 호환 소켓 인터페이스를 제공합니다. 이를 통해 기존 네트워크 애플리케이션 코드를 NetX Duo로 마이그레이션하는 데 도움이 됩니다.

## <a name="rfcs-supported-by-netx-duo"></a>NetX Duo에서 지원되는 RFC

기본 네트워크 프로토콜을 설명하는 RFC의 NetX Duo 지원에는 다음 네트워크 프로토콜이 포함되지만 이에 국한되지 않습니다. NetX Duo는 작은 메모리 사용 공간과 효율적인 실행으로 실시간 운영 체제의 제약 조건 내에서 모든 일반 권장 사항 및 기본 요구 사항을 따릅니다.

| **RFC**  | **설명**                                        |
| -------- | ------------------------------------------------------ |
|RFC 1112 | IGMPv1(IP 멀티캐스팅을 위한 호스트 확장)           |
|RFC 1122 | 인터넷 호스트에 대한 요구 사항 - 통신 계층 |
|RFC 2236 | Internet Group Management Protocol, 버전 2          |
|RFC 768  | UDP(User Datagram Protocol)                           |
|RFC 791  | IP(인터넷 프로토콜)                                 |
|RFC 792  | ICMP(Internet Control Message Protocol)               |
|RFC 793  | TCP(Transmission Control Protocol)                    |
|RFC 826  | 이더넷 ARP(주소 확인 프로토콜) |
|RFC 903  | RARP(역주소 확인 프로토콜) |
|RFC 5681 | TCP 정체 제어                     |

다음은 NetX Duo에서 지원하는 IPv6 관련 RFC입니다.

|**RFC** |**설명**|
-------- | ------------------------------------------ |
|RFC 1981 |IPv6(인터넷 프로토콜 v6)의 경로 MTU 검색|
|RFC 2460 | IPv6(인터넷 프로토콜 v6) 사양|
|RFC 2464 |이더넷 네트워크를 통한 IPv6 패킷 전송|
|RFC 4291 |IPv6(인터넷 프로토콜 v6) 주소 지정 아키텍처|
|RFC 4443 |IPv6(인터넷 프로토콜 v6) 사양에 대한 ICMPv6(internet Control Message Protocol)|
|RFC 4861 |IPv6의 네트워크 환경 검색|
|RFC 4862 |IPv6 상태 비저장 주소 자동 구성|

## <a name="embedded-network-applications"></a>포함된 네트워크 애플리케이션

포함된 네트워크 애플리케이션은 네트워크에 액세스해야 하며 휴대폰, 통신 장비, 자동차 엔진, 레이저 프린터, 의료 디바이스 등의 제품 내에서 숨겨진 마이크로프로세서에서 실행되는 애플리케이션입니다. 이와 같은 애플리케이션에는 거의 항상 몇 가지 메모리와 성능 제약 조건이 있습니다. 포함된 네트워크 애플리케이션의 또 다른 차이점은 소프트웨어와 하드웨어에 전용 용도가 있다는 점입니다.

정확한 시간 내에 처리를 수행해야 하는 네트워크 소프트웨어를 ‘실시간’ ‘네트워크’ 소프트웨어라고 하며, 시간 제약 조건이 네트워크 애플리케이션에 적용되는 경우에는 실시간 애플리케이션으로 분류됩니다. 포함된 네트워크 애플리케이션은 본질적으로 외부와 상호 작용하기 때문에 거의 항상 실시간입니다.

## <a name="netx-duo-benefits"></a>NetX Duo의 이점

포함된 애플리케이션에 NetX Duo를 사용할 경우의 주요 이점은 고속 인터넷 연결 및 작은 메모리 요구 사항입니다. NetX Duo는 고성능, 멀티태스킹 ThreadX 실시간 운영 체제와도 통합됩니다.

### <a name="improved-responsiveness"></a>향상된 응답성

고성능 NetX Duo 프로토콜 스택을 사용하면 포함된 네트워크 애플리케이션이 이전보다 더 빠르게 응답할 수 있습니다. 이러한 특성은 단일 패킷에 상당한 양의 네트워크 트래픽이나 엄격한 처리 요구 사항을 발생하는 포함된 애플리케이션에 특히 중요합니다.

### <a name="software-maintenance"></a>소프트웨어 유지 관리

NetX Duo를 사용하면 개발자는 포함된 애플리케이션의 네트워크 측면을 쉽게 분할할 수 있습니다. 분할을 통해 전체 개발 프로세스를 쉽게 진행하고 향후 소프트웨어 유지 관리를 크게 개선할 수 있습니다.

### <a name="increased-throughput"></a>향상된 처리량.

NetX Duo는 사용 가능한 최고 성능 네트워킹을 제공하며, 이러한 이점은 최소 패킷 처리 오버헤드를 통해 구현됩니다. 이를 통해 처리량을 높일 수도 있습니다.

### <a name="processor-isolation"></a>프로세서 격리

NetX Duo는 애플리케이션, 기본 프로세서, 네트워크 하드웨어 간에 프로세서와 관련이 없는 강력한 인터페이스를 제공합니다. 이를 통해 개발자는 네트워킹에 직접적으로 영향을 주는 하드웨어 문제를 처리하는 데 불필요한 시간을 낭비하지 않고, 애플리케이션의 네트워크 측면에 집중할 수 있습니다.

### <a name="ease-of-use"></a>사용 편의성

NetX Duo는 애플리케이션 개발자를 고려해서 설계되었습니다. NetX Duo 아키텍처와 서비스 호출 인터페이스는 이해하기 쉽습니다. 결과적으로 NetX Duo 개발자는 고급 기능을 신속하게 사용할 수 있습니다.

### <a name="improve-time-to-market"></a>출시 시간 개선

NetX Duo의 강력한 특징이 소프트웨어 개발 프로세스를 가속화합니다. NetX Duo는 대부분의 프로세서 및 네트워크 하드웨어 문제를 추상화하여 대부분의 애플리케이션 네트워크 관련 영역에서 이러한 문제를 방지합니다. 사용 편의성과 뛰어난 기능 집합과 함께 이 특징은 시장 출시 시간을 단축해 줍니다!

### <a name="protecting-the-software-investment"></a>소프트웨어 투자 보호

NetX Duo는 ANSI C로만 작성되며 ThreadX 실시간 운영 체제와 완전히 통합됩니다. 즉, NetX Duo 애플리케이션은 모든 ThreadX 지원 프로세서에 즉시 이식할 수 있습니다. 더 놀라운 점은 ThreadX를 사용하면 불과 몇 주 만에 새로운 프로세서 아키텍처를 지원할 수 있다는 사실입니다. 따라서 NetX Duo를 사용하면 애플리케이션의 마이그레이션 경로를 보장하고 원래 개발 투자를 보호할 수 있습니다.

## <a name="ipv6-ready-logo-certification"></a>IPv6 준비 로고 인증

NetX Duo "IPv6 준비 완료" 인증은 IPv6 준비 조직에서 사용할 수 있는 "IPv6 핵심 프로토콜(2단계) 자체 테스트" 패키지를 통해 획득되었습니다. 테스트 플랫폼과 테스트 사례에 대한 자세한 내용은 IPv6 준비 완료 프로젝트 웹 사이트 [ **https://www.ipv6ready.org/**](https://www.ipv6ready.org/)를 참조하세요.

2단계 IPv6 핵심 프로토콜 자체 테스트 도구 모음은 IPv6 스택이 광범위한 테스트를 통해 다음 RFC에 설정된 요구 사항을 준수하는지 확인합니다.  
섹션 1: RFC 2460  
섹션 2: RFC 4861  
섹션 3: RFC 4862  
섹션 4: RFC 1981  
섹션 5: RFC 4443  

## <a name="ixanvl-test"></a>IxANVL 테스트

NetX Duo는 IXIA의 IxANVL를 사용하여 테스트되었습니다. IxANVL은 자동화된 네트워크 및 프로토콜 유효성 검사를 위한 업계 표준입니다. IxANVL에 대한 자세한 내용은 [ **https://www.ixiacom.com/products/ixanvl**](https://www.ipv6ready.org/)서 확인할 수 있습니다.

특히 다음 NetX Duo 모듈은 IxANVL을 사용하여 테스트됩니다.

|**모듈** | **표준** |
| --------- | ------------ |
|IP | RFC791 </br> RFC1122 </br> RFC894|
|ICMP | RFC792 </br> RFC1122 </br> RFC1812|
|UDP | RFC768 </br> RFC1122|
|TCP-Core| RFC793 </br> RFC1122 </br> RFC2460|
|TCP-Advanced| RFC1981</br>RFC2001</br>RFC2385</br>RFC2463</br>RFC813</br>RFC896|
|TCP-Performance| RFC793</br>RFC1323</br>RFC2018|

## <a name="safety-certifications"></a>안전 인증

### <a name="tv-certification"></a>TÜV 인증  

NetX Duo는 IEC61508 및 IEC-62304에 따라 안전이 중요한 시스템에서 사용하도록 SG-TÜV Saar에서 인증되었습니다. 이 인증은 "전기, 전자 및 프로그램 가능한 전자 안전 관련 시스템의 기능적 안전"에 대한 최고 수준의 IEC(International Electrotechnical Commission) 61508 및 IEC 62304의 안전 무결성 등급에 따라, NetX Duo를 보안 관련 소프트웨어의 개발에 사용할 수 있음을 확인합니다. 독일 SGSGroup 및 TÜV Saarland의 공동 벤처인 SGS-TÜV Saar는 세계적으로 안전 관련 시스템용 포함 소프트웨어를 테스트, 감사, 확인 및 검증하는 최고 권위의 독립 기업으로 자리했습니다. 산업 보안 표준 IEC 61508과, 거기에서 파생된 모든 표준(IEC 62304 포함)은 전기, 전자 및 프로그래밍 가능한 전자 안전 관련 의료 장비, 공정 제어 시스템, 산업용 기계, 철도 제어 시스템의 기능 안전을 보장하는 데 사용됩니다. 

SGS-TÜV Saar는 ISO 26262 표준에 따라 안전이 중요한 자동차 시스템에서 NetX Duo를 사용할 수 있도록 인증했습니다. 또한 NetX Duo는 최고 수준의 ISO 26262 인증을 나타내는 ASIL(자동차 안전 무결성 수준) D로 인증되었습니다. 

그리고 SGS-TÜV Saar는 안전이 중요한 철도 응용 분야에서 NetX Duo를 사용할 수 있도록 인증했으며 SW-SIL 4까지 EN 50128 표준을 충족하는 것으로 확인했습니다.

![SG-TÜV Saar 인증 로고의 다이어그램입니다.](./media/user-guide/sgs-tuv-saar-logo.png)

최대 SIL 4의 IEC 61508  
IEC 62304 최대 SW 안전 클래스 C ISO 26262 ASIL D EN 50128 SW-SIL 4

> [!IMPORTANT]
> TÜV에서 인증한 NetX Duo 버전 또는 테스트 보고서, 인증서 및 관련 설명서의 가용성에 대한 자세한 내용은 Microsoft에 문의하세요.

### <a name="ul-certification"></a>UL 인증

UL은 NetX Duo가 프로그래밍 가능한 구성 요소에서의 소프트웨어에 대한 UL 60730-1 부칙 H, CSA E60730-1 부칙 H, IEC 60730-1 부칙 H, UL 60335-1 부칙 R, IEC 60335-1 부칙 R 및 UL 1998 안전 표준의 규정을 준수한다고 인증했습니다. IEC 60335-1 표준에서는 해당 부록 H에 포함된 "소프트웨어를 사용하여 제어"에 대한 요구 사항이 있는 IEC/UL 60730-1과 함께, 부록 R의 "프로그래밍 가능 전자 회로"에 대한 요구 사항을 설명합니다. IEC 60730 부록 H 및 IEC 60335-1 부록 R은 세탁기, 식기세척기, 건조기, 냉장고, 냉동고 및 오븐과 같은 어플라이언스에서 사용되는 MCU 하드웨어 및 소프트웨어의 안전을 다룹니다.

![UL 인증 로고의 다이어그램입니다.](./media/user-guide/c-ru-us-logo.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]  
> *UL에서 인증한 NetX Duo 버전 또는 테스트 보고서, 인증서 및 관련 설명서의 가용성에 대한 자세한 내용은 Microsoft에 문의하세요.*