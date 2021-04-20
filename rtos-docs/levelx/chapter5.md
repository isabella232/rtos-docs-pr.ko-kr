---
title: 5장 - Azure RTOS LevelX NOR 지원
description: NOR 플래시 메모리는 일반적으로 512바이트로 균등하게 나눌 수 있는 블록으로 구성됩니다. Azure RTOS LevelX는 각 NOR 플래시 블록을 512 바이트 논리 섹터로 나눕니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3a0c73c2b45c32bf3f1ef56de684fa83c334b59e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811076"
---
# <a name="chapter-5---azure-rtos-levelx-nor-support"></a><span data-ttu-id="315d2-104">5장 - Azure RTOS LevelX NOR 지원</span><span class="sxs-lookup"><span data-stu-id="315d2-104">Chapter 5 - Azure RTOS LevelX NOR support</span></span>

<span data-ttu-id="315d2-105">NOR 플래시 메모리는 일반적으로 512바이트로 균등하게 나눌 수 있는 *블록* 으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-105">NOR flash memory is composed of *blocks* that are typically evenly divisible by 512 bytes.</span></span> <span data-ttu-id="315d2-106">NOR 플래시 메모리에 플래시 *페이지* 의 개념이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-106">There are no concept of a flash *page* in NOR flash memory.</span></span> <span data-ttu-id="315d2-107">또한 NOR 플래시 메모리에 *예비* 바이트가 없습니다. 따라서 Azure RTOS LevelX는 모든 관리 정보에 대해 또는 NOR 플래시 메모리 자체를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-107">Also, there are no *spare* bytes in NOR flash memory, hence Azure RTOS LevelX must use the NOR flash memory itself for all management information.</span></span> <span data-ttu-id="315d2-108">직접 읽기 권한은 NOR 플래시 메모리에서 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-108">Direct read access is possible in NOR flash memory.</span></span> <span data-ttu-id="315d2-109">쓰기 권한에는 일반적으로 특별한 작업 시퀀스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-109">Write access typically requires a special sequence of operations.</span></span> <span data-ttu-id="315d2-110">NOR 플래시 메모리를 여러 번 기록하여 비트를 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-110">NOR flash memory may be written to multiple times, providing that bits are being cleared.</span></span> <span data-ttu-id="315d2-111">NOR 플래시 메모리의 비트는 블록 지우기 작업을 통해 한 번만 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-111">Bits in NOR flash memory can only be set once, via the erase block operation.</span></span>

<span data-ttu-id="315d2-112">LevelX는 각 NOR 플래시 블록을 512바이트 논리 *섹터* 로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-112">LevelX divides each NOR flash block into 512-byte logical *sectors*.</span></span> <span data-ttu-id="315d2-113">또한 LevelX는 각 NOR 플래시 블록의 첫 번째 "n" 섹터를 사용하여 관리 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-113">Furthermore, LevelX uses the first "n" sectors of each NOR flash block to store management information.</span></span> <span data-ttu-id="315d2-114">LevelX NOR 플래시 메모리 관리 정보의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-114">The format of the LevelX NOR flash memory management information is:</span></span>

<span data-ttu-id="315d2-115">**LevelX NOR 블록 형식**</span><span class="sxs-lookup"><span data-stu-id="315d2-115">**LevelX NOR Block Format**</span></span>

