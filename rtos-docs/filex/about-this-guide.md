---
title: Azure RTOS FileX 사용자 가이드
description: 이 가이드에는 Microsoft의 고성능 실시간 파일 시스템인 Azure RTOS FileX에 대한 포괄적인 정보가 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 640d9ed4c8037d3af6c5f45158c9496ad1258a3c
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550102"
---
# <a name="about-this-filex-user-guide"></a><span data-ttu-id="f934b-103">해당 FileX 사용자 가이드 정보</span><span class="sxs-lookup"><span data-stu-id="f934b-103">About This FileX User Guide</span></span>

<span data-ttu-id="f934b-104">이 가이드에는 Microsoft의 고성능 실시간 포함된 파일 시스템인 Azure RTOS FileX에 대한 포괄적인 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-104">This guide contains comprehensive information about Azure RTOS FileX, the high-performance, real-time embedded file system from Microsoft.</span></span> <span data-ttu-id="f934b-105">이 가이드를 최대한 활용하려면 표준 실시간 운영 체제 함수, FAT 파일 시스템 서비스 및 C 프로그래밍 언어에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-105">To gain the most from this guide, you should be familiar with standard real-time operating system functions, FAT file system services, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="f934b-106">조직</span><span class="sxs-lookup"><span data-stu-id="f934b-106">Organization</span></span>

<span data-ttu-id="f934b-107">[1장](chapter1.md) - Azure RTOS FileX 소개</span><span class="sxs-lookup"><span data-stu-id="f934b-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS FileX</span></span>

<span data-ttu-id="f934b-108">[2장](chapter2.md) - Azure RTOS ThreadX 애플리케이션에서 Azure RTOS FileX를 설치하고 사용하기 위한 기본 단계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS FileX with your Azure RTOS ThreadX application</span></span>

<span data-ttu-id="f934b-109">[3장](chapter3.md) - Azure RTOS FileX 시스템의 기능 개요와 FAT 파일 시스템 형식에 대한 기본 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS FileX system and basic information about FAT file system formats</span></span>

<span data-ttu-id="f934b-110">[4장](chapter4.md) - Azure RTOS FileX에 대한 애플리케이션의 인터페이스에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS FileX</span></span>

<span data-ttu-id="f934b-111">[5장](chapter5.md) - 제공된 Azure RTOS FileX RAM 드라이버 및 사용자 지정 Azure RTOS FileX 드라이버를 작성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-111">[Chapter 5](chapter5.md) - Describes the supplied Azure RTOS FileX RAM driver and how to write your own custom Azure RTOS FileX drivers</span></span>

<span data-ttu-id="f934b-112">[6장](chapter6.md) - Azure RTOS FileX 내결함성 모듈을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-112">[Chapter 6](chapter6.md) - Describes the Azure RTOS FileX Fault Tolerant Module</span></span>

<span data-ttu-id="f934b-113">[부록 A](appendix-a.md) - Azure RTOS FileX 서비스</span><span class="sxs-lookup"><span data-stu-id="f934b-113">[Appendix A](appendix-a.md) - Azure RTOS FileX Services</span></span>

<span data-ttu-id="f934b-114">[부록 B](appendix-b.md) - Azure RTOS FileX 상수</span><span class="sxs-lookup"><span data-stu-id="f934b-114">[Appendix B](appendix-b.md) - Azure RTOS FileX Constants</span></span>

<span data-ttu-id="f934b-115">[부록 C](appendix-c.md) - Azure RTOS FileX 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="f934b-115">[Appendix C](appendix-c.md) - Azure RTOS FileX Data Types</span></span>

