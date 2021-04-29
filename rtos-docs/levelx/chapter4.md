---
title: 4장 - Azure RTOS LevelX NAND API
description: 애플리케이션에 사용할 수 있는 Azure RTOS LevelX NAND API.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73bb94768396b4b8461791a164a102d1f8ef159f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811880"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a><span data-ttu-id="5f0e2-103">4장 - Azure RTOS LevelX NAND API</span><span class="sxs-lookup"><span data-stu-id="5f0e2-103">Chapter 4 - Azure RTOS LevelX NAND APIs</span></span>

<span data-ttu-id="5f0e2-104">애플리케이션에 사용할 수 있는 Azure RTOS LevelX NAND API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-104">The Azure RTOS LevelX NAND APIs available to the application are:</span></span>

- <span data-ttu-id="5f0e2-105">***lx_nand_flash_close** _: _NAND* 플래시 인스턴스를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-105">***lx_nand_flash_close** _: _Close NAND flash instance*</span></span>
- <span data-ttu-id="5f0e2-106">***lx_nand_flash_defragment** _: _NAND* 플래시 인스턴스를 조각 모음합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-106">***lx_nand_flash_defragment** _: _Defragment NAND flash instance*</span></span>
- <span data-ttu-id="5f0e2-107">***lx_nand_flash_extended_cache_enable** _: 확장된 _NAND* 캐시 사용/사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-107">***lx_nand_flash_extended_cache_enable** _: _Enable/disable extended NAND cache*</span></span>
- <span data-ttu-id="5f0e2-108">***lx_nand_flash_initialize** _: _NAND* 플래시 지원을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-108">***lx_nand_flash_initialize** _: _Initialize NAND flash support*</span></span>
- <span data-ttu-id="5f0e2-109">***lx_nand_flash_open** _: _NAND* 플래시 인스턴스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-109">***lx_nand_flash_open** _: _Open NAND flash instance*</span></span>
- <span data-ttu-id="5f0e2-110">***lx_nand_flash_page_ecc_check** _: 수정 사항과 함께 _ECC* 오류가 있는지 페이지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-110">***lx_nand_flash_page_ecc_check** _: _Check page for ECC errors with correction*</span></span>
- <span data-ttu-id="5f0e2-111">***lx_nand_flash_page_ecc_compute** _: 페이지에 대한 _ECC*를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-111">***lx_nand_flash_page_ecc_compute** _: _Computes ECC for page*</span></span>
- <span data-ttu-id="5f0e2-112">***lx_nand_flash_partial_defragment** _: _NAND* 플래시 인스턴스를 부분 조각 모음합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-112">***lx_nand_flash_partial_defragment** _: _Partial defragment of NAND flash instance*</span></span>
- <span data-ttu-id="5f0e2-113">***lx_nand_flash_sector_read** _: _NAND* 플래시 섹터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-113">***lx_nand_flash_sector_read** _: _Read NAND flash sector*</span></span>
- <span data-ttu-id="5f0e2-114">***lx_nand_flash_sector_release** _: _NAND* 플래시 섹터를 릴리스합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-114">***lx_nand_flash_sector_release** _: _Release NAND flash sector*</span></span>
- <span data-ttu-id="5f0e2-115">***lx_nand_flash_sector_write** _: _NAND* 플래시 섹터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-115">***lx_nand_flash_sector_write** _: _Write NAND flash sector*</span></span>

## <a name="lx_nand_flash_close"></a><span data-ttu-id="5f0e2-116">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="5f0e2-116">lx_nand_flash_close</span></span>

<span data-ttu-id="5f0e2-117">NAND 플래시 인스턴스를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-117">Close NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5f0e2-118">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5f0e2-118">Prototype</span></span>

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="5f0e2-119">Description</span><span class="sxs-lookup"><span data-stu-id="5f0e2-119">Description</span></span>

<span data-ttu-id="5f0e2-120">이 서비스는 이전에 열었던 NAND 플래시 인스턴스를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-120">This service closes the previously opened NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5f0e2-121">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f0e2-121">Input Parameters</span></span>

- <span data-ttu-id="5f0e2-122">**nand_flash**: NAND 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-122">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="5f0e2-123">반환 값</span><span class="sxs-lookup"><span data-stu-id="5f0e2-123">Return Values</span></span>

- <span data-ttu-id="5f0e2-124">**LX_SUCCESS**: (0x00) 요청에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-124">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="5f0e2-125">**LX_ERROR**: (0x01) 플래시 인스턴스를 닫는 중 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-125">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5f0e2-126">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="5f0e2-126">Allowed From</span></span>

