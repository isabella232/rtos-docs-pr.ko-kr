---
title: Azure RTOS TraceX 이해
description: Azure RTOS TraceX는 시스템 개발자에게 실시간 시스템 이벤트에 대한 그래픽 보기를 제공하고, 실시간 시스템의 동작을 시각화하여 더 잘 이해할 수 있도록 하는 Microsoft 호스트 기반 분석 도구입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 9fd33eec6da69e6dda421a125a2dde5eae93b46d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813441"
---
# <a name="overview-of-azure-rtos-tracex"></a><span data-ttu-id="98da6-103">Azure RTOS TraceX 개요</span><span class="sxs-lookup"><span data-stu-id="98da6-103">Overview of Azure RTOS TraceX</span></span>

<span data-ttu-id="98da6-104">Azure RTOS TraceX는 시스템 개발자에게 실시간 시스템 이벤트에 대한 그래픽 보기를 제공하고, 실시간 시스템의 동작을 시각화하여 더 잘 이해할 수 있도록 하는 Microsoft 호스트 기반 분석 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-104">Azure RTOS TraceX is Microsoft's host-based analysis tool that provides developers with a graphical view of real-time system events and enables them to visualize and better understand the behavior of their real-time systems.</span></span> <span data-ttu-id="98da6-105">개발자는 Azure RTOS TraceX를 사용하여 표준 디버깅 도구로 포착하지 못하는 인터럽트 및 컨텍스트 전환 같은 시스템 이벤트의 발생을 명확하게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-105">With Azure RTOS TraceX, developers can see clearly the occurrence of system events like interrupts and context switches that occur out of view of standard debugging tools.</span></span> <span data-ttu-id="98da6-106">이러한 이벤트를 식별 및 연구하고 전반적인 시스템 작업의 컨텍스트에서 이벤트가 발생하는 시간을 정확하게 파악하는 기능을 통해 개발자는 예기치 않은 동작을 찾아 특정 영역을 조사하여 프로그래밍 문제를 해결할 수 있습니다. 추적 정보는 런타임 시 애플리케이션에 의해 결정된 버퍼 위치와 크기를 사용하여 대상 시스템의 버퍼에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-106">The ability to identify and study these events, and to pinpoint the timing of their occurrence in the context of the overall system’s operation enables developers to resolve programming problems by finding unexpected behavior and letting them investigate specific areas further Trace information is stored in a buffer on the target system, with the buffer location and size determined by the application at run-time.</span></span> <span data-ttu-id="98da6-107">Azure RTOS TraceX는 Azure RTOS ThreadX뿐만 아니라 모든 애플리케이션 또는 RTOS에서 적절한 방식으로 생성된 버퍼를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-107">Azure RTOS TraceX can process any buffer constructed in the proper manner, not only from Azure RTOS ThreadX, but from any application or RTOS.</span></span> <span data-ttu-id="98da6-108">추적 정보는 분석을 위해 언제든지(사후 또는 중단 시) 호스트로 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-108">The trace information may be uploaded to the host for analysis at any time – either post mortem or upon a breakpoint.</span></span> <span data-ttu-id="98da6-109">Azure RTOS ThreadX는 시스템 오작동 또는 기타 중요한 이벤트 발생 시 최근의 "N"개 이벤트를 검사할 수 있도록 하는 순환 버퍼를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-109">Azure RTOS ThreadX implements a circular buffer, which enables the most recent “N” events to be available for inspection in the event of system malfunction or other significant event.</span></span>

![Azure RTOS TraceX Single-Core 표시](./media/user-guide/screen_shot_33.png)

<span data-ttu-id="98da6-111">**TraceX Single-Core 표시**</span><span class="sxs-lookup"><span data-stu-id="98da6-111">**TraceX Single-Core Display**</span></span>

## <a name="key-capabilites"></a><span data-ttu-id="98da6-112">주요 기능</span><span class="sxs-lookup"><span data-stu-id="98da6-112">Key capabilites</span></span>

### <a name="azure-rtos-tracex-built-in-system-analysis"></a><span data-ttu-id="98da6-113">Azure RTOS TraceX 기본 제공 시스템 분석</span><span class="sxs-lookup"><span data-stu-id="98da6-113">Azure RTOS TraceX built-in system analysis</span></span>

<span data-ttu-id="98da6-114">Azure RTOS TraceX는 TraceX 도구 모음에서 단일 단추 클릭을 통해 사용할 수 있는 기본 제공 시스템 분석 보고서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-114">Azure RTOS TraceX is provides built-in system analysis reports that are available via a single button click from the TraceX toolbar.</span></span> <span data-ttu-id="98da6-115">이러한 단추와 보고서에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-115">These buttons and reports include:</span></span>

