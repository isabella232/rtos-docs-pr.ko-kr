---
title: 챕터 2 - USBX 디바이스 클래스 고려 사항
description: USB 디바이스 RNDIS 클래스를 사용하면 USB 호스트 시스템이 이더넷 디바이스로 디바이스와 통신할 수 있습니다. 이 클래스는 Microsoft 독점 구현을 기반으로 하며 Windows 플랫폼에만 적용됩니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 035492644a911eba3b1c62a79572bc7d4c55f6dd
ms.sourcegitcommit: 1aeca2f91960856d8cc24fef65f909639e527599
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082220"
---
# <a name="chapter-2---usbx-device-class-considerations"></a><span data-ttu-id="67ce7-104">챕터 2 - USBX 디바이스 클래스 고려 사항</span><span class="sxs-lookup"><span data-stu-id="67ce7-104">Chapter 2 - USBX Device Class Considerations</span></span>

## <a name="usb-device-rndis-class"></a><span data-ttu-id="67ce7-105">USB 디바이스 RNDIS 클래스</span><span class="sxs-lookup"><span data-stu-id="67ce7-105">USB Device RNDIS Class</span></span>

<span data-ttu-id="67ce7-106">USB 디바이스 RNDIS 클래스를 사용하면 USB 호스트 시스템이 이더넷 디바이스로 디바이스와 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-106">The USB device RNDIS class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="67ce7-107">이 클래스는 Microsoft 독점 구현을 기반으로 하며 Windows 플랫폼에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-107">This class is based on the Microsoft proprietary implementation and is specific to Windows platforms.</span></span>

<span data-ttu-id="67ce7-108">디바이스 스택에서 RNDIS 규격 디바이스 프레임워크를 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-108">A RNDIS compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="67ce7-109">아래에서 예제를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-109">An example is found below.</span></span>

```C
unsigned char device_framework_full_speed[] = {
    /* VID: 0x04b4
    PID: 0x1127
    */

    /* Device Descriptor */
    0x12, /* bLength */
    0x01, /* bDescriptorType */
    0x10, 0x01, /* bcdUSB */
    0x02, /* bDeviceClass - CDC */
    0x00, /* bDeviceSubClass */
    0x00, /* bDeviceProtocol */
    0x40, /* bMaxPacketSize0 */
    0xb4, 0x04, /* idVendor */
    0x27, 0x11, /* idProduct */
    0x00, 0x01, /* bcdDevice */
    0x01, /* iManufacturer */
    0x02, /* iProduct */
    0x03, /* iSerialNumber */
    0x01, /* bNumConfigurations */

    /* Configuration Descriptor */
    0x09, /* bLength */
    0x02, /* bDescriptorType */
    0x38, 0x00, /* wTotalLength */
    0x02, /* bNumInterfaces */
    0x01, /* bConfigurationValue */
    0x00, /* iConfiguration */
    0x40, /* bmAttributes - Self-powered */
    0x00, /* bMaxPower */

    /* Interface Association Descriptor */
    0x08, /* bLength */
    0x0b, /* bDescriptorType */
    0x00, /* bFirstInterface */
    0x02, /* bInterfaceCount */
    0x02, /* bFunctionClass - CDC - Communication */
    0xff, /* bFunctionSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bFunctionProtocol - No class specific protocol required */
    0x00, /* iFunction */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x00, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x01, /* bNumEndpoints */
    0x02, /* bInterfaceClass - CDC - Communication */
    0xff, /* bInterfaceSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x83, /* bEndpointAddress */
    0x03, /* bmAttributes - Interrupt */
    0x08, 0x00, /* wMaxPacketSize */
    0xff, /* bInterval */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x01, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x02, /* bNumEndpoints */
    0x0a, /* bInterfaceClass - CDC - Data */
    0x00, /* bInterfaceSubClass - Should be 0x00 */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x02, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x81, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */
};
```

<span data-ttu-id="67ce7-110">RNDIS 클래스는 CDC-ACM 및 CDC-ECM과 매우 유사한 디바이스 설명자 방법을 사용하며 IAD 설명자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-110">The RNDIS class uses a very similar device descriptor approach to the CDC-ACM and CDC-ECM and also requires a IAD descriptor.</span></span> <span data-ttu-id="67ce7-111">디바이스 설명자에 대한 정의 및 요구 사항은 CDC-ACM 클래스를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="67ce7-111">See the CDC-ACM class for definition and requirements for the device descriptor.</span></span>

<span data-ttu-id="67ce7-112">RNDIS 클래스의 활성화는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-112">The activation of the RNDIS class is as follows.</span></span>

```C
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/

parameter.ux_slave_class_rndis_instance_activate = UX_NULL;
parameter.ux_slave_class_rndis_instance_deactivate = UX_NULL;

/* Define a local NODE ID. */

parameter.ux_slave_class_rndis_parameter_local_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_local_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_local_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_local_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_local_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */

parameter.ux_slave_class_rndis_parameter_remote_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_remote_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_remote_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_remote_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_remote_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_remote_node_id[5] = 0x79;

/* Set extra parameters used by the RNDIS query command with certain OIDs. */

parameter.ux_slave_class_rndis_parameter_vendor_id = 0x04b4 ;
parameter.ux_slave_class_rndis_parameter_driver_version = 0x1127;
ux_utility_memory_copy(parameter.ux_slave_class_rndis_parameter_vendor_description,
    "ELOGIC RNDIS", 12);

/* Initialize the device rndis class. This class owns both interfaces. */
status = ux_device_stack_class_register(_ux_system_slave_class_rndis_name,
    ux_device_class_rndis_entry, 1,0, &parameter);
```

<span data-ttu-id="67ce7-113">CDC-ECM과 마찬가지로 RNDIS 클래스에는 로컬 및 원격인 2개의 노드가 필요하지만 원격 노드를 설명하는 문자열 설명자를 가질 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-113">As for the CDC-ECM, the RNDIS class requires 2 nodes, one local and one remote but there is no requirement to have a string descriptor describing the remote node.</span></span>

<span data-ttu-id="67ce7-114">그러나 Microsoft 독점 메시징 메커니즘으로 인해 몇 가지 추가 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-114">However due to Microsoft proprietary messaging mechanism, some extra parameters are required.</span></span> <span data-ttu-id="67ce7-115">먼저 공급업체 ID를 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-115">First the vendor ID has to be passed.</span></span> <span data-ttu-id="67ce7-116">마찬가지로, RNDIS의 드라이버 버전을 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-116">Likewise, the driver version of the RNDIS.</span></span> <span data-ttu-id="67ce7-117">공급업체 문자열도 주어져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-117">A vendor string must also be given.</span></span>

<span data-ttu-id="67ce7-118">RNDIS 클래스에는 두 방법 모두로 데이터를 전송할 수 있는 기본 제공 API가 있지만 사용자 애플리케이션이 NetX를 통해 USB 이더넷 디바이스와 통신하기 때문에 해당 API는 애플리케이션에서 숨겨져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-118">The RNDIS class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="67ce7-119">USBX RNDIS 클래스는 Azure RTOS NetX 네트워크 스택에 긴밀히 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-119">The USBX RNDIS class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="67ce7-120">NetX 및 USBX RNDIS 클래스를 모두 사용하는 애플리케이션은 일반적인 방식으로 NetX 네트워크 스택을 활성화하지만 USB 네트워크 스택도 다음과 같이 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-120">An application using both NetX and USBX RNDIS class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="67ce7-121">USB 네트워크 스택은 한 번만 활성화하면 되며 RNDIS에 국한되지 않고 NetX 서비스를 필요로 하는 모든 USB 클래스에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-121">The USB network stack needs to be activated only once and is not specific to RNDIS but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="67ce7-122">RNDIS 클래스는 Microsoft 운영 체제 전용이므로 MAC OS 및 Linux 호스트에서 인식되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-122">The RNDIS class will not be recognized by MAC OS and Linux hosts as it is specific to Microsoft operating systems.</span></span> <span data-ttu-id="67ce7-123">Windows 플랫폼에서 디바이스 설명자와 일치하는 호스트에 .inf 파일이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-123">On windows platforms a .inf file needs to be present on the host that matches the device descriptor.</span></span> <span data-ttu-id="67ce7-124">Microsoft에서 RNDIS 클래스용 템플릿이 제공되며 usbx_windows_host_files 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-124">Microsoft supplies a template for the RNDIS class and it can be found in the usbx_windows_host_files directory.</span></span> <span data-ttu-id="67ce7-125">최신 버전의 Windows의 경우 RNDIS_Template.inf 파일을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-125">For more recent version of Windows the file RNDIS_Template.inf should be used.</span></span> <span data-ttu-id="67ce7-126">디바이스에서 사용하는 PID/VID에 맞게 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-126">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="67ce7-127">회사와 제품이 USB-IF를 사용하여 등록된 경우 PID/VID는 최종 고객에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-127">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="67ce7-128">inf 파일에서 수정할 필드는 아래에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-128">In the inf file, the fields to modify are located here.</span></span>

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

<span data-ttu-id="67ce7-129">RNDIS 디바이스의 디바이스 프레임워크에서 PID/VID는 디바이스 설명자에 저장됩니다(위에서 명시된 디바이스 설명자 참조).</span><span class="sxs-lookup"><span data-stu-id="67ce7-129">In the device framework of the RNDIS device, the PID/VID are stored in the device descriptor (see the device descriptor declared above)</span></span>

<span data-ttu-id="67ce7-130">USB 호스트 시스템은 USB RNDIS 디바이스를 검색할 때 네트워크 인터페이스를 탑재하고 디바이스를 네트워크 프로토콜 스택과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-130">When a USB host systems discovers the USB RNDIS device, it will mount a network interface and the device can be used with network protocol stack.</span></span> <span data-ttu-id="67ce7-131">호스트 운영 체제를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="67ce7-131">See the host Operating System for reference.</span></span>

## <a name="usb-device-dfu-class"></a><span data-ttu-id="67ce7-132">USB 디바이스 DFU 클래스</span><span class="sxs-lookup"><span data-stu-id="67ce7-132">USB Device DFU Class</span></span>

<span data-ttu-id="67ce7-133">USB 디바이스 DFU 클래스를 사용 하면 USB 호스트 시스템에서 호스트 애플리케이션을 기반으로 디바이스 펌웨어를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-133">The USB device DFU class allows for a USB host system to update the device firmware based on a host application.</span></span> <span data-ttu-id="67ce7-134">DFU 클래스는 USB IF 표준 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-134">The DFU class is a USB-IF standard class.</span></span>

<span data-ttu-id="67ce7-135">USBX DFU 클래스는 비교적 단순합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-135">USBX DFU class is relatively simple.</span></span> <span data-ttu-id="67ce7-136">디바이스 설명자에는 컨트롤 끝점을 제외한 아무것도 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-136">It device descriptor does not require anything but a control endpoint.</span></span> <span data-ttu-id="67ce7-137">대부분의 경우 이 클래스는 USB 복합 디바이스에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-137">Most of the time, this class will be embedded into a USB composite device.</span></span> <span data-ttu-id="67ce7-138">디바이스는 저장 디바이스 또는 통신 디바이스와 같은 무엇이든, 추가된 DFU 인터페이스는 디바이스의 펌웨어가 즉시 업데이트될 수 있음을 호스트에 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-138">The device can be anything such as a storage device or a comm device and the added DFU interface can inform the host that the device can have its firmware updated on the fly.</span></span>

<span data-ttu-id="67ce7-139">DFU 클래스는 세 단계로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-139">The DFU class works in 3 steps.</span></span> <span data-ttu-id="67ce7-140">먼저 내보낸 클래스를 사용하여 디바이스를 정상적으로 탑재합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-140">First the device mounts as normal using the class exported.</span></span> <span data-ttu-id="67ce7-141">호스트(Windows 또는 Linux)의 애플리케이션은 DFU 클래스를 실행하고 디바이스를 DFU 모드로 다시 설정하는 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-141">An application on the host (Windows or Linux) will exercise the DFU class and send a request to reset the device into DFU mode.</span></span> <span data-ttu-id="67ce7-142">디바이스는 짧은 시간 동안(호스트와 디바이스에서 다시 설정 시퀀스를 검색하는 데 충분한) 버스에서 사라지지만, 다시 시작될 때 호스트 애플리케이션이 펌웨어 업그레이드를 보낼 때까지 대기하면서 디바이스는 DFU 모드에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-142">The device will disappear from the bus for a short time (enough for the host and the device to detect a RESET sequence) and upon restarting, the device will be exclusively in DFU mode, waiting for the host application to send a firmware upgrade.</span></span> <span data-ttu-id="67ce7-143">펌웨어 업그레이드가 완료되면 호스트 애플리케이션이 디바이스를 다시 설정하고, 다시 열거하면 디바이스는 새 펌웨어를 사용하여 정상적인 작업으로 되돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-143">When the firmware upgrade has been completed, the host application resets the device and upon re-enumeration the device will revert to its normal operation with the new firmware.</span></span>

