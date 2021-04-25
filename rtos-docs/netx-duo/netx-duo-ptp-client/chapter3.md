---
title: 챕터 3 - Azure RTOS NetX Duo PTP 클라이언트 서비스 설명
description: 이 챕터에서는 모든 NetX Duo PTP 클라이언트 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b4cdeca81c157934e35a219cd5535ec38f2c0746
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810620"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a>챕터 3 - Azure RTOS NetX Duo PTP 클라이언트 서비스 설명

이 챕터에서는 아래에 나열된 모든 NetX Duo PTP 클라이언트 서비스를 알파벳 순서로 설명합니다.

[!NOTE]
> *다음 API 함수 설명의 **반환 값** 섹션에서 **굵게 표시된** 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용할 수 없게 됩니다.*

## <a name="nx_ptp_client_create"></a>nx_ptp_client_create

PTP 클라이언트 인스턴스 만들기.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a>Description

이 서비스는 PTP 클라이언트의 인스턴스를 만듭니다.

애플리케이션에서 패킷을 전송하기 위해 먼저 PTP 클라이언트에 대한 IP 인스턴스 및 패킷 풀을 만들어야 합니다. 패킷 풀의 경우 애플리케이션은 IP 인스턴스에서 동일한 패킷 풀을 사용할 수 있습니다. 또는 PTP 클라이언트에 대한 전용 패킷 풀을 만들 수 있습니다.  전용 패킷 풀 접근 방식은 작은 패킷(IPv6을 사용하는 경우 128바이트 패킷 또는 IPv4 전용의 경우 108바이트)을 사용하는 이점이 있습니다.

### <a name="input-parameters"></a>입력 매개 변수
* **client_ptr** 만들 PTP 클라이언트에 대한 포인터
* **ip_ptr** IP 인스턴스에 대한 포인터
* **interface_index** PTP 네트워크 인터페이스의 인덱스
* **packet_pool_ptr** 클라이언트 패킷 풀에 대한 포인터
* **thread_priority**  PTP 스레드의 우선 순위
* **thread_stack** 스레드 스택에 대한 포인터
* **stack_size** 스레드 스택의 크기
* **clock_callback** PTP 클록 콜백
* **clock_callback_data** 클록 콜백에 대한 데이터

### <a name="return-values"></a>반환 값
* **NX_SUCCESS** (0x00) 클라이언트를 만듦
* **NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) 패킷 페이로드가 너무 작음
* **NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) 클록 콜백 실패
* **status** NetX Duo 및 ThreadX 서비스 호출의 완료 상태
* NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수
* NX_INVALID_INTERFACE (0x4C) 잘못된 인터페이스

### <a name="allowed-from"></a>허용된 위치
스레드

### <a name="example"></a>예제
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a>nx_ptp_client_delete

PTP 클라이언트 인스턴스를 삭제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 PTP 클라이언트의 인스턴스를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수
* **client_ptr** 삭제할 PTP 클라이언트에 대한 포인터

### <a name="return-values"></a>반환 값
* **NX_SUCCESS** (0x00) 클라이언트를 삭제함
* NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용된 위치
스레드

### <a name="example"></a>예제
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a>nx_ptp_client_master_info_get

마스터 클록 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a>Description
이 서비스는 마스터 클록의 정보를 가져옵니다. 마스터 제어 블록은 이벤트 콜백 함수를 통해 사용자 애플리케이션에 전달됩니다.

### <a name="input-parameters"></a>입력 매개 변수
* **master_ptr** PTP 마스터 클록에 대한 포인터
* **주소** 마스터 클록의 주소
* **port_identity** PTP 마스터 포트 및 ID
* **port_identity_length** PTP 마스터 포트 및 ID의 길이
* **priority1** PTP 마스터 클록의 Priority1
* **priority2** PTP 마스터 클록의 Priority2
* **clock_class** PTP 마스터 클록의 클래스
* **clock_accuracy** PTP 마스터 클록의 정확도
* **clock_variance** PTP 마스터 클록의 분산
* **grandmaster_identity** Grandmaster 클록의 ID
* **grandmaster_identity_length** Grandmaster ID의 길이
* **steps_removed** PTP 헤더에서 제거된 단계
* **time_source** Grandmaster 클록에서 사용하는 타이머의 소스입니다.