<span data-ttu-id="5f0e2-127">스레드</span><span class="sxs-lookup"><span data-stu-id="5f0e2-127">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5f0e2-128">예제</span><span class="sxs-lookup"><span data-stu-id="5f0e2-128">Example</span></span>

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="5f0e2-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f0e2-129">See Also</span></span>

- <span data-ttu-id="5f0e2-130">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-130">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="5f0e2-131">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="5f0e2-131">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="5f0e2-132">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="5f0e2-132">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="5f0e2-133">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="5f0e2-133">lx_nand_flash_open</span></span>
- <span data-ttu-id="5f0e2-134">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="5f0e2-134">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="5f0e2-135">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="5f0e2-135">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="5f0e2-136">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-136">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="5f0e2-137">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="5f0e2-137">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="5f0e2-138">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="5f0e2-138">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="5f0e2-139">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="5f0e2-139">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_defragment"></a><span data-ttu-id="5f0e2-140">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-140">lx_nand_flash_defragment</span></span>

<span data-ttu-id="5f0e2-141">NAND 플래시 인스턴스를 조각 모음합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-141">Defragment NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5f0e2-142">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5f0e2-142">Prototype</span></span>

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="5f0e2-143">Description</span><span class="sxs-lookup"><span data-stu-id="5f0e2-143">Description</span></span>

<span data-ttu-id="5f0e2-144">이 서비스는 이전에 열었던 NAND 플래시 인스턴스의 조각을 모읍니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-144">This service defragments the previously opened NAND flash instance.</span></span> <span data-ttu-id="5f0e2-145">조각 모음 프로세스는 사용 가능한 페이지와 블록 수를 최대화합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-145">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5f0e2-146">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f0e2-146">Input Parameters</span></span>

- <span data-ttu-id="5f0e2-147">**nand_flash**: NAND 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-147">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="5f0e2-148">반환 값</span><span class="sxs-lookup"><span data-stu-id="5f0e2-148">Return Values</span></span>

- <span data-ttu-id="5f0e2-149">**LX_SUCCESS**: (0x00) 요청에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-149">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="5f0e2-150">**LX_ERROR**: (0x01) 플래시 인스턴스를 조각 모음하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-150">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5f0e2-151">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="5f0e2-151">Allowed From</span></span>

<span data-ttu-id="5f0e2-152">스레드</span><span class="sxs-lookup"><span data-stu-id="5f0e2-152">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5f0e2-153">예제</span><span class="sxs-lookup"><span data-stu-id="5f0e2-153">Example</span></span>

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="5f0e2-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f0e2-154">See Also</span></span>

- <span data-ttu-id="5f0e2-155">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="5f0e2-155">lx_nand_flash_close</span></span>
- <span data-ttu-id="5f0e2-156">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="5f0e2-156">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="5f0e2-157">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="5f0e2-157">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="5f0e2-158">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="5f0e2-158">lx_nand_flash_open</span></span>
- <span data-ttu-id="5f0e2-159">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="5f0e2-159">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="5f0e2-160">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="5f0e2-160">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="5f0e2-161">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-161">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="5f0e2-162">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="5f0e2-162">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="5f0e2-163">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="5f0e2-163">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="5f0e2-164">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="5f0e2-164">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_extended_cache_enable"></a><span data-ttu-id="5f0e2-165">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="5f0e2-165">lx_nand_flash_extended_cache_enable</span></span>

<span data-ttu-id="5f0e2-166">확장된 NAND 캐시를 사용/사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-166">Enable/disable extended NAND cache</span></span>

### <a name="prototype"></a><span data-ttu-id="5f0e2-167">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5f0e2-167">Prototype</span></span>

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="5f0e2-168">Description</span><span class="sxs-lookup"><span data-stu-id="5f0e2-168">Description</span></span>

<span data-ttu-id="5f0e2-169">이 서비스는 애플리케이션에서 제공하는 메모리를 사용하여 RAM에서 캐시 계층을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-169">This service implements a cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="5f0e2-170">전체 캐시 작업에 필요한 총 메모리 양을 다음과 같이 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-170">The total amount of memory required for full cache operation can be calculated as follows:</span></span>

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

<span data-ttu-id="5f0e2-171">제공된 메모리가 전체 NAND 캐시를 수용할 수 있을 정도로 충분히 크지 않은 경우 이 루틴은 제공된 메모리에 따라 가능한 한 많은 NAND 플래시 캐시를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-171">If the supplied memory is not large enough to accommodate the full NAND cache, this routine will enable as much of the NAND flash cache as possible based on the memory supplied.</span></span>

