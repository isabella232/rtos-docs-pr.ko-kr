---
title: Azure RTOS GUIX 사용자 가이드
description: 이 가이드는 Microsoft의 고성능 GUI 제품인 Azure RTOS GUIX에 대한 포괄적인 정보를 포함합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: e7cc1f44648111a75cd6b28d6b98480b721af9c8521e8fcb8cdac6f24c5514e7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784702"
---
# <a name="about-guix-user-guide"></a>GUIX 사용자 가이드 정보

이 가이드는 Microsoft의 고성능 GUI 제품인 Azure RTOS GUIX에 대한 포괄적인 정보를 포함합니다. 이는 기본적인 GUI 개념, Azure RTOS ThreadX 및 C 프로그래밍 언어에 익숙한 포함된 실시간 소프트웨어 개발자를 대상으로 합니다.

## <a name="organization"></a>조직

[1장 - Azure RTOS GUIX 소개](chapter-1.md)

[2장 - Azure RTOS GUIX 설치 및 사용](chapter-2.md)

[3장 - Azure RTOS GUIX의 기능 개요](chapter-3.md)

[4장 - Azure RTOS GUIX 서비스 설명](chapter-4.md)

[5장 - Azure RTOS GUIX 디스플레이 드라이버](chapter-5.md)  

[Azure RTOS GUIX 예제](guix-example.md)

[부록 A - Azure RTOS GUIX 색 정의](appendix-a.md)

[부록 B - Azure RTOS GUIX 색 형식](appendix-b.md)

[부록 C - Azure RTOS GUIX 위젯 스타일](appendix-c.md)

[부록 D - Azure RTOS GUIX 브러시, 캔버스 및 그라데이션 특성](appendix-d.md)

[부록 E - Azure RTOS GUIX 이벤트 설명](appendix-e.md)

[부록 F - Azure RTOS GUIX RTOS 바인딩 서비스](appendix-f.md)

[부록 G - Azure RTOS GUIX 글꼴 구조](appendix-g.md)

[부록 H - Azure RTOS GUIX 빌드 시간 구성 플래그](appendix-h.md)

[부록 I - Azure RTOS GUIX 정보 구조](appendix-i.md)

## <a name="guide-conventions"></a>가이드 규칙

*기울임꼴* - 서체는 책 제목을 나타내고, 중요한 단어를 강조하고, 변수를 나타냅니다.

**굵게** - 서체는 파일 이름, 키워드를 표시하고 중요한 단어와 변수를 추가로 강조 표시합니다.

> [!IMPORTANT]
> 정보 기호는 성능 또는 기능에 영향을 줄 수 있는 중요한 정보나 추가 정보를 강조합니다.

## <a name="azure-rtos-guix-data-types"></a>Azure RTOS GUIX 데이터 형식

사용자 지정 Azure RTOS GUIX 컨트롤 구조 데이터 형식 외에도 Azure RTOS GUIX 서비스 호출 인터페이스에 사용되는 몇 가지 특수 데이터 형식이 있습니다. 이러한 특수 데이터 형식은 기본 C 컴파일러의 데이터 형식에 직접 매핑됩니다. 이 매핑은 서로 다른 C 컴파일러 간의 이식성을 보장하기 위해 수행됩니다. 정확한 구현은 ThreadX에서 상속되며 ThreadX 배포에 포함된 ***tx_port.h*** 파일에서 찾을 수 있습니다.

다음은 Azure RTOS GUIX 서비스 호출 데이터 형식 및 관련된 의미의 목록입니다.

