---
title: 5장 - Azure RTOS FileX용 I/O 드라이버
description: 이 장은 Azure RTOS FileX에 대한 I/O 드라이버를 설명하며 개발자들의 애플리케이션별 드라이버 작성을 지원하도록 설계되었습니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b44822b9d8f16208cf470a84013be5a5ff833325
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811353"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a><span data-ttu-id="4fea0-103">5장 - Azure RTOS FileX용 I/O 드라이버</span><span class="sxs-lookup"><span data-stu-id="4fea0-103">Chapter 5 - I/O Drivers for Azure RTOS FileX</span></span>

<span data-ttu-id="4fea0-104">이 장은 Azure RTOS FileX에 대한 I/O 드라이버를 설명하며 개발자들의 애플리케이션별 드라이버 작성을 지원하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-104">This chapter contains a description of I/O drivers for Azure RTOS FileX and is designed to help developers write application-specific drivers.</span></span>

## <a name="io-driver-introduction"></a><span data-ttu-id="4fea0-105">I/O 드라이버 소개</span><span class="sxs-lookup"><span data-stu-id="4fea0-105">I/O Driver Introduction</span></span>

<span data-ttu-id="4fea0-106">FileX는 여러 미디어 디바이스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-106">FileX supports multiple media devices.</span></span> <span data-ttu-id="4fea0-107">FX_MEDIA 구조는 미디어 디바이스 관리에 필요한 모든 항목을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-107">The FX_MEDIA structure defines everything required to manage a media device.</span></span> <span data-ttu-id="4fea0-108">이 구조에는 미디어 관련 I/O 드라이버와, 드라이버와 FileX 사이에 정보와 상태를 전달하기 위한 관련 매개 변수를 비롯한 모든 미디어 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-108">This structure contains all media information, including the media-specific I/O driver and associated parameters for passing information and status between the driver and FileX.</span></span> <span data-ttu-id="4fea0-109">대부분의 시스템에는 각 FileX 미디어 인스턴스에 대해 고유한 I/O 드라이버가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-109">In most systems, there is a unique I/O driver for each FileX media instance.</span></span>

## <a name="io-driver-entry"></a><span data-ttu-id="4fea0-110">I/O 드라이버 항목</span><span class="sxs-lookup"><span data-stu-id="4fea0-110">I/O Driver Entry</span></span>

<span data-ttu-id="4fea0-111">각 FileX I/O 드라이버에는 ***fx_media_open*** 서비스 호출로 정의된 단일 항목 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-111">Each FileX I/O driver has a single entry function that is defined by the ***fx_media_open*** service call.</span></span> <span data-ttu-id="4fea0-112">드라이버 항목 함수의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-112">The driver entry function has the following format:</span></span>

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

<span data-ttu-id="4fea0-113">FileX는 I/O 드라이버 항목 함수를 호출하여 초기화 및 부트 섹터 읽기를 비롯한 모든 실제 미디어 액세스를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-113">FileX calls the I/O driver entry function to request all physical media access, including initialization and boot sector reading.</span></span> <span data-ttu-id="4fea0-114">드라이버에 대한 요청은 순차적으로 수행됩니다. 즉, FileX는 다른 요청을 보내기 전에 현재 요청이 완료될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-114">Requests made to the driver are done sequentially; i.e., FileX waits for the current request to complete before another request is sent.</span></span>

## <a name="io-driver-requests"></a><span data-ttu-id="4fea0-115">I/O 드라이버 요청</span><span class="sxs-lookup"><span data-stu-id="4fea0-115">I/O Driver Requests</span></span>

<span data-ttu-id="4fea0-116">각 I/O 드라이버에는 단일 항목 함수가 있으므로 FileX는 미디어 제어 블록을 통해 특정 요청을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-116">Because each I/O driver has a single entry function, FileX makes specific requests through the media control block.</span></span> <span data-ttu-id="4fea0-117">특히 **FX_MEDIA** 의 **fx_media_driver_request** 멤버를 사용하여 정확한 드라이버 요청을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-117">Specifically, the  **fx_media_driver_request** member of **FX_MEDIA** is used to specify the exact driver request.</span></span> <span data-ttu-id="4fea0-118">I/o 드라이버는 **FX_MEDIA** 의 **fx_media_driver_status** 멤버를 통해 요청의 성공 또는 실패를 알립니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-118">The I/O driver communicates the success or failure of the request through the **fx_media_driver_status** member of **FX_MEDIA**.</span></span> <span data-ttu-id="4fea0-119">드라이버 요청이 성공하면 드라이버 반환 전에 **FX_SUCCESS** 가 이 필드에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-119">If the driver request was successful, **FX_SUCCESS** is placed in this field before the driver returns.</span></span> <span data-ttu-id="4fea0-120">그렇지 않고 오류가 검색되면 FX_IO_ERROR가 이 필드에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-120">Otherwise, if an error is detected, FX_IO_ERROR is placed in this field.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="4fea0-121">드라이버 초기화</span><span class="sxs-lookup"><span data-stu-id="4fea0-121">Driver Initialization</span></span>

