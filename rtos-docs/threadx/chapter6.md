---
title: 6장 - Azure RTOS ThreadX에 대한 데모 시스템
description: 이 장에는 모든 Azure RTOS ThreadX 프로세서 지원 패키지와 함께 제공되는 데모 시스템에 대한 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be85ba77e5c27366f61899c0939be7cad1845bbe
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810267"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx"></a><span data-ttu-id="8ba12-103">6장 - Azure RTOS ThreadX에 대한 데모 시스템</span><span class="sxs-lookup"><span data-stu-id="8ba12-103">Chapter 6 - Demonstration System for Azure RTOS ThreadX</span></span>

<span data-ttu-id="8ba12-104">이 장에는 모든 Azure RTOS ThreadX 프로세서 지원 패키지와 함께 제공되는 데모 시스템에 대한 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-104">This chapter contains a description of the demonstration system that is delivered with all Azure RTOS ThreadX processor support packages.</span></span>

## <a name="overview"></a><span data-ttu-id="8ba12-105">개요</span><span class="sxs-lookup"><span data-stu-id="8ba12-105">Overview</span></span>

<span data-ttu-id="8ba12-106">각 ThreadX 제품 배포에는 지원되는 모든 마이크로프로세서에서 실행되는 데모 시스템이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-106">Each ThreadX product distribution contains a demonstration system that runs on all supported microprocessors.</span></span>

<span data-ttu-id="8ba12-107">이 예제 시스템은 배포 파일 ***demo_threadx.c*** 에 정의되어 있으며, ThreadX가 포함된 다중 스레드 환경에서 어떻게 사용되는지 보여 주기 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-107">This example system is defined in the distribution file ***demo_threadx.c*** and is designed to illustrate how ThreadX is used in an embedded multithread environment.</span></span> <span data-ttu-id="8ba12-108">이 데모는 초기화, 8개의 스레드, 1바이트 풀, 하나의 블록 풀, 하나의 큐, 하나의 세마포, 하나의 뮤텍스 및 하나의 이벤트 플래그 그룹으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-108">The demonstration consists of initialization, eight threads, one byte pool, one block pool, one queue, one semaphore, one mutex, and one event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="8ba12-109">*스레드의 스택 크기를 제외하고 데모 애플리케이션은 모든 ThreadX 지원 프로세서에서 동일합니다.*</span><span class="sxs-lookup"><span data-stu-id="8ba12-109">*Except for the thread's stack size, the demonstration application is identical on all ThreadX supported processors.*</span></span>

<span data-ttu-id="8ba12-110">이 장의 나머지 부분에서 참조되는 줄 번호를 포함하는 ***demo_threadx.c*** 의 전체 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-110">The complete listing of ***demo_threadx.c***, including the line numbers referenced throughout the remainder of this chapter.</span></span>

## <a name="application-define"></a><span data-ttu-id="8ba12-111">애플리케이션 정의</span><span class="sxs-lookup"><span data-stu-id="8ba12-111">Application Define</span></span>

<span data-ttu-id="8ba12-112">***tx_application_define*** 함수는 기본 ThreadX 초기화가 완료된 후에 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-112">The ***tx_application_define*** function executes after the basic ThreadX initialization is complete.</span></span> <span data-ttu-id="8ba12-113">스레드, 큐, 세마포, 뮤텍스, 이벤트 플래그 및 메모리 풀을 비롯한 모든 초기 시스템 리소스를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-113">It is responsible for setting up all of the initial system resources, including threads, queues, semaphores, mutexes, event flags, and memory pools.</span></span>

<span data-ttu-id="8ba12-114">데모 시스템의 ***tx_application_define** _(_줄 번호 60-164*)은 데모 개체를 다음 순서로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-114">The demonstration system's ***tx_application_define** _ (_line numbers 60-164*) creates the demonstration objects in the following order:</span></span>

