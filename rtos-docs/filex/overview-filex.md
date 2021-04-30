---
title: Azure RTOS FileX 이해
description: Azure RTOS FileX는 Azure RTOS ThreadX와 완전히 통합된 고성능의 FAT(파일 할당 테이블) 호환 파일 시스템으로, 지원되는 모든 프로세서에서 사용할 수 있습니다. Azure RTOS FileX는 Azure RTOS ThreadX와 마찬가지로 공간을 적게 차지하면서 고성능을 제공하도록 설계되었으므로 파일 관리 작업이 필요한 오늘날의 긴밀하게 포함된 애플리케이션에 적합합니다. FileX는 Azure RTOS LevelX를 통해 RAM, Azure RTOS USBX, SD 카드 및 NAND/NOR 플래시 메모리를 비롯한 대부분의 물리적 미디어를 지원합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a3a20c8ced3426399ceedf6994c872ce7aec93c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812138"
---
# <a name="overview-of-azure-rtos-filex"></a>Azure RTOS FileX 개요

Azure RTOS FileX 포함 파일 시스템은 Microsoft FAT 파일 형식을 위한 Azure RTOS의 고급 산업 등급 솔루션으로, 포함 수준이 높은 실시간 IoT 애플리케이션 전용으로 설계되었습니다. Azure RTOS FileX는 FAT12, FAT16, FAT32, exFAT 등을 비롯한 모든 Microsoft 파일 형식을 지원합니다. 또한 FileX는 [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/)라는 추가 기능 제품을 통해 선택적인 내결함성 및 FLASH 마모 레벨링을 제공합니다. 이뿐 아니라 Azure RTOS FileX는 적은 메모리 공간, 빠른 실행 및 뛰어난 사용 편의성을 제공하므로 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.

## <a name="api-protocols"></a>API 프로토콜

### <a name="azure-rtos-filex-api"></a>Azure RTOS FileX API

- 직관적이고 일관성 있는 API
- 명사 동사 명명 규칙
- 모든 API는 FileX로 쉽게 식별할 수 있도록 앞에 *fx_* 가 옴
- 차단 API에 선택적 스레드 시간 제한 적용
- 미디어 및 파일 작업에 대한 선택적 사용자 알림 콜백
- 자세한 내용은 [Azure RTOS FileX 사용자 가이드](about-this-guide.md)를 참조하세요.

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

## <a name="small-footprint"></a>적은 메모리 공간

Azure RTOS FileX 포함된 파일 시스템은 8.6 ~ 12KB라는 획기적으로 적은 수준의 메모리 공간으로 기본 파일 읽기/쓰기를 지원합니다. 최소 Azure RTOS FileX RAM 사용량은 단일 미디어 인스턴스에 대해 1.8KB 수준으로, 논리 섹터 캐시는 512바이트에 불과합니다. Azure RTOS ThreadX와 같이 Azure RTOS FileX의 크기는 애플리케이션에서 사용하는 서비스에 따라 자동으로 조정됩니다. 이렇게 하면 실질적으로 복잡한 구성 및 빌드 매개 변수가 제거되므로 개발자가 더 쉽게 작업을 수행할 수 있습니다.

## <a name="fast-execution"></a>고속 실행

Azure RTOS FileX는 FAT 항목 캐시뿐 아니라 논리 섹터 캐시를 제공합니다. 두 가지 모두 크기를 애플리케이션에서 직접 제어합니다. 또한 Azure RTOS FileX는 연속 클러스터 할당과, 직접 연속 클러스터 읽기 및 쓰기를 제공합니다. 전체 섹터의 읽기/쓰기 요청은 애플리케이션 버퍼와 미디어 간에 직접 이루어지므로 중간 버퍼링이 수행되지 않습니다. 이런 특징과 일반 성능 중심 디자인 철학으로 Azure RTOS FileX에서 가능한 가장 빠른 성능을 구현하고 있습니다.

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

## <a name="fastest-time-to-market"></a>가장 빠른 출시 시간

Azure RTOS FileX는 설치, 학습, 사용, 디버그, 확인, 인증 및 유지 관리를 손쉽게 수행할 수 있습니다. 이 덕분에 Azure RTOS FileX는 포함된 IoT 디바이스에 가장 널리 사용되는 FAT 파일 시스템 중 하나가 되었습니다. 일관된 신속 출시가 가능한 몇 가지 이유는 다음과 같습니다.