<span data-ttu-id="4fea0-122">실제 드라이버 초기화 프로세스는 애플리케이션마다 다르지만 일반적으로 데이터 구조 초기화와 가능한 일부 예비 하드웨어 초기화로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-122">Although the actual driver initialization processing is application specific, it usually consists of data structure initialization and possibly some preliminary hardware initialization.</span></span> <span data-ttu-id="4fea0-123">이 요청은 FileX에서 처음으로 수행되며 fx_media_open 서비스 안에서 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-123">This request is the first made by FileX and is done from within the fx_media_open service.</span></span>

<span data-ttu-id="4fea0-124">미디어 쓰기 방지가 검색되면 FX_MEDIA의 드라이버 fx_media_driver_write_protect 멤버를 FX_TRUE로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-124">If media write protection is detected, the driver fx_media_driver_write_protect member of FX_MEDIA should be set to FX_TRUE.</span></span>

<span data-ttu-id="4fea0-125">I/O 드라이버 초기화 요청에 사용되는 FX_MEDIA 멤버는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-125">The following FX_MEDIA members are used for the I/O driver initialization request:</span></span>

|<span data-ttu-id="4fea0-126">FX_MEDIA 멤버</span><span class="sxs-lookup"><span data-stu-id="4fea0-126">FX_MEDIA member</span></span>|<span data-ttu-id="4fea0-127">의미</span><span class="sxs-lookup"><span data-stu-id="4fea0-127">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="4fea0-128">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="4fea0-128">fx_media_driver_request</span></span>|<span data-ttu-id="4fea0-129">FX_DRIVER_INIT</span><span class="sxs-lookup"><span data-stu-id="4fea0-129">FX_DRIVER_INIT</span></span>|

<span data-ttu-id="4fea0-130">FileX는 섹터를 더 이상 사용하지 않을 때 애플리케이션 드라이버에 알리는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-130">FileX provides a mechanism to inform the application driver when sectors are no longer being used.</span></span> <span data-ttu-id="4fea0-131">이것은 FLASH에 매핑된 모든 사용 중인 논리 섹터를 관리해야 하는 FLASH 메모리 관리자에게 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-131">This is especially useful for FLASH memory managers that must manage all in-use logical sectors mapped to the FLASH.</span></span>

<span data-ttu-id="4fea0-132">이러한 여유 섹터 알림이 필요한 경우 애플리케이션 드라이버는 간단히 **FX_MEDIA** 구조의 *fx_media_driver_free_sector_update* 필드를 **FX_TRUE** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-132">If such notification of free sectors is required, the application driver simply sets the *fx_media_driver_free_sector_update* field in the associated **FX_MEDIA** structure to **FX_TRUE**.</span></span> <span data-ttu-id="4fea0-133">설정 후 FileX는 하나 이상의 연속 섹터가 여유 상태가 되었음을 표시하는 **_FX_DRIVER_RELEASE_SECTORS_** I/O 드라이버 호출을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-133">After set, FileX makes a **_FX_DRIVER_RELEASE_SECTORS_** I/O driver call indicating when one or more consecutive sectors becomes free.</span></span>

### <a name="boot-sector-read"></a><span data-ttu-id="4fea0-134">부트 섹터 읽기</span><span class="sxs-lookup"><span data-stu-id="4fea0-134">Boot Sector Read</span></span>

<span data-ttu-id="4fea0-135">FileX는 표준 읽기 요청을 사용하는 대신 미디어의 부트 섹터를 읽기 위한 특정 요청을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-135">Instead of using a standard read request, FileX makes a specific request to read the media's boot sector.</span></span> <span data-ttu-id="4fea0-136">I/O 드라이버 부트 섹터 읽기 요청에 사용되는 **FX_MEDIA** 멤버는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-136">The following **FX_MEDIA** members are used for the I/O driver boot sector read request:</span></span>

|<span data-ttu-id="4fea0-137">FX_MEDIA 멤버</span><span class="sxs-lookup"><span data-stu-id="4fea0-137">FX_MEDIA member</span></span>|<span data-ttu-id="4fea0-138">의미</span><span class="sxs-lookup"><span data-stu-id="4fea0-138">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="4fea0-139">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="4fea0-139">fx_media_driver_request</span></span>| <span data-ttu-id="4fea0-140">FX_DRIVER_BOOT_READ</span><span class="sxs-lookup"><span data-stu-id="4fea0-140">FX_DRIVER_BOOT_READ</span></span>|
|<span data-ttu-id="4fea0-141">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="4fea0-141">fx_media_driver_buffer</span></span>| <span data-ttu-id="4fea0-142">부트 섹터의 대상 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-142">Address of destination for boot sector.</span></span>|

