---
title: Azure RTOS FileX 이해
description: Azure RTOS FileX는 Azure RTOS ThreadX와 완전히 통합된 고성능의 FAT(파일 할당 테이블) 호환 파일 시스템으로, 지원되는 모든 프로세서에서 사용할 수 있습니다. Azure RTOS FileX는 Azure RTOS ThreadX와 마찬가지로 공간을 적게 차지하면서 고성능을 제공하도록 설계되었으므로 파일 관리 작업이 필요한 오늘날의 긴밀하게 포함된 애플리케이션에 적합합니다. FileX는 Azure RTOS LevelX를 통해 RAM, Azure RTOS USBX, SD 카드 및 NAND/NOR 플래시 메모리를 비롯한 대부분의 물리적 미디어를 지원합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a54f160c96fb3e90c2295ae72020c121d367a12
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171355"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="f1ab1-105">Azure RTOS FileX 개요</span><span class="sxs-lookup"><span data-stu-id="f1ab1-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="f1ab1-106">Azure RTOS FileX 포함 파일 시스템은 Microsoft FAT 파일 형식을 위한 Azure RTOS의 고급 산업 등급 솔루션으로, 포함 수준이 높은 실시간 IoT 애플리케이션 전용으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="f1ab1-107">Azure RTOS FileX는 FAT12, FAT16, FAT32, exFAT 등을 비롯한 모든 Microsoft 파일 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="f1ab1-108">또한 FileX는 [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/)라는 추가 기능 제품을 통해 선택적인 내결함성 및 FLASH 마모 레벨링을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="f1ab1-109">이뿐 아니라 Azure RTOS FileX는 적은 메모리 공간, 빠른 실행 및 뛰어난 사용 편의성을 제공하므로 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="f1ab1-110">API 프로토콜</span><span class="sxs-lookup"><span data-stu-id="f1ab1-110">API protocols</span></span>

### <a name="media-services"></a><span data-ttu-id="f1ab1-111">Media Services</span><span class="sxs-lookup"><span data-stu-id="f1ab1-111">Media Services</span></span>

- <span data-ttu-id="f1ab1-112">FAT 12/16/32 및 exFAT 지원</span><span class="sxs-lookup"><span data-stu-id="f1ab1-112">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="f1ab1-113">최소 6KB FLASH, 2.5KB RAM</span><span class="sxs-lookup"><span data-stu-id="f1ab1-113">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="f1ab1-114">종합 미디어 액세스 서비스</span><span class="sxs-lookup"><span data-stu-id="f1ab1-114">Complete media access services</span></span>
- <span data-ttu-id="f1ab1-115">미디어 인스턴스 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="f1ab1-115">Unlimited number of media instance</span></span>
- <span data-ttu-id="f1ab1-116">단순 읽기/쓰기 논리 섹터 드라이버 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f1ab1-116">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="f1ab1-117">다중 파티션 지원</span><span class="sxs-lookup"><span data-stu-id="f1ab1-117">Multiple partition support</span></span>
- <span data-ttu-id="f1ab1-118">논리 섹터 캐시</span><span class="sxs-lookup"><span data-stu-id="f1ab1-118">Logical sector cache</span></span>
- <span data-ttu-id="f1ab1-119">FAT 항목 캐시</span><span class="sxs-lookup"><span data-stu-id="f1ab1-119">FAT entry cache</span></span>
- <span data-ttu-id="f1ab1-120">선택적 내결함성 지원</span><span class="sxs-lookup"><span data-stu-id="f1ab1-120">Optional fault tolerance support</span></span>
- <span data-ttu-id="f1ab1-121">지연된 보조 FAT 업데이트</span><span class="sxs-lookup"><span data-stu-id="f1ab1-121">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="f1ab1-122">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="f1ab1-122">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="f1ab1-123">다음을 포함하는 직관적인 미디어 액세스 API:</span><span class="sxs-lookup"><span data-stu-id="f1ab1-123">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="f1ab1-124">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="f1ab1-124">fx_media_open</span></span>
  - <span data-ttu-id="f1ab1-125">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="f1ab1-125">fx_media_close</span></span>
  - <span data-ttu-id="f1ab1-126">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="f1ab1-126">fx_media_format</span></span>
  - <span data-ttu-id="f1ab1-127">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="f1ab1-127">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="f1ab1-128">디렉터리 서비스</span><span class="sxs-lookup"><span data-stu-id="f1ab1-128">Directory Services</span></span>

