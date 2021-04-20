---
title: 6장 - Azure RTOS ThreadX 추적 이벤트
description: 이 장에서는 Azure RTOS ThreadX 이벤트에 대해 설명합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8f0ff03d112597371059d925f64b7511454e123c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812372"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a>6장 - Azure RTOS ThreadX 추적 이벤트

이 장에서는 Azure RTOS ThreadX 이벤트에 대해 설명합니다. 

## <a name="list-of-events-and-icons"></a>이벤트 및 아이콘 목록

다음은 TraceX에 의해 표시되는 ThreadX 이벤트 목록입니다.

| **아이콘**                         | **의미** |
| -------------------------------- | ------------------------------------- |
| ![내부 스레드 다시 시작 아이콘](./media/user-guide/tx-events/image1.png)    | 내부 스레드 다시 시작  |
| ![내부 스레드 일시 중단 아이콘](./media/user-guide/tx-events/image2.png)    | 내부 스레드 일시 중단 |
| ![인터럽트 서비스 루틴 들어가기 아이콘](./media/user-guide/tx-events/image3.png)    | ISR(인터럽트 서비스 루틴) 들어가기 |
| ![인터럽트 서비스 루틴 끝내기 아이콘](./media/user-guide/tx-events/image4.png)    | ISR(인터럽트 서비스 루틴) 끝내기  |
| ![내부 시간 조각 아이콘](./media/user-guide/tx-events/image5.png)    | 내부 시간 조각 |
| ![실행 아이콘](./media/user-guide/tx-events/image6.png)    | 실행 중 |
| ![블록 풀 할당 아이콘](./media/user-guide/tx-events/image7.png)    | **블록 풀 할당**(*tx_block_allocate*)  |
| ![블록 풀 만들기 아이콘](./media/user-guide/tx-events/image8.png)    | **블록 풀 만들기**(*tx_block_pool_create*) |
| ![블록 풀 삭제 아이콘](./media/user-guide/tx-events/image9.png)    | **블록 풀 삭제**(*tx_block_pool_delete*) |
| ![블록 풀 정보 가져오기 아이콘](./media/user-guide/tx-events/image10.png)    | **블록 풀 정보 가져오기**(*tx_block_pool_info_get*) |
| ![블록 풀 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image11.png)    | **블록 풀 성능 정보 가져오기**(*tx_block_pool_performance_info_get*) |
| ![블록 풀 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image12.png)    | **블록 풀 시스템 성능 정보 가져오기**(*tx_block_pool_performance_system_info_get*) |
| ![블록 풀 우선 순위 지정 아이콘](./media/user-guide/tx-events/image13.png)    | **블록 풀 우선 순위 지정**(*tx_block_pool_prioritize*) |
| ![풀에 대한 블록 해제 아이콘](./media/user-guide/tx-events/image14.png)    | **풀에 대한 블록 해제**(*tx_block_release*) |
| ![메모리 바이트 풀 할당 아이콘](./media/user-guide/tx-events/image15.png)    | **메모리 바이트 풀 할당**(*tx_byte_allocate*) |
| ![바이트 풀 만들기 아이콘](./media/user-guide/tx-events/image16.png)    | **바이트 풀 만들기**(*tx_byte_pool_create*) |
| ![바이트 풀 삭제 아이콘](./media/user-guide/tx-events/image17.png)    | **바이트 풀 삭제**(*tx_byte_pool_delete*) |
| ![바이트 풀 정보 가져오기 아이콘](./media/user-guide/tx-events/image18.png)    | **바이트 풀 정보 가져오기**(*tx_byte_pool_info_get*) |
| ![바이트 풀 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image19.png)    | **바이트 풀 성능 정보 가져오기**(*tx_byte_pool_performance_info_get*) |
| ![바이트 풀 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image20.png)    | **바이트 풀 시스템 성능 정보 가져오기**(*tx_byte_pool_performance_system_info_get*) |
| ![*바이트 풀 우선 순위 지정 아이콘](./media/user-guide/tx-events/image21.png)    | **바이트 풀 우선 순위 지정**(*tx_byte_pool_prioritize*) |
| ![풀에 대한 바이트 메모리 해제 아이콘](./media/user-guide/tx-events/image22.png)    | **풀에 대한 바이트 메모리 해제**(*tx_byte_release*) |
| ![이벤트 플래그 만들기 아이콘](./media/user-guide/tx-events/image23.png)    | **이벤트 플래그 만들기**(*tx_event_flags_create*) |
| ![이벤트 플래그 삭제 아이콘](./media/user-guide/tx-events/image24.png)    | **이벤트 플래그 삭제**(*tx_event_flags_delete*) |
| ![이벤트 플래그 가져오기 아이콘](./media/user-guide/tx-events/image25.png)    | **이벤트 플래그 가져오기**(*tx_event_flags_get*) |
| ![이벤트 플래그 정보 가져오기 아이콘](./media/user-guide/tx-events/image26.png)    | **이벤트 플래그 정보 가져오기**(*tx_event_flags_info_get*) |
| ![이벤트 플래그 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image27.png)    | **이벤트 플래그 성능 정보 가져오기**(*tx_event_flags_performance_info_get*) |
| ![이벤트 플래그 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image28.png)    | **이벤트 플래그 시스템 성능 정보 가져오기**(*tx_event_flags_performance_system_info_get*) |
| ![이벤트 플래그 설정 아이콘](./media/user-guide/tx-events/image29.png)    | **이벤트 플래그 설정**(*tx_event_flags_set*) |
| ![이벤트 플래그 설정 알림 아이콘](./media/user-guide/tx-events/image30.png)    | **이벤트 플래그 설정 알림**(*tx_event_flags_set_notify*) |
| ![인터럽트 사용/사용 안 함 아이콘](./media/user-guide/tx-events/image31.png)    | **인터럽트 사용/사용 안 함**(*tx_interrupt_control*) |
| ![뮤텍스 만들기 아이콘](./media/user-guide/tx-events/image32.png)    | **뮤텍스 만들기**(*tx_mutex_create*) |
| ![뮤텍스 삭제 아이콘](./media/user-guide/tx-events/image33.png)    | **뮤텍스 삭제**(*tx_mutex_delete*) |
| ![뮤텍스 가져오기 아이콘](./media/user-guide/tx-events/image34.png)    | **뮤텍스 가져오기**(*tx_mutex_get*) |
| ![뮤텍스 정보 가져오기 아이콘](./media/user-guide/tx-events/image35.png)    | **뮤텍스 정보 가져오기**(*tx_mutex_info_get*) |
| ![뮤텍스 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image36.png)    | **뮤텍스 성능 정보 가져오기**(*tx_mutex_performance_info_get*) |
| ![뮤텍스 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image37.png)    | **뮤텍스 시스템 성능 정보 가져오기**(*tx_mutex_performance_system_info_get*) |
| ![뮤텍스 우선 순위 지정 아이콘](./media/user-guide/tx-events/image38.png)    | **뮤텍스 우선 순위 지정**(*tx_mutex_prioritize*) |
| ![뮤텍스 넣기 아이콘](./media/user-guide/tx-events/image39.png)    | **뮤텍스 넣기**(*tx_mutex_put*) |
| ![큐 만들기 아이콘](./media/user-guide/tx-events/image40.png)    | **큐 만들기**(*tx_queue_create*) |
| ![큐 삭제 아이콘](./media/user-guide/tx-events/image41.png)    | **큐 삭제**(*tx_queue_delete*) |
| ![큐 플러시 아이콘](./media/user-guide/tx-events/image42.png)    | **큐 플러시**(*tx_queue_flush*) |
| ![큐의 맨 앞으로 보내기 아이콘](./media/user-guide/tx-events/image43.png)    | **큐의 맨 앞으로 보내기**(*tx_queue_front_send*) |
| ![큐 정보 가져오기 아이콘](./media/user-guide/tx-events/image44.png)    | **큐 정보 가져오기**(*tx_queue_info_get*) |
| ![큐 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image45.png)    | **큐 성능 정보 가져오기**(*tx_queue_performance_info_get*) |
| ![큐 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image46.png)    | **큐 시스템 성능 정보 가져오기**(*tx_queue_performance_system_info_get*) |
| ![큐 우선 순위 지정 아이콘](./media/user-guide/tx-events/image47.png)    | **큐 우선 순위 지정**(*tx_queue_prioritize*) |
| ![큐 수신 메시지 아이콘](./media/user-guide/tx-events/image48.png)    | **큐 수신 메시지**(*tx_queue_receive*) |
| ![큐 송신 메시지 아이콘](./media/user-guide/tx-events/image49.png)    | **큐 송신 메시지**(*tx_queue_send*) |
| ![큐 송신 알림 아이콘](./media/user-guide/tx-events/image50.png)    | **큐 송신 알림**(*tx_queue_send_notify*) |
| ![세마포 상한 넣기 아이콘](./media/user-guide/tx-events/image51.png)    | **세마포 상한 넣기**(*tx_semaphore_ceiling_put*) |
| ![세마포 만들기 아이콘](./media/user-guide/tx-events/image52.png)    | **세마포 만들기**(*tx_semaphore_create*) |
| ![세마포 삭제 아이콘](./media/user-guide/tx-events/image53.png)    | **세마포 삭제**(*tx_semaphore_delete*) |
| ![세마포 가져오기 아이콘](./media/user-guide/tx-events/image54.png)    | **세마포 가져오기**(*tx_semaphore_get*) |
| ![세마포 정보 가져오기 아이콘](./media/user-guide/tx-events/image55.png)    | **세마포 정보 가져오기**(*tx_semaphore_info_get*) |
| ![세마포 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image56.png)    | **세마포 성능 정보 가져오기**(*tx_semaphroe_performance_info_get*) |
| ![세마포 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image57.png)    | **세마포 시스템 성능 정보 가져오기**(*tx_semaphore_performance_system_info_get*) |
| ![세마포 우선 순위 지정 아이콘](./media/user-guide/tx-events/image58.png)    | **세마포 우선 순위 지정**(*tx_semaphore_prioritize*) |
| ![세마포 넣기 아이콘](./media/user-guide/tx-events/image59.png)    | **세마포 넣기**(*tx_semaphore_put*) |
| ![세마포 넣기 알림 아이콘](./media/user-guide/tx-events/image60.png)    | **세마포 넣기 알림**(*tx_semaphore_put_notify*) |
| ![스레드 만들기 아이콘](./media/user-guide/tx-events/image61.png)    | **스레드 만들기**(*tx_thread_create*) |
| ![스레드 삭제 아이콘](./media/user-guide/tx-events/image62.png)    | **스레드 삭제**(*tx_thread_delete*) |
| ![스레드 종료/진입 아이콘](./media/user-guide/tx-events/image63.png)    | **스레드 종료/진입 알림**(*tx_thread_entry_exit_notify*) |
| ![스레드 식별 아이콘](./media/user-guide/tx-events/image64.png)    | **스레드 식별**(*tx_thread_identify*) |
| ![스레드 정보 가져오기 아이콘](./media/user-guide/tx-events/image65.png)    | **스레드 정보 가져오기**(*tx_thread_info_get*) |
| ![스레드 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image66.png)    | **스레드 성능 정보 가져오기**(*tx_thread_performance_info_get*) |
| ![스레드 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image67.png)    | **스레드 성능 시스템 정보 가져오기**(*tx_thread_performance_system_info_get*) |
| ![스레드 선점 변경 아이콘](./media/user-guide/tx-events/image68.png)    | **스레드 선점 변경**(*tx_thread_preemption_change*) |
| ![스레드 우선 순위 변경 아이콘](./media/user-guide/tx-events/image69.png)    | **스레드 우선 순위 변경**(*tx_thread_priority_change*) |
| ![스레드 양도 아이콘](./media/user-guide/tx-events/image70.png)    | **스레드 양도**(*tx_thread_relinquish*) |
| ![스레드 재설정 아이콘](./media/user-guide/tx-events/image71.png)    | **스레드 재설정**(*tx_thread_reset*) |
| ![*스레드 다시 시작 아이콘](./media/user-guide/tx-events/image72.png)    | **스레드 다시 시작**(**tx_thread_resume*) |
| ![스레드 일시 중지 아이콘](./media/user-guide/tx-events/image73.png)    | **스레드 일시 중지**(*tx_thread_sleep*)* |
| ![스레드 스택 오류 알림 아이콘](./media/user-guide/tx-events/image74.png)    | **스레드 스택 오류 알림**(*tx_thread_stack_error_notify*) |
| ![스레드 일시 중단 아이콘](./media/user-guide/tx-events/image75.png)    | **스레드 일시 중단**(*tx_thread_suspend*) |
| ![스레드 종료 아이콘](./media/user-guide/tx-events/image76.png)    | **스레드 종료**(*tx_thread_terminate*) |
| ![스레드 시간 조각 변경 아이콘](./media/user-guide/tx-events/image77.png)    | **스레드 시간 조각 변경**(*tx_thread_time_slice_change*) |
| ![스레드 대기 중단 아이콘](./media/user-guide/tx-events/image78.png)    | **스레드 대기 중단**(*tx_thread_wait_abort*) |
| ![시간 가져오기 아이콘](./media/user-guide/tx-events/image79.png)    | **시간 가져오기**(*tx_time_get*) |
| ![시간 설정 아이콘](./media/user-guide/tx-events/image80.png)    | **시간 설정**(*tx_time_set*) |
| ![타이머 활성화 아이콘](./media/user-guide/tx-events/image81.png)    | **타이머 활성화**(*tx_timer_activate*) |
| ![타이머 변경 아이콘](./media/user-guide/tx-events/image82.png)    | **타이머 변경**(*tx_timer_change*) |
| ![타이머 만들기 아이콘](./media/user-guide/tx-events/image83.png)    | **타이머 만들기**(*tx_timer_create*) |
| ![타이머 비활성화 아이콘](./media/user-guide/tx-events/image84.png)    | **타이머 비활성화**(*tx_timer_deactivate*) |
| ![타이머 삭제 아이콘](./media/user-guide/tx-events/image85.png)    | **타이머 삭제**(*tx_timer_delete*) |
| ![타이머 정보 가져오기 아이콘](./media/user-guide/tx-events/image86.png)    | **타이머 정보 가져오기**(*tx_timer_info_get*) |
| ![타이머 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image87.png)    | **타이머 성능 정보 가져오기**(*tx_timer_performance_info_get*) |
| ![*타이머 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image88.png)    | **타이머 성능 시스템 정보 가져오기**(*tx_timer_performance_system_info_get*) |
| ![사용자 정의 이벤트 아이콘](./media/user-guide/tx-events/image0.png)    | **사용자 정의 이벤트**(10장 참조)    |