### <a name="boot-sector-write"></a><span data-ttu-id="4fea0-143">부트 섹터 쓰기</span><span class="sxs-lookup"><span data-stu-id="4fea0-143">Boot Sector Write</span></span>

<span data-ttu-id="4fea0-144">FileX는 표준 쓰기 요청을 사용하는 대신 미디어의 부트 섹터에 쓰기 위한 특정 요청을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-144">Instead of using a standard write request, FileX makes a specific request to write the media's boot sector.</span></span> <span data-ttu-id="4fea0-145">I/O 드라이버 부트 섹터 쓰기 요청에 사용되는 **FX_MEDIA** 멤버는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-145">The following **FX_MEDIA** members are used for the I/O driver boot sector write request:</span></span>

|<span data-ttu-id="4fea0-146">FX_MEDIA 멤버</span><span class="sxs-lookup"><span data-stu-id="4fea0-146">FX_MEDIA member</span></span>|<span data-ttu-id="4fea0-147">의미</span><span class="sxs-lookup"><span data-stu-id="4fea0-147">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="4fea0-148">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="4fea0-148">fx_media_driver_request</span></span>| <span data-ttu-id="4fea0-149">FX_DRIVER_BOOT_WRITE</span><span class="sxs-lookup"><span data-stu-id="4fea0-149">FX_DRIVER_BOOT_WRITE</span></span>|
|<span data-ttu-id="4fea0-150">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="4fea0-150">fx_media_driver_buffer</span></span>| <span data-ttu-id="4fea0-151">부트 섹터의 원본 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-151">Address of source for boot sector.</span></span>|

### <a name="sector-read"></a><span data-ttu-id="4fea0-152">섹터 읽기</span><span class="sxs-lookup"><span data-stu-id="4fea0-152">Sector Read</span></span>

<span data-ttu-id="4fea0-153">FileX는 I/O 드라이버에 대한 읽기 요청을 실행하여 하나 이상의 섹터를 메모리로 읽어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-153">FileX reads one or more sectors into memory by issuing a read request to the I/O driver.</span></span> <span data-ttu-id="4fea0-154">I/O 드라이버 읽기 요청에 사용되는 **FX_MEDIA** 멤버는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-154">The following **FX_MEDIA** members are used for the I/O driver read request:</span></span>

|<span data-ttu-id="4fea0-155">FX_MEDIA 멤버</span><span class="sxs-lookup"><span data-stu-id="4fea0-155">FX_MEDIA member</span></span>|<span data-ttu-id="4fea0-156">의미</span><span class="sxs-lookup"><span data-stu-id="4fea0-156">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="4fea0-157">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="4fea0-157">fx_media_driver_request</span></span>| <span data-ttu-id="4fea0-158">FX_DRIVER_READ</span><span class="sxs-lookup"><span data-stu-id="4fea0-158">FX_DRIVER_READ</span></span>|
|<span data-ttu-id="4fea0-159">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="4fea0-159">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="4fea0-160">읽을 논리 섹터</span><span class="sxs-lookup"><span data-stu-id="4fea0-160">Logical sector to read</span></span>|
|<span data-ttu-id="4fea0-161">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="4fea0-161">fx_media_driver_sectors</span></span>|<span data-ttu-id="4fea0-162">읽을 섹터 수</span><span class="sxs-lookup"><span data-stu-id="4fea0-162">Number of sectors to read</span></span>|
|<span data-ttu-id="4fea0-163">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="4fea0-163">fx_media_driver_buffer</span></span>|<span data-ttu-id="4fea0-164">읽은 섹터에 대한 대상 버퍼</span><span class="sxs-lookup"><span data-stu-id="4fea0-164">Destination buffer for sector(s) read</span></span>|
|<span data-ttu-id="4fea0-165">fx_media_driver_data_sector_read</span><span class="sxs-lookup"><span data-stu-id="4fea0-165">fx_media_driver_data_sector_read</span></span>|<span data-ttu-id="4fea0-166">파일 데이터 섹터가 요청된 경우 FX_TRUE로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-166">Set to FX_TRUE if a file data sector is requested.</span></span> <span data-ttu-id="4fea0-167">그렇지 않고 시스템 섹터(FAT 또는 디렉터리 섹터)가 요청된 경우 FX_FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-167">Otherwise, FX_FALSE if a system sector (FAT or directory sector) is requested.</span></span>|
|<span data-ttu-id="4fea0-168">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="4fea0-168">fx_media_driver_sector_type</span></span>|<span data-ttu-id="4fea0-169">다음과 같이 요청된 섹터의 명시적 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-169">Defines the explicit type of sector requested, as follows:</span></span><br /><span data-ttu-id="4fea0-170">FX_FAT_SECTOR (2)</span><span class="sxs-lookup"><span data-stu-id="4fea0-170">FX_FAT_SECTOR (2)</span></span><br /><span data-ttu-id="4fea0-171">FX_DIRECTORY_SECTOR (3)</span><span class="sxs-lookup"><span data-stu-id="4fea0-171">FX_DIRECTORY_SECTOR (3)</span></span><br /><span data-ttu-id="4fea0-172">FX_DATA_SECTOR (4)</span><span class="sxs-lookup"><span data-stu-id="4fea0-172">FX_DATA_SECTOR (4)</span></span>|

