---
title: 챕터 5 - 추적 버퍼 생성
description: 이 챕터는 Azure RTOS TraceX 이벤트 버퍼를 빌드하는 방법에 대한 설명을 포함하며 버퍼의 기본 형식에 대해서도 설명합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: f296137d23b9f3c1c4fd115947bb50a32b768123
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812337"
---
# <a name="chapter-5---generating-trace-buffers"></a><span data-ttu-id="2373c-103">챕터 5 - 추적 버퍼 생성</span><span class="sxs-lookup"><span data-stu-id="2373c-103">Chapter 5 - Generating trace buffers</span></span>

<span data-ttu-id="2373c-104">이 챕터는 Azure RTOS TraceX 이벤트 버퍼를 빌드하는 방법에 대한 설명을 포함하며 버퍼의 기본 형식에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-104">This chapter contains a description about how to build a Azure RTOS TraceX event buffer and also describes the underlying format of the buffer.</span></span>

## <a name="threadx-event-trace-support"></a><span data-ttu-id="2373c-105">ThreadX 이벤트 추적 지원</span><span class="sxs-lookup"><span data-stu-id="2373c-105">ThreadX Event Trace Support</span></span>

<span data-ttu-id="2373c-106">ThreadX는 모든 ThreadX 서비스, 스레드 상태 변경 및 사용자 정의 이벤트에 대한 기본 제공 이벤트 추적 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-106">ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="2373c-107">ThreadX 이벤트 추적 기능은 주로 애플리케이션의 마지막 'n' 작업을 분석하는 사후 분석 도구로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-107">The ThreadX event-trace capability is primarily designed as a post-mortem tool to analyze the last "n" activities in the application.</span></span> <span data-ttu-id="2373c-108">개발자는 이 정보를 통해 문제 및/또는 잠재적 최적화 대상을 발견할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-108">From this information, the developer may spot problems and/or potential targets of optimization.</span></span>

<span data-ttu-id="2373c-109">TraceX는 ThreadX로 빌드된 이벤트 추적 버퍼를 그래픽으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-109">TraceX graphically displays the event trace buffer built by ThreadX.</span></span> <span data-ttu-id="2373c-110">다음은 버퍼를 빌드하는 방법과 버퍼의 기본 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-110">The following describes how to build the buffer and describes the underlying format of the buffer.</span></span>

## <a name="enabling-event-trace"></a><span data-ttu-id="2373c-111">이벤트 추적 사용</span><span class="sxs-lookup"><span data-stu-id="2373c-111">Enabling Event Trace</span></span>

<span data-ttu-id="2373c-112">이벤트 추적을 사용하도록 설정하려면 타임스탬프 상수를 정의하고, **TX_ENABLE_EVENT_TRACE** 가 정의된 ThreadX 라이브러리를 빌드하고, **tx_trace_enable** 함수를 호출하여 추적을 사용하도록 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="2373c-112">To enable event trace, define the time-stamp constants, build the ThreadX library with **TX_ENABLE_EVENT_TRACE** defined, and enable tracing by calling the **tx_trace_enable** function.</span></span>

## <a name="defining-time-stamp-constants"></a><span data-ttu-id="2373c-113">타임스탬프 상수 정의</span><span class="sxs-lookup"><span data-stu-id="2373c-113">Defining Time-Stamp Constants</span></span>

<span data-ttu-id="2373c-114">타임스탬프 상수는 이벤트 추적 항목에 사용된 타임스탬프에 대한 개발자 제어를 제공하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-114">The time-stamp constants are designed to provide the developer control over the time-stamp used in the event trace entries.</span></span> <span data-ttu-id="2373c-115">2개의 타임스탬프 상수 및 해당 기본값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-115">The two time-stamp constants and their default values are as follows:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

<span data-ttu-id="2373c-116">위의 상수는 **tx_port.h** 에서 정의되어 있으며, 각 이벤트에서 1씩 증가하는 '가짜' 타임스탬프를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-116">The above constants are defined in **tx_port.h** and create a "fake" time-stamp that simply increments by one on each event.</span></span> <span data-ttu-id="2373c-117">다음은 실제 타임스탬프 정의의 예시입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-117">The following is an example of an actual timestamp definition:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

