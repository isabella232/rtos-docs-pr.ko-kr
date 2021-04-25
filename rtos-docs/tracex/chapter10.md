---
title: 챕터 10 - 고객 사용자 이벤트
description: 이 챕터에는 해당 이벤트에 대한 사용자 정의 이벤트, 사용자 지정 아이콘 및 정보 필드를 만드는 방법에 대한 설명이 포함되어 있습니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 635c2d79922de9d5649bab841ae946cac862056c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812421"
---
# <a name="chapter-10---customer-user-events"></a><span data-ttu-id="7264e-103">챕터 10 - 고객 사용자 이벤트</span><span class="sxs-lookup"><span data-stu-id="7264e-103">Chapter 10 - Customer user events</span></span>

<span data-ttu-id="7264e-104">이 챕터에는 해당 이벤트에 대한 사용자 정의 이벤트, 사용자 지정 아이콘 및 정보 필드를 만드는 방법에 대한 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-104">This chapter contains a description of how to create user-defined events and custom icons and information fields for such events.</span></span> <span data-ttu-id="7264e-105">이 챕터에는 다음 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-105">This chapter includes the following sections:</span></span> 

## <a name="inserting-user-defined-events"></a><span data-ttu-id="7264e-106">사용자 정의 이벤트 삽입</span><span class="sxs-lookup"><span data-stu-id="7264e-106">Inserting User-Defined Events</span></span>

<span data-ttu-id="7264e-107">ThreadX는 개발자가 자신의 고유한 사용자 정의 이벤트를 기록할 수 있는 기능을 제공하며 TraceX에서 그래픽으로 볼 수 있는 더 유용한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-107">ThreadX provides the ability for developers to log their own user-defined events, providing even more useful information that can be viewed graphically by TraceX.</span></span> <span data-ttu-id="7264e-108">사용자 정의 이벤트 번호의 범위는</span><span class="sxs-lookup"><span data-stu-id="7264e-108">User-defined event numbers range from</span></span>

<span data-ttu-id="7264e-109">**TX_TRACE_USER_EVENT_START**(4096)~**TX_TRACE_USER_EVENT_END**(65535)(포함)입니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-109">**TX_TRACE_USER_EVENT_START** (4096) through **TX_TRACE_USER_EVENT_END** (65535), inclusive.</span></span> <span data-ttu-id="7264e-110">추적 버퍼의 이벤트는 챕터 5에서 정의된 ***tx_trace_user_event_insert*** 를 통해 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-110">The placement of the events in the trace buffer is done via the ***tx_trace_user_event_insert***, defined in Chapter 5.</span></span> <span data-ttu-id="7264e-111">다음 예제 호출은 사용자 정의 이벤트를 대상의 현재 추적 버퍼에 삽입합니다. 즉, 사용자 정의 이벤트 4096 및 이벤트 4098을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-111">The following example calls insert two user-defined events into the current trace buffer on the target, namely user-defined event 4096 and event 4098:</span></span>

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a><span data-ttu-id="7264e-112">사용자 정의 이벤트의 기본 표시</span><span class="sxs-lookup"><span data-stu-id="7264e-112">Default Display of User-Defined Events</span></span>

![사용자 정의 이벤트 아이콘](./media/user-guide/tx-events/image0.png)

<span data-ttu-id="7264e-114">기본적으로 TraceX는 챕터 6에서 설명한 대로 기본 사용자 정의 이벤트 아이콘을 사용하여 모든 사용자 이벤트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-114">By default, TraceX displays all user events with a default user-defined Event icon as described in Chapter 6.</span></span> <span data-ttu-id="7264e-115">그림 28은 이전 ***tx_trace_user_event_insert*** 예제를 통해 이벤트 버퍼에 배치된 이벤트 452 및 453에 대한 기본 사용자 정의 이벤트 아이콘을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-115">Figure 28 shows the default user-defined event icon for events 452 and 453, which were placed in the event buffer via the previous ***tx_trace_user_event_insert*** examples.</span></span>

<span data-ttu-id="7264e-116">![사용자 정의 이벤트의 기본 표시에 대한 스크린샷입니다.](./media/user-guide/10.1.png)
**그림 28**</span><span class="sxs-lookup"><span data-stu-id="7264e-116">![Screenshot of the default display of user-defined events.](./media/user-guide/10.1.png)
**FIGURE 28**</span></span>

