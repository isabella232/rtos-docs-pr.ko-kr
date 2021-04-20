---
title: 화면 흐름 정의
description: GUIX Studio는 화면 전환 논리의 자동 생성 및 실행을 지원합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 1c590725281c785181bcb4c5852346bc973c24d1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811113"
---
# <a name="chapter-7-defining-screen-flow"></a><span data-ttu-id="8226e-103">7장: 화면 흐름 정의</span><span class="sxs-lookup"><span data-stu-id="8226e-103">Chapter 7: Defining Screen Flow</span></span>

<span data-ttu-id="8226e-104">GUIX Studio는 화면 전환 논리의 자동 생성 및 실행을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-104">GUIX Studio supports automatic generation and execution of screen transition logic.</span></span> <span data-ttu-id="8226e-105">사용자는 그래픽 화면 흐름 다이어그램을 만들고 편집하여 화면 전환 논리를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-105">The user defines the screen transition logic by creating and editing a graphical screen flow diagram.</span></span> <span data-ttu-id="8226e-106">화면 흐름 다이어그램이 프로젝트에 추가되면 다음 두 가지 중요한 기능을 사용할 수 있습니다. 1) Studio 환경 내에서 애플리케이션을 실행할 수 있습니다. 2) 생성된 specifications.c 파일 내에서 지정된 화면 흐름을 구현하는 이벤트 처리기 및 화면 전환 논리를 Studio가 자동으로 생성하여 애플리케이션 프로그램에서 이 부담을 없앱니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-106">When a screen flow diagram is added to the project, it enables two important features: 1) The application can be executed from within the Studio environment and 2) Studio automatically generates event handlers and screen transition logic to implement the designated screen flow within the generated specifications.c file, removing this burden from the application program.</span></span> 

<span data-ttu-id="8226e-107">Studio 환경 내의 데스크톱에서 애플리케이션을 실행하면 애플리케이션을 실행하기 위해 컴파일/링크 주기를 거치지 않아도 되므로 시간을 절약할 수 있는 편리한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-107">Running the application on your desktop from within the Studio environment is a handy feature which saves time in that you are not required to go through a compile/link cycle to execute your application.</span></span> <span data-ttu-id="8226e-108">애플리케이션을 컴파일하지 않고 수행할 수 있는 작업에는 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-108">There are of course limitations to what can be done without compiling the application.</span></span> <span data-ttu-id="8226e-109">GUIX Studio 환경 내에서 애플리케이션을 실행하는 경우 사용자 지정 그리기 함수, 사용자 지정 이벤트 처리기 및 복잡한 이벤트 처리를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-109">Custom drawing functions, custom event handlers, and complex event handling are not available when running the application from within the GUIX Studio environment.</span></span> <span data-ttu-id="8226e-110">그러나 이 기능을 사용하면 한 화면에서 다른 화면으로 전환을 실행할 화면 전환 논리와 프로그램 애니메이션을 자동으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-110">Still, this capability allows you to auto-generate screen transition logic, and program animations to be executed to transition from one screen to another.</span></span> <span data-ttu-id="8226e-111">이러한 효과와 애니메이션은 GUIX Studio 환경 내에서 직접 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-111">These effects and animations can be observed directly from within the GUIX Studio environment.</span></span>

<span data-ttu-id="8226e-112">다음 단락에서 설명하는 화면 흐름, 트리거 및 작업을 정의하는 경우 Studio 환경 내에서 UI를 실행하도록 설정하는 것은 물론, GUIX Studio에서 이벤트를 처리하고 해당 이벤트를 기반으로 한 화면에서 다른 화면으로 전환하는 등의 작업을 수행하는 논리를 사양 파일 내에서 생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-112">Note that when you define screen flow, triggers, and actions which we will describe in the following paragraphs, you are not only enabling the execution of your UI from within the Studio environment, but you are also enabling GUIX Studio to generate logic within your specifications file that will handle events and take actions based on those events, such as transitioning from one screen to another.</span></span>

