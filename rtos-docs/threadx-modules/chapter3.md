---
title: 3장 - 모듈 관리자 요구 사항
description: 이 문서에서는 ThreadX 모듈 관리자 빌드에 필요한 단계를 설명합니다.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6c4d0993284c8e0b8264020d721ac12bdfe8117df4480fb54ee4d5b20a1f677e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799186"
---
# <a name="chapter-3---module-manager-requirements"></a>3장 - 모듈 관리자 요구 사항

ThreadX 모듈 관리자는 ThreadX RTOS와 함께 애플리케이션의 상주 부분에 위치합니다. 모듈 시작과, ThreadX API 서비스에 대한 모든 모듈 요청의 배치 및 발송을 담당합니다.

> [!NOTE]
> ThreadX 모듈 **관리자** 소스 파일(C 및 어셈블리)는 ThreadX 라이브러리 프로젝트 "**tx**"에 추가되어야 합니다.

ThreadX 모듈 관리자 빌드에 필요한 단계는 다음과 같습니다(각 단계는 아래에서 더 상세히 설명).

1. 모듈 정보를 포함하려면 **TX_THREAD** 제어 블록을 확장해야 합니다. 이를 수행하는 가장 쉬운 방법은 **_tx_port.h_ *_ 파일의 **TX_THREAD_EXTENSION_2** 정의를 **_txm_module_port.h_** 의 _* TX_THREAD_EXTENSION_2** 로 바꾸는 것입니다. 포트 관련 확장에 대해서는 [부록](appendix.md)을 참조하세요.

확장 예제:

   ```c
   #define TX_THREAD_EXTENSION_2                     \
       VOID      tx_thread_module_instance_ptr;      \
       VOID      tx_thread_module_entry_info_ptr;    \
       ULONG     tx_thread_module_current_user_mode; \
       ULONG     tx_thread_module_user_mode;         \
       VOID     *tx_thread_module_kernel_stack_start;\
       VOID     *tx_thread_module_kernel_stack_end;  \
       ULONG     tx_thread_module_kernel_stack_size; \
       VOID     *tx_thread_module_stack_ptr;         \
       VOID     *tx_thread_module_stack_start;       \
       VOID     *tx_thread_module_stack_end;         \
       ULONG     tx_thread_module_stack_size;        \
       VOID     *tx_thread_module_reserved;
   ```

   다음 확장은 ***tx_port.h*** 에 정의되어야 합니다.

   ```c
   #define TX_EVENT_FLAGS_GROUP_EXTENSION  VOID    *tx_event_flags_group_module_instance; \
        VOID   (*tx_event_flags_group_set_module_notify)(struct TX_EVENT_FLAGS_GROUP_STRUCT *group_ptr);

   #define TX_QUEUE_EXTENSION              VOID    *tx_queue_module_instance; \
        VOID   (*tx_queue_send_module_notify)(struct TX_QUEUE_STRUCT *queue_ptr);

   #define TX_SEMAPHORE_EXTENSION          VOID    *tx_semaphore_module_instance; \
        VOID   (*tx_semaphore_put_module_notify)(struct TX_SEMAPHORE_STRUCT *semaphore_ptr);

   #define TX_TIMER_EXTENSION              VOID    *tx_timer_module_instance; \
        VOID   (*tx_timer_module_expiration_function)(ULONG id);
   ```

2. 모든 ***txm_module_manager_\**** C 및 어셈블리 파일을 ThreadX 라이브러리 프로젝트 **_tx_** 에 추가합니다.
3. 모든 라이브러리와 실행 파일 프로젝트를 다시 빌드합니다. NetX Duo가 필요한 경우, 정의된 **TXM_MODULE_ENABLE_NETX_DUO** 를 사용하여 모든 모듈 및 모듈 관리자 C 코드를 빌드해야 합니다.

## <a name="module-manager-sources"></a>모듈 관리자 원본

ThreadX 모듈 관리자에는 상주 ThreadX 코드에 직접 연결 및 배치할 수 있도록 설계된 원본 파일 세트가 있습니다. 이 파일은 모듈을 실행하고, 모듈로부터의 후속 ThreadX API 요청을 배치하는 기능을 제공합니다. 모듈 관리자 파일은 다음과 같습니다.

