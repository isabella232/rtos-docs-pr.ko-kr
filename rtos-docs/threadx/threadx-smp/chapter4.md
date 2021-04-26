---
title: 4장 - Azure RTOS ThreadX SMP 서비스 설명
description: 이 장에서는 모든 Azure RTOS ThreadX SMP 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4432001b773b4ef4f99b1b34193e90863966aad4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812840"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-smp-services"></a><span data-ttu-id="38207-103">4장 - Azure RTOS ThreadX SMP 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="38207-103">Chapter 4 - Description of Azure RTOS ThreadX SMP Services</span></span>

<span data-ttu-id="38207-104">이 장에서는 모든 Azure RTOS ThreadX SMP 서비스를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-104">This chapter contains a description of all Azure RTOS ThreadX SMP services in alphabetic order.</span></span> <span data-ttu-id="38207-105">서비스 이름은 모든 유사한 서비스가 함께 그룹화되도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="38207-106">다음 설명의 “반환 값” 섹션에서 **굵게** 표시된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **TX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않는 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-106">In the “Return Values” section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="38207-107">또한, “**가능한 선점**” 제목 아래 표시된 “**예**”는 서비스를 호출하면 우선 순위가 더 높은 스레드를 다시 시작할 수 있으므로 호출 스레드를 선점할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-107">In addition, a “**Yes**” listed under the “**Preemption Possible**” heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

- <span data-ttu-id="38207-108">**tx_block_allocate**: 고정 크기의 메모리 블록 할당</span><span class="sxs-lookup"><span data-stu-id="38207-108">**tx_block_allocate**: *Allocate fixed-size block of memory*</span></span> 
- <span data-ttu-id="38207-109">**tx_block_pool_create**: 고정 크기 메모리 블록의 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-109">**tx_block_pool_create**: *Create pool of fixed-size memory blocks*</span></span> 
- <span data-ttu-id="38207-110">**tx_block_pool_delete**: 메모리 블록 풀 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-110">**tx_block_pool_delete**: *Delete memory block pool*</span></span> 
- <span data-ttu-id="38207-111">**tx_block_pool_info_get**: 블록 풀에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-111">**tx_block_pool_info_get**: *Retrieve information about block pool*</span></span> 
- <span data-ttu-id="38207-112">**tx_block_pool_performance_info_get**: 블록 풀 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-112">**tx_block_pool_performance_info_get**: *Get block pool performance information*</span></span> 
- <span data-ttu-id="38207-113">**tx_block_pool_performance_system_info_get**: 블록 풀 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-113">**tx_block_pool_performance_system_info_get**: *Get block pool system performance information*</span></span> 
- <span data-ttu-id="38207-114">**tx_block_pool_prioritize**: 블록 풀 일시 중단 목록의 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="38207-114">**tx_block_pool_prioritize**: *Prioritize block pool suspension list*</span></span> 
- <span data-ttu-id="38207-115">**tx_block_release**: 고정 크기의 메모리 블록 해제</span><span class="sxs-lookup"><span data-stu-id="38207-115">**tx_block_release**: *Release fixed-size block of memory*</span></span>
- <span data-ttu-id="38207-116">**tx_byte_allocate**: 메모리 바이트 할당</span><span class="sxs-lookup"><span data-stu-id="38207-116">**tx_byte_allocate**: *Allocate bytes of memory*</span></span> 
- <span data-ttu-id="38207-117">**tx_byte_pool_create**: 바이트의 메모리 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-117">**tx_byte_pool_create**: *Create memory pool of bytes*</span></span> 
- <span data-ttu-id="38207-118">**tx_byte_pool_delete**: 메모리 바이트 풀 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-118">**tx_byte_pool_delete**: *Delete memory byte pool*</span></span> 
- <span data-ttu-id="38207-119">**tx_byte_pool_info_get**: 바이트 풀에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-119">**tx_byte_pool_info_get**: *Retrieve information about byte pool*</span></span> 
- <span data-ttu-id="38207-120">**tx_byte_pool_performance_info_get**: 바이트 풀 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-120">**tx_byte_pool_performance_info_get**: *Get byte pool performance information*</span></span> 
- <span data-ttu-id="38207-121">**tx_byte_pool_performance_system_info_get**: 바이트 풀 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-121">**tx_byte_pool_performance_system_info_get**: *Get byte pool system performance information*</span></span> 
- <span data-ttu-id="38207-122">**tx_byte_pool_prioritize**: 바이트 풀 일시 중단 목록 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="38207-122">**tx_byte_pool_prioritize**: *Prioritize byte pool suspension list*</span></span> 
- <span data-ttu-id="38207-123">**tx_byte_release**: 바이트를 메모리 풀로 다시 해제</span><span class="sxs-lookup"><span data-stu-id="38207-123">**tx_byte_release**: *Release bytes back to memory pool*</span></span> 
- <span data-ttu-id="38207-124">**tx_event_flags_create**: 이벤트 플래그 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-124">**tx_event_flags_create**: *Create event flags group*</span></span> 
- <span data-ttu-id="38207-125">**tx_event_flags_delete**: 이벤트 플래그 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-125">**tx_event_flags_delete**: *Delete event flags group*</span></span> 
- <span data-ttu-id="38207-126">**tx_event_flags_get**: 이벤트 플래그 그룹에서 이벤트 플래그 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-126">**tx_event_flags_get**: *Get event flags from event flags group*</span></span> 
- <span data-ttu-id="38207-127">**tx_event_flags_info_get**: 이벤트 플래그 그룹에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-127">**tx_event_flags_info_get**: *Retrieve information about event flags group*</span></span> 
- <span data-ttu-id="38207-128">**tx_event_flags_performance_info_get**: 이벤트 플래그 그룹 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-128">**tx_event_flags_performance_info_get**: *Get event flags group performance information*</span></span> 
- <span data-ttu-id="38207-129">**tx_event_flags_performance_system_info_get**: 성능 시스템 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-129">**tx_event_flags_performance_system_info_get**: *Retrieve performance system information*</span></span> 
- <span data-ttu-id="38207-130">**tx_event_flags_set**: 이벤트 플래그 그룹에서 이벤트 플래그 설정</span><span class="sxs-lookup"><span data-stu-id="38207-130">**tx_event_flags_set**: *Set event flags in an event flags group*</span></span> 
- <span data-ttu-id="38207-131">**tx_event_flags_set_notify**: 이벤트 플래그가 설정되면 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="38207-131">**tx_event_flags_set_notify**: *Notify application when event flags are set*</span></span>
- <span data-ttu-id="38207-132">**tx_interrupt_control**: 인터럽트 사용 및 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="38207-132">**tx_interrupt_control**: *Enable and disable interrupts*</span></span> 
- <span data-ttu-id="38207-133">**tx_mutex_create**: 상호 제외 뮤텍스 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-133">**tx_mutex_create**: *Create mutual exclusion mutex*</span></span> 
- <span data-ttu-id="38207-134">**tx_mutex_delete**: 상호 제외 뮤텍스 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-134">**tx_mutex_delete**: *Delete mutual exclusion mutex*</span></span> 
- <span data-ttu-id="38207-135">**tx_mutex_get**: 뮤텍스의 소유권 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-135">**tx_mutex_get**: *Obtain ownership of mutex*</span></span> 
- <span data-ttu-id="38207-136">**tx_mutex_info_get**: 뮤텍스에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-136">**tx_mutex_info_get**: *Retrieve information about mutex*</span></span> 
- <span data-ttu-id="38207-137">**tx_mutex_performance_info_get**: 뮤텍스 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-137">**tx_mutex_performance_info_get**: *Get mutex performance information*</span></span> 
- <span data-ttu-id="38207-138">**tx_mutex_performance_system_info_get**: 뮤텍스 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-138">**tx_mutex_performance_system_info_get**: *Get mutex system performance information*</span></span> 
- <span data-ttu-id="38207-139">**tx_mutex_prioritize**: 뮤텍스 일시 중단 목록 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="38207-139">**tx_mutex_prioritize**: *Prioritize mutex suspension list*</span></span> 
- <span data-ttu-id="38207-140">**tx_mutex_put**: 뮤텍스의 소유권 해제</span><span class="sxs-lookup"><span data-stu-id="38207-140">**tx_mutex_put**: *Release ownership of mutex*</span></span> 
- <span data-ttu-id="38207-141">**tx_queue_create**: 메시지 큐 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-141">**tx_queue_create**: *Create message queue*</span></span> 
- <span data-ttu-id="38207-142">**tx_queue_delete**: 메시지 큐 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-142">**tx_queue_delete**: *Delete message queue*</span></span> 
- <span data-ttu-id="38207-143">**tx_queue_flush**: 메시지 큐의 메시지 비우기</span><span class="sxs-lookup"><span data-stu-id="38207-143">**tx_queue_flush**: *Empty messages in message queue*</span></span> 
- <span data-ttu-id="38207-144">**tx_queue_front_send**: 큐 맨 앞에 메시지 보내기</span><span class="sxs-lookup"><span data-stu-id="38207-144">**tx_queue_front_send**: *Send message to the front of queue*</span></span> 
- <span data-ttu-id="38207-145">**tx_queue_info_get**: 큐에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-145">**tx_queue_info_get**: *Retrieve information about queue*</span></span> 
- <span data-ttu-id="38207-146">**tx_queue_performance_info_get**: 큐 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-146">**tx_queue_performance_info_get**: *Get queue performance information*</span></span> 
- <span data-ttu-id="38207-147">**tx_queue_performance_system_info_get**: 큐 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-147">**tx_queue_performance_system_info_get**: *Get queue system performance information*</span></span>
- <span data-ttu-id="38207-148">**tx_queue_prioritize**: 큐 일시 중단 목록 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="38207-148">**tx_queue_prioritize**: *Prioritize queue suspension list*</span></span> 
- <span data-ttu-id="38207-149">**tx_queue_receive**: 메시지 큐에서 메시지 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-149">**tx_queue_receive**: *Get message from message queue*</span></span> 
- <span data-ttu-id="38207-150">**tx_queue_send**: 메시지 큐로 메시지 보내기</span><span class="sxs-lookup"><span data-stu-id="38207-150">**tx_queue_send**: *Send message to message queue*</span></span> 
- <span data-ttu-id="38207-151">**tx_queue_send_notify**: 메시지가 큐에 전송될 때 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="38207-151">**tx_queue_send_notify**: *Notify application when message is sent to queue*</span></span> 
- <span data-ttu-id="38207-152">**tx_semaphore_ceiling_put**: 상한을 지정하여 계산 세마포에 인스턴스 배치</span><span class="sxs-lookup"><span data-stu-id="38207-152">**tx_semaphore_ceiling_put**: *Place an instance in counting semaphore with ceiling*</span></span> 
- <span data-ttu-id="38207-153">**tx_semaphore_create**: 계산 세마포 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-153">**tx_semaphore_create**: *Create counting semaphore*</span></span> 
- <span data-ttu-id="38207-154">**tx_semaphore_delete**: 계산 세마포 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-154">**tx_semaphore_delete**: *Delete counting semaphore*</span></span> 
- <span data-ttu-id="38207-155">**tx_semaphore_get**: 계산 세마포에 대한 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-155">**tx_semaphore_get**: *Get instance from counting semaphore*</span></span> 
- <span data-ttu-id="38207-156">**tx_semaphore_info_get**: 세마포에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-156">**tx_semaphore_info_get**: *Retrieve information about semaphore*</span></span> 
- <span data-ttu-id="38207-157">**tx_semaphore_performance_info_get**: 세마포 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-157">**tx_semaphore_performance_info_get**: *Get semaphore performance information*</span></span> 
- <span data-ttu-id="38207-158">**tx_semaphore_performance_system_info_get**: 세마포 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-158">**tx_semaphore_performance_system_info_get**: *Get semaphore system performance information*</span></span> 
- <span data-ttu-id="38207-159">**tx_semaphore_prioritize**: 세마포 일시 중단 목록 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="38207-159">**tx_semaphore_prioritize**: *Prioritize semaphore suspension list*</span></span> 
- <span data-ttu-id="38207-160">**tx_semaphore_put**: 계산 세마포에 인스턴스 배치</span><span class="sxs-lookup"><span data-stu-id="38207-160">**tx_semaphore_put**: *Place an instance in counting semaphore*</span></span> 
- <span data-ttu-id="38207-161">**tx_semaphore_put_notify**: 세마포가 배치 될 때 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="38207-161">**tx_semaphore_put_notify**: *Notify application when semaphore is put*</span></span> 
- <span data-ttu-id="38207-162">**tx_thread_create**: 애플리케이션 스레드 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-162">**tx_thread_create**: *Create application thread*</span></span> 
- <span data-ttu-id="38207-163">**tx_thread_delete**: 애플리케이션 스레드 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-163">**tx_thread_delete**: *Delete application thread*</span></span>
- <span data-ttu-id="38207-164">**tx_thread_entry_exit_notify**: 스레드 입력 및 종료 시 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="38207-164">**tx_thread_entry_exit_notify**: *Notify application upon thread entry and exit*</span></span> 
- <span data-ttu-id="38207-165">**tx_thread_identify**: 현재 실행 중인 스레드에 대한 포인터 검색</span><span class="sxs-lookup"><span data-stu-id="38207-165">**tx_thread_identify**: *Retrieves pointer to currently executing thread*</span></span> 
- <span data-ttu-id="38207-166">**tx_thread_info_get**: 스레드에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-166">**tx_thread_info_get**: *Retrieve information about thread*</span></span> 
- <span data-ttu-id="38207-167">**tx_thread_performance_info_get**: 스레드 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-167">**tx_thread_performance_info_get**: *Get thread performance information*</span></span> 
- <span data-ttu-id="38207-168">**tx_thread_performance_system_info_get**: 스레드 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-168">**tx_thread_performance_system_info_get**: *Get thread system performance information*</span></span> 
- <span data-ttu-id="38207-169">**tx_thread_preemption_change**: 애플리케이션 스레드의 선점 임계값 변경</span><span class="sxs-lookup"><span data-stu-id="38207-169">**tx_thread_preemption_change**: *Change preemption-threshold of application thread*</span></span> 
- <span data-ttu-id="38207-170">**tx_thread_priority_change**: 애플리케이션 스레드의 우선 순위 변경</span><span class="sxs-lookup"><span data-stu-id="38207-170">**tx_thread_priority_change**: *Change priority of application thread*</span></span> 
- <span data-ttu-id="38207-171">**tx_thread_relinquish**: 다른 애플리케이션 스레드에 대한 제어권 포기</span><span class="sxs-lookup"><span data-stu-id="38207-171">**tx_thread_relinquish**: *Relinquish control to other application threads*</span></span> 
- <span data-ttu-id="38207-172">**tx_thread_reset**: 스레드 다시 설정</span><span class="sxs-lookup"><span data-stu-id="38207-172">**tx_thread_reset**: *Reset thread*</span></span> 
- <span data-ttu-id="38207-173">**tx_thread_resume**: 일시 중단된 애플리케이션 스레드 다시 시작</span><span class="sxs-lookup"><span data-stu-id="38207-173">**tx_thread_resume**: *Resume suspended application thread*</span></span> 
- <span data-ttu-id="38207-174">**tx_thread_sleep**: 지정된 시간 동안 현재 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="38207-174">**tx_thread_sleep**: *Suspend current thread for specified time*</span></span> 
- <span data-ttu-id="38207-175">**tx_thread_smp_core_exclude**: 코어 세트에서 스레드 실행 제외</span><span class="sxs-lookup"><span data-stu-id="38207-175">**tx_thread_smp_core_exclude**: *Exclude thread execution on a set of cores*</span></span> 
- <span data-ttu-id="38207-176">**tx_thread_smp_core_exclude_get**: 스레드의 현재 코어 제외 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-176">**tx_thread_smp_core_exclude_get**: *Gets the thread's current core exclusion*</span></span> 
- <span data-ttu-id="38207-177">**tx_thread_smp_core_get**: 현재 실행 중인 호출자의 코어 검색</span><span class="sxs-lookup"><span data-stu-id="38207-177">**tx_thread_smp_core_get**: *Retrieve currently executing core of caller*</span></span> 
- <span data-ttu-id="38207-178">**tx_thread_stack_error_notify**: 스레드 스택 오류 알림 콜백 등록</span><span class="sxs-lookup"><span data-stu-id="38207-178">**tx_thread_stack_error_notify**: *Register thread stack error notification callback*</span></span> 
- <span data-ttu-id="38207-179">**tx_thread_suspend**: 애플리케이션 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="38207-179">**tx_thread_suspend**: *Suspend application thread*</span></span>
- <span data-ttu-id="38207-180">**tx_thread_terminate**: 애플리케이션 스레드 종료</span><span class="sxs-lookup"><span data-stu-id="38207-180">**tx_thread_terminate**: *Terminates application thread*</span></span> 
- <span data-ttu-id="38207-181">**tx_thread_time_slice_change**: 애플리케이션 스레드의 시간 조각 변경</span><span class="sxs-lookup"><span data-stu-id="38207-181">**tx_thread_time_slice_change**: *Changes time-slice of application thread*</span></span> 
- <span data-ttu-id="38207-182">**tx_thread_wait_abort**: 지정된 스레드의 일시 중단 중단</span><span class="sxs-lookup"><span data-stu-id="38207-182">**tx_thread_wait_abort**: *Abort suspension of specified thread*</span></span> 
- <span data-ttu-id="38207-183">**tx_time_get**: 현재 시간 검색</span><span class="sxs-lookup"><span data-stu-id="38207-183">**tx_time_get**: *Retrieves the current time*</span></span> 
- <span data-ttu-id="38207-184">**tx_time_set**: 현재 시간 설정</span><span class="sxs-lookup"><span data-stu-id="38207-184">**tx_time_set**: *Sets the current time*</span></span> 
- <span data-ttu-id="38207-185">**tx_timer_activate**: 애플리케이션 타이머 활성화</span><span class="sxs-lookup"><span data-stu-id="38207-185">**tx_timer_activate**: *Activate application timer*</span></span> 
- <span data-ttu-id="38207-186">**tx_timer_change**: 애플리케이션 타이머 변경</span><span class="sxs-lookup"><span data-stu-id="38207-186">**tx_timer_change**: *Change application timer*</span></span> 
- <span data-ttu-id="38207-187">**tx_timer_create**: 애플리케이션 타이머 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-187">**tx_timer_create**: *Create application timer*</span></span> 
- <span data-ttu-id="38207-188">**tx_timer_deactivate**: 애플리케이션 타이머 비활성화</span><span class="sxs-lookup"><span data-stu-id="38207-188">**tx_timer_deactivate**: *Deactivate application timer*</span></span> 
- <span data-ttu-id="38207-189">**tx_timer_delete**: 애플리케이션 타이머 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-189">**tx_timer_delete**: *Delete application timer*</span></span> 
- <span data-ttu-id="38207-190">**tx_timer_info_get**: 애플리케이션 타이머에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-190">**tx_timer_info_get**: *Retrieve information about an application timer*</span></span> 
- <span data-ttu-id="38207-191">**tx_timer_performance_info_get**: 타이머 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-191">**tx_timer_performance_info_get**: *Get timer performance information*</span></span> 
- <span data-ttu-id="38207-192">**tx_timer_performance_system_info_get**: 타이머 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-192">**tx_timer_performance_system_info_get**: *Get timer system performance information*</span></span> 
- <span data-ttu-id="38207-193">**tx_timer_smp_core_exclude**: 코어 세트에서 타이머 실행 제외</span><span class="sxs-lookup"><span data-stu-id="38207-193">**tx_timer_smp_core_exclude**: *Exclude timer execution on a set of cores*</span></span> 
- <span data-ttu-id="38207-194">**tx_timer_smp_core_exclude_get**: 타이머의 현재 코어 제외 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-194">**tx_timer_smp_core_exclude_get**: *Gets the timer's current core exclusion*</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="38207-195">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-195">tx_block_allocate</span></span>
<span data-ttu-id="38207-196">고정 크기의 메모리 블록 할당</span><span class="sxs-lookup"><span data-stu-id="38207-196">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-197">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-197">Prototype</span></span>

```C
UINT tx_block_allocate(TX_BLOCK_POOL *pool_ptr, VOID **block_ptr,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="38207-198">Description</span><span class="sxs-lookup"><span data-stu-id="38207-198">Description</span></span>

<span data-ttu-id="38207-199">이 서비스는 지정된 메모리 풀에서 고정 크기 메모리 블록을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-199">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="38207-200">메모리 블록의 실제 크기는 메모리 풀을 만드는 동안 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-200">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!WARNING]
> <span data-ttu-id="38207-201">애플리케이션 코드는 할당 된 메모리 블록 외부에 쓰지 않도록 하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-201">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="38207-202">만약 그렇게 되면 인접한(일반적으로 후속) 메모리 블록에서 손상이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-202">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="38207-203">결과는 예측할 수 없으며 치명적인 경우도 많습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-203">The results are unpredictable and are often fatal!</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-204">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-204">Parameters</span></span>

- <span data-ttu-id="38207-205">**pool_ptr**: 이전에 만든 메모리 블록 풀을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-205">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="38207-206">**block_ptr**: 대상 블록 포인터를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-206">**block_ptr**: Pointer to a destination block pointer.</span></span> <span data-ttu-id="38207-207">할당에 성공하면 할당된 메모리 블록 주소가 이 매개 변수에서 가리키는 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-207">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="38207-208">**wait_option**: 사용할 수 있는 메모리 블록이 없는 경우의 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-208">**wait_option**: Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="38207-209">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-209">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38207-210">**TX_NO_WAIT**:(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="38207-210">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="38207-211">**TX_WAIT_FOREVER**:(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38207-211">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="38207-212">시간 제한 값:(0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38207-212">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>  
    
    <span data-ttu-id="38207-213">TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-213">Selecting TX_NO_WAIT results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="38207-214">초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-214">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="38207-215">TX_WAIT_FOREVER를 선택하면 메모리 블록을 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-215">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a memory block is available.</span></span>

    <span data-ttu-id="38207-216">숫자 값(1-0xFFFFFFFE)을 선택하면 메모리 블록을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-216">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-217">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-217">Return Values</span></span>

- <span data-ttu-id="38207-218">**TX_SUCCESS**:(0x00) 메모리 블록 할당에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-218">**TX_SUCCESS**: (0x00) Successful memory block allocation.</span></span>
- <span data-ttu-id="38207-219">**TX_DELETED**:(0x01) 스레드가 일시 중단된 동안 메모리 블록 풀이 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-219">**TX_DELETED**: (0x01) Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="38207-220">**TX_NO_MEMORY**(0x10) 서비스가 지정된 대기 시간 내에 메모리 블록을 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-220">**TX_NO_MEMORY**: (0x10) Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="38207-221">**TX_WAIT_ABORTED**:(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-221">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="38207-222">TX_POOL_ERROR:(0x02) 잘못된 메모리 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-222">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="38207-223">TX_PTR_ERROR:(0x03) 대상 포인터를 가리키는 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-223">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="38207-224">TX_WAIT_ERROR:(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-224">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-225">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-225">Allowed From</span></span>

<span data-ttu-id="38207-226">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-226">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-227">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-227">Preemption Possible</span></span>

<span data-ttu-id="38207-228">예</span><span class="sxs-lookup"><span data-stu-id="38207-228">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-229">예제</span><span class="sxs-lookup"><span data-stu-id="38207-229">Example</span></span>

```c
TX_BLOCK_POOL   my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a memory block from my_pool. Assume that the
   pool has already been created with a call to
   tx_block_pool_create. */
status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
                               TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated block of memory. */
