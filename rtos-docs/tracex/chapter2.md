---
title: 2장 - Azure RTOS TraceX 설치 및 사용
description: 이 장에서는 Azure RTOS TraceX 시스템 분석 도구의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 05d7fe3df38c7e8a3480c8ea0d4922a109de9ede
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812390"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a>2장 - Azure RTOS TraceX 설치 및 사용

이 장에서는 Azure RTOS TraceX 시스템 분석 도구의 설치, 설정 및 사용과 관련된 다양한 문제에 대해 설명합니다. 

## <a name="product-distribution"></a>제품 배포

TraceX를 검색하거나 [TraceX 페이지](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab)로 직접 이동하여 [Microsoft 앱 스토어](https://microsoft.com/store/apps)에서 TraceX 앱을 가져올 수 있습니다. 그런 다음, 다음을 실행합니다.

1. 앱 스토어의 TraceX 페이지에서 **가져오기** 또는 **설치** 단추를 클릭하여 TraceX를 설치합니다.

1. 아래 그림에 표시된 것처럼 브라우저에 Microsoft Store를 열 것인지 묻는 메시지가 표시될 수 있습니다. 이 경우 **열기** 단추를 선택합니다.
![열기를 선택하여 TraceX를 설치합니다.](../guix/media/guix-studio/open-ms-store.png)

1. 설치가 완료되면 **시작** 단추를 선택합니다. 

## <a name="using-tracex"></a>TraceX 사용

TraceX를 사용하는 것은 TraceX 내에서 추적 파일을 여는 것만큼 쉽습니다! ***Start** _ 단추를 통해 TraceX를 실행합니다. 이 시점에서 TraceX GUI(그래픽 사용자 인터페이스)를 확인할 수 있습니다. 이제 TraceX를 사용하여 기존 대상 추적 버퍼를 그래픽으로 볼 수 있습니다. _ *_파일 -> 열기_**를 클릭한 다음, 이진 추적 파일을 입력하여 이 작업을 쉽게 수행할 수 있습니다.

>[!IMPORTANT]
>*또한 확장명이 **trx** 인 추적 파일을 두 번 클릭하면 TraceX가 자동으로 시작됩니다.*

![TraceX GUI의 스크린샷](./media/user-guide/screen_shot_8.png)

**그림 1**

>[!IMPORTANT]
>*ThreadX를 사용하여 대상에서 추적 버퍼를 생성하는 방법에 대한 지침은 **5장** 을 참조하세요.*

## <a name="tracex-examples"></a>TraceX 예제

TraceX 애플리케이션을 처음 실행하거나 TraceX 애플리케이션을 업데이트할 때 TraceX 예제 추적 파일 및 custom_events.trxc 파일을 로컬 머신의 사용자 정의 디렉터리에 설치하라는 메시지가 표시됩니다.

이 설치 단계를 완료한 후에는 확장명이 **trx** 인 추적 파일 예제는 설치 폴더의 **TraceFiles** 하위 디렉터리에 있습니다. 이러한 미리 작성된 예제는 애플리케이션과 함께 실행되는 ThreadX에서 생성된 추적 버퍼에 TraceX를 사용하는 데 도움이 됩니다.

추적 파일의 한 가지 예제는 항상 ***demo_threadx.trx** _ 파일입니다. 이 예제 추적 파일은 __ThreadX 사용자 가이드*의 6장에서 설명한 대로 표준 ThreadX 데모를 실행하는 방법을 보여 줍니다.

![TraceX의 열기 대화 상자 스크린샷](./media/user-guide/screen_shot_9.png)

**그림 2**
