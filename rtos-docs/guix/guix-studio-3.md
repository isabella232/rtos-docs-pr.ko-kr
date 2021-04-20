---
title: GUIX Studio 설명
description: 이 챕터에서는 GUIX Studio 시스템 분석 도구에 대한 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 89bbcd51c22dddef6e420750e8c8805a66344335
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811185"
---
# <a name="chapter-3-description-of-guix-studio"></a>챕터 3: GUIX Studio 설명

이 챕터에서는 GUIX Studio 시스템 분석 도구에 대한 설명이 포함되어 있습니다. GUI의 전체 기능에 대한 설명을 이 챕터에서 확인할 수 있습니다. 

## <a name="guix-studio-views"></a>GUIX Studio 보기

GUIX Studio UI에는 ***도구 모음** _, _*_프로젝트 보기_*_, _*_속성 보기_*_, _*_대상 보기_*_, _*_리소스 보기_*_ , 이상 5가지 주요 영역이 있습니다. _ *_그림 2_**는 기본 GUIX Studio UI를 보여줍니다. 각각의 보기는 이후 하위 섹션에서 추가로 설명합니다.

![기본 GUIX Studio UI 스크린샷.](./media/guix-studio/image_10.png)

**그림 2**

### <a name="title"></a>제목

- GUIX Studio 18: 앞서 _ *_그림 2_**의 상단에 표시된 것과 같이 ***제목** _에는 GUIX Studio 버전과 현재 열린 프로젝트가 표시됩니다.

### <a name="toolbar"></a>도구 모음

***도구 모음** _은 _*_그림 3_**과 같이 GUIX Studio 개발자가 사용 가능한 단추가 표시됩니다.

![GUIX Studio 도구 모음 스크린샷.](./media/guix-studio/image11.jpg)

**그림 3**

도구 모음 단추는 다음과 같이 정의됩니다.

![새 단추](./media/guix-studio/new-button.png) 새 GUIX Studio 프로젝트를 만듭니다.

![열기 단추](./media/guix-studio/open-button.png) 기존 GUIX Studio 프로젝트를 엽니다.

![저장 단추](./media/guix-studio/save-button.png) 프로젝트를 저장합니다.

![잘라내기 단추](./media/guix-studio/cut-button.png) 자식 요소를 포함하여 선택한 위젯을 잘라냅니다.

![복사 단추](./media/guix-studio/copy-button.png) 자식 요소를 포함하여 선택한 위젯을 복사합니다.

![붙여넣기 단추](./media/guix-studio/paste-button.png) 위젯과 자식 요소를 붙여넣습니다.

![왼쪽 맞춤 단추](./media/guix-studio/left-align-button.png) 선택한 위젯을 왼쪽에 맞춥니다.

![오른쪽 맞춤 단추](./media/guix-studio/right-align-button.png) 선택한 위젯을 오른쪽에 맞춥니다.

![위쪽 맞춤 단추](./media/guix-studio/top-align-button.png) 선택한 위젯을 위쪽에 맞춥니다.

![아래쪽 맞춤 단추](./media/guix-studio/bottom-align-button.png) 선택한 위젯을 아래쪽에 맞춥니다.

![세로로 띄우기 단추](./media/guix-studio/space-vertically-button.png) 선택한 위젯을 세로로 동일한 간격으로 띄웁니다.

![가로로 띄우기 단추](./media/guix-studio/space-horizontally-button.png) 선택한 위젯을 가로로 동일한 간격으로 띄웁니다.

![동일 너비 단추](./media/guix-studio/equal-width-button.png) 선택한 위젯을 동일한 너비로 설정합니다.

![동일 높이 단추](./media/guix-studio/equal-height-button.png) 선택한 위젯을 동일한 높이로 설정합니다.

![앞으로 이동 단추](./media/guix-studio/move-front-button.png) 선택한 위젯을 앞으로 이동합니다.

![뒤로 이동 단추](./media/guix-studio/move-back-button.png) 선택한 위젯을 뒤로 이동합니다.

![크기 조정 단추](./media/guix-studio/size-button.png) 선택한 위젯의 크기를 콘텐츠 축소 대상 화면에 맞춰 조정합니다.

![축소 단추](./media/guix-studio/zoom-out-button.png) 대상 화면을 축소합니다.

![확대 단추](./media/guix-studio/zoom-in-button.png) 대상 화면을 확대합니다.

![기록 단추](./media/guix-studio/record-button.png) 매크로를 기록합니다.

