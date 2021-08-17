---
title: 챕터 5 - 추적 버퍼 생성
description: 이 챕터는 Azure RTOS TraceX 이벤트 버퍼를 빌드하는 방법에 대한 설명을 포함하며 버퍼의 기본 형식에 대해서도 설명합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 7d5c90675728fc7e374d625f5a9ae27340268ca8398200c68fb7113a84aa2983
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801787"
---
# <a name="chapter-5---generating-trace-buffers"></a>챕터 5 - 추적 버퍼 생성

이 챕터는 Azure RTOS TraceX 이벤트 버퍼를 빌드하는 방법에 대한 설명을 포함하며 버퍼의 기본 형식에 대해서도 설명합니다.

## <a name="threadx-event-trace-support"></a>ThreadX 이벤트 추적 지원

ThreadX는 모든 ThreadX 서비스, 스레드 상태 변경 및 사용자 정의 이벤트에 대한 기본 제공 이벤트 추적 지원을 제공합니다. ThreadX 이벤트 추적 기능은 주로 애플리케이션의 마지막 'n' 작업을 분석하는 사후 분석 도구로 설계되었습니다. 개발자는 이 정보를 통해 문제 및/또는 잠재적 최적화 대상을 발견할 수 있습니다.

TraceX는 ThreadX로 빌드된 이벤트 추적 버퍼를 그래픽으로 표시합니다. 다음은 버퍼를 빌드하는 방법과 버퍼의 기본 형식에 대해 설명합니다.

## <a name="enabling-event-trace"></a>이벤트 추적 사용

이벤트 추적을 사용하도록 설정하려면 타임스탬프 상수를 정의하고, **TX_ENABLE_EVENT_TRACE** 가 정의된 ThreadX 라이브러리를 빌드하고, **tx_trace_enable** 함수를 호출하여 추적을 사용하도록 설정하십시오.

## <a name="defining-time-stamp-constants"></a>타임스탬프 상수 정의

타임스탬프 상수는 이벤트 추적 항목에 사용된 타임스탬프에 대한 개발자 제어를 제공하도록 설계되었습니다. 2개의 타임스탬프 상수 및 해당 기본값은 다음과 같습니다.

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

위의 상수는 **tx_port.h** 에서 정의되어 있으며, 각 이벤트에서 1씩 증가하는 '가짜' 타임스탬프를 만듭니다. 다음은 실제 타임스탬프 정의의 예시입니다.

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

위의 상수는 0x13000004 주소를 읽어서 얻은 32비트 타이머를 지정합니다. 대부분의 애플리케이션 관련 타임스탬프는 비슷한 방식으로 설정됩니다.

## <a name="exporting-the-trace-buffer"></a>추적 버퍼 내보내기

호스트의 TraceX에는 이진, Intel HEX 또는 Motorola S-레코드 파일 형식의 추적 버퍼가 필요합니다. 이를 수행하는 가장 쉬운 방법은 대상을 중지하고 디버거에 지시하여 사용자가 ***tx_trace_enable*** 함수에 제공한 메모리 영역을 호스트의 파일로 덤프하도록 하는 것입니다.

> [!WARNING]
>***추적 수집 코드 내에서 대상을 중지하지 않도록 주의하십시오. 대상을 중지하면 잘못된 추적 정보가 발생할 수 있습니다. ThreadX 내에서 프로그램이 중지되는 경우 추적 버퍼를 덤프하기 전에 추적 삽입 매크로를 한 단계씩 실행하는 것이 가장 좋습니다.***

> [!IMPORTANT]
> *부록 D는 다양한 개발 도구 내에서 추적 버퍼를 덤프하는 방법을 보여줍니다.*

## <a name="extended-event-trace-api"></a>확장 이벤트 추적 API

**TX_ENABLE_EVENT_TRACE** 가 정의된 ThreadX를 빌드하면 애플리케이션에서 사용할 수 있는 새 이벤트 추적 API는 다음과 같습니다.

- tx_trace_enable: *이벤트 추적 사용*
- tx_trace_event_filter: *지정된 이벤트 필터링*
- tx_trace_event_unfilter: *지정된 이벤트 필터링 안 함*
- tx_trace_disable: *이벤트 추적 사용 안 함*
- tx_trace_isr_enter_insert: *ISR 입력 추적 이벤트 삽입*
- tx_trace_isr_exit_insert: *ISR 종료 추적 이벤트 삽입*
- tx_trace_buffer_full_notify: *추적 버퍼 전체 애플리케이션 콜백 등록*
- tx_trace_user_event_insert: *사용자 이벤트 삽입*

