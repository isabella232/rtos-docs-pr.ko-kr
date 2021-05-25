---
title: 2장 - Azure RTOS LevelX 설치 및 사용
description: LevelX의 설치 및 사용은 간단하며 이 장의 다음 섹션에서 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 34110e74e8ad0a6acd376c00c1284a3ea715c5f5
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223318"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a><span data-ttu-id="e465b-103">2장 - Azure RTOS LevelX 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="e465b-103">Chapter 2 - Installation and use of Azure RTOS LevelX</span></span>

<span data-ttu-id="e465b-104">Azure RTOS LevelX의 설치 및 사용은 간단하며 이 장의 다음 섹션에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-104">Installation and use of Azure RTOS LevelX is straightforward and described in the following sections of this chapter.</span></span>

## <a name="distribution"></a><span data-ttu-id="e465b-105">배포</span><span class="sxs-lookup"><span data-stu-id="e465b-105">Distribution</span></span>

<span data-ttu-id="e465b-106">LevelX는 ANSI C로 배포되며 여기서는 각 함수가 별도의 C 파일에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-106">LevelX is distributed in ANSI C where each function is contained in its own separate C file.</span></span> <span data-ttu-id="e465b-107">LevelX 배포의 파일은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-107">The files in the LevelX distribution are as follows.</span></span>
- <span data-ttu-id="e465b-108">lx_api.h</span><span class="sxs-lookup"><span data-stu-id="e465b-108">lx_api.h</span></span>
- <span data-ttu-id="e465b-109">lx_nand_flash_256byte_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="e465b-109">lx_nand_flash_256byte_ecc_check.c</span></span>
- <span data-ttu-id="e465b-110">lx_nand_flash_256byte_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="e465b-110">lx_nand_flash_256byte_ecc_compute.c</span></span>
- <span data-ttu-id="e465b-111">lx_nand_flash_block_full_update.c</span><span class="sxs-lookup"><span data-stu-id="e465b-111">lx_nand_flash_block_full_update.c</span></span>
- <span data-ttu-id="e465b-112">lx_nand_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="e465b-112">lx_nand_flash_block_reclaim.c</span></span>
- <span data-ttu-id="e465b-113">lx_nand_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="e465b-113">lx_nand_flash_close.c</span></span>
- <span data-ttu-id="e465b-114">lx_nand_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="e465b-114">lx_nand_flash_defragment.c</span></span>  
- <span data-ttu-id="e465b-115">lx_nand_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="e465b-115">lx_nand_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="e465b-116">lx_nand_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="e465b-116">lx_nand_flash_initialize.c</span></span>
- <span data-ttu-id="e465b-117">lx_nand_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="e465b-117">lx_nand_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="e465b-118">lx_nand_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="e465b-118">lx_nand_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="e465b-119">lx_nand_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="e465b-119">lx_nand_flash_open.c</span></span>
- <span data-ttu-id="e465b-120">lx_nand_flash_page_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="e465b-120">lx_nand_flash_page_ecc_check.c</span></span>
- <span data-ttu-id="e465b-121">lx_nand_flash_page_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="e465b-121">lx_nand_flash_page_ecc_compute.c</span></span>  
- <span data-ttu-id="e465b-122">lx_nand_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="e465b-122">lx_nand_flash_partial_defragment.c</span></span>
- <span data-ttu-id="e465b-123">lx_nand_flash_physical_page_allocate.c</span><span class="sxs-lookup"><span data-stu-id="e465b-123">lx_nand_flash_physical_page_allocate.c</span></span>
- <span data-ttu-id="e465b-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="e465b-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="e465b-125">lx_nand_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="e465b-125">lx_nand_flash_sector_read.c</span></span>
- <span data-ttu-id="e465b-126">lx_nand_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="e465b-126">lx_nand_flash_sector_release.c</span></span>
- <span data-ttu-id="e465b-127">lx_nand_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="e465b-127">lx_nand_flash_sector_write.c</span></span>
- <span data-ttu-id="e465b-128">lx_nand_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="e465b-128">lx_nand_flash_system_error.c</span></span>
- <span data-ttu-id="e465b-129">lx_nor_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="e465b-129">lx_nor_flash_block_reclaim.c</span></span>
- <span data-ttu-id="e465b-130">lx_nor_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="e465b-130">lx_nor_flash_close.c</span></span>
- <span data-ttu-id="e465b-131">lx_nor_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="e465b-131">lx_nor_flash_defragment.c</span></span>  
- <span data-ttu-id="e465b-132">lx_nor_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="e465b-132">lx_nor_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="e465b-133">lx_nor_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="e465b-133">lx_nor_flash_initialize.c</span></span>
- <span data-ttu-id="e465b-134">lx_nor_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="e465b-134">lx_nor_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="e465b-135">lx_nor_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="e465b-135">lx_nor_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="e465b-136">lx_nor_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="e465b-136">lx_nor_flash_open.c</span></span>
- <span data-ttu-id="e465b-137">lx_nor_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="e465b-137">lx_nor_flash_partial_defragment.c</span></span>
- <span data-ttu-id="e465b-138">lx_nor_flash_physical_sector_allocate.c</span><span class="sxs-lookup"><span data-stu-id="e465b-138">lx_nor_flash_physical_sector_allocate.c</span></span>
- <span data-ttu-id="e465b-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="e465b-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="e465b-140">lx_nor_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="e465b-140">lx_nor_flash_sector_read.c</span></span>
- <span data-ttu-id="e465b-141">lx_nor_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="e465b-141">lx_nor_flash_sector_release.c</span></span>
- <span data-ttu-id="e465b-142">lx_nor_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="e465b-142">lx_nor_flash_sector_write.c</span></span>
- <span data-ttu-id="e465b-143">lx_nor_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="e465b-143">lx_nor_flash_system_error.c</span></span>

