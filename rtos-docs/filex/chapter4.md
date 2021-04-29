---
title: 4장 - Azure RTOS FileX 서비스 설명
description: 이 장에서는 모든 Azure RTOS FileX 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c9e91244856b322d53f85bdd572bd317a055776a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811359"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a><span data-ttu-id="47325-103">4장 - Azure RTOS FileX 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="47325-103">Chapter 4- Description of Azure RTOS FileX services</span></span>

<span data-ttu-id="47325-104">이 장에서는 모든 Azure RTOS FileX 서비스를 알파벳 순서로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-104">This chapter contains a description of all Azure RTOS FileX services in alphabetic order.</span></span> <span data-ttu-id="47325-105">서비스 이름은 모든 유사한 서비스가 함께 그룹화되도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-105">Service names are designed so all similar services are grouped together.</span></span>

## <a name="fx_directory_attributes_read"></a><span data-ttu-id="47325-106">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-106">fx_directory_attributes_read</span></span>

<span data-ttu-id="47325-107">디렉터리 특성을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-107">Reads directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-108">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-108">Prototype</span></span>

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a><span data-ttu-id="47325-109">Description</span><span class="sxs-lookup"><span data-stu-id="47325-109">Description</span></span>

<span data-ttu-id="47325-110">이 서비스는 지정된 미디어에서 디렉터리의 특성을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-110">This service reads the directory's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-111">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-111">Input Parameters</span></span>

- <span data-ttu-id="47325-112">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-112">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-113">**directory_name**: 요청된 디렉터리의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).</span><span class="sxs-lookup"><span data-stu-id="47325-113">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="47325-114">**attributes** _ptr: 배치할 디렉터리 특성의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-114">**attributes** _ptr: Pointer to the destination for the directory's attributes to be placed.</span></span> <span data-ttu-id="47325-115">디렉터리 특성은 다음과 같은 가능한 설정으로 비트맵 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-115">The directory attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="47325-116">FX_READ_ONLY(0x01)</span><span class="sxs-lookup"><span data-stu-id="47325-116">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="47325-117">FX_HIDDEN(0x02)</span><span class="sxs-lookup"><span data-stu-id="47325-117">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="47325-118">FX_SYSTEM(0x04)</span><span class="sxs-lookup"><span data-stu-id="47325-118">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="47325-119">FX_VOLUME(0x08)</span><span class="sxs-lookup"><span data-stu-id="47325-119">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="47325-120">FX_DIRECTORY(0x10)</span><span class="sxs-lookup"><span data-stu-id="47325-120">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="47325-121">FX_ARCHIVE(0x20)</span><span class="sxs-lookup"><span data-stu-id="47325-121">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-122">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-122">Return Values</span></span>

- <span data-ttu-id="47325-123">**FX_SUCCESS**(0x00) 디렉터리 특성 읽기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-123">**FX_SUCCESS** (0x00) Successful directory attributes read</span></span>
- <span data-ttu-id="47325-124">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-124">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="47325-125">**FX _NOT FOUND**(0x04) 지정된 디렉터리가 미디어에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-125">**FX _NOT FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="47325-126">**FX_NOT_DIRECTORY**(0x0E) 항목이 디렉터리가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-126">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="47325-127">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류</span><span class="sxs-lookup"><span data-stu-id="47325-127">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="47325-128">**FX_FILE_CORRUPT** 0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-128">**FX_FILE_CORRUPT** 0x08) File is corrupted</span></span>
- <span data-ttu-id="47325-129">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터</span><span class="sxs-lookup"><span data-stu-id="47325-129">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="47325-130">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-130">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="47325-131">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-131">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-132">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어</span><span class="sxs-lookup"><span data-stu-id="47325-132">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="47325-133">**FX_PTR_ERROR**(0x18) 잘못된 미디어 포인터</span><span class="sxs-lookup"><span data-stu-id="47325-133">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="47325-134">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-134">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-135">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-135">Allowed From</span></span>

<span data-ttu-id="47325-136">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-136">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-137">예제</span><span class="sxs-lookup"><span data-stu-id="47325-137">Example</span></span>

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a><span data-ttu-id="47325-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-138">See Also</span></span>

- <span data-ttu-id="47325-139">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-139">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-140">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-140">fx_directory_create</span></span>
- <span data-ttu-id="47325-141">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-141">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-142">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-142">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-143">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-143">fx_directory_delete</span></span>
- <span data-ttu-id="47325-144">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-144">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-145">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-145">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-146">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-146">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-147">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-147">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-148">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-148">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-149">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-149">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-150">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-150">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-151">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-151">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-152">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-152">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-153">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-153">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-154">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-154">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-155">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-155">fx_directory_rename</span></span>
- <span data-ttu-id="47325-156">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-156">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-157">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-157">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-158">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-158">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_attributes_set"></a><span data-ttu-id="47325-159">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-159">fx_directory_attributes_set</span></span>

<span data-ttu-id="47325-160">디렉터리 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-160">Sets directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-161">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-161">Prototype</span></span>

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a><span data-ttu-id="47325-162">Description</span><span class="sxs-lookup"><span data-stu-id="47325-162">Description</span></span>

<span data-ttu-id="47325-163">이 서비스는 디렉터리의 특성을 호출자가 지정한 특성으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-163">This service sets the directory's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-164">이 애플리케이션은 서비스와 함께 디렉터리 특성의 하위 집합만 수정할 수 있습니다. 추가 특성을 설정하려고 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-164">*This application is only allowed to modify a subset of the directory's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-165">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-165">Input Parameters</span></span>

- <span data-ttu-id="47325-166">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-166">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-167">**directory_name**: 요청된 디렉터리의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).</span><span class="sxs-lookup"><span data-stu-id="47325-167">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="47325-168">**attributes**: 디렉터리에 대한 새 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-168">**attributes**: The new attributes to this directory.</span></span> <span data-ttu-id="47325-169">유효한 디렉터리 특성은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-169">The valid directory attributes are defined as follows:</span></span>
  - <span data-ttu-id="47325-170">FX_READ_ONLY(0x01)</span><span class="sxs-lookup"><span data-stu-id="47325-170">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="47325-171">FX_HIDDEN(0x02)</span><span class="sxs-lookup"><span data-stu-id="47325-171">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="47325-172">FX_SYSTEM(0x04)</span><span class="sxs-lookup"><span data-stu-id="47325-172">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="47325-173">FX_ARCHIVE(0x20)</span><span class="sxs-lookup"><span data-stu-id="47325-173">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-174">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-174">Return Values</span></span>

- <span data-ttu-id="47325-175">**FX_SUCCESS**(0x00) 디렉터리 특성 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-175">**FX_SUCCESS** (0x00) Successful directory attribute set</span></span>
- <span data-ttu-id="47325-176">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-176">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="47325-177">**FX_NOT_FOUND**(0x04) 지정된 디렉터리가 미디어에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-177">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="47325-178">**FX_NOT_DIRECTORY**(0x0E) 항목이 디렉터리가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-178">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="47325-179">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류</span><span class="sxs-lookup"><span data-stu-id="47325-179">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="47325-180">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-180">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="47325-181">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-181">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="47325-182">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터</span><span class="sxs-lookup"><span data-stu-id="47325-182">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="47325-183">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-183">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="47325-184">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-184">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-185">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어</span><span class="sxs-lookup"><span data-stu-id="47325-185">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="47325-186">**FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-186">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="47325-187">**FX_PTR_ERROR**(0x18) 잘못된 미디어 포인터</span><span class="sxs-lookup"><span data-stu-id="47325-187">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="47325-188">**FX_INVALID_ATTR**(0x19) 잘못된 특성을 선택했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-188">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="47325-189">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-190">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-190">Allowed From</span></span>

<span data-ttu-id="47325-191">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-192">예제</span><span class="sxs-lookup"><span data-stu-id="47325-192">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a><span data-ttu-id="47325-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-193">See Also</span></span>

- <span data-ttu-id="47325-194">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-194">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-195">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-195">fx_directory_create</span></span>
- <span data-ttu-id="47325-196">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-196">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-197">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-197">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-198">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-198">fx_directory_delete</span></span>
- <span data-ttu-id="47325-199">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-199">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-200">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-200">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-201">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-201">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-202">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-202">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-203">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-203">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-204">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-204">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-205">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-205">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-206">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-206">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-207">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-207">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-208">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-208">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-209">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-209">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-210">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-210">fx_directory_rename</span></span>
- <span data-ttu-id="47325-211">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-211">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-212">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-212">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-213">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-213">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_create"></a><span data-ttu-id="47325-214">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-214">fx_directory_create</span></span>

<span data-ttu-id="47325-215">하위 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47325-215">Creates subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-216">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-216">Prototype</span></span>

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a><span data-ttu-id="47325-217">Description</span><span class="sxs-lookup"><span data-stu-id="47325-217">Description</span></span>

<span data-ttu-id="47325-218">이 서비스는 현재 기본 디렉터리 또는 디렉터리 이름에 제공된 경로에 하위 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47325-218">This service creates a subdirectory in the current default directory or in the path supplied in the directory name.</span></span> <span data-ttu-id="47325-219">루트 디렉터리와 달리 하위 디렉터리는 저장할 수 있는 파일 수에 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-219">Unlike the root directory, subdirectories do not have a limit on the number of files they can hold.</span></span> <span data-ttu-id="47325-220">루트 디렉터리는 부팅 레코드에서 결정한 항목 수만 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-220">The root directory can only hold the number of entries determined by the boot record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-221">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-221">Input Parameters</span></span>

- <span data-ttu-id="47325-222">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-222">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-223">**directory_name**: 만들 디렉터리의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).</span><span class="sxs-lookup"><span data-stu-id="47325-223">**directory_name**: Pointer to the name of the directory to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-224">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-224">Return Values</span></span>

- <span data-ttu-id="47325-225">**FX_SUCCESS**(0x00) 디렉터리 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-225">**FX_SUCCESS** (0x00) Successful directory create.</span></span>
- <span data-ttu-id="47325-226">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-226">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="47325-227">**FX_NOT_FOUND**(0x04) 지정된 디렉터리가 미디어에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-227">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="47325-228">**FX_NOT_DIRECTORY**(0x0E) 항목이 디렉터리가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-228">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="47325-229">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류</span><span class="sxs-lookup"><span data-stu-id="47325-229">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="47325-230">**FX_FILE _CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-230">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="47325-231">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터</span><span class="sxs-lookup"><span data-stu-id="47325-231">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="47325-232">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-232">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="47325-233">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-233">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-234">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어</span><span class="sxs-lookup"><span data-stu-id="47325-234">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="47325-235">**FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-235">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="47325-236">**FX_PTR_ERROR**(0x18) 잘못된 미디어 포인터</span><span class="sxs-lookup"><span data-stu-id="47325-236">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="47325-237">**FX_INVALID_ATTR**(0x19) 잘못된 특성을 선택했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-237">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="47325-238">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-238">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-239">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-239">Allowed From</span></span>

<span data-ttu-id="47325-240">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-240">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-241">예제</span><span class="sxs-lookup"><span data-stu-id="47325-241">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a><span data-ttu-id="47325-242">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-242">See Also</span></span>

- <span data-ttu-id="47325-243">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-243">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-244">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-244">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-245">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-245">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-246">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-246">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-247">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-247">fx_directory_delete</span></span>
- <span data-ttu-id="47325-248">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-248">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-249">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-249">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-250">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-250">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-251">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-251">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-252">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-252">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-253">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-253">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-254">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-254">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-255">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-255">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-256">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-256">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-257">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-257">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-258">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-258">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-259">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-259">fx_directory_rename</span></span>
- <span data-ttu-id="47325-260">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-260">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-261">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-261">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-262">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-262">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_get"></a><span data-ttu-id="47325-263">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-263">fx_directory_default_get</span></span>

<span data-ttu-id="47325-264">마지막 기본 디렉터리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-264">Gets last default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-265">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-265">Prototype</span></span>

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="47325-266">Description</span><span class="sxs-lookup"><span data-stu-id="47325-266">Description</span></span>

<span data-ttu-id="47325-267">이 서비스는 ***fx_directory_default_set*** 으로 마지막에 설정한 경로에 대한 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-267">This service returns the pointer to the path last set by ***fx_directory_default_set***.</span></span> <span data-ttu-id="47325-268">기본 디렉터리가 설정되지 않았거나 현재 기본 디렉터리가 루트 디렉터리인 경우 FX_NULL 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-268">If the default directory has not been set or if the current default directory is the root directory, a value of FX_NULL is returned.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-269">내부 경로 문자열의 기본 크기는 256자입니다. **fx_api** 에서 **FX_MAXIMUM_PATH** 를 수정하고 전체 FileX 라이브러리를 다시 빌드하여 이 설정을 변경할 수 있습니다. 문자열 경로는 애플리케이션에 대해 유지되며 FileX에서 내부적으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-269">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-270">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-270">Input Parameters</span></span>

- <span data-ttu-id="47325-271">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-271">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-272">**return_path_name**: 마지막 기본 디렉터리 문자열의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-272">**return_path_name**: Pointer to the destination for the last default directory string.</span></span> <span data-ttu-id="47325-273">기본 디렉터리의 현재 설정이 루트이면 FX_NULL의 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-273">A value of FX_NULL is returned if the current setting of the default directory is the root.</span></span> <span data-ttu-id="47325-274">미디어가 열리면 루트가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-274">When the media is opened, root is the default.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-275">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-275">Return Values</span></span>

- <span data-ttu-id="47325-276">**FX_SUCCESS**(0x00) 기본 디렉터리 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-276">**FX_SUCCESS** (0x00) Successful default directory get</span></span>
- <span data-ttu-id="47325-277">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="47325-278">**FX_PTR_ERROR**(0x18) 미디어 또는 대상 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-278">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="47325-279">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-279">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-280">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-280">Allowed From</span></span>

<span data-ttu-id="47325-281">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-282">예제</span><span class="sxs-lookup"><span data-stu-id="47325-282">Example</span></span>

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a><span data-ttu-id="47325-283">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-283">See Also</span></span>

- <span data-ttu-id="47325-284">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-284">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-285">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-285">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-286">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-286">fx_directory_create</span></span>
- <span data-ttu-id="47325-287">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-287">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-288">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-288">fx_directory_delete</span></span>
- <span data-ttu-id="47325-289">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-289">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-290">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-290">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-291">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-291">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-292">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-292">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-293">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-293">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-294">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-294">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-295">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-295">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-296">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-296">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-297">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-297">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-298">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-298">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-299">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-299">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-300">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-300">fx_directory_rename</span></span>
- <span data-ttu-id="47325-301">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-301">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-302">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-302">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-303">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-303">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_set"></a><span data-ttu-id="47325-304">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-304">fx_directory_default_set</span></span>

<span data-ttu-id="47325-305">기본 디렉터리를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-305">Sets default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-306">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-306">Prototype</span></span>

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="47325-307">Description</span><span class="sxs-lookup"><span data-stu-id="47325-307">Description</span></span>

<span data-ttu-id="47325-308">이 서비스는 미디어의 기본 디렉터리를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-308">This service sets the default directory of the media.</span></span> <span data-ttu-id="47325-309">FX_NULL의 값이 제공되면 기본 디렉터리가 미디어의 루트 디렉터리로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-309">If a value of FX_NULL is supplied, the default directory is set to the media's root directory.</span></span> <span data-ttu-id="47325-310">경로를 명시적으로 지정하지 않는 모든 후속 파일 작업은 기본적으로 이 디렉터리로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-310">All subsequent file operations that do not explicitly specify a path will default to this directory.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-311">내부 경로 문자열의 기본 크기는 256자입니다. **fx_api** 에서 **FX_MAXIMUM_PATH** 를 수정하고 전체 FileX 라이브러리를 다시 빌드하여 이 설정을 변경할 수 있습니다. 문자열 경로는 애플리케이션에 대해 유지되며 FileX에서 내부적으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-311">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-312">애플리케이션에서 제공하는 이름의 경우 FileX는 디렉터리, 하위 디렉터리 및 파일 이름을 구분하기 위해 백슬래시(\\)와 슬래시(/) 문자 둘 다를 지원합니다. 그러나 FileX는 애플리케이션으로 반환되는 경로에는 백슬래시 문자만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-312">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-313">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-313">Input Parameters</span></span>

- <span data-ttu-id="47325-314">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-314">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-315">**new_path_name**: 새 기본 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-315">**new_path_name**: Pointer to new default directory name.</span></span> <span data-ttu-id="47325-316">FX_NULL의 값이 제공되면 미디어의 기본 디렉터리가 미디어의 루트 디렉터리로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-316">If a value of FX_NULL is supplied, the default directory of the media is set to the media's root directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-317">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-317">Return Values</span></span>

- <span data-ttu-id="47325-318">**FX_SUCCESS**(0x00) 기본 디렉터리 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-318">**FX_SUCCESS** (0x00)  Successful default directory set</span></span>
- <span data-ttu-id="47325-319">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-319">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="47325-320">**FX_INVALID_PATH**(0x0D) 새 디렉터리를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-320">**FX_INVALID_PATH** (0x0D) New directory could not be found</span></span>
- <span data-ttu-id="47325-321">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-321">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="47325-322">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-322">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-323">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-323">Allowed From</span></span>

<span data-ttu-id="47325-324">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-324">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-325">예제</span><span class="sxs-lookup"><span data-stu-id="47325-325">Example</span></span>

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a><span data-ttu-id="47325-326">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-326">See Also</span></span>

- <span data-ttu-id="47325-327">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-327">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-328">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-328">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-329">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-329">fx_directory_create</span></span>
- <span data-ttu-id="47325-330">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-330">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-331">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-331">fx_directory_delete</span></span>
- <span data-ttu-id="47325-332">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-332">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-333">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-333">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-334">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-334">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-335">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-335">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-336">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-336">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-337">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-337">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-338">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-338">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-339">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-339">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-340">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-340">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-341">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-341">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-342">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-342">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-343">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-343">fx_directory_rename</span></span>
- <span data-ttu-id="47325-344">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-344">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-345">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-345">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-346">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-346">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_delete"></a><span data-ttu-id="47325-347">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-347">fx_directory_delete</span></span>

<span data-ttu-id="47325-348">하위 디렉터리를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-348">Deletes subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-349">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-349">Prototype</span></span>

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="47325-350">Description</span><span class="sxs-lookup"><span data-stu-id="47325-350">Description</span></span>

<span data-ttu-id="47325-351">이 서비스는 지정된 디렉터리를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-351">This service deletes the specified directory.</span></span> <span data-ttu-id="47325-352">삭제하려면 디렉터리가 비어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-352">Note that the directory must be empty to delete it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-353">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-353">Input Parameters</span></span>

- <span data-ttu-id="47325-354">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-354">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-355">**directory_name**: 삭제할 디렉터리 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).</span><span class="sxs-lookup"><span data-stu-id="47325-355">**directory_name**: Pointer to name of directory to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-356">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-356">Return Values</span></span>

- <span data-ttu-id="47325-357">**FX_SUCCESS**(0x00) 디렉터리 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-357">**FX_SUCCESS** (0x00) Successful directory delete</span></span>
- <span data-ttu-id="47325-358">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-358">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="47325-359">**FX_NOT_FOUND**(0x04) 지정된 디렉터리를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-359">**FX_NOT_FOUND** (0x04) Specified directory was not found</span></span>
- <span data-ttu-id="47325-360">**FX_DIR_NOT_EMPTY**(0x10) 지정된 디렉터리가 비어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-360">**FX_DIR_NOT_EMPTY** (0x10) Specified directory is not empty</span></span>
- <span data-ttu-id="47325-361">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류</span><span class="sxs-lookup"><span data-stu-id="47325-361">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="47325-362">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-362">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="47325-363">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-363">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="47325-364">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터</span><span class="sxs-lookup"><span data-stu-id="47325-364">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="47325-365">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-365">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="47325-366">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-366">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-367">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어</span><span class="sxs-lookup"><span data-stu-id="47325-367">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="47325-368">**FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-368">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="47325-369">**FX_NOT_DIRECTORY**(0x0E) 디렉터리 항목이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-369">**FX_NOT_DIRECTORY** (0x0E) Not a directory entry</span></span>
- <span data-ttu-id="47325-370">**FX_PTR_ERROR**(0x18) 잘못된 미디어 포인터</span><span class="sxs-lookup"><span data-stu-id="47325-370">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="47325-371">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-371">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-372">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-372">Allowed From</span></span>

<span data-ttu-id="47325-373">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-373">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-374">예제</span><span class="sxs-lookup"><span data-stu-id="47325-374">Example</span></span>
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a><span data-ttu-id="47325-375">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-375">See Also</span></span>

- <span data-ttu-id="47325-376">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-376">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-377">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-377">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-378">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-378">fx_directory_create</span></span>
- <span data-ttu-id="47325-379">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-379">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-380">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-380">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-381">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-381">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-382">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-382">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-383">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-383">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-384">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-384">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-385">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-385">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-386">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-386">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-387">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-387">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-388">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-388">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-389">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-389">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-390">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-390">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-391">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-391">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-392">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-392">fx_directory_rename</span></span>
- <span data-ttu-id="47325-393">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-393">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-394">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-394">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-395">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-395">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_entry_find"></a><span data-ttu-id="47325-396">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-396">fx_directory_first_entry_find</span></span>

<span data-ttu-id="47325-397">첫 번째 디렉터리 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-397">Gets first directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-398">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-398">Prototype</span></span>

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="47325-399">Description</span><span class="sxs-lookup"><span data-stu-id="47325-399">Description</span></span>

<span data-ttu-id="47325-400">이 서비스는 기본 디렉터리에서 첫 번째 항목 이름을 검색하여 지정된 대상에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-400">This service retrieves the first entry name in the default directory and copies it to the specified destination.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-401">지정된 대상은 **FX_MAX_LONG_NAME_LEN** 으로 정의한 FileX 이름의 최대 크기를 저장할 수 있을 만큼 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-401">*The specified destination must be large enough to hold the maximum sized FileX name, as defined by **FX_MAX_LONG_NAME_LEN.***</span></span>

> [!WARNING]
> <span data-ttu-id="47325-402">로컬이 아닌 경로를 사용하는 경우 디렉터리를 순회하는 동안 (ThreadX 세마포, 뮤텍스 또는 우선 순위 수준 변경에 따라) 다른 애플리케이션 스레드가 이 디렉터리를 변경할 수 없도록 방지해야 합니다. 그러지 않으면 잘못된 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-402">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-403">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-403">Input Parameters</span></span>

- <span data-ttu-id="47325-404">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-404">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-405">**return_entry_name**: 기본 디렉터리에 있는 첫 번째 항목 이름의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-405">**return_entry_name**: Pointer to destination for the first entry name in the default directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-406">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-406">Return Values</span></span>

- <span data-ttu-id="47325-407">**FX_SUCCESS**(0x00) 첫 번째 디렉터리 항목 찾기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-407">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="47325-408">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-408">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="47325-409">**FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-409">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="47325-410">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류</span><span class="sxs-lookup"><span data-stu-id="47325-410">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="47325-411">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-411">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="47325-412">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터</span><span class="sxs-lookup"><span data-stu-id="47325-412">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="47325-413">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-413">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="47325-414">**FX_PTR_ERROR**(0x18) 미디어 또는 대상 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-414">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer</span></span>
- <span data-ttu-id="47325-415">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-415">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-416">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-416">Allowed From</span></span>

<span data-ttu-id="47325-417">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-417">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-418">예제</span><span class="sxs-lookup"><span data-stu-id="47325-418">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a><span data-ttu-id="47325-419">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-419">See Also</span></span>

- <span data-ttu-id="47325-420">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-420">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-421">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-421">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-422">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-422">fx_directory_create</span></span>
- <span data-ttu-id="47325-423">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-423">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-424">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-424">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-425">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-425">fx_directory_delete</span></span>
- <span data-ttu-id="47325-426">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-426">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-427">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-427">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-428">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-428">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-429">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-429">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-430">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-430">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-431">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-431">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-432">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-432">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-433">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-433">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-434">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-434">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-435">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-435">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-436">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-436">fx_directory_rename</span></span>
- <span data-ttu-id="47325-437">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-437">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-438">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-438">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-439">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-439">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="47325-440">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-440">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="47325-441">첫 번째 디렉터리 항목을 모든 정보와 함께 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-441">Gets first directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-442">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-442">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="47325-443">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-443">Input Parameters</span></span>

- <span data-ttu-id="47325-444">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-444">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-445">**directory_name**: 디렉터리 항목 이름의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-445">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="47325-446">적어도 FX_MAX_LONG_NAME_LEN만큼 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-446">Must be at least as big as FX_MAX_LONG_NAME_LEN.</span></span>
- <span data-ttu-id="47325-447">**특성**: null이 아닌 경우 배치할 항목 특성의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-447">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.</span></span> <span data-ttu-id="47325-448">특성은 다음과 같은 가능한 설정과 함께 비트맵 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-448">The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="47325-449">**FX_READ_ONLY**(0x01)</span><span class="sxs-lookup"><span data-stu-id="47325-449">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="47325-450">**FX_HIDDEN**(0x02)</span><span class="sxs-lookup"><span data-stu-id="47325-450">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="47325-451">**FX_SYSTEM**(0x04)</span><span class="sxs-lookup"><span data-stu-id="47325-451">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="47325-452">**FX_VOLUME**(0x08)</span><span class="sxs-lookup"><span data-stu-id="47325-452">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="47325-453">**FX_DIRECTORY**(0x10)</span><span class="sxs-lookup"><span data-stu-id="47325-453">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="47325-454">**FX_ARCHIVE**(0x20)</span><span class="sxs-lookup"><span data-stu-id="47325-454">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="47325-455">**size**: null이 아닌 경우 항목 크기(바이트)의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-455">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="47325-456">**year**: null이 아닌 경우 항목 수정 연도의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-456">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="47325-457">**month**: null이 아닌 경우 항목 수정 월의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-457">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="47325-458">**day**: null이 아닌 경우 항목 수정일의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-458">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="47325-459">**hour**: null이 아닌 경우 항목 수정 시간의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-459">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="47325-460">**minute**: null이 아닌 경우 항목 수정 분의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-460">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="47325-461">**second**: null이 아닌 경우 항목 수정 초의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-461">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-462">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-462">Return Values</span></span>

- <span data-ttu-id="47325-463">**FX_SUCCESS**(0x00) 첫 번째 디렉터리 항목 찾기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-463">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="47325-464">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-464">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="47325-465">**FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-465">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="47325-466">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류</span><span class="sxs-lookup"><span data-stu-id="47325-466">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="47325-467">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-467">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="47325-468">**FX_FILE _CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-468">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="47325-469">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터</span><span class="sxs-lookup"><span data-stu-id="47325-469">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="47325-470">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-470">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="47325-471">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-471">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-472">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어</span><span class="sxs-lookup"><span data-stu-id="47325-472">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="47325-473">**FX_PTR_ERROR**(0x18) 미디어 또는 대상 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-473">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="47325-474">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-474">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-475">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-475">Allowed From</span></span>

