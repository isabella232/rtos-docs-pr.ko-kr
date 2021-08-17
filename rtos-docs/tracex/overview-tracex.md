---
title: Azure RTOS TraceX 이해
description: Azure RTOS TraceX는 시스템 개발자에게 실시간 시스템 이벤트에 대한 그래픽 보기를 제공하고, 실시간 시스템의 동작을 시각화하여 더 잘 이해할 수 있도록 하는 Microsoft 호스트 기반 분석 도구입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 966f3be5ebe34e006067175e422480fbf1ab664bb0ff627d7b01e71036dc5e82
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792183"
---
# <a name="overview-of-azure-rtos-tracex"></a>Azure RTOS TraceX 개요

Azure RTOS TraceX는 시스템 개발자에게 실시간 시스템 이벤트에 대한 그래픽 보기를 제공하고, 실시간 시스템의 동작을 시각화하여 더 잘 이해할 수 있도록 하는 Microsoft 호스트 기반 분석 도구입니다. 개발자는 Azure RTOS TraceX를 사용하여 표준 디버깅 도구로 포착하지 못하는 인터럽트 및 컨텍스트 전환 같은 시스템 이벤트의 발생을 명확하게 확인할 수 있습니다. 이러한 이벤트를 식별 및 연구하고 전반적인 시스템 작업의 컨텍스트에서 이벤트가 발생하는 시간을 정확하게 파악하는 기능을 통해 개발자는 예기치 않은 동작을 찾아 특정 영역을 조사하여 프로그래밍 문제를 해결할 수 있습니다. 추적 정보는 런타임 시 애플리케이션에 의해 결정된 버퍼 위치와 크기를 사용하여 대상 시스템의 버퍼에 저장됩니다. Azure RTOS TraceX는 Azure RTOS ThreadX뿐만 아니라 모든 애플리케이션 또는 RTOS에서 적절한 방식으로 생성된 버퍼를 처리할 수 있습니다. 추적 정보는 분석을 위해 언제든지(사후 또는 중단 시) 호스트로 업로드할 수 있습니다. Azure RTOS ThreadX는 시스템 오작동 또는 기타 중요한 이벤트 발생 시 최근의 "N"개 이벤트를 검사할 수 있도록 하는 순환 버퍼를 구현합니다.

![Azure RTOS TraceX Single-Core 표시](./media/user-guide/screen_shot_33.png)

**TraceX Single-Core 표시**

## <a name="key-capabilites"></a>주요 기능

### <a name="azure-rtos-tracex-built-in-system-analysis"></a>Azure RTOS TraceX 기본 제공 시스템 분석

Azure RTOS TraceX는 TraceX 도구 모음에서 단일 단추 클릭을 통해 사용할 수 있는 기본 제공 시스템 분석 보고서를 제공합니다. 이러한 단추와 보고서에는 다음이 포함됩니다.

![실행 프로필 생성 보고서](./media/overview-tracex/execution-profile-report-button.jpg) 실행 프로필 생성 보고서

![성능 통계 생성 보고서](./media/overview-tracex/performance-statistics-report-button.jpg) 성능 통계 생성 보고서

![스레드 스택 사용량 생성 보고서](./media/overview-tracex/thread-stack-usage-report-button.jpg) 스레드 스택 사용량 생성 보고서

### <a name="trace-data-collected-by-azure-rtos-threadx"></a>Azure RTOS ThreadX에서 수집된 추적 데이터

Azure RTOS TraceX는 런타임 중에 대상 시스템에서 시스템 및 애플리케이션 "이벤트"의 데이터베이스를 생성하는 Azure RTOS ThreadX에서 작동하도록 설계되었습니다. 이러한 이벤트는 다음과 같습니다.

* 스레드 컨텍스트 전환
* 선점
* 일시 중단
* 종료
* 시스템 인터럽트
* 애플리케이션별 이벤트
* 모든 Azure RTOS ThreadX API 호출
* 모든 Azure RTOS NetX API 호출
* 모든 Azure RTOS FileX API 호출
* 모든 Azure RTOS USBX API 호출
* 애플리케이션 정의 아이콘 및 정보

이벤트는 타임스탬프 및 활성 스레드 ID를 사용하여 프로그램 제어를 통해 기록되므로 나중에 적절한 시간 순서로 표시하고 적절한 스레드와 연결할 수 있습니다. 이벤트 로깅은 애플리케이션에서 동적으로 중지한 후 다시 시작할 수 있습니다(예: 관심 영역이 있는 경우). 이렇게 하면 시스템이 제대로 수행될 때 데이터베이스가 복잡해지지 않도록 하고 대상 메모리를 최대로 사용하는 것을 방지할 수 있습니다.

