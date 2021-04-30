---
title: 챕터 5 - Azure RTOS ThreadX용 디바이스 드라이버
description: 이 챕터에서는 Azure RTOS ThreadX의 디바이스 드라이버에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2432b291f2b3fa7d6d798b8b4c187dd20b97db6b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812174"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx"></a><span data-ttu-id="4533f-103">챕터 5 - Azure RTOS ThreadX용 디바이스 드라이버</span><span class="sxs-lookup"><span data-stu-id="4533f-103">Chapter 5 - Device Drivers for Azure RTOS ThreadX</span></span>

<span data-ttu-id="4533f-104">이 챕터에서는 Azure RTOS ThreadX의 디바이스 드라이버에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-104">This chapter contains a description of device drivers for Azure RTOS ThreadX.</span></span> <span data-ttu-id="4533f-105">이 챕터에 제시된 정보는 개발자가 애플리케이션별 드라이버를 작성하는 데 도움이 되도록 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-105">The information presented in this chapter is designed to help developers write application-specific drivers.</span></span>

## <a name="device-driver-introduction"></a><span data-ttu-id="4533f-106">디바이스 드라이버 소개</span><span class="sxs-lookup"><span data-stu-id="4533f-106">Device Driver Introduction</span></span>

<span data-ttu-id="4533f-107">외부 환경과의 통신은 대부분의 임베디드 애플리케이션의 중요한 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-107">Communication with the external environment is an important component of most embedded applications.</span></span> <span data-ttu-id="4533f-108">이 통신은 임베디드 애플리케이션 소프트웨어에 액세스할 수 있는 하드웨어 디바이스를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-108">This communication is accomplished through hardware devices that are accessible to the embedded application software.</span></span> <span data-ttu-id="4533f-109">이러한 디바이스를 관리하는 소프트웨어 구성 요소를 일반적으로 *디바이스 드라이버* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-109">The software components responsible for managing such devices are commonly called *device drivers*.</span></span>

<span data-ttu-id="4533f-110">임베디드 실시간 시스템의 디바이스 드라이버는 본질적으로 애플리케이션에 의존합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-110">Device drivers in embedded, real-time systems are inherently application dependent.</span></span> <span data-ttu-id="4533f-111">이는 두 가지 주요 이유, 즉 대상 하드웨어의 다양함과 실시간 애플리케이션에 부과되는 동일한 성능 요구 사항 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-111">This is true for two principal reasons: the vast diversity of target hardware and the equally vast performance requirements imposed on real-time applications.</span></span> <span data-ttu-id="4533f-112">따라서 모든 애플리케이션의 요구 사항을 충족하는 공통 드라이버 세트를 제공하는 것은 사실상 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-112">Because of this, it is virtually impossible to provide a common set of drivers that will meet the requirements of every application.</span></span> <span data-ttu-id="4533f-113">이러한 이유로 이 챕터의 정보는 사용자가 *기성 제품* ThreadX 디바이스 드라이버를 사용자 정의하고 고유한 특정 드라이버를 작성하는 데 도움이 되도록 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-113">For these reasons, the information in this chapter is designed to help users customize *off-the-shelf* ThreadX device drivers and write their own specific drivers.</span></span>

## <a name="driver-functions"></a><span data-ttu-id="4533f-114">드라이버 함수</span><span class="sxs-lookup"><span data-stu-id="4533f-114">Driver Functions</span></span>

<span data-ttu-id="4533f-115">ThreadX 디바이스 드라이버는 다음과 같은 8가지 기본 기능 영역으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-115">ThreadX device drivers are composed of eight basic functional areas, as follows.</span></span>

- <span data-ttu-id="4533f-116">**드라이버 초기화**</span><span class="sxs-lookup"><span data-stu-id="4533f-116">**Driver Initialization**</span></span>
- <span data-ttu-id="4533f-117">**드라이버 컨트롤**</span><span class="sxs-lookup"><span data-stu-id="4533f-117">**Driver Control**</span></span>
- <span data-ttu-id="4533f-118">**드라이버 액세스**</span><span class="sxs-lookup"><span data-stu-id="4533f-118">**Driver Access**</span></span>
- <span data-ttu-id="4533f-119">**드라이버 입력**</span><span class="sxs-lookup"><span data-stu-id="4533f-119">**Driver Input**</span></span>
- <span data-ttu-id="4533f-120">**드라이버 출력**</span><span class="sxs-lookup"><span data-stu-id="4533f-120">**Driver Output**</span></span>
- <span data-ttu-id="4533f-121">**드라이버 인터럽트**</span><span class="sxs-lookup"><span data-stu-id="4533f-121">**Driver Interrupts**</span></span>
- <span data-ttu-id="4533f-122">**드라이버 상태**</span><span class="sxs-lookup"><span data-stu-id="4533f-122">**Driver Status**</span></span>
- <span data-ttu-id="4533f-123">**드라이버 종료**</span><span class="sxs-lookup"><span data-stu-id="4533f-123">**Driver Termination**</span></span>

<span data-ttu-id="4533f-124">초기화를 제외하고 각 드라이버 기능 영역은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-124">With the exception of initialization, each driver functional area is optional.</span></span> <span data-ttu-id="4533f-125">또한 각 영역의 정확한 처리 과정은 디바이스 드라이버에만 한정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-125">Furthermore, the exact processing in each area is specific to the device driver.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="4533f-126">드라이버 초기화</span><span class="sxs-lookup"><span data-stu-id="4533f-126">Driver Initialization</span></span>
<span data-ttu-id="4533f-127">이 기능 영역은 실제 하드웨어 디바이스 및 드라이버의 내부 데이터 구조를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-127">This functional area is responsible for initialization of the actual hardware device and the internal data structures of the driver.</span></span> <span data-ttu-id="4533f-128">초기화가 완료될 때까지 다른 드라이버 서비스를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-128">Calling other driver services is not allowed until initialization is complete.</span></span>