<span data-ttu-id="47325-476">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-476">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-477">예제</span><span class="sxs-lookup"><span data-stu-id="47325-477">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
UINT         attributes;
ULONG        size;
UINT         year;
UINT         month;
UINT         day;
UINT         hour;
UINT         minute;
UINT         second;
/* Get the first directory entry in the default directory with full information. */
status = fx_directory_first_full_entry_find(&my_media, entry_name,
    &attributes, &size, &year, &month, &day, &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="47325-478">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-478">See Also</span></span>

- <span data-ttu-id="47325-479">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-479">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-480">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-480">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-481">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-481">fx_directory_create</span></span>
- <span data-ttu-id="47325-482">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-482">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-483">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-483">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-484">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-484">fx_directory_delete</span></span>
- <span data-ttu-id="47325-485">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-485">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-486">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-486">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-487">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-487">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-488">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-488">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-489">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-489">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-490">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-490">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-491">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-491">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-492">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-492">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-493">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-493">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-494">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-494">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-495">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-495">fx_directory_rename</span></span>
- <span data-ttu-id="47325-496">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-496">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-497">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-497">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-498">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-498">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_information_get"></a><span data-ttu-id="47325-499">fx_directory_information_get:</span><span class="sxs-lookup"><span data-stu-id="47325-499">fx_directory_information_get:</span></span>

<span data-ttu-id="47325-500">디렉터리 항목 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-500">Gets directory entry information</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-501">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-501">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="47325-502">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-502">Input Parameters</span></span>

- <span data-ttu-id="47325-503">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-503">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-504">**directory_name**: 디렉터리 항목 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-504">**directory_name**: Pointer to name of the directory entry.</span></span>
- <span data-ttu-id="47325-505">**attributes**: 특성의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-505">**attributes**: Pointer to the destination for the attributes.</span></span>
- <span data-ttu-id="47325-506">**size**: 크기의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-506">**size**: Pointer to the destination for the size.</span></span>
- <span data-ttu-id="47325-507">**year**: 연도의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-507">**year**: Pointer to the destination for the year.</span></span>
- <span data-ttu-id="47325-508">**month**: 월의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-508">**month**: Pointer to the destination for the month.</span></span>
- <span data-ttu-id="47325-509">**day**: 날짜의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-509">**day**: Pointer to the destination for the day.</span></span>
- <span data-ttu-id="47325-510">**hour**: 시간의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-510">**hour**: Pointer to the destination for the hour.</span></span>
- <span data-ttu-id="47325-511">**minute**: 분의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-511">**minute**: Pointer to the destination for the minute.</span></span>
- <span data-ttu-id="47325-512">**second**: 초의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-512">**second**: Pointer to the destination for the second.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-513">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-513">Return Values</span></span>

- <span data-ttu-id="47325-514">**FX_SUCCESS**(0x00) 첫 번째 디렉터리 항목 찾기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-514">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="47325-515">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-515">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="47325-516">**FX_NOT_FOUND**(0x04) 지정된 디렉터리가 미디어에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-516">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="47325-517">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류</span><span class="sxs-lookup"><span data-stu-id="47325-517">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="47325-518">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어</span><span class="sxs-lookup"><span data-stu-id="47325-518">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="47325-519">**FX_FILE _CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-519">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="47325-520">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-520">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="47325-521">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-521">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-522">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터</span><span class="sxs-lookup"><span data-stu-id="47325-522">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="47325-523">**FX_PTR_ERROR**(0x18) 미디어 또는 대상 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-523">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="47325-524">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-524">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-525">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-525">Allowed From</span></span>

<span data-ttu-id="47325-526">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-526">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-527">예제</span><span class="sxs-lookup"><span data-stu-id="47325-527">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status; attributes; year; month; day;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
ULONG        size;
UINT         hour; minute; second;
/* Retrieve information about the directory entry "myfile.txt".*/
status = fx_directory_information_get(&my_media, "myfile.txt", &attributes, &size,
                                      &year, &month, &day,
                                      &hour, &minute, &second);
/* If status equals FX_SUCCESS, the directory entry information is available in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="47325-528">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-528">See Also</span></span>

- <span data-ttu-id="47325-529">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-529">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-530">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-530">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-531">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-531">fx_directory_create</span></span>
- <span data-ttu-id="47325-532">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-532">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-533">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-533">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-534">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-534">fx_directory_delete</span></span>
- <span data-ttu-id="47325-535">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-535">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-536">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-536">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-537">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-537">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-538">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-538">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-539">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-539">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-540">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-540">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-541">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-541">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-542">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-542">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-543">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-543">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-544">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-544">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-545">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-545">fx_directory_rename</span></span>
- <span data-ttu-id="47325-546">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-546">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-547">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-547">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-548">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-548">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_clear"></a><span data-ttu-id="47325-549">fx_directory_local_path_clear:</span><span class="sxs-lookup"><span data-stu-id="47325-549">fx_directory_local_path_clear:</span></span>

<span data-ttu-id="47325-550">기본 로컬 경로를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="47325-550">Clears default local path</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-551">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-551">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="47325-552">Description</span><span class="sxs-lookup"><span data-stu-id="47325-552">Description</span></span>

<span data-ttu-id="47325-553">이 서비스는 호출 스레드에 대해 설정된 이전 로컬 경로 설정을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="47325-553">This service clears the previous local path set up for the calling thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-554">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-554">Input Parameters</span></span>

- <span data-ttu-id="47325-555">**media_ptr**: 이전에 열린 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-555">**media_ptr**: Pointer to a previously opened media.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-556">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-556">Return Values</span></span>

- <span data-ttu-id="47325-557">**FX_SUCCESS**(0x00) 로컬 경로 지우기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-557">**FX_SUCCESS** (0x00) Successful local path clear.</span></span>
- <span data-ttu-id="47325-558">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 현재 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-558">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="47325-559">**FX_NOT_IMPLEMENTED**(0x22) FX_NO_LCOAL_PATH가 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined</span></span>
- <span data-ttu-id="47325-560">**FX_PTR_ERROR**(0x18) 잘못된 미디어 포인터</span><span class="sxs-lookup"><span data-stu-id="47325-560">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-561">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-561">Allowed From</span></span>

<span data-ttu-id="47325-562">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-562">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-563">예제</span><span class="sxs-lookup"><span data-stu-id="47325-563">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a><span data-ttu-id="47325-564">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-564">See Also</span></span>

- <span data-ttu-id="47325-565">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-565">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-566">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-566">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-567">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-567">fx_directory_create</span></span>
- <span data-ttu-id="47325-568">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-568">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-569">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-569">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-570">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-570">fx_directory_delete</span></span>
- <span data-ttu-id="47325-571">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-571">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-572">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-572">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-573">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-573">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-574">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-574">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-575">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-575">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-576">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-576">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-577">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-577">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-578">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-578">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-579">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-579">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-580">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-580">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-581">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-581">fx_directory_rename</span></span>
- <span data-ttu-id="47325-582">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-582">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-583">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-583">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-584">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-584">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_get"></a><span data-ttu-id="47325-585">fx_directory_local_path_get:</span><span class="sxs-lookup"><span data-stu-id="47325-585">fx_directory_local_path_get:</span></span>

<span data-ttu-id="47325-586">현재 로컬 경로 문자열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-586">Gets the current local path string</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-587">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-587">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="47325-588">Description</span><span class="sxs-lookup"><span data-stu-id="47325-588">Description</span></span>

<span data-ttu-id="47325-589">이 서비스는 지정된 미디어의 로컬 경로 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-589">This service returns the local path pointer of the specified media.</span></span> <span data-ttu-id="47325-590">로컬 경로가 설정되어 있지 않으면 NULL이 호출자에게 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-590">If there is no local path set, a NULL is returned to the caller.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-591">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-591">Input Parameters</span></span>

- <span data-ttu-id="47325-592">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-592">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-593">**return_path_name**: 저장할 로컬 경로 문자열의 대상 문자열 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-593">**return_path_name**: Pointer to the destination string pointer for the local path string to be stored.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-594">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-594">Return Values</span></span>

- <span data-ttu-id="47325-595">**FX_SUCCESS**(0x00) 로컬 경로 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-595">**FX_SUCCESS** (0x00) Successful local path get.</span></span>
- <span data-ttu-id="47325-596">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 현재 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-596">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="47325-597">**FX_NOT_IMPLEMENTED**(0x22) NX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="47325-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="47325-598">**FX_PTR_ERROR**(0x18) 잘못된 미디어 포인터</span><span class="sxs-lookup"><span data-stu-id="47325-598">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>


### <a name="allowed-from"></a><span data-ttu-id="47325-599">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-599">Allowed From</span></span>

<span data-ttu-id="47325-600">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-600">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-601">예제</span><span class="sxs-lookup"><span data-stu-id="47325-601">Example</span></span>

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a><span data-ttu-id="47325-602">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-602">See Also</span></span>

- <span data-ttu-id="47325-603">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-603">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-604">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-604">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-605">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-605">fx_directory_create</span></span>
- <span data-ttu-id="47325-606">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-606">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-607">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-607">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-608">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-608">fx_directory_delete</span></span>
- <span data-ttu-id="47325-609">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-609">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-610">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-610">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-611">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-611">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-612">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-612">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-613">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-613">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-614">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-614">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-615">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-615">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-616">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-616">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-617">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-617">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-618">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-618">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-619">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-619">fx_directory_rename</span></span>
- <span data-ttu-id="47325-620">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-620">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-621">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-621">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-622">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-622">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_restore"></a><span data-ttu-id="47325-623">fx_directory_local_path_restore:</span><span class="sxs-lookup"><span data-stu-id="47325-623">fx_directory_local_path_restore:</span></span>

<span data-ttu-id="47325-624">이전 로컬 경로를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-624">Restores previous local path</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-625">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-625">Prototype</span></span>

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a><span data-ttu-id="47325-626">Description</span><span class="sxs-lookup"><span data-stu-id="47325-626">Description</span></span>

<span data-ttu-id="47325-627">서비스가 이전에 설정된 로컬 경로를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-627">This service restores a previously set local path.</span></span> <span data-ttu-id="47325-628">이 로컬 경로에 만든 디렉터리 검색 위치도 복원되어 애플리케이션에서 재귀 디렉터리를 순회하는 데 이 루틴을 유용하게 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-628">The directory search position made on this local path is also restored, which makes this routine useful in recursive directory traversals by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-629">각 로컬 경로에는 **FX_MAXIMUM_PATH** 크기의 로컬 경로 문자열이 포함됩니다. 크기는 기본적으로 256자입니다. 이 내부 경로 문자열은 FileX에서 사용되지 않으며 애플리케이션용으로만 제공됩니다. **FX_LOCAL_PATH** 를 지역 변수로 선언하려는 경우 사용자는 이 구조체의 크기만큼 증가하는 스택에 주의해야 합니다. 사용자는 **FX_MAXIMUM_PATH** 의 크기를 줄이고 FileX 라이브러리 소스를 다시 빌드하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-629">*Each local path contains a local path string of **FX_MAXIMUM_PATH** in size, which by default is 256 characters. This internal path string is not used by FileX and is provided only for the application's use. If **FX_LOCAL_PATH** is going to be declared as a local variable, users should beware of the stack growing by the size of this structure. Users are welcome to reduce the size of **FX_MAXIMUM_PATH** and rebuild the FileX library source.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-630">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-630">Input Parameters</span></span>

- <span data-ttu-id="47325-631">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-631">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-632">**local_path_ptr**: 이전에 설정한 로컬 경로에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-632">**local_path_ptr**: Pointer to the previously set local path.</span></span> <span data-ttu-id="47325-633">이 포인터는 이전에 사용되었는데 아직 그대로 남아 있는 로컬 경로를 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-633">It's very important to ensure that this pointer does indeed point to a previously used and still intact local path.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-634">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-634">Return Values</span></span>

- <span data-ttu-id="47325-635">**FX_SUCCESS**(0x00) 로컬 경로 복원에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-635">**FX_SUCCESS** (0x00) Successful local path restore.</span></span>
- <span data-ttu-id="47325-636">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 현재 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open.</span></span>
- <span data-ttu-id="47325-637">**FX_NOT_IMPLEMENTED**(0x22) FX_NO_LCOAL_PATH가 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined.</span></span>
- <span data-ttu-id="47325-638">**FX_PTR_ERROR**(0x18) 잘못된 미디어 또는 로컬 경로 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-638">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-639">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-639">Allowed From</span></span>

<span data-ttu-id="47325-640">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-640">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-641">예제</span><span class="sxs-lookup"><span data-stu-id="47325-641">Example</span></span>

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a><span data-ttu-id="47325-642">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-642">See Also</span></span>

- <span data-ttu-id="47325-643">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-643">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-644">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-644">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-645">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-645">fx_directory_create</span></span>
- <span data-ttu-id="47325-646">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-646">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-647">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-647">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-648">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-648">fx_directory_delete</span></span>
- <span data-ttu-id="47325-649">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-649">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-650">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-650">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-651">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-651">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-652">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-652">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-653">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-653">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-654">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-654">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-655">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-655">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-656">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-656">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-657">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-657">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-658">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-658">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-659">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-659">fx_directory_rename</span></span>
- <span data-ttu-id="47325-660">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-660">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-661">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-661">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-662">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-662">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_set"></a><span data-ttu-id="47325-663">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-663">fx_directory_local_path_set</span></span>

<span data-ttu-id="47325-664">스레드별 로컬 경로를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-664">Sets up a thread-specific local path</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-665">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-665">Prototype</span></span>

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="47325-666">Description</span><span class="sxs-lookup"><span data-stu-id="47325-666">Description</span></span>

<span data-ttu-id="47325-667">이 서비스는 \***new_path_string** _로 지정한 스레드별 경로를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-667">This service sets up a thread-specific path as specified by the \***new_path_string** _.</span></span> <span data-ttu-id="47325-668">이 루틴이 성공적으로 완료되면 _ \*_local_path_ptr_\*\*에 저장된 로컬 경로 정보가 이 스레드에서 만든 모든 파일 및 디렉터리 작업에 대한 전역 미디어 경로보다 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-668">After successful completion of this routine, the local path information stored in _ *_local_path_ptr_*\* will take precedence over the global media path for all file and directory operations made by this thread.</span></span> <span data-ttu-id="47325-669">이는 시스템의 다른 스레드에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-669">This will have no impact on any other thread in the system</span></span> 
> [!IMPORTANT]
> <span data-ttu-id="47325-670">로컬 경로 문자열의 기본 크기는 256자입니다. **fx_api** 에서 **FX_MAXIMUM_PATH** 를 수정하고 전체 FileX 라이브러리를 다시 빌드하여 이 설정을 변경할 수 있습니다. 문자열 경로는 애플리케이션에 대해 유지되며 FileX에서 내부적으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-670">*The default size of the local path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-671">애플리케이션에서 제공하는 이름의 경우 FileX는 디렉터리, 하위 디렉터리 및 파일 이름을 구분하기 위해 백슬래시(\\)와 슬래시(/) 문자 둘 다를 지원합니다. 그러나 FileX는 애플리케이션으로 반환되는 경로에는 백슬래시 문자만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-671">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-672">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-672">Input Parameters</span></span>

- <span data-ttu-id="47325-673">**media_ptr**: 이전에 열린 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-673">**media_ptr**: Pointer to the previously opened media.</span></span>
- <span data-ttu-id="47325-674">**local_path_ptr**: 스레드별 로컬 경로 정보를 저장하는 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-674">**local_path_ptr**: Destination for holding the thread-specific local path information.</span></span> <span data-ttu-id="47325-675">이 구조체의 주소는 나중에 로컬 경로 복원 함수에 제공될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-675">The address of this structure may be supplied to the local path restore function in the future.</span></span>
- <span data-ttu-id="47325-676">**new_path_name**: 설치할 로컬 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-676">**new_path_name**: Specifies the local path to setup.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-677">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-677">Return Values</span></span>

- <span data-ttu-id="47325-678">**FX_SUCCESS**(0x00) 기본 디렉터리 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-678">**FX_SUCCESS** (0x00) Successful default directory set.</span></span>
- <span data-ttu-id="47325-679">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-679">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-680">**FX_NOT_IMPLEMENTED**(0x22) \*\*FX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="47325-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="47325-681">**FX_INVALID_PATH**(0x0D) 새 디렉터리를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-681">**FX_INVALID_PATH** (0x0D) New directory could not be found.</span></span>
- <span data-ttu-id="47325-682">**FX_NOT_IMPLEMENTED**(0x22)- \*\*FX_NO_LOCAL_PATH가 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH is defined.</span></span>
- <span data-ttu-id="47325-683">**FX_PTR_ERROR**(0x18) 잘못된 미디어 또는 로컬 경로 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-683">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-684">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-684">Allowed From</span></span>

<span data-ttu-id="47325-685">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-685">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-686">예제</span><span class="sxs-lookup"><span data-stu-id="47325-686">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
FX_LOCAL_PATH     my_previous_local_path;
/* Set the local path to \abc\def\ghi. */
status = fx_directory_local_path_set (&my_media,&local_path,"\\abc\\def\\ghi");

/* If status equals FX_SUCCESS, the default directory for this thread
is \abc\def\ghi. All subsequent file operations that do not explicitly
specify a path will default to this directory. Note that the character
"\" serves as an escape character in a string. To represent the
character "\", use the construct "\\".*/
```

### <a name="see-also"></a><span data-ttu-id="47325-687">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-687">See Also</span></span>

- <span data-ttu-id="47325-688">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-688">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-689">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-689">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-690">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-690">fx_directory_create</span></span>
- <span data-ttu-id="47325-691">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-691">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-692">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-692">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-693">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-693">fx_directory_delete</span></span>
- <span data-ttu-id="47325-694">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-694">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-695">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-695">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-696">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-696">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-697">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-697">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-698">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-698">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-699">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-699">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-700">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-700">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-701">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-701">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-702">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-702">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-703">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-703">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-704">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-704">fx_directory_rename</span></span>
- <span data-ttu-id="47325-705">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-705">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-706">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-706">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-707">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-707">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get"></a><span data-ttu-id="47325-708">fx_directory_long_name_get:</span><span class="sxs-lookup"><span data-stu-id="47325-708">fx_directory_long_name_get:</span></span>

<span data-ttu-id="47325-709">짧은 이름에서 긴 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-709">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-710">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-710">Prototype</span></span>

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a><span data-ttu-id="47325-711">Description</span><span class="sxs-lookup"><span data-stu-id="47325-711">Description</span></span>

<span data-ttu-id="47325-712">이 서비스는 제공된 짧은 (8.3 형식) 이름과 연결된 긴 이름을(있는 경우) 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-712">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="47325-713">짧은 이름은 파일 이름 또는 디렉터리 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-713">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-714">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-714">Input Parameters</span></span>

- <span data-ttu-id="47325-715">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-715">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-716">**short_name**: 원본 짧은 이름(8.3 형식)에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-716">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="47325-717">**long_name**: 긴 이름의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-717">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="47325-718">긴 이름이 없으면 짧은 이름이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-718">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="47325-719">긴 이름의 대상은 FX_MAX_LONG_NAME_LEN자를 저장할 수 있을 만큼 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-719">Note that the destination for the long name must be large enough to hold FX_MAX_LONG_NAME_LEN characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-720">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-720">Return Values</span></span>

- <span data-ttu-id="47325-721">**FX_SUCCESS**(0x00) 긴 이름 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-721">**FX_SUCCESS** (0x00) Successful long name get</span></span>
- <span data-ttu-id="47325-722">**FX_NOT_FOUND**(0x04) 짧은 이름을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-722">**FX_NOT_FOUND** (0x04) Short name was not found</span></span>
- <span data-ttu-id="47325-723">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류</span><span class="sxs-lookup"><span data-stu-id="47325-723">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="47325-724">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어</span><span class="sxs-lookup"><span data-stu-id="47325-724">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="47325-725">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-725">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="47325-726">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터</span><span class="sxs-lookup"><span data-stu-id="47325-726">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="47325-727">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-727">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="47325-728">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-728">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-729">**FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-729">**FX_PTR_ERROR** (0x18) Invalid media or name pointer</span></span>
- <span data-ttu-id="47325-730">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-730">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-731">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-731">Allowed From</span></span>

<span data-ttu-id="47325-732">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-733">예제</span><span class="sxs-lookup"><span data-stu-id="47325-733">Example</span></span>

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="47325-734">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-734">See Also</span></span>

- <span data-ttu-id="47325-735">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-735">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-736">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-736">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-737">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-737">fx_directory_create</span></span>
- <span data-ttu-id="47325-738">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-738">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-739">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-739">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-740">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-740">fx_directory_delete</span></span>
- <span data-ttu-id="47325-741">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-741">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-742">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-742">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-743">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-743">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-744">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-744">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-745">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-745">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-746">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-746">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-747">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-747">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-748">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-748">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-749">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-749">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-750">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-750">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-751">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-751">fx_directory_rename</span></span>
- <span data-ttu-id="47325-752">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-752">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-753">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-753">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-754">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-754">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get_extended"></a><span data-ttu-id="47325-755">fx_directory_long_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="47325-755">fx_directory_long_name_get_extended</span></span>

<span data-ttu-id="47325-756">짧은 이름에서 긴 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-756">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-757">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-757">Prototype</span></span>

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="47325-758">Description</span><span class="sxs-lookup"><span data-stu-id="47325-758">Description</span></span>

<span data-ttu-id="47325-759">이 서비스는 제공된 짧은 (8.3 형식) 이름과 연결된 긴 이름을(있는 경우) 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-759">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="47325-760">짧은 이름은 파일 이름 또는 디렉터리 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-760">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-761">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-761">Input Parameters</span></span>

- <span data-ttu-id="47325-762">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-762">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-763">**short_name**: 원본 짧은 이름(8.3 형식)에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-763">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="47325-764">**long_name**: 긴 이름의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-764">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="47325-765">긴 이름이 없으면 짧은 이름이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-765">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="47325-766">참고: 긴 이름의 대상은 **FX_MAX_LONG_NAME_LEN** 자를 저장할 수 있을 만큼 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-766">Note: Destination for the long name must be large enough to hold **FX_MAX_LONG_NAME_LEN** characters.</span></span>
- <span data-ttu-id="47325-767">**long_file_name_buffer_length**: 긴 이름 버퍼의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-767">**long_file_name_buffer_length**: Length of the long name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-768">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-768">Return Values</span></span>

- <span data-ttu-id="47325-769">**FX_SUCCESS**(0x00) 긴 이름 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-769">**FX_SUCCESS** (0x00) Successful long name get.</span></span>
- <span data-ttu-id="47325-770">**FX_NOT_FOUND**(0x04) 짧은 이름을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-770">**FX_NOT_FOUND** (0x04) Short name was not found.</span></span>
- <span data-ttu-id="47325-771">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-771">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-772">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-772">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="47325-773">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-773">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-774">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-774">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-775">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-775">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-776">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-776">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="47325-777">**FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-777">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="47325-778">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-778">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-779">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-779">Allowed From</span></span>

<span data-ttu-id="47325-780">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-780">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-781">예제</span><span class="sxs-lookup"><span data-stu-id="47325-781">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="47325-782">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-782">See Also</span></span>

- <span data-ttu-id="47325-783">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-783">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-784">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-784">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-785">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-785">fx_directory_create</span></span>
- <span data-ttu-id="47325-786">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-786">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-787">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-787">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-788">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-788">fx_directory_delete</span></span>
- <span data-ttu-id="47325-789">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-789">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-790">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-790">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-791">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-791">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-792">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-792">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-793">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-793">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-794">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-794">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-795">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-795">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-796">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-796">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-797">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-797">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-798">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-798">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-799">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-799">fx_directory_rename</span></span>
- <span data-ttu-id="47325-800">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-800">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-801">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-801">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-802">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-802">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_name_test"></a><span data-ttu-id="47325-803">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-803">fx_directory_name_test</span></span>

<span data-ttu-id="47325-804">디렉터리 테스트</span><span class="sxs-lookup"><span data-stu-id="47325-804">Tests for directory</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-805">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-805">Prototype</span></span>

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="47325-806">Description</span><span class="sxs-lookup"><span data-stu-id="47325-806">Description</span></span>

<span data-ttu-id="47325-807">이 서비스는 제공된 이름이 디렉터리인지 여부를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-807">This service tests whether or not the supplied name is a directory.</span></span> <span data-ttu-id="47325-808">디렉터리인 경우 FX_SUCCESS가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-808">If so, a FX_SUCCESS is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-809">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-809">Input Parameters</span></span>

- <span data-ttu-id="47325-810">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-810">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-811">**directory_name**: 디렉터리 항목 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-811">**directory_name**: Pointer to name of the directory entry.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-812">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-812">Return Values</span></span>

- <span data-ttu-id="47325-813">**FX_SUCCESS**(0x00) 제공된 이름이 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-813">**FX_SUCCESS** (0x00) Supplied name is a directory.</span></span>
- <span data-ttu-id="47325-814">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-814">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="47325-815">**FX_NOT_FOUND**(0x04) 디렉터리 항목을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-815">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="47325-816">**FX_NOT_DIRECTORY**(0x0E) 항목이 디렉터리가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-816">**FX_NOT_DIRECTORY** (0x0E)  Entry is not a directory</span></span>
- <span data-ttu-id="47325-817">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-817">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-818">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-818">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="47325-819">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-819">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-820">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-820">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-821">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-821">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-822">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-822">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="47325-823">**FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-823">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="47325-824">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-824">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-825">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-825">Allowed From</span></span>

<span data-ttu-id="47325-826">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-826">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-827">예제</span><span class="sxs-lookup"><span data-stu-id="47325-827">Example</span></span>

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a><span data-ttu-id="47325-828">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-828">See Also</span></span>

- <span data-ttu-id="47325-829">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-829">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-830">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-830">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-831">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-831">fx_directory_create</span></span>
- <span data-ttu-id="47325-832">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-832">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-833">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-833">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-834">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-834">fx_directory_delete</span></span>
- <span data-ttu-id="47325-835">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-835">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-836">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-836">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-837">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-837">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-838">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-838">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-839">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-839">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-840">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-840">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-841">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-841">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-842">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-842">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-843">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-843">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-844">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-844">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-845">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-845">fx_directory_rename</span></span>
- <span data-ttu-id="47325-846">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-846">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-847">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-847">fx_unicode_directory_create</span></span>

## <a name="fx_directory_next_entry_find"></a><span data-ttu-id="47325-848">fx_directory_next_entry_find:</span><span class="sxs-lookup"><span data-stu-id="47325-848">fx_directory_next_entry_find:</span></span>

<span data-ttu-id="47325-849">다음 디렉터리 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-849">Picks up next directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-850">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-850">Prototype</span></span>

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="47325-851">Description</span><span class="sxs-lookup"><span data-stu-id="47325-851">Description</span></span>

<span data-ttu-id="47325-852">이 서비스는 현재 기본 디렉터리의 다음 항목 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-852">This service returns the next entry name in the current default directory.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-853">로컬이 아닌 경로를 사용하는 경우 디렉터리를 순회하는 동안 (ThreadX 세마포 또는 스레드 우선 순위 수준에 따라) 다른 애플리케이션 스레드가 이 디렉터리를 변경할 수 없도록 방지해야 합니다. 그러지 않으면 잘못된 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-853">*If using a non-local path, it is also important to prevent (with a ThreadX semaphore or thread priority level) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-854">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-854">Input Parameters</span></span>

- <span data-ttu-id="47325-855">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-855">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-856">**return_entry_name**: 기본 디렉터리에 있는 다음 항목 이름의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-856">**return_entry_name**: Pointer to destination for the next entry name in the default directory.</span></span> <span data-ttu-id="47325-857">이 포인터가 가리키는 버퍼는 **_FX_MAX_LONG_NAME_LEN_** 으로 정의한 FileX 이름의 최대 크기를 저장할 수 있을 만큼 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-857">The buffer this pointer points to must be large enough to hold the maximum size of FileX name, defined by **_FX_MAX_LONG_NAME_LEN_**.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-858">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-858">Return Values</span></span>

- <span data-ttu-id="47325-859">**FX_SUCCESS**(0x00) 다음 항목 찾기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-859">**FX_SUCCESS** (0x00) Successful next entry find</span></span>
- <span data-ttu-id="47325-860">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-860">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-861">**FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-861">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="47325-862">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-862">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-863">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-863">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-864">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-864">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-865">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-865">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-866">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-866">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-867">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-867">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="47325-868">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-868">**FX_CALLER_ERROR** (0x20)     Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-869">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-869">Allowed From</span></span>

<span data-ttu-id="47325-870">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-871">예제</span><span class="sxs-lookup"><span data-stu-id="47325-871">Example</span></span>

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a><span data-ttu-id="47325-872">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-872">See Also</span></span>

- <span data-ttu-id="47325-873">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-873">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-874">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-874">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-875">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-875">fx_directory_create</span></span>
- <span data-ttu-id="47325-876">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-876">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-877">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-877">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-878">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-878">fx_directory_delete</span></span>
- <span data-ttu-id="47325-879">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-879">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-880">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-880">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-881">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-881">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-882">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-882">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-883">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-883">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-884">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-884">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-885">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-885">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-886">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-886">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-887">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-887">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-888">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-888">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-889">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-889">fx_directory_rename</span></span>
- <span data-ttu-id="47325-890">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-890">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-891">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-891">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-892">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-892">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="47325-893">fx_directory_next_full_entry_find:</span><span class="sxs-lookup"><span data-stu-id="47325-893">fx_directory_next_full_entry_find:</span></span>

<span data-ttu-id="47325-894">전체 정보와 함께 다음 디렉터리 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-894">Gets next directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-895">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-895">Prototype</span></span>

```c
UINT fx_directory_next_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes, 
    ULONG *size,
    UINT *year, 
    UINT *month, 
    UINT *day,
    UINT *hour, 
    UINT *minute, 
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="47325-896">Description</span><span class="sxs-lookup"><span data-stu-id="47325-896">Description</span></span>

<span data-ttu-id="47325-897">이 서비스는 기본 디렉터리에서 다음 항목 이름을 검색하고 지정된 대상에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-897">This service retrieves the next entry name in the default directory and copies it to the specified destination.</span></span> <span data-ttu-id="47325-898">또한 추가 입력 매개 변수로 지정된 항목에 대한 전체 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-898">It also returns full information about the entry as specified by the additional input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-899">\**지정된 대상은 ***FX_MAX_LONG_NAME_LEN***으로 정의한 FileX 이름의 최대 크기를 저장할 수 있을 만큼 커야 합니다.*</span><span class="sxs-lookup"><span data-stu-id="47325-899">\*The specified destination must be large enough to hold the maximum sized FileX name, as defined by \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*</span></span>

> [!WARNING]
> <span data-ttu-id="47325-900">로컬이 아닌 경로를 사용하는 경우 디렉터리를 순회하는 동안 (ThreadX 세마포, 뮤텍스 또는 우선 순위 수준 변경에 따라) 다른 애플리케이션 스레드가 이 디렉터리를 변경할 수 없도록 방지해야 합니다. 그러지 않으면 잘못된 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-900">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-901">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-901">Input Parameters</span></span>

- <span data-ttu-id="47325-902">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-902">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-903">**directory_name**: 디렉터리 항목 이름의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-903">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="47325-904">적어도 **FX_MAX_LONG_NAME_LEN** 만큼 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-904">Must be at least as big as **FX_MAX_LONG_NAME_LEN**.</span></span>
- <span data-ttu-id="47325-905">**특성**: null이 아닌 경우 배치할 항목 특성의 대상에 대한 포인터입니다. 특성은 다음과 같은 가능한 설정과 함께 비트맵 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-905">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="47325-906">**FX_READ_ONLY**(0x01)</span><span class="sxs-lookup"><span data-stu-id="47325-906">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="47325-907">**FX_HIDDEN**(0x02)</span><span class="sxs-lookup"><span data-stu-id="47325-907">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="47325-908">**FX_SYSTEM**(0x04)</span><span class="sxs-lookup"><span data-stu-id="47325-908">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="47325-909">**FX_VOLUME**(0x08)</span><span class="sxs-lookup"><span data-stu-id="47325-909">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="47325-910">**FX_DIRECTORY**(0x10)</span><span class="sxs-lookup"><span data-stu-id="47325-910">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="47325-911">**FX_ARCHIVE**(0x20)</span><span class="sxs-lookup"><span data-stu-id="47325-911">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="47325-912">**size**: null이 아닌 경우 항목 크기(바이트)의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-912">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="47325-913">**month**: null이 아닌 경우 항목 수정 월의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-913">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="47325-914">**year**: null이 아닌 경우 항목 수정 연도의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-914">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="47325-915">**day**: null이 아닌 경우 항목 수정일의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-915">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="47325-916">**hour**: null이 아닌 경우 항목 수정 시간의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-916">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="47325-917">**minute**: null이 아닌 경우 항목 수정 분의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-917">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="47325-918">**second**: null이 아닌 경우 항목 수정 초의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-918">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-919">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-919">Return Values</span></span>

- <span data-ttu-id="47325-920">**FX_SUCCESS**(0x00) 디렉터리 다음 항목 찾기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-920">**FX_SUCCESS** (0x00) Successful directory next entry find.</span></span>
- <span data-ttu-id="47325-921">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-921">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-922">**FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-922">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="47325-923">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-923">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-924">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-924">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-925">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-925">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-926">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-926">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-927">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-927">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="47325-928">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-928">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="47325-929">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었거나 모든 입력 매개 변수가 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-929">**FX_PTR_ERROR** (0x18) Invalid media pointer or all input parameters are NULL.</span></span>
- <span data-ttu-id="47325-930">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-930">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-931">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-931">Allowed From</span></span>

<span data-ttu-id="47325-932">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-932">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-933">예제</span><span class="sxs-lookup"><span data-stu-id="47325-933">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
CHAR        entry_name[FX_MAX_LONG_NAME_LEN];
UINT        attributes;
ULONG       size;
UINT        year;
UINT        month;
UINT        day;
UINT        hour;
UINT        minute;
UINT        second;

/* Get the next directory entry in the default directory with full information. */
status = fx_directory_next_full_entry_find(&my_media, entry_name, &attributes, &size,
                                           &year, &month, &day,
                                           &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="47325-934">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-934">See Also</span></span>

- <span data-ttu-id="47325-935">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-935">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-936">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-936">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-937">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-937">fx_directory_create</span></span>
- <span data-ttu-id="47325-938">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-938">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-939">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-939">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-940">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-940">fx_directory_delete</span></span>
- <span data-ttu-id="47325-941">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-941">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-942">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-942">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-943">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-943">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-944">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-944">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-945">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-945">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-946">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-946">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-947">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-947">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-948">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-948">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-949">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-949">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-950">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-950">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-951">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-951">fx_directory_rename</span></span>
- <span data-ttu-id="47325-952">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-952">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-953">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-953">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-954">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-954">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_rename"></a><span data-ttu-id="47325-955">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-955">fx_directory_rename</span></span>

<span data-ttu-id="47325-956">디렉터리 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="47325-956">Renames directory</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-957">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-957">Prototype</span></span>

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a><span data-ttu-id="47325-958">Description</span><span class="sxs-lookup"><span data-stu-id="47325-958">Description</span></span>

<span data-ttu-id="47325-959">이 서비스는 디렉터리 이름을 지정된 새 디렉터리 이름으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-959">This service changes the directory name to the specified new directory name.</span></span> <span data-ttu-id="47325-960">지정된 경로 또는 기본 경로를 기준으로 이름이 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="47325-960">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="47325-961">경로가 새 디렉터리 이름에 지정된 경우 이름이 바뀐 디렉터리가 지정된 경로로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-961">If a path is specified in the new directory name, the renamed directory is effectively moved to the specified path.</span></span> <span data-ttu-id="47325-962">지정된 경로가 없으면 이름이 바뀐 디렉터리가 현재 기본 경로에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-962">If no path is specified, the renamed directory is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-963">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-963">Input Parameters</span></span>

- <span data-ttu-id="47325-964">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-964">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-965">**old_directory_name**: 현재 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-965">**old_directory_name**: Pointer to current directory name.</span></span>
- <span data-ttu-id="47325-966">**new_directory_name**: 새 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-966">**new_directory_name**: Pointer to new directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-967">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-967">Return Values</span></span>

- <span data-ttu-id="47325-968">**FX_SUCCESS**(0x00) 디렉터리 이름 바꾸기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-968">**FX_SUCCESS** (0x00) Successful directory rename.</span></span>
- <span data-ttu-id="47325-969">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-969">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-970">**FX_NOT_FOUND**(0x04) 디렉터리 항목을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-970">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="47325-971">**FX_NOT_DIRECTORY**(0x0E) 항목이 디렉터리가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-971">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory.</span></span>
- <span data-ttu-id="47325-972">**FX_INVALID_NAME**(0x0C) 새 디렉터리 이름이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-972">**FX_INVALID_NAME** (0x0C) New directory name is invalid.</span></span>
- <span data-ttu-id="47325-973">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-973">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-974">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-974">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-975">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-975">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-976">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-976">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-977">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-977">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-978">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-978">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="47325-979">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-979">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="47325-980">**FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-980">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="47325-981">**FX_INVALID_PATH**(0x0D) 디렉터리 이름과 함께 제공된 경로가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-981">**FX_INVALID_PATH** (0x0D) Invalid path supplied with directory name.</span></span>
- <span data-ttu-id="47325-982">**FX_ALREADY_CREATED**(0x0B) 지정된 디렉터리가 이미 생성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-982">**FX_ALREADY_CREATED** (0x0B) Specified directory was already created.</span></span>
- <span data-ttu-id="47325-983">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-983">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="47325-984">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-984">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-985">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-985">Allowed From</span></span>

<span data-ttu-id="47325-986">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-986">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-987">예제</span><span class="sxs-lookup"><span data-stu-id="47325-987">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a><span data-ttu-id="47325-988">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-988">See Also</span></span>

- <span data-ttu-id="47325-989">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-989">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-990">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-990">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-991">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-991">fx_directory_create</span></span>
- <span data-ttu-id="47325-992">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-992">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-993">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-993">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-994">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-994">fx_directory_delete</span></span>
- <span data-ttu-id="47325-995">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-995">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-996">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-996">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-997">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-997">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-998">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-998">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-999">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-999">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-1000">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-1000">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-1001">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-1001">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-1002">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1002">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-1003">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-1003">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-1004">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-1004">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-1005">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-1005">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-1006">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1006">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-1007">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-1007">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-1008">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1008">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get"></a><span data-ttu-id="47325-1009">fx_directory_short_name_get:</span><span class="sxs-lookup"><span data-stu-id="47325-1009">fx_directory_short_name_get:</span></span>

<span data-ttu-id="47325-1010">긴 이름에서 짧은 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1010">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1011">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1011">Prototype</span></span>

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="47325-1012">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1012">Description</span></span>

<span data-ttu-id="47325-1013">이 서비스는 제공된 긴 이름과 연결된 짧은 (8.3 형식) 이름을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1013">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="47325-1014">긴 이름은 파일 이름 또는 디렉터리 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1014">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1015">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1015">Input Parameters</span></span>

- <span data-ttu-id="47325-1016">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1016">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-1017">**long_name**: 원본 긴 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1017">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="47325-1018">**short_name**: 대상 짧은 이름(8.3 형식)에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1018">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="47325-1019">짧은 이름의 대상은 14자를 포함할 수 있도록 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1019">Note that the destination for the short name must be large enough to hold 14 characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1020">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1020">Return Values</span></span>

- <span data-ttu-id="47325-1021">**FX_SUCCESS**(0x00) 짧은 이름 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1021">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="47325-1022">**FX_NOT_FOUND**(0x04) 긴 이름을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1022">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="47325-1023">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1023">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1024">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1024">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-1025">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1025">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1026">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1026">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1027">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1027">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-1028">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1028">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-1029">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1029">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="47325-1030">**FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1030">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="47325-1031">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1031">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1032">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1032">Allowed From</span></span>

<span data-ttu-id="47325-1033">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1033">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1034">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1034">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="47325-1035">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1035">See Also</span></span>

- <span data-ttu-id="47325-1036">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1036">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-1037">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1037">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-1038">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-1038">fx_directory_create</span></span>
- <span data-ttu-id="47325-1039">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-1039">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-1040">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-1040">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-1041">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1041">fx_directory_delete</span></span>
- <span data-ttu-id="47325-1042">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-1042">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-1043">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-1043">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-1044">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-1044">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-1045">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-1045">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-1046">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-1046">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-1047">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-1047">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-1048">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-1048">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-1049">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1049">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-1050">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-1050">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-1051">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-1051">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-1052">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-1052">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-1053">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1053">fx_directory_rename</span></span>
- <span data-ttu-id="47325-1054">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-1054">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-1055">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1055">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get_extended"></a><span data-ttu-id="47325-1056">fx_directory_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="47325-1056">fx_directory_short_name_get_extended</span></span>

<span data-ttu-id="47325-1057">긴 이름에서 짧은 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1057">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1058">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1058">Prototype</span></span>

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a><span data-ttu-id="47325-1059">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1059">Description</span></span>

<span data-ttu-id="47325-1060">이 서비스는 제공된 긴 이름과 연결된 짧은 (8.3 형식) 이름을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1060">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="47325-1061">긴 이름은 파일 이름 또는 디렉터리 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1061">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1062">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1062">Input Parameters</span></span>

- <span data-ttu-id="47325-1063">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1063">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-1064">**long_name**: 원본 긴 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1064">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="47325-1065">**short_name**: 대상 짧은 이름(8.3 형식)에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1065">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="47325-1066">참고: 짧은 이름의 대상은 14자를 포함할 수 있도록 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1066">Note: Destination for the short name must be large enough to hold 14 characters.</span></span>
- <span data-ttu-id="47325-1067">**short_file_name_length**: 짧은 이름 버퍼의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1067">**short_file_name_length**: Length of short name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1068">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1068">Return Values</span></span>

- <span data-ttu-id="47325-1069">**FX_SUCCESS**(0x00) 짧은 이름 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1069">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="47325-1070">**FX_NOT_FOUND**(0x04) 긴 이름을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1070">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="47325-1071">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1071">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1072">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1072">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-1073">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1074">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1075">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1075">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-1076">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1076">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-1077">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1077">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="47325-1078">**FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1078">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="47325-1079">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1079">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1080">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1080">Allowed From</span></span>

<span data-ttu-id="47325-1081">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1081">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1082">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1082">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="47325-1083">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1083">See Also</span></span>

- <span data-ttu-id="47325-1084">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1084">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-1085">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1085">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-1086">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-1086">fx_directory_create</span></span>
- <span data-ttu-id="47325-1087">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-1087">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-1088">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-1088">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-1089">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1089">fx_directory_delete</span></span>
- <span data-ttu-id="47325-1090">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-1090">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-1091">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-1091">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-1092">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-1092">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-1093">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-1093">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-1094">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-1094">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-1095">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-1095">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-1096">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-1096">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-1097">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1097">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-1098">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-1098">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-1099">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-1099">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-1100">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-1100">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-1101">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1101">fx_directory_rename</span></span>
- <span data-ttu-id="47325-1102">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-1102">fx_unicode_directory_create</span></span>
- <span data-ttu-id="47325-1103">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1103">fx_unicode_directory_rename</span></span>

## <a name="fx_fault_tolerant_enable"></a><span data-ttu-id="47325-1104">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-1104">fx_fault_tolerant_enable</span></span>

<span data-ttu-id="47325-1105">내결함성 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1105">Enables the fault tolerant service</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1106">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1106">Prototype</span></span>

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a><span data-ttu-id="47325-1107">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1107">Description</span></span>

<span data-ttu-id="47325-1108">이 서비스는 내결함성 모듈을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1108">This service enables the fault tolerant module.</span></span> <span data-ttu-id="47325-1109">시작 시 내결함성 모듈은 파일 시스템이 FileX 내결함성 보호 상태인지 여부를 감지합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1109">Upon starting, the fault tolerant module detects whether or not the file system is under FileX fault tolerant protection.</span></span> <span data-ttu-id="47325-1110">내결함성 보호 상태가 아니면 서비스가 파일 시스템 트랜잭션의 로그를 저장할 수 있는 섹터를 파일 시스템에서 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1110">If it is not, the service finds available sectors on the file system to store logs on file system transactions.</span></span> <span data-ttu-id="47325-1111">파일 시스템이 FileX 내결함성 보호 상태이면 무결성을 유지하기 위해 파일 시스템에 로그를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1111">If the file system is under FileX fault tolerant protection, it applies the logs to the file system to maintain its integrity.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1112">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1112">Input Parameters</span></span>

- <span data-ttu-id="47325-1113">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1113">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-1114">**memory_ptr**: 내결함성 모듈에서 스크래치 메모리로 사용하는 메모리 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1114">**memory_ptr**: Pointer to a block of memory used by the fault tolerant module as scratch memory.</span></span>
- <span data-ttu-id="47325-1115">**memory_size**: 스크래치 메모리의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1115">**memory_size**: The size of the scratch memory.</span></span> <span data-ttu-id="47325-1116">내결함성이 제대로 작동하려면 스크래치 메모리 크기가 3072바이트 이상이어야 하며 섹터 크기의 배수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1116">In order for fault tolerant to work properly, the scratch memory size shall be at least 3072 bytes,- and must be multiple of sector size.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1117">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1117">Return Values</span></span>

- <span data-ttu-id="47325-1118">**FX_SUCCESS**(0x00) 내결함성을 사용하도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1118">**FX_SUCCESS** (0x00) Successfully enabled fault tolerant.</span></span>
- <span data-ttu-id="47325-1119">**FX_NOT_ENOUGH_MEMORY**(0x91) 메모리 크기가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1119">**FX_NOT_ENOUGH_MEMORY** (0x91)    memory size too small.</span></span>
- <span data-ttu-id="47325-1120">**FX_BOOT_ERROR**(0x01) 부팅 섹터 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1120">**FX_BOOT_ERROR** (0x01) Boot sector error.</span></span>
- <span data-ttu-id="47325-1121">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1121">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1122">**FX_NO_MORE_ENTRIES**(0x0F) 사용 가능한 여유 클러스터가 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1122">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="47325-1123">**FX_NO_MORE_SPACE**(0x0A) 이 파일과 연결된 미디어에 사용 가능한 클러스터가 충분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1123">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="47325-1124">**FX_SECTOR_INVALID**(0x89) 섹터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1124">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="47325-1125">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1125">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1126">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1126">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="47325-1127">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1127">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1128">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1128">Allowed From</span></span>

<span data-ttu-id="47325-1129">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1129">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1130">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1130">Example</span></span>

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a><span data-ttu-id="47325-1131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1131">See Also</span></span>

- <span data-ttu-id="47325-1132">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-1132">fx_system_initialize</span></span>
- <span data-ttu-id="47325-1133">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-1133">fx_media_abort</span></span>
- <span data-ttu-id="47325-1134">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-1134">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-1135">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-1135">fx_media_check</span></span>
- <span data-ttu-id="47325-1136">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-1136">fx_media_close</span></span>
- <span data-ttu-id="47325-1137">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1137">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-1138">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-1138">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-1139">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-1139">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-1140">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-1140">fx_media_flush</span></span>
- <span data-ttu-id="47325-1141">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-1141">fx_media_format</span></span>
- <span data-ttu-id="47325-1142">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-1142">fx_media_open</span></span>
- <span data-ttu-id="47325-1143">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1143">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-1144">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-1144">fx_media_read</span></span>
- <span data-ttu-id="47325-1145">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-1145">fx_media_space_available</span></span>
- <span data-ttu-id="47325-1146">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-1146">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-1147">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-1147">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-1148">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-1148">fx_media_write</span></span>

## <a name="fx_file_allocate"></a><span data-ttu-id="47325-1149">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1149">fx_file_allocate</span></span>

<span data-ttu-id="47325-1150">파일에 필요한 공간을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1150">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1151">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1151">Prototype</span></span>

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="47325-1152">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1152">Description</span></span>

<span data-ttu-id="47325-1153">이 서비스는 하나 이상의 인접한 클러스터를 할당하여 지정된 파일의 끝에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1153">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="47325-1154">FileX는 요청된 크기를 클러스터당 바이트 수로 나누어 필요한 클러스터 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1154">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="47325-1155">나눈 결과는 다음 전체 클러스터로 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1155">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="47325-1156">4GB를 초과하는 공간을 할당하려면 애플리케이션이 *fx_file_extended_allocate* 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1156">To allocate space beyond 4GB, application shall use the service *fx_file_extended_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1157">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1157">Input Parameters</span></span>

- <span data-ttu-id="47325-1158">**file_ptr**: 이전에 연 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1158">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="47325-1159">**size**: 파일에 할당할 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1159">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1160">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1160">Return Values</span></span>

- <span data-ttu-id="47325-1161">**FX_SUCCESS**(0x00) 파일 할당에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1161">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="47325-1162">**FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1162">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="47325-1163">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1163">**FX_FAT_READ_ERROR** (0x03) Failed to read FAT entry.</span></span>
- <span data-ttu-id="47325-1164">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1164">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1165">**FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1165">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="47325-1166">**FX_NO_MORE_ENTRIES**(0x0F) 사용 가능한 여유 클러스터가 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1166">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="47325-1167">**FX_NO_MORE_SPACE**(0x0A) 이 파일과 연결된 미디어에 사용 가능한 클러스터가 충분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1167">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="47325-1168">**FX_SECTOR_INVALID**(0x89) 섹터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1168">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="47325-1169">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1169">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1170">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1170">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-1171">**FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1171">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="47325-1172">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1172">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1173">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1173">Allowed From</span></span>

<span data-ttu-id="47325-1174">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1175">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1175">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="47325-1176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1176">See Also</span></span>

- <span data-ttu-id="47325-1177">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1177">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1178">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1178">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1179">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1179">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1180">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1180">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="47325-1181">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1181">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1182">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1182">fx_file_delete</span></span>
- <span data-ttu-id="47325-1183">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1183">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1184">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1184">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1185">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1185">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1186">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1186">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1187">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1187">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1188">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1188">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1189">fx_file_open- fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1189">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="47325-1190">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1190">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1191">fx_file_rename- fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1191">fx_file_rename- fx_file_seek</span></span>
- <span data-ttu-id="47325-1192">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1192">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1193">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1193">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1194">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1194">fx_file_write</span></span>
- <span data-ttu-id="47325-1195">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1195">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1196">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1196">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1197">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1197">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1198">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1198">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1199">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1199">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_read"></a><span data-ttu-id="47325-1200">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1200">fx_file_attributes_read</span></span>

<span data-ttu-id="47325-1201">파일 특성을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1201">Reads file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1202">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1202">Prototype</span></span>

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a><span data-ttu-id="47325-1203">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1203">Description</span></span>

<span data-ttu-id="47325-1204">이 서비스는 지정된 미디어에서 파일의 특성을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1204">This service reads the file's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1205">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1205">Input Parameters</span></span>

- <span data-ttu-id="47325-1206">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1206">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-1207">**file_name**: 요청된 파일의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).</span><span class="sxs-lookup"><span data-stu-id="47325-1207">**file_name**: Pointer to the name of the requested file (directory path is optional).</span></span>
- <span data-ttu-id="47325-1208">**attributes_ptr**: 배치할 파일 특성의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1208">**attributes_ptr**: Pointer to the destination for the file's attributes to be placed.</span></span> <span data-ttu-id="47325-1209">파일 특성은 다음과 같은 가능한 설정과 함께 비트맵 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1209">The file attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="47325-1210">FX_READ_ONLY(0x01)</span><span class="sxs-lookup"><span data-stu-id="47325-1210">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="47325-1211">FX_HIDDEN(0x02)</span><span class="sxs-lookup"><span data-stu-id="47325-1211">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="47325-1212">FX_SYSTEM(0x04)</span><span class="sxs-lookup"><span data-stu-id="47325-1212">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="47325-1213">FX_VOLUME(0x08)</span><span class="sxs-lookup"><span data-stu-id="47325-1213">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="47325-1214">FX_DIRECTORY(0x10)</span><span class="sxs-lookup"><span data-stu-id="47325-1214">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="47325-1215">FX_ARCHIVE(0x20)</span><span class="sxs-lookup"><span data-stu-id="47325-1215">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1216">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1216">Return Values</span></span>

- <span data-ttu-id="47325-1217">**FX_SUCCESS**(0x00) 특성 읽기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1217">**FX_SUCCESS** (0x00) Successful attribute read.</span></span>
- <span data-ttu-id="47325-1218">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1218">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-1219">**FX_NOT_FOUND**(0x04) 지정된 파일이 미디어에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1219">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="47325-1220">**FX_NOT_A_FILE**(0x05) 지정된 파일이 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1220">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="47325-1221">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1221">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1222">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1222">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-1223">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1223">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-1224">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1224">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-1225">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1225">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1226">**FX_PTR_ERROR**(0x18) 미디어 또는 특성 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1226">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="47325-1227">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1227">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1228">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1228">Allowed From</span></span>

<span data-ttu-id="47325-1229">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1230">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1230">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a><span data-ttu-id="47325-1231">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1231">See Also</span></span>

- <span data-ttu-id="47325-1232">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1232">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1233">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1233">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1234">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1234">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1235">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1235">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="47325-1236">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1236">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1237">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1237">fx_file_delete</span></span>
- <span data-ttu-id="47325-1238">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1238">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1239">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1239">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1240">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1240">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1241">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1241">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1242">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1242">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1243">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1243">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1244">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1244">fx_file_open</span></span>
- <span data-ttu-id="47325-1245">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1245">fx_file_read</span></span>
- <span data-ttu-id="47325-1246">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1246">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1247">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1247">fx_file_rename</span></span>
- <span data-ttu-id="47325-1248">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1248">fx_file_seek</span></span>
- <span data-ttu-id="47325-1249">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1249">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1250">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1250">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1251">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1251">fx_file_write</span></span>
- <span data-ttu-id="47325-1252">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1252">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1253">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1253">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1254">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1254">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1255">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1255">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1256">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1256">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_set"></a><span data-ttu-id="47325-1257">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1257">fx_file_attributes_set</span></span>

<span data-ttu-id="47325-1258">파일 특성 설정</span><span class="sxs-lookup"><span data-stu-id="47325-1258">Sets file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1259">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1259">Prototype</span></span>

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a><span data-ttu-id="47325-1260">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1260">Description</span></span>

<span data-ttu-id="47325-1261">이 서비스는 파일의 특성을 호출자가 지정한 특성으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1261">This service sets the file's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-1262">이 애플리케이션은 서비스와 함께 파일 특성의 하위 집합만 수정할 수 있습니다. 추가 특성을 설정하려고 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1262">*The application is only allowed to modify a subset of the file's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1263">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1263">Input Parameters</span></span>

- <span data-ttu-id="47325-1264">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1264">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-1265">**file_name**: 요청된 파일의 이름에 대한 포인터입니다\*\*(디렉터리 경로는 선택 사항임).</span><span class="sxs-lookup"><span data-stu-id="47325-1265">**file_name**: Pointer to the name of the requested file\*\* (directory path is optional).</span></span>
- <span data-ttu-id="47325-1266">**attributes**: 파일의 새 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1266">**attributes**: The new attributes for the file.</span></span> <span data-ttu-id="47325-1267">유효한 파일 특성은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1267">The valid file attributes are defined as follows:</span></span>
  - <span data-ttu-id="47325-1268">FX_READ_ONLY(0x01)</span><span class="sxs-lookup"><span data-stu-id="47325-1268">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="47325-1269">FX_HIDDEN(0x02)</span><span class="sxs-lookup"><span data-stu-id="47325-1269">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="47325-1270">FX_SYSTEM(0x04)</span><span class="sxs-lookup"><span data-stu-id="47325-1270">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="47325-1271">FX_ARCHIVE(0x20)</span><span class="sxs-lookup"><span data-stu-id="47325-1271">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1272">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1272">Return Values</span></span>

- <span data-ttu-id="47325-1273">**FX_SUCCESS**(0x00) 특성 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1273">**FX_SUCCESS** (0x00) Successful attribute set.</span></span>
- <span data-ttu-id="47325-1274">**FX_ACCESS_ERROR**(0x06) 파일이 열려 있어 파일의 특성을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1274">**FX_ACCESS_ERROR** (0x06) File is open and cannot have its attributes set.</span></span>
- <span data-ttu-id="47325-1275">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1275">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-1276">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1276">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1277">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-1278">**FX_NO_MORE_ENTRIES**(0x0F) FAT 테이블 또는 exFAT 클러스터 맵에 더 이상 항목이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1278">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in the FAT table or exFAT cluster map.</span></span>
- <span data-ttu-id="47325-1279">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1279">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="47325-1280">**FX_NOT_FOUND**(0x04) 지정된 파일이 미디어에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1280">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="47325-1281">**FX_NOT_A_FILE**(0x05) 지정된 파일이 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1281">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="47325-1282">**FX_SECTOR_INVALID**(0x89) 섹터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1282">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="47325-1283">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1283">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1284">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1284">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-1285">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1285">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="47325-1286">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1286">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="47325-1287">**FX_INVALID_ATTR**(0x19) 잘못된 특성을 선택했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1287">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="47325-1288">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1288">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1289">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1289">Allowed From</span></span>

<span data-ttu-id="47325-1290">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1290">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1291">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1291">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a><span data-ttu-id="47325-1292">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1292">See Also</span></span>

- <span data-ttu-id="47325-1293">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1293">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1294">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1294">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1295">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1295">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1296">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-1296">fx_file_close</span></span>
- <span data-ttu-id="47325-1297">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1297">fx_file_create</span></span>
- <span data-ttu-id="47325-1298">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1298">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1299">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1299">fx_file_delete</span></span>
- <span data-ttu-id="47325-1300">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1300">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1301">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1301">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1302">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1302">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1303">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1303">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1304">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1304">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1305">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1305">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1306">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1306">fx_file_open</span></span>
- <span data-ttu-id="47325-1307">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1307">fx_file_read</span></span>
- <span data-ttu-id="47325-1308">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1308">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1309">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1309">fx_file_rename</span></span>
- <span data-ttu-id="47325-1310">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1310">fx_file_seek</span></span>
- <span data-ttu-id="47325-1311">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1311">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1312">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1312">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1313">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1313">fx_file_write</span></span>
- <span data-ttu-id="47325-1314">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1314">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1315">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1315">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1316">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1316">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1317">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1317">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1318">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1318">fx_unicode_short_name_get</span></span>

## <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="47325-1319">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1319">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="47325-1320">파일에 공간을 할당하기 위한 최상의 노력</span><span class="sxs-lookup"><span data-stu-id="47325-1320">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1321">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1321">Prototype</span></span>

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="47325-1322">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1322">Description</span></span>

<span data-ttu-id="47325-1323">이 서비스는 하나 이상의 인접한 클러스터를 할당하여 지정된 파일의 끝에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1323">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="47325-1324">FileX는 요청된 크기를 클러스터당 바이트 수로 나누어 필요한 클러스터 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1324">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="47325-1325">나눈 결과는 다음 전체 클러스터로 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1325">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="47325-1326">미디어에서 사용할 수 있는 연속 클러스터가 부족한 경우 이 서비스는 연속 클러스터의 사용 가능한 가장 큰 블록을 파일에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1326">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="47325-1327">실제로 파일에 할당된 공간이 호출자에게 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1327">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="47325-1328">4GB를 초과하는 공간을 할당하려면 애플리케이션이 *fx_file_extended_best_effort_allocate* 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1328">To allocate space beyond 4GB, application shall use the service *fx_file_extended_best_effort_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1329">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1329">Input Parameters</span></span>

- <span data-ttu-id="47325-1330">**file_ptr**: 이전에 연 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1330">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="47325-1331">**size**: 파일에 할당할 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1331">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1332">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1332">Return Values</span></span>

- <span data-ttu-id="47325-1333">**FX_SUCCESS**(0x00) 최선의 파일 할당에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1333">**FX_SUCCESS** (0x00) Successful best-effort file allocation.</span></span>
- <span data-ttu-id="47325-1334">**FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1334">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="47325-1335">**FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1335">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="47325-1336">**FX_NO_MORE_SPACE**(0x0A) 이 파일과 연결된 미디어에 사용 가능한 클러스터가 충분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1336">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="47325-1337">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1337">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1338">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1338">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1339">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1339">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-1340">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1340">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-1341">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1341">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1342">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1342">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-1343">**FX_PTR_ERROR**(0x18) 파일 포인터 또는 대상이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1343">**FX_PTR_ERROR** (0x18) Invalid file pointer or destination.</span></span>
- <span data-ttu-id="47325-1344">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1344">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1345">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1345">Allowed From</span></span>

<span data-ttu-id="47325-1346">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1346">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1347">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1347">Example</span></span>

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a><span data-ttu-id="47325-1348">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1348">See Also</span></span>

- <span data-ttu-id="47325-1349">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1349">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1350">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1350">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1351">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1351">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-1352">fx_file_close</span></span>
- <span data-ttu-id="47325-1353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1353">fx_file_create</span></span>
- <span data-ttu-id="47325-1354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1354">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1355">fx_file_delete</span></span>
- <span data-ttu-id="47325-1356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1359">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1362">fx_file_open</span></span>
- <span data-ttu-id="47325-1363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1363">fx_file_read</span></span>
- <span data-ttu-id="47325-1364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1364">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1365">fx_file_rename</span></span>
- <span data-ttu-id="47325-1366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1366">fx_file_seek</span></span>
- <span data-ttu-id="47325-1367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1367">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1368">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1369">fx_file_write</span></span>
- <span data-ttu-id="47325-1370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1371">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1371">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1372">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1372">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1373">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1373">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1374">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1374">fx_unicode_short_name_get</span></span>

## <a name="fx_file_close"></a><span data-ttu-id="47325-1375">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-1375">fx_file_close</span></span>

<span data-ttu-id="47325-1376">파일을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1376">Closes file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1377">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1377">Prototype</span></span>

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a><span data-ttu-id="47325-1378">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1378">Description</span></span>

<span data-ttu-id="47325-1379">이 서비스는 지정된 파일을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1379">This service closes the specified file.</span></span> <span data-ttu-id="47325-1380">쓰기 위해 파일이 열려 있는데 수정된 경우 이 서비스는 새 크기, 현재 시스템 시간, 날짜와 함께 디렉터리 항목을 업데이트하여 파일 수정 프로세스를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1380">If the file was open for writing and if it was modified, this service completes the file modification process by updating its directory entry with the new size and the current system time and date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1381">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1381">Input Parameters</span></span>

- <span data-ttu-id="47325-1382">**file_ptr**: 이전에 연 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1382">**file_ptr**: Pointer to a previously opened file.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1383">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1383">Return Values</span></span>

- <span data-ttu-id="47325-1384">**FX_SUCCESS**(0x00) 파일 닫기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1384">**FX_SUCCESS** (0x00) Successful file close.</span></span>
- <span data-ttu-id="47325-1385">**FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1385">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="47325-1386">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1386">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1387">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1387">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1388">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1388">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1389">**FX_PTR_ERROR**(0x18) 미디어 또는 특성 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1389">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="47325-1390">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1390">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1391">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1391">Allowed From</span></span>

<span data-ttu-id="47325-1392">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1392">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1393">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1393">Example</span></span>

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a><span data-ttu-id="47325-1394">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1394">See Also</span></span>

- <span data-ttu-id="47325-1395">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1395">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1396">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1396">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1397">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1397">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1398">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1398">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1399">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1399">fx_file_create</span></span>
- <span data-ttu-id="47325-1400">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1400">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1401">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1401">fx_file_delete</span></span>
- <span data-ttu-id="47325-1402">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1402">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1403">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1403">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1404">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1404">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1405">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1405">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1406">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1406">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1407">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1407">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1408">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1408">fx_file_open</span></span>
- <span data-ttu-id="47325-1409">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1409">fx_file_read</span></span>
- <span data-ttu-id="47325-1410">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1410">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1411">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1411">fx_file_rename</span></span>
- <span data-ttu-id="47325-1412">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1412">fx_file_seek</span></span>
- <span data-ttu-id="47325-1413">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1413">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1414">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1414">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1415">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1415">fx_file_write</span></span>
- <span data-ttu-id="47325-1416">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1416">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1417">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1417">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1418">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1418">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1419">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1419">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1420">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1420">fx_unicode_short_name_get</span></span>

## <a name="fx_file_create"></a><span data-ttu-id="47325-1421">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1421">fx_file_create</span></span>

<span data-ttu-id="47325-1422">파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1422">Creates file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1423">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1423">Prototype</span></span>

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="47325-1424">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1424">Description</span></span>

<span data-ttu-id="47325-1425">이 서비스는 기본 디렉터리 또는 파일 이름과 함께 제공된 디렉터리 경로에 지정된 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1425">This service creates the specified file in the default directory or in the directory path supplied with the file name.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-1426">이 서비스는 길이가 0인 파일을 만듭니다. 즉, 클러스터가 할당되지 않습니다. 할당은 후속 파일을 쓸 때 자동으로 발생하거나 (공간이 4GB를 초과하는 경우에는) fx_file_allocate 또는 fx_file_extended_allocate 서비스를 사용하여 미리 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1426">*This service creates a file of zero length, i.e., no clusters allocated. Allocation will automatically take place on subsequent file writes or can be done in advance with the fx_file_allocate service or fx_file_extended_allocate for space beyond 4GB) service.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1427">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1427">Input Parameters</span></span>

- <span data-ttu-id="47325-1428">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1428">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-1429">**file_name**: 만들 파일의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).</span><span class="sxs-lookup"><span data-stu-id="47325-1429">**file_name**: Pointer to the name of the file to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1430">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1430">Return Values</span></span>