| <span data-ttu-id="315d2-116">바이트 오프셋</span><span class="sxs-lookup"><span data-stu-id="315d2-116">Byte Offset</span></span>  | <span data-ttu-id="315d2-117">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="315d2-117">Contents</span></span>                     |
| ------------ | ---------------------------- |
| <span data-ttu-id="315d2-118">0</span><span class="sxs-lookup"><span data-stu-id="315d2-118">0</span></span>            | <span data-ttu-id="315d2-119">[블록 지우기 수]</span><span class="sxs-lookup"><span data-stu-id="315d2-119">[Block Erase Count]</span></span>          |
| <span data-ttu-id="315d2-120">4</span><span class="sxs-lookup"><span data-stu-id="315d2-120">4</span></span>            | <span data-ttu-id="315d2-121">[최소 매핑된 섹터]</span><span class="sxs-lookup"><span data-stu-id="315d2-121">[Minimum Mapped Sector]</span></span>      |
| <span data-ttu-id="315d2-122">8</span><span class="sxs-lookup"><span data-stu-id="315d2-122">8</span></span>            | <span data-ttu-id="315d2-123">[최대 매핑된 섹터]</span><span class="sxs-lookup"><span data-stu-id="315d2-123">[Maximum Mapped Sector]</span></span>      |
| <span data-ttu-id="315d2-124">12</span><span class="sxs-lookup"><span data-stu-id="315d2-124">12</span></span>           | <span data-ttu-id="315d2-125">[무료 섹터 비트 맵]</span><span class="sxs-lookup"><span data-stu-id="315d2-125">[Free Sector Bit Map]</span></span>        |
| <span data-ttu-id="315d2-126">분</span><span class="sxs-lookup"><span data-stu-id="315d2-126">m</span></span>            | <span data-ttu-id="315d2-127">[섹터 0 매핑 항목]</span><span class="sxs-lookup"><span data-stu-id="315d2-127">[Sector 0 Mapping Entry]</span></span>     |
|              | <span data-ttu-id="315d2-128">…</span><span class="sxs-lookup"><span data-stu-id="315d2-128">…</span></span>                            |
| <span data-ttu-id="315d2-129">m+4\*(n-1)</span><span class="sxs-lookup"><span data-stu-id="315d2-129">m+4\*(n-1)</span></span>    | <span data-ttu-id="315d2-130">[섹터 "n" 매핑 항목]</span><span class="sxs-lookup"><span data-stu-id="315d2-130">[Sector "n" Mapping Entry]</span></span>   |
|              | <span data-ttu-id="315d2-131">…</span><span class="sxs-lookup"><span data-stu-id="315d2-131">…</span></span>                            |
| <span data-ttu-id="315d2-132">초</span><span class="sxs-lookup"><span data-stu-id="315d2-132">s</span></span>            | <span data-ttu-id="315d2-133">[섹터 0 콘텐츠]</span><span class="sxs-lookup"><span data-stu-id="315d2-133">[Sector 0 Contents]</span></span>          |
|              | <span data-ttu-id="315d2-134">…</span><span class="sxs-lookup"><span data-stu-id="315d2-134">…</span></span>                            |
| <span data-ttu-id="315d2-135">s+512\*(n-1)</span><span class="sxs-lookup"><span data-stu-id="315d2-135">s+512\*(n-1)</span></span> | <span data-ttu-id="315d2-136">[섹터 "n" 콘텐츠]</span><span class="sxs-lookup"><span data-stu-id="315d2-136">[Sector "n" Contents]</span></span>         |

