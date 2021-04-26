---
title: 6장 - Azure RTOS LevelX NOR API
description: 애플리케이션에 사용할 수 있는 Azure RTOS LevelX NOR API
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ab7d3a7e431d7c8f49ef4f5cab9216dc77c8d33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811868"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a><span data-ttu-id="893b3-103">6장 - Azure RTOS LevelX NOR API</span><span class="sxs-lookup"><span data-stu-id="893b3-103">Chapter 6 - Azure RTOS LevelX NOR APIs</span></span>

<span data-ttu-id="893b3-104">애플리케이션에 사용할 수 있는 Azure RTOS LevelX NOR API 함수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-104">The Azure RTOS LevelX NOR API functions available to the application are as follows.</span></span>

- <span data-ttu-id="893b3-105">***lx_nor_flash_close** _: _NOR 플래시 인스턴스 닫기*</span><span class="sxs-lookup"><span data-stu-id="893b3-105">***lx_nor_flash_close** _: _Close NOR flash instance*</span></span>
- <span data-ttu-id="893b3-106">***lx_nor_flash_defragment** _: _NOR 플래시 인스턴스 조각 모음*</span><span class="sxs-lookup"><span data-stu-id="893b3-106">***lx_nor_flash_defragment** _: _Defragment NOR flash instance*</span></span>
- <span data-ttu-id="893b3-107">***lx_nor_flash_extended_cache_enable** _: _확장된 NOR 캐시 사용/사용 안 함*</span><span class="sxs-lookup"><span data-stu-id="893b3-107">***lx_nor_flash_extended_cache_enable** _: _Enable/disable extended NOR cache*</span></span>
- <span data-ttu-id="893b3-108">***lx_nor_flash_initialize** _: _NOR 플래시 지원 초기화*</span><span class="sxs-lookup"><span data-stu-id="893b3-108">***lx_nor_flash_initialize** _: _Initialize NOR flash support*</span></span>
- <span data-ttu-id="893b3-109">***lx_nor_flash_open** _: _NOR 플래시 인스턴스 열기*</span><span class="sxs-lookup"><span data-stu-id="893b3-109">***lx_nor_flash_open** _: _Open NOR flash instance*</span></span>
- <span data-ttu-id="893b3-110">***lx_nor_flash_partial_defragment** _: _NOR 플래시 인스턴스의 부분 조각 모음*</span><span class="sxs-lookup"><span data-stu-id="893b3-110">***lx_nor_flash_partial_defragment** _: _Partial defragment of NOR flash instance*</span></span>
- <span data-ttu-id="893b3-111">***lx_nor_flash_sector_read** _: _NOR 플래시 섹터 읽기*</span><span class="sxs-lookup"><span data-stu-id="893b3-111">***lx_nor_flash_sector_read** _: _Read NOR flash sector*</span></span>
- <span data-ttu-id="893b3-112">***lx_nor_flash_sector_release** _: _NOR 플래시 섹터 해제*</span><span class="sxs-lookup"><span data-stu-id="893b3-112">***lx_nor_flash_sector_release** _: _Release NOR flash sector*</span></span>
- <span data-ttu-id="893b3-113">***lx_nor_flash_sector_write** _: _NOR 플래시 섹터 쓰기*</span><span class="sxs-lookup"><span data-stu-id="893b3-113">***lx_nor_flash_sector_write** _: _Write NOR flash sector*</span></span>

## <a name="lx_nor_flash_close"></a><span data-ttu-id="893b3-114">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="893b3-114">lx_nor_flash_close</span></span>

<span data-ttu-id="893b3-115">NOR 플래시 인스턴스 닫기</span><span class="sxs-lookup"><span data-stu-id="893b3-115">Close NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="893b3-116">프로토타입</span><span class="sxs-lookup"><span data-stu-id="893b3-116">Prototype</span></span>

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="893b3-117">Description</span><span class="sxs-lookup"><span data-stu-id="893b3-117">Description</span></span>

<span data-ttu-id="893b3-118">이 서비스는 이전에 열었던 NOR 플래시 인스턴스를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-118">This service closes the previously opened NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="893b3-119">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="893b3-119">Input Parameters</span></span>