<span data-ttu-id="5f0e2-172">지정된 메모리 주소가 NULL인 경우에는 NAND 캐시가 사용되지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-172">The NAND cache is disabled if the memory address specified is NULL.</span></span> <span data-ttu-id="5f0e2-173">따라서 일시적으로 NAND 캐시가 사용될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-173">Hence, the NAND cache maybe be used in a temporary fashion.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5f0e2-174">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f0e2-174">Input Parameters</span></span>

- <span data-ttu-id="5f0e2-175">**nand_flash**: NAND 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-175">**nand_flash**: NAND flash instance pointer.</span></span>  
- <span data-ttu-id="5f0e2-176">**memory**: 캐시 메모리에 대한 시작 주소로, ULONG 액세스에 맞게 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-176">**memory**: Starting address for cache memory aligned for ULONG access.</span></span> <span data-ttu-id="5f0e2-177">LX_NULL 값은 캐시를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-177">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="5f0e2-178">**size**: 제공된 메모리의 크기입니다(바이트 단위).</span><span class="sxs-lookup"><span data-stu-id="5f0e2-178">**size**: The size in bytes of the memory supplied.</span></span>

### <a name="return-values"></a><span data-ttu-id="5f0e2-179">반환 값</span><span class="sxs-lookup"><span data-stu-id="5f0e2-179">Return Values</span></span>

- <span data-ttu-id="5f0e2-180">**LX_SUCCESS**: (0x00) 요청에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-180">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="5f0e2-181">**LX_ERROR**: (0x01) NAND 캐시의 한 가지 요소를 위한 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-181">**LX_ERROR**: (0x01) Not enough memory for one element of the NAND cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5f0e2-182">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="5f0e2-182">Allowed From</span></span>

<span data-ttu-id="5f0e2-183">스레드</span><span class="sxs-lookup"><span data-stu-id="5f0e2-183">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5f0e2-184">예제</span><span class="sxs-lookup"><span data-stu-id="5f0e2-184">Example</span></span>

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="5f0e2-185">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f0e2-185">See Also</span></span>

- <span data-ttu-id="5f0e2-186">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="5f0e2-186">lx_nand_flash_close</span></span>
- <span data-ttu-id="5f0e2-187">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-187">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="5f0e2-188">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="5f0e2-188">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="5f0e2-189">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="5f0e2-189">lx_nand_flash_open</span></span>
- <span data-ttu-id="5f0e2-190">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="5f0e2-190">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="5f0e2-191">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="5f0e2-191">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="5f0e2-192">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-192">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="5f0e2-193">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="5f0e2-193">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="5f0e2-194">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="5f0e2-194">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="5f0e2-195">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="5f0e2-195">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_initialize"></a><span data-ttu-id="5f0e2-196">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="5f0e2-196">lx_nand_flash_initialize</span></span>

<span data-ttu-id="5f0e2-197">NAND 플래시 지원을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-197">Initialize NAND flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="5f0e2-198">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5f0e2-198">Prototype</span></span>

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="5f0e2-199">Description</span><span class="sxs-lookup"><span data-stu-id="5f0e2-199">Description</span></span>

<span data-ttu-id="5f0e2-200">이 서비스는 LevelX NAND 플래시 지원을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-200">This service initializes LevelX NAND flash support.</span></span> <span data-ttu-id="5f0e2-201">다른 LevelX NAND API보다 먼저 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-201">It must be called before any other LevelX NAND APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5f0e2-202">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f0e2-202">Input Parameters</span></span>

- <span data-ttu-id="5f0e2-203">**없음**</span><span class="sxs-lookup"><span data-stu-id="5f0e2-203">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="5f0e2-204">반환 값</span><span class="sxs-lookup"><span data-stu-id="5f0e2-204">Return Values</span></span>

- <span data-ttu-id="5f0e2-205">**LX_SUCCESS**: (0x00) 요청에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-205">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="5f0e2-206">**LX_ERROR**: (0x01) NAND 플래시 지원을 초기화하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-206">**LX_ERROR**: (0x01) Error initializing NAND flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5f0e2-207">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="5f0e2-207">Allowed From</span></span>

<span data-ttu-id="5f0e2-208">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="5f0e2-208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="5f0e2-209">예제</span><span class="sxs-lookup"><span data-stu-id="5f0e2-209">Example</span></span>

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="5f0e2-210">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f0e2-210">See Also</span></span>

