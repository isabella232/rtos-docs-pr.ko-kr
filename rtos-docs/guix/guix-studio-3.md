---
title: GUIX Studio 설명
description: 이 챕터에서는 GUIX Studio 시스템 분석 도구에 대한 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 89bbcd51c22dddef6e420750e8c8805a66344335
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811185"
---
# <a name="chapter-3-description-of-guix-studio"></a><span data-ttu-id="9521d-103">챕터 3: GUIX Studio 설명</span><span class="sxs-lookup"><span data-stu-id="9521d-103">Chapter 3: Description of GUIX Studio</span></span>

<span data-ttu-id="9521d-104">이 챕터에서는 GUIX Studio 시스템 분석 도구에 대한 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-104">This chapter contains a description of the GUIX Studio system analysis tool.</span></span> <span data-ttu-id="9521d-105">GUI의 전체 기능에 대한 설명을 이 챕터에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-105">A description of the overall functionality of the GUI is found in this chapter.</span></span> 

## <a name="guix-studio-views"></a><span data-ttu-id="9521d-106">GUIX Studio 보기</span><span class="sxs-lookup"><span data-stu-id="9521d-106">GUIX Studio Views</span></span>

<span data-ttu-id="9521d-107">GUIX Studio UI에는 ***도구 모음** _, _*_프로젝트 보기_*_, _*_속성 보기_*_, _*_대상 보기_*_, _*_리소스 보기_\*_ , 이상 5가지 주요 영역이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-107">There are five principal areas of the GUIX Studio UI, namely the ***Toolbar** _, _*_Project View_*_, _*_Properties View_*_, _*_Target View_*_, and _*_Resource View_\*_.</span></span> <span data-ttu-id="9521d-108">_ \*_그림 2_\*\*는 기본 GUIX Studio UI를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-108">_ *_Figure 2_*\* shows the basic GUIX Studio UI.</span></span> <span data-ttu-id="9521d-109">각각의 보기는 이후 하위 섹션에서 추가로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-109">Each of the views is further discussed in the following sub-sections.</span></span>

![기본 GUIX Studio UI 스크린샷.](./media/guix-studio/image_10.png)

<span data-ttu-id="9521d-111">**그림 2**</span><span class="sxs-lookup"><span data-stu-id="9521d-111">**Figure 2**</span></span>

### <a name="title"></a><span data-ttu-id="9521d-112">제목</span><span class="sxs-lookup"><span data-stu-id="9521d-112">Title</span></span>

- <span data-ttu-id="9521d-113">GUIX Studio 18: 앞서 _ \*_그림 2_\*\*의 상단에 표시된 것과 같이 \***제목** _에는 GUIX Studio 버전과 현재 열린 프로젝트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-113">GUIX Studio 18: The ***Title** _ displays the GUIX Studio version as well as the currently open project, as shown at the top of _ *_Figure 2_** previously.</span></span>

### <a name="toolbar"></a><span data-ttu-id="9521d-114">도구 모음</span><span class="sxs-lookup"><span data-stu-id="9521d-114">Toolbar</span></span>

<span data-ttu-id="9521d-115">***도구 모음** _은 _*_그림 3_\*\*과 같이 GUIX Studio 개발자가 사용 가능한 단추가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-115">The ***Toolbar** _ shows the buttons available to the GUIX Studio developer, as shown in _*_Figure 3_\*\*.</span></span>

![GUIX Studio 도구 모음 스크린샷.](./media/guix-studio/image11.jpg)

<span data-ttu-id="9521d-117">**그림 3**</span><span class="sxs-lookup"><span data-stu-id="9521d-117">**Figure 3**</span></span>

<span data-ttu-id="9521d-118">도구 모음 단추는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-118">The toolbar buttons are defined as follows:</span></span>

![새 단추](./media/guix-studio/new-button.png) <span data-ttu-id="9521d-120">새 GUIX Studio 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-120">Creates a new GUIX Studio project</span></span>

![열기 단추](./media/guix-studio/open-button.png) <span data-ttu-id="9521d-122">기존 GUIX Studio 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-122">Opens an existing GUIX Studio project</span></span>