## <a name="event-descriptions"></a>이벤트 설명

### <a name="internal-thread-resume"></a>내부 스레드 다시 시작

#### <a name="internal-thread-resume"></a>내부 스레드 다시 시작

**아이콘** ![내부 스레드 다시 시작 아이콘](./media/user-guide/tx-events/image1.png)

**설명**

이 이벤트는 스레드 실행을 다시 시작하는 ThreadX의 내부 처리를 나타냅니다. 지정된 스레드가 가장 높은 우선 순위이고 선점 임계값의 실행이 차단되지 않는 경우 시스템에서 새로 준비된 스레드 실행을 시작합니다.

**정보 필드**

- 정보 필드 1: 다시 시작 중인 스레드에 대한 포인터입니다.
- 정보 필드 2: 다음과 같이 다시 시작되는 스레드의 이전 상태입니다.

  |  스레드 상태                     | 값        |
  |---------------------------------- | --------|
  |  TX_READY                         | 0       |
  |  TX_COMPLETED                     | 1       |
  |  TX_TERMINATED                    | 2       |
  |  TX_SUSPENDED                     | 3       |
  |  TX_SLEEP                         | 4       |
  |  TX_QUEUE_SUSP                    | 5       |
  |  TX_SEMAPHORE_SUSP                | 6       |
  |  TX_EVENT_FLAG                    | 7       |
  |  TX_BLOCK_MEMORY                  | 8       |
  |  TX_BYTE_MEMORY                   | 9       |
  |  TX_TCP_IP                        | 12      |
  |  TX_MUTEX_SUSP                    | 13      |

