---
title: 7장 - Azure RTOS FileX 추적 이벤트
description: 이 장에서는 Azure RTOS FileX 이벤트에 대해 설명합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8668f0867e205afdeab112dfedd257998a5f5b7ff256f27298072dde3e9019b0
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116803305"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a>7장 - Azure RTOS FileX 추적 이벤트

이 장에서는 Azure RTOS FileX 이벤트에 대해 설명합니다. 

## <a name="list-of-events-and-icons"></a>이벤트 및 아이콘 목록

**다음은 TraceX에 의해 표시되는 FileX 이벤트 목록입니다.**

다음에서는 각 이벤트에 대해 설명합니다.

| **아이콘**                         | **의미**                               |
| -------------------------------- | ----------------------------------------- |
| ![내부 논리 섹터 캐시 누락 아이콘](./media/user-guide/fx-events/image1.png)    | 내부 논리 섹터 캐시 누락 |
| ![내부 디렉터리 캐시 누락 아이콘](./media/user-guide/fx-events/image2.png)    | 내부 디렉터리 캐시 누락 |
| ![내부 미디어 플러시 아이콘](./media/user-guide/fx-events/image3.png)    | 내부 미디어 플러시 |
| ![내부 디렉터리 항목 읽기 아이콘](./media/user-guide/fx-events/image4.png)    | 내부 디렉터리 항목 읽기 |
| ![내부 디렉터리 항목 쓰기 아이콘](./media/user-guide/fx-events/image5.png)    | 내부 디렉터리 항목 쓰기 |
| ![내부 I/O 드라이버 읽기 아이콘](./media/user-guide/fx-events/image6.png)    | 내부 I/O 드라이버 읽기 |
| ![내부 I/O 드라이버 쓰기 아이콘](./media/user-guide/fx-events/image7.png)    | 내부 I/O 드라이버 쓰기 |
| ![내부 I/O 드라이버 플러시 아이콘](./media/user-guide/fx-events/image8.png)    | 내부 I/O 드라이버 플러시 |
| ![내부 I/O 드라이버 중단 아이콘](./media/user-guide/fx-events/image9.png)    | 내부 I/O 드라이버 중단 |
| ![내부 I/O 드라이버 초기화 아이콘](./media/user-guide/fx-events/image10.png)    | 내부 I/O 드라이버 초기화 |
| ![내부 I/O 드라이버 부팅 읽기 아이콘](./media/user-guide/fx-events/image11.png)    | 내부 I/O 드라이버 부팅 읽기 |
| ![내부 I/O 드라이버 해제 섹터 아이콘](./media/user-guide/fx-events/image12.png)    | 내부 I/O 드라이버 해제 섹터 |
| ![내부 I/O 드라이버 부팅 쓰기 아이콘](./media/user-guide/fx-events/image13.png)    | 내부 I/O 드라이버 부팅 쓰기 |
| ![내부 I/O 드라이버 초기화 취소 아이콘](./media/user-guide/fx-events/image14.png)    | 내부 I/O 드라이버 초기화 취소 |
| ![디렉터리 특성 읽기 아이콘](./media/user-guide/fx-events/image15.png)    | **디렉터리 특성 읽기**(*fx_directory_attributes_read*) |
| ![디렉터리 특성 설정 아이콘](./media/user-guide/fx-events/image16.png)    | **디렉터리 특성 설정**(*fx_directory_attributes_set*) |
| ![디렉터리 만들기 아이콘](./media/user-guide/fx-events/image17.png)    | **디렉터리 만들기**(*fx_directory_create*) |
| ![디렉터리 기본값 가져오기 아이콘](./media/user-guide/fx-events/image18.png)    | **디렉터리 기본값 가져오기**(*fx_directory_default_get*) |
| ![디렉터리 기본값 설정 아이콘](./media/user-guide/fx-events/image19.png)    | **디렉터리 기본값 설정**(*fx_directory_default_set*) |
| ![디렉터리 삭제 아이콘](./media/user-guide/fx-events/image20.png)    | **디렉터리 삭제**(*fx_directory_delete*) |
| ![디렉터리의 첫 번째 항목 찾기 아이콘](./media/user-guide/fx-events/image21.png)    | **디렉터리의 첫 번째 항목 찾기**(*fx_directory_first_entry_find*) |
| ![디렉터리의 첫 번째 전체 항목 찾기 아이콘](./media/user-guide/fx-events/image22.png)    | **디렉터리의 첫 번째 전체 항목 찾기**(*fx_directory_first_full_entry_find*) |
| ![디렉터리 정보 가져오기 아이콘](./media/user-guide/fx-events/image23.png)    | **디렉터리 정보 가져오기**(*fx_directory_information_get*) |
| ![디렉터리 로컬 경로 지우기 아이콘](./media/user-guide/fx-events/image24.png)    | **디렉터리 로컬 경로 지우기**(*fx_directory_local_path_clear*) |
| ![디렉터리 로컬 경로 가져오기 아이콘](./media/user-guide/fx-events/image25.png)    | **디렉터리 로컬 경로 가져오기**(*fx_directory_local_path_get*) |
| ![디렉터리 로컬 경로 복원 아이콘](./media/user-guide/fx-events/image26.png)    | **디렉터리 로컬 경로 복원**(*fx_directory_local_path_restore*) |
| ![디렉터리 로컬 경로 설정 아이콘](./media/user-guide/fx-events/image27.png)    | **디렉터리 로컬 경로 설정**(*fx_directory_local_path_set*) |
| ![디렉터리의 긴 이름 가져오기 아이콘](./media/user-guide/fx-events/image28.png)    | **디렉터리의 긴 이름 가져오기**(*fx_directory_long_name_get*) |
| ![디렉터리 이름 테스트 아이콘](./media/user-guide/fx-events/image29.png)    | **디렉터리 이름 테스트**(*fx_directory_name_test*) |
| ![디렉터리의 다음 항목 찾기 아이콘](./media/user-guide/fx-events/image30.png)    | **디렉터리의 다음 항목 찾기**(*fx_directory_next_entry_find*) |
| ![디렉터리의 다음 전체 항목 찾기 아이콘](./media/user-guide/fx-events/image31.png)    | **디렉터리의 다음 전체 항목 찾기**(*fx_directory_next_full_entry_find*) |
| ![디렉터리 이름 바꾸기 아이콘](./media/user-guide/fx-events/image32.png)    | **디렉터리 이름 바꾸기**(*fx_directory_rename*) |
| ![디렉터리의 짧은 이름 가져오기 아이콘](./media/user-guide/fx-events/image33.png)    | **디렉터리의 짧은 이름 가져오기**(*fx_directory_short_name_get*) |
| ![파일 할당 아이콘](./media/user-guide/fx-events/image34.png)    | **파일 할당**(*fx_file_allocate*) |
| ![파일 특성 읽기 아이콘](./media/user-guide/fx-events/image35.png)    | **파일 특성 읽기**(*fx_file_attributes_read*) |
| ![파일 특성 설정 아이콘](./media/user-guide/fx-events/image36.png)    | **파일 특성 설정**(*fx_file_attributes_set*) |
| ![최선의 파일 할당 아이콘](./media/user-guide/fx-events/image37.png)    | **최선의 파일 할당**(*fx_file_best_effort_allocate*) |
| ![파일 닫기 아이콘](./media/user-guide/fx-events/image38.png)    | **파일 닫기**(*fx_file_close*) |
| ![파일 만들기 아이콘](./media/user-guide/fx-events/image39.png)    | **파일 만들기**(*fx_file_create*) |
| ![파일 날짜 시간 설정 아이콘](./media/user-guide/fx-events/image40.png)    | **파일 날짜 시간 설정**(*fx_file_date_time_set*) |
| ![파일 삭제 아이콘](./media/user-guide/fx-events/image41.png)    | **파일 삭제**(*fx_file_delete*) |
| ![파일 열기 아이콘](./media/user-guide/fx-events/image42.png)    | **파일 열기**(*fx_file_open*) |
| ![파일 읽기 아이콘](./media/user-guide/fx-events/image43.png)    | **파일 읽기**(*fx_file_read*) |
| ![파일 상대 검색 아이콘](./media/user-guide/fx-events/image44.png)    | **파일 상대 검색**(*fx_file_relative_seek*) |
| ![파일 이름 바꾸기 아이콘](./media/user-guide/fx-events/image45.png)    | **파일 이름 바꾸기**(*fx_file_rename*) |
| ![파일 검색 아이콘](./media/user-guide/fx-events/image46.png)    | **파일 검색**(*fx_file_seek*) |
| ![파일 자르기 아이콘](./media/user-guide/fx-events/image47.png)    | **파일 자르기**(*fx_file_truncate*) |
| ![파일 자르기 해제 아이콘](./media/user-guide/fx-events/image48.png)    | **파일 자르기 해제**(*fx_file_truncate_release*) |
| ![파일 쓰기 아이콘](./media/user-guide/fx-events/image49.png)    | **파일 쓰기**(*fx_file_write*) |
| ![미디어 중단 아이콘](./media/user-guide/fx-events/image50.png)    | **미디어 중단**(*fx_media_abort*) |
| ![미디어 캐시 무효화 아이콘](./media/user-guide/fx-events/image51.png)    | **미디어 캐시 무효화**(*fx_media_cache_invalidate*) |
| ![미디어 검사 아이콘](./media/user-guide/fx-events/image52.png)    | **미디어 검사**(*fx_media_check*) |
| ![\* 미디어 닫기 아이콘](./media/user-guide/fx-events/image53.png)    | **미디어 닫기**(*fx_media_close*) |
| ![미디어 플러시 아이콘](./media/user-guide/fx-events/image54.png)    | **미디어 플러시**(*fx_media_flush*) |
| ![미디어 형식 아이콘](./media/user-guide/fx-events/image55.png)    | **미디어 형식**(*fx_media_format*) |
| ![미디어 열기 아이콘](./media/user-guide/fx-events/image56.png)    | **미디어 열기**(*fx_media_open*) |
| ![미디어 읽기 아이콘](./media/user-guide/fx-events/image57.png)    | **미디어 읽기**(*fx_media_read*) |
| ![사용 가능한 미디어 공간 아이콘](./media/user-guide/fx-events/image58.png)    | **사용 가능한 미디어 공간**(*fx_media_space_available*) |
| ![미디어 볼륨 가져오기 아이콘](./media/user-guide/fx-events/image59.png)    | **미디어 볼륨 가져오기**(*fx_media_volume_get*) |
| ![미디어 볼륨 설정 아이콘](./media/user-guide/fx-events/image60.png)    | **미디어 볼륨 설정**(*fx_media_volume_set*) |
| ![미디어 쓰기 아이콘](./media/user-guide/fx-events/image61.png)    | **미디어 쓰기**(*fx_media_write*) |
| ![시스템 날짜 가져오기 아이콘](./media/user-guide/fx-events/image62.png)    | **시스템 날짜 가져오기**(*fx_system_date_get*) |
| ![시스템 날짜 설정 아이콘](./media/user-guide/fx-events/image63.png)    | **시스템 날짜 설정**(*fx_system_date_set*) |
| ![시스템 초기화 아이콘](./media/user-guide/fx-events/image64.png)    | **시스템 초기화**(*fx_system_initialize*) |
| ![시스템 시간 가져오기 아이콘](./media/user-guide/fx-events/image65.png)    | **시스템 시간 가져오기**(*fx_system_time_get*) |
| ![시스템 시간 설정 아이콘](./media/user-guide/fx-events/image66.png)    | **시스템 시간 설정**(*fx_system_time_set*) |
| ![유니코드 디렉터리 만들기 아이콘](./media/user-guide/fx-events/image67.png)    | **유니코드 디렉터리 만들기**(*fx_unicode_directory_create*) |
| ![유니코드 디렉터리 이름 바꾸기 아이콘](./media/user-guide/fx-events/image68.png)    | **유니코드 디렉터리 이름 바꾸기**(*fx_unicode_directory_rename*) |
| ![유니코드 파일 만들기 아이콘](./media/user-guide/fx-events/image69.png)    | **유니코드 파일 만들기**(*fx_unicode_file_create*) |
| ![유니코드 파일 이름 바꾸기 아이콘](./media/user-guide/fx-events/image70.png)    | **유니코드 파일 이름 바꾸기**(*fx_unicode_file_rename*) |
| ![유니코드 길이 가져오기 아이콘](./media/user-guide/fx-events/image71.png)    | **유니코드 길이 가져오기**(*fx_unicode_length_get*) |
| ![유니코드 이름 가져오기 아이콘](./media/user-guide/fx-events/image72.png)    | **유니코드 이름 가져오기**(*fx_unicode_name_get*) |
| ![유니코드의 짧은 이름 가져오기 아이콘](./media/user-guide/fx-events/image73.png)    | **유니코드의 짧은 이름 가져오기**(*fx_unicode_short_name_get*) |

