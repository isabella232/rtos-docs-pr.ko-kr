---
title: Azure RTOS ThreadX 가이드 정보
description: 이 가이드는 Microsoft 고성능 실시간 커널인 Azure RTOS ThreadX에 대한 포괄적인 정보를 제공합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 28f088409fdd5e2c075cbf90b21d3d260c811806066e74bffc395207cde0239c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802127"
---
# <a name="about-the-azure-rtos-threadx-guide"></a>Azure RTOS ThreadX 가이드 정보

이 가이드는 Microsoft 고성능 실시간 커널인 Azure RTOS ThreadX에 대한 포괄적인 정보를 제공합니다. 

포함된 실시간 소프트웨어 개발자를 위한 것입니다. 개발자는 표준 실시간 운영 체제 함수 및 C 프로그래밍 언어에 대해 잘 알고 있어야 합니다.

## <a name="organization"></a>조직

[1장](chapter1.md) - Azure RTOS ThreadX와 실시간 포함된 개발과의 관계에 대한 기본 개요를 제공합니다.

[2장](chapter2.md) - 애플리케이션에서 *즉시* Azure RTOS ThreadX를 설치하고 사용하는 기본 단계를 제공합니다.

[3장](chapter3.md) - 고성능 실시간 커널인 Azure RTOS ThreadX의 기능 작업에 대해 자세히 설명합니다.

[4장](chapter4.md) - Azure RTOS ThreadX에 대한 애플리케이션의 인터페이스에 대해 자세히 설명합니다.

[5장](chapter5.md) - Azure RTOS ThreadX 애플리케이션용 I/O 드라이버 작성에 대해 설명합니다.

[6장](chapter6.md) - 모든 Azure RTOS ThreadX 프로세서 지원 패키지와 함께 제공되는 데모 애플리케이션에 대해 설명합니다.

[부록 A](appendix-a.md) - Azure RTOS ThreadX API

[부록 B](appendix-b.md) - Azure RTOS ThreadX 상수

[부록 C](appendix-c.md) - Azure RTOS ThreadX 데이터 형식

[부록 D](appendix-d.md) - ASCII 차트

## <a name="guide-conventions"></a>가이드 규칙

*기울임꼴* - 서체는 책 제목을 나타내고, 중요한 단어를 강조하고, 매개 변수를 나타냅니다.

**굵게** - 서체는 키워드, 상수, 형식 이름, 사용자 인터페이스 요소, 변수 이름을 나타내며, 중요한 단어를 추가로 강조 표시합니다.

***기울임꼴 및 굵게*** - 서체는 파일 이름 및 함수 이름을 나타냅니다.

> [!IMPORTANT]
> 정보 기호는 성능 또는 기능에 영향을 줄 수 있는 중요한 정보나 추가 정보를 강조합니다.

> [!WARNING]
> 경고 기호는 심각한 오류가 발생할 수 있기 때문에 개발자가 피해야 하는 상황에 주목합니다.

## <a name="azure-rtos-threadx-data-types"></a>Azure RTOS ThreadX 데이터 형식

사용자 지정 Azure RTOS ThreadX 컨트롤 구조 데이터 형식 외에도 Azure RTOS ThreadX 서비스 호출 인터페이스에 사용되는 일련의 특수 데이터 형식이 있습니다. 이러한 특수 데이터 형식은 기본 C 컴파일러의 데이터 형식에 직접 매핑됩니다. 이는 서로 다른 C 컴파일러 간의 이식성을 보장하기 위해 수행됩니다. 정확한 구현은 원본에 포함된 ***tx_port.h*** 파일에서 찾을 수 있습니다.

다음은 Azure RTOS ThreadX 서비스 호출 데이터 형식 및 관련된 의미의 목록입니다.

| 데이터 형식  | Description |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **UINT** | 부호 없는 기본 정수입니다. 이 형식은 8비트의 부호 없는 데이터를 지원해야 합니다. 그러나 가장 편리한 부호 없는 데이터 형식에 매핑됩니다. |
| **ULONG** | 부호 없는 long 형식입니다. 이 형식은 32비트의 부호 없는 데이터를 지원해야 합니다. |
| **VOID** | 거의 항상 컴파일러의 void 형식과 동일합니다. |
| **CHAR** | 표준 8비트 문자 형식이 가장 일반적입니다. |
|  |  |

Azure RTOS ThreadX 원본 내에서 추가 데이터 형식이 사용됩니다. ***tx_port.h*** 파일에도 있습니다.

## <a name="customer-support-center"></a>고객 지원 센터

다음 단계에 대한 질문 또는 도움이 필요하면 Azure Portal을 통해 지원 티켓을 제출하세요. 지원 요청을 보다 효율적으로 해결할 수 있도록 이메일 메시지에 다음 정보를 제공해 주세요.

1. 발생 빈도와 안정적으로 재현할 수 있는지 여부를 포함한 문제에 대한 자세한 설명입니다.
2. 문제가 발생하기 전의 애플리케이션 및/또는 Azure RTOS ThreadX의 변경 내용에 대한 자세한 설명입니다.
3. 배포의 *tx_port.h* 파일에 있는 *_tx_version_id* 문자열의 내용입니다. 이 문자열은 런타임 환경에 대한 유용한 정보를 제공합니다.
4. **_tx_build_options** **ULONG** 변수의 RAM에 있는 내용입니다. 이 변수는 Azure RTOS ThreadX 라이브러리가 빌드되는 방법에 대한 정보를 제공합니다.
