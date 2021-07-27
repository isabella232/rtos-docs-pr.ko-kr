---
title: Azure RTOS GUIX 및 Azure RTOS GUIX Studio 이해
description: Azure RTOS GUIX는 포함된 시스템 개발자의 요구 사항에 맞게 제작된 전문가용 패키지입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a6ac2c7a76893d516b9beae9b893c9764de60ba
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754933"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a>Azure RTOS GUIX 및 Azure RTOS GUIX Studio 개요

Azure GUIX 내장형 GUI는 심층 내장형, 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 Microsoft의 고급 산업용 GUI 솔루션입니다. 또한 Microsoft는 개발자가 데스크톱에서 GUI를 디자인하고 대상으로 내보낼 수 있는 Azure RTOS GUIX 내장형 GUI 코드를 생성할 수 있는 Azure RTOS GUIX Studio라는 모든 기능을 갖춘 WYSIWYG 데스크톱 디자인 도구를 제공합니다. Azure RTOS GUIX는 Azure RTOS ThreadX RTOS와 완전히 통합되며 Azure RTOS ThreadX에서 지원하는 많은 동일한 프로세서에 사용할 수 있습니다. 또한 Azure RTOS GUIX는 매우 적은 메모리 공간에서 고속 실행과 뛰어난 사용 편의성을 구현하므로, 사용자 인터페이스가 요구되는 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다. 

## <a name="azure-rtos-guix-api"></a>Azure RTOS GUIX API

### <a name="powerful-apis"></a>강력한 API

* 필요할 때 직접 캔버스 그리기 완벽 지원
* Azure RTOS GUIX Studio 생성 코드와 간단하게 상호 작용
* 선, 사각형, 다각형 등을 위한 API
* 원, 호, 원형, 현, 타원 등을 위한 API
* 텍스트 그리기 및 위치 지정을 위한 API
* 앤티앨리어싱, 텍스처 채우기 및 단색 채우기
* 화면과 위젯 생성 및 수정을 위한 API

### <a name="azure-rtos-guix-studio-generated-files"></a>Azure RTOS GUIX Studio 생성 파일

* 자동으로 생성된 ANSI C 원본 파일
* 레이아웃 정보에서 애플리케이션 소프트웨어 분리
* UI 디자인에 필요한 글꼴 및 이미지 포함
* 애플리케이션 코드로 컴파일 및 생성된 파일
* 애플리케이션 논리에 영향을 주지 않고 화면 레이아웃 업데이트 가능
* 리소스 ID에서 언어 및 테마 독립성 만들기
* 사용자가 제공하는 사용자 지정 그리기 및 이벤트 처리 함수

### <a name="widget-library"></a>위젯 라이브러리

* 사전 정의되었지만 사용자 정의 가능한 공통 인터페이스 요소 세트
* 매우 작고 간단하고 효율적
* 라이브러리에 단추, 계기, 목록, 창, 스크롤, 슬라이더, 진행률 표시줄, 프롬프트 등이 포함됨
* 완전히 사용자 지정 가능한 그리기 및 모양
* 완전히 사용자 지정 가능한 작업 및 이벤트 처리
* 사용된 위젯만 애플리케이션 소프트웨어와 연결됨

### <a name="math-and-utilities"></a>수학 및 유틸리티

* 사인, 코사인, 아크사인, 아크코사인, 탄젠트, 제곱근에 대한 함수
* 화면 영역 조작을 위한 함수
* 시스템 구성 및 시작
* 메모리 풀 정의(옵션)
* 타이머 관리
* 애니메이션 관리
* 더티 목록 유지 관리

### <a name="image-processing"></a>이미지 처리

* jpeg 및 png 이미지의 런타임 디코딩을 위한 함수
* 디더링 및 색 공간 변환 적용
* 이미지 회전
* 이미지 크기 조정
* 이미지 혼합

### <a name="event-processing"></a>이벤트 처리

