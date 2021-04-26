---
title: 1장 - Azure RTOS NetX Duo SNTP 소개
description: Azure RTOS NetX SNTP(Simple Network Time Protocol)는 인터넷을 통해 시계를 동기화하기 위해 설계된 프로토콜입니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b3e1170197c6c4981060459104da80e354fac5db
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810567"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-sntp"></a>1장 - Azure RTOS NetX Duo SNTP 소개 

Azure RTOS NetX SNTP(Simple Network Time Protocol)는 인터넷을 통해 시계를 동기화하기 위해 설계된 프로토콜입니다. SNTP 버전 4는 NTP(Network Time Protocol)를 기준으로 하는 간소화된 프로토콜입니다. UDP(User Datagram Protocol) 서비스를 활용하여 간단한 상태 비저장 프로토콜에서 시간 업데이트를 수행합니다. NTP처럼 복잡하지는 않지만 SNTP는 상당히 안정적이고 정확합니다. 오늘날 대부분의 인터넷 환경에서 SNTP는 동기화 원본 및 네트워크 경로의 특성에 따라 1-50밀리초의 정확도를 제공합니다. SNTP는 시간 업데이트를 안정적으로 수신하기 위한 많은 옵션을 제공합니다. 대체 서버로 전환하여 백오프 폴링 알고리즘과 자동 시간 서버 검색을 적용하는 기능은 SNTP 클라이언트가 가변적인 인터넷 시간 서비스 환경을 처리할 수 있는 방법 중 일부에 불과합니다. 이 방법의 경우 정밀도는 부족하지만 구현 간편성 및 용이성이 개선됩니다. SNTP는 주로 국가별 시간 및 빈도 분산(예: NTP 서버) 서비스에 액세스할 수 있는 포괄적인 메커니즘을 제공하기 위한 것입니다.

## <a name="netx-duo-sntp-client-requirements"></a>NetX Duo SNTP 클라이언트 요구 사항

NetX Duo SNTP 클라이언트를 사용하려면 IP 인스턴스가 이미 만들어져 있어야 합니다. 또한 동일한 IP 인스턴스에서 UDP를 사용하도록 설정해야 하며, 대체 포트가 잘 작동하더라도 SNTP 서버에 시간 데이터를 전송하는 데 사용되는 *잘 알려진* 포트 123에 액세스할 수 있어야 합니다. 브로드캐스트 클라이언트는 브로드캐스트 서버가 보내는 UDP 포트(일반적으로 123)를 바인딩해야 합니다. NetX Duo SNTP 클라이언트 애플리케이션에는 하나 이상의 IP SNTP 서버 주소가 있어야 합니다.

## <a name="netx-duo-sntp-client-limitations"></a>NetX Duo SNTP 클라이언트 제한 사항 

SNTP 클라이언트 API에서 처리하는 NTP 시간 업데이트의 현지 시간 전체 자릿수 표시는 밀리초 정밀도로 제한됩니다.

SNTP 클라이언트는 언제든지 단일 SNTP 서버 주소만 보유합니다. 해당 서버가 더 이상 유효하지 않은 것으로 나타나는 경우 애플리케이션에서 SNTP 클라이언트 작업을 중지하고 브로드캐스트 또는 유니캐스트 SNTP 통신을 사용하여 다른 SNTP 서버 주소로 다시 초기화해야 합니다.

SNTP 클라이언트는 manycast을 지원하지 않습니다.

NetX Duo SNTP 클라이언트는 수신 패킷 데이터를 확인하는 인증 메커니즘을 지원하지 않습니다.

## <a name="netx-duo-sntp-client-operation"></a>NetX Duo SNTP 클라이언트 작업

RFC 4330은 SNTP 클라이언트를 로컬 네트워크의 최고 Stratum에서 NTP 또는 SNTP 클라이언트가 동기화를 위해 종속되지 않는 구성으로 작동할 것을 권장합니다. Stratum 수준은 NTP 시간 계층에서의 호스트 위치를 반영합니다. 여기서 Stratum 1은 가장 높은 수준(루트 시간 서버)이고 15는 허용되는 가장 낮은 수준(예: 클라이언트)입니다. SNTP 클라이언트 기본 최소 stratum은 2입니다.

