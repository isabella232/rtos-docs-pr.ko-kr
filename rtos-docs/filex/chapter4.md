---
title: 4장 - Azure RTOS FileX 서비스 설명
description: 이 장에서는 모든 Azure RTOS FileX 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c24259fb9b6b212dda99422e3ee1ad0e2fd970ce
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754882"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a>4장 - Azure RTOS FileX 서비스 설명

이 장에서는 모든 Azure RTOS FileX 서비스를 알파벳 순서로 설명합니다. 서비스 이름은 모든 유사한 서비스가 함께 그룹화되도록 설계되었습니다.

## <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read

디렉터리 특성을 읽습니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 미디어에서 디렉터리의 특성을 읽습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **directory_name**: 요청된 디렉터리의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).
- **attributes** _ptr: 배치할 디렉터리 특성의 대상에 대한 포인터입니다. 디렉터리 특성은 다음과 같은 가능한 설정으로 비트맵 형식으로 반환됩니다.
  - FX_READ_ONLY(0x01)
  - FX_HIDDEN(0x02)
  - FX_SYSTEM(0x04)
  - FX_VOLUME(0x08)
  - FX_DIRECTORY(0x10)
  - FX_ARCHIVE(0x20)

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 디렉터리 특성 읽기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX _NOT FOUND**(0x04) 지정된 디렉터리가 미디어에 없습니다.
- **FX_NOT_DIRECTORY**(0x0E) 항목이 디렉터리가 아닙니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류
- **FX_FILE_CORRUPT** 0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어
- **FX_PTR_ERROR**(0x18) 잘못된 미디어 포인터
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set

디렉터리 특성을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a>Description

이 서비스는 디렉터리의 특성을 호출자가 지정한 특성으로 설정합니다.

> [!WARNING]
> 이 애플리케이션은 서비스와 함께 디렉터리 특성의 하위 집합만 수정할 수 있습니다. 추가 특성을 설정하려고 하면 오류가 발생합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **directory_name**: 요청된 디렉터리의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).
- **attributes**: 디렉터리에 대한 새 특성입니다. 유효한 디렉터리 특성은 다음과 같이 정의됩니다.
  - FX_READ_ONLY(0x01)
  - FX_HIDDEN(0x02)
  - FX_SYSTEM(0x04)
  - FX_ARCHIVE(0x20)

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 디렉터리 특성 설정에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 지정된 디렉터리가 미디어에 없습니다.
- **FX_NOT_DIRECTORY**(0x0E) 항목이 디렉터리가 아닙니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어
- **FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.
- **FX_PTR_ERROR**(0x18) 잘못된 미디어 포인터
- **FX_INVALID_ATTR**(0x19) 잘못된 특성을 선택했습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_create"></a>fx_directory_create

하위 디렉터리를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a>Description

이 서비스는 현재 기본 디렉터리 또는 디렉터리 이름에 제공된 경로에 하위 디렉터리를 만듭니다. 루트 디렉터리와 달리 하위 디렉터리는 저장할 수 있는 파일 수에 제한이 없습니다. 루트 디렉터리는 부팅 레코드에서 결정한 항목 수만 저장할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **directory_name**: 만들 디렉터리의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 디렉터리 만들기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 지정된 디렉터리가 미디어에 없습니다.
- **FX_NOT_DIRECTORY**(0x0E) 항목이 디렉터리가 아닙니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류
- **FX_FILE _CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어
- **FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.
- **FX_PTR_ERROR**(0x18) 잘못된 미디어 포인터
- **FX_INVALID_ATTR**(0x19) 잘못된 특성을 선택했습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_get"></a>fx_directory_default_get

마지막 기본 디렉터리를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Description

이 서비스는 ***fx_directory_default_set*** 으로 마지막에 설정한 경로에 대한 포인터를 반환합니다. 기본 디렉터리가 설정되지 않았거나 현재 기본 디렉터리가 루트 디렉터리인 경우 FX_NULL 값이 반환됩니다.

> [!IMPORTANT]
> 내부 경로 문자열의 기본 크기는 256자입니다. **fx_api** 에서 **FX_MAXIMUM_PATH** 를 수정하고 전체 FileX 라이브러리를 다시 빌드하여 이 설정을 변경할 수 있습니다. 문자열 경로는 애플리케이션에 대해 유지되며 FileX에서 내부적으로 사용되지 않습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **return_path_name**: 마지막 기본 디렉터리 문자열의 대상에 대한 포인터입니다. 기본 디렉터리의 현재 설정이 루트이면 FX_NULL의 값이 반환됩니다. 미디어가 열리면 루트가 기본값입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 기본 디렉터리 가져오기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 대상 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_set"></a>fx_directory_default_set

기본 디렉터리를 설정합니다.

### <a name="prototype"></a>프로토타입

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Description

이 서비스는 미디어의 기본 디렉터리를 설정합니다. FX_NULL의 값이 제공되면 기본 디렉터리가 미디어의 루트 디렉터리로 설정됩니다. 경로를 명시적으로 지정하지 않는 모든 후속 파일 작업은 기본적으로 이 디렉터리로 지정됩니다.

> [!IMPORTANT]
> 내부 경로 문자열의 기본 크기는 256자입니다. **fx_api** 에서 **FX_MAXIMUM_PATH** 를 수정하고 전체 FileX 라이브러리를 다시 빌드하여 이 설정을 변경할 수 있습니다. 문자열 경로는 애플리케이션에 대해 유지되며 FileX에서 내부적으로 사용되지 않습니다.

> [!IMPORTANT]
> 애플리케이션에서 제공하는 이름의 경우 FileX는 디렉터리, 하위 디렉터리 및 파일 이름을 구분하기 위해 백슬래시(\\)와 슬래시(/) 문자 둘 다를 지원합니다. 그러나 FileX는 애플리케이션으로 반환되는 경로에는 백슬래시 문자만 사용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **new_path_name**: 새 기본 디렉터리 이름에 대한 포인터입니다. FX_NULL의 값이 제공되면 미디어의 기본 디렉터리가 미디어의 루트 디렉터리로 설정됩니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 기본 디렉터리 설정에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_INVALID_PATH**(0x0D) 새 디렉터리를 찾을 수 없습니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_delete"></a>fx_directory_delete

하위 디렉터리를 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Description

이 서비스는 지정된 디렉터리를 삭제합니다. 삭제하려면 디렉터리가 비어 있어야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **directory_name**: 삭제할 디렉터리 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 디렉터리 삭제에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 지정된 디렉터리를 찾을 수 없습니다.
- **FX_DIR_NOT_EMPTY**(0x10) 지정된 디렉터리가 비어 있지 않습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어
- **FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.
- **FX_NOT_DIRECTORY**(0x0E) 디렉터리 항목이 아닙니다.
- **FX_PTR_ERROR**(0x18) 잘못된 미디어 포인터
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

첫 번째 디렉터리 항목을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Description

이 서비스는 기본 디렉터리에서 첫 번째 항목 이름을 검색하여 지정된 대상에 복사합니다.

> [!WARNING]
> 지정된 대상은 **FX_MAX_LONG_NAME_LEN** 으로 정의한 FileX 이름의 최대 크기를 저장할 수 있을 만큼 커야 합니다.

> [!WARNING]
> 로컬이 아닌 경로를 사용하는 경우 디렉터리를 순회하는 동안 (ThreadX 세마포, 뮤텍스 또는 우선 순위 수준 변경에 따라) 다른 애플리케이션 스레드가 이 디렉터리를 변경할 수 없도록 방지해야 합니다. 그러지 않으면 잘못된 결과를 얻을 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **return_entry_name**: 기본 디렉터리에 있는 첫 번째 항목 이름의 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 첫 번째 디렉터리 항목 찾기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 대상 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

첫 번째 디렉터리 항목을 모든 정보와 함께 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **directory_name**: 디렉터리 항목 이름의 대상에 대한 포인터입니다. 적어도 FX_MAX_LONG_NAME_LEN만큼 커야 합니다.
- **특성**: null이 아닌 경우 배치할 항목 특성의 대상에 대한 포인터입니다. 특성은 다음과 같은 가능한 설정과 함께 비트맵 형식으로 반환됩니다.
  - **FX_READ_ONLY**(0x01)
  - **FX_HIDDEN**(0x02)
  - **FX_SYSTEM**(0x04)
  - **FX_VOLUME**(0x08)
  - **FX_DIRECTORY**(0x10)
  - **FX_ARCHIVE**(0x20)
- **size**: null이 아닌 경우 항목 크기(바이트)의 대상에 대한 포인터입니다.
- **year**: null이 아닌 경우 항목 수정 연도의 대상에 대한 포인터입니다.
- **month**: null이 아닌 경우 항목 수정 월의 대상에 대한 포인터입니다.
- **day**: null이 아닌 경우 항목 수정일의 대상에 대한 포인터입니다.
- **hour**: null이 아닌 경우 항목 수정 시간의 대상에 대한 포인터입니다.
- **minute**: null이 아닌 경우 항목 수정 분의 대상에 대한 포인터입니다.
- **second**: null이 아닌 경우 항목 수정 초의 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 첫 번째 디렉터리 항목 찾기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_FILE _CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어
- **FX_PTR_ERROR**(0x18) 미디어 또는 대상 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_information_get"></a>fx_directory_information_get:

디렉터리 항목 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **directory_name**: 디렉터리 항목 이름에 대한 포인터입니다.
- **attributes**: 특성의 대상에 대한 포인터입니다.
- **size**: 크기의 대상에 대한 포인터입니다.
- **year**: 연도의 대상에 대한 포인터입니다.
- **month**: 월의 대상에 대한 포인터입니다.
- **day**: 날짜의 대상에 대한 포인터입니다.
- **hour**: 시간의 대상에 대한 포인터입니다.
- **minute**: 분의 대상에 대한 포인터입니다.
- **second**: 초의 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 첫 번째 디렉터리 항목 찾기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 지정된 디렉터리가 미디어에 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어
- **FX_FILE _CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터
- **FX_PTR_ERROR**(0x18) 미디어 또는 대상 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear:

기본 로컬 경로를 지웁니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Description

이 서비스는 호출 스레드에 대해 설정된 이전 로컬 경로 설정을 지웁니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 이전에 열린 미디어에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 로컬 경로 지우기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 현재 열려 있지 않습니다.
- **FX_NOT_IMPLEMENTED**(0x22) FX_NO_LCOAL_PATH가 정의되어 있습니다.
- **FX_PTR_ERROR**(0x18) 잘못된 미디어 포인터

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get:

현재 로컬 경로 문자열을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Description

