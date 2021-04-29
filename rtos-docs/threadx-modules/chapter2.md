---
title: 2장 - 모듈 요구 사항
description: 이 문서에서는 ThreadX 모듈을 빌드하는 데 필요한 요구 사항에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 32288d78ceffb74ab088a1d720dbac657f6d3ed4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810309"
---
# <a name="chapter-2---module-requirements"></a>2장 - 모듈 요구 사항

ThreadX 모듈에는 모듈의 기본 특성을 정의하는 프리앰블이 있습니다. 프리앰블 다음에는 모듈의 명령어 영역이 표시됩니다. 모듈은 현재 위치에서 실행될 수도 있고 실행 전 모듈 관리자를 통해 모듈 메모리 영역으로 로드될 수도 있습니다. 유일한 요구 사항은 프리앰블이 항상 모듈의 첫 번째 주소에 배치되어야 한다는 것입니다. 그림 2는 기본 모듈 레이아웃을 보여 줍니다.

| 모듈 레이아웃 |
|:---:|
| \[모듈 프리앰블\]         |
| \[모듈 명령어 영역\] |
| \[모듈 RAM 영역\]         |

**그림 2** - 모듈 레이아웃

> [!NOTE]
> 모듈은 적절한 위치 독립적 코드 및 데이터 컴파일러/링커 옵션을 사용하여 빌드되어야 합니다. 이렇게 하면 어떤 메모리 영역에서도 모듈을 실행할 수 있습니다.

모듈 스레드를 만들 때 스레드가 메모리 보호 커널에 있는 경우 사용할 두 번째 스택 공간이 할당됩니다. 스레드의 커널 스택 공간 크기는 **_txm_module_port.h_ *_에서 **TXM_MODULE_KERNEL_STACK_SIZE** 를 사용하여 사용자가 구성할 수 있습니다. 이렇게 하면 _* _tx_thread_create_** 를 호출할 때 사용자가 지정한 스택만이 모듈에서 사용되므로 모듈 스레드를 만들 때 더 작은 스택 크기를 사용할 수 있습니다.

> [!NOTE]
> 모듈 스레드 스택의 맨 위에는 스레드 진입 정보 구조(**TXM_MODULE_THREAD_ENTRY_INFO**)가 있으므로 사용 가능한 스택 크기가 이 구조의 크기만큼 줄어듭니다. 모듈에서 스레드를 만들 때 스택 크기를 적어도 이 구조의 크기만큼 늘리세요.

ThreadX 모듈을 만들고 빌드하는 데 필요한 단계는 다음과 같습니다. 각 단계는 아래에서 자세히 설명합니다.

1. 모듈의 모든 C 파일에는 **_txm_module.h_** 포함 전에 #define **TXM_MODULE** 이 추가되어야 합니다. 이 작업은 원본 파일을 컴파일하는 과정에서 또는 프로젝트 설정의 일부로 수행할 수 있습니다. 이렇게 하면 상주 모듈 관리자에서 디스패치 함수를 호출하는 API의 모듈별 버전에 ThreadX API 호출을 다시 매핑하여 실제 API 함수를 호출합니다.
2. 각 모듈에서는 모듈 특성 및 리소스 요구 사항이 정의된 프리앰블이 모듈의 첫 번째 명령어 영역 주소에 있어야 합니다.
3. 각 모듈은 모듈 명령어 영역의 시작 부분에 있는 프리앰블을 연결해야 합니다.
4. 각 모듈은 ThreadX 조작에 사용되는 모듈별 함수가 포함된 모듈 라이브러리(***txm.a***)에 대해 연결해야 합니다.

## <a name="module-sources"></a>모듈 원본

ThreadX 모듈에는 모듈 소스 코드를 사용하여 직접 연결되고 배치되도록 설계된 고유한 원본 파일 세트가 있습니다. 이러한 파일은 별도의 모듈과 상주 모듈 관리자 간에 브리지를 제공합니다. 모듈 파일은 다음과 같습니다.

