---
title: Azure RTOS ThreadX 이해
description: Azure ThreadX는 깊게 포함된 애플리케이션용으로 특별히 설계된 고급 RTOS(실시간 운영 체제)입니다.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: e786e5bf1f434ec9543823dee8784b677a2b371f
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171389"
---
# <a name="overview-of-azure-rtos-threadx"></a><span data-ttu-id="80953-103">Azure RTOS ThreadX 개요</span><span class="sxs-lookup"><span data-stu-id="80953-103">Overview of Azure RTOS ThreadX</span></span>

<span data-ttu-id="80953-104">Azure RTOS ThreadX는 심층 임베디드, 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 Microsoft의 고급 산업용 RTOS(실시간 운영 체제)입니다.</span><span class="sxs-lookup"><span data-stu-id="80953-104">Azure RTOS ThreadX is Microsoft's advanced industrial grade Real-Time Operating System (RTOS) designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="80953-105">Azure RTOS ThreadX는 고급 예약, 통신, 동기화, 타이머, 메모리 관리 및 인터럽트 관리 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-105">Azure RTOS ThreadX provides advanced scheduling, communication, synchronization, timer, memory management, and interrupt management facilities.</span></span> <span data-ttu-id="80953-106">또한 Azure RTOS ThreadX에는 picokernel™ 아키텍처, preemption-threshold™ 예약, event-chaining™, 실행 프로파일링, 성능 메트릭 및 시스템 이벤트 추적을 포함한 많은 고급 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-106">In addition, Azure RTOS ThreadX has many advanced features, including its picokernel™ architecture, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics, and system event tracing.</span></span> <span data-ttu-id="80953-107">Azure RTOS ThreadX는 뛰어난 사용 편의성과 함께 가장 까다로운 임베디드 애플리케이션에 이상적인 선택입니다.</span><span class="sxs-lookup"><span data-stu-id="80953-107">Combined with its superior ease-of-use, Azure RTOS ThreadX is the ideal choice for the most demanding of embedded applications.</span></span> <span data-ttu-id="80953-108">2017년 현재 Azure RTOS ThreadX는 소비자 디바이스, 의료 전자 제품 및 산업 제어 장비를 포함한 다양한 제품에 62억 개 이상이 배포되었습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-108">As of 2017, Azure RTOS ThreadX has over 6.2 billion deployments, in a wide variety of products, including consumer devices, medical electronics, and industrial control equipment.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="80953-109">API 프로토콜</span><span class="sxs-lookup"><span data-stu-id="80953-109">API Protocols</span></span>

### <a name="azure-rtos-threadx-services"></a><span data-ttu-id="80953-110">Azure RTOS ThreadX 서비스</span><span class="sxs-lookup"><span data-stu-id="80953-110">Azure RTOS ThreadX Services</span></span>

* <span data-ttu-id="80953-111">동적 스레드 만들기</span><span class="sxs-lookup"><span data-stu-id="80953-111">Dynamic thread creation</span></span>
* <span data-ttu-id="80953-112">스레드 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="80953-112">No limits on the number of threads</span></span>
* <span data-ttu-id="80953-113">주 스레드 API에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="80953-113">Main thread APIs include:</span></span>
  * <span data-ttu-id="80953-114">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="80953-114">tx_thread_create</span></span>
  * <span data-ttu-id="80953-115">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="80953-115">tx_thread_delete</span></span>
  * <span data-ttu-id="80953-116">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="80953-116">tx_thread_preemption_change</span></span>
  * <span data-ttu-id="80953-117">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="80953-117">tx_thread_priority_change</span></span>
  * <span data-ttu-id="80953-118">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="80953-118">tx_thread_relinquish</span></span>
  * <span data-ttu-id="80953-119">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="80953-119">tx_thread_reset</span></span>
  * <span data-ttu-id="80953-120">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="80953-120">tx_thread_resume</span></span>
  * <span data-ttu-id="80953-121">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="80953-121">tx_thread_sleep</span></span>
  * <span data-ttu-id="80953-122">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="80953-122">tx_thread_suspend</span></span>
  * <span data-ttu-id="80953-123">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="80953-123">tx_thread_terminate</span></span>
  * <span data-ttu-id="80953-124">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="80953-124">tx_thread_wait_abort</span></span>
* <span data-ttu-id="80953-125">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="80953-125">Additional information and performance APIs</span></span>

### <a name="message-queues"></a><span data-ttu-id="80953-126">메시지 큐</span><span class="sxs-lookup"><span data-stu-id="80953-126">Message Queues</span></span>

* <span data-ttu-id="80953-127">동적 큐 만들기</span><span class="sxs-lookup"><span data-stu-id="80953-127">Dynamic queue creation</span></span>
* <span data-ttu-id="80953-128">큐 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="80953-128">No limits on the number of queues</span></span>
* <span data-ttu-id="80953-129">값(또는 포인터를 통한 참조)으로 복사된 메시지</span><span class="sxs-lookup"><span data-stu-id="80953-129">Messages copied by value (or by reference via pointer)</span></span>
* <span data-ttu-id="80953-130">1 ~ 16개의 32비트 단어의 메시지 크기</span><span class="sxs-lookup"><span data-stu-id="80953-130">Message sizes from 1 to 16 32-bit words</span></span>
* <span data-ttu-id="80953-131">비거나 가득 찼을 때 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="80953-131">Optional thread suspension on empty and full</span></span>
* <span data-ttu-id="80953-132">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="80953-132">Optional timeout on all suspension</span></span>
* <span data-ttu-id="80953-133">주 메시지 큐 API에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="80953-133">Main message queue APIs include:</span></span>
  * <span data-ttu-id="80953-134">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="80953-134">tx_queue_create</span></span>
  * <span data-ttu-id="80953-135">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="80953-135">tx_queue_delete</span></span>
  * <span data-ttu-id="80953-136">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="80953-136">tx_queue_flush</span></span>
  * <span data-ttu-id="80953-137">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="80953-137">tx_queue_front_send</span></span>
  * <span data-ttu-id="80953-138">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="80953-138">tx_queue_receive</span></span>
  * <span data-ttu-id="80953-139">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="80953-139">tx_queue_send_notify</span></span>