- <span data-ttu-id="f1ab1-129">최대 256바이트 경로</span><span class="sxs-lookup"><span data-stu-id="f1ab1-129">Up to 256 byte paths</span></span>
- <span data-ttu-id="f1ab1-130">긴 및 8.3 디렉터리 이름 지원</span><span class="sxs-lookup"><span data-stu-id="f1ab1-130">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="f1ab1-131">디렉터리 만들기 및 삭제</span><span class="sxs-lookup"><span data-stu-id="f1ab1-131">Directory create & delete</span></span>
- <span data-ttu-id="f1ab1-132">디렉터리 탐색 및 트래버스</span><span class="sxs-lookup"><span data-stu-id="f1ab1-132">Directory navigation and traversal</span></span>
- <span data-ttu-id="f1ab1-133">디렉터리 특성 관리</span><span class="sxs-lookup"><span data-stu-id="f1ab1-133">Directory attributes management</span></span>
- <span data-ttu-id="f1ab1-134">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="f1ab1-134">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="f1ab1-135">다음을 포함하는 직관적인 디렉터리 액세스 API:</span><span class="sxs-lookup"><span data-stu-id="f1ab1-135">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="f1ab1-136">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="f1ab1-136">fx_directory_create</span></span>
  - <span data-ttu-id="f1ab1-137">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="f1ab1-137">fx_directory_delete</span></span>
  - <span data-ttu-id="f1ab1-138">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="f1ab1-138">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="f1ab1-139">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="f1ab1-139">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="f1ab1-140">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="f1ab1-140">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="f1ab1-141">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="f1ab1-141">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="f1ab1-142">파일 서비스</span><span class="sxs-lookup"><span data-stu-id="f1ab1-142">File Services</span></span>

- <span data-ttu-id="f1ab1-143">최소 3.3KB FLASH</span><span class="sxs-lookup"><span data-stu-id="f1ab1-143">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="f1ab1-144">무제한 파일 열기</span><span class="sxs-lookup"><span data-stu-id="f1ab1-144">Unlimited open files</span></span>
- <span data-ttu-id="f1ab1-145">읽기 전용 파일을 여러 번 열 수 있음</span><span class="sxs-lookup"><span data-stu-id="f1ab1-145">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="f1ab1-146">긴 및 8.3 디렉터리 이름 지원</span><span class="sxs-lookup"><span data-stu-id="f1ab1-146">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="f1ab1-147">연속 파일 지원</span><span class="sxs-lookup"><span data-stu-id="f1ab1-147">Contiguous file support</span></span>
- <span data-ttu-id="f1ab1-148">빠른 검색 논리</span><span class="sxs-lookup"><span data-stu-id="f1ab1-148">Fast seek logic</span></span>
- <span data-ttu-id="f1ab1-149">클러스터 사전 할당</span><span class="sxs-lookup"><span data-stu-id="f1ab1-149">Pre-allocation of clusters</span></span>
- <span data-ttu-id="f1ab1-150">파일 만들기, 삭제 및 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="f1ab1-150">File create, delete, and rename</span></span>
- <span data-ttu-id="f1ab1-151">파일 읽기, 쓰기 및 보기</span><span class="sxs-lookup"><span data-stu-id="f1ab1-151">File read, write, and see</span></span>
- <span data-ttu-id="f1ab1-152">파일 특성 관리</span><span class="sxs-lookup"><span data-stu-id="f1ab1-152">File attributes management</span></span>
- <span data-ttu-id="f1ab1-153">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="f1ab1-153">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="f1ab1-154">다음을 포함하는 직관적인 파일 액세스 API:</span><span class="sxs-lookup"><span data-stu-id="f1ab1-154">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="f1ab1-155">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="f1ab1-155">fx_file_create</span></span>
  - <span data-ttu-id="f1ab1-156">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="f1ab1-156">fx_file_delete</span></span>
  - <span data-ttu-id="f1ab1-157">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="f1ab1-157">fx_file_attributes_set</span></span>
  - <span data-ttu-id="f1ab1-158">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="f1ab1-158">fx_file_attributes_read</span></span>
  - <span data-ttu-id="f1ab1-159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="f1ab1-159">fx_file_read</span></span>
  - <span data-ttu-id="f1ab1-160">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="f1ab1-160">fx_file_seek</span></span>
  - <span data-ttu-id="f1ab1-161">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="f1ab1-161">fx_file_write</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="f1ab1-162">고급 기술</span><span class="sxs-lookup"><span data-stu-id="f1ab1-162">Advanced technology</span></span>