### <a name="tx_trace_enable"></a>tx_trace_enable

이벤트 추적 사용

#### <a name="prototype"></a>프로토타입

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a>Description
이 서비스는 ThreadX 내의 이벤트 추적을 사용하도록 설정합니다. 애플리케이션에서 추적 버퍼와 ThreadX 개체의 최대 수를 제공합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.

#### <a name="input-parameters"></a>입력 매개 변수

- **trace_buffer_start**: 사용자가 제공한 추적 버퍼의 시작에 대한 포인터입니다.
- **trace_buffer_size**: 추적 버퍼에 대한 메모리의 총 바이트 수입니다. 추적 버퍼가 클수록 저장할 수 있는 항목이 더 많습니다.
- **registry_entries**: 추적 레지스트리에 유지할 애플리케이션 ThreadX 개체의 수입니다. 레지스트리는 개체 주소와 개체 이름의 상관 관계를 지정하는 데 사용됩니다. 이는 GUI 추적 분석 도구에 매우 유용합니다.

#### <a name="return-values"></a>반환 값

- **TX_SUCCESS** (0x00) 이벤트 추적을 사용하도록 설정했습니다.
- **TX_SIZE_ERROR** (0x05) 지정된 추적 버퍼 크기가 너무 작습니다. 추적 헤더, 개체 레지스트리 및 하나 이상의 추적 항목에 대해 충분히 커야 합니다.
- **TX_NOT_DONE** (0X20) 이미 이벤트 추적을 사용하도록 설정되었습니다.
- **TX_FEATURE_NOT_ENABLED** (0xFF) 추적을 사용하도록 설정된 상태에서 시스템이 컴파일되지 않았습니다.

#### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

#### <a name="example"></a>예제

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a>참고 항목

tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_event_filter"></a>tx_trace_event_filter

지정된 이벤트 필터링

#### <a name="prototype"></a>프로토타입

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a>Description

이 서비스는 지정된 이벤트가 활성 추적 버퍼에 삽입되지 않도록 필터링합니다. 기본적으로 *tx_trace_enable* 를 호출한 후에는 이벤트를 필터링하지 않습니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.

#### <a name="input-parameters"></a>입력 매개 변수

- **event_filter_bits**: 필터링할 이벤트에 해당하는 비트입니다. 적절한 상수를 OR 연산하면 여러 이벤트를 필터링할 수 있습니다. 이 변수에 대한 유효한 상수는 다음과 같이 정의됩니다.

```c
TX_TRACE_ALL_EVENTS                   0x000007FF
TX_TRACE_INTERNAL_EVENTS              0x00000001
TX_TRACE_BLOCK_POOL_EVENTS            0x00000002
TX_TRACE_BYTE_POOL_EVENTS             0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS           0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT      0x00000010
TX_TRACE_MUTEX_EVENTS                 0x00000020
TX_TRACE_QUEUE_EVENTS                 0x00000040
TX_TRACE_SEMAPHORE_EVENTS             0x00000080
TX_TRACE_THREAD_EVENTS                0x00000100
TX_TRACE_TIME_EVENTS                  0x00000200
TX_TRACE_TIMER_EVENTS                 0x00000400
FX_TRACE_ALL_EVENTS                   0x00007800
FX_TRACE_INTERNAL_EVENTS              0x00000800
FX_TRACE_MEDIA_EVENTS                 0x00001000
FX_TRACE_DIRECTORY_EVENTS             0x00002000
FX_TRACE_FILE_EVENTS                  0x00004000
NX_TRACE_ALL_EVENTS                   0x00FF8000
NX_TRACE_INTERNAL_EVENTS              0x00008000
NX_TRACE_ARP_EVENTS                   0x00010000
NX_TRACE_ICMP_EVENTS                  0x00020000
NX_TRACE_IGMP_EVENTS                  0x00040000
NX_TRACE_IP_EVENTS                    0x00080000
NX_TRACE_PACKET_EVENTS                0x00100000
NX_TRACE_RARP_EVENTS                  0x00200000
NX_TRACE_TCP_EVENTS                   0x00400000
NX_TRACE_UDP_EVENTS                   0x00800000
UX_TRACE_ALL_EVENTS                   0x7F000000
UX_TRACE_ERRORS                       0x01000000
UX_TRACE_HOST_STACK_EVENTS            0x02000000
UX_TRACE_DEVICE_STACK_EVENTS          0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS       0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS     0x10000000
UX_TRACE_HOST_CLASS_EVENTS            0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS          0x40000000
```

