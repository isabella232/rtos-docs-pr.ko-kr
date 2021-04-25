---
title: 챕터 1 - Azure RTOS FileX 소개
description: Azure RTOS FileX는 심층에 내장된 애플리케이션을 위한 완전한 FAT 형식 미디어 및 파일 관리 시스템입니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be7e6f9cd9fbc69ac0908d1de733dac1c4f73bf6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810333"
---
# <a name="chapter-1---introduction-to-azure-rtos-filex"></a>챕터 1 - Azure RTOS FileX 소개

Azure RTOS FileX는 심층에 내장된 애플리케이션을 위한 완전한 FAT 형식 미디어 및 파일 관리 시스템입니다. 이 챕터에서는 FileX를 소개하고 해당 애플리케이션과 이점을 설명합니다.

## <a name="filex-unique-features"></a>FileX의 고유 기능

Azure RTOS FileX는 RAM 디스크, FLASH 관리자 및 실제 물리적 디바이스를 포함하여 동시에 무제한의 미디어 디바이스를 지원 합니다. 12비트, 16비트 및 32비트 FAT(파일 할당 테이블) 형식을 지원하고, exFAT(확장 파일 할당 테이블) 및 연속 파일 할당을 지원하며, 크기와 성능 면에서 최적화되어 있습니다. FileX에는 내결함성 지원, 미디어 열기/닫기 및 파일 쓰기 콜백 함수도 포함됩니다.

플래시 디바이스를 대상으로 증가하는 요구에 부응하도록 설계된 FileX는 ThreadX와 동일한 디자인 및 코딩 메서드를 사용합니다. 모든 Microsoft 제품과 마찬가지로 FileX는 전체 ANSI C 소스 코드를 사용하여 배포되며 런타임 로열티가 없습니다.

### <a name="product-highlights"></a>제품 중요 정보

- 완벽한 ThreadX 프로세서 지원
- 로열티 없음
- 전체 ANSI C 소스 코드
- 실시간 성능
- 반응형 기술 지원
- 무제한 FileX 개체(미디어, 디렉터리 및 파일)
- 동적 FileX 개체 생성/삭제
- 유연한 메모리 사용
- 크기 자동 조정
- 적은 공간(최소 6Kb) 명령 영역 크기: 6-30K
- ThreadX와의 완전한 통합
- Endian 중립
- 구현하기 쉬운 FileX I/O 드라이버
- 12비트, 16비트 및 32비트 FAT 지원
- exFAT 지원
- 긴 파일 이름 지원
- 내부 FAT 항목 캐시
- 유니코드 이름 지원
- 연속 파일 할당
- 연속 섹터 및 클러스터 읽기/쓰기
- 내부 논리 섹터 캐시
- RAM 디스크 데모는 즉시 실행
- 미디어 형식 기능
- 오류 검색 및 복구
- 내결함성 옵션
- 성능 통계 기본 제공
- 독립 실행형 지원(Azure RTOS는 해당하지 않음)

## <a name="safety-certifications"></a>안전 인증

### <a name="tv-certification"></a>TÜV 인증

FileX는 IEC-61508 및 IEC-62304에 따라 안전이 중요한 시스템에서 사용하도록 SGS-TÜV Saar에서 인증되었습니다. 이 인증은 "전기, 전자 및 프로그램 가능한 전자 안전 관련 시스템의 기능적 안전"에 대한 최고 수준의 IEC(International Electrotechnical Commission) 61508 및 IEC 62304의 안전 무결성 등급에 따라, FileX를 보안 관련 소프트웨어의 개발에 사용할 수 있음을 확인합니다. 독일의 SGS-Group 및 TÜV Saarland의 합작으로 구성된 SGS-TÜV Saar는 전 세계의 안전 관련 시스템에 내장된 소프트웨어를 테스트, 감사, 확인, 인증하며, 널리 인정받는 주요한 독립 회사로 발전했습니다. 산업 보안 표준 IEC 61508과, 거기에서 파생된 모든 표준(IEC 62304 포함)은 전기, 전자 및 프로그래밍 가능한 전자 안전 관련 의료 장비, 공정 제어 시스템, 산업용 기계, 철도 제어 시스템의 기능 안전을 보장하는 데 사용됩니다.

