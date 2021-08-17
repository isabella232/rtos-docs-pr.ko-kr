---
title: 2장 - Azure RTOS NetX 설치 및 사용
description: 이 장에서는 고성능 네트워크 스택인 Azure RTOS NetX의 설치, 설정, 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 942250cf864fca3c35b97ae731549c070ac2f2f2ef3ef8897e5cbf1e705e7c6a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801806"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx"></a>2장 - Azure RTOS NetX 설치 및 사용

이 장에서는 고성능 네트워크 스택인 Azure RTOS NetX의 설치, 설정, 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="host-considerations"></a>호스트 고려 사항

임베디드 개발은 일반적으로 Windows 또는 Linux(Unix) 호스트 컴퓨터에서 수행됩니다. 애플리케이션이 컴파일되고 연결된 후 호스트에서 실행 파일이 생성되면 실행을 위해 대상 하드웨어로 다운로드됩니다.

일반적으로 대상 다운로드는 개발 도구의 디버거 내에서 수행됩니다. 다운로드 후 디버거는 대상 실행 제어(이동, 중지, 중단점 등) 뿐만 아니라 메모리 및 프로세서 레지스터에 대한 액세스를 제공합니다.

대부분의 개발 도구 디버거는 JTAG(IEEE 1149.1) 및 BDM(백그라운드 디버그 모드)과 같은 OCD(온-칩 디버그) 연결을 통해 대상 하드웨어와 통신합니다. 또한 디버거는 ICE(회로 내 에뮬레이션) 연결을 통해 대상 하드웨어와 통신합니다. OCD 및 ICE 연결 둘 다 대상 상주 소프트웨어에 대한 침입이 최소화된 강력한 솔루션을 제공합니다.

호스트에서 사용되는 리소스의 경우 NetX 소스 코드는 ASCII 형식으로 전달되며 호스트 컴퓨터 하드 디스크에 약 1MB의 공간이 있어야 합니다.

## <a name="target-considerations"></a>대상 고려 사항

NetX를 사용하려면 대상에 5~45KB의 ROM(읽기 전용 메모리)이 있어야 합니다. NetX 스레드 스택 및 기타 글로벌 데이터 구조에 사용할 1~5KB의 RAM(Random Access Memory)도 대상에 있어야 합니다.

NetX는 두 개의 ThreadX 타이머 개체와 하나의 ThreadX 뮤텍스 개체도 사용해야 합니다. 이러한 기능은 NetX 프로토콜 스택 내의 정기적인 처리 요구 사항 및 스레드 보호에 사용됩니다.

## <a name="product-distribution"></a>제품 배포

Azure RTOS NetX는 <https://github.com/azure-rtos/netx/>에 있는 퍼블릭 소스 코드 리포지토리에서 가져올 수 있습니다.

다음은 리포지토리에 있는 몇 가지 중요한 파일 목록입니다.

- ***nx_api.h***: 모든 시스템 등식, 데이터 구조 및 서비스 프로토타입이 포함되어 있는 C 헤더 파일입니다.
- ***nx_port.h***: 모든 개발 도구와 대상별 데이터 정의 및 구조가 포함되어 있는 C 헤더 파일입니다.  
- ***demo_netx.c***: 소규모 데모 애플리케이션이 포함되어 있는 C 파일입니다.
- ***nx.a(또는 nx.lib)** _: _standard* 패키지와 함께 배포되는 NetX C 라이브러리의 이진 버전입니다.             |

## <a name="netx-installation"></a>NetX 설치

GitHub 리포지토리를 로컬 머신에 복제하여 NetX를 설치할 수 있습니다. 다음은 PC에서 NetX 리포지토리의 복제본을 만들기 위한 일반적인 구문입니다.

```c
    git clone https://github.com/azure-rtos/netx
```

또는 GitHub 기본 페이지의 **다운로드** 단추를 사용하여 리포지토리의 복사본을 다운로드할 수 있습니다.