## <a name="configuring-screen-flow"></a><span data-ttu-id="8226e-113">화면 흐름 구성</span><span class="sxs-lookup"><span data-stu-id="8226e-113">Configuring Screen Flow</span></span>

<span data-ttu-id="8226e-114">Studio 환경 내에서 애플리케이션을 실행하기 전에 몇 가지를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-114">Before an application can be executed from within the Studio environment a few things must be defined.</span></span> <span data-ttu-id="8226e-115">먼저, 프로그램 시작 시 표시되어야 하는 최상위 화면을 Studio 속성 보기에서 "시작 시 표시" 속성을 선택하여 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-115">First, the top level screen or screens that should be displayed at program startup must be indicated by selecting the "Visible at Startup" property in the Studio properties view.</span></span> <span data-ttu-id="8226e-116">이 플래그는 프로그램이 시작될 때 이 화면이 처음에 표시되어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-116">This flag indicates that this screen should initially be displayed when the program starts.</span></span> <span data-ttu-id="8226e-117">필요한 경우 둘 이상의 화면에서 이러한 지정을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-117">More than one screen can have this designation if desired.</span></span>

<span data-ttu-id="8226e-118">시작할 때 표시되는 화면을 정의한 후 UI 애플리케이션이 화면에서 화면으로 이동하는 방법을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-118">After defining the screen(s) which are visible at startup, the user can define how the UI application will flow from screen to screen.</span></span> <span data-ttu-id="8226e-119">GUIX Studio는 화면 전환 논리를 정의할 수 있는 그래픽 화면 흐름 다이어그램을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-119">GUIX Studio provides a graphical screen flow diagram to define screen transition logic.</span></span> <span data-ttu-id="8226e-120">메뉴 항목인 ***구성, 화면 흐름** _을 선택하면 화면 흐름 편집 대화 상자가 표시됩니다(_*_그림 30_\*\*의 스크린 샷 참조).</span><span class="sxs-lookup"><span data-stu-id="8226e-120">Simply select the menu selection ***Configure, Screen Flow** _ to bring up screen flow edit dialog, see the screen shot in _*_Figure 30_\*\*.</span></span>

![GUIX Studio 화면 흐름 대화 상자 스크린샷](./media/guix-studio/config_screen_flow.png)

<span data-ttu-id="8226e-122">**그림 30**</span><span class="sxs-lookup"><span data-stu-id="8226e-122">**Figure 30**</span></span>

<span data-ttu-id="8226e-123">프로젝트에 정의된 각 최상위 화면은 화면 이름이 표시된 상자로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-123">Each top-level screen defined in the project will be shown as a box showing the screen name.</span></span> <span data-ttu-id="8226e-124">이 상자는 프로젝트에 정의된 각 최상위 화면을 나타내는 자리 표시자입니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-124">This box is a placeholder representing each top-level screen defined in the project.</span></span> <span data-ttu-id="8226e-125">이러한 상자는 원하는 대로 이동하고 크기를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-125">These boxes can be moved and resized as desired.</span></span> <span data-ttu-id="8226e-126">한 최상위 화면에서 다른 화면으로의 전환이 정의된 경우 두 화면 사이에 화살표가 있는 연결선이 표시되어 한 화면에서 다른 화면으로의 전환을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-126">When a transition from one top-level screen to another has been defined, a connection line with an arrow head between two screens will be shown to indicate transitions from one screen to another.</span></span>

<span data-ttu-id="8226e-127">화면 흐름 다이어그램 왼쪽의 트리 뷰에는 각 최상위 화면이 표시되며 여기서 화면 흐름 다이어그램에서 그려야 하는 최상위 화면을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-127">The tree view in left-side of the screen-flow diagram shows each top-level screen and you are able to select which top-level screens should be drawn in the screen-flow diagram.</span></span>