NetX Duo SNTP 클라이언트는 유니캐스트 또는 브로드캐스트의 두 가지 기본 모드 중 하나로 작동되어 인터넷을 통한 시간을 파악할 수 있습니다. 유니캐스트 모드에서 클라이언트는 정기적으로 SNTP 서버를 폴링하고 해당 서버에서 응답을 받을 때까지 기다립니다. 일단 수신되면 클라이언트는 RFC 4330에서 권장하는 '온전성 검사' 세트를 적용하여 응답에 올바른 시간 업데이트가 포함되어 있는지 확인합니다. 그런 다음, 클라이언트는 서버 시계에 대한 시간 차이(있는 경우)를 로컬 시계에 적용합니다. 브로드캐스트 모드에서 클라이언트는 시간 업데이트 브로드캐스트를 수신 대기하고, 비슷한 온전성 검사 세트를 적용하여 업데이트 시간 데이터를 확인한 후에 로컬 시계를 유지 관리합니다. 온전성 검사는 아래의 **SNTP 온전성 검사** 섹션에 자세히 설명되어 있습니다.

어떤 모드에서든지 클라이언트를 실행하려면 먼저 해당 작동 매개 변수를 설정해야 합니다. 이러한 작업은 각각 유니캐스트 또는 브로드캐스트 모드에 대해 nx_sntp_client_initialize_unicast 또는 nx_sntp_client_initialize_broadcast를 호출하여 수행됩니다. 이러한 매개 변수는 유효한 업데이트가 없는 최대 시간 경과에 대한 제한 시간, 수신된 잘못된 연속 업데이트에 대한 제한, 유니캐스트 모드의 폴링 간격, 작업 모드(예: 유니캐스트 및 브로드캐스트), SNTP 서버를 설정합니다.

최대 시간 경과 또는 수신된 유효하지 않은 최대 업데이트를 초과하는 경우 SNTP 클라이언트는 계속 실행되지만 현재 SNTP 서버 상태를 잘못됨으로 설정합니다. 애플리케이션은 nx_sntp_client_receiving_updates 서비스를 통해 SNTP 클라이언트를 폴링하여 SNTP 서버가 유효한 업데이트를 계속 보내고 있는지 확인할 수 있습니다. 유효한 업데이트를 보내고 있지 않으면 nx_sntp_client_stop 서비스를 통해 SNTP 클라이언트 스레드를 중지하고 두 초기화 서비스 중 하나를 호출하여 다른 SNTP 서버 주소를 설정해야 합니다. SNTP 클라이언트를 다시 시작하기 위해 애플리케이션은 nx_sntp_client_run_broadcast 또는 nx_sntp_client_run_unicast를 호출합니다. 애플리케이션은 초기화 호출에서 SNTP 클라이언트 작동 모드를 변경하여 필요에 따라 유니캐스트 또는 브로드캐스트로 전환할 수 있습니다.

### <a name="local-clock-operation"></a>로컬 시계 작업

마스터 NTP 시계에 표시되는 시간(초)을 기준으로 하는 SNTP 시간 또는 첫 번째 NTP Epoch에서 경과된 시간(초)입니다(예: 1월 1일 **1900 00:00:00부터** 1월 1일 **1999 00:00:00** 까지). significance 01-01-1999는 마지막 윤초가 나왔을 때입니다. 이 값은 아래와 같이 정의됩니다.

\#define NTP_SECONDS_AT_01011999 0xBA368E80

SNTP 클라이언트를 실행하기 전에 애플리케이션은 클라이언트에서 기준 시간으로 사용할 SNTP 클라이언트 로컬 시간을 선택적으로 초기화할 수 있습니다. 이렇게 하려면 nx_sntp_client_set_local_time 서비스를 사용해야 합니다. 이 서비스는 시간을 NTP 형식(초 및 초의 부분)으로 시간을 사용합니다. 여기서 초의 부분은 NTP 압축 시간(밀리초)입니다. 이상적으로 애플리케이션은 독립된 원본에서 SNTP 시간을 얻을 수 있습니다. 년, 월, 일 및 시간을 NetX Duo SNTP 클라이언트의 NTP 시간으로 변환하기 위한 API는 없습니다. NTP 시간 형식에 대한 설명은 *IPv4, IPv6 및 OSI에 대한 RFC4330 "SNTP(Simple Network Time Protocol) 버전 4"* 를 참조하세요.

SNTP 클라이언트를 시작할 때 기본 로컬 시간이 제공되지 않으면 SNTP 클라이언트는 첫 번째 업데이트의 로컬 시간과 비교하지 않고 SNTP 업데이트를 수락합니다. 그 후에는 최대 및 최소 시간 업데이트 값을 적용하여 로컬 시간이 달라지는지 확인합니다.

SNTP 클라이언트 로컬 시간을 얻기 위해 애플리케이션은 nx_sntp_client_get_local_time_extended 서비스를 사용할 수 있습니다.

### <a name="sntp-sanity-checks"></a>SNTP 온전성 검사 