- <span data-ttu-id="8ba12-115">byte_pool_0</span><span class="sxs-lookup"><span data-stu-id="8ba12-115">byte_pool_0</span></span>
- <span data-ttu-id="8ba12-116">thread_0</span><span class="sxs-lookup"><span data-stu-id="8ba12-116">thread_0</span></span>
- <span data-ttu-id="8ba12-117">thread_1</span><span class="sxs-lookup"><span data-stu-id="8ba12-117">thread_1</span></span>
- <span data-ttu-id="8ba12-118">thread_2</span><span class="sxs-lookup"><span data-stu-id="8ba12-118">thread_2</span></span>
- <span data-ttu-id="8ba12-119">thread_3</span><span class="sxs-lookup"><span data-stu-id="8ba12-119">thread_3</span></span>
- <span data-ttu-id="8ba12-120">thread_4</span><span class="sxs-lookup"><span data-stu-id="8ba12-120">thread_4</span></span>
- <span data-ttu-id="8ba12-121">thread_5</span><span class="sxs-lookup"><span data-stu-id="8ba12-121">thread_5</span></span>
- <span data-ttu-id="8ba12-122">thread_6</span><span class="sxs-lookup"><span data-stu-id="8ba12-122">thread_6</span></span>
- <span data-ttu-id="8ba12-123">thread_7</span><span class="sxs-lookup"><span data-stu-id="8ba12-123">thread_7</span></span>
- <span data-ttu-id="8ba12-124">queue_0</span><span class="sxs-lookup"><span data-stu-id="8ba12-124">queue_0</span></span>
- <span data-ttu-id="8ba12-125">semaphore_0</span><span class="sxs-lookup"><span data-stu-id="8ba12-125">semaphore_0</span></span>
- <span data-ttu-id="8ba12-126">event_flags_0</span><span class="sxs-lookup"><span data-stu-id="8ba12-126">event_flags_0</span></span>
- <span data-ttu-id="8ba12-127">mutex_0</span><span class="sxs-lookup"><span data-stu-id="8ba12-127">mutex_0</span></span>
- <span data-ttu-id="8ba12-128">block_pool_0</span><span class="sxs-lookup"><span data-stu-id="8ba12-128">block_pool_0</span></span>

<span data-ttu-id="8ba12-129">데모 시스템은 다른 추가적인 ThreadX 개체를 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-129">The demonstration system does not create any other additional ThreadX objects.</span></span> <span data-ttu-id="8ba12-130">그러나 실제 애플리케이션은 실행 중인 스레드 내에서 런타임 중에 시스템 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-130">However, an actual application may create system objects during runtime inside of executing threads.</span></span>

### <a name="initial-execution"></a><span data-ttu-id="8ba12-131">초기 실행</span><span class="sxs-lookup"><span data-stu-id="8ba12-131">Initial Execution</span></span>

<span data-ttu-id="8ba12-132">모든 스레드는 **TX_AUTO_START** 옵션을 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-132">All threads are created with the **TX_AUTO_START** option.</span></span> <span data-ttu-id="8ba12-133">이렇게 하면 처음에 실행할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-133">This makes them initially ready for execution.</span></span> <span data-ttu-id="8ba12-134">***tx_application_define*** 이 완료되면 컨트롤이 스레드 스케줄러에 전송되며 거기서 각 개별 스레드로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-134">After ***tx_application_define*** completes, control is transferred to the thread scheduler and from there to each individual thread.</span></span>

<span data-ttu-id="8ba12-135">스레드가 실행되는 순서는 우선 순위 및 생성된 순서에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-135">The order in which the threads execute is determined by their priority and the order that they were created.</span></span> <span data-ttu-id="8ba12-136">데모 시스템에서 우선 순위가 가장 높은(*우선 순위 1로 생성*) ***thread_0*** 이 먼저 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-136">In the demonstration system, ***thread_0*** executes first because it has the highest priority (*it was created with a priority of 1*).</span></span> <span data-ttu-id="8ba12-137">***thread_0*** 이 일시 중단된 후에는 ***thread_5*** 가 실행된 다음, ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _*_thread_7_\*\*, \***thread_1**_ 이 실행되고, 마지막으로 _\*_thread_2_\*\*가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-137">After ***thread_0*** suspends, ***thread_5*** is executed, followed by the execution of ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _*_thread_7_\*\*, \***thread_1**_, and finally _\*_thread_2_\*\*.</span></span>

> [!NOTE]
> <span data-ttu-id="8ba12-138">***thread_3** 및 **thread_4** 의 우선 순위가 동일하더라도(둘 다 우선 순위 8로 생성됨), **thread_3** 이 먼저 실행됩니다. 이는 **thread_4** 보다 먼저 **thread_3** 이 생성되고 준비되었기 때문입니다. 우선 순위가 같은 스레드는 FIFO 방식으로 실행됩니다.*</span><span class="sxs-lookup"><span data-stu-id="8ba12-138">*Even though **thread_3** and **thread_4** have the same priority (both created with a priority of 8), **thread_3** executes first. This is because **thread_3** was created and became ready before **thread_4**. Threads of equal priority execute in a FIFO fashion.*</span></span>