- 품질 설명서 – [Azure RTOS FileX 사용자 가이드](about-this-guide.md)를 검토하고 직접 확인할 수 있습니다.
- 전체 소스 코드 가용성
- 사용하기 쉬운 API
- 포괄적인 고급 기능 세트

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a>TUV 및 UL을 비롯한 여러 안전 표준의 사전 인증

![SGS-TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

Azure RTOS FileX는 안전이 매우 중요한 시스템에서의 사용을 위해, IEC-61508 SIL 4, IEC-62304 SW 안전 등급 C, ISO 26262 ASIL D 및 EN 50128에 따라 SGS-TUV Saar 인증을 받았습니다. 이 인증은 “전기, 전자 및 프로그램 가능한 전자 안전 관련 시스템의 기능적 안전”에 대한 최고 수준의 IEC-61508, IEC-62304, ISO 26262 및 EN 50128의 안전 무결성 등급에 따라, FileX를 보안 관련 소프트웨어의 개발에 사용할 수 있음을 확인합니다. 독일 SGS-Group 및 TUV Saarland의 공동 벤처인 SGS-TUV Saar는 세계적으로 안전 관련 시스템용 포함 소프트웨어를 테스트, 감사, 확인 및 검증하는 최고 권위의 독립 기업으로 자리했습니다. 산업 보안 표준 IEC 61508과, 거기에서 파생된 모든 표준(IEC-62304, ISO 26262 및 EN 50128 포함)은 전기, 전자 및 프로그래밍 가능한 전자 안전 관련 의료 장비, 공정 제어 시스템, 산업용 기계, 자동차, 철도 제어 시스템의 기능 안전을 보장하는 데 사용됩니다.

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="CRU UL 인증":::

UL은 Azure RTOS FileX가 프로그래밍 가능한 구성 요소에서의 소프트웨어에 대한 UL 60730-1 부칙 H, CSA E60730-1 부칙 H, IEC 60730-1 부칙 H, UL 60335-1 부칙 R, IEC 60335-1 부칙 R 및 UL 1998 안전 표준의 규정을 준수한다고 인정했습니다. UL은 전기의 공공 도입에서부터 지속 가능성, 재생 에너지 및 나노 기술의 혁신에 이르기까지 안전 솔루션을 혁신하는 1세기 이상의 전문 지식을 보유한 글로벌 독립 안전 과학 기업입니다.

TUV 및 UL 인증과 관련한 아티팩트(인증서, 안전 매뉴얼, 테스트 보고서 등)는 판매 가능합니다.

애플리케이션에 추가 인증이 필요한 경우, 실제 하드웨어 플랫폼을 사용한 다양한 표준에 대한 턴키 방식의 인증을 제공하고 애플리케이션 코드까지도 다루는 인증 서비스를 Microsoft를 통해 사용할 수 있습니다.

## <a name="one-simple-license"></a>하나의 간단한 라이선스

사전에 사용이 허가된 디바이스에 배포하는 경우에는 소스 코드를 사용 및 테스트하는 데 비용이 들지 않으며 프로덕션 라이선스에 대한 비용도 부과되지 않습니다. 다른 모든 디바이스에는 간단한 연간 라이선스가 필요합니다.

## <a name="full-highest-quality-source-code"></a>최고 품질의 전체 소스 코드

오랜 시간을 통해 FileX 소스 코드는 품질 및 이해 용이성의 기준을 정립했습니다. 또한 파일당 하나의 함수를 포함하는 규칙을 통해 손쉬운 소스 탐색을 제공합니다.

## <a name="supports-most-popular-architectures"></a>대부분의 주요 아키텍처 지원

Azure RTOS FileX는 완전한 테스트와 지원을 통해 다음과 같이 대부분의 주요 32/64비트 마이크로프로세서에서 실행되며, 바로 사용할 수 있습니다.

**아날로그 디바이스**: SHARC, Blackfin, CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: Apollo MCU

**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64비트/R4/R5, TrustZone ARMv8-M

**Cadence**: Xtensa, Diamond

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi

**Cypress**: RISC-V

**EnSilica**: eSi-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel**; **Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10

**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

**Microsemi**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, Synergy

**Silicon** Labs: EFM32

**Synopsys**: ARC 600, 700, ARC EM, ARC HS

**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7

**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C

**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*나열된 모든 타이밍 및 크기 수치는 예상치이며, 개발 플랫폼에 따라 다를 수 있습니다.*