* 유휴 상태일 때 자동으로 Azure RTOS GUIX 스레드 일시 중단
* UI 디자인에 널리 사용되는 이벤트 기반 프로그래밍 모델
* Azure RTOS GUIX 그리기 스레드에서 입력 드라이버 분리
* 이벤트를 보내고 받기 위한 함수
* 모든 Azure RTOS GUIX 위젯 형식에 대한 미리 정의된 이벤트 형식
* 사용자 정의된 사용자 지정 이벤트 지원

### <a name="canvas-processing"></a>캔버스 처리

* 클리핑 및 Z 순서 유지 관리
* 하드웨어 정보에서 위젯 라이브러리 분리
* 하드웨어 정보에서 애플리케이션 분리
* 더티 영역의 자동 백그라운드 새로 고침
* 계층화 및 혼합이 지원되는 여러 캔버스
* 애플리케이션 소프트웨어에서 직접 호출 가능

### <a name="input-device-drivers"></a>입력 디바이스 드라이버

* 하드웨어 관련 지원, 하드웨어 정보에서 Azure RTOS GUIX 및 애플리케이션 분리
* 저항 접촉식 터치, 캡 터치 및 키패드 지원
* Azure RTOS GUIX 이벤트 큐에 입력 이벤트 전달

### <a name="display-drivers"></a>디스플레이 드라이버

* 하드웨어 관련 지원
* 모든 색 농도 및 형식에 대해 제공되는 일반 드라이버
* 사용 가능한 그래픽 가속기를 활용하도록 사용자 지정됨

### <a name="target-hardware"></a>대상 하드웨어

* 그래픽 출력을 지원하는 거의 모든 하드웨어가 GUIX와 호환
* 여러 물리적 디스플레이 지원
* 최소 RAM 및 플래시 요구 사항

## <a name="create-elegant-user-interfaces"></a>세련된 사용자 인터페이스 만들기

Azure RTOS GUIX 및 Azure RTOS GUIX Studio는 세련된 사용자 인터페이스를 만드는 데 필요한 모든 기능을 제공합니다. 표준 Azure RTOS GUIX 패키지에는 의료 기기 참조, 스마트 시계 참조, 가정 자동화 참조, 산업 제어 참조, 자동차 참조, 다양한 스프라이트 및 애니메이션 예제를 비롯한 다양한 샘플 사용자 인터페이스가 포함되어 있습니다. 아래에 표시된 참조 예제를 클릭하세요.

### <a name="home-automation"></a>가정 자동화

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a>의료

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a>소비자

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a>백색 가전

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a>자동차

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a>공업 제품

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

Azure RTOS GUIX 참조마다 참조 디자인의 모든 그래픽 요소를 정의하는 해당 Azure RTOS GUIX Studio 프로젝트가 있습니다. 참조 디자인을 변경하는 것은 쉽습니다. 해당하는 Azure RTOS GUIX 프로젝트를 열고 원하는 대로 변경한 후 프로젝트를 저장하고 *프로젝트* 를 선택하면 됩니다.

모든 출력 파일을 생성하여 Azure RTOS GUIX에 대한 C 코드를 생성합니다. 그런 다음, 대상 애플리케이션을 다시 빌드하고 실행하여 수정된 참조 디자인을 관찰합니다.

### <a name="guix-memory-footprint"></a>GUIX 메모리 공간

Azure RTOS GUIX는 캔버스에 필요한 메모리를 제외하고 기본 지원을 위한 13.2KB의 FLASH 및 4KB RAM의 매우 작은 최소 메모리 공간을 가지고 있습니다.

내부 GRAM 및 자체 새로 고침 기술이 있는 디스플레이의 경우 캔버스 메모리가 필요하지 않습니다. 그러나 그리기 성능 향상이나 디스플레이에 로컬인 GRAM을 활용하지 않는 디스플레이 구성을 위해 캔버스 메모리 영역이 애플리케이션에 의해 정의됩니다.

캔버스 메모리 요구 사항은 캔버스 크기 및 색 농도의 함수이며 다음 수식으로 정의됩니다.