## <a name="thread-0"></a><span data-ttu-id="8ba12-139">스레드 0</span><span class="sxs-lookup"><span data-stu-id="8ba12-139">Thread 0</span></span>

<span data-ttu-id="8ba12-140">함수 ***thread_0_entry*** 는 스레드의 진입점 *(167-190줄*)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-140">The function ***thread_0_entry*** marks the entry point of the thread *(lines 167-190*).</span></span> <span data-ttu-id="8ba12-141">***Thread_0*** 은 데모 시스템에서 첫 번째로 실행되는 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-141">***Thread_0*** is the first thread in the demonstration system to execute.</span></span> <span data-ttu-id="8ba12-142">해당 프로세스는 간단합니다. 카운터를 증가시키고, 10개 타이머 틱에 대해 대기하고, ***thread_5*** 를 해제하도록 이벤트 플래그를 설정한 다음, 시퀀스를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-142">Its processing is simple: it increments its counter, sleeps for 10 timer ticks, sets an event flag to wake up ***thread_5***, then repeats the sequence.</span></span>

<span data-ttu-id="8ba12-143">***Thread_0*** 은 시스템에서 가장 높은 우선 순위 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-143">***Thread_0*** is the highest priority thread in the system.</span></span> <span data-ttu-id="8ba12-144">요청된 일시 중지가 만료되면 데모에서 다른 실행 스레드를 선점합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-144">When its requested sleep expires, it will preempt any other executing thread in the demonstration.</span></span>

## <a name="thread-1"></a><span data-ttu-id="8ba12-145">스레드 1</span><span class="sxs-lookup"><span data-stu-id="8ba12-145">Thread 1</span></span>

<span data-ttu-id="8ba12-146">함수 ***thread_1_entry** _는 스레드의 진입점을 표시합니다 _(193-216줄 *). ***Thread_1*** 은 데모 시스템에서 끝에서 두 번째로 실행되는 스레드입니다. 해당 프로세스는 카운터를 증가시키고, ***thread_2*** 에 메시지를 보내고(* \*\*\*\*queue_0*\*\* 을 통해), 시퀀스를 반복하는 것으로 구성됩니다. \***thread_1**_ 은 _*_queue_0_*_ 이 가득 찰 때마다 일시 중단됩니다(_207줄\*).</span><span class="sxs-lookup"><span data-stu-id="8ba12-146">The function ***thread_1_entry** _ marks the entry point of the thread _(lines 193-216 *). ***Thread_1*** is the second-to-last thread in the demonstration system to execute. Its processing consists of incrementing its counter, sending a message to ***thread_2*** (* through* ***queue_0***), and repeating the sequence. Notice that \***thread_1**_ suspends whenever _*_queue_0_*_ becomes full (_line 207\*).</span></span>

## <a name="thread-2"></a><span data-ttu-id="8ba12-147">스레드 2</span><span class="sxs-lookup"><span data-stu-id="8ba12-147">Thread 2</span></span>

<span data-ttu-id="8ba12-148">함수 ***thread_2_entry*** 는 스레드의 진입점 *(219-243줄*)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-148">The function ***thread_2_entry*** marks the entry point of the thread *(lines 219-243*).</span></span> <span data-ttu-id="8ba12-149">***Thread_2*** 는 데모 시스템에서 마지막으로 실행되는 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-149">***Thread_2*** is the last thread in the demonstration system to execute.</span></span> <span data-ttu-id="8ba12-150">해당 프로세스는 카운터를 증가시키고, ***thread_1*** 에서 메시지를 가져오고(***queue_0*** 을 통해), 시퀀스를 반복하는 것으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-150">Its processing consists of incrementing its counter, getting a message from ***thread_1*** (through ***queue_0***), and repeating the sequence.</span></span> <span data-ttu-id="8ba12-151">***thread_2** 는 _*_queue_0_*_ 이 비어 있을 때마다 일시 중단됩니다(_233줄*).</span><span class="sxs-lookup"><span data-stu-id="8ba12-151">Notice that ***thread_2** _ suspends whenever _*_queue_0_*_ becomes empty (_line 233*).</span></span>