- <span data-ttu-id="47325-1431">**FX_SUCCESS**(0x00) 파일 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1431">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="47325-1432">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1432">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-1433">**FX_ALREADY_CREATED**(0x0B) 지정된 파일이 이미 생성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1433">**FX_ALREADY_CREATED** (0x0B) Specified file was already created.</span></span>
- <span data-ttu-id="47325-1434">**FX_NO_MORE_SPACE**(0x0A) 루트 디렉터리에 항목이 더 이상 없거나 사용 가능한 클러스터가 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1434">**FX_NO_MORE_SPACE** (0x0A)    Either there are no more entries in the root directory or there are no more clusters available.</span></span>
- <span data-ttu-id="47325-1435">**FX_INVALID_PATH**(0x0D) 파일 이름과 함께 제공된 경로가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1435">**FX_INVALID_PATH** (0x0D) Invalid path supplied with file name.</span></span>
- <span data-ttu-id="47325-1436">**FX_INVALID_NAME**(0x0C) 파일 이름이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1436">**FX_INVALID_NAME** (0x0C) File name is invalid.</span></span>
- <span data-ttu-id="47325-1437">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1437">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1438">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1438">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1439">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1439">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-1440">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1440">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-1441">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1441">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation</span></span>
- <span data-ttu-id="47325-1442">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1442">**FX_MEDIA_INVALID** (0x02)Invalid media.</span></span>
- <span data-ttu-id="47325-1443">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1443">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1444">**FX_WRITE_PROTECT**(0x23) 기본 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1444">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="47325-1445">**FX_PTR_ERROR**(0x18) 미디어 또는 파일 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1445">**FX_PTR_ERROR** (0x18) Invalid media or file name pointer.</span></span>
- <span data-ttu-id="47325-1446">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1446">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1447">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1447">Allowed From</span></span>

<span data-ttu-id="47325-1448">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1448">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1449">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1449">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a><span data-ttu-id="47325-1450">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1450">See Also</span></span>
- <span data-ttu-id="47325-1451">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1451">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1452">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1452">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1453">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1453">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1454">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1454">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1455">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-1455">fx_file_close</span></span>
- <span data-ttu-id="47325-1456">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1456">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1457">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1457">fx_file_delete</span></span>
- <span data-ttu-id="47325-1458">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1458">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1459">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1459">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1460">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1460">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1461">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1461">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1462">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1462">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1463">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1463">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1464">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1464">fx_file_open</span></span>
- <span data-ttu-id="47325-1465">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1465">fx_file_read</span></span>
- <span data-ttu-id="47325-1466">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1466">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1467">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1467">fx_file_rename</span></span>
- <span data-ttu-id="47325-1468">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1468">fx_file_seek</span></span>
- <span data-ttu-id="47325-1469">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1469">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1470">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1470">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1471">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1471">fx_file_write</span></span>
- <span data-ttu-id="47325-1472">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1472">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1473">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1473">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1474">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1474">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1475">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1475">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1476">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1476">fx_unicode_short_name_get</span></span>

## <a name="fx_file_date_time_set"></a><span data-ttu-id="47325-1477">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1477">fx_file_date_time_set</span></span>

### <a name="sets-file-date-and-time"></a><span data-ttu-id="47325-1478">파일 날짜 및 시간 설정</span><span class="sxs-lookup"><span data-stu-id="47325-1478">Sets file date and time</span></span>

<span data-ttu-id="47325-1479">파일 날짜 및 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1479">Setting File Date and Time</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1480">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1480">Prototype</span></span>

```c
UINT fx_file_date_time_set(
    FX_MEDIA *media_ptr, 
    CHAR *file_name,
    UINT year, 
    UINT month, 
    UINT day,
    UINT hour, 
    UINT minute, 
    UINT second);
```
### <a name="description"></a><span data-ttu-id="47325-1481">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1481">Description</span></span>

<span data-ttu-id="47325-1482">이 서비스는 지정된 파일의 날짜와 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1482">This service sets the date and time of the specified file.</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a><span data-ttu-id="47325-1483">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1483">Input Parameters</span></span>

- <span data-ttu-id="47325-1484">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1484">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-1485">**file_name**: 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1485">**file_name**: Pointer to name of the file.</span></span>
- <span data-ttu-id="47325-1486">**year**: 연도의 값입니다(1980~2107 포함).</span><span class="sxs-lookup"><span data-stu-id="47325-1486">**year**: Value of year (1980-2107 inclusive).</span></span>
- <span data-ttu-id="47325-1487">**month**: 월의 값입니다(1~12 포함).</span><span class="sxs-lookup"><span data-stu-id="47325-1487">**month**: Value of month (1-12 inclusive).</span></span>
- <span data-ttu-id="47325-1488">**day**: 날짜의 값입니다(1~31 포함).</span><span class="sxs-lookup"><span data-stu-id="47325-1488">**day**: Value of day (1-31 inclusive).</span></span>
- <span data-ttu-id="47325-1489">**hour**: 시간의 값입니다(0~23 포함).</span><span class="sxs-lookup"><span data-stu-id="47325-1489">**hour**: Value of hour (0-23 inclusive).</span></span>
- <span data-ttu-id="47325-1490">**minute**: 분의 값입니다(0~59 포함).</span><span class="sxs-lookup"><span data-stu-id="47325-1490">**minute**: Value of minute (0-59 inclusive).</span></span>
- <span data-ttu-id="47325-1491">**second**: 초의 값입니다(0~59 포함).</span><span class="sxs-lookup"><span data-stu-id="47325-1491">**second**: Value of second (0-59 inclusive).</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1492">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1492">Return Values</span></span>

- <span data-ttu-id="47325-1493">**FX_SUCCESS**(0x00) 날짜/시간 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1493">**FX_SUCCESS** (0x00) Successful date/time set.</span></span>
- <span data-ttu-id="47325-1494">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1494">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-1495">**FX_NOT_FOUND**(0x04) 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1495">**FX_NOT_FOUND** (0x04)    File was not found.</span></span>
- <span data-ttu-id="47325-1496">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1496">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="47325-1497">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1497">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1498">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1498">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-1499">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1499">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-1500">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1500">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="47325-1501">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1501">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1502">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1502">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-1503">**FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1503">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="47325-1504">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1504">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="47325-1505">**FX_INVALID_YEAR**(0x12) 연도가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1505">**FX_INVALID_YEAR** (0x12) Year is invalid.</span></span>
- <span data-ttu-id="47325-1506">**FX_INVALID_MONTH**(0x13) 월이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1506">**FX_INVALID_MONTH** (0x13) Month is invalid.</span></span>
- <span data-ttu-id="47325-1507">**FX_INVALID_DAY**(0x14) 날짜가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1507">**FX_INVALID_DAY** (0x14) Day is invalid.</span></span>
- <span data-ttu-id="47325-1508">**FX_INVALID_HOUR**(0x15) 시간이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1508">**FX_INVALID_HOUR** (0x15)    Hour is invalid.</span></span>
- <span data-ttu-id="47325-1509">**FX_INVALID_MINUTE**(0x16) 분이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1509">**FX_INVALID_MINUTE** (0x16) Minute is invalid.</span></span>
- <span data-ttu-id="47325-1510">**FX_INVALID_SECOND**(0x17) 초가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1510">**FX_INVALID_SECOND** (0x17) Second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1511">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1511">Allowed From</span></span>

<span data-ttu-id="47325-1512">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1512">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1513">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1513">Example</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a><span data-ttu-id="47325-1514">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1514">See Also</span></span>

- <span data-ttu-id="47325-1515">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1515">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1516">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1516">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1517">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1517">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1518">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1518">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1519">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-1519">fx_file_close</span></span>
- <span data-ttu-id="47325-1520">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1520">fx_file_create</span></span>
- <span data-ttu-id="47325-1521">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1521">fx_file_delete</span></span>
- <span data-ttu-id="47325-1522">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1522">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1523">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1523">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1524">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1524">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1525">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1525">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1526">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1526">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1527">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1527">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1528">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1528">fx_file_open</span></span>
- <span data-ttu-id="47325-1529">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1529">fx_file_read</span></span>
- <span data-ttu-id="47325-1530">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1530">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1531">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1531">fx_file_rename</span></span>
- <span data-ttu-id="47325-1532">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1532">fx_file_seek</span></span>
- <span data-ttu-id="47325-1533">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1533">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1534">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1534">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1535">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1535">fx_file_write</span></span>
- <span data-ttu-id="47325-1536">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1536">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1537">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1537">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1538">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1538">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1539">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1539">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1540">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1540">fx_unicode_short_name_get</span></span>

