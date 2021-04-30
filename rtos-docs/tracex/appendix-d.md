---
title: 부록 D - 덤프 및 추적 버퍼
description: Azure RTOS ThreadX에서 만든 추적 버퍼를 호스트 컴퓨터의 파일에 덤프하는 작업은 사용되는 특정 개발 도구에서 제공하는 명령 및/또는 유틸리티를 통해 수행됩니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 30f6b5e329feeb2dca37dda391fd738aba587c9a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812540"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a>부록 D - 덤프 및 추적 버퍼

Azure RTOS ThreadX에서 만든 추적 버퍼를 호스트 컴퓨터의 파일에 덤프하는 작업은 사용되는 특정 개발 도구에서 제공하는 명령 및/또는 유틸리티를 통해 수행됩니다. 이 부록에는 ThreadX와 함께 사용되는 몇 가지 인기 있는 개발 도구에서 추적 버퍼를 호스트 파일에 덤프하는 예제가 포함되어 있습니다. 

## <a name="benchx-tools"></a>BenchX 도구

아래와 같이 _*_메모리 보기_** 내에서 ***파일에 메모리 저장** _ 단추를 선택하여 BenchX 도구를 통해 추적 버퍼를 호스트 파일에 쉽게 덤프할 수 있습니다.

![BenchX 도구의 메모리 보기 스크린샷](./media/user-guide/image642.jpg)

여기서 아래와 같이 추적 버퍼 주소, 크기, 대상 파일 이름(경로 포함)을 지정하고 ***저장*** 단추를 선택합니다. 그러면 TraceX 내에서 볼 이진 추적 파일이 생성됩니다.

