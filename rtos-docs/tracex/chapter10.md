---
title: 챕터 10 - 고객 사용자 이벤트
description: 이 챕터에는 해당 이벤트에 대한 사용자 정의 이벤트, 사용자 지정 아이콘 및 정보 필드를 만드는 방법에 대한 설명이 포함되어 있습니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: b287436fb7f61df846bb0c84d910f5c095bc1f8f6635305e97c9e8b7aab64655
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790436"
---
# <a name="chapter-10---customer-user-events"></a>챕터 10 - 고객 사용자 이벤트

이 챕터에는 해당 이벤트에 대한 사용자 정의 이벤트, 사용자 지정 아이콘 및 정보 필드를 만드는 방법에 대한 설명이 포함되어 있습니다. 이 챕터에는 다음 섹션이 포함되어 있습니다. 

## <a name="inserting-user-defined-events"></a>사용자 정의 이벤트 삽입

ThreadX는 개발자가 자신의 고유한 사용자 정의 이벤트를 기록할 수 있는 기능을 제공하며 TraceX에서 그래픽으로 볼 수 있는 더 유용한 정보를 제공합니다. 사용자 정의 이벤트 번호의 범위는

**TX_TRACE_USER_EVENT_START**(4096)~**TX_TRACE_USER_EVENT_END**(65535)(포함)입니다. 추적 버퍼의 이벤트는 챕터 5에서 정의된 ***tx_trace_user_event_insert*** 를 통해 배치됩니다. 다음 예제 호출은 사용자 정의 이벤트를 대상의 현재 추적 버퍼에 삽입합니다. 즉, 사용자 정의 이벤트 4096 및 이벤트 4098을 호출합니다.

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a>사용자 정의 이벤트의 기본 표시

![사용자 정의 이벤트 아이콘](./media/user-guide/tx-events/image0.png)

기본적으로 TraceX는 챕터 6에서 설명한 대로 기본 사용자 정의 이벤트 아이콘을 사용하여 모든 사용자 이벤트를 표시합니다. 그림 28은 이전 ***tx_trace_user_event_insert*** 예제를 통해 이벤트 버퍼에 배치된 이벤트 452 및 453에 대한 기본 사용자 정의 이벤트 아이콘을 보여줍니다.

![사용자 정의 이벤트의 기본 표시에 대한 스크린샷입니다.](./media/user-guide/10.1.png)
**그림 28**

자세한 정보는 사용자 정의 이벤트에도 사용할 수 있습니다. 그림 28은 이벤트 번호가 4096인 이벤트 452에 대한 자세한 이벤트 정보를 보여주고 지정된 4개의 정보 필드를 보여줍니다.

![사용자 정의 이벤트의 자세한 표시에 대한 스크린샷입니다.](./media/user-guide/10.2.png)
**그림 29**

## <a name="defining-custom-user-defined-event-icons"></a>사용자 지정 사용자 정의 이벤트 아이콘 정의

또한 TraceX는 사용자 지정 사용자 정의 이벤트 아이콘 및 사용자 지정 정보 필드 레이블을 만들 수 있는 기능을 제공합니다. 이 기능은 ***tracex_custom trxc** _ 구성 파일에 이벤트 아이콘 사양을 추가하여 수행할 수 있습니다. 이 파일은 사용자 정의 TraceX 설치 디렉터리의 _ *_CustomEvents_** 하위 디렉터리에 있으며 기본값은 ‘c:\Azure_RTOS\TraceX’입니다. 예제 디렉터리 경로는 그림 30에 나와 있습니다.

![예제 디렉터리 경로의 스크린샷입니다.](./media/user-guide/custom_events_folder.png)
**그림 30**

***tracex_custom.trxc*** 사용자 지정 이벤트 구성 파일은 0개 이상의 사용자 지정 이벤트 정의를 포함하는 간단한 ASCII 텍스트 파일입니다. 파일 형식은 다음과 같습니다.

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

시작 및 종료 사이의 각 줄은 단일 사용자 지정 이벤트를 정의하는 데 사용됩니다. TraceX는 사용자 지정 이벤트가 정의되지 않은 이 파일의 템플릿 버전을 제공합니다('시작' 및 '종료' 레이블 사이에는 아무 것도 없음). 사용자 지정 이벤트 정의 형식은 다음과 같습니다.

