---
title: Azure RTOS NetX Duo 사용자 가이드 소개
description: 이 가이드에는 Microsoft 고성능 IPv4/IPv6 듀얼 네트워크 스택인 Azure RTOS NetX Duo에 대한 포괄적인 정보가 나와 있습니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b1eef5bfa28f13d7a6b627792f96039b252f2355
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811053"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a><span data-ttu-id="90d00-103">Azure RTOS NetX Duo 사용자 가이드 소개</span><span class="sxs-lookup"><span data-stu-id="90d00-103">About The Azure RTOS NetX Duo User Guide</span></span>

<span data-ttu-id="90d00-104">이 가이드에는 Microsoft 고성능 IPv4/IPv6 듀얼 네트워크 스택인 Azure RTOS NetX Duo에 대한 포괄적인 정보가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-104">This guide contains comprehensive information about Azure RTOS NetX Duo, the Microsoft high-performance IPv4/IPv6 dual network stack.</span></span> 

<span data-ttu-id="90d00-105">이는 기본적인 네트워킹 개념, Azure RTOS ThreadX, C 프로그래밍 언어에 익숙한 포함된 실시간 소프트웨어 개발자를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="90d00-106">조직</span><span class="sxs-lookup"><span data-stu-id="90d00-106">Organization</span></span>

<span data-ttu-id="90d00-107">[1장](chapter1.md) - Azure RTOS NetX Duo 소개</span><span class="sxs-lookup"><span data-stu-id="90d00-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX Duo</span></span>

<span data-ttu-id="90d00-108">[2장](chapter2.md) - ThreadX 애플리케이션에서 Azure RTOS NetX Duo를 설치하고 사용하기 위한 기본 단계 설명</span><span class="sxs-lookup"><span data-stu-id="90d00-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX Duo with your ThreadX application</span></span>

<span data-ttu-id="90d00-109">[3장](chapter3.md) - Azure RTOS NetX Duo 시스템의 기능을 개괄적으로 설명하고 TCP/IP 네트워킹 표준에 대한 기본 정보 제공</span><span class="sxs-lookup"><span data-stu-id="90d00-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX Duo system and basic information about the TCP/IP networking standards</span></span>

<span data-ttu-id="90d00-110">[4장](chapter4.md) - Azure RTOS NetX Duo에 대한 애플리케이션의 인터페이스 세부 정보</span><span class="sxs-lookup"><span data-stu-id="90d00-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX Duo</span></span>

<span data-ttu-id="90d00-111">[5장](chapter5.md) - Azure RTOS NetX Duo용 네트워크 드라이버에 대한 설명</span><span class="sxs-lookup"><span data-stu-id="90d00-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX Duo</span></span>

<span data-ttu-id="90d00-112">[부록 A](appendix-a.md) - Azure RTOS NetX Duo 서비스</span><span class="sxs-lookup"><span data-stu-id="90d00-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Duo Services</span></span>

<span data-ttu-id="90d00-113">[부록 B](appendix-b.md) - Azure RTOS NetX Duo 상수</span><span class="sxs-lookup"><span data-stu-id="90d00-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Duo Constants</span></span>

<span data-ttu-id="90d00-114">[부록 C](appendix-c.md) - Azure RTOS NetX Duo 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="90d00-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="90d00-115">[부록 D](appendix-d.md) - BSD 호환 소켓 API</span><span class="sxs-lookup"><span data-stu-id="90d00-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="90d00-116">[부록 E](appendix-e.md) - ASCII 차트</span><span class="sxs-lookup"><span data-stu-id="90d00-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="90d00-117">가이드 규칙</span><span class="sxs-lookup"><span data-stu-id="90d00-117">Guide Conventions</span></span>

<span data-ttu-id="90d00-118">기울임꼴 - 책 제목을 나타내고 중요한 단어를 강조하며 변수를 가리키는 서체입니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-118">Italics - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="90d00-119">**굵게** - 파일 이름과 키워드를 나타내고 중요한 단어와 변수를 추가로 강조하는 서체입니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90d00-120">정보 기호는 성능 또는 기능에 영향을 줄 수 있는 중요한 정보나 추가 정보를 강조합니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>
 
> [!WARNING]
> <span data-ttu-id="90d00-121">경고 기호는 심각한 오류가 발생할 수 있기 때문에 개발자가 피해야 하는 상황을 강조합니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-netx-duo-data-types"></a><span data-ttu-id="90d00-122">Azure RTOS NetX Duo 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="90d00-122">Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="90d00-123">사용자 지정 Azure RTOS NetX Duo 컨트롤 구조 데이터 형식 외에도 Azure RTOS NetX Duo 서비스 호출 인터페이스에 사용되는 몇 가지 특수 데이터 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-123">In addition to the custom Azure RTOS NetX Duo control structure data types, there are several special data types that are used in Azure RTOS NetX Duo service call interfaces.</span></span> <span data-ttu-id="90d00-124">이러한 특수 데이터 형식은 기본 C 컴파일러의 데이터 형식에 직접 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="90d00-125">이 매핑은 서로 다른 C 컴파일러 간의 이식성을 보장하기 위해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="90d00-126">정확한 구현은 ThreadX에서 상속되며 ThreadX 배포에 포함된 ***tx_port.h*** 파일에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-126">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="90d00-127">다음은 Azure RTOS NetX Duo 서비스 호출 데이터 형식과 그와 관련된 의미의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-127">The following is a list of Azure RTOS NetX Duo service call data types and their associated meanings:</span></span>

