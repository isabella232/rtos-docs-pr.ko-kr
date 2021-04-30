---
title: Azure RTOS ThreadX 가이드 정보
description: 이 가이드는 Microsoft 고성능 실시간 커널인 Azure RTOS ThreadX에 대한 포괄적인 정보를 제공합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ad9f782942bcdbb2dc49a9c841d865d97bcb1d4e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811407"
---
# <a name="about-the-azure-rtos-threadx-guide"></a><span data-ttu-id="b9f58-103">Azure RTOS ThreadX 가이드 정보</span><span class="sxs-lookup"><span data-stu-id="b9f58-103">About the Azure RTOS ThreadX Guide</span></span>

<span data-ttu-id="b9f58-104">이 가이드는 Microsoft 고성능 실시간 커널인 Azure RTOS ThreadX에 대한 포괄적인 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-104">This guide provides comprehensive information about Azure RTOS ThreadX, the Microsoft high-performance real-time kernel.</span></span> 

<span data-ttu-id="b9f58-105">포함된 실시간 소프트웨어 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="b9f58-106">개발자는 표준 실시간 운영 체제 함수 및 C 프로그래밍 언어에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-106">The developer should be familiar with standard real-time operating system functions and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="b9f58-107">조직</span><span class="sxs-lookup"><span data-stu-id="b9f58-107">Organization</span></span>

<span data-ttu-id="b9f58-108">[1장](chapter1.md) - Azure RTOS ThreadX와 실시간 포함된 개발과의 관계에 대한 기본 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-108">[Chapter 1](chapter1.md) - Provides a basic overview of Azure RTOS ThreadX and its relationship to real-time embedded development</span></span>

<span data-ttu-id="b9f58-109">[2장](chapter2.md) - 애플리케이션에서 *즉시* Azure RTOS ThreadX를 설치하고 사용하는 기본 단계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-109">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS ThreadX in your application right *out of the box*</span></span>

<span data-ttu-id="b9f58-110">[3장](chapter3.md) - 고성능 실시간 커널인 Azure RTOS ThreadX의 기능 작업에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-110">[Chapter 3](chapter3.md) - Describes in detail the functional operation of Azure RTOS ThreadX, the high performance real-time kernel</span></span>

<span data-ttu-id="b9f58-111">[4장](chapter4.md) - Azure RTOS ThreadX에 대한 애플리케이션의 인터페이스에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-111">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS ThreadX</span></span>

<span data-ttu-id="b9f58-112">[5장](chapter5.md) - Azure RTOS ThreadX 애플리케이션용 I/O 드라이버 작성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-112">[Chapter 5](chapter5.md) - Describes writing I/O drivers for Azure RTOS ThreadX applications</span></span>

<span data-ttu-id="b9f58-113">[6장](chapter6.md) - 모든 Azure RTOS ThreadX 프로세서 지원 패키지와 함께 제공되는 데모 애플리케이션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-113">[Chapter 6](chapter6.md) - Describes the demonstration application that is supplied with every Azure RTOS ThreadX processor support package</span></span>

<span data-ttu-id="b9f58-114">[부록 A](appendix-a.md) - Azure RTOS ThreadX API</span><span class="sxs-lookup"><span data-stu-id="b9f58-114">[Appendix A](appendix-a.md) - Azure RTOS ThreadX API</span></span>

<span data-ttu-id="b9f58-115">[부록 B](appendix-b.md) - Azure RTOS ThreadX 상수</span><span class="sxs-lookup"><span data-stu-id="b9f58-115">[Appendix B](appendix-b.md) - Azure RTOS ThreadX constants</span></span>

<span data-ttu-id="b9f58-116">[부록 C](appendix-c.md) - Azure RTOS ThreadX 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b9f58-116">[Appendix C](appendix-c.md) - Azure RTOS ThreadX data types</span></span>

<span data-ttu-id="b9f58-117">[부록 D](appendix-d.md) - ASCII 차트</span><span class="sxs-lookup"><span data-stu-id="b9f58-117">[Appendix D](appendix-d.md) - ASCII chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="b9f58-118">가이드 규칙</span><span class="sxs-lookup"><span data-stu-id="b9f58-118">Guide Conventions</span></span>

<span data-ttu-id="b9f58-119">*기울임꼴* - 서체는 책 제목을 나타내고, 중요한 단어를 강조하고, 매개 변수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-119">*Italics* - typeface denotes book titles, emphasizes important words, and indicates parameters.</span></span>

<span data-ttu-id="b9f58-120">**굵게** - 서체는 키워드, 상수, 형식 이름, 사용자 인터페이스 요소, 변수 이름을 나타내며, 중요한 단어를 추가로 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-120">**Boldface** - typeface denotes key words, constants, type names, user interface elements, variable names, and further emphasizes important words.</span></span>