| <!-- --> | <!-- --> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **UINT**             | 부호 없는 기본 정수입니다. 이 형식은 가장 편리한 부호 없는 데이터 형식에 매핑됩니다.                                |
| **INT**              | 부호 있는 기본 정수입니다. 이 형식은 가장 편리한 부호 있는 데이터 형식에 매핑됩니다.                                    |
| **ULONG**            | 부호 없는 long 형식입니다. 이 형식은 32비트의 부호 없는 데이터를 지원해야 합니다.                                                      |
| **VOID**             | 거의 항상 컴파일러의 void 형식과 동일합니다.                                                                 |
| **GX_CHAR**         | 일반적으로 형식 정의는 컴파일러 정의 문자 유형입니다.                                                               |
| **GX_BYTE**          | 8비트 부호 있는 형식입니다.                                                                                                    |
| **GX_UBYTE**         | 부호 없는 8비트 형식입니다.                                                                                                  |
| **GX_VALUE**        | 16 또는 32비트 부호 있는 형식입니다. 대상 시스템의 성능을 최적화하기 위해 필요에 따라 정의됩니다.                                |
| **GX_FIXED_VAL**   | 고정 소수점 숫자 데이터 형식입니다.                                                                                        |
| **GX_RESOURCE_ID** | 부호 없는 long 형식입니다.                                                                                                   |
| **GX_COLOR**        | 부호 없는 long 형식입니다.                                                                                                   |
| **GX_STRING**       | GX_CHAR \*gx_string_ptr 및 UINT gx_string_length를 포함하는 구조입니다.                                          |
| **GX_POINT**        | gx_point_x 및 gx_point_y를 포함하는 구조입니다.                                                                   |
| **GX_RECTANGLE**    | gx_rectangle_left, gx_rectangle_top, gx_rectangle_right 및 gx_rectangle_bottom 필드를 포함하는 구조입니다. |
| **GX_GLYPH**        | 문자 모양 메트릭을 포함하는 구조입니다.                                                                                   |
| **GX_FONT**         | 글꼴 메트릭을 포함하는 구조입니다.                                                                                    |
| **GX_BRUSH**        | 브러시 메트릭을 포함하는 구조입니다.                                                                               |
**GX_PIXELMAP**       | pixelmap 메트릭을 포함하는 구조입니다.

Azure RTOS GUIX 원본 내에서 추가 데이터 형식이 사용됩니다. ***tx_port.h** _ 또는 _ *_gx_port.h_** 파일에도 있습니다.

## <a name="customer-support-center"></a>고객 지원 센터

다음 단계에 대한 질문 또는 도움이 필요하면 Azure Portal을 통해 지원 티켓을 제출하세요. 지원 요청을 보다 효율적으로 해결할 수 있도록 이메일 메시지에 다음 정보를 제공해 주세요.

1. 발생 빈도와 안정적으로 재현할 수 있는지 여부를 포함한 문제에 대한 자세한 설명입니다.

2. 문제가 발생하기 전의 애플리케이션 및/또는 Azure RTOS GUIX의 변경 내용에 대한 자세한 설명입니다.

3. 배포의 *_**tx_port.h**_ 및 _ *_gx_port.h_** 파일에 있는 _tx_version_id 및 gx_version_id 문자열의 내용입니다. 이러한 문자열은 런타임 환경에 대한 유용한 정보를 제공합니다.

4. 다음 ULONG 변수의 RAM에 있는 내용:

    **_tx_build_options** **_gx_system_build_options**

    이러한 변수는 Azure RTOS ThreadX 및 Azure RTOS GUIX 라이브러리가 빌드되는 방법에 대한 정보를 제공합니다.

5. 다음 ULONG 변수의 RAM에 있는 내용:

    **_gx_system_last_error** **_gx_system_error_count**

    이러한 변수는 Azure RTOS GUIX에서 내부 시스템 오류를 추적합니다. _gx_system_error_count가 1보다 크면 _gx_system_error_process 함수에서 함수 반환에 대한 중단점을 설정하고 이 시점에서 _gx_system_last_error 값을 제공합니다. 이렇게 하면 첫 번째 내부 Azure RTOS GUIX 시스템 오류가 생성됩니다.

6. 문제가 탐지된 직후에 캡처된 추적 버퍼. 이렇게 하려면 TX_ENABLE_EVENT_TRACE를 사용하여 Azure RTOS ThreadX 및 Azure RTOS GUIX 라이브러리를 빌드하고 추적 버퍼 정보를 사용하여 tx_trace_enable을 호출합니다.

7. 사용 중인 Azure RTOS GUIX Studio 프로젝트(해당하는 경우) 또는 보고하는 문제점을 보여 줄 수 있는 최소 작은 프로젝트에 있습니다.
