---
title: 2장 - Azure RTOS LevelX 설치 및 사용
description: LevelX의 설치 및 사용은 간단하며 이 장의 다음 섹션에서 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 34110e74e8ad0a6acd376c00c1284a3ea715c5f5
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223318"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a>2장 - Azure RTOS LevelX 설치 및 사용

Azure RTOS LevelX의 설치 및 사용은 간단하며 이 장의 다음 섹션에서 설명합니다.

## <a name="distribution"></a>배포

LevelX는 ANSI C로 배포되며 여기서는 각 함수가 별도의 C 파일에 포함되어 있습니다. LevelX 배포의 파일은 다음과 같습니다.
- lx_api.h
- lx_nand_flash_256byte_ecc_check.c
- lx_nand_flash_256byte_ecc_compute.c
- lx_nand_flash_block_full_update.c
- lx_nand_flash_block_reclaim.c
- lx_nand_flash_close.c
- lx_nand_flash_defragment.c  
- lx_nand_flash_extended_cache_enable.c
- lx_nand_flash_initialize.c
- lx_nand_flash_logical_sector_find.c
- lx_nand_flash_next_block_to_erase_find.c
- lx_nand_flash_open.c
- lx_nand_flash_page_ecc_check.c
- lx_nand_flash_page_ecc_compute.c  
- lx_nand_flash_partial_defragment.c
- lx_nand_flash_physical_page_allocate.c
- lx_nand_flash_sector_mapping_cache_invalidate.c
- lx_nand_flash_sector_read.c
- lx_nand_flash_sector_release.c
- lx_nand_flash_sector_write.c
- lx_nand_flash_system_error.c
- lx_nor_flash_block_reclaim.c
- lx_nor_flash_close.c
- lx_nor_flash_defragment.c  
- lx_nor_flash_extended_cache_enable.c
- lx_nor_flash_initialize.c
- lx_nor_flash_logical_sector_find.c
- lx_nor_flash_next_block_to_erase_find.c
- lx_nor_flash_open.c
- lx_nor_flash_partial_defragment.c
- lx_nor_flash_physical_sector_allocate.c
- lx_nor_flash_sector_mapping_cache_invalidate.c
- lx_nor_flash_sector_read.c
- lx_nor_flash_sector_release.c
- lx_nor_flash_sector_write.c
- lx_nor_flash_system_error.c

다음과 같이 LevelX NAND 및 NOR 인스턴스 모두에 대한 시뮬레이터와 FileX 드라이버 샘플도 제공됩니다.

- demo_filex_nand_flash.c  
- fx_nand_flash_simulated_driver.c
- lx_nand_flash_simulator.c
- demo_filex_nor_flash.c  
- fx_nor_flash_simulated_driver.c
- lx_nor_flash_simulator.c

물론, NAND 플래시만 필요한 경우 LevelX NAND 플래시 파일(***lx_nand_\*.c***)만 필요합니다. 마찬가지로, NOR 플래시만 필요한 경우에는 NOR 플래시 파일(* *_lx_nor_\_.c***)만 필요합니다.

## <a name="configuration-options"></a>구성 옵션

LevelX는 아래에 설명된 조건 정의를 통해 컴파일 시간에 구성할 수 있습니다. 이 옵션을 사용하려면 각 LevelX 원본의 컴파일에 원하는 정의를 추가하기만 하면 됩니다.

- **LX_DIRECT_READ**: 정의되면 이 옵션은 NOR 메모리를 직접 읽기 위해 NOR 플래시 드라이버 읽기 루틴을 무시하므로 결과적으로 성능이 크게 향상됩니다.
- **LX_FREE_SECTOR_DATA_VERIFY**: 정의되면 LevelX NOR 인스턴스 열기 논리로 인해 사용 가능한 NOR 섹터가 모두 1인지 확인됩니다.
- **LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: 기본적으로 이 값은 16이며 논리 섹터 매핑 캐시 크기를 정의합니다. 값이 크면 성능이 향상되지만 메모리가 부족해집니다. 최소 크기는 8이며 모든 값은 2의 거듭제곱이어야 합니다.
- **LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: 정의되면 캐시 누락이 없도록 직접 매핑 캐시가 생성됩니다. 또한 LX_NAND_SECTOR_MAPPING_CACHE_SIZE는 플래시 디바이스의 정확한 총 페이지 수를 나타내야 합니다.
- **LX_NOR_DISABLE_EXTENDED_CACHE**: 정의되면 확장된 NOR 캐시가 사용하지 않도록 설정됩니다.
- **LX_NOR_EXTENDED_CACHE_SIZE**: 기본적으로 이 값은 NOR 인스턴스에서 캐시할 수 있는 최대 8개 섹터를 나타내는 8입니다.
- **LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: 기본적으로 이 값은 16이며 논리 섹터 매핑 캐시 크기를 정의합니다. 값이 크면 성능이 향상되지만 메모리가 부족해집니다. 최소 크기는 8이며 모든 값은 2의 거듭제곱이어야 합니다.
- **LX_THREAD_SAFE_ENABLE**: 정의되면 API 전체에서 ThreadX 뮤텍스 개체를 사용하여 LevelX를 스레드로부터 안전하게 보호합니다.
- **LX_STANDALONE_ENABLE**: 정의되면 LevelX를 독립 실행형 모드(Azure RTOS 사용 안 함)로 사용할 수 있습니다. 기본적으로 이 기호는 정의되어 있지 않습니다.

> [!IMPORTANT]
> LevelX를 독립 실행형 모드(**LX_STANDALONE_ENABLE** 을 정의해야 함)로 사용하는 경우 ThreadX 파일/라이브러리가 필요하지 않습니다. 이 모드에서는 LevelX의 스레드로부터 안전한 기능을 사용할 수 없습니다.

## <a name="using-levelx"></a>LevelX 사용

LevelX를 단독으로 사용하거나 FileX와 함께 사용하려면 LevelX API를 참조하는 코드에 ***lx_api.h** _ 파일을 포함합니다. 또한 링크 타임에 LevelX 개체 코드를 사용할 수 있는지 확인합니다. LevelX를 사용하는 방법에 대한 예제를 보려면 _*_demo_filex_nand_flash.c_*_ 및 _ *_demo_filex_nor_flash.c_** 파일을 검토하세요.