![저장 단추](./media/guix-studio/save-button.png) <span data-ttu-id="9521d-124">프로젝트를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-124">Saves the project</span></span>

![잘라내기 단추](./media/guix-studio/cut-button.png) <span data-ttu-id="9521d-126">자식 요소를 포함하여 선택한 위젯을 잘라냅니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-126">Cut widget selected, including children</span></span>

![복사 단추](./media/guix-studio/copy-button.png) <span data-ttu-id="9521d-128">자식 요소를 포함하여 선택한 위젯을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-128">Copy selected widget, including children</span></span>

![붙여넣기 단추](./media/guix-studio/paste-button.png) <span data-ttu-id="9521d-130">위젯과 자식 요소를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-130">Paste widget and children</span></span>

![왼쪽 맞춤 단추](./media/guix-studio/left-align-button.png) <span data-ttu-id="9521d-132">선택한 위젯을 왼쪽에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-132">Left-align selected widgets</span></span>

![오른쪽 맞춤 단추](./media/guix-studio/right-align-button.png) <span data-ttu-id="9521d-134">선택한 위젯을 오른쪽에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-134">Right-align selected widgets</span></span>

![위쪽 맞춤 단추](./media/guix-studio/top-align-button.png) <span data-ttu-id="9521d-136">선택한 위젯을 위쪽에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-136">Top-align selected widgets</span></span>

![아래쪽 맞춤 단추](./media/guix-studio/bottom-align-button.png) <span data-ttu-id="9521d-138">선택한 위젯을 아래쪽에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-138">Bottom-align selected widgets</span></span>

![세로로 띄우기 단추](./media/guix-studio/space-vertically-button.png) <span data-ttu-id="9521d-140">선택한 위젯을 세로로 동일한 간격으로 띄웁니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-140">Equally space selected widgets vertically</span></span>

![가로로 띄우기 단추](./media/guix-studio/space-horizontally-button.png) <span data-ttu-id="9521d-142">선택한 위젯을 가로로 동일한 간격으로 띄웁니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-142">Equally space selected widgets horizontally</span></span>

![동일 너비 단추](./media/guix-studio/equal-width-button.png) <span data-ttu-id="9521d-144">선택한 위젯을 동일한 너비로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-144">Make selected widgets equal width</span></span>

![동일 높이 단추](./media/guix-studio/equal-height-button.png) <span data-ttu-id="9521d-146">선택한 위젯을 동일한 높이로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-146">Make selected widgets equal height</span></span>

![앞으로 이동 단추](./media/guix-studio/move-front-button.png) <span data-ttu-id="9521d-148">선택한 위젯을 앞으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-148">Move selected widgets to front</span></span>

![뒤로 이동 단추](./media/guix-studio/move-back-button.png) <span data-ttu-id="9521d-150">선택한 위젯을 뒤로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-150">Move selected widgets to back</span></span>

![크기 조정 단추](./media/guix-studio/size-button.png) <span data-ttu-id="9521d-152">선택한 위젯의 크기를 콘텐츠 축소 대상 화면에 맞춰 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-152">Size selected widget to content Zoom out target screen</span></span>

![축소 단추](./media/guix-studio/zoom-out-button.png) <span data-ttu-id="9521d-154">대상 화면을 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-154">Zoom out target screen</span></span>

![확대 단추](./media/guix-studio/zoom-in-button.png) <span data-ttu-id="9521d-156">대상 화면을 확대합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-156">Zoom in target screen</span></span>

![기록 단추](./media/guix-studio/record-button.png) <span data-ttu-id="9521d-158">매크로를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-158">Record Macro</span></span>

![재생 단추](./media/guix-studio/playback-button.png) <span data-ttu-id="9521d-160">매크로를 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-160">Playback Macro</span></span>

![실행 단추](./media/guix-studio/run-button.png) <span data-ttu-id="9521d-162">애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-162">Run Application</span></span>

![정보 단추](./media/guix-studio/about-button.png) <span data-ttu-id="9521d-164">GUIX Studio 정보</span><span class="sxs-lookup"><span data-stu-id="9521d-164">About GUIX Studio</span></span>

