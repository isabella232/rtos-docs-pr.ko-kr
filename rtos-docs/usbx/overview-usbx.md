---
title: Azure RTOS USBX 이해
description: Azure RTOS USBX는 고성능 USB 호스트, 디바이스 및 OTG(On-The-Go) 포함 스택으로, Azure RTOS ThreadX와 완전히 통합되며 모든 Azure RTOS ThreadX 지원 프로세서에서 사용할 수 있습니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 87eb6ee9f8733db3201280d377aa832b87131871
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813285"
---
# <a name="overview-of-azure-rtos-usbx"></a><span data-ttu-id="ad549-103">Azure RTOS USBX 개요</span><span class="sxs-lookup"><span data-stu-id="ad549-103">Overview of Azure RTOS USBX</span></span>

<span data-ttu-id="ad549-104">Azure RTOS USBX는 고성능의 USB 호스트, 디바이스 및 OTG(On-The-Go) 포함 스택입니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-104">Azure RTOS USBX is a high-performance USB host, device, and on-the-go (OTG) embedded stack.</span></span> <span data-ttu-id="ad549-105">Azure RTOS USBX는 Azure RTOS ThreadX와 완전히 통합되며 모든 ThreadX 지원 프로세서에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-105">Azure RTOS USBX is fully integrated with Azure RTOS ThreadX and available for all ThreadX–supported processors.</span></span> <span data-ttu-id="ad549-106">Azure RTOS USBX는 ThreadX와 마찬가지로 메모리 공간을 적게 차지하면서 고성능을 제공하도록 설계되었으므로 USB 디바이스와 인터페이스가 필요한 긴밀하게 포함된 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-106">Like ThreadX, Azure RTOS USBX is designed to have a small footprint and high performance, making it ideal for deeply embedded applications that require an interface with USB devices.</span></span>

## <a name="host-device-otg--extensive-class-support"></a><span data-ttu-id="ad549-107">호스트, 디바이스, OTG 및 광범위 클래스 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-107">Host, Device, OTG & Extensive Class Support</span></span>

<span data-ttu-id="ad549-108">Azure RTOS USBX 호스트/디바이스 포함 USB 프로토콜 스택은 포함 수준이 높은 실시간 IoT 애플리케이션 전용으로 설계된 산업 등급 포함 USB 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-108">Azure RTOS USBX Host/Device embedded USB protocol stack is an Industrial Grade embedded USB solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="ad549-109">Azure RTOS USBX는 호스트, 디바이스, OTG 지원과, 광범위 클래스 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-109">Azure RTOS USBX provides host, device, and OTG support, as well as extensive class support.</span></span> <span data-ttu-id="ad549-110">Azure RTOS USBX는 ThreadX 실시간 운영 체제, Azure RTOS FileX 포함 FAT 호환 파일 시스템, Azure RTOS NetX 및 Azure RTOS NetX Duo 포함 TCP/IP 스택에 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-110">Azure RTOS USBX is fully integrated with ThreadX Real-Time Operating System, Azure RTOS FileX embedded FAT-compatible file system, Azure RTOS NetX, and Azure RTOS NetX Duo embedded TCP/IP stacks.</span></span> <span data-ttu-id="ad549-111">이뿐 아니라 Azure RTOS USBX는 매우 적은 메모리 공간에서 고속 실행과 뛰어난 사용 편의성을 구현하므로, USB 연결이 요구되는 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-111">All of this, combined with an extremely small footprint, fast execution and superior ease-of-use, make Azure RTOS USBX the ideal choice for the most demanding embedded IoT applications requiring USB connectivity.</span></span>

### <a name="small-footprint"></a><span data-ttu-id="ad549-112">적은 메모리 공간</span><span class="sxs-lookup"><span data-stu-id="ad549-112">Small-footprint</span></span>

<span data-ttu-id="ad549-113">Azure RTOS USBX는 Azure RTOS USBX 디바이스 CDC/ACM 지원을 위한 최소 메모리 공간이 10.5KB FLASH, 5.1KB RAM으로, 매우 적습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-113">Azure RTOS USBX has a remarkably small minimal footprint of 10.5 KB of FLASH and 5.1 KB RAM for Azure RTOS USBX Device CDC/ACM support.</span></span> <span data-ttu-id="ad549-114">Azure RTOS USBX 호스트에서는 CDC/ACM 지원에 최소 18KB FLASH와 25KB RAM이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-114">Azure RTOS USBX Host requires a minimum of 18 KB of FLASH and 25 KB of RAM for CDC/ACM support.</span></span>

<span data-ttu-id="ad549-115">TCP 기능을 위해서는 추가적으로 10 ~ 13KB의 명령 영역 메모리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-115">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="ad549-116">Azure RTOS USBX RAM 사용량은 일반적으로 2.6KB에서 3.6KB까지이며, 애플리케이션에 의해 정의되는 패킷 풀 메모리를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-116">Azure RTOS USBX RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span>

