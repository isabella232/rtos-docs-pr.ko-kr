---
title: Azure RTOS(실시간 운영 체제) GUIX Studio 빠른 시작 가이드
description: 이 가이드에서는 Microsoft의 Azure RTOS GUIX 런타임 라이브러리용으로 특별히 설계된 Microsoft Windows 기반의 빠른 UI 개발 환경인 Azure RTOS GUIX Studio 애플리케이션의 사용법을 간략히 소개합니다.
author: philmea
ms.author: philmea
ms.date: 7/20/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: eedd53867b56312b53f4e9509136ee856acabfd7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811928"
---
# <a name="azure-rtos-guix-studio-quick-start-guide"></a>Azure RTOS GUIX Studio 빠른 시작 가이드

이 가이드에서는 Azure RTOS GUIX Studio의 사용법을 간략히 소개합니다. GUIX Studio는 Microsoft의 Azure RTOS GUIX 런타임 라이브러리와 함께 사용하도록 설계된 Windows 기반 UI 디자인 애플리케이션입니다. 

ThreadX RTOS(실시간 운영 체제) 및 Azure RTOS GUIX UI 런타임 라이브러리를 사용하는 임베디드 실시간 소프트웨어 개발자를 위한 것입니다. 개발자는 표준 Azure RTOS ThreadX 및 Azure RTOS GUIX 개념을 숙지해야 합니다.

## <a name="summary"></a>요약

Azure RTOS GUIX Studio에는 고유한 그래픽 인터페이스 디자인을 만들고 빌드하고 실행하는 데 필요한 모든 항목이 포함되어 있습니다. GUIX Studio를 평가할 때 사용하는 평가 키트는 GUIX 디자인을 독립 실행형 Windows 데스크톱 애플리케이션으로 빌드하고 실행하여 테스트하고 평가할 수 있게 설계되었습니다. GUIX는 그래픽 출력을 지원하는 거의 모든 임베디드 대상에서 사용하도록 설계되었으므로, 사용자가 수행하는 작업과 데스크톱에서 만드는 디자인이 애플리케이션 소프트웨어 변경 없이도 항상 컴파일되고 실행될 수 있습니다.
GUIX Studio 설치 관리자는 개발 시스템에 몇 가지 구성 요소를 배치합니다.

- GUIX Studio 애플리케이션
- 몇 가지 GUIX 예제 프로젝트
- 예제 프로젝트에 사용되는 모든 그래픽 리소스 및 글꼴
- Windows 데스크톱 환경에서 Microsoft Visual Studio IDE를 사용하여 빌드할 솔루션 파일 및 프로젝트 파일
- 사용자가 PC에서 자체 애플리케이션을 빌드하고 실행할 수 있도록 미리 빌드된 Win32용 GUIX 및 ThreadX 라이브러리
- GUIX 및 ThreadX API 헤더 파일

## <a name="prerequisites"></a>필수 조건

Azure RTOS GUIX Studio 설치 관리자에는 몇 가지 간단한 예제 프로젝트가 포함되어 있으며, GUIX Studio 애플리케이션을 사용하는 방법을 배울 때 이러한 예제를 수정, 빌드 및 실행하게 될 것입니다. Windows 데스크톱에서 예제를 빌드하고 실행하려면 Microsoft Visual Studio 컴파일러가 필요합니다. 이러한 도구는 다음 위치에서 다운로드할 수 있습니다.

https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs#DownloadFamilies_4

Microsoft 개발자 도구가 설치되어 있지 않은 경우에도 GUIX Studio 애플리케이션을 평가하고 사용하여 고유한 인터페이스 디자인을 만들고 생성된 소스 코드를 검사할 수 있습니다. 그러나 디자인을 독립 실행형 애플리케이션으로 빌드하고 실행할 수는 없습니다.

## <a name="running-the-examples"></a>예제 실행