> [!NOTE]
> <span data-ttu-id="4533f-129">\*드라이버의 초기화 함수 구성 요소는 일반적으로 \***tx_application_define** _ 함수 또는 초기화 스레드에서 호출됩니다._</span><span class="sxs-lookup"><span data-stu-id="4533f-129">\*The driver's initialization function component is typically called from the \***tx_application_define** _ function or from an initialization thread._</span></span>

### <a name="driver-control"></a><span data-ttu-id="4533f-130">드라이버 컨트롤</span><span class="sxs-lookup"><span data-stu-id="4533f-130">Driver Control</span></span>

<span data-ttu-id="4533f-131">드라이버가 초기화되고 작동 준비가 완료되면 이 기능 영역이 런타임 제어를 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-131">After the driver is initialized and ready for operation, this functional area is responsible for run-time control.</span></span> <span data-ttu-id="4533f-132">일반적으로 런타임 제어는 기본 하드웨어 디바이스를 변경하는 것으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-132">Typically, run-time control consists of making changes to the underlying hardware device.</span></span> <span data-ttu-id="4533f-133">예를 들어 직렬 디바이스의 전송 속도를 변경하거나 디스크에서 새 섹터를 찾는 것이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-133">Examples include changing the baud rate of a serial device or seeking a new sector on a disk.</span></span>

### <a name="driver-access"></a><span data-ttu-id="4533f-134">드라이버 액세스</span><span class="sxs-lookup"><span data-stu-id="4533f-134">Driver Access</span></span>

<span data-ttu-id="4533f-135">일부 디바이스 드라이버는 단일 애플리케이션 스레드에서만 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-135">Some device drivers are called only from a single application thread.</span></span> <span data-ttu-id="4533f-136">이 경우 이 함수 영역은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-136">In such cases, this functional area is not needed.</span></span> <span data-ttu-id="4533f-137">그러나 여러 스레드가 동시에 드라이버에 액세스해야 하는 애플리케이션에서는 디바이스 드라이버에 할당/릴리스 기능을 추가하여 상호 작용을 제어해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-137">However, in applications where multiple threads need simultaneous driver access, their interaction must be controlled by adding assign/ release facilities in the device driver.</span></span> <span data-ttu-id="4533f-138">또는 애플리케이션이 세마포를 사용하여 드라이버의 접근을 제어하고 드라이버 내부의 추가적인 오버헤드 및 복잡성을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-138">Alternatively, the application may use a semaphore to control driver access and avoid extra overhead and complication inside the driver.</span></span>

### <a name="driver-input"></a><span data-ttu-id="4533f-139">드라이버 입력</span><span class="sxs-lookup"><span data-stu-id="4533f-139">Driver Input</span></span>

<span data-ttu-id="4533f-140">이 기능 영역은 모든 디바이스 입력을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-140">This functional area is responsible for all device input.</span></span> <span data-ttu-id="4533f-141">드라이버 입력과 관련된 주요 문제는 일반적으로 입력이 버퍼링되는 방식과 스레드가 이러한 입력을 기다리는 방식과 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-141">The principal issues associated with driver input usually involve how the input is buffered and how threads wait for such input.</span></span>

### <a name="driver-output"></a><span data-ttu-id="4533f-142">드라이버 출력</span><span class="sxs-lookup"><span data-stu-id="4533f-142">Driver Output</span></span>

<span data-ttu-id="4533f-143">이 기능 영역은 모든 디바이스 출력을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-143">This functional area is responsible for all device output.</span></span> <span data-ttu-id="4533f-144">드라이버 출력과 관련된 주요 문제는 일반적으로 출력이 버퍼링되는 방식과 스레드가 출력을 수행하기 위해 기다리는 방식과 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-144">The principal issues associated with driver output usually involve how the output is buffered and how threads wait to perform output.</span></span>

### <a name="driver-interrupts"></a><span data-ttu-id="4533f-145">드라이버 인터럽트</span><span class="sxs-lookup"><span data-stu-id="4533f-145">Driver Interrupts</span></span>

<span data-ttu-id="4533f-146">대부분의 실시간 시스템은 디바이스 입력, 출력, 제어 및 오류 이벤트를 드라이버에 알리기 위해 하드웨어 인터럽트에 의존합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-146">Most real-time systems rely on hardware interrupts to notify the driver of device input, output, control, and error events.</span></span> <span data-ttu-id="4533f-147">인터럽트는 이러한 외부 이벤트에 대해 보장된 응답 시간을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-147">Interrupts provide a guaranteed response time to such external events.</span></span> <span data-ttu-id="4533f-148">인터럽트 대신 드라이버 소프트웨어는 이러한 이벤트에 대해 외부 하드웨어를 주기적으로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-148">Instead of interrupts, the driver software may periodically check the external hardware for such events.</span></span> <span data-ttu-id="4533f-149">이러한 기술을 *폴링* 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-149">This technique is called *polling*.</span></span> <span data-ttu-id="4533f-150">인터럽트보다 덜 실시간이지만 일부 덜 실시간 애플리케이션에서는 폴링이 적합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-150">It is less real-time than interrupts, but polling may make sense for some less real-time applications.</span></span>

### <a name="driver-status"></a><span data-ttu-id="4533f-151">드라이버 상태</span><span class="sxs-lookup"><span data-stu-id="4533f-151">Driver Status</span></span>

<span data-ttu-id="4533f-152">이 함수 영역은 드라이버 작업과 관련된 런타임 상태와 통계를 제공하는 일을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-152">This function area is responsible for providing run-time status and statistics associated with the driver operation.</span></span> <span data-ttu-id="4533f-153">이 함수 영역에서 관리하는 정보에는 일반적으로 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-153">Information managed by this function area typically includes the following.</span></span>