## <a name="fx_file_delete"></a><span data-ttu-id="47325-1541">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1541">fx_file_delete</span></span>

### <a name="deletes-file"></a><span data-ttu-id="47325-1542">파일 삭제</span><span class="sxs-lookup"><span data-stu-id="47325-1542">Deletes file</span></span>

<span data-ttu-id="47325-1543">파일 삭제</span><span class="sxs-lookup"><span data-stu-id="47325-1543">File Deletion</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1544">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1544">Prototype</span></span>

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="47325-1545">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1545">Description</span></span>

<span data-ttu-id="47325-1546">이 서비스는 지정된 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1546">This service deletes the specified file.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="47325-1547">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1547">Input Parameters</span></span>

- <span data-ttu-id="47325-1548">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1548">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-1549">**file_name**: 삭제할 파일의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).</span><span class="sxs-lookup"><span data-stu-id="47325-1549">**file_name**: Pointer to the name of the file to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1550">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1550">Return Values</span></span>

- <span data-ttu-id="47325-1551">**FX_SUCCESS**(0x00) 파일 삭제에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1551">**FX_SUCCESS** (0x00) Successful file delete.</span></span>
- <span data-ttu-id="47325-1552">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1552">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-1553">**FX_NOT_FOUND**(0x04) 지정된 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1553">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="47325-1554">**FX_NOT_A_FILE**(0x05) 지정된 파일 이름이 디렉터리 또는 볼륨입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1554">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="47325-1555">**FX_ACCESS_ERROR**(0x06) 지정된 파일이 현재 열려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1555">**FX_ACCESS_ERROR** (0x06) Specified file is currently open.</span></span>
- <span data-ttu-id="47325-1556">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1556">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1557">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1557">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1558">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1558">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-1559">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1559">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-1560">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1560">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-1561">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1561">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1562">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1562">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-1563">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1563">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="47325-1564">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1564">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="47325-1565">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1565">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1566">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1566">Allowed From</span></span>

<span data-ttu-id="47325-1567">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1568">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1568">Example</span></span>

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="47325-1569">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1569">See Also</span></span>

- <span data-ttu-id="47325-1570">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1570">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1571">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1571">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1572">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1572">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1573">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1573">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1574">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-1574">fx_file_close</span></span>
- <span data-ttu-id="47325-1575">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1575">fx_file_create</span></span>
- <span data-ttu-id="47325-1576">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1576">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1577">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1577">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1578">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1578">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1579">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1579">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1580">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1580">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1581">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1581">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1582">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1582">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1583">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1583">fx_file_open</span></span>
- <span data-ttu-id="47325-1584">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1584">fx_file_read</span></span>
- <span data-ttu-id="47325-1585">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1585">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1586">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1586">fx_file_rename</span></span>
- <span data-ttu-id="47325-1587">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1587">fx_file_seek</span></span>
- <span data-ttu-id="47325-1588">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1588">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1589">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1589">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1590">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1590">fx_file_write</span></span>
- <span data-ttu-id="47325-1591">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1591">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1592">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1592">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1593">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1593">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1594">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1594">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1595">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1595">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_allocate"></a><span data-ttu-id="47325-1596">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1596">fx_file_extended_allocate</span></span>

<span data-ttu-id="47325-1597">파일에 필요한 공간을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1597">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1598">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1598">Prototype</span></span>

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="47325-1599">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1599">Description</span></span>

<span data-ttu-id="47325-1600">이 서비스는 하나 이상의 인접한 클러스터를 할당하여 지정된 파일의 끝에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1600">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="47325-1601">FileX는 요청된 크기를 클러스터당 바이트 수로 나누어 필요한 클러스터 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1601">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="47325-1602">나눈 결과는 다음 전체 클러스터로 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1602">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="47325-1603">이 서비스는 exFAT용으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1603">This service is designed for exFAT.</span></span> <span data-ttu-id="47325-1604">*size* 매개 변수는 64비트 정수 값을 사용합니다. 따라서 호출자가 4GB 범위를 벗어나 공간을 미리 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1604">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1605">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1605">Input Parameters</span></span>

- <span data-ttu-id="47325-1606">**file_ptr**: 이전에 연 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1606">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="47325-1607">**size**: 파일에 할당할 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1607">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1608">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1608">Return Values</span></span>

- <span data-ttu-id="47325-1609">**FX_SUCCESS**(0x00) 파일 할당에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1609">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="47325-1610">**FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1610">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="47325-1611">**FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1611">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="47325-1612">**FX_NO_MORE_SPACE**(0x0A) 이 파일과 연결된 미디어에 사용 가능한 클러스터가 충분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1612">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="47325-1613">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1613">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1614">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1614">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1615">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1615">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-1616">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1616">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-1617">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1617">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1618">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1618">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-1619">**FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1619">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="47325-1620">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1620">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1621">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1621">Allowed From</span></span>

<span data-ttu-id="47325-1622">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1622">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1623">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1623">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="47325-1624">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1624">See Also</span></span>

- <span data-ttu-id="47325-1625">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1625">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1626">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1626">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1627">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1627">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1628">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1628">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1629">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-1629">fx_file_close</span></span>
- <span data-ttu-id="47325-1630">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1630">fx_file_create</span></span>
- <span data-ttu-id="47325-1631">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1631">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1632">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1632">fx_file_delete</span></span>
- <span data-ttu-id="47325-1633">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1633">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1634">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1634">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1635">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1635">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1636">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1636">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1637">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1637">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1638">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1638">fx_file_open</span></span>
- <span data-ttu-id="47325-1639">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1639">fx_file_read</span></span>
- <span data-ttu-id="47325-1640">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1640">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1641">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1641">fx_file_rename</span></span>
- <span data-ttu-id="47325-1642">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1642">fx_file_seek</span></span>
- <span data-ttu-id="47325-1643">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1643">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1644">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1644">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1645">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1645">fx_file_write</span></span>
- <span data-ttu-id="47325-1646">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1646">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1647">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1647">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1648">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1648">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1649">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1649">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1650">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1650">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_best_effort_allocate"></a><span data-ttu-id="47325-1651">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1651">fx_file_extended_best_effort_allocate</span></span>

<span data-ttu-id="47325-1652">파일에 공간을 할당하기 위한 최상의 노력</span><span class="sxs-lookup"><span data-stu-id="47325-1652">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1653">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1653">Prototype</span></span>

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="47325-1654">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1654">Description</span></span>

<span data-ttu-id="47325-1655">이 서비스는 하나 이상의 인접한 클러스터를 할당하여 지정된 파일의 끝에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1655">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="47325-1656">FileX는 요청된 크기를 클러스터당 바이트 수로 나누어 필요한 클러스터 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1656">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="47325-1657">나눈 결과는 다음 전체 클러스터로 반올림됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1657">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="47325-1658">미디어에서 사용할 수 있는 연속 클러스터가 부족한 경우 이 서비스는 연속 클러스터의 사용 가능한 가장 큰 블록을 파일에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1658">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="47325-1659">실제로 파일에 할당된 공간이 호출자에게 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1659">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="47325-1660">이 서비스는 exFAT용으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1660">This service is designed for exFAT.</span></span> <span data-ttu-id="47325-1661">*size* 매개 변수는 64비트 정수 값을 사용합니다. 따라서 호출자가 4GB 범위를 벗어나 공간을 미리 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1661">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1662">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1662">Input Parameters</span></span>

- <span data-ttu-id="47325-1663">**file_ptr**: 이전에 연 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1663">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="47325-1664">**size**: 파일에 할당할 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1664">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1665">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1665">Return Values</span></span>

- <span data-ttu-id="47325-1666">**FX_SUCCESS**(0x00) 파일 할당에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1666">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="47325-1667">**FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1667">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="47325-1668">**FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1668">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="47325-1669">**FX_NO_MORE_SPACE**(0x0A) 이 파일과 연결된 미디어에 사용 가능한 클러스터가 충분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1669">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="47325-1670">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1670">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1671">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1671">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1672">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1672">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-1673">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1673">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-1674">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1674">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1675">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1675">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-1676">**FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1676">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="47325-1677">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1677">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1678">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1678">Allowed From</span></span>

<span data-ttu-id="47325-1679">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1679">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1680">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1680">Example</span></span>

```c

FX_FILE my_file;
UINT             status;
ULONG64         actual_allocation;

/* Attempt to allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_best_effort_allocate(&my_file,
    0x100000000, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */
```

### <a name="see-also"></a><span data-ttu-id="47325-1681">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1681">See Also</span></span>

- <span data-ttu-id="47325-1682">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1682">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1683">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1683">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1684">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1684">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1685">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1685">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1686">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-1686">fx_file_close</span></span>
- <span data-ttu-id="47325-1687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1687">fx_file_create</span></span>
- <span data-ttu-id="47325-1688">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1688">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1689">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1689">fx_file_delete</span></span>
- <span data-ttu-id="47325-1690">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1690">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1691">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1691">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1692">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1692">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1693">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1693">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1694">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1694">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1695">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1695">fx_file_open</span></span>
- <span data-ttu-id="47325-1696">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1696">fx_file_read</span></span>
- <span data-ttu-id="47325-1697">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1697">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1698">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1698">fx_file_rename</span></span>
- <span data-ttu-id="47325-1699">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1699">fx_file_seek</span></span>
- <span data-ttu-id="47325-1700">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1700">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1701">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1701">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1702">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1702">fx_file_write</span></span>
- <span data-ttu-id="47325-1703">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1703">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1704">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1704">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1705">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1705">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1706">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1706">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1707">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1707">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_relative_seek"></a><span data-ttu-id="47325-1708">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1708">fx_file_extended_relative_seek</span></span>

<span data-ttu-id="47325-1709">상대 바이트 오프셋에 대한 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1709">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1710">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1710">Prototype</span></span>

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="47325-1711">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1711">Description</span></span>

<span data-ttu-id="47325-1712">이 서비스는 내부 파일 읽기/쓰기 포인터를 지정된 상대 바이트 오프셋에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1712">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="47325-1713">모든 후속 파일 읽기 또는 쓰기 요청은 파일의 이 위치에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1713">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="47325-1714">이 서비스는 exFAT용으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1714">This service is designed for exFAT.</span></span> <span data-ttu-id="47325-1715">*byte_offset* 매개 변수는 64비트 정수 값을 사용하므로 호출자가 4GB 범위를 벗어나 읽기/쓰기 포인터의 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1715">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-1716">찾기 작업이 파일의 끝을 지나 찾으려고 하면 파일의 읽기/쓰기 포인터가 파일의 끝에 배치됩니다. 반대로 찾기 작업이 파일의 시작 부분을 지나서 배치하려고 하면 파일의 읽기/쓰기 포인터가 파일의 시작 부분에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1716">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1717">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1717">Input Parameters</span></span>

- <span data-ttu-id="47325-1718">**file_ptr**: 이전에 연 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1718">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="47325-1719">**byte_offset**: 파일에서 원하는 상대 바이트 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1719">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="47325-1720">**seek_from**: 상대 찾기를 수행할 방향과 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1720">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="47325-1721">유효한 찾기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1721">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="47325-1722">FX_SEEK_BEGIN(0x00)</span><span class="sxs-lookup"><span data-stu-id="47325-1722">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="47325-1723">FX_SEEK_END(0x01)</span><span class="sxs-lookup"><span data-stu-id="47325-1723">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="47325-1724">FX_SEEK_FORWARD(0x02)</span><span class="sxs-lookup"><span data-stu-id="47325-1724">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="47325-1725">FX_SEEK_BACK(0x03) FX_SEEK_BEGIN이 지정된 경우 찾기 작업은 파일의 시작 부분에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1725">FX_SEEK_BACK (0x03) If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="47325-1726">FX_SEEK_END가 지정된 경우 찾기 작업은 파일의 끝에서 뒤로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1726">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="47325-1727">FX_SEEK_FORWARD가 지정된 경우 찾기 작업은 현재 파일 위치에서 정방향으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1727">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="47325-1728">FX_SEEK_BACK이 지정된 경우 찾기 작업은 현재 파일 위치에서 역방향으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1728">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1729">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1729">Return Values</span></span>

- <span data-ttu-id="47325-1730">**FX_SUCCESS**(0x00) 파일 상대 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1730">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="47325-1731">**FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1731">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="47325-1732">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1732">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1733">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1733">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1734">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1734">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-1735">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1735">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1736">**FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1736">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="47325-1737">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1737">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1738">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1738">Allowed From</span></span>

<span data-ttu-id="47325-1739">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1740">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1740">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="47325-1741">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1741">See Also</span></span>

- <span data-ttu-id="47325-1742">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1742">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1743">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1743">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1744">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1744">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1745">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1745">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1746">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-1746">fx_file_close</span></span>
- <span data-ttu-id="47325-1747">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1747">fx_file_create</span></span>
- <span data-ttu-id="47325-1748">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1748">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1749">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1749">fx_file_delete</span></span>
- <span data-ttu-id="47325-1750">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1750">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1751">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1751">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1752">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1752">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1753">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1753">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1754">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1754">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1755">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1755">fx_file_open</span></span>
- <span data-ttu-id="47325-1756">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1756">fx_file_read</span></span>
- <span data-ttu-id="47325-1757">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1757">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1758">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1758">fx_file_rename</span></span>
- <span data-ttu-id="47325-1759">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1759">fx_file_seek</span></span>
- <span data-ttu-id="47325-1760">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1760">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1761">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1761">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1762">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1762">fx_file_write</span></span>
- <span data-ttu-id="47325-1763">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1763">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1764">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1764">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1765">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1765">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1766">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1766">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1767">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1767">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_seek"></a><span data-ttu-id="47325-1768">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1768">fx_file_extended_seek</span></span>

<span data-ttu-id="47325-1769">바이트 오프셋에 대한 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1769">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1770">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1770">Prototype</span></span>

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a><span data-ttu-id="47325-1771">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1771">Description</span></span>

<span data-ttu-id="47325-1772">이 서비스는 내부 파일 읽기/쓰기 포인터를 지정된 바이트 오프셋에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1772">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="47325-1773">모든 후속 파일 읽기 또는 쓰기 요청은 파일의 이 위치에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1773">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="47325-1774">이 서비스는 exFAT용으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1774">This service is designed for exFAT.</span></span> <span data-ttu-id="47325-1775">*byte_offset* 매개 변수는 64비트 정수 값을 사용하므로 호출자가 4GB 범위를 벗어나 읽기/쓰기 포인터의 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1775">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1776">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1776">Input Parameters</span></span>

- <span data-ttu-id="47325-1777">**file_ptr**: 파일 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1777">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="47325-1778">**byte_offset**: 파일에서 원하는 바이트 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1778">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="47325-1779">값이 0이면 파일의 시작 부분에 읽기/쓰기 포인터가 배치되고 값이 파일의 크기보다 크면 파일의 끝에 읽기/쓰기 포인터를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1779">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1780">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1780">Return Values</span></span>

- <span data-ttu-id="47325-1781">**FX_SUCCESS**(0x00) 파일 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1781">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="47325-1782">**FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1782">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="47325-1783">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1783">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1784">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1784">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1785">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1785">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-1786">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1786">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1787">**FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1787">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="47325-1788">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1788">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1789">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1789">Allowed From</span></span>

<span data-ttu-id="47325-1790">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1790">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1791">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1791">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="47325-1792">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1792">See Also</span></span>

- <span data-ttu-id="47325-1793">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1793">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1794">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1794">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1795">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1795">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1796">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1796">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1797">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-1797">fx_file_close</span></span>
- <span data-ttu-id="47325-1798">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1798">fx_file_create</span></span>
- <span data-ttu-id="47325-1799">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1799">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1800">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1800">fx_file_delete</span></span>
- <span data-ttu-id="47325-1801">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1801">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1802">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1802">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1803">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1803">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1804">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1804">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1805">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1805">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1806">fx_file_open- fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1806">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="47325-1807">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1807">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1808">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1808">fx_file_rename</span></span>
- <span data-ttu-id="47325-1809">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1809">fx_file_seek</span></span>
- <span data-ttu-id="47325-1810">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1810">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1811">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1811">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1812">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1812">fx_file_write</span></span>
- <span data-ttu-id="47325-1813">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1813">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1814">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1814">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1815">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1815">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1816">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1816">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1817">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1817">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate"></a><span data-ttu-id="47325-1818">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1818">fx_file_extended_truncate</span></span>

<span data-ttu-id="47325-1819">파일을 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1819">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1820">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1820">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="47325-1821">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1821">Description</span></span>

<span data-ttu-id="47325-1822">이 서비스는 파일의 크기를 지정된 크기로 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1822">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="47325-1823">제공된 크기가 실제 파일 크기보다 크면 이 서비스는 아무것도 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1823">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="47325-1824">파일과 연결된 미디어 클러스터 중 해제된 클러스터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1824">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-1825">읽으려고 동시에 열 수 있는 파일을 잘라낼 때는 주의해야 합니다. 읽기 위해 열려 있는 파일을 자르면 잘못된 데이터를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1825">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="47325-1826">이 서비스는 exFAT용으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1826">This service is designed for exFAT.</span></span> <span data-ttu-id="47325-1827">*size* 매개 변수는 64비트 정수 값을 사용합니다. 따라서 호출자가 4GB 범위를 벗어나 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1827">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1828">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1828">Input Parameters</span></span>

- <span data-ttu-id="47325-1829">**file_ptr**: 파일 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1829">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="47325-1830">**size**: 새 파일 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1830">**size**: New file size.</span></span> <span data-ttu-id="47325-1831">이 새 파일 크기를 벗어난 바이트는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1831">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1832">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1832">Return Values</span></span>

- <span data-ttu-id="47325-1833">**FX_SUCCESS**(0x00) 파일 자르기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1833">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="47325-1834">**FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1834">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="47325-1835">**FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1835">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="47325-1836">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1836">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1837">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1837">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1838">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1838">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-1839">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1839">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-1840">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1840">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1841">**FX_WRITE_PROTECT**(0x23) 기본 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1841">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="47325-1842">**FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1842">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="47325-1843">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1843">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1844">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1844">Allowed From</span></span>

<span data-ttu-id="47325-1845">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1845">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1846">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1846">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="47325-1847">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1847">See Also</span></span>

- <span data-ttu-id="47325-1848">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1848">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1849">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1849">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1850">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1850">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1851">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1851">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1852">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-1852">fx_file_close</span></span>
- <span data-ttu-id="47325-1853">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1853">fx_file_create</span></span>
- <span data-ttu-id="47325-1854">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1854">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1855">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1855">fx_file_delete</span></span>
- <span data-ttu-id="47325-1856">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1856">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1857">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1857">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1858">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1858">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1859">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1859">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1860">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1860">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1861">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1861">fx_file_open</span></span>
- <span data-ttu-id="47325-1862">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1862">fx_file_read</span></span>
- <span data-ttu-id="47325-1863">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1863">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1864">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1864">fx_file_rename</span></span>
- <span data-ttu-id="47325-1865">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1865">fx_file_seek</span></span>
- <span data-ttu-id="47325-1866">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1866">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1867">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1867">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1868">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1868">fx_file_write</span></span>
- <span data-ttu-id="47325-1869">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1869">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1870">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1870">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1871">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1871">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1872">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1872">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1873">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1873">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate_release"></a><span data-ttu-id="47325-1874">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1874">fx_file_extended_truncate_release</span></span>

<span data-ttu-id="47325-1875">파일을 자르고 클러스터를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1875">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1876">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1876">Prototype</span></span>

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a><span data-ttu-id="47325-1877">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1877">Description</span></span>

<span data-ttu-id="47325-1878">이 서비스는 파일의 크기를 지정된 크기로 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1878">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="47325-1879">제공된 크기가 실제 파일 크기보다 크면 이 서비스는 아무것도 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1879">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="47325-1880">***Fx_file_extended_truncate*** 서비스와 달리 이 서비스는 사용되지 않는 클러스터를 모두 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1880">Unlike the ***fx_file_extended_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-1881">읽으려고 동시에 열 수 있는 파일을 잘라낼 때는 주의해야 합니다. 읽기 위해 열려 있는 파일을 자르면 잘못된 데이터를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1881">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="47325-1882">이 서비스는 exFAT용으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1882">This service is designed for exFAT.</span></span> <span data-ttu-id="47325-1883">*size* 매개 변수는 64비트 정수 값을 사용합니다. 따라서 호출자가 4GB 범위를 벗어나 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1883">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1884">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1884">Input Parameters</span></span>

- <span data-ttu-id="47325-1885">**file_ptr**: 이전에 연 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1885">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="47325-1886">**size**: 새 파일 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1886">**size**: New file size.</span></span> <span data-ttu-id="47325-1887">이 새 파일 크기를 벗어난 바이트는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1887">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1888">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1888">Return Values</span></span>

- <span data-ttu-id="47325-1889">**FX_SUCCESS**(0x00) 파일 자르기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1889">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="47325-1890">**FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1890">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="47325-1891">**FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1891">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="47325-1892">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1892">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1893">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1893">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-1894">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1894">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-1895">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1895">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-1896">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1896">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-1897">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1897">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1898">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1898">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-1899">**FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1899">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="47325-1900">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1900">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1901">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1901">Allowed From</span></span>

<span data-ttu-id="47325-1902">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1902">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1903">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1903">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a><span data-ttu-id="47325-1904">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1904">See Also</span></span>

- <span data-ttu-id="47325-1905">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1905">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1906">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1906">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1907">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1907">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1908">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1908">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1909">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-1909">fx_file_close</span></span>
- <span data-ttu-id="47325-1910">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1910">fx_file_create</span></span>
- <span data-ttu-id="47325-1911">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1911">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1912">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1912">fx_file_delete</span></span>
- <span data-ttu-id="47325-1913">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1913">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1914">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1914">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1915">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1915">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1916">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1916">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1917">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1917">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1918">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1918">fx_file_open</span></span>
- <span data-ttu-id="47325-1919">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1919">fx_file_read</span></span>
- <span data-ttu-id="47325-1920">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1920">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1921">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1921">fx_file_rename</span></span>
- <span data-ttu-id="47325-1922">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1922">fx_file_seek</span></span>
- <span data-ttu-id="47325-1923">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1923">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1924">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1924">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1925">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1925">fx_file_write</span></span>
- <span data-ttu-id="47325-1926">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1926">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1927">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1927">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1928">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1928">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1929">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1929">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1930">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1930">fx_unicode_short_name_get</span></span>

## <a name="fx_file_open"></a><span data-ttu-id="47325-1931">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-1931">fx_file_open</span></span>

<span data-ttu-id="47325-1932">파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1932">Opens file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1933">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1933">Prototype</span></span>

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a><span data-ttu-id="47325-1934">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1934">Description</span></span>

<span data-ttu-id="47325-1935">이 서비스는 읽거나 쓰기 위해 지정된 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1935">This service opens the specified file for either reading or writing.</span></span> <span data-ttu-id="47325-1936">파일은 읽기 위해 여러 번 열 수 있지만 쓰기 위해서는 쓰기 권한자가 파일을 닫을 때까지 한 번만 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1936">A file may be opened for reading multiple times, while a file can only be opened for writing once until the writer closes the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-1937">읽고 쓰기 위해 파일이 동시에 열려 있는 경우 주의해야 합니다. 읽기 위해 파일을 동시에 연 상태에서 수행한 파일 쓰기는 읽기 권한자가 파일을 닫고 읽기 위해 다시 열지 않는 한 읽기 권한자에게 표시되지 않을 수 있습니다. 마찬가지로 파일 쓰기 권한자는 파일 자르기 서비스를 사용하는 경우 주의해야 합니다. 쓰기 권한자가 파일을 자른 경우 동일한 파일의 읽기 권한자가 잘못된 데이터를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1937">*Care must be taken if a file is concurrently open for reading and writing. File writing performed when a file is simultaneously opened for reading may not be seen by the reader, unless the reader closes and reopens the file for reading. Similarly, the file writer should be careful when using file truncate services. If a file is truncated by the writer, readers of the same file could return invalid data.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-1938">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-1938">Input Parameters</span></span>

- <span data-ttu-id="47325-1939">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1939">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-1940">**file_ptr**: 파일 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1940">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="47325-1941">**file_name**: 연 파일의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).</span><span class="sxs-lookup"><span data-stu-id="47325-1941">**file_name**: Pointer to the name of the file to open (directory path is optional).</span></span>
- <span data-ttu-id="47325-1942">**open_type**: 열려 있는 파일의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1942">**open_type**: Type of file open.</span></span> <span data-ttu-id="47325-1943">유효한 개방형 형식 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1943">Valid open type options are:</span></span>
  - <span data-ttu-id="47325-1944">FX_OPEN_FOR_READ(0x00)</span><span class="sxs-lookup"><span data-stu-id="47325-1944">FX_OPEN_FOR_READ (0x00)</span></span>
  - <span data-ttu-id="47325-1945">FX_OPEN_FOR_WRITE(0x01)</span><span class="sxs-lookup"><span data-stu-id="47325-1945">FX_OPEN_FOR_WRITE (0x01)</span></span>
  - <span data-ttu-id="47325-1946">FX_OPEN_FOR_READ_FAST(0x02)</span><span class="sxs-lookup"><span data-stu-id="47325-1946">FX_OPEN_FOR_READ_FAST (0x02)</span></span>

<span data-ttu-id="47325-1947">FX_OPEN_FOR_READ 및 FX_OPEN_FOR_READ_FAST를 사용하여 파일 열기는 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1947">Opening files with FX_OPEN_FOR_READ and FX_OPEN_FOR_READ_FAST is similar:</span></span>

- <span data-ttu-id="47325-1948">FX_OPEN_FOR_READ에는 파일을 구성하는 클러스터의 연결된 목록이 그대로 유지되는지 확인하는 작업이 포함되는데, FX_OPEN_FOR_READ_FAST는 해당 확인 작업을 수행하지 않기 때문에 더 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1948">FX_OPEN_FOR_READ includes verification that the linked-list of clusters that comprise the file are intact, and FX_OPEN_FOR_READ_FAST does not perform this verification, which makes it faster.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-1949">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-1949">Return Values</span></span>

- <span data-ttu-id="47325-1950">**FX_SUCCESS**(0x00) 파일 열기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1950">**FX_SUCCESS** (0x00) Successful file open.</span></span>
- <span data-ttu-id="47325-1951">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1951">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-1952">**FX_NOT_FOUND**(0x04) 지정된 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1952">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="47325-1953">**FX_NOT_A_FILE**(0x05) 지정된 파일 이름이 디렉터리 또는 볼륨입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1953">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="47325-1954">**FX_FILE_CORRUPT**(0x08) 지정된 파일이 손상되어 열지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1954">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the open failed.</span></span>
- <span data-ttu-id="47325-1955">**FX_ACCESS_ERROR**(0x06) 지정된 파일이 이미 열려 있거나 개방형 형식이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1955">**FX_ACCESS_ERROR** (0x06) Specified file is already open or open type is invalid.</span></span>
- <span data-ttu-id="47325-1956">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1956">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-1957">**FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1957">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="47325-1958">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1958">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-1959">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1959">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-1960">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1960">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-1961">**FX_WRITE_PROTECT**(0x23) 기본 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1961">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="47325-1962">**FX_PTR_ERROR**(0x18) 미디어 또는 파일 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1962">**FX_PTR_ERROR** (0x18) Invalid media or file pointer.</span></span>
- <span data-ttu-id="47325-1963">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1963">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-1964">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-1964">Allowed From</span></span>

<span data-ttu-id="47325-1965">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-1965">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-1966">예제</span><span class="sxs-lookup"><span data-stu-id="47325-1966">Example</span></span>

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a><span data-ttu-id="47325-1967">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-1967">See Also</span></span>

- <span data-ttu-id="47325-1968">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1968">fx_file_allocate</span></span>
- <span data-ttu-id="47325-1969">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-1969">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-1970">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-1970">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-1971">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1971">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1972">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1972">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="47325-1973">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-1973">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-1974">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-1974">fx_file_delete</span></span>
- <span data-ttu-id="47325-1975">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1975">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-1976">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-1976">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-1977">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1977">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-1978">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1978">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-1979">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1979">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-1980">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1980">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-1981">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1981">fx_file_read</span></span>
- <span data-ttu-id="47325-1982">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1982">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-1983">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1983">fx_file_rename</span></span>
- <span data-ttu-id="47325-1984">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-1984">fx_file_seek</span></span>
- <span data-ttu-id="47325-1985">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-1985">fx_file_truncate</span></span>
- <span data-ttu-id="47325-1986">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-1986">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-1987">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-1987">fx_file_write</span></span>
- <span data-ttu-id="47325-1988">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-1988">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-1989">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-1989">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-1990">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-1990">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-1991">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1991">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-1992">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-1992">fx_unicode_short_name_get</span></span>

## <a name="fx_file_read"></a><span data-ttu-id="47325-1993">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-1993">fx_file_read</span></span>

<span data-ttu-id="47325-1994">파일의 바이트를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1994">Reads bytes from file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-1995">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-1995">Prototype</span></span>

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a><span data-ttu-id="47325-1996">Description</span><span class="sxs-lookup"><span data-stu-id="47325-1996">Description</span></span>

<span data-ttu-id="47325-1997">이 서비스는 파일에서 바이트를 읽은 다음 제공된 버퍼에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1997">This service reads bytes from the file and stores them in the supplied buffer.</span></span> <span data-ttu-id="47325-1998">읽기가 완료되면 파일의 내부 읽기 포인터가 파일의 다음 바이트를 가리키도록 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1998">After the read is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span> <span data-ttu-id="47325-1999">요청에 남아 있는 바이트 수가 적으면 남은 바이트만 버퍼에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-1999">If there are fewer bytes remaining in the request, only the bytes remaining are stored in the buffer.</span></span> <span data-ttu-id="47325-2000">어떤 경우든 버퍼에 배치된 총 바이트 수가 호출자에게 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2000">In any case, the total number of bytes placed in the buffer is returned to the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-2001">애플리케이션은 제공된 버퍼가 지정된 요청 바이트 수를 저장할 수 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2001">*The application must ensure that the buffer supplied is able to store the specified number of requested bytes.*</span></span>

> [!WARNING]
> <span data-ttu-id="47325-2002">대상 버퍼가 긴 단어 경계에 있고 요청된 크기가 sizeof(**ULONG**)로 균등하게 나눌 수 있는 경우 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2002">*Faster performance is achieved if the destination buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2003">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2003">Input Parameters</span></span>

- <span data-ttu-id="47325-2004">**file_ptr**: 파일 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2004">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="47325-2005">**buffer_ptr**: 읽기의 대상 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2005">**buffer_ptr**: Pointer to the destination buffer for the read.</span></span>
- <span data-ttu-id="47325-2006">**request_size**: 읽을 최대 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2006">**request_size**: Maximum number of bytes to read.</span></span>
- <span data-ttu-id="47325-2007">**actual_size**: 읽은 실제 바이트 수를 제공된 버퍼에 저장하는 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2007">**actual_size**: Pointer to the variable to hold the actual number of bytes read into the supplied buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2008">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2008">Return Values</span></span>

- <span data-ttu-id="47325-2009">**FX_SUCCESS**(0x00) 파일 읽기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2009">**FX_SUCCESS** (0x00) Successful file read.</span></span>
- <span data-ttu-id="47325-2010">**FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2010">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="47325-2011">**FX_FILE_CORRUPT**(0x08) 지정된 파일이 손상되어 읽지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2011">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the read failed.</span></span>
- <span data-ttu-id="47325-2012">**FX_END_OF_FILE**(0x09) 파일의 끝에 도달했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2012">**FX_END_OF_FILE** (0x09) End of file has been reached.</span></span>
- <span data-ttu-id="47325-2013">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2013">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-2014">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2014">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-2015">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2015">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2016">**FX_PTR_ERROR**(0x18) 파일 또는 버퍼 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2016">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="47325-2017">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2017">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2018">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2018">Allowed From</span></span>

<span data-ttu-id="47325-2019">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2019">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2020">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2020">Example</span></span>

```c
FX_FILE                 my_file;
unsigned char           my_buffer[1024];
ULONG                   actual_bytes;
UINT                    status;

/* Read up to 1024 bytes into "my_buffer." */
status = fx_file_read(&my_file, my_buffer, 1024, &actual_bytes);

/* If status equals FX_SUCCESS, "my_buffer" contains the bytes
    read from the file. The total number of bytes read is in "actual_bytes." */
```
### <a name="see-also"></a><span data-ttu-id="47325-2021">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2021">See Also</span></span>