<span data-ttu-id="ad549-117">ThreadX와 같이 Azure RTOS USBX의 크기는 애플리케이션에서 실제 사용하는 서비스에 따라 자동으로 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-117">Like ThreadX, the size of Azure RTOS USBX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="ad549-118">이렇게 하면 사실상 복잡한 구성 및 빌드 매개 변수가 제거되어 개발자가 더 쉽게 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-118">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

### <a name="fast-execution"></a><span data-ttu-id="ad549-119">고속 실행</span><span class="sxs-lookup"><span data-stu-id="ad549-119">Fast execution</span></span>

<span data-ttu-id="ad549-120">빠른 속도를 위해 설계된 Azure RTOS USBX는 내부 함수 호출 계층화가 최소 수준이며, 캐시 및 DMA 사용률을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-120">Azure RTOS USBX is designed for speed and has minimal internal function call layering and support for cache and DMA utilization.</span></span> <span data-ttu-id="ad549-121">이런 특징과 일반 성능 중심 디자인 철학으로 Azure RTOS USBX에서 가능한 가장 빠른 성능을 구현하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-121">All of this and a general performance-oriented design philosophy helps Azure RTOS USBX achieve the fastest possible performance.</span></span>

### <a name="simple-easy-to-use"></a><span data-ttu-id="ad549-122">간단하고 손쉬운 사용</span><span class="sxs-lookup"><span data-stu-id="ad549-122">Simple, easy-to-use</span></span>

<span data-ttu-id="ad549-123">Azure RTOS USBX는 사용이 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-123">Azure RTOS USBX is simple to use.</span></span> <span data-ttu-id="ad549-124">Azure RTOS USBX API는 직관적이고 매우 기능적입니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-124">The Azure RTOS USBX API is both intuitive and highly functional.</span></span> <span data-ttu-id="ad549-125">API 이름은 다른 파일 시스템에서 흔히 볼 수 있는 매우 축약된 이름의 알파벳 약자가 아니라 실제 단어로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-125">The API names are made of real words and not the "alphabet soup" or highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="ad549-126">모든 Azure RTOS USBX API에는 선행 "ux_"가 있으며 명사-동사 명명 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-126">All Azure RTOS USBX APIs have a leading "ux_" and follow a noun-verb naming convention.</span></span> <span data-ttu-id="ad549-127">또한 API 전체에 걸쳐 기능적 일관성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-127">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="ad549-128">예를 들어 일시 중단된 모든 API는 API에 대해 동일한 방식으로 작동하는 선택적 시간 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-128">For example, all APIs that suspend have an optional timeout that functions in an identical manner for APIs.</span></span>

### <a name="usb-interoperability-verification"></a><span data-ttu-id="ad549-129">USB 상호 운용성 확인</span><span class="sxs-lookup"><span data-stu-id="ad549-129">USB Interoperability verification</span></span>

<span data-ttu-id="ad549-130">Azure RTOS USBX 디바이스 스택은 완벽한 USB 규정 준수와 다양한 시스템과의 상호 운용성을 보장하기 위해, USB IF 표준 테스트 도구 USBCV로 엄격히 테스트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-130">Azure RTOS USBX Device Stack has been rigorously tested with the USB IF standard testing tool USBCV to ensure full compliance with the USB specifications and interoperability with different host systems.</span></span>
<span data-ttu-id="ad549-131">또한 Azure RTOS USBX OTG 스택은 대만의 독립적인 테스트 랩 Allion 확인 및 인증을 거쳤습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-131">In addition, Azure RTOS USBX OTG stack has been verified and certified by the independent test lab Allion in Taiwan.</span></span>

### <a name="usb-host-controller-support"></a><span data-ttu-id="ad549-132">USB 호스트 컨트롤러 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-132">USB Host controller support</span></span>

<span data-ttu-id="ad549-133">Azure RTOS USBX는 OHCI 및 EHCI 같은 주요 USB 표준을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-133">Azure RTOS USBX supports major USB standards like OHCI and EHCI.</span></span> <span data-ttu-id="ad549-134">또한 Azure RTOS USBX는 Atmel, Microchip, Philips, Renesas, ST, TI 및 기타 공급업체에서 제공하는 독점적인 개별 USB 호스트 컨트롤러를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-134">In addition, Azure RTOS USBX supports proprietary discrete USB host controllers from Atmel, Microchip, Philips, Renesas, ST, TI, and other vendors.</span></span> <span data-ttu-id="ad549-135">Azure RTOS USBX는 동일한 애플리케이션에서 여러 호스트 컨트롤러도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-135">Azure RTOS USBX also supports multiple host controllers in the same application.</span></span>
<span data-ttu-id="ad549-136">USB 디바이스 컨트롤러. Azure RTOS USBX는 Analog Devices, Atmel, Microchip, NXP, Philips, Renesas, ST, TI 및 기타 공급업체의 주요 USB 디바이스 컨트롤러를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-136">USB Device controller support Azure RTOS USBX supports popular USB device controllers from Analog Devices, Atmel, Microchip, NXP, Philips, Renesas, ST, TI, and other vendors.</span></span>