* <span data-ttu-id="80953-140">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="80953-140">Additional information and performance APIs</span></span>

### <a name="counting-semaphores"></a><span data-ttu-id="80953-141">세마포 수 계산</span><span class="sxs-lookup"><span data-stu-id="80953-141">Counting Semaphores</span></span>

* <span data-ttu-id="80953-142">동적 세마포 만들기</span><span class="sxs-lookup"><span data-stu-id="80953-142">Dynamic semaphore creation</span></span>
* <span data-ttu-id="80953-143">세마포 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="80953-143">No limits on the number of semaphores</span></span>
* <span data-ttu-id="80953-144">32비트 세마포 계산(0 ~ 4,294,967,295)</span><span class="sxs-lookup"><span data-stu-id="80953-144">32-bit counting semaphores (0 to 4,294,967,295)</span></span>
* <span data-ttu-id="80953-145">소비자-생산자 또는 리소스 보호 지원</span><span class="sxs-lookup"><span data-stu-id="80953-145">Supports consumer-producer or resource protection</span></span>
* <span data-ttu-id="80953-146">세마포를 사용할 수 없을 때 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="80953-146">Optional thread suspension when semaphore unavailable</span></span>
* <span data-ttu-id="80953-147">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="80953-147">Optional timeout on all suspension</span></span>
* <span data-ttu-id="80953-148">주 세마포 API에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="80953-148">Main semaphore APIs include:</span></span>
  * <span data-ttu-id="80953-149">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="80953-149">tx_semaphore_create</span></span>
  * <span data-ttu-id="80953-150">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="80953-150">tx_semaphore_delete</span></span>
  * <span data-ttu-id="80953-151">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="80953-151">tx_semaphore_get</span></span>
  * <span data-ttu-id="80953-152">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="80953-152">tx_semaphore_put</span></span>
  * <span data-ttu-id="80953-153">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="80953-153">tx_semaphore_put_notify</span></span>
* <span data-ttu-id="80953-154">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="80953-154">Additional information and performance APIs</span></span>

### <a name="mutexes"></a><span data-ttu-id="80953-155">뮤텍스</span><span class="sxs-lookup"><span data-stu-id="80953-155">Mutexes</span></span>

* <span data-ttu-id="80953-156">동적 뮤텍스 만들기</span><span class="sxs-lookup"><span data-stu-id="80953-156">Dynamic mutex creation</span></span>
* <span data-ttu-id="80953-157">뮤텍스 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="80953-157">No limits on the number of mutexes</span></span>
* <span data-ttu-id="80953-158">중첩된 리소스 보호 지원</span><span class="sxs-lookup"><span data-stu-id="80953-158">Nested resource protection supported</span></span>
* <span data-ttu-id="80953-159">선택적 우선 순위 상속 지원</span><span class="sxs-lookup"><span data-stu-id="80953-159">Optional priority inheritance supported</span></span>
* <span data-ttu-id="80953-160">뮤텍스를 사용할 수 없을 때 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="80953-160">Optional thread suspension when mutex unavailable</span></span>
* <span data-ttu-id="80953-161">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="80953-161">Optional timeout on all suspension</span></span>
* <span data-ttu-id="80953-162">기본 뮤텍스 API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-162">Main mutex APIs include:</span></span>
  * <span data-ttu-id="80953-163">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="80953-163">tx_mutex_create</span></span>
  * <span data-ttu-id="80953-164">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="80953-164">tx_mutex_delete</span></span>
  * <span data-ttu-id="80953-165">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="80953-165">tx_mutex_get</span></span>
  * <span data-ttu-id="80953-166">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="80953-166">tx_mutex_put</span></span>
* <span data-ttu-id="80953-167">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="80953-167">Additional information and performance APIs</span></span>

### <a name="event-flags"></a><span data-ttu-id="80953-168">이벤트 플래그</span><span class="sxs-lookup"><span data-stu-id="80953-168">Event Flags</span></span>

* <span data-ttu-id="80953-169">동적 이벤트 플래그 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="80953-169">Dynamic event flag group creation</span></span>
* <span data-ttu-id="80953-170">이벤트 플래그 그룹 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="80953-170">No limits on the number of event flag groups</span></span>
* <span data-ttu-id="80953-171">단일 스레드 또는 다중 스레드 동기화</span><span class="sxs-lookup"><span data-stu-id="80953-171">Synchronization of one thread or multiple threads</span></span>
* <span data-ttu-id="80953-172">원자성 가져오기 및 지우기 지원</span><span class="sxs-lookup"><span data-stu-id="80953-172">Atomic get and clear supported</span></span>
* <span data-ttu-id="80953-173">AND/OR 이벤트 세트의 선택적 다중 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="80953-173">Optional multithread suspension on AND/OR set of events</span></span>
* <span data-ttu-id="80953-174">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="80953-174">Optional timeout on all suspension</span></span>
* <span data-ttu-id="80953-175">기본 이벤트 플래그 API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-175">Main event flag APIs include:</span></span>
  * <span data-ttu-id="80953-176">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="80953-176">tx_event_flags_create</span></span>
  * <span data-ttu-id="80953-177">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="80953-177">tx_event_flags_delete</span></span>
  * <span data-ttu-id="80953-178">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="80953-178">tx_event_flags_get</span></span>
  * <span data-ttu-id="80953-179">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="80953-179">tx_event_flags_set</span></span>
  * <span data-ttu-id="80953-180">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="80953-180">tx_event_flags_set_notify</span></span>
* <span data-ttu-id="80953-181">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="80953-181">Additional information and performance APIs</span></span>

### <a name="block-memory-pools"></a><span data-ttu-id="80953-182">메모리 풀 차단</span><span class="sxs-lookup"><span data-stu-id="80953-182">Block Memory Pools</span></span>

