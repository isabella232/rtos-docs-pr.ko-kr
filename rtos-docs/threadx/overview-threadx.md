---
title: Azure RTOS ThreadX 이해
description: Azure ThreadX는 깊게 포함된 애플리케이션용으로 특별히 설계된 고급 RTOS(실시간 운영 체제)입니다.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: acee58d9c48cb7a66993aaa5dc4a565dfe96234d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812162"
---
# <a name="overview-of-azure-rtos-threadx"></a><span data-ttu-id="0c21d-103">Azure RTOS ThreadX 개요</span><span class="sxs-lookup"><span data-stu-id="0c21d-103">Overview of Azure RTOS ThreadX</span></span>

<span data-ttu-id="0c21d-104">Azure RTOS ThreadX는 심층 임베디드, 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 Microsoft의 고급 산업용 RTOS(실시간 운영 체제)입니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-104">Azure RTOS ThreadX is Microsoft's advanced industrial grade Real-Time Operating System (RTOS) designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="0c21d-105">Azure RTOS ThreadX는 고급 예약, 통신, 동기화, 타이머, 메모리 관리 및 인터럽트 관리 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-105">Azure RTOS ThreadX provides advanced scheduling, communication, synchronization, timer, memory management, and interrupt management facilities.</span></span> <span data-ttu-id="0c21d-106">또한 Azure RTOS ThreadX에는 picokernel™ 아키텍처, preemption-threshold™ 예약, event-chaining™, 실행 프로파일링, 성능 메트릭 및 시스템 이벤트 추적을 포함한 많은 고급 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-106">In addition, Azure RTOS ThreadX has many advanced features, including its picokernel™ architecture, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics, and system event tracing.</span></span> <span data-ttu-id="0c21d-107">Azure RTOS ThreadX는 뛰어난 사용 편의성과 함께 가장 까다로운 임베디드 애플리케이션에 이상적인 선택입니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-107">Combined with its superior ease-of-use, Azure RTOS ThreadX is the ideal choice for the most demanding of embedded applications.</span></span> <span data-ttu-id="0c21d-108">2017년 현재 Azure RTOS ThreadX는 소비자 디바이스, 의료 전자 제품 및 산업 제어 장비를 포함한 다양한 제품에 62억 개 이상이 배포되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-108">As of 2017, Azure RTOS ThreadX has over 6.2 billion deployments, in a wide variety of products, including consumer devices, medical electronics, and industrial control equipment.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="0c21d-109">API 프로토콜</span><span class="sxs-lookup"><span data-stu-id="0c21d-109">API Protocols</span></span>

### <a name="azure-rtos-threadx-api"></a><span data-ttu-id="0c21d-110">Azure RTOS ThreadX API</span><span class="sxs-lookup"><span data-stu-id="0c21d-110">Azure RTOS ThreadX API</span></span>

* <span data-ttu-id="0c21d-111">직관적이고 일관적인 API</span><span class="sxs-lookup"><span data-stu-id="0c21d-111">Intuitive and consistent API</span></span>
* <span data-ttu-id="0c21d-112">명사-동사 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="0c21d-112">Noun-verb naming convention</span></span>
* <span data-ttu-id="0c21d-113">모든 API에는 Azure RTOS ThreadX로 쉽게 식별할 수 있도록 *tx_* 가 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-113">All APIs have leading *tx_* to easily identify as Azure RTOS ThreadX</span></span>
* <span data-ttu-id="0c21d-114">차단 API에는 선택적 스레드 시간 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-114">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="0c21d-115">많은 API를 애플리케이션 ISR에서 직접 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-115">Many APIs are directly available from application ISRs</span></span>

### <a name="azure-rtos-threadx-services"></a><span data-ttu-id="0c21d-116">Azure RTOS ThreadX 서비스</span><span class="sxs-lookup"><span data-stu-id="0c21d-116">Azure RTOS ThreadX Services</span></span>

* <span data-ttu-id="0c21d-117">동적 스레드 만들기</span><span class="sxs-lookup"><span data-stu-id="0c21d-117">Dynamic thread creation</span></span>
* <span data-ttu-id="0c21d-118">스레드 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="0c21d-118">No limits on the number of threads</span></span>
* <span data-ttu-id="0c21d-119">주 스레드 API에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-119">Main thread APIs include:</span></span>
  * <span data-ttu-id="0c21d-120">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="0c21d-120">tx_thread_create</span></span>
  * <span data-ttu-id="0c21d-121">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="0c21d-121">tx_thread_delete</span></span>
  * <span data-ttu-id="0c21d-122">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="0c21d-122">tx_thread_preemption_change</span></span>
  * <span data-ttu-id="0c21d-123">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="0c21d-123">tx_thread_priority_change</span></span>
  * <span data-ttu-id="0c21d-124">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="0c21d-124">tx_thread_relinquish</span></span>
  * <span data-ttu-id="0c21d-125">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="0c21d-125">tx_thread_reset</span></span>
  * <span data-ttu-id="0c21d-126">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="0c21d-126">tx_thread_resume</span></span>
  * <span data-ttu-id="0c21d-127">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="0c21d-127">tx_thread_sleep</span></span>
  * <span data-ttu-id="0c21d-128">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="0c21d-128">tx_thread_suspend</span></span>
  * <span data-ttu-id="0c21d-129">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="0c21d-129">tx_thread_terminate</span></span>
  * <span data-ttu-id="0c21d-130">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="0c21d-130">tx_thread_wait_abort</span></span>
* <span data-ttu-id="0c21d-131">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="0c21d-131">Additional information and performance APIs</span></span>

### <a name="message-queues"></a><span data-ttu-id="0c21d-132">메시지 큐</span><span class="sxs-lookup"><span data-stu-id="0c21d-132">Message Queues</span></span>

* <span data-ttu-id="0c21d-133">동적 큐 만들기</span><span class="sxs-lookup"><span data-stu-id="0c21d-133">Dynamic queue creation</span></span>
* <span data-ttu-id="0c21d-134">큐 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="0c21d-134">No limits on the number of queues</span></span>
* <span data-ttu-id="0c21d-135">값(또는 포인터를 통한 참조)으로 복사된 메시지</span><span class="sxs-lookup"><span data-stu-id="0c21d-135">Messages copied by value (or by reference via pointer)</span></span>
* <span data-ttu-id="0c21d-136">1 ~ 16개의 32비트 단어의 메시지 크기</span><span class="sxs-lookup"><span data-stu-id="0c21d-136">Message sizes from 1 to 16 32-bit words</span></span>
* <span data-ttu-id="0c21d-137">비거나 가득 찼을 때 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="0c21d-137">Optional thread suspension on empty and full</span></span>
* <span data-ttu-id="0c21d-138">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="0c21d-138">Optional timeout on all suspension</span></span>
* <span data-ttu-id="0c21d-139">주 메시지 큐 API에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-139">Main message queue APIs include:</span></span>
  * <span data-ttu-id="0c21d-140">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="0c21d-140">tx_queue_create</span></span>
  * <span data-ttu-id="0c21d-141">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="0c21d-141">tx_queue_delete</span></span>
  * <span data-ttu-id="0c21d-142">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="0c21d-142">tx_queue_flush</span></span>
  * <span data-ttu-id="0c21d-143">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="0c21d-143">tx_queue_front_send</span></span>
  * <span data-ttu-id="0c21d-144">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="0c21d-144">tx_queue_receive</span></span>
  * <span data-ttu-id="0c21d-145">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="0c21d-145">tx_queue_send_notify</span></span>
* <span data-ttu-id="0c21d-146">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="0c21d-146">Additional information and performance APIs</span></span>

### <a name="counting-semaphores"></a><span data-ttu-id="0c21d-147">세마포 수 계산</span><span class="sxs-lookup"><span data-stu-id="0c21d-147">Counting Semaphores</span></span>

