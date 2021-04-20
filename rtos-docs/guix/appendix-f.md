---
title: 부록 F - GUIX RTOS 바인딩 서비스
description: GUIX RTOS 바인딩 서비스에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d94dbb9d7d53ec3e1900188142974cc981dfea9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812085"
---
# <a name="appendix-f---guix-rtos-binding-services"></a><span data-ttu-id="5022c-103">부록 F - GUIX RTOS 바인딩 서비스</span><span class="sxs-lookup"><span data-stu-id="5022c-103">Appendix F - GUIX RTOS Binding Services</span></span>

<span data-ttu-id="5022c-104">GUIX에는 기본 RTOS에서 제공하는 스레드 또는 태스킹 서비스, 뮤텍스, 이벤트 큐 및 타이밍 서비스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-104">GUIX requires thread or tasking services, mutex, event queue, and timing services providing by the underlying RTOS.</span></span> <span data-ttu-id="5022c-105">기본적으로 GUIX는 ThreadX 실시간 운영 체제를 활용하여 이러한 서비스를 제공하도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-105">By default GUIX is configured to utilize the ThreadX real time operating system to provide these services.</span></span> <span data-ttu-id="5022c-106">GUIX를 다른 운영 체제로 이식하려면 개발자는 전처리기 지시문 GX_DISABLE_THREADX_BINDING을 # 정의하고 GUIX 라이브러리를 다시 빌드하여 ThreadX 종속성을 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-106">To port GUIX to another operating system, the developer should # define the pre-processor directive GX_DISABLE_THREADX_BINDING and rebuild the GUIX library to remove the ThreadX dependencies.</span></span> <span data-ttu-id="5022c-107">또한 개발자는 다음 매크로 정의 및 지원 함수를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-107">In addition, the developer will need to provide the following macro definitions and supporting functions.</span></span> <span data-ttu-id="5022c-108">이러한 매크로 정의 및 지원 함수의 예는 일반적인 rtos 통합 예제를 제공하는 파일 gx_system_rtos_bind.h 및 gx_system_rtos_bind.c에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-108">Examples of these macro definitions and supporting functions can be found in the files gx_system_rtos_bind.h and gx_system_rtos_bind.c, which provide an example generic rtos integration.</span></span>

<span data-ttu-id="5022c-109">시스템 통합 매크로:</span><span class="sxs-lookup"><span data-stu-id="5022c-109">System Integration macros:</span></span>

<span data-ttu-id="5022c-110">**GX_RTOS_BINDING_INITIALIZE**</span><span class="sxs-lookup"><span data-stu-id="5022c-110">**GX_RTOS_BINDING_INITIALIZE**</span></span>

<span data-ttu-id="5022c-111">이 매크로는 시스템 초기화 중에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-111">This macro is invoked during system initialization.</span></span> <span data-ttu-id="5022c-112">사용하기 전에 rtos 시스템 서비스 또는 rtos 리소스를 준비하는 데 필요한 함수를 호출하도록 매크로를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-112">The macro should be defined to call any function needed to prepare your rtos system services or rtos resources prior to use.</span></span> <span data-ttu-id="5022c-113">이것은 GUIX에서 사용할 rtos 리소스를 준비하기 위한 바인딩의 기회입니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-113">This is the binding’s opportunity to prepare the rtos resources that GUIX will use.</span></span>

<span data-ttu-id="5022c-114">**GX_SYSTEM_THREAD_START**</span><span class="sxs-lookup"><span data-stu-id="5022c-114">**GX_SYSTEM_THREAD_START**</span></span>

<span data-ttu-id="5022c-115">이 매크로는 GUIX 작업 또는 스레드가 실행을 시작해야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-115">This macro is invoked when the GUIX task or thread should start executing.</span></span> <span data-ttu-id="5022c-116">이 매크로는 실행 중인 GUIX 스레드를 시작하는 함수를 호출하도록 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-116">This macro should be defined to call a function which will start the GUIX thread running.</span></span> <span data-ttu-id="5022c-117">GUIX 스레드의 진입점은 호출된 함수에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-117">The entry point to the GUIX thread is passed to the called function.</span></span> <span data-ttu-id="5022c-118">호출된 함수의 서명은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-118">The signature of the called function must be</span></span>