<span data-ttu-id="e465b-144">다음과 같이 LevelX NAND 및 NOR 인스턴스 모두에 대한 시뮬레이터와 FileX 드라이버 샘플도 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-144">There are also simulator and FileX driver samples for both LevelX NAND and NOR instances, as follows.</span></span>

- <span data-ttu-id="e465b-145">demo_filex_nand_flash.c</span><span class="sxs-lookup"><span data-stu-id="e465b-145">demo_filex_nand_flash.c</span></span>  
- <span data-ttu-id="e465b-146">fx_nand_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="e465b-146">fx_nand_flash_simulated_driver.c</span></span>
- <span data-ttu-id="e465b-147">lx_nand_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="e465b-147">lx_nand_flash_simulator.c</span></span>
- <span data-ttu-id="e465b-148">demo_filex_nor_flash.c</span><span class="sxs-lookup"><span data-stu-id="e465b-148">demo_filex_nor_flash.c</span></span>  
- <span data-ttu-id="e465b-149">fx_nor_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="e465b-149">fx_nor_flash_simulated_driver.c</span></span>
- <span data-ttu-id="e465b-150">lx_nor_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="e465b-150">lx_nor_flash_simulator.c</span></span>

<span data-ttu-id="e465b-151">물론, NAND 플래시만 필요한 경우 LevelX NAND 플래시 파일(***lx_nand_\*.c***)만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-151">Of course, if only NAND flash is required, only the LevelX NAND flash files (***lx_nand_\*.c***) are needed.</span></span> <span data-ttu-id="e465b-152">마찬가지로, NOR 플래시만 필요한 경우에는 NOR 플래시 파일(\* \*_lx_nor_\_.c\*\*\*)만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-152">Similarly, if only NOR flash is required, only the NOR flash files (\*\*_lx_nor_\_.c\*\*\*) are needed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="e465b-153">구성 옵션</span><span class="sxs-lookup"><span data-stu-id="e465b-153">Configuration Options</span></span>

<span data-ttu-id="e465b-154">LevelX는 아래에 설명된 조건 정의를 통해 컴파일 시간에 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-154">LevelX can be configured at compile time via the conditional defines described below.</span></span> <span data-ttu-id="e465b-155">이 옵션을 사용하려면 각 LevelX 원본의 컴파일에 원하는 정의를 추가하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-155">Simply add the desired define to the compilation of each LevelX source to use the option.</span></span>