* <span data-ttu-id="0c21d-148">동적 세마포 만들기</span><span class="sxs-lookup"><span data-stu-id="0c21d-148">Dynamic semaphore creation</span></span>
* <span data-ttu-id="0c21d-149">세마포 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="0c21d-149">No limits on the number of semaphores</span></span>
* <span data-ttu-id="0c21d-150">32비트 세마포 계산(0 ~ 4,294,967,295)</span><span class="sxs-lookup"><span data-stu-id="0c21d-150">32-bit counting semaphores (0 to 4,294,967,295)</span></span>
* <span data-ttu-id="0c21d-151">소비자-생산자 또는 리소스 보호 지원</span><span class="sxs-lookup"><span data-stu-id="0c21d-151">Supports consumer-producer or resource protection</span></span>
* <span data-ttu-id="0c21d-152">세마포를 사용할 수 없을 때 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="0c21d-152">Optional thread suspension when semaphore unavailable</span></span>
* <span data-ttu-id="0c21d-153">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="0c21d-153">Optional timeout on all suspension</span></span>
* <span data-ttu-id="0c21d-154">주 세마포 API에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-154">Main semaphore APIs include:</span></span>
  * <span data-ttu-id="0c21d-155">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="0c21d-155">tx_semaphore_create</span></span>
  * <span data-ttu-id="0c21d-156">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="0c21d-156">tx_semaphore_delete</span></span>
  * <span data-ttu-id="0c21d-157">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="0c21d-157">tx_semaphore_get</span></span>
  * <span data-ttu-id="0c21d-158">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="0c21d-158">tx_semaphore_put</span></span>
  * <span data-ttu-id="0c21d-159">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="0c21d-159">tx_semaphore_put_notify</span></span>
* <span data-ttu-id="0c21d-160">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="0c21d-160">Additional information and performance APIs</span></span>

### <a name="mutexes"></a><span data-ttu-id="0c21d-161">뮤텍스</span><span class="sxs-lookup"><span data-stu-id="0c21d-161">Mutexes</span></span>

* <span data-ttu-id="0c21d-162">동적 뮤텍스 만들기</span><span class="sxs-lookup"><span data-stu-id="0c21d-162">Dynamic mutex creation</span></span>
* <span data-ttu-id="0c21d-163">뮤텍스 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="0c21d-163">No limits on the number of mutexes</span></span>
* <span data-ttu-id="0c21d-164">중첩된 리소스 보호 지원</span><span class="sxs-lookup"><span data-stu-id="0c21d-164">Nested resource protection supported</span></span>
* <span data-ttu-id="0c21d-165">선택적 우선 순위 상속 지원</span><span class="sxs-lookup"><span data-stu-id="0c21d-165">Optional priority inheritance supported</span></span>
* <span data-ttu-id="0c21d-166">뮤텍스를 사용할 수 없을 때 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="0c21d-166">Optional thread suspension when mutex unavailable</span></span>
* <span data-ttu-id="0c21d-167">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="0c21d-167">Optional timeout on all suspension</span></span>
* <span data-ttu-id="0c21d-168">기본 뮤텍스 API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-168">Main mutex APIs include:</span></span>
  * <span data-ttu-id="0c21d-169">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="0c21d-169">tx_mutex_create</span></span>
  * <span data-ttu-id="0c21d-170">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="0c21d-170">tx_mutex_delete</span></span>
  * <span data-ttu-id="0c21d-171">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="0c21d-171">tx_mutex_get</span></span>
  * <span data-ttu-id="0c21d-172">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="0c21d-172">tx_mutex_put</span></span>
* <span data-ttu-id="0c21d-173">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="0c21d-173">Additional information and performance APIs</span></span>

### <a name="event-flags"></a><span data-ttu-id="0c21d-174">이벤트 플래그</span><span class="sxs-lookup"><span data-stu-id="0c21d-174">Event Flags</span></span>

* <span data-ttu-id="0c21d-175">동적 이벤트 플래그 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="0c21d-175">Dynamic event flag group creation</span></span>
* <span data-ttu-id="0c21d-176">이벤트 플래그 그룹 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="0c21d-176">No limits on the number of event flag groups</span></span>
* <span data-ttu-id="0c21d-177">단일 스레드 또는 다중 스레드 동기화</span><span class="sxs-lookup"><span data-stu-id="0c21d-177">Synchronization of one thread or multiple threads</span></span>
* <span data-ttu-id="0c21d-178">원자성 가져오기 및 지우기 지원</span><span class="sxs-lookup"><span data-stu-id="0c21d-178">Atomic get and clear supported</span></span>
* <span data-ttu-id="0c21d-179">AND/OR 이벤트 세트의 선택적 다중 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="0c21d-179">Optional multithread suspension on AND/OR set of events</span></span>
* <span data-ttu-id="0c21d-180">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="0c21d-180">Optional timeout on all suspension</span></span>
* <span data-ttu-id="0c21d-181">기본 이벤트 플래그 API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-181">Main event flag APIs include:</span></span>
  * <span data-ttu-id="0c21d-182">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="0c21d-182">tx_event_flags_create</span></span>
  * <span data-ttu-id="0c21d-183">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="0c21d-183">tx_event_flags_delete</span></span>
  * <span data-ttu-id="0c21d-184">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="0c21d-184">tx_event_flags_get</span></span>
  * <span data-ttu-id="0c21d-185">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="0c21d-185">tx_event_flags_set</span></span>
  * <span data-ttu-id="0c21d-186">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="0c21d-186">tx_event_flags_set_notify</span></span>
* <span data-ttu-id="0c21d-187">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="0c21d-187">Additional information and performance APIs</span></span>

### <a name="block-memory-pools"></a><span data-ttu-id="0c21d-188">메모리 풀 차단</span><span class="sxs-lookup"><span data-stu-id="0c21d-188">Block Memory Pools</span></span>

* <span data-ttu-id="0c21d-189">동적 블록 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="0c21d-189">Dynamic block pool creation</span></span>
* <span data-ttu-id="0c21d-190">블록 풀 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="0c21d-190">No limits on the number of block pools</span></span>
* <span data-ttu-id="0c21d-191">고정 크기 블록 크기 또는 풀 크기 제한 없음</span><span class="sxs-lookup"><span data-stu-id="0c21d-191">No limits on size of fixed-size blocks or size of pool</span></span>
* <span data-ttu-id="0c21d-192">가능한 가장 빠른 메모리 할당/할당 취소</span><span class="sxs-lookup"><span data-stu-id="0c21d-192">Fastest possible memory allocation/deal-location</span></span>
* <span data-ttu-id="0c21d-193">비었을 때 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="0c21d-193">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="0c21d-194">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="0c21d-194">Optional timeout on all suspension</span></span>
* <span data-ttu-id="0c21d-195">기본 블록 풀 API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-195">Main block pool APIs include:</span></span>
  * <span data-ttu-id="0c21d-196">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="0c21d-196">tx_block_pool_create</span></span>
  * <span data-ttu-id="0c21d-197">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="0c21d-197">tx_block_pool_delete</span></span>
  * <span data-ttu-id="0c21d-198">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="0c21d-198">tx_block_allocate</span></span>
  * <span data-ttu-id="0c21d-199">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="0c21d-199">tx_block_release</span></span>
* <span data-ttu-id="0c21d-200">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="0c21d-200">Additional information and performance APIs</span></span>

### <a name="byte-memory-pools"></a><span data-ttu-id="0c21d-201">바이트 메모리 풀</span><span class="sxs-lookup"><span data-stu-id="0c21d-201">Byte Memory Pools</span></span>

