---
title: 7장 - Azure RTOS FileX 추적 이벤트
description: 이 장에서는 Azure RTOS FileX 이벤트에 대해 설명합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: c3cbc945e33b87b6759c56ec1429d6bf57259bd9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812307"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a><span data-ttu-id="c19de-103">7장 - Azure RTOS FileX 추적 이벤트</span><span class="sxs-lookup"><span data-stu-id="c19de-103">Chapter 7 - Azure RTOS FileX trace events</span></span>

<span data-ttu-id="c19de-104">이 장에서는 Azure RTOS FileX 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-104">This chapter contains a description of the Azure RTOS FileX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="c19de-105">이벤트 및 아이콘 목록</span><span class="sxs-lookup"><span data-stu-id="c19de-105">List of Events and Icons</span></span>

<span data-ttu-id="c19de-106">**다음은 TraceX에 의해 표시되는 FileX 이벤트 목록입니다.**</span><span class="sxs-lookup"><span data-stu-id="c19de-106">**The following is a list of FileX events displayed by TraceX.**</span></span>

<span data-ttu-id="c19de-107">다음에서는 각 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-107">The following describes each event:</span></span>

| <span data-ttu-id="c19de-108">**아이콘**</span><span class="sxs-lookup"><span data-stu-id="c19de-108">**Icon**</span></span>                         | <span data-ttu-id="c19de-109">**의미**</span><span class="sxs-lookup"><span data-stu-id="c19de-109">**Meaning**</span></span>                               |
| -------------------------------- | ----------------------------------------- |
| ![내부 논리 섹터 캐시 누락 아이콘](./media/user-guide/fx-events/image1.png)    | <span data-ttu-id="c19de-111">내부 논리 섹터 캐시 누락</span><span class="sxs-lookup"><span data-stu-id="c19de-111">Internal Logical Sector Cache Miss</span></span> |
| ![내부 디렉터리 캐시 누락 아이콘](./media/user-guide/fx-events/image2.png)    | <span data-ttu-id="c19de-113">내부 디렉터리 캐시 누락</span><span class="sxs-lookup"><span data-stu-id="c19de-113">Internal Directory Cache Miss</span></span> |
| ![내부 미디어 플러시 아이콘](./media/user-guide/fx-events/image3.png)    | <span data-ttu-id="c19de-115">내부 미디어 플러시</span><span class="sxs-lookup"><span data-stu-id="c19de-115">Internal Media Flush</span></span> |
| ![내부 디렉터리 항목 읽기 아이콘](./media/user-guide/fx-events/image4.png)    | <span data-ttu-id="c19de-117">내부 디렉터리 항목 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-117">Internal Directory Entry Read</span></span> |
| ![내부 디렉터리 항목 쓰기 아이콘](./media/user-guide/fx-events/image5.png)    | <span data-ttu-id="c19de-119">내부 디렉터리 항목 쓰기</span><span class="sxs-lookup"><span data-stu-id="c19de-119">Internal Directory Entry Write</span></span> |
| ![내부 I/O 드라이버 읽기 아이콘](./media/user-guide/fx-events/image6.png)    | <span data-ttu-id="c19de-121">내부 I/O 드라이버 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-121">Internal I/O Driver Read</span></span> |
| ![내부 I/O 드라이버 쓰기 아이콘](./media/user-guide/fx-events/image7.png)    | <span data-ttu-id="c19de-123">내부 I/O 드라이버 쓰기</span><span class="sxs-lookup"><span data-stu-id="c19de-123">Internal I/O Driver Write</span></span> |
| ![내부 I/O 드라이버 플러시 아이콘](./media/user-guide/fx-events/image8.png)    | <span data-ttu-id="c19de-125">내부 I/O 드라이버 플러시</span><span class="sxs-lookup"><span data-stu-id="c19de-125">Internal I/O Driver Flush</span></span> |
| ![내부 I/O 드라이버 중단 아이콘](./media/user-guide/fx-events/image9.png)    | <span data-ttu-id="c19de-127">내부 I/O 드라이버 중단</span><span class="sxs-lookup"><span data-stu-id="c19de-127">Internal I/O Driver Abort</span></span> |
| ![내부 I/O 드라이버 초기화 아이콘](./media/user-guide/fx-events/image10.png)    | <span data-ttu-id="c19de-129">내부 I/O 드라이버 초기화</span><span class="sxs-lookup"><span data-stu-id="c19de-129">Internal I/O Driver Initialize</span></span> |
| ![내부 I/O 드라이버 부팅 읽기 아이콘](./media/user-guide/fx-events/image11.png)    | <span data-ttu-id="c19de-131">내부 I/O 드라이버 부팅 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-131">Internal I/O Driver Boot Read</span></span> |
| ![내부 I/O 드라이버 해제 섹터 아이콘](./media/user-guide/fx-events/image12.png)    | <span data-ttu-id="c19de-133">내부 I/O 드라이버 해제 섹터</span><span class="sxs-lookup"><span data-stu-id="c19de-133">Internal I/O Driver Release Sectors</span></span> |
| ![내부 I/O 드라이버 부팅 쓰기 아이콘](./media/user-guide/fx-events/image13.png)    | <span data-ttu-id="c19de-135">내부 I/O 드라이버 부팅 쓰기</span><span class="sxs-lookup"><span data-stu-id="c19de-135">Internal I/O Driver Boot Write</span></span> |
| ![내부 I/O 드라이버 초기화 취소 아이콘](./media/user-guide/fx-events/image14.png)    | <span data-ttu-id="c19de-137">내부 I/O 드라이버 초기화 취소</span><span class="sxs-lookup"><span data-stu-id="c19de-137">Internal I / O Driver Driver Un-initialize</span></span> |
| ![디렉터리 특성 읽기 아이콘](./media/user-guide/fx-events/image15.png)    | <span data-ttu-id="c19de-139">**디렉터리 특성 읽기**(*fx_directory_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="c19de-139">**Directory Attributes Read** (*fx_directory_attributes_read*)</span></span> |
| ![디렉터리 특성 설정 아이콘](./media/user-guide/fx-events/image16.png)    | <span data-ttu-id="c19de-141">**디렉터리 특성 설정**(*fx_directory_attributes_set*)</span><span class="sxs-lookup"><span data-stu-id="c19de-141">**Directory Attributes Set** (*fx_directory_attributes_set*)</span></span> |
| ![디렉터리 만들기 아이콘](./media/user-guide/fx-events/image17.png)    | <span data-ttu-id="c19de-143">**디렉터리 만들기**(*fx_directory_create*)</span><span class="sxs-lookup"><span data-stu-id="c19de-143">**Directory Create** (*fx_directory_create*)</span></span> |
| ![디렉터리 기본값 가져오기 아이콘](./media/user-guide/fx-events/image18.png)    | <span data-ttu-id="c19de-145">**디렉터리 기본값 가져오기**(*fx_directory_default_get*)</span><span class="sxs-lookup"><span data-stu-id="c19de-145">**Directory Default Get** (*fx_directory_default_get*)</span></span> |
| ![디렉터리 기본값 설정 아이콘](./media/user-guide/fx-events/image19.png)    | <span data-ttu-id="c19de-147">**디렉터리 기본값 설정**(*fx_directory_default_set*)</span><span class="sxs-lookup"><span data-stu-id="c19de-147">**Directory Default Set** (*fx_directory_default_set*)</span></span> |
| ![디렉터리 삭제 아이콘](./media/user-guide/fx-events/image20.png)    | <span data-ttu-id="c19de-149">**디렉터리 삭제**(*fx_directory_delete*)</span><span class="sxs-lookup"><span data-stu-id="c19de-149">**Directory Delete** (*fx_directory_delete*)</span></span> |
| ![디렉터리의 첫 번째 항목 찾기 아이콘](./media/user-guide/fx-events/image21.png)    | <span data-ttu-id="c19de-151">**디렉터리의 첫 번째 항목 찾기**(*fx_directory_first_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="c19de-151">**Directory First Entry Find** (*fx_directory_first_entry_find*)</span></span> |
| ![디렉터리의 첫 번째 전체 항목 찾기 아이콘](./media/user-guide/fx-events/image22.png)    | <span data-ttu-id="c19de-153">**디렉터리의 첫 번째 전체 항목 찾기**(*fx_directory_first_full_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="c19de-153">**Directory First Full Entry Find** (*fx_directory_first_full_entry_find*)</span></span> |
| ![디렉터리 정보 가져오기 아이콘](./media/user-guide/fx-events/image23.png)    | <span data-ttu-id="c19de-155">**디렉터리 정보 가져오기**(*fx_directory_information_get*)</span><span class="sxs-lookup"><span data-stu-id="c19de-155">**Directory Information Get** (*fx_directory_information_get*)</span></span> |
| ![디렉터리 로컬 경로 지우기 아이콘](./media/user-guide/fx-events/image24.png)    | <span data-ttu-id="c19de-157">**디렉터리 로컬 경로 지우기**(*fx_directory_local_path_clear*)</span><span class="sxs-lookup"><span data-stu-id="c19de-157">**Directory Local Path Clear** (*fx_directory_local_path_clear*)</span></span> |
| ![디렉터리 로컬 경로 가져오기 아이콘](./media/user-guide/fx-events/image25.png)    | <span data-ttu-id="c19de-159">**디렉터리 로컬 경로 가져오기**(*fx_directory_local_path_get*)</span><span class="sxs-lookup"><span data-stu-id="c19de-159">**Directory Local Path Get** (*fx_directory_local_path_get*)</span></span> |
| ![디렉터리 로컬 경로 복원 아이콘](./media/user-guide/fx-events/image26.png)    | <span data-ttu-id="c19de-161">**디렉터리 로컬 경로 복원**(*fx_directory_local_path_restore*)</span><span class="sxs-lookup"><span data-stu-id="c19de-161">**Directory Local Path Restore** (*fx_directory_local_path_restore*)</span></span> |
| ![디렉터리 로컬 경로 설정 아이콘](./media/user-guide/fx-events/image27.png)    | <span data-ttu-id="c19de-163">**디렉터리 로컬 경로 설정**(*fx_directory_local_path_set*)</span><span class="sxs-lookup"><span data-stu-id="c19de-163">**Directory Local Path Set** (*fx_directory_local_path_set*)</span></span> |
| ![디렉터리의 긴 이름 가져오기 아이콘](./media/user-guide/fx-events/image28.png)    | <span data-ttu-id="c19de-165">**디렉터리의 긴 이름 가져오기**(*fx_directory_long_name_get*)</span><span class="sxs-lookup"><span data-stu-id="c19de-165">**Directory Long Name Get** (*fx_directory_long_name_get*)</span></span> |
| ![디렉터리 이름 테스트 아이콘](./media/user-guide/fx-events/image29.png)    | <span data-ttu-id="c19de-167">**디렉터리 이름 테스트**(*fx_directory_name_test*)</span><span class="sxs-lookup"><span data-stu-id="c19de-167">**Directory Name Test** (*fx_directory_name_test*)</span></span> |
| ![디렉터리의 다음 항목 찾기 아이콘](./media/user-guide/fx-events/image30.png)    | <span data-ttu-id="c19de-169">**디렉터리의 다음 항목 찾기**(*fx_directory_next_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="c19de-169">**Directory Next Entry Find** (*fx_directory_next_entry_find*)</span></span> |
| ![디렉터리의 다음 전체 항목 찾기 아이콘](./media/user-guide/fx-events/image31.png)    | <span data-ttu-id="c19de-171">**디렉터리의 다음 전체 항목 찾기**(*fx_directory_next_full_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="c19de-171">**Directory Next Full Entry Find** (*fx_directory_next_full_entry_find*)</span></span> |
| ![디렉터리 이름 바꾸기 아이콘](./media/user-guide/fx-events/image32.png)    | <span data-ttu-id="c19de-173">**디렉터리 이름 바꾸기**(*fx_directory_rename*)</span><span class="sxs-lookup"><span data-stu-id="c19de-173">**Directory Rename** (*fx_directory_rename*)</span></span> |
| ![디렉터리의 짧은 이름 가져오기 아이콘](./media/user-guide/fx-events/image33.png)    | <span data-ttu-id="c19de-175">**디렉터리의 짧은 이름 가져오기**(*fx_directory_short_name_get*)</span><span class="sxs-lookup"><span data-stu-id="c19de-175">**Directory Short Name Get** (*fx_directory_short_name_get*)</span></span> |
| ![파일 할당 아이콘](./media/user-guide/fx-events/image34.png)    | <span data-ttu-id="c19de-177">**파일 할당**(*fx_file_allocate*)</span><span class="sxs-lookup"><span data-stu-id="c19de-177">**File Allocate** (*fx_file_allocate*)</span></span> |
| ![파일 특성 읽기 아이콘](./media/user-guide/fx-events/image35.png)    | <span data-ttu-id="c19de-179">**파일 특성 읽기**(*fx_file_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="c19de-179">**File Attributes Read** (*fx_file_attributes_read*)</span></span> |
| ![파일 특성 설정 아이콘](./media/user-guide/fx-events/image36.png)    | <span data-ttu-id="c19de-181">**파일 특성 설정**(*fx_file_attributes_set*)</span><span class="sxs-lookup"><span data-stu-id="c19de-181">**File Attributes Set** (*fx_file_attributes_set*)</span></span> |
| ![최선의 파일 할당 아이콘](./media/user-guide/fx-events/image37.png)    | <span data-ttu-id="c19de-183">**최선의 파일 할당**(*fx_file_best_effort_allocate*)</span><span class="sxs-lookup"><span data-stu-id="c19de-183">**File Best Effort Allocate** (*fx_file_best_effort_allocate*)</span></span> |
| ![파일 닫기 아이콘](./media/user-guide/fx-events/image38.png)    | <span data-ttu-id="c19de-185">**파일 닫기**(*fx_file_close*)</span><span class="sxs-lookup"><span data-stu-id="c19de-185">**File Close** (*fx_file_close*)</span></span> |
| ![파일 만들기 아이콘](./media/user-guide/fx-events/image39.png)    | <span data-ttu-id="c19de-187">**파일 만들기**(*fx_file_create*)</span><span class="sxs-lookup"><span data-stu-id="c19de-187">**File Create** (*fx_file_create*)</span></span> |
| ![파일 날짜 시간 설정 아이콘](./media/user-guide/fx-events/image40.png)    | <span data-ttu-id="c19de-189">**파일 날짜 시간 설정**(*fx_file_date_time_set*)</span><span class="sxs-lookup"><span data-stu-id="c19de-189">**File Date Time Set** (*fx_file_date_time_set*)</span></span> |
| ![파일 삭제 아이콘](./media/user-guide/fx-events/image41.png)    | <span data-ttu-id="c19de-191">**파일 삭제**(*fx_file_delete*)</span><span class="sxs-lookup"><span data-stu-id="c19de-191">**File Delete** (*fx_file_delete*)</span></span> |
| ![파일 열기 아이콘](./media/user-guide/fx-events/image42.png)    | <span data-ttu-id="c19de-193">**파일 열기**(*fx_file_open*)</span><span class="sxs-lookup"><span data-stu-id="c19de-193">**File Open** (*fx_file_open*)</span></span> |
| ![파일 읽기 아이콘](./media/user-guide/fx-events/image43.png)    | <span data-ttu-id="c19de-195">**파일 읽기**(*fx_file_read*)</span><span class="sxs-lookup"><span data-stu-id="c19de-195">**File Read** (*fx_file_read*)</span></span> |
| ![파일 상대 검색 아이콘](./media/user-guide/fx-events/image44.png)    | <span data-ttu-id="c19de-197">**파일 상대 검색**(*fx_file_relative_seek*)</span><span class="sxs-lookup"><span data-stu-id="c19de-197">**File Relative Seek** (*fx_file_relative_seek*)</span></span> |
| ![파일 이름 바꾸기 아이콘](./media/user-guide/fx-events/image45.png)    | <span data-ttu-id="c19de-199">**파일 이름 바꾸기**(*fx_file_rename*)</span><span class="sxs-lookup"><span data-stu-id="c19de-199">**File Rename** (*fx_file_rename*)</span></span> |
| ![파일 검색 아이콘](./media/user-guide/fx-events/image46.png)    | <span data-ttu-id="c19de-201">**파일 검색**(*fx_file_seek*)</span><span class="sxs-lookup"><span data-stu-id="c19de-201">**File Seek** (*fx_file_seek*)</span></span> |
| ![파일 자르기 아이콘](./media/user-guide/fx-events/image47.png)    | <span data-ttu-id="c19de-203">**파일 자르기**(*fx_file_truncate*)</span><span class="sxs-lookup"><span data-stu-id="c19de-203">**File Truncate** (*fx_file_truncate*)</span></span> |
| ![파일 자르기 해제 아이콘](./media/user-guide/fx-events/image48.png)    | <span data-ttu-id="c19de-205">**파일 자르기 해제**(*fx_file_truncate_release*)</span><span class="sxs-lookup"><span data-stu-id="c19de-205">**File Truncate Release** (*fx_file_truncate_release*)</span></span> |
| ![파일 쓰기 아이콘](./media/user-guide/fx-events/image49.png)    | <span data-ttu-id="c19de-207">**파일 쓰기**(*fx_file_write*)</span><span class="sxs-lookup"><span data-stu-id="c19de-207">**File Write** (*fx_file_write*)</span></span> |
| ![미디어 중단 아이콘](./media/user-guide/fx-events/image50.png)    | <span data-ttu-id="c19de-209">**미디어 중단**(*fx_media_abort*)</span><span class="sxs-lookup"><span data-stu-id="c19de-209">**Media Abort** (*fx_media_abort*)</span></span> |
| ![미디어 캐시 무효화 아이콘](./media/user-guide/fx-events/image51.png)    | <span data-ttu-id="c19de-211">**미디어 캐시 무효화**(*fx_media_cache_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="c19de-211">**Media Cache Invalidate** (*fx_media_cache_invalidate*)</span></span> |
| ![미디어 검사 아이콘](./media/user-guide/fx-events/image52.png)    | <span data-ttu-id="c19de-213">**미디어 검사**(*fx_media_check*)</span><span class="sxs-lookup"><span data-stu-id="c19de-213">**Media Check** (*fx_media_check*)</span></span> |
| ![\* 미디어 닫기 아이콘](./media/user-guide/fx-events/image53.png)    | <span data-ttu-id="c19de-215">**미디어 닫기**(*fx_media_close*)</span><span class="sxs-lookup"><span data-stu-id="c19de-215">**Media Close** (*fx_media_close*)</span></span> |
| ![미디어 플러시 아이콘](./media/user-guide/fx-events/image54.png)    | <span data-ttu-id="c19de-217">**미디어 플러시**(*fx_media_flush*)</span><span class="sxs-lookup"><span data-stu-id="c19de-217">**Media Flush** (*fx_media_flush*)</span></span> |
| ![미디어 형식 아이콘](./media/user-guide/fx-events/image55.png)    | <span data-ttu-id="c19de-219">**미디어 형식**(*fx_media_format*)</span><span class="sxs-lookup"><span data-stu-id="c19de-219">**Media Format** (*fx_media_format*)</span></span> |
| ![미디어 열기 아이콘](./media/user-guide/fx-events/image56.png)    | <span data-ttu-id="c19de-221">**미디어 열기**(*fx_media_open*)</span><span class="sxs-lookup"><span data-stu-id="c19de-221">**Media Open** (*fx_media_open*)</span></span> |
| ![미디어 읽기 아이콘](./media/user-guide/fx-events/image57.png)    | <span data-ttu-id="c19de-223">**미디어 읽기**(*fx_media_read*)</span><span class="sxs-lookup"><span data-stu-id="c19de-223">**Media Read** (*fx_media_read*)</span></span> |
| ![사용 가능한 미디어 공간 아이콘](./media/user-guide/fx-events/image58.png)    | <span data-ttu-id="c19de-225">**사용 가능한 미디어 공간**(*fx_media_space_available*)</span><span class="sxs-lookup"><span data-stu-id="c19de-225">**Media Space Available** (*fx_media_space_available*)</span></span> |
| ![미디어 볼륨 가져오기 아이콘](./media/user-guide/fx-events/image59.png)    | <span data-ttu-id="c19de-227">**미디어 볼륨 가져오기**(*fx_media_volume_get*)</span><span class="sxs-lookup"><span data-stu-id="c19de-227">**Media Volume Get** (*fx_media_volume_get*)</span></span> |
| ![미디어 볼륨 설정 아이콘](./media/user-guide/fx-events/image60.png)    | <span data-ttu-id="c19de-229">**미디어 볼륨 설정**(*fx_media_volume_set*)</span><span class="sxs-lookup"><span data-stu-id="c19de-229">**Media Volume Set** (*fx_media_volume_set*)</span></span> |
| ![미디어 쓰기 아이콘](./media/user-guide/fx-events/image61.png)    | <span data-ttu-id="c19de-231">**미디어 쓰기**(*fx_media_write*)</span><span class="sxs-lookup"><span data-stu-id="c19de-231">**Media Write** (*fx_media_write*)</span></span> |
| ![시스템 날짜 가져오기 아이콘](./media/user-guide/fx-events/image62.png)    | <span data-ttu-id="c19de-233">**시스템 날짜 가져오기**(*fx_system_date_get*)</span><span class="sxs-lookup"><span data-stu-id="c19de-233">**System Date Get** (*fx_system_date_get*)</span></span> |
| ![시스템 날짜 설정 아이콘](./media/user-guide/fx-events/image63.png)    | <span data-ttu-id="c19de-235">**시스템 날짜 설정**(*fx_system_date_set*)</span><span class="sxs-lookup"><span data-stu-id="c19de-235">**System Date Set** (*fx_system_date_set*)</span></span> |
| ![시스템 초기화 아이콘](./media/user-guide/fx-events/image64.png)    | <span data-ttu-id="c19de-237">**시스템 초기화**(*fx_system_initialize*)</span><span class="sxs-lookup"><span data-stu-id="c19de-237">**System Initialize** (*fx_system_initialize*)</span></span> |
| ![시스템 시간 가져오기 아이콘](./media/user-guide/fx-events/image65.png)    | <span data-ttu-id="c19de-239">**시스템 시간 가져오기**(*fx_system_time_get*)</span><span class="sxs-lookup"><span data-stu-id="c19de-239">**System Time Get** (*fx_system_time_get*)</span></span> |
| ![시스템 시간 설정 아이콘](./media/user-guide/fx-events/image66.png)    | <span data-ttu-id="c19de-241">**시스템 시간 설정**(*fx_system_time_set*)</span><span class="sxs-lookup"><span data-stu-id="c19de-241">**System Time Set** (*fx_system_time_set*)</span></span> |
| ![유니코드 디렉터리 만들기 아이콘](./media/user-guide/fx-events/image67.png)    | <span data-ttu-id="c19de-243">**유니코드 디렉터리 만들기**(*fx_unicode_directory_create*)</span><span class="sxs-lookup"><span data-stu-id="c19de-243">**Unicode Directory Create** (*fx_unicode_directory_create*)</span></span> |
| ![유니코드 디렉터리 이름 바꾸기 아이콘](./media/user-guide/fx-events/image68.png)    | <span data-ttu-id="c19de-245">**유니코드 디렉터리 이름 바꾸기**(*fx_unicode_directory_rename*)</span><span class="sxs-lookup"><span data-stu-id="c19de-245">**Unicode Directory Rename** (*fx_unicode_directory_rename*)</span></span> |
| ![유니코드 파일 만들기 아이콘](./media/user-guide/fx-events/image69.png)    | <span data-ttu-id="c19de-247">**유니코드 파일 만들기**(*fx_unicode_file_create*)</span><span class="sxs-lookup"><span data-stu-id="c19de-247">**Unicode File Create** (*fx_unicode_file_create*)</span></span> |
| ![유니코드 파일 이름 바꾸기 아이콘](./media/user-guide/fx-events/image70.png)    | <span data-ttu-id="c19de-249">**유니코드 파일 이름 바꾸기**(*fx_unicode_file_rename*)</span><span class="sxs-lookup"><span data-stu-id="c19de-249">**Unicode File Rename** (*fx_unicode_file_rename*)</span></span> |
| ![유니코드 길이 가져오기 아이콘](./media/user-guide/fx-events/image71.png)    | <span data-ttu-id="c19de-251">**유니코드 길이 가져오기**(*fx_unicode_length_get*)</span><span class="sxs-lookup"><span data-stu-id="c19de-251">**Unicode Lenght Get** (*fx_unicode_length_get*)</span></span> |
| ![유니코드 이름 가져오기 아이콘](./media/user-guide/fx-events/image72.png)    | <span data-ttu-id="c19de-253">**유니코드 이름 가져오기**(*fx_unicode_name_get*)</span><span class="sxs-lookup"><span data-stu-id="c19de-253">**Unicode Name Get** (*fx_unicode_name_get*)</span></span> |
| ![유니코드의 짧은 이름 가져오기 아이콘](./media/user-guide/fx-events/image73.png)    | <span data-ttu-id="c19de-255">**유니코드의 짧은 이름 가져오기**(*fx_unicode_short_name_get*)</span><span class="sxs-lookup"><span data-stu-id="c19de-255">**Unicode Short Name Get** (*fx_unicode_short_name_get*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="c19de-256">이벤트 설명</span><span class="sxs-lookup"><span data-stu-id="c19de-256">Event Descriptions</span></span>

<span data-ttu-id="c19de-257">다음에서는 각 개별 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-257">The following describes each individual event.</span></span>

### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="c19de-258">내부 논리 섹터 캐시 누락</span><span class="sxs-lookup"><span data-stu-id="c19de-258">Internal Logical Sector Cache Miss</span></span> 

#### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="c19de-259">내부 논리 섹터 캐시 누락</span><span class="sxs-lookup"><span data-stu-id="c19de-259">Internal logical sector cache miss</span></span>

<span data-ttu-id="c19de-260">**아이콘** ![내부 논리 섹터 캐시 누락 아이콘](./media/user-guide/fx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-260">**Icon** ![Internal logical sector cache miss icon](./media/user-guide/fx-events/image1.png)</span></span>

<span data-ttu-id="c19de-261">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-261">**Description**</span></span>

<span data-ttu-id="c19de-262">이 이벤트는 내부 FileX 논리 섹터 캐시 누락을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-262">This event represents an internal FileX logical sector cache miss.</span></span>

<span data-ttu-id="c19de-263">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-263">**Information Fields**</span></span>

- <span data-ttu-id="c19de-264">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-264">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-265">정보 필드 2: 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-265">Info Field 2: Sector.</span></span>
- <span data-ttu-id="c19de-266">정보 필드 3: 총 누락입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-266">Info Field 3: Total misses.</span></span>
- <span data-ttu-id="c19de-267">정보 필드 4: 캐시 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-267">Info Field 4: Cache size.</span></span>

### <a name="internal-directory-cache-miss"></a><span data-ttu-id="c19de-268">내부 디렉터리 캐시 누락</span><span class="sxs-lookup"><span data-stu-id="c19de-268">Internal Directory Cache Miss</span></span>

#### <a name="internal-directory-cache-miss"></a><span data-ttu-id="c19de-269">내부 디렉터리 캐시 누락</span><span class="sxs-lookup"><span data-stu-id="c19de-269">Internal directory cache miss</span></span>

<span data-ttu-id="c19de-270">**아이콘** ![내부 디렉터리 캐시 누락 아이콘](./media/user-guide/fx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-270">**Icon** ![Internal directory cache miss icon](./media/user-guide/fx-events/image2.png)</span></span>

<span data-ttu-id="c19de-271">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-271">**Description**</span></span> 

<span data-ttu-id="c19de-272">이 이벤트는 내부 FileX 디렉터리 캐시 누락을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-272">This event represents an internal FileX directory cache miss.</span></span>

<span data-ttu-id="c19de-273">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-273">**Information Fields**</span></span>

- <span data-ttu-id="c19de-274">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-274">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-275">정보 필드 2: 총 누락입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-275">Info Field 2: Total misses.</span></span>
- <span data-ttu-id="c19de-276">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-276">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-277">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-277">Info Field 4: Not used.</span></span>

### <a name="internal-media-flush"></a><span data-ttu-id="c19de-278">내부 미디어 플러시</span><span class="sxs-lookup"><span data-stu-id="c19de-278">Internal Media Flush</span></span> 

#### <a name="internal-media-flush"></a><span data-ttu-id="c19de-279">내부 미디어 플러시</span><span class="sxs-lookup"><span data-stu-id="c19de-279">Internal media flush</span></span>

<span data-ttu-id="c19de-280">**아이콘** ![내부 미디어 플러시 아이콘](./media/user-guide/fx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-280">**Icon** ![Internal media flush icon](./media/user-guide/fx-events/image3.png)</span></span>

<span data-ttu-id="c19de-281">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-281">**Description**</span></span>

<span data-ttu-id="c19de-282">이 이벤트는 내부 FileX 미디어 플러시를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-282">This event represents an internal FileX media flush.</span></span>

<span data-ttu-id="c19de-283">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-283">**Information Fields**</span></span>

- <span data-ttu-id="c19de-284">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-284">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-285">정보 필드 2: 더티 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-285">Info Field 2: Number of dirty sectors.</span></span>
- <span data-ttu-id="c19de-286">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-286">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-287">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-287">Info Field 4: Not used.</span></span>


### <a name="internal-directory-entry-read"></a><span data-ttu-id="c19de-288">내부 디렉터리 항목 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-288">Internal Directory Entry Read</span></span> 

#### <a name="internal-directory-entry-read"></a><span data-ttu-id="c19de-289">내부 디렉터리 항목 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-289">Internal directory entry read</span></span>

<span data-ttu-id="c19de-290">**아이콘** ![내부 디렉터리 항목 읽기 아이콘](./media/user-guide/fx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-290">**Icon** ![Internal directory entry read icon](./media/user-guide/fx-events/image4.png)</span></span>

<span data-ttu-id="c19de-291">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-291">**Description**</span></span>

<span data-ttu-id="c19de-292">이 이벤트는 내부 FileX 디렉터리 항목 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-292">This event represents an internal FileX directory entry read event.</span></span>

<span data-ttu-id="c19de-293">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-293">**Information Fields**</span></span>

- <span data-ttu-id="c19de-294">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-294">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-295">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-295">Info Field 2: Not used.</span></span>
- <span data-ttu-id="c19de-296">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-296">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-297">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-297">Info Field 4: Not used.</span></span>

### <a name="internal-directory-entry-write"></a><span data-ttu-id="c19de-298">내부 디렉터리 항목 쓰기</span><span class="sxs-lookup"><span data-stu-id="c19de-298">Internal Directory Entry Write</span></span>

#### <a name="internal-directory-entry-write"></a><span data-ttu-id="c19de-299">내부 디렉터리 항목 쓰기</span><span class="sxs-lookup"><span data-stu-id="c19de-299">Internal directory entry write</span></span>

<span data-ttu-id="c19de-300">**아이콘** ![내부 디렉터리 항목 쓰기 아이콘](./media/user-guide/fx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-300">**Icon** ![Internal directory entry write icon](./media/user-guide/fx-events/image5.png)</span></span>

<span data-ttu-id="c19de-301">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-301">**Description**</span></span>

<span data-ttu-id="c19de-302">이 이벤트는 내부 FileX 디렉터리 항목 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-302">This event represents an internal FileX directory entry write event.</span></span>

<span data-ttu-id="c19de-303">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-303">**Information Fields**</span></span>

- <span data-ttu-id="c19de-304">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-304">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-305">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-305">Info Field 2: Not used.</span></span>
- <span data-ttu-id="c19de-306">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-306">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-307">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-307">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-read"></a><span data-ttu-id="c19de-308">내부 I/O 드라이버 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-308">Internal I/O Driver Read</span></span> 

#### <a name="internal-io-driver-read"></a><span data-ttu-id="c19de-309">내부 I/O 드라이버 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-309">Internal I/O driver read</span></span> 

<span data-ttu-id="c19de-310">**아이콘** ![내부 I/O 드라이버 읽기 아이콘](./media/user-guide/fx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-310">**Icon** ![Internal I / O driver read icon](./media/user-guide/fx-events/image6.png)</span></span>

<span data-ttu-id="c19de-311">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-311">**Description**</span></span> 

<span data-ttu-id="c19de-312">이 이벤트는 내부 FileX I/O 드라이버 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-312">This event represents an internal FileX I/O driver read event.</span></span>

<span data-ttu-id="c19de-313">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-313">**Information Fields**</span></span>

- <span data-ttu-id="c19de-314">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-314">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-315">정보 필드 2: 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-315">Info Field 2: Sector.</span></span>
- <span data-ttu-id="c19de-316">정보 필드 3: 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-316">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="c19de-317">정보 필드 4: 버퍼 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-317">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-write"></a><span data-ttu-id="c19de-318">내부 I/O 드라이버 쓰기</span><span class="sxs-lookup"><span data-stu-id="c19de-318">Internal I/O Driver Write</span></span> 

#### <a name="internal-io-driver-write"></a><span data-ttu-id="c19de-319">내부 I/O 드라이버 쓰기</span><span class="sxs-lookup"><span data-stu-id="c19de-319">Internal I/O driver write</span></span> 

<span data-ttu-id="c19de-320">**아이콘** ![내부 I/O 드라이버 쓰기 아이콘](./media/user-guide/fx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-320">**Icon** ![Internal I / O driver write icon](./media/user-guide/fx-events/image7.png)</span></span>

<span data-ttu-id="c19de-321">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-321">**Description**</span></span> 

<span data-ttu-id="c19de-322">이 이벤트는 내부 FileX I/O 드라이버 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-322">This event represents an internal FileX I/O driver write event.</span></span>

<span data-ttu-id="c19de-323">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-323">**Information Fields**</span></span>

- <span data-ttu-id="c19de-324">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-324">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-325">정보 필드 2: 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-325">Info Field 2: Sector.</span></span>
- <span data-ttu-id="c19de-326">정보 필드 3: 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-326">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="c19de-327">정보 필드 4: 버퍼 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-327">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-flush"></a><span data-ttu-id="c19de-328">내부 I/O 드라이버 플러시</span><span class="sxs-lookup"><span data-stu-id="c19de-328">Internal I/O Driver Flush</span></span> 

#### <a name="internal-io-driver-flush"></a><span data-ttu-id="c19de-329">내부 I/O 드라이버 플러시</span><span class="sxs-lookup"><span data-stu-id="c19de-329">Internal I/O driver flush</span></span> 

<span data-ttu-id="c19de-330">**아이콘** ![내부 I/O 드라이버 플러시 아이콘](./media/user-guide/fx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-330">**Icon** ![Internal I / O driver flush icon](./media/user-guide/fx-events/image8.png)</span></span>

<span data-ttu-id="c19de-331">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-331">**Description**</span></span> 

<span data-ttu-id="c19de-332">이 이벤트는 내부 FileX I/O 드라이버 플러시 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-332">This event represents an internal FileX I/O driver flush event.</span></span>

<span data-ttu-id="c19de-333">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-333">**Information Fields**</span></span>

- <span data-ttu-id="c19de-334">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-334">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-335">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-335">Info Field 2: Not used.</span></span>
- <span data-ttu-id="c19de-336">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-336">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-337">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-337">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-abort"></a><span data-ttu-id="c19de-338">내부 I/O 드라이버 중단</span><span class="sxs-lookup"><span data-stu-id="c19de-338">Internal I/O Driver Abort</span></span> 

#### <a name="internal-io-dirver-abort"></a><span data-ttu-id="c19de-339">내부 I/O 드라이버 중단</span><span class="sxs-lookup"><span data-stu-id="c19de-339">Internal I/O dirver abort</span></span>

<span data-ttu-id="c19de-340">**아이콘** ![내부 I/O 드라이버 중단 아이콘](./media/user-guide/fx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-340">**Icon** ![Internal I / O driver abort icon](./media/user-guide/fx-events/image9.png)</span></span>

<span data-ttu-id="c19de-341">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-341">**Description**</span></span>

<span data-ttu-id="c19de-342">이 이벤트는 내부 FileX I/O 드라이버 중단 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-342">This event represents an internal FileX I/O driver abort event.</span></span>

<span data-ttu-id="c19de-343">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-343">**Information Fields**</span></span>

- <span data-ttu-id="c19de-344">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-344">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-345">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-345">Info Field 2: Not used.</span></span>
- <span data-ttu-id="c19de-346">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-346">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-347">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-347">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="c19de-348">내부 I/O 드라이버 초기화</span><span class="sxs-lookup"><span data-stu-id="c19de-348">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="c19de-349">내부 I/O 드라이버 초기화</span><span class="sxs-lookup"><span data-stu-id="c19de-349">Internal I/O driver initialize</span></span> 

<span data-ttu-id="c19de-350">**아이콘** ![내부 I/O 드라이버 초기화 아이콘](./media/user-guide/fx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-350">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/fx-events/image10.png)</span></span>

<span data-ttu-id="c19de-351">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-351">**Description**</span></span> 

<span data-ttu-id="c19de-352">이 이벤트는 내부 FileX I/O 드라이버 초기화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-352">This event represents an internal FileX I/O driver initialize event.</span></span>

<span data-ttu-id="c19de-353">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-353">**Information Fields**</span></span>

- <span data-ttu-id="c19de-354">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-354">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-355">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-355">Info Field 2: Not used.</span></span>
- <span data-ttu-id="c19de-356">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-356">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-357">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-357">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="c19de-358">내부 I/O 드라이버 부팅 섹터 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-358">Internal I/O Driver Boot Sector Read</span></span> 

#### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="c19de-359">내부 I/O 드라이버 부팅 섹터 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-359">Internal I/O driver boot sector read</span></span> 

<span data-ttu-id="c19de-360">**아이콘** ![내부 I/O 드라이버 부팅 섹터 읽기 아이콘](./media/user-guide/fx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-360">**Icon** ![Internal I / O driver boot sector read icon](./media/user-guide/fx-events/image11.png)</span></span>

<span data-ttu-id="c19de-361">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-361">**Description**</span></span> 

<span data-ttu-id="c19de-362">이 이벤트는 내부 FileX I/O 드라이버 부팅 섹터 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-362">This event represents an internal FileX I/O driver boot sector read event.</span></span>

<span data-ttu-id="c19de-363">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-363">**Information Fields**</span></span>

- <span data-ttu-id="c19de-364">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-364">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-365">정보 필드 2: 버퍼 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-365">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="c19de-366">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-366">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-367">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-367">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="c19de-368">내부 I/O 드라이버 해제 섹터</span><span class="sxs-lookup"><span data-stu-id="c19de-368">Internal I/O Driver Release Sectors</span></span> 

#### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="c19de-369">내부 I/O 드라이버 해제 섹터</span><span class="sxs-lookup"><span data-stu-id="c19de-369">Internal I/O driver release sectors</span></span> 

<span data-ttu-id="c19de-370">**아이콘** ![내부 I/O 드라이버 해제 섹터 아이콘](./media/user-guide/fx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-370">**Icon** ![Internal I / O driver release sectors icon](./media/user-guide/fx-events/image12.png)</span></span>

<span data-ttu-id="c19de-371">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-371">**Description**</span></span> 

<span data-ttu-id="c19de-372">이 이벤트는 내부 FileX I/O 드라이버 해제 섹터 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-372">This event represents an internal FileX I/O driver release sectors event.</span></span>

<span data-ttu-id="c19de-373">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-373">**Information Fields**</span></span>

- <span data-ttu-id="c19de-374">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-374">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-375">정보 필드 2: 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-375">Info Field 2: Sector.</span></span>
- <span data-ttu-id="c19de-376">정보 필드 3: 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-376">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="c19de-377">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-377">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="c19de-378">내부 I/O 드라이버 부팅 섹터 쓰기</span><span class="sxs-lookup"><span data-stu-id="c19de-378">Internal I/O Driver Boot Sector Write</span></span>

#### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="c19de-379">내부 I/O 드라이버 부팅 섹터 쓰기</span><span class="sxs-lookup"><span data-stu-id="c19de-379">Internal I/O driver boot sector write</span></span> 

<span data-ttu-id="c19de-380">**아이콘** ![내부 I/O 드라이버 부팅 섹터 쓰기 아이콘](./media/user-guide/fx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-380">**Icon** ![Internal I / O driver boot sector write icon](./media/user-guide/fx-events/image13.png)</span></span>

<span data-ttu-id="c19de-381">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-381">**Description**</span></span> 

<span data-ttu-id="c19de-382">이 이벤트는 내부 FileX I/O 드라이버 부팅 섹터 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-382">This event represents an internal FileX I/O driver boot sector write event.</span></span>

<span data-ttu-id="c19de-383">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-383">**Information Fields**</span></span>

- <span data-ttu-id="c19de-384">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-384">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-385">정보 필드 2: 버퍼 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-385">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="c19de-386">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-386">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-387">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-387">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="c19de-388">내부 I/O 드라이버 초기화 취소</span><span class="sxs-lookup"><span data-stu-id="c19de-388">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="c19de-389">내부 I/O 드라이버 초기화 취소</span><span class="sxs-lookup"><span data-stu-id="c19de-389">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="c19de-390">**아이콘** ![내부 I/O 드라이버 초기화 취소 아이콘](./media/user-guide/fx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-390">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/fx-events/image14.png)</span></span>

<span data-ttu-id="c19de-391">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-391">**Description**</span></span> 

<span data-ttu-id="c19de-392">이 이벤트는 내부 FileX I/O 드라이버 초기화 취소 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-392">This event represents an internal FileX I/O driver un-initialize event.</span></span>

<span data-ttu-id="c19de-393">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-393">**Information Fields**</span></span>

- <span data-ttu-id="c19de-394">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-394">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-395">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-395">Info Field 2: Not used.</span></span>
- <span data-ttu-id="c19de-396">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-396">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-397">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-397">Info Field 4: Not used.</span></span>
</blockquote></td>

### <a name="directory-attributes-read"></a><span data-ttu-id="c19de-398">디렉터리 특성 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-398">Directory Attributes Read</span></span> 

#### <a name="fx_directory_attributes_read"></a><span data-ttu-id="c19de-399">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="c19de-399">fx_directory_attributes_read</span></span> 

<span data-ttu-id="c19de-400">**아이콘** ![디렉터리 특성 읽기 아이콘](./media/user-guide/fx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-400">**Icon** ![Directory attributes read icon](./media/user-guide/fx-events/image15.png)</span></span>

<span data-ttu-id="c19de-401">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-401">**Description**</span></span> 

<span data-ttu-id="c19de-402">이 이벤트는 디렉터리 특성 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-402">This event represents a directory attributes read event.</span></span>

<span data-ttu-id="c19de-403">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-403">**Information Fields**</span></span>

- <span data-ttu-id="c19de-404">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-404">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-405">정보 필드 2: 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-405">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="c19de-406">정보 필드 3: 다음과 같은 특성 비트 맵입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-406">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="c19de-407">attribute</span><span class="sxs-lookup"><span data-stu-id="c19de-407">Attribute</span></span>                         | <span data-ttu-id="c19de-408">값</span><span class="sxs-lookup"><span data-stu-id="c19de-408">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="c19de-409">읽기 전용</span><span class="sxs-lookup"><span data-stu-id="c19de-409">Read Only</span></span>                        | <span data-ttu-id="c19de-410">(0x01)</span><span class="sxs-lookup"><span data-stu-id="c19de-410">(0x01)</span></span>  |
  |  <span data-ttu-id="c19de-411">숨김</span><span class="sxs-lookup"><span data-stu-id="c19de-411">Hidden</span></span>                           | <span data-ttu-id="c19de-412">(0x02)</span><span class="sxs-lookup"><span data-stu-id="c19de-412">(0x02)</span></span>  |
  |  <span data-ttu-id="c19de-413">시스템</span><span class="sxs-lookup"><span data-stu-id="c19de-413">System</span></span>                           | <span data-ttu-id="c19de-414">(0x04)</span><span class="sxs-lookup"><span data-stu-id="c19de-414">(0x04)</span></span>  |
  |  <span data-ttu-id="c19de-415">볼륨</span><span class="sxs-lookup"><span data-stu-id="c19de-415">Volume</span></span>                           | <span data-ttu-id="c19de-416">(0x08)</span><span class="sxs-lookup"><span data-stu-id="c19de-416">(0x08)</span></span>  |
  |  <span data-ttu-id="c19de-417">디렉터리</span><span class="sxs-lookup"><span data-stu-id="c19de-417">Directory</span></span>                        | <span data-ttu-id="c19de-418">(0x10)</span><span class="sxs-lookup"><span data-stu-id="c19de-418">(0x10)</span></span>  |
  |  <span data-ttu-id="c19de-419">보관</span><span class="sxs-lookup"><span data-stu-id="c19de-419">Archive</span></span>                          | <span data-ttu-id="c19de-420">(0x20)</span><span class="sxs-lookup"><span data-stu-id="c19de-420">(0x20)</span></span>  |
- <span data-ttu-id="c19de-421">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-421">Info Field 4: Not used.</span></span>

### <a name="directory-attributes-set"></a><span data-ttu-id="c19de-422">디렉터리 특성 설정</span><span class="sxs-lookup"><span data-stu-id="c19de-422">Directory Attributes Set</span></span> 

#### <a name="fx_directory_attributes_set"></a><span data-ttu-id="c19de-423">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="c19de-423">fx_directory_attributes_set</span></span> 

<span data-ttu-id="c19de-424">**아이콘** ![특성 설정 아이콘](./media/user-guide/fx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-424">**Icon** ![Attributes set icon](./media/user-guide/fx-events/image16.png)</span></span>

<span data-ttu-id="c19de-425">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-425">**Description**</span></span> 

<span data-ttu-id="c19de-426">이 이벤트는 디렉터리 특성 설정 이벤트 디렉터리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-426">This event represents a directory a directory attributes set event.</span></span>

<span data-ttu-id="c19de-427">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-427">**Information Fields**</span></span>

- <span data-ttu-id="c19de-428">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-428">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-429">정보 필드 2: 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-429">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="c19de-430">정보 필드 3: 다음과 같은 특성 비트 맵입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-430">Info Field 3: Attributes bit map:</span></span>

  |  <span data-ttu-id="c19de-431">attribute</span><span class="sxs-lookup"><span data-stu-id="c19de-431">Attribute</span></span>                        | <span data-ttu-id="c19de-432">값</span><span class="sxs-lookup"><span data-stu-id="c19de-432">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="c19de-433">읽기 전용</span><span class="sxs-lookup"><span data-stu-id="c19de-433">Read Only</span></span>                        | <span data-ttu-id="c19de-434">(0x01)</span><span class="sxs-lookup"><span data-stu-id="c19de-434">(0x01)</span></span>  |
  |  <span data-ttu-id="c19de-435">숨김</span><span class="sxs-lookup"><span data-stu-id="c19de-435">Hidden</span></span>                           | <span data-ttu-id="c19de-436">(0x02)</span><span class="sxs-lookup"><span data-stu-id="c19de-436">(0x02)</span></span>  |
  |  <span data-ttu-id="c19de-437">시스템</span><span class="sxs-lookup"><span data-stu-id="c19de-437">System</span></span>                           | <span data-ttu-id="c19de-438">(0x04)</span><span class="sxs-lookup"><span data-stu-id="c19de-438">(0x04)</span></span>  |
  |  <span data-ttu-id="c19de-439">보관</span><span class="sxs-lookup"><span data-stu-id="c19de-439">Archive</span></span>                          | <span data-ttu-id="c19de-440">(0x20)</span><span class="sxs-lookup"><span data-stu-id="c19de-440">(0x20)</span></span>  |
- <span data-ttu-id="c19de-441">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-441">Info Field 4: Not used.</span></span>

### <a name="directory-create"></a><span data-ttu-id="c19de-442">디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="c19de-442">Directory Create</span></span> 

#### <a name="fx_directory_create"></a><span data-ttu-id="c19de-443">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="c19de-443">fx_directory_create</span></span>

<span data-ttu-id="c19de-444">**아이콘** ![디렉터리 만들기 아이콘](./media/user-guide/fx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-444">**Icon** ![Directory create icon](./media/user-guide/fx-events/image17.png)</span></span>

<span data-ttu-id="c19de-445">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-445">**Description**</span></span> 

<span data-ttu-id="c19de-446">이 이벤트는 디렉터리 만들기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-446">This event represents a directory create event.</span></span>

<span data-ttu-id="c19de-447">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-447">**Information Fields**</span></span>

- <span data-ttu-id="c19de-448">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-448">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-449">정보 필드 2: 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-449">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="c19de-450">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-451">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-451">Info Field 4: Not used.</span></span>

### <a name="directory-default-get"></a><span data-ttu-id="c19de-452">디렉터리 기본값 가져오기</span><span class="sxs-lookup"><span data-stu-id="c19de-452">Directory Default Get</span></span> 

#### <a name="fx_directory_default_get"></a><span data-ttu-id="c19de-453">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="c19de-453">fx_directory_default_get</span></span> 

<span data-ttu-id="c19de-454">**아이콘** ![디렉터리 기본값 가져오기 아이콘](./media/user-guide/fx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-454">**Icon** ![Directory default get icon](./media/user-guide/fx-events/image18.png)</span></span>

<span data-ttu-id="c19de-455">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-455">**Description**</span></span> 

<span data-ttu-id="c19de-456">이 이벤트는 디렉터리 기본값 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-456">This event represents a directory default set event.</span></span>

<span data-ttu-id="c19de-457">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-457">**Information Fields**</span></span>

- <span data-ttu-id="c19de-458">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-458">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-459">정보 필드 2: 반환 경로 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-459">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="c19de-460">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-461">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-461">Info Field 4: Not used.</span></span>

### <a name="directory-default-set"></a><span data-ttu-id="c19de-462">디렉터리 기본값 설정</span><span class="sxs-lookup"><span data-stu-id="c19de-462">Directory Default Set</span></span> 

#### <a name="fx_directory_default_set"></a><span data-ttu-id="c19de-463">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="c19de-463">fx_directory_default_set</span></span> 

<span data-ttu-id="c19de-464">**아이콘** ![디렉터리 기본값 설정 아이콘](./media/user-guide/fx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-464">**Icon** ![Directory default set icon](./media/user-guide/fx-events/image19.png)</span></span>

<span data-ttu-id="c19de-465">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-465">**Description**</span></span> 

<span data-ttu-id="c19de-466">이 이벤트는 디렉터리 기본값 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-466">This event represents a directory default set event.</span></span>

<span data-ttu-id="c19de-467">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-467">**Information Fields**</span></span>

- <span data-ttu-id="c19de-468">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-468">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-469">정보 필드 2: 새 기본 경로 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-469">Info Field 2: Pointer to new default path name.</span></span>
- <span data-ttu-id="c19de-470">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-471">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-471">Info Field 4: Not used.</span></span>

### <a name="directory-delete"></a><span data-ttu-id="c19de-472">디렉터리 삭제</span><span class="sxs-lookup"><span data-stu-id="c19de-472">Directory Delete</span></span> 

#### <a name="fx_directory_delete"></a><span data-ttu-id="c19de-473">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="c19de-473">fx_directory_delete</span></span>

<span data-ttu-id="c19de-474">**아이콘** ![디렉터리 삭제 아이콘](./media/user-guide/fx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-474">**Icon** ![Directory delete icon](./media/user-guide/fx-events/image20.png)</span></span>

<span data-ttu-id="c19de-475">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-475">**Description**</span></span> 

<span data-ttu-id="c19de-476">이 이벤트는 디렉터리 삭제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-476">This event represents a directory delete event.</span></span>

<span data-ttu-id="c19de-477">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-477">**Information Fields**</span></span>
- <span data-ttu-id="c19de-478">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-478">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-479">정보 필드 2: 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-479">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="c19de-480">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-481">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-481">Info Field 4: Not used.</span></span>

### <a name="directory-first-entry-find"></a><span data-ttu-id="c19de-482">디렉터리의 첫 번째 항목 찾기</span><span class="sxs-lookup"><span data-stu-id="c19de-482">Directory First Entry Find</span></span> 

#### <a name="fx_directory_first_entry_find"></a><span data-ttu-id="c19de-483">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="c19de-483">fx_directory_first_entry_find</span></span>

<span data-ttu-id="c19de-484">**아이콘** ![디렉터리의 첫 번째 항목 찾기 아이콘](./media/user-guide/fx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-484">**Icon** ![Directory first entry find icon](./media/user-guide/fx-events/image21.png)</span></span>

<span data-ttu-id="c19de-485">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-485">**Description**</span></span> 

<span data-ttu-id="c19de-486">이 이벤트는 디렉터리의 첫 번째 항목 찾기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-486">This event represents a directory first entry find event.</span></span>

<span data-ttu-id="c19de-487">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-487">**Information Fields**</span></span>

- <span data-ttu-id="c19de-488">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-488">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-489">정보 필드 2: 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-489">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="c19de-490">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-491">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-491">Info Field 4: Not used.</span></span>

### <a name="directory-first-full-entry-find"></a><span data-ttu-id="c19de-492">디렉터리의 첫 번째 전체 항목 찾기</span><span class="sxs-lookup"><span data-stu-id="c19de-492">Directory First Full Entry Find</span></span> 

#### <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="c19de-493">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="c19de-493">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="c19de-494">**아이콘** ![디렉터리의 첫 번째 전체 항목 찾기 아이콘](./media/user-guide/fx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-494">**Icon** ![Directory first full entry find icon](./media/user-guide/fx-events/image22.png)</span></span>

<span data-ttu-id="c19de-495">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-495">**Description**</span></span> 

<span data-ttu-id="c19de-496">이 이벤트는 디렉터리의 첫 번째 전체 항목 찾기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-496">This event represents a directory first full entry find event.</span></span>

<span data-ttu-id="c19de-497">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-497">**Information Fields**</span></span>

- <span data-ttu-id="c19de-498">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-498">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-499">정보 필드 2: 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-499">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="c19de-500">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-501">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-501">Info Field 4: Not used.</span></span>

### <a name="directory-information-get"></a><span data-ttu-id="c19de-502">디렉터리 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="c19de-502">Directory Information Get</span></span> 

#### <a name="fx_directory_information_get"></a><span data-ttu-id="c19de-503">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="c19de-503">fx_directory_information_get</span></span>

<span data-ttu-id="c19de-504">**아이콘** ![디렉터리 정보 가져오기 아이콘](./media/user-guide/fx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-504">**Icon** ![Directory information get icon](./media/user-guide/fx-events/image23.png)</span></span>

<span data-ttu-id="c19de-505">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-505">**Description**</span></span> 

<span data-ttu-id="c19de-506">이 이벤트는 디렉터리 정보 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-506">This event represents a directory information get event.</span></span>

<span data-ttu-id="c19de-507">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-507">**Information Fields**</span></span>

- <span data-ttu-id="c19de-508">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-508">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-509">정보 필드 2: 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-509">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="c19de-510">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-510">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-511">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-511">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-clear"></a><span data-ttu-id="c19de-512">디렉터리 로컬 경로 지우기</span><span class="sxs-lookup"><span data-stu-id="c19de-512">Directory Local Path Clear</span></span> 

#### <a name="fx_directory_local_path_clear"></a><span data-ttu-id="c19de-513">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="c19de-513">fx_directory_local_path_clear</span></span>

<span data-ttu-id="c19de-514">**아이콘** ![디렉터리 로컬 경로 지우기 아이콘](./media/user-guide/fx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-514">**Icon** ![Directory local path clear icon](./media/user-guide/fx-events/image24.png)</span></span>

<span data-ttu-id="c19de-515">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-515">**Description**</span></span> 

<span data-ttu-id="c19de-516">이 이벤트는 디렉터리 로컬 경로 지우기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-516">This event represents a directory local path clear event.</span></span>

<span data-ttu-id="c19de-517">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-517">**Information Fields**</span></span>

- <span data-ttu-id="c19de-518">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-518">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-519">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="c19de-520">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-521">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-521">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-get"></a><span data-ttu-id="c19de-522">디렉터리 로컬 경로 가져오기</span><span class="sxs-lookup"><span data-stu-id="c19de-522">Directory Local Path Get</span></span> 

#### <a name="fx_directory_local_path_get"></a><span data-ttu-id="c19de-523">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="c19de-523">fx_directory_local_path_get</span></span>

<span data-ttu-id="c19de-524">**아이콘** ![디렉터리 로컬 경로 가져오기 아이콘](./media/user-guide/fx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-524">**Icon** ![Directory local path get icon](./media/user-guide/fx-events/image25.png)</span></span>

<span data-ttu-id="c19de-525">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-525">**Description**</span></span> 

<span data-ttu-id="c19de-526">이 이벤트는 디렉터리 로컬 경로 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-526">This event represents a directory local path get event.</span></span>

<span data-ttu-id="c19de-527">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-527">**Information Fields**</span></span>

- <span data-ttu-id="c19de-528">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-528">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-529">정보 필드 2: 반환 경로 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-529">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="c19de-530">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-531">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-531">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-restore"></a><span data-ttu-id="c19de-532">디렉터리 로컬 경로 복원</span><span class="sxs-lookup"><span data-stu-id="c19de-532">Directory Local Path Restore</span></span> 

#### <a name="fx_directory_local_path_restore"></a><span data-ttu-id="c19de-533">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="c19de-533">fx_directory_local_path_restore</span></span>

<span data-ttu-id="c19de-534">**아이콘** ![디렉터리 로컬 경로 복원 아이콘](./media/user-guide/fx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-534">**Icon** ![Directory local path restore icon](./media/user-guide/fx-events/image26.png)</span></span>

<span data-ttu-id="c19de-535">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-535">**Description**</span></span> 

<span data-ttu-id="c19de-536">이 이벤트는 디렉터리 로컬 경로 복원 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-536">This event represents a directory local path restore event.</span></span>

<span data-ttu-id="c19de-537">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-537">**Information Fields**</span></span>

- <span data-ttu-id="c19de-538">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-538">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-539">정보 필드 2: 로컬 경로 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-539">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="c19de-540">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-540">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-541">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-541">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-set"></a><span data-ttu-id="c19de-542">디렉터리 로컬 경로 설정</span><span class="sxs-lookup"><span data-stu-id="c19de-542">Directory Local Path Set</span></span> 

#### <a name="fx_directory_local_path_set"></a><span data-ttu-id="c19de-543">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="c19de-543">fx_directory_local_path_set</span></span>

<span data-ttu-id="c19de-544">**아이콘** ![디렉터리 로컬 경로 설정 아이콘](./media/user-guide/fx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-544">**Icon** ![Directory local path set icon](./media/user-guide/fx-events/image27.png)</span></span>

<span data-ttu-id="c19de-545">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-545">**Description**</span></span> 

<span data-ttu-id="c19de-546">이 이벤트는 디렉터리 로컬 경로 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-546">This event represents a directory local path set event.</span></span>

<span data-ttu-id="c19de-547">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-547">**Information Fields**</span></span>

- <span data-ttu-id="c19de-548">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-548">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-549">정보 필드 2: 로컬 경로 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-549">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="c19de-550">정보 필드 3: 새 경로 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-550">Info Field 3: Pointer to new path name.</span></span>
- <span data-ttu-id="c19de-551">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-551">Info Field 4: Not used.</span></span>

### <a name="directory-long-name-get"></a><span data-ttu-id="c19de-552">디렉터리의 긴 이름 가져오기</span><span class="sxs-lookup"><span data-stu-id="c19de-552">Directory Long Name Get</span></span> 

#### <a name="fx_directory_long_name_get"></a><span data-ttu-id="c19de-553">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="c19de-553">fx_directory_long_name_get</span></span>

<span data-ttu-id="c19de-554">**아이콘** ![디렉터리의 긴 이름 가져오기 아이콘](./media/user-guide/fx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-554">**Icon** ![Directory long name get icon](./media/user-guide/fx-events/image28.png)</span></span>

<span data-ttu-id="c19de-555">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-555">**Description**</span></span> 

<span data-ttu-id="c19de-556">이 이벤트는 디렉터리의 긴 이름 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-556">This event represents a directory long name get event.</span></span>

<span data-ttu-id="c19de-557">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-557">**Information Fields**</span></span>

- <span data-ttu-id="c19de-558">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-558">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-559">정보 필드 2: 짧은 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-559">Info Field 2: Pointer to short file name.</span></span>
- <span data-ttu-id="c19de-560">정보 필드 3: 긴 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-560">Info Field 3: Pointer to long file name.</span></span>
- <span data-ttu-id="c19de-561">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-561">Info Field 4: Not used.</span></span>

### <a name="directory-name-test"></a><span data-ttu-id="c19de-562">디렉터리 이름 테스트</span><span class="sxs-lookup"><span data-stu-id="c19de-562">Directory Name Test</span></span> 

#### <a name="fx_directory_name_test"></a><span data-ttu-id="c19de-563">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="c19de-563">fx_directory_name_test</span></span>

<span data-ttu-id="c19de-564">**아이콘** ![디렉터리 이름 테스트 아이콘](./media/user-guide/fx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-564">**Icon** ![Directory name test icon](./media/user-guide/fx-events/image29.png)</span></span>

<span data-ttu-id="c19de-565">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-565">**Description**</span></span> 

<span data-ttu-id="c19de-566">이 이벤트는 디렉터리 이름 테스트 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-566">This event represents a directory name test event.</span></span>

<span data-ttu-id="c19de-567">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-567">**Information Fields**</span></span>

- <span data-ttu-id="c19de-568">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-568">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-569">정보 필드 2: 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-569">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="c19de-570">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-570">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-571">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-571">Info Field 4: Not used.</span></span>

### <a name="directory-next-entry-find"></a><span data-ttu-id="c19de-572">디렉터리의 다음 항목 찾기</span><span class="sxs-lookup"><span data-stu-id="c19de-572">Directory Next Entry Find</span></span> 

#### <a name="fx_directory_next_entry_find"></a><span data-ttu-id="c19de-573">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="c19de-573">fx_directory_next_entry_find</span></span>

<span data-ttu-id="c19de-574">**아이콘** ![디렉터리의 다음 항목 찾기 아이콘](./media/user-guide/fx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-574">**Icon** ![Directory next entry find icon](./media/user-guide/fx-events/image30.png)</span></span>

<span data-ttu-id="c19de-575">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-575">**Description**</span></span> 

<span data-ttu-id="c19de-576">이 이벤트는 디렉터리의 다음 항목 찾기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-576">This event represents a directory next entry find event.</span></span>

<span data-ttu-id="c19de-577">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-577">**Information Fields**</span></span>

- <span data-ttu-id="c19de-578">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-578">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-579">정보 필드 2: 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-579">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="c19de-580">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-580">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-581">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-581">Info Field 4: Not used.</span></span>

### <a name="directory-next-full-entry-find"></a><span data-ttu-id="c19de-582">디렉터리의 다음 전체 항목 찾기</span><span class="sxs-lookup"><span data-stu-id="c19de-582">Directory Next Full Entry Find</span></span> 

#### <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="c19de-583">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="c19de-583">fx_directory_next_full_entry_find</span></span>

<span data-ttu-id="c19de-584">**아이콘** ![디렉터리의 다음 전체 항목 찾기 아이콘](./media/user-guide/fx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-584">**Icon** ![Directory next full entry find icon](./media/user-guide/fx-events/image31.png)</span></span>

<span data-ttu-id="c19de-585">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-585">**Description**</span></span>

<span data-ttu-id="c19de-586">이 이벤트는 디렉터리의 다음 전체 항목 찾기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-586">This event represents a directory next full entry find event.</span></span>

<span data-ttu-id="c19de-587">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-587">**Information Fields**</span></span>

- <span data-ttu-id="c19de-588">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-588">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-589">정보 필드 2: 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-589">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="c19de-590">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-590">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-591">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-591">Info Field 4: Not used.</span></span>

### <a name="directory-rename"></a><span data-ttu-id="c19de-592">디렉터리 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="c19de-592">Directory Rename</span></span> 

#### <a name="fx_directory_rename-event"></a><span data-ttu-id="c19de-593">fx_directory_rename event</span><span class="sxs-lookup"><span data-stu-id="c19de-593">fx_directory_rename event</span></span>

<span data-ttu-id="c19de-594">**아이콘** ![디렉터리 이름 바꾸기 아이콘](./media/user-guide/fx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-594">**Icon** ![Directory rename icon](./media/user-guide/fx-events/image32.png)</span></span>

<span data-ttu-id="c19de-595">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-595">**Description**</span></span>

<span data-ttu-id="c19de-596">이 이벤트는 디렉터리 이름 바꾸기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-596">This event represents a directory rename event.</span></span>

<span data-ttu-id="c19de-597">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-597">**Information Fields**</span></span>

- <span data-ttu-id="c19de-598">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-598">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-599">정보 필드 2: 이전 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-599">Info Field 2: Pointer to old directory name.</span></span>
- <span data-ttu-id="c19de-600">정보 필드 3: 새 디렉터리 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-600">Info Field 3: Pointer to new directory name.</span></span>
- <span data-ttu-id="c19de-601">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-601">Info Field 4: Not used.</span></span>

### <a name="directory-short-name-get"></a><span data-ttu-id="c19de-602">디렉터리의 짧은 이름 가져오기</span><span class="sxs-lookup"><span data-stu-id="c19de-602">Directory Short Name Get</span></span> 

#### <a name="fx_directory_short_name_get"></a><span data-ttu-id="c19de-603">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="c19de-603">fx_directory_short_name_get</span></span>

<span data-ttu-id="c19de-604">**아이콘** ![디렉터리의 짧은 이름 가져오기 아이콘](./media/user-guide/fx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-604">**Icon** ![Directory short name get icon](./media/user-guide/fx-events/image33.png)</span></span>

<span data-ttu-id="c19de-605">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-605">**Description**</span></span>

<span data-ttu-id="c19de-606">이 이벤트는 디렉터리의 짧은 이름 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-606">This event represents a directory short name get event.</span></span>

<span data-ttu-id="c19de-607">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-607">**Information Fields**</span></span> 

- <span data-ttu-id="c19de-608">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-608">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-609">정보 필드 2: 긴 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-609">Info Field 2: Pointer to long file name.</span></span>
- <span data-ttu-id="c19de-610">정보 필드 3: 짧은 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-610">Info Field 3: Pointer to short file name.</span></span>
- <span data-ttu-id="c19de-611">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-611">Info Field 4: Not used.</span></span>

### <a name="file-allocate"></a><span data-ttu-id="c19de-612">파일 할당</span><span class="sxs-lookup"><span data-stu-id="c19de-612">File Allocate</span></span> 

#### <a name="fx_file_allocate"></a><span data-ttu-id="c19de-613">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="c19de-613">fx_file_allocate</span></span>

<span data-ttu-id="c19de-614">**아이콘** ![파일 할당 아이콘](./media/user-guide/fx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-614">**Icon** ![File allocate icon](./media/user-guide/fx-events/image34.png)</span></span>

<span data-ttu-id="c19de-615">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-615">**Description**</span></span>

<span data-ttu-id="c19de-616">이 이벤트는 파일 할당 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-616">This event represents a file allocate event.</span></span>

<span data-ttu-id="c19de-617">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-617">**Information Fields**</span></span>

- <span data-ttu-id="c19de-618">정보 필드 1: 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-618">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="c19de-619">정보 필드 2: 요청된 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-619">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="c19de-620">정보 필드 3: 현재 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-620">Info Field 3: Current size.</span></span>
- <span data-ttu-id="c19de-621">정보 필드 4: 새 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-621">Info Field 4: New size.</span></span>

### <a name="file-attributes-read"></a><span data-ttu-id="c19de-622">파일 특성 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-622">File Attributes Read</span></span> 

#### <a name="fx_file_attributes_read"></a><span data-ttu-id="c19de-623">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="c19de-623">fx_file_attributes_read</span></span>

<span data-ttu-id="c19de-624">**아이콘** ![파일 특성 읽기 아이콘](./media/user-guide/fx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-624">**Icon** ![File attributes read icon](./media/user-guide/fx-events/image35.png)</span></span>

<span data-ttu-id="c19de-625">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-625">**Description**</span></span>

<span data-ttu-id="c19de-626">이 이벤트는 파일 특성 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-626">This event represents a file attributes read event.</span></span>

<span data-ttu-id="c19de-627">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-627">**Information Fields**</span></span>

- <span data-ttu-id="c19de-628">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-628">Info Field 1: Pointer to the media.</span></span> 
- <span data-ttu-id="c19de-629">정보 필드 2: 다음과 같은 특성 비트 맵입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-629">Info Field 2: Attributes bit map:</span></span>

  |  <span data-ttu-id="c19de-630">특성</span><span class="sxs-lookup"><span data-stu-id="c19de-630">Attribut</span></span>                         | <span data-ttu-id="c19de-631">값</span><span class="sxs-lookup"><span data-stu-id="c19de-631">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="c19de-632">읽기 전용</span><span class="sxs-lookup"><span data-stu-id="c19de-632">Read Only</span></span>                        | <span data-ttu-id="c19de-633">(0x01)</span><span class="sxs-lookup"><span data-stu-id="c19de-633">(0x01)</span></span>  |
  |  <span data-ttu-id="c19de-634">숨김</span><span class="sxs-lookup"><span data-stu-id="c19de-634">Hidden</span></span>                           | <span data-ttu-id="c19de-635">(0x02)</span><span class="sxs-lookup"><span data-stu-id="c19de-635">(0x02)</span></span>  |
  |  <span data-ttu-id="c19de-636">시스템</span><span class="sxs-lookup"><span data-stu-id="c19de-636">System</span></span>                           | <span data-ttu-id="c19de-637">(0x04)</span><span class="sxs-lookup"><span data-stu-id="c19de-637">(0x04)</span></span>  |
  |  <span data-ttu-id="c19de-638">볼륨</span><span class="sxs-lookup"><span data-stu-id="c19de-638">Volume</span></span>                           | <span data-ttu-id="c19de-639">(0x08)</span><span class="sxs-lookup"><span data-stu-id="c19de-639">(0x08)</span></span>  |
  |  <span data-ttu-id="c19de-640">디렉터리</span><span class="sxs-lookup"><span data-stu-id="c19de-640">Directory</span></span>                        | <span data-ttu-id="c19de-641">(0x10)</span><span class="sxs-lookup"><span data-stu-id="c19de-641">(0x10)</span></span>  |
  |  <span data-ttu-id="c19de-642">보관</span><span class="sxs-lookup"><span data-stu-id="c19de-642">Archive</span></span>                          | <span data-ttu-id="c19de-643">(0x20)</span><span class="sxs-lookup"><span data-stu-id="c19de-643">(0x20)</span></span>  |
- <span data-ttu-id="c19de-644">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-644">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-645">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-645">Info Field 4: Not used.</span></span>

### <a name="file-attributes-set"></a><span data-ttu-id="c19de-646">파일 특성 설정</span><span class="sxs-lookup"><span data-stu-id="c19de-646">File Attributes Set</span></span> 

#### <a name="fx_file_attributes_set"></a><span data-ttu-id="c19de-647">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="c19de-647">fx_file_attributes_set</span></span>

<span data-ttu-id="c19de-648">**아이콘** ![파일 특성 설정 아이콘](./media/user-guide/fx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-648">**Icon** ![File attributes set icon](./media/user-guide/fx-events/image36.png)</span></span>

<span data-ttu-id="c19de-649">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-649">**Description**</span></span> 

<span data-ttu-id="c19de-650">이 이벤트는 파일 특성 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-650">This event represents a file attributes set event.</span></span>

<span data-ttu-id="c19de-651">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-651">**Information Fields**</span></span>

- <span data-ttu-id="c19de-652">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-652">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-653">정보 필드 2: 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-653">Info Field 2: Pointer to file name.</span></span> 
- <span data-ttu-id="c19de-654">정보 필드 3: 다음과 같은 특성 비트 맵입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-654">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="c19de-655">attribute</span><span class="sxs-lookup"><span data-stu-id="c19de-655">Attribute</span></span>                         | <span data-ttu-id="c19de-656">값</span><span class="sxs-lookup"><span data-stu-id="c19de-656">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="c19de-657">읽기 전용</span><span class="sxs-lookup"><span data-stu-id="c19de-657">Read Only</span></span>                        | <span data-ttu-id="c19de-658">(0x01)</span><span class="sxs-lookup"><span data-stu-id="c19de-658">(0x01)</span></span>  |
  |  <span data-ttu-id="c19de-659">숨김</span><span class="sxs-lookup"><span data-stu-id="c19de-659">Hidden</span></span>                           | <span data-ttu-id="c19de-660">(0x02)</span><span class="sxs-lookup"><span data-stu-id="c19de-660">(0x02)</span></span>  |
  |  <span data-ttu-id="c19de-661">시스템</span><span class="sxs-lookup"><span data-stu-id="c19de-661">System</span></span>                           | <span data-ttu-id="c19de-662">(0x04)</span><span class="sxs-lookup"><span data-stu-id="c19de-662">(0x04)</span></span>  |
  |  <span data-ttu-id="c19de-663">보관</span><span class="sxs-lookup"><span data-stu-id="c19de-663">Archive</span></span>                          | <span data-ttu-id="c19de-664">(0x20)</span><span class="sxs-lookup"><span data-stu-id="c19de-664">(0x20)</span></span>  |
- <span data-ttu-id="c19de-665">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-665">Info Field 4: Not used.</span></span>

### <a name="file-best-effort-allocate"></a><span data-ttu-id="c19de-666">최선의 파일 할당</span><span class="sxs-lookup"><span data-stu-id="c19de-666">File Best Effort Allocate</span></span> 

#### <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="c19de-667">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="c19de-667">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="c19de-668">**아이콘** ![최선의 파일 할당 아이콘](./media/user-guide/fx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-668">**Icon** ![File best effort allocate icon](./media/user-guide/fx-events/image37.png)</span></span>

<span data-ttu-id="c19de-669">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-669">**Description**</span></span> 

<span data-ttu-id="c19de-670">이 이벤트는 최선의 파일 할당 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-670">This event represents a file best effort allocate event.</span></span>

<span data-ttu-id="c19de-671">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-671">**Information Fields**</span></span>

- <span data-ttu-id="c19de-672">정보 필드 1: 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-672">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="c19de-673">정보 필드 2: 요청된 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-673">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="c19de-674">정보 필드 3: 할당된 실제 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-674">Info Field 3: Actual size allocated.</span></span>
- <span data-ttu-id="c19de-675">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-675">Info Field 4: Not used.</span></span>

### <a name="file-close"></a><span data-ttu-id="c19de-676">파일 닫기</span><span class="sxs-lookup"><span data-stu-id="c19de-676">File Close</span></span> 

#### <a name="fx_file_close"></a><span data-ttu-id="c19de-677">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="c19de-677">fx_file_close</span></span>

<span data-ttu-id="c19de-678">**아이콘** ![파일 닫기 아이콘](./media/user-guide/fx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-678">**Icon** ![File close icon](./media/user-guide/fx-events/image38.png)</span></span>

<span data-ttu-id="c19de-679">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-679">**Description**</span></span> 

<span data-ttu-id="c19de-680">이 이벤트는 파일 닫기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-680">This event represents a file close event.</span></span>

<span data-ttu-id="c19de-681">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-681">**Information Fields**</span></span>

- <span data-ttu-id="c19de-682">정보 필드 1: 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-682">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="c19de-683">정보 필드 2: 파일 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-683">Info Field 2: File size.</span></span>
- <span data-ttu-id="c19de-684">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-684">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-685">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-685">Info Field 4: Not used.</span></span>

### <a name="file-create"></a><span data-ttu-id="c19de-686">파일 만들기</span><span class="sxs-lookup"><span data-stu-id="c19de-686">File Create</span></span>

#### <a name="fx_file_create"></a><span data-ttu-id="c19de-687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="c19de-687">fx_file_create</span></span>

<span data-ttu-id="c19de-688">**아이콘** ![파일 만들기 아이콘](./media/user-guide/fx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-688">**Icon** ![File create icon](./media/user-guide/fx-events/image39.png)</span></span>

<span data-ttu-id="c19de-689">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-689">**Description**</span></span>

<span data-ttu-id="c19de-690">이 이벤트는 파일 만들기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-690">This event represents a file create event.</span></span>

<span data-ttu-id="c19de-691">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-691">**Information Fields**</span></span>

- <span data-ttu-id="c19de-692">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-692">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-693">정보 필드 2: 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-693">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="c19de-694">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-694">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-695">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-695">Info Field 4: Not used.</span></span>

### <a name="file-date-time-set"></a><span data-ttu-id="c19de-696">파일 날짜 시간 설정</span><span class="sxs-lookup"><span data-stu-id="c19de-696">File Date Time Set</span></span> 

#### <a name="fx_file_date_time_set"></a><span data-ttu-id="c19de-697">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="c19de-697">fx_file_date_time_set</span></span>

<span data-ttu-id="c19de-698">**아이콘** ![파일 날짜 시간 설정 아이콘](./media/user-guide/fx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-698">**Icon** ![File date time set icon](./media/user-guide/fx-events/image40.png)</span></span>

<span data-ttu-id="c19de-699">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-699">**Description**</span></span>

<span data-ttu-id="c19de-700">이 이벤트는 파일 날짜/시간 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-700">This event represents a file date/time set event.</span></span>

<span data-ttu-id="c19de-701">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-701">**Information Fields**</span></span>

- <span data-ttu-id="c19de-702">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-702">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-703">정보 필드 2: 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-703">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="c19de-704">정보 필드 3: 연도입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-704">Info Field 3: Year.</span></span>
- <span data-ttu-id="c19de-705">정보 필드 4: 월입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-705">Info Field 4: Month.</span></span>

### <a name="file-delete"></a><span data-ttu-id="c19de-706">파일 삭제</span><span class="sxs-lookup"><span data-stu-id="c19de-706">File Delete</span></span> 

#### <a name="fx_file_delete"></a><span data-ttu-id="c19de-707">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="c19de-707">fx_file_delete</span></span>

<span data-ttu-id="c19de-708">**아이콘** ![파일 삭제 아이콘](./media/user-guide/fx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-708">**Icon** ![File delete icon](./media/user-guide/fx-events/image41.png)</span></span>

<span data-ttu-id="c19de-709">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-709">**Description**</span></span>

<span data-ttu-id="c19de-710">이 이벤트는 파일 삭제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-710">This event represents a file delete event.</span></span>

<span data-ttu-id="c19de-711">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-711">**Information Fields**</span></span>

- <span data-ttu-id="c19de-712">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-712">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-713">정보 필드 2: 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-713">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="c19de-714">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-714">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-715">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-715">Info Field 4: Not used.</span></span>

### <a name="file-open"></a><span data-ttu-id="c19de-716">파일 열기</span><span class="sxs-lookup"><span data-stu-id="c19de-716">File Open</span></span> 

#### <a name="fx_file_open"></a><span data-ttu-id="c19de-717">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="c19de-717">fx_file_open</span></span>

<span data-ttu-id="c19de-718">**아이콘** ![파일 열기 아이콘](./media/user-guide/fx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-718">**Icon** ![File open icon](./media/user-guide/fx-events/image42.png)</span></span>

<span data-ttu-id="c19de-719">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-719">**Description**</span></span>

<span data-ttu-id="c19de-720">이 이벤트는 파일 열기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-720">This event represents a file open event.</span></span>

<span data-ttu-id="c19de-721">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-721">**Information Fields**</span></span> 

- <span data-ttu-id="c19de-722">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-722">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-723">정보 필드 2: 파일 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-723">Info Field 2: Pointer to the file control block.</span></span>
- <span data-ttu-id="c19de-724">정보 필드 3: 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-724">Info Field 3: Pointer to file name.</span></span>
- <span data-ttu-id="c19de-725">정보 필드 4: 다음과 같은 열기 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-725">Info Field 4: Open type:</span></span>

  |  <span data-ttu-id="c19de-726">열기 유형</span><span class="sxs-lookup"><span data-stu-id="c19de-726">Open Type</span></span>                        | <span data-ttu-id="c19de-727">값</span><span class="sxs-lookup"><span data-stu-id="c19de-727">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="c19de-728">읽기를 위한 열기</span><span class="sxs-lookup"><span data-stu-id="c19de-728">Open for Read</span></span>                    | <span data-ttu-id="c19de-729">(0x00)</span><span class="sxs-lookup"><span data-stu-id="c19de-729">(0x00)</span></span>  |
  |  <span data-ttu-id="c19de-730">쓰기를 위한 열기</span><span class="sxs-lookup"><span data-stu-id="c19de-730">Open for Write</span></span>                   | <span data-ttu-id="c19de-731">(0x01)</span><span class="sxs-lookup"><span data-stu-id="c19de-731">(0x01)</span></span>  |
  |  <span data-ttu-id="c19de-732">읽기를 위한 빠른 열기</span><span class="sxs-lookup"><span data-stu-id="c19de-732">Fast Open for Read</span></span>               | <span data-ttu-id="c19de-733">(0x02)</span><span class="sxs-lookup"><span data-stu-id="c19de-733">(0x02)</span></span>  |

### <a name="file-read"></a><span data-ttu-id="c19de-734">파일 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-734">File Read</span></span> 

#### <a name="fx_file_read"></a><span data-ttu-id="c19de-735">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="c19de-735">fx_file_read</span></span>

<span data-ttu-id="c19de-736">**아이콘** ![파일 읽기 아이콘](./media/user-guide/fx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-736">**Icon** ![File read icon](./media/user-guide/fx-events/image43.png)</span></span>

<span data-ttu-id="c19de-737">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-737">**Description**</span></span>

<span data-ttu-id="c19de-738">이 이벤트는 파일 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-738">This event represents a file read event.</span></span>

<span data-ttu-id="c19de-739">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-739">**Information Fields**</span></span>

- <span data-ttu-id="c19de-740">정보 필드 1: 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-740">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="c19de-741">정보 필드 2: 버퍼 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-741">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="c19de-742">정보 필드 3: 요청 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-742">Info Field 3: Request size.</span></span>
- <span data-ttu-id="c19de-743">정보 필드 4: 읽은 실제 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-743">Info Field 4: Actual size read.</span></span>

### <a name="file-relative-seek"></a><span data-ttu-id="c19de-744">파일 상대 검색</span><span class="sxs-lookup"><span data-stu-id="c19de-744">File Relative Seek</span></span> 

#### <a name="fx_file_relative_seek"></a><span data-ttu-id="c19de-745">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="c19de-745">fx_file_relative_seek</span></span>

<span data-ttu-id="c19de-746">**아이콘** ![파일 상대 검색 아이콘](./media/user-guide/fx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-746">**Icon** ![File relative seek icon](./media/user-guide/fx-events/image44.png)</span></span>

<span data-ttu-id="c19de-747">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-747">**Description**</span></span>

<span data-ttu-id="c19de-748">이 이벤트는 파일 상대 검색 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-748">This event represents a file relative seek event.</span></span>

<span data-ttu-id="c19de-749">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-749">**Information Fields**</span></span>

- <span data-ttu-id="c19de-750">정보 필드 1: 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-750">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="c19de-751">정보 필드 2: 바이트 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-751">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="c19de-752">정보 필드 3: 다음에서 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-752">Info Field 3: Seek from:</span></span>

  | <span data-ttu-id="c19de-753">이벤트</span><span class="sxs-lookup"><span data-stu-id="c19de-753">Event</span></span>                             | <span data-ttu-id="c19de-754">값</span><span class="sxs-lookup"><span data-stu-id="c19de-754">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="c19de-755">시작부터</span><span class="sxs-lookup"><span data-stu-id="c19de-755">From Beginning</span></span>                   | <span data-ttu-id="c19de-756">(0x00)</span><span class="sxs-lookup"><span data-stu-id="c19de-756">(0x00)</span></span>  |
  |  <span data-ttu-id="c19de-757">끝부터</span><span class="sxs-lookup"><span data-stu-id="c19de-757">From End</span></span>                         | <span data-ttu-id="c19de-758">(0x01)</span><span class="sxs-lookup"><span data-stu-id="c19de-758">(0x01)</span></span>  | 
  |  <span data-ttu-id="c19de-759">앞으로</span><span class="sxs-lookup"><span data-stu-id="c19de-759">Forward</span></span>                          | <span data-ttu-id="c19de-760">(0x02)</span><span class="sxs-lookup"><span data-stu-id="c19de-760">(0x02)</span></span>  |
  |  <span data-ttu-id="c19de-761">뒤로</span><span class="sxs-lookup"><span data-stu-id="c19de-761">Backward</span></span>                         | <span data-ttu-id="c19de-762">(0x03)</span><span class="sxs-lookup"><span data-stu-id="c19de-762">(0x03)</span></span>  |
- <span data-ttu-id="c19de-763">정보 필드 4: 이전 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-763">Info Field 4: Previous offset.</span></span>

### <a name="file-rename"></a><span data-ttu-id="c19de-764">파일 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="c19de-764">File Rename</span></span> 

#### <a name="fx_file_rename"></a><span data-ttu-id="c19de-765">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="c19de-765">fx_file_rename</span></span>

<span data-ttu-id="c19de-766">**아이콘** ![파일 이름 바꾸기 아이콘](./media/user-guide/fx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-766">**Icon** ![File rename icon](./media/user-guide/fx-events/image45.png)</span></span>

<span data-ttu-id="c19de-767">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-767">**Description**</span></span>

<span data-ttu-id="c19de-768">이 이벤트는 파일 이름 바꾸기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-768">This event represents a file rename event.</span></span>

<span data-ttu-id="c19de-769">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-769">**Information Fields**</span></span>

- <span data-ttu-id="c19de-770">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-770">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-771">정보 필드 2: 이전 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-771">Info Field 2: Pointer to old file name.</span></span>
- <span data-ttu-id="c19de-772">정보 필드 3: 새 파일 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-772">Info Field 3: Pointer to new file name.</span></span>
- <span data-ttu-id="c19de-773">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-773">Info Field 4: Not used.</span></span>

### <a name="file-seek"></a><span data-ttu-id="c19de-774">파일 검색</span><span class="sxs-lookup"><span data-stu-id="c19de-774">File Seek</span></span> 

#### <a name="fx_file_seek"></a><span data-ttu-id="c19de-775">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="c19de-775">fx_file_seek</span></span>

<span data-ttu-id="c19de-776">**아이콘** ![파일 검색 아이콘](./media/user-guide/fx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-776">**Icon** ![File seek icon](./media/user-guide/fx-events/image46.png)</span></span>

<span data-ttu-id="c19de-777">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-777">**Description**</span></span>

<span data-ttu-id="c19de-778">이 이벤트는 파일 검색 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-778">This event represents a file seek event.</span></span>

<span data-ttu-id="c19de-779">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-779">**Information Fields**</span></span> 

- <span data-ttu-id="c19de-780">정보 필드 1: 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-780">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="c19de-781">정보 필드 2: 바이트 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-781">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="c19de-782">정보 필드 3: 이전 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-782">Info Field 3: Previous offset.</span></span>
- <span data-ttu-id="c19de-783">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-783">Info Field 4: Not used.</span></span>

### <a name="file-truncate"></a><span data-ttu-id="c19de-784">파일 자르기</span><span class="sxs-lookup"><span data-stu-id="c19de-784">File Truncate</span></span> 

#### <a name="fx_file_truncate"></a><span data-ttu-id="c19de-785">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="c19de-785">fx_file_truncate</span></span>

<span data-ttu-id="c19de-786">**아이콘** ![파일 자르기 아이콘](./media/user-guide/fx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-786">**Icon** ![File truncate icon](./media/user-guide/fx-events/image47.png)</span></span>

<span data-ttu-id="c19de-787">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-787">**Description**</span></span>

<span data-ttu-id="c19de-788">이 이벤트는 파일 자르기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-788">This event represents a file truncate event.</span></span>

<span data-ttu-id="c19de-789">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-789">**Information Fields**</span></span>

- <span data-ttu-id="c19de-790">정보 필드 1: 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-790">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="c19de-791">정보 필드 2: 요청된 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-791">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="c19de-792">정보 필드 3: 이전 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-792">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="c19de-793">정보 필드 4: 새 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-793">Info Field 4: New size.</span></span>

### <a name="file-truncate-release"></a><span data-ttu-id="c19de-794">파일 자르기 해제</span><span class="sxs-lookup"><span data-stu-id="c19de-794">File Truncate Release</span></span> 

#### <a name="fx_file_truncate_release"></a><span data-ttu-id="c19de-795">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="c19de-795">fx_file_truncate_release</span></span> 

<span data-ttu-id="c19de-796">**아이콘** ![파일 자르기 해제 아이콘](./media/user-guide/fx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-796">**Icon** ![File truncate release icon](./media/user-guide/fx-events/image48.png)</span></span>

<span data-ttu-id="c19de-797">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-797">**Description**</span></span>

<span data-ttu-id="c19de-798">이 이벤트는 파일 자르기 해제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-798">This event represents a file truncate release event.</span></span>

<span data-ttu-id="c19de-799">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-799">**Information Fields**</span></span>

- <span data-ttu-id="c19de-800">정보 필드 1: 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-800">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="c19de-801">정보 필드 2: 요청된 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-801">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="c19de-802">정보 필드 3: 이전 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-802">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="c19de-803">정보 필드 4: 새 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-803">Info Field 4: New size.</span></span>

### <a name="file-write"></a><span data-ttu-id="c19de-804">파일 쓰기</span><span class="sxs-lookup"><span data-stu-id="c19de-804">File Write</span></span> 

#### <a name="fx_file_write"></a><span data-ttu-id="c19de-805">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="c19de-805">fx_file_write</span></span> 

<span data-ttu-id="c19de-806">**아이콘** ![파일 쓰기 아이콘](./media/user-guide/fx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-806">**Icon** ![File write icon](./media/user-guide/fx-events/image49.png)</span></span>

<span data-ttu-id="c19de-807">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-807">**Description**</span></span>

<span data-ttu-id="c19de-808">이 이벤트는 파일 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-808">This event represents a file write event.</span></span>

<span data-ttu-id="c19de-809">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-809">**Information Fields**</span></span>

- <span data-ttu-id="c19de-810">정보 필드 1: 파일에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-810">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="c19de-811">정보 필드 2: 버퍼 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-811">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="c19de-812">정보 필드 3: 요청 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-812">Info Field 3: Request size.</span></span>
- <span data-ttu-id="c19de-813">정보 필드 4: 쓰여진 실제 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-813">Info Field 4: Actual size written.</span></span>

### <a name="media-abort"></a><span data-ttu-id="c19de-814">미디어 중단</span><span class="sxs-lookup"><span data-stu-id="c19de-814">Media Abort</span></span> 

#### <a name="fx_media_abort"></a><span data-ttu-id="c19de-815">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="c19de-815">fx_media_abort</span></span> 

<span data-ttu-id="c19de-816">**아이콘** ![미디어 중단 아이콘](./media/user-guide/fx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-816">**Icon** ![Media abort icon](./media/user-guide/fx-events/image50.png)</span></span>

<span data-ttu-id="c19de-817">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-817">**Description**</span></span>

<span data-ttu-id="c19de-818">이 이벤트는 미디어 중단 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-818">This event represents a media abort event.</span></span>

<span data-ttu-id="c19de-819">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-819">**Information Fields**</span></span>

- <span data-ttu-id="c19de-820">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-820">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-821">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-821">Info Field 2: Not used.</span></span>
- <span data-ttu-id="c19de-822">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-822">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-823">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-823">Info Field 4: Not used.</span></span>

### <a name="media-cache-invalidate"></a><span data-ttu-id="c19de-824">미디어 캐시 무효화</span><span class="sxs-lookup"><span data-stu-id="c19de-824">Media Cache Invalidate</span></span>

#### <a name="fx_media_cache_invalidate"></a><span data-ttu-id="c19de-825">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="c19de-825">fx_media_cache_invalidate</span></span>

<span data-ttu-id="c19de-826">**아이콘** ![미디어 캐시 무효화 아이콘](./media/user-guide/fx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-826">**Icon** ![Media cache invalidate icon](./media/user-guide/fx-events/image51.png)</span></span>

<span data-ttu-id="c19de-827">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-827">**Description**</span></span>

<span data-ttu-id="c19de-828">이 이벤트는 미디어 캐시 무효화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-828">This event represents a media cache invalidate event.</span></span>

<span data-ttu-id="c19de-829">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-829">**Information Fields**</span></span>

- <span data-ttu-id="c19de-830">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-830">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-831">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-831">Info Field 2: Not used.</span></span>
- <span data-ttu-id="c19de-832">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-832">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-833">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-833">Info Field 4: Not used.</span></span>

### <a name="media-check"></a><span data-ttu-id="c19de-834">미디어 검사</span><span class="sxs-lookup"><span data-stu-id="c19de-834">Media Check</span></span> 

#### <a name="fx_media_check"></a><span data-ttu-id="c19de-835">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="c19de-835">fx_media_check</span></span>

<span data-ttu-id="c19de-836">**아이콘** ![미디어 검사 아이콘](./media/user-guide/fx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-836">**Icon** ![Media check icon](./media/user-guide/fx-events/image52.png)</span></span>

<span data-ttu-id="c19de-837">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-837">**Description**</span></span>

<span data-ttu-id="c19de-838">이 이벤트는 미디어 검사 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-838">This event represents a media check event.</span></span>

<span data-ttu-id="c19de-839">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-839">**Information Fields**</span></span> 

- <span data-ttu-id="c19de-840">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-840">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-841">정보 필드 2: 스크래치 메모리 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-841">Info Field 2: Scratch memory pointer.</span></span>
- <span data-ttu-id="c19de-842">정보 필드 3: 스크래치 메모리 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-842">Info Field 3: Scratch memory size.</span></span>
- <span data-ttu-id="c19de-843">정보 필드 4: 다음과 같은 오류 비트 맵입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-843">Info Field 4: Errors bit map:</span></span>

  | <span data-ttu-id="c19de-844">오류 유형</span><span class="sxs-lookup"><span data-stu-id="c19de-844">Error type</span></span>                        | <span data-ttu-id="c19de-845">값</span><span class="sxs-lookup"><span data-stu-id="c19de-845">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="c19de-846">FAT 체인 오류</span><span class="sxs-lookup"><span data-stu-id="c19de-846">FAT Chain Error</span></span>                  | <span data-ttu-id="c19de-847">(0x01)</span><span class="sxs-lookup"><span data-stu-id="c19de-847">(0x01)</span></span>  |
  |  <span data-ttu-id="c19de-848">디렉터리 오류</span><span class="sxs-lookup"><span data-stu-id="c19de-848">Directory Error</span></span>                  | <span data-ttu-id="c19de-849">(0x02)</span><span class="sxs-lookup"><span data-stu-id="c19de-849">(0x02)</span></span>  |
  |  <span data-ttu-id="c19de-850">클러스터 손실 오류</span><span class="sxs-lookup"><span data-stu-id="c19de-850">Lost Cluster Error</span></span>               | <span data-ttu-id="c19de-851">(0x04)</span><span class="sxs-lookup"><span data-stu-id="c19de-851">(0x04)</span></span>  |
  |  <span data-ttu-id="c19de-852">파일 크기 오류</span><span class="sxs-lookup"><span data-stu-id="c19de-852">File Size Error</span></span>                  | <span data-ttu-id="c19de-853">(0x08)</span><span class="sxs-lookup"><span data-stu-id="c19de-853">(0x08)</span></span>  |

### <a name="media-close"></a><span data-ttu-id="c19de-854">미디어 닫기</span><span class="sxs-lookup"><span data-stu-id="c19de-854">Media Close</span></span> 

#### <a name="fx_media_close"></a><span data-ttu-id="c19de-855">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="c19de-855">fx_media_close</span></span>

<span data-ttu-id="c19de-856">**아이콘** ![미디어 닫기 아이콘](./media/user-guide/fx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-856">**Icon** ![Media Close icon](./media/user-guide/fx-events/image53.png)</span></span>

<span data-ttu-id="c19de-857">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-857">**Description**</span></span>

<span data-ttu-id="c19de-858">이 이벤트는 미디어 닫기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-858">This event represents a media close event.</span></span>

<span data-ttu-id="c19de-859">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-859">**Information Fields**</span></span> 

- <span data-ttu-id="c19de-860">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-860">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-861">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-861">Info Field 2: Not used.</span></span>
- <span data-ttu-id="c19de-862">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-862">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-863">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-863">Info Field 4: Not used.</span></span>

### <a name="media-flush"></a><span data-ttu-id="c19de-864">미디어 플러시</span><span class="sxs-lookup"><span data-stu-id="c19de-864">Media Flush</span></span> 

#### <a name="fx_media_flush"></a><span data-ttu-id="c19de-865">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="c19de-865">fx_media_flush</span></span>

<span data-ttu-id="c19de-866">**아이콘** ![미디어 플러시 아이콘](./media/user-guide/fx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-866">**Icon** ![Media flush icon](./media/user-guide/fx-events/image54.png)</span></span>

<span data-ttu-id="c19de-867">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-867">**Description**</span></span>

<span data-ttu-id="c19de-868">이 이벤트는 미디어 플러시 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-868">This event represents a media flush event.</span></span>

<span data-ttu-id="c19de-869">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-869">**Information Fields**</span></span>

- <span data-ttu-id="c19de-870">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-870">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-871">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-871">Info Field 2: Not used.</span></span>
- <span data-ttu-id="c19de-872">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-872">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-873">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-873">Info Field 4: Not used.</span></span>

### <a name="media-format"></a><span data-ttu-id="c19de-874">미디어 형식</span><span class="sxs-lookup"><span data-stu-id="c19de-874">Media Format</span></span> 

#### <a name="fx_media_format"></a><span data-ttu-id="c19de-875">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="c19de-875">fx_media_format</span></span>

<span data-ttu-id="c19de-876">**아이콘** ![미디어 형식 아이콘](./media/user-guide/fx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-876">**Icon** ![Media format icon](./media/user-guide/fx-events/image55.png)</span></span>

<span data-ttu-id="c19de-877">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-877">**Description**</span></span>

<span data-ttu-id="c19de-878">이 이벤트는 미디어 형식 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-878">This event represents a media format event.</span></span>

<span data-ttu-id="c19de-879">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-879">**Information Fields**</span></span>

- <span data-ttu-id="c19de-880">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-880">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-881">정보 필드 2: 루트 항목 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-881">Info Field 2: Number of root entries.</span></span>
- <span data-ttu-id="c19de-882">정보 필드 3: 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-882">Info Field 3: Sectors.</span></span>
- <span data-ttu-id="c19de-883">정보 필드 4: 클러스터당 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-883">Info Field 4: Sectors per cluster.</span></span>

### <a name="media-open"></a><span data-ttu-id="c19de-884">미디어 열기</span><span class="sxs-lookup"><span data-stu-id="c19de-884">Media Open</span></span> 

#### <a name="fx_media_open"></a><span data-ttu-id="c19de-885">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="c19de-885">fx_media_open</span></span>

<span data-ttu-id="c19de-886">**아이콘** ![미디어 열기 아이콘](./media/user-guide/fx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-886">**Icon** ![Media open icon](./media/user-guide/fx-events/image56.png)</span></span>

<span data-ttu-id="c19de-887">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-887">**Description**</span></span>

<span data-ttu-id="c19de-888">이 이벤트는 미디어 열기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-888">This event represents a media open event.</span></span>

<span data-ttu-id="c19de-889">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-889">**Information Fields**</span></span>

- <span data-ttu-id="c19de-890">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-890">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-891">정보 필드 2: 미디어 드라이버 항목에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-891">Info Field 2: Pointer to media driver entry.</span></span>
- <span data-ttu-id="c19de-892">정보 필드 3: 메모리 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-892">Info Field 3: Memory pointer.</span></span>
- <span data-ttu-id="c19de-893">정보 필드 4: 메모리 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-893">Info Field 4: Memory size.</span></span>

### <a name="media-read-media-read"></a><span data-ttu-id="c19de-894">미디어 읽기 미디어 읽기</span><span class="sxs-lookup"><span data-stu-id="c19de-894">Media Read Media Read</span></span> 

#### <a name="fx_media_read"></a><span data-ttu-id="c19de-895">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="c19de-895">fx_media_read</span></span>

<span data-ttu-id="c19de-896">**아이콘** ![미디어 읽기 아이콘](./media/user-guide/fx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-896">**Icon** ![Media read icon](./media/user-guide/fx-events/image57.png)</span></span>

<span data-ttu-id="c19de-897">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-897">**Description**</span></span>

<span data-ttu-id="c19de-898">이 이벤트는 미디어 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-898">This event represents a media read event.</span></span>

<span data-ttu-id="c19de-899">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-899">**Information Fields**</span></span>

- <span data-ttu-id="c19de-900">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-900">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-901">정보 필드 2: 논리 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-901">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="c19de-902">정보 필드 3: 버퍼 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-902">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="c19de-903">정보 필드 4: 읽은 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-903">Info Field 4: Bytes read.</span></span>

### <a name="media-space-available"></a><span data-ttu-id="c19de-904">사용 가능한 미디어 공간</span><span class="sxs-lookup"><span data-stu-id="c19de-904">Media Space Available</span></span> 

#### <a name="fx_media_space_available"></a><span data-ttu-id="c19de-905">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="c19de-905">fx_media_space_available</span></span>

<span data-ttu-id="c19de-906">**아이콘** ![사용 가능한 미디어 공간 아이콘](./media/user-guide/fx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-906">**Icon** ![Media space available icon](./media/user-guide/fx-events/image58.png)</span></span>

<span data-ttu-id="c19de-907">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-907">**Description**</span></span>

<span data-ttu-id="c19de-908">이 이벤트는 사용 가능한 미디어 공간 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-908">This event represents a media space available event.</span></span>

<span data-ttu-id="c19de-909">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-909">**Information Fields**</span></span> 

- <span data-ttu-id="c19de-910">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-910">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-911">정보 필드 2: 사용 가능한 바이트 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-911">Info Field 2: Available bytes pointer.</span></span>
- <span data-ttu-id="c19de-912">정보 필드 3: 사용 가능한 클러스터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-912">Info Field 3: Number of free clusters.</span></span>
- <span data-ttu-id="c19de-913">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-913">Info Field 4: Not used.</span></span>

### <a name="media-volume-get"></a><span data-ttu-id="c19de-914">미디어 볼륨 가져오기</span><span class="sxs-lookup"><span data-stu-id="c19de-914">Media Volume Get</span></span> 

#### <a name="fx_media_volume_get"></a><span data-ttu-id="c19de-915">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="c19de-915">fx_media_volume_get</span></span>

<span data-ttu-id="c19de-916">**아이콘** ![미디어 볼륨 가져오기 아이콘](./media/user-guide/fx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-916">**Icon** ![Media volume get icon](./media/user-guide/fx-events/image59.png)</span></span>

<span data-ttu-id="c19de-917">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-917">**Description**</span></span>

<span data-ttu-id="c19de-918">이 이벤트는 미디어 볼륨 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-918">This event represents a media volume get event.</span></span>

<span data-ttu-id="c19de-919">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-919">**Information Fields**</span></span>

- <span data-ttu-id="c19de-920">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-920">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-921">정보 필드 2: 볼륨 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-921">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="c19de-922">정보 필드 3: 볼륨 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-922">Info Field 3: Volume source.</span></span>
- <span data-ttu-id="c19de-923">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-923">Info Field 4: Not used.</span></span>

### <a name="media-volume-set"></a><span data-ttu-id="c19de-924">미디어 볼륨 설정</span><span class="sxs-lookup"><span data-stu-id="c19de-924">Media Volume Set</span></span> 

#### <a name="fx_media_volume_set"></a><span data-ttu-id="c19de-925">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="c19de-925">fx_media_volume_set</span></span>

<span data-ttu-id="c19de-926">**아이콘** ![미디어 볼륨 설정 아이콘](./media/user-guide/fx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-926">**Icon** ![Media volume set icon](./media/user-guide/fx-events/image60.png)</span></span>

<span data-ttu-id="c19de-927">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-927">**Description**</span></span>

<span data-ttu-id="c19de-928">이 이벤트는 미디어 볼륨 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-928">This event represents a media volume set event.</span></span>

<span data-ttu-id="c19de-929">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-929">**Information Fields**</span></span> 
- <span data-ttu-id="c19de-930">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-930">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-931">정보 필드 2: 볼륨 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-931">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="c19de-932">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-932">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-933">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-933">Info Field 4: Not used.</span></span>

### <a name="media-write"></a><span data-ttu-id="c19de-934">미디어 쓰기</span><span class="sxs-lookup"><span data-stu-id="c19de-934">Media Write</span></span> 

#### <a name="fx_media_write"></a><span data-ttu-id="c19de-935">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="c19de-935">fx_media_write</span></span>

<span data-ttu-id="c19de-936">**아이콘** ![미디어 쓰기 아이콘](./media/user-guide/fx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-936">**Icon** ![Media write icon](./media/user-guide/fx-events/image61.png)</span></span>

<span data-ttu-id="c19de-937">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-937">**Description**</span></span>

<span data-ttu-id="c19de-938">이 이벤트는 미디어 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-938">This event represents a media write event.</span></span>

<span data-ttu-id="c19de-939">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-939">**Information Fields**</span></span>

- <span data-ttu-id="c19de-940">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-940">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-941">정보 필드 2: 논리 섹터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-941">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="c19de-942">정보 필드 3: 버퍼 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-942">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="c19de-943">정보 필드 4: 쓰여진 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-943">Info Field 4: Bytes written.</span></span>

### <a name="system-date-get"></a><span data-ttu-id="c19de-944">시스템 날짜 가져오기</span><span class="sxs-lookup"><span data-stu-id="c19de-944">System Date Get</span></span> 

#### <a name="fx_system_date_get"></a><span data-ttu-id="c19de-945">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="c19de-945">fx_system_date_get</span></span> 

<span data-ttu-id="c19de-946">**아이콘** ![시스템 날짜 가져오기 아이콘](./media/user-guide/fx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-946">**Icon** ![System date get icon](./media/user-guide/fx-events/image62.png)</span></span>

<span data-ttu-id="c19de-947">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-947">**Description**</span></span>

<span data-ttu-id="c19de-948">이 이벤트는 시스템 날짜 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-948">This event represents a system date get event.</span></span>

<span data-ttu-id="c19de-949">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-949">**Information Fields**</span></span>

- <span data-ttu-id="c19de-950">정보 필드 1: 연도입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-950">Info Field 1: Year.</span></span>
- <span data-ttu-id="c19de-951">정보 필드 2: 월입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-951">Info Field 2: Month.</span></span>
- <span data-ttu-id="c19de-952">정보 필드 3: 일입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-952">Info Field 3: Day.</span></span>
- <span data-ttu-id="c19de-953">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-953">Info Field 4: Not used.</span></span>

### <a name="system-date-set"></a><span data-ttu-id="c19de-954">시스템 날짜 설정</span><span class="sxs-lookup"><span data-stu-id="c19de-954">System Date Set</span></span> 

#### <a name="fx_system_date_set"></a><span data-ttu-id="c19de-955">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="c19de-955">fx_system_date_set</span></span> 

<span data-ttu-id="c19de-956">**아이콘** ![시스템 날짜 설정 아이콘](./media/user-guide/fx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-956">**Icon** ![System date set icon](./media/user-guide/fx-events/image63.png)</span></span>

<span data-ttu-id="c19de-957">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-957">**Description**</span></span>

<span data-ttu-id="c19de-958">이 이벤트는 시스템 날짜 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-958">This event represents a system date set event.</span></span>

<span data-ttu-id="c19de-959">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-959">**Information Fields**</span></span>

- <span data-ttu-id="c19de-960">정보 필드 1: 연도입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-960">Info Field 1: Year.</span></span>
- <span data-ttu-id="c19de-961">정보 필드 2: 월입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-961">Info Field 2: Month.</span></span>
- <span data-ttu-id="c19de-962">정보 필드 3: 일입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-962">Info Field 3: Day.</span></span>
- <span data-ttu-id="c19de-963">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-963">Info Field 4: Not used.</span></span>

### <a name="system-initialize"></a><span data-ttu-id="c19de-964">시스템 초기화</span><span class="sxs-lookup"><span data-stu-id="c19de-964">System Initialize</span></span> 

#### <a name="fx_system_initialize"></a><span data-ttu-id="c19de-965">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="c19de-965">fx_system_initialize</span></span> 

<span data-ttu-id="c19de-966">**아이콘** ![시스템 초기화 아이콘](./media/user-guide/fx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-966">**Icon** ![System initialize icon](./media/user-guide/fx-events/image64.png)</span></span>

<span data-ttu-id="c19de-967">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-967">**Description**</span></span>

<span data-ttu-id="c19de-968">이 이벤트는 시스템 초기화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-968">This event represents a system initialize event.</span></span>

<span data-ttu-id="c19de-969">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-969">**Information Fields**</span></span>

- <span data-ttu-id="c19de-970">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-970">Info Field 1: Not used.</span></span>
- <span data-ttu-id="c19de-971">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-971">Info Field 2: Not used.</span></span>
- <span data-ttu-id="c19de-972">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-972">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-973">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-973">Info Field 4: Not used.</span></span>

### <a name="system-time-get"></a><span data-ttu-id="c19de-974">시스템 시간 가져오기</span><span class="sxs-lookup"><span data-stu-id="c19de-974">System Time Get</span></span> 

#### <a name="fx_system_time_get"></a><span data-ttu-id="c19de-975">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="c19de-975">fx_system_time_get</span></span> 

<span data-ttu-id="c19de-976">**아이콘** ![시스템 시간 가져오기 아이콘](./media/user-guide/fx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-976">**Icon** ![System time get icon](./media/user-guide/fx-events/image65.png)</span></span>

<span data-ttu-id="c19de-977">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-977">**Description**</span></span>

<span data-ttu-id="c19de-978">이 이벤트는 시스템 시간 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-978">This event represents a system time get event.</span></span>

<span data-ttu-id="c19de-979">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-979">**Information Fields**</span></span> 

- <span data-ttu-id="c19de-980">정보 필드 1: 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-980">Info Field 1: Hour.</span></span>
- <span data-ttu-id="c19de-981">정보 필드 2: 분입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-981">Info Field 2: Minute.</span></span>
- <span data-ttu-id="c19de-982">정보 필드 3: 초입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-982">Info Field 3: Second.</span></span>
- <span data-ttu-id="c19de-983">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-983">Info Field 4: Not used.</span></span>

### <a name="system-time-set"></a><span data-ttu-id="c19de-984">시스템 시간 설정</span><span class="sxs-lookup"><span data-stu-id="c19de-984">System Time Set</span></span> 

#### <a name="fx_system_time_set"></a><span data-ttu-id="c19de-985">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="c19de-985">fx_system_time_set</span></span> 

<span data-ttu-id="c19de-986">**아이콘** ![시스템 시간 설정 아이콘](./media/user-guide/fx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-986">**Icon** ![System time set icon](./media/user-guide/fx-events/image66.png)</span></span>

<span data-ttu-id="c19de-987">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-987">**Description**</span></span>

<span data-ttu-id="c19de-988">이 이벤트는 시스템 시간 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-988">This event represents a system time set event.</span></span>

<span data-ttu-id="c19de-989">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-989">**Information Fields**</span></span>

- <span data-ttu-id="c19de-990">정보 필드 1: 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-990">Info Field 1: Hour.</span></span>
- <span data-ttu-id="c19de-991">정보 필드 2: 분입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-991">Info Field 2: Minute.</span></span>
- <span data-ttu-id="c19de-992">정보 필드 3: 초입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-992">Info Field 3: Second.</span></span>
- <span data-ttu-id="c19de-993">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-993">Info Field 4: Not used.</span></span>

### <a name="unicode-directory-create"></a><span data-ttu-id="c19de-994">유니코드 디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="c19de-994">Unicode Directory Create</span></span> 

#### <a name="fx_unicode_directory_create"></a><span data-ttu-id="c19de-995">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="c19de-995">fx_unicode_directory_create</span></span> 

<span data-ttu-id="c19de-996">**아이콘** ![유니코드 디렉터리 만들기 아이콘](./media/user-guide/fx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-996">**Icon** ![Unicode directory create icon](./media/user-guide/fx-events/image67.png)</span></span>

<span data-ttu-id="c19de-997">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-997">**Description**</span></span>

<span data-ttu-id="c19de-998">이 이벤트는 유니코드 디렉터리 만들기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-998">This event represents a Unicode directory create event.</span></span>

<span data-ttu-id="c19de-999">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-999">**Information Fields**</span></span> 

- <span data-ttu-id="c19de-1000">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1000">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-1001">정보 필드 2: 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1001">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="c19de-1002">정보 필드 3: 유니코드 이름의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1002">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="c19de-1003">정보 필드 4: 짧은 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1003">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-directory-rename"></a><span data-ttu-id="c19de-1004">유니코드 디렉터리 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="c19de-1004">Unicode Directory Rename</span></span> 

#### <a name="fx_unicode_directory_rename"></a><span data-ttu-id="c19de-1005">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="c19de-1005">fx_unicode_directory_rename</span></span>

<span data-ttu-id="c19de-1006">**아이콘** ![유니코드 디렉터리 이름 바꾸기 아이콘](./media/user-guide/fx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-1006">**Icon** ![Unicode directory rename icon](./media/user-guide/fx-events/image68.png)</span></span>

<span data-ttu-id="c19de-1007">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-1007">**Description**</span></span>

<span data-ttu-id="c19de-1008">이 이벤트는 유니코드 디렉터리 이름 바꾸기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1008">This event represents a Unicode directory rename event.</span></span>

<span data-ttu-id="c19de-1009">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-1009">**Information Fields**</span></span> 

- <span data-ttu-id="c19de-1010">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1010">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-1011">정보 필드 2: 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1011">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="c19de-1012">정보 필드 3: 유니코드 이름의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1012">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="c19de-1013">정보 필드 4: 짧은 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1013">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-create"></a><span data-ttu-id="c19de-1014">유니코드 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="c19de-1014">Unicode File Create</span></span> 

#### <a name="fx_unicode_file_create"></a><span data-ttu-id="c19de-1015">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="c19de-1015">fx_unicode_file_create</span></span>

<span data-ttu-id="c19de-1016">**아이콘** ![유니코드 파일 만들기 아이콘](./media/user-guide/fx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-1016">**Icon** ![Unicode file create icon](./media/user-guide/fx-events/image69.png)</span></span>

<span data-ttu-id="c19de-1017">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-1017">**Description**</span></span>

<span data-ttu-id="c19de-1018">이 이벤트는 유니코드 파일 만들기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1018">This event represents a Unicode file create event.</span></span>

<span data-ttu-id="c19de-1019">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-1019">**Information Fields**</span></span>

- <span data-ttu-id="c19de-1020">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1020">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-1021">정보 필드 2: 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1021">Info Field 2: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="c19de-1022">정보 필드 3: 유니코드 이름의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1022">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="c19de-1023">정보 필드 4: 짧은 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1023">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-rename"></a><span data-ttu-id="c19de-1024">유니코드 파일 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="c19de-1024">Unicode File Rename</span></span> 

#### <a name="fx_unicode_file_rename"></a><span data-ttu-id="c19de-1025">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="c19de-1025">fx_unicode_file_rename</span></span>

<span data-ttu-id="c19de-1026">**아이콘** ![유니코드 파일 이름 바꾸기 아이콘](./media/user-guide/fx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-1026">**Icon** ![Unicode file rename icon](./media/user-guide/fx-events/image70.png)</span></span>

<span data-ttu-id="c19de-1027">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-1027">**Description**</span></span>

<span data-ttu-id="c19de-1028">이 이벤트는 유니코드 파일 이름 바꾸기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1028">This event represents a Unicode file rename event.</span></span>

<span data-ttu-id="c19de-1029">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-1029">**Information Fields**</span></span>

- <span data-ttu-id="c19de-1030">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1030">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-1031">정보 필드 2: 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1031">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="c19de-1032">정보 필드 3: 유니코드 이름의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1032">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="c19de-1033">정보 필드 4: 짧은 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1033">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-length-get"></a><span data-ttu-id="c19de-1034">유니코드 길이 가져오기</span><span class="sxs-lookup"><span data-stu-id="c19de-1034">Unicode Length Get</span></span> 

#### <a name="fx_unicode_length_get"></a><span data-ttu-id="c19de-1035">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="c19de-1035">fx_unicode_length_get</span></span>

<span data-ttu-id="c19de-1036">**아이콘** ![유니코드 길이 가져오기 아이콘](./media/user-guide/fx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-1036">**Icon** ![Unicode length get icon](./media/user-guide/fx-events/image71.png)</span></span>

<span data-ttu-id="c19de-1037">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-1037">**Description**</span></span>

<span data-ttu-id="c19de-1038">이 이벤트는 유니코드 길이 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1038">This event represents a Unicode length get event.</span></span>

<span data-ttu-id="c19de-1039">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-1039">**Information Fields**</span></span>

- <span data-ttu-id="c19de-1040">정보 필드 1: 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1040">Info Field 1: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="c19de-1041">정보 필드 2: 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1041">Info Field 2: Length.</span></span>
- <span data-ttu-id="c19de-1042">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1042">Info Field 3: Not used.</span></span>
- <span data-ttu-id="c19de-1043">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1043">Info Field 4: Not used.</span></span>

### <a name="unicode-name-get"></a><span data-ttu-id="c19de-1044">유니코드 이름 가져오기</span><span class="sxs-lookup"><span data-stu-id="c19de-1044">Unicode Name Get</span></span> 

#### <a name="fx_unicode_name_get"></a><span data-ttu-id="c19de-1045">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="c19de-1045">fx_unicode_name_get</span></span>

<span data-ttu-id="c19de-1046">**아이콘** ![유니코드 이름 가져오기 아이콘](./media/user-guide/fx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-1046">**Icon** ![Unicode name get icon](./media/user-guide/fx-events/image72.png)</span></span>

<span data-ttu-id="c19de-1047">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-1047">**Description**</span></span>

<span data-ttu-id="c19de-1048">이 이벤트는 유니코드 이름 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1048">This event represents a Unicode name get event.</span></span>

<span data-ttu-id="c19de-1049">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-1049">**Information Fields**</span></span>

- <span data-ttu-id="c19de-1050">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1050">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-1051">정보 필드 2: 소스의 짧은 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1051">Info Field 2: Source short name.</span></span>
- <span data-ttu-id="c19de-1052">정보 필드 3: 대상 유니코드 이름 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1052">Info Field 3: Destination Unicode name pointer.</span></span>
- <span data-ttu-id="c19de-1053">정보 필드 4: 대상 유니코드 이름 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1053">Info Field 4: Destination Unicode name length.</span></span>

### <a name="unicode-short-name-get"></a><span data-ttu-id="c19de-1054">유니코드의 짧은 이름 가져오기</span><span class="sxs-lookup"><span data-stu-id="c19de-1054">Unicode Short Name Get</span></span> 

#### <a name="fx_unicode_short_name_get"></a><span data-ttu-id="c19de-1055">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="c19de-1055">fx_unicode_short_name_get</span></span>

<span data-ttu-id="c19de-1056">**아이콘** ![유니코드의 짧은 이름 가져오기 아이콘](./media/user-guide/fx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="c19de-1056">**Icon** ![Unicode short name get icon](./media/user-guide/fx-events/image73.png)</span></span>

<span data-ttu-id="c19de-1057">**설명**</span><span class="sxs-lookup"><span data-stu-id="c19de-1057">**Description**</span></span>

<span data-ttu-id="c19de-1058">이 이벤트는 유니코드의 짧은 이름 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1058">This event represents a Unicode short name get event.</span></span>

<span data-ttu-id="c19de-1059">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="c19de-1059">**Information Fields**</span></span>

- <span data-ttu-id="c19de-1060">정보 필드 1: 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1060">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="c19de-1061">정보 필드 2: 소스 유니코드 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1061">Info Field 2: Pointer to source Unicode name.</span></span>
- <span data-ttu-id="c19de-1062">정보 필드 3: 유니코드 이름의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1062">Info Field 3: Length of Unicode name.</span></span>
- <span data-ttu-id="c19de-1063">정보 필드 4: 짧은 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c19de-1063">Info Field 4: Pointer to short name.</span></span>