#### <a name="return-values"></a>반환 값

- **TX_SUCCESS** (0X00) 이벤트 필터링을 수행했습니다.
- **TX_FEATURE_NOT_ENABLED** (0xFF) 추적을 사용하도록 설정된 상태에서 시스템이 컴파일되지 않았습니다.

#### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

#### <a name="example"></a>예제

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a>참고 항목

tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_event_unfilter"></a>tx_trace_event_unfilter

지정된 이벤트 필터링 안 함

#### <a name="prototype"></a>프로토타입

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a>Description

이 서비스는 활성 추적 버퍼에 삽입되도록 지정된 이벤트를 필터링하지 않습니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.

#### <a name="input-parameters"></a>입력 매개 변수

- **event_unfilter_bits**: 필터링하지 않는 이벤트에 해당하는 비트입니다. 적절한 상수를 OR 연산하여 여러 이벤트를 필터링하지 않을 수 있습니다. 이 변수에 대한 유효한 상수는 다음과 같이 정의됩니다.

```c
TX_TRACE_ALL_EVENTS                  0x000007FF
TX_TRACE_INTERNAL_EVENTS             0x00000001
TX_TRACE_BLOCK_POOL_EVENTS           0x00000002
TX_TRACE_BYTE_POOL_EVENTS            0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS          0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT     0x00000010
TX_TRACE_MUTEX_EVENTS                0x00000020
TX_TRACE_QUEUE_EVENTS                0x00000040
TX_TRACE_SEMAPHORE_EVENTS            0x00000080
TX_TRACE_THREAD_EVENTS               0x00000100
TX_TRACE_TIME_EVENTS                 0x00000200
TX_TRACE_TIMER_EVENTS                0x00000400
FX_TRACE_ALL_EVENTS                  0x00007800
FX_TRACE_INTERNAL_EVENTS             0x00000800
FX_TRACE_MEDIA_EVENTS                0x00001000
FX_TRACE_DIRECTORY_EVENTS            0x00002000
FX_TRACE_FILE_EVENTS                 0x00004000
NX_TRACE_ALL_EVENTS                  0x00FF8000
NX_TRACE_INTERNAL_EVENTS             0x00008000
NX_TRACE_ARP_EVENTS                  0x00010000
NX_TRACE_ICMP_EVENTS                 0x00020000
NX_TRACE_IGMP_EVENTS                 0x00040000
NX_TRACE_IP_EVENTS                   0x00080000
NX_TRACE_PACKET_EVENTS               0x00100000
NX_TRACE_RARP_EVENTS                 0x00200000
NX_TRACE_TCP_EVENTS                  0x00400000
NX_TRACE_UDP_EVENTS                  0x00800000
UX_TRACE_ALL_EVENTS                  0x7F000000
UX_TRACE_ERRORS                      0x01000000
UX_TRACE_HOST_STACK_EVENTS           0x02000000
UX_TRACE_DEVICE_STACK_EVENTS         0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS      0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS    0x10000000
UX_TRACE_HOST_CLASS_EVENTS           0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS         0x40000000
```

#### <a name="return-values"></a>반환 값

- **TX_SUCCESS** (0X00) 이벤트 필터링을 수행하지 않았습니다.
- **TX_FEATURE_NOT_ENABLED** (0xFF) 추적을 사용하도록 설정된 상태에서 시스템이 컴파일되지 않았습니다.

#### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

#### <a name="example"></a>예제

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a>참고 항목

tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_disable"></a>tx_trace_disable

#### <a name="disable-event-tracing"></a>이벤트 추적 사용 안 함

#### <a name="prototype"></a>프로토타입

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a>Description

이 서비스는 ThreadX 내의 이벤트 추적을 사용하지 않도록 설정합니다. 이는 애플리케이션이 런타임 중에 현재 이벤트 추적 버퍼를 고정하고 외부에서 전송하려는 경우 유용할 수 있습니다. 사용하지 않도록 설정되면 **tx_trace_enable** 를 호출하여 추적을 다시 시작할 수 있습니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.

#### <a name="input-parameters"></a>입력 매개 변수

없음

#### <a name="return-values"></a>반환 값

- **TX_SUCCESS** (0x00) 이벤트 추적을 사용하지 않도록 설정했습니다.
- **TX_NOT_DONE** (0X20) 이벤트 추적을 사용하도록 설정되지 않았습니다.
- **TX_FEATURE_NOT_ENABLED** (0xFF) 추적을 사용하도록 설정된 상태에서 시스템이 컴파일되지 않았습니다.

#### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

