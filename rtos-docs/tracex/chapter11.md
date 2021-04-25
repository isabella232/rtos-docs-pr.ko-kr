---
title: 챕터 11 - 이벤트 추적 버퍼의 형식
description: ThreadX는 모든 Azure RTOS ThreadX 서비스, 스레드 상태 변경 및 사용자 정의 이벤트에 대한 기본 제공 이벤트 추적 지원을 제공합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: d11b827558e9c96df44f462329b7807a500a64a4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812391"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a>챕터 11 - 이벤트 추적 버퍼의 형식

Azure RTOS ThreadX는 모든 ThreadX 서비스, 스레드 상태 변경 및 사용자 정의 이벤트에 대한 기본 제공 이벤트 추적 지원을 제공합니다. 이벤트 추적을 사용하려면 **TX_ENABLE_EVENT_TRACE** 가 정의된 Threadx, Netx 및 FileX 라이브러리를 간단하게 빌드하고 **_tx_trace_enable_** 함수를 호출하여 추적을 사용하도록 설정하면 됩니다. 이 챕터에서는 해당 프로세스에 대해 설명합니다.

## <a name="event-trace-format"></a>이벤트 추적 형식

ThreadX 이벤트 추적 버퍼의 형식은 컨트롤 헤더, 개체 레지스트리 및 추적 항목의 세 가지 섹션으로 구분 됩니다. 다음은 ThreadX 이벤트 추적 버퍼의 일반 레이아웃을 설명합니다.

**컨트롤 헤더**

**개체 레지스트리 항목 0**

**…**

**개체 등록 항목 "n"**

**이벤트 추적 항목 0**

**…**

**이벤트 추적 항목 "n"**

### <a name="event-trace-control-header"></a>이벤트 추적 컨트롤 헤더

컨트롤 헤더는 이벤트 추적 버퍼의 정확한 레이아웃을 정의합니다. 여기에는 등록할 수 있는 ThreadX 개체 수뿐만 아니라 기록될 수 있는 이벤트의 수가 포함됩니다. 또한 컨트롤 헤더는 추적 버퍼의 각 요소가 상주하는 위치를 정의합니다. 다음 데이터 구조는 컨트롤 헤더를 정의합니다.

```c
typedef struct TX_TRACE_CONTROL_HEADER_STRUCT
{
    ULONG    tx_trace_control_header_id;
    ULONG    tx_trace_control_header_timer_valid_mask;
    ULONG    tx_trace_control_header_trace_base_address;
    ULONG    tx_trace_control_header_object_registry_start_pointer;
    USHORT   tx_trace_control_header_reserved1;
    USHORT   tx_trace_control_header_object_registry_name_size;
    ULONG    tx_trace_control_header_object_registry_end_pointer;
    ULONG    tx_trace_control_header_buffer_start_pointer;
    ULONG    tx_trace_control_header_buffer_end_pointer;
    ULONG    tx_trace_control_header_buffer_current_pointer;
    ULONG    tx_trace_control_header_reserved2;
    ULONG    tx_trace_control_header_reserved3;
    ULONG    tx_trace_control_header_reserved4;
} TX_TRACE_CONTROL_HEADER;
```

### <a name="control-header-id"></a>컨트롤 헤더 ID

컨트롤 헤더 ID는 ASCII 문자 ***TXTB*** 에 해당하는 32 비트 16진수 값(0x54585442)으로 구성됩니다. 이 값은 32비트의 부호 없는 변수로 작성되므로, 이벤트 추적 버퍼의 엔디언을 검색하는 데 사용할 수도 있습니다. 예를 들어 처음 네 개의 메모리에 있는 값이 0x54, 0x58, 0x54, 0x42인 경우 이벤트 추적 버퍼는 big endian 형식으로 작성된 것입니다. 그렇지 않으면 이벤트 추적 버퍼가 little endian 형식으로 작성된 것입니다.

### <a name="timer-valid-mask"></a>타이머 유효 마스크

타이머 유효 마스크는 실제 이벤트 추적 항목에 유효한 타임스탬프의 비트 수를 정의합니다. 예를 들어 타임스탬프 원본이 16비트인 경우, 이 필드의 값은 0xFFFF여야 합니다. 32비트 타임스탬프 원본의 값은 0xFFFFFFFF입니다. 이 값은 _*_tx_port.h_**의 ***TX_TRACE_TIME_MASK** _ 상수에 의해 정의됩니다.

### <a name="trace-base-address"></a>추적 기준 주소

추적 버퍼 기준 주소는 애플리케이션이 ***tx_trace_enable*** 호출에서 추적 버퍼의 시작으로 지정한 주소입니다. 이 주소는 분석 도구를 사용하여 버퍼의 다양한 요소에 대한 상대 버퍼 오프셋을 유도하는 용도로만 유지 관리됩니다. 예를 들어 추적 버퍼에서 현재 이벤트의 상대 버퍼 오프셋은 현재 이벤트 주소에서 간단하게 빼기를 사용하여 기준 주소를 계산합니다.

### <a name="registry-start-and-end-pointers"></a>레지스트리 시작 및 끝 포인터

