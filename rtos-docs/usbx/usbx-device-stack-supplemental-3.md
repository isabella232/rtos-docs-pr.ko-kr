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
# <a name="chapter-3---usbx-dpump-class-considerations"></a><span data-ttu-id="c31a9-104">3장 - USBX DPUMP 클래스 고려 사항</span><span class="sxs-lookup"><span data-stu-id="c31a9-104">Chapter 3 - USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="c31a9-105">USBX에는 호스트 및 디바이스 측에 대한 **DPUMP** 클래스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31a9-105">USBX contains a **DPUMP** class for the host and device side.</span></span> <span data-ttu-id="c31a9-106">이 클래스는 자체의 표준 클래스가 아니라 두 개의 대량 파이프를 사용하고 이러한 두 파이프에서 데이터를 앞뒤로 전송하여 간단한 디바이스를 만드는 방법을 보여주는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="c31a9-106">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="c31a9-107">**DPUMP** 클래스를 사용하여 사용자 지정 클래스 또는 레거시 RS232 디바이스를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31a9-107">The **DPUMP** class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="c31a9-108">USB DPUMP 흐름 차트:</span><span class="sxs-lookup"><span data-stu-id="c31a9-108">USB DPUMP flow chart:</span></span>

![USB DPUMP 흐름 차트](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="c31a9-110">USBX DPUMP 디바이스 클래스</span><span class="sxs-lookup"><span data-stu-id="c31a9-110">USBX DPUMP Device Class</span></span>

<span data-ttu-id="c31a9-111">디바이스 **DPUMP** 클래스는 USB 호스트에 연결할 때 시작되는 스레드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c31a9-111">The device **DPUMP** class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="c31a9-112">스레드는 대량 출력 엔드포인트에서 들어오는 패킷을 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="c31a9-112">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="c31a9-113">패킷이 수신되면 콘텐츠를 대량 입력 엔드포인트 버퍼에 복사하고 이 엔드포인트에 트랜잭션을 게시하여 호스트가 이 엔드포인트에서 읽기 요청을 발행할 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="c31a9-113">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="c31a9-114">이렇게 하면 대량 출력 및 대량 입력 엔드포인트 간에 루프백 메커니즘이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31a9-114">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