<span data-ttu-id="7264e-117">자세한 정보는 사용자 정의 이벤트에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-117">Detailed information is also available for user-defined Events.</span></span> <span data-ttu-id="7264e-118">그림 28은 이벤트 번호가 4096인 이벤트 452에 대한 자세한 이벤트 정보를 보여주고 지정된 4개의 정보 필드를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-118">Figure 28 shows the detailed event information for event 452, which has event number 4096 and shows the specified four information fields.</span></span>

<span data-ttu-id="7264e-119">![사용자 정의 이벤트의 자세한 표시에 대한 스크린샷입니다.](./media/user-guide/10.2.png)
**그림 29**</span><span class="sxs-lookup"><span data-stu-id="7264e-119">![Screenshot of the detailed display of user-defined events.](./media/user-guide/10.2.png)
**FIGURE 29**</span></span>

## <a name="defining-custom-user-defined-event-icons"></a><span data-ttu-id="7264e-120">사용자 지정 사용자 정의 이벤트 아이콘 정의</span><span class="sxs-lookup"><span data-stu-id="7264e-120">Defining Custom User-Defined Event Icons</span></span>

<span data-ttu-id="7264e-121">또한 TraceX는 사용자 지정 사용자 정의 이벤트 아이콘 및 사용자 지정 정보 필드 레이블을 만들 수 있는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-121">TraceX also provides the user the ability to create custom user-defined event icons and custom information field labels.</span></span> <span data-ttu-id="7264e-122">이 기능은 \***tracex_custom trxc** _ 구성 파일에 이벤트 아이콘 사양을 추가하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-122">This capability is achieved by adding event icon specifications to the \***tracex_custom.trxc** _ configuration file.</span></span> <span data-ttu-id="7264e-123">이 파일은 사용자 정의 TraceX 설치 디렉터리의 _ *_CustomEvents_*\* 하위 디렉터리에 있으며 기본값은 ‘c:\Azure_RTOS\TraceX’입니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-123">This file is located in the _ *_CustomEvents_*\* subdirectory of your user-defined TraceX installation directory, which defaults to c:\Azure_RTOS\TraceX.</span></span> <span data-ttu-id="7264e-124">예제 디렉터리 경로는 그림 30에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-124">An example directory path is shown in Figure 30.</span></span>

<span data-ttu-id="7264e-125">![예제 디렉터리 경로의 스크린샷입니다.](./media/user-guide/custom_events_folder.png)
**그림 30**</span><span class="sxs-lookup"><span data-stu-id="7264e-125">![Screenshot of an example directory path.](./media/user-guide/custom_events_folder.png)
**FIGURE 30**</span></span>

<span data-ttu-id="7264e-126">***tracex_custom.trxc*** 사용자 지정 이벤트 구성 파일은 0개 이상의 사용자 지정 이벤트 정의를 포함하는 간단한 ASCII 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-126">The ***tracex_custom.trxc*** custom event configuration file is a simple ASCII text file containing zero or more custom event definitions.</span></span> <span data-ttu-id="7264e-127">파일 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-127">The format of the file is as follows:</span></span>

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

<span data-ttu-id="7264e-128">시작 및 종료 사이의 각 줄은 단일 사용자 지정 이벤트를 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-128">Each line between Start and End is used to define a single custom event.</span></span> <span data-ttu-id="7264e-129">TraceX는 사용자 지정 이벤트가 정의되지 않은 이 파일의 템플릿 버전을 제공합니다('시작' 및 '종료' 레이블 사이에는 아무 것도 없음).</span><span class="sxs-lookup"><span data-stu-id="7264e-129">TraceX provides a template version of this file with no custom events defined (nothing between the "Start" and "End" labels).</span></span> <span data-ttu-id="7264e-130">사용자 지정 이벤트 정의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-130">The format of a custom event definition is as follows:</span></span>

<span data-ttu-id="7264e-131">**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**</span><span class="sxs-lookup"><span data-stu-id="7264e-131">**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**</span></span>

<span data-ttu-id="7264e-132">여기서</span><span class="sxs-lookup"><span data-stu-id="7264e-132">where:</span></span>