이 서비스는 지정된 미디어의 로컬 경로 포인터를 반환합니다. 로컬 경로가 설정되어 있지 않으면 NULL이 호출자에게 반환됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **return_path_name**: 저장할 로컬 경로 문자열의 대상 문자열 포인터에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 로컬 경로 가져오기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 현재 열려 있지 않습니다.
- **FX_NOT_IMPLEMENTED**(0x22) NX_NO_LCOAL_PATH
- **FX_PTR_ERROR**(0x18) 잘못된 미디어 포인터


### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore:

이전 로컬 경로를 복원합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a>Description

서비스가 이전에 설정된 로컬 경로를 복원합니다. 이 로컬 경로에 만든 디렉터리 검색 위치도 복원되어 애플리케이션에서 재귀 디렉터리를 순회하는 데 이 루틴을 유용하게 사용할 수 있게 됩니다.

> [!IMPORTANT]
> 각 로컬 경로에는 **FX_MAXIMUM_PATH** 크기의 로컬 경로 문자열이 포함됩니다. 크기는 기본적으로 256자입니다. 이 내부 경로 문자열은 FileX에서 사용되지 않으며 애플리케이션용으로만 제공됩니다. **FX_LOCAL_PATH** 를 지역 변수로 선언하려는 경우 사용자는 이 구조체의 크기만큼 증가하는 스택에 주의해야 합니다. 사용자는 **FX_MAXIMUM_PATH** 의 크기를 줄이고 FileX 라이브러리 소스를 다시 빌드하는 것이 좋습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **local_path_ptr**: 이전에 설정한 로컬 경로에 대한 포인터입니다. 이 포인터는 이전에 사용되었는데 아직 그대로 남아 있는 로컬 경로를 가리켜야 합니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 로컬 경로 복원에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 현재 열려 있지 않습니다.
- **FX_NOT_IMPLEMENTED**(0x22) FX_NO_LCOAL_PATH가 정의되어 있습니다.
- **FX_PTR_ERROR**(0x18) 잘못된 미디어 또는 로컬 경로 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

스레드별 로컬 경로를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Description

이 서비스는 ***new_path_string** _로 지정한 스레드별 경로를 설정합니다. 이 루틴이 성공적으로 완료되면 _ *_local_path_ptr_**에 저장된 로컬 경로 정보가 이 스레드에서 만든 모든 파일 및 디렉터리 작업에 대한 전역 미디어 경로보다 우선 적용됩니다. 이는 시스템의 다른 스레드에는 영향을 주지 않습니다. 
> [!IMPORTANT]
> 로컬 경로 문자열의 기본 크기는 256자입니다. **fx_api** 에서 **FX_MAXIMUM_PATH** 를 수정하고 전체 FileX 라이브러리를 다시 빌드하여 이 설정을 변경할 수 있습니다. 문자열 경로는 애플리케이션에 대해 유지되며 FileX에서 내부적으로 사용되지 않습니다.

> [!IMPORTANT]
> 애플리케이션에서 제공하는 이름의 경우 FileX는 디렉터리, 하위 디렉터리 및 파일 이름을 구분하기 위해 백슬래시(\\)와 슬래시(/) 문자 둘 다를 지원합니다. 그러나 FileX는 애플리케이션으로 반환되는 경로에는 백슬래시 문자만 사용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 이전에 열린 미디어에 대한 포인터입니다.
- **local_path_ptr**: 스레드별 로컬 경로 정보를 저장하는 대상입니다. 이 구조체의 주소는 나중에 로컬 경로 복원 함수에 제공될 수 있습니다.
- **new_path_name**: 설치할 로컬 경로를 지정합니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 기본 디렉터리 설정에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_IMPLEMENTED**(0x22) **FX_NO_LCOAL_PATH
- **FX_INVALID_PATH**(0x0D) 새 디렉터리를 찾을 수 없습니다.
- **FX_NOT_IMPLEMENTED**(0x22)- **FX_NO_LOCAL_PATH가 정의되어 있습니다.
- **FX_PTR_ERROR**(0x18) 잘못된 미디어 또는 로컬 경로 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get:

짧은 이름에서 긴 이름을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a>Description

이 서비스는 제공된 짧은 (8.3 형식) 이름과 연결된 긴 이름을(있는 경우) 검색합니다. 짧은 이름은 파일 이름 또는 디렉터리 이름일 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **short_name**: 원본 짧은 이름(8.3 형식)에 대한 포인터입니다.
- **long_name**: 긴 이름의 대상에 대한 포인터입니다. 긴 이름이 없으면 짧은 이름이 반환됩니다. 긴 이름의 대상은 FX_MAX_LONG_NAME_LEN자를 저장할 수 있을 만큼 커야 합니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 긴 이름 가져오기에 성공했습니다.
- **FX_NOT_FOUND**(0x04) 짧은 이름을 찾을 수 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get_extended"></a>fx_directory_long_name_get_extended

짧은 이름에서 긴 이름을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a>Description

이 서비스는 제공된 짧은 (8.3 형식) 이름과 연결된 긴 이름을(있는 경우) 검색합니다. 짧은 이름은 파일 이름 또는 디렉터리 이름일 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **short_name**: 원본 짧은 이름(8.3 형식)에 대한 포인터입니다.
- **long_name**: 긴 이름의 대상에 대한 포인터입니다. 긴 이름이 없으면 짧은 이름이 반환됩니다. 참고: 긴 이름의 대상은 **FX_MAX_LONG_NAME_LEN** 자를 저장할 수 있을 만큼 커야 합니다.
- **long_file_name_buffer_length**: 긴 이름 버퍼의 길이입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 긴 이름 가져오기에 성공했습니다.
- **FX_NOT_FOUND**(0x04) 짧은 이름을 찾을 수 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name, sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_name_test"></a>fx_directory_name_test

디렉터리 테스트

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Description

이 서비스는 제공된 이름이 디렉터리인지 여부를 테스트합니다. 디렉터리인 경우 FX_SUCCESS가 반환됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **directory_name**: 디렉터리 항목 이름에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 제공된 이름이 디렉터리입니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 디렉터리 항목을 찾을 수 없습니다.
- **FX_NOT_DIRECTORY**(0x0E) 항목이 디렉터리가 아닙니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find:

다음 디렉터리 항목을 선택합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Description

이 서비스는 현재 기본 디렉터리의 다음 항목 이름을 반환합니다.

> [!WARNING]
> 로컬이 아닌 경로를 사용하는 경우 디렉터리를 순회하는 동안 (ThreadX 세마포 또는 스레드 우선 순위 수준에 따라) 다른 애플리케이션 스레드가 이 디렉터리를 변경할 수 없도록 방지해야 합니다. 그러지 않으면 잘못된 결과를 얻을 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **return_entry_name**: 기본 디렉터리에 있는 다음 항목 이름의 대상에 대한 포인터입니다. 이 포인터가 가리키는 버퍼는 **_FX_MAX_LONG_NAME_LEN_** 으로 정의한 FileX 이름의 최대 크기를 저장할 수 있을 만큼 커야 합니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 다음 항목 찾기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find:

전체 정보와 함께 다음 디렉터리 항목을 가져옵니다.

### <a name="prototype"></a>프로토타입

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

### <a name="description"></a>Description

이 서비스는 기본 디렉터리에서 다음 항목 이름을 검색하고 지정된 대상에 복사합니다. 또한 추가 입력 매개 변수로 지정된 항목에 대한 전체 정보를 반환합니다.

> [!WARNING]
> **지정된 대상은 ***FX_MAX_LONG_NAME_LEN***으로 정의한 FileX 이름의 최대 크기를 저장할 수 있을 만큼 커야 합니다.*

> [!WARNING]
> 로컬이 아닌 경로를 사용하는 경우 디렉터리를 순회하는 동안 (ThreadX 세마포, 뮤텍스 또는 우선 순위 수준 변경에 따라) 다른 애플리케이션 스레드가 이 디렉터리를 변경할 수 없도록 방지해야 합니다. 그러지 않으면 잘못된 결과를 얻을 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **directory_name**: 디렉터리 항목 이름의 대상에 대한 포인터입니다. 적어도 **FX_MAX_LONG_NAME_LEN** 만큼 커야 합니다.
- **특성**: null이 아닌 경우 배치할 항목 특성의 대상에 대한 포인터입니다. 특성은 다음과 같은 가능한 설정과 함께 비트맵 형식으로 반환됩니다.
  - **FX_READ_ONLY**(0x01)
  - **FX_HIDDEN**(0x02)
  - **FX_SYSTEM**(0x04)
  - **FX_VOLUME**(0x08)
  - **FX_DIRECTORY**(0x10)
  - **FX_ARCHIVE**(0x20)
- **size**: null이 아닌 경우 항목 크기(바이트)의 대상에 대한 포인터입니다.
- **month**: null이 아닌 경우 항목 수정 월의 대상에 대한 포인터입니다.
- **year**: null이 아닌 경우 항목 수정 연도의 대상에 대한 포인터입니다.
- **day**: null이 아닌 경우 항목 수정일의 대상에 대한 포인터입니다.
- **hour**: null이 아닌 경우 항목 수정 시간의 대상에 대한 포인터입니다.
- **minute**: null이 아닌 경우 항목 수정 분의 대상에 대한 포인터입니다.
- **second**: null이 아닌 경우 항목 수정 초의 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 디렉터리 다음 항목 찾기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었거나 모든 입력 매개 변수가 NULL입니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_rename"></a>fx_directory_rename

디렉터리 이름을 바꿉니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a>Description

이 서비스는 디렉터리 이름을 지정된 새 디렉터리 이름으로 변경합니다. 지정된 경로 또는 기본 경로를 기준으로 이름이 바뀝니다. 경로가 새 디렉터리 이름에 지정된 경우 이름이 바뀐 디렉터리가 지정된 경로로 이동합니다. 지정된 경로가 없으면 이름이 바뀐 디렉터리가 현재 기본 경로에 배치됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **old_directory_name**: 현재 디렉터리 이름에 대한 포인터입니다.
- **new_directory_name**: 새 디렉터리 이름에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 디렉터리 이름 바꾸기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 디렉터리 항목을 찾을 수 없습니다.
- **FX_NOT_DIRECTORY**(0x0E) 항목이 디렉터리가 아닙니다.
- **FX_INVALID_NAME**(0x0C) 새 디렉터리 이름이 잘못되었습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.
- **FX_NO_MORE_ENTRIES**(0x0F) 이 디렉터리에 항목이 더 없습니다.
- **FX_INVALID_PATH**(0x0D) 디렉터리 이름과 함께 제공된 경로가 잘못되었습니다.
- **FX_ALREADY_CREATED**(0x0B) 지정된 디렉터리가 이미 생성되어 있습니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get:

긴 이름에서 짧은 이름을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a>Description