<span data-ttu-id="90d00-128">**UINT**: 부호 없는 기본 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-128">**UINT**: Basic unsigned integer.</span></span> <span data-ttu-id="90d00-129">이 형식은 32비트의 부호 없는 데이터를 지원해야 합니다. 그러나 가장 편리한 부호 없는 데이터 형식에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-129">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span>  
<span data-ttu-id="90d00-130">**ULONG**: 부호 없는 long 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-130">**ULONG**: Unsigned long type.</span></span> <span data-ttu-id="90d00-131">이 형식은 32비트의 부호 없는 데이터를 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-131">This type must support 32-bit unsigned  data.</span></span>
<span data-ttu-id="90d00-132">**VOID**: 거의 항상 컴파일러의 void 형식과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-132">**VOID**: Almost always equivalent to the compiler's void type.</span></span>  
<span data-ttu-id="90d00-133">**CHAR**: 대개 표준 8비트 문자 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-133">**CHAR**: Most often a standard 8-bit character type.</span></span>  

<span data-ttu-id="90d00-134">추가 데이터 형식은 Azure RTOS NetX Duo 원본 내에서 사용되며,</span><span class="sxs-lookup"><span data-stu-id="90d00-134">Additional data types are used within the Azure RTOS NetX Duo source.</span></span> <span data-ttu-id="90d00-135">***tx_port.h** _ 또는 _ *_nx_port.h_** 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-135">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="90d00-136">고객 지원 센터</span><span class="sxs-lookup"><span data-stu-id="90d00-136">Customer Support Center</span></span>

<span data-ttu-id="90d00-137">다음 단계에 대한 질문 또는 도움이 필요하면 Azure Portal을 통해 지원 티켓을 제출하세요.</span><span class="sxs-lookup"><span data-stu-id="90d00-137">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="90d00-138">지원 요청을 보다 효율적으로 해결해 드릴 수 있도록 메일 메시지에 다음 정보를 제공해 주세요.</span><span class="sxs-lookup"><span data-stu-id="90d00-138">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="90d00-139">발생 빈도와 안정적으로 재현할 수 있는지 여부를 포함한 문제에 대한 자세한 설명</span><span class="sxs-lookup"><span data-stu-id="90d00-139">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="90d00-140">문제가 발생하기 전의 애플리케이션 및/또는 Azure RTOS NetX Duo의 변경 내용에 대한 자세한 설명</span><span class="sxs-lookup"><span data-stu-id="90d00-140">A detailed description of any changes to the application and/or Azure RTOS NetX Duo that preceded the problem.</span></span>
3. <span data-ttu-id="90d00-141">배포의 tx_port.h와 nx_port.h 파일에 있는 _tx_version_id와 _nx_version_id 문자열의 내용</span><span class="sxs-lookup"><span data-stu-id="90d00-141">The contents of the _tx_version_id and _nx_version_id strings found in the tx_port.h and nx_port.h files of your distribution.</span></span> <span data-ttu-id="90d00-142">이 문자열은 런타임 환경과 관련하여 유용한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-142">These strings will provide us valuable information regarding your run- time environment.</span></span>
4. <span data-ttu-id="90d00-143">다음 ULONG 변수의 RAM에 있는 내용:</span><span class="sxs-lookup"><span data-stu-id="90d00-143">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="90d00-144">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="90d00-144">**_tx_build_options**</span></span>

    <span data-ttu-id="90d00-145">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="90d00-145">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="90d00-146">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="90d00-146">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="90d00-147">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="90d00-147">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="90d00-148">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="90d00-148">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="90d00-149">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="90d00-149">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="90d00-150">위 변수는 Azure RTOS ThreadX와 Azure RTOS NetX Duo 라이브러리가 빌드된 방법에 관한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-150">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX Duo libraries were built.</span></span>

5. <span data-ttu-id="90d00-151">문제가 탐지된 직후에 캡처된 추적 버퍼.</span><span class="sxs-lookup"><span data-stu-id="90d00-151">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="90d00-152">추적 버퍼는 TX_ENABLE_EVENT_TRACE를 사용하여 Azure RTOS ThreadX와 Azure RTOS NetX Duo 라이브러리를 빌드하고 추적 버퍼 정보를 사용해 tx_trace_enable을 호출하여 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="90d00-152">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX Duo libraries with TX_ENABLE_EVENT_TRACE and calling tx_trace_enable with the trace buffer information.</span></span>