* <span data-ttu-id="0c21d-202">동적 바이트 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="0c21d-202">Dynamic byte pool creation</span></span>
* <span data-ttu-id="0c21d-203">바이트 풀 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="0c21d-203">No limits on the number of byte pools</span></span>
* <span data-ttu-id="0c21d-204">바이트 풀 크기 제한 없음</span><span class="sxs-lookup"><span data-stu-id="0c21d-204">No limits on size of byte pool</span></span>
* <span data-ttu-id="0c21d-205">가장 유연한 가변 길이 메모리 할당/할당 취소</span><span class="sxs-lookup"><span data-stu-id="0c21d-205">Most flexible variable-length memory allocation/deallocation</span></span>
* <span data-ttu-id="0c21d-206">할당 크기 인근 지원</span><span class="sxs-lookup"><span data-stu-id="0c21d-206">Allocation size locality supported</span></span>
* <span data-ttu-id="0c21d-207">비었을 때 선택적 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="0c21d-207">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="0c21d-208">모든 일시 중단 시 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="0c21d-208">Optional timeout on all suspension</span></span>
* <span data-ttu-id="0c21d-209">기본 바이트 풀 API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-209">Main byte pool APIs include:</span></span>
  * <span data-ttu-id="0c21d-210">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="0c21d-210">tx_byte_pool_create</span></span>
  * <span data-ttu-id="0c21d-211">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="0c21d-211">tx_byte_pool_delete</span></span>
  * <span data-ttu-id="0c21d-212">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="0c21d-212">tx_byte_allocate</span></span>
  * <span data-ttu-id="0c21d-213">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="0c21d-213">tx_byte_release</span></span>
* <span data-ttu-id="0c21d-214">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="0c21d-214">Additional information and performance APIs</span></span>

### <a name="application-timers"></a><span data-ttu-id="0c21d-215">애플리케이션 타이머</span><span class="sxs-lookup"><span data-stu-id="0c21d-215">Application Timers</span></span>

* <span data-ttu-id="0c21d-216">동적 타이머 만들기</span><span class="sxs-lookup"><span data-stu-id="0c21d-216">Dynamic timer creation</span></span>
* <span data-ttu-id="0c21d-217">타이머 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="0c21d-217">No limits on the number of timers</span></span>
* <span data-ttu-id="0c21d-218">정기 또는 원샷 타이머 지원</span><span class="sxs-lookup"><span data-stu-id="0c21d-218">Periodic or one-shot timers supported</span></span>
* <span data-ttu-id="0c21d-219">정기 타이머의 초기 만료 값은 다를 수 있음</span><span class="sxs-lookup"><span data-stu-id="0c21d-219">Periodic timers may have different initial expiration value</span></span>
* <span data-ttu-id="0c21d-220">타이머 활성화 또는 비활성화 시 검색 없음</span><span class="sxs-lookup"><span data-stu-id="0c21d-220">No searching on timer activation or deactivation</span></span>
* <span data-ttu-id="0c21d-221">모든 타이머가 한 대의 하드웨어 타이머 인터럽트에서 구동</span><span class="sxs-lookup"><span data-stu-id="0c21d-221">All timers driven from one hardware timer interrupt</span></span>
* <span data-ttu-id="0c21d-222">기본 타이머 API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-222">Main timer APIs include:</span></span>
  * <span data-ttu-id="0c21d-223">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="0c21d-223">tx_timer_create</span></span>
  * <span data-ttu-id="0c21d-224">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="0c21d-224">tx_timer_delete</span></span>
  * <span data-ttu-id="0c21d-225">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="0c21d-225">tx_timer_activate</span></span>
  * <span data-ttu-id="0c21d-226">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="0c21d-226">tx_timer_change</span></span>
  * <span data-ttu-id="0c21d-227">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="0c21d-227">tx_timer_deactivate</span></span>
* <span data-ttu-id="0c21d-228">추가 정보 및 성능 API</span><span class="sxs-lookup"><span data-stu-id="0c21d-228">Additional information and performance APIs</span></span>

### <a name="azure-rtos-threadx-core-scheduler"></a><span data-ttu-id="0c21d-229">Azure RTOS ThreadX Core Scheduler</span><span class="sxs-lookup"><span data-stu-id="0c21d-229">Azure RTOS ThreadX Core Scheduler</span></span>

* <span data-ttu-id="0c21d-230">최소 2KB FLASH, 1KB RAM 메모리 공간</span><span class="sxs-lookup"><span data-stu-id="0c21d-230">Minimal 2KB FLASH,1KB RAM footprint</span></span>
* <span data-ttu-id="0c21d-231">마이크로 초 미만의 빠른 컨텍스트 전환</span><span class="sxs-lookup"><span data-stu-id="0c21d-231">Fast, sub-microsecond context-switch</span></span>
* <span data-ttu-id="0c21d-232">스레드 수에 관계없이 완전 결정적</span><span class="sxs-lookup"><span data-stu-id="0c21d-232">Fully deterministic regardless of number of threads</span></span>
* <span data-ttu-id="0c21d-233">우선 순위 기반의 완전한 선점 예약</span><span class="sxs-lookup"><span data-stu-id="0c21d-233">Priority-based, fully preemptive-scheduling</span></span>
* <span data-ttu-id="0c21d-234">32개의 기본 우선 순위 수준, 선택적으로 최대 1024개의 수준</span><span class="sxs-lookup"><span data-stu-id="0c21d-234">32 default priority levels, optionally up to 1024 levels</span></span>
* <span data-ttu-id="0c21d-235">우선 순위 수준 내 협력 예약(FIFO)</span><span class="sxs-lookup"><span data-stu-id="0c21d-235">Cooperative scheduling within priority level (FIFO)</span></span>
* <span data-ttu-id="0c21d-236">Preemption-threshold 기술</span><span class="sxs-lookup"><span data-stu-id="0c21d-236">Preemption-threshold technology</span></span>
* <span data-ttu-id="0c21d-237">다음을 포함하는 선택적 타이머 서비스:</span><span class="sxs-lookup"><span data-stu-id="0c21d-237">Optional timer services, including:</span></span>
  * <span data-ttu-id="0c21d-238">스레드별 선택적 시간-조각</span><span class="sxs-lookup"><span data-stu-id="0c21d-238">Per-thread optional time-slice</span></span>
  * <span data-ttu-id="0c21d-239">모든 차단에 대한 선택적 시간 제한</span><span class="sxs-lookup"><span data-stu-id="0c21d-239">Optional timeout on all blocking</span></span>
  * <span data-ttu-id="0c21d-240">하드웨어 타이머 인터럽트에 API 필요</span><span class="sxs-lookup"><span data-stu-id="0c21d-240">APIs Requires on hardware timer interrupt</span></span>
* <span data-ttu-id="0c21d-241">실행 프로파일링</span><span class="sxs-lookup"><span data-stu-id="0c21d-241">Execution profiling</span></span>
* <span data-ttu-id="0c21d-242">시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="0c21d-242">System-level Trace</span></span>
* <span data-ttu-id="0c21d-243">여러 표준으로 인증된 안전</span><span class="sxs-lookup"><span data-stu-id="0c21d-243">Safety certified to many standards</span></span>

## <a name="most-deployed-rtos"></a><span data-ttu-id="0c21d-244">가장 많이 배포된 RTOS</span><span class="sxs-lookup"><span data-stu-id="0c21d-244">Most deployed RTOS</span></span>

<span data-ttu-id="0c21d-245">선도적인 M2M 시장 인텔리전스 회사인 VDC Research에 따르면 Azure RTOS ThreadX는 전 세계적으로 62억 개 이상의 배포를 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-245">Azure RTOS ThreadX has over 6.2 billion deployments worldwide, according to the leading M2M market intelligence firm, VDC Research.</span></span> <span data-ttu-id="0c21d-246">Azure RTOS ThreadX의 인기는 신뢰도, 품질, 크기, 성능, 고급 기능, 사용 편의성 및 전반적인 출시 시간 이점에 대한 증거입니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-246">The popularity of Azure RTOS ThreadX is a testament to its reliability, quality, size, performance, advanced features, ease-of-use, and overall time-to-market advantages.</span></span>