<span data-ttu-id="2373c-118">위의 상수는 0x13000004 주소를 읽어서 얻은 32비트 타이머를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-118">The above constants specify a 32-bit timer that is obtained by reading the address 0x13000004.</span></span> <span data-ttu-id="2373c-119">대부분의 애플리케이션 관련 타임스탬프는 비슷한 방식으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-119">Most application specific time-stamps should be setup in a similar fashion.</span></span>

## <a name="exporting-the-trace-buffer"></a><span data-ttu-id="2373c-120">추적 버퍼 내보내기</span><span class="sxs-lookup"><span data-stu-id="2373c-120">Exporting the Trace Buffer</span></span>

<span data-ttu-id="2373c-121">호스트의 TraceX에는 이진, Intel HEX 또는 Motorola S-레코드 파일 형식의 추적 버퍼가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-121">TraceX needs the trace buffer in a binary, Intel HEX, or Motorola S-Record file format on the host.</span></span> <span data-ttu-id="2373c-122">이를 수행하는 가장 쉬운 방법은 대상을 중지하고 디버거에 지시하여 사용자가 ***tx_trace_enable*** 함수에 제공한 메모리 영역을 호스트의 파일로 덤프하도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-122">The easiest way to accomplish this is to stop the target and instruct your debugger to dump the memory area you supplied to ***tx_trace_enable*** function into a file on the host.</span></span>

> [!WARNING]
><span data-ttu-id="2373c-123">***추적 수집 코드 내에서 대상을 중지하지 않도록 주의하십시오. 대상을 중지하면 잘못된 추적 정보가 발생할 수 있습니다. ThreadX 내에서 프로그램이 중지되는 경우 추적 버퍼를 덤프하기 전에 추적 삽입 매크로를 한 단계씩 실행하는 것이 가장 좋습니다.***</span><span class="sxs-lookup"><span data-stu-id="2373c-123">***Be careful not to stop the target within a trace gathering code itself. Doing so can cause invalid trace information. If the program is halted within ThreadX, it is best to step over any trace insert macro before dumping the trace buffer.***</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2373c-124">*부록 D는 다양한 개발 도구 내에서 추적 버퍼를 덤프하는 방법을 보여줍니다.*</span><span class="sxs-lookup"><span data-stu-id="2373c-124">*Appendix D shows how to dump the trace buffer from within a variety of development tools.*</span></span>

## <a name="extended-event-trace-api"></a><span data-ttu-id="2373c-125">확장 이벤트 추적 API</span><span class="sxs-lookup"><span data-stu-id="2373c-125">Extended Event Trace API</span></span>

<span data-ttu-id="2373c-126">**TX_ENABLE_EVENT_TRACE** 가 정의된 ThreadX를 빌드하면 애플리케이션에서 사용할 수 있는 새 이벤트 추적 API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-126">When ThreadX is built with **TX_ENABLE_EVENT_TRACE** defined, the following new event trace APIs are available to the application:</span></span>

- <span data-ttu-id="2373c-127">tx_trace_enable: *이벤트 추적 사용*</span><span class="sxs-lookup"><span data-stu-id="2373c-127">tx_trace_enable: *Enable event tracing*</span></span>
- <span data-ttu-id="2373c-128">tx_trace_event_filter: *지정된 이벤트 필터링*</span><span class="sxs-lookup"><span data-stu-id="2373c-128">tx_trace_event_filter: *Filter specified event(s)*</span></span>
- <span data-ttu-id="2373c-129">tx_trace_event_unfilter: *지정된 이벤트 필터링 안 함*</span><span class="sxs-lookup"><span data-stu-id="2373c-129">tx_trace_event_unfilter: *Unfilter specified event(s)*</span></span>
- <span data-ttu-id="2373c-130">tx_trace_disable: *이벤트 추적 사용 안 함*</span><span class="sxs-lookup"><span data-stu-id="2373c-130">tx_trace_disable: *Disable event tracing*</span></span>
- <span data-ttu-id="2373c-131">tx_trace_isr_enter_insert: *ISR 입력 추적 이벤트 삽입*</span><span class="sxs-lookup"><span data-stu-id="2373c-131">tx_trace_isr_enter_insert: *Insert ISR enter trace event*</span></span>
- <span data-ttu-id="2373c-132">tx_trace_isr_exit_insert: *ISR 종료 추적 이벤트 삽입*</span><span class="sxs-lookup"><span data-stu-id="2373c-132">tx_trace_isr_exit_insert: *Insert ISR exit trace event*</span></span>
- <span data-ttu-id="2373c-133">tx_trace_buffer_full_notify: *추적 버퍼 전체 애플리케이션 콜백 등록*</span><span class="sxs-lookup"><span data-stu-id="2373c-133">tx_trace_buffer_full_notify: *Register trace buffer full application callback*</span></span>
- <span data-ttu-id="2373c-134">tx_trace_user_event_insert: *사용자 이벤트 삽입*</span><span class="sxs-lookup"><span data-stu-id="2373c-134">tx_trace_user_event_insert: *Insert user event*</span></span>