![실행 프로필 생성 보고서](./media/overview-tracex/execution-profile-report-button.jpg) <span data-ttu-id="98da6-117">실행 프로필 생성 보고서</span><span class="sxs-lookup"><span data-stu-id="98da6-117">Generate Execution Profile report</span></span>

![성능 통계 생성 보고서](./media/overview-tracex/performance-statistics-report-button.jpg) <span data-ttu-id="98da6-119">성능 통계 생성 보고서</span><span class="sxs-lookup"><span data-stu-id="98da6-119">Generate Performance Statistics report</span></span>

![스레드 스택 사용량 생성 보고서](./media/overview-tracex/thread-stack-usage-report-button.jpg) <span data-ttu-id="98da6-121">스레드 스택 사용량 생성 보고서</span><span class="sxs-lookup"><span data-stu-id="98da6-121">Generate Thread Stack Usage report</span></span>

### <a name="trace-data-collected-by-azure-rtos-threadx"></a><span data-ttu-id="98da6-122">Azure RTOS ThreadX에서 수집된 추적 데이터</span><span class="sxs-lookup"><span data-stu-id="98da6-122">Trace data collected By Azure RTOS ThreadX</span></span>

<span data-ttu-id="98da6-123">Azure RTOS TraceX는 런타임 중에 대상 시스템에서 시스템 및 애플리케이션 "이벤트"의 데이터베이스를 생성하는 Azure RTOS ThreadX에서 작동하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-123">Azure RTOS TraceX is designed to work with Azure RTOS ThreadX, which constructs a database of system and application “events” on the target system during run-time.</span></span> <span data-ttu-id="98da6-124">이러한 이벤트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-124">These events include:</span></span>

* <span data-ttu-id="98da6-125">스레드 컨텍스트 전환</span><span class="sxs-lookup"><span data-stu-id="98da6-125">thread context switches</span></span>
* <span data-ttu-id="98da6-126">선점</span><span class="sxs-lookup"><span data-stu-id="98da6-126">preemptions</span></span>
* <span data-ttu-id="98da6-127">일시 중단</span><span class="sxs-lookup"><span data-stu-id="98da6-127">suspensions</span></span>
* <span data-ttu-id="98da6-128">종료</span><span class="sxs-lookup"><span data-stu-id="98da6-128">terminations</span></span>
* <span data-ttu-id="98da6-129">시스템 인터럽트</span><span class="sxs-lookup"><span data-stu-id="98da6-129">system interrupts</span></span>
* <span data-ttu-id="98da6-130">애플리케이션별 이벤트</span><span class="sxs-lookup"><span data-stu-id="98da6-130">application-specific events</span></span>
* <span data-ttu-id="98da6-131">모든 Azure RTOS ThreadX API 호출</span><span class="sxs-lookup"><span data-stu-id="98da6-131">all Azure RTOS ThreadX API calls</span></span>
* <span data-ttu-id="98da6-132">모든 Azure RTOS NetX API 호출</span><span class="sxs-lookup"><span data-stu-id="98da6-132">all Azure RTOS NetX API calls</span></span>
* <span data-ttu-id="98da6-133">모든 Azure RTOS FileX API 호출</span><span class="sxs-lookup"><span data-stu-id="98da6-133">all Azure RTOS FileX API calls</span></span>
* <span data-ttu-id="98da6-134">모든 Azure RTOS USBX API 호출</span><span class="sxs-lookup"><span data-stu-id="98da6-134">all Azure RTOS USBX API calls</span></span>
* <span data-ttu-id="98da6-135">애플리케이션 정의 아이콘 및 정보</span><span class="sxs-lookup"><span data-stu-id="98da6-135">application-defined icons and information</span></span>

<span data-ttu-id="98da6-136">이벤트는 타임스탬프 및 활성 스레드 ID를 사용하여 프로그램 제어를 통해 기록되므로 나중에 적절한 시간 순서로 표시하고 적절한 스레드와 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-136">Events are logged under program control, with time-stamping and active thread identification so they can be displayed later in the proper time sequence, and associated with the appropriate thread.</span></span> <span data-ttu-id="98da6-137">이벤트 로깅은 애플리케이션에서 동적으로 중지한 후 다시 시작할 수 있습니다(예: 관심 영역이 있는 경우).</span><span class="sxs-lookup"><span data-stu-id="98da6-137">Event logging may be stopped and restarted by the application program dynamically, for example, when an area of interest is encountered.</span></span> <span data-ttu-id="98da6-138">이렇게 하면 시스템이 제대로 수행될 때 데이터베이스가 복잡해지지 않도록 하고 대상 메모리를 최대로 사용하는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-138">This avoids cluttering the database and using up target memory when the system is performing correctly.</span></span>

