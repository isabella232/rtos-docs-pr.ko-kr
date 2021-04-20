---
title: Azure RTOS LevelX NAND 지원
description: NAND 플래시 메모리는 일반적인 파일 시스템인 대규모 데이터 스토리지용 LevelX에 많이 사용됩니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3286e4ea7f16b28ff55fc95a87a1e0c313ec4240
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811083"
---
# <a name="chapter-3---azure-rtos-levelx-nand-support"></a><span data-ttu-id="95e26-103">3장 - Azure RTOS LevelX NAND 지원</span><span class="sxs-lookup"><span data-stu-id="95e26-103">Chapter 3 - Azure RTOS LevelX NAND support</span></span>

<span data-ttu-id="95e26-104">NAND 플래시 메모리는 일반적인 파일 시스템인 대규모 데이터 스토리지에 많이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-104">NAND flash memory is commonly utilized for large data storage, which is typical of file systems.</span></span> <span data-ttu-id="95e26-105">NAND 메모리는 *블록* 으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-105">NAND memory consists of *blocks*.</span></span> <span data-ttu-id="95e26-106">각 NAND 블록 내에는 일련의 *페이지* 가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-106">Within each NAND block is a series of *pages*.</span></span> <span data-ttu-id="95e26-107">NAND 블록은 지울 수 있습니다. 즉, NAND 블록 내의 모든 페이지가 지워집니다(모두로 설정됨).</span><span class="sxs-lookup"><span data-stu-id="95e26-107">NAND blocks are erasable, which means that all pages within the NAND block are erased (set to all ones).</span></span> <span data-ttu-id="95e26-108">각 NAND 블록 페이지에는 기록, 불량 블록 관리 및 오류 검색을 위해 Azure RTOS LevelX에서 사용하는 *예비 바이트* 세트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-108">Each NAND block page has a set of *spare bytes* that are utilized by Azure RTOS LevelX for bookkeeping, bad block management, and error detection.</span></span> <span data-ttu-id="95e26-109">NAND 블록 페이지는 다양한 크기로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-109">NAND block pages are available in a variety of sizes.</span></span> <span data-ttu-id="95e26-110">가장 일반적인 페이지 크기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-110">The most common page sizes are:</span></span> 

| <span data-ttu-id="95e26-111">**페이지 크기**</span><span class="sxs-lookup"><span data-stu-id="95e26-111">**Page Size**</span></span> | <span data-ttu-id="95e26-112">**예비 바이트**</span><span class="sxs-lookup"><span data-stu-id="95e26-112">**Spare Bytes**</span></span> |
| ------------- | --------------- |
| <span data-ttu-id="95e26-113">256</span><span class="sxs-lookup"><span data-stu-id="95e26-113">256</span></span>           | <span data-ttu-id="95e26-114">8</span><span class="sxs-lookup"><span data-stu-id="95e26-114">8</span></span>               |
| <span data-ttu-id="95e26-115">512</span><span class="sxs-lookup"><span data-stu-id="95e26-115">512</span></span>           | <span data-ttu-id="95e26-116">16</span><span class="sxs-lookup"><span data-stu-id="95e26-116">16</span></span>              |
| <span data-ttu-id="95e26-117">2048</span><span class="sxs-lookup"><span data-stu-id="95e26-117">2048</span></span>          | <span data-ttu-id="95e26-118">64</span><span class="sxs-lookup"><span data-stu-id="95e26-118">64</span></span>              |

<span data-ttu-id="95e26-119">NAND 메모리는 직접 액세스할 수 없다는 점에서 NOR 메모리와 다릅니다. 즉, NOR 메모리와 같은 프로세서에서 직접 NAND 메모리를 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-119">NAND memory differs from NOR memory in that there is no direct access, i.e., NAND memory cannot be read directly from the processor like NOR memory.</span></span> <span data-ttu-id="95e26-120">제한된 횟수만큼 지운 후에만 NAND 메모리에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-120">NAND memory can only be written to after an erase a limited number of times.</span></span> <span data-ttu-id="95e26-121">이는 쓰기 요청이 설정된 비트를 지우는 경우 무제한으로 기록할 수 있는 NOR 메모리와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-121">Again, this differs from NOR memory that can be written an unlimited number of times providing the write request is clearing set bits.</span></span> <span data-ttu-id="95e26-122">마지막으로 각 페이지와 연결된 예비 바이트는 NAND 플래시에 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-122">Finally, the spare bytes associated with each page are unique to NAND flash.</span></span> <span data-ttu-id="95e26-123">일반적인 예비 바이트 구성은 아래 표와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-123">Typical spare byte configurations are as shown in the table below.</span></span>