- <span data-ttu-id="5f0e2-211">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="5f0e2-211">lx_nand_flash_close</span></span>
- <span data-ttu-id="5f0e2-212">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-212">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="5f0e2-213">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="5f0e2-213">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="5f0e2-214">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="5f0e2-214">lx_nand_flash_open</span></span>
- <span data-ttu-id="5f0e2-215">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="5f0e2-215">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="5f0e2-216">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="5f0e2-216">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="5f0e2-217">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-217">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="5f0e2-218">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="5f0e2-218">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="5f0e2-219">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="5f0e2-219">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="5f0e2-220">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="5f0e2-220">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_open"></a><span data-ttu-id="5f0e2-221">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="5f0e2-221">lx_nand_flash_open</span></span>

<span data-ttu-id="5f0e2-222">NAND 플래시 인스턴스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-222">Open NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5f0e2-223">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5f0e2-223">Prototype</span></span>

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a><span data-ttu-id="5f0e2-224">Description</span><span class="sxs-lookup"><span data-stu-id="5f0e2-224">Description</span></span>

<span data-ttu-id="5f0e2-225">이 서비스는 지정된 NAND 플래시 제어 블록과 드라이버 초기화 함수를 사용하여 NAND 플래시 인스턴스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-225">This service opens a NAND flash instance with the specified NAND flash control block and driver initialization function.</span></span> <span data-ttu-id="5f0e2-226">드라이버 초기화 함수는 이 NAND 플래시 인스턴스와 연결된 NAND 하드웨어의 블록/페이지를 읽고, 쓰고, 지우기 위한 다양한 함수 포인터를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-226">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks/pages of the NAND hardware associated with this NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5f0e2-227">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f0e2-227">Input Parameters</span></span>

- <span data-ttu-id="5f0e2-228">**nand_flash**: NAND 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-228">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="5f0e2-229">**name**: NAND 플래시 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-229">**name**: Name of NAND flash instance.</span></span>
- <span data-ttu-id="5f0e2-230">**nor_driver_initialize**: NAND 플래시 드라이버 초기화 함수에 대한 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-230">**nand_driver_initialize**: Function pointer to NAND flash driver initialization function.</span></span> <span data-ttu-id="5f0e2-231">NAND 플래시 드라이버 역할에 대한 자세한 내용은 이 가이드의 3장을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-231">Please refer to Chapter 3 of this guide for more details on NAND flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="5f0e2-232">반환 값</span><span class="sxs-lookup"><span data-stu-id="5f0e2-232">Return Values</span></span>

- <span data-ttu-id="5f0e2-233">**LX_SUCCESS**: (0x00) 요청에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-233">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="5f0e2-234">**LX_ERROR**: (0x01) NAND 플래시 인스턴스를 여는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-234">**LX_ERROR**: (0x01) Error opening NAND flash instance.</span></span>
- <span data-ttu-id="5f0e2-235">**LX_NO_MEMORY**: (0x08) 드라이버가 RAM으로 페이지 하나를 읽기 위한 버퍼를 제공하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-235">**LX_NO_MEMORY**: (0x08) Driver did not provide buffer for reading one page into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5f0e2-236">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="5f0e2-236">Allowed From</span></span>

<span data-ttu-id="5f0e2-237">스레드</span><span class="sxs-lookup"><span data-stu-id="5f0e2-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5f0e2-238">예제</span><span class="sxs-lookup"><span data-stu-id="5f0e2-238">Example</span></span>

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="5f0e2-239">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f0e2-239">See Also</span></span>

- <span data-ttu-id="5f0e2-240">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="5f0e2-240">lx_nand_flash_close</span></span>
- <span data-ttu-id="5f0e2-241">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-241">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="5f0e2-242">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="5f0e2-242">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="5f0e2-243">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="5f0e2-243">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="5f0e2-244">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="5f0e2-244">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="5f0e2-245">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="5f0e2-245">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="5f0e2-246">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-246">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="5f0e2-247">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="5f0e2-247">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="5f0e2-248">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="5f0e2-248">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="5f0e2-249">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="5f0e2-249">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_check"></a><span data-ttu-id="5f0e2-250">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="5f0e2-250">lx_nand_flash_page_ecc_check</span></span>

<span data-ttu-id="5f0e2-251">수정 사항과 함께 ECC 오류가 있는지 페이지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-251">Check page for ECC errors with correction</span></span>