<i>캔버스 RAM(바이트) = (x * y * (bpp/8))</i>

여기서 "x"와 "y"는 캔버스(디스플레이)의 크기입니다.

또한 대부분의 애플리케이션은 핵심 Azure RTOS GUIX 라이브러리 스토리지 요구 사항에 포함되지 않은 그래픽 리소스를 활용합니다. 이러한 리소스에는 글꼴, 그래픽 아이콘(pixelmap) 및 정적 문자열이 포함됩니다. 이 데이터는 const 메모리 섹션(예: FLASH)에 저장할 수 있습니다.

이 메모리 영역의 크기는 사용되는 고유 글꼴의 수와 크기, 사용되는 그래픽 아이콘의 수와 크기, 출력 색 형식, 각 리소스가 압축된 데이터를 사용하는지 여부를 포함한 여러 요인에 따라 달라집니다. Azure RTOS GUIX는 글꼴 데이터와 pixelmap 데이터 모두의 RLE 압축을 지원하기 때문입니다. 각 리소스에 대한 스토리지 요구 사항은 Azure RTOS GUIX Studio 애플리케이션 내에 표시되므로 사용자는 애플리케이션 리소스에서 사용하는 플래시 메모리의 양을 추적하고 모니터링할 수 있습니다.

Azure RTOS ThreadX와 같이 Azure RTOS GUIX의 크기는 애플리케이션에서 실제로 사용하는 서비스에 따라 자동으로 조정됩니다. 이렇게 하면 사실상 복잡한 구성 및 빌드 매개 변수가 제거되어 개발자가 더 쉽게 작업을 수행할 수 있습니다.

#### <a name="simple-easy-to-use"></a>간단하고 손쉬운 사용

Azure RTOS GUIX는 사용이 매우 간단합니다. Azure RTOS GUIX Studio를 사용하면 개발자가 데스크톱에서 시각적으로 디자인하고 실제 대상에서 실행되는 C 코드를 생성할 수 있으므로 Azure RTOS GUIX를 훨씬 더 쉽게 사용할 수 있습니다. 그러면 애플리케이션에서 자체 사용자 지정 이벤트 처리 및 그리기 기능을 추가하여 GUI를 완성할 수 있습니다.

Azure RTOS GUIX API를 사용하는 것은 간단합니다. Azure RTOS GUIX API는 직관적이고 매우 기능적입니다. API 이름은 다른 파일 시스템 제품에서 흔히 볼 수 있는 매우 축약된 이름 및/또는 “알파벳 약자”가 아니라 실제 단어로 구성됩니다. 모든 Azure RTOS GUIX API에는 선행 *gx_* 가 있으며 명사-동사 명명 규칙을 따릅니다. 또한 API 전체에 걸쳐 기능적 일관성이 있습니다. 예를 들어 위젯 제어 블록을 초기화하는 모든 API의 이름은 &lt; widget_type&gt;_create이고 각 위젯 형식에 대한 만들기 함수 매개 변수는 항상 동일한 순서로 정의됩니다.

### <a name="comprehensive-set-of-built-in-widgets"></a>포괄적인 기본 제공 위젯 세트

* Azure RTOS GUIX는 다음과 같은 다양한 기본 제공 위젯 세트를 제공합니다.
* 아코디언 메뉴
* 단추
* 확인란
* 순환 계기
* 드롭다운 목록
* 가로 목록
* 가로 스크롤 막대 창
* 아이콘
* 아이콘 단추
* 꺾은선형 차트
* 메뉴
* 여러 줄 텍스트 단추
* 여러 줄 텍스트 입력
* 여러 줄 텍스트 보기
* 숫자 Pixelmap 프롬프트
* 숫자 프롬프트
* 숫자 스크롤 휠
* Pixelmap 단추
* Pixelmap 프롬프트
* Pixelmap 슬라이더
* Pixelmap 스프라이트
* Progress Bar
* prompt
* 방사형 진행률 표시줄
* Radio Button
* 스크롤 휠
* 한 줄 텍스트 입력
* 슬라이더
* 문자열 스크롤 휠
* 텍스트 단추
* 트리 뷰
* 세로 목록
* 세로 스크롤 막대