* <span data-ttu-id="80953-183">동적 블록 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="80953-183">Dynamic block pool creation</span></span>
* <span data-ttu-id="80953-184">블록 풀 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="80953-184">No limits on the number of block pools</span></span>
* <span data-ttu-id="80953-185">고정 크기 블록 크기 또는 풀 크기 제한 없음</span><span class="sxs-lookup"><span data-stu-id="80953-185">No limits on size of fixed-size blocks or size of pool</span></span>
* <span data-ttu-id="80953-186">가능한 가장 빠른 메모리 할당/할당 취소</span><span class="sxs-lookup"><span data-stu-id="80953-186">Fastest possible memory allocation/deal-location</span></span>
* <span data-ttu-id="80953-187">비었을 때 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="80953-187">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="80953-188">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="80953-188">Optional timeout on all suspension</span></span>
* <span data-ttu-id="80953-189">기본 블록 풀 API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-189">Main block pool APIs include:</span></span>
  * <span data-ttu-id="80953-190">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="80953-190">tx_block_pool_create</span></span>
  * <span data-ttu-id="80953-191">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="80953-191">tx_block_pool_delete</span></span>
  * <span data-ttu-id="80953-192">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="80953-192">tx_block_allocate</span></span>
  * <span data-ttu-id="80953-193">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="80953-193">tx_block_release</span></span>
* <span data-ttu-id="80953-194">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="80953-194">Additional information and performance APIs</span></span>

### <a name="byte-memory-pools"></a><span data-ttu-id="80953-195">바이트 메모리 풀</span><span class="sxs-lookup"><span data-stu-id="80953-195">Byte Memory Pools</span></span>

* <span data-ttu-id="80953-196">동적 바이트 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="80953-196">Dynamic byte pool creation</span></span>
* <span data-ttu-id="80953-197">바이트 풀 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="80953-197">No limits on the number of byte pools</span></span>
* <span data-ttu-id="80953-198">바이트 풀 크기 제한 없음</span><span class="sxs-lookup"><span data-stu-id="80953-198">No limits on size of byte pool</span></span>
* <span data-ttu-id="80953-199">가장 유연한 가변 길이 메모리 할당/할당 취소</span><span class="sxs-lookup"><span data-stu-id="80953-199">Most flexible variable-length memory allocation/deallocation</span></span>
* <span data-ttu-id="80953-200">할당 크기 인근 지원</span><span class="sxs-lookup"><span data-stu-id="80953-200">Allocation size locality supported</span></span>
* <span data-ttu-id="80953-201">비었을 때 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="80953-201">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="80953-202">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="80953-202">Optional timeout on all suspension</span></span>
* <span data-ttu-id="80953-203">기본 바이트 풀 API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-203">Main byte pool APIs include:</span></span>
  * <span data-ttu-id="80953-204">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="80953-204">tx_byte_pool_create</span></span>
  * <span data-ttu-id="80953-205">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="80953-205">tx_byte_pool_delete</span></span>
  * <span data-ttu-id="80953-206">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="80953-206">tx_byte_allocate</span></span>
  * <span data-ttu-id="80953-207">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="80953-207">tx_byte_release</span></span>
* <span data-ttu-id="80953-208">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="80953-208">Additional information and performance APIs</span></span>

### <a name="application-timers"></a><span data-ttu-id="80953-209">애플리케이션 타이머</span><span class="sxs-lookup"><span data-stu-id="80953-209">Application Timers</span></span>

* <span data-ttu-id="80953-210">동적 타이머 만들기</span><span class="sxs-lookup"><span data-stu-id="80953-210">Dynamic timer creation</span></span>
* <span data-ttu-id="80953-211">타이머 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="80953-211">No limits on the number of timers</span></span>
* <span data-ttu-id="80953-212">정기 또는 원샷 타이머 지원</span><span class="sxs-lookup"><span data-stu-id="80953-212">Periodic or one-shot timers supported</span></span>
* <span data-ttu-id="80953-213">정기 타이머의 초기 만료 값은 다를 수 있음</span><span class="sxs-lookup"><span data-stu-id="80953-213">Periodic timers may have different initial expiration value</span></span>
* <span data-ttu-id="80953-214">타이머 활성화 또는 비활성화 시 검색 없음</span><span class="sxs-lookup"><span data-stu-id="80953-214">No searching on timer activation or deactivation</span></span>
* <span data-ttu-id="80953-215">모든 타이머가 한 대의 하드웨어 타이머 인터럽트에서 구동</span><span class="sxs-lookup"><span data-stu-id="80953-215">All timers driven from one hardware timer interrupt</span></span>
* <span data-ttu-id="80953-216">기본 타이머 API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-216">Main timer APIs include:</span></span>
  * <span data-ttu-id="80953-217">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="80953-217">tx_timer_create</span></span>
  * <span data-ttu-id="80953-218">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="80953-218">tx_timer_delete</span></span>
  * <span data-ttu-id="80953-219">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="80953-219">tx_timer_activate</span></span>
  * <span data-ttu-id="80953-220">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="80953-220">tx_timer_change</span></span>
  * <span data-ttu-id="80953-221">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="80953-221">tx_timer_deactivate</span></span>
* <span data-ttu-id="80953-222">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="80953-222">Additional information and performance APIs</span></span>

### <a name="azure-rtos-threadx-core-scheduler"></a><span data-ttu-id="80953-223">Azure RTOS ThreadX Core Scheduler</span><span class="sxs-lookup"><span data-stu-id="80953-223">Azure RTOS ThreadX Core Scheduler</span></span>

