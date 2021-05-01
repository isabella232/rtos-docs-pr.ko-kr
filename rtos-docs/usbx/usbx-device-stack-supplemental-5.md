---
title: 5장 - USBX OTG
description: OTG 호환 USB 컨트롤러를 하드웨어 설계에서 사용할 수 있는 경우 USBX가 USB의 OTG 기능을 어떻게 지원하는지 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 64a3c44f84b9ffca31d9e616d14d3d5d87c56bd7
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550323"
---
# <a name="chapter-5---usbx-otg"></a><span data-ttu-id="b9a6e-103">5장 - USBX OTG</span><span class="sxs-lookup"><span data-stu-id="b9a6e-103">Chapter 5 - USBX OTG</span></span>

<span data-ttu-id="b9a6e-104">USBX는 하드웨어 디자인에서 OTG 규격 USB 컨트롤러를 사용할 수 있는 경우에 USB의 OTG 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-104">USBX supports the OTG functionalities of USB when an OTG compliant USB controller is available in the hardware design.</span></span>

<span data-ttu-id="b9a6e-105">USBX는 코어 USB 스택의 OTG를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-105">USBX supports OTG in the core USB stack.</span></span> <span data-ttu-id="b9a6e-106">그러나 OTG가 작동하려면 특정 USB 컨트롤러가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-106">But for OTG to function, it requires a specific USB controller.</span></span> <span data-ttu-id="b9a6e-107">usbx_otg 디렉터리에서 USBX OTG 컨트롤러 함수를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-107">USBX OTG controller functions can be found in the usbx_otg directory.</span></span> <span data-ttu-id="b9a6e-108">현재 USBX 버전은 전체 OTG 기능을 갖춘 NXP LPC3131을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-108">The current USBX version only supports the NXP LPC3131 with full OTG capabilities.</span></span>

<span data-ttu-id="b9a6e-109">일반 컨트롤러 드라이버 기능(호스트 또는 디바이스)은 표준 USBX usbx_device_controllers 및 usbx_host_controllers에도 있지만 usbx_otg 디렉터리에는 USB 컨트롤러와 연결된 특정 OTG 기능이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-109">The regular controller driver functions (host or device) can still be found in the standard USBX usbx_device_controllers and usbx_host_controllers but the usbx_otg directory contains the specific OTG functions associated with the USB controller.</span></span>

<span data-ttu-id="b9a6e-110">OTG 컨트롤러에는 일반적인 호스트/디바이스 함수 외에도 네 가지 범주의 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-110">There are four categories of functions for an OTG controller in addition to the usual host/device functions.</span></span>

- <span data-ttu-id="b9a6e-111">VBUS 특정 함수</span><span class="sxs-lookup"><span data-stu-id="b9a6e-111">VBUS specific functions</span></span>
- <span data-ttu-id="b9a6e-112">컨트롤러 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="b9a6e-112">Start and Stop of the controller</span></span>
- <span data-ttu-id="b9a6e-113">USB 역할 관리자</span><span class="sxs-lookup"><span data-stu-id="b9a6e-113">USB role manager</span></span>
- <span data-ttu-id="b9a6e-114">인터럽트 처리기</span><span class="sxs-lookup"><span data-stu-id="b9a6e-114">Interrupt handlers</span></span>

## <a name="vbus-functions"></a><span data-ttu-id="b9a6e-115">VBUS 함수</span><span class="sxs-lookup"><span data-stu-id="b9a6e-115">VBUS functions</span></span>

<span data-ttu-id="b9a6e-116">각 컨트롤러에는 전원 관리 요구 사항에 따라 VBUS의 상태를 변경하는 VBUS 관리자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-116">Each controller needs to have a VBUS manager to change the state of VBUS based on power management requirements.</span></span> <span data-ttu-id="b9a6e-117">일반적으로 이 함수는 VBUS 켜기 또는 끄기를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-117">Usually, this function only performs turning on or off VBUS.</span></span>

## <a name="start-and-stop-the-controller"></a><span data-ttu-id="b9a6e-118">컨트롤러 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="b9a6e-118">Start and Stop the controller</span></span>

<span data-ttu-id="b9a6e-119">일반 USB 구현과 달리 OTG에서는 역할이 변경될 때 호스트 및/또는 디바이스 스택을 활성화하고 비활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-119">Unlike a regular USB implementation, OTG requires the host and/or the device stack to be activated and deactivated when the role changes.</span></span>

## <a name="usb-role-manager"></a><span data-ttu-id="b9a6e-120">USB 역할 관리자</span><span class="sxs-lookup"><span data-stu-id="b9a6e-120">USB role Manager</span></span>