## <a name="event-descriptions"></a>이벤트 설명

다음에서는 각 개별 이벤트에 대해 설명합니다.

### <a name="internal-logical-sector-cache-miss"></a>내부 논리 섹터 캐시 누락 

#### <a name="internal-logical-sector-cache-miss"></a>내부 논리 섹터 캐시 누락

**아이콘** ![내부 논리 섹터 캐시 누락 아이콘](./media/user-guide/fx-events/image1.png)

**설명**

이 이벤트는 내부 FileX 논리 섹터 캐시 누락을 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 섹터입니다.
- 정보 필드 3: 총 누락입니다.
- 정보 필드 4: 캐시 크기입니다.

### <a name="internal-directory-cache-miss"></a>내부 디렉터리 캐시 누락

#### <a name="internal-directory-cache-miss"></a>내부 디렉터리 캐시 누락

**아이콘** ![내부 디렉터리 캐시 누락 아이콘](./media/user-guide/fx-events/image2.png)

**설명** 

이 이벤트는 내부 FileX 디렉터리 캐시 누락을 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 총 누락입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-media-flush"></a>내부 미디어 플러시 

#### <a name="internal-media-flush"></a>내부 미디어 플러시

**아이콘** ![내부 미디어 플러시 아이콘](./media/user-guide/fx-events/image3.png)