* <span data-ttu-id="80953-224">최소 2KB FLASH, 1KB RAM 메모리 공간</span><span class="sxs-lookup"><span data-stu-id="80953-224">Minimal 2KB FLASH,1KB RAM footprint</span></span>
* <span data-ttu-id="80953-225">마이크로 초 미만의 빠른 컨텍스트 전환</span><span class="sxs-lookup"><span data-stu-id="80953-225">Fast, sub-microsecond context-switch</span></span>
* <span data-ttu-id="80953-226">스레드 수에 관계없이 완전 결정적</span><span class="sxs-lookup"><span data-stu-id="80953-226">Fully deterministic regardless of number of threads</span></span>
* <span data-ttu-id="80953-227">우선 순위 기반의 완전한 선점 예약</span><span class="sxs-lookup"><span data-stu-id="80953-227">Priority-based, fully preemptive-scheduling</span></span>
* <span data-ttu-id="80953-228">32개의 기본 우선 순위 수준, 선택적으로 최대 1024개의 수준</span><span class="sxs-lookup"><span data-stu-id="80953-228">32 default priority levels, optionally up to 1024 levels</span></span>
* <span data-ttu-id="80953-229">우선 순위 수준 내 협력 예약(FIFO)</span><span class="sxs-lookup"><span data-stu-id="80953-229">Cooperative scheduling within priority level (FIFO)</span></span>
* <span data-ttu-id="80953-230">Preemption-threshold 기술</span><span class="sxs-lookup"><span data-stu-id="80953-230">Preemption-threshold technology</span></span>
* <span data-ttu-id="80953-231">다음을 포함하는 선택적 타이머 서비스:</span><span class="sxs-lookup"><span data-stu-id="80953-231">Optional timer services, including:</span></span>
  * <span data-ttu-id="80953-232">스레드별 선택적 시간-조각</span><span class="sxs-lookup"><span data-stu-id="80953-232">Per-thread optional time-slice</span></span>
  * <span data-ttu-id="80953-233">모든 차단에 대한 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="80953-233">Optional timeout on all blocking</span></span>
  * <span data-ttu-id="80953-234">하드웨어 타이머 인터럽트에 API 필요</span><span class="sxs-lookup"><span data-stu-id="80953-234">APIs Requires on hardware timer interrupt</span></span>
* <span data-ttu-id="80953-235">실행 프로파일링</span><span class="sxs-lookup"><span data-stu-id="80953-235">Execution profiling</span></span>
* <span data-ttu-id="80953-236">시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="80953-236">System-level Trace</span></span>
* <span data-ttu-id="80953-237">여러 표준으로 인증된 안전</span><span class="sxs-lookup"><span data-stu-id="80953-237">Safety certified to many standards</span></span>

## <a name="most-deployed-rtos"></a><span data-ttu-id="80953-238">가장 많이 배포된 RTOS</span><span class="sxs-lookup"><span data-stu-id="80953-238">Most deployed RTOS</span></span>

<span data-ttu-id="80953-239">선도적인 M2M 시장 인텔리전스 회사인 VDC Research에 따르면 Azure RTOS ThreadX는 전 세계적으로 62억 개 이상의 배포를 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-239">Azure RTOS ThreadX has over 6.2 billion deployments worldwide, according to the leading M2M market intelligence firm, VDC Research.</span></span> <span data-ttu-id="80953-240">Azure RTOS ThreadX의 인기는 신뢰도, 품질, 크기, 성능, 고급 기능, 사용 편의성 및 전반적인 출시 시간 이점에 대한 증거입니다.</span><span class="sxs-lookup"><span data-stu-id="80953-240">The popularity of Azure RTOS ThreadX is a testament to its reliability, quality, size, performance, advanced features, ease-of-use, and overall time-to-market advantages.</span></span>

> <span data-ttu-id="80953-241">*"우리는 회사 창립 이래 무선 및 IoT 시장에서 THREADX의 성장 궤적을 따라왔으며, THREADX의 광범위한 업계 채택에 점점 더 깊은 인상을 받았습니다."*</span><span class="sxs-lookup"><span data-stu-id="80953-241">*“We have followed the growth trajectory of THREADX in the wireless and IoT markets since the company’s founding, and are increasingly impressed by the widespread industry adoption of THREADX.”*</span></span> <span data-ttu-id="80953-242">– Chris Rommel, 부사장, VDC Research</span><span class="sxs-lookup"><span data-stu-id="80953-242">– Chris Rommel, Executive Vice President, VDC Research</span></span>

## <a name="small-footprint"></a><span data-ttu-id="80953-243">적은 메모리 공간</span><span class="sxs-lookup"><span data-stu-id="80953-243">Small footprint</span></span>

<span data-ttu-id="80953-244">Azure RTOS ThreadX는 매우 적은 2KB 명령 영역과 RAM 1KB의 최소 메모리 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-244">Azure RTOS ThreadX requires a remarkably small 2KB instruction area and 1KB of RAM for its minimal footprint.</span></span> <span data-ttu-id="80953-245">이는 주로 계층화되지 않은 picokernel™ 아키텍처와 자동 크기 조정으로 인해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-245">This is largely due to its non-layered picokernel™ architecture and automatic scaling.</span></span> <span data-ttu-id="80953-246">자동 크기 조정은 애플리케이션에서 사용되는 서비스(및 지원 인프라)만 링크 타임에서 최종 이미지에 포함된다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-246">Automatic scaling means that only the services (and supporting infrastructure) used by the application are included in the final image at link time.</span></span>

<span data-ttu-id="80953-247">몇 가지 일반적인 Azure RTOS ThreadX 크기 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-247">Here are some typical Azure RTOS ThreadX size characteristics.</span></span>

|<span data-ttu-id="80953-248">Azure RTOS ThreadX 서비스</span><span class="sxs-lookup"><span data-stu-id="80953-248">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="80953-249">일반적인 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="80953-249">Typical Size in Bytes</span></span>  |
|---------|---------|
|<span data-ttu-id="80953-250">Core Services(필수)</span><span class="sxs-lookup"><span data-stu-id="80953-250">Core Services (Require)</span></span> |<span data-ttu-id="80953-251">2,000</span><span class="sxs-lookup"><span data-stu-id="80953-251">2,000</span></span>  |
|<span data-ttu-id="80953-252">큐 서비스</span><span class="sxs-lookup"><span data-stu-id="80953-252">Queue Services</span></span>  |<span data-ttu-id="80953-253">900</span><span class="sxs-lookup"><span data-stu-id="80953-253">900</span></span>  |
|<span data-ttu-id="80953-254">이벤트 플래그 서비스</span><span class="sxs-lookup"><span data-stu-id="80953-254">Event Flag Services</span></span>  |<span data-ttu-id="80953-255">900</span><span class="sxs-lookup"><span data-stu-id="80953-255">900</span></span>  |
|<span data-ttu-id="80953-256">세마포 서비스</span><span class="sxs-lookup"><span data-stu-id="80953-256">Semaphore Services</span></span>  |<span data-ttu-id="80953-257">450</span><span class="sxs-lookup"><span data-stu-id="80953-257">450</span></span>  |
|<span data-ttu-id="80953-258">뮤텍스 서비스</span><span class="sxs-lookup"><span data-stu-id="80953-258">Mutex Services</span></span>  |<span data-ttu-id="80953-259">1,200</span><span class="sxs-lookup"><span data-stu-id="80953-259">1,200</span></span>  |
|<span data-ttu-id="80953-260">블록 메모리 서비스</span><span class="sxs-lookup"><span data-stu-id="80953-260">Block Memory Services</span></span>  |<span data-ttu-id="80953-261">550</span><span class="sxs-lookup"><span data-stu-id="80953-261">550</span></span>  |
|<span data-ttu-id="80953-262">바이트 메모리 서비스</span><span class="sxs-lookup"><span data-stu-id="80953-262">Byte Memory Services</span></span>  |<span data-ttu-id="80953-263">900</span><span class="sxs-lookup"><span data-stu-id="80953-263">900</span></span>  |