이 서비스는 제공된 긴 이름과 연결된 짧은 (8.3 형식) 이름을 검색합니다. 긴 이름은 파일 이름 또는 디렉터리 이름일 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **long_name**: 원본 긴 이름에 대한 포인터입니다.
- **short_name**: 대상 짧은 이름(8.3 형식)에 대한 포인터입니다. 짧은 이름의 대상은 14자를 포함할 수 있도록 충분히 커야 합니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 짧은 이름 가져오기에 성공했습니다.
- **FX_NOT_FOUND**(0x04) 긴 이름을 찾을 수 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get_extended"></a>fx_directory_short_name_get_extended

긴 이름에서 짧은 이름을 가져옵니다.

### <a name="prototype"></a>프로토타입

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a>Description

이 서비스는 제공된 긴 이름과 연결된 짧은 (8.3 형식) 이름을 검색합니다. 긴 이름은 파일 이름 또는 디렉터리 이름일 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **long_name**: 원본 긴 이름에 대한 포인터입니다.
- **short_name**: 대상 짧은 이름(8.3 형식)에 대한 포인터입니다. 참고: 짧은 이름의 대상은 14자를 포함할 수 있도록 충분히 커야 합니다.
- **short_file_name_length**: 짧은 이름 버퍼의 길이입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 짧은 이름 가져오기에 성공했습니다.
- **FX_NOT_FOUND**(0x04) 긴 이름을 찾을 수 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_fault_tolerant_enable"></a>fx_fault_tolerant_enable

내결함성 서비스를 사용합니다.

### <a name="prototype"></a>프로토타입

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a>Description

이 서비스는 내결함성 모듈을 사용합니다. 시작 시 내결함성 모듈은 파일 시스템이 FileX 내결함성 보호 상태인지 여부를 감지합니다. 내결함성 보호 상태가 아니면 서비스가 파일 시스템 트랜잭션의 로그를 저장할 수 있는 섹터를 파일 시스템에서 찾습니다. 파일 시스템이 FileX 내결함성 보호 상태이면 무결성을 유지하기 위해 파일 시스템에 로그를 적용합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **memory_ptr**: 내결함성 모듈에서 스크래치 메모리로 사용하는 메모리 블록에 대한 포인터입니다.
- **memory_size**: 스크래치 메모리의 크기입니다. 내결함성이 제대로 작동하려면 스크래치 메모리 크기가 3072바이트 이상이어야 하며 섹터 크기의 배수여야 합니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 내결함성을 사용하도록 설정했습니다.
- **FX_NOT_ENOUGH_MEMORY**(0x91) 메모리 크기가 너무 작습니다.
- **FX_BOOT_ERROR**(0x01) 부팅 섹터 오류입니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) 사용 가능한 여유 클러스터가 더 이상 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 이 파일과 연결된 미디어에 사용 가능한 클러스터가 충분하지 않습니다.
- **FX_SECTOR_INVALID**(0x89) 섹터가 잘못되었습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a>참고 항목

- fx_system_initialize
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write

## <a name="fx_file_allocate"></a>fx_file_allocate

파일에 필요한 공간을 할당합니다.

### <a name="prototype"></a>프로토타입

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a>Description

이 서비스는 하나 이상의 인접한 클러스터를 할당하여 지정된 파일의 끝에 연결합니다. FileX는 요청된 크기를 클러스터당 바이트 수로 나누어 필요한 클러스터 수를 결정합니다. 나눈 결과는 다음 전체 클러스터로 반올림됩니다.

4GB를 초과하는 공간을 할당하려면 애플리케이션이 *fx_file_extended_allocate* 서비스를 사용해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 이전에 연 파일에 대한 포인터입니다.
- **size**: 파일에 할당할 바이트 수입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 할당에 성공했습니다.
- **FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽지 못했습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) 사용 가능한 여유 클러스터가 더 이상 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 이 파일과 연결된 미디어에 사용 가능한 클러스터가 충분하지 않습니다.
- **FX_SECTOR_INVALID**(0x89) 섹터가 잘못되었습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a>참고 항목

- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open- fx_file_read
- fx_file_relative_seek
- fx_file_rename- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_read"></a>fx_file_attributes_read

파일 특성을 읽습니다.

### <a name="prototype"></a>프로토타입

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 미디어에서 파일의 특성을 읽습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **file_name**: 요청된 파일의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).
- **attributes_ptr**: 배치할 파일 특성의 대상에 대한 포인터입니다. 파일 특성은 다음과 같은 가능한 설정과 함께 비트맵 형식으로 반환됩니다.
  - FX_READ_ONLY(0x01)
  - FX_HIDDEN(0x02)
  - FX_SYSTEM(0x04)
  - FX_VOLUME(0x08)
  - FX_DIRECTORY(0x10)
  - FX_ARCHIVE(0x20)

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 특성 읽기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 지정된 파일이 미디어에 없습니다.
- **FX_NOT_A_FILE**(0x05) 지정된 파일이 디렉터리입니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 특성 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_set"></a>fx_file_attributes_set

파일 특성 설정

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a>Description

이 서비스는 파일의 특성을 호출자가 지정한 특성으로 설정합니다.

> [!WARNING]
> 이 애플리케이션은 서비스와 함께 파일 특성의 하위 집합만 수정할 수 있습니다. 추가 특성을 설정하려고 하면 오류가 발생합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **file_name**: 요청된 파일의 이름에 대한 포인터입니다**(디렉터리 경로는 선택 사항임).
- **attributes**: 파일의 새 특성입니다. 유효한 파일 특성은 다음과 같이 정의됩니다.
  - FX_READ_ONLY(0x01)
  - FX_HIDDEN(0x02)
  - FX_SYSTEM(0x04)
  - FX_ARCHIVE(0x20)

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 특성 설정에 성공했습니다.
- **FX_ACCESS_ERROR**(0x06) 파일이 열려 있어 파일의 특성을 설정할 수 없습니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 테이블 또는 exFAT 클러스터 맵에 더 이상 항목이 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_NOT_FOUND**(0x04) 지정된 파일이 미디어에 없습니다.
- **FX_NOT_A_FILE**(0x05) 지정된 파일이 디렉터리입니다.
- **FX_SECTOR_INVALID**(0x89) 섹터가 잘못되었습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.
- **FX_INVALID_ATTR**(0x19) 잘못된 특성을 선택했습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

파일에 공간을 할당하기 위한 최상의 노력

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a>Description

이 서비스는 하나 이상의 인접한 클러스터를 할당하여 지정된 파일의 끝에 연결합니다. FileX는 요청된 크기를 클러스터당 바이트 수로 나누어 필요한 클러스터 수를 결정합니다. 나눈 결과는 다음 전체 클러스터로 반올림됩니다. 미디어에서 사용할 수 있는 연속 클러스터가 부족한 경우 이 서비스는 연속 클러스터의 사용 가능한 가장 큰 블록을 파일에 연결합니다. 실제로 파일에 할당된 공간이 호출자에게 반환됩니다.

4GB를 초과하는 공간을 할당하려면 애플리케이션이 *fx_file_extended_best_effort_allocate* 서비스를 사용해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 이전에 연 파일에 대한 포인터입니다.
- **size**: 파일에 할당할 바이트 수입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 최선의 파일 할당에 성공했습니다.
- **FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.
- **FX_NO_MORE_SPACE**(0x0A) 이 파일과 연결된 미디어에 사용 가능한 클러스터가 충분하지 않습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 파일 포인터 또는 대상이 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_close"></a>fx_file_close

파일을 닫습니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 파일을 닫습니다. 쓰기 위해 파일이 열려 있는데 수정된 경우 이 서비스는 새 크기, 현재 시스템 시간, 날짜와 함께 디렉터리 항목을 업데이트하여 파일 수정 프로세스를 완료합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 이전에 연 파일에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 닫기에 성공했습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 특성 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_create"></a>fx_file_create

파일을 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a>Description

이 서비스는 기본 디렉터리 또는 파일 이름과 함께 제공된 디렉터리 경로에 지정된 파일을 만듭니다.

> [!WARNING]
> 이 서비스는 길이가 0인 파일을 만듭니다. 즉, 클러스터가 할당되지 않습니다. 할당은 후속 파일을 쓸 때 자동으로 발생하거나 (공간이 4GB를 초과하는 경우에는) fx_file_allocate 또는 fx_file_extended_allocate 서비스를 사용하여 미리 수행할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **file_name**: 만들 파일의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 만들기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_ALREADY_CREATED**(0x0B) 지정된 파일이 이미 생성되어 있습니다.
- **FX_NO_MORE_SPACE**(0x0A) 루트 디렉터리에 항목이 더 이상 없거나 사용 가능한 클러스터가 더 이상 없습니다.
- **FX_INVALID_PATH**(0x0D) 파일 이름과 함께 제공된 경로가 잘못되었습니다.
- **FX_INVALID_NAME**(0x0C) 파일 이름이 잘못되었습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 기본 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 파일 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a>참고 항목
- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_date_time_set"></a>fx_file_date_time_set

### <a name="sets-file-date-and-time"></a>파일 날짜 및 시간 설정

파일 날짜 및 시간을 설정합니다.

### <a name="prototype"></a>프로토타입

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
### <a name="description"></a>Description

이 서비스는 지정된 파일의 날짜와 시간을 설정합니다.

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **file_name**: 파일 이름에 대한 포인터입니다.
- **year**: 연도의 값입니다(1980~2107 포함).
- **month**: 월의 값입니다(1~12 포함).
- **day**: 날짜의 값입니다(1~31 포함).
- **hour**: 시간의 값입니다(0~23 포함).
- **minute**: 분의 값입니다(0~59 포함).
- **second**: 초의 값입니다(0~59 포함).

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 날짜/시간 설정에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 파일을 찾을 수 없습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.
- **FX_INVALID_YEAR**(0x12) 연도가 잘못되었습니다.
- **FX_INVALID_MONTH**(0x13) 월이 잘못되었습니다.
- **FX_INVALID_DAY**(0x14) 날짜가 잘못되었습니다.
- **FX_INVALID_HOUR**(0x15) 시간이 잘못되었습니다.
- **FX_INVALID_MINUTE**(0x16) 분이 잘못되었습니다.
- **FX_INVALID_SECOND**(0x17) 초가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_delete"></a>fx_file_delete

### <a name="deletes-file"></a>파일 삭제

파일 삭제

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a>Description

이 서비스는 지정된 파일을 삭제합니다.


### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **file_name**: 삭제할 파일의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 삭제에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 지정된 파일을 찾을 수 없습니다.
- **FX_NOT_A_FILE**(0x05) 지정된 파일 이름이 디렉터리 또는 볼륨입니다.
- **FX_ACCESS_ERROR**(0x06) 지정된 파일이 현재 열려 있습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_allocate"></a>fx_file_extended_allocate

파일에 필요한 공간을 할당합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a>Description

이 서비스는 하나 이상의 인접한 클러스터를 할당하여 지정된 파일의 끝에 연결합니다. FileX는 요청된 크기를 클러스터당 바이트 수로 나누어 필요한 클러스터 수를 결정합니다. 나눈 결과는 다음 전체 클러스터로 반올림됩니다.