<span data-ttu-id="5022c-119">**UINT *function_name*(VOID (thread_entry_point)(VOID));**</span><span class="sxs-lookup"><span data-stu-id="5022c-119">**UINT *function_name*(VOID (thread_entry_point)(VOID));**</span></span>

<span data-ttu-id="5022c-120">이 함수는 스레드가 성공적으로 시작된 경우 GX_SUCCESS를 반환해야 하며, 그렇지 않으면 GX_FAILURE를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-120">This function should return GX_SUCCESS if the thread is successfully started, or GX_FAILURE.</span></span>

<span data-ttu-id="5022c-121">**GX_EVENT_PUSH**</span><span class="sxs-lookup"><span data-stu-id="5022c-121">**GX_EVENT_PUSH**</span></span>

<span data-ttu-id="5022c-122">이 매크로는 GUIX에서 사용하는 FIFO 이벤트 큐에 이벤트를 푸시하기 위해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-122">This macro is invoked to push an event into the FIFO event queue used by GUIX.</span></span> <span data-ttu-id="5022c-123">새 rtos로 이식할 때 이 이벤트 큐를 스레드로부터 안전한 방식으로 구현하는 것은 사용자의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-123">When porting to a new rtos, it is your responsibility to implement this event queue in a thread-safe manner.</span></span> <span data-ttu-id="5022c-124">GX_EVENT 구조체를 이 큐로 복사하고 이 큐에서 복사해야 합니다. 즉, GUIX 이벤트는 이벤트 생산자의 뷰에서 자동 변수가 될 수 있으므로 GX_EVENT 포인터의 큐가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-124">GX_EVENT structures must be copied into this queue and copied out of this queue, i.e. a queue of GX_EVENT pointers will not work, since GUIX events can be automatic variables from the view of the event producer.</span></span> <span data-ttu-id="5022c-125">이 매크로에 의해 호출되는 함수의 서명은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-125">The signature of the function called by this macro must be:</span></span>

<span data-ttu-id="5022c-126">\**UINT *function_name* (GX_EVENT *event_ptr);**</span><span class="sxs-lookup"><span data-stu-id="5022c-126">\**UINT *function_name* (GX_EVENT *event_ptr);**</span></span>

<span data-ttu-id="5022c-127">이벤트가 이벤트 큐로 푸시되는 경우 이 함수는 GX_SUCCESS을 반환해야 하며, 그렇지 않으면 GX_FAILURE을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-127">This function should return GX_SUCCESS if the event is pushed into the event queue, otherwise it should return GX_FAILURE.</span></span>

<span data-ttu-id="5022c-128">**GX_EVENT_POP**</span><span class="sxs-lookup"><span data-stu-id="5022c-128">**GX_EVENT_POP**</span></span>

<span data-ttu-id="5022c-129">이 매크로는 GUIX 이벤트 큐에서 head(가장 오래 된) 이벤트를 제거하고 요청된 위치에 복사하기 위해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-129">This macro is invoked to remove the head (oldest) event from the GUIX event queue and copy it into the requested location.</span></span> <span data-ttu-id="5022c-130">이벤트 큐에 현재 이벤트가 없으면, 이 함수는 필요에 따라 이벤트를 차단하거나 이벤트를 대기할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-130">This function must be able to optionally block or wait for an event if no events are currently in the event queue.</span></span> <span data-ttu-id="5022c-131">이 매크로에 의해 호출되는 함수의 서명은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-131">The signature of the function invoked by this macro must be</span></span>

<span data-ttu-id="5022c-132">UINT function_name (GX_EVENT \* put_event, GX_BOOL wait)</span><span class="sxs-lookup"><span data-stu-id="5022c-132">UINT function_name(GX_EVENT \*put_event, GX_BOOL wait)</span></span>

<span data-ttu-id="5022c-133">Wait 매개 변수가 GX_TRUE이면 이벤트를 제공할 때까지 함수가 반환되어서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-133">If the wait parameter == GX_TRUE, the function should not return until an event is provided.</span></span> <span data-ttu-id="5022c-134">Wait 매개 변수가 GX_FALSE이면 함수는 이벤트를 사용하거나 사용하지 않고 즉시 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-134">If the wait parameter is GX_FALSE, the function should return immediately with or without an event.</span></span>

