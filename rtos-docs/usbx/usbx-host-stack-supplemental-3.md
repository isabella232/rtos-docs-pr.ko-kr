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
# <a name="chapter-3-usbx-dpump-class-considerations"></a>3장: USBX DPUMP 클래스 고려 사항

USBX에는 호스트 및 디바이스 측에 대한 DPUMP 클래스가 포함되어 있습니다. 이 클래스는 자체의 표준 클래스가 아니라 두 개의 대량 파이프를 사용하고 이러한 두 파이프에서 데이터를 앞뒤로 전송하여 간단한 디바이스를 만드는 방법을 보여주는 예제입니다. DPUMP 클래스를 사용하여 사용자 지정 클래스 또는 레거시 RS232 디바이스를 시작할 수 있습니다.

USB DPUMP 흐름 차트:

![USB DPUMP 흐름 차트](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a>USBX DPUMP 호스트 클래스

DPUMP 클래스의 호스트 쪽에는 데이터 전송과 데이터 수신의 두 가지 함수가 있습니다.

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

두 함수는 모두 더 쉽게 DPUMP 애플리케이션을 만들기 위해 차단됩니다. 두 파이프(IN 및 OUT)를 동시에 실행해야 하는 경우 애플리케이션은 전송 스레드와 수신 스레드를 만들어야 합니다.

쓰기 함수의 프로토타입은 다음과 같습니다.

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

위치:

- dpump는 클래스의 인스턴스입니다.
- data_pointer는 보낼 버퍼에 대한 포인터입니다.
- requested_length는 전송할 길이입니다.
- actual_length는 성공적으로 또는 부분적으로 전송 완료 후 전송된 길이입니다.

수신 함수의 프로토타입은 비슷합니다.

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

다음은 애플리케이션이 디바이스 쪽에 패킷을 쓰고 수신 시 동일한 패킷을 수신하는 호스트 DPUMP 클래스의 예입니다.

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

## <a name="usbx-dpump-device-class"></a>USBX DPUMP 디바이스 클래스

디바이스 DPUMP 클래스는 USB 호스트에 연결할 때 시작되는 스레드를 사용합니다. 스레드는 대량 출력 엔드포인트에서 들어오는 패킷을 대기합니다. 패킷이 수신되면 콘텐츠를 대량 입력 엔드포인트 버퍼에 복사하고 이 엔드포인트에 트랜잭션을 게시하여 호스트가 이 엔드포인트에서 읽기 요청을 발행할 때까지 대기합니다. 이렇게 하면 대량 출력 및 대량 입력 엔드포인트 간에 루프백 메커니즘이 제공됩니다.