- <span data-ttu-id="4533f-154">현재 디바이스 상태</span><span class="sxs-lookup"><span data-stu-id="4533f-154">Current device status</span></span>
- <span data-ttu-id="4533f-155">입력 바이트</span><span class="sxs-lookup"><span data-stu-id="4533f-155">Input bytes</span></span>
- <span data-ttu-id="4533f-156">출력 바이트</span><span class="sxs-lookup"><span data-stu-id="4533f-156">Output bytes</span></span>
- <span data-ttu-id="4533f-157">디바이스 오류 개수</span><span class="sxs-lookup"><span data-stu-id="4533f-157">Device error counts</span></span>

### <a name="driver-termination"></a><span data-ttu-id="4533f-158">드라이버 종료</span><span class="sxs-lookup"><span data-stu-id="4533f-158">Driver Termination</span></span>

<span data-ttu-id="4533f-159">이 기능 영역은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-159">This functional area is optional.</span></span> <span data-ttu-id="4533f-160">드라이버 및/또는 물리적 하드웨어 디바이스를 종료해야 하는 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-160">It is only required if the driver and/or the physical hardware device need to be shut down.</span></span> <span data-ttu-id="4533f-161">종료된 후에는 다시 초기화될 때까지 드라이버를 다시 호출하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-161">After being terminated, the driver must not be called again until it is reinitialized.</span></span>

## <a name="simple-driver-example"></a><span data-ttu-id="4533f-162">단순 드라이버 예</span><span class="sxs-lookup"><span data-stu-id="4533f-162">Simple Driver Example</span></span>

<span data-ttu-id="4533f-163">예는 디바이스 드라이버를 설명하는 가장 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-163">An example is the best way to describe a device driver.</span></span> <span data-ttu-id="4533f-164">이 예에서 드라이버는 구성 레지스터, 입력 레지스터 및 출력 레지스터가 있는 간단한 직렬 하드웨어 디바이스를 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-164">In this example, the driver assumes a simple serial hardware device with a configuration register, an input register, and an output register.</span></span> <span data-ttu-id="4533f-165">이 간단한 드라이버 예는 초기화, 입력, 출력 및 인터럽트 기능 영역을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-165">This simple driver example illustrates the initialization, input, output, and interrupt functional areas.</span></span>

### <a name="simple-driver-initialization"></a><span data-ttu-id="4533f-166">단순 드라이버 초기화</span><span class="sxs-lookup"><span data-stu-id="4533f-166">Simple Driver Initialization</span></span>

<span data-ttu-id="4533f-167">단순 드라이버의 ***tx_sdriver_initialize*** 함수는 드라이버의 입력 및 출력 작업을 관리하는 데 사용되는 두 개의 카운트 세마포를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-167">The ***tx_sdriver_initialize*** function of the simple driver creates two counting semaphores that are used to manage the driver's input and output operation.</span></span> <span data-ttu-id="4533f-168">입력 세마포는 직렬 하드웨어 디바이스에서 문자를 수신할 때 입력 ISR에 의해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-168">The input semaphore is set by the input ISR when a character is received by the serial hardware device.</span></span> <span data-ttu-id="4533f-169">이 때문에 입력 세마포는 초기 카운트가 0인 상태로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-169">Because of this, the input semaphore is created with an initial count of zero.</span></span>

<span data-ttu-id="4533f-170">반대로 출력 세마포는 직렬 하드웨어 전송 레지스터의 가용성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-170">Conversely, the output semaphore indicates the availability of the serial hardware transmit register.</span></span> <span data-ttu-id="4533f-171">전송 레지스터가 처음에 사용 가능함을 나타내기 위해 값 1로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-171">It is created with a value of one to indicate the transmit register is initially available.</span></span>

<span data-ttu-id="4533f-172">초기화 함수는 또한 입력 및 출력 알림을 위한 하위 수준의 인터럽트 벡터 처리기 설치를 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-172">The initialization function is also responsible for installing the low-level interrupt vector handlers for input and output notifications.</span></span> <span data-ttu-id="4533f-173">다른 ThreadX 인터럽트 서비스 루틴과 마찬가지로, 단순 드라이버 ISR을 호출하기 전에 하위 수준의 처리기가 \* **_tx_thread_context_save** _를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-173">Like other ThreadX interrupt service routines, the low-level handler must call \***_tx_thread_context_save** _ before calling the simple driver ISR.</span></span> <span data-ttu-id="4533f-174">드라이버 ISR이 반환된 후 하위 수준 처리기는 _\*_ _tx_thread_context_restore_\*\*를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-174">After the driver ISR returns, the low-level handler must call _\*_ _tx_thread_context_restore_\*\*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4533f-175">\* 다른 드라이버 함수보다 먼저 초기화가 호출되는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-175">\*It is important that initialization is called before any of the other driver functions.</span></span> <span data-ttu-id="4533f-176">일반적으로 드라이버 초기화는 ***tx_application_define*** 에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-176">Typically, driver initialization is called from ***tx_application_define***.</span></span>

```c
VOID tx_sdriver_initialize(VOID)
{
    /* Initialize the two counting semaphores used to control
    the simple driver I/O. */
    tx_semaphore_create(&tx_sdriver_input_semaphore,
                        "simple driver input semaphore", 0);
    tx_semaphore_create(&tx_sdriver_output_semaphore,
                        "simple driver output semaphore", 1);

    /* Setup interrupt vectors for input and output ISRs.
    The initial vector handling should call the ISRs
    defined in this file. */

    /* Configure serial device hardware for RX/TX interrupt
    generation, baud rate, stop bits, etc. */
}
```
<span data-ttu-id="4533f-177">**그림 9. 단순 드라이버 초기화**</span><span class="sxs-lookup"><span data-stu-id="4533f-177">**FIGURE 9. Simple Driver Initialization**</span></span>

