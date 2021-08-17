---
title: 간단한 예제 프로젝트
description: 이 장에서는 GUIX Studio에서 예제 프로젝트를 만들고 GUIX에서 예제를 실행하는 방법을 설명합니다.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 8981bed62d2929703e4233d6a3ee31b692226c26d046875a235bf3aca32a7573
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786568"
---
# <a name="chapter-10-example-project"></a>10장: 예제 프로젝트

이 장에서는 GUIX Studio에서 예제 프로젝트를 만들고 GUIX에서 예제를 실행하는 방법을 설명합니다.

## <a name="create-new-project"></a>새 프로젝트 만들기

첫 번째 단계는 새 프로젝트를 만들고 프로젝트에서 지원할 표시 및 언어를 구성하는 것입니다. GUIX Studio를 처음 시작하면 ***최근 프로젝트*** 화면이 표시됩니다.

![GUIX Studio 최근 프로젝트 대화 상자 스크린샷](./media/guix-studio/recent_projects.png)

**그림 10.1**

***새 프로젝트 만들기** _… 단추를 클릭하여 새 프로젝트를 시작합니다. 다음과 같이 *_새 GUIX 프로젝트_* 대화 상자가 표시됩니다.

![GUIX Studio 새 프로젝트 만들기 대화 상자 스크린샷](./media/guix-studio/create_new_project.png)

**그림 10.2**

이름 “***new_example***”을 프로젝트 이름으로 입력합니다. 프로젝트 이름은 표준 C 변수 명명 규칙을 사용해야 합니다. 즉, 특수 문자나 예약된 문자를 사용할 수 없습니다. 프로젝트를 저장할 위치의 경로를 입력합니다. 경로는 유효한 파일 시스템 디렉터리여야 합니다. 즉, 디렉터리가 없어도 GUIX Studio에서 디렉터리를 만들지 않습니다. “확인”을 클릭하여 프로젝트를 만듭니다.

표시되는 다음 화면은 아래와 같은 프로젝트 구성 화면입니다.

![GUIX Studio 프로젝트 구성 대화 상자 스크린샷](./media/guix-studio/config_new_project.png)

**그림 10.3**

이 대화 상자를 사용하여 프로젝트에서 지원할 표시 수를 지정하고 각 표시에 이름을 지정할 수 있습니다. 각 표시에서 지원되는 색 형식을 지정하고, 필요에 따라 Studio에서 생성되는 각 표시에 대한 출력 파일의 경로 이름을 입력해야 합니다. 출력 파일의 기본 디렉터리는 “***.\\***”로, C 출력 파일이 프로젝트 자체와 동일한 디렉터리에 기록된다는 것을 의미합니다.

이 예제에서는 “1”로 설정된 ***표시 수** _를 유지하고 표시 이름 필드에 이름 “_*_main_display_*_”를 입력한 다음, “_*_캔버스 메모리 할당_*_”을 선택합니다. 해상도, 색 형식, 디렉터리 필드를 기본값으로 유지하고 _*_확인_**을 클릭합니다.

이제 그림 10.4와 같이 프로젝트가 Studio IDE에서 열립니다.

![Studio IDE에서 열린 프로젝트 스크린샷](./media/guix-studio/initial_screen.png)

**그림 10.4**

새 프로젝트를 만들면 GUIX Studio에서 프로젝트의 시작점으로 사용할 기본 창을 자동으로 만듭니다. 이 회색 상자가 자동으로 생성되는 기본 창으로, ‘대상 뷰’의 가운데에 표시됩니다.

이 창이 선택되어 있지 않으면 창을 클릭하여 창 주위에 파선 선택 상자가 그려지도록 합니다. 이제 ***속성 뷰** _에서 _*_위젯 이름_*_, _*_위젯 ID_*_, _*_왼쪽_*_, _*_위쪽_*_ , _*_너비_*_ , _*_높이_*_ , _ *_테두리_* *를 아래 표시된 설정과 일치하도록 변경합니다. 변경 작업을 수행함에 따라 변경 내용이 대상 뷰에 즉시 적용됩니다.

