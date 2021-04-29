---
title: 4장 - 모듈 API
author: philmea
ms.author: philmea
description: 이 문서에는 모듈에 사용할 수 있는 추가 API가 요약되어 있습니다.
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5804e2dbb8d08a272abc85a583576f43b7204c1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810303"
---
# <a name="chapter-4---module-apis"></a><span data-ttu-id="cd1e4-103">4장 - 모듈 API</span><span class="sxs-lookup"><span data-stu-id="cd1e4-103">Chapter 4 - Module APIs</span></span>

## <a name="summary-of-module-apis"></a><span data-ttu-id="cd1e4-104">모듈 API 요약</span><span class="sxs-lookup"><span data-stu-id="cd1e4-104">Summary of Module APIs</span></span>

<span data-ttu-id="cd1e4-105">모듈에는 다음과 같이 다양한 추가 API 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-105">There are several additional API functions available to a module, as follows:</span></span>

- <span data-ttu-id="cd1e4-106">***txm_module_application_request** _ - _*상주 코드에 대한 애플리케이션별 요청입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-106">***txm_module_application_request** _ - _Application-specific request to resident code*</span></span>
- <span data-ttu-id="cd1e4-107">***txm_module_object_allocate** _ - _*모듈 외부에 개체용 메모리를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-107">***txm_module_object_allocate** _ - _Allocate memory outside of module for object*</span></span>
- <span data-ttu-id="cd1e4-108">***txm_module_object_deallocate** _ - _*이전에 할당된 개체 메모리에 대한 할당을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-108">***txm_module_object_deallocate** _ - _Deallocate previously allocated object memory*</span></span>
- <span data-ttu-id="cd1e4-109">***txm_module_object_pointer_get** _ - _*시스템 개체를 찾고 개체 포인터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-109">***txm_module_object_pointer_get** _ - _Find system object and retrieve object pointer*</span></span>
- <span data-ttu-id="cd1e4-110">***txm_module_object_pointer_get_extended** _ - _*시스템 개체를 찾고 개체 포인터인 이름 길이 보호를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-110">***txm_module_object_pointer_get_extended** _ - _Find system object and retrieve object pointer, name length safety*</span></span>

## <a name="return-values"></a><span data-ttu-id="cd1e4-111">반환 값</span><span class="sxs-lookup"><span data-stu-id="cd1e4-111">Return values</span></span>

<span data-ttu-id="cd1e4-112">일부 Azure RTOS API에 대해 추가 오류 코드가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-112">Additional error codes are returned for some Azure RTOS APIs.</span></span> <span data-ttu-id="cd1e4-113">해당 추가 오류 코드는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-113">These additional error codes are defined as follows:</span></span>

- <span data-ttu-id="cd1e4-114">**TXM_MODULE_INVALID_PROPERTIES**(0xF3): 모듈에 API 호출을 수행하는 데 적합한 속성이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): Indicates the module does not have the correct properties to make an API call.</span></span> <span data-ttu-id="cd1e4-115">예를 들어 추적 API는 사용자 모드에서 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-115">For example, calling trace APIs in user mode.</span></span>
- <span data-ttu-id="cd1e4-116">**TXM_MODULE_INVALID_MEMORY**(0xF4): 모듈에서 제공한 메모리가 잘못되었거나 잘못된 위치에 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): Indicates the memory supplied by the module is invalid or is in an invalid location.</span></span> <span data-ttu-id="cd1e4-117">예를 들어 메모리 보호 모듈에서는 모듈이 액세스할 수 있는 메모리에 개체 제어 블록을 배치할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-117">For example, in memory protected modules, object control blocks are not allowed to be located in memory the module can access.</span></span>
- <span data-ttu-id="cd1e4-118">**TXM_MODULE_INVALID_CALLBACK**(0xF5): API에 지정된 콜백이 모듈 코드 범위를 벗어나므로 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): Callback specified in the API is outside the range of the module's code and is therefore invalid.</span></span>

---

## <a name="txm_module_application_request"></a><span data-ttu-id="cd1e4-119">txm_module_application_request</span><span class="sxs-lookup"><span data-stu-id="cd1e4-119">txm_module_application_request</span></span>

<span data-ttu-id="cd1e4-120">상주 코드에 대한 애플리케이션별 요청입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-120">Application-specific request to resident code.</span></span>

### <a name="prototype"></a><span data-ttu-id="cd1e4-121">프로토타입</span><span class="sxs-lookup"><span data-stu-id="cd1e4-121">Prototype</span></span>

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a><span data-ttu-id="cd1e4-122">Description</span><span class="sxs-lookup"><span data-stu-id="cd1e4-122">Description</span></span>