- <span data-ttu-id="47325-2022">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="47325-2022">fx_file_allocate,</span></span>
- <span data-ttu-id="47325-2023">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="47325-2023">fx_file_attributes_read,</span></span>
- <span data-ttu-id="47325-2024">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="47325-2024">fx_file_attributes_set,</span></span>
- <span data-ttu-id="47325-2025">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="47325-2025">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="47325-2026">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="47325-2026">fx_file_close,</span></span>
- <span data-ttu-id="47325-2027">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="47325-2027">fx_file_create,</span></span>
- <span data-ttu-id="47325-2028">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="47325-2028">fx_file_date_time_set,</span></span>
- <span data-ttu-id="47325-2029">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="47325-2029">fx_file_delete,</span></span>
- <span data-ttu-id="47325-2030">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="47325-2030">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="47325-2031">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="47325-2031">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="47325-2032">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="47325-2032">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="47325-2033">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="47325-2033">fx_file_extended_seek,</span></span>
- <span data-ttu-id="47325-2034">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="47325-2034">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="47325-2035">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="47325-2035">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="47325-2036">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="47325-2036">fx_file_open,</span></span>
- <span data-ttu-id="47325-2037">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="47325-2037">fx_file_relative_seek,</span></span>
- <span data-ttu-id="47325-2038">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="47325-2038">fx_file_rename,</span></span>
- <span data-ttu-id="47325-2039">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="47325-2039">fx_file_seek,</span></span>
- <span data-ttu-id="47325-2040">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="47325-2040">fx_file_truncate,</span></span>
- <span data-ttu-id="47325-2041">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="47325-2041">fx_file_truncate_release,</span></span>
- <span data-ttu-id="47325-2042">fx_file_write,</span><span class="sxs-lookup"><span data-stu-id="47325-2042">fx_file_write,</span></span>
- <span data-ttu-id="47325-2043">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="47325-2043">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="47325-2044">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="47325-2044">fx_unicode_file_create,</span></span>
- <span data-ttu-id="47325-2045">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="47325-2045">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="47325-2046">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="47325-2046">fx_unicode_name_get,</span></span>
- <span data-ttu-id="47325-2047">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2047">fx_unicode_short_name_get</span></span>

## <a name="fx_file_relative_seek"></a><span data-ttu-id="47325-2048">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2048">fx_file_relative_seek</span></span>

<span data-ttu-id="47325-2049">상대 바이트 오프셋에 대한 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2049">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2050">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2050">Prototype</span></span>

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="47325-2051">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2051">Description</span></span>

<span data-ttu-id="47325-2052">이 서비스는 내부 파일 읽기/쓰기 포인터를 지정된 상대 바이트 오프셋에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2052">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="47325-2053">모든 후속 파일 읽기 또는 쓰기 요청은 파일의 이 위치에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2053">Any subsequent file read or write request will begin at this location in the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-2054">찾기 작업이 파일의 끝을 지나 찾으려고 하면 파일의 읽기/쓰기 포인터가 파일의 끝에 배치됩니다. 반대로 찾기 작업이 파일의 시작 부분을 지나서 배치하려고 하면 파일의 읽기/쓰기 포인터가 파일의 시작 부분에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2054">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

<span data-ttu-id="47325-2055">4GB를 초과하는 오프셋 값으로 찾으려면 애플리케이션이 *fx_file_extended_relative_seek* 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2055">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_relative_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2056">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2056">Input Parameters</span></span>

- <span data-ttu-id="47325-2057">**file_ptr**: 이전에 연 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2057">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="47325-2058">**byte_offset**: 파일에서 원하는 상대 바이트 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2058">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="47325-2059">**seek_from**: 상대 찾기를 수행할 방향과 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2059">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="47325-2060">유효한 찾기 옵션은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2060">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="47325-2061">FX_SEEK_BEGIN(0x00)</span><span class="sxs-lookup"><span data-stu-id="47325-2061">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="47325-2062">FX_SEEK_END(0x01)</span><span class="sxs-lookup"><span data-stu-id="47325-2062">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="47325-2063">FX_SEEK_FORWARD(0x02)</span><span class="sxs-lookup"><span data-stu-id="47325-2063">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="47325-2064">FX_SEEK_BACK(0x03)</span><span class="sxs-lookup"><span data-stu-id="47325-2064">FX_SEEK_BACK (0x03)</span></span>

<span data-ttu-id="47325-2065">FX_SEEK_BEGIN이 지정된 경우 찾기 작업은 파일의 시작 부분에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2065">If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="47325-2066">FX_SEEK_END가 지정된 경우 찾기 작업은 파일의 끝에서 뒤로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2066">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="47325-2067">FX_SEEK_FORWARD가 지정된 경우 찾기 작업은 현재 파일 위치에서 정방향으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2067">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="47325-2068">FX_SEEK_BACK이 지정된 경우 찾기 작업은 현재 파일 위치에서 역방향으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2068">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2069">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2069">Return Values</span></span>

- <span data-ttu-id="47325-2070">**FX_SUCCESS**(0x00) 파일 상대 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2070">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="47325-2071">**FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2071">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="47325-2072">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2072">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2073">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-2074">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-2075">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2075">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-2076">**FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2076">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="47325-2077">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2077">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2078">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2078">Allowed From</span></span>

<span data-ttu-id="47325-2079">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2079">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2080">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2080">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="47325-2081">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2081">See Also</span></span>

- <span data-ttu-id="47325-2082">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2082">fx_file_allocate</span></span>
- <span data-ttu-id="47325-2083">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-2083">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-2084">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-2084">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-2085">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2085">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-2086">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-2086">fx_file_close</span></span>
- <span data-ttu-id="47325-2087">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-2087">fx_file_create</span></span>
- <span data-ttu-id="47325-2088">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-2088">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-2089">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-2089">fx_file_delete</span></span>
- <span data-ttu-id="47325-2090">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2090">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-2091">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2091">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-2092">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2092">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-2093">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2093">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-2094">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-2094">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-2095">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-2095">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-2096">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-2096">fx_file_open</span></span>
- <span data-ttu-id="47325-2097">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-2097">fx_file_read</span></span>
- <span data-ttu-id="47325-2098">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-2098">fx_file_rename</span></span>
- <span data-ttu-id="47325-2099">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2099">fx_file_seek</span></span>
- <span data-ttu-id="47325-2100">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-2100">fx_file_truncate</span></span>
- <span data-ttu-id="47325-2101">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-2101">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-2102">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-2102">fx_file_write</span></span>
- <span data-ttu-id="47325-2103">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2103">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-2104">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-2104">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-2105">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-2105">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-2106">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2106">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-2107">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2107">fx_unicode_short_name_get</span></span>

## <a name="fx_file_rename"></a><span data-ttu-id="47325-2108">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-2108">fx_file_rename</span></span>

<span data-ttu-id="47325-2109">파일 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2109">Renames  file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2110">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2110">Prototype</span></span>

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a><span data-ttu-id="47325-2111">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2111">Description</span></span>

<span data-ttu-id="47325-2112">이 서비스는 *old_file_name* 으로 지정된 파일의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2112">This service changes the name of the file specified by *old_file_name*.</span></span> <span data-ttu-id="47325-2113">지정된 경로 또는 기본 경로를 기준으로 이름이 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2113">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="47325-2114">새 파일 이름에 경로가 지정된 경우 이름이 바뀐 파일이 실제로 지정된 경로로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2114">If a path is specified in the new file name, the renamed file is effectively moved to the specified path.</span></span> <span data-ttu-id="47325-2115">지정된 경로가 없으면 이름이 바뀐 파일이 현재 기본 경로에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2115">If no path is specified, the renamed file is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2116">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2116">Input Parameters</span></span>

- <span data-ttu-id="47325-2117">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2117">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="47325-2118">**old_file_name**: 이름을 바꿀 파일의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).</span><span class="sxs-lookup"><span data-stu-id="47325-2118">**old_file_name**: Pointer to the name of the file to rename (directory path is optional).</span></span>
- <span data-ttu-id="47325-2119">**new_file_name**: 새 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2119">**new_file_name**: Pointer to the new file name.</span></span> <span data-ttu-id="47325-2120">디렉터리 경로가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2120">The directory path is not allowed.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2121">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2121">Return Values</span></span>

- <span data-ttu-id="47325-2122">**FX_SUCCESS**(0x00) 파일 이름 바꾸기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2122">**FX_SUCCESS** (0x00) Successful file rename.</span></span>
- <span data-ttu-id="47325-2123">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2123">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-2124">**FX_NOT_FOUND**(0x04) 지정된 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2124">**FX_NOT_FOUND** (0x04)    Specified file was not found.</span></span>
- <span data-ttu-id="47325-2125">**FX_NOT_A_FILE**(0x05) 지정된 파일이 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2125">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="47325-2126">**FX_ACCESS_ERROR**(0x06) 지정된 파일이 이미 열려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2126">**FX_ACCESS_ERROR** (0x06) Specified file is already open.</span></span>
- <span data-ttu-id="47325-2127">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2127">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2128">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2128">**FX_WRITE_PROTECT** (0x23)    Specified media is write protected.</span></span>
- <span data-ttu-id="47325-2129">**FX_INVALID_NAME**(0x0C) 지정된 새 파일 이름이 유효한 파일 이름이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2129">**FX_INVALID_NAME** (0x0C) Specified new file name is not a valid file name.</span></span>
- <span data-ttu-id="47325-2130">**FX_INVALID_PATH**(0x0D) 경로가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2130">**FX_INVALID_PATH** (0x0D)    Path is invalid.</span></span>
- <span data-ttu-id="47325-2131">**FX_ALREADY_CREATED**(0x0B) 새 파일 이름이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2131">**FX_ALREADY_CREATED** (0x0B) The new file name is used.</span></span>
- <span data-ttu-id="47325-2132">**FX_MEDIA_INVALID**(0x02) 미디어가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2132">**FX_MEDIA_INVALID** (0x02)    Media is invalid.</span></span>
- <span data-ttu-id="47325-2133">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2133">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-2134">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2134">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-2135">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2135">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-2136">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2136">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-2137">**FX_FAT_READ_ERROR**(0x03) FAT 테이블을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2137">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="47325-2138">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2138">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="47325-2139">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2139">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2140">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2140">Allowed From</span></span>

<span data-ttu-id="47325-2141">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2142">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2142">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a><span data-ttu-id="47325-2143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2143">See Also</span></span>

- <span data-ttu-id="47325-2144">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2144">fx_file_allocate</span></span>
- <span data-ttu-id="47325-2145">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-2145">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-2146">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-2146">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-2147">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2147">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-2148">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-2148">fx_file_close</span></span>
- <span data-ttu-id="47325-2149">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-2149">fx_file_create</span></span>
- <span data-ttu-id="47325-2150">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-2150">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-2151">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-2151">fx_file_delete</span></span>
- <span data-ttu-id="47325-2152">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2152">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-2153">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2153">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-2154">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2154">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-2155">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2155">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-2156">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-2156">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-2157">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-2157">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-2158">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-2158">fx_file_open</span></span>
- <span data-ttu-id="47325-2159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-2159">fx_file_read</span></span>
- <span data-ttu-id="47325-2160">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2160">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-2161">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2161">fx_file_seek</span></span>
- <span data-ttu-id="47325-2162">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-2162">fx_file_truncate</span></span>
- <span data-ttu-id="47325-2163">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-2163">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-2164">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-2164">fx_file_write</span></span>
- <span data-ttu-id="47325-2165">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2165">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-2166">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-2166">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-2167">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-2167">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-2168">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2168">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-2169">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2169">fx_unicode_short_name_get</span></span>

## <a name="fx_file_seek"></a><span data-ttu-id="47325-2170">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2170">fx_file_seek</span></span>

<span data-ttu-id="47325-2171">바이트 오프셋에 대한 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2171">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2172">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2172">Prototype</span></span>

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a><span data-ttu-id="47325-2173">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2173">Description</span></span>

<span data-ttu-id="47325-2174">이 서비스는 내부 파일 읽기/쓰기 포인터를 지정된 바이트 오프셋에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2174">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="47325-2175">모든 후속 파일 읽기 또는 쓰기 요청은 파일의 이 위치에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2175">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="47325-2176">4GB를 초과하는 오프셋 값으로 찾으려면 애플리케이션이 *fx_file_extended_seek* 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2176">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2177">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2177">Input Parameters</span></span>

- <span data-ttu-id="47325-2178">**file_ptr**: 파일 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2178">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="47325-2179">**byte_offset**: 파일에서 원하는 바이트 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2179">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="47325-2180">값이 0이면 파일의 시작 부분에 읽기/쓰기 포인터가 배치되고 값이 파일의 크기보다 크면 파일의 끝에 읽기/쓰기 포인터를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2180">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2181">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2181">Return Values</span></span>

- <span data-ttu-id="47325-2182">**FX_SUCCESS**(0x00) 파일 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2182">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="47325-2183">**FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2183">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="47325-2184">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2184">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2185">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2185">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-2186">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2186">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-2187">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2187">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-2188">**FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2188">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="47325-2189">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2190">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2190">Allowed From</span></span>

<span data-ttu-id="47325-2191">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2192">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2192">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="47325-2193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2193">See Also</span></span>

- <span data-ttu-id="47325-2194">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2194">fx_file_allocate</span></span>
- <span data-ttu-id="47325-2195">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-2195">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-2196">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-2196">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-2197">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2197">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-2198">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-2198">fx_file_close</span></span>
- <span data-ttu-id="47325-2199">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-2199">fx_file_create</span></span>
- <span data-ttu-id="47325-2200">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-2200">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-2201">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-2201">fx_file_delete</span></span>
- <span data-ttu-id="47325-2202">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2202">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-2203">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2203">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-2204">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2204">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-2205">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2205">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-2206">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-2206">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-2207">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-2207">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-2208">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-2208">fx_file_open</span></span>
- <span data-ttu-id="47325-2209">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-2209">fx_file_read</span></span>
- <span data-ttu-id="47325-2210">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-2210">fx_file_rename</span></span>
- <span data-ttu-id="47325-2211">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2211">fx_file_seek</span></span>
- <span data-ttu-id="47325-2212">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-2212">fx_file_truncate</span></span>
- <span data-ttu-id="47325-2213">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-2213">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-2214">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-2214">fx_file_write</span></span>
- <span data-ttu-id="47325-2215">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2215">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-2216">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-2216">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-2217">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-2217">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-2218">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2218">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-2219">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2219">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate"></a><span data-ttu-id="47325-2220">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-2220">fx_file_truncate</span></span>

<span data-ttu-id="47325-2221">파일을 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2221">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2222">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2222">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="47325-2223">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2223">Description</span></span>

<span data-ttu-id="47325-2224">이 서비스는 파일의 크기를 지정된 크기로 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2224">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="47325-2225">제공된 크기가 실제 파일 크기보다 크면 이 서비스는 아무것도 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2225">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="47325-2226">파일과 연결된 미디어 클러스터 중 해제된 클러스터가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2226">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-2227">읽으려고 동시에 열 수 있는 파일을 잘라낼 때는 주의해야 합니다. 읽기 위해 열려 있는 파일을 자르면 잘못된 데이터를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2227">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="47325-2228">4GB를 초과하여 작동하기 위해 애플리케이션은 *fx_file_extended_truncate* 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2228">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2229">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2229">Input Parameters</span></span>

- <span data-ttu-id="47325-2230">**file_ptr**: 파일 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2230">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="47325-2231">**size**: 새 파일 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2231">**size**: New file size.</span></span> <span data-ttu-id="47325-2232">이 새 파일 크기를 벗어난 바이트는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2232">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2233">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2233">Return Values</span></span>

- <span data-ttu-id="47325-2234">**FX_SUCCESS**(0x00) 파일 자르기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2234">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="47325-2235">**FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2235">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="47325-2236">**FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2236">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="47325-2237">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2237">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2238">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2238">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-2239">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2239">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-2240">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2240">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-2241">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2241">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-2242">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2242">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="47325-2243">**FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2243">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="47325-2244">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2244">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2245">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2245">Allowed From</span></span>

<span data-ttu-id="47325-2246">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2247">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2247">Example</span></span>

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="47325-2248">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2248">See Also</span></span>

- <span data-ttu-id="47325-2249">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2249">fx_file_allocate</span></span>
- <span data-ttu-id="47325-2250">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-2250">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-2251">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-2251">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-2252">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2252">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-2253">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-2253">fx_file_close</span></span>
- <span data-ttu-id="47325-2254">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-2254">fx_file_create</span></span>
- <span data-ttu-id="47325-2255">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-2255">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-2256">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-2256">fx_file_delete</span></span>
- <span data-ttu-id="47325-2257">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2257">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-2258">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2258">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-2259">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2259">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-2260">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2260">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-2261">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-2261">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-2262">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-2262">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-2263">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-2263">fx_file_open</span></span>
- <span data-ttu-id="47325-2264">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-2264">fx_file_read</span></span>
- <span data-ttu-id="47325-2265">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2265">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-2266">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-2266">fx_file_rename</span></span>
- <span data-ttu-id="47325-2267">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2267">fx_file_seek</span></span>
- <span data-ttu-id="47325-2268">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-2268">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-2269">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-2269">fx_file_write</span></span>
- <span data-ttu-id="47325-2270">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2270">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-2271">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-2271">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-2272">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-2272">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-2273">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2273">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-2274">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2274">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate_release"></a><span data-ttu-id="47325-2275">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-2275">fx_file_truncate_release</span></span>

<span data-ttu-id="47325-2276">파일을 자르고 클러스터를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2276">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2277">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2277">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="47325-2278">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2278">Description</span></span>

<span data-ttu-id="47325-2279">이 서비스는 파일의 크기를 지정된 크기로 자릅니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2279">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="47325-2280">제공된 크기가 실제 파일 크기보다 크면 이 서비스는 아무것도 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2280">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="47325-2281">***Fx_file_truncate*** 서비스와 달리 이 서비스는 사용되지 않는 클러스터를 모두 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2281">Unlike the ***fx_file_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-2282">읽으려고 동시에 열 수 있는 파일을 잘라낼 때는 주의해야 합니다. 읽기 위해 열려 있는 파일을 자르면 잘못된 데이터를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2282">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="47325-2283">4GB를 초과하여 작동하기 위해 애플리케이션은 *fx_file_extended_truncate_release* 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2283">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate_release*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2284">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2284">Input Parameters</span></span>

- <span data-ttu-id="47325-2285">**file_ptr**: 이전에 연 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2285">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="47325-2286">**size**: 새 파일 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2286">**size**: New file size.</span></span> <span data-ttu-id="47325-2287">이 새 파일 크기를 벗어난 바이트는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2287">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2288">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2288">Return Values</span></span>

- <span data-ttu-id="47325-2289">**FX_SUCCESS**(0x00) 파일 자르기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2289">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="47325-2290">**FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2290">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="47325-2291">**FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2291">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="47325-2292">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류.</span><span class="sxs-lookup"><span data-stu-id="47325-2292">**FX_IO_ERROR** (0x90)    Driver I/O error.</span></span>
- <span data-ttu-id="47325-2293">**FX_WRITE_PROTECT**(0x23) 기본 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2293">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="47325-2294">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2294">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="47325-2295">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2295">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-2296">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2296">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-2297">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2297">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-2298">**FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2298">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation.</span></span>
- <span data-ttu-id="47325-2299">**FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2299">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="47325-2300">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2300">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2301">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2301">Allowed From</span></span>

<span data-ttu-id="47325-2302">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2303">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2303">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a><span data-ttu-id="47325-2304">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2304">See Also</span></span>

- <span data-ttu-id="47325-2305">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2305">fx_file_allocate</span></span>
- <span data-ttu-id="47325-2306">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-2306">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-2307">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-2307">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-2308">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2308">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-2309">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-2309">fx_file_close</span></span>
- <span data-ttu-id="47325-2310">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-2310">fx_file_create</span></span>
- <span data-ttu-id="47325-2311">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-2311">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-2312">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-2312">fx_file_delete</span></span>
- <span data-ttu-id="47325-2313">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2313">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-2314">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2314">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-2315">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2315">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-2316">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2316">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-2317">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-2317">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-2318">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-2318">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-2319">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-2319">fx_file_open</span></span>
- <span data-ttu-id="47325-2320">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-2320">fx_file_read</span></span>
- <span data-ttu-id="47325-2321">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2321">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-2322">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-2322">fx_file_rename</span></span>
- <span data-ttu-id="47325-2323">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2323">fx_file_seek</span></span>
- <span data-ttu-id="47325-2324">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-2324">fx_file_truncate</span></span>
- <span data-ttu-id="47325-2325">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-2325">fx_file_write</span></span>
- <span data-ttu-id="47325-2326">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2326">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-2327">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-2327">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-2328">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-2328">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-2329">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2329">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-2330">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2330">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write"></a><span data-ttu-id="47325-2331">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-2331">fx_file_write</span></span>

<span data-ttu-id="47325-2332">파일에 바이트를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2332">Writes bytes to file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2333">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2333">Prototype</span></span>

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="47325-2334">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2334">Description</span></span>

<span data-ttu-id="47325-2335">이 서비스는 파일의 현재 위치부터 시작하여 지정된 버퍼의 바이트를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2335">This service writes bytes from the specified buffer starting at the file's current position.</span></span> <span data-ttu-id="47325-2336">쓰기가 완료되면 파일의 내부 읽기 포인터가 파일의 다음 바이트를 가리키도록 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2336">After the write is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-2337">원본 버퍼가 긴 단어 경계에 있고 요청된 크기가 sizeof(**ULONG**)로 균등하게 나눌 수 있는 경우 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2337">*Faster performance is achieved if the source buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2338">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2338">Input Parameters</span></span>

- <span data-ttu-id="47325-2339">**file_ptr**: 파일 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2339">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="47325-2340">**buffer_ptr**: 쓰기의 원본 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2340">**buffer_ptr**: Pointer to the source buffer for the write.</span></span>
- <span data-ttu-id="47325-2341">**size**: 쓸 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2341">**size**: Number of bytes to write.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2342">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2342">Return Values</span></span>

- <span data-ttu-id="47325-2343">**FX_SUCCESS**(0x00) 파일 쓰기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2343">**FX_SUCCESS** (0x00) Successful file write.</span></span>
- <span data-ttu-id="47325-2344">**FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2344">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="47325-2345">**FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2345">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="47325-2346">**FX_NO_MORE_SPACE**(0x0A) 이번에 쓰는 데 사용할 수 있는 공간이 미디어에 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2346">**FX_NO_MORE_SPACE** (0x0A) There is no more room available in the media to perform this write.</span></span>
- <span data-ttu-id="47325-2347">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2347">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2348">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2348">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-2349">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2349">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-2350">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2350">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-2351">**FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2351">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="47325-2352">**FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2352">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="47325-2353">**FX_PTR_ERROR**(0x18) 파일 또는 버퍼 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2353">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="47325-2354">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2354">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2355">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2355">Allowed From</span></span>

<span data-ttu-id="47325-2356">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2356">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2357">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2357">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a><span data-ttu-id="47325-2358">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2358">See Also</span></span>

- <span data-ttu-id="47325-2359">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="47325-2359">fx_file_allocate,</span></span>
- <span data-ttu-id="47325-2360">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="47325-2360">fx_file_attributes_read,</span></span>
- <span data-ttu-id="47325-2361">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="47325-2361">fx_file_attributes_set,</span></span>
- <span data-ttu-id="47325-2362">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="47325-2362">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="47325-2363">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="47325-2363">fx_file_close,</span></span>
- <span data-ttu-id="47325-2364">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="47325-2364">fx_file_create,</span></span>
- <span data-ttu-id="47325-2365">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="47325-2365">fx_file_date_time_set,</span></span>
- <span data-ttu-id="47325-2366">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="47325-2366">fx_file_delete,</span></span>
- <span data-ttu-id="47325-2367">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="47325-2367">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="47325-2368">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="47325-2368">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="47325-2369">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="47325-2369">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="47325-2370">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="47325-2370">fx_file_extended_seek,</span></span>
- <span data-ttu-id="47325-2371">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="47325-2371">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="47325-2372">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="47325-2372">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="47325-2373">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="47325-2373">fx_file_open,</span></span>
- <span data-ttu-id="47325-2374">fx_file_read,</span><span class="sxs-lookup"><span data-stu-id="47325-2374">fx_file_read,</span></span>
- <span data-ttu-id="47325-2375">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="47325-2375">fx_file_relative_seek,</span></span>
- <span data-ttu-id="47325-2376">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="47325-2376">fx_file_rename,</span></span>
- <span data-ttu-id="47325-2377">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="47325-2377">fx_file_seek,</span></span>
- <span data-ttu-id="47325-2378">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="47325-2378">fx_file_truncate,</span></span>
- <span data-ttu-id="47325-2379">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="47325-2379">fx_file_truncate_release,</span></span>
- <span data-ttu-id="47325-2380">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="47325-2380">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="47325-2381">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="47325-2381">fx_unicode_file_create,</span></span>
- <span data-ttu-id="47325-2382">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="47325-2382">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="47325-2383">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="47325-2383">fx_unicode_name_get,</span></span>
- <span data-ttu-id="47325-2384">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2384">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write_notify_set"></a><span data-ttu-id="47325-2385">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2385">fx_file_write_notify_set</span></span>

<span data-ttu-id="47325-2386">파일 쓰기 알림 기능을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2386">Sets the file write notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2387">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2387">Prototype</span></span>

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a><span data-ttu-id="47325-2388">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2388">Description</span></span>

<span data-ttu-id="47325-2389">이 서비스는 파일 쓰기 작업에 성공한 후 호출되는 콜백 함수를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2389">This service installs callback function that is invoked after a successful file write operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2390">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2390">Input Parameters</span></span>

- <span data-ttu-id="47325-2391">**file_ptr**: 파일 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2391">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="47325-2392">**file_write_notify**: 설치할 파일 쓰기 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2392">**file_write_notify**: File write callback function to be installed.</span></span> <span data-ttu-id="47325-2393">콜백 함수를 NULL로 설정하면 콜백 함수가 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2393">Set the callback function to NULL disables the callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2394">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2394">Return Values</span></span>

- <span data-ttu-id="47325-2395">**FX_SUCCESS**(0x00) 콜백 함수 설치에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2395">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="47325-2396">**FX_PTR_ERROR**(0x18) file_ptr이 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2396">**FX_PTR_ERROR** (0x18) file_ptr is NULL.</span></span>
- <span data-ttu-id="47325-2397">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2397">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2398">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2398">Allowed From</span></span>

<span data-ttu-id="47325-2399">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2400">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2400">Example</span></span>

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a><span data-ttu-id="47325-2401">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2401">See Also</span></span>

- <span data-ttu-id="47325-2402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2402">fx_file_allocate</span></span>
- <span data-ttu-id="47325-2403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-2403">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-2404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-2404">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-2405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-2406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-2406">fx_file_close</span></span>
- <span data-ttu-id="47325-2407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-2407">fx_file_create</span></span>
- <span data-ttu-id="47325-2408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-2408">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-2409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-2409">fx_file_delete</span></span>
- <span data-ttu-id="47325-2410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-2411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-2411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-2412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-2413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2413">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-2414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-2414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-2415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-2415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-2416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-2416">fx_file_open</span></span>
- <span data-ttu-id="47325-2417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-2417">fx_file_read</span></span>
- <span data-ttu-id="47325-2418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2418">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-2419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-2419">fx_file_rename</span></span>
- <span data-ttu-id="47325-2420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-2420">fx_file_seek</span></span>
- <span data-ttu-id="47325-2421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-2421">fx_file_truncate</span></span>
- <span data-ttu-id="47325-2422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-2422">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-2423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-2423">fx_file_write</span></span>
- <span data-ttu-id="47325-2424">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-2424">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-2425">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-2425">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-2426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2426">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-2427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-2427">fx_unicode_short_name_get</span></span>

## <a name="fx_media_abort"></a><span data-ttu-id="47325-2428">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2428">fx_media_abort</span></span>

<span data-ttu-id="47325-2429">미디어 작업을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2429">Aborts media activities</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2430">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2430">Prototype</span></span>

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="47325-2431">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2431">Description</span></span>

<span data-ttu-id="47325-2432">이 서비스는 열려 있는 모든 파일 닫기, 연결된 드라이버로 중단 요청 보내기, 미디어를 중단된 상태로 전환 등 미디어와 관련된 모든 현재 작업을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2432">This service aborts all current activities associated with the media, including closing all open files, sending an abort request to the associated driver, and placing the media in an aborted state.</span></span> <span data-ttu-id="47325-2433">이 서비스는 I/O 오류가 검색될 때 일반적으로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2433">This service is typically called when I/O errors are detected.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-2434">중단 작업을 수행한 후 다시 사용하려면 미디어를 다시 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2434">*The media must be re-opened to use it again after an abort operation is performed.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2435">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2435">Input Parameters</span></span>

- <span data-ttu-id="47325-2436">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2436">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2437">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2437">Return Values</span></span>

- <span data-ttu-id="47325-2438">**FX_SUCCESS**(0x00) 미디어 중단에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2438">**FX_SUCCESS** (0x00) Successful media abort.</span></span>
- <span data-ttu-id="47325-2439">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2439">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-2440">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2440">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="47325-2441">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2441">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2442">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2442">Allowed From</span></span>

<span data-ttu-id="47325-2443">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2444">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2444">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a><span data-ttu-id="47325-2445">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2445">See Also</span></span>

- <span data-ttu-id="47325-2446">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2446">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2447">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2447">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2448">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2448">fx_media_check</span></span>
- <span data-ttu-id="47325-2449">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2449">fx_media_close</span></span>
- <span data-ttu-id="47325-2450">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2450">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2451">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2451">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2452">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2452">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2453">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2453">fx_media_flush</span></span>
- <span data-ttu-id="47325-2454">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2454">fx_media_format</span></span>
- <span data-ttu-id="47325-2455">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2455">fx_media_open</span></span>
- <span data-ttu-id="47325-2456">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2456">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2457">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2457">fx_media_read</span></span>
- <span data-ttu-id="47325-2458">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2458">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2459">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2459">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2460">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2460">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2461">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2461">fx_media_write</span></span>
- <span data-ttu-id="47325-2462">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2462">fx_system_initialize</span></span>

## <a name="fx_media_cache_invalidate"></a><span data-ttu-id="47325-2463">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2463">fx_media_cache_invalidate</span></span>

<span data-ttu-id="47325-2464">논리 섹터 캐시를 무효화합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2464">Invalidates logical sector cache</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2465">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2465">Prototype</span></span>

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="47325-2466">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2466">Description</span></span>

<span data-ttu-id="47325-2467">이 서비스는 캐시에 있는 모든 더티 섹터를 플러시하고 전체 논리 섹터 캐시를 무효화합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2467">This service flushes all dirty sectors in the cache and then invalidates the entire logical sector cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2468">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2468">Input Parameters</span></span>

- <span data-ttu-id="47325-2469">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2469">**media_ptr**: Pointer to media control block</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2470">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2470">Return Values</span></span>

- <span data-ttu-id="47325-2471">**FX_SUCCESS**(0x00) 미디어 캐시 무효화에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2471">**FX_SUCCESS** (0x00) Successful media cache invalidate.</span></span>
- <span data-ttu-id="47325-2472">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2472">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-2473">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2473">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2474">**FX_PTR_ERROR**(0x18) 미디어 또는 스크래치 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2474">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="47325-2475">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2475">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2476">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2476">Allowed From</span></span>

<span data-ttu-id="47325-2477">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2478">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2478">Example</span></span>

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a><span data-ttu-id="47325-2479">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2479">See Also</span></span>

- <span data-ttu-id="47325-2480">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2480">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2481">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2481">fx_media_abort</span></span>
- <span data-ttu-id="47325-2482">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2482">fx_media_check</span></span>
- <span data-ttu-id="47325-2483">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2483">fx_media_close</span></span>
- <span data-ttu-id="47325-2484">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2484">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2485">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2485">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2486">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2486">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2487">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2487">fx_media_flush</span></span>
- <span data-ttu-id="47325-2488">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2488">fx_media_format</span></span>
- <span data-ttu-id="47325-2489">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2489">fx_media_open</span></span>
- <span data-ttu-id="47325-2490">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2490">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2491">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2491">fx_media_read</span></span>
- <span data-ttu-id="47325-2492">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2492">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2493">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2493">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2494">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2494">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2495">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2495">fx_media_write</span></span>
- <span data-ttu-id="47325-2496">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2496">fx_system_initialize</span></span>

## <a name="fx_media_check"></a><span data-ttu-id="47325-2497">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2497">fx_media_check</span></span>

<span data-ttu-id="47325-2498">오류가 있는지 미디어를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2498">Checks media for errors</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2499">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2499">Prototype</span></span>

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a><span data-ttu-id="47325-2500">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2500">Description</span></span>

<span data-ttu-id="47325-2501">이 서비스는 지정된 미디어에서 파일/디렉터리 교차 링크, 잘못된 FAT 체인, 손실된 클러스터를 비롯한 기본 구조 오류가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2501">This service checks the specified media for basic structural errors, including file/directory cross-linking, invalid FAT chains, and lost clusters.</span></span> <span data-ttu-id="47325-2502">또한 검색된 오류를 수정하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2502">This service also provides the capability to correct detected errors.</span></span>

<span data-ttu-id="47325-2503">fx_media_check 서비스를 사용하려면 미디어의 디렉터리와 파일에 대한 깊이 우선 분석을 위한 스크래치 메모리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2503">The fx_media_check service requires scratch memory for its depth-first analysis of directories and files in the media.</span></span> <span data-ttu-id="47325-2504">특히, 미디어 검사 서비스에 제공되는 스크래치 메모리는 여러 디렉터리 항목, 하위 디렉터리에 입력하기 전에 현재 디렉터리 항목 위치를 “스택”하기 위한 데이터 구조, 마지막으로 논리적 FAT 비트맵을 포함하는 데이터 구조를 저장할 만큼 충분히 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2504">Specifically, the scratch memory supplied to the media check service must be large enough to hold several directory entries, a data structure to "stack" the current directory entry position before entering into subdirectories, and finally the logical FAT bit map.</span></span> <span data-ttu-id="47325-2505">스크래치 메모리는 최소 512~1024바이트에 논리적 FAT 비트맵을 위한 메모리를 더한 크기여야 합니다. 논리적 FAT 비트맵에는 미디어에 있는 클러스터만큼의 비트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2505">The scratch memory should be at least 512-1024 bytes plus memory for the logical FAT bit map, which requires as many bits as there are clusters in the media.</span></span> <span data-ttu-id="47325-2506">예를 들어 클러스터가 8000개 있는 디바이스는 1000바이트가 필요한 것으로 표시되므로 필요한 총 스크래치 영역은 약 2048바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2506">For example, a device with 8000 clusters would require 1000 bytes to represent and thus require a total scratch area on the order of 2048 bytes.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-2507">이 서비스는 fx_media_open 직후 다른 파일 시스템 작업 없이 바로 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2507">*This service should only be called immediately after fx_media_open and without any other file system activity.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2508">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2508">Input Parameters</span></span>