<span data-ttu-id="f1ab1-163">Azure RTOS FileX는 다음을 포괄하는 고급 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-163">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="f1ab1-164">FAT 12/16/32 및 exFAT 지원</span><span class="sxs-lookup"><span data-stu-id="f1ab1-164">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="f1ab1-165">다중 파티션 지원</span><span class="sxs-lookup"><span data-stu-id="f1ab1-165">Multiple partition support</span></span>
- <span data-ttu-id="f1ab1-166">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="f1ab1-166">Automatic scaling</span></span>
- <span data-ttu-id="f1ab1-167">Endian 중립</span><span class="sxs-lookup"><span data-stu-id="f1ab1-167">Endian neutral</span></span>
- <span data-ttu-id="f1ab1-168">긴 파일 이름 및 8.3 지원</span><span class="sxs-lookup"><span data-stu-id="f1ab1-168">Long file name and 8.3 support</span></span>
- <span data-ttu-id="f1ab1-169">선택적 내결함성 지원</span><span class="sxs-lookup"><span data-stu-id="f1ab1-169">Optional fault tolerance support</span></span>
- <span data-ttu-id="f1ab1-170">논리 섹터 캐시</span><span class="sxs-lookup"><span data-stu-id="f1ab1-170">Logical sector cache</span></span>
- <span data-ttu-id="f1ab1-171">FAT 항목 캐시</span><span class="sxs-lookup"><span data-stu-id="f1ab1-171">FAT entry cache</span></span>
- <span data-ttu-id="f1ab1-172">클러스터 사전 할당</span><span class="sxs-lookup"><span data-stu-id="f1ab1-172">Pre-allocation of clusters</span></span>
- <span data-ttu-id="f1ab1-173">연속 파일 지원</span><span class="sxs-lookup"><span data-stu-id="f1ab1-173">Contiguous file support</span></span>
- <span data-ttu-id="f1ab1-174">선택적 성능 메트릭</span><span class="sxs-lookup"><span data-stu-id="f1ab1-174">Optional performance metrics</span></span>
- <span data-ttu-id="f1ab1-175">Azure RTOS TraceX 시스템 분석 지원</span><span class="sxs-lookup"><span data-stu-id="f1ab1-175">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="f1ab1-176">NOR/NAND 마모 레벨링(Azure RTOS LevelX)</span><span class="sxs-lookup"><span data-stu-id="f1ab1-176">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="f1ab1-177">Azure RTOS LevelX는 Microsoft의 NOR/NAND FLASH 마모 레벨링 제품입니다.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-177">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="f1ab1-178">Azure RTOS LevelX는 애플리케이션에 대해 FileX와 결합하여, 또는 독립 실행형 직접 읽기/쓰기 FLASH 섹터 라이브러리로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1ab1-178">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>