<span data-ttu-id="315d2-137">32비트 *블록 지우기 횟수* 에는 블록이 지워진 횟수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-137">The 32-bit *Block Erase Count* contains the number of times the block has been erased.</span></span> <span data-ttu-id="315d2-138">LevelX의 주요 목표는 모든 블록의 지우기 수를 상대적으로 가깝게 유지하여 한 블록이 중간에 발생하는 것을 방지하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-138">The main goal of LevelX is to keep the erase count of all blocks relatively close to help prevent any one block from wearing out prematurely.</span></span> <span data-ttu-id="315d2-139">32비트 *최소 매핑된 섹터* 및 *최대 매핑된 섹터* 필드는 블록의 모든 논리 섹터가 매핑되고 기록된 경우에만 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-139">The 32-bit *Minimum Mapped Sector* and *Maximum Mapped Sector* fields are written only when all the logical sectors in the block have been mapped and written to.</span></span> <span data-ttu-id="315d2-140">이러한 필드는 섹터 읽기 작업을 최적화하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-140">These fields are useful for optimization of the sector read operation.</span></span> <span data-ttu-id="315d2-141">*사용 가능한 섹터 비트 맵* 항목은 각 설정 비트가 블록의 매핑되지 않은 섹터에 해당하는 비트 맵입니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-141">The *Free Sector Bit Map* entry is a bit map where each set bit corresponds to an unmapped sector in the block.</span></span> <span data-ttu-id="315d2-142">이 필드는 사용 가능한 섹터 검색을 더 효율적으로 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-142">This field is used to make the free sector search more efficient.</span></span> <span data-ttu-id="315d2-143">블록의 32섹터마다 한 단어가 필요한 가변 길이 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-143">This is a variable length field that requires one word for every 32 sectors in the block.</span></span> <span data-ttu-id="315d2-144">*섹터 매핑 항목* 배열에는 블록의 각 섹터에 대한 매핑 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-144">The *Sector Mapping Entry* array contains mapping information for each sector in the block.</span></span> <span data-ttu-id="315d2-145">각 항목에는 다음과 같은 데이터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-145">Each entry has the following format:</span></span>

<span data-ttu-id="315d2-146">**섹터 매핑 항목**</span><span class="sxs-lookup"><span data-stu-id="315d2-146">**Sector Mapping Entry**</span></span>

| <span data-ttu-id="315d2-147">비트</span><span class="sxs-lookup"><span data-stu-id="315d2-147">Bit(s)</span></span> | <span data-ttu-id="315d2-148">의미</span><span class="sxs-lookup"><span data-stu-id="315d2-148">Meaning</span></span>  |
| ------ | -------- |
| <span data-ttu-id="315d2-149">31</span><span class="sxs-lookup"><span data-stu-id="315d2-149">31</span></span>     | <span data-ttu-id="315d2-150">유효한 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-150">Valid flag.</span></span> <span data-ttu-id="315d2-151">설정 및 논리 섹터가 모두 아닌 경우 매핑이 유효함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-151">When set and logical sector not all ones indicates mapping is valid</span></span> |
| <span data-ttu-id="315d2-152">30</span><span class="sxs-lookup"><span data-stu-id="315d2-152">30</span></span>     | <span data-ttu-id="315d2-153">사용되지 않는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-153">Obsolete flag.</span></span> <span data-ttu-id="315d2-154">Clear인 경우 이 매핑은 더 이상 사용되지 않거나 사용되지 않는 것으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-154">When clear, this mapping is either obsolete or is in the process of becoming obsolete.</span></span> |
| <span data-ttu-id="315d2-155">29</span><span class="sxs-lookup"><span data-stu-id="315d2-155">29</span></span>     | <span data-ttu-id="315d2-156">이 비트가 0인 경우 매핑 항목 쓰기가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-156">Mapping entry write is complete when this bit is 0</span></span> |
| <span data-ttu-id="315d2-157">0-28</span><span class="sxs-lookup"><span data-stu-id="315d2-157">0-28</span></span>   | <span data-ttu-id="315d2-158">이 물리적 섹터에 매핑된 논리 섹터입니다. 모든 것이 아닌 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-158">Logical sector mapped to this physical sector—when not all ones.</span></span> |