애플리케이션에서 자체 고객 위젯도 쉽게 만들 수 있습니다.

### <a name="complete-low-level-drawing-api"></a>완벽한 하위 수준 그리기 API

Azure RTOS GUIX는 애플리케이션에서 복잡한 그래픽 도형을 렌더링할 수 있도록 하는 강력한 캔버스 그리기 API를 제공합니다.

모든 기능은 높은 색상 농도 대상에서 앤티앨리어싱을 지원하며 단색 및 pixelmap 패턴 채우기를 포함하여 모든 도형의 윤곽선을 그리고 채울 수 있습니다. 모든 그리기 기본 도형은 16bpp 이상의 색 농도로 실행 시 브러시 알파를 지원합니다. 그리기 기능은 다음과 같습니다.

* 원호 그리기
* 원 그리기
* 선 그리기
* 원형 그리기
* Pixelmap 혼합
* Pixelmap 타일
* 다각형 그리기
* 텍스트 그리기
* 현 그리기
* 타원 그리기
* 픽셀 그리기
* Pixelmap 그리기
* Pixelmap 회전
* 사각형 그리기
* 텍스트 혼합

### <a name="default-free-fonts-and-easy-to-add-more"></a>기본 무료 글꼴 및 손쉬운 추가

Azure RTOS GUIX는 무료 트루타입 글꼴 세트를 제공합니다. 개발자는 원하는 대로 트루타입 글꼴을 더 추가할 수 있습니다.

Azure RTOS GUIX 글꼴 형식은 8bpp 앤티앨리어싱, 4bpp 앤티앨리어싱 및 1bpp 단색 글꼴을 지원합니다. 리소스가 제한된 대부분의 애플리케이션의 경우 Azure RTOS GUIX는 GUIX Studio 데스크톱 도구를 사용하여 트루타입 글꼴을 압축된 비트맵 형식으로 미리 렌더링합니다.

### <a name="custom-jpg-and-png-decoder-implementation"></a>사용자 지정 JPG 및 PNG 디코더 구현

사용자 지정 JPG 및 PNG 디코더 구현 JPG 및 PNG 파일 디코더 구현입니다. 이 구현은 Azure RTOS GUIX 호환 pixelmap 형식 이미지의 색 공간 변환, 디더링 및 런타임 생성을 지원합니다.

### <a name="extensive-display-and-touchscreen-support"></a>광범위한 디스플레이 및 터치 스크린 지원

Azure RTOS GUIX는 1bpp 단색, 8bpp 팔레트, 8bpp 3:3:2 형식,

16bpp 565 rgb 형식, 16bpp 4:4:4:4 형식, 32bpp x:r:g:b 형식, 32bpp a:r:g:b 형식을 포함한 거의 모든 색상 형식에 대한 일반 디스플레이 드라이버를 제공합니다. 또한 Azure RTOS GUIX는 가장 많이 사용되는 여러 LCD 컨트롤러 및 하드웨어 가속기(ST ChromeArt, Renesas Synergy 등)와 통합됩니다.

Azure RTOS GUIX는 터치 스크린(제스처 지원 포함), 펜 및 가상 키보드 입력 디바이스를 완벽하게 지원합니다.

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a>Azure RTOS GUIX Studio 데스크톱 WYSIWYG 도구

Azure RTOS GUIX Studio는 사용자가 GUI 화면을 만드는 데 사용되는 그래픽 요소를 끌어서 놓을 수 있는 완전한 WYSIWYG 화면 디자인 환경을 제공합니다. Azure RTOS GUIX Studio는 대상에서 컴파일되고 실행할 준비가 된 Azure RTOS GUIX 라이브러리와 호환되는 C 코드를 자동으로 생성합니다. 개발자는 통합된 Azure RTOS GUIX Studio 글꼴 생성 도구를 사용하여 애플리케이션 내에서 사용할 미리 렌더링된 글꼴을 생성할 수 있습니다. 글꼴은 단색 또는 앤티앨리어싱 형식으로 생성될 수 있으며 대상의 공간을 절약하도록 최적화되어 있습니다. 글꼴에는 다국어 애플리케이션의 유니코드 문자를 비롯한 모든 문자 세트가 포함될 수 있습니다.

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