## <a name="fast-execution"></a><span data-ttu-id="80953-264">고속 실행</span><span class="sxs-lookup"><span data-stu-id="80953-264">Fast execution</span></span>

<span data-ttu-id="80953-265">Azure RTOS ThreadX는 대부분의 인기 있는 프로세서에서 초소형 컨텍스트 전환을 달성하며 전반적으로 다른 상용 RTOS보다 훨씬 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="80953-265">Azure RTOS ThreadX achieves a sub-microsecond context switch on most popular processors and is significantly faster overall than other commercial RTOSes.</span></span> <span data-ttu-id="80953-266">Azure RTOS ThreadX는 속도가 빠를 뿐만 아니라 결정성도 뛰어납니다.</span><span class="sxs-lookup"><span data-stu-id="80953-266">In addition to being fast, Azure RTOS ThreadX is also highly deterministic.</span></span> <span data-ttu-id="80953-267">200개의 스레드가 준비되어 있든 단 한 개만 준비되어 있든 동일한 빠른 성능을 달성합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-267">It achieves the same fast performance whether there are 200 threads ready, or just one.</span></span>

<span data-ttu-id="80953-268">Azure RTOS ThreadX의 일반적인 성능 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-268">Here are some typical performance characteristics of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="80953-269">빠른 부팅: Azure RTOS ThreadX는 120 사이클 미만으로 부팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="80953-269">Fast Boot: Azure RTOS ThreadX boots in less than 120 cycles.</span></span>
* <span data-ttu-id="80953-270">선택적 기본 오류 검사 제거: 컴파일 타임에 기본 Azure RTOS ThreadX 오류 검사를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-270">Optional Removal of basic error checking: Basic Azure RTOS ThreadX error checking can be skipped at compile time.</span></span> <span data-ttu-id="80953-271">이는 애플리케이션 코드가 확인되고 더 이상 각 매개 변수에 대한 오류 검사가 필요하지 않을 때 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-271">This can be useful when the application code is verified and no longer requires error checking on each parameter.</span></span> <span data-ttu-id="80953-272">이는 시스템 차원이 아닌 컴파일 단위에서 수행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-272">Note that this can be done on a compilation unit, rather than system-wide.</span></span>
* <span data-ttu-id="80953-273">Picokernel™ 디자인: 서비스가 서로 계층화되지 않으므로 불필요한 함수 호출 오버 헤드가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="80953-273">Picokernel™ Design: Services are not layered on each other, thus eliminating unnecessary function call overhead.</span></span>
* <span data-ttu-id="80953-274">\*최적화된 인터럽트 처리: 선점이 필요한 경우가 아니면 ISR 진입/종료 시 스크래치 레지스터만 저장/복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="80953-274">\*Optimized Interrupt Processing: Only scratch registers are saved/restored upon ISR entry/exit, unless preemption is necessary.</span></span>
* <span data-ttu-id="80953-275">최적화된 API 처리:</span><span class="sxs-lookup"><span data-stu-id="80953-275">Optimized API Processing:</span></span>

    |<span data-ttu-id="80953-276">Azure RTOS ThreadX 서비스</span><span class="sxs-lookup"><span data-stu-id="80953-276">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="80953-277">서비스 시간(마이크로초)\*</span><span class="sxs-lookup"><span data-stu-id="80953-277">Service Time in Microseconds\*</span></span>  |
    |---------|---------|
    |<span data-ttu-id="80953-278">스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="80953-278">Thread Suspend</span></span>  |<span data-ttu-id="80953-279">0.6</span><span class="sxs-lookup"><span data-stu-id="80953-279">0.6</span></span>  |
    |<span data-ttu-id="80953-280">스레드 계속하기</span><span class="sxs-lookup"><span data-stu-id="80953-280">Thread Resume</span></span>  |<span data-ttu-id="80953-281">0.6</span><span class="sxs-lookup"><span data-stu-id="80953-281">0.6</span></span>  |
    |<span data-ttu-id="80953-282">큐 송신</span><span class="sxs-lookup"><span data-stu-id="80953-282">Queue Send</span></span>  |<span data-ttu-id="80953-283">0.3</span><span class="sxs-lookup"><span data-stu-id="80953-283">0.3</span></span>  |
    |<span data-ttu-id="80953-284">큐 수신</span><span class="sxs-lookup"><span data-stu-id="80953-284">Queue Receive</span></span>  |<span data-ttu-id="80953-285">0.3</span><span class="sxs-lookup"><span data-stu-id="80953-285">0.3</span></span>  |
    |<span data-ttu-id="80953-286">세마포 가져오기</span><span class="sxs-lookup"><span data-stu-id="80953-286">Get Semaphore</span></span>  |<span data-ttu-id="80953-287">0.2</span><span class="sxs-lookup"><span data-stu-id="80953-287">0.2</span></span>  |
    |<span data-ttu-id="80953-288">세마포 배치</span><span class="sxs-lookup"><span data-stu-id="80953-288">Put Semaphore</span></span>  |<span data-ttu-id="80953-289">0.2</span><span class="sxs-lookup"><span data-stu-id="80953-289">0.2</span></span>  |
    |<span data-ttu-id="80953-290">컨텍스트 전환</span><span class="sxs-lookup"><span data-stu-id="80953-290">Context Switch</span></span>  |<span data-ttu-id="80953-291">0.4</span><span class="sxs-lookup"><span data-stu-id="80953-291">0.4</span></span>  |
    |<span data-ttu-id="80953-292">인터럽트 응답</span><span class="sxs-lookup"><span data-stu-id="80953-292">Interrupt Response</span></span>  |<span data-ttu-id="80953-293">0.0 – 0.6</span><span class="sxs-lookup"><span data-stu-id="80953-293">0.0 – 0.6</span></span>  |

    <span data-ttu-id="80953-294">\**200MHz로 실행되는 일반적인 프로세서에 따른 성능 수치*.</span><span class="sxs-lookup"><span data-stu-id="80953-294">\**Performance figures based on typical processor running at 200MHz*.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="80953-295">고급 기술</span><span class="sxs-lookup"><span data-stu-id="80953-295">Advanced technology</span></span>