### <a name="tx_trace_enable"></a><span data-ttu-id="2373c-135">tx_trace_enable</span><span class="sxs-lookup"><span data-stu-id="2373c-135">tx_trace_enable</span></span>

<span data-ttu-id="2373c-136">이벤트 추적 사용</span><span class="sxs-lookup"><span data-stu-id="2373c-136">Enable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="2373c-137">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2373c-137">Prototype</span></span>

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a><span data-ttu-id="2373c-138">Description</span><span class="sxs-lookup"><span data-stu-id="2373c-138">Description</span></span>
<span data-ttu-id="2373c-139">이 서비스는 ThreadX 내의 이벤트 추적을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-139">This service enables event tracing inside ThreadX.</span></span> <span data-ttu-id="2373c-140">애플리케이션에서 추적 버퍼와 ThreadX 개체의 최대 수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-140">The trace buffer and the maximum number of ThreadX objects are supplied by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2373c-141">ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-141">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="2373c-142">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2373c-142">Input Parameters</span></span>

- <span data-ttu-id="2373c-143">**trace_buffer_start**: 사용자가 제공한 추적 버퍼의 시작에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-143">**trace_buffer_start**: Pointer to the start of the user-supplied trace buffer.</span></span>
- <span data-ttu-id="2373c-144">**trace_buffer_size**: 추적 버퍼에 대한 메모리의 총 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-144">**trace_buffer_size**: Total number of bytes in the memory for the trace buffer.</span></span> <span data-ttu-id="2373c-145">추적 버퍼가 클수록 저장할 수 있는 항목이 더 많습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-145">The larger the trace buffer, the more entries it is able to store.</span></span>
- <span data-ttu-id="2373c-146">**registry_entries**: 추적 레지스트리에 유지할 애플리케이션 ThreadX 개체의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-146">**registry_entries**: Number of application ThreadX objects to keep in the trace registry.</span></span> <span data-ttu-id="2373c-147">레지스트리는 개체 주소와 개체 이름의 상관 관계를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-147">The registry is used to correlate object addresses with object names.</span></span> <span data-ttu-id="2373c-148">이는 GUI 추적 분석 도구에 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-148">This is highly useful for GUI trace analysis tools.</span></span>

#### <a name="return-values"></a><span data-ttu-id="2373c-149">반환 값</span><span class="sxs-lookup"><span data-stu-id="2373c-149">Return Values</span></span>

- <span data-ttu-id="2373c-150">**TX_SUCCESS** (0x00) 이벤트 추적을 사용하도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-150">**TX_SUCCESS** (0x00) Successful event trace enable.</span></span>
- <span data-ttu-id="2373c-151">**TX_SIZE_ERROR** (0x05) 지정된 추적 버퍼 크기가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-151">**TX_SIZE_ERROR** (0x05) Specified trace buffer size is too small.</span></span> <span data-ttu-id="2373c-152">추적 헤더, 개체 레지스트리 및 하나 이상의 추적 항목에 대해 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-152">It must be large enough for the trace header, the object registry, and at least one trace entry.</span></span>
- <span data-ttu-id="2373c-153">**TX_NOT_DONE** (0X20) 이미 이벤트 추적을 사용하도록 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-153">**TX_NOT_DONE** (0x20) Event tracing was already enabled.</span></span>
- <span data-ttu-id="2373c-154">**TX_FEATURE_NOT_ENABLED** (0xFF) 추적을 사용하도록 설정된 상태에서 시스템이 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-154">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="2373c-155">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="2373c-155">Allowed From</span></span>

<span data-ttu-id="2373c-156">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="2373c-156">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="2373c-157">예제</span><span class="sxs-lookup"><span data-stu-id="2373c-157">Example</span></span>

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a><span data-ttu-id="2373c-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2373c-158">See Also</span></span>

<span data-ttu-id="2373c-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="2373c-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_filter"></a><span data-ttu-id="2373c-160">tx_trace_event_filter</span><span class="sxs-lookup"><span data-stu-id="2373c-160">tx_trace_event_filter</span></span>