<span data-ttu-id="8226e-128">화면 흐름 다이어그램은 스크롤할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-128">The screen-flow diagram is scrollable.</span></span> <span data-ttu-id="8226e-129">화면 블록을 아래쪽과 오른쪽으로 보이는 영역 밖으로 끌어 스크롤 가능한 창을 확대할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-129">You are able to drag any screen block down and right outside the visible area to enlarge the scrollable window.</span></span> <span data-ttu-id="8226e-130">스크롤 가능한 창이 확대된 후에는 마우스 휠을 아래로 스크롤하여 보이는 영역에 맞게 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-130">Once your scrollable window is enlarged, you are able to zoom out to make it fit the visible area by scrolling the mouse wheel down.</span></span> <span data-ttu-id="8226e-131">스크롤 가능한 창이 축소된 경우에는 마우스 휠을 위로 스크롤하여 모든 블록이 표시될 만큼 크게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-131">If the scrollable window is zoomed out, you are able to make it big enough to hold all of blocks by scrolling the mouse wheel up.</span></span>

<span data-ttu-id="8226e-132">화면에 대한 전환을 정의하려면 해당 화면의 자리 표시자를 마우스 오른쪽 단추로 클릭하여 트리거 목록 편집 대화 상자를 표시합니다(***그림 31*** 참조).</span><span class="sxs-lookup"><span data-stu-id="8226e-132">To define transitions for a screen, right click on the placeholder for that screen to bring up a Edit Trigger List dialog, see ***Figure 31***.</span></span>

![GUIX Studio 트리거 목록 편집 대화 상자 스크린샷](./media/guix-studio/edit_trigger_list.png)

<span data-ttu-id="8226e-134">**그림 31**</span><span class="sxs-lookup"><span data-stu-id="8226e-134">**Figure 31**</span></span>

<span data-ttu-id="8226e-135">트리거 편집 대화 상자에는 화면 전환을 트리거하는 사용자가 정의한 이벤트가 나열됩니다. 이러한 이벤트 트리거를 호출하는 이유가 바로 이것입니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-135">The trigger edit dialog list the events that the user has defined that will trigger a screen transition, which is why we call these events triggers.</span></span> <span data-ttu-id="8226e-136">트리거는 일반적으로 선택한 화면의 하나 이상의 자식 위젯에 의해 생성된 신호입니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-136">Triggers are normally signals generated by one or more child widgets of the selected screen.</span></span>

<span data-ttu-id="8226e-137">새 트리거를 정의하려면 트리거 목록 편집 대화 상자에서 ***새 트리거 추가** _ 단추를 선택하여 _*_그림 32_\*\*에 표시된 트리거 추가 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-137">To define a new trigger, select the ***Add New Trigger** _ button in the Edit Trigger List  dialog to bring up Add Trigger dialog shown in _*_Figure 32_\*\*.</span></span>

![GUIX Studio 트리거 추가 대화 상자 스크린샷](./media/guix-studio/add_trigger_for.png)

<span data-ttu-id="8226e-139">**그림 32**</span><span class="sxs-lookup"><span data-stu-id="8226e-139">**Figure 32**</span></span>

<span data-ttu-id="8226e-140">새 작업 세트를 트리거할 이벤트 유형을 정의하고 해당 트리거 이벤트를 수신할 때 실행될 작업을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-140">You are able to define the event type that will trigger a new set of actions, and define the actions that will be executed when that trigger event is received.</span></span>

<span data-ttu-id="8226e-141">새 애니메이션 화면 전환을 트리거하는 데 사용할 이벤트 유형을 정의한 후 이 새 트리거를 저장하면 트리거 목록 편집 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-141">Once you define the event type that you want to use to trigger a new animation screen transition, save this new trigger and it will be displayed in the Edit Trigger List dialog.</span></span>

<span data-ttu-id="8226e-142">트리거 목록 편집 대화 상자에서 이벤트를 선택하고 ***트리거 이벤트 편집*** 단추를 선택하면 수행할 관련 작업을 수정하지 않고 이 이벤트를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-142">You can modify this event (without modifying the related actions to be taken) by selecting the event in the Edit Trigger List dialog and selecting the ***Edit Trigger Event*** button.</span></span>