<span data-ttu-id="67ce7-144">DFU 디바이스 프레임 워크는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-144">A DFU device framework will look like this.</span></span>

```C
UCHAR device_framework_full_speed[] = {

    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x40,
    0x99, 0x99, 0x00, 0x00, 0x00, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x1b, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor for DFU. */
    0x09, 0x04, 0x00, 0x00, 0x00, 0xFE, 0x01, 0x01, 0x00,

    /* Functional descriptor for DFU. */
    0x09, 0x21, 0x0f, 0xE8, 0x03, 0x40, 0x00, 0x00,
    0x01,

};
```

<span data-ttu-id="67ce7-145">이 예제에서 DFU 설명자는 다른 클래스와 연결되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-145">In this example, the DFU descriptor is not associated with any other classes.</span></span> <span data-ttu-id="67ce7-146">여기에는 단순 인터페이스 설명자가 있으며 다른 끝점이 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-146">It has a simple interface descriptor and no other endpoints attached to it.</span></span> <span data-ttu-id="67ce7-147">디바이스의 DFU 기능에 대한 세부 정보를 설명하는 기능 설명자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-147">There is a Functional descriptor that describes the specifics of the DFU capabilities of the device.</span></span>

<span data-ttu-id="67ce7-148">DFU 기능에 대한 설명은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-148">The description of the DFU capabilities are as follows.</span></span>