### <a name="extensive-host-class-support"></a><span data-ttu-id="ad549-137">광범위한 호스트 클래스 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-137">Extensive Host Class support</span></span>

<span data-ttu-id="ad549-138">Azure RTOS USBX 호스트는 ASIX, AUDIO, CDC/ACM, CDC/ECM, GSER, HID(키보드, 마우스 및 원격 제어), HUB, PIMA(PTP/MTP), 프린터, PROLIFIC 및 스토리지를 비롯한 주요 클래스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-138">Azure RTOS USBX Host provides support for most popular classes, including ASIX, AUDIO, CDC/ACM, CDC/ECM, GSER, HID (keyboard, mouse, and remote control), HUB, PIMA (PTP/MTP), PRINTER, PROLIFIC, and STORAGE.</span></span>

### <a name="extensive-usb-device-class-support"></a><span data-ttu-id="ad549-139">광범위한 USB 디바이스 클래스 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-139">Extensive USB Device Class support</span></span>

<span data-ttu-id="ad549-140">Azure RTOS USBX 디바이스는 CDC/ACM, CDC/ECM, DFU, HID, PIMA(PTP/MTP) (w/MTP), RNDIS 및 스토리지를 비롯한 주요 클래스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-140">Azure RTOS USBX Device provides support for most popular classes, including CDC/ACM, CDC/ECM, DFU, HID, PIMA (PTP/MTP) (w/MTP), RNDIS, and STORAGE.</span></span> <span data-ttu-id="ad549-141">사용자 지정 클래스에 대한 지원도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-141">Support for custom classes is also available.</span></span>

### <a name="pictbridge-support"></a><span data-ttu-id="ad549-142">Pictbridge 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-142">Pictbridge support</span></span>

<span data-ttu-id="ad549-143">Azure RTOS USBX는 호스트와 디바이스 모두에서 전체 Pictbridge 구현을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-143">Azure RTOS USBX supports the full Pictbridge implementation both on the host and the device.</span></span> <span data-ttu-id="ad549-144">Pictbridge는 양쪽 모두에서 Azure RTOS USBX PIMA(PTP/MTP) 클래스 위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-144">Pictbridge sits on top of Azure RTOS USBX PIMA (PTP/MTP) class on both sides.</span></span> <span data-ttu-id="ad549-145">PictBridge 표준을 사용하면 디지털 스틸 카메라 또는 스마트폰을 PC 없이 프린터에 직접 연결하여 특정 Pictbridge 인식 프린터에 직접 인쇄할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-145">The PictBridge standard allows the connection of a digital still camera or a smart phone directly to a printer without a PC, enabling direct printing to certain Pictbridge aware printers.</span></span> <span data-ttu-id="ad549-146">카메라 또는 휴대폰이 프린터에 연결된 경우 프린터는 USB 호스트이고 카메라는 USB 디바이스입니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-146">When a camera or phone is connected to a printer, the printer is the USB host and the camera is the USB device.</span></span> <span data-ttu-id="ad549-147">그러나 Pictbridge를 사용하면 카메라가 호스트로 표시되고 명령은 카메라에서 구동됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-147">However, with Pictbridge, the camera will appear as being the host and commands are driven from the camera.</span></span> <span data-ttu-id="ad549-148">카메라는 스토리지 서버이며, 프린터는 스토리지 클라이언트입니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-148">The camera is the storage server, the printer the storage client.</span></span> <span data-ttu-id="ad549-149">카메라는 인쇄 클라이언트이며 프린터는 당연히 인쇄 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-149">The camera is the print client and the printer is of course the print server.</span></span> <span data-ttu-id="ad549-150">Pictbridge는 USB를 전송 계층으로 사용하지만 통신 프로토콜에 대한 PTP(사진 전송 프로토콜)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-150">Pictbridge uses USB as a transport layer but relies on PTP (Picture Transfer Protocol) for the communication protocol.</span></span>

### <a name="custom-class-support"></a><span data-ttu-id="ad549-151">사용자 지정 클래스 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-151">Custom class support</span></span>