SGS-TÜV Saar는 ISO 26262 표준에 따라 안전이 중요한 자동차 시스템에서 FileX를 사용할 수 있도록 인증했습니다. 또한 FileX는 최고 수준의 ISO 26262 인증을 나타내는 ASIL(자동차 안전 무결성 수준) D로 인증되었습니다.

그리고 SGS-TÜV Saar는 안전이 중요한 철도 응용 분야에서 FileX를 사용할 수 있도록 인증했으며 SW-SIL 4까지 EN 50128 표준을 충족하는 것으로 확인했습니다.

![SGS TUV Saar 로고](./media/user-guide/sgs-tuv-saar-logo.png)

- 최대 SIL 4의 IEC 61508
- 최대 SW 안전 등급 C의 IEC 62304
- ISO 26262 ASIL D
- EN 50128 SW-SIL 4

> [!IMPORTANT]
> TÜV에서 인증한 FileX 버전 또는 테스트 보고서, 인증서 및 관련 설명서의 가용성에 대한 자세한 내용은 Microsoft에 문의하세요.*

### <a name="ul-certification"></a>UL 인증

UL은 FileX가 프로그래밍 가능한 구성 요소에서의 소프트웨어에 대한 UL 60730-1 부칙 H, CSA E60730-1 부칙 H, IEC 60730-1 부칙 H, UL 60335-1 부칙 R, IEC 60335-1 부칙 R 및 UL 1998 안전 표준의 규정을 준수한다고 인증했습니다. IEC 60335-1 표준에서는 해당 부록 H에 포함된 "소프트웨어를 사용하여 제어"에 대한 요구 사항이 있는 IEC/UL 60730-1과 함께, 부록 R의 "프로그래밍 가능 전자 회로"에 대한 요구 사항을 설명합니다. IEC 60730 부록 H 및 IEC 60335-1 부록 R은 세탁기, 식기세척기, 건조기, 냉장고, 냉동고 및 오븐과 같은 가전 제품에서 사용되는 MCU 하드웨어 및 소프트웨어의 안전을 다룹니다.

![C RU US 2](./media/user-guide/c-ru-us-logo.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]
>*UL에서 인증한 FileX 버전 또는 테스트 보고서, 인증서 및 관련 설명서의 가용성에 대한 자세한 내용은 Microsoft에 문의하세요.*

## <a name="powerful-services-of-filex"></a>FileX의 강력한 서비스

### <a name="multiple-media-management"></a>다중 미디어 관리

FileX는 개수에 제한 없이 물리적 미디어를 지원할 수 있습니다. 각 미디어 인스턴스에는 ***fx_media_open*** 호출에 지정된 고유 메모리 영역 및 관련 드라이버가 있습니다. FileX의 기본 배포에는 간단한 RAM 미디어 드라이버와 이 RAM 디스크를 사용하는 데모 시스템이 함께 제공됩니다.

### <a name="logical-sector-cache"></a>논리 섹터 캐시

모든 섹터 전송의 수를 미디어와 미디어 간에 줄이면 FileX 논리 섹터 캐시가 성능을 크게 향상시킵니다. FileX는 열려 있는 각 미디어의 논리 섹터 캐시를 유지 관리합니다. 논리 섹터 캐시의 깊이는 ***fx_media_open*** API 호출을 사용하여 FileX에 제공된 메모리 양에 따라 결정됩니다.

### <a name="contiguous-file-support"></a>연속적인 파일 지원

