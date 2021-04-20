---
title: GUIX Studio 설치 및 사용
description: 이 챕터에서는 GUIX Studio UI 시스템 디자인 도구의 설치, 설정, 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d7b5f94c26842b408ea1b00aeeb78e111bea3623
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811983"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a><span data-ttu-id="43d2c-103">2장 - GUIX Studio 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="43d2c-103">Chapter 2: Installation and Use of GUIX Studio</span></span>

<span data-ttu-id="43d2c-104">이 챕터에서는 GUIX Studio UI 시스템 디자인 도구의 설치, 설정, 사용과 관련된 다양한 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-104">This chapter contains a description of various issues related to installation, setup, and usage of the GUIX Studio UI system design tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="43d2c-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="43d2c-105">Product Distribution</span></span>

<span data-ttu-id="43d2c-106">GUIX Studio를 검색하거나 [GUIX Studio 페이지](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab)로 직접 이동하여 [Microsoft 앱 스토어](https://microsoft.com/store/apps) 에서 GUIX Studio 앱을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-106">You can obtain the GUIX Studio app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for GUIX Studio, or by going directly to [the GUIX Studio page](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="43d2c-107">그런 다음, 아래 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-107">Then do the following.</span></span>

1. <span data-ttu-id="43d2c-108">앱 스토어의 GUIX Studio 페이지에서 **가져오기** 또는 **설치** 단추를 클릭하여 GUIX Studio를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-108">From the GUIX Studio page in the App Store, click the **Get** or **Install** button to download GUIX Studio.</span></span>

1. <span data-ttu-id="43d2c-109">아래 그림에 표시된 것처럼 브라우저에 Microsoft Store를 열 것인지 묻는 메시지가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="43d2c-110">이 경우 **열기** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="43d2c-111">![열기를 선택하여 GUIX Studio를 설치합니다.](./media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="43d2c-111">![Choose Open to install GUIX Studio.](./media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="43d2c-112">설치가 완료되면 **시작** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-112">When the install finishes, choose the **Launch** button.</span></span>

1. <span data-ttu-id="43d2c-113">GUIX Studio가 처음 시작될 때 GUIX 리포지토리를 로컬 컴퓨터에 복제할지 여부를 묻는 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-113">The first time that GUIX Studio launches, it displays a dialog box asking if you want to clone the GUIX repo to your local computer.</span></span> <span data-ttu-id="43d2c-114">리포지토리를 복제하도록 선택하거나, 이미 리포지토리를 복제한 위치를 가리키거나, 리포지토리를 전혀 복제하지 않도록 선택할 수 있습니다(이 경우에는 컴퓨터에 예제 프로젝트 1개가 설치됨).</span><span class="sxs-lookup"><span data-stu-id="43d2c-114">You can either choose to clone the repository, point to where you have already cloned the repo, or choose not to clone the repo at all (in which case, one example project is installed on your computer).</span></span>
<span data-ttu-id="43d2c-115">![리포지토리를 복제하거나, 이미 복제된 리포지토리를 가리키거나, 건너뛰려면 선택합니다.](./media/guix-studio/clone-repo.png)</span><span class="sxs-lookup"><span data-stu-id="43d2c-115">![Choose to clone the repo, point to an already-cloned repo, or skip.](./media/guix-studio/clone-repo.png)</span></span>

> <span data-ttu-id="43d2c-116">!</span><span class="sxs-lookup"><span data-stu-id="43d2c-116">!</span></span>[!NOTE]
> <span data-ttu-id="43d2c-117">GUIX Stuido의 주 메뉴에서 **구성** 을 선택하고, **GUIX 리포지토리** 를 선택하여 언제든지 이 대화 상자로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-117">You can return to this dialog box at any time by choosing **Configure** from the main menu of GUIX Stuido, followed by **GUIX Repository**.</span></span>

<span data-ttu-id="43d2c-118">시작 프로세스가 완료되면 GUIX Studio를 사용할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-118">After the startup process is finished, you will be ready to use GUIX Studio.</span></span>

## <a name="using-guix-studio"></a><span data-ttu-id="43d2c-119">GUIX Studio 사용</span><span class="sxs-lookup"><span data-stu-id="43d2c-119">Using GUIX Studio</span></span>

<span data-ttu-id="43d2c-120">GUIX Studio를 사용하는 것은 간단합니다. "***시작***" 단추를 사용하여 GUIX studio를 실행하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-120">Using GUIX Studio is easy - simply run GUIX Studio via the "***Start***" button.</span></span> <span data-ttu-id="43d2c-121">이 시점에서 GUIX Studio UI가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-121">At this point you will observe the GUIX Studio UI.</span></span> <span data-ttu-id="43d2c-122">이제 GUIX Studio를 사용하여 그래픽으로 포함 된 UI를 만들 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-122">You are now ready to use GUIX Studio to graphically create your embedded UI.</span></span> <span data-ttu-id="43d2c-123">여기에서 GUIX 예제 프로젝트를 포함하여 새 프로젝트를 만들거나 기존 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-123">From here you create a new project or open an existing project, including the GUIX example projects.</span></span>

> [!NOTE]
> <span data-ttu-id="43d2c-124">확장명이 "**gxp**" 인 GUIX Studio 프로젝트 파일을 두 번 클릭하여 GUIX Studio를 자동으로 시작하고 참조된 프로젝트를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-124">You can also double-click on any GUIX Studio project file with an extension of "**gxp,**" which will automatically launch GUIX Studio and open the referenced project.</span></span>

## <a name="guix-studio-project-samples"></a><span data-ttu-id="43d2c-125">GUIX Studio 프로젝트 샘플</span><span class="sxs-lookup"><span data-stu-id="43d2c-125">GUIX Studio Project Samples</span></span>

<span data-ttu-id="43d2c-126">확장명 "***gxp** _"_ 를 포함하는 일련의 예제 GUIX Studio 프로젝트 파일은 설치의 "*_Sample_\*\*" 하위 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-126">A series of example GUIX Studio project files with the extension "\***gxp**_" are found in the "_\*_Samples_\*\*" sub-directory of your installation.</span></span> <span data-ttu-id="43d2c-127">이러한 미리 작성된 예제 프로젝트를 사용하면 GUIX Studio를 사용하는 데 익숙해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-127">These pre-built example projects will help you get comfortable with using GUIX Studio.</span></span>

<span data-ttu-id="43d2c-128">항상 표시되는 한 가지 예제 프로젝트 파일은 \***samples/demo_guix_simple/guix_simple. gxp** _ 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-128">One example project file that is always present is the file \***samples/demo_guix_simple/guix_simple.gxp** _.</span></span> <span data-ttu-id="43d2c-129">이 예제 프로젝트 파일은 이 문서의 _ \*_7장_\*\*에 설명된 간단한 GUIX UI의 정의를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="43d2c-129">This example project file shows the definition of a simple GUIX UI, as described in _ *_Chapter 7_*\* of this document.</span></span>

![GUIX Studio UI의 스크린샷](./media/guix-studio/image_10.png)

<span data-ttu-id="43d2c-131">**그림 1**</span><span class="sxs-lookup"><span data-stu-id="43d2c-131">**Figure 1**</span></span>

## <a name="keyboard-shortcuts"></a><span data-ttu-id="43d2c-132">바로 가기 키</span><span class="sxs-lookup"><span data-stu-id="43d2c-132">Keyboard Shortcuts</span></span>

- <span data-ttu-id="43d2c-133">**Ctrl + N:** 새 프로젝트</span><span class="sxs-lookup"><span data-stu-id="43d2c-133">**Ctrl + N:** New Project</span></span>
- <span data-ttu-id="43d2c-134">**Ctrl + O:** 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="43d2c-134">**Ctrl + O:** Open Project</span></span>
- <span data-ttu-id="43d2c-135">**Ctrl + S:** 프로젝트 저장</span><span class="sxs-lookup"><span data-stu-id="43d2c-135">**Ctrl + S:** Save Project</span></span>
- <span data-ttu-id="43d2c-136">**Ctrl + Shift + S:** 다른 이름으로 프로젝트 저장</span><span class="sxs-lookup"><span data-stu-id="43d2c-136">**Ctrl + Shift + S:** Save Project As</span></span>
- <span data-ttu-id="43d2c-137">**Alt + F4:** 끝내기</span><span class="sxs-lookup"><span data-stu-id="43d2c-137">**Alt + F4:** Exit</span></span>