- <span data-ttu-id="47325-2509">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2509">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-2510">**scratch_memory_ptr**: 스크래치 메모리의 시작에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2510">**scratch_memory_ptr**: Pointer to the start of scratch memory.</span></span>
- <span data-ttu-id="47325-2511">**scratch_memory_size**: 스크래치 메모리 크기입니다(바이트).</span><span class="sxs-lookup"><span data-stu-id="47325-2511">**scratch_memory_size**: Size of scratch memory in bytes.</span></span>
- <span data-ttu-id="47325-2512">**error_correction_option**: 오류 수정 옵션 비트입니다. 비트가 설정된 경우 오류가 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2512">**error_correction_option**: Error correction option bits, when the bit is set, error correction is performed.</span></span> <span data-ttu-id="47325-2513">오류 수정 옵션 비트는 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2513">The error correction option bits are defined as follows:</span></span>
  - <span data-ttu-id="47325-2514">FX_FAT_CHAIN_ERROR(0x01)</span><span class="sxs-lookup"><span data-stu-id="47325-2514">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="47325-2515">FX_DIRECTORY_ERROR(0x02)</span><span class="sxs-lookup"><span data-stu-id="47325-2515">FX_DIRECTORY_ERROR (0x02)</span></span>
  - <span data-ttu-id="47325-2516">FX_LOST_CLUSTER_ERROR(0x04) 필요한 오류 수정 옵션을 간단하게 사용하거나 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2516">FX_LOST_CLUSTER_ERROR (0x04) Simply OR together the required error correction options.</span></span> <span data-ttu-id="47325-2517">오류 수정이 필요하지 않은 경우 0 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2517">If no error correction is required, a value of 0 should be supplied.</span></span>
- <span data-ttu-id="47325-2518">**errors_detected_ptr**: 아래 정의된 것처럼 오류 검색 비트의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2518">**errors_detected_ptr**: Destination for error detection bits, as defined below:</span></span>
  - <span data-ttu-id="47325-2519">FX_FAT_CHAIN_ERROR(0x01)</span><span class="sxs-lookup"><span data-stu-id="47325-2519">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="47325-2520">FX_DIRECTORY_ERROR(0x02) FX_LOST_CLUSTER_ERROR(0x04)</span><span class="sxs-lookup"><span data-stu-id="47325-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span></span>
  - <span data-ttu-id="47325-2521">FX_FILE_SIZE_ERROR(0x08)</span><span class="sxs-lookup"><span data-stu-id="47325-2521">FX_FILE_SIZE_ERROR (0x08)</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2522">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2522">Return Values</span></span>

- <span data-ttu-id="47325-2523">**FX_SUCCESS**(0x00) 미디어 검색에 성공했습니다. 자세한 내용은 오류 감지 대상을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="47325-2523">**FX_SUCCESS** (0x00) Successful media check, view the errors detected destination for details.</span></span>
- <span data-ttu-id="47325-2524">**FX_ACCESS_ERROR**(0x06) 파일이 열려 있는 상태에서는 검사를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2524">**FX_ACCESS_ERROR** (0x06) Unable to perform check with open files.</span></span>
- <span data-ttu-id="47325-2525">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2525">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-2526">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2526">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-2527">**FX_NO_MORE_SPACE**(0x0A) 미디어에 공간이 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2527">**FX_NO_MORE_SPACE** (0x0A) No more space on the media.</span></span>
- <span data-ttu-id="47325-2528">**FX_NOT_ENOUGH_MEMORY**(0x91) 제공된 스크래치 메모리가 충분히 크지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Supplied scratch memory is not large enough.</span></span>
- <span data-ttu-id="47325-2529">**FX_ERROR_NOT_FIXED**(0x93) 수정할 수 없는 FAT32 루트 디렉터리가 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2529">**FX_ERROR_NOT_FIXED** (0x93) Corruption of FAT32 root directory that could not be fixed.</span></span>
- <span data-ttu-id="47325-2530">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2531">**FX_SECTOR_INVALID**(0x89) 섹터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2531">**FX_SECTOR_INVALID** (0x89) Sector is invalid.</span></span>
- <span data-ttu-id="47325-2532">**FX_PTR_ERROR**(0x18) 미디어 또는 스크래치 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2532">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="47325-2533">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="47325-2534">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2534">Allowed From</span></span>

<span data-ttu-id="47325-2535">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2536">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2536">Example</span></span>

```c
FX_MEDIA         my_media;
ULONG             detected_errors;
UCHAR             sratch_memory[4096];

/* Check the media and correct all errors. */

status = fx_media_check(&my_media, sratch_memory, 4096,
                        FX_FAT_CHAIN_ERROR |
                        FX_DIRECTORY_ERROR |
                        FX_LOST_CLUSTER_ERROR, &detected_errors);

/* If status is FX_SUCCESS and detected_errors is 0,
    the media was successfully checked and found to be error free. */

```

### <a name="see-also"></a><span data-ttu-id="47325-2537">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2537">See Also</span></span>

- <span data-ttu-id="47325-2538">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2538">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2539">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2539">fx_media_abort</span></span>
- <span data-ttu-id="47325-2540">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2540">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2541">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2541">fx_media_close</span></span>
- <span data-ttu-id="47325-2542">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2542">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2543">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2543">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2544">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2544">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2545">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2545">fx_media_flush</span></span>
- <span data-ttu-id="47325-2546">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2546">fx_media_format</span></span>
- <span data-ttu-id="47325-2547">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2547">fx_media_open</span></span>
- <span data-ttu-id="47325-2548">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2548">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2549">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2549">fx_media_read</span></span>
- <span data-ttu-id="47325-2550">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2550">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2551">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2551">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2552">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2552">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2553">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2553">fx_media_write</span></span>
- <span data-ttu-id="47325-2554">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2554">fx_system_initialize</span></span>

## <a name="fx_media_close"></a><span data-ttu-id="47325-2555">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2555">fx_media_close</span></span>

<span data-ttu-id="47325-2556">미디어를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2556">Closes media</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2557">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2557">Prototype</span></span>

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="47325-2558">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2558">Description</span></span>

<span data-ttu-id="47325-2559">이 서비스는 지정된 미디어를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2559">This service closes the specified media.</span></span> <span data-ttu-id="47325-2560">미디어를 닫는 과정에서 열려 있는 파일이 모두 닫히고 나머지 버퍼는 실제 미디어로 플러시됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2560">In the process of closing the media, all open files are closed and any remaining buffers are flushed to the physical media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2561">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2561">Input Parameters</span></span>

- <span data-ttu-id="47325-2562">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2562">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2563">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2563">Return Values</span></span>

- <span data-ttu-id="47325-2564">**FX_SUCCESS**(0x00) 미디어 닫기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2564">**FX_SUCCESS** (0x00) Successful media close.</span></span>
- <span data-ttu-id="47325-2565">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2565">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-2566">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2566">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2567">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2567">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="47325-2568">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2568">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2569">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2569">Allowed From</span></span>

<span data-ttu-id="47325-2570">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2571">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2571">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a><span data-ttu-id="47325-2572">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2572">See Also</span></span>

- <span data-ttu-id="47325-2573">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2573">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2574">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2574">fx_media_abort</span></span>
- <span data-ttu-id="47325-2575">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2575">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2576">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2576">fx_media_check</span></span>
- <span data-ttu-id="47325-2577">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2577">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2578">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2578">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2579">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2579">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2580">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2580">fx_media_flush</span></span>
- <span data-ttu-id="47325-2581">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2581">fx_media_format</span></span>
- <span data-ttu-id="47325-2582">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2582">fx_media_open</span></span>
- <span data-ttu-id="47325-2583">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2583">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2584">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2584">fx_media_read</span></span>
- <span data-ttu-id="47325-2585">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2585">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2586">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2586">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2587">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2587">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2588">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2588">fx_media_write</span></span>
- <span data-ttu-id="47325-2589">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2589">fx_system_initialize</span></span>

## <a name="fx_media_close_notify_set"></a><span data-ttu-id="47325-2590">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2590">fx_media_close_notify_set</span></span>

<span data-ttu-id="47325-2591">미디어 닫기 알림 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2591">Sets the media close notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2592">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2592">Prototype</span></span>

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a><span data-ttu-id="47325-2593">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2593">Description</span></span>

<span data-ttu-id="47325-2594">이 서비스는 미디어가 닫힌 후 호출될 알림 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2594">This service sets a notify callback function which will be invoked after a media is successfully closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2595">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2595">Input Parameters</span></span>

- <span data-ttu-id="47325-2596">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2596">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-2597">**media_close_notify**: 설치할 미디어 닫기 알림 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2597">**media_close_notify**: Media close notify callback function to be installed.</span></span> <span data-ttu-id="47325-2598">콜백 함수로 NULL을 전달하면 미디어 닫기 콜백이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2598">Passing NULL as the callback function disables the media close callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2599">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2599">Return Values</span></span>

- <span data-ttu-id="47325-2600">**FX_SUCCESS**(0x00) 콜백 함수 설치에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2600">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="47325-2601">**FX_PTR_ERROR**(0x18) media_ptr이 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2601">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="47325-2602">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2602">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2603">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2603">Allowed From</span></span>

<span data-ttu-id="47325-2604">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2604">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2605">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2605">Example</span></span>

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a><span data-ttu-id="47325-2606">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2606">See Also</span></span>

- <span data-ttu-id="47325-2607">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2607">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2608">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2608">fx_media_abort</span></span>
- <span data-ttu-id="47325-2609">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2609">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2610">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2610">fx_media_check</span></span>
- <span data-ttu-id="47325-2611">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2611">fx_media_close</span></span>
- <span data-ttu-id="47325-2612">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2612">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2613">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2613">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2614">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2614">fx_media_flush</span></span>
- <span data-ttu-id="47325-2615">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2615">fx_media_format</span></span>
- <span data-ttu-id="47325-2616">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2616">fx_media_open</span></span>
- <span data-ttu-id="47325-2617">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2617">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2618">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2618">fx_media_read</span></span>
- <span data-ttu-id="47325-2619">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2619">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2620">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2620">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2621">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2621">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2622">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2622">fx_media_write</span></span>
- <span data-ttu-id="47325-2623">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2623">fx_system_initialize</span></span>

## <a name="fx_media_exfat_format"></a><span data-ttu-id="47325-2624">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2624">fx_media_exFAT_format</span></span>

<span data-ttu-id="47325-2625">미디어를 포맷합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2625">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2626">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2626">Prototype</span></span>

```c
UINT fx_media_exFAT_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr, 
    UCHAR *memory_ptr,
    UINT memory_size, 
    CHAR *volume_name,
    UINT number_of_fats,
    ULONG64 hidden_sectors, 
    ULONG64 total_sectors,
    UINT bytes_per_sector, 
    UINT sectors_per_cluster,
    UINT volume_serial_number, 
    UINT boundary_unit);
```
### <a name="description"></a><span data-ttu-id="47325-2627">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2627">Description</span></span>

<span data-ttu-id="47325-2628">이 서비스는 제공된 매개 변수에 따라 exFAT 호환 방식으로 제공된 미디어를 포맷합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2628">This service formats the supplied media in an exFAT compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="47325-2629">미디어를 열기 전에 이 서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2629">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-2630">이미 포맷된 미디어를 포맷하면 미디어의 파일과 디렉터리가 실제로 모두 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2630">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2631">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2631">Input Parameters</span></span>

- <span data-ttu-id="47325-2632">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2632">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="47325-2633">드라이버가 작동하는 데 필요한 몇 가지 기본적인 정보를 제공하기 위해서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2633">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="47325-2634">**driver**: 미디어의 I/O 드라이버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2634">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="47325-2635">일반적으로 후속 fx_media_open 호출에 제공되는 것과 동일한 드라이버입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2635">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="47325-2636">**driver_info_ptr**: I/O 드라이버가 활용할 수 있는 선택적 정보에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2636">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="47325-2637">**memory_ptr**: 미디어의 작업 메모리에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2637">**memory_ptr**: Pointer to the working memory for the media.</span></span> <span data-ttu-id="47325-2638">memory_size는 작업 미디어 메모리의 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2638">memory_size Specifies the size of the working media memory.</span></span> <span data-ttu-id="47325-2639">크기는 적어도 미디어의 섹터 크기보다 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2639">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="47325-2640">**volume_name**: 최대 11자인 볼륨 이름 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2640">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="47325-2641">**number_of_fats**: 미디어의 FAT 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2641">**number_of_fats**: Number of FATs on the media.</span></span> <span data-ttu-id="47325-2642">현재 구현에서는 미디어에서 FAT를 하나만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2642">Current implementation supports one FAT on the media.</span></span>
- <span data-ttu-id="47325-2643">**hidden_sectors**: 미디어의 부팅 섹터 앞에 숨겨진 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2643">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="47325-2644">파티션이 여러 개 있는 경우 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2644">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="47325-2645">**total_sectors**: 미디어의 총 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2645">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="47325-2646">**bytes_per_sector**: 섹터당 바이트 수로, 일반적으로 512입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2646">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="47325-2647">FileX에서는 32의 배수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2647">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="47325-2648">**sectors_per_cluster**: 각 클러스터의 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2648">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="47325-2649">클러스터는 FAT 파일 시스템의 최소 할당 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2649">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="47325-2650">**volumne_serial_number**: 볼륨에 사용할 일련 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2650">**volumne_serial_number**: Serial number to be used for this volume.</span></span>
- <span data-ttu-id="47325-2651">**boundary_unit**: 실제 데이터 영역 맞춤 크기입니다(섹터 수).</span><span class="sxs-lookup"><span data-stu-id="47325-2651">**boundary_unit**: Physical data area alignment size, in number of sectors.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2652">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2652">Return Values</span></span>

- <span data-ttu-id="47325-2653">**FX_SUCCESS**(0x00) 미디어 포맷에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2653">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="47325-2654">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2654">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2655">**FX_PTR_ERROR**(0x18) 미디어, 드라이버 또는 메모리 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2655">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="47325-2656">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2656">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2657">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2657">Allowed From</span></span>

<span data-ttu-id="47325-2658">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2658">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2659">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2659">Example</span></span>

```c
FX_MEDIA             sd_card;
UCHAR                 media_memory[512];

/* Format a 64GB SD card with exFAT file system. The media has
    been properly partitioned, with the partition starts from sector 32768.
    For 64GB, there are total of 120913920 sectors, each sector 512 bytes. */

status = fx_media_exFAT_format(&sd_card, _fx_sd_driver,
                                driver_information, media_memory,
                                sizeof(media_memory),
                                "exFAT_DISK" /* Volume Name */,
                                1 /* Number of FATs */,
                                32768 /* Hidden sectors */,
                                120913920 /* Total sectors */,
                                512 /* Sector size */,
                                256 /* Sectors per cluster */,
                                12345 /* Volume ID */,
                                8192 /* Boundary unit */);

/* If status is FX_SUCCESS, the media was successfully formatted. */

```

### <a name="see-also"></a><span data-ttu-id="47325-2660">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2660">See Also</span></span>

- <span data-ttu-id="47325-2661">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2661">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2662">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2662">fx_media_abort</span></span>
- <span data-ttu-id="47325-2663">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2663">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2664">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2664">fx_media_check</span></span>
- <span data-ttu-id="47325-2665">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2665">fx_media_close</span></span>
- <span data-ttu-id="47325-2666">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2666">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2667">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2667">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2668">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2668">fx_media_flush</span></span>
- <span data-ttu-id="47325-2669">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2669">fx_media_format</span></span>
- <span data-ttu-id="47325-2670">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2670">fx_media_open</span></span>
- <span data-ttu-id="47325-2671">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2671">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2672">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2672">fx_media_read</span></span>
- <span data-ttu-id="47325-2673">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2673">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2674">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2674">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2675">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2675">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2676">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2676">fx_media_write</span></span>
- <span data-ttu-id="47325-2677">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2677">fx_system_initialize</span></span>

## <a name="fx_media_extended_space_available"></a><span data-ttu-id="47325-2678">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2678">fx_media_extended_space_available</span></span>

<span data-ttu-id="47325-2679">사용 가능한 미디어 공간을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2679">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2680">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2680">Prototype</span></span>

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a><span data-ttu-id="47325-2681">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2681">Description</span></span>

<span data-ttu-id="47325-2682">이 서비스는 미디어에서 사용할 수 있는 바이트 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2682">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="47325-2683">이 서비스는 exFAT용으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2683">This service is designed for exFAT.</span></span> <span data-ttu-id="47325-2684">*available_bytes* 매개 변수에 대한 포인터는 64비트 정수 값을 사용합니다. 따라서 호출자가 4GB 범위를 벗어나 미디어를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2684">The pointer to *available_bytes* parameter takes a 64-bit integer value, which allows the caller to work with media beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2685">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2685">Input Parameters</span></span>

- <span data-ttu-id="47325-2686">**media_ptr**: 이전에 열린 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2686">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="47325-2687">**available_bytes_ptr**: 미디어에 남아 있는 사용 가능한 바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2687">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2688">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2688">Return Values</span></span>

- <span data-ttu-id="47325-2689">**FX_SUCCESS**(0x00) 미디어에서 사용 가능한 공간 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2689">**FX_SUCCESS** (0x00) Successfully retrieved space available on the media.</span></span>
- <span data-ttu-id="47325-2690">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2690">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-2691">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었거나 사용 가능한 바이트 포인터가 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2691">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="47325-2692">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2692">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2693">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2693">Allowed From</span></span>

<span data-ttu-id="47325-2694">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2694">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2695">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2695">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="47325-2696">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2696">See Also</span></span>

- <span data-ttu-id="47325-2697">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2697">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2698">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2698">fx_media_abort</span></span>
- <span data-ttu-id="47325-2699">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2699">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2700">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2700">fx_media_check</span></span>
- <span data-ttu-id="47325-2701">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2701">fx_media_close</span></span>
- <span data-ttu-id="47325-2702">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2702">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2703">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2703">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2704">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2704">fx_media_flush</span></span>
- <span data-ttu-id="47325-2705">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2705">fx_media_format</span></span>
- <span data-ttu-id="47325-2706">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2706">fx_media_open</span></span>
- <span data-ttu-id="47325-2707">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2707">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2708">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2708">fx_media_read</span></span>
- <span data-ttu-id="47325-2709">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2709">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2710">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2710">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2711">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2711">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2712">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2712">fx_media_write</span></span>
- <span data-ttu-id="47325-2713">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2713">fx_system_initialize</span></span>

## <a name="fx_media_flush"></a><span data-ttu-id="47325-2714">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2714">fx_media_flush</span></span>

<span data-ttu-id="47325-2715">실제 미디어로 데이터를 플러시합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2715">Flushes data to physical media</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2716">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2716">Prototype</span></span>

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="47325-2717">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2717">Description</span></span>

<span data-ttu-id="47325-2718">이 서비스는 캐시된 섹터와 수정된 파일의 디렉터리 항목을 모두 실제 미디어로 플러시합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2718">This service flushes all cached sectors and directory entries of any modified files to the physical media.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-2719">대상에서 갑작스러운 정전 발생 시 파일 손상 및/또는 데이터 손실 위험을 줄이기 위해 애플리케이션에서 이 루틴을 주기적으로 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2719">*This routine may be called periodically by the application to reduce the risk of file corruption and/or data loss in the event of a sudden loss of power on the target.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2720">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2720">Input Parameters</span></span>

- <span data-ttu-id="47325-2721">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2721">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2722">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2722">Return Values</span></span>

- <span data-ttu-id="47325-2723">**FX_SUCCESS**(0x00) 미디어 플러시에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2723">**FX_SUCCESS** (0x00) Successful media flush.</span></span>
- <span data-ttu-id="47325-2724">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2724">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-2725">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2725">**FX_FILE_CORRUPT**    (0x08) File is corrupted.</span></span>
- <span data-ttu-id="47325-2726">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2726">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-2727">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2727">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2728">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2728">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-2729">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2729">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="47325-2730">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2730">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2731">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2731">Allowed From</span></span>

<span data-ttu-id="47325-2732">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2733">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2733">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a><span data-ttu-id="47325-2734">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2734">See Also</span></span>

- <span data-ttu-id="47325-2735">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2735">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2736">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2736">fx_media_abort</span></span>
- <span data-ttu-id="47325-2737">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2737">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2738">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2738">fx_media_check</span></span>
- <span data-ttu-id="47325-2739">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2739">fx_media_close</span></span>
- <span data-ttu-id="47325-2740">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2740">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2741">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2741">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2742">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2742">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2743">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2743">fx_media_format</span></span>
- <span data-ttu-id="47325-2744">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2744">fx_media_open</span></span>
- <span data-ttu-id="47325-2745">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2745">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2746">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2746">fx_media_read</span></span>
- <span data-ttu-id="47325-2747">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2747">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2748">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2748">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2749">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2749">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2750">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2750">fx_media_write</span></span>
- <span data-ttu-id="47325-2751">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2751">fx_system_initialize</span></span>

## <a name="fx_media_format"></a><span data-ttu-id="47325-2752">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2752">fx_media_format</span></span>

<span data-ttu-id="47325-2753">미디어를 포맷합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2753">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2754">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2754">Prototype</span></span>

```c
UINT fx_media_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr,
    UCHAR *memory_ptr, 
    UINT memory_size,
    CHAR *volume_name, 
    UINT number_of_fats,
    UINT directory_entries, 
    UINT hidden_sectors,
    ULONG total_sectors, 
    UINT bytes_per_sector,
    UINT sectors_per_cluster,
    UINT heads,
    UINT sectors_per_track);
```
### <a name="description"></a><span data-ttu-id="47325-2755">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2755">Description</span></span>

<span data-ttu-id="47325-2756">이 서비스는 제공된 매개 변수에 따라 FAT 12/16/32 호환 방식으로 제공된 미디어를 포맷합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2756">This service formats the supplied media in a FAT 12/16/32 compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="47325-2757">미디어를 열기 전에 이 서비스를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2757">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-2758">이미 포맷된 미디어를 포맷하면 미디어의 파일과 디렉터리가 실제로 모두 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2758">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2759">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2759">Input Parameters</span></span>

- <span data-ttu-id="47325-2760">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2760">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="47325-2761">드라이버가 작동하는 데 필요한 몇 가지 기본적인 정보를 제공하기 위해서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2761">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="47325-2762">**driver**: 미디어의 I/O 드라이버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2762">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="47325-2763">일반적으로 후속 fx_media_open 호출에 제공되는 것과 동일한 드라이버입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2763">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="47325-2764">**driver_info_ptr**: I/O 드라이버가 활용할 수 있는 선택적 정보에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2764">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="47325-2765">**memory_ptr**: 미디어의 작업 메모리에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2765">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="47325-2766">**memory_size**: 작업 미디어 메모리의 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2766">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="47325-2767">크기는 적어도 미디어의 섹터 크기보다 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2767">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="47325-2768">**volume_name**: 최대 11자인 볼륨 이름 문자열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2768">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="47325-2769">**number_of_fats**: 미디어의 FAT 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2769">**number_of_fats**: Number of FATs in the media.</span></span> <span data-ttu-id="47325-2770">기본 FAT가 있기 때문에 최솟값은 1입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2770">The minimal value is 1 for the primary FAT.</span></span> <span data-ttu-id="47325-2771">값이 1보다 크면 런타임에 유지 관리 중인 추가 FAT 복사본이 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2771">Values greater than 1 result in additional FAT copies being maintained at run-time.</span></span>
- <span data-ttu-id="47325-2772">**directory_entries**: 루트 디렉터리의 디렉터리 항목 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2772">**directory_entries**: Number of directory entries in the root directory.</span></span>
- <span data-ttu-id="47325-2773">**hidden_sectors**: 미디어의 부팅 섹터 앞에 숨겨진 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2773">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="47325-2774">파티션이 여러 개 있는 경우 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2774">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="47325-2775">**total_sectors**: 미디어의 총 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2775">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="47325-2776">**bytes_per_sector**: 섹터당 바이트 수로, 일반적으로 512입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2776">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="47325-2777">FileX에서는 32의 배수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2777">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="47325-2778">**sectors_per_cluster**: 각 클러스터의 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2778">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="47325-2779">클러스터는 FAT 파일 시스템의 최소 할당 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2779">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="47325-2780">**heads**: 실제 헤드 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2780">**heads**: Number of physical heads.</span></span>
- <span data-ttu-id="47325-2781">**sectors_per_track**: 트랙당 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2781">**sectors_per_track**: Number of sectors per track.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2782">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2782">Return Values</span></span>

- <span data-ttu-id="47325-2783">**FX_SUCCESS**(0x00) 미디어 포맷에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2783">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="47325-2784">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2784">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2785">**FX_PTR_ERROR**(0x18) 미디어, 드라이버 또는 메모리 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2785">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="47325-2786">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2786">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2787">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2787">Allowed From</span></span>

<span data-ttu-id="47325-2788">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2788">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2789">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2789">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             media_memory[512];
UCHAR             ram_disk_memory[32768];

/* Format a RAM disk with 32768 bytes and 512 bytes per sector. */

status = fx_media_format(&ram_disk, _fx_ram_driver,
                         ram_disk_memory, media_memory,
                         sizeof(media_memory),
                         "MY_RAM_DISK" /* Volume Name */,
                         1 /* Number of FATs */,
                         32 /* Directory Entries */,
                         0 /* Hidden sectors */,
                         64 /* Total sectors */,
                         512 /* Sector size */,
                         1 /* Sectors per cluster */,
                         1 /* Heads */,
                         1 /* Sectors per track */);

/* If status is FX_SUCCESS, the media was successfully formatted
    and can now be opened with the following call: */