FileX는 API 서비스 ***fx_file_allocate*** 를 통해 연속적인 파일 지원을 제공하여 파일 액세스를 개선하고 시간 결정적으로 만듭니다. 이 루틴은 요청된 메모리의 양을 가져와서 요청을 충족하는 일련의 인접한 클러스터를 찾습니다. 이러한 클러스터를 찾은 경우 할당된 클러스터의 파일 체인에 포함되도록 하여 미리 할당됩니다. 물리적 미디어를 이동하면 FileX의 연속적인 파일 지원으로 성능이 크게 향상되고 액세스를 시간 결정적으로 만듭니다.

### <a name="dynamic-creation"></a>동적으로 생성

FileX를 사용하면 시스템 리소스를 동적으로 만들 수 있습니다. 이는 애플리케이션에 다중 또는 동적 구성 요구 사항이 있는 경우에 특히 중요합니다. 또한 사용할 수 있는 FileX 리소스(미디어 또는 파일)의 수에는 미리 정해진 제한이 없습니다. 또한 시스템 개체의 수는 성능에 영향을 주지 않습니다.

## <a name="easy-to-use-api"></a>사용하기 쉬운 API

FileX는 쉽게 이해하고 사용할 수 있는 방식으로 가장 심층적인 내장 파일 시스템 기술을 제공합니다. FileX API(애플리케이션 프로그래밍 인터페이스)를 사용하면 서비스를 직관적이고 일관되게 유지할 수 있습니다. 다른 파일 시스템에서 널리 사용되는 "알파벳 수프" 서비스를 해독할 필요가 없습니다.

FileX 버전 5 서비스의 전체 목록은 [부록 A](appendix-a.md)를 참조하십시오.

## <a name="exfat-support"></a>exFAT 지원

exFAT(확장 파일 할당 테이블)은 Microsoft에서 설계한 파일 시스템으로, 파일 크기가 FAT32 파일 시스템이 제한하는 2GB를 초과할 수 있도록 허용합니다. 이는 용량이 32GB를 초과하는 SD 카드에 대한 기본 파일 시스템입니다. FileX exFAT 형식으로 포맷된 SD 카드나 플래시 드라이브는 Windows와 호환됩니다. exFAT는 약 10억 기가바이트(GB)에 달하는 최대 1엑사바이트(EB)의 파일 크기를 지원합니다.

exFAT를 사용하려면 기호 ***FX_ENABLE_EXFAT** _ 정의를 사용하여 FileX 라이브러리를 다시 컴파일해야 합니다. 미디어를 열 때 FileX는 미디어 유형을 검색합니다. 미디어가 exFAT로 포맷된 경우 FileX는 exFAT 표준에 따라 파일 시스템을 읽고 씁니다. exFAT를 사용하여 새 미디어의 형식을 지정하려면 _*_fx_media_exFAT_format_** 서비스를 사용합니다. 기본적으로 exFAT는 사용하지 않도록 설정됩니다.

## <a name="fault-tolerant-support"></a>내결함성 지원

FileX 내결함성 모듈은 파일이나 디렉터리를 업데이트하는 동안 중단으로 발생하는 파일 시스템 손상을 방지하도록 설계되었습니다. 예를 들어 파일에 데이터를 추가할 때 FileX는 파일의 내용, 디렉터리 항목 및 FAT 항목을 업데이트해야 합니다. 이 업데이트 순서가 중단된 경우(예: 전원 결함 또는 미디어를 업데이트 중에 꺼낼 경우) 파일 시스템이 일관되지 않은 상태에 있어 다른 파일의 손상이 발생하면서 전체 파일 시스템의 무결성에 영향을 줄 수 있습니다.

FileX 내결함성 모듈은 파일 또는 디렉터리를 업데이트하는 데 필요한 모든 단계를 기록하는 방식으로 작동합니다. 이 로그 항목은 FileX가 찾아서 액세스할 수 있는 전용 섹터(블록)의 미디어에 저장됩니다. 적절한 파일 시스템이 없어도 로그 데이터의 위치에 액세스할 수 있습니다. 따라서 파일 시스템이 손상된 경우 FileX는 여전히 로그 항목을 찾아 파일 시스템을 다시 정상 상태로 복원할 수 있습니다.