> <span data-ttu-id="0c21d-247">*"우리는 회사 창립 이래 무선 및 IoT 시장에서 THREADX의 성장 궤적을 따라왔으며, THREADX의 광범위한 업계 채택에 점점 더 깊은 인상을 받았습니다."*</span><span class="sxs-lookup"><span data-stu-id="0c21d-247">*“We have followed the growth trajectory of THREADX in the wireless and IoT markets since the company’s founding, and are increasingly impressed by the widespread industry adoption of THREADX.”*</span></span> <span data-ttu-id="0c21d-248">– Chris Rommel, 부사장, VDC Research</span><span class="sxs-lookup"><span data-stu-id="0c21d-248">– Chris Rommel, Executive Vice President, VDC Research</span></span>

## <a name="small-footprint"></a><span data-ttu-id="0c21d-249">적은 메모리 공간</span><span class="sxs-lookup"><span data-stu-id="0c21d-249">Small footprint</span></span>

<span data-ttu-id="0c21d-250">Azure RTOS ThreadX는 매우 적은 2KB 명령 영역과 RAM 1KB의 최소 메모리 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-250">Azure RTOS ThreadX requires a remarkably small 2KB instruction area and 1KB of RAM for its minimal footprint.</span></span> <span data-ttu-id="0c21d-251">이는 주로 계층화되지 않은 picokernel™ 아키텍처와 자동 크기 조정으로 인해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-251">This is largely due to its non-layered picokernel™ architecture and automatic scaling.</span></span> <span data-ttu-id="0c21d-252">자동 크기 조정은 애플리케이션에서 사용되는 서비스(및 지원 인프라)만 링크 타임에서 최종 이미지에 포함된다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-252">Automatic scaling means that only the services (and supporting infrastructure) used by the application are included in the final image at link time.</span></span>

<span data-ttu-id="0c21d-253">몇 가지 일반적인 Azure RTOS ThreadX 크기 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-253">Here are some typical Azure RTOS ThreadX size characteristics:</span></span>

|<span data-ttu-id="0c21d-254">Azure RTOS ThreadX 서비스</span><span class="sxs-lookup"><span data-stu-id="0c21d-254">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="0c21d-255">일반적인 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="0c21d-255">Typical Size in Bytes</span></span>  |
|---------|---------|
|<span data-ttu-id="0c21d-256">Core Services(필수)</span><span class="sxs-lookup"><span data-stu-id="0c21d-256">Core Services (Require)</span></span> |<span data-ttu-id="0c21d-257">2,000</span><span class="sxs-lookup"><span data-stu-id="0c21d-257">2,000</span></span>  |
|<span data-ttu-id="0c21d-258">큐 서비스</span><span class="sxs-lookup"><span data-stu-id="0c21d-258">Queue Services</span></span>  |<span data-ttu-id="0c21d-259">900</span><span class="sxs-lookup"><span data-stu-id="0c21d-259">900</span></span>  |
|<span data-ttu-id="0c21d-260">이벤트 플래그 서비스</span><span class="sxs-lookup"><span data-stu-id="0c21d-260">Event Flag Services</span></span>  |<span data-ttu-id="0c21d-261">900</span><span class="sxs-lookup"><span data-stu-id="0c21d-261">900</span></span>  |
|<span data-ttu-id="0c21d-262">세마포 서비스</span><span class="sxs-lookup"><span data-stu-id="0c21d-262">Semaphore Services</span></span>  |<span data-ttu-id="0c21d-263">450</span><span class="sxs-lookup"><span data-stu-id="0c21d-263">450</span></span>  |
|<span data-ttu-id="0c21d-264">뮤텍스 서비스</span><span class="sxs-lookup"><span data-stu-id="0c21d-264">Mutex Services</span></span>  |<span data-ttu-id="0c21d-265">1,200</span><span class="sxs-lookup"><span data-stu-id="0c21d-265">1,200</span></span>  |
|<span data-ttu-id="0c21d-266">블록 메모리 서비스</span><span class="sxs-lookup"><span data-stu-id="0c21d-266">Block Memory Services</span></span>  |<span data-ttu-id="0c21d-267">550</span><span class="sxs-lookup"><span data-stu-id="0c21d-267">550</span></span>  |
|<span data-ttu-id="0c21d-268">바이트 메모리 서비스</span><span class="sxs-lookup"><span data-stu-id="0c21d-268">Byte Memory Services</span></span>  |<span data-ttu-id="0c21d-269">900</span><span class="sxs-lookup"><span data-stu-id="0c21d-269">900</span></span>  |

## <a name="fast-execution"></a><span data-ttu-id="0c21d-270">고속 실행</span><span class="sxs-lookup"><span data-stu-id="0c21d-270">Fast execution</span></span>

<span data-ttu-id="0c21d-271">Azure RTOS ThreadX는 대부분의 인기 있는 프로세서에서 초소형 컨텍스트 전환을 달성하며 전반적으로 다른 상용 RTOS보다 훨씬 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-271">Azure RTOS ThreadX achieves a sub-microsecond context switch on most popular processors and is significantly faster overall than other commercial RTOSes.</span></span> <span data-ttu-id="0c21d-272">Azure RTOS ThreadX는 속도가 빠를 뿐만 아니라 결정성도 뛰어납니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-272">In addition to being fast, Azure RTOS ThreadX is also highly deterministic.</span></span> <span data-ttu-id="0c21d-273">200개의 스레드가 준비되어 있든 단 한 개만 준비되어 있든 동일한 빠른 성능을 달성합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-273">It achieves the same fast performance whether there are 200 threads ready, or just one.</span></span>

<span data-ttu-id="0c21d-274">Azure RTOS ThreadX의 일반적인 성능 특성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-274">Here are some typical performance characteristics of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="0c21d-275">빠른 부팅: Azure RTOS ThreadX는 120 사이클 미만으로 부팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-275">Fast Boot: Azure RTOS ThreadX boots in less than 120 cycles.</span></span>
* <span data-ttu-id="0c21d-276">선택적 기본 오류 검사 제거: 컴파일 타임에 기본 Azure RTOS ThreadX 오류 검사를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-276">Optional Removal of basic error checking: Basic Azure RTOS ThreadX error checking can be skipped at compile time.</span></span> <span data-ttu-id="0c21d-277">이는 애플리케이션 코드가 확인되고 더 이상 각 매개 변수에 대한 오류 검사가 필요하지 않을 때 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-277">This can be useful when the application code is verified and no longer requires error checking on each parameter.</span></span> <span data-ttu-id="0c21d-278">이는 시스템 차원이 아닌 컴파일 단위에서 수행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-278">Note that this can be done on a compilation unit, rather than system-wide.</span></span>
* <span data-ttu-id="0c21d-279">Picokernel™ 디자인: 서비스가 서로 계층화되지 않으므로 불필요한 함수 호출 오버 헤드가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-279">Picokernel™ Design: Services are not layered on each other, thus eliminating unnecessary function call overhead.</span></span>
* <span data-ttu-id="0c21d-280">\*최적화된 인터럽트 처리: 선점이 필요한 경우가 아니면 ISR 진입/종료 시 스크래치 레지스터만 저장/복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-280">\*Optimized Interrupt Processing: Only scratch registers are saved/restored upon ISR entry/exit, unless preemption is necessary.</span></span>
* <span data-ttu-id="0c21d-281">최적화된 API 처리:</span><span class="sxs-lookup"><span data-stu-id="0c21d-281">Optimized API Processing:</span></span>

    |<span data-ttu-id="0c21d-282">Azure RTOS ThreadX 서비스</span><span class="sxs-lookup"><span data-stu-id="0c21d-282">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="0c21d-283">서비스 시간(마이크로초)\*</span><span class="sxs-lookup"><span data-stu-id="0c21d-283">Service Time in Microseconds\*</span></span>  |
    |---------|---------|
    |<span data-ttu-id="0c21d-284">스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="0c21d-284">Thread Suspend</span></span>  |<span data-ttu-id="0c21d-285">0.6</span><span class="sxs-lookup"><span data-stu-id="0c21d-285">0.6</span></span>  |
    |<span data-ttu-id="0c21d-286">스레드 계속하기</span><span class="sxs-lookup"><span data-stu-id="0c21d-286">Thread Resume</span></span>  |<span data-ttu-id="0c21d-287">0.6</span><span class="sxs-lookup"><span data-stu-id="0c21d-287">0.6</span></span>  |
    |<span data-ttu-id="0c21d-288">큐 송신</span><span class="sxs-lookup"><span data-stu-id="0c21d-288">Queue Send</span></span>  |<span data-ttu-id="0c21d-289">0.3</span><span class="sxs-lookup"><span data-stu-id="0c21d-289">0.3</span></span>  |
    |<span data-ttu-id="0c21d-290">큐 수신</span><span class="sxs-lookup"><span data-stu-id="0c21d-290">Queue Receive</span></span>  |<span data-ttu-id="0c21d-291">0.3</span><span class="sxs-lookup"><span data-stu-id="0c21d-291">0.3</span></span>  |
    |<span data-ttu-id="0c21d-292">세마포 가져오기</span><span class="sxs-lookup"><span data-stu-id="0c21d-292">Get Semaphore</span></span>  |<span data-ttu-id="0c21d-293">0.2</span><span class="sxs-lookup"><span data-stu-id="0c21d-293">0.2</span></span>  |
    |<span data-ttu-id="0c21d-294">세마포 배치</span><span class="sxs-lookup"><span data-stu-id="0c21d-294">Put Semaphore</span></span>  |<span data-ttu-id="0c21d-295">0.2</span><span class="sxs-lookup"><span data-stu-id="0c21d-295">0.2</span></span>  |
    |<span data-ttu-id="0c21d-296">컨텍스트 전환</span><span class="sxs-lookup"><span data-stu-id="0c21d-296">Context Switch</span></span>  |<span data-ttu-id="0c21d-297">0.4</span><span class="sxs-lookup"><span data-stu-id="0c21d-297">0.4</span></span>  |
    |<span data-ttu-id="0c21d-298">인터럽트 응답</span><span class="sxs-lookup"><span data-stu-id="0c21d-298">Interrupt Response</span></span>  |<span data-ttu-id="0c21d-299">0.0 – 0.6</span><span class="sxs-lookup"><span data-stu-id="0c21d-299">0.0 – 0.6</span></span>  |

    <span data-ttu-id="0c21d-300">\**200MHz로 실행되는 일반적인 프로세서에 따른 성능 수치*.</span><span class="sxs-lookup"><span data-stu-id="0c21d-300">\**Performance figures based on typical processor running at 200MHz*.</span></span>