<span data-ttu-id="8226e-143">마찬가지로 이벤트를 선택하고 ***선택한 트리거 삭제*** 단추를 클릭하면 목록에서 트리거 이벤트를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-143">Likewise, you can remove any trigger event from the list by selecting the event and clicking on the ***Delete Selected Trigger*** button.</span></span>

<span data-ttu-id="8226e-144">특정 트리거 이벤트에 따라 발생해야 하는 애니메이션 또는 화면 전환을 지정하려면 이벤트 트리거를 선택하고 ***작업 편집*** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-144">To specify the animation or screen transition that should occur based on a particular trigger event, select that trigger event and click the ***Edit Action(s)*** button.</span></span> <span data-ttu-id="8226e-145">각 정의된 트리거를 기반으로 둘 이상의 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-145">Note that you can fire off more than one action based on each defined trigger.</span></span>

<span data-ttu-id="8226e-146">**작업 편집** 단추를 누르면 그림 33의 트리거에 대한 작업 편집 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-146">The **Edit Action(s)** button brings up the Edit Actions for Trigger dialog, shown in Figure 33:</span></span> 

![GUIX Studio 트리거에 대한 작업 편집 대화 상자 스크린샷](./media/guix-studio/edit_actions_for_trigger.png)

<span data-ttu-id="8226e-148">**그림 33**</span><span class="sxs-lookup"><span data-stu-id="8226e-148">**Figure 33**</span></span>

<span data-ttu-id="8226e-149">이 대화 상자를 사용하여 이 트리거 이벤트를 기반으로 구현할 작업 수를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-149">This dialog allows you to define any number of actions to implement based on this trigger event.</span></span> <span data-ttu-id="8226e-150">각 작업 정의를 시각적 애니메이션 또는 전환과 연결하는 데 도움이 되는 의미 있는 이름을 각 작업에 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-150">You can give each action a meaningful name to help you associate each action definition with a visual animation or transition.</span></span> <span data-ttu-id="8226e-151">위의 예제에서는 “fade_in_text_screen” 및 “fade_out_button_screen”이라는 이름의 두 작업을 정의했습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-151">In the example above, we defined two actions named “fade_in_text_screen” and “fade_out_button_screen”.</span></span>

<span data-ttu-id="8226e-152">구현할 새 작업을 정의하려면 새 작업 추가 단추를 클릭하여 그림 34의 작업 선택 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-152">The define a new action to implement, click the Add New Action button, which brings up the Select Action dialog, Figure 34:</span></span>

![GUIX Studio 작업 선택 대화 상자 스크린샷](./media/guix-studio/select_action.png)

<span data-ttu-id="8226e-154">**그림 34**</span><span class="sxs-lookup"><span data-stu-id="8226e-154">**Figure 34**</span></span>

<span data-ttu-id="8226e-155">사용 가능한 작업 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-155">Available action types include:</span></span>

- <span data-ttu-id="8226e-156">**애니메이션**: 지정된 정보를 사용하여 애니메이션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-156">**Animation**: Start an animation with specified information.</span></span>
- <span data-ttu-id="8226e-157">**연결**: 부모 화면에 대상 화면을 연결합니다. 부모 화면을 지정하지 않으면 대상 화면이 루트 창에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-157">**Attach**: Attach the target screen to the parent screen, if the parent screen is not specified, the target screen will be attached to the root window.</span></span>
- <span data-ttu-id="8226e-158">**분리**: 대상 화면을 부모에서 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-158">**Detach**: Detach the target screen from its parent.</span></span>
- <span data-ttu-id="8226e-159">**숨기기**: 대상 화면을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-159">**Hide**: Hide the target screen.</span></span>
- <span data-ttu-id="8226e-160">**화면 스택 팝**: 내부 화면 스택에서 화면을 팝합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-160">**Screen Stack Pop**: Pop a screen from the internal screen stack.</span></span>
- <span data-ttu-id="8226e-161">**화면 스택 푸시**: 내부 화면 스택에 화면 포인터를 푸시합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-161">**Screen Stack Push**: Push a screen pointer to the internal screen stack.</span></span>
- <span data-ttu-id="8226e-162">**화면 스택 초기화**: 내부 화면 스택의 모든 화면 포인터를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-162">**Screen Stack Reset**: Remove all screen pointers from the internal screen stack.</span></span>
- <span data-ttu-id="8226e-163">**표시**: 대상 화면을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-163">**Show**: Show the target screen.</span></span>
- <span data-ttu-id="8226e-164">**토글**: 대상 화면을 현재 화면의 부모에 연결하고 부모에서 현재 화면을 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-164">**Toggle**: Attach the target screen to the current screen's parent, and detach the current screen from its parent.</span></span>
- <span data-ttu-id="8226e-165">**창 실행**: 대상 화면을 모달 형식으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-165">**Window Execute**: Modally executes the target screen.</span></span>
- <span data-ttu-id="8226e-166">**창 실행 중지**: 현재 화면의 실행을 모달 형식으로 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-166">**Window Execute Stop**: Exit modally execution of the current screen.</span></span>

