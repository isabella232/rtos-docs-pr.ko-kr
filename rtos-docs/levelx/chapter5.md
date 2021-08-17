---
title: 5장 - Azure RTOS LevelX NOR 지원
description: NOR 플래시 메모리는 일반적으로 512바이트로 균등하게 나눌 수 있는 블록으로 구성됩니다. Azure RTOS LevelX는 각 NOR 플래시 블록을 512 바이트 논리 섹터로 나눕니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5d06fa66f0cae29eeb2a89560704b2ef510597e44a565499bf672a75555f208
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790567"
---
# <a name="chapter-5---azure-rtos-levelx-nor-support"></a>5장 - Azure RTOS LevelX NOR 지원

NOR 플래시 메모리는 일반적으로 512바이트로 균등하게 나눌 수 있는 *블록* 으로 구성됩니다. NOR 플래시 메모리에 플래시 *페이지* 의 개념이 없습니다. 또한 NOR 플래시 메모리에 *예비* 바이트가 없습니다. 따라서 Azure RTOS LevelX는 모든 관리 정보에 대해 또는 NOR 플래시 메모리 자체를 사용해야 합니다. 직접 읽기 권한은 NOR 플래시 메모리에서 가능합니다. 쓰기 권한에는 일반적으로 특별한 작업 시퀀스가 필요합니다. NOR 플래시 메모리를 여러 번 기록하여 비트를 지울 수 있습니다. NOR 플래시 메모리의 비트는 블록 지우기 작업을 통해 한 번만 설정할 수 있습니다.

LevelX는 각 NOR 플래시 블록을 512바이트 논리 *섹터* 로 나눕니다. 또한 LevelX는 각 NOR 플래시 블록의 첫 번째 "n" 섹터를 사용하여 관리 정보를 저장합니다. LevelX NOR 플래시 메모리 관리 정보의 형식은 다음과 같습니다.

**LevelX NOR 블록 형식**

| 바이트 오프셋  | 콘텐츠                     |
| ------------ | ---------------------------- |
| 0            | [블록 지우기 수]          |
| 4            | [최소 매핑된 섹터]      |
| 8            | [최대 매핑된 섹터]      |
| 12           | [무료 섹터 비트 맵]        |
| 분            | [섹터 0 매핑 항목]     |
|              | …                            |
| m+4*(n-1)    | [섹터 "n" 매핑 항목]   |
|              | …                            |
| 초            | [섹터 0 콘텐츠]          |
|              | …                            |
| s+512*(n-1) | [섹터 "n" 콘텐츠]         |

32비트 *블록 지우기 횟수* 에는 블록이 지워진 횟수가 포함됩니다. LevelX의 주요 목표는 모든 블록의 지우기 수를 상대적으로 가깝게 유지하여 한 블록이 중간에 발생하는 것을 방지하는 것입니다. 32비트 *최소 매핑된 섹터* 및 *최대 매핑된 섹터* 필드는 블록의 모든 논리 섹터가 매핑되고 기록된 경우에만 기록됩니다. 이러한 필드는 섹터 읽기 작업을 최적화하는 데 유용합니다. *사용 가능한 섹터 비트 맵* 항목은 각 설정 비트가 블록의 매핑되지 않은 섹터에 해당하는 비트 맵입니다. 이 필드는 사용 가능한 섹터 검색을 더 효율적으로 만드는 데 사용됩니다. 블록의 32섹터마다 한 단어가 필요한 가변 길이 필드입니다. *섹터 매핑 항목* 배열에는 블록의 각 섹터에 대한 매핑 정보가 포함됩니다. 각 항목에는 다음과 같은 데이터가 있습니다.

**섹터 매핑 항목**

| 비트 | 의미  |
| ------ | -------- |
| 31     | 유효한 플래그입니다. 설정 및 논리 섹터가 모두 아닌 경우 매핑이 유효함을 나타냅니다. |
| 30     | 사용되지 않는 플래그입니다. Clear인 경우 이 매핑은 더 이상 사용되지 않거나 더 이상 사용되지 않는 과정에 있습니다. |
| 29     | 이 비트가 0인 경우 매핑 항목 쓰기가 완료되었습니다. |
| 0-28   | 이 물리적 섹터에 매핑된 논리 섹터입니다. 모든 것이 아닌 경우입니다. |