또한 온라인 리포지토리의 프런트 페이지에서 NetX 라이브러리를 빌드하기 위한 지침을 찾을 수 있습니다.

> [!IMPORTANT]
> 애플리케이션 소프트웨어는 NetX 라이브러리 파일(일반적으로 ***nx.a** _ 또는 _*_nx.lib_*_)과 C 포함 파일 _*_nx_api.h 및 nx_port.h_**에 액세스할 수 있어야 합니다. 이렇게 하려면 개발 도구에 대한 적절한 경로를 설정하거나 해당 파일을 애플리케이션 개발 영역으로 복사합니다.

## <a name="using-netx"></a>NetX 사용

NetX를 사용하려면 컴파일하는 동안 및 NetX 라이브러리 _*_nx.a_*_(또는 _ *_nx.lib_*)*와 연결하는 동안 ***nx_api.h** _가 애플리케이션 코드에 포함되어 있어야 합니다.

NetX 애플리케이션을 빌드하는 데 필요한 네 가지 단계는 다음과 같습니다.

1. NetX 서비스 또는 데이터 구조를 사용하는 모든 애플리케이션 파일에 ***nx_api.h*** 파일을 포함합니다.
1. _ *_tx_application_define_** 함수 또는 애플리케이션 스레드에서 ***nx_system_initialize** _를 호출하여 NetX 시스템을 초기화합니다.  
1. ***nx_system_initialize*** 를 호출한 후 IP 인스턴스를 만들고 ARP(주소 확인 프로토콜) 및 소켓(필요한 경우)을 사용하도록 설정합니다.  
1. 애플리케이션 원본을 컴파일하고 NetX 런타임 라이브러리 ***nx.a** _(또는 _*_nx.lib_**)와 연결합니다. 결과 이미지를 대상으로 다운로드하여 실행할 수 있습니다.

## <a name="troubleshooting"></a>문제 해결

각 NetX 포트는 실제 네트워크에서 또는 시뮬레이션된 네트워크 드라이버를 통해 실행되는 하나 이상의 샘플과 함께 제공됩니다. 항상 샘플 시스템을 먼저 실행하는 것이 좋습니다.

샘플 시스템이 제대로 실행되지 않으면 다음 작업을 수행하여 문제의 범위를 좁힙니다.

1. 샘플이 어느 정도 실행되고 있는지 확인합니다.
2. 모든 새 애플리케이션 스레드의 스택 크기를 늘립니다.
3. 구성 옵션 섹션에 나열된 적절한 디버그 옵션을 사용하여 NetX 라이브러리를 다시 컴파일합니다.
4. **NX_IP** 구조를 검사하여 패킷이 송신 또는 수신되고 있는지 확인합니다.
5. 기본 패킷 풀을 검사하여 사용할 수 있는 패킷이 있는지 확인합니다.
6. 네트워크 드라이버가 IP 연결이 필요한 애플리케이션의 4바이트 경계에 ARP 및 IP 패킷을 해당 헤더와 함께 제공하는지 확인합니다.
7. 최근 변경 내용을 일시적으로 무시하여 문제가 사라지거나 달라지는지 확인합니다. 이러한 정보는 지원 엔지니어에게 유용합니다.

[고객 지원 센터](about-this-guide.md) 항목에 설명된 절차에 따라 문제 해결 단계에서 수집한 정보를 보냅니다.

## <a name="configuration-options"></a>구성 옵션

NetX를 사용하여 NetX 라이브러리 및 애플리케이션을 빌드할 때 몇 가지 구성 옵션이 있습니다. 구성 옵션은 달리 지정되지 않은 경우 애플리케이션 원본, 명령줄 또는 ***nx_user.h*** 포함 파일 내에 정의할 수 있습니다.

> [!IMPORTANT]
> _ *NX_INCLUDE_USER_DEFINE_FILE**이 정의된 애플리케이션 및 NetX 라이브러리가 빌드되어 있는 경우에만 ***nx_user.h** _에 정의된 옵션이 적용됩니다.

