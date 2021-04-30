---
title: Azure RTOS TraceX 사용자 가이드
description: 이 가이드는 Microsoft의 Microsoft Windows 기반 시스템 분석 도구인 Azure RTOS TraceX에 대한 포괄적인 정보를 포함합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 92d886b19a0c67292cd4f6a5f8bd7f9d3106374b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812685"
---
# <a name="about-this-guide"></a><span data-ttu-id="62249-103">이 가이드의 내용</span><span class="sxs-lookup"><span data-stu-id="62249-103">About this guide</span></span>

<span data-ttu-id="62249-104">이 가이드는 Microsoft Azure RTOS용 Microsoft Windows 기반 시스템 분석 도구인 Azure RTOS TraceX에 대한 포괄적인 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-104">This guide contains comprehensive information about Azure RTOS TraceX, the Microsoft Windows-based system analysis tool for Microsoft Azure RTOS.</span></span>

<span data-ttu-id="62249-105">Azure RTOS ThreadX RTOS(실시간 운영 체제) 및 추가 기능 구성 요소를 사용하는 포함된 실시간 소프트웨어 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="62249-105">It is intended for the embedded real-time software developer using Azure RTOS ThreadX Real-Time Operating System (RTOS) and add-on components.</span></span> <span data-ttu-id="62249-106">개발자는 표준 Azure RTOS ThreadX, Azure RTOS FileX 및 Azure RTOS NetX 개념을 숙지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-106">The developer should be familiar with standard Azure RTOS ThreadX Azure RTOS FileX, and Azure RTOS NetX concepts.</span></span>

## <a name="organization"></a><span data-ttu-id="62249-107">조직</span><span class="sxs-lookup"><span data-stu-id="62249-107">Organization</span></span>