32비트 필드의 상한 비트(비트 31)는 논리 섹터 매핑이 유효함을 나타내는 데 사용됩니다. 이 비트가 0이면 이 항목의 정보(및 해당 섹터 콘텐츠)가 더 이상 유효하지 않습니다. 다음 비트, 비트 30은 이 섹터가 사용되지 않는 것으로 표시되고 새 섹터가 작성되고 있음을 나타내는 데 사용됩니다. 비트 29는 매핑 항목 쓰기가 완료된 시간을 나타내는 데 사용됩니다. 비트 29가 0이면 매핑 항목 쓰기가 완료된 것입니다. 비트 29를 설정하면 매핑 항목을 기록하는 중입니다. Bits 30 및 29는 새 섹터 매핑을 업데이트하는 동안 잠재적인 전원 손실에서 복구하는 데 사용됩니다. 마지막으로 하위 29 비트(28-0)에는 섹터의 논리 섹터 번호가 포함됩니다. 섹터가 매핑되지 않은 경우 모든 비트가 설정됩니다. 즉, 값은 0xFFFFFFFF입니다.

## <a name="nor-driver-requirements"></a>NOR 드라이버 요구 사항

LevelX를 사용하려면 기본 플래시 부분과 하드웨어 구현과 관련된 기본 NOR 플래시 드라이버가 필요합니다. API ***lx_nor_flash_open*** 을 통해 초기화하는 동안 드라이버가 LevelX로 지정됩니다. LevelX 드라이버의 프로토타입은 다음과 같습니다.

```c
INT nor_driver_initialize(LX_NOR_FLASH *instance);
```

"*Instance*" 매개 변수는 LevelX NOR 제어 블록을 지정합니다. 드라이버 초기화 함수는 연결된 LevelX 인스턴스에 대해 다른 모든 드라이버 수준 서비스를 설정합니다. 각 LevelX NOR 인스턴스에 필요한 서비스는 다음과 같습니다.

- 섹터 읽기
- 섹터 쓰기
- Block Erase
- Block Erased Verify
- 시스템 오류 처리기

## <a name="driver-initialization"></a>드라이버 초기화

이러한 서비스는 드라이버의 초기화 함수 내 **LX_NOR_FLASH** 인스턴스에서 함수 포인터 설정을 통해 설정합니다. 드라이버 초기화 함수도 다음과 같은 역할을 합니다.

1. 플래시의 기본 주소를 지정합니다.
1. 블록의 총 수와 블록 당 단어 수를 지정합니다.
1. 하나의 플래시 섹터(512 바이트)를 읽고 ULONG 액세스를 위해 정렬된 RAM 버퍼입니다.

드라이버 초기화 함수는 **LX_SUCCESS** 를 반환 하기 전에 추가 디바이스 및/또는 구현별 초기화 의무를 수행할 수도 있습니다.

## <a name="driver-read-sector"></a>드라이버 Read Sector

LevelX NOR 드라이버 "read sector" 서비스는 NOR 플래시의 특정 블록에서 특정 섹터를 읽을 책임이 있습니다. 모든 오류 검사 및 수정 논리는 드라이버 서비스의 책임입니다. 성공하면 LevelX NOR 드라이버는 **LX_SUCCESS** 를 반환합니다. 성공하지 않으면 LevelX NOR 드라이버는 *LX_ERROR* 를 반환합니다. LevelX NOR 드라이버 "read sector" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nor_driver_read_sector(
    ULONG *flash_address,
    ULONG *destination, 
    ULONG words);
```

여기서 "*flash_address*"는 메모리의 NOR 플래시 블록 내에서 논리 섹터의 주소를 지정하고 "*destination*" 및 "*words*"는 섹터 콘텐츠를 저장할 위치와 읽을 32비트 단어의 수를 지정합니다.

## <a name="driver-write-sector"></a>드라이버 Write Sector

LevelX NOR 드라이버 "write sector" 서비스는 특정 섹터를 NOR 플래시의 블록에 기록하는 일을 담당합니다. 모든 오류 검사는 드라이버 서비스의 책임입니다. 성공하면 LevelX NOR 드라이버는 **LX_SUCCESS** 를 반환합니다. 성공하지 않으면 LevelX NOR 드라이버는 **LX_ERROR** 를 반환합니다. LevelX NOR 드라이버 "write sector" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nor_driver_write_sector(
    ULONG *flash_address,
    ULONG *source, 
    ULONG words);
```

여기서 "*flash_address*"는 메모리의 NOR 플래시 블록 내에서 논리 섹터의 주소를 지정하고 "*source*" 및 "*words*"는 쓰기 소스와 기록할 32비트 단어 수를 지정합니다.

> [!NOTE]
> LevelX는 드라이버를 사용하여 쓰기 섹터가 성공적인지 확인합니다. 일반적으로 이 작업은 기록될 요청 값과 일치하는지 확인하기 위해 프로그래밍된 값을 다시 읽는 방법으로 수행됩니다.

## <a name="driver-block-erase"></a>Driver Block Erase

LevelX NOR 드라이버 "block erase" 서비스는 NOR 플래시의 지정된 블록을 지우는 일을 담당합니다. 성공하면 LevelX NOR 드라이버는 **LX_SUCCESS** 를 반환합니다. 성공하지 않으면 LevelX NOR 드라이버는 **LX_ERROR** 를 반환합니다. LevelX NOR 드라이버 "block erase" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nor_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