### <a name="azure-rtos-tracex-is-like-a-software-logic-analyzer"></a><span data-ttu-id="98da6-139">Azure RTOS TraceX는 소프트웨어 논리 분석기와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-139">Azure RTOS TraceX is like a software logic analyzer</span></span>

<span data-ttu-id="98da6-140">이벤트 로그가 대상 메모리에서 호스트로 업로드되면 Azure RTOS TraceX는 이벤트가 세로 축을 따라 나열된 다양한 애플리케이션 스레드 및 시스템 루틴을 사용하여 시간을 나타내는 가로 축에 그래픽으로 이벤트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-140">Once the event log has been uploaded from target memory to the host, Azure RTOS TraceX displays the events graphically on a horizontal axis representing time, with the various application threads and system routines to which the events are related listed along the vertical axis.</span></span> <span data-ttu-id="98da6-141">Azure RTOS TraceX는 호스트에서 "소프트웨어 논리 분석기"를 만들어 시스템 이벤트를 명확하게 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-141">Azure RTOS TraceX creates a “software logic analyzer” on the host, making system events plainly visible.</span></span> <span data-ttu-id="98da6-142">이벤트는 관련 스레드 또는 시스템 루틴의 오른쪽에 가로 시간 표시줄을 따라 발생 지점에 위치한 색으로 구분된 아이콘으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-142">Events are represented by color coded icons, located at the point of occurrence along the horizontal timeline, to the right of the relevant thread or system routine.</span></span> <span data-ttu-id="98da6-143">이벤트 아이콘을 선택하면 해당 이벤트에 대한 정보가 두 개의 이전 이벤트 및 두 개의 후속 이벤트에 대한 정보와 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-143">When an event icon is selected, the corresponding information for that event is displayed, as well as the information for the two previous and two subsequent events.</span></span> <span data-ttu-id="98da6-144">이를 통해 이벤트 및 그 주변의 이벤트와 관련한 가장 즉각적인 정보에 단일 클릭으로 빠르게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-144">This provides quick, single-click access to the most immediate information about the event and its immediately surrounding events.</span></span> <span data-ttu-id="98da6-145">Azure RTOS TraceX는 단일 가로선에 모든 시스템 이벤트를 표시하는 "요약" 표시를 제공하여 많은 스레드를 포함하는 시스템의 분석을 간소화합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-145">Azure RTOS TraceX provides a “Summary” display that shows all system events on a single horizontal line to simplify analysis of systems with many threads.</span></span>

### <a name="sequential-view-mode"></a><span data-ttu-id="98da6-146">순차 보기 모드</span><span class="sxs-lookup"><span data-stu-id="98da6-146">Sequential view mode</span></span>

<span data-ttu-id="98da6-147">"순차 보기" 탭을 클릭하여 순차 보기 모드를 선택하며 이것이 기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-147">The sequential view mode is selected by clicking the “Sequential View” tab. This is the default mode.</span></span> <span data-ttu-id="98da6-148">이 모드에서는 이벤트 사이에 경과된 시간에 관계 없이 이벤트가 바로 다음에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-148">In this mode, events are shown immediately following each other–regardless of the elapsed time between them.</span></span> <span data-ttu-id="98da6-149">표시 영역 위에 있는 눈금자도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-149">Note also the ruler above the display area.</span></span> <span data-ttu-id="98da6-150">여기에는 추적 시작을 기준으로 상대 이벤트 번호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-150">It shows the relative event number from the beginning of the trace.</span></span> <span data-ttu-id="98da6-151">이 모드는 기본 모드이며, 시스템에서 진행되는 상황에 적절한 개요를 얻는 데 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-151">This mode is the default mode and is especially useful in getting a good overview of what is going on in the system.</span></span>

![순차 보기 모드](./media/user-guide/screen_shot_10.png)

<span data-ttu-id="98da6-153">**순차 보기 모드**</span><span class="sxs-lookup"><span data-stu-id="98da6-153">**Sequential view mode**</span></span>

### <a name="time-view-mode"></a><span data-ttu-id="98da6-154">시간 보기 모드</span><span class="sxs-lookup"><span data-stu-id="98da6-154">Time view mode</span></span>

