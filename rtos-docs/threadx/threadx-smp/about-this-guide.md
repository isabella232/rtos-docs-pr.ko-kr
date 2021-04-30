---
title: 이 가이드 정보
description: 이 가이드는 Microsoft 고성능 포함된 실시간 커널인 Azure RTOS ThreadX SMP에 대한 포괄적인 정보를 제공합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2399666b5b4d7c34db50d539e200c90f06f7235f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810261"
---
# <a name="about-this-guide"></a><span data-ttu-id="5c7f1-103">이 가이드 정보</span><span class="sxs-lookup"><span data-stu-id="5c7f1-103">About This Guide</span></span>

<span data-ttu-id="5c7f1-104">이 가이드는 Microsoft 고성능 포함된 실시간 커널인 Azure RTOS ThreadX SMP에 대한 포괄적인 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-104">This guide provides comprehensive information about Azure RTOS ThreadX SMP, the Microsoft high-performance embedded real-time kernel.</span></span>

<span data-ttu-id="5c7f1-105">포함된 실시간 소프트웨어 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="5c7f1-106">개발자는 표준 실시간 운영 체제 함수 및 C 프로그래밍 언어에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-106">The developer should be familiar with standard real-time operating system functions and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="5c7f1-107">조직</span><span class="sxs-lookup"><span data-stu-id="5c7f1-107">Organization</span></span>

| <span data-ttu-id="5c7f1-108">장</span><span class="sxs-lookup"><span data-stu-id="5c7f1-108">Chapter</span></span>       | <span data-ttu-id="5c7f1-109">개요</span><span class="sxs-lookup"><span data-stu-id="5c7f1-109">Overview</span></span>                    |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="5c7f1-110">**1장**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-110">**Chapter 1**</span></span> | <span data-ttu-id="5c7f1-111">ThreadX SMP에 대한 기본적인 개요와 실시간 포함된 개발과의 관계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-111">Provides a basic overview of ThreadX SMP and its relationship to real-time embedded development.</span></span>           |
| <span data-ttu-id="5c7f1-112">**2장**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-112">**Chapter 2**</span></span> | <span data-ttu-id="5c7f1-113">애플리케이션에서 ThreadX SMP를 *즉시* 설치하고 사용하는 기본 단계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-113">Gives the basic steps to install and use ThreadX SMP in your application right *out of the box*.</span></span>           |
| <span data-ttu-id="5c7f1-114">**3장**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-114">**Chapter 3**</span></span> | <span data-ttu-id="5c7f1-115">고성능 실시간 SMP 커널인 ThreadX SMP의 기능 작업에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-115">Describes in detail the functional operation of ThreadX SMP, the high-performance real-time SMP kernel.</span></span>    |
| <span data-ttu-id="5c7f1-116">**4장**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-116">**Chapter 4**</span></span> | <span data-ttu-id="5c7f1-117">ThreadX SMP에 대한 애플리케이션의 인터페이스에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-117">Details the application’s interface to ThreadX SMP.</span></span>                                                        |
| <span data-ttu-id="5c7f1-118">**5장**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-118">**Chapter 5**</span></span> | <span data-ttu-id="5c7f1-119">ThreadX SMP 애플리케이션에 대한 I/O 드라이버 작성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-119">Describes writing I/O drivers for ThreadX SMP applications.</span></span>                                                |
| <span data-ttu-id="5c7f1-120">**6장**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-120">**Chapter 6**</span></span> | <span data-ttu-id="5c7f1-121">모든 ThreadX SMP 프로세서 지원 패키지와 함께 제공되는 데모 애플리케이션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-121">Describes the demonstration application that is supplied with every ThreadX SMP processor support package.</span></span> |
| <span data-ttu-id="5c7f1-122">**부록 A**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-122">**Appendix A**</span></span> | <span data-ttu-id="5c7f1-123">ThreadX SMP API</span><span class="sxs-lookup"><span data-stu-id="5c7f1-123">ThreadX SMP API</span></span>        |
| <span data-ttu-id="5c7f1-124">**부록 B**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-124">**Appendix B**</span></span> | <span data-ttu-id="5c7f1-125">ThreadX SMP 상수</span><span class="sxs-lookup"><span data-stu-id="5c7f1-125">ThreadX SMP constants</span></span>  |
| <span data-ttu-id="5c7f1-126">**부록 C**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-126">**Appendix C**</span></span> | <span data-ttu-id="5c7f1-127">ThreadX SMP 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="5c7f1-127">ThreadX SMP data types</span></span> |
| <span data-ttu-id="5c7f1-128">**부록 D**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-128">**Appendix D**</span></span> | <span data-ttu-id="5c7f1-129">ASCII 차트</span><span class="sxs-lookup"><span data-stu-id="5c7f1-129">ASCII chart</span></span>            |