<span data-ttu-id="cd1e4-123">이 서비스는 애플리케이션의 상주 부분에 대해 지정된 요청을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-123">This service makes the specified request to the resident portion of the application.</span></span> <span data-ttu-id="cd1e4-124">호출 전에 요청 구조가 준비되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-124">It is assumed that the request structure is prepared prior to the call.</span></span> <span data-ttu-id="cd1e4-125">요청의 실제 처리는 ***_txm_module_manager_application_request*** 함수의 상주 코드에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-125">The actual processing of the request takes place in the resident code in the function ***_txm_module_manager_application_request***.</span></span> <span data-ttu-id="cd1e4-126">기본적으로 이 함수는 비어 있으며 상주 애플리케이션 개발자가 수정하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-126">By default, this function is left empty and is designed for the resident application developer to modify.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="cd1e4-127">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="cd1e4-127">Input parameters</span></span>

- <span data-ttu-id="cd1e4-128">**request** 요청 ID입니다(애플리케이션이 정의됨).</span><span class="sxs-lookup"><span data-stu-id="cd1e4-128">**request** Request ID (application defined)</span></span>
- <span data-ttu-id="cd1e4-129">**param_1** 첫 번째 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-129">**param_1** First parameter</span></span>
- <span data-ttu-id="cd1e4-130">**param_2** 두 번째 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-130">**param_2** Second parameter</span></span>
- <span data-ttu-id="cd1e4-131">**param_3** 세 번째 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-131">**param_3** Third parameter</span></span>

### <a name="return-values"></a><span data-ttu-id="cd1e4-132">반환 값</span><span class="sxs-lookup"><span data-stu-id="cd1e4-132">Return values</span></span>

- <span data-ttu-id="cd1e4-133">**TX_SUCCESS**(0x00) 요청에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-133">**TX_SUCCESS** (0x00) Successful request.</span></span>
- <span data-ttu-id="cd1e4-134">**TX_NOT_AVAILABLE**(0x1D) 요청이 상주 코드에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-134">**TX_NOT_AVAILABLE** (0x1D) Request not supported by resident code.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="cd1e4-135">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="cd1e4-135">Allowed from</span></span>

<span data-ttu-id="cd1e4-136">모듈 스레드</span><span class="sxs-lookup"><span data-stu-id="cd1e4-136">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="cd1e4-137">예제</span><span class="sxs-lookup"><span data-stu-id="cd1e4-137">Example</span></span>

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a><span data-ttu-id="cd1e4-138">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="cd1e4-138">txm_module_object_allocate</span></span>

<span data-ttu-id="cd1e4-139">개체 풀(상주 애플리케이션에서 만든 풀)에 모듈 개체 제어 블록용 메모리를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-139">Allocate memory in the object pool (created by the resident application) for a module object control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="cd1e4-140">프로토타입</span><span class="sxs-lookup"><span data-stu-id="cd1e4-140">Prototype</span></span>

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a><span data-ttu-id="cd1e4-141">Description</span><span class="sxs-lookup"><span data-stu-id="cd1e4-141">Description</span></span>

<span data-ttu-id="cd1e4-142">이 서비스는 모듈 외부의 메모리에서 모듈 개체용 메모리를 할당합니다. 이렇게 하면 모듈 코드의 개체 제어 블록 손상을 방지하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-142">This service allocates memory for a module object from memory outside of the module, which helps prevent corruption of the object control block by the module's code.</span></span> <span data-ttu-id="cd1e4-143">메모리 보호 시스템에서는 모든 개체 제어 블록을 만들려면 먼저 이 API를 사용하여 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-143">In memory protected systems, all object control blocks must be allocated with this API before they can be created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="cd1e4-144">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="cd1e4-144">Input parameters</span></span>

- <span data-ttu-id="cd1e4-145">**object_ptr** 할당에 성공한 개체 포인터 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-145">**object_ptr** Destination of object pointer on successful allocation.</span></span>
- <span data-ttu-id="cd1e4-146">**object_size** 할당할 개체의 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-146">**object_size** Size in bytes of the object to be allocated.</span></span>

### <a name="return-values"></a><span data-ttu-id="cd1e4-147">반환 값</span><span class="sxs-lookup"><span data-stu-id="cd1e4-147">Return values</span></span>

- <span data-ttu-id="cd1e4-148">**TX_SUCCESS**(0x00) 개체 할당에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-148">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>
- <span data-ttu-id="cd1e4-149">**TX_NO_MEMORY**(0x10) 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-149">**TX_NO_MEMORY** (0x10) Not enough memory.</span></span>
- <span data-ttu-id="cd1e4-150">**TX_NOT_AVAILABLE**(0x1D) 모듈 관리자가 할당할 개체 풀을 만들지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-150">**TX_NOT_AVAILABLE** (0x1D) Module manager has not created an object pool to allocate from</span></span>

