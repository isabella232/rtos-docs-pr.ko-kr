---
title: 4장 - Azure RTOS TraceX 성능 분석
description: 이 장에서는 Azure RTOS TraceX 성능 분석 도구에 대해 설명합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 6cf1b5bd5349efd97c3afc8a9e7f57f477f06f8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812354"
---
# <a name="chapter-4---azure-rtos-tracex-performance-analysis"></a><span data-ttu-id="1c799-103">4장 - Azure RTOS TraceX 성능 분석</span><span class="sxs-lookup"><span data-stu-id="1c799-103">Chapter 4 - Azure RTOS TraceX performance analysis</span></span>

<span data-ttu-id="1c799-104">이 장에서는 Azure RTOS TraceX 성능 분석 도구에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-104">This chapter describes the Azure RTOS TraceX performance analysis tool:</span></span>

## <a name="performance-analysis"></a><span data-ttu-id="1c799-105">성능 분석</span><span class="sxs-lookup"><span data-stu-id="1c799-105">Performance Analysis</span></span>

<span data-ttu-id="1c799-106">TraceX는 추적 파일에 대한 기본 제공 성능 분석을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-106">TraceX provides built-in performance analysis of trace files.</span></span> <span data-ttu-id="1c799-107">*실행 프로필*, *인기 있는 서비스*, *스레드 스택 사용* 및 FileX 및 NetX 통계 *,* 를 비롯한 다양한 *성능 통계* 와 같은 정보를 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-107">Information such as the *execution profile*, *popular services*, *thread stack usage*, and various *performance statistics,* including FileX and NetX statistics *,* are readily available.</span></span> <span data-ttu-id="1c799-108">이 정보는 ***보기*** 메뉴 항목을 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-108">This information is available via the ***View*** menu item.</span></span> 


## <a name="execution-profile"></a><span data-ttu-id="1c799-109">실행 프로필</span><span class="sxs-lookup"><span data-stu-id="1c799-109">Execution Profile</span></span>

<span data-ttu-id="1c799-110">***실행 프로필 생성** _ 단추나 _*_보기 - 실행 프로필_\*_ 을 선택하면 현재 로드된 추적 파일의 TraceX 실행 프로필이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-110">Selecting the ***Generate Execution Profile** _ button or _*_View -Execution Profile_\*_ presents the TraceX execution profile for the currently loaded trace file.</span></span> <span data-ttu-id="1c799-111">샘플 ThreadX 데모 추적과 연결된 실행 프로필이 _\*그림 19\*\*에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-111">The execution profile associated with the sample ThreadX demonstration trace is shown in _\*Figure 19\*\*.</span></span>

![샘플 ThreadX 데모 추적과 연결된 실행 프로필의 스크린샷](./media/user-guide/execution_profile.png)

<span data-ttu-id="1c799-113">**그림 19**</span><span class="sxs-lookup"><span data-stu-id="1c799-113">**FIGURE 19**</span></span>

<span data-ttu-id="1c799-114">**그림 19** 에 나와 있는 예제에서는 처리 시간 중 거의 45%가 **_스레드 2_*에, 처리 시간 중 거의 51%가\* _스레드 1_*\* 에 해당합니다. 추적의 대부분이 메시지를 보내고 받는 스레드를 표시하므로 이는 논리적입니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-114">The example shown in **Figure 19** indicates that nearly 45% of the processing time is inside of **_thread 2_*_ and nearly 51% of the processing time is inside of _*_thread 1_** This is logical since the bulk of the trace shows these threads sending and receiving messages.</span></span> <span data-ttu-id="1c799-115">이 예제에서 나머지 실행 컨텍스트의 실행 시간은 적습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-115">The remaining execution contexts have only a small amount of execution time in this example.</span></span>

## <a name="popular-services"></a><span data-ttu-id="1c799-116">인기 있는 서비스</span><span class="sxs-lookup"><span data-stu-id="1c799-116">Popular Services</span></span>

<span data-ttu-id="1c799-117">\***보기 -> 인기 있는 서비스** _를 선택하면 현재 로드된 추적 파일에 인기 있는 서비스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-117">Selecting \***View ->Popular Services** _ presents the popular services in the currently loaded trace file.</span></span> <span data-ttu-id="1c799-118">기본적으로 이 정보는 전체 시스템에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-118">By default, this information is displayed for the entire system.</span></span> <span data-ttu-id="1c799-119">그러나 특정 스레드에 대한 인기 있는 서비스도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-119">However, the popular services for specific threads are also available.</span></span> <span data-ttu-id="1c799-120">샘플 ThreadX 데모 추적의 인기 있는 서비스는 _\*그림 20\*\*에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-120">The popular services in the sample ThreadX demonstration trace are shown in _\*Figure 20\*\*.</span></span>