이 서비스는 exFAT용으로 설계되었습니다. *size* 매개 변수는 64비트 정수 값을 사용합니다. 따라서 호출자가 4GB 범위를 벗어나 공간을 미리 할당할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 이전에 연 파일에 대한 포인터입니다.
- **size**: 파일에 할당할 바이트 수입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 할당에 성공했습니다.
- **FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.
- **FX_NO_MORE_SPACE**(0x0A) 이 파일과 연결된 미디어에 사용 가능한 클러스터가 충분하지 않습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_best_effort_allocate"></a>fx_file_extended_best_effort_allocate

파일에 공간을 할당하기 위한 최상의 노력

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a>Description

이 서비스는 하나 이상의 인접한 클러스터를 할당하여 지정된 파일의 끝에 연결합니다. FileX는 요청된 크기를 클러스터당 바이트 수로 나누어 필요한 클러스터 수를 결정합니다. 나눈 결과는 다음 전체 클러스터로 반올림됩니다. 미디어에서 사용할 수 있는 연속 클러스터가 부족한 경우 이 서비스는 연속 클러스터의 사용 가능한 가장 큰 블록을 파일에 연결합니다. 실제로 파일에 할당된 공간이 호출자에게 반환됩니다.

이 서비스는 exFAT용으로 설계되었습니다. *size* 매개 변수는 64비트 정수 값을 사용합니다. 따라서 호출자가 4GB 범위를 벗어나 공간을 미리 할당할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 이전에 연 파일에 대한 포인터입니다.
- **size**: 파일에 할당할 바이트 수입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 할당에 성공했습니다.
- **FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.
- **FX_NO_MORE_SPACE**(0x0A) 이 파일과 연결된 미디어에 사용 가능한 클러스터가 충분하지 않습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_relative_seek"></a>fx_file_extended_relative_seek

상대 바이트 오프셋에 대한 위치입니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Description

이 서비스는 내부 파일 읽기/쓰기 포인터를 지정된 상대 바이트 오프셋에 배치합니다. 모든 후속 파일 읽기 또는 쓰기 요청은 파일의 이 위치에서 시작됩니다.

이 서비스는 exFAT용으로 설계되었습니다. *byte_offset* 매개 변수는 64비트 정수 값을 사용하므로 호출자가 4GB 범위를 벗어나 읽기/쓰기 포인터의 위치를 변경할 수 있습니다.

> [!IMPORTANT]
> 찾기 작업이 파일의 끝을 지나 찾으려고 하면 파일의 읽기/쓰기 포인터가 파일의 끝에 배치됩니다. 반대로 찾기 작업이 파일의 시작 부분을 지나서 배치하려고 하면 파일의 읽기/쓰기 포인터가 파일의 시작 부분에 배치됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 이전에 연 파일에 대한 포인터입니다.
- **byte_offset**: 파일에서 원하는 상대 바이트 오프셋입니다.
- **seek_from**: 상대 찾기를 수행할 방향과 위치입니다. 유효한 찾기 옵션은 다음과 같이 정의됩니다.
  - FX_SEEK_BEGIN(0x00)
  - FX_SEEK_END(0x01)
  - FX_SEEK_FORWARD(0x02)
  - FX_SEEK_BACK(0x03) FX_SEEK_BEGIN이 지정된 경우 찾기 작업은 파일의 시작 부분에서 수행됩니다. FX_SEEK_END가 지정된 경우 찾기 작업은 파일의 끝에서 뒤로 수행됩니다. FX_SEEK_FORWARD가 지정된 경우 찾기 작업은 현재 파일 위치에서 정방향으로 수행됩니다. FX_SEEK_BACK이 지정된 경우 찾기 작업은 현재 파일 위치에서 역방향으로 수행됩니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 상대 검색에 성공했습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_seek"></a>fx_file_extended_seek

바이트 오프셋에 대한 위치

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a>Description

이 서비스는 내부 파일 읽기/쓰기 포인터를 지정된 바이트 오프셋에 배치합니다. 모든 후속 파일 읽기 또는 쓰기 요청은 파일의 이 위치에서 시작됩니다.

이 서비스는 exFAT용으로 설계되었습니다. *byte_offset* 매개 변수는 64비트 정수 값을 사용하므로 호출자가 4GB 범위를 벗어나 읽기/쓰기 포인터의 위치를 변경할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 파일 제어 블록에 대한 포인터입니다.
- **byte_offset**: 파일에서 원하는 바이트 오프셋입니다. 값이 0이면 파일의 시작 부분에 읽기/쓰기 포인터가 배치되고 값이 파일의 크기보다 크면 파일의 끝에 읽기/쓰기 포인터를 배치합니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 검색에 성공했습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate"></a>fx_file_extended_truncate

파일을 자릅니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a>Description

이 서비스는 파일의 크기를 지정된 크기로 자릅니다. 제공된 크기가 실제 파일 크기보다 크면 이 서비스는 아무것도 수행하지 않습니다. 파일과 연결된 미디어 클러스터 중 해제된 클러스터가 없습니다.

> [!WARNING]
> 읽으려고 동시에 열 수 있는 파일을 잘라낼 때는 주의해야 합니다. 읽기 위해 열려 있는 파일을 자르면 잘못된 데이터를 읽을 수 있습니다.

이 서비스는 exFAT용으로 설계되었습니다. *size* 매개 변수는 64비트 정수 값을 사용합니다. 따라서 호출자가 4GB 범위를 벗어나 작동할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 파일 제어 블록에 대한 포인터입니다.
- **size**: 새 파일 크기입니다. 이 새 파일 크기를 벗어난 바이트는 무시됩니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 자르기에 성공했습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.
- **FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 기본 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate_release"></a>fx_file_extended_truncate_release

파일을 자르고 클러스터를 해제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a>Description

이 서비스는 파일의 크기를 지정된 크기로 자릅니다. 제공된 크기가 실제 파일 크기보다 크면 이 서비스는 아무것도 수행하지 않습니다. ***Fx_file_extended_truncate*** 서비스와 달리 이 서비스는 사용되지 않는 클러스터를 모두 해제합니다.

> [!WARNING]
> 읽으려고 동시에 열 수 있는 파일을 잘라낼 때는 주의해야 합니다. 읽기 위해 열려 있는 파일을 자르면 잘못된 데이터를 읽을 수 있습니다.

이 서비스는 exFAT용으로 설계되었습니다. *size* 매개 변수는 64비트 정수 값을 사용합니다. 따라서 호출자가 4GB 범위를 벗어나 작동할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 이전에 연 파일에 대한 포인터입니다.
- **size**: 새 파일 크기입니다. 이 새 파일 크기를 벗어난 바이트는 무시됩니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 자르기에 성공했습니다.
- **FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_open"></a>fx_file_open

파일을 엽니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a>Description

이 서비스는 읽거나 쓰기 위해 지정된 파일을 엽니다. 파일은 읽기 위해 여러 번 열 수 있지만 쓰기 위해서는 쓰기 권한자가 파일을 닫을 때까지 한 번만 열 수 있습니다.

> [!IMPORTANT]
> 읽고 쓰기 위해 파일이 동시에 열려 있는 경우 주의해야 합니다. 읽기 위해 파일을 동시에 연 상태에서 수행한 파일 쓰기는 읽기 권한자가 파일을 닫고 읽기 위해 다시 열지 않는 한 읽기 권한자에게 표시되지 않을 수 있습니다. 마찬가지로 파일 쓰기 권한자는 파일 자르기 서비스를 사용하는 경우 주의해야 합니다. 쓰기 권한자가 파일을 자른 경우 동일한 파일의 읽기 권한자가 잘못된 데이터를 반환할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **file_ptr**: 파일 제어 블록에 대한 포인터입니다.
- **file_name**: 연 파일의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).
- **open_type**: 열려 있는 파일의 유형입니다. 유효한 개방형 형식 옵션은 다음과 같습니다.
  - FX_OPEN_FOR_READ(0x00)
  - FX_OPEN_FOR_WRITE(0x01)
  - FX_OPEN_FOR_READ_FAST(0x02)

FX_OPEN_FOR_READ 및 FX_OPEN_FOR_READ_FAST를 사용하여 파일 열기는 유사합니다.

- FX_OPEN_FOR_READ에는 파일을 구성하는 클러스터의 연결된 목록이 그대로 유지되는지 확인하는 작업이 포함되는데, FX_OPEN_FOR_READ_FAST는 해당 확인 작업을 수행하지 않기 때문에 더 빠릅니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 열기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 지정된 파일을 찾을 수 없습니다.
- **FX_NOT_A_FILE**(0x05) 지정된 파일 이름이 디렉터리 또는 볼륨입니다.
- **FX_FILE_CORRUPT**(0x08) 지정된 파일이 손상되어 열지 못했습니다.
- **FX_ACCESS_ERROR**(0x06) 지정된 파일이 이미 열려 있거나 개방형 형식이 잘못되었습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_MEDIA_INVALID**(0x02) 잘못된 미디어입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 기본 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 파일 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_read"></a>fx_file_read

파일의 바이트를 읽습니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a>Description

이 서비스는 파일에서 바이트를 읽은 다음 제공된 버퍼에 저장합니다. 읽기가 완료되면 파일의 내부 읽기 포인터가 파일의 다음 바이트를 가리키도록 조정됩니다. 요청에 남아 있는 바이트 수가 적으면 남은 바이트만 버퍼에 저장됩니다. 어떤 경우든 버퍼에 배치된 총 바이트 수가 호출자에게 반환됩니다.

> [!WARNING]
> 애플리케이션은 제공된 버퍼가 지정된 요청 바이트 수를 저장할 수 있는지 확인해야 합니다.

> [!WARNING]
> 대상 버퍼가 긴 단어 경계에 있고 요청된 크기가 sizeof(**ULONG**)로 균등하게 나눌 수 있는 경우 성능이 향상됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 파일 제어 블록에 대한 포인터입니다.
- **buffer_ptr**: 읽기의 대상 버퍼에 대한 포인터입니다.
- **request_size**: 읽을 최대 바이트 수입니다.
- **actual_size**: 읽은 실제 바이트 수를 제공된 버퍼에 저장하는 변수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 읽기에 성공했습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.
- **FX_FILE_CORRUPT**(0x08) 지정된 파일이 손상되어 읽지 못했습니다.
- **FX_END_OF_FILE**(0x09) 파일의 끝에 도달했습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 파일 또는 버퍼 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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
### <a name="see-also"></a>참고 항목