<span data-ttu-id="2373c-161">지정된 이벤트 필터링</span><span class="sxs-lookup"><span data-stu-id="2373c-161">Filter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="2373c-162">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2373c-162">Prototype</span></span>

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a><span data-ttu-id="2373c-163">Description</span><span class="sxs-lookup"><span data-stu-id="2373c-163">Description</span></span>

<span data-ttu-id="2373c-164">이 서비스는 지정된 이벤트가 활성 추적 버퍼에 삽입되지 않도록 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-164">This service filters the specified event(s) from being inserted into the active trace buffer.</span></span> <span data-ttu-id="2373c-165">기본적으로 *tx_trace_enable* 를 호출한 후에는 이벤트를 필터링하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-165">Note that by default no events are filtered after *tx_trace_enable* is called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2373c-166">ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-166">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="2373c-167">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2373c-167">Input Parameters</span></span>

- <span data-ttu-id="2373c-168">**event_filter_bits**: 필터링할 이벤트에 해당하는 비트입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-168">**event_filter_bits**: Bits that correspond to events to filter.</span></span> <span data-ttu-id="2373c-169">적절한 상수를 OR 연산하면 여러 이벤트를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-169">Multiple events may be filtered by simply oring together the appropriate constants.</span></span> <span data-ttu-id="2373c-170">이 변수에 대한 유효한 상수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-170">Valid constants for this variable are defined as follows:</span></span>

```c
TX_TRACE_ALL_EVENTS                   0x000007FF
TX_TRACE_INTERNAL_EVENTS              0x00000001
TX_TRACE_BLOCK_POOL_EVENTS            0x00000002
TX_TRACE_BYTE_POOL_EVENTS             0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS           0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT      0x00000010
TX_TRACE_MUTEX_EVENTS                 0x00000020
TX_TRACE_QUEUE_EVENTS                 0x00000040
TX_TRACE_SEMAPHORE_EVENTS             0x00000080
TX_TRACE_THREAD_EVENTS                0x00000100
TX_TRACE_TIME_EVENTS                  0x00000200
TX_TRACE_TIMER_EVENTS                 0x00000400
FX_TRACE_ALL_EVENTS                   0x00007800
FX_TRACE_INTERNAL_EVENTS              0x00000800
FX_TRACE_MEDIA_EVENTS                 0x00001000
FX_TRACE_DIRECTORY_EVENTS             0x00002000
FX_TRACE_FILE_EVENTS                  0x00004000
NX_TRACE_ALL_EVENTS                   0x00FF8000
NX_TRACE_INTERNAL_EVENTS              0x00008000
NX_TRACE_ARP_EVENTS                   0x00010000
NX_TRACE_ICMP_EVENTS                  0x00020000
NX_TRACE_IGMP_EVENTS                  0x00040000
NX_TRACE_IP_EVENTS                    0x00080000
NX_TRACE_PACKET_EVENTS                0x00100000
NX_TRACE_RARP_EVENTS                  0x00200000
NX_TRACE_TCP_EVENTS                   0x00400000
NX_TRACE_UDP_EVENTS                   0x00800000
UX_TRACE_ALL_EVENTS                   0x7F000000
UX_TRACE_ERRORS                       0x01000000
UX_TRACE_HOST_STACK_EVENTS            0x02000000
UX_TRACE_DEVICE_STACK_EVENTS          0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS       0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS     0x10000000
UX_TRACE_HOST_CLASS_EVENTS            0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS          0x40000000
```

#### <a name="return-values"></a><span data-ttu-id="2373c-171">반환 값</span><span class="sxs-lookup"><span data-stu-id="2373c-171">Return Values</span></span>

- <span data-ttu-id="2373c-172">**TX_SUCCESS** (0X00) 이벤트 필터링을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-172">**TX_SUCCESS** (0x00) Successful event filter.</span></span>
- <span data-ttu-id="2373c-173">**TX_FEATURE_NOT_ENABLED** (0xFF) 추적을 사용하도록 설정된 상태에서 시스템이 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-173">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="2373c-174">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="2373c-174">Allowed From</span></span>

<span data-ttu-id="2373c-175">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="2373c-175">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="2373c-176">예제</span><span class="sxs-lookup"><span data-stu-id="2373c-176">Example</span></span>

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="2373c-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2373c-177">See Also</span></span>