| 파일 이름 | 콘텐츠 |
|---|---|
| **txm_module.h** | 모듈 정보가 정의된 파일을 포함합니다. |
| **txm_module_port.h** | 포트별 모듈 정보가 정의된 파일을 포함합니다. |
| **txm_module_user.h** | 사용자가 사용자 지정할 수 있는 값을 정의합니다. |
| **txm_module_initialize.s [1][3]** | 모듈을 시작하는 내장 함수를 호출합니다. |
| **txm_module_preamble.\{s/S/68\}** | 모듈 프리앰블 어셈블리 파일입니다. 이 파일은 다양한 모듈별 특성을 정의하고 모듈 애플리케이션 코드와 연결됩니다. |
| **txm_module_application_request.c [1]** | 모듈 애플리케이션 요청 함수는 애플리케이션별 요청을 상주 코드로 송신합니다. |
| **txm_module_callback_request_thread_entry.c&nbsp;[1]** | 타이머 및 알림 콜백을 비롯하여 모듈에서 요청하는 콜백을 처리해야 하는 모듈 콜백 스레드입니다. |
| **txm_*.c [1][2]** | 표준 ThreadX API 서비스로, 커널 디스패처를 호출합니다.
| **txm_module_object_allocate.c [1]** | 관리자 메모리 풀에 배치된 모듈 개체용 메모리를 할당하는 모듈 함수입니다. |
| **txm_module_object_deallocate.c [1]** | 관리자 메모리 풀에 배치된 모듈 개체용 메모리를 할당 취소하는 모듈 함수입니다. |
| **txm_module_object_pointer_get.c [1]** | 시스템 개체에 대한 포인터를 검색하는 모듈 함수입니다. |
| **txm_module_object_pointer_get_extended.c [1]** | 시스템 개체에 대한 포인터인 이름 길이 보호를 검색하는 모듈 함수입니다. |
| **txm_module_thread_shell_entry.c [1]** | 모듈 스레드 진입 함수입니다. |
| **txm_module_thread_system_suspend.c [1]** | 스레드를 일시 중단하는 모듈 함수입니다. |

**[1]** 라이브러리 **_txm.a_** 에 배치됩니다.

**[2]** 이러한 파일은 ThreadX API 파일과 이름이 동일하며, **tx_** 접두사가 아닌 **txm_** 접두사를 사용합니다.

**[3]** **txm_module_initialize.s** 파일은 ARM 도구를 사용하는 포트에만 사용됩니다.

## <a name="module-preamble"></a>모듈 프리앰블

모듈 프리앰블은 모듈 특성 및 리소스를 정의합니다. 초기 스레드 진입 함수, 스레드와 연결된 초기 메모리 영역 등의 정보가 프리앰블에 정의됩니다. 포트별 프리앰블 예는 [부록](appendix.md)에 있습니다. 그림 3은 제네릭 대상에 대한 ThreadX 모듈 프리앰블 예를 보여 줍니다. *로 시작하는 줄은 일반적으로 애플리케이션에서 수정하는 값입니다.

```c
    AREA Init, CODE, READONLY

    /* Define public symbols. */
    EXPORT __txm_module_preamble

    /* Define application-specific start/stop entry points for the module. */
    IMPORT demo_module_start

    /* Define common external refrences. */
    IMPORT _txm_module_thread_shell_entry
    IMPORT _txm_module_callback_request_thread_entry
    IMPORT |Image$$ER_RO$$Length|
    IMPORT |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                  ; Module ID
    DCD     0x6                                         ; Module Major Version
    DCD     0x1                                         ; Module Minor Version
    DCD     32                                          ; Module Preamble Size in 32-bit words
*   DCD     0x12345678                                  ; Module ID (application defined)
*   DCD     0x01000001                                  ; Module Properties where:
                                                        ; Bits 31-24: Compiler ID
                                                        ;   0 -> IAR
                                                        ;   1 -> ARM
                                                        ;   2 -> GNU
                                                        ;   Bits 23-1: Reserved
                                                        ;   Bit 0: 0 -> Privileged mode execution (no MMU protection)
                                                        ;          1 -> User mode execution (MMU protection)
    DCD     _txm_module_thread_shell_entry - . + .      ; Module Shell Entry Point
*   DCD     demo_module_start - . + .                   ; Module Start Thread Entry Point
    DCD     0                                           ; Module Stop Thread Entry Point
*   DCD     1                                           ; Module Start/Stop Thread Priority
*   DCD     2048                                        ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD     1                                            ; Module Callback Thread Priority
    DCD     2048                                         ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length|                       ; Module Code Size
    DCD     |Image$$ER_RW$$Length|                       ; Module Data Size
    DCD     0                                            ; Reserved 0
    DCD     0                                            ; Reserved 1
    DCD     0                                            ; Reserved 2
    DCD     0                                            ; Reserved 3
    DCD     0                                            ; Reserved 4
    DCD     0                                            ; Reserved 5
    DCD     0                                            ; Reserved 6
    DCD     0                                            ; Reserved 7
    DCD     0                                            ; Reserved 8
    DCD     0                                            ; Reserved 9
    DCD     0                                            ; Reserved 10
    DCD     0                                            ; Reserved 11
    DCD     0                                            ; Reserved 12
    DCD     0                                            ; Reserved 13
    DCD     0                                            ; Reserved 14
    DCD     0                                            ; Reserved 15
    END
```