<span data-ttu-id="b9a6e-121">USB 역할 관리자는 USB 상태를 변경하는 명령을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-121">The USB role manager receives commands to change the state of the USB.</span></span> <span data-ttu-id="b9a6e-122">다음과 같이 전환해야 하는 여러 가지 상태가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-122">There are several states that need transitions to and from:</span></span>

| <span data-ttu-id="b9a6e-123">주</span><span class="sxs-lookup"><span data-stu-id="b9a6e-123">State</span></span>                    | <span data-ttu-id="b9a6e-124">값</span><span class="sxs-lookup"><span data-stu-id="b9a6e-124">Value</span></span> | <span data-ttu-id="b9a6e-125">Description</span><span class="sxs-lookup"><span data-stu-id="b9a6e-125">Description</span></span>                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| <span data-ttu-id="b9a6e-126">UX_OTG_IDLE</span><span class="sxs-lookup"><span data-stu-id="b9a6e-126">UX_OTG_IDLE</span></span>            | <span data-ttu-id="b9a6e-127">0</span><span class="sxs-lookup"><span data-stu-id="b9a6e-127">0</span></span>     | <span data-ttu-id="b9a6e-128">디바이스가 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-128">The device is Idle.</span></span> <span data-ttu-id="b9a6e-129">어떤 항목에도 연결되지 않음</span><span class="sxs-lookup"><span data-stu-id="b9a6e-129">Not connected to anything</span></span> |
| <span data-ttu-id="b9a6e-130">UX_OTG_IDLE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="b9a6e-130">UX_OTG_IDLE_TO_HOST</span></span>  | <span data-ttu-id="b9a6e-131">1</span><span class="sxs-lookup"><span data-stu-id="b9a6e-131">1</span></span>     | <span data-ttu-id="b9a6e-132">디바이스가 A 형식 커넥터로 연결됨</span><span class="sxs-lookup"><span data-stu-id="b9a6e-132">Device is connected with type A connector</span></span>             |
| <span data-ttu-id="b9a6e-133">UX_OTG_IDLE_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="b9a6e-133">UX_OTG_IDLE_TO_SLAVE</span></span> | <span data-ttu-id="b9a6e-134">2</span><span class="sxs-lookup"><span data-stu-id="b9a6e-134">2</span></span>     | <span data-ttu-id="b9a6e-135">디바이스가 B 형식 커넥터로 연결됨</span><span class="sxs-lookup"><span data-stu-id="b9a6e-135">Device is connected with type B connector</span></span>             |
| <span data-ttu-id="b9a6e-136">UX_OTG_HOST_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="b9a6e-136">UX_OTG_HOST_TO_IDLE</span></span>  | <span data-ttu-id="b9a6e-137">3</span><span class="sxs-lookup"><span data-stu-id="b9a6e-137">3</span></span>     | <span data-ttu-id="b9a6e-138">호스트 디바이스의 연결 끊김</span><span class="sxs-lookup"><span data-stu-id="b9a6e-138">Host device got disconnected</span></span>                          |
| <span data-ttu-id="b9a6e-139">UX_OTG_HOST_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="b9a6e-139">UX_OTG_HOST_TO_SLAVE</span></span> | <span data-ttu-id="b9a6e-140">4</span><span class="sxs-lookup"><span data-stu-id="b9a6e-140">4</span></span>     | <span data-ttu-id="b9a6e-141">호스트에서 슬레이브로 역할 전환</span><span class="sxs-lookup"><span data-stu-id="b9a6e-141">Role swap from Host to Slave</span></span>                          |
| <span data-ttu-id="b9a6e-142">UX_OTG_SLAVE_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="b9a6e-142">UX_OTG_SLAVE_TO_IDLE</span></span> | <span data-ttu-id="b9a6e-143">5</span><span class="sxs-lookup"><span data-stu-id="b9a6e-143">5</span></span>     | <span data-ttu-id="b9a6e-144">슬레이브 디바이스의 연결 끊김</span><span class="sxs-lookup"><span data-stu-id="b9a6e-144">Slave device is disconnected</span></span>                          |
| <span data-ttu-id="b9a6e-145">UX_OTG_SLAVE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="b9a6e-145">UX_OTG_SLAVE_TO_HOST</span></span> | <span data-ttu-id="b9a6e-146">6</span><span class="sxs-lookup"><span data-stu-id="b9a6e-146">6</span></span>     | <span data-ttu-id="b9a6e-147">슬레이브에서 호스트로 역할 전환</span><span class="sxs-lookup"><span data-stu-id="b9a6e-147">Role swap from Slave to Host</span></span>                          |

