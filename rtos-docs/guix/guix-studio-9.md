---
title: GUIX Studio 명령줄
description: GUIX Studio는 Studio 생성 출력 파일을 업데이트하는 데 필요한 빌드 파이프라인에 유용한 명령줄 호출을 제공합니다.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9f9bfc67c524a77b5bf736407bf2ca372ce98308
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811107"
---
# <a name="chapter-9-guix-studio-command-line"></a><span data-ttu-id="366ee-103">9장 - GUIX Studio 명령줄</span><span class="sxs-lookup"><span data-stu-id="366ee-103">Chapter 9: GUIX Studio Command Line</span></span>

<span data-ttu-id="366ee-104">GUIX Studio는 명령줄 호출을 지원합니다. 이 호출은 Studio 생성 출력 파일을 업데이트하는 데 필요한 빌드 파이프라인에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-104">GUIX Studio supports command-line invocation,  which is useful for build pipelines that are required to update of the Studio-generated output files.</span></span>

## <a name="command-line-usage"></a><span data-ttu-id="366ee-105">명령줄 사용법</span><span class="sxs-lookup"><span data-stu-id="366ee-105">Command-Line Usage</span></span>

<span data-ttu-id="366ee-106">**사용법:** guix_studio \[OPTION\] \[ARGUMENT\]</span><span class="sxs-lookup"><span data-stu-id="366ee-106">**Usage:** guix_studio \[OPTION\] \[ARGUMENT\]</span></span>

<span data-ttu-id="366ee-107">*.gxp* 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-107">Open the *.gxp* project.</span></span>

<span data-ttu-id="366ee-108">Studio 프로젝트를 열고 원하는 출력 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-108">Open the Studio project and generate desired output files.</span></span>


<span data-ttu-id="366ee-109">**예:**</span><span class="sxs-lookup"><span data-stu-id="366ee-109">**Examples:**</span></span>

`guix_studio demo.gxp`  
<span data-ttu-id="366ee-110">"demo.gxp" 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="366ee-110">Open "demo.gxp" project</span></span>


`guix_studio.exe –p demo.gxp`  
<span data-ttu-id="366ee-111">"demo.gxp" 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="366ee-111">Open "demo.gxp" project</span></span>


`guix_studio.exe –n –p demo.gxp`  
<span data-ttu-id="366ee-112">demo.gxp 프로젝트의 모든 출력 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-112">Generate all output files of demo.gxp project.</span></span>

`guix_studio.exe –n –r –p demo.gxp`  
<span data-ttu-id="366ee-113">demo.gxp 프로젝트의 리소스 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-113">Generate resource files of demo.gxp project</span></span>


## <a name="command-line-options"></a><span data-ttu-id="366ee-114">명령줄 옵션</span><span class="sxs-lookup"><span data-stu-id="366ee-114">Command-Line Options</span></span>

```C
***-n --nogui***  
```

<span data-ttu-id="366ee-115">"nogui" 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-115">The "nogui" option.</span></span> <span data-ttu-id="366ee-116">GUIX Studio에 창 UI 인터페이스를 시작하지 않고 실행하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-116">Tell GUIX Studio to run without starting the windowing UI interface.</span></span>

```C
***-o pathname***  
***--log***  
```

<span data-ttu-id="366ee-117">로그 옵션, 로그 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-117">Log option, specify a log file.</span></span>

```C
***-b***  
***--binary***  
```

<span data-ttu-id="366ee-118">이진 리소스 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-118">Binary resource option.</span></span> <span data-ttu-id="366ee-119">C 파일이 아닌 이진 리소스 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-119">Produces a binary resource file rather than a C file.</span></span>

```C
***-d display1, display2***  
***--display***  
```

<span data-ttu-id="366ee-120">표시 이름 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-120">Display names option.</span></span> <span data-ttu-id="366ee-121">이 옵션을 사용할 경우 지정된 표시 이름만 생성된 리소스 또는 사양 파일에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-121">If this option is used, then only the specified display names are included in any generated resource or specification files.</span></span> <span data-ttu-id="366ee-122">이 옵션을 사용하지 않으면 모든 표시가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-122">If this option is not used,  all displays are included.</span></span>

```C
***-t theme1, theme2***  
***--theme***  
```

<span data-ttu-id="366ee-123">테마 이름 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-123">Theme name(s) option.</span></span> <span data-ttu-id="366ee-124">이 옵션을 사용할 경우 지정된 테마 이름만 생성된 리소스 또는 사양 파일에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-124">If this option is used, then only the specified theme names are included in any generated resource or specification files.</span></span> <span data-ttu-id="366ee-125">이 옵션을 사용하지 않으면 모든 테마가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-125">If this option is not used, all themes are included.</span></span>

```C
***-l langage1, language2***  
***--language***  
```

<span data-ttu-id="366ee-126">언어 이름 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-126">Language name(s) option.</span></span> <span data-ttu-id="366ee-127">이 옵션을 사용할 경우 지정된 언어 이름이 생성된 리소스 또는 사양 파일에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-127">If this option is used,  the specified language names are included in the generated resource or specification files.</span></span> <span data-ttu-id="366ee-128">그렇지 않으면 모든 언어 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-128">Otherwise all language names are included.</span></span>

```C
***-r [filename]***  
***--resource***  
```

<span data-ttu-id="366ee-129">리소스 옵션은 Studio에서 이전에 지정된 표시, 테마 및 언어에 대한 리소스 파일을 생성하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-129">The resource option, specifies that Studio should produce a resource file for previously designated display(s), theme(s), and language(s).</span></span>

```C
***-s [filename]***  
***--specification***  
```

<span data-ttu-id="366ee-130">사양 옵션은 Studio에서 지정된 표시, 테마 및 언어에 대한 사양 파일을 생성하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-130">The specification option, specify that studio should produce a specification file for designated display(s), theme(s), and language(s).</span></span>

```C
***-p project_pathname***  
***--project***  
```

<span data-ttu-id="366ee-131">프로젝트 경로 이름 옵션은 로드할 예제 프로젝트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-131">Project pathname option, specify the example project to be loaded.</span></span>

```C
***-i [pathname]***  
***--import***  
```

<span data-ttu-id="366ee-132">xliff 또는 csv 서식 파일에서 문자열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-132">Import string from xliff or csv format file.</span></span>

<span data-ttu-id="366ee-133">***--big_endian***</span><span class="sxs-lookup"><span data-stu-id="366ee-133">***--big_endian***</span></span>  
<span data-ttu-id="366ee-134">big-endian 형식으로 리소스 데이터를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="366ee-134">Generate resource data in big-endian format.</span></span>