**그림 3**

대부분의 경우 개발자는 모듈의 시작 스레드(오프셋 0x1C), 모듈 ID(오프셋 0x10), 시작/중지 스레드 우선 순위(오프셋 0x24), 시작/중지 스레드 스택 크기(오프셋 0x28)를 정의하기만 하면 됩니다. 위의 데모에서는 모듈의 시작 스레드가 ***demo_module_start** _, 모듈 ID가 _*_0x12345678_*_, 시작 스레드의 우선 순위가 _*_1_*_, 스택 크기가 _ *_2048_**바이트로 설정되었습니다.

일부 애플리케이션은 모듈 관리자가 모듈을 중지할 때 실행되는 중지 스레드를 선택적으로 정의할 수 있습니다. 또한 일부 애플리케이션은 다음과 같이 정의된 모듈 속성 필드를 활용할 수 있습니다.

## <a name="module-properties-bit-map"></a>모듈 속성 비트맵

아래 테이블에서는 속성 비트맵의 예를 보여 줍니다. 포트별 속성 비트맵은 [부록](appendix.md)에 있습니다.

| bit | 값 | 의미 |
|---|---|---|
| 0 | 0<br />1 | 권한 있는 모드 실행<br />사용자 모드 실행 |
| 1 | 0<br />1 | MPU 보호 없음<br />MPU 보호(사용자 모드가 선택되어 있어야 함) |
| 2 | 0<br />1 | 공유/외부 메모리 액세스 사용 안 함<br />공유/외부 메모리 액세스 사용 |
| [23-3] | 0 | 예약됨
| [31-24] | <br />0x01<br />0x02<br />0x03 | **컴파일러 ID**<br />IAR<br />ARM<br />GNU |


## <a name="module-linker-control-file"></a>모듈 링커 제어 파일

모듈을 빌드하는 경우 다른 모든 코드 섹션 앞에 모듈 프리앰블을 배치해야 합니다. 모듈은 위치 독립적 코드 및 데이터 섹션을 사용하여 빌드해야 합니다. 포트별 링커 파일 예는 [부록](appendix.md)에 있습니다.

## <a name="module-threadx-library"></a>모듈 ThreadX 라이브러리

각 모듈은 모듈 중심의 특수 ThreadX 라이브러리에 대해 연결해야 합니다. 이 라이브러리는 상주 코드의 ThreadX 서비스에 대한 액세스를 제공합니다. 대부분의 액세스는 ***txm_\*.c*** 파일을 통해 수행됩니다. 다음은 ThreadX API 함수 **_tx_thread_relinquish_* _( _*_ \_txm_thread_relinquish.c\****에 있음)에 대한 모듈 액세스 호출의 예입니다.

```c
(_txm_module_kernel_call_dispatcher)(TXM_THREAD_RELINQUISH_CALL, 0, 0, 0);
```

이 예에서는 모듈 관리자가 제공하는 함수 포인터를 사용하여 ***tx_thread_relinquish*** 서비스와 연결된 ID로 모듈 관리자 디스패치 함수를 호출합니다. 이 서비스는 매개 변수를 사용하지 않습니다.

## <a name="module-example"></a>모듈 예