다음 섹션에는 NetX에서 사용할 수 있는 구성 옵션이 나열되어 있습니다.

### <a name="system-configuration-options"></a>시스템 구성 옵션  

| 옵션  | Description  |
|---|---|
| X_DEBUG | 정의된 경우 RAM 이더넷 네트워크 드라이버에서 제공되는 선택적 출력 디버그 정보를 사용하도록 설정합니다. |
| NX_DISABLE_ERROR_CHECKING | 정의된 경우 기본 NetX 오류 검사 API를 제거하여 성능을 개선합니다. 오류 검사를 사용하지 않도록 설정해도 영향을 받지 않는 API 반환 코드는 API 정의에 굵은 서체로 나열됩니다. 이 정의는 일반적으로 애플리케이션을 디버그한 후 사용되거나 정의를 사용하면 성능은 개선되고 코드 크기는 감소하는 경우 사용됩니다. |
| NX_DRIVER_DEFERRED_PROCESSING | 정의된 경우 지연된 네트워크 드라이버 패킷 처리를 사용하도록 설정합니다. 이렇게 하면 네트워크 드라이버에서 IP 인스턴스에 패킷을 배치하고 NetX 내부 IP 도우미 스레드에서 실제 처리 루틴이 호출되도록 할 수 있습니다. |
| NX_ENABLE_EXTENDED_NOTIFY_SUPPORT | 스택에서 더 많은 콜백 후크를 사용하도록 설정합니다. 이러한 콜백 함수는 BSD 래퍼 계층에서 사용됩니다. 기본적으로 이 옵션은 정의되어 있지 않습니다. |
| NX_ENABLE_SOURCE_ADDRESS_CHECK | 정의된 경우 수신 패킷의 원본 주소를 확인할 수 있도록 합니다. 이 옵션은 기본적으로 사용하지 않도록 설정됩니다. |
| NX_LITTLE_ENDIAN | 정의된 경우 little endian 환경에서 필요한 바이트 스와핑을 수행하여 프로토콜 헤더가 적절한 big endian 형식인지 확인합니다. 기본값은 일반적으로 ***nx_port.h*** 에 설정됩니다. |
| NX_MAX_PHYSICAL_INTERFACES | 디바이스의 총 실제 네트워크 인터페이스 수를 지정합니다. 기본값은 1이고 ***nx_api.h*** 에 정의됩니다. 디바이스에는 하나 이상의 실제 인터페이스가 있어야 합니다. 루프백 인터페이스는 포함되지 않습니다. |
| NX_PHYSICAL_HEADER | 프레임의 실제 헤더 크기(바이트)를 지정합니다. 기본값은 16이며(32비트 경계에 맞춘 일반적인 14바이트 이더넷 프레임 기준) ***nx_api.h** _에 정의됩니다. 애플리케이션은 _ *_nx_user.h_**에서와 같이 _*_nx_api.h_*_ 가 포함되기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |

### <a name="arp-configuration-options"></a>ARP 구성 옵션  

