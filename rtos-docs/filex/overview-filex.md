---
title: Azure RTOS FileX 이해
description: Azure RTOS FileX는 Azure RTOS ThreadX와 완전히 통합된 고성능의 FAT(파일 할당 테이블) 호환 파일 시스템으로, 지원되는 모든 프로세서에서 사용할 수 있습니다. Azure RTOS FileX는 Azure RTOS ThreadX와 마찬가지로 공간을 적게 차지하면서 고성능을 제공하도록 설계되었으므로 파일 관리 작업이 필요한 오늘날의 긴밀하게 포함된 애플리케이션에 적합합니다. FileX는 Azure RTOS LevelX를 통해 RAM, Azure RTOS USBX, SD 카드 및 NAND/NOR 플래시 메모리를 비롯한 대부분의 물리적 미디어를 지원합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 399586eca18ef9345b94cc577bdacbf3c3a591bcd22b474b4e3d4ca4eefb4432
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782852"
---
# <a name="overview-of-azure-rtos-filex"></a>Azure RTOS FileX 개요

Azure RTOS FileX 포함 파일 시스템은 Microsoft FAT 파일 형식을 위한 Azure RTOS의 고급 산업 등급 솔루션으로, 포함 수준이 높은 실시간 IoT 애플리케이션 전용으로 설계되었습니다. Azure RTOS FileX는 FAT12, FAT16, FAT32, exFAT 등을 비롯한 모든 Microsoft 파일 형식을 지원합니다. 또한 FileX는 [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/)라는 추가 기능 제품을 통해 선택적인 내결함성 및 FLASH 마모 레벨링을 제공합니다. 이뿐 아니라 Azure RTOS FileX는 적은 메모리 공간, 빠른 실행 및 뛰어난 사용 편의성을 제공하므로 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.

## <a name="api-protocols"></a>API 프로토콜

### <a name="media-services"></a>Media Services

- FAT 12/16/32 및 exFAT 지원
- 최소 6KB FLASH, 2.5KB RAM
- 종합 미디어 액세스 서비스
- 미디어 인스턴스 수 제한 없음
- 단순 읽기/쓰기 논리 섹터 드라이버 인터페이스
- 다중 파티션 지원
- 논리 섹터 캐시
- FAT 항목 캐시
- 선택적 내결함성 지원
- 지연된 보조 FAT 업데이트
- Azure RTOS TraceX를 통한 시스템 수준 추적
- 다음을 포함하는 직관적인 미디어 액세스 API:
  - fx_media_open
  - fx_media_close
  - fx_media_format
  - fx_media_space_available

### <a name="directory-services"></a>디렉터리 서비스

- 최대 256바이트 경로
- 긴 및 8.3 디렉터리 이름 지원
- 디렉터리 만들기 및 삭제
- 디렉터리 탐색 및 트래버스
- 디렉터리 특성 관리
- Azure RTOS TraceX를 통한 시스템 수준 추적
- 다음을 포함하는 직관적인 디렉터리 액세스 API:
  - fx_directory_create
  - fx_directory_delete
  - fx_directory_attributes_set
  - fx_directory_attributes_read
  - fx_directory_first_entry_find
  - fx_directory_next_entry_find

### <a name="file-services"></a>파일 서비스

- 최소 3.3KB FLASH
- 무제한 파일 열기
- 읽기 전용 파일을 여러 번 열 수 있음
- 긴 및 8.3 디렉터리 이름 지원
- 연속 파일 지원
- 빠른 검색 논리
- 클러스터 사전 할당
- 파일 만들기, 삭제 및 이름 바꾸기
- 파일 읽기, 쓰기 및 보기
- 파일 특성 관리
- Azure RTOS TraceX를 통한 시스템 수준 추적
- 다음을 포함하는 직관적인 파일 액세스 API:
  - fx_file_create
  - fx_file_delete
  - fx_file_attributes_set
  - fx_file_attributes_read
  - fx_file_read
  - fx_file_seek
  - fx_file_write

## <a name="advanced-technology"></a>고급 기술

Azure RTOS FileX는 다음을 포괄하는 고급 기술입니다.

- FAT 12/16/32 및 exFAT 지원
- 다중 파티션 지원
- 자동 크기 조정
- Endian 중립
- 긴 파일 이름 및 8.3 지원
- 선택적 내결함성 지원
- 논리 섹터 캐시
- FAT 항목 캐시
- 클러스터 사전 할당
- 연속 파일 지원
- 선택적 성능 메트릭
- Azure RTOS TraceX 시스템 분석 지원

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a>NOR/NAND 마모 레벨링(Azure RTOS LevelX)

Azure RTOS LevelX는 Microsoft의 NOR/NAND FLASH 마모 레벨링 제품입니다. Azure RTOS LevelX는 애플리케이션에 대해 FileX와 결합하여, 또는 독립 실행형 직접 읽기/쓰기 FLASH 섹터 라이브러리로 사용할 수 있습니다.
