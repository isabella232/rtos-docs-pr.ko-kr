---
title: Azure RTOS TraceX 사용자 가이드
description: 이 가이드는 Microsoft의 Microsoft Windows 기반 시스템 분석 도구인 Azure RTOS TraceX에 대한 포괄적인 정보를 포함합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 89a39112d6fc6d231408179ebb3867c21f927326930a1610529b142aa71a1027
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784073"
---
# <a name="about-this-guide"></a>이 가이드의 내용

이 가이드는 Microsoft Azure RTOS용 Microsoft Windows 기반 시스템 분석 도구인 Azure RTOS TraceX에 대한 포괄적인 정보를 포함합니다.

Azure RTOS ThreadX RTOS(실시간 운영 체제) 및 추가 기능 구성 요소를 사용하는 포함된 실시간 소프트웨어 개발자를 위한 것입니다. 개발자는 표준 Azure RTOS ThreadX, Azure RTOS FileX 및 Azure RTOS NetX 개념을 숙지해야 합니다.

## <a name="organization"></a>조직

- [1장](chapter1.md) - Azure RTOS TraceX의 기본 개요를 포함하고 실시간 개발과의 관계를 설명합니다.
- [2장](chapter2.md) - Azure RTOS TraceX를 설치하고 사용하여 즉시 애플리케이션을 분석하는 기본 단계를 제공합니다.
- [3장](chapter3.md) - Azure RTOS TraceX의 주요 기능에 대해 설명합니다.
- [4장](chapter4.md) - Azure RTOS TraceX의 성능 분석 기능에 대해 자세히 설명합니다.
- [5장](chapter5.md) - Azure RTOS TraceX에서 볼 수 있는 추적 버퍼를 생성하기 위해 Azure RTOS ThreadX, Azure RTOS FileX 및 Azure RTOS NetX를 설정하는 방법을 설명합니다.
- [6장](chapter6.md) - Azure RTOS TraceX 이벤트에 대해 자세히 설명합니다.
- [7장](chapter7.md) - Azure RTOS FileX 이벤트에 대해 자세히 설명합니다.
- [8장](chapter8.md) - Azure RTOS NetX 이벤트에 대해 자세히 설명합니다.
- [9장](chapter9.md) - Azure RTOS USBX 이벤트에 대해 자세히 설명합니다.
- [10장](chapter10.md) - 사용자 지정 사용자 이벤트 만들기에 대해 자세히 설명합니다.
- [11장](chapter11.md) - 내부 추적 버퍼에 대해 자세히 설명합니다.
- [부록 A](appendix-a.md) - 추적 이벤트를 수집하기 위한 타임 스탬프 원본을 포함하는 Azure RTOS ThreadX 포트 관련 파일입니다.
- [부록 B](appendix-b.md) - 이벤트 추적 버퍼에 대한 구현 세부 정보를 표시하는 Azure RTOS ThreadX *tx_trace.h* 파일입니다.
- [부록 C](appendix-c.md) - 다양한 파일 형식을 적절한 Azure RTOS TraceX 이진 파일로 변환하기 위한 명령줄 유틸리티를 요약합니다.
- [부록 D](appendix-d.md) - 다양한 개발 도구에서 추적 파일을 덤프하는 예제입니다.

## <a name="guide-conventions"></a>가이드 규칙

*기울임꼴* - 서체는 책 제목을 나타내고, 중요한 단어를 강조하고, 변수를 나타냅니다.

**굵게** - 서체는 파일 이름, 키워드를 표시하고 중요한 단어와 변수를 추가로 강조 표시합니다.

> [!NOTE]
> 메모 정보를 나타냅니다.

## <a name="customer-support-center"></a>고객 지원 센터

다음 단계에 대한 질문 또는 도움이 필요하면 Azure Portal을 통해 지원 티켓을 제출하세요. 지원 요청을 보다 효율적으로 해결할 수 있도록 이메일 메시지에 다음 정보를 제공해 주세요.

1. 발생 빈도와 안정적으로 재현할 수 있는지 여부를 포함한 문제에 대한 자세한 설명입니다.
2. 문제가 발생하기 전의 애플리케이션 및/또는 Azure RTOS ThreadX의 변경 내용에 대한 자세한 설명입니다.
3. 배포의 *tx_port.h* 파일에 있는 *_tx_version_id* 문자열의 내용입니다. 이 문자열은 런타임 환경에 대한 유용한 정보를 제공합니다.
4. *_tx_build_options* ULONG 변수의 RAM에 있는 내용입니다. 이 변수는 Azure RTOS ThreadX 라이브러리가 빌드되는 방법에 대한 정보를 제공합니다.