| <span data-ttu-id="67ce7-149">이름</span><span class="sxs-lookup"><span data-stu-id="67ce7-149">Name</span></span>             | <span data-ttu-id="67ce7-150">Offset</span><span class="sxs-lookup"><span data-stu-id="67ce7-150">Offset</span></span>  | <span data-ttu-id="67ce7-151">크기</span><span class="sxs-lookup"><span data-stu-id="67ce7-151">Size</span></span> | <span data-ttu-id="67ce7-152">type</span><span class="sxs-lookup"><span data-stu-id="67ce7-152">type</span></span>      | <span data-ttu-id="67ce7-153">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-153">Description</span></span> |
|------------------|----------|------|-----------|------------|
| <span data-ttu-id="67ce7-154">bmAttributes</span><span class="sxs-lookup"><span data-stu-id="67ce7-154">bmAttributes</span></span>  | <span data-ttu-id="67ce7-155">2</span><span class="sxs-lookup"><span data-stu-id="67ce7-155">2</span></span>     | <span data-ttu-id="67ce7-156">1</span><span class="sxs-lookup"><span data-stu-id="67ce7-156">1</span></span>   | <span data-ttu-id="67ce7-157">비트 필드</span><span class="sxs-lookup"><span data-stu-id="67ce7-157">Bit field</span></span> | <span data-ttu-id="67ce7-158">비트 3: 디바이스는 DFU_DETACH 요청을 받을 때 버스 분리-연결 시퀀스를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-158">Bit 3: device will perform a bus detach-attach sequence when it receives a DFU_DETACH request.</span></span> <span data-ttu-id="67ce7-159">호스트에서 USB 재설정을 실행해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-159">The host must not issue a USB Reset.</span></span> <span data-ttu-id="67ce7-160">(bitWillDetach) 0 = 아니요 1 = 예 비트 2: 디바이스가 매니페스트 단계 이후에 USB를 통해 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-160">(bitWillDetach) 0 = no 1 = yes Bit 2: device is able to communicate via USB after Manifestation phase.</span></span> <span data-ttu-id="67ce7-161">(bitManifestationTolerant) 0 = 아니요, 버스 재설정 확인 필요 1 = 예 비트 1: 업로드 가능 (bitCanUpload) 0 = 아니요 1 = 예 비트 0: 다운로드 가능 (bitCanDnload) 0 = 아니요 1 = 예</span><span class="sxs-lookup"><span data-stu-id="67ce7-161">(bitManifestationTolerant) 0 = no, must see bus reset 1 = yes Bit 1: upload capable (bitCanUpload) 0 = no 1 = yes Bit 0: download capable (bitCanDnload) 0 = no 1 = yes</span></span>  |
| <span data-ttu-id="67ce7-162">wDetachTimeOut</span><span class="sxs-lookup"><span data-stu-id="67ce7-162">wDetachTimeOut</span></span>  | <span data-ttu-id="67ce7-163">3</span><span class="sxs-lookup"><span data-stu-id="67ce7-163">3</span></span>      | <span data-ttu-id="67ce7-164">2</span><span class="sxs-lookup"><span data-stu-id="67ce7-164">2</span></span>  | <span data-ttu-id="67ce7-165">number</span><span class="sxs-lookup"><span data-stu-id="67ce7-165">number</span></span>    | <span data-ttu-id="67ce7-166">디바이스가 DFU_DETACH 요청을 수신하고 나서 대기하는 시간(밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-166">Time, in milliseconds, that the device will wait after receipt of the DFU_DETACH request.</span></span> <span data-ttu-id="67ce7-167">이 시간이 USB 재설정 없이 경과되면 디바이스는 재구성 단계를 종료하고 정상 작업으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-167">If this time elapses without a USB reset, then the device will terminate the Reconfiguration phase and revert back to normal operation.</span></span> <span data-ttu-id="67ce7-168">디바이스에서 대기할 수 있는 최대 시간(타이머에 따라 다름)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-168">This represents the maximum time that the device can wait (depending on its timers, etc.).</span></span> <span data-ttu-id="67ce7-169">USBX는 이 값을 1000밀리초로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-169">USBX sets this value to 1000 ms.</span></span>  |
| <span data-ttu-id="67ce7-170">wTransferSize</span><span class="sxs-lookup"><span data-stu-id="67ce7-170">wTransferSize</span></span>  | <span data-ttu-id="67ce7-171">5</span><span class="sxs-lookup"><span data-stu-id="67ce7-171">5</span></span>      | <span data-ttu-id="67ce7-172">2</span><span class="sxs-lookup"><span data-stu-id="67ce7-172">2</span></span>  | <span data-ttu-id="67ce7-173">number</span><span class="sxs-lookup"><span data-stu-id="67ce7-173">number</span></span>    | <span data-ttu-id="67ce7-174">디바이스에서 제어\-쓰기 작업당 허용할 수 있는 최대 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-174">Maximum number of bytes that the device can accept per control\-write operation.</span></span> <span data-ttu-id="67ce7-175">USBX는 이 값을 64바이트로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-175">USBX sets this value to 64 bytes.</span></span> |

<span data-ttu-id="67ce7-176">DFU 클래스의 선언은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-176">The declaration of the DFU class is as follows:</span></span>

```C
/* Store the DFU parameters. */

dfu_parameter.ux_slave_class_dfu_parameter_instance_activate =
    tx_demo_thread_dfu_activate;

dfu_parameter.ux_slave_class_dfu_parameter_instance_deactivate =
    tx_demo_thread_dfu_deactivate;

dfu_parameter.ux_slave_class_dfu_parameter_read =
    tx_demo_thread_dfu_read;

dfu_parameter.ux_slave_class_dfu_parameter_write =
    tx_demo_thread_dfu_write;

dfu_parameter.ux_slave_class_dfu_parameter_get_status =
    tx_demo_thread_dfu_get_status;

dfu_parameter.ux_slave_class_dfu_parameter_notify =
    tx_demo_thread_dfu_notify;

dfu_parameter.ux_slave_class_dfu_parameter_framework =
    device_framework_dfu;

dfu_parameter.ux_slave_class_dfu_parameter_framework_length =
    DEVICE_FRAMEWORK_LENGTH_DFU;

/* Initialize the device dfu class. The class is connected with interface
1 on configuration 1. */
status = ux_device_stack_class_register(_ux_system_slave_class_dfu_name,
    ux_device_class_dfu_entry, 1, 0,
    (VOID *)&dfu_parameter);

if (status!=UX_SUCCESS) return;
```

<span data-ttu-id="67ce7-177">DFU 클래스는 대상에 특정한 디바이스 펌웨어 애플리케이션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-177">The DFU class needs to work with a device firmware application specific to the target.</span></span> <span data-ttu-id="67ce7-178">따라서 펌웨어 블록을 읽고 쓰기 위한 여러 콜백을 정의하고 펌웨어 업데이트 애플리케이션에서 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-178">Therefore it defines several call back to read and write blocks of firmware and to get status from the firmware update application.</span></span> <span data-ttu-id="67ce7-179">또한 DFU 클래스에는 펌웨어 전송의 시작과 끝이 발생했을 때 애플리케이션에 알리는 알림 콜백 함수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-179">The DFU class also has a notify callback function to inform the application when a begin and end of transfer of the firmware occur.</span></span>

<span data-ttu-id="67ce7-180">다음은 일반적인 DFU 애플리케이션 흐름에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-180">Following is the description of a typical DFU application flow.</span></span>

![DFU 애플리케이션 흐름](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

<span data-ttu-id="67ce7-182">DFU 클래스의 주요 문제는 호스트에서 적절한 애플리케이션을 가져와 펌웨어 다운로드를 수행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-182">The major challenge of the DFU class is getting the right application on the host to perform the download the firmware.</span></span> <span data-ttu-id="67ce7-183">Microsoft에서 제공하는 애플리케이션이 없거나 USB-IF인 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-183">There is no application supplied by Microsoft or the USB-IF.</span></span> <span data-ttu-id="67ce7-184">일부 셰어웨어가 존재하며 Linux에서 상당히 잘 작동하고 Windows에서 약간 낮은 수준으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-184">Some shareware exist and they work reasonably well on Linux and to a lesser extent on Windows.</span></span>

<span data-ttu-id="67ce7-185">Linux에서는 dfu 유틸리티를 사용하여 다음을 찾을 수 있습니다. [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) dfu 유틸리티에 대한 많은 정보를 이 링크에서 찾을 수도 있습니다. [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span><span class="sxs-lookup"><span data-stu-id="67ce7-185">On Linux, one can use dfu-utils to be found here: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) A lot of information on dfu utils can also be found on this link: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span></span>

<span data-ttu-id="67ce7-186">DFU의 Linux 구현은 호스트와 디바이스 간의 재설정 시퀀스를 올바르게 수행하므로 디바이스에서 이 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-186">The Linux implementation of DFU performs correctly the reset sequence between the host and the device and therefore the device does not need to do it.</span></span> <span data-ttu-id="67ce7-187">Linux는 bmAttributes *bitWillDetach* 가 0이 될 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-187">Linux can accept for the bmAttributes *bitWillDetach* to be 0.</span></span> <span data-ttu-id="67ce7-188">반면 Windows에서는 디바이스를 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-188">Windows on the other side requires the device to perform the reset.</span></span>

<span data-ttu-id="67ce7-189">Windows에서 USB 레지스트리는 USB 디바이스를 해당 PID/VID 및 USB 라이브러리와 연결할 수 있어야 하며,이는 DFU 애플리케이션에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-189">On Windows, the USB registry must be able to associate the USB device with its PID/VID and the USB library which will in turn be used by the DFU application.</span></span> <span data-ttu-id="67ce7-190">다음에서 찾을 수 있는 무료 유틸리티 Zadig를 사용하여 이 작업을 쉽게 수행할 수 있습니다. [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/)</span><span class="sxs-lookup"><span data-stu-id="67ce7-190">This can be easily done with the free utility Zadig which can be found here: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/).</span></span>

<span data-ttu-id="67ce7-191">Zadig를 처음 실행하면 다음 화면이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-191">Running Zadig for the first time will show this screen:</span></span>

![처음으로 Zadig 실행](./media/usbx-device-stack-supplemental/zadig.png)

<span data-ttu-id="67ce7-193">디바이스 목록에서 디바이스를 찾아 libusb Windows 드라이버와 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-193">From the device list, find your device and associate it with the libusb windows driver.</span></span> <span data-ttu-id="67ce7-194">그러면 DFU 유틸리티에서 사용하는 Windows USB 라이브러리를 사용하여 디바이스의 PID/VID를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-194">This will bind the PID/VID of the device with the Windows USB library used by the DFU utilities.</span></span>

<span data-ttu-id="67ce7-195">DFU 명령을 작동하려면 디렉터리에 dfu 유틸리티의 압축을 풀어 libusb dll이 동일한 디렉터리에 있는지도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-195">To operate the DFU command, simply unpack the zipped dfu utilities into a directory, making sure the libusb dll is also present in the same directory.</span></span> <span data-ttu-id="67ce7-196">DFU 유틸리티는 명령줄의 DOS 상자에서 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-196">The DFU utilities must be run from a DOS box at the command line.</span></span>

<span data-ttu-id="67ce7-197">먼저, **dfu-util – l** 명령을 입력하여 디바이스가 목록에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-197">First, type the command **dfu-util –l** to determine whether the device is listed.</span></span> <span data-ttu-id="67ce7-198">그렇지 않은 경우 Zadig를 실행하여 디바이스가 표시되고 USB 라이브러리와 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-198">If not, run Zadig to make sure the device is listed and associated with the USB library.</span></span> <span data-ttu-id="67ce7-199">다음과 같은 화면이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-199">You should see a screen as follows:</span></span>

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

<span data-ttu-id="67ce7-200">다음 단계는 다운로드할 파일을 준비하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-200">The next step will be to prepare the file to be downloaded.</span></span> <span data-ttu-id="67ce7-201">USBX DFU 클래스는이 파일에 대한 확인을 수행하지 않으며 내부 형식과 관계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-201">The USBX DFU class does not perform any verification on this file and is agnostic of its internal format.</span></span> <span data-ttu-id="67ce7-202">이 펌웨어 파일은 대상에만 해당되며, DFU 또는 USBX에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-202">This firmware file is very specific to the target but not to DFU nor to USBX.</span></span>

<span data-ttu-id="67ce7-203">그런 다음, 다음 명령을 입력하여 dfu 유틸리티에 파일을 보내도록 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-203">Then the dfu-util can be instructed to send the file by typing the following command:</span></span>

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

<span data-ttu-id="67ce7-204">dfu 유틸리티는 펌웨어가 완전히 다운로드될 때까지 파일 다운로드 프로세스를 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-204">The dfu-util should display the file download process until the firmware has been completely downloaded.</span></span>

## <a name="usb-device-pima-class-ptp-responder"></a><span data-ttu-id="67ce7-205">USB 디바이스 PIMA 클래스(PTP 응답기)</span><span class="sxs-lookup"><span data-stu-id="67ce7-205">USB Device PIMA Class (PTP Responder)</span></span>

<span data-ttu-id="67ce7-206">USB 디바이스 PIMA 클래스를 사용하여 USB 호스트 시스템(개시 디바이스)에서</span><span class="sxs-lookup"><span data-stu-id="67ce7-206">The USB device PIMA class allows for a USB host system (Initiator) to connect to a</span></span>

<span data-ttu-id="67ce7-207">PIMA 디바이스(응답자)에 연결하여 미디어 파일을 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-207">PIMA device (Resonder) to transfer media files.</span></span> <span data-ttu-id="67ce7-208">USBX Pima 클래스는 PTP 클래스(그림 전송 프로토콜용)라고도 하는 USB-IF PIMA 15740 클래스를 준수합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-208">USBX Pima Class is conforming to the USB-IF PIMA 15740 class also known as PTP class (for Picture Transfer Protocol).</span></span>

<span data-ttu-id="67ce7-209">USBX 디바이스 측 PIMA 클래스는 다음 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-209">USBX device side PIMA class supports the following operations.</span></span>

| <span data-ttu-id="67ce7-210">작업 코드</span><span class="sxs-lookup"><span data-stu-id="67ce7-210">Operation code</span></span>                                    | <span data-ttu-id="67ce7-211">값</span><span class="sxs-lookup"><span data-stu-id="67ce7-211">Value</span></span> | <span data-ttu-id="67ce7-212">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-212">Description</span></span>                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| <span data-ttu-id="67ce7-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span><span class="sxs-lookup"><span data-stu-id="67ce7-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span></span>    | <span data-ttu-id="67ce7-214">0x1001</span><span class="sxs-lookup"><span data-stu-id="67ce7-214">0x1001</span></span>  | <span data-ttu-id="67ce7-215">디바이스 지원 작업 및 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-215">Obtain the device supported operations and events</span></span>                                                         |
| <span data-ttu-id="67ce7-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span><span class="sxs-lookup"><span data-stu-id="67ce7-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span></span>        | <span data-ttu-id="67ce7-217">0x1002</span><span class="sxs-lookup"><span data-stu-id="67ce7-217">0x1002</span></span>  | <span data-ttu-id="67ce7-218">호스트와 디바이스 간의 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-218">Open a session between the host and the device</span></span>                                                            |
| <span data-ttu-id="67ce7-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span><span class="sxs-lookup"><span data-stu-id="67ce7-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span></span>       | <span data-ttu-id="67ce7-220">0x1003</span><span class="sxs-lookup"><span data-stu-id="67ce7-220">0x1003</span></span>  | <span data-ttu-id="67ce7-221">호스트와 디바이스 간의 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-221">Close a session between the host and the device</span></span>                                                           |
| <span data-ttu-id="67ce7-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span><span class="sxs-lookup"><span data-stu-id="67ce7-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span></span>    | <span data-ttu-id="67ce7-223">0x1004</span><span class="sxs-lookup"><span data-stu-id="67ce7-223">0x1004</span></span>  | <span data-ttu-id="67ce7-224">디바이스에 대한 저장소 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-224">Returns the storage ID for the device.</span></span> <span data-ttu-id="67ce7-225">USBX PIMA는 하나의 저장소 ID만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-225">USBX PIMA uses one storage ID only</span></span> |
| <span data-ttu-id="67ce7-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span><span class="sxs-lookup"><span data-stu-id="67ce7-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span></span>   | <span data-ttu-id="67ce7-227">0x1005</span><span class="sxs-lookup"><span data-stu-id="67ce7-227">0x1005</span></span>  | <span data-ttu-id="67ce7-228">최대 용량과 사용 가능한 공간 같은 저장소 개체에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-228">Return information about the storage object such as max capacity and free space</span></span>                           |
| <span data-ttu-id="67ce7-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span><span class="sxs-lookup"><span data-stu-id="67ce7-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span></span>    | <span data-ttu-id="67ce7-230">0x1006</span><span class="sxs-lookup"><span data-stu-id="67ce7-230">0x1006</span></span>  | <span data-ttu-id="67ce7-231">저장 디바이스에 포함된 개체 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-231">Return the number of objects contained in the storage device</span></span>                                              |
| <span data-ttu-id="67ce7-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span><span class="sxs-lookup"><span data-stu-id="67ce7-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span></span> | <span data-ttu-id="67ce7-233">0x1007</span><span class="sxs-lookup"><span data-stu-id="67ce7-233">0x1007</span></span>  | <span data-ttu-id="67ce7-234">저장 디바이스에서 개체 핸들의 배열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-234">Return an array of handles of the objects on the storage device</span></span>                                           |
| <span data-ttu-id="67ce7-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="67ce7-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span></span>    | <span data-ttu-id="67ce7-236">0x1008</span><span class="sxs-lookup"><span data-stu-id="67ce7-236">0x1008</span></span>  | <span data-ttu-id="67ce7-237">개체 이름, 만든 날짜, 수정 날짜 등의 개체에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-237">Return information about an object such as the name of the object, its creation date, modification date</span></span> |
| <span data-ttu-id="67ce7-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="67ce7-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span></span>          | <span data-ttu-id="67ce7-239">0x1009</span><span class="sxs-lookup"><span data-stu-id="67ce7-239">0x1009</span></span>  | <span data-ttu-id="67ce7-240">특정 개체와 관련된 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-240">Return the data pertaining to a specific object</span></span>                                                         |
| <span data-ttu-id="67ce7-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span><span class="sxs-lookup"><span data-stu-id="67ce7-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span></span>           | <span data-ttu-id="67ce7-242">0x100A</span><span class="sxs-lookup"><span data-stu-id="67ce7-242">0x100A</span></span>  | <span data-ttu-id="67ce7-243">개체와 관련해 사용할 수 있는 경우 미리 보기를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-243">Send the thumbnail if available about an object</span></span>                                                           |
| <span data-ttu-id="67ce7-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="67ce7-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span></span>       | <span data-ttu-id="67ce7-245">0x100B</span><span class="sxs-lookup"><span data-stu-id="67ce7-245">0x100B</span></span>  | <span data-ttu-id="67ce7-246">미디어에서 개체를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-246">Delete an object on the media</span></span>                                                                             |
| <span data-ttu-id="67ce7-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="67ce7-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span></span>   | <span data-ttu-id="67ce7-248">0x100C</span><span class="sxs-lookup"><span data-stu-id="67ce7-248">0x100C</span></span>  | <span data-ttu-id="67ce7-249">미디어에서 개체를 만들기 위해 개체에 대한 정보를 디바이스에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-249">Send to the device information about an object for its creation on the media</span></span>                              |
| <span data-ttu-id="67ce7-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span><span class="sxs-lookup"><span data-stu-id="67ce7-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span></span>         | <span data-ttu-id="67ce7-251">0x100D</span><span class="sxs-lookup"><span data-stu-id="67ce7-251">0x100D</span></span>  | <span data-ttu-id="67ce7-252">디바이스에 개체에 대한 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-252">Send data for an object to the device</span></span>                                                                     |
| <span data-ttu-id="67ce7-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span><span class="sxs-lookup"><span data-stu-id="67ce7-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span></span>        | <span data-ttu-id="67ce7-254">0x100F</span><span class="sxs-lookup"><span data-stu-id="67ce7-254">0x100F</span></span>  | <span data-ttu-id="67ce7-255">디바이스 미디어를 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-255">Clean the device media</span></span>                                                                                    |
| <span data-ttu-id="67ce7-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span><span class="sxs-lookup"><span data-stu-id="67ce7-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span></span>        | <span data-ttu-id="67ce7-257">0x0110</span><span class="sxs-lookup"><span data-stu-id="67ce7-257">0x0110</span></span>  | <span data-ttu-id="67ce7-258">대상 디바이스를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-258">Reset the target device</span></span>                                                                                   |

| <span data-ttu-id="67ce7-259">작업 코드</span><span class="sxs-lookup"><span data-stu-id="67ce7-259">Operation Code</span></span>                                         | <span data-ttu-id="67ce7-260">값</span><span class="sxs-lookup"><span data-stu-id="67ce7-260">Value</span></span> | <span data-ttu-id="67ce7-261">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-261">Description</span></span> |
|--------------------------------------------------------|-------|-----------------------------------------|
| <span data-ttu-id="67ce7-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="67ce7-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span></span>       | <span data-ttu-id="67ce7-263">0x4001</span><span class="sxs-lookup"><span data-stu-id="67ce7-263">0x4001</span></span>  | <span data-ttu-id="67ce7-264">현재 트랜잭션을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-264">Cancels the current transaction</span></span>                                                 |
| <span data-ttu-id="67ce7-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span><span class="sxs-lookup"><span data-stu-id="67ce7-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span></span>             | <span data-ttu-id="67ce7-266">0x4002</span><span class="sxs-lookup"><span data-stu-id="67ce7-266">0x4002</span></span>  | <span data-ttu-id="67ce7-267">개체가 디바이스 미디어에 추가되고 호스트에서 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-267">An object has been added to the device media and can be retrieved by the host\.</span></span> |
| <span data-ttu-id="67ce7-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span><span class="sxs-lookup"><span data-stu-id="67ce7-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span></span>           | <span data-ttu-id="67ce7-269">0x4003</span><span class="sxs-lookup"><span data-stu-id="67ce7-269">0x4003</span></span>  | <span data-ttu-id="67ce7-270">디바이스 미디어에서 개체가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-270">An object has been deleted from the device media</span></span>                                |
| <span data-ttu-id="67ce7-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span><span class="sxs-lookup"><span data-stu-id="67ce7-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span></span>              | <span data-ttu-id="67ce7-272">0x4004</span><span class="sxs-lookup"><span data-stu-id="67ce7-272">0x4004</span></span>  | <span data-ttu-id="67ce7-273">미디어를 디바이스에 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-273">A media has been added to the device</span></span>                                            |
| <span data-ttu-id="67ce7-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span><span class="sxs-lookup"><span data-stu-id="67ce7-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span></span>            | <span data-ttu-id="67ce7-275">0x4005</span><span class="sxs-lookup"><span data-stu-id="67ce7-275">0x4005</span></span>  | <span data-ttu-id="67ce7-276">미디어를 디바이스에서 삭제했습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-276">A media has been deleted from the device</span></span>                                        |
| <span data-ttu-id="67ce7-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span><span class="sxs-lookup"><span data-stu-id="67ce7-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span></span>     | <span data-ttu-id="67ce7-278">0x4006</span><span class="sxs-lookup"><span data-stu-id="67ce7-278">0x4006</span></span>  | <span data-ttu-id="67ce7-279">디바이스 속성이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-279">Device properties have changed</span></span>                                                  |
| <span data-ttu-id="67ce7-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="67ce7-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span></span>     | <span data-ttu-id="67ce7-281">0x4007</span><span class="sxs-lookup"><span data-stu-id="67ce7-281">0x4007</span></span>  | <span data-ttu-id="67ce7-282">개체 정보가 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-282">An object information has changed</span></span>                                               |
| <span data-ttu-id="67ce7-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span><span class="sxs-lookup"><span data-stu-id="67ce7-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span></span>      | <span data-ttu-id="67ce7-284">0x4008</span><span class="sxs-lookup"><span data-stu-id="67ce7-284">0x4008</span></span>  | <span data-ttu-id="67ce7-285">디바이스가 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-285">A device has changed</span></span>                                                            |
| <span data-ttu-id="67ce7-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span><span class="sxs-lookup"><span data-stu-id="67ce7-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span></span> | <span data-ttu-id="67ce7-287">0x4009</span><span class="sxs-lookup"><span data-stu-id="67ce7-287">0x4009</span></span>  | <span data-ttu-id="67ce7-288">디바이스에서 호스트의 개체 전송을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-288">The device requests the transfer of an object from the host</span></span>                     |
| <span data-ttu-id="67ce7-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span><span class="sxs-lookup"><span data-stu-id="67ce7-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span></span>               | <span data-ttu-id="67ce7-290">0x400A</span><span class="sxs-lookup"><span data-stu-id="67ce7-290">0x400A</span></span>  | <span data-ttu-id="67ce7-291">디바이스가 꽉 찬 미디어를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-291">Device reports the media is full</span></span>                                                |
| <span data-ttu-id="67ce7-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span><span class="sxs-lookup"><span data-stu-id="67ce7-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span></span>             | <span data-ttu-id="67ce7-293">0x400B</span><span class="sxs-lookup"><span data-stu-id="67ce7-293">0x400B</span></span>  | <span data-ttu-id="67ce7-294">디바이스가 초기화되었음을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-294">Device reports it was reset</span></span>                                                     |
| <span data-ttu-id="67ce7-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="67ce7-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span></span>    | <span data-ttu-id="67ce7-296">0x400C</span><span class="sxs-lookup"><span data-stu-id="67ce7-296">0x400C</span></span>  | <span data-ttu-id="67ce7-297">디바이스에서 저장소 정보가 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-297">Storage information has changed on the device</span></span>                                   |
| <span data-ttu-id="67ce7-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span><span class="sxs-lookup"><span data-stu-id="67ce7-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span></span>         | <span data-ttu-id="67ce7-299">0x400D</span><span class="sxs-lookup"><span data-stu-id="67ce7-299">0x400D</span></span>  | <span data-ttu-id="67ce7-300">캡처가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-300">Capture is completed</span></span>                                                            |

<span data-ttu-id="67ce7-301">USBX PIMA 디바이스 클래스는 TX 스레드를 사용하여 호스트에서 PIMA 명령을 수신 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-301">The USBX PIMA device class uses a TX Thread to listen to PIMA commands from the host.</span></span>

<span data-ttu-id="67ce7-302">PIMA 명령은 명령 블록, 데이터 블록 및 상태 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-302">A PIMA command is composed of a command block, a data block and a status phase.</span></span>

<span data-ttu-id="67ce7-303">호스트 쪽에서 PIMA 명령을 수신하기 위해 함수 ux_device_class_pima_thread는 스택에 요청을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-303">The function ux_device_class_pima_thread posts a request to the stack to receive a PIMA command from the host side.</span></span> <span data-ttu-id="67ce7-304">PIMA 명령이 디코딩되어 콘텐츠를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-304">The PIMA command is decoded and verified for content.</span></span> <span data-ttu-id="67ce7-305">명령 블록이 유효한 경우 적절한 명령 처리기로 분기합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-305">If the command block is valid, it branches to the appropriate command handler.</span></span>

<span data-ttu-id="67ce7-306">호스트에서 세션을 연 경우에만 대부분의 PIMA 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-306">Most PIMA commands can only be executed when a session has been opened by the host.</span></span> <span data-ttu-id="67ce7-307">유일한 예외는 **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO** 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-307">The only exception is the command **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**.</span></span> <span data-ttu-id="67ce7-308">USBX PIMA 구현을 사용하면 언제든지 개시 장치와 응답기 간에 하나의 세션만 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-308">With USBX PIMA implementation, only one session can be opened between an Initiator and Responder at any time.</span></span> <span data-ttu-id="67ce7-309">단일 세션 내의 모든 트랜잭션은 차단되며 이전 트랜잭션이 완료되기 전에 새 트랜잭션이 시작될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-309">All transactions within the single session are blocking and no new transaction can begin before the previous one completed.</span></span>

<span data-ttu-id="67ce7-310">PIMA 트랜잭션은 명령 단계, 선택적 데이터 단계 및 응답 단계의 3단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-310">PIMA transactions are composed of 3 phases, a command phase, an optional data phase and a response phase.</span></span> <span data-ttu-id="67ce7-311">데이터 단계가 있으면 한 방향으로만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-311">If a data phase is present, it can only be in one direction.</span></span>

<span data-ttu-id="67ce7-312">개시 장치는 항상 PIMA 작업의 흐름을 결정하지만 응답기는 세션 중에 발생한 상태 변경 내용을 알리기 위해 개시 장치에 이벤트를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-312">The Initiator always determines the flow of the PIMA operations but the Responder can initiate events back to the Initiator to inform status changes that happened during a session.</span></span>

<span data-ttu-id="67ce7-313">다음 다이어그램에서는 호스트와 PIMA 디바이스 클래스 간에 데이터 개체를 전송하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-313">The following diagram shows the transfer of a data object between the host and the PIMA device class.</span></span>

![ACID 트랜잭션](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a><span data-ttu-id="67ce7-315">PIMA 디바이스 클래스 초기화</span><span class="sxs-lookup"><span data-stu-id="67ce7-315">Initialization of the PIMA device class</span></span>

<span data-ttu-id="67ce7-316">PIMA 디바이스 클래스는 초기화하는 동안 애플리케이션에서 제공하는 일부 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-316">The PIMA device class needs some parameters supplied by the application during the initialization.</span></span>

<span data-ttu-id="67ce7-317">다음 매개 변수는 디바이스 및 저장소 정보를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-317">The following parameters describe the device and storage information.</span></span>

- `ux_device_class_pima_manufacturer`
- `ux_device_class_pima_model`
- `ux_device_class_pima_device_version`
- `ux_device_class_pima_serial_number`
- `ux_device_class_pima_storage_id`
- `ux_device_class_pima_storage_type`
- `ux_device_class_pima_storage_file_system_type`
- `ux_device_class_pima_storage_access_capability`
- `ux_device_class_pima_storage_max_capacity_low`
- `ux_device_class_pima_storage_max_capacity_high`
- `ux_device_class_pima_storage_free_space_low`
- `ux_device_class_pima_storage_free_space_high`
- `ux_device_class_pima_storage_free_space_image`
- `ux_device_class_pima_storage_description`
- `ux_device_class_pima_storage_volume_label`

<span data-ttu-id="67ce7-318">또한 PIMA 클래스는 애플리케이션에 콜백을 등록하여 특정 이벤트를 애플리케이션에 알리거나 로컬 미디어에서 데이터를 검색/저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-318">The PIMA class also requires the registration of callback into the application to inform the application of certain events or retrieve/store data from/to the local media.</span></span> <span data-ttu-id="67ce7-319">콜백은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-319">The callbacks are as follows.</span></span>

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

<span data-ttu-id="67ce7-320">다음 예제에서는 PIMA의 클라이언트 쪽을 초기화하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-320">The following example shows how to initialize the client side of PIMA.</span></span> <span data-ttu-id="67ce7-321">이 예제에서는 PIMA에 대한 클라이언트로 Pictbridge를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-321">This example uses Pictbridge as a client for PIMA.</span></span>

```C
/* Initialize the first XML object valid in the pictbridge instance.

Initialize the handle, type and file name.

The storage handle and the object handle have a fixed value of 1 in our implementation. */

object_info = pictbridge -> ux_pictbridge_object_client;

object_info -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_SCRIPT;
object_info -> ux_device_class_pima_object_storage_id = 1;
object_info -> ux_device_class_pima_object_handle_id = 2;

ux_utility_string_to_unicode(_ux_pictbridge_ddiscovery_name,
    object_info -> ux_device_class_pima_object_filename);

/* Initialize the head and tail of the notification round robin buffers.
   At first, the head and tail are pointing to the beginning of the array.
*/

pictbridge -> ux_pictbridge_event_array_head =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_tail =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_end =
    pictbridge -> ux_pictbridge_event_array +
    UX_PICTBRIDGE_MAX_EVENT_NUMBER;

/* Initialialize the pima device parameter. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_manufacturer =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_model =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_serial_number =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_id = 1;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_type =
    UX_DEVICE_CLASS_PIMA_STC_FIXED_RAM;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_file_system_type =
    UX_DEVICE_CLASS_PIMA_FSTC_GENERIC_FLAT;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_access_capability =
    UX_DEVICE_CLASS_PIMA_AC_READ_WRITE;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_image = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_description =
    _ux_pictbridge_volume_description;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_volume_label =
    _ux_pictbridge_volume_label;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_number_get =
    ux_pictbridge_dpsclient_object_number_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_handles_get =
    ux_pictbridge_dpsclient_object_handles_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_get =
    ux_pictbridge_dpsclient_object_info_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_get =
    ux_pictbridge_dpsclient_object_data_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_send =
    ux_pictbridge_dpsclient_object_info_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_send =
    ux_pictbridge_dpsclient_object_data_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_delete =
    ux_pictbridge_dpsclient_object_delete;

/* Store the instance owner. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_application =
    (VOID *) pictbridge;

/* Initialize the device pima class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_pima_name,
    ux_device_class_pima_entry, 1, 0, (VOID *)&pictbridge -> ux_pictbridge_pima_parameter);

/* Check status. */
if (status != UX_SUCCESS)
```

## <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="67ce7-322">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="67ce7-322">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="67ce7-323">개체를 추가하고 호스트에 이벤트 보내기</span><span class="sxs-lookup"><span data-stu-id="67ce7-323">Adding an object and sending the event to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-324">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-324">Prototype</span></span>

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="67ce7-325">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-325">Description</span></span>

<span data-ttu-id="67ce7-326">이 함수는 PIMA 클래스에서 개체를 추가하고 호스트에 알려야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-326">This function is called when the PIMA class needs to add an object and inform the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-327">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-327">Parameters</span></span>

- <span data-ttu-id="67ce7-328">**pima**: pima 클래스 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-328">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="67ce7-329">**object_handle**: 개체의 핸들</span><span class="sxs-lookup"><span data-stu-id="67ce7-329">**object_handle**: Handle of the object.</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-330">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-330">Example</span></span>

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a><span data-ttu-id="67ce7-331">ux_device_class_pima_object_number_get</span><span class="sxs-lookup"><span data-stu-id="67ce7-331">ux_device_class_pima_object_number_get</span></span>

<span data-ttu-id="67ce7-332">애플리케이션에서 개체 번호 가져오기</span><span class="sxs-lookup"><span data-stu-id="67ce7-332">Getting the object number from the application</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-333">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-333">Prototype</span></span>

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a><span data-ttu-id="67ce7-334">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-334">Description</span></span>

<span data-ttu-id="67ce7-335">이 함수는 PIMA 클래스에서 로컬 시스템의 개체 수를 검색하여 호스트에 다시 전송해야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-335">This function is called when the PIMA class needs to retrieve the number of objects in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-336">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-336">Parameters</span></span>

- <span data-ttu-id="67ce7-337">**pima**: pima 클래스 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-337">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="67ce7-338">**object_number**: 반환될 개체 수의 주소</span><span class="sxs-lookup"><span data-stu-id="67ce7-338">**object_number**: Address of the number of objects to be returned</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-339">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-339">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a><span data-ttu-id="67ce7-340">ux_device_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="67ce7-340">ux_device_class_pima_object_handles_get</span></span>

<span data-ttu-id="67ce7-341">개체 핸들 배열 반환</span><span class="sxs-lookup"><span data-stu-id="67ce7-341">Return the object handle array</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-342">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-342">Prototype</span></span>

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a><span data-ttu-id="67ce7-343">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-343">Description</span></span>

<span data-ttu-id="67ce7-344">이 함수는 PIMA 클래스에서 로컬 시스템의 개체 핸들 배열을 검색하여 호스트로 다시 전송해야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-344">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-345">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-345">Parameters</span></span>

- <span data-ttu-id="67ce7-346">**pima**: pima 클래스 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-346">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="67ce7-347">**object_handles_format_code**: 핸들의 서식 코드</span><span class="sxs-lookup"><span data-stu-id="67ce7-347">**object_handles_format_code**: Format code for the handles</span></span>
- <span data-ttu-id="67ce7-348">**object_handles_association**: 개체 연결 코드</span><span class="sxs-lookup"><span data-stu-id="67ce7-348">**object_handles_association**: Object association code</span></span>
- <span data-ttu-id="67ce7-349">**object_handle_array**: 핸들을 저장할 위치 주소</span><span class="sxs-lookup"><span data-stu-id="67ce7-349">**object_handle_array**: Address where to store the handles</span></span>
- <span data-ttu-id="67ce7-350">**object_handles_max_number**: 배열의 최대 핸들 수</span><span class="sxs-lookup"><span data-stu-id="67ce7-350">**object_handles_max_number**: Maximum number of handles in the array</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-351">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-351">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_handles_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *) pima -> ux_device_class_pima_application;

    /* Set the pima pointer to the pictbridge instance. */
    pictbridge -> ux_pictbridge_pima = (VOID *) pima;

    /* We say we have one object but the caller might specify different format code and associations. */
    object_info = pictbridge -> ux_pictbridge_object_client;

    /* Insert in the array the number of found handles so far: 0. */
    ux_utility_long_put((UCHAR *)object_handles_array, 0);

    /* Check the type demanded. */

    if (object_handles_format_code == 0 || object_handles_format_code ==
        0xFFFFFFFF || object_info -> ux_device_class_pima_object_format ==
        object_handles_format_code)
    {
        /* Insert in the array the number of found handles. This handle is for the client XML script. */
        ux_utility_long_put((UCHAR *)object_handles_array, 1);

        /* Adjust the array to point after the number of elements. */
        object_handles_array++;

        /* We have a candicate. Store the handle. */
        ux_utility_long_put((UCHAR *)object_handles_array, object_info ->
            ux_device_class_pima_object_handle_id);
    }

    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_info_get"></a><span data-ttu-id="67ce7-352">ux_device_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="67ce7-352">ux_device_class_pima_object_info_get</span></span>

<span data-ttu-id="67ce7-353">개체 정보 반환</span><span class="sxs-lookup"><span data-stu-id="67ce7-353">Return the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-354">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-354">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a><span data-ttu-id="67ce7-355">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-355">Description</span></span>

<span data-ttu-id="67ce7-356">이 함수는 PIMA 클래스에서 로컬 시스템의 개체 핸들 배열을 검색하여 호스트로 다시 전송해야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-356">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-357">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-357">Parameters</span></span>

- <span data-ttu-id="67ce7-358">**pima**: pima 클래스 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-358">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="67ce7-359">**object_handles**: 개체의 핸들</span><span class="sxs-lookup"><span data-stu-id="67ce7-359">**object_handles**: Handle of the object</span></span>
- <span data-ttu-id="67ce7-360">**object**: 개체 포인터 주소</span><span class="sxs-lookup"><span data-stu-id="67ce7-360">**object**: Object pointer address</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-361">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-361">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UX_SLAVE_CLASS_PIMA_OBJECT **object)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST)) {

        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge -> ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;
    } else
        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;
    /* Return the pointer to this object. */
    *object = object_info;

    /* We are done. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="67ce7-362">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="67ce7-362">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="67ce7-363">개체 데이터 반환</span><span class="sxs-lookup"><span data-stu-id="67ce7-363">Return the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-364">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-364">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a><span data-ttu-id="67ce7-365">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-365">Description</span></span>

<span data-ttu-id="67ce7-366">이 함수는 PIMA 클래스에서 로컬 시스템의 개체 데이터를 검색하여 호스트에 다시 전송해야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-366">This function is called when the PIMA class needs to retrieve the object data in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-367">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-367">Parameters</span></span>

- <span data-ttu-id="67ce7-368">**pima**: pima 클래스 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-368">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="67ce7-369">**object_handle**: 개체의 핸들</span><span class="sxs-lookup"><span data-stu-id="67ce7-369">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="67ce7-370">**object_buffer**: 개체 버퍼 주소</span><span class="sxs-lookup"><span data-stu-id="67ce7-370">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="67ce7-371">**object_length_requested**: 클라이언트에서 애플리케이션에 요청한 개체 데이터 길이</span><span class="sxs-lookup"><span data-stu-id="67ce7-371">**object_length_requested**: Object data length requested by the client to the application</span></span>
- <span data-ttu-id="67ce7-372">**object_actual_length**: 애플리케이션에서 반환된 개체 데이터 길이</span><span class="sxs-lookup"><span data-stu-id="67ce7-372">**object_actual_length**: Object data length returned by the application</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-373">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-373">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UCHAR *object_buffer, ULONG object_offset,
    ULONG object_length_requested, ULONG *object_actual_length)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    UCHAR *pima_object_buffer;
    ULONG actual_length;
    UINT status;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST))
    {
        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;

       /* Is this the corrent handle ? */
       if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
       {
           /* Get the pointer to the object buffer. */
           pima_object_buffer = object_info -> ux_device_class_pima_object_buffer;

           /* Copy the demanded object data portion. */
           ux_utility_memory_copy(object_buffer, pima_object_buffer +
               object_offset, object_length_requested);

           /* Update the length requested. for a demo, we do not do any checking. */
           *object_actual_length = object_length_requested;

           /* What cycle are we in ? */
           if (pictbridge -> ux_pictbridge_host_client_state_machine &
               UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST)
            {
                /* Check if we are blocking for a client request. */
                if (pictbridge -> ux_pictbridge_host_client_state_machine &
                    UX_PICTBRIDGE_STATE_MACHINE_CLIENT_REQUEST_PENDING)

                    /* Yes we are pending, send an event to release the pending request. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_STATE_MACHINE_READY, TX_OR);

               /* Since we are in host request, this indicates we are done with the cycle. */
               pictbridge -> ux_pictbridge_host_client_state_machine =
                   UX_PICTBRIDGE_STATE_MACHINE_IDLE;

            }

            /* We have copied the requested data. Return OK. */
            return(UX_SUCCESS);

        }
    }
    else
    {

        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;

        /* Obtain the data from the application jobinfo callback. */
        status = pictbridge -> ux_pictbridge_jobinfo.
            ux_pictbridge_jobinfo_object_data_read(pictbridge, object_buffer, object_offset,
            object_length_requested, &actual_length);

        /* Save the length returned. */
        *object_actual_length = actual_length;

        /* Return the application status. */
        return(status);

    }

    /* Could not find the handle. */

    return(UX_DEVICE_CLASS_PIMA_RC_INVALID_OBJECT_HANDLE);
}
```

## <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="67ce7-374">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="67ce7-374">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="67ce7-375">호스트에서 개체 정보 보내기</span><span class="sxs-lookup"><span data-stu-id="67ce7-375">Host sends the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-376">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-376">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a><span data-ttu-id="67ce7-377">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-377">Description</span></span>

<span data-ttu-id="67ce7-378">이 함수는 PIMA 클래스에서 추후 저장을 위해 로컬 시스템에서 개체 정보를 받아야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-378">This function is called when the PIMA class needs to receive the object information in the local system for future storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-379">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-379">Parameters</span></span>

- <span data-ttu-id="67ce7-380">**pima**: pima 클래스 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-380">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="67ce7-381">**object**: 개체에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-381">**object**:  Pointer to the object</span></span>
- <span data-ttu-id="67ce7-382">**object_handle**: 개체의 핸들</span><span class="sxs-lookup"><span data-stu-id="67ce7-382">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-383">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-383">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_send(UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, ULONG *object_handle)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info; UCHAR
    string_discovery_name[UX_PICTBRIDGE_MAX_FILE_NAME_SIZE];

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* We only have one object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Copy the demanded object info set. */
    ux_utility_memory_copy(object_info, object,
        UX_SLAVE_CLASS_PIMA_OBJECT_DATA_LENGTH);

    /* Store the object handle. In Pictbridge we only receive XML scripts so the handle is hardwired to 1. */
    object_info -> ux_device_class_pima_object_handle_id = 1;
    *object_handle = 1;

    /* Check state machine. If we are in discovery pending mode, check file name of this object. */
    if (pictbridge -> ux_pictbridge_discovery_state ==
        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_PENDING)
    {
        /* We are in the discovery mode. Check for file name. It must match
           HDISCVRY.DPS in Unicode mode. */

        /* Check if this is a script. */
        if (object_info -> ux_device_class_pima_object_format ==
            UX_DEVICE_CLASS_PIMA_OFC_SCRIPT)
        {

            /* Yes this is a script. We need to search for the HDISCVRY.DPS file name. Get the file name in a ascii format. */
            ux_utility_unicode_to_string(object_info ->
                ux_device_class_pima_object_filename,
                string_discovery_name);

            /* Now, compare it to the HDISCVRY.DPS file name. Check length first. */
            if (ux_utility_string_length_get(_ux_pictbridge_hdiscovery_name)
                == ux_utility_string_length_get(string_discovery_name))
            {

                /* So far, the length of name of the files are the same. Compare names now. */
                if(ux_utility_memory_compare(_ux_pictbridge_hdiscovery_name,
                    string_discovery_name,
                    ux_utility_string_length_get(string_discovery_name)) == UX_SUCCESS)
                {
                    /* We are done with discovery of the printer. We can now send notifications when the camera wants to print an object. */
                    pictbridge -> ux_pictbridge_discovery_state =
                        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_COMPLETE;

                    /* Set an event flag if the application is listening. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY, TX_OR);

                    /* There is no object during th discovery cycle. */
                    return(UX_SUCCESS);
                }
            }
        }
    }
    /* What cycle are we in ? */
    if (pictbridge -> ux_pictbridge_host_client_state_machine ==
        UX_PICTBRIDGE_STATE_MACHINE_IDLE)

        /* Since we are in idle state, we must have received a request from the host. */
        pictbridge -> ux_pictbridge_host_client_state_machine =
            UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="67ce7-384">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="67ce7-384">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="67ce7-385">호스트에서 개체 데이터 보내기</span><span class="sxs-lookup"><span data-stu-id="67ce7-385">Host sends the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-386">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-386">Prototype</span></span>

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a><span data-ttu-id="67ce7-387">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-387">Description</span></span>

<span data-ttu-id="67ce7-388">이 함수는 PIMA 클래스에서 추후 저장을 위해 로컬 시스템에서 개체 데이터를 받아야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-388">This function is called when the PIMA class needs to receive the object data in the local system for storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-389">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-389">Parameters</span></span>

- <span data-ttu-id="67ce7-390">**pima**: pima 클래스 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-390">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="67ce7-391">**object_handle**: 개체의 핸들</span><span class="sxs-lookup"><span data-stu-id="67ce7-391">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="67ce7-392">**phase**: 전송 단계(활성 또는 전체)</span><span class="sxs-lookup"><span data-stu-id="67ce7-392">**phase**: phase of the transfer (active or complete)</span></span>
- <span data-ttu-id="67ce7-393">**object_buffer**: 개체 버퍼 주소</span><span class="sxs-lookup"><span data-stu-id="67ce7-393">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="67ce7-394">**object_offset**: 데이터 주소</span><span class="sxs-lookup"><span data-stu-id="67ce7-394">**object_offset**: Address of data</span></span>
- <span data-ttu-id="67ce7-395">**object_length**: 애플리케이션에서 보낸 개체 데이터 길이</span><span class="sxs-lookup"><span data-stu-id="67ce7-395">**object_length**: Object data length sent by application</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-396">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-396">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_send(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    ULONG phase,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length)
{
    UINT status;
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    ULONG event_flag;
    UCHAR *pima_object_buffer;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Get the pointer to the pima object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Is this the corrent handle ? */
    if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
    {
        /* Get the pointer to the object buffer. */
        pima_object_buffer = object_info ->
            ux_device_class_pima_object_buffer;

        /* Check the phase. We should wait for the object to be completed and the response sent back before parsing the object. */
        if (phase == UX_DEVICE_CLASS_PIMA_OBJECT_TRANSFER_PHASE_ACTIVE)
        {
            /* Copy the demanded object data portion. */
            ux_utility_memory_copy(pima_object_buffer + object_offset,
                object_buffer, object_length);

            /* Save the length of this object. */
            object_info -> ux_device_class_pima_object_length = object_length;

            /* We are not done yet. */
            return(UX_SUCCESS);
        }
        else
        {
            /* Completion of transfer. We are done. */
            return(UX_SUCCESS);
        }
    }
}
```