<span data-ttu-id="98da6-155">이 모드에서는 이벤트가 상대 시간 방식으로 표시되며, 녹색 막대가 이벤트 간의 실행을 표시하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-155">In this mode, events are shown in a time relative manner–with a solid green bar being used to show execution between events.</span></span> <span data-ttu-id="98da6-156">이 모드는 시스템에서 대량 처리가 수행되는 위치를 확인하는 데 특히 유용하며, 개발자가 성능 및/또는 응답성을 높이기 위해 시스템을 조정하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-156">This mode is especially useful to see where the bulk of processing is taking place in the system, which can help developers tune their system for greater performance and/or responsiveness.</span></span>

<span data-ttu-id="98da6-157">이벤트 표시 위에 있는 눈금자도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-157">Note also the ruler above the event display.</span></span> <span data-ttu-id="98da6-158">이 눈금자는 Azure RTOS ThreadX 내부의 이벤트 추적 로깅에서 계측된 타임스탬프에서 파생된 추적 시작을 기준으로 상대 틱 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-158">This ruler shows relative ticks from the beginning of the trace, as derived from the time stamp instrumented in the event trace logging inside of Azure RTOS ThreadX.</span></span> <span data-ttu-id="98da6-159">타임스탬프가 너무 가까이 있으면(빈도가 낮은 타이머) 이벤트가 동시에 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-159">If the time-stamps are too close (low frequency timer), the events will run together.</span></span> <span data-ttu-id="98da6-160">반대로 타임스탬프가 너무 멀리 떨어져 있으면(빈도가 높은 타이머) 이벤트가 너무 멀리 떨어지게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-160">Conversely, if the time-stamps are too far apart (high frequency timer), then the events will be too far apart.</span></span> <span data-ttu-id="98da6-161">올바른 빈도 타임스탬프를 선택하는 것은 상대 시간 보기를 의미 있게 만드는 데 중요한 고려 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-161">Choosing the right frequency time stamp is an important consideration in making the time relative view meaningful.</span></span>

![시간 보기 모드](./media/user-guide/screen_shot_31.png)

### <a name="system-summary-line"></a><span data-ttu-id="98da6-163">시스템 요약 줄</span><span class="sxs-lookup"><span data-stu-id="98da6-163">System summary line</span></span>

<span data-ttu-id="98da6-164">Azure RTOS TraceX는 동일한 줄의 모든 이벤트가 포함된 단일 요약 줄도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-164">Azure RTOS TraceX also provides a single summary line that includes all events on the same line.</span></span> <span data-ttu-id="98da6-165">요약 줄에는 컨텍스트 요약이 포함되어 있고 그 아래에는 해당 이벤트 요약이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-165">The summary line contains a summary of the context as well as the corresponding event summary underneath.</span></span> <span data-ttu-id="98da6-166">이를 통해 복잡한 시스템의 개요를 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-166">This makes it easy to see an overview of a complex system.</span></span> <span data-ttu-id="98da6-167">요약 표시줄은 스레드가 많은 시스템에서 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-167">The summary bar is especially beneficial in systems that have a great number of threads.</span></span> <span data-ttu-id="98da6-168">이러한 요약 줄이 없는 경우 사용자는 실행 컨텍스트를 따라 세로 스크롤 막대를 사용하여 복잡한 시스템 상호 작용을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-168">Without such a summary line, the user would have to follow complex system interactions using the vertical scroll bar to follow the context of execution.</span></span>

<span data-ttu-id="98da6-169">Azure RTOS TraceX는 시스템 컨텍스트를 표시 왼쪽에 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-169">Azure RTOS TraceX lists the system contexts on the left-hand side of the display.</span></span>
<span data-ttu-id="98da6-170">특정 컨텍스트에서 발생하는 이벤트는 해당 컨텍스트의 오른쪽에 있는 가로줄에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-170">Events that occur in a particular context are displayed on the horizontal line to the right of that context.</span></span> <span data-ttu-id="98da6-171">이렇게 하면 이벤트가 발생한 컨텍스트를 쉽게 확인할 수 있을 뿐만 아니라 해당 컨텍스트 줄을 따라 특정 컨텍스트에서 발생한 모든 이벤트를 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-171">In this way, the user can easily ascertain which context the event occurred as well as follow that context line to see all the events that occurred in a particular context.</span></span>

![시스템 요약 줄](./media/user-guide/screen_shot_32.png)

