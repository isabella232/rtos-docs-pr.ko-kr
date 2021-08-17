---
title: 6장 - Azure RTOS LevelX NOR API
description: 애플리케이션에 사용할 수 있는 Azure RTOS LevelX NOR API
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e109f5916a9e903aa3341f2855ade085e9d9a22b80ec7cb2e0c310e43ff3eac
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790244"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a>6장 - Azure RTOS LevelX NOR API

애플리케이션에 사용할 수 있는 Azure RTOS LevelX NOR API 함수는 다음과 같습니다.

- ***lx_nor_flash_close** _: _NOR 플래시 인스턴스 닫기*
- ***lx_nor_flash_defragment** _: _NOR 플래시 인스턴스 조각 모음*
- ***lx_nor_flash_extended_cache_enable** _: _확장된 NOR 캐시 사용/사용 안 함*
- ***lx_nor_flash_initialize** _: _NOR 플래시 지원 초기화*
- ***lx_nor_flash_open** _: _NOR 플래시 인스턴스 열기*
- ***lx_nor_flash_partial_defragment** _: _NOR 플래시 인스턴스의 부분 조각 모음*
- ***lx_nor_flash_sector_read** _: _NOR 플래시 섹터 읽기*
- ***lx_nor_flash_sector_release** _: _NOR 플래시 섹터 해제*
- ***lx_nor_flash_sector_write** _: _NOR 플래시 섹터 쓰기*

## <a name="lx_nor_flash_close"></a>lx_nor_flash_close

NOR 플래시 인스턴스 닫기

### <a name="prototype"></a>프로토타입

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Description

이 서비스는 이전에 열었던 NOR 플래시 인스턴스를 닫습니다.

### <a name="input-parameters"></a>입력 매개 변수

- *nor_flash*: NOR 플래시 인스턴스 포인터입니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_ERROR**: (0x01) 플래시 인스턴스를 닫는 중 오류가 발생했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>참고 항목

- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_defragment"></a>lx_nor_flash_defragment

NOR 플래시 인스턴스 조각 모음

### <a name="prototype"></a>프로토타입

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Description

이 서비스는 이전에 열었던 NOR 플래시 인스턴스의 조각을 모읍니다. 조각 모음 프로세스는 사용 가능한 섹터 및 블록의 수를 최대화합니다.

### <a name="input-parameters"></a>입력 매개 변수

- *nor_flash*: NOR 플래시 인스턴스 포인터입니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_ERROR**: (0x01) 플래시 인스턴스를 조각 모음하는 동안 오류가 발생했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>참고 항목

- lx_nor_flash_close
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_extended_cache_enable"></a>lx_nor_flash_extended_cache_enable

확장된 NOR 캐시 사용/사용 안 함

### <a name="prototype"></a>프로토타입

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션에서 제공하는 메모리를 사용하여 RAM에서 NOR 섹터 캐시 계층을 구현합니다. 제공된 각 512바이트의 메모리는 캐시될 수 있는 하나의 NOR 섹터로 변환됩니다. 캐시된 섹터는 블록 제어 정보(예: 지우기 수, 사용 가능한 섹터 맵 및 섹터 매핑 정보)를 포함하는 섹터입니다. 데이터 섹터는 이 캐시에 저장되지 않습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nor_flash**: NOR 플래시 인스턴스 포인터입니다.  
- **memory**: 캐시 메모리에 대한 시작 주소로, ULONG 액세스에 맞게 정렬됩니다. LX_NULL 값은 캐시를 사용하지 않도록 설정합니다.  
- **size** 제공된 메모리의 크기(바이트)입니다(512바이트의 배수여야 함).

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 성공적인 요청
- **LX_ERROR**: (0x01) 단일 NOR 섹션에 대한 메모리가 부족합니다.
- **LX_DISABLED**: (0x09) 구성 옵션으로 NOR 확장 캐시가 사용하지 않도록 설정됩니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>참고 항목

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_initialize"></a>lx_nor_flash_initialize

NOR 플래시 지원 초기화

### <a name="prototype"></a>프로토타입

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a>Description

이 서비스는 LevelX NOR 플래시 지원을 초기화합니다. 다른 LevelX NOR API보다 먼저 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **없음**

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 성공적인 요청
- **LX_ERROR**: (0x01) NOR 플래시 지원을 초기화하는 동안 오류 발생

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>참고 항목

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_partial_defragment
- lx_nor_flash_open
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_open"></a>lx_nor_flash_open

NOR 플래시 인스턴스 열기