<span data-ttu-id="315d2-159">32비트 필드의 상한 비트(비트 31)는 논리 섹터 매핑이 유효함을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-159">The upper bit of the 32-bit field (bit 31) is used to indicate the logical sector mapping is valid.</span></span> <span data-ttu-id="315d2-160">이 비트가 0이면 이 항목의 정보(및 해당 섹터 콘텐츠)가 더 이상 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-160">If this bit is 0, the information in this entry (and corresponding sector contents) is no longer valid.</span></span> <span data-ttu-id="315d2-161">다음 비트, 비트 30은 이 섹터가 사용되지 않는 것으로 표시되고 새 섹터가 작성되고 있음을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-161">The next bit - bit 30 - is used to indicate this sector is in the process of becoming obsolete and a new sector is being written.</span></span> <span data-ttu-id="315d2-162">비트 29는 매핑 항목 쓰기가 완료된 시간을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-162">Bit 29 is used to indicate when the mapping entry write is complete.</span></span> <span data-ttu-id="315d2-163">비트 29가 0이면 매핑 항목 쓰기가 완료된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-163">If bit 29 is 0, the mapping entry write is complete.</span></span> <span data-ttu-id="315d2-164">비트 29를 설정하면 매핑 항목을 기록하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-164">If bit 29 is set, the mapping entry was in the process of being written.</span></span> <span data-ttu-id="315d2-165">Bits 30 및 29는 새 섹터 매핑을 업데이트하는 동안 잠재적인 전원 손실에서 복구하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-165">Bits 30 and 29 are used in recovering from a potential power loss while updating a new sector mapping.</span></span> <span data-ttu-id="315d2-166">마지막으로 하위 29 비트(28-0)에는 섹터의 논리 섹터 번호가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-166">Finally, the lower 29-bits (28-0) contain the logical sector number for the sector.</span></span> <span data-ttu-id="315d2-167">섹터가 매핑되지 않은 경우 모든 비트가 설정됩니다. 즉, 값은 0xFFFFFFFF입니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-167">If a sector has not been mapped, all bits will be set, i.e., it will have a value of 0xFFFFFFFF.</span></span>

## <a name="nor-driver-requirements"></a><span data-ttu-id="315d2-168">NOR 드라이버 요구 사항</span><span class="sxs-lookup"><span data-stu-id="315d2-168">NOR Driver Requirements</span></span>

<span data-ttu-id="315d2-169">LevelX를 사용하려면 기본 플래시 부분과 하드웨어 구현과 관련된 기본 NOR 플래시 드라이버가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-169">LevelX requires an underlying NOR flash driver that is specific to the underlying flash part and hardware implementation.</span></span> <span data-ttu-id="315d2-170">API ***lx_nor_flash_open*** 을 통해 초기화하는 동안 드라이버가 LevelX로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-170">The driver is specified to LevelX during initialization via the API ***lx_nor_flash_open***.</span></span> <span data-ttu-id="315d2-171">LevelX 드라이버의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-171">The prototype of the LevelX driver is:</span></span>

```c
INT nor_driver_initialize(LX_NOR_FLASH *instance);
```

<span data-ttu-id="315d2-172">"*Instance*" 매개 변수는 LevelX NOR 제어 블록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-172">The "*instance*" parameter specifies the LevelX NOR control block.</span></span> <span data-ttu-id="315d2-173">드라이버 초기화 함수는 연결된 LevelX 인스턴스에 대해 다른 모든 드라이버 수준 서비스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-173">The driver initialization function is responsible for setting up all the other driver-level services for the associated LevelX instance.</span></span> <span data-ttu-id="315d2-174">각 LevelX NOR 인스턴스에 필요한 서비스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-174">The services required for each LevelX NOR instance are:</span></span>

- <span data-ttu-id="315d2-175">섹터 읽기</span><span class="sxs-lookup"><span data-stu-id="315d2-175">Read Sector</span></span>
- <span data-ttu-id="315d2-176">섹터 쓰기</span><span class="sxs-lookup"><span data-stu-id="315d2-176">Write Sector</span></span>
- <span data-ttu-id="315d2-177">Block Erase</span><span class="sxs-lookup"><span data-stu-id="315d2-177">Block Erase</span></span>
- <span data-ttu-id="315d2-178">Block Erased Verify</span><span class="sxs-lookup"><span data-stu-id="315d2-178">Block Erased Verify</span></span>
- <span data-ttu-id="315d2-179">시스템 오류 처리기</span><span class="sxs-lookup"><span data-stu-id="315d2-179">System Error Handler</span></span>

## <a name="driver-initialization"></a><span data-ttu-id="315d2-180">드라이버 초기화</span><span class="sxs-lookup"><span data-stu-id="315d2-180">Driver Initialization</span></span>

