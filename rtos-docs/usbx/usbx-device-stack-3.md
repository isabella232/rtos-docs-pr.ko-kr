---
title: 3장 - USBX 디바이스 스택의 기능 구성 요소
description: 이 장에는 기능 관점에서 고성능 USBX 임베디드 USB 디바이스 스택에 대한 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a20fed71cbee8c50519be4a971eb191e0cc93915
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812241"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a><span data-ttu-id="d78a7-103">3장 - USBX 디바이스 스택의 기능 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d78a7-103">Chapter 3 - Functional Components of USBX Device Stack</span></span>

<span data-ttu-id="d78a7-104">이 장에는 기능 관점에서 고성능 USBX 임베디드 USB 디바이스 스택에 대한 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-104">This chapter contains a description of the high performance USBX embedded USB device stack from a functional perspective.</span></span>

## <a name="execution-overview"></a><span data-ttu-id="d78a7-105">실행 개요</span><span class="sxs-lookup"><span data-stu-id="d78a7-105">Execution Overview</span></span>

<span data-ttu-id="d78a7-106">디바이스에 대한 USBX는 여러 구성 요소로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-106">USBX for the device is composed of several components.</span></span>

- <span data-ttu-id="d78a7-107">초기화</span><span class="sxs-lookup"><span data-stu-id="d78a7-107">Initialization</span></span>
- <span data-ttu-id="d78a7-108">애플리케이션 인터페이스 호출</span><span class="sxs-lookup"><span data-stu-id="d78a7-108">Application interface calls</span></span>
- <span data-ttu-id="d78a7-109">디바이스 클래스</span><span class="sxs-lookup"><span data-stu-id="d78a7-109">Device Classes</span></span>
- <span data-ttu-id="d78a7-110">USB 디바이스 스택</span><span class="sxs-lookup"><span data-stu-id="d78a7-110">USB Device Stack</span></span>
- <span data-ttu-id="d78a7-111">디바이스 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="d78a7-111">Device controller</span></span>
- <span data-ttu-id="d78a7-112">VBUS 관리자</span><span class="sxs-lookup"><span data-stu-id="d78a7-112">VBUS manager</span></span>

<span data-ttu-id="d78a7-113">다음 다이어그램에서는 USBX 디바이스 스택을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-113">The following diagram illustrates the USBX Device stack.</span></span>