<span data-ttu-id="ad549-152">Azure RTOS USBX의 호스트 및 디바이스는 사용자 지정 클래스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-152">Azure RTOS USBX Host and Device support custom classes.</span></span> <span data-ttu-id="ad549-153">예제 사용자 지정 클래스는Azure RTOS USBX 배포에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-153">An example custom class is provided in the Azure RTOS USBX distribution.</span></span> <span data-ttu-id="ad549-154">이 간단한 데이터 펌프 클래스를 DPUMP라 하며, 사용자 지정 애플리케이션 클래스의 모델로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-154">This simple data pump class is called DPUMP and can be used as a model for custom application classes.</span></span>
<span data-ttu-id="ad549-155">고급 기술 Azure RTOS USBX 호스트 및 디바이스는 사용자 지정 클래스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-155">Advanced technology Azure RTOS USBX Host and Device support custom classes.</span></span> <span data-ttu-id="ad549-156">예제 사용자 지정 클래스는Azure RTOS USBX 배포에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-156">An example custom class is provided in the Azure RTOS USBX distribution.</span></span> <span data-ttu-id="ad549-157">Azure RTOS USBX는 다음을 포함하는 고급 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-157">Azure RTOS USBX is advanced technology that includes:</span></span>

* <span data-ttu-id="ad549-158">호스트, 디바이스 및 OTG 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-158">Host, Device, and OTG support</span></span>
* <span data-ttu-id="ad549-159">USB 낮음, 전체 및 고속 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-159">USB low, full, and high-speed support</span></span>
* <span data-ttu-id="ad549-160">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-160">Automatic scaling</span></span>
* <span data-ttu-id="ad549-161">ThreadX, Azure RTOS FileX 및 Azure RTOS NetX 완전 통합</span><span class="sxs-lookup"><span data-stu-id="ad549-161">Fully integrated with ThreadX, Azure RTOS FileX, and Azure RTOS NetX</span></span>
* <span data-ttu-id="ad549-162">선택적 성능 메트릭</span><span class="sxs-lookup"><span data-stu-id="ad549-162">Optional performance metrics</span></span>
* <span data-ttu-id="ad549-163">Azure RTOS TraceX 시스템 분석 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-163">Azure RTOS TraceX system analysis support</span></span>

### <a name="fastest-time-to-market"></a><span data-ttu-id="ad549-164">가장 빠른 출시 시간</span><span class="sxs-lookup"><span data-stu-id="ad549-164">Fastest time-to-market</span></span>

<span data-ttu-id="ad549-165">Azure RTOS USBX는 기본 IP 및 UDP 지원을 위한 메모리 공간이 9 ~ 15KB로 매우 적습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-165">Azure RTOS USBX has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="ad549-166">Azure RTOS USBX는 설치, 학습, 사용, 디버그, 확인, 인증 및 유지 관리를 손쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-166">Azure RTOS USBX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="ad549-167">이 덕분에 Azure RTOS USBX는 포함된 IoT 디바이스에 가장 널리 사용되는 USB 솔루션 중 하나가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-167">As a result, Azure RTOS USBX is one of the most popular USB solutions for embedded IoT devices.</span></span> <span data-ttu-id="ad549-168">일관적인 출시 시간 이점은 다음을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-168">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="ad549-169">품질 설명서 – Azure RTOS USBX 호스트 및 디바이스 사용자 가이드를 검토하고 직접 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-169">Quality documentation – please review our Azure RTOS USBX Host and Device User Guides and see for yourself!</span></span>
* <span data-ttu-id="ad549-170">전체 소스 코드 가용성</span><span class="sxs-lookup"><span data-stu-id="ad549-170">Complete source code availability</span></span>
* <span data-ttu-id="ad549-171">사용하기 쉬운 API</span><span class="sxs-lookup"><span data-stu-id="ad549-171">Easy-to-use API</span></span>
* <span data-ttu-id="ad549-172">포괄적인 고급 기능 세트</span><span class="sxs-lookup"><span data-stu-id="ad549-172">Comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="ad549-173">하나의 간단한 라이선스</span><span class="sxs-lookup"><span data-stu-id="ad549-173">One Simple License</span></span>

<span data-ttu-id="ad549-174">사전에 사용이 허가된 디바이스에 배포하는 경우에는 소스 코드를 사용 및 테스트하는 데 비용이 들지 않으며 프로덕션 라이선스에 대한 비용도 부과되지 않습니다. 다른 모든 디바이스에는 간단한 연간 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-174">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="ad549-175">최고 품질의 전체 소스 코드</span><span class="sxs-lookup"><span data-stu-id="ad549-175">Full, highest-quality source code</span></span>

<span data-ttu-id="ad549-176">오랜 시간을 통해 Azure RTOS NetX 소스 코드는 품질 및 이해 용이성의 기준을 정립했습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-176">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="ad549-177">또한 파일당 하나의 함수를 포함하는 규칙을 통해 손쉬운 소스 탐색을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-177">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

### <a name="supports-most-popular-architectures"></a><span data-ttu-id="ad549-178">대부분의 주요 아키텍처 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-178">Supports most popular architectures</span></span>