### <a name="return-values"></a>반환 값
* **NX_SUCCESS** (0x00) 마스터 클록 정보 가져오기에 성공
* NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용된 위치
스레드

### <a name="example"></a>예제
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a>nx_ptp_client_packet_timestamp_notify

PTP 클라이언트에 패킷의 타임스탬프를 알립니다.

### <a name="prototype"></a>프로토타입

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a>Description
이 서비스는 패킷이 타임스탬프와 함께 전송됨을 PTP 클라이언트에 알립니다. 이 서비스는 네트워크 드라이버용으로 설계되었으며 패킷이 전송될 때 호출됩니다. 일반적으로 하드웨어가 타임스탬프를 생성합니다.

### <a name="input-parameters"></a>입력 매개 변수
* **client_ptr** 만들 PTP 클라이언트에 대한 포인터
* **packet_ptr** 전송되는 PTP 패킷에 대한 포인터
* **timestamp_ptr** PTP 패킷의 타임스탬프에 대한 포인터

### <a name="return-values"></a>반환 값
없음

### <a name="allowed-from"></a>허용된 위치
스레드

### <a name="example"></a>예제
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a>nx_ptp_client_soft_clock_callback

PTP 클록의 소프트웨어 구현입니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a>Description
이 콜백 함수는 시뮬레이션된 낮은 해상도의 PTP 클록 원본으로 사용됩니다. 이 루틴은 참조로 제공되며 프로덕션에 사용할 수 없습니다.

### <a name="input-parameters"></a>입력 매개 변수
* **client_ptr** 만들 PTP 클라이언트에 대한 포인터
* **작업** 콜백 작업, 유효한 값은 다음과 같이 정의됩니다.
  * **NX_PTP_CLIENT_CLOCK_INIT** 클록을 초기화합니다.
  * **NX_PTP_CLIENT_CLOCK_SET** `time_ptr`(으)로 지정된 현재 타임스탬프를 설정합니다.
  * **NX_PTP_CLIENT_CLOCK_GET** `time_ptr`(으)로 현재 타임스탬프를 반환합니다.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** `packet_ptr`에서 `time_ptr`(으)로 타임스탬프를 추출합니다.
  * **NX_PTP_CLIENT_CLOCK_ADJUST** 현재 타임스탬프를 *1* 초 미만으로 조정합니다.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** 전송 시 PTP 클라이언트에 타임스탬프를 알리도록 하는 `packet_ptr`을(를) 표시합니다.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** 소프트 타이머를 업데이트합니다. 하드웨어 클록에서 무시할 수 있습니다.
* **time_ptr** 타임스탬프를 가리키는 포인터입니다.
* **packet_ptr** 패킷을 가리키는 포인터입니다.
* **callback_data** 불투명 콜백 데이터를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값
* **NX_SUCCESS** (0X00) 작업 성공
* **NX_PTP_PARAM_ERROR** (0xD03) 잘못된 매개 변수

### <a name="allowed-from"></a>허용된 위치
PTP 내부

### <a name="example"></a>예제
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a>nx_ptp_client_start

PTP 클라이언트를 시작합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a>Description
이 서비스는 이전에 만든 PTP 인스턴스를 시작합니다.

### <a name="input-parameters"></a>입력 매개 변수
* **client_ptr** 만들 PTP 클라이언트에 대한 포인터
* **client_port_identity_ptr** 클라이언트 포트 및 ID에 대한 포인터입니다. NULL이 될 수 있습니다.
* **client_port_identity_length** 클라이언트 포트 및 ID의 길이입니다. client_port_identity_ptr이 NULL이거나 NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)인 경우 0이어야 합니다.
* **도메인** PTP 클록 도메인
* **transport_specific** 4비트 전송 관련
* **event_callback** 이벤트에서 호출되는 콜백 함수
* **event_callback_data** 이벤트 콜백에 대한 데이터

### <a name="return-values"></a>반환 값
* **NX_SUCCESS** (0x00) 클라이언트가 시작됨
* **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP 클라이언트가 이미 시작됨
* **status** NetX Duo 및 ThreadX 서비스 호출의 완료 상태
* NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용된 위치
스레드

