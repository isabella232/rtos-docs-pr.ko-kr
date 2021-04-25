---
title: 챕터 11 - 이벤트 추적 버퍼의 형식
description: ThreadX는 모든 Azure RTOS ThreadX 서비스, 스레드 상태 변경 및 사용자 정의 이벤트에 대한 기본 제공 이벤트 추적 지원을 제공합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: d11b827558e9c96df44f462329b7807a500a64a4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812391"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a><span data-ttu-id="aa32e-103">챕터 11 - 이벤트 추적 버퍼의 형식</span><span class="sxs-lookup"><span data-stu-id="aa32e-103">Chapter 11 - Format of event trace buffer</span></span>

<span data-ttu-id="aa32e-104">Azure RTOS ThreadX는 모든 ThreadX 서비스, 스레드 상태 변경 및 사용자 정의 이벤트에 대한 기본 제공 이벤트 추적 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-104">Azure RTOS ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="aa32e-105">이벤트 추적을 사용하려면 **TX_ENABLE_EVENT_TRACE** 가 정의된 Threadx, Netx 및 FileX 라이브러리를 간단하게 빌드하고 **_tx_trace_enable_** 함수를 호출하여 추적을 사용하도록 설정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-105">To use event trace, simply build the ThreadX, NetX, and FileX libraries with **TX_ENABLE_EVENT_TRACE** defined and enable tracing by calling the **_tx_trace_enable_** function.</span></span> <span data-ttu-id="aa32e-106">이 챕터에서는 해당 프로세스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-106">This chapter describes that process.</span></span>

## <a name="event-trace-format"></a><span data-ttu-id="aa32e-107">이벤트 추적 형식</span><span class="sxs-lookup"><span data-stu-id="aa32e-107">Event Trace Format</span></span>

<span data-ttu-id="aa32e-108">ThreadX 이벤트 추적 버퍼의 형식은 컨트롤 헤더, 개체 레지스트리 및 추적 항목의 세 가지 섹션으로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-108">The format of the ThreadX event trace buffer is divided into three sections, namely the control header, object registry, and the trace entries.</span></span> <span data-ttu-id="aa32e-109">다음은 ThreadX 이벤트 추적 버퍼의 일반 레이아웃을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-109">The following describes the general layout of the ThreadX event trace buffer:</span></span>

<span data-ttu-id="aa32e-110">**컨트롤 헤더**</span><span class="sxs-lookup"><span data-stu-id="aa32e-110">**Control Header**</span></span>

<span data-ttu-id="aa32e-111">**개체 레지스트리 항목 0**</span><span class="sxs-lookup"><span data-stu-id="aa32e-111">**Object Registry Entry 0**</span></span>

<span data-ttu-id="aa32e-112">**…**</span><span class="sxs-lookup"><span data-stu-id="aa32e-112">**…**</span></span>

<span data-ttu-id="aa32e-113">**개체 등록 항목 "n"**</span><span class="sxs-lookup"><span data-stu-id="aa32e-113">**Object Register Entry "n"**</span></span>

<span data-ttu-id="aa32e-114">**이벤트 추적 항목 0**</span><span class="sxs-lookup"><span data-stu-id="aa32e-114">**Event Trace Entry 0**</span></span>

<span data-ttu-id="aa32e-115">**…**</span><span class="sxs-lookup"><span data-stu-id="aa32e-115">**…**</span></span>

<span data-ttu-id="aa32e-116">**이벤트 추적 항목 "n"**</span><span class="sxs-lookup"><span data-stu-id="aa32e-116">**Event Trace Entry "n"**</span></span>

### <a name="event-trace-control-header"></a><span data-ttu-id="aa32e-117">이벤트 추적 컨트롤 헤더</span><span class="sxs-lookup"><span data-stu-id="aa32e-117">Event Trace Control Header</span></span>

<span data-ttu-id="aa32e-118">컨트롤 헤더는 이벤트 추적 버퍼의 정확한 레이아웃을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-118">The control header defines the exact layout of the event trace buffer.</span></span> <span data-ttu-id="aa32e-119">여기에는 등록할 수 있는 ThreadX 개체 수뿐만 아니라 기록될 수 있는 이벤트의 수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-119">This includes how many ThreadX objects can be registered as well as how many events can be recorded.</span></span> <span data-ttu-id="aa32e-120">또한 컨트롤 헤더는 추적 버퍼의 각 요소가 상주하는 위치를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-120">In addition, the control header defines where each of the elements of the trace buffer resides.</span></span> <span data-ttu-id="aa32e-121">다음 데이터 구조는 컨트롤 헤더를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-121">The following data structure defines the control header:</span></span>