<span data-ttu-id="98da6-173">**시스템 요약 줄**</span><span class="sxs-lookup"><span data-stu-id="98da6-173">**System Summary Line**</span></span>

<span data-ttu-id="98da6-174">처음 두 컨텍스트 항목은 항상 “인터럽트” 및 “초기화/유휴” 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-174">The first two context entries are always the “Interrupt” and “Initialize/Idle” contexts.</span></span> <span data-ttu-id="98da6-175">“인터럽트” 컨텍스트는 ISR(인터럽트 서비스 루틴)에서 생성된 모든 시스템 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-175">The “Interrupt” context represents all system events made from Interrupt Service Routines (ISRs).</span></span> <span data-ttu-id="98da6-176">“초기화/유휴” 컨텍스트는 Azure RTOS ThreadX의 두 가지 컨텍스트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-176">The “Initialize/Idle” context represents two contexts in Azure RTOS ThreadX.</span></span> <span data-ttu-id="98da6-177">tx_application_define을 수행하는 중에 발생하는 이벤트는 "초기화" 이벤트이며 "초기화/유휴" 컨텍스트에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-177">Events that occur during tx_application_define, are “Initialize” events and are displayed on the “Initialize/Idle” context.</span></span> <span data-ttu-id="98da6-178">시스템이 유휴 상태이고 이로 인해 이벤트가 발생하지 않는 경우 시간 보기에서 “실행 중”을 나타내는 녹색 막대가 “초기화/유휴” 컨텍스트에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-178">If the system is idle and thus no events are occurring, the green bar representing ”Running” in the time view is drawn on the ”Initialize/Idle” context.</span></span>

## <a name="methods-of-navigation"></a><span data-ttu-id="98da6-179">탐색 방법</span><span class="sxs-lookup"><span data-stu-id="98da6-179">Methods of navigation</span></span>

<span data-ttu-id="98da6-180">개발자는 Azure RTOS TraceX를 사용하여 "다음" 및 "이전" 탐색 단추가 작동하는 방식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-180">Azure RTOS TraceX enables the developer to specify how the "Next" and "Previous" navigation buttons operate.</span></span>

![탐색 단추](./media/user-guide/event.png)

<span data-ttu-id="98da6-182">“이벤트”를 선택하면 다음/이전 이벤트에 대한 탐색이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-182">If “Event” is selected, navigation is done on the next/previous event.</span></span> <span data-ttu-id="98da6-183">“컨텍스트”를 선택하면 동일한 컨텍스트의 다음/이전 이벤트에 대한 탐색이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-183">If “Context” is selected, navigation is done on the next/previous event on the same context.</span></span> <span data-ttu-id="98da6-184">“개체”를 선택하면 현재 개체의 다음/이전 이벤트(예: 특정 큐와 연결된 이벤트)에 대한 탐색이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-184">If “Object” is selected, navigation is done on the next/previous event of the current object, e.g., events associated with a specific queue.</span></span> <span data-ttu-id="98da6-185">“스위치”를 선택하면 다음/이전 컨텍스트 전환에 대한 탐색이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-185">If “Switches” is selected, navigation is done on the next/previous context switch.</span></span> <span data-ttu-id="98da6-186">“동일한 ID”를 선택하면 동일한 이벤트 ID의 다음/이전 이벤트에 대한 탐색이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-186">If “Same ID” is selected, navigation is done on the next/previous event for the same event ID.</span></span>

### <a name="event-information-display"></a><span data-ttu-id="98da6-187">이벤트 정보 표시</span><span class="sxs-lookup"><span data-stu-id="98da6-187">Event information display</span></span>

<span data-ttu-id="98da6-188">Azure RTOS TraceX는 300개 이벤트에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-188">Azure RTOS TraceX provides detailed information on some 300 events.</span></span> <span data-ttu-id="98da6-189">여기에는 6개의 내부 Azure RTOS ThreadX 이벤트, 2개의 ISR 이벤트(enter 및 exit), 14개의 내부 Azure RTOS FileX 이벤트, 42개의 내부 Azure RTOS NetX 이벤트, 1개의 사용자 정의 이벤트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-189">These include six internal Azure RTOS ThreadX events, two ISR events (enter and exit), 14 internal Azure RTOS FileX events, 42 internal Azure RTOS NetX events, and one user-defined event.</span></span> <span data-ttu-id="98da6-190">나머지 이벤트는 Azure RTOS ThreadX, Azure RTOS FileX 및 Azure RTOS NetX API 서비스에 직접 대응됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-190">The remaining events correspond directly to Azure RTOS ThreadX, Azure RTOS FileX, and Azure RTOS NetX API services.</span></span>
<span data-ttu-id="98da6-191">순차 또는 시간 표시 모드의 선택 여부에 관계 없이 마우스를 표시 영역의 이벤트 위에 놓으면 이벤트 근처에 자세한 이벤트 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-191">Regardless of whether sequential or time display mode is selected, a mouse-over on any event in the display area results in detailed event information displayed near the event.</span></span> <span data-ttu-id="98da6-192">여기서는 마우스를 데모 demo_threadx.trx 추적 파일의 이벤트 494 위에 놓았습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-192">The mouse-over of event 494 in the demonstration demo_threadx.trx trace file is shown here:</span></span>