**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**

여기서

- number: 4096과 65535 사이의 사용자 정의 이벤트 번호(포함)를 정의합니다.</th>
- name: 사용자 정의 이벤트의 논리적 이름을 정의합니다.</td>
- abbreviation: 두 글자로 된 사용자 정의 이벤트 약어를 정의합니다.</td>
- top_color: 괄호 안의 3자리 숫자인 아이콘의 위쪽 절반에 대한 RGB 값을 정의합니다. 일부 일반적인 RGB 정의는 다음과 같습니다.
  - 검은색 = (0,0,0)       
  - 흰색 = (255,255,255)
  - 빨간색 = (255,0,0)     
  - 녹색 = (0,255,0)     
  - 파란색 = (0,0,255)     
  - 노란색 = (255,255,0)   
  - 녹청색 = (0,255,255)   
  - 자홍색 = (255,0,255)   
  RBG 사양을 사용하면 사용자가 각 사용자 정의 아이콘에 대해 광범위한 색 범위를 제공합니다. RBG 색 정의에 대한 자세한 내용은 다음을 참조하십시오. https://en.wikipedia.org/wiki/RGB#Digital_representations
- botton_color: 아이콘의 아래쪽 절반에 대한 RGB 값(괄호 안의 3자리 숫자)을 정의합니다.
- label1: _ *_tx_trace_user_event_insert_** 호출에 지정된 대로 ***Info_field_1** _의 레이블입니다.
- label2: _ *_tx_trace_user_event_insert_** 호출에 지정된 대로 ***Info_field_2** _의 레이블입니다.
- label3: _ *_tx_trace_user_event_insert_** 호출에 지정된 대로 ***Info_field_3** _의 레이블입니다.
- label4: _ *_tx_trace_user_event_insert_** 호출에 지정된 대로 ***Info_field_4** _의 레이블입니다.

이 챕터에서 사용되는 두 개의 사용자 정의 이벤트에 대한 예제 정의는 그림 10.4에 나와 있습니다. 첫 번째 정의는 ***tracex_custom.trxc** _ 파일의 5번째 줄에 있는 이벤트 4096에 대한 것입니다. 이 정의는 사용자 정의 이벤트 4096의 이름을 ‘_*First_User_Event**’로 지정하고, 두 글자로 된 약어 **FE** 를 지정하고, 아이콘의 위쪽 부분을 빨간색으로 지정하고, 아래쪽 부분을 녹색으로 지정하고, 정보 필드 이름을 **First_Info1**, **First_Info2**, **First_Info3** 및 **First_Info4** 로 지정합니다. 사용자 정의 이벤트 4098은 **_tracex_custom.trxc_** 의 6번째 줄에서 유사하게 정의됩니다.

![사용자 정의 이벤트에 대한 예제 정의의 스크린샷입니다.](./media/user-guide/10.4.png)
**그림 31**

초기화하는 동안 TraceX가 ***tracex_custom.trxc** _ 파일을 읽기 때문에, 사용자 지정 아이콘 정의를 적용하려면 TraceX를 종료하고 다시 시작해야 합니다. 그림 32는 _*_tracex_custom.trxc_**에서 정의된 사용자 지정 이벤트 아이콘이 있는 사용자 정의 이벤트 452 및 453의 TraceX 표시를 보여줍니다.

![사용자 지정 이벤트 아이콘이 있는 사용자 정의 이벤트의 TraceX 표시에 대한 스크린샷입니다.](./media/user-guide/10.5.png)
**그림 32**

사용자 지정 이벤트 정의의 추가 정보는 두 번 클릭하거나, 마우스를 위에 놓거나, 현재 이벤트 단추를 클릭하여 선택한 이벤트에 표시됩니다. 그림 33은 이벤트 452에서 두 번 클릭하여 선택하는 방법을 보여줍니다. 이벤트 이름 및 정보 필드는 ***tracex_custom.trxc*** 에 추가된 샘플 정의와 모두 일치합니다.

![이벤트의 두 번 클릭 선택에 대한 스크린샷입니다.](./media/user-guide/10.6.png)
**그림 33**
