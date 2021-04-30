---
title: 2장 - Azure RTOS TraceX 설치 및 사용
description: 이 장에서는 Azure RTOS TraceX 시스템 분석 도구의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 05d7fe3df38c7e8a3480c8ea0d4922a109de9ede
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812390"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a><span data-ttu-id="3f181-103">2장 - Azure RTOS TraceX 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="3f181-103">Chapter 2 - Installation and use of Azure RTOS TraceX</span></span>

<span data-ttu-id="3f181-104">이 장에서는 Azure RTOS TraceX 시스템 분석 도구의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS TraceX system analysis tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="3f181-105">제품 배포</span><span class="sxs-lookup"><span data-stu-id="3f181-105">Product Distribution</span></span>

<span data-ttu-id="3f181-106">TraceX를 검색하거나 [TraceX 페이지](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab)로 직접 이동하여 [Microsoft 앱 스토어](https://microsoft.com/store/apps)에서 TraceX 앱을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-106">You can obtain the TraceX app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for TraceX, or by going directly to [the TraceX page](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="3f181-107">그런 다음, 다음을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-107">Then do the following.</span></span>

1. <span data-ttu-id="3f181-108">앱 스토어의 TraceX 페이지에서 **가져오기** 또는 **설치** 단추를 클릭하여 TraceX를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-108">From the TraceX page in the App Store, click the **Get** or **Install** button to install TraceX.</span></span>

1. <span data-ttu-id="3f181-109">아래 그림에 표시된 것처럼 브라우저에 Microsoft Store를 열 것인지 묻는 메시지가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="3f181-110">이 경우 **열기** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="3f181-111">![열기를 선택하여 TraceX를 설치합니다.](../guix/media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="3f181-111">![Choose Open to install TraceX.](../guix/media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="3f181-112">설치가 완료되면 **시작** 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-112">When the install finishes, choose the **Launch** button.</span></span> 

## <a name="using-tracex"></a><span data-ttu-id="3f181-113">TraceX 사용</span><span class="sxs-lookup"><span data-stu-id="3f181-113">Using TraceX</span></span>

<span data-ttu-id="3f181-114">TraceX를 사용하는 것은 TraceX 내에서 추적 파일을 여는 것만큼 쉽습니다!</span><span class="sxs-lookup"><span data-stu-id="3f181-114">Using TraceX is as easy as opening a trace file inside TraceX!</span></span> <span data-ttu-id="3f181-115">\***Start** _ 단추를 통해 TraceX를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-115">Run TraceX via the \***Start** _ button.</span></span> <span data-ttu-id="3f181-116">이 시점에서 TraceX GUI(그래픽 사용자 인터페이스)를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-116">At this point you will observe the TraceX graphic user interface (GUI).</span></span> <span data-ttu-id="3f181-117">이제 TraceX를 사용하여 기존 대상 추적 버퍼를 그래픽으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-117">You are now ready to use TraceX to graphically view an existing target trace buffer.</span></span> <span data-ttu-id="3f181-118">_ \*_파일 -> 열기_\*\*를 클릭한 다음, 이진 추적 파일을 입력하여 이 작업을 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-118">This is easily done by clicking _ *_File -> Open,_*\* then entering the binary trace file.</span></span>

>[!IMPORTANT]
><span data-ttu-id="3f181-119">*또한 확장명이 **trx** 인 추적 파일을 두 번 클릭하면 TraceX가 자동으로 시작됩니다.*</span><span class="sxs-lookup"><span data-stu-id="3f181-119">*You can also double-click on any trace file with an extension of **trx,** which will automatically launch TraceX.*</span></span>

![TraceX GUI의 스크린샷](./media/user-guide/screen_shot_8.png)

<span data-ttu-id="3f181-121">**그림 1**</span><span class="sxs-lookup"><span data-stu-id="3f181-121">**FIGURE 1**</span></span>

>[!IMPORTANT]
><span data-ttu-id="3f181-122">*ThreadX를 사용하여 대상에서 추적 버퍼를 생성하는 방법에 대한 지침은 **5장** 을 참조하세요.*</span><span class="sxs-lookup"><span data-stu-id="3f181-122">*Refer to **Chapter 5** for instructions on how to generate trace buffers on the target using ThreadX.*</span></span>

## <a name="tracex-examples"></a><span data-ttu-id="3f181-123">TraceX 예제</span><span class="sxs-lookup"><span data-stu-id="3f181-123">TraceX Examples</span></span>

<span data-ttu-id="3f181-124">TraceX 애플리케이션을 처음 실행하거나 TraceX 애플리케이션을 업데이트할 때 TraceX 예제 추적 파일 및 custom_events.trxc 파일을 로컬 머신의 사용자 정의 디렉터리에 설치하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-124">The first time you run the TraceX application, or when the TraceX application is updated, you will be prompted to install the TraceX example trace files and the custom_events.trxc file to a user-defined directory on your local machine.</span></span>

<span data-ttu-id="3f181-125">이 설치 단계를 완료한 후에는 확장명이 **trx** 인 추적 파일 예제는 설치 폴더의 **TraceFiles** 하위 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-125">After this installation step in completed, the example trace files with the extension **trx** are found in the **TraceFiles** subdirectory of your installation folder.</span></span> <span data-ttu-id="3f181-126">이러한 미리 작성된 예제는 애플리케이션과 함께 실행되는 ThreadX에서 생성된 추적 버퍼에 TraceX를 사용하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-126">These pre-built examples will help you get comfortable with using TraceX on the trace buffers generated by ThreadX running with your application.</span></span>

<span data-ttu-id="3f181-127">추적 파일의 한 가지 예제는 항상 \***demo_threadx.trx** _ 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-127">One example trace file always present is the file \***demo_threadx.trx** _.</span></span> <span data-ttu-id="3f181-128">이 예제 추적 파일은 __ThreadX 사용자 가이드\*의 6장에서 설명한 대로 표준 ThreadX 데모를 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f181-128">This example trace file shows the execution of the standard ThreadX demo, as described in Chapter 6 of the _ThreadX User Guide\*.</span></span>

![TraceX의 열기 대화 상자 스크린샷](./media/user-guide/screen_shot_9.png)

<span data-ttu-id="3f181-130">**그림 2**</span><span class="sxs-lookup"><span data-stu-id="3f181-130">**FIGURE 2**</span></span>
