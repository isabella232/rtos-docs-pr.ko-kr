---
title: 1장 - Azure RTOS USBX 호스트 스택 소개
description: 이 장에서는 USBX 호스트 스택을 소개하고 애플리케이션과 이점을 설명합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a9fdd86d47bd4680409cc550c87bc6f456d146a9
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377053"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a><span data-ttu-id="eb784-103">1장 - Azure RTOS USBX 호스트 스택 소개</span><span class="sxs-lookup"><span data-stu-id="eb784-103">Chapter 1 - Introduction to Azure RTOS USBX Host Stack</span></span>

<span data-ttu-id="eb784-104">USBX는 심층적인 포함된 애플리케이션을 위한 모든 기능을 갖춘 USB 스택입니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-104">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="eb784-105">이 장에서는 USBX를 소개하고 해당 애플리케이션과 이점을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-105">This chapter introduces USBX, describing its applications and benefits.</span></span>

## <a name="usbx-features"></a><span data-ttu-id="eb784-106">USBX 기능</span><span class="sxs-lookup"><span data-stu-id="eb784-106">USBX features</span></span>

<span data-ttu-id="eb784-107">USBX는 1.1, 2.0 및 OTG의 세 가지 기존 USB 사양을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-107">USBX support the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="eb784-108">확장 가능하도록 설계되었으며 하나의 연결된 디바이스만으로 간단한 USB 토폴로지를 수용하고 여러 디바이스와 연계 허브가 포함된 복잡한 토폴로지도 수용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-108">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="eb784-109">USBX는 USB 프로토콜의 모든 데이터 전송 유형(제어, 대량, 인터럽트 및 등시)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-109">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="eb784-110">USBX는 호스트 쪽과 디바이스 쪽 모두를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-110">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="eb784-111">각 측면은 세 개의 계층으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-111">Each side is comprised of three layers.</span></span>

- <span data-ttu-id="eb784-112">컨트롤러 계층</span><span class="sxs-lookup"><span data-stu-id="eb784-112">Controller layer</span></span>
- <span data-ttu-id="eb784-113">스택 계층</span><span class="sxs-lookup"><span data-stu-id="eb784-113">Stack layer</span></span>
- <span data-ttu-id="eb784-114">클래스 계층</span><span class="sxs-lookup"><span data-stu-id="eb784-114">Class layer</span></span>

<span data-ttu-id="eb784-115">USB 계층 간의 관계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-115">The relationship between the USB layers is as follows.</span></span>