<span data-ttu-id="2373c-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="2373c-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_unfilter"></a><span data-ttu-id="2373c-179">tx_trace_event_unfilter</span><span class="sxs-lookup"><span data-stu-id="2373c-179">tx_trace_event_unfilter</span></span>

<span data-ttu-id="2373c-180">지정된 이벤트 필터링 안 함</span><span class="sxs-lookup"><span data-stu-id="2373c-180">Unfilter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="2373c-181">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2373c-181">Prototype</span></span>

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a><span data-ttu-id="2373c-182">Description</span><span class="sxs-lookup"><span data-stu-id="2373c-182">Description</span></span>

<span data-ttu-id="2373c-183">이 서비스는 활성 추적 버퍼에 삽입되도록 지정된 이벤트를 필터링하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-183">This service unfilters the specified event(s) such that they will be inserted into the active trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2373c-184">ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-184">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="2373c-185">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2373c-185">Input Parameters</span></span>

- <span data-ttu-id="2373c-186">**event_unfilter_bits**: 필터링하지 않는 이벤트에 해당하는 비트입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-186">**event_unfilter_bits**: Bits that correspond to events to unfilter.</span></span> <span data-ttu-id="2373c-187">적절한 상수를 OR 연산하여 여러 이벤트를 필터링하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-187">Multiple events may be unfiltered by simply or-ing together the appropriate constants.</span></span> <span data-ttu-id="2373c-188">이 변수에 대한 유효한 상수는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-188">Valid constants for this variable are defined as follows:</span></span>

```c
TX_TRACE_ALL_EVENTS                  0x000007FF
TX_TRACE_INTERNAL_EVENTS             0x00000001
TX_TRACE_BLOCK_POOL_EVENTS           0x00000002
TX_TRACE_BYTE_POOL_EVENTS            0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS          0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT     0x00000010
TX_TRACE_MUTEX_EVENTS                0x00000020
TX_TRACE_QUEUE_EVENTS                0x00000040
TX_TRACE_SEMAPHORE_EVENTS            0x00000080
TX_TRACE_THREAD_EVENTS               0x00000100
TX_TRACE_TIME_EVENTS                 0x00000200
TX_TRACE_TIMER_EVENTS                0x00000400
FX_TRACE_ALL_EVENTS                  0x00007800
FX_TRACE_INTERNAL_EVENTS             0x00000800
FX_TRACE_MEDIA_EVENTS                0x00001000
FX_TRACE_DIRECTORY_EVENTS            0x00002000
FX_TRACE_FILE_EVENTS                 0x00004000
NX_TRACE_ALL_EVENTS                  0x00FF8000
NX_TRACE_INTERNAL_EVENTS             0x00008000
NX_TRACE_ARP_EVENTS                  0x00010000
NX_TRACE_ICMP_EVENTS                 0x00020000
NX_TRACE_IGMP_EVENTS                 0x00040000
NX_TRACE_IP_EVENTS                   0x00080000
NX_TRACE_PACKET_EVENTS               0x00100000
NX_TRACE_RARP_EVENTS                 0x00200000
NX_TRACE_TCP_EVENTS                  0x00400000
NX_TRACE_UDP_EVENTS                  0x00800000
UX_TRACE_ALL_EVENTS                  0x7F000000
UX_TRACE_ERRORS                      0x01000000
UX_TRACE_HOST_STACK_EVENTS           0x02000000
UX_TRACE_DEVICE_STACK_EVENTS         0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS      0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS    0x10000000
UX_TRACE_HOST_CLASS_EVENTS           0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS         0x40000000
```

#### <a name="return-values"></a><span data-ttu-id="2373c-189">반환 값</span><span class="sxs-lookup"><span data-stu-id="2373c-189">Return Values</span></span>

- <span data-ttu-id="2373c-190">**TX_SUCCESS** (0X00) 이벤트 필터링을 수행하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-190">**TX_SUCCESS** (0x00) Successful event unfilter.</span></span>
- <span data-ttu-id="2373c-191">**TX_FEATURE_NOT_ENABLED** (0xFF) 추적을 사용하도록 설정된 상태에서 시스템이 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-191">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="2373c-192">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="2373c-192">Allowed From</span></span>

<span data-ttu-id="2373c-193">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="2373c-193">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="2373c-194">예제</span><span class="sxs-lookup"><span data-stu-id="2373c-194">Example</span></span>

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="2373c-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2373c-195">See Also</span></span>