```

### <a name="see-also"></a><span data-ttu-id="47325-2790">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2790">See Also</span></span>

- <span data-ttu-id="47325-2791">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2791">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2792">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2792">fx_media_abort</span></span>
- <span data-ttu-id="47325-2793">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2793">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2794">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2794">fx_media_check</span></span>
- <span data-ttu-id="47325-2795">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2795">fx_media_close</span></span>
- <span data-ttu-id="47325-2796">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2796">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2797">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2797">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2798">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2798">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2799">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2799">fx_media_flush</span></span>
- <span data-ttu-id="47325-2800">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2800">fx_media_open</span></span>
- <span data-ttu-id="47325-2801">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2801">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2802">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2802">fx_media_read</span></span>
- <span data-ttu-id="47325-2803">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2803">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2804">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2804">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2805">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2805">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2806">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2806">fx_media_write</span></span>
- <span data-ttu-id="47325-2807">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2807">fx_system_initialize</span></span>

## <a name="fx_media_open"></a><span data-ttu-id="47325-2808">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2808">fx_media_open</span></span>

<span data-ttu-id="47325-2809">파일 액세스하기 위한 미디어를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2809">Opens media for file access</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2810">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2810">Prototype</span></span>

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a><span data-ttu-id="47325-2811">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2811">Description</span></span>

<span data-ttu-id="47325-2812">이 서비스는 제공된 I/O 드라이버를 사용하여 파일에 액세스하기 위한 미디어를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2812">This service opens a media for file access using the supplied I/O driver.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-2813">이 서비스에 제공되는 메모리는 내부 논리 섹터 캐시를 구현하는 데 사용되므로 더 많은 메모리가 제공될수록 실제 I/O는 더 줄어듭니다. FileX에는 최소한 한 개의 논리 섹터 캐시가 필요합니다(미디어의 섹터당 바이트 수).</span><span class="sxs-lookup"><span data-stu-id="47325-2813">*The memory supplied to this service is used to implement an internal logical sector cache, hence, the more memory supplied the more physical I/O is reduced. FileX requires a cache of at least one logical sector (bytes per sector of the media).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2814">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2814">Input Parameters</span></span>

- <span data-ttu-id="47325-2815">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2815">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-2816">**media_name**: 미디어 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2816">**media_name**: Pointer to media's name.</span></span>
- <span data-ttu-id="47325-2817">**media_driver**: 미디어의 I/O 드라이버에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2817">**media_driver**: Pointer to I/O driver for this media.</span></span> <span data-ttu-id="47325-2818">I/O 드라이버는 5장에서 정의한 FileX 드라이버 요구 사항을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2818">The I/O driver must conform to FileX driver requirements defined in Chapter 5.</span></span>
- <span data-ttu-id="47325-2819">**driver_info_ptr**: 제공된 I/O 드라이버가 활용할 수 있는 선택적 정보에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2819">**driver_info_ptr**: Pointer to optional information that the supplied I/O driver may utilize.</span></span>
- <span data-ttu-id="47325-2820">**memory_ptr**: 미디어의 작업 메모리에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2820">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="47325-2821">**memory_size**: 작업 미디어 메모리의 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2821">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="47325-2822">크기는 미디어의 섹터 크기만큼(일반적으로 512 바이트) 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2822">The size must be as large as the media's sector size (typically 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2823">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2823">Return Values</span></span>

- <span data-ttu-id="47325-2824">**FX_SUCCESS**(0x00) 미디어 열기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2824">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="47325-2825">**FX_BOOT_ERROR**(0x01) 미디어의 부팅 섹터를 읽는 중 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2825">**FX_BOOT_ERROR** (0x01) Error reading the media's boot sector.</span></span>
- <span data-ttu-id="47325-2826">**FX_MEDIA_INVALID**(0x02) 지정된 미디어의 부팅 섹터가 손상되었거나 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2826">**FX_MEDIA_INVALID** (0x02) Specified media's boot sector is corrupt or invalid.</span></span> <span data-ttu-id="47325-2827">또한 이 반환 코드는 논리 섹터 캐시 크기나 FAT 항목 크기가 2의 거듭제곱이 아님을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2827">In addition, this return code is used to indicate that either the logical sector cache size or the FAT entry size is not a power of 2.</span></span>
- <span data-ttu-id="47325-2828">**FX_FAT_READ_ERROR**(0x03) 미디어 FAT를 읽는 중 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2828">**FX_FAT_READ_ERROR** (0x03) Error reading the media FAT.</span></span>
- <span data-ttu-id="47325-2829">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2829">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2830">**FX_PTR_ERROR**(0x18) 하나 이상의 포인터가 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2830">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="47325-2831">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2831">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2832">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2832">Allowed From</span></span>

<span data-ttu-id="47325-2833">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2833">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2834">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2834">Example</span></span>

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a><span data-ttu-id="47325-2835">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2835">See Also</span></span>

- <span data-ttu-id="47325-2836">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2836">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2837">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2837">fx_media_abort</span></span>
- <span data-ttu-id="47325-2838">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2838">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2839">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2839">fx_media_check</span></span>
- <span data-ttu-id="47325-2840">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2840">fx_media_close</span></span>
- <span data-ttu-id="47325-2841">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2841">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2842">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2842">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2843">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2843">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2844">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2844">fx_media_flush</span></span>
- <span data-ttu-id="47325-2845">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2845">fx_media_format</span></span>
- <span data-ttu-id="47325-2846">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2846">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2847">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2847">fx_media_read</span></span>
- <span data-ttu-id="47325-2848">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2848">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2849">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2849">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2850">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2850">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2851">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2851">fx_media_write</span></span>
- <span data-ttu-id="47325-2852">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2852">fx_system_initialize</span></span>

## <a name="fx_media_open_notify_set"></a><span data-ttu-id="47325-2853">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2853">fx_media_open_notify_set</span></span>

<span data-ttu-id="47325-2854">미디어 열기 알림 기능을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2854">Sets the media open notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2855">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2855">Prototype</span></span>

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a><span data-ttu-id="47325-2856">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2856">Description</span></span>

<span data-ttu-id="47325-2857">이 서비스는 미디어가 열린 후 호출될 알림 콜백 함수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2857">This service sets a notify callback function which will be invoked after a media is successfully opened.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2858">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2858">Input Parameters</span></span>

- <span data-ttu-id="47325-2859">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2859">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-2860">**media_open_notify**: 설치할 미디어 열기 알림 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2860">**media_open_notify**: Media open notify callback function to be installed.</span></span> <span data-ttu-id="47325-2861">콜백 함수로 NULL을 전달하면 미디어 열기 콜백이 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2861">Passing NULL as the callback function disables the media open callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2862">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2862">Return Values</span></span>


- <span data-ttu-id="47325-2863">**FX_SUCCESS**(0x00) 콜백 함수 설치에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2863">**FX_SUCCESS** (0x00) Successfuly installed the callback function.</span></span>
- <span data-ttu-id="47325-2864">**FX_PTR_ERROR**(0x18) media_ptr이 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2864">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="47325-2865">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2865">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2866">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2866">Allowed From</span></span>

<span data-ttu-id="47325-2867">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2868">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2868">Example</span></span>

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a><span data-ttu-id="47325-2869">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2869">See Also</span></span>

- <span data-ttu-id="47325-2870">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2870">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2871">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2871">fx_media_abort</span></span>
- <span data-ttu-id="47325-2872">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2872">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2873">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2873">fx_media_check</span></span>
- <span data-ttu-id="47325-2874">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2874">fx_media_close</span></span>
- <span data-ttu-id="47325-2875">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2875">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2876">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2876">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2877">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2877">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2878">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2878">fx_media_flush</span></span>
- <span data-ttu-id="47325-2879">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2879">fx_media_format</span></span>
- <span data-ttu-id="47325-2880">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2880">fx_media_open</span></span>
- <span data-ttu-id="47325-2881">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2881">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2882">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2882">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2883">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2883">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2884">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2884">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2885">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2885">fx_media_write</span></span>
- <span data-ttu-id="47325-2886">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2886">fx_system_initialize</span></span>

## <a name="fx_media_read"></a><span data-ttu-id="47325-2887">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2887">fx_media_read</span></span>

<span data-ttu-id="47325-2888">미디어에서 논리 섹터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2888">Reads logical sector from media</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2889">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2889">Prototype</span></span>

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="47325-2890">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2890">Description</span></span>

<span data-ttu-id="47325-2891">이 서비스는 미디어에서 논리 섹터를 읽어 제공된 버퍼에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2891">This service reads a logical sector from the media and places it into the supplied buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2892">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2892">Input Parameters</span></span>

- <span data-ttu-id="47325-2893">**media_ptr**: 이전에 열린 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2893">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="47325-2894">**logical_sector**: 읽을 논리 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2894">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="47325-2895">**buffer_ptr**: 논리 섹터 읽기를 위한 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2895">**buffer_ptr**: Pointer to the destination for the logical sector read.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2896">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2896">Return Values</span></span>

- <span data-ttu-id="47325-2897">**FX_SUCCESS**(0x00) 미디어 읽기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2897">**FX_SUCCESS** (0x00) Successful media read.</span></span>
- <span data-ttu-id="47325-2898">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2898">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-2899">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2899">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2900">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2900">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-2901">**FX_PTR_ERROR**(0x18) 미디어 또는 버퍼 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2901">**FX_PTR_ERROR** (0x18) Invalid media or buffer pointer.</span></span>
- <span data-ttu-id="47325-2902">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2902">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2903">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2903">Allowed From</span></span>

<span data-ttu-id="47325-2904">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2904">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2905">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2905">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a><span data-ttu-id="47325-2906">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2906">See Also</span></span>

- <span data-ttu-id="47325-2907">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2907">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2908">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2908">fx_media_abort</span></span>
- <span data-ttu-id="47325-2909">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2909">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2910">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2910">fx_media_check</span></span>
- <span data-ttu-id="47325-2911">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2911">fx_media_close</span></span>
- <span data-ttu-id="47325-2912">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2912">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2913">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2913">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2914">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2914">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2915">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2915">fx_media_flush</span></span>
- <span data-ttu-id="47325-2916">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2916">fx_media_format</span></span>
- <span data-ttu-id="47325-2917">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2917">fx_media_open</span></span>
- <span data-ttu-id="47325-2918">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2918">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2919">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2919">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2920">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2920">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2921">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2921">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2922">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2922">fx_media_write</span></span>
- <span data-ttu-id="47325-2923">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2923">fx_system_initialize</span></span>

## <a name="fx_media_space_available"></a><span data-ttu-id="47325-2924">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2924">fx_media_space_available</span></span>

<span data-ttu-id="47325-2925">사용 가능한 미디어 공간을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2925">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2926">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2926">Prototype</span></span>

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a><span data-ttu-id="47325-2927">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2927">Description</span></span>

<span data-ttu-id="47325-2928">이 서비스는 미디어에서 사용할 수 있는 바이트 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2928">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="47325-2929">4GB보다 큰 미디어를 사용하여 작업하려면 애플리케이션이 *fx_media_extended_space_available* 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2929">To work with the media larger than 4GB, application shall use the service *fx_media_extended_space_available*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2930">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2930">Input Parameters</span></span>

- <span data-ttu-id="47325-2931">**media_ptr**: 이전에 열린 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2931">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="47325-2932">**available_bytes_ptr**: 미디어에 남아 있는 사용 가능한 바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2932">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2933">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2933">Return Values</span></span>

- <span data-ttu-id="47325-2934">**FX_SUCCESS**(0x00) 미디어에서 사용 가능한 공간 반환에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2934">**FX_SUCCESS** (0x00) Successfully returned available space on media.</span></span>
- <span data-ttu-id="47325-2935">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2935">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-2936">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었거나 사용 가능한 바이트 포인터가 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2936">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="47325-2937">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2937">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2938">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2938">Allowed From</span></span>

<span data-ttu-id="47325-2939">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2939">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2940">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2940">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="47325-2941">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2941">See Also</span></span>

- <span data-ttu-id="47325-2942">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2942">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2943">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2943">fx_media_abort</span></span>
- <span data-ttu-id="47325-2944">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2944">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2945">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2945">fx_media_check</span></span>
- <span data-ttu-id="47325-2946">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2946">fx_media_close</span></span>
- <span data-ttu-id="47325-2947">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2947">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2948">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2948">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2949">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2949">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2950">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2950">fx_media_flush</span></span>
- <span data-ttu-id="47325-2951">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2951">fx_media_format</span></span>
- <span data-ttu-id="47325-2952">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2952">fx_media_open</span></span>
- <span data-ttu-id="47325-2953">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2953">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2954">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2954">fx_media_read</span></span>
- <span data-ttu-id="47325-2955">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2955">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-2956">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2956">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2957">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2957">fx_media_write</span></span>
- <span data-ttu-id="47325-2958">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2958">fx_system_initialize</span></span>

## <a name="fx_media_volume_get"></a><span data-ttu-id="47325-2959">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-2959">fx_media_volume_get</span></span>

<span data-ttu-id="47325-2960">미디어 볼륨 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2960">Gets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-2961">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-2961">Prototype</span></span>

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="47325-2962">Description</span><span class="sxs-lookup"><span data-stu-id="47325-2962">Description</span></span>

<span data-ttu-id="47325-2963">이 서비스는 이전에 열린 미디어의 볼륨 이름을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2963">This service retrieves the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-2964">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-2964">Input Parameters</span></span>

- <span data-ttu-id="47325-2965">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2965">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-2966">**volume_name**: 볼륨 이름의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2966">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="47325-2967">대상은 최소한 12자를 포함할 수 있을 정도로 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2967">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="47325-2968">**volume_source**: 부팅 섹터 또는 루트 디렉터리에서 이름을 검색할 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2968">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="47325-2969">이 매개 변수에 유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2969">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="47325-2970">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="47325-2970">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="47325-2971">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="47325-2971">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-2972">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-2972">Return Values</span></span>

- <span data-ttu-id="47325-2973">**FX_SUCCESS**(0x00) 미디어 볼륨 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2973">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="47325-2974">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2974">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-2975">**FX_NOT_FOUND**(0x04) 볼륨을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2975">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="47325-2976">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2976">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-2977">**FX_PTR_ERROR**(0x18) 미디어 또는 볼륨 대상 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2977">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="47325-2978">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-2978">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-2979">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-2979">Allowed From</span></span>

<span data-ttu-id="47325-2980">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-2980">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-2981">예제</span><span class="sxs-lookup"><span data-stu-id="47325-2981">Example</span></span>

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a><span data-ttu-id="47325-2982">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-2982">See Also</span></span>

- <span data-ttu-id="47325-2983">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-2983">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-2984">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-2984">fx_media_abort</span></span>
- <span data-ttu-id="47325-2985">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-2985">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-2986">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-2986">fx_media_check</span></span>
- <span data-ttu-id="47325-2987">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-2987">fx_media_close</span></span>
- <span data-ttu-id="47325-2988">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2988">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-2989">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-2989">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-2990">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2990">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-2991">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-2991">fx_media_flush</span></span>
- <span data-ttu-id="47325-2992">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-2992">fx_media_format</span></span>
- <span data-ttu-id="47325-2993">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-2993">fx_media_open</span></span>
- <span data-ttu-id="47325-2994">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-2994">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-2995">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-2995">fx_media_read</span></span>
- <span data-ttu-id="47325-2996">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-2996">fx_media_space_available</span></span>
- <span data-ttu-id="47325-2997">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-2997">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-2998">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-2998">fx_media_write</span></span>
- <span data-ttu-id="47325-2999">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-2999">fx_system_initialize</span></span>

## <a name="fx_media_volume_get_extended"></a><span data-ttu-id="47325-3000">fx_media_volume_get_extended</span><span class="sxs-lookup"><span data-stu-id="47325-3000">fx_media_volume_get_extended</span></span>

<span data-ttu-id="47325-3001">이전에 열린 미디어의 미디어 볼륨 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3001">Gets media volume name of previously opened media</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3002">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3002">Prototype</span></span>

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="47325-3003">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3003">Description</span></span>

<span data-ttu-id="47325-3004">이 서비스는 이전에 열린 미디어의 볼륨 이름을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3004">This service retrieves the volume name of the previously opened media.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-3005">이 서비스는 호출자가 _ *volume_name*\* 버퍼의 크기를 전달한다는 점을 제외하면 \***fx_media_volume_get()** _와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3005">This service is identical to ***fx_media_volume_get()** _ except the caller passes in the size of the _ *volume_name** buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3006">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3006">Input Parameters</span></span>


- <span data-ttu-id="47325-3007">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3007">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-3008">**volume_name**: 볼륨 이름의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3008">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="47325-3009">대상은 최소한 12자를 포함할 수 있을 정도로 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3009">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="47325-3010">**volume_name_buffer_length**: volume_name 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3010">**volume_name_buffer_length**: Size of volume_name buffer.</span></span>
- <span data-ttu-id="47325-3011">**volume_source**: 부팅 섹터 또는 루트 디렉터리에서 이름을 검색할 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3011">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="47325-3012">이 매개 변수에 유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3012">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="47325-3013">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="47325-3013">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="47325-3014">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="47325-3014">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3015">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3015">Return Values</span></span>

- <span data-ttu-id="47325-3016">**FX_SUCCESS**(0x00) 미디어 볼륨 가져오기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3016">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="47325-3017">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3017">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-3018">**FX_NOT_FOUND**(0x04) 볼륨을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3018">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="47325-3019">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3019">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-3020">**FX_PTR_ERROR**(0x18) 미디어 또는 볼륨 대상 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3020">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="47325-3021">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3021">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3022">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3022">Allowed From</span></span>

<span data-ttu-id="47325-3023">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3023">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3024">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3024">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="47325-3025">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3025">See Also</span></span>

- <span data-ttu-id="47325-3026">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-3026">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-3027">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-3027">fx_media_abort</span></span>
- <span data-ttu-id="47325-3028">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-3028">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-3029">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-3029">fx_media_check</span></span>
- <span data-ttu-id="47325-3030">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-3030">fx_media_close</span></span>
- <span data-ttu-id="47325-3031">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3031">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-3032">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-3032">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-3033">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-3033">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-3034">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-3034">fx_media_flush</span></span>
- <span data-ttu-id="47325-3035">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-3035">fx_media_format</span></span>
- <span data-ttu-id="47325-3036">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-3036">fx_media_open</span></span>
- <span data-ttu-id="47325-3037">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3037">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-3038">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-3038">fx_media_read</span></span>
- <span data-ttu-id="47325-3039">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-3039">fx_media_space_available</span></span>
- <span data-ttu-id="47325-3040">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-3040">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-3041">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-3041">fx_media_write</span></span>
- <span data-ttu-id="47325-3042">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-3042">fx_system_initialize</span></span>

## <a name="fx_media_volume_set"></a><span data-ttu-id="47325-3043">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-3043">fx_media_volume_set</span></span>

<span data-ttu-id="47325-3044">미디어 볼륨 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3044">Sets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3045">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3045">Prototype</span></span>

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a><span data-ttu-id="47325-3046">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3046">Description</span></span>

<span data-ttu-id="47325-3047">이 서비스는 이전에 열린 미디어의 볼륨 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3047">This service sets the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3048">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3048">Input Parameters</span></span>

- <span data-ttu-id="47325-3049">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3049">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-3050">**volume_name**: 볼륨 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3050">**volume_name**: Pointer to the volume name.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3051">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3051">Return Values</span></span>

- <span data-ttu-id="47325-3052">**FX_SUCCESS**(0x00) 미디어 볼륨 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3052">**FX_SUCCESS** (0x00) Successful media volume set.</span></span>
- <span data-ttu-id="47325-3053">**FX_INVALID_NAME**(0x0C) Volume_name이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3053">**FX_INVALID_NAME** (0x0C) Volume_name is invalid.</span></span>
- <span data-ttu-id="47325-3054">**FX_MEDIA_INVALID**(0x02) 볼륨 이름을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3054">**FX_MEDIA_INVALID** (0x02) Unable to set volume name.</span></span>
- <span data-ttu-id="47325-3055">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3055">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-3056">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3056">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-3057">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3057">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-3058">**FX_PTR_ERROR**(0x18) 미디어 또는 볼륨 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3058">**FX_PTR_ERROR** (0x18) Invalid media or volume name pointer.</span></span>
- <span data-ttu-id="47325-3059">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3059">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3060">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3060">Allowed From</span></span>

<span data-ttu-id="47325-3061">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3061">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3062">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3062">Example</span></span>

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="47325-3063">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3063">See Also</span></span>

- <span data-ttu-id="47325-3064">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-3064">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-3065">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-3065">fx_media_abort</span></span>
- <span data-ttu-id="47325-3066">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-3066">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-3067">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-3067">fx_media_check</span></span>
- <span data-ttu-id="47325-3068">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-3068">fx_media_close</span></span>
- <span data-ttu-id="47325-3069">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3069">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-3070">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-3070">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-3071">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-3071">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-3072">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-3072">fx_media_flush</span></span>
- <span data-ttu-id="47325-3073">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-3073">fx_media_format</span></span>
- <span data-ttu-id="47325-3074">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-3074">fx_media_open</span></span>
- <span data-ttu-id="47325-3075">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3075">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-3076">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-3076">fx_media_read</span></span>
- <span data-ttu-id="47325-3077">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-3077">fx_media_space_available</span></span>
- <span data-ttu-id="47325-3078">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-3078">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-3079">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-3079">fx_media_write</span></span>
- <span data-ttu-id="47325-3080">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-3080">fx_system_initialize</span></span>

## <a name="fx_media_write"></a><span data-ttu-id="47325-3081">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="47325-3081">fx_media_write</span></span>

<span data-ttu-id="47325-3082">논리 섹터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3082">Writes logical sector</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3083">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3083">Prototype</span></span>

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="47325-3084">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3084">Description</span></span>

<span data-ttu-id="47325-3085">이 서비스는 지정된 논리 섹터에 제공된 버퍼를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3085">This service writes the supplied buffer to the specified logical sector.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3086">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3086">Input Parameters</span></span>

- <span data-ttu-id="47325-3087">**media_ptr**: 이전에 열린 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3087">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="47325-3088">**logical_sector**: 쓸 논리 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3088">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="47325-3089">**buffer_ptr**: 논리 섹터 쓰기의 원본에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3089">**buffer_ptr**: Pointer to the source for the logical sector write.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3090">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3090">Return Values</span></span>

- <span data-ttu-id="47325-3091">**FX_SUCCESS**(0x00) 미디어 쓰기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3091">**FX_SUCCESS** (0x00) Successful media write.</span></span>
- <span data-ttu-id="47325-3092">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3092">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-3093">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3093">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-3094">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3094">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-3095">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3095">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-3096">**FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3096">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="47325-3097">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3097">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3098">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3098">Allowed From</span></span>

<span data-ttu-id="47325-3099">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3099">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3100">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3100">Example</span></span>

```c
FX_MEDIA             my_media;
UCHAR                 my_buffer[128];
UINT                 status;

/* Write logical sector 22 from "my_buffer" assuming
    the physical media has a sector size of 128. */

status = fx_media_write(&my_media, 22, my_buffer);

/* If status equals FX_SUCCESS, the contents of logical
    sector 22 are now the same as "my_buffer." */
```

### <a name="see-also"></a><span data-ttu-id="47325-3101">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3101">See Also</span></span>

- <span data-ttu-id="47325-3102">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="47325-3102">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="47325-3103">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="47325-3103">fx_media_abort</span></span>
- <span data-ttu-id="47325-3104">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="47325-3104">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="47325-3105">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="47325-3105">fx_media_check</span></span>
- <span data-ttu-id="47325-3106">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="47325-3106">fx_media_close</span></span>
- <span data-ttu-id="47325-3107">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3107">fx_media_close_notify_set</span></span>
- <span data-ttu-id="47325-3108">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="47325-3108">fx_media_exFAT_format</span></span>
- <span data-ttu-id="47325-3109">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-3109">fx_media_extended_space_available</span></span>
- <span data-ttu-id="47325-3110">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="47325-3110">fx_media_flush</span></span>
- <span data-ttu-id="47325-3111">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="47325-3111">fx_media_format</span></span>
- <span data-ttu-id="47325-3112">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="47325-3112">fx_media_open</span></span>
- <span data-ttu-id="47325-3113">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3113">fx_media_open_notify_set</span></span>
- <span data-ttu-id="47325-3114">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="47325-3114">fx_media_read</span></span>
- <span data-ttu-id="47325-3115">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="47325-3115">fx_media_space_available</span></span>
- <span data-ttu-id="47325-3116">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="47325-3116">fx_media_volume_get</span></span>
- <span data-ttu-id="47325-3117">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="47325-3117">fx_media_volume_set</span></span>
- <span data-ttu-id="47325-3118">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-3118">fx_system_initialize</span></span>

## <a name="fx_system_date_get"></a><span data-ttu-id="47325-3119">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="47325-3119">fx_system_date_get</span></span>

<span data-ttu-id="47325-3120">파일 시스템 날짜를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3120">Gets file system date</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3121">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3121">Prototype</span></span>

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a><span data-ttu-id="47325-3122">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3122">Description</span></span>

<span data-ttu-id="47325-3123">이 서비스는 현재 시스템 날짜를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3123">This service returns the current system date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3124">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3124">Input Parameters</span></span>

- <span data-ttu-id="47325-3125">**year**: 연도의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3125">**year**: Pointer to destination for year.</span></span>
- <span data-ttu-id="47325-3126">**month**: 월의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3126">**month**: Pointer to destination for month.</span></span>
- <span data-ttu-id="47325-3127">**day**: 날짜의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3127">**day**: Pointer to destination for day.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3128">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3128">Return Values</span></span>

- <span data-ttu-id="47325-3129">**FX_SUCCESS**(0x00) 날짜 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3129">**FX_SUCCESS** (0x00) Successful date retrieval.</span></span>
- <span data-ttu-id="47325-3130">**FX_PTR_ERROR**(0x18) 하나 이상의 입력 매개 변수가 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3130">**FX_PTR_ERROR** (0x18) One or more of the input parameters are NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3131">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3131">Allowed From</span></span>

<span data-ttu-id="47325-3132">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3133">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3133">Example</span></span>

```c
UINT            status;
UINT            year;
UINT            month;
UINT            day;
/* Retrieve the current system date. */

status = fx_system_date_get(&year, &month, &day);

/* If status equals FX_SUCCESS, the year, month,
    and day parameters now have meaningful information. */
```

### <a name="see-also"></a><span data-ttu-id="47325-3134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3134">See Also</span></span>

- <span data-ttu-id="47325-3135">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="47325-3135">fx_system_date_set</span></span>
- <span data-ttu-id="47325-3136">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-3136">fx_system_initialize</span></span>
- <span data-ttu-id="47325-3137">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="47325-3137">fx_system_time_get</span></span>
- <span data-ttu-id="47325-3138">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3138">fx_system_time_set</span></span>

## <a name="fx_system_date_set"></a><span data-ttu-id="47325-3139">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="47325-3139">fx_system_date_set</span></span>

<span data-ttu-id="47325-3140">시스템 날짜를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3140">Sets system date</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3141">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3141">Prototype</span></span>

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a><span data-ttu-id="47325-3142">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3142">Description</span></span>

<span data-ttu-id="47325-3143">이 서비스는 지정된 대로 시스템 날짜를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3143">This service sets the system date as specified.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-3144">초기 시스템 날짜를 설정하려면 **fx_system_initialize** 직후에 서비스를 호출해야 합니다. 기본적으로 시스템 날짜는 마지막 일반 FileX 릴리스의 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3144">*This service should be called shortly after **fx_system_initialize** to set the initial system date. By default, the system date is that of the last generic FileX release.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3145">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3145">Input Parameters</span></span>

- <span data-ttu-id="47325-3146">**year**: 새 연도입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3146">**year**: New year.</span></span> <span data-ttu-id="47325-3147">유효 범위는 1980~2107년입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3147">The valid range is from 1980 through the year 2107.</span></span>
- <span data-ttu-id="47325-3148">**month**: 새 월입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3148">**month**: New month.</span></span> <span data-ttu-id="47325-3149">유효 범위는 1~12입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3149">The valid range is from 1 through 12.</span></span>
- <span data-ttu-id="47325-3150">**day**: 새 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3150">**day**: New day.</span></span> <span data-ttu-id="47325-3151">유효 범위는 월과 윤년 조건에 따라 1~31입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3151">The valid range is from 1 through 31, depending on month and leap year conditions.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3152">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3152">Return Values</span></span>

- <span data-ttu-id="47325-3153">**FX_SUCCESS**(0x00) 날짜 설정에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3153">**FX_SUCCESS** (0x00) Successful date setting.</span></span>
- <span data-ttu-id="47325-3154">**FX_INVALID_YEAR**(0x12) 지정된 연도가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3154">**FX_INVALID_YEAR** (0x12) Invalid year specified.</span></span>
- <span data-ttu-id="47325-3155">**FX_INVALID_MONTH**(0x13) 지정된 월이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3155">**FX_INVALID_MONTH** (0x13) Invalid month specified.</span></span>
- <span data-ttu-id="47325-3156">**FX_INVALID_DAY**(0x14) 지정된 날짜가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3156">**FX_INVALID_DAY** (0x14) Invalid day specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3157">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3157">Allowed From</span></span>

<span data-ttu-id="47325-3158">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3158">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3159">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3159">Example</span></span>

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a><span data-ttu-id="47325-3160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3160">See Also</span></span>

- <span data-ttu-id="47325-3161">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="47325-3161">fx_system_date_get</span></span>
- <span data-ttu-id="47325-3162">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-3162">fx_system_initialize</span></span>
- <span data-ttu-id="47325-3163">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="47325-3163">fx_system_time_get</span></span>
- <span data-ttu-id="47325-3164">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3164">fx_system_time_set</span></span>

## <a name="fx_system_initialize"></a><span data-ttu-id="47325-3165">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-3165">fx_system_initialize</span></span>

<span data-ttu-id="47325-3166">전체 시스템을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3166">Initializes entire system</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3167">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3167">Prototype</span></span>

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a><span data-ttu-id="47325-3168">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3168">Description</span></span>

<span data-ttu-id="47325-3169">이 서비스는 모든 주요 FileX 데이터 구조를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3169">This service initializes all the major FileX data structures.</span></span> <span data-ttu-id="47325-3170">***Tx_application_define*** 에서 호출해야 하며 초기화 스레드에서 호출할 수도 있고 기타 모든 FileX 서비스를 사용하기 전에 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3170">It should be called either in ***tx_application_define*** or possibly from an initialization thread and must be called prior to using any other FileX service.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-3171">\*이와 같이 호출하여 초기화되면 애플리케이션은 **fx_system_date_set** _ 및 _ \*fx_system_time_set\*\*을 호출하여 정확한 시스템 날짜와 시간으로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3171">*Once initialized by this call, the application should call ***fx_system_date_set** _ and _ *fx_system_time_set** to start with an accurate system date and time.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3172">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3172">Input Parameters</span></span>

<span data-ttu-id="47325-3173">None</span><span class="sxs-lookup"><span data-stu-id="47325-3173">None</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3174">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3174">Return Values</span></span>

<span data-ttu-id="47325-3175">없음</span><span class="sxs-lookup"><span data-stu-id="47325-3175">None.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3176">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3176">Allowed From</span></span>

<span data-ttu-id="47325-3177">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3177">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3178">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3178">Example</span></span>

```c
void tx_application_define(VOID *free_memory)
{
    UINT status;
    /* Initialize the FileX system. */
    fx_system_initialize();
    /* Set the file system date. */
    fx_system_date_set(my_year, my_month, my_day);

    /* Set the file system time. */
    fx_system_time_set(my_hour, my_minute, my_second);

    /* Now perform all other initialization and possibly FileX media
        open calls if the corresponding driver does not block on the boot sector read. */

    ...

}
```

### <a name="see-also"></a><span data-ttu-id="47325-3179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3179">See Also</span></span>

- <span data-ttu-id="47325-3180">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="47325-3180">fx_system_date_get</span></span>
- <span data-ttu-id="47325-3181">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="47325-3181">fx_system_date_set</span></span>
- <span data-ttu-id="47325-3182">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="47325-3182">fx_system_time_get</span></span>
- <span data-ttu-id="47325-3183">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3183">fx_system_time_set</span></span>

## <a name="fx_system_time_get"></a><span data-ttu-id="47325-3184">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="47325-3184">fx_system_time_get</span></span>

<span data-ttu-id="47325-3185">현재 시스템 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3185">Gets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3186">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3186">Prototype</span></span>

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="47325-3187">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3187">Description</span></span>

<span data-ttu-id="47325-3188">이 서비스는 현재 시스템 시간을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3188">This service retrieves the current system time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3189">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3189">Input Parameters</span></span>

- <span data-ttu-id="47325-3190">**hour**: 시간의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3190">**hour**: Pointer to destination for hour.</span></span>
- <span data-ttu-id="47325-3191">**minute**: 분의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3191">**minute**: Pointer to destination for minute.</span></span>
- <span data-ttu-id="47325-3192">**second**: 초의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3192">**second**: Pointer to destination for second.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3193">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3193">Return Values</span></span>

- <span data-ttu-id="47325-3194">**FX_SUCCESS**(0x00) 시스템 시간 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3194">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="47325-3195">**FX_PTR_ERROR**(0x18) 하나 이상의 입력 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3195">**FX_PTR_ERROR** (0x18) One or more of the input parameters</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3196">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3196">Allowed From</span></span>

<span data-ttu-id="47325-3197">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3197">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3198">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3198">Example</span></span>

```c
UINT             status;
UINT             hour;
UINT             minute;
UINT             second;

/* Retrieve the current system time. */

status = fx_system_time_get(&hour, &minute, &second);

/* If status equals FX_SUCCESS, the current system time
    is in the hour, minute, and second variables. */