| <span data-ttu-id="95e26-124">**예비 바이트**</span><span class="sxs-lookup"><span data-stu-id="95e26-124">**Spare Bytes**</span></span> | <span data-ttu-id="95e26-125">**바이트 번호**</span><span class="sxs-lookup"><span data-stu-id="95e26-125">**Byte numbers**</span></span> | <span data-ttu-id="95e26-126">**Configuration**</span><span class="sxs-lookup"><span data-stu-id="95e26-126">**Configuration**</span></span>     |
| ------------------------- | -------------- | --------------------- |
| <span data-ttu-id="95e26-127">8</span><span class="sxs-lookup"><span data-stu-id="95e26-127">8</span></span>                         | <span data-ttu-id="95e26-128">바이트 0-2:</span><span class="sxs-lookup"><span data-stu-id="95e26-128">Bytes 0-2:</span></span>     | <span data-ttu-id="95e26-129">ECC 바이트</span><span class="sxs-lookup"><span data-stu-id="95e26-129">ECC bytes</span></span>             |
|                           | <span data-ttu-id="95e26-130">바이트 3,4,6,7:</span><span class="sxs-lookup"><span data-stu-id="95e26-130">Bytes 3,4,6,7:</span></span> | <span data-ttu-id="95e26-131">LevelX 섹터 매핑</span><span class="sxs-lookup"><span data-stu-id="95e26-131">LevelX Sector Mapping</span></span> |
|                           | <span data-ttu-id="95e26-132">바이트 5:</span><span class="sxs-lookup"><span data-stu-id="95e26-132">Byte 5:</span></span>        | <span data-ttu-id="95e26-133">불량 블록 플래그</span><span class="sxs-lookup"><span data-stu-id="95e26-133">Bad block flag</span></span>        |
| <span data-ttu-id="95e26-134">16</span><span class="sxs-lookup"><span data-stu-id="95e26-134">16</span></span>                        | <span data-ttu-id="95e26-135">바이트 0-3,6-7:</span><span class="sxs-lookup"><span data-stu-id="95e26-135">Bytes 0-3,6-7:</span></span> | <span data-ttu-id="95e26-136">ECC 바이트</span><span class="sxs-lookup"><span data-stu-id="95e26-136">ECC bytes</span></span>             |
|                           | <span data-ttu-id="95e26-137">바이트 8-11:</span><span class="sxs-lookup"><span data-stu-id="95e26-137">Bytes 8-11:</span></span>    | <span data-ttu-id="95e26-138">LevelX 섹터 매핑</span><span class="sxs-lookup"><span data-stu-id="95e26-138">LevelX Sector Mapping</span></span> |
|                           | <span data-ttu-id="95e26-139">바이트 12-15:</span><span class="sxs-lookup"><span data-stu-id="95e26-139">Bytes 12-15:</span></span>   | <span data-ttu-id="95e26-140">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="95e26-140">Unused</span></span>                |
|                           | <span data-ttu-id="95e26-141">바이트 5:</span><span class="sxs-lookup"><span data-stu-id="95e26-141">Byte 5:</span></span>        | <span data-ttu-id="95e26-142">불량 블록 플래그</span><span class="sxs-lookup"><span data-stu-id="95e26-142">Bad block flag</span></span>        |
| <span data-ttu-id="95e26-143">64</span><span class="sxs-lookup"><span data-stu-id="95e26-143">64</span></span>                        | <span data-ttu-id="95e26-144">바이트 0:</span><span class="sxs-lookup"><span data-stu-id="95e26-144">Byte 0:</span></span>        | <span data-ttu-id="95e26-145">불량 블록 플래그</span><span class="sxs-lookup"><span data-stu-id="95e26-145">Bad block flag</span></span>        |
|                           | <span data-ttu-id="95e26-146">바이트 2-5:</span><span class="sxs-lookup"><span data-stu-id="95e26-146">Bytes 2-5:</span></span>     | <span data-ttu-id="95e26-147">LevelX 섹터 매핑</span><span class="sxs-lookup"><span data-stu-id="95e26-147">LevelX Sector Mapping</span></span> |
|                           | <span data-ttu-id="95e26-148">바이트 6-39:</span><span class="sxs-lookup"><span data-stu-id="95e26-148">Bytes 6-39:</span></span>    | <span data-ttu-id="95e26-149">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="95e26-149">Unused</span></span>                |
|                           | <span data-ttu-id="95e26-150">바이트 40-63:</span><span class="sxs-lookup"><span data-stu-id="95e26-150">Bytes 40-63:</span></span>   | <span data-ttu-id="95e26-151">ECC 바이트</span><span class="sxs-lookup"><span data-stu-id="95e26-151">ECC bytes</span></span>             |

<span data-ttu-id="95e26-152">LevelX는 실제 NAND 페이지에 매핑된 논리 섹터를 추적하기 위해 각 NAND 페이지의 예비 바이트 중 4개를 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-152">LevelX Utilizes 4 of the spare bytes of each NAND page for keeping track of the logical sector mapped to the physical NAND page.</span></span> <span data-ttu-id="95e26-153">이러한 4개의 바이트는 LevelX 소유 형식으로 32비트 부호 없는 정수를 구현하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-153">These 4 bytes are used to implement a 32-bit unsigned integer with a LevelX proprietary format.</span></span> <span data-ttu-id="95e26-154">32비트 필드의 상위 비트(비트 31)는 논리적 섹터와 페이지 간 매핑이 유효함을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-154">The upper bit of the 32-bit field (bit 31) is used to indicate the logical sector-to-page mapping is valid.</span></span> <span data-ttu-id="95e26-155">이 비트가 0이면 이 페이지의 정보는 더 이상 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-155">If this bit is 0, the information in this page is no longer valid.</span></span> <span data-ttu-id="95e26-156">다음 비트(비트 30)는 이 페이지가 더 이상 사용되지 않는 과정에 있으며 새 섹터가 기록되고 있음을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-156">The next bit—bit 30—is used to indicate this page is in the process of becoming obsolete and a new sector is being written.</span></span> <span data-ttu-id="95e26-157">비트 29는 매핑 항목 쓰기가 완료된 시간을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-157">Bit 29 is used to indicate when the mapping entry write is complete.</span></span> <span data-ttu-id="95e26-158">비트 29가 0이면 매핑 항목 쓰기가 완료된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-158">If bit 29 is 0, the mapping entry write is complete.</span></span> <span data-ttu-id="95e26-159">비트 29를 설정하면 매핑 항목을 기록하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-159">If bit 29 is set, the mapping entry was in the process of being written.</span></span> <span data-ttu-id="95e26-160">비트 30 및 29는 새 플래시 페이지를 업데이트하는 동안 잠재적인 전력 손실에서 복구하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-160">Bits 30 and 29 are used in recovering from a potential power loss while updating a new flash page.</span></span> <span data-ttu-id="95e26-161">마지막으로 하위 29 비트(28-0)에는 페이지의 논리 섹터 번호가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-161">Finally, the lower 29-bits (28-0) contain the logical sector number for the page.</span></span>