<span data-ttu-id="f934b-116">[부록 D](appendix-d.md) - ASCII 차트</span><span class="sxs-lookup"><span data-stu-id="f934b-116">[Appendix D](appendix-d.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="f934b-117">가이드 규칙</span><span class="sxs-lookup"><span data-stu-id="f934b-117">Guide Conventions</span></span>

<span data-ttu-id="f934b-118">*기울임꼴* - 서체는 책 제목을 나타내고, 중요한 단어를 강조하고, 변수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-118">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="f934b-119">**굵게** - 서체는 파일 이름, 키워드를 표시하고 중요한 단어와 변수를 추가로 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="f934b-120">정보 기호는 성능 또는 기능에 영향을 줄 수 있는 중요한 정보나 추가 정보를 강조합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f934b-121">경고 기호는 심각한 오류가 발생할 수 있기 때문에 개발자가 피해야 하는 상황을 강조합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="filex-data-types"></a><span data-ttu-id="f934b-122">FileX 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="f934b-122">FileX Data Types</span></span>

<span data-ttu-id="f934b-123">사용자 지정 Azure RTOS FileX 컨트롤 구조 데이터 형식 외에도 Azure RTOS FileX 서비스 호출 인터페이스에 사용되는 일련의 특수 데이터 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-123">In addition to the custom Azure RTOS FileX control structure data types, there is a series of special data types that are used in Azure RTOS FileX service call interfaces.</span></span> <span data-ttu-id="f934b-124">이러한 특수 데이터 형식은 기본 C 컴파일러의 데이터 형식에 직접 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="f934b-125">이 매핑은 서로 다른 C 컴파일러 간의 이식성을 보장하기 위해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="f934b-126">정확한 구현은 Azure RTOS ThreadX에서 상속되며 Azure RTOS ThreadX 배포에 포함된 tx_port.h 파일에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-126">The exact implementation is inherited from Azure RTOS ThreadX and can be found in the tx_port.h file included in the Azure RTOS ThreadX distribution.</span></span>

<span data-ttu-id="f934b-127">다음은 Azure RTOS FileX 서비스 호출 데이터 형식 및 관련된 의미의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-127">The following is a list of Azure RTOS FileX service call data types and their associated meanings.</span></span>

| <span data-ttu-id="f934b-128">유형</span><span class="sxs-lookup"><span data-stu-id="f934b-128">Type</span></span>  | <span data-ttu-id="f934b-129">Description</span><span class="sxs-lookup"><span data-stu-id="f934b-129">Description</span></span>  |
|---|---|
| <span data-ttu-id="f934b-130">**UINT**</span><span class="sxs-lookup"><span data-stu-id="f934b-130">**UINT**</span></span> | <span data-ttu-id="f934b-131">부호 없는 기본 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-131">Basic unsigned integer.</span></span> <span data-ttu-id="f934b-132">이 형식은 8비트의 부호 없는 데이터를 지원해야 합니다. 그러나 가장 편리한 부호 없는 데이터 형식에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-132">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="f934b-133">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="f934b-133">**ULONG**</span></span> | <span data-ttu-id="f934b-134">부호 없는 long 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-134">Unsigned long type.</span></span> <span data-ttu-id="f934b-135">이 형식은 32비트의 부호 없는 데이터를 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-135">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="f934b-136">**VOID**</span><span class="sxs-lookup"><span data-stu-id="f934b-136">**VOID**</span></span> | <span data-ttu-id="f934b-137">거의 항상 컴파일러의 void 형식과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-137">Almost always equivalent to the compiler’s void type.</span></span> |
| <span data-ttu-id="f934b-138">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="f934b-138">**CHAR**</span></span> | <span data-ttu-id="f934b-139">표준 8비트 문자 형식이 가장 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-139">Most often a standard 8-bit character type.</span></span> |
| <span data-ttu-id="f934b-140">**ULONG64**</span><span class="sxs-lookup"><span data-stu-id="f934b-140">**ULONG64**</span></span> | <span data-ttu-id="f934b-141">64비트의 부호 없는 정수 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-141">64-bit unsigned integer data type.</span></span> |

<span data-ttu-id="f934b-142">FileX 원본 내에서 추가 데이터 형식이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-142">Additional data types are used within the FileX source.</span></span> <span data-ttu-id="f934b-143">***tx_port.h** _ 또는 _ *_fx_port.h_** 파일에도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-143">They are located in either the ***tx_port.h** _ or _ *_fx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="f934b-144">고객 지원 센터</span><span class="sxs-lookup"><span data-stu-id="f934b-144">Customer Support Center</span></span>

<span data-ttu-id="f934b-145">다음 단계에 대한 질문 또는 도움이 필요하면 Azure Portal을 통해 지원 티켓을 제출하세요.</span><span class="sxs-lookup"><span data-stu-id="f934b-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="f934b-146">지원 요청을 보다 효율적으로 해결할 수 있도록 이메일 메시지에 다음 정보를 제공해 주세요.</span><span class="sxs-lookup"><span data-stu-id="f934b-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request.</span></span>

1. <span data-ttu-id="f934b-147">발생 빈도와 안정적으로 재현할 수 있는지 여부를 포함한 문제에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="f934b-148">문제가 발생하기 전의 애플리케이션 및/또는 FileX의 변경 내용에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-148">A detailed description of any changes to the application and/or FileX that preceded the problem.</span></span>
3. <span data-ttu-id="f934b-149">배포의 _\***tx_port.h**_ 및 _ *_fx_port.h_*\* 파일에 있는 _tx_version_id 및 fx_version_id 문자열의 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-149">The contents of the _tx_version_id and _fx_version_id strings found in the \***tx_port.h**_ and _ *_fx_port.h_*\* files of your distribution.</span></span> <span data-ttu-id="f934b-150">이러한 문자열은 런타임 환경에 대한 유용한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-150">These strings will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="f934b-151">다음 **ULONG** 변수의 RAM에 있는 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-151">The contents in RAM of the following **ULONG** variables.</span></span> <span data-ttu-id="f934b-152">이러한 변수는 ThreadX 및 FileX 라이브러리가 빌드되는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f934b-152">These variables will give us information on how your ThreadX and FileX libraries were built:</span></span>

    <span data-ttu-id="f934b-153">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="f934b-153">**_tx_build_options**</span></span>

    <span data-ttu-id="f934b-154">**_fx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="f934b-154">**_fx_system_build_options1**</span></span>

    <span data-ttu-id="f934b-155">**_fx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="f934b-155">**_fx_system_build_options2**</span></span>

    <span data-ttu-id="f934b-156">**_fx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="f934b-156">**_fx_system_build_options3**</span></span>