| 옵션  | Description  |
|---|---|
| NX_ARP_DEFEND_BY_REPLY | 정의된 경우 NetX에서 ARP 응답을 송신하여 해당 IP 주소를 방어할 수 있습니다. |
| NX_ARP_DEFEND_INTERVAL | 충돌하는 주소가 표시된 수신 ARP 메시지에 응답하여 ARP 모듈이 다음 방어 패킷을 송신하는 간격(초)을 정의합니다. |
| NX_ARP_DISABLE_AUTO_ARP_ENTRY | **NX_DISABLE_ARP_AUTO_ENTRY** 로 이름이 바뀌었습니다. 아직 지원되는 옵션이지만 새 디자인에서는 **NX_DISABLE_ARP_AUTO_ENTRY** 를 사용하는 것이 좋습니다.
| NX_ARP_EXPIRATION_RATE | ARP 항목이 유효한 상태로 유지되는 시간(초)을 지정합니다. 기본값인 0을 사용하면 ARP 항목 만료 또는 에이징을 사용하지 않도록 설정하며 기본값은 ***nx_api.h** _에 정의됩니다. 애플리케이션은 _ _nx_api.h_*가 포함되기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다.
| NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION** 으로 이름이 바뀌었습니다. 아직 지원되는 옵션이지만 새 디자인에서는 **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION** 을 사용하는 것이 좋습니다. |
| NX_ARP_MAX_QUEUE_DEPTH | ARP 응답을 기다리는 동안 큐에 대기될 수 있는 최대 패킷 수를 지정합니다. 기본값은 4이고 ***nx_api.h*** 에 정의됩니다. |
| NX_ARP_MAXIMUM_RETRIES | ARP 응답 없이 수행되는 최대 ARP 재시도 수를 지정합니다. 기본값은 18이고 ***nx_api.h** _에 정의됩니다. 애플리케이션은 _*_nx_api.h_**를 포함하기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |
| NX_ARP_UPDATE_RATE | ARP 재시도 간 시간(초)을 지정합니다. 기본값은 10으로, 10초를 나타내며 ***nx_api.h** _에 정의됩니다. 애플리케이션은 _*_nx_api.h_**를 포함하기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |
| NX_DISABLE_ARP_AUTO_ENTRY | 정의된 경우 ARP 캐시에 ARP 요청 정보를 입력할 수 없습니다. |
| NX_DISABLE_ARP_INFO | 정의된 경우 ARP 정보를 수집할 수 없습니다. |
| NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION | 정의된 경우 MAC 주소가 업데이트된 것이 검색되면 ARP에서 콜백 알림 함수를 호출하도록 허용합니다. |

### <a name="icmp-configuration-options"></a>ICMP 구성 옵션  

| 옵션  | Description  |
|---|---|
| NX_DISABLE_ICMP_INFO | 정의된 경우 ICMP 정보를 수집할 수 없습니다. |
| NX_DISABLE_ICMP_RX_CHECKSUM | 수신된 ICMP 패킷에 대한 ICMP 체크섬 계산을 사용하지 않도록 설정합니다. 이 옵션은 네트워크 인터페이스 드라이버가 ICMP 체크섬을 확인할 수 있고 애플리케이션에서 IP 조각화 기능을 사용하지 않는 경우에 유용합니다. 이 옵션은 기본적으로 정의되지 않습니다. |
| NX_DISABLE_ICMP_TX_CHECKSUM | 전송된 ICMP 패킷에 대한 ICMP 체크섬 계산을 사용하지 않도록 설정합니다. 이 옵션은 네트워크 인터페이스 드라이버가 ICMP 체크섬을 계산할 수 있으나 애플리케이션이 IP 조각화 기능을 사용하지 않는 경우에 유용합니다. 이 옵션은 기본적으로 정의되지 않습니다. |

### <a name="igmp-configuration-options"></a>IGMP 구성 옵션  

| 옵션  | Description  |
|---|---| 
| NX_DISABLE_IGMP_INFO | 정의된 경우 IGMP 정보를 수집할 수 없습니다. |
| NX_DISABLE_IGMPV2 | 정의된 경우 IGMPv2 지원을 사용하지 않도록 설정하므로 NetX에서 IGMPv1만 지원합니다. 기본적으로 이 옵션은 설정되어 있지 않으며 ***nx_api.h*** 에 정의됩니다. |
| NX_MAX_MULTICAST_GROUPS | 가입할 수 있는 최대 멀티캐스트 그룹 수를 지정합니다. 기본값은 7이며 ***nx_api.h** _에 정의됩니다. 애플리케이션은 _ _nx_api.h_*가 포함되기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |

### <a name="ip-configuration-options"></a>IP 구성 옵션