- 정보 필드 3: 호출하는 동안의 스택 포인터 값입니다. 
- 정보 필드 4: 실행 우선 순위가 다음으로 가장 높은 스레드에 대한 포인터입니다.

### <a name="internal-thread-suspend"></a>내부 스레드 일시 중단

#### <a name="internal-thread-suspend"></a>내부 스레드 일시 중단

**아이콘** ![내부 스레드 일시 중단 아이콘](./media/user-guide/tx-events/image2.png)

**설명**

이 이벤트는 스레드 실행을 일시 중단하는 ThreadX의 내부 처리를 나타냅니다. 실행할 준비가 된 다음으로 우선 순위가 가장 높은 스레드는 네 번째 정보 필드에 배치됩니다. 이 값이 Null이면 실행할 준비가 된 다른 스레드가 없으며 시스템이 유휴 상태인 것입니다.

**정보 필드**

- 정보 필드 1: 일시 중단 중인 스레드에 대한 포인터입니다.
- 정보 필드 2: 다음과 같이 일시 중단 중인 스레드의 새 상태입니다.

  |  스레드 상태                     | 값        |
  |---------------------------------- | --------|
  |  TX_COMPLETED                     | 1       |
  |  TX_TERMINATED                    | 2       |
  |  TX_SUSPENDED                     | 3       |
  |  TX_SLEEP                         | 4       |
  |  TX_QUEUE_SUSP                    | 5       |
  |  TX_SEMAPHORE_SUSP                | 6       |
  |  TX_EVENT_FLAG                    | 7       |
  |  TX_BLOCK_MEMORY                  | 8       |
  |  TX_BYTE_MEMORY                   | 9       |
  |  TX_TCP_IP                        | 12      |
  |  TX_MUTEX_SUSP                    | 13      |

- 정보 필드 3: 호출하는 동안의 스택 포인터 값입니다. 정보 필드 4: 실행 우선 순위가 다음으로 가장 높은 스레드에 대한 포인터입니다. Null인 경우 시스템은 유휴 상태입니다.

### <a name="interrupt-service-routine-isr-enter"></a>ISR(인터럽트 서비스 루틴) 들어가기 

#### <a name="enter-isr"></a>ISR 들어가기 

**아이콘** ![ISR 들어가기 아이콘](./media/user-guide/tx-events/image3.png)

**설명**

이 이벤트는 애플리케이션에서 ISR(인터럽트 서비스 루틴)에 들어가는 것을 나타냅니다. 인터럽트 서비스 루틴 실행은 ISR 종료 이벤트가 발생할 때까지 계속됩니다.

**정보 필드**

- 정보 필드 1: 호출하는 동안의 스택 포인터 값입니다.
- 정보 필드 2: 애플리케이션 정의 ISR 번호(선택 사항)입니다.
- 정보 필드 3: 중첩된 인터럽트 수입니다.
- 정보 필드 4: 내부 선점 사용 안 함 플래그입니다.

### <a name="interrupt-service-routine-isr-exit"></a>ISR(인터럽트 서비스 루틴) 끝내기 

#### <a name="exit-isr"></a>ISR 끝내기

**아이콘** ![ISR 끝내기 아이콘](./media/user-guide/tx-events/image4.png)

**설명**

이 이벤트는 애플리케이션에서 ISR(인터럽트 서비스 루틴)을 종료하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 호출하는 동안의 스택 포인터 값입니다.
- 정보 필드 2: 애플리케이션 정의 ISR 번호(선택 사항)입니다.
- 정보 필드 3: 중첩된 인터럽트 수입니다.
- 정보 필드 4: 내부 선점 사용 안 함 플래그입니다.

### <a name="internal-time-slice"></a>내부 시간 조각

#### <a name="internal-time-slice"></a>내부 시간 조각

**아이콘** ![내부 시간 조각 아이콘](./media/user-guide/tx-events/image5.png)

**설명**

이 이벤트는 시간 조각 작업을 수행하는 ThreadX의 내부 처리를 나타냅니다. 우선 순위가 같은 다음 스레드는 첫 번째 정보 필드에 배치됩니다. 이 값이 현재 스레드와 같으면 시간 조각이 수행되지 않은 것입니다.

- 정보 필드 1: 실행할 다음 스레드에 대한 포인터입니다.
- 정보 필드 2: 중첩된 인터럽트 수입니다.
- 정보 필드 3: 내부 선점 사용 안 함 플래그입니다.
- 정보 필드 4: 호출하는 동안의 스택 포인터 값입니다.

### <a name="running"></a>실행 중

#### <a name="running-in-context"></a>컨텍스트에서 실행

**아이콘** ![실행 아이콘](./media/user-guide/tx-events/image6.png)

**설명**

이 이벤트는 스레드 컨텍스트 또는 유휴 시스템에서 실행되는 것을 나타냅니다. 이는 인터럽트의 결과로 컨텍스트의 후속 변경을 설명하는 데 사용됩니다.

**정보 필드**
- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="block-allocate"></a>블록 할당 

#### <a name="tx_block_allocate"></a>tx_block_allocate

**아이콘** ![블록 할당 아이콘](./media/user-guide/tx-events/image7.png)

**설명**

이 이벤트는 tx_block_allocate를 통해 메모리 블록을 할당하는 것을 나타냅니다. 성공하면 할당된 블록의 주소가 두 번째 정보 필드로 반환됩니다.

**정보 필드**
- 정보 필드 1: 해당 블록 풀에 대한 포인터입니다.
- 정보 필드 2: 반환된 메모리 블록에 대한 포인터입니다(성공한 경우).
- 정보 필드 3: tx_block_allocate 호출에 제공되는 대기 옵션입니다.
- 정보 필드 4: 이 할당 후 풀에서 사용 가능한 남은 블록 수입니다.

### <a name="block-pool-create"></a>블록 풀 만들기

#### <a name="tx_block_pool_create"></a>tx_block_pool_create

**아이콘** ![블록 풀 만들기 아이콘](./media/user-guide/tx-events/image8.png)

**설명**