- fx_file_allocate,
- fx_file_attributes_read,
- fx_file_attributes_set,
- fx_file_best_effort_allocate,
- fx_file_close,
- fx_file_create,
- fx_file_date_time_set,
- fx_file_delete,
- fx_file_extended_allocate,
- fx_file_extended_best_effort_allocate,
- fx_file_extended_relative_seek,
- fx_file_extended_seek,
- fx_file_extended_truncate,
- fx_file_extended_truncate_release,
- fx_file_open,
- fx_file_relative_seek,
- fx_file_rename,
- fx_file_seek,
- fx_file_truncate,
- fx_file_truncate_release,
- fx_file_write,
- fx_file_write_notify_set,
- fx_unicode_file_create,
- fx_unicode_file_rename,
- fx_unicode_name_get,
- fx_unicode_short_name_get

## <a name="fx_file_relative_seek"></a>fx_file_relative_seek

상대 바이트 오프셋에 대한 위치입니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Description

이 서비스는 내부 파일 읽기/쓰기 포인터를 지정된 상대 바이트 오프셋에 배치합니다. 모든 후속 파일 읽기 또는 쓰기 요청은 파일의 이 위치에서 시작됩니다.

> [!IMPORTANT]
> 찾기 작업이 파일의 끝을 지나 찾으려고 하면 파일의 읽기/쓰기 포인터가 파일의 끝에 배치됩니다. 반대로 찾기 작업이 파일의 시작 부분을 지나서 배치하려고 하면 파일의 읽기/쓰기 포인터가 파일의 시작 부분에 배치됩니다.

4GB를 초과하는 오프셋 값으로 찾으려면 애플리케이션이 *fx_file_extended_relative_seek* 서비스를 사용해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 이전에 연 파일에 대한 포인터입니다.
- **byte_offset**: 파일에서 원하는 상대 바이트 오프셋입니다.
- **seek_from**: 상대 찾기를 수행할 방향과 위치입니다. 유효한 찾기 옵션은 다음과 같이 정의됩니다.
  - FX_SEEK_BEGIN(0x00)
  - FX_SEEK_END(0x01)
  - FX_SEEK_FORWARD(0x02)
  - FX_SEEK_BACK(0x03)

FX_SEEK_BEGIN이 지정된 경우 찾기 작업은 파일의 시작 부분에서 수행됩니다. FX_SEEK_END가 지정된 경우 찾기 작업은 파일의 끝에서 뒤로 수행됩니다. FX_SEEK_FORWARD가 지정된 경우 찾기 작업은 현재 파일 위치에서 정방향으로 수행됩니다. FX_SEEK_BACK이 지정된 경우 찾기 작업은 현재 파일 위치에서 역방향으로 수행됩니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 상대 검색에 성공했습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_rename"></a>fx_file_rename

파일 이름을 바꿉니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a>Description

이 서비스는 *old_file_name* 으로 지정된 파일의 이름을 변경합니다. 지정된 경로 또는 기본 경로를 기준으로 이름이 바뀝니다. 새 파일 이름에 경로가 지정된 경우 이름이 바뀐 파일이 실제로 지정된 경로로 이동합니다. 지정된 경로가 없으면 이름이 바뀐 파일이 현재 기본 경로에 배치됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **old_file_name**: 이름을 바꿀 파일의 이름에 대한 포인터입니다(디렉터리 경로는 선택 사항임).
- **new_file_name**: 새 파일 이름에 대한 포인터입니다. 디렉터리 경로가 허용되지 않습니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 이름 바꾸기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 지정된 파일을 찾을 수 없습니다.
- **FX_NOT_A_FILE**(0x05) 지정된 파일이 디렉터리입니다.
- **FX_ACCESS_ERROR**(0x06) 지정된 파일이 이미 열려 있습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_INVALID_NAME**(0x0C) 지정된 새 파일 이름이 유효한 파일 이름이 아닙니다.
- **FX_INVALID_PATH**(0x0D) 경로가 잘못되었습니다.
- **FX_ALREADY_CREATED**(0x0B) 새 파일 이름이 사용됩니다.
- **FX_MEDIA_INVALID**(0x02) 미디어가 잘못되었습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 테이블을 읽을 수 없습니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_seek"></a>fx_file_seek

바이트 오프셋에 대한 위치

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a>Description

이 서비스는 내부 파일 읽기/쓰기 포인터를 지정된 바이트 오프셋에 배치합니다. 모든 후속 파일 읽기 또는 쓰기 요청은 파일의 이 위치에서 시작됩니다.

4GB를 초과하는 오프셋 값으로 찾으려면 애플리케이션이 *fx_file_extended_seek* 서비스를 사용해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 파일 제어 블록에 대한 포인터입니다.
- **byte_offset**: 파일에서 원하는 바이트 오프셋입니다. 값이 0이면 파일의 시작 부분에 읽기/쓰기 포인터가 배치되고 값이 파일의 크기보다 크면 파일의 끝에 읽기/쓰기 포인터를 배치합니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 검색에 성공했습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate"></a>fx_file_truncate

파일을 자릅니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a>Description

이 서비스는 파일의 크기를 지정된 크기로 자릅니다. 제공된 크기가 실제 파일 크기보다 크면 이 서비스는 아무것도 수행하지 않습니다. 파일과 연결된 미디어 클러스터 중 해제된 클러스터가 없습니다.

> [!WARNING]
> 읽으려고 동시에 열 수 있는 파일을 잘라낼 때는 주의해야 합니다. 읽기 위해 열려 있는 파일을 자르면 잘못된 데이터를 읽을 수 있습니다.

4GB를 초과하여 작동하기 위해 애플리케이션은 *fx_file_extended_truncate* 서비스를 사용해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 파일 제어 블록에 대한 포인터입니다.
- **size**: 새 파일 크기입니다. 이 새 파일 크기를 벗어난 바이트는 무시됩니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 자르기에 성공했습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.
- **FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate_release"></a>fx_file_truncate_release

파일을 자르고 클러스터를 해제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a>Description

이 서비스는 파일의 크기를 지정된 크기로 자릅니다. 제공된 크기가 실제 파일 크기보다 크면 이 서비스는 아무것도 수행하지 않습니다. ***Fx_file_truncate*** 서비스와 달리 이 서비스는 사용되지 않는 클러스터를 모두 해제합니다.

> [!WARNING]
> 읽으려고 동시에 열 수 있는 파일을 잘라낼 때는 주의해야 합니다. 읽기 위해 열려 있는 파일을 자르면 잘못된 데이터를 읽을 수 있습니다.

4GB를 초과하여 작동하기 위해 애플리케이션은 *fx_file_extended_truncate_release* 서비스를 사용해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 이전에 연 파일에 대한 포인터입니다.
- **size**: 새 파일 크기입니다. 이 새 파일 크기를 벗어난 바이트는 무시됩니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 자르기에 성공했습니다.
- **FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 현재 열려 있지 않습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류.
- **FX_WRITE_PROTECT**(0x23) 기본 미디어가 쓰기 금지되어 있습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_NO_MORE_SPACE**(0x0A) 작업을 완료하기 위한 공간이 없습니다.
- **FX_PTR_ERROR**(0x18) 파일 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_write"></a>fx_file_write

파일에 바이트를 씁니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a>Description

이 서비스는 파일의 현재 위치부터 시작하여 지정된 버퍼의 바이트를 씁니다. 쓰기가 완료되면 파일의 내부 읽기 포인터가 파일의 다음 바이트를 가리키도록 조정됩니다.

> [!WARNING]
> 원본 버퍼가 긴 단어 경계에 있고 요청된 크기가 sizeof(**ULONG**)로 균등하게 나눌 수 있는 경우 성능이 향상됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 파일 제어 블록에 대한 포인터입니다.
- **buffer_ptr**: 쓰기의 원본 버퍼에 대한 포인터입니다.
- **size**: 쓸 바이트 수입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 쓰기에 성공했습니다.
- **FX_NOT_OPEN**(0x07) 지정된 파일이 열려 있지 않습니다.
- **FX_ACCESS_ERROR**(0x06) 지정된 파일이 쓰기용으로 열려 있지 않습니다.
- **FX_NO_MORE_SPACE**(0x0A) 이번에 쓰는 데 사용할 수 있는 공간이 미디어에 더 이상 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 항목을 읽을 수 없습니다.
- **FX_NO_MORE_ENTRIES**(0x0F) FAT 항목이 더 없습니다.
- **FX_PTR_ERROR**(0x18) 파일 또는 버퍼 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a>참고 항목

- fx_file_allocate,
- fx_file_attributes_read,
- fx_file_attributes_set,
- fx_file_best_effort_allocate,
- fx_file_close,
- fx_file_create,
- fx_file_date_time_set,
- fx_file_delete,
- fx_file_extended_allocate,
- fx_file_extended_best_effort_allocate,
- fx_file_extended_relative_seek,
- fx_file_extended_seek,
- fx_file_extended_truncate,
- fx_file_extended_truncate_release,
- fx_file_open,
- fx_file_read,
- fx_file_relative_seek,
- fx_file_rename,
- fx_file_seek,
- fx_file_truncate,
- fx_file_truncate_release,
- fx_file_write_notify_set,
- fx_unicode_file_create,
- fx_unicode_file_rename,
- fx_unicode_name_get,
- fx_unicode_short_name_get

## <a name="fx_file_write_notify_set"></a>fx_file_write_notify_set

파일 쓰기 알림 기능을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a>Description

이 서비스는 파일 쓰기 작업에 성공한 후 호출되는 콜백 함수를 설치합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **file_ptr**: 파일 제어 블록에 대한 포인터입니다.
- **file_write_notify**: 설치할 파일 쓰기 콜백 함수입니다. 콜백 함수를 NULL로 설정하면 콜백 함수가 사용하지 않도록 설정됩니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 콜백 함수 설치에 성공했습니다.
- **FX_PTR_ERROR**(0x18) file_ptr이 NULL입니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_media_abort"></a>fx_media_abort

미디어 작업을 중단합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Description

이 서비스는 열려 있는 모든 파일 닫기, 연결된 드라이버로 중단 요청 보내기, 미디어를 중단된 상태로 전환 등 미디어와 관련된 모든 현재 작업을 중단합니다. 이 서비스는 I/O 오류가 검색될 때 일반적으로 호출됩니다.

> [!WARNING]
> 중단 작업을 수행한 후 다시 사용하려면 미디어를 다시 열어야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 중단에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

논리 섹터 캐시를 무효화합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Description

이 서비스는 캐시에 있는 모든 더티 섹터를 플러시하고 전체 논리 섹터 캐시를 무효화합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 캐시 무효화에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 스크래치 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_check"></a>fx_media_check

오류가 있는지 미디어를 확인합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 미디어에서 파일/디렉터리 교차 링크, 잘못된 FAT 체인, 손실된 클러스터를 비롯한 기본 구조 오류가 있는지 확인합니다. 또한 검색된 오류를 수정하는 기능을 제공합니다.