<span data-ttu-id="2373c-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="2373c-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_disable"></a><span data-ttu-id="2373c-197">tx_trace_disable</span><span class="sxs-lookup"><span data-stu-id="2373c-197">tx_trace_disable</span></span>

#### <a name="disable-event-tracing"></a><span data-ttu-id="2373c-198">이벤트 추적 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="2373c-198">Disable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="2373c-199">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2373c-199">Prototype</span></span>

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a><span data-ttu-id="2373c-200">Description</span><span class="sxs-lookup"><span data-stu-id="2373c-200">Description</span></span>

<span data-ttu-id="2373c-201">이 서비스는 ThreadX 내의 이벤트 추적을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-201">This service disables event tracing inside ThreadX.</span></span> <span data-ttu-id="2373c-202">이는 애플리케이션이 런타임 중에 현재 이벤트 추적 버퍼를 고정하고 외부에서 전송하려는 경우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-202">This can be useful if the application wants to freeze the current event trace buffer and possibly transport it externally during run-time.</span></span> <span data-ttu-id="2373c-203">사용하지 않도록 설정되면 **tx_trace_enable** 를 호출하여 추적을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-203">Once disabled, the **tx_trace_enable** can be called to start tracing again.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2373c-204">ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-204">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="2373c-205">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2373c-205">Input Parameters</span></span>

<span data-ttu-id="2373c-206">없음</span><span class="sxs-lookup"><span data-stu-id="2373c-206">None.</span></span>

#### <a name="return-values"></a><span data-ttu-id="2373c-207">반환 값</span><span class="sxs-lookup"><span data-stu-id="2373c-207">Return Values</span></span>

- <span data-ttu-id="2373c-208">**TX_SUCCESS** (0x00) 이벤트 추적을 사용하지 않도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-208">**TX_SUCCESS** (0x00) Successful event trace disable.</span></span>
- <span data-ttu-id="2373c-209">**TX_NOT_DONE** (0X20) 이벤트 추적을 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-209">**TX_NOT_DONE** (0x20) Event tracing was not enabled.</span></span>
- <span data-ttu-id="2373c-210">**TX_FEATURE_NOT_ENABLED** (0xFF) 추적을 사용하도록 설정된 상태에서 시스템이 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-210">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="2373c-211">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="2373c-211">Allowed From</span></span>

<span data-ttu-id="2373c-212">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="2373c-212">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="2373c-213">예제</span><span class="sxs-lookup"><span data-stu-id="2373c-213">Example</span></span> 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a><span data-ttu-id="2373c-214">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2373c-214">See Also</span></span>

<span data-ttu-id="2373c-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="2373c-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_enter_insert"></a><span data-ttu-id="2373c-216">tx_trace_isr_enter_insert</span><span class="sxs-lookup"><span data-stu-id="2373c-216">tx_trace_isr_enter_insert</span></span>

#### <a name="insert-isr-enter-event"></a><span data-ttu-id="2373c-217">ISR 입력 이벤트 삽입</span><span class="sxs-lookup"><span data-stu-id="2373c-217">Insert ISR enter event</span></span>

#### <a name="prototype"></a><span data-ttu-id="2373c-218">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2373c-218">Prototype</span></span>

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="2373c-219">Description</span><span class="sxs-lookup"><span data-stu-id="2373c-219">Description</span></span>

<span data-ttu-id="2373c-220">이 서비스는 이벤트 추적 버퍼에 ISR 입력 이벤트를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-220">This service inserts the ISR enter event into the event trace buffer.</span></span> <span data-ttu-id="2373c-221">ISR 처리가 시작될 때 애플리케이션에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-221">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="2373c-222">제공된 매개 변수는 애플리케이션에 대한 특정 ISR을 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-222">The supplied parameter should identify the specific ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2373c-223">ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-223">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="2373c-224">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2373c-224">Input Parameters</span></span> 
- <span data-ttu-id="2373c-225">**isr_id**: ISR을 식별하기 위한 애플리케이션 관련 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-225">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="2373c-226">반환 값</span><span class="sxs-lookup"><span data-stu-id="2373c-226">Return Values</span></span>

<span data-ttu-id="2373c-227">**없음**</span><span class="sxs-lookup"><span data-stu-id="2373c-227">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="2373c-228">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="2373c-228">Allowed From</span></span> 