| 옵션  | Description  |
|---|---|
| NX_DISABLE_FRAGMENTATION | 정의된 경우 IP 조각화 및 리어셈블리 논리를 사용하지 않도록 설정합니다. |
| NX_DISABLE_IP_INFO | 정의된 경우 IP 정보를 수집할 수 없습니다. |
| NX_DISABLE_IP_RX_CHECKSUM | 정의된 경우 수신된 IP 패킷의 체크섬 논리를 사용하지 않도록 설정합니다. 네트워크 디바이스에서 IP 헤더 체크섬을 확인할 수 있고 애플리케이션에서 IP 조각화를 사용하지 않는 경우에 유용합니다. |
| NX_DISABLE_IP_TX_CHECKSUM | 정의된 경우 송신된 IP 패킷의 체크섬 논리를 사용하지 않도록 설정합니다. 기본 네트워크 디바이스에서 IP 헤더 체크섬을 생성할 수 있고 애플리케이션에서 IP 조각화를 사용하지 않는 경우에 유용합니다. |
| NX_DISABLE_LOOPBACK_INTERFACE | 정의된 경우 루프백 인터페이스에 대해 NetX 지원을 사용하지 않도록 설정합니다. |
| NX_DISABLE_RX_SIZE_CHECKING | 정의된 경우 수신된 패킷에서 크기 검사를 사용하지 않도록 설정합니다. |
| NX_ENABLE_IP_STATIC_ROUTING | 정의된 경우 대상 주소에 특정한 다음 홉 주소를 할당할 수 있는 IP 고정 라우팅을 사용하도록 설정합니다. 기본적으로 IP 고정 라우팅은 사용하지 않도록 설정되어 있습니다. |
| NX_IP_PERIODIC_RATE | 정의된 경우 1초 동안의 ThreadX 타이머 틱 수를 지정합니다. 기본값은 ThreadX 기호 **TX_TIMER_TICKS_PER_SECOND** 에서 파생되며 기본적으로 100(10ms 타이머)으로 설정됩니다. NetX 모듈의 나머지 부분도 **NX_IP_PERIODIC_RATE*** 에서 타이밍 정보가 파생되므로 이 값을 수정하는 경우 애플리케이션에서 주의를 기울여야 합니다. |
| NX_IP_ROUTING_TABLE_SIZE | 정의된 경우 지정된 대상 주소의 발신 인터페이스 및 다음 홉 주소 목록에 해당하는 IP 고정 라우팅 테이블의
최대 항목 수를 설정합니다. 기본값은 8이며 ***nx_api.h** _에 정의됩니다. 이 기호는 _ *NX_ENABLE_IP_STATIC_ROUTING**이 정의된 경우에만 사용됩니다. |

### <a name="packet-configuration-options"></a>패킷 구성 옵션  

| 옵션  | Description  |
|---|---|
| NX_DISABLE_PACKET_INFO | 정의된 경우 패킷 풀 정보를 수집할 수 없습니다. | 
| NX_PACKET_HEADER_PAD | 정의된 경우 NX_PACKET 제어 블록의 끝에 패딩을 사용하도록 설정합니다. 패딩할 **ULONG** 워드 수는 **NX_PACKET_HEADER_PAD_SIZE** 로 정의됩니다. |
| NX_PACKET_HEADER_PAD_SIZE | NX_PACKET 구조에 패딩할 **ULONG** 단어 수를 설정하여 패킷 페이로드 영역을 원하는 맞춤에서 시작할 수 있도록
합니다. 이 기능은 수신 버퍼 설명자가 NX_PACKET 페이로드 영역을 직접 가리키며 네트워크 인터페이스 수신 논리 또는 캐시 작업 논리에서 특정 맞춤 요구 사항을 충족하는 버퍼 시작 주소가 필요한 경우에 유용합니다. 이 값은 **NX_PACKET_HEADER_PAD** 가 정의된 경우에만 유효합니다. |

### <a name="rarp-configuration-options"></a>RARP 구성 옵션  

