---
title: 6장 - USBX CDC-ECM 클래스 사용법
description: USBX에는 호스트 및 디바이스 측에 대한 CDC-ECM 클래스가 포함되어 있습니다. 이 클래스는 NetX에서 사용하도록 설계되었으며, 특히 USBX CDC-ECM 클래스는 NetX용 드라이버 역할을 합니다. 이것이 5장에 나열된 CDC-ECM API가 없는 이유입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 7328b8c3537acac1ef02fced32b0c2731065aea0c6e2742a96f0644e9a8045f0
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798353"
---
# <a name="chapter-6---usbx-cdc-ecm-class-usage"></a>6장 - USBX CDC-ECM 클래스 사용법

USBX에는 호스트 및 디바이스 측에 대한 CDC-ECM 클래스가 포함되어 있습니다. 이 클래스는 NetX에서 사용하도록 설계되었으며, 특히 USBX CDC-ECM 클래스는 NetX용 드라이버 역할을 합니다. 이것이 5장에 나열된 CDC-ECM API가 없는 이유입니다.

NetX 및 USBX가 초기화되고 USBX에서 CDC-ECM 디바이스의 인스턴스를 찾으면 애플리케이션은 NetX만 사용하여 디바이스와 통신합니다. 초기화는 아래 예제에 표시된 패턴을 따릅니다.

```c
UINT status;

/* The USB controller should be the last component initialized so that
everything is ready when data starts being received. */

/* Initialize USBX. */

ux_system_initialize(memory_pointer, UX_USBX_MEMORY_SIZE, UX_NULL, 0);

/* The code below is required for installing the host portion of USBX */
status = ux_host_stack_initialize(UX_NULL);

/* Register cdc_ecm class. */

status = ux_host_stack_class_register(_ux_system_host_class_cdc_ecm_name,
    ux_host_class_cdc_ecm_entry);

/* Perform the initialization of the network driver. */

_ux_network_driver_init();

/* Initialize NetX. Refer to NetX user guide for details to add initialization code. */

/* Register the platform-specific USB controller. */

status = ux_host_stack_hcd_register("controller_name", controller_entry, param1, param2);

/* Find the CDC-ECM class. */
class_cdc_ecm_get();

/* Now wait for the link to be up. */

while (cdc_ecm -> ux_host_class_cdc_ecm_link_state != UX_HOST_CLASS_CDC_ECM_LINK_STATE_UP)
    tx_thread_sleep(10);

/* At this point, everything has been initialized, and we've found a CDC-ECM device.
    Now NetX can be used to communicate with the device. */
```