<span data-ttu-id="95e26-162">**LevelX 매핑 항목**</span><span class="sxs-lookup"><span data-stu-id="95e26-162">**LevelX Mapping Entry**</span></span>

| <span data-ttu-id="95e26-163">비트</span><span class="sxs-lookup"><span data-stu-id="95e26-163">Bit(s)</span></span> | <span data-ttu-id="95e26-164">의미</span><span class="sxs-lookup"><span data-stu-id="95e26-164">Meaning</span></span> |
| ------ | ------- |
| <span data-ttu-id="95e26-165">31</span><span class="sxs-lookup"><span data-stu-id="95e26-165">31</span></span>     | <span data-ttu-id="95e26-166">유효한 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-166">Valid flag.</span></span> <span data-ttu-id="95e26-167">설정 및 논리 섹터가 모두 아닌 경우 매핑이 유효함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-167">When set and logical sector is not all ones indicates mapping is valid</span></span> |
| <span data-ttu-id="95e26-168">30</span><span class="sxs-lookup"><span data-stu-id="95e26-168">30</span></span>     | <span data-ttu-id="95e26-169">사용되지 않는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-169">Obsolete flag.</span></span> <span data-ttu-id="95e26-170">Clear인 경우 이 매핑은 더 이상 사용되지 않거나 더 이상 사용되지 않는 과정에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-170">When clear, this mapping is either obsolete or is in the process of becoming obsolete.</span></span> |
| <span data-ttu-id="95e26-171">29</span><span class="sxs-lookup"><span data-stu-id="95e26-171">29</span></span>     | <span data-ttu-id="95e26-172">이 비트가 0인 경우 매핑 항목 쓰기가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-172">Mapping entry write is complete when this bit is 0</span></span> |
| <span data-ttu-id="95e26-173">0-28</span><span class="sxs-lookup"><span data-stu-id="95e26-173">0-28</span></span>   | <span data-ttu-id="95e26-174">이 물리적 페이지에 매핑된 논리 섹터입니다(모두가 아닌 경우).</span><span class="sxs-lookup"><span data-stu-id="95e26-174">Logical sector mapped to this physical page—when not all ones.</span></span> |

<span data-ttu-id="95e26-175">또한 LevelX는 블록이 꽉 찼을 때 매핑된 페이지 목록뿐만 아니라 블록 지우기 수에 각 NAND 블록의 첫 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-175">LevelX also utilizes the first page of each NAND block for the block erase count as well as the list of mapped pages when the block is full.</span></span> <span data-ttu-id="95e26-176">LevelX에서 NAND 블록의 첫 페이지 형식이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-176">The format of the first page of a NAND block in LevelX is shown below:</span></span>

| <span data-ttu-id="95e26-177">LevelX 블록 페이지 0 형식</span><span class="sxs-lookup"><span data-stu-id="95e26-177">LevelX Block Page 0 Format</span></span> |
|:--------------------------:|
| <span data-ttu-id="95e26-178">[블록 지우기 수]</span><span class="sxs-lookup"><span data-stu-id="95e26-178">[Block Erase Count]</span></span>        |
| <span data-ttu-id="95e26-179">[1페이지 섹터 매핑]</span><span class="sxs-lookup"><span data-stu-id="95e26-179">[Page 1 Sector Mapping]</span></span>    |
| <span data-ttu-id="95e26-180">...</span><span class="sxs-lookup"><span data-stu-id="95e26-180">...</span></span>                        |
| <span data-ttu-id="95e26-181">["n"페이지 섹터 매핑]</span><span class="sxs-lookup"><span data-stu-id="95e26-181">[Page "n" Sector Mapping]</span></span>  |
| <span data-ttu-id="95e26-182">[0xF0F0F0F0]</span><span class="sxs-lookup"><span data-stu-id="95e26-182">[0xF0F0F0F0]</span></span>               |

> [!NOTE]
> <span data-ttu-id="95e26-183">블록이 꽉 찬 경우, 즉 블록의 모든 페이지가 기록된 경우에만 페이지 매핑 정보가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-183">The page mapping information is only written when the block is full, i.e., all the pages of the block have been written to.</span></span> <span data-ttu-id="95e26-184">이렇게 하면 런타임 중 사용 가능한 페이지 및 논리 섹터 매핑을 더 빠르게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-184">This enables faster search for free pages and logical sector mapping during run-time.</span></span>