### <a name="project-view"></a><span data-ttu-id="9521d-165">프로젝트 보기</span><span class="sxs-lookup"><span data-stu-id="9521d-165">Project View</span></span>

<span data-ttu-id="9521d-166">\***프로젝트 보기** _에는 포함된 UI를 구성하는 계층적 목록 GUIX 개체가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-166">The \***Project View** _ shows the hierarchical list GUIX objects that comprise the embedded UI.</span></span> <span data-ttu-id="9521d-167">부모 개체를 클릭하고 _\*_삽입_\*_ 메뉴에서 개체를 선택(또는 개체를 마우스 오른쪽 단추로 클릭하고 표시되는 메뉴에서 선택)하여 새 GUIX 개체를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-167">New GUIX objects can be added by clicking on the parent object and then selecting an object from the _*_Insert_*_ menu (or by right-clicking on the object and selecting from the right-click menu).</span></span> <span data-ttu-id="9521d-168">아래 _\*_그림 4_*_ 는 GUIX Studio _*_프로젝트 보기_\*\*를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-168">_*_Figure 4_*_ below shows the GUIX Studio _\*_Project View_\*\*.</span></span>

![GUIX Studio 프로젝트 보기 스크린샷.](./media/guix-studio/image_35.png)

<span data-ttu-id="9521d-170">**그림 4**</span><span class="sxs-lookup"><span data-stu-id="9521d-170">**Figure 4**</span></span>

### <a name="properties-view"></a><span data-ttu-id="9521d-171">속성 보기</span><span class="sxs-lookup"><span data-stu-id="9521d-171">Properties View</span></span>

<span data-ttu-id="9521d-172">***속성 보기** _에는 현재 선택한 GUIX 개체에 대한 자세한 속성 정보가 표시됩니다. 개체는 _*_프로젝트 보기_*_ 를 통해 선택하거나 _*_대상 보기_\*_ 에서 개체를 직접 클릭하여 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-172">The ***Properties View** _ shows detailed property information of the currently selected GUIX object, which can be selected via the _*_Project View_*_ or by clicking directly on the object in the _*_Target View_\*_.</span></span> <span data-ttu-id="9521d-173">아래 _\*_그림 5_*_ 는 GUIX Studio _*_속성 보기_\*\*를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-173">_*_Figure 5_*_ below shows the GUIX Studio _\*_Properties View_\*\*.</span></span>

![GUIX Studio 속성 보기 스크린샷.](./media/guix-studio/image36.jpg)

<span data-ttu-id="9521d-175">**그림 5**</span><span class="sxs-lookup"><span data-stu-id="9521d-175">**Figure 5**</span></span>

### <a name="target-view"></a><span data-ttu-id="9521d-176">대상 보기</span><span class="sxs-lookup"><span data-stu-id="9521d-176">Target View</span></span>

<span data-ttu-id="9521d-177">\***대상 보기** _는 WYSIWYG 화면 디자인 및 레이아웃 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-177">The \***Target View** _ is the WYSIWYG screen design and layout area.</span></span> <span data-ttu-id="9521d-178">이 보기는 대상 하드웨어에서 사용할 수 있는 물리적 디스플레이를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-178">This view is meant to represent the physical display or displays available on your target hardware.</span></span> <span data-ttu-id="9521d-179">간편한 마우스 작업을 통해 개체를 선택, 이동, 크기 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-179">Objects can be selected, moved, resized, etc. via simple mouse operations.</span></span> <span data-ttu-id="9521d-180">또한 대상 보기의 선택한 개체에서 조정 및 Z 순서 단추가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-180">In addition, alignment and Z-order button operations are available on selected objects in the Target View.</span></span> <span data-ttu-id="9521d-181">_\*_대상 보기_\*_ 에서 개체를 선택하면 _\*_속성 보기_\*_ 에서 해당 개체의 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-181">Selecting an object in the _*_Target View_*_ will also result in the properties for that object to be displayed in the _*_Properties View_*_.</span></span> <span data-ttu-id="9521d-182">아래 _\*_그림 6_*_ 은 GUIX Studio _*_대상 보기_\*\*를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-182">_*_Figure 6_*_ below shows the GUIX Studio _\*_Target View_\*\*.</span></span>