<span data-ttu-id="315d2-181">이러한 서비스는 드라이버의 초기화 함수 내 **LX_NOR_FLASH** 인스턴스에서 함수 포인터 설정을 통해 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-181">These services are setup via setting function pointers in the **LX_NOR_FLASH** instance within the driver's initialization function.</span></span> <span data-ttu-id="315d2-182">드라이버 초기화 함수도 다음과 같은 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-182">The driver initialization function also is responsible for:</span></span>

1. <span data-ttu-id="315d2-183">플래시의 기본 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-183">Specifying the base address of the flash.</span></span>
1. <span data-ttu-id="315d2-184">블록의 총 수와 블록 당 단어 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-184">Specifying the total number of blocks and the number of words per block.</span></span>
1. <span data-ttu-id="315d2-185">하나의 플래시 섹터(512 바이트)를 읽고 ULONG 액세스를 위해 정렬된 RAM 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-185">A RAM buffer for reading one sector of flash (512 bytes) and aligned for ULONG access.</span></span>

<span data-ttu-id="315d2-186">드라이버 초기화 함수는 **LX_SUCCESS** 를 반환 하기 전에 추가 디바이스 및/또는 구현별 초기화 의무를 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-186">The driver initialization function likely also performs additional device and/or implementation-specific initialization duties before returning **LX_SUCCESS**.</span></span>

## <a name="driver-read-sector"></a><span data-ttu-id="315d2-187">드라이버 Read Sector</span><span class="sxs-lookup"><span data-stu-id="315d2-187">Driver Read Sector</span></span>

<span data-ttu-id="315d2-188">LevelX NOR 드라이버 "read sector" 서비스는 NOR 플래시의 특정 블록에서 특정 섹터를 읽을 책임이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-188">The LevelX NOR driver "read sector" service is responsible for reading a specific sector in a specific block of the NOR flash.</span></span> <span data-ttu-id="315d2-189">모든 오류 검사 및 수정 논리는 드라이버 서비스의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-189">All error checking and correcting logic is the responsibility of the driver service.</span></span> <span data-ttu-id="315d2-190">성공하면 LevelX NOR 드라이버는 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-190">If successful, the LevelX NOR driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="315d2-191">성공하지 않으면 LevelX NOR 드라이버는 *LX_ERROR* 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-191">If not successful, the LevelX NOR driver returns *LX_ERROR*.</span></span> <span data-ttu-id="315d2-192">LevelX NOR 드라이버 "read sector" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-192">The prototype of the LevelX NOR driver "read sector" service is:</span></span>

```c
INT nor_driver_read_sector(
    ULONG *flash_address,
    ULONG *destination, 
    ULONG words);
```

<span data-ttu-id="315d2-193">여기서 "*flash_address*"는 메모리의 NOR 플래시 블록 내에서 논리 섹터의 주소를 지정하고 "*destination*" 및 "*words*"는 섹터 콘텐츠를 저장할 위치와 읽을 32비트 단어의 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-193">Where "*flash_address*" specifies the address of a logical sector within a NOR flash block of memory and "*destination*" and "*words*" specify where to place the sector contents and how many 32-bit words to read.</span></span>

## <a name="driver-write-sector"></a><span data-ttu-id="315d2-194">드라이버 Write Sector</span><span class="sxs-lookup"><span data-stu-id="315d2-194">Driver Write Sector</span></span>

<span data-ttu-id="315d2-195">LevelX NOR 드라이버 "write sector" 서비스는 특정 섹터를 NOR 플래시의 블록에 기록하는 일을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-195">The LevelX NOR driver "write sector" service is responsible for writing a specific sector into a block of the NOR flash.</span></span> <span data-ttu-id="315d2-196">모든 오류 검사는 드라이버 서비스의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-196">All error checking is the responsibility of the driver service.</span></span> <span data-ttu-id="315d2-197">성공하면 LevelX NOR 드라이버는 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-197">If successful, the LevelX NOR driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="315d2-198">성공하지 않으면 LevelX NOR 드라이버는 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-198">If not successful, the LevelX NOR driver returns **LX_ERROR**.</span></span> <span data-ttu-id="315d2-199">LevelX NOR 드라이버 "write sector" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-199">The prototype of the LevelX NOR driver "write sector" service is:</span></span>

