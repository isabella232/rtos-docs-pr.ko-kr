---
title: Azure RTOS FileX 이해
description: Azure RTOS FileX는 Azure RTOS ThreadX와 완전히 통합된 고성능의 FAT(파일 할당 테이블) 호환 파일 시스템으로, 지원되는 모든 프로세서에서 사용할 수 있습니다. Azure RTOS FileX는 Azure RTOS ThreadX와 마찬가지로 공간을 적게 차지하면서 고성능을 제공하도록 설계되었으므로 파일 관리 작업이 필요한 오늘날의 긴밀하게 포함된 애플리케이션에 적합합니다. FileX는 Azure RTOS LevelX를 통해 RAM, Azure RTOS USBX, SD 카드 및 NAND/NOR 플래시 메모리를 비롯한 대부분의 물리적 미디어를 지원합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a3a20c8ced3426399ceedf6994c872ce7aec93c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812138"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="baa69-105">Azure RTOS FileX 개요</span><span class="sxs-lookup"><span data-stu-id="baa69-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="baa69-106">Azure RTOS FileX 포함 파일 시스템은 Microsoft FAT 파일 형식을 위한 Azure RTOS의 고급 산업 등급 솔루션으로, 포함 수준이 높은 실시간 IoT 애플리케이션 전용으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="baa69-107">Azure RTOS FileX는 FAT12, FAT16, FAT32, exFAT 등을 비롯한 모든 Microsoft 파일 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="baa69-108">또한 FileX는 [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/)라는 추가 기능 제품을 통해 선택적인 내결함성 및 FLASH 마모 레벨링을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="baa69-109">이뿐 아니라 Azure RTOS FileX는 적은 메모리 공간, 빠른 실행 및 뛰어난 사용 편의성을 제공하므로 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="baa69-110">API 프로토콜</span><span class="sxs-lookup"><span data-stu-id="baa69-110">API protocols</span></span>

### <a name="azure-rtos-filex-api"></a><span data-ttu-id="baa69-111">Azure RTOS FileX API</span><span class="sxs-lookup"><span data-stu-id="baa69-111">Azure RTOS FileX API</span></span>

