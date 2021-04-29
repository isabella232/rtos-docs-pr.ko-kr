---
title: 4장 - Azure RTOS LevelX NAND API
description: 애플리케이션에 사용할 수 있는 Azure RTOS LevelX NAND API.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73bb94768396b4b8461791a164a102d1f8ef159f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811880"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a>4장 - Azure RTOS LevelX NAND API

애플리케이션에 사용할 수 있는 Azure RTOS LevelX NAND API는 다음과 같습니다.

- ***lx_nand_flash_close** _: _NAND* 플래시 인스턴스를 닫습니다.
- ***lx_nand_flash_defragment** _: _NAND* 플래시 인스턴스를 조각 모음합니다.
- ***lx_nand_flash_extended_cache_enable** _: 확장된 _NAND* 캐시 사용/사용하지 않도록 설정합니다.
- ***lx_nand_flash_initialize** _: _NAND* 플래시 지원을 초기화합니다.
- ***lx_nand_flash_open** _: _NAND* 플래시 인스턴스를 엽니다.
- ***lx_nand_flash_page_ecc_check** _: 수정 사항과 함께 _ECC* 오류가 있는지 페이지를 확인합니다.
- ***lx_nand_flash_page_ecc_compute** _: 페이지에 대한 _ECC*를 계산합니다.
- ***lx_nand_flash_partial_defragment** _: _NAND* 플래시 인스턴스를 부분 조각 모음합니다.
- ***lx_nand_flash_sector_read** _: _NAND* 플래시 섹터를 읽습니다.
- ***lx_nand_flash_sector_release** _: _NAND* 플래시 섹터를 릴리스합니다.
- ***lx_nand_flash_sector_write** _: _NAND* 플래시 섹터를 씁니다.

## <a name="lx_nand_flash_close"></a>lx_nand_flash_close

NAND 플래시 인스턴스를 닫습니다.

### <a name="prototype"></a>프로토타입

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Description

이 서비스는 이전에 열었던 NAND 플래시 인스턴스를 닫습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nand_flash**: NAND 플래시 인스턴스 포인터입니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_ERROR**: (0x01) 플래시 인스턴스를 닫는 중 오류가 발생했습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>참고 항목

- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_defragment"></a>lx_nand_flash_defragment

NAND 플래시 인스턴스를 조각 모음합니다.

### <a name="prototype"></a>프로토타입

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Description

이 서비스는 이전에 열었던 NAND 플래시 인스턴스의 조각을 모읍니다. 조각 모음 프로세스는 사용 가능한 페이지와 블록 수를 최대화합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nand_flash**: NAND 플래시 인스턴스 포인터입니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_ERROR**: (0x01) 플래시 인스턴스를 조각 모음하는 동안 오류가 발생했습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>참고 항목

- lx_nand_flash_close
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_extended_cache_enable"></a>lx_nand_flash_extended_cache_enable

확장된 NAND 캐시를 사용/사용하지 않도록 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션에서 제공하는 메모리를 사용하여 RAM에서 캐시 계층을 구현합니다. 전체 캐시 작업에 필요한 총 메모리 양을 다음과 같이 계산할 수 있습니다.

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

제공된 메모리가 전체 NAND 캐시를 수용할 수 있을 정도로 충분히 크지 않은 경우 이 루틴은 제공된 메모리에 따라 가능한 한 많은 NAND 플래시 캐시를 사용하도록 설정합니다.

지정된 메모리 주소가 NULL인 경우에는 NAND 캐시가 사용되지 않도록 설정됩니다. 따라서 일시적으로 NAND 캐시가 사용될 수도 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nand_flash**: NAND 플래시 인스턴스 포인터입니다.  
- **memory**: 캐시 메모리에 대한 시작 주소로, ULONG 액세스에 맞게 정렬됩니다. LX_NULL 값은 캐시를 사용하지 않도록 설정합니다.  
- **size**: 제공된 메모리의 크기입니다(바이트 단위).

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_ERROR**: (0x01) NAND 캐시의 한 가지 요소를 위한 메모리가 부족합니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>참고 항목

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_initialize"></a>lx_nand_flash_initialize

NAND 플래시 지원을 초기화합니다.

### <a name="prototype"></a>프로토타입

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a>Description

이 서비스는 LevelX NAND 플래시 지원을 초기화합니다. 다른 LevelX NAND API보다 먼저 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **없음**

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_ERROR**: (0x01) NAND 플래시 지원을 초기화하는 동안 오류가 발생했습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>참고 항목

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_open"></a>lx_nand_flash_open

NAND 플래시 인스턴스를 엽니다.

### <a name="prototype"></a>프로토타입

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a>Description

이 서비스는 지정된 NAND 플래시 제어 블록과 드라이버 초기화 함수를 사용하여 NAND 플래시 인스턴스를 엽니다. 드라이버 초기화 함수는 이 NAND 플래시 인스턴스와 연결된 NAND 하드웨어의 블록/페이지를 읽고, 쓰고, 지우기 위한 다양한 함수 포인터를 설치합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nand_flash**: NAND 플래시 인스턴스 포인터입니다.
- **name**: NAND 플래시 인스턴스의 이름입니다.
- **nor_driver_initialize**: NAND 플래시 드라이버 초기화 함수에 대한 함수 포인터입니다. NAND 플래시 드라이버 역할에 대한 자세한 내용은 이 가이드의 3장을 참조하세요.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_ERROR**: (0x01) NAND 플래시 인스턴스를 여는 동안 오류가 발생했습니다.
- **LX_NO_MEMORY**: (0x08) 드라이버가 RAM으로 페이지 하나를 읽기 위한 버퍼를 제공하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>참고 항목

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_check"></a>lx_nand_flash_page_ecc_check