<span data-ttu-id="80953-296">Azure RTOS ThreadX는 가장 중요한 기능이 preemption-threshold 예약인 고급 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="80953-296">Azure RTOS ThreadX is advanced technology whose most notable feature is preemption-threshold scheduling.</span></span> <span data-ttu-id="80953-297">이 기능은 Azure RTOS ThreadX의 고유한 것이며 광범위한 학술 연구의 주제였습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-297">This feature is unique to Azure RTOS ThreadX and has been the subject of extensive academic research.</span></span> <span data-ttu-id="80953-298">예를 들어, Yun Wang(콩코디아 대학교) 및 Manas Saksena(피츠버그 대학교)의 [Preemption Threshold를 사용하여 고정 우선 순위 작업 예약(Scheduling Fixed-Priority Tasks with Preemption Threshold)](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="80953-298">For example, see [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), by Yun Wang, Concordia University, and Manas Saksena, University of Pittsburgh.</span></span>

<span data-ttu-id="80953-299">Azure RTOS ThreadX의 기능을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-299">Consider the capabilities of Azure RTOS ThreadX.</span></span>

* <span data-ttu-id="80953-300">완전하고 포괄적인 멀티태스킹 기능 제공</span><span class="sxs-lookup"><span data-stu-id="80953-300">Complete and Comprehensive Multitasking Facilities</span></span>
  * <span data-ttu-id="80953-301">스레드, 애플리케이션 타이머, 메시지 큐, 세마포 계산, 뮤텍스, 이벤트 플래그, 블록 및 바이트 메모리 풀</span><span class="sxs-lookup"><span data-stu-id="80953-301">Threads, application timers, message queues, counting semaphores, mutexes, event flags, block and byte memory pools</span></span>
* <span data-ttu-id="80953-302">우선 순위 기반의 선점 예약</span><span class="sxs-lookup"><span data-stu-id="80953-302">Priority-Based Preemptive Scheduling</span></span>
* <span data-ttu-id="80953-303">우선 순위 유연성 – 최대 1024개의 우선 순위 수준</span><span class="sxs-lookup"><span data-stu-id="80953-303">Priority Flexibility – Up to 1024 Priority Levels</span></span>
* <span data-ttu-id="80953-304">협력 예약</span><span class="sxs-lookup"><span data-stu-id="80953-304">Cooperative Scheduling</span></span>
* <span data-ttu-id="80953-305">Preemption-Threshold™ – Azure RTOS ThreadX만의 고유한 기능으로 컨텍스트 스위치를 줄이고 예약 가능성을 보장할 수 있습니다(학술 연구 기준).</span><span class="sxs-lookup"><span data-stu-id="80953-305">Preemption-Threshold™ – Unique to Azure RTOS ThreadX, helps reduce context switches and help guarantee schedulability (per academic research)</span></span>
* <span data-ttu-id="80953-306">Azure RTOS ThreadX MODULES를 통한 메모리 보호</span><span class="sxs-lookup"><span data-stu-id="80953-306">Memory Protection via Azure RTOS ThreadX MODULES</span></span>
* <span data-ttu-id="80953-307">완전 결정적</span><span class="sxs-lookup"><span data-stu-id="80953-307">Fully Deterministic</span></span>
* <span data-ttu-id="80953-308">이벤트 추적 – 마지막 *n* 개의 시스템/애플리케이션 이벤트 캡처</span><span class="sxs-lookup"><span data-stu-id="80953-308">Event Trace – Capture last *n* system/application events</span></span>
* <span data-ttu-id="80953-309">Event Chaining™ – 각 Azure RTOS ThreadX 통신 또는 동기화 개체에 대해 애플리케이션별 "알림" 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-309">Event Chaining™ – Register an application-specific “notify” callback function for each Azure RTOS ThreadX communication or synchronization object</span></span>
* <span data-ttu-id="80953-310">선택적 메모리 보호 기능이 있는 Azure RTOS ThreadX MODULES</span><span class="sxs-lookup"><span data-stu-id="80953-310">Azure RTOS ThreadX MODULES with Optional Memory Protection</span></span>
* <span data-ttu-id="80953-311">런타임 성능 메트릭</span><span class="sxs-lookup"><span data-stu-id="80953-311">Run-Time Performance Metrics</span></span>
  * <span data-ttu-id="80953-312">스레드 재개 수</span><span class="sxs-lookup"><span data-stu-id="80953-312">Number of thread resumptions</span></span>
  * <span data-ttu-id="80953-313">스레드 일시 중단 수</span><span class="sxs-lookup"><span data-stu-id="80953-313">Number of thread suspensions</span></span>
  * <span data-ttu-id="80953-314">요청된 스레드 선점 수</span><span class="sxs-lookup"><span data-stu-id="80953-314">Number of solicited thread preemptions</span></span>
  * <span data-ttu-id="80953-315">비동기 스레드 인터럽트 선점 수</span><span class="sxs-lookup"><span data-stu-id="80953-315">Number of asynchronous thread interrupt preemptions</span></span>
  * <span data-ttu-id="80953-316">스레드 우선 순위 반전 수</span><span class="sxs-lookup"><span data-stu-id="80953-316">Number of thread priority inversions</span></span>
  * <span data-ttu-id="80953-317">스레드 포기 수</span><span class="sxs-lookup"><span data-stu-id="80953-317">Number of thread relinquishes</span></span>