클라이언트는 다음 기준에 따라 수신 패킷을 검사합니다.

  - 원본 IP 주소는 현재 서버 IP 주소와 일치해야 합니다.

  - 발신자 원본 포트는 현재 서버 원본 포트와 일치해야 합니다.

  - 패킷 길이는 SNTP 시간 메시지를 보관할 최소 길이여야 합니다.

그런 다음, 패킷 버퍼에서 시간 데이터가 추출되며, 클라이언트는 이 시간 데이터에 특정 '온전성 검사' 세트를 적용합니다.

  - 윤년/윤초 표시기가 3으로 설정되면 서버가 동기화되지 않음을 나타냅니다. 클라이언트는 대체 서버를 찾으려고 시도합니다.

  - 0으로 설정된 Stratum 필드를 KOD(Kiss of Death) 패킷이라고 합니다. 이 상황에 대한 SMTP 클라이언트 KOD 처리기는 사용자 정의 콜백입니다. 작은 예제 데모 파일에는 이 상황에 대한 간단한 KOD 처리기가 포함되어 있습니다. 참조 ID 필드에는 선택적으로 KOD 응답 이유를 나타내는 코드가 포함됩니다. 어떤 경우에도 KOD 처리기는 SNTP 서버에서의 Kiss of Death 수신 문제를 처리하는 방법을 나타내야 합니다. 일반적으로 다른 SNTP 서버를 사용하여 SNTP 클라이언트를 다시 초기화하려고 합니다.

  - 서버 SNTP 버전, Stratum 및 작업 모드는 클라이언트 서비스와 일치해야 합니다.

  - 클라이언트가 서버 시계 분산 최대값으로 구성된 경우 클라이언트는 받은 첫 번째 업데이트에 대해서만 서버 시계 분산을 확인하고, 클라이언트 최대값을 초과하는 경우 클라이언트는 서버를 거부합니다.

  - 또한 서버 타임스탬프 필드는 특정 검사를 통과해야 합니다. 유니캐스트 서버의 경우 모든 시간 필드를 채워야 하며 NULL일 수 없습니다. 클라이언트의 SNTP 시간 메시지 요청에서 시작 타임스탬프가 전송 타임스탬프와 같아야 합니다. 이렇게 하면 악의적인 침입자 및 Rogue 서버 동작으로부터 클라이언트가 보호됩니다. 브로드캐스트 서버는 전송 타임스탬프를 입력하기만 하면 됩니다. 서버는 클라이언트에서 어떤 항목도 수신하지 않으므로 채울 수신 또는 시작 필드가 없습니다.

    실패한 온전성 검사는 시간 업데이트를 잘못된 시간 업데이트로 표시합니다. SNTP 클라이언트 온전성 검사 서비스는 동일한 서버에서 수신된 잘못된 연속 시간 업데이트 수를 추적합니다.

SNTP 클라이언트 스레드 작업이 로컬 SNTP 클라이언트 시간에 적용하기 위해 SNTP 패킷의 유효성을 검사하는 경우 SNTP 클라이언트 `nx_sntp_client_invalid_time_updates.`의 수가 증분됩니다. 또한 호출자에게 오류 상태를 반환하지만 모두 내부에서 처리되므로 애플리케이션에 즉시 표시되지 않습니다. 실패한 시간 업데이트를 검색하는 방법은 SNTP 서버 시간 업데이트를 수신한 후에 SNTP 클라이언트 `nx_sntp_client_invalid_time_updates`의 값을 쿼리하는 것입니다.

서버 시간 업데이트가 온전성 검사를 통과하면 클라이언트는 시간 데이터를 로컬 시간으로 처리하려고 시도합니다. 클라이언트가 왕복 계산을 위해 구성된 경우(예: 업데이트 요청을 보낸 시간부터 받은 시간까지) 왕복 시간이 계산됩니다. 이 값을 절반으로 나눈 후 서버 시간에 추가합니다.

다음으로, 이 업데이트가 현재 SNTP 서버에서 수신한 첫 번째 업데이트인 경우 SNTP 클라이언트는 서버 로컬 시간과 클라이언트 로컬 시간 사이의 차이를 무시해야 하는지 여부를 확인합니다. 그 이후에 SNTP 서버의 모든 업데이트가 클라이언트 로컬 시간과 차이가 있는지 평가됩니다.

클라이언트 시간과 서버 시간의 차이는 `NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT`와 비교됩니다. 이 값을 초과하면 데이터가 throw됩니다. 차이가 `NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT`보다 작으면 너무 작아서 조정이 필요하지 않은 것으로 간주됩니다.