GUIX Studio 설치 프로그램을 실행하면 설치 된 콘텐츠에 몇 가지 예제 Studio 프로젝트와 빌드 파일이 포함되어 있을 것입니다. 데스크톱 도구가 설치되어 있고 올바르게 작동 하는지 확인하려면 제공된 각 예제를 그대로 빌드하고 실행하여 시작하는 것이 좋습니다. 설치 디렉터리는 \<root>라고 합니다. 이 경우 파일 브라우저를 사용하여 \<root>/GUIX_Studio_6.x/examples로 이동해야 합니다. 이 디렉터리 내에 demo_guix_calculator, demo_guix_car_infotainment, demo_guix__home_automation, demo_guix_widget_types 등의 몇 가지 간단한 예제 프로그램이 표시됩니다.

## <a name="building-an-example"></a>예제 빌드

각 예제 폴더 내에서 *build* 라는 하위 디렉터리를 찾아야 합니다. 이 방향에는 지원되는 각 도구 체인을 위해 미리 구성된 프로젝트가 있습니다. 예를 들어 \<root>/GUIX_Studio_6.x/examples/thermometer/build/vs_2019로 이동하면 Visual Studio IDE에서 로드하고 실행할 수 있는, 미리 구성된 Microsoft Visual Studio 솔루션 파일 및 프로젝트 파일을 찾을 수 있습니다. 다른 도구 체인을 사용하려면 [azure_rtos_support](https://docs.microsoft.com/azure/azure-portal/supportability/how-to-create-azure-support-request#create-a-support-request)에 문의하세요.

Microsoft Visual C++ IDE를 시작하고 다음 예제 중 하나 이상을 여는 것이 좋습니다. \<F7> 키를 눌러 예제 프로젝트를 빌드하고, 프로젝트가 성공적으로 빌드되면 \<F5> 키를 눌러 프로그램을 실행합니다. 이제 GUIX 사용자 인터페이스가 Microsoft Windows 창에서 실행되는 것을 볼 수 있습니다.

## <a name="designing-and-running-your-own-user-interface"></a>자체 사용자 인터페이스 설계 및 실행

이 빠른 시작 가이드는 GUIX Studio 사용자 가이드 또는 GUIX 사용자 가이드를 대체하는 것은 아니지만 시작하는 데 충분한 정보를 제공합니다. GUIX Studio 사용자 가이드에서 자세한 내용을 참조하여 계속 진행하시기 바랍니다.

자체 사용자 인터페이스를 만들고 수정하는 방법에는 두 가지가 있습니다. GUIX 라이브러리 프로그래밍 설명서를 살펴보고 애플리케이션 소프트웨어 내에서 직접 GUIX API를 사용하여 디자인을 완벽하게 구현할 수 있습니다. GUIX Studio 애플리케이션을 사용하여 대부분의 화면 요소 디자인과 레이아웃 작업을 수행한 다음, 이벤트 처리 및 사용자 인터페이스가 실제로 작업을 수행하는 데 필요한 기타 애플리케이션 논리를 완료하는 경우가 더 많습니다.

제공된 각 예제는 GUIX Studio 인터페이스 디자인 애플리케이션을 사용하여 만들어졌습니다. GUIX Studio 설치 프로그램을 실행하면 바탕 화면에 GUIX Studio 6.x.x.x 아이콘이 생깁니다.  GUIX Studio를 지금 시작하고 “demo_guix_widget_types\guix_widget_types.gxp”라는 프로젝트를 엽니다. *widget_types* 데모는 가장 일반적인 GUIX 위젯 형식의 여러 변형을 보여 주는 예제 프로젝트입니다.

이제 프로젝트가 열렸으므로 "+"를 클릭하여 IDE의 왼쪽 상단 모퉁이에 있는 프로젝트 뷰에서 "Primary"라는 트리 노드를 열고 이 폴더 내에서 "Menu_Screen"이라는 최상위 창을 클릭합니다. 프로젝트가 아래와 같이 표시되면 안 됩니다.

![프로젝트가 열려 있는 Studio의 스크린샷](./media/guix-studio/qs_project_open.png)

## <a name="guix-studio-views"></a>GUIX Studio 뷰

GUIX Studio IDE는 여러 ***뷰*** 로 구성되어 있습니다. 각 뷰는 디자인을 탐색하고 해당 디자인을 변경하는 데 도움이 되도록 설계되었습니다.

### <a name="project-view"></a>프로젝트 보기

상단 왼쪽 뷰를 프로젝트 뷰라고 합니다. 이 뷰에는 프로젝트에 포함된 각 실제 디스플레이(대부분의 프로젝트에는 프로젝트가 하나만 있음)와 해당 디스플레이에서 실행되도록 설계된 화면과 자식 위젯이 표시됩니다.

### <a name="properties-view"></a>속성 뷰

프로젝트 뷰 아래에는 속성 뷰가 있습니다. 속성 뷰라는 이름에서 알 수 있듯이, 이 뷰에서는 관련된 다양한 속성을 변경하여 위젯을 수정할 수 있습니다.

### <a name="target-view"></a>대상 뷰

중앙 표시 영역을 대상 뷰라고 합니다. 이 뷰는 사용자 인터페이스를 WYSIWYG으로 표시한 것입니다. GUIX 라이브러리가 대상 뷰 내에서 그려지기 때문에 이 뷰는 디자인이 포함된 대상에서 실행될 때의 모습을 픽셀 단위로 표현한 것입니다. 프로젝트 뷰나 중앙 대상 뷰에서 다른 위젯을 클릭하면 속성 뷰에 표시된 값이 선택된 위젯의 속성을 표시하도록 변경되는 것을 볼 수 있습니다.

### <a name="resource-view"></a>리소스 뷰

마지막으로, 오른쪽에는 리소스 뷰가 표시됩니다. 이 뷰에서는 프로젝트에 포함된 색, 글꼴, 픽셀 맵 및 문자열을 선택, 추가, 삭제 및 수정할 수 있습니다.

## <a name="modifying-the-example"></a>예제 수정

GUIX Studio는 직관적으로 설계되었습니다. 위에 표시된 위젯 중 하나를 이동하려면 대상 뷰에서 해당 위젯을 클릭하고 새 위치로 끌어 놓기만 하면 됩니다. 위젯 색을 변경하려면 원하는 위젯을 클릭하고 속성 뷰에 표시되는 색을 변경합니다. 텍스트 표시 위젯에서 사용하는 글꼴을 변경하려면 리소스 뷰 내에서 원하는 글꼴을 클릭하고 원하는 대상 위젯에 끌어서 놓기만 하면 됩니다. 각 도구 모음 단추가 수행하는 작업과 관련된 빠른 도움말을 보려면 각 단추 위로 마우스를 가져갑니다.

직접 실험하고 예제를 약간 변경합니다. 예를 들어 위젯을 새 위치로 끌거나, 창 배경색을 변경하거나, 단추의 크기를 조정할 수 있습니다. 위젯을 삭제하면 애플리케이션 소스 코드와 관련된 수정 작업이 필요할 수 있으므로 GUIX 작업에 관한 경험이 더 쌓일 때까지 예제에서 위젯을 삭제하지 않는 것이 좋습니다.

## <a name="running-the-application-within-studio"></a>Studio 내에서 애플리케이션 실행

애플리케이션 편집 | 실행 메뉴 명령(또는 단추 모음의 애플리케이션 실행 단추)을 사용하여 새 바탕 화면 창에서 애플리케이션을 즉시 실행할 수 있습니다. 이 방법으로 사용자 지정 그리기 함수와 기타 애플리케이션 코드를 호출할 수는 없지만, UI 디자인을 신속하게 탐색하고 한 화면에서 다음 화면으로 탐색하는 등, 애플리케이션의 모양과 느낌을 전반적으로 이해할 수 있습니다.

## <a name="generating-source-files"></a>원본 파일 생성

변경 작업을 수행한 후에는 GUIX Studio 메뉴 명령을 호출하여 프로젝트의 새 원본 파일을 생성해야 합니다. 그런 다음, 예제 프로그램을 다시 빌드하여 작업의 변경 내용을 확인할 수 있습니다. 원본 파일을 생성하려면 GUIX Studio에서 프로젝트|리소스 파일 및 프로젝트 생성|사양 파일 생성 메뉴 명령을 사용합니다(프로젝트 뷰에서 디스플레이를 마우스 오른쪽 단추로 클릭하여 이 명령을 실행할 수도 있음).

이러한 원본 파일을 생성하면 프로젝트와 연결된 원본 파일이 업데이트되었음을 알리는 확인 메시지가 표시됩니다. 이 확인 메시지가 표시되지 않으면 프로젝트가 있는 디렉터리에 대한 쓰기 권한이 있는지 확인합니다. 이제 GUIX Studio 애플리케이션을 닫아도 됩니다. 프로젝트를 변경한 경우 GUIX Studio에서 해당 변경 내용을 저장할 것인지 묻는 메시지를 표시합니다. 계속 진행하여 변경 내용을 저장합니다. 이러한 예제는 GUIX Studio를 사용하는 방법을 배울 때 사용하고 실험하기 위한 것입니다.

### <a name="building-and-running-the-application"></a>애플리케이션 빌드 및 실행

GUIX Studio에서 프로젝트 출력 파일을 생성 했으므로 컴파일하고 연결하여 독립 실행형 Win32 실행 파일을 만들 수 있습니다. 또한 애플리케이션에서 정의한 사용자 지정 그리기 또는 이벤트 처리를 통합하기 위해 GUIX Studio에서 생성한 출력 파일을 사용자 고유의 애플리케이션 소프트웨어와 통합하여 연결해야 합니다. 여기서는 Microsoft Visual C++ 도구 체인을 예로 들지만 원하는 대상용으로 빌드하고 실행하는 경우에도 똑같은 절차가 사용됩니다.

- MSVC IDE를 시작하고 \<root>/GUIX_Studio_5.x/examples/demo_guix_widget_types/build/vs_2019/guix_widget_types.sln 솔루션을 엽니다.

- \<F7> 키를 사용하여 솔루션을 다시 빌드합니다.
- \<F5> 키를 사용하여 프로그램을 실행합니다.
 
이제 Studio 내에서 변경한 내용이 실행 중인 프로그램에 적용된 것을 볼 수 있습니다.

### <a name="learning-more"></a>자세히 알아보기

**GUIX Studio 사용자 가이드** 는 [azrtos-guix-studio-user-guide](https://docs.microsoft.com/azure/rtos/guix/about-guix-studio)에서 볼 수 있습니다. GUIX Studio 사용자 가이드는 GUIX Studio 사용법이 훨씬 더 자세히 설명된 가이드입니다.

또한 **GUIX 사용자 가이드** 는 [azrtos-guix-user-guide](https://docs.microsoft.com/azure/rtos/guix/about-guix)에서 볼 수 있습니다.  이 가이드는 GUIX 애플리케이션이 실행될 때 “내부에서” 발생하는 상황에 대한 자세한 정보를 제공합니다. GUIX 런타임 라이브러리 및 GUIX Studio의 기능을 제대로 활용하려면 이러한 가이드를 둘 다 참조해야 합니다.

## <a name="customer-support-center"></a>고객 지원 센터

다음 단계에 대한 질문 또는 도움이 필요하면 Azure Portal을 통해 지원 티켓을 제출하세요. 지원 요청을 보다 효율적으로 해결할 수 있도록 이메일 메시지에 다음 정보를 제공해 주세요.

- 발생 빈도와 안정적으로 재현할 수 있는 방법을 포함한 문제에 대한 자세한 설명입니다.
- 문제를 발생시키는 추적 파일을 첨부합니다.
- 사용 중인 Azure RTOS GUIX Studio의 버전(디스플레이 왼쪽 위에 표시됨).
- **_gx_version_idstring** 및 **_gx_build_options** 변수를 포함하여 사용 중인 Azure RTOS GUIX의 버전입니다.