### <a name="prototype"></a><span data-ttu-id="5f0e2-252">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5f0e2-252">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="5f0e2-253">Description</span><span class="sxs-lookup"><span data-stu-id="5f0e2-253">Description</span></span>

<span data-ttu-id="5f0e2-254">이 서비스는 제공된 ECC를 사용하여 제공된 NAND 페이지 버퍼의 무결성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-254">This service verifies the integrity of the supplied NAND page buffer with the supplied ECC.</span></span> <span data-ttu-id="5f0e2-255">(NAND 플래시 인스턴스 포인터에 정의된) 페이지 크기는 256바이트의 배수로 가정되고 제공된 ECC 코드는 페이지의 각 256바이트 부분에서 1비트 오류를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-255">Page size (defined in the NAND flash instance pointer) is assumed to be a multiple of 256-bytes and the ECC code supplied is capable of correcting a 1 bit error in each 256-byte portion of the page.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5f0e2-256">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f0e2-256">Input Parameters</span></span>

- <span data-ttu-id="5f0e2-257">**nand_flash**: NAND 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-257">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="5f0e2-258">**page_buffer**: NAND 플래시 페이지 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-258">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="5f0e2-259">**ecc_buffer**: NAND 플래시 페이지의 ECC에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-259">**ecc_buffer**: Pointer to ECC for NAND flash page.</span></span> <span data-ttu-id="5f0e2-260">페이지의 256바이트 부분마다 ECC 3바이트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-260">Note that there are 3 ECC bytes per 256-byte portion of the page.</span></span>

### <a name="return-values"></a><span data-ttu-id="5f0e2-261">반환 값</span><span class="sxs-lookup"><span data-stu-id="5f0e2-261">Return Values</span></span>

- <span data-ttu-id="5f0e2-262">**LX_SUCCESS**: (0x00) NAND 페이지에 오류가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-262">**LX_SUCCESS**: (0x00) NAND page has no errors.</span></span>
- <span data-ttu-id="5f0e2-263">**LX_NAND_ERROR_CORRECTED**: (0x06) NAND 페이지에서 1비트 오류가 한 개 이상 수정되었으며, 수정 사항은 페이지 버퍼에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-263">**LX_NAND_ERROR_CORRECTED**: (0x06) One or more 1-bit errors were corrected in the NAND page—correction(s) are in the page buffer.</span></span>
- <span data-ttu-id="5f0e2-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0x07) NAND 페이지에 오류가 너무 많아 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0x07) Too many errors to correct on the NAND page.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5f0e2-265">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="5f0e2-265">Allowed From</span></span>

<span data-ttu-id="5f0e2-266">LevelX 드라이버</span><span class="sxs-lookup"><span data-stu-id="5f0e2-266">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="5f0e2-267">예제</span><span class="sxs-lookup"><span data-stu-id="5f0e2-267">Example</span></span>

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a><span data-ttu-id="5f0e2-268">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f0e2-268">See Also</span></span>

- <span data-ttu-id="5f0e2-269">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="5f0e2-269">lx_nand_flash_close</span></span>
- <span data-ttu-id="5f0e2-270">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-270">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="5f0e2-271">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="5f0e2-271">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="5f0e2-272">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="5f0e2-272">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="5f0e2-273">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="5f0e2-273">lx_nand_flash_open</span></span>
- <span data-ttu-id="5f0e2-274">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="5f0e2-274">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="5f0e2-275">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-275">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="5f0e2-276">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="5f0e2-276">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="5f0e2-277">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="5f0e2-277">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="5f0e2-278">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="5f0e2-278">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_compute"></a><span data-ttu-id="5f0e2-279">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="5f0e2-279">lx_nand_flash_page_ecc_compute</span></span>

<span data-ttu-id="5f0e2-280">페이지의 ECC를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-280">Compute ECC for page</span></span>

### <a name="prototype"></a><span data-ttu-id="5f0e2-281">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5f0e2-281">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="5f0e2-282">Description</span><span class="sxs-lookup"><span data-stu-id="5f0e2-282">Description</span></span>

<span data-ttu-id="5f0e2-283">이 서비스는 제공된 NAND 페이지 버퍼의 ECC를 계산하고 제공된 ECC 버퍼에서 ECC를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-283">This service computes the ECC of the supplied NAND page buffer and returns the ECC in the supplied ECC buffer.</span></span> <span data-ttu-id="5f0e2-284">페이지 크기는 (NAND 플래시 인스턴스 포인터에 정의된) 256바이트의 배수로 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-284">Page size is assume to be a multiple of 256-bytes (defined in the NAND flash instance pointer).</span></span> <span data-ttu-id="5f0e2-285">ECC 코드는 나중에 읽을 때 페이지의 무결성을 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-285">The ECC code is used to verify the integrity of the page when it is read at a later time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5f0e2-286">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f0e2-286">Input Parameters</span></span>