- <span data-ttu-id="7264e-133">number: 4096과 65535 사이의 사용자 정의 이벤트 번호(포함)를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-133">number: Defines the user-defined event number, between 4096 and 65535, inclusive.</span></span></th>
- <span data-ttu-id="7264e-134">name: 사용자 정의 이벤트의 논리적 이름을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-134">name: Defines the logical name for the user-defined event.</span></span></td>
- <span data-ttu-id="7264e-135">abbreviation: 두 글자로 된 사용자 정의 이벤트 약어를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-135">abbreviation: Defines the two-letter user-defined event abbreviation.</span></span></td>
- <span data-ttu-id="7264e-136">top_color: 괄호 안의 3자리 숫자인 아이콘의 위쪽 절반에 대한 RGB 값을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-136">top_color: Defines the RGB value for the top-half of the icon, which is a three-digit number in parenthesis.</span></span> <span data-ttu-id="7264e-137">일부 일반적인 RGB 정의는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-137">Some typical RGB definitions are</span></span>
  - <span data-ttu-id="7264e-138">검은색 = (0,0,0)</span><span class="sxs-lookup"><span data-stu-id="7264e-138">BLACK = (0,0,0)</span></span>       
  - <span data-ttu-id="7264e-139">흰색 = (255,255,255)</span><span class="sxs-lookup"><span data-stu-id="7264e-139">WHITE = (255,255,255)</span></span>
  - <span data-ttu-id="7264e-140">빨간색 = (255,0,0)</span><span class="sxs-lookup"><span data-stu-id="7264e-140">RED = (255,0,0)</span></span>     
  - <span data-ttu-id="7264e-141">녹색 = (0,255,0)</span><span class="sxs-lookup"><span data-stu-id="7264e-141">GREEN = (0,255,0)</span></span>     
  - <span data-ttu-id="7264e-142">파란색 = (0,0,255)</span><span class="sxs-lookup"><span data-stu-id="7264e-142">BLUE = (0,0,255)</span></span>     
  - <span data-ttu-id="7264e-143">노란색 = (255,255,0)</span><span class="sxs-lookup"><span data-stu-id="7264e-143">YELLOW = (255,255,0)</span></span>   
  - <span data-ttu-id="7264e-144">녹청색 = (0,255,255)</span><span class="sxs-lookup"><span data-stu-id="7264e-144">CYAN = (0,255,255)</span></span>   
  - <span data-ttu-id="7264e-145">자홍색 = (255,0,255)</span><span class="sxs-lookup"><span data-stu-id="7264e-145">MAGENTA = (255,0,255)</span></span>   
  <span data-ttu-id="7264e-146">RBG 사양을 사용하면 사용자가 각 사용자 정의 아이콘에 대해 광범위한 색 범위를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-146">Using the RBG specification gives the user a broad range of colors for each user-defined icon.</span></span> <span data-ttu-id="7264e-147">RBG 색 정의에 대한 자세한 내용은 다음을 참조하십시오. https://en.wikipedia.org/wiki/RGB#Digital_representations</span><span class="sxs-lookup"><span data-stu-id="7264e-147">For more information on RBG color definition, see: https://en.wikipedia.org/wiki/RGB#Digital_representations</span></span>
- <span data-ttu-id="7264e-148">botton_color: 아이콘의 아래쪽 절반에 대한 RGB 값(괄호 안의 3자리 숫자)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-148">botton_color: Defines the RGB value for the bottom half of the icon, which is a three-digit number in parenthesis.</span></span>
- <span data-ttu-id="7264e-149">label1: _ *_tx_trace_user_event_insert_*\* 호출에 지정된 대로 \***Info_field_1** _의 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-149">label1: Label for ***info_field_1** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="7264e-150">label2: _ *_tx_trace_user_event_insert_*\* 호출에 지정된 대로 \***Info_field_2** _의 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-150">label2: Label for ***info_field_2** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="7264e-151">label3: _ *_tx_trace_user_event_insert_*\* 호출에 지정된 대로 \***Info_field_3** _의 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-151">label3: Label for ***info_field_3** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="7264e-152">label4: _ *_tx_trace_user_event_insert_*\* 호출에 지정된 대로 \***Info_field_4** _의 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-152">label4: Label for ***info_field_4** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>