여기서 "*block*"은 지울 NOR 블록을 식별합니다. "*Erase_count*" 매개 변수는 진단 용도로 제공됩니다. 예를 들어, 드라이버는 지우기 횟수가 특정 임계값을 초과할 때 애플리케이션 소프트웨어의 다른 부분에 경고할 수 있습니다.

> [!NOTE]
> LevelX는 드라이버를 사용하여 블록의 모든 바이트를 검사하고 삭제되었는지 확인합니다(모두 포함).

## <a name="driver-block-erased-verify"></a>Driver Block Erased Verify

LevelX NOR 드라이버 "block erased verify" 서비스는 NOR 플래시의 지정된 블록이 삭제되었는지 확인하는 일을 담당합니다. 블록이 지워지면 LevelX NOR 드라이버는 **LX_SUCCESS** 를 반환합니다. 블록이 지워지지 않으면 LevelX NOR 드라이버는 **LX_ERROR** 를 반환합니다. LevelX NOR 드라이버 "block erased verify" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nor_driver_block_erased_verify(ULONG block);
```

여기서 "*block*"은 삭제되었는지 확인하는 블록을 지정합니다.

> [!NOTE]
> LevelX는 드라이버를 사용하여 지정된 블록의 모든 바이트를 검사하고 삭제되었는지 확인합니다(모두 포함).

## <a name="driver-system-error"></a>Driver System Error

LevelX NOR 드라이버 "system error handler" 서비스는 LevelX에서 감지한 시스템 오류 처리 설정을 담당합니다. 이 루틴의 처리는 애플리케이션에 따라 다릅니다. 성공하면 LevelX NOR 드라이버는 **LX_SUCCESS** 를 반환합니다. 성공하지 않으면 LevelX NOR 드라이버는 **LX_ERROR** 를 반환합니다. LevelX NOR 드라이버 "system error" 서비스의 프로토타입은 다음과 같습니다.

```c
INT nor_driver_system_error(UINT error_code);
```

여기서 "*error_code*"는 발생한 오류를 나타냅니다.

## <a name="nor-simulated-driver"></a>NOR 시뮬레이션된 드라이버

LevelX는 단순히 RAM을 사용하는 시뮬레이션된 NOR 플래시 드라이버를 제공하여 NOR 플래시 파트의 작동을 시뮬레이션합니다. 기본적으로 NOR 시뮬레이션된 드라이버는 블록 당 512바이트 섹터 16개와 NOR 플래시 블록 8개를 제공합니다.

시뮬레이션된 NOR 플래시 드라이버 초기화 함수는 ***lx_nor_flash_simulator_initialize** 이며 *_lx_nor_flash_simulator_**에 정의되어 있습니다. 또한 이 드라이버는 특정 NOR 드라이버를 쓰는 데 유용한 템플릿을 제공합니다.

## <a name="nor-filex-integration"></a>NOR FileX 통합

앞에서 설명한 것처럼 LevelX는 작업을 위해 FileX를 사용하지 않습니다. 모든 LevelX API는 LevelX에서 제공하는 논리 섹터로 원시 데이터를 저장/검색하기 위해 애플리케이션 소프트웨어가 직접 호출할 수 있습니다. 그러나 LevelX는 FileX도 지원합니다.

***Fx_nor_flash_simulated_driver*** 파일에는 NOR 플래시 시뮬레이션에 사용할 예제 FileX 드라이버가 포함되어 있습니다. LevelX용 NOR 플래시 FileX 드라이버는 사용자 지정 FileX 드라이버를 쓰는 데 적합한 시작점을 제공합니다.

> [!NOTE]
> FileX NOR 플래시 형식은 NOR 플래시에서 제공하는 것보다 적은 섹터의 전체 블록 크기 중 하나여야 합니다. 이를 통해 마모 수준 처리 중 최상의 성능을 보장할 수 있습니다. LevelX 마모 평준화 알고리즘에서 쓰기 성능을 향상시킬 수 있는 추가 기술은 다음과 같습니다.
> 1. 모든 쓰기는 정확히 하나 이상의 클러스터 크기이며 정확한 클러스터 경계에서 시작해야 합니다.
> 2. API의 FileX ***fx_file_allocate*** 클래스를 통해 대량 파일 쓰기 작업을 수행하기 전에 클러스터를 미리 할당합니다.
> 3.  주기적으로 ***lx_nor_flash_defragment*** 를 사용하여 가능한 한 많은 NOR 블록을 확보하고 쓰기 성능을 향상시킬 수 있습니다.
> 4. FileX 드라이버가 릴리스 섹터 정보를 수신하도록 설정되어 있는지 확인하고, 릴리스 섹터에 대한 드라이버로 전달된 요청은 ***lx_nor_flash_sector_release*** 를 호출하여 드라이버에서 처리됩니다.