![샘플 ThreadX 데모 추적의 인기 있는 서비스 스크린샷](./media/user-guide/popular_services.png)

<span data-ttu-id="1c799-122">**그림 20**</span><span class="sxs-lookup"><span data-stu-id="1c799-122">**FIGURE 20**</span></span>

<span data-ttu-id="1c799-123">**그림 20** 에 나온 예제를 보면 **_tx_queue_send_ *_ 및 _* _tx_queue_receive_** 가 이 추적에서 가장 인기 있는 두 가지 서비스임을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-123">The example shown in **Figure 20** indicates that **_tx_queue_send_*_ and _*_tx_queue_receive_** are the two most popular services in this trace.</span></span> <span data-ttu-id="1c799-124">이는 이 추적이 캡처된 표준 ThreadX 데모의 동작과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-124">This is consistent with the behavior of the standard ThreadX demonstration from which this trace was captured.</span></span>

<span data-ttu-id="1c799-125">이 창의 맨 위에 있는 드롭다운 선택 목록을 사용하여 이 분석에 대해 특정 스레드를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-125">Specific threads can be selected for this analysis by using the drop down selection list at the top of this window.</span></span> <span data-ttu-id="1c799-126">**그림 21** 은 **_스레드 3_** 에 대한 분석을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-126">**Figure 21** shows this analysis for **_thread 3_**.</span></span>

![TraceX 인기 있는 서비스에 대한 분석 스크린샷](./media/user-guide/popular_services_thread3.png)

<span data-ttu-id="1c799-128">**그림 21**</span><span class="sxs-lookup"><span data-stu-id="1c799-128">**FIGURE 21**</span></span>

## <a name="thread-stack-usage-analysis-for-thread-3"></a><span data-ttu-id="1c799-129">스레드 스택 사용량</span><span class="sxs-lookup"><span data-stu-id="1c799-129">Thread Stack Usage</span></span> ![스레드 3에 대한 분석입니다.](./media/user-guide/screen_shot_17.png)

<span data-ttu-id="1c799-131">***스레드 스택 사용량 생성** _ 단추 또는 _*_보기 -> 스레드 스택 사용량_\*_ 을 선택하면 추적 파일의 각 스레드에 대한 스택 사용량이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-131">Selecting the ***Generate Thread Stack Usage** _ button or _*_View -> Thread Stack Usage_\*_ presents the stack usage for each thread in the trace file.</span></span> <span data-ttu-id="1c799-132">이는 파일의 많은 추적 항목에서 현재 스레드 스택 포인터를 포함하는 ThreadX에 의해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-132">This is accomplished by ThreadX including the current thread stack pointer in many of the trace entries in the file.</span></span> <span data-ttu-id="1c799-133">스택 사용량이 100%면 스택이 오버플로되었으며 애플리케이션에서 수정해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-133">A stack usage of 100% indicates the stack has overflowed and must be corrected in the application.</span></span> <span data-ttu-id="1c799-134">이 추적 파일 내에 스레드 실행이 없으면 해당 스레드에 대한 스택 사용량이 0%로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-134">If there is no thread execution within this trace file, the stack usage for that thread is shown at 0%.</span></span> <span data-ttu-id="1c799-135">샘플 ThreadX 데모 추적의 스레드 스택 사용량은 _\*그림 22\*\*에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-135">The thread stack usage in the sample ThreadX demonstration trace is shown in _\*Figure 22\*\*.</span></span>

![TraceX 스레드 스택 사용량의 스크린샷](./media/user-guide/thread_stack_usage.png)

<span data-ttu-id="1c799-137">**그림 22**</span><span class="sxs-lookup"><span data-stu-id="1c799-137">**FIGURE 22**</span></span>

<span data-ttu-id="1c799-138">**그림 22** 에 표시된 예제는 이 추적에 포함된 대부분의 스레드가 스택 사용량이 9%에서 12%임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-138">The example shown in **Figure 22** indicates that most threads in this trace have between 9% and 12% stack usage.</span></span>

## <a name="performance-statistics"></a><span data-ttu-id="1c799-139">성능 통계</span><span class="sxs-lookup"><span data-stu-id="1c799-139">Performance Statistics</span></span>