## <a name="nand-bad-block-support"></a><span data-ttu-id="95e26-185">NAND 불량 블록 지원</span><span class="sxs-lookup"><span data-stu-id="95e26-185">NAND Bad Block Support</span></span>

<span data-ttu-id="95e26-186">또한 NAND 메모리는 NOR 메모리보다 블록 블록을 가질 가능성이 더 높습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-186">NAND memory is also more likely to have bad blocks than NOR memory.</span></span> <span data-ttu-id="95e26-187">이는 NAND 제조업체가 불량 블록을 허용하고 소프트웨어가 그러한 불량 블록을 해결하도록 함으로써 수율을 높일 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-187">This is largely because NAND manufacturers can increase yield by allowing bad blocks and requiring software to work-around such bad blocks.</span></span> <span data-ttu-id="95e26-188">LevelX는 단순히 불량 블록을 매핑하여 NAND 불량 블록 관리를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-188">LevelX handles NAND bad block management by simply mapping around bad blocks.</span></span>

<span data-ttu-id="95e26-189">또한 LevelX는 기본 LevelX 드라이버가 새로운 ECC 코드를 계산하는 데 활용하거나 페이지의 각 256바이트 섹션 내 페이지 읽기에서 1비트 오류 수정을 수행할 수 있도록 256바이트 해밍 ECC(오류 수정 코드) 용 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-189">LevelX also provides APIs for 256-byte Hamming Error Correction Codes (ECC) for the underlying LevelX driver to utilize for calculating new ECC codes or to perform 1-bit error correction on page reading within each 256-byte section of the page.</span></span>

## <a name="nand-driver-requirements"></a><span data-ttu-id="95e26-190">NAND 드라이버 요구 사항</span><span class="sxs-lookup"><span data-stu-id="95e26-190">NAND Driver Requirements</span></span>

<span data-ttu-id="95e26-191">LevelX를 사용하려면 기본 플래시 부분과 하드웨어 구현과 관련된 기본 NAND 플래시 드라이버가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-191">LevelX requires an underlying NAND flash driver that is specific to the underlying flash part and hardware implementation.</span></span> <span data-ttu-id="95e26-192">API ***lx_nand_flash_open*** 을 통해 초기화하는 동안 드라이버가 LevelX로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-192">The driver is specified to LevelX during initialization via the API ***lx_nand_flash_open***.</span></span> <span data-ttu-id="95e26-193">LevelX 드라이버의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-193">The prototype of the LevelX driver is as follows.</span></span>

```c
INT nand_driver_initialize(LX_NAND_FLASH *instance);
```

<span data-ttu-id="95e26-194">*Instance* 매개 변수는 LevelX NAND 제어 블록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-194">The *instance* parameter specifies the LevelX NAND control block.</span></span> <span data-ttu-id="95e26-195">드라이버 초기화 함수는 연결된 LevelX 인스턴스에 대해 다른 모든 드라이버 수준 서비스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-195">The driver initialization function is responsible for setting up all the other driver-level services for the associated LevelX instance.</span></span> <span data-ttu-id="95e26-196">각 LevelX NAND 인스턴스에 필요한 서비스는 아래 목록에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-196">The services required for each LevelX NAND instance are shown in the list below.</span></span>

- <span data-ttu-id="95e26-197">Read Page</span><span class="sxs-lookup"><span data-stu-id="95e26-197">Read Page</span></span>
- <span data-ttu-id="95e26-198">Write Page</span><span class="sxs-lookup"><span data-stu-id="95e26-198">Write Page</span></span>
- <span data-ttu-id="95e26-199">Block Erase</span><span class="sxs-lookup"><span data-stu-id="95e26-199">Block Erase</span></span>
- <span data-ttu-id="95e26-200">Block Erased Verify</span><span class="sxs-lookup"><span data-stu-id="95e26-200">Block Erased Verify</span></span>
- <span data-ttu-id="95e26-201">Page Erased Verify</span><span class="sxs-lookup"><span data-stu-id="95e26-201">Page Erased Verify</span></span>
- <span data-ttu-id="95e26-202">Block Status Get</span><span class="sxs-lookup"><span data-stu-id="95e26-202">Block Status Get</span></span>
- <span data-ttu-id="95e26-203">Block Status Set</span><span class="sxs-lookup"><span data-stu-id="95e26-203">Block Status Set</span></span>
- <span data-ttu-id="95e26-204">Block Extra Bytes Get</span><span class="sxs-lookup"><span data-stu-id="95e26-204">Block Extra Bytes Get</span></span>
- <span data-ttu-id="95e26-205">Block Extra Bytes Set</span><span class="sxs-lookup"><span data-stu-id="95e26-205">Block Extra Bytes Set</span></span>
- <span data-ttu-id="95e26-206">System Error Handler</span><span class="sxs-lookup"><span data-stu-id="95e26-206">System Error Handler</span></span>

## <a name="driver-initialization"></a><span data-ttu-id="95e26-207">드라이버 초기화</span><span class="sxs-lookup"><span data-stu-id="95e26-207">Driver Initialization</span></span>