<span data-ttu-id="7264e-153">이 챕터에서 사용되는 두 개의 사용자 정의 이벤트에 대한 예제 정의는 그림 10.4에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-153">Example definitions for each of the two user-defined events used in this chapter are shown in Figure 10.4.</span></span> <span data-ttu-id="7264e-154">첫 번째 정의는 \***tracex_custom.trxc** _ 파일의 5번째 줄에 있는 이벤트 4096에 대한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-154">The first definition is for event 4096 at line 5 of the \***tracex_custom.trxc** _ file.</span></span> <span data-ttu-id="7264e-155">이 정의는 사용자 정의 이벤트 4096의 이름을 ‘_\*First_User_Event\*\*’로 지정하고, 두 글자로 된 약어 **FE** 를 지정하고, 아이콘의 위쪽 부분을 빨간색으로 지정하고, 아래쪽 부분을 녹색으로 지정하고, 정보 필드 이름을 **First_Info1**, **First_Info2**, **First_Info3** 및 **First_Info4** 로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-155">This definition gives user-defined event 4096 the name _\*First_User_Event\*\*, specifies a two-letter abbreviation of **FE**, makes the top portion of the icon red, the bottom portion of the icon green, and names the information fields as **First_Info1**, **First_Info2**, **First_Info3**, and **First_Info4**.</span></span> <span data-ttu-id="7264e-156">사용자 정의 이벤트 4098은 **_tracex_custom.trxc_** 의 6번째 줄에서 유사하게 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-156">User-defined event 4098 is defined similarly at line 6 of **_tracex_custom.trxc_**.</span></span>

<span data-ttu-id="7264e-157">![사용자 정의 이벤트에 대한 예제 정의의 스크린샷입니다.](./media/user-guide/10.4.png)
**그림 31**</span><span class="sxs-lookup"><span data-stu-id="7264e-157">![Screenshot of the example definitions for the user-defined events.](./media/user-guide/10.4.png)
**FIGURE 31**</span></span>

<span data-ttu-id="7264e-158">초기화하는 동안 TraceX가 \***tracex_custom.trxc** _ 파일을 읽기 때문에, 사용자 지정 아이콘 정의를 적용하려면 TraceX를 종료하고 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-158">Since the \***tracex_custom.trxc** _ file is read by TraceX during initialization, TraceX must be exited and restarted before the custom icon definitions can take effect.</span></span> <span data-ttu-id="7264e-159">그림 32는 _\*_tracex_custom.trxc_\*\*에서 정의된 사용자 지정 이벤트 아이콘이 있는 사용자 정의 이벤트 452 및 453의 TraceX 표시를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-159">Figure 32 shows the TraceX display of user-defined events 452 and 453 with the custom event icons defined in _\*_tracex_custom.trxc_\*\*.</span></span>

<span data-ttu-id="7264e-160">![사용자 지정 이벤트 아이콘이 있는 사용자 정의 이벤트의 TraceX 표시에 대한 스크린샷입니다.](./media/user-guide/10.5.png)
**그림 32**</span><span class="sxs-lookup"><span data-stu-id="7264e-160">![Screenshot of the TraceX display of user defined events with the custom event icons.](./media/user-guide/10.5.png)
**FIGURE 32**</span></span>

<span data-ttu-id="7264e-161">사용자 지정 이벤트 정의의 추가 정보는 두 번 클릭하거나, 마우스를 위에 놓거나, 현재 이벤트 단추를 클릭하여 선택한 이벤트에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-161">The additional information in the custom event definition is shown when the event you select using a double-click, mouse-over, or clicking the current event button.</span></span> <span data-ttu-id="7264e-162">그림 33은 이벤트 452에서 두 번 클릭하여 선택하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-162">Figure 33 shows the double-click selection on event 452.</span></span> <span data-ttu-id="7264e-163">이벤트 이름 및 정보 필드는 ***tracex_custom.trxc*** 에 추가된 샘플 정의와 모두 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="7264e-163">The event name and information fields all match the sample definition that was added to ***tracex_custom.trxc***.</span></span>

<span data-ttu-id="7264e-164">![이벤트의 두 번 클릭 선택에 대한 스크린샷입니다.](./media/user-guide/10.6.png)
**그림 33**</span><span class="sxs-lookup"><span data-stu-id="7264e-164">![Screenshot of the double-click selection on an event.](./media/user-guide/10.6.png)
**FIGURE 33**</span></span>