수정 사항과 함께 ECC 오류가 있는지 페이지를 확인합니다.

### <a name="prototype"></a>프로토타입

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Description

이 서비스는 제공된 ECC를 사용하여 제공된 NAND 페이지 버퍼의 무결성을 확인합니다. (NAND 플래시 인스턴스 포인터에 정의된) 페이지 크기는 256바이트의 배수로 가정되고 제공된 ECC 코드는 페이지의 각 256바이트 부분에서 1비트 오류를 수정할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nand_flash**: NAND 플래시 인스턴스 포인터입니다.
- **page_buffer**: NAND 플래시 페이지 버퍼에 대한 포인터입니다.
- **ecc_buffer**: NAND 플래시 페이지의 ECC에 대한 포인터입니다. 페이지의 256바이트 부분마다 ECC 3바이트가 있습니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) NAND 페이지에 오류가 없습니다.
- **LX_NAND_ERROR_CORRECTED**: (0x06) NAND 페이지에서 1비트 오류가 한 개 이상 수정되었으며, 수정 사항은 페이지 버퍼에 있습니다.
- **LX_NAND_ERROR_NOT_CORRECTED**: (0x07) NAND 페이지에 오류가 너무 많아 수정할 수 없습니다.

### <a name="allowed-from"></a>허용되는 위치

LevelX 드라이버

### <a name="example"></a>예제

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a>참고 항목

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_compute"></a>lx_nand_flash_page_ecc_compute

페이지의 ECC를 계산합니다.

### <a name="prototype"></a>프로토타입

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Description

이 서비스는 제공된 NAND 페이지 버퍼의 ECC를 계산하고 제공된 ECC 버퍼에서 ECC를 반환합니다. 페이지 크기는 (NAND 플래시 인스턴스 포인터에 정의된) 256바이트의 배수로 가정됩니다. ECC 코드는 나중에 읽을 때 페이지의 무결성을 확인하는 데 사용됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nand_flash**: NAND 플래시 인스턴스 포인터입니다.
- **page_buffer**: NAND 플래시 페이지 버퍼에 대한 포인터입니다.
- **ecc_buffer**: NAND 플래시 페이지의 ECC 대상에 대한 포인터입니다. 페이지의 256바이트 부분마다 ECC 스토리지는 3바이트여야 합니다. 예를 들어 2048바이트 페이지에는 ECC에 24바이트가 필요합니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) ECC가 계산되었습니다.
- **LX_ERROR**: (0x01) ECC를 계산하는 동안 오류가 발생했습니다.

### <a name="allowed-from"></a>허용되는 위치

LevelX 드라이버

### <a name="example"></a>예제

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a>참고 항목

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_partial_defragment"></a>lx_nand_flash_partial_defragment

NAND 플래시 인스턴스를 부분 조각 모음합니다.

### <a name="prototype"></a>프로토타입

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a>Description

이 서비스는 이전에 열었던 NAND 플래시 인스턴스를 지정된 최대 블록 수까지 조각 모음합니다. 조각 모음 프로세스는 사용 가능한 페이지와 블록 수를 최대화합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nand_flash**: NAND 플래시 인스턴스 포인터입니다.
- **max_blocks**: 최대 블록 수입니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_ERROR**: (0x01) 플래시 인스턴스를 조각 모음하는 동안 오류가 발생했습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>참고 항목

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_read"></a>lx_nand_flash_sector_read

NAND 플래시 섹터 읽기

### <a name="prototype"></a>프로토타입

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Description

이 서비스는 NAND 플래시 인스턴스에서 논리 섹터를 읽고, 성공하면 제공된 버퍼의 내용을 반환합니다. NAND 섹터 크기는 항상 기본 NAND 하드웨어의 페이지 크기입니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nand_flash**: NAND 플래시 인스턴스 포인터입니다.
- **logical_sector**: 읽을 논리 섹터입니다.
- **buffer**: 논리 섹터 내용의 대상에 대한 포인터입니다. 버퍼는 NAND 플래시 페이지 크기이고 ULONG 액세스를 위해 정렬된 것으로 간주됩니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_ERROR**: (0x01) NAND 플래시 섹터를 읽는 동안 오류가 발생했습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a>참고 항목

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_release"></a>lx_nand_flash_sector_release

NAND 플래시 섹터를 해제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Description

이 서비스는 NAND 플래시 인스턴스에서 논리 섹터 매핑을 해제합니다. 사용되지 않을 때 논리 섹터를 해제하면 LevelX 사용 평균화를 보다 효율적으로 구현할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nand_flash**: NAND 플래시 인스턴스 포인터입니다.
- **logical_sector**: 해제할 논리 섹터입니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_ERROR**: (0x01) NAND 플래시 섹터를 쓰는 중 오류가 발생했습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>참고 항목

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_write"></a>lx_nand_flash_sector_write

NAND 플래시 섹터를 씁니다.

### <a name="prototype"></a>프로토타입

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Description

이 서비스는 NAND 플래시 인스턴스에 지정된 논리 섹터를 씁니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nand_flash**: NAND 플래시 인스턴스 포인터입니다.
- **logical_sector**: 쓸 논리 섹터입니다.
- **buffer**: 논리 섹터 내용에 대한 포인터입니다. 버퍼는 NAND 플래시 페이지 크기이고 ULONG 액세스를 위해 정렬된 것으로 간주됩니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_NO_SECTORS**: (0x02) 쓰기를 수행하는 데 사용할 수 있는 더 이상의 여유 섹터가 없습니다.
- **LX_ERROR**: (0x01) NAND 플래시 섹터를 해제하는 동안 오류가 발생했습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>참고 항목

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