fx_media_check 서비스를 사용하려면 미디어의 디렉터리와 파일에 대한 깊이 우선 분석을 위한 스크래치 메모리가 필요합니다. 특히, 미디어 검사 서비스에 제공되는 스크래치 메모리는 여러 디렉터리 항목, 하위 디렉터리에 입력하기 전에 현재 디렉터리 항목 위치를 “스택”하기 위한 데이터 구조, 마지막으로 논리적 FAT 비트맵을 포함하는 데이터 구조를 저장할 만큼 충분히 커야 합니다. 스크래치 메모리는 최소 512~1024바이트에 논리적 FAT 비트맵을 위한 메모리를 더한 크기여야 합니다. 논리적 FAT 비트맵에는 미디어에 있는 클러스터만큼의 비트가 필요합니다. 예를 들어 클러스터가 8000개 있는 디바이스는 1000바이트가 필요한 것으로 표시되므로 필요한 총 스크래치 영역은 약 2048바이트입니다.

> [!WARNING]
> 이 서비스는 fx_media_open 직후 다른 파일 시스템 작업 없이 바로 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **scratch_memory_ptr**: 스크래치 메모리의 시작에 대한 포인터입니다.
- **scratch_memory_size**: 스크래치 메모리 크기입니다(바이트).
- **error_correction_option**: 오류 수정 옵션 비트입니다. 비트가 설정된 경우 오류가 수정됩니다. 오류 수정 옵션 비트는 다음과 같이 정의됩니다.
  - FX_FAT_CHAIN_ERROR(0x01)
  - FX_DIRECTORY_ERROR(0x02)
  - FX_LOST_CLUSTER_ERROR(0x04) 필요한 오류 수정 옵션을 간단하게 사용하거나 함께 사용합니다. 오류 수정이 필요하지 않은 경우 0 값을 제공해야 합니다.
- **errors_detected_ptr**: 아래 정의된 것처럼 오류 검색 비트의 대상입니다.
  - FX_FAT_CHAIN_ERROR(0x01)
  - FX_DIRECTORY_ERROR(0x02) FX_LOST_CLUSTER_ERROR(0x04)
  - FX_FILE_SIZE_ERROR(0x08)

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 검색에 성공했습니다. 자세한 내용은 오류 감지 대상을 확인하세요.
- **FX_ACCESS_ERROR**(0x06) 파일이 열려 있는 상태에서는 검사를 수행할 수 없습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NO_MORE_SPACE**(0x0A) 미디어에 공간이 더 이상 없습니다.
- **FX_NOT_ENOUGH_MEMORY**(0x91) 제공된 스크래치 메모리가 충분히 크지 않습니다.
- **FX_ERROR_NOT_FIXED**(0x93) 수정할 수 없는 FAT32 루트 디렉터리가 손상되었습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_SECTOR_INVALID**(0x89) 섹터가 잘못되었습니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 스크래치 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.


### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close"></a>fx_media_close

미디어를 닫습니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 미디어를 닫습니다. 미디어를 닫는 과정에서 열려 있는 파일이 모두 닫히고 나머지 버퍼는 실제 미디어로 플러시됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 닫기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close_notify_set"></a>fx_media_close_notify_set

미디어 닫기 알림 함수를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a>Description

이 서비스는 미디어가 닫힌 후 호출될 알림 콜백 함수를 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **media_close_notify**: 설치할 미디어 닫기 알림 콜백 함수입니다. 콜백 함수로 NULL을 전달하면 미디어 닫기 콜백이 사용하지 않도록 설정됩니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 콜백 함수 설치에 성공했습니다.
- **FX_PTR_ERROR**(0x18) media_ptr이 NULL입니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_exfat_format"></a>fx_media_exFAT_format

미디어를 포맷합니다.

### <a name="prototype"></a>프로토타입

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
### <a name="description"></a>Description

이 서비스는 제공된 매개 변수에 따라 exFAT 호환 방식으로 제공된 미디어를 포맷합니다. 미디어를 열기 전에 이 서비스를 호출해야 합니다.

> [!WARNING]
> 이미 포맷된 미디어를 포맷하면 미디어의 파일과 디렉터리가 실제로 모두 지워집니다.

> [!IMPORTANT]
> *exFAT 볼륨 크기는 파티션의 크기(MBR 또는 GPT 레이아웃이 있는 경우) 또는 파티션 레이아웃이 없는 경우(MBR 또는 GPT 없음) 전체 디바이스의 크기와 일치해야 합니다. Windows에는 사용 가능한 섹터보다 적은 총 섹터 값으로 포맷된 경우 exFAT 디스크가 다시 인식되지 않는다는 제한이 있습니다.*

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다. 드라이버가 작동하는 데 필요한 몇 가지 기본적인 정보를 제공하기 위해서만 사용됩니다.
- **driver**: 미디어의 I/O 드라이버에 대한 포인터입니다. 일반적으로 후속 fx_media_open 호출에 제공되는 것과 동일한 드라이버입니다.
- **driver_info_ptr**: I/O 드라이버가 활용할 수 있는 선택적 정보에 대한 포인터입니다.
- **memory_ptr**: 미디어의 작업 메모리에 대한 포인터입니다. memory_size는 작업 미디어 메모리의 크기를 지정합니다. 크기는 적어도 미디어의 섹터 크기보다 커야 합니다.
- **volume_name**: 최대 11자인 볼륨 이름 문자열에 대한 포인터입니다.
- **number_of_fats**: 미디어의 FAT 수입니다. 현재 구현에서는 미디어에서 FAT를 하나만 지원합니다.
- **hidden_sectors**: 미디어의 부팅 섹터 앞에 숨겨진 섹터 수입니다. 파티션이 여러 개 있는 경우 일반적입니다.
- **total_sectors**: 미디어의 총 섹터 수입니다.
- **bytes_per_sector**: 섹터당 바이트 수로, 일반적으로 512입니다. FileX에서는 32의 배수여야 합니다.
> [!IMPORTANT]
> *사양과 관련하여, 섹터당 바이트는 512, 1024, 2048 또는 4096 값만 사용할 수 있습니다.*

- **sectors_per_cluster**: 각 클러스터의 섹터 수입니다. 클러스터는 FAT 파일 시스템의 최소 할당 단위입니다.
- **volumne_serial_number**: 볼륨에 사용할 일련 번호입니다.
- **boundary_unit**: 실제 데이터 영역 맞춤 크기입니다(섹터 수).

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 포맷에 성공했습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 미디어, 드라이버 또는 메모리 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_extended_space_available"></a>fx_media_extended_space_available

사용 가능한 미디어 공간을 반환합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a>Description

이 서비스는 미디어에서 사용할 수 있는 바이트 수를 반환합니다.

이 서비스는 exFAT용으로 설계되었습니다. *available_bytes* 매개 변수에 대한 포인터는 64비트 정수 값을 사용합니다. 따라서 호출자가 4GB 범위를 벗어나 미디어를 사용할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 이전에 열린 미디어에 대한 포인터입니다.
- **available_bytes_ptr**: 미디어에 남아 있는 사용 가능한 바이트입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어에서 사용 가능한 공간 검색에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었거나 사용 가능한 바이트 포인터가 NULL입니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_flush"></a>fx_media_flush

실제 미디어로 데이터를 플러시합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Description

이 서비스는 캐시된 섹터와 수정된 파일의 디렉터리 항목을 모두 실제 미디어로 플러시합니다.

> [!WARNING]
> 대상에서 갑작스러운 정전 발생 시 파일 손상 및/또는 데이터 손실 위험을 줄이기 위해 애플리케이션에서 이 루틴을 주기적으로 호출할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 플러시에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_format"></a>fx_media_format

미디어를 포맷합니다.

### <a name="prototype"></a>프로토타입

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
### <a name="description"></a>Description

이 서비스는 제공된 매개 변수에 따라 FAT 12/16/32 호환 방식으로 제공된 미디어를 포맷합니다. 미디어를 열기 전에 이 서비스를 호출해야 합니다.

> [!WARNING]
> 이미 포맷된 미디어를 포맷하면 미디어의 파일과 디렉터리가 실제로 모두 지워집니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다. 드라이버가 작동하는 데 필요한 몇 가지 기본적인 정보를 제공하기 위해서만 사용됩니다.
- **driver**: 미디어의 I/O 드라이버에 대한 포인터입니다. 일반적으로 후속 fx_media_open 호출에 제공되는 것과 동일한 드라이버입니다.
- **driver_info_ptr**: I/O 드라이버가 활용할 수 있는 선택적 정보에 대한 포인터입니다.
- **memory_ptr**: 미디어의 작업 메모리에 대한 포인터입니다.
- **memory_size**: 작업 미디어 메모리의 크기를 지정합니다. 크기는 적어도 미디어의 섹터 크기보다 커야 합니다.
- **volume_name**: 최대 11자인 볼륨 이름 문자열에 대한 포인터입니다.
- **number_of_fats**: 미디어의 FAT 수입니다. 기본 FAT가 있기 때문에 최솟값은 1입니다. 값이 1보다 크면 런타임에 유지 관리 중인 추가 FAT 복사본이 있는 것입니다.
- **directory_entries**: 루트 디렉터리의 디렉터리 항목 수입니다.
- **hidden_sectors**: 미디어의 부팅 섹터 앞에 숨겨진 섹터 수입니다. 파티션이 여러 개 있는 경우 일반적입니다.
- **total_sectors**: 미디어의 총 섹터 수입니다.
- **bytes_per_sector**: 섹터당 바이트 수로, 일반적으로 512입니다. FileX에서는 32의 배수여야 합니다.
> [!IMPORTANT]
> *사양과 관련하여, 섹터당 바이트는 512, 1024, 2048 또는 4096 값만 사용할 수 있습니다.*

- **sectors_per_cluster**: 각 클러스터의 섹터 수입니다. 클러스터는 FAT 파일 시스템의 최소 할당 단위입니다.
- **heads**: 실제 헤드 수입니다.
- **sectors_per_track**: 트랙당 섹터 수입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 포맷에 성공했습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 미디어, 드라이버 또는 메모리 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open"></a>fx_media_open

파일 액세스하기 위한 미디어를 엽니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a>Description

이 서비스는 제공된 I/O 드라이버를 사용하여 파일에 액세스하기 위한 미디어를 엽니다.