이러한 모든 검사를 통과하면 내부 SNTP 클라이언트 처리 지연을 수정하기 위해 SNTP 클라이언트에 시간 업데이트가 적용됩니다.

### <a name="sntp-asynchronous-unicast-requests"></a>SNTP 비동기 유니캐스트 요청 

SNTP 클라이언트를 사용하면 호스트 애플리케이션에서 현재 시간에 대한 유니캐스트 요청을 NTP 서버에서 비동기적으로 보낼 수 있습니다.

```C
UINT _nx_sntp_client_request_unicast_time(
NX_SNTP_CLIENT *client_ptr, 
UINT wait_option)
```

대기 옵션은 응답을 대기하기까지의 만료 기간입니다.

NTP 서버에서 응답하는 경우 SNTP 클라이언트 로컬 시간을 업데이트하기 전에 이전 섹션에서 설명한 것과 동일한 처리 및 온전성 검사가 패킷에 적용됩니다.

호출이 성공적으로 완료되면 애플리케이션은 업데이트된 로컬 시간에 대해 nx_sntp_client_utility_display_date_time 또는 nx_sntp_client_get_local_time_extended를 호출할 수 있습니다.

이러한 유니캐스트 요청은 다음 유니캐스트 요청 전송에 대한 일반적인 SNTP 클라이언트 일정을 방해하지 않으며, 브로드캐스트 모드인 경우 다음 NTP 브로드캐스트가 나와야 하는 시기에도 영향을 미치지 않습니다.

### <a name="periodic-local-time-updates"></a>정기 로컬 시간 업데이트

로컬 시간에 대한 최대 조정은 NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT 옵션(밀리초)에 설정됩니다. 유니캐스트 SNTP 클라이언트 작업에 대한 폴링 업데이트 간격은 NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL 옵션(초)에 설정됩니다. 폴링 간격이 최대 조정보다 크면 첫 번째 서버 업데이트 이후의 후속 서버 업데이트가 거부됩니다. 이를 방지하기 위해 SNTP 클라이언트는 NX_SNTP_UPDATE_TIMEOUT_INTERVAL로 정의된 로컬 시간을 주기적으로 업데이트합니다. 

온보딩 RTC와 서버 시간(SNTP 클라이언트 로컬 시간으로 설정해야 함) 사이에 차이가 있는 경우 RTC를 SNTP 클라이언트 시간과 동기화해야 합니다(이 사용자 가이드에서는 설명하지 않음).

SNTP 서버 업데이트는 시간당 한 번 넘게 발생하지 않아야 하므로 SNTP 클라이언트에서 서버 업데이트 또는 서버 상태를 이 간격보다 더 자주 폴링하는 것은 유용하지 않습니다. 그러나 SNTP 클라이언트는 최대 시간 조정 매개 변수 NX_SNTP_CLIENT_MAX_TIME_LAPSE를 크게 벗어나지 않도록 로컬 시계를 충분히 자주 업데이트해야 합니다.

또는 최대 조정 NX_SNTP_CLIENT_MAX_TIME_LAPSE를 유니캐스트 폴링 업데이트(또는 예상되는 브로드캐스트 간격)보다 큰 값으로 설정할 수 있습니다. 후자의 경우는 독립적인 실시간 시계를 사용할 필요가 없습니다. 그러나 SNTP 프로토콜의 목적은 로컬 RTC 또는 네트워크 시간 업데이트에 대한 전체적인 의존을 피하는 것입니다. 또한 SNTP 서버 업데이트는 로컬 시간 시계의 드리프트를 방지하기 위한 것입니다.

## <a name="multiple-network-interfaces"></a>여러 네트워크 인터페이스

NetX Duo SNTP 클라이언트는 해당 네트워크가 IP 인스턴스에 등록되어 있는 한, 보조 네트워크에서 실행되도록 구성할 수 있습니다. 보조 네트워크를 등록하는 방법에 대한 자세한 내용은 NetX Duo 또는 NetX 사용자 가이드를 참조하세요.

nx_sntp_client_create 호출에서, 세 번째 입력인 iface_index를 SNTP 클라이언트가 시간 업데이트를 받을 네트워크의 인덱스로 설정합니다. 기본 인터페이스는 항상 인덱스 0에 있습니다. NetX Duo SNTP 클라이언트는 여러 네트워크 인터페이스에서 동시에 시간 업데이트를 지원할 수 없습니다.

## <a name="sntp-and-ntp-rfcs"></a>SNTP 및 NTP RFC

NetX Duo SNTP 클라이언트는 IPv4, IPv6 및 OSI에 대한 RFC4330 "SNTP(Simple Network Time Protocol) 버전 4” 및 관련 RFC를 준수합니다.