![마우스를 위에 놓을 때 표시되는 추가 정보](./media/user-guide/screen_shot_37.png)

<span data-ttu-id="98da6-194">**마우스를 위에 놓을 때 표시되는 추가 정보**</span><span class="sxs-lookup"><span data-stu-id="98da6-194">**Mouse-Over Displays More Info**</span></span>

<span data-ttu-id="98da6-195">표시되는 각 이벤트에는 컨텍스트, 상대 시간 및 타임스탬프에 대한 표준 정보가 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-195">Each event displayed contains standard information about Context and both the Relative Time and Time Stamp.</span></span> <span data-ttu-id="98da6-196">컨텍스트 필드에는 이벤트가 발생한 컨텍스트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-196">The Context field shows what context the event took place in.</span></span> <span data-ttu-id="98da6-197">정확히 스레드, 유휴, ISR 및 초기화의 4가지 컨텍스트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-197">There are exactly four contexts: thread, idle, ISR, and initialization.</span></span> <span data-ttu-id="98da6-198">스레드 컨텍스트에서 이벤트가 발생하면 스레드의 이름과 우선 순위가 해당 시간에 수집되어 위와 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-198">When an event takes place in a thread context, the thread name and its priority at that time is gathered and displayed as shown above.</span></span> <span data-ttu-id="98da6-199">상대 시간에는 추적 시작 시점을 기준으로 상대 타이머 틱 수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-199">The Relative Time shows the relative number of timer ticks from the beginning of the trace.</span></span> <span data-ttu-id="98da6-200">원시 타임스탬프에는 이벤트의 원시 시간 원본이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-200">The Raw Time Stamp displays the raw time source of the event.</span></span> <span data-ttu-id="98da6-201">마지막으로 모든 이벤트 관련 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-201">Finally, all event-specific information is displayed.</span></span>

### <a name="zooming-in-and-out"></a><span data-ttu-id="98da6-202">확대 및 축소</span><span class="sxs-lookup"><span data-stu-id="98da6-202">Zooming in and out</span></span>

<span data-ttu-id="98da6-203">기본적으로 Azure RTOS TraceX는 1:1 픽셀 대 틱 매핑을 사용하여 보기 쉬운 크기로 이벤트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-203">By default, Azure RTOS TraceX displays the events in an easy-to-view size, with a 1:1 pixel:tick mapping.</span></span> <span data-ttu-id="98da6-204">사용자가 원하는 대로 확대하거나 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-204">The user may zoom in or zoom out as desired.</span></span> <span data-ttu-id="98da6-205">100%로 축소는 현재 표시 보기에서 전체 추적을 확인하는 데 유용합니다. 확대는 타임스탬프 원본의 해상도로 인해 이벤트가 겹치는 상태에서 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-205">Zooming out to 100% is useful to see the entire trace in the current display view, while zooming in is useful in conditions where the events overlap due to the resolution of the time stamp source.</span></span>

![100% 보기로 축소 또는 확대하여 세부 정보 보기](./media/user-guide/screen_shot_41.png)

<span data-ttu-id="98da6-207">**100% 보기로 축소 또는 확대하여 세부 정보 보기**</span><span class="sxs-lookup"><span data-stu-id="98da6-207">**Zoom Out to 100% View or Zoom In for Details**</span></span>

<span data-ttu-id="98da6-208">100%로 축소하여 현재 표시 페이지 내의 전체 추적을 표시하면 추적에서 캡처된 모든 컨텍스트 실행과 해당 컨텍스트 내에서 발생하는 일반 이벤트를 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-208">When zoomed out at 100% – showing the entire trace within the current display page – it is easy to see all the context execution captured in the trace as well as the general events occurring within those contexts.</span></span> <span data-ttu-id="98da6-209">“스레드 1” 및 “스레드 2”가 가장 자주 실행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-209">Notice that “thread 1“ and “thread 2“ execute most often.</span></span> <span data-ttu-id="98da6-210">또한 해당 이벤트에 대해 지정한 파란색은 이러한 스레드에서 큐 서비스 호출을 수행하고 있음을 나타냅니다(큐 이벤트는 파란색임).</span><span class="sxs-lookup"><span data-stu-id="98da6-210">The blue coloring for their events also suggests that these threads are making queue service calls (queue events are blue in color).</span></span>