**설명**

이 이벤트는 내부 FileX 미디어 플러시를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 더티 섹터 수입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.


### <a name="internal-directory-entry-read"></a>내부 디렉터리 항목 읽기 

#### <a name="internal-directory-entry-read"></a>내부 디렉터리 항목 읽기

**아이콘** ![내부 디렉터리 항목 읽기 아이콘](./media/user-guide/fx-events/image4.png)

**설명**

이 이벤트는 내부 FileX 디렉터리 항목 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-directory-entry-write"></a>내부 디렉터리 항목 쓰기

#### <a name="internal-directory-entry-write"></a>내부 디렉터리 항목 쓰기

**아이콘** ![내부 디렉터리 항목 쓰기 아이콘](./media/user-guide/fx-events/image5.png)

**설명**

이 이벤트는 내부 FileX 디렉터리 항목 쓰기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-read"></a>내부 I/O 드라이버 읽기 

#### <a name="internal-io-driver-read"></a>내부 I/O 드라이버 읽기 

**아이콘** ![내부 I/O 드라이버 읽기 아이콘](./media/user-guide/fx-events/image6.png)

**설명** 

이 이벤트는 내부 FileX I/O 드라이버 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 섹터입니다.
- 정보 필드 3: 섹터 수입니다.
- 정보 필드 4: 버퍼 포인터입니다.

### <a name="internal-io-driver-write"></a>내부 I/O 드라이버 쓰기 

#### <a name="internal-io-driver-write"></a>내부 I/O 드라이버 쓰기 

**아이콘** ![내부 I/O 드라이버 쓰기 아이콘](./media/user-guide/fx-events/image7.png)

**설명** 

이 이벤트는 내부 FileX I/O 드라이버 쓰기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 섹터입니다.
- 정보 필드 3: 섹터 수입니다.
- 정보 필드 4: 버퍼 포인터입니다.

### <a name="internal-io-driver-flush"></a>내부 I/O 드라이버 플러시 

#### <a name="internal-io-driver-flush"></a>내부 I/O 드라이버 플러시 

**아이콘** ![내부 I/O 드라이버 플러시 아이콘](./media/user-guide/fx-events/image8.png)

**설명** 