| 옵션  | Description  |
|---|---|
| NX_DISABLE_RARP_INFO | 정의된 경우 RARP 정보를 수집할 수 없습니다. |

### <a name="tcp-configuration-options"></a>TCP 구성 옵션

| 옵션  | Description  |
|---|---|
| NX_DISABLE_RESET_DISCONNECT | 정의된 경우 제공되는 시간 제한 값이 **NX_NO_WAIT** 로 지정되면 연결 해제 중에 초기화 처리를 사용하지 않도록 설정합니다. |
| NX_DISABLE_TCP_INFO | 정의된 경우 TCP 정보를 수집할 수 없습니다. |
| NX_DISABLE_TCP_RX_CHECKSUM | 정의된 경우 수신된 TCP 패킷의 체크섬 논리를 사용하지 않도록 설정합니다. 이 기능은 링크 계층에 안정적인 체크섬 또는 CRC 처리가 있거나 인터페이스 드라이버가 하드웨어의 TCP 체크섬을 확인할 수 있는 경우에만 유용합니다. |
| NX_DISABLE_TCP_TX_CHECKSUM | 정의된 경우 TCP 패킷 송신에 체크섬 논리를 사용하지 않도록 설정합니다. 수신 네트워크 노드에 수신된 TCP 체크섬 논리가 사용하지 않도록 설정되어 있거나 기본 네트워크 드라이버가 TCP 체크섬을 생성할 수 있는 경우에만 유용합니다. |
| NX_ENABLE_TCP_KEEPALIVE | 정의된 경우 선택적 TCP 연결 유지 타이머를 사용하도록 설정합니다. 기본 설정은 사용하지 않도록 설정됩니다. |
| NX_ENABLE_TCP_MSS_CHECKING | 정의된 경우 TCP 연결을 수락하기 전에 최소 피어 MSS 확인을 사용하도록 설정합니다. 이 기능을 사용하려면 **NX_ENABLE_TCP_MSS_MINIMUM** 기호가 정의되어 있어야 합니다. 이 옵션은 기본적으로 사용하도록 설정되지 않습니다. |
NX_ENABLE_TCP_WINDOW_SCALING | TCP 애플리케이션의 창 크기 조정 옵션을 사용하도록 설정합니다. 정의된 경우 TCP 연결 단계에서 창 크기 조정 옵션을 협상하고 애플리케이션에서 64K보다 큰 창 크기를 지정할 수 있습니다. 기본 설정은 사용하지 않도록 설정됩니다(정의되지 않음). |
| NX_MAX_LISTEN_REQUESTS | 최대 서버 수신 대기 요청 수를 지정합니다. 기본값은 10이며 ***nx_api.h** _에 정의됩니다. 애플리케이션은 _ _nx_api.h_*가 포함되기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |
| NX_TCP_ACK_EVERY_N_PACKETS | ACK 송신 전 수신할 TCP 패킷 수를 지정합니다. **NX_TCP_IMMEDIATE_ACK** 는 사용하도록 설정되어 있지만 **NX_TCP_ACK_EVERY_N_PACKETS** 는 사용하도록 설정되어 있지 않은 경우 이전 버전과의 호환성을 위해 이 값이 자동으로 1로 설정됩니다. |
| NX_TCP_ACK_TIMER_RATE | TCP 지연 ACK 처리의 타이머 속도를 계산하기 위해 시스템 틱 수(NX_IP_PERIODIC_RATE)를 나누는 방법을 지정합니다. 기본값은 5로, 200ms를 나타내며 ***nx_tcp.h** _에 정의됩니다. 애플리케이션은 _*_nx_api.h_**를 포함하기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |
| NX_TCP_ENABLE_KEEPALIVE | **NX_ENABLE_TCP_KEEPALIVE** 로 이름이 변경되었습니다. 아직 지원되는 옵션이지만 새 디자인에서는 **NX_ENABLE_TCP_KEEPALIVE** 를 사용하는 것이 좋습니다. |
| NX_TCP_ENABLE_WINDOW_SCALING | **NX_ENABLE_TCP_WINDOW_SCALING** 으로 이름이 변경되었습니다. 아직 지원되는 옵션이지만 새 디자인에서는 **NX_ENABLE_TCP_WINDOW_SCALING** 을 사용하는 것이 좋습니다. |
| NX_TCP_FAST_TIMER_RATE | 빠른 TCP 타이머 속도를 계산하기 위해 NetX 내부 틱 수(NX_IP_PERIODIC_RATE)를 나누는 방법을 지정합니다. 빠른 TCP 타이머는 지연 ACK 타이머를 포함하여 다양한 TCP 타이머를 구동하는 데 사용됩니다. 기본값은 10으로, 100ms를 나타내며 ThreadX 타이머가 10ms로 실행되고 있다고 가정합니다. 이 값은 ***nx_tcp.h** _에 정의됩니다. 애플리케이션은 _*_nx_api.h_**를 포함하기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |
| NX_TCP_IMMEDIATE_ACK | 정의된 경우 선택적으로 TCP 즉시 ACK 응답 처리를 사용하도록 설정합니다. 이 기호를 정의하는 것은 **NX_TCP_ACK_EVERY_N_PACKETS** 를 1로 정의하는 것과 같습니다. |
| NX_TCP_KEEPALIVE_INITIAL | 연결 유지 타이머가 활성화되기 전의 비활성 시간(초)을 지정합니다. 기본값은 7200으로, 2시간을 나타내며 ***nx_tcp.h** _에 정의됩니다. 애플리케이션은 _*_nx_api.h_**를 포함하기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |
| NX_TCP_KEEPALIVE_RETRIES | 연결이 끊어진 것으로 간주하기 전 허용되는 연결 유지 재시도 수를 지정합니다. 기본값은 10으로, 10번의 재시도를 나타내며 ***nx_tcp.h** _에 정의됩니다. 애플리케이션은 _ _nx_api.h_*가 포함되기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |
| NX_TCP_KEEPALIVE_RETRY | 연결의 상대방이 응답하지 않는다고 가정하는 연결 유지 타이머의 재시도 간 간격(초)을 지정합니다. 기본값은 75로, 재시도 간 간격이 75초임을 나타내며 ***nx_tcp.h** _에 정의됩니다. 애플리케이션은 _ _nx_api.h_*가 포함되기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |
| NX_TCP_MAX_OUT_OF_ORDER_PACKETS | TCP 소켓 수신 큐에 보관할 수 있는 순서가 잘못된 TCP 패킷의 최대 수를 정의하는 기호입니다. 이 기호를 사용하면 TCP 수신 소켓에서 큐에 대기되는 패킷 수를 제한하여 패킷 풀이 부족해지는 것을 방지할 수 있습니다. 기본적으로 이 기호는 정의되지 않으므로 TCP 소켓에서 큐에 대기되는, 순서가 잘못된 패킷 수에는 제한이 없습니다. |
| NX_TCP_MAXIMUM_RETRIES | 연결이 끊어진 것으로 간주하기 전 허용되는 데이터 전송 재시도 수를 지정합니다. 기본값은 10으로, 10번의 재시도를 나타내며 ***nx_tcp.h** _에 정의됩니다. 애플리케이션은 _*_nx_api.h_**를 포함하기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |
| NX_TCP_MAXIMUM_TX_QUEUE | TCP 송신 요청을 일시 중단하거나 거부하기 전 TCP 전송 큐의 최대 크기를 지정합니다. 기본값은 20으로, 언제든지 최대 20개의 패킷이 전송 큐에 있을 수 있음을 나타냅니다. 패킷은 패킷 데이터의 일부 또는 전체에 적용되는 ACK를 연결 상대방으로부터 수신할 때까지 전송 큐에 남아 있습니다. 이 상수는 ***nx_tcp.h** _에 정의됩니다. 애플리케이션은 _*_nx_api.h_**를 포함하기 전에 값을 정의하여 기본값을 재정의할 수 있습니다. |
| X_TCP_MSS_CHECKING_ENABLED | **NX_ENABLE_TCP_MSS_CHECKING** 으로 이름이 변경되었습니다. 아직 지원되는 옵션이지만 새 디자인에서는 **NX_ENABLE_TCP_MSS_CHECKING** 을 사용하는 것이 좋습니다. |
| NX_TCP_MSS_MINIMUM | NetX TCP 모듈에서 수락하는 최소 MSS 값을 정의하는 기호입니다. 이 기능은 **NX_ENABLE_TCP_MSS_CHECK** 를 통해 사용하도록 설정됩니다. |
| NX_TCP_RETRY_SHIFT | 재시도 간 재전송 시간 제한 기간이 변경되는 방법을 지정합니다. 이 값이 0이면 초기 재전송 시간 제한과 이어지는 재전송 시간 제한이 동일합니다. 이 값이 1이면 각각의 이어지는 재전송 시간 제한이 2배로 길어집니다. 이 값이 2이면 각각의 이어지는 재전송 시간 제한이 4배로 길어집니다. 기본값은 0이며 ***nx_tcp.h** _에 정의됩니다. 애플리케이션은 _*_nx_api.h_**를 포함하기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |
| NX_TCP_TRANSMIT_TIMER_RATE| TCP 전송 재시도 처리에 대한 타이머 속도를 계산하기 위해 시스템 틱 수(**NX_IP_PERIODIC_RATE**)를 나누는 방법을 지정합니다. 기본값은 1로, 1초를 나타내며 **_nx_tcp.h_ *_에 정의됩니다. 애플리케이션은 _* _nx_api.h_** 를 포함하기 전에 값을 정의하여 이 기본값을 재정의할 수 있습니다. |