FileX에서 파일 또는 디렉터리를 업데이트하면 로그 항목이 생성됩니다. 업데이트 작업이 성공적으로 완료되면 로그 항목이 제거됩니다. 성공적으로 파일을 업데이트 한 후에 로그 항목이 제대로 제거되지 않은 경우, 복구 프로세스에서 로그 항목의 내용이 파일 시스템과 일치하는 것으로 확인되면 작업을 수행할 필요가 없으며 로그 항목을 정리할 수 있습니다.

파일 시스템 업데이트 작업이 중단된 경우 다음에 FileX로 미디어를 탑재하면 내결함성 모듈이 로그 항목을 분석합니다. 로그 항목의 정보를 통해 FileX는 파일 시스템에 이미 적용된 부분 변경 내용(파일 업데이트 작업의 초기 단계에서 오류가 발생하는 경우)을 취소할 수 있습니다. 또는 로그 항목에 다시 실행 정보가 포함된 경우 FileX는 이전 작업을 완료하는 데 필요한 변경 내용을 적용할 수 있습니다.

이 내결함성 기능은 FileX에서 지원하는 모든 FAT 파일 시스템(FAT12, FAT16, FAT32, exFAT 등)에서 사용할 수 있습니다. 기본적으로 내결함성 기능은 FileX에서 사용되지 않습니다. 내결함성 기능을 사용하도록 설정하려면 **FX_ENABLE_FAULT_TOLERANT** 기호 및 **FX_FAULT_TOLERANT** 정의로 FileX가 빌드되어야 합니다. 런타임에서 애플리케이션은 **_fx_fault_tolerant_enable_** 를 호출하여 내결함성 서비스를 시작합니다.
서비스가 시작된 후 모든 파일 및 디렉터리 쓰기 작업은 내결함성이 있는 모듈을 통해 진행 됩니다.

내결함성 서비스가 시작되면 먼저 내결함성이 있는 모듈에서 미디어를 보호하는지를 검색 합니다. 그렇지 않은 경우 FileX는 파일 시스템의 무결성을 가정하고, 로깅 및 캐싱에 사용할 파일 시스템의 빈 블록을 할당하여 보호를 시작합니다. 내결함성 모듈 로그가 파일 시스템에서 발견된 경우 로그 항목을 분석합니다. FileX는 로그 항목의 내용에 따라 이전 작업을 되돌리거나 이전 작업을 다시 실행합니다. 이전의 모든 로그 항목이 처리된 후 파일 시스템을 사용할 수 있게 됩니다. 이렇게 하면 FIleX가 알려진 양호한 상태에서 시작됩니다.

FileX 내결함성 모듈에서 미디어를 보호한 후에는 미디어가 다른 파일 시스템으로 업데이트되지 않습니다. 그렇게 하면 파일 시스템의 로그 항목이 FAT 테이블의 콘텐츠(디렉터리 항목)와 일치하지 않게 됩니다. 오류 허용 모듈이 있는 FileX로 미디어를 다시 이동하기 전에 다른 파일 시스템으로 업데이트하는 경우 결과가 정의되지 않습니다.

## <a name="callback-functions"></a>콜백 함수

다음 세 가지 콜백 함수가 FileX에 추가됩니다.

- 미디어 열기 콜백
- 미디어 닫기 콜백
- 파일 쓰기 콜백

등록 후 이러한 함수는 이러한 이벤트가 발생할 때 애플리케이션에 알립니다.

## <a name="easy-integration"></a>간편한 통합

FileX는 거의 모든 플래시 또는 미디어 디바이스와 쉽게 통합됩니다. FileX의 포팅은 간단합니다. 이 가이드는 프로세스를 자세히 설명하고 있습니다. 데모 시스템의 RAM 드라이버를 사용하면 시작하기에 아주 좋습니다.