## <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="67ce7-397">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="67ce7-397">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="67ce7-398">로컬 개체 삭제</span><span class="sxs-lookup"><span data-stu-id="67ce7-398">Delete a local object</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-399">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-399">Prototype</span></span>

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="67ce7-400">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-400">Description</span></span>

<span data-ttu-id="67ce7-401">이 함수는 PIMA 클래스가 로컬 저장소에서 개체를 삭제해야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-401">This function is called when the PIMA class needs to delete an object on the local storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-402">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-402">Parameters</span></span>

- <span data-ttu-id="67ce7-403">**pima**: pima 클래스 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-403">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="67ce7-404">**object_handle**: 개체의 핸들</span><span class="sxs-lookup"><span data-stu-id="67ce7-404">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-405">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-405">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a><span data-ttu-id="67ce7-406">USB 디바이스 오디오 클래스</span><span class="sxs-lookup"><span data-stu-id="67ce7-406">USB Device Audio Class</span></span>

<span data-ttu-id="67ce7-407">USB 디바이스 오디오 클래스를 사용하면 USB 호스트 시스템이 오디오 디바이스로 디바이스와 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-407">The USB device Audio class allows for a USB host system to communicate with the device as an audio device.</span></span> <span data-ttu-id="67ce7-408">이 클래스는 USB 표준 및 USB 오디오 클래스 1.0 또는 2.0 표준을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-408">This class is based on the USB standard and USB Audio Class 1.0 or 2.0 standard.</span></span>