- <span data-ttu-id="62249-108">[1장](chapter1.md) - Azure RTOS TraceX의 기본 개요를 포함하고 실시간 개발과의 관계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-108">[Chapter 1](chapter1.md) - contains an basic overview of Azure RTOS TraceX and describes its relationship to real-time development.</span></span>
- <span data-ttu-id="62249-109">[2장](chapter2.md) - Azure RTOS TraceX를 설치하고 사용하여 즉시 애플리케이션을 분석하는 기본 단계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-109">[Chapter 2](chapter2.md) - gives the basic steps to install and use Azure RTOS TraceX to analyze your application right out of the box.</span></span>
- <span data-ttu-id="62249-110">[3장](chapter3.md) - Azure RTOS TraceX의 주요 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-110">[Chapter 3](chapter3.md) - describes the main features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="62249-111">[4장](chapter4.md) - Azure RTOS TraceX의 성능 분석 기능에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-111">[Chapter 4](chapter4.md) - details performance analysis features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="62249-112">[5장](chapter5.md) - Azure RTOS TraceX에서 볼 수 있는 추적 버퍼를 생성하기 위해 Azure RTOS ThreadX, Azure RTOS FileX 및 Azure RTOS NetX를 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-112">[Chapter 5](chapter5.md) - describes how to set up Azure RTOS ThreadX, Azure RTOS FileX, and Azure RTOS NetX in order to generate a trace buffer that is viewable by Azure RTOS TraceX.</span></span>
- <span data-ttu-id="62249-113">[6장](chapter6.md) - Azure RTOS TraceX 이벤트에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-113">[Chapter 6](chapter6.md) - describes Azure RTOS TraceX events in detail.</span></span>
- <span data-ttu-id="62249-114">[7장](chapter7.md) - Azure RTOS FileX 이벤트에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-114">[Chapter 7](chapter7.md) - describes Azure RTOS FileX events in detail.</span></span>
- <span data-ttu-id="62249-115">[8장](chapter8.md) - Azure RTOS NetX 이벤트에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-115">[Chapter 8](chapter8.md) - describes Azure RTOS NetX events in detail.</span></span>
- <span data-ttu-id="62249-116">[9장](chapter9.md) - Azure RTOS USBX 이벤트에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-116">[Chapter 9](chapter9.md) - describes Azure RTOS USBX events in detail.</span></span>
- <span data-ttu-id="62249-117">[10장](chapter10.md) - 사용자 지정 사용자 이벤트 만들기에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-117">[Chapter 10](chapter10.md) - describes creating custom user events in detail.</span></span>
- <span data-ttu-id="62249-118">[11장](chapter11.md) - 내부 추적 버퍼에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-118">[Chapter 11](chapter11.md) - describes the internal trace buffer in detail.</span></span>
- <span data-ttu-id="62249-119">[부록 A](appendix-a.md) - 추적 이벤트를 수집하기 위한 타임 스탬프 원본을 포함하는 Azure RTOS ThreadX 포트 관련 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="62249-119">[Appendix A](appendix-a.md) - Azure RTOS ThreadX port-specific file with its time-stamp source for gathering trace events.</span></span>
- <span data-ttu-id="62249-120">[부록 B](appendix-b.md) - 이벤트 추적 버퍼에 대한 구현 세부 정보를 표시하는 Azure RTOS ThreadX *tx_trace.h* 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="62249-120">[Appendix B](appendix-b.md) - Azure RTOS ThreadX *tx_trace.h* file that shows implementation details regarding the event trace buffer.</span></span>
- <span data-ttu-id="62249-121">[부록 C](appendix-c.md) - 다양한 파일 형식을 적절한 Azure RTOS TraceX 이진 파일로 변환하기 위한 명령줄 유틸리티를 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-121">[Appendix C](appendix-c.md) - Summarizes command line utilities for converting various file formats into proper Azure RTOS TraceX binary files.</span></span>
- <span data-ttu-id="62249-122">[부록 D](appendix-d.md) - 다양한 개발 도구에서 추적 파일을 덤프하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="62249-122">[Appendix D](appendix-d.md) - Examples of dumping trace files from various development tools.</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="62249-123">가이드 규칙</span><span class="sxs-lookup"><span data-stu-id="62249-123">Guide Conventions</span></span>

<span data-ttu-id="62249-124">*기울임꼴* - 서체는 책 제목을 나타내고, 중요한 단어를 강조하고, 변수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="62249-124">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="62249-125">**굵게** - 서체는 파일 이름, 키워드를 표시하고 중요한 단어와 변수를 추가로 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-125">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="62249-126">메모 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="62249-126">Indicates information of note.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="62249-127">고객 지원 센터</span><span class="sxs-lookup"><span data-stu-id="62249-127">Customer Support Center</span></span>

<span data-ttu-id="62249-128">다음 단계에 대한 질문 또는 도움이 필요하면 Azure Portal을 통해 지원 티켓을 제출하세요.</span><span class="sxs-lookup"><span data-stu-id="62249-128">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="62249-129">지원 요청을 보다 효율적으로 해결할 수 있도록 이메일 메시지에 다음 정보를 제공해 주세요.</span><span class="sxs-lookup"><span data-stu-id="62249-129">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="62249-130">발생 빈도와 안정적으로 재현할 수 있는지 여부를 포함한 문제에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="62249-130">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="62249-131">문제가 발생하기 전의 애플리케이션 및/또는 Azure RTOS ThreadX의 변경 내용에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="62249-131">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="62249-132">배포의 *tx_port.h* 파일에 있는 *_tx_version_id* 문자열의 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="62249-132">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="62249-133">이 문자열은 런타임 환경에 대한 유용한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-133">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="62249-134">*_tx_build_options* ULONG 변수의 RAM에 있는 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="62249-134">The contents in RAM of the *_tx_build_options* ULONG variable.</span></span> <span data-ttu-id="62249-135">이 변수는 Azure RTOS ThreadX 라이브러리가 빌드되는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="62249-135">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