![USB 계층](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="eb784-117">제품 중요 정보</span><span class="sxs-lookup"><span data-stu-id="eb784-117">Product Highlights</span></span>

- <span data-ttu-id="eb784-118">완벽한 ThreadX 프로세서 지원</span><span class="sxs-lookup"><span data-stu-id="eb784-118">Complete ThreadX processor support</span></span>
- <span data-ttu-id="eb784-119">로열티 없음</span><span class="sxs-lookup"><span data-stu-id="eb784-119">No royalties</span></span>
- <span data-ttu-id="eb784-120">전체 ANSI C 소스 코드</span><span class="sxs-lookup"><span data-stu-id="eb784-120">Complete ANSI C source code</span></span>
- <span data-ttu-id="eb784-121">실시간 성능</span><span class="sxs-lookup"><span data-stu-id="eb784-121">Real-time performance</span></span>
- <span data-ttu-id="eb784-122">반응형 기술 지원</span><span class="sxs-lookup"><span data-stu-id="eb784-122">Responsive technical support</span></span>
- <span data-ttu-id="eb784-123">여러 호스트 컨트롤러 지원</span><span class="sxs-lookup"><span data-stu-id="eb784-123">Multiple host controller support</span></span>
- <span data-ttu-id="eb784-124">여러 클래스 지원</span><span class="sxs-lookup"><span data-stu-id="eb784-124">Multiple class support</span></span>
- <span data-ttu-id="eb784-125">여러 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="eb784-125">Multiple class instances</span></span>
- <span data-ttu-id="eb784-126">ThreadX, FileX 및 NetX와 클래스 통합</span><span class="sxs-lookup"><span data-stu-id="eb784-126">Integration of classes with ThreadX, FileX and NetX</span></span>
- <span data-ttu-id="eb784-127">여러 구성이 있는 USB 디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="eb784-127">Support for USB devices with multiple configuration</span></span>
- <span data-ttu-id="eb784-128">USB 복합 디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="eb784-128">Support for USB composite devices</span></span>
- <span data-ttu-id="eb784-129">연계 허브에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="eb784-129">Support for cascading hubs</span></span>
- <span data-ttu-id="eb784-130">USB 전원 관리 지원</span><span class="sxs-lookup"><span data-stu-id="eb784-130">Support for USB power management</span></span>
- <span data-ttu-id="eb784-131">USB OTG 지원</span><span class="sxs-lookup"><span data-stu-id="eb784-131">Support for USB OTG</span></span>
- <span data-ttu-id="eb784-132">TraceX에 대한 추적 이벤트 내보내기</span><span class="sxs-lookup"><span data-stu-id="eb784-132">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="eb784-133">USBX의 강력한 서비스</span><span class="sxs-lookup"><span data-stu-id="eb784-133">Powerful Services of USBX</span></span>

### <a name="multiple-host-controller-support"></a><span data-ttu-id="eb784-134">여러 호스트 컨트롤러 지원</span><span class="sxs-lookup"><span data-stu-id="eb784-134">Multiple Host Controller Support</span></span>

<span data-ttu-id="eb784-135">USBX는 동시에 실행되는 여러 USB 호스트 컨트롤러를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-135">USBX can support multiple USB host controllers running concurrently.</span></span> <span data-ttu-id="eb784-136">이 기능을 사용하면 현재 시장에서 대부분의 USB 2.0 호스트 컨트롤러와 연결된 이전 버전과의 호환성 체계를 사용하여 USBX에서 USB 2.0 표준을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-136">This feature allows USBX to support the USB 2.0 standard using the backward compatibility scheme associated with most USB 2.0 host controllers on the market today.</span></span>

### <a name="usb-software-scheduler"></a><span data-ttu-id="eb784-137">USB 소프트웨어 스케줄러</span><span class="sxs-lookup"><span data-stu-id="eb784-137">USB Software Scheduler</span></span>

<span data-ttu-id="eb784-138">USBX에는 하드웨어 목록 처리가 없는 USB 컨트롤러를 지원하는 데 필요한 USB 소프트웨어 스케줄러가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-138">USBX contains a USB software scheduler necessary to support USB controllers that do not have hardware list processing.</span></span> <span data-ttu-id="eb784-139">USBX 소프트웨어 스케줄러는 정확한 빈도의 서비스와 우선 순위를 사용하여 USB 전송을 구성하고 각 전송을 실행하도록 USB 컨트롤러에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-139">The USBX software scheduler will organize USB transfers with the correct frequency of service and priority, and will instruct the USB controller to execute each transfer.</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="eb784-140">USB 디바이스 프레임워크 지원 완료</span><span class="sxs-lookup"><span data-stu-id="eb784-140">Complete USB Device Framework Support</span></span>

<span data-ttu-id="eb784-141">USBX는 다중 구성, 다중 인터페이스 및 다중 대체 설정을 포함하여 가장 까다로운 USB 디바이스를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-141">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="eb784-142">사용하기 쉬운 API</span><span class="sxs-lookup"><span data-stu-id="eb784-142">Easy-To-Use APIs</span></span>

<span data-ttu-id="eb784-143">USBX는 이해하고 사용하기 쉬운 방식으로 가장 심층적인 포함된 USB 스택을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-143">USBX provides the very best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="eb784-144">USBX API를 사용하면 서비스를 직관적이고 일관되게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-144">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="eb784-145">제공된 USBX 클래스 API를 사용하면 사용자 애플리케이션은 USB 프로토콜의 복잡성을 이해할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb784-145">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