이 이벤트는 내부 FileX I/O 드라이버 플러시 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-abort"></a>내부 I/O 드라이버 중단 

#### <a name="internal-io-dirver-abort"></a>내부 I/O 드라이버 중단

**아이콘** ![내부 I/O 드라이버 중단 아이콘](./media/user-guide/fx-events/image9.png)

**설명**

이 이벤트는 내부 FileX I/O 드라이버 중단 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-initialize"></a>내부 I/O 드라이버 초기화 

#### <a name="internal-io-driver-initialize"></a>내부 I/O 드라이버 초기화 

**아이콘** ![내부 I/O 드라이버 초기화 아이콘](./media/user-guide/fx-events/image10.png)

**설명** 

이 이벤트는 내부 FileX I/O 드라이버 초기화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-boot-sector-read"></a>내부 I/O 드라이버 부팅 섹터 읽기 

#### <a name="internal-io-driver-boot-sector-read"></a>내부 I/O 드라이버 부팅 섹터 읽기 

**아이콘** ![내부 I/O 드라이버 부팅 섹터 읽기 아이콘](./media/user-guide/fx-events/image11.png)

**설명** 

이 이벤트는 내부 FileX I/O 드라이버 부팅 섹터 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 버퍼 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-release-sectors"></a>내부 I/O 드라이버 해제 섹터 

#### <a name="internal-io-driver-release-sectors"></a>내부 I/O 드라이버 해제 섹터 

**아이콘** ![내부 I/O 드라이버 해제 섹터 아이콘](./media/user-guide/fx-events/image12.png)

**설명** 

이 이벤트는 내부 FileX I/O 드라이버 해제 섹터 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 섹터입니다.
- 정보 필드 3: 섹터 수입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-boot-sector-write"></a>내부 I/O 드라이버 부팅 섹터 쓰기

#### <a name="internal-io-driver-boot-sector-write"></a>내부 I/O 드라이버 부팅 섹터 쓰기 

**아이콘** ![내부 I/O 드라이버 부팅 섹터 쓰기 아이콘](./media/user-guide/fx-events/image13.png)

**설명** 

이 이벤트는 내부 FileX I/O 드라이버 부팅 섹터 쓰기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 버퍼 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-un-initialize"></a>내부 I/O 드라이버 초기화 취소 

#### <a name="internal-io-driver-un-initialize"></a>내부 I/O 드라이버 초기화 취소 

**아이콘** ![내부 I/O 드라이버 초기화 취소 아이콘](./media/user-guide/fx-events/image14.png)

**설명** 

이 이벤트는 내부 FileX I/O 드라이버 초기화 취소 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.
</blockquote></td>

### <a name="directory-attributes-read"></a>디렉터리 특성 읽기 

#### <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read 

**아이콘** ![디렉터리 특성 읽기 아이콘](./media/user-guide/fx-events/image15.png)

**설명** 

이 이벤트는 디렉터리 특성 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 디렉터리 이름에 대한 포인터입니다.
- 정보 필드 3: 다음과 같은 특성 비트 맵입니다.

  | attribute                         | 값        |
  |---------------------------------- | --------|
  |  읽기 전용                        | (0x01)  |
  |  숨김                           | (0x02)  |
  |  시스템                           | (0x04)  |
  |  볼륨                           | (0x08)  |
  |  디렉터리                        | (0x10)  |
  |  보관                          | (0x20)  |
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-attributes-set"></a>디렉터리 특성 설정 

#### <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set 

**아이콘** ![특성 설정 아이콘](./media/user-guide/fx-events/image16.png)

**설명** 

이 이벤트는 디렉터리 특성 설정 이벤트 디렉터리를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 디렉터리 이름에 대한 포인터입니다.
- 정보 필드 3: 다음과 같은 특성 비트 맵입니다.

  |  attribute                        | 값        |
  |---------------------------------- | --------|
  |  읽기 전용                        | (0x01)  |
  |  숨김                           | (0x02)  |
  |  시스템                           | (0x04)  |
  |  보관                          | (0x20)  |
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-create"></a>디렉터리 만들기 

#### <a name="fx_directory_create"></a>fx_directory_create

**아이콘** ![디렉터리 만들기 아이콘](./media/user-guide/fx-events/image17.png)

**설명** 

이 이벤트는 디렉터리 만들기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 디렉터리 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-default-get"></a>디렉터리 기본값 가져오기 

#### <a name="fx_directory_default_get"></a>fx_directory_default_get 

**아이콘** ![디렉터리 기본값 가져오기 아이콘](./media/user-guide/fx-events/image18.png)

**설명** 

이 이벤트는 디렉터리 기본값 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 반환 경로 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-default-set"></a>디렉터리 기본값 설정 

#### <a name="fx_directory_default_set"></a>fx_directory_default_set 

**아이콘** ![디렉터리 기본값 설정 아이콘](./media/user-guide/fx-events/image19.png)

**설명** 

이 이벤트는 디렉터리 기본값 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 새 기본 경로 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-delete"></a>디렉터리 삭제 

#### <a name="fx_directory_delete"></a>fx_directory_delete

**아이콘** ![디렉터리 삭제 아이콘](./media/user-guide/fx-events/image20.png)

**설명** 

이 이벤트는 디렉터리 삭제 이벤트를 나타냅니다.

**정보 필드**
- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 디렉터리 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-first-entry-find"></a>디렉터리의 첫 번째 항목 찾기 

#### <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

**아이콘** ![디렉터리의 첫 번째 항목 찾기 아이콘](./media/user-guide/fx-events/image21.png)

**설명** 