<span data-ttu-id="67ce7-409">디바이스 스택에서 USB 오디오 규격 디바이스 프레임워크를 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-409">A USB audio compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="67ce7-410">오디오 2.0 스피커의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-410">An example of an Audio 2.0 speaker follows:</span></span>

```C
unsigned char device_framework_high_speed[] = {

    /* --- Device Descriptor 18 bytes
    0x00 bDeviceClass: Refer to interface
    0x00 bDeviceSubclass: Refer to interface
    0x00 bDeviceProtocol: Refer to interface

    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    /* 0 bLength, bDescriptorType */ 18, 0x01,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00, 0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 0x08,
    /* 8 idVendor, idProduct */ 0x84, 0x84, 0x03, 0x00,
    /* 12 bcdDevice */ 0x00, 0x02,
    /* 14 iManufacturer, iProduct, iSerialNumber */ 0, 0, 0,
    /* 17 bNumConfigurations */ 1,
    /* ---------------- Device Qualifier Descriptor */
    /* 0 bLength, bDescriptorType */ 10, 0x06,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00,0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 8,
    /* 8 bNumConfigurations */ 1,
    /* 9 bReserved */ 0,
    /* --- Configuration Descriptor (9+8+73+55=145, 0x91) */
    /* 0 bLength, bDescriptorType */ 9, 0x02,
    /* 2 wTotalLength */ 145, 0,
    /* 4 bNumInterfaces, bConfigurationValue */ 2, 1,
    /* 6 iConfiguration */ 0,
    /* 7 bmAttributes, bMaxPower */ 0x80, 50,
    /* ----------- Interface Association Descriptor */
    /* 0 bLength, bDescriptorType */ 8, 0x0B,
    /* 2 bFirstInterface, bInterfaceCount */ 0, 2,
    /* 4 bFunctionClass : 0x01 (Audio) */ 0x01,
    /* 5 bFunctionSubClass : 0x00 (UNDEFINED) */ 0x00,
    /* 6 bFunctionProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 7 iFunction */ 0,
    /* --- Interface Descriptor #0: Control (9+64=73) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 0, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioControl) */ 0x01,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* --- Audio 2.0 AC Interface Header Descriptor (9+8+17+18+12=64, 0x40) */
    /* 0 bLength */ 9,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bcdADC */ 0x00, 0x02,
    /* 5 bCategory : 0x08 (IO Box) */ 0x08,
    /* 6 wTotalLength */ 64, 0,
    /* 8 bmControls */ 0x00,
    /* -------- Audio 2.0 AC Clock Source Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x0A,
    /* 3 bClockID */ 0x10,
    /* 4 bmAttributes : 0x05 (Sync|InternalFixedClk) */ 0x05,
    /* 5 bmControls : 0x01 (FreqReadOnly) */ 0x01,
    /* 6 bAssocTerminal, iClockSource */ 0x00, 0,
    /* ------ Audio 2.0 AC Input Terminal Descriptor */
    /* 0 bLength */ 17,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02, /* 3 bTerminalID */ 0x04,
    /* 4 wTerminalType : 0x0101 (USB Streaming) */ 0x01, 0x01,
    /* 6 bAssocTerminal, bCSourceID */ 0x00, 0x10,
    /* 8 bNrChannels */ 2,
    /* 9 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 13 iChannelNames, bmControls, iTerminal */ 0, 0x00, 0x00, 0,
    /* -------- Audio 2.0 AC Feature Unit Descriptor */
    /* 0 bLength */ 18,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x06,
    /* 3 bUnitID, bSourceID */ 0x05, 0x04,
    /* 5 bmaControls(0) : 0x0F (VolumeRW|MuteRW) */ 0x0F, 0x00, 0x00, 0x00,
    /* 9 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* 13 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* . iFeature */ 0,
    /* ----- Audio 2.0 AC Output Terminal Descriptor */
    /* 0 bLength */ 12,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x03, /* 3 bTerminalID */ 0x06,
    /* 4 wTerminalType : 0x0301 (Speaker) */ 0x01, 0x03,
    /* 6 bAssocTerminal, bSourceID, bCSourceID */ 0x00, 0x05, 0x10,
    /* 9 bmControls, iTerminal */ 0x00, 0x00, 0,
    /* --- Interface Descriptor #1: Stream OUT (9+9+16+6+7+8=55) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------------------- Interface Descriptor */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 1,
    /* 4 bNumEndpoints */ 1,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------- Audio 2.0 AS Interface Descriptor */
    /* 0 bLength */ 16,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bTerminalLink, bmControls */ 0x04, 0x00,
    /* 5 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 6 bmFormats : 0x000000001 (PCM) */ 0x01, 0x00, 0x00, 0x00, /* 10 bNrChannels */ 2,
    /* 11 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 15 iChannelNames */ 0, /* --------- Audio 2.0 AS Format Type Descriptor */
    /* 0 bLength */ 6,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02,
    /* 3 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 4 bSubslotSize, bBitResolution */ 2, 16,
    /* ------------------------- Endpoint Descriptor */
    /* 0 bLength, bDescriptorType */ 7, 0x05,
    /* 2 bEndpointAddress */ 0x02,
    /* 3 bmAttributes : 0x0D (Sync|ISO) */ 0x0D,
    /* 4 wMaxPacketSize : 0x0100 (256) */ 0x00, 0x01,
    /* 6 bInterval : 0x04 (1ms) */ 4,
    /* - Audio 2.0 AS ISO Audio Data Endpoint Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x25, 0x01,
    /* 3 bmAttributes, bmControls */ 0x00, 0x00,
    /* 5 bLockDelayUnits, wLockDelay */ 0x00, 0x00, 0x00,
};
```