* <span data-ttu-id="80953-318">EPK(실행 프로필 키트)</span><span class="sxs-lookup"><span data-stu-id="80953-318">Execution Profile Kit (EPK)</span></span>
* <span data-ttu-id="80953-319">별도의 인터럽트 스택</span><span class="sxs-lookup"><span data-stu-id="80953-319">Separate Interrupt Stack</span></span>
* <span data-ttu-id="80953-320">런타임 스택 분석</span><span class="sxs-lookup"><span data-stu-id="80953-320">Run-Time Stack Analysis</span></span>
* <span data-ttu-id="80953-321">최적화된 타이머 인터럽트 처리</span><span class="sxs-lookup"><span data-stu-id="80953-321">Optimized Timer Interrupt Processing</span></span>

## <a name="multicore-support-amp--smp"></a><span data-ttu-id="80953-322">멀티 코어 지원(AMP 및 SMP)</span><span class="sxs-lookup"><span data-stu-id="80953-322">Multicore support (AMP & SMP)</span></span>

<span data-ttu-id="80953-323">표준 Azure RTOS ThreadX는 종종 AMP(비대칭적 다중 처리) 방식으로 사용되며, Azure RTOS ThreadX 및 애플리케이션(또는 Linux)의 별도 복사본이 각 코어에서 실행되고 공유 메모리 또는 OpenAMP(Azure RTOS ThreadX는 OpenAMP를 지원)와 같은 프로세서 간 통신 메커니즘을 통해 서로 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-323">Standard Azure RTOS ThreadX is often used in an Asymmetric Multiprocessing (AMP) fashion, where a separate copy of Azure RTOS ThreadX and the application (or Linux) execute on each core and communicate with each other via shared memory or an inter-processor communication mechanism such as OpenAMP (Azure RTOS ThreadX supports OpenAMP).</span></span> <span data-ttu-id="80953-324">이는 Azure RTOS ThreadX를 사용하는 가장 일반적인 다중 코어 구성이며 애플리케이션에서 프로세서를 효과적으로 로드할 수 있는 경우 가장 효율적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-324">This is the most typical multicore configuration using Azure RTOS ThreadX and can be the most efficient if the application is able to effectively load the processors.</span></span>

<span data-ttu-id="80953-325">프로세서를 로드하는 것이 매우 동적인 환경에서는 다음 프로세서 제품군에 대해 Azure RTOS ThreadX SMP(대칭적 다중 처리)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-325">For environments where loading the processors is highly dynamic, Azure RTOS ThreadX Symetric Multiprocessing (SMP) is available for the following processor families:</span></span>

* <span data-ttu-id="80953-326">ARM Cortex-Ax</span><span class="sxs-lookup"><span data-stu-id="80953-326">ARM Cortex-Ax</span></span>
* <span data-ttu-id="80953-327">ARM Cortex-Rx</span><span class="sxs-lookup"><span data-stu-id="80953-327">ARM Cortex-Rx</span></span>
* <span data-ttu-id="80953-328">ARM Cortex-A5x 64비트</span><span class="sxs-lookup"><span data-stu-id="80953-328">ARM Cortex-A5x 64-bit</span></span>
* <span data-ttu-id="80953-329">MIPS 34K, 1004K 및 interAptiv</span><span class="sxs-lookup"><span data-stu-id="80953-329">MIPS 34K, 1004K, and interAptiv</span></span>
* <span data-ttu-id="80953-330">PowerPC</span><span class="sxs-lookup"><span data-stu-id="80953-330">PowerPC</span></span>
* <span data-ttu-id="80953-331">Synopsys ARC HS</span><span class="sxs-lookup"><span data-stu-id="80953-331">Synopsys ARC HS</span></span>
* <span data-ttu-id="80953-332">x86</span><span class="sxs-lookup"><span data-stu-id="80953-332">x86</span></span>

<span data-ttu-id="80953-333">Azure RTOS ThreadX SMP는 *n* 개 프로세서에서 동적 부하 분산을 수행하고 모든 Azure RTOS ThreadX 리소스(큐, 세마포, 이벤트 플래그, 메모리 풀 등)를 모든 코어의 모든 스레드에서 액세스할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-333">Azure RTOS ThreadX SMP performs dynamic load balancing across *n* processors and allows all Azure RTOS ThreadX resources (queues, semaphores, event flags, memory pools, etc.) to be accessed by any thread on any core.</span></span> <span data-ttu-id="80953-334">Azure RTOS ThreadX SMP는 모든 코어에서 전체 Azure RTOS ThreadX API를 사용하고 SMP 작업에 적용되는 다음과 같은 새 API를 도입합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-334">Azure RTOS ThreadX SMP enables the complete Azure RTOS ThreadX API on all cores and introduces the following new API’s applicable to SMP operation:</span></span>

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a><span data-ttu-id="80953-335">Azure RTOS ThreadX MODULES를 통한 메모리 보호</span><span class="sxs-lookup"><span data-stu-id="80953-335">Memory protection via Azure RTOS ThreadX Modules</span></span>

<span data-ttu-id="80953-336">Azure RTOS ThreadX MODULES라는 추가 기능 제품을 사용하면 하나 이상의 애플리케이션 스레드를 대상에서 동적으로 로드하고 실행할 수 있는 "모듈"에 묶을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-336">An add-on product called Azure RTOS ThreadX MODULES enables one or more application threads to be bundled into a “Module” that can be dynamically loaded and run (or executed in place) on the target.</span></span>