![재생 단추](./media/guix-studio/playback-button.png) 매크로를 재생합니다.

![실행 단추](./media/guix-studio/run-button.png) 애플리케이션을 실행합니다.

![정보 단추](./media/guix-studio/about-button.png) GUIX Studio 정보

### <a name="project-view"></a>프로젝트 보기

***프로젝트 보기** _에는 포함된 UI를 구성하는 계층적 목록 GUIX 개체가 표시됩니다. 부모 개체를 클릭하고 _*_삽입_*_ 메뉴에서 개체를 선택(또는 개체를 마우스 오른쪽 단추로 클릭하고 표시되는 메뉴에서 선택)하여 새 GUIX 개체를 추가할 수 있습니다. 아래 _*_그림 4_*_ 는 GUIX Studio _*_프로젝트 보기_**를 보여줍니다.

![GUIX Studio 프로젝트 보기 스크린샷.](./media/guix-studio/image_35.png)

**그림 4**

### <a name="properties-view"></a>속성 보기

***속성 보기** _에는 현재 선택한 GUIX 개체에 대한 자세한 속성 정보가 표시됩니다. 개체는 _*_프로젝트 보기_*_ 를 통해 선택하거나 _*_대상 보기_*_ 에서 개체를 직접 클릭하여 선택할 수 있습니다. 아래 _*_그림 5_*_ 는 GUIX Studio _*_속성 보기_**를 보여줍니다.

![GUIX Studio 속성 보기 스크린샷.](./media/guix-studio/image36.jpg)

**그림 5**

### <a name="target-view"></a>대상 보기

***대상 보기** _는 WYSIWYG 화면 디자인 및 레이아웃 영역입니다. 이 보기는 대상 하드웨어에서 사용할 수 있는 물리적 디스플레이를 나타냅니다. 간편한 마우스 작업을 통해 개체를 선택, 이동, 크기 조정할 수 있습니다. 또한 대상 보기의 선택한 개체에서 조정 및 Z 순서 단추가 제공됩니다. _*_대상 보기_*_ 에서 개체를 선택하면 _*_속성 보기_*_ 에서 해당 개체의 속성이 표시됩니다. 아래 _*_그림 6_*_ 은 GUIX Studio _*_대상 보기_**를 보여줍니다.

![GUIX Studio 대상 보기 스크린샷.](./media/guix-studio/image_37.png)

**그림 6**

### <a name="resource-view"></a>리소스 뷰

***리소스 보기** _는 각 디스플레이에 정의되는 애플리케이션 화면에 제공되는 리소스(색, 글꼴, pixelmap, 문자열)를 관리하는 데 사용됩니다. 리소스 보기 그룹 헤더를 클릭하여 각 그룹을 확장하고 그룹 콘텐츠를 검토할 수 있습니다. 아래 _*_그림 7_*_ 은 GUIX Studio _*_리소스 보기_**를 보여줍니다.

![GUIX Studio 리소스 보기 스크린샷.](./media/guix-studio/image38.jpg)

**그림 7**

리소스 그룹의 제목은 현재 테마 이름을 나타냅니다. 여러 테마가 제공되는 경우 위쪽 및 아래쪽 화살표를 클릭하여 테마를 전환할 수 있습니다.

위의 보기에서 각 리소스 그룹은 그룹 헤더를 클릭하여 확장하거나 축소할 수 있습니다. 각 리소스 그룹에 대한 자세한 설명은 다음 챕터에 있습니다.

## <a name="the-guix-studio-project"></a>GUIX Studio 프로젝트

GUIX Studio 프로젝트는 UI 화면 디자인 및 UI 리소스에 대한 정보를 유지 관리합니다. 프로젝트 데이터는 ".***gxp***" 확장자의 XML 서식 파일에 저장됩니다. 프로젝트 파일은 XML 스키마 파일이므로 다른 모든 원본 파일과 비슷하게 버전 관리 제어 및 공유될 수 있습니다.

GUIX Studio를 처음 사용하는 경우 배포와 함께 제공된 예제 프로젝트 중 하나를 열거나 새 프로젝트를 만들어야 합니다. 모든 작업은 프로젝트 데이터 파일에 저장됩니다.

