---
title: 6장 - USBX CDC-ECM 클래스 사용법
description: USBX에는 호스트 및 디바이스 측에 대한 CDC-ECM 클래스가 포함되어 있습니다. 이 클래스는 NetX에서 사용하도록 설계되었으며, 특히 USBX CDC-ECM 클래스는 NetX용 드라이버 역할을 합니다. 이것이 5장에 나열된 CDC-ECM API가 없는 이유입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 18e7e075788623916de36cf911597230295b56c5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813254"
---
# <a name="chapter-6---usbx-cdc-ecm-class-usage"></a><span data-ttu-id="7b3aa-105">6장 - USBX CDC-ECM 클래스 사용법</span><span class="sxs-lookup"><span data-stu-id="7b3aa-105">Chapter 6 - USBX CDC-ECM Class Usage</span></span>

<span data-ttu-id="7b3aa-106">USBX에는 호스트 및 디바이스 측에 대한 CDC-ECM 클래스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3aa-106">USBX contains a CDC-ECM class for the host and device side.</span></span> <span data-ttu-id="7b3aa-107">이 클래스는 NetX에서 사용하도록 설계되었으며, 특히 USBX CDC-ECM 클래스는 NetX용 드라이버 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3aa-107">This class is designed to be used with NetX, specifically, the USBX CDC-ECM class acts as the driver for NetX.</span></span> <span data-ttu-id="7b3aa-108">이것이 5장에 나열된 CDC-ECM API가 없는 이유입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3aa-108">This is why there are no CDC-ECM APIs listed in Chapter 5.</span></span>

<span data-ttu-id="7b3aa-109">NetX 및 USBX가 초기화되고 USBX에서 CDC-ECM 디바이스의 인스턴스를 찾으면 애플리케이션은 NetX만 사용하여 디바이스와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3aa-109">Once NetX and USBX are initialized and an instance of a CDC-ECM device is found by USBX, the application exclusively uses NetX to communicate with the device.</span></span> <span data-ttu-id="7b3aa-110">초기화는 아래 예제에 표시된 패턴을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3aa-110">Initialization follows the pattern shown in the example below.</span></span>

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