### <a name="sector-write"></a><span data-ttu-id="4fea0-173">섹터 쓰기</span><span class="sxs-lookup"><span data-stu-id="4fea0-173">Sector Write</span></span>

<span data-ttu-id="4fea0-174">FileX는 I/O 드라이버에 대한 쓰기 요청을 실행하여 실제 미디어에 하나 이상의 섹터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-174">FileX writes one or more sectors to the physical media by issuing a write request to the I/O driver.</span></span> <span data-ttu-id="4fea0-175">I/O 드라이버 쓰기 요청에 사용되는 FX_MEDIA 멤버는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-175">The following FX_MEDIA members are used for the I/O driver write request:</span></span>

|<span data-ttu-id="4fea0-176">FX_MEDIA 멤버</span><span class="sxs-lookup"><span data-stu-id="4fea0-176">FX_MEDIA member</span></span>| <span data-ttu-id="4fea0-177">의미</span><span class="sxs-lookup"><span data-stu-id="4fea0-177">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="4fea0-178">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="4fea0-178">fx_media_driver_request</span></span>|<span data-ttu-id="4fea0-179">FX_DRIVER_WRITE</span><span class="sxs-lookup"><span data-stu-id="4fea0-179">FX_DRIVER_WRITE</span></span>|
|<span data-ttu-id="4fea0-180">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="4fea0-180">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="4fea0-181">쓸 논리 섹터</span><span class="sxs-lookup"><span data-stu-id="4fea0-181">Logical sector to write</span></span>|
|<span data-ttu-id="4fea0-182">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="4fea0-182">fx_media_driver_sectors</span></span>|<span data-ttu-id="4fea0-183">쓸 섹터 수</span><span class="sxs-lookup"><span data-stu-id="4fea0-183">Number of sectors to write</span></span>|
|<span data-ttu-id="4fea0-184">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="4fea0-184">fx_media_driver_buffer</span></span>|<span data-ttu-id="4fea0-185">쓸 섹터의 원본 버퍼</span><span class="sxs-lookup"><span data-stu-id="4fea0-185">Source buffer for sector(s) to write</span></span>|
|<span data-ttu-id="4fea0-186">fx_media_driver_system_write</span><span class="sxs-lookup"><span data-stu-id="4fea0-186">fx_media_driver_system_write</span></span>| <span data-ttu-id="4fea0-187">시스템 섹터(FAT 또는 디렉터리 섹터)가 요청된 경우 FX_TRUE로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-187">Set to FX_TRUE if a system sector is requested (FAT or directory sector).</span></span> <span data-ttu-id="4fea0-188">그 밖에 파일 데이터 섹터가 요청된 경우 FX_FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-188">Otherwise, FX_FALSE if a file data sector is requested.</span></span>|
|<span data-ttu-id="4fea0-189">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="4fea0-189">fx_media_driver_sector_type</span></span>|<span data-ttu-id="4fea0-190">다음과 같이 요청된 섹터의 명시적 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-190">Defines the explicit type of sector requested, as follows:</span></span>
<span data-ttu-id="4fea0-191">FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4)|</span><span class="sxs-lookup"><span data-stu-id="4fea0-191">FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4)|</span></span>

### <a name="driver-flush"></a><span data-ttu-id="4fea0-192">드라이버 플러시</span><span class="sxs-lookup"><span data-stu-id="4fea0-192">Driver Flush</span></span>

<span data-ttu-id="4fea0-193">FileX는 I/O 드라이버에 대한 플러시 요청을 실행하여 현재 드라이버 섹터 캐시에 있는 모든 섹터를 실제 미디어에 플러시합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-193">FileX flushes all sectors currently in the driver's sector cache to the physical media by issuing a flush request to the I/O driver.</span></span> <span data-ttu-id="4fea0-194">물론 드라이버가 섹터를 캐싱하지 않는 경우 이 요청에 드라이버 처리가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-194">Of course, if the driver is not caching sectors, this request requires no driver processing.</span></span> <span data-ttu-id="4fea0-195">I/O 드라이버 플러시 요청에 사용되는 FX_MEDIA 멤버는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-195">The following FX_MEDIA members are used for the I/O driver flush request:</span></span>