### <a name="simple-driver-input"></a><span data-ttu-id="4533f-178">단순 드라이버 입력</span><span class="sxs-lookup"><span data-stu-id="4533f-178">Simple Driver Input</span></span>

<span data-ttu-id="4533f-179">단순 드라이버에 대한 입력은 입력 세마포를 중심으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-179">Input for the simple driver centers around the input semaphore.</span></span> <span data-ttu-id="4533f-180">직렬 디바이스 입력 인터럽트가 수신되면 입력 세마포가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-180">When a serial device input interrupt is received, the input semaphore is set.</span></span> <span data-ttu-id="4533f-181">하나 이상의 스레드가 드라이버의 문자를 기다리고 있는 경우 가장 오래 대기 중인 스레드가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-181">If one or more threads are waiting for a character from the driver, the thread waiting the longest is resumed.</span></span> <span data-ttu-id="4533f-182">대기 중인 스레드가 없으면 스레드가 드라이브 입력 함수를 호출할 때까지 세마포가 설정된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-182">If no threads are waiting, the semaphore simply remains set until a thread calls the drive input function.</span></span>

<span data-ttu-id="4533f-183">단순 드라이버 입력 처리에는 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-183">There are several limitations to the simple driver input handling.</span></span> <span data-ttu-id="4533f-184">가장 중요한 것은 입력 문자를 삭제될 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-184">The most significant is the potential for dropping input characters.</span></span> <span data-ttu-id="4533f-185">이는 이전 문자가 처리되기 전에 도착한 입력 문자를 버퍼링하는 기능이 없기 때문에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-185">This is possible because there is no ability to buffer input characters that arrive before the previous character is processed.</span></span> <span data-ttu-id="4533f-186">이는 입력 문자 버퍼를 추가하여 쉽게 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-186">This is easily handled by adding an input character buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="4533f-187">*스레드만*  ***tx_sdriver_input** __ 함수를 호출할 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="4533f-187">*Only threads are allowed to call the* ***tx_sdriver_input** _ _function.*</span></span>

<span data-ttu-id="4533f-188">그림 10은 간단한 드라이버 입력과 관련된 소스 코드를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-188">Figure 10 shows the source code associated with simple driver input.</span></span>

```c
UCHAR tx_sdriver_input(VOID)
{
  /* Determine if there is a character waiting. If not,
  suspend. */
  tx_semaphore_get(&tx_sdriver_input_semaphore,
  TX_WAIT_FOREVER;

  /* Return character from serial RX hardware register. */
  return(*serial_hardware_input_ptr);
}
  VOID tx_sdriver_input_ISR(VOID)
{
  /* See if an input character notification is pending. */
  if (!tx_sdriver_input_semaphore.tx_semaphore_count)
  {
    /* If not, notify thread of an input character. */
    tx_semaphore_put(&tx_sdriver_input_semaphore);
  }
}
```
<span data-ttu-id="4533f-189">**그림 10. 단순 드라이버 입력**</span><span class="sxs-lookup"><span data-stu-id="4533f-189">**FIGURE 10. Simple Driver Input**</span></span>

### <a name="simple-driver-output"></a><span data-ttu-id="4533f-190">단순 드라이버 출력</span><span class="sxs-lookup"><span data-stu-id="4533f-190">Simple Driver Output</span></span>

<span data-ttu-id="4533f-191">출력 처리는 출력 세마포를 활용하여 직렬 디바이스의 송신 레지스터가 비어 있을 때 신호를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-191">Output processing utilizes the output semaphore to signal when the serial device's transmit register is free.</span></span> <span data-ttu-id="4533f-192">출력 문자를 디바이스에 실제로 기록되기 전에 출력 세마포를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-192">Before an output character is actually written to the device, the output semaphore is obtained.</span></span> <span data-ttu-id="4533f-193">이를 사용할 수 없는 경우 이전 전송이 아직 완료되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-193">If it is not available, the previous transmit is not yet complete.</span></span>

<span data-ttu-id="4533f-194">출력 ISR은 전송 완료 인터럽트 처리를 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-194">The output ISR is responsible for handling the transmit complete interrupt.</span></span> <span data-ttu-id="4533f-195">출력 ISR의 처리를 통해 출력 세마포를 설정하므로 다른 문자를 출력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-195">Processing of the output ISR amounts to setting the output semaphore, thereby allowing output of another character.</span></span>

> [!NOTE]
> <span data-ttu-id="4533f-196">*스레드만*  ***tx_sdriver_output** __ 함수를 호출할 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="4533f-196">*Only threads are allowed to call the* ***tx_sdriver_output** _ _function.*</span></span>

<span data-ttu-id="4533f-197">그림 11은 간단한 드라이버 출력과 관련된 소스 코드를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-197">Figure 11 shows the source code associated with simple driver output.</span></span>