GUIX Studio는 ANSI C 원본 파일 또한 생성합니다. 이러한 원본 파일에는 애플리케이션 리소스 또는 디자인된 화면을 설명하는 데이터 구조가 포함되어 있습니다. GUIX Studio는 생성된 데이터 구조를 활용하여 애플리케이션 화면을 동적으로 만드는 것을 알고 있는 생성된 원본 파일 API 함수에도 이를 씁니다. 애플리케이션 소프트웨어는 제공된 API 함수를 호출하여 GUIX Studio 내에서 디자인한 화면을 만듭니다.

사용자 인터페이스를 디자인하는 과정에서 GUIX Studio를 사용하여 디자인한 인터페이스를 빌드하고 실행할 수 있도록 하는 GUIX 호환 출력 파일을 정기적으로 생성하고자 할 것입니다. 대상 하드웨어 또는 ThreadX 및 GUIX를 시뮬레이션하는 Windows 데스크톱에서 생성된 소스 파일을 컴파일 및 실행할 수 있습니다.

## <a name="guix-studio-project-organization"></a>GUIX Studio 프로젝트 구성

GUIX Studio를 효과적으로 사용하는 방법을 이해하고 GUIX Studio IDE의 프로젝트 보기에 제공되는 정보를 이해하는 데 있어 GUIX Studio 프로젝트의 기본 구성을 아는 것이 도움이 됩니다. 프로젝트 보기는 프로젝트에 포함된 모든 정보의 요약을 시각적으로 제공합니다.

프로젝트를 설명하기 전에 몇 가지 용어를 정의해야 합니다. 우선 **디스플레이** 라는 용어는 물리적 디스플레이 디바이스를 의미합니다. 대체로 LCD 디스플레이 디바이스를 사용하지만 다른 기술을 사용할 수 있습니다. 다음 용어는 **화면** 으로, 최상위 GUIX 개체(일반적으로 GUIX 창) 및 연결된 모든 자식 요소를 의미합니다. 화면은 런타임에서 정의 및 수정할 수 있는 소프트웨어 구문입니다. 마지막으로 **테마** 는 리소스의 컬렉션입니다. 테마에는 조화롭고 최종 사용자에게 일관적인 외관을 제공하도록 디자인된 색 정의, 글꼴 정의 및 pixelmap 정의 표가 포함되어 있습니다.

프로젝트에는 프로젝트 이름, 지원되는 디스플레이의 수, 각 디스플레이의 해상도 및 색 형식, 지원되는 언어의 수, 지원되는 각 언어의 이름 등 전역 정보 세트가 포함되어 있습니다. 프로젝트 이름은 프로젝트 보기에 표시되는 첫 번째 노드입니다.

이후 프로젝트는 최대 4개의 물리적 디스플레이에 필요한 모든 정보와 각 디스플레이에 사용할 수 있는 화면과 리소스를 구성합니다. 디스플레이 이름은 프로젝트 보기 트리의 다음 수준 노드입니다.

GUIX Studio 애플리케이션의 고유한 기능은 각각 고유한 x, y 해상도, 색 형식, 화면 및 리소스를 포함하는 여러 물리적 디스플레이를 기본적으로 지원하는 것입니다. 대다수의 GUIX 애플리케이션은 하나의 물리적 디스플레이만 활용하지만 이 기능은 여러 개의 동시 물리적 디스플레이를 지원하는 제품을 만드는 데 중요합니다.

각 디스플레이 정의 아래에는 해당 디스플레이에 대해 정의된 최상위 창 또는 화면이 있습니다. 화면 정의는 각 화면에서 자식 위젯의 수와 중첩에 따라 모든 수준으로 중첩될 수 있습니다.

이 화면 및 자식 위젯 구성은 프로젝트 보기에 그래픽 방식으로 표시됩니다.

또한 각 디스플레이와 연결된 테마는 디스플레이에서 지원하는 테마와 각 테마를 구성하는 리소스 콘텐츠입니다. 프로젝트에 여러 디스플레이가 포함된 경우 하나의 디스플레이를 선택하고 다른 디스플레이를 선택하면 리소스 보기의 콘텐츠가 변경되는 것을 알 수 있습니다. 리소스 콘텐츠가 각 디스플레이에 연결되어 있기 때문입니다. 색 형식은 다를 수 있지만, 사용하는 pixelmap, 색, 글꼴은 물리적 디스플레이마다 다를 수 있습니다.

프로젝트에서 유지 관리되는 마지막 구성 요소는 각 디스플레이와 연결된 문자열 테이블 데이터입니다. 디스플레이의 x, y 해상도는 크게 다를 수 있으므로, 문자열 데이터는 프로젝트에 정의된 각 디스플레이에 대해 독립적으로 유지됩니다.
