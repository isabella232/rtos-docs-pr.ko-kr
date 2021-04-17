---
title: 3장 - USBX DPUMP 클래스 고려 사항
description: USBX에는 호스트 및 디바이스 측에 대한 DPUMP 클래스가 포함되어 있습니다. 이 클래스는 자체의 표준 클래스가 아니라 두 개의 대량 파이프를 사용하고 이러한 두 파이프에서 데이터를 앞뒤로 전송하여 간단한 디바이스를 만드는 방법을 보여주는 예제입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c7870f1984fe3104d30e3b9efd82010218acbe27
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813429"
---
# <a name="chapter-3---usbx-dpump-class-considerations"></a>3장 - USBX DPUMP 클래스 고려 사항

USBX에는 호스트 및 디바이스 측에 대한 **DPUMP** 클래스가 포함되어 있습니다. 이 클래스는 자체의 표준 클래스가 아니라 두 개의 대량 파이프를 사용하고 이러한 두 파이프에서 데이터를 앞뒤로 전송하여 간단한 디바이스를 만드는 방법을 보여주는 예제입니다. **DPUMP** 클래스를 사용하여 사용자 지정 클래스 또는 레거시 RS232 디바이스를 시작할 수 있습니다.

USB DPUMP 흐름 차트:

![USB DPUMP 흐름 차트](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a>USBX DPUMP 디바이스 클래스

디바이스 **DPUMP** 클래스는 USB 호스트에 연결할 때 시작되는 스레드를 사용합니다. 스레드는 대량 출력 엔드포인트에서 들어오는 패킷을 대기합니다. 패킷이 수신되면 콘텐츠를 대량 입력 엔드포인트 버퍼에 복사하고 이 엔드포인트에 트랜잭션을 게시하여 호스트가 이 엔드포인트에서 읽기 요청을 발행할 때까지 대기합니다. 이렇게 하면 대량 출력 및 대량 입력 엔드포인트 간에 루프백 메커니즘이 제공됩니다.