이 이벤트는 tx_block_pool_create를 통해 메모리 블록 풀을 만드는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 해당 블록 풀 제어 블록에 대한 포인터입니다.
- 정보 필드 2: 풀의 시작 메모리 영역에 대한 포인터입니다.
- 정보 필드 3: 풀의 블록 수입니다. 정보 필드 4: 풀의 각 블록 크기(바이트)입니다.

### <a name="block-pool-delete"></a>블록 풀 삭제

#### <a name="tx_block_pool_delete"></a>tx_block_pool_delete

**아이콘** ![블록 풀 삭제 아이콘](./media/user-guide/tx-events/image9.png)

**설명**

이 이벤트는 tx_block_pool_delete를 통해 메모리 블록 풀을 삭제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 블록 풀 제어 블록에 대한 포인터입니다.
- 정보 필드 2: 호출하는 동안의 스택 포인터 값입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="block-pool-information-get"></a>블록 풀 정보 가져오기 

#### <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

**아이콘** ![블록 풀 정보 가져오기 아이콘](./media/user-guide/tx-events/image10.png)

**설명**

이 이벤트는 tx_block_pool_info_get을 통해 메모리 블록 풀에 대한 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 블록 풀 제어 블록에 대한 포인터입니다.
- 정보 필드 2: 호출하는 동안의 스택 포인터 값입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="block-pool-performance-information-get"></a>블록 풀 성능 정보 가져오기

#### <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

**아이콘** ![블록 풀 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image11.png)

**설명**

이 이벤트는 tx_block_pool_performance_info_get을 통해 메모리 블록 풀에 대한 성능 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 블록 풀 제어 블록에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="block-pool-performance-system-information-get"></a>블록 풀 성능 시스템 정보 가져오기

#### <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

**아이콘** ![블록 풀 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image12.png)

**설명**

이 이벤트는 tx_block_pool_performance_system_info_get을 통해 모든 메모리 블록 풀에 대한 성능 정보를 가져오는 것을 나타냅니다.

**정보 필드**
- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="block-pool-prioritize"></a>블록 풀 우선 순위 지정

#### <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

**아이콘** ![블록 풀 우선 순위 지정 아이콘](./media/user-guide/tx-events/image13.png)

**설명**

이 이벤트는 highestpriority suspended 스레드를 블록 풀 일시 중단 목록의 맨 앞에 배치하는 것을 나타냅니다. tx_block_release를 호출하기 전에 이 작업을 수행하면 일시 중단된 스레드 중 우선 순위가 가장 높은 스레드가 해제된 블록을 받게 됩니다.

**정보 필드**
- 정보 필드 1: 메모리 블록 풀 포인터입니다.
- 정보 필드 2: 이 블록 풀에 대해 일시 중단된 스레드 수입니다.
- 정보 필드 3: 호출 시의 스택 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="block-release"></a>블록 해제 

#### <a name="tx_block_release"></a>tx_block_release

**아이콘** ![블록 해제 아이콘](./media/user-guide/tx-events/image14.png)

**설명**

이 이벤트는 이전에 할당된 블록을 블록 풀로 다시 해제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 메모리 블록 풀 포인터입니다.
- 정보 필드 2: 해제할 블록에 대한 포인터입니다.
- 정보 필드 3: 이 블록 풀에 대해 일시 중단된 스레드 수입니다.
- 정보 필드 4: 호출 시의 스택 포인터입니다.

### <a name="byte-allocate"></a>바이트 할당 

#### <a name="tx_byte_allocate"></a>tx_byte_allocate

**아이콘** ![바이트 할당 아이콘](./media/user-guide/tx-events/image15.png)

**설명**

이 이벤트는 tx_byte_allocate를 통해 메모리를 할당하는 것을 나타냅니다. 성공하면 할당된 메모리의 주소가 두 번째 정보 필드로 반환됩니다.

**정보 필드**
- 정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.
- 정보 필드 2: 반환된 메모리에 대한 포인터입니다(성공한 경우).
- 정보 필드 3: 요청된 바이트 수입니다. 정보 필드 4: tx_byte_allocate 호출에 제공되는 대기 옵션입니다.

### <a name="byte-pool-create"></a>바이트 풀 만들기

#### <a name="tx_byte_pool_create"></a>tx_byte_pool_create

**아이콘** ![바이트 풀 만들기 아이콘](./media/user-guide/tx-events/image16.png)

**설명**

이 이벤트는 tx_byte_pool_create를 통해 바이트 풀을 만드는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.
- 정보 필드 2: 메모리 영역의 시작 부분에 대한 포인터입니다. 정보 필드 3: 바이트 풀의 바이트 수입니다.
- 정보 필드 4: 호출 시의 스택 포인터입니다.

### <a name="byte-pool-delete"></a>바이트 풀 삭제 

#### <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

**아이콘** ![바이트 풀 삭제 아이콘](./media/user-guide/tx-events/image17.png)

**설명**

이 이벤트는 tx_byte_pool_delete를 통해 바이트 풀을 삭제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.
- 정보 필드 2: 호출 시의 스택 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="byte-pool-information-get"></a>바이트 풀 정보 가져오기

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**아이콘** ![바이트 풀 정보 가져오기 아이콘](./media/user-guide/tx-events/image18.png)

**설명**

이 이벤트는 tx_byte_pool_info_get을 통해 바이트 풀 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="byte-pool-performance-info-get"></a>바이트 풀 성능 정보 가져오기 

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**아이콘** ![바이트 풀 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image19.png)

**설명**

이 이벤트는 tx_byte_pool_performance_info_get을 통해 바이트 풀 성능 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="byte-pool-performance-system-info-get"></a>바이트 풀 성능 시스템 정보 가져오기 

#### <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

**아이콘** ![바이트 풀 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image20.png)

**설명**

이 이벤트는 tx_byte_pool_performance_system_info_get을 통해 바이트 풀 성능 시스템 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="byte-pool-prioritize"></a>바이트 풀 우선 순위 지정

#### <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

**아이콘** ![바이트 풀 우선 순위 지정 아이콘](./media/user-guide/tx-events/image21.png)

**설명**

이 이벤트는 tx_byte_pool_prioritize를 통해 바이트 풀의 일시 중단 목록의 우선 순위를 지정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.
- 정보 필드 2: 바이트 풀에 대해 현재 일시 중단된 스레드 수입니다.
- 정보 필드 3: 호출 시의 스택 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="byte-release"></a>바이트 해제

#### <a name="tx_byte_release"></a>tx_byte_release

**아이콘** ![바이트 해제 아이콘](./media/user-guide/tx-events/image22.png)

**설명**

이 이벤트는 tx_byte_release를 통해 바이트 풀에서 할당된 메모리 블록을 해제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.
- 정보 필드 2: 이전에 할당된 바이트 풀 메모리에 대한 포인터입니다.
- 정보 필드 3: 이 바이트 풀에 대해 일시 중단된 스레드 수입니다.
- 정보 필드 4: 사용 가능한 메모리 바이트 수입니다.

### <a name="event-flags-create"></a>이벤트 플래그 만들기 

#### <a name="tx_event_flags_create"></a>tx_event_flags_create

**아이콘** ![이벤트 플래그 만들기 아이콘](./media/user-guide/tx-events/image23.png)

**설명**

이 이벤트는 tx_event_flags_create를 통해 새 이벤트 플래그 그룹을 만드는 것을 나타냅니다.

**정보 필드** 
- 정보 필드 1: 이벤트 플래그 그룹 제어 블록에 대한 포인터입니다.
- 정보 필드 2: 호출 시의 스택 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="event-flags-delete"></a>이벤트 플래그 삭제 

#### <a name="tx_event_flags_delete"></a>tx_event_flags_delete