- <span data-ttu-id="e465b-156">**LX_DIRECT_READ**: 정의되면 이 옵션은 NOR 메모리를 직접 읽기 위해 NOR 플래시 드라이버 읽기 루틴을 무시하므로 결과적으로 성능이 크게 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-156">**LX_DIRECT_READ**:  Defined, this option bypasses the NOR flash driver read routine in favor or reading the NOR memory directly, resulting in a significant performance increase.</span></span>
- <span data-ttu-id="e465b-157">**LX_FREE_SECTOR_DATA_VERIFY**: 정의되면 LevelX NOR 인스턴스 열기 논리로 인해 사용 가능한 NOR 섹터가 모두 1인지 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-157">**LX_FREE_SECTOR_DATA_VERIFY**: Defined, this causes the LevelX NOR instance open logic to verify free NOR sectors are all ones.</span></span>
- <span data-ttu-id="e465b-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: 기본적으로 이 값은 16이며 논리 섹터 매핑 캐시 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**:  By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="e465b-159">값이 크면 성능이 향상되지만 메모리가 부족해집니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-159">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="e465b-160">최소 크기는 8이며 모든 값은 2의 거듭제곱이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-160">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="e465b-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: 정의되면 캐시 누락이 없도록 직접 매핑 캐시가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Defined, this creates a direct mapping cache, such that there are no cache misses.</span></span> <span data-ttu-id="e465b-162">또한 LX_NAND_SECTOR_MAPPING_CACHE_SIZE는 플래시 디바이스의 정확한 총 페이지 수를 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-162">It also requires that LX_NAND_SECTOR_MAPPING_CACHE_SIZE represents the exact number of total pages in your flash device.</span></span>
- <span data-ttu-id="e465b-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: 정의되면 확장된 NOR 캐시가 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: Defined, this disabled the extended NOR cache.</span></span>
- <span data-ttu-id="e465b-164">**LX_NOR_EXTENDED_CACHE_SIZE**: 기본적으로 이 값은 NOR 인스턴스에서 캐시할 수 있는 최대 8개 섹터를 나타내는 8입니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-164">**LX_NOR_EXTENDED_CACHE_SIZE**: By default this value is 8, which represents a maximum of 8 sectors that can be cached in a NOR instance.</span></span>
- <span data-ttu-id="e465b-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: 기본적으로 이 값은 16이며 논리 섹터 매핑 캐시 크기를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="e465b-166">값이 크면 성능이 향상되지만 메모리가 부족해집니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-166">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="e465b-167">최소 크기는 8이며 모든 값은 2의 거듭제곱이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-167">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="e465b-168">**LX_THREAD_SAFE_ENABLE**: 정의되면 API 전체에서 ThreadX 뮤텍스 개체를 사용하여 LevelX를 스레드로부터 안전하게 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-168">**LX_THREAD_SAFE_ENABLE**: Defined, this makes LevelX thread-safe by using a ThreadX mutex object throughout the API.</span></span>
- <span data-ttu-id="e465b-169">**LX_STANDALONE_ENABLE**: 정의되면 LevelX를 독립 실행형 모드(Azure RTOS 사용 안 함)로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-169">**LX_STANDALONE_ENABLE**: Defined, enables LevelX to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="e465b-170">기본적으로 이 기호는 정의되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-170">By default this symbol is not defined.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e465b-171">LevelX를 독립 실행형 모드(**LX_STANDALONE_ENABLE** 을 정의해야 함)로 사용하는 경우 ThreadX 파일/라이브러리가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-171">When using LevelX in Standalone mode (**LX_STANDALONE_ENABLE** must be defined), ThreadX files/libraries are not required.</span></span> <span data-ttu-id="e465b-172">이 모드에서는 LevelX의 스레드로부터 안전한 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-172">LevelX thread-safe feature is disabled in this mode.</span></span>

## <a name="using-levelx"></a><span data-ttu-id="e465b-173">LevelX 사용</span><span class="sxs-lookup"><span data-stu-id="e465b-173">Using LevelX</span></span>

<span data-ttu-id="e465b-174">LevelX를 단독으로 사용하거나 FileX와 함께 사용하려면 LevelX API를 참조하는 코드에 \***lx_api.h** _ 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-174">To use LevelX, either by itself or with FileX, include the file \***lx_api.h** _ in the code that references the LevelX API.</span></span> <span data-ttu-id="e465b-175">또한 링크 타임에 LevelX 개체 코드를 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e465b-175">Also ensure that the LevelX object code is available at link time.</span></span> <span data-ttu-id="e465b-176">LevelX를 사용하는 방법에 대한 예제를 보려면 _*_demo_filex_nand_flash.c_*_ 및 _ *_demo_filex_nor_flash.c_*\* 파일을 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="e465b-176">Please examine the files _*_demo_filex_nand_flash.c_*_ and _ *_demo_filex_nor_flash.c_*\* for examples of how to use LevelX.</span></span>