- <span data-ttu-id="893b3-120">*nor_flash*: NOR 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-120">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="893b3-121">반환 값</span><span class="sxs-lookup"><span data-stu-id="893b3-121">Return Values</span></span>

- <span data-ttu-id="893b3-122">**LX_SUCCESS**: (0x00) 성공적인 요청</span><span class="sxs-lookup"><span data-stu-id="893b3-122">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="893b3-123">**LX_ERROR**: (0x01) 플래시 인스턴스를 닫는 동안 오류 발생</span><span class="sxs-lookup"><span data-stu-id="893b3-123">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="893b3-124">허용 위치</span><span class="sxs-lookup"><span data-stu-id="893b3-124">Allowed From</span></span>

<span data-ttu-id="893b3-125">스레드</span><span class="sxs-lookup"><span data-stu-id="893b3-125">Threads</span></span>

### <a name="example"></a><span data-ttu-id="893b3-126">예제</span><span class="sxs-lookup"><span data-stu-id="893b3-126">Example</span></span>

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="893b3-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="893b3-127">See Also</span></span>

- <span data-ttu-id="893b3-128">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-128">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="893b3-129">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="893b3-129">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="893b3-130">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="893b3-130">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="893b3-131">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="893b3-131">lx_nor_flash_open</span></span>
- <span data-ttu-id="893b3-132">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-132">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="893b3-133">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="893b3-133">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="893b3-134">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="893b3-134">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="893b3-135">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="893b3-135">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_defragment"></a><span data-ttu-id="893b3-136">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-136">lx_nor_flash_defragment</span></span>

<span data-ttu-id="893b3-137">NOR 플래시 인스턴스 조각 모음</span><span class="sxs-lookup"><span data-stu-id="893b3-137">Defragment NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="893b3-138">프로토타입</span><span class="sxs-lookup"><span data-stu-id="893b3-138">Prototype</span></span>

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="893b3-139">Description</span><span class="sxs-lookup"><span data-stu-id="893b3-139">Description</span></span>

<span data-ttu-id="893b3-140">이 서비스는 이전에 열었던 NOR 플래시 인스턴스의 조각을 모읍니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-140">This service defragments the previously opened NOR flash instance.</span></span> <span data-ttu-id="893b3-141">조각 모음 프로세스는 사용 가능한 섹터 및 블록의 수를 최대화합니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-141">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="893b3-142">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="893b3-142">Input Parameters</span></span>

- <span data-ttu-id="893b3-143">*nor_flash*: NOR 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-143">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="893b3-144">반환 값</span><span class="sxs-lookup"><span data-stu-id="893b3-144">Return Values</span></span>

- <span data-ttu-id="893b3-145">**LX_SUCCESS**: (0x00) 성공적인 요청</span><span class="sxs-lookup"><span data-stu-id="893b3-145">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="893b3-146">**LX_ERROR**: (0x01) 플래시 인스턴스를 조각 모음하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-146">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="893b3-147">허용 위치</span><span class="sxs-lookup"><span data-stu-id="893b3-147">Allowed From</span></span>

<span data-ttu-id="893b3-148">스레드</span><span class="sxs-lookup"><span data-stu-id="893b3-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="893b3-149">예제</span><span class="sxs-lookup"><span data-stu-id="893b3-149">Example</span></span>

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="893b3-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="893b3-150">See Also</span></span>

- <span data-ttu-id="893b3-151">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="893b3-151">lx_nor_flash_close</span></span>
- <span data-ttu-id="893b3-152">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="893b3-152">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="893b3-153">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="893b3-153">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="893b3-154">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="893b3-154">lx_nor_flash_open</span></span>
- <span data-ttu-id="893b3-155">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-155">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="893b3-156">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="893b3-156">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="893b3-157">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="893b3-157">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="893b3-158">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="893b3-158">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_extended_cache_enable"></a><span data-ttu-id="893b3-159">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="893b3-159">lx_nor_flash_extended_cache_enable</span></span>

<span data-ttu-id="893b3-160">확장된 NOR 캐시 사용/사용 안 함</span><span class="sxs-lookup"><span data-stu-id="893b3-160">Enable/disable extended NOR cache</span></span>