## <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="0c21d-301">TUV 및 UL을 비롯한 여러 안전 표준의 사전 인증</span><span class="sxs-lookup"><span data-stu-id="0c21d-301">Pre-certified by TUV and UL to many safety standards</span></span>

<span data-ttu-id="0c21d-302">Azure RTOS ThreadX 및 Azure RTOS ThreadX SMP는 안전이 매우 중요한 시스템에서의 사용을 위해, IEC-61508 SIL 4, IEC-62304 SW 안전 등급 C, ISO 26262 ASIL D 및 EN 50128에 따라 SGS-TUV Saar 인증을 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-302">Azure RTOS ThreadX and Azure RTOS ThreadX SMP have been certified by SGS-TUV Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="0c21d-303">이 인증은 "전기, 전자 및 프로그램 가능한 전자 안전 관련 시스템의 기능적 안전"에 대한 최고 수준의 IEC-61508, IEC-62304, ISO 26262 및 EN 50128의 안전 무결성 등급에 따라, Azure RTOS ThreadX 및 Azure RTOS ThreadX SMP를 보안 관련 소프트웨어의 개발에 사용할 수 있음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-303">The certification confirms that Azure RTOS ThreadX and Azure RTOS ThreadX SMP can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="0c21d-304">독일 SGS-Group 및 TUV Saarland의 공동 벤처인 SGS-TUV Saar는 세계적으로 안전 관련 시스템용 포함 소프트웨어를 테스트, 감사, 확인 및 검증하는 최고 권위의 독립 기업으로 자리했습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-304">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="0c21d-305">산업 보안 표준 IEC 61508과, 거기에서 파생된 모든 표준(IEC-62304, ISO 26262 및 EN 50128 포함)은 전기, 전자 및 프로그래밍 가능한 전자 안전 관련 의료 장비, 공정 제어 시스템, 산업용 기계, 자동차, 철도 제어 시스템의 기능 안전을 보장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-305">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to ensure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

:::image type="content" source="media/overview-threadx/partener-logo-sgs-tuv-saar-2.png" alt-text="SGS TUV SAAR 인증":::

<span data-ttu-id="0c21d-307">UL은 Azure RTOS ThreadX 및 Azure RTOS ThreadX SMP가 프로그래밍 가능한 구성 요소에서의 소프트웨어에 대한 UL 60730-1 부칙 H, CSA E60730-1 부칙 H, IEC 60730-1 부칙 H, UL 60335-1 부칙 R, IEC 60335-1 부칙 R 및 UL 1998 안전 표준을 준수한다고 인정했습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-307">Azure RTOS ThreadX and Azure RTOS ThreadX SMP have been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="0c21d-308">UL은 전기의 공공 도입에서부터 지속 가능성, 재생 에너지 및 나노 기술의 혁신에 이르기까지 안전 솔루션을 혁신하는 1세기 이상의 전문 지식을 보유한 글로벌 독립 안전 과학 기업입니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-308">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

:::image type="content" source="media/overview-threadx/cru-logo-certification.png" alt-text="UL 인증":::

<span data-ttu-id="0c21d-310">TUV 및 UL 인증과 관련한 아티팩트(인증서, 안전 매뉴얼, 테스트 보고서 등)는 판매 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-310">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

## <a name="eal4-common-criteria-security-certification"></a><span data-ttu-id="0c21d-311">EAL4+ Common Criteria 보안 인증</span><span class="sxs-lookup"><span data-stu-id="0c21d-311">EAL4+ Common Criteria security certification</span></span>

<span data-ttu-id="0c21d-312">Azure RTOS는 EAL4+ Common Criteria 보안 인증을 달성했습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-312">Azure RTOS has achieved EAL4+ Common Criteria security certification.</span></span> <span data-ttu-id="0c21d-313">TOE(평가 대상)은 Azure RTOS ThreadX, Azure RTOS NetX-Duo, Azure RTOS NetX Secure TLS 및 Azure RTOS NetX MQTT를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-313">The Target of Evalution (TOE) covers Azure RTOS ThreadX, Azure RTOS NetX-Duo, Azure RTOS NetX Secure TLS, and Azure RTOS NetX MQTT.</span></span> <span data-ttu-id="0c21d-314">이는 깊이 내장된 센서, 디바이스, 에지 라우터 및 게이트웨이에 필요한 가장 일반적인 IoT 프로토콜을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-314">This represents the most typical IoT protocols required by deeply embedded sensors, devices, edge routers, and gateways.</span></span>

:::image type="content" border="false" source="media/overview-threadx/eal-logo-certification.png" alt-text="EAL 인증":::

<span data-ttu-id="0c21d-316">Azure RTOS 보안 인증에 사용되는 IT 보안 평가 시설은 Brightsight BV이고 인증 기관은 SERTIT입니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-316">The IT Security Evaluation Facility used for the Azure RTOS security certification is Brightsight BV and the Certification Authority is SERTIT.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="0c21d-317">간단하고 손쉬운 사용</span><span class="sxs-lookup"><span data-stu-id="0c21d-317">Simple, easy to use</span></span>