## <a name="guide-conventions"></a><span data-ttu-id="5c7f1-130">가이드 규칙</span><span class="sxs-lookup"><span data-stu-id="5c7f1-130">Guide Conventions</span></span>

- <span data-ttu-id="5c7f1-131">*기울임꼴* - *서체는 책 제목을 나타내고, 중요한 단어를 강조하고, 변수를 나타냅니다.*</span><span class="sxs-lookup"><span data-stu-id="5c7f1-131">*Italics* - *typeface denotes book titles, emphasizes important words, and indicates variables.*</span></span>
- <span data-ttu-id="5c7f1-132">**굵게** - **서체는 파일 이름, 키워드를 표시하고 중요한 단어와 변수를 추가로 강조 표시합니다.**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-132">**Boldface** - **typeface denotes file names, key words, and further emphasizes important words and variables.**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5c7f1-133">정보 기호는 성능 또는 기능에 영향을 줄 수 있는 중요한 정보나 추가 정보를 강조합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-133">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!WARNING]
> <span data-ttu-id="5c7f1-134">경고 기호는 심각한 오류가 발생할 수 있기 때문에 개발자가 피해야 하는 상황에 주목합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-134">Warning symbols draw attention to situations in which developers should take care to avoid because they could cause fatal errors.</span></span>

## <a name="threadx-smp-data-types"></a><span data-ttu-id="5c7f1-135">ThreadX SMP 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="5c7f1-135">ThreadX SMP Data Types</span></span>

<span data-ttu-id="5c7f1-136">사용자 지정 ThreadX SMP 컨트롤 구조 데이터 형식 외에도 ThreadX SMP 서비스 호출 인터페이스에 사용되는 일련의 특수 데이터 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-136">In addition to the custom ThreadX SMP control structure data types, there are a series of special data types that are used in ThreadX SMP service call interfaces.</span></span> <span data-ttu-id="5c7f1-137">이러한 특수 데이터 형식은 기본 C 컴파일러의 데이터 형식에 직접 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-137">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="5c7f1-138">이는 서로 다른 C 컴파일러 간의 이식성을 보장하기 위해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-138">This is done to insure portability between different C compilers.</span></span> <span data-ttu-id="5c7f1-139">정확한 구현은 배포 디스크에 포함된 ***tx_port.h*** 파일에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-139">The exact implementation can be found in the ***tx_port.h*** file included on the distribution disk.</span></span>

<span data-ttu-id="5c7f1-140">다음은 ThreadX SMP 서비스 호출 데이터 형식 및 관련된 의미의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-140">The following is a list of ThreadX SMP service call data types and their associated meanings:</span></span>

| <span data-ttu-id="5c7f1-141">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="5c7f1-141">Data Type</span></span>          | <span data-ttu-id="5c7f1-142">의미</span><span class="sxs-lookup"><span data-stu-id="5c7f1-142">Meaning</span></span>                                                          |
| --------- | --------------------------------------------------------- |
| <span data-ttu-id="5c7f1-143">**UINT**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-143">**UINT**</span></span>  | <span data-ttu-id="5c7f1-144">부호 없는 기본 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-144">Basic unsigned integer.</span></span> <span data-ttu-id="5c7f1-145">이 형식은 8비트의 부호 없는 데이터를 지원해야 합니다. 그러나 가장 편리한 부호 없는 데이터 형식에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-145">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="5c7f1-146">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-146">**ULONG**</span></span> | <span data-ttu-id="5c7f1-147">부호 없는 long 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-147">Unsigned long type.</span></span> <span data-ttu-id="5c7f1-148">이 형식은 32비트의 부호 없는 데이터를 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-148">This type must support 32-bit unsigned data.</span></span>                                                                     |
| <span data-ttu-id="5c7f1-149">**VOID**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-149">**VOID**</span></span>  | <span data-ttu-id="5c7f1-150">거의 항상 컴파일러의 void 형식과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-150">Almost always equivalent to the compiler’s void type.</span></span>                                                                                |
| <span data-ttu-id="5c7f1-151">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="5c7f1-151">**CHAR**</span></span>  | <span data-ttu-id="5c7f1-152">표준 8비트 문자 형식이 가장 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-152">Most often a standard 8-bit character type.</span></span>                                                                                          |