```c
INT nor_driver_write_sector(
    ULONG *flash_address,
    ULONG *source, 
    ULONG words);
```

<span data-ttu-id="315d2-200">여기서 "*flash_address*"는 메모리의 NOR 플래시 블록 내에서 논리 섹터의 주소를 지정하고 "*source*" 및 "*words*"는 쓰기 소스와 기록할 32비트 단어 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-200">Where "*flash_address*" specifies the address of a logical sector within a NOR flash block of memory and "*source*" and "*words*" specify the source of the write and how many 32-bit words to write.</span></span>

> [!NOTE]
> <span data-ttu-id="315d2-201">LevelX는 드라이버를 사용하여 쓰기 섹터가 성공적인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-201">LevelX relies on the driver to verify that the write sector was successful.</span></span> <span data-ttu-id="315d2-202">일반적으로 이 작업은 기록될 요청 값과 일치하는지 확인하기 위해 프로그래밍된 값을 다시 읽는 방법으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-202">This is typically done by reading back the programmed value to ensure it matches the requested value to be written.</span></span>

## <a name="driver-block-erase"></a><span data-ttu-id="315d2-203">Driver Block Erase</span><span class="sxs-lookup"><span data-stu-id="315d2-203">Driver Block Erase</span></span>

<span data-ttu-id="315d2-204">LevelX NOR 드라이버 "block erase" 서비스는 NOR 플래시의 지정된 블록을 지우는 일을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-204">The LevelX NOR driver "block erase" service is responsible for erasing the specified block of the NOR flash.</span></span> <span data-ttu-id="315d2-205">성공하면 LevelX NOR 드라이버는 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-205">If successful, the LevelX NOR driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="315d2-206">성공하지 않으면 LevelX NOR 드라이버는 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-206">If not successful, the LevelX NOR driver returns **LX_ERROR**.</span></span> <span data-ttu-id="315d2-207">LevelX NOR 드라이버 "block erase" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-207">The prototype of the LevelX NOR driver "block erase" service is:</span></span>