|<span data-ttu-id="4fea0-196">FX_MEDIA 멤버</span><span class="sxs-lookup"><span data-stu-id="4fea0-196">FX_MEDIA member</span></span>| <span data-ttu-id="4fea0-197">의미</span><span class="sxs-lookup"><span data-stu-id="4fea0-197">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="4fea0-198">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="4fea0-198">fx_media_driver_request</span></span>|<span data-ttu-id="4fea0-199">FX_DRIVER_FLUSH</span><span class="sxs-lookup"><span data-stu-id="4fea0-199">FX_DRIVER_FLUSH</span></span>|

### <a name="driver-abort"></a><span data-ttu-id="4fea0-200">드라이버 중단</span><span class="sxs-lookup"><span data-stu-id="4fea0-200">Driver Abort</span></span>

<span data-ttu-id="4fea0-201">FileX는 I/O 드라이버에 대한 중단 요청을 실행하여 실제 미디어에서의 추가적인 모든 I/O 작업을 중단하도록 드라이버에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-201">FileX informs the driver to abort all further physical I/O activity with the physical media by issuing an abort request to the I/O driver.</span></span> <span data-ttu-id="4fea0-202">드라이버는 다시 초기화되기 전까지는 I/O를 더 이상 수행하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-202">The driver should not perform any I/O again until it is re-initialized.</span></span> <span data-ttu-id="4fea0-203">I/O 드라이버 중단 요청에 사용되는 FX_MEDIA 멤버는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-203">The following FX_MEDIA members are used for the I/O driver abort request:</span></span>

|<span data-ttu-id="4fea0-204">FX_MEDIA 멤버</span><span class="sxs-lookup"><span data-stu-id="4fea0-204">FX_MEDIA member</span></span>| <span data-ttu-id="4fea0-205">의미</span><span class="sxs-lookup"><span data-stu-id="4fea0-205">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="4fea0-206">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="4fea0-206">fx_media_driver_request</span></span>| <span data-ttu-id="4fea0-207">FX_DRIVER_ABORT</span><span class="sxs-lookup"><span data-stu-id="4fea0-207">FX_DRIVER_ABORT</span></span>|

### <a name="release-sectors"></a><span data-ttu-id="4fea0-208">릴리스 섹터</span><span class="sxs-lookup"><span data-stu-id="4fea0-208">Release Sectors</span></span>

<span data-ttu-id="4fea0-209">초기화하는 동안 드라이버에서 이전에 선택한 경우 FileX는 하나 이상의 연속 섹터가 여유 상태가 될 때마다 드라이버에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-209">If previously selected by the driver during initialization, FileX informs the driver whenever one or more consecutive sectors become free.</span></span> <span data-ttu-id="4fea0-210">드라이버가 실제로 FLASH 관리자인 경우 이 정보를 사용하여 FLASH 관리자에게 해당 섹터가 더 이상 필요하지 않음을 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-210">If the driver is actually a FLASH manager, this information can be used to tell the FLASH manager that these sectors are no longer needed.</span></span> <span data-ttu-id="4fea0-211">I/O 드라이버 릴리스 요청에 사용되는 **FX_MEDIA** 멤버는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-211">The following **FX_MEDIA** members are used for the I/O release sectors request:</span></span>

|<span data-ttu-id="4fea0-212">FX_MEDIA 멤버</span><span class="sxs-lookup"><span data-stu-id="4fea0-212">FX_MEDIA member</span></span>| <span data-ttu-id="4fea0-213">의미</span><span class="sxs-lookup"><span data-stu-id="4fea0-213">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="4fea0-214">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="4fea0-214">fx_media_driver_request</span></span>|<span data-ttu-id="4fea0-215">FX_DRIVER_RELEASE_SECTORS</span><span class="sxs-lookup"><span data-stu-id="4fea0-215">FX_DRIVER_RELEASE_SECTORS</span></span>|
|<span data-ttu-id="4fea0-216">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="4fea0-216">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="4fea0-217">여유 섹터 시작</span><span class="sxs-lookup"><span data-stu-id="4fea0-217">Start of free sector</span></span>|
|<span data-ttu-id="4fea0-218">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="4fea0-218">fx_media_driver_sectors</span></span>|<span data-ttu-id="4fea0-219">여유 섹터 수</span><span class="sxs-lookup"><span data-stu-id="4fea0-219">Number of free sectors</span></span>|

