---
title: 부록 H - GUIX 빌드 시간 구성 플래그
description: GUIX 빌드 시간 구성 플래그에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 65095e326bc6809eba6e9472e2d74325351354ca
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811232"
---
# <a name="appendix-h---guix-build-time-configuration-flags"></a>부록 H - GUIX 빌드 시간 구성 플래그

GUIX는 여러 조건부 컴파일 옵션과 구성 값을 지원합니다. gx_user.h 헤더 파일 또는 컴파일러 명령줄에서 값을 미리 정의하여 조건부와 구성 값의 기본 설정을 재정의할 수 있습니다.

**GX_DISABLE_THREADX_BINDING**
- 기본값: 정의되지 않음
- 설명: 이 조건부를 사용하여 기본 ThreadX RTOS 바인딩을 사용하지 않도록 설정할 수 있습니다. ThreadX가 아닌 RTOS를 사용하여 GUIX를 실행하려면 #define GX_DISABLE_THREADX_BINDING을 사용하고 사용자 고유의 RTOS 바인딩 서비스를 제공해야 합니다.

GX_SYSTEM_TIMER_MS
- 기본값: 20
- 설명: 이 값은 원하는 GUIX 타이머 간격이나 정밀도를 정의합니다.

TX_TIMER_TICKS_PER_SECOND
- Default: 100
- 설명: 이 값은 TX 타이머 인터럽트 진동 수를 정의합니다. 기본 ThreadX 간격 타이머가 10ms이므로 이 값은 기본적으로 100Hz 주파수로 설정됩니다.

GX_SYSTEM_TIMER_TICKS
- 기본값: ((GX_SYSTEM_TIMER_MS * TX_TIMER_TICKS_PER_SECOND)/1000)
- 설명: 이 값은 GUIX 타이머 틱당 기본 RTOS 타이머 틱 수를 정의합니다. 기본값은 2입니다. 즉, GUIX 타이머 간격은 기본적으로 ThreadX 타이머 인터럽트 간격 2개 또는 20ms입니다.

GX_DISABLE_MULTITHREAD_SUPPORT
- 기본값: 정의되지 않음
- 설명: 이 컴파일 시간 조건부를 사용하여 GUIX API를 동시에 호출하는 여러 스레드에 대해 GUIX API 지원을 사용하지 않도록 설정할 수 있습니다. 하나의 애플리케이션 스레드만 GUIX API를 활용하는 경우 이 플래그를 정의하여 중요한 코드 섹션 보호와 관련된 시스템 오버헤드를 줄여야 합니다.

GX_DISABLE_UTF8_SUPPORT
- 기본값: 정의되지 않음
- 설명: 이 컴파일 시간 조건부를 사용하여 UTF8 형식 문자열 인코딩에 대한 GUIX 내부 지원을 제거할 수 있습니다. 애플리케이션에서 문자 값 M-0xff만 사용하는 경우 이 #define을 설정하면 UTF8 형식 문자열 인코딩 지원과 관련된 코드 크기와 오버헤드가 줄어듭니다.

GX_DISABLE_ARC_DRAWING_SUPPORT
- 기본값: 정의되지 않음
- 설명: 이 조건부를 사용하여 원호 그리기 함수 circle, arc, pie, ellipse에 대한 지원을 제거하면 GUIX 라이브러리 코드 크기와 GX_DISPLAY 구조체 크기를 줄일 수 있습니다. 이 함수는 기본 GUIX 위젯 세트에 필요하지 않습니다.

GX_DISABLE_SOFTWARE_DECODER_SUPPORT
- 기본값: 정의되지 않음
- 설명: 이 조건부를 정의하여 GUIX 라이브러리 런타임 jpeg 및 png 소프트웨어 디코더 지원을 제거할 수 있습니다. 애플리케이션이 Studio에서 생성된 RAW 형식 pixelmap을 사용하지 않고 외부 파일 시스템에서 이미지 파일을 읽어오지 않아 애플리케이션에서 jpg 또는 png 파일의 런타임 디코드를 요구하지 않는 경우에는 이 #define을 설정하여 GUIX 라이브러리 공간을 줄일 수 있습니다.

GX_DISABLE_BINARY_RESOURCE_SUPPORT
- 기본값: 정의되지 않음
- 설명: 이 조건부를 사용하여 이진 리소스 데이터 로드에 대한 GUIX 라이브러리 지원을 제거할 수 있습니다. 이진 리소스를 사용하면 GUIX 애플리케이션과 리소스 데이터의 런타임 바인딩을 수행할 수 있습니다. C 소스 코드 형식 리소스 파일만 사용하는 경우 이 조건부를 정의하여 GUIX 라이브러리 공간을 줄일 수 있습니다.

