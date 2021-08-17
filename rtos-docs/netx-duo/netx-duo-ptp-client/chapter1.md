---
title: 1장 - Azure RTOS NetX Duo PTP 클라이언트 소개
description: 이 장에서는 Azure RTOS NetX Duo PTP 클라이언트를 소개합니다.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf7210529121c8e49ff3cabbb7c673288b803f24760096396f32f33d4a9fb7e6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798047"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a>1장 - Azure RTOS NetX Duo PTP 클라이언트 소개

Azure RTOS NetX Duo PTP는 PTP(Precision Time Protocol, 정밀 시각 프로토콜) 버전 2, IEEE 1588-2008의 클라이언트 부분을 구현합니다. IPv4 또는 IPv6 멀티 캐스트 패킷을 통해 서로 통신하여 로컬 네트워크의 MCU 간에 클록을 동기화하는 데 사용됩니다.

## <a name="netx-duo-ptp-client-setup"></a>NetX Duo PTP 클라이언트 설정

제대로 작동하기 위해 PTP 클라이언트 패키지에 NetX Duo IP 인스턴스가 이미 생성되어 있어야 합니다.

기본적으로 PTP 클라이언트는 IPv4 멀티캐스트 그룹을 조인합니다. IPv6 네트워크에서 PTP 클라이언트를 실행하려면 NetX Duo 라이브러리를 빌드할 때 `NX_ENABLE_IPV6_MULTICAST`를 정의해야 합니다.

PTP 클라이언트를 만들 때 애플리케이션은 들어오고 나가는 패킷의 타임스탬프를 처리하는 콜백 함수를 제공해야 합니다. 높은 해상도를 얻기 위해 애플리케이션에서 고해상도 타이머를 사용하여 타임스탬프를 생성하는 것이 좋습니다. 시뮬레이터에서 PTP를 실행하기 위해 소프트웨어 기반 구현 `nx_ptp_client_soft_clock_callback`이 제공됩니다.

PTP 클라이언트는 PTP 메시지를 전송하기 위한 패킷 풀이 필요합니다. 패킷 풀의 페이로드 크기는 `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE` 이상이어야 합니다. 즉, IPv4의 경우 108바이트이고 IPv6이 사용되는 경우에는 128바이트입니다.

PTP 클라이언트를 만든 후 애플리케이션은 PTP 클라이언트를 시작할 수 있습니다. 동기화는 PTP 도우미 스레드에서 수행됩니다. 이벤트 콜백 함수를 지정할 수 있습니다. 다음 이벤트 중 하나가 발생하면 호출됩니다.
* 마스터가 선택됩니다. 
* 시간이 보정됩니다.
* 마스터 시간이 초과됩니다.

## <a name="netx-duo-ptp-client-messages"></a>NetX Duo PTP 클라이언트 메시지

NetX Duo PTP 클라이언트는 지연 요청-응답 메커니즘만 구현합니다. PTP 클라이언트는 두 개의 UDP 포트를 엽니다. **이벤트** 메시지의 경우 *319* 이고 **일반** 메시지의 경우 *320* 입니다. 이 메커니즘에는 다섯 가지 유형의 메시지가 있습니다.

* **Announce**. 이는 이벤트 메시지입니다. 마스터 클록 선택에 사용됩니다.
* **Sync**. 이는 이벤트 메시지입니다. 원본 타임스탬프를 보내고 마스터에서 클라이언트로의 경로 지연을 계산하는 데 사용됩니다.
* **Follow_Up**. 이는 일반 메시지입니다. 이는 선택 사항이며 관련된 Sync 메시지에서 원본 타임스탬프를 수정하는 데 사용됩니다. Sync 플래그에서 두 단계 비트가 설정된 경우에만 전송됩니다.
* **Delay_Req**. 이는 이벤트 메시지입니다. Delay_Resp 수신 시 클라이언트에서 마스터로의 경로 지연을 계산하기 위해 PTP 클라이언트에서 전송됩니다.
* **Delay_Resp**. 이는 이벤트 메시지입니다. 클라이언트에서 마스터로의 경로 지연을 계산하기 위해 마스터에서 클라이언트로 전송됩니다.

*“Best master clock” 알고리즘이 구현되어 있지 않습니다. PTP 클라이언트가 수신 대기 상태인 경우 첫 번째 마스터 클록만 수락됩니다.*