```c
typedef struct TX_TRACE_CONTROL_HEADER_STRUCT
{
    ULONG    tx_trace_control_header_id;
    ULONG    tx_trace_control_header_timer_valid_mask;
    ULONG    tx_trace_control_header_trace_base_address;
    ULONG    tx_trace_control_header_object_registry_start_pointer;
    USHORT   tx_trace_control_header_reserved1;
    USHORT   tx_trace_control_header_object_registry_name_size;
    ULONG    tx_trace_control_header_object_registry_end_pointer;
    ULONG    tx_trace_control_header_buffer_start_pointer;
    ULONG    tx_trace_control_header_buffer_end_pointer;
    ULONG    tx_trace_control_header_buffer_current_pointer;
    ULONG    tx_trace_control_header_reserved2;
    ULONG    tx_trace_control_header_reserved3;
    ULONG    tx_trace_control_header_reserved4;
} TX_TRACE_CONTROL_HEADER;
```

### <a name="control-header-id"></a><span data-ttu-id="aa32e-122">컨트롤 헤더 ID</span><span class="sxs-lookup"><span data-stu-id="aa32e-122">Control Header ID</span></span>

<span data-ttu-id="aa32e-123">컨트롤 헤더 ID는 ASCII 문자 ***TXTB*** 에 해당하는 32 비트 16진수 값(0x54585442)으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-123">The control header ID consists of the 32-bit HEX value of 0x54585442, which corresponds to the ASCII characters ***TXTB***.</span></span> <span data-ttu-id="aa32e-124">이 값은 32비트의 부호 없는 변수로 작성되므로, 이벤트 추적 버퍼의 엔디언을 검색하는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-124">Since this value is written as a 32-bit unsigned variable, it can also be used to detect the endianness of the event trace buffer.</span></span> <span data-ttu-id="aa32e-125">예를 들어 처음 네 개의 메모리에 있는 값이 0x54, 0x58, 0x54, 0x42인 경우 이벤트 추적 버퍼는 big endian 형식으로 작성된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-125">For example, if the value in the first four byes of memory is 0x54, 0x58, 0x54, 0x42, the event trace buffer was written in big endian format.</span></span> <span data-ttu-id="aa32e-126">그렇지 않으면 이벤트 추적 버퍼가 little endian 형식으로 작성된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-126">Otherwise, the event trace buffer was written in little endian format.</span></span>

### <a name="timer-valid-mask"></a><span data-ttu-id="aa32e-127">타이머 유효 마스크</span><span class="sxs-lookup"><span data-stu-id="aa32e-127">Timer Valid Mask</span></span>

<span data-ttu-id="aa32e-128">타이머 유효 마스크는 실제 이벤트 추적 항목에 유효한 타임스탬프의 비트 수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-128">The timer valid mask defines how many bits of the timestamp in the actual event trace entries are valid.</span></span> <span data-ttu-id="aa32e-129">예를 들어 타임스탬프 원본이 16비트인 경우, 이 필드의 값은 0xFFFF여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-129">For example, if the time-stamp source has 16-bits, the value in this field should be 0xFFFF.</span></span> <span data-ttu-id="aa32e-130">32비트 타임스탬프 원본의 값은 0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-130">A 32-bit time-stamp source would have a value of 0xFFFFFFFF.</span></span> <span data-ttu-id="aa32e-131">이 값은 _\*_tx_port.h_\*\*의 \***TX_TRACE_TIME_MASK** _ 상수에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-131">This value is defined by the ***TX_TRACE_TIME_MASK** _ constant in _*_tx_port.h_\*\*.</span></span>

### <a name="trace-base-address"></a><span data-ttu-id="aa32e-132">추적 기준 주소</span><span class="sxs-lookup"><span data-stu-id="aa32e-132">Trace Base Address</span></span>

<span data-ttu-id="aa32e-133">추적 버퍼 기준 주소는 애플리케이션이 ***tx_trace_enable*** 호출에서 추적 버퍼의 시작으로 지정한 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-133">The trace buffer base address is the address the application specified as the start of the trace buffer in the ***tx_trace_enable*** call.</span></span> <span data-ttu-id="aa32e-134">이 주소는 분석 도구를 사용하여 버퍼의 다양한 요소에 대한 상대 버퍼 오프셋을 유도하는 용도로만 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-134">This address is maintained for the sole use of the analysis tool to derive bufferrelative offsets for the various elements in the buffer.</span></span> <span data-ttu-id="aa32e-135">예를 들어 추적 버퍼에서 현재 이벤트의 상대 버퍼 오프셋은 현재 이벤트 주소에서 간단하게 빼기를 사용하여 기준 주소를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-135">For example, the buffer relative offset of the current event in the trace buffer is calculated by simple subtraction of the base address from the current event address.</span></span>

### <a name="registry-start-and-end-pointers"></a><span data-ttu-id="aa32e-136">레지스트리 시작 및 끝 포인터</span><span class="sxs-lookup"><span data-stu-id="aa32e-136">Registry Start and End Pointers</span></span>