![GUIX Studio 대상 보기 스크린샷.](./media/guix-studio/image_37.png)

<span data-ttu-id="9521d-184">**그림 6**</span><span class="sxs-lookup"><span data-stu-id="9521d-184">**Figure 6**</span></span>

### <a name="resource-view"></a><span data-ttu-id="9521d-185">리소스 뷰</span><span class="sxs-lookup"><span data-stu-id="9521d-185">Resource View</span></span>

<span data-ttu-id="9521d-186">\***리소스 보기** _는 각 디스플레이에 정의되는 애플리케이션 화면에 제공되는 리소스(색, 글꼴, pixelmap, 문자열)를 관리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-186">The \***Resource View** _ is used to manage the resources (colors, fonts, pixelmaps, and strings) available to applications screens defined for each display.</span></span> <span data-ttu-id="9521d-187">리소스 보기 그룹 헤더를 클릭하여 각 그룹을 확장하고 그룹 콘텐츠를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-187">You can click on the resource view group headers to expand each group and examine the group contents.</span></span> <span data-ttu-id="9521d-188">아래 _\*_그림 7_*_ 은 GUIX Studio _*_리소스 보기_\*\*를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-188">_*_Figure 7_*_ below shows the GUIX Studio _\*_Resource View_\*\*.</span></span>

![GUIX Studio 리소스 보기 스크린샷.](./media/guix-studio/image38.jpg)

<span data-ttu-id="9521d-190">**그림 7**</span><span class="sxs-lookup"><span data-stu-id="9521d-190">**Figure 7**</span></span>

<span data-ttu-id="9521d-191">리소스 그룹의 제목은 현재 테마 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-191">The title of the resource groups indicates current theme name.</span></span> <span data-ttu-id="9521d-192">여러 테마가 제공되는 경우 위쪽 및 아래쪽 화살표를 클릭하여 테마를 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-192">If multi themes available, you are able to switch between themes by clicking on the up and down arrow.</span></span>

<span data-ttu-id="9521d-193">위의 보기에서 각 리소스 그룹은 그룹 헤더를 클릭하여 확장하거나 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-193">Each resource group in the view above can be expanded or collapsed by clicking on the group header.</span></span> <span data-ttu-id="9521d-194">각 리소스 그룹에 대한 자세한 설명은 다음 챕터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-194">A more detailed description of each resource groups follows in the next chapter.</span></span>

## <a name="the-guix-studio-project"></a><span data-ttu-id="9521d-195">GUIX Studio 프로젝트</span><span class="sxs-lookup"><span data-stu-id="9521d-195">The GUIX Studio Project</span></span>

<span data-ttu-id="9521d-196">GUIX Studio 프로젝트는 UI 화면 디자인 및 UI 리소스에 대한 정보를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-196">A GUIX Studio project maintains information about your UI screen design and UI resources.</span></span> <span data-ttu-id="9521d-197">프로젝트 데이터는 ".***gxp***" 확장자의 XML 서식 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-197">The project data is saved to an XML format file with the extension ".***gxp***".</span></span> <span data-ttu-id="9521d-198">프로젝트 파일은 XML 스키마 파일이므로 다른 모든 원본 파일과 비슷하게 버전 관리 제어 및 공유될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-198">Since the project file is an XML schema file, it can be versioned controlled and shared similar to any other source file.</span></span>

<span data-ttu-id="9521d-199">GUIX Studio를 처음 사용하는 경우 배포와 함께 제공된 예제 프로젝트 중 하나를 열거나 새 프로젝트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-199">When you first start using GUIX Studio, you will need to either open one of the example projects provided with the distribution or create a new project.</span></span> <span data-ttu-id="9521d-200">모든 작업은 프로젝트 데이터 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-200">All of your work is saved to the project data file.</span></span>