| **파일 이름** |  **콘텐츠** |
|-------------- | ------------- |
| ***txm_module.h*** | 모듈 정보를 정의하는 파일을 포함합니다(모듈 소스 코드에도 포함). |
| ***txm_module_manager_dispatch.h*** | 발송 도우미 함수를 정의하는 파일을 포함합니다.|
| ***txm_module_manager_util.h*** | 내부 유틸리티 도우미 매크로 및 함수를 정의하는 파일을 포함합니다. |
| ***txm_module_port.h*** | 포트 관련 모듈 정보를 정의하는 파일을 포함합니다(모듈 소스 코드에도 포함). |
| ***tx_initialize_low_level.\[s,S,68\]** _ | 기존 ThreadX 라이브러리 파일을 바꿉니다. 모듈 관리자 및 메모리 실행을 위한 벡터 테이블과 추가 벡터 처리기를 업데이트합니다. _ 이 파일은 Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR에만 있습니다.*|
| ***tx_thread_context_restore.s** _ | 기존 ThreadX 라이브러리 파일을 바꿉니다. 인터럽트 처리 후 스레드 컨텍스트를 복원합니다. _ 이 파일은 Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR에만 있습니다.*|
| ***tx_thread_schedule.\[s,S,68\]*** | 기존 ThreadX 라이브러리 파일을 바꿉니다. 스케줄러 코드를 확장합니다. 이 경우 메모리 관리 레지스터를 업데이트하는 데 사용됩니다. |
| ***tx_thread_stack_build.s** _ | 기존 ThreadX 라이브러리 파일을 바꿉니다. 스레드의 스택 프레임을 빌드합니다. _ 이 파일은 Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR에만 있습니다.*|
| ***txm_module_manager_thread_stack_build.\[s,S,68\]*** | 모든 모듈 초기 스택을 빌드하고, 위치 중립적 데이터 액세스를 위한 설정을 포함합니다. |
| ***txm_module_manager_user_mode_entry.\[s,S\]** _ | 모듈이 커널 모드에 들어갈 수 있게 합니다. _ 이 파일은 Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR에만 있습니다.*|
| ***txm_module_manager_alignment_adjust.c*** | 포트 관련 정렬 요구 사항을 처리합니다.|
| ***txm_module_manager_application_request.c*** | 상주 코드에 대한 애플리케이션 관련 요청을 처리합니다. |
| ***txm_module_manager_callback_request.c*** | 모듈에 콜백 요청을 보냅니다. |
| ***txm_module_manager_event_flags_notify_trampoline.c*** | ThreadX로부터의 이벤트 플래그 설정 알림 호출을 처리합니다. |
| ***txm_module_manager_external_memory_enable.c*** | 모듈이 액세스할 수 있는 공유 메모리 공간에 대해 메모리 관리 테이블에 항목을 만듭니다. |
| ***txm_module_manager_file_load.c*** | 모듈 메모리 영역에 바이너리 모듈 파일을 할당 및 로드하고 실행을 준비합니다. |
| ***txm_module_manager_in_place_load.c*** | 모듈 데이터 영역을 할당하고 제공된 코드 주소로부터 모듈 실행을 준비합니다. |
| ***txm_module_manager_initialize.c*** | 모듈 로드 및 실행에 사용 가능한 모듈 메모리 영역의 지정을 포함하여, 모듈 관리자를 초기화합니다. |
| ***txm_module_manager_initialize_mmu.c** _ | MMU를 초기화합니다. 사용자는 자신의 메모리 맵에 따라 이 파일을 편집할 수 있습니다. _ 이 파일은 Cortex-A7/ARM에만 있음* |
| ***txm_module_manager_mm_initialize.c** _ | MPU/MMU를 초기화합니다. 사용자는 자신의 메모리 맵에 따라 이 파일을 편집할 수 있습니다. _ 이 파일은 Cortex-A7/ARM에만 있음* |
| ***txm_module_manager_kernel_dispatch.c*** | 요청 ID를 기준으로 모듈 API 요청을 처리합니다. |
| ***txm_module_manager_maximum_module_priority_set.c*** | 모듈에서 허용되는 최대 스레드 우선 순위를 설정합니다. |
| ***txm_module_manager_memory_fault_handler.c*** | 실행 모듈에서 검색된 메모리 오류를 처리합니다. |
| ***txm_module_manager_memory_fault_notify.c*** | 메모리 오류가 발생할 때마다 애플리케이션 알림 콜백을 등록합니다. |
| ***txm_module_manager_memory_load.c*** | 모듈의 코드와 데이터를 할당 및 로드하고 모듈 실행을 준비합니다. |
| ***txm_module_manager_mm_register_setup.c*** | 코드와 데이터가 로드된 위치에 따라 모듈에 대해 MPU/MMU 레지스터를 설정합니다. |
| ***txm_module_manager_object_allocate.c*** | 모듈 개체에 대해 메모리를 할당합니다. |
| ***txm_module_manager_object_deallocate.c*** | 모듈 개체에 대해 메모리를 할당 해제합니다. |
| ***txm_module_manager_object_pointer_get.c*** | 제공된 개체 형식과 이름을 검색하고, 찾으면 개체 포인터를 반환합니다. |
| ***txm_module_manager_object_pointer_get_extended.c*** | 제공된 개체 형식과 이름을 검색하고, 찾으면 개체 포인터를 반환합니다. 안전을 위해 지정된 이름 길이 |
| ***txm_module_manager_object_pool_create.c***  | 애플리케이션이 할당할 수 있게 모듈의 데이터 영역 밖에 개체 풀을 만듭니다. |
| ***txm_module_manager_properties_get.c*** | 지정한 모듈의 속성을 가져옵니다. |
| ***txm_module_manager_queue_notify_trampoline.c*** | ThreadX로부터의 큐 호출을 처리합니다. |
| ***txm_module_manager_semaphore_notify_trampoline.c*** | ThreadX로부터의 세마포 Put 알림 호출을 처리합니다.|
| ***txm_module_manager_start.c*** | 모듈 실행을 시작합니다. |
| ***txm_module_manager_stop.c*** | 모듈의 실행을 중지합니다. |
| ***txm_module_manager_thread_create.c*** | 모든 모듈 스레드를 만듭니다. |
| ***txm_module_manager_thread_notify_trampoline.c*** | ThreadX로부터의 진입/진출 알림을 처리합니다. |
| ***txm_module_manager_thread_reset.c*** | 모듈 스레드를 다시 설정합니다. |
| ***txm_module_manager_timer_notify_trampoline.c*** | ThreadX로부터의 타이머 만료를 처리합니다. |
| ***txm_module_manager_unload.c*** | 모듈 메모리 영역에서 모듈을 언로드합니다. |
| ***txm_module_manager_util.c*** | 관리자에 대한 내부 도우미 함수입니다. |