<span data-ttu-id="95e26-208">드라이버의 초기화 함수 내에서 **LX_NAND_FLASH** 인스턴스의 함수 포인터 설정을 통해 이러한 서비스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-208">These services are setup via setting function pointers in the **LX_NAND_FLASH** instance within the driver's initialization function.</span></span> <span data-ttu-id="95e26-209">또한 드라이버 초기화 함수는 총 블록 수, 블록당 페이지 수, 페이지당 바이트 수 및 한 페이지를 메모리로 읽을 수 있을 만큼 큰 RAM 영역을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-209">The driver initialization function also specifies the total number of block, pages per block, bytes per page, and a RAM area large enough to read one page into memory.</span></span> <span data-ttu-id="95e26-210">드라이버 초기화 함수는 **LX_SUCCESS** 를 반환하기 전에 추가 디바이스 및/또는 구현별 초기화 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-210">The driver initialization function likely also performs additional device and/or implementation-specific initialization duties before returning **LX_SUCCESS**.</span></span>

## <a name="driver-read-page"></a><span data-ttu-id="95e26-211">Driver Read Page</span><span class="sxs-lookup"><span data-stu-id="95e26-211">Driver Read Page</span></span>

<span data-ttu-id="95e26-212">LevelX NAND 드라이버 "read page" 서비스는 NAND 플래시의 특정 블록에서 특정 페이지를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-212">The LevelX NAND driver "read page" service is responsible for reading a specific page in a specific block of the NAND flash.</span></span> <span data-ttu-id="95e26-213">모든 오류 검사 및 수정 논리는 드라이버 서비스의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-213">All error checking and correcting logic is the responsibility of the driver service.</span></span> <span data-ttu-id="95e26-214">성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-214">If successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="95e26-215">성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-215">If not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="95e26-216">LevelX NAND 드라이버 "read page" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-216">The prototype of the LevelX NAND driver "read page" service is given below.</span></span>

```c
INT nand_driver_read_page(
    ULONG block,
    ULONG page,
    ULONG *destination, 
    ULONG words);
```

<span data-ttu-id="95e26-217">여기서 *block* 과 *page* 는 읽을 페이지를 식별하고 *destination* 과 *words* 는 페이지 내용을 배치할 위치와 읽을 32비트 단어 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-217">Where *block* and *page* identify which page to read and *destination* and *words* specify where to place the page contents and how many 32-bit words to read.</span></span>

## <a name="driver-write-page"></a><span data-ttu-id="95e26-218">Driver Write Page</span><span class="sxs-lookup"><span data-stu-id="95e26-218">Driver Write Page</span></span>

<span data-ttu-id="95e26-219">LevelX NAND 드라이버 "write page" 서비스는 특정 페이지를 NAND 플래시의 지정된 블록에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-219">The LevelX NAND driver "write page" service is responsible for writing a specific page into the specified block of the NAND flash.</span></span> <span data-ttu-id="95e26-220">모든 오류 검사 및 ECC 계산은 드라이버 서비스의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-220">All error checking and ECC computation is the responsibility of the driver service.</span></span> <span data-ttu-id="95e26-221">성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-221">If successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="95e26-222">성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-222">If not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="95e26-223">LevelX NAND 드라이버 "write page" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-223">The prototype of the LevelX NAND driver "write page" service is shown below.</span></span>

```c
INT nand_driver_write_page(
    ULONG block, 
    ULONG page,
    ULONG *source, 
    ULONG words);
```

<span data-ttu-id="95e26-224">여기서 *block* 과 *page* 는 쑬 페이지를 식별하고 *source* 와 *words* 는 쓰기 원본과 쓸 32비트 단어 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-224">Where *block* and *page* identify which page to write and *source* and *words* specify the source of the write and how many 32-bit words to write.</span></span>

> [!NOTE]
> <span data-ttu-id="95e26-225">LevelX는 플래시 페이지에 쓸 때 하위 수준 오류 검색을 위해 드라이버를 사용합니다. 여기에는 일반적으로 페이지를 다시 읽고 쓰기 버퍼와 비교하여 쓰기가 성공했는지 확인하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-225">LevelX relies on the driver for low-level error detection when writing to the flash page, which typically involves reading back the page and comparing with the write buffer to ensure the write was successful.</span></span>

## <a name="driver-block-erase"></a><span data-ttu-id="95e26-226">Driver Block Erase</span><span class="sxs-lookup"><span data-stu-id="95e26-226">Driver Block Erase</span></span>

<span data-ttu-id="95e26-227">LevelX NAND 드라이버 "block erase" 서비스는 NAND 플래시의 지정된 블록을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-227">The LevelX NAND driver "block erase" service is responsible for erasing the specified block of the NAND flash.</span></span> <span data-ttu-id="95e26-228">성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-228">If successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="95e26-229">성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-229">If not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="95e26-230">LevelX NAND 드라이버 "block erase" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-230">The prototype of the LevelX NAND driver "block erase" service is as follows.</span></span>