<span data-ttu-id="80953-337">모듈을 사용하면 필드 업그레이드, 버그 수정 및 프로그램 분할을 사용하여 많은 애플리케이션이 활성 스레드에 필요한 메모리만 차지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-337">Modules enable field upgrade, bug fixing, and program partitioning to allow large applications to occupy only the memory needed by active threads.</span></span>

<span data-ttu-id="80953-338">또한 모듈에는 Azure RTOS ThreadX 자체와 완전히 별개의 주소 공간이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-338">Modules also have a completely separate address space from Azure RTOS ThreadX itself.</span></span> <span data-ttu-id="80953-339">이를 통해 Azure RTOS ThreadX는 모듈 주변에 메모리 보호(MPU 또는 MMU를 통해)를 배치하여 실수로 모듈 외부에 액세스해도 다른 소프트웨어 구성 요소가 손상되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-339">This enables Azure RTOS ThreadX to place memory protection (via MPU or MMU) around the Module such that accidental access outside the module will not be able to corrupt any other software component.</span></span>


## <a name="misra-compliant"></a><span data-ttu-id="80953-340">MISRA 준수</span><span class="sxs-lookup"><span data-stu-id="80953-340">MISRA compliant</span></span>

<span data-ttu-id="80953-341">Azure RTOS ThreadX 및 Azure RTOS ThreadX SMP 소스 코드는 MISRA-C:2004 및 MISRA C:2012를 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-341">Azure RTOS ThreadX and Azure RTOS ThreadX SMP souce code is MISRA-C:2004 and MISRA C:2012 compliant.</span></span> <span data-ttu-id="80953-342">MISRA C는 C 프로그래밍 언어를 사용하는 중요 시스템에 대한 프로그래밍 지침 세트입니다.</span><span class="sxs-lookup"><span data-stu-id="80953-342">MISRA C is a set of programming guidelines for critical systems using the C programming language.</span></span> <span data-ttu-id="80953-343">원래의 MISRA C 지침은 주로 자동차 분야를 대상으로 했지만, MISRA C는 이제 모든 안전 중요 분야에 적용할 수 있는 것으로 널리 인식되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-343">The original MISRA C guidelines were primarily targeted toward automotive applications; however, MISRA C is now widely recognized as being applicable to any safety-critical application.</span></span> <span data-ttu-id="80953-344">Azure RTOS ThreadX는 MISRA-C:2004 및 MISRA C:2012의 모든 필수 및 의무 규칙을 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-344">Azure RTOS ThreadX is compliant with all required and mandatory rules of MISRA-C:2004 and MISRA C:2012.</span></span>

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Misra 인증":::

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="80953-346">대부분의 주요 아키텍처 지원</span><span class="sxs-lookup"><span data-stu-id="80953-346">Supports most popular architectures</span></span>

<span data-ttu-id="80953-347">Azure RTOS ThreadX는 완전한 테스트와 지원을 통해 다음과 같이 대부분의 주요 32/64비트 마이크로프로세서에서 실행되며, 바로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80953-347">Azure RTOS ThreadX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

* <span data-ttu-id="80953-348">아날로그 디바이스: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="80953-348">Analog Devices: SHARC, Blackfin, CM4xx</span></span>
* <span data-ttu-id="80953-349">Andes Core: RISC-V</span><span class="sxs-lookup"><span data-stu-id="80953-349">Andes Core: RISC-V</span></span>
* <span data-ttu-id="80953-350">Ambiqmicro: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="80953-350">Ambiqmicro: Apollo MCUs</span></span>
* <span data-ttu-id="80953-351">ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="80953-351">ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>
* <span data-ttu-id="80953-352">Cadence: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="80953-352">Cadence: Xtensa, Diamond</span></span>
* <span data-ttu-id="80953-353">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="80953-353">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>
* <span data-ttu-id="80953-354">Cypress: RISC-V</span><span class="sxs-lookup"><span data-stu-id="80953-354">Cypress: RISC-V</span></span>
* <span data-ttu-id="80953-355">EnSilica: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="80953-355">EnSilica: eSi-RISC</span></span>
* <span data-ttu-id="80953-356">Infineon: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="80953-356">Infineon: XMC1000, XMC4000, TriCore</span></span>
* <span data-ttu-id="80953-357">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="80953-357">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>
* <span data-ttu-id="80953-358">Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="80953-358">Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>
* <span data-ttu-id="80953-359">Microsemi: RISC-V</span><span class="sxs-lookup"><span data-stu-id="80953-359">Microsemi: RISC-V</span></span>
* <span data-ttu-id="80953-360">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="80953-360">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>
* <span data-ttu-id="80953-361">Renesas: SH, HS, V850, RX, RZ, Synergy</span><span class="sxs-lookup"><span data-stu-id="80953-361">Renesas: SH, HS, V850, RX, RZ, Synergy</span></span>
* <span data-ttu-id="80953-362">Silicon Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="80953-362">Silicon Labs: EFM32</span></span>
* <span data-ttu-id="80953-363">Synopsys: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="80953-363">Synopsys: ARC 600, 700, ARC EM, ARC HS</span></span>
* <span data-ttu-id="80953-364">ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="80953-364">ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>
* <span data-ttu-id="80953-365">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="80953-365">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>
* <span data-ttu-id="80953-366">Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="80953-366">Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>
* <span data-ttu-id="80953-367">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="80953-367">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

## <a name="supports-most-popular-tools"></a><span data-ttu-id="80953-368">가장 널리 사용되는 도구 지원</span><span class="sxs-lookup"><span data-stu-id="80953-368">Supports most popular tools</span></span>

<span data-ttu-id="80953-369">Azure RTOS ThreadX는 IAR의 Embedded Workbench™를 비롯하여 가장 널리 사용되는 임베디드 개발 도구를 지원하며, 가장 포괄적인 Azure RTOS ThreadX 커널 인식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="80953-369">Azure RTOS ThreadX supports most popular embedded development tools, including IAR’s Embedded Workbench™, which also has the most comprehensive Azure RTOS ThreadX kernel awareness available.</span></span> <span data-ttu-id="80953-370">추가 도구 통합에는 GNU(GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore 및 모든 아날로그 디바이스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="80953-370">Additional tool integration includes GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore and all analog devices.</span></span>