<span data-ttu-id="ad549-179">Azure RTOS USBX는 완전한 테스트와 지원을 통해 다음과 같이 대부분의 주요 32/64비트 마이크로프로세서에서 실행되며, 바로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-179">Azure RTOS USBX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

* <span data-ttu-id="ad549-180">**아날로그 디바이스**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="ad549-180">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>
* <span data-ttu-id="ad549-181">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="ad549-181">**Andes Core**: RISC-V</span></span>
* <span data-ttu-id="ad549-182">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="ad549-182">**Ambiqmicro**: Apollo MCUs</span></span>
* <span data-ttu-id="ad549-183">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64비트/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="ad549-183">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>
* <span data-ttu-id="ad549-184">**Cadence**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="ad549-184">**Cadence**: Xtensa, Diamond</span></span>
* <span data-ttu-id="ad549-185">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="ad549-185">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>
* <span data-ttu-id="ad549-186">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="ad549-186">**Cypress**: RISC-V</span></span>
* <span data-ttu-id="ad549-187">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="ad549-187">**EnSilica**: eSi-RISC</span></span>
* <span data-ttu-id="ad549-188">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="ad549-188">**Infineon**: XMC1000, XMC4000, TriCore</span></span>
* <span data-ttu-id="ad549-189">**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="ad549-189">**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>
* <span data-ttu-id="ad549-190">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="ad549-190">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>
* <span data-ttu-id="ad549-191">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="ad549-191">**Microsemi**: RISC-V</span></span>
* <span data-ttu-id="ad549-192">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="ad549-192">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>
* <span data-ttu-id="ad549-193">**Renesas**: SH, HS, V850, RX, RZ, Synergy Silicon Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="ad549-193">**Renesas**: SH, HS, V850, RX, RZ, Synergy Silicon Labs: EFM32</span></span>
* <span data-ttu-id="ad549-194">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="ad549-194">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>
* <span data-ttu-id="ad549-195">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="ad549-195">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>
* <span data-ttu-id="ad549-196">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="ad549-196">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>
* <span data-ttu-id="ad549-197">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class **Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="ad549-197">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class **Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

## <a name="azure-rtos-usbx-apis"></a><span data-ttu-id="ad549-198">Azure RTOS USBX API</span><span class="sxs-lookup"><span data-stu-id="ad549-198">Azure RTOS USBX APIs</span></span>

### <a name="azure-rtos-usbx-host-api"></a><span data-ttu-id="ad549-199">Azure RTOS USBX 호스트 API</span><span class="sxs-lookup"><span data-stu-id="ad549-199">Azure RTOS USBX Host API</span></span>

<span data-ttu-id="ad549-200">Azure RTOS USBX 호스트 API는 명사 동사 명명 규칙에 따르는 직관적이고 일관된 API입니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-200">The Azure RTOS USBX Host API is an intuitive and consistent API, following a noun-verb naming convention.</span></span> <span data-ttu-id="ad549-201">모든 API 앞에는 USBX로 쉽게 식별할 수 있는 ux_host_\*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-201">All APIs have leading ux_host_\* to easily identify as USBX.</span></span> <span data-ttu-id="ad549-202">모든 차단 API에는 선택적 스레드 시간 제한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-202">Any blocking APIs have optional thread timeout.</span></span>

* <span data-ttu-id="ad549-203">.ASIX</span><span class="sxs-lookup"><span data-stu-id="ad549-203">ASIX</span></span>
    - <span data-ttu-id="ad549-204">최소 0.3KB FLASH, 4KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-204">Minimal 0.3 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="ad549-205">자동 크기 조정 | Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-205">Automatic scalingSystem-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-206">*ux_host_class_asix_* \* 형식의 직관적인 Azure RTOS USBX 호스트 API</span><span class="sxs-lookup"><span data-stu-id="ad549-206">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_asix_*\*</span></span>
* <span data-ttu-id="ad549-207">오디오</span><span class="sxs-lookup"><span data-stu-id="ad549-207">AUDIO</span></span>
    - <span data-ttu-id="ad549-208">최소 1.2KB FLASH, 4KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-208">Minimal 1.2 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="ad549-209">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-209">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-210">*ux_host_class_audio_* \* 형식의 직관적인 Azure RTOS USBX 호스트 API</span><span class="sxs-lookup"><span data-stu-id="ad549-210">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_audio_*\*</span></span>
* <span data-ttu-id="ad549-211">CDC/ACM</span><span class="sxs-lookup"><span data-stu-id="ad549-211">CDC/ACM</span></span>
    - <span data-ttu-id="ad549-212">최소 1.4KB FLASH, 4KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-212">Minimal 1.4 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="ad549-213">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-213">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-214">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-214">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-215">*ux_host_class_cdc_acm_* \* 형식의 직관적인 Azure RTOS USBX 호스트 API</span><span class="sxs-lookup"><span data-stu-id="ad549-215">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_cdc_acm_*\*</span></span>