레지스트리 시작 포인터는 첫 번째 개체 레지스트리 항목의 주소를 가리키며, 레지스트리 끝 포인터는 마지막 등록 항목의 다음 주소 im../mediately를 가리킵니다. 이러한 값은 *tx_trace_enable* 을 처리하는 동안 설정되며 추적 기간 동안 변경되지 않습니다.

### <a name="registry-name-size"></a>레지스트리 이름 크기

레지스트리 이름 크기는 레지스트리 항목의 각 개체 이름에 대한 최대 크기(바이트)를 정의하며 ***TX_TRACE_OBJECT_REGISTRY_NAME** _ 기호로 정의됩니다. 기본값은 32이며 _*_tx_trace.h_*_ 에 정의됩니다. 개체 이름은 개체가 생성될 때 애플리케이션에서 지정하는 이름에 해당합니다. 예를 들어 스레드의 개체 레지스트리 이름은 애플리케이션이 _*_tx_thread_create_** 호출에 제공한 이름입니다.

### <a name="buffer-start-and-end-pointers"></a>버퍼 시작 및 끝 포인터

이벤트 추적 버퍼 시작 포인터는 첫 번째 추적 항목의 주소를 가리키며, 레지스트리 끝 포인터는 마지막 추적 항목의 다음 주소 im../mediately를 가리킵니다. 이러한 값은 ***tx_trace_enable</*** 을 처리하는 동안 설정되며 추적 기간 동안 변경되지 않습니다.

### <a name="current-buffer-pointer"></a>현재 버퍼 포인터

이벤트 추적 버퍼의 현재 포인터는 가장 오래된 추적 항목의 주소를 가리킵니다. 추적 항목은 순환 목록으로 유지 관리되므로, 현재 버퍼 포인터는 작성할 다음 추적 항목을 나타냅니다. |

## <a name="event-trace-object-registry"></a>이벤트 추적 개체 레지스트리

이벤트 추적 개체 레지스트리는 애플리케이션에서 만든 개체에 해당하는 ***n** _ 개체 레지스트리 항목을 포함합니다. 개체 레지스트리의 주요 목적은 외부 분석 도구를 사용하여 실제 개체 이름과 추적 버퍼 항목의 개체 주소를 상호 연결하는 것입니다. 레지스트리 항목의 수는 _ *_tx_trace_enable_** 호출에서 애플리케이션에 의해 지정됩니다.

각 개체 등록 항목에는 애플리케이션에서 이전에 만든 특정 ThreadX 개체에 대한 정보가 포함됩니다. 다음 데이터 구조는 각 개체 레지스트리 항목을 정의합니다.

```c
typedef struct TX_TRACE_OBJECT_REGISTRY_ENTRY_STRUCT
{
    UCHAR    tx_trace_object_registry_entry_object_available**;
    UCHAR    tx_trace_object_registry_entry_object_type**;
    UCHAR    tx_trace_object_registry_entry_object_reserved1;
    UCHAR    tx_trace_object_registry_entry_object_reserved2;
    ULONG    tx_trace_thread_registry_entry_object_pointer;
    ULONG    tx_trace_object_registry_entry_object_parameter_1;
    ULONG    tx_trace_object_registry_entry_object_parameter_2;
    UCHAR    tx_trace_thread_registry_entry_object_name[TX_TRACE_OBJECT_REGISTRY_NAME];

} TX_TRACE_OBJECT_REGISTRY_ENTRY;
```

### <a name="object-available-flag"></a>개체 사용 가능 플래그

개체 레지스트리 항목을 사용할 수 있는 경우 개체 사용 가능 플래그가 1로 설정됩니다. 값이 1이 아닌 경우에는 개체 레지스트리 항목을 사용할 수 없습니다. 항목을 사용할 수 있는 경우에도 유효한 정보를 계속 포함할 수 있습니다.

### <a name="object-entry-type"></a>개체 항목 유형

개체 항목 유형은 이 항목의 개체 유형을 식별합니다. 다음은 유효한 개체 유형 목록입니다.

| **값** | **개체 형식** |
|---------- | --------------- |
| 0         | 유효하지 않음       |
| 1         | 스레드          |
| 2         | 타이머 |
| 3         | 큐 |
| 4         | 세마포 |
| 5         | Mutex |
| 6         | 이벤트 플래그 그룹 |
| 7         | 블록 풀 |
| 8         | 바이트 풀 |
| 9         | ../media |
| 10        | 파일 |
| 11        | IP |
| 12        | 패킷 풀 |
| 13        | TCP 소켓 |
| 14        | UDP 소켓 |
| 15-20     | 예약됨 |  
| 21        | USB 호스트 스택 디바이스 |
| 22        | USB 호스트 스택 인터페이스 |
| 23        | USB 호스트 엔드포인트 |
| 24        | USB 호스트 클래스 |
| 25        | USB 디바이스 |
| 26        | USB 디바이스 인터페이스 |
| 27        | USB 디바이스 엔드포인트 |
| 28        | USB 디바이스 클래스 |

### <a name="object-pointer"></a>개체 포인터

개체 포인터는 ThreadX API를 사용하여 개체에 액세스하는 데 사용되는 개체 주소를 지정합니다.

### <a name="object-reserved-fields"></a>개체 예약 필드

스레드 이외의 모든 개체의 경우, 이러한 예약된 필드는 0이어야 합니다. 스레드의 경우, 레지스트리에 입력될 때 스레드의 우선 순위는 이러한 두 개의 예약된 필드에 배치됩니다.

### <a name="object-parameters"></a>개체 매개 변수

개체 매개 변수는 개체에 대한 추가 정보를 포함합니다. 다음은 각 ThreadX 개체에 대한 추가 정보를 설명합니다.

| **개체 형식**        | **매개 변수 1**  | **매개 변수 2** |
|----------------------- | ---------------- | --------------- |
| 스레드                 | 스택 시작      | 스택 크기 |
| 타이머                  | 초기 틱 | 틱 다시 예약 |
| 큐                  | 큐 크기 | 메시지 크기 |
| 세마포              | 초기 인스턴스 | - |
| Mutex                  | 상속 플래그 | - |
| 이벤트 플래그 그룹      | - | - |
| 블록 풀             | 총 블록 | 블록 크기 |
| 바이트 풀              | 총 바이트 | - |
| ../media                  | Fat 캐시 크기 | 섹터 캐시 크기 |
| 파일                   | - | - |
| IP                     | 스택 시작 | 스택 크기 |
| 패킷 풀            | 패킷 크기 | 패킷 수 |
| TCP 소켓             | IP 주소 | 창 크기 |
| UDP 소켓             | IP 주소 | RX 큐 최대값 |

### <a name="object-name"></a>개체 이름

개체 이름에는 ThreadX 개체의 이름이 포함됩니다. 이 이름은 개체가 생성될 때 ThreadX에 제공되는 이름입니다. 기본적으로 개체 이름의 최대 크기는 32자입니다. 32자를 초과하는 실제 이름은 일부가 잘립니다.

## <a name="event-trace-entries"></a>이벤트 추적 항목

이벤트 추적 항목은 이벤트 추적 버퍼의 하단에 있습니다. 항목은 현재 항목 포인터가 가장 오래된 항목을 가리키는 순환 목록으로 유지 관리됩니다. 목록의 항목 수는 ***tx_trace_enable*** 호출로 계산됩니다.

각 개체 등록 항목에는 특정 ThreadX 추적 이벤트에 대한 정보가 포함됩니다. 다음 데이터 구조는 각 추적 이벤트 항목을 정의합니다.

```c
typedef struct TX_TRACE_BUFFER_ENTRY_STRUCT
{
    ULONG     tx_trace_buffer_entry_thread_pointer;
    ULONG     tx_trace_buffer_entry_thread_priority;
    ULONG     tx_trace_buffer_entry_event_id;
    ULONG     tx_trace_buffer_entry_time_stamp;
    ULONG     tx_trace_buffer_entry_information_field_1;
    ULONG     tx_trace_buffer_entry_information_field_2;
    ULONG     tx_trace_buffer_entry_information_field_3;
    ULONG     tx_trace_buffer_entry_information_field_4;
} TX_TRACE_BUFFER_ENTRY;
```

### <a name="thread-pointer"></a>스레드 포인터

스레드 포인터는 이 이벤트가 발생했을 때 실행되는 스레드의 주소를 포함합니다. 초기화 중에 이벤트가 발생한 경우(실행 중인 스레드 없음) 이 포인터의 값은 0xF0F0F0F0입니다. ISR(인터럽트 서비스 루틴) 중에 이벤트가 발생한 경우 이 포인터의 값은 0xFFFFFFFF입니다. 항목을 아직 사용하지 않은 경우 이 포인터의 값은 0입니다.

### <a name="thread-priority"></a>스레드 우선 순위

스레드 우선 순위 필드에는 이 이벤트가 발생했을 때 실행 중이던 스레드의 우선 순위 및 선점 임계값이 포함됩니다. 인터럽트 컨텍스트가 있는 경우(스레드 포인터는 0xFFFFFFFF) 이 필드의 값은 우선 순위가 아닌, 이벤트 시점의 ***_tx_thread_current_ptr*** 값입니다. 그렇지 않은 경우, 이 필드의 값은 0입니다.

### <a name="event-id"></a>이벤트 ID

이벤트 ID는 발생한 이벤트를 지정합니다. 유효한 ThreadX 추적 이벤트 ID의 범위는 1~1024입니다. 1025 이상으로 시작되는 값은 사용자별 이벤트용으로 예약되어 있습니다. ThreadX 이벤트ID의 전체 정의는 ***tx_trace.h*** 파일을 참조하세요.</td>

### <a name="information-fields-1-4"></a>정보 필드(1~4)

정보 필드는 특정 이벤트에 대한 추가 정보를 포함합니다. 정의된 각 ThreadX 이벤트 ID에 대한 정보 필드의 전체 설명은 ***tx_trace.h*** 파일을 참조하세요.