이 이벤트는 디렉터리의 첫 번째 항목 찾기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 디렉터리 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-first-full-entry-find"></a>디렉터리의 첫 번째 전체 항목 찾기 

#### <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

**아이콘** ![디렉터리의 첫 번째 전체 항목 찾기 아이콘](./media/user-guide/fx-events/image22.png)

**설명** 

이 이벤트는 디렉터리의 첫 번째 전체 항목 찾기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 디렉터리 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-information-get"></a>디렉터리 정보 가져오기 

#### <a name="fx_directory_information_get"></a>fx_directory_information_get

**아이콘** ![디렉터리 정보 가져오기 아이콘](./media/user-guide/fx-events/image23.png)

**설명** 

이 이벤트는 디렉터리 정보 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 디렉터리 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-local-path-clear"></a>디렉터리 로컬 경로 지우기 

#### <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear

**아이콘** ![디렉터리 로컬 경로 지우기 아이콘](./media/user-guide/fx-events/image24.png)

**설명** 

이 이벤트는 디렉터리 로컬 경로 지우기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-local-path-get"></a>디렉터리 로컬 경로 가져오기 

#### <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get

**아이콘** ![디렉터리 로컬 경로 가져오기 아이콘](./media/user-guide/fx-events/image25.png)

**설명** 

이 이벤트는 디렉터리 로컬 경로 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 반환 경로 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-local-path-restore"></a>디렉터리 로컬 경로 복원 

#### <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore

**아이콘** ![디렉터리 로컬 경로 복원 아이콘](./media/user-guide/fx-events/image26.png)

**설명** 

이 이벤트는 디렉터리 로컬 경로 복원 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 로컬 경로 구조에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-local-path-set"></a>디렉터리 로컬 경로 설정 

#### <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

**아이콘** ![디렉터리 로컬 경로 설정 아이콘](./media/user-guide/fx-events/image27.png)

**설명** 

이 이벤트는 디렉터리 로컬 경로 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 로컬 경로 구조에 대한 포인터입니다.
- 정보 필드 3: 새 경로 이름에 대한 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-long-name-get"></a>디렉터리의 긴 이름 가져오기 

#### <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get

**아이콘** ![디렉터리의 긴 이름 가져오기 아이콘](./media/user-guide/fx-events/image28.png)

**설명** 

이 이벤트는 디렉터리의 긴 이름 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 짧은 파일 이름에 대한 포인터입니다.
- 정보 필드 3: 긴 파일 이름에 대한 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-name-test"></a>디렉터리 이름 테스트 

#### <a name="fx_directory_name_test"></a>fx_directory_name_test

**아이콘** ![디렉터리 이름 테스트 아이콘](./media/user-guide/fx-events/image29.png)

**설명** 

이 이벤트는 디렉터리 이름 테스트 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 디렉터리 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-next-entry-find"></a>디렉터리의 다음 항목 찾기 

#### <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find

**아이콘** ![디렉터리의 다음 항목 찾기 아이콘](./media/user-guide/fx-events/image30.png)

**설명** 

이 이벤트는 디렉터리의 다음 항목 찾기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 디렉터리 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-next-full-entry-find"></a>디렉터리의 다음 전체 항목 찾기 

#### <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find

**아이콘** ![디렉터리의 다음 전체 항목 찾기 아이콘](./media/user-guide/fx-events/image31.png)

**설명**

이 이벤트는 디렉터리의 다음 전체 항목 찾기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 디렉터리 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-rename"></a>디렉터리 이름 바꾸기 

#### <a name="fx_directory_rename-event"></a>fx_directory_rename event

**아이콘** ![디렉터리 이름 바꾸기 아이콘](./media/user-guide/fx-events/image32.png)

**설명**

이 이벤트는 디렉터리 이름 바꾸기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 이전 디렉터리 이름에 대한 포인터입니다.
- 정보 필드 3: 새 디렉터리 이름에 대한 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="directory-short-name-get"></a>디렉터리의 짧은 이름 가져오기 

#### <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get

**아이콘** ![디렉터리의 짧은 이름 가져오기 아이콘](./media/user-guide/fx-events/image33.png)

**설명**

이 이벤트는 디렉터리의 짧은 이름 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 긴 파일 이름에 대한 포인터입니다.
- 정보 필드 3: 짧은 파일 이름에 대한 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="file-allocate"></a>파일 할당 

#### <a name="fx_file_allocate"></a>fx_file_allocate

**아이콘** ![파일 할당 아이콘](./media/user-guide/fx-events/image34.png)

**설명**

이 이벤트는 파일 할당 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 파일에 대한 포인터입니다.
- 정보 필드 2: 요청된 크기입니다.
- 정보 필드 3: 현재 크기입니다.
- 정보 필드 4: 새 크기입니다.

### <a name="file-attributes-read"></a>파일 특성 읽기 

#### <a name="fx_file_attributes_read"></a>fx_file_attributes_read

**아이콘** ![파일 특성 읽기 아이콘](./media/user-guide/fx-events/image35.png)

**설명**

이 이벤트는 파일 특성 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다. 
- 정보 필드 2: 다음과 같은 특성 비트 맵입니다.

  |  특성                         | 값        |
  |---------------------------------- | --------|
  |  읽기 전용                        | (0x01)  |
  |  숨김                           | (0x02)  |
  |  시스템                           | (0x04)  |
  |  볼륨                           | (0x08)  |
  |  디렉터리                        | (0x10)  |
  |  보관                          | (0x20)  |
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="file-attributes-set"></a>파일 특성 설정 