<span data-ttu-id="98da6-211">전체 아이콘 보기로 복원하는 것도 마찬가지로 쉽습니다. 확대 단추를 반복적으로 선택하거나 일부 비율을 100으로 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-211">Restoring to a full icon view is equally easy; Either the zoom-in button may be selected repeatedly or some factor of 100 may be entered.</span></span>

### <a name="delta-ticks-between-events"></a><span data-ttu-id="98da6-212">이벤트 간 델타 틱 수</span><span class="sxs-lookup"><span data-stu-id="98da6-212">Delta ticks between events</span></span>

<span data-ttu-id="98da6-213">다양한 이벤트 간의 틱 수는 Azure RTOS TraceX에서 쉽게 확인할 수 있습니다. 시작 이벤트를 클릭하고 마우스를 끝 이벤트로 끌면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-213">Determining the number of ticks between various events in Azure RTOS TraceX is easy–simply click on the starting event and drag the mouse to the ending event.</span></span>
<span data-ttu-id="98da6-214">이벤트 간의 델타 틱 수는 표시의 오른쪽 위 모서리에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-214">The delta number of ticks between the events will show up in the upper right-hand corner of the display.</span></span>

![델타 틱](./media/user-guide/screen_shot_42.png)

<span data-ttu-id="98da6-216">**델타 틱**</span><span class="sxs-lookup"><span data-stu-id="98da6-216">**Delta Ticks**</span></span>

<span data-ttu-id="98da6-217">델타 틱 수는 이벤트 494와 이벤트 496 사이에서 5,032개 틱이 경과했음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-217">The delta ticks show that 5032 ticks have elapsed between event 494 and event 496.</span></span> <span data-ttu-id="98da6-218">이는 각 이벤트의 상대 타임스탬프를 확인하고 뺄셈을 수행하여 수동으로 계산할 수도 있지만 GUI를 사용하는 것이 쉽고 즉각적입니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-218">This could also be calculated manually by looking at the relative time stamps in each event and subtracting, but using the GUI is easy and instantaneous.</span></span>

### <a name="priority-inversions"></a><span data-ttu-id="98da6-219">우선 순위 반전</span><span class="sxs-lookup"><span data-stu-id="98da6-219">Priority inversions</span></span>

<span data-ttu-id="98da6-220">Azure RTOS TraceX는 추적 파일에서 검색된 우선 순위 반전을 자동으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-220">Azure RTOS TraceX automatically displays priority inversions detected in the trace file.</span></span> <span data-ttu-id="98da6-221">우선 순위 반전은 우선 순위가 낮은 스레드에서 현재 소유하고 있는 뮤텍스를 얻으려고 시도하는 우선 순위가 높은 스레드가 차단되는 조건으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-221">Priority inversions are defined as conditions where a higher-priority thread is blocked trying to obtain a mutex that is currently owned by a lower-priority thread.</span></span> <span data-ttu-id="98da6-222">시스템이 이 방식으로 작동하도록 설정되었으므로 이 조건을 “결정적”이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-222">This condition is termed “deterministic,” since the system was setup to operate in this manner.</span></span> <span data-ttu-id="98da6-223">사용자에게 알리기 위해 Azure RTOS TraceX는 “결정적” 우선 순위 반전 범위를 연한 연어 색으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-223">In order to inform the user, Azure RTOS TraceX shows “deterministic” priority inversion ranges as a light salmon color.</span></span>

<span data-ttu-id="98da6-224">Azure RTOS TraceX는 “비결정적” 우선 순위 반전도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-224">Azure RTOS TraceX also displays “un-deterministic” priority inversions.</span></span> <span data-ttu-id="98da6-225">이러한 우선 순위 반전은 다른 우선 순위 수준의 다른 스레드가 “결정적” 우선 순위 반전의 중간에 실행되었다는 점에서 “결정적” 우선 순위 반전과 다릅니다. 따라서 우선 순위 반전 내의 시간은 다소 “비결정적”입니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-225">These priority inversions differ from the “deterministic” priority inversions in that another thread of a different priority level has executed in the middle of what was a “deterministic” priority inversion, thereby making the time within the priority inversion somewhat “un-deterministic.”</span></span> <span data-ttu-id="98da6-226">이 조건은 사용자가 알 수 없는 경우가 많으며 매우 심각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-226">This condition is often unknown to the user and can be very serious.</span></span> <span data-ttu-id="98da6-227">사용자에게 이 조건을 경고하기 위해 Azure RTOS TraceX는 “비결정적” 우선 순위 반전을 더 밝은 연어 색으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-227">In order to alert the user of this condition, Azure RTOS TraceX shows “un-deterministic” priority inversions as a brighter salmon color.</span></span>