<span data-ttu-id="8ba12-152">***thread_1** _과 _ *_thread_2_\*\*가 데모 시스템에서 가장 낮은 우선 순위를 공유하긴 하지만(* 우선 순위 16*) *,*</span><span class="sxs-lookup"><span data-stu-id="8ba12-152">Although ***thread_1** _ and _ *_thread_2_** share the lowest priority in the demonstration system (\* priority 16\*), they *Threads 3 and 4*</span></span>

<span data-ttu-id="8ba12-153">대부분의 시간 동안 실행할 준비가 되어 있는 유일한 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-153">are also the only threads that are ready for execution most of the time.</span></span> <span data-ttu-id="8ba12-154">또한 이러한 스레드는 시간 조각화(*87줄 및 93줄*)를 사용하여 생성된 유일한 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-154">They are also the only threads created with time-slicing (*lines 87 and 93*).</span></span> <span data-ttu-id="8ba12-155">각 스레드는 다른 스레드가 실행되기 전에 최대 4개의 타이머 틱을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-155">Each thread is allowed to execute for a maximum of 4 timer ticks before the other thread is executed.</span></span>

## <a name="threads-3-and-4"></a><span data-ttu-id="8ba12-156">스레드 3 및 4</span><span class="sxs-lookup"><span data-stu-id="8ba12-156">Threads 3 and 4</span></span>

<span data-ttu-id="8ba12-157">***thread_3_and_4_entry*** 함수는 \***thread_3** _ 및 _ \*_thread_4_\*\*(246-280줄) 모두의 진입점을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-157">The function ***thread_3_and_4_entry*** marks the entry point of both ***thread_3** _ and _ *_thread_4_** (lines 246-280).</span></span> <span data-ttu-id="8ba12-158">두 스레드 모두 우선 순위가 8이며, 따라서 데모 시스템에서 세 번째와 네 번째로 실행되는 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-158">Both threads have a priority of 8, which makes them the third and fourth threads in the demonstration system to execute.</span></span> <span data-ttu-id="8ba12-159">각 스레드에 대한 프로세스는 동일합니다. 즉, 카운터를 증가시키고, ***semaphore_0*** 을 가져오고, 2개의 타이머 틱을 일시 중지하고, ***semaphore_0*** 을 해제한 후, 시퀀스를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-159">The processing for each thread is the same: incrementing its counter, getting ***semaphore_0***, sleeping for 2 timer ticks, releasing ***semaphore_0***, and repeating the sequence.</span></span> <span data-ttu-id="8ba12-160">***semaphore_0*** 을 사용할 수 없을 때마다 각 스레드가 일시 중단됩니다(264줄).</span><span class="sxs-lookup"><span data-stu-id="8ba12-160">Notice that each thread suspends whenever ***semaphore_0*** is unavailable (line 264).</span></span>

<span data-ttu-id="8ba12-161">또한 두 스레드 모두 주 프로세스에 동일한 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-161">Also both threads use the same function for their main processing.</span></span>
<span data-ttu-id="8ba12-162">여기에는 자체의 고유한 스택이 있고 C가 기본적으로 재진입되기 때문에 문제가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-162">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span> <span data-ttu-id="8ba12-163">각 스레드는 스레드 입력 매개 변수를 검사하여(258줄) 어떤 스레드인지 결정하며, 이는 생성될 때 설정됩니다(102 및 109줄).</span><span class="sxs-lookup"><span data-stu-id="8ba12-163">Each thread determines which one it is by examination of the thread input parameter (line 258), which is setup when they are created (lines 102 and 109).</span></span>

> [!NOTE]
> <span data-ttu-id="8ba12-164">*스레드를 실행하는 동안 현재 스레드 지점을 가져와서 이를 제어 블록의 주소와 비교하여 스레드 ID를 확인하는 것도 합리적입니다.*</span><span class="sxs-lookup"><span data-stu-id="8ba12-164">*It is also reasonable to obtain the current thread point during thread execution and compare it with the control block's address to determine thread identity.*</span></span>

## <a name="thread-5"></a><span data-ttu-id="8ba12-165">스레드 5</span><span class="sxs-lookup"><span data-stu-id="8ba12-165">Thread 5</span></span>