**아이콘** ![이벤트 플래그 삭제 아이콘](./media/user-guide/tx-events/image24.png)

**설명**

이 이벤트는 tx_event_flags_delete를 통해 이벤트 플래그 그룹을 삭제하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 이벤트 플래그 그룹에 대한 포인터입니다.
- 정보 필드 2: 호출 시의 스택 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="event-flags-get"></a>이벤트 플래그 가져오기 

#### <a name="tx_event_flags_get"></a>tx_event_flags_get

**아이콘** ![이벤트 플래그 가져오기 아이콘](./media/user-guide/tx-events/image25.png)

**설명**

이 이벤트는 tx_event_flags_get을 통해 기존 이벤트 플래그 그룹에서 이벤트 플래그를 검색하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 이벤트 플래그 그룹에 대한 포인터입니다.
- 정보 필드 2: 요청된 이벤트 플래그입니다.
- 정보 필드 3: 그룹에 현재 설정된 이벤트 플래그입니다.
- 정보 필드 4: 이벤트 플래그 가져오기에 대한 요청된 옵션입니다.

### <a name="event-flags-information-get"></a>이벤트 플래그 정보 가져오기

#### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

**아이콘** ![이벤트 플래그 정보 가져오기 아이콘](./media/user-guide/tx-events/image26.png)

**설명**

이 이벤트는 tx_event_flags_info_get을 통해 기존 이벤트 플래그 그룹에 대한 정보를 검색하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 이벤트 플래그 그룹에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="event-flags-performance-information-get"></a>이벤트 플래그 성능 정보 가져오기 

#### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

**아이콘** ![이벤트 플래그 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image27.png)

**설명**

이 이벤트는 tx_event_flags_performance_info_get을 통해 기존 이벤트 플래그 그룹에 대한 성능 정보를 검색하는 것을 나타냅니다.

**정보 필드** 
- 정보 필드 1: 이벤트 플래그 그룹에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="event-flags-performance-system-info-get"></a>이벤트 플래그 성능 시스템 정보 가져오기

#### <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

**아이콘** ![이벤트 플래그 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image28.png)

**설명**

이 이벤트는 tx_event_flags_performance_system_info_get을 통해 기존 이벤트 플래그 그룹에 대한 성능 정보를 검색하는 것을 나타냅니다.

**정보 필드**
- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="event-flags-set"></a>이벤트 플래그 설정 

#### <a name="tx_event_flags_set"></a>tx_event_flags_set

**아이콘** ![이벤트 플래그 설정 아이콘](./media/user-guide/tx-events/image29.png)

**설명**

이 이벤트는 tx_event_flags_set을 통해 기존 이벤트 플래그 그룹의 이벤트 플래그를 설정(또는 해제)하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 이벤트 플래그 그룹에 대한 포인터입니다.
- 정보 필드 2: 설정(또는 해제)할 이벤트 플래그입니다.
- 정보 필드 3: AND 또는 OR 이벤트 플래그 옵션입니다.
- 정보 필드 4: 이벤트 플래그 그룹에 대해 일시 중단된 스레드 수입니다.

### <a name="event-flags-set-notify"></a>이벤트 플래그 설정 알림

#### <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

**아이콘** ![이벤트 플래그 설정 알림 아이콘](./media/user-guide/tx-events/image30.png)

**설명**

이 이벤트는 tx_event_flags_set_notify를 통해 기존 이벤트 플래그 그룹에 대한 이벤트 플래그 설정 작업의 알림 콜백을 등록하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 이벤트 플래그 그룹에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="interrupt-control"></a>인터럽트 제어 

#### <a name="tx_interrupt_control"></a>tx_interrupt_control

**아이콘** ![인터럽트 제어 아이콘](./media/user-guide/tx-events/image31.png)

**설명**

이 이벤트는 tx_interrupt_control을 통해 프로세서의 인터럽트 잠금 상태를 변경하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 새 인터럽트 상태입니다.
- 정보 필드 2: 호출 시의 스택 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="mutex-create"></a>뮤텍스 만들기 

#### <a name="tx_mutex_create"></a>tx_mutex_create

**아이콘** ![뮤텍스 만들기 아이콘](./media/user-guide/tx-events/image32.png)

**설명**

이 이벤트는 tx_mutex_create를 통해 뮤텍스를 만드는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 뮤텍스 제어 블록에 대한 포인터입니다.
- 정보 필드 2: 우선 순위 상속 옵션
- (TX_INHERIT 또는 TX_NO_INHERIT)입니다.
- 정보 필드 3: 호출 시의 스택 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="mutex-delete"></a>뮤텍스 삭제 

#### <a name="tx_mutex_delete"></a>tx_mutex_delete

**아이콘** ![뮤텍스 삭제 아이콘](./media/user-guide/tx-events/image33.png)

**설명**

이 이벤트는 tx_mutex_delete를 통해 뮤텍스를 삭제하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 뮤텍스에 대한 포인터입니다.
- 정보 필드 2: 호출 시의 스택 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="mutex-get"></a>뮤텍스 가져오기 

#### <a name="tx_mutex_get"></a>tx_mutex_get

**아이콘** ![뮤텍스 가져오기 아이콘](./media/user-guide/tx-events/image34.png)

**설명**

이 이벤트는 tx_mutex_get을 통해 뮤텍스를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 뮤텍스에 대한 포인터입니다.
- 정보 필드 2: tx_mutex_get 호출에 제공되는 대기 옵션입니다.
- 정보 필드 3: 뮤텍스를 소유하는 스레드에 대한 포인터입니다(Null은 뮤텍스를 소유하고 있지 않음을 의미).
- 정보 필드 4: 소유 스레드가 tx_mutex_get을 호출한 횟수입니다.

### <a name="mutex-information-get"></a>뮤텍스 정보 가져오기

#### <a name="tx_mutex_info_get"></a>tx_mutex_info_get

**아이콘** ![뮤텍스 정보 가져오기 아이콘](./media/user-guide/tx-events/image35.png)

**설명**

이 이벤트는 tx_mutex_info_get을 통해 뮤텍스 정보를 검색하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 뮤텍스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="mutex-performance-information-get"></a>뮤텍스 성능 정보 가져오기 

#### <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

**아이콘** ![뮤텍스 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image36.png)

**설명**

이 이벤트는 tx_mutex_performance_info_get을 통해 뮤텍스 성능 정보를 검색하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 뮤텍스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="mutex-performance-system-info-get"></a>뮤텍스 성능 시스템 정보 가져오기

#### <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

**아이콘** ![뮤텍스 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image37.png)

**설명**

이 이벤트는 tx_mutex_performance_system_info_get을 통해 뮤텍스 시스템 성능 정보를 검색하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="mutex-prioritize"></a>뮤텍스 우선 순위 지정 

#### <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

**아이콘** ![뮤텍스 우선 순위 지정 아이콘](./media/user-guide/tx-events/image38.png)

**설명**

이 이벤트는 tx_mutex_prioritize를 통해 뮤텍스 일시 중단 목록의 우선 순위를 지정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 해당 뮤텍스에 대한 포인터입니다.
- 정보 필드 2: 뮤텍스에 대해 현재 일시 중단된 스레드 수입니다.
- 정보 필드 3: 호출 시의 스택 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="mutex-put"></a>뮤텍스 넣기 

#### <a name="tx_mutex_put"></a>tx_mutex_put

**아이콘** ![뮤텍스 넣기 아이콘](./media/user-guide/tx-events/image39.png)

**설명**