```c
INT nand_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

<span data-ttu-id="95e26-231">여기서 *block* 은 지울 블록을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-231">Where *block* identifies which block to erase.</span></span> <span data-ttu-id="95e26-232">*erase_count* 매개 변수는 진단 용도로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-232">The parameter *erase_count* is provided for diagnostic purposes.</span></span> <span data-ttu-id="95e26-233">예를 들어, 드라이버는 지우기 횟수가 특정 임계값을 초과할 때 애플리케이션 소프트웨어의 다른 부분에 경고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-233">For example, the driver may want to alert another portion of the application software when the erase count exceeds a specific threshold.</span></span>

> [!NOTE]
> <span data-ttu-id="95e26-234">LevelX는 블록을 지울 때 하위 수준 오류 검색을 위해 드라이버를 사용 합니다. 여기에는 일반적으로 블록의 모든 페이지가 모두임을 확인하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-234">LevelX relies on the driver for low-level error detection when the block is erased, which typically involves ensuring that all pages of the block are all ones.</span></span>

## <a name="driver-block-erased-verify"></a><span data-ttu-id="95e26-235">Driver Block Erased Verify</span><span class="sxs-lookup"><span data-stu-id="95e26-235">Driver Block Erased Verify</span></span>

<span data-ttu-id="95e26-236">LevelX NAND 드라이버 "block erased verify" 서비스는 NAND 플래시의 지정된 블록이 삭제되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-236">The LevelX NAND driver "block erased verify" service is responsible for verifying that the specified block of the NAND flash is erased.</span></span> <span data-ttu-id="95e26-237">블록이 지워지면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-237">If it is erased, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="95e26-238">블록이 지워지지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-238">If the block is not erased, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="95e26-239">LevelX NAND 드라이버 "block erased verify" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-239">The prototype of the LevelX NAND driver "block erased verify" service is:</span></span>

```c
INT nand_driver_block_erased_verify(ULONG block);
```

<span data-ttu-id="95e26-240">여기서 *block* 은 삭제되었는지 확인하는 블록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-240">Where *block* specifies which block to verify that it is erased.</span></span>

> [!NOTE]
> <span data-ttu-id="95e26-241">LevelX는 드라이버로 모든 페이지와 각 페이지의 모든 바이트(예비 및 데이터 바이트 포함)를 검사하여 지워졌는지 확인합니다(모두 포함).</span><span class="sxs-lookup"><span data-stu-id="95e26-241">LevelX relies on the driver to examine all pages and all bytes of each page – including spare and data bytes – to ensure they are erased (contain all ones).</span></span>

## <a name="driver-page-erased-verify"></a><span data-ttu-id="95e26-242">Driver Page Erased Verify</span><span class="sxs-lookup"><span data-stu-id="95e26-242">Driver Page Erased Verify</span></span>

<span data-ttu-id="95e26-243">LevelX NAND 드라이버 "page erased verify" 서비스는 NAND 플래시의 지정된 블록의 지정된 페이지가 삭제되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-243">The LevelX NAND driver "page erased verify" service is responsible for verifying that the specified page of the specified block of the NAND flash is erased.</span></span> <span data-ttu-id="95e26-244">블록이 지워지면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-244">If it is erased, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="95e26-245">페이지가 지워지지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-245">If the page is not erased, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="95e26-246">LevelX NAND 드라이버 "page erased verify" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-246">The prototype of the LevelX NAND driver "page erased verify" service is:</span></span>

```c
INT nand_driver_page_erased_verify(
    ULONG block,  
    ULONG page);
```
<span data-ttu-id="95e26-247">여기서 *block* 은 어떤 블록과 *페이지* 가 지워졌는지 확인할 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-247">Where *block* specifies which block and *page* specifies the page to verify that it is erased.</span></span>

> [!NOTE]
> <span data-ttu-id="95e26-248">LevelX는 드라이버로 지정된 페이지의 모든 바이트(예비 및 데이터 바이트 포함)를 검사하여 지워졌는지 확인합니다(모두 포함).</span><span class="sxs-lookup"><span data-stu-id="95e26-248">LevelX relies on the driver to examine all bytes of the specified page – including spare and data bytes – to ensure they are erased (contain all ones).</span></span>

## <a name="driver-block-status-get"></a><span data-ttu-id="95e26-249">Driver Block Status Get</span><span class="sxs-lookup"><span data-stu-id="95e26-249">Driver Block Status Get</span></span>

<span data-ttu-id="95e26-250">LevelX NAND 드라이버 "block status get" 서비스는 NAND 플래시의 지정된 블록의 불량 블록 플래그를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-250">The LevelX NAND driver "block status get" service is responsible for retrieving the bad block flag of the specified block of the NAND flash.</span></span> <span data-ttu-id="95e26-251">성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-251">If it is successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="95e26-252">성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-252">If it is not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="95e26-253">LevelX NAND 드라이버 "block status get" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-253">The prototype of the LevelX NAND driver "block status get" service is: shown below.</span></span>

```c
INT nand_driver_block_status_get(
    ULONG block,  
    UCHAR *bad_block_byte);
```

<span data-ttu-id="95e26-254">여기서 *block* 은 불량 블록 플래그의 대상을 지정하는 블록과 *bad_block_byte* 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-254">Where *block* specifies which block and *bad_block_byte* specifies the destination for the bad block flag.</span></span>

## <a name="driver-block-status-set"></a><span data-ttu-id="95e26-255">Driver Block Status Set</span><span class="sxs-lookup"><span data-stu-id="95e26-255">Driver Block Status Set</span></span>

<span data-ttu-id="95e26-256">LevelX NAND 드라이버 "block status set" 서비스는 NAND 플래시의 지정된 블록의 불량 블록 플래그를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-256">The LevelX NAND driver "block status set" service is responsible for setting the bad block flag of the specified block of the NAND flash.</span></span> <span data-ttu-id="95e26-257">성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-257">If it is successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="95e26-258">성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-258">If it is not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="95e26-259">LevelX NAND 드라이버 "block status set" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-259">The prototype of the LevelX NAND driver "block status set" service is:</span></span>

```c
INT nand_driver_block_status_set(
    ULONG block,
    UCHAR bad_block_byte);
