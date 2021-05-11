---
title: Azure RTOS FileX 사용자 가이드
description: 이 가이드에는 Microsoft의 고성능 실시간 파일 시스템인 Azure RTOS FileX에 대한 포괄적인 정보가 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 640d9ed4c8037d3af6c5f45158c9496ad1258a3c
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550102"
---
# <a name="about-this-filex-user-guide"></a>해당 FileX 사용자 가이드 정보

이 가이드에는 Microsoft의 고성능 실시간 포함된 파일 시스템인 Azure RTOS FileX에 대한 포괄적인 정보가 포함되어 있습니다. 이 가이드를 최대한 활용하려면 표준 실시간 운영 체제 함수, FAT 파일 시스템 서비스 및 C 프로그래밍 언어에 대해 잘 알고 있어야 합니다.

## <a name="organization"></a>조직

[1장](chapter1.md) - Azure RTOS FileX 소개

[2장](chapter2.md) - Azure RTOS ThreadX 애플리케이션에서 Azure RTOS FileX를 설치하고 사용하기 위한 기본 단계를 제공합니다.

[3장](chapter3.md) - Azure RTOS FileX 시스템의 기능 개요와 FAT 파일 시스템 형식에 대한 기본 정보를 제공합니다.

[4장](chapter4.md) - Azure RTOS FileX에 대한 애플리케이션의 인터페이스에 대해 자세히 설명합니다.

[5장](chapter5.md) - 제공된 Azure RTOS FileX RAM 드라이버 및 사용자 지정 Azure RTOS FileX 드라이버를 작성하는 방법에 대해 설명합니다.

[6장](chapter6.md) - Azure RTOS FileX 내결함성 모듈을 설명합니다.

[부록 A](appendix-a.md) - Azure RTOS FileX 서비스

[부록 B](appendix-b.md) - Azure RTOS FileX 상수

[부록 C](appendix-c.md) - Azure RTOS FileX 데이터 형식

[부록 D](appendix-d.md) - ASCII 차트

## <a name="guide-conventions"></a>가이드 규칙

*기울임꼴* - 서체는 책 제목을 나타내고, 중요한 단어를 강조하고, 변수를 나타냅니다.

**굵게** - 서체는 파일 이름, 키워드를 표시하고 중요한 단어와 변수를 추가로 강조 표시합니다.

> [!NOTE]
> 정보 기호는 성능 또는 기능에 영향을 줄 수 있는 중요한 정보나 추가 정보를 강조합니다.

> [!IMPORTANT]
> 경고 기호는 심각한 오류가 발생할 수 있기 때문에 개발자가 피해야 하는 상황을 강조합니다.

## <a name="filex-data-types"></a>FileX 데이터 형식

사용자 지정 Azure RTOS FileX 컨트롤 구조 데이터 형식 외에도 Azure RTOS FileX 서비스 호출 인터페이스에 사용되는 일련의 특수 데이터 형식이 있습니다. 이러한 특수 데이터 형식은 기본 C 컴파일러의 데이터 형식에 직접 매핑됩니다. 이 매핑은 서로 다른 C 컴파일러 간의 이식성을 보장하기 위해 수행됩니다. 정확한 구현은 Azure RTOS ThreadX에서 상속되며 Azure RTOS ThreadX 배포에 포함된 tx_port.h 파일에서 찾을 수 있습니다.

다음은 Azure RTOS FileX 서비스 호출 데이터 형식 및 관련된 의미의 목록입니다.

| 유형  | Description  |
|---|---|
| **UINT** | 부호 없는 기본 정수입니다. 이 형식은 8비트의 부호 없는 데이터를 지원해야 합니다. 그러나 가장 편리한 부호 없는 데이터 형식에 매핑됩니다. |
| **ULONG** | 부호 없는 long 형식입니다. 이 형식은 32비트의 부호 없는 데이터를 지원해야 합니다. |
| **VOID** | 거의 항상 컴파일러의 void 형식과 동일합니다. |
| **CHAR** | 표준 8비트 문자 형식이 가장 일반적입니다. |
| **ULONG64** | 64비트의 부호 없는 정수 데이터 형식입니다. |

FileX 원본 내에서 추가 데이터 형식이 사용됩니다. ***tx_port.h** _ 또는 _ *_fx_port.h_** 파일에도 있습니다.

## <a name="customer-support-center"></a>고객 지원 센터

다음 단계에 대한 질문 또는 도움이 필요하면 Azure Portal을 통해 지원 티켓을 제출하세요. 지원 요청을 보다 효율적으로 해결할 수 있도록 이메일 메시지에 다음 정보를 제공해 주세요.

1. 발생 빈도와 안정적으로 재현할 수 있는지 여부를 포함한 문제에 대한 자세한 설명입니다.
2. 문제가 발생하기 전의 애플리케이션 및/또는 FileX의 변경 내용에 대한 자세한 설명입니다.
3. 배포의 _***tx_port.h**_ 및 _ *_fx_port.h_** 파일에 있는 _tx_version_id 및 fx_version_id 문자열의 내용입니다. 이러한 문자열은 런타임 환경에 대한 유용한 정보를 제공합니다.
4. 다음 **ULONG** 변수의 RAM에 있는 내용입니다. 이러한 변수는 ThreadX 및 FileX 라이브러리가 빌드되는 방법에 대한 정보를 제공합니다.

    **_tx_build_options**

    **_fx_system_build_options1**

    **_fx_system_build_options2**

    **_fx_system_build_options3**