> [!WARNING]
> 이 서비스에 제공되는 메모리는 내부 논리 섹터 캐시를 구현하는 데 사용되므로 더 많은 메모리가 제공될수록 실제 I/O는 더 줄어듭니다. FileX에는 최소한 한 개의 논리 섹터 캐시가 필요합니다(미디어의 섹터당 바이트 수).

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **media_name**: 미디어 이름에 대한 포인터입니다.
- **media_driver**: 미디어의 I/O 드라이버에 대한 포인터입니다. I/O 드라이버는 5장에서 정의한 FileX 드라이버 요구 사항을 준수해야 합니다.
- **driver_info_ptr**: 제공된 I/O 드라이버가 활용할 수 있는 선택적 정보에 대한 포인터입니다.
- **memory_ptr**: 미디어의 작업 메모리에 대한 포인터입니다.
- **memory_size**: 작업 미디어 메모리의 크기를 지정합니다. 크기는 미디어의 섹터 크기만큼(일반적으로 512 바이트) 커야 합니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 열기에 성공했습니다.
- **FX_BOOT_ERROR**(0x01) 미디어의 부팅 섹터를 읽는 중 오류가 발생했습니다.
- **FX_MEDIA_INVALID**(0x02) 지정된 미디어의 부팅 섹터가 손상되었거나 잘못되었습니다. 또한 이 반환 코드는 논리 섹터 캐시 크기나 FAT 항목 크기가 2의 거듭제곱이 아님을 나타내는 데 사용됩니다.
- **FX_FAT_READ_ERROR**(0x03) 미디어 FAT를 읽는 중 오류가 발생했습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 하나 이상의 포인터가 NULL입니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open_notify_set"></a>fx_media_open_notify_set

미디어 열기 알림 기능을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a>Description

이 서비스는 미디어가 열린 후 호출될 알림 콜백 함수를 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **media_open_notify**: 설치할 미디어 열기 알림 콜백 함수입니다. 콜백 함수로 NULL을 전달하면 미디어 열기 콜백이 사용하지 않도록 설정됩니다.

### <a name="return-values"></a>반환 값


- **FX_SUCCESS**(0x00) 콜백 함수 설치에 성공했습니다.
- **FX_PTR_ERROR**(0x18) media_ptr이 NULL입니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_read"></a>fx_media_read

미디어에서 논리 섹터를 읽습니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a>Description

이 서비스는 미디어에서 논리 섹터를 읽어 제공된 버퍼에 배치합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 이전에 열린 미디어에 대한 포인터입니다.
- **logical_sector**: 읽을 논리 섹터입니다.
- **buffer_ptr**: 논리 섹터 읽기를 위한 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 읽기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 버퍼 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_space_available"></a>fx_media_space_available

사용 가능한 미디어 공간을 반환합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a>Description

이 서비스는 미디어에서 사용할 수 있는 바이트 수를 반환합니다.

4GB보다 큰 미디어를 사용하여 작업하려면 애플리케이션이 *fx_media_extended_space_available* 서비스를 사용해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 이전에 열린 미디어에 대한 포인터입니다.
- **available_bytes_ptr**: 미디어에 남아 있는 사용 가능한 바이트입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어에서 사용 가능한 공간 반환에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었거나 사용 가능한 바이트 포인터가 NULL입니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get"></a>fx_media_volume_get

미디어 볼륨 이름을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a>Description

이 서비스는 이전에 열린 미디어의 볼륨 이름을 검색합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **volume_name**: 볼륨 이름의 대상에 대한 포인터입니다. 대상은 최소한 12자를 포함할 수 있을 정도로 커야 합니다.
- **volume_source**: 부팅 섹터 또는 루트 디렉터리에서 이름을 검색할 위치를 지정합니다. 이 매개 변수에 유효한 값은 다음과 같습니다.
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 볼륨 가져오기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 볼륨을 찾을 수 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 볼륨 대상 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get_extended"></a>fx_media_volume_get_extended

이전에 열린 미디어의 미디어 볼륨 이름을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a>Description

이 서비스는 이전에 열린 미디어의 볼륨 이름을 검색합니다.

> [!IMPORTANT]
> 이 서비스는 호출자가 _ *volume_name** 버퍼의 크기를 전달한다는 점을 제외하면 ***fx_media_volume_get()** _와 동일합니다.

### <a name="input-parameters"></a>입력 매개 변수


- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **volume_name**: 볼륨 이름의 대상에 대한 포인터입니다. 대상은 최소한 12자를 포함할 수 있을 정도로 커야 합니다.
- **volume_name_buffer_length**: volume_name 버퍼의 크기입니다.
- **volume_source**: 부팅 섹터 또는 루트 디렉터리에서 이름을 검색할 위치를 지정합니다. 이 매개 변수에 유효한 값은 다음과 같습니다.
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 볼륨 가져오기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 볼륨을 찾을 수 없습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 볼륨 대상 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_set"></a>fx_media_volume_set

미디어 볼륨 이름을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a>Description

이 서비스는 이전에 열린 미디어의 볼륨 이름을 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **volume_name**: 볼륨 이름에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 볼륨 설정에 성공했습니다.
- **FX_INVALID_NAME**(0x0C) Volume_name이 잘못되었습니다.
- **FX_MEDIA_INVALID**(0x02) 볼륨 이름을 설정할 수 없습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 볼륨 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_write
- fx_system_initialize

## <a name="fx_media_write"></a>fx_media_write

논리 섹터를 씁니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 논리 섹터에 제공된 버퍼를 씁니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 이전에 열린 미디어에 대한 포인터입니다.
- **logical_sector**: 쓸 논리 섹터입니다.
- **buffer_ptr**: 논리 섹터 쓰기의 원본에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 쓰기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 미디어 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_system_initialize

## <a name="fx_system_date_get"></a>fx_system_date_get

파일 시스템 날짜를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a>Description

이 서비스는 현재 시스템 날짜를 반환합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **year**: 연도의 대상에 대한 포인터입니다.
- **month**: 월의 대상에 대한 포인터입니다.
- **day**: 날짜의 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 날짜 검색에 성공했습니다.
- **FX_PTR_ERROR**(0x18) 하나 이상의 입력 매개 변수가 NULL입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_system_date_set
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_date_set"></a>fx_system_date_set

시스템 날짜를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a>Description

이 서비스는 지정된 대로 시스템 날짜를 설정합니다.

> [!WARNING]
> 초기 시스템 날짜를 설정하려면 **fx_system_initialize** 직후에 서비스를 호출해야 합니다. 기본적으로 시스템 날짜는 마지막 일반 FileX 릴리스의 날짜입니다.

### <a name="input-parameters"></a>입력 매개 변수

- **year**: 새 연도입니다. 유효 범위는 1980~2107년입니다.
- **month**: 새 월입니다. 유효 범위는 1~12입니다.
- **day**: 새 날짜입니다. 유효 범위는 월과 윤년 조건에 따라 1~31입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 날짜 설정에 성공했습니다.
- **FX_INVALID_YEAR**(0x12) 지정된 연도가 잘못되었습니다.
- **FX_INVALID_MONTH**(0x13) 지정된 월이 잘못되었습니다.
- **FX_INVALID_DAY**(0x14) 지정된 날짜가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a>참고 항목

- fx_system_date_get
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_initialize"></a>fx_system_initialize

전체 시스템을 초기화합니다.

### <a name="prototype"></a>프로토타입

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a>Description

이 서비스는 모든 주요 FileX 데이터 구조를 초기화합니다. ***Tx_application_define*** 에서 호출해야 하며 초기화 스레드에서 호출할 수도 있고 기타 모든 FileX 서비스를 사용하기 전에 호출해야 합니다.

> [!WARNING]
> *이와 같이 호출하여 초기화되면 애플리케이션은 **fx_system_date_set** _ 및 _ *fx_system_time_set**을 호출하여 정확한 시스템 날짜와 시간으로 시작해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

None

### <a name="return-values"></a>반환 값

없음

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_system_date_get
- fx_system_date_set
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_time_get"></a>fx_system_time_get

현재 시스템 시간을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a>Description

이 서비스는 현재 시스템 시간을 검색합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **hour**: 시간의 대상에 대한 포인터입니다.
- **minute**: 분의 대상에 대한 포인터입니다.
- **second**: 초의 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 시스템 시간 검색에 성공했습니다.
- **FX_PTR_ERROR**(0x18) 하나 이상의 입력 매개 변수입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_set

## <a name="fx_system_time_set"></a>fx_system_time_set

현재 시스템 시간을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a>Description

이 서비스는 현재 시스템 시간을 입력 매개 변수로 지정된 시간으로 설정합니다.

> [!WARNING]
> 초기 시스템 시간을 설정하려면 **fx_system_initialize** 직후 이 서비스를 호출해야 합니다. 기본적으로 시스템 시간은 0:0:0입니다.

### <a name="input-parameters"></a>입력 매개 변수

- **hour**: 새 시간입니다(0~23).
- **분**: 새 분입니다(0~59).
- **초**: 새 초입니다(0~59).

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 시스템 시간 검색에 성공했습니다.
- **FX_INVALID_HOUR**(0x15) 새 시간이 잘못되었습니다.
- **FX_INVALID_MINUTE**(0x16) 새 분이 잘못되었습니다.
- **FX_INVALID_SECOND**(0x17) 새 초가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a>참고 항목

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_get

## <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create

유니코드 디렉터리를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a>Description

이 서비스는 현재 기본 디렉터리에 유니코드 이름이 지정된 하위 디렉터리를 만듭니다. 유니코드 원본 이름 매개 변수에는 경로 정보가 허용되지 않습니다. 성공하면 서비스에서 새로 만든 유니코드 하위 디렉터리의 짧은 이름(8.3 형식)을 반환합니다.

> [!WARNING]
> 반환된 짧은 이름(8.3 형식)을 표준 FileX 디렉터리 서비스에 제공하여 유니코드 하위 디렉터리에 대한 모든 작업(이 디렉터리를 기본 경로로 설정, 삭제 등)을 수행해야 합니다.

> [!IMPORTANT]
> 이 서비스는 exFAT 미디어에서 지원되지 않습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **source_unicode_name**: 새 하위 디렉터리의 유니코드 이름에 대한 포인터입니다.
- **source_unicode_length**: 유니코드 이름의 길이입니다.
- **short_name**: 새 유니코드 하위 디렉터리의 짧은 이름(8.3 형식) 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 유니코드 디렉터리 만들기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_ALREADY_CREATED**(0x0B) 지정한 디렉터리가 이미 있습니다.
- **FX_NO_MORE_SPACE**(0x0A) 새 디렉터리 항목의 미디어에 사용 가능한 클러스터가 더 이상 없습니다.
- **FX_NOT_IMPLEMENTED**(0x22) exFAT 파일 시스템을 위해 서비스가 구현되지 않았습니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.
- **FX_IO_ERROR(0x90)** 드라이버 I/O 오류.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_rename

## <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

유니코드 문자열을 사용하여 디렉터리 이름을 바꿉니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a>Description

이 서비스는 유니코드 이름이 지정된 하위 디렉터리를 현재 작업 디렉터리의 지정된 새 유니코드 이름으로 변경합니다. 유니코드 이름 매개 변수에는 경로 정보가 없어야 합니다.