### <a name="azure-rtos-tracex-is-like-a-software-logic-analyzer"></a>Azure RTOS TraceX는 소프트웨어 논리 분석기와 비슷합니다.

이벤트 로그가 대상 메모리에서 호스트로 업로드되면 Azure RTOS TraceX는 이벤트가 세로 축을 따라 나열된 다양한 애플리케이션 스레드 및 시스템 루틴을 사용하여 시간을 나타내는 가로 축에 그래픽으로 이벤트를 표시합니다. Azure RTOS TraceX는 호스트에서 "소프트웨어 논리 분석기"를 만들어 시스템 이벤트를 명확하게 표시합니다. 이벤트는 관련 스레드 또는 시스템 루틴의 오른쪽에 가로 시간 표시줄을 따라 발생 지점에 위치한 색으로 구분된 아이콘으로 표시됩니다. 이벤트 아이콘을 선택하면 해당 이벤트에 대한 정보가 두 개의 이전 이벤트 및 두 개의 후속 이벤트에 대한 정보와 함께 표시됩니다. 이를 통해 이벤트 및 그 주변의 이벤트와 관련한 가장 즉각적인 정보에 단일 클릭으로 빠르게 액세스할 수 있습니다. Azure RTOS TraceX는 단일 가로선에 모든 시스템 이벤트를 표시하는 "요약" 표시를 제공하여 많은 스레드를 포함하는 시스템의 분석을 간소화합니다.

### <a name="sequential-view-mode"></a>순차 보기 모드

"순차 보기" 탭을 클릭하여 순차 보기 모드를 선택하며 이것이 기본 모드입니다. 이 모드에서는 이벤트 사이에 경과된 시간에 관계 없이 이벤트가 바로 다음에 표시됩니다. 표시 영역 위에 있는 눈금자도 확인합니다. 여기에는 추적 시작을 기준으로 상대 이벤트 번호가 표시됩니다. 이 모드는 기본 모드이며, 시스템에서 진행되는 상황에 적절한 개요를 얻는 데 특히 유용합니다.

![순차 보기 모드](./media/user-guide/screen_shot_10.png)

**순차 보기 모드**

### <a name="time-view-mode"></a>시간 보기 모드

이 모드에서는 이벤트가 상대 시간 방식으로 표시되며, 녹색 막대가 이벤트 간의 실행을 표시하는 데 사용됩니다. 이 모드는 시스템에서 대량 처리가 수행되는 위치를 확인하는 데 특히 유용하며, 개발자가 성능 및/또는 응답성을 높이기 위해 시스템을 조정하는 데 도움이 될 수 있습니다.

이벤트 표시 위에 있는 눈금자도 확인합니다. 이 눈금자는 Azure RTOS ThreadX 내부의 이벤트 추적 로깅에서 계측된 타임스탬프에서 파생된 추적 시작을 기준으로 상대 틱 수를 표시합니다. 타임스탬프가 너무 가까이 있으면(빈도가 낮은 타이머) 이벤트가 동시에 실행됩니다. 반대로 타임스탬프가 너무 멀리 떨어져 있으면(빈도가 높은 타이머) 이벤트가 너무 멀리 떨어지게 됩니다. 올바른 빈도 타임스탬프를 선택하는 것은 상대 시간 보기를 의미 있게 만드는 데 중요한 고려 사항입니다.

![시간 보기 모드](./media/user-guide/screen_shot_31.png)

### <a name="system-summary-line"></a>시스템 요약 줄

Azure RTOS TraceX는 동일한 줄의 모든 이벤트가 포함된 단일 요약 줄도 제공합니다. 요약 줄에는 컨텍스트 요약이 포함되어 있고 그 아래에는 해당 이벤트 요약이 포함되어 있습니다. 이를 통해 복잡한 시스템의 개요를 쉽게 확인할 수 있습니다. 요약 표시줄은 스레드가 많은 시스템에서 특히 유용합니다. 이러한 요약 줄이 없는 경우 사용자는 실행 컨텍스트를 따라 세로 스크롤 막대를 사용하여 복잡한 시스템 상호 작용을 수행해야 합니다.

Azure RTOS TraceX는 시스템 컨텍스트를 표시 왼쪽에 나열합니다.
특정 컨텍스트에서 발생하는 이벤트는 해당 컨텍스트의 오른쪽에 있는 가로줄에 표시됩니다. 이렇게 하면 이벤트가 발생한 컨텍스트를 쉽게 확인할 수 있을 뿐만 아니라 해당 컨텍스트 줄을 따라 특정 컨텍스트에서 발생한 모든 이벤트를 확인할 수도 있습니다.

![시스템 요약 줄](./media/user-guide/screen_shot_32.png)

**시스템 요약 줄**