#### <a name="fx_file_attributes_set"></a>fx_file_attributes_set

**아이콘** ![파일 특성 설정 아이콘](./media/user-guide/fx-events/image36.png)

**설명** 

이 이벤트는 파일 특성 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 파일 이름에 대한 포인터입니다. 
- 정보 필드 3: 다음과 같은 특성 비트 맵입니다.

  | attribute                         | 값        |
  |---------------------------------- | --------|
  |  읽기 전용                        | (0x01)  |
  |  숨김                           | (0x02)  |
  |  시스템                           | (0x04)  |
  |  보관                          | (0x20)  |
- 정보 필드 4: 사용되지 않습니다.

### <a name="file-best-effort-allocate"></a>최선의 파일 할당 

#### <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

**아이콘** ![최선의 파일 할당 아이콘](./media/user-guide/fx-events/image37.png)

**설명** 

이 이벤트는 최선의 파일 할당 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 파일에 대한 포인터입니다.
- 정보 필드 2: 요청된 크기입니다.
- 정보 필드 3: 할당된 실제 크기입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="file-close"></a>파일 닫기 

#### <a name="fx_file_close"></a>fx_file_close

**아이콘** ![파일 닫기 아이콘](./media/user-guide/fx-events/image38.png)

**설명** 

이 이벤트는 파일 닫기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 파일에 대한 포인터입니다.
- 정보 필드 2: 파일 크기입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="file-create"></a>파일 만들기

#### <a name="fx_file_create"></a>fx_file_create

**아이콘** ![파일 만들기 아이콘](./media/user-guide/fx-events/image39.png)

**설명**

이 이벤트는 파일 만들기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 파일 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="file-date-time-set"></a>파일 날짜 시간 설정 

#### <a name="fx_file_date_time_set"></a>fx_file_date_time_set

**아이콘** ![파일 날짜 시간 설정 아이콘](./media/user-guide/fx-events/image40.png)

**설명**

이 이벤트는 파일 날짜/시간 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 파일 이름에 대한 포인터입니다.
- 정보 필드 3: 연도입니다.
- 정보 필드 4: 월입니다.

### <a name="file-delete"></a>파일 삭제 

#### <a name="fx_file_delete"></a>fx_file_delete

**아이콘** ![파일 삭제 아이콘](./media/user-guide/fx-events/image41.png)

**설명**

이 이벤트는 파일 삭제 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 파일 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="file-open"></a>파일 열기 

#### <a name="fx_file_open"></a>fx_file_open

**아이콘** ![파일 열기 아이콘](./media/user-guide/fx-events/image42.png)

**설명**

이 이벤트는 파일 열기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 파일 제어 블록에 대한 포인터입니다.
- 정보 필드 3: 파일 이름에 대한 포인터입니다.
- 정보 필드 4: 다음과 같은 열기 유형입니다.

  |  열기 유형                        | 값        |
  |---------------------------------- | --------|
  |  읽기를 위한 열기                    | (0x00)  |
  |  쓰기를 위한 열기                   | (0x01)  |
  |  읽기를 위한 빠른 열기               | (0x02)  |

### <a name="file-read"></a>파일 읽기 

#### <a name="fx_file_read"></a>fx_file_read

**아이콘** ![파일 읽기 아이콘](./media/user-guide/fx-events/image43.png)

**설명**

이 이벤트는 파일 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 파일에 대한 포인터입니다.
- 정보 필드 2: 버퍼 포인터입니다.
- 정보 필드 3: 요청 크기입니다.
- 정보 필드 4: 읽은 실제 크기입니다.

### <a name="file-relative-seek"></a>파일 상대 검색 

#### <a name="fx_file_relative_seek"></a>fx_file_relative_seek

**아이콘** ![파일 상대 검색 아이콘](./media/user-guide/fx-events/image44.png)

**설명**

이 이벤트는 파일 상대 검색 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 파일에 대한 포인터입니다.
- 정보 필드 2: 바이트 오프셋입니다.
- 정보 필드 3: 다음에서 검색합니다.

  | 이벤트                             | 값        |
  |---------------------------------- | --------|
  |  시작부터                   | (0x00)  |
  |  끝부터                         | (0x01)  | 
  |  앞으로                          | (0x02)  |
  |  뒤로                         | (0x03)  |
- 정보 필드 4: 이전 오프셋입니다.

### <a name="file-rename"></a>파일 이름 바꾸기 

#### <a name="fx_file_rename"></a>fx_file_rename

**아이콘** ![파일 이름 바꾸기 아이콘](./media/user-guide/fx-events/image45.png)

**설명**

이 이벤트는 파일 이름 바꾸기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 이전 파일 이름에 대한 포인터입니다.
- 정보 필드 3: 새 파일 이름에 대한 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="file-seek"></a>파일 검색 

#### <a name="fx_file_seek"></a>fx_file_seek

**아이콘** ![파일 검색 아이콘](./media/user-guide/fx-events/image46.png)

**설명**

이 이벤트는 파일 검색 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 파일에 대한 포인터입니다.
- 정보 필드 2: 바이트 오프셋입니다.
- 정보 필드 3: 이전 오프셋입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="file-truncate"></a>파일 자르기 

#### <a name="fx_file_truncate"></a>fx_file_truncate

**아이콘** ![파일 자르기 아이콘](./media/user-guide/fx-events/image47.png)

**설명**

이 이벤트는 파일 자르기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 파일에 대한 포인터입니다.
- 정보 필드 2: 요청된 크기입니다.
- 정보 필드 3: 이전 크기입니다.
- 정보 필드 4: 새 크기입니다.