<span data-ttu-id="9521d-201">GUIX Studio는 ANSI C 원본 파일 또한 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-201">GUIX Studio also produces ANSI C source files.</span></span> <span data-ttu-id="9521d-202">이러한 원본 파일에는 애플리케이션 리소스 또는 디자인된 화면을 설명하는 데이터 구조가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-202">These source files contain either your application resources or data structures describing your designed screens.</span></span> <span data-ttu-id="9521d-203">GUIX Studio는 생성된 데이터 구조를 활용하여 애플리케이션 화면을 동적으로 만드는 것을 알고 있는 생성된 원본 파일 API 함수에도 이를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-203">GUIX Studio also writes to these generated source files API functions that know to utilize the generated data structures to dynamically create your application screens.</span></span> <span data-ttu-id="9521d-204">애플리케이션 소프트웨어는 제공된 API 함수를 호출하여 GUIX Studio 내에서 디자인한 화면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-204">Your application software will simply invoke the provided API functions to create the screens you have designed within GUIX Studio.</span></span>

<span data-ttu-id="9521d-205">사용자 인터페이스를 디자인하는 과정에서 GUIX Studio를 사용하여 디자인한 인터페이스를 빌드하고 실행할 수 있도록 하는 GUIX 호환 출력 파일을 정기적으로 생성하고자 할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-205">As you progress in designing your user interface, you will periodically want to use GUIX Studio to generate the GUIX compatible output files that will allow you to build and run the interface you have designed.</span></span> <span data-ttu-id="9521d-206">대상 하드웨어 또는 ThreadX 및 GUIX를 시뮬레이션하는 Windows 데스크톱에서 생성된 소스 파일을 컴파일 및 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-206">You can compile and run the generated source files for either your target hardware or on your Windows desktop that simulates ThreadX and GUIX.</span></span>

## <a name="guix-studio-project-organization"></a><span data-ttu-id="9521d-207">GUIX Studio 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="9521d-207">GUIX Studio Project Organization</span></span>

<span data-ttu-id="9521d-208">GUIX Studio를 효과적으로 사용하는 방법을 이해하고 GUIX Studio IDE의 프로젝트 보기에 제공되는 정보를 이해하는 데 있어 GUIX Studio 프로젝트의 기본 구성을 아는 것이 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-208">It is helpful to have some knowledge of the basic organization of a GUIX Studio project to understand how to use GUIX Studio effectively and to understand the information presented in the Project View of the GUIX Studio IDE.</span></span> <span data-ttu-id="9521d-209">프로젝트 보기는 프로젝트에 포함된 모든 정보의 요약을 시각적으로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-209">The Project View is a summary visual representation of all of the information contained in your project.</span></span>

<span data-ttu-id="9521d-210">프로젝트를 설명하기 전에 몇 가지 용어를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-210">Before describing the project, it is necessary to define few terms.</span></span> <span data-ttu-id="9521d-211">우선 **디스플레이** 라는 용어는 물리적 디스플레이 디바이스를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-211">First, we use the term **Display** to mean a physical display device.</span></span> <span data-ttu-id="9521d-212">대체로 LCD 디스플레이 디바이스를 사용하지만 다른 기술을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-212">This is most often an LCD display device but it could be using other technology.</span></span> <span data-ttu-id="9521d-213">다음 용어는 **화면** 으로, 최상위 GUIX 개체(일반적으로 GUIX 창) 및 연결된 모든 자식 요소를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-213">The next term is **Screen**, which mean a top-level GUIX object, usually a GUIX Window, and all of its associated child elements.</span></span> <span data-ttu-id="9521d-214">화면은 런타임에서 정의 및 수정할 수 있는 소프트웨어 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-214">A Screen is a software construct that can be defined and modified at runtime.</span></span> <span data-ttu-id="9521d-215">마지막으로 **테마** 는 리소스의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-215">Finally, a **Theme** is a collection of resources.</span></span> <span data-ttu-id="9521d-216">테마에는 조화롭고 최종 사용자에게 일관적인 외관을 제공하도록 디자인된 색 정의, 글꼴 정의 및 pixelmap 정의 표가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-216">A theme includes a table of color definitions, font definitions, and pixelmap definitions that are designed to work well together and present your end user with a consistent look and feel.</span></span>