### <a name="driver-suspension"></a><span data-ttu-id="4fea0-220">드라이버 일시 중단</span><span class="sxs-lookup"><span data-stu-id="4fea0-220">Driver Suspension</span></span>

<span data-ttu-id="4fea0-221">실제 미디어에서의 I/O에는 다소 시간이 걸릴 수 있으므로 호출 스레드를 일시 중단하는 것이 바람직한 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-221">Because I/O with physical media may take some time, suspending the calling thread is often desirable.</span></span> <span data-ttu-id="4fea0-222">물론 기본 I/O 작업의 완료가 인터럽트 기반인 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-222">Of course, this assumes completion of the underlying I/O operation is interrupt driven.</span></span> <span data-ttu-id="4fea0-223">그렇다면 스레드 일시 중단은 ThreadX 세마포를 사용하여 쉽게 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-223">If so, thread suspension is easily implemented with a ThreadX semaphore.</span></span> <span data-ttu-id="4fea0-224">입력 또는 출력 작업 시작 후 I/O 드라이버는 자체 내부 I/O 세마포에 대해 일시 중단됩니다(드라이버 초기화 중에 최초값 0으로 만들어짐).</span><span class="sxs-lookup"><span data-stu-id="4fea0-224">After starting the input or output operation, the I/O driver suspends on its own internal I/O semaphore (created with an initial count of zero during driver initialization).</span></span> <span data-ttu-id="4fea0-225">드라이버 I/O 완료 인터럽트 처리 과정에서 동일한 I/O 세마포가 설정되어 일시 중단된 스레드를 깨우게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-225">As part of the driver I/O completion interrupt processing, the same I/O semaphore is set, which in turn wakes up the suspended thread.</span></span>

### <a name="sector-translation"></a><span data-ttu-id="4fea0-226">섹터 변환</span><span class="sxs-lookup"><span data-stu-id="4fea0-226">Sector Translation</span></span>

<span data-ttu-id="4fea0-227">FileX는 미디어를 선형 논리 섹터로 보기 때문에 I/O 드라이버에 대한 I/O 요청은 논리 섹터를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-227">Because FileX views the media as linear logical sectors, I/O requests made to the I/O driver are made with logical sectors.</span></span> <span data-ttu-id="4fea0-228">미디어의 논리적 섹터와, 헤드, 트랙, 물리적 섹터 등이 포함될 수 있는 실제 구조 정보 간의 변환은 드라이버가 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-228">It is the driver's responsibility to translate between logical sectors and the physical geometry of the media, which may include heads, tracks, and physical sectors.</span></span> <span data-ttu-id="4fea0-229">FLASH 및 RAM 디스크 미디어의 경우 논리 섹터는 일반적으로 디렉터리를 실제 섹터에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-229">For FLASH and RAM disk media, the logical sectors typically map directory to physical sectors.</span></span> <span data-ttu-id="4fea0-230">어떤 경우든 I/O 드라이버에서 논리적 및 실제 섹터의 매핑을 수행하기 위한 일반적인 수식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-230">In any case, here are the typical formulas to perform the logical to physical sector mapping in the I/O driver:</span></span>

```c
media_ptr -> fx_media_driver_physical_sector =
    (media_ptr -> fx_media_driver_logical_sector % media_ptr -> fx_media_sectors_per_track) + 1;

media_ptr -> fx_media_driver_physical_head =
    (media_ptr -> fx_media_driver_logical_sector/ media_ptr ->
    fx_media_sectors_per_track) % media_ptr -> fx_media_heads;

media_ptr -> fx_media_driver_physical_track =(media_ptr ->
    fx_media_driver_logical_sector/ (media_ptr -> fx_media_sectors_per_track *
    media_ptr -> fx_media_heads)));
```

<span data-ttu-id="4fea0-231">실제 섹터는 1부터 시작하지만 논리 섹터는 0부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-231">Note that physical sectors start at one, while logical sectors start at zero.</span></span>

### <a name="hidden-sectors"></a><span data-ttu-id="4fea0-232">숨겨진 섹터</span><span class="sxs-lookup"><span data-stu-id="4fea0-232">Hidden Sectors</span></span>

<span data-ttu-id="4fea0-233">미디어의 부트 레코드 앞에 숨겨진 섹터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-233">Hidden sectors resided prior to the boot record on the media.</span></span> <span data-ttu-id="4fea0-234">이러한 파일은 실제로 FAT 파일 시스템 레이아웃의 범위를 벗어나므로 드라이버에서 수행하는 각 논리 섹터 작업에서 고려되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-234">Because they are really outside the scope of the FAT file system layout, they must be accounted for in each logical sector operation the driver does.</span></span>

