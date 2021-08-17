---
title: USBX OTG
description: USBX는 하드웨어 디자인에서 OTG 규격 USB 컨트롤러를 사용할 수 있는 경우에 USB의 OTG 기능을 지원합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bb9a0b98ed3f843ee690dfe419a3684562f1255e6839ddb06ded9d8f6023adcc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798268"
---
# <a name="chapter-5-usbx-otg"></a>5장: USBX OTG

USBX는 하드웨어 디자인에서 OTG 규격 USB 컨트롤러를 사용할 수 있는 경우에 USB의 OTG 기능을 지원합니다.

USBX는 코어 USB 스택의 OTG를 지원합니다. 그러나 OTG가 작동하려면 특정 USB 컨트롤러가 필요합니다. ***usbx_otg*** 디렉터리에서 USBX OTG 컨트롤러 함수를 찾을 수 있습니다. 현재 USBX 버전은 전체 OTG 기능을 갖춘 NXP LPC3131을 지원합니다.

일반 컨트롤러 드라이버 기능(호스트 또는 디바이스)은 표준 USBX usbx_device_controllers 및 usbx_host_controllers에도 있지만 ***usbx_otg*** 디렉터리에는 USB 컨트롤러와 연결된 특정 OTG 기능이 포함되어 있습니다.

OTG 컨트롤러에는 일반적인 호스트/디바이스 함수 외에도 네 가지 범주의 함수가 있습니다.

- VBUS 특정 함수
- 컨트롤러 시작 및 중지
- USB 역할 관리자
- 인터럽트 처리기

## <a name="vbus-functions"></a>VBUS 함수

각 컨트롤러에는 전원 관리 요구 사항에 따라 VBUS의 상태를 변경하는 VBUS 관리자가 있어야 합니다. 일반적으로 이 함수는 VBUS 켜기 또는 끄기를 수행합니다.

## <a name="start-and-stop-the-controller"></a>컨트롤러 시작 및 중지

일반 USB 구현과 달리 OTG에서는 역할이 변경될 때 호스트 및/또는 디바이스 스택을 활성화하고 비활성화해야 합니다.

## <a name="usb-role-manager"></a>USB 역할 관리자

USB 역할 관리자는 USB 상태를 변경하는 명령을 수신합니다. 아래 표에 지정된 대로 전환해야 하는 여러 가지 상태가 있습니다.

| 주                    | 값 | Description                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| UX_OTG_IDLE            | 0     | 디바이스가 유휴 상태입니다. 어떤 항목에도 연결되지 않음 |
| UX_OTG_IDLE_TO_HOST  | 1     | 디바이스가 A 형식 커넥터로 연결됨             |
| UX_OTG_IDLE_TO_SLAVE | 2     | 디바이스가 B 형식 커넥터로 연결됨             |
| UX_OTG_HOST_TO_IDLE  | 3     | 호스트 디바이스의 연결 끊김                          |
| UX_OTG_HOST_TO_SLAVE | 4     | 호스트에서 슬레이브로 역할 전환                          |
| UX_OTG_SLAVE_TO_IDLE | 5     | 슬레이브 디바이스의 연결 끊김                          |
| UX_OTG_SLAVE_TO_HOST | 6     | 슬레이브에서 호스트로 역할 전환                          |

## <a name="interrupt-handlers"></a>인터럽트 처리기

OTG용 호스트 및 디바이스 컨트롤러 드라이버는 SRP 및 VBUS로 인한 특정 신호에서 기존 USB 인터럽트를 벗어나 신호를 모니터링하는 데 다른 인터럽트 처리기가 필요합니다.

USB OTG 컨트롤러를 초기화하는 방법 여기서는 NXP LPC3131을 예제로 사용합니다.

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

이 예제에서는 VBUS 함수 및 모드 변경에 대한 콜백(호스트에서 슬레이브로 또는 그 반대로)을 전달하여 OTG 모드에서 LPC3131을 초기화합니다.

콜백 함수는 단순히 새 모드를 기록하고 보류 중인 스레드의 절전 모드를 해제하여 새 상태를 작동시켜야 합니다.

```C
void tx_demo_change_mode_callback(ULONG mode)
{
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

전달되는 모드 값은 다음 값을 가질 수 있습니다.

- UX_OTG_MODE_IDLE
- UX_OTG_MODE_SLAVE
- UX_OTG_MODE_HOST

애플리케이션은 변수를 조회하여 디바이스가 무엇인지 확인할 수 있습니다.

```C
ux_system_otg ->ux_system_otg_device_type
```

다음 값 중 하나일 수 있습니다.

- UX_OTG_DEVICE_A
- UX_OTG_DEVICE_B
- UX_OTG_DEVICE_IDLE

USB OTG 호스트 디바이스는 해당 명령을 실행하여 언제든지 역할 교체를 요청할 수 있습니다.

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */

ux_host_stack_role_swap(storage ->ux_host_class_storage_device);
```

슬레이브 디바이스에는 발급할 명령이 없지만 슬레이브 디바이스는 역할을 변경할 수 있는 상태를 설정할 수 있습니다. 이 역할은 호스트에서 GET_STATUS를 발급하고 교환이 시작될 때 선택됩니다.

```C
/* We are a B device, ask for role swap. The next GET_STATUS from the host will get the status change and do the HNP. */

ux_system_otg ->ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