![속성 뷰 대화 상자 스크린샷](./media/guix-studio/initial_window_properties.png)

**그림 10.5**

다음으로 ***GX_ICON** _ 위젯 내에서 사용할 pixelmap 리소스를 추가합니다. GUIX Studio 배포와 함께 제공된 몇 가지 아이콘을 이 예제에 사용할 수 있습니다. _*_Pixelmap_*_ 리소스 뷰를 확장하고 *_새 Pixelmap 추가_* 단추를 클릭합니다.

![새 Pixelmap 추가 단추 스크린샷](./media/guix-studio/image74.jpg)

GUIX Studio 설치 폴더로 이동한 다음 * **./graphics/icons** _ 폴더 내에서 이름이 _*_i_history_lg.png_*_ 인 파일을 선택합니다. _*_열기_*_ 를 클릭하여 이 리소스를 프로젝트에 추가합니다. 이제 새로 추가한 아이콘 이미지의 미리 보기가 _ *_Pixelmap_** 리소스 뷰에 표시됩니다.

![Pixelmap 리소스 뷰 스크린샷](./media/guix-studio/example_add_pixelmap.png)

**그림 10.6**

새 이미지 리소스는 나중에 UI 디자인의 일부로 사용할 것입니다.

pixelmap 리소스 추가와 유사하게, 도구 상자에 새 글꼴 리소스를 추가하여 나중에 이 글꼴을 디자인에 사용할 수 있도록 하겠습니다. **글꼴** 리소스 뷰를 확장하고 _*_새 글꼴 추가_*_ 단추를 클릭합니다. 이 작업을 수행하면 글꼴 _*_추가/편집_*_ 대화 상자가 호출됩니다. 다음으로, GUIX Studio 설치 폴더 _*_ .\\fonts\\verasans_ *_에서 제공된 GUIX 글꼴을 찾아보고 이름이 _* _VeraIt.ttf_*_인 트루타입 글꼴 파일을 선택합니다. 글꼴 이름 필드에 글꼴 이름 “_*_MEDIUM_ITALIC_*_”을 입력하고 높이 필드에 “_*_30_**”을 입력합니다. 이제 대화 상자가 다음과 같이 표시됩니다.

![글꼴 편집 대화 상자 스크린샷](./media/guix-studio/example_add_font.png)

**그림 10.7**

***확인*** 을 클릭하여 이 글꼴을 프로젝트에 추가합니다. 이제 글꼴이 리소스 뷰에 표시됩니다.

![리소스 뷰의 글꼴 스크린샷](./media/guix-studio/example_font_added.png)

**그림 10.8**

새 글꼴은 나중에 UI 디자인에 사용할 것입니다.

이제 새로운 리소스를 사용할 수 있으므로 해당 리소스를 활용할 수 있는 몇 가지 자식 위젯을 화면에 추가해야 합니다. 대상 뷰에서 창을 마우스 오른쪽 단추로 클릭하여 이전에 만든 “***hello_world** _”라는 창을 선택합니다. 이제 표시되는 팝업 메뉴에서 메뉴 명령 _*_삽입, 텍스트, 프롬프트_*_ 를 선택하여 새 _ *_GX_PROMPT_** 위젯을 삽입하고 배경 창에 위젯을 연결합니다. 이제 창이 다음과 같이 표시됩니다.

![프롬프트 선택 항목이 있는 팝업 메뉴 스크린샷](./media/guix-studio/image78.jpg)

**그림 10.9**

*_글꼴_* 리소스 뷰에서 이름이 “***MEDIUM_ITALIC** _”인 글꼴을 클릭하고 끌어서 프롬프트 위젯에 글꼴을 놓습니다. 다음으로, 프롬프트 속성을 그림 10.10과 같이 편집하여 프롬프트의 크기를 조정하고, 프롬프트 투명도를 설정하고, 프롬프트 텍스트 및 스타일을 변경합니다.