## <a name="module-manager-initialization"></a>모듈 관리자 초기화

애플리케이션의 상주 부분은 모듈 관리자 초기화 함수 ***Txm_module_manager_initialize*** 의 호출을 담당합니다. 이 함수는 모듈 메모리 할당에 사용되는 메모리 영역 설정을 포함하여, 모듈 로드 및 언로드를 위한 내부 구조를 설정합니다.

## <a name="module-manager-loading"></a>모듈 관리자 로드

모듈 관리자는 이미 상주 코드 영역에 있는 바이너리 모듈 파일이나 모듈 코드 섹션으로부터 동적으로 모듈을 모듈 메모리에 로드할 수 있습니다. 또한 모듈 관리자는 위치에서 코드를 실행할 수 있습니다. 즉, 모듈 데이터만 모듈 메모리에 할당되며 코드 실행은 위치에서 실행됩니다. 다음 모듈 관리자 로드 API 함수를 사용할 수 있습니다.

* ***txm_module_manager_file_load***

* ***txm_module_manager_in_place_load***

* ***txm_module_manager_memory_load***

모듈 관리자의 메모리 보호 버전은 모듈에 적합한 맞춤이 로드되고 메모리 관리 레지스터가 모듈마다 적합하게 설정되었는지도 확인합니다. 모듈 프리앰블 옵션을 통해 메모리 보호를 사용하도록 설정하면 모듈 메모리 액세스가 모듈 코드 및 데이터 영역으로 제한됩니다.

## <a name="module-manager-starting"></a>모듈 관리자 시작

모듈 관리자는 ***txm_module_manager_start*** API 함수를 통해 이전에 로드된 모듈의 실행을 시작합니다. 모듈 실행을 시작하기 위해 이 함수는 모듈 프리앰블에서 지정한 시작 위치에서 모듈을 입력하는 스레드를 만듭니다. 이 스레드의 우선 순위 및 스택 크기도 모듈 프리앰블에 지정됩니다.

## <a name="module-manager-stopping"></a>모듈 관리자 중지

모듈 관리자는 ***txm_module_manager_stop*** 함수를 통해 이전에 로드되어 실행 중인 모듈의 실행을 종료합니다. 이 API 함수는 먼저 초기 시작 스레드를 종료하고 삭제합니다. 모듈 프리앰블이 중지 스레드를 지정하는 경우 이 스레드를 만들고 실행합니다. 모듈 관리자는 중지 스레드가 완료될 때까지 일정 시간 대기합니다. 완료되면 모듈이 만든 모든 시스템 리소스가 삭제되고 모듈이 유휴 상태로 들어가며, 여기서 다시 시작 또는 언로드될 수 있습니다.

## <a name="module-manager-unloading"></a>모듈 관리자 언로드

모듈 관리자는 이전에 로드되었으나 실행 중이 아닌 모듈을 ***txm_module_manager_unload*** 함수를 통해 언로드합니다. 이 API는 모듈에 연결된 모든 메모리를 해제하여 향후 다른 모듈이 사용할 수 있게 합니다.

## <a name="module-manager-requests"></a>모듈 관리자 요청