<span data-ttu-id="67ce7-411">오디오 클래스는 복합 디바이스 프레임워크를 사용하여 인터페이스(제어 및 데이터)를 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-411">The Audio class uses a composite device framework to group interfaces (control and streaming).</span></span> <span data-ttu-id="67ce7-412">따라서 디바이스 설명자를 정의할 때는 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-412">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="67ce7-413">USBX는 IAD 설명자를 사용하여 내부적으로 인터페이스 바인딩 방법을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-413">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="67ce7-414">IAD 설명자는 인터페이스(하나 이상의 오디오 스트리밍 인터페이스가 뒤따르는 오디오 컨트롤 인터페이스) 앞에 선언되어야 하며 오디오 클래스(오디오 컨트롤 인터페이스)의 첫 번째 인터페이스 및 연결된 인터페이스의 수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-414">The IAD descriptor should be declared before the interfaces (an AudioControl interface followed by one or more AudioStreaming interfaces) and contain the first interface of the Audio class (the AudioControl interface) and how many interfaces are attached.</span></span>

<span data-ttu-id="67ce7-415">오디오 클래스가 작동하는 방식은 디바이스가 오디오를 송수신하고 있는지에 따라 다르며 두 경우 모두 오디오 프레임 버퍼를 저장하는 데 FIFO를 사용합니다. 디바이스에서 호스트로 오디오를 보내는 경우 애플리케이션은 나중에 USBX에 의해 호스트에 전송되는 FIFO에 오디오 프레임 버퍼를 추가합니다. 디바이스가 호스트에서 오디오를 수신하는 경우에는 USBX가 호스트에서 받은 오디오 프레임 버퍼를 나중에 애플리케이션에서 읽은 FIFO로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-415">The way the audio class works depends on whether the device is sending or receiving audio, but both cases use a FIFO for storing audio frame buffers: if the device is sending audio to the host, then the application adds audio frame buffers to the FIFO which are later sent to the host by USBX; if the device is receiving audio from the host, then USBX adds the audio frame buffers received from the host to the FIFO which are later read by the application.</span></span> <span data-ttu-id="67ce7-416">각 오디오 스트림에는 고유한 FIFO가 있으며 각 오디오 프레임 버퍼는 여러 샘플로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-416">Each audio stream has its own FIFO, and each audio frame buffer consists of multiple samples.</span></span>

<span data-ttu-id="67ce7-417">오디오 클래스의 초기화에는 다음 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-417">The initialization of the Audio class expects the following parts.</span></span>

1. <span data-ttu-id="67ce7-418">Audio 클래스에는 다음 스트리밍 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-418">Audio class expects the following streaming parameters:</span></span>

   ```C
   /* Set the parameters for Audio streams. */
   /* Set the application-defined callback that is invoked when the
      host requests a change to the alternate setting. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_change = demo_audio_read_change;

   /* Set the application-defined callback that is invoked whenever
      a USB packet (audio frame) is sent to or received from the host. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_frame_done = demo_audio_read_done;

   /* Set the number of audio frame buffers in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_nb = UX_DEMO_FRAME_BUFFER_NB;

   /* Set the maximum size of each audio frame buffer in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_size = UX_DEMO_MAX_FRAME_SIZE;

   /* Set the internally-defined audio processing thread entry pointer. If the application wishes to receive audio from the host
      (which is the case in this example), ux_device_class_audio_read_thread_entry should be used;
      if the application wishes to send data to the host, ux_device_class_audio_write_thread_entry should be used. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry = ux_device_class_audio_read_thread_entry;
   ```

2. <span data-ttu-id="67ce7-419">Audio 클래스에는 다음 함수 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-419">Audio class expects the following function parameters.</span></span>

   ```C
   /* Set the parameters for Audio device. */

   /* Set the number of streams. */
   audio_parameter.ux_device_class_audio_parameter_streams_nb = 1;

   /* Set the pointer to the first audio stream parameter.
      Note that we initialized this parameter in the previous section.
      Also note that for more than one streams, this should be an array. */
   audio_parameter.ux_device_class_audio_parameter_streams = audio_stream_parameter;

   /* Set the application-defined callback that is invoked when the audio class
      is activated i.e. device is connected to host. */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_activate = demo_audio_instance_activate;

   /* Set the application-defined callback that is invoked when the audio class
      is deactivated i.e. device is disconnected from host. */

   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_deactivate = demo_audio_instance_deactivate;

   /* Set the application-defined callback that is invoked when the stack receives a control request from the host.
      See below for more details.
   */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_device_class_audio_control_process = demo_audio20_request_process;

   /* Initialize the device Audio class. This class owns interfaces starting with 0. */
   status = ux_device_stack_class_register(_ux_system_slave_class_audio_name,
       ux_device_class_audio_entry, 1, 0, &audio_parameter);
   if(status!=UX_SUCCESS)
       return;
   ```

   <span data-ttu-id="67ce7-420">애플리케이션 정의 제어 요청 콜백 (이전 예제에서 설정된 ***ux_device_class_audio_control_process***)은 스택에서 호스트의 제어 요청을 받을 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-420">The application-defined control request callback (***ux_device_class_audio_control_process***; set in the previous example) is invoked when the stack receives a control request from the host.</span></span> <span data-ttu-id="67ce7-421">요청을 수락하고 처리(승인 또는 중단)하는 경우 콜백이 성공을 반환해야 합니다. 그렇지 않으면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-421">If the request is accepted and handled (acknowledged or stalled) the callback must return success, otherwise error should be returned.</span></span>

   <span data-ttu-id="67ce7-422">클래스 관련 제어 요청 프로세스는 애플리케이션 정의 콜백으로 정의됩니다. 이러한 제어 요청은 USB 오디오 버전 간에 매우 다르며 요청 프로세스의 많은 부분은 디바이스 프레임 워크와 관련되어 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-422">The class-specific control request process is defined as an application-defined callback because the control requests are very different between USB Audio versions and a large part of the request process relates to the device framework.</span></span> <span data-ttu-id="67ce7-423">애플리케이션은 디바이스 기능하도록 요청을 올바르게 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-423">The application should handle requests correctly to make the device functional.</span></span>

   <span data-ttu-id="67ce7-424">오디오 디바이스에 대한 볼륨, 음소거 및 샘플링 빈도는 일반적인 제어 요청이므로 다른 USB 오디오 버전에 대한 간단한 내부적으로 정의된 콜백은 애플리케이션에서 사용할 수 있도록 이후 섹션에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-424">Since for an audio device, volume, mute and sampling frequency are common control requests, simple, internally-defined callbacks for different USB audio versions are introduced in later sections for applications to use.</span></span> <span data-ttu-id="67ce7-425">자세한 내용은 \***ux_device_class_audio10_control_process** _ 및 _ \*_ux_device_class_audio_control_request_\*\*를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="67ce7-425">Refer to ***ux_device_class_audio10_control_process** _ and _ *_ux_device_class_audio_control_request_** for more details.</span></span>

<span data-ttu-id="67ce7-426">오디오 디바이스의 디바이스 프레임워크에서 PID/VID는 디바이스 설명자에 저장됩니다(위에서 선언한 디바이스 설명자 참조).</span><span class="sxs-lookup"><span data-stu-id="67ce7-426">In the device framework of the Audio device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="67ce7-427">USB 호스트 시스템에서 USB 오디오 디바이스를 검색하고 오디오 클래스를 탑재하면 디바이스는 프레임 워크에 따라 모든 오디오 플레이어 또는 레코더와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-427">When a USB host system discovers the USB Audio device and mounts the audio class, the device can be used with any audio player or recorder (depending on the framework).</span></span> <span data-ttu-id="67ce7-428">호스트 운영 체제를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="67ce7-428">See the host Operating System for reference.</span></span>

<span data-ttu-id="67ce7-429">오디오 클래스 API는 아래에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-429">The Audio class APIs are defined below.</span></span>