- <span data-ttu-id="5f0e2-287">**nand_flash**: NAND 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-287">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="5f0e2-288">**page_buffer**: NAND 플래시 페이지 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-288">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="5f0e2-289">**ecc_buffer**: NAND 플래시 페이지의 ECC 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-289">**ecc_buffer**: Pointer to destination for ECC of the NAND flash page.</span></span> <span data-ttu-id="5f0e2-290">페이지의 256바이트 부분마다 ECC 스토리지는 3바이트여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-290">Note that must be 3 bytes of ECC storage per 256-byte portion of the page.</span></span> <span data-ttu-id="5f0e2-291">예를 들어 2048바이트 페이지에는 ECC에 24바이트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-291">For example, a 2048 byte page would require 24 bytes for the ECC.</span></span>

### <a name="return-values"></a><span data-ttu-id="5f0e2-292">반환 값</span><span class="sxs-lookup"><span data-stu-id="5f0e2-292">Return Values</span></span>

- <span data-ttu-id="5f0e2-293">**LX_SUCCESS**: (0x00) ECC가 계산되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-293">**LX_SUCCESS**: (0x00) ECC successfully calculated.</span></span>
- <span data-ttu-id="5f0e2-294">**LX_ERROR**: (0x01) ECC를 계산하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-294">**LX_ERROR**: (0x01) Error calculating ECC.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5f0e2-295">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="5f0e2-295">Allowed From</span></span>

<span data-ttu-id="5f0e2-296">LevelX 드라이버</span><span class="sxs-lookup"><span data-stu-id="5f0e2-296">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="5f0e2-297">예제</span><span class="sxs-lookup"><span data-stu-id="5f0e2-297">Example</span></span>

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a><span data-ttu-id="5f0e2-298">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f0e2-298">See Also</span></span>

- <span data-ttu-id="5f0e2-299">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="5f0e2-299">lx_nand_flash_close</span></span>
- <span data-ttu-id="5f0e2-300">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-300">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="5f0e2-301">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="5f0e2-301">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="5f0e2-302">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="5f0e2-302">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="5f0e2-303">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="5f0e2-303">lx_nand_flash_open</span></span>
- <span data-ttu-id="5f0e2-304">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="5f0e2-304">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="5f0e2-305">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-305">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="5f0e2-306">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="5f0e2-306">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="5f0e2-307">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="5f0e2-307">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="5f0e2-308">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="5f0e2-308">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_partial_defragment"></a><span data-ttu-id="5f0e2-309">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-309">lx_nand_flash_partial_defragment</span></span>

<span data-ttu-id="5f0e2-310">NAND 플래시 인스턴스를 부분 조각 모음합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-310">Partial defragment of NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5f0e2-311">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5f0e2-311">Prototype</span></span>

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="5f0e2-312">Description</span><span class="sxs-lookup"><span data-stu-id="5f0e2-312">Description</span></span>

<span data-ttu-id="5f0e2-313">이 서비스는 이전에 열었던 NAND 플래시 인스턴스를 지정된 최대 블록 수까지 조각 모음합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-313">This service defragments the previously opened NAND flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="5f0e2-314">조각 모음 프로세스는 사용 가능한 페이지와 블록 수를 최대화합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-314">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5f0e2-315">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f0e2-315">Input Parameters</span></span>

- <span data-ttu-id="5f0e2-316">**nand_flash**: NAND 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-316">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="5f0e2-317">**max_blocks**: 최대 블록 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-317">**max_blocks**: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="5f0e2-318">반환 값</span><span class="sxs-lookup"><span data-stu-id="5f0e2-318">Return Values</span></span>

- <span data-ttu-id="5f0e2-319">**LX_SUCCESS**: (0x00) 요청에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-319">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="5f0e2-320">**LX_ERROR**: (0x01) 플래시 인스턴스를 조각 모음하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-320">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5f0e2-321">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="5f0e2-321">Allowed From</span></span>