이 이벤트는 tx_mutex_put을 통해 이전에 소유한 뮤텍스를 해제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 해당 뮤텍스에 대한 포인터입니다.
- 정보 필드 2: 뮤텍스를 소유하는 스레드의 포인터입니다.
- 정보 필드 3: 처리 중인 뮤텍스 가져오기 요청 수입니다.
- 정보 필드 4: 호출 시의 스택 포인터입니다.

### <a name="queue-create"></a>큐 만들기 

#### <a name="tx_queue_create"></a>tx_queue_create

**아이콘** ![큐 만들기 아이콘](./media/user-guide/tx-events/image40.png)

**설명**

이 이벤트는 tx_queue_create를 통해 메시지 큐를 만드는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 큐 제어 블록에 대한 포인터입니다.
- 정보 필드 2: 32비트 단어를 기준으로 하는 메시지 크기입니다.
- 정보 필드 3: 큐 메모리 영역의 시작 부분에 대한 포인터입니다.
- 정보 필드 4: 큐 메모리 영역의 바이트 수입니다.

### <a name="queue-delete"></a>큐 삭제 

#### <a name="tx_queue_delete"></a>tx_queue_delete

**아이콘** ![큐 삭제 아이콘](./media/user-guide/tx-events/image41.png)

**설명**

이 이벤트는 tx_queue_delete를 통해 큐를 삭제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 큐에 대한 포인터입니다.
- 정보 필드 2: 호출 시의 스택 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="queue-flush"></a>큐 플러시 

#### <a name="tx_queue_flush"></a>tx_queue_flush

**아이콘** ![큐 플러시 아이콘](./media/user-guide/tx-events/image42.png)

**설명**

이 이벤트는 tx_queue_flush를 통해 큐의 플러시(모든 큐 콘텐츠 지우기)를 나타냅니다.

**정보 필드**

- 정보 필드 1: 큐에 대한 포인터입니다.
- 정보 필드 2: 호출 시의 스택 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="queue-front-send"></a>큐의 맨 앞으로 보내기 

#### <a name="tx_queue_front_send"></a>tx_queue_front_send

**아이콘** ![큐의 맨 앞으로 보내기 아이콘](./media/user-guide/tx-events/image43.png)

**설명**

이 이벤트는 tx_queue_front_send를 통해 큐의 맨 앞으로 메시지를 보내는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 큐에 대한 포인터입니다.
- 정보 필드 2: 메시지의 시작 부분에 대한 포인터입니다.
- 정보 필드 3: tx_queue_front_send 호출에 제공된
- 대기 옵션입니다.
- 정보 필드 4: 이미 큐에 넣은 메시지 수입니다.

### <a name="queue-information-get"></a>큐 정보 가져오기 

#### <a name="tx_queue_info_get"></a>tx_queue_info_get

**아이콘** ![큐 정보 가져오기 아이콘](./media/user-guide/tx-events/image44.png)

**설명**

이 이벤트는 tx_queue_info_get을 통해 큐에 대한 정보를 가져오는 것을 나타냅니다.

**정보 필드** 
- 정보 필드 1: 큐에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="queue-performance-info-get"></a>큐 성능 정보 가져오기 

#### <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

**아이콘** ![큐 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image45.png)

**설명**

이 이벤트는 tx_queue_performance_info_get을 통해 큐에 대한 성능 정보를 가져오는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 큐에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="queue-performance-system-info-get"></a>큐 성능 시스템 정보 가져오기 

#### <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

**아이콘** ![큐 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image46.png)

**설명**

이 이벤트는 시스템에 있는 모든 큐에 대한 시스템 성능 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="queue-prioritize"></a>큐 우선 순위 지정 

#### <a name="tx_queue_prioritize"></a>tx_queue_prioritize

**아이콘** ![큐 우선 순위 지정 아이콘](./media/user-guide/tx-events/image47.png)

**설명**

이 이벤트는 tx_queue_prioritize를 통해 큐 일시 중단 목록의 우선 순위를 지정하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 해당 큐에 대한 포인터입니다.
- 정보 필드 2: 큐에 대해 현재 일시 중단된 스레드 수입니다.
- 정보 필드 3: 호출 시의 스택 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

#### <a name="queue-receive"></a>큐 수신 

##### <a name="tx_queue_receive"></a>tx_queue_receive

**아이콘** ![큐 수신 아이콘](./media/user-guide/tx-events/image48.png)

**설명**

이 이벤트는 tx_queue_receive를 통해 큐에서 메시지를 수신하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 큐에 대한 포인터입니다.
- 정보 필드 2: 메시지의 대상에 대한 포인터입니다. 정보 필드 3: 호출에 제공되는 대기 옵션입니다.
- 정보 필드 4: 현재 큐에 대기 중인 메시지 수입니다.

### <a name="queue-send"></a>큐 송신 

#### <a name="tx_queue_send"></a>tx_queue_send

**아이콘** ![큐 송신 아이콘](./media/user-guide/tx-events/image49.png)

**설명**

이 이벤트는 tx_queue_send를 통해 큐에 메시지를 보내는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 큐에 대한 포인터입니다.
- 정보 필드 2: 메시지에 대한 포인터입니다.
- 정보 필드 3: 호출에 제공되는 대기 옵션입니다.
- 정보 필드 4: 현재 큐에 대기 중인 메시지 수입니다.

### <a name="queue-send-notify"></a>큐 송신 알림 

#### <a name="tx_queue_send_notify"></a>tx_queue_send_notify

**아이콘** ![큐 송신 알림 아이콘](./media/user-guide/tx-events/image50.png)

**설명**

<p>이 이벤트는 메시지를 큐에 보낼 때마다 호출되는 tx_queue_send_notify를 통해 콜백을 등록하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 큐에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="semaphore-ceiling-put"></a>세마포 상한 넣기 

#### <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

**아이콘** ![세마포 상한 넣기 아이콘](./media/user-guide/tx-events/image51.png)

**설명**

이 이벤트는 tx_semaphore_ceiling_put을 통해 세마포에 넣는 것을 나타냅니다. 이는 넣기 작업이 최댓값 또는 상한을 초과할 수 없도록 세마포의 최댓값이 검사된다는 점에서 tx_semaphore_put과 다릅니다.

**정보 필드**

- 정보 필드 1: 세마포에 대한 포인터입니다.
- 정보 필드 2: 현재 세마포 수입니다.
- 정보 필드 3: 세마포에 대해 일시 중단된 스레드 수입니다.
- 정보 필드 4: 호출에 제공된 상한 제한입니다.

#### <a name="semaphore-create"></a>세마포 만들기 

##### <a name="tx_semaphore_create"></a>tx_semaphore_create

**아이콘** ![세마포 만들기 아이콘](./media/user-guide/tx-events/image52.png)

**설명**

이 이벤트는 tx_semaphore_create를 통해 세마포를 만드는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 세마포 제어 블록에 대한 포인터입니다.
- 정보 필드 2: 초기 세마포 수입니다.
- 정보 필드 3: 호출 시의 스택 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="semaphore-delete"></a>세마포 삭제 

#### <a name="tx_semaphore_delete"></a>tx_semaphore_delete

**아이콘** ![세마포 삭제 아이콘](./media/user-guide/tx-events/image53.png)

**설명**

이 이벤트는 tx_semaphore_delete를 통해 세마포를 삭제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 세마포에 대한 포인터입니다.
- 정보 필드 2: 호출 시의 스택 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="semaphore-get"></a>세마포 가져오기 

#### <a name="tx_semaphore_get"></a>tx_semaphore_get