```c
VOID tx_sdriver_output(UCHAR alpha)
{
  /* Determine if the hardware is ready to transmit a
  character. If not, suspend until the previous output
  completes. */
  tx_semaphore_get(&tx_sdriver_output_semaphore,
                                          TX_WAIT_FOREVER);

  /* Send the character through the hardware. */
  *serial_hardware_output_ptr = alpha;
}
  
VOID tx_sdriver_output_ISR(VOID)
{
  /* Notify thread last character transmit is
  complete. */
  tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
<span data-ttu-id="4533f-198">**그림 11. 단순 드라이버 출력**</span><span class="sxs-lookup"><span data-stu-id="4533f-198">**FIGURE 11. Simple Driver Output**</span></span>

### <a name="simple-driver-shortcomings"></a><span data-ttu-id="4533f-199">단순 드라이버 단점</span><span class="sxs-lookup"><span data-stu-id="4533f-199">Simple Driver Shortcomings</span></span>

<span data-ttu-id="4533f-200">이러한 단순 디바이스 드라이버 예에서는 ThreadX 디바이스 드라이버의 기본 개념을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-200">This simple device driver example illustrates the basic idea of a ThreadX device driver.</span></span> <span data-ttu-id="4533f-201">그러나 단순 디바이스 드라이버는 데이터 버퍼링 또는 오버헤드 문제를 해결하지 않으므로 실제 ThreadX 드라이버를 완전히 보여주지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-201">However, because the simple device driver does not address data buffering or any overhead issues, it does not fully represent real-world ThreadX drivers.</span></span> <span data-ttu-id="4533f-202">다음 섹션에서는 디바이스 드라이버와 관련된 좀 더 복잡한 몇 가지 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-202">The following section describes some of the more advanced issues associated with device drivers.</span></span>

## <a name="advanced-driver-issues"></a><span data-ttu-id="4533f-203">고급 드라이버 문제</span><span class="sxs-lookup"><span data-stu-id="4533f-203">Advanced Driver Issues</span></span>

<span data-ttu-id="4533f-204">앞에서 설명한 대로 디바이스 드라이버에는 애플리케이션의 고유한 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-204">As mentioned previously, device drivers have requirements as unique as their applications.</span></span> <span data-ttu-id="4533f-205">일부 애플리케이션에는 상당한 양의 데이터 버퍼링이 필요할 수 있으며, 다른 애플리케이션은 잦은 디바이스 중단으로 인해 최적화된 드라이버 ISR이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-205">Some applications may require an enormous amount of data buffering while another application may require optimized driver ISRs because of high-frequency device interrupts.</span></span>

### <a name="io-buffering"></a><span data-ttu-id="4533f-206">I/O 버퍼링</span><span class="sxs-lookup"><span data-stu-id="4533f-206">I/O Buffering</span></span>

<span data-ttu-id="4533f-207">실시간 임베디드 애플리케이션의 데이터 버퍼링에는 상당한 계획이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-207">Data buffering in real-time embedded applications requires considerable planning.</span></span> <span data-ttu-id="4533f-208">일부 디자인은 기본 하드웨어 디바이스에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-208">Some of the design is dictated by the underlying hardware device.</span></span> <span data-ttu-id="4533f-209">디바이스에서 기본 바이트 I/O를 제공하는 경우 간단한 순환 버퍼가 순서대로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-209">If the device provides basic byte I/O, a simple circular buffer is probably in order.</span></span> <span data-ttu-id="4533f-210">그러나 디바이스가 블록, DMA 또는 패킷 I/O를 제공하는 경우 버퍼 관리 체계가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-210">However, if the device provides block, DMA, or packet I/O, a buffer management scheme is probably warranted.</span></span>

### <a name="circular-byte-buffers"></a><span data-ttu-id="4533f-211">순환 바이트 버퍼</span><span class="sxs-lookup"><span data-stu-id="4533f-211">Circular Byte Buffers</span></span>

<span data-ttu-id="4533f-212">순환 바이트 버퍼는 일반적으로 UART와 같은 간단한 직렬 하드웨어 디바이스를 관리하는 드라이버에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-212">Circular byte buffers are typically used in drivers that manage a simple serial hardware device like a UART.</span></span> <span data-ttu-id="4533f-213">이러한 상황에서 두 개의 순환 버퍼(입력용 1개, 출력용 1개)를 사용하는 경우가 가장 많습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-213">Two circular buffers are most often used in such situations—one for input and one for output.</span></span>

<span data-ttu-id="4533f-214">각 순환 바이트 버퍼는 바이트 메모리 영역(일반적으로 **UCHAR** 의 배열), 읽기 포인터 및 쓰기 포인터로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-214">Each circular byte buffer is comprised of a byte memory area (typically an array of **UCHAR** s), a read pointer, and a write pointer.</span></span> <span data-ttu-id="4533f-215">읽기 포인터와 쓰기 포인터가 버퍼의 동일한 메모리 위치를 참조하는 경우 버퍼가 빈 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-215">A buffer is considered empty when the read pointer and the write pointers reference the same memory location in the buffer.</span></span> <span data-ttu-id="4533f-216">드라이버 초기화는 버퍼의 시작 주소에 대한 읽기 및 쓰기 버퍼 포인터를 모두 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-216">Driver initialization sets both the read and write buffer pointers to the beginning address of the buffer.</span></span>

### <a name="circular-buffer-input"></a><span data-ttu-id="4533f-217">순환 버퍼 입력</span><span class="sxs-lookup"><span data-stu-id="4533f-217">Circular Buffer Input</span></span>

<span data-ttu-id="4533f-218">입력 버퍼는 애플리케이션이 준비되기 전에 도착하는 문자를 저장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-218">The input buffer is used to hold characters that arrive before the application is ready for them.</span></span> <span data-ttu-id="4533f-219">입력 문자가 수신되면(일반적으로 인터럽트 서비스 루틴에서) 새 문자는 하드웨어 디바이스에서 검색되고 쓰기 포인터가 가리키는 위치의 입력 버퍼에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-219">When an input character is received (usually in an interrupt service routine), the new character is retrieved from the hardware device and placed into the input buffer at the location pointed to by the write pointer.</span></span> <span data-ttu-id="4533f-220">그런 다음, 쓰기 포인터가 버퍼의 다음 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-220">The write pointer is then advanced to the next position in the buffer.</span></span> <span data-ttu-id="4533f-221">다음 위치가 버퍼의 끝을 지나는 경우 쓰기 포인터는 버퍼의 시작 부분으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-221">If the next position is past the end of the buffer, the write pointer is set to the beginning of the buffer.</span></span> <span data-ttu-id="4533f-222">새 쓰기 포인터가 읽기 포인터와 동일한 경우 쓰기 포인터 진행을 취소하여 큐 가득 참 상태를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-222">The queue full condition is handled by canceling the write pointer advancement if the new write pointer is the same as the read pointer.</span></span>

<span data-ttu-id="4533f-223">드라이버에 대한 애플리케이션 입력 바이트 요청은 먼저 입력 버퍼의 읽기 및 쓰기 포인터를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-223">Application input byte requests to the driver first examine the read and write pointers of the input buffer.</span></span> <span data-ttu-id="4533f-224">읽기 및 쓰기 포인터가 동일한 경우 버퍼가 비어 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-224">If the read and write pointers are identical, the buffer is empty.</span></span> <span data-ttu-id="4533f-225">읽기 포인터가 동일하지 않으면 읽기 포인터가 가리키는 바이트는 입력 버퍼에서 복사되고 읽기 포인터는 다음 버퍼 위치로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-225">Otherwise, if the read pointer is not the same, the byte pointed to by the read pointer is copied from the input buffer and the read pointer is advanced to the next buffer location.</span></span> <span data-ttu-id="4533f-226">새 읽기 포인터가 버퍼의 끝을 지나면 시작 부분으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-226">If the new read pointer is past the end of the buffer, it is reset to the beginning.</span></span> <span data-ttu-id="4533f-227">그림 12는 순환 입력 버퍼에 대한 논리를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-227">Figure 12 shows the logic for the circular input buffer.</span></span>

```c
UCHAR   tx_input_buffer[MAX_SIZE];
UCHAR   tx_input_write_ptr;
UCHAR   tx_input_read_ptr;

