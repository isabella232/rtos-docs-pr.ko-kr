---
title: 1장 - Azure RTOS USBX 디바이스 스택 소개
description: USBX는 딥 임베디드 애플리케이션을 위한 모든 기능을 갖춘 USB 스택입니다. 이 장에서는 USBX를 소개하고 해당 애플리케이션과 이점을 설명합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6965303f1fbf19212b9f7ff20f811a71fb207f54
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813440"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a><span data-ttu-id="4355e-104">1장 - Azure RTOS USBX 디바이스 스택 소개</span><span class="sxs-lookup"><span data-stu-id="4355e-104">Chapter 1 - Introduction to Azure RTOS USBX Device Stack</span></span>

<span data-ttu-id="4355e-105">USBX는 딥 임베디드 애플리케이션을 위한 모든 기능을 갖춘 USB 스택입니다.</span><span class="sxs-lookup"><span data-stu-id="4355e-105">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="4355e-106">이 장에서는 USBX를 소개하고 해당 애플리케이션과 이점을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4355e-106">This chapter introduces USBX, describing its applications and benefits</span></span> 

## <a name="usbx-features"></a><span data-ttu-id="4355e-107">USBX 기능</span><span class="sxs-lookup"><span data-stu-id="4355e-107">USBX features</span></span>

<span data-ttu-id="4355e-108">USBX는 1.1, 2.0 및 OTG의 세 가지 기존 USB 사양을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4355e-108">USBX supports the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="4355e-109">확장 가능하도록 설계되었으며 하나의 연결된 디바이스만으로 간단한 USB 토폴로지를 수용하고 여러 디바이스와 연계 허브가 포함된 복잡한 토폴로지도 수용합니다.</span><span class="sxs-lookup"><span data-stu-id="4355e-109">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="4355e-110">USBX는 USB 프로토콜의 모든 데이터 전송 유형(제어, 대량, 인터럽트 및 등시)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4355e-110">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="4355e-111">USBX는 호스트 쪽과 디바이스 쪽 모두를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4355e-111">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="4355e-112">각 측면은 세 개의 계층으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4355e-112">Each side is composed of three layers.</span></span>

- <span data-ttu-id="4355e-113">컨트롤러 계층</span><span class="sxs-lookup"><span data-stu-id="4355e-113">Controller layer</span></span>
- <span data-ttu-id="4355e-114">스택 계층</span><span class="sxs-lookup"><span data-stu-id="4355e-114">Stack layer</span></span>
- <span data-ttu-id="4355e-115">클래스 계층</span><span class="sxs-lookup"><span data-stu-id="4355e-115">Class layer</span></span>

<span data-ttu-id="4355e-116">USB 계층 간의 관계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4355e-116">The relationship between the USB layers is as follows:</span></span>

![USB 계층](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="4355e-118">제품 중요 정보</span><span class="sxs-lookup"><span data-stu-id="4355e-118">Product Highlights</span></span>

- <span data-ttu-id="4355e-119">ThreadX 프로세서 지원 완료</span><span class="sxs-lookup"><span data-stu-id="4355e-119">Complete ThreadX processor support</span></span>
- <span data-ttu-id="4355e-120">로열티 없음</span><span class="sxs-lookup"><span data-stu-id="4355e-120">No royalties</span></span>
- <span data-ttu-id="4355e-121">전체 ANSI C 소스 코드</span><span class="sxs-lookup"><span data-stu-id="4355e-121">Complete ANSI C source code</span></span>
- <span data-ttu-id="4355e-122">실시간 성능</span><span class="sxs-lookup"><span data-stu-id="4355e-122">Real-time performance</span></span>
- <span data-ttu-id="4355e-123">반응형 기술 지원</span><span class="sxs-lookup"><span data-stu-id="4355e-123">Responsive technical support</span></span>
- <span data-ttu-id="4355e-124">여러 클래스 지원</span><span class="sxs-lookup"><span data-stu-id="4355e-124">Multiple class support</span></span>
- <span data-ttu-id="4355e-125">여러 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="4355e-125">Multiple class instances</span></span>
- <span data-ttu-id="4355e-126">ThreadX, FileX 및 NetX와 클래스 통합</span><span class="sxs-lookup"><span data-stu-id="4355e-126">Integration of classes with ThreadX, FileX, and NetX</span></span>
- <span data-ttu-id="4355e-127">여러 구성이 있는 USB 디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="4355e-127">Support for USB devices with multiple configurations</span></span>
- <span data-ttu-id="4355e-128">USB 복합 디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="4355e-128">Support for USB composite devices</span></span>
- <span data-ttu-id="4355e-129">USB 전원 관리 지원</span><span class="sxs-lookup"><span data-stu-id="4355e-129">Support for USB power management</span></span>
- <span data-ttu-id="4355e-130">USB OTG 지원</span><span class="sxs-lookup"><span data-stu-id="4355e-130">Support for USB OTG</span></span>
- <span data-ttu-id="4355e-131">TraceX에 대한 추적 이벤트 내보내기</span><span class="sxs-lookup"><span data-stu-id="4355e-131">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="4355e-132">USBX의 강력한 서비스</span><span class="sxs-lookup"><span data-stu-id="4355e-132">Powerful Services of USBX</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="4355e-133">USB 디바이스 프레임워크 지원 완료</span><span class="sxs-lookup"><span data-stu-id="4355e-133">Complete USB Device Framework Support</span></span>

<span data-ttu-id="4355e-134">USBX는 다중 구성, 다중 인터페이스 및 다중 대체 설정을 포함하여 가장 까다로운 USB 디바이스를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4355e-134">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="4355e-135">사용하기 쉬운 API</span><span class="sxs-lookup"><span data-stu-id="4355e-135">Easy-To-Use APIs</span></span>

<span data-ttu-id="4355e-136">USBX는 이해하고 사용하기 쉬운 방식으로 가장 심층적인 임베디드 USB 스택을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4355e-136">USBX provides the best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="4355e-137">USBX API를 사용하면 서비스를 직관적이고 일관되게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4355e-137">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="4355e-138">제공된 USBX 클래스 API를 사용하면 사용자 애플리케이션은 USB 프로토콜의 복잡성을 이해할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4355e-138">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