다음은 모듈 형식의 표준 ThreadX 데모에 대한 예입니다. 표준 ThreadX 데모와 모듈 데모의 주요 차이점은 다음과 같습니다.

1. ***tx_api.h** _를 _ *_txm_module.h_**로 바꿉니다.
2. **_txm_module.h_** 앞에 **#define TXM_MODULE** 을 추가합니다.
3. ***main** _ 및 _ *tx_application_define**을 **_demo_module_start_** 로 바꿉니다.
4. 개체 자체가 아닌 ThreadX 개체를 가리키는 ‘포인터’를 선언합니다.

```c
/* Specify that this is a module! */
#define TXM_MODULE

/* Include the ThreadX module header. */
#include "txm_module.h"

/* Define constants. */
#define DEMO_STACK_SIZE         1024
#define DEMO_BYTE_POOL_SIZE     9120
#define DEMO_BLOCK_POOL_SIZE    100
#define DEMO_QUEUE_SIZE         100

/* Define the pool space in the bss section of the module. ULONG is used to
   get word alignment. */
   
ULONG                   demo_module_pool_space[DEMO_BYTE_POOL_SIZE / 4];

/* Define the ThreadX object control block pointers. */

TX_THREAD               *thread_0;
TX_THREAD               *thread_1;
TX_THREAD               *thread_2;
TX_THREAD               *thread_3;
TX_THREAD               *thread_4;
TX_THREAD               *thread_5;
TX_THREAD               *thread_6;
TX_THREAD               *thread_7;
TX_QUEUE                *queue_0;
TX_SEMAPHORE            *semaphore_0;
TX_MUTEX                *mutex_0;
TX_EVENT_FLAGS_GROUP    *event_flags_0;
TX_BYTE_POOL            *byte_pool_0;
TX_BLOCK_POOL           *block_pool_0;


/* Define the counters used in the demo application. */
ULONG       thread_0_counter;
ULONG       thread_1_counter;
ULONG       thread_1_messages_sent;
ULONG       thread_2_counter;
ULONG       thread_2_messages_received;
ULONG       thread_3_counter;
ULONG       thread_4_counter;
ULONG       thread_5_counter;
ULONG       thread_6_counter;
ULONG       thread_7_counter;
ULONG       semaphore_0_puts;
ULONG       event_0_sets;
ULONG       queue_0_sends;

/* Define thread prototypes. */

void    thread_0_entry(ULONG thread_input);
void    thread_1_entry(ULONG thread_input);
void    thread_2_entry(ULONG thread_input);
void    thread_3_and_4_entry(ULONG thread_input);
void    thread_5_entry(ULONG thread_input);
void    thread_6_and_7_entry(ULONG thread_input);

/* Define notify functions. */

void semaphore_0_notify(TX_SEMAPHORE *semaphore_ptr)
{
    if (semaphore_ptr == semaphore_0)
        semaphore_0_puts++;
}


void event_0_notify(TX_EVENT_FLAGS_GROUP *event_flag_group_ptr)
{
    if (event_flag_group_ptr == event_flags_0)
        event_0_sets++;
}


void queue_0_notify(TX_QUEUE *queue_ptr)
{
    if (queue_ptr == queue_0)
        queue_0_sends++;
}

/* Define the module start function. */
void demo_module_start(ULONG id)
{
    CHAR *pointer;

    /* Allocate all the objects. In memory protection mode,
        modules cannot allocate control blocks within their
        own memory area so they cannot corrupt the resident
        portion of ThreadX by corrupting the control block(s). */
    txm_module_object_allocate(&thread_0, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_1, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_2, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_3, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_4, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_5, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_6, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_7, sizeof(TX_THREAD));
    txm_module_object_allocate(&queue_0, sizeof(TX_QUEUE));
    txm_module_object_allocate(&semaphore_0, sizeof(TX_SEMAPHORE));
    txm_module_object_allocate(&mutex_0, sizeof(TX_MUTEX));
    txm_module_object_allocate(&event_flags_0, sizeof(TX_EVENT_FLAGS_GROUP));
    txm_module_object_allocate(&byte_pool_0, sizeof(TX_BYTE_POOL));
    txm_module_object_allocate(&block_pool_0, sizeof(TX_BLOCK_POOL));

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(byte_pool_0, "module byte pool 0",
        demo_module_pool_space, DEMO_BYTE_POOL_SIZE);

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 0. */
    tx_thread_create(thread_0, "module thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through
        a ThreadX message queue. It is also interesting to note that
        these threads have a time slice. */
    tx_thread_create(thread_1, "module thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack and create thread 2. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_2, "module thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX
        counting semaphore. An interesting thing here is that both threads
        share the same instruction area. */
    tx_thread_create(thread_3, "module thread 3",
        thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 4. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_4, "module thread 4",
        thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag which
        will be set by thread 0. */
    tx_thread_create(thread_5, "module thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(thread_6, "module thread 6",
        thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 7. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_7, "module thread 7",
        thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(queue_0, "module queue 0", TX_1_ULONG, pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Register queue send callback. */
    tx_queue_send_notify(queue_0, queue_0_notify);

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(semaphore_0, "module semaphore 0", 1);

    /* Register semaphore put callback. */
    tx_semaphore_put_notify(semaphore_0, semaphore_0_notify);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(event_flags_0, "module event flags 0");

    /* Register event flag set callback. */
    tx_event_flags_set_notify(event_flags_0, event_0_notify);

    /* Create the mutex used by thread 6 and 7 without priority
        inheritance. */
    tx_mutex_create(mutex_0, "module mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool. */
    tx_block_pool_create(block_pool_0, "module block pool 0",
        sizeof(ULONG), pointer, DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block. */
    tx_block_allocate(block_pool_0, (VOID **) &pointer,
        TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);

}

/* Define all the threads. */

void thread_0_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sits in while-forever-sleep loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_0_counter++;

        /* Sleep for 10 ticks. */
        tx_thread_sleep(10);

        /* Set event flag 0 to wake up thread 5. */
        status = tx_event_flags_set(event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_1_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sends messages to a queue shared by
       thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(queue_0, &thread_1_messages_sent,
            TX_WAIT_FOREVER);

        /* Check completion status. */
        if (status != TX_SUCCESS)
            break;

        /* Increment the message sent. */
        thread_1_messages_sent++;
    }
}

void thread_2_entry(ULONG thread_input)
{
    ULONG received_message;
    UINT status;

    /* This thread retrieves messages placed on the queue by thread 1. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_2_counter++;

        /* Retrieve a message from the queue. */
        status = tx_queue_receive(queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what
           we expected. */
        if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
            break;

        /* Otherwise, all is okay. Increment the received message count. */
        thread_2_messages_received++;
    }
}

void thread_3_and_4_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 3 and thread 4. As the loop
       below shows, these function compete for ownership of semaphore_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 3)
            thread_3_counter++;
        else
            thread_4_counter++;

        /* Get the semaphore with suspension. */
        status = tx_semaphore_get(semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(semaphore_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_5_entry(ULONG thread_input)
{
    UINT status;
    ULONG actual_flags;

    /* This thread simply waits for an event in a forever loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_5_counter++;

        /* Wait for event flag 0. */
        status = tx_event_flags_get(event_flags_0, 0x1, TX_OR_CLEAR,
                                        &actual_flags, TX_WAIT_FOREVER);

        /* Check status. */
        if ((status != TX_SUCCESS) || (actual_flags != 0x1))
            break;
    }
}

void thread_6_and_7_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 6 and thread 7. As the loop
       below shows, these function compete for ownership of mutex_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 6)
            thread_6_counter++;
        else
            thread_7_counter++;

        /* Get the mutex with suspension. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows that an
           owning thread may retrieve the mutex it owns multiple times. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually release ownership
           since it was obtained twice. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```

## <a name="building-modules"></a>모듈 빌드

모듈 빌드는 사용하는 도구 체인에 따라 달라집니다. 포트별 예는 [부록](appendix.md)을 참조하세요. 모든 포트에 공통되는 작업은 다음과 같습니다.

- 모듈 라이브러리 빌드
- 모듈 애플리케이션 빌드

각 모듈에는 **txm_module_preamble**(해당 모듈용으로 특별히 설정됨) 및 모듈 라이브러리(예: **_txm.a_**)가 있어야 합니다.
