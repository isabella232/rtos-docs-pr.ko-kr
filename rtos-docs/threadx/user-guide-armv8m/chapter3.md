---
title: 챕터 3 - ARMv8-M의 ThreadX API
description: 이 챕터는 ARMv8-M 관련 ThreadX 서비스에 대한 설명입니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 14bdfab3d56476d52ba91f859cec4af4ab7f4bef
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377511"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a><span data-ttu-id="489c0-103">챕터 3 - ARMv8-M의 ThreadX API</span><span class="sxs-lookup"><span data-stu-id="489c0-103">Chapter 3  ThreadX APIs for ARMv8-M</span></span>

<span data-ttu-id="489c0-104">이 챕터는 알파벳 순서로 정렬된 ARMv8-M 관련 ThreadX 서비스에 대한 설명을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-104">This chapter contains a description of the ARMv8-M-specific ThreadX services in alphabetic order.</span></span> <span data-ttu-id="489c0-105">서비스 이름은 모든 유사한 서비스가 함께 그룹화되도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="489c0-106">다음 설명의 '반환 값' 섹션에서 **굵게** 표시된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **TX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않는 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in non-bold are completely disabled.</span></span>

- <span data-ttu-id="489c0-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) 보안 메모리에 스레드 스택을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Allocate a thread stack in secure memory.</span></span>
- <span data-ttu-id="489c0-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) 보안 메모리에서 스레드 스택을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Free thread stack in secure memory</span></span>

## <a name="tx_thread_secure_stack_allocate"></a><span data-ttu-id="489c0-109">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="489c0-109">tx_thread_secure_stack_allocate</span></span>

<span data-ttu-id="489c0-110">보안 메모리에 스레드 스택을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-110">Allocate a thread stack in secure memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="489c0-111">프로토타입</span><span class="sxs-lookup"><span data-stu-id="489c0-111">Prototype</span></span>

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="489c0-112">Description</span><span class="sxs-lookup"><span data-stu-id="489c0-112">Description</span></span>

<span data-ttu-id="489c0-113">이 서비스는 stack_size 바이트 크기의 스택을 보안 메모리에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-113">This service allocates a stack of size stack_size bytes in secure memory.</span></span> <span data-ttu-id="489c0-114">보안 함수를 호출하는 모든 스레드에 대해 이 함수를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-114">This function should be called for every thread that calls secure functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="489c0-115">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="489c0-115">Input Parameters</span></span>

- <span data-ttu-id="489c0-116">**thread_ptr** 이전에 만든 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-116">**thread_ptr** Pointer to previously created thread.</span></span>

- <span data-ttu-id="489c0-117">**stack_size** 보안 스택의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-117">**stack_size** Size of secure stack.</span></span>

### <a name="return-values"></a><span data-ttu-id="489c0-118">반환 값</span><span class="sxs-lookup"><span data-stu-id="489c0-118">Return Values</span></span>

- <span data-ttu-id="489c0-119">**TX_SUCCESS** (0x00) 요청을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-119">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="489c0-120">**TX_SIZE_ERROR** (0x05) 스택 크기가 범위를 벗어났습니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-120">**TX_SIZE_ERROR** (0x05) Stack size out of range.</span></span>

- <span data-ttu-id="489c0-121">**TX_THREAD_ERROR** (0x0E) 잘못된 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-121">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="489c0-122">**TX_NO_MEMORY** (0x10) 메모리를 할당할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-122">**TX_NO_MEMORY** (0x10) Unable to allocate memory.</span></span>

- <span data-ttu-id="489c0-123">**TX_CALLER_ERROR** (0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-123">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="489c0-124">**TX_FEATURE_NOT_ENABLED** (0xFF) 시스템이 보안 모드에서 실행되도록 컴파일되었습니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-124">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="489c0-125">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="489c0-125">Allowed From</span></span>

<span data-ttu-id="489c0-126">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="489c0-126">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="489c0-127">예제</span><span class="sxs-lookup"><span data-stu-id="489c0-127">Example</span></span>

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a><span data-ttu-id="489c0-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="489c0-128">See Also</span></span>

<span data-ttu-id="489c0-129">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="489c0-129">tx_thread_secure_stack_free</span></span>

##  <a name="tx_thread_secure_stack_free"></a><span data-ttu-id="489c0-130">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="489c0-130">tx_thread_secure_stack_free</span></span>

<span data-ttu-id="489c0-131">보안 메모리에서 스레드 스택을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-131">Free a thread stack in secure memory.</span></span> 

### <a name="prototype"></a><span data-ttu-id="489c0-132">프로토타입</span><span class="sxs-lookup"><span data-stu-id="489c0-132">Prototype</span></span>

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="489c0-133">Description</span><span class="sxs-lookup"><span data-stu-id="489c0-133">Description</span></span>

<span data-ttu-id="489c0-134">이 서비스는 보안 메모리에서 스레드의 보안 스택을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-134">This service frees a thread's secure stack in secure memory.</span></span> <span data-ttu-id="489c0-135">스레드에 보안 스택이 있고 스레드가 더 이상 보안 함수를 호출하지 않아도 되거나 스레드를 삭제하는 경우 이 함수를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-135">This function should be called if a thread has a secure stack and when the thread no longer needs to call secure functions or the thread is deleted.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="489c0-136">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="489c0-136">Input Parameters</span></span>

- <span data-ttu-id="489c0-137">**thread_ptr** 이전에 만든 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-137">**thread_ptr** Pointer to previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="489c0-138">반환 값</span><span class="sxs-lookup"><span data-stu-id="489c0-138">Return Values</span></span>

- <span data-ttu-id="489c0-139">**TX_SUCCESS** (0x00) 요청을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-139">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="489c0-140">**TX_THREAD_ERROR** (0x0E) 잘못된 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-140">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="489c0-141">**TX_CALLER_ERROR** (0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-141">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="489c0-142">**TX_FEATURE_NOT_ENABLED** (0xFF) 시스템이 보안 모드에서 실행되도록 컴파일되었습니다.</span><span class="sxs-lookup"><span data-stu-id="489c0-142">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="489c0-143">허용된 원본</span><span class="sxs-lookup"><span data-stu-id="489c0-143">Allowed From</span></span>

<span data-ttu-id="489c0-144">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="489c0-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="489c0-145">예제</span><span class="sxs-lookup"><span data-stu-id="489c0-145">Example</span></span>

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a><span data-ttu-id="489c0-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="489c0-146">See Also</span></span>

<span data-ttu-id="489c0-147">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="489c0-147">tx_thread_secure_stack_allocate</span></span>