<span data-ttu-id="aa32e-137">레지스트리 시작 포인터는 첫 번째 개체 레지스트리 항목의 주소를 가리키며, 레지스트리 끝 포인터는 마지막 등록 항목의 다음 주소 im../mediately를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-137">The registry start pointer points to the address of the first object registry entry, while the registry end pointer points to the address im../mediately following the last register entry.</span></span> <span data-ttu-id="aa32e-138">이러한 값은 *tx_trace_enable* 을 처리하는 동안 설정되며 추적 기간 동안 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-138">These values are setup during the *tx_trace_enable* processing and are not changed throughout the duration of tracing.</span></span>

### <a name="registry-name-size"></a><span data-ttu-id="aa32e-139">레지스트리 이름 크기</span><span class="sxs-lookup"><span data-stu-id="aa32e-139">Registry Name Size</span></span>

<span data-ttu-id="aa32e-140">레지스트리 이름 크기는 레지스트리 항목의 각 개체 이름에 대한 최대 크기(바이트)를 정의하며 \***TX_TRACE_OBJECT_REGISTRY_NAME** _ 기호로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-140">The registry name size defines maximum size in bytes for each object name in the registry entry and is defined by the symbol \***TX_TRACE_OBJECT_REGISTRY_NAME** _.</span></span> <span data-ttu-id="aa32e-141">기본값은 32이며 _*_tx_trace.h_*_ 에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-141">The default value is 32 and is defined in _*_tx_trace.h_*_.</span></span> <span data-ttu-id="aa32e-142">개체 이름은 개체가 생성될 때 애플리케이션에서 지정하는 이름에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-142">The object name corresponds to the name given by the application when the object was created.</span></span> <span data-ttu-id="aa32e-143">예를 들어 스레드의 개체 레지스트리 이름은 애플리케이션이 _*_tx_thread_create_*\* 호출에 제공한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-143">For example, the object registry name for a thread is the name supplied by the application to the _\*_tx_thread_create_\*\*call.</span></span>

### <a name="buffer-start-and-end-pointers"></a><span data-ttu-id="aa32e-144">버퍼 시작 및 끝 포인터</span><span class="sxs-lookup"><span data-stu-id="aa32e-144">Buffer Start and End Pointers</span></span>