### <a name="file-truncate-release"></a>파일 자르기 해제 

#### <a name="fx_file_truncate_release"></a>fx_file_truncate_release 

**아이콘** ![파일 자르기 해제 아이콘](./media/user-guide/fx-events/image48.png)

**설명**

이 이벤트는 파일 자르기 해제 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 파일에 대한 포인터입니다.
- 정보 필드 2: 요청된 크기입니다.
- 정보 필드 3: 이전 크기입니다.
- 정보 필드 4: 새 크기입니다.

### <a name="file-write"></a>파일 쓰기 

#### <a name="fx_file_write"></a>fx_file_write 

**아이콘** ![파일 쓰기 아이콘](./media/user-guide/fx-events/image49.png)

**설명**

이 이벤트는 파일 쓰기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 파일에 대한 포인터입니다.
- 정보 필드 2: 버퍼 포인터입니다.
- 정보 필드 3: 요청 크기입니다.
- 정보 필드 4: 쓰여진 실제 크기입니다.

### <a name="media-abort"></a>미디어 중단 

#### <a name="fx_media_abort"></a>fx_media_abort 

**아이콘** ![미디어 중단 아이콘](./media/user-guide/fx-events/image50.png)

**설명**

이 이벤트는 미디어 중단 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="media-cache-invalidate"></a>미디어 캐시 무효화

#### <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

**아이콘** ![미디어 캐시 무효화 아이콘](./media/user-guide/fx-events/image51.png)

**설명**

이 이벤트는 미디어 캐시 무효화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="media-check"></a>미디어 검사 

#### <a name="fx_media_check"></a>fx_media_check

**아이콘** ![미디어 검사 아이콘](./media/user-guide/fx-events/image52.png)

**설명**

이 이벤트는 미디어 검사 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 스크래치 메모리 포인터입니다.
- 정보 필드 3: 스크래치 메모리 크기입니다.
- 정보 필드 4: 다음과 같은 오류 비트 맵입니다.

  | 오류 유형                        | 값        |
  |---------------------------------- | --------|
  |  FAT 체인 오류                  | (0x01)  |
  |  디렉터리 오류                  | (0x02)  |
  |  클러스터 손실 오류               | (0x04)  |
  |  파일 크기 오류                  | (0x08)  |

### <a name="media-close"></a>미디어 닫기 

#### <a name="fx_media_close"></a>fx_media_close

**아이콘** ![미디어 닫기 아이콘](./media/user-guide/fx-events/image53.png)

**설명**

이 이벤트는 미디어 닫기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="media-flush"></a>미디어 플러시 

#### <a name="fx_media_flush"></a>fx_media_flush

**아이콘** ![미디어 플러시 아이콘](./media/user-guide/fx-events/image54.png)

**설명**

이 이벤트는 미디어 플러시 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="media-format"></a>미디어 형식 

#### <a name="fx_media_format"></a>fx_media_format

**아이콘** ![미디어 형식 아이콘](./media/user-guide/fx-events/image55.png)

**설명**

이 이벤트는 미디어 형식 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 루트 항목 수입니다.
- 정보 필드 3: 섹터입니다.
- 정보 필드 4: 클러스터당 섹터 수입니다.

### <a name="media-open"></a>미디어 열기 

#### <a name="fx_media_open"></a>fx_media_open

**아이콘** ![미디어 열기 아이콘](./media/user-guide/fx-events/image56.png)

**설명**

이 이벤트는 미디어 열기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 미디어 드라이버 항목에 대한 포인터입니다.
- 정보 필드 3: 메모리 포인터입니다.
- 정보 필드 4: 메모리 크기입니다.

### <a name="media-read-media-read"></a>미디어 읽기 미디어 읽기 

#### <a name="fx_media_read"></a>fx_media_read

**아이콘** ![미디어 읽기 아이콘](./media/user-guide/fx-events/image57.png)

**설명**

이 이벤트는 미디어 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 논리 섹터입니다.
- 정보 필드 3: 버퍼 포인터입니다.
- 정보 필드 4: 읽은 바이트 수입니다.

### <a name="media-space-available"></a>사용 가능한 미디어 공간 

#### <a name="fx_media_space_available"></a>fx_media_space_available

**아이콘** ![사용 가능한 미디어 공간 아이콘](./media/user-guide/fx-events/image58.png)

**설명**

이 이벤트는 사용 가능한 미디어 공간 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 사용 가능한 바이트 포인터입니다.
- 정보 필드 3: 사용 가능한 클러스터 수입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="media-volume-get"></a>미디어 볼륨 가져오기 

#### <a name="fx_media_volume_get"></a>fx_media_volume_get

**아이콘** ![미디어 볼륨 가져오기 아이콘](./media/user-guide/fx-events/image59.png)

**설명**

이 이벤트는 미디어 볼륨 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 볼륨 이름에 대한 포인터입니다.
- 정보 필드 3: 볼륨 원본입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="media-volume-set"></a>미디어 볼륨 설정 

#### <a name="fx_media_volume_set"></a>fx_media_volume_set

**아이콘** ![미디어 볼륨 설정 아이콘](./media/user-guide/fx-events/image60.png)

**설명**

이 이벤트는 미디어 볼륨 설정 이벤트를 나타냅니다.

**정보 필드** 
- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 볼륨 이름에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="media-write"></a>미디어 쓰기 

#### <a name="fx_media_write"></a>fx_media_write

**아이콘** ![미디어 쓰기 아이콘](./media/user-guide/fx-events/image61.png)