<span data-ttu-id="0c21d-318">Azure RTOS ThreadX는 매우 간단하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-318">Azure RTOS ThreadX is very simple to use.</span></span> <span data-ttu-id="0c21d-319">Azure RTOS ThreadX API는 직관적이고 매우 기능적입니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-319">The Azure RTOS ThreadX API is both intuitive and highly functional.</span></span> <span data-ttu-id="0c21d-320">API 이름은 다른 RTOS 제품에서 흔히 볼 수 있는 매우 축약된 이름의 알파벳 약자가 아니라 실제 단어로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-320">The API names are made of real words and not the alphabet soup of highly abbreviated names that are so common in other RTOS products.</span></span> <span data-ttu-id="0c21d-321">모든 Azure RTOS ThreadX API에는 선행 `tx_`가 있으며 명사-동사 명명 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-321">All Azure RTOS ThreadX APIs have a leading `tx_` and follow a noun-verb naming convention.</span></span> <span data-ttu-id="0c21d-322">또한 API 전체에 걸쳐 기능적 일관성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-322">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="0c21d-323">예를 들어 일시 중단된 모든 API는 API에 대해 동일한 방식으로 작동하는 선택적 시간 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-323">For example, all APIs that suspend have an optional timeout that functions in an identical manner for APIs.</span></span>

<span data-ttu-id="0c21d-324">Azure RTOS ThreadX 애플리케이션을 쉽게 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-324">Building an Azure RTOS ThreadX application is easy.</span></span> <span data-ttu-id="0c21d-325">애플리케이션은 *tx_api.h* 를 포함하고, main에서 `tx_kernel_enter`를 호출하고, `tx_application_define` 함수를 정의하고, 스레드 하나를 만들고, 스레드 진입점 함수를 정의하고, Azure RTOS ThreadX 라이브러리에 대한 링크(일반적으로 *tx.a*)를 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-325">The application needs to include *tx_api.h*, call `tx_kernel_enter` from main, define the `tx_application_define` function and create one thread, define the thread entry point function, and link against the Azure RTOS ThreadX library (typically *tx.a*).</span></span>

<span data-ttu-id="0c21d-326">또한 Azure RTOS ThreadX는 사용 가능한 최고 수준의 문서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-326">Azure RTOS ThreadX also boasts the highest caliber of documentation available.</span></span> 

## <a name="advanced-technology"></a><span data-ttu-id="0c21d-327">고급 기술</span><span class="sxs-lookup"><span data-stu-id="0c21d-327">Advanced technology</span></span>

