---
title: 부록 D - 덤프 및 추적 버퍼
description: Azure RTOS ThreadX에서 만든 추적 버퍼를 호스트 컴퓨터의 파일에 덤프하는 작업은 사용되는 특정 개발 도구에서 제공하는 명령 및/또는 유틸리티를 통해 수행됩니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 30f6b5e329feeb2dca37dda391fd738aba587c9a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812540"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a><span data-ttu-id="a26a1-103">부록 D - 덤프 및 추적 버퍼</span><span class="sxs-lookup"><span data-stu-id="a26a1-103">Appendix D - Dumping and trace buffer</span></span>

<span data-ttu-id="a26a1-104">Azure RTOS ThreadX에서 만든 추적 버퍼를 호스트 컴퓨터의 파일에 덤프하는 작업은 사용되는 특정 개발 도구에서 제공하는 명령 및/또는 유틸리티를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-104">Dumping the trace buffer created by Azure RTOS ThreadX to a file on the host computer is done via commands and/or utilities provided by the specific development tool being used.</span></span> <span data-ttu-id="a26a1-105">이 부록에는 ThreadX와 함께 사용되는 몇 가지 인기 있는 개발 도구에서 추적 버퍼를 호스트 파일에 덤프하는 예제가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-105">This appendix contains examples of dumping a trace buffer to a host file in some of the more popular development tools used with ThreadX.</span></span> 

## <a name="benchx-tools"></a><span data-ttu-id="a26a1-106">BenchX 도구</span><span class="sxs-lookup"><span data-stu-id="a26a1-106">BenchX Tools</span></span>

<span data-ttu-id="a26a1-107">아래와 같이 _\*_메모리 보기_\*\* 내에서 \***파일에 메모리 저장** _ 단추를 선택하여 BenchX 도구를 통해 추적 버퍼를 호스트 파일에 쉽게 덤프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-107">The trace buffer can be dumped to a host file easily with the BenchX tools by selecting the ***Store Memory To File** _ button within the _*_Memory View_\*\*, as shown below:</span></span>

![BenchX 도구의 메모리 보기 스크린샷](./media/user-guide/image642.jpg)

<span data-ttu-id="a26a1-109">여기서 아래와 같이 추적 버퍼 주소, 크기, 대상 파일 이름(경로 포함)을 지정하고 ***저장*** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-109">At this point, specify the trace buffer address, size, destination file name (including path), and select the ***Save*** button as shown below.</span></span> <span data-ttu-id="a26a1-110">그러면 TraceX 내에서 볼 이진 추적 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-110">This will create the binary trace file for viewing within TraceX.</span></span>