<span data-ttu-id="8226e-167">선택한 트리거 이벤트를 기반으로 수행할 작업을 정의하면 해당 작업이 트리거에 대한 작업 편집 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-167">Once you have defined an action to take based on the selected trigger event, that action will be displayed in the Edit Actions for Trigger dialog.</span></span> <span data-ttu-id="8226e-168">그림 35에 표시된 것처럼 이 작업을 선택하여 해당 작업의 매개 변수를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-168">You can select this action to modify the parameters of that action as shown in Figure 35.</span></span>

![GUIX Studio 트리거에 대한 작업 편집 대화 상자 스크린샷](./media/guix-studio/edit_actions_for_trigger.png)

<span data-ttu-id="8226e-170">**그림 35**</span><span class="sxs-lookup"><span data-stu-id="8226e-170">**Figure 35**</span></span>

<span data-ttu-id="8226e-171">작업 유형이 애니메이션인 경우 실행할 슬라이드 및/또는 페이드 유형 애니메이션을 정의할 수 있는 애니메이션 매개 변수 세트가 오른쪽에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-171">If the action type is an animation, a set of animation parameters are displayed on the right to allow you to define a slide and/or fade type animation to be executed.</span></span> <span data-ttu-id="8226e-172">또한 애니메이션 작업이 완료되면 애니메이션을 부모에서 자동으로 분리해야 하는지, 아니면 내부 화면 스택에 푸시해야 하는지 결정할 수 있습니다. 이 기능은 다중 계층 메뉴 시스템을 정의할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-172">When an animation action is completed, you can also determine if the animation should be automatically detached from it’s parent and/or pushed to the internal screen stack, which is often useful when defining multi-layer menu systems.</span></span>

<span data-ttu-id="8226e-173">슬라이드 및 페이드 애니메이션의 경우 감속/가속 함수 선택 단추를 선택하여 사용할 감속/가속 함수를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-173">For slide and fade animations, you can also define the Easing Function to use by Selecting the Easing Func Select button.</span></span> <span data-ttu-id="8226e-174">감속/가속 함수는 실제 이동 이벤트에 보다 가깝게 모방하도록 디자인된 다양한 곡선입니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-174">Easing functions are various curves designed to more closely mimic real life movement events.</span></span> <span data-ttu-id="8226e-175">이 단추를 선택 하면 **감속/가속 함수 선택** 대화 상자(그림 36)가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-175">Selecting this button brings up the **Select Easing Function** dialog, Figure 36:</span></span>

![GUIX Studio 감속/가속 함수 선택 대화 상자 스크린샷](./media/guix-studio/easing_function_select.png)

<span data-ttu-id="8226e-177">**그림 36**</span><span class="sxs-lookup"><span data-stu-id="8226e-177">**Figure 36**</span></span>