<span data-ttu-id="0c21d-328">Azure RTOS ThreadX는 가장 중요한 기능이 preemption-threshold 예약인 고급 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-328">Azure RTOS ThreadX is advanced technology whose most notable feature is preemption-threshold scheduling.</span></span> <span data-ttu-id="0c21d-329">이 기능은 Azure RTOS ThreadX의 고유한 것이며 광범위한 학술 연구의 주제였습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-329">This feature is unique to Azure RTOS ThreadX and has been the subject of extensive academic research.</span></span> <span data-ttu-id="0c21d-330">예를 들어, Yun Wang(콩코디아 대학교) 및 Manas Saksena(피츠버그 대학교)의 [Preemption Threshold를 사용하여 고정 우선 순위 작업 예약(Scheduling Fixed-Priority Tasks with Preemption Threshold)](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0c21d-330">For example, see [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), by Yun Wang, Concordia University, and Manas Saksena, University of Pittsburgh.</span></span>

<span data-ttu-id="0c21d-331">Azure RTOS ThreadX의 기능을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-331">Consider the capabilities of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="0c21d-332">완전하고 포괄적인 멀티태스킹 기능 제공</span><span class="sxs-lookup"><span data-stu-id="0c21d-332">Complete and Comprehensive Multitasking Facilities</span></span>
  * <span data-ttu-id="0c21d-333">스레드, 애플리케이션 타이머, 메시지 큐, 세마포 계산, 뮤텍스, 이벤트 플래그, 블록 및 바이트 메모리 풀</span><span class="sxs-lookup"><span data-stu-id="0c21d-333">Threads, application timers, message queues, counting semaphores, mutexes, event flags, block and byte memory pools</span></span>
* <span data-ttu-id="0c21d-334">우선 순위 기반의 선점 예약</span><span class="sxs-lookup"><span data-stu-id="0c21d-334">Priority-Based Preemptive Scheduling</span></span>
* <span data-ttu-id="0c21d-335">우선 순위 유연성 – 최대 1024개의 우선 순위 수준</span><span class="sxs-lookup"><span data-stu-id="0c21d-335">Priority Flexibility – Up to 1024 Priority Levels</span></span>
* <span data-ttu-id="0c21d-336">협력 예약</span><span class="sxs-lookup"><span data-stu-id="0c21d-336">Cooperative Scheduling</span></span>
* <span data-ttu-id="0c21d-337">Preemption-Threshold™ – Azure RTOS ThreadX만의 고유한 기능으로 컨텍스트 스위치를 줄이고 예약 가능성을 보장할 수 있습니다(학술 연구 기준).</span><span class="sxs-lookup"><span data-stu-id="0c21d-337">Preemption-Threshold™ – Unique to Azure RTOS ThreadX, helps reduce context switches and help guarantee schedulability (per academic research)</span></span>
* <span data-ttu-id="0c21d-338">Azure RTOS ThreadX MODULES를 통한 메모리 보호</span><span class="sxs-lookup"><span data-stu-id="0c21d-338">Memory Protection via Azure RTOS ThreadX MODULES</span></span>
* <span data-ttu-id="0c21d-339">완전 결정적</span><span class="sxs-lookup"><span data-stu-id="0c21d-339">Fully Deterministic</span></span>
* <span data-ttu-id="0c21d-340">이벤트 추적 – 마지막 *n* 개의 시스템/애플리케이션 이벤트 캡처</span><span class="sxs-lookup"><span data-stu-id="0c21d-340">Event Trace – Capture last *n* system/application events</span></span>
* <span data-ttu-id="0c21d-341">Event Chaining™ – 각 Azure RTOS ThreadX 통신 또는 동기화 개체에 대해 애플리케이션별 "알림" 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-341">Event Chaining™ – Register an application-specific “notify” callback function for each Azure RTOS ThreadX communication or synchronization object</span></span>
* <span data-ttu-id="0c21d-342">선택적 메모리 보호 기능이 있는 Azure RTOS ThreadX MODULES</span><span class="sxs-lookup"><span data-stu-id="0c21d-342">Azure RTOS ThreadX MODULES with Optional Memory Protection</span></span>
* <span data-ttu-id="0c21d-343">런타임 성능 메트릭</span><span class="sxs-lookup"><span data-stu-id="0c21d-343">Run-Time Performance Metrics</span></span>
  * <span data-ttu-id="0c21d-344">스레드 재개 수</span><span class="sxs-lookup"><span data-stu-id="0c21d-344">Number of thread resumptions</span></span>
  * <span data-ttu-id="0c21d-345">스레드 일시 중단 수</span><span class="sxs-lookup"><span data-stu-id="0c21d-345">Number of thread suspensions</span></span>
  * <span data-ttu-id="0c21d-346">요청된 스레드 선점 수</span><span class="sxs-lookup"><span data-stu-id="0c21d-346">Number of solicited thread preemptions</span></span>
  * <span data-ttu-id="0c21d-347">비동기 스레드 인터럽트 선점 수</span><span class="sxs-lookup"><span data-stu-id="0c21d-347">Number of asynchronous thread interrupt preemptions</span></span>
  * <span data-ttu-id="0c21d-348">스레드 우선 순위 반전 수</span><span class="sxs-lookup"><span data-stu-id="0c21d-348">Number of thread priority inversions</span></span>
  * <span data-ttu-id="0c21d-349">스레드 포기 수</span><span class="sxs-lookup"><span data-stu-id="0c21d-349">Number of thread relinquishes</span></span>
* <span data-ttu-id="0c21d-350">EPK(실행 프로필 키트)</span><span class="sxs-lookup"><span data-stu-id="0c21d-350">Execution Profile Kit (EPK)</span></span>
* <span data-ttu-id="0c21d-351">별도의 인터럽트 스택</span><span class="sxs-lookup"><span data-stu-id="0c21d-351">Separate Interrupt Stack</span></span>
* <span data-ttu-id="0c21d-352">런타임 스택 분석</span><span class="sxs-lookup"><span data-stu-id="0c21d-352">Run-Time Stack Analysis</span></span>
* <span data-ttu-id="0c21d-353">최적화된 타이머 인터럽트 처리</span><span class="sxs-lookup"><span data-stu-id="0c21d-353">Optimized Timer Interrupt Processing</span></span>

## <a name="multicore-support-amp--smp"></a><span data-ttu-id="0c21d-354">멀티 코어 지원(AMP 및 SMP)</span><span class="sxs-lookup"><span data-stu-id="0c21d-354">Multicore support (AMP & SMP)</span></span>

<span data-ttu-id="0c21d-355">표준 Azure RTOS ThreadX는 종종 AMP(비대칭적 다중 처리) 방식으로 사용되며, Azure RTOS ThreadX 및 애플리케이션(또는 Linux)의 별도 복사본이 각 코어에서 실행되고 공유 메모리 또는 OpenAMP(Azure RTOS ThreadX는 OpenAMP를 지원)와 같은 프로세서 간 통신 메커니즘을 통해 서로 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-355">Standard Azure RTOS ThreadX is often used in an Asymmetric Multiprocessing (AMP) fashion, where a separate copy of Azure RTOS ThreadX and the application (or Linux) execute on each core and communicate with each other via shared memory or an inter-processor communication mechanism such as OpenAMP (Azure RTOS ThreadX supports OpenAMP).</span></span> <span data-ttu-id="0c21d-356">이는 Azure RTOS ThreadX를 사용하는 가장 일반적인 다중 코어 구성이며 애플리케이션에서 프로세서를 효과적으로 로드할 수 있는 경우 가장 효율적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-356">This is the most typical multicore configuration using Azure RTOS ThreadX and can be the most efficient if the application is able to effectively load the processors.</span></span>

<span data-ttu-id="0c21d-357">프로세서를 로드하는 것이 매우 동적인 환경에서는 다음 프로세서 제품군에 대해 Azure RTOS ThreadX SMP(대칭적 다중 처리)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-357">For environments where loading the processors is highly dynamic, Azure RTOS ThreadX Symetric Multiprocessing (SMP) is available for the following processor families:</span></span>

* <span data-ttu-id="0c21d-358">ARM Cortex-Ax</span><span class="sxs-lookup"><span data-stu-id="0c21d-358">ARM Cortex-Ax</span></span>
* <span data-ttu-id="0c21d-359">ARM Cortex-Rx</span><span class="sxs-lookup"><span data-stu-id="0c21d-359">ARM Cortex-Rx</span></span>
* <span data-ttu-id="0c21d-360">ARM Cortex-A5x 64비트</span><span class="sxs-lookup"><span data-stu-id="0c21d-360">ARM Cortex-A5x 64-bit</span></span>
* <span data-ttu-id="0c21d-361">MIPS 34K, 1004K 및 interAptiv</span><span class="sxs-lookup"><span data-stu-id="0c21d-361">MIPS 34K, 1004K, and interAptiv</span></span>
* <span data-ttu-id="0c21d-362">PowerPC</span><span class="sxs-lookup"><span data-stu-id="0c21d-362">PowerPC</span></span>
* <span data-ttu-id="0c21d-363">Synopsys ARC HS</span><span class="sxs-lookup"><span data-stu-id="0c21d-363">Synopsys ARC HS</span></span>
* <span data-ttu-id="0c21d-364">x86</span><span class="sxs-lookup"><span data-stu-id="0c21d-364">x86</span></span>

<span data-ttu-id="0c21d-365">Azure RTOS ThreadX SMP는 *n* 개 프로세서에서 동적 부하 분산을 수행하고 모든 Azure RTOS ThreadX 리소스(큐, 세마포, 이벤트 플래그, 메모리 풀 등)를 모든 코어의 모든 스레드에서 액세스할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-365">Azure RTOS ThreadX SMP performs dynamic load balancing across *n* processors and allows all Azure RTOS ThreadX resources (queues, semaphores, event flags, memory pools, etc.) to be accessed by any thread on any core.</span></span> <span data-ttu-id="0c21d-366">Azure RTOS ThreadX SMP는 모든 코어에서 전체 Azure RTOS ThreadX API를 사용하고 SMP 작업에 적용되는 다음과 같은 새 API를 도입합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-366">Azure RTOS ThreadX SMP enables the complete Azure RTOS ThreadX API on all cores and introduces the following new API’s applicable to SMP operation:</span></span>

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a><span data-ttu-id="0c21d-367">Azure RTOS ThreadX MODULES를 통한 메모리 보호</span><span class="sxs-lookup"><span data-stu-id="0c21d-367">Memory protection via Azure RTOS ThreadX Modules</span></span>

<span data-ttu-id="0c21d-368">Azure RTOS ThreadX MODULES라는 추가 기능 제품을 사용하면 하나 이상의 애플리케이션 스레드를 대상에서 동적으로 로드하고 실행할 수 있는 "모듈"에 묶을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-368">An add-on product called Azure RTOS ThreadX MODULES enables one or more application threads to be bundled into a “Module” that can be dynamically loaded and run (or executed in place) on the target.</span></span>

<span data-ttu-id="0c21d-369">모듈을 사용하면 필드 업그레이드, 버그 수정 및 프로그램 분할을 사용하여 많은 애플리케이션이 활성 스레드에 필요한 메모리만 차지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-369">Modules enable field upgrade, bug fixing, and program partitioning to allow large applications to occupy only the memory needed by active threads.</span></span>

<span data-ttu-id="0c21d-370">또한 모듈에는 Azure RTOS ThreadX 자체와 완전히 별개의 주소 공간이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-370">Modules also have a completely separate address space from Azure RTOS ThreadX itself.</span></span> <span data-ttu-id="0c21d-371">이를 통해 Azure RTOS ThreadX는 모듈 주변에 메모리 보호(MPU 또는 MMU를 통해)를 배치하여 실수로 모듈 외부에 액세스해도 다른 소프트웨어 구성 요소가 손상되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-371">This enables Azure RTOS ThreadX to place memory protection (via MPU or MMU) around the Module such that accidental access outside the module will not be able to corrupt any other software component.</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="0c21d-372">가장 빠른 출시 시간</span><span class="sxs-lookup"><span data-stu-id="0c21d-372">Fastest time-to-market</span></span>

<span data-ttu-id="0c21d-373">Azure RTOS ThreadX는 설치, 학습, 사용, 디버그, 확인, 인증 및 유지 관리를 손쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-373">Azure RTOS ThreadX is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="0c21d-374">그 결과 Azure RTOS ThreadX는 EMF(Embedded Market Forecasters) 설문 조사에서 지난 7년 연속 가장 빠른 출시 시간의 RTOS였습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-374">As a result, Azure RTOS ThreadX has been the leading time-to-market RTOS for the last seven consecutive years, per the Embedded Market Forecasters (EMF) surveys.</span></span> <span data-ttu-id="0c21d-375">설문 조사에서 Azure RTOS ThreadX를 사용한 디자인의 70%가 제 시간에 출시된 것으로 나타났으며, 이는 다른 모든 RTOS를 능가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-375">The surveys consistently show that 70% of designs using Azure RTOS ThreadX get to market on time – surpassing all other RTOSes.</span></span>

<span data-ttu-id="0c21d-376">일관된 출시 시간이 가능한 몇 가지 이유는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-376">The following are reasons for our consistent time-to-market advantage:</span></span>

* <span data-ttu-id="0c21d-377">품질 설명서</span><span class="sxs-lookup"><span data-stu-id="0c21d-377">Quality Documentation</span></span>
* <span data-ttu-id="0c21d-378">전체 소스 코드 가용성</span><span class="sxs-lookup"><span data-stu-id="0c21d-378">Complete Source Code Availability</span></span>
* <span data-ttu-id="0c21d-379">사용하기 쉬운 API</span><span class="sxs-lookup"><span data-stu-id="0c21d-379">Easy-to-Use API</span></span>
* <span data-ttu-id="0c21d-380">포괄적인 고급 기능 세트</span><span class="sxs-lookup"><span data-stu-id="0c21d-380">Comprehensive and Advanced Feature Set</span></span>
* <span data-ttu-id="0c21d-381">광범위한 타사 도구 통합 – 특히 IAR의 Embedded Workbench™</span><span class="sxs-lookup"><span data-stu-id="0c21d-381">Broad 3rd Party Tools Integration – Especially IAR’s Embedded Workbench™</span></span>

## <a name="royalty-free"></a><span data-ttu-id="0c21d-382">로열티 무료</span><span class="sxs-lookup"><span data-stu-id="0c21d-382">Royalty free</span></span>

<span data-ttu-id="0c21d-383">사전에 사용이 허가된 디바이스에 배포하는 경우에는 소스 코드를 사용 및 테스트하는 데 비용이 들지 않으며 프로덕션 라이선스에 대한 비용도 부과되지 않습니다. 다른 모든 디바이스에는 간단한 연간 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-383">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="0c21d-384">최고 품질의 전체 소스 코드</span><span class="sxs-lookup"><span data-stu-id="0c21d-384">Full, highest-quality source code</span></span>

<span data-ttu-id="0c21d-385">처음부터 Azure RTOS ThreadX는 완전한 C 소스 코드로 배포된 산업 등급 RTOS로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-385">From the very beginning, Azure RTOS ThreadX was designed to be an Industrial Grade RTOS, distributed with full C source code.</span></span> <span data-ttu-id="0c21d-386">Azure RTOS ThreadX 소스 코드는 품질 및 이해 용이성의 기준을 정립했습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-386">Azure RTOS ThreadX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="0c21d-387">또한 파일당 하나의 함수를 포함하는 규칙을 통해 손쉬운 소스 탐색을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-387">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

<span data-ttu-id="0c21d-388">Azure RTOS ThreadX는 모든 C 코드 행에 의미 있는 주석이 있어야 한다는 요구 사항을 비롯한 엄격한 코딩 규칙을 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-388">Azure RTOS ThreadX conforms to strict coding conventions, including the requirement that every line of C code has a meaningful comment.</span></span> <span data-ttu-id="0c21d-389">또한 Azure RTOS ThreadX 소스는 가장 높은 표준으로 인증되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-389">In addition, the Azure RTOS ThreadX source has been certified to the highest standards.</span></span>

## <a name="misra-compliant"></a><span data-ttu-id="0c21d-390">MISRA 준수</span><span class="sxs-lookup"><span data-stu-id="0c21d-390">MISRA compliant</span></span>

<span data-ttu-id="0c21d-391">Azure RTOS ThreadX 및 Azure RTOS ThreadX SMP 소스 코드는 MISRA-C:2004 및 MISRA C:2012를 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-391">Azure RTOS ThreadX and Azure RTOS ThreadX SMP souce code is MISRA-C:2004 and MISRA C:2012 compliant.</span></span> <span data-ttu-id="0c21d-392">MISRA C는 C 프로그래밍 언어를 사용하는 중요 시스템에 대한 프로그래밍 지침 세트입니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-392">MISRA C is a set of programming guidelines for critical systems using the C programming language.</span></span> <span data-ttu-id="0c21d-393">원래의 MISRA C 지침은 주로 자동차 분야를 대상으로 했지만, MISRA C는 이제 모든 안전 중요 분야에 적용할 수 있는 것으로 널리 인식되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-393">The original MISRA C guidelines were primarily targeted toward automotive applications; however, MISRA C is now widely recognized as being applicable to any safety-critical application.</span></span> <span data-ttu-id="0c21d-394">Azure RTOS ThreadX는 MISRA-C:2004 및 MISRA C:2012의 모든 필수 및 의무 규칙을 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-394">Azure RTOS ThreadX is compliant with all required and mandatory rules of MISRA-C:2004 and MISRA C:2012.</span></span>

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Misra 인증":::

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="0c21d-396">대부분의 주요 아키텍처 지원</span><span class="sxs-lookup"><span data-stu-id="0c21d-396">Supports most popular architectures</span></span>

<span data-ttu-id="0c21d-397">Azure RTOS ThreadX는 완전한 테스트와 지원을 통해 다음과 같이 대부분의 주요 32/64비트 마이크로프로세서에서 실행되며, 바로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-397">Azure RTOS ThreadX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

* <span data-ttu-id="0c21d-398">아날로그 디바이스: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="0c21d-398">Analog Devices: SHARC, Blackfin, CM4xx</span></span>
* <span data-ttu-id="0c21d-399">Andes Core: RISC-V</span><span class="sxs-lookup"><span data-stu-id="0c21d-399">Andes Core: RISC-V</span></span>
* <span data-ttu-id="0c21d-400">Ambiqmicro: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="0c21d-400">Ambiqmicro: Apollo MCUs</span></span>
* <span data-ttu-id="0c21d-401">ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="0c21d-401">ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>
* <span data-ttu-id="0c21d-402">Cadence: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="0c21d-402">Cadence: Xtensa, Diamond</span></span>
* <span data-ttu-id="0c21d-403">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="0c21d-403">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>
* <span data-ttu-id="0c21d-404">Cypress: RISC-V</span><span class="sxs-lookup"><span data-stu-id="0c21d-404">Cypress: RISC-V</span></span>
* <span data-ttu-id="0c21d-405">EnSilica: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="0c21d-405">EnSilica: eSi-RISC</span></span>
* <span data-ttu-id="0c21d-406">Infineon: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="0c21d-406">Infineon: XMC1000, XMC4000, TriCore</span></span>
* <span data-ttu-id="0c21d-407">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="0c21d-407">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>
* <span data-ttu-id="0c21d-408">Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="0c21d-408">Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>
* <span data-ttu-id="0c21d-409">Microsemi: RISC-V</span><span class="sxs-lookup"><span data-stu-id="0c21d-409">Microsemi: RISC-V</span></span>
* <span data-ttu-id="0c21d-410">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="0c21d-410">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>
* <span data-ttu-id="0c21d-411">Renesas: SH, HS, V850, RX, RZ, Synergy</span><span class="sxs-lookup"><span data-stu-id="0c21d-411">Renesas: SH, HS, V850, RX, RZ, Synergy</span></span>
* <span data-ttu-id="0c21d-412">Silicon Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="0c21d-412">Silicon Labs: EFM32</span></span>
* <span data-ttu-id="0c21d-413">Synopsys: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="0c21d-413">Synopsys: ARC 600, 700, ARC EM, ARC HS</span></span>
* <span data-ttu-id="0c21d-414">ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="0c21d-414">ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>
* <span data-ttu-id="0c21d-415">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="0c21d-415">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>
* <span data-ttu-id="0c21d-416">Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="0c21d-416">Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>
* <span data-ttu-id="0c21d-417">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="0c21d-417">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

## <a name="supports-most-popular-tools"></a><span data-ttu-id="0c21d-418">가장 널리 사용되는 도구 지원</span><span class="sxs-lookup"><span data-stu-id="0c21d-418">Supports most popular tools</span></span>

<span data-ttu-id="0c21d-419">Azure RTOS ThreadX는 IAR의 Embedded Workbench™를 비롯하여 가장 널리 사용되는 임베디드 개발 도구를 지원하며, 가장 포괄적인 Azure RTOS ThreadX 커널 인식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-419">Azure RTOS ThreadX supports most popular embedded development tools, including IAR’s Embedded Workbench™, which also has the most comprehensive Azure RTOS ThreadX kernel awareness available.</span></span> <span data-ttu-id="0c21d-420">추가 도구 통합에는 GNU(GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore 및 모든 아날로그 디바이스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c21d-420">Additional tool integration includes GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore and all analog devices.</span></span>