```

### <a name="see-also"></a><span data-ttu-id="47325-3199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3199">See Also</span></span>

- <span data-ttu-id="47325-3200">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="47325-3200">fx_system_date_get</span></span>
- <span data-ttu-id="47325-3201">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="47325-3201">fx_system_date_set</span></span>
- <span data-ttu-id="47325-3202">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-3202">fx_system_initialize</span></span>
- <span data-ttu-id="47325-3203">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3203">fx_system_time_set</span></span>

## <a name="fx_system_time_set"></a><span data-ttu-id="47325-3204">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3204">fx_system_time_set</span></span>

<span data-ttu-id="47325-3205">현재 시스템 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3205">Sets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3206">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3206">Prototype</span></span>

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a><span data-ttu-id="47325-3207">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3207">Description</span></span>

<span data-ttu-id="47325-3208">이 서비스는 현재 시스템 시간을 입력 매개 변수로 지정된 시간으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3208">This service sets the current system time to that specified by the input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-3209">초기 시스템 시간을 설정하려면 **fx_system_initialize** 직후 이 서비스를 호출해야 합니다. 기본적으로 시스템 시간은 0:0:0입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3209">*This service should be called shortly after **fx_system_initialize** to set the initial system time. By default, the system time is 0:0:0.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3210">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3210">Input Parameters</span></span>

- <span data-ttu-id="47325-3211">**hour**: 새 시간입니다(0~23).</span><span class="sxs-lookup"><span data-stu-id="47325-3211">**hour**: New hour (0-23).</span></span>
- <span data-ttu-id="47325-3212">**분**: 새 분입니다(0~59).</span><span class="sxs-lookup"><span data-stu-id="47325-3212">**minute**: New minute (0-59).</span></span>
- <span data-ttu-id="47325-3213">**초**: 새 초입니다(0~59).</span><span class="sxs-lookup"><span data-stu-id="47325-3213">**second**: New second (0-59).</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3214">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3214">Return Values</span></span>

- <span data-ttu-id="47325-3215">**FX_SUCCESS**(0x00) 시스템 시간 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3215">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="47325-3216">**FX_INVALID_HOUR**(0x15) 새 시간이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3216">**FX_INVALID_HOUR**    (0x15) New hour is invalid.</span></span>
- <span data-ttu-id="47325-3217">**FX_INVALID_MINUTE**(0x16) 새 분이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3217">**FX_INVALID_MINUTE** (0x16) New minute is invalid.</span></span>
- <span data-ttu-id="47325-3218">**FX_INVALID_SECOND**(0x17) 새 초가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3218">**FX_INVALID_SECOND** (0x17) New second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3219">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3219">Allowed From</span></span>

<span data-ttu-id="47325-3220">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3220">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3221">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3221">Example</span></span>

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a><span data-ttu-id="47325-3222">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3222">See Also</span></span>

- <span data-ttu-id="47325-3223">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="47325-3223">fx_system_date_get</span></span>
- <span data-ttu-id="47325-3224">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="47325-3224">fx_system_date_set</span></span>
- <span data-ttu-id="47325-3225">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="47325-3225">fx_system_initialize</span></span>
- <span data-ttu-id="47325-3226">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="47325-3226">fx_system_time_get</span></span>

## <a name="fx_unicode_directory_create"></a><span data-ttu-id="47325-3227">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-3227">fx_unicode_directory_create</span></span>

<span data-ttu-id="47325-3228">유니코드 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3228">Creates a Unicode directory</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3229">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3229">Prototype</span></span>

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a><span data-ttu-id="47325-3230">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3230">Description</span></span>

<span data-ttu-id="47325-3231">이 서비스는 현재 기본 디렉터리에 유니코드 이름이 지정된 하위 디렉터리를 만듭니다. 유니코드 원본 이름 매개 변수에는 경로 정보가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3231">This service creates a Unicode-named subdirectory in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="47325-3232">성공하면 서비스에서 새로 만든 유니코드 하위 디렉터리의 짧은 이름(8.3 형식)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3232">If successful, the short name (8.3 format) of the newly created Unicode subdirectory is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-3233">반환된 짧은 이름(8.3 형식)을 표준 FileX 디렉터리 서비스에 제공하여 유니코드 하위 디렉터리에 대한 모든 작업(이 디렉터리를 기본 경로로 설정, 삭제 등)을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3233">*All operations on the Unicode subdirectory (making it the default path, deleting, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX directory services.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-3234">이 서비스는 exFAT 미디어에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3234">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3235">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3235">Input Parameters</span></span>

- <span data-ttu-id="47325-3236">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3236">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-3237">**source_unicode_name**: 새 하위 디렉터리의 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3237">**source_unicode_name**: Pointer to the Unicode name for the new subdirectory.</span></span>
- <span data-ttu-id="47325-3238">**source_unicode_length**: 유니코드 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3238">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="47325-3239">**short_name**: 새 유니코드 하위 디렉터리의 짧은 이름(8.3 형식) 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3239">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode subdirectory.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3240">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3240">Return Values</span></span>

- <span data-ttu-id="47325-3241">**FX_SUCCESS**(0x00) 유니코드 디렉터리 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3241">**FX_SUCCESS** (0x00) Successful Unicode directory create.</span></span>
- <span data-ttu-id="47325-3242">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3242">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-3243">**FX_ALREADY_CREATED**(0x0B) 지정한 디렉터리가 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3243">**FX_ALREADY_CREATED** (0x0B) Specified directory already exists.</span></span>
- <span data-ttu-id="47325-3244">**FX_NO_MORE_SPACE**(0x0A) 새 디렉터리 항목의 미디어에 사용 가능한 클러스터가 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3244">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new directory entry.</span></span>
- <span data-ttu-id="47325-3245">**FX_NOT_IMPLEMENTED**(0x22) exFAT 파일 시스템을 위해 서비스가 구현되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3245">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="47325-3246">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3246">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-3247">**FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3247">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="47325-3248">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3248">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="47325-3249">**FX_IO_ERROR(0x90)** 드라이버 I/O 오류.</span><span class="sxs-lookup"><span data-stu-id="47325-3249">**FX_IO_ERROR    (0x90)** Driver I/O error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3250">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3250">Allowed From</span></span>

<span data-ttu-id="47325-3251">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3252">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3252">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_short_name[13];
UCHAR                 my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                         0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                         0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                         0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                         0x63,0x00, 0x00,0x00};

/* Create a Unicode subdirectory with the name contained in "my_unicode_name". */

length = fx_unicode_directory_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode subdirectory is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="47325-3253">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3253">See Also</span></span>

- <span data-ttu-id="47325-3254">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-3254">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-3255">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-3255">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-3256">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-3256">fx_directory_create</span></span>
- <span data-ttu-id="47325-3257">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-3257">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-3258">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-3258">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-3259">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-3259">fx_directory_delete</span></span>
- <span data-ttu-id="47325-3260">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-3260">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-3261">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-3261">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-3262">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-3262">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-3263">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-3263">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-3264">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-3264">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-3265">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-3265">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-3266">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-3266">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-3267">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3267">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-3268">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-3268">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-3269">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-3269">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-3270">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-3270">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-3271">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3271">fx_directory_rename</span></span>
- <span data-ttu-id="47325-3272">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3272">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-3273">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3273">fx_unicode_directory_rename</span></span>

## <a name="fx_unicode_directory_rename"></a><span data-ttu-id="47325-3274">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3274">fx_unicode_directory_rename</span></span>

<span data-ttu-id="47325-3275">유니코드 문자열을 사용하여 디렉터리 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3275">Renames directory using Unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3276">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3276">Prototype</span></span>

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a><span data-ttu-id="47325-3277">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3277">Description</span></span>

<span data-ttu-id="47325-3278">이 서비스는 유니코드 이름이 지정된 하위 디렉터리를 현재 작업 디렉터리의 지정된 새 유니코드 이름으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3278">This service changes a Unicode-named subdirectory to specified new Unicode name in current working directory.</span></span> <span data-ttu-id="47325-3279">유니코드 이름 매개 변수에는 경로 정보가 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3279">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-3280">이 서비스는 exFAT 미디어에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3280">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3281">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3281">Input Parameters</span></span>

- <span data-ttu-id="47325-3282">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3282">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-3283">**old_unicode_name**: 현재 파일의 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3283">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="47325-3284">**old_unicode_name_length**: 현재 유니코드 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3284">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="47325-3285">**new_unicode_name**: 새 유니코드 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3285">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="47325-3286">**old_unicode_name_length**: 새 유니코드 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3286">**old_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="47325-3287">**new_short_name**: 이름이 바뀐 유니코드 파일의 짧은 이름(8.3 형식)의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3287">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span> <span data-ttu-id="47325-3288">유니코드로 디렉터리 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3288">Rename Directory with Unicode</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3289">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3289">Return Values</span></span>

- <span data-ttu-id="47325-3290">**FX_SUCCESS**(0x00) 미디어 열기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3290">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="47325-3291">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3291">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-3292">**FX_ALREADY_CREATED**(0x0B) 지정한 디렉터리 이름이 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3292">**FX_ALREADY_CREATED** (0x0B) Specified directory name already exists.</span></span>
- <span data-ttu-id="47325-3293">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3293">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-3294">**FX_PTR_ERROR**(0x18) 하나 이상의 포인터가 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3294">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="47325-3295">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3295">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="47325-3296">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3296">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3297">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3297">Allowed From</span></span>

<span data-ttu-id="47325-3298">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3298">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3299">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3299">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_directory_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the directory was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="47325-3300">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3300">See Also</span></span>

- <span data-ttu-id="47325-3301">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-3301">fx_directory_attributes_read</span></span>
- <span data-ttu-id="47325-3302">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-3302">fx_directory_attributes_set</span></span>
- <span data-ttu-id="47325-3303">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-3303">fx_directory_create</span></span>
- <span data-ttu-id="47325-3304">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="47325-3304">fx_directory_default_get</span></span>
- <span data-ttu-id="47325-3305">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="47325-3305">fx_directory_default_set</span></span>
- <span data-ttu-id="47325-3306">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="47325-3306">fx_directory_delete</span></span>
- <span data-ttu-id="47325-3307">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-3307">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="47325-3308">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-3308">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="47325-3309">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="47325-3309">fx_directory_information_get</span></span>
- <span data-ttu-id="47325-3310">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="47325-3310">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="47325-3311">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="47325-3311">fx_directory_local_path_get</span></span>
- <span data-ttu-id="47325-3312">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="47325-3312">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="47325-3313">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="47325-3313">fx_directory_local_path_set</span></span>
- <span data-ttu-id="47325-3314">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3314">fx_directory_long_name_get</span></span>
- <span data-ttu-id="47325-3315">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="47325-3315">fx_directory_name_test</span></span>
- <span data-ttu-id="47325-3316">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-3316">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="47325-3317">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="47325-3317">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="47325-3318">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3318">fx_directory_rename</span></span>
- <span data-ttu-id="47325-3319">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3319">fx_directory_short_name_get</span></span>
- <span data-ttu-id="47325-3320">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="47325-3320">fx_unicode_directory_create</span></span>

## <a name="fx_unicode_file_create"></a><span data-ttu-id="47325-3321">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3321">fx_unicode_file_create</span></span>

<span data-ttu-id="47325-3322">유니코드 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3322">Creates a Unicode file</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3323">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3323">Prototype</span></span>

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="47325-3324">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3324">Description</span></span>

<span data-ttu-id="47325-3325">이 서비스는 현재 기본 디렉터리에 유니코드 이름이 지정된 파일을 만듭니다. 유니코드 원본 이름 매개 변수에는 경로 정보가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3325">This service creates a Unicode-named file in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="47325-3326">성공하면 서비스에서 새로 만든 유니코드 파일의 짧은 이름(8.3 형식)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3326">If successful, the short name (8.3 format) of the newly created Unicode file is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="47325-3327">유니코드 파일에 대한 모든 작업(열기, 쓰기, 읽기, 닫기 등)은 표준 FileX 파일 서비스에 반환된 짧은 이름(8.3 형식)을 제공하여 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3327">*All operations on the Unicode file (opening, writing, reading, closing, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX file services.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3328">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3328">Input Parameters</span></span>


- <span data-ttu-id="47325-3329">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3329">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-3330">**source_unicode_name**: 새 파일의 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3330">**source_unicode_name**: Pointer to the Unicode name for the new file.</span></span>
- <span data-ttu-id="47325-3331">**source_unicode_length**: 유니코드 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3331">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="47325-3332">**short_name**: 새 유니코드 파일의 짧은 이름(8.3 형식) 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3332">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3333">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3333">Return Values</span></span>

- <span data-ttu-id="47325-3334">**FX_SUCCESS**(0x00) 파일 만들기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3334">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="47325-3335">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3335">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-3336">**FX_ALREADY_CREATED**(0x0B) 지정된 파일이 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3336">**FX_ALREADY_CREATED** (0x0B) Specified file already exists.</span></span>
- <span data-ttu-id="47325-3337">**FX_NO_MORE_SPACE**(0x0A) 새 파일 항목의 미디어에 사용 가능한 클러스터가 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3337">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new file entry.</span></span>
- <span data-ttu-id="47325-3338">**FX_NOT_IMPLEMENTED**(0x22) exFAT 파일 시스템을 위해 서비스가 구현되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3338">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="47325-3339">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3339">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-3340">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3340">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="47325-3341">**FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3341">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="47325-3342">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3342">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3343">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3343">Allowed From</span></span>

<span data-ttu-id="47325-3344">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3344">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3345">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3345">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Create a Unicode file with the name contained in "my_unicode_name". */

length = fx_unicode_file_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode file is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="47325-3346">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3346">See Also</span></span>

- <span data-ttu-id="47325-3347">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3347">fx_file_allocate</span></span>
- <span data-ttu-id="47325-3348">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-3348">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-3349">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-3349">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-3350">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3350">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3351">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-3351">fx_file_close</span></span>
- <span data-ttu-id="47325-3352">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3352">fx_file_create</span></span>
- <span data-ttu-id="47325-3353">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3353">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-3354">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-3354">fx_file_delete</span></span>
- <span data-ttu-id="47325-3355">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3355">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-3356">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3356">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3357">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3357">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-3358">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3358">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-3359">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3359">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-3360">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3360">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-3361">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-3361">fx_file_open</span></span>
- <span data-ttu-id="47325-3362">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-3362">fx_file_read</span></span>
- <span data-ttu-id="47325-3363">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3363">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-3364">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3364">fx_file_rename</span></span>
- <span data-ttu-id="47325-3365">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3365">fx_file_seek</span></span>
- <span data-ttu-id="47325-3366">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3366">fx_file_truncate</span></span>
- <span data-ttu-id="47325-3367">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3367">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-3368">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-3368">fx_file_write</span></span>
- <span data-ttu-id="47325-3369">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3369">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-3370">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3370">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-3371">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3371">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-3372">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3372">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_file_rename"></a><span data-ttu-id="47325-3373">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3373">fx_unicode_file_rename</span></span>

<span data-ttu-id="47325-3374">유니코드 문자열을 사용하여 파일 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3374">Renames a file using unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3375">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3375">Prototype</span></span>

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a><span data-ttu-id="47325-3376">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3376">Description</span></span>

<span data-ttu-id="47325-3377">이 서비스는 유니코드 이름이 지정된 파일 이름을 현재 기본 디렉터리의 지정된 새 유니코드 이름으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3377">This service changes a Unicode-named file name to specified new Unicode name in current default directory.</span></span> <span data-ttu-id="47325-3378">유니코드 이름 매개 변수에는 경로 정보가 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3378">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-3379">이 서비스는 exFAT 미디어에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3379">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3380">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3380">Input Parameters</span></span>

- <span data-ttu-id="47325-3381">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3381">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-3382">**old_unicode_name**: 현재 파일의 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3382">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="47325-3383">**old_unicode_name_length**: 현재 유니코드 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3383">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="47325-3384">**new_unicode_name**: 새 유니코드 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3384">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="47325-3385">**new_unicode_name_length**: 새 유니코드 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3385">**new_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="47325-3386">**new_short_name**: 이름이 바뀐 유니코드 파일의 짧은 이름(8.3 형식)의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3386">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3387">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3387">Return Values</span></span>


- <span data-ttu-id="47325-3388">**FX_SUCCESS**(0x00) 미디어 열기에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3388">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="47325-3389">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3389">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-3390">**FX_ALREADY_CREATED**(0x0B) 지정된 파일 이름이 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3390">**FX_ALREADY_CREATED** (0x0B) Specified file name already exists.</span></span>
- <span data-ttu-id="47325-3391">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3391">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-3392">**FX_PTR_ERROR**(0x18) 하나 이상의 포인터가 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3392">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="47325-3393">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3393">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="47325-3394">**FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3394">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3395">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3395">Allowed From</span></span>

<span data-ttu-id="47325-3396">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3396">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3397">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3397">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_file_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the file name was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="47325-3398">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3398">See Also</span></span>

- <span data-ttu-id="47325-3399">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3399">fx_file_allocate</span></span>
- <span data-ttu-id="47325-3400">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-3400">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-3401">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-3401">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-3402">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3402">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3403">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-3403">fx_file_close</span></span>
- <span data-ttu-id="47325-3404">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3404">fx_file_create</span></span>
- <span data-ttu-id="47325-3405">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3405">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-3406">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-3406">fx_file_delete</span></span>
- <span data-ttu-id="47325-3407">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3407">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-3408">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3408">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3409">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3409">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-3410">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3410">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-3411">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3411">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-3412">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3412">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-3413">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-3413">fx_file_open</span></span>
- <span data-ttu-id="47325-3414">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-3414">fx_file_read</span></span>
- <span data-ttu-id="47325-3415">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3415">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-3416">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3416">fx_file_rename</span></span>
- <span data-ttu-id="47325-3417">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3417">fx_file_seek</span></span>
- <span data-ttu-id="47325-3418">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3418">fx_file_truncate</span></span>
- <span data-ttu-id="47325-3419">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3419">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-3420">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-3420">fx_file_write</span></span>
- <span data-ttu-id="47325-3421">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3421">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-3422">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3422">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-3423">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3423">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-3424">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3424">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get"></a><span data-ttu-id="47325-3425">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="47325-3425">fx_unicode_length_get</span></span>

<span data-ttu-id="47325-3426">유니코드 이름의 길이를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3426">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3427">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3427">Prototype</span></span>

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a><span data-ttu-id="47325-3428">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3428">Description</span></span>

<span data-ttu-id="47325-3429">이 서비스는 제공된 유니코드 이름의 길이를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3429">This service determines the length of the supplied Unicode name.</span></span> <span data-ttu-id="47325-3430">유니코드 문자는 2바이트로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3430">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="47325-3431">유니코드 이름은 두 개의 NULL 바이트(0 값은 2바이트)로 끝나는 일련의 2바이트 유니코드 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3431">A Unicode name is a series of two byte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3432">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3432">Input Parameters</span></span>

<span data-ttu-id="47325-3433">**unicode_name**: 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3433">**unicode_name**: Pointer to Unicode name.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3434">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3434">Return Values</span></span>

<span data-ttu-id="47325-3435">**length**: 유니코드 이름의 길이입니다(이름의 유니코드 문자 수).</span><span class="sxs-lookup"><span data-stu-id="47325-3435">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3436">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3436">Allowed From</span></span>

<span data-ttu-id="47325-3437">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3438">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3438">Example</span></span>

```c
UCHAR     my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                           0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                           0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                           0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                           0x63,0x00, 0x00,0x00};

UINT     length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get(my_unicode_name);

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="47325-3439">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3439">See Also</span></span>

- <span data-ttu-id="47325-3440">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3440">fx_file_allocate</span></span>
- <span data-ttu-id="47325-3441">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-3441">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-3442">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-3442">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-3443">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3443">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3444">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-3444">fx_file_close</span></span>
- <span data-ttu-id="47325-3445">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3445">fx_file_create</span></span>
- <span data-ttu-id="47325-3446">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3446">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-3447">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-3447">fx_file_delete</span></span>
- <span data-ttu-id="47325-3448">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3448">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-3449">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3449">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3450">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3450">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-3451">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3451">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-3452">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3452">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-3453">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3453">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-3454">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-3454">fx_file_open</span></span>
- <span data-ttu-id="47325-3455">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-3455">fx_file_read</span></span>
- <span data-ttu-id="47325-3456">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3456">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-3457">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3457">fx_file_rename</span></span>
- <span data-ttu-id="47325-3458">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3458">fx_file_seek</span></span>
- <span data-ttu-id="47325-3459">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3459">fx_file_truncate</span></span>
- <span data-ttu-id="47325-3460">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3460">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-3461">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-3461">fx_file_write</span></span>
- <span data-ttu-id="47325-3462">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3462">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-3463">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3463">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-3464">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3464">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-3465">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3465">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-3466">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3466">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get_extended"></a><span data-ttu-id="47325-3467">fx_unicode_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="47325-3467">fx_unicode_length_get_extended</span></span>

<span data-ttu-id="47325-3468">유니코드 이름의 길이를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3468">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3469">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3469">Prototype</span></span>

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a><span data-ttu-id="47325-3470">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3470">Description</span></span>

<span data-ttu-id="47325-3471">이 서비스는 제공된 유니코드 이름의 길이를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3471">This service gets the length of the supplied Unicode name.</span></span> <span data-ttu-id="47325-3472">유니코드 문자는 2바이트로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3472">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="47325-3473">유니코드 이름은 두 개의 NULL 바이트(0 값은 2바이트)로 끝나는 일련의 2바이트 유니코드 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3473">A Unicode name is a series of twobyte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-3474">이 서비스는 호출자가 NULL 문자 두 개를 비롯하여 **unicode_name** 버퍼의 크기를 전달한다는 점을 제외하면 **fx_unicode_length_get()** 과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3474">*This service is identical to **fx_unicode_length_get()** except the caller passes in the size of the **unicode_name** buffer, including the two NULL characters.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3475">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3475">Input Parameters</span></span>

- <span data-ttu-id="47325-3476">**unicode_name**: 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3476">**unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="47325-3477">**buffer_length**: 유니코드 이름 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3477">**buffer_length**: Size of Unicode name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3478">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3478">Return Values</span></span>

<span data-ttu-id="47325-3479">**length**: 유니코드 이름의 길이입니다(이름의 유니코드 문자 수).</span><span class="sxs-lookup"><span data-stu-id="47325-3479">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3480">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3480">Allowed From</span></span>

<span data-ttu-id="47325-3481">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3481">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3482">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3482">Example</span></span>

```c
UCHAR         my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                 0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                 0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                 0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                 0x63,0x00, 0x00,0x00};

UINT         length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get_extended(my_unicode_name, sizeof(my_unicode_name));

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="47325-3483">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3483">See Also</span></span>

- <span data-ttu-id="47325-3484">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3484">fx_file_allocate</span></span>
- <span data-ttu-id="47325-3485">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-3485">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-3486">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-3486">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-3487">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3487">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3488">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-3488">fx_file_close</span></span>
- <span data-ttu-id="47325-3489">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3489">fx_file_create</span></span>
- <span data-ttu-id="47325-3490">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3490">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-3491">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-3491">fx_file_delete</span></span>
- <span data-ttu-id="47325-3492">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3492">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-3493">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3493">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3494">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3494">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-3495">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3495">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-3496">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3496">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-3497">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3497">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-3498">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-3498">fx_file_open</span></span>
- <span data-ttu-id="47325-3499">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-3499">fx_file_read</span></span>
- <span data-ttu-id="47325-3500">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3500">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-3501">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3501">fx_file_rename</span></span>
- <span data-ttu-id="47325-3502">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3502">fx_file_seek</span></span>
- <span data-ttu-id="47325-3503">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3503">fx_file_truncate</span></span>
- <span data-ttu-id="47325-3504">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3504">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-3505">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-3505">fx_file_write</span></span>
- <span data-ttu-id="47325-3506">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3506">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-3507">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3507">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-3508">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3508">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-3509">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3509">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-3510">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3510">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get"></a><span data-ttu-id="47325-3511">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3511">fx_unicode_name_get</span></span>

<span data-ttu-id="47325-3512">짧은 이름에서 유니코드 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3512">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3513">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3513">Prototype</span></span>

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a><span data-ttu-id="47325-3514">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3514">Description</span></span>

<span data-ttu-id="47325-3515">이 서비스는 현재 기본 디렉터리 내에서 제공된 짧은 이름(8.3 형식)과 연결된 유니코드 이름을 검색합니다. 짧은 이름 매개 변수에는 경로 정보가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3515">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="47325-3516">성공하면 서비스에서 짧은 이름과 연결된 유니코드 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3516">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-3517">이 서비스를 사용하여 파일과 하위 디렉터리의 유니코드 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3517">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3518">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3518">Input Parameters</span></span>

- <span data-ttu-id="47325-3519">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3519">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-3520">**short_name** 짧은 이름(8.3 형식)에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3520">**short_name** Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="47325-3521">**destination_unicode_name**: 제공된 짧은 이름과 연결된 유니코드 이름의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3521">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="47325-3522">**destination_unicode_length**: 반환된 유니코드 이름 길이에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3522">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3523">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3523">Return Values</span></span>

- <span data-ttu-id="47325-3524">**FX_SUCCESS**(0x00) 유니코드 이름 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3524">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="47325-3525">**FX_FAT_READ_ERROR**(0x03) FAT 테이블을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3525">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="47325-3526">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3526">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="47325-3527">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3527">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-3528">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3528">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-3529">**FX_NOT_FOUND**(0x04) 짧은 이름을 찾을 수 없거나 유니코드 대상 크기가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3529">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="47325-3530">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3530">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-3531">**FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3531">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="47325-3532">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3532">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3533">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3533">Allowed From</span></span>

<span data-ttu-id="47325-3534">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3534">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3535">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3535">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_unicode_name[256*2];
ULONG                 unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the
    number of maximum characters in the name. */

length = fx_unicode_name_get(&ram_disk, "ABC0~111.TXT", my_unicode_name, unicode_name_length);

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="47325-3536">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3536">See Also</span></span>

- <span data-ttu-id="47325-3537">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3537">fx_file_allocate</span></span>
- <span data-ttu-id="47325-3538">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-3538">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-3539">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-3539">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-3540">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3540">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3541">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-3541">fx_file_close</span></span>
- <span data-ttu-id="47325-3542">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3542">fx_file_create</span></span>
- <span data-ttu-id="47325-3543">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3543">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-3544">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-3544">fx_file_delete</span></span>
- <span data-ttu-id="47325-3545">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3545">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-3546">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3546">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3547">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3547">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-3548">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3548">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-3549">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3549">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-3550">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3550">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-3551">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-3551">fx_file_open</span></span>
- <span data-ttu-id="47325-3552">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-3552">fx_file_read</span></span>
- <span data-ttu-id="47325-3553">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3553">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-3554">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3554">fx_file_rename</span></span>
- <span data-ttu-id="47325-3555">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3555">fx_file_seek</span></span>
- <span data-ttu-id="47325-3556">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3556">fx_file_truncate</span></span>
- <span data-ttu-id="47325-3557">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3557">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-3558">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-3558">fx_file_write</span></span>
- <span data-ttu-id="47325-3559">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3559">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-3560">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3560">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-3561">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3561">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-3562">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3562">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get_extended"></a><span data-ttu-id="47325-3563">fx_unicode_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="47325-3563">fx_unicode_name_get_extended</span></span>

<span data-ttu-id="47325-3564">짧은 이름에서 유니코드 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3564">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3565">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3565">Prototype</span></span>

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a><span data-ttu-id="47325-3566">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3566">Description</span></span>

<span data-ttu-id="47325-3567">이 서비스는 현재 기본 디렉터리 내에서 제공된 짧은 이름(8.3 형식)과 연결된 유니코드 이름을 검색합니다. 짧은 이름 매개 변수에는 경로 정보가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3567">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="47325-3568">성공하면 서비스에서 짧은 이름과 연결된 유니코드 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3568">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-3569">\*이 서비스는 호출자가 대상 유니코드 버퍼의 크기를 입력 인수로 제공한다는 점을 제외하면 \***fx_unicode_name_get** 과 동일합니다. 따라서 서비스가 대상 유니코드 버퍼를 덮어쓰지 않음을 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3569">\*This service is identical to \***fx_unicode_name_get**_, except the caller supplies the size of the destination Unicode buffer as an input argument. This allows the service to guarantee that it will not overwrite the destination Unicode buffer_</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-3570">이 서비스를 사용하여 파일과 하위 디렉터리의 유니코드 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3570">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3571">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3571">Input Parameters</span></span>

- <span data-ttu-id="47325-3572">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3572">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-3573">**short_name**: 짧은 이름(8.3 형식)에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3573">**short_name**: Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="47325-3574">**destination_unicode_name**: 제공된 짧은 이름과 연결된 유니코드 이름의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3574">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="47325-3575">**destination_unicode_length**: 반환된 유니코드 이름 길이에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3575">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>
- <span data-ttu-id="47325-3576">**unicode_name_buffer_length**: 유니코드 이름 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3576">**unicode_name_buffer_length**: Size of the Unicode name buffer.</span></span> <span data-ttu-id="47325-3577">참고: 추가 바이트를 만드는 NULL 종결자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3577">Note: A NULL terminator is required, which makes an extra byte.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3578">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3578">Return Values</span></span>

- <span data-ttu-id="47325-3579">**FX_SUCCESS**(0x00) 유니코드 이름 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3579">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="47325-3580">**FX_FAT_READ_ERROR**(0x03) FAT 테이블을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3580">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="47325-3581">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3581">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="47325-3582">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3582">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-3583">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3583">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-3584">**FX_NOT_FOUND**(0x04) 짧은 이름을 찾을 수 없거나 유니코드 대상 크기가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3584">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="47325-3585">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3585">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-3586">**FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3586">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="47325-3587">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3587">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3588">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3588">Allowed From</span></span>

<span data-ttu-id="47325-3589">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3589">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3590">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3590">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_unicode_name[256*2];
ULONG             unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the number of maximum characters in the name. */

length = fx_unicode_name_get_extended(&ram_disk, "ABC0~111.TXT",
    my_unicode_name,&unicode_name_length, sizeof(ny_unicode_name));

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="47325-3591">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3591">See Also</span></span>

- <span data-ttu-id="47325-3592">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3592">fx_file_allocate</span></span>
- <span data-ttu-id="47325-3593">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-3593">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-3594">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-3594">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-3595">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3595">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3596">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-3596">fx_file_close</span></span>
- <span data-ttu-id="47325-3597">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3597">fx_file_create</span></span>
- <span data-ttu-id="47325-3598">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3598">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-3599">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-3599">fx_file_delete</span></span>
- <span data-ttu-id="47325-3600">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3600">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-3601">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3601">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3602">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3602">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-3603">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3603">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-3604">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3604">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-3605">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3605">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-3606">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-3606">fx_file_open</span></span>
- <span data-ttu-id="47325-3607">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-3607">fx_file_read</span></span>
- <span data-ttu-id="47325-3608">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3608">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-3609">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3609">fx_file_rename</span></span>
- <span data-ttu-id="47325-3610">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3610">fx_file_seek</span></span>
- <span data-ttu-id="47325-3611">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3611">fx_file_truncate</span></span>
- <span data-ttu-id="47325-3612">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3612">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-3613">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-3613">fx_file_write</span></span>
- <span data-ttu-id="47325-3614">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3614">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-3615">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3615">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-3616">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3616">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-3617">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3617">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_short_name_get"></a><span data-ttu-id="47325-3618">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3618">fx_unicode_short_name_get</span></span>

<span data-ttu-id="47325-3619">유니코드 이름에서 짧은 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3619">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3620">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3620">Prototype</span></span>

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

<span data-ttu-id="47325-3621">이 서비스는 현재 기본 디렉터리 내에서 유니코드 이름과 연결된 짧은 이름(8.3 형식)을 검색합니다. 유니코드 이름 매개 변수에는 경로 정보가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3621">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="47325-3622">성공하면 서비스에서 유니코드 이름과 연결된 짧은 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3622">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-3623">이 서비스를 사용하여 파일과 하위 디렉터리의 짧은 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3623">*This service can be used to get short names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3624">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3624">Input Parameters</span></span>

- <span data-ttu-id="47325-3625">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3625">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-3626">**source_unicode_name**: 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3626">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="47325-3627">**source_unicode_length**: 유니코드 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3627">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="47325-3628">**destination_short_name**: 짧은 이름(8.3 형식)의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3628">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="47325-3629">크기는 13바이트 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3629">This must be at least 13 bytes in size.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3630">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3630">Return Values</span></span>

- <span data-ttu-id="47325-3631">**FX_SUCCESS**(0x00) 짧은 이름 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3631">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="47325-3632">**FX_FAT_READ_ERROR**(0x03) FAT 테이블을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3632">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="47325-3633">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3633">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="47325-3634">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3634">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-3635">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3635">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-3636">**FX_NOT_FOUND**(0x04) 유니코드 이름을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3636">**FX_NOT_FOUND** (0x04)    Unicode name was not found.</span></span>
- <span data-ttu-id="47325-3637">**FX_NOT_IMPLEMENTED**(0x22) exFAT 파일 시스템을 위해 서비스가 구현되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3637">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="47325-3638">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3638">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-3639">**FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3639">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="47325-3640">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3640">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3641">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3641">Allowed From</span></span>

<span data-ttu-id="47325-3642">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3642">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3643">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3643">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="47325-3644">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3644">See Also</span></span>

- <span data-ttu-id="47325-3645">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3645">fx_file_allocate</span></span>
- <span data-ttu-id="47325-3646">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-3646">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-3647">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-3647">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-3648">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3648">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3649">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-3649">fx_file_close</span></span>
- <span data-ttu-id="47325-3650">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3650">fx_file_create</span></span>
- <span data-ttu-id="47325-3651">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3651">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-3652">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-3652">fx_file_delete</span></span>
- <span data-ttu-id="47325-3653">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3653">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-3654">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3654">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3655">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3655">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-3656">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3656">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-3657">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3657">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-3658">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3658">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-3659">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-3659">fx_file_open</span></span>
- <span data-ttu-id="47325-3660">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-3660">fx_file_read</span></span>
- <span data-ttu-id="47325-3661">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3661">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-3662">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3662">fx_file_rename</span></span>
- <span data-ttu-id="47325-3663">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3663">fx_file_seek</span></span>
- <span data-ttu-id="47325-3664">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3664">fx_file_truncate</span></span>
- <span data-ttu-id="47325-3665">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3665">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-3666">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-3666">fx_file_write</span></span>
- <span data-ttu-id="47325-3667">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3667">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-3668">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3668">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-3669">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3669">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-3670">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3670">fx_unicode_name_get</span></span>

## <a name="fx_unicode_short_name_get_extended"></a><span data-ttu-id="47325-3671">fx_unicode_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="47325-3671">fx_unicode_short_name_get_extended</span></span>

<span data-ttu-id="47325-3672">유니코드 이름에서 짧은 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3672">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="47325-3673">프로토타입</span><span class="sxs-lookup"><span data-stu-id="47325-3673">Prototype</span></span>

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="47325-3674">Description</span><span class="sxs-lookup"><span data-stu-id="47325-3674">Description</span></span>

<span data-ttu-id="47325-3675">이 서비스는 현재 기본 디렉터리 내에서 유니코드 이름과 연결된 짧은 이름(8.3 형식)을 검색합니다. 유니코드 이름 매개 변수에는 경로 정보가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3675">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="47325-3676">성공하면 서비스에서 유니코드 이름과 연결된 짧은 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3676">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47325-3677">이 서비스는 호출자가 대상 버퍼의 크기를 입력 인수로 제공한다는 점을 제외하고 **fx_unicode_short_name_get()** 과 동일합니다. 따라서 서비스가 짧은 이름이 대상 버퍼를 초과하지 않도록 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3677">*This service is identical to **fx_unicode_short_name_get()**, except the caller supplies the size of the destination buffer as an input argument. This allows the service to guarantee the short name does not exceed the destination buffer.*</span></span>

<span data-ttu-id="47325-3678">이 서비스를 사용하여 파일과 하위 디렉터리의 짧은 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3678">*This service can be used to get short names for both files and subdirectories*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="47325-3679">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="47325-3679">Input Parameters</span></span>

- <span data-ttu-id="47325-3680">**media_ptr**: 미디어 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3680">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="47325-3681">**source_unicode_name**: 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3681">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="47325-3682">**source_unicode_length**: 유니코드 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3682">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="47325-3683">**destination_short_name**: 짧은 이름(8.3 형식)의 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3683">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="47325-3684">크기는 13바이트 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3684">This must be at least 13 bytes in size.</span></span>
- <span data-ttu-id="47325-3685">**short_name_buffer_length**: 대상 버퍼의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3685">**short_name_buffer_length**: Size of the destination buffer.</span></span> <span data-ttu-id="47325-3686">버퍼 크기는 최소한 14바이트 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3686">The buffer size must be at least 14 bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="47325-3687">반환 값</span><span class="sxs-lookup"><span data-stu-id="47325-3687">Return Values</span></span>

- <span data-ttu-id="47325-3688">**FX_SUCCESS**(0x00) 짧은 이름 검색에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3688">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="47325-3689">**FX_FAT_READ_ERROR**(0x03) FAT 테이블을 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3689">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="47325-3690">**FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3690">**FX_FILE_CORRUPT** (0x08)    File is corrupted</span></span>
- <span data-ttu-id="47325-3691">**FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3691">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="47325-3692">**FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3692">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="47325-3693">**FX_NOT_FOUND**(0x04) 유니코드 이름을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3693">**FX_NOT_FOUND** (0x04) Unicode name was not found.</span></span>
- <span data-ttu-id="47325-3694">**FX_NOT_IMPLEMENTED**(0x22) exFAT 파일 시스템을 위해 서비스가 구현되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3694">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="47325-3695">**FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3695">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="47325-3696">**FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3696">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="47325-3697">**FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="47325-3697">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="47325-3698">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="47325-3698">Allowed From</span></span>

<span data-ttu-id="47325-3699">스레드</span><span class="sxs-lookup"><span data-stu-id="47325-3699">Threads</span></span>

### <a name="example"></a><span data-ttu-id="47325-3700">예제</span><span class="sxs-lookup"><span data-stu-id="47325-3700">Example</span></span>

```c
#define         SHORT_NAME_BUFFER_SIZE 13
FX_MEDIA         ram_disk;
UCHAR             my_short_name[SHORT_NAME_BUFFER_SIZE];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get_extended(&ram_disk,
    my_unicode_name, 17, my_short_name,SHORT_NAME_BUFFER_SIZE);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="47325-3701">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47325-3701">See Also</span></span>

- <span data-ttu-id="47325-3702">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3702">fx_file_allocate</span></span>
- <span data-ttu-id="47325-3703">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="47325-3703">fx_file_attributes_read</span></span>
- <span data-ttu-id="47325-3704">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="47325-3704">fx_file_attributes_set</span></span>
- <span data-ttu-id="47325-3705">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3705">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3706">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="47325-3706">fx_file_close</span></span>
- <span data-ttu-id="47325-3707">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3707">fx_file_create</span></span>
- <span data-ttu-id="47325-3708">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="47325-3708">fx_file_date_time_set</span></span>
- <span data-ttu-id="47325-3709">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="47325-3709">fx_file_delete</span></span>
- <span data-ttu-id="47325-3710">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3710">fx_file_extended_allocate</span></span>
- <span data-ttu-id="47325-3711">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="47325-3711">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="47325-3712">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3712">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="47325-3713">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3713">fx_file_extended_seek</span></span>
- <span data-ttu-id="47325-3714">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3714">fx_file_extended_truncate</span></span>
- <span data-ttu-id="47325-3715">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3715">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="47325-3716">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="47325-3716">fx_file_open</span></span>
- <span data-ttu-id="47325-3717">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="47325-3717">fx_file_read</span></span>
- <span data-ttu-id="47325-3718">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3718">fx_file_relative_seek</span></span>
- <span data-ttu-id="47325-3719">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3719">fx_file_rename</span></span>
- <span data-ttu-id="47325-3720">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="47325-3720">fx_file_seek</span></span>
- <span data-ttu-id="47325-3721">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="47325-3721">fx_file_truncate</span></span>
- <span data-ttu-id="47325-3722">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="47325-3722">fx_file_truncate_release</span></span>
- <span data-ttu-id="47325-3723">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="47325-3723">fx_file_write</span></span>
- <span data-ttu-id="47325-3724">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="47325-3724">fx_file_write_notify_set</span></span>
- <span data-ttu-id="47325-3725">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="47325-3725">fx_unicode_file_create</span></span>
- <span data-ttu-id="47325-3726">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="47325-3726">fx_unicode_file_rename</span></span>
- <span data-ttu-id="47325-3727">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3727">fx_unicode_name_get</span></span>
- <span data-ttu-id="47325-3728">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="47325-3728">fx_unicode_short_name_get</span></span>