### <a name="prototype"></a><span data-ttu-id="893b3-161">프로토타입</span><span class="sxs-lookup"><span data-stu-id="893b3-161">Prototype</span></span>

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="893b3-162">Description</span><span class="sxs-lookup"><span data-stu-id="893b3-162">Description</span></span>

<span data-ttu-id="893b3-163">이 서비스는 애플리케이션에서 제공하는 메모리를 사용하여 RAM에서 NOR 섹터 캐시 계층을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-163">This service implements a NOR sector cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="893b3-164">제공된 각 512바이트의 메모리는 캐시될 수 있는 하나의 NOR 섹터로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-164">Each 512 bytes of memory supplied translates to one NOR sector that can be cached.</span></span> <span data-ttu-id="893b3-165">캐시된 섹터는 블록 제어 정보(예: 지우기 수, 사용 가능한 섹터 맵 및 섹터 매핑 정보)를 포함하는 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-165">The sectors cached are those that contain the block control information, e.g., erase count, free sector map, and sector mapping information.</span></span> <span data-ttu-id="893b3-166">데이터 섹터는 이 캐시에 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-166">Data sectors are not stored in this cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="893b3-167">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="893b3-167">Input Parameters</span></span>

- <span data-ttu-id="893b3-168">**nor_flash**: NOR 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-168">**nor_flash**: NOR flash instance pointer.</span></span>  
- <span data-ttu-id="893b3-169">**memory**: 캐시 메모리에 대한 시작 주소로, ULONG 액세스에 맞게 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-169">**memory**: Starting address for cache memory, aligned for ULONG access.</span></span> <span data-ttu-id="893b3-170">LX_NULL 값은 캐시를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-170">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="893b3-171">**size** 제공된 메모리의 크기(바이트)입니다(512바이트의 배수여야 함).</span><span class="sxs-lookup"><span data-stu-id="893b3-171">**size**: The size in bytes of the memory supplied (should be multiple of 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="893b3-172">반환 값</span><span class="sxs-lookup"><span data-stu-id="893b3-172">Return Values</span></span>

- <span data-ttu-id="893b3-173">**LX_SUCCESS**: (0x00) 성공적인 요청</span><span class="sxs-lookup"><span data-stu-id="893b3-173">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="893b3-174">**LX_ERROR**: (0x01) 단일 NOR 섹션에 대한 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-174">**LX_ERROR**: (0x01) Not enough memory for one NOR sector.</span></span>
- <span data-ttu-id="893b3-175">**LX_DISABLED**: (0x09) 구성 옵션으로 NOR 확장 캐시가 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-175">**LX_DISABLED**: (0x09) NOR extended cache disabled by configuration option.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="893b3-176">허용 위치</span><span class="sxs-lookup"><span data-stu-id="893b3-176">Allowed From</span></span>

<span data-ttu-id="893b3-177">스레드</span><span class="sxs-lookup"><span data-stu-id="893b3-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="893b3-178">예제</span><span class="sxs-lookup"><span data-stu-id="893b3-178">Example</span></span>

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="893b3-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="893b3-179">See Also</span></span>

- <span data-ttu-id="893b3-180">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="893b3-180">lx_nor_flash_close</span></span>
- <span data-ttu-id="893b3-181">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-181">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="893b3-182">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="893b3-182">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="893b3-183">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="893b3-183">lx_nor_flash_open</span></span>
- <span data-ttu-id="893b3-184">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-184">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="893b3-185">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="893b3-185">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="893b3-186">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="893b3-186">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="893b3-187">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="893b3-187">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_initialize"></a><span data-ttu-id="893b3-188">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="893b3-188">lx_nor_flash_initialize</span></span>

<span data-ttu-id="893b3-189">NOR 플래시 지원 초기화</span><span class="sxs-lookup"><span data-stu-id="893b3-189">Initialize NOR flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="893b3-190">프로토타입</span><span class="sxs-lookup"><span data-stu-id="893b3-190">Prototype</span></span>

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="893b3-191">Description</span><span class="sxs-lookup"><span data-stu-id="893b3-191">Description</span></span>

<span data-ttu-id="893b3-192">이 서비스는 LevelX NOR 플래시 지원을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-192">This service initializes LevelX NOR flash support.</span></span> <span data-ttu-id="893b3-193">다른 LevelX NOR API보다 먼저 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-193">It must be called before any other LevelX NOR APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="893b3-194">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="893b3-194">Input Parameters</span></span>

- <span data-ttu-id="893b3-195">**없음**</span><span class="sxs-lookup"><span data-stu-id="893b3-195">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="893b3-196">반환 값</span><span class="sxs-lookup"><span data-stu-id="893b3-196">Return Values</span></span>

- <span data-ttu-id="893b3-197">**LX_SUCCESS**: (0x00) 성공적인 요청</span><span class="sxs-lookup"><span data-stu-id="893b3-197">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="893b3-198">**LX_ERROR**: (0x01) NOR 플래시 지원을 초기화하는 동안 오류 발생</span><span class="sxs-lookup"><span data-stu-id="893b3-198">**LX_ERROR**: (0x01) Error initializing NOR flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="893b3-199">허용 위치</span><span class="sxs-lookup"><span data-stu-id="893b3-199">Allowed From</span></span>

<span data-ttu-id="893b3-200">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="893b3-200">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="893b3-201">예제</span><span class="sxs-lookup"><span data-stu-id="893b3-201">Example</span></span>

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="893b3-202">참고 항목</span><span class="sxs-lookup"><span data-stu-id="893b3-202">See Also</span></span>

- <span data-ttu-id="893b3-203">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="893b3-203">lx_nor_flash_close</span></span>
- <span data-ttu-id="893b3-204">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-204">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="893b3-205">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="893b3-205">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="893b3-206">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-206">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="893b3-207">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="893b3-207">lx_nor_flash_open</span></span>
- <span data-ttu-id="893b3-208">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="893b3-208">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="893b3-209">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="893b3-209">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="893b3-210">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="893b3-210">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_open"></a><span data-ttu-id="893b3-211">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="893b3-211">lx_nor_flash_open</span></span>

<span data-ttu-id="893b3-212">NOR 플래시 인스턴스 열기</span><span class="sxs-lookup"><span data-stu-id="893b3-212">Open NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="893b3-213">프로토타입</span><span class="sxs-lookup"><span data-stu-id="893b3-213">Prototype</span></span>

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a><span data-ttu-id="893b3-214">Description</span><span class="sxs-lookup"><span data-stu-id="893b3-214">Description</span></span>

<span data-ttu-id="893b3-215">이 서비스는 지정된 NOR 플래시 제어 블록과 드라이버 초기화 함수를 사용하여 NOR 플래시 인스턴스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-215">This service opens a NOR flash instance with the specified NOR flash control block and driver initialization function.</span></span> <span data-ttu-id="893b3-216">드라이버 초기화 함수는 이 NOR 플래시 인스턴스와 연결된 NOR 하드웨어의 블록을 읽고, 쓰고, 지우기 위한 다양한 함수 포인터를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-216">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks of the NOR hardware associated with this NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="893b3-217">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="893b3-217">Input Parameters</span></span>

- <span data-ttu-id="893b3-218">*nor_flash*: NOR 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-218">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="893b3-219">*name*: NOR 플래시 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-219">*name*: Name of NOR flash instance.</span></span>
- <span data-ttu-id="893b3-220">*nor_driver_initialize*: NOR 플래시 드라이버 초기화 함수에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-220">*nor_driver_initialize*: Function pointer to NOR flash driver Initialization function.</span></span> <span data-ttu-id="893b3-221">NOR 플래시 드라이버 역할에 대한 자세한 내용은 이 가이드의 5장을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="893b3-221">Please refer to Chapter 5 of this guide for more details on NOR flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="893b3-222">반환 값</span><span class="sxs-lookup"><span data-stu-id="893b3-222">Return Values</span></span>

- <span data-ttu-id="893b3-223">**LX_SUCCESS**: (0x00) 성공적인 요청</span><span class="sxs-lookup"><span data-stu-id="893b3-223">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="893b3-224">**LX_ERROR**: (0x01) NOR 플래시 인스턴스를 여는 동안 오류 발생</span><span class="sxs-lookup"><span data-stu-id="893b3-224">**LX_ERROR**: (0x01) Error opening NOR flash instance.</span></span>
- <span data-ttu-id="893b3-225">**LX_NO_MEMORY**: (0X08) 드라이버가 RAM으로 none 섹터를 읽기 위한 버퍼를 제공하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-225">**LX_NO_MEMORY**:  (0x08) Driver did not provide buffer for reading none sector into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="893b3-226">허용 위치</span><span class="sxs-lookup"><span data-stu-id="893b3-226">Allowed From</span></span>

<span data-ttu-id="893b3-227">스레드</span><span class="sxs-lookup"><span data-stu-id="893b3-227">Threads</span></span>

### <a name="example"></a><span data-ttu-id="893b3-228">예제</span><span class="sxs-lookup"><span data-stu-id="893b3-228">Example</span></span>

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="893b3-229">참고 항목</span><span class="sxs-lookup"><span data-stu-id="893b3-229">See Also</span></span>

- <span data-ttu-id="893b3-230">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="893b3-230">lx_nor_flash_close</span></span>
- <span data-ttu-id="893b3-231">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-231">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="893b3-232">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="893b3-232">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="893b3-233">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="893b3-233">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="893b3-234">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-234">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="893b3-235">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="893b3-235">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="893b3-236">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="893b3-236">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="893b3-237">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="893b3-237">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_partial_defragment"></a><span data-ttu-id="893b3-238">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-238">lx_nor_flash_partial_defragment</span></span>

<span data-ttu-id="893b3-239">NOR 플래시 인스턴스의 부분 조각 모음</span><span class="sxs-lookup"><span data-stu-id="893b3-239">Partial defragment of NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="893b3-240">프로토타입</span><span class="sxs-lookup"><span data-stu-id="893b3-240">Prototype</span></span>

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="893b3-241">Description</span><span class="sxs-lookup"><span data-stu-id="893b3-241">Description</span></span>

<span data-ttu-id="893b3-242">이 서비스는 이전에 열었던 NOR 플래시 인스턴스를 지정된 최대 블록 수까지 조각 모음합니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-242">This service defragments the previously opened NOR flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="893b3-243">조각 모음 프로세스는 사용 가능한 섹터 및 블록의 수를 최대화합니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-243">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="893b3-244">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="893b3-244">Input Parameters</span></span>

- <span data-ttu-id="893b3-245">*nor_flash*: NOR 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-245">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="893b3-246">*max_blocks*: 최대 블록 수입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-246">*max_blocks*: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="893b3-247">반환 값</span><span class="sxs-lookup"><span data-stu-id="893b3-247">Return Values</span></span>

- <span data-ttu-id="893b3-248">**LX_SUCCESS**: (0x00) 성공적인 요청</span><span class="sxs-lookup"><span data-stu-id="893b3-248">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="893b3-249">**LX_ERROR**: (0x01) 플래시 인스턴스를 조각 모음하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-249">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="893b3-250">허용 위치</span><span class="sxs-lookup"><span data-stu-id="893b3-250">Allowed From</span></span>

<span data-ttu-id="893b3-251">스레드</span><span class="sxs-lookup"><span data-stu-id="893b3-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="893b3-252">예제</span><span class="sxs-lookup"><span data-stu-id="893b3-252">Example</span></span>

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="893b3-253">참고 항목</span><span class="sxs-lookup"><span data-stu-id="893b3-253">See Also</span></span>

- <span data-ttu-id="893b3-254">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="893b3-254">lx_nor_flash_close</span></span>
- <span data-ttu-id="893b3-255">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-255">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="893b3-256">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="893b3-256">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="893b3-257">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="893b3-257">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="893b3-258">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="893b3-258">lx_nor_flash_open</span></span>
- <span data-ttu-id="893b3-259">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="893b3-259">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="893b3-260">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="893b3-260">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="893b3-261">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="893b3-261">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_read"></a><span data-ttu-id="893b3-262">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="893b3-262">lx_nor_flash_sector_read</span></span>

<span data-ttu-id="893b3-263">NOR 플래시 섹터 읽기</span><span class="sxs-lookup"><span data-stu-id="893b3-263">Read NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="893b3-264">프로토타입</span><span class="sxs-lookup"><span data-stu-id="893b3-264">Prototype</span></span>

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="893b3-265">Description</span><span class="sxs-lookup"><span data-stu-id="893b3-265">Description</span></span>

<span data-ttu-id="893b3-266">이 서비스는 NOR 플래시 인스턴스에서 논리 섹터를 읽고, 성공하면 제공된 버퍼의 내용을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-266">This service reads the logical sector from the NOR flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="893b3-267">NOR 섹터 크기는 항상 512바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-267">Note that NOR sector size is always 512 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="893b3-268">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="893b3-268">Input Parameters</span></span>

- <span data-ttu-id="893b3-269">*nor_flash* NOR 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-269">*nor_flash* NOR flash instance pointer.</span></span>
- <span data-ttu-id="893b3-270">*logical_sector*: 읽을 논리 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-270">*logical_sector*: Logical sector to read.</span></span>
- <span data-ttu-id="893b3-271">*buffer*: 논리 섹터 내용의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-271">*buffer*: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="893b3-272">버퍼는 512바이트로 간주되고 ULONG 액세스에 맞게 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-272">Note that the buffer is assumed to be 512 bytes and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="893b3-273">반환 값</span><span class="sxs-lookup"><span data-stu-id="893b3-273">Return Values</span></span>

- <span data-ttu-id="893b3-274">**LX_SUCCESS**: (0x00) 성공적인 요청</span><span class="sxs-lookup"><span data-stu-id="893b3-274">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="893b3-275">**LX_ERROR**: (0x01) NOR 플래시 섹터를 읽는 동안 오류 발생</span><span class="sxs-lookup"><span data-stu-id="893b3-275">**LX_ERROR**: (0x01) Error reading NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="893b3-276">허용 위치</span><span class="sxs-lookup"><span data-stu-id="893b3-276">Allowed From</span></span>

<span data-ttu-id="893b3-277">스레드</span><span class="sxs-lookup"><span data-stu-id="893b3-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="893b3-278">예제</span><span class="sxs-lookup"><span data-stu-id="893b3-278">Example</span></span>

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="893b3-279">참고 항목</span><span class="sxs-lookup"><span data-stu-id="893b3-279">See Also</span></span>

- <span data-ttu-id="893b3-280">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="893b3-280">lx_nor_flash_close</span></span>
- <span data-ttu-id="893b3-281">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-281">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="893b3-282">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="893b3-282">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="893b3-283">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="893b3-283">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="893b3-284">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="893b3-284">lx_nor_flash_open</span></span>
- <span data-ttu-id="893b3-285">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-285">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="893b3-286">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="893b3-286">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="893b3-287">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="893b3-287">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_release"></a><span data-ttu-id="893b3-288">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="893b3-288">lx_nor_flash_sector_release</span></span>

<span data-ttu-id="893b3-289">NOR 플래시 섹터 해제</span><span class="sxs-lookup"><span data-stu-id="893b3-289">Release NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="893b3-290">프로토타입</span><span class="sxs-lookup"><span data-stu-id="893b3-290">Prototype</span></span>

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="893b3-291">Description</span><span class="sxs-lookup"><span data-stu-id="893b3-291">Description</span></span>

<span data-ttu-id="893b3-292">이 서비스는 NOR 플래시 인스턴스에서 논리 섹터 매핑을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-292">This service releases the logical sector mapping in the NOR flash instance.</span></span> <span data-ttu-id="893b3-293">사용되지 않을 때 논리 섹터를 해제하면 LevelX 사용 평균화를 보다 효율적으로 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-293">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="893b3-294">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="893b3-294">Input Parameters</span></span>

- <span data-ttu-id="893b3-295">*nor_flash*: NOR 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-295">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="893b3-296">*logical_sector*: 해제할 논리 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-296">*logical_sector*: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="893b3-297">반환 값</span><span class="sxs-lookup"><span data-stu-id="893b3-297">Return Values</span></span>

- <span data-ttu-id="893b3-298">**LX_SUCCESS**: (0x00) 성공적인 요청</span><span class="sxs-lookup"><span data-stu-id="893b3-298">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="893b3-299">**LX_ERROR**: (0x01) NOR 플래시 섹터 쓰기 오류</span><span class="sxs-lookup"><span data-stu-id="893b3-299">**LX_ERROR**: (0x01) Error NOR flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="893b3-300">허용 위치</span><span class="sxs-lookup"><span data-stu-id="893b3-300">Allowed From</span></span>

<span data-ttu-id="893b3-301">스레드</span><span class="sxs-lookup"><span data-stu-id="893b3-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="893b3-302">예제</span><span class="sxs-lookup"><span data-stu-id="893b3-302">Example</span></span>

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="893b3-303">참고 항목</span><span class="sxs-lookup"><span data-stu-id="893b3-303">See Also</span></span>

- <span data-ttu-id="893b3-304">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="893b3-304">lx_nor_flash_close</span></span>
- <span data-ttu-id="893b3-305">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-305">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="893b3-306">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="893b3-306">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="893b3-307">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="893b3-307">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="893b3-308">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="893b3-308">lx_nor_flash_open</span></span>
- <span data-ttu-id="893b3-309">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-309">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="893b3-310">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="893b3-310">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="893b3-311">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="893b3-311">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_write"></a><span data-ttu-id="893b3-312">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="893b3-312">lx_nor_flash_sector_write</span></span>

<span data-ttu-id="893b3-313">NOR 플래시 섹터 쓰기</span><span class="sxs-lookup"><span data-stu-id="893b3-313">Write NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="893b3-314">프로토타입</span><span class="sxs-lookup"><span data-stu-id="893b3-314">Prototype</span></span>

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="893b3-315">Description</span><span class="sxs-lookup"><span data-stu-id="893b3-315">Description</span></span>

<span data-ttu-id="893b3-316">이 서비스는 NOR 플래시 인스턴스에 지정된 논리 섹터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-316">This service writes the specified logical sector in the NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="893b3-317">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="893b3-317">Input Parameters</span></span>

- <span data-ttu-id="893b3-318">*nor_flash*: NOR 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-318">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="893b3-319">*logical_sector*: 쓸 논리 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-319">*logical_sector*: Logical sector to write.</span></span>
- <span data-ttu-id="893b3-320">*buffer*: 논리 섹터 내용에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-320">*buffer*: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="893b3-321">버퍼는 ULONG 액세스에 맞게 정렬된 512바이트로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-321">Note that the buffer is assumed to be 512 bytes aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="893b3-322">반환 값</span><span class="sxs-lookup"><span data-stu-id="893b3-322">Return Values</span></span>

- <span data-ttu-id="893b3-323">**LX_SUCCESS**: (0x00) 성공적인 요청</span><span class="sxs-lookup"><span data-stu-id="893b3-323">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="893b3-324">**LX_NO_SECTORS**: (0x02) 쓰기를 수행하는 데 사용할 수 있는 더 이상의 여유 섹터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="893b3-324">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="893b3-325">**LX_ERROR**: (0x01) NOR 플래시 섹터를 해제하는 동안 오류 발생</span><span class="sxs-lookup"><span data-stu-id="893b3-325">**LX_ERROR**: (0x01) Error releasing NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="893b3-326">허용 위치</span><span class="sxs-lookup"><span data-stu-id="893b3-326">Allowed From</span></span>

<span data-ttu-id="893b3-327">스레드</span><span class="sxs-lookup"><span data-stu-id="893b3-327">Threads</span></span>

### <a name="example"></a><span data-ttu-id="893b3-328">예제</span><span class="sxs-lookup"><span data-stu-id="893b3-328">Example</span></span>

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="893b3-329">참고 항목</span><span class="sxs-lookup"><span data-stu-id="893b3-329">See Also</span></span>

- <span data-ttu-id="893b3-330">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="893b3-330">lx_nor_flash_close</span></span>
- <span data-ttu-id="893b3-331">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-331">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="893b3-332">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="893b3-332">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="893b3-333">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="893b3-333">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="893b3-334">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="893b3-334">lx_nor_flash_open</span></span>
- <span data-ttu-id="893b3-335">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="893b3-335">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="893b3-336">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="893b3-336">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="893b3-337">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="893b3-337">lx_nor_flash_sector_release</span></span>