<span data-ttu-id="b9f58-121">***기울임꼴 및 굵게*** - 서체는 파일 이름 및 함수 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-121">***Italics and Boldface*** - typeface denotes file names and function names.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9f58-122">정보 기호는 성능 또는 기능에 영향을 줄 수 있는 중요한 정보나 추가 정보를 강조합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-122">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!WARNING]
> <span data-ttu-id="b9f58-123">경고 기호는 심각한 오류가 발생할 수 있기 때문에 개발자가 피해야 하는 상황에 주목합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-123">Warning symbols draw attention to situations in which developers should take care to avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-threadx-data-types"></a><span data-ttu-id="b9f58-124">Azure RTOS ThreadX 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b9f58-124">Azure RTOS ThreadX Data Types</span></span>

<span data-ttu-id="b9f58-125">사용자 지정 Azure RTOS ThreadX 컨트롤 구조 데이터 형식 외에도 Azure RTOS ThreadX 서비스 호출 인터페이스에 사용되는 일련의 특수 데이터 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-125">In addition to the custom Azure RTOS ThreadX control structure data types, there are a series of special data types that are used in Azure RTOS ThreadX service call interfaces.</span></span> <span data-ttu-id="b9f58-126">이러한 특수 데이터 형식은 기본 C 컴파일러의 데이터 형식에 직접 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-126">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="b9f58-127">이는 서로 다른 C 컴파일러 간의 이식성을 보장하기 위해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-127">This is done to insure portability between different C compilers.</span></span> <span data-ttu-id="b9f58-128">정확한 구현은 원본에 포함된 ***tx_port.h*** 파일에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-128">The exact implementation can be found in the ***tx_port.h*** file included with the source.</span></span>

<span data-ttu-id="b9f58-129">다음은 Azure RTOS ThreadX 서비스 호출 데이터 형식 및 관련된 의미의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-129">The following is a list of Azure RTOS ThreadX service call data types and their associated meanings:</span></span>

| <span data-ttu-id="b9f58-130">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="b9f58-130">Data type</span></span>  | <span data-ttu-id="b9f58-131">Description</span><span class="sxs-lookup"><span data-stu-id="b9f58-131">Description</span></span> |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="b9f58-132">**UINT**</span><span class="sxs-lookup"><span data-stu-id="b9f58-132">**UINT**</span></span> | <span data-ttu-id="b9f58-133">부호 없는 기본 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-133">Basic unsigned integer.</span></span> <span data-ttu-id="b9f58-134">이 형식은 8비트의 부호 없는 데이터를 지원해야 합니다. 그러나 가장 편리한 부호 없는 데이터 형식에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-134">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="b9f58-135">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="b9f58-135">**ULONG**</span></span> | <span data-ttu-id="b9f58-136">부호 없는 long 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-136">Unsigned long type.</span></span> <span data-ttu-id="b9f58-137">이 형식은 32비트의 부호 없는 데이터를 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-137">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="b9f58-138">**VOID**</span><span class="sxs-lookup"><span data-stu-id="b9f58-138">**VOID**</span></span> | <span data-ttu-id="b9f58-139">거의 항상 컴파일러의 void 형식과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-139">Almost always equivalent to the compiler's void type.</span></span> |
| <span data-ttu-id="b9f58-140">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="b9f58-140">**CHAR**</span></span> | <span data-ttu-id="b9f58-141">표준 8비트 문자 형식이 가장 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-141">Most often a standard 8-bit character type.</span></span> |
|  |  |

<span data-ttu-id="b9f58-142">Azure RTOS ThreadX 원본 내에서 추가 데이터 형식이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-142">Additional data types are used within the Azure RTOS ThreadX source.</span></span> <span data-ttu-id="b9f58-143">***tx_port.h*** 파일에도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-143">They are also located in the ***tx_port.h*** file.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="b9f58-144">고객 지원 센터</span><span class="sxs-lookup"><span data-stu-id="b9f58-144">Customer Support Center</span></span>

<span data-ttu-id="b9f58-145">다음 단계에 대한 질문 또는 도움이 필요하면 Azure Portal을 통해 지원 티켓을 제출하세요.</span><span class="sxs-lookup"><span data-stu-id="b9f58-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="b9f58-146">지원 요청을 보다 효율적으로 해결할 수 있도록 이메일 메시지에 다음 정보를 제공해 주세요.</span><span class="sxs-lookup"><span data-stu-id="b9f58-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="b9f58-147">발생 빈도와 안정적으로 재현할 수 있는지 여부를 포함한 문제에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="b9f58-148">문제가 발생하기 전의 애플리케이션 및/또는 Azure RTOS ThreadX의 변경 내용에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-148">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="b9f58-149">배포의 *tx_port.h* 파일에 있는 *_tx_version_id* 문자열의 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-149">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="b9f58-150">이 문자열은 런타임 환경에 대한 유용한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-150">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="b9f58-151">**_tx_build_options** **ULONG** 변수의 RAM에 있는 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-151">The contents in RAM of the **_tx_build_options** **ULONG** variable.</span></span> <span data-ttu-id="b9f58-152">이 변수는 Azure RTOS ThreadX 라이브러리가 빌드되는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9f58-152">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
