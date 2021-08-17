---
title: 5장 - Azure RTOS FileX용 I/O 드라이버
description: 이 장은 Azure RTOS FileX에 대한 I/O 드라이버를 설명하며 개발자들의 애플리케이션별 드라이버 작성을 지원하도록 설계되었습니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 163893119837a46479b3f346c2bd47d200de2af75232f91a23bbc3f64e20ea50
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782917"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a>5장 - Azure RTOS FileX용 I/O 드라이버

이 장은 Azure RTOS FileX에 대한 I/O 드라이버를 설명하며 개발자들의 애플리케이션별 드라이버 작성을 지원하도록 설계되었습니다.

## <a name="io-driver-introduction"></a>I/O 드라이버 소개

FileX는 여러 미디어 디바이스를 지원합니다. FX_MEDIA 구조는 미디어 디바이스 관리에 필요한 모든 항목을 정의합니다. 이 구조에는 미디어 관련 I/O 드라이버와, 드라이버와 FileX 사이에 정보와 상태를 전달하기 위한 관련 매개 변수를 비롯한 모든 미디어 정보가 포함됩니다. 대부분의 시스템에는 각 FileX 미디어 인스턴스에 대해 고유한 I/O 드라이버가 있습니다.

## <a name="io-driver-entry"></a>I/O 드라이버 항목

각 FileX I/O 드라이버에는 ***fx_media_open*** 서비스 호출로 정의된 단일 항목 함수가 있습니다. 드라이버 항목 함수의 형식은 다음과 같습니다.

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

FileX는 I/O 드라이버 항목 함수를 호출하여 초기화 및 부트 섹터 읽기를 비롯한 모든 실제 미디어 액세스를 요청합니다. 드라이버에 대한 요청은 순차적으로 수행됩니다. 즉, FileX는 다른 요청을 보내기 전에 현재 요청이 완료될 때까지 대기합니다.

## <a name="io-driver-requests"></a>I/O 드라이버 요청

각 I/O 드라이버에는 단일 항목 함수가 있으므로 FileX는 미디어 제어 블록을 통해 특정 요청을 수행합니다. 특히 **FX_MEDIA** 의 **fx_media_driver_request** 멤버를 사용하여 정확한 드라이버 요청을 지정합니다. I/o 드라이버는 **FX_MEDIA** 의 **fx_media_driver_status** 멤버를 통해 요청의 성공 또는 실패를 알립니다. 드라이버 요청이 성공하면 드라이버 반환 전에 **FX_SUCCESS** 가 이 필드에 배치됩니다. 그렇지 않고 오류가 검색되면 FX_IO_ERROR가 이 필드에 배치됩니다.

### <a name="driver-initialization"></a>드라이버 초기화

실제 드라이버 초기화 프로세스는 애플리케이션마다 다르지만 일반적으로 데이터 구조 초기화와 가능한 일부 예비 하드웨어 초기화로 구성됩니다. 이 요청은 FileX에서 처음으로 수행되며 fx_media_open 서비스 안에서 이루어집니다.

미디어 쓰기 방지가 검색되면 FX_MEDIA의 드라이버 fx_media_driver_write_protect 멤버를 FX_TRUE로 설정해야 합니다.

I/O 드라이버 초기화 요청에 사용되는 FX_MEDIA 멤버는 다음과 같습니다.

|FX_MEDIA 멤버|의미|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_INIT|

FileX는 섹터를 더 이상 사용하지 않을 때 애플리케이션 드라이버에 알리는 메커니즘을 제공합니다. 이것은 FLASH에 매핑된 모든 사용 중인 논리 섹터를 관리해야 하는 FLASH 메모리 관리자에게 특히 유용합니다.

이러한 여유 섹터 알림이 필요한 경우 애플리케이션 드라이버는 간단히 **FX_MEDIA** 구조의 *fx_media_driver_free_sector_update* 필드를 **FX_TRUE** 로 설정합니다. 설정 후 FileX는 하나 이상의 연속 섹터가 여유 상태가 되었음을 표시하는 **_FX_DRIVER_RELEASE_SECTORS_** I/O 드라이버 호출을 수행합니다.