모듈 관리자에 대한 모듈의 요청은 모듈 관리자가 모듈에 제공한 함수 포인터를 통해 모듈 관리자 발송 함수를 호출하기 위해 모든 ThreadX 호출을 매핑하는 ***txm_module.h*** 의 매크로를 통해 수행됩니다.

***txm_module_application_request*** 를 호출하는 모듈을 통해 이루어지는 추가 애플리케이션 관련 서비스는 ThreadX API에 사용되는 것과 동일한 매크로 메커니즘으로 처리됩니다. 기본적으로 모듈 관리자의 이 처리 함수는 비어 있고 애플리케이션 관련 요청을 처리하기 위해 필요한 코드를 애플리케이션이 추가하도록 설계되었습니다.

모듈 관리자가 요청을 구현하지 않으면 모듈 관리자가 **TX_NOT_AVAILABLE** 오류 상태 값을 반환합니다. 모듈의 액세스 범위를 벗어나는 작업을 모듈이 요청하는 경우에도 이 오류 코드가 반환됩니다. 예를 들어, 모듈은 타이머 제어 블록이 있는 타이머나, 모듈 코드 영역 외부의 콜백 주소를 만들 수 없습니다.

## <a name="module-manager-example"></a>모듈 관리자 예제

다음은 이전에 2장에서 정의한 예제 모듈을 실행하는 모듈 관리자 코드의 예제입니다. 디버거에서는 모듈이 이미 ROM 주소 0x00800000에 로그된 것으로 가정합니다.

```c
#include "tx_api.h"
#include "txm_module.h"

#define DEMO_STACK_SIZE 1024

/* Define the ThreadX object control blocks. */
TX_THREAD   module_manager;

/* Define thread prototype. */
void        module_manager_entry(ULONG thread_input);

/* Define the module object pool area. */
UCHAR       object_memory[8192];

/* Define the module data pool area. */
#define MODULE_DATA_SIZE 65536
UCHAR       module_data_area[MODULE_DATA_SIZE];

/* Define module instances. */
TXM_MODULE_INSTANCE     my_module1;
TXM_MODULE_INSTANCE     my_module2;

/* Define the count of memory faults. */
ULONG memory_faults;

/* Define fault handler. */
VOID module_fault_handler(TX_THREAD *thread, TXM_MODULE_INSTANCE *module)
{
    /* Just increment the fault counter. */
    memory_faults++;
}

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    /* Create the module manager thread. */
    tx_thread_create(&module_manager, "Module Manager Thread", module_manager_entry, 0,
                    first_unused_memory, DEMO_STACK_SIZE,
                    1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

/* Define the test threads. */
void module_manager_entry(ULONG thread_input)
{
    /* Initialize the module manager. */
    txm_module_manager_initialize((VOID *) module_data_area, MODULE_DATA_SIZE);

    /* Create a pool for module objects. */
    txm_module_manager_object_pool_create(object_memory, sizeof(object_memory));

    /* Register a fault handler. */
    txm_module_manager_memory_fault_notify(module_fault_handler);

    /* Load the module that is already there,
        in this example it is placed at 0x00800000. */
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Load a second instance of the module. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);

    /* Enable shared memory region for module2. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);

    /* Start the modules. */
    txm_module_manager_start(&my_module1);
    txm_module_manager_start(&my_module2);

    /* Sleep for a while and let the modules run... */
    tx_thread_sleep(300);

    /* Stop the modules. */
    txm_module_manager_stop(&my_module1);
    txm_module_manager_stop(&my_module2);

    /* Unload the modules. */
    txm_module_manager_unload(&my_module1);
    txm_module_manager_unload(&my_module2);

    /* Reload the modules. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Give both modules shared memory. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);
    txm_module_manager_external_memory_enable(&my_module1, (void*)0x20600000, 0x010000, 0x3F);

    /* Set maximum module1 priority to 5. */
    txm_module_manager_maximum_module_priority_set(&my_module1, 5);

    /* Start the modules again. */
    txm_module_manager_start(&my_module2);
    txm_module_manager_start(&my_module1);

    /* Now just spin... */
    while(1)
    {
        tx_thread_sleep(100);

        /* Threads 0 and 5 in module1 are not created because they violate the maximum priority. */
    }
}
```

## <a name="module-manager-building"></a>모듈 관리자 빌드

***txm_module_manager_\**** 원본 파일을 ThreadX 라이브러리에 추가해야 합니다.

ThreadX 모듈 관리자 애플리케이션은 실제로 하나 이상의 애플리케이션 파일이 ThreadX 라이브러리 ***tx.a*** 에 하나로 연결된 표준 ThreadX 애플리케이션과 동일합니다. 모듈 관리자 애플리케이션 빌드는 사용 중인 도구 체인에 따라 다릅니다. 포트 관련 예제는 [부록](appendix.md)을 참조하세요.