<span data-ttu-id="5c7f1-153">ThreadX SMP 원본 내에서 추가 데이터 형식이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-153">Additional data types are used within the ThreadX SMP source.</span></span> <span data-ttu-id="5c7f1-154">***tx_port.h*** 파일에도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-154">They are also located in the ***tx_port.h*** file.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="5c7f1-155">고객 지원 센터</span><span class="sxs-lookup"><span data-stu-id="5c7f1-155">Customer Support Center</span></span>

<span data-ttu-id="5c7f1-156">지원 이메일: [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) 웹 페이지: azure.com/rtos</span><span class="sxs-lookup"><span data-stu-id="5c7f1-156">Support email: [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Web page: azure.com/rtos</span></span>

### <a name="latest-product-information"></a><span data-ttu-id="5c7f1-157">최신 제품 정보</span><span class="sxs-lookup"><span data-stu-id="5c7f1-157">Latest Product Information</span></span>

<span data-ttu-id="5c7f1-158">azure.com/rtos 웹 사이트를 방문하고 "지원" 메뉴 옵션을 선택하여 최신 ThreadX SMP 제품 릴리스에 대한 정보를 비롯한 최신 온라인 지원 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-158">Visit the azure.com/rtos web site and select the “Support” menu option to find the latest online support information, including information about the latest ThreadX SMP product releases.</span></span>

### <a name="what-we-need-from-you"></a><span data-ttu-id="5c7f1-159">제공할 사항</span><span class="sxs-lookup"><span data-stu-id="5c7f1-159">What We Need From You</span></span>

<span data-ttu-id="5c7f1-160">지원 요청을 보다 효율적으로 해결할 수 있도록 이메일 메시지에 다음 정보를 제공해 주세요.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-160">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="5c7f1-161">발생 빈도와 안정적으로 재현할 수 있는지 여부를 포함한 문제에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-161">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="5c7f1-162">문제가 발생하기 전의 애플리케이션 및/또는 ThreadX SMP의 변경 내용에 대한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-162">A detailed description of any changes to the application and/or ThreadX SMP that preceded the problem.</span></span>
3. <span data-ttu-id="5c7f1-163">배포의 _ *_tx_port.h_*\* 파일에 있는 \* **_tx_version_id** _ 문자열의 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-163">The contents of the ***_tx_version_id** _ string found in the _ *_tx_port.h_** file of your distribution.</span></span> <span data-ttu-id="5c7f1-164">이 문자열은 런타임 환경에 대한 유용한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-164">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="5c7f1-165">***_tx_build_options*** ULONG 변수의 RAM에 있는 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-165">The contents in RAM of the ***_tx_build_options*** ULONG variable.</span></span> <span data-ttu-id="5c7f1-166">이 변수는 ThreadX SMP 라이브러리가 빌드되는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-166">This variable will give us information on how your ThreadX SMP library was built.</span></span>

### <a name="where-to-send-comments-about-this-guide"></a><span data-ttu-id="5c7f1-167">이 가이드에 대한 의견을 보낼 위치</span><span class="sxs-lookup"><span data-stu-id="5c7f1-167">Where to Send Comments About This Guide</span></span>

<span data-ttu-id="5c7f1-168">[azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com)에서 고객 지원 센터에 의견 및 제안을 이메일로 보낼 수 있습니다. 제목 줄에 "ThreadX SMP 사용자 가이드"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5c7f1-168">Email any comments and suggestions to the Customer Support Center at [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Enter “ThreadX SMP User Guide” in the subject line.</span></span>