/* Initialization. */
tx_input_write_ptr =    &tx_input_buffer[0];
tx_input_read_ptr =     &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr = tx_input_write_ptr;
*tx_input_write_ptr++ = alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr = &tx_input_buffer[0]; /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr = save_ptr; /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
  alpha = *tx_input_read_ptr++;
  if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
      tx_input_read_ptr = &tx_input_buffer[0];
}
```
<span data-ttu-id="4533f-228">**그림 12. 순환 입력 버퍼에 대한 논리**</span><span class="sxs-lookup"><span data-stu-id="4533f-228">**FIGURE 12. Logic for Circular Input Buffer**</span></span>

> [!NOTE]
> <span data-ttu-id="4533f-229">\*신뢰할 수 있는 작업의 경우 입출력 순환 버퍼의 읽기 및 쓰기 포인터를 조작할 때 인터럽트를 잠가야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-229">\*For reliable operation, it may be necessary to lockout interrupts when manipulating the read and write pointers of both the input and output circular buffers.</span></span> *

### <a name="circular-output-buffer"></a><span data-ttu-id="4533f-230">순환 출력 버퍼</span><span class="sxs-lookup"><span data-stu-id="4533f-230">Circular Output Buffer</span></span>

<span data-ttu-id="4533f-231">출력 버퍼는 하드웨어 디바이스가 이전 바이트 전송을 완료하기 전에 출력을 위해 도착한 문자를 보관하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-231">The output buffer is used to hold characters that have arrived for output before the hardware device finished sending the previous byte.</span></span> <span data-ttu-id="4533f-232">출력 버퍼 처리는 전송 완료 인터럽트 처리가 출력 읽기 포인터를 조작하는 반면 애플리케이션 출력 요청은 출력 쓰기 포인터를 활용한다는 점을 제외하면 입력 버퍼 처리와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-232">Output buffer processing is similar to input buffer processing, except the transmit complete interrupt processing manipulates the output read pointer, while the application output request utilizes the output write pointer.</span></span>
<span data-ttu-id="4533f-233">그렇지 않은 경우 출력 버퍼 처리는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-233">Otherwise, the output buffer processing is the same.</span></span> <span data-ttu-id="4533f-234">그림 13은 순환 출력 버퍼에 대한 논리를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-234">Figure 13 shows the logic for the circular output buffer.</span></span>

```c
UCHAR   tx_output_buffer[MAX_SIZE];
UCHAR   tx_output_write_ptr;
UCHAR   tx_output_read_ptr;

/* Initialization. */
tx_output_write_ptr = &tx_output_buffer[0];
tx_output_read_ptr = &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
  *device_reg = *tx_output_read_ptr++;
  if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
      tx_output_read_ptr = &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr = tx_output_write_ptr;