처음 두 컨텍스트 항목은 항상 “인터럽트” 및 “초기화/유휴” 컨텍스트입니다. “인터럽트” 컨텍스트는 ISR(인터럽트 서비스 루틴)에서 생성된 모든 시스템 이벤트를 나타냅니다. “초기화/유휴” 컨텍스트는 Azure RTOS ThreadX의 두 가지 컨텍스트를 나타냅니다. tx_application_define을 수행하는 중에 발생하는 이벤트는 "초기화" 이벤트이며 "초기화/유휴" 컨텍스트에 표시됩니다. 시스템이 유휴 상태이고 이로 인해 이벤트가 발생하지 않는 경우 시간 보기에서 “실행 중”을 나타내는 녹색 막대가 “초기화/유휴” 컨텍스트에 표시됩니다.

## <a name="methods-of-navigation"></a>탐색 방법

개발자는 Azure RTOS TraceX를 사용하여 "다음" 및 "이전" 탐색 단추가 작동하는 방식을 지정할 수 있습니다.

![탐색 단추](./media/user-guide/event.png)

“이벤트”를 선택하면 다음/이전 이벤트에 대한 탐색이 수행됩니다. “컨텍스트”를 선택하면 동일한 컨텍스트의 다음/이전 이벤트에 대한 탐색이 수행됩니다. “개체”를 선택하면 현재 개체의 다음/이전 이벤트(예: 특정 큐와 연결된 이벤트)에 대한 탐색이 수행됩니다. “스위치”를 선택하면 다음/이전 컨텍스트 전환에 대한 탐색이 수행됩니다. “동일한 ID”를 선택하면 동일한 이벤트 ID의 다음/이전 이벤트에 대한 탐색이 수행됩니다.

### <a name="event-information-display"></a>이벤트 정보 표시

Azure RTOS TraceX는 300개 이벤트에 대한 자세한 정보를 제공합니다. 여기에는 6개의 내부 Azure RTOS ThreadX 이벤트, 2개의 ISR 이벤트(enter 및 exit), 14개의 내부 Azure RTOS FileX 이벤트, 42개의 내부 Azure RTOS NetX 이벤트, 1개의 사용자 정의 이벤트가 포함됩니다. 나머지 이벤트는 Azure RTOS ThreadX, Azure RTOS FileX 및 Azure RTOS NetX API 서비스에 직접 대응됩니다.
순차 또는 시간 표시 모드의 선택 여부에 관계 없이 마우스를 표시 영역의 이벤트 위에 놓으면 이벤트 근처에 자세한 이벤트 정보가 표시됩니다. 여기서는 마우스를 데모 demo_threadx.trx 추적 파일의 이벤트 494 위에 놓았습니다.

![마우스를 위에 놓을 때 표시되는 추가 정보](./media/user-guide/screen_shot_37.png)

**마우스를 위에 놓을 때 표시되는 추가 정보**

표시되는 각 이벤트에는 컨텍스트, 상대 시간 및 타임스탬프에 대한 표준 정보가 모두 포함됩니다. 컨텍스트 필드에는 이벤트가 발생한 컨텍스트가 표시됩니다. 정확히 스레드, 유휴, ISR 및 초기화의 4가지 컨텍스트가 있습니다. 스레드 컨텍스트에서 이벤트가 발생하면 스레드의 이름과 우선 순위가 해당 시간에 수집되어 위와 같이 표시됩니다. 상대 시간에는 추적 시작 시점을 기준으로 상대 타이머 틱 수가 표시됩니다. 원시 타임스탬프에는 이벤트의 원시 시간 원본이 표시됩니다. 마지막으로 모든 이벤트 관련 정보가 표시됩니다.

### <a name="zooming-in-and-out"></a>확대 및 축소

기본적으로 Azure RTOS TraceX는 1:1 픽셀 대 틱 매핑을 사용하여 보기 쉬운 크기로 이벤트를 표시합니다. 사용자가 원하는 대로 확대하거나 축소할 수 있습니다. 100%로 축소는 현재 표시 보기에서 전체 추적을 확인하는 데 유용합니다. 확대는 타임스탬프 원본의 해상도로 인해 이벤트가 겹치는 상태에서 유용합니다.

![100% 보기로 축소 또는 확대하여 세부 정보 보기](./media/user-guide/screen_shot_41.png)

**100% 보기로 축소 또는 확대하여 세부 정보 보기**

100%로 축소하여 현재 표시 페이지 내의 전체 추적을 표시하면 추적에서 캡처된 모든 컨텍스트 실행과 해당 컨텍스트 내에서 발생하는 일반 이벤트를 쉽게 확인할 수 있습니다. “스레드 1” 및 “스레드 2”가 가장 자주 실행되었습니다. 또한 해당 이벤트에 대해 지정한 파란색은 이러한 스레드에서 큐 서비스 호출을 수행하고 있음을 나타냅니다(큐 이벤트는 파란색임).