**아이콘** ![세마포 가져오기 아이콘](./media/user-guide/tx-events/image54.png)

**설명**

이 이벤트는 tx_semaphore_get을 통해 세마포를 얻는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 세마포에 대한 포인터입니다.
- 정보 필드 2: 호출에 제공되는 대기 옵션입니다.
- 정보 필드 3: 현재 세마포 수입니다.
- 정보 필드 4: 호출 시의 스택 포인터입니다.

### <a name="semaphore-information-get"></a>세마포 정보 가져오기 

#### <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

**아이콘** ![세마포 정보 가져오기 아이콘](./media/user-guide/tx-events/image55.png)

**설명**

이 이벤트는 tx_semaphore_info_get을 통해 세마포에 대한 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 세마포에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="semaphore-performance-info-get"></a>세마포 성능 정보 가져오기 

#### <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

**아이콘** ![세마포 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image56.png)

**설명**

이 이벤트는 tx_semaphore_performance_info_get을 통해 세마포에 대한 성능 정보를 얻는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 세마포에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="semaphore-performance-system-info"></a>세마포 성능 시스템 정보 

#### <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

**아이콘** ![세마포 성능 시스템 정보 아이콘](./media/user-guide/tx-events/image57.png)

**설명**

이 이벤트는 tx_semaphore_performance_system_info_get을 통해 시스템의 모든 세마포에 대한 성능 정보를 얻는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="semaphore-prioritize"></a>세마포 우선 순위 지정 

#### <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

**아이콘** ![ 세마포 우선 순위 지정 아이콘](./media/user-guide/tx-events/image58.png)

**설명**

이 이벤트는 tx_semaphore_prioritize를 통해 세마포 일시 중단 목록의 우선 순위를 지정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 해당 세마포에 대한 포인터입니다.
- 정보 필드 2: 세마포에 대해 현재 일시 중단된 스레드 수입니다.
- 정보 필드 3: 호출 시의 스택 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="semaphore-put"></a>세마포 넣기 

#### <a name="tx_semaphore_put"></a>tx_semaphore_put

**아이콘** ![세마포 넣기 아이콘](./media/user-guide/tx-events/image59.png)

**설명**

이 이벤트는 tx_semaphore_put을 통해 세마포 인스턴스를 해제하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 해당 세마포에 대한 포인터입니다. 정보 필드 2: 현재 세마포 수입니다.
- 정보 필드 3: 세마포에 대해 일시 중단된 스레드 수입니다.
- 정보 필드 4: 호출 시의 스택 포인터입니다.

### <a name="semaphore-put-notify"></a>세마포 넣기 알림 

#### <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

**아이콘** ![세마포 넣기 알림 아이콘](./media/user-guide/tx-events/image60.png)

**설명**

이 이벤트는 세마포 인스턴스를 넣을 때마다 호출되는 tx_semaphore_put_notify를 통해 콜백을 등록하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 세마포에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="thread-create"></a>스레드 만들기 

#### <a name="tx_thread_create"></a>tx_thread_create

**아이콘** ![스레드 만들기 아이콘](./media/user-guide/tx-events/image61.png)

**설명**

이 이벤트는 tx_thread_create를 통해 스레드를 만드는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 스레드 제어 블록에 대한 포인터입니다.
- 정보 필드 2: 스레드의 우선 순위입니다.
- 정보 필드 3: 스레드에 대한 스택 포인터입니다.
- 정보 필드 4: 스택 크기(바이트)입니다.

### <a name="thread-delete"></a>스레드 삭제 

#### <a name="tx_thread_delete"></a>tx_thread_delete

**아이콘** ![스레드 삭제 아이콘](./media/user-guide/tx-events/image62.png)

**설명**

이 이벤트는 tx_thread_delete를 통해 스레드를 삭제하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 스레드에 대한 포인터입니다.
- 정보 필드 2: 호출 시의 스택 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="thread-entryexit-notify"></a>스레드 진입/종료 알림 

#### <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

**아이콘** ![스레드 진입/종료 알림 아이콘](./media/user-guide/tx-events/image63.png)

**설명**

이 이벤트는 스레드가 진입되거나 종료될 때마다 호출되는 tx_thread_entry_exit_notify를 통해 콜백을 등록하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 스레드에 대한 포인터입니다.
- 정보 필드 2: 등록 시 스레드 상태입니다.
- 정보 필드 3: 호출 시 스택에 대한 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

#### <a name="thread-identify"></a>스레드 식별 

##### <a name="tx_thread_identify"></a>tx_thread_identify

**아이콘** ![스레드 식별 아이콘](./media/user-guide/tx-events/image64.png)

**설명**

이 이벤트는 tx_thread_identify를 통해 현재 스레드 포인터를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="thread-information-get"></a>스레드 정보 가져오기 

#### <a name="tx_thread_info_get"></a>tx_thread_info_get

**아이콘** ![스레드 정보 가져오기 아이콘](./media/user-guide/tx-events/image65.png)

**설명**

이 이벤트는 tx_thread_info_get을 통해 지정된 스레드에 대한 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 스레드에 대한 포인터입니다.
- 정보 필드 2: 호출 시 스레드 상태입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

#### <a name="thread-performance-information-get"></a>스레드 성능 정보 가져오기 

##### <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

**아이콘** ![스레드 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image66.png)

**설명**

이 이벤트는 tx_thread_performance_info_get을 통해 지정된 스레드에 대한 성능 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 스레드에 대한 포인터입니다.
- 정보 필드 2: 호출 시 스레드 상태입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="thread-performance-system-info-get"></a>스레드 성능 시스템 정보 가져오기 

#### <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

**아이콘** ![스레드 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image67.png)

**설명**

이 이벤트는 tx_thread_performance_system_info_get을 통해 모든 스레드에 대한 성능 정보를 가져오는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="thread-preemption-change"></a>스레드 선점 변경 

#### <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

**아이콘** ![스레드 선점 변경 아이콘](./media/user-guide/tx-events/image68.png)

**설명**

이 이벤트는 tx_thread_preemption_change를 통해 스레드의 선점 임계값을 변경하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 스레드에 대한 포인터입니다.
- 정보 필드 2: 새 선점 임계값입니다.
- 정보 필드 3: 이전 선점 임계값입니다.
- 정보 필드 4: 호출 시 스레드의 상태입니다.

### <a name="thread-priority-change"></a>스레드 우선 순위 변경 

#### <a name="tx_thread_priority_change"></a>tx_thread_priority_change

**아이콘** ![스레드 우선 순위 변경 아이콘](./media/user-guide/tx-events/image69.png)

**설명**

이 이벤트는 tx_thread_priority_change를 통해 스레드의 우선 순위를 변경하는 것을 나타냅니다.

- 정보 필드 
- 정보 필드 1: 스레드에 대한 포인터입니다.
- 정보 필드 2: 새 우선 순위입니다.
- 정보 필드 3: 이전 우선 순위입니다.
- 정보 필드 4: 호출 시 스레드의 상태입니다.

### <a name="thread-relinquish"></a>스레드 양도 

#### <a name="tx_thread_relinquish"></a>tx_thread_relinquish

**아이콘** ![스레드 양도 아이콘](./media/user-guide/tx-events/image70.png)

**설명**

이 이벤트는 tx_thread_relinquish를 통해 스레드에서 프로세서를 양도하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 호출 시의 스택 포인터입니다.
- 정보 필드 2: 실행할 다음 스레드에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="thread-reset"></a>스레드 재설정 

#### <a name="tx_thread_reset"></a>tx_thread_reset