<span data-ttu-id="8ba12-166">함수 ***thread_5_entry*** 는 스레드의 진입점(283-305줄)을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-166">The function ***thread_5_entry*** marks the entry point of the thread (lines 283-305).</span></span> <span data-ttu-id="8ba12-167">***Thread_5*** 는 데모 시스템에서 두 번째로 실행되는 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-167">***Thread_5*** is the second thread in the demonstration system to execute.</span></span> <span data-ttu-id="8ba12-168">해당 프로세스는 카운터를 증가시키고, ***thread_0*** 에서 이벤트 플래그를 가져오고(***event_flags_0*** 을 통해), 시퀀스를 반복하는 것으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-168">Its processing consists of incrementing its counter, getting an event flag from ***thread_0*** (through ***event_flags_0***), and repeating the sequence.</span></span> <span data-ttu-id="8ba12-169">***event_flags_0*** 의 이벤트 플래그를 사용할 수 없는 경우(298줄) ***thread_5*** 가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-169">Notice that ***thread_5*** suspends whenever the event flag in ***event_flags_0*** is not available (line 298).</span></span>

## <a name="threads-6-and-7"></a><span data-ttu-id="8ba12-170">스레드 6 및 7</span><span class="sxs-lookup"><span data-stu-id="8ba12-170">Threads 6 and 7</span></span>

<span data-ttu-id="8ba12-171">***thread_6_and_7_entry*** 함수는 \***thread_6** _ 및 _ \*_thread_7_\*\*(307-358줄) 모두의 진입점을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-171">The function ***thread_6_and_7_entry*** marks the entry point of both ***thread_6** _ and _ *_thread_7_** (lines 307-358).</span></span> <span data-ttu-id="8ba12-172">두 스레드 모두 우선 순위가 8이며, 따라서 데모 시스템에서 다섯 번째와 여섯 번째로 실행되는 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-172">Both threads have a priority of 8, which makes them the fifth and sixth threads in the demonstration system to execute.</span></span> <span data-ttu-id="8ba12-173">각 스레드에 대한 프로세스는 동일합니다. 즉, 카운터를 증가시키고, ***mutex_0*** 을 두 번 가져오고, 2개의 타이머 틱을 일시 중지하고, ***mutex_0*** 을 두 번 해제한 후, 시퀀스를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-173">The processing for each thread is the same: incrementing its counter, getting ***mutex_0*** twice, sleeping for 2 timer ticks, releasing ***mutex_0*** twice, and repeating the sequence.</span></span> <span data-ttu-id="8ba12-174">***mutex_0*** 을 사용할 수 없을 때마다 각 스레드가 일시 중단됩니다(325줄).</span><span class="sxs-lookup"><span data-stu-id="8ba12-174">Notice that each thread suspends whenever ***mutex_0*** is unavailable (line 325).</span></span>

<span data-ttu-id="8ba12-175">또한 두 스레드 모두 주 프로세스에 동일한 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-175">Also both threads use the same function for their main processing.</span></span> <span data-ttu-id="8ba12-176">여기에는 자체의 고유한 스택이 있고 C가 기본적으로 재진입되기 때문에 문제가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-176">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span>
<span data-ttu-id="8ba12-177">각 스레드는 스레드 입력 매개 변수를 검사하여(319줄) 어떤 스레드인지 결정하며, 이는 생성될 때 설정됩니다(126 및 133줄).</span><span class="sxs-lookup"><span data-stu-id="8ba12-177">Each thread determines which one it is by examination of the thread input parameter (line 319), which is setup when they are created (lines 126 and 133).</span></span>

## <a name="observing-the-demonstration"></a><span data-ttu-id="8ba12-178">데모 관찰</span><span class="sxs-lookup"><span data-stu-id="8ba12-178">Observing the Demonstration</span></span>

<span data-ttu-id="8ba12-179">각 데모 스레드는 고유한 카운터를 증가시킵니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-179">Each of the demonstration threads increments its own unique counter.</span></span>
<span data-ttu-id="8ba12-180">다음 카운터를 검사하여 데모의 작업을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-180">The following counters may be examined to check on the demo's operation:</span></span>