```c
INT nor_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

<span data-ttu-id="315d2-208">여기서 "*block*"은 지울 NOR 블록을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-208">Where "*block*" identifies which NOR block to erase.</span></span> <span data-ttu-id="315d2-209">"*Erase_count*" 매개 변수는 진단 용도로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-209">The parameter "*erase_count*" is provided for diagnostic purposes.</span></span> <span data-ttu-id="315d2-210">예를 들어, 드라이버는 지우기 횟수가 특정 임계값을 초과할 때 애플리케이션 소프트웨어의 다른 부분에 경고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-210">For example, the driver may want to alert another portion of the application software when the erase count exceeds a specific threshold.</span></span>

> [!NOTE]
> <span data-ttu-id="315d2-211">LevelX는 드라이버를 사용하여 블록의 모든 바이트를 검사하고 삭제되었는지 확인합니다(모두 포함).</span><span class="sxs-lookup"><span data-stu-id="315d2-211">LevelX relies on the driver to examine all bytes of the block to ensure they are erased (contain all ones).</span></span>

## <a name="driver-block-erased-verify"></a><span data-ttu-id="315d2-212">Driver Block Erased Verify</span><span class="sxs-lookup"><span data-stu-id="315d2-212">Driver Block Erased Verify</span></span>

<span data-ttu-id="315d2-213">LevelX NOR 드라이버 "block erased verify" 서비스는 NOR 플래시의 지정된 블록이 삭제되었는지 확인하는 일을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-213">The LevelX NOR driver "block erased verify" service is responsible for verifying that the specified block of the NOR flash is erased.</span></span> <span data-ttu-id="315d2-214">블록이 지워지면 LevelX NOR 드라이버는 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-214">If it is erased, the LevelX NOR driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="315d2-215">블록이 지워지지 않으면 LevelX NOR 드라이버는 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-215">If the block is not erased, the LevelX NOR driver returns **LX_ERROR**.</span></span> <span data-ttu-id="315d2-216">LevelX NOR 드라이버 "block erased verify" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-216">The prototype of the LevelX NOR driver "block erased verify" service is:</span></span>

```c
INT nor_driver_block_erased_verify(ULONG block);
```

<span data-ttu-id="315d2-217">여기서 "*block*"은 삭제되었는지 확인하는 블록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-217">Where "*block*" specifies which block to verify that it is erased.</span></span>

> [!NOTE]
> <span data-ttu-id="315d2-218">LevelX는 드라이버를 사용하여 지정된 블록의 모든 바이트를 검사하고 삭제되었는지 확인합니다(모두 포함).</span><span class="sxs-lookup"><span data-stu-id="315d2-218">LevelX relies on the driver to examine all bytes of the specified to ensure they are erased (contain all ones).</span></span>

## <a name="driver-system-error"></a><span data-ttu-id="315d2-219">Driver System Error</span><span class="sxs-lookup"><span data-stu-id="315d2-219">Driver System Error</span></span>

<span data-ttu-id="315d2-220">LevelX NOR 드라이버 "system error handler" 서비스는 LevelX에서 감지한 시스템 오류 처리 설정을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-220">The LevelX NOR driver "system error handler" service is responsible for setting handling system errors detected by LevelX.</span></span> <span data-ttu-id="315d2-221">이 루틴의 처리는 애플리케이션에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-221">The processing in this routine is application dependent.</span></span> <span data-ttu-id="315d2-222">성공하면 LevelX NOR 드라이버는 **LX_SUCCESS** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-222">If it is successful, the LevelX NOR driver returns **LX_SUCCESS**.</span></span> <span data-ttu-id="315d2-223">성공하지 않으면 LevelX NOR 드라이버는 **LX_ERROR** 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-223">If it is not successful, the LevelX NOR driver returns **LX_ERROR**.</span></span> <span data-ttu-id="315d2-224">LevelX NOR 드라이버 "system error" 서비스의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-224">The prototype of the LevelX NOR driver "system error" service is:</span></span>

```c
INT nor_driver_system_error(UINT error_code);
```

<span data-ttu-id="315d2-225">여기서 "*error_code*"는 발생한 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-225">Where "*error_code*" represents the error that occurred.</span></span>

## <a name="nor-simulated-driver"></a><span data-ttu-id="315d2-226">NOR 시뮬레이션된 드라이버</span><span class="sxs-lookup"><span data-stu-id="315d2-226">NOR Simulated Driver</span></span>

<span data-ttu-id="315d2-227">LevelX는 단순히 RAM을 사용하는 시뮬레이션된 NOR 플래시 드라이버를 제공하여 NOR 플래시 파트의 작동을 시뮬레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-227">LevelX provides a simulated NOR flash driver that simply uses RAM to simulate the operation of a NOR flash part.</span></span> <span data-ttu-id="315d2-228">기본적으로 NOR 시뮬레이션된 드라이버는 블록 당 512바이트 섹터 16개와 NOR 플래시 블록 8개를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-228">By default, the NOR simulated driver provides 8 NOR flash blocks with 16 512-byte sectors per block.</span></span>

<span data-ttu-id="315d2-229">시뮬레이션된 NOR 플래시 드라이버 초기화 함수는 \***lx_nor_flash_simulator_initialize** 이며 \*_lx_nor_flash_simulator_\*\*에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-229">The simulated NOR flash driver initialization function is ***lx_nor_flash_simulator_initialize** _ and is defined in _*_lx_nor_flash_simulator.c_\*\*.</span></span> <span data-ttu-id="315d2-230">또한 이 드라이버는 특정 NOR 드라이버를 쓰는 데 유용한 템플릿을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-230">This driver also provides a good template for writing specific NOR flash drivers.</span></span>

## <a name="nor-filex-integration"></a><span data-ttu-id="315d2-231">NOR FileX 통합</span><span class="sxs-lookup"><span data-stu-id="315d2-231">NOR FileX Integration</span></span>

<span data-ttu-id="315d2-232">앞에서 설명한 것처럼 LevelX는 작업을 위해 FileX를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-232">As mentioned earlier, LevelX does not rely on FileX for operation.</span></span> <span data-ttu-id="315d2-233">모든 LevelX API는 LevelX에서 제공하는 논리 섹터로 원시 데이터를 저장/검색하기 위해 애플리케이션 소프트웨어가 직접 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-233">All the LevelX APIs may be called directly by the application software to store/retrieve raw data to the logical sectors provided by LevelX.</span></span> <span data-ttu-id="315d2-234">그러나 LevelX는 FileX도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-234">However, LevelX also supports FileX.</span></span>

<span data-ttu-id="315d2-235">***Fx_nor_flash_simulated_driver*** 파일에는 NOR 플래시 시뮬레이션에 사용할 예제 FileX 드라이버가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-235">The file ***fx_nor_flash_simulated_driver.c*** contains an example FileX driver for use with the NOR flash simulation.</span></span> <span data-ttu-id="315d2-236">LevelX용 NOR 플래시 FileX 드라이버는 사용자 지정 FileX 드라이버를 쓰는 데 적합한 시작점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-236">The NOR flash FileX driver for LevelX provides a good starting point for writing custom FileX drivers.</span></span>

> [!NOTE]
> <span data-ttu-id="315d2-237">FileX NOR 플래시 형식은 NOR 플래시에서 제공하는 것보다 적은 섹터의 전체 블록 크기 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-237">The FileX NOR flash format should be one full block size of sectors less than the NOR flash provides.</span></span> <span data-ttu-id="315d2-238">이를 통해 마모 수준 처리 중 최상의 성능을 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-238">This will help ensure best performance during the wear level processing.</span></span> <span data-ttu-id="315d2-239">LevelX 마모 평준화 알고리즘에서 쓰기 성능을 향상시킬 수 있는 추가 기술은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-239">Additional techniques to improve write performance in the LevelX wear leveling algorithm include:</span></span>
> 1. <span data-ttu-id="315d2-240">모든 쓰기는 정확히 하나 이상의 클러스터 크기이며 정확한 클러스터 경계에서 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-240">Ensure that all writes are exactly one or more clusters in size and start on exact cluster boundaries.</span></span>
> 2. <span data-ttu-id="315d2-241">API의 FileX ***fx_file_allocate*** 클래스를 통해 대량 파일 쓰기 작업을 수행하기 전에 클러스터를 미리 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-241">Pre-allocate clusters before performing large file write operations via the FileX ***fx_file_allocate*** class of APIs.</span></span>
> 3.  <span data-ttu-id="315d2-242">주기적으로 ***lx_nor_flash_defragment*** 를 사용하여 가능한 한 많은 NOR 블록을 확보하고 쓰기 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-242">Periodic use of ***lx_nor_flash_defragment*** to free up as many NOR blocks as possible and thus improve write performance.</span></span>
> 4. <span data-ttu-id="315d2-243">FileX 드라이버가 릴리스 섹터 정보를 수신하도록 설정되어 있는지 확인하고, 릴리스 섹터에 대한 드라이버로 전달된 요청은 ***lx_nor_flash_sector_release*** 를 호출하여 드라이버에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="315d2-243">Ensure the FileX driver is enabled to receive release sector information and requests made to the driver to release sectors are handled in the driver by calling ***lx_nor_flash_sector_release***.</span></span>