![BenchX 도구 저장 대화 상자의 스크린샷](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a>RealView 도구

RealView의 명령줄 프롬프트에서 다음 명령을 입력하여 ARM RealView 도구를 통해 추적 버퍼를 호스트 파일에 쉽게 덤프할 수 있습니다.

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

완료되면 ***trace_file.trx*** 파일에는 주소 0x6860에서 시작하여 0xE560까지 이동하는 추적 버퍼가 포함됩니다. 이 파일은 TraceX에서 볼 수 있습니다.

## <a name="iar-tools"></a>IAR 도구

다음과 같이 메모리 보기에서 간단히 마우스 오른쪽 단추를 클릭하고 ***메모리 저장...*** 옵션을 선택하면 IAR 도구로 추적 버퍼를 호스트 파일에 쉽게 덤프할 수 있습니다.

![IAR 도구의 메모리 저장 옵션 스크린샷](./media/user-guide/image0_311.jpg)

그러면 ***메모리 저장** _ 대화 상자가 표시됩니다. 시작 주소와 끝 주소 및 추적 파일 이름을 입력한 다음, _*_저장_*_ 단추를 선택합니다. 아래 예제에서 IAR 도구는 지정된 추적 버퍼를 _*_trace_file.hex_** 파일의 Intel HEX 레코드에 저장합니다.

![IAR 도구 메모리 저장 대화 상자의 스크린샷](./media/user-guide/image648.jpg)

이 시점에서 추적 버퍼는 호스트의 ***trace_file.hex*** 파일에 저장되며 TraceX를 사용하여 볼 수 있습니다.

## <a name="codewarrior-tools"></a>CodeWarrior 도구

명령 창에서 ***save** _ 명령을 입력하면 CodeWarrior 도구로 추적 버퍼를 호스트 파일에 쉽게 덤프할 수 있습니다. 다음 예제 _ *_save_** 명령은 추적 버퍼가 0x102200에서 시작하고 0x109F00에서 끝나는 것으로 가정합니다.

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

이로 인해 추적 버퍼가 호스트의 ***trace_file.trx*** 파일에 저장됩니다.

## <a name="mplab-tools"></a>MPLAB 도구

MPLAB는 테이블 내보내기 유틸리티를 통해 TraceX 호환 추적 파일을 만들 수 있습니다. 이를 통해 모든 범위의 메모리를 호스트 파일로 내보낼 수 있습니다. 이 유틸리티를 사용하여 TraceX에 대한 추적 파일을 만들려면 다음과 같이 수행합니다.

**1단계** 보기 -> 메모리를 선택하여 메모리 창을 엽니다.

![보기 메뉴에서 선택한 메모리의 스크린샷](./media/user-guide/image0_316.jpg)

**2단계** **메모리 보기** 내에서 마우스 오른쪽 단추를 클릭하여 옵션 목록을 표시합니다. **표시 형식-1 바이트** 를 지정하여 바이트 표시를 선택합니다.

![표시 형식 옵션이 선택된 메모리 보기의 스크린샷](./media/user-guide/image650.png)

![이동 대화 상자의 스크린샷](./media/user-guide/image651.jpg)

**3단계** **메모리 보기** 창 내에서 마우스 오른쪽 단추를 다시 클릭하고 **이동** 을 선택합니다. 그러면 이벤트 버퍼의 주소를 지정할 수 있는 대화 상자가 열립니다. 이 예제에서는 **_event_buffer_** 가 표시됩니다.

![이동 옵션이 선택된 메모리 보기의 스크린샷](./media/user-guide/image0_312.jpg)

![표시된 event_buffer를 보여 주는 예제의 스크린샷](./media/user-guide/image653.png)

**4단계** 이렇게 하면 항상 문자열 BTXT...인 추적 버퍼의 첫 번째 위치 콘텐츠가 강조 표시됩니다.

![추적 버퍼의 첫 번째 위치에 대한 스크린샷](./media/user-guide/image0_313.jpg)

**5단계** 이제 다시 마우스 오른쪽 단추를 클릭하여 옵션 메뉴를 표시하고 **테이블 내보내기** 를 선택합니다.

![테이블 내보내기 옵션이 선택된 메모리 보기의 스크린샷](./media/user-guide/image0_314.jpg)

**6단계** 표시된 것처럼 **테이블 내보내기** 대화 상자가 나타납니다. 내보낼 주소의 범위를 지정합니다. 8K 추적 버퍼의 경우 이 예제에서와 같이 범위를 0xA00006AC부터 0xA00026AC까지로 지정하고, 만들 호스트 파일의 이름을 입력합니다(이 예제에서는 demo_threadx.trx).

![[내보내기 대화 상자의 스크린샷.](./media/user-guide/image656.jpg)

**7단계** **demo_threadx.trx** 라는 파일이 호스트에 생성됩니다. 이 파일은 TraceX에서 열 수 있습니다.

## <a name="ghs-tools"></a>GHS 도구

디버그 명령 창의 명령줄 프롬프트에서 다음 명령을 입력하면 GHS 도구를 통해 추적 버퍼를 호스트 파일에 쉽게 덤프할 수 있습니다.

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

완료되면 **demo_threadx.trx** 파일에는 event_buffer에 있는 32,768바이트 크기의 추적 버퍼가 포함되고 TraceX에서 볼 수 있습니다.

## <a name="renesas-hew"></a>Renesas HEW

다음 세 가지 단계(및 하위 단계)를 수행하면 Renasas HEW로 추적 버퍼를 쉽게 덤프할 수 있습니다.

**1단계** 메모리 창을 엽니다.

![[메모리 창의 스크린샷.](./media/user-guide/image657.jpg)

**2단계** 메모리 창 내에 커서를 놓고 마우스 오른쪽 단추를 클릭합니다.

![저장 옵션이 선택된 메모리 창의 스크린샷](./media/user-guide/image0_315.jpg)

**3단계** 저장을 선택한 다음, 다른 이름으로 메모리 저장 창에서 다음을 수행합니다.

- 파일 형식 선택: 이진
- 파일 이름 지정: 원하는 대로
- 시작 주소 지정: trace_buffer
- 끝 주소 지정: (trace_buffer+크기)
- 액세스 크기 지정: 1
- 저장을 클릭합니다.

![다른 이름으로 메모리 저장 대화 상자의 스크린샷](./media/user-guide/image659.jpg)