### <a name="allowed-from"></a><span data-ttu-id="cd1e4-151">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="cd1e4-151">Allowed from</span></span>

<span data-ttu-id="cd1e4-152">모듈 스레드</span><span class="sxs-lookup"><span data-stu-id="cd1e4-152">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="cd1e4-153">예제</span><span class="sxs-lookup"><span data-stu-id="cd1e4-153">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a><span data-ttu-id="cd1e4-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd1e4-154">See also</span></span>

- <span data-ttu-id="cd1e4-155">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="cd1e4-155">txm_module_object_deallocate</span></span>
- <span data-ttu-id="cd1e4-156">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="cd1e4-156">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_deallocate"></a><span data-ttu-id="cd1e4-157">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="cd1e4-157">txm_module_object_deallocate</span></span>

<span data-ttu-id="cd1e4-158">이전에 할당한 개체 메모리를 할당 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-158">Deallocate previously allocated object memory</span></span>

### <a name="prototype"></a><span data-ttu-id="cd1e4-159">프로토타입</span><span class="sxs-lookup"><span data-stu-id="cd1e4-159">Prototype</span></span>

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a><span data-ttu-id="cd1e4-160">Description</span><span class="sxs-lookup"><span data-stu-id="cd1e4-160">Description</span></span>

<span data-ttu-id="cd1e4-161">이 서비스는 더 이상 필요하지 않으므로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-161">***This service has been deprecated because it is no longer needed***.</span></span>

<span data-ttu-id="cd1e4-162">***txm_module_object_allocate* *_를 통해 이전에 할당한 메모리를 _* _tx_\__delete service**\* 에서 할당 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-162">The memory that was previously allocated via ***txm_module_object_allocate\**_ is deallocated in the _*_tx_\__delete service***.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="cd1e4-163">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="cd1e4-163">Input parameters</span></span>

- <span data-ttu-id="cd1e4-164">**object_ptr** 할당을 취소할 개체 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-164">**object_ptr** Object pointer to deallocate.</span></span>

### <a name="return-values"></a><span data-ttu-id="cd1e4-165">반환 값</span><span class="sxs-lookup"><span data-stu-id="cd1e4-165">Return values</span></span>

- <span data-ttu-id="cd1e4-166">**TX_SUCCESS**(0x00) 개체 할당에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-166">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="cd1e4-167">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="cd1e4-167">Allowed from</span></span>

<span data-ttu-id="cd1e4-168">모듈 스레드</span><span class="sxs-lookup"><span data-stu-id="cd1e4-168">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="cd1e4-169">예제</span><span class="sxs-lookup"><span data-stu-id="cd1e4-169">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a><span data-ttu-id="cd1e4-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd1e4-170">See also</span></span>

- <span data-ttu-id="cd1e4-171">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="cd1e4-171">txm_module_object_allocate</span></span>
- <span data-ttu-id="cd1e4-172">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="cd1e4-172">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_pointer_get"></a><span data-ttu-id="cd1e4-173">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="cd1e4-173">txm_module_object_pointer_get</span></span>

<span data-ttu-id="cd1e4-174">시스템 개체를 찾고 개체 포인터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-174">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="cd1e4-175">프로토타입</span><span class="sxs-lookup"><span data-stu-id="cd1e4-175">Prototype</span></span>

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="cd1e4-176">Description</span><span class="sxs-lookup"><span data-stu-id="cd1e4-176">Description</span></span>

<span data-ttu-id="cd1e4-177">이 서비스는 특정 이름을 사용하는 특정 형식의 개체 포인터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-177">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="cd1e4-178">개체를 찾지 못하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-178">If the object is not found, an error is returned.</span></span> <span data-ttu-id="cd1e4-179">개체를 찾으면 해당 개체의 주소가 “object_ptr”에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-179">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="cd1e4-180">그러면 이 포인터로 시스템 서비스를 호출하여 상주 코드 및/또는 시스템의 다른 로드된 모듈을 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-180">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="cd1e4-181">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="cd1e4-181">Input parameters</span></span>