*tx_output_write_ptr++ = alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr = &tx_output_buffer[0]; /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr = save_ptr; /* Buffer full! */
```
<span data-ttu-id="4533f-235">**그림 13. 순환 출력 버퍼에 대한 논리**</span><span class="sxs-lookup"><span data-stu-id="4533f-235">**FIGURE 13. Logic for Circular Output Buffer**</span></span>

### <a name="buffer-io-management"></a><span data-ttu-id="4533f-236">버퍼 I/O 관리</span><span class="sxs-lookup"><span data-stu-id="4533f-236">Buffer I/O Management</span></span>

<span data-ttu-id="4533f-237">임베디드 마이크로프로세서의 성능을 향상시키기 위해 많은 주변 디바이스는 소프트웨어에서 제공하는 버퍼를 사용하여 데이터를 전송하고 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-237">To improve the performance of embedded microprocessors, many peripheral device devices transmit and receive data with buffers supplied by software.</span></span> <span data-ttu-id="4533f-238">일부 구현에서는 여러 버퍼를 사용하여 개별 데이터 패킷을 전송하거나 수신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-238">In some implementations, multiple buffers may be used to transmit or receive individual packets of data.</span></span>

<span data-ttu-id="4533f-239">I/O 버퍼의 크기 및 위치는 애플리케이션 및/또는 드라이버 소프트웨어에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-239">The size and location of I/O buffers is determined by the application and/or driver software.</span></span> <span data-ttu-id="4533f-240">일반적으로 버퍼는 크기가 고정되며 ThreadX 블록 메모리 풀 내에서 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-240">Typically, buffers are fixed in size and managed within a ThreadX block memory pool.</span></span> <span data-ttu-id="4533f-241">그림 14는 일반적인 I/O 버퍼와 할당을 관리하는 ThreadX 블록 메모리 풀을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-241">Figure 14 describes a typical I/O buffer and a ThreadX block memory pool that manages their allocation.</span></span>

```c
typedef struct TX_IO_BUFFER_STRUCT
{
      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
      struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR tx_buffer_area[TX_MAX_BUFFER_SIZE];
} TX_IO_BUFFER;

TX_BLOCK_POOL tx_io_block_pool;

/* Create a pool of I/O buffers. Assume that the pointer
"free_memory_ptr"points to an available memory area that
is 64 KBytes in size. */
tx_block_pool_create(&tx_io_block_pool,
                  "Sample IO Driver Buffer Pool",
                  free_memory_ptr, 0x10000,
                  sizeof(TX_IO_BUFFER));