* <span data-ttu-id="ad549-216">HID</span><span class="sxs-lookup"><span data-stu-id="ad549-216">HID</span></span>
    - <span data-ttu-id="ad549-217">최소 0.3KB FLASH, 4KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-217">Minimal 0.3 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="ad549-218">키보드, 마우스 및 원격 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-218">Keyboard, mouse, and remote support</span></span>
    - <span data-ttu-id="ad549-219">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-219">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-220">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-220">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-221">*ux_host_class_hid_* \* 형식의 직관적인 Azure RTOS USBX 호스트 API</span><span class="sxs-lookup"><span data-stu-id="ad549-221">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_hid_*\*</span></span> 
* <span data-ttu-id="ad549-222">HUB</span><span class="sxs-lookup"><span data-stu-id="ad549-222">HUB</span></span>
    - <span data-ttu-id="ad549-223">최소 1.7KB FLASH, 2KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-223">Minimal 1.7 KB FLASH, 2 KB RAM</span></span>
    - <span data-ttu-id="ad549-224">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-224">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-225">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-225">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-226">*ux_host_class_hub_* \* 형식의 직관적인 Azure RTOS USBX 호스트 API</span><span class="sxs-lookup"><span data-stu-id="ad549-226">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_hub_*\*</span></span>
* <span data-ttu-id="ad549-227">PIMA(PTP/MTP)</span><span class="sxs-lookup"><span data-stu-id="ad549-227">PIMA (PTP/MTP)</span></span>
    - <span data-ttu-id="ad549-228">최소 0.9KB FLASH, 8KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-228">Minimal 0.9 KB FLASH, 8 KB RAM</span></span>
    - <span data-ttu-id="ad549-229">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-229">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-230">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-230">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-231">*ux_host_class_pima_* \* 형식의 직관적인 Azure RTOS USBX 호스트 API</span><span class="sxs-lookup"><span data-stu-id="ad549-231">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_pima_*\*</span></span>
* <span data-ttu-id="ad549-232">프린터</span><span class="sxs-lookup"><span data-stu-id="ad549-232">PRINTER</span></span>
    - <span data-ttu-id="ad549-233">최소 0.8KB FLASH, 8KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-233">Minimal 0.8 KB FLASH, 8 KB RAM</span></span>
    - <span data-ttu-id="ad549-234">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-234">Automatic scaling</span></span>
    -  <span data-ttu-id="ad549-235">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-235">System-level trace via Azure RTOS TraceX</span></span>
    -  <span data-ttu-id="ad549-236">*ux_host_class_printer_* \* 형식의 직관적인 Azure RTOS USBX 호스트 API</span><span class="sxs-lookup"><span data-stu-id="ad549-236">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_printer_*\*</span></span>
* <span data-ttu-id="ad549-237">PROLIFIC</span><span class="sxs-lookup"><span data-stu-id="ad549-237">PROLIFIC</span></span>
    - <span data-ttu-id="ad549-238">최소 1.5KB FLASH, 4KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-238">Minimal 1.5 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="ad549-239">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-239">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-240">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-240">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-241">*ux_host_class_prolific_* \* 형식의 직관적인 Azure RTOS USBX 호스트 API</span><span class="sxs-lookup"><span data-stu-id="ad549-241">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_prolific_*\*</span></span>
* <span data-ttu-id="ad549-242">STORAG</span><span class="sxs-lookup"><span data-stu-id="ad549-242">STORAG</span></span>
    - <span data-ttu-id="ad549-243">최소 5.6KB FLASH, 4KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-243">Minimal 5.6 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="ad549-244">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-244">Automatic scaling</span></span><br> <span data-ttu-id="ad549-245">Azure RTOS FileX 통합</span><span class="sxs-lookup"><span data-stu-id="ad549-245">Integrated with Azure RTOS FileX</span></span>
    - <span data-ttu-id="ad549-246">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-246">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-247">*ux_host_class_storage_* \* 형식의 직관적인 Azure RTOS USBX 호스트 API</span><span class="sxs-lookup"><span data-stu-id="ad549-247">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_class_storage_*\*</span></span>