전체 아이콘 보기로 복원하는 것도 마찬가지로 쉽습니다. 확대 단추를 반복적으로 선택하거나 일부 비율을 100으로 입력할 수 있습니다.

### <a name="delta-ticks-between-events"></a>이벤트 간 델타 틱 수

다양한 이벤트 간의 틱 수는 Azure RTOS TraceX에서 쉽게 확인할 수 있습니다. 시작 이벤트를 클릭하고 마우스를 끝 이벤트로 끌면 됩니다.
이벤트 간의 델타 틱 수는 표시의 오른쪽 위 모서리에 표시됩니다.

![델타 틱](./media/user-guide/screen_shot_42.png)

**델타 틱**

델타 틱 수는 이벤트 494와 이벤트 496 사이에서 5,032개 틱이 경과했음을 보여 줍니다. 이는 각 이벤트의 상대 타임스탬프를 확인하고 뺄셈을 수행하여 수동으로 계산할 수도 있지만 GUI를 사용하는 것이 쉽고 즉각적입니다.

### <a name="priority-inversions"></a>우선 순위 반전

Azure RTOS TraceX는 추적 파일에서 검색된 우선 순위 반전을 자동으로 표시합니다. 우선 순위 반전은 우선 순위가 낮은 스레드에서 현재 소유하고 있는 뮤텍스를 얻으려고 시도하는 우선 순위가 높은 스레드가 차단되는 조건으로 정의됩니다. 시스템이 이 방식으로 작동하도록 설정되었으므로 이 조건을 “결정적”이라고 합니다. 사용자에게 알리기 위해 Azure RTOS TraceX는 “결정적” 우선 순위 반전 범위를 연한 연어 색으로 표시합니다.

Azure RTOS TraceX는 “비결정적” 우선 순위 반전도 표시합니다. 이러한 우선 순위 반전은 다른 우선 순위 수준의 다른 스레드가 “결정적” 우선 순위 반전의 중간에 실행되었다는 점에서 “결정적” 우선 순위 반전과 다릅니다. 따라서 우선 순위 반전 내의 시간은 다소 “비결정적”입니다. 이 조건은 사용자가 알 수 없는 경우가 많으며 매우 심각할 수 있습니다. 사용자에게 이 조건을 경고하기 위해 Azure RTOS TraceX는 “비결정적” 우선 순위 반전을 더 밝은 연어 색으로 표시합니다.

![결정적 및 비결정적 우선 순위 반전](./media/user-guide/screen_shot_43.png)

**결정적 및 비결정적 우선 순위 반전**

### <a name="execution-profile"></a>실행 프로필

Azure RTOS TraceX는 현재 로드된 추적 파일 내의 모든 실행 컨텍스트에 대한 기본 제공 실행 프로필 보고서를 제공합니다.

![실행 프로필](./media/user-guide/execution_profile.png)

### <a name="performance-statistics"></a>Performance statistics

Azure RTOS TraceX는 현재 로드된 추적 파일에 대한 기본 제공 성능 통계 보고서를 제공합니다.

![Performance statistics](./media/user-guide/performance_statistics.png)

### <a name="thread-stack-usage"></a>스레드 스택 사용

Azure RTOS TraceX는 현재 로드된 추적 파일 내에서 실행 중인 모든 스레드에 대한 기본 제공 스택 사용 보고서를 제공합니다.

![스택 사용](./media/user-guide/thread_stack_usage.png)

Azure RTOS TraceX는 현재 로드된 추적 파일의 Azure RTOS FileX 성능 통계를 표시합니다. 이 정보는 모든 열린 미디어 개체에서 전체 시스템에 대해 표시됩니다.

![FileX 통계](./media/user-guide/filex_statistics.png)

### <a name="azure-rtos-netx-statistics"></a>Azure RTOS NetX 통계

또한 Azure RTOS TraceX는 현재 로드된 추적 파일의 NetX 성능 통계도 표시합니다. 이 정보는 전체 시스템에 대해 표시됩니다.

![NetX 통계](./media/user-guide/netx_statistics.png)

### <a name="raw-trace-dump"></a>원시 추적 덤프

Azure RTOS TraceX는 원시 추적 파일을 텍스트 형식으로 작성하고 메모장을 시작하여 표시할 수 있습니다.

![원시 추적 덤프](./media/user-guide/raw_trace_dump.png)

나열된 모든 타이밍 및 크기 수치는 예상치이며, 개발 플랫폼에 따라 다를 수 있습니다.