<span data-ttu-id="9521d-217">프로젝트에는 프로젝트 이름, 지원되는 디스플레이의 수, 각 디스플레이의 해상도 및 색 형식, 지원되는 언어의 수, 지원되는 각 언어의 이름 등 전역 정보 세트가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-217">The project first includes a set of global information such as the project name, number of displays supported, the resolution and color format of each display, the number of languages supported, the name of each supported language.</span></span> <span data-ttu-id="9521d-218">프로젝트 이름은 프로젝트 보기에 표시되는 첫 번째 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-218">The project name is the first node displayed in the Project View.</span></span>

<span data-ttu-id="9521d-219">이후 프로젝트는 최대 4개의 물리적 디스플레이에 필요한 모든 정보와 각 디스플레이에 사용할 수 있는 화면과 리소스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-219">The project next organizes all of the information required for up to 4 physical displays and the screens and resources available to each display.</span></span> <span data-ttu-id="9521d-220">디스플레이 이름은 프로젝트 보기 트리의 다음 수준 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-220">The display names are the next level nodes in the Project View tree.</span></span>

<span data-ttu-id="9521d-221">GUIX Studio 애플리케이션의 고유한 기능은 각각 고유한 x, y 해상도, 색 형식, 화면 및 리소스를 포함하는 여러 물리적 디스플레이를 기본적으로 지원하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-221">A unique feature of the GUIX Studio application is built-in support for multiple physical displays, each with its own x,y resolution, color format, screens, and resources.</span></span> <span data-ttu-id="9521d-222">대다수의 GUIX 애플리케이션은 하나의 물리적 디스플레이만 활용하지만 이 기능은 여러 개의 동시 물리적 디스플레이를 지원하는 제품을 만드는 데 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-222">While the vast majority of GUIX applications utilize only one physical display, this capability is important for those making a product that must support multiple simultaneous physical displays.</span></span>

<span data-ttu-id="9521d-223">각 디스플레이 정의 아래에는 해당 디스플레이에 대해 정의된 최상위 창 또는 화면이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-223">Beneath each display definition are the top-level windows or screens defined for that display.</span></span> <span data-ttu-id="9521d-224">화면 정의는 각 화면에서 자식 위젯의 수와 중첩에 따라 모든 수준으로 중첩될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-224">The screen definitions can be nested to any level depending on the number and nesting of child widgets on each screen.</span></span>

<span data-ttu-id="9521d-225">이 화면 및 자식 위젯 구성은 프로젝트 보기에 그래픽 방식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-225">This screen and child widget organization is displayed in a graphical manner in the Project View.</span></span>

<span data-ttu-id="9521d-226">또한 각 디스플레이와 연결된 테마는 디스플레이에서 지원하는 테마와 각 테마를 구성하는 리소스 콘텐츠입니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-226">Also associated with each display are the Themes supported by the display and the resource content composing each Theme.</span></span> <span data-ttu-id="9521d-227">프로젝트에 여러 디스플레이가 포함된 경우 하나의 디스플레이를 선택하고 다른 디스플레이를 선택하면 리소스 보기의 콘텐츠가 변경되는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-227">If your project includes multiple displays, you will notice that the Resource View changes its content when you select one display and then another.</span></span> <span data-ttu-id="9521d-228">리소스 콘텐츠가 각 디스플레이에 연결되어 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-228">This is because the resource content is linked to each display.</span></span> <span data-ttu-id="9521d-229">색 형식은 다를 수 있지만, 사용하는 pixelmap, 색, 글꼴은 물리적 디스플레이마다 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-229">Not only the color format may be different, but the pixelmaps, colors, and fonts you choose to use may vary from one physical display to another.</span></span>

<span data-ttu-id="9521d-230">프로젝트에서 유지 관리되는 마지막 구성 요소는 각 디스플레이와 연결된 문자열 테이블 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-230">The final component maintained by the project is the string table data associated with each display.</span></span> <span data-ttu-id="9521d-231">디스플레이의 x, y 해상도는 크게 다를 수 있으므로, 문자열 데이터는 프로젝트에 정의된 각 디스플레이에 대해 독립적으로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="9521d-231">Since displays can be of very different x,y resolutions, the string data is maintained independently for each display defined in the project.</span></span>