![결정적 및 비결정적 우선 순위 반전](./media/user-guide/screen_shot_43.png)

<span data-ttu-id="98da6-229">**결정적 및 비결정적 우선 순위 반전**</span><span class="sxs-lookup"><span data-stu-id="98da6-229">**Deterministic and Non-Deterministic Priority Inversion**</span></span>

### <a name="execution-profile"></a><span data-ttu-id="98da6-230">실행 프로필</span><span class="sxs-lookup"><span data-stu-id="98da6-230">Execution profile</span></span>

<span data-ttu-id="98da6-231">Azure RTOS TraceX는 현재 로드된 추적 파일 내의 모든 실행 컨텍스트에 대한 기본 제공 실행 프로필 보고서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-231">Azure RTOS TraceX provides a built-in execution profile report for all execution contexts within in the currently loaded trace file.</span></span>

![실행 프로필](./media/user-guide/execution_profile.png)

### <a name="performance-statistics"></a><span data-ttu-id="98da6-233">Performance statistics</span><span class="sxs-lookup"><span data-stu-id="98da6-233">Performance statistics</span></span>

<span data-ttu-id="98da6-234">Azure RTOS TraceX는 현재 로드된 추적 파일에 대한 기본 제공 성능 통계 보고서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-234">Azure RTOS TraceX provides a built-in performance statistics report for the currently loaded trace file.</span></span>

![Performance statistics](./media/user-guide/performance_statistics.png)

### <a name="thread-stack-usage"></a><span data-ttu-id="98da6-236">스레드 스택 사용</span><span class="sxs-lookup"><span data-stu-id="98da6-236">Thread stack usage</span></span>

<span data-ttu-id="98da6-237">Azure RTOS TraceX는 현재 로드된 추적 파일 내에서 실행 중인 모든 스레드에 대한 기본 제공 스택 사용 보고서를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-237">Azure RTOS TraceX provides a built-in stack usage report for all threads executing within in the currently loaded trace file.</span></span>

![스택 사용](./media/user-guide/thread_stack_usage.png)

<span data-ttu-id="98da6-239">Azure RTOS TraceX는 현재 로드된 추적 파일의 Azure RTOS FileX 성능 통계를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-239">Azure RTOS TraceX presents the Azure RTOS FileX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="98da6-240">이 정보는 모든 열린 미디어 개체에서 전체 시스템에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-240">This information is displayed for the entire system–on all opened media objects.</span></span>

![FileX 통계](./media/user-guide/filex_statistics.png)

### <a name="azure-rtos-netx-statistics"></a><span data-ttu-id="98da6-242">Azure RTOS NetX 통계</span><span class="sxs-lookup"><span data-stu-id="98da6-242">Azure RTOS NetX statistics</span></span>

<span data-ttu-id="98da6-243">또한 Azure RTOS TraceX는 현재 로드된 추적 파일의 NetX 성능 통계도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-243">Azure RTOS TraceX also presents the NetX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="98da6-244">이 정보는 전체 시스템에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-244">This information is displayed for the entire system.</span></span>

![NetX 통계](./media/user-guide/netx_statistics.png)

### <a name="raw-trace-dump"></a><span data-ttu-id="98da6-246">원시 추적 덤프</span><span class="sxs-lookup"><span data-stu-id="98da6-246">Raw trace dump</span></span>

<span data-ttu-id="98da6-247">Azure RTOS TraceX는 원시 추적 파일을 텍스트 형식으로 작성하고 메모장을 시작하여 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-247">Azure RTOS TraceX can build a raw trace file in text format and launch notepad to display it.</span></span>

![원시 추적 덤프](./media/user-guide/raw_trace_dump.png)

<span data-ttu-id="98da6-249">나열된 모든 타이밍 및 크기 수치는 예상치이며, 개발 플랫폼에 따라 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98da6-249">Please note that all timing and size figures listed are estimates and may be different on your development platform</span></span>