![프롬프트 속성 뷰 스크린샷](./media/guix-studio/image79.jpg)

**그림 10.10**

화면 해상도에 따라 각 설정을 보기 위해 속성 뷰에서 세로로 스크롤해야 할 수도 있습니다. 변경 작업을 수행한 후에는 대상 뷰가 다음과 같이 표시됩니다.

![Hello World 선택 항목이 있는 팝업 메뉴 스크린샷](./media/guix-studio/image80.jpg)

**그림 10.11**

다음으로, 아이콘 단추 스타일 위젯을 화면에 배치하겠습니다. 배경 창을 클릭하여 선택하고 최상위 메뉴 또는 오른쪽 클릭 팝업 메뉴를 사용하여 ***삽입, 단추, 아이콘 단추** _를 선택한 다음, 새 _*_GX_ICON_BUTTON_*_ 을 창에 추가합니다. 이전에 추가한 _ *_I_HISTORY_LG_**라는 아이콘을 클릭하고 아이콘 단추로 끌어옵니다. 속성 뷰를 사용하여 아이콘 위치 및 크기를 아래와 같이 조정합니다.

![아이콘 단추 스타일 위젯의 속성 뷰 스크린샷](./media/guix-studio/image81.jpg)

**그림 10.12**

이제 화면이 다음과 같이 표시됩니다.

![Hello World 및 클립보드 아이콘이 있는 팝업 메뉴 스크린샷](./media/guix-studio/image82.jpg)

**그림 10.13**

간단한 예제 화면 디자인을 마쳤습니다. 실제 애플리케이션 화면은 훨씬 더 복잡하겠지만 GUIX Studio를 사용하여 사용자 고유의 애플리케이션 화면을 만드는 방법을 보여 주기에는 충분합니다.

## <a name="generate-resource-and-application-code"></a>리소스 및 애플리케이션 코드 생성

다음 단계는 포함된 GUIX 런타임 UI를 정의하는 리소스 파일과 사양 파일을 생성하는 것입니다. 출력 파일을 생성하려면 프로젝트 뷰에서 ***main_display** _ 노드를 마우스 오른쪽 단추로 클릭하고 _ *_리소스 파일 생성_** 명령을 선택해야 합니다. 리소스 파일이 생성되었음을 나타내는 정보 창이 그림 10.14와 같이 표시됩니다.

![알림 대화 상자 스크린샷](./media/guix-studio/image83.jpg)

**그림 10.14**

**확인** 을 클릭하여 이 알림을 해제하고 동일한 절차를 사용하여 _*_main_display_*_ 노드를 마우스 오른쪽 단추로 클릭한 다음, *_사양 파일 생성_* 명령을 선택합니다. 유사한 알림 창이 표시됩니다. 이제 간단한 UI 애플리케이션 파일을 생성했습니다.

## <a name="create-user-supplied-code"></a>사용자 제공 코드 만들기

다음 단계는 GUIX Studio에서 생성된 화면 디자인을 호출하는 사용자 고유의 애플리케이션 파일을 만드는 것입니다. 원하는 편집기를 사용하여 ***new_example.c*** 라는 원본 파일을 만들고 이 파일에 다음 소스 코드를 입력합니다.

