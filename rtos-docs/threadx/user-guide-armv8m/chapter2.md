---
title: 챕터 2 - ARMv8-M의 ThreadX 지원 설치
description: 이 챕터는 ARMv8-M 아키텍처의 ThreadX 소스 코드를 설치하고 사용하는 방법을 설명합니다.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 303b83bcc92797314b764353b770965c0170fb99
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377505"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a><span data-ttu-id="2f2c1-103">챕터 2 - ARMv8-M의 ThreadX 지원 설치</span><span class="sxs-lookup"><span data-stu-id="2f2c1-103">Chapter 2  Installing ThreadX support for ARMv8-M</span></span>

<span data-ttu-id="2f2c1-104">ARMv8-M 아키텍처를 지원하는 추가 ThreadX 소스 코드 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-104">There are additional ThreadX source code files to support the ARMv8-M architecture.</span></span>

<span data-ttu-id="2f2c1-105">ThreadX가 보안 모드에서 실행되는 경우 이러한 추가 파일 및 API는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-105">If ThreadX is to be run in secure mode, these additional files and APIs are not needed.</span></span> <span data-ttu-id="2f2c1-106">보안 모드에서 ThreadX를 실행하려면 **_tx_port.h_ *_의 상단, 명령줄 또는 프로젝트 설정에서 기호 **TX_SECURE_EXECUTION** 을 정의하십시오. 모든 c 및 어셈블리 파일에 대해 _* TX_SECURE_EXECUTION** 이 정의되어 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-106">To run ThreadX in secure mode, define the symbol **TX_SECURE_EXECUTION** at the top of **_tx_port.h_*_ or on the command line or project settings. Ensure _\* TX_SECURE_EXECUTION*\* is defined for all c and assembly files.</span></span> <span data-ttu-id="2f2c1-107">ThreadX 및 사용자 애플리케이션이 보안 모드에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-107">ThreadX and the user application will execute in secure mode.</span></span>

<span data-ttu-id="2f2c1-108">ThreadX 및 사용자 애플리케이션을 비보안 모드로 실행하고 비보안 호출 가능 보안 함수를 지원하려면 다음을 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-108">To run ThreadX and the user application in non-secure mode and support non-secure callable secure functions, please do the following.</span></span>

<span data-ttu-id="2f2c1-109">***tx_thread_secure_stack.c*** 파일을 보안 애플리케이션에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-109">The file ***tx_thread_secure_stack.c*** must be added to the secure application.</span></span>

<span data-ttu-id="2f2c1-110">다음 파일을 ThreadX 라이브러리에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-110">The following files must be added to the ThreadX library.</span></span>

- <span data-ttu-id="2f2c1-111">***tx_secure_interface.h***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-111">***tx_secure_interface.h***</span></span>
- <span data-ttu-id="2f2c1-112">***txe_thread_secure_stack_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-112">***txe_thread_secure_stack_allocate.c***</span></span>
- <span data-ttu-id="2f2c1-113">***txe_thread_secure_stack_free.c***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-113">***txe_thread_secure_stack_free.c***</span></span>
- <span data-ttu-id="2f2c1-114">***tx_thread_secure_stack_allocate.s***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-114">***tx_thread_secure_stack_allocate.s***</span></span>
- <span data-ttu-id="2f2c1-115">***tx_thread_secure_stack_free.s***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-115">***tx_thread_secure_stack_free.s***</span></span>

<span data-ttu-id="2f2c1-116">다음 두 파일은 ThreadX 라이브러리의 일반 파일을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-116">The following two files replace the generic files in the ThreadX library.</span></span>

- <span data-ttu-id="2f2c1-117">***tx_thread_stack_error_handler.c***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-117">***tx_thread_stack_error_handler.c***</span></span>
- <span data-ttu-id="2f2c1-118">***tx_thread_stack_error_notify.c***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-118">***tx_thread_stack_error_notify.c***</span></span>

## <a name="additional-threadx-sources-for-armv8-m"></a><span data-ttu-id="2f2c1-119">ARMv8-M의 추가 ThreadX 소스</span><span class="sxs-lookup"><span data-stu-id="2f2c1-119">Additional ThreadX Sources for ARMv8-M</span></span>

<span data-ttu-id="2f2c1-120">ARMv8-M TrustZone 아키텍처의 추가 ThreadX 파일은 아래에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-120">The additional ThreadX files for the ARMv8-M TrustZone architecture are described below.</span></span>

  | <span data-ttu-id="2f2c1-121">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="2f2c1-121">**File Name**</span></span>                            | <span data-ttu-id="2f2c1-122">**콘텐츠**</span><span class="sxs-lookup"><span data-stu-id="2f2c1-122">**Contents**</span></span>                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | <span data-ttu-id="2f2c1-123">***tx_secure_interface.h***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-123">***tx_secure_interface.h***</span></span>              | <span data-ttu-id="2f2c1-124">ThreadX 비보안 호출 가능 함수를 정의하는 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-124">Include file that defines the ThreadX non-secure callable functions.</span></span> |
  | <span data-ttu-id="2f2c1-125">***txe_thread_secure_stack_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-125">***txe_thread_secure_stack_allocate.c***</span></span> |  <span data-ttu-id="2f2c1-126">보안 스택 할당 API의 오류 검사 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-126">Error-checking file for the secure stack allocate API.</span></span> |
  | <span data-ttu-id="2f2c1-127">***txe_thread_secure_stack_free.c***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-127">***txe_thread_secure_stack_free.c***</span></span>     |  <span data-ttu-id="2f2c1-128">보안 스택 해제 API의 오류 검사 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-128">Error-checking file for the secure stack free API.</span></span> |
  | <span data-ttu-id="2f2c1-129">***tx_thread_secure_stack_allocate.s***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-129">***tx_thread_secure_stack_allocate.s***</span></span>  |  <span data-ttu-id="2f2c1-130">보안 스택 할당 서비스의 비보안 베니어입니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-130">Non-secure veneer for the secure stack allocate service.</span></span> |
  | <span data-ttu-id="2f2c1-131">***tx_thread_secure_stack_free.s***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-131">***tx_thread_secure_stack_free.s***</span></span>      |  <span data-ttu-id="2f2c1-132">보안 스택 해제 서비스의 비보안 베니어입니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-132">Non-secure veneer for the secure stack free service.</span></span> |
  | <span data-ttu-id="2f2c1-133">***tx_thread_stack_error_handler.c***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-133">***tx_thread_stack_error_handler.c***</span></span>    |  <span data-ttu-id="2f2c1-134">스레드 스택 오류의 처리기입니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-134">Handler for thread stack errors.</span></span> |
  | <span data-ttu-id="2f2c1-135">***tx_thread_stack_error_notify.c***</span><span class="sxs-lookup"><span data-stu-id="2f2c1-135">***tx_thread_stack_error_notify.c***</span></span>     |  <span data-ttu-id="2f2c1-136">스레드 스택 오류를 처리하기 위한 알림 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="2f2c1-136">Register notification callback for handling thread stack errors.</span></span> |