**아이콘** ![스레드 재설정 아이콘](./media/user-guide/tx-events/image71.png)

**설명**

이 이벤트는 tx_thread_reset을 통해 완료되었거나 종료된 스레드를 재설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 스레드에 대한 포인터입니다.
- 정보 필드 2: 호출 시 스레드의 상태입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

#### <a name="thread-resume"></a>스레드 다시 시작 

##### <a name="tx_thread_resume"></a>tx_thread_resume

**아이콘** ![스레드 다시 시작 아이콘](./media/user-guide/tx-events/image72.png)

**설명**

이 이벤트는 tx_thread_resume을 통해 일시 중단된 스레드를 다시 시작하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 스레드에 대한 포인터입니다.
- 정보 필드 2: 호출 시 스레드의 상태입니다.
- 정보 필드 3: 호출 시의 스택 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="thread-sleep"></a>스레드 대기 

#### <a name="tx_thread_sleep"></a>tx_thread_sleep

**아이콘** ![스레드 대기 아이콘](./media/user-guide/tx-events/image73.png)

**설명**

이 이벤트는 tx_thread_sleep을 통해 지정된 수의 타이머 틱에 대해 현재 스레드를 일시 중단하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 일시 중단할 틱 수입니다.
- 정보 필드 2: 호출 시 스레드의 상태입니다.
- 정보 필드 3: 호출 시의 스택 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="thread-stack-error-notify"></a>스레드 스택 오류 알림 

#### <a name="tx_thread_stack_error_notify_event"></a>tx_thread_stack_error_notify_event

**아이콘** ![스레드 스택 오류 알림 아이콘](./media/user-guide/tx-events/image74.png)

**설명**

이 이벤트는 tx_thread_stack_error_notify_event를 통해 스레드 스택 오류 알림 루틴을 등록하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="thread-suspend"></a>스레드 일시 중단 

#### <a name="tx_thread_suspend"></a>tx_thread_suspend

**아이콘** ![스레드 일시 중단 아이콘](./media/user-guide/tx-events/image75.png)

**설명**

이 이벤트는 tx_thread_suspend를 통해 스레드를 일시 중단하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 일시 중단할 스레드에 대한 포인터입니다.
- 정보 필드 2: 호출 시 스레드의 상태입니다.
- 정보 필드 3: 호출 시의 스택 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="thread-terminate"></a>스레드 종료 

#### <a name="tx_thread_terminate"></a>tx_thread_terminate

**아이콘** ![스레드 종료 아이콘](./media/user-guide/tx-events/image76.png)

**설명**

이 이벤트는 tx_thread_terminate를 통해 스레드를 종료하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 종료할 스레드에 대한 포인터입니다.
- 정보 필드 2: 호출 시 스레드의 상태입니다.
- 정보 필드 3: 호출 시의 스택 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="thread-time-slice-change"></a>스레드 시간 조각 변경 

#### <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

**아이콘** ![스레드 시간 조각 변경 아이콘](./media/user-guide/tx-events/image77.png)

**설명**

이 이벤트는 tx_thread_time_slice_change를 통해 스레드의 시간 조각을 변경하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 스레드에 대한 포인터입니다.
- 정보 필드 2: 새 시간 조각입니다.
- 정보 필드 3: 이전 시간 조각입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="thread-wait-abort"></a>스레드 대기 중단 

#### <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

**아이콘** ![스레드 대기 중단 아이콘](./media/user-guide/tx-events/image78.png)

**설명**

이 이벤트는 tx_thread_wait_abort를 통해 스레드의 일시 중단을 중단하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 스레드에 대한 포인터입니다.
- 정보 필드 2: 호출 시 스레드의 상태입니다.
- 정보 필드 3: 호출 시의 스택 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="time-get"></a>시간 가져오기 

#### <a name="tx_time_get"></a>tx_time_get

**아이콘** ![시간 가져오기 아이콘](./media/user-guide/tx-events/image79.png)

**설명**

이 이벤트는 tx_time_get을 통해 현재 타이머 틱 수를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 현재 타이머 틱 수입니다.
- 정보 필드 2: 호출 시의 스택 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="time-set"></a>시간 설정 

#### <a name="tx_time_set"></a>tx_time_set

**아이콘** ![시간 설정 아이콘](./media/user-guide/tx-events/image80.png)

**설명**

이 이벤트는 tx_time_set을 통해 현재 타이머 틱 수를 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 새 타이머 틱 수입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="timer-activate"></a>타이머 활성화 

#### <a name="tx_timer_activate"></a>tx_timer_activate

**아이콘** ![타이머 활성화 아이콘](./media/user-guide/tx-events/image81.png)

**설명**

이 이벤트는 tx_timer_activate를 통해 지정된 타이머를 활성화하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 타이머에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="timer-change"></a>타이머 변경 

#### <a name="tx_timer_change"></a>tx_timer_change

**아이콘** ![타이머 변경 아이콘](./media/user-guide/tx-events/image82.png)

**설명**

이 이벤트는 tx_timer_change를 통해 지정된 타이머를 변경하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 타이머에 대한 포인터입니다.
- 정보 필드 2: 초기 만료 틱입니다.
- 정보 필드 3: 만료 틱을 다시 예약합니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="timer-create"></a>타이머 만들기 

#### <a name="tx_timer_create"></a>tx_timer_create

**아이콘** ![타이머 만들기 아이콘](./media/user-guide/tx-events/image83.png)

**설명**

이 이벤트는 tx_timer_create를 통해 타이머를 만드는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 타이머 제어 블록에 대한 포인터입니다.
- 정보 필드 2: 초기 만료 틱입니다.
- 정보 필드 3: 만료 틱을 다시 예약합니다.
- 정보 필드 4: 자동 사용 값인 TX_AUTO_ACTIVATE (1) 또는 TX_NO_ACTIVATE (0)입니다.

### <a name="timer-deactivate"></a>타이머 비활성화 

#### <a name="tx_timer_deactivate"></a>tx_timer_deactivate

**아이콘** ![타이머 비활성화 아이콘](./media/user-guide/tx-events/image84.png)

**설명**

이 이벤트는 tx_timer_deactivate를 통한 타이머 비활성화를 나타냅니다.

**정보 필드**

- 정보 필드 1: 타이머에 대한 포인터입니다.
- 정보 필드 2: 호출 시의 스택 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="timer-delete"></a>타이머 삭제 

#### <a name="tx_timer_delete"></a>tx_timer_delete

**아이콘** ![타이머 삭제 아이콘](./media/user-guide/tx-events/image85.png)

**설명**

이 이벤트는 tx_timer_delete를 통해 타이머를 삭제하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 타이머에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="timer-information-get"></a>타이머 정보 가져오기 

#### <a name="tx_timer_info_get"></a>tx_timer_info_get

**아이콘** ![타이머 정보 가져오기 아이콘](./media/user-guide/tx-events/image86.png)

**설명**

이 이벤트는 tx_timer_info_get을 통해 타이머 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 타이머에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="timer-performance-information-get"></a>타이머 성능 정보 가져오기 

#### <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

**아이콘** ![타이머 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image87.png)

**설명** 

이 이벤트는 tx_timer_performance_info_get을 통해 타이머 성능 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 타이머에 대한 포인터입니다.
- 정보 필드 2: 호출 시의 스택 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="timer-system-performance-info-get"></a>타이머 시스템 성능 정보 가져오기 

#### <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

**아이콘** ![타이머 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image88.png)


**설명** 

이 이벤트는 tx_timer_performance_system_info_get을 통해 모든 타이머 성능 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.