<span data-ttu-id="5022c-135">큐에서 이벤트를 검색하면 put_event 위치로 복사 되고 반환 상태는 GX_SUCCESS가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-135">If an event is retrieved from the queue, it should copied into the put_event location and the return status is GX_SUCCESS.</span></span> <span data-ttu-id="5022c-136">그렇지 않으면 반환 상태는 GX_FAILURE여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-136">Otherwise the return status should be GX_FAILURE.</span></span>

<span data-ttu-id="5022c-137">**GX_EVENT_FOLD**</span><span class="sxs-lookup"><span data-stu-id="5022c-137">**GX_EVENT_FOLD**</span></span>

<span data-ttu-id="5022c-138">이 매크로는 이벤트를 FIFO 이벤트 큐로 접도록 GUIX에서 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-138">This macro is invoked by GUIX to fold an event into the FIFO event queue.</span></span> <span data-ttu-id="5022c-139">이벤트 접기는 동일한 유형의 이벤트가 큐에 이미 있는 경우, 해당 항목이 새 이벤트의 페이로드를 포함하는 업데이트임을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-139">Folding an event means that if an event of the same type already exists in the queue, that entry is update to contain the payload of the new event.</span></span> <span data-ttu-id="5022c-140">동일한 유형의 기존 이벤트를 큐에서 찾을 수 없는 경우, 새 이벤트가 큐로 푸시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-140">If an existing event of the same type is not found in the queue, a new event is pushed into the queue.</span></span> 

<span data-ttu-id="5022c-141">이벤트 접기 기능을 구현할 수 없는 바인딩의 경우 단순히 GX_EVENT_PUSH 호출하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-141">For bindings that cannot implement the event fold feature, it is acceptable to simply invoke the GX_EVENT_PUSH.</span></span>

<span data-ttu-id="5022c-142">**GX_TIMER_START**</span><span class="sxs-lookup"><span data-stu-id="5022c-142">**GX_TIMER_START**</span></span>

<span data-ttu-id="5022c-143">이 매크로는 GUIX가 주기적 타이머 입력을 받아야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-143">This macro is invoked when GUIX needs to receive periodic timer input.</span></span> <span data-ttu-id="5022c-144">이 매크로는 하위 수준 RTOS 주기적 타이머 서비스를 시작하는 서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-144">This macro should invoke a service that starts the low-level RTOS periodic timer service.</span></span> <span data-ttu-id="5022c-145">RTOS 타이머 서비스를 쉽게 중지하고 시작할 수 없다면, 이 서비스를 항상 실행 상태로 유지하는 것이 허용되지만 효율성이 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-145">If the RTOS timer service cannot be easily stopped and started, it is acceptable but less efficient to leave this service running at all times.</span></span>

<span data-ttu-id="5022c-146">하위 수준 RTOS 타이머 서비스가 주기적으로 만료되면 바인딩에서 GUIX 시스템 함수 _gx_system_timer_expiration(0);을 호출해야 합니다. 이 함수를 주기적으로 호출하면 상위 수준의 GUIX 타이머 위젯 타이머 서비스를 구동하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-146">When the low-level RTOS timer service periodically expires, the binding must call the GUIX system function _gx_system_timer_expiration(0); Calling this function periodically is what drives the high-level GUIX timer widget timer services.</span></span>

<span data-ttu-id="5022c-147">**GX_TIMER_STOP**</span><span class="sxs-lookup"><span data-stu-id="5022c-147">**GX_TIMER_STOP**</span></span>

<span data-ttu-id="5022c-148">GUIX에 더 이상 주기적 타이머가 필요로 하지 않을 때(즉, 실행되는 활성 GUIX 타이머가 없을 때) 이 매크로가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-148">This macro is invoked when GUIX no longer needs a periodic timer (i.e. there are no active GUIX timers running).</span></span> <span data-ttu-id="5022c-149">RTOS 타이머 서비스를 쉽게 중지하고 시작할 수 없다면, 이 서비스를 항상 실행 상태로 유지하고 이 매크로가 아무것도 수행하지 않도록 정의하는 것은 허용되지만 효율성이 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-149">If the RTOS timer service cannot be easily stopped and started, it is acceptable but less efficient to leave this service running at all times and define this macro to do nothing.</span></span>