```C

/* This is an example of the GUIX graphics framework in Win32. */
/* Include system files. */

#include <stdio.h>
#include "tx_api.h"
#include "gx_api.h"

/* Include GUIX resource and specification files for example. */

#include "new_example_resources.h"
#include "new_example_specifications.h"

/* Define the new example thread control block and stack. */

TX_THREAD new_example_thread;
UCHAR new_example_thread_stack[4096];

/* Define the root window pointer. */

GX_WINDOW_ROOT *root_window;

/* Define function prototypes. */

VOID new_example_thread_entry(ULONG thread_input);
UINT win32_graphics_driver_setup_24bpp(GX_DISPLAY *display);

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

VOID tx_application_define(void *first_unused_memory)
{
    /* Create the new example thread. */
    tx_thread_create(&new_example_thread, "GUIX New Example Thread", 
                      new_example_thread_entry, 0, 
                      new_example_thread_stack, sizeof(new_example_thread_stack),
                      1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

VOID new_example_thread_entry(ULONG thread_input)
{

    /* Initialize the GUIX library */
    gx_system_initialize();

    /* Configure the main display. */
    gx_studio_display_configure(MAIN_DISPLAY,                      /* Display to configure*/
                                win32_graphics_driver_setup_24bpp, /* Driver to use */
                                LANGUAGE_ENGLISH,                  /* Language to install */
                                MAIN_DISPLAY_DEFAULT_THEME,        /* Theme to install */
                                &root_window);                     /* Root window pointer */

    /* Create the screen - attached to root window. */

    gx_studio_named_widget_create("hello_world", (GX_WIDGET *) root_window, GX_NULL);

    /* Show the root window to make it visible. */
    gx_widget_show(root_window);

    /* Let GUIX run. */
    gx_system_start();

}
```

위의 소스 코드는 스택 크기가 4K바이트인 `GUIX New Example Thread`라는 일반적인 ThreadX 스레드를 만듭니다. 흥미로운 작업은 ***new_example_thread_entry*** 라는 함수에서 시작됩니다. 이 함수에서 GUIX 특정 스레드가 실행되기 시작합니다.

먼저 ***gx_system_initialize*** 라는 함수가 호출됩니다. GUIX 라이브러리를 처음 사용할 준비를 하기 위해 이 호출은 항상 다른 GUIX API가 호출되기 전에 수행해야 합니다.

다음으로, 예제에서는 ***gx_studio_display_configure*** 함수를 호출합니다. 이 함수는 GUIX 표시 인스턴스를 만들고, 요청된 언어의 애플리케이션 문자열 테이블을 설치하고, 표시 리소스에서 요청된 테마를 설치하고, 이 표시에 대해 생성된 루트 창에 대한 포인터를 반환합니다. 루트 창은 애플리케이션에서 표시할 모든 최상위 화면의 부모로 사용됩니다.

다음으로, 예제에서는 ***gx_studio_named_widget_create** _를 호출하여 _ *_hello_world_** 화면의 인스턴스를 만듭니다. 이 함수는 GUIX Studio에서 생성된 데이터 구조와 리소스를 사용하여 화면 인스턴스를 정의된 대로 만듭니다. 이 함수 호출에 루트 창 포인터를 두 번째 매개 변수로 전달하여 화면이 루트 창에 즉시 연결되도록 합니다. 마지막 매개 변수는 생성된 화면에 대한 포인터를 유지하려는 경우에 사용할 수 있는 선택적 반환 포인터입니다.

다음으로, ***gx_widget_show** _가 호출되어 루트 창과 _ *_hello_world_** 화면을 비롯한 모든 자식을 표시합니다.

마지막으로 예제에서는 ***gx_system_start*** 를 호출합니다. 이 함수는 GUIX 시스템 이벤트 처리 루프 실행을 시작합니다.

## <a name="build-and-run-the-example"></a>예제 빌드 및 실행

예제 빌드 및 실행은 빌드 도구와 환경에 따라 다릅니다. 그러나 일반적인 프로세스를 정의할 수 있습니다.

1. 새 디렉터리 및 애플리케이션 프로젝트 만들기
1. 프로젝트에 다음 파일을 추가합니다.

    **new_example_resources.c**

    **new_example_specification.c**

    **new_example.c**

1. GUIX Studio 설치 경로 ***./win32_runtime*** 에서 Win32 런타임 지원 파일을 추가합니다. 여기에는 ThreadX 및 GUIX Win32 헤더와 런타임 라이브러리 파일이 포함됩니다.
1. 프로젝트에 GUIX Win32 라이브러리(***gx.lib***) 추가
1. 프로젝트에 ThreadX Win32 라이브러리(***tx.lib***) 추가
1. 애플리케이션 컴파일, 연결 및 실행
