---
title: USBX DPUMP 클래스 고려 사항
description: USBX에는 호스트 및 디바이스 측에 대한 DPUMP 클래스가 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9960b391418fa2f9203e761115bcba71cc3619e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812889"
---
# <a name="chapter-3-usbx-dpump-class-considerations"></a><span data-ttu-id="21711-103">3장: USBX DPUMP 클래스 고려 사항</span><span class="sxs-lookup"><span data-stu-id="21711-103">Chapter 3: USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="21711-104">USBX에는 호스트 및 디바이스 측에 대한 DPUMP 클래스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21711-104">USBX contains a DPUMP class for the host and device side.</span></span> <span data-ttu-id="21711-105">이 클래스는 자체의 표준 클래스가 아니라 두 개의 대량 파이프를 사용하고 이러한 두 파이프에서 데이터를 앞뒤로 전송하여 간단한 디바이스를 만드는 방법을 보여주는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="21711-105">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="21711-106">DPUMP 클래스를 사용하여 사용자 지정 클래스 또는 레거시 RS232 디바이스를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21711-106">The DPUMP class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="21711-107">USB DPUMP 흐름 차트:</span><span class="sxs-lookup"><span data-stu-id="21711-107">USB DPUMP flow chart:</span></span>

![USB DPUMP 흐름 차트](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a><span data-ttu-id="21711-109">USBX DPUMP 호스트 클래스</span><span class="sxs-lookup"><span data-stu-id="21711-109">USBX DPUMP Host Class</span></span>

<span data-ttu-id="21711-110">DPUMP 클래스의 호스트 쪽에는 데이터 전송과 데이터 수신의 두 가지 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21711-110">The host side of the DPUMP Class has two functions, one for sending data and one for receiving data:</span></span>

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

<span data-ttu-id="21711-111">두 함수는 모두 더 쉽게 DPUMP 애플리케이션을 만들기 위해 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="21711-111">Both functions are blocking to make the DPUMP application easier.</span></span> <span data-ttu-id="21711-112">두 파이프(IN 및 OUT)를 동시에 실행해야 하는 경우 애플리케이션은 전송 스레드와 수신 스레드를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="21711-112">If it is necessary to have both pipes (IN and OUT) running at the same time, the application will be required to create a transmit thread and a receive thread.</span></span>

<span data-ttu-id="21711-113">쓰기 함수의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="21711-113">The prototype for the writing function is as follows.</span></span>

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

<span data-ttu-id="21711-114">위치:</span><span class="sxs-lookup"><span data-stu-id="21711-114">Where:</span></span>

- <span data-ttu-id="21711-115">dpump는 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="21711-115">dpump is the instance of the class</span></span>
- <span data-ttu-id="21711-116">data_pointer는 보낼 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="21711-116">data_pointer is the pointer to the buffer to be sent</span></span>
- <span data-ttu-id="21711-117">requested_length는 전송할 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="21711-117">requested_length is the length to send</span></span>
- <span data-ttu-id="21711-118">actual_length는 성공적으로 또는 부분적으로 전송 완료 후 전송된 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="21711-118">actual_length is the length sent after completion of the transfer, either successfully or partially.</span></span>

<span data-ttu-id="21711-119">수신 함수의 프로토타입은 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="21711-119">The prototype for the receiving function is similar.</span></span>

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

<span data-ttu-id="21711-120">다음은 애플리케이션이 디바이스 쪽에 패킷을 쓰고 수신 시 동일한 패킷을 수신하는 호스트 DPUMP 클래스의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="21711-120">Here is an example of the host DPUMP class where an application writes a packet to the device side and receives the same packet on the reception:</span></span>

```C
/* We start with a 'A' in buffer. */
current_char = 'A';

while(1)
{
    /* Initialize the write buffer. */
    ux_utility_memory_set(out_buffer, current_char,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE);

    /* Increment the character in buffer. */
    current_char++;

    /* Check for upper alphabet limit. */
    if (current_char > 'Z')
        current_char = 'A';

    /* Write to the Data Pump Bulk out endpoint. */
    status = ux_host_class_dpump_write (dpump, out_buffer,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE,
        &actual_length);

    /* Verify that the status and the amount of data is correct. */
    if ((status == UX_SUCCESS) && actual_length == UX_HOST_CLASS_DPUMP_PACKET_SIZE)
    {
        /* Read to the Data Pump Bulk out endpoint. */
        status = ux_host_class_dpump_read (dpump, in_buffer,
            UX_HOST_CLASS_DPUMP_PACKET_SIZE, &actual_length);
    }
}
```

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="21711-121">USBX DPUMP 디바이스 클래스</span><span class="sxs-lookup"><span data-stu-id="21711-121">USBX DPUMP Device Class</span></span>

<span data-ttu-id="21711-122">디바이스 DPUMP 클래스는 USB 호스트에 연결할 때 시작되는 스레드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="21711-122">The device DPUMP class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="21711-123">스레드는 대량 출력 엔드포인트에서 들어오는 패킷을 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="21711-123">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="21711-124">패킷이 수신되면 콘텐츠를 대량 입력 엔드포인트 버퍼에 복사하고 이 엔드포인트에 트랜잭션을 게시하여 호스트가 이 엔드포인트에서 읽기 요청을 발행할 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="21711-124">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="21711-125">이렇게 하면 대량 출력 및 대량 입력 엔드포인트 간에 루프백 메커니즘이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="21711-125">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