<span data-ttu-id="8226e-178">하나의 트리거 이벤트와 연결할 여러 작업을 정의하는 경우 각 작업에 의미 있는 이름을 지정하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-178">If you are defining multiple actions to associate with one trigger event, it can be useful to assign each action a meaningful name.</span></span> <span data-ttu-id="8226e-179">작업 이름은 생성된 사양 파일 내에서 이벤트 및 작업 테이블을 정의하는 데 사용되므로 C 구문의 명명 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-179">Action names must follow C syntax naming rules, as these names will be used within the generated specifications file to define event and action tables.</span></span>

<span data-ttu-id="8226e-180">GUIX Studio 내에서 트리거 이벤트 및 작업을 정의하는 경우 이러한 이벤트를 처리하고 지정된 작업을 실행하기 위해 프로젝트 사양 파일 내에서 자동화된 이벤트 처리기가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-180">When you define trigger events and actions within GUIX Studio, automated event handlers are generated within your project specifications file to handle these events and execute the specified actions.</span></span> <span data-ttu-id="8226e-181">따라서 사용자가 정의한 사용자 지정 이벤트 처리기에 트리거 이벤트를 계속 전달하더라도 애플리케이션 코드에서 이러한 이벤트를 처리할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-181">This means that you do NOT need to handle these events in your application code, although the trigger events are still passed to any custom event handlers you have defined.</span></span> <span data-ttu-id="8226e-182">즉, Studio에서 생성된 이벤트 처리기가 사용자 지정 이벤트 처리기를 대체하는 대신 보강합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-182">In other words the Studio generated event handlers augment, rather than replace, your own custom event handlers.</span></span>

## <a name="running-the-application"></a><span data-ttu-id="8226e-183">애플리케이션 실행</span><span class="sxs-lookup"><span data-stu-id="8226e-183">Running the Application</span></span>

<span data-ttu-id="8226e-184">시작 화면 및 화면 흐름 다이어그램이 생성되면 도구 모음에서 "애플리케이션 실행"</span><span class="sxs-lookup"><span data-stu-id="8226e-184">Once startup screens and a screen flow diagram have been created, you can run your application within Studio by selecting the "Run Application"</span></span>

![애플리케이션 실행 단추 스크린샷](./media/guix-studio/image68.jpg)

<span data-ttu-id="8226e-186">단추를 선택하거나, 프로젝트 메뉴에서 편집 | 애플리케이션 실행을 선택하거나, 화면 흐름 편집 대화 상자 아래쪽에 있는 실행 단추를 선택하면 Studio 내에서 애플리케이션을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-186">button on the toolbar, selecting Edit | Run Application from the project menu, or by selecting the Run button at the bottom of the Edit Screen Flow dialog.</span></span>

<span data-ttu-id="8226e-187">애플리케이션을 실행하면 새 창에 "시작 시 표시" 표시로 지정한 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-187">When you run the application, you will see the screen(s) you have designated as "Visible At Startup" display within a new window.</span></span> <span data-ttu-id="8226e-188">이러한 화면의 자식 위젯은 완전히 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-188">The child widgets on these screen are fully operational.</span></span> <span data-ttu-id="8226e-189">단추를 클릭하고, 슬라이더를 작동하고, 휠 등을 스크롤할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-189">You can click on buttons, operate sliders and scroll wheels, etc..</span></span> <span data-ttu-id="8226e-190">이러한 위젯에 대한 사용자 지정 그리기 함수 또는 고객 이벤트 처리를 정의한 경우 이 모드에서 애플리케이션을 실행할 때는 이를 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-190">If you have defined custom drawing functions or customer event handling for any of these widgets, you will of course NOT see this when running the application in this mode.</span></span> <span data-ttu-id="8226e-191">그러나 트리거 이벤트 및 작업을 사용하여 화면 흐름 다이어그램을 정의한 경우에는 이러한 트리거를 작동할 수 있으며 사용자가 정의한 모든 애니메이션을 포함하여 사용자가 정의한 대로 화면을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8226e-191">But if you have defined a screen flow diagram with trigger events and actions, those triggers will be operational and your screens will transition as you have defined, including any animations that you may have defined.</span></span>