<span data-ttu-id="5f0e2-322">스레드</span><span class="sxs-lookup"><span data-stu-id="5f0e2-322">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5f0e2-323">예제</span><span class="sxs-lookup"><span data-stu-id="5f0e2-323">Example</span></span>

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="5f0e2-324">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f0e2-324">See Also</span></span>

- <span data-ttu-id="5f0e2-325">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="5f0e2-325">lx_nand_flash_close</span></span>
- <span data-ttu-id="5f0e2-326">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-326">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="5f0e2-327">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="5f0e2-327">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="5f0e2-328">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="5f0e2-328">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="5f0e2-329">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="5f0e2-329">lx_nand_flash_open</span></span>
- <span data-ttu-id="5f0e2-330">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="5f0e2-330">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="5f0e2-331">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="5f0e2-331">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="5f0e2-332">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="5f0e2-332">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="5f0e2-333">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="5f0e2-333">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="5f0e2-334">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="5f0e2-334">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_read"></a><span data-ttu-id="5f0e2-335">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="5f0e2-335">lx_nand_flash_sector_read</span></span>

<span data-ttu-id="5f0e2-336">NAND 플래시 섹터 읽기</span><span class="sxs-lookup"><span data-stu-id="5f0e2-336">Read NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="5f0e2-337">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5f0e2-337">Prototype</span></span>

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="5f0e2-338">Description</span><span class="sxs-lookup"><span data-stu-id="5f0e2-338">Description</span></span>

<span data-ttu-id="5f0e2-339">이 서비스는 NAND 플래시 인스턴스에서 논리 섹터를 읽고, 성공하면 제공된 버퍼의 내용을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-339">This service reads the logical sector from the NAND flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="5f0e2-340">NAND 섹터 크기는 항상 기본 NAND 하드웨어의 페이지 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-340">Note that NAND sector size is always the page size of the underlying NAND hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5f0e2-341">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f0e2-341">Input Parameters</span></span>

- <span data-ttu-id="5f0e2-342">**nand_flash**: NAND 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-342">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="5f0e2-343">**logical_sector**: 읽을 논리 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-343">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="5f0e2-344">**buffer**: 논리 섹터 내용의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-344">**buffer**: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="5f0e2-345">버퍼는 NAND 플래시 페이지 크기이고 ULONG 액세스를 위해 정렬된 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-345">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="5f0e2-346">반환 값</span><span class="sxs-lookup"><span data-stu-id="5f0e2-346">Return Values</span></span>

- <span data-ttu-id="5f0e2-347">**LX_SUCCESS**: (0x00) 요청에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-347">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="5f0e2-348">**LX_ERROR**: (0x01) NAND 플래시 섹터를 읽는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-348">**LX_ERROR**: (0x01) Error reading NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5f0e2-349">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="5f0e2-349">Allowed From</span></span>

<span data-ttu-id="5f0e2-350">스레드</span><span class="sxs-lookup"><span data-stu-id="5f0e2-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5f0e2-351">예제</span><span class="sxs-lookup"><span data-stu-id="5f0e2-351">Example</span></span>

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="5f0e2-352">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f0e2-352">See Also</span></span>

- <span data-ttu-id="5f0e2-353">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="5f0e2-353">lx_nand_flash_close</span></span>
- <span data-ttu-id="5f0e2-354">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-354">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="5f0e2-355">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="5f0e2-355">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="5f0e2-356">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="5f0e2-356">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="5f0e2-357">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="5f0e2-357">lx_nand_flash_open</span></span>
- <span data-ttu-id="5f0e2-358">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="5f0e2-358">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="5f0e2-359">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="5f0e2-359">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="5f0e2-360">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-360">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="5f0e2-361">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="5f0e2-361">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="5f0e2-362">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="5f0e2-362">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_release"></a><span data-ttu-id="5f0e2-363">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="5f0e2-363">lx_nand_flash_sector_release</span></span>

<span data-ttu-id="5f0e2-364">NAND 플래시 섹터를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-364">Release NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="5f0e2-365">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5f0e2-365">Prototype</span></span>

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="5f0e2-366">Description</span><span class="sxs-lookup"><span data-stu-id="5f0e2-366">Description</span></span>

<span data-ttu-id="5f0e2-367">이 서비스는 NAND 플래시 인스턴스에서 논리 섹터 매핑을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-367">This service releases the logical sector mapping in the NAND flash instance.</span></span> <span data-ttu-id="5f0e2-368">사용되지 않을 때 논리 섹터를 해제하면 LevelX 사용 평균화를 보다 효율적으로 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-368">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5f0e2-369">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f0e2-369">Input Parameters</span></span>

