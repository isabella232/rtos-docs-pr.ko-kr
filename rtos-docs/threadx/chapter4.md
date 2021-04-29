---
title: 4장 - Azure RTOS ThreadX 서비스 설명
description: 이 장에서는 모든 Azure RTOS ThreadX 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 60ecc96df07b1f77b9b448814c4420133f3e2afc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810273"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a><span data-ttu-id="c6e75-103">4장 - Azure RTOS ThreadX 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="c6e75-103">Chapter 4 - Description of Azure RTOS ThreadX Services</span></span>

<span data-ttu-id="c6e75-104">이 장에서는 모든 Azure RTOS ThreadX 서비스를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-104">This chapter contains a description of all Azure RTOS ThreadX services in alphabetic order.</span></span> <span data-ttu-id="c6e75-105">서비스 이름은 모든 유사한 서비스가 함께 그룹화되도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="c6e75-106">다음 설명의 “반환 값” 섹션에서 **굵게** 표시된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **TX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않는 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="c6e75-107">또한 “**가능한 선점**” 제목 아래 표시된 “**예**”는 서비스를 호출하면 우선 순위가 더 높은 스레드를 다시 시작할 수 있으므로 호출 스레드를 선점할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-107">In addition, a "**Yes**" listed under the "**Preemption Possible**" heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="c6e75-108">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-108">tx_block_allocate</span></span>

<span data-ttu-id="c6e75-109">고정 크기 메모리 블록을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-109">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-110">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-110">Prototype</span></span>

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c6e75-111">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-111">Description</span></span>

<span data-ttu-id="c6e75-112">이 서비스는 지정된 메모리 풀에서 고정 크기 메모리 블록을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-112">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="c6e75-113">메모리 블록의 실제 크기는 메모리 풀을 만드는 동안 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-113">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-114">애플리케이션 코드가 할당된 메모리 블록의 외부에 쓰지 않도록 하는 것이 중요합니다. 외부에 쓰면 인접한(일반적으로 이후) 메모리 블록에 손상이 발생합니다. 결과를 예측할 수 없으며 치명적인 결과가 발생하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-114">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-115">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-115">Parameters</span></span>

- <span data-ttu-id="c6e75-116">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-116">**pool_ptr**</span></span> <br><span data-ttu-id="c6e75-117">이전에 만든 메모리 블록 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-117">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="c6e75-118">**block_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-118">**block_ptr**</span></span> <br><span data-ttu-id="c6e75-119">대상 블록 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-119">Pointer to a destination block pointer.</span></span> <span data-ttu-id="c6e75-120">할당에 성공하면 할당된 메모리 블록 주소가 이 매개 변수에서 가리키는 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-120">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="c6e75-121">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="c6e75-121">**wait_option**</span></span> <br><span data-ttu-id="c6e75-122">사용할 수 있는 메모리 블록이 없는 경우의 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-122">Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="c6e75-123">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-123">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c6e75-124">**TX_NO_WAIT**(0x00000000) - **TX_NO_WAIT** 를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-124">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="c6e75-125">초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-125">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="c6e75-126">**TX_WAIT_FOREVER**(0xFFFFFFF) - **TX_WAIT_FOREVER** 를 선택하면 메모리 블록을 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-126">**TX_WAIT_FOREVER** (0xFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until a memory block is available.</span></span>
  - <span data-ttu-id="c6e75-127">‘시간 제한 값’(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 메모리 블록을 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-127">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-128">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-128">Return Values</span></span>

- <span data-ttu-id="c6e75-129">**TX_SUCCESS**(0x00) 메모리 블록 할당에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-129">**TX_SUCCESS**    (0x00)  Successful memory block allocation.</span></span>
- <span data-ttu-id="c6e75-130">**TX_DELETED**(0x01) 스레드가 일시 중단된 동안 메모리 블록 풀이 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-130">**TX_DELETED**    (0x01)  Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="c6e75-131">**TX_NO_MEMORY**(0x10) 서비스가 지정된 대기 시간 내에 메모리 블록을 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-131">**TX_NO_MEMORY**  (0x10)  Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="c6e75-132">**TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-132">**TX_WAIT_ABORTED**   (0x1A)  Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="c6e75-133">**TX_POOL_ERROR**(0x02) 잘못된 메모리 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-133">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="c6e75-134">**TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-134">**TX_WAIT_ERROR** (0x04)  A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="c6e75-135">**TX_PTR_ERROR**(0x03) 대상 포인터에 대한 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-135">**TX_PTR_ERROR**  (0x03)  Invalid pointer to destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-136">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-136">Allowed From</span></span>

<span data-ttu-id="c6e75-137">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-137">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-138">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-138">Preemption Possible</span></span>

<span data-ttu-id="c6e75-139">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-140">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-140">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;

UINT status;

/* Allocate a memory block from my_pool. Assume that the pool has
already been created with a call to tx_block_pool_create. */

status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
  TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the address of
the allocated block of memory. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-141">See Also</span></span>

- <span data-ttu-id="c6e75-142">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-142">tx_block_pool_create</span></span>
- <span data-ttu-id="c6e75-143">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-143">tx_block_pool_delete</span></span>
- <span data-ttu-id="c6e75-144">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-144">tx_block_pool_info_get</span></span>
- <span data-ttu-id="c6e75-145">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-145">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-146">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-146">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-147">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-147">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="c6e75-148">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-148">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="c6e75-149">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-149">tx_block_pool_create</span></span>

<span data-ttu-id="c6e75-150">고정 크기 메모리 블록 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-150">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-151">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-151">Prototype</span></span>

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="c6e75-152">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-152">Description</span></span>

<span data-ttu-id="c6e75-153">이 서비스는 고정 크기 메모리 블록 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-153">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="c6e75-154">지정된 메모리 영역은 다음 수식을 사용하여 가능한 한 많은 고정 크기 메모리 블록으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-154">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>

<span data-ttu-id="c6e75-155">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span><span class="sxs-lookup"><span data-stu-id="c6e75-155">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!NOTE]
><span data-ttu-id="c6e75-156">\*각 메모리 블록에는 사용자에게 표시되지 않고 앞의 수식에서 “sizeof(void *)”로 표시되는 오버헤드 포인터 하나가 포함되어 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="c6e75-156">\*Each memory block contains one pointer of overhead that is invisible to the user and is represented by the "sizeof(void *)" in the preceding formula.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-157">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-157">Parameters</span></span>

- <span data-ttu-id="c6e75-158">**pool_ptr**  메모리 블록 풀 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-158">**pool_ptr**  Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="c6e75-159">**name_ptr** 메모리 블록 풀의 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-159">**name_ptr**  Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="c6e75-160">**block_size** 각 메모리 블록의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-160">**block_size**    Number of bytes in each memory block.</span></span>
- <span data-ttu-id="c6e75-161">**pool_start** 메모리 블록 풀의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-161">**pool_start**    Starting address of the memory block pool.</span></span> <span data-ttu-id="c6e75-162">시작 주소는 ULONG 데이터 형식의 크기에 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-162">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="c6e75-163">**pool_size** 메모리 블록 풀에 사용할 수 있는 총 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-163">**pool_size** Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-164">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-164">Return Values</span></span>

- <span data-ttu-id="c6e75-165">**TX_SUCCESS**(0x00) 메모리 블록 풀 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-165">**TX_SUCCESS**    (0x00)  Successful memory block pool creation.</span></span>
- <span data-ttu-id="c6e75-166">**TX_POOL_ERROR**(0x02) 잘못된 메모리 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-166">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span> <span data-ttu-id="c6e75-167">포인터가 NULL이거나 풀이 이미 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-167">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="c6e75-168">**TX_PTR_ERROR**(0x03) 풀 시작 주소가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-168">**TX_PTR_ERROR**  (0x03)  Invalid starting address of the pool.</span></span>
- <span data-ttu-id="c6e75-169">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-169">**TX_CALLER_ERROR**   (0x13)  Invalid caller of this service.</span></span>
- <span data-ttu-id="c6e75-170">**TX_SIZE_ERROR**(0x05) 풀 크기가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-170">**TX_SIZE_ERROR** (0x05)  Size of pool is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-171">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-171">Allowed From</span></span>

<span data-ttu-id="c6e75-172">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-172">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-173">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-173">Preemption Possible</span></span>

<span data-ttu-id="c6e75-174">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-174">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-175">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-175">Example</span></span>

```c
TX_BLOCK_POOL my_pool;

UINT status;

/* Create a memory pool whose total size is 1000 bytes starting at
address 0x100000. Each block in this pool is defined to be 50 bytes
long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
  50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18 memory blocks
of 50 bytes each. The reason there are not 20 blocks in the pool is
because of the one overhead pointer associated with each block. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-176">See Also</span></span>

- <span data-ttu-id="c6e75-177">tx_block_allocate, tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-177">tx_block_allocate, tx_block_pool_delete</span></span>
- <span data-ttu-id="c6e75-178">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-178">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-179">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-179">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-180">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-180">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="c6e75-181">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-181">tx_block_pool_delete</span></span>

<span data-ttu-id="c6e75-182">메모리 블록 풀을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-182">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-183">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-183">Prototype</span></span>

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-184">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-184">Description</span></span>

<span data-ttu-id="c6e75-185">이 서비스는 지정된 블록 메모리 풀을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-185">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="c6e75-186">이 풀의 메모리 블록을 기다리는 일시 중단된 모든 스레드는 다시 시작되며 **TX_DELETED** 반환 상태가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-186">All threads suspended waiting for a memory block from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-187">이 서비스가 완료된 후 사용할 수 있는 풀과 연결된 메모리 영역은 애플리케이션에서 관리해야 합니다. 또한 애플리케이션은 삭제된 풀이나 이전 메모리 블록을 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-187">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or its former memory blocks.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-188">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-188">Parameters</span></span>

- <span data-ttu-id="c6e75-189">**pool_ptr** 이전에 만든 메모리 블록 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-189">**pool_ptr** Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-190">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-190">Return Values</span></span>

- <span data-ttu-id="c6e75-191">**TX_SUCCESS**(0x00) 메모리 블록 풀 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-191">**TX_SUCCESS** (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="c6e75-192">**TX_POOL_ERROR**(0x02) 잘못된 메모리 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-192">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="c6e75-193">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-193">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-194">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-194">Allowed From</span></span>

<span data-ttu-id="c6e75-195">스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-195">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-196">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-196">Preemption Possible</span></span>

<span data-ttu-id="c6e75-197">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-197">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-198">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-198">Example</span></span>

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a><span data-ttu-id="c6e75-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-199">See Also</span></span>

- <span data-ttu-id="c6e75-200">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-200">tx_block_allocate</span></span>
- <span data-ttu-id="c6e75-201">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-201">tx_block_pool_create</span></span>
- <span data-ttu-id="c6e75-202">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-202">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-203">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-203">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-204">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-204">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="c6e75-205">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-205">tx_block_pool_info_get</span></span>

<span data-ttu-id="c6e75-206">블록 풀에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-206">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-207">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-207">Prototype</span></span>

```c
UINT tx_block_pool_info_get(
    TX_BLOCK_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *total_blocks,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BLOCK_POOL **next_pool);
```

### <a name="description"></a><span data-ttu-id="c6e75-208">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-208">Description</span></span>

<span data-ttu-id="c6e75-209">이 서비스는 지정된 블록 메모리 풀에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-209">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-210">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-210">Parameters</span></span>

- <span data-ttu-id="c6e75-211">**pool_ptr**  이전에 만든 메모리 블록 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-211">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="c6e75-212">**name** 블록 풀 이름 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-212">**name**  Pointer to destination for the pointer to the block pool's name.</span></span>
- <span data-ttu-id="c6e75-213">**available** 블록 풀의 사용 가능한 블록 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-213">**available** Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="c6e75-214">**total_blocks** 블록 풀의 총 블록 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-214">**total_blocks**  Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="c6e75-215">**first_suspended** 이 블록 풀의 일시 중단 목록에 있는 첫 번째 스레드 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-215">**first_suspended**   Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="c6e75-216">**suspended_count** 이 블록 풀의 현재 일시 중단된 스레드 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-216">**suspended_count**   Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="c6e75-217">**next_pool** 다음에 만들 블록 풀 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-217">**next_pool** Pointer to destination for the pointer of the next created block pool.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-218">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-218">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-219">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-219">Return Values</span></span>

- <span data-ttu-id="c6e75-220">**TX_SUCCESS**(0x00) 블록 풀 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-220">**TX_SUCCESS** (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="c6e75-221">**TX_POOL_ERROR**(0x02) 잘못된 메모리 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-221">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-222">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-222">Allowed From</span></span>

<span data-ttu-id="c6e75-223">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-223">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-224">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-224">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
CHAR *name;
ULONG available;
ULONG total_blocks;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BLOCK_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
  &available,&total_blocks,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-225">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-225">See Also</span></span>

- <span data-ttu-id="c6e75-226">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-226">tx_block_allocate</span></span>
- <span data-ttu-id="c6e75-227">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-227">tx_block_pool_create</span></span>
- <span data-ttu-id="c6e75-228">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-228">tx_block_pool_delete</span></span>
- <span data-ttu-id="c6e75-229">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-229">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-230">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-230">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-231">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-231">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="c6e75-232">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-232">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="c6e75-233">블록 풀 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-233">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-234">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-234">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="c6e75-235">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-235">Description</span></span>

<span data-ttu-id="c6e75-236">이 서비스는 지정된 메모리 블록 풀에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-236">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-237">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. </span><span class="sxs-lookup"><span data-stu-id="c6e75-237">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-238">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-238">Parameters</span></span>

- <span data-ttu-id="c6e75-239">**pool_ptr**  이전에 만든 메모리 블록 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-239">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="c6e75-240">**allocates** 이 풀에서 수행된 할당 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-240">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="c6e75-241">**releases** 이 풀에서 수행된 해제 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-241">**releases**  Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="c6e75-242">**suspensions** 이 풀의 스레드 할당 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-242">**suspensions**   Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="c6e75-243">**timeouts** 이 풀의 할당 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-243">**timeouts**  Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

>[!NOTE]
> <span data-ttu-id="c6e75-244">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-244">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-245">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-245">Return Values</span></span>

- <span data-ttu-id="c6e75-246">**TX_SUCCESS**(0x00) 블록 풀 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-246">**TX_SUCCESS**    (0x00)  Successful block pool performance get.</span></span>
- <span data-ttu-id="c6e75-247">**TX_PTR_ERROR**(0x03) 잘못된 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-247">**TX_PTR_ERROR**  (0x03)  Invalid block pool pointer.</span></span>
- <span data-ttu-id="c6e75-248">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-248">**TX_FEATURE_NOT_ENABLED**    (0xFF)  The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-249">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-249">Allowed From</span></span>

<span data-ttu-id="c6e75-250">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-250">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-251">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-251">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created block
pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
  &releases,
  &suspensions,
  &timeouts);

/* If status is TX_SUCCESS the performance information was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-252">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-252">See Also</span></span>

- <span data-ttu-id="c6e75-253">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-253">tx_block_allocate</span></span>
- <span data-ttu-id="c6e75-254">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-254">tx_block_pool_create</span></span>
- <span data-ttu-id="c6e75-255">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-255">tx_block_pool_delete</span></span>
- <span data-ttu-id="c6e75-256">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-256">tx_block_pool_info_get</span></span>
- <span data-ttu-id="c6e75-257">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-257">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-258">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-258">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-259">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-259">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="c6e75-260">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-260">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="c6e75-261">블록 풀 시스템 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-261">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-262">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-262">Prototype</span></span>

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="c6e75-263">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-263">Description</span></span>

<span data-ttu-id="c6e75-264">이 서비스는 애플리케이션의 모든 메모리 블록 풀에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-264">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-265">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. </span><span class="sxs-lookup"><span data-stu-id="c6e75-265">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-266">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-266">Parameters</span></span>

- <span data-ttu-id="c6e75-267">**allocates** 모든 블록 풀에서 수행된 총 할당 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-267">**allocates** Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="c6e75-268">**releases** 모든 블록 풀에서 수행된 총 해제 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-268">**releases**  Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="c6e75-269">**suspensions** 모든 블록 풀의 총 스레드 할당 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-269">**suspensions**   Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="c6e75-270">**timeouts** 모든 블록 풀의 총 할당 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-270">**timeouts**  Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-271">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-271">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-272">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-272">Return Values</span></span>

- <span data-ttu-id="c6e75-273">**TX_SUCCESS**(0x00) 블록 풀 시스템 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-273">**TX_SUCCESS** (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="c6e75-274">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-275">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-275">Allowed From</span></span>

<span data-ttu-id="c6e75-276">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-277">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-277">Example</span></span>

```c
ULONG       allocates;
ULONG       releases;
ULONG       suspensions;
ULONG       timeouts;

/* Retrieve performance information on all the block pools in
the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
    &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-278">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-278">See Also</span></span>

- <span data-ttu-id="c6e75-279">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-279">tx_block_allocate</span></span>
- <span data-ttu-id="c6e75-280">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-280">tx_block_pool_create</span></span>
- <span data-ttu-id="c6e75-281">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-281">tx_block_pool_delete</span></span>
- <span data-ttu-id="c6e75-282">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-282">tx_block_pool_info_get</span></span>
- <span data-ttu-id="c6e75-283">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-283">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-284">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-284">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="c6e75-285">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-285">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="c6e75-286">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-286">tx_block_pool_prioritize</span></span>

<span data-ttu-id="c6e75-287">블록 풀 일시 중단 목록의 우선 순위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-287">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-288">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-288">Prototype</span></span>

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-289">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-289">Description</span></span>

<span data-ttu-id="c6e75-290">이 서비스는 일시 중단 목록 맨 앞에 있는, 이 풀의 메모리 블록 때문에 일시 중단된 스레드를 가장 높은 우선 순위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-290">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="c6e75-291">다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-291">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-292">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-292">Parameters</span></span>

- <span data-ttu-id="c6e75-293">**pool_ptr** 메모리 블록 풀 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-293">**pool_ptr** Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-294">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-294">Return Values</span></span>

- <span data-ttu-id="c6e75-295">**TX_SUCCESS**(0x00) 블록 풀 우선 순위 지정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-295">**TX_SUCCESS** (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="c6e75-296">**TX_POOL_ERROR**(0x02) 잘못된 메모리 블록 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-296">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-297">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-297">Allowed From</span></span>

<span data-ttu-id="c6e75-298">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-298">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-299">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-299">Preemption Possible</span></span>

<span data-ttu-id="c6e75-300">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-300">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-301">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-301">Example</span></span>
```c
TX_BLOCK_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_block_release call will wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-302">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-302">See Also</span></span>

- <span data-ttu-id="c6e75-303">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-303">tx_block_allocate</span></span>
- <span data-ttu-id="c6e75-304">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-304">tx_block_pool_create</span></span>
- <span data-ttu-id="c6e75-305">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-305">tx_block_pool_delete</span></span>
- <span data-ttu-id="c6e75-306">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-306">tx_block_pool_info_get</span></span>
- <span data-ttu-id="c6e75-307">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-307">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-308">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-308">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-309">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-309">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="c6e75-310">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-310">tx_block_release</span></span>

<span data-ttu-id="c6e75-311">고정된 크기의 메모리 블록을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-311">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-312">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-312">Prototype</span></span>

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a><span data-ttu-id="c6e75-313">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-313">Description</span></span>

<span data-ttu-id="c6e75-314">이 서비스는 이전에 할당된 블록을 연결된 메모리 풀로 다시 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-314">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="c6e75-315">이 풀의 메모리 블록을 기다리는 일시 중단된 스레드가 하나 이상인 경우 일시 중단된 첫 번째 스레드에 이 메모리 블록이 제공되고 해당 스레드는 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-315">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="c6e75-316">애플리케이션은 메모리 블록 영역이 풀로 다시 해제된 후에는 이 메모리 블록 영역을 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-316">*The application must prevent using a memory block area after it has been released back to the pool.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-317">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-317">Parameters</span></span>

- <span data-ttu-id="c6e75-318">**block_ptr** 이전에 할당된 메모리 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-318">**block_ptr** Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-319">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-319">Return Values</span></span>

- <span data-ttu-id="c6e75-320">**TX_SUCCESS**(0x00) 메모리 블록 해제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-320">**TX_SUCCESS** (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="c6e75-321">**TX_PTR_ERROR**(0x03) 메모리 블록에 대한 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-321">**TX_PTR_ERROR** (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-322">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-322">Allowed From</span></span>

<span data-ttu-id="c6e75-323">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-323">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-324">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-324">Preemption Possible</span></span>

<span data-ttu-id="c6e75-325">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-325">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-326">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-326">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;
UINT status;

/* Release a memory block back to my_pool. Assume that the
pool has been created and the memory block has been
allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
to by memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-327">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-327">See Also</span></span>

- <span data-ttu-id="c6e75-328">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-328">tx_block_allocate</span></span>
- <span data-ttu-id="c6e75-329">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-329">tx_block_pool_create</span></span>
- <span data-ttu-id="c6e75-330">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-330">tx_block_pool_delete</span></span>
- <span data-ttu-id="c6e75-331">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-331">tx_block_pool_info_get</span></span>
- <span data-ttu-id="c6e75-332">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-332">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-333">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-333">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-334">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-334">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="c6e75-335">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-335">tx_byte_allocate</span></span>

<span data-ttu-id="c6e75-336">메모리 바이트를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-336">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-337">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-337">Prototype</span></span>

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c6e75-338">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-338">Description</span></span>

<span data-ttu-id="c6e75-339">이 서비스는 지정된 메모리 바이트 풀에서 지정된 바이트 수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-339">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-340">애플리케이션 코드가 할당된 메모리 블록의 외부에 쓰지 않도록 하는 것이 중요합니다. 외부에 쓰면 인접한(일반적으로 이후) 메모리 블록에 손상이 발생합니다. 결과를 예측할 수 없으며 치명적인 결과가 발생하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-340">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-341">이 서비스의 성능은 블록 크기의 함수와 풀의 조각화 양에 따라 결정됩니다. 따라서 이 서비스는 시간이 중요한 스레드를 실행하는 중에는 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-341">*The performance of this service is a function of the block size and the amount of fragmentation in the pool. Hence, this service should not be used during time-critical threads of execution.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-342">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-342">Parameters</span></span>

- <span data-ttu-id="c6e75-343">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-343">**pool_ptr**</span></span> <br><span data-ttu-id="c6e75-344">이전에 만든 메모리 블록 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-344">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="c6e75-345">**memory_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-345">**memory_ptr**</span></span> <br><span data-ttu-id="c6e75-346">대상 메모리 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-346">Pointer to a destination memory pointer.</span></span> <span data-ttu-id="c6e75-347">할당에 성공하면 할당된 메모리 영역 주소가 이 매개 변수에서 가리키는 위치에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-347">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="c6e75-348">**memory_size**</span><span class="sxs-lookup"><span data-stu-id="c6e75-348">**memory_size**</span></span> <br><span data-ttu-id="c6e75-349">요청된 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-349">Number of bytes requested.</span></span>
- <span data-ttu-id="c6e75-350">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="c6e75-350">**wait_option**</span></span> <br><span data-ttu-id="c6e75-351">사용할 수 있는 메모리가 충분하지 않은 경우의 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-351">Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="c6e75-352">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-352">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c6e75-353">**TX_NO_WAIT**(0x00000000) - **TX_NO_WAIT** 를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-353">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="c6e75-354">초기화에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-354">*This is the only valid option if the service is called from initialization.*</span></span>
  - <span data-ttu-id="c6e75-355">**TX_WAIT_FOREVER** 0xFFFFFFFF) - **TX_WAIT_FOREVER** 를 선택하면 충분한 메모리를 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-355">**TX_WAIT_FOREVER** 0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until enough memory is available.</span></span>
  - <span data-ttu-id="c6e75-356">‘시간 제한 값’(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 메모리를 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-356">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-357">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-357">Return Values</span></span>

- <span data-ttu-id="c6e75-358">**TX_SUCCESS**(0x00) 메모리 할당에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-358">**TX_SUCCESS** (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="c6e75-359">**TX_DELETED**(0x01) 스레드가 일시 중단된 동안 메모리 풀이 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-359">**TX_DELETED** (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="c6e75-360">**TX_NO_MEMORY**(0x10) 서비스가 지정된 대기 시간 내에 메모리를 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-360">**TX_NO_MEMORY** (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="c6e75-361">**TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-361">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="c6e75-362">**TX_POOL_ERROR**(0x02) 잘못된 메모리 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-362">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="c6e75-363">**TX_PTR_ERROR**(0x03) 대상 포인터에 대한 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-363">**TX_PTR_ERROR** (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="c6e75-364">**TX_SIZE_ERROR**(0x05) 요청된 크기가 0이거나 풀보다 큽니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-364">**TX_SIZE_ERROR** (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="c6e75-365">**TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-365">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="c6e75-366">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-366">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-367">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-367">Allowed From</span></span>

<span data-ttu-id="c6e75-368">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-368">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-369">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-369">Preemption Possible</span></span>

<span data-ttu-id="c6e75-370">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-370">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-371">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-371">Example</span></span>
```c
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT status;
/* Allocate a 112 byte memory area from my_pool. Assume
that the pool has already been created with a call to
tx_byte_pool_create. */
status = tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
    112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
address of the allocated memory area. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-372">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-372">See Also</span></span>

- <span data-ttu-id="c6e75-373">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-373">tx_byte_pool_create</span></span>
- <span data-ttu-id="c6e75-374">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-374">tx_byte_pool_delete</span></span>
- <span data-ttu-id="c6e75-375">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-375">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="c6e75-376">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-376">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-377">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-377">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-378">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-378">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="c6e75-379">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-379">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="c6e75-380">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-380">tx_byte_pool_create</span></span>

<span data-ttu-id="c6e75-381">메모리 바이트 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-381">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-382">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-382">Prototype</span></span>

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="c6e75-383">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-383">Description</span></span>

<span data-ttu-id="c6e75-384">이 서비스는 지정된 영역에 메모리 바이트 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-384">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="c6e75-385">처음에는 풀이 기본적으로 하나의 매우 큰 빈 블록으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-385">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="c6e75-386">하지만 할당이 진행되면 이 풀이 더 작은 블록으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-386">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-387">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-387">Parameters</span></span>

- <span data-ttu-id="c6e75-388">**pool_ptr** 메모리 풀 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-388">**pool_ptr** Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="c6e75-389">**name_ptr** 메모리 풀 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-389">**name_ptr** Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="c6e75-390">**pool_start** 메모리 풀의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-390">**pool_start** Starting address of the memory pool.</span></span> <span data-ttu-id="c6e75-391">시작 주소는 ULONG 데이터 형식의 크기에 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-391">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="c6e75-392">**pool_size** 메모리 풀에 사용할 수 있는 총 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-392">**pool_size** Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-393">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-393">Return Values</span></span>