<span data-ttu-id="5022c-150">**GX_SYSTEM_MUTEX_LOCK**</span><span class="sxs-lookup"><span data-stu-id="5022c-150">**GX_SYSTEM_MUTEX_LOCK**</span></span>

<span data-ttu-id="5022c-151">이 매크로는 중요한 코드 섹션 중에 GUIX에서 호출하여 다른 작업이 선점하고 공통 데이터 구조를 수정하여 잠재적인 손상을 일으키는 것을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-151">This macro is invoked by GUIX during critical code sections to prevent another task from  pre-empting and modifying common data structures, potentially causing corruption.</span></span> <span data-ttu-id="5022c-152">이 매크로는 적절한 RTOS 리소스 잠금 서비스를 구현하는 함수를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-152">This macro should call a function that implements the suitable RTOS resource locking service.</span></span>

<span data-ttu-id="5022c-153">GUIX 스레드 외부에서 GUIX API 서비스를 활용하지 않는다면 이 매크로를 아무 작업도 수행하지 않도록 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-153">If you never utilize any GUIX API services outside of the GUIX thread, you can define this macro to do nothing.</span></span>

<span data-ttu-id="5022c-154">**GX_SYSTEM_MUTEX_UNLOCK**</span><span class="sxs-lookup"><span data-stu-id="5022c-154">**GX_SYSTEM_MUTEX_UNLOCK**</span></span>

<span data-ttu-id="5022c-155">이 매크로는 중요한 코드 섹션의 끝에서 호출되며 적절한 기본 RTOS 서비스를 사용하여 GUIX 리소스를 잠금 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-155">This macro is invoked at the end of critical code sections, and should unlock the GUIX resource using the suitable underlying RTOS service.</span></span> <span data-ttu-id="5022c-156">GUIX 스레드 외부에서 GUIX API 서비스를 활용하지 않는다면 이 매크로를 아무 작업도 수행하지 않도록 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-156">If you never utilize any GUIX API services outside of the GUIX thread, you can define this macro to do nothing.</span></span>

<span data-ttu-id="5022c-157">**GX_SYSTEM_TIME_GET**</span><span class="sxs-lookup"><span data-stu-id="5022c-157">**GX_SYSTEM_TIME_GET**</span></span>

<span data-ttu-id="5022c-158">이 매크로는 현재 시스템 시간인 “시스템 틱”을 반환하는 함수를 호출해야 합니다. 이는 일반적으로 시스템 시작 이후 발생한 하위 수준 타이머 인터럽트의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-158">This macro should call a function that returns the current system time is “system ticks”, which is usually the number of low-level timer interrupts that have occurred since system startup.</span></span> <span data-ttu-id="5022c-159">이 서비스는 터치 입력 제스처에 대한 터치 이벤트 펜 속도를 계산하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-159">This service is used to calculate touch event pen speed for touch input gestures.</span></span> <span data-ttu-id="5022c-160">이 매크로에서 호출하는 함수의 서명은 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-160">The signature of the function invoked by this macro must be:</span></span>

<span data-ttu-id="5022c-161">**ULONG *function_name*(VOID);**</span><span class="sxs-lookup"><span data-stu-id="5022c-161">**ULONG *function_name*(VOID);**</span></span>

<span data-ttu-id="5022c-162">**GX_CURRENT_THREAD**</span><span class="sxs-lookup"><span data-stu-id="5022c-162">**GX_CURRENT_THREAD**</span></span>

<span data-ttu-id="5022c-163">이 매크로는 현재 실행 중인 스레드를 식별하기 위해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-163">This macro is invoked to identify the currently executing thread.</span></span> <span data-ttu-id="5022c-164">이 매크로에서 호출하는 서비스는 void*를 반환해야 합니다. 즉, 운영 체제에서 현재 실행 스레드를 식별하기 위해 사용하는 데이터 형식이 void*로 캐스팅되어 GUX로 반환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-164">The service called by this macro must return a void \*, meaning that the data type used by your operating system to identify the current execution thread must be cast to a void \* to be returned to GUX.</span></span>

<span data-ttu-id="5022c-165">일반 RTOS 바인딩의 전체 예제는 gx_system_rtos_bind. h 및 gx_system_rtos_bind 파일에서 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="5022c-165">A complete example of a generic RTOS binding is implemented in the filed gx_system_rtos_bind.h and gx_system_rtos_bind.c</span></span>