## <a name="netx-duo-ptp-client-clock-callback"></a>NetX Duo PTP 클라이언트 클록 콜백
마스터에서 클록을 동기화하려면 PTP 클라이언트에 로컬 클록이 필요합니다. 클록 콜백 함수는 만드는 동안 PTP 클라이언트에 전달됩니다. 클록 콜백 루틴의 형식은 아래에 정의되어 있습니다.
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
입력 매개 변수는 다음과 같이 정의됩니다.
* *client_ptr* 은 PTP 클라이언트를 가리킵니다.
* *operation* 은 콜백 작업을 지정합니다. 유효한 값은 아래 목록에 표시된 것처럼 정의됩니다.
  * **NX_PTP_CLIENT_CLOCK_INIT** 클록을 초기화합니다.
  * **NX_PTP_CLIENT_CLOCK_SET** `time_ptr`로 지정된 현재 타임스탬프를 설정합니다.
  * **NX_PTP_CLIENT_CLOCK_GET** `time_ptr`로 현재 타임스탬프를 반환합니다.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** `packet_ptr`에서 `time_ptr`로 타임스탬프를 추출합니다.
  * **NX_PTP_CLIENT_CLOCK_ADJUST** 현재 타임스탬프를 *1* 초 미만으로 조정합니다.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** 전송 시 PTP 클라이언트에 타임스탬프를 알려야 하는 `packet_ptr`을 표시합니다.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** 소프트 타이머를 업데이트합니다. 하드웨어 클록에서 무시할 수 있습니다.
* *time_ptr* 은 타임스탬프를 가리킵니다.
* *packet_ptr* 은 패킷을 가리킵니다.
* *callback_data* 는 불투명 콜백 데이터를 가리킵니다.

NX_PTP_TIME 데이터 형식은 다음과 같이 정의됩니다.
```C
typedef struct NX_PTP_TIME_STRUCT
{
    /* The MSB of the number of seconds */
    LONG  second_high;

    /* The LSB of the number of seconds */
    ULONG second_low;

    /* The number of nanoseconds */
    LONG  nanosecond;
} NX_PTP_TIME;
```

## <a name="netx-duo-ptp-client-event-callback"></a>NetX Duo PTP 클라이언트 이벤트 콜백
애플리케이션에 PTP 클라이언트 상태를 알리도록 이벤트 콜백 함수를 설정할 수 있습니다. 이벤트 콜백 루틴의 형식은 아래와 같이 정의됩니다.
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
입력 매개 변수입니다.
* *client_ptr* 은 PTP 클라이언트를 가리킵니다.
* *event* 는 콜백 이벤트를 지정하며 유효한 값은 다음과 같이 정의됩니다.
  * **NX_PTP_CLIENT_EVENT_MASTER** 마스터 클록이 선택됩니다.
  * **NX_PTP_CLIENT_EVENT_SYNC** PTP 클라이언트가 보정됩니다.
  * **NX_PTP_CLIENT_EVENT_TIMEOUT** 마스터 클록의 시간이 초과되었습니다.
* *event_data* 는 이벤트와 관련된 데이터를 지정합니다. 이벤트가 **NX_PTP_CLIENT_EVENT_MASTER** 인 경우 event_data는 `NX_PTP_CLIENT_MASTER` 인스턴스를 가리킵니다. 이벤트가 **NX_PTP_CLIENT_EVENT_SYNC** 인 경우 event data는 `NX_PTP_CLIENT_SYNC` 인스턴스를 가리킵니다.

## <a name="netx-duo-ptp-client-communication"></a>NetX Duo PTP 클라이언트 통신
앞에서 설명한 대로 NetX Duo PTP 클라이언트는 지연 요청-응답 메커니즘만 지원합니다. 이 메커니즘은 아래와 같이 클라이언트와 마스터 클록 사이의 평균 경로 지연을 측정합니다.
1. 클라이언트가 마스터로부터 *Announce* 메시지를 수신하고 가장 적합한 마스터로 선택합니다.
1. 클라이언트가 마스터로부터 *Sync* 메시지를 수신합니다. 타임스탬프 *t1* 은 이 메시지의 원본 타임스탬프입니다. 이 메시지가 수신되면 타임스탬프 *t2* 를 로컬 클록에서 읽습니다.
1. 클라이언트가 마스터로부터 *Follow_Up* 메시지를 수신합니다. 이 메시지는 선택 사항이며 *Sync* 플래그의 두 단계가 설정된 경우에만 유효합니다. 그런 다음, 타임스탬프 *t1* 이 이 메시지의 원본 타임스탬프로 업데이트됩니다.
1. 클라이언트가 *Delay_Req* 메시지를 마스터로 보냅니다. 메시지가 전송될 때 로컬 클록에서 타임스탬프 *t3* 을 읽습니다.
1. 클라이언트가 마스터로부터 *Delay_Resp* 메시지를 수신합니다. 타임스탬프 *t4* 는 이 메시지의 수신 타임스탬프입니다.

평균 경로 지연은 다음과 같이 계산됩니다.
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
마스터의 오프셋은 아래와 같이 계산됩니다.
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> ***correctionField** _는 계산 도중에 무시됩니다._