- <span data-ttu-id="8ba12-181">thread_0_counter</span><span class="sxs-lookup"><span data-stu-id="8ba12-181">thread_0_counter</span></span>
- <span data-ttu-id="8ba12-182">thread_1_counter</span><span class="sxs-lookup"><span data-stu-id="8ba12-182">thread_1_counter</span></span>
- <span data-ttu-id="8ba12-183">thread_2_counter</span><span class="sxs-lookup"><span data-stu-id="8ba12-183">thread_2_counter</span></span>
- <span data-ttu-id="8ba12-184">thread_3_counter</span><span class="sxs-lookup"><span data-stu-id="8ba12-184">thread_3_counter</span></span>
- <span data-ttu-id="8ba12-185">thread_4_counter</span><span class="sxs-lookup"><span data-stu-id="8ba12-185">thread_4_counter</span></span>
- <span data-ttu-id="8ba12-186">thread_5_counter</span><span class="sxs-lookup"><span data-stu-id="8ba12-186">thread_5_counter</span></span>
- <span data-ttu-id="8ba12-187">thread_6_counter</span><span class="sxs-lookup"><span data-stu-id="8ba12-187">thread_6_counter</span></span>
- <span data-ttu-id="8ba12-188">thread_7_counter</span><span class="sxs-lookup"><span data-stu-id="8ba12-188">thread_7_counter</span></span>

<span data-ttu-id="8ba12-189">이러한 각 카운터는 데모를 실행할 때 계속 증가해야 하며, \***thread_1_counter** _ 및 _ \*_thread_2_counter_\*\*가 가장 빠른 속도로 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-189">Each of these counters should continue to increase as the demonstration executes, with ***thread_1_counter** _ and _ *_thread_2_counter_** increasing at the fastest rate.</span></span>

## <a name="distribution-file-demo_threadxc"></a><span data-ttu-id="8ba12-190">배포 파일: demo_threadx.c</span><span class="sxs-lookup"><span data-stu-id="8ba12-190">Distribution file: demo_threadx.c</span></span>

<span data-ttu-id="8ba12-191">이 섹션에는 이 장 전반에 걸쳐 참조되는 줄 번호를 포함하는 ***demo_threadx.c*** 의 전체 목록이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba12-191">This section displays the complete listing of ***demo_threadx.c***, including the line numbers referenced throughout this chapter.</span></span>

```c
/* This is a small demo of the high-performance ThreadX kernel. It includes examples of eight
threads of different priorities, using a message queue, semaphore, mutex, event flags group,
byte pool, and block pool. */

#include "tx_api.h"

#define DEMO_STACK_SIZE 1024
#define DEMO_BYTE_POOL_SIZE 9120
#define DEMO_BLOCK_POOL_SIZE 100
#define DEMO_QUEUE_SIZE 100

/* Define the ThreadX object control blocks... */

TX_THREAD thread_0;
TX_THREAD thread_1;
TX_THREAD thread_2;
TX_THREAD thread_3;
TX_THREAD thread_4;
TX_THREAD thread_5;
TX_THREAD thread_6;
TX_THREAD thread_7;
TX_QUEUE queue_0;
TX_SEMAPHORE semaphore_0;
TX_MUTEX mutex_0;
TX_EVENT_FLAGS_GROUP event_flags_0;
TX_BYTE_POOL byte_pool_0;
TX_BLOCK_POOL block_pool_0;

/* Define the counters used in the demo application... */

ULONG thread_0_counter;
ULONG thread_1_counter;
ULONG thread_1_messages_sent;
ULONG thread_2_counter;
ULONG thread_2_messages_received;
ULONG thread_3_counter;
ULONG thread_4_counter;
ULONG thread_5_counter;
ULONG thread_6_counter;
ULONG thread_7_counter;

/* Define thread prototypes. */

void thread_0_entry(ULONG thread_input);
void thread_1_entry(ULONG thread_input);
void thread_2_entry(ULONG thread_input);
void thread_3_and_4_entry(ULONG thread_input);
void thread_5_entry(ULONG thread_input);
void thread_6_and_7_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

    CHAR *pointer;

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
        DEMO_BYTE_POOL_SIZE);

    /* Put system definition stuff in here, e.g., thread creates and other assorted
        create information. */

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through a ThreadX
        message queue. It is also interesting to note that these threads have a time
        slice. */
    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 2. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
        tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX counting semaphore.
        An interesting thing here is that both threads share the same instruction area. */
    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 4. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag, which will be set
        by thread_0. */
    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 7. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(&event_flags_0, "event flags 0");

    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool to allocate a message buffer from. */
    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
        DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block and release the block memory. */
    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);
}

/* Define the test threads. */
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

        /* Set event flag 0 to wakeup thread 5. */
        status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_1_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sends messages to a queue shared by thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);

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
        status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what we
        expected. */
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
        status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(&semaphore_0);

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
        status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
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
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows
            that an owning thread may retrieve the mutex it
            owns multiple times. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually
            release ownership since it was obtained twice. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```