GX_DISABLE_BRUSH_ALPHA_SUPPORT
- 기본값: 정의되지 않음
- 설명: 16bpp 이상의 색 농도로 실행하는 경우 GUIX는 필요에 따라 드로잉 컨텍스트 브러시에서 정의된 알파 값을 사용하여 비원호 그래픽, pixelmap, 글꼴을 그릴 수 있도록 지원합니다. 이 그리기 모드를 지원하면 런타임 오버헤드와 라이브러리 공간이 약간 증가합니다. 알파 혼합 그리기 지원이 필요하지 않은 경우 이 플래그를 정의하여 제거할 수 있습니다. 알파 채널, 앤티앨리어싱된 글꼴, 기타 앤티앨리어싱 그리기 모드를 사용하는 pixelmap은 이 조건부 설정에 관계없이 계속 지원됩니다.

GX_DISABLE_THREADX_TIMER_SOURCE
- 기본값: 정의되지 않음
- 설명: 이 조건부를 사용하여 ThreadX 타이머 원본을 사용하지 않도록 설정할 수 있습니다. 다른 타이머 원본을 사용하려면 GX_DISABLE_THREADX_TIMER_SOURCE를 정의해야 합니다.

GX_REPEAT_BUTTON_INITIAL_TICS
- 기본값은 10입니다.
- 설명: 단추에 GX_STYLE_BUTTON_REPEAT 스타일이 있는 경우 이 값은 GX_EVENT_CLICKED 반복 이벤트 전송을 시작하기 전에 단추가 대기하는 기간을 정의합니다.

GX_MAX_QUEUE_EVENTS
- 기본값: 48
- 설명: GUIX 이벤트 큐의 크기를 이벤트 구조 항목 단위로 정의합니다. 이벤트 큐가 오버플로되면 큐에 푸시되는 이벤트는 무시되고 gx_system_event_send() 함수에서 GX_SYSTEM_ERROR가 반환됩니다.

GX_MAX_DIRTY_AREAS
- 기본값: 64
- 설명: 한 캔버스에서 유지 관리할 수 있는 고유한 더티 목록 항목의 최대 개수를 정의합니다. 더티 목록이 오버플로되면 GUIX는 기본적으로 캔버스 루트 창을 더티로 표시합니다. 이는 개별 자식 위젯을 그리는 것보다 효율성이 낮습니다.

GX_MAX_CONTEXT_NESTING
- 기본값: 8
- 설명: 드로잉 컨텍스트 스택의 최대 중첩을 정의합니다. UI 정의 내 부모/자식/자식/자식 위젯의 최대 중첩에 해당합니다.

GX_MAX_INPUT_CAPTURE_NESTING
- 기본값: 4
- 설명: 사용자 입력(마우스 및 키보드)을 캡처하는 위젯 목록을 유지 관리하는 데 사용되는 스택의 크기를 정의합니다.

GX_SYSTEM_THREAD_PRIORITY
- 기본값: 16
- 설명: gx_system_initialize() 중에 생성된 GUIX 스레드의 우선 순위를 정의합니다.

GX_SYSTEM_THREAD_TIMESLICE
- 기본값은 10입니다.
- 설명: RTOS 타이머 틱을 기준으로 GUIX 스레드 시간 조각을 정의합니다. 다른 스레드가 GUIX 스레드와 동일한 우선 순위로 정의된 경우 이 값은 경쟁 스레드에 CPU 제어를 부여하는 빈도를 결정합니다.

GX_CURSOR_BLINK_INTERVAL
- 기본값: 20.
- 설명: 텍스트 입력 위젯의 입력 커서가 깜박이는 속도를 정의합니다. 이 값은 기본적으로 50ms로 정의되는 GUIX 타이머 틱을 기준으로 하므로 값 20은 입력 커서가 초당 한 번 깜박이는 것을 나타냅니다.

GX_MULTI_LINE_INDEX_CACHE_SIZE
- 기본값: 32
- 설명: 여러 줄 텍스트 보기 및 여러 줄 텍스트 입력 위젯에서 유지 관리되는 목록 시작 인덱스 캐시의 크기를 정의합니다. 이 캐시를 사용하여 여러 줄 텍스트 위젯을 빠르게 세로로 스크롤할 수 있습니다. 최상의 성능을 얻으려면 캐시 크기를 애플리케이션에서 정의된 가장 큰 여러 줄 텍스트 위젯의 표시 행 수보다 크게 설정해야 합니다. 예를 들어 텍스트 위젯의 최대 표시 행 수가 20개 행이면 애플리케이션에서 캐시 크기를 32(기본값)로 정의할 수 있습니다. 이렇게 하면 GUIX에서 모든 줄 시작 인덱스를 다시 계산하지 않고도 세로로 스크롤할 수 있습니다.

GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES
- 기본값: 4
- 설명: 여러 줄 텍스트 단추 제어 블록은 단추에 표시되는 각 텍스트 줄에 대한 포인터를 유지 관리합니다. 이 값은 최악의 경우 여러 줄 텍스트 단추에 필요한 텍스트 포인터 수를 결정합니다.