```

<span data-ttu-id="95e26-260">여기서 *block* 은 불량 블록 플래그의 값을 지정하는 블록과 *bad_block_byte* 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-260">Where *block* specifies which block and *bad_block_byte* specifies the value of the bad block flag.</span></span>

## <a name="driver-block-extra-bytes-get"></a><span data-ttu-id="95e26-261">Driver Block Extra Bytes Get</span><span class="sxs-lookup"><span data-stu-id="95e26-261">Driver Block Extra Bytes Get</span></span>

<span data-ttu-id="95e26-262">LevelX NAND 드라이버 "block extra bytes get" 서비스는 NAND 플래시의 특정 페이지와 관련된 추가 바이트를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-262">The LevelX NAND driver "block extra bytes get" service is responsible for retrieving extra bytes associated with a specific page of a specific block of the NAND flash.</span></span> <span data-ttu-id="95e26-263">성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-263">If it is successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="95e26-264">성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-264">If it is not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="95e26-265">LevelX NAND 드라이버 "block extra bytes get" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-265">The prototype of the LevelX NAND driver "block extra bytes get" service is:</span></span>

```c
INT nand_driver_block_extra_bytes_get(
    ULONG block,  
    ULONG page, 
    UCHAR *destination, 
    UINT size);
```

<span data-ttu-id="95e26-266">여기서 *block* 은 블록을 지정하고, *page* 는 특정 페이지를 지정하고, *destination* 은 추가 바이트의 대상을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-266">Where *block* specifies which block, *page* specifies the specific page and *destination* specifies the destination for the extra bytes.</span></span> <span data-ttu-id="95e26-267">*size* 매개 변수는 가져올 추가 바이트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-267">The parameter *size* specifies how many extra bytes to get.</span></span>

## <a name="driver-block-extra-bytes-set"></a><span data-ttu-id="95e26-268">Driver Block Extra Bytes Set</span><span class="sxs-lookup"><span data-stu-id="95e26-268">Driver Block Extra Bytes Set</span></span>

<span data-ttu-id="95e26-269">LevelX NAND 드라이버 "block extra bytes set" 서비스는 NAND 플래시의 특정 블록의 특정 페이지에 추가 바이트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-269">The LevelX NAND driver "block extra bytes set" service is responsible for setting extra bytes in a specific page of a specific block of the NAND flash.</span></span> <span data-ttu-id="95e26-270">성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-270">If it is successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="95e26-271">성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-271">If it is not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="95e26-272">LevelX NAND 드라이버 "block extra bytes set" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-272">The prototype of the LevelX NAND driver "block extra bytes set" service is:</span></span>

```c
INT nand_driver_block_extra_bytes_set(
    ULONG block,  
    ULONG page, 
    UCHAR *source, 
    UINT size);
```

<span data-ttu-id="95e26-273">여기서 *block* 은 블록을 지정하고, *page* 는 특정 페이지를 지정하고, *source* 는 추가 바이트의 원본을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-273">Where *block* specifies which block, *page* specifies the specific page and *source* specifies the source of the extra bytes.</span></span> <span data-ttu-id="95e26-274">*size* 매개 변수는 설정할 추가 바이트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-274">The parameter *size* specifies how many extra bytes to set.</span></span>

## <a name="driver-system-error"></a><span data-ttu-id="95e26-275">Driver System Error</span><span class="sxs-lookup"><span data-stu-id="95e26-275">Driver System Error</span></span>

<span data-ttu-id="95e26-276">LevelX NAND 드라이버 "system error handler" 서비스는 LevelX에서 감지한 시스템 오류 처리 설정을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-276">The LevelX NAND driver "system error handler" service is responsible for setting handling system errors detected by LevelX.</span></span> <span data-ttu-id="95e26-277">이 루틴의 처리는 애플리케이션에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-277">The processing in this routine is application dependent.</span></span> <span data-ttu-id="95e26-278">성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-278">If it is successful, the LevelX NAND driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="95e26-279">성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-279">If it is not successful, the LevelX NAND driver returns **LX_ERROR**.</span></span> <span data-ttu-id="95e26-280">LevelX NAND 드라이버 "system error" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-280">The prototype of the LevelX NAND driver "system error" service is:</span></span>

```c
INT nand_driver_system_error(
    UINT error_code,  
    ULONG block, 
    ULONG page);
