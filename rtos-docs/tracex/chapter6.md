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
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a><span data-ttu-id="eecd5-103">6장 - Azure RTOS ThreadX 추적 이벤트</span><span class="sxs-lookup"><span data-stu-id="eecd5-103">Chapter 6 - Azure RTOS ThreadX trace events</span></span>

<span data-ttu-id="eecd5-104">이 장에서는 Azure RTOS ThreadX 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-104">This chapter describes the Azure RTOS ThreadX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="eecd5-105">이벤트 및 아이콘 목록</span><span class="sxs-lookup"><span data-stu-id="eecd5-105">List of Events and Icons</span></span>

<span data-ttu-id="eecd5-106">다음은 TraceX에 의해 표시되는 ThreadX 이벤트 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-106">The following is a list of ThreadX events displayed by TraceX:</span></span>

| <span data-ttu-id="eecd5-107">**아이콘**</span><span class="sxs-lookup"><span data-stu-id="eecd5-107">**Icon**</span></span>                         | <span data-ttu-id="eecd5-108">**의미**</span><span class="sxs-lookup"><span data-stu-id="eecd5-108">**Meaning**</span></span> |
| -------------------------------- | ------------------------------------- |
| ![내부 스레드 다시 시작 아이콘](./media/user-guide/tx-events/image1.png)    | <span data-ttu-id="eecd5-110">내부 스레드 다시 시작</span><span class="sxs-lookup"><span data-stu-id="eecd5-110">Internal thread resume</span></span>  |
| ![내부 스레드 일시 중단 아이콘](./media/user-guide/tx-events/image2.png)    | <span data-ttu-id="eecd5-112">내부 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="eecd5-112">Internal thread suspend</span></span> |
| ![인터럽트 서비스 루틴 들어가기 아이콘](./media/user-guide/tx-events/image3.png)    | <span data-ttu-id="eecd5-114">ISR(인터럽트 서비스 루틴) 들어가기</span><span class="sxs-lookup"><span data-stu-id="eecd5-114">Interrupt Service Routine (ISR) Enter</span></span> |
| ![인터럽트 서비스 루틴 끝내기 아이콘](./media/user-guide/tx-events/image4.png)    | <span data-ttu-id="eecd5-116">ISR(인터럽트 서비스 루틴) 끝내기</span><span class="sxs-lookup"><span data-stu-id="eecd5-116">Interrupt Service Routine (ISR) Exit</span></span>  |
| ![내부 시간 조각 아이콘](./media/user-guide/tx-events/image5.png)    | <span data-ttu-id="eecd5-118">내부 시간 조각</span><span class="sxs-lookup"><span data-stu-id="eecd5-118">Internal time-slice</span></span> |
| ![실행 아이콘](./media/user-guide/tx-events/image6.png)    | <span data-ttu-id="eecd5-120">실행 중</span><span class="sxs-lookup"><span data-stu-id="eecd5-120">Running</span></span> |
| ![블록 풀 할당 아이콘](./media/user-guide/tx-events/image7.png)    | <span data-ttu-id="eecd5-122">**블록 풀 할당**(*tx_block_allocate*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-122">**Block pool allocate** (*tx_block_allocate*)</span></span>  |
| ![블록 풀 만들기 아이콘](./media/user-guide/tx-events/image8.png)    | <span data-ttu-id="eecd5-124">**블록 풀 만들기**(*tx_block_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-124">**Block pool create** (*tx_block_pool_create*)</span></span> |
| ![블록 풀 삭제 아이콘](./media/user-guide/tx-events/image9.png)    | <span data-ttu-id="eecd5-126">**블록 풀 삭제**(*tx_block_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-126">**Block pool delete** (*tx_block_pool_delete*)</span></span> |
| ![블록 풀 정보 가져오기 아이콘](./media/user-guide/tx-events/image10.png)    | <span data-ttu-id="eecd5-128">**블록 풀 정보 가져오기**(*tx_block_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-128">**Block pool information get** (*tx_block_pool_info_get*)</span></span> |
| ![블록 풀 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image11.png)    | <span data-ttu-id="eecd5-130">**블록 풀 성능 정보 가져오기**(*tx_block_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-130">**Block pool performance information get** (*tx_block_pool_performance_info_get*)</span></span> |
| ![블록 풀 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image12.png)    | <span data-ttu-id="eecd5-132">**블록 풀 시스템 성능 정보 가져오기**(*tx_block_pool_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-132">**Block pool system performance information get** (*tx_block_pool_performance_system_info_get*)</span></span> |
| ![블록 풀 우선 순위 지정 아이콘](./media/user-guide/tx-events/image13.png)    | <span data-ttu-id="eecd5-134">**블록 풀 우선 순위 지정**(*tx_block_pool_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-134">**Block pool prioritize** (*tx_block_pool_prioritize*)</span></span> |
| ![풀에 대한 블록 해제 아이콘](./media/user-guide/tx-events/image14.png)    | <span data-ttu-id="eecd5-136">**풀에 대한 블록 해제**(*tx_block_release*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-136">**Block release to pool** (*tx_block_release*)</span></span> |
| ![메모리 바이트 풀 할당 아이콘](./media/user-guide/tx-events/image15.png)    | <span data-ttu-id="eecd5-138">**메모리 바이트 풀 할당**(*tx_byte_allocate*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-138">**Byte pool allocate memory** (*tx_byte_allocate*)</span></span> |
| ![바이트 풀 만들기 아이콘](./media/user-guide/tx-events/image16.png)    | <span data-ttu-id="eecd5-140">**바이트 풀 만들기**(*tx_byte_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-140">**Byte pool create** (*tx_byte_pool_create*)</span></span> |
| ![바이트 풀 삭제 아이콘](./media/user-guide/tx-events/image17.png)    | <span data-ttu-id="eecd5-142">**바이트 풀 삭제**(*tx_byte_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-142">**Byte pool delete** (*tx_byte_pool_delete*)</span></span> |
| ![바이트 풀 정보 가져오기 아이콘](./media/user-guide/tx-events/image18.png)    | <span data-ttu-id="eecd5-144">**바이트 풀 정보 가져오기**(*tx_byte_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-144">**Byte pool information get** (*tx_byte_pool_info_get*)</span></span> |
| ![바이트 풀 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image19.png)    | <span data-ttu-id="eecd5-146">**바이트 풀 성능 정보 가져오기**(*tx_byte_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-146">**Byte pool performance information get** (*tx_byte_pool_performance_info_get*)</span></span> |
| ![바이트 풀 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image20.png)    | <span data-ttu-id="eecd5-148">**바이트 풀 시스템 성능 정보 가져오기**(*tx_byte_pool_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-148">**Byte pool system performance information get** (*tx_byte_pool_performance_system_info_get*)</span></span> |
| ![\*바이트 풀 우선 순위 지정 아이콘](./media/user-guide/tx-events/image21.png)    | <span data-ttu-id="eecd5-150">**바이트 풀 우선 순위 지정**(*tx_byte_pool_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-150">**Byte pool prioritize** (*tx_byte_pool_prioritize*)</span></span> |
| ![풀에 대한 바이트 메모리 해제 아이콘](./media/user-guide/tx-events/image22.png)    | <span data-ttu-id="eecd5-152">**풀에 대한 바이트 메모리 해제**(*tx_byte_release*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-152">**Byte memory release to pool** (*tx_byte_release*)</span></span> |
| ![이벤트 플래그 만들기 아이콘](./media/user-guide/tx-events/image23.png)    | <span data-ttu-id="eecd5-154">**이벤트 플래그 만들기**(*tx_event_flags_create*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-154">**Event flags create** (*tx_event_flags_create*)</span></span> |
| ![이벤트 플래그 삭제 아이콘](./media/user-guide/tx-events/image24.png)    | <span data-ttu-id="eecd5-156">**이벤트 플래그 삭제**(*tx_event_flags_delete*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-156">**Event flags delete** (*tx_event_flags_delete*)</span></span> |
| ![이벤트 플래그 가져오기 아이콘](./media/user-guide/tx-events/image25.png)    | <span data-ttu-id="eecd5-158">**이벤트 플래그 가져오기**(*tx_event_flags_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-158">**Event flags get** (*tx_event_flags_get*)</span></span> |
| ![이벤트 플래그 정보 가져오기 아이콘](./media/user-guide/tx-events/image26.png)    | <span data-ttu-id="eecd5-160">**이벤트 플래그 정보 가져오기**(*tx_event_flags_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-160">**Event flags information get** (*tx_event_flags_info_get*)</span></span> |
| ![이벤트 플래그 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image27.png)    | <span data-ttu-id="eecd5-162">**이벤트 플래그 성능 정보 가져오기**(*tx_event_flags_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-162">**Event flags performance information get** (*tx_event_flags_performance_info_get*)</span></span> |
| ![이벤트 플래그 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image28.png)    | <span data-ttu-id="eecd5-164">**이벤트 플래그 시스템 성능 정보 가져오기**(*tx_event_flags_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-164">**Event flags system performance information get** (*tx_event_flags_performance_system_info_get*)</span></span> |
| ![이벤트 플래그 설정 아이콘](./media/user-guide/tx-events/image29.png)    | <span data-ttu-id="eecd5-166">**이벤트 플래그 설정**(*tx_event_flags_set*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-166">**Event flags set** (*tx_event_flags_set*)</span></span> |
| ![이벤트 플래그 설정 알림 아이콘](./media/user-guide/tx-events/image30.png)    | <span data-ttu-id="eecd5-168">**이벤트 플래그 설정 알림**(*tx_event_flags_set_notify*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-168">**Event flags set notify** (*tx_event_flags_set_notify*)</span></span> |
| ![인터럽트 사용/사용 안 함 아이콘](./media/user-guide/tx-events/image31.png)    | <span data-ttu-id="eecd5-170">**인터럽트 사용/사용 안 함**(*tx_interrupt_control*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-170">**Interrupt enable/disable** (*tx_interrupt_control*)</span></span> |
| ![뮤텍스 만들기 아이콘](./media/user-guide/tx-events/image32.png)    | <span data-ttu-id="eecd5-172">**뮤텍스 만들기**(*tx_mutex_create*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-172">**Mutex create** (*tx_mutex_create*)</span></span> |
| ![뮤텍스 삭제 아이콘](./media/user-guide/tx-events/image33.png)    | <span data-ttu-id="eecd5-174">**뮤텍스 삭제**(*tx_mutex_delete*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-174">**Mutex delete** (*tx_mutex_delete*)</span></span> |
| ![뮤텍스 가져오기 아이콘](./media/user-guide/tx-events/image34.png)    | <span data-ttu-id="eecd5-176">**뮤텍스 가져오기**(*tx_mutex_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-176">**Mutex get** (*tx_mutex_get*)</span></span> |
| ![뮤텍스 정보 가져오기 아이콘](./media/user-guide/tx-events/image35.png)    | <span data-ttu-id="eecd5-178">**뮤텍스 정보 가져오기**(*tx_mutex_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-178">**Mutex information get** (*tx_mutex_info_get*)</span></span> |
| ![뮤텍스 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image36.png)    | <span data-ttu-id="eecd5-180">**뮤텍스 성능 정보 가져오기**(*tx_mutex_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-180">**Mutex performance information get** (*tx_mutex_performance_info_get*)</span></span> |
| ![뮤텍스 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image37.png)    | <span data-ttu-id="eecd5-182">**뮤텍스 시스템 성능 정보 가져오기**(*tx_mutex_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-182">**Mutex system performance information get** (*tx_mutex_performance_system_info_get*)</span></span> |
| ![뮤텍스 우선 순위 지정 아이콘](./media/user-guide/tx-events/image38.png)    | <span data-ttu-id="eecd5-184">**뮤텍스 우선 순위 지정**(*tx_mutex_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-184">**Mutex prioritize** (*tx_mutex_prioritize*)</span></span> |
| ![뮤텍스 넣기 아이콘](./media/user-guide/tx-events/image39.png)    | <span data-ttu-id="eecd5-186">**뮤텍스 넣기**(*tx_mutex_put*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-186">**Mutex put** (*tx_mutex_put*)</span></span> |
| ![큐 만들기 아이콘](./media/user-guide/tx-events/image40.png)    | <span data-ttu-id="eecd5-188">**큐 만들기**(*tx_queue_create*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-188">**Queue create** (*tx_queue_create*)</span></span> |
| ![큐 삭제 아이콘](./media/user-guide/tx-events/image41.png)    | <span data-ttu-id="eecd5-190">**큐 삭제**(*tx_queue_delete*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-190">**Queue delete** (*tx_queue_delete*)</span></span> |
| ![큐 플러시 아이콘](./media/user-guide/tx-events/image42.png)    | <span data-ttu-id="eecd5-192">**큐 플러시**(*tx_queue_flush*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-192">**Queue flush** (*tx_queue_flush*)</span></span> |
| ![큐의 맨 앞으로 보내기 아이콘](./media/user-guide/tx-events/image43.png)    | <span data-ttu-id="eecd5-194">**큐의 맨 앞으로 보내기**(*tx_queue_front_send*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-194">**Queue front send** (*tx_queue_front_send*)</span></span> |
| ![큐 정보 가져오기 아이콘](./media/user-guide/tx-events/image44.png)    | <span data-ttu-id="eecd5-196">**큐 정보 가져오기**(*tx_queue_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-196">**Queue information get** (*tx_queue_info_get*)</span></span> |
| ![큐 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image45.png)    | <span data-ttu-id="eecd5-198">**큐 성능 정보 가져오기**(*tx_queue_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-198">**Queue performance information get** (*tx_queue_performance_info_get*)</span></span> |
| ![큐 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image46.png)    | <span data-ttu-id="eecd5-200">**큐 시스템 성능 정보 가져오기**(*tx_queue_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-200">**Queue system performance information get** (*tx_queue_performance_system_info_get*)</span></span> |
| ![큐 우선 순위 지정 아이콘](./media/user-guide/tx-events/image47.png)    | <span data-ttu-id="eecd5-202">**큐 우선 순위 지정**(*tx_queue_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-202">**Queue prioritize** (*tx_queue_prioritize*)</span></span> |
| ![큐 수신 메시지 아이콘](./media/user-guide/tx-events/image48.png)    | <span data-ttu-id="eecd5-204">**큐 수신 메시지**(*tx_queue_receive*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-204">**Queue receive message** (*tx_queue_receive*)</span></span> |
| ![큐 송신 메시지 아이콘](./media/user-guide/tx-events/image49.png)    | <span data-ttu-id="eecd5-206">**큐 송신 메시지**(*tx_queue_send*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-206">**Queue send message** (*tx_queue_send*)</span></span> |
| ![큐 송신 알림 아이콘](./media/user-guide/tx-events/image50.png)    | <span data-ttu-id="eecd5-208">**큐 송신 알림**(*tx_queue_send_notify*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-208">**Queue send notify** (*tx_queue_send_notify*)</span></span> |
| ![세마포 상한 넣기 아이콘](./media/user-guide/tx-events/image51.png)    | <span data-ttu-id="eecd5-210">**세마포 상한 넣기**(*tx_semaphore_ceiling_put*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-210">**Semaphore ceiling put** (*tx_semaphore_ceiling_put*)</span></span> |
| ![세마포 만들기 아이콘](./media/user-guide/tx-events/image52.png)    | <span data-ttu-id="eecd5-212">**세마포 만들기**(*tx_semaphore_create*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-212">**Semaphore create** (*tx_semaphore_create*)</span></span> |
| ![세마포 삭제 아이콘](./media/user-guide/tx-events/image53.png)    | <span data-ttu-id="eecd5-214">**세마포 삭제**(*tx_semaphore_delete*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-214">**Semaphore delete** (*tx_semaphore_delete*)</span></span> |
| ![세마포 가져오기 아이콘](./media/user-guide/tx-events/image54.png)    | <span data-ttu-id="eecd5-216">**세마포 가져오기**(*tx_semaphore_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-216">**Semaphore get** (*tx_semaphore_get*)</span></span> |
| ![세마포 정보 가져오기 아이콘](./media/user-guide/tx-events/image55.png)    | <span data-ttu-id="eecd5-218">**세마포 정보 가져오기**(*tx_semaphore_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-218">**Semaphore information get** (*tx_semaphore_info_get*)</span></span> |
| ![세마포 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image56.png)    | <span data-ttu-id="eecd5-220">**세마포 성능 정보 가져오기**(*tx_semaphroe_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-220">**Semaphore performance information get** (*tx_semaphroe_performance_info_get*)</span></span> |
| ![세마포 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image57.png)    | <span data-ttu-id="eecd5-222">**세마포 시스템 성능 정보 가져오기**(*tx_semaphore_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-222">**Semaphore system performance information get** (*tx_semaphore_performance_system_info_get*)</span></span> |
| ![세마포 우선 순위 지정 아이콘](./media/user-guide/tx-events/image58.png)    | <span data-ttu-id="eecd5-224">**세마포 우선 순위 지정**(*tx_semaphore_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-224">**Semaphore prioritize** (*tx_semaphore_prioritize*)</span></span> |
| ![세마포 넣기 아이콘](./media/user-guide/tx-events/image59.png)    | <span data-ttu-id="eecd5-226">**세마포 넣기**(*tx_semaphore_put*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-226">**Semaphore put** (*tx_semaphore_put*)</span></span> |
| ![세마포 넣기 알림 아이콘](./media/user-guide/tx-events/image60.png)    | <span data-ttu-id="eecd5-228">**세마포 넣기 알림**(*tx_semaphore_put_notify*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-228">**Semaphore put notify** (*tx_semaphore_put_notify*)</span></span> |
| ![스레드 만들기 아이콘](./media/user-guide/tx-events/image61.png)    | <span data-ttu-id="eecd5-230">**스레드 만들기**(*tx_thread_create*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-230">**Thread create** (*tx_thread_create*)</span></span> |
| ![스레드 삭제 아이콘](./media/user-guide/tx-events/image62.png)    | <span data-ttu-id="eecd5-232">**스레드 삭제**(*tx_thread_delete*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-232">**Thread delete** (*tx_thread_delete*)</span></span> |
| ![스레드 종료/진입 아이콘](./media/user-guide/tx-events/image63.png)    | <span data-ttu-id="eecd5-234">**스레드 종료/진입 알림**(*tx_thread_entry_exit_notify*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-234">**Thread exit/entry notify** (*tx_thread_entry_exit_notify*)</span></span> |
| ![스레드 식별 아이콘](./media/user-guide/tx-events/image64.png)    | <span data-ttu-id="eecd5-236">**스레드 식별**(*tx_thread_identify*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-236">**Thread identify** (*tx_thread_identify*)</span></span> |
| ![스레드 정보 가져오기 아이콘](./media/user-guide/tx-events/image65.png)    | <span data-ttu-id="eecd5-238">**스레드 정보 가져오기**(*tx_thread_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-238">**Thread information get** (*tx_thread_info_get*)</span></span> |
| ![스레드 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image66.png)    | <span data-ttu-id="eecd5-240">**스레드 성능 정보 가져오기**(*tx_thread_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-240">**Thread performance information get** (*tx_thread_performance_info_get*)</span></span> |
| ![스레드 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image67.png)    | <span data-ttu-id="eecd5-242">**스레드 성능 시스템 정보 가져오기**(*tx_thread_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-242">**Thread performance system information get** (*tx_thread_performance_system_info_get*)</span></span> |
| ![스레드 선점 변경 아이콘](./media/user-guide/tx-events/image68.png)    | <span data-ttu-id="eecd5-244">**스레드 선점 변경**(*tx_thread_preemption_change*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-244">**Thread preemption change** (*tx_thread_preemption_change*)</span></span> |
| ![스레드 우선 순위 변경 아이콘](./media/user-guide/tx-events/image69.png)    | <span data-ttu-id="eecd5-246">**스레드 우선 순위 변경**(*tx_thread_priority_change*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-246">**Thread priority change** (*tx_thread_priority_change*)</span></span> |
| ![스레드 양도 아이콘](./media/user-guide/tx-events/image70.png)    | <span data-ttu-id="eecd5-248">**스레드 양도**(*tx_thread_relinquish*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-248">**Thread relinquish** (*tx_thread_relinquish*)</span></span> |
| ![스레드 재설정 아이콘](./media/user-guide/tx-events/image71.png)    | <span data-ttu-id="eecd5-250">**스레드 재설정**(*tx_thread_reset*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-250">**Thread reset** (*tx_thread_reset*)</span></span> |
| ![\*스레드 다시 시작 아이콘](./media/user-guide/tx-events/image72.png)    | <span data-ttu-id="eecd5-252">**스레드 다시 시작**(\**tx_thread_resume*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-252">**Thread resume** (\**tx_thread_resume*)</span></span> |
| ![스레드 일시 중지 아이콘](./media/user-guide/tx-events/image73.png)    | <span data-ttu-id="eecd5-254">**스레드 일시 중지**(*tx_thread_sleep*)\*</span><span class="sxs-lookup"><span data-stu-id="eecd5-254">**Thread Sleep** (*tx_thread_sleep*)\*</span></span> |
| ![스레드 스택 오류 알림 아이콘](./media/user-guide/tx-events/image74.png)    | <span data-ttu-id="eecd5-256">**스레드 스택 오류 알림**(*tx_thread_stack_error_notify*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-256">**Thread stack error notify** (*tx_thread_stack_error_notify*)</span></span> |
| ![스레드 일시 중단 아이콘](./media/user-guide/tx-events/image75.png)    | <span data-ttu-id="eecd5-258">**스레드 일시 중단**(*tx_thread_suspend*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-258">**Thread suspend** (*tx_thread_suspend*)</span></span> |
| ![스레드 종료 아이콘](./media/user-guide/tx-events/image76.png)    | <span data-ttu-id="eecd5-260">**스레드 종료**(*tx_thread_terminate*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-260">**Thread terminate** (*tx_thread_terminate*)</span></span> |
| ![스레드 시간 조각 변경 아이콘](./media/user-guide/tx-events/image77.png)    | <span data-ttu-id="eecd5-262">**스레드 시간 조각 변경**(*tx_thread_time_slice_change*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-262">**Thread time-slice change** (*tx_thread_time_slice_change*)</span></span> |
| ![스레드 대기 중단 아이콘](./media/user-guide/tx-events/image78.png)    | <span data-ttu-id="eecd5-264">**스레드 대기 중단**(*tx_thread_wait_abort*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-264">**Thread wait abort** (*tx_thread_wait_abort*)</span></span> |
| ![시간 가져오기 아이콘](./media/user-guide/tx-events/image79.png)    | <span data-ttu-id="eecd5-266">**시간 가져오기**(*tx_time_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-266">**Time get** (*tx_time_get*)</span></span> |
| ![시간 설정 아이콘](./media/user-guide/tx-events/image80.png)    | <span data-ttu-id="eecd5-268">**시간 설정**(*tx_time_set*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-268">**Time set** (*tx_time_set*)</span></span> |
| ![타이머 활성화 아이콘](./media/user-guide/tx-events/image81.png)    | <span data-ttu-id="eecd5-270">**타이머 활성화**(*tx_timer_activate*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-270">**Timer activate** (*tx_timer_activate*)</span></span> |
| ![타이머 변경 아이콘](./media/user-guide/tx-events/image82.png)    | <span data-ttu-id="eecd5-272">**타이머 변경**(*tx_timer_change*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-272">**Timer change** (*tx_timer_change*)</span></span> |
| ![타이머 만들기 아이콘](./media/user-guide/tx-events/image83.png)    | <span data-ttu-id="eecd5-274">**타이머 만들기**(*tx_timer_create*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-274">**Timer create** (*tx_timer_create*)</span></span> |
| ![타이머 비활성화 아이콘](./media/user-guide/tx-events/image84.png)    | <span data-ttu-id="eecd5-276">**타이머 비활성화**(*tx_timer_deactivate*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-276">**Timer deactivate** (*tx_timer_deactivate*)</span></span> |
| ![타이머 삭제 아이콘](./media/user-guide/tx-events/image85.png)    | <span data-ttu-id="eecd5-278">**타이머 삭제**(*tx_timer_delete*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-278">**Timer delete** (*tx_timer_delete*)</span></span> |
| ![타이머 정보 가져오기 아이콘](./media/user-guide/tx-events/image86.png)    | <span data-ttu-id="eecd5-280">**타이머 정보 가져오기**(*tx_timer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-280">**Timer information get** (*tx_timer_info_get*)</span></span> |
| ![타이머 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image87.png)    | <span data-ttu-id="eecd5-282">**타이머 성능 정보 가져오기**(*tx_timer_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-282">**Timer performance information get** (*tx_timer_performance_info_get*)</span></span> |
| ![\*타이머 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image88.png)    | <span data-ttu-id="eecd5-284">**타이머 성능 시스템 정보 가져오기**(*tx_timer_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="eecd5-284">**Timer performance system information get** (*tx_timer_performance_system_info_get*)</span></span> |
| ![사용자 정의 이벤트 아이콘](./media/user-guide/tx-events/image0.png)    | <span data-ttu-id="eecd5-286">**사용자 정의 이벤트**(10장 참조)</span><span class="sxs-lookup"><span data-stu-id="eecd5-286">**User-Defined Event** (See Chapter 10)</span></span>    |

## <a name="event-descriptions"></a><span data-ttu-id="eecd5-287">이벤트 설명</span><span class="sxs-lookup"><span data-stu-id="eecd5-287">Event Descriptions</span></span>

### <a name="internal-thread-resume"></a><span data-ttu-id="eecd5-288">내부 스레드 다시 시작</span><span class="sxs-lookup"><span data-stu-id="eecd5-288">Internal thread resume</span></span>

#### <a name="internal-thread-resume"></a><span data-ttu-id="eecd5-289">내부 스레드 다시 시작</span><span class="sxs-lookup"><span data-stu-id="eecd5-289">Internal thread resume</span></span>

<span data-ttu-id="eecd5-290">**아이콘** ![내부 스레드 다시 시작 아이콘](./media/user-guide/tx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-290">**Icon** ![Internal thread resume icon](./media/user-guide/tx-events/image1.png)</span></span>

<span data-ttu-id="eecd5-291">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-291">**Description**</span></span>

<span data-ttu-id="eecd5-292">이 이벤트는 스레드 실행을 다시 시작하는 ThreadX의 내부 처리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-292">This event represents the internal processing in ThreadX that resumes a thread for execution.</span></span> <span data-ttu-id="eecd5-293">지정된 스레드가 가장 높은 우선 순위이고 선점 임계값의 실행이 차단되지 않는 경우 시스템에서 새로 준비된 스레드 실행을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-293">If the specified thread is the highest priority and preemption-threshold does not block its execution, the system will start executing this newly ready thread.</span></span>

<span data-ttu-id="eecd5-294">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-294">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-295">정보 필드 1: 다시 시작 중인 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-295">Info Field 1: Pointer to the thread being resumed.</span></span>
- <span data-ttu-id="eecd5-296">정보 필드 2: 다음과 같이 다시 시작되는 스레드의 이전 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-296">Info Field 2: Previous state of the thread being resumed, as follows:</span></span>

  |  <span data-ttu-id="eecd5-297">스레드 상태</span><span class="sxs-lookup"><span data-stu-id="eecd5-297">Thread state</span></span>                     | <span data-ttu-id="eecd5-298">값</span><span class="sxs-lookup"><span data-stu-id="eecd5-298">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="eecd5-299">TX_READY</span><span class="sxs-lookup"><span data-stu-id="eecd5-299">TX_READY</span></span>                         | <span data-ttu-id="eecd5-300">0</span><span class="sxs-lookup"><span data-stu-id="eecd5-300">0</span></span>       |
  |  <span data-ttu-id="eecd5-301">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="eecd5-301">TX_COMPLETED</span></span>                     | <span data-ttu-id="eecd5-302">1</span><span class="sxs-lookup"><span data-stu-id="eecd5-302">1</span></span>       |
  |  <span data-ttu-id="eecd5-303">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="eecd5-303">TX_TERMINATED</span></span>                    | <span data-ttu-id="eecd5-304">2</span><span class="sxs-lookup"><span data-stu-id="eecd5-304">2</span></span>       |
  |  <span data-ttu-id="eecd5-305">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="eecd5-305">TX_SUSPENDED</span></span>                     | <span data-ttu-id="eecd5-306">3</span><span class="sxs-lookup"><span data-stu-id="eecd5-306">3</span></span>       |
  |  <span data-ttu-id="eecd5-307">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="eecd5-307">TX_SLEEP</span></span>                         | <span data-ttu-id="eecd5-308">4</span><span class="sxs-lookup"><span data-stu-id="eecd5-308">4</span></span>       |
  |  <span data-ttu-id="eecd5-309">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="eecd5-309">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="eecd5-310">5</span><span class="sxs-lookup"><span data-stu-id="eecd5-310">5</span></span>       |
  |  <span data-ttu-id="eecd5-311">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="eecd5-311">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="eecd5-312">6</span><span class="sxs-lookup"><span data-stu-id="eecd5-312">6</span></span>       |
  |  <span data-ttu-id="eecd5-313">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="eecd5-313">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="eecd5-314">7</span><span class="sxs-lookup"><span data-stu-id="eecd5-314">7</span></span>       |
  |  <span data-ttu-id="eecd5-315">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="eecd5-315">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="eecd5-316">8</span><span class="sxs-lookup"><span data-stu-id="eecd5-316">8</span></span>       |
  |  <span data-ttu-id="eecd5-317">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="eecd5-317">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="eecd5-318">9</span><span class="sxs-lookup"><span data-stu-id="eecd5-318">9</span></span>       |
  |  <span data-ttu-id="eecd5-319">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="eecd5-319">TX_TCP_IP</span></span>                        | <span data-ttu-id="eecd5-320">12</span><span class="sxs-lookup"><span data-stu-id="eecd5-320">12</span></span>      |
  |  <span data-ttu-id="eecd5-321">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="eecd5-321">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="eecd5-322">13</span><span class="sxs-lookup"><span data-stu-id="eecd5-322">13</span></span>      |

- <span data-ttu-id="eecd5-323">정보 필드 3: 호출하는 동안의 스택 포인터 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-323">Info Field 3: Stack pointer value during the call.</span></span> 
- <span data-ttu-id="eecd5-324">정보 필드 4: 실행 우선 순위가 다음으로 가장 높은 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-324">Info Field 4: Pointer to next highest priority thread to execute.</span></span>

### <a name="internal-thread-suspend"></a><span data-ttu-id="eecd5-325">내부 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="eecd5-325">Internal thread suspend</span></span>

#### <a name="internal-thread-suspend"></a><span data-ttu-id="eecd5-326">내부 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="eecd5-326">Internal thread suspend</span></span>

<span data-ttu-id="eecd5-327">**아이콘** ![내부 스레드 일시 중단 아이콘](./media/user-guide/tx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-327">**Icon** ![Internal thread suspend icon](./media/user-guide/tx-events/image2.png)</span></span>

<span data-ttu-id="eecd5-328">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-328">**Description**</span></span>

<span data-ttu-id="eecd5-329">이 이벤트는 스레드 실행을 일시 중단하는 ThreadX의 내부 처리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-329">This event represents the internal processing in ThreadX that suspends a thread's execution.</span></span> <span data-ttu-id="eecd5-330">실행할 준비가 된 다음으로 우선 순위가 가장 높은 스레드는 네 번째 정보 필드에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-330">The next highest priority thread ready for execution is placed in the fourth information field.</span></span> <span data-ttu-id="eecd5-331">이 값이 Null이면 실행할 준비가 된 다른 스레드가 없으며 시스템이 유휴 상태인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-331">If this value is NULL, there is no other thread ready for execution and the system is idle.</span></span>

<span data-ttu-id="eecd5-332">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-332">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-333">정보 필드 1: 일시 중단 중인 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-333">Info Field 1: Pointer to the thread being suspended.</span></span>
- <span data-ttu-id="eecd5-334">정보 필드 2: 다음과 같이 일시 중단 중인 스레드의 새 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-334">Info Field 2: New state of the thread being suspended, as follows:</span></span>

  |  <span data-ttu-id="eecd5-335">스레드 상태</span><span class="sxs-lookup"><span data-stu-id="eecd5-335">Thread state</span></span>                     | <span data-ttu-id="eecd5-336">값</span><span class="sxs-lookup"><span data-stu-id="eecd5-336">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="eecd5-337">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="eecd5-337">TX_COMPLETED</span></span>                     | <span data-ttu-id="eecd5-338">1</span><span class="sxs-lookup"><span data-stu-id="eecd5-338">1</span></span>       |
  |  <span data-ttu-id="eecd5-339">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="eecd5-339">TX_TERMINATED</span></span>                    | <span data-ttu-id="eecd5-340">2</span><span class="sxs-lookup"><span data-stu-id="eecd5-340">2</span></span>       |
  |  <span data-ttu-id="eecd5-341">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="eecd5-341">TX_SUSPENDED</span></span>                     | <span data-ttu-id="eecd5-342">3</span><span class="sxs-lookup"><span data-stu-id="eecd5-342">3</span></span>       |
  |  <span data-ttu-id="eecd5-343">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="eecd5-343">TX_SLEEP</span></span>                         | <span data-ttu-id="eecd5-344">4</span><span class="sxs-lookup"><span data-stu-id="eecd5-344">4</span></span>       |
  |  <span data-ttu-id="eecd5-345">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="eecd5-345">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="eecd5-346">5</span><span class="sxs-lookup"><span data-stu-id="eecd5-346">5</span></span>       |
  |  <span data-ttu-id="eecd5-347">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="eecd5-347">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="eecd5-348">6</span><span class="sxs-lookup"><span data-stu-id="eecd5-348">6</span></span>       |
  |  <span data-ttu-id="eecd5-349">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="eecd5-349">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="eecd5-350">7</span><span class="sxs-lookup"><span data-stu-id="eecd5-350">7</span></span>       |
  |  <span data-ttu-id="eecd5-351">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="eecd5-351">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="eecd5-352">8</span><span class="sxs-lookup"><span data-stu-id="eecd5-352">8</span></span>       |
  |  <span data-ttu-id="eecd5-353">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="eecd5-353">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="eecd5-354">9</span><span class="sxs-lookup"><span data-stu-id="eecd5-354">9</span></span>       |
  |  <span data-ttu-id="eecd5-355">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="eecd5-355">TX_TCP_IP</span></span>                        | <span data-ttu-id="eecd5-356">12</span><span class="sxs-lookup"><span data-stu-id="eecd5-356">12</span></span>      |
  |  <span data-ttu-id="eecd5-357">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="eecd5-357">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="eecd5-358">13</span><span class="sxs-lookup"><span data-stu-id="eecd5-358">13</span></span>      |

- <span data-ttu-id="eecd5-359">정보 필드 3: 호출하는 동안의 스택 포인터 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-359">Info Field 3: Stack pointer value during the call.</span></span> <span data-ttu-id="eecd5-360">정보 필드 4: 실행 우선 순위가 다음으로 가장 높은 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-360">Info Field 4: Pointer to next highest priority thread to execute.</span></span> <span data-ttu-id="eecd5-361">Null인 경우 시스템은 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-361">If NULL, the system is idle.</span></span>

### <a name="interrupt-service-routine-isr-enter"></a><span data-ttu-id="eecd5-362">ISR(인터럽트 서비스 루틴) 들어가기</span><span class="sxs-lookup"><span data-stu-id="eecd5-362">Interrupt Service Routine (ISR) enter</span></span> 

#### <a name="enter-isr"></a><span data-ttu-id="eecd5-363">ISR 들어가기</span><span class="sxs-lookup"><span data-stu-id="eecd5-363">Enter ISR</span></span> 

<span data-ttu-id="eecd5-364">**아이콘** ![ISR 들어가기 아이콘](./media/user-guide/tx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-364">**Icon** ![Enter I S R icon](./media/user-guide/tx-events/image3.png)</span></span>

<span data-ttu-id="eecd5-365">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-365">**Description**</span></span>

<span data-ttu-id="eecd5-366">이 이벤트는 애플리케이션에서 ISR(인터럽트 서비스 루틴)에 들어가는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-366">This event represents entering an Interrupt Service Routine (ISR) in the application.</span></span> <span data-ttu-id="eecd5-367">인터럽트 서비스 루틴 실행은 ISR 종료 이벤트가 발생할 때까지 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-367">The interrupt service routine execution continues until the ISR exit event takes place.</span></span>

<span data-ttu-id="eecd5-368">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-368">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-369">정보 필드 1: 호출하는 동안의 스택 포인터 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-369">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="eecd5-370">정보 필드 2: 애플리케이션 정의 ISR 번호(선택 사항)입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-370">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="eecd5-371">정보 필드 3: 중첩된 인터럽트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-371">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="eecd5-372">정보 필드 4: 내부 선점 사용 안 함 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-372">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="interrupt-service-routine-isr-exit"></a><span data-ttu-id="eecd5-373">ISR(인터럽트 서비스 루틴) 끝내기</span><span class="sxs-lookup"><span data-stu-id="eecd5-373">Interrupt Service Routine (ISR) exit</span></span> 

#### <a name="exit-isr"></a><span data-ttu-id="eecd5-374">ISR 끝내기</span><span class="sxs-lookup"><span data-stu-id="eecd5-374">Exit ISR</span></span>

<span data-ttu-id="eecd5-375">**아이콘** ![ISR 끝내기 아이콘](./media/user-guide/tx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-375">**Icon** ![Exit I S R icon](./media/user-guide/tx-events/image4.png)</span></span>

<span data-ttu-id="eecd5-376">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-376">**Description**</span></span>

<span data-ttu-id="eecd5-377">이 이벤트는 애플리케이션에서 ISR(인터럽트 서비스 루틴)을 종료하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-377">This event represents exiting an Interrupt Service Routine (ISR) in the application.</span></span>

<span data-ttu-id="eecd5-378">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-378">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-379">정보 필드 1: 호출하는 동안의 스택 포인터 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-379">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="eecd5-380">정보 필드 2: 애플리케이션 정의 ISR 번호(선택 사항)입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-380">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="eecd5-381">정보 필드 3: 중첩된 인터럽트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-381">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="eecd5-382">정보 필드 4: 내부 선점 사용 안 함 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-382">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="internal-time-slice"></a><span data-ttu-id="eecd5-383">내부 시간 조각</span><span class="sxs-lookup"><span data-stu-id="eecd5-383">Internal time-slice</span></span>

#### <a name="internal-time-slice"></a><span data-ttu-id="eecd5-384">내부 시간 조각</span><span class="sxs-lookup"><span data-stu-id="eecd5-384">Internal time-slice</span></span>

<span data-ttu-id="eecd5-385">**아이콘** ![내부 시간 조각 아이콘](./media/user-guide/tx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-385">**Icon** ![Internal time-slice icon](./media/user-guide/tx-events/image5.png)</span></span>

<span data-ttu-id="eecd5-386">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-386">**Description**</span></span>

<span data-ttu-id="eecd5-387">이 이벤트는 시간 조각 작업을 수행하는 ThreadX의 내부 처리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-387">This event represents the internal processing in ThreadX that performs the time-slice operation.</span></span> <span data-ttu-id="eecd5-388">우선 순위가 같은 다음 스레드는 첫 번째 정보 필드에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-388">The next thread of the same priority is placed in the first information field.</span></span> <span data-ttu-id="eecd5-389">이 값이 현재 스레드와 같으면 시간 조각이 수행되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-389">If this value is the same as the current thread, no time-slice was performed.</span></span>

- <span data-ttu-id="eecd5-390">정보 필드 1: 실행할 다음 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-390">Info Field 1: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="eecd5-391">정보 필드 2: 중첩된 인터럽트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-391">Info Field 2: Nested interrupt count.</span></span>
- <span data-ttu-id="eecd5-392">정보 필드 3: 내부 선점 사용 안 함 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-392">Info Field 3: Internal preemption disable flag.</span></span>
- <span data-ttu-id="eecd5-393">정보 필드 4: 호출하는 동안의 스택 포인터 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-393">Info Field 4: Stack pointer value during the call.</span></span>

### <a name="running"></a><span data-ttu-id="eecd5-394">실행 중</span><span class="sxs-lookup"><span data-stu-id="eecd5-394">Running</span></span>

#### <a name="running-in-context"></a><span data-ttu-id="eecd5-395">컨텍스트에서 실행</span><span class="sxs-lookup"><span data-stu-id="eecd5-395">Running in context</span></span>

<span data-ttu-id="eecd5-396">**아이콘** ![실행 아이콘](./media/user-guide/tx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-396">**Icon** ![Running icon](./media/user-guide/tx-events/image6.png)</span></span>

<span data-ttu-id="eecd5-397">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-397">**Description**</span></span>

<span data-ttu-id="eecd5-398">이 이벤트는 스레드 컨텍스트 또는 유휴 시스템에서 실행되는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-398">This event represents running within a thread context or idle system.</span></span> <span data-ttu-id="eecd5-399">이는 인터럽트의 결과로 컨텍스트의 후속 변경을 설명하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-399">It is used to illustrate subsequent changes in context as a result of an interrupt.</span></span>

<span data-ttu-id="eecd5-400">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-400">**Information Fields**</span></span>
- <span data-ttu-id="eecd5-401">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-401">Info Field 1: Not used.</span></span>
- <span data-ttu-id="eecd5-402">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-402">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-403">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-403">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-404">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-404">Info Field 4: Not used.</span></span>

### <a name="block-allocate"></a><span data-ttu-id="eecd5-405">블록 할당</span><span class="sxs-lookup"><span data-stu-id="eecd5-405">Block Allocate</span></span> 

#### <a name="tx_block_allocate"></a><span data-ttu-id="eecd5-406">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="eecd5-406">tx_block_allocate</span></span>

<span data-ttu-id="eecd5-407">**아이콘** ![블록 할당 아이콘](./media/user-guide/tx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-407">**Icon** ![Block allocate icon](./media/user-guide/tx-events/image7.png)</span></span>

<span data-ttu-id="eecd5-408">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-408">**Description**</span></span>

<span data-ttu-id="eecd5-409">이 이벤트는 tx_block_allocate를 통해 메모리 블록을 할당하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-409">This event represents allocating a memory block via tx_block_allocate.</span></span> <span data-ttu-id="eecd5-410">성공하면 할당된 블록의 주소가 두 번째 정보 필드로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-410">If successful, the address of the block allocated is returned in the second information field.</span></span>

<span data-ttu-id="eecd5-411">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-411">**Information Fields**</span></span>
- <span data-ttu-id="eecd5-412">정보 필드 1: 해당 블록 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-412">Info Field 1: Pointer to the corresponding block pool.</span></span>
- <span data-ttu-id="eecd5-413">정보 필드 2: 반환된 메모리 블록에 대한 포인터입니다(성공한 경우).</span><span class="sxs-lookup"><span data-stu-id="eecd5-413">Info Field 2: Pointer to the memory block returned (if successful).</span></span>
- <span data-ttu-id="eecd5-414">정보 필드 3: tx_block_allocate 호출에 제공되는 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-414">Info Field 3: The wait option supplied to the tx_block_allocate call.</span></span>
- <span data-ttu-id="eecd5-415">정보 필드 4: 이 할당 후 풀에서 사용 가능한 남은 블록 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-415">Info Field 4: Remaining available blocks in the pool after this allocation.</span></span>

### <a name="block-pool-create"></a><span data-ttu-id="eecd5-416">블록 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="eecd5-416">Block Pool Create</span></span>

#### <a name="tx_block_pool_create"></a><span data-ttu-id="eecd5-417">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="eecd5-417">tx_block_pool_create</span></span>

<span data-ttu-id="eecd5-418">**아이콘** ![블록 풀 만들기 아이콘](./media/user-guide/tx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-418">**Icon** ![Block pool create icon](./media/user-guide/tx-events/image8.png)</span></span>

<span data-ttu-id="eecd5-419">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-419">**Description**</span></span>

<span data-ttu-id="eecd5-420">이 이벤트는 tx_block_pool_create를 통해 메모리 블록 풀을 만드는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-420">This event represents creating a memory block pool via tx_block_pool_create.</span></span>

<span data-ttu-id="eecd5-421">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-421">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-422">정보 필드 1: 해당 블록 풀 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-422">Info Field 1: Pointer to the corresponding block pool control block.</span></span>
- <span data-ttu-id="eecd5-423">정보 필드 2: 풀의 시작 메모리 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-423">Info Field 2: Pointer to the starting memory area of the pool.</span></span>
- <span data-ttu-id="eecd5-424">정보 필드 3: 풀의 블록 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-424">Info Field 3: The number of blocks in the pool.</span></span> <span data-ttu-id="eecd5-425">정보 필드 4: 풀의 각 블록 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-425">Info Field 4: The size of each block in the pool in bytes.</span></span>

### <a name="block-pool-delete"></a><span data-ttu-id="eecd5-426">블록 풀 삭제</span><span class="sxs-lookup"><span data-stu-id="eecd5-426">Block Pool Delete</span></span>

#### <a name="tx_block_pool_delete"></a><span data-ttu-id="eecd5-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="eecd5-427">tx_block_pool_delete</span></span>

<span data-ttu-id="eecd5-428">**아이콘** ![블록 풀 삭제 아이콘](./media/user-guide/tx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-428">**Icon** ![Block pool delete icon](./media/user-guide/tx-events/image9.png)</span></span>

<span data-ttu-id="eecd5-429">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-429">**Description**</span></span>

<span data-ttu-id="eecd5-430">이 이벤트는 tx_block_pool_delete를 통해 메모리 블록 풀을 삭제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-430">This event represents deleting a memory block pool via tx_block_pool_delete.</span></span>

<span data-ttu-id="eecd5-431">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-431">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-432">정보 필드 1: 블록 풀 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-432">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="eecd5-433">정보 필드 2: 호출하는 동안의 스택 포인터 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-433">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="eecd5-434">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-434">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-435">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-435">Info Field 4: Not used.</span></span>

### <a name="block-pool-information-get"></a><span data-ttu-id="eecd5-436">블록 풀 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-436">Block Pool Information Get</span></span> 

#### <a name="tx_block_pool_info_get"></a><span data-ttu-id="eecd5-437">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-437">tx_block_pool_info_get</span></span>

<span data-ttu-id="eecd5-438">**아이콘** ![블록 풀 정보 가져오기 아이콘](./media/user-guide/tx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-438">**Icon** ![Block pool information get icon](./media/user-guide/tx-events/image10.png)</span></span>

<span data-ttu-id="eecd5-439">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-439">**Description**</span></span>

<span data-ttu-id="eecd5-440">이 이벤트는 tx_block_pool_info_get을 통해 메모리 블록 풀에 대한 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-440">This event represents getting information about a memory block pool via tx_block_pool_info_get.</span></span>

<span data-ttu-id="eecd5-441">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-441">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-442">정보 필드 1: 블록 풀 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-442">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="eecd5-443">정보 필드 2: 호출하는 동안의 스택 포인터 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-443">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="eecd5-444">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-444">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-445">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-445">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-information-get"></a><span data-ttu-id="eecd5-446">블록 풀 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-446">Block Pool Performance Information Get</span></span>

#### <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="eecd5-447">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-447">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="eecd5-448">**아이콘** ![블록 풀 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-448">**Icon** ![Block pool performance information get icon](./media/user-guide/tx-events/image11.png)</span></span>

<span data-ttu-id="eecd5-449">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-449">**Description**</span></span>

<span data-ttu-id="eecd5-450">이 이벤트는 tx_block_pool_performance_info_get을 통해 메모리 블록 풀에 대한 성능 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-450">This event represents getting performance information about a memory block pool via tx_block_pool_performance_info_get.</span></span>

<span data-ttu-id="eecd5-451">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-451">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-452">정보 필드 1: 블록 풀 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-452">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="eecd5-453">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-453">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-454">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-454">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-455">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-455">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-system-information-get"></a><span data-ttu-id="eecd5-456">블록 풀 성능 시스템 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-456">Block Pool Performance System Information Get</span></span>

#### <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="eecd5-457">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-457">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="eecd5-458">**아이콘** ![블록 풀 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-458">**Icon** ![Block pool performance system information get icon](./media/user-guide/tx-events/image12.png)</span></span>

<span data-ttu-id="eecd5-459">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-459">**Description**</span></span>

<span data-ttu-id="eecd5-460">이 이벤트는 tx_block_pool_performance_system_info_get을 통해 모든 메모리 블록 풀에 대한 성능 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-460">This event represents getting performance information about all memory block pools via tx_block_pool_performance_system_info_get.</span></span>

<span data-ttu-id="eecd5-461">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-461">**Information Fields**</span></span>
- <span data-ttu-id="eecd5-462">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-462">Info Field 1: Not used.</span></span>
- <span data-ttu-id="eecd5-463">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-463">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-464">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-464">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-465">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-465">Info Field 4: Not used.</span></span>

### <a name="block-pool-prioritize"></a><span data-ttu-id="eecd5-466">블록 풀 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="eecd5-466">Block Pool Prioritize</span></span>

#### <a name="tx_block_pool_prioritize"></a><span data-ttu-id="eecd5-467">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="eecd5-467">tx_block_pool_prioritize</span></span>

<span data-ttu-id="eecd5-468">**아이콘** ![블록 풀 우선 순위 지정 아이콘](./media/user-guide/tx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-468">**Icon** ![Block pool prioritize icon](./media/user-guide/tx-events/image13.png)</span></span>

<span data-ttu-id="eecd5-469">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-469">**Description**</span></span>

<span data-ttu-id="eecd5-470">이 이벤트는 highestpriority suspended 스레드를 블록 풀 일시 중단 목록의 맨 앞에 배치하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-470">This event represents placing the highestpriority suspended thread at the front of the block pool suspension list.</span></span> <span data-ttu-id="eecd5-471">tx_block_release를 호출하기 전에 이 작업을 수행하면 일시 중단된 스레드 중 우선 순위가 가장 높은 스레드가 해제된 블록을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-471">If this is done prior to calling tx_block_release, the highest priority suspended thread will receive the released block.</span></span>

<span data-ttu-id="eecd5-472">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-472">**Information Fields**</span></span>
- <span data-ttu-id="eecd5-473">정보 필드 1: 메모리 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-473">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="eecd5-474">정보 필드 2: 이 블록 풀에 대해 일시 중단된 스레드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-474">Info Field 2: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="eecd5-475">정보 필드 3: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-475">Info Field 3: Stack pointer at the time of the call.</span></span>
- <span data-ttu-id="eecd5-476">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-476">Info Field 4: Not used.</span></span>

### <a name="block-release"></a><span data-ttu-id="eecd5-477">블록 해제</span><span class="sxs-lookup"><span data-stu-id="eecd5-477">Block Release</span></span> 

#### <a name="tx_block_release"></a><span data-ttu-id="eecd5-478">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="eecd5-478">tx_block_release</span></span>

<span data-ttu-id="eecd5-479">**아이콘** ![블록 해제 아이콘](./media/user-guide/tx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-479">**Icon** ![Block release icon](./media/user-guide/tx-events/image14.png)</span></span>

<span data-ttu-id="eecd5-480">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-480">**Description**</span></span>

<span data-ttu-id="eecd5-481">이 이벤트는 이전에 할당된 블록을 블록 풀로 다시 해제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-481">This event represents releasing a previously allocated block back to the block pool.</span></span>

<span data-ttu-id="eecd5-482">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-482">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-483">정보 필드 1: 메모리 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-483">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="eecd5-484">정보 필드 2: 해제할 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-484">Info Field 2: Pointer to block to release.</span></span>
- <span data-ttu-id="eecd5-485">정보 필드 3: 이 블록 풀에 대해 일시 중단된 스레드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-485">Info Field 3: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="eecd5-486">정보 필드 4: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-486">Info Field 4: Stack pointer at the time of the call.</span></span>

### <a name="byte-allocate"></a><span data-ttu-id="eecd5-487">바이트 할당</span><span class="sxs-lookup"><span data-stu-id="eecd5-487">Byte Allocate</span></span> 

#### <a name="tx_byte_allocate"></a><span data-ttu-id="eecd5-488">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="eecd5-488">tx_byte_allocate</span></span>

<span data-ttu-id="eecd5-489">**아이콘** ![바이트 할당 아이콘](./media/user-guide/tx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-489">**Icon** ![Byte allocate icon](./media/user-guide/tx-events/image15.png)</span></span>

<span data-ttu-id="eecd5-490">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-490">**Description**</span></span>

<span data-ttu-id="eecd5-491">이 이벤트는 tx_byte_allocate를 통해 메모리를 할당하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-491">This event represents allocating memory via tx_byte_allocate.</span></span> <span data-ttu-id="eecd5-492">성공하면 할당된 메모리의 주소가 두 번째 정보 필드로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-492">If successful, the address of the memory allocated is returned in the second information field.</span></span>

<span data-ttu-id="eecd5-493">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-493">**Information Fields**</span></span>
- <span data-ttu-id="eecd5-494">정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-494">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="eecd5-495">정보 필드 2: 반환된 메모리에 대한 포인터입니다(성공한 경우).</span><span class="sxs-lookup"><span data-stu-id="eecd5-495">Info Field 2: Pointer to the memory returned (if successful).</span></span>
- <span data-ttu-id="eecd5-496">정보 필드 3: 요청된 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-496">Info Field 3: Number of bytes requested.</span></span> <span data-ttu-id="eecd5-497">정보 필드 4: tx_byte_allocate 호출에 제공되는 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-497">Info Field 4: The wait option supplied to the tx_byte_allocate call.</span></span>

### <a name="byte-pool-create"></a><span data-ttu-id="eecd5-498">바이트 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="eecd5-498">Byte Pool Create</span></span>

#### <a name="tx_byte_pool_create"></a><span data-ttu-id="eecd5-499">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="eecd5-499">tx_byte_pool_create</span></span>

<span data-ttu-id="eecd5-500">**아이콘** ![바이트 풀 만들기 아이콘](./media/user-guide/tx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-500">**Icon** ![Byte pool create icon](./media/user-guide/tx-events/image16.png)</span></span>

<span data-ttu-id="eecd5-501">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-501">**Description**</span></span>

<span data-ttu-id="eecd5-502">이 이벤트는 tx_byte_pool_create를 통해 바이트 풀을 만드는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-502">This event represents creating a byte pool via tx_byte_pool_create.</span></span>

<span data-ttu-id="eecd5-503">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-503">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-504">정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-504">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="eecd5-505">정보 필드 2: 메모리 영역의 시작 부분에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-505">Info Field 2: Pointer to the start of the memory area.</span></span> <span data-ttu-id="eecd5-506">정보 필드 3: 바이트 풀의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-506">Info Field 3: Number of bytes in the byte pool.</span></span>
- <span data-ttu-id="eecd5-507">정보 필드 4: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-507">Info Field 4: The stack pointer at the time of the call.</span></span>

### <a name="byte-pool-delete"></a><span data-ttu-id="eecd5-508">바이트 풀 삭제</span><span class="sxs-lookup"><span data-stu-id="eecd5-508">Byte Pool Delete</span></span> 

#### <a name="tx_byte_pool_delete"></a><span data-ttu-id="eecd5-509">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="eecd5-509">tx_byte_pool_delete</span></span>

<span data-ttu-id="eecd5-510">**아이콘** ![바이트 풀 삭제 아이콘](./media/user-guide/tx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-510">**Icon** ![Byte pool delete icon](./media/user-guide/tx-events/image17.png)</span></span>

<span data-ttu-id="eecd5-511">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-511">**Description**</span></span>

<span data-ttu-id="eecd5-512">이 이벤트는 tx_byte_pool_delete를 통해 바이트 풀을 삭제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-512">This event represents deleting a byte pool via tx_byte_pool_delete.</span></span>

<span data-ttu-id="eecd5-513">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-513">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-514">정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-514">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="eecd5-515">정보 필드 2: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-515">Info Field 2: The stack pointer at the time of the call.</span></span>
- <span data-ttu-id="eecd5-516">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-516">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-517">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-517">Info Field 4: Not used.</span></span>

### <a name="byte-pool-information-get"></a><span data-ttu-id="eecd5-518">바이트 풀 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-518">Byte Pool Information Get</span></span>

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="eecd5-519">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-519">tx_byte_pool_info_get</span></span>

<span data-ttu-id="eecd5-520">**아이콘** ![바이트 풀 정보 가져오기 아이콘](./media/user-guide/tx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-520">**Icon** ![Byte pool information get icon](./media/user-guide/tx-events/image18.png)</span></span>

<span data-ttu-id="eecd5-521">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-521">**Description**</span></span>

<span data-ttu-id="eecd5-522">이 이벤트는 tx_byte_pool_info_get을 통해 바이트 풀 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-522">This event represents getting byte pool information via tx_byte_pool_info_get.</span></span>

<span data-ttu-id="eecd5-523">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-523">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-524">정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-524">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="eecd5-525">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-525">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-526">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-526">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-527">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-527">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-info-get"></a><span data-ttu-id="eecd5-528">바이트 풀 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-528">Byte Pool Performance Info Get</span></span> 

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="eecd5-529">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-529">tx_byte_pool_info_get</span></span>

<span data-ttu-id="eecd5-530">**아이콘** ![바이트 풀 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-530">**Icon** ![Byte pool performance info get icon](./media/user-guide/tx-events/image19.png)</span></span>

<span data-ttu-id="eecd5-531">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-531">**Description**</span></span>

<span data-ttu-id="eecd5-532">이 이벤트는 tx_byte_pool_performance_info_get을 통해 바이트 풀 성능 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-532">This event represents getting byte pool performance information via tx_byte_pool_performance_info_get.</span></span>

<span data-ttu-id="eecd5-533">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-533">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-534">정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-534">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="eecd5-535">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-535">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-536">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-536">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-537">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-537">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-system-info-get"></a><span data-ttu-id="eecd5-538">바이트 풀 성능 시스템 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-538">Byte Pool Performance System Info Get</span></span> 

#### <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="eecd5-539">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-539">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="eecd5-540">**아이콘** ![바이트 풀 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-540">**Icon** ![Byte pool performance system info get icon](./media/user-guide/tx-events/image20.png)</span></span>

<span data-ttu-id="eecd5-541">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-541">**Description**</span></span>

<span data-ttu-id="eecd5-542">이 이벤트는 tx_byte_pool_performance_system_info_get을 통해 바이트 풀 성능 시스템 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-542">This event represents getting byte pool performance system information via tx_byte_pool_performance_system_info_get.</span></span>

<span data-ttu-id="eecd5-543">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-543">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-544">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-544">Info Field 1: Not used.</span></span>
- <span data-ttu-id="eecd5-545">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-545">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-546">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-546">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-547">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-547">Info Field 4: Not used.</span></span>

### <a name="byte-pool-prioritize"></a><span data-ttu-id="eecd5-548">바이트 풀 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="eecd5-548">Byte Pool Prioritize</span></span>

#### <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="eecd5-549">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="eecd5-549">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="eecd5-550">**아이콘** ![바이트 풀 우선 순위 지정 아이콘](./media/user-guide/tx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-550">**Icon** ![Byte pool prioritize icon](./media/user-guide/tx-events/image21.png)</span></span>

<span data-ttu-id="eecd5-551">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-551">**Description**</span></span>

<span data-ttu-id="eecd5-552">이 이벤트는 tx_byte_pool_prioritize를 통해 바이트 풀의 일시 중단 목록의 우선 순위를 지정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-552">This event represents prioritizing the byte pool's suspension list via tx_byte_pool_prioritize.</span></span>

<span data-ttu-id="eecd5-553">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-553">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-554">정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-554">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="eecd5-555">정보 필드 2: 바이트 풀에 대해 현재 일시 중단된 스레드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-555">Info Field 2: Number of threads currently suspended on byte pool.</span></span>
- <span data-ttu-id="eecd5-556">정보 필드 3: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-556">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-557">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-557">Info Field 4: Not used.</span></span>

### <a name="byte-release"></a><span data-ttu-id="eecd5-558">바이트 해제</span><span class="sxs-lookup"><span data-stu-id="eecd5-558">Byte Release</span></span>

#### <a name="tx_byte_release"></a><span data-ttu-id="eecd5-559">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="eecd5-559">tx_byte_release</span></span>

<span data-ttu-id="eecd5-560">**아이콘** ![바이트 해제 아이콘](./media/user-guide/tx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-560">**Icon** ![Byte release icon](./media/user-guide/tx-events/image22.png)</span></span>

<span data-ttu-id="eecd5-561">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-561">**Description**</span></span>

<span data-ttu-id="eecd5-562">이 이벤트는 tx_byte_release를 통해 바이트 풀에서 할당된 메모리 블록을 해제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-562">This event represents releasing a block of memory allocated from a byte pool via tx_byte_release.</span></span>

<span data-ttu-id="eecd5-563">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-563">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-564">정보 필드 1: 해당 바이트 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-564">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="eecd5-565">정보 필드 2: 이전에 할당된 바이트 풀 메모리에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-565">Info Field 2: Pointer to previously allocated byte pool memory.</span></span>
- <span data-ttu-id="eecd5-566">정보 필드 3: 이 바이트 풀에 대해 일시 중단된 스레드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-566">Info Field 3: Number of threads suspended on this byte pool.</span></span>
- <span data-ttu-id="eecd5-567">정보 필드 4: 사용 가능한 메모리 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-567">Info Field 4: Number of available bytes of memory.</span></span>

### <a name="event-flags-create"></a><span data-ttu-id="eecd5-568">이벤트 플래그 만들기</span><span class="sxs-lookup"><span data-stu-id="eecd5-568">Event Flags Create</span></span> 

#### <a name="tx_event_flags_create"></a><span data-ttu-id="eecd5-569">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="eecd5-569">tx_event_flags_create</span></span>

<span data-ttu-id="eecd5-570">**아이콘** ![이벤트 플래그 만들기 아이콘](./media/user-guide/tx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-570">**Icon** ![Event flags create icon](./media/user-guide/tx-events/image23.png)</span></span>

<span data-ttu-id="eecd5-571">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-571">**Description**</span></span>

<span data-ttu-id="eecd5-572">이 이벤트는 tx_event_flags_create를 통해 새 이벤트 플래그 그룹을 만드는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-572">This event represents creating a new event flags group via tx_event_flags_create.</span></span>

<span data-ttu-id="eecd5-573">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-573">**Information Fields**</span></span> 
- <span data-ttu-id="eecd5-574">정보 필드 1: 이벤트 플래그 그룹 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-574">Info Field 1: Pointer to event flags group control block.</span></span>
- <span data-ttu-id="eecd5-575">정보 필드 2: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-575">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-576">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-576">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-577">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-577">Info Field 4: Not used.</span></span>

### <a name="event-flags-delete"></a><span data-ttu-id="eecd5-578">이벤트 플래그 삭제</span><span class="sxs-lookup"><span data-stu-id="eecd5-578">Event Flags Delete</span></span> 

#### <a name="tx_event_flags_delete"></a><span data-ttu-id="eecd5-579">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="eecd5-579">tx_event_flags_delete</span></span>

<span data-ttu-id="eecd5-580">**아이콘** ![이벤트 플래그 삭제 아이콘](./media/user-guide/tx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-580">**Icon** ![Event flags delete icon](./media/user-guide/tx-events/image24.png)</span></span>

<span data-ttu-id="eecd5-581">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-581">**Description**</span></span>

<span data-ttu-id="eecd5-582">이 이벤트는 tx_event_flags_delete를 통해 이벤트 플래그 그룹을 삭제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-582">This event represents deleting an event flags group via tx_event_flags_delete.</span></span>

<span data-ttu-id="eecd5-583">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-583">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-584">정보 필드 1: 이벤트 플래그 그룹에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-584">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="eecd5-585">정보 필드 2: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-585">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-586">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-586">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-587">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-587">Info Field 4: Not used.</span></span>

### <a name="event-flags-get"></a><span data-ttu-id="eecd5-588">이벤트 플래그 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-588">Event Flags Get</span></span> 

#### <a name="tx_event_flags_get"></a><span data-ttu-id="eecd5-589">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-589">tx_event_flags_get</span></span>

<span data-ttu-id="eecd5-590">**아이콘** ![이벤트 플래그 가져오기 아이콘](./media/user-guide/tx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-590">**Icon** ![Event flags gt icon](./media/user-guide/tx-events/image25.png)</span></span>

<span data-ttu-id="eecd5-591">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-591">**Description**</span></span>

<span data-ttu-id="eecd5-592">이 이벤트는 tx_event_flags_get을 통해 기존 이벤트 플래그 그룹에서 이벤트 플래그를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-592">This event represents retrieving event flags from an existing event flags group via tx_event_flags_get.</span></span>

<span data-ttu-id="eecd5-593">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-593">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-594">정보 필드 1: 이벤트 플래그 그룹에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-594">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="eecd5-595">정보 필드 2: 요청된 이벤트 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-595">Info Field 2: Event flags requested.</span></span>
- <span data-ttu-id="eecd5-596">정보 필드 3: 그룹에 현재 설정된 이벤트 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-596">Info Field 3: Event flags currently set in the group.</span></span>
- <span data-ttu-id="eecd5-597">정보 필드 4: 이벤트 플래그 가져오기에 대한 요청된 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-597">Info Field 4: Option requested on the event flags get.</span></span>

### <a name="event-flags-information-get"></a><span data-ttu-id="eecd5-598">이벤트 플래그 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-598">Event Flags Information Get</span></span>

#### <a name="tx_event_flags_info_get"></a><span data-ttu-id="eecd5-599">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-599">tx_event_flags_info_get</span></span>

<span data-ttu-id="eecd5-600">**아이콘** ![이벤트 플래그 정보 가져오기 아이콘](./media/user-guide/tx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-600">**Icon** ![Event flags information get icon](./media/user-guide/tx-events/image26.png)</span></span>

<span data-ttu-id="eecd5-601">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-601">**Description**</span></span>

<span data-ttu-id="eecd5-602">이 이벤트는 tx_event_flags_info_get을 통해 기존 이벤트 플래그 그룹에 대한 정보를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-602">This event represents retrieving information regarding an existing event flags group via tx_event_flags_info_get.</span></span>

<span data-ttu-id="eecd5-603">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-603">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-604">정보 필드 1: 이벤트 플래그 그룹에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-604">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="eecd5-605">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-605">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-606">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-606">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-607">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-607">Info Field 4: Not used.</span></span>

### <a name="event-flags-performance-information-get"></a><span data-ttu-id="eecd5-608">이벤트 플래그 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-608">Event Flags Performance Information Get</span></span> 

#### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="eecd5-609">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-609">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="eecd5-610">**아이콘** ![이벤트 플래그 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-610">**Icon** ![Event flags performance information get icon](./media/user-guide/tx-events/image27.png)</span></span>

<span data-ttu-id="eecd5-611">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-611">**Description**</span></span>

<span data-ttu-id="eecd5-612">이 이벤트는 tx_event_flags_performance_info_get을 통해 기존 이벤트 플래그 그룹에 대한 성능 정보를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-612">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_info_get.</span></span>

<span data-ttu-id="eecd5-613">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-613">**Information Fields**</span></span> 
- <span data-ttu-id="eecd5-614">정보 필드 1: 이벤트 플래그 그룹에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-614">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="eecd5-615">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-615">Info Field 2: Not used</span></span>
- <span data-ttu-id="eecd5-616">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-616">Info Field 3: Not used</span></span>
- <span data-ttu-id="eecd5-617">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-617">Info Field 4: Not Used</span></span>

### <a name="event-flags-performance-system-info-get"></a><span data-ttu-id="eecd5-618">이벤트 플래그 성능 시스템 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-618">Event Flags Performance System Info Get</span></span>

#### <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="eecd5-619">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-619">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="eecd5-620">**아이콘** ![이벤트 플래그 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-620">**Icon** ![Event flags performance system info get icon](./media/user-guide/tx-events/image28.png)</span></span>

<span data-ttu-id="eecd5-621">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-621">**Description**</span></span>

<span data-ttu-id="eecd5-622">이 이벤트는 tx_event_flags_performance_system_info_get을 통해 기존 이벤트 플래그 그룹에 대한 성능 정보를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-622">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_system_info_get.</span></span>

<span data-ttu-id="eecd5-623">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-623">**Information Fields**</span></span>
- <span data-ttu-id="eecd5-624">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-624">Info Field 1: Not used.</span></span>
- <span data-ttu-id="eecd5-625">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-625">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-626">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-626">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-627">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-627">Info Field 4: Not used.</span></span>

### <a name="event-flags-set"></a><span data-ttu-id="eecd5-628">이벤트 플래그 설정</span><span class="sxs-lookup"><span data-stu-id="eecd5-628">Event Flags Set</span></span> 

#### <a name="tx_event_flags_set"></a><span data-ttu-id="eecd5-629">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="eecd5-629">tx_event_flags_set</span></span>

<span data-ttu-id="eecd5-630">**아이콘** ![이벤트 플래그 설정 아이콘](./media/user-guide/tx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-630">**Icon** ![Event flags set icon](./media/user-guide/tx-events/image29.png)</span></span>

<span data-ttu-id="eecd5-631">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-631">**Description**</span></span>

<span data-ttu-id="eecd5-632">이 이벤트는 tx_event_flags_set을 통해 기존 이벤트 플래그 그룹의 이벤트 플래그를 설정(또는 해제)하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-632">This event represents setting (or clearing) event flags in an existing event flags group via tx_event_flags_set.</span></span>

<span data-ttu-id="eecd5-633">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-633">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-634">정보 필드 1: 이벤트 플래그 그룹에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-634">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="eecd5-635">정보 필드 2: 설정(또는 해제)할 이벤트 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-635">Info Field 2: Event flags to set (or clear).</span></span>
- <span data-ttu-id="eecd5-636">정보 필드 3: AND 또는 OR 이벤트 플래그 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-636">Info Field 3: AND or OR event flag option.</span></span>
- <span data-ttu-id="eecd5-637">정보 필드 4: 이벤트 플래그 그룹에 대해 일시 중단된 스레드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-637">Info Field 4: Number of threads suspended on event flag group.</span></span>

### <a name="event-flags-set-notify"></a><span data-ttu-id="eecd5-638">이벤트 플래그 설정 알림</span><span class="sxs-lookup"><span data-stu-id="eecd5-638">Event Flags Set Notify</span></span>

#### <a name="tx_event_flags_set_notify"></a><span data-ttu-id="eecd5-639">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="eecd5-639">tx_event_flags_set_notify</span></span>

<span data-ttu-id="eecd5-640">**아이콘** ![이벤트 플래그 설정 알림 아이콘](./media/user-guide/tx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-640">**Icon** ![Event flags set notify icon](./media/user-guide/tx-events/image30.png)</span></span>

<span data-ttu-id="eecd5-641">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-641">**Description**</span></span>

<span data-ttu-id="eecd5-642">이 이벤트는 tx_event_flags_set_notify를 통해 기존 이벤트 플래그 그룹에 대한 이벤트 플래그 설정 작업의 알림 콜백을 등록하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-642">This event represents registering a notification callback for any event flag set operation on an existing event flags group via tx_event_flags_set_notify.</span></span>

<span data-ttu-id="eecd5-643">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-643">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-644">정보 필드 1: 이벤트 플래그 그룹에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-644">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="eecd5-645">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-645">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-646">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-646">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-647">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-647">Info Field 4: Not used.</span></span>

### <a name="interrupt-control"></a><span data-ttu-id="eecd5-648">인터럽트 제어</span><span class="sxs-lookup"><span data-stu-id="eecd5-648">Interrupt Control</span></span> 

#### <a name="tx_interrupt_control"></a><span data-ttu-id="eecd5-649">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="eecd5-649">tx_interrupt_control</span></span>

<span data-ttu-id="eecd5-650">**아이콘** ![인터럽트 제어 아이콘](./media/user-guide/tx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-650">**Icon** ![Interrupt control icon](./media/user-guide/tx-events/image31.png)</span></span>

<span data-ttu-id="eecd5-651">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-651">**Description**</span></span>

<span data-ttu-id="eecd5-652">이 이벤트는 tx_interrupt_control을 통해 프로세서의 인터럽트 잠금 상태를 변경하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-652">This event represents changing the interrupt lockout posture of the processor via tx_interrupt_control.</span></span>

<span data-ttu-id="eecd5-653">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-653">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-654">정보 필드 1: 새 인터럽트 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-654">Info Field 1: New interrupt posture.</span></span>
- <span data-ttu-id="eecd5-655">정보 필드 2: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-655">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-656">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-656">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-657">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-657">Info Field 4: Not used.</span></span>

### <a name="mutex-create"></a><span data-ttu-id="eecd5-658">뮤텍스 만들기</span><span class="sxs-lookup"><span data-stu-id="eecd5-658">Mutex Create</span></span> 

#### <a name="tx_mutex_create"></a><span data-ttu-id="eecd5-659">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="eecd5-659">tx_mutex_create</span></span>

<span data-ttu-id="eecd5-660">**아이콘** ![뮤텍스 만들기 아이콘](./media/user-guide/tx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-660">**Icon** ![Mutex create icon](./media/user-guide/tx-events/image32.png)</span></span>

<span data-ttu-id="eecd5-661">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-661">**Description**</span></span>

<span data-ttu-id="eecd5-662">이 이벤트는 tx_mutex_create를 통해 뮤텍스를 만드는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-662">This event represents creating a mutex via tx_mutex_create.</span></span>

<span data-ttu-id="eecd5-663">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-663">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-664">정보 필드 1: 뮤텍스 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-664">Info Field 1: Pointer to mutex control block.</span></span>
- <span data-ttu-id="eecd5-665">정보 필드 2: 우선 순위 상속 옵션</span><span class="sxs-lookup"><span data-stu-id="eecd5-665">Info Field 2: Priority inheritance option</span></span>
- <span data-ttu-id="eecd5-666">(TX_INHERIT 또는 TX_NO_INHERIT)입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-666">(TX_INHERIT or TX_NO_INHERIT).</span></span>
- <span data-ttu-id="eecd5-667">정보 필드 3: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-667">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-668">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-668">Info Field 4: Not used.</span></span>

### <a name="mutex-delete"></a><span data-ttu-id="eecd5-669">뮤텍스 삭제</span><span class="sxs-lookup"><span data-stu-id="eecd5-669">Mutex Delete</span></span> 

#### <a name="tx_mutex_delete"></a><span data-ttu-id="eecd5-670">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="eecd5-670">tx_mutex_delete</span></span>

<span data-ttu-id="eecd5-671">**아이콘** ![뮤텍스 삭제 아이콘](./media/user-guide/tx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-671">**Icon** ![Mutex delete icon](./media/user-guide/tx-events/image33.png)</span></span>

<span data-ttu-id="eecd5-672">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-672">**Description**</span></span>

<span data-ttu-id="eecd5-673">이 이벤트는 tx_mutex_delete를 통해 뮤텍스를 삭제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-673">This event represents deleting a mutex via tx_mutex_delete.</span></span>

<span data-ttu-id="eecd5-674">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-674">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-675">정보 필드 1: 뮤텍스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-675">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="eecd5-676">정보 필드 2: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-676">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-677">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-677">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-678">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-678">Info Field 4: Not used.</span></span>

### <a name="mutex-get"></a><span data-ttu-id="eecd5-679">뮤텍스 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-679">Mutex Get</span></span> 

#### <a name="tx_mutex_get"></a><span data-ttu-id="eecd5-680">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-680">tx_mutex_get</span></span>

<span data-ttu-id="eecd5-681">**아이콘** ![뮤텍스 가져오기 아이콘](./media/user-guide/tx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-681">**Icon** ![Mutex get icon](./media/user-guide/tx-events/image34.png)</span></span>

<span data-ttu-id="eecd5-682">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-682">**Description**</span></span>

<span data-ttu-id="eecd5-683">이 이벤트는 tx_mutex_get을 통해 뮤텍스를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-683">This event represents obtaining a mutex via tx_mutex_get.</span></span>

<span data-ttu-id="eecd5-684">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-684">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-685">정보 필드 1: 뮤텍스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-685">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="eecd5-686">정보 필드 2: tx_mutex_get 호출에 제공되는 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-686">Info Field 2: The wait option supplied to the tx_mutex_get call.</span></span>
- <span data-ttu-id="eecd5-687">정보 필드 3: 뮤텍스를 소유하는 스레드에 대한 포인터입니다(Null은 뮤텍스를 소유하고 있지 않음을 의미).</span><span class="sxs-lookup"><span data-stu-id="eecd5-687">Info Field 3: Pointer to thread that owns the mutex (NULL implies the mutex is not owned).</span></span>
- <span data-ttu-id="eecd5-688">정보 필드 4: 소유 스레드가 tx_mutex_get을 호출한 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-688">Info Field 4: Number of times the owning thread has called tx_mutex_get.</span></span>

### <a name="mutex-information-get"></a><span data-ttu-id="eecd5-689">뮤텍스 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-689">Mutex Information Get</span></span>

#### <a name="tx_mutex_info_get"></a><span data-ttu-id="eecd5-690">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-690">tx_mutex_info_get</span></span>

<span data-ttu-id="eecd5-691">**아이콘** ![뮤텍스 정보 가져오기 아이콘](./media/user-guide/tx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-691">**Icon** ![Mutex information get icon](./media/user-guide/tx-events/image35.png)</span></span>

<span data-ttu-id="eecd5-692">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-692">**Description**</span></span>

<span data-ttu-id="eecd5-693">이 이벤트는 tx_mutex_info_get을 통해 뮤텍스 정보를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-693">This event represents retrieving mutex information via tx_mutex_info_get.</span></span>

<span data-ttu-id="eecd5-694">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-694">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-695">정보 필드 1: 뮤텍스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-695">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="eecd5-696">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-696">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-697">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-697">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-698">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-698">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-information-get"></a><span data-ttu-id="eecd5-699">뮤텍스 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-699">Mutex Performance Information Get</span></span> 

#### <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="eecd5-700">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-700">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="eecd5-701">**아이콘** ![뮤텍스 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-701">**Icon** ![Mutex performance information get icon](./media/user-guide/tx-events/image36.png)</span></span>

<span data-ttu-id="eecd5-702">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-702">**Description**</span></span>

<span data-ttu-id="eecd5-703">이 이벤트는 tx_mutex_performance_info_get을 통해 뮤텍스 성능 정보를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-703">This event represents retrieving mutex performance information via tx_mutex_performance_info_get.</span></span>

<span data-ttu-id="eecd5-704">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-704">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-705">정보 필드 1: 뮤텍스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-705">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="eecd5-706">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-706">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-707">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-707">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-708">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-708">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-system-info-get"></a><span data-ttu-id="eecd5-709">뮤텍스 성능 시스템 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-709">Mutex Performance System Info Get</span></span>

#### <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="eecd5-710">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-710">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="eecd5-711">**아이콘** ![뮤텍스 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-711">**Icon** ![Mutex performance system info get icon](./media/user-guide/tx-events/image37.png)</span></span>

<span data-ttu-id="eecd5-712">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-712">**Description**</span></span>

<span data-ttu-id="eecd5-713">이 이벤트는 tx_mutex_performance_system_info_get을 통해 뮤텍스 시스템 성능 정보를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-713">This event represents retrieving mutex system performance information via tx_mutex_performance_system_info_get.</span></span>

<span data-ttu-id="eecd5-714">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-714">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-715">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-715">Info Field 1: Not used.</span></span>
- <span data-ttu-id="eecd5-716">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-716">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-717">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-717">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-718">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-718">Info Field 4: Not used.</span></span>

### <a name="mutex-prioritize"></a><span data-ttu-id="eecd5-719">뮤텍스 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="eecd5-719">Mutex Prioritize</span></span> 

#### <a name="tx_mutex_prioritize"></a><span data-ttu-id="eecd5-720">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="eecd5-720">tx_mutex_prioritize</span></span>

<span data-ttu-id="eecd5-721">**아이콘** ![뮤텍스 우선 순위 지정 아이콘](./media/user-guide/tx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-721">**Icon** ![Mutex prioritize icon](./media/user-guide/tx-events/image38.png)</span></span>

<span data-ttu-id="eecd5-722">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-722">**Description**</span></span>

<span data-ttu-id="eecd5-723">이 이벤트는 tx_mutex_prioritize를 통해 뮤텍스 일시 중단 목록의 우선 순위를 지정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-723">This event represents prioritizing the mutex's suspension list via tx_mutex_prioritize.</span></span>

<span data-ttu-id="eecd5-724">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-724">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-725">정보 필드 1: 해당 뮤텍스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-725">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="eecd5-726">정보 필드 2: 뮤텍스에 대해 현재 일시 중단된 스레드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-726">Info Field 2: Number of threads currently suspended on the mutex.</span></span>
- <span data-ttu-id="eecd5-727">정보 필드 3: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-727">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-728">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-728">Info Field 4: Not used.</span></span>

### <a name="mutex-put"></a><span data-ttu-id="eecd5-729">뮤텍스 넣기</span><span class="sxs-lookup"><span data-stu-id="eecd5-729">Mutex Put</span></span> 

#### <a name="tx_mutex_put"></a><span data-ttu-id="eecd5-730">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="eecd5-730">tx_mutex_put</span></span>

<span data-ttu-id="eecd5-731">**아이콘** ![뮤텍스 넣기 아이콘](./media/user-guide/tx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-731">**Icon** ![Mutex put icon](./media/user-guide/tx-events/image39.png)</span></span>

<span data-ttu-id="eecd5-732">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-732">**Description**</span></span>

<span data-ttu-id="eecd5-733">이 이벤트는 tx_mutex_put을 통해 이전에 소유한 뮤텍스를 해제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-733">This event represents releasing a previously owned mutex via tx_mutex_put.</span></span>

<span data-ttu-id="eecd5-734">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-734">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-735">정보 필드 1: 해당 뮤텍스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-735">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="eecd5-736">정보 필드 2: 뮤텍스를 소유하는 스레드의 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-736">Info Field 2: Pointer of thread owning the mutex.</span></span>
- <span data-ttu-id="eecd5-737">정보 필드 3: 처리 중인 뮤텍스 가져오기 요청 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-737">Info Field 3: Number of outstanding mutex get requests.</span></span>
- <span data-ttu-id="eecd5-738">정보 필드 4: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-738">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="queue-create"></a><span data-ttu-id="eecd5-739">큐 만들기</span><span class="sxs-lookup"><span data-stu-id="eecd5-739">Queue Create</span></span> 

#### <a name="tx_queue_create"></a><span data-ttu-id="eecd5-740">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="eecd5-740">tx_queue_create</span></span>

<span data-ttu-id="eecd5-741">**아이콘** ![큐 만들기 아이콘](./media/user-guide/tx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-741">**Icon** ![Queue create icon](./media/user-guide/tx-events/image40.png)</span></span>

<span data-ttu-id="eecd5-742">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-742">**Description**</span></span>

<span data-ttu-id="eecd5-743">이 이벤트는 tx_queue_create를 통해 메시지 큐를 만드는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-743">This event represents creating a message queue via tx_queue_create.</span></span>

<span data-ttu-id="eecd5-744">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-744">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-745">정보 필드 1: 큐 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-745">Info Field 1: Pointer to queue control block.</span></span>
- <span data-ttu-id="eecd5-746">정보 필드 2: 32비트 단어를 기준으로 하는 메시지 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-746">Info Field 2: Size of message – in terms of 32-bit words.</span></span>
- <span data-ttu-id="eecd5-747">정보 필드 3: 큐 메모리 영역의 시작 부분에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-747">Info Field 3: Pointer to start of queue memory area.</span></span>
- <span data-ttu-id="eecd5-748">정보 필드 4: 큐 메모리 영역의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-748">Info Field 4: Number of bytes in the queue memory area.</span></span>

### <a name="queue-delete"></a><span data-ttu-id="eecd5-749">큐 삭제</span><span class="sxs-lookup"><span data-stu-id="eecd5-749">Queue Delete</span></span> 

#### <a name="tx_queue_delete"></a><span data-ttu-id="eecd5-750">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="eecd5-750">tx_queue_delete</span></span>

<span data-ttu-id="eecd5-751">**아이콘** ![큐 삭제 아이콘](./media/user-guide/tx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-751">**Icon** ![Queue delete icon](./media/user-guide/tx-events/image41.png)</span></span>

<span data-ttu-id="eecd5-752">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-752">**Description**</span></span>

<span data-ttu-id="eecd5-753">이 이벤트는 tx_queue_delete를 통해 큐를 삭제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-753">This event represents deleting a queue via tx_queue_delete.</span></span>

<span data-ttu-id="eecd5-754">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-754">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-755">정보 필드 1: 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-755">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="eecd5-756">정보 필드 2: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-756">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-757">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-757">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-758">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-758">Info Field 4: Not used.</span></span>

### <a name="queue-flush"></a><span data-ttu-id="eecd5-759">큐 플러시</span><span class="sxs-lookup"><span data-stu-id="eecd5-759">Queue Flush</span></span> 

#### <a name="tx_queue_flush"></a><span data-ttu-id="eecd5-760">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="eecd5-760">tx_queue_flush</span></span>

<span data-ttu-id="eecd5-761">**아이콘** ![큐 플러시 아이콘](./media/user-guide/tx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-761">**Icon** ![Queue flush icon](./media/user-guide/tx-events/image42.png)</span></span>

<span data-ttu-id="eecd5-762">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-762">**Description**</span></span>

<span data-ttu-id="eecd5-763">이 이벤트는 tx_queue_flush를 통해 큐의 플러시(모든 큐 콘텐츠 지우기)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-763">This event represents flushing (clearing all queue contents) of a queue via tx_queue_flush.</span></span>

<span data-ttu-id="eecd5-764">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-764">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-765">정보 필드 1: 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-765">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="eecd5-766">정보 필드 2: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-766">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-767">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-767">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-768">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-768">Info Field 4: Not used.</span></span>

### <a name="queue-front-send"></a><span data-ttu-id="eecd5-769">큐의 맨 앞으로 보내기</span><span class="sxs-lookup"><span data-stu-id="eecd5-769">Queue Front Send</span></span> 

#### <a name="tx_queue_front_send"></a><span data-ttu-id="eecd5-770">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="eecd5-770">tx_queue_front_send</span></span>

<span data-ttu-id="eecd5-771">**아이콘** ![큐의 맨 앞으로 보내기 아이콘](./media/user-guide/tx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-771">**Icon** ![Queue front send icon](./media/user-guide/tx-events/image43.png)</span></span>

<span data-ttu-id="eecd5-772">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-772">**Description**</span></span>

<span data-ttu-id="eecd5-773">이 이벤트는 tx_queue_front_send를 통해 큐의 맨 앞으로 메시지를 보내는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-773">This event represents sending a message to the front of a queue via tx_queue_front_send.</span></span>

<span data-ttu-id="eecd5-774">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-774">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-775">정보 필드 1: 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-775">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="eecd5-776">정보 필드 2: 메시지의 시작 부분에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-776">Info Field 2: Pointer to start of message.</span></span>
- <span data-ttu-id="eecd5-777">정보 필드 3: tx_queue_front_send 호출에 제공된</span><span class="sxs-lookup"><span data-stu-id="eecd5-777">Info Field 3: Wait option supplied to the</span></span>
- <span data-ttu-id="eecd5-778">대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-778">tx_queue_front_send call.</span></span>
- <span data-ttu-id="eecd5-779">정보 필드 4: 이미 큐에 넣은 메시지 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-779">Info Field 4: Number of messages already enqueued.</span></span>

### <a name="queue-information-get"></a><span data-ttu-id="eecd5-780">큐 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-780">Queue Information Get</span></span> 

#### <a name="tx_queue_info_get"></a><span data-ttu-id="eecd5-781">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-781">tx_queue_info_get</span></span>

<span data-ttu-id="eecd5-782">**아이콘** ![큐 정보 가져오기 아이콘](./media/user-guide/tx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-782">**Icon** ![Queue information get icon](./media/user-guide/tx-events/image44.png)</span></span>

<span data-ttu-id="eecd5-783">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-783">**Description**</span></span>

<span data-ttu-id="eecd5-784">이 이벤트는 tx_queue_info_get을 통해 큐에 대한 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-784">This event represents getting information about a queue via tx_queue_info_get.</span></span>

<span data-ttu-id="eecd5-785">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-785">**Information Fields**</span></span> 
- <span data-ttu-id="eecd5-786">정보 필드 1: 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-786">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="eecd5-787">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-787">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-788">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-788">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-789">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-789">Info Field 4: Not used.</span></span>

### <a name="queue-performance-info-get"></a><span data-ttu-id="eecd5-790">큐 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-790">Queue Performance Info Get</span></span> 

#### <a name="tx_queue_performance_info_get"></a><span data-ttu-id="eecd5-791">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-791">tx_queue_performance_info_get</span></span>

<span data-ttu-id="eecd5-792">**아이콘** ![큐 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-792">**Icon** ![Queue performance info get icon](./media/user-guide/tx-events/image45.png)</span></span>

<span data-ttu-id="eecd5-793">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-793">**Description**</span></span>

<span data-ttu-id="eecd5-794">이 이벤트는 tx_queue_performance_info_get을 통해 큐에 대한 성능 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-794">This event represents getting performance information about a queue via tx_queue_performance_info_get.</span></span>

<span data-ttu-id="eecd5-795">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-795">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-796">정보 필드 1: 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-796">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="eecd5-797">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-797">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-798">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-798">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-799">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-799">Info Field 4: Not used.</span></span>

### <a name="queue-performance-system-info-get"></a><span data-ttu-id="eecd5-800">큐 성능 시스템 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-800">Queue Performance System Info Get</span></span> 

#### <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="eecd5-801">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-801">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="eecd5-802">**아이콘** ![큐 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-802">**Icon** ![Queue performance system info get icon](./media/user-guide/tx-events/image46.png)</span></span>

<span data-ttu-id="eecd5-803">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-803">**Description**</span></span>

<span data-ttu-id="eecd5-804">이 이벤트는 시스템에 있는 모든 큐에 대한 시스템 성능 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-804">This event represents getting system performance information about all the queues in the system.</span></span>

<span data-ttu-id="eecd5-805">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-805">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-806">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-806">Info Field 1: Not used.</span></span>
- <span data-ttu-id="eecd5-807">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-807">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-808">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-808">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-809">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-809">Info Field 4: Not used.</span></span>

### <a name="queue-prioritize"></a><span data-ttu-id="eecd5-810">큐 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="eecd5-810">Queue Prioritize</span></span> 

#### <a name="tx_queue_prioritize"></a><span data-ttu-id="eecd5-811">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="eecd5-811">tx_queue_prioritize</span></span>

<span data-ttu-id="eecd5-812">**아이콘** ![큐 우선 순위 지정 아이콘](./media/user-guide/tx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-812">**Icon** ![Queue prioritize icon](./media/user-guide/tx-events/image47.png)</span></span>

<span data-ttu-id="eecd5-813">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-813">**Description**</span></span>

<span data-ttu-id="eecd5-814">이 이벤트는 tx_queue_prioritize를 통해 큐 일시 중단 목록의 우선 순위를 지정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-814">This event represents prioritizing the queue's suspension list via tx_queue_prioritize.</span></span>

<span data-ttu-id="eecd5-815">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-815">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-816">정보 필드 1: 해당 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-816">Info Field 1: Pointer to corresponding queue.</span></span>
- <span data-ttu-id="eecd5-817">정보 필드 2: 큐에 대해 현재 일시 중단된 스레드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-817">Info Field 2: Number of threads currently suspended on the queue.</span></span>
- <span data-ttu-id="eecd5-818">정보 필드 3: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-818">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-819">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-819">Info Field 4: Not used.</span></span>

#### <a name="queue-receive"></a><span data-ttu-id="eecd5-820">큐 수신</span><span class="sxs-lookup"><span data-stu-id="eecd5-820">Queue Receive</span></span> 

##### <a name="tx_queue_receive"></a><span data-ttu-id="eecd5-821">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="eecd5-821">tx_queue_receive</span></span>

<span data-ttu-id="eecd5-822">**아이콘** ![큐 수신 아이콘](./media/user-guide/tx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-822">**Icon** ![Queue receive icon](./media/user-guide/tx-events/image48.png)</span></span>

<span data-ttu-id="eecd5-823">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-823">**Description**</span></span>

<span data-ttu-id="eecd5-824">이 이벤트는 tx_queue_receive를 통해 큐에서 메시지를 수신하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-824">This event represents receiving a message from a queue via tx_queue_receive.</span></span>

<span data-ttu-id="eecd5-825">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-825">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-826">정보 필드 1: 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-826">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="eecd5-827">정보 필드 2: 메시지의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-827">Info Field 2: Pointer to destination for message.</span></span> <span data-ttu-id="eecd5-828">정보 필드 3: 호출에 제공되는 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-828">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="eecd5-829">정보 필드 4: 현재 큐에 대기 중인 메시지 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-829">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send"></a><span data-ttu-id="eecd5-830">큐 송신</span><span class="sxs-lookup"><span data-stu-id="eecd5-830">Queue Send</span></span> 

#### <a name="tx_queue_send"></a><span data-ttu-id="eecd5-831">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="eecd5-831">tx_queue_send</span></span>

<span data-ttu-id="eecd5-832">**아이콘** ![큐 송신 아이콘](./media/user-guide/tx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-832">**Icon** ![Queue send icon](./media/user-guide/tx-events/image49.png)</span></span>

<span data-ttu-id="eecd5-833">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-833">**Description**</span></span>

<span data-ttu-id="eecd5-834">이 이벤트는 tx_queue_send를 통해 큐에 메시지를 보내는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-834">This event represents sending a message to a queue via tx_queue_send.</span></span>

<span data-ttu-id="eecd5-835">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-835">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-836">정보 필드 1: 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-836">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="eecd5-837">정보 필드 2: 메시지에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-837">Info Field 2: Pointer to message.</span></span>
- <span data-ttu-id="eecd5-838">정보 필드 3: 호출에 제공되는 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-838">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="eecd5-839">정보 필드 4: 현재 큐에 대기 중인 메시지 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-839">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send-notify"></a><span data-ttu-id="eecd5-840">큐 송신 알림</span><span class="sxs-lookup"><span data-stu-id="eecd5-840">Queue Send Notify</span></span> 

#### <a name="tx_queue_send_notify"></a><span data-ttu-id="eecd5-841">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="eecd5-841">tx_queue_send_notify</span></span>

<span data-ttu-id="eecd5-842">**아이콘** ![큐 송신 알림 아이콘](./media/user-guide/tx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-842">**Icon** ![Queue send notify icon](./media/user-guide/tx-events/image50.png)</span></span>

<span data-ttu-id="eecd5-843">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-843">**Description**</span></span>

<p><span data-ttu-id="eecd5-844">이 이벤트는 메시지를 큐에 보낼 때마다 호출되는 tx_queue_send_notify를 통해 콜백을 등록하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-844">This event represents registering a callback via tx_queue_send_notify which is called whenever a message is sent to a queue.</span></span>

<span data-ttu-id="eecd5-845">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-845">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-846">정보 필드 1: 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-846">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="eecd5-847">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-847">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-848">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-848">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-849">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-849">Info Field 4: Not used.</span></span>

### <a name="semaphore-ceiling-put"></a><span data-ttu-id="eecd5-850">세마포 상한 넣기</span><span class="sxs-lookup"><span data-stu-id="eecd5-850">Semaphore Ceiling Put</span></span> 

#### <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="eecd5-851">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="eecd5-851">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="eecd5-852">**아이콘** ![세마포 상한 넣기 아이콘](./media/user-guide/tx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-852">**Icon** ![Semaphore ceiling put icon](./media/user-guide/tx-events/image51.png)</span></span>

<span data-ttu-id="eecd5-853">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-853">**Description**</span></span>

<span data-ttu-id="eecd5-854">이 이벤트는 tx_semaphore_ceiling_put을 통해 세마포에 넣는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-854">This event represents putting to a semaphore via tx_semaphore_ceiling_put.</span></span> <span data-ttu-id="eecd5-855">이는 넣기 작업이 최댓값 또는 상한을 초과할 수 없도록 세마포의 최댓값이 검사된다는 점에서 tx_semaphore_put과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-855">This differs from tx_semaphore_put in that the maximum value of the semaphore is examined such that the put operation is not allowed to exceed the maximum value or ceiling.</span></span>

<span data-ttu-id="eecd5-856">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-856">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-857">정보 필드 1: 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-857">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="eecd5-858">정보 필드 2: 현재 세마포 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-858">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="eecd5-859">정보 필드 3: 세마포에 대해 일시 중단된 스레드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-859">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="eecd5-860">정보 필드 4: 호출에 제공된 상한 제한입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-860">Info Field 4: Ceiling limit supplied to the call.</span></span>

#### <a name="semaphore-create"></a><span data-ttu-id="eecd5-861">세마포 만들기</span><span class="sxs-lookup"><span data-stu-id="eecd5-861">Semaphore Create</span></span> 

##### <a name="tx_semaphore_create"></a><span data-ttu-id="eecd5-862">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="eecd5-862">tx_semaphore_create</span></span>

<span data-ttu-id="eecd5-863">**아이콘** ![세마포 만들기 아이콘](./media/user-guide/tx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-863">**Icon** ![Semaphore create icon](./media/user-guide/tx-events/image52.png)</span></span>

<span data-ttu-id="eecd5-864">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-864">**Description**</span></span>

<span data-ttu-id="eecd5-865">이 이벤트는 tx_semaphore_create를 통해 세마포를 만드는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-865">This event represents creating a semaphore via tx_semaphore_create.</span></span>

<span data-ttu-id="eecd5-866">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-866">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-867">정보 필드 1: 세마포 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-867">Info Field 1: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="eecd5-868">정보 필드 2: 초기 세마포 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-868">Info Field 2: Initial semaphore count.</span></span>
- <span data-ttu-id="eecd5-869">정보 필드 3: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-869">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-870">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-870">Info Field 4: Not used.</span></span>

### <a name="semaphore-delete"></a><span data-ttu-id="eecd5-871">세마포 삭제</span><span class="sxs-lookup"><span data-stu-id="eecd5-871">Semaphore Delete</span></span> 

#### <a name="tx_semaphore_delete"></a><span data-ttu-id="eecd5-872">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="eecd5-872">tx_semaphore_delete</span></span>

<span data-ttu-id="eecd5-873">**아이콘** ![세마포 삭제 아이콘](./media/user-guide/tx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-873">**Icon** ![Semaphore delete icon](./media/user-guide/tx-events/image53.png)</span></span>

<span data-ttu-id="eecd5-874">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-874">**Description**</span></span>

<span data-ttu-id="eecd5-875">이 이벤트는 tx_semaphore_delete를 통해 세마포를 삭제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-875">This event represents deleting a semaphore via tx_semaphore_delete.</span></span>

<span data-ttu-id="eecd5-876">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-876">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-877">정보 필드 1: 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-877">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="eecd5-878">정보 필드 2: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-878">nfo Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-879">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-879">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-880">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-880">Info Field 4: Not used.</span></span>

### <a name="semaphore-get"></a><span data-ttu-id="eecd5-881">세마포 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-881">Semaphore Get</span></span> 

#### <a name="tx_semaphore_get"></a><span data-ttu-id="eecd5-882">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-882">tx_semaphore_get</span></span>

<span data-ttu-id="eecd5-883">**아이콘** ![세마포 가져오기 아이콘](./media/user-guide/tx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-883">**Icon** ![Semaphore get icon](./media/user-guide/tx-events/image54.png)</span></span>

<span data-ttu-id="eecd5-884">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-884">**Description**</span></span>

<span data-ttu-id="eecd5-885">이 이벤트는 tx_semaphore_get을 통해 세마포를 얻는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-885">This event represents obtaining a semaphore via tx_semaphore_get.</span></span>

<span data-ttu-id="eecd5-886">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-886">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-887">정보 필드 1: 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-887">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="eecd5-888">정보 필드 2: 호출에 제공되는 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-888">Info Field 2: Wait option supplied to the call.</span></span>
- <span data-ttu-id="eecd5-889">정보 필드 3: 현재 세마포 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-889">Info Field 3: Current semaphore count.</span></span>
- <span data-ttu-id="eecd5-890">정보 필드 4: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-890">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-information-get"></a><span data-ttu-id="eecd5-891">세마포 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-891">Semaphore Information Get</span></span> 

#### <a name="tx_semaphore_info_get"></a><span data-ttu-id="eecd5-892">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-892">tx_semaphore_info_get</span></span>

<span data-ttu-id="eecd5-893">**아이콘** ![세마포 정보 가져오기 아이콘](./media/user-guide/tx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-893">**Icon** ![Semaphore information get icon](./media/user-guide/tx-events/image55.png)</span></span>

<span data-ttu-id="eecd5-894">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-894">**Description**</span></span>

<span data-ttu-id="eecd5-895">이 이벤트는 tx_semaphore_info_get을 통해 세마포에 대한 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-895">This event represents obtaining information about a semaphore via tx_semaphore_info_get.</span></span>

<span data-ttu-id="eecd5-896">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-896">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-897">정보 필드 1: 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-897">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="eecd5-898">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-898">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-899">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-899">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-900">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-900">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-info-get"></a><span data-ttu-id="eecd5-901">세마포 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-901">Semaphore Performance Info Get</span></span> 

#### <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="eecd5-902">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-902">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="eecd5-903">**아이콘** ![세마포 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-903">**Icon** ![Semaphore performance info get icon](./media/user-guide/tx-events/image56.png)</span></span>

<span data-ttu-id="eecd5-904">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-904">**Description**</span></span>

<span data-ttu-id="eecd5-905">이 이벤트는 tx_semaphore_performance_info_get을 통해 세마포에 대한 성능 정보를 얻는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-905">This event represents obtaining performance information about a semaphore via tx_semaphore_performance_info_get.</span></span>

<span data-ttu-id="eecd5-906">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-906">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-907">정보 필드 1: 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-907">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="eecd5-908">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-908">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-909">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-909">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-910">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-910">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-system-info"></a><span data-ttu-id="eecd5-911">세마포 성능 시스템 정보</span><span class="sxs-lookup"><span data-stu-id="eecd5-911">Semaphore Performance System Info</span></span> 

#### <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="eecd5-912">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-912">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="eecd5-913">**아이콘** ![세마포 성능 시스템 정보 아이콘](./media/user-guide/tx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-913">**Icon** ![Semaphore performance system info icon](./media/user-guide/tx-events/image57.png)</span></span>

<span data-ttu-id="eecd5-914">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-914">**Description**</span></span>

<span data-ttu-id="eecd5-915">이 이벤트는 tx_semaphore_performance_system_info_get을 통해 시스템의 모든 세마포에 대한 성능 정보를 얻는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-915">This event represents obtaining performance information about all semaphores in the system via tx_semaphore_performance_system_info_get.</span></span>

<span data-ttu-id="eecd5-916">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-916">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-917">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-917">Info Field 1: Not used.</span></span>
- <span data-ttu-id="eecd5-918">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-918">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-919">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-919">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-920">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-920">Info Field 4: Not used.</span></span>

### <a name="semaphore-prioritize"></a><span data-ttu-id="eecd5-921">세마포 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="eecd5-921">Semaphore Prioritize</span></span> 

#### <a name="tx_semaphore_prioritize"></a><span data-ttu-id="eecd5-922">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="eecd5-922">tx_semaphore_prioritize</span></span>

<span data-ttu-id="eecd5-923">**아이콘** ![ 세마포 우선 순위 지정 아이콘](./media/user-guide/tx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-923">**Icon** ![Semaphore prioritize icon](./media/user-guide/tx-events/image58.png)</span></span>

<span data-ttu-id="eecd5-924">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-924">**Description**</span></span>

<span data-ttu-id="eecd5-925">이 이벤트는 tx_semaphore_prioritize를 통해 세마포 일시 중단 목록의 우선 순위를 지정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-925">This event represents prioritizing the semaphore's suspension list via tx_semaphore_prioritize.</span></span>

<span data-ttu-id="eecd5-926">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-926">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-927">정보 필드 1: 해당 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-927">Info Field 1: Pointer to corresponding semaphore.</span></span>
- <span data-ttu-id="eecd5-928">정보 필드 2: 세마포에 대해 현재 일시 중단된 스레드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-928">Info Field 2: Number of threads currently suspended on the semaphore.</span></span>
- <span data-ttu-id="eecd5-929">정보 필드 3: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-929">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-930">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-930">Info Field 4: Not used.</span></span>

### <a name="semaphore-put"></a><span data-ttu-id="eecd5-931">세마포 넣기</span><span class="sxs-lookup"><span data-stu-id="eecd5-931">Semaphore Put</span></span> 

#### <a name="tx_semaphore_put"></a><span data-ttu-id="eecd5-932">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="eecd5-932">tx_semaphore_put</span></span>

<span data-ttu-id="eecd5-933">**아이콘** ![세마포 넣기 아이콘](./media/user-guide/tx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-933">**Icon** ![Semaphore put icon](./media/user-guide/tx-events/image59.png)</span></span>

<span data-ttu-id="eecd5-934">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-934">**Description**</span></span>

<span data-ttu-id="eecd5-935">이 이벤트는 tx_semaphore_put을 통해 세마포 인스턴스를 해제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-935">This event represents releasing a semaphore instance via tx_semaphore_put.</span></span>

<span data-ttu-id="eecd5-936">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-936">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-937">정보 필드 1: 해당 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-937">Info Field 1: Pointer to corresponding semaphore.</span></span> <span data-ttu-id="eecd5-938">정보 필드 2: 현재 세마포 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-938">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="eecd5-939">정보 필드 3: 세마포에 대해 일시 중단된 스레드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-939">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="eecd5-940">정보 필드 4: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-940">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-put-notify"></a><span data-ttu-id="eecd5-941">세마포 넣기 알림</span><span class="sxs-lookup"><span data-stu-id="eecd5-941">Semaphore Put Notify</span></span> 

#### <a name="tx_semaphore_put_notify"></a><span data-ttu-id="eecd5-942">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="eecd5-942">tx_semaphore_put_notify</span></span>

<span data-ttu-id="eecd5-943">**아이콘** ![세마포 넣기 알림 아이콘](./media/user-guide/tx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-943">**Icon** ![Semaphore put notify icon](./media/user-guide/tx-events/image60.png)</span></span>

<span data-ttu-id="eecd5-944">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-944">**Description**</span></span>

<span data-ttu-id="eecd5-945">이 이벤트는 세마포 인스턴스를 넣을 때마다 호출되는 tx_semaphore_put_notify를 통해 콜백을 등록하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-945">This event represents registering a callback via tx_semaphore_put_notify that is called whenever a semaphore instance is put.</span></span>

<span data-ttu-id="eecd5-946">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-946">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-947">정보 필드 1: 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-947">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="eecd5-948">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-948">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-949">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-949">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-950">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-950">Info Field 4: Not used.</span></span>

### <a name="thread-create"></a><span data-ttu-id="eecd5-951">스레드 만들기</span><span class="sxs-lookup"><span data-stu-id="eecd5-951">Thread Create</span></span> 

#### <a name="tx_thread_create"></a><span data-ttu-id="eecd5-952">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="eecd5-952">tx_thread_create</span></span>

<span data-ttu-id="eecd5-953">**아이콘** ![스레드 만들기 아이콘](./media/user-guide/tx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-953">**Icon** ![Thread create icon](./media/user-guide/tx-events/image61.png)</span></span>

<span data-ttu-id="eecd5-954">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-954">**Description**</span></span>

<span data-ttu-id="eecd5-955">이 이벤트는 tx_thread_create를 통해 스레드를 만드는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-955">This event represents creating a thread via tx_thread_create.</span></span>

<span data-ttu-id="eecd5-956">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-956">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-957">정보 필드 1: 스레드 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-957">Info Field 1: Pointer to thread control block.</span></span>
- <span data-ttu-id="eecd5-958">정보 필드 2: 스레드의 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-958">Info Field 2: Priority of thread.</span></span>
- <span data-ttu-id="eecd5-959">정보 필드 3: 스레드에 대한 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-959">Info Field 3: Stack pointer for thread.</span></span>
- <span data-ttu-id="eecd5-960">정보 필드 4: 스택 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-960">nfo Field 4: Size of stack in bytes.</span></span>

### <a name="thread-delete"></a><span data-ttu-id="eecd5-961">스레드 삭제</span><span class="sxs-lookup"><span data-stu-id="eecd5-961">Thread Delete</span></span> 

#### <a name="tx_thread_delete"></a><span data-ttu-id="eecd5-962">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="eecd5-962">tx_thread_delete</span></span>

<span data-ttu-id="eecd5-963">**아이콘** ![스레드 삭제 아이콘](./media/user-guide/tx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-963">**Icon** ![Thread delete icon](./media/user-guide/tx-events/image62.png)</span></span>

<span data-ttu-id="eecd5-964">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-964">**Description**</span></span>

<span data-ttu-id="eecd5-965">이 이벤트는 tx_thread_delete를 통해 스레드를 삭제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-965">This event represents deleting a thread via tx_thread_delete.</span></span>

<span data-ttu-id="eecd5-966">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-966">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-967">정보 필드 1: 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-967">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="eecd5-968">정보 필드 2: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-968">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-969">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-969">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-970">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-970">Info Field 4: Not used.</span></span>

### <a name="thread-entryexit-notify"></a><span data-ttu-id="eecd5-971">스레드 진입/종료 알림</span><span class="sxs-lookup"><span data-stu-id="eecd5-971">Thread Entry/Exit Notify</span></span> 

#### <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="eecd5-972">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="eecd5-972">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="eecd5-973">**아이콘** ![스레드 진입/종료 알림 아이콘](./media/user-guide/tx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-973">**Icon** ![Thread entry/exit notify icon](./media/user-guide/tx-events/image63.png)</span></span>

<span data-ttu-id="eecd5-974">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-974">**Description**</span></span>

<span data-ttu-id="eecd5-975">이 이벤트는 스레드가 진입되거나 종료될 때마다 호출되는 tx_thread_entry_exit_notify를 통해 콜백을 등록하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-975">This event represents registering a callback via tx_thread_entry_exit_notify that is called whenever a thread is entered or exits.</span></span>

<span data-ttu-id="eecd5-976">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-976">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-977">정보 필드 1: 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-977">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="eecd5-978">정보 필드 2: 등록 시 스레드 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-978">Info Field 2: Thread state at time of the registration.</span></span>
- <span data-ttu-id="eecd5-979">정보 필드 3: 호출 시 스택에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-979">Info Field 3: Pointer to stack at time of call.</span></span>
- <span data-ttu-id="eecd5-980">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-980">Info Field 4: Not used.</span></span>

#### <a name="thread-identify"></a><span data-ttu-id="eecd5-981">스레드 식별</span><span class="sxs-lookup"><span data-stu-id="eecd5-981">Thread Identify</span></span> 

##### <a name="tx_thread_identify"></a><span data-ttu-id="eecd5-982">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="eecd5-982">tx_thread_identify</span></span>

<span data-ttu-id="eecd5-983">**아이콘** ![스레드 식별 아이콘](./media/user-guide/tx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-983">**Icon** ![Thread identify icon](./media/user-guide/tx-events/image64.png)</span></span>

<span data-ttu-id="eecd5-984">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-984">**Description**</span></span>

<span data-ttu-id="eecd5-985">이 이벤트는 tx_thread_identify를 통해 현재 스레드 포인터를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-985">This event represents getting the current thread pointer via tx_thread_identify.</span></span>

<span data-ttu-id="eecd5-986">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-986">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-987">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-987">Info Field 1: Not used.</span></span>
- <span data-ttu-id="eecd5-988">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-988">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-989">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-989">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-990">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-990">Info Field 4: Not used.</span></span>

### <a name="thread-information-get"></a><span data-ttu-id="eecd5-991">스레드 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-991">Thread Information Get</span></span> 

#### <a name="tx_thread_info_get"></a><span data-ttu-id="eecd5-992">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-992">tx_thread_info_get</span></span>

<span data-ttu-id="eecd5-993">**아이콘** ![스레드 정보 가져오기 아이콘](./media/user-guide/tx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-993">**Icon** ![Thread information get icon](./media/user-guide/tx-events/image65.png)</span></span>

<span data-ttu-id="eecd5-994">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-994">**Description**</span></span>

<span data-ttu-id="eecd5-995">이 이벤트는 tx_thread_info_get을 통해 지정된 스레드에 대한 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-995">This event represents getting information about the specified thread via tx_thread_info_get.</span></span>

<span data-ttu-id="eecd5-996">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-996">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-997">정보 필드 1: 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-997">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="eecd5-998">정보 필드 2: 호출 시 스레드 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-998">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="eecd5-999">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-999">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1000">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1000">Info Field 4: Not used.</span></span>

#### <a name="thread-performance-information-get"></a><span data-ttu-id="eecd5-1001">스레드 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-1001">Thread Performance Information Get</span></span> 

##### <a name="tx_thread_performance_info_get"></a><span data-ttu-id="eecd5-1002">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-1002">tx_thread_performance_info_get</span></span>

<span data-ttu-id="eecd5-1003">**아이콘** ![스레드 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1003">**Icon** ![Thread performance information get icon](./media/user-guide/tx-events/image66.png)</span></span>

<span data-ttu-id="eecd5-1004">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1004">**Description**</span></span>

<span data-ttu-id="eecd5-1005">이 이벤트는 tx_thread_performance_info_get을 통해 지정된 스레드에 대한 성능 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1005">This event represents getting performance information about the specified thread via tx_thread_performance_info_get.</span></span>

<span data-ttu-id="eecd5-1006">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1006">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1007">정보 필드 1: 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1007">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="eecd5-1008">정보 필드 2: 호출 시 스레드 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1008">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="eecd5-1009">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1009">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1010">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1010">Info Field 4: Not used.</span></span>

### <a name="thread-performance-system-info-get"></a><span data-ttu-id="eecd5-1011">스레드 성능 시스템 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-1011">Thread Performance System Info Get</span></span> 

#### <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="eecd5-1012">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-1012">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="eecd5-1013">**아이콘** ![스레드 성능 시스템 정보 가져오기 아이콘](./media/user-guide/tx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1013">**Icon** ![Thread performance system info get icon](./media/user-guide/tx-events/image67.png)</span></span>

<span data-ttu-id="eecd5-1014">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1014">**Description**</span></span>

<span data-ttu-id="eecd5-1015">이 이벤트는 tx_thread_performance_system_info_get을 통해 모든 스레드에 대한 성능 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1015">This event represents getting performance information about all threads via tx_thread_performance_system_info_get.</span></span>

<span data-ttu-id="eecd5-1016">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1016">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-1017">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1017">Info Field 1: Not used.</span></span>
- <span data-ttu-id="eecd5-1018">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1018">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-1019">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1019">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1020">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1020">Info Field 4: Not used.</span></span>

### <a name="thread-preemption-change"></a><span data-ttu-id="eecd5-1021">스레드 선점 변경</span><span class="sxs-lookup"><span data-stu-id="eecd5-1021">Thread Preemption Change</span></span> 

#### <a name="tx_thread_preemption_change"></a><span data-ttu-id="eecd5-1022">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="eecd5-1022">tx_thread_preemption_change</span></span>

<span data-ttu-id="eecd5-1023">**아이콘** ![스레드 선점 변경 아이콘](./media/user-guide/tx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1023">**Icon** ![Thread preemption change icon](./media/user-guide/tx-events/image68.png)</span></span>

<span data-ttu-id="eecd5-1024">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1024">**Description**</span></span>

<span data-ttu-id="eecd5-1025">이 이벤트는 tx_thread_preemption_change를 통해 스레드의 선점 임계값을 변경하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1025">This event represents changing a thread's preemption-threshold via tx_thread_preemption_change.</span></span>

<span data-ttu-id="eecd5-1026">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1026">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-1027">정보 필드 1: 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1027">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="eecd5-1028">정보 필드 2: 새 선점 임계값입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1028">Info Field 2: New preemption-threshold.</span></span>
- <span data-ttu-id="eecd5-1029">정보 필드 3: 이전 선점 임계값입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1029">Info Field 3: Previous preemption-threshold.</span></span>
- <span data-ttu-id="eecd5-1030">정보 필드 4: 호출 시 스레드의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1030">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-priority-change"></a><span data-ttu-id="eecd5-1031">스레드 우선 순위 변경</span><span class="sxs-lookup"><span data-stu-id="eecd5-1031">Thread Priority Change</span></span> 

#### <a name="tx_thread_priority_change"></a><span data-ttu-id="eecd5-1032">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="eecd5-1032">tx_thread_priority_change</span></span>

<span data-ttu-id="eecd5-1033">**아이콘** ![스레드 우선 순위 변경 아이콘](./media/user-guide/tx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1033">**Icon** ![Thread priority change icon](./media/user-guide/tx-events/image69.png)</span></span>

<span data-ttu-id="eecd5-1034">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1034">**Description**</span></span>

<span data-ttu-id="eecd5-1035">이 이벤트는 tx_thread_priority_change를 통해 스레드의 우선 순위를 변경하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1035">This event represents changing a thread's priority via tx_thread_priority_change.</span></span>

- <span data-ttu-id="eecd5-1036">정보 필드</span><span class="sxs-lookup"><span data-stu-id="eecd5-1036">Information Fields</span></span> 
- <span data-ttu-id="eecd5-1037">정보 필드 1: 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1037">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="eecd5-1038">정보 필드 2: 새 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1038">Info Field 2: New priority.</span></span>
- <span data-ttu-id="eecd5-1039">정보 필드 3: 이전 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1039">Info Field 3: Previous priority.</span></span>
- <span data-ttu-id="eecd5-1040">정보 필드 4: 호출 시 스레드의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1040">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-relinquish"></a><span data-ttu-id="eecd5-1041">스레드 양도</span><span class="sxs-lookup"><span data-stu-id="eecd5-1041">Thread Relinquish</span></span> 

#### <a name="tx_thread_relinquish"></a><span data-ttu-id="eecd5-1042">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="eecd5-1042">tx_thread_relinquish</span></span>

<span data-ttu-id="eecd5-1043">**아이콘** ![스레드 양도 아이콘](./media/user-guide/tx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1043">**Icon** ![Thread relinquish icon](./media/user-guide/tx-events/image70.png)</span></span>

<span data-ttu-id="eecd5-1044">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1044">**Description**</span></span>

<span data-ttu-id="eecd5-1045">이 이벤트는 tx_thread_relinquish를 통해 스레드에서 프로세서를 양도하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1045">This event represents relinquishing the processor from a thread via tx_thread_relinquish.</span></span>

<span data-ttu-id="eecd5-1046">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1046">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1047">정보 필드 1: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1047">Info Field 1: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-1048">정보 필드 2: 실행할 다음 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1048">Info Field 2: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="eecd5-1049">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1049">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1050">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1050">Info Field 4: Not used.</span></span>

### <a name="thread-reset"></a><span data-ttu-id="eecd5-1051">스레드 재설정</span><span class="sxs-lookup"><span data-stu-id="eecd5-1051">Thread Reset</span></span> 

#### <a name="tx_thread_reset"></a><span data-ttu-id="eecd5-1052">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="eecd5-1052">tx_thread_reset</span></span>

<span data-ttu-id="eecd5-1053">**아이콘** ![스레드 재설정 아이콘](./media/user-guide/tx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1053">**Icon** ![Thread reset icon](./media/user-guide/tx-events/image71.png)</span></span>

<span data-ttu-id="eecd5-1054">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1054">**Description**</span></span>

<span data-ttu-id="eecd5-1055">이 이벤트는 tx_thread_reset을 통해 완료되었거나 종료된 스레드를 재설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1055">This event represents resetting a completed or terminated thread via tx_thread_reset.</span></span>

<span data-ttu-id="eecd5-1056">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1056">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1057">정보 필드 1: 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1057">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="eecd5-1058">정보 필드 2: 호출 시 스레드의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1058">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="eecd5-1059">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1060">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1060">Info Field 4: Not used.</span></span>

#### <a name="thread-resume"></a><span data-ttu-id="eecd5-1061">스레드 다시 시작</span><span class="sxs-lookup"><span data-stu-id="eecd5-1061">Thread Resume</span></span> 

##### <a name="tx_thread_resume"></a><span data-ttu-id="eecd5-1062">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="eecd5-1062">tx_thread_resume</span></span>

<span data-ttu-id="eecd5-1063">**아이콘** ![스레드 다시 시작 아이콘](./media/user-guide/tx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1063">**Icon** ![Thread resume icon](./media/user-guide/tx-events/image72.png)</span></span>

<span data-ttu-id="eecd5-1064">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1064">**Description**</span></span>

<span data-ttu-id="eecd5-1065">이 이벤트는 tx_thread_resume을 통해 일시 중단된 스레드를 다시 시작하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1065">This event represents resuming a suspended thread via tx_thread_resume.</span></span>

<span data-ttu-id="eecd5-1066">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1066">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1067">정보 필드 1: 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1067">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="eecd5-1068">정보 필드 2: 호출 시 스레드의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1068">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="eecd5-1069">정보 필드 3: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1069">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-1070">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1070">Info Field 4: Not used.</span></span>

### <a name="thread-sleep"></a><span data-ttu-id="eecd5-1071">스레드 대기</span><span class="sxs-lookup"><span data-stu-id="eecd5-1071">Thread Sleep</span></span> 

#### <a name="tx_thread_sleep"></a><span data-ttu-id="eecd5-1072">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="eecd5-1072">tx_thread_sleep</span></span>

<span data-ttu-id="eecd5-1073">**아이콘** ![스레드 대기 아이콘](./media/user-guide/tx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1073">**Icon** ![Thread sleep icon](./media/user-guide/tx-events/image73.png)</span></span>

<span data-ttu-id="eecd5-1074">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1074">**Description**</span></span>

<span data-ttu-id="eecd5-1075">이 이벤트는 tx_thread_sleep을 통해 지정된 수의 타이머 틱에 대해 현재 스레드를 일시 중단하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1075">This event represents suspending the current thread for a specified number of timer ticks via tx_thread_sleep.</span></span>

<span data-ttu-id="eecd5-1076">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1076">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1077">정보 필드 1: 일시 중단할 틱 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1077">Info Field 1: Number of ticks to suspend for.</span></span>
- <span data-ttu-id="eecd5-1078">정보 필드 2: 호출 시 스레드의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1078">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="eecd5-1079">정보 필드 3: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1079">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-1080">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1080">Info Field 4: Not used.</span></span>

### <a name="thread-stack-error-notify"></a><span data-ttu-id="eecd5-1081">스레드 스택 오류 알림</span><span class="sxs-lookup"><span data-stu-id="eecd5-1081">Thread Stack Error Notify</span></span> 

#### <a name="tx_thread_stack_error_notify_event"></a><span data-ttu-id="eecd5-1082">tx_thread_stack_error_notify_event</span><span class="sxs-lookup"><span data-stu-id="eecd5-1082">tx_thread_stack_error_notify_event</span></span>

<span data-ttu-id="eecd5-1083">**아이콘** ![스레드 스택 오류 알림 아이콘](./media/user-guide/tx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1083">**Icon** ![Thread stack error notify icon](./media/user-guide/tx-events/image74.png)</span></span>

<span data-ttu-id="eecd5-1084">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1084">**Description**</span></span>

<span data-ttu-id="eecd5-1085">이 이벤트는 tx_thread_stack_error_notify_event를 통해 스레드 스택 오류 알림 루틴을 등록하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1085">This event represents registering a thread stack error notification routine via tx_thread_stack_error_notify_event.</span></span>

<span data-ttu-id="eecd5-1086">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1086">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-1087">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1087">Info Field 1: Not used.</span></span>
- <span data-ttu-id="eecd5-1088">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1088">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-1089">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1089">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1090">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1090">Info Field 4: Not used.</span></span>

### <a name="thread-suspend"></a><span data-ttu-id="eecd5-1091">스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="eecd5-1091">Thread Suspend</span></span> 

#### <a name="tx_thread_suspend"></a><span data-ttu-id="eecd5-1092">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="eecd5-1092">tx_thread_suspend</span></span>

<span data-ttu-id="eecd5-1093">**아이콘** ![스레드 일시 중단 아이콘](./media/user-guide/tx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1093">**Icon** ![Thread suspend icon](./media/user-guide/tx-events/image75.png)</span></span>

<span data-ttu-id="eecd5-1094">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1094">**Description**</span></span>

<span data-ttu-id="eecd5-1095">이 이벤트는 tx_thread_suspend를 통해 스레드를 일시 중단하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1095">This event represents suspending a thread via tx_thread_suspend.</span></span>

<span data-ttu-id="eecd5-1096">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1096">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-1097">정보 필드 1: 일시 중단할 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1097">Info Field 1: Pointer to thread to suspend.</span></span>
- <span data-ttu-id="eecd5-1098">정보 필드 2: 호출 시 스레드의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1098">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="eecd5-1099">정보 필드 3: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1099">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-1100">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1100">Info Field 4: Not used.</span></span>

### <a name="thread-terminate"></a><span data-ttu-id="eecd5-1101">스레드 종료</span><span class="sxs-lookup"><span data-stu-id="eecd5-1101">Thread Terminate</span></span> 

#### <a name="tx_thread_terminate"></a><span data-ttu-id="eecd5-1102">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="eecd5-1102">tx_thread_terminate</span></span>

<span data-ttu-id="eecd5-1103">**아이콘** ![스레드 종료 아이콘](./media/user-guide/tx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1103">**Icon** ![Thread terminate icon](./media/user-guide/tx-events/image76.png)</span></span>

<span data-ttu-id="eecd5-1104">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1104">**Description**</span></span>

<span data-ttu-id="eecd5-1105">이 이벤트는 tx_thread_terminate를 통해 스레드를 종료하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1105">This event represents terminating a thread via tx_thread_terminate.</span></span>

<span data-ttu-id="eecd5-1106">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1106">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-1107">정보 필드 1: 종료할 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1107">Info Field 1: Pointer to thread to terminate.</span></span>
- <span data-ttu-id="eecd5-1108">정보 필드 2: 호출 시 스레드의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1108">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="eecd5-1109">정보 필드 3: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1109">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-1110">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1110">Info Field 4: Not used.</span></span>

### <a name="thread-time-slice-change"></a><span data-ttu-id="eecd5-1111">스레드 시간 조각 변경</span><span class="sxs-lookup"><span data-stu-id="eecd5-1111">Thread Time-Slice Change</span></span> 

#### <a name="tx_thread_time_slice_change"></a><span data-ttu-id="eecd5-1112">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="eecd5-1112">tx_thread_time_slice_change</span></span>

<span data-ttu-id="eecd5-1113">**아이콘** ![스레드 시간 조각 변경 아이콘](./media/user-guide/tx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1113">**Icon** ![Thread time-slice change icon](./media/user-guide/tx-events/image77.png)</span></span>

<span data-ttu-id="eecd5-1114">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1114">**Description**</span></span>

<span data-ttu-id="eecd5-1115">이 이벤트는 tx_thread_time_slice_change를 통해 스레드의 시간 조각을 변경하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1115">This event represents changing a thread's time-slice via tx_thread_time_slice_change.</span></span>

<span data-ttu-id="eecd5-1116">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1116">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1117">정보 필드 1: 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1117">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="eecd5-1118">정보 필드 2: 새 시간 조각입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1118">Info Field 2: New time-slice.</span></span>
- <span data-ttu-id="eecd5-1119">정보 필드 3: 이전 시간 조각입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1119">Info Field 3: Previous time-slice.</span></span>
- <span data-ttu-id="eecd5-1120">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1120">Info Field 4: Not used.</span></span>

### <a name="thread-wait-abort"></a><span data-ttu-id="eecd5-1121">스레드 대기 중단</span><span class="sxs-lookup"><span data-stu-id="eecd5-1121">Thread Wait Abort</span></span> 

#### <a name="tx_thread_wait_abort"></a><span data-ttu-id="eecd5-1122">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="eecd5-1122">tx_thread_wait_abort</span></span>

<span data-ttu-id="eecd5-1123">**아이콘** ![스레드 대기 중단 아이콘](./media/user-guide/tx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1123">**Icon** ![Thread wait abort icon](./media/user-guide/tx-events/image78.png)</span></span>

<span data-ttu-id="eecd5-1124">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1124">**Description**</span></span>

<span data-ttu-id="eecd5-1125">이 이벤트는 tx_thread_wait_abort를 통해 스레드의 일시 중단을 중단하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1125">This event represents aborting a thread's suspension via tx_thread_wait_abort.</span></span>

<span data-ttu-id="eecd5-1126">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1126">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1127">정보 필드 1: 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1127">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="eecd5-1128">정보 필드 2: 호출 시 스레드의 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1128">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="eecd5-1129">정보 필드 3: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1129">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-1130">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1130">Info Field 4: Not used.</span></span>

### <a name="time-get"></a><span data-ttu-id="eecd5-1131">시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-1131">Time Get</span></span> 

#### <a name="tx_time_get"></a><span data-ttu-id="eecd5-1132">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-1132">tx_time_get</span></span>

<span data-ttu-id="eecd5-1133">**아이콘** ![시간 가져오기 아이콘](./media/user-guide/tx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1133">**Icon** ![Time get icon](./media/user-guide/tx-events/image79.png)</span></span>

<span data-ttu-id="eecd5-1134">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1134">**Description**</span></span>

<span data-ttu-id="eecd5-1135">이 이벤트는 tx_time_get을 통해 현재 타이머 틱 수를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1135">This event represents getting the current number of timer ticks via tx_time_get.</span></span>

<span data-ttu-id="eecd5-1136">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1136">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1137">정보 필드 1: 현재 타이머 틱 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1137">Info Field 1: Current number of timer ticks.</span></span>
- <span data-ttu-id="eecd5-1138">정보 필드 2: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1138">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-1139">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1139">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1140">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1140">Info Field 4: Not used.</span></span>

### <a name="time-set"></a><span data-ttu-id="eecd5-1141">시간 설정</span><span class="sxs-lookup"><span data-stu-id="eecd5-1141">Time Set</span></span> 

#### <a name="tx_time_set"></a><span data-ttu-id="eecd5-1142">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="eecd5-1142">tx_time_set</span></span>

<span data-ttu-id="eecd5-1143">**아이콘** ![시간 설정 아이콘](./media/user-guide/tx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1143">**Icon** ![Time set icon](./media/user-guide/tx-events/image80.png)</span></span>

<span data-ttu-id="eecd5-1144">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1144">**Description**</span></span>

<span data-ttu-id="eecd5-1145">이 이벤트는 tx_time_set을 통해 현재 타이머 틱 수를 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1145">This event represents setting the current number of timer ticks via tx_time_set.</span></span>

<span data-ttu-id="eecd5-1146">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1146">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1147">정보 필드 1: 새 타이머 틱 수입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1147">Info Field 1: New number of timer ticks.</span></span>
- <span data-ttu-id="eecd5-1148">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1148">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-1149">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1149">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1150">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1150">Info Field 4: Not used.</span></span>

### <a name="timer-activate"></a><span data-ttu-id="eecd5-1151">타이머 활성화</span><span class="sxs-lookup"><span data-stu-id="eecd5-1151">Timer Activate</span></span> 

#### <a name="tx_timer_activate"></a><span data-ttu-id="eecd5-1152">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="eecd5-1152">tx_timer_activate</span></span>

<span data-ttu-id="eecd5-1153">**아이콘** ![타이머 활성화 아이콘](./media/user-guide/tx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1153">**Icon** ![Timer activate icon](./media/user-guide/tx-events/image81.png)</span></span>

<span data-ttu-id="eecd5-1154">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1154">**Description**</span></span>

<span data-ttu-id="eecd5-1155">이 이벤트는 tx_timer_activate를 통해 지정된 타이머를 활성화하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1155">This event represents activating the specified timer via tx_timer_activate.</span></span>

<span data-ttu-id="eecd5-1156">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1156">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1157">정보 필드 1: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1157">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="eecd5-1158">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1158">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-1159">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1159">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1160">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1160">Info Field 4: Not used.</span></span>

### <a name="timer-change"></a><span data-ttu-id="eecd5-1161">타이머 변경</span><span class="sxs-lookup"><span data-stu-id="eecd5-1161">Timer Change</span></span> 

#### <a name="tx_timer_change"></a><span data-ttu-id="eecd5-1162">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="eecd5-1162">tx_timer_change</span></span>

<span data-ttu-id="eecd5-1163">**아이콘** ![타이머 변경 아이콘](./media/user-guide/tx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1163">**Icon** ![Timer change icon](./media/user-guide/tx-events/image82.png)</span></span>

<span data-ttu-id="eecd5-1164">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1164">**Description**</span></span>

<span data-ttu-id="eecd5-1165">이 이벤트는 tx_timer_change를 통해 지정된 타이머를 변경하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1165">This event represents changing the specified timer via tx_timer_change.</span></span>

<span data-ttu-id="eecd5-1166">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1166">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1167">정보 필드 1: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1167">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="eecd5-1168">정보 필드 2: 초기 만료 틱입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1168">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="eecd5-1169">정보 필드 3: 만료 틱을 다시 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1169">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="eecd5-1170">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1170">Info Field 4: Not used.</span></span>

### <a name="timer-create"></a><span data-ttu-id="eecd5-1171">타이머 만들기</span><span class="sxs-lookup"><span data-stu-id="eecd5-1171">Timer Create</span></span> 

#### <a name="tx_timer_create"></a><span data-ttu-id="eecd5-1172">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="eecd5-1172">tx_timer_create</span></span>

<span data-ttu-id="eecd5-1173">**아이콘** ![타이머 만들기 아이콘](./media/user-guide/tx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1173">**Icon** ![Timer create icon](./media/user-guide/tx-events/image83.png)</span></span>

<span data-ttu-id="eecd5-1174">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1174">**Description**</span></span>

<span data-ttu-id="eecd5-1175">이 이벤트는 tx_timer_create를 통해 타이머를 만드는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1175">This event represents creating a timer via tx_timer_create.</span></span>

<span data-ttu-id="eecd5-1176">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1176">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1177">정보 필드 1: 타이머 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1177">Info Field 1: Pointer to timer control block.</span></span>
- <span data-ttu-id="eecd5-1178">정보 필드 2: 초기 만료 틱입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1178">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="eecd5-1179">정보 필드 3: 만료 틱을 다시 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1179">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="eecd5-1180">정보 필드 4: 자동 사용 값인 TX_AUTO_ACTIVATE (1) 또는 TX_NO_ACTIVATE (0)입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1180">Info Field 4: Automatic enable value—either TX_AUTO_ACTIVATE (1) or TX_NO_ACTIVATE (0).</span></span>

### <a name="timer-deactivate"></a><span data-ttu-id="eecd5-1181">타이머 비활성화</span><span class="sxs-lookup"><span data-stu-id="eecd5-1181">Timer Deactivate</span></span> 

#### <a name="tx_timer_deactivate"></a><span data-ttu-id="eecd5-1182">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="eecd5-1182">tx_timer_deactivate</span></span>

<span data-ttu-id="eecd5-1183">**아이콘** ![타이머 비활성화 아이콘](./media/user-guide/tx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1183">**Icon** ![Timer deactivate icon](./media/user-guide/tx-events/image84.png)</span></span>

<span data-ttu-id="eecd5-1184">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1184">**Description**</span></span>

<span data-ttu-id="eecd5-1185">이 이벤트는 tx_timer_deactivate를 통한 타이머 비활성화를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1185">This event represents deactivating a timer via tx_timer_deactivate.</span></span>

<span data-ttu-id="eecd5-1186">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1186">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1187">정보 필드 1: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1187">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="eecd5-1188">정보 필드 2: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1188">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-1189">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1189">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1190">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1190">Info Field 4: Not used.</span></span>

### <a name="timer-delete"></a><span data-ttu-id="eecd5-1191">타이머 삭제</span><span class="sxs-lookup"><span data-stu-id="eecd5-1191">Timer Delete</span></span> 

#### <a name="tx_timer_delete"></a><span data-ttu-id="eecd5-1192">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="eecd5-1192">tx_timer_delete</span></span>

<span data-ttu-id="eecd5-1193">**아이콘** ![타이머 삭제 아이콘](./media/user-guide/tx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1193">**Icon** ![Timer delete icon](./media/user-guide/tx-events/image85.png)</span></span>

<span data-ttu-id="eecd5-1194">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1194">**Description**</span></span>

<span data-ttu-id="eecd5-1195">이 이벤트는 tx_timer_delete를 통해 타이머를 삭제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1195">This event represents deleting a timer via tx_timer_delete.</span></span>

<span data-ttu-id="eecd5-1196">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1196">**Information Fields**</span></span> 

- <span data-ttu-id="eecd5-1197">정보 필드 1: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1197">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="eecd5-1198">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1198">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-1199">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1199">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1200">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1200">Info Field 4: Not used.</span></span>

### <a name="timer-information-get"></a><span data-ttu-id="eecd5-1201">타이머 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-1201">Timer Information Get</span></span> 

#### <a name="tx_timer_info_get"></a><span data-ttu-id="eecd5-1202">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-1202">tx_timer_info_get</span></span>

<span data-ttu-id="eecd5-1203">**아이콘** ![타이머 정보 가져오기 아이콘](./media/user-guide/tx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1203">**Icon** ![Timer get information icon](./media/user-guide/tx-events/image86.png)</span></span>

<span data-ttu-id="eecd5-1204">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1204">**Description**</span></span>

<span data-ttu-id="eecd5-1205">이 이벤트는 tx_timer_info_get을 통해 타이머 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1205">This event represents getting timer information via tx_timer_info_get.</span></span>

<span data-ttu-id="eecd5-1206">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1206">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1207">정보 필드 1: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1207">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="eecd5-1208">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1208">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-1209">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1209">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1210">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1210">Info Field 4: Not used.</span></span>

### <a name="timer-performance-information-get"></a><span data-ttu-id="eecd5-1211">타이머 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-1211">Timer Performance Information Get</span></span> 

#### <a name="tx_timer_performance_info_get"></a><span data-ttu-id="eecd5-1212">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-1212">tx_timer_performance_info_get</span></span>

<span data-ttu-id="eecd5-1213">**아이콘** ![타이머 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1213">**Icon** ![Timer performance information get icon](./media/user-guide/tx-events/image87.png)</span></span>

<span data-ttu-id="eecd5-1214">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1214">**Description**</span></span> 

<span data-ttu-id="eecd5-1215">이 이벤트는 tx_timer_performance_info_get을 통해 타이머 성능 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1215">This event represents getting timer performance information via tx_timer_performance_info_get.</span></span>

<span data-ttu-id="eecd5-1216">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1216">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1217">정보 필드 1: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1217">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="eecd5-1218">정보 필드 2: 호출 시의 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1218">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="eecd5-1219">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1219">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1220">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1220">Info Field 4: Not used.</span></span>

### <a name="timer-system-performance-info-get"></a><span data-ttu-id="eecd5-1221">타이머 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="eecd5-1221">Timer System Performance Info Get</span></span> 

#### <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="eecd5-1222">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="eecd5-1222">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="eecd5-1223">**아이콘** ![타이머 시스템 성능 정보 가져오기 아이콘](./media/user-guide/tx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="eecd5-1223">**Icon** ![Timer system performance info get icon](./media/user-guide/tx-events/image88.png)</span></span>


<span data-ttu-id="eecd5-1224">**설명**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1224">**Description**</span></span> 

<span data-ttu-id="eecd5-1225">이 이벤트는 tx_timer_performance_system_info_get을 통해 모든 타이머 성능 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1225">This event represents getting all timer performance information via tx_timer_performance_system_info_get.</span></span>

<span data-ttu-id="eecd5-1226">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="eecd5-1226">**Information Fields**</span></span>

- <span data-ttu-id="eecd5-1227">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1227">Info Field 1: Not used.</span></span>
- <span data-ttu-id="eecd5-1228">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1228">Info Field 2: Not used.</span></span>
- <span data-ttu-id="eecd5-1229">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1229">Info Field 3: Not used.</span></span>
- <span data-ttu-id="eecd5-1230">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eecd5-1230">Info Field 4: Not used.</span></span>