> [!IMPORTANT]
> 이 서비스는 exFAT 미디어에서 지원되지 않습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **old_unicode_name**: 현재 파일의 유니코드 이름에 대한 포인터입니다.
- **old_unicode_name_length**: 현재 유니코드 이름의 길이입니다.
- **new_unicode_name**: 새 유니코드 파일 이름에 대한 포인터입니다.
- **old_unicode_name_length**: 새 유니코드 이름의 길이입니다.
- **new_short_name**: 이름이 바뀐 유니코드 파일의 짧은 이름(8.3 형식)의 대상에 대한 포인터입니다. 유니코드로 디렉터리 이름을 바꿉니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 미디어 열기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_ALREADY_CREATED**(0x0B) 지정한 디렉터리 이름이 이미 있습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 하나 이상의 포인터가 NULL입니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_unicode_file_create"></a>fx_unicode_file_create

유니코드 파일을 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a>Description

이 서비스는 현재 기본 디렉터리에 유니코드 이름이 지정된 파일을 만듭니다. 유니코드 원본 이름 매개 변수에는 경로 정보가 허용되지 않습니다. 성공하면 서비스에서 새로 만든 유니코드 파일의 짧은 이름(8.3 형식)을 반환합니다.

> [!WARNING]
> 유니코드 파일에 대한 모든 작업(열기, 쓰기, 읽기, 닫기 등)은 표준 FileX 파일 서비스에 반환된 짧은 이름(8.3 형식)을 제공하여 수행해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수


- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **source_unicode_name**: 새 파일의 유니코드 이름에 대한 포인터입니다.
- **source_unicode_length**: 유니코드 이름의 길이입니다.
- **short_name**: 새 유니코드 파일의 짧은 이름(8.3 형식) 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 파일 만들기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_ALREADY_CREATED**(0x0B) 지정된 파일이 이미 있습니다.
- **FX_NO_MORE_SPACE**(0x0A) 새 파일 항목의 미디어에 사용 가능한 클러스터가 더 이상 없습니다.
- **FX_NOT_IMPLEMENTED**(0x22) exFAT 파일 시스템을 위해 서비스가 구현되지 않았습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

유니코드 문자열을 사용하여 파일 이름을 바꿉니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a>Description

이 서비스는 유니코드 이름이 지정된 파일 이름을 현재 기본 디렉터리의 지정된 새 유니코드 이름으로 변경합니다. 유니코드 이름 매개 변수에는 경로 정보가 없어야 합니다.

> [!IMPORTANT]
> 이 서비스는 exFAT 미디어에서 지원되지 않습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **old_unicode_name**: 현재 파일의 유니코드 이름에 대한 포인터입니다.
- **old_unicode_name_length**: 현재 유니코드 이름의 길이입니다.
- **new_unicode_name**: 새 유니코드 파일 이름에 대한 포인터입니다.
- **new_unicode_name_length**: 새 유니코드 이름의 길이입니다.
- **new_short_name**: 이름이 바뀐 유니코드 파일의 짧은 이름(8.3 형식)의 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값


- **FX_SUCCESS**(0x00) 미디어 열기에 성공했습니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_ALREADY_CREATED**(0x0B) 지정된 파일 이름이 이미 있습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_PTR_ERROR**(0x18) 하나 이상의 포인터가 NULL입니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.
- **FX_WRITE_PROTECT**(0x23) 지정된 미디어가 쓰기 금지되어 있습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get"></a>fx_unicode_length_get

유니코드 이름의 길이를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a>Description

이 서비스는 제공된 유니코드 이름의 길이를 확인합니다. 유니코드 문자는 2바이트로 표시됩니다. 유니코드 이름은 두 개의 NULL 바이트(0 값은 2바이트)로 끝나는 일련의 2바이트 유니코드 문자입니다.

### <a name="input-parameters"></a>입력 매개 변수

**unicode_name**: 유니코드 이름에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

**length**: 유니코드 이름의 길이입니다(이름의 유니코드 문자 수).

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get_extended"></a>fx_unicode_length_get_extended

유니코드 이름의 길이를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a>Description

이 서비스는 제공된 유니코드 이름의 길이를 가져옵니다. 유니코드 문자는 2바이트로 표시됩니다. 유니코드 이름은 두 개의 NULL 바이트(0 값은 2바이트)로 끝나는 일련의 2바이트 유니코드 문자입니다.

> [!IMPORTANT]
> 이 서비스는 호출자가 NULL 문자 두 개를 비롯하여 **unicode_name** 버퍼의 크기를 전달한다는 점을 제외하면 **fx_unicode_length_get()** 과 동일합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **unicode_name**: 유니코드 이름에 대한 포인터입니다.
- **buffer_length**: 유니코드 이름 버퍼의 크기입니다.

### <a name="return-values"></a>반환 값

**length**: 유니코드 이름의 길이입니다(이름의 유니코드 문자 수).

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get"></a>fx_unicode_name_get

짧은 이름에서 유니코드 이름을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a>Description

이 서비스는 현재 기본 디렉터리 내에서 제공된 짧은 이름(8.3 형식)과 연결된 유니코드 이름을 검색합니다. 짧은 이름 매개 변수에는 경로 정보가 허용되지 않습니다. 성공하면 서비스에서 짧은 이름과 연결된 유니코드 이름을 반환합니다.

> [!IMPORTANT]
> 이 서비스를 사용하여 파일과 하위 디렉터리의 유니코드 이름을 가져올 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **short_name** 짧은 이름(8.3 형식)에 대한 포인터입니다.
- **destination_unicode_name**: 제공된 짧은 이름과 연결된 유니코드 이름의 대상에 대한 포인터입니다.
- **destination_unicode_length**: 반환된 유니코드 이름 길이에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 유니코드 이름 검색에 성공했습니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 테이블을 읽을 수 없습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 짧은 이름을 찾을 수 없거나 유니코드 대상 크기가 너무 작습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get_extended"></a>fx_unicode_name_get_extended

짧은 이름에서 유니코드 이름을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a>Description

이 서비스는 현재 기본 디렉터리 내에서 제공된 짧은 이름(8.3 형식)과 연결된 유니코드 이름을 검색합니다. 짧은 이름 매개 변수에는 경로 정보가 허용되지 않습니다. 성공하면 서비스에서 짧은 이름과 연결된 유니코드 이름을 반환합니다.

> [!IMPORTANT]
> *이 서비스는 호출자가 대상 유니코드 버퍼의 크기를 입력 인수로 제공한다는 점을 제외하면 ***fx_unicode_name_get** 과 동일합니다. 따라서 서비스가 대상 유니코드 버퍼를 덮어쓰지 않음을 보장할 수 있습니다.

> [!IMPORTANT]
> 이 서비스를 사용하여 파일과 하위 디렉터리의 유니코드 이름을 가져올 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **short_name**: 짧은 이름(8.3 형식)에 대한 포인터입니다.
- **destination_unicode_name**: 제공된 짧은 이름과 연결된 유니코드 이름의 대상에 대한 포인터입니다.
- **destination_unicode_length**: 반환된 유니코드 이름 길이에 대한 포인터입니다.
- **unicode_name_buffer_length**: 유니코드 이름 버퍼의 크기입니다. 참고: 추가 바이트를 만드는 NULL 종결자가 필요합니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 유니코드 이름 검색에 성공했습니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 테이블을 읽을 수 없습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 짧은 이름을 찾을 수 없거나 유니코드 대상 크기가 너무 작습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

유니코드 이름에서 짧은 이름을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

이 서비스는 현재 기본 디렉터리 내에서 유니코드 이름과 연결된 짧은 이름(8.3 형식)을 검색합니다. 유니코드 이름 매개 변수에는 경로 정보가 허용되지 않습니다. 성공하면 서비스에서 유니코드 이름과 연결된 짧은 이름을 반환합니다.

> [!IMPORTANT]
> 이 서비스를 사용하여 파일과 하위 디렉터리의 짧은 이름을 가져올 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **source_unicode_name**: 유니코드 이름에 대한 포인터입니다.
- **source_unicode_length**: 유니코드 이름의 길이입니다.
- **destination_short_name**: 짧은 이름(8.3 형식)의 대상에 대한 포인터입니다. 크기는 13바이트 이상이어야 합니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 짧은 이름 검색에 성공했습니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 테이블을 읽을 수 없습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 유니코드 이름을 찾을 수 없습니다.
- **FX_NOT_IMPLEMENTED**(0x22) exFAT 파일 시스템을 위해 서비스가 구현되지 않았습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get

## <a name="fx_unicode_short_name_get_extended"></a>fx_unicode_short_name_get_extended

유니코드 이름에서 짧은 이름을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a>Description

이 서비스는 현재 기본 디렉터리 내에서 유니코드 이름과 연결된 짧은 이름(8.3 형식)을 검색합니다. 유니코드 이름 매개 변수에는 경로 정보가 허용되지 않습니다. 성공하면 서비스에서 유니코드 이름과 연결된 짧은 이름을 반환합니다.

> [!IMPORTANT]
> 이 서비스는 호출자가 대상 버퍼의 크기를 입력 인수로 제공한다는 점을 제외하고 **fx_unicode_short_name_get()** 과 동일합니다. 따라서 서비스가 짧은 이름이 대상 버퍼를 초과하지 않도록 보장할 수 있습니다.

이 서비스를 사용하여 파일과 하위 디렉터리의 짧은 이름을 가져올 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **media_ptr**: 미디어 제어 블록에 대한 포인터입니다.
- **source_unicode_name**: 유니코드 이름에 대한 포인터입니다.
- **source_unicode_length**: 유니코드 이름의 길이입니다.
- **destination_short_name**: 짧은 이름(8.3 형식)의 대상에 대한 포인터입니다. 크기는 13바이트 이상이어야 합니다.
- **short_name_buffer_length**: 대상 버퍼의 크기입니다. 버퍼 크기는 최소한 14바이트 이상이어야 합니다.

### <a name="return-values"></a>반환 값

- **FX_SUCCESS**(0x00) 짧은 이름 검색에 성공했습니다.
- **FX_FAT_READ_ERROR**(0x03) FAT 테이블을 읽을 수 없습니다.
- **FX_FILE_CORRUPT**(0x08) 파일이 손상되었습니다.
- **FX_IO_ERROR**(0x90) 드라이버 I/O 오류입니다.
- **FX_MEDIA_NOT_OPEN**(0x11) 지정된 미디어가 열려 있지 않습니다.
- **FX_NOT_FOUND**(0x04) 유니코드 이름을 찾을 수 없습니다.
- **FX_NOT_IMPLEMENTED**(0x22) exFAT 파일 시스템을 위해 서비스가 구현되지 않았습니다.
- **FX_SECTOR_INVALID**(0x89) 잘못된 섹터입니다.
- **FX_PTR_ERROR**(0x18) 미디어 또는 이름 포인터가 잘못되었습니다.
- **FX_CALLER_ERROR**(0x20) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

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

### <a name="see-also"></a>참고 항목

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get