<span data-ttu-id="2373c-229">ISR</span><span class="sxs-lookup"><span data-stu-id="2373c-229">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="2373c-230">예제</span><span class="sxs-lookup"><span data-stu-id="2373c-230">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="2373c-231">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2373c-231">See Also</span></span>

<span data-ttu-id="2373c-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="2373c-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_exit_insert"></a><span data-ttu-id="2373c-233">tx_trace_isr_exit_insert</span><span class="sxs-lookup"><span data-stu-id="2373c-233">tx_trace_isr_exit_insert</span></span>

#### <a name="insert-isr-exit-event"></a><span data-ttu-id="2373c-234">ISR 종료 이벤트 삽입</span><span class="sxs-lookup"><span data-stu-id="2373c-234">Insert ISR exit event</span></span>

#### <a name="prototype"></a><span data-ttu-id="2373c-235">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2373c-235">Prototype</span></span>

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="2373c-236">Description</span><span class="sxs-lookup"><span data-stu-id="2373c-236">Description</span></span>

<span data-ttu-id="2373c-237">이 서비스는 이벤트 추적 버퍼에 ISR 항목 이벤트를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-237">This service inserts the ISR entry event into the event trace buffer.</span></span> <span data-ttu-id="2373c-238">ISR 처리가 시작될 때 애플리케이션에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-238">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="2373c-239">제공된 매개 변수는 애플리케이션에 대한 ISR을 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-239">The supplied parameter should identify the ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2373c-240">ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-240">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="2373c-241">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2373c-241">Input Parameters</span></span> 

- <span data-ttu-id="2373c-242">**isr_id**: ISR을 식별하기 위한 애플리케이션 관련 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-242">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="2373c-243">반환 값</span><span class="sxs-lookup"><span data-stu-id="2373c-243">Return Values</span></span>

<span data-ttu-id="2373c-244">**없음**</span><span class="sxs-lookup"><span data-stu-id="2373c-244">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="2373c-245">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="2373c-245">Allowed From</span></span>

<span data-ttu-id="2373c-246">ISR</span><span class="sxs-lookup"><span data-stu-id="2373c-246">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="2373c-247">예제</span><span class="sxs-lookup"><span data-stu-id="2373c-247">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="2373c-248">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2373c-248">See Also</span></span>

<span data-ttu-id="2373c-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="2373c-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_buffer_full_notify"></a><span data-ttu-id="2373c-250">tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="2373c-250">tx_trace_buffer_full_notify</span></span>

#### <a name="register-trace-buffer-full-application-callback"></a><span data-ttu-id="2373c-251">추적 버퍼 전체 애플리케이션 콜백 등록</span><span class="sxs-lookup"><span data-stu-id="2373c-251">Register trace buffer full application callback</span></span>

#### <a name="prototype"></a><span data-ttu-id="2373c-252">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2373c-252">Prototype</span></span>

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a><span data-ttu-id="2373c-253">Description</span><span class="sxs-lookup"><span data-stu-id="2373c-253">Description</span></span>

<span data-ttu-id="2373c-254">이 서비스는 추적 버퍼가 가득 찰 때 ThreadX에 의해 호출되는 애플리케이션 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-254">This service registers an application callback function that is called by ThreadX when the trace buffer becomes full.</span></span> <span data-ttu-id="2373c-255">그런 다음 애플리케이션에서 추적을 사용하지 않도록 설정하거나 새 추적 버퍼를 설정하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-255">The application can then choose to disable tracing and/or possibly setup a new trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2373c-256">ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-256">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="2373c-257">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2373c-257">Input Parameters</span></span>

- <span data-ttu-id="2373c-258">**full_buffer_callback**: 추적 버퍼가 가득 차면 호출할 애플리케이션 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-258">**full_buffer_callback**: Application function to call when the trace buffer is full.</span></span> <span data-ttu-id="2373c-259">NULL 값은 알림 콜백을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-259">A value of NULL disables the notification callback.</span></span>

#### <a name="return-values"></a><span data-ttu-id="2373c-260">반환 값</span><span class="sxs-lookup"><span data-stu-id="2373c-260">Return Values</span></span>

<span data-ttu-id="2373c-261">**없음**</span><span class="sxs-lookup"><span data-stu-id="2373c-261">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="2373c-262">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="2373c-262">Allowed From</span></span>