<span data-ttu-id="aa32e-145">이벤트 추적 버퍼 시작 포인터는 첫 번째 추적 항목의 주소를 가리키며, 레지스트리 끝 포인터는 마지막 추적 항목의 다음 주소 im../mediately를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-145">The event trace buffer start pointer points to the address of the first trace entry, while the registry end pointer points to the address im../mediately following the last trace entry.</span></span> <span data-ttu-id="aa32e-146">이러한 값은 ***tx_trace_enable</*** 을 처리하는 동안 설정되며 추적 기간 동안 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-146">These values are setup during the ***tx_trace_enable</*** processing and are not changed throughout the duration of tracing.</span></span>

### <a name="current-buffer-pointer"></a><span data-ttu-id="aa32e-147">현재 버퍼 포인터</span><span class="sxs-lookup"><span data-stu-id="aa32e-147">Current Buffer Pointer</span></span>

<span data-ttu-id="aa32e-148">이벤트 추적 버퍼의 현재 포인터는 가장 오래된 추적 항목의 주소를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-148">The event trace buffer current pointer points to the address of the oldest trace entry.</span></span> <span data-ttu-id="aa32e-149">추적 항목은 순환 목록으로 유지 관리되므로, 현재 버퍼 포인터는 작성할 다음 추적 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-149">Since the trace entries are maintained in a circular list, the current buffer pointer is also represents the next trace entry to be written.</span></span> |

## <a name="event-trace-object-registry"></a><span data-ttu-id="aa32e-150">이벤트 추적 개체 레지스트리</span><span class="sxs-lookup"><span data-stu-id="aa32e-150">Event Trace Object Registry</span></span>

<span data-ttu-id="aa32e-151">이벤트 추적 개체 레지스트리는 애플리케이션에서 만든 개체에 해당하는 \***n** _ 개체 레지스트리 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-151">The event trace object registry contains \***n** _ object registry entries that correspond to the objects created by the application.</span></span> <span data-ttu-id="aa32e-152">개체 레지스트리의 주요 목적은 외부 분석 도구를 사용하여 실제 개체 이름과 추적 버퍼 항목의 개체 주소를 상호 연결하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-152">The main purpose of the object registry is for external analysis tools to correlate actual object names with the object addresses of the trace buffer entries.</span></span> <span data-ttu-id="aa32e-153">레지스트리 항목의 수는 _ *_tx_trace_enable_*\* 호출에서 애플리케이션에 의해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-153">The number of registry entries is specified by the application in the _ *_tx_trace_enable_*\* call.</span></span>

<span data-ttu-id="aa32e-154">각 개체 등록 항목에는 애플리케이션에서 이전에 만든 특정 ThreadX 개체에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-154">Each object register entry contains information about a specific ThreadX object previously created by the application.</span></span> <span data-ttu-id="aa32e-155">다음 데이터 구조는 각 개체 레지스트리 항목을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-155">The following data structure defines each object registry entry:</span></span>

```c
typedef struct TX_TRACE_OBJECT_REGISTRY_ENTRY_STRUCT
{
    UCHAR    tx_trace_object_registry_entry_object_available**;
    UCHAR    tx_trace_object_registry_entry_object_type**;
    UCHAR    tx_trace_object_registry_entry_object_reserved1;
    UCHAR    tx_trace_object_registry_entry_object_reserved2;
    ULONG    tx_trace_thread_registry_entry_object_pointer;
    ULONG    tx_trace_object_registry_entry_object_parameter_1;
    ULONG    tx_trace_object_registry_entry_object_parameter_2;
    UCHAR    tx_trace_thread_registry_entry_object_name[TX_TRACE_OBJECT_REGISTRY_NAME];

} TX_TRACE_OBJECT_REGISTRY_ENTRY;
```

### <a name="object-available-flag"></a><span data-ttu-id="aa32e-156">개체 사용 가능 플래그</span><span class="sxs-lookup"><span data-stu-id="aa32e-156">Object Available Flag</span></span>

<span data-ttu-id="aa32e-157">개체 레지스트리 항목을 사용할 수 있는 경우 개체 사용 가능 플래그가 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-157">The object available flag is set to 1 if the object registry entry is available.</span></span> <span data-ttu-id="aa32e-158">값이 1이 아닌 경우에는 개체 레지스트리 항목을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-158">Otherwise, if the value is not 1, the object registry entry is not available.</span></span> <span data-ttu-id="aa32e-159">항목을 사용할 수 있는 경우에도 유효한 정보를 계속 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-159">Note that the entry could still contain valid information even though it is available.</span></span>

### <a name="object-entry-type"></a><span data-ttu-id="aa32e-160">개체 항목 유형</span><span class="sxs-lookup"><span data-stu-id="aa32e-160">Object Entry Type</span></span>

<span data-ttu-id="aa32e-161">개체 항목 유형은 이 항목의 개체 유형을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-161">The object entry type identifies the type of object in this entry.</span></span> <span data-ttu-id="aa32e-162">다음은 유효한 개체 유형 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-162">The following is a list of the valid object types:</span></span>

| <span data-ttu-id="aa32e-163">**값**</span><span class="sxs-lookup"><span data-stu-id="aa32e-163">**Value**</span></span> | <span data-ttu-id="aa32e-164">**개체 형식**</span><span class="sxs-lookup"><span data-stu-id="aa32e-164">**Object Type**</span></span> |
|---------- | --------------- |
| <span data-ttu-id="aa32e-165">0</span><span class="sxs-lookup"><span data-stu-id="aa32e-165">0</span></span>         | <span data-ttu-id="aa32e-166">유효하지 않음</span><span class="sxs-lookup"><span data-stu-id="aa32e-166">Not Valid</span></span>       |
| <span data-ttu-id="aa32e-167">1</span><span class="sxs-lookup"><span data-stu-id="aa32e-167">1</span></span>         | <span data-ttu-id="aa32e-168">스레드</span><span class="sxs-lookup"><span data-stu-id="aa32e-168">Thread</span></span>          |
| <span data-ttu-id="aa32e-169">2</span><span class="sxs-lookup"><span data-stu-id="aa32e-169">2</span></span>         | <span data-ttu-id="aa32e-170">타이머</span><span class="sxs-lookup"><span data-stu-id="aa32e-170">Timer</span></span> |
| <span data-ttu-id="aa32e-171">3</span><span class="sxs-lookup"><span data-stu-id="aa32e-171">3</span></span>         | <span data-ttu-id="aa32e-172">큐</span><span class="sxs-lookup"><span data-stu-id="aa32e-172">Queue</span></span> |
| <span data-ttu-id="aa32e-173">4</span><span class="sxs-lookup"><span data-stu-id="aa32e-173">4</span></span>         | <span data-ttu-id="aa32e-174">세마포</span><span class="sxs-lookup"><span data-stu-id="aa32e-174">Semaphore</span></span> |
| <span data-ttu-id="aa32e-175">5</span><span class="sxs-lookup"><span data-stu-id="aa32e-175">5</span></span>         | <span data-ttu-id="aa32e-176">Mutex</span><span class="sxs-lookup"><span data-stu-id="aa32e-176">Mutex</span></span> |
| <span data-ttu-id="aa32e-177">6</span><span class="sxs-lookup"><span data-stu-id="aa32e-177">6</span></span>         | <span data-ttu-id="aa32e-178">이벤트 플래그 그룹</span><span class="sxs-lookup"><span data-stu-id="aa32e-178">Event Flags Group</span></span> |
| <span data-ttu-id="aa32e-179">7</span><span class="sxs-lookup"><span data-stu-id="aa32e-179">7</span></span>         | <span data-ttu-id="aa32e-180">블록 풀</span><span class="sxs-lookup"><span data-stu-id="aa32e-180">Block Pool</span></span> |
| <span data-ttu-id="aa32e-181">8</span><span class="sxs-lookup"><span data-stu-id="aa32e-181">8</span></span>         | <span data-ttu-id="aa32e-182">바이트 풀</span><span class="sxs-lookup"><span data-stu-id="aa32e-182">Byte Pool</span></span> |
| <span data-ttu-id="aa32e-183">9</span><span class="sxs-lookup"><span data-stu-id="aa32e-183">9</span></span>         | <span data-ttu-id="aa32e-184">../media</span><span class="sxs-lookup"><span data-stu-id="aa32e-184">../media</span></span> |
| <span data-ttu-id="aa32e-185">10</span><span class="sxs-lookup"><span data-stu-id="aa32e-185">10</span></span>        | <span data-ttu-id="aa32e-186">파일</span><span class="sxs-lookup"><span data-stu-id="aa32e-186">File</span></span> |
| <span data-ttu-id="aa32e-187">11</span><span class="sxs-lookup"><span data-stu-id="aa32e-187">11</span></span>        | <span data-ttu-id="aa32e-188">IP</span><span class="sxs-lookup"><span data-stu-id="aa32e-188">IP</span></span> |
| <span data-ttu-id="aa32e-189">12</span><span class="sxs-lookup"><span data-stu-id="aa32e-189">12</span></span>        | <span data-ttu-id="aa32e-190">패킷 풀</span><span class="sxs-lookup"><span data-stu-id="aa32e-190">Packet Pool</span></span> |
| <span data-ttu-id="aa32e-191">13</span><span class="sxs-lookup"><span data-stu-id="aa32e-191">13</span></span>        | <span data-ttu-id="aa32e-192">TCP 소켓</span><span class="sxs-lookup"><span data-stu-id="aa32e-192">TCP Socket</span></span> |
| <span data-ttu-id="aa32e-193">14</span><span class="sxs-lookup"><span data-stu-id="aa32e-193">14</span></span>        | <span data-ttu-id="aa32e-194">UDP 소켓</span><span class="sxs-lookup"><span data-stu-id="aa32e-194">UDP Socket</span></span> |
| <span data-ttu-id="aa32e-195">15-20</span><span class="sxs-lookup"><span data-stu-id="aa32e-195">15-20</span></span>     | <span data-ttu-id="aa32e-196">예약됨</span><span class="sxs-lookup"><span data-stu-id="aa32e-196">Reserved</span></span> |  
| <span data-ttu-id="aa32e-197">21</span><span class="sxs-lookup"><span data-stu-id="aa32e-197">21</span></span>        | <span data-ttu-id="aa32e-198">USB 호스트 스택 디바이스</span><span class="sxs-lookup"><span data-stu-id="aa32e-198">USB Host Stack Device</span></span> |
| <span data-ttu-id="aa32e-199">22</span><span class="sxs-lookup"><span data-stu-id="aa32e-199">22</span></span>        | <span data-ttu-id="aa32e-200">USB 호스트 스택 인터페이스</span><span class="sxs-lookup"><span data-stu-id="aa32e-200">USB Host Stack Interface</span></span> |
| <span data-ttu-id="aa32e-201">23</span><span class="sxs-lookup"><span data-stu-id="aa32e-201">23</span></span>        | <span data-ttu-id="aa32e-202">USB 호스트 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="aa32e-202">USB Host Endpoint</span></span> |
| <span data-ttu-id="aa32e-203">24</span><span class="sxs-lookup"><span data-stu-id="aa32e-203">24</span></span>        | <span data-ttu-id="aa32e-204">USB 호스트 클래스</span><span class="sxs-lookup"><span data-stu-id="aa32e-204">USB Host Class</span></span> |
| <span data-ttu-id="aa32e-205">25</span><span class="sxs-lookup"><span data-stu-id="aa32e-205">25</span></span>        | <span data-ttu-id="aa32e-206">USB 디바이스</span><span class="sxs-lookup"><span data-stu-id="aa32e-206">USB Device</span></span> |
| <span data-ttu-id="aa32e-207">26</span><span class="sxs-lookup"><span data-stu-id="aa32e-207">26</span></span>        | <span data-ttu-id="aa32e-208">USB 디바이스 인터페이스</span><span class="sxs-lookup"><span data-stu-id="aa32e-208">USB Device Interface</span></span> |
| <span data-ttu-id="aa32e-209">27</span><span class="sxs-lookup"><span data-stu-id="aa32e-209">27</span></span>        | <span data-ttu-id="aa32e-210">USB 디바이스 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="aa32e-210">USB Device Endpoint</span></span> |
| <span data-ttu-id="aa32e-211">28</span><span class="sxs-lookup"><span data-stu-id="aa32e-211">28</span></span>        | <span data-ttu-id="aa32e-212">USB 디바이스 클래스</span><span class="sxs-lookup"><span data-stu-id="aa32e-212">USB Device Class</span></span> |

### <a name="object-pointer"></a><span data-ttu-id="aa32e-213">개체 포인터</span><span class="sxs-lookup"><span data-stu-id="aa32e-213">Object Pointer</span></span>

<span data-ttu-id="aa32e-214">개체 포인터는 ThreadX API를 사용하여 개체에 액세스하는 데 사용되는 개체 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-214">The object pointer specifies the object address that is used for accessing the object using the ThreadX API.</span></span>

### <a name="object-reserved-fields"></a><span data-ttu-id="aa32e-215">개체 예약 필드</span><span class="sxs-lookup"><span data-stu-id="aa32e-215">Object Reserved Fields</span></span>

<span data-ttu-id="aa32e-216">스레드 이외의 모든 개체의 경우, 이러한 예약된 필드는 0이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-216">For all objects other than threads, these reserved fields should be 0.</span></span> <span data-ttu-id="aa32e-217">스레드의 경우, 레지스트리에 입력될 때 스레드의 우선 순위는 이러한 두 개의 예약된 필드에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-217">For threads, the priority of the thread at the time it is entered into the registry is placed in these two reserved fields.</span></span>

### <a name="object-parameters"></a><span data-ttu-id="aa32e-218">개체 매개 변수</span><span class="sxs-lookup"><span data-stu-id="aa32e-218">Object Parameters</span></span>

<span data-ttu-id="aa32e-219">개체 매개 변수는 개체에 대한 추가 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-219">The object parameters contain supplemental information about the object.</span></span> <span data-ttu-id="aa32e-220">다음은 각 ThreadX 개체에 대한 추가 정보를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-220">The following describes the supplemental information for each ThreadX object:</span></span>

| <span data-ttu-id="aa32e-221">**개체 형식**</span><span class="sxs-lookup"><span data-stu-id="aa32e-221">**Object Type**</span></span>        | <span data-ttu-id="aa32e-222">**매개 변수 1**</span><span class="sxs-lookup"><span data-stu-id="aa32e-222">**Parameter 1**</span></span>  | <span data-ttu-id="aa32e-223">**매개 변수 2**</span><span class="sxs-lookup"><span data-stu-id="aa32e-223">**Parameter 2**</span></span> |
|----------------------- | ---------------- | --------------- |
| <span data-ttu-id="aa32e-224">스레드</span><span class="sxs-lookup"><span data-stu-id="aa32e-224">Thread</span></span>                 | <span data-ttu-id="aa32e-225">스택 시작</span><span class="sxs-lookup"><span data-stu-id="aa32e-225">Stack Start</span></span>      | <span data-ttu-id="aa32e-226">스택 크기</span><span class="sxs-lookup"><span data-stu-id="aa32e-226">Stack Size</span></span> |
| <span data-ttu-id="aa32e-227">타이머</span><span class="sxs-lookup"><span data-stu-id="aa32e-227">Timer</span></span>                  | <span data-ttu-id="aa32e-228">초기 틱</span><span class="sxs-lookup"><span data-stu-id="aa32e-228">Initial Ticks</span></span> | <span data-ttu-id="aa32e-229">틱 다시 예약</span><span class="sxs-lookup"><span data-stu-id="aa32e-229">Reschedule Ticks</span></span> |
| <span data-ttu-id="aa32e-230">큐</span><span class="sxs-lookup"><span data-stu-id="aa32e-230">Queue</span></span>                  | <span data-ttu-id="aa32e-231">큐 크기</span><span class="sxs-lookup"><span data-stu-id="aa32e-231">Queue Size</span></span> | <span data-ttu-id="aa32e-232">메시지 크기</span><span class="sxs-lookup"><span data-stu-id="aa32e-232">Message Size</span></span> |
| <span data-ttu-id="aa32e-233">세마포</span><span class="sxs-lookup"><span data-stu-id="aa32e-233">Semaphore</span></span>              | <span data-ttu-id="aa32e-234">초기 인스턴스</span><span class="sxs-lookup"><span data-stu-id="aa32e-234">Initial Instances</span></span> | - |
| <span data-ttu-id="aa32e-235">Mutex</span><span class="sxs-lookup"><span data-stu-id="aa32e-235">Mutex</span></span>                  | <span data-ttu-id="aa32e-236">상속 플래그</span><span class="sxs-lookup"><span data-stu-id="aa32e-236">Inheritance Flag</span></span> | - |
| <span data-ttu-id="aa32e-237">이벤트 플래그 그룹</span><span class="sxs-lookup"><span data-stu-id="aa32e-237">Event Flags Group</span></span>      | - | - |
| <span data-ttu-id="aa32e-238">블록 풀</span><span class="sxs-lookup"><span data-stu-id="aa32e-238">Block Pool</span></span>             | <span data-ttu-id="aa32e-239">총 블록</span><span class="sxs-lookup"><span data-stu-id="aa32e-239">Total Blocks</span></span> | <span data-ttu-id="aa32e-240">블록 크기</span><span class="sxs-lookup"><span data-stu-id="aa32e-240">Block Size</span></span> |
| <span data-ttu-id="aa32e-241">바이트 풀</span><span class="sxs-lookup"><span data-stu-id="aa32e-241">Byte Pool</span></span>              | <span data-ttu-id="aa32e-242">총 바이트</span><span class="sxs-lookup"><span data-stu-id="aa32e-242">Total Bytes</span></span> | - |
| <span data-ttu-id="aa32e-243">../media</span><span class="sxs-lookup"><span data-stu-id="aa32e-243">../media</span></span>                  | <span data-ttu-id="aa32e-244">Fat 캐시 크기</span><span class="sxs-lookup"><span data-stu-id="aa32e-244">Fat Cache Size</span></span> | <span data-ttu-id="aa32e-245">섹터 캐시 크기</span><span class="sxs-lookup"><span data-stu-id="aa32e-245">Sector Cache Size</span></span> |
| <span data-ttu-id="aa32e-246">파일</span><span class="sxs-lookup"><span data-stu-id="aa32e-246">File</span></span>                   | - | - |
| <span data-ttu-id="aa32e-247">IP</span><span class="sxs-lookup"><span data-stu-id="aa32e-247">IP</span></span>                     | <span data-ttu-id="aa32e-248">스택 시작</span><span class="sxs-lookup"><span data-stu-id="aa32e-248">Stack Start</span></span> | <span data-ttu-id="aa32e-249">스택 크기</span><span class="sxs-lookup"><span data-stu-id="aa32e-249">Stack Size</span></span> |
| <span data-ttu-id="aa32e-250">패킷 풀</span><span class="sxs-lookup"><span data-stu-id="aa32e-250">Packet Pool</span></span>            | <span data-ttu-id="aa32e-251">패킷 크기</span><span class="sxs-lookup"><span data-stu-id="aa32e-251">Packet Size</span></span> | <span data-ttu-id="aa32e-252">패킷 수</span><span class="sxs-lookup"><span data-stu-id="aa32e-252">Number of Packets</span></span> |
| <span data-ttu-id="aa32e-253">TCP 소켓</span><span class="sxs-lookup"><span data-stu-id="aa32e-253">TCP Socket</span></span>             | <span data-ttu-id="aa32e-254">IP 주소</span><span class="sxs-lookup"><span data-stu-id="aa32e-254">IP address</span></span> | <span data-ttu-id="aa32e-255">창 크기</span><span class="sxs-lookup"><span data-stu-id="aa32e-255">Window Size</span></span> |
| <span data-ttu-id="aa32e-256">UDP 소켓</span><span class="sxs-lookup"><span data-stu-id="aa32e-256">UDP Socket</span></span>             | <span data-ttu-id="aa32e-257">IP 주소</span><span class="sxs-lookup"><span data-stu-id="aa32e-257">IP address</span></span> | <span data-ttu-id="aa32e-258">RX 큐 최대값</span><span class="sxs-lookup"><span data-stu-id="aa32e-258">RX Queue Max</span></span> |

### <a name="object-name"></a><span data-ttu-id="aa32e-259">개체 이름</span><span class="sxs-lookup"><span data-stu-id="aa32e-259">Object Name</span></span>

<span data-ttu-id="aa32e-260">개체 이름에는 ThreadX 개체의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-260">The object name contains the name of the ThreadX object.</span></span> <span data-ttu-id="aa32e-261">이 이름은 개체가 생성될 때 ThreadX에 제공되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-261">The name is the name provided to ThreadX at the time the object was created.</span></span> <span data-ttu-id="aa32e-262">기본적으로 개체 이름의 최대 크기는 32자입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-262">By default, the object name has a maximum of 32 characters.</span></span> <span data-ttu-id="aa32e-263">32자를 초과하는 실제 이름은 일부가 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-263">Actual names greater than 32 characters are truncated.</span></span>

## <a name="event-trace-entries"></a><span data-ttu-id="aa32e-264">이벤트 추적 항목</span><span class="sxs-lookup"><span data-stu-id="aa32e-264">Event Trace Entries</span></span>

<span data-ttu-id="aa32e-265">이벤트 추적 항목은 이벤트 추적 버퍼의 하단에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-265">The event trace entries are found in the bottom portion of the event trace buffer.</span></span> <span data-ttu-id="aa32e-266">항목은 현재 항목 포인터가 가장 오래된 항목을 가리키는 순환 목록으로 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-266">The entries are maintained in a circular list, with the current entry pointer pointing to the oldest entry.</span></span> <span data-ttu-id="aa32e-267">목록의 항목 수는 ***tx_trace_enable*** 호출로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-267">The number of entries in the list is calculated by the ***tx_trace_enable*** call.</span></span>

<span data-ttu-id="aa32e-268">각 개체 등록 항목에는 특정 ThreadX 추적 이벤트에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-268">Each object register entry contains information about a specific ThreadX trace event.</span></span> <span data-ttu-id="aa32e-269">다음 데이터 구조는 각 추적 이벤트 항목을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-269">The following data structure defines each trace event entry:</span></span>

```c
typedef struct TX_TRACE_BUFFER_ENTRY_STRUCT
{
    ULONG     tx_trace_buffer_entry_thread_pointer;
    ULONG     tx_trace_buffer_entry_thread_priority;
    ULONG     tx_trace_buffer_entry_event_id;
    ULONG     tx_trace_buffer_entry_time_stamp;
    ULONG     tx_trace_buffer_entry_information_field_1;
    ULONG     tx_trace_buffer_entry_information_field_2;
    ULONG     tx_trace_buffer_entry_information_field_3;
    ULONG     tx_trace_buffer_entry_information_field_4;
} TX_TRACE_BUFFER_ENTRY;
```

### <a name="thread-pointer"></a><span data-ttu-id="aa32e-270">스레드 포인터</span><span class="sxs-lookup"><span data-stu-id="aa32e-270">Thread Pointer</span></span>

<span data-ttu-id="aa32e-271">스레드 포인터는 이 이벤트가 발생했을 때 실행되는 스레드의 주소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-271">The thread pointer contains the address of the thread running at the time of this event.</span></span> <span data-ttu-id="aa32e-272">초기화 중에 이벤트가 발생한 경우(실행 중인 스레드 없음) 이 포인터의 값은 0xF0F0F0F0입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-272">If the event occurred during initialization (no thread running), the value of this pointer is 0xF0F0F0F0.</span></span> <span data-ttu-id="aa32e-273">ISR(인터럽트 서비스 루틴) 중에 이벤트가 발생한 경우 이 포인터의 값은 0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-273">If the event occurred during an Interrupt Service Routine (ISR), the value of this pointer is 0xFFFFFFFF.</span></span> <span data-ttu-id="aa32e-274">항목을 아직 사용하지 않은 경우 이 포인터의 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-274">If the entry has not yet been used, the value of this pointer is 0.</span></span>

### <a name="thread-priority"></a><span data-ttu-id="aa32e-275">스레드 우선 순위</span><span class="sxs-lookup"><span data-stu-id="aa32e-275">Thread Priority</span></span>

<span data-ttu-id="aa32e-276">스레드 우선 순위 필드에는 이 이벤트가 발생했을 때 실행 중이던 스레드의 우선 순위 및 선점 임계값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-276">The thread priority field contains the thread priority and preemption-threshold of the thread that was running at the time of this event.</span></span> <span data-ttu-id="aa32e-277">인터럽트 컨텍스트가 있는 경우(스레드 포인터는 0xFFFFFFFF) 이 필드의 값은 우선 순위가 아닌, 이벤트 시점의 ***_tx_thread_current_ptr*** 값입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-277">If an interrupt context is present (thread pointer is 0xFFFFFFFF), the value of this field is not the priority but instead the value of ***_tx_thread_current_ptr*** at the time of the event.</span></span> <span data-ttu-id="aa32e-278">그렇지 않은 경우, 이 필드의 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-278">Otherwise, the value of this field is 0.</span></span>

### <a name="event-id"></a><span data-ttu-id="aa32e-279">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="aa32e-279">Event ID</span></span>

<span data-ttu-id="aa32e-280">이벤트 ID는 발생한 이벤트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-280">The event ID specifies the event that took place.</span></span> <span data-ttu-id="aa32e-281">유효한 ThreadX 추적 이벤트 ID의 범위는 1~1024입니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-281">Valid ThreadX trace event IDs range from 1 through 1024.</span></span> <span data-ttu-id="aa32e-282">1025 이상으로 시작되는 값은 사용자별 이벤트용으로 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-282">Values starting at 1025 and above are reserved for user-specific events.</span></span> <span data-ttu-id="aa32e-283">ThreadX 이벤트ID의 전체 정의는 ***tx_trace.h*** 파일을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa32e-283">Please refer to the ***tx_trace.h*** file for the complete definition of ThreadX event IDs.</span></span></td>

### <a name="information-fields-1-4"></a><span data-ttu-id="aa32e-284">정보 필드(1~4)</span><span class="sxs-lookup"><span data-stu-id="aa32e-284">Information Fields (1-4)</span></span>

<span data-ttu-id="aa32e-285">정보 필드는 특정 이벤트에 대한 추가 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="aa32e-285">The information fields contain additional information about the specific event.</span></span> <span data-ttu-id="aa32e-286">정의된 각 ThreadX 이벤트 ID에 대한 정보 필드의 전체 설명은 ***tx_trace.h*** 파일을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa32e-286">Please refer to the ***tx_trace.h*** file for the complete description of the information fields for each of the defined ThreadX event IDs.</span></span>