### <a name="boot-sector-read"></a>부트 섹터 읽기

FileX는 표준 읽기 요청을 사용하는 대신 미디어의 부트 섹터를 읽기 위한 특정 요청을 만듭니다. I/O 드라이버 부트 섹터 읽기 요청에 사용되는 **FX_MEDIA** 멤버는 다음과 같습니다.

|FX_MEDIA 멤버|의미|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_READ|
|fx_media_driver_buffer| 부트 섹터의 대상 주소입니다.|

### <a name="boot-sector-write"></a>부트 섹터 쓰기

FileX는 표준 쓰기 요청을 사용하는 대신 미디어의 부트 섹터에 쓰기 위한 특정 요청을 만듭니다. I/O 드라이버 부트 섹터 쓰기 요청에 사용되는 **FX_MEDIA** 멤버는 다음과 같습니다.

|FX_MEDIA 멤버|의미|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_WRITE|
|fx_media_driver_buffer| 부트 섹터의 원본 주소입니다.|

### <a name="sector-read"></a>섹터 읽기

FileX는 I/O 드라이버에 대한 읽기 요청을 실행하여 하나 이상의 섹터를 메모리로 읽어 옵니다. I/O 드라이버 읽기 요청에 사용되는 **FX_MEDIA** 멤버는 다음과 같습니다.

|FX_MEDIA 멤버|의미|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_READ|
|fx_media_driver_logical_sector|읽을 논리 섹터|
|fx_media_driver_sectors|읽을 섹터 수|
|fx_media_driver_buffer|읽은 섹터에 대한 대상 버퍼|
|fx_media_driver_data_sector_read|파일 데이터 섹터가 요청된 경우 FX_TRUE로 설정합니다. 그렇지 않고 시스템 섹터(FAT 또는 디렉터리 섹터)가 요청된 경우 FX_FALSE입니다.|
|fx_media_driver_sector_type|다음과 같이 요청된 섹터의 명시적 형식을 정의합니다.<br />FX_FAT_SECTOR (2)<br />FX_DIRECTORY_SECTOR (3)<br />FX_DATA_SECTOR (4)|

### <a name="sector-write"></a>섹터 쓰기

FileX는 I/O 드라이버에 대한 쓰기 요청을 실행하여 실제 미디어에 하나 이상의 섹터를 씁니다. I/O 드라이버 쓰기 요청에 사용되는 FX_MEDIA 멤버는 다음과 같습니다.

|FX_MEDIA 멤버| 의미|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_WRITE|
|fx_media_driver_logical_sector|쓸 논리 섹터|
|fx_media_driver_sectors|쓸 섹터 수|
|fx_media_driver_buffer|쓸 섹터의 원본 버퍼|
|fx_media_driver_system_write| 시스템 섹터(FAT 또는 디렉터리 섹터)가 요청된 경우 FX_TRUE로 설정합니다. 그 밖에 파일 데이터 섹터가 요청된 경우 FX_FALSE입니다.|
|fx_media_driver_sector_type|다음과 같이 요청된 섹터의 명시적 형식을 정의합니다.<br> <br>FX_FAT_SECTOR (2) <br> FX_DIRECTORY_SECTOR (3) <br>FX_DATA_SECTOR (4).|

### <a name="driver-flush"></a>드라이버 플러시

FileX는 I/O 드라이버에 대한 플러시 요청을 실행하여 현재 드라이버 섹터 캐시에 있는 모든 섹터를 실제 미디어에 플러시합니다. 물론 드라이버가 섹터를 캐싱하지 않는 경우 이 요청에 드라이버 처리가 필요하지 않습니다. I/O 드라이버 플러시 요청에 사용되는 FX_MEDIA 멤버는 다음과 같습니다.

|FX_MEDIA 멤버| 의미|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_FLUSH|

### <a name="driver-abort"></a>드라이버 중단