### <a name="media-write-protect"></a><span data-ttu-id="4fea0-235">미디어 쓰기 방지</span><span class="sxs-lookup"><span data-stu-id="4fea0-235">Media Write Protect</span></span>

<span data-ttu-id="4fea0-236">FileX 드라이버는 미디어 제어 블록에서 fx_media_driver_write_protect 필드를 설정하여 쓰기 방지를 켤 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-236">The FileX driver can turn on write protect by setting the fx_media_driver_write_protect field in the media control block.</span></span> <span data-ttu-id="4fea0-237">이로 인해 미디어에 대한 쓰기 시도에서 FileX 호출이 수행되면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-237">This will cause an error to be returned if any FileX calls are made in an attempt to write to the media.</span></span>

## <a name="sample-ram-driver"></a><span data-ttu-id="4fea0-238">샘플 RAM 드라이버</span><span class="sxs-lookup"><span data-stu-id="4fea0-238">Sample RAM Driver</span></span>

<span data-ttu-id="4fea0-239">FileX 데모 시스템은 작은 RAM 디스크 드라이버와 함께 제공되며 fx_ram_driver.c 파일에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-239">The FileX demonstration system is delivered with a small RAM disk driver, which is defined in the file fx_ram_driver.c.</span></span> <span data-ttu-id="4fea0-240">이 드라이버는 32K 메모리 공간을 가정하고 256 128바이트 섹터에 대한 부트 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-240">The driver assumes a 32K memory space and creates a boot record for 256 128-byte sectors.</span></span> <span data-ttu-id="4fea0-241">이 파일은 애플리케이션별 FileX I/O 드라이버를 구현하는 방법에 대한 좋은 예제가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4fea0-241">This file provides a good example of how to implement application specific FileX I/O drivers.</span></span>