**설명**

이 이벤트는 미디어 쓰기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 논리 섹터입니다.
- 정보 필드 3: 버퍼 포인터입니다.
- 정보 필드 4: 쓰여진 바이트 수입니다.

### <a name="system-date-get"></a>시스템 날짜 가져오기 

#### <a name="fx_system_date_get"></a>fx_system_date_get 

**아이콘** ![시스템 날짜 가져오기 아이콘](./media/user-guide/fx-events/image62.png)

**설명**

이 이벤트는 시스템 날짜 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 연도입니다.
- 정보 필드 2: 월입니다.
- 정보 필드 3: 일입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="system-date-set"></a>시스템 날짜 설정 

#### <a name="fx_system_date_set"></a>fx_system_date_set 

**아이콘** ![시스템 날짜 설정 아이콘](./media/user-guide/fx-events/image63.png)

**설명**

이 이벤트는 시스템 날짜 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 연도입니다.
- 정보 필드 2: 월입니다.
- 정보 필드 3: 일입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="system-initialize"></a>시스템 초기화 

#### <a name="fx_system_initialize"></a>fx_system_initialize 

**아이콘** ![시스템 초기화 아이콘](./media/user-guide/fx-events/image64.png)

**설명**

이 이벤트는 시스템 초기화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="system-time-get"></a>시스템 시간 가져오기 

#### <a name="fx_system_time_get"></a>fx_system_time_get 

**아이콘** ![시스템 시간 가져오기 아이콘](./media/user-guide/fx-events/image65.png)

**설명**

이 이벤트는 시스템 시간 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 시간입니다.
- 정보 필드 2: 분입니다.
- 정보 필드 3: 초입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="system-time-set"></a>시스템 시간 설정 

#### <a name="fx_system_time_set"></a>fx_system_time_set 

**아이콘** ![시스템 시간 설정 아이콘](./media/user-guide/fx-events/image66.png)

**설명**

이 이벤트는 시스템 시간 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 시간입니다.
- 정보 필드 2: 분입니다.
- 정보 필드 3: 초입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="unicode-directory-create"></a>유니코드 디렉터리 만들기 

#### <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create 

**아이콘** ![유니코드 디렉터리 만들기 아이콘](./media/user-guide/fx-events/image67.png)

**설명**

이 이벤트는 유니코드 디렉터리 만들기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 유니코드 이름에 대한 포인터입니다.
- 정보 필드 3: 유니코드 이름의 크기입니다.
- 정보 필드 4: 짧은 이름에 대한 포인터입니다.

### <a name="unicode-directory-rename"></a>유니코드 디렉터리 이름 바꾸기 

#### <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

**아이콘** ![유니코드 디렉터리 이름 바꾸기 아이콘](./media/user-guide/fx-events/image68.png)

**설명**

이 이벤트는 유니코드 디렉터리 이름 바꾸기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 유니코드 이름에 대한 포인터입니다.
- 정보 필드 3: 유니코드 이름의 크기입니다.
- 정보 필드 4: 짧은 이름에 대한 포인터입니다.

### <a name="unicode-file-create"></a>유니코드 파일 만들기 

#### <a name="fx_unicode_file_create"></a>fx_unicode_file_create

**아이콘** ![유니코드 파일 만들기 아이콘](./media/user-guide/fx-events/image69.png)

**설명**

이 이벤트는 유니코드 파일 만들기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 유니코드 이름에 대한 포인터입니다.
- 정보 필드 3: 유니코드 이름의 크기입니다.
- 정보 필드 4: 짧은 이름에 대한 포인터입니다.

### <a name="unicode-file-rename"></a>유니코드 파일 이름 바꾸기 

#### <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

**아이콘** ![유니코드 파일 이름 바꾸기 아이콘](./media/user-guide/fx-events/image70.png)

**설명**

이 이벤트는 유니코드 파일 이름 바꾸기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 유니코드 이름에 대한 포인터입니다.
- 정보 필드 3: 유니코드 이름의 크기입니다.
- 정보 필드 4: 짧은 이름에 대한 포인터입니다.

### <a name="unicode-length-get"></a>유니코드 길이 가져오기 

#### <a name="fx_unicode_length_get"></a>fx_unicode_length_get

**아이콘** ![유니코드 길이 가져오기 아이콘](./media/user-guide/fx-events/image71.png)

**설명**

이 이벤트는 유니코드 길이 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 유니코드 이름에 대한 포인터입니다.
- 정보 필드 2: 길이입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="unicode-name-get"></a>유니코드 이름 가져오기 

#### <a name="fx_unicode_name_get"></a>fx_unicode_name_get

**아이콘** ![유니코드 이름 가져오기 아이콘](./media/user-guide/fx-events/image72.png)

**설명**

이 이벤트는 유니코드 이름 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 소스의 짧은 이름입니다.
- 정보 필드 3: 대상 유니코드 이름 포인터입니다.
- 정보 필드 4: 대상 유니코드 이름 길이입니다.

### <a name="unicode-short-name-get"></a>유니코드의 짧은 이름 가져오기 

#### <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

**아이콘** ![유니코드의 짧은 이름 가져오기 아이콘](./media/user-guide/fx-events/image73.png)

**설명**

이 이벤트는 유니코드의 짧은 이름 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 미디어에 대한 포인터입니다.
- 정보 필드 2: 소스 유니코드 이름에 대한 포인터입니다.
- 정보 필드 3: 유니코드 이름의 길이입니다.
- 정보 필드 4: 짧은 이름에 대한 포인터입니다.