![USBX 디바이스 스택](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a><span data-ttu-id="d78a7-115">초기화</span><span class="sxs-lookup"><span data-stu-id="d78a7-115">Initialization</span></span>

<span data-ttu-id="d78a7-116">USBX를 활성화하기 위해 ***ux_system_initialize*** 함수를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-116">In order to activate USBX, the function ***ux_system_initialize*** must be called.</span></span> <span data-ttu-id="d78a7-117">이 함수는 USBX에 대한 메모리 리소스를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-117">This function initializes the memory resources of USBX.</span></span>

<span data-ttu-id="d78a7-118">USBX 디바이스 기능을 활성화하기 위해 ***ux_device_stack_initialize*** 함수를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-118">In order to activate USBX device facilities, the function ***ux_device_stack_initialize*** must be called.</span></span> <span data-ttu-id="d78a7-119">이 함수는 ThreadX 스레드, 뮤텍스 및 세마포와 같은 USBX 디바이스 스택에서 사용하는 모든 리소스를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-119">This function will in turn initialize all the resources used by the USBX device stack such as ThreadX threads, mutexes, and semaphores.</span></span>

<span data-ttu-id="d78a7-120">USB 디바이스 컨트롤러 및 하나 이상의 USB 클래스를 활성화하는 것은 애플리케이션 초기화에 달려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-120">It is up to the application initialization to activate the USB device controller and one or more USB classes.</span></span> <span data-ttu-id="d78a7-121">USB 호스트 쪽과는 반대로, 디바이스 쪽에는 언제든지 실행되는 USB 컨트롤러 드라이버가 하나만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-121">Contrary to the USB host side, the device side can have only one USB controller driver running at any time.</span></span> <span data-ttu-id="d78a7-122">클래스가 스택에 등록되고 디바이스 컨트롤러 초기화 함수가 호출되면 버스가 활성화되고 스택이 버스 다시 설정 및 호스트 열거 명령에 대해 회신하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-122">When the classes have been registered to the stack and the device controller(s) initialization function has been called, the bus is active and the stack will reply to bus reset and host enumeration commands.</span></span>

### <a name="application-interface-calls"></a><span data-ttu-id="d78a7-123">애플리케이션 인터페이스 호출</span><span class="sxs-lookup"><span data-stu-id="d78a7-123">Application Interface Calls</span></span>

<span data-ttu-id="d78a7-124">USBX에는 두 가지 수준의 API가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-124">There are two levels of APIs in USBX.</span></span>

- <span data-ttu-id="d78a7-125">USB 디바이스 스택 API</span><span class="sxs-lookup"><span data-stu-id="d78a7-125">USB Device Stack APIs</span></span>
- <span data-ttu-id="d78a7-126">USB 디바이스 클래스 API</span><span class="sxs-lookup"><span data-stu-id="d78a7-126">USB Device Class APIs</span></span>

<span data-ttu-id="d78a7-127">일반적으로, USBX 애플리케이션은 USB 디바이스 스택 API를 호출하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-127">Normally, a USBX application should not have to call any of the USB device stack APIs.</span></span> <span data-ttu-id="d78a7-128">대부분의 애플리케이션은 USB 클래스 API에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-128">Most applications will only access the USB Class APIs.</span></span>

### <a name="usb-device-stack-apis"></a><span data-ttu-id="d78a7-129">USB 디바이스 스택 API</span><span class="sxs-lookup"><span data-stu-id="d78a7-129">USB Device Stack APIs</span></span>

<span data-ttu-id="d78a7-130">디바이스 스택 API는 클래스 및 디바이스 프레임워크와 같은 USBX 디바이스 구성 요소를 등록하는 일을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-130">The device stack APIs are responsible for the registration of USBX device components such as classes and the device framework.</span></span>

### <a name="usb-device-class-apis"></a><span data-ttu-id="d78a7-131">USB 디바이스 클래스 API</span><span class="sxs-lookup"><span data-stu-id="d78a7-131">USB Device Class APIs</span></span>

<span data-ttu-id="d78a7-132">클래스 API는 각 USB 클래스에 매우 한정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-132">The Class APIs are very specific to each USB class.</span></span> <span data-ttu-id="d78a7-133">USB 클래스에 대한 일반적인 API는 대부분 디바이스 열기/닫기, 디바이스에서 읽기 및 쓰기와 같은 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-133">Most of the common APIs for USB classes provided services such as opening/closing a device and reading from and writing to a device.</span></span> <span data-ttu-id="d78a7-134">API는 호스트 쪽의 특성과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-134">The APIs are similar in nature to the host side.</span></span>

## <a name="device-framework"></a><span data-ttu-id="d78a7-135">디바이스 프레임워크</span><span class="sxs-lookup"><span data-stu-id="d78a7-135">Device Framework</span></span>

<span data-ttu-id="d78a7-136">USB 디바이스 쪽은 디바이스 프레임워크의 정의를 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-136">The USB device side is responsible for the definition of the device framework.</span></span> <span data-ttu-id="d78a7-137">다음 섹션에 설명된 것처럼 디바이스 프레임워크는 세 가지 범주로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-137">The device framework is divided into three categories, as described in the following sections.</span></span>

### <a name="definition-of-the-components-of-the-device-framework"></a><span data-ttu-id="d78a7-138">디바이스 프레임워크의 구성 요소 정의</span><span class="sxs-lookup"><span data-stu-id="d78a7-138">Definition of the Components of the Device Framework</span></span>

<span data-ttu-id="d78a7-139">디바이스 프레임워크의 각 구성 요소에 대한 정의는 디바이스 특성 및 디바이스에서 사용하는 리소스와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-139">The definition of each component of the device framework is related to the nature of the device and the resources utilized by the device.</span></span> <span data-ttu-id="d78a7-140">다음은 주요 범주입니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-140">Following are the main categories.</span></span>

- <span data-ttu-id="d78a7-141">디바이스 설명자</span><span class="sxs-lookup"><span data-stu-id="d78a7-141">Device Descriptor</span></span>
- <span data-ttu-id="d78a7-142">구성 설명자</span><span class="sxs-lookup"><span data-stu-id="d78a7-142">Configuration Descriptor</span></span>
- <span data-ttu-id="d78a7-143">인터페이스 설명자</span><span class="sxs-lookup"><span data-stu-id="d78a7-143">Interface Descriptor</span></span>
- <span data-ttu-id="d78a7-144">엔드포인트 설명자</span><span class="sxs-lookup"><span data-stu-id="d78a7-144">Endpoint Descriptor</span></span>

<span data-ttu-id="d78a7-145">USBX는 고속 및 전속(full speed) 모두에 대한 디바이스 구성 요소 정의를 지원합니다(저속은 전속과 동일하게 취급).</span><span class="sxs-lookup"><span data-stu-id="d78a7-145">USBX supports device component definition for both high and full speed (low speed being treated the same way as full speed).</span></span> <span data-ttu-id="d78a7-146">이를 통해 속도가 고속 또는 전속 호스트에 연결된 경우 디바이스가 다르게 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-146">This allows the device to operate differently when connected to a high speed or full speed host.</span></span> <span data-ttu-id="d78a7-147">일반적인 차이점은 각 엔드포인트의 크기와 디바이스에서 사용하는 전원입니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-147">The typical differences are the size of each endpoint and the power consumed by the device.</span></span>

<span data-ttu-id="d78a7-148">디바이스 구성 요소의 정의는 USB 사양 뒤에 오는 바이트 문자열 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-148">The definition of the device component takes the form of a byte string that follows the USB specification.</span></span> <span data-ttu-id="d78a7-149">정의는 연속되며 프레임워크가 메모리에 표시되는 순서는 열거하는 동안 호스트에 반환된 순서와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-149">The definition is contiguous and the order in which the framework is represented in memory will be the same as the one returned to the host during enumeration.</span></span>

<span data-ttu-id="d78a7-150">다음은 고속 USB 플래시 디스크에 대한 디바이스 프레임워크의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-150">Following is an example of a device framework for a high speed USB Flash Disk.</span></span>

```c
#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60
UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02, 0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50, 0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};
```

### <a name="definition-of-the-strings-of-the-device-framework"></a><span data-ttu-id="d78a7-151">디바이스 프레임워크의 문자열 정의</span><span class="sxs-lookup"><span data-stu-id="d78a7-151">Definition of the Strings of the Device Framework</span></span>

<span data-ttu-id="d78a7-152">디바이스에서 문자열은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-152">Strings are optional in a device.</span></span> <span data-ttu-id="d78a7-153">이는 유니코드 문자열을 통해 USB 호스트에서 디바이스의 제조업체, 제품 이름 및 수정 버전을 알 수 있도록 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-153">Their purpose is to let the USB host know about the manufacturer of the device, the product name, and the revision number through Unicode strings.</span></span>

<span data-ttu-id="d78a7-154">주 문자열은 디바이스 설명자에 포함된 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-154">The main strings are indexes embedded in the device descriptors.</span></span> <span data-ttu-id="d78a7-155">추가 문자열 인덱스는 개별 인터페이스에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-155">Additional strings indexes can be embedded into individual interfaces.</span></span>

<span data-ttu-id="d78a7-156">위의 디바이스 프레임워크에서 디바이스 설명자에 포함된 세 개의 문자열 인덱스가 있다고 가정하면 문자열 프레임워크 정의는 이 예제 코드처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-156">Assuming the device framework above has three string indexes embedded into the device descriptor, the string framework definition could look like this example code.</span></span>

```c
/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string
*/

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};
```

<span data-ttu-id="d78a7-157">각 속도에 대해 서로 다른 문자열을 사용해야 하는 경우 인덱스는 속도에 구애 받지 않으므로 다른 인덱스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-157">If different strings have to be used for each speed, different indexes must be used as the indexes are speed agnostic.</span></span>

<span data-ttu-id="d78a7-158">문자열의 인코딩은 UNICODE 기반입니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-158">The encoding of the string is UNICODE-based.</span></span> <span data-ttu-id="d78a7-159">UNICODE 인코딩 표준에 대한 자세한 내용은 다음 간행물을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d78a7-159">For more information on the UNICODE encoding standard refer to the following publication:</span></span>

<span data-ttu-id="d78a7-160">*유니코드 표준, 전 세계 문자 인코딩, 버전 1., 1권 및 2권, 유니코드 컨소시엄, Addison-Wesley 출판사, Reading MA.*</span><span class="sxs-lookup"><span data-stu-id="d78a7-160">*The Unicode Standard, Worldwide Character Encoding, Version 1., Volumes 1 and 2, The Unicode Consortium, Addison-Wesley Publishing Company, Reading MA.*</span></span>

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a><span data-ttu-id="d78a7-161">각 문자열에 대해 디바이스에서 지원하는 언어의 정의</span><span class="sxs-lookup"><span data-stu-id="d78a7-161">Definition of the Languages Supported by the Device for each String</span></span>

<span data-ttu-id="d78a7-162">기본값은 영어이지만, USBX는 여러 언어를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-162">USBX has the ability to support multiple languages although English is the default.</span></span> <span data-ttu-id="d78a7-163">문자열 설명자에 대한 각 언어의 정의는 다음과 같이 정의된 언어 정의의 배열 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-163">The definition of each language for the string descriptors is in the form of an array of languages definition defined as follows.</span></span>

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="d78a7-164">추가 언어를 지원하려면 기본 영어 코드 뒤에 언어 코드 더블 바이트 정의를 추가하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-164">To support additional languages, simply add the language code double-byte definition after the default English code.</span></span> <span data-ttu-id="d78a7-165">언어 코드는 문서에서 Microsoft에 의해 정의되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-165">The language code has been defined by Microsoft in the document.</span></span>

<span data-ttu-id="d78a7-166">*Windows 95 및 Windows NT용 국제 소프트웨어 개발, Nadine Kano, Microsoft Press, Redmond WA*</span><span class="sxs-lookup"><span data-stu-id="d78a7-166">*Developing International Software for Windows 95 and Windows NT, Nadine Kano, Microsoft Press, Redmond WA*</span></span>

## <a name="vbus-manager"></a><span data-ttu-id="d78a7-167">VBUS 관리자</span><span class="sxs-lookup"><span data-stu-id="d78a7-167">VBUS Manager</span></span>

<span data-ttu-id="d78a7-168">대부분의 USB 디바이스 디자인에서 VBUS는 USB 디바이스 코어의 일부가 아니지만, 외부 GPIO에 연결되며, 이는 선 신호를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-168">In most USB device designs, VBUS is not part of the USB Device core but rather connected to an external GPIO, which monitors the line signal.</span></span>

<span data-ttu-id="d78a7-169">따라서 VBUS는 디바이스 컨트롤러 드라이버와 별도로 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-169">As a result, VBUS has to be managed separately from the device controller driver.</span></span>

<span data-ttu-id="d78a7-170">디바이스 컨트롤러에 VBUS IO 주소를 제공하는 것은 애플리케이션에 달려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-170">It is up to the application to provide the device controller with the address of the VBUS IO.</span></span> <span data-ttu-id="d78a7-171">디바이스 컨트롤러를 초기화하기 전에 VBUS를 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-171">VBUS must be initialized prior to the device controller initialization.</span></span>

<span data-ttu-id="d78a7-172">VBUS 모니터링에 대한 플랫폼 사양에 따라 VBUS IO가 초기화된 후 컨트롤러 드라이버에서 VBUS 신호를 처리하도록 할 수 있습니다. 이것이 불가능한 경우 애플리케이션이 VBUS를 처리하는 코드를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-172">Depending on the platform specification for monitoring VBUS, it is possible to let the controller driver handle VBUS signals after the VBUS IO is initialized or if this is not possible, the application has to provide the code for handling VBUS.</span></span>

<span data-ttu-id="d78a7-173">애플리케이션에서 VBUS를 자체적으로 처리하려는 경우에는 디바이스가 추출된 것을 감지했을 때 ***ux_device_stack_disconnect*** 함수를 호출하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-173">If the application wishes to handle VBUS by itself, its only requirement is to call the function ***ux_device_stack_disconnect*** when it detects that a device has been extracted.</span></span> <span data-ttu-id="d78a7-174">버스 다시 설정 어설션/디어설션 신호가 감지되면 컨트롤러가 절전 모드에서 해제되므로 디바이스가 삽입될 때 컨트롤러에 알릴 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d78a7-174">It is not necessary to inform the controller when a device is inserted because the controller will wake up when the BUS RESET assert/deassert signal is detected.</span></span>