## <a name="interrupt-handlers"></a><span data-ttu-id="b9a6e-148">인터럽트 처리기</span><span class="sxs-lookup"><span data-stu-id="b9a6e-148">Interrupt handlers</span></span>

<span data-ttu-id="b9a6e-149">OTG용 호스트 및 디바이스 컨트롤러 드라이버는 SRP 및 VBUS로 인한 특정 신호에서 기존 USB 인터럽트를 벗어나 신호를 모니터링하는 데 다른 인터럽트 처리기가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-149">Both host and device controller drivers for OTG needs different interrupt handlers to monitor signals beyond traditional USB interrupts, in particular signals due to SRP and VBUS.</span></span>

<span data-ttu-id="b9a6e-150">USB OTG 컨트롤러를 초기화하는 방법</span><span class="sxs-lookup"><span data-stu-id="b9a6e-150">How to initialize a USB OTG controller.</span></span> <span data-ttu-id="b9a6e-151">여기서는 NXP LPC3131을 예제로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-151">We use the NXP LPC3131 as an example here.</span></span>

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

<span data-ttu-id="b9a6e-152">이 예제에서는 VBUS 함수 및 모드 변경에 대한 콜백(호스트에서 슬레이브로 또는 그 반대로)을 전달하여 OTG 모드에서 LPC3131을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-152">In this example, we initialize the LPC3131 in OTG mode by passing a VBUS function and a callback for mode change (from host to slave or vice versa).</span></span>

<span data-ttu-id="b9a6e-153">콜백 함수는 단순히 새 모드를 기록하고 보류 중인 스레드의 절전 모드를 해제하여 새 상태를 작동시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-153">The callback function should simply record the new mode and wake up a pending thread to act up the new state.</span></span>

```C
void tx_demo_change_mode_callback(ULONG mode) {
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

<span data-ttu-id="b9a6e-154">전달되는 모드 값은 다음 값을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-154">The mode value that is passed can have the following values.</span></span>

- <span data-ttu-id="b9a6e-155">**UX_OTG_MODE_IDLE**</span><span class="sxs-lookup"><span data-stu-id="b9a6e-155">**UX_OTG_MODE_IDLE**</span></span>
- <span data-ttu-id="b9a6e-156">**UX_OTG_MODE_SLAVE**</span><span class="sxs-lookup"><span data-stu-id="b9a6e-156">**UX_OTG_MODE_SLAVE**</span></span>
- <span data-ttu-id="b9a6e-157">**UX_OTG_MODE_HOST**</span><span class="sxs-lookup"><span data-stu-id="b9a6e-157">**UX_OTG_MODE_HOST**</span></span>

<span data-ttu-id="b9a6e-158">애플리케이션은 변수를 조회하여 디바이스가 무엇인지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-158">The application can always check what the device is by looking at the variable:</span></span>

```C
_ux_system_otg -> ux_system_otg_device_type
```

<span data-ttu-id="b9a6e-159">해당 값은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-159">Its values can be any of the following.</span></span>

- <span data-ttu-id="b9a6e-160">**UX_OTG_DEVICE_A**</span><span class="sxs-lookup"><span data-stu-id="b9a6e-160">**UX_OTG_DEVICE_A**</span></span>
- <span data-ttu-id="b9a6e-161">**UX_OTG_DEVICE_B**</span><span class="sxs-lookup"><span data-stu-id="b9a6e-161">**UX_OTG_DEVICE_B**</span></span>
- <span data-ttu-id="b9a6e-162">**UX_OTG_DEVICE_IDLE**</span><span class="sxs-lookup"><span data-stu-id="b9a6e-162">**UX_OTG_DEVICE_IDLE**</span></span>

<span data-ttu-id="b9a6e-163">USB OTG 호스트 디바이스는 다음 명령을 실행하여 언제든지 역할 교체를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-163">A USB OTG host device can always ask for a role swap by issuing the following command.</span></span>

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */
ux_host_stack_role_swap(storage -> ux_host_class_storage_device);
```

<span data-ttu-id="b9a6e-164">슬레이브 디바이스에는 발급할 명령이 없지만 슬레이브 디바이스는 역할을 변경할 수 있는 상태를 설정할 수 있습니다. 이 역할은 호스트에서 **GET_STATUS** 를 발급하고 교환이 시작될 때 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9a6e-164">For a slave device, there is no command to issue but the slave device can set a state to change the role, which will be picked up by the host when it issues a **GET_STATUS** and the swap will then be initiated.</span></span>

```C
/* We are a B device, ask for role swap.
   The next GET_STATUS from the host will get the status change and do the HNP. */
_ux_system_otg -> ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