<span data-ttu-id="2373c-263">ISR</span><span class="sxs-lookup"><span data-stu-id="2373c-263">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="2373c-264">예제</span><span class="sxs-lookup"><span data-stu-id="2373c-264">Example</span></span>

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a><span data-ttu-id="2373c-265">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2373c-265">See Also</span></span>

<span data-ttu-id="2373c-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="2373c-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_user_event_insert"></a><span data-ttu-id="2373c-267">tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="2373c-267">tx_trace_user_event_insert</span></span>

#### <a name="insert-user-event"></a><span data-ttu-id="2373c-268">사용자 이벤트 삽입</span><span class="sxs-lookup"><span data-stu-id="2373c-268">Insert user event</span></span>

#### <a name="prototype"></a><span data-ttu-id="2373c-269">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2373c-269">Prototype</span></span>

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a><span data-ttu-id="2373c-270">Description</span><span class="sxs-lookup"><span data-stu-id="2373c-270">Description</span></span>

<span data-ttu-id="2373c-271">이 서비스는 사용자 이벤트를 추적 버퍼에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-271">This service inserts the user event into the trace buffer.</span></span> <span data-ttu-id="2373c-272">사용자 이벤트 ID는 4096으로 정의된 상수 **TX_TRACE_USER_EVENT_START** 보다 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-272">User event IDs must be greater than the constant **TX_TRACE_USER_EVENT_START**, which is defined to be 4096.</span></span> <span data-ttu-id="2373c-273">최대 사용자 이벤트는 65535로 정의된 상수 **TX_TRACE_USER_EVENT_END** 에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-273">The maximum user event is defined by the constant **TX_TRACE_USER_EVENT_END**, which is defined to be 65535.</span></span> <span data-ttu-id="2373c-274">이 범위 내의 모든 이벤트는 애플리케이션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-274">All events within this range are available to the application.</span></span> <span data-ttu-id="2373c-275">정보 필드는 애플리케이션마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-275">The information fields are application specific.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2373c-276">ThreadX 라이브러리 및 애플리케이션은 이벤트 추적을 사용하기 위해 정의된 **TX_ENABLE_EVENT_TRACE** 를 사용하여 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-276">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="2373c-277">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="2373c-277">Input Parameters</span></span>

- <span data-ttu-id="2373c-278">**event_id**: 애플리케이션 관련 이벤트 ID는 **TX_TRACE_USER_EVENT_START** 보다 크고 **TX_TRACE_USER_EVENT_END** 보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-278">**event_id**: Application-specific event identification and must start be greater than **TX_TRACE_USER_EVENT_START** and less than or equal to **TX_TRACE_USER_EVENT_END**.</span></span>
- <span data-ttu-id="2373c-279">**info_field_1**: 애플리케이션 관련 정보 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-279">**info_field_1**: Application-specific information field.</span></span>
- <span data-ttu-id="2373c-280">**info_field_2**: 애플리케이션 관련 정보 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-280">**info_field_2**: Application-specific information field.</span></span>
- <span data-ttu-id="2373c-281">**info_field_3**: 애플리케이션 관련 정보 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-281">**info_field_3**: Application-specific information field.</span></span>
- <span data-ttu-id="2373c-282">**info_field_4**: 애플리케이션 관련 정보 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-282">**info_field_4**: Application-specific information field.</span></span>

#### <a name="return-values"></a><span data-ttu-id="2373c-283">반환 값</span><span class="sxs-lookup"><span data-stu-id="2373c-283">Return Values</span></span>
- <span data-ttu-id="2373c-284">**TX_SUCCESS** (0x00) 사용자 이벤트 삽입을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-284">**TX_SUCCESS** (0x00) Successful user event insert.</span></span>
- <span data-ttu-id="2373c-285">**TX_NOT_DONE** (0X20) 이벤트 추적을 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-285">**TX_NOT_DONE** (0x20) Event tracing is not enabled.</span></span>
- <span data-ttu-id="2373c-286">**TX_FEATURE_NOT_ENABLED** (0xFF) 추적이 설정된 상태에서 시스템이 컴파일되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2373c-286">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="2373c-287">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="2373c-287">Allowed From</span></span>

<span data-ttu-id="2373c-288">초기화 및 스레드</span><span class="sxs-lookup"><span data-stu-id="2373c-288">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="2373c-289">예제</span><span class="sxs-lookup"><span data-stu-id="2373c-289">Example</span></span>

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="2373c-290">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2373c-290">See Also</span></span>

<span data-ttu-id="2373c-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="2373c-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify</span></span>