---
title: GUIX Studio 설치 및 사용
description: 이 챕터에서는 GUIX Studio UI 시스템 디자인 도구의 설치, 설정, 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 55d2b0ac08bdceebdf286effe4bbc679320541243ff78359deafe0858a7b597e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786475"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a>2장 - GUIX Studio 설치 및 사용

이 챕터에서는 GUIX Studio UI 시스템 디자인 도구의 설치, 설정, 사용과 관련된 다양한 문제에 대해 설명합니다. 

## <a name="product-distribution"></a>제품 배포

GUIX Studio를 검색하거나 [GUIX Studio 페이지](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab)로 직접 이동하여 [Microsoft 앱 스토어](https://microsoft.com/store/apps) 에서 GUIX Studio 앱을 가져올 수 있습니다. 그런 다음, 아래 작업을 수행합니다.

1. 앱 스토어의 GUIX Studio 페이지에서 **가져오기** 또는 **설치** 단추를 클릭하여 GUIX Studio를 다운로드합니다.

1. 아래 그림에 표시된 것처럼 브라우저에 Microsoft Store를 열 것인지 묻는 메시지가 표시될 수 있습니다. 이 경우 **열기** 단추를 선택합니다.
![열기를 선택하여 GUIX Studio를 설치합니다.](./media/guix-studio/open-ms-store.png)

1. 설치가 완료되면 **시작** 단추를 선택합니다.

1. GUIX Studio가 처음 시작될 때 GUIX 리포지토리를 로컬 컴퓨터에 복제할지 여부를 묻는 대화 상자가 표시됩니다. 리포지토리를 복제하도록 선택하거나, 이미 리포지토리를 복제한 위치를 가리키거나, 리포지토리를 전혀 복제하지 않도록 선택할 수 있습니다(이 경우에는 컴퓨터에 예제 프로젝트 1개가 설치됨).
![리포지토리를 복제하거나, 이미 복제된 리포지토리를 가리키거나, 건너뛰려면 선택합니다.](./media/guix-studio/clone-repo.png)

> ![!NOTE]
> GUIX Stuido의 주 메뉴에서 **구성** 을 선택하고, **GUIX 리포지토리** 를 선택하여 언제든지 이 대화 상자로 돌아갈 수 있습니다.

시작 프로세스가 완료되면 GUIX Studio를 사용할 준비가 된 것입니다.

## <a name="using-guix-studio"></a>GUIX Studio 사용

GUIX Studio를 사용하는 것은 간단합니다. "***시작***" 단추를 사용하여 GUIX studio를 실행하기만 하면 됩니다. 이 시점에서 GUIX Studio UI가 표시됩니다. 이제 GUIX Studio를 사용하여 그래픽으로 포함 된 UI를 만들 준비가 되었습니다. 여기에서 GUIX 예제 프로젝트를 포함하여 새 프로젝트를 만들거나 기존 프로젝트를 엽니다.

> [!NOTE]
> 확장명이 "**gxp**" 인 GUIX Studio 프로젝트 파일을 두 번 클릭하여 GUIX Studio를 자동으로 시작하고 참조된 프로젝트를 열 수도 있습니다.

## <a name="guix-studio-project-samples"></a>GUIX Studio 프로젝트 샘플

확장명 "***gxp** _"_ 를 포함하는 일련의 예제 GUIX Studio 프로젝트 파일은 설치의 "*_Sample_**" 하위 디렉터리에 있습니다. 이러한 미리 작성된 예제 프로젝트를 사용하면 GUIX Studio를 사용하는 데 익숙해질 수 있습니다.

항상 표시되는 한 가지 예제 프로젝트 파일은 ***samples/demo_guix_simple/guix_simple. gxp** _ 파일입니다. 이 예제 프로젝트 파일은 이 문서의 _ *_7장_**에 설명된 간단한 GUIX UI의 정의를 보여줍니다.

![GUIX Studio UI의 스크린샷](./media/guix-studio/image_10.png)

**그림 1**

## <a name="keyboard-shortcuts"></a>바로 가기 키

- **Ctrl + N:** 새 프로젝트
- **Ctrl + O:** 프로젝트 열기
- **Ctrl + S:** 프로젝트 저장
- **Ctrl + Shift + S:** 다른 이름으로 프로젝트 저장
- **Alt + F4:** 끝내기