## <a name="ux_device_class_audio_read_thread_entry"></a><span data-ttu-id="67ce7-430">ux_device_class_audio_read_thread_entry</span><span class="sxs-lookup"><span data-stu-id="67ce7-430">ux_device_class_audio_read_thread_entry</span></span>

<span data-ttu-id="67ce7-431">오디오 함수의 데이터를 읽기 위한 스레드 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-431">Thread entry for reading data for the Audio function.</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-432">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-432">Prototype</span></span>

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="67ce7-433">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-433">Description</span></span>

<span data-ttu-id="67ce7-434">이 함수는 호스트에서 오디오를 읽으려는 경우 오디오 스트림 초기화 매개 변수로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-434">This function is passed to the audio stream initialization parameter if reading audio from the host is desired.</span></span> <span data-ttu-id="67ce7-435">내부적으로 이 함수를 항목 함수로 사용하여 스레드를 만듭니다. 스레드 자체는 오디오 함수에서 등시성 OUT 끝점을 통해 오디오 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-435">Internally, a thread is created with this function as its entry function; the thread itself reads audio data through the isochronous OUT endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-436">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-436">Parameters</span></span>

- <span data-ttu-id="67ce7-437">**audio_stream**: 오디오 스트림 인스턴스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="67ce7-437">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-438">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-438">Example</span></span>

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a><span data-ttu-id="67ce7-439">ux_device_class_audio_write_thread_entry</span><span class="sxs-lookup"><span data-stu-id="67ce7-439">ux_device_class_audio_write_thread_entry</span></span>

<span data-ttu-id="67ce7-440">오디오 함수에 대한 데이터를 쓰기 위한 스레드 항목</span><span class="sxs-lookup"><span data-stu-id="67ce7-440">Thread entry for writing data for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-441">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-441">Prototype</span></span>

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="67ce7-442">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-442">Description</span></span>

<span data-ttu-id="67ce7-443">이 함수는 호스트에 오디오 쓰기가 필요한 경우 오디오 스트림 초기화 매개 변수에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-443">This function is passed to the audio stream initialization parameter if writing audio to the host is desired.</span></span> <span data-ttu-id="67ce7-444">내부적으로 이 함수를 항목 함수로 사용하여 스레드를 만듭니다. 스레드 자체는 오디오 함수의 끝점에서 등시성 IN 끝점을 통해 오디오 데이터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-444">Internally, a thread is created with this function as its entry function; the thread itself writes audio data through the isochronous IN endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-445">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-445">Parameters</span></span>

- <span data-ttu-id="67ce7-446">**audio_stream**: 오디오 스트림 인스턴스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="67ce7-446">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-447">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-447">Example</span></span>

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a><span data-ttu-id="67ce7-448">ux_device_class_audio_stream_get</span><span class="sxs-lookup"><span data-stu-id="67ce7-448">ux_device_class_audio_stream_get</span></span>

<span data-ttu-id="67ce7-449">오디오 함수의 특정 스트림 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-449">Get specific stream instance for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-450">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-450">Prototype</span></span>

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a><span data-ttu-id="67ce7-451">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-451">Description</span></span>

<span data-ttu-id="67ce7-452">이 함수는 오디오 클래스의 스트림 인스턴스를 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-452">This function is used to get a stream instance of audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-453">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-453">Parameters</span></span>

- <span data-ttu-id="67ce7-454">**audio**: 오디오 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-454">**audio**: Pointer to the audio instance</span></span>
- <span data-ttu-id="67ce7-455">**stream_index**: 0을 기준으로 하는 스트림 인스턴스 인덱스</span><span class="sxs-lookup"><span data-stu-id="67ce7-455">**stream_index**: Stream instance index based on 0</span></span>
- <span data-ttu-id="67ce7-456">**stream**: 오디오 스트림 인스턴스 포인터를 저장할 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-456">**stream**: Pointer to buffer to store the audio stream instance pointer</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-457">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-457">Return Value</span></span>

- <span data-ttu-id="67ce7-458">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-458">**UX_SUCCESS** (0x00) This operation was successful</span></span>
- <span data-ttu-id="67ce7-459">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-459">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-460">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-460">Example</span></span>

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a><span data-ttu-id="67ce7-461">ux_device_class_audio_reception_start</span><span class="sxs-lookup"><span data-stu-id="67ce7-461">ux_device_class_audio_reception_start</span></span>

<span data-ttu-id="67ce7-462">오디오 스트림에 대한 오디오 데이터 수신 시작</span><span class="sxs-lookup"><span data-stu-id="67ce7-462">Start audio data reception for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-463">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-463">Prototype</span></span>

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="67ce7-464">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-464">Description</span></span>

<span data-ttu-id="67ce7-465">이 함수는 오디오 스트림에서 오디오 데이터 읽기를 시작하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-465">This function is used to start audio data reading in audio streams.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-466">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-466">Parameters</span></span>

- <span data-ttu-id="67ce7-467">**stream**: 오디오 스트림 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-467">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-468">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-468">Return Value</span></span>

- <span data-ttu-id="67ce7-469">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-469">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인터페이스가 다운되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="67ce7-471">**UX_BUFFER_OVERFLOW** (0x5d) FIFO 버퍼가 가득 찼습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-471">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="67ce7-472">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-472">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-473">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-473">Example</span></span>

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a><span data-ttu-id="67ce7-474">ux_device_class_audio_sample_read8</span><span class="sxs-lookup"><span data-stu-id="67ce7-474">ux_device_class_audio_sample_read8</span></span>

<span data-ttu-id="67ce7-475">오디오 스트림에서 8비트 샘플 읽기</span><span class="sxs-lookup"><span data-stu-id="67ce7-475">Read 8-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-476">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-476">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="67ce7-477">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-477">Description</span></span>

<span data-ttu-id="67ce7-478">이 함수는 지정된 스트림에서 8비트 오디오 샘플 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-478">This function reads 8-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="67ce7-479">특히 FIFO의 현재 오디오 프레임 버퍼에서 샘플 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-479">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="67ce7-480">오디오 프레임에서 마지막 샘플을 읽을 때 프레임은 호스트에서 더 많은 데이터를 수락하는 데 사용할 수 있도록 자동으로 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-480">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-481">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-481">Parameters</span></span>

- <span data-ttu-id="67ce7-482">**stream**: 오디오 스트림 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-482">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="67ce7-483">**buffer**: 샘플 바이트를 저장할 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-483">**buffer**: Pointer to the buffer to save sample byte.</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-484">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-484">Return Value</span></span>

- <span data-ttu-id="67ce7-485">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-485">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인터페이스가 다운되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="67ce7-487">**UX_BUFFER_OVERFLOW** (0x5d) FIFO 버퍼가 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-487">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="67ce7-488">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-488">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-489">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-489">Example</span></span>

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a><span data-ttu-id="67ce7-490">ux_device_class_audio_sample_read16</span><span class="sxs-lookup"><span data-stu-id="67ce7-490">ux_device_class_audio_sample_read16</span></span>

<span data-ttu-id="67ce7-491">오디오 스트림에서 16 비트 샘플 읽기</span><span class="sxs-lookup"><span data-stu-id="67ce7-491">Read 16-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-492">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-492">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a><span data-ttu-id="67ce7-493">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-493">Description</span></span>

<span data-ttu-id="67ce7-494">이 함수는 지정된 스트림에서 16비트 오디오 샘플 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-494">This function reads 16-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="67ce7-495">특히 FIFO의 현재 오디오 프레임 버퍼에서 샘플 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-495">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="67ce7-496">오디오 프레임에서 마지막 샘플을 읽을 때 프레임은 호스트에서 더 많은 데이터를 수락하는 데 사용할 수 있도록 자동으로 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-496">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-497">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-497">Parameters</span></span>

- <span data-ttu-id="67ce7-498">**stream**: 오디오 스트림 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-498">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="67ce7-499">**buffer**: 16비트 샘플을 저장할 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-499">**buffer**: Pointer to the buffer to save the 16-bit sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-500">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-500">Return Value</span></span>

- <span data-ttu-id="67ce7-501">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-501">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인터페이스가 다운되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="67ce7-503">**UX_BUFFER_OVERFLOW** (0x5d) FIFO 버퍼가 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-503">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="67ce7-504">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-504">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-505">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-505">Example</span></span>

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a><span data-ttu-id="67ce7-506">ux_device_class_audio_sample_read24</span><span class="sxs-lookup"><span data-stu-id="67ce7-506">ux_device_class_audio_sample_read24</span></span>

<span data-ttu-id="67ce7-507">오디오 스트림에서 24비트 샘플 읽기</span><span class="sxs-lookup"><span data-stu-id="67ce7-507">Read 24-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-508">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-508">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="67ce7-509">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-509">Description</span></span>

<span data-ttu-id="67ce7-510">이 함수는 지정된 스트림에서 24비트 오디오 샘플 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-510">This function reads 24-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="67ce7-511">특히 FIFO의 현재 오디오 프레임 버퍼에서 샘플 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-511">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="67ce7-512">오디오 프레임에서 마지막 샘플을 읽을 때 프레임은 호스트에서 더 많은 데이터를 수락하는 데 사용할 수 있도록 자동으로 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-512">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-513">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-513">Parameters</span></span>

- <span data-ttu-id="67ce7-514">**stream**: 오디오 스트림 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-514">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="67ce7-515">**buffer**: 3바이트 샘플을 저장할 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-515">**buffer**: Pointer to the buffer to save the 3-byte sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-516">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-516">Return Value</span></span>

- <span data-ttu-id="67ce7-517">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-517">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인터페이스가 다운되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="67ce7-519">**UX_BUFFER_OVERFLOW** (0x5d) FIFO 버퍼가 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-519">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="67ce7-520">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-520">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-521">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-521">Example</span></span>

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a><span data-ttu-id="67ce7-522">ux_device_class_audio_sample_read32</span><span class="sxs-lookup"><span data-stu-id="67ce7-522">ux_device_class_audio_sample_read32</span></span>

<span data-ttu-id="67ce7-523">오디오 스트림에서 32비트 샘플 읽기</span><span class="sxs-lookup"><span data-stu-id="67ce7-523">Read 32-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-524">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-524">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="67ce7-525">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-525">Description</span></span>

<span data-ttu-id="67ce7-526">이 함수는 지정된 스트림에서 32비트 오디오 샘플 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-526">This function reads 32-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="67ce7-527">특히 FIFO의 현재 오디오 프레임 버퍼에서 샘플 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-527">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="67ce7-528">오디오 프레임에서 마지막 샘플을 읽을 때 프레임은 호스트에서 더 많은 데이터를 수락하는 데 사용할 수 있도록 자동으로 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-528">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-529">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-529">Parameters</span></span>

- <span data-ttu-id="67ce7-530">**stream**: 오디오 스트림 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-530">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="67ce7-531">**buffer**: 4바이트 데이터를 저장할 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-531">**buffer**: Pointer to the buffer to save the 4-byte data.</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-532">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-532">Return Value</span></span>

- <span data-ttu-id="67ce7-533">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-533">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인터페이스가 다운되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="67ce7-535">**UX_BUFFER_OVERFLOW** (0x5d) FIFO 버퍼가 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-535">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="67ce7-536">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-536">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-537">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-537">Example</span></span>

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a><span data-ttu-id="67ce7-538">ux_device_class_audio_read_frame_get</span><span class="sxs-lookup"><span data-stu-id="67ce7-538">ux_device_class_audio_read_frame_get</span></span>

<span data-ttu-id="67ce7-539">오디오 스트림에서 오디오 프레임에 대한 액세스 권한 얻기</span><span class="sxs-lookup"><span data-stu-id="67ce7-539">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-540">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-540">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="67ce7-541">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-541">Description</span></span>

<span data-ttu-id="67ce7-542">이 함수는 지정된 스트림의 FIFO에서 첫 번째 오디오 프레임 버퍼 및 길이를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-542">This function returns the first audio frame buffer and its length in the specified stream's FIFO.</span></span> <span data-ttu-id="67ce7-543">애플리케이션에서 데이터 처리를 완료한 후에는 ux_device_class_audio_read_frame_free를 사용하여 FIFO에서 프레임 버퍼를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-543">When the application is done processing the data, ux_device_class_audio_read_frame_free must be used to free the frame buffer in the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-544">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-544">Parameters</span></span>

- <span data-ttu-id="67ce7-545">**stream**: 오디오 스트림 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-545">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="67ce7-546">**frame_data**: 데이터 포인터를 반환할 데이터 포인터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-546">**frame_data**: Pointer to data pointer to return the data pointer in.</span></span>
- <span data-ttu-id="67ce7-547">**frame_length**: 프레임 길이를 바이트 수로 저장할 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-547">**frame_length**: Pointer to buffer to save the frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-548">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-548">Return Value</span></span>