GX_POLYGON_MAX_EDGE_NUM
- 기본값은 10입니다.
- 설명: 이 값은 GUIX에서 그릴 수 있는 가장 복잡한 다각형을 결정합니다. 다각형 그리기 알고리즘에 따라 다각형 가장자리를 정의하는 데 필요한 선이 결정되며, 이 정의는 지원할 수 있는 최대 가장자리 수를 설정합니다.

GX_NUMERIC_SCROLL_WHEEL_STRING_BUFFER_SIZE
- 기본값: 16
- 설명: 숫자 스크롤 휠의 경우 스크롤 휠 위젯이 정수 값을 ASCII 문자열로 변환합니다. 이 값은 할당된 정수 값을 표시하는 데 필요한 문자열의 최대 길이를 결정합니다.

GX_DEFAULT_CIRCULAR_GAUGE_ANIMATION_DELAY
- 기본값: 5
- 설명: 마지막 각도 위치와 현재 각도 위치 사이의 바늘 이동에 애니메이션 효과를 적용하도록 구성된 원형 계기의 업데이트 간 GUIX 타이머 틱(50ms) 수를 정의합니다.

GX_NUMERIC_PROMPT_BUFFER_SIZE
- 기본값: 16
- 설명: 숫자 프롬프트는 프롬프트에 할당된 정수 값을 ASCII 문자열로 변환하기 위해 버퍼를 할당합니다. 이 정의는 문자 버퍼의 크기를 설정합니다.

GX_ANIMATION_POOL_SIZE
- 기본값: 6
- 설명: GUIX는 gx_system_animation_get 및 gx_system_animation_free() API를 사용하여 애니메이션 정보 구조를 동적으로 할당하고 반환할 수 있는 애니메이션 풀을 정의합니다. 이 정의는 애니메이션 제어 블록 풀의 크기를 설정합니다.

GX_MOUSE_SUPPORT
- 기본값: 정의되지 않음
- 설명: 이 정의를 통해 마우스 입력을 지원할 수 있습니다. 소프트웨어 마우스를 사용하려면 디스플레이 드라이버에서 마우스 커서를 그리거나 추적해야 하므로 디스플레이 드라이버에 오버헤드가 추가됩니다. 이 정의는 터치 스크린이 아닌 마우스를 지원해야 하는 경우에만 설정해야 합니다.

GX_HARDWARE_MOUSE_SUPPORT
- 기본값: 정의되지 않음
- 설명: 이 정의를 설정하면 GUIX 디스플레이 드라이버에서 하드웨어 마우스 커서 그리기 지원을 활용합니다. 이렇게 하면 마우스 커서 아래의 캔버스 메모리를 캡처하는 데 필요한 메모리가 감소하고 마우스 오버레이 그래프 계층을 지원하는 하드웨어 대상의 시스템 성능이 향상됩니다.

GX_FONT_KERNING_SUPPORT
- 기본값: 정의되지 않음
- 설명: 이 정의를 설정하면 글꼴 커닝 지원을 사용할 수 있습니다. 글꼴 커닝은 특정 문자 모양 조합의 문자 모양 간격을 향상시킵니다. 이 지원으로 인해 런타임 문자열 그리기 함수에 약간의 오버헤드가 추가되고 글꼴 데이터 구조의 크기도 약간 증가합니다.

GX_WIDGET_USER_DATA
- 기본값: 정의되지 않음
- 설명: 이 정의를 설정하면 사용자 정의 데이터 필드가 GX_WIDGET 제어 블록에 추가됩니다. GUIX Studio 내에서 속성 뷰를 사용하여 이 데이터 필드를 할당할 수 있습니다. 이 데이터 필드는 내부적으로 GUIX에서 무시되지만 애플리케이션 소프트웨어에서 다양한 용도로 사용될 수 있습니다.

GUIX_5_4_0_COMPATIBILITY
- 기본값: 정의되지 않음
- 설명: 특정 GUI API는 사용할 수 없는 텍스트 색에 대한 지원을 추가하고 고정 소수점 일치 매개 변수를 사용하여 특정 수학 함수의 정확도를 높이기 위해 릴리스 5.4.0 이후 수정되었습니다. 이 변경 내용으로 인해 5.4.0 이후의 GUIX 라이브러리 릴리스는 이전 릴리스와 호환되지 않습니다. 그러나 이 #define을 설정하면 API가 5.4.0 및 아전 릴리스와 완전히 호환되도록 라이브러리를 빌드할 수 있으므로 최신 GUIX 라이브러리 릴리스로 컴파일하기 위해 기존 애플리케이션을 변경할 필요가 없습니다.

GX_MAX_STRING_LENGTH
- 기본값: 102400
- 설명: 잘못된 문자열을 테스트하는 데 사용되는 문자열의 최대 길이를 정의합니다. 최대 문자열 길이를 초과하는 입력 문자열은 잘못된 것으로 간주됩니다.