```

<span data-ttu-id="4533f-242">**그림 14. I/O 버퍼**</span><span class="sxs-lookup"><span data-stu-id="4533f-242">**FIGURE 14. I/O Buffer**</span></span>

### <a name="tx_io_buffer"></a><span data-ttu-id="4533f-243">TX_IO_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4533f-243">TX_IO_BUFFER</span></span>

<span data-ttu-id="4533f-244">Typedef TX_IO_BUFFER는 두 개의 포인터로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-244">The typedef TX_IO_BUFFER consists of two pointers.</span></span> <span data-ttu-id="4533f-245">**tx_next_packet** 포인터는 입력 또는 출력 목록에서 여러 패킷을 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-245">The **tx_next_packet** pointer is used to link multiple packets on either the input or output list.</span></span> <span data-ttu-id="4533f-246">**tx_next_buffer** 포인터는 디바이스에서 데이터의 개별 패킷을 구성하는 버퍼를 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-246">The **tx_next_buffer** pointer is used to link together buffers that make up an individual packet of data from the device.</span></span> <span data-ttu-id="4533f-247">풀에서 버퍼를 할당하면 이들 두 포인터는 모두 NULL로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-247">Both of these pointers are set to NULL when the buffer is allocated from the pool.</span></span> <span data-ttu-id="4533f-248">또한 일부 디바이스는 버퍼 영역에 실제로 데이터가 얼마나 포함되었는지를 나타내는 다른 필드가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-248">In addition, some devices may require another field to indicate how much of the buffer area actually contains data.</span></span>

### <a name="buffered-io-advantage"></a><span data-ttu-id="4533f-249">버퍼링된 I/O 장점</span><span class="sxs-lookup"><span data-stu-id="4533f-249">Buffered I/O Advantage</span></span>

<span data-ttu-id="4533f-250">버퍼 I/O 체계의 장점은 무엇일까요?</span><span class="sxs-lookup"><span data-stu-id="4533f-250">What are the advantages of a buffer I/O scheme?</span></span> <span data-ttu-id="4533f-251">가장 큰 장점은 디바이스 레지스터와 애플리케이션의 메모리 간에 데이터가 복사되지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-251">The biggest advantage is that data is not copied between the device registers and the application's memory.</span></span> <span data-ttu-id="4533f-252">대신 드라이버는 일련의 버퍼 포인터를 디바이스에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-252">Instead, the driver provides the device with a series of buffer pointers.</span></span> <span data-ttu-id="4533f-253">물리적 디바이스 I/O는 제공된 버퍼 메모리를 직접 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-253">Physical device I/O utilizes the supplied buffer memory directly.</span></span>

<span data-ttu-id="4533f-254">프로세서를 사용하여 정보의 입력 또는 출력 패킷을 복사하는 것은 비용이 많이 들기 때문에 처리량이 많은 I/O 상황에서 피해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-254">Using the processor to copy input or output packets of information is extremely costly and should be avoided in any high throughput I/O situation.</span></span>

<span data-ttu-id="4533f-255">버퍼링된 I/O 방식의 또 다른 장점은 입력 및 출력 목록에 전체 조건이 없다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-255">Another advantage to the buffered I/O approach is that the input and output lists do not have full conditions.</span></span> <span data-ttu-id="4533f-256">사용 가능한 모든 버퍼는 한 번에 두 목록 중 하나에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-256">All of the available buffers can be on either list at any one time.</span></span> <span data-ttu-id="4533f-257">이는 챕터의 앞부분에 나오는 단순 바이트 순환 버퍼와 대조됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-257">This contrasts with the simple byte circular buffers presented earlier in the chapter.</span></span> <span data-ttu-id="4533f-258">각각은 컴파일할 때 크기가 정해져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-258">Each had a fixed size determined at compilation.</span></span>

### <a name="buffered-driver-responsibilities"></a><span data-ttu-id="4533f-259">버퍼링된 드라이버 책임</span><span class="sxs-lookup"><span data-stu-id="4533f-259">Buffered Driver Responsibilities</span></span>

<span data-ttu-id="4533f-260">버퍼링된 디바이스 드라이버는 연결된 I/O 버퍼 목록 관리에만 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-260">Buffered device drivers are only concerned with managing linked lists of I/O buffers.</span></span> <span data-ttu-id="4533f-261">입력 버퍼 목록은 애플리케이션 소프트웨어가 준비되기 전에 수신되는 패킷에 대해 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-261">An input buffer list is maintained for packets that are received before the application software is ready.</span></span> <span data-ttu-id="4533f-262">반대로, 하드웨어 디바이스가 처리할 수 있는 것보다 빠르게 전송되는 패킷에 대해 출력 버퍼 목록이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-262">Conversely, an output buffer list is maintained for packets being sent faster than the hardware device can handle them.</span></span> <span data-ttu-id="4533f-263">그림 15는 데이터 패킷의 간단한 입력 및 출력 링크 목록과 각 패킷을 구성하는 버퍼를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-263">Figure 15 shows simple input and output linked lists of data packets and the buffer(s) that make up each packet.</span></span>

<span data-ttu-id="4533f-264">**입력 목록**</span><span class="sxs-lookup"><span data-stu-id="4533f-264">**Input List**</span></span>

![입력 목록](./media/user-guide/input-list.png)

<span data-ttu-id="4533f-266">**출력 목록**</span><span class="sxs-lookup"><span data-stu-id="4533f-266">**Output List**</span></span>

![출력 목록](./media/user-guide/output-list.png)

<span data-ttu-id="4533f-268">**그림 15. 입출력 목록**</span><span class="sxs-lookup"><span data-stu-id="4533f-268">**FIGURE 15. Input-Output Lists**</span></span>

<span data-ttu-id="4533f-269">애플리케이션은 동일한 I/O 버퍼를 사용하여 버퍼링된 드라이버와 인터페이스합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-269">Applications interface with buffered drivers with the same I/O buffers.</span></span> <span data-ttu-id="4533f-270">전송 시 애플리케이션 소프트웨어는 드라이버에 전송할 하나 이상의 버퍼를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-270">On transmit, application software provides the driver with one or more buffers to transmit.</span></span> <span data-ttu-id="4533f-271">애플리케이션 소프트웨어가 입력을 요청하면 드라이버는 I/O 버퍼에 입력 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-271">When the application software requests input, the driver returns the input data in I/O buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="4533f-272">*일부 애플리케이션에서는 애플리케이션이 드라이버의 입력 버퍼와 사용 가능한 버퍼를 교환해야 하는 드라이버 입력 인터페이스를 빌드하는 것이 유용할 수 있습니다. 이렇게 하면 드라이버 내부의 일부 버퍼 할당 처리를 완화할 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="4533f-272">*In some applications, it may be useful to build a driver input interface that requires the application to exchange a free buffer for an input buffer from the driver. This might alleviate some buffer allocation processing inside of the driver.*</span></span>

### <a name="interrupt-management"></a><span data-ttu-id="4533f-273">인터럽트 관리</span><span class="sxs-lookup"><span data-stu-id="4533f-273">Interrupt Management</span></span>

<span data-ttu-id="4533f-274">일부 애플리케이션에서 디바이스 인터럽트 빈도는 C로 ISR을 쓰거나 각 인터럽트의 ThreadX와 상호 작용하는 것을 금지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-274">In some applications, the device interrupt frequency may prohibit writing the ISR in C or to interact with ThreadX on each interrupt.</span></span> <span data-ttu-id="4533f-275">예를 들어, 인터럽트된 컨텍스트를 저장하고 복원하는 데 25us가 필요한 경우 인터럽트 빈도가 50us이면 전체 컨텍스트를 저장하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-275">For example, if it takes 25us to save and restore the interrupted context, it would not be advisable to perform a full context save if the interrupt frequency was 50us.</span></span> <span data-ttu-id="4533f-276">이러한 경우 대부분의 디바이스 인터럽트를 처리하는 데 작은 어셈블리 언어 ISR이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-276">In such cases, a small assembly language ISR is used to handle most of the device interrupts.</span></span> <span data-ttu-id="4533f-277">이러한 낮은 오버헤드 ISR은 필요할 때만 ThreadX와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-277">This low-overhead ISR would only interact with ThreadX when necessary.</span></span>

<span data-ttu-id="4533f-278">챕터 3 끝에 나오는 인터럽트 관리 설명에서 유사한 설명을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-278">A similar discussion can be found in the interrupt management discussion at the end of Chapter 3.</span></span>

### <a name="thread-suspension"></a><span data-ttu-id="4533f-279">스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="4533f-279">Thread Suspension</span></span>

<span data-ttu-id="4533f-280">이 챕터의 앞부분에 제공된 단순 드라이버 예제에서 문자를 사용할 수 없는 경우 입력 서비스 호출자가 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-280">In the simple driver example presented earlier in this chapter, the caller of the input service suspends if a character is not available.</span></span> <span data-ttu-id="4533f-281">일부 애플리케이션에서는 허용되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-281">In some applications, this might not be acceptable.</span></span>

<span data-ttu-id="4533f-282">예를 들어, 드라이버의 입력을 처리하는 스레드에 다른 작업이 있는 경우 드라이버 입력만 일시 중단하는 것이 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-282">For example, if the thread responsible for processing input from a driver also has other duties, suspending on just the driver input is probably not going to work.</span></span> <span data-ttu-id="4533f-283">대신 드라이버를 사용자 정의하여 다른 처리 요청이 스레드에 생성되는 방식과 유사한 처리를 요청해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-283">Instead, the driver needs to be customized to request processing similar to the way other processing requests are made to the thread.</span></span>

<span data-ttu-id="4533f-284">대부분의 경우 입력 버퍼가 연결된 목록에 배치되고 입력 이벤트 메시지가 스레드의 입력 큐로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="4533f-284">In most cases, the input buffer is placed on a linked list and an input event message is sent to the thread's input queue.</span></span>