![BenchX 도구 저장 대화 상자의 스크린샷](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a><span data-ttu-id="a26a1-112">RealView 도구</span><span class="sxs-lookup"><span data-stu-id="a26a1-112">RealView Tools</span></span>

<span data-ttu-id="a26a1-113">RealView의 명령줄 프롬프트에서 다음 명령을 입력하여 ARM RealView 도구를 통해 추적 버퍼를 호스트 파일에 쉽게 덤프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-113">The trace buffer can be dumped to a host file easily with the ARM RealView tools by entering the following command at the command-line prompt in RealView:</span></span>

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

<span data-ttu-id="a26a1-114">완료되면 ***trace_file.trx*** 파일에는 주소 0x6860에서 시작하여 0xE560까지 이동하는 추적 버퍼가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-114">Upon completion, the file ***trace_file.trx*** will contain the trace buffer that is located starting at the address 0x6860 and goes up to address 0xE560.</span></span> <span data-ttu-id="a26a1-115">이 파일은 TraceX에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-115">This file is ready for viewing by TraceX.</span></span>

## <a name="iar-tools"></a><span data-ttu-id="a26a1-116">IAR 도구</span><span class="sxs-lookup"><span data-stu-id="a26a1-116">IAR Tools</span></span>

<span data-ttu-id="a26a1-117">다음과 같이 메모리 보기에서 간단히 마우스 오른쪽 단추를 클릭하고 ***메모리 저장...*** 옵션을 선택하면 IAR 도구로 추적 버퍼를 호스트 파일에 쉽게</span><span class="sxs-lookup"><span data-stu-id="a26a1-117">The trace buffer can be dumped to a host file easily with the IAR tools by simply right-clicking in the memory view and selecting the ***Memory Save…***</span></span> <span data-ttu-id="a26a1-118">덤프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-118">option, as shown below.</span></span>

![IAR 도구의 메모리 저장 옵션 스크린샷](./media/user-guide/image0_311.jpg)

<span data-ttu-id="a26a1-120">그러면 \***메모리 저장** _ 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-120">This results in the \***Memory Save** _ dialog to be displayed.</span></span> <span data-ttu-id="a26a1-121">시작 주소와 끝 주소 및 추적 파일 이름을 입력한 다음, _\*_저장_\*_ 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-121">Enter the starting and ending address and the trace file name, then select the _*_Save_*_ button.</span></span> <span data-ttu-id="a26a1-122">아래 예제에서 IAR 도구는 지정된 추적 버퍼를 _*_trace_file.hex_*\* 파일의 Intel HEX 레코드에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-122">In the example shown below, the IAR tools save the specified trace buffer into Intel HEX records in the file _\*_trace_file.hex_\*\*.</span></span>

![IAR 도구 메모리 저장 대화 상자의 스크린샷](./media/user-guide/image648.jpg)

<span data-ttu-id="a26a1-124">이 시점에서 추적 버퍼는 호스트의 ***trace_file.hex*** 파일에 저장되며 TraceX를 사용하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-124">At this point, we have the trace buffer saved in the ***trace_file.hex*** file on the host and is ready for viewing with TraceX.</span></span>

## <a name="codewarrior-tools"></a><span data-ttu-id="a26a1-125">CodeWarrior 도구</span><span class="sxs-lookup"><span data-stu-id="a26a1-125">CodeWarrior Tools</span></span>

<span data-ttu-id="a26a1-126">명령 창에서 \***save** _ 명령을 입력하면 CodeWarrior 도구로 추적 버퍼를 호스트 파일에 쉽게 덤프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-126">The trace buffer can be dumped to a host file easily with the CodeWarrior tools by entering the \***save** _ command in the Command Window.</span></span> <span data-ttu-id="a26a1-127">다음 예제 _ *_save_*\* 명령은 추적 버퍼가 0x102200에서 시작하고 0x109F00에서 끝나는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-127">The following example _ *_save_*\* command assumes the trace buffer starts at 0x102200 and ends at 0x109F00:</span></span>

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

<span data-ttu-id="a26a1-128">이로 인해 추적 버퍼가 호스트의 ***trace_file.trx*** 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-128">This results in the trace buffer being saved in the file ***trace_file.trx*** on the host.</span></span>

## <a name="mplab-tools"></a><span data-ttu-id="a26a1-129">MPLAB 도구</span><span class="sxs-lookup"><span data-stu-id="a26a1-129">MPLAB Tools</span></span>

<span data-ttu-id="a26a1-130">MPLAB는 테이블 내보내기 유틸리티를 통해 TraceX 호환 추적 파일을 만들 수 있습니다. 이를 통해 모든 범위의 메모리를 호스트 파일로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-130">MPLAB can create a TraceX-compatible trace file through its Export Table utility, which allows the export of any range of memory to a host file.</span></span> <span data-ttu-id="a26a1-131">이 유틸리티를 사용하여 TraceX에 대한 추적 파일을 만들려면 다음과 같이 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-131">To use this utility to create a trace file for TraceX, proceed as follows:</span></span>

<span data-ttu-id="a26a1-132">**1단계** 보기 -> 메모리를 선택하여 메모리 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-132">**Step 1** Open a memory window by selecting View -> Memory.</span></span>

![보기 메뉴에서 선택한 메모리의 스크린샷](./media/user-guide/image0_316.jpg)

<span data-ttu-id="a26a1-134">**2단계** **메모리 보기** 내에서 마우스 오른쪽 단추를 클릭하여 옵션 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-134">**Step 2** Right-click within the **Memory View** to display a list of options.</span></span> <span data-ttu-id="a26a1-135">**표시 형식-1 바이트** 를 지정하여 바이트 표시를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-135">Specify **Display Format -1 Byte** to select byte display..</span></span>

![표시 형식 옵션이 선택된 메모리 보기의 스크린샷](./media/user-guide/image650.png)

![이동 대화 상자의 스크린샷](./media/user-guide/image651.jpg)

<span data-ttu-id="a26a1-138">**3단계** **메모리 보기** 창 내에서 마우스 오른쪽 단추를 다시 클릭하고 **이동** 을 선택합니다. 그러면 이벤트 버퍼의 주소를 지정할 수 있는 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-138">**Step 3** Right-click again within the **Memory View** Window and select **Go To**, which opens a dialog box that enables you to specify the address of the event buffer.</span></span> <span data-ttu-id="a26a1-139">이 예제에서는 **_event_buffer_** 가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-139">This example shows **_event_buffer_** being displayed.</span></span>

![이동 옵션이 선택된 메모리 보기의 스크린샷](./media/user-guide/image0_312.jpg)

![표시된 event_buffer를 보여 주는 예제의 스크린샷](./media/user-guide/image653.png)

<span data-ttu-id="a26a1-142">**4단계** 이렇게 하면 항상 문자열 BTXT...인 추적 버퍼의 첫 번째 위치 콘텐츠가 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-142">**Step 4** This highlights the contents of the first location of the trace buffer, which is always the string BTXT….</span></span>

![추적 버퍼의 첫 번째 위치에 대한 스크린샷](./media/user-guide/image0_313.jpg)

<span data-ttu-id="a26a1-144">**5단계** 이제 다시 마우스 오른쪽 단추를 클릭하여 옵션 메뉴를 표시하고 **테이블 내보내기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-144">**Step 5** Now, right-click again to bring up the options menu, and select **Export Table**.</span></span>

![테이블 내보내기 옵션이 선택된 메모리 보기의 스크린샷](./media/user-guide/image0_314.jpg)

<span data-ttu-id="a26a1-146">**6단계** 표시된 것처럼 **테이블 내보내기** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-146">**Step 6** This brings up the **Export Table** dialog, as shown.</span></span> <span data-ttu-id="a26a1-147">내보낼 주소의 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-147">Specify the range of addresses to export.</span></span> <span data-ttu-id="a26a1-148">8K 추적 버퍼의 경우 이 예제에서와 같이 범위를 0xA00006AC부터 0xA00026AC까지로 지정하고, 만들 호스트 파일의 이름을 입력합니다(이 예제에서는 demo_threadx.trx).</span><span class="sxs-lookup"><span data-stu-id="a26a1-148">For an 8K trace buffer, as is the case in this example, specify the range 0xA00006AC to 0xA00026AC, and enter a name for the host file to be created (demo_threadx.trx in this example).</span></span>

<span data-ttu-id="a26a1-149">![[내보내기 대화 상자의 스크린샷.](./media/user-guide/image656.jpg)</span><span class="sxs-lookup"><span data-stu-id="a26a1-149">![[Screenshot of the Export As dialog.](./media/user-guide/image656.jpg)</span></span>

<span data-ttu-id="a26a1-150">**7단계** **demo_threadx.trx** 라는 파일이 호스트에 생성됩니다. 이 파일은 TraceX에서 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-150">**Step 7** A file named **demo_threadx.trx** will be created on the host, and this file can be opened by TraceX.</span></span>

## <a name="ghs-tools"></a><span data-ttu-id="a26a1-151">GHS 도구</span><span class="sxs-lookup"><span data-stu-id="a26a1-151">GHS Tools</span></span>

<span data-ttu-id="a26a1-152">디버그 명령 창의 명령줄 프롬프트에서 다음 명령을 입력하면 GHS 도구를 통해 추적 버퍼를 호스트 파일에 쉽게 덤프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-152">The trace buffer can be dumped to a host file easily with the GHS tools by entering the following command at the command-line prompt in the debug command window:</span></span>

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

<span data-ttu-id="a26a1-153">완료되면 **demo_threadx.trx** 파일에는 event_buffer에 있는 32,768바이트 크기의 추적 버퍼가 포함되고 TraceX에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-153">Upon completion, the file **demo_threadx.trx** will contain the trace buffer that is located in the event_buffer with a size of 32,768 bytes and is ready for viewing by TraceX.</span></span>

## <a name="renesas-hew"></a><span data-ttu-id="a26a1-154">Renesas HEW</span><span class="sxs-lookup"><span data-stu-id="a26a1-154">Renesas HEW</span></span>

<span data-ttu-id="a26a1-155">다음 세 가지 단계(및 하위 단계)를 수행하면 Renasas HEW로 추적 버퍼를 쉽게 덤프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-155">The trace buffer can be dumped to a host file easily with the Renasas HEW tools by following the three steps (and substeps) below:</span></span>

<span data-ttu-id="a26a1-156">**1단계** 메모리 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-156">**Step 1** Open Memory Window.</span></span>

<span data-ttu-id="a26a1-157">![[메모리 창의 스크린샷.](./media/user-guide/image657.jpg)</span><span class="sxs-lookup"><span data-stu-id="a26a1-157">![[Screenshot of the Memory Window.](./media/user-guide/image657.jpg)</span></span>

<span data-ttu-id="a26a1-158">**2단계** 메모리 창 내에 커서를 놓고 마우스 오른쪽 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-158">**Step 2** Place cursor within memory window and right click.</span></span>

![저장 옵션이 선택된 메모리 창의 스크린샷](./media/user-guide/image0_315.jpg)

<span data-ttu-id="a26a1-160">**3단계** 저장을 선택한 다음, 다른 이름으로 메모리 저장 창에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-160">**Step 3** Select Save, then in the Save Memory As window do the following:</span></span>

- <span data-ttu-id="a26a1-161">파일 형식 선택: 이진</span><span class="sxs-lookup"><span data-stu-id="a26a1-161">Select File format: Binary.</span></span>
- <span data-ttu-id="a26a1-162">파일 이름 지정: 원하는 대로</span><span class="sxs-lookup"><span data-stu-id="a26a1-162">Specify Filename: As Desired</span></span>
- <span data-ttu-id="a26a1-163">시작 주소 지정: trace_buffer</span><span class="sxs-lookup"><span data-stu-id="a26a1-163">Specify Start address: trace_buffer</span></span>
- <span data-ttu-id="a26a1-164">끝 주소 지정: (trace_buffer+크기)</span><span class="sxs-lookup"><span data-stu-id="a26a1-164">Specify End address: (trace_buffer+size)</span></span>
- <span data-ttu-id="a26a1-165">액세스 크기 지정: 1</span><span class="sxs-lookup"><span data-stu-id="a26a1-165">Specify Access size: 1</span></span>
- <span data-ttu-id="a26a1-166">저장을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a26a1-166">Click Save</span></span>

![다른 이름으로 메모리 저장 대화 상자의 스크린샷](./media/user-guide/image659.jpg)