- <span data-ttu-id="baa69-112">직관적이고 일관성 있는 API</span><span class="sxs-lookup"><span data-stu-id="baa69-112">Intuitive and consistent API</span></span>
- <span data-ttu-id="baa69-113">명사 동사 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="baa69-113">Noun-verb naming convention</span></span>
- <span data-ttu-id="baa69-114">모든 API는 FileX로 쉽게 식별할 수 있도록 앞에 *fx_* 가 옴</span><span class="sxs-lookup"><span data-stu-id="baa69-114">All APIs have leading *fx_* to easily identify as FileX</span></span>
- <span data-ttu-id="baa69-115">차단 API에 선택적 스레드 시간 제한 적용</span><span class="sxs-lookup"><span data-stu-id="baa69-115">Blocking APIs have optional thread timeout</span></span>
- <span data-ttu-id="baa69-116">미디어 및 파일 작업에 대한 선택적 사용자 알림 콜백</span><span class="sxs-lookup"><span data-stu-id="baa69-116">Optional user-notification callbacks for media and file operations</span></span>
- <span data-ttu-id="baa69-117">자세한 내용은 [Azure RTOS FileX 사용자 가이드](about-this-guide.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="baa69-117">Please see [Azure RTOS FileX User Guide](about-this-guide.md) for more details</span></span>

### <a name="media-services"></a><span data-ttu-id="baa69-118">Media Services</span><span class="sxs-lookup"><span data-stu-id="baa69-118">Media Services</span></span>

- <span data-ttu-id="baa69-119">FAT 12/16/32 및 exFAT 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-119">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="baa69-120">최소 6KB FLASH, 2.5KB RAM</span><span class="sxs-lookup"><span data-stu-id="baa69-120">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="baa69-121">종합 미디어 액세스 서비스</span><span class="sxs-lookup"><span data-stu-id="baa69-121">Complete media access services</span></span>
- <span data-ttu-id="baa69-122">미디어 인스턴스 수 제한 없음</span><span class="sxs-lookup"><span data-stu-id="baa69-122">Unlimited number of media instance</span></span>
- <span data-ttu-id="baa69-123">단순 읽기/쓰기 논리 섹터 드라이버 인터페이스</span><span class="sxs-lookup"><span data-stu-id="baa69-123">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="baa69-124">다중 파티션 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-124">Multiple partition support</span></span>
- <span data-ttu-id="baa69-125">논리 섹터 캐시</span><span class="sxs-lookup"><span data-stu-id="baa69-125">Logical sector cache</span></span>
- <span data-ttu-id="baa69-126">FAT 항목 캐시</span><span class="sxs-lookup"><span data-stu-id="baa69-126">FAT entry cache</span></span>
- <span data-ttu-id="baa69-127">선택적 내결함성 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-127">Optional fault tolerance support</span></span>
- <span data-ttu-id="baa69-128">지연된 보조 FAT 업데이트</span><span class="sxs-lookup"><span data-stu-id="baa69-128">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="baa69-129">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="baa69-129">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="baa69-130">다음을 포함하는 직관적인 미디어 액세스 API:</span><span class="sxs-lookup"><span data-stu-id="baa69-130">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="baa69-131">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="baa69-131">fx_media_open</span></span>
  - <span data-ttu-id="baa69-132">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="baa69-132">fx_media_close</span></span>
  - <span data-ttu-id="baa69-133">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="baa69-133">fx_media_format</span></span>
  - <span data-ttu-id="baa69-134">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="baa69-134">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="baa69-135">디렉터리 서비스</span><span class="sxs-lookup"><span data-stu-id="baa69-135">Directory Services</span></span>

- <span data-ttu-id="baa69-136">최대 256바이트 경로</span><span class="sxs-lookup"><span data-stu-id="baa69-136">Up to 256 byte paths</span></span>
- <span data-ttu-id="baa69-137">긴 및 8.3 디렉터리 이름 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-137">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="baa69-138">디렉터리 만들기 및 삭제</span><span class="sxs-lookup"><span data-stu-id="baa69-138">Directory create & delete</span></span>
- <span data-ttu-id="baa69-139">디렉터리 탐색 및 트래버스</span><span class="sxs-lookup"><span data-stu-id="baa69-139">Directory navigation and traversal</span></span>
- <span data-ttu-id="baa69-140">디렉터리 특성 관리</span><span class="sxs-lookup"><span data-stu-id="baa69-140">Directory attributes management</span></span>
- <span data-ttu-id="baa69-141">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="baa69-141">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="baa69-142">다음을 포함하는 직관적인 디렉터리 액세스 API:</span><span class="sxs-lookup"><span data-stu-id="baa69-142">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="baa69-143">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="baa69-143">fx_directory_create</span></span>
  - <span data-ttu-id="baa69-144">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="baa69-144">fx_directory_delete</span></span>
  - <span data-ttu-id="baa69-145">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="baa69-145">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="baa69-146">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="baa69-146">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="baa69-147">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="baa69-147">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="baa69-148">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="baa69-148">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="baa69-149">파일 서비스</span><span class="sxs-lookup"><span data-stu-id="baa69-149">File Services</span></span>

- <span data-ttu-id="baa69-150">최소 3.3KB FLASH</span><span class="sxs-lookup"><span data-stu-id="baa69-150">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="baa69-151">무제한 파일 열기</span><span class="sxs-lookup"><span data-stu-id="baa69-151">Unlimited open files</span></span>
- <span data-ttu-id="baa69-152">읽기 전용 파일을 여러 번 열 수 있음</span><span class="sxs-lookup"><span data-stu-id="baa69-152">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="baa69-153">긴 및 8.3 디렉터리 이름 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-153">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="baa69-154">연속 파일 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-154">Contiguous file support</span></span>
- <span data-ttu-id="baa69-155">빠른 검색 논리</span><span class="sxs-lookup"><span data-stu-id="baa69-155">Fast seek logic</span></span>
- <span data-ttu-id="baa69-156">클러스터 사전 할당</span><span class="sxs-lookup"><span data-stu-id="baa69-156">Pre-allocation of clusters</span></span>
- <span data-ttu-id="baa69-157">파일 만들기, 삭제 및 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="baa69-157">File create, delete, and rename</span></span>
- <span data-ttu-id="baa69-158">파일 읽기, 쓰기 및 보기</span><span class="sxs-lookup"><span data-stu-id="baa69-158">File read, write, and see</span></span>
- <span data-ttu-id="baa69-159">파일 특성 관리</span><span class="sxs-lookup"><span data-stu-id="baa69-159">File attributes management</span></span>
- <span data-ttu-id="baa69-160">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="baa69-160">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="baa69-161">다음을 포함하는 직관적인 파일 액세스 API:</span><span class="sxs-lookup"><span data-stu-id="baa69-161">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="baa69-162">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="baa69-162">fx_file_create</span></span>
  - <span data-ttu-id="baa69-163">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="baa69-163">fx_file_delete</span></span>
  - <span data-ttu-id="baa69-164">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="baa69-164">fx_file_attributes_set</span></span>
  - <span data-ttu-id="baa69-165">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="baa69-165">fx_file_attributes_read</span></span>
  - <span data-ttu-id="baa69-166">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="baa69-166">fx_file_read</span></span>
  - <span data-ttu-id="baa69-167">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="baa69-167">fx_file_seek</span></span>
  - <span data-ttu-id="baa69-168">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="baa69-168">fx_file_write</span></span>

## <a name="small-footprint"></a><span data-ttu-id="baa69-169">적은 메모리 공간</span><span class="sxs-lookup"><span data-stu-id="baa69-169">Small-footprint</span></span>

<span data-ttu-id="baa69-170">Azure RTOS FileX 포함된 파일 시스템은 8.6 ~ 12KB라는 획기적으로 적은 수준의 메모리 공간으로 기본 파일 읽기/쓰기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-170">Azure RTOS FileX embedded file system has a remarkably small minimal footprint of 8.6 KB to 12 KB for basic file read/write support.</span></span> <span data-ttu-id="baa69-171">최소 Azure RTOS FileX RAM 사용량은 단일 미디어 인스턴스에 대해 1.8KB 수준으로, 논리 섹터 캐시는 512바이트에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-171">Minimal Azure RTOS FileX RAM usage is on the order of 1.8 KB for one media instance and with only a 512-byte logical sector cache.</span></span> <span data-ttu-id="baa69-172">Azure RTOS ThreadX와 같이 Azure RTOS FileX의 크기는 애플리케이션에서 사용하는 서비스에 따라 자동으로 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-172">Like Azure RTOS ThreadX, the size of Azure RTOS FileX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="baa69-173">이렇게 하면 실질적으로 복잡한 구성 및 빌드 매개 변수가 제거되므로 개발자가 더 쉽게 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-173">This virtually eliminates the need for complicated configuration and builds parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="baa69-174">고속 실행</span><span class="sxs-lookup"><span data-stu-id="baa69-174">Fast execution</span></span>

<span data-ttu-id="baa69-175">Azure RTOS FileX는 FAT 항목 캐시뿐 아니라 논리 섹터 캐시를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-175">Azure RTOS FileX provides a logical sector cache as well as a FAT entry cache.</span></span> <span data-ttu-id="baa69-176">두 가지 모두 크기를 애플리케이션에서 직접 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-176">The sizes of both are under direct control of the application.</span></span> <span data-ttu-id="baa69-177">또한 Azure RTOS FileX는 연속 클러스터 할당과, 직접 연속 클러스터 읽기 및 쓰기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-177">In addition, Azure RTOS FileX provides contiguous cluster allocation and direct consecutive cluster reading and writing.</span></span> <span data-ttu-id="baa69-178">전체 섹터의 읽기/쓰기 요청은 애플리케이션 버퍼와 미디어 간에 직접 이루어지므로 중간 버퍼링이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-178">Read/write requests of whole sectors are done directly between the application buffer and the media – that is, no intermediate buffering is done.</span></span> <span data-ttu-id="baa69-179">이런 특징과 일반 성능 중심 디자인 철학으로 Azure RTOS FileX에서 가능한 가장 빠른 성능을 구현하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-179">All of this and a general performance-oriented design philosophy helps Azure RTOS FileX achieve the fastest possible performance.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="baa69-180">고급 기술</span><span class="sxs-lookup"><span data-stu-id="baa69-180">Advanced technology</span></span>

<span data-ttu-id="baa69-181">Azure RTOS FileX는 다음을 포괄하는 고급 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-181">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="baa69-182">FAT 12/16/32 및 exFAT 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-182">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="baa69-183">다중 파티션 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-183">Multiple partition support</span></span>
- <span data-ttu-id="baa69-184">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="baa69-184">Automatic scaling</span></span>
- <span data-ttu-id="baa69-185">Endian 중립</span><span class="sxs-lookup"><span data-stu-id="baa69-185">Endian neutral</span></span>
- <span data-ttu-id="baa69-186">긴 파일 이름 및 8.3 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-186">Long file name and 8.3 support</span></span>
- <span data-ttu-id="baa69-187">선택적 내결함성 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-187">Optional fault tolerance support</span></span>
- <span data-ttu-id="baa69-188">논리 섹터 캐시</span><span class="sxs-lookup"><span data-stu-id="baa69-188">Logical sector cache</span></span>
- <span data-ttu-id="baa69-189">FAT 항목 캐시</span><span class="sxs-lookup"><span data-stu-id="baa69-189">FAT entry cache</span></span>
- <span data-ttu-id="baa69-190">클러스터 사전 할당</span><span class="sxs-lookup"><span data-stu-id="baa69-190">Pre-allocation of clusters</span></span>
- <span data-ttu-id="baa69-191">연속 파일 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-191">Contiguous file support</span></span>
- <span data-ttu-id="baa69-192">선택적 성능 메트릭</span><span class="sxs-lookup"><span data-stu-id="baa69-192">Optional performance metrics</span></span>
- <span data-ttu-id="baa69-193">Azure RTOS TraceX 시스템 분석 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-193">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="baa69-194">NOR/NAND 마모 레벨링(Azure RTOS LevelX)</span><span class="sxs-lookup"><span data-stu-id="baa69-194">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="baa69-195">Azure RTOS LevelX는 Microsoft의 NOR/NAND FLASH 마모 레벨링 제품입니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-195">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="baa69-196">Azure RTOS LevelX는 애플리케이션에 대해 FileX와 결합하여, 또는 독립 실행형 직접 읽기/쓰기 FLASH 섹터 라이브러리로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-196">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="baa69-197">가장 빠른 출시 시간</span><span class="sxs-lookup"><span data-stu-id="baa69-197">Fastest time-to-market</span></span>

<span data-ttu-id="baa69-198">Azure RTOS FileX는 설치, 학습, 사용, 디버그, 확인, 인증 및 유지 관리를 손쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-198">Azure RTOS FileX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="baa69-199">이 덕분에 Azure RTOS FileX는 포함된 IoT 디바이스에 가장 널리 사용되는 FAT 파일 시스템 중 하나가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-199">As a result, Azure RTOS FileX is one of the most popular FAT file systems for embedded IoT devices.</span></span> <span data-ttu-id="baa69-200">일관된 신속 출시가 가능한 몇 가지 이유는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-200">The following are some reasons for our consistent time-to-market advantage:</span></span>

- <span data-ttu-id="baa69-201">품질 설명서 – [Azure RTOS FileX 사용자 가이드](about-this-guide.md)를 검토하고 직접 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-201">Quality Documentation – please review our [Azure RTOS FileX User Guide](about-this-guide.md) and see for yourself!</span></span>
- <span data-ttu-id="baa69-202">전체 소스 코드 가용성</span><span class="sxs-lookup"><span data-stu-id="baa69-202">Complete Source Code Availability</span></span>
- <span data-ttu-id="baa69-203">사용하기 쉬운 API</span><span class="sxs-lookup"><span data-stu-id="baa69-203">Easy-to-use API</span></span>
- <span data-ttu-id="baa69-204">포괄적인 고급 기능 세트</span><span class="sxs-lookup"><span data-stu-id="baa69-204">Comprehensive and Advanced Feature Set</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="baa69-205">TUV 및 UL을 비롯한 여러 안전 표준의 사전 인증</span><span class="sxs-lookup"><span data-stu-id="baa69-205">Pre-certified  by TUV and UL to many safety standards</span></span>

![SGS-TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

<span data-ttu-id="baa69-207">Azure RTOS FileX는 안전이 매우 중요한 시스템에서의 사용을 위해, IEC-61508 SIL 4, IEC-62304 SW 안전 등급 C, ISO 26262 ASIL D 및 EN 50128에 따라 SGS-TUV Saar 인증을 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-207">Azure RTOS FileX has been certified by SGS-TUV Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="baa69-208">이 인증은 “전기, 전자 및 프로그램 가능한 전자 안전 관련 시스템의 기능적 안전”에 대한 최고 수준의 IEC-61508, IEC-62304, ISO 26262 및 EN 50128의 안전 무결성 등급에 따라, FileX를 보안 관련 소프트웨어의 개발에 사용할 수 있음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-208">The certification confirms that FileX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="baa69-209">독일 SGS-Group 및 TUV Saarland의 공동 벤처인 SGS-TUV Saar는 세계적으로 안전 관련 시스템용 포함 소프트웨어를 테스트, 감사, 확인 및 검증하는 최고 권위의 독립 기업으로 자리했습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-209">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="baa69-210">산업 보안 표준 IEC 61508과, 거기에서 파생된 모든 표준(IEC-62304, ISO 26262 및 EN 50128 포함)은 전기, 전자 및 프로그래밍 가능한 전자 안전 관련 의료 장비, 공정 제어 시스템, 산업용 기계, 자동차, 철도 제어 시스템의 기능 안전을 보장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-210">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles, and railway control systems.</span></span>

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="CRU UL 인증":::

<span data-ttu-id="baa69-212">UL은 Azure RTOS FileX가 프로그래밍 가능한 구성 요소에서의 소프트웨어에 대한 UL 60730-1 부칙 H, CSA E60730-1 부칙 H, IEC 60730-1 부칙 H, UL 60335-1 부칙 R, IEC 60335-1 부칙 R 및 UL 1998 안전 표준의 규정을 준수한다고 인정했습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-212">Azure RTOS FileX has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="baa69-213">UL은 전기의 공공 도입에서부터 지속 가능성, 재생 에너지 및 나노 기술의 혁신에 이르기까지 안전 솔루션을 혁신하는 1세기 이상의 전문 지식을 보유한 글로벌 독립 안전 과학 기업입니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-213">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

<span data-ttu-id="baa69-214">TUV 및 UL 인증과 관련한 아티팩트(인증서, 안전 매뉴얼, 테스트 보고서 등)는 판매 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-214">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="baa69-215">애플리케이션에 추가 인증이 필요한 경우, 실제 하드웨어 플랫폼을 사용한 다양한 표준에 대한 턴키 방식의 인증을 제공하고 애플리케이션 코드까지도 다루는 인증 서비스를 Microsoft를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-215">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="baa69-216">하나의 간단한 라이선스</span><span class="sxs-lookup"><span data-stu-id="baa69-216">One Simple License</span></span>

<span data-ttu-id="baa69-217">사전에 사용이 허가된 디바이스에 배포하는 경우에는 소스 코드를 사용 및 테스트하는 데 비용이 들지 않으며 프로덕션 라이선스에 대한 비용도 부과되지 않습니다. 다른 모든 디바이스에는 간단한 연간 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-217">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="baa69-218">최고 품질의 전체 소스 코드</span><span class="sxs-lookup"><span data-stu-id="baa69-218">Full, highest-quality source code</span></span>

<span data-ttu-id="baa69-219">오랜 시간을 통해 FileX 소스 코드는 품질 및 이해 용이성의 기준을 정립했습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-219">Throughout the years, FileX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="baa69-220">또한 파일당 하나의 함수를 포함하는 규칙을 통해 손쉬운 소스 탐색을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-220">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="baa69-221">대부분의 주요 아키텍처 지원</span><span class="sxs-lookup"><span data-stu-id="baa69-221">Supports most popular architectures</span></span>

<span data-ttu-id="baa69-222">Azure RTOS FileX는 완전한 테스트와 지원을 통해 다음과 같이 대부분의 주요 32/64비트 마이크로프로세서에서 실행되며, 바로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baa69-222">Azure RTOS FileX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="baa69-223">**아날로그 디바이스**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="baa69-223">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="baa69-224">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="baa69-224">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="baa69-225">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="baa69-225">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="baa69-226">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64비트/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="baa69-226">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="baa69-227">**Cadence**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="baa69-227">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="baa69-228">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="baa69-228">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="baa69-229">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="baa69-229">**Cypress**: RISC-V</span></span>

<span data-ttu-id="baa69-230">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="baa69-230">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="baa69-231">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="baa69-231">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="baa69-232">**Intel**; **Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="baa69-232">**Intel**; **Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="baa69-233">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="baa69-233">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="baa69-234">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="baa69-234">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="baa69-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="baa69-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="baa69-236">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span><span class="sxs-lookup"><span data-stu-id="baa69-236">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="baa69-237">**Silicon** Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="baa69-237">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="baa69-238">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="baa69-238">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="baa69-239">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="baa69-239">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="baa69-240">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="baa69-240">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="baa69-241">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="baa69-241">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="baa69-242">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="baa69-242">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="baa69-243">*나열된 모든 타이밍 및 크기 수치는 예상치이며, 개발 플랫폼에 따라 다를 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="baa69-243">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