#### <a name="example"></a>예제 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a>참고 항목

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_isr_enter_insert"></a>tx_trace_isr_enter_insert

#### <a name="insert-isr-enter-event"></a>ISR 입력 이벤트 삽입

#### <a name="prototype"></a>프로토타입

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a>Description

이 서비스는 이벤트 추적 버퍼에 ISR 입력 이벤트를 삽입합니다. ISR 처리가 시작될 때 애플리케이션에서 호출해야 합니다. 제공된 매개 변수는 애플리케이션에 대한 특정 ISR을 식별해야 합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.

#### <a name="input-parameters"></a>입력 매개 변수 
- **isr_id**: ISR을 식별하기 위한 애플리케이션 관련 값입니다.

#### <a name="return-values"></a>반환 값

**없음**

#### <a name="allowed-from"></a>허용된 원본 

ISR

#### <a name="example"></a>예제

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a>참고 항목

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_isr_exit_insert"></a>tx_trace_isr_exit_insert

#### <a name="insert-isr-exit-event"></a>ISR 종료 이벤트 삽입

#### <a name="prototype"></a>프로토타입

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a>Description

이 서비스는 이벤트 추적 버퍼에 ISR 항목 이벤트를 삽입합니다. ISR 처리가 시작될 때 애플리케이션에서 호출해야 합니다. 제공된 매개 변수는 애플리케이션에 대한 ISR을 식별해야 합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.

#### <a name="input-parameters"></a>입력 매개 변수 

- **isr_id**: ISR을 식별하기 위한 애플리케이션 관련 값입니다.

#### <a name="return-values"></a>반환 값

**없음**

#### <a name="allowed-from"></a>허용된 원본

ISR

#### <a name="example"></a>예제

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a>참고 항목

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_buffer_full_notify"></a>tx_trace_buffer_full_notify

#### <a name="register-trace-buffer-full-application-callback"></a>추적 버퍼 전체 애플리케이션 콜백 등록

#### <a name="prototype"></a>프로토타입

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a>Description

이 서비스는 추적 버퍼가 가득 찰 때 ThreadX에 의해 호출되는 애플리케이션 콜백 함수를 등록합니다. 그런 다음 애플리케이션에서 추적을 사용하지 않도록 설정하거나 새 추적 버퍼를 설정하도록 선택할 수 있습니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.

#### <a name="input-parameters"></a>입력 매개 변수

- **full_buffer_callback**: 추적 버퍼가 가득 차면 호출할 애플리케이션 함수입니다. NULL 값은 알림 콜백을 사용하지 않도록 설정합니다.

#### <a name="return-values"></a>반환 값

**없음**

#### <a name="allowed-from"></a>허용된 원본

ISR

#### <a name="example"></a>예제

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a>참고 항목

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert

### <a name="tx_trace_user_event_insert"></a>tx_trace_user_event_insert

#### <a name="insert-user-event"></a>사용자 이벤트 삽입

#### <a name="prototype"></a>프로토타입

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a>Description

이 서비스는 사용자 이벤트를 추적 버퍼에 삽입합니다. 사용자 이벤트 ID는 4096으로 정의된 상수 **TX_TRACE_USER_EVENT_START** 보다 커야 합니다. 최대 사용자 이벤트는 65535로 정의된 상수 **TX_TRACE_USER_EVENT_END** 에 의해 정의됩니다. 이 범위 내의 모든 이벤트는 애플리케이션에서 사용할 수 있습니다. 정보 필드는 애플리케이션마다 다릅니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.

#### <a name="input-parameters"></a>입력 매개 변수

- **event_id**: 애플리케이션 관련 이벤트 ID는 **TX_TRACE_USER_EVENT_START** 보다 크고 **TX_TRACE_USER_EVENT_END** 보다 작거나 같아야 합니다.
- **info_field_1**: 애플리케이션 관련 정보 필드입니다.
- **info_field_2**: 애플리케이션 관련 정보 필드입니다.
- **info_field_3**: 애플리케이션 관련 정보 필드입니다.
- **info_field_4**: 애플리케이션 관련 정보 필드입니다.

#### <a name="return-values"></a>반환 값
- **TX_SUCCESS** (0x00) 사용자 이벤트 삽입을 수행했습니다.
- **TX_NOT_DONE** (0X20) 이벤트 추적을 사용하도록 설정되지 않았습니다.
- **TX_FEATURE_NOT_ENABLED** (0xFF) 추적이 설정된 상태에서 시스템이 컴파일되지 않았습니다.

#### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

#### <a name="example"></a>예제

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a>참고 항목

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify