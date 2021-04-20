---
title: Azure RTOS LevelX NAND 지원
description: NAND 플래시 메모리는 일반적인 파일 시스템인 대규모 데이터 스토리지용 LevelX에 많이 사용됩니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3286e4ea7f16b28ff55fc95a87a1e0c313ec4240
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811083"
---
# <a name="chapter-3---azure-rtos-levelx-nand-support"></a>3장 - Azure RTOS LevelX NAND 지원

NAND 플래시 메모리는 일반적인 파일 시스템인 대규모 데이터 스토리지에 많이 사용됩니다. NAND 메모리는 *블록* 으로 구성됩니다. 각 NAND 블록 내에는 일련의 *페이지* 가 있습니다. NAND 블록은 지울 수 있습니다. 즉, NAND 블록 내의 모든 페이지가 지워집니다(모두로 설정됨). 각 NAND 블록 페이지에는 기록, 불량 블록 관리 및 오류 검색을 위해 Azure RTOS LevelX에서 사용하는 *예비 바이트* 세트가 있습니다. NAND 블록 페이지는 다양한 크기로 사용할 수 있습니다. 가장 일반적인 페이지 크기는 다음과 같습니다. 

| **페이지 크기** | **예비 바이트** |
| ------------- | --------------- |
| 256           | 8               |
| 512           | 16              |
| 2048          | 64              |

NAND 메모리는 직접 액세스할 수 없다는 점에서 NOR 메모리와 다릅니다. 즉, NOR 메모리와 같은 프로세서에서 직접 NAND 메모리를 읽을 수 없습니다. 제한된 횟수만큼 지운 후에만 NAND 메모리에 기록할 수 있습니다. 이는 쓰기 요청이 설정된 비트를 지우는 경우 무제한으로 기록할 수 있는 NOR 메모리와 다릅니다. 마지막으로 각 페이지와 연결된 예비 바이트는 NAND 플래시에 고유합니다. 일반적인 예비 바이트 구성은 아래 표와 같습니다.

| **예비 바이트** | **바이트 번호** | **Configuration**     |
| ------------------------- | -------------- | --------------------- |
| 8                         | 바이트 0-2:     | ECC 바이트             |
|                           | 바이트 3,4,6,7: | LevelX 섹터 매핑 |
|                           | 바이트 5:        | 불량 블록 플래그        |
| 16                        | 바이트 0-3,6-7: | ECC 바이트             |
|                           | 바이트 8-11:    | LevelX 섹터 매핑 |
|                           | 바이트 12-15:   | 사용 안 함                |
|                           | 바이트 5:        | 불량 블록 플래그        |
| 64                        | 바이트 0:        | 불량 블록 플래그        |
|                           | 바이트 2-5:     | LevelX 섹터 매핑 |
|                           | 바이트 6-39:    | 사용 안 함                |
|                           | 바이트 40-63:   | ECC 바이트             |

LevelX는 실제 NAND 페이지에 매핑된 논리 섹터를 추적하기 위해 각 NAND 페이지의 예비 바이트 중 4개를 활용합니다. 이러한 4개의 바이트는 LevelX 소유 형식으로 32비트 부호 없는 정수를 구현하는 데 사용됩니다. 32비트 필드의 상위 비트(비트 31)는 논리적 섹터와 페이지 간 매핑이 유효함을 나타내는 데 사용됩니다. 이 비트가 0이면 이 페이지의 정보는 더 이상 유효하지 않습니다. 다음 비트(비트 30)는 이 페이지가 더 이상 사용되지 않는 과정에 있으며 새 섹터가 기록되고 있음을 나타내는 데 사용됩니다. 비트 29는 매핑 항목 쓰기가 완료된 시간을 나타내는 데 사용됩니다. 비트 29가 0이면 매핑 항목 쓰기가 완료된 것입니다. 비트 29를 설정하면 매핑 항목을 기록하는 중입니다. 비트 30 및 29는 새 플래시 페이지를 업데이트하는 동안 잠재적인 전력 손실에서 복구하는 데 사용됩니다. 마지막으로 하위 29 비트(28-0)에는 페이지의 논리 섹터 번호가 포함됩니다.

**LevelX 매핑 항목**

| 비트 | 의미 |
| ------ | ------- |
| 31     | 유효한 플래그입니다. 설정 및 논리 섹터가 모두 아닌 경우 매핑이 유효함을 나타냅니다. |
| 30     | 사용되지 않는 플래그입니다. Clear인 경우 이 매핑은 더 이상 사용되지 않거나 더 이상 사용되지 않는 과정에 있습니다. |
| 29     | 이 비트가 0인 경우 매핑 항목 쓰기가 완료되었습니다. |
| 0-28   | 이 물리적 페이지에 매핑된 논리 섹터입니다(모두가 아닌 경우). |

또한 LevelX는 블록이 꽉 찼을 때 매핑된 페이지 목록뿐만 아니라 블록 지우기 수에 각 NAND 블록의 첫 페이지를 사용합니다. LevelX에서 NAND 블록의 첫 페이지 형식이 다음과 같이 표시됩니다.

| LevelX 블록 페이지 0 형식 |
|:--------------------------:|
| [블록 지우기 수]        |
| [1페이지 섹터 매핑]    |
| ...                        |
| ["n"페이지 섹터 매핑]  |
| [0xF0F0F0F0]               |

> [!NOTE]
> 블록이 꽉 찬 경우, 즉 블록의 모든 페이지가 기록된 경우에만 페이지 매핑 정보가 기록됩니다. 이렇게 하면 런타임 중 사용 가능한 페이지 및 논리 섹터 매핑을 더 빠르게 검색할 수 있습니다.

## <a name="nand-bad-block-support"></a>NAND 불량 블록 지원

또한 NAND 메모리는 NOR 메모리보다 블록 블록을 가질 가능성이 더 높습니다. 이는 NAND 제조업체가 불량 블록을 허용하고 소프트웨어가 그러한 불량 블록을 해결하도록 함으로써 수율을 높일 수 있기 때문입니다. LevelX는 단순히 불량 블록을 매핑하여 NAND 불량 블록 관리를 처리합니다.

또한 LevelX는 기본 LevelX 드라이버가 새로운 ECC 코드를 계산하는 데 활용하거나 페이지의 각 256바이트 섹션 내 페이지 읽기에서 1비트 오류 수정을 수행할 수 있도록 256바이트 해밍 ECC(오류 수정 코드) 용 API를 제공합니다.

## <a name="nand-driver-requirements"></a>NAND 드라이버 요구 사항

LevelX를 사용하려면 기본 플래시 부분과 하드웨어 구현과 관련된 기본 NAND 플래시 드라이버가 필요합니다. API ***lx_nand_flash_open*** 을 통해 초기화하는 동안 드라이버가 LevelX로 지정됩니다. LevelX 드라이버의 프로토타입은 다음과 같습니다.

```c
INT nand_driver_initialize(LX_NAND_FLASH *instance);
```

*Instance* 매개 변수는 LevelX NAND 제어 블록을 지정합니다. 드라이버 초기화 함수는 연결된 LevelX 인스턴스에 대해 다른 모든 드라이버 수준 서비스를 설정합니다. 각 LevelX NAND 인스턴스에 필요한 서비스는 아래 목록에 나와 있습니다.

- Read Page
- Write Page
- Block Erase
- Block Erased Verify
- Page Erased Verify
- Block Status Get
- Block Status Set
- Block Extra Bytes Get
- Block Extra Bytes Set
- System Error Handler

## <a name="driver-initialization"></a>드라이버 초기화

드라이버의 초기화 함수 내에서 **LX_NAND_FLASH** 인스턴스의 함수 포인터 설정을 통해 이러한 서비스를 설정합니다. 또한 드라이버 초기화 함수는 총 블록 수, 블록당 페이지 수, 페이지당 바이트 수 및 한 페이지를 메모리로 읽을 수 있을 만큼 큰 RAM 영역을 지정합니다. 드라이버 초기화 함수는 **LX_SUCCESS** 를 반환하기 전에 추가 디바이스 및/또는 구현별 초기화 작업을 수행할 수도 있습니다.

## <a name="driver-read-page"></a>Driver Read Page

LevelX NAND 드라이버 "read page" 서비스는 NAND 플래시의 특정 블록에서 특정 페이지를 읽습니다. 모든 오류 검사 및 수정 논리는 드라이버 서비스의 책임입니다. 성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다. 성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다. LevelX NAND 드라이버 "read page" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nand_driver_read_page(
    ULONG block,
    ULONG page,
    ULONG *destination, 
    ULONG words);
```

여기서 *block* 과 *page* 는 읽을 페이지를 식별하고 *destination* 과 *words* 는 페이지 내용을 배치할 위치와 읽을 32비트 단어 수를 지정합니다.

## <a name="driver-write-page"></a>Driver Write Page

LevelX NAND 드라이버 "write page" 서비스는 특정 페이지를 NAND 플래시의 지정된 블록에 씁니다. 모든 오류 검사 및 ECC 계산은 드라이버 서비스의 책임입니다. 성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다. 성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다. LevelX NAND 드라이버 "write page" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nand_driver_write_page(
    ULONG block, 
    ULONG page,
    ULONG *source, 
    ULONG words);
```

여기서 *block* 과 *page* 는 쑬 페이지를 식별하고 *source* 와 *words* 는 쓰기 원본과 쓸 32비트 단어 수를 지정합니다.

> [!NOTE]
> LevelX는 플래시 페이지에 쓸 때 하위 수준 오류 검색을 위해 드라이버를 사용합니다. 여기에는 일반적으로 페이지를 다시 읽고 쓰기 버퍼와 비교하여 쓰기가 성공했는지 확인하는 작업이 포함됩니다.

## <a name="driver-block-erase"></a>Driver Block Erase

LevelX NAND 드라이버 "block erase" 서비스는 NAND 플래시의 지정된 블록을 지웁니다. 성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다. 성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다. LevelX NAND 드라이버 "block erase" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nand_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

여기서 *block* 은 지울 블록을 식별합니다. *erase_count* 매개 변수는 진단 용도로 제공됩니다. 예를 들어, 드라이버는 지우기 횟수가 특정 임계값을 초과할 때 애플리케이션 소프트웨어의 다른 부분에 경고할 수 있습니다.

> [!NOTE]
> LevelX는 블록을 지울 때 하위 수준 오류 검색을 위해 드라이버를 사용 합니다. 여기에는 일반적으로 블록의 모든 페이지가 모두임을 확인하는 작업이 포함됩니다.

## <a name="driver-block-erased-verify"></a>Driver Block Erased Verify

LevelX NAND 드라이버 "block erased verify" 서비스는 NAND 플래시의 지정된 블록이 삭제되었는지 확인합니다. 블록이 지워지면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다. 블록이 지워지지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다. LevelX NAND 드라이버 "block erased verify" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nand_driver_block_erased_verify(ULONG block);
```

여기서 *block* 은 삭제되었는지 확인하는 블록을 지정합니다.

> [!NOTE]
> LevelX는 드라이버로 모든 페이지와 각 페이지의 모든 바이트(예비 및 데이터 바이트 포함)를 검사하여 지워졌는지 확인합니다(모두 포함).

## <a name="driver-page-erased-verify"></a>Driver Page Erased Verify

LevelX NAND 드라이버 "page erased verify" 서비스는 NAND 플래시의 지정된 블록의 지정된 페이지가 삭제되었는지 확인합니다. 블록이 지워지면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다. 페이지가 지워지지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다. LevelX NAND 드라이버 "page erased verify" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nand_driver_page_erased_verify(
    ULONG block,  
    ULONG page);
```
여기서 *block* 은 어떤 블록과 *페이지* 가 지워졌는지 확인할 페이지를 지정합니다.

> [!NOTE]
> LevelX는 드라이버로 지정된 페이지의 모든 바이트(예비 및 데이터 바이트 포함)를 검사하여 지워졌는지 확인합니다(모두 포함).

## <a name="driver-block-status-get"></a>Driver Block Status Get

LevelX NAND 드라이버 "block status get" 서비스는 NAND 플래시의 지정된 블록의 불량 블록 플래그를 검색합니다. 성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다. 성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다. LevelX NAND 드라이버 "block status get" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nand_driver_block_status_get(
    ULONG block,  
    UCHAR *bad_block_byte);
```

여기서 *block* 은 불량 블록 플래그의 대상을 지정하는 블록과 *bad_block_byte* 를 지정합니다.

## <a name="driver-block-status-set"></a>Driver Block Status Set

LevelX NAND 드라이버 "block status set" 서비스는 NAND 플래시의 지정된 블록의 불량 블록 플래그를 설정합니다. 성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다. 성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다. LevelX NAND 드라이버 "block status set" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nand_driver_block_status_set(
    ULONG block,
    UCHAR bad_block_byte);
```

여기서 *block* 은 불량 블록 플래그의 값을 지정하는 블록과 *bad_block_byte* 를 지정합니다.

## <a name="driver-block-extra-bytes-get"></a>Driver Block Extra Bytes Get

LevelX NAND 드라이버 "block extra bytes get" 서비스는 NAND 플래시의 특정 페이지와 관련된 추가 바이트를 검색합니다. 성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다. 성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다. LevelX NAND 드라이버 "block extra bytes get" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nand_driver_block_extra_bytes_get(
    ULONG block,  
    ULONG page, 
    UCHAR *destination, 
    UINT size);
```

여기서 *block* 은 블록을 지정하고, *page* 는 특정 페이지를 지정하고, *destination* 은 추가 바이트의 대상을 지정합니다. *size* 매개 변수는 가져올 추가 바이트 수를 지정합니다.

## <a name="driver-block-extra-bytes-set"></a>Driver Block Extra Bytes Set

LevelX NAND 드라이버 "block extra bytes set" 서비스는 NAND 플래시의 특정 블록의 특정 페이지에 추가 바이트를 설정합니다. 성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다. 성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다. LevelX NAND 드라이버 "block extra bytes set" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nand_driver_block_extra_bytes_set(
    ULONG block,  
    ULONG page, 
    UCHAR *source, 
    UINT size);
```

여기서 *block* 은 블록을 지정하고, *page* 는 특정 페이지를 지정하고, *source* 는 추가 바이트의 원본을 지정합니다. *size* 매개 변수는 설정할 추가 바이트 수를 지정합니다.

## <a name="driver-system-error"></a>Driver System Error

LevelX NAND 드라이버 "system error handler" 서비스는 LevelX에서 감지한 시스템 오류 처리 설정을 담당합니다. 이 루틴의 처리는 애플리케이션에 따라 다릅니다. 성공하면 LevelX NAND 드라이버가 **LX_SUCCESS** 를 반환합니다. 성공하지 않으면 LevelX NAND 드라이버가 **LX_ERROR** 를 반환합니다. LevelX NAND 드라이버 "system error" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nand_driver_system_error(
    UINT error_code,  
    ULONG block, 
    ULONG page);
```

여기서 *block* 은 블록을 지정하고 *page* 는 *error_code* 가 나타내는 오류가 발생한 특정 페이지를 지정합니다.

## <a name="nand-simulated-driver"></a>NAND Simulated Driver

LevelX는 단순히 RAM을 사용하는 시뮬레이션된 NAND 플래시 드라이버를 제공하여 NAND 플래시 파트의 작동을 시뮬레이션합니다. 기본적으로 NAND 시뮬레이션된 드라이버는 블록당 16페이지와 페이지당 2048바이트가 있는 8개의 NAND 플래시 블록을 제공합니다.

시뮬레이션된 NAND 플래시 드라이버 초기화 함수는 ***lx_nand_flash_simulator_initialize** _이며 _*_lx_nand_flash_simulator.c_**에 정의되어 있습니다. 또한 이 드라이버는 특정 NAND 플래시 드라이버를 쓰는 데 유용한 템플릿을 제공합니다.

## <a name="nand-filex-integration"></a>NAND FileX 통합

앞에서 설명한 것처럼 LevelX는 작업을 위해 FileX를 사용하지 않습니다. 모든 LevelX API는 LevelX에서 제공하는 논리 섹터로 원시 데이터를 저장/검색하기 위해 애플리케이션 소프트웨어가 직접 호출할 수 있습니다. 그러나 LevelX는 FileX도 지원합니다.

***fx_nand_flash_simulated_driver.c*** 파일에는 NAND 플래시 시뮬레이션에 사용할 예제 FileX 드라이버가 포함되어 있습니다. 이 드라이버의 흥미로운 점은 FileX에서 일반적으로 사용하는 512바이트 논리 섹터를 2048바이트 페이지를 사용하는 LevelX 시뮬레이터에 대한 단일 논리 섹터 읽기/쓰기 요청으로 결합한다는 것입니다. 이를 통해 NAND 플래시 메모리를 보다 효율적으로 사용할 수 있습니다. LevelX용 NAND 플래시 FileX 드라이버는 사용자 지정 FileX 드라이버를 쓰는 데 적합한 시작점을 제공합니다.  
  
> [!NOTE]
> FileX NAND 플래시 형식은 NAND 플래시에서 제공하는 것보다 적은 섹터의 전체 블록 크기 중 하나여야 합니다. 이를 통해 마모 수준 처리 중 최상의 성능을 보장할 수 있습니다. LevelX 마모 평준화 알고리즘에서 쓰기 성능을 향상시킬 수 있는 추가 기술은 다음과 같습니다.

1. 모든 쓰기는 정확히 하나 이상의 클러스터 크기이며 정확한 클러스터 경계에서 시작해야 합니다.
1. API의 FileX ***fx_file_allocate*** 클래스를 통해 대량 파일 쓰기 작업을 수행하기 전에 클러스터를 미리 할당합니다.
1. FileX 드라이버가 릴리스 섹터 정보를 수신하도록 설정되어 있는지 확인하고, 릴리스 섹터에 대한 드라이버로 전달된 요청은 ***lx_nor_flash_sector_release*** 를 호출하여 드라이버에서 처리됩니다.
1. 주기적으로 ***lx_nand_flash_defragment*** 를 사용하여 가능한 한 많은 NAND 블록을 확보하고 쓰기 성능을 향상시킬 수 있습니다.
1. ***Lx_nand_flash_extended_cache_enable*** API를 활용하여 더 빠른 성능을 위해 다양한 NAND 블록 리소스의 RAM 캐시를 제공합니다.