### <a name="udp-configuration-options"></a>UDP 구성 옵션
| 옵션  | Description  |
|---|---|
| NX_DISABLE_UDP_INFO | 정의된 경우 UDP 정보를 수집할 수 없습니다. |
| NX_DISABLE_UDP_RX_CHECKSUM | 정의된 경우 수신 UDP 패킷의 UDP 체크섬 계산을 사용하지 않도록 설정합니다. 네트워크 인터페이스 드라이버가 하드웨어의 UDP 헤더 체크섬을 확인할 수 있고 애플리케이션이 IP 조각화 논리를 사용하도록 설정하지 않는 경우에 유용합니다. |
| NX_DISABLE_UDP_TX_CHECKSUM | 정의된 경우 발신 UDP 패킷의 UDP 체크섬 계산을 사용하지 않도록 설정합니다. 네트워크 인터페이스 드라이버가 UDP 헤더 체크섬을 계산하여 데이터를 전송하기 전 IP 헤드에 값을 삽입할 수 있으며 애플리케이션이 IP 조각화 논리를 사용하도록 설정하지 않는 경우에 유용합니다. |

## <a name="netx-version-id"></a>NetX 버전 ID

사용자 및 애플리케이션 소프트웨어 둘 다 런타임 중에 NetX의 현재 버전을 사용할 수 있습니다. 프로그래머는 **nx_port.h** 파일에서 NetX 버전을 가져올 수 있습니다. 또한 이 파일에는 해당 포트의 버전 기록이 포함되어 있습니다. 애플리케이션 소프트웨어는 **_nx_port.h_** 에서 전역 문자열 **_nx_version_id** 를 검사하여 NetX 버전을 가져올 수 있습니다.  

애플리케이션 소프트웨어는 ***nx_api.h***에 정의되어 있는 아래에 표시된 상수에서 릴리스 정보를 가져올 수도 있습니다.

이러한 상수는 이름과 제품 주 버전 및 부 버전별로 현재 제품 릴리스를 식별합니다.

```c
#define EL_PRODUCT_NETX

#define NETX_MAJOR_VERSION

#define NETX_MINOR_VERSION
```