* <span data-ttu-id="ad549-248">USB 호스트 스택</span><span class="sxs-lookup"><span data-stu-id="ad549-248">USB Host STACK</span></span>
    - <span data-ttu-id="ad549-249">다수의 호스트 컨트롤러 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-249">Supports many host controllers</span></span>
    - <span data-ttu-id="ad549-250">최소 18KB FLASH, 25KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-250">Minimal 18 KB FLASH, 25 KB RAM</span></span>
    - <span data-ttu-id="ad549-251">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-251">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-252">동일한 플랫폼에서 여러 호스트 컨트롤러 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-252">Support for multiple host controllers on same platform</span></span>
    -  <span data-ttu-id="ad549-253">USB 낮음, 전체 및 고속 지원</span><span class="sxs-lookup"><span data-stu-id="ad549-253">USB low, full, and high-speed support</span></span>
    -  <span data-ttu-id="ad549-254">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-254">System-level trace via Azure RTOS TraceX</span></span>
    -  <span data-ttu-id="ad549-255">*ux_host_stack_*  \* 형식의 직관적인 Azure RTOS USBX 호스트 API</span><span class="sxs-lookup"><span data-stu-id="ad549-255">Intuitive Azure RTOS USBX host APIs in this form: *ux_host_stack_* \*</span></span> 
* <span data-ttu-id="ad549-256">OHCI, EHCI, 소유 호스트 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="ad549-256">OHCI, EHCI, PROPRIETARY Host CONTROLLERS</span></span> 

### <a name="azure-rtos-usbx-device-api"></a><span data-ttu-id="ad549-257">Azure RTOS USBX 디바이스 API</span><span class="sxs-lookup"><span data-stu-id="ad549-257">Azure RTOS USBX Device API</span></span>

<span data-ttu-id="ad549-258">Azure RTOS USBX 디바이스 API는 명사 동사 명명 규칙에 따르는 직관적이고 일관된 API입니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-258">The Azure RTOS USBX Device API is an intuitive and consistent API following a noun-verb naming convention.</span></span> <span data-ttu-id="ad549-259">모든 API 앞에는 USBX로 쉽게 식별할 수 있는 선행 ux_device_\*가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-259">All APIs have leading ux_device_\* to easily identify as USBX.</span></span> <span data-ttu-id="ad549-260">차단 API에는 선택적 스레드 시간 제한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-260">Blocking APIs have optional thread timeout.</span></span> <span data-ttu-id="ad549-261">자세한 내용은 [Azure RTOS USBX 호스트 사용자 가이드](usbx-host-stack-about.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad549-261">Please see [Azure RTOS USBX Host User Guide](usbx-host-stack-about.md) for more details.</span></span>

* <span data-ttu-id="ad549-262">CDC/ACM</span><span class="sxs-lookup"><span data-stu-id="ad549-262">CDC/ACM</span></span>
    - <span data-ttu-id="ad549-263">최소 0.8KB FLASH, 2KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-263">Minimal 0.8 KB FLASH, 2 KB RAM</span></span>
    - <span data-ttu-id="ad549-264">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-264">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-265">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-265">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-266">*ux_device_class_cdc_acm_*\* 형식의 직관적인 Azure RTOS USBX 디바이스 API</span><span class="sxs-lookup"><span data-stu-id="ad549-266">Intuitive Azure RTOS USBX device APIs in this form: \*ux_device_class_cdc_acm_\*\*.</span></span>
* <span data-ttu-id="ad549-267">CDC/ECM</span><span class="sxs-lookup"><span data-stu-id="ad549-267">CDC/ECM</span></span>
    - <span data-ttu-id="ad549-268">최소 1.5KB FLASH, 4 ~ 8KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-268">Minimal 1.5 KB FLASH, 4 KB to 8 KB RAM</span></span>
    - <span data-ttu-id="ad549-269">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-269">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-270">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-270">System-level trace via Azure RTOS TraceX</span></span><br> <span data-ttu-id="ad549-271">*ux_device_class_cdc_ecm_*\* 형식의 직관적인 Azure RTOS USBX 디바이스 API</span><span class="sxs-lookup"><span data-stu-id="ad549-271">Intuitive Azure RTOS USBX device APIs in this form: \*ux_device_class_cdc_ecm_\*\*.</span></span>
* <span data-ttu-id="ad549-272">DFU</span><span class="sxs-lookup"><span data-stu-id="ad549-272">DFU</span></span>
    - <span data-ttu-id="ad549-273">최소 1.1KB FLASH, 2KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-273">Minimal 1.1 KB FLASH, 2 KB RAM</span></span>
    -  <span data-ttu-id="ad549-274">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-274">Automatic scaling</span></span>
    -  <span data-ttu-id="ad549-275">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-275">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-276">*ux_device_class_dfu_* \* 형식의 직관적인 Azure RTOS USBX 디바이스 API</span><span class="sxs-lookup"><span data-stu-id="ad549-276">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_dfu_*\*</span></span> 
* <span data-ttu-id="ad549-277">GSER</span><span class="sxs-lookup"><span data-stu-id="ad549-277">GSER</span></span>
    - <span data-ttu-id="ad549-278">최소 0.6KB FLASH, 4KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-278">Minimal 0.6 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="ad549-279">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-279">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-280">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-280">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-281">*ux_device_class_gser_* \* 형식의 직관적인 Azure RTOS USBX 디바이스 API</span><span class="sxs-lookup"><span data-stu-id="ad549-281">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_gser_*\*</span></span>