- <span data-ttu-id="67ce7-549">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-549">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인터페이스가 다운되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="67ce7-551">**UX_BUFFER_OVERFLOW** (0x5d) FIFO 버퍼가 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-551">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="67ce7-552">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-552">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-553">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-553">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a><span data-ttu-id="67ce7-554">ux_device_class_audio_read_frame_free</span><span class="sxs-lookup"><span data-stu-id="67ce7-554">ux_device_class_audio_read_frame_free</span></span>

<span data-ttu-id="67ce7-555">오디오 스트림에서 오디오 프레임 버퍼 해제</span><span class="sxs-lookup"><span data-stu-id="67ce7-555">Free an audio frame buffer in Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-556">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-556">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="67ce7-557">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-557">Description</span></span>

<span data-ttu-id="67ce7-558">이 함수는 호스트에서 데이터를 받을 수 있도록 지정된 스트림의 FIFO 앞에서 오디오 프레임 버퍼를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-558">This function frees the audio frame buffer at the front of the specified stream's FIFO so that it can receive data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-559">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-559">Parameters</span></span>

- <span data-ttu-id="67ce7-560">**stream**: 오디오 스트림 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-560">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-561">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-561">Return Value</span></span>

- <span data-ttu-id="67ce7-562">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-562">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인터페이스가 다운되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="67ce7-564">**UX_BUFFER_OVERFLOW** (0x5d) FIFO 버퍼가 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-564">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="67ce7-565">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-565">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-566">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-566">Example</span></span>

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a><span data-ttu-id="67ce7-567">ux_device_class_audio_transmission_start</span><span class="sxs-lookup"><span data-stu-id="67ce7-567">ux_device_class_audio_transmission_start</span></span>

<span data-ttu-id="67ce7-568">오디오 스트림에 대한 오디오 데이터 전송 시작</span><span class="sxs-lookup"><span data-stu-id="67ce7-568">Start audio data transmission for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-569">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-569">Prototype</span></span>

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="67ce7-570">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-570">Description</span></span>

<span data-ttu-id="67ce7-571">이 함수는 오디오 클래스에서 FIFO에 쓴 오디오 데이터 전송을 시작하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-571">This function is used to start sending audio data written to the FIFO in the audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-572">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-572">Parameters</span></span>

- <span data-ttu-id="67ce7-573">**stream**: 오디오 스트림 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-573">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-574">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-574">Return Value</span></span>

- <span data-ttu-id="67ce7-575">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-575">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인터페이스가 다운되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="67ce7-577">**UX_BUFFER_OVERFLOW** (0x5d) FIFO 버퍼가 Null입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-577">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="67ce7-578">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-578">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-579">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-579">Example</span></span>

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a><span data-ttu-id="67ce7-580">ux_device_class_audio_frame_write</span><span class="sxs-lookup"><span data-stu-id="67ce7-580">ux_device_class_audio_frame_write</span></span>

<span data-ttu-id="67ce7-581">오디오 스트림에 오디오 프레임을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-581">Write an audio frame into the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-582">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-582">Prototype</span></span>

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a><span data-ttu-id="67ce7-583">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-583">Description</span></span>

<span data-ttu-id="67ce7-584">이 함수는 오디오 스트림의 FIFO에 프레임을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-584">This function writes a frame to the audio stream's FIFO.</span></span> <span data-ttu-id="67ce7-585">프레임 데이터는 호스트에 전송될 수 있도록 FIFO에서 사용 가능한 버퍼로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-585">The frame data is copied to the available buffer in the FIFO so that it can be sent to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-586">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-586">Parameters</span></span>

- <span data-ttu-id="67ce7-587">**stream**: 오디오 스트림 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-587">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="67ce7-588">**frame**: 프레임 데이터에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="67ce7-588">**frame**: Pointer to frame data.</span></span>
- <span data-ttu-id="67ce7-589">**frame_length** 프레임 길이(바이트 수)</span><span class="sxs-lookup"><span data-stu-id="67ce7-589">**frame_length** Frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-590">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-590">Return Value</span></span>

- <span data-ttu-id="67ce7-591">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-591">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인터페이스가 다운되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="67ce7-593">**UX_BUFFER_OVERFLOW** (0x5d) FIFO 버퍼가 가득 찼습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-593">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="67ce7-594">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-594">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-595">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-595">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a><span data-ttu-id="67ce7-596">ux_device_class_audio_write_frame_get</span><span class="sxs-lookup"><span data-stu-id="67ce7-596">ux_device_class_audio_write_frame_get</span></span>

<span data-ttu-id="67ce7-597">오디오 스트림에서 오디오 프레임에 대한 액세스 권한 얻기</span><span class="sxs-lookup"><span data-stu-id="67ce7-597">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-598">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-598">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="67ce7-599">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-599">Description</span></span>

<span data-ttu-id="67ce7-600">이 함수는 FIFO의 마지막 오디오 프레임 버퍼의 주소를 검색합니다. 또한 오디오 프레임 버퍼의 길이를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-600">This function retrieves the address of the last audio frame buffer of the FIFO; it also retrieves the length of the audio frame buffer.</span></span> <span data-ttu-id="67ce7-601">애플리케이션에서 원하는 데이터로 오디오 프레임 버퍼를 채운 후에는 ***ux_device_class_audio_write_frame_commit*** 을 사용하여 FIFO에 프레임 버퍼를 추가/커밋해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-601">After the application fills the audio frame buffer with its desired data, ***ux_device_class_audio_write_frame_commit*** must be used to add/commit the frame buffer to the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-602">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-602">Parameters</span></span>

- <span data-ttu-id="67ce7-603">**stream**: 오디오 스트림 인스턴스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="67ce7-603">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="67ce7-604">**frame_data**: 프레임 데이터 포인터를 반환할 프레임 데이터에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="67ce7-604">**frame_data**: Pointer to frame data pointer to return the frame data pointer in.</span></span>
- <span data-ttu-id="67ce7-605">**frame_length** 프레임 길이를 바이트 수로 저장하는 버퍼에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="67ce7-605">**frame_length** Pointer to the buffer to save frame length in number of bytes .</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-606">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-606">Return Value</span></span>

- <span data-ttu-id="67ce7-607">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-607">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인터페이스가 다운되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="67ce7-609">**UX_BUFFER_OVERFLOW** (0x5d) FIFO 버퍼가 가득 찼습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-609">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="67ce7-610">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-610">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-611">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-611">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a><span data-ttu-id="67ce7-612">ux_device_class_audio_write_frame_commit</span><span class="sxs-lookup"><span data-stu-id="67ce7-612">ux_device_class_audio_write_frame_commit</span></span>

<span data-ttu-id="67ce7-613">오디오 스트림에서 오디오 프레임 버퍼 커밋하기</span><span class="sxs-lookup"><span data-stu-id="67ce7-613">Commit an audio frame buffer in Audio stream.</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-614">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-614">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="67ce7-615">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-615">Description</span></span>

<span data-ttu-id="67ce7-616">이 함수는 버퍼를 호스트로 전송할 준비가 되도록 마지막 오디오 프레임 버퍼를 FIFO에 추가/커밋합니다. 마지막 오디오 프레임 버퍼를 ux_device_class_write_frame_get를 통해 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-616">This function adds/commits the last audio frame buffer to the FIFO so the buffer is ready to be transferred to host; note the last audio frame buffer should have been filled out via ux_device_class_write_frame_get.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-617">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-617">Parameters</span></span>

- <span data-ttu-id="67ce7-618">**stream**: 오디오 스트림 인스턴스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="67ce7-618">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="67ce7-619">**length**: 버퍼에 준비된 바이트 수.</span><span class="sxs-lookup"><span data-stu-id="67ce7-619">**length**: Number of bytes ready in the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-620">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-620">Return Value</span></span>

- <span data-ttu-id="67ce7-621">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-621">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인터페이스가 다운되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="67ce7-623">**UX_BUFFER_OVERFLOW** (0x5d) FIFO 버퍼는 fssull입니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-623">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is fssull.</span></span>
- <span data-ttu-id="67ce7-624">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-624">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-625">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-625">Example</span></span>

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a><span data-ttu-id="67ce7-626">ux_device_class_audio10_control_process</span><span class="sxs-lookup"><span data-stu-id="67ce7-626">ux_device_class_audio10_control_process</span></span>

<span data-ttu-id="67ce7-627">USB 오디오 1.0 제어 요청 처리</span><span class="sxs-lookup"><span data-stu-id="67ce7-627">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-628">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-628">Prototype</span></span>

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="67ce7-629">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-629">Description</span></span>

<span data-ttu-id="67ce7-630">이 함수는 USB 오디오 1.0 특정 유형을 사용하여 컨트롤 끝점에서 호스트가 보낸 기본 요청을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-630">This function manages basic requests sent by the host on the control endpoint with a USB Audio 1.0 specific type.</span></span>

<span data-ttu-id="67ce7-631">볼륨 및 음소거 요청의 오디오 1.0 기능은 함수에서 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-631">Audio 1.0 features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="67ce7-632">요청을 처리할 때 마지막 매개 변수(그룹)로 전달되는 미리 정의된 데이터는 요청에 응답하고 컨트롤 변경 내용을 저장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-632">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-633">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-633">Parameters</span></span>

- <span data-ttu-id="67ce7-634">**audio**: 오디오 인스턴스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="67ce7-634">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="67ce7-635">**transfer_request** 전송 요청에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="67ce7-635">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="67ce7-636">**그룹**: 요청 프로세스에 대한 데이터 그룹.</span><span class="sxs-lookup"><span data-stu-id="67ce7-636">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-637">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-637">Return Value</span></span>

- <span data-ttu-id="67ce7-638">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-638">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-639">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-639">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-640">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-640">Example</span></span>

```C
/* Initialize audio 1.0 control values. */

audio_control[0].ux_device_class_audio10_control_fu_id = 2;
audio_control[0].ux_device_class_audio10_control_mute[0] = 0;
audio_control[0].ux_device_class_audio10_control_volume[0] = 0;
audio_control[1].ux_device_class_audio10_control_fu_id = 5;
audio_control[1].ux_device_class_audio10_control_mute[0] = 0;
audio_control[1].ux_device_class_audio10_control_volume[0] = 0;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio10_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio10_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```

## <a name="ux_device_class_audio20_control_process"></a><span data-ttu-id="67ce7-641">ux_device_class_audio20_control_process</span><span class="sxs-lookup"><span data-stu-id="67ce7-641">ux_device_class_audio20_control_process</span></span>

<span data-ttu-id="67ce7-642">USB 오디오 1.0 제어 요청 처리</span><span class="sxs-lookup"><span data-stu-id="67ce7-642">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="67ce7-643">프로토타입</span><span class="sxs-lookup"><span data-stu-id="67ce7-643">Prototype</span></span>
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="67ce7-644">Description</span><span class="sxs-lookup"><span data-stu-id="67ce7-644">Description</span></span>

<span data-ttu-id="67ce7-645">이 함수는 USB 오디오 2.0 특정 유형을 사용하여 컨트롤 끝점에서 호스트가 보낸 기본 요청을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-645">This function manages basic requests sent by the host on the control endpoint with a USB Audio 2.0 specific type.</span></span>

<span data-ttu-id="67ce7-646">오디오 2.0 샘플링 주기(단일 고정 빈도로 가정), 볼륨 및 음소거 요청의 기능은 함수에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-646">Audio 2.0 sampling rate (assumed single fixed frequency), features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="67ce7-647">요청을 처리할 때 마지막 매개 변수(그룹)로 전달되는 미리 정의된 데이터는 요청에 응답하고 컨트롤 변경 내용을 저장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-647">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="67ce7-648">매개 변수</span><span class="sxs-lookup"><span data-stu-id="67ce7-648">Parameters</span></span>

- <span data-ttu-id="67ce7-649">**audio**: 오디오 인스턴스에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="67ce7-649">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="67ce7-650">**transfer_request** 전송 요청에 대한 포인터.</span><span class="sxs-lookup"><span data-stu-id="67ce7-650">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="67ce7-651">**그룹**: 요청 프로세스에 대한 데이터 그룹.</span><span class="sxs-lookup"><span data-stu-id="67ce7-651">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="67ce7-652">반환 값</span><span class="sxs-lookup"><span data-stu-id="67ce7-652">Return Value</span></span>

- <span data-ttu-id="67ce7-653">**UX_SUCCESS** (0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67ce7-653">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="67ce7-654">**UX_ERROR** (0xFF) 함수에서 오류 발생</span><span class="sxs-lookup"><span data-stu-id="67ce7-654">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="67ce7-655">예제</span><span class="sxs-lookup"><span data-stu-id="67ce7-655">Example</span></span>

```C
/* Initialize audio 2.0 control values. */

audio_control[0].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[0].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[0].ux_device_class_audio20_control_fu_id = 2;
audio_control[0].ux_device_class_audio20_control_mute[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[0].ux_device_class_audio20_control_volume[0] = 50;
audio_control[1].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[1].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[1].ux_device_class_audio20_control_fu_id = 5;
audio_control[1].ux_device_class_audio20_control_mute[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[1].ux_device_class_audio20_control_volume[0] = 50;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio20_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio20_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```