<span data-ttu-id="1c799-140">\***성능 통계 생성** _ 단추 또는 _ \*_보기 -> 성능 통계_\*\*를 선택하면 현재 로드된 추적 파일의 성능 통계가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-140">Selecting the ***Generate Performance Statistics** _ button or _ *_View -> Performance Statistics_** presents the performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="1c799-141">기본적으로 이 정보는 전체 시스템에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-141">By default, this information is displayed for the entire system.</span></span> <span data-ttu-id="1c799-142">그러나 성능 통계를 각각의 특정 스레드에 대해 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-142">However, the performance statistics are also available for each specific thread.</span></span>

<span data-ttu-id="1c799-143">샘플 ThreadX 데모 추적의 성능 통계가 **그림 23** 에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-143">The performance statistics of the sample ThreadX demonstration trace are shown in **Figure 23**.</span></span>

![TraceX 성능 통계의 스크린샷](./media/user-guide/performance_statistics.png)

<span data-ttu-id="1c799-145">**그림 23**</span><span class="sxs-lookup"><span data-stu-id="1c799-145">**FIGURE 23**</span></span>

<span data-ttu-id="1c799-146">**그림 23** 에 표시된 예제를 보면 이 추적 파일에 18개의 컨텍스트 전환, 5개의 스레드 선점(preemption), 16개의 스레드 일시 중단, 19개의 스레드 재개 및 3개의 인터럽트가 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-146">The example shown in **Figure 23** indicates that there were 18 context switches in this trace file, as well as five thread preemptions, 16 thread suspensions, 19 thread resumptions, and three interrupts.</span></span> <span data-ttu-id="1c799-147">이 추적 파일에는 우선 순위 반전이 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-147">There were no priority inversions found in this trace file.</span></span> <span data-ttu-id="1c799-148">우선 순위에는 *결정적* 및 *비결정적* 이라는 두 가지 범주가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-148">Notice there are two categories of priority inversions, namely, *deterministic* and *nondeterministic*.</span></span> <span data-ttu-id="1c799-149">결정적 우선 순위 반전은 우선 순위가 낮은 스레드가 소유하는 뮤텍스에서 스레드가 차단되는 우선 순위 반전입니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-149">Deterministic priority inversions are priority inversion in which a thread is blocked on a mutex owned by a lower priority thread.</span></span> <span data-ttu-id="1c799-150">비결정적 우선 순위 반전은 결정적 우선 순위 반전 중에 다른 우선 순위가 낮은 스레드를 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-150">An nondeterministic priority inversion is where a different lower priority thread runs during a deterministic priority inversion.</span></span> <span data-ttu-id="1c799-151">나중에 애플리케이션에서 예기치 않은 타이밍 동작을 발생시킬 수 있으므로 신중하게 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-151">The later can cause unforeseen timing behavior in the application and should be studied carefully.</span></span>

## <a name="filex-statistics"></a><span data-ttu-id="1c799-152">FileX 통계</span><span class="sxs-lookup"><span data-stu-id="1c799-152">FileX Statistics</span></span>

<span data-ttu-id="1c799-153">\***보기 -> FileX 통계** _를 선택하면 현재 로드된 추적 파일의 FileX 성능 통계가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-153">Selecting \***View -> FileX Statistics** _ presents the FileX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="1c799-154">이 정보는 모두 열린 미디어 개체에서 전체 시스템에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-154">This information is displayed for the entire system, on all opened ../media objects.</span></span> <span data-ttu-id="1c799-155">샘플 FileX 데모 추적의 성능 통계가 _\*그림 24\*\*에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-155">The performance statistics of the sample FileX demonstration trace are shown in _\*Figure 24\*\*.</span></span>

![FileX 통계의 스크린샷](./media/user-guide/filex_statistics.png)

<span data-ttu-id="1c799-157">**그림 24**</span><span class="sxs-lookup"><span data-stu-id="1c799-157">**FIGURE 24**</span></span>

<span data-ttu-id="1c799-158">**그림 27** 에 표시된 예제를 보면 19건의 미디어 열기, 19건의 미디어 닫기, 19건의 미디어 플러시, 18건의 디렉터리 읽기, 19건의 디렉터리 쓰기 및 18건의 디렉터리 캐시 누락이 있었음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-158">The example shown in **Figure 27** indicates there were 19 ../media opens, 19 ../media closes, 19 ../media flushes, 18 directory reads, 19 directory writes, and 18 directory cache misses.</span></span> <span data-ttu-id="1c799-159">통계 창에서 아래로 스크롤하면 추가 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-159">Additonal information can be viewed by scrolling down in the statistics window.</span></span>