```

<span data-ttu-id="95e26-281">여기서 *block* 은 블록을 지정하고 *page* 는 *error_code* 가 나타내는 오류가 발생한 특정 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-281">Where *block* specifies which block, and *page* specifies the specific page the error represented by *error_code* occurred.</span></span>

## <a name="nand-simulated-driver"></a><span data-ttu-id="95e26-282">NAND Simulated Driver</span><span class="sxs-lookup"><span data-stu-id="95e26-282">NAND Simulated Driver</span></span>

<span data-ttu-id="95e26-283">LevelX는 단순히 RAM을 사용하는 시뮬레이션된 NAND 플래시 드라이버를 제공하여 NAND 플래시 파트의 작동을 시뮬레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-283">LevelX provides a simulated NAND flash driver that simply uses RAM to simulate the operation of a NAND flash part.</span></span> <span data-ttu-id="95e26-284">기본적으로 NAND 시뮬레이션된 드라이버는 블록당 16페이지와 페이지당 2048바이트가 있는 8개의 NAND 플래시 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-284">By default, the NAND simulated driver provides 8 NAND flash blocks with 16 pages per block and 2048 bytes per page.</span></span>

<span data-ttu-id="95e26-285">시뮬레이션된 NAND 플래시 드라이버 초기화 함수는 ***lx_nand_flash_simulator_initialize** _이며 _*_lx_nand_flash_simulator.c_\*\*에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-285">The simulated NAND flash driver initialization function is ***lx_nand_flash_simulator_initialize** _ and is defined in _*_lx_nand_flash_simulator.c_\*\*.</span></span> <span data-ttu-id="95e26-286">또한 이 드라이버는 특정 NAND 플래시 드라이버를 쓰는 데 유용한 템플릿을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-286">This driver also provides a good template for writing specific NAND flash drivers.</span></span>

## <a name="nand-filex-integration"></a><span data-ttu-id="95e26-287">NAND FileX 통합</span><span class="sxs-lookup"><span data-stu-id="95e26-287">NAND FileX Integration</span></span>

<span data-ttu-id="95e26-288">앞에서 설명한 것처럼 LevelX는 작업을 위해 FileX를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-288">As mentioned earlier, LevelX does not rely on FileX for operation.</span></span> <span data-ttu-id="95e26-289">모든 LevelX API는 LevelX에서 제공하는 논리 섹터로 원시 데이터를 저장/검색하기 위해 애플리케이션 소프트웨어가 직접 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-289">All the LevelX APIs may be called directly by the application software to store/retrieve raw data to the logical sectors provided by LevelX.</span></span> <span data-ttu-id="95e26-290">그러나 LevelX는 FileX도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-290">However, LevelX also supports FileX.</span></span>

<span data-ttu-id="95e26-291">***fx_nand_flash_simulated_driver.c*** 파일에는 NAND 플래시 시뮬레이션에 사용할 예제 FileX 드라이버가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-291">The file ***fx_nand_flash_simulated_driver.c*** contains an example FileX driver for use with the NAND flash simulation.</span></span> <span data-ttu-id="95e26-292">이 드라이버의 흥미로운 점은 FileX에서 일반적으로 사용하는 512바이트 논리 섹터를 2048바이트 페이지를 사용하는 LevelX 시뮬레이터에 대한 단일 논리 섹터 읽기/쓰기 요청으로 결합한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-292">An interesting aspect of this driver is that it combines 512-byte logical sectors typically used by FileX into single logical sector read/write requests to the LevelX simulator using 2048-byte pages.</span></span> <span data-ttu-id="95e26-293">이를 통해 NAND 플래시 메모리를 보다 효율적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-293">This results in more efficient use of the NAND flash memory.</span></span> <span data-ttu-id="95e26-294">LevelX용 NAND 플래시 FileX 드라이버는 사용자 지정 FileX 드라이버를 쓰는 데 적합한 시작점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-294">The NAND flash FileX driver for LevelX provides a good starting point for writing custom FileX drivers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95e26-295">FileX NAND 플래시 형식은 NAND 플래시에서 제공하는 것보다 적은 섹터의 전체 블록 크기 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-295">The FileX NAND flash format should be one full block size of sectors less than the NAND flash provides.</span></span> <span data-ttu-id="95e26-296">이를 통해 마모 수준 처리 중 최상의 성능을 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-296">This will help ensure best performance during the wear level processing.</span></span> <span data-ttu-id="95e26-297">LevelX 마모 평준화 알고리즘에서 쓰기 성능을 향상시킬 수 있는 추가 기술은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-297">Additional techniques to improve write performance in the LevelX wear leveling algorithm include the following.</span></span>

1. <span data-ttu-id="95e26-298">모든 쓰기는 정확히 하나 이상의 클러스터 크기이며 정확한 클러스터 경계에서 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-298">Ensure that all writes are exactly one or more clusters in size and start on exact cluster boundaries.</span></span>
1. <span data-ttu-id="95e26-299">API의 FileX ***fx_file_allocate*** 클래스를 통해 대량 파일 쓰기 작업을 수행하기 전에 클러스터를 미리 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-299">Pre-allocate clusters before performing large file write operations via the FileX ***fx_file_allocate*** class of APIs.</span></span>
1. <span data-ttu-id="95e26-300">FileX 드라이버가 릴리스 섹터 정보를 수신하도록 설정되어 있는지 확인하고, 릴리스 섹터에 대한 드라이버로 전달된 요청은 ***lx_nor_flash_sector_release*** 를 호출하여 드라이버에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-300">Ensure the FileX driver is enabled to receive release sector information and requests made to the driver to release sectors are handled in the driver by calling ***lx_nor_flash_sector_release***.</span></span>
1. <span data-ttu-id="95e26-301">주기적으로 ***lx_nand_flash_defragment*** 를 사용하여 가능한 한 많은 NAND 블록을 확보하고 쓰기 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-301">Periodic use of ***lx_nand_flash_defragment*** to free up as many NAND blocks as possible and thus improve write performance.</span></span>
1. <span data-ttu-id="95e26-302">***Lx_nand_flash_extended_cache_enable*** API를 활용하여 더 빠른 성능을 위해 다양한 NAND 블록 리소스의 RAM 캐시를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="95e26-302">Utilize the ***lx_nand_flash_extended_cache_enable*** API to provide a RAM cache of various NAND block resources for faster performance.</span></span>