```c
/*FUNCTION: _fx_ram_driver
RELEASE: PORTABLE C 5.7
AUTHOR: William E. Lamie, Microsoft, Inc.
DESCRIPTION: This function is the entry point to the generic
    RAM disk driver that is delivered with all versions of FileX.
    The format of the RAM disk is easily modified by calling fx_media_format prior to opening the media.

    This driver also serves as a template for developing FileX drivers
    for actual devices. Simply replace the read/write sector logic
    with calls to read/write from the appropriate physical device.

FileX RAM/FLASH structures look like the following:
Physical Sector             Contents
    0                         Boot record
    1                         FAT Area Start
    +FAT Sectors             Root Directory Start
    +Directory Sectors         Data Sector Start

INPUT: media_ptr Media control block pointer
OUTPUT: None
CALLS:     _fx_utility_memory_copy Copy sector memory
        _fx_utility_16_unsigned_read Read 16-bit unsigned
CALLED BY: FileX System Functions
RELEASE HISTORY:

    DATE         NAME         DESCRIPTION
    12-12-2005     William E.     Lamie Initial Version 5.0
    07-18-2007     William E.     Lamie Modified comment(s),
                                resulting in version 5.1
    03-01-2009     William E.     Lamie Modified comment(s),
                                resulting in version 5.2
    11-01-2015     William E.     Lamie Modified comment(s),
                                resulting in version 5.3
    04-15-2016     William E.     Lamie Modified comment(s),
                                resulting in version 5.4
    04-03-2017     William E.     Lamie Modified comment(s),
                                fixed compiler warnings,
                                resulting in version 5.5
    12-01-2018     William E.     Lamie Modified comment(s),
                                checked buffer overflow,
                                resulting in version 5.6
    08-15-2019     William E.     Lamie Modified comment(s),
                                resulting in version 5.7
*/

VOID _fx_ram_driver(FX_MEDIA *media_ptr) { UCHAR *source_buffer;
                                           UCHAR *destination_buffer;
                                           UINT bytes_per_sector;

    /* There are several useful/important pieces of information contained
        in the media structure, some of which are supplied by FileX and
        others are for the driver to setup. The following
        is a summary of the necessary FX_MEDIA structure members:
    FX_MEDIA Member                     Meaning

    fx_media_driver_request             FileX request type.
        Valid requests from FileX are as follows:
        FX_DRIVER_READ
        FX_DRIVER_WRITE
        FX_DRIVER_FLUSH
        FX_DRIVER_ABORT
        FX_DRIVER_INIT
        FX_DRIVER_BOOT_READ
        FX_DRIVER_RELEASE_SECTORS
        FX_DRIVER_BOOT_WRITE FX_DRIVER_UNINIT

    fx_media_driver_status              This value is RETURNED by the driver.
        If the operation is successful, this field should be set to FX_SUCCESS
        for before returning. Otherwise, if an error occurred, this field should be set to FX_IO_ERROR.

    fx_media_driver_buffer              Pointer to buffer to read or write sector data. This is supplied by FileX.

    fx_media_driver_logical_sector      Logical sector FileX is requesting.
    fx_media_driver_sectors             Number of sectors FileX is requesting.

    The following is a summary of the optional FX_MEDIA structure members: FX_MEDIA Member Meaning

    fx_media_driver_info                Pointer to any additional information or memory.
        This is optional for the driver use and is setup from the fx_media_open call.
        The RAM disk uses this pointer for the RAM disk memory itself.

    fx_media_driver_write_protect       The DRIVER sets this to FX_TRUE when media is write protected.
        This is typically done in initialization, but can be done anytime.

    fx_media_driver_free_sector_update  The DRIVER sets this to FX_TRUE when it needs
        to know when clusters are released. This is important for FLASH wear-leveling drivers.

    fx_media_driver_system_write        FileX sets this flag to FX_TRUE if the sector
        being written is a system sector, e.g., a boot, FAT, or directory sector.
        The driver may choose to use this to initiate error recovery logic for greater fault
        tolerance. fx_media_driver_data_sector_read FileX sets this flag to FX_TRUE
        if the sector(s) being read are file data sectors, i.e., NOT system sectors.

    fx_media_driver_sector_type         FileX sets this variable to the specific type of
        sector being read or written. The following sector types are identified:
            FX_UNKNOWN_SECTOR
            FX_BOOT_SECTOR
            FX_FAT_SECTOR
            FX_DIRECTORY_SECTOR
            FX_DATA_SECTOR */

    /* Process the driver request specified in the media control block. */

    switch (media_ptr -> fx_media_driver_request){

        case FX_DRIVER_READ: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
            is pointed to by the fx_media_driver_info pointer, which is supplied
            by the application in the call to fx_media_open. */

            source_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the RAM sector into the destination. */

             _fx_utility_memory_copy(source_buffer,
                media_ptr -> fx_media_driver_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_WRITE: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
                is pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */

            destination_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the source to the RAM sector. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_FLUSH: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_ABORT: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_INIT: {

            /* FLASH drivers are responsible for setting several fields
                in the media structure, as follows:
                media_ptr -> fx_media_driver_free_sector_update media_ptr ->
                fx_media_driver_write_protect
                The fx_media_driver_free_sector_update flag is used to instruct
                FileX to inform the driver whenever sectors are not being used.
                This is especially useful for FLASH managers so they don't have
                maintain mapping for sectors no longer in use.
                The fx_media_driver_write_protect flag can be set anytime by
                the driver to indicate the media is not writable. Write attempts
                made when this flag is set are returned as errors. */
            /* Perform basic initialization here... since the boot record is going
                to be read subsequently and again for volume name requests. */
            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

         case FX_DRIVER_UNINIT: {

            /* There is nothing to do in this case for the RAM driver.
                For actual devices some shutdown processing may be necessary. */

            /* Successful driver request. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_READ: {
            /* Read the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is pointed
                to by the fx_media_driver_info pointer, which is supplied by the
                application in the call to fx_media_open. */

            source_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* For RAM driver, determine if the boot record is valid. */

            if ((source_buffer[0] != (UCHAR)0xEB) ||

            ((source_buffer[1] != (UCHAR)0x34) &&

            (source_buffer[1] != (UCHAR)0x76)) || /* exFAT jump code. */

            (source_buffer[2] != (UCHAR)0x90)) {

            /* Invalid boot record, return an error! */
            media_ptr -> fx_media_driver_status = FX_MEDIA_INVALID; return; }

            /* For RAM disk only, pickup the bytes per sector. */

            bytes_per_sector =
                _fx_utility_16_unsigned_read(&source_buffer[FX_BYTES_SECTOR]); #ifdef FX_ENABLE_EXFAT

            /* if byte per sector is zero, then treat it as exFAT volume. */

            if (bytes_per_sector == 0 && (source_buffer[1] == (UCHAR)0x76)) {

            /* Pickup the byte per sector shift, and calculate byte per sector. */ 
            bytes_per_sector = (UINT)(1 << source_buffer[FX_EF_BYTE_PER_SECTOR_SHIFT]);

            }

            #endif /* FX_ENABLE_EXFAT */

            /* Ensure this is less than the media memory size. */
            if (bytes_per_sector \media_ptr -> fx_media_memory_size) {

            media_ptr -> fx_media_driver_status = FX_BUFFER_ERROR; break; }

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(source_buffer, media_ptr -> fx_media_driver_buffer, bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_WRITE: {

            /* Write the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is
                pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */ 
            destination_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        default: {
            /* Invalid driver request. */
            media_ptr -> fx_media_driver_status = FX_IO_ERROR; break;}
    }
}
```