Azure RTOS GUIX Studio는 대상 시스템에서 사용할 수 있도록 압축된 Azure RTOS GUIX Pixelmap으로 변환하여 PNG 또는 JPG 파일에서 그래픽을 쉽게 가져올 수 있게 합니다. 많은 Azure RTOS GUIX 위젯 형식은 사용자 지정 모양과 느낌을 위해 사용자 그래픽을 통합하도록 디자인되었습니다. 또한 Azure RTOS GUIX Studio를 사용하면 Azure RTOS GUIX 위젯에서 사용하는 기본 색상 및 그리기 스타일을 사용자 지정할 수 있으므로 개발자가 Azure RTOS GUIX의 모양을 매우 쉽게 조정할 수 있습니다. 애플리케이션 문자열의 생성 및 유지 관리는 Azure RTOS GUIX Studio의 또 다른 기본 제공 기능입니다. 이를 통해 개발자는 개발에 하나의 언어를 사용하여 애플리케이션을 디자인하고 제품 출시 후 추가 언어에 대한 지원을 빠르고 쉽게 추가할 수 있습니다. Azure RTOS GUIX Studio 환경 내의 PC 데스크톱에서 완전한 Azure RTOS GUIX 애플리케이션을 실행할 수 있으므로 GUI 개념의 빠르고 쉬운 생성 및 데모, 화면 흐름 테스트, 화면 전환 및 애니메이션 관찰이 가능합니다. 완료 시 컴파일하고 Azure RTOS GUIX 및 Azure RTOS ThreadX 라이브러리와 연결할 준비가 되었으며 대상에서 사용할 수 있는 C 데이터 구조로 디자인을 내보낼 수 있습니다.

Azure RTOS GUIX 및 Azure RTOS GUIX Studio는 여러 리소스 테마를 지원하므로 런타임에 애플리케이션의 스킨을 쉽게 다시 지정할 수 있습니다. 하나의 단순한 API를 사용하여 글꼴, 색 및 pixelmap을 런타임에 변경할 수 있습니다.

GUIX Studio에 대한 자세한 정보

### <a name="complete-win32-simulation"></a>전체 Win32 시뮬레이션

Azure RTOS GUIX는 대상 보드에서 실행되는 것과 똑같은 그리기 라이브러리를 사용하여 Windows PC에서 실행됩니다. Azure RTOS GUIX를 사용하면 PC에서 GUI 애플리케이션을 빌드하고 실행할 수 있으며 디버깅, 신속한 프로토타입 생성, 데모 및 WYSIWYG 대상 작업을 위해 대상에서 동일한 애플리케이션 코드를 사용할 수 있습니다.

### <a name="advanced-technology"></a>고급 기술

* Azure RTOS GUIX의 고급 기술은 다음과 같습니다.
* 알파 혼합
* 앤티앨리어싱
* 자동 크기 조정
* 비트맵 압축
* 캔버스 혼합
* 사용자 지정 위젯 지원
* 지연된 그리기 지원
* 디더링 지원
* Endian 중립 프로그래밍
* 하드웨어 가속기 지원
* 다국어 지원 및 UTF-8 인코딩
* 다중 디스플레이 및 캔버스 지원
* 최적화된 클리핑, 그리기 및 이벤트 처리
* 런타임 JPEG 및 PNG 디코더
* 스킨 적용 및 테마
* 알파 그래픽 형식으로 단색부터 32비트 트루 컬러까지 지원
* 전환, 스프라이트 및 애니메이션 지원
* Win32 시뮬레이션
* 뷰포트 및 Z 순서 유지 관리를 포함한 창 관리