- <span data-ttu-id="cd1e4-182">**object_type** 요청된 ThreadX 개체 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-182">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="cd1e4-183">유효한 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-183">Valid types are as follows:</span></span>
  - <span data-ttu-id="cd1e4-184">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-184">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-185">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-185">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-186">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-186">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-187">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-187">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-188">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-188">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-189">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-189">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-190">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-190">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-191">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-191">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-192">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-192">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-193">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-193">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-194">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-194">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-195">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-195">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="cd1e4-196">**name** 개체를 만들 때 정의된 애플리케이션별 개체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-196">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="cd1e4-197">**object_ptr** 개체 포인터 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-197">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="cd1e4-198">반환 값</span><span class="sxs-lookup"><span data-stu-id="cd1e4-198">Return values</span></span>

- <span data-ttu-id="cd1e4-199">**TX_SUCCESS**(0x00) 개체 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-199">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="cd1e4-200">**TX_OPTION_ERROR**(0x08) 잘못된 개체 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-200">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="cd1e4-201">**TX_PTR_ERROR**(0x03) 잘못된 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-201">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="cd1e4-202">**TX_SIZE_ERROR**(0x05) 잘못된 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-202">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="cd1e4-203">**TX_NO_INSTANCE**(0x0D) 개체를 찾지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-203">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="cd1e4-204">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="cd1e4-204">Allowed from</span></span>

<span data-ttu-id="cd1e4-205">모듈 스레드</span><span class="sxs-lookup"><span data-stu-id="cd1e4-205">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="cd1e4-206">예제</span><span class="sxs-lookup"><span data-stu-id="cd1e4-206">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="cd1e4-207">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd1e4-207">See also</span></span>

- <span data-ttu-id="cd1e4-208">txm_module_manager_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="cd1e4-208">txm_module_manager_object_pointer_get_extended</span></span>

---

## <a name="txm_module_object_pointer_get_extended"></a><span data-ttu-id="cd1e4-209">txm_module_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="cd1e4-209">txm_module_object_pointer_get_extended</span></span>

<span data-ttu-id="cd1e4-210">시스템 개체를 찾고 개체 포인터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-210">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="cd1e4-211">프로토타입</span><span class="sxs-lookup"><span data-stu-id="cd1e4-211">Prototype</span></span>

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="cd1e4-212">Description</span><span class="sxs-lookup"><span data-stu-id="cd1e4-212">Description</span></span>

<span data-ttu-id="cd1e4-213">이 서비스는 특정 이름을 사용하는 특정 형식의 개체 포인터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-213">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="cd1e4-214">개체를 찾지 못하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-214">If the object is not found, an error is returned.</span></span> <span data-ttu-id="cd1e4-215">개체를 찾으면 해당 개체의 주소가 “object_ptr”에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-215">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="cd1e4-216">그러면 이 포인터로 시스템 서비스를 호출하여 상주 코드 및/또는 시스템의 다른 로드된 모듈을 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-216">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="cd1e4-217">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="cd1e4-217">Input parameters</span></span>

- <span data-ttu-id="cd1e4-218">**object_type** 요청된 ThreadX 개체 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-218">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="cd1e4-219">유효한 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-219">Valid types are as follows:</span></span>
  - <span data-ttu-id="cd1e4-220">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-220">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-221">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-221">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-222">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-222">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-223">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-223">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-224">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-224">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-225">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-225">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-226">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-226">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-227">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-227">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-228">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-228">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-229">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-229">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-230">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-230">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="cd1e4-231">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="cd1e4-231">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="cd1e4-232">**name** 개체를 만들 때 정의된 애플리케이션별 개체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-232">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="cd1e4-233">**name_length** 이름 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-233">**name_length** Length of name.</span></span>
- <span data-ttu-id="cd1e4-234">**object_ptr** 개체 포인터 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-234">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="cd1e4-235">반환 값</span><span class="sxs-lookup"><span data-stu-id="cd1e4-235">Return values</span></span>

- <span data-ttu-id="cd1e4-236">**TX_SUCCESS**(0x00) 개체 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-236">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="cd1e4-237">**TX_OPTION_ERROR**(0x08) 잘못된 개체 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-237">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="cd1e4-238">**TX_PTR_ERROR**(0x03) 잘못된 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-238">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="cd1e4-239">**TX_SIZE_ERROR**(0x05) 잘못된 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-239">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="cd1e4-240">**TX_NO_INSTANCE**(0x0D) 개체를 찾지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd1e4-240">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="cd1e4-241">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="cd1e4-241">Allowed from</span></span>

<span data-ttu-id="cd1e4-242">모듈 스레드</span><span class="sxs-lookup"><span data-stu-id="cd1e4-242">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="cd1e4-243">예제</span><span class="sxs-lookup"><span data-stu-id="cd1e4-243">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="cd1e4-244">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd1e4-244">See also</span></span>

- <span data-ttu-id="cd1e4-245">txm_module_manager_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="cd1e4-245">txm_module_manager_object_pointer_get</span></span>