- <span data-ttu-id="5f0e2-370">**nand_flash**: NAND 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-370">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="5f0e2-371">**logical_sector**: 해제할 논리 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-371">**logical_sector**: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="5f0e2-372">반환 값</span><span class="sxs-lookup"><span data-stu-id="5f0e2-372">Return Values</span></span>

- <span data-ttu-id="5f0e2-373">**LX_SUCCESS**: (0x00) 요청에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-373">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="5f0e2-374">**LX_ERROR**: (0x01) NAND 플래시 섹터를 쓰는 중 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-374">**LX_ERROR**: (0x01) Error NAND flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5f0e2-375">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="5f0e2-375">Allowed From</span></span>

<span data-ttu-id="5f0e2-376">스레드</span><span class="sxs-lookup"><span data-stu-id="5f0e2-376">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5f0e2-377">예제</span><span class="sxs-lookup"><span data-stu-id="5f0e2-377">Example</span></span>

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="5f0e2-378">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f0e2-378">See Also</span></span>

- <span data-ttu-id="5f0e2-379">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="5f0e2-379">lx_nand_flash_close</span></span>
- <span data-ttu-id="5f0e2-380">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-380">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="5f0e2-381">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="5f0e2-381">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="5f0e2-382">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="5f0e2-382">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="5f0e2-383">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="5f0e2-383">lx_nand_flash_open</span></span>
- <span data-ttu-id="5f0e2-384">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="5f0e2-384">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="5f0e2-385">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="5f0e2-385">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="5f0e2-386">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-386">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="5f0e2-387">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="5f0e2-387">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="5f0e2-388">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="5f0e2-388">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_write"></a><span data-ttu-id="5f0e2-389">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="5f0e2-389">lx_nand_flash_sector_write</span></span>

<span data-ttu-id="5f0e2-390">NAND 플래시 섹터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-390">Write NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="5f0e2-391">프로토타입</span><span class="sxs-lookup"><span data-stu-id="5f0e2-391">Prototype</span></span>

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="5f0e2-392">Description</span><span class="sxs-lookup"><span data-stu-id="5f0e2-392">Description</span></span>

<span data-ttu-id="5f0e2-393">이 서비스는 NAND 플래시 인스턴스에 지정된 논리 섹터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-393">This service writes the specified logical sector in the NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5f0e2-394">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="5f0e2-394">Input Parameters</span></span>

- <span data-ttu-id="5f0e2-395">**nand_flash**: NAND 플래시 인스턴스 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-395">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="5f0e2-396">**logical_sector**: 쓸 논리 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-396">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="5f0e2-397">**buffer**: 논리 섹터 내용에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-397">**buffer**: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="5f0e2-398">버퍼는 NAND 플래시 페이지 크기이고 ULONG 액세스를 위해 정렬된 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-398">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="5f0e2-399">반환 값</span><span class="sxs-lookup"><span data-stu-id="5f0e2-399">Return Values</span></span>

- <span data-ttu-id="5f0e2-400">**LX_SUCCESS**: (0x00) 요청에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-400">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="5f0e2-401">**LX_NO_SECTORS**: (0x02) 쓰기를 수행하는 데 사용할 수 있는 더 이상의 여유 섹터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-401">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="5f0e2-402">**LX_ERROR**: (0x01) NAND 플래시 섹터를 해제하는 동안 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5f0e2-402">**LX_ERROR**: (0x01) Error releasing NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5f0e2-403">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="5f0e2-403">Allowed From</span></span>

<span data-ttu-id="5f0e2-404">스레드</span><span class="sxs-lookup"><span data-stu-id="5f0e2-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5f0e2-405">예제</span><span class="sxs-lookup"><span data-stu-id="5f0e2-405">Example</span></span>

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="5f0e2-406">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f0e2-406">See Also</span></span>

- <span data-ttu-id="5f0e2-407">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="5f0e2-407">lx_nand_flash_close</span></span>
- <span data-ttu-id="5f0e2-408">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-408">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="5f0e2-409">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="5f0e2-409">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="5f0e2-410">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="5f0e2-410">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="5f0e2-411">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="5f0e2-411">lx_nand_flash_open</span></span>
- <span data-ttu-id="5f0e2-412">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="5f0e2-412">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="5f0e2-413">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="5f0e2-413">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="5f0e2-414">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="5f0e2-414">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="5f0e2-415">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="5f0e2-415">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="5f0e2-416">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="5f0e2-416">lx_nand_flash_sector_release</span></span>