* <span data-ttu-id="ad549-282">HID</span><span class="sxs-lookup"><span data-stu-id="ad549-282">HID</span></span>
    - <span data-ttu-id="ad549-283">최소 0.9KB FLASH, 2KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-283">Minimal 0.9 KB FLASH, 2 KB RAM</span></span>
    - <span data-ttu-id="ad549-284">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-284">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-285">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-285">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-286">*ux_device_class_hid_* \* PIMA(PTP/MTP) 형식의 직관적인 Azure RTOS USBX 디바이스 API</span><span class="sxs-lookup"><span data-stu-id="ad549-286">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_hid_*\* PIMA (PTP/MTP)</span></span>
    - <span data-ttu-id="ad549-287">최소 5.2KB FLASH, 8KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-287">Minimal 5.2 KB FLASH, 8 KB RAM</span></span>
    - <span data-ttu-id="ad549-288">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-288">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-289">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-289">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-290">*ux_device_class_pima_* \* 형식의 직관적인 Azure RTOS USBX 디바이스 API</span><span class="sxs-lookup"><span data-stu-id="ad549-290">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_pima_*\*</span></span> 
* <span data-ttu-id="ad549-291">STORAGE</span><span class="sxs-lookup"><span data-stu-id="ad549-291">STORAGE</span></span>
    - <span data-ttu-id="ad549-292">최소 2.3KB FLASH, 4KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-292">Minimal 2.3 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="ad549-293">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-293">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-294">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-294">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-295">*ux_device_class_storage_* \* 형식의 직관적인 Azure RTOS USBX 디바이스 API</span><span class="sxs-lookup"><span data-stu-id="ad549-295">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_storage_*\*</span></span>
* <span data-ttu-id="ad549-296">RNDIS</span><span class="sxs-lookup"><span data-stu-id="ad549-296">RNDIS</span></span>
    - <span data-ttu-id="ad549-297">최소 2.3KB FLASH, 4 ~ 8KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-297">Minimal 2.3 KB FLASH, 4 KB to 8 KB RAM</span></span>
    - <span data-ttu-id="ad549-298">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-298">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-299">Azure RTOS NetX 및 Azure RTOS NetX DUO와 통합</span><span class="sxs-lookup"><span data-stu-id="ad549-299">Integrated with Azure RTOS NetX and Azure RTOS NetX DUO</span></span>
    - <span data-ttu-id="ad549-300">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-300">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-301">*ux_device_class_rndls_* \* 형식의 직관적인 Azure RTOS USBX 디바이스 API</span><span class="sxs-lookup"><span data-stu-id="ad549-301">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_rndls_*\*</span></span>
* <span data-ttu-id="ad549-302">Azure RTOS USBX 디바이스 스택</span><span class="sxs-lookup"><span data-stu-id="ad549-302">Azure RTOS USBX Device STACK</span></span>
    - <span data-ttu-id="ad549-303">최소 2.3KB FLASH, 4KB RAM</span><span class="sxs-lookup"><span data-stu-id="ad549-303">Minimal 2.3 KB FLASH, 4 KB RAM</span></span>
    - <span data-ttu-id="ad549-304">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="ad549-304">Automatic scaling</span></span>
    - <span data-ttu-id="ad549-305">Azure RTOS TraceX를 통한 시스템 수준 추적</span><span class="sxs-lookup"><span data-stu-id="ad549-305">System-level trace via Azure RTOS TraceX</span></span>
    - <span data-ttu-id="ad549-306">*ux_device_class_storage_* \* 형식의 직관적인 Azure RTOS USBX 디바이스 API</span><span class="sxs-lookup"><span data-stu-id="ad549-306">Intuitive Azure RTOS USBX device APIs in this form: *ux_device_class_storage_*\*</span></span>
* <span data-ttu-id="ad549-307">소유 호스트 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="ad549-307">PROPRIETARY Host CONTROLLERS</span></span>

## <a name="next-steps"></a><span data-ttu-id="ad549-308">다음 단계</span><span class="sxs-lookup"><span data-stu-id="ad549-308">Next steps</span></span>

<span data-ttu-id="ad549-309">[호스트 스택 사용자 가이드](usbx-host-stack-about.md) 또는 [디바이스 스택 사용자 가이드](usbx-device-stack-about.md)에 따라 Azure RTOS USBX 호스트 및 스택 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ad549-309">Start working with the Azure RTOS USBX Host and Device Stack by following our [Host Stack User Guide](usbx-host-stack-about.md) or [Device Stack User Guide](usbx-device-stack-about.md).</span></span>