- <span data-ttu-id="c6e75-394">**TX_SUCCESS**(0x00) 메모리 풀 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-394">**TX_SUCCESS** (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="c6e75-395">**TX_POOL_ERROR**(0x02) 잘못된 메모리 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-395">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="c6e75-396">포인터가 NULL이거나 풀이 이미 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-396">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="c6e75-397">**TX_PTR_ERROR**(0x03) 풀의 시작 주소가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-397">**TX_PTR_ERROR** (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="c6e75-398">**TX_SIZE_ERROR**(0x05) 풀 크기가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-398">**TX_SIZE_ERROR** (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="c6e75-399">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-399">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-400">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-400">Allowed From</span></span>

<span data-ttu-id="c6e75-401">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-401">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-402">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-402">Preemption Possible</span></span>

<span data-ttu-id="c6e75-403">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-403">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-404">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-404">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Create a memory pool whose total size is 2000 bytes
starting at address 0x500000. */
status = tx_byte_pool_create(&my_pool, "my_pool_name",
    (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
allocating memory. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-405">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-405">See Also</span></span>

- <span data-ttu-id="c6e75-406">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-406">tx_byte_allocate</span></span>
- <span data-ttu-id="c6e75-407">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-407">tx_byte_pool_delete</span></span>
- <span data-ttu-id="c6e75-408">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-408">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="c6e75-409">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-409">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-410">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-410">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-411">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-411">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="c6e75-412">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-412">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="c6e75-413">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-413">tx_byte_pool_delete</span></span>

<span data-ttu-id="c6e75-414">메모리 바이트 풀을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-414">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-415">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-415">Prototype</span></span>

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-416">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-416">Description</span></span>

<span data-ttu-id="c6e75-417">이 서비스는 지정된 메모리 바이트 풀을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-417">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="c6e75-418">이 풀의 메모리를 기다리는 일시 중단된 모든 스레드는 다시 시작되며 **TX_DELETED** 반환 상태가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-418">All threads suspended waiting for memory from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-419">이 서비스가 완료된 후 사용할 수 있는 풀과 연결된 메모리 영역은 애플리케이션에서 관리해야 합니다. 또한 애플리케이션은 삭제된 풀이나 해당 풀에서 이전에 할당된 메모리를 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-419">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or memory previously allocated from it.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-420">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-420">Parameters</span></span>

- <span data-ttu-id="c6e75-421">**pool_ptr** 이전에 만든 메모리 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-421">**pool_ptr** Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-422">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-422">Return Values</span></span>

- <span data-ttu-id="c6e75-423">**TX_SUCCESS**(0x00) 메모리 풀 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-423">**TX_SUCCESS** (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="c6e75-424">**TX_POOL_ERROR**(0x02) 잘못된 메모리 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-424">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="c6e75-425">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-425">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-426">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-426">Allowed From</span></span>

<span data-ttu-id="c6e75-427">스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-427">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-428">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-428">Preemption Possible</span></span>

<span data-ttu-id="c6e75-429">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-429">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-430">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-430">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-431">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-431">See Also</span></span>

- <span data-ttu-id="c6e75-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-432">tx_byte_allocate</span></span>
- <span data-ttu-id="c6e75-433">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-433">tx_byte_pool_create</span></span>
- <span data-ttu-id="c6e75-434">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-434">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="c6e75-435">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-435">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-436">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-436">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-437">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-437">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="c6e75-438">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-438">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="c6e75-439">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-439">tx_byte_pool_info_get</span></span>

<span data-ttu-id="c6e75-440">바이트 풀에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-440">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-441">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-441">Prototype</span></span>

```c
UINT tx_byte_pool_info_get(
    TX_BYTE_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *fragments,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BYTE_POOL **next_pool);
```

### <a name="description"></a><span data-ttu-id="c6e75-442">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-442">Description</span></span>

<span data-ttu-id="c6e75-443">이 서비스는 지정된 메모리 바이트 풀에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-443">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-444">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-444">Parameters</span></span>

- <span data-ttu-id="c6e75-445">**pool_ptr** 이전에 만든 메모리 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-445">**pool_ptr** Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="c6e75-446">**name** 바이트 풀 이름에 대한 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-446">**name** Pointer to destination for the pointer to the byte pool's name.</span></span>
- <span data-ttu-id="c6e75-447">**available** 풀에서 사용 가능한 바이트 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-447">**available** Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="c6e75-448">**fragments** 바이트 풀에 있는 총 메모리 조각 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-448">**fragments** Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="c6e75-449">**first_suspended** 이 바이트 풀의 일시 중단 목록에 있는 첫 번째 스레드 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-449">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="c6e75-450">**suspended_count** 이 바이트 풀의 현재 일시 중단된 스레드 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-450">**suspended_count** Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="c6e75-451">**next_pool** 다음에 만들 바이트 풀 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-451">**next_pool** Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-452">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-452">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-453">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-453">Return Values</span></span>

- <span data-ttu-id="c6e75-454">**TX_SUCCESS**(0x00) 풀 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-454">**TX_SUCCESS** (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="c6e75-455">**TX_POOL_ERROR**(0x02) 잘못된 메모리 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-455">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-456">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-456">Allowed From</span></span>

<span data-ttu-id="c6e75-457">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-457">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-458">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-458">Preemption Possible</span></span>

<span data-ttu-id="c6e75-459">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-459">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-460">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-460">Example</span></span>

```c
TX_BYTE_POOL my_pool;
CHAR *name;
ULONG available;
ULONG fragments;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BYTE_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_byte_pool_info_get(&my_pool, &name,
  &available, &fragments,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-461">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-461">See Also</span></span>

- <span data-ttu-id="c6e75-462">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-462">tx_byte_allocate</span></span>
- <span data-ttu-id="c6e75-463">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-463">tx_byte_pool_create</span></span>
- <span data-ttu-id="c6e75-464">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-464">tx_byte_pool_delete</span></span>
- <span data-ttu-id="c6e75-465">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-465">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-466">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-466">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-467">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-467">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="c6e75-468">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-468">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="c6e75-469">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-469">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="c6e75-470">바이트 풀 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-470">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-471">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-471">Prototype</span></span>

```c
UINT tx_byte_pool_performance_info_get(
    TX_BYTE_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *fragments_searched, 
    ULONG *merges, 
    ULONG *splits,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="c6e75-472">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-472">Description</span></span>

<span data-ttu-id="c6e75-473">이 서비스는 지정된 메모리 바이트 풀에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-473">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-474">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. </span><span class="sxs-lookup"><span data-stu-id="c6e75-474">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-475">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-475">Parameters</span></span>

- <span data-ttu-id="c6e75-476">**pool_ptr** 이전에 만든 메모리 바이트 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-476">**pool_ptr** Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="c6e75-477">**allocates** 이 풀에서 수행된 할당 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-477">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="c6e75-478">**releases** 이 풀에서 수행된 해제 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-478">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="c6e75-479">**fragments_searched** 이 풀에서 할당 요청 중 검색된 내부 메모리 조각 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-479">**fragments_searched** Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="c6e75-480">**merges** 이 풀에서 할당 요청 중 병합된 내부 메모리 블록 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-480">**merges** Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="c6e75-481">**splits** 이 풀에서 할당 요청 중 만들어진 내부 메모리 블록 분할(조각) 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-481">**splits** Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="c6e75-482">**suspensions** 이 풀의 스레드 할당 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-482">**suspensions** Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="c6e75-483">**timeouts** 이 풀의 할당 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-483">**timeouts** Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-484">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-484">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-485">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-485">Return Values</span></span>

- <span data-ttu-id="c6e75-486">**TX_SUCCESS**(0x00) 바이트 풀 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-486">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="c6e75-487">**TX_PTR_ERROR**(0x03) 잘못된 바이트 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-487">**TX_PTR_ERROR** (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="c6e75-488">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-488">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-489">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-489">Allowed From</span></span>

<span data-ttu-id="c6e75-490">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-490">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-491">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-491">Example</span></span>

```c
TX_BYTE_POOL my_pool;
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created byte
pool. */
status = tx_byte_pool_performance_info_get(&my_pool,
  &fragments_searched,
  &merges, &splits,
  &allocates, &releases,
  &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="c6e75-492">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-492">See Also</span></span>

- <span data-ttu-id="c6e75-493">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-493">tx_byte_allocate</span></span>
- <span data-ttu-id="c6e75-494">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-494">tx_byte_pool_create</span></span>
- <span data-ttu-id="c6e75-495">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-495">tx_byte_pool_delete</span></span>
- <span data-ttu-id="c6e75-496">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-496">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="c6e75-497">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-497">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-498">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-498">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="c6e75-499">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-499">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="c6e75-500">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-500">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="c6e75-501">바이트 풀 시스템 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-501">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-502">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-502">Prototype</span></span>

```c
UINT tx_byte_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *fragments_searched, 
    ULONG *merges,
    ULONG *splits, 
    ULONG *suspensions, 
    ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="c6e75-503">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-503">Description</span></span>

<span data-ttu-id="c6e75-504">이 서비스는 시스템의 모든 메모리 바이트 풀에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-504">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-505">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. </span><span class="sxs-lookup"><span data-stu-id="c6e75-505">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-506">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-506">Parameters</span></span>

- <span data-ttu-id="c6e75-507">**allocates** 이 풀에서 수행된 할당 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-507">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="c6e75-508">**releases** 이 풀에서 수행된 해제 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-508">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="c6e75-509">**fragments_searched** 모든 바이트 풀에서 할당 요청 중 검색된 총 내부 메모리 조각 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-509">**fragments_searched** Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="c6e75-510">**merges** 모든 바이트 풀에서 할당 요청 중 병합된 총 내부 메모리 블록 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-510">**merges** Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="c6e75-511">**splits** 모든 바이트 풀에서 할당 요청 중 만들어진 총 내부 메모리 블록 분할(조각) 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-511">**splits** Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="c6e75-512">**suspensions** 모든 바이트 풀의 총 스레드 할당 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-512">**suspensions** Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="c6e75-513">**timeouts** 모든 바이트 풀의 총 할당 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-513">**timeouts** Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-514">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-514">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-515">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-515">Return Values</span></span>

- <span data-ttu-id="c6e75-516">**TX_SUCCESS**(0x00) 바이트 풀 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-516">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="c6e75-517">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-517">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-518">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-518">Allowed From</span></span>

 <span data-ttu-id="c6e75-519">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-519">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-520">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-520">Example</span></span>

```c
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all byte pools in the
system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
  &merges, &splits, &allocates, &releases,
  &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-521">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-521">See Also</span></span>

- <span data-ttu-id="c6e75-522">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-522">tx_byte_allocate</span></span>
- <span data-ttu-id="c6e75-523">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-523">tx_byte_pool_create</span></span>
- <span data-ttu-id="c6e75-524">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-524">tx_byte_pool_delete</span></span>
- <span data-ttu-id="c6e75-525">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-525">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="c6e75-526">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-526">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-527">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-527">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="c6e75-528">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-528">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="c6e75-529">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-529">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="c6e75-530">바이트 풀 일시 중단 목록의 우선 순위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-530">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-531">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-531">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="c6e75-532">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-532">Description</span></span>

<span data-ttu-id="c6e75-533">이 서비스는 일시 중단 목록 맨 앞에 있는, 이 풀의 메모리 때문에 일시 중단된 스레드를 가장 높은 우선 순위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-533">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="c6e75-534">다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-534">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-535">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-535">Parameters</span></span>

- <span data-ttu-id="c6e75-536">**pool_ptr** 메모리 풀 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-536">**pool_ptr** Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-537">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-537">Return Values</span></span>

- <span data-ttu-id="c6e75-538">**TX_SUCCESS**(0x00) 메모리 풀 우선 순위 지정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-538">**TX_SUCCESS** (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="c6e75-539">**TX_POOL_ERROR**(0x02) 잘못된 메모리 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-539">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-540">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-540">Allowed From</span></span>

<span data-ttu-id="c6e75-541">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-542">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-542">Preemption Possible</span></span>

<span data-ttu-id="c6e75-543">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-543">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-544">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-544">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_byte_release call will wake up this thread,
if there is enough memory to satisfy its request. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-545">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-545">See Also</span></span>

- <span data-ttu-id="c6e75-546">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-546">tx_byte_allocate</span></span>
- <span data-ttu-id="c6e75-547">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-547">tx_byte_pool_create</span></span>
- <span data-ttu-id="c6e75-548">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-548">tx_byte_pool_delete</span></span>
- <span data-ttu-id="c6e75-549">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-549">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="c6e75-550">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-550">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-551">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-551">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-552">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-552">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="c6e75-553">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="c6e75-553">tx_byte_release</span></span>

<span data-ttu-id="c6e75-554">바이트를 메모리 풀로 다시 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-554">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-555">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-555">Prototype</span></span>

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-556">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-556">Description</span></span>

<span data-ttu-id="c6e75-557">이 서비스는 이전에 할당된 메모리 영역을 연결된 풀로 다시 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-557">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="c6e75-558">이 풀의 메모리를 기다리는 일시 중단된 스레드가 하나 이상인 경우 해당 메모리가 고갈될 때까지 또는 일시 중단된 스레드가 더 이상 없을 때까지 일시 중단된 각 스레드에 메모리가 제공되고 스레드는 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-558">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="c6e75-559">일시 중단된 스레드에 메모리를 할당하는 이 프로세스는 항상 일시 중단된 첫 번째 스레드부터 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-559">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-560">애플리케이션은 메모리 영역이 해제된 후에는 이 메모리 영역을 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-560">*The application must prevent using the memory area after it is released.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-561">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-561">Parameters</span></span>

- <span data-ttu-id="c6e75-562">**memory_ptr** 이전에 할당된 메모리 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-562">**memory_ptr** Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-563">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-563">Return Values</span></span>

- <span data-ttu-id="c6e75-564">**TX_SUCCESS**(0x00) 메모리 해제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-564">**TX_SUCCESS** (0x00) Successful memory release.</span></span>
- <span data-ttu-id="c6e75-565">**TX_PTR_ERROR**(0x03) 잘못된 메모리 영역 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-565">**TX_PTR_ERROR** (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="c6e75-566">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-566">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-567">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-567">Allowed From</span></span>

<span data-ttu-id="c6e75-568">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-568">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-569">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-569">Preemption Possible</span></span>

<span data-ttu-id="c6e75-570">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-570">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-571">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-571">Example</span></span>

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-572">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-572">See Also</span></span>

- <span data-ttu-id="c6e75-573">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="c6e75-573">tx_byte_allocate</span></span>
- <span data-ttu-id="c6e75-574">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-574">tx_byte_pool_create</span></span>
- <span data-ttu-id="c6e75-575">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-575">tx_byte_pool_delete</span></span>
- <span data-ttu-id="c6e75-576">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-576">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="c6e75-577">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-577">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="c6e75-578">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-578">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-579">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-579">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="c6e75-580">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-580">tx_event_flags_create</span></span>

<span data-ttu-id="c6e75-581">이벤트 플래그 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-581">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-582">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-582">Prototype</span></span>

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-583">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-583">Description</span></span>

<span data-ttu-id="c6e75-584">이 서비스는 32개의 이벤트 플래그로 된 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-584">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="c6e75-585">그룹에 있는 32개의 이벤트 플래그 모두 0으로 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-585">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="c6e75-586">각 이벤트 플래그는 단일 비트로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-586">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-587">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-587">Parameters</span></span>

- <span data-ttu-id="c6e75-588">**group_ptr** 이벤트 플래그 그룹 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-588">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="c6e75-589">**name_ptr** 이벤트 플래그 그룹 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-589">**name_ptr** Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-590">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-590">Return Values</span></span>

- <span data-ttu-id="c6e75-591">**TX_SUCCESS**(0x00) 이벤트 그룹 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-591">**TX_SUCCESS** (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="c6e75-592">**TX_GROUP_ERROR**(0x06) 잘못된 이벤트 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-592">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="c6e75-593">포인터가 **NULL** 이거나 이벤트 그룹을 이미 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-593">Either the pointer is **NULL** or the event group is already created.</span></span>
- <span data-ttu-id="c6e75-594">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-594">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-595">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-595">Allowed From</span></span>

<span data-ttu-id="c6e75-596">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-596">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-597">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-597">Preemption Possible</span></span>

<span data-ttu-id="c6e75-598">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-598">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-599">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-599">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-600">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-600">See Also</span></span>

- <span data-ttu-id="c6e75-601">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-601">tx_event_flags_delete</span></span>
- <span data-ttu-id="c6e75-602">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-602">tx_event_flags_get</span></span>
- <span data-ttu-id="c6e75-603">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-603">tx_event_flags_info_get</span></span>
- <span data-ttu-id="c6e75-604">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-604">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="c6e75-605">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-605">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-606">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="c6e75-606">tx_event_flags_set</span></span>
- <span data-ttu-id="c6e75-607">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-607">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="c6e75-608">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-608">tx_event_flags_delete</span></span>

<span data-ttu-id="c6e75-609">이벤트 플래그 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-609">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-610">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-610">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-611">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-611">Description</span></span>

<span data-ttu-id="c6e75-612">이 서비스는 지정된 이벤트 플래그 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-612">This service deletes the specified event flags group.</span></span> <span data-ttu-id="c6e75-613">이 그룹의 이벤트를 기다리는 일시 중단된 모든 스레드는 다시 시작되며 TX_DELETED 반환 상태가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-613">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="c6e75-614">애플리케이션은 이 이벤트 플래그 그룹을 삭제하기 전에 이 이벤트 플래그 그룹에 대한 설정 알림 콜백이 완료되었는지(또는 사용하지 않도록 설정되었는지) 확인해야 합니다. 또한 애플리케이션은 이후에는 삭제된 이벤트 플래그 그룹을 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-614">*The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group. In addition, the application must prevent all future use of a deleted event flags group.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-615">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-615">Parameters</span></span>

- <span data-ttu-id="c6e75-616">**group_ptr** 이전에 만든 이벤트 플래그 그룹에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-616">**group_ptr** Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-617">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-617">Return Values</span></span>

- <span data-ttu-id="c6e75-618">**TX_SUCCESS**(0x00) 이벤트 플래그 그룹 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-618">**TX_SUCCESS** (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="c6e75-619">**TX_GROUP_ERROR**(0x06) 잘못된 이벤트 플래그 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-619">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="c6e75-620">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-620">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-621">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-621">Allowed From</span></span>

<span data-ttu-id="c6e75-622">스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-622">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-623">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-623">Preemption Possible</span></span>

<span data-ttu-id="c6e75-624">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-624">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-625">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-625">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Delete event flags group. Assume that the group has
already been created with a call to
tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-626">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-626">See Also</span></span>

- <span data-ttu-id="c6e75-627">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-627">tx_event_flags_create</span></span>
- <span data-ttu-id="c6e75-628">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-628">tx_event_flags_get</span></span>
- <span data-ttu-id="c6e75-629">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-629">tx_event_flags_info_get</span></span>
- <span data-ttu-id="c6e75-630">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-630">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="c6e75-631">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-631">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-632">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="c6e75-632">tx_event_flags_set</span></span>
- <span data-ttu-id="c6e75-633">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-633">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="c6e75-634">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-634">tx_event_flags_get</span></span>

<span data-ttu-id="c6e75-635">이벤트 플래그 그룹의 이벤트 플래그를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-635">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-636">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-636">Prototype</span></span>

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c6e75-637">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-637">Description</span></span>

<span data-ttu-id="c6e75-638">이 서비스는 지정된 이벤트 플래그 그룹의 이벤트 플래그를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-638">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="c6e75-639">각 이벤트 플래그 그룹에는 32개의 이벤트 플래그가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-639">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="c6e75-640">각 플래그는 단일 비트로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-640">Each flag is represented by a single bit.</span></span> <span data-ttu-id="c6e75-641">이 서비스는 입력 매개 변수를 통해 선택한 대로 다양한 이벤트 플래그 조합을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-641">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-642">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-642">Parameters</span></span>

- <span data-ttu-id="c6e75-643">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-643">**group_ptr**</span></span> <br><span data-ttu-id="c6e75-644">이전에 만든 이벤트 플래그 그룹에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-644">Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="c6e75-645">**requested_flags**</span><span class="sxs-lookup"><span data-stu-id="c6e75-645">**requested_flags**</span></span> <br><span data-ttu-id="c6e75-646">요청된 이벤트 플래그를 나타내는 부호 없는 32비트 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-646">32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="c6e75-647">**get_option**</span><span class="sxs-lookup"><span data-stu-id="c6e75-647">**get_option**</span></span> <br><span data-ttu-id="c6e75-648">요청된 이벤트 플래그가 전체가 필요한지 일부가 필요한지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-648">Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="c6e75-649">유효한 선택 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-649">The following are valid selections:</span></span>

  - <span data-ttu-id="c6e75-650">**TX_AND**(0x02)</span><span class="sxs-lookup"><span data-stu-id="c6e75-650">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="c6e75-651">**TX_AND_CLEAR**(0x03)</span><span class="sxs-lookup"><span data-stu-id="c6e75-651">**TX_AND_CLEAR** (0x03)</span></span>
  - <span data-ttu-id="c6e75-652">**TX_OR**(0x00)</span><span class="sxs-lookup"><span data-stu-id="c6e75-652">**TX_OR** (0x00)</span></span>
  - <span data-ttu-id="c6e75-653">**TX_OR_CLEAR**(0x01)</span><span class="sxs-lookup"><span data-stu-id="c6e75-653">**TX_OR_CLEAR** (0x01)</span></span>

    <span data-ttu-id="c6e75-654">TX_AND 또는 TX_AND_CLEAR를 선택하면 모든 이벤트 플래그가 그룹에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-654">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="c6e75-655">TX_OR 또는 TX_OR_CLEAR를 선택하면 모든 이벤트 플래그가 충족되는 것으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-655">Selecting TX_OR or TX_OR_CLEAR     specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="c6e75-656">TX_AND_CLEAR 또는 TX_OR_CLEAR가 지정된 경우 요청을 충족시키는 이벤트 플래그를 지웁니다(0으로 설정함).</span><span class="sxs-lookup"><span data-stu-id="c6e75-656">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="c6e75-657">**actual_flags_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-657">**actual_flags_ptr**</span></span> <br><span data-ttu-id="c6e75-658">검색된 이벤트 플래그가 배치되는 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-658">Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="c6e75-659">가져온 실제 플래그는 요청되지 않은 플래그를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-659">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="c6e75-660">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="c6e75-660">**wait_option**</span></span>  <br><span data-ttu-id="c6e75-661">선택한 이벤트 플래그가 설정되지 않은 경우의 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-661">Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="c6e75-662">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c6e75-663">**TX_NO_WAIT**(0x00000000) - TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-663">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="c6e75-664">초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-664">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="c6e75-665">**TX_WAIT_FOREVER** 시간 제한 값(0xFFFFFFFF) - TX_WAIT_FOREVER를 선택하면 이벤트 플래그를 사용할 수 있을 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-665">**TX_WAIT_FOREVER** timeout value  (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>
  - <span data-ttu-id="c6e75-666">시간 제한 값(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 이벤트 플래그를 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-666">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-667">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-667">Return Values</span></span>

- <span data-ttu-id="c6e75-668">**TX_SUCCESS**(0x00) 이벤트 플래그 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-668">**TX_SUCCESS** (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="c6e75-669">**TX_DELETED**(0x01) 스레드가 일시 중단된 동안 이벤트 플래그 그룹이 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-669">**TX_DELETED** (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="c6e75-670">**TX_NO_EVENTS**(0x07) 서비스가 지정된 대기 시간 내에 지정된 이벤트를 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-670">**TX_NO_EVENTS** (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="c6e75-671">**TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-671">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="c6e75-672">**TX_GROUP_ERROR**(0x06) 잘못된 이벤트 플래그 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-672">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="c6e75-673">**TX_PTR_ERROR**(0x03) 실제 이벤트 플래그에 대한 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-673">**TX_PTR_ERROR** (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="c6e75-674">**TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-674">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="c6e75-675">**TX_OPTION_ERROR**(0x08) 잘못된 get-option을 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-675">**TX_OPTION_ERROR** (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-676">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-676">Allowed From</span></span>

<span data-ttu-id="c6e75-677">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-677">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-678">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-678">Preemption Possible</span></span>

<span data-ttu-id="c6e75-679">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-679">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-680">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-680">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG actual_events;
UINT status;

/* Request that event flags 0, 4, and 8 are all set. Also,
if they are set they should be cleared. If the event
flags are not set, this service suspends for a maximum of
20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
    TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
actual events obtained. */
```

<span data-ttu-id="c6e75-681">**참고 항목**</span><span class="sxs-lookup"><span data-stu-id="c6e75-681">**See Also**</span></span>

- <span data-ttu-id="c6e75-682">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-682">tx_event_flags_create</span></span>
- <span data-ttu-id="c6e75-683">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-683">tx_event_flags_delete</span></span>
- <span data-ttu-id="c6e75-684">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-684">tx_event_flags_info_get</span></span>
- <span data-ttu-id="c6e75-685">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-685">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="c6e75-686">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-686">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-687">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="c6e75-687">tx_event_flags_set</span></span>
- <span data-ttu-id="c6e75-688">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-688">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_info_get"></a><span data-ttu-id="c6e75-689">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-689">tx_event_flags_info_get</span></span>

<span data-ttu-id="c6e75-690">이벤트 플래그 그룹에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-690">Retrieve information about event flags group</span></span>

<span data-ttu-id="c6e75-691">**프로토타입**</span><span class="sxs-lookup"><span data-stu-id="c6e75-691">**Prototype**</span></span>

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

<span data-ttu-id="c6e75-692">**설명**</span><span class="sxs-lookup"><span data-stu-id="c6e75-692">**Description**</span></span>

<span data-ttu-id="c6e75-693">이 서비스는 지정된 이벤트 플래그 그룹에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-693">This service retrieves information about the specified event flags group.</span></span>

<span data-ttu-id="c6e75-694">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="c6e75-694">**Parameters**</span></span>

- <span data-ttu-id="c6e75-695">**group_ptr** 이벤트 플래그 그룹 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-695">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="c6e75-696">**name** 이벤트 플래그 그룹의 이름에 대한 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-696">**name** Pointer to destination for the pointer to the event flags group's name.</span></span>
- <span data-ttu-id="c6e75-697">**current_flags** 이벤트 플래그 그룹에서 현재 설정된 플래그 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-697">**current_flags** Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="c6e75-698">**first_suspended** 이 이벤트 플래그 그룹의 일시 중단 목록에 있는 첫 번째 스레드 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-698">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="c6e75-699">**suspended_count** 이 이벤트 플래그 그룹에서 현재 일시 중단된 스레드 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-699">**suspended_count** Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="c6e75-700">**next_group** 다음에 만들 이벤트 플래그 그룹 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-700">**next_group** Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-701">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-701">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-702">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-702">Return Values</span></span>

- <span data-ttu-id="c6e75-703">**TX_SUCCESS**(0x00) 이벤트 그룹 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-703">**TX_SUCCESS** (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="c6e75-704">**TX_GROUP_ERROR**(0x06) 잘못된 이벤트 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-704">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-705">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-705">Allowed From</span></span>

<span data-ttu-id="c6e75-706">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-706">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-707">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-707">Preemption Possible</span></span>

<span data-ttu-id="c6e75-708">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-708">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-709">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-709">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_group;
CHAR *name;
ULONG current_flags;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_EVENT_FLAGS_GROUP *next_group;
UINT status;

/* Retrieve information about the previously created
event flags group "my_event_group." */
status = tx_event_flags_info_get(&my_event_group, &name,
    &current_flags,
    &first_suspended, &suspended_count,
    &next_group);
/* If status equals TX_SUCCESS, the information requested is
valid. */
```
<span data-ttu-id="c6e75-710">**참고 항목**</span><span class="sxs-lookup"><span data-stu-id="c6e75-710">**See Also**</span></span>

- <span data-ttu-id="c6e75-711">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-711">tx_event_flags_create</span></span>
- <span data-ttu-id="c6e75-712">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-712">tx_event_flags_delete</span></span>
- <span data-ttu-id="c6e75-713">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-713">tx_event_flags_get</span></span>
- <span data-ttu-id="c6e75-714">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-714">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="c6e75-715">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-715">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-716">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="c6e75-716">tx_event_flags_set</span></span>
- <span data-ttu-id="c6e75-717">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-717">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="c6e75-718">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-718">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="c6e75-719">이벤트 플래그 그룹 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-719">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-720">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-720">Prototype</span></span>

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="c6e75-721">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-721">Description</span></span>

<span data-ttu-id="c6e75-722">이 서비스는 지정된 이벤트 플래그 그룹에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-722">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-723">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. </span><span class="sxs-lookup"><span data-stu-id="c6e75-723">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-724">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-724">Parameters</span></span>

- <span data-ttu-id="c6e75-725">**group_ptr** 이전에 만든 이벤트 플래그 그룹에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-725">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="c6e75-726">**sets** 이 그룹에서 수행된 이벤트 플래그 설정 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-726">**sets** Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="c6e75-727">**gets** 이 그룹에서 수행된 이벤트 플래그 가져오기 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-727">**gets** Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="c6e75-728">**suspensions** 이 그룹의 스레드 이벤트 플래그 가져오기 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-728">**suspensions** Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="c6e75-729">**timeouts** 이 그룹의 이벤트 플래그 가져오기 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-729">**timeouts** Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-730">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-730">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-731">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-731">Return Values</span></span>

- <span data-ttu-id="c6e75-732">**TX_SUCCESS**(0x00) 이벤트 플래그 그룹 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-732">**TX_SUCCESS** (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="c6e75-733">**TX_PTR_ERROR**(0x03) 잘못된 이벤트 플래그 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-733">**TX_PTR_ERROR** (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="c6e75-734">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-734">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-735">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-735">Allowed From</span></span>

<span data-ttu-id="c6e75-736">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-736">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-737">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-737">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flag_group;
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created event
flag group. */
status = tx_event_flags_performance_info_get(&my_event_flag_group,
    &sets, &gets, &suspensions,
    &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-738">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-738">See Also</span></span>

- <span data-ttu-id="c6e75-739">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-739">tx_event_flags_create</span></span>
- <span data-ttu-id="c6e75-740">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-740">tx_event_flags_delete</span></span>
- <span data-ttu-id="c6e75-741">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-741">tx_event_flags_get</span></span>
- <span data-ttu-id="c6e75-742">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-742">tx_event_flags_info_get</span></span>
- <span data-ttu-id="c6e75-743">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-743">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-744">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="c6e75-744">tx_event_flags_set</span></span>
- <span data-ttu-id="c6e75-745">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-745">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="c6e75-746">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-746">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="c6e75-747">성능 시스템 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-747">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-748">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-748">Prototype</span></span>

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="c6e75-749">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-749">Description</span></span>

<span data-ttu-id="c6e75-750">이 서비스는 시스템의 모든 이벤트 플래그 그룹에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-750">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-751">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. </span><span class="sxs-lookup"><span data-stu-id="c6e75-751">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-752">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-752">Parameters</span></span>

- <span data-ttu-id="c6e75-753">**sets** 모든 그룹에서 수행된 총 이벤트 플래그 설정 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-753">**sets** Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="c6e75-754">**gets** 모든 그룹에서 수행된 총 이벤트 플래그 가져오기 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-754">**gets** Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="c6e75-755">**suspensions** 모든 그룹의 총 스레드 이벤트 플래그 가져오기 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-755">**suspensions** Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="c6e75-756">**timeouts** 모든 그룹의 총 이벤트 플래그 가져오기 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-756">**timeouts** Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-757">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-757">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-758">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-758">Return Values</span></span>

- <span data-ttu-id="c6e75-759">**TX_SUCCESS**(0x00) 이벤트 플래그 시스템 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-759">**TX_SUCCESS** (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="c6e75-760">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-760">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-761">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-761">Example</span></span>

```c
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created event
flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-762">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-762">See Also</span></span>

- <span data-ttu-id="c6e75-763">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-763">tx_event_flags_create</span></span>
- <span data-ttu-id="c6e75-764">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-764">tx_event_flags_delete</span></span>
- <span data-ttu-id="c6e75-765">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-765">tx_event_flags_get</span></span>
- <span data-ttu-id="c6e75-766">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-766">tx_event_flags_info_get</span></span>
- <span data-ttu-id="c6e75-767">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-767">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="c6e75-768">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="c6e75-768">tx_event_flags_set</span></span>
- <span data-ttu-id="c6e75-769">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-769">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="c6e75-770">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="c6e75-770">tx_event_flags_set</span></span>

<span data-ttu-id="c6e75-771">이벤트 플래그 그룹에서 이벤트 플래그를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-771">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-772">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-772">Prototype</span></span>

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a><span data-ttu-id="c6e75-773">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-773">Description</span></span>

<span data-ttu-id="c6e75-774">이 서비스는 지정된 set-option에 따라 이벤트 플래그 그룹에서 이벤트 플래그를 설정하거나 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-774">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="c6e75-775">이제 해당 이벤트 플래그 요청이 충족된 모든 일시 중단된 스레드가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-775">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-776">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-776">Parameters</span></span>

- <span data-ttu-id="c6e75-777">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-777">**group_ptr**</span></span> <br><span data-ttu-id="c6e75-778">이전에 만든 이벤트 플래그 그룹 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-778">Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="c6e75-779">**flags_to_set**</span><span class="sxs-lookup"><span data-stu-id="c6e75-779">**flags_to_set**</span></span> <br><span data-ttu-id="c6e75-780">선택한 설정 옵션에 따라 설정하거나 지울 이벤트 플래그를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-780">Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="c6e75-781">**set_option**</span><span class="sxs-lookup"><span data-stu-id="c6e75-781">**set_option**</span></span> <br><span data-ttu-id="c6e75-782">지정된 이벤트 플래그를 그룹의 현재 이벤트 플래그에 AND로 연결할지 또는 OR로 연결할지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-782">Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="c6e75-783">유효한 선택 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-783">The following are valid selections:</span></span>
  - <span data-ttu-id="c6e75-784">**TX_AND**(0x02)</span><span class="sxs-lookup"><span data-stu-id="c6e75-784">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="c6e75-785">**TX_OR**(0x00)</span><span class="sxs-lookup"><span data-stu-id="c6e75-785">**TX_OR** (0x00)</span></span>

  <span data-ttu-id="c6e75-786">TX_AND를 선택하면 지정된 이벤트 플래그가 그룹의 현재 이벤트 플래그에 **AND** 로 연결되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-786">Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="c6e75-787">이 옵션은 그룹의 이벤트 플래그를 지우는 데 사용되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-787">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="c6e75-788">그러지 않고 TX_OR이 지정되면 지정된 이벤트 플래그가 그룹의 현재 이벤트에 **OR** 로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-788">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-789">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-789">Return Values</span></span>
- <span data-ttu-id="c6e75-790">**TX_SUCCESS**(0x00) 이벤트 플래그 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-790">**TX_SUCCESS** (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="c6e75-791">**TX_GROUP_ERROR**(0x06) 잘못된 이벤트 플래그 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-791">**TX_GROUP_ERROR** (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="c6e75-792">**TX_OPTION_ERROR**(0x08) 잘못된 set-option이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-792">**TX_OPTION_ERROR** (0x08) Invalid set-option specified.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-793">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-793">Preemption Possible</span></span>

<span data-ttu-id="c6e75-794">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-794">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-795">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-795">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Set event flags 0, 4, and 8. */
status = tx_event_flags_set(&my_event_flags_group,
    0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
set and any suspended thread whose request was satisfied
has been resumed. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-796">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-796">See Also</span></span>

- <span data-ttu-id="c6e75-797">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-797">tx_event_flags_create</span></span>
- <span data-ttu-id="c6e75-798">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-798">tx_event_flags_delete</span></span>
- <span data-ttu-id="c6e75-799">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-799">tx_event_flags_get</span></span>
- <span data-ttu-id="c6e75-800">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-800">tx_event_flags_info_get</span></span>
- <span data-ttu-id="c6e75-801">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-801">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="c6e75-802">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-802">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-803">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-803">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="c6e75-804">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-804">tx_event_flags_set_notify</span></span>

<span data-ttu-id="c6e75-805">이벤트 플래그가 설정되면 애플리케이션에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-805">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-806">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-806">Prototype</span></span>

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a><span data-ttu-id="c6e75-807">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-807">Description</span></span>

<span data-ttu-id="c6e75-808">이 서비스는 지정된 이벤트 플래그 그룹에 하나 이상의 이벤트 플래그가 설정될 때마다 호출되는 알림 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-808">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="c6e75-809">알림 콜백 처리는 애플리케이션에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-809">The processing of the notification callback is defined by the</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-810">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-810">Parameters</span></span>
- <span data-ttu-id="c6e75-811">**group_ptr** 이전에 만든 이벤트 플래그 그룹에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-811">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="c6e75-812">**events_set_notify** 애플리케이션의 이벤트 플래그 설정 알림 기능에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-812">**events_set_notify** Pointer to application's event flags set notification function.</span></span> <span data-ttu-id="c6e75-813">이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-813">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-814">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-814">Return Values</span></span>

- <span data-ttu-id="c6e75-815">**TX_SUCCESS**(0x00) 이벤트 플래그 설정 알림 등록에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-815">**TX_SUCCESS** (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="c6e75-816">**TX_GROUP_ERROR**(0x06) 잘못된 이벤트 플래그 그룹 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-816">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="c6e75-817">**TX_FEATURE_NOT_ENABLED**(0xFF) 시스템이 알림 기능을 사용하지 않도록 설정하여 컴파일되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-817">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-818">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-818">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_group;

/* Register the "my_event_flags_set_notify" function for monitoring
event flags set in the event flags group "my_group." */
status = tx_event_flags_set_notify(&my_group, my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
was successfully registered. */
void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)

/* One or more event flags was set in this group! */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-819">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-819">See Also</span></span>

- <span data-ttu-id="c6e75-820">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-820">tx_event_flags_create</span></span>
- <span data-ttu-id="c6e75-821">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-821">tx_event_flags_delete</span></span>
- <span data-ttu-id="c6e75-822">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-822">tx_event_flags_get</span></span>
- <span data-ttu-id="c6e75-823">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-823">tx_event_flags_info_get</span></span>
- <span data-ttu-id="c6e75-824">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-824">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="c6e75-825">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-825">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-826">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="c6e75-826">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="c6e75-827">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="c6e75-827">tx_interrupt_control</span></span>

<span data-ttu-id="c6e75-828">인터럽트를 사용하거나 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-828">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-829">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-829">Prototype</span></span>

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a><span data-ttu-id="c6e75-830">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-830">Description</span></span>

<span data-ttu-id="c6e75-831">이 서비스는 입력 매개 변수 *new_posture* 를 통해 지정된 대로 인터럽트를 사용하거나 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-831">This service enables or disables interrupts as specified by the input parameter *new_posture*.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-832">애플리케이션 스레드에서 이 서비스를 호출하는 경우 인터럽트 상태는 해당 스레드 컨텍스트에 포함된 상태로 유지됩니다. 예를 들어 스레드가 이 루틴을 호출하여 인터럽트를 사용하지 않도록 설정한 후 일시 중단되면 다시 시작되는 경우 인터럽트는 다시 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-832">*If this service is called from an application thread, the interrupt posture remains part of that thread's context. For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.*</span></span>

> [!WARNING]
> <span data-ttu-id="c6e75-833">초기화 중에는 이 서비스를 사용하여 인터럽트를 사용하도록 설정하지 않는 것이 좋습니다. 사용하면 예기치 않은 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-833">*This service should not be used to enable interrupts during initialization! Doing so could cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-834">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-834">Parameters</span></span>

- <span data-ttu-id="c6e75-835">**new_posture** 이 매개 변수는 인터럽트가 사용하지 않도록 설정되는지 사용하도록 설정되는지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-835">**new_posture** This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="c6e75-836">올바른 값에는 **TX_INT_DISABLE** 및 **TX_INT_ENABLE** 이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-836">Legal values include **TX_INT_DISABLE** and **TX_INT_ENABLE**.</span></span> <span data-ttu-id="c6e75-837">이러한 매개 변수의 실제 값은 포트에 특정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-837">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="c6e75-838">또한 일부 처리 아키텍처는 추가 인터럽트 사용 안 함 상태를 지원할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-838">In addition, some processing architectures might support additional interrupt disable postures.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-839">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-839">Return Values</span></span>
- <span data-ttu-id="c6e75-840">**previous posture** 이 서비스는 이전 인터럽트 상태를 호출자에게 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-840">**previous posture** This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="c6e75-841">이렇게 하면 서비스 사용자가 인터럽트를 사용하지 않도록 설정한 후 이전 상태를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-841">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-842">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-842">Allowed From</span></span>

<span data-ttu-id="c6e75-843">스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-843">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-844">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-844">Preemption Possible</span></span>

<span data-ttu-id="c6e75-845">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-845">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-846">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-846">Example</span></span>

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a><span data-ttu-id="c6e75-847">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-847">See Also</span></span>

<span data-ttu-id="c6e75-848">None</span><span class="sxs-lookup"><span data-stu-id="c6e75-848">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="c6e75-849">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-849">tx_mutex_create</span></span>

<span data-ttu-id="c6e75-850">상호 배제 뮤텍스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-850">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-851">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-851">Prototype</span></span>

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a><span data-ttu-id="c6e75-852">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-852">Description</span></span>

<span data-ttu-id="c6e75-853">이 서비스는 리소스 보호를 위해 스레드 간 상호 배제 뮤텍스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-853">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-854">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-854">Parameters</span></span>

- <span data-ttu-id="c6e75-855">**mutex_ptr** 뮤텍스 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-855">**mutex_ptr** Pointer to a mutex control block.</span></span>
- <span data-ttu-id="c6e75-856">**name_ptr** 뮤텍스 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-856">**name_ptr** Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="c6e75-857">**priority_inherit** 이 뮤텍스가 우선 순위 상속을 지원하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-857">**priority_inherit** Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="c6e75-858">이 값이 TX_INHERIT인 경우 우선 순위 상속이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-858">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="c6e75-859">하지만 TX_NO_INHERIT이 지정되면 이 뮤텍스에서 우선 순위 상속이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-859">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-860">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-860">Return Values</span></span>

- <span data-ttu-id="c6e75-861">**TX_SUCCESS**(0x00) 뮤텍스 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-861">**TX_SUCCESS** (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="c6e75-862">**TX_MUTEX_ERROR**(0x1C) 잘못된 뮤텍스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-862">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="c6e75-863">포인터가 NULL이거나 뮤텍스가 이미 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-863">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="c6e75-864">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-864">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="c6e75-865">**TX_INHERIT_ERROR**(0x1F) 우선 순위 상속 매개 변수가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-865">**TX_INHERIT_ERROR** (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-866">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-866">Allowed From</span></span>

<span data-ttu-id="c6e75-867">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-867">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-868">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-868">Preemption Possible</span></span>

<span data-ttu-id="c6e75-869">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-869">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-870">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-870">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Create a mutex to provide protection over a
common resource. */
status = tx_mutex_create(&my_mutex,"my_mutex_name",
    TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
use. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-871">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-871">See Also</span></span>

- <span data-ttu-id="c6e75-872">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-872">tx_mutex_delete</span></span>
- <span data-ttu-id="c6e75-873">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-873">tx_mutex_get</span></span>
- <span data-ttu-id="c6e75-874">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-874">tx_mutex_info_get</span></span>
- <span data-ttu-id="c6e75-875">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-875">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="c6e75-876">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-876">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-877">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-877">tx_mutex_prioritize</span></span>
- <span data-ttu-id="c6e75-878">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-878">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="c6e75-879">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-879">tx_mutex_delete</span></span>

<span data-ttu-id="c6e75-880">상호 배제 뮤텍스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-880">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-881">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-881">Prototype</span></span>

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-882">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-882">Description</span></span>

<span data-ttu-id="c6e75-883">이 서비스는 지정된 뮤텍스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-883">This service deletes the specified mutex.</span></span> <span data-ttu-id="c6e75-884">뮤텍스를 기다리는 일시 중단된 모든 스레드는 다시 시작되며 **TX_DELETED** 반환 상태가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-884">All threads suspended waiting for the mutex are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-885">애플리케이션은 삭제된 뮤텍스를 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-885">*It is the application's responsibility to prevent use of a deleted mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-886">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-886">Parameters</span></span>

- <span data-ttu-id="c6e75-887">**mutex_ptr** 이전에 만든 뮤텍스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-887">**mutex_ptr** Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-888">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-888">Return Values</span></span>

- <span data-ttu-id="c6e75-889">**TX_SUCCESS**(0x00) 뮤텍스 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-889">**TX_SUCCESS** (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="c6e75-890">**TX_MUTEX_ERROR**(0x1C) 잘못된 뮤텍스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-890">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="c6e75-891">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-891">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-892">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-892">Allowed From</span></span>

<span data-ttu-id="c6e75-893">스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-893">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-894">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-894">Preemption Possible</span></span>

<span data-ttu-id="c6e75-895">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-895">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-896">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-896">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-897">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-897">See Also</span></span>

- <span data-ttu-id="c6e75-898">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-898">tx_mutex_create</span></span>
- <span data-ttu-id="c6e75-899">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-899">tx_mutex_get</span></span>
- <span data-ttu-id="c6e75-900">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-900">tx_mutex_info_get</span></span>
- <span data-ttu-id="c6e75-901">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-901">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="c6e75-902">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-902">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-903">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-903">tx_mutex_prioritize</span></span>
- <span data-ttu-id="c6e75-904">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-904">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="c6e75-905">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-905">tx_mutex_get</span></span>

<span data-ttu-id="c6e75-906">뮤텍스 소유권을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-906">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-907">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-907">Prototype</span></span>

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c6e75-908">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-908">Description</span></span>

<span data-ttu-id="c6e75-909">이 서비스는 지정된 뮤텍스의 배타적 소유권을 얻으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-909">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="c6e75-910">호출 스레드가 뮤텍스를 이미 소유하고 있으면 내부 카운터가 증분되고 성공 상태가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-910">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="c6e75-911">다른 스레드에서 뮤텍스를 소유하지만 이 스레드의 우선 순위가 더 높으며 뮤텍스를 만들 때 우선 순위 상속이 지정된 경우, 우선 순위가 더 낮은 스레드의 우선 순위가 호출 스레드의 우선 순위로 일시적으로 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-911">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread's priority will be temporarily raised to that of the calling thread.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-912">priorityinheritance가 지정된 뮤텍스를 소유하는 우선 순위가 더 낮은 스레드의 우선 순위는 뮤텍스 소유 중 외부 스레드에 의해 수정되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-912">*The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-913">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-913">Parameters</span></span>

- <span data-ttu-id="c6e75-914">**mutex_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-914">**mutex_ptr**</span></span>   <br><span data-ttu-id="c6e75-915">이전에 만든 뮤텍스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-915">Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="c6e75-916">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="c6e75-916">**wait_option**</span></span> <br><span data-ttu-id="c6e75-917">다른 스레드가 뮤텍스를 이미 소유하고 있는 경우 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-917">Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="c6e75-918">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c6e75-919">**TX_NO_WAIT**(0x00000000) - TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-919">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="c6e75-920">초기화에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-920">*This is the only valid option if the service is called from Initialization.*</span></span>
  - <span data-ttu-id="c6e75-921">**TX_WAIT_FOREVER** 시간 제한 값(0xFFFFFFFF) - **TX_WAIT_FOREVER** 를 선택하면 뮤텍스를 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-921">**TX_WAIT_FOREVER** timeout value (0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until the mutex is available.</span></span>
  - <span data-ttu-id="c6e75-922">시간 제한 값(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 뮤텍스를 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-922">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-923">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-923">Return Values</span></span>

- <span data-ttu-id="c6e75-924">**TX_SUCCESS**(0x00) 뮤텍스 가져오기 작업에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-924">**TX_SUCCESS** (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="c6e75-925">**TX_DELETED**(0x01) 스레드가 일시 중단된 동안 뮤텍스가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-925">**TX_DELETED** (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="c6e75-926">**TX_NOT_AVAILABLE**(0x1D) 서비스가 지정된 대기 시간 내에 뮤텍스 소유권을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-926">**TX_NOT_AVAILABLE** (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="c6e75-927">**TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-927">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="c6e75-928">**TX_MUTEX_ERROR**(0x1C) 잘못된 뮤텍스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-928">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="c6e75-929">**TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-929">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>
- <span data-ttu-id="c6e75-930">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-930">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-931">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-931">Allowed From</span></span>

<span data-ttu-id="c6e75-932">초기화, 스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="c6e75-932">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-933">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-933">Preemption Possible</span></span>

<span data-ttu-id="c6e75-934">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-934">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-935">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-935">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="c6e75-936">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-936">See Also</span></span>

- <span data-ttu-id="c6e75-937">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-937">tx_mutex_create</span></span>
- <span data-ttu-id="c6e75-938">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-938">tx_mutex_delete</span></span>
- <span data-ttu-id="c6e75-939">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-939">tx_mutex_info_get</span></span>
- <span data-ttu-id="c6e75-940">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-940">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="c6e75-941">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-941">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-942">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-942">tx_mutex_prioritize</span></span>
- <span data-ttu-id="c6e75-943">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-943">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="c6e75-944">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-944">tx_mutex_info_get</span></span>

<span data-ttu-id="c6e75-945">뮤텍스에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-945">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-946">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-946">Prototype</span></span>

```c
UINT tx_mutex_info_get(
    TX_MUTEX *mutex_ptr, 
    CHAR **name,
    ULONG *count, 
    TX_THREAD **owner,
    TX_THREAD **first_suspended,
    ULONG *suspended_count, 
    TX_MUTEX **next_mutex);
```

### <a name="description"></a><span data-ttu-id="c6e75-947">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-947">Description</span></span>

<span data-ttu-id="c6e75-948">이 서비스는 지정된 뮤텍스의 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-948">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-949">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-949">Parameters</span></span>

- <span data-ttu-id="c6e75-950">**mutex_ptr** 뮤텍스 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-950">**mutex_ptr** Pointer to mutex control block.</span></span>
- <span data-ttu-id="c6e75-951">**name** 뮤텍스 이름에 대한 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-951">**name** Pointer to destination for the pointer to the mutex's name.</span></span>
- <span data-ttu-id="c6e75-952">**count** 뮤텍스 소유권 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-952">**count** Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="c6e75-953">**owner** 소유 스레드 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-953">**owner** Pointer to destination for the owning thread's pointer.</span></span>
- <span data-ttu-id="c6e75-954">**first_suspended** 이 뮤텍스의 일시 중단 목록에 있는 첫 번째 스레드에 대한 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-954">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="c6e75-955">**suspended_count** 이 뮤텍스에서 현재 일시 중단된 스레드 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-955">**suspended_count** Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="c6e75-956">**next_mutex** 다음에 만들 뮤텍스 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-956">**next_mutex** Pointer to destination for the pointer of the next created mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-957">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-957">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-958">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-958">Return Values</span></span>

- <span data-ttu-id="c6e75-959">**TX_SUCCESS**(0x00) 뮤텍스 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-959">**TX_SUCCESS** (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="c6e75-960">**TX_MUTEX_ERROR**(0x1C) 잘못된 뮤텍스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-960">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-961">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-961">Allowed From</span></span>

<span data-ttu-id="c6e75-962">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-962">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-963">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-963">Preemption Possible</span></span>

<span data-ttu-id="c6e75-964">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-964">No</span></span>

<span data-ttu-id="c6e75-965">**예제**</span><span class="sxs-lookup"><span data-stu-id="c6e75-965">**Example**</span></span>

```c
TX_MUTEX my_mutex;
CHAR *name;
ULONG count;
TX_THREAD *owner;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_MUTEX *next_mutex;
UINT status;

/* Retrieve information about the previously created
mutex "my_mutex." */
status = tx_mutex_info_get(&my_mutex, &name,
    &count, &owner,
    &first_suspended, &suspended_count,
    &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-966">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-966">See Also</span></span>

- <span data-ttu-id="c6e75-967">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-967">tx_mutex_create</span></span>
- <span data-ttu-id="c6e75-968">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-968">tx_mutex_delete</span></span>
- <span data-ttu-id="c6e75-969">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-969">tx_mutex_get</span></span>
- <span data-ttu-id="c6e75-970">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-970">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="c6e75-971">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-971">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-972">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-972">tx_mutex_prioritize</span></span>
- <span data-ttu-id="c6e75-973">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-973">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="c6e75-974">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-974">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="c6e75-975">뮤텍스 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-975">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-976">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-976">Prototype</span></span>

```c
UINT tx_mutex_performance_info_get(
    TX_MUTEX *mutex_ptr, 
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a><span data-ttu-id="c6e75-977">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-977">Description</span></span>

<span data-ttu-id="c6e75-978">이 서비스는 지정된 뮤텍스에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-978">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-979">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 \***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-979">*The ThreadX library and application must be built with* ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-980">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-980">Parameters</span></span>

- <span data-ttu-id="c6e75-981">**mutex_ptr** 이전에 만든 뮤텍스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-981">**mutex_ptr** Pointer to previously created mutex.</span></span>
- <span data-ttu-id="c6e75-982">**puts** 이 뮤텍스에서 수행된 넣기 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-982">**puts** Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="c6e75-983">**gets** 이 뮤텍스에서 수행된 가져오기 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-983">**gets** Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="c6e75-984">**suspensions** 이 뮤텍스의 스레드 뮤텍스 가져오기 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-984">**suspensions** Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="c6e75-985">**timeouts** 이 뮤텍스의 뮤텍스 가져오기 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-985">**timeouts** Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="c6e75-986">**inversions** 이 뮤텍스의 스레드 우선 순위 반전 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-986">**inversions** Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="c6e75-987">**inheritances** 이 뮤텍스의 스레드 우선 순위 상속 작업 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-987">**inheritances** Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-988">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-988">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-989">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-989">Return Values</span></span>

- <span data-ttu-id="c6e75-990">**TX_SUCCESS**(0x00) 뮤텍스 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-990">**TX_SUCCESS** (0x00) Successful mutex performance get.</span></span>
- <span data-ttu-id="c6e75-991">**TX_PTR_ERROR**(0x03) 잘못된 뮤텍스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-991">**TX_PTR_ERROR** (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="c6e75-992">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-992">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-993">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-993">Allowed From</span></span>

<span data-ttu-id="c6e75-994">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-994">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-995">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-995">Example</span></span>

```c
TX_MUTEX my_mutex;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on the previously created
mutex. */
status = tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
    &suspensions, &timeouts, &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-996">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-996">See Also</span></span>

- <span data-ttu-id="c6e75-997">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-997">tx_mutex_create</span></span>
- <span data-ttu-id="c6e75-998">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-998">tx_mutex_delete</span></span>
- <span data-ttu-id="c6e75-999">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-999">tx_mutex_get</span></span>
- <span data-ttu-id="c6e75-1000">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1000">tx_mutex_info_get</span></span>
- <span data-ttu-id="c6e75-1001">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1001">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1002">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1002">tx_mutex_prioritize</span></span>
- <span data-ttu-id="c6e75-1003">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1003">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="c6e75-1004">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1004">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="c6e75-1005">뮤텍스 시스템 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1005">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1006">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1006">Prototype</span></span>

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a><span data-ttu-id="c6e75-1007">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1007">Description</span></span>

<span data-ttu-id="c6e75-1008">이 서비스는 시스템의 모든 뮤텍스에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1008">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-1009">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_MUTEX_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. </span><span class="sxs-lookup"><span data-stu-id="c6e75-1009">*The ThreadX library and application must be built with* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1010">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1010">Parameters</span></span>

- <span data-ttu-id="c6e75-1011">**puts** 모든 뮤텍스에서 수행된 총 넣기 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1011">**puts** Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="c6e75-1012">**gets** 모든 뮤텍스에서 수행된 총 가져오기 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1012">**gets** Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="c6e75-1013">**suspensions** 모든 뮤텍스의 총 스레드 뮤텍스 가져오기 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1013">**suspensions** Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="c6e75-1014">**timeouts** 모든 뮤텍스의 총 뮤텍스 가져오기 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1014">**timeouts** Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="c6e75-1015">**inversions** 모든 뮤텍스의 총 스레드 우선 순위 반전 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1015">**inversions** Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="c6e75-1016">**inheritances** 모든 뮤텍스의 총 스레드 우선 순위 상속 작업 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1016">**inheritances** Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1017">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1017">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1018">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1018">Return Values</span></span>

- <span data-ttu-id="c6e75-1019">**TX_SUCCESS**(0x00) 뮤텍스 시스템 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1019">**TX_SUCCESS** (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="c6e75-1020">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1020">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1021">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1021">Allowed From</span></span>

<span data-ttu-id="c6e75-1022">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1022">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1023">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1023">Example</span></span>

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on all previously created
mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts,
    &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1024">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1024">See Also</span></span>

- <span data-ttu-id="c6e75-1025">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1025">tx_mutex_create</span></span>
- <span data-ttu-id="c6e75-1026">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1026">tx_mutex_delete</span></span>
- <span data-ttu-id="c6e75-1027">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1027">tx_mutex_get</span></span>
- <span data-ttu-id="c6e75-1028">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1028">tx_mutex_info_get</span></span>
- <span data-ttu-id="c6e75-1029">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1029">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1030">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1030">tx_mutex_prioritize</span></span>
- <span data-ttu-id="c6e75-1031">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1031">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="c6e75-1032">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1032">tx_mutex_prioritize</span></span>

<span data-ttu-id="c6e75-1033">뮤텍스 일시 중단 목록의 우선 순위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1033">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1034">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1034">Prototype</span></span>

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-1035">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1035">Description</span></span>

<span data-ttu-id="c6e75-1036">이 서비스는 일시 중단 목록 맨 앞에 있는, 뮤텍스 소유권 때문에 일시 중단된 스레드를 가장 높은 우선 순위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1036">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="c6e75-1037">다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1037">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1038">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1038">Parameters</span></span>

- <span data-ttu-id="c6e75-1039">**mutex_ptr** 이전에 만든 뮤텍스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1039">**mutex_ptr** Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1040">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1040">Return Values</span></span>

- <span data-ttu-id="c6e75-1041">**TX_SUCCESS**(0x00) 뮤텍스 우선 순위 지정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1041">**TX_SUCCESS** (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="c6e75-1042">**TX_MUTEX_ERROR**(0x1C) 잘못된 뮤텍스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1042">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1043">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1043">Allowed From</span></span>

<span data-ttu-id="c6e75-1044">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1044">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1045">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1045">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1046">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1046">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1047">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1047">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Ensure that the highest priority thread will receive
ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_mutex_put call that releases ownership of the
mutex will give ownership to this thread and wake it
up. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1048">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1048">See Also</span></span>

- <span data-ttu-id="c6e75-1049">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1049">tx_mutex_create</span></span>
- <span data-ttu-id="c6e75-1050">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1050">tx_mutex_delete</span></span>
- <span data-ttu-id="c6e75-1051">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1051">tx_mutex_get</span></span>
- <span data-ttu-id="c6e75-1052">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1052">tx_mutex_info_get</span></span>
- <span data-ttu-id="c6e75-1053">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1053">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1054">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1054">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1055">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1055">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="c6e75-1056">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1056">tx_mutex_put</span></span>

<span data-ttu-id="c6e75-1057">뮤텍스 소유권을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1057">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1058">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1058">Prototype</span></span>

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-1059">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1059">Description</span></span>

<span data-ttu-id="c6e75-1060">이 서비스는 지정된 뮤텍스의 소유권 수를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1060">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="c6e75-1061">소유권 수가 0이면 뮤텍스를 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1061">If the ownership count is zero, the mutex is made available.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1062">뮤텍스를 만들 때 우선 순위 상속을 선택한 경우 처음 뮤텍스 소유권을 얻었을 때의 우선 순위로 해제 스레드 우선 순위가 복원됩니다. 뮤텍스 소유 기간 동안 해제 스레드에 수행된 다른 모든 우선 순위 변경은 실행 취소될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1062">*If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex. Any other priority changes made to the releasing thread during ownership of the mutex may be undone.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1063">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1063">Parameters</span></span>
- <span data-ttu-id="c6e75-1064">mutex_ptr 이전에 만든 뮤텍스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1064">mutex_ptr Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1065">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1065">Return Values</span></span>
- <span data-ttu-id="c6e75-1066">**TX_SUCCESS**(0x00) 뮤텍스 해제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1066">**TX_SUCCESS** (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="c6e75-1067">**TX_NOT_OWNED**(0x1E) 호출자가 뮤텍스를 소유하고 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1067">**TX_NOT_OWNED** (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="c6e75-1068">**TX_MUTEX_ERROR**(0x1C) 뮤텍스에 대한 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1068">**TX_MUTEX_ERROR** (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="c6e75-1069">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1069">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1070">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1070">Allowed From</span></span>

<span data-ttu-id="c6e75-1071">초기화, 스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="c6e75-1071">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1072">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1072">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1073">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1073">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1074">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1074">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1075">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1075">See Also</span></span>

- <span data-ttu-id="c6e75-1076">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1076">tx_mutex_create</span></span>
- <span data-ttu-id="c6e75-1077">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1077">tx_mutex_delete</span></span>
- <span data-ttu-id="c6e75-1078">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1078">tx_mutex_get</span></span>
- <span data-ttu-id="c6e75-1079">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1079">tx_mutex_info_get</span></span>
- <span data-ttu-id="c6e75-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1080">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1081">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1081">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1082">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1082">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="c6e75-1083">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1083">tx_queue_create</span></span>

<span data-ttu-id="c6e75-1084">메시지 큐를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1084">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1085">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1085">Prototype</span></span>

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a><span data-ttu-id="c6e75-1086">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1086">Description</span></span>

<span data-ttu-id="c6e75-1087">이 서비스는 일반적으로 스레드 간 통신에 사용되는 메시지 큐를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1087">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="c6e75-1088">총 메시지 수는 지정된 메시지 크기와 큐의 총 바이트 수로 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1088">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1089">큐의 메모리 영역에 지정된 총 바이트 수를 지정된 메시지 크기로 균등하게 나눌 수 없는 경우 메모리 영역의 나머지 바이트는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1089">*If the total number of bytes specified in the queue's memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1090">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1090">Parameters</span></span>

- <span data-ttu-id="c6e75-1091">**queue_ptr** 메시지 큐 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1091">**queue_ptr** Pointer to a message queue control block.</span></span>
- <span data-ttu-id="c6e75-1092">**name_ptr** 메시지 큐 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1092">**name_ptr** Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="c6e75-1093">**message_size** 큐에 있는 각 메시지의 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1093">**message_size** Specifies the size of each message in the queue.</span></span> <span data-ttu-id="c6e75-1094">메시지 크기 범위는 1개의 32비트 단어부터 16개의 32비트 단어입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1094">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="c6e75-1095">유효한 메시지 크기 옵션은 1에서 16(포함) 사이의 숫자 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1095">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="c6e75-1096">**queue_start** 메시지 큐의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1096">**queue_start** Starting address of the message queue.</span></span> <span data-ttu-id="c6e75-1097">시작 주소는 ULONG 데이터 형식의 크기에 맞춰야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1097">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="c6e75-1098">**queue_size** 메시지 큐에 사용할 수 있는 총 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1098">**queue_size** Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1099">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1099">Return Values</span></span>

- <span data-ttu-id="c6e75-1100">**TX_SUCCESS**(0x00) 메시지 큐 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1100">**TX_SUCCESS** (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="c6e75-1101">**TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1101">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="c6e75-1102">포인터가 NULL이거나 큐가 이미 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1102">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="c6e75-1103">**TX_PTR_ERROR**(0x03) 메시지 큐의 시작 주소가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1103">**TX_PTR_ERROR** (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="c6e75-1104">**TX_SIZE_ERROR**(0x05) 메시지 큐의 크기가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1104">**TX_SIZE_ERROR** (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="c6e75-1105">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1105">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1106">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1106">Allowed From</span></span>

<span data-ttu-id="c6e75-1107">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-1107">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1108">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1108">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1109">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1109">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1110">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1110">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Create a message queue whose total size is 2000 bytes
starting at address 0x300000. Each message in this
queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
    4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
for storing 125 messages (2000 bytes/ 16 bytes per
message). */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1111">See Also</span></span>

- <span data-ttu-id="c6e75-1112">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1112">tx_queue_delete</span></span>
- <span data-ttu-id="c6e75-1113">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="c6e75-1113">tx_queue_flush</span></span>
- <span data-ttu-id="c6e75-1114">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1114">tx_queue_front_send</span></span>
- <span data-ttu-id="c6e75-1115">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1115">tx_queue_info_get</span></span>
- <span data-ttu-id="c6e75-1116">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1116">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1117">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1117">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1118">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1118">tx_queue_prioritize</span></span>
- <span data-ttu-id="c6e75-1119">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="c6e75-1119">tx_queue_receive</span></span>
- <span data-ttu-id="c6e75-1120">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1120">tx_queue_send</span></span>
- <span data-ttu-id="c6e75-1121">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1121">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="c6e75-1122">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1122">tx_queue_delete</span></span>

<span data-ttu-id="c6e75-1123">메시지 큐를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1123">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1124">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1124">Prototype</span></span>

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-1125">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1125">Description</span></span>

<span data-ttu-id="c6e75-1126">이 서비스는 지정된 메시지 큐를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1126">This service deletes the specified message queue.</span></span> <span data-ttu-id="c6e75-1127">이 큐의 메시지 기다리는 일시 중단된 모든 스레드는 다시 시작되며 TX_DELETED 반환 상태가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1127">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="c6e75-1128">애플리케이션은 이 큐를 삭제하기 전에 이 큐에 대한 모든 설정 알림 콜백이 완료되었는지(또는 사용하지 않도록 설정되었는지) 확인해야 합니다. 또한 애플리케이션은 이후에는 삭제된 큐를 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1128">*The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue. In addition, the application must prevent any future use of a deleted queue.*</span></span> <br><br><span data-ttu-id="c6e75-1129">애플리케이션은 또한 이 서비스가 완료된 후 사용할 수 있는 큐와 연결된 메모리 영역을 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1129">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1130">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1130">Parameters</span></span>

- <span data-ttu-id="c6e75-1131">**queue_ptr** 이전에 만든 메시지 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1131">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1132">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1132">Return Values</span></span>

- <span data-ttu-id="c6e75-1133">**TX_SUCCESS**(0x00) 메시지 큐 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1133">**TX_SUCCESS** (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="c6e75-1134">**TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1134">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="c6e75-1135">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1135">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1136">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1136">Allowed From</span></span>

<span data-ttu-id="c6e75-1137">스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-1137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1138">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1138">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1139">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1140">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1140">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Delete entire message queue. Assume that the queue
has already been created with a call to
tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1141">See Also</span></span>

- <span data-ttu-id="c6e75-1142">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1142">tx_queue_create</span></span>
- <span data-ttu-id="c6e75-1143">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="c6e75-1143">tx_queue_flush</span></span>
- <span data-ttu-id="c6e75-1144">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1144">tx_queue_front_send</span></span>
- <span data-ttu-id="c6e75-1145">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1145">tx_queue_info_get</span></span>
- <span data-ttu-id="c6e75-1146">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1146">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1147">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1147">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1148">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1148">tx_queue_prioritize</span></span>
- <span data-ttu-id="c6e75-1149">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="c6e75-1149">tx_queue_receive</span></span>
- <span data-ttu-id="c6e75-1150">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1150">tx_queue_send</span></span>
- <span data-ttu-id="c6e75-1151">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1151">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="c6e75-1152">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="c6e75-1152">tx_queue_flush</span></span>

<span data-ttu-id="c6e75-1153">메시지 큐의 메시지를 비웁니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1153">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1154">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1154">Prototype</span></span>

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-1155">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1155">Description</span></span>

<span data-ttu-id="c6e75-1156">이 서비스는 지정된 메시지 큐에 저장된 모든 메시지를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1156">This service deletes all messages stored in the specified message queue.</span></span>

<span data-ttu-id="c6e75-1157">메시지 큐가 가득 차면 모든 일시 중단된 스레드의 메시지가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1157">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="c6e75-1158">일시 중단된 각 스레드는 메시지 송신이 성공했음을 나타내는 반환 상태로 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1158">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="c6e75-1159">큐가 비어 있으면 이 서비스는 아무 작업도 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1159">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1160">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1160">Parameters</span></span>

- <span data-ttu-id="c6e75-1161">**queue_ptr** 이전에 만든 메시지 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1161">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1162">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1162">Return Values</span></span>

- <span data-ttu-id="c6e75-1163">**TX_SUCCESS**(0x00) 메시지 큐 플러시에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1163">**TX_SUCCESS** (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="c6e75-1164">**TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1164">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1165">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1165">Allowed From</span></span>

<span data-ttu-id="c6e75-1166">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1166">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1167">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1167">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1168">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1168">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1169">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1169">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Flush out all pending messages in the specified message
queue. Assume that the queue has already been created
with a call to tx_queue_create. */
status = tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
empty. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1170">See Also</span></span>

- <span data-ttu-id="c6e75-1171">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1171">tx_queue_create</span></span>
- <span data-ttu-id="c6e75-1172">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1172">tx_queue_delete</span></span>
- <span data-ttu-id="c6e75-1173">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1173">tx_queue_front_send</span></span>
- <span data-ttu-id="c6e75-1174">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1174">tx_queue_info_get</span></span>
- <span data-ttu-id="c6e75-1175">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1175">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1176">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1176">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1177">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1177">tx_queue_prioritize</span></span>
- <span data-ttu-id="c6e75-1178">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="c6e75-1178">tx_queue_receive</span></span>
- <span data-ttu-id="c6e75-1179">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1179">tx_queue_send</span></span>
- <span data-ttu-id="c6e75-1180">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1180">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="c6e75-1181">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1181">tx_queue_front_send</span></span>

<span data-ttu-id="c6e75-1182">메시지를 큐 맨 앞으로 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1182">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1183">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1183">Prototype</span></span>

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c6e75-1184">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1184">Description</span></span>

<span data-ttu-id="c6e75-1185">이 서비스는 메시지를 지정된 메시지 큐의 맨 앞 위치로 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1185">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="c6e75-1186">메시지는 원본 포인터로 지정된 메모리 영역의 큐 맨 앞으로 **복사됩니다**.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1186">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1187">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1187">Parameters</span></span>

- <span data-ttu-id="c6e75-1188">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1188">**queue_ptr**</span></span> <br><span data-ttu-id="c6e75-1189">메시지 큐 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1189">Pointer to a message queue control block.</span></span>
- <span data-ttu-id="c6e75-1190">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1190">**source_ptr**</span></span> <br><span data-ttu-id="c6e75-1191">메시지에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1191">Pointer to the message.</span></span>
- <span data-ttu-id="c6e75-1192">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1192">**wait_option**</span></span>  <br><span data-ttu-id="c6e75-1193">메시지 큐가 가득 찬 경우의 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1193">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="c6e75-1194">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1194">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c6e75-1195">**TX_NO_WAIT**(0x00000000) - TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1195">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="c6e75-1196">초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1196">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="c6e75-1197">**TX_WAIT_FOREVER**(0xFFFFFFFF) - TX_WAIT_FOREVER를 선택하면 큐에 공간이 있을 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1197">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="c6e75-1198">시간 제한 값(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 큐의 공간을 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1198">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1199">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1199">Return Values</span></span>

- <span data-ttu-id="c6e75-1200">**TX_SUCCESS**(0x00) 메시지 송신에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1200">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="c6e75-1201">**TX_DELETED**(0x01) 스레드가 일시 중단된 동안 메시지 큐가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1201">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="c6e75-1202">**TX_QUEUE_FULL**(0x0B) 지정된 대기 시간 중 큐가 가득 찼으므로 서비스에서 메시지를 송신할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1202">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="c6e75-1203">**TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1203">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="c6e75-1204">**TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1204">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="c6e75-1205">**TX_PTR_ERROR**(0x03) 잘못된 메시지 원본 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1205">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="c6e75-1206">**TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1206">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1207">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1207">Allowed From</span></span>

<span data-ttu-id="c6e75-1208">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1208">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1209">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1209">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1210">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1210">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1211">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1211">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to the front of "my_queue." Return
immediately, regardless of success. This wait
option is used for calls from initialization, timers,
and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
    TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
of the specified queue. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1212">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1212">See Also</span></span>

- <span data-ttu-id="c6e75-1213">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1213">tx_queue_create</span></span>
- <span data-ttu-id="c6e75-1214">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1214">tx_queue_delete</span></span>
- <span data-ttu-id="c6e75-1215">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="c6e75-1215">tx_queue_flush</span></span>
- <span data-ttu-id="c6e75-1216">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1216">tx_queue_info_get</span></span>
- <span data-ttu-id="c6e75-1217">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1217">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1218">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1218">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1219">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1219">tx_queue_prioritize</span></span>
- <span data-ttu-id="c6e75-1220">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="c6e75-1220">tx_queue_receive</span></span>
- <span data-ttu-id="c6e75-1221">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1221">tx_queue_send</span></span>
- <span data-ttu-id="c6e75-1222">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1222">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="c6e75-1223">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1223">tx_queue_info_get</span></span>

<span data-ttu-id="c6e75-1224">큐에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1224">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1225">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1225">Prototype</span></span>

```c
UINT tx_queue_info_get(
    TX_QUEUE *queue_ptr, 
    CHAR **name,
    ULONG *enqueued, 
    ULONG *available_storage
    TX_THREAD **first_suspended, 
    ULONG *suspended_count,
    TX_QUEUE **next_queue);
```

### <a name="description"></a><span data-ttu-id="c6e75-1226">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1226">Description</span></span>

<span data-ttu-id="c6e75-1227">이 서비스는 지정된 메시지 큐에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1227">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1228">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1228">Parameters</span></span>

- <span data-ttu-id="c6e75-1229">**queue_ptr** 이전에 만든 메시지 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1229">**queue_ptr** Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="c6e75-1230">**name** 큐 이름에 대한 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1230">**name** Pointer to destination for the pointer to the queue's name.</span></span>
- <span data-ttu-id="c6e75-1231">**enqueued** 현재 큐에 있는 메시지 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1231">**enqueued** Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="c6e75-1232">**available_storage** 큐에 현재 공간이 있는 메시지 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1232">**available_storage** Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="c6e75-1233">**first_suspended** 이 큐의 일시 중단 목록에 있는 첫 번째 스레드에 대한 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1233">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="c6e75-1234">**suspended_count** 이 큐에서 현재 일시 중단된 스레드 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1234">**suspended_count** Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="c6e75-1235">**next_queue** 다음에 만들 큐 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1235">**next_queue** Pointer to destination for the pointer of the next created queue.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1236">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1236">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1237">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1237">Return Values</span></span>

- <span data-ttu-id="c6e75-1238">**TX_SUCCESS**(0x00) 큐 정보 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1238">**TX_SUCCESS** (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="c6e75-1239">**TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1239">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1240">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1240">Allowed From</span></span>

<span data-ttu-id="c6e75-1241">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1241">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1242">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1242">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1243">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1243">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1244">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1244">Example</span></span>

```c
TX_QUEUE my_queue;
CHAR *name;
ULONG enqueued;
ULONG available_storage;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_QUEUE *next_queue;
UINT status;

/* Retrieve information about the previously created
message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
    &enqueued, &available_storage,
    &first_suspended, &suspended_count,
    &next_queue);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1245">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1245">See Also</span></span>

- <span data-ttu-id="c6e75-1246">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1246">tx_queue_create</span></span>
- <span data-ttu-id="c6e75-1247">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1247">tx_queue_delete</span></span>
- <span data-ttu-id="c6e75-1248">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="c6e75-1248">tx_queue_flush</span></span>
- <span data-ttu-id="c6e75-1249">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1249">tx_queue_front_send</span></span>
- <span data-ttu-id="c6e75-1250">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1250">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1251">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1251">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1252">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1252">tx_queue_prioritize</span></span>
- <span data-ttu-id="c6e75-1253">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="c6e75-1253">tx_queue_receive</span></span>
- <span data-ttu-id="c6e75-1254">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1254">tx_queue_send</span></span>
- <span data-ttu-id="c6e75-1255">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1255">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="c6e75-1256">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1256">tx_queue_performance_info_get</span></span>

<span data-ttu-id="c6e75-1257">큐 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1257">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1258">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1258">Prototype</span></span>

```c
UINT tx_queue_performance_info_get(
    TX_QUEUE *queue_ptr,
    ULONG *messages_sent, 
    ULONG *messages_received,
    ULONG *empty_suspensions, 
    ULONG *full_suspensions,
    ULONG *full_errors, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="c6e75-1259">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1259">Description</span></span>

<span data-ttu-id="c6e75-1260">이 서비스는 지정된 큐에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1260">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-1261">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 \***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1261">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1262">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1262">Parameters</span></span>

- <span data-ttu-id="c6e75-1263">**queue_ptr** 이전에 만든 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1263">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="c6e75-1264">**messages_sent** 이 큐에서 수행된 송신 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1264">**messages_sent** Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="c6e75-1265">**messages_received** 이 큐에서 수행된 수신 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1265">**messages_received** Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="c6e75-1266">**empty_suspensions** 이 큐의 큐 비우기 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1266">**empty_suspensions** Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="c6e75-1267">**full_suspensions** 이 큐의 큐 채우기 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1267">**full_suspensions** Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="c6e75-1268">**full_errors** 이 큐의 큐 채우기 오류 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1268">**full_errors** Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="c6e75-1269">**timeouts** 이 큐의 스레드 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1269">**timeouts** Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1270">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1270">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1271">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1271">Return Values</span></span>

- <span data-ttu-id="c6e75-1272">**TX_SUCCESS**(0x00) 큐 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1272">**TX_SUCCESS** (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="c6e75-1273">**TX_PTR_ERROR**(0x03) 잘못된 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1273">**TX_PTR_ERROR** (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="c6e75-1274">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1275">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1275">Allowed From</span></span>

<span data-ttu-id="c6e75-1276">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1277">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1277">Example</span></span>

```c
TX_QUEUE my_queue;
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on the previously created
queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1278">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1278">See Also</span></span>

- <span data-ttu-id="c6e75-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1279">tx_queue_create</span></span>
- <span data-ttu-id="c6e75-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1280">tx_queue_delete</span></span>
- <span data-ttu-id="c6e75-1281">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="c6e75-1281">tx_queue_flush</span></span>
- <span data-ttu-id="c6e75-1282">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1282">tx_queue_front_send</span></span>
- <span data-ttu-id="c6e75-1283">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1283">tx_queue_info_get</span></span>
- <span data-ttu-id="c6e75-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="c6e75-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="c6e75-1286">tx_queue_receive</span></span>
- <span data-ttu-id="c6e75-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1287">tx_queue_send</span></span>
- <span data-ttu-id="c6e75-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="c6e75-1289">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1289">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="c6e75-1290">큐 시스템 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1290">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1291">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1291">Prototype</span></span>

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="c6e75-1292">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1292">Description</span></span>

<span data-ttu-id="c6e75-1293">이 서비스는 시스템의 모든 큐에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1293">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-1294">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 \***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1294">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1295">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1295">Parameters</span></span>

- <span data-ttu-id="c6e75-1296">**messages_sent** 모든 큐에서 수행된 총 송신 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1296">**messages_sent** Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="c6e75-1297">**messages_received** 모든 큐에서 수행된 총 수신 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1297">**messages_received** Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="c6e75-1298">**empty_suspensions** 모든 큐의 총 큐 비우기 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1298">**empty_suspensions** Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="c6e75-1299">**full_suspensions** 모든 큐의 총 큐 채우기 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1299">**full_suspensions** Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="c6e75-1300">**full_errors** 모든 큐의 총 큐 채우기 오류 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1300">**full_errors** Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="c6e75-1301">**timeouts** 모든 큐의 총 스레드 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1301">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1302">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1302">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

<span data-ttu-id="c6e75-1303">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1303">**Return Values**</span></span>

- <span data-ttu-id="c6e75-1304">**TX_SUCCESS**(0x00) 큐 시스템 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1304">**TX_SUCCESS** (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="c6e75-1305">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1305">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1306">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1306">Allowed From</span></span>

<span data-ttu-id="c6e75-1307">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1307">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1308">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1308">Example</span></span>

```c
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on all previously created
queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1309">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1309">See Also</span></span>

- <span data-ttu-id="c6e75-1310">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1310">tx_queue_create</span></span>
- <span data-ttu-id="c6e75-1311">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1311">tx_queue_delete</span></span>
- <span data-ttu-id="c6e75-1312">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="c6e75-1312">tx_queue_flush</span></span>
- <span data-ttu-id="c6e75-1313">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1313">tx_queue_front_send</span></span>
- <span data-ttu-id="c6e75-1314">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1314">tx_queue_info_get</span></span>
- <span data-ttu-id="c6e75-1315">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1315">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1316">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1316">tx_queue_prioritize</span></span>
- <span data-ttu-id="c6e75-1317">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="c6e75-1317">tx_queue_receive</span></span>
- <span data-ttu-id="c6e75-1318">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1318">tx_queue_send</span></span>
- <span data-ttu-id="c6e75-1319">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1319">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="c6e75-1320">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1320">tx_queue_prioritize</span></span>

<span data-ttu-id="c6e75-1321">큐 일시 중단 목록의 우선 순위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1321">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1322">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1322">Prototype</span></span>

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-1323">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1323">Description</span></span>

<span data-ttu-id="c6e75-1324">이 서비스는 일시 중단 목록 맨 앞에 있는, 이 큐의 메시지(또는 메시지 배치) 때문에 일시 중단된 스레드를 가장 높은 우선 순위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1324">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span>

<span data-ttu-id="c6e75-1325">다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1325">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1326">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1326">Parameters</span></span>

- <span data-ttu-id="c6e75-1327">**queue_ptr** 이전에 만든 메시지 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1327">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1328">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1328">Return Values</span></span>

- <span data-ttu-id="c6e75-1329">**TX_SUCCESS**(0x00) 큐 우선 순위 지정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1329">**TX_SUCCESS** (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="c6e75-1330">**TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1330">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1331">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1331">Allowed From</span></span>

<span data-ttu-id="c6e75-1332">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1332">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1333">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1333">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1334">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1334">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1335">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1335">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Ensure that the highest priority thread will receive
the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_queue_send or tx_queue_front_send call made
to this queue will wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1336">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1336">See Also</span></span>

- <span data-ttu-id="c6e75-1337">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1337">tx_queue_create</span></span>
- <span data-ttu-id="c6e75-1338">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1338">tx_queue_delete</span></span>
- <span data-ttu-id="c6e75-1339">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="c6e75-1339">tx_queue_flush</span></span>
- <span data-ttu-id="c6e75-1340">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1340">tx_queue_front_send</span></span>
- <span data-ttu-id="c6e75-1341">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1341">tx_queue_info_get</span></span>
- <span data-ttu-id="c6e75-1342">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1342">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1343">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1343">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1344">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="c6e75-1344">tx_queue_receive</span></span>
- <span data-ttu-id="c6e75-1345">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1345">tx_queue_send</span></span>
- <span data-ttu-id="c6e75-1346">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1346">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="c6e75-1347">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="c6e75-1347">tx_queue_receive</span></span>

<span data-ttu-id="c6e75-1348">메시지 큐에서 메시지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1348">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1349">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1349">Prototype</span></span>

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c6e75-1350">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1350">Description</span></span>

<span data-ttu-id="c6e75-1351">이 서비스는 지정된 메시지 큐에서 메시지를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1351">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="c6e75-1352">검색된 메시지는 큐로부터 대상 포인터로 지정된 메모리 영역으로 **복사됩니다**.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1352">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="c6e75-1353">그러면 해당 메시지는 큐에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1353">That message is then removed from the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-1354">지정된 대상 메모리 영역은 메시지를 저장할 수 있을 만큼 충분히 커야 합니다. 즉, **destination_ptr** __로 가리키는 메시지 대상은 이 큐의 메시지 크기 이상이어야 합니다. \*</span><span class="sxs-lookup"><span data-stu-id="c6e75-1354">*The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by* \***destination_ptr** _ _must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="c6e75-1355">그러지 않고 대상이 충분히 크지 않으면 다음 메모리 영역에서 메모리 손상이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1355">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1356">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1356">Parameters</span></span>

- <span data-ttu-id="c6e75-1357">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1357">**queue_ptr**</span></span> <br><span data-ttu-id="c6e75-1358">이전에 만든 메시지 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1358">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="c6e75-1359">**destination_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1359">**destination_ptr**</span></span> <br><span data-ttu-id="c6e75-1360">메시지를 복사할 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1360">Location of where to copy the message.</span></span>
- <span data-ttu-id="c6e75-1361">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1361">**wait_option**</span></span> <br><span data-ttu-id="c6e75-1362">메시지 큐가 비어 있는 경우의 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1362">Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="c6e75-1363">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1363">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c6e75-1364">**TX_NO_WAIT**(0x00000000) - TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1364">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="c6e75-1365">초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1365">This is the only valid option if the service is called from a non-thread; e.g.,  Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="c6e75-1366">**TX_WAIT_FOREVER**(0xFFFFFFFF) - TX_WAIT_FOREVER를 선택하면 메시지를 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1366">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>
  - <span data-ttu-id="c6e75-1367">시간 제한 값(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 메시지를 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1367">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1368">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1368">Return Values</span></span>

- <span data-ttu-id="c6e75-1369">**TX_SUCCESS**(0x00) 메시지 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1369">**TX_SUCCESS** (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="c6e75-1370">**TX_DELETED**(0x01) 스레드가 일시 중단된 동안 메시지 큐가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1370">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="c6e75-1371">**TX_QUEUE_EMPTY**(0x0A) 지정된 대기 시간 동안 큐가 비어 있어서 서비스가 메시지를 검색하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1371">**TX_QUEUE_EMPTY** (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="c6e75-1372">**TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1372">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="c6e75-1373">**TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1373">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="c6e75-1374">**TX_PTR_ERROR**(0x03) 메시지 대상 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1374">**TX_PTR_ERROR** (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="c6e75-1375">**TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1375">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1376">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1376">Allowed From</span></span>

<span data-ttu-id="c6e75-1377">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1377">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1378">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1378">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1379">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1379">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1380">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1380">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
empty, suspend until a message is present. Note that
this suspension is only possible from application
threads. */
status = tx_queue_receive(&my_queue, my_message,
    TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
"my_message." */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1381">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1381">See Also</span></span>

- <span data-ttu-id="c6e75-1382">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1382">tx_queue_create</span></span>
- <span data-ttu-id="c6e75-1383">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1383">tx_queue_delete</span></span>
- <span data-ttu-id="c6e75-1384">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="c6e75-1384">tx_queue_flush</span></span>
- <span data-ttu-id="c6e75-1385">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1385">tx_queue_front_send</span></span>
- <span data-ttu-id="c6e75-1386">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1386">tx_queue_info_get</span></span>
- <span data-ttu-id="c6e75-1387">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1387">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1388">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1388">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1389">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1389">tx_queue_prioritize</span></span>
- <span data-ttu-id="c6e75-1390">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1390">tx_queue_send</span></span>
- <span data-ttu-id="c6e75-1391">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1391">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="c6e75-1392">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1392">tx_queue_send</span></span>

<span data-ttu-id="c6e75-1393">메시지를 메시지 큐로 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1393">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1394">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1394">Prototype</span></span>

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c6e75-1395">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1395">Description</span></span>

<span data-ttu-id="c6e75-1396">이 서비스는 메시지를 지정된 메시지 큐로 송신합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1396">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="c6e75-1397">송신된 메시지는 원본 포인터로 지정된 메모리 영역에서 큐로 **복사됩니다**.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1397">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1398">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1398">Parameters</span></span>
- <span data-ttu-id="c6e75-1399">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1399">**queue_ptr**</span></span> <br><span data-ttu-id="c6e75-1400">이전에 만든 메시지 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1400">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="c6e75-1401">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1401">**source_ptr**</span></span> <br><span data-ttu-id="c6e75-1402">메시지에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1402">Pointer to the message.</span></span>
- <span data-ttu-id="c6e75-1403">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1403">**wait_option**</span></span> <br><span data-ttu-id="c6e75-1404">메시지 큐가 가득 찬 경우의 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1404">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="c6e75-1405">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1405">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c6e75-1406">**TX_NO_WAIT**(0x00000000) - TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1406">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="c6e75-1407">초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1407">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="c6e75-1408">**TX_WAIT_FOREVER**(0xFFFFFFFF) - TX_WAIT_FOREVER를 선택하면 큐에 공간이 있을 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1408">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="c6e75-1409">시간 제한 값(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 큐의 공간을 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1409">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1410">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1410">Return Values</span></span>

- <span data-ttu-id="c6e75-1411">**TX_SUCCESS**(0x00) 메시지 송신에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1411">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="c6e75-1412">**TX_DELETED**(0x01) 스레드가 일시 중단된 동안 메시지 큐가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1412">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="c6e75-1413">**TX_QUEUE_FULL**(0x0B) 지정된 대기 시간 중 큐가 가득 찼으므로 서비스에서 메시지를 송신할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1413">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="c6e75-1414">**TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1414">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="c6e75-1415">**TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1415">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="c6e75-1416">**TX_PTR_ERROR**(0x03) 잘못된 메시지 원본 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1416">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="c6e75-1417">**TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1417">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1418">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1418">Allowed From</span></span>

<span data-ttu-id="c6e75-1419">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1419">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1420">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1420">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1421">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1421">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1422">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1422">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
regardless of success. This wait option is used for
calls from initialization, timers, and ISRs. */
status = tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
queue. */
```

<span data-ttu-id="c6e75-1423">**참고 항목**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1423">**See Also**</span></span>

- <span data-ttu-id="c6e75-1424">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1424">tx_queue_create</span></span>
- <span data-ttu-id="c6e75-1425">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1425">tx_queue_delete</span></span>
- <span data-ttu-id="c6e75-1426">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="c6e75-1426">tx_queue_flush</span></span>
- <span data-ttu-id="c6e75-1427">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1427">tx_queue_front_send</span></span>
- <span data-ttu-id="c6e75-1428">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1428">tx_queue_info_get</span></span>
- <span data-ttu-id="c6e75-1429">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1429">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1430">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1430">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1431">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1431">tx_queue_prioritize</span></span>
- <span data-ttu-id="c6e75-1432">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="c6e75-1432">tx_queue_receive</span></span>
- <span data-ttu-id="c6e75-1433">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1433">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="c6e75-1434">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1434">tx_queue_send_notify</span></span>

<span data-ttu-id="c6e75-1435">메시지가 큐로 송신되면 애플리케이션에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1435">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1436">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1436">Prototype</span></span>

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a><span data-ttu-id="c6e75-1437">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1437">Description</span></span>

<span data-ttu-id="c6e75-1438">이 서비스는 메시지가 지정된 큐로 송신될 때마다 호출되는 알림 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1438">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="c6e75-1439">알림 콜백 처리는 애플리케이션에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1439">The processing of the notification callback is defined by the application.</span></span>

>[!NOTE]
> <span data-ttu-id="c6e75-1440">애플리케이션의 큐 송신 알림 콜백은 일시 중단 옵션을 사용하여 ThreadX API를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1440">*The application's queue send notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1441">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1441">Parameters</span></span>

- <span data-ttu-id="c6e75-1442">**queue_ptr** 이전에 만든 큐에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1442">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="c6e75-1443">**queue_send_notify** 애플리케이션 큐 송신 알림 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1443">**queue_send_notify** Pointer to application's queue send notification function.</span></span> <span data-ttu-id="c6e75-1444">이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1444">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1445">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1445">Return Values</span></span>

- <span data-ttu-id="c6e75-1446">**TX_SUCCESS**(0x00) 큐 송신 알림 등록에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1446">**TX_SUCCESS** (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="c6e75-1447">**TX_QUEUE_ERROR**(0x09) 잘못된 큐 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1447">**TX_QUEUE_ERROR** (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="c6e75-1448">**TX_FEATURE_NOT_ENABLED**(0xFF) 시스템이 알림 기능을 사용하지 않도록 설정하여 컴파일되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1448">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1449">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1449">Allowed From</span></span>

<span data-ttu-id="c6e75-1450">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1450">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1451">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1451">Example</span></span>

```c
TX_QUEUE my_queue;
/* Register the "my_queue_send_notify" function for monitoring
messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
    /* A message was just sent to this queue! */
}
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1452">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1452">See Also</span></span>

- <span data-ttu-id="c6e75-1453">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1453">tx_queue_create</span></span>
- <span data-ttu-id="c6e75-1454">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1454">tx_queue_delete</span></span>
- <span data-ttu-id="c6e75-1455">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="c6e75-1455">tx_queue_flush</span></span>
- <span data-ttu-id="c6e75-1456">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1456">tx_queue_front_send</span></span>
- <span data-ttu-id="c6e75-1457">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1457">tx_queue_info_get</span></span>
- <span data-ttu-id="c6e75-1458">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1458">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1459">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1459">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1460">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1460">tx_queue_prioritize</span></span>
- <span data-ttu-id="c6e75-1461">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="c6e75-1461">tx_queue_receive</span></span>
- <span data-ttu-id="c6e75-1462">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="c6e75-1462">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="c6e75-1463">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1463">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="c6e75-1464">최댓값이 있는 가산 세마포에 인스턴스를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1464">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1465">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1465">Prototype</span></span>

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a><span data-ttu-id="c6e75-1466">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1466">Description</span></span>

<span data-ttu-id="c6e75-1467">이 서비스는 지정된 가산 세마포에 인스턴스를 배치합니다. 실제로는 가산 세마포가 1씩 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1467">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="c6e75-1468">가산 세마포의 현재 값이 지정된 최댓값 이상인 경우 인스턴스가 배치되지 않으며 TX_CEILING_EXCEEDED 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1468">If the counting semaphore's current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1469">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1469">Parameters</span></span>

- <span data-ttu-id="c6e75-1470">**semaphore_ptr** 이전에 만든 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1470">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="c6e75-1471">**ceiling** 이 세마포에 허용되는 최대 한도입니다(유효한 값 범위는 1-0xFFFFFFFF임).</span><span class="sxs-lookup"><span data-stu-id="c6e75-1471">**ceiling** Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1472">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1472">Return Values</span></span>

- <span data-ttu-id="c6e75-1473">**TX_SUCCESS(0x00)** 세마포 최댓값 넣기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1473">**TX_SUCCESS (0x00)** Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="c6e75-1474">**TX_CEILING_EXCEEDED**(0x21) 넣기 요청이 최댓값을 초과합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1474">**TX_CEILING_EXCEEDED** (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="c6e75-1475">**TX_INVALID_CEILING**(0x22) 최댓값에 잘못된 값인 0이 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1475">**TX_INVALID_CEILING** (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="c6e75-1476">**TX_SEMAPHORE_ERROR**(0x0C) 잘못된 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1476">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1477">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1477">Allowed From</span></span>

<span data-ttu-id="c6e75-1478">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1478">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1479">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1479">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1480">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1480">See Also</span></span>

- <span data-ttu-id="c6e75-1481">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1481">tx_semaphore_create</span></span>
- <span data-ttu-id="c6e75-1482">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1482">tx_semaphore_delete</span></span>
- <span data-ttu-id="c6e75-1483">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1483">tx_semaphore_get</span></span>
- <span data-ttu-id="c6e75-1484">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1484">tx_semaphore_info_get</span></span>
- <span data-ttu-id="c6e75-1485">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1485">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1486">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1486">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1487">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1487">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="c6e75-1488">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1488">tx_semaphore_put</span></span>
- <span data-ttu-id="c6e75-1489">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1489">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="c6e75-1490">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1490">tx_semaphore_create</span></span>

<span data-ttu-id="c6e75-1491">가산 세마포를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1491">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1492">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1492">Prototype</span></span>

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a><span data-ttu-id="c6e75-1493">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1493">Description</span></span>

<span data-ttu-id="c6e75-1494">이 서비스는 스레드 간 동기화에 사용되는 가산 세마포를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1494">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="c6e75-1495">초기 세마포 개수는 입력 매개 변수로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1495">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1496">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1496">Parameters</span></span>

- <span data-ttu-id="c6e75-1497">**semaphore_ptr** 세마포 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1497">**semaphore_ptr** Pointer to a semaphore control block.</span></span>
- <span data-ttu-id="c6e75-1498">**name_ptr** 세마포 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1498">**name_ptr** Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="c6e75-1499">**initial_count** 이 세마포의 초기 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1499">**initial_count** Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="c6e75-1500">올바른 값 범위는 0x00000000-0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1500">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1501">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1501">Return Values</span></span>

- <span data-ttu-id="c6e75-1502">**TX_SUCCESS**(0x00) 세마포 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1502">**TX_SUCCESS** (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="c6e75-1503">**TX_SEMAPHORE_ERROR**(0x0C) 잘못된 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1503">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="c6e75-1504">포인터가 NULL이거나 세마포가 이미 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1504">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="c6e75-1505">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1505">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1506">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1506">Allowed From</span></span>

<span data-ttu-id="c6e75-1507">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-1507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1508">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1508">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1509">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1509">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1510">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1510">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Create a counting semaphore whose initial value is 1.
This is typically the technique used to make a binary
semaphore. Binary semaphores are used to provide
protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
    "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
use. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1511">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1511">See Also</span></span>

- <span data-ttu-id="c6e75-1512">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1512">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="c6e75-1513">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1513">tx_semaphore_delete</span></span>
- <span data-ttu-id="c6e75-1514">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1514">tx_semaphore_get</span></span>
- <span data-ttu-id="c6e75-1515">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1515">tx_semaphore_info_get</span></span>
- <span data-ttu-id="c6e75-1516">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1516">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1517">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1517">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1518">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1518">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="c6e75-1519">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1519">tx_semaphore_put</span></span>
- <span data-ttu-id="c6e75-1520">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1520">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="c6e75-1521">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1521">tx_semaphore_delete</span></span>

<span data-ttu-id="c6e75-1522">가산 세마포를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1522">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1523">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1523">Prototype</span></span>
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-1524">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1524">Description</span></span>

<span data-ttu-id="c6e75-1525">이 서비스는 지정된 가산 세마포를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1525">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="c6e75-1526">세마포 인스턴스를 기다리는 일시 중단된 모든 스레드는 다시 시작되며 TX_DELETED 반환 상태가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1526">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-1527">애플리케이션은 이 세마포를 삭제하기 전에 이 세마포에 대한 모든 넣기 알림 콜백이 완료되었는지(또는 사용하지 않도록 설정되었는지) 확인해야 합니다. 또한 애플리케이션은 이후에는 삭제된 세마포를 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1527">*The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore. In addition, the application must prevent all future use of a deleted semaphore.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1528">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1528">Parameters</span></span>

- <span data-ttu-id="c6e75-1529">**semaphore_ptr** 이전에 만든 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1529">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1530">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1530">Return Values</span></span>

- <span data-ttu-id="c6e75-1531">**TX_SUCCESS**(0x00) 가산 세마포 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1531">**TX_SUCCESS** (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="c6e75-1532">**TX_SEMAPHORE_ERROR**(0x0C) 잘못된 가산 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1532">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="c6e75-1533">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1533">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1534">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1534">Allowed From</span></span>

<span data-ttu-id="c6e75-1535">스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-1535">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1536">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1536">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1537">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1537">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1538">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1538">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

<span data-ttu-id="c6e75-1539">**참고 항목**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1539">**See Also**</span></span>

- <span data-ttu-id="c6e75-1540">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1540">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="c6e75-1541">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1541">tx_semaphore_create</span></span>
- <span data-ttu-id="c6e75-1542">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1542">tx_semaphore_get</span></span>
- <span data-ttu-id="c6e75-1543">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1543">tx_semaphore_info_get</span></span>
- <span data-ttu-id="c6e75-1544">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1544">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1545">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1545">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1546">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1546">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="c6e75-1547">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1547">tx_semaphore_put</span></span>
- <span data-ttu-id="c6e75-1548">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1548">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="c6e75-1549">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1549">tx_semaphore_get</span></span>

<span data-ttu-id="c6e75-1550">가산 세마포에서 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1550">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1551">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1551">Prototype</span></span>

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c6e75-1552">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1552">Description</span></span>

<span data-ttu-id="c6e75-1553">이 서비스는 지정된 가산 세마포에서 인스턴스(단일 개수)를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1553">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="c6e75-1554">결과적으로 지정된 세마포 개수가 1씩 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1554">As a result, the specified semaphore's count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1555">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1555">Parameters</span></span>

- <span data-ttu-id="c6e75-1556">**semaphore_ptr**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1556">**semaphore_ptr**</span></span> <br><span data-ttu-id="c6e75-1557">이전에 만든 가산 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1557">Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="c6e75-1558">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1558">**wait_option**</span></span> <br><span data-ttu-id="c6e75-1559">사용할 수 있는 세마포 인스턴스가 없는 경우(세마포 개수가 0인 경우)의 서비스 작동 방식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1559">Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="c6e75-1560">대기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1560">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c6e75-1561">**TX_NO_WAIT**(0x00000000) - TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1561">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="c6e75-1562">초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1562">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="c6e75-1563">**TX_WAIT_FOREVER**(0xFFFFFFFF) - TX_WAIT_FOREVER를 선택하면 세마포 인스턴스를 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1563">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span>
  - <span data-ttu-id="c6e75-1564">시간 제한 값(0x00000001 through 0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 세마포 인스턴스를 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1564">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1565">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1565">Return Values</span></span>

- <span data-ttu-id="c6e75-1566">**TX_SUCCESS**(0x00) 세마포 인스턴스 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1566">**TX_SUCCESS** (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="c6e75-1567">**TX_DELETED**(0x01) 스레드가 일시 중단된 동안 가산 세마포가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1567">**TX_DELETED** (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="c6e75-1568">**TX_NO_INSTANCE**(0x0D) 서비스가 가산 세마포 인스턴스를 검색하지 못했습니다(지정된 대기 시간에 세마포 개수가 0임).</span><span class="sxs-lookup"><span data-stu-id="c6e75-1568">**TX_NO_INSTANCE** (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="c6e75-1569">**TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1569">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="c6e75-1570">**TX_SEMAPHORE_ERROR**(0x0C) 잘못된 가산 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1570">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="c6e75-1571">**TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1571">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1572">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1572">Allowed From</span></span>

<span data-ttu-id="c6e75-1573">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1573">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1574">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1574">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1575">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1575">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1576">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1576">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Get a semaphore instance from the semaphore
"my_semaphore." If the semaphore count is zero,
suspend until an instance becomes available.
Note that this suspension is only possible from
application threads. */
status = tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
an instance of the semaphore. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1577">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1577">See Also</span></span>

- <span data-ttu-id="c6e75-1578">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1578">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="c6e75-1579">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1579">tx_semaphore_create</span></span>
- <span data-ttu-id="c6e75-1580">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1580">tx_semahore_delete</span></span>
- <span data-ttu-id="c6e75-1581">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1581">tx_semaphore_info_get</span></span>
- <span data-ttu-id="c6e75-1582">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1582">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1583">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1583">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="c6e75-1584">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1584">tx_semaphore_put</span></span>
- <span data-ttu-id="c6e75-1585">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1585">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="c6e75-1586">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1586">tx_semaphore_info_get</span></span>

<span data-ttu-id="c6e75-1587">세마포에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1587">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1588">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1588">Prototype</span></span>

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a><span data-ttu-id="c6e75-1589">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1589">Description</span></span>

<span data-ttu-id="c6e75-1590">이 서비스는 지정된 세마포에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1590">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1591">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1591">Parameters</span></span>

- <span data-ttu-id="c6e75-1592">**semaphore_ptr** 세마포 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1592">**semaphore_ptr** Pointer to semaphore control block.</span></span>
- <span data-ttu-id="c6e75-1593">**name** 세마포 이름에 대한 포인터의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1593">**name** Pointer to destination for the pointer to the semaphore's name.</span></span>
- <span data-ttu-id="c6e75-1594">**current_value** 현재 세마포 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1594">**current_value** Pointer to destination for the current semaphore's count.</span></span>
- <span data-ttu-id="c6e75-1595">**first_suspended** 이 세마포의 일시 중단 목록에 있는 첫 번째 스레드에 대한 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1595">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="c6e75-1596">**suspended_count** 현재 이 세마포의 일시 중단된 스레드 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1596">**suspended_count** Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="c6e75-1597">**next_semaphore** 다음에 만들 세마포 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1597">**next_semaphore** Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1598">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1598">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1599">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1599">Return Values</span></span>

- <span data-ttu-id="c6e75-1600">**TX_SUCCESS**(0x00) 정보를 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1600">**TX_SUCCESS** (0x00) information retrieval.</span></span>

- <span data-ttu-id="c6e75-1601">**TX_SEMAPHORE_ERROR**(0x0C) 잘못된 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1601">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1602">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1602">Allowed From</span></span>

<span data-ttu-id="c6e75-1603">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1603">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1604">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1604">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1605">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1605">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1606">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1606">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
CHAR *name;
ULONG current_value;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT status;

/* Retrieve information about the previously created
semaphore "my_semaphore." */
status = tx_semaphore_info_get(&my_semaphore, &name,
    &current_value,
    &first_suspended, &suspended_count,
    &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1607">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1607">See Also</span></span>

- <span data-ttu-id="c6e75-1608">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1608">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="c6e75-1609">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1609">tx_semaphore_create</span></span>
- <span data-ttu-id="c6e75-1610">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1610">tx_semaphore_delete</span></span>
- <span data-ttu-id="c6e75-1611">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1611">tx_semaphore_get</span></span>
- <span data-ttu-id="c6e75-1612">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1612">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1613">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1613">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1614">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1614">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="c6e75-1615">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1615">tx_semaphore_put</span></span>
- <span data-ttu-id="c6e75-1616">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1616">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="c6e75-1617">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1617">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="c6e75-1618">세마포 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1618">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1619">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1619">Prototype</span></span>

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="c6e75-1620">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1620">Description</span></span>

<span data-ttu-id="c6e75-1621">이 서비스는 지정된 세마포에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1621">This service retrieves performance information about the specified semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-1622">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 \***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1622">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

<span data-ttu-id="c6e75-1623">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1623">**Parameters**</span></span>

-  <span data-ttu-id="c6e75-1624">**semaphore_ptr** 이전에 만든 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1624">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
-  <span data-ttu-id="c6e75-1625">**puts** 이 세마포에서 수행된 넣기 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1625">**puts** Pointer to destination for the number of put requests performed on this semaphore.</span></span>
-  <span data-ttu-id="c6e75-1626">**gets** 이 세마포에서 수행된 가져오기 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1626">**gets** Pointer to destination for the number of get requests performed on this semaphore.</span></span>
-  <span data-ttu-id="c6e75-1627">**suspensions** 이 세마포의 스레드 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1627">**suspensions** Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
-  <span data-ttu-id="c6e75-1628">**timeouts** 이 세마포의 스레드 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1628">**timeouts** Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1629">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1629">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1630">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1630">Return Values</span></span>

- <span data-ttu-id="c6e75-1631">**TX_SUCCESS**(0x00) 세마포 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1631">**TX_SUCCESS** (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="c6e75-1632">**TX_PTR_ERROR**(0x03) 잘못된 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1632">**TX_PTR_ERROR** (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="c6e75-1633">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1633">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1634">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1634">Allowed From</span></span>

<span data-ttu-id="c6e75-1635">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1635">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1636">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1636">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created
semaphore. */
status = tx_semaphore_performance_info_get(&my_semaphore, &puts,
    &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1637">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1637">See Also</span></span>

- <span data-ttu-id="c6e75-1638">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1638">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="c6e75-1639">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1639">tx_semaphore_create</span></span>
- <span data-ttu-id="c6e75-1640">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1640">tx_semaphore_delete</span></span>
- <span data-ttu-id="c6e75-1641">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1641">tx_semaphore_get</span></span>
- <span data-ttu-id="c6e75-1642">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1642">tx_semaphore_info_get</span></span>
- <span data-ttu-id="c6e75-1643">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1643">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1644">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1644">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="c6e75-1645">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1645">tx_semaphore_put</span></span>
- <span data-ttu-id="c6e75-1646">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1646">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="c6e75-1647">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1647">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="c6e75-1648">세마포 시스템 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1648">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1649">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1649">Prototype</span></span>

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="c6e75-1650">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1650">Description</span></span>

<span data-ttu-id="c6e75-1651">이 서비스는 시스템의 모든 세마포에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1651">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-1652">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 \***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1652">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1653">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1653">Parameters</span></span>

- <span data-ttu-id="c6e75-1654">**puts** 모든 세마포에서 수행된 총 넣기 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1654">**puts** Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="c6e75-1655">**gets** 모든 세마포에서 수행된 총 가져오기 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1655">**gets** Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="c6e75-1656">**suspensions** 모든 세마포의 총 스레드 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1656">**suspensions** Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="c6e75-1657">**timeouts** 모든 세마포의 총 스레드 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1657">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1658">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1658">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1659">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1659">Return Values</span></span>

- <span data-ttu-id="c6e75-1660">**TX_SUCCESS**(0x00) 시스템 성능을 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1660">**TX_SUCCESS** (0x00) system performance get.</span></span>
- <span data-ttu-id="c6e75-1661">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1661">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1662">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1662">Allowed From</span></span>

<span data-ttu-id="c6e75-1663">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1663">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1664">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1664">Example</span></span>

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created
semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1665">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1665">See Also</span></span>

- <span data-ttu-id="c6e75-1666">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1666">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="c6e75-1667">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1667">tx_semaphore_create</span></span>
- <span data-ttu-id="c6e75-1668">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1668">tx_semaphore_delete</span></span>
- <span data-ttu-id="c6e75-1669">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1669">tx_semaphore_get</span></span>
- <span data-ttu-id="c6e75-1670">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1670">tx_semaphore_info_get</span></span>
- <span data-ttu-id="c6e75-1671">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1671">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1672">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1672">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="c6e75-1673">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1673">tx_semaphore_put</span></span>
- <span data-ttu-id="c6e75-1674">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1674">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="c6e75-1675">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1675">tx_semaphore_prioritize</span></span>

<span data-ttu-id="c6e75-1676">세마포 일시 중단 목록의 우선 순위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1676">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1677">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1677">Prototype</span></span>

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-1678">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1678">Description</span></span>

<span data-ttu-id="c6e75-1679">이 서비스는 일시 중단 목록 맨 앞에 있는, 세마포 인스턴스 때문에 일시 중단된 스레드를 가장 높은 우선 순위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1679">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="c6e75-1680">다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1680">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1681">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1681">Parameters</span></span>

- <span data-ttu-id="c6e75-1682">**semaphore_ptr** 이전에 만든 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1682">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1683">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1683">Return Values</span></span>

- <span data-ttu-id="c6e75-1684">**TX_SUCCESS**(0x00) 세마포 우선 순위 지정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1684">**TX_SUCCESS** (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="c6e75-1685">**TX_SEMAPHORE_ERROR**(0x0C) 잘못된 가산 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1685">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1686">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1686">Allowed From</span></span>

<span data-ttu-id="c6e75-1687">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1687">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1688">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1688">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1689">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1689">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1690">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1690">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Ensure that the highest priority thread will receive
the next instance of this semaphore. */
status = tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_semaphore_put call made to this semaphore will
wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1691">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1691">See Also</span></span>

- <span data-ttu-id="c6e75-1692">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1692">tx_semaphore_create</span></span>
- <span data-ttu-id="c6e75-1693">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1693">tx_semaphore_delete</span></span>
- <span data-ttu-id="c6e75-1694">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1694">tx_semaphore_get</span></span>
- <span data-ttu-id="c6e75-1695">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1695">tx_semaphore_info_get</span></span>
- <span data-ttu-id="c6e75-1696">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1696">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="c6e75-1697">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1697">tx_semaphore_put</span></span>

<span data-ttu-id="c6e75-1698">가산 세마포에 인스턴스를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1698">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1699">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1699">Prototype</span></span>

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-1700">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1700">Description</span></span>

<span data-ttu-id="c6e75-1701">이 서비스는 지정된 가산 세마포에 인스턴스를 배치합니다. 실제로는 가산 세마포가 1씩 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1701">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1702">세마포가 모두 1(OxFFFFFFFF)인 경우 이 서비스를 호출하면 새 넣기 작업으로 인해 세마포가 0으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1702">*If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1703">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1703">Parameters</span></span>

- <span data-ttu-id="c6e75-1704">**semaphore_ptr** 이전에 만든 가산 세마포 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1704">**semaphore_ptr** Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1705">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1705">Return Values</span></span>

- <span data-ttu-id="c6e75-1706">**TX_SUCCESS**(0x00) 세마포 넣기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1706">**TX_SUCCESS** (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="c6e75-1707">**TX_SEMAPHORE_ERROR**(0x0C) 잘못된 가산 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1707">**TX_SEMAPHORE_ERROR** (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1708">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1708">Allowed From</span></span>

<span data-ttu-id="c6e75-1709">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1709">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1710">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1710">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1711">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1711">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1712">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1712">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1713">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1713">See Also</span></span>

- <span data-ttu-id="c6e75-1714">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1714">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="c6e75-1715">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1715">tx_semaphore_create</span></span>
- <span data-ttu-id="c6e75-1716">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1716">tx_semaphore_delete</span></span>
- <span data-ttu-id="c6e75-1717">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1717">tx_semaphore_info_get</span></span>
- <span data-ttu-id="c6e75-1718">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1718">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1719">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1719">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1720">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1720">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="c6e75-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="c6e75-1722">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1722">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="c6e75-1723">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1723">tx_semaphore_put_notify</span></span>

<span data-ttu-id="c6e75-1724">세마포가 배치되면 애플리케이션에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1724">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1725">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1725">Prototype</span></span>

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a><span data-ttu-id="c6e75-1726">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1726">Description</span></span>

<span data-ttu-id="c6e75-1727">이 서비스는 지정된 세마포가 배치될 때마다 호출되는 알림 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1727">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="c6e75-1728">알림 콜백 처리는 애플리케이션에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1728">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1729">애플리케이션의 세마포 알림 콜백은 일시 중단 옵션을 사용하여 ThreadX API를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1729">*The application's semaphore notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1730">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1730">Parameters</span></span>

- <span data-ttu-id="c6e75-1731">**semaphore_ptr** 이전에 만든 세마포에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1731">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="c6e75-1732">**semaphore_put_notify** 애플리케이션의 세마포 넣기 알림 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1732">**semaphore_put_notify** Pointer to application's semaphore put notification function.</span></span> <span data-ttu-id="c6e75-1733">이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1733">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1734">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1734">Return Values</span></span>

- <span data-ttu-id="c6e75-1735">**TX_SUCCESS**(0x00) 세마포 넣기 알림 등록에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1735">**TX_SUCCESS** (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="c6e75-1736">**TX_SEMAPHORE_ERROR**(0x0C) 잘못된 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1736">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="c6e75-1737">**TX_FEATURE_NOT_ENABLED**(0xFF) 시스템이 알림 기능을 사용하지 않도록 설정하여 컴파일되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1737">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1738">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1738">Allowed From</span></span>

<span data-ttu-id="c6e75-1739">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1739">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1740">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1740">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
the put operations on the semaphore "my_semaphore." */
status = tx_semaphore_put_notify(&my_semaphore, my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
was successfully registered. */
void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
    /* The semaphore was just put! */
}
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1741">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1741">See Also</span></span>

- <span data-ttu-id="c6e75-1742">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1742">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="c6e75-1743">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1743">tx_semaphore_create</span></span>
- <span data-ttu-id="c6e75-1744">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1744">tx_semaphore_delete</span></span>
- <span data-ttu-id="c6e75-1745">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1745">tx_semaphore_get</span></span>
- <span data-ttu-id="c6e75-1746">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1746">tx_semaphore_info_get</span></span>
- <span data-ttu-id="c6e75-1747">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1747">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1748">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1748">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1749">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="c6e75-1749">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="c6e75-1750">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="c6e75-1750">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="c6e75-1751">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1751">tx_thread_create</span></span>

<span data-ttu-id="c6e75-1752">애플리케이션 스레드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1752">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1753">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1753">Prototype</span></span>

```c
UINT tx_thread_create(
    TX_THREAD *thread_ptr,
    CHAR *name_ptr, 
    VOID (*entry_function)(ULONG),
    ULONG entry_input, 
    VOID *stack_start,
    ULONG stack_size, 
    UINT priority,
    UINT preempt_threshold, 
    ULONG time_slice,
    UINT auto_start);
```

### <a name="description"></a><span data-ttu-id="c6e75-1754">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1754">Description</span></span>

<span data-ttu-id="c6e75-1755">이 서비스는 지정된 작업 항목 함수에서 실행되기 시작하는 애플리케이션 스레드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1755">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="c6e75-1756">스택, 우선 순위, 선점 임계값, 시간 조각과 같은 특성은 입력 매개 변수를 통해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1756">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="c6e75-1757">스레드의 초기 실행 상태도 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1757">In addition, the initial execution state of the thread is also specified.</span></span>

<span data-ttu-id="c6e75-1758">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="c6e75-1758">**Parameters**</span></span>

- <span data-ttu-id="c6e75-1759">**thread_ptr** 스레드 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1759">**thread_ptr** Pointer to a thread control block.</span></span>
- <span data-ttu-id="c6e75-1760">**name_ptr** 스레드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1760">**name_ptr** Pointer to the name of the thread.</span></span>
- <span data-ttu-id="c6e75-1761">**entry_function** 스레드 실행을 위한 초기 C 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1761">**entry_function** Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="c6e75-1762">이 진입 함수에서 스레드가 반환되면 ‘완료됨’ 상태로 지정되고 무기한으로 일시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1762">When a thread returns from this entry function, it is placed in a *completed* state and suspended indefinitely.</span></span>
- <span data-ttu-id="c6e75-1763">**entry_input** 처음 실행될 때 스레드의 진입 함수로 전달되는 32비트 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1763">**entry_input** A 32-bit value that is passed to the thread's entry function when it first executes.</span></span> <span data-ttu-id="c6e75-1764">이러한 입력을 사용할 것인지 여부는 전적으로 해당 애플리케이션에서 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1764">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="c6e75-1765">**stack_start** 스택 메모리 영역의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1765">**stack_start** Starting address of the stack's memory area.</span></span>
- <span data-ttu-id="c6e75-1766">**stack_size** 스택 메모리 영역의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1766">**stack_size** Number bytes in the stack memory area.</span></span> <span data-ttu-id="c6e75-1767">스레드의 스택 영역은 최악의 사례 함수 호출 중첩 및 지역 변수 사용을 처리할 수 있을 만큼 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1767">The thread's stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="c6e75-1768">**priority** 숫자로 된 스레드 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1768">**priority** Numerical priority of thread.</span></span> <span data-ttu-id="c6e75-1769">유효한 값 범위는 0에서 (TX_MAX_PRIORITES-1)까지입니다. 여기서 값 0은 가장 높은 우선 순위를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1769">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="c6e75-1770">**preempt_threshold** 사용하지 않도록 설정된 선점의 가장 높은 우선 순위 수준(0에서 (TX_MAX_PRIORITIES-1))입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1770">**preempt_threshold** Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="c6e75-1771">우선 순위가 이 수준보다 높아야만 이 스레드를 선점할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1771">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="c6e75-1772">이 값은 지정한 우선 순위 이하여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1772">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="c6e75-1773">스레드 우선 순위와 값이 같으면 선점 임계값이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1773">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="c6e75-1774">**time_slice** 우선 순위가 같은 다른 준비 스레드를 실행할 수 있을 때까지 이 스레드를 실행할 수 있는 타이머 틱 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1774">**time_slice** Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="c6e75-1775">선점 임계값을 사용하면 시간 조각화를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1775">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="c6e75-1776">유효한 시간 조각 값 범위는 1-0xFFFFFFFF(포함)입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1776">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="c6e75-1777">**TX_NO_TIME_SLICE** 값(값 0)을 사용하면 이 스레드의 시간 조각화가 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1777">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c6e75-1778">시간 조각화를 사용하면 약간의 시스템 오버헤드가 발생합니다. 시간 조각화는 여러 스레드가 동일한 우선 순위를 공유하는 경우에만 유용하므로 고유한 우선 순위가 있는 스레드에는 시간 조각이 할당되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1778">*Using time-slicing results in a slight amount of system overhead.   Since time-slicing is only useful in cases where multiple threads   share the same priority, threads having a unique priority should not   be assigned a time-slice.*</span></span>

- <span data-ttu-id="c6e75-1779">**auto_start** 스레드가 바로 시작되는지 일시 중단 상태로 설정되는지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1779">**auto_start** Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="c6e75-1780">유효한 옵션은 **TX_AUTO_START**(0x01) 및 **TX_DONT_START**(0x00)입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1780">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="c6e75-1781">TX_DONT_START를 지정하면 애플리케이션은 나중에 tx_thread_resume을 호출해야 스레드를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1781">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1782">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1782">Return Values</span></span>

- <span data-ttu-id="c6e75-1783">**TX_SUCCESS**(0x00) 스레드 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1783">**TX_SUCCESS** (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="c6e75-1784">**TX_THREAD_ERROR**(0x0E) 잘못된 스레드 제어 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1784">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="c6e75-1785">포인터가 NULL이거나 스레드가 이미 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1785">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="c6e75-1786">**TX_PTR_ERROR**(0x03) 진입점의 시작 주소가 잘못되었거나 스택 영역이 잘못되었습니다(일반적으로 NULL).</span><span class="sxs-lookup"><span data-stu-id="c6e75-1786">**TX_PTR_ERROR** (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="c6e75-1787">**TX_SIZE_ERROR**(0x05) 스택 영역 크기가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1787">**TX_SIZE_ERROR** (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="c6e75-1788">스레드를 실행하려면 **TX_MINIMUM_STACK** 바이트 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1788">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="c6e75-1789">**TX_PRIORITY_ERROR**(0x0F) 잘못된 스레드 우선 순위입니다. 값이 (0-(TX_MAX_PRIORITIES-1)) 범위를 벗어납니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1789">**TX_PRIORITY_ERROR** (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="c6e75-1790">**TX_THRESH_ERROR**(0x18) 잘못된 preemptionthreshold가 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1790">**TX_THRESH_ERROR** (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="c6e75-1791">이 값은 스레드 초기 우선 순위 이하의 유효한 우선 순위여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1791">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="c6e75-1792">**TX_START_ERROR**(0x10) 잘못된 자동 시작 선택입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1792">**TX_START_ERROR** (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="c6e75-1793">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1793">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1794">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1794">Allowed From</span></span>

<span data-ttu-id="c6e75-1795">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-1795">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1796">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1796">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1797">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1797">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1798">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1798">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Create a thread of priority 15 whose entry point is
"my_thread_entry". This thread’s stack area is 1000
bytes in size, starting at address 0x400000. The
preemption-threshold is setup to allow preemption of threads
with priorities ranging from 0 through 14. Time-slicing is
disabled. This thread is automatically put into a ready
condition. */
status = tx_thread_create(&my_thread, "my_thread_name",
    my_thread_entry, 0x1234,
    (VOID *) 0x400000, 1000,
    15, 15, TX_NO_TIME_SLICE,
    TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
for execution! */

...

/* Thread’s entry function. When "my_thread" actually
begins execution, control is transferred to this
function. */

VOID my_thread_entry (ULONG initial_input)
{
    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */
    /* The real work of the thread, including calls to
    other function should be called from here! */
    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1799">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1799">See Also</span></span>

- <span data-ttu-id="c6e75-1800">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1800">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-1801">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1801">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-1802">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1802">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-1803">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1803">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-1804">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1804">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1805">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1805">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1806">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1806">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-1807">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1807">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-1808">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-1808">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-1809">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-1809">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-1810">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-1810">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-1811">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-1811">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-1812">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1812">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-1813">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-1813">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-1814">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-1814">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-1815">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1815">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-1816">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-1816">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="c6e75-1817">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1817">tx_thread_delete</span></span>

<span data-ttu-id="c6e75-1818">애플리케이션 스레드를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1818">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1819">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1819">Prototype</span></span>

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-1820">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1820">Description</span></span>

<span data-ttu-id="c6e75-1821">이 서비스는 지정된 애플리케이션 스레드를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1821">This service deletes the specified application thread.</span></span> <span data-ttu-id="c6e75-1822">지정된 스레드가 종료 상태 또는 완료 상태여야 하므로 이 서비스는 자체를 삭제하려고 시도하는 스레드에서 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1822">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1823">이 서비스가 완료된 후 사용할 수 있는 스레드 스택과 연결된 메모리 영역은 애플리케이션에서 관리해야 합니다. 또한 애플리케이션은 삭제된 스레드를 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1823">*It is the application's responsibility to manage the memory area associated with the thread's stack, which is available after this service completes. In addition, the application must prevent use of a deleted thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1824">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1824">Parameters</span></span>

- <span data-ttu-id="c6e75-1825">**thread_ptr** 이전에 만든 애플리케이션 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1825">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1826">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1826">Return Values</span></span>

- <span data-ttu-id="c6e75-1827">**TX_SUCCESS**(0x00) 스레드 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1827">**TX_SUCCESS** (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="c6e75-1828">**TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1828">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="c6e75-1829">**TX_DELETE_ERROR**(0x11) 지정된 스레드가 종료 상태 또는 완료 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1829">**TX_DELETE_ERROR** (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="c6e75-1830">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1830">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1831">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1831">Allowed From</span></span>

<span data-ttu-id="c6e75-1832">스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="c6e75-1832">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1833">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1833">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1834">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1834">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1835">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1835">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Delete an application thread whose control block is
"my_thread". Assume that the thread has already been
created with a call to tx_thread_create. */
status = tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1836">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1836">See Also</span></span>

- <span data-ttu-id="c6e75-1837">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1837">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-1838">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1838">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-1839">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1839">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-1840">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1840">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-1841">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1841">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1842">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1842">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1843">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1843">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-1844">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1844">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-1845">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-1845">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-1846">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-1846">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-1847">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-1847">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-1848">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-1848">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-1849">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1849">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-1850">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-1850">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-1851">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-1851">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-1852">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1852">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-1853">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-1853">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="c6e75-1854">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1854">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="c6e75-1855">스레드 진입 및 종료 시 애플리케이션에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1855">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1856">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1856">Prototype</span></span>

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a><span data-ttu-id="c6e75-1857">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1857">Description</span></span>

<span data-ttu-id="c6e75-1858">이 서비스는 지정된 스레드에 진입하거나 종료할 때마다 호출되는 알림 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1858">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="c6e75-1859">알림 콜백 처리는 애플리케이션에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1859">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1860">애플리케이션 스레드 진입/종료 알림 콜백은 일시 중단 옵션을 사용하여 ThreadX API를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1860">The application's thread entry/exit notification callback is not allowed to call any ThreadX API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1861">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1861">Parameters</span></span>

- <span data-ttu-id="c6e75-1862">**thread_ptr** 이전에 만든 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1862">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="c6e75-1863">**entry_exit_notify** 애플리케이션 스레드 진입/종료 알림 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1863">**entry_exit_notify** Pointer to application's thread entry/exit notification function.</span></span> <span data-ttu-id="c6e75-1864">진입/종료 알림 함수의 두 번째 매개 변수는 진입 또는 종료가 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1864">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="c6e75-1865">값 **TX_THREAD_ENTRY**(0x00)는 스레드에 진입했음을 나타내고, 값 **TX_THREAD_EXIT**(0x01)는 스레드가 종료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1865">The value **TX_THREAD_ENTRY** (0x00) indicates the thread was entered, while the value **TX_THREAD_EXIT** (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="c6e75-1866">이 값이 **TX_NULL** 이면 알림이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1866">If this value is **TX_NULL**, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1867">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1867">Return Values</span></span>

- <span data-ttu-id="c6e75-1868">**TX_SUCCESS**(0x00) 스레드 진입/종료 알림 함수 등록에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1868">**TX_SUCCESS** (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="c6e75-1869">**TX_THREAD_ERROR**(0x0E) 잘못된 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1869">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="c6e75-1870">**TX_FEATURE_NOT_ENABLED**(0xFF) 시스템이 알림 기능을 사용하지 않도록 설정하여 컴파일되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1870">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1871">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1871">Allowed From</span></span>

<span data-ttu-id="c6e75-1872">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1872">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1873">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1873">Example</span></span>

```c
TX_THREAD my_thread;
/* Register the "my_entry_exit_notify" function for monitoring
the entry/exit of the thread "my_thread." */
status = tx_thread_entry_exit_notify(&my_thread,
    my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{
    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
        /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
        /* Thread exit! */
}
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1874">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1874">See Also</span></span>

- <span data-ttu-id="c6e75-1875">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1875">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-1876">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1876">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-1877">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1877">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-1878">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1878">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-1879">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1879">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-1880">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1880">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1881">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1881">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1882">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1882">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-1883">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1883">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-1884">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-1884">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-1885">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-1885">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-1886">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-1886">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-1887">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-1887">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-1888">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1888">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-1889">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-1889">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-1890">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-1890">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-1891">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1891">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-1892">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-1892">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="c6e75-1893">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1893">tx_thread_identify</span></span>

<span data-ttu-id="c6e75-1894">현재 실행 중인 스레드에 대한 포인터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1894">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1895">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1895">Prototype</span></span>

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="c6e75-1896">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1896">Description</span></span>

<span data-ttu-id="c6e75-1897">이 서비스는 현재 실행 중인 스레드에 대한 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1897">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="c6e75-1898">스레드가 실행되고 있지 않으면 이 서비스는 Null 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1898">If no thread is executing, this service returns a null pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1899">이 서비스를 ISR에서 호출하는 경우 반환 값은 실행 중인 인터럽트 처리기 이전에 실행되는 스레드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1899">*If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1900">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1900">Parameters</span></span>

<span data-ttu-id="c6e75-1901">None</span><span class="sxs-lookup"><span data-stu-id="c6e75-1901">None</span></span>

### <a name="retuen-values"></a><span data-ttu-id="c6e75-1902">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1902">Retuen Values</span></span>

- <span data-ttu-id="c6e75-1903">**thread pointer** 현재 실행 중인 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1903">**thread pointer** Pointer to the currently executing thread.</span></span> <span data-ttu-id="c6e75-1904">실행 중인 스레드가 없는 경우 반환 값은 **TX_NULL** 입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1904">If no thread is executing, the return value is **TX_NULL**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1905">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1905">Allowed From</span></span>

<span data-ttu-id="c6e75-1906">스레드, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1906">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1907">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1907">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1908">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1908">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1909">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1909">Example</span></span>

<span data-ttu-id="c6e75-1910">TX_THREAD \*my_thread_ptr;</span><span class="sxs-lookup"><span data-stu-id="c6e75-1910">TX_THREAD \*my_thread_ptr;</span></span>

```c
TX_THREAD *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr = tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
from that thread or an ISR that interrupted that thread.
Otherwise, this service was called
from an ISR when no thread was running when the
interrupt occurred. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1911">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1911">See Also</span></span>

- <span data-ttu-id="c6e75-1912">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1912">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-1913">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1913">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-1914">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1914">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-1915">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1915">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-1916">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1916">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1917">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1917">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1918">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1918">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-1919">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1919">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-1920">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-1920">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-1921">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-1921">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-1922">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-1922">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-1923">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-1923">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-1924">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1924">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-1925">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-1925">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-1926">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-1926">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-1927">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1927">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-1928">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-1928">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="c6e75-1929">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1929">tx_thread_info_get</span></span>

<span data-ttu-id="c6e75-1930">스레드에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1930">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1931">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1931">Prototype</span></span>

```c
UINT tx_thread_info_get(
    TX_THREAD *thread_ptr, 
    CHAR **name,
    UINT *state, 
    ULONG *run_count,
    UINT *priority,
    UINT *preemption_threshold,
    ULONG *time_slice,
    TX_THREAD **next_thread,
    TX_THREAD **suspended_thread);
```

### <a name="description"></a><span data-ttu-id="c6e75-1932">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1932">Description</span></span>

<span data-ttu-id="c6e75-1933">이 서비스는 지정된 스레드에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1933">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1934">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1934">Parameters</span></span>
- <span data-ttu-id="c6e75-1935">**thread_ptr** 스레드 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1935">**thread_ptr** Pointer to thread control block.</span></span>
- <span data-ttu-id="c6e75-1936">**name** 스레드 이름에 대한 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1936">**name** Pointer to destination for the pointer to the thread's name.</span></span>
- <span data-ttu-id="c6e75-1937">**state** 스레드의 현재 실행 상태 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1937">**state** Pointer to destination for the thread's current execution state.</span></span> <span data-ttu-id="c6e75-1938">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1938">Possible values are as follows.</span></span>
    - <span data-ttu-id="c6e75-1939">**TX_READY**(0x00)</span><span class="sxs-lookup"><span data-stu-id="c6e75-1939">**TX_READY** (0x00)</span></span>
    - <span data-ttu-id="c6e75-1940">**TX_COMPLETED**(0x01)</span><span class="sxs-lookup"><span data-stu-id="c6e75-1940">**TX_COMPLETED** (0x01)</span></span>
    - <span data-ttu-id="c6e75-1941">**TX_TERMINATED**(0x02)</span><span class="sxs-lookup"><span data-stu-id="c6e75-1941">**TX_TERMINATED** (0x02)</span></span>
    - <span data-ttu-id="c6e75-1942">**TX_SUSPENDED**(0x03)</span><span class="sxs-lookup"><span data-stu-id="c6e75-1942">**TX_SUSPENDED** (0x03)</span></span>
    - <span data-ttu-id="c6e75-1943">**TX_SLEEP**(0x04)</span><span class="sxs-lookup"><span data-stu-id="c6e75-1943">**TX_SLEEP** (0x04)</span></span>
    - <span data-ttu-id="c6e75-1944">**TX_QUEUE_SUSP**(0x05)</span><span class="sxs-lookup"><span data-stu-id="c6e75-1944">**TX_QUEUE_SUSP** (0x05)</span></span>
    - <span data-ttu-id="c6e75-1945">**TX_SEMAPHORE_SUSP**(0x06)</span><span class="sxs-lookup"><span data-stu-id="c6e75-1945">**TX_SEMAPHORE_SUSP** (0x06)</span></span>
    - <span data-ttu-id="c6e75-1946">**TX_EVENT_FLAG**(0x07)</span><span class="sxs-lookup"><span data-stu-id="c6e75-1946">**TX_EVENT_FLAG** (0x07)</span></span>
    - <span data-ttu-id="c6e75-1947">**TX_BLOCK_MEMORY**(0x08)</span><span class="sxs-lookup"><span data-stu-id="c6e75-1947">**TX_BLOCK_MEMORY** (0x08)</span></span>
    - <span data-ttu-id="c6e75-1948">**TX_BYTE_MEMORY**(0x09)</span><span class="sxs-lookup"><span data-stu-id="c6e75-1948">**TX_BYTE_MEMORY** (0x09)</span></span>
    - <span data-ttu-id="c6e75-1949">**TX_MUTEX_SUSP**(0x0D)</span><span class="sxs-lookup"><span data-stu-id="c6e75-1949">**TX_MUTEX_SUSP** (0x0D)</span></span>  

- <span data-ttu-id="c6e75-1950">**run_count** 스레드 실행 횟수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1950">**run_count** Pointer to destination for the thread's run count.</span></span>
- <span data-ttu-id="c6e75-1951">**priority** 스레드 우선 순위 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1951">**priority** Pointer to destination for the thread's priority.</span></span>
- <span data-ttu-id="c6e75-1952">**preemption_threshold** 스레드 선점 임계값 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1952">**preemption_threshold** Pointer to destination for the thread's preemption-threshold.</span></span>
<span data-ttu-id="c6e75-1953">**time_slice** 스레드 시간 조각 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1953">**time_slice** Pointer to destination for the thread's time-slice.</span></span>
<span data-ttu-id="c6e75-1954">**next_thread** 다음에 만들 스레드 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1954">**next_thread** Pointer to destination for next created thread pointer.</span></span>

<span data-ttu-id="c6e75-1955">**suspended_thread** 일시 중단 목록의 다음 스레드에 대한 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1955">**suspended_thread** Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-1956">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1956">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-1957">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-1957">Return Values</span></span>

- <span data-ttu-id="c6e75-1958">**TX_SUCCESS**(0x00) 스레드 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1958">**TX_SUCCESS** (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="c6e75-1959">**TX_THREAD_ERROR**(0x0E) 잘못된 스레드 제어 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1959">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-1960">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-1960">Allowed From</span></span>

<span data-ttu-id="c6e75-1961">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-1961">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-1962">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-1962">Preemption Possible</span></span>

<span data-ttu-id="c6e75-1963">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-1963">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-1964">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-1964">Example</span></span>

```c
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
thread "my_thread." */

status = tx_thread_info_get(&my_thread, &name,
    &state, &run_count,
    &priority, &preemption_threshold,
    &time_slice, &next_thread,&suspended_thread);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-1965">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-1965">See Also</span></span>

- <span data-ttu-id="c6e75-1966">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-1966">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-1967">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-1967">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-1968">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1968">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-1969">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1969">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-1970">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1970">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-1971">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1971">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-1972">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1972">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-1973">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1973">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-1974">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-1974">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-1975">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-1975">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-1976">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-1976">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-1977">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-1977">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-1978">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-1978">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-1979">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-1979">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-1980">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-1980">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-1981">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-1981">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-1982">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-1982">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="c6e75-1983">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-1983">tx_thread_performance_info_get</span></span>

<span data-ttu-id="c6e75-1984">스레드 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1984">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-1985">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-1985">Prototype</span></span>

```c
UINT tx_thread_performance_info_get(
    TX_THREAD *thread_ptr,
    LONG *resumptions, 
    ULONG *suspensions,
    ULONG *solicited_preemptions, 
    ULONG *interrupt_preemptions,
    ULONG *priority_inversions, 
    ULONG *time_slices,
    ULONG *relinquishes, 
    ULONG *timeouts, 
    ULONG *wait_aborts,
    TX_THREAD **last_preempted_by);
```

### <a name="description"></a><span data-ttu-id="c6e75-1986">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-1986">Description</span></span>

<span data-ttu-id="c6e75-1987">이 서비스는 지정된 스레드에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1987">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-1988">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 \***TX_THREAD_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1988">*The ThreadX library and application must be built with* ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-1989">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-1989">Parameters</span></span>
- <span data-ttu-id="c6e75-1990">**thread_ptr** 이전에 만든 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1990">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="c6e75-1991">**resumptions** 이 스레드 재개 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1991">**resumptions** Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="c6e75-1992">**suspensions** 이 스레드 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1992">**suspensions** Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="c6e75-1993">**solicited_preemptions** 이 스레드에서 수행한 ThreadX API 서비스 호출의 결과인 선점 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1993">**solicited_preemptions** Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="c6e75-1994">**interrupt_preemptions** 인터럽트 처리의 결과인 이 스레드 선점 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1994">**interrupt_preemptions** Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="c6e75-1995">**priority_inversions** 이 스레드 우선 순위 반전 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1995">**priority_inversions** Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="c6e75-1996">**time_slices** 이 스레드 시간 조각 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1996">**time_slices** Pointer to destination for the number of time-slices of this thread.</span></span>
- <span data-ttu-id="c6e75-1997">**relinquishes** 이 스레드에서 수행된 스레드 양도 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1997">**relinquishes** Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="c6e75-1998">**timeouts** 이 스레드의 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1998">**timeouts** Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="c6e75-1999">**wait_aborts** 이 스레드에서 수행된 대기 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-1999">**wait_aborts** Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="c6e75-2000">**last_preempted_by** 이 스레드를 마지막으로 선점한 스레드 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2000">**last_preempted_by** Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2001">매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2001">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2002">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2002">Return Values</span></span>

- <span data-ttu-id="c6e75-2003">**TX_SUCCESS**(0x00) 스레드 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2003">**TX_SUCCESS** (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="c6e75-2004">**TX_PTR_ERROR**(0x03) 잘못된 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2004">**TX_PTR_ERROR** (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="c6e75-2005">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2005">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2006">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2006">Allowed From</span></span>

<span data-ttu-id="c6e75-2007">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2007">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2008">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2008">Example</span></span>

```c
TX_THREAD my_thread;
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
TX_THREAD *last_preempted_by;

/* Retrieve performance information on the previously created
thread. */

status = tx_thread_performance_info_get(&my_thread, &resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices,
    &relinquishes, &timeouts,
    &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2009">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2009">See Also</span></span>

- <span data-ttu-id="c6e75-2010">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2010">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-2011">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2011">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2012">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2012">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2013">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2013">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2014">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2014">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2015">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2015">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-2016">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2016">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-2017">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2017">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-2018">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2018">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-2019">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2019">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-2020">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2020">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-2021">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2021">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-2022">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2022">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-2023">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2023">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-2024">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2024">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-2025">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2025">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-2026">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2026">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="c6e75-2027">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2027">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="c6e75-2028">스레드 시스템 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2028">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2029">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2029">Prototype</span></span>

```c
UINT tx_thread_performance_system_info_get(
    ULONG *resumptions,
    ULONG *suspensions, 
    ULONG *solicited_preemptions,
    ULONG *interrupt_preemptions, 
    ULONG *priority_inversions,
    ULONG *time_slices, 
    ULONG *relinquishes, 
    ULONG *timeouts,
    ULONG *wait_aborts, 
    ULONG *non_idle_returns,
    ULONG *idle_returns);
```

### <a name="description"></a><span data-ttu-id="c6e75-2030">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2030">Description</span></span>

<span data-ttu-id="c6e75-2031">이 서비스는 시스템의 모든 스레드에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2031">This service retrieves performance information about all the threads in the system.</span></span>

<span data-ttu-id="c6e75-2032">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된</span><span class="sxs-lookup"><span data-stu-id="c6e75-2032">*The ThreadX library and application must be built with*</span></span>

<span data-ttu-id="c6e75-2033">\***TX_THREAD_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2033">***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2034">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2034">Parameters</span></span>

- <span data-ttu-id="c6e75-2035">**resumptions** 총 스레드 재개 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2035">**resumptions** Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="c6e75-2036">**suspensions** 총 스레드 일시 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2036">**suspensions** Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="c6e75-2037">**solicited_preemptions** ThreadX API 서비스를 호출하는 스레드의 결과인 총 스레드 선점 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2037">**solicited_preemptions** Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="c6e75-2038">**interrupt_preemptions** 인터럽트 처리 결과인 총 스레드 선점 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2038">**interrupt_preemptions** Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="c6e75-2039">**priority_inversions** 총 스레드 우선 순위 반전 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2039">**priority_inversions** Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="c6e75-2040">**time_slices** 총 스레드 시간 조각 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2040">**time_slices** Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="c6e75-2041">**relinquishes** 총 스레드 양도 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2041">**relinquishes** Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="c6e75-2042">**timeouts** 총 스레드 일시 중단 시간 제한 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2042">**timeouts** Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="c6e75-2043">**wait_aborts** 총 스레드 대기 중단 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2043">**wait_aborts** Pointer to destination for the total number of thread wait aborts.</span></span>
- <span data-ttu-id="c6e75-2044">**non_idle_returns** 다른 스레드를 실행할 준비가 되면 스레드가 시스템으로 반환되는 횟수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2044">**non_idle_returns** Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span>
- <span data-ttu-id="c6e75-2045">**idle_returns** 실행할 준비가 된 스레드가 없는 경우(유휴 시스템) 스레드가 시스템으로 반환되는 횟수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2045">**idle_returns** Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2046">매개 변수에 **TX_NULL** 을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2046">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2047">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2047">Return Values</span></span>

- <span data-ttu-id="c6e75-2048">**TX_SUCCESS**(0x00) 스레드 시스템 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2048">**TX_SUCCESS** (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="c6e75-2049">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2049">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2050">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2050">Allowed From</span></span>

<span data-ttu-id="c6e75-2051">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2051">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2052">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2052">Example</span></span>

```c
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
ULONG non_idle_returns;
ULONG idle_returns;

/* Retrieve performance information on all previously created
thread. */

status = tx_thread_performance_system_info_get(&resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices, &relinquishes,
    &timeouts, &wait_aborts, &non_idle_returns,
    &idle_returns);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2053">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2053">See Also</span></span>

- <span data-ttu-id="c6e75-2054">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2054">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-2055">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2055">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2056">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2056">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2057">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2057">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2058">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2058">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2059">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2059">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2060">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2060">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-2061">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2061">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-2062">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2062">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-2063">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2063">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-2064">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2064">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-2065">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2065">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-2066">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2066">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-2067">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2067">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-2068">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2068">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-2069">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2069">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-2070">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2070">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="c6e75-2071">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2071">tx_thread_preemption_change</span></span>

<span data-ttu-id="c6e75-2072">애플리케이션 스레드의 선점 임계값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2072">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2073">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2073">Prototype</span></span>

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a><span data-ttu-id="c6e75-2074">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2074">Description</span></span>

<span data-ttu-id="c6e75-2075">이 서비스는 지정된 스레드의 선점 임계값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2075">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="c6e75-2076">선점 임계값을 사용하면 선점 임계값 이하인 스레드에서 지정된 스레드를 선점하는 것을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2076">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

>[!NOTE]
> <span data-ttu-id="c6e75-2077">선점 임계값을 사용하면 지정된 스레드에 시간 조각화를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2077">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2078">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2078">Parameters</span></span>
- <span data-ttu-id="c6e75-2079">**thread_ptr** 이전에 만든 애플리케이션 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2079">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="c6e75-2080">**new_threshold** 새 선점 임계값 우선 순위 수준입니다(0-(TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="c6e75-2080">**new_threshold** New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="c6e75-2081">**old_threshold** 이전 선점 임계값을 반환할 위치에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2081">**old_threshold** Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2082">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2082">Return Values</span></span>

- <span data-ttu-id="c6e75-2083">**TX_SUCCESS**(0x00) 선점 임계값 변경에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2083">**TX_SUCCESS** (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="c6e75-2084">**TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2084">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="c6e75-2085">**TX_THRESH_ERROR**(0x18) 지정된 새 선점 임계값이 잘못된 스레드 우선 순위((0-(**TX_MAX_PRIORITIES**-1) 이외의 값)이거나 현재 스레드 우선 순위보다 높습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2085">**TX_THRESH_ERROR** (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (**TX_MAX_PRIORITIES**-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="c6e75-2086">**TX_PTR_ERROR**(0x03) 이전 preemptionthreshold 스토리지 위치에 대한 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2086">**TX_PTR_ERROR** (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="c6e75-2087">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2087">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2088">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2088">Allowed From</span></span>

<span data-ttu-id="c6e75-2089">스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="c6e75-2089">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2090">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2090">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2091">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2091">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2092">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2092">Example</span></span>

```c
TX_THREAD my_thread;
UINT my_old_threshold;
UINT status;

/* Disable all preemption of the specified thread. The
current preemption-threshold is returned in
"my_old_threshold". Assume that "my_thread" has
already been created. */

status = tx_thread_preemption_change(&my_thread,
    0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
non-preemptable by another thread. Note that ISRs are
not prevented by preemption disabling. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2093">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2093">See Also</span></span>

- <span data-ttu-id="c6e75-2094">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2094">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-2095">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2095">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2096">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2096">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2097">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2097">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2098">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2098">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2099">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2099">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2100">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2100">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-2101">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2101">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-2102">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2102">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-2103">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2103">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-2104">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2104">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-2105">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2105">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-2106">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2106">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-2107">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2107">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-2108">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2108">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-2109">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2109">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-2110">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2110">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="c6e75-2111">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2111">tx_thread_priority_change</span></span>

<span data-ttu-id="c6e75-2112">애플리케이션 스레드의 우선 순위를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2112">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2113">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2113">Prototype</span></span>

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a><span data-ttu-id="c6e75-2114">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2114">Description</span></span>

<span data-ttu-id="c6e75-2115">이 서비스는 지정된 스레드의 우선 순위를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2115">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="c6e75-2116">유효한 우선 순위 범위는 0-(TX_MAX_PRIORITES-1)입니다. 여기서 0은 가장 높은 우선 순위 수준을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2116">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-2117">지정된 스레드의 선점 임계값은 새 우선 순위로 자동 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2117">\*The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="c6e75-2118">새 임계값을 사용하려면 이 호출 후 ***tx_thread_preemption_change*** 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2118">If a new threshold is desired, the \***tx_thread_preemption_change** _ service must be used after this call._</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2119">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2119">Parameters</span></span>

- <span data-ttu-id="c6e75-2120">**thread_ptr** 이전에 만든 애플리케이션 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2120">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="c6e75-2121">**new_priority** 새 스레드 우선 순위 수준(0-(TX_MAX_PRIORITIES-1))입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2121">**new_priority** New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="c6e75-2122">**old_priority** 스레드의 이전 우선 순위를 반환할 위치에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2122">**old_priority** Pointer to a location to return the thread's previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2123">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2123">Return Values</span></span>

- <span data-ttu-id="c6e75-2124">**TX_SUCCESS**(0x00) 우선 순위 변경에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2124">**TX_SUCCESS** (0x00) Successful priority change.</span></span>
- <span data-ttu-id="c6e75-2125">**TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2125">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="c6e75-2126">**TX_PRIORITY_ERROR**(0x0F) 지정된 새 우선 순위가 잘못되었습니다((0-(TX_MAX_PRIORITIES-1) 이외의 값).</span><span class="sxs-lookup"><span data-stu-id="c6e75-2126">**TX_PRIORITY_ERROR** (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="c6e75-2127">**TX_PTR_ERROR**(0x03) 이전 우선 순위 스토리지 위치에 대한 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2127">**TX_PTR_ERROR** (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="c6e75-2128">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2128">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2129">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2129">Allowed From</span></span>

<span data-ttu-id="c6e75-2130">스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="c6e75-2130">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2131">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2131">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2132">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2132">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2133">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2133">Example</span></span>

```c
TX_THREAD my_thread;
UINT my_old_priority;
UINT status;

/* Change the thread represented by "my_thread" to priority
0. */

status = tx_thread_priority_change(&my_thread,
    0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
now at the highest priority level in the system. */
```
### <a name="see-also"></a><span data-ttu-id="c6e75-2134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2134">See Also</span></span>

- <span data-ttu-id="c6e75-2135">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2135">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-2136">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2136">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2137">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2137">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2138">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2138">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2139">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2139">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2140">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2140">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2141">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2141">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-2142">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2142">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-2143">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2143">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-2144">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2144">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-2145">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2145">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-2146">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2146">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-2147">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2147">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-2148">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2148">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-2149">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2149">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-2150">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2150">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-2151">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2151">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="c6e75-2152">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2152">tx_thread_relinquish</span></span>

<span data-ttu-id="c6e75-2153">다른 애플리케이션 스레드로 제어를 양도합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2153">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2154">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2154">Prototype</span></span>

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a><span data-ttu-id="c6e75-2155">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2155">Description</span></span>

<span data-ttu-id="c6e75-2156">이 서비스는 우선 순위가 동일하거나 더 높은, 실행 준비가 된 다른 스레드로 프로세서 제어를 양도합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2156">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2157">이 서비스는 우선 순위가 동일한 스레드로 제어를 양도할 뿐만 아니라, 현재 스레드의 선점 임계값 설정으로 실행이 방지된 우선 순위가 가장 높은 스레드로 제어를 양도하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2157">*In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2158">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2158">Parameters</span></span>

<span data-ttu-id="c6e75-2159">None</span><span class="sxs-lookup"><span data-stu-id="c6e75-2159">None</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2160">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2160">Return Values</span></span>

<span data-ttu-id="c6e75-2161">None</span><span class="sxs-lookup"><span data-stu-id="c6e75-2161">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2162">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2162">Allowed From</span></span>

<span data-ttu-id="c6e75-2163">스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-2163">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2164">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2164">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2165">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2165">Yes</span></span>

### <a name="examples"></a><span data-ttu-id="c6e75-2166">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2166">Examples</span></span>

```c
ULONG run_counter_1 = 0;
ULONG run_counter_2 = 0;

/* Example of two threads relinquishing control to
each other in an infinite loop. Assume that
both of these threads are ready and have the same
priority. The run counters will always stay within one
of each other. */

VOID my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{

    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2167">See Also</span></span>

- <span data-ttu-id="c6e75-2168">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2168">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-2169">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2169">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2170">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2170">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2171">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2171">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2172">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2172">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2173">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2173">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2174">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2174">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-2175">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2175">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-2176">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2176">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-2177">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2177">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-2178">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2178">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-2179">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2179">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-2180">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2180">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-2181">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2181">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-2182">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2182">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-2183">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2183">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-2184">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2184">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="c6e75-2185">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2185">tx_thread_reset</span></span>

<span data-ttu-id="c6e75-2186">스레드를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2186">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2187">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2187">Prototype</span></span>

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-2188">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2188">Description</span></span>

<span data-ttu-id="c6e75-2189">이 서비스는 지정된 스레드가 스레드를 만들 때 정의한 진입점에서 실행되도록 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2189">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="c6e75-2190">다시 설정하려면 스레드가 **TX_COMPLETED** 또는 **TX_TERMINATED** 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2190">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-2191">스레드를 다시 실행하려면 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2191">*The thread must be resumed for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2192">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2192">Parameters</span></span>

- <span data-ttu-id="c6e75-2193">**thread_ptr** 이전에 만든 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2193">**thread_ptr** Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2194">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2194">Return Values</span></span>

- <span data-ttu-id="c6e75-2195">**TX_SUCCESS**(0x00) 스레드를 다시 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2195">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="c6e75-2196">**TX_NOT_DONE**(0x20) 지정된 스레드가 **TX_COMPLETED** 또는 **TX_TERMINATED** 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2196">**TX_NOT_DONE** (0x20) Specified thread is not in a **TX_COMPLETED** or **TX_TERMINATED** state.</span></span>
- <span data-ttu-id="c6e75-2197">**TX_THREAD_ERROR**(0x0E) 잘못된 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2197">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="c6e75-2198">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2198">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2199">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2199">Allowed From</span></span>

<span data-ttu-id="c6e75-2200">스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-2200">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2201">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2201">Example</span></span>

<span data-ttu-id="c6e75-2202">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="c6e75-2202">TX_THREAD my_thread;</span></span>

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2203">See Also</span></span>

- <span data-ttu-id="c6e75-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2204">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2205">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2207">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2210">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2210">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="c6e75-2211">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2211">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-2212">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2212">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-2213">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2213">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2214">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="c6e75-2221">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2221">tx_thread_resume</span></span>

<span data-ttu-id="c6e75-2222">일시 중단된 애플리케이션 스레드를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2222">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2223">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2223">Prototype</span></span>

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-2224">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2224">Description</span></span>

<span data-ttu-id="c6e75-2225">이 서비스는 이전에 ***tx_thread_suspend*** 호출로 일시 중단된 스레드의 실행을 다시 시작하거나 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2225">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="c6e75-2226">이 서비스는 자동 시작 없이 생성된 스레드도 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2226">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2227">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2227">Parameters</span></span>

- <span data-ttu-id="c6e75-2228">**thread_ptr** 일시 중단된 애플리케이션 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2228">**thread_ptr** Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2229">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2229">Return Values</span></span>

- <span data-ttu-id="c6e75-2230">**TX_SUCCESS**(0x00) 스레드를 다시 시작하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2230">**TX_SUCCESS** (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="c6e75-2231">**TX_SUSPEND_LIFTED**(0x19) 이전에 설정한 지연된 일시 중단이 해제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2231">**TX_SUSPEND_LIFTED** (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="c6e75-2232">**TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2232">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="c6e75-2233">**TX_RESUME_ERROR**(0x12) 지정된 스레드가 일시 중단되지 않았거나 이전에 **_tx_thread_suspend_** 이외의 서비스를 통해 일시 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2233">**TX_RESUME_ERROR** (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2234">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2234">Allowed From</span></span>

<span data-ttu-id="c6e75-2235">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2235">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2236">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2236">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2237">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2237">Yes</span></span>

<span data-ttu-id="c6e75-2238">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="c6e75-2238">TX_THREAD my_thread;</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2239">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2239">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2240">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2240">See Also</span></span>

- <span data-ttu-id="c6e75-2241">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2241">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-2242">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2242">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2243">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2243">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2244">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2244">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2245">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2245">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2246">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2246">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2247">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2247">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-2248">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2248">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-2249">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2249">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-2250">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2250">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-2251">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2251">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-2252">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2252">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-2253">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2253">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-2254">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2254">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-2255">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2255">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-2256">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2256">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-2257">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2257">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="c6e75-2258">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2258">tx_thread_sleep</span></span>

<span data-ttu-id="c6e75-2259">지정된 시간 동안 현재 스레드 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2259">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2260">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2260">Prototype</span></span>

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a><span data-ttu-id="c6e75-2261">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2261">Description</span></span>

<span data-ttu-id="c6e75-2262">이 서비스는 지정된 타이머 틱 수 기간 동안 호출 스레드가 일시 중단되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2262">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="c6e75-2263">타이머 틱과 연결된 실제 시간의 양은 애플리케이션마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2263">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="c6e75-2264">이 서비스는 애플리케이션 스레드에서만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2264">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2265">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2265">Parameters</span></span>

- <span data-ttu-id="c6e75-2266">**timer_ticks** 호출하는 애플리케이션 스레드를 일시 중단할 타이머 틱 수이며, 범위는 0-0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2266">**timer_ticks** The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="c6e75-2267">0을 지정하면 서비스에서 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2267">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2268">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2268">Return Values</span></span>

- <span data-ttu-id="c6e75-2269">**TX_SUCCESS**(0x00) 스레드 일시 중지에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2269">**TX_SUCCESS** (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="c6e75-2270">**TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2270">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="c6e75-2271">**TX_CALLER_ERROR**(0x13) 서비스가 비스레드에서 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2271">**TX_CALLER_ERROR** (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2272">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2272">Allowed From</span></span>

<span data-ttu-id="c6e75-2273">스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2274">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2274">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2275">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2276">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2276">Example</span></span>

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2277">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2277">See Also</span></span>

- <span data-ttu-id="c6e75-2278">tx_thread_create, tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2278">tx_thread_create, tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2279">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2279">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2280">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2280">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2281">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2281">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2282">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2282">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2283">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2283">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-2284">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2284">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-2285">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2285">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-2286">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2286">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2287">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2288">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-2289">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2289">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-2290">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2290">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-2291">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2291">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-2292">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2292">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-2293">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2293">tx_thread_wait_abort</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="c6e75-2294">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2294">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="c6e75-2295">스레드 스택 오류 알림 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2295">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2296">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2296">Prototype</span></span>

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a><span data-ttu-id="c6e75-2297">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2297">Description</span></span>

<span data-ttu-id="c6e75-2298">이 서비스는 스레드 스택 오류 처리를 위한 알림 콜백 함수를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2298">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="c6e75-2299">ThreadX가 실행 중에 스레드 스택 오류를 검색하면 오류를 처리하도록 이 알림 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2299">When ThreadX detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="c6e75-2300">오류 처리는 전적으로 해당 애플리케이션에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2300">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="c6e75-2301">위반 스레드 일시 중단부터 전체 시스템 초기화까지 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2301">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-2302">ThreadX 라이브러리는 이 서비스가 성능 정보를 반환하도록 정의된 **TX_ENABLE_STACK_CHECKING** 을 사용하여 빌드되어야 합니다. </span><span class="sxs-lookup"><span data-stu-id="c6e75-2302">*The ThreadX library must be built with* **TX_ENABLE_STACK_CHECKING** *defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2303">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2303">Parameters</span></span>
- <span data-ttu-id="c6e75-2304">**error_handler** 애플리케이션의 스택 오류를 처리하는 함수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2304">**error_handler** Pointer to application's stack error handling function.</span></span> <span data-ttu-id="c6e75-2305">이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2305">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2306">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2306">Return Values</span></span>

- <span data-ttu-id="c6e75-2307">**TX_SUCCESS**(0x00) 스레드를 다시 설정하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2307">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="c6e75-2308">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2308">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2309">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2309">Allowed From</span></span>

<span data-ttu-id="c6e75-2310">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2310">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2311">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2311">Example</span></span>

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2312">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2312">See Also</span></span>

- <span data-ttu-id="c6e75-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2313">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2314">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2316">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2319">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2319">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="c6e75-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-2323">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2323">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-2324">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2324">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-2325">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2325">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="c6e75-2330">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2330">tx_thread_suspend</span></span>

<span data-ttu-id="c6e75-2331">애플리케이션 스레드를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2331">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2332">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2332">Prototype</span></span>

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-2333">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2333">Description</span></span>

<span data-ttu-id="c6e75-2334">이 서비스는 지정된 애플리케이션 스레드를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2334">This service suspends the specified application thread.</span></span> <span data-ttu-id="c6e75-2335">스레드가 이 서비스를 호출하여 자체적으로 일시 중단할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2335">A thread may call this service to suspend itself.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2336">지정된 스레드가 다른 이유로 이미 일시 중단되어 있는 경우 이전 일시 중단이 해제될 때까지 이 일시 중단은 내부적으로 보류됩니다. 이전 일시 중단이 해제되면 지정된 스레드에 대한 무조건 일시 중단이 수행됩니다. 향후의 무조건 일시 중단 요청은 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2336">*If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted. When that happens, this unconditional suspension of the specified thread is performed. Further unconditional suspension requests have no effect.*</span></span>

<span data-ttu-id="c6e75-2337">일시 중단된 후 스레드를 다시 실행하려면 ***tx_thread_resume*** 을 통해 스레드를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2337">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2338">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2338">Parameters</span></span>

- <span data-ttu-id="c6e75-2339">**thread_ptr** 애플리케이션 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2339">**thread_ptr** Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2340">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2340">Return Values</span></span>

- <span data-ttu-id="c6e75-2341">**TX_SUCCESS**(0x00) 스레드 일시 중단에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2341">**TX_SUCCESS** (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="c6e75-2342">**TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2342">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="c6e75-2343">**TX_SUSPEND_ERROR**(0x14) 지정된 스레드가 종료 상태 또는 완료 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2343">**TX_SUSPEND_ERROR** (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="c6e75-2344">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2344">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2345">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2345">Allowed From</span></span>

<span data-ttu-id="c6e75-2346">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2346">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2347">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2347">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2348">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2348">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2349">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2349">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2350">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2350">See Also</span></span>

- <span data-ttu-id="c6e75-2351">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2351">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-2352">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2352">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2353">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2353">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2354">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2354">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2355">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2355">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2356">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2356">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2357">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2357">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-2358">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2358">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-2359">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2359">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-2360">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2360">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-2361">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2361">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-2362">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2362">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-2363">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2363">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-2364">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2364">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-2365">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2365">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-2366">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2366">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-2367">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2367">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="c6e75-2368">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2368">tx_thread_terminate</span></span>

<span data-ttu-id="c6e75-2369">애플리케이션 스레드를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2369">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2370">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2370">Prototype</span></span>

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="c6e75-2371">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2371">Description</span></span>

<span data-ttu-id="c6e75-2372">이 서비스는 스레드가 일시 중단되었는지 여부에 관계없이 지정된 애플리케이션 스레드를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2372">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="c6e75-2373">스레드가 이 서비스를 호출하여 자체적으로 종료할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2373">A thread may call this service to terminate itself.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2374">애플리케이션은 스레드가 종료에 적합한 상태인지 확인해야 합니다. 예를 들어 중요한 애플리케이션을 처리하는 중이거나 이러한 처리가 알 수 없는 상태로 남아 있을 수 있는 다른 미들웨어 구성 요소 내에서는 스레드를 종료하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2374">*It is the application's responsibility to ensure that the thread is in a state suitable for termination. For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-2375">종료된 후 스레드를 다시 실행하려면 스레드를 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2375">*After being terminated, the thread must be reset for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2376">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2376">Parameters</span></span>

- <span data-ttu-id="c6e75-2377">**thread_ptr** 애플리케이션 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2377">**thread_ptr** Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2378">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2378">Return Values</span></span>
- <span data-ttu-id="c6e75-2379">**TX_SUCCESS**(0x00) 스레드를 종료하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2379">**TX_SUCCESS** (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="c6e75-2380">**TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2380">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="c6e75-2381">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2381">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2382">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2382">Allowed From</span></span>

<span data-ttu-id="c6e75-2383">스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="c6e75-2383">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2384">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2384">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2385">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2385">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2386">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2386">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2387">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2387">See Also</span></span>

- <span data-ttu-id="c6e75-2388">tx_thread_create tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2388">tx_thread_create tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2389">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2389">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2390">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2390">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2391">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2391">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2392">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2392">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2393">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2393">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-2394">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2394">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-2395">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2395">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-2396">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2396">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-2397">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2397">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-2398">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2398">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-2399">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2399">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-2400">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2400">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-2401">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2401">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-2402">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2402">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="c6e75-2403">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2403">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="c6e75-2404">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2404">tx_thread_time_slice_change</span></span>

<span data-ttu-id="c6e75-2405">애플리케이션 스레드의 시간 조각을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2405">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2406">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2406">Prototype</span></span>

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a><span data-ttu-id="c6e75-2407">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2407">Description</span></span>

<span data-ttu-id="c6e75-2408">이 서비스는 지정된 애플리케이션 스레드의 시간 조각을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2408">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="c6e75-2409">스레드에 대해 시간 조각을 선택하면 우선 순위가 같거나 더 높은 다른 스레드를 실행하기 전에 지정된 타이머 틱 수 이하로 스레드가 실행되도록 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2409">Selecting a time-slice for a thread insures that it won't execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2410">선점 임계값을 사용하면 지정된 스레드에 시간 조각화를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2410">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2411">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2411">Parameters</span></span>

- <span data-ttu-id="c6e75-2412">**thread_ptr** 애플리케이션 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2412">**thread_ptr** Pointer to application thread.</span></span>
- <span data-ttu-id="c6e75-2413">**new_time_slice** 새 시간 조각 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2413">**new_time_slice** New time slice value.</span></span> <span data-ttu-id="c6e75-2414">유효한 값에는 TX_NO_TIME_SLICE와 숫자 값 1부터 0xFFFFFFFF까지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2414">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="c6e75-2415">**old_time_slice** 지정된 스레드의 이전 timeslice 값 저장 위치에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2415">**old_time_slice** Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2416">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2416">Return Values</span></span>

- <span data-ttu-id="c6e75-2417">**TX_SUCCESS**(0x00) 시간 조각 변경에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2417">**TX_SUCCESS** (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="c6e75-2418">**TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2418">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="c6e75-2419">**TX_PTR_ERROR**(0x03) 이전 시간 조각 스토리지 위치에 대한 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2419">**TX_PTR_ERROR** (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="c6e75-2420">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2420">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2421">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2421">Allowed From</span></span>

<span data-ttu-id="c6e75-2422">스레드, 타이머</span><span class="sxs-lookup"><span data-stu-id="c6e75-2422">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2423">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2423">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2424">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2424">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2425">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2425">Example</span></span>

```c
TX_THREAD my_thread;
ULONG my_old_time_slice;
UINT status;

/* Change the time-slice of the thread associated with
"my_thread" to 20. This will mean that "my_thread"
can only run for 20 timer-ticks consecutively before
other threads of equal or higher priority get a chance
to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
    &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
has been changed to 20 and the previous time-slice is
in "my_old_time_slice." */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2426">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2426">See Also</span></span>

- <span data-ttu-id="c6e75-2427">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2427">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-2428">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2428">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2429">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2429">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2430">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2430">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2431">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2431">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2432">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2432">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2433">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2433">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-2434">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2434">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-2435">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2435">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-2436">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2436">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-2437">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2437">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-2438">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2438">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-2439">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2439">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-2440">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2440">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-2441">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2441">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-2442">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2442">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-2443">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2443">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="c6e75-2444">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="c6e75-2444">tx_thread_wait_abort</span></span>

<span data-ttu-id="c6e75-2445">지정된 스레드의 일시 중단을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2445">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2446">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2446">Prototype</span></span>

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-2447">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2447">Description</span></span>

<span data-ttu-id="c6e75-2448">이 서비스는 지정된 스레드의 일시 중지 또는 다른 개체 일시 중단을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2448">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="c6e75-2449">대기가 중단되면 스레드가 대기하고 있던 서비스에서 **TX_WAIT_ABORTED** 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2449">If the wait is aborted, a **TX_WAIT_ABORTED** value is returned from the service that the thread was waiting on.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2450">이 서비스는 *tx_thread_suspend* 서비스에서 수행한 명시적 일시 중단은 해제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2450">*This service does not release explicit suspension that is made by the tx_thread_suspend service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2451">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2451">Parameters</span></span>

- <span data-ttu-id="c6e75-2452">**thread_ptr** 이전에 만든 애플리케이션 스레드에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2452">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2453">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2453">Return Values</span></span>

- <span data-ttu-id="c6e75-2454">**TX_SUCCESS**(0x00) 스레드 대기 중단에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2454">**TX_SUCCESS** (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="c6e75-2455">**TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2455">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="c6e75-2456">**TX_WAIT_ABORT_ERROR**(0x1B) 지정된 스레드가 대기 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2456">**TX_WAIT_ABORT_ERROR** (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2457">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2457">Allowed From</span></span>

<span data-ttu-id="c6e75-2458">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2458">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2459">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2459">Preemption Possible</span></span>
<span data-ttu-id="c6e75-2460">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2460">Yes</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2461">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2461">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2462">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2462">See Also</span></span>

- <span data-ttu-id="c6e75-2463">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2463">tx_thread_create</span></span>
- <span data-ttu-id="c6e75-2464">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2464">tx_thread_delete</span></span>
- <span data-ttu-id="c6e75-2465">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2465">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="c6e75-2466">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2466">tx_thread_identify</span></span>
- <span data-ttu-id="c6e75-2467">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2467">tx_thread_info_get</span></span>
- <span data-ttu-id="c6e75-2468">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2468">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2469">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2469">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="c6e75-2470">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2470">tx_thread_preemption_change</span></span>
- <span data-ttu-id="c6e75-2471">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2471">tx_thread_priority_change</span></span>
- <span data-ttu-id="c6e75-2472">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="c6e75-2472">tx_thread_relinquish</span></span>
- <span data-ttu-id="c6e75-2473">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="c6e75-2473">tx_thread_reset</span></span>
- <span data-ttu-id="c6e75-2474">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="c6e75-2474">tx_thread_resume</span></span>
- <span data-ttu-id="c6e75-2475">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="c6e75-2475">tx_thread_sleep</span></span>
- <span data-ttu-id="c6e75-2476">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="c6e75-2476">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="c6e75-2477">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="c6e75-2477">tx_thread_suspend</span></span>
- <span data-ttu-id="c6e75-2478">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2478">tx_thread_terminate</span></span>
- <span data-ttu-id="c6e75-2479">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2479">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="c6e75-2480">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2480">tx_time_get</span></span>

<span data-ttu-id="c6e75-2481">현재 시간을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2481">Retrieves the current time</span></span>

<span data-ttu-id="c6e75-2482">애플리케이션 타이머</span><span class="sxs-lookup"><span data-stu-id="c6e75-2482">Application Timers</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2483">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2483">Prototype</span></span>

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a><span data-ttu-id="c6e75-2484">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2484">Description</span></span>

<span data-ttu-id="c6e75-2485">이 서비스는 내부 시스템 클록의 콘텐츠를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2485">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="c6e75-2486">각 타이머 틱은 내부 시스템 클록을 1씩 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2486">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="c6e75-2487">시스템 클록은 초기화 중에 0으로 설정되며 ***tx_time_set*** 서비스를 통해 특정 값으로 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2487">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2488">각 타이머 틱이 나타내는 실제 시간은 애플리케이션마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2488">*The actual time each timer-tick represents is application specific.*</span></span>

<span data-ttu-id="c6e75-2489">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="c6e75-2489">**Parameters**</span></span>

<span data-ttu-id="c6e75-2490">None</span><span class="sxs-lookup"><span data-stu-id="c6e75-2490">None</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2491">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2491">Return Values</span></span>

- <span data-ttu-id="c6e75-2492">**system clock ticks** 원하는 대로 실행할 수 있는 내부 시스템 클록 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2492">**system clock ticks** Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2493">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2493">Allowed From</span></span>

<span data-ttu-id="c6e75-2494">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2494">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2495">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2495">Preemption Possible</span></span>
<span data-ttu-id="c6e75-2496">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2496">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2497">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2497">Example</span></span>

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2498">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2498">See Also</span></span>

- <span data-ttu-id="c6e75-2499">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="c6e75-2499">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="c6e75-2500">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="c6e75-2500">tx_time_set</span></span>

<span data-ttu-id="c6e75-2501">현재 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2501">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2502">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2502">Prototype</span></span>

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a><span data-ttu-id="c6e75-2503">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2503">Description</span></span>

<span data-ttu-id="c6e75-2504">이 서비스는 내부 시스템 클록을 지정된 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2504">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="c6e75-2505">각 타이머 틱은 내부 시스템 클록을 1씩 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2505">Each timer-tick increases the internal system clock by one.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2506">각 타이머 틱이 나타내는 실제 시간은 애플리케이션마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2506">*The actual time each timer-tick represents is application specific.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2507">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2507">Parameters</span></span>

- <span data-ttu-id="c6e75-2508">**new_time** 시스템 클록에 배치할 새 시간입니다. 유효한 값 범위는 0-0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2508">**new_time** New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2509">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2509">Return Values</span></span>

<span data-ttu-id="c6e75-2510">None</span><span class="sxs-lookup"><span data-stu-id="c6e75-2510">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2511">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2511">Allowed From</span></span>

<span data-ttu-id="c6e75-2512">스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2512">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2513">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2513">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2514">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2514">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2515">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2515">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2516">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2516">See Also</span></span>

- <span data-ttu-id="c6e75-2517">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2517">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="c6e75-2518">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2518">tx_timer_activate</span></span>

<span data-ttu-id="c6e75-2519">애플리케이션 타이머를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2519">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2520">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2520">Prototype</span></span>

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-2521">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2521">Description</span></span>

<span data-ttu-id="c6e75-2522">이 서비스는 지정된 애플리케이션 타이머를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2522">This service activates the specified application timer.</span></span> <span data-ttu-id="c6e75-2523">동시에 만료되는 여러 타이머의 만료 루틴은 활성화된 순서대로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2523">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2524">만료된 일회성 타이머를 다시 활성화하려면 먼저 ***tx_timer_change** __*를 통해 타이머를 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2524">*An expired one-shot timer must be reset via* ***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2525">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2525">Parameters</span></span>

- <span data-ttu-id="c6e75-2526">**timer_ptr** 이전에 만든 애플리케이션 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2526">**timer_ptr** Pointer to a previously created application timer.</span></span>

<span data-ttu-id="c6e75-2527">**반환 값**</span><span class="sxs-lookup"><span data-stu-id="c6e75-2527">**Return Values**</span></span>

- <span data-ttu-id="c6e75-2528">**TX_SUCCESS**(0x00) 애플리케이션 타이머 활성화에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2528">**TX_SUCCESS** (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="c6e75-2529">**TX_TIMER_ERROR**(0x15) 잘못된 애플리케이션 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2529">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="c6e75-2530">**TX_ACTIVATE_ERROR**(0x17) 타이머가 이미 활성이거나 이미 만료된 일회성 타이머입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2530">**TX_ACTIVATE_ERROR** (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2531">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2531">Allowed From</span></span>

<span data-ttu-id="c6e75-2532">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2532">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2533">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2533">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2534">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2534">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2535">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2535">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2536">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2536">See Also</span></span>

- <span data-ttu-id="c6e75-2537">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2537">tx_timer_change</span></span>
- <span data-ttu-id="c6e75-2538">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2538">tx_timer_create</span></span>
- <span data-ttu-id="c6e75-2539">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2539">tx_timer_deactivate</span></span>
- <span data-ttu-id="c6e75-2540">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2540">tx_timer_delete</span></span>
- <span data-ttu-id="c6e75-2541">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2541">tx_timer_info_get</span></span>
- <span data-ttu-id="c6e75-2542">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2542">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2543">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2543">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="c6e75-2544">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2544">tx_timer_change</span></span>

<span data-ttu-id="c6e75-2545">애플리케이션 타이머를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2545">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2546">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2546">Prototype</span></span>

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a><span data-ttu-id="c6e75-2547">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2547">Description</span></span>

<span data-ttu-id="c6e75-2548">이 서비스는 지정된 애플리케이션 타이머의 만료 특성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2548">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="c6e75-2549">이 서비스를 호출하기 전에 타이머를 비활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2549">The timer must be deactivated prior to calling this service.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2550">타이머를 다시 시작하려면 이 서비스 다음에 ***tx_timer_activate** _ _*서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2550">*A call to the* ***tx_timer_activate** _ _service is required after this service in order to start the timer again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2551">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2551">Parameters</span></span>

- <span data-ttu-id="c6e75-2552">**timer_ptr** 타이머 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2552">**timer_ptr** Pointer to a timer control block.</span></span>
- <span data-ttu-id="c6e75-2553">**initial_ticks** 타이머 만료에 사용되는 초기 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2553">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="c6e75-2554">유효한 값 범위는 1-0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2554">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="c6e75-2555">**reschedule_ticks** 첫 번째 이후의 모든 타이머 만료에 사용되는 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2555">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="c6e75-2556">이 매개 변수가 0이면 타이머가 ‘일회성’ 타이머가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2556">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="c6e75-2557">매개 변수가 0이 아닌 정기적인 타이머의 경우 유효한 값 범위는 1-0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2557">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2558">만료된 일회성 타이머를 다시 활성화하려면 먼저
***tx_timer_change** __*를 통해 타이머를 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2558">*An expired one-shot timer must be reset via*
***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2559">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2559">Return Values</span></span>

- <span data-ttu-id="c6e75-2560">**TX_SUCCESS**(0x00) 애플리케이션 타이머를 변경하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2560">**TX_SUCCESS** (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="c6e75-2561">**TX_TIMER_ERROR**(0x15) 잘못된 애플리케이션 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2561">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="c6e75-2562">**TX_TICK_ERROR**(0x16) 초기 틱에 잘못된 값(0)이 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2562">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="c6e75-2563">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2563">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2564">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2564">Allowed From</span></span>

<span data-ttu-id="c6e75-2565">스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2565">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2566">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2566">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2567">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2567">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2568">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2568">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Change a previously created and now deactivated timer
to expire every 50 timer ticks, including the initial
expiration. */
status = tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2569">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2569">See Also</span></span>

- <span data-ttu-id="c6e75-2570">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2570">tx_timer_activate</span></span>
- <span data-ttu-id="c6e75-2571">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2571">tx_timer_create</span></span>
- <span data-ttu-id="c6e75-2572">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2572">tx_timer_deactivate</span></span>
- <span data-ttu-id="c6e75-2573">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2573">tx_timer_delete</span></span>
- <span data-ttu-id="c6e75-2574">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2574">tx_timer_info_get</span></span>
- <span data-ttu-id="c6e75-2575">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2575">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2576">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2576">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="c6e75-2577">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2577">tx_timer_create</span></span>

<span data-ttu-id="c6e75-2578">애플리케이션 타이머를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2578">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2579">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2579">Prototype</span></span>

```c
UINT tx_timer_create(
    TX_TIMER *timer_ptr, 
    CHAR *name_ptr,
    VOID (*expiration_function)(ULONG),
    ULONG expiration_input, 
    ULONG initial_ticks,
    ULONG reschedule_ticks, 
    UINT auto_activate);
```

### <a name="description"></a><span data-ttu-id="c6e75-2580">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2580">Description</span></span>

<span data-ttu-id="c6e75-2581">이 서비스는 지정된 만료 함수 및 정기 설정을 사용하여 애플리케이션 타이머를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2581">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2582">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2582">Parameters</span></span>

- <span data-ttu-id="c6e75-2583">**timer_ptr** 타이머 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2583">**timer_ptr** Pointer to a timer control block</span></span>
- <span data-ttu-id="c6e75-2584">**name_ptr** 타이머 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2584">**name_ptr** Pointer to the name of the timer.</span></span>
- <span data-ttu-id="c6e75-2585">**expiration_function** 타이머가 만료될 때 호출하는 애플리케이션 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2585">**expiration_function** Application function to call when the timer expires.</span></span>
- <span data-ttu-id="c6e75-2586">**expiration_input** 타이머가 만료될 때 만료 함수에 전달하는 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2586">**expiration_input** Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="c6e75-2587">**initial_ticks** 타이머 만료에 사용되는 초기 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2587">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="c6e75-2588">유효한 값 범위는 1-0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2588">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="c6e75-2589">**reschedule_ticks** 첫 번째 이후의 모든 타이머 만료에 사용되는 틱 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2589">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="c6e75-2590">이 매개 변수가 0이면 타이머가 ‘일회성’ 타이머가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2590">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="c6e75-2591">매개 변수가 0이 아닌 정기적인 타이머의 경우 유효한 값 범위는 1-0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2591">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c6e75-2592">일회성 타이머가 만료된 후 다시 활성화하려면 먼저 *tx_timer_change* 를 통해 일회성 타이머를 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2592">*After a one-shot timer expires, it must be reset via   tx_timer_change before it can be activated again.*</span></span>

- <span data-ttu-id="c6e75-2593">**auto_activate** 타이머를 만드는 동안 타이머가 자동으로 활성화되는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2593">**auto_activate** Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="c6e75-2594">이 값이 **TX_AUTO_ACTIVATE**(0x01)이면 타이머가 활성 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2594">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="c6e75-2595">그러지 않고 **TX_NO_ACTIVATE**(0x00) 값을 선택하면 타이머가 비활성 상태로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2595">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="c6e75-2596">이 경우 타이머를 실제로 시작하려면 후속 **_tx_timer_activate_** 서비스 호출이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2596">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2597">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2597">Return Values</span></span>

- <span data-ttu-id="c6e75-2598">**TX_SUCCESS**(0x00) 애플리케이션 타이머 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2598">**TX_SUCCESS** (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="c6e75-2599">**TX_TIMER_ERROR**(0x15) 잘못된 애플리케이션 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2599">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="c6e75-2600">포인터가 NULL이거나 타이머가 이미 만들어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2600">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="c6e75-2601">**TX_TICK_ERROR**(0x16) 초기 틱에 잘못된 값(0)이 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2601">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="c6e75-2602">**TX_ACTIVATE_ERROR**(0x17) 잘못된 활성화를 선택했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2602">**TX_ACTIVATE_ERROR** (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="c6e75-2603">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2603">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2604">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2604">Allowed From</span></span>

<span data-ttu-id="c6e75-2605">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-2605">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2606">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2606">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2607">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2607">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2608">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2608">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Create an application timer that executes
"my_timer_function" after 100 ticks initially and then
after every 25 ticks. This timer is specified to start
immediately! */
status = tx_timer_create(&my_timer,"my_timer_name",
    my_timer_function, 0x1234, 100, 25,
    TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
be called 100 timer ticks later and then called every
25 timer ticks. Note that the value 0x1234 is passed to
my_timer_function every time it is called. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2609">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2609">See Also</span></span>

- <span data-ttu-id="c6e75-2610">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2610">tx_timer_activate</span></span>
- <span data-ttu-id="c6e75-2611">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2611">tx_timer_change</span></span>
- <span data-ttu-id="c6e75-2612">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2612">tx_timer_deactivate</span></span>
- <span data-ttu-id="c6e75-2613">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2613">tx_timer_delete</span></span>
- <span data-ttu-id="c6e75-2614">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2614">tx_timer_info_get</span></span>
- <span data-ttu-id="c6e75-2615">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2615">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2616">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2616">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="c6e75-2617">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2617">tx_timer_deactivate</span></span>

<span data-ttu-id="c6e75-2618">애플리케이션 타이머를 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2618">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2619">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2619">Prototype</span></span>

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-2620">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2620">Description</span></span>

<span data-ttu-id="c6e75-2621">이 서비스는 지정된 애플리케이션 타이머를 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2621">This service deactivates the specified application timer.</span></span> <span data-ttu-id="c6e75-2622">타이머가 이미 비활성화되어 있는 경우에는 이 서비스가 아무런 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2622">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2623">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2623">Parameters</span></span>

- <span data-ttu-id="c6e75-2624">**timer_ptr** 이전에 만든 애플리케이션 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2624">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2625">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2625">Return Values</span></span>

- <span data-ttu-id="c6e75-2626">**TX_SUCCESS**(0x00) 애플리케이션 타이머를 비활성화하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2626">**TX_SUCCESS** (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="c6e75-2627">**TX_TIMER_ERROR**(0x15) 잘못된 애플리케이션 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2627">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2628">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2628">Allowed From</span></span>

<span data-ttu-id="c6e75-2629">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2629">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2630">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2630">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2631">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2631">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2632">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2632">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2633">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2633">See Also</span></span>

- <span data-ttu-id="c6e75-2634">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2634">tx_timer_activate</span></span>
- <span data-ttu-id="c6e75-2635">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2635">tx_timer_change</span></span>
- <span data-ttu-id="c6e75-2636">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2636">tx_timer_create</span></span>
- <span data-ttu-id="c6e75-2637">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2637">tx_timer_delete</span></span>
- <span data-ttu-id="c6e75-2638">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2638">tx_timer_info_get</span></span>
- <span data-ttu-id="c6e75-2639">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2639">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2640">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2640">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="c6e75-2641">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2641">tx_timer_delete</span></span>

<span data-ttu-id="c6e75-2642">애플리케이션 타이머를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2642">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2643">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2643">Prototype</span></span>

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="c6e75-2644">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2644">Description</span></span>

<span data-ttu-id="c6e75-2645">이 서비스는 지정된 애플리케이션 타이머를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2645">This service deletes the specified application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2646">애플리케이션은 삭제된 타이머를 사용하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2646">*It is the application's responsibility to prevent use of a deleted timer.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2647">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2647">Parameters</span></span>

- <span data-ttu-id="c6e75-2648">**timer_ptr** 이전에 만든 애플리케이션 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2648">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2649">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2649">Return Values</span></span>

- <span data-ttu-id="c6e75-2650">**TX_SUCCESS**(0x00) 애플리케이션 타이머를 삭제하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2650">**TX_SUCCESS** (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="c6e75-2651">**TX_TIMER_ERROR**(0x15) 잘못된 애플리케이션 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2651">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="c6e75-2652">**TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2652">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2653">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2653">Allowed From</span></span>

<span data-ttu-id="c6e75-2654">스레드</span><span class="sxs-lookup"><span data-stu-id="c6e75-2654">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2655">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2655">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2656">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2656">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2657">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2657">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2658">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2658">See Also</span></span>

- <span data-ttu-id="c6e75-2659">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2659">tx_timer_activate</span></span>
- <span data-ttu-id="c6e75-2660">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2660">tx_timer_change</span></span>
- <span data-ttu-id="c6e75-2661">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2661">tx_timer_create</span></span>
- <span data-ttu-id="c6e75-2662">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2662">tx_timer_deactivate</span></span>
- <span data-ttu-id="c6e75-2663">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2663">tx_timer_info_get</span></span>
- <span data-ttu-id="c6e75-2664">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2664">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2665">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2665">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="c6e75-2666">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2666">tx_timer_info_get</span></span>

<span data-ttu-id="c6e75-2667">애플리케이션 타이머에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2667">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2668">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2668">Prototype</span></span>

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a><span data-ttu-id="c6e75-2669">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2669">Description</span></span>

<span data-ttu-id="c6e75-2670">이 서비스는 지정된 애플리케이션 타이머에 대한 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2670">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2671">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2671">Parameters</span></span>

- <span data-ttu-id="c6e75-2672">**timer_ptr** 이전에 만든 애플리케이션 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2672">**timer_ptr** Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="c6e75-2673">**name** 타이머 이름에 대한 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2673">**name** Pointer to destination for the pointer to the timer's name.</span></span>
- <span data-ttu-id="c6e75-2674">**active** 타이머 활성 표시 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2674">**active** Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="c6e75-2675">타이머가 비활성 상태이거나 이 서비스가 타이머 자체에서 호출된 경우 **TX_FALSE** 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2675">If the timer is inactive or this service is called from the timer itself, a **TX_FALSE** value is returned.</span></span> <span data-ttu-id="c6e75-2676">그러지 않고 타이머가 활성 상태인 경우 **TX_TRUE** 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2676">Otherwise, if the timer is active, a **TX_TRUE** value is returned.</span></span>
- <span data-ttu-id="c6e75-2677">**remaining_ticks** 타이머 만료까지 남은 타이머 틱 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2677">**remaining_ticks** Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="c6e75-2678">**reschedule_ticks** 이 타이머를 자동으로 다시 예약하는 데 사용될 타이머 틱 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2678">**reschedule_ticks** Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="c6e75-2679">값이 0이면 타이머는 일회성이며 다시 예약되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2679">If the value is zero, then the timer is a one-shot and won't be rescheduled.</span></span>
- <span data-ttu-id="c6e75-2680">**next_timer** 다음에 만들 애플리케이션 타이머 포인터 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2680">**next_timer** Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2681">매개 변수에 **TX_NULL** 을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2681">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2682">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2682">Return Values</span></span>

- <span data-ttu-id="c6e75-2683">**TX_SUCCESS**(0x00) 타이머 정보 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2683">**TX_SUCCESS** (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="c6e75-2684">**TX_TIMER_ERROR**(0x15) 잘못된 애플리케이션 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2684">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2685">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2685">Allowed From</span></span>

<span data-ttu-id="c6e75-2686">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2686">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="c6e75-2687">가능한 선점</span><span class="sxs-lookup"><span data-stu-id="c6e75-2687">Preemption Possible</span></span>

<span data-ttu-id="c6e75-2688">예</span><span class="sxs-lookup"><span data-stu-id="c6e75-2688">No</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2689">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2689">Example</span></span>

```c
TX_TIMER my_timer;
CHAR *name;
UINT active;
ULONG remaining_ticks;
ULONG reschedule_ticks;
TX_TIMER *next_timer;
UINT status;

/* Retrieve information about the previously created
application timer "my_timer." */
status = tx_timer_info_get(&my_timer, &name,
    &active,&remaining_ticks,
    &reschedule_ticks,
    &next_timer);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2690">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2690">See Also</span></span>

- <span data-ttu-id="c6e75-2691">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2691">tx_timer_activate</span></span>
- <span data-ttu-id="c6e75-2692">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2692">tx_timer_change</span></span>
- <span data-ttu-id="c6e75-2693">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2693">tx_timer_create</span></span>
- <span data-ttu-id="c6e75-2694">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2694">tx_timer_deactivate</span></span>
- <span data-ttu-id="c6e75-2695">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2695">tx_timer_delete</span></span>
- <span data-ttu-id="c6e75-2696">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2696">tx_timer_info_get</span></span>
- <span data-ttu-id="c6e75-2697">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2697">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="c6e75-2698">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2698">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="c6e75-2699">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2699">tx_timer_performance_info_get</span></span>

<span data-ttu-id="c6e75-2700">타이머 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2700">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2701">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2701">Prototype</span></span>

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="c6e75-2702">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2702">Description</span></span>

<span data-ttu-id="c6e75-2703">이 서비스는 지정된 애플리케이션 타이머에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2703">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-2704">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 \***TX_TIMER_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2704">*The ThreadX library and application must be built with* ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="c6e75-2705">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c6e75-2705">Parameters</span></span>
- <span data-ttu-id="c6e75-2706">**timer_ptr** 이전에 만든 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2706">**timer_ptr** Pointer to previously created timer.</span></span>
- <span data-ttu-id="c6e75-2707">**activates** 이 타이머에서 수행된 활성화 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2707">**activates** Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="c6e75-2708">**reactivates** 이 주기적인 타이머에서 수행되는 자동 다시 활성화 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2708">**reactivates** Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="c6e75-2709">**deactivates** 이 타이머에서 수행되는 비활성화 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2709">**deactivates** Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="c6e75-2710">**expirations** 이 타이머의 만료 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2710">**expirations** Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="c6e75-2711">**expiration_adjusts** 이 타이머에서 수행되는 내부 만료 조정 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2711">**expiration_adjusts** Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="c6e75-2712">이러한 조정은 기본 타이머 목록 크기보다 큰 타이머의 타이머 인터럽트 처리에서 수행됩니다(기본적으로 만료 시간이 32틱을 초과하는 타이머).</span><span class="sxs-lookup"><span data-stu-id="c6e75-2712">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> <span data-ttu-id="c6e75-2713">[참고] 매개 변수에 *TX_NULL* 을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2713">[NOTE] *Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2714">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2714">Return Values</span></span>

- <span data-ttu-id="c6e75-2715">**TX_SUCCESS**(0x00) 타이머 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2715">**TX_SUCCESS** (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="c6e75-2716">**TX_PTR_ERROR**(0x03) 잘못된 타이머 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2716">**TX_PTR_ERROR** (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="c6e75-2717">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2717">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2718">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2718">Allowed From</span></span>

<span data-ttu-id="c6e75-2719">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2719">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2720">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2720">Example</span></span>

```c
TX_TIMER my_timer;
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on the previously created
timer. */
status = tx_timer_performance_info_get(&my_timer, &activates,
    &reactivates,&deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2721">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2721">See Also</span></span>

- <span data-ttu-id="c6e75-2722">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2722">tx_timer_activate</span></span>
- <span data-ttu-id="c6e75-2723">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2723">tx_timer_change</span></span>
- <span data-ttu-id="c6e75-2724">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2724">tx_timer_create</span></span>
- <span data-ttu-id="c6e75-2725">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2725">tx_timer_deactivate</span></span>
- <span data-ttu-id="c6e75-2726">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2726">tx_timer_delete</span></span>
- <span data-ttu-id="c6e75-2727">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2727">tx_timer_info_get</span></span>
- <span data-ttu-id="c6e75-2728">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2728">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="c6e75-2729">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2729">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="c6e75-2730">타이머 시스템 성능 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2730">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6e75-2731">프로토타입</span><span class="sxs-lookup"><span data-stu-id="c6e75-2731">Prototype</span></span>

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="c6e75-2732">Description</span><span class="sxs-lookup"><span data-stu-id="c6e75-2732">Description</span></span>

<span data-ttu-id="c6e75-2733">이 서비스는 시스템의 모든 애플리케이션 타이머에 대한 성능 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2733">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6e75-2734">ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_TIMER_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. </span><span class="sxs-lookup"><span data-stu-id="c6e75-2734">*The ThreadX library and application must be built with* **TX_TIMER_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

<span data-ttu-id="c6e75-2735">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="c6e75-2735">**Parameters**</span></span>

- <span data-ttu-id="c6e75-2736">**activates** 모든 타이머에서 수행되는 총 활성화 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2736">**activates** Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="c6e75-2737">**reactivates** 모든 주기적인 타이머에서 수행되는 총 자동 다시 활성화 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2737">**reactivates** Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="c6e75-2738">**deactivates** 모든 타이머에서 수행되는 총 비활성화 요청 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2738">**deactivates** Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="c6e75-2739">**expirations** 모든 타이머의 총 만료 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2739">**expirations** Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="c6e75-2740">**expiration_adjusts** 모든 타이머에서 수행되는 총 내부 만료 조정 수 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2740">**expiration_adjusts** Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="c6e75-2741">이러한 조정은 기본 타이머 목록 크기보다 큰 타이머의 타이머 인터럽트 처리에서 수행됩니다(기본적으로 만료 시간이 32틱을 초과하는 타이머).</span><span class="sxs-lookup"><span data-stu-id="c6e75-2741">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!NOTE]
> <span data-ttu-id="c6e75-2742">매개 변수에 **TX_NULL** 을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2742">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="c6e75-2743">반환 값</span><span class="sxs-lookup"><span data-stu-id="c6e75-2743">Return Values</span></span>

- <span data-ttu-id="c6e75-2744">**TX_SUCCESS**(0x00) 타이머 시스템 성능 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2744">**TX_SUCCESS** (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="c6e75-2745">**TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="c6e75-2745">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6e75-2746">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="c6e75-2746">Allowed From</span></span>

<span data-ttu-id="c6e75-2747">초기화, 스레드, 타이머, ISR</span><span class="sxs-lookup"><span data-stu-id="c6e75-2747">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="c6e75-2748">예제</span><span class="sxs-lookup"><span data-stu-id="c6e75-2748">Example</span></span>

```c
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on all previously created
timers. */
status = tx_timer_performance_system_info_get(&activates,
    &reactivates, &deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="c6e75-2749">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6e75-2749">See Also</span></span>

- <span data-ttu-id="c6e75-2750">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2750">tx_timer_activate</span></span>
- <span data-ttu-id="c6e75-2751">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="c6e75-2751">tx_timer_change</span></span>
- <span data-ttu-id="c6e75-2752">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="c6e75-2752">tx_timer_create</span></span>
- <span data-ttu-id="c6e75-2753">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="c6e75-2753">tx_timer_deactivate</span></span>
- <span data-ttu-id="c6e75-2754">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="c6e75-2754">tx_timer_delete</span></span>
- <span data-ttu-id="c6e75-2755">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2755">tx_timer_info_get</span></span>
- <span data-ttu-id="c6e75-2756">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="c6e75-2756">tx_timer_performance_info_get</span></span>