```

### <a name="see-also"></a><span data-ttu-id="38207-230">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-230">See Also</span></span>

- <span data-ttu-id="38207-231">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-231">tx_block_pool_create</span></span>
- <span data-ttu-id="38207-232">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-232">tx_block_pool_delete</span></span>
- <span data-ttu-id="38207-233">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-233">tx_block_pool_info_get</span></span>
- <span data-ttu-id="38207-234">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-234">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-235">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-235">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-236">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-236">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="38207-237">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="38207-237">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="38207-238">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-238">tx_block_pool_create</span></span>
<span data-ttu-id="38207-239">고정 크기 메모리 블록의 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-239">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-240">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-240">Prototype</span></span>

```C
UINT tx_block_pool_create(TX_BLOCK_POOL *pool_ptr,
                          CHAR *name_ptr, ULONG block_size,
                          VOID *pool_start, ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="38207-241">Description</span><span class="sxs-lookup"><span data-stu-id="38207-241">Description</span></span>

<span data-ttu-id="38207-242">이 서비스는 고정 크기 메모리 블록 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38207-242">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="38207-243">지정된 메모리 영역은 다음 수식을 사용하여 가능한 한 많은 고정 크기 메모리 블록으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-243">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>    
<span data-ttu-id="38207-244">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span><span class="sxs-lookup"><span data-stu-id="38207-244">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-245">각 메모리 블록에는 사용자에게 표시되지 않고 앞의 수식에서 “sizeof(void \*)”로 표시되는 오버헤드 포인터 하나가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-245">Each memory block contains one pointer of overhead that is invisible to the user and is represented by the “sizeof(void \*)” in the preceding formula.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-246">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-246">Parameters</span></span>

- <span data-ttu-id="38207-247">**pool_ptr**: 메모리 블록 풀 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-247">**pool_ptr**: Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="38207-248">**name_ptr**: 메모리 블록 풀의 이름을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-248">**name_ptr**: Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="38207-249">**block_size**: 각 메모리 블록의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-249">**block_size**: Number of bytes in each memory block.</span></span>
- <span data-ttu-id="38207-250">**pool_start**: 메모리 블록 풀의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-250">**pool_start**: Starting address of the memory block pool.</span></span> <span data-ttu-id="38207-251">시작 주소는 ULONG 데이터 형식의 크기에 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-251">The starting address must be aligned to the size of the ULONG data type..</span></span>
- <span data-ttu-id="38207-252">**pool_size**: 메모리 블록 풀에 사용할 수 있는 총 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-252">**pool_size**: Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-253">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-253">Return Values</span></span>

- <span data-ttu-id="38207-254">**TX_SUCCESS**:(0x00) 메모리 블록 풀 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-254">**TX_SUCCESS**: (0x00) Successful memory block pool creation.</span></span>
- <span data-ttu-id="38207-255">TX_POOL_ERROR:(0x02) 잘못된 메모리 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-255">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span> <span data-ttu-id="38207-256">포인터가 NULL이거나 풀이 이미 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-256">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="38207-257">TX_PTR_ERROR:(0x03) 풀의 시작 주소가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-257">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="38207-258">TX_SIZE_ERROR:(0x05) 풀 크기가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-258">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="38207-259">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-259">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-260">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-260">Allowed From</span></span>

<span data-ttu-id="38207-261">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="38207-261">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-262">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-262">Preemption Possible</span></span>

<span data-ttu-id="38207-263">예</span><span class="sxs-lookup"><span data-stu-id="38207-263">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-264">예제</span><span class="sxs-lookup"><span data-stu-id="38207-264">Example</span></span>

```C
TX_BLOCK_POOL  my_pool;
UINT           status;

/* Create a memory pool whose total size is 1000 bytes
   starting at address 0x100000. Each block in this
   pool is defined to be 50 bytes long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
               50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18
   memory blocks of 50 bytes each. The reason
   there are not 20 blocks in the pool is
   because of the one overhead pointer associated with each
   block. */
```
### <a name="see-also"></a><span data-ttu-id="38207-265">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-265">See Also</span></span>

- <span data-ttu-id="38207-266">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-266">tx_block_allocate</span></span>
- <span data-ttu-id="38207-267">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-267">tx_block_pool_delete</span></span>
- <span data-ttu-id="38207-268">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-268">tx_block_pool_info_get</span></span>
- <span data-ttu-id="38207-269">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-269">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-270">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-270">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-271">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-271">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="38207-272">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="38207-272">tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="38207-273">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-273">tx_block_pool_delete</span></span>

<span data-ttu-id="38207-274">메모리 블록 풀 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-274">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-275">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-275">Prototype</span></span>

```C
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-276">Description</span><span class="sxs-lookup"><span data-stu-id="38207-276">Description</span></span>

<span data-ttu-id="38207-277">이 서비스는 지정된 블록 메모리 풀을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-277">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="38207-278">이 풀에서 메모리 블록을 기다리는 동안 일시 중단된 모든 스레드가 다시 시작되며 TX_DELETED 반환 상태가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-278">All threads suspended waiting for a memory block from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-279">이 서비스가 완료된 후에 사용할 수 있는 풀과 연결된 메모리 영역을 관리하는 것은 애플리케이션의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-279">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="38207-280">또한 애플리케이션은 삭제된 풀이나 이전 메모리 블록을 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-280">In addition, the application must prevent use of a deleted pool or its former memory blocks.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-281">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-281">Parameters</span></span>

- <span data-ttu-id="38207-282">**pool_ptr**: 이전에 만든 메모리 블록 풀을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-282">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-283">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-283">Return Values</span></span>

- <span data-ttu-id="38207-284">**TX_SUCCESS**:(0x00) 메모리 블록 풀 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-284">**TX_SUCCESS**: (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="38207-285">TX_POOL_ERROR:(0x02) 잘못된 메모리 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-285">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="38207-286">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-286">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-287">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-287">Allowed From</span></span>

<span data-ttu-id="38207-288">스레드</span><span class="sxs-lookup"><span data-stu-id="38207-288">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-289">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-289">Preemption Possible</span></span>

<span data-ttu-id="38207-290">예</span><span class="sxs-lookup"><span data-stu-id="38207-290">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-291">예제</span><span class="sxs-lookup"><span data-stu-id="38207-291">Example</span></span>

```C
TX_BLOCK_POOLmy_pool;
UINT           status;

    /* Delete entire memory block pool. Assume that the pool
      has already been created with a call to
      tx_block_pool_create. */
    status =  tx_block_pool_delete(&my_pool);

    /* If status equals TX_SUCCESS, the memory block pool is
       deleted. */
```
### <a name="see-also"></a><span data-ttu-id="38207-292">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-292">See Also</span></span>

- <span data-ttu-id="38207-293">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-293">tx_block_allocate</span></span>
- <span data-ttu-id="38207-294">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-294">tx_block_pool_create</span></span>
- <span data-ttu-id="38207-295">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-295">tx_block_pool_info_get</span></span>
- <span data-ttu-id="38207-296">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-296">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-297">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-297">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-298">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-298">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="38207-299">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="38207-299">tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="38207-300">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-300">tx_block_pool_info_get</span></span>

<span data-ttu-id="38207-301">블록 풀에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-301">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-302">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-302">Prototype</span></span>

```C
UINT tx_block_pool_info_get(TX_BLOCK_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *total_blocks,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BLOCK_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="38207-303">Description</span><span class="sxs-lookup"><span data-stu-id="38207-303">Description</span></span>

<span data-ttu-id="38207-304">이 서비스는 지정된 블록 메모리 풀에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-304">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-305">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-305">Parameters</span></span>

- <span data-ttu-id="38207-306">**pool_ptr**: 이전에 만든 메모리 블록 풀을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-306">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="38207-307">**name**: 블록 풀 이름 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-307">**name**: Pointer to destination for the pointer to the block pool’s name.</span></span>
- <span data-ttu-id="38207-308">**available**: 블록 풀의 사용 가능한 블록 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-308">**available**: Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="38207-309">**total_blocks**: 블록 풀의 총 블록 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-309">**total_blocks**: Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="38207-310">**first_suspended**: 이 블록 풀의 일시 중단 목록에 있는 첫 번째 스레드 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-310">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="38207-311">**suspended_count**: 이 블록 풀의 현재 일시 중단된 스레드 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-311">**suspended_count**: Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="38207-312">**next_pool**: 다음에 만든 블록 풀 포인터의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-312">**next_pool**: Pointer to destination for the pointer of the next created block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-313">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-313">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-314">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-314">Return Values</span></span>

- <span data-ttu-id="38207-315">**TX_SUCCESS**:(0x00) 블록 풀 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-315">**TX_SUCCESS**: (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="38207-316">TX_POOL_ERROR:(0x02) 잘못된 메모리 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-316">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-317">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-317">Allowed From</span></span>

<span data-ttu-id="38207-318">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-318">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-319">예제</span><span class="sxs-lookup"><span data-stu-id="38207-319">Example</span></span>

```C
TX_BLOCK_POOL    my_pool;
CHAR             *name;
ULONG            available;
ULONG            total_blocks;
TX_THREAD        *first_suspended;
ULONG            suspended_count;
TX_BLOCK_POOL    *next_pool;
UINT             status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
                &available,&total_blocks,
                &first_suspended, &suspended_count,
                &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="38207-320">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-320">See Also</span></span>

- <span data-ttu-id="38207-321">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-321">tx_block_allocate</span></span>
- <span data-ttu-id="38207-322">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-322">tx_block_pool_create</span></span>
- <span data-ttu-id="38207-323">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-323">tx_block_pool_delete</span></span>
- <span data-ttu-id="38207-324">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-324">tx_block_pool_info_get</span></span>
- <span data-ttu-id="38207-325">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-325">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-326">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-326">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-327">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-327">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="38207-328">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="38207-328">tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="38207-329">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-329">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="38207-330">블록 풀 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-330">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-331">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-331">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(TX_BLOCK_POOL *pool_ptr,
       ULONG *allocates, ULONG *releases,
       ULONG *suspensions, ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="38207-332">Description</span><span class="sxs-lookup"><span data-stu-id="38207-332">Description</span></span>

<span data-ttu-id="38207-333">이 서비스는 지정된 메모리 블록 풀에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-333">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-334">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-334">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-335">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-335">Parameters</span></span>

- <span data-ttu-id="38207-336">**pool_ptr**: 이전에 만든 메모리 블록 풀을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-336">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="38207-337">**allocates**: 이 풀에서 수행된 할당 요청 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-337">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="38207-338">**releases**: 이 풀에서 수행된 해제 요청 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-338">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="38207-339">**suspensions**: 이 풀의 스레드 할당 일시 중단 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-339">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="38207-340">**timeouts**: 이 풀의 할당 일시 중단 시간 제한 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-340">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-341">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-341">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-342">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-342">Return Values</span></span>

- <span data-ttu-id="38207-343">**TX_SUCCESS**:(0x00) 블록 풀 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-343">**TX_SUCCESS**: (0x00) Successful block pool performance get.</span></span>
- <span data-ttu-id="38207-344">**TX_PTR_ERROR**:(0x03) 잘못된 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-344">**TX_PTR_ERROR**: (0x03) Invalid block pool pointer.</span></span>
- <span data-ttu-id="38207-345">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-345">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-346">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-346">Allowed From</span></span>

<span data-ttu-id="38207-347">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-347">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-348">예제</span><span class="sxs-lookup"><span data-stu-id="38207-348">Example</span></span>

```C
TX_BLOCK_POOL     my_pool;
ULONG             allocates;
ULONG             releases;
ULONG             suspensions;
ULONG             timeouts;

/* Retrieve performance information on the previously created block
   pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
                                            &releases,
                &suspensions,
                &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-349">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-349">See Also</span></span>

- <span data-ttu-id="38207-350">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-350">tx_block_allocate</span></span>
- <span data-ttu-id="38207-351">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-351">tx_block_pool_create</span></span>
- <span data-ttu-id="38207-352">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-352">tx_block_pool_delete</span></span>
- <span data-ttu-id="38207-353">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-353">tx_block_pool_info_get</span></span>
- <span data-ttu-id="38207-354">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-354">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-355">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-355">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-356">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="38207-356">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="38207-357">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-357">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="38207-358">블록 풀 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-358">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-359">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-359">Prototype</span></span>

```C
UINT tx_block_pool_performance_system_info_get(ULONG *allocates,
       ULONG *releases, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="38207-360">Description</span><span class="sxs-lookup"><span data-stu-id="38207-360">Description</span></span>

<span data-ttu-id="38207-361">이 서비스는 애플리케이션의 모든 메모리 블록 풀에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-361">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-362">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-362">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-363">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-363">Parameters</span></span>

- <span data-ttu-id="38207-364">**allocates**: 모든 블록 풀에서 수행된 총 할당 요청 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-364">**allocates**: Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="38207-365">**releases**: 모든 블록 풀에서 수행된 총 해제 요청 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-365">**releases**: Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="38207-366">**suspensions**: 모든 블록 풀의 총 스레드 할당 일시 중단 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-366">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="38207-367">**timeouts**: 모든 블록 풀의 총 할당 일시 중단 시간 제한 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-367">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-368">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-368">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-369">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-369">Return Values</span></span>

- <span data-ttu-id="38207-370">**TX_SUCCESS**:(0x00) 블록 풀 시스템 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-370">**TX_SUCCESS**: (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="38207-371">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-371">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-372">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-372">Allowed From</span></span>

<span data-ttu-id="38207-373">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-373">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-374">예제</span><span class="sxs-lookup"><span data-stu-id="38207-374">Example</span></span>

```C
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all the block pools in
   the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
                     &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-375">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-375">See Also</span></span>

- <span data-ttu-id="38207-376">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-376">tx_block_allocate</span></span>
- <span data-ttu-id="38207-377">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-377">tx_block_pool_create</span></span>
- <span data-ttu-id="38207-378">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-378">tx_block_pool_delete</span></span>
- <span data-ttu-id="38207-379">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-379">tx_block_pool_info_get</span></span>
- <span data-ttu-id="38207-380">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-380">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-381">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-381">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="38207-382">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="38207-382">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="38207-383">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-383">tx_block_pool_prioritize</span></span>

<span data-ttu-id="38207-384">블록 풀 일시 중단 목록 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="38207-384">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-385">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-385">Prototype</span></span>

```C
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-386">Description</span><span class="sxs-lookup"><span data-stu-id="38207-386">Description</span></span>

<span data-ttu-id="38207-387">이 서비스는 일시 중단 목록 맨 앞에 있는, 이 풀의 메모리 블록에 대해 일시 중단된 스레드를 가장 높은 우선 순위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-387">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="38207-388">다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-388">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-389">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-389">Parameters</span></span> 

- <span data-ttu-id="38207-390">**pool_ptr**: 메모리 블록 풀 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-390">**pool_ptr**: Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-391">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-391">Return Values</span></span>

- <span data-ttu-id="38207-392">**TX_SUCCESS**:(0x00) 블록 풀 우선 순위 지정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-392">**TX_SUCCESS**: (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="38207-393">TX_POOL_ERROR:(0x02) 잘못된 메모리 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-393">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-394">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-394">Allowed From</span></span>

<span data-ttu-id="38207-395">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-395">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-396">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-396">Preemption Possible</span></span>

<span data-ttu-id="38207-397">예</span><span class="sxs-lookup"><span data-stu-id="38207-397">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-398">예제</span><span class="sxs-lookup"><span data-stu-id="38207-398">Example</span></span>

```C
TX_BLOCK_POOL my_pool;
UINT          status;

/* Ensure that the highest priority thread will receive
   the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_block_release call will wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="38207-399">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-399">See Also</span></span>

- <span data-ttu-id="38207-400">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-400">tx_block_allocate</span></span>
- <span data-ttu-id="38207-401">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-401">tx_block_pool_create</span></span>
- <span data-ttu-id="38207-402">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-402">tx_block_pool_delete</span></span>
- <span data-ttu-id="38207-403">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-403">tx_block_pool_info_get</span></span>
- <span data-ttu-id="38207-404">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-404">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-405">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-405">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-406">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="38207-406">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="38207-407">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="38207-407">tx_block_release</span></span>

<span data-ttu-id="38207-408">고정된 크기의 메모리 블록 해제</span><span class="sxs-lookup"><span data-stu-id="38207-408">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-409">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-409">Prototype</span></span>

```C
UINT tx_block_release(VOID *block_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-410">Description</span><span class="sxs-lookup"><span data-stu-id="38207-410">Description</span></span>

<span data-ttu-id="38207-411">이 서비스는 이전에 할당된 블록을 연결된 메모리 풀로 다시 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-411">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="38207-412">이 풀의 메모리 블록을 기다리는 일시 중단된 스레드가 하나 이상인 경우 일시 중단된 첫 번째 스레드에 이 메모리 블록이 지정되고 해당 스레드는 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-412">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-413">애플리케이션은 메모리 블록 영역이 풀로 다시 해제된 후에는 이 메모리 블록 영역을 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-413">The application must prevent using a memory block area after it has been released back to the pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-414">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-414">Parameters</span></span>

- <span data-ttu-id="38207-415">**block_ptr**: 이전에 할당된 메모리 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-415">**block_ptr**: Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-416">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-416">Return Values</span></span>

- <span data-ttu-id="38207-417">**TX_SUCCESS**:(0x00) 메모리 블록 해제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-417">**TX_SUCCESS**: (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="38207-418">TX_PTR_ERROR:(0x03) 메모리 블록을 가리키는 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-418">TX_PTR_ERROR: (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-419">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-419">Allowed From</span></span>

<span data-ttu-id="38207-420">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-420">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-421">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-421">Preemption Possible</span></span>

<span data-ttu-id="38207-422">예</span><span class="sxs-lookup"><span data-stu-id="38207-422">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-423">예제</span><span class="sxs-lookup"><span data-stu-id="38207-423">Example</span></span>

```C
TX_BLOCK_POOLmy_pool;
unsigned char*memory_ptr;
UINT         status;

/* Release a memory block back to my_pool. Assume that the
   pool has been created and the memory block has been
   allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
   to by memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="38207-424">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-424">See Also</span></span>

- <span data-ttu-id="38207-425">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-425">tx_block_allocate</span></span>
- <span data-ttu-id="38207-426">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-426">tx_block_pool_create</span></span>
- <span data-ttu-id="38207-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-427">tx_block_pool_delete</span></span>
- <span data-ttu-id="38207-428">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-428">tx_block_pool_info_get</span></span>
- <span data-ttu-id="38207-429">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-429">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-430">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-430">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-431">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-431">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="38207-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-432">tx_byte_allocate</span></span>

<span data-ttu-id="38207-433">메모리 바이트 할당</span><span class="sxs-lookup"><span data-stu-id="38207-433">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-434">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-434">Prototype</span></span>

```C
UINT tx_byte_allocate(TX_BYTE_POOL *pool_ptr,
                          VOID **memory_ptr, ULONG memory_size,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="38207-435">Description</span><span class="sxs-lookup"><span data-stu-id="38207-435">Description</span></span>

<span data-ttu-id="38207-436">이 서비스는 지정된 메모리 바이트 풀에서 지정된 바이트 수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-436">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!WARNING]
> <span data-ttu-id="38207-437">애플리케이션 코드는 할당 된 메모리 블록 외부에 쓰지 않도록 하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-437">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="38207-438">만약 그렇게 되면 인접한(일반적으로 후속) 메모리 블록에서 손상이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-438">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="38207-439">결과는 예측할 수 없으며 치명적인 경우도 많습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-439">The results are unpredictable and are often fatal!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-440">이 서비스의 성능은 블록 크기와 풀의 조각화 양에 대한 함수로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-440">The performance of this service is a function of the block size and the amount of fragmentation in the pool.</span></span> <span data-ttu-id="38207-441">따라서 이 서비스는 시간이 중요한 실행 스레드 중에는 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-441">Hence, this service should not be used during time-critical threads of execution.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-442">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-442">Parameters</span></span>

- <span data-ttu-id="38207-443">**pool_ptr**: 이전에 만든 메모리 풀을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-443">**pool_ptr**: Pointer to a previously created memory pool.</span></span>
- <span data-ttu-id="38207-444">**memory_ptr**: 대상 메모리 포인터를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-444">**memory_ptr**: Pointer to a destination memory pointer.</span></span> <span data-ttu-id="38207-445">할당에 성공하면 할당된 메모리 영역 주소가 이 매개 변수에서 가리키는 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-445">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="38207-446">**memory_size**: 요청된 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-446">**memory_size**: Number of bytes requested.</span></span>
- <span data-ttu-id="38207-447">**wait_option**: 사용할 수 있는 메모리가 충분하지 않은 경우의 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-447">**wait_option**: Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="38207-448">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-448">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38207-449">**TX_NO_WAIT**:(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="38207-449">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="38207-450">**TX_WAIT_FOREVER**:(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38207-450">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="38207-451">시간 제한 값:(0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38207-451">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="38207-452">TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-452">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="38207-453">초기화에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-453">*This is the only valid option if the service is called from initialization.*</span></span>

    <span data-ttu-id="38207-454">TX_WAIT_FOREVER를 선택하면 충분한 메모리를 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-454">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until enough memory is available.</span></span>

    <span data-ttu-id="38207-455">숫자 값(1-0xFFFFFFFE)을 선택하면 메모리를 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-455">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-456">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-456">Return Values</span></span>

- <span data-ttu-id="38207-457">**TX_SUCCESS**:(0x00) 메모리 할당에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-457">**TX_SUCCESS**: (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="38207-458">**TX_DELETED**:(0x01) 스레드가 일시 중단된 동안 메모리 풀이 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-458">**TX_DELETED**: (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="38207-459">**TX_NO_MEMORY**:(0x10) 서비스가 지정된 대기 시간 내에 메모리를 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-459">**TX_NO_MEMORY**: (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="38207-460">**TX_WAIT_ABORTED**:(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-460">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="38207-461">TX_POOL_ERROR:(0x02) 잘못된 메모리 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-461">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="38207-462">TX_PTR_ERROR:(0x03) 대상 포인터를 가리키는 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-462">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="38207-463">TX_SIZE_ERROR:(0X05) 요청된 크기가 0이거나 풀보다 큽니다.</span><span class="sxs-lookup"><span data-stu-id="38207-463">TX_SIZE_ERROR: (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="38207-464">TX_WAIT_ERROR:(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-464">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="38207-465">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-465">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-466">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-466">Allowed From</span></span>

<span data-ttu-id="38207-467">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="38207-467">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-468">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-468">Preemption Possible</span></span>

<span data-ttu-id="38207-469">예</span><span class="sxs-lookup"><span data-stu-id="38207-469">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-470">예제</span><span class="sxs-lookup"><span data-stu-id="38207-470">Example</span></span>

```C
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a 112 byte memory area from my_pool. Assume
   that the pool has already been created with a call to
   tx_byte_pool_create. */
status =  tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
                       112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated memory area. */
```
### <a name="see-also"></a><span data-ttu-id="38207-471">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-471">See Also</span></span>

- <span data-ttu-id="38207-472">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-472">tx_byte_pool_create</span></span>
- <span data-ttu-id="38207-473">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-473">tx_byte_pool_delete</span></span>
- <span data-ttu-id="38207-474">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-474">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="38207-475">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-475">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-476">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-476">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-477">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-477">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="38207-478">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="38207-478">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="38207-479">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-479">tx_byte_pool_create</span></span>

<span data-ttu-id="38207-480">메모리 바이트 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-480">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-481">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-481">Prototype</span></span>

```C
UINT tx_byte_pool_create(TX_BYTE_POOL *pool_ptr,
                          CHAR *name_ptr, VOID *pool_start,
                          ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="38207-482">Description</span><span class="sxs-lookup"><span data-stu-id="38207-482">Description</span></span>

<span data-ttu-id="38207-483">이 서비스는 지정된 영역에 메모리 바이트 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38207-483">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="38207-484">처음에는 풀이 기본적으로 하나의 매우 큰 빈 블록으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-484">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="38207-485">하지만 할당이 진행되면 이 풀이 더 작은 블록으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-485">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-486">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-486">Parameters</span></span>

- <span data-ttu-id="38207-487">**pool_ptr**: 메모리 풀 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-487">**pool_ptr**: Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="38207-488">**name_ptr**: 메모리 풀 이름을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-488">**name_ptr**: Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="38207-489">**pool_start**: 메모리 풀의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-489">**pool_start**: Starting address of the memory pool.</span></span> <span data-ttu-id="38207-490">시작 주소는 ULONG 데이터 형식의 크기에 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-490">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="38207-491">**pool_size**: 메모리 풀에 사용할 수 있는 총 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-491">**pool_size**: Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-492">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-492">Return Values</span></span>

- <span data-ttu-id="38207-493">**TX_SUCCESS**:(0x00) 메모리 풀 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-493">**TX_SUCCESS**: (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="38207-494">TX_POOL_ERROR:(0x02) 잘못된 메모리 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-494">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="38207-495">포인터가 NULL이거나 풀이 이미 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-495">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="38207-496">TX_PTR_ERROR:(0x03) 풀의 시작 주소가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-496">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="38207-497">TX_SIZE_ERROR:(0x05) 풀 크기가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-497">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="38207-498">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-498">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-499">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-499">Allowed From</span></span>

<span data-ttu-id="38207-500">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="38207-500">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-501">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-501">Preemption Possible</span></span>

<span data-ttu-id="38207-502">예</span><span class="sxs-lookup"><span data-stu-id="38207-502">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-503">예제</span><span class="sxs-lookup"><span data-stu-id="38207-503">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Create a memory pool whose total size is 2000 bytes
   starting at address 0x500000. */
status =  tx_byte_pool_create(&my_pool, "my_pool_name",
             (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
   allocating memory. */
```
### <a name="see-also"></a><span data-ttu-id="38207-504">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-504">See Also</span></span>

- <span data-ttu-id="38207-505">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-505">tx_byte_allocate</span></span>
- <span data-ttu-id="38207-506">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-506">tx_byte_pool_delete</span></span>
- <span data-ttu-id="38207-507">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-507">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="38207-508">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-508">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-509">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-509">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-510">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-510">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="38207-511">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="38207-511">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="38207-512">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-512">tx_byte_pool_delete</span></span>

<span data-ttu-id="38207-513">메모리 바이트 풀 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-513">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-514">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-514">Prototype</span></span>

```C
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-515">Description</span><span class="sxs-lookup"><span data-stu-id="38207-515">Description</span></span>

<span data-ttu-id="38207-516">이 서비스는 지정된 메모리 바이트 풀을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-516">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="38207-517">이 풀에서 메모리를 기다리는 동안 일시 중단된 모든 스레드가 다시 시작되며 TX_DELETED 반환 상태가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-517">All threads suspended waiting for memory from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-518">이 서비스가 완료된 후에 사용할 수 있는 풀과 연결된 메모리 영역을 관리하는 것은 애플리케이션의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-518">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="38207-519">또한 애플리케이션은 삭제된 풀이나 이전에 할당된 메모리를 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-519">In addition, the application must prevent use of a deleted pool or memory previously allocated from it.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-520">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-520">Parameters</span></span> 

- <span data-ttu-id="38207-521">**pool_ptr**: 이전에 만든 메모리 풀을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-521">**pool_ptr**: Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-522">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-522">Return Values</span></span>

- <span data-ttu-id="38207-523">**TX_SUCCESS**:(0x00) 메모리 풀 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-523">**TX_SUCCESS**: (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="38207-524">TX_POOL_ERROR:(0x02) 잘못된 메모리 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-524">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="38207-525">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-525">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-526">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-526">Allowed From</span></span>

<span data-ttu-id="38207-527">스레드</span><span class="sxs-lookup"><span data-stu-id="38207-527">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-528">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-528">Preemption Possible</span></span>

<span data-ttu-id="38207-529">예</span><span class="sxs-lookup"><span data-stu-id="38207-529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-530">예제</span><span class="sxs-lookup"><span data-stu-id="38207-530">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Delete entire memory pool. Assume that the pool has already
   been created with a call to tx_byte_pool_create. */
status =   tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```
### <a name="see-also"></a><span data-ttu-id="38207-531">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-531">See Also</span></span>

- <span data-ttu-id="38207-532">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-532">tx_byte_allocate</span></span>
- <span data-ttu-id="38207-533">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-533">tx_byte_pool_create</span></span>
- <span data-ttu-id="38207-534">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-534">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="38207-535">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-535">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-536">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-536">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-537">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-537">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="38207-538">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="38207-538">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="38207-539">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-539">tx_byte_pool_info_get</span></span>

<span data-ttu-id="38207-540">바이트 풀에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-540">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-541">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-541">Prototype</span></span>

```C
UINT tx_byte_pool_info_get(TX_BYTE_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *fragments,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BYTE_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="38207-542">Description</span><span class="sxs-lookup"><span data-stu-id="38207-542">Description</span></span>

<span data-ttu-id="38207-543">이 서비스는 지정된 메모리 바이트 풀에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-543">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-544">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-544">Parameters</span></span>

- <span data-ttu-id="38207-545">**pool_ptr**: 이전에 만든 메모리 풀을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-545">**pool_ptr**: Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="38207-546">**name**: 바이트 풀 이름에 대한 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-546">**name**: Pointer to destination for the pointer to the byte pool’s name.</span></span>
- <span data-ttu-id="38207-547">**available**: 풀에서 사용 가능한 바이트 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-547">**available**: Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="38207-548">**fragments**: 바이트 풀에 있는 총 메모리 조각 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-548">**fragments**: Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="38207-549">**first_suspended**: 이 바이트 풀의 일시 중단 목록에 있는 첫 번째 스레드 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-549">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="38207-550">**suspended_count**: 이 바이트 풀의 현재 일시 중단된 스레드 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-550">**suspended_count**: Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="38207-551">**next_pool**: 다음에 만든 바이트 풀 포인터의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-551">**next_pool**: Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-552">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-552">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-553">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-553">Return Values</span></span>

- <span data-ttu-id="38207-554">**TX_SUCCESS**:(0x00) 풀 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-554">**TX_SUCCESS**: (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="38207-555">TX_POOL_ERROR:(0x02) 잘못된 메모리 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-555">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-556">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-556">Allowed From</span></span>

<span data-ttu-id="38207-557">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-557">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-558">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-558">Preemption Possible</span></span>

<span data-ttu-id="38207-559">예</span><span class="sxs-lookup"><span data-stu-id="38207-559">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-560">예제</span><span class="sxs-lookup"><span data-stu-id="38207-560">Example</span></span>

```C
TX_BYTE_POOL my_pool;
CHAR         *name;
ULONG        available;
ULONG        fragments;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_BYTE_POOL *next_pool;
UINT         status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status =  tx_byte_pool_info_get(&my_pool, &name,
             &available, &fragments,
             &first_suspended, &suspended_count,
             &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="38207-561">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-561">See Also</span></span>

- <span data-ttu-id="38207-562">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-562">tx_byte_allocate</span></span>
- <span data-ttu-id="38207-563">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-563">tx_byte_pool_create</span></span>
- <span data-ttu-id="38207-564">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-564">tx_byte_pool_delete</span></span>
- <span data-ttu-id="38207-565">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-565">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-566">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-566">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-567">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-567">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="38207-568">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="38207-568">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="38207-569">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-569">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="38207-570">바이트 풀 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-570">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-571">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-571">Prototype</span></span>

```C
UINT tx_byte_pool_performance_info_get(TX_BYTE_POOL *pool_ptr,
        ULONG *allocates, ULONG *releases,
        ULONG *fragments_searched, ULONG *merges, ULONG *splits,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="38207-572">Description</span><span class="sxs-lookup"><span data-stu-id="38207-572">Description</span></span>

<span data-ttu-id="38207-573">이 서비스는 지정된 메모리 바이트 풀에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-573">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-574">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-574">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-575">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-575">Parameters</span></span>

- <span data-ttu-id="38207-576">**pool_ptr**: 이전에 만든 메모리 바이트 풀을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-576">**pool_ptr**: Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="38207-577">**allocates**: 이 풀에서 수행된 할당 요청 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-577">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="38207-578">**releases**: 이 풀에서 수행된 해제 요청 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-578">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="38207-579">**fragments_searched**: 이 풀에서 할당 요청 중 검색된 내부 메모리 조각 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-579">**fragments_searched**: Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="38207-580">**merges**: 이 풀에서 할당 요청 중 병합된 내부 메모리 블록 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-580">**merges**: Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="38207-581">**splits**: 이 풀에서 할당 요청 중 만들어진 내부 메모리 블록 분할(조각) 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-581">**splits**: Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="38207-582">**suspensions**: 이 풀의 스레드 할당 일시 중단 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-582">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="38207-583">**timeouts**: 이 풀의 할당 일시 중단 시간 제한 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-583">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-584">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-584">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-585">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-585">Return Values</span></span>

- <span data-ttu-id="38207-586">TX_SUCCESS:(0x00) 바이트 풀 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-586">TX_SUCCESS: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="38207-587">**TX_PTR_ERROR**:(0x03) 잘못된 바이트 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-587">**TX_PTR_ERROR**: (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="38207-588">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-588">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-589">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-589">Allowed From</span></span>

<span data-ttu-id="38207-590">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-590">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-591">예제</span><span class="sxs-lookup"><span data-stu-id="38207-591">Example</span></span>

```C
TX_BYTE_POOL     my_pool;
ULONG            fragments_searched;
ULONG            merges;
ULONG            splits;
ULONG            allocates;
ULONG            releases;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created byte
   pool.  */
status =  tx_byte_pool_performance_info_get(&my_pool,
                &fragments_searched,
                &merges, &splits,
                &allocates, &releases,
                      &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-592">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-592">See Also</span></span>

- <span data-ttu-id="38207-593">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-593">tx_byte_allocate</span></span>
- <span data-ttu-id="38207-594">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-594">tx_byte_pool_create</span></span>
- <span data-ttu-id="38207-595">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-595">tx_byte_pool_delete</span></span>
- <span data-ttu-id="38207-596">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-596">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="38207-597">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-597">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-598">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-598">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="38207-599">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="38207-599">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="38207-600">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-600">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="38207-601">바이트 풀 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-601">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-602">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-602">Prototype</span></span>

```C
UINT  tx_byte_pool_performance_system_info_get(ULONG *allocates,
        ULONG *releases, ULONG *fragments_searched, ULONG *merges,
        ULONG *splits, ULONG *suspensions, ULONG *timeouts);;
```
### <a name="description"></a><span data-ttu-id="38207-603">Description</span><span class="sxs-lookup"><span data-stu-id="38207-603">Description</span></span>

<span data-ttu-id="38207-604">이 서비스는 시스템의 모든 메모리 바이트 풀에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-604">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-605">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-605">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-606">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-606">Parameters</span></span>

- <span data-ttu-id="38207-607">**allocates**: 이 풀에서 수행된 할당 요청 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-607">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="38207-608">**releases**: 이 풀에서 수행된 해제 요청 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-608">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="38207-609">**fragments_searched**: 모든 바이트 풀에서 할당 요청 중 검색된 총 내부 메모리 조각 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-609">**fragments_searched**: Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="38207-610">**merges**: 모든 바이트 풀에서 할당 요청 중 병합된 총 내부 메모리 블록 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-610">**merges**: Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="38207-611">**splits**: 모든 바이트 풀에서 할당 요청 중 만들어진 총 내부 메모리 블록 분할(조각) 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-611">**splits**: Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="38207-612">**suspensions**: 모든 바이트 풀의 총 스레드 할당 일시 중단 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-612">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="38207-613">**timeouts**: 모든 바이트 풀의 총 할당 일시 중단 시간 제한 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-613">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-614">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-614">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-615">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-615">Return Values</span></span>

- <span data-ttu-id="38207-616">**TX_SUCCESS**:(0x00) 바이트 풀 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-616">**TX_SUCCESS**: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="38207-617">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-617">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-618">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-618">Allowed From</span></span>

<span data-ttu-id="38207-619">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-619">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-620">예제</span><span class="sxs-lookup"><span data-stu-id="38207-620">Example</span></span>

```C
ULONG         fragments_searched;
ULONG         merges;
ULONG         splits;
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all byte pools in the
   system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
                &merges, &splits, &allocates, &releases,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-621">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-621">See Also</span></span>

- <span data-ttu-id="38207-622">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-622">tx_byte_allocate</span></span>
- <span data-ttu-id="38207-623">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-623">tx_byte_pool_create</span></span>
- <span data-ttu-id="38207-624">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-624">tx_byte_pool_delete</span></span>
- <span data-ttu-id="38207-625">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-625">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="38207-626">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-626">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-627">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-627">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="38207-628">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="38207-628">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="38207-629">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-629">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="38207-630">바이트 풀 일시 중단 목록 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="38207-630">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-631">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-631">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-632">Description</span><span class="sxs-lookup"><span data-stu-id="38207-632">Description</span></span>

<span data-ttu-id="38207-633">이 서비스는 일시 중단 목록 맨 앞에 있는, 이 풀의 메모리에 대해 일시 중단된 스레드를 가장 높은 우선 순위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-633">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="38207-634">다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-634">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-635">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-635">Parameters</span></span> 

- <span data-ttu-id="38207-636">**pool_ptr**: 메모리 풀 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-636">**pool_ptr**: Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-637">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-637">Return Values</span></span>

- <span data-ttu-id="38207-638">**TX_SUCCESS**:(0x00) 메모리 풀 우선 순위를 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-638">**TX_SUCCESS**: (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="38207-639">TX_POOL_ERROR:(0x02) 잘못된 메모리 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-639">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-640">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-640">Allowed From</span></span>

<span data-ttu-id="38207-641">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-641">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-642">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-642">Preemption Possible</span></span>

<span data-ttu-id="38207-643">예</span><span class="sxs-lookup"><span data-stu-id="38207-643">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-644">예제</span><span class="sxs-lookup"><span data-stu-id="38207-644">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_byte_release call will wake up this thread,
   if there is enough memory to satisfy its request. */
```
### <a name="see-also"></a><span data-ttu-id="38207-645">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-645">See Also</span></span>

- <span data-ttu-id="38207-646">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-646">tx_byte_allocate</span></span>
- <span data-ttu-id="38207-647">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-647">tx_byte_pool_create</span></span>
- <span data-ttu-id="38207-648">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-648">tx_byte_pool_delete</span></span>
- <span data-ttu-id="38207-649">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-649">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="38207-650">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-650">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-651">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-651">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-652">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="38207-652">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="38207-653">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="38207-653">tx_byte_release</span></span>

<span data-ttu-id="38207-654">바이트를 메모리 풀로 다시 해제</span><span class="sxs-lookup"><span data-stu-id="38207-654">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-655">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-655">Prototype</span></span>

```C
UINT tx_byte_release(VOID *memory_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-656">Description</span><span class="sxs-lookup"><span data-stu-id="38207-656">Description</span></span>

<span data-ttu-id="38207-657">이 서비스는 이전에 할당된 메모리 영역을 연결된 풀로 다시 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-657">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="38207-658">이 풀에서 메모리를 대기하는 일시 중단된 스레드가 하나 이상 있는 경우 일시 중단된 각 스레드에는 메모리를 제공되고 해당 메모리가 고갈되거나 일시 중단된 스레드가 더 이상 없게 될 때까지 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-658">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="38207-659">일시 중단된 스레드에 메모리를 할당하는 이 프로세스는 항상 일시 중단된 첫 번째 스레드로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-659">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-660">애플리케이션은 메모리 영역이 해제된 후 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-660">The application must prevent using the memory area after it is released.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-661">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-661">Parameters</span></span>

- <span data-ttu-id="38207-662">**memory_ptr**: 이전에 할당된 메모리 영역을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-662">**memory_ptr**: Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-663">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-663">Return Values</span></span>

- <span data-ttu-id="38207-664">**TX_SUCCESS**:(0x00) 메모리 해제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-664">**TX_SUCCESS**: (0x00) Successful memory release.</span></span>
- <span data-ttu-id="38207-665">TX_PTR_ERROR:(0x03) 잘못된 메모리 영역 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-665">TX_PTR_ERROR: (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="38207-666">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-666">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-667">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-667">Allowed From</span></span>

<span data-ttu-id="38207-668">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="38207-668">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-669">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-669">Preemption Possible</span></span>

<span data-ttu-id="38207-670">예</span><span class="sxs-lookup"><span data-stu-id="38207-670">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-671">예제</span><span class="sxs-lookup"><span data-stu-id="38207-671">Example</span></span>

```C
unsigned char    *memory_ptr;
UINT             status;

/* Release a memory back to my_pool. Assume that the memory
   area was previously allocated from my_pool. */
status =  tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
   memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="38207-672">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-672">See Also</span></span>

- <span data-ttu-id="38207-673">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="38207-673">tx_byte_allocate</span></span>
- <span data-ttu-id="38207-674">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="38207-674">tx_byte_pool_create</span></span>
- <span data-ttu-id="38207-675">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="38207-675">tx_byte_pool_delete</span></span>
- <span data-ttu-id="38207-676">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-676">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="38207-677">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-677">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="38207-678">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-678">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="38207-679">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-679">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="38207-680">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="38207-680">tx_event_flags_create</span></span>

<span data-ttu-id="38207-681">이벤트 플래그 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-681">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-682">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-682">Prototype</span></span>

```c
UINT tx_event_flags_create(TX_EVENT_FLAGS_GROUP *group_ptr,
                          CHAR *name_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-683">Description</span><span class="sxs-lookup"><span data-stu-id="38207-683">Description</span></span>

<span data-ttu-id="38207-684">이 서비스는 32개의 이벤트 플래그 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38207-684">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="38207-685">그룹의 모든 32개 이벤트 플래그는 0으로 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-685">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="38207-686">각 이벤트 플래그는 단일 비트로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-686">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-687">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-687">Parameters</span></span>

- <span data-ttu-id="38207-688">**group_ptr**: 이벤트 플래그 그룹 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-688">**group_ptr**: Pointer to an event flags group control block.</span></span> 
- <span data-ttu-id="38207-689">**name_ptr**: 이벤트 플래그 그룹 이름을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-689">**name_ptr**: Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-690">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-690">Return Values</span></span>

- <span data-ttu-id="38207-691">**TX_SUCCESS**:(0x00) 이벤트 그룹을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-691">**TX_SUCCESS**: (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="38207-692">TX_GROUP_ERROR:(0x06) 잘못된 이벤트 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-692">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="38207-693">포인터가 NULL이거나 이벤트 그룹을 이미 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-693">Either the pointer is NULL or the event group is already created.</span></span>
- <span data-ttu-id="38207-694">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-694">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-695">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-695">Allowed From</span></span>

<span data-ttu-id="38207-696">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="38207-696">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-697">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-697">Preemption Possible</span></span>

<span data-ttu-id="38207-698">예</span><span class="sxs-lookup"><span data-stu-id="38207-698">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-699">예제</span><span class="sxs-lookup"><span data-stu-id="38207-699">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_group;
UINT         status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
            "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
   for get and set services. */
```
### <a name="see-also"></a><span data-ttu-id="38207-700">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-700">See Also</span></span>

- <span data-ttu-id="38207-701">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="38207-701">tx_event_flags_delete</span></span>
- <span data-ttu-id="38207-702">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="38207-702">tx_event_flags_get</span></span>
- <span data-ttu-id="38207-703">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-703">tx_event_flags_info_get</span></span>
- <span data-ttu-id="38207-704">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-704">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="38207-705">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-705">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="38207-706">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="38207-706">tx_event_flags_set</span></span>
- <span data-ttu-id="38207-707">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="38207-707">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="38207-708">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="38207-708">tx_event_flags_delete</span></span>

<span data-ttu-id="38207-709">이벤트 플래그 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-709">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-710">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-710">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-711">Description</span><span class="sxs-lookup"><span data-stu-id="38207-711">Description</span></span>

<span data-ttu-id="38207-712">이 서비스는 지정된 이벤트 플래그 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-712">This service deletes the specified event flags group.</span></span> <span data-ttu-id="38207-713">이 그룹에서 이벤트를 기다리는 동안 일시 중단된 모든 스레드가 다시 시작되며 TX_DELETED 반환 상태가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-713">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-714">애플리케이션은 이벤트 플래그 그룹을 삭제 하기 전에 이 이벤트 플래그 그룹에 대한 알림 설정 콜백이 완료(또는 사용하지 않도록 설정)되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-714">The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group.</span></span> <span data-ttu-id="38207-715">또한 애플리케이션은 나중에 삭제된 이벤트 플래그 그룹을 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-715">In addition, the application must prevent all future use of a deleted event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-716">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-716">Parameters</span></span> 

- <span data-ttu-id="38207-717">**group_ptr**: 이전에 만든 이벤트 플래그 그룹을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-717">**group_ptr**: Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-718">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-718">Return Values</span></span>

- <span data-ttu-id="38207-719">**TX_SUCCESS**:(0x00) 이벤트 플래그 그룹을 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-719">**TX_SUCCESS**: (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="38207-720">TX_GROUP_ERROR:(0x06) 잘못된 이벤트 플래그 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-720">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="38207-721">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-721">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-722">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-722">Allowed From</span></span>

<span data-ttu-id="38207-723">스레드</span><span class="sxs-lookup"><span data-stu-id="38207-723">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-724">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-724">Preemption Possible</span></span>

<span data-ttu-id="38207-725">예</span><span class="sxs-lookup"><span data-stu-id="38207-725">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-726">예제</span><span class="sxs-lookup"><span data-stu-id="38207-726">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT                 status;

/* Delete event flags group. Assume that the group has
   already been created with a call to
   tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="38207-727">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-727">See Also</span></span>

- <span data-ttu-id="38207-728">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="38207-728">tx_event_flags_create</span></span>
- <span data-ttu-id="38207-729">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="38207-729">tx_event_flags_get</span></span>
- <span data-ttu-id="38207-730">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-730">tx_event_flags_info_get</span></span>
- <span data-ttu-id="38207-731">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-731">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="38207-732">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-732">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="38207-733">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="38207-733">tx_event_flags_set</span></span>
- <span data-ttu-id="38207-734">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="38207-734">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="38207-735">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="38207-735">tx_event_flags_get</span></span>

<span data-ttu-id="38207-736">이벤트 플래그 그룹에서 이벤트 플래그 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-736">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-737">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-737">Prototype</span></span>

```C
UINT tx_event_flags_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG requested_flags, UINT get_option,
                          ULONG *actual_flags_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="38207-738">Description</span><span class="sxs-lookup"><span data-stu-id="38207-738">Description</span></span>

<span data-ttu-id="38207-739">이 서비스는 지정된 이벤트 플래그 그룹에서 이벤트 플래그를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-739">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="38207-740">각 이벤트 플래그 그룹에는 32개의 이벤트 플래그가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-740">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="38207-741">각 이벤트 플래그는 단일 비트로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-741">Each flag is represented by a single bit.</span></span> <span data-ttu-id="38207-742">이 서비스는 입력 매개 변수에 의해 선택된 대로 다양한 이벤트 플래그 조합을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-742">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-743">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-743">Parameters</span></span>

- <span data-ttu-id="38207-744">**group_ptr**: 이전에 만든 이벤트 플래그 그룹을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-744">**group_ptr**: Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="38207-745">**requested_flags**: 요청된 이벤트 플래그를 나타내는 32비트 부호 없는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-745">**requested_flags**: 32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="38207-746">**get_option**: 요청된 이벤트 플래그의 전체 또는 일부라도 필요한지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-746">**get_option**: Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="38207-747">유효한 선택 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-747">The following are valid selections:</span></span>
    - <span data-ttu-id="38207-748">**TX_AND**:(0x02)</span><span class="sxs-lookup"><span data-stu-id="38207-748">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="38207-749">**TX_AND_CLEAR**:(0x03)</span><span class="sxs-lookup"><span data-stu-id="38207-749">**TX_AND_CLEAR**: (0x03)</span></span>
    - <span data-ttu-id="38207-750">**TX_OR**:(0x00)</span><span class="sxs-lookup"><span data-stu-id="38207-750">**TX_OR**: (0x00)</span></span>
    - <span data-ttu-id="38207-751">**TX_OR_CLEAR**:(0x01)</span><span class="sxs-lookup"><span data-stu-id="38207-751">**TX_OR_CLEAR**: (0x01)</span></span>

    <span data-ttu-id="38207-752">TX_AND 또는 TX_AND_CLEAR를 선택하면 그룹에 모든 이벤트 플래그가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-752">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="38207-753">TX_OR 또는 TX_OR_CLEAR를 선택하면 모든 이벤트 플래그가 만족스러운 것으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-753">Selecting TX_OR or TX_OR_CLEAR specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="38207-754">TX_AND_CLEAR 또는 TX_OR_CLEAR가 지정되면 요청을 만족하는 이벤트 플래그가 지워집니다(0으로 설정).</span><span class="sxs-lookup"><span data-stu-id="38207-754">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="38207-755">**actual_flags_ptr**: 검색된 이벤트 플래그가 배치되는 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-755">**actual_flags_ptr**: Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="38207-756">획득한 실제 플래그는 요청되지 않은 플래그를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-756">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="38207-757">**wait_option**: 선택한 이벤트 플래그가 설정되지 않은 경우 서비스가 동작하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-757">**wait_option**: Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="38207-758">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-758">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38207-759">**TX_NO_WAIT**:(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="38207-759">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="38207-760">**TX_WAIT_FOREVER**:(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38207-760">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="38207-761">시간 제한 값:(0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38207-761">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="38207-762">TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-762">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="38207-763">초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-763">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="38207-764">TX_WAIT_FOREVER를 선택하면 이벤트 플래그를 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-764">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>

    <span data-ttu-id="38207-765">숫자 값(1-0xFFFFFFFE)을 선택하면 이벤트 플래그를 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-765">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-766">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-766">Return Values</span></span>

- <span data-ttu-id="38207-767">**TX_SUCCESS**:(0X00) 이벤트 플래그를 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-767">**TX_SUCCESS**: (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="38207-768">**TX_DELETED**:(0x01) 스레드가 일시 중단된 동안 이벤트 플래그 그룹이 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-768">**TX_DELETED**: (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="38207-769">**TX_NO_EVENTS**:(0X07) 서비스가 지정된 대기 시간 내에 지정된 이벤트를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-769">**TX_NO_EVENTS**: (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="38207-770">**TX_WAIT_ABORTED**:(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-770">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="38207-771">TX_GROUP_ERROR:(0x06) 잘못된 이벤트 플래그 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-771">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="38207-772">TX_PTR_ERROR:(0x03) 실제 이벤트 플래그에 대한 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-772">TX_PTR_ERROR: (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="38207-773">TX_WAIT_ERROR:(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-773">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="38207-774">TX_OPTION_ERROR:(0x08) 잘못된 get-option을 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-774">TX_OPTION_ERROR: (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-775">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-775">Allowed From</span></span>

<span data-ttu-id="38207-776">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-776">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-777">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-777">Preemption Possible</span></span>

<span data-ttu-id="38207-778">예</span><span class="sxs-lookup"><span data-stu-id="38207-778">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-779">예제</span><span class="sxs-lookup"><span data-stu-id="38207-779">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG         actual_events;
UINT          status;

/* Request that event flags 0, 4, and 8 are all set. Also,
   if they are set they should be cleared. If the event
   flags are not set, this service suspends for a maximum of
   20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
                      TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
   actual events obtained. */
```
### <a name="see-also"></a><span data-ttu-id="38207-780">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-780">See Also</span></span>

- <span data-ttu-id="38207-781">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="38207-781">tx_event_flags_create</span></span>
- <span data-ttu-id="38207-782">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="38207-782">tx_event_flags_delete</span></span>
- <span data-ttu-id="38207-783">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-783">tx_event_flags_info_get</span></span>
- <span data-ttu-id="38207-784">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-784">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="38207-785">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-785">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="38207-786">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="38207-786">tx_event_flags_set</span></span>
- <span data-ttu-id="38207-787">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="38207-787">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_info_get"></a><span data-ttu-id="38207-788">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-788">tx_event_flags_info_get</span></span>

<span data-ttu-id="38207-789">이벤트 플래그 그룹에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-789">Retrieve information about event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-790">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-790">Prototype</span></span>

```C
UINT tx_event_flags_info_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                         CHAR **name, ULONG *current_flags,
                         TX_THREAD **first_suspended,
                         ULONG *suspended_count,
                         TX_EVENT_FLAGS_GROUP **next_group);
```
### <a name="description"></a><span data-ttu-id="38207-791">Description</span><span class="sxs-lookup"><span data-stu-id="38207-791">Description</span></span>

<span data-ttu-id="38207-792">이 서비스는 지정된 이벤트 플래그 그룹에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-792">This service retrieves information about the specified event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-793">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-793">Parameters</span></span>

- <span data-ttu-id="38207-794">**group_ptr**: 이벤트 플래그 그룹 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-794">**group_ptr**: Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="38207-795">**name**: 이벤트 플래그 그룹의 이름에 대한 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-795">**name**: Pointer to destination for the pointer to the event flags group’s name.</span></span>
- <span data-ttu-id="38207-796">**current_flags**: 이벤트 플래그 그룹에서 현재 설정된 플래그의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-796">**current_flags**: Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="38207-797">**first_suspended**: 이 이벤트 플래그 그룹의 일시 중단 목록에 있는 첫 번째 스레드 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-797">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="38207-798">**suspended_count**: 이 이벤트 플래그 그룹에서 현재 일시 중단된 스레드 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-798">**suspended_count**: Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="38207-799">**next_group**: 다음에 생성된 이벤트 플래그 그룹의 포인터에 대한 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-799">**next_group**: Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-800">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-800">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-801">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-801">Return Values</span></span>

- <span data-ttu-id="38207-802">**TX_SUCCESS**:(0x00) 이벤트 그룹 정보를 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-802">**TX_SUCCESS**: (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="38207-803">TX_GROUP_ERROR:(0x06) 잘못된 이벤트 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-803">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-804">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-804">Allowed From</span></span>

<span data-ttu-id="38207-805">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-805">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-806">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-806">Preemption Possible</span></span>

<span data-ttu-id="38207-807">예</span><span class="sxs-lookup"><span data-stu-id="38207-807">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-808">예제</span><span class="sxs-lookup"><span data-stu-id="38207-808">Example</span></span>

```c
TX_EVENT_FLAGS_GROUPmy_event_group;
CHAR          *name;
ULONG         current_flags;
TX_THREAD     *first_suspended;
ULONG         suspended_count;
TX_EVENT_FLAGS_GROUP*next_group;
UINT          status;

/* Retrieve information about the previously created
   event flags group "my_event_group." */
status =  tx_event_flags_info_get(&my_event_group, &name,
             &current_flags,
             &first_suspended, &suspended_count,
             &next_group);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="38207-809">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-809">See Also</span></span>

- <span data-ttu-id="38207-810">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="38207-810">tx_event_flags_create</span></span>
- <span data-ttu-id="38207-811">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="38207-811">tx_event_flags_delete</span></span>
- <span data-ttu-id="38207-812">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="38207-812">tx_event_flags_get</span></span>
- <span data-ttu-id="38207-813">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-813">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="38207-814">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-814">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="38207-815">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="38207-815">tx_event_flags_set</span></span>
- <span data-ttu-id="38207-816">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="38207-816">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance-info_get"></a><span data-ttu-id="38207-817">tx_event_flags_performance info_get</span><span class="sxs-lookup"><span data-stu-id="38207-817">tx_event_flags_performance info_get</span></span>

<span data-ttu-id="38207-818">이벤트 플래그 그룹 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-818">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-819">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-819">Prototype</span></span>

```C
UINT tx_event_flags_performance_info_get(TX_EVENT_FLAGS_GROUP
                        *group_ptr, ULONG *sets, ULONG *gets,
                        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="38207-820">Description</span><span class="sxs-lookup"><span data-stu-id="38207-820">Description</span></span>

<span data-ttu-id="38207-821">이 서비스는 지정된 이벤트 플래그 그룹에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-821">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-822">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-822">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-823">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-823">Parameters</span></span>

- <span data-ttu-id="38207-824">**group_ptr**: 이전에 만든 이벤트 플래그 그룹을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-824">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="38207-825">**sets**: 이 그룹에서 수행된 이벤트 플래그 설정 요청 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-825">**sets**: Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="38207-826">**gets** 이 그룹에서 수행된 이벤트 플래그 가져오기 요청 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-826">**gets**: Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="38207-827">**suspensions** 이 그룹의 스레드 이벤트 플래그 가져오기 일시 중단 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-827">**suspensions**: Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="38207-828">**timeouts** 이 그룹의 이벤트 플래그 가져오기 일시 중단 시간 초과 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-828">**timeouts**: Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-829">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-829">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-830">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-830">Return Values</span></span>

- <span data-ttu-id="38207-831">**TX_SUCCESS**:(0x00) 이벤트 플래그 그룹 성능을 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-831">**TX_SUCCESS**: (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="38207-832">**TX_PTR_ERROR**:(0x03) 잘못된 이벤트 플래그 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-832">**TX_PTR_ERROR**: (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="38207-833">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-833">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-834">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-834">Allowed From</span></span>

<span data-ttu-id="38207-835">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-835">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-836">예제</span><span class="sxs-lookup"><span data-stu-id="38207-836">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_event_flag_group;
ULONG           sets;
ULONG           gets;
ULONG           suspensions;
ULONG           timeouts;

/* Retrieve performance information on the previously created event
   flag group. */
status =  tx_event_flags_performance_info_get(&my_event_flag_group,
   &sets, &gets, &suspensions,
   &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
   retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-837">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-837">See Also</span></span>

- <span data-ttu-id="38207-838">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="38207-838">tx_event_flags_create</span></span>
- <span data-ttu-id="38207-839">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="38207-839">tx_event_flags_delete</span></span>
- <span data-ttu-id="38207-840">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="38207-840">tx_event_flags_get</span></span>
- <span data-ttu-id="38207-841">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-841">tx_event_flags_info_get</span></span>
- <span data-ttu-id="38207-842">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-842">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="38207-843">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="38207-843">tx_event_flags_set</span></span>
- <span data-ttu-id="38207-844">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="38207-844">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="38207-845">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-845">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="38207-846">성능 시스템 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-846">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-847">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-847">Prototype</span></span>

```c
UINT  tx_event_flags_performance_system_info_get(ULONG *sets,
        ULONG *gets,ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="38207-848">Description</span><span class="sxs-lookup"><span data-stu-id="38207-848">Description</span></span>

<span data-ttu-id="38207-849">이 서비스는 시스템의 모든 이벤트 플래그 그룹에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-849">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-850">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-850">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-851">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-851">Parameters</span></span>

- <span data-ttu-id="38207-852">**sets**: 모든 그룹에서 수행된 총 이벤트 플래그 설정 요청 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-852">**sets**: Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="38207-853">**gets**: 모든 그룹에서 수행된 총 이벤트 플래그 가져오기 요청 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-853">**gets**: Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="38207-854">**suspensions** 모든 그룹의 총 스레드 이벤트 플래그 가져오기 일시 중단 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-854">**suspensions**: Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="38207-855">**timeouts** 모든 그룹의 총 이벤트 플래그 가져오기 일시 중단 시간 초과 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-855">**timeouts**: Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-856">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-856">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-857">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-857">Return Values</span></span>

- <span data-ttu-id="38207-858">**TX_SUCCESS**:(0x00) 이벤트 플래그 시스템 성능을 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-858">**TX_SUCCESS**: (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="38207-859">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-859">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-860">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-860">Allowed From</span></span>

<span data-ttu-id="38207-861">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-861">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-862">예제</span><span class="sxs-lookup"><span data-stu-id="38207-862">Example</span></span>

```c
ULONG         sets;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created event
   flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-863">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-863">See Also</span></span>

- <span data-ttu-id="38207-864">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="38207-864">tx_event_flags_create</span></span>
- <span data-ttu-id="38207-865">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="38207-865">tx_event_flags_delete</span></span>
- <span data-ttu-id="38207-866">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="38207-866">tx_event_flags_get</span></span>
- <span data-ttu-id="38207-867">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-867">tx_event_flags_info_get</span></span>
- <span data-ttu-id="38207-868">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-868">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="38207-869">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="38207-869">tx_event_flags_set</span></span>
- <span data-ttu-id="38207-870">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="38207-870">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="38207-871">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="38207-871">tx_event_flags_set</span></span>

<span data-ttu-id="38207-872">이벤트 플래그 그룹에 이벤트 플래그 설정</span><span class="sxs-lookup"><span data-stu-id="38207-872">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-873">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-873">Prototype</span></span>

```C
UINT tx_event_flags_set(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG  flags_to_set,UINT set_option);
```
### <a name="description"></a><span data-ttu-id="38207-874">Description</span><span class="sxs-lookup"><span data-stu-id="38207-874">Description</span></span>

<span data-ttu-id="38207-875">이 서비스는 지정된 set_option에 따라 이벤트 플래그 그룹에서 이벤트 플래그를 설정하거나 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="38207-875">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="38207-876">이제 이벤트 플래그 요청이 충족된 일시 중단된 모든 스레드가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-876">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-877">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-877">Parameters</span></span>

- <span data-ttu-id="38207-878">**group_ptr**: 이전에 만든 이벤트 플래그 그룹 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-878">**group_ptr**: Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="38207-879">**flags_to_set**: 선택한 set_option에 따라 설정하거나 지울 이벤트 플래그를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-879">**flags_to_set**: Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="38207-880">**set_option**: 지정된 이벤트 플래그를 그룹의 현재 이벤트 플래그에 AND로 연결할지 또는 OR로 연결할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-880">**set_option**: Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="38207-881">유효한 선택 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-881">The following are valid selections:</span></span>
    - <span data-ttu-id="38207-882">**TX_AND**:(0x02)</span><span class="sxs-lookup"><span data-stu-id="38207-882">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="38207-883">**TX_OR**:(0x00) TX_AND를 선택하면 지정된 이벤트 플래그가 그룹의 현재 이벤트 플래그에 **AND** 로 연결되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-883">**TX_OR**: (0x00) Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="38207-884">이 옵션은 종종 그룹의 이벤트 플래그를 지우는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-884">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="38207-885">그렇지 않고 TX_OR이 지정된 경우 지정된 이벤트 플래그가 그룹의 현재 이벤트에 **OR** 로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-885">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-886">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-886">Return Values</span></span>

- <span data-ttu-id="38207-887">**TX_SUCCESS**:(0X00) 이벤트 플래그를 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-887">**TX_SUCCESS**: (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="38207-888">TX_GROUP_ERROR:(0x06) 잘못된 이벤트 플래그 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-888">TX_GROUP_ERROR: (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="38207-889">TX_OPTION_ERROR:(0x08) 잘못된 set-option을 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-889">TX_OPTION_ERROR: (0x08) Invalid set-option specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-890">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-890">Allowed From</span></span>

<span data-ttu-id="38207-891">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-891">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-892">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-892">Preemption Possible</span></span>

<span data-ttu-id="38207-893">예</span><span class="sxs-lookup"><span data-stu-id="38207-893">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-894">예제</span><span class="sxs-lookup"><span data-stu-id="38207-894">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_event_flags_group;
UINT         status;

/* Set event flags 0, 4, and 8. */
status =  tx_event_flags_set(&my_event_flags_group,
                           0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
   set and any suspended thread whose request was satisfied
   has been resumed. */
```
### <a name="see-also"></a><span data-ttu-id="38207-895">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-895">See Also</span></span>

- <span data-ttu-id="38207-896">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="38207-896">tx_event_flags_create</span></span>
- <span data-ttu-id="38207-897">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="38207-897">tx_event_flags_delete</span></span>
- <span data-ttu-id="38207-898">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="38207-898">tx_event_flags_get</span></span>
- <span data-ttu-id="38207-899">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-899">tx_event_flags_info_get</span></span>
- <span data-ttu-id="38207-900">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-900">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="38207-901">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-901">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="38207-902">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="38207-902">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="38207-903">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="38207-903">tx_event_flags_set_notify</span></span>

<span data-ttu-id="38207-904">이벤트 플래그가 설정되면 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="38207-904">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-905">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-905">Prototype</span></span>

```C
UINT tx_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr,
       VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```
### <a name="description"></a><span data-ttu-id="38207-906">Description</span><span class="sxs-lookup"><span data-stu-id="38207-906">Description</span></span>

<span data-ttu-id="38207-907">이 서비스는 지정된 이벤트 플래그 그룹에 하나 이상의 이벤트 플래그가 설정될 때마다 호출되는 알림 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-907">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="38207-908">알림 콜백의 처리는 애플리케이션에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-908">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="38207-909">애플리케이션의 이벤트 플래그 설정 알림 콜백은 일시 중단 옵션을 사용하여 ThreadX SMP API를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-909">The application’s event flags set notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-910">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-910">Parameters</span></span> 
- <span data-ttu-id="38207-911">**group_ptr**: 이전에 만든 이벤트 플래그 그룹을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-911">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="38207-912">**events_set_notify**: 애플리케이션의 이벤트 플래그 설정 알림 기능을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-912">**events_set_notify**: Pointer to application’s event flags set notification function.</span></span> <span data-ttu-id="38207-913">이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-913">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-914">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-914">Return Values</span></span>

- <span data-ttu-id="38207-915">**TX_SUCCESS**:(0x00) 이벤트 플래그 설정 알림을 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-915">**TX_SUCCESS**: (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="38207-916">TX_GROUP_ERROR:(0x06) 잘못된 이벤트 플래그 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-916">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="38207-917">TX_FEATURE_NOT_ENABLED:(0xFF) 시스템이 알림 기능을 사용하지 않도록 설정하여 컴파일되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-917">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-918">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-918">Allowed From</span></span>

<span data-ttu-id="38207-919">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-919">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-920">예제</span><span class="sxs-lookup"><span data-stu-id="38207-920">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_group;

/* Register the "my_event_flags_set_notify" function for monitoring
   event flags set in the event flags group "my_group." */
status =  tx_event_flags_set_notify(&my_group,
                my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
   was successfully registered. */

void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)
   /* One or more event flags was set in this group! */
```
### <a name="see-also"></a><span data-ttu-id="38207-921">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-921">See Also</span></span>

- <span data-ttu-id="38207-922">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="38207-922">tx_event_flags_create</span></span>
- <span data-ttu-id="38207-923">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="38207-923">tx_event_flags_delete</span></span>
- <span data-ttu-id="38207-924">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="38207-924">tx_event_flags_get</span></span>
- <span data-ttu-id="38207-925">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-925">tx_event_flags_info_get</span></span>
- <span data-ttu-id="38207-926">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-926">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="38207-927">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-927">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="38207-928">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="38207-928">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="38207-929">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="38207-929">tx_interrupt_control</span></span>

<span data-ttu-id="38207-930">인터럽트 사용 및 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="38207-930">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-931">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-931">Prototype</span></span>

```C
UINT tx_interrupt_control(UINT new_posture);
```
### <a name="description"></a><span data-ttu-id="38207-932">Description</span><span class="sxs-lookup"><span data-stu-id="38207-932">Description</span></span>

<span data-ttu-id="38207-933">이 서비스는 입력 매개 변수 **new_posture** 로 지정된 인터럽트를 사용하거나 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-933">This service enables or disables interrupts as specified by the input parameter **new_posture**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-934">이 서비스가 애플리케이션 스레드에서 호출되는 경우 인터럽트 상태는 해당 스레드의 컨텍스트에 포함된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-934">If this service is called from an application thread, the interrupt posture remains part of that thread’s context.</span></span> <span data-ttu-id="38207-935">예를 들어, 스레드가 이 루틴을 호출하여 인터럽트를 사용하지 않도록 설정한 후 일시 중단되었다가 다시 시작되면 인터럽트가 다시 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-935">For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.</span></span>

> [!WARNING]
> <span data-ttu-id="38207-936">초기화하는 동안에는 이 서비스를 사용하여 인터럽트를 사용하도록 설정하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-936">This service should not be used to enable interrupts during initialization!</span></span> <span data-ttu-id="38207-937">이렇게 하면 예기치 않은 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-937">Doing so could cause unpredictable results.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-938">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-938">Parameters</span></span>

- <span data-ttu-id="38207-939">**new_posture**: 이 매개 변수는 인터럽트가 사용하지 않도록 설정되었는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-939">**new_posture**: This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="38207-940">올바른 값에는 **TX_INT_DISABLE 및 TX_INT_ENABLE** 이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-940">Legal values include **TX_INT_DISABLE and TX_INT_ENABLE.**</span></span> <span data-ttu-id="38207-941">이러한 매개 변수의 실제 값은 포트마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-941">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="38207-942">또한 일부 처리 아키텍처는 추가 인터럽트 사용 안 함 상태를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-942">In addition, some processing architectures might support additional interrupt disable postures.</span></span> <span data-ttu-id="38207-943">자세한 내용은 배포 디스크에 제공된 **_readme_threadx.txt_** 정보를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38207-943">Please see the **_readme_threadx.txt_** information supplied on the distribution disk for more details.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-944">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-944">Return Values</span></span>

- <span data-ttu-id="38207-945">이전 상태: 이 서비스는 호출자에게 이전 인터럽트 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-945">previous posture: This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="38207-946">이렇게 하면 서비스 사용자가 인터럽트를 사용하지 않도록 설정한 후 이전 상태를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-946">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-947">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-947">Allowed From</span></span>

<span data-ttu-id="38207-948">스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-948">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-949">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-949">Preemption Possible</span></span>

<span data-ttu-id="38207-950">예</span><span class="sxs-lookup"><span data-stu-id="38207-950">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-951">예제</span><span class="sxs-lookup"><span data-stu-id="38207-951">Example</span></span>

```C
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture =  tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
   locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```
### <a name="see-also"></a><span data-ttu-id="38207-952">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-952">See Also</span></span>

<span data-ttu-id="38207-953">None</span><span class="sxs-lookup"><span data-stu-id="38207-953">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="38207-954">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="38207-954">tx_mutex_create</span></span>

<span data-ttu-id="38207-955">상호 제외 뮤텍스 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-955">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-956">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-956">Prototype</span></span>

```C
UINT tx_mutex_create(TX_MUTEX *mutex_ptr,
                          CHAR *name_ptr, UINT priority_inherit);
```
### <a name="description"></a><span data-ttu-id="38207-957">Description</span><span class="sxs-lookup"><span data-stu-id="38207-957">Description</span></span>
    
<span data-ttu-id="38207-958">이 서비스는 리소스 보호에 대한 스레드 간 상호 제외를 위해 뮤텍스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38207-958">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-959">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-959">Parameters</span></span>

- <span data-ttu-id="38207-960">**mutex_ptr**: 뮤텍스 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-960">**mutex_ptr**: Pointer to a mutex control block.</span></span>
- <span data-ttu-id="38207-961">**name_ptr**: 뮤텍스 이름을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-961">**name_ptr**: Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="38207-962">**priority_inherit**: 이 뮤텍스가 우선 순위 상속을 지원하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-962">**priority_inherit**: Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="38207-963">이 값이 TX_INHERIT인 경우 우선 순위 상속이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-963">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="38207-964">그러나 TX_NO_INHERIT를 지정하면 이 뮤텍스에서 우선 순위 상속을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-964">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-965">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-965">Return Values</span></span>

- <span data-ttu-id="38207-966">**TX_SUCCESS**:(0X00) 뮤텍스를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-966">**TX_SUCCESS**: (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="38207-967">TX_MUTEX_ERROR:(0x1C) 잘못된 뮤텍스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-967">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="38207-968">포인터가 NULL이거나 뮤텍스가 이미 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-968">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="38207-969">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-969">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="38207-970">TX_INHERIT_ERROR:(0x1F) 잘못된 우선 순위 상속 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-970">TX_INHERIT_ERROR: (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-971">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-971">Allowed From</span></span>

<span data-ttu-id="38207-972">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="38207-972">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-973">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-973">Preemption Possible</span></span>

<span data-ttu-id="38207-974">예</span><span class="sxs-lookup"><span data-stu-id="38207-974">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-975">예제</span><span class="sxs-lookup"><span data-stu-id="38207-975">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Create a mutex to provide protection over a
   common resource. */
status =  tx_mutex_create(&my_mutex,"my_mutex_name",
                           TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
   use. */
```
### <a name="see-also"></a><span data-ttu-id="38207-976">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-976">See Also</span></span>

- <span data-ttu-id="38207-977">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="38207-977">tx_mutex_delete</span></span>
- <span data-ttu-id="38207-978">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="38207-978">tx_mutex_get</span></span>
- <span data-ttu-id="38207-979">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-979">tx_mutex_info_get</span></span>
- <span data-ttu-id="38207-980">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-980">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="38207-981">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-981">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="38207-982">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-982">tx_mutex_prioritize</span></span>
- <span data-ttu-id="38207-983">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="38207-983">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="38207-984">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="38207-984">tx_mutex_delete</span></span>

<span data-ttu-id="38207-985">상호 제외 뮤텍스 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-985">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-986">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-986">Prototype</span></span>

```C
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-987">Description</span><span class="sxs-lookup"><span data-stu-id="38207-987">Description</span></span>

<span data-ttu-id="38207-988">이 서비스는 지정된 뮤텍스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-988">This service deletes the specified mutex.</span></span> <span data-ttu-id="38207-989">뮤텍스를 기다리는 일시 중단된 모든 스레드는 다시 시작되며 TX_DELETED 반환 상태가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-989">All threads suspended waiting for the mutex are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-990">애플리케이션은 삭제된 뮤텍스를 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-990">It is the application’s responsibility to prevent use of a deleted mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-991">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-991">Parameters</span></span>

- <span data-ttu-id="38207-992">**mutex_ptr**: 이전에 만든 뮤텍스를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-992">**mutex_ptr**: Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-993">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-993">Return Values</span></span>

- <span data-ttu-id="38207-994">**TX_SUCCESS**:(0X00) 뮤텍스를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-994">**TX_SUCCESS**: (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="38207-995">TX_MUTEX_ERROR:(0x1C) 잘못된 뮤텍스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-995">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="38207-996">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-996">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-997">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-997">Allowed From</span></span>

<span data-ttu-id="38207-998">스레드</span><span class="sxs-lookup"><span data-stu-id="38207-998">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-999">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-999">Preemption Possible</span></span>

<span data-ttu-id="38207-1000">예</span><span class="sxs-lookup"><span data-stu-id="38207-1000">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-1001">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1001">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Delete a mutex. Assume that the mutex
   has already been created. */
status =  tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1002">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1002">See Also</span></span>

- <span data-ttu-id="38207-1003">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="38207-1003">tx_mutex_create</span></span>
- <span data-ttu-id="38207-1004">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="38207-1004">tx_mutex_get</span></span>
- <span data-ttu-id="38207-1005">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1005">tx_mutex_info_get</span></span>
- <span data-ttu-id="38207-1006">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1006">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="38207-1007">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1007">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1008">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1008">tx_mutex_prioritize</span></span>
- <span data-ttu-id="38207-1009">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="38207-1009">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="38207-1010">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="38207-1010">tx_mutex_get</span></span>

<span data-ttu-id="38207-1011">뮤텍스의 소유권 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-1011">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1012">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1012">Prototype</span></span>

```C
UINT tx_mutex_get(TX_MUTEX *mutex_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="38207-1013">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1013">Description</span></span>

<span data-ttu-id="38207-1014">이 서비스는 지정된 뮤텍스의 전용 소유권을 가져오려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1014">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="38207-1015">호출 스레드가 뮤텍스를 이미 소유하고 있으면 내부 카운터가 증분되고 성공적인 상태가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1015">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="38207-1016">뮤텍스를 다른 스레드에서 소유하고 이 스레드가 더 높은 우선 순위를 가지며 뮤텍스 생성 시 우선 순위 상속이 지정된 경우 우선 순위가 낮은 스레드의 우선 순위가 호출 스레드의 우선 순위로 일시적으로 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1016">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread’s priority will be temporarily raised to that of the calling thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1017">priorityinheritance가 지정된 뮤텍스를 소유하는 우선 순위가 낮은 스레드의 우선 순위는 뮤텍스 소유권이 있는 동안 외부 스레드에 의해 수정되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1017">The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1018">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1018">Parameters</span></span>

- <span data-ttu-id="38207-1019">**mutex_ptr**: 이전에 만든 뮤텍스를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1019">**mutex_ptr**: Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="38207-1020">**wait_option**: 다른 스레드가 뮤텍스를 이미 소유하고 있는 경우 서비스가 동작하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1020">**wait_option**: Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="38207-1021">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1021">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38207-1022">**TX_NO_WAIT**:(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="38207-1022">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="38207-1023">**TX_WAIT_FOREVER**:(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38207-1023">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="38207-1024">시간 제한 값:(0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38207-1024">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="38207-1025">TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1025">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="38207-1026">초기화에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1026">*This is the only valid option if the service is called from Initialization.*</span></span>

    <span data-ttu-id="38207-1027">TX_WAIT_FOREVER를 선택하면 뮤텍스를 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1027">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the mutex is available.</span></span>

    <span data-ttu-id="38207-1028">숫자 값(1-0xFFFFFFFE)을 선택하면 뮤텍스를 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1028">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1029">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1029">Return Values</span></span>

- <span data-ttu-id="38207-1030">**TX_SUCCESS**:(0X00) 뮤텍스 가져오기 작업에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1030">**TX_SUCCESS**: (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="38207-1031">**TX_DELETED**:(0x01) 스레드가 일시 중단된 동안 뮤텍스가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1031">**TX_DELETED**: (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="38207-1032">**TX_NOT_AVAILABLE**:(0x1D) 서비스가 지정된 대기 시간 내에 뮤텍스의 소유권을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1032">**TX_NOT_AVAILABLE**: (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="38207-1033">**TX_WAIT_ABORTED**:(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1033">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="38207-1034">TX_MUTEX_ERROR:(0x1C) 잘못된 뮤텍스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1034">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="38207-1035">TX_WAIT_ERROR:(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1035">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="38207-1036">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1036">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1037">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1037">Allowed From</span></span>

<span data-ttu-id="38207-1038">초기화, 스레드 및 타이머</span><span class="sxs-lookup"><span data-stu-id="38207-1038">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1039">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1039">Preemption Possible</span></span>

<span data-ttu-id="38207-1040">예</span><span class="sxs-lookup"><span data-stu-id="38207-1040">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-1041">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1041">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Obtain exclusive ownership of the mutex "my_mutex".
   If the mutex "my_mutex" is not available, suspend until it
   becomes available. */
status =  tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```
### <a name="see-also"></a><span data-ttu-id="38207-1042">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1042">See Also</span></span>

- <span data-ttu-id="38207-1043">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="38207-1043">tx_mutex_create</span></span>
- <span data-ttu-id="38207-1044">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1044">tx_mutex_delete</span></span>
- <span data-ttu-id="38207-1045">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1045">tx_mutex_info_get</span></span>
- <span data-ttu-id="38207-1046">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1046">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="38207-1047">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1047">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1048">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1048">tx_mutex_prioritize</span></span>
- <span data-ttu-id="38207-1049">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="38207-1049">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="38207-1050">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1050">tx_mutex_info_get</span></span>

<span data-ttu-id="38207-1051">뮤텍스에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-1051">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1052">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1052">Prototype</span></span>

```C
UINT tx_mutex_info_get(TX_MUTEX *mutex_ptr, CHAR **name,
                          ULONG *count, TX_THREAD **owner,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count, TX_MUTEX **next_mutex);
```
### <a name="description"></a><span data-ttu-id="38207-1053">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1053">Description</span></span>

<span data-ttu-id="38207-1054">이 서비스는 지정된 뮤텍스에서 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1054">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1055">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1055">Parameters</span></span>

- <span data-ttu-id="38207-1056">**mutex_ptr**: 뮤텍스 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1056">**mutex_ptr**: Pointer to mutex control block.</span></span>
- <span data-ttu-id="38207-1057">**name**: 뮤텍스 이름에 대한 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1057">**name**: Pointer to destination for the pointer to the mutex’s name.</span></span>
- <span data-ttu-id="38207-1058">**count**: 뮤텍스의 소유권 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1058">**count**: Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="38207-1059">**owner**: 소유 스레드 포인터의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1059">**owner**: Pointer to destination for the owning thread’s pointer.</span></span>
- <span data-ttu-id="38207-1060">**first_suspended**: 이 뮤텍스의 일시 중단 목록 맨 처음에 나오는 스레드에 대한 포인터의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1060">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="38207-1061">**suspended_count**: 이 뮤텍스에서 현재 일시 중단된 스레드 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1061">**suspended_count**: Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="38207-1062">**next_mutex**: 다음에 만든 뮤텍스 포인트의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1062">**next_mutex**: Pointer to destination for the pointer of the next created mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1063">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1063">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1064">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1064">Return Values</span></span>

- <span data-ttu-id="38207-1065">**NX_SUCCESS**:(0x00) 뮤텍스 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1065">**TX_SUCCESS**: (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="38207-1066">TX_MUTEX_ERROR:(0x1C) 잘못된 뮤텍스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1066">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1067">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1067">Allowed From</span></span>

<span data-ttu-id="38207-1068">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1068">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1069">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1069">Preemption Possible</span></span>

<span data-ttu-id="38207-1070">예</span><span class="sxs-lookup"><span data-stu-id="38207-1070">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-1071">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1071">Example</span></span>

```C
TX_MUTEX     my_mutex;
CHAR         *name;
ULONG        count;
TX_THREAD    *owner;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_MUTEX     *next_mutex;
UINT         status;

/* Retrieve information about the previously created
   mutex "my_mutex." */
status =  tx_mutex_info_get(&my_mutex, &name,
                          &count, &owner,
                          &first_suspended, &suspended_count,
                          &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1072">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1072">See Also</span></span>

- <span data-ttu-id="38207-1073">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="38207-1073">tx_mutex_create</span></span>
- <span data-ttu-id="38207-1074">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1074">tx_mutex_delete</span></span>
- <span data-ttu-id="38207-1075">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="38207-1075">tx_mutex_get</span></span>
- <span data-ttu-id="38207-1076">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1076">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="38207-1077">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1077">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1078">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1078">tx_mutex_prioritize</span></span>
- <span data-ttu-id="38207-1079">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="38207-1079">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="38207-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1080">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="38207-1081">뮤텍스 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-1081">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1082">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1082">Prototype</span></span>

```C
UINT tx_mutex_performance_info_get(TX_MUTEX *mutex_ptr, ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts,
       ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="38207-1083">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1083">Description</span></span>

<span data-ttu-id="38207-1084">이 서비스는 지정된 뮤텍스에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1084">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1085">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_MUTEX_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1085">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1086">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1086">Parameters</span></span>

- <span data-ttu-id="38207-1087">**mutex_ptr**: 이전에 만든 뮤텍스를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1087">**mutex_ptr**: Pointer to previously created mutex.</span></span>
- <span data-ttu-id="38207-1088">**puts** 이 뮤텍스에서 수행된 요청 수행 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1088">**puts**: Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="38207-1089">**gets** 이 뮤텍스에서 수행된 요청 가져오기 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1089">**gets**: Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="38207-1090">**suspensions**: 이 뮤텍스에 대한 스레드 뮤텍스 가져오기 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1090">**suspensions**: Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="38207-1091">**timeouts**: 이 뮤텍스의 뮤텍스 가져오기 일시 중단 시간 제한 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1091">**timeouts**: Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="38207-1092">**inversions**: 이 뮤텍스에 있는 스레드 우선 순위 반전 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1092">**inversions**: Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="38207-1093">**inheritances**: 이 뮤텍스에 있는 스레드 우선 순위 상속 작업 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1093">**inheritances**: Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1094">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1094">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1095">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1095">Return Values</span></span>

- <span data-ttu-id="38207-1096">**TX_SUCCESS**:(0X00) 뮤텍스 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1096">**TX_SUCCESS**: (0x00) Successful mutex performance get.</span></span> 
- <span data-ttu-id="38207-1097">**TX_PTR_ERROR**:(0x03) 잘못된 뮤텍스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1097">**TX_PTR_ERROR**: (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="38207-1098">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1098">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1099">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1099">Allowed From</span></span>

<span data-ttu-id="38207-1100">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1100">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-1101">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1101">Example</span></span>

```C
TX_MUTEX     my_mutex;
ULONG        puts;
ULONG        gets;
ULONG        suspensions;
ULONG        timeouts;
ULONG        inversions;
ULONG        inheritances;

/* Retrieve performance information on the previously created
   mutex. */
status =  tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
                &suspensions, &timeouts, &inversions,
                &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1102">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1102">See Also</span></span>

- <span data-ttu-id="38207-1103">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="38207-1103">tx_mutex_create</span></span>
- <span data-ttu-id="38207-1104">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1104">tx_mutex_delete</span></span>
- <span data-ttu-id="38207-1105">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="38207-1105">tx_mutex_get</span></span>
- <span data-ttu-id="38207-1106">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1106">tx_mutex_info_get</span></span>
- <span data-ttu-id="38207-1107">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1107">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1108">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1108">tx_mutex_prioritize</span></span>
- <span data-ttu-id="38207-1109">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="38207-1109">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="38207-1110">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1110">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="38207-1111">뮤텍스 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-1111">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1112">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1112">Prototype</span></span>

```C
UINT  tx_mutex_performance_system_info_get(ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts,
        ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="38207-1113">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1113">Description</span></span>

<span data-ttu-id="38207-1114">이 서비스는 시스템의 모든 뮤텍스에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1114">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1115">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_MUTEX_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1115">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1116">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1116">Parameters</span></span>

- <span data-ttu-id="38207-1117">**puts** 모든 뮤텍스에서 수행된 총 요청 수행 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1117">**puts**: Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="38207-1118">**gets** 모든 뮤텍스에서 수행된 총 요청 가져오기 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1118">**gets**: Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="38207-1119">**suspensions** 모든 뮤텍스의 총 스레드 뮤텍스 가져오기 일시 중단 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1119">**suspensions**: Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="38207-1120">**timeouts** 모든 뮤텍스의 총 뮤텍스 가져오기 일시 중단 시간 초과 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1120">**timeouts**: Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="38207-1121">**inversions**: 모든 뮤텍스에 있는 총 스레드 우선 순위 반전 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1121">**inversions**: Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="38207-1122">**inheritances**: 모든 뮤텍스에 있는 총 스레드 우선 순위 상속 작업 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1122">**inheritances**: Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1123">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1123">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1124">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1124">Return Values</span></span>

- <span data-ttu-id="38207-1125">**TX_SUCCESS**:(0X00) 뮤텍스 시스템 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1125">**TX_SUCCESS**: (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="38207-1126">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1126">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1127">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1127">Allowed From</span></span>

<span data-ttu-id="38207-1128">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1128">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-1129">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1129">Example</span></span>

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;
ULONG         inversions;
ULONG         inheritances;

/* Retrieve performance information on all previously created
   mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
                &suspensions, &timeouts,
                &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1130">See Also</span></span>

- <span data-ttu-id="38207-1131">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="38207-1131">tx_mutex_create</span></span>
- <span data-ttu-id="38207-1132">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1132">tx_mutex_delete</span></span>
- <span data-ttu-id="38207-1133">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="38207-1133">tx_mutex_get</span></span>
- <span data-ttu-id="38207-1134">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1134">tx_mutex_info_get</span></span>
- <span data-ttu-id="38207-1135">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1135">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="38207-1136">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1136">tx_mutex_prioritize</span></span>
- <span data-ttu-id="38207-1137">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="38207-1137">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="38207-1138">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1138">tx_mutex_prioritize</span></span>

<span data-ttu-id="38207-1139">뮤텍스 일시 중단 목록 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="38207-1139">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1140">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1140">Prototype</span></span>

```C
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-1141">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1141">Description</span></span>

<span data-ttu-id="38207-1142">이 서비스는 뮤텍스트 소유권에 대해 일시 중단된 최고 우선 순위 스레드를 일시 중단 목록 맨 앞에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1142">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="38207-1143">다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1143">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1144">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1144">Parameters</span></span> 

- <span data-ttu-id="38207-1145">**mutex_ptr**: 이전에 만든 뮤텍스를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1145">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1146">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1146">Return Values</span></span>

- <span data-ttu-id="38207-1147">**TX_SUCCESS**:(0X00) 뮤텍스의 우선 순위를 성공적으로 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1147">**TX_SUCCESS**: (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="38207-1148">TX_MUTEX_ERROR:(0x1C) 잘못된 뮤텍스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1148">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1149">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1149">Allowed From</span></span>

<span data-ttu-id="38207-1150">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1150">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1151">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1151">Preemption Possible</span></span>

<span data-ttu-id="38207-1152">예</span><span class="sxs-lookup"><span data-stu-id="38207-1152">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-1153">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1153">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Ensure that the highest priority thread will receive
   ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_mutex_put call that releases ownership of the
   mutex will give ownership to this thread and wake it
   up. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1154">See Also</span></span>

- <span data-ttu-id="38207-1155">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="38207-1155">tx_mutex_create</span></span>
- <span data-ttu-id="38207-1156">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1156">tx_mutex_delete</span></span>
- <span data-ttu-id="38207-1157">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="38207-1157">tx_mutex_get</span></span>
- <span data-ttu-id="38207-1158">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1158">tx_mutex_info_get</span></span>
- <span data-ttu-id="38207-1159">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1159">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="38207-1160">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1160">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1161">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="38207-1161">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="38207-1162">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="38207-1162">tx_mutex_put</span></span>

<span data-ttu-id="38207-1163">뮤텍스의 소유권 해제</span><span class="sxs-lookup"><span data-stu-id="38207-1163">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1164">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1164">Prototype</span></span>

```C
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-1165">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1165">Description</span></span>

<span data-ttu-id="38207-1166">이 서비스는 지정된 뮤텍스의 소유권 수를 감소시킵니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1166">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="38207-1167">소유권 수가 0이면 뮤텍스를 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1167">If the ownership count is zero, the mutex is made available.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1168">뮤텍스를 만드는 동안 우선 순위 상속이 선택된 경우 해제 스레드 우선 순위가 처음에 뮤텍스의 소유권을 얻었을 때의 우선 순위로 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1168">If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex.</span></span> <span data-ttu-id="38207-1169">뮤텍스를 소유하는 동안 해제 스레드에 적용되는 다른 모든 우선 순위 변경 작업은 실행 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1169">Any other priority changes made to the releasing thread during ownership of the mutex may be undone.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1170">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1170">Parameters</span></span>

- <span data-ttu-id="38207-1171">**mutex_ptr**: 이전에 만든 뮤텍스를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1171">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1172">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1172">Return Values</span></span>

- <span data-ttu-id="38207-1173">**TX_SUCCESS**:(0X00) 뮤텍스를 성공적으로 해제했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1173">**TX_SUCCESS**: (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="38207-1174">**TX_NOT_OWNED**:(0x1E) 뮤텍스를 호출자가 소유하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1174">**TX_NOT_OWNED**: (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="38207-1175">TX_MUTEX_ERROR:(0x1C) 뮤텍스에 대한 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1175">TX_MUTEX_ERROR: (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="38207-1176">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1176">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1177">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1177">Allowed From</span></span>

<span data-ttu-id="38207-1178">초기화, 스레드 및 타이머</span><span class="sxs-lookup"><span data-stu-id="38207-1178">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1179">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1179">Preemption Possible</span></span>

<span data-ttu-id="38207-1180">예</span><span class="sxs-lookup"><span data-stu-id="38207-1180">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-1181">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1181">Example</span></span>

```C
TX_MUTEX         my_mutex;
UINT             status;
/* Release ownership of "my_mutex." */
status =  tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
   count has been decremented and if zero, released. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1182">See Also</span></span>

- <span data-ttu-id="38207-1183">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="38207-1183">tx_mutex_create</span></span>
- <span data-ttu-id="38207-1184">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1184">tx_mutex_delete</span></span>
- <span data-ttu-id="38207-1185">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="38207-1185">tx_mutex_get</span></span>
- <span data-ttu-id="38207-1186">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1186">tx_mutex_info_get</span></span>
- <span data-ttu-id="38207-1187">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1187">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="38207-1188">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1188">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1189">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1189">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="38207-1190">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="38207-1190">tx_queue_create</span></span>

<span data-ttu-id="38207-1191">메시지 큐 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-1191">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1192">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1192">Prototype</span></span>

```c
UINT tx_queue_create(TX_QUEUE *queue_ptr, CHAR *name_ptr,
                          UINT message_size,
                          VOID *queue_start, ULONG queue_size);
```
### <a name="description"></a><span data-ttu-id="38207-1193">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1193">Description</span></span>

<span data-ttu-id="38207-1194">이 서비스는 일반적으로 스레드 간 통신에 사용되는 메시지 큐를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1194">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="38207-1195">메시지의 총 수는 지정된 메시지 크기와 큐의 총 바이트 수에서 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1195">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1196">큐의 메모리 영역에 지정된 총 바이트 수를 지정된 메시지 크기로 균등하게 나눌 수 없는 경우 메모리 영역의 나머지 바이트는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1196">If the total number of bytes specified in the queue’s memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1197">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1197">Parameters</span></span>

- <span data-ttu-id="38207-1198">**queue_ptr**: 메시지 큐 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1198">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="38207-1199">**name_ptr**: 메시지 큐 이름을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1199">**name_ptr**: Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="38207-1200">**message_size**: 큐에 있는 각 메시지의 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1200">**message_size**: Specifies the size of each message in the queue.</span></span> <span data-ttu-id="38207-1201">메시지 크기는 1개의 32비트 단어부터 16개의 32비트 단어까지 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1201">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="38207-1202">유효한 메시지 크기 옵션은 1에서 16 사이의 숫자 값입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1202">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="38207-1203">**queue_start**: 메시지 큐의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1203">**queue_start**: Starting address of the message queue.</span></span> <span data-ttu-id="38207-1204">시작 주소는 ULONG 데이터 형식의 크기에 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1204">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="38207-1205">**queue_size**: 메시지 큐에 사용할 수 있는 총 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1205">**queue_size**: Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1206">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1206">Return Values</span></span>

- <span data-ttu-id="38207-1207">**TX_SUCCESS**:(0x00) 메시지 큐를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1207">**TX_SUCCESS**: (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="38207-1208">TX_QUEUE_ERROR:(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1208">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="38207-1209">포인터가 NULL이거나 큐가 이미 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1209">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="38207-1210">TX_PTR_ERROR:(0x03) 메시지 큐의 시작 주소가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1210">TX_PTR_ERROR: (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="38207-1211">TX_SIZE_ERROR:(0x05) 메시지 큐의 크기가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1211">TX_SIZE_ERROR: (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="38207-1212">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1212">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1213">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1213">Allowed From</span></span>

<span data-ttu-id="38207-1214">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="38207-1214">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1215">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1215">Preemption Possible</span></span>

<span data-ttu-id="38207-1216">예</span><span class="sxs-lookup"><span data-stu-id="38207-1216">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-1217">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1217">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Create a message queue whose total size is 2000 bytes
   starting at address 0x300000. Each message in this
   queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
            4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
   for storing 125 messages (2000 bytes/ 16 bytes per
   message). */
```
### <a name="see-also"></a><span data-ttu-id="38207-1218">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1218">See Also</span></span>

- <span data-ttu-id="38207-1219">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1219">tx_queue_delete</span></span>
- <span data-ttu-id="38207-1220">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="38207-1220">tx_queue_flush</span></span>
- <span data-ttu-id="38207-1221">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="38207-1221">tx_queue_front_send</span></span>
- <span data-ttu-id="38207-1222">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1222">tx_queue_info_get</span></span>
- <span data-ttu-id="38207-1223">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1223">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="38207-1224">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1224">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1225">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1225">tx_queue_prioritize</span></span>
- <span data-ttu-id="38207-1226">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="38207-1226">tx_queue_receive</span></span>
- <span data-ttu-id="38207-1227">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="38207-1227">tx_queue_send</span></span>
- <span data-ttu-id="38207-1228">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1228">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="38207-1229">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1229">tx_queue_delete</span></span>

<span data-ttu-id="38207-1230">메시지 큐 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-1230">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1231">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1231">Prototype</span></span>

```C
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-1232">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1232">Description</span></span>

<span data-ttu-id="38207-1233">이 서비스는 지정된 메시지 큐를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1233">This service deletes the specified message queue.</span></span> <span data-ttu-id="38207-1234">이 큐의 메시지 기다리는 일시 중단된 모든 스레드는 다시 시작되며 TX_DELETED 반환 상태가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1234">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1235">애플리케이션은 큐를 삭제하기 전에 이 큐에 대한 알림 보내기 콜백이 완료(또는 사용하지 않도록 설정)되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1235">The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue.</span></span> <span data-ttu-id="38207-1236">또한 애플리케이션은 나중에 삭제된 모든 큐를 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1236">In addition, the application must prevent any future use of a deleted queue.</span></span>

<span data-ttu-id="38207-1237">애플리케이션은 또한 이 서비스가 완료된 후 사용할 수 있는 큐와 연결된 메모리 영역을 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1237">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1238">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1238">Parameters</span></span> 

- <span data-ttu-id="38207-1239">**queue_ptr**: 이전에 만든 메시지 큐를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1239">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1240">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1240">Return Values</span></span>

- <span data-ttu-id="38207-1241">**TX_SUCCESS**:(0x00) 메시지 큐를 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1241">**TX_SUCCESS**: (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="38207-1242">TX_QUEUE_ERROR:(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1242">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="38207-1243">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1243">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1244">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1244">Allowed From</span></span>

<span data-ttu-id="38207-1245">스레드</span><span class="sxs-lookup"><span data-stu-id="38207-1245">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1246">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1246">Preemption Possible</span></span>

<span data-ttu-id="38207-1247">예</span><span class="sxs-lookup"><span data-stu-id="38207-1247">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-1248">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1248">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Delete entire message queue. Assume that the queue
   has already been created with a call to
   tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1249">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1249">See Also</span></span>

- <span data-ttu-id="38207-1250">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="38207-1250">tx_queue_create</span></span>
- <span data-ttu-id="38207-1251">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="38207-1251">tx_queue_flush</span></span>
- <span data-ttu-id="38207-1252">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="38207-1252">tx_queue_front_send</span></span>
- <span data-ttu-id="38207-1253">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1253">tx_queue_info_get</span></span>
- <span data-ttu-id="38207-1254">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1254">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="38207-1255">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1255">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1256">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1256">tx_queue_prioritize</span></span>
- <span data-ttu-id="38207-1257">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="38207-1257">tx_queue_receive</span></span>
- <span data-ttu-id="38207-1258">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="38207-1258">tx_queue_send</span></span>
- <span data-ttu-id="38207-1259">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1259">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="38207-1260">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="38207-1260">tx_queue_flush</span></span>

<span data-ttu-id="38207-1261">메시지 큐의 메시지 비우기</span><span class="sxs-lookup"><span data-stu-id="38207-1261">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1262">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1262">Prototype</span></span>

```C
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-1263">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1263">Description</span></span>

<span data-ttu-id="38207-1264">이 서비스는 지정된 메시지 큐에 저장된 모든 메시지를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1264">This service deletes all messages stored in the specified message queue.</span></span> <span data-ttu-id="38207-1265">메시지 큐가 가득 차면 모든 일시 중단된 스레드의 메시지가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1265">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="38207-1266">일시 중단된 각 스레드는 메시지 전송이 성공했음을 나타내는 반환 상태로 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1266">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="38207-1267">큐가 비어 있으면 이 서비스는 아무 작업도 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1267">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1268">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1268">Parameters</span></span> 

- <span data-ttu-id="38207-1269">**queue_ptr**: 이전에 만든 메시지 큐를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1269">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1270">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1270">Return Values</span></span>

- <span data-ttu-id="38207-1271">**TX_SUCCESS**:(0x00) 메시지 큐를 플러시했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1271">**TX_SUCCESS**: (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="38207-1272">TX_QUEUE_ERROR:(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1272">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1273">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1273">Allowed From</span></span>

<span data-ttu-id="38207-1274">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1274">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1275">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1275">Preemption Possible</span></span>

<span data-ttu-id="38207-1276">예</span><span class="sxs-lookup"><span data-stu-id="38207-1276">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-1277">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1277">Example</span></span>

```c
TX_QUEUE     my_queue;
UINT         status;

/* Flush out all pending messages in the specified message
   queue. Assume that the queue has already been created
   with a call to tx_queue_create. */
status =  tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
    empty. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1278">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1278">See Also</span></span>

- <span data-ttu-id="38207-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="38207-1279">tx_queue_create</span></span>
- <span data-ttu-id="38207-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1280">tx_queue_delete</span></span>
- <span data-ttu-id="38207-1281">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="38207-1281">tx_queue_front_send</span></span>
- <span data-ttu-id="38207-1282">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1282">tx_queue_info_get</span></span>
- <span data-ttu-id="38207-1283">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1283">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="38207-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="38207-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="38207-1286">tx_queue_receive</span></span>
- <span data-ttu-id="38207-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="38207-1287">tx_queue_send</span></span>
- <span data-ttu-id="38207-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="38207-1289">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="38207-1289">tx_queue_front_send</span></span>

<span data-ttu-id="38207-1290">메시지를 큐 맨 앞으로 보내기</span><span class="sxs-lookup"><span data-stu-id="38207-1290">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1291">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1291">Prototype</span></span>

```C
UINT tx_queue_front_send(TX_QUEUE *queue_ptr,
                           VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="38207-1292">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1292">Description</span></span>

<span data-ttu-id="38207-1293">이 서비스는 메시지를 지정된 메시지 큐의 맨 앞 위치로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1293">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="38207-1294">메시지는 소스 포인터로 지정된 메모리 영역에서 큐의 맨 앞으로 **복사됩니다**.</span><span class="sxs-lookup"><span data-stu-id="38207-1294">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1295">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1295">Parameters</span></span>

- <span data-ttu-id="38207-1296">**queue_ptr**: 메시지 큐 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1296">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="38207-1297">**source_ptr**: 메시지를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1297">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="38207-1298">**wait_option**: 메시지 큐가 가득 찬 경우의 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1298">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="38207-1299">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1299">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38207-1300">**TX_NO_WAIT**:(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="38207-1300">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="38207-1301">**TX_WAIT_FOREVER**:(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38207-1301">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="38207-1302">시간 제한 값:(0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38207-1302">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="38207-1303">TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1303">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="38207-1304">초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1304">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="38207-1305">TX_WAIT_FOREVER를 선택하면 큐에 공간이 생길 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1305">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="38207-1306">숫자 값(1-0xFFFFFFFE)을 선택하면 큐의 공간을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1306">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1307">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1307">Return Values</span></span>

- <span data-ttu-id="38207-1308">**TX_SUCCESS**:(0x00) 메시지 송신에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1308">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="38207-1309">**TX_DELETED**:(0x01) 스레드가 일시 중단된 동안 메시지 큐가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1309">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="38207-1310">**TX_QUEUE_FULL**:(0x0B) 지정된 대기 시간 중 큐가 가득 찼으므로 서비스에서 메시지를 송신할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1310">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="38207-1311">**TX_WAIT_ABORTED**:(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1311">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="38207-1312">TX_QUEUE_ERROR:(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1312">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="38207-1313">TX_PTR_ERROR:(0x03) 잘못된 메시지 원본 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1313">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="38207-1314">TX_WAIT_ERROR:(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1314">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1315">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1315">Allowed From</span></span>

<span data-ttu-id="38207-1316">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1316">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1317">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1317">Preemption Possible</span></span>

<span data-ttu-id="38207-1318">예</span><span class="sxs-lookup"><span data-stu-id="38207-1318">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-1319">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1319">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG        my_message[4];

/* Send a message to the front of "my_queue." Return
   immediately, regardless of success. This wait
   option is used for calls from initialization, timers,
   and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
            TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
   of the specified queue. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1320">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1320">See Also</span></span>

- <span data-ttu-id="38207-1321">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="38207-1321">tx_queue_create</span></span>
- <span data-ttu-id="38207-1322">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1322">tx_queue_delete</span></span>
- <span data-ttu-id="38207-1323">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="38207-1323">tx_queue_flush</span></span>
- <span data-ttu-id="38207-1324">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1324">tx_queue_info_get</span></span>
- <span data-ttu-id="38207-1325">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1325">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="38207-1326">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1326">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1327">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1327">tx_queue_prioritize</span></span>
- <span data-ttu-id="38207-1328">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="38207-1328">tx_queue_receive</span></span>
- <span data-ttu-id="38207-1329">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="38207-1329">tx_queue_send</span></span>
- <span data-ttu-id="38207-1330">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1330">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="38207-1331">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1331">tx_queue_info_get</span></span>

<span data-ttu-id="38207-1332">큐에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-1332">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1333">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1333">Prototype</span></span>

```C
UINT tx_queue_info_get(TX_QUEUE *queue_ptr, CHAR **name,
        ULONG *enqueued, ULONG *available_storage
        TX_THREAD **first_suspended, ULONG *suspended_count,
        TX_QUEUE **next_queue);
```
### <a name="description"></a><span data-ttu-id="38207-1334">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1334">Description</span></span>

<span data-ttu-id="38207-1335">이 서비스는 지정된 메시지 큐에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1335">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1336">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1336">Parameters</span></span>

- <span data-ttu-id="38207-1337">**queue_ptr**: 이전에 만든 메시지 큐를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1337">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="38207-1338">**name**: 큐 이름에 대한 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1338">**name**: Pointer to destination for the pointer to the queue’s name.</span></span>
- <span data-ttu-id="38207-1339">**enqueued**: 현재 큐에 있는 메시지 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1339">**enqueued**: Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="38207-1340">**available_storage**: 큐에 현재 공간이 있는 메시지 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1340">**available_storage**: Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="38207-1341">**first_suspended**: 이 큐의 일시 중단 목록 맨 처음에 나오는 스레드에 대한 포인터의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1341">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="38207-1342">**suspended_count**: 이 큐에서 현재 일시 중단된 스레드 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1342">**suspended_count**: Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="38207-1343">**next_queue**: 다음에 만든 큐 포인트의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1343">**next_queue**: Pointer to destination for the pointer of the next created queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1344">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1344">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1345">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1345">Return Values</span></span>

- <span data-ttu-id="38207-1346">**TX_SUCCESS**:(0X00) 큐 정보 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1346">**TX_SUCCESS**: (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="38207-1347">TX_QUEUE_ERROR:(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1347">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1348">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1348">Allowed From</span></span>

<span data-ttu-id="38207-1349">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1349">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1350">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1350">Preemption Possible</span></span>

<span data-ttu-id="38207-1351">예</span><span class="sxs-lookup"><span data-stu-id="38207-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-1352">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1352">Example</span></span>

```C
TX_QUEUE     my_queue;
CHAR         *name;
ULONG        enqueued;
ULONG        available_storage;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_QUEUE     *next_queue;
UINT         status;

/* Retrieve information about the previously created
   message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
            &enqueued, &available_storage,
            &first_suspended, &suspended_count,
            &next_queue);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1353">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1353">See Also</span></span>

- <span data-ttu-id="38207-1354">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="38207-1354">tx_queue_create</span></span>
- <span data-ttu-id="38207-1355">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1355">tx_queue_delete</span></span>
- <span data-ttu-id="38207-1356">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="38207-1356">tx_queue_flush</span></span>
- <span data-ttu-id="38207-1357">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="38207-1357">tx_queue_front_send</span></span>
- <span data-ttu-id="38207-1358">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1358">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="38207-1359">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1359">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1360">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1360">tx_queue_prioritize</span></span>
- <span data-ttu-id="38207-1361">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="38207-1361">tx_queue_receive</span></span>
- <span data-ttu-id="38207-1362">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="38207-1362">tx_queue_send</span></span>
- <span data-ttu-id="38207-1363">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1363">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="38207-1364">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1364">tx_queue_performance_info_get</span></span>

<span data-ttu-id="38207-1365">큐 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-1365">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1366">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1366">Prototype</span></span>

```C
UINT  tx_queue_performance_info_get(TX_QUEUE *queue_ptr,
        ULONG *messages_sent, ULONG *messages_received,
        ULONG *empty_suspensions, ULONG *full_suspensions,
        ULONG *full_errors, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="38207-1367">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1367">Description</span></span>

<span data-ttu-id="38207-1368">이 서비스는 지정된 큐에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1368">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1369">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_QUEUE_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1369">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1370">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1370">Parameters</span></span>

- <span data-ttu-id="38207-1371">**queue_ptr**: 이전에 만든 큐를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1371">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="38207-1372">**messages_sent**: 이 큐에서 수행된 송신 요청 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1372">**messages_sent**: Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="38207-1373">**messages_received**: 이 큐에서 수행된 수신 요청 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1373">**messages_received**: Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="38207-1374">**empty_suspensions**: 이 큐에 대한 큐 비우기 일시 중단 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1374">**empty_suspensions**: Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="38207-1375">**full_suspensions**: 이 큐에 대한 큐 채우기 일시 중단 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1375">**full_suspensions**: Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="38207-1376">**full_errors**: 이 큐에 대한 큐 채우기 오류 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1376">**full_errors**: Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="38207-1377">**timeouts**: 이 큐에 대한 스레드 일시 중단 시간 초과 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1377">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1378">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1378">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1379">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1379">Return Values</span></span>

- <span data-ttu-id="38207-1380">**TX_SUCCESS**:(0X00) 큐 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1380">**TX_SUCCESS**: (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="38207-1381">**TX_PTR_ERROR**:(0x03) 잘못된 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1381">**TX_PTR_ERROR**: (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="38207-1382">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1382">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1383">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1383">Allowed From</span></span>

<span data-ttu-id="38207-1384">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1384">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-1385">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1385">Example</span></span>

```C
TX_QUEUE     my_queue;
ULONG        messages_sent;
ULONG        messages_received;
ULONG        empty_suspensions;
ULONG        full_suspensions;
ULONG        full_errors;
ULONG        timeouts;

/* Retrieve performance information on the previously created
   queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1386">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1386">See Also</span></span>

- <span data-ttu-id="38207-1387">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="38207-1387">tx_queue_create</span></span>
- <span data-ttu-id="38207-1388">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1388">tx_queue_delete</span></span>
- <span data-ttu-id="38207-1389">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="38207-1389">tx_queue_flush</span></span>
- <span data-ttu-id="38207-1390">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="38207-1390">tx_queue_front_send</span></span>
- <span data-ttu-id="38207-1391">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1391">tx_queue_info_get</span></span>
- <span data-ttu-id="38207-1392">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1392">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1393">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1393">tx_queue_prioritize</span></span>
- <span data-ttu-id="38207-1394">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="38207-1394">tx_queue_receive</span></span>
- <span data-ttu-id="38207-1395">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="38207-1395">tx_queue_send</span></span>
- <span data-ttu-id="38207-1396">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1396">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="38207-1397">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1397">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="38207-1398">큐 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-1398">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1399">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1399">Prototype</span></span>

```C
UINT  tx_queue_performance_system_info_get(ULONG *messages_sent,
        ULONG *messages_received, ULONG *empty_suspensions,
        ULONG *full_suspensions, ULONG *full_errors,
        ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="38207-1400">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1400">Description</span></span>

<span data-ttu-id="38207-1401">이 서비스는 시스템의 모든 큐에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1401">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1402">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_QUEUE_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1402">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1403">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1403">Parameters</span></span>

- <span data-ttu-id="38207-1404">**messages_sent**: 모든 큐에서 수행된 총 송신 요청 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1404">**messages_sent**: Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="38207-1405">**messages_received**: 모든 큐에서 수행된 총 수신 요청 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1405">**messages_received**: Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="38207-1406">**empty_suspensions**: 모든 큐에 대한 총 큐 비우기 일시 중단 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1406">**empty_suspensions**: Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="38207-1407">**full_suspensions**: 모든 큐에 대한 총 큐 채우기 일시 중단 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1407">**full_suspensions**: Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="38207-1408">**full_errors**: 모든 큐에 대한 총 큐 채우기 오류 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1408">**full_errors**: Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="38207-1409">**timeouts**: 모든 큐에 대한 총 스레드 일시 중단 시간 초과 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1409">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1410">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1410">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1411">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1411">Return Values</span></span>

- <span data-ttu-id="38207-1412">**TX_SUCCESS**:(0X00) 큐 시스템 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1412">**TX_SUCCESS**: (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="38207-1413">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1413">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1414">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1414">Allowed From</span></span>

<span data-ttu-id="38207-1415">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1415">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-1416">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1416">Example</span></span>

```c
ULONG         messages_sent;
ULONG         messages_received;
ULONG         empty_suspensions;
ULONG         full_suspensions;
ULONG         full_errors;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1417">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1417">See Also</span></span>

- <span data-ttu-id="38207-1418">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="38207-1418">tx_queue_create</span></span>
- <span data-ttu-id="38207-1419">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1419">tx_queue_delete</span></span>
- <span data-ttu-id="38207-1420">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="38207-1420">tx_queue_flush</span></span>
- <span data-ttu-id="38207-1421">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="38207-1421">tx_queue_front_send</span></span>
- <span data-ttu-id="38207-1422">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1422">tx_queue_info_get</span></span>
- <span data-ttu-id="38207-1423">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1423">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="38207-1424">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1424">tx_queue_prioritize</span></span>
- <span data-ttu-id="38207-1425">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="38207-1425">tx_queue_receive</span></span>
- <span data-ttu-id="38207-1426">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="38207-1426">tx_queue_send</span></span>
- <span data-ttu-id="38207-1427">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1427">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="38207-1428">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1428">tx_queue_prioritize</span></span>

<span data-ttu-id="38207-1429">큐 일시 중단 목록 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="38207-1429">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1430">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1430">Prototype</span></span>

```C
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="38207-1431">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1431">Description</span></span>

<span data-ttu-id="38207-1432">이 서비스는 이 큐에 있는 메시지에 대해 일시 중단된 최고 우선 순위 스레드(또는 메시지)를 일시 중단 목록 맨 앞에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1432">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span> <span data-ttu-id="38207-1433">다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1433">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1434">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1434">Parameters</span></span> 

- <span data-ttu-id="38207-1435">**queue_ptr**: 이전에 만든 메시지 큐를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1435">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1436">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1436">Return Values</span></span>

- <span data-ttu-id="38207-1437">**TX_SUCCESS**:(0X00) 큐의 우선 순위를 성공적으로 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1437">**TX_SUCCESS**: (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="38207-1438">TX_QUEUE_ERROR:(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1438">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1439">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1439">Allowed From</span></span>

<span data-ttu-id="38207-1440">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1440">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1441">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1441">Preemption Possible</span></span>

<span data-ttu-id="38207-1442">예</span><span class="sxs-lookup"><span data-stu-id="38207-1442">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-1443">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1443">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_queue_send or tx_queue_front_send call made
   to this queue will wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1444">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1444">See Also</span></span>

- <span data-ttu-id="38207-1445">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="38207-1445">tx_queue_create</span></span>
- <span data-ttu-id="38207-1446">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1446">tx_queue_delete</span></span>
- <span data-ttu-id="38207-1447">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="38207-1447">tx_queue_flush</span></span>
- <span data-ttu-id="38207-1448">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="38207-1448">tx_queue_front_send</span></span>
- <span data-ttu-id="38207-1449">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1449">tx_queue_info_get</span></span>
- <span data-ttu-id="38207-1450">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1450">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="38207-1451">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1451">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1452">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="38207-1452">tx_queue_receive</span></span>
- <span data-ttu-id="38207-1453">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="38207-1453">tx_queue_send</span></span>
- <span data-ttu-id="38207-1454">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1454">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="38207-1455">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="38207-1455">tx_queue_receive</span></span>

<span data-ttu-id="38207-1456">메시지 큐에서 메시지 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-1456">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1457">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1457">Prototype</span></span>

```C
UINT tx_queue_receive(TX_QUEUE *queue_ptr,
                          VOID *destination_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="38207-1458">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1458">Description</span></span>

<span data-ttu-id="38207-1459">이 서비스는 지정된 메시지 큐에서 메시지를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1459">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="38207-1460">검색된 메시지는 큐로부터 대상 포인터로 지정된 메모리 영역으로 **복사됩니다**.</span><span class="sxs-lookup"><span data-stu-id="38207-1460">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="38207-1461">그런 후에 메시지가 큐에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1461">That message is then removed from the queue.</span></span>

> [!WARNING]
> <span data-ttu-id="38207-1462">지정된 대상 메모리 영역은 메시지를 저장할 수 있을 만큼 충분히 커야 합니다. 즉, **destination_ptr** 로 가리키는 메시지 대상은 적어도 이 큐의 메시지 크기 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1462">The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by **destination_ptr** must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="38207-1463">그렇지 않고 대상이 충분히 크지 않은 경우 다음 메모리 영역에서 메모리 손상이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1463">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1464">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1464">Parameters</span></span>

- <span data-ttu-id="38207-1465">**queue_ptr**: 이전에 만든 메시지 큐를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1465">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="38207-1466">**destination_ptr**: 메시지를 복사해 넣을 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1466">**destination_ptr**: Location of where to copy the message.</span></span>
- <span data-ttu-id="38207-1467">**wait_option**: 메시지 큐가 비어 있는 경우의 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1467">**wait_option**: Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="38207-1468">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1468">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38207-1469">**TX_NO_WAIT**:(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="38207-1469">**TX_NO_WAIT**: (0x00000000)</span></span> 
    - <span data-ttu-id="38207-1470">**TX_WAIT_FOREVER**:(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38207-1470">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span> 
    - <span data-ttu-id="38207-1471">시간 제한 값:(0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38207-1471">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="38207-1472">TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1472">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="38207-1473">초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1473">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="38207-1474">TX_WAIT_FOREVER를 선택하면 메시지를 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1474">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>

    <span data-ttu-id="38207-1475">숫자 값(1-0xFFFFFFFE)을 선택하면 메시지를 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1475">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1476">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1476">Return Values</span></span>

- <span data-ttu-id="38207-1477">**TX_SUCCESS**:(0x00) 메시지를 성공적으로 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1477">**TX_SUCCESS**: (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="38207-1478">**TX_DELETED**:(0x01) 스레드가 일시 중단된 동안 메시지 큐가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1478">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="38207-1479">**TX_QUEUE_EMPTY**:(0X0A) 지정된 대기 시간 동안 큐가 비어 있기 때문에 서비스에서 메시지를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1479">**TX_QUEUE_EMPTY**: (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="38207-1480">**TX_WAIT_ABORTED**:(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1480">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="38207-1481">TX_QUEUE_ERROR:(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1481">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="38207-1482">TX_PTR_ERROR:(0x03) 메시지에 대한 대상 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1482">TX_PTR_ERROR: (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="38207-1483">TX_WAIT_ERROR:(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1483">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1484">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1484">Allowed From</span></span>

<span data-ttu-id="38207-1485">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1485">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1486">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1486">Preemption Possible</span></span>

<span data-ttu-id="38207-1487">예</span><span class="sxs-lookup"><span data-stu-id="38207-1487">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-1488">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1488">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
   empty, suspend until a message is present. Note that
   this suspension is only possible from application
   threads. */
status =  tx_queue_receive(&my_queue, my_message,
                          TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
   "my_message." */
```
### <a name="see-also"></a><span data-ttu-id="38207-1489">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1489">See Also</span></span>

- <span data-ttu-id="38207-1490">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="38207-1490">tx_queue_create</span></span>
- <span data-ttu-id="38207-1491">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1491">tx_queue_delete</span></span>
- <span data-ttu-id="38207-1492">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="38207-1492">tx_queue_flush</span></span>
- <span data-ttu-id="38207-1493">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="38207-1493">tx_queue_front_send</span></span>
- <span data-ttu-id="38207-1494">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1494">tx_queue_info_get</span></span>
- <span data-ttu-id="38207-1495">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1495">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="38207-1496">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1496">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1497">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1497">tx_queue_prioritize</span></span>
- <span data-ttu-id="38207-1498">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="38207-1498">tx_queue_send</span></span>
- <span data-ttu-id="38207-1499">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1499">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="38207-1500">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="38207-1500">tx_queue_send</span></span>

<span data-ttu-id="38207-1501">메시지 큐로 메시지 보내기</span><span class="sxs-lookup"><span data-stu-id="38207-1501">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1502">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1502">Prototype</span></span>

```C
UINT tx_queue_send(TX_QUEUE *queue_ptr,
                          VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="38207-1503">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1503">Description</span></span>

<span data-ttu-id="38207-1504">이 서비스는 메시지를 지정된 메시지 큐로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1504">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="38207-1505">보낸 메시지는 소스 포인터로 지정된 메모리 영역에서 큐로 **복사됩니다**.</span><span class="sxs-lookup"><span data-stu-id="38207-1505">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1506">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1506">Parameters</span></span>

- <span data-ttu-id="38207-1507">**queue_ptr**: 이전에 만든 메시지 큐를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1507">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="38207-1508">**source_ptr**: 메시지를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1508">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="38207-1509">**wait_option**: 메시지 큐가 가득 찬 경우의 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1509">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="38207-1510">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1510">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38207-1511">**TX_NO_WAIT**:(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="38207-1511">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="38207-1512">**TX_WAIT_FOREVER**:(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38207-1512">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="38207-1513">시간 제한 값:(0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38207-1513">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="38207-1514">TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1514">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="38207-1515">초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1515">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="38207-1516">TX_WAIT_FOREVER를 선택하면 큐에 공간이 생길 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1516">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="38207-1517">숫자 값(1-0xFFFFFFFE)을 선택하면 큐의 공간을 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1517">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1518">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1518">Return Values</span></span>

- <span data-ttu-id="38207-1519">**TX_SUCCESS**:(0x00) 메시지 송신에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1519">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="38207-1520">**TX_DELETED**:(0x01) 스레드가 일시 중단된 동안 메시지 큐가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1520">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="38207-1521">**TX_QUEUE_FULL**:(0x0B) 지정된 대기 시간 중 큐가 가득 찼으므로 서비스에서 메시지를 송신할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1521">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="38207-1522">**TX_WAIT_ABORTED**:(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1522">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="38207-1523">TX_QUEUE_ERROR:(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1523">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="38207-1524">TX_PTR_ERROR:(0x03) 잘못된 메시지 원본 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1524">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="38207-1525">TX_WAIT_ERROR:(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1525">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1526">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1526">Allowed From</span></span>

<span data-ttu-id="38207-1527">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1527">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1528">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1528">Preemption Possible</span></span>

<span data-ttu-id="38207-1529">예</span><span class="sxs-lookup"><span data-stu-id="38207-1529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-1530">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1530">Example</span></span>

```C
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
   regardless of success. This wait option is used for
   calls from initialization, timers, and ISRs. */
status =  tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
   queue. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1531">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1531">See Also</span></span>

- <span data-ttu-id="38207-1532">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="38207-1532">tx_queue_create</span></span>
- <span data-ttu-id="38207-1533">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1533">tx_queue_delete</span></span>
- <span data-ttu-id="38207-1534">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="38207-1534">tx_queue_flush</span></span>
- <span data-ttu-id="38207-1535">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="38207-1535">tx_queue_front_send</span></span>
- <span data-ttu-id="38207-1536">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1536">tx_queue_info_get</span></span>
- <span data-ttu-id="38207-1537">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1537">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="38207-1538">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1538">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1539">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1539">tx_queue_prioritize</span></span>
- <span data-ttu-id="38207-1540">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="38207-1540">tx_queue_receive</span></span>
- <span data-ttu-id="38207-1541">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1541">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="38207-1542">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1542">tx_queue_send_notify</span></span> 

<span data-ttu-id="38207-1543">메시지가 큐에 전송될 때 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="38207-1543">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1544">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1544">Prototype</span></span>

```C
UINT  tx_queue_send_notify(TX_QUEUE *queue_ptr,
        VOID (*queue_send_notify)(TX_QUEUE *));
```
### <a name="description"></a><span data-ttu-id="38207-1545">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1545">Description</span></span>

<span data-ttu-id="38207-1546">이 서비스는 지정된 큐에 메시지를 보낼 때마다 호출되는 알림 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1546">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="38207-1547">알림 콜백의 처리는 애플리케이션에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1547">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="38207-1548">애플리케이션의 큐 보내기 알림 콜백은 일시 중단 옵션을 사용하여 ThreadX SMP API를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1548">The application’s queue send notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1549">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1549">Parameters</span></span> 

- <span data-ttu-id="38207-1550">**queue_ptr**: 이전에 만든 큐를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1550">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="38207-1551">**queue_send_notify**: 애플리케이션의 큐 보내기 알림 함수를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1551">**queue_send_notify**: Pointer to application’s queue send notification function.</span></span> <span data-ttu-id="38207-1552">이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1552">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1553">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1553">Return Values</span></span>

- <span data-ttu-id="38207-1554">**TX_SUCCESS**:(0x00) 큐 보내기 알림을 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1554">**TX_SUCCESS**: (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="38207-1555">TX_QUEUE_ERROR:(0x09) 잘못된 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1555">TX_QUEUE_ERROR: (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="38207-1556">TX_FEATURE_NOT_ENABLED:(0xFF) 시스템이 알림 기능을 사용하지 않도록 설정하여 컴파일되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1556">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1557">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1557">Allowed From</span></span>

<span data-ttu-id="38207-1558">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1558">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-1559">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1559">Example</span></span>

```C
TX_QUEUE         my_queue;

/* Register the "my_queue_send_notify" function for monitoring
   messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
   successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
/* A message was just sent to this queue! */
}
```
### <a name="see-also"></a><span data-ttu-id="38207-1560">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1560">See Also</span></span>

- <span data-ttu-id="38207-1561">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="38207-1561">tx_queue_create</span></span>
- <span data-ttu-id="38207-1562">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1562">tx_queue_delete</span></span>
- <span data-ttu-id="38207-1563">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="38207-1563">tx_queue_flush</span></span>
- <span data-ttu-id="38207-1564">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="38207-1564">tx_queue_front_send</span></span>
- <span data-ttu-id="38207-1565">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1565">tx_queue_info_get</span></span>
- <span data-ttu-id="38207-1566">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1566">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="38207-1567">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1567">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1568">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1568">tx_queue_prioritize</span></span>
- <span data-ttu-id="38207-1569">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="38207-1569">tx_queue_receive</span></span>
- <span data-ttu-id="38207-1570">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="38207-1570">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="38207-1571">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="38207-1571">tx_semaphore_ceiling_put</span></span> 

<span data-ttu-id="38207-1572">상한을 지정하여 계산 세마포에 인스턴스 배치</span><span class="sxs-lookup"><span data-stu-id="38207-1572">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1573">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1573">Prototype</span></span>

```C
UINT  tx_semaphore_ceiling_put(TX_SEMAPHORE *semaphore_ptr,
        ULONG ceiling);
```
### <a name="description"></a><span data-ttu-id="38207-1574">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1574">Description</span></span>

<span data-ttu-id="38207-1575">이 서비스는 지정된 계산 세마포에 인스턴스를 배치합니다. 실제로는 계산 세마포가 1씩 증분됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1575">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="38207-1576">계산 세마포의 현재 값이 지정된 상한보다 크거나 같은 경우 인스턴스는 추가되지 않으며 TX_CEILING_EXCEEDED 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1576">If the counting semaphore’s current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1577">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1577">Parameters</span></span> 

- <span data-ttu-id="38207-1578">**semaphore_ptr**: 이전에 만든 세마포를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1578">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="38207-1579">**ceiling**: 세마포에 대해 허용되는 최대 제한입니다(유효한 값 범위는 1에서 0xFFFFFFFF임).</span><span class="sxs-lookup"><span data-stu-id="38207-1579">**ceiling**: Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1580">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1580">Return Values</span></span>

- <span data-ttu-id="38207-1581">**TX_SUCCESS**:(0X00) 세마포 상한을 적용했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1581">**TX_SUCCESS**: (0x00) Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="38207-1582">**TX_CEILING_EXCEEDED**:(0X21) 추가 요청이 상한을 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1582">**TX_CEILING_EXCEEDED**: (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="38207-1583">TX_INVALID_CEILING:(0x22) 상한으로 잘못된 0 값을 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1583">TX_INVALID_CEILING: (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="38207-1584">TX_SEMAPHORE_ERROR:(0x0C) 잘못된 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1584">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1585">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1585">Allowed From</span></span>

<span data-ttu-id="38207-1586">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1586">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-1587">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1587">Example</span></span>

```c
TX_SEMAPHORE     my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
   that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
```
### <a name="see-also"></a><span data-ttu-id="38207-1588">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1588">See Also</span></span>

- <span data-ttu-id="38207-1589">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="38207-1589">tx_semaphore_create</span></span>
- <span data-ttu-id="38207-1590">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1590">tx_semaphore_delete</span></span>
- <span data-ttu-id="38207-1591">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="38207-1591">tx_semaphore_get</span></span>
- <span data-ttu-id="38207-1592">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1592">tx_semaphore_info_get</span></span>
- <span data-ttu-id="38207-1593">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1593">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="38207-1594">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1594">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1595">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1595">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="38207-1596">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="38207-1596">tx_semaphore_put</span></span>
- <span data-ttu-id="38207-1597">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1597">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="38207-1598">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="38207-1598">tx_semaphore_create</span></span>

<span data-ttu-id="38207-1599">계산 세마포 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-1599">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1600">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1600">Prototype</span></span>

```C
UINT tx_semaphore_create(TX_SEMAPHORE *semaphore_ptr,
                           CHAR *name_ptr, ULONG initial_count);
```
### <a name="description"></a><span data-ttu-id="38207-1601">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1601">Description</span></span>

<span data-ttu-id="38207-1602">이 서비스는 스레드 간 동기화에 대한 계산 세마포를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1602">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="38207-1603">초기 세마포 수는 입력 매개 변수로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1603">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1604">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1604">Parameters</span></span> 

- <span data-ttu-id="38207-1605">**semaphore_ptr**: 세마포 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1605">**semaphore_ptr**: Pointer to a semaphore control block.</span></span> 
- <span data-ttu-id="38207-1606">**name_ptr**: 세마포 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1606">**name_ptr**: Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="38207-1607">**initial_count**: 이 세마포에 대한 초기 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1607">**initial_count**: Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="38207-1608">올바른 값의 범위는 0x00000000부터 0xFFFFFFFF까지입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1608">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1609">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1609">Return Values</span></span>

- <span data-ttu-id="38207-1610">**TX_SUCCESS**:(0X00) 성공적으로 세마포를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1610">**TX_SUCCESS**: (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="38207-1611">TX_SEMAPHORE_ERROR:(0x0C) 잘못된 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1611">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="38207-1612">포인터가 NULL이거나 세마포가 이미 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1612">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="38207-1613">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1613">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1614">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1614">Allowed From</span></span>

<span data-ttu-id="38207-1615">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="38207-1615">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1616">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1616">Preemption Possible</span></span>

<span data-ttu-id="38207-1617">예</span><span class="sxs-lookup"><span data-stu-id="38207-1617">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-1618">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1618">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Create a counting semaphore whose initial value is 1.
   This is typically the technique used to make a binary
   semaphore. Binary semaphores are used to provide
   protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
            "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
   use. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1619">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1619">See Also</span></span>

- <span data-ttu-id="38207-1620">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="38207-1620">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="38207-1621">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1621">tx_semaphore_delete</span></span>
- <span data-ttu-id="38207-1622">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="38207-1622">tx_semaphore_get</span></span>
- <span data-ttu-id="38207-1623">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1623">tx_semaphore_info_get</span></span>
- <span data-ttu-id="38207-1624">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1624">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="38207-1625">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1625">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1626">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1626">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="38207-1627">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="38207-1627">tx_semaphore_put</span></span>
- <span data-ttu-id="38207-1628">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1628">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="38207-1629">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1629">tx_semaphore_delete</span></span>

<span data-ttu-id="38207-1630">계산 세마포 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-1630">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1631">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1631">Prototype</span></span>

```C
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-1632">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1632">Description</span></span>

<span data-ttu-id="38207-1633">이 서비스는 지정된 계산 세마포를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1633">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="38207-1634">세마포 인스턴스 대기를 일시 중단한 모든 스레드가 다시 시작되고 TX_DELETED 반환 상태가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1634">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1635">애플리케이션은 세마포를 삭제하기 전에 이 세마포에 대한 알림 추가 콜백이 완료(또는 사용하지 않도록 설정)되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1635">The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore.</span></span> <span data-ttu-id="38207-1636">또한 애플리케이션은 나중에 삭제된 세마포를 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1636">In addition, the application must prevent all future use of a deleted semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1637">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1637">Parameters</span></span> 

- <span data-ttu-id="38207-1638">**semaphore_ptr**: 이전에 만든 세마포를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1638">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1639">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1639">Return Values</span></span>

- <span data-ttu-id="38207-1640">**TX_SUCCESS**:(0x00) 세마포 삭제를 성공적으로 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1640">**TX_SUCCESS**: (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="38207-1641">TX_SEMAPHORE_ERROR:(0x0C) 잘못된 가산 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1641">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="38207-1642">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1642">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1643">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1643">Allowed From</span></span>

<span data-ttu-id="38207-1644">스레드</span><span class="sxs-lookup"><span data-stu-id="38207-1644">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1645">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1645">Preemption Possible</span></span>

<span data-ttu-id="38207-1646">예</span><span class="sxs-lookup"><span data-stu-id="38207-1646">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-1647">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1647">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Delete counting semaphore. Assume that the counting
   semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1648">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1648">See Also</span></span>

- <span data-ttu-id="38207-1649">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="38207-1649">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="38207-1650">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="38207-1650">tx_semaphore_create</span></span>
- <span data-ttu-id="38207-1651">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="38207-1651">tx_semaphore_get</span></span>
- <span data-ttu-id="38207-1652">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1652">tx_semaphore_info_get</span></span>
- <span data-ttu-id="38207-1653">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1653">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="38207-1654">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1654">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1655">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1655">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="38207-1656">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="38207-1656">tx_semaphore_put</span></span>
- <span data-ttu-id="38207-1657">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1657">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="38207-1658">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="38207-1658">tx_semaphore_get</span></span>

<span data-ttu-id="38207-1659">계산 세마포에서 인스턴스 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-1659">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1660">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1660">Prototype</span></span>

```C
UINT tx_semaphore_get(TX_SEMAPHORE *semaphore_ptr,
                          ULONG wait_option)
```
### <a name="description"></a><span data-ttu-id="38207-1661">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1661">Description</span></span>

<span data-ttu-id="38207-1662">이 서비스는 지정된 계산 세마포에서 인스턴스(단일 개수)를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1662">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="38207-1663">따라서 지정된 세마포의 수가 1씩 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1663">As a result, the specified semaphore’s count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1664">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1664">Parameters</span></span>

- <span data-ttu-id="38207-1665">**semaphore_ptr**: 이전에 만든 계산 세마포를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1665">**semaphore_ptr**: Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="38207-1666">**wait_option**: 사용 가능한 세마포 인스턴스가 없는 경우(예: 세마포 수가 0임) 서비스가 동작하는 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1666">**wait_option**: Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="38207-1667">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1667">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="38207-1668">**TX_NO_WAIT**:(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="38207-1668">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="38207-1669">**TX_WAIT_FOREVER**:(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="38207-1669">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="38207-1670">시간 제한 값:(0x00000001~0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="38207-1670">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="38207-1671">TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1671">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="38207-1672">*초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유효한 유일한 옵션입니다.*</span><span class="sxs-lookup"><span data-stu-id="38207-1672">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="38207-1673">TX_WAIT_FOREVER를 선택하면 세마포 인스턴스를 사용할 수 있게 될 때까지 호출 스레드가 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1673">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span> 

    <span data-ttu-id="38207-1674">숫자 값(1-0xFFFFFFFE)을 선택하면 세마포 인스턴스를 기다리는 동안 일시 중단됨 상태로 유지되는 최대 타이머 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1674">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1675">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1675">Return Values</span></span>

- <span data-ttu-id="38207-1676">**TX_SUCCESS**:(0x00) 세마포 인스턴스를 성공적으로 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1676">**TX_SUCCESS**: (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="38207-1677">**TX_DELETED**:(0x01) 스레드가 일시 중단된 동안 계산 세마포가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1677">**TX_DELETED**: (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="38207-1678">**TX_NO_INSTANCE**:(0X0D) 서비스가 계산 세마포 인스턴스를 검색할 수 없습니다(지정된 대기 시간 내에 세마포 수가 0임).</span><span class="sxs-lookup"><span data-stu-id="38207-1678">**TX_NO_INSTANCE**: (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="38207-1679">**TX_WAIT_ABORTED**:(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1679">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="38207-1680">TX_SEMAPHORE_ERROR:(0x0C) 잘못된 가산 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1680">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="38207-1681">TX_WAIT_ERROR:(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1681">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1682">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1682">Allowed From</span></span>

<span data-ttu-id="38207-1683">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1683">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1684">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1684">Preemption Possible</span></span>

<span data-ttu-id="38207-1685">예</span><span class="sxs-lookup"><span data-stu-id="38207-1685">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-1686">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1686">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Get a semaphore instance from the semaphore
   "my_semaphore." If the semaphore count is zero,
   suspend until an instance becomes available.
   Note that this suspension is only possible from
   application threads. */
status =  tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
   an instance of the semaphore. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1687">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1687">See Also</span></span>

- <span data-ttu-id="38207-1688">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="38207-1688">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="38207-1689">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="38207-1689">tx_semaphore_create</span></span>
- <span data-ttu-id="38207-1690">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1690">tx_semahore_delete</span></span>
- <span data-ttu-id="38207-1691">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1691">tx_semaphore_info_get</span></span>
- <span data-ttu-id="38207-1692">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1692">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="38207-1693">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1693">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="38207-1694">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="38207-1694">tx_semaphore_put</span></span>
- <span data-ttu-id="38207-1695">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1695">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="38207-1696">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1696">tx_semaphore_info_get</span></span>

<span data-ttu-id="38207-1697">세마포에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-1697">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1698">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1698">Prototype</span></span>

```C
UINT tx_semaphore_info_get(TX_SEMAPHORE *semaphore_ptr,
                          CHAR **name, ULONG *current_value,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_SEMAPHORE **next_semaphore)
```
### <a name="description"></a><span data-ttu-id="38207-1699">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1699">Description</span></span>

<span data-ttu-id="38207-1700">이 서비스는 지정된 세마포에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1700">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1701">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1701">Parameters</span></span>

- <span data-ttu-id="38207-1702">**semaphore_ptr**: 세마포 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1702">**semaphore_ptr**: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="38207-1703">**name**: 세마포 이름에 대한 포인터의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1703">**name**: Pointer to destination for the pointer to the semaphore’s name.</span></span>
- <span data-ttu-id="38207-1704">**current_value**: 현재 세마포 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1704">**current_value**: Pointer to destination for the current semaphore’s count.</span></span>
- <span data-ttu-id="38207-1705">**first_suspended**: 이 세마포의 일시 중단 목록 맨 처음에 나오는 스레드에 대한 포인터의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1705">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="38207-1706">**suspended_count**: 이 세마포에서 현재 일시 중단된 스레드 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1706">**suspended_count**: Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="38207-1707">**next_semaphore**: 다음에 생성된 세마포의 포인터의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1707">**next_semaphore**: Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1708">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1708">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1709">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1709">Return Values</span></span>

- <span data-ttu-id="38207-1710">**NX_SUCCESS**:(0x00) 세마포 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1710">**TX_SUCCESS**: (0x00) Successful semaphore information retrieval.</span></span>
- <span data-ttu-id="38207-1711">TX_SEMAPHORE_ERROR:(0x0C) 잘못된 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1711">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1712">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1712">Allowed From</span></span>

<span data-ttu-id="38207-1713">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1713">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1714">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1714">Preemption Possible</span></span>

<span data-ttu-id="38207-1715">예</span><span class="sxs-lookup"><span data-stu-id="38207-1715">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-1716">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1716">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
CHAR         *name;
ULONG        current_value;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT         status;

/* Retrieve information about the previously created
   semaphore "my_semaphore." */
status =  tx_semaphore_info_get(&my_semaphore, &name,
                      &current_value,
                      &first_suspended, &suspended_count,
                      &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1717">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1717">See Also</span></span>

- <span data-ttu-id="38207-1718">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="38207-1718">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="38207-1719">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="38207-1719">tx_semaphore_create</span></span>
- <span data-ttu-id="38207-1720">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1720">tx_semaphore_delete</span></span>
- <span data-ttu-id="38207-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="38207-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="38207-1722">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1722">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="38207-1723">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1723">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1724">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1724">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="38207-1725">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="38207-1725">tx_semaphore_put</span></span>
- <span data-ttu-id="38207-1726">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1726">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="38207-1727">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1727">tx_semaphore_performance_info_get</span></span> 

<span data-ttu-id="38207-1728">세마포 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-1728">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1729">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1729">Prototype</span></span>

```C
UINT  tx_semaphore_performance_info_get(TX_SEMAPHORE *semaphore_ptr,
        ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="38207-1730">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1730">Description</span></span>

<span data-ttu-id="38207-1731">이 서비스는 지정된 세마포에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1731">This service retrieves performance information about the specified semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="38207-1732">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** 로 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1732">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1733">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1733">Parameters</span></span>

- <span data-ttu-id="38207-1734">**semaphore_ptr**: 이전에 만든 세마포를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1734">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="38207-1735">**puts** 이 세마포에서 수행된 요청 수행 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1735">**puts**: Pointer to destination for the number of put requests performed on this semaphore.</span></span>
- <span data-ttu-id="38207-1736">**gets** 이 세마포에서 수행된 요청 가져오기 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1736">**gets**: Pointer to destination for the number of get requests performed on this semaphore.</span></span>
- <span data-ttu-id="38207-1737">**suspensions**: 이 세마포에 대한 스레드 일시 중단 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1737">**suspensions**: Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
- <span data-ttu-id="38207-1738">**timeouts**: 이 세마포에 대한 스레드 일시 중단 시간 초과 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1738">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1739">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1739">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1740">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1740">Return Values</span></span>

- <span data-ttu-id="38207-1741">**TX_SUCCESS**:(0X00) 세마포 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1741">**TX_SUCCESS**: (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="38207-1742">**TX_PTR_ERROR**:(0x03) 잘못된 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1742">**TX_PTR_ERROR**: (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="38207-1743">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1743">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1744">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1744">Allowed From</span></span>

<span data-ttu-id="38207-1745">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1745">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-1746">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1746">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
ULONG            puts;
ULONG            gets;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created
   semaphore. */
status =  tx_semaphore_performance_info_get(&my_semaphore, &puts,
               &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1747">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1747">See Also</span></span>

- <span data-ttu-id="38207-1748">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="38207-1748">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="38207-1749">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="38207-1749">tx_semaphore_create</span></span>
- <span data-ttu-id="38207-1750">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1750">tx_semaphore_delete</span></span>
- <span data-ttu-id="38207-1751">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="38207-1751">tx_semaphore_get</span></span>
- <span data-ttu-id="38207-1752">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1752">tx_semaphore_info_get</span></span>
- <span data-ttu-id="38207-1753">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1753">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1754">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1754">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="38207-1755">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="38207-1755">tx_semaphore_put</span></span>
- <span data-ttu-id="38207-1756">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1756">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="38207-1757">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1757">tx_semaphore_performance_system_info_get</span></span> 

<span data-ttu-id="38207-1758">세마포 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-1758">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1759">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1759">Prototype</span></span>

```C
UINT tx_semaphore_performance_system_info_get(ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="38207-1760">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1760">Description</span></span>

<span data-ttu-id="38207-1761">이 서비스는 시스템의 모든 세마포에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1761">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1762">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** 로 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1762">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1763">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1763">Parameters</span></span>

- <span data-ttu-id="38207-1764">**puts** 모든 세마포에서 수행된 총 요청 수행 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1764">**puts**: Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="38207-1765">**gets** 모든 세마포에서 수행된 총 요청 가져오기 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1765">**gets**: Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="38207-1766">**suspensions**: 모든 세마포에 대한 총 스레드 일시 중단 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1766">**suspensions**: Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="38207-1767">**timeouts**: 모든 세마포에 대한 총 스레드 일시 중단 시간 초과 수의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1767">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1768">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1768">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1769">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1769">Return Values</span></span>

- <span data-ttu-id="38207-1770">TX_SUCCESS:(0X00) 세마포 시스템 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1770">TX_SUCCESS: (0x00) Successful semaphore system performance get.</span></span>
- <span data-ttu-id="38207-1771">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1771">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1772">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1772">Allowed From</span></span>

<span data-ttu-id="38207-1773">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1773">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-1774">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1774">Example</span></span>

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
               &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1775">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1775">See Also</span></span>

- <span data-ttu-id="38207-1776">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="38207-1776">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="38207-1777">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="38207-1777">tx_semaphore_create</span></span>
- <span data-ttu-id="38207-1778">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1778">tx_semaphore_delete</span></span>
- <span data-ttu-id="38207-1779">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="38207-1779">tx_semaphore_get</span></span>
- <span data-ttu-id="38207-1780">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1780">tx_semaphore_info_get</span></span>
- <span data-ttu-id="38207-1781">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1781">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="38207-1782">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1782">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="38207-1783">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="38207-1783">tx_semaphore_put</span></span>
- <span data-ttu-id="38207-1784">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1784">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="38207-1785">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1785">tx_semaphore_prioritize</span></span>

<span data-ttu-id="38207-1786">세마포 일시 중단 목록 우선 순위 지정</span><span class="sxs-lookup"><span data-stu-id="38207-1786">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1787">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1787">Prototype</span></span>

```C
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-1788">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1788">Description</span></span>

<span data-ttu-id="38207-1789">이 서비스는 세마포 인스턴스에 대해 일시 중단된 최고 우선 순위 스레드를 일시 중단 목록 맨 앞에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1789">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="38207-1790">다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1790">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1791">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1791">Parameters</span></span> 

- <span data-ttu-id="38207-1792">**semaphore_ptr**: 이전에 만든 세마포를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1792">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1793">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1793">Return Values</span></span>

- <span data-ttu-id="38207-1794">**TX_SUCCESS**:(0X00) 세마포 우선 순위를 성공적으로 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1794">**TX_SUCCESS**: (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="38207-1795">TX_SEMAPHORE_ERROR:(0x0C) 잘못된 가산 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1795">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1796">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1796">Allowed From</span></span>

<span data-ttu-id="38207-1797">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1797">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1798">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1798">Preemption Possible</span></span>

<span data-ttu-id="38207-1799">예</span><span class="sxs-lookup"><span data-stu-id="38207-1799">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-1800">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1800">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next instance of this semaphore. */
status =  tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_semaphore_put call made to this semaphore will
   wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1801">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1801">See Also</span></span>

- <span data-ttu-id="38207-1802">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="38207-1802">tx_semaphore_create</span></span>
- <span data-ttu-id="38207-1803">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1803">tx_semaphore_delete</span></span>
- <span data-ttu-id="38207-1804">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="38207-1804">tx_semaphore_get</span></span>
- <span data-ttu-id="38207-1805">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1805">tx_semaphore_info_get</span></span>
- <span data-ttu-id="38207-1806">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="38207-1806">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="38207-1807">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="38207-1807">tx_semaphore_put</span></span>

<span data-ttu-id="38207-1808">계산 세마포에 인스턴스 배치</span><span class="sxs-lookup"><span data-stu-id="38207-1808">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1809">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1809">Prototype</span></span>

```C
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-1810">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1810">Description</span></span>

<span data-ttu-id="38207-1811">이 서비스는 지정된 계산 세마포에 인스턴스를 배치합니다. 실제로는 계산 세마포가 1씩 증분됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1811">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1812">세마포가 모두 1(OxFFFFFFFF)인 경우 이 서비스를 호출하면 새 추가 작업이 있으면 세마포가 0으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1812">If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1813">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1813">Parameters</span></span>

- <span data-ttu-id="38207-1814">**semaphore_ptr**: 이전에 만든 가산 세마포 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1814">**semaphore_ptr**: Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1815">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1815">Return Values</span></span>

- <span data-ttu-id="38207-1816">**TX_SUCCESS**:(0X00) 세마포를 성공적으로 배치했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1816">**TX_SUCCESS**: (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="38207-1817">TX_SEMAPHORE_ERROR:(0x0C) 잘못된 가산 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1817">TX_SEMAPHORE_ERROR: (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1818">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1818">Allowed From</span></span>

<span data-ttu-id="38207-1819">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1819">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1820">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1820">Preemption Possible</span></span>

<span data-ttu-id="38207-1821">예</span><span class="sxs-lookup"><span data-stu-id="38207-1821">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-1822">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1822">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
UINT             status;

/* Increment the counting semaphore "my_semaphore." */
status =  tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
   been incremented. Of course, if a thread was waiting,
   it was given the semaphore instance and resumed. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1823">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1823">See Also</span></span>

- <span data-ttu-id="38207-1824">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="38207-1824">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="38207-1825">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="38207-1825">tx_semaphore_create</span></span>
- <span data-ttu-id="38207-1826">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1826">tx_semaphore_delete</span></span>
- <span data-ttu-id="38207-1827">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1827">tx_semaphore_info_get</span></span>
- <span data-ttu-id="38207-1828">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1828">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="38207-1829">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1829">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1830">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1830">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="38207-1831">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="38207-1831">tx_semaphore_get</span></span>
- <span data-ttu-id="38207-1832">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1832">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="38207-1833">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1833">tx_semaphore_put_notify</span></span>

<span data-ttu-id="38207-1834">세마포가 배치될 때 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="38207-1834">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1835">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1835">Prototype</span></span>

```C
UINT  tx_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr,
        VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```
### <a name="description"></a><span data-ttu-id="38207-1836">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1836">Description</span></span>

<span data-ttu-id="38207-1837">이 서비스는 지정된 세마포를 배치할 때마다 호출되는 알림 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1837">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="38207-1838">알림 콜백의 처리는 애플리케이션에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1838">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="38207-1839">애플리케이션의 세마포 알림 콜백은 일시 중단 옵션을 사용하여 ThreadX SMP API를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1839">The application’s semaphore notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1840">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1840">Parameters</span></span> 

- <span data-ttu-id="38207-1841">**semaphore_ptr**: 이전에 만든 세마포를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1841">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="38207-1842">**semaphore_put_notify**: 애플리케이션의 세마포 알림 추가 함수를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1842">**semaphore_put_notify**: Pointer to application’s semaphore put notification function.</span></span> <span data-ttu-id="38207-1843">이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1843">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1844">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1844">Return Values</span></span>

- <span data-ttu-id="38207-1845">**TX_SUCCESS**:(0x00) 세마포 추가 알림이 성공적으로 등록되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1845">**TX_SUCCESS**: (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="38207-1846">TX_SEMAPHORE_ERROR:(0x0C) 잘못된 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1846">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="38207-1847">**TX_FEATURE_NOT_ENABLED**:(0xff) 시스템이 알림 기능을 사용하지 않도록 설정한 상태로 컴파일되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1847">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1848">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1848">Allowed From</span></span>

<span data-ttu-id="38207-1849">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1849">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-1850">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1850">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
   the put operations on the semaphore "my_semaphore." */
status =  tx_semaphore_put_notify(&my_semaphore,
                my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
   was successfully registered. */

void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
   /* The semaphore was just put! */
}
```
### <a name="see-also"></a><span data-ttu-id="38207-1851">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1851">See Also</span></span>

- <span data-ttu-id="38207-1852">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="38207-1852">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="38207-1853">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="38207-1853">tx_semaphore_create</span></span>
- <span data-ttu-id="38207-1854">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1854">tx_semaphore_delete</span></span>
- <span data-ttu-id="38207-1855">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="38207-1855">tx_semaphore_get</span></span>
- <span data-ttu-id="38207-1856">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1856">tx_semaphore_info_get</span></span>
- <span data-ttu-id="38207-1857">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1857">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="38207-1858">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1858">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1859">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="38207-1859">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="38207-1860">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="38207-1860">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="38207-1861">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-1861">tx_thread_create</span></span>

<span data-ttu-id="38207-1862">애플리케이션 스레드 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-1862">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1863">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1863">Prototype</span></span>

```C
UINT tx_thread_create(TX_THREAD *thread_ptr,
                          CHAR *name_ptr, VOID (*entry_function)(ULONG),
                          ULONG entry_input, VOID *stack_start,
                          ULONG stack_size, UINT priority,
                          UINT preempt_threshold, ULONG time_slice,
                          UINT auto_start);
```
### <a name="description"></a><span data-ttu-id="38207-1864">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1864">Description</span></span>

<span data-ttu-id="38207-1865">이 서비스는 지정된 작업 진입 함수에서 실행을 시작하는 애플리케이션 스레드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1865">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="38207-1866">스택, 우선 순위, 선점 임계값 및 시간 조각은 입력 매개 변수로 지정된 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1866">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="38207-1867">또한 스레드의 초기 실행 상태도 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1867">In addition, the initial execution state of the thread is also specified.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1868">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1868">Parameters</span></span>

- <span data-ttu-id="38207-1869">**thread_ptr**: 스레드 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1869">**thread_ptr**: Pointer to a thread control block.</span></span>
- <span data-ttu-id="38207-1870">**name_ptr** 스레드 이름을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1870">**name_ptr**: Pointer to the name of the thread.</span></span>
- <span data-ttu-id="38207-1871">**entry_function**: 스레드 실행을 위한 초기 C 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1871">**entry_function**: Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="38207-1872">스레드가 이 진입 함수에서 반환되면 완료됨 상태로 전환되고 무기한 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1872">When a thread returns from this entry function, it is placed in a completed state and suspended indefinitely.</span></span>
- <span data-ttu-id="38207-1873">**entry_input**: 처음 실행될 때 스레드의 진입 함수로 전달되는 32비트 값입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1873">**entry_input**: A 32-bit value that is passed to the thread’s entry function when it first executes.</span></span> <span data-ttu-id="38207-1874">이 입력의 사용 여부는 애플리케이션에서 단독으로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1874">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="38207-1875">**stack_start**: 스택 메모리 영역의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1875">**stack_start**: Starting address of the stack’s memory area.</span></span> 
- <span data-ttu-id="38207-1876">**stack_size**: 스택 메모리 영역의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1876">**stack_size**: Number bytes in the stack memory area.</span></span> <span data-ttu-id="38207-1877">스레드의 스택 영역은 최악의 함수 호출 중첩 및 로컬 변수 사용을 처리할 수 있을 만큼 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1877">The thread’s stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="38207-1878">**priority**: 스레드의 숫자 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1878">**priority**: Numerical priority of thread.</span></span> <span data-ttu-id="38207-1879">유효한 값의 범위는 0에서 (TX_MAX_PRIORITES-1)까지입니다. 여기서 값 0은 가장 높은 우선 순위를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1879">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="38207-1880">**preempt_threshold**: 사용하지 않도록 설정된 선점의 가장 높은 우선 순위 수준(0-(TX_MAX_PRIORITIES-1))입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1880">**preempt_threshold**: Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="38207-1881">우선 순위가 이 수준보다 높아야만 이 스레드를 선점할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1881">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="38207-1882">이 값은 지정한 우선 순위보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1882">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="38207-1883">스레드 우선 순위와 값이 같으면 선점 임계값이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1883">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="38207-1884">**time_slice**: 같은 우선 순위의 다른 준비 스레드를 실행할 수 있을 때까지 이 스레드를 실행할 수 있는 타이머 틱의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1884">**time_slice**: Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="38207-1885">선점 임계값을 사용하면 시간 조각화를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1885">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="38207-1886">유효한 시간 조각 값의 범위는 1에서 0xFFFFFFFF까지입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1886">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="38207-1887">**TX_NO_TIME_SLICE** 값(값 0)을 사용하면 이 스레드의 시간 조각화가 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1887">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="38207-1888">시간 조각화를 사용하면 약간의 시스템 오버헤드가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1888">Using time-slicing results in a slight amount of system overhead.</span></span> <span data-ttu-id="38207-1889">시간 조각화는 여러 스레드가 동일한 우선 순위를 공유하는 경우에만 유용하기 때문에 고유한 우선 순위를 갖는 스레드에 시간 조각을 할당해서는 안됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1889">Since time-slicing is only useful in cases where multiple threads share the same priority, threads having a unique priority should not be assigned a time-slice.</span></span>

- <span data-ttu-id="38207-1890">**auto_start**: 스레드가 즉시 시작되는지 또는 일시 중단된 상태가 되는지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1890">**auto_start**: Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="38207-1891">유효한 옵션은 **TX_AUTO_START**(0x01) 및 **TX_DONT_START**(0x00)입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1891">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="38207-1892">TX_DONT_START를 지정하면 애플리케이션은 나중에 스레드를 실행하기 위해 tx_thread_resume을 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1892">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1893">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1893">Return Values</span></span>

- <span data-ttu-id="38207-1894">**TX_SUCCESS** (0x00) 스레드를 성공적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1894">**TX_SUCCESS**: (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="38207-1895">TX_THREAD_ERROR:(0x0E) 잘못된 스레드 제어 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1895">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="38207-1896">포인터가 NULL이거나 스레드가 이미 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1896">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="38207-1897">TX_PTR_ERROR:(0x03) 진입점의 시작 주소가 잘못되었거나 스택 영역이 잘못되었습니다(일반적으로 NULL).</span><span class="sxs-lookup"><span data-stu-id="38207-1897">TX_PTR_ERROR: (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="38207-1898">TX_SIZE_ERROR:(0x05) 스택 영역의 크기가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1898">TX_SIZE_ERROR: (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="38207-1899">스레드를 실행하려면 적어도 **TX_MINIMUM_STACK** 바이트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1899">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="38207-1900">TX_PRIORITY_ERROR:(0x0F) 스레드 우선 순위가 잘못되었습니다. 값이 (0~(TX_MAX_PRIORITIES-1) 범위를 벗어납니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1900">TX_PRIORITY_ERROR: (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="38207-1901">TX_THRESH_ERROR:(0x18) 잘못된 preemptionthreshold를 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1901">TX_THRESH_ERROR: (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="38207-1902">이 값은 스레드의 초기 우선 순위보다 작거나 같은 유효한 우선 순위여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1902">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="38207-1903">TX_START_ERROR:(0x10) 잘못된 자동 시작 선택입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1903">TX_START_ERROR: (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="38207-1904">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1904">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1905">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1905">Allowed From</span></span>

<span data-ttu-id="38207-1906">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="38207-1906">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1907">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1907">Preemption Possible</span></span>

<span data-ttu-id="38207-1908">예</span><span class="sxs-lookup"><span data-stu-id="38207-1908">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-1909">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1909">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Create a thread of priority 15 whose entry point is
   "my_thread_entry". This thread’s stack area is 1000
   bytes in size, starting at address 0x400000. The
   preemption-threshold is setup to allow preemption of threads
   with priorities ranging from 0 through 14. Time-slicing is
   disabled. This thread is automatically put into a ready
   condition. */
status =  tx_thread_create(&my_thread, "my_thread_name",
                my_thread_entry, 0x1234,
                (VOID *) 0x400000, 1000,
                15, 15, TX_NO_TIME_SLICE,
                TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
   for execution! */
...

/* Thread’s entry function. When "my_thread" actually
   begins execution, control is transferred to this
   function. */
VOID my_thread_entry (ULONG initial_input)
{

    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */

    /* The real work of the thread, including calls to
    other function should be called from here! */

    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```
### <a name="see-also"></a><span data-ttu-id="38207-1910">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1910">See Also</span></span>

- <span data-ttu-id="38207-1911">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1911">tx_thread_delete</span></span>
- <span data-ttu-id="38207-1912">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1912">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-1913">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-1913">tx_thread_identify</span></span>
- <span data-ttu-id="38207-1914">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1914">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-1915">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1915">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-1916">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1916">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1917">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-1917">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-1918">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-1918">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-1919">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-1919">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-1920">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-1920">tx_thread_reset</span></span>
- <span data-ttu-id="38207-1921">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-1921">tx_thread_resume</span></span>
- <span data-ttu-id="38207-1922">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-1922">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-1923">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1923">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-1924">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-1924">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-1925">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-1925">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-1926">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-1926">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-1927">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-1927">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="38207-1928">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1928">tx_thread_delete</span></span>

<span data-ttu-id="38207-1929">애플리케이션 스레드 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-1929">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1930">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1930">Prototype</span></span>

```C
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-1931">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1931">Description</span></span>

<span data-ttu-id="38207-1932">이 서비스는 지정된 애플리케이션 스레드를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1932">This service deletes the specified application thread.</span></span> <span data-ttu-id="38207-1933">지정된 스레드가 종료된 상태 또는 완료된 상태여야 하므로 이 서비스는 자신을 삭제하려고 시도하는 스레드에서 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1933">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-1934">이 서비스가 완료된 후에 사용할 수 있는 스레드 스택과 연결된 메모리 영역을 관리하는 것은 애플리케이션의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1934">It is the application’s responsibility to manage the memory area associated with the thread’s stack, which is available after this service completes.</span></span> <span data-ttu-id="38207-1935">또한 애플리케이션은 삭제된 스레드를 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1935">In addition, the application must prevent use of a deleted thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1936">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1936">Parameters</span></span>

- <span data-ttu-id="38207-1937">**thread_ptr**: 이전에 만든 애플리케이션 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1937">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1938">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1938">Return Values</span></span>

- <span data-ttu-id="38207-1939">**TX_SUCCESS** (0x00) 스레드를 성공적으로 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1939">**TX_SUCCESS**: (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="38207-1940">TX_THREAD_ERROR:(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1940">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="38207-1941">**TX_DELETE_ERROR**:(0X11) 지정된 스레드가 종료된 상태 또는 완료된 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1941">**TX_DELETE_ERROR**: (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="38207-1942">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1942">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1943">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1943">Allowed From</span></span>

<span data-ttu-id="38207-1944">스레드 및 타이머</span><span class="sxs-lookup"><span data-stu-id="38207-1944">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-1945">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-1945">Preemption Possible</span></span>

<span data-ttu-id="38207-1946">예</span><span class="sxs-lookup"><span data-stu-id="38207-1946">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-1947">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1947">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Delete an application thread whose control block is
   "my_thread". Assume that the thread has already been
   created with a call to tx_thread_create. */
status =  tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="38207-1948">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1948">See Also</span></span>

- <span data-ttu-id="38207-1949">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-1949">tx_thread_create</span></span>
- <span data-ttu-id="38207-1950">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1950">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-1951">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-1951">tx_thread_identify</span></span>
- <span data-ttu-id="38207-1952">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1952">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-1953">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1953">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-1954">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1954">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1955">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-1955">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-1956">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-1956">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-1957">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-1957">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-1958">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-1958">tx_thread_reset</span></span>
- <span data-ttu-id="38207-1959">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-1959">tx_thread_resume</span></span>
- <span data-ttu-id="38207-1960">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-1960">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-1961">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1961">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-1962">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-1962">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-1963">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-1963">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-1964">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-1964">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-1965">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-1965">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="38207-1966">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1966">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="38207-1967">스레드 입력 및 종료 시 애플리케이션에 알림</span><span class="sxs-lookup"><span data-stu-id="38207-1967">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-1968">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-1968">Prototype</span></span>

```C
UINT  tx_thread_entry_exit_notify(TX_THREAD *thread_ptr,
        VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```
### <a name="description"></a><span data-ttu-id="38207-1969">Description</span><span class="sxs-lookup"><span data-stu-id="38207-1969">Description</span></span>

<span data-ttu-id="38207-1970">이 서비스는 지정된 스레드를 진입하거나 종료할 때마다 호출되는 알림 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1970">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="38207-1971">알림 콜백의 처리는 애플리케이션에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1971">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="38207-1972">애플리케이션의 알림 진입/종료 알림 콜백은 일시 중단 옵션을 사용하여 ThreadX SMP API를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1972">The application’s thread entry/exit notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-1973">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-1973">Parameters</span></span>

- <span data-ttu-id="38207-1974">**thread_ptr**: 이전에 만든 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1974">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="38207-1975">**entry_exit_notify**: 애플리케이션의 스레드 진입/종료 알림 함수를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1975">**entry_exit_notify**: Pointer to application’s thread entry/exit notification function.</span></span> <span data-ttu-id="38207-1976">진입/종료 알림 함수의 두 번째 매개 변수는 진입인지 또는 종료인지를 정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1976">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="38207-1977">값 TX_THREAD_ENTRY(0x00)는 스레드에 진입했음을 나타내고, 값 TX_THREAD_EXIT(0x01)는 스레드가 종료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1977">The value TX_THREAD_ENTRY (0x00) indicates the thread was entered, while the value TX_THREAD_EXIT (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="38207-1978">이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1978">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-1979">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-1979">Return Values</span></span>

- <span data-ttu-id="38207-1980">**TX_SUCCESS**:(0x00) 스레드 진입/종료 알림 함수를 등록했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1980">**TX_SUCCESS**: (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="38207-1981">TX_THREAD_ERROR:(0x0E) 잘못된 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1981">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="38207-1982">**TX_FEATURE_NOT_ENABLED(0xff)** 시스템이 알림 기능을 사용하지 않도록 설정한 상태로 컴파일되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-1982">**TX_FEATURE_NOT_ENABLED(0xFF)** The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-1983">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-1983">Allowed From</span></span>

<span data-ttu-id="38207-1984">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-1984">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-1985">예제</span><span class="sxs-lookup"><span data-stu-id="38207-1985">Example</span></span>

```C
TX_THREAD         my_thread;

/* Register the "my_entry_exit_notify" function for monitoring
   the entry/exit of the thread "my_thread." */
status =  tx_thread_entry_exit_notify(&my_thread,
                my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
   successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{

    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
                 /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
         /* Thread exit! */
}
```

### <a name="see-also"></a><span data-ttu-id="38207-1986">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-1986">See Also</span></span>

- <span data-ttu-id="38207-1987">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-1987">tx_thread_create</span></span>
- <span data-ttu-id="38207-1988">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-1988">tx_thread_delete</span></span>
- <span data-ttu-id="38207-1989">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-1989">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-1990">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-1990">tx_thread_identify</span></span>
- <span data-ttu-id="38207-1991">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1991">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-1992">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1992">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-1993">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-1993">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-1994">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-1994">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-1995">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-1995">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-1996">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-1996">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-1997">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-1997">tx_thread_reset</span></span>
- <span data-ttu-id="38207-1998">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-1998">tx_thread_resume</span></span>
- <span data-ttu-id="38207-1999">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-1999">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2000">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2000">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2001">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2001">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2002">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2002">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2003">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2003">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2004">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2004">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="38207-2005">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2005">tx_thread_identify</span></span>

<span data-ttu-id="38207-2006">현재 실행 중인 스레드에 대한 포인터 검색</span><span class="sxs-lookup"><span data-stu-id="38207-2006">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2007">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2007">Prototype</span></span>

```C
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="38207-2008">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2008">Description</span></span>

<span data-ttu-id="38207-2009">이 서비스는 현재 실행 중인 스레드를 가리키는 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2009">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="38207-2010">스레드가 실행되고 있지 않으면 이 서비스는 null 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2010">If no thread is executing, this service returns a null pointer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2011">이 서비스를 ISR에서 호출하는 경우 반환 값은 실행 중인 인터럽트 처리기 이전에 실행되는 스레드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2011">If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2012">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2012">Parameters</span></span>

<span data-ttu-id="38207-2013">None</span><span class="sxs-lookup"><span data-stu-id="38207-2013">None</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2014">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2014">Return Values</span></span>

- <span data-ttu-id="38207-2015">thread pointer: 현재 실행 중인 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2015">thread pointer: Pointer to the currently executing thread.</span></span> <span data-ttu-id="38207-2016">실행 중인 스레드가 없는 경우 반환 값은 TX_NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2016">If no thread is executing, the return value is TX_NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2017">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2017">Allowed From</span></span>

<span data-ttu-id="38207-2018">스레드 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2018">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2019">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2019">Preemption Possible</span></span>

<span data-ttu-id="38207-2020">예</span><span class="sxs-lookup"><span data-stu-id="38207-2020">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-2021">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2021">Example</span></span>

```C
TX_THREAD     *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr =  tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
   from that thread or an ISR that interrupted that thread.
   Otherwise, this service was called
   from an ISR when no thread was running when the
   interrupt occurred.  */
```
### <a name="see-also"></a><span data-ttu-id="38207-2022">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2022">See Also</span></span>

- <span data-ttu-id="38207-2023">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2023">tx_thread_create</span></span>
- <span data-ttu-id="38207-2024">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2024">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2025">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2025">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2026">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2026">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2027">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2027">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2028">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2028">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2029">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2029">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2030">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2030">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2031">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2031">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2032">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2032">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2033">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2033">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2034">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2034">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2035">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2035">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2036">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2036">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2037">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2037">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2038">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2038">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2039">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2039">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="38207-2040">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2040">tx_thread_info_get</span></span>

<span data-ttu-id="38207-2041">스레드에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-2041">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2042">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2042">Prototype</span></span>

```C
UINT tx_thread_info_get(TX_THREAD *thread_ptr, CHAR **name,
                          UINT *state, ULONG *run_count,
                          UINT *priority,
                          UINT *preemption_threshold,
                          ULONG *time_slice,
                          TX_THREAD **next_thread,
                          TX_THREAD **suspended_thread);
```
### <a name="description"></a><span data-ttu-id="38207-2043">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2043">Description</span></span>

<span data-ttu-id="38207-2044">이 서비스는 지정된 스레드에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2044">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2045">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2045">Parameters</span></span> 

- <span data-ttu-id="38207-2046">**thread_ptr**: 스레드 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2046">**thread_ptr**: Pointer to thread control block.</span></span>
- <span data-ttu-id="38207-2047">**name**: 스레드 이름에 대한 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2047">**name**: Pointer to destination for the pointer to the thread’s name.</span></span>
- <span data-ttu-id="38207-2048">**state**: 스레드의 현재 실행 상태에 대한 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2048">**state**:  Pointer to destination for the thread’s current execution state.</span></span> <span data-ttu-id="38207-2049">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2049">Possible values are as follows:</span></span>
    - <span data-ttu-id="38207-2050">**TX_READY**:(0x00)</span><span class="sxs-lookup"><span data-stu-id="38207-2050">**TX_READY**: (0x00)</span></span>
    - <span data-ttu-id="38207-2051">**TX_COMPLETED**:(0x01)</span><span class="sxs-lookup"><span data-stu-id="38207-2051">**TX_COMPLETED**: (0x01)</span></span>
    - <span data-ttu-id="38207-2052">**TX_TERMINATED**:(0x02)</span><span class="sxs-lookup"><span data-stu-id="38207-2052">**TX_TERMINATED**: (0x02)</span></span>
    - <span data-ttu-id="38207-2053">**TX_SUSPENDED**:(0x03)</span><span class="sxs-lookup"><span data-stu-id="38207-2053">**TX_SUSPENDED**: (0x03)</span></span>
    - <span data-ttu-id="38207-2054">**TX_SLEEP**:(0x04)</span><span class="sxs-lookup"><span data-stu-id="38207-2054">**TX_SLEEP**: (0x04)</span></span>
    - <span data-ttu-id="38207-2055">**TX_QUEUE_SUSP**:(0x05)</span><span class="sxs-lookup"><span data-stu-id="38207-2055">**TX_QUEUE_SUSP**: (0x05)</span></span>
    - <span data-ttu-id="38207-2056">**TX_SEMAPHORE_SUSP**:(0x06)</span><span class="sxs-lookup"><span data-stu-id="38207-2056">**TX_SEMAPHORE_SUSP**: (0x06)</span></span>
    - <span data-ttu-id="38207-2057">**TX_EVENT_FLAG**:(0x07)</span><span class="sxs-lookup"><span data-stu-id="38207-2057">**TX_EVENT_FLAG**: (0x07)</span></span>
    - <span data-ttu-id="38207-2058">**TX_BLOCK_MEMORY**:(0x08)</span><span class="sxs-lookup"><span data-stu-id="38207-2058">**TX_BLOCK_MEMORY**: (0x08)</span></span>
    - <span data-ttu-id="38207-2059">**TX_BYTE_MEMORY**:(0x09)</span><span class="sxs-lookup"><span data-stu-id="38207-2059">**TX_BYTE_MEMORY**: (0x09)</span></span>
    - <span data-ttu-id="38207-2060">**TX_MUTEX_SUSP**:(0x0D)</span><span class="sxs-lookup"><span data-stu-id="38207-2060">**TX_MUTEX_SUSP**: (0x0D)</span></span>

- <span data-ttu-id="38207-2061">**run_count**: 스레드 실행 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2061">**run_count**: Pointer to destination for the thread’s run count.</span></span> 
- <span data-ttu-id="38207-2062">**priority** 스레드 우선 순위 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2062">**priority**: Pointer to destination for the thread’s priority.</span></span>
- <span data-ttu-id="38207-2063">**preemption_threshold**: 스레드 선점 임계값 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2063">**preemption_threshold**: Pointer to destination for the thread’s preemption-threshold.</span></span>
- <span data-ttu-id="38207-2064">**time_slice**: 스레드 시간 조각 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2064">**time_slice**: Pointer to destination for the thread’s time-slice.</span></span> 
- <span data-ttu-id="38207-2065">**next_thread**: 다음에 만들 스레드 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2065">**next_thread**: Pointer to destination for next created thread pointer.</span></span>
- <span data-ttu-id="38207-2066">**suspended_thread**: 일시 중단 목록의 다음 스레드에 대한 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2066">**suspended_thread**: Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2067">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2067">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2068">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2068">Return Values</span></span>

- <span data-ttu-id="38207-2069">**NX_SUCCESS**(0x00) 스레드 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2069">**TX_SUCCESS**: (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="38207-2070">TX_THREAD_ERROR:(0x0E) 잘못된 스레드 제어 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2070">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2071">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2071">Allowed From</span></span>

<span data-ttu-id="38207-2072">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2072">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2073">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2073">Preemption Possible</span></span>

<span data-ttu-id="38207-2074">예</span><span class="sxs-lookup"><span data-stu-id="38207-2074">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-2075">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2075">Example</span></span>

```C
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
   thread "my_thread." */
status =  tx_thread_info_get(&my_thread, &name,
                  &state, &run_count,
            &priority, &preemption_threshold,
                  &time_slice, &next_thread,&suspended_thread);
/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2076">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2076">See Also</span></span>

- <span data-ttu-id="38207-2077">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2077">tx_thread_create</span></span>
- <span data-ttu-id="38207-2078">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2078">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2079">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2079">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2080">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2080">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2081">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2081">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2082">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2082">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2083">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2083">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2084">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2084">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2085">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2085">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2086">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2086">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2087">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2087">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2088">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2088">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2089">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2089">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2090">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2090">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2091">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2091">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2092">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2092">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2093">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2093">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="38207-2094">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2094">tx_thread_performance_info_get</span></span> 

<span data-ttu-id="38207-2095">스레드 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-2095">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2096">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2096">Prototype</span></span>

```C
UINT  tx_thread_performance_info_get(TX_THREAD *thread_ptr,
        ULONG *resumptions, ULONG *suspensions,
        ULONG *solicited_preemptions, ULONG *interrupt_preemptions,
        ULONG *priority_inversions, ULONG *time_slices,
        ULONG *relinquishes, ULONG *timeouts, ULONG *wait_aborts,
        TX_THREAD **last_preempted_by);
```
### <a name="description"></a><span data-ttu-id="38207-2097">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2097">Description</span></span>

<span data-ttu-id="38207-2098">이 서비스는 지정된 스레드에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2098">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2099">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_THREAD_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2099">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2100">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2100">Parameters</span></span> 

- <span data-ttu-id="38207-2101">**thread_ptr**: 이전에 만든 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2101">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="38207-2102">**resumptions**: 이 스레드 재개 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2102">**resumptions**: Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="38207-2103">**suspensions**: 이 스레드 일시 중단 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2103">**suspensions**: Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="38207-2104">**solicited_preemptions**: 이 스레드에서 수행한 ThreadX API 서비스 호출의 결과인 선점 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2104">**solicited_preemptions**: Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="38207-2105">**interrupt_preemptions**: 인터럽트 처리의 결과인 이 스레드 선점 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2105">**interrupt_preemptions**: Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="38207-2106">**priority_inversions**: 이 스레드 우선 순위 반전 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2106">**priority_inversions**: Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="38207-2107">**time_slices**: 이 스레드 시간 조각 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2107">**time_slices**: Pointer to destination for the number of timeslices of this thread.</span></span>
- <span data-ttu-id="38207-2108">**relinquishes**: 이 스레드에서 수행된 스레드 양도 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2108">**relinquishes**: Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="38207-2109">**timeouts**: 이 스레드의 일시 중단 시간 제한 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2109">**timeouts**: Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="38207-2110">**wait_aborts**: 이 스레드에서 수행된 대기 중단 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2110">**wait_aborts**: Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="38207-2111">**last_preempted_by**: 이 스레드를 마지막으로 선점한 스레드 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2111">**last_preempted_by**: Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2112">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2112">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2113">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2113">Return Values</span></span>

- <span data-ttu-id="38207-2114">**TX_SUCCESS**:(0X00) 스레드 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2114">**TX_SUCCESS**: (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="38207-2115">**TX_PTR_ERROR**:(0x03) 잘못된 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2115">**TX_PTR_ERROR**: (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="38207-2116">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2116">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2117">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2117">Allowed From</span></span>

<span data-ttu-id="38207-2118">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2118">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-2119">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2119">Example</span></span>

```c
TX_THREAD     my_thread;
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
TX_THREAD     *last_preempted_by;

/* Retrieve performance information on the previously created
   thread. */
status = tx_thread_performance_info_get(&my_thread, &resumptions,
               &suspensions,
               &solicited_preemptions, &interrupt_preemptions,
               &priority_inversions, &time_slices,
               &relinquishes, &timeouts,
               &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2120">See Also</span></span>

- <span data-ttu-id="38207-2121">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2121">tx_thread_create</span></span>
- <span data-ttu-id="38207-2122">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2122">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2123">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2123">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2124">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2124">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2125">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2125">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2126">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2126">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2127">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2127">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2128">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2128">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2129">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2129">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2130">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2130">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2131">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2131">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2132">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2132">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2133">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2133">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2134">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2134">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2135">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2135">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2136">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2136">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2137">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2137">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="38207-2138">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2138">tx_thread_performance_system_info_get</span></span> 

<span data-ttu-id="38207-2139">스레드 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-2139">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2140">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2140">Prototype</span></span>

```C
UINT tx_thread_performance_system_info_get(ULONG *resumptions,
       ULONG *suspensions, ULONG *solicited_preemptions,
       ULONG *interrupt_preemptions, ULONG *priority_inversions,
       ULONG *time_slices, ULONG *relinquishes, ULONG *timeouts,
       ULONG *wait_aborts, ULONG *non_idle_returns,
       ULONG *idle_returns);
```
### <a name="description"></a><span data-ttu-id="38207-2141">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2141">Description</span></span>

<span data-ttu-id="38207-2142">이 서비스는 시스템의 모든 스레드에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2142">This service retrieves performance information about all the threads in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2143">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_THREAD_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2143">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2144">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2144">Parameters</span></span>

- <span data-ttu-id="38207-2145">**resumptions**: 총 스레드 재개 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2145">**resumptions**: Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="38207-2146">**suspensions**: 총 스레드 일시 중단 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2146">**suspensions**: Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="38207-2147">**solicited_preemptions**: ThreadX API 서비스를 호출하는 스레드의 결과인 총 스레드 선점 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2147">**solicited_preemptions**: Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="38207-2148">**interrupt_preemptions**: 인터럽트 처리 결과인 총 스레드 선점 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2148">**interrupt_preemptions**: Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="38207-2149">**priority_inversions**: 총 스레드 우선 순위 반전 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2149">**priority_inversions**: Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="38207-2150">**time_slices**: 총 스레드 시간 조각 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2150">**time_slices**: Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="38207-2151">**relinquishes**: 총 스레드 양도 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2151">**relinquishes**: Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="38207-2152">**timeouts**: 총 스레드 일시 중단 시간 초과 수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2152">**timeouts**: Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="38207-2153">**wait_aborts**: 총 스레드 대기 중단 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2153">**wait_aborts**: Pointer to destination for the total number of thread wait aborts.</span></span> 
- <span data-ttu-id="38207-2154">**non_idle_returns**: 다른 스레드를 실행할 준비가 되었을 때 스레드가 시스템으로 반환되는 횟수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2154">**non_idle_returns**: Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span> 
- <span data-ttu-id="38207-2155">**_idle_returns**: 실행 준비가 완료된 스레드가 없을 때(유휴 시스템) 스레드가 시스템으로 반환되는 횟수의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2155">**idle_returns**: Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2156">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2156">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2157">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2157">Return Values</span></span>

- <span data-ttu-id="38207-2158">**TX_SUCCESS**:(0x00) 스레드 시스템 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2158">**TX_SUCCESS**: (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="38207-2159">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2159">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2160">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2160">Allowed From</span></span>

<span data-ttu-id="38207-2161">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2161">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-2162">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2162">Example</span></span>

```C
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
ULONG         non_idle_returns;
ULONG         idle_returns;

/* Retrieve performance information on all previously created
   thread. */
status = tx_thread_performance_system_info_get(&resumptions,
                &suspensions,
                &solicited_preemptions, &interrupt_preemptions,
                &priority_inversions, &time_slices, &relinquishes,
                &timeouts, &wait_aborts, &non_idle_returns,
                &idle_returns);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2163">See Also</span></span>

- <span data-ttu-id="38207-2164">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2164">tx_thread_create</span></span>
- <span data-ttu-id="38207-2165">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2165">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2166">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2166">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2167">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2167">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2168">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2168">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2169">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2169">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2170">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2170">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2171">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2171">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2172">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2172">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2173">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2173">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2174">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2174">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2175">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2175">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2176">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2176">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2177">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2177">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2178">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2178">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2179">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2179">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2180">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2180">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="38207-2181">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2181">tx_thread_preemption_change</span></span>

<span data-ttu-id="38207-2182">애플리케이션 스레드의 선점 임계값 변경</span><span class="sxs-lookup"><span data-stu-id="38207-2182">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2183">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2183">Prototype</span></span>

```C
UINT tx_thread_preemption_change(TX_THREAD *thread_ptr,
                          UINT new_threshold, UINT *old_threshold);
```
### <a name="description"></a><span data-ttu-id="38207-2184">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2184">Description</span></span>

<span data-ttu-id="38207-2185">이 서비스는 지정된 스레드의 선점 임계값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2185">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="38207-2186">선점 임계값은 선점 임계값보다 작거나 같은 스레드가 지정된 스레드를 선점하지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2186">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2187">선점 임계값을 사용하면 지정된 스레드에 대한 시간 조각화가 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2187">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2188">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2188">Parameters</span></span>

- <span data-ttu-id="38207-2189">**thread_ptr**: 이전에 만든 애플리케이션 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2189">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="38207-2190">**new_threshold**: 새 선점 임계값 우선 순위 수준입니다(0~(TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="38207-2190">**new_threshold**: New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="38207-2191">**old_threshold**: 이전 선점 임계값을 반환할 위치를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2191">**old_threshold**: Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2192">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2192">Return Values</span></span>

- <span data-ttu-id="38207-2193">**TX_SUCCESS**:(0X00) 선점 임계값을 변경했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2193">**TX_SUCCESS**: (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="38207-2194">TX_THREAD_ERROR:(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2194">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="38207-2195">**TX_THRESH_ERROR**:(0X18) 지정된 새 선점 임계값이 올바른 스레드 우선 순위((0-(TX_MAX_PRIORITIES-1)이 아닌 값)가 아니거나 현재 스레드 우선 순위보다 높거나 낮은 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2195">**TX_THRESH_ERROR**: (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (TX_MAX_PRIORITIES-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="38207-2196">TX_PTR_ERROR:(0x03) 이전 preemptionthreshold 스토리지 위치에 대한 잘못된 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2196">TX_PTR_ERROR: (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="38207-2197">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2197">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2198">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2198">Allowed From</span></span>

<span data-ttu-id="38207-2199">스레드 및 타이머</span><span class="sxs-lookup"><span data-stu-id="38207-2199">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2200">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2200">Preemption Possible</span></span>

<span data-ttu-id="38207-2201">예</span><span class="sxs-lookup"><span data-stu-id="38207-2201">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-2202">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2202">Example</span></span>

```c
TX_THREAD     my_thread;
UINT          my_old_threshold;
UINT          status;

/* Disable all preemption of the specified thread. The
   current preemption-threshold is returned in
   "my_old_threshold". Assume that "my_thread" has
   already been created. */
status = tx_thread_preemption_change(&my_thread,
                             0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
   non-preemptable by another thread. Note that ISRs are
   not prevented by preemption disabling. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2203">See Also</span></span>

- <span data-ttu-id="38207-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2204">tx_thread_create</span></span>
- <span data-ttu-id="38207-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2205">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2207">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2210">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2210">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2211">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2211">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2212">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2212">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2213">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2213">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2214">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="38207-2221">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2221">tx_thread_priority_change</span></span>

<span data-ttu-id="38207-2222">애플리케이션 스레드의 우선 순위 변경</span><span class="sxs-lookup"><span data-stu-id="38207-2222">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2223">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2223">Prototype</span></span>

```C
UINT tx_thread_priority_change(TX_THREAD *thread_ptr,
                          UINT new_priority, UINT *old_priority);
```
### <a name="description"></a><span data-ttu-id="38207-2224">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2224">Description</span></span>

<span data-ttu-id="38207-2225">이 서비스는 지정된 스레드의 우선 순위를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2225">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="38207-2226">유효한 우선 순위는 0~(TX_MAX_PRIORITES-1) 사이입니다. 여기서 0은 가장 높은 우선 순위 수준을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2226">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2227">지정된 스레드의 선점 임계값은 새 우선 순위로 자동 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2227">The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="38207-2228">새 임계값을 원할 경우 이 호출 후에 **tx_thread_preemption_change** 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2228">If a new threshold is desired, the **tx_thread_preemption_change** service must be used after this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2229">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2229">Parameters</span></span>

- <span data-ttu-id="38207-2230">**thread_ptr**: 이전에 만든 애플리케이션 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2230">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="38207-2231">**new_priority**: 새 스레드 우선 순위 수준(0-(TX_MAX_PRIORITIES-1))입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2231">**new_priority**: New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="38207-2232">**old_priority**: 스레드의 이전 우선 순위를 반환할 위치를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2232">**old_priority**: Pointer to a location to return the thread’s previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2233">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2233">Return Values</span></span>

- <span data-ttu-id="38207-2234">**TX_SUCCESS**:(0x00) 우선 순위를 변경했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2234">**TX_SUCCESS**: (0x00) Successful priority change.</span></span>
- <span data-ttu-id="38207-2235">TX_THREAD_ERROR:(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2235">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="38207-2236">TX_PRIORITY_ERROR:(0x0F) 지정된 새 우선 순위가 잘못되었습니다((0-(TX_MAX_PRIORITIES-1) 이외의 값).</span><span class="sxs-lookup"><span data-stu-id="38207-2236">TX_PRIORITY_ERROR: (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="38207-2237">TX_PTR_ERROR:(0x03) 이전 우선 순위 스토리지 위치에 대한 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2237">TX_PTR_ERROR: (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="38207-2238">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2238">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2239">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2239">Allowed From</span></span>

<span data-ttu-id="38207-2240">스레드 및 타이머</span><span class="sxs-lookup"><span data-stu-id="38207-2240">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2241">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2241">Preemption Possible</span></span>

<span data-ttu-id="38207-2242">예</span><span class="sxs-lookup"><span data-stu-id="38207-2242">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-2243">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2243">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          my_old_priority;
UINT          status;

/* Change the thread represented by "my_thread" to priority
   0. */
status = tx_thread_priority_change(&my_thread,
                            0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
   now at the highest priority level in the system. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2244">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2244">See Also</span></span>

- <span data-ttu-id="38207-2245">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2245">tx_thread_create</span></span>
- <span data-ttu-id="38207-2246">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2246">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2247">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2247">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2248">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2248">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2249">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2249">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2250">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2250">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2251">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2251">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2252">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2252">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2253">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2253">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2254">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2254">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2255">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2255">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2256">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2256">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2257">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2257">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2258">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2258">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2259">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2259">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2260">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2260">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2261">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2261">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="38207-2262">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2262">tx_thread_relinquish</span></span>

<span data-ttu-id="38207-2263">다른 애플리케이션 스레드에 대한 제어권 포기</span><span class="sxs-lookup"><span data-stu-id="38207-2263">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2264">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2264">Prototype</span></span>

```C
VOID tx_thread_relinquish(VOID);
```
### <a name="description"></a><span data-ttu-id="38207-2265">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2265">Description</span></span>

<span data-ttu-id="38207-2266">이 서비스는 동일하거나 더 높은 우선 순위를 갖는 즉시 실행 가능한 다른 스레드에 대한 프로세서 제어권을 포기합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2266">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2267">이 서비스는 동일한 우선 순위 스레드에 대한 제어권을 포기하는 것 외에도 현재 스레드의 선점 임계값 설정으로 인해 실행이 차단되는 우선 순위가 가장 높은 스레드에 대한 제어권을 포기합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2267">In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2268">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2268">Parameters</span></span>

<span data-ttu-id="38207-2269">None</span><span class="sxs-lookup"><span data-stu-id="38207-2269">None</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2270">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2270">Return Values</span></span>

<span data-ttu-id="38207-2271">None</span><span class="sxs-lookup"><span data-stu-id="38207-2271">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2272">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2272">Allowed From</span></span>

<span data-ttu-id="38207-2273">스레드</span><span class="sxs-lookup"><span data-stu-id="38207-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2274">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2274">Preemption Possible</span></span>

<span data-ttu-id="38207-2275">예</span><span class="sxs-lookup"><span data-stu-id="38207-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-2276">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2276">Example</span></span>

```C
ULONG run_counter_1 =  0;
ULONG run_counter_2 =  0;

/* Example of two threads relinquishing control to
   each other in an infinite loop. Assume that
   both of these threads are ready and have the same
   priority. The run counters will always stay within one
   of each other. */

VOID  my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {

        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```
### <a name="see-also"></a><span data-ttu-id="38207-2277">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2277">See Also</span></span>

- <span data-ttu-id="38207-2278">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2278">tx_thread_create</span></span>
- <span data-ttu-id="38207-2279">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2279">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2280">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2280">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2281">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2281">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2282">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2282">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2283">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2283">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2284">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2284">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2285">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2285">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2286">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2286">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2287">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2288">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2289">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2289">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2290">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2290">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2291">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2291">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2292">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2292">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2293">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2293">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2294">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2294">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="38207-2295">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2295">tx_thread_reset</span></span>

<span data-ttu-id="38207-2296">스레드 다시 설정</span><span class="sxs-lookup"><span data-stu-id="38207-2296">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2297">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2297">Prototype</span></span>

```C
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-2298">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2298">Description</span></span>

<span data-ttu-id="38207-2299">이 서비스는 지정된 스레드를 스레드 생성 시 정의된 진입점에서 실행되도록 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2299">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="38207-2300">다시 설정하려면 스레드가 **TX_COMPLETED** 또는 **TX_TERMINATED** 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2300">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2301">다시 실행하려면 스레드를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2301">The thread must be resumed for it to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2302">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2302">Parameters</span></span> 

- <span data-ttu-id="38207-2303">**thread_ptr**: 이전에 만든 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2303">**thread_ptr**: Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2304">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2304">Return Values</span></span>

- <span data-ttu-id="38207-2305">**TX_SUCCESS**:(0x00) 스레드를 다시 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2305">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="38207-2306">**TX_NOT_DONE**:(0X20) 지정된 스레드가 TX_COMPLETED 또는 TX_TERMINATED 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2306">**TX_NOT_DONE**: (0x20) Specified thread is not in a TX_COMPLETED or TX_TERMINATED state.</span></span>
- <span data-ttu-id="38207-2307">TX_THREAD_ERROR:(0x0E) 잘못된 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2307">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="38207-2308">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2308">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2309">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2309">Allowed From</span></span>

<span data-ttu-id="38207-2310">스레드</span><span class="sxs-lookup"><span data-stu-id="38207-2310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="38207-2311">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2311">Example</span></span>

```C
TX_THREAD     my_thread;

/* Reset the previously created thread "my_thread." */
status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2312">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2312">See Also</span></span>

- <span data-ttu-id="38207-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2313">tx_thread_create</span></span>
- <span data-ttu-id="38207-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2314">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2316">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2319">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2319">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2323">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2323">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2324">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2324">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2325">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2325">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="38207-2330">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2330">tx_thread_resume</span></span>

<span data-ttu-id="38207-2331">일시 중단된 애플리케이션 스레드 다시 시작</span><span class="sxs-lookup"><span data-stu-id="38207-2331">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2332">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2332">Prototype</span></span>

```C
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-2333">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2333">Description</span></span>

<span data-ttu-id="38207-2334">이 서비스는 이전에 ***tx_thread_suspend*** 호출로 일시 중단된 스레드의 실행을 다시 시작하거나 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2334">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="38207-2335">또한 이 서비스는 자동 시작 없이 생성된 스레드를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2335">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2336">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2336">Parameters</span></span>

- <span data-ttu-id="38207-2337">**thread_ptr**: 일시 중단된 애플리케이션 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2337">**thread_ptr**: Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2338">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2338">Return Values</span></span>

- <span data-ttu-id="38207-2339">**TX_SUCCESS**:(0x00) 스레드를 다시 시작하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2339">**TX_SUCCESS**: (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="38207-2340">**TX_SUSPEND_LIFTED**:(0x19) 이전에 설정된 지연된 일시 중단이 해제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2340">**TX_SUSPEND_LIFTED**: (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="38207-2341">TX_THREAD_ERROR:(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2341">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="38207-2342">**TX_RESUME_ERROR**:(12) 지정된 스레드가 일시 중단되지 않았거나 이전에 **_tx_thread_suspend_** 이외의 서비스에 의해 일시 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2342">**TX_RESUME_ERROR**: (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2343">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2343">Allowed From</span></span>

<span data-ttu-id="38207-2344">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2344">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2345">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2345">Preemption Possible</span></span>

<span data-ttu-id="38207-2346">예</span><span class="sxs-lookup"><span data-stu-id="38207-2346">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-2347">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2347">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Resume the thread represented by "my_thread". */
status =  tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   now ready to execute. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2348">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2348">See Also</span></span>

- <span data-ttu-id="38207-2349">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2349">tx_thread_create</span></span>
- <span data-ttu-id="38207-2350">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2350">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2351">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2351">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2352">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2352">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2353">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2353">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2354">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2354">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2355">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2355">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2356">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2356">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2357">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2357">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2358">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2358">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2359">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2359">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2360">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2360">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2361">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2361">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2362">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2362">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2363">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2363">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2364">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2364">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2365">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2365">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="38207-2366">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2366">tx_thread_sleep</span></span>

<span data-ttu-id="38207-2367">지정된 시간 동안 현재 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="38207-2367">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2368">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2368">Prototype</span></span>

```C
UINT tx_thread_sleep(ULONG timer_ticks);
```
### <a name="description"></a><span data-ttu-id="38207-2369">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2369">Description</span></span>

<span data-ttu-id="38207-2370">이 서비스는 지정된 수의 타이머 틱 동안 호출 스레드가 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2370">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="38207-2371">타이머 틱과 연결된 실제 시간의 양은 애플리케이션마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2371">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="38207-2372">이 서비스는 애플리케이션 스레드에서만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2372">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2373">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2373">Parameters</span></span>

- <span data-ttu-id="38207-2374">**timer_ticks**: 호출하는 애플리케이션 스레드를 일시 중단할 타이머 틱의 수입니다(0-0xFFFFFFFF 범위).</span><span class="sxs-lookup"><span data-stu-id="38207-2374">**timer_ticks**: The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="38207-2375">0을 지정하면 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2375">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2376">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2376">Return Values</span></span>

- <span data-ttu-id="38207-2377">**TX_SUCCESS**:(0x00) 스레드를 절전 모드로 전환했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2377">**TX_SUCCESS**: (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="38207-2378">**TX_WAIT_ABORTED**:(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2378">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="38207-2379">**TX_CALLER_ERROR**:(0X13) 서비스가 비스레드에서 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2379">**TX_CALLER_ERROR**: (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2380">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2380">Allowed From</span></span>

<span data-ttu-id="38207-2381">스레드</span><span class="sxs-lookup"><span data-stu-id="38207-2381">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2382">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2382">Preemption Possible</span></span>

<span data-ttu-id="38207-2383">예</span><span class="sxs-lookup"><span data-stu-id="38207-2383">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-2384">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2384">Example</span></span>

```C
UINT status;

/* Make the calling thread sleep for 100
   timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
   application thread slept for the specified number of
   timer-ticks. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2385">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2385">See Also</span></span>

- <span data-ttu-id="38207-2386">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2386">tx_thread_create</span></span>
- <span data-ttu-id="38207-2387">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2387">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2388">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2388">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2389">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2389">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2390">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2390">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2391">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2391">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2392">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2392">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2393">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2393">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2394">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2394">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2395">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2395">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2396">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2396">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2397">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2397">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2398">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2398">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2399">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2399">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2400">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2400">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2401">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2401">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2402">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2402">tx_thread_wait_abort</span></span>

## <a name="tx_thread_smp_core_exclude"></a><span data-ttu-id="38207-2403">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="38207-2403">tx_thread_smp_core_exclude</span></span>

<span data-ttu-id="38207-2404">코어 세트에서 스레드 실행 제외</span><span class="sxs-lookup"><span data-stu-id="38207-2404">Exclude thread execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2405">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2405">Prototype</span></span>

```C
UINT  tx_thread_smp_core_exclude(TX_THREAD *thread_ptr,
                          ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="38207-2406">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2406">Description</span></span>

<span data-ttu-id="38207-2407">이 함수는 지정된 스레드가 "exclusion_map"이라는 비트 맵에 지정된 코어에서 실행되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2407">This function excludes the specified thread from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="38207-2408">"exclusion_map"의 각 비트는 코어를 나타냅니다(비트 0은 코어 0을 나타냄).</span><span class="sxs-lookup"><span data-stu-id="38207-2408">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="38207-2409">비트가 설정된 경우 해당 코어는 지정된 스레드 실행에서 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2409">If the bit is set, the corresponding core is excluded from executing the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2410">프로세서 제외를 사용하면 가장 최적 상태로 일치하는 항목을 찾기 위해 코어 매핑 논리에 대한 스레드의 추가 처리가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2410">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="38207-2411">이 처리는 준비 상태인 스레드 수에 따라 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2411">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2412">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2412">Parameters</span></span> 

- <span data-ttu-id="38207-2413">**thread_ptr**: 코어 제외를 변경하는 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2413">**thread_ptr**: Pointer to thread to change the core exclusion.</span></span>
- <span data-ttu-id="38207-2414">**exclusion_map**: sit 비트에서 코어가 제외되었음을 나타내는 비트 맵입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2414">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="38207-2415">0 값을 제공하면 스레드가 어떤 코어에서도 실행될 수 있습니다(기본값).</span><span class="sxs-lookup"><span data-stu-id="38207-2415">Supplying a 0 value enables the thread to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2416">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2416">Return Values</span></span>

- <span data-ttu-id="38207-2417">TX_SUCCESS:(0X00) 코어를 성공적으로 제외했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2417">TX_SUCCESS: (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="38207-2418">TX_THREAD_ERROR:(0x0E) 잘못된 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2418">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2419">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2419">Allowed From</span></span>

<span data-ttu-id="38207-2420">초기화, ISR, 스레드 및 타이머</span><span class="sxs-lookup"><span data-stu-id="38207-2420">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="38207-2421">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2421">Example</span></span>

```C
/* Exclude core 0 for "Thread 0". */
tx_thread_smp_core_exclude(&thread_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="38207-2422">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2422">See Also</span></span>

- <span data-ttu-id="38207-2423">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="38207-2423">tx_thread_smp_core_exclude_get</span></span>
- <span data-ttu-id="38207-2424">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="38207-2424">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_exclude_get"></a><span data-ttu-id="38207-2425">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="38207-2425">tx_thread_smp_core_exclude_get</span></span>

<span data-ttu-id="38207-2426">스레드의 현재 코어 제외 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-2426">Gets the thread's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2427">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2427">Prototype</span></span>

```C
UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-2428">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2428">Description</span></span>

<span data-ttu-id="38207-2429">이 함수는 현재 코어 제외 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2429">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2430">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2430">Parameters</span></span>

- <span data-ttu-id="38207-2431">**thread_ptr**: 코어 제외를 검색할 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2431">**thread_ptr**: Pointer to thread from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="38207-2432">**exclusion_map_ptr**: 현재 코어 제외 비트 맵에 대한 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2432">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2433">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2433">Return Values</span></span>

- <span data-ttu-id="38207-2434">TX_SUCCESS:(0x00) 스레드의 코어 제외를 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2434">TX_SUCCESS: (0x00) Successful retrieval of thread's core exclusion.</span></span>
- <span data-ttu-id="38207-2435">TX_THREAD_ERROR:(0x0E) 잘못된 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2435">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="38207-2436">TX_PTR_ERROR:(0x03) 잘못된 제외 대상 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2436">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2437">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2437">Allowed From</span></span>

<span data-ttu-id="38207-2438">초기화, ISR, 스레드 및 타이머</span><span class="sxs-lookup"><span data-stu-id="38207-2438">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="38207-2439">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2439">Example</span></span>

```C
ULONGexcluded_cores;
/* Retrieve the core exclusion for "Thread 0". */
tx_thread_smp_core_exclude_get(&thread_0, &excluded_cores);
```

### <a name="see-also"></a><span data-ttu-id="38207-2440">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2440">See Also</span></span>

- <span data-ttu-id="38207-2441">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="38207-2441">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="38207-2442">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="38207-2442">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_get"></a><span data-ttu-id="38207-2443">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="38207-2443">tx_thread_smp_core_get</span></span>

<span data-ttu-id="38207-2444">현재 실행 중인 호출자의 코어 검색</span><span class="sxs-lookup"><span data-stu-id="38207-2444">Retrieve currently executing core of caller</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2445">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2445">Prototype</span></span>

```C
UINT  tx_thread_smp_core_get(void);
```
### <a name="description"></a><span data-ttu-id="38207-2446">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2446">Description</span></span>

<span data-ttu-id="38207-2447">이 함수는 이 서비스를 실행하는 코어의 코어 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2447">This function returns the core ID of the core executing this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2448">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2448">Parameters</span></span>

<span data-ttu-id="38207-2449">None</span><span class="sxs-lookup"><span data-stu-id="38207-2449">None</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2450">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2450">Return Values</span></span>

- <span data-ttu-id="38207-2451">core_id: 현재 실행 중인 코어의 ID(0-TX_THREAD_SMP_MAX_CORES-1)</span><span class="sxs-lookup"><span data-stu-id="38207-2451">core_id: ID of currently executing core, (0 through TX_THREAD_SMP_MAX_CORES-1)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2452">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2452">Allowed From</span></span>

<span data-ttu-id="38207-2453">초기화, ISR, 스레드 및 타이머</span><span class="sxs-lookup"><span data-stu-id="38207-2453">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="38207-2454">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2454">Example</span></span>

```C
UINTcore;
/* Pickup the currently executing core. */
core = tx_thread_smp_core_get();

/* At this point, “core” contains the executing core ID. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2455">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2455">See Also</span></span>

- <span data-ttu-id="38207-2456">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="38207-2456">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="38207-2457">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="38207-2457">tx_thread_smp_core_exclude_get</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="38207-2458">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2458">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="38207-2459">스레드 스택 오류 알림 콜백 등록</span><span class="sxs-lookup"><span data-stu-id="38207-2459">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2460">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2460">Prototype</span></span>

```C
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```
### <a name="description"></a><span data-ttu-id="38207-2461">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2461">Description</span></span>

<span data-ttu-id="38207-2462">이 서비스는 스레드 스택 오류를 처리하기 위한 알림 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2462">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="38207-2463">ThreadX SMP가 실행 중에 스레드 스택 오류를 감지하면 이 알림 함수를 호출하여 오류를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2463">When ThreadX SMP detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="38207-2464">오류 처리는 애플리케이션에서 완전히 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2464">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="38207-2465">위반 스레드 일시 중단부터 전체 시스템 다시 설정에 이르는 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2465">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2466">ThreadX SMP 라이브러리는 이 서비스가 성능 정보를 반환하도록 정의된 **TX_ENABLE_STACK_CHECKING** 을 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2466">The ThreadX SMP library must be built with **TX_ENABLE_STACK_CHECKING** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2467">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2467">Parameters</span></span>

- <span data-ttu-id="38207-2468">**error_handler**: 애플리케이션 스택 오류 처리 함수를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2468">**error_handler**: Pointer to application’s stack error handling function.</span></span> <span data-ttu-id="38207-2469">이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2469">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2470">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2470">Return Values</span></span>

- <span data-ttu-id="38207-2471">**TX_SUCCESS**:(0x00) 스레드를 다시 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2471">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="38207-2472">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2472">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2473">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2473">Allowed From</span></span>

<span data-ttu-id="38207-2474">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2474">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-2475">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2475">Example</span></span>

```C
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX SMP
   so that thread stack errors can be handled by the application. */
status =  tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```
### <a name="see-also"></a><span data-ttu-id="38207-2476">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2476">See Also</span></span>

- <span data-ttu-id="38207-2477">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2477">tx_thread_create</span></span>
- <span data-ttu-id="38207-2478">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2478">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2479">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2479">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2480">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2480">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2481">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2481">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2482">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2482">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2483">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2483">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2484">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2484">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2485">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2485">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2486">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2486">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2487">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2487">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2488">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2488">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2489">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2489">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2490">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2490">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2491">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2491">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2492">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2492">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2493">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2493">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="38207-2494">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2494">tx_thread_suspend</span></span>

<span data-ttu-id="38207-2495">애플리케이션 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="38207-2495">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2496">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2496">Prototype</span></span>

```C
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-2497">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2497">Description</span></span>

<span data-ttu-id="38207-2498">이 서비스는 지정된 애플리케이션 스레드를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2498">This service suspends the specified application thread.</span></span> <span data-ttu-id="38207-2499">스레드는 이 서비스를 호출하여 자신을 일시 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2499">A thread may call this service to suspend itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2500">지정된 스레드가 다른 이유로 이미 일시 중단된 경우 이 일시 중단은 이전 일시 중단이 해제될 때까지 내부적으로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2500">If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted.</span></span> <span data-ttu-id="38207-2501">이 경우 지정된 스레드가 이와 같이 무조건적으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2501">When that happens, this unconditional suspension of the specified thread is performed.</span></span> <span data-ttu-id="38207-2502">향후의 무조건 일시 중단 요청은 더 이상 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2502">Further unconditional suspension requests have no effect.</span></span>

<span data-ttu-id="38207-2503">일시 중단된 후에는 ***tx_thread_resume*** 을 다시 실행하여 스레드를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2503">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

## <a name="parameters"></a><span data-ttu-id="38207-2504">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2504">Parameters</span></span>

- <span data-ttu-id="38207-2505">**thread_ptr**: 애플리케이션 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2505">**thread_ptr**: Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2506">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2506">Return Values</span></span>

- <span data-ttu-id="38207-2507">**TX_SUCCESS**:(0x00) 스레드를 일시 중단 모드로 전환했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2507">**TX_SUCCESS**: (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="38207-2508">TX_THREAD_ERROR:(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2508">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="38207-2509">**TX_SUSPEND_ERROR**:(0X14) 지정된 스레드가 종료된 상태 또는 완료된 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2509">**TX_SUSPEND_ERROR**: (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="38207-2510">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2510">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2511">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2511">Allowed From</span></span>

<span data-ttu-id="38207-2512">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2512">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2513">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2513">Preemption Possible</span></span>

<span data-ttu-id="38207-2514">예</span><span class="sxs-lookup"><span data-stu-id="38207-2514">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-2515">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2515">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   unconditionally suspended. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2516">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2516">See Also</span></span>

- <span data-ttu-id="38207-2517">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2517">tx_thread_create</span></span>
- <span data-ttu-id="38207-2518">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2518">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2519">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2519">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2520">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2520">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2521">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2521">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2522">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2522">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2523">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2523">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2524">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2524">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2525">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2525">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2526">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2526">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2527">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2527">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2528">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2528">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2529">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2529">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2530">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2530">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2531">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2531">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2532">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2532">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2533">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2533">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="38207-2534">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2534">tx_thread_terminate</span></span>

<span data-ttu-id="38207-2535">애플리케이션 스레드 종료</span><span class="sxs-lookup"><span data-stu-id="38207-2535">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2536">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2536">Prototype</span></span>

```C
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-2537">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2537">Description</span></span>

<span data-ttu-id="38207-2538">이 서비스는 스레드가 일시 중단되었는지 여부에 관계없이 지정된 애플리케이션 스레드를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2538">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="38207-2539">스레드는 이 서비스를 호출하여 자신을 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2539">A thread may call this service to terminate itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2540">종료된 후에는 다시 실행되도록 스레드를 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2540">After being terminated, the thread must be reset for it to execute again.</span></span>

> [!WARNING]
> <span data-ttu-id="38207-2541">스레드가 종료에 적합한 상태인지 확인하는 것은 애플리케이션의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2541">It is the application's responsibility to ensure the thread is in a state suitable for termination.</span></span> <span data-ttu-id="38207-2542">예를 들어 중요한 애플리케이션을 처리하는 동안이나 다른 미들웨어 구성 요소 내에서 스레드를 종료하면 안 됩니다. 이렇게 하면 처리가 알 수 없는 상태로 남아 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2542">For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2543">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2543">Parameters</span></span>

- <span data-ttu-id="38207-2544">**thread_ptr**: 애플리케이션 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2544">**thread_ptr**: Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2545">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2545">Return Values</span></span>

- <span data-ttu-id="38207-2546">**TX_SUCCESS**:(0x00) 스레드 종료에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2546">**TX_SUCCESS**: (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="38207-2547">TX_THREAD_ERROR:(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2547">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="38207-2548">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2548">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2549">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2549">Allowed From</span></span>

<span data-ttu-id="38207-2550">스레드 및 타이머</span><span class="sxs-lookup"><span data-stu-id="38207-2550">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2551">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2551">Preemption Possible</span></span>

<span data-ttu-id="38207-2552">예</span><span class="sxs-lookup"><span data-stu-id="38207-2552">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-2553">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2553">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Terminate the thread represented by "my_thread". */
status =  tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
   and cannot execute again until it is reset. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2554">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2554">See Also</span></span>

- <span data-ttu-id="38207-2555">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2555">tx_thread_create</span></span>
- <span data-ttu-id="38207-2556">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2556">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2557">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2557">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2558">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2558">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2559">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2559">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2560">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2560">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2561">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2561">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2562">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2562">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2563">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2563">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2564">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2564">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2565">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2565">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2566">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2566">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2567">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2567">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2568">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2568">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2569">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2569">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2570">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2570">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="38207-2571">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2571">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="38207-2572">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2572">tx_thread_time_slice_change</span></span>

<span data-ttu-id="38207-2573">애플리케이션 스레드의 시간 조각 변경</span><span class="sxs-lookup"><span data-stu-id="38207-2573">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2574">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2574">Prototype</span></span>

```C
UINT tx_thread_time_slice_change(TX_THREAD *thread_ptr,
                          ULONG new_time_slice, ULONG *old_time_slice);
```
### <a name="description"></a><span data-ttu-id="38207-2575">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2575">Description</span></span>

<span data-ttu-id="38207-2576">이 서비스는 지정된 애플리케이션 스레드의 시간 조각을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2576">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="38207-2577">스레드에 대한 시간 조각을 선택하면 우선 순위가 같거나 더 높은 다른 스레드를 실행하기 전까지, 지정된 타이머 틱 수보다 오래 실행되는 일이 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2577">Selecting a time-slice for a thread insures that it won’t execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2578">선점 임계값을 사용하면 지정된 스레드에 대한 시간 조각화가 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2578">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2579">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2579">Parameters</span></span>

- <span data-ttu-id="38207-2580">**thread_ptr**: 애플리케이션 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2580">**thread_ptr**: Pointer to application thread.</span></span>
- <span data-ttu-id="38207-2581">**new_time_slice**: 새 시간 조각 값입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2581">**new_time_slice**: New time slice value.</span></span> <span data-ttu-id="38207-2582">유효한 값에는 TX_NO_TIME_SLICE와 1부터 0xFFFFFFFF까지의 숫자 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2582">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="38207-2583">**old_time_slice**: 지정된 스레드의 이전 시간 조각 값 저장 위치를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2583">**old_time_slice**: Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2584">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2584">Return Values</span></span>

- <span data-ttu-id="38207-2585">**TX_SUCCESS**:(0X00) 성공한 시간 조각화 기회입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2585">**TX_SUCCESS**: (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="38207-2586">TX_THREAD_ERROR:(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2586">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="38207-2587">TX_PTR_ERROR:(0x03) 이전 시간 조각 스토리지 위치에 대한 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2587">TX_PTR_ERROR: (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="38207-2588">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2588">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2589">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2589">Allowed From</span></span>

<span data-ttu-id="38207-2590">스레드 및 타이머</span><span class="sxs-lookup"><span data-stu-id="38207-2590">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2591">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2591">Preemption Possible</span></span>

<span data-ttu-id="38207-2592">예</span><span class="sxs-lookup"><span data-stu-id="38207-2592">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-2593">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2593">Example</span></span>

```C
TX_THREAD     my_thread;
ULONG         my_old_time_slice;
UINT          status;

/* Change the time-slice of the thread associated with
   "my_thread" to 20. This will mean that "my_thread"
   can only run for 20 timer-ticks consecutively before
   other threads of equal or higher priority get a chance
   to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
                             &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
   has been changed to 20 and the previous time-slice is
   in "my_old_time_slice." */
```
### <a name="see-also"></a><span data-ttu-id="38207-2594">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2594">See Also</span></span>

- <span data-ttu-id="38207-2595">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2595">tx_thread_create</span></span>
- <span data-ttu-id="38207-2596">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2596">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2597">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2597">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2598">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2598">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2599">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2599">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2600">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2600">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2601">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2601">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2602">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2602">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2603">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2603">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2604">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2604">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2605">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2605">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2606">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2606">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2607">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2607">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2608">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2608">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2609">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2609">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2610">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2610">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2611">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2611">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="38207-2612">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="38207-2612">tx_thread_wait_abort</span></span>

<span data-ttu-id="38207-2613">지정된 스레드의 일시 중단 중단</span><span class="sxs-lookup"><span data-stu-id="38207-2613">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2614">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2614">Prototype</span></span>

```C
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="38207-2615">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2615">Description</span></span>

<span data-ttu-id="38207-2616">이 서비스는 지정된 스레드의 절전 또는 다른 개체 일시 중단을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2616">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="38207-2617">대기가 중단되면 스레드가 대기하고 있는 서비스에서 TX_WAIT_ABORTED 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2617">If the wait is aborted, a TX_WAIT_ABORTED value is returned from the service that the thread was waiting on.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2618">이 서비스는 tx_thread_suspend 서비스를 통해 수행된 명시적 일시 중단을 해제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2618">This service does not release explicit suspension that is made by the tx_thread_suspend service.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2619">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2619">Parameters</span></span>

- <span data-ttu-id="38207-2620">**thread_ptr**: 이전에 만든 애플리케이션 스레드를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2620">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2621">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2621">Return Values</span></span>

- <span data-ttu-id="38207-2622">**TX_SUCCESS**:(0x00) 스레드 대기 중단에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2622">**TX_SUCCESS**: (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="38207-2623">TX_THREAD_ERROR:(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2623">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="38207-2624">**TX_WAIT_ABORT_ERROR**:(0x1B) 지정된 스레드가 대기 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2624">**TX_WAIT_ABORT_ERROR**: (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2625">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2625">Allowed From</span></span>

<span data-ttu-id="38207-2626">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2626">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2627">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2627">Preemption Possible</span></span>

<span data-ttu-id="38207-2628">예</span><span class="sxs-lookup"><span data-stu-id="38207-2628">Yes</span></span>

### <a name="example"></a><span data-ttu-id="38207-2629">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2629">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Abort the suspension condition of "my_thread." */
status =  tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
   again, with a return value showing its suspension
   was aborted (TX_WAIT_ABORTED). */
```
### <a name="see-also"></a><span data-ttu-id="38207-2630">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2630">See Also</span></span>

- <span data-ttu-id="38207-2631">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="38207-2631">tx_thread_create</span></span>
- <span data-ttu-id="38207-2632">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2632">tx_thread_delete</span></span>
- <span data-ttu-id="38207-2633">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2633">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="38207-2634">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="38207-2634">tx_thread_identify</span></span>
- <span data-ttu-id="38207-2635">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2635">tx_thread_info_get</span></span>
- <span data-ttu-id="38207-2636">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2636">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="38207-2637">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2637">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="38207-2638">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="38207-2638">tx_thread_preemption_change</span></span>
- <span data-ttu-id="38207-2639">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="38207-2639">tx_thread_priority_change</span></span>
- <span data-ttu-id="38207-2640">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="38207-2640">tx_thread_relinquish</span></span>
- <span data-ttu-id="38207-2641">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="38207-2641">tx_thread_reset</span></span>
- <span data-ttu-id="38207-2642">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="38207-2642">tx_thread_resume</span></span>
- <span data-ttu-id="38207-2643">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="38207-2643">tx_thread_sleep</span></span>
- <span data-ttu-id="38207-2644">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="38207-2644">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="38207-2645">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="38207-2645">tx_thread_suspend</span></span>
- <span data-ttu-id="38207-2646">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="38207-2646">tx_thread_terminate</span></span>
- <span data-ttu-id="38207-2647">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="38207-2647">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="38207-2648">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="38207-2648">tx_time_get</span></span>

<span data-ttu-id="38207-2649">현재 시간 검색</span><span class="sxs-lookup"><span data-stu-id="38207-2649">Retrieves the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2650">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2650">Prototype</span></span>

```C
ULONG tx_time_get(VOID);
```
### <a name="description"></a><span data-ttu-id="38207-2651">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2651">Description</span></span>

<span data-ttu-id="38207-2652">이 서비스는 내부 시스템 클록의 내용을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2652">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="38207-2653">각 타이머 틱은 내부 시스템 클록을 1씩 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2653">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="38207-2654">초기화하는 동안 시스템 클록이 0으로 설정되며 서비스 ***tx_time_set*** 에 따라 특정 값으로 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2654">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2655">각 타이머 틱이 나타내는 실제 시간은 애플리케이션마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2655">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2656">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2656">Parameters</span></span>

<span data-ttu-id="38207-2657">None</span><span class="sxs-lookup"><span data-stu-id="38207-2657">None</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2658">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2658">Return Values</span></span>

- <span data-ttu-id="38207-2659">system clock ticks: 원하는 대로 실행할 수 있는 내부 시스템 클록 값입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2659">system clock ticks: Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2660">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2660">Allowed From</span></span>

<span data-ttu-id="38207-2661">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2661">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2662">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2662">Preemption Possible</span></span>

<span data-ttu-id="38207-2663">예</span><span class="sxs-lookup"><span data-stu-id="38207-2663">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-2664">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2664">Example</span></span>

```C
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time =  tx_time_get();

/* Current time now contains a copy of the internal system
   clock. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2665">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2665">See Also</span></span>

- <span data-ttu-id="38207-2666">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="38207-2666">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="38207-2667">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="38207-2667">tx_time_set</span></span>

<span data-ttu-id="38207-2668">현재 시간 설정</span><span class="sxs-lookup"><span data-stu-id="38207-2668">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2669">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2669">Prototype</span></span>

```C
VOID tx_time_set(ULONG new_time);
```
### <a name="description"></a><span data-ttu-id="38207-2670">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2670">Description</span></span>

<span data-ttu-id="38207-2671">이 서비스는 내부 시스템 클록을 지정된 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2671">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="38207-2672">각 타이머 틱은 내부 시스템 클록을 1씩 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2672">Each timer-tick increases the internal system clock by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2673">각 타이머 틱이 나타내는 실제 시간은 애플리케이션마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2673">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2674">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2674">Parameters</span></span>

- <span data-ttu-id="38207-2675">**new_time**: 시스템 클록에 배치할 새 시간입니다. 유효한 값 범위는 0-0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2675">**new_time**: New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2676">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2676">Return Values</span></span>

<span data-ttu-id="38207-2677">None</span><span class="sxs-lookup"><span data-stu-id="38207-2677">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2678">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2678">Allowed From</span></span>

<span data-ttu-id="38207-2679">스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2679">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2680">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2680">Preemption Possible</span></span>

<span data-ttu-id="38207-2681">예</span><span class="sxs-lookup"><span data-stu-id="38207-2681">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-2682">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2682">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
   interrupt. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2683">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2683">See Also</span></span>

- <span data-ttu-id="38207-2684">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="38207-2684">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="38207-2685">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="38207-2685">tx_timer_activate</span></span>

<span data-ttu-id="38207-2686">애플리케이션 타이머 활성화</span><span class="sxs-lookup"><span data-stu-id="38207-2686">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2687">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2687">Prototype</span></span>

```C
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-2688">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2688">Description</span></span>

<span data-ttu-id="38207-2689">이 서비스는 지정된 애플리케이션 타이머를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2689">This service activates the specified application timer.</span></span> <span data-ttu-id="38207-2690">동시에 만료되는 타이머의 만료 루틴은 활성화된 순서대로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2690">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="38207-2691">만료된 일회성 타이머를 다시 활성화하려면 먼저 **tx_timer_change** 를 통해 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2691">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2692">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2692">Parameters</span></span>

- <span data-ttu-id="38207-2693">**timer_ptr**: 이전에 만든 애플리케이션 타이머를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2693">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2694">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2694">Return Values</span></span>

- <span data-ttu-id="38207-2695">**TX_SUCCESS**:(0x00) 애플리케이션 타이머를 활성화했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2695">**TX_SUCCESS**: (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="38207-2696">**TX_TIMER_ERROR**:(0x15) 잘못된 애플리케이션 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2696">**TX_TIMER_ERROR**: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="38207-2697">**TX_ACTIVATE_ERROR**:(0x17) 타이머가 이미 활성 상태이거나 이미 만료된 일회성 타이머입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2697">**TX_ACTIVATE_ERROR**: (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2698">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2698">Allowed From</span></span>

<span data-ttu-id="38207-2699">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2699">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2700">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2700">Preemption Possible</span></span>

<span data-ttu-id="38207-2701">예</span><span class="sxs-lookup"><span data-stu-id="38207-2701">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-2702">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2702">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Activate an application timer. Assume that the
   application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now active. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2703">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2703">See Also</span></span>

- <span data-ttu-id="38207-2704">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="38207-2704">tx_timer_change</span></span>
- <span data-ttu-id="38207-2705">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="38207-2705">tx_timer_create</span></span>
- <span data-ttu-id="38207-2706">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="38207-2706">tx_timer_deactivate</span></span>
- <span data-ttu-id="38207-2707">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2707">tx_timer_delete</span></span>
- <span data-ttu-id="38207-2708">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2708">tx_timer_info_get</span></span>
- <span data-ttu-id="38207-2709">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2709">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="38207-2710">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2710">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="38207-2711">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="38207-2711">tx_timer_change</span></span>

<span data-ttu-id="38207-2712">애플리케이션 타이머 변경</span><span class="sxs-lookup"><span data-stu-id="38207-2712">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2713">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2713">Prototype</span></span>

```C
UINT tx_timer_change(TX_TIMER *timer_ptr,
                          ULONG initial_ticks, ULONG reschedule_ticks);
```
### <a name="description"></a><span data-ttu-id="38207-2714">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2714">Description</span></span>

<span data-ttu-id="38207-2715">이 서비스는 지정된 애플리케이션 타이머의 만료 특성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2715">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="38207-2716">이 서비스를 호출하기 전에 타이머를 비활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2716">The timer must be deactivated prior to calling this service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2717">타이머를 다시 시작하려면 이 서비스 다음에 **tx_timer_activate** 서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2717">A call to the **tx_timer_activate** service is required after this service in order to start the timer again.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2718">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2718">Parameters</span></span>

- <span data-ttu-id="38207-2719">**timer_ptr**: 타이머 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2719">**timer_ptr**: Pointer to a timer control block.</span></span>
- <span data-ttu-id="38207-2720">**initial_ticks**: 타이머 만료의 초기 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2720">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="38207-2721">유효한 값 범위는 1-0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2721">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="38207-2722">**reschedule_ticks**: 첫 번째 이후의 모든 타이머 만료에 대한 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2722">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="38207-2723">이 매개 변수에 0은 지정하면 타이머가 일회성 타이머가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2723">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="38207-2724">그렇지 않고, 정기적인 타이머의 경우 유효한 값의 범위는 1부터 0xFFFFFFFF까지입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2724">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="38207-2725">만료된 일회성 타이머를 다시 활성화하려면 먼저 **tx_timer_change** 를 통해 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2725">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2726">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2726">Return Values</span></span>

- <span data-ttu-id="38207-2727">**TX_SUCCESS**:(0x00) 애플리케이션 타이머를 변경했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2727">**TX_SUCCESS**: (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="38207-2728">TX_TIMER_ERROR:(0x15) 잘못된 애플리케이션 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2728">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="38207-2729">TX_TICK_ERROR:(0x16) 초기 틱에 잘못된 값(0)이 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2729">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="38207-2730">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2730">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2731">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2731">Allowed From</span></span>

<span data-ttu-id="38207-2732">스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2732">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2733">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2733">Preemption Possible</span></span>

<span data-ttu-id="38207-2734">예</span><span class="sxs-lookup"><span data-stu-id="38207-2734">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-2735">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2735">Example</span></span>

```C
TX_TIMER         my_timer;
UINT             status;

/* Change a previously created and now deactivated timer
   to expire every 50 timer ticks, including the initial
   expiration. */
status =  tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
   changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```
### <a name="see-also"></a><span data-ttu-id="38207-2736">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2736">See Also</span></span>

- <span data-ttu-id="38207-2737">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="38207-2737">tx_timer_activate</span></span>
- <span data-ttu-id="38207-2738">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="38207-2738">tx_timer_create</span></span>
- <span data-ttu-id="38207-2739">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="38207-2739">tx_timer_deactivate</span></span>
- <span data-ttu-id="38207-2740">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2740">tx_timer_delete</span></span>
- <span data-ttu-id="38207-2741">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2741">tx_timer_info_get</span></span>
- <span data-ttu-id="38207-2742">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2742">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="38207-2743">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2743">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="38207-2744">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="38207-2744">tx_timer_create</span></span>

<span data-ttu-id="38207-2745">애플리케이션 타이머 만들기</span><span class="sxs-lookup"><span data-stu-id="38207-2745">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2746">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2746">Prototype</span></span>

```C
UINT tx_timer_create(TX_TIMER *timer_ptr, CHAR *name_ptr,
                          VOID (*expiration_function)(ULONG),
                          ULONG expiration_input, ULONG initial_ticks,
                          ULONG reschedule_ticks, UINT auto_activate)
```
### <a name="description"></a><span data-ttu-id="38207-2747">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2747">Description</span></span>

<span data-ttu-id="38207-2748">이 서비스는 지정된 만료 함수 및 주기에 따라 애플리케이션 타이머를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2748">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2749">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2749">Parameters</span></span>

- <span data-ttu-id="38207-2750">**timer_ptr**: 타이머 제어 블록을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2750">**timer_ptr**: Pointer to a timer control block</span></span>
- <span data-ttu-id="38207-2751">**name_ptr**: 타이머 이름을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2751">**name_ptr**: Pointer to the name of the timer.</span></span>
- <span data-ttu-id="38207-2752">**expiration_function**: 타이머가 만료될 때 호출할 애플리케이션 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2752">**expiration_function**: Application function to call when the timer expires.</span></span>
- <span data-ttu-id="38207-2753">**expiration_input**: 타이머가 만료될 때 만료 함수에 전달할 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2753">**expiration_input**: Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="38207-2754">**initial_ticks**: 타이머 만료의 초기 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2754">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="38207-2755">유효한 값 범위는 1-0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2755">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="38207-2756">**reschedule_ticks**: 첫 번째 이후의 모든 타이머 만료에 대한 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2756">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="38207-2757">이 매개 변수에 0은 지정하면 타이머가 일회성 타이머가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2757">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="38207-2758">그렇지 않고, 정기적인 타이머의 경우 유효한 값의 범위는 1부터 0xFFFFFFFF까지입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2758">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="38207-2759">만료된 일회성 타이머를 다시 활성화하려면 먼저 tx_timer_change를 통해 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2759">After a one-shot timer expires, it must be reset via tx_timer_change before it can be activated again.</span></span>

- <span data-ttu-id="38207-2760">**auto_activate**: 만드는 동안 타이머가 자동으로 활성화되는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2760">**auto_activate**: Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="38207-2761">이 값이 **TX_AUTO_ACTIVATE**(0x01)이면 타이머가 활성 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2761">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="38207-2762">그렇지 않고 **TX_NO_ACTIVATE**(0x00) 값을 선택하면 타이머가 비활성 상태로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2762">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="38207-2763">이 경우 타이머를 실제로 시작하려면 후속 **_tx_timer_activate_** 서비스 호출이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2763">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2764">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2764">Return Values</span></span>

- <span data-ttu-id="38207-2765">**TX_SUCCESS**:(0x00) 애플리케이션 타이머를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2765">**TX_SUCCESS**: (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="38207-2766">TX_TIMER_ERROR:(0x15) 잘못된 애플리케이션 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2766">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="38207-2767">포인터가 NULL이거나 타이머가 이미 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2767">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="38207-2768">TX_TICK_ERROR:(0x16) 초기 틱에 잘못된 값(0)이 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2768">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="38207-2769">TX_ACTIVATE_ERROR:(0x17) 잘못된 활성화를 선택했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2769">TX_ACTIVATE_ERROR: (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="38207-2770">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2770">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2771">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2771">Allowed From</span></span>

<span data-ttu-id="38207-2772">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="38207-2772">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2773">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2773">Preemption Possible</span></span>

<span data-ttu-id="38207-2774">예</span><span class="sxs-lookup"><span data-stu-id="38207-2774">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-2775">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2775">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Create an application timer that executes
   "my_timer_function" after 100 ticks initially and then
   after every 25 ticks. This timer is specified to start
   immediately! */
status =  tx_timer_create(&my_timer,"my_timer_name",
                my_timer_function, 0x1234, 100, 25,
                TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
   be called 100 timer ticks later and then called every
   25 timer ticks. Note that the value 0x1234 is passed to
   my_timer_function every time it is called. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2776">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2776">See Also</span></span>

- <span data-ttu-id="38207-2777">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="38207-2777">tx_timer_activate</span></span>
- <span data-ttu-id="38207-2778">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="38207-2778">tx_timer_change</span></span>
- <span data-ttu-id="38207-2779">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="38207-2779">tx_timer_deactivate</span></span>
- <span data-ttu-id="38207-2780">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2780">tx_timer_delete</span></span>
- <span data-ttu-id="38207-2781">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2781">tx_timer_info_get</span></span>
- <span data-ttu-id="38207-2782">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2782">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="38207-2783">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2783">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="38207-2784">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="38207-2784">tx_timer_deactivate</span></span>

<span data-ttu-id="38207-2785">애플리케이션 타이머 비활성화</span><span class="sxs-lookup"><span data-stu-id="38207-2785">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2786">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2786">Prototype</span></span>

```C
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="38207-2787">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2787">Description</span></span>

<span data-ttu-id="38207-2788">이 서비스는 지정된 애플리케이션 타이머를 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2788">This service deactivates the specified application timer.</span></span> <span data-ttu-id="38207-2789">타이머가 이미 비활성화된 경우 이 서비스는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2789">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2790">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2790">Parameters</span></span> 

- <span data-ttu-id="38207-2791">**timer_ptr**: 이전에 만든 애플리케이션 타이머를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2791">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2792">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2792">Return Values</span></span>

- <span data-ttu-id="38207-2793">**TX_SUCCESS**:(0x00) 애플리케이션 타이머를 비활성화했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2793">**TX_SUCCESS**: (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="38207-2794">TX_TIMER_ERROR:(0x15) 잘못된 애플리케이션 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2794">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2795">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2795">Allowed From</span></span>

<span data-ttu-id="38207-2796">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2796">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2797">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2797">Preemption Possible</span></span>

<span data-ttu-id="38207-2798">예</span><span class="sxs-lookup"><span data-stu-id="38207-2798">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-2799">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2799">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Deactivate an application timer. Assume that the
   application timer has already been created. */
status =  tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now deactivated. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2800">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2800">See Also</span></span>

- <span data-ttu-id="38207-2801">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="38207-2801">tx_timer_activate</span></span>
- <span data-ttu-id="38207-2802">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="38207-2802">tx_timer_change</span></span>
- <span data-ttu-id="38207-2803">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="38207-2803">tx_timer_create</span></span>
- <span data-ttu-id="38207-2804">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2804">tx_timer_delete</span></span>
- <span data-ttu-id="38207-2805">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2805">tx_timer_info_get</span></span>
- <span data-ttu-id="38207-2806">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2806">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="38207-2807">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2807">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="38207-2808">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2808">tx_timer_delete</span></span>

<span data-ttu-id="38207-2809">애플리케이션 타이머 삭제</span><span class="sxs-lookup"><span data-stu-id="38207-2809">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2810">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2810">Prototype</span></span>

```C
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-2811">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2811">Description</span></span>

<span data-ttu-id="38207-2812">이 서비스는 지정된 애플리케이션 타이머를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2812">This service deletes the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2813">애플리케이션은 삭제된 타이머를 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2813">It is the application’s responsibility to prevent use of a deleted timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2814">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2814">Parameters</span></span> 

- <span data-ttu-id="38207-2815">**timer_ptr**: 이전에 만든 애플리케이션 타이머를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2815">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2816">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2816">Return Values</span></span>

- <span data-ttu-id="38207-2817">**TX_SUCCESS**:(0x00) 애플리케이션 타이머를 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2817">**TX_SUCCESS**: (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="38207-2818">TX_TIMER_ERROR:(0x15) 잘못된 애플리케이션 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2818">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="38207-2819">TX_CALLER_ERROR:(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2819">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2820">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2820">Allowed From</span></span>

<span data-ttu-id="38207-2821">스레드</span><span class="sxs-lookup"><span data-stu-id="38207-2821">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2822">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2822">Preemption Possible</span></span>

<span data-ttu-id="38207-2823">예</span><span class="sxs-lookup"><span data-stu-id="38207-2823">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-2824">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2824">Example</span></span>

```c
TX_TIMER     my_timer;
UINT         status;

/* Delete application timer. Assume that the application
   timer has already been created. */
status =  tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2825">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2825">See Also</span></span>

- <span data-ttu-id="38207-2826">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="38207-2826">tx_timer_activate</span></span>
- <span data-ttu-id="38207-2827">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="38207-2827">tx_timer_change</span></span>
- <span data-ttu-id="38207-2828">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="38207-2828">tx_timer_create</span></span>
- <span data-ttu-id="38207-2829">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="38207-2829">tx_timer_deactivate</span></span>
- <span data-ttu-id="38207-2830">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2830">tx_timer_info_get</span></span>
- <span data-ttu-id="38207-2831">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2831">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="38207-2832">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2832">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="38207-2833">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2833">tx_timer_info_get</span></span>

<span data-ttu-id="38207-2834">애플리케이션 타이머에 대한 정보 검색</span><span class="sxs-lookup"><span data-stu-id="38207-2834">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2835">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2835">Prototype</span></span>

```C
UINT tx_timer_info_get(TX_TIMER *timer_ptr, CHAR **name,
                          UINT *active, ULONG *remaining_ticks,
                          ULONG *reschedule_ticks,
                          TX_TIMER **next_timer)
```
### <a name="description"></a><span data-ttu-id="38207-2836">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2836">Description</span></span>

<span data-ttu-id="38207-2837">이 서비스는 지정된 애플리케이션 타이머에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2837">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2838">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2838">Parameters</span></span>

- <span data-ttu-id="38207-2839">**timer_ptr**: 이전에 만든 애플리케이션 타이머를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2839">**timer_ptr**: Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="38207-2840">**name**: 타이머 이름에 대한 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2840">**name**: Pointer to destination for the pointer to the timer’s name.</span></span>
- <span data-ttu-id="38207-2841">**active**: 타이머 활성 표시의 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2841">**active**: Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="38207-2842">타이머가 비활성 상태이거나 타이머 자체에서 이 서비스를 호출하는 경우에는 TX_FALSE 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2842">If the timer is inactive or this service is called from the timer itself, a TX_FALSE value is returned.</span></span> <span data-ttu-id="38207-2843">그렇지 않고 타이머가 활성 상태인 경우에는 TX_TRUE 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2843">Otherwise, if the timer is active, a TX_TRUE value is returned.</span></span>
- <span data-ttu-id="38207-2844">**remaining_ticks**: 타이머 만료까지 남은 타이머 틱 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2844">**remaining_ticks**: Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="38207-2845">**reschedule_ticks**: 이 타이머를 자동으로 다시 예약하는 데 사용될 타이머 틱 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2845">**reschedule_ticks**: Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="38207-2846">이 값이 0이면 타이머는 일회성이며 다시 예약되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2846">If the value is zero, then the timer is a one-shot and won’t be rescheduled.</span></span>
- <span data-ttu-id="38207-2847">**next_timer**: 다음에 만들 애플리케이션 타이머 포인터 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2847">**next_timer**: Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="38207-2848">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2848">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2849">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2849">Return Values</span></span>

- <span data-ttu-id="38207-2850">**TX_SUCCESS**:(0x00) 타이머 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2850">**TX_SUCCESS**: (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="38207-2851">TX_TIMER_ERROR:(0x15) 잘못된 애플리케이션 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2851">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2852">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2852">Allowed From</span></span>

<span data-ttu-id="38207-2853">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2853">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="38207-2854">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="38207-2854">Preemption Possible</span></span>

<span data-ttu-id="38207-2855">예</span><span class="sxs-lookup"><span data-stu-id="38207-2855">No</span></span>

### <a name="example"></a><span data-ttu-id="38207-2856">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2856">Example</span></span>

```C
TX_TIMER     my_timer;
CHAR         *name;
UINT         active;
ULONG        remaining_ticks;
ULONG        reschedule_ticks;
TX_TIMER     *next_timer;
UINT         status;

/* Retrieve information about the previously created
   application timer "my_timer." */
status =  tx_timer_info_get(&my_timer, &name,
                          &active,&remaining_ticks,
                &reschedule_ticks,
                         &next_timer);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2857">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2857">See Also</span></span>

- <span data-ttu-id="38207-2858">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="38207-2858">tx_timer_activate</span></span>
- <span data-ttu-id="38207-2859">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="38207-2859">tx_timer_change</span></span>
- <span data-ttu-id="38207-2860">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="38207-2860">tx_timer_create</span></span>
- <span data-ttu-id="38207-2861">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="38207-2861">tx_timer_deactivate</span></span>
- <span data-ttu-id="38207-2862">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2862">tx_timer_delete</span></span>
- <span data-ttu-id="38207-2863">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2863">tx_timer_info_get</span></span>
- <span data-ttu-id="38207-2864">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2864">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="38207-2865">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2865">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="38207-2866">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2866">tx_timer_performance_info_get</span></span> 

<span data-ttu-id="38207-2867">타이머 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-2867">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2868">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2868">Prototype</span></span>

```C
UINT  tx_timer_performance_info_get(TX_TIMER *timer_ptr,
        ULONG *activates, ULONG *reactivates,
        ULONG *deactivates, ULONG *expirations,
        ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="38207-2869">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2869">Description</span></span>

<span data-ttu-id="38207-2870">이 서비스는 지정된 애플리케이션 타이머에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2870">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2871">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_TIMER_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2871">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2872">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2872">Parameters</span></span> 

- <span data-ttu-id="38207-2873">**timer_ptr**: 이전에 만든 타이머를 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2873">**timer_ptr**: Pointer to previously created timer.</span></span>
- <span data-ttu-id="38207-2874">**activates**: 이 타이머에서 수행된 활성화 요청 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2874">**activates**: Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="38207-2875">**reactivates**: 이 주기적인 타이머에서 수행되는 자동 다시 활성화 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2875">**reactivates**: Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="38207-2876">**deactivates**: 이 타이머에서 수행되는 비활성화 요청 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2876">**deactivates**: Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="38207-2877">**expirations**: 이 타이머의 만료 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2877">**expirations**: Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="38207-2878">**expiration_adjusts**: 이 타이머에서 수행되는 내부 만료 조정 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2878">**expiration_adjusts**: Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="38207-2879">이러한 조정은 기본 타이머 목록 크기보다 큰 타이머에 대한 타이머 인터럽트 처리에서 수행됩니다(기본적으로 만료 시간이 32개 틱보다 큰 타이머).</span><span class="sxs-lookup"><span data-stu-id="38207-2879">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2880">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2880">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2881">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2881">Return Values</span></span>

- <span data-ttu-id="38207-2882">**TX_SUCCESS**:(0x00) 타이머 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2882">**TX_SUCCESS**: (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="38207-2883">**TX_PTR_ERROR**:(0x03) 잘못된 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2883">**TX_PTR_ERROR**: (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="38207-2884">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2884">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2885">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2885">Allowed From</span></span>

<span data-ttu-id="38207-2886">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2886">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-2887">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2887">Example</span></span>

```C
TX_TIMER     my_timer;
ULONG        activates;
ULONG        reactivates;
ULONG        deactivates;
ULONG        expirations;
ULONG        expiration_adjusts;

/* Retrieve performance information on the previously created
   timer.  */
status =  tx_timer_performance_info_get(&my_timer, &activates,
                &reactivates,&deactivates, &expirations,
                &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2888">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2888">See Also</span></span>

- <span data-ttu-id="38207-2889">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="38207-2889">tx_timer_activate</span></span>
- <span data-ttu-id="38207-2890">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="38207-2890">tx_timer_change</span></span>
- <span data-ttu-id="38207-2891">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="38207-2891">tx_timer_create</span></span>
- <span data-ttu-id="38207-2892">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="38207-2892">tx_timer_deactivate</span></span>
- <span data-ttu-id="38207-2893">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2893">tx_timer_delete</span></span>
- <span data-ttu-id="38207-2894">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2894">tx_timer_info_get</span></span>
- <span data-ttu-id="38207-2895">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2895">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="38207-2896">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2896">tx_timer_performance_system_info_get</span></span> 

<span data-ttu-id="38207-2897">타이머 시스템 성능 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-2897">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2898">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2898">Prototype</span></span>

```C
UINT  tx_timer_performance_system_info_get(ULONG *activates,
        ULONG *reactivates, ULONG *deactivates,
        ULONG *expirations, ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="38207-2899">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2899">Description</span></span>

<span data-ttu-id="38207-2900">이 서비스는 시스템의 모든 애플리케이션 타이머에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2900">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2901">ThreadX SMP 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하려면 정의된 **TX_TIMER_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2901">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2902">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2902">Parameters</span></span>

- <span data-ttu-id="38207-2903">**activates**: 모든 타이머에서 수행되는 총 활성화 요청 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2903">**activates**: Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="38207-2904">**reactivates**: 모든 주기적인 타이머에서 수행되는 총 자동 다시 활성화 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2904">**reactivates**: Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="38207-2905">**deactivates**: 모든 타이머에서 수행되는 총 비활성화 요청 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2905">**deactivates**: Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="38207-2906">**expirations**: 모든 타이머의 총 만료 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2906">**expirations**: Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="38207-2907">**expiration_adjusts**: 모든 타이머에서 수행되는 총 내부 만료 조정 수 대상을 가리키는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2907">**expiration_adjusts**: Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="38207-2908">이러한 조정은 기본 타이머 목록 크기보다 큰 타이머에 대한 타이머 인터럽트 처리에서 수행됩니다(기본적으로 만료 시간이 32개 틱보다 큰 타이머).</span><span class="sxs-lookup"><span data-stu-id="38207-2908">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2909">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2909">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2910">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2910">Return Values</span></span>

- <span data-ttu-id="38207-2911">**TX_SUCCESS**:(0x00) 타이머 시스템 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2911">**TX_SUCCESS**: (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="38207-2912">**TX_FEATURE_NOT_ENABLED**:(0xFF) 시스템이 성능 정보를 사용하도록 설정하여 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2912">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2913">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2913">Allowed From</span></span>

<span data-ttu-id="38207-2914">초기화, 스레드, 타이머 및 ISR</span><span class="sxs-lookup"><span data-stu-id="38207-2914">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="38207-2915">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2915">Example</span></span>

```C
ULONG     activates;
ULONG     reactivates;
ULONG     deactivates;
ULONG     expirations;
ULONG     expiration_adjusts;

/* Retrieve performance information on all previously created
   timers.  */
status =  tx_timer_performance_system_info_get(&activates,
                &reactivates, &deactivates, &expirations,
                &expiration_adjusts);
/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="38207-2916">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2916">See Also</span></span>

- <span data-ttu-id="38207-2917">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="38207-2917">tx_timer_activate</span></span>
- <span data-ttu-id="38207-2918">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="38207-2918">tx_timer_change</span></span>
- <span data-ttu-id="38207-2919">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="38207-2919">tx_timer_create</span></span>
- <span data-ttu-id="38207-2920">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="38207-2920">tx_timer_deactivate</span></span>
- <span data-ttu-id="38207-2921">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="38207-2921">tx_timer_delete</span></span>
- <span data-ttu-id="38207-2922">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2922">tx_timer_info_get</span></span>
- <span data-ttu-id="38207-2923">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="38207-2923">tx_timer_performance_info_get</span></span>

## <a name="tx_timer_smp_core_exclude"></a><span data-ttu-id="38207-2924">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="38207-2924">tx_timer_smp_core_exclude</span></span>

<span data-ttu-id="38207-2925">코어 세트에서 타이머 실행 제외</span><span class="sxs-lookup"><span data-stu-id="38207-2925">Exclude timer execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2926">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2926">Prototype</span></span>

```C
UINT  tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="38207-2927">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2927">Description</span></span>

<span data-ttu-id="38207-2928">이 함수는 지정된 타이머가 "exclusion_map"이라는 비트 맵에 지정된 코어에서 실행되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2928">This function excludes the specified timer from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="38207-2929">"exclusion_map"의 각 비트는 코어를 나타냅니다(비트 0은 코어 0을 나타냄).</span><span class="sxs-lookup"><span data-stu-id="38207-2929">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="38207-2930">비트가 설정된 경우 해당 코어는 지정된 타이머 실행에서 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2930">If the bit is set, the corresponding core is excluded from executing the specified timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38207-2931">프로세서 제외를 사용하면 가장 최적 상태로 일치하는 항목을 찾기 위해 코어 매핑 논리에 대한 스레드의 추가 처리가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2931">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="38207-2932">이 처리는 준비 상태인 스레드 수에 따라 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2932">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2933">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2933">Parameters</span></span>

- <span data-ttu-id="38207-2934">**timer_ptr**: 코어 제외를 변경하기 위한 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2934">**timer_ptr**: Pointer to timer to change the core exclusion.</span></span>
- <span data-ttu-id="38207-2935">**exclusion_map**: sit 비트에서 코어가 제외되었음을 나타내는 비트 맵입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2935">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="38207-2936">0 값을 제공하면 타이머가 어떤 코어에서도 실행될 수 있습니다(기본값).</span><span class="sxs-lookup"><span data-stu-id="38207-2936">Supplying a 0 value enables the timer to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2937">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2937">Return Values</span></span>

- <span data-ttu-id="38207-2938">**TX_SUCCESS**(0X00) 코어를 성공적으로 제외했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2938">**TX_SUCCESS** (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="38207-2939">**TX_TIMER_ERROR**(0x0E) 잘못된 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2939">**TX_TIMER_ERROR** (0x0E) Invalid timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2940">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2940">Allowed From</span></span>

<span data-ttu-id="38207-2941">초기화, ISR, 스레드 및 타이머</span><span class="sxs-lookup"><span data-stu-id="38207-2941">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="38207-2942">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2942">Example</span></span>

```C
/* Exclude core 0 for "Timer 0". */
tx_timer_smp_core_exclude(&timer_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="38207-2943">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2943">See Also</span></span>

- <span data-ttu-id="38207-2944">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="38207-2944">tx_timer_smp_core_exclude_get</span></span>

## <a name="tx_timer_smp_core_exclude_get"></a><span data-ttu-id="38207-2945">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="38207-2945">tx_timer_smp_core_exclude_get</span></span>

<span data-ttu-id="38207-2946">타이머의 현재 코어 제외 가져오기</span><span class="sxs-lookup"><span data-stu-id="38207-2946">Gets the timer's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="38207-2947">프로토타입</span><span class="sxs-lookup"><span data-stu-id="38207-2947">Prototype</span></span>

```C
UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="38207-2948">Description</span><span class="sxs-lookup"><span data-stu-id="38207-2948">Description</span></span>

<span data-ttu-id="38207-2949">이 함수는 현재 코어 제외 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2949">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="38207-2950">매개 변수</span><span class="sxs-lookup"><span data-stu-id="38207-2950">Parameters</span></span>

- <span data-ttu-id="38207-2951">**timer_ptr**: 코어 제외를 검색할 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2951">**timer_ptr**: Pointer to timer from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="38207-2952">**exclusion_map_ptr**: 현재 코어 제외 비트 맵에 대한 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2952">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="38207-2953">반환 값</span><span class="sxs-lookup"><span data-stu-id="38207-2953">Return Values</span></span>

- <span data-ttu-id="38207-2954">TX_SUCCESS:(0x00) 타이머의 코어 제외를 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2954">TX_SUCCESS: (0x00) Successful retrieval of timer's core exclusion.</span></span>
- <span data-ttu-id="38207-2955">TX_TIMER_ERROR:(0x0E) 잘못된 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2955">TX_TIMER_ERROR: (0x0E) Invalid timer pointer.</span></span>
- <span data-ttu-id="38207-2956">TX_PTR_ERROR:(0x03) 잘못된 제외 대상 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="38207-2956">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="38207-2957">허용 위치</span><span class="sxs-lookup"><span data-stu-id="38207-2957">Allowed From</span></span>

<span data-ttu-id="38207-2958">초기화, ISR, 스레드 및 타이머</span><span class="sxs-lookup"><span data-stu-id="38207-2958">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="38207-2959">예제</span><span class="sxs-lookup"><span data-stu-id="38207-2959">Example</span></span>

```C
ULONGexcluded_cores;

/* Retrieve the core exclusion for "Timer 0". */
tx_timer_smp_core_exclude_get(&timer_0,&excluded_cores);
```
### <a name="see-also"></a><span data-ttu-id="38207-2960">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38207-2960">See Also</span></span>

- <span data-ttu-id="38207-2961">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="38207-2961">tx_timer_smp_core_exclude</span></span>