### <a name="prototype"></a>프로토타입

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a>Description

이 서비스는 지정된 NOR 플래시 제어 블록과 드라이버 초기화 함수를 사용하여 NOR 플래시 인스턴스를 엽니다. 드라이버 초기화 함수는 이 NOR 플래시 인스턴스와 연결된 NOR 하드웨어의 블록을 읽고, 쓰고, 지우기 위한 다양한 함수 포인터를 설치합니다.

### <a name="input-parameters"></a>입력 매개 변수

- *nor_flash*: NOR 플래시 인스턴스 포인터입니다.
- *name*: NOR 플래시 인스턴스의 이름입니다.
- *nor_driver_initialize*: NOR 플래시 드라이버 초기화 함수에 대한 함수 포인터입니다. NOR 플래시 드라이버 역할에 대한 자세한 내용은 이 가이드의 5장을 참조하세요.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 성공적인 요청
- **LX_ERROR**: (0x01) NOR 플래시 인스턴스를 여는 동안 오류 발생
- **LX_NO_MEMORY**: (0X08) 드라이버가 RAM으로 none 섹터를 읽기 위한 버퍼를 제공하지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>참고 항목

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_partial_defragment"></a>lx_nor_flash_partial_defragment

NOR 플래시 인스턴스의 부분 조각 모음

### <a name="prototype"></a>프로토타입

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a>Description

이 서비스는 이전에 열었던 NOR 플래시 인스턴스를 지정된 최대 블록 수까지 조각 모음합니다. 조각 모음 프로세스는 사용 가능한 섹터 및 블록의 수를 최대화합니다.

### <a name="input-parameters"></a>입력 매개 변수

- *nor_flash*: NOR 플래시 인스턴스 포인터입니다.
- *max_blocks*: 최대 블록 수입니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_ERROR**: (0x01) 플래시 인스턴스를 조각 모음하는 동안 오류가 발생했습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>참고 항목

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_read"></a>lx_nor_flash_sector_read

NOR 플래시 섹터 읽기

### <a name="prototype"></a>프로토타입

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Description

이 서비스는 NOR 플래시 인스턴스에서 논리 섹터를 읽고, 성공하면 제공된 버퍼의 내용을 반환합니다. NOR 섹터 크기는 항상 512바이트입니다.

### <a name="input-parameters"></a>입력 매개 변수

- *nor_flash* NOR 플래시 인스턴스 포인터입니다.
- *logical_sector*: 읽을 논리 섹터입니다.
- *buffer*: 논리 섹터 내용의 대상에 대한 포인터입니다. 버퍼는 512바이트로 간주되고 ULONG 액세스에 맞게 정렬됩니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 성공적인 요청
- **LX_ERROR**: (0x01) NOR 플래시 섹터를 읽는 동안 오류 발생

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a>참고 항목

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_release"></a>lx_nor_flash_sector_release

NOR 플래시 섹터 해제

### <a name="prototype"></a>프로토타입

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Description

이 서비스는 NOR 플래시 인스턴스에서 논리 섹터 매핑을 해제합니다. 사용되지 않을 때 논리 섹터를 해제하면 LevelX 사용 평균화를 보다 효율적으로 구현할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- *nor_flash*: NOR 플래시 인스턴스 포인터입니다.
- *logical_sector*: 해제할 논리 섹터입니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 성공적인 요청
- **LX_ERROR**: (0x01) NOR 플래시 섹터 쓰기 오류

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>참고 항목

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_write"></a>lx_nor_flash_sector_write

NOR 플래시 섹터 쓰기

### <a name="prototype"></a>프로토타입

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Description

이 서비스는 NOR 플래시 인스턴스에 지정된 논리 섹터를 씁니다.

### <a name="input-parameters"></a>입력 매개 변수

- *nor_flash*: NOR 플래시 인스턴스 포인터입니다.
- *logical_sector*: 쓸 논리 섹터입니다.
- *buffer*: 논리 섹터 내용에 대한 포인터입니다. 버퍼는 ULONG 액세스에 맞게 정렬된 512바이트로 간주됩니다.

### <a name="return-values"></a>반환 값

- **LX_SUCCESS**: (0x00) 요청에 성공했습니다.
- **LX_NO_SECTORS**: (0x02) 쓰기를 수행하는 데 사용할 수 있는 더 이상의 여유 섹터가 없습니다.
- **LX_ERROR**: (0x01) NOR 플래시 섹터를 해제하는 동안 오류 발생

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="example"></a>예제

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>참고 항목

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