FileX는 I/O 드라이버에 대한 중단 요청을 실행하여 실제 미디어에서의 추가적인 모든 I/O 작업을 중단하도록 드라이버에 알립니다. 드라이버는 다시 초기화되기 전까지는 I/O를 더 이상 수행하면 안 됩니다. I/O 드라이버 중단 요청에 사용되는 FX_MEDIA 멤버는 다음과 같습니다.

|FX_MEDIA 멤버| 의미|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_ABORT|

### <a name="release-sectors"></a>릴리스 섹터

초기화하는 동안 드라이버에서 이전에 선택한 경우 FileX는 하나 이상의 연속 섹터가 여유 상태가 될 때마다 드라이버에 알립니다. 드라이버가 실제로 FLASH 관리자인 경우 이 정보를 사용하여 FLASH 관리자에게 해당 섹터가 더 이상 필요하지 않음을 알릴 수 있습니다. I/O 드라이버 릴리스 요청에 사용되는 **FX_MEDIA** 멤버는 다음과 같습니다.

|FX_MEDIA 멤버| 의미|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_RELEASE_SECTORS|
|fx_media_driver_logical_sector|여유 섹터 시작|
|fx_media_driver_sectors|여유 섹터 수|

### <a name="driver-suspension"></a>드라이버 일시 중단

실제 미디어에서의 I/O에는 다소 시간이 걸릴 수 있으므로 호출 스레드를 일시 중단하는 것이 바람직한 경우가 종종 있습니다. 물론 기본 I/O 작업의 완료가 인터럽트 기반인 것으로 가정합니다. 그렇다면 스레드 일시 중단은 ThreadX 세마포를 사용하여 쉽게 구현할 수 있습니다. 입력 또는 출력 작업 시작 후 I/O 드라이버는 자체 내부 I/O 세마포에 대해 일시 중단됩니다(드라이버 초기화 중에 최초값 0으로 만들어짐). 드라이버 I/O 완료 인터럽트 처리 과정에서 동일한 I/O 세마포가 설정되어 일시 중단된 스레드를 깨우게 됩니다.

### <a name="sector-translation"></a>섹터 변환

FileX는 미디어를 선형 논리 섹터로 보기 때문에 I/O 드라이버에 대한 I/O 요청은 논리 섹터를 통해 수행됩니다. 미디어의 논리적 섹터와, 헤드, 트랙, 물리적 섹터 등이 포함될 수 있는 실제 구조 정보 간의 변환은 드라이버가 담당합니다. FLASH 및 RAM 디스크 미디어의 경우 논리 섹터는 일반적으로 디렉터리를 실제 섹터에 매핑합니다. 어떤 경우든 I/O 드라이버에서 논리적 및 실제 섹터의 매핑을 수행하기 위한 일반적인 수식은 다음과 같습니다.

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

실제 섹터는 1부터 시작하지만 논리 섹터는 0부터 시작합니다.

### <a name="hidden-sectors"></a>숨겨진 섹터

미디어의 부트 레코드 앞에 숨겨진 섹터가 있습니다. 이러한 파일은 실제로 FAT 파일 시스템 레이아웃의 범위를 벗어나므로 드라이버에서 수행하는 각 논리 섹터 작업에서 고려되어야 합니다.

### <a name="media-write-protect"></a>미디어 쓰기 방지

FileX 드라이버는 미디어 제어 블록에서 fx_media_driver_write_protect 필드를 설정하여 쓰기 방지를 켤 수 있습니다. 이로 인해 미디어에 대한 쓰기 시도에서 FileX 호출이 수행되면 오류가 반환됩니다.

## <a name="sample-ram-driver"></a>샘플 RAM 드라이버

FileX 데모 시스템은 작은 RAM 디스크 드라이버와 함께 제공되며 fx_ram_driver.c 파일에 정의되어 있습니다. 이 드라이버는 32K 메모리 공간을 가정하고 256 128바이트 섹터에 대한 부트 레코드를 만듭니다. 이 파일은 애플리케이션별 FileX I/O 드라이버를 구현하는 방법에 대한 좋은 예제가 됩니다.

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