## <a name="netx-statistics"></a><span data-ttu-id="1c799-160">NetX 통계</span><span class="sxs-lookup"><span data-stu-id="1c799-160">NetX Statistics</span></span>

<span data-ttu-id="1c799-161">\***보기 -> NetX 통계** _를 선택하면 현재 로드된 추적 파일의 NetX 성능 통계가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-161">Selecting \***View -NetX Statistics** _ presents the NetX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="1c799-162">이 정보는 전체 시스템에 대해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-162">This information is displayed for the entire system.</span></span> <span data-ttu-id="1c799-163">샘플 NetX 데모 추적의 성능 통계가 _\*그림 25\*\*에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-163">The performance statistics of the sample NetX demonstration trace are shown in _\*Figure 25\*\*.</span></span>

![NetX 통계의 스크린샷](./media/user-guide/netx_statistics.png)

<span data-ttu-id="1c799-165">**그림 25**</span><span class="sxs-lookup"><span data-stu-id="1c799-165">**FIGURE 25**</span></span>

<span data-ttu-id="1c799-166">**그림 25** 에 표시된 예제를 보면 ARP, Ping 또는 UDP 이벤트는 없으나, 30개의 IP 패킷이 전송되고, 1,368개의 IP 바이트가 전송되었으며, 30개의 IP 패킷이 수신되고, 1,360개의 IP 바이트가 수신되었음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-166">The example shown in **Figure 25** indicates there were no ARP, Ping, or UDP events, but there were 30 IP packets sent, 1,368 IP bytes sent, 30 IP packets received, and 1,360 IP bytes received.</span></span>

## <a name="trace-file-information"></a><span data-ttu-id="1c799-167">추적 파일 정보</span><span class="sxs-lookup"><span data-stu-id="1c799-167">Trace File Information</span></span>

<span data-ttu-id="1c799-168">\***보기 -> 추적 파일 정보** _를 선택하면 열려 있는 추적 파일에 대한 몇 가지 기본 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-168">Selecting \***View -> Trace File Information** _ presents some basic information about the opened trace file.</span></span> <span data-ttu-id="1c799-169">이 정보에는 파일의 바이트 순서, 시간 원본의 크기, 각 개체 이름에 대한 최대 바이트 수 및 모든 추적 파일 포인터의 기본 주소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-169">This information includes the byte order of the file, size of the time source, maximum number of bytes for each object name, and the base address of all trace file pointers.</span></span> <span data-ttu-id="1c799-170">_ \*그림 26\*\*은 표준 **_demo_threadx.trx_** 추적 파일에 대한 추적 파일 정보를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-170">_ *Figure 26*\* shows the trace file information for the standard **_demo_threadx.trx_** trace file.</span></span>

![TraceX 파일 정보의 스크린샷](./media/user-guide/trace_file_info.png)

<span data-ttu-id="1c799-172">**그림 26**</span><span class="sxs-lookup"><span data-stu-id="1c799-172">**FIGURE 26**</span></span>

## <a name="raw-trace-dump"></a><span data-ttu-id="1c799-173">원시 추적 덤프</span><span class="sxs-lookup"><span data-stu-id="1c799-173">Raw Trace Dump</span></span>

<span data-ttu-id="1c799-174">\***보기 -> 원시 추적 덤프** _를 선택하면 원시 추적 덤프를 포함하는 파일의 이름을 지정하는 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-174">Selecting \***View -> Raw Trace Dump** _ presents a dialog to name the file containing the raw trace dump.</span></span> <span data-ttu-id="1c799-175">파일 이름 및 경로를 입력한 후 TraceX는 원시 추적 파일을 텍스트 형식으로 빌드하고 _*_notepad.exe_*_ 를 시작하여 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-175">After the file name and path are entered, TraceX builds the raw trace file in text format and launches _*_notepad.exe_*_ to display it.</span></span> <span data-ttu-id="1c799-176">_ \*그림 27\*\*은 표준 **_demo_threadx.trx_** 추적 파일에 대한 원시 추적 파일 덤프를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1c799-176">_ *Figure 27*\* shows the raw trace file dump for the standard **_demo_threadx.trx_** trace file.</span></span>

![원시 추적 덤프의 스크린샷](./media/user-guide/raw_trace_dump.png)

<span data-ttu-id="1c799-178">**그림 27**</span><span class="sxs-lookup"><span data-stu-id="1c799-178">**FIGURE 27**</span></span>