### <a name="example"></a>예제
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a>nx_ptp_client_stop

PTP 클라이언트를 중지합니다.  PTP 클라이언트를 중지한 후에는 PTP 패킷을 처리 하지 않으며 PTP 패킷을 전송하지도 않습니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description
이 서비스는 이전에 만들어서 시작한 PTP 클라이언트 인스턴스를 중지합니다.

### <a name="input-parameters"></a>입력 매개 변수
* **client_ptr** 중지할 PTP 클라이언트에 대한 포인터

### <a name="return-values"></a>반환 값
* **NX_SUCCESS** (0x00) 클라이언트를 만듦
* **NX_PTP_CLIENT_NOT_STARTED** (0xD01) 클라이언트가 시작되지 않음
* NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용된 위치
스레드

### <a name="example"></a>예제
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a>nx_ptp_client_sync_info_get

동기화 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a>Description
이 서비스는 동기화 메시지에 대한 정보를 가져옵니다. 동기화 제어 블록은 이벤트 콜백 함수를 통해 사용자 애플리케이션에 전달됩니다.

### <a name="input-parameters"></a>입력 매개 변수
* **client_ptr** 만들 PTP 클라이언트에 대한 포인터
* **플래그** 동기화 메시지의 플래그
* **utc_offset** TAI와 UTC 사이의 오프셋

### <a name="return-values"></a>반환 값
* **NX_SUCCESS** (0X00) 동기화 정보를 가져옴
* NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용된 위치
스레드

### <a name="example"></a>예제
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a>nx_ptp_client_time_get

현재 시간을 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Description
이 서비스는 PTP 클록의 현재 값을 가져옵니다. 이는 PTP 클라이언트를 마스터 클록과 동기화하지 않아도 사용할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수
* **client_ptr** 만들 PTP 클라이언트에 대한 포인터
* **time_ptr** PTP 시간에 대한 포인터

### <a name="return-values"></a>반환 값
* **NX_SUCCESS** (0x00) 클라이언트를 만듦
* NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용된 위치
스레드

### <a name="example"></a>예제
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a>nx_ptp_client_time_set

현재 시간을 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Description
이 서비스는 PTP 클록의 현재 값을 설정합니다. 이는 PTP 클라이언트를 시작하기 전에 호출되어야 합니다.

### <a name="input-parameters"></a>입력 매개 변수
* **client_ptr** 만들 PTP 클라이언트에 대한 포인터
* **time_ptr** PTP 시간에 대한 포인터

### <a name="return-values"></a>반환 값
* **NX_SUCCESS** (0x00) 클라이언트를 만듦
* **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP 클라이언트가 이미 시작됨
* NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용된 위치
스레드

### <a name="example"></a>예제
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a>nx_ptp_client_utility_convert_time_to_date

PTP 시간을 UTC 날짜 및 시간으로 변환합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a>Description
이 서비스는 PTP 시간을 UTC 날짜 및 시간으로 변환합니다.

### <a name="input-parameters"></a>입력 매개 변수
* **time_ptr** PTP 시간에 대한 포인터
* **오프셋** PTP 시간을 추가하기 위한 부호가 있는 두 번째 오프셋
* **date_time_ptr** 결과 날짜에 대한 포인터

### <a name="return-values"></a>반환 값
* **NX_SUCCESS** (0x00) 클라이언트를 만듦
* **결과 날짜에 대한 포인터** (0xD03) 잘못된 입력 매개 변수
* NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용된 위치
스레드

### <a name="example"></a>예제
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a>nx_ptp_client_utility_time_diff

두 개의 PTP 시간을 비교합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a>Description
이 서비스는 두 PTP 시간 사이의 차이를 계산합니다.

### <a name="input-parameters"></a>입력 매개 변수
* **time1_ptr** 첫 번째 PTP 시간에 대한 포인터
* **time2_ptr** 두 번째 PTP 시간에 대한 포인터
* **result_ptr** 결과 time1-time2에 대한 포인터

### <a name="return-values"></a>반환 값
* **NX_SUCCESS** (0x00) 클라이언트를 만듦
* NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용된 위치
스레드

### <a name="example"></a>예제
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```