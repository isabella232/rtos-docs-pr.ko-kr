---
title: 3장 - UDP 전송 테스트 실행
description: 이 장에서는 Iperf 샘플을 실행하는 방법에 대한 지침을 제공합니다.
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2a68ba3ddb71adc424002c815fd023f50b552997
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2021
ms.locfileid: "122609801"
---
# <a name="chapter-3-running-the-demonstration"></a>챕터 3 데모 실행

호스트 브라우저가 이전에 표시된 대로 NetX Duo Iperf 데모 웹 페이지를 표시하고 Jperf가 호스트에서 실행되고 있다고 가정하고 이 장에서는 각 Iperf 테스트를 실행하는 방법을 설명합니다.

## <a name="running-the-udp-transmit-test"></a>UDP 전송 테스트 실행

UDP 전송 테스트는 NetX Duo UDP를 호스트로 전송하는 성능을 결정합니다. 이 테스트에서 NetX Duo 대상은 클라이언트이고 Jperf 호스트는 서버입니다. 먼저 Jperf IDE에서 **서버** 및 **UDP** 를 선택합니다. 그런 다음, **IPerf 실행!** 을 선택하여 아래와 같이 Iperf 서버를 시작합니다.

![UDP 전송 테스트 실행.](media/picture3.jpg)

이제 NetX Duo Iperf 데모 웹 페이지에서 **UDP 전송 테스트 시작** 단추를 선택하여 테스트를 시작합니다. 이제 아래와 같이 Jperf IDE 및 업데이트된 NetX Duo 웹 페이지에서 성능 통계를 관찰해야 합니다.

![UDP 전송 테스트 통계.](media/picture4.jpg)

테스트를 완료하려면 NetX Duo Iperf 데모 웹 페이지에서 **여기** 링크를 선택합니다. 이제 테스트의 성능 결과를 관찰해야 합니다. 이 예에서 NetX Duo 대상에서 Iperf 호스트에 대한 UDP 전송 성능은 아래와 같이 NetX Duo 대상에서 94Mbps였습니다.

![UDP 전송 테스트 결과.](media/picture5.jpg)

## <a name="running-the-udp-receive-test"></a>UDP 수신 테스트 실행

UDP 수신 테스트는 NetX Duo 대상에서 NetX Duo UDP 수신의 성능을 결정합니다. 이 테스트에서 NetX Duo 대상은 클라이언트이고 Jperf 호스트는 서버입니다. 먼저 Jperf IDE에서 **클라이언트** 및 **UDP** 를 선택합니다. 그런 다음, 다음 그림과 같이 NetX Duo Iperf 데모 웹 페이지에서 **UDP 수신 테스트 시작** 을 선택합니다.

![UDP 수신 테스트 실행.](media/picture6.jpg)

그런 다음, Jperf IDE에서 **IPerf 실행!** 을 선택하여 아래와 같이 Jperf IDE의 통계를 관찰합니다.

![UDP 수신 테스트 통계.](media/picture7.jpg)

테스트를 완료하려면 NetX Duo Iperf 데모 웹 페이지에서 **여기** 링크를 선택합니다. 이제 테스트의 성능 결과를 관찰해야 합니다. 이 예에서 NetX Duo 대상의 UDP 수신 성능은 아래와 같이 95Mbps였습니다.

![UDP 수신 테스트 결과](media/picture8.jpg)

## <a name="running-the-tcp-transmit-test"></a>TCP 전송 테스트 실행

TCP 전송 테스트는 NetX Duo TCP를 호스트로 전송하는 성능을 결정합니다. 이 테스트에서 NetX Duo 대상은 클라이언트이고 Jperf 호스트는 서버입니다. 먼저 Jperf IDE에서 **서버** 및 **TCP** 를 선택합니다. 그런 다음, **IPerf 실행!** 을 선택하여 아래와 같이 Iperf 서버를 시작합니다.

![TCP 전송 테스트 실행.](media/picture9.jpg)

이제 NetX Duo Iperf 데모 웹 페이지에서 **TCP 전송 테스트 시작** 단추를 선택하여 테스트를 시작합니다. 이제 아래와 같이 Jperf IDE 및 업데이트된 NetX Duo Iperf 데모 웹 페이지에서 성능 통계를 관찰해야 합니다.

![TCP 전송 테스트 통계.](media/picture10.jpg)

테스트를 완료하려면 NetX Duo Iperf 데모 웹 페이지에서 ***여기*** 링크를 선택합니다. 이제 테스트의 성능 결과를 관찰해야 합니다. 이 예에서 NetX Duo 대상의 TCP 전송 성능은 아래와 같이 91Mbps였습니다.

![TCP 전송 테스트 결과.](media/picture11.jpg)

## <a name="running-the-tcp-receive-test"></a>TCP 수신 테스트 실행

TCP 수신 테스트는 NetX Duo 대상에서 NetX Duo TCP 수신의 성능을 결정합니다. 이 테스트에서 NetX Duo 대상은 클라이언트이고 Jperf 호스트는 서버입니다. 먼저 Jperf IDE에서 **클라이언트** 및 **TCP** 를 선택합니다. 다음으로, 표시된 대로 NetX Duo 웹 페이지에서 **TCP 수신 테스트 시작** 을 선택합니다.

![TCP 수신 테스트 실행](media/picture12.jpg)

그런 다음, Jperf IDE에서 **IPerf 실행!** 을 선택하여 아래와 같이 Jperf IDE의 통계를 관찰합니다.

![TCP 수신 테스트 통계.](media/picture13.jpg)

테스트를 완료하려면 NetX Duo Iperf 데모 웹 페이지에서 ***여기*** 링크를 선택합니다. 이제 테스트의 성능 결과를 관찰해야 합니다. 이 예에서 NetX Duo 대상의 TCP 수신 성능은 아래와 같이 71Mbps였습니다.

![TCP 수신 테스트 결과.](media/picture14.jpg)
