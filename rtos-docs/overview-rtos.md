---
title: Microsoft Azure RTOS란?
description: Azure RTOS는 MCU(마이크로 컨트롤러 단위)로 구동되는 IoT 및 에지 디바이스의 RTOS(실시간 운영 체제)입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: c902289b487c439da4ef5138319fe09d74a2347f
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171278"
---
# <a name="what-is-microsoft-azure-rtos"></a><span data-ttu-id="243b2-103">Microsoft Azure RTOS란?</span><span class="sxs-lookup"><span data-stu-id="243b2-103">What is Microsoft Azure RTOS?</span></span>

<span data-ttu-id="243b2-104">Azure RTOS는 MCU(마이크로 컨트롤러 단위)로 구동되는 IoT(사물 인터넷) 및 에지 디바이스의 RTOS(실시간 운영 체제)입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-104">Azure RTOS is a real time operating system (RTOS) for Internet of Things (IoT) and edge devices powered by microcontroller units (MCUs).</span></span> <span data-ttu-id="243b2-105">Azure RTOS는 대부분의 매우 제한된 디바이스(배터리 전원을 공급하고 64KB 미만의 플래시 메모리)를 지원하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-105">Azure RTOS is designed to support most highly constrained devices (battery powered and having less than 64 KB of flash memory).</span></span>

<span data-ttu-id="243b2-106">Azure RTOS는 다양한 안전 표준에 대해 사전 인증을 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-106">Azure RTOS is pre-certified for a variety of safety standards.</span></span> <span data-ttu-id="243b2-107">여기에는 IEC 61508 SIL 4, IEC 62304 클래스 C 및 ISO 26262 ASIL D 인증이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-107">These include the IEC 61508 SIL 4, IEC 62304 Class C, and ISO 26262 ASIL D certifications.</span></span> <span data-ttu-id="243b2-108">또한 Azure RTOS ThreadX는 DO-178 인증을 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-108">Azure RTOS ThreadX is also DO-178 certified.</span></span>

<span data-ttu-id="243b2-109">Azure RTOS는 TLS 및 DTLS를 통해 IPsec 및 소켓 계층 보안을 통해 전체 IP 계층 보안을 비롯하여 EAL4+ Common Criteria 보안 인증 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-109">Azure RTOS provides an EAL4+ Common Criteria security certified environment, including full IP layer security via IPsec and socket layer security via TLS and DTLS.</span></span> <span data-ttu-id="243b2-110">소프트웨어 암호화 라이브러리는 FIPS 140-2 인증을 달성했습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-110">Our software crypto library has achieved FIPS 140-2 certification.</span></span> <span data-ttu-id="243b2-111">또한 하드웨어 암호화 기능, ThreadX 모듈을 통한 메모리 보호 및 ARM의 TrustZone ARMv8-M 보안 기능에 대한 지원을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-111">We also leverage hardware cryptographic capabilities, memory protection via ThreadX MODULES, and support for ARM's TrustZone ARMv8-M security features.</span></span>

## <a name="components-of-azure-rtos"></a><span data-ttu-id="243b2-112">Azure RTOS의 구성 요소</span><span class="sxs-lookup"><span data-stu-id="243b2-112">Components of Azure RTOS</span></span>

<span data-ttu-id="243b2-113">Azure RTOS 플랫폼은 Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo 및 Azure RTOS USBX를 비롯한 런타임 솔루션의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-113">The Azure RTOS platform is the collection of run-time solutions including Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo, and Azure RTOS USBX.</span></span>

### <a name="azure-rtos-threadx"></a><span data-ttu-id="243b2-114">Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="243b2-114">Azure RTOS ThreadX</span></span>

<span data-ttu-id="243b2-115">Azure RTOS ThreadX는 깊게 포함된 애플리케이션용으로 특별히 설계된 고급 RTOS(실시간 운영 체제)입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-115">Azure RTOS ThreadX is an advanced Real-Time Operating System (RTOS) designed specifically for deeply embedded applications.</span></span> <span data-ttu-id="243b2-116">Azure RTOS ThreadX에서 제공하는 여러 이점 중 하나는 고급 예약 기능, 메시지 전달, 인터럽트 관리 및 메시징 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-116">Among the multiple benefits Azure RTOS ThreadX provides are advanced scheduling facilities, message passing, interrupt management, and messaging services.</span></span> <span data-ttu-id="243b2-117">Azure RTOS ThreadX에는 picokernel 아키텍처, preemption-threshold 스케줄링, event-chaining 및 다양한 시스템 서비스 집합을 포함한 많은 고급 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-117">Azure RTOS ThreadX has many advanced features, including its picokernel architecture, preemption-threshold scheduling, event-chaining, and a rich set of system services.</span></span>

### <a name="azure-rtos-filex"></a><span data-ttu-id="243b2-118">Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="243b2-118">Azure RTOS FileX</span></span>

<span data-ttu-id="243b2-119">Azure RTOS FileX는 고성능 FAT 호환 파일 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-119">Azure RTOS FileX is a high-performance FAT-compatible file system.</span></span> <span data-ttu-id="243b2-120">Azure RTOS ThreadX와 완전히 통합되고 지원되는 모든 프로세서에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-120">It is fully integrated with Azure RTOS ThreadX and is available for all supported processors.</span></span> <span data-ttu-id="243b2-121">Azure RTOS FileX는 Azure RTOS ThreadX와 마찬가지로 공간을 적게 차지하면서 고성능을 제공하도록 설계되었으므로 파일 작업이 필요한 오늘날의 긴밀하게 포함된 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-121">Like Azure RTOS ThreadX, Azure RTOS FileX is designed to have a small footprint and high performance, making it ideal for today's deeply embedded applications that require file operations.</span></span> <span data-ttu-id="243b2-122">Azure RTOS FileX는 Azure RTOS LevelX를 통해 RAM 디스크, USBX, SD 카드 및 NAND/NOR 플래시 메모리를 비롯한 대부분의 물리적 미디어를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-122">Azure RTOS FileX supports most physical media, including RAM disk, USBX, SD CARD, and NAND/NOR flash memories via Azure RTOS LevelX.</span></span>

### <a name="azure-rtos-guix"></a><span data-ttu-id="243b2-123">Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="243b2-123">Azure RTOS GUIX</span></span>

<span data-ttu-id="243b2-124">Azure RTOS GUIX는 포함된 시스템 개발자의 요구 사항에 맞게 제작된 전문적인 품질의 그래픽 사용자 인터페이스 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-124">Azure RTOS GUIX is a professional quality graphical user interface package, created to meet the needs of embedded systems developers.</span></span> <span data-ttu-id="243b2-125">다른 대안과 달리 Azure RTOS GUIX는 그래픽 출력을 지원할 수 있는 거의 모든 하드웨어 구성으로 작고 빠르고 쉽게 이식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-125">Unlike the alternatives, Azure RTOS GUIX is small, fast, and easily ported to virtually any hardware configuration capable of supporting graphical output.</span></span> <span data-ttu-id="243b2-126">또한 Azure RTOS GUIX는 애플리케이션 수준 사용자 인터페이스 개발을 위한 뛰어난 시각적 효과와 직관적이고 강력한 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-126">Azure RTOS GUIX also delivers exceptional visual appeal and an intuitive and powerful API for application-level user interface development.</span></span>

### <a name="azure-rtos-netx"></a><span data-ttu-id="243b2-127">Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="243b2-127">Azure RTOS NetX</span></span>

<span data-ttu-id="243b2-128">Azure RTOS NetX는 TCP/IP 프로토콜 표준의 고성능 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-128">Azure RTOS NetX is a high-performance implementation of TCP/IP protocol standards.</span></span> <span data-ttu-id="243b2-129">Azure RTOS ThreadX와 완전히 통합되고 지원되는 모든 프로세서에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-129">It is fully integrated with Azure RTOS ThreadX, and is available for all supported processors.</span></span> <span data-ttu-id="243b2-130">Azure RTOS NetX에는 고유한 Piconet 아키텍처가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-130">Azure RTOS NetX has a unique Piconet architecture.</span></span> <span data-ttu-id="243b2-131">제로 복사 API와 함께 사용하면 네트워크에 연결해야 하는 오늘날의 긴밀하게 포함된 애플리케이션에 완벽하게 부합합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-131">Combined with a zero-copy API, it makes it a perfect fit for today's deeply embedded applications that require network connectivity.</span></span>

### <a name="azure-rtos-netx-duo"></a><span data-ttu-id="243b2-132">Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="243b2-132">Azure RTOS NetX Duo</span></span>

<span data-ttu-id="243b2-133">Azure RTOS NetX Duo는 긴밀하게 포함된 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 고급, 산업용 TCP/IP 네트워크 스택입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-133">Azure RTOS NetX Duo is an advanced, Industrial Grade TCP/IP network stacks designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="243b2-134">Azure RTOS NetX Duo는 이중 IPv4 및 IPv6 네트워크 스택이고, NetX는 원래 IPv4 네트워크 스택이며, 기본적으로 Azure RTOS NetX Duo의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-134">Azure RTOS NetX Duo is a dual IPv4 and IPv6 network stack, while NetX is the original IPv4 network stack, essentially a subset of Azure RTOS NetX Duo.</span></span>

### <a name="azure-rtos-usbx"></a><span data-ttu-id="243b2-135">Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="243b2-135">Azure RTOS USBX</span></span>

<span data-ttu-id="243b2-136">Azure RTOS USBX는 고성능의 USB 호스트, 디바이스 및 OTG(On-The-Go) 포함 스택입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-136">Azure RTOS USBX is a high-performance USB host, device, and On-The-Go (OTG) embedded stack.</span></span> <span data-ttu-id="243b2-137">ThreadX와 완전히 통합되고 지원되는 모든 Azure RTOS ThreadX 프로세서에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-137">It is fully integrated with ThreadX and is available for all Azure RTOS ThreadX supported processors.</span></span> <span data-ttu-id="243b2-138">Azure RTOS USBX는 Azure RTOS ThreadX와 마찬가지로 공간을 적게 차지하면서 고성능을 제공하도록 설계되었으므로 USB 디바이스와 인터페이스가 필요한 긴밀하게 포함된 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-138">Like Azure RTOS ThreadX, Azure RTOS USBX is designed to have a small footprint and high performance, making it ideal for deeply embedded applications that require an interface with USB devices.</span></span>

### <a name="windows-tools"></a><span data-ttu-id="243b2-139">Windows 도구</span><span class="sxs-lookup"><span data-stu-id="243b2-139">Windows tools</span></span>

<span data-ttu-id="243b2-140">Azure RTOS GUIX Studio는 전체 GUI 애플리케이션 디자인 환경을 제공하여 애플리케이션의 GUI에서 모든 그래픽 요소를 만들고 유지 관리하는 작업을 용이하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-140">Azure RTOS GUIX Studio provides a complete GUI application design environment, facilitating the creation and maintenance of all graphical elements in the application's GUI.</span></span> <span data-ttu-id="243b2-141">Azure RTOS GUIX Studio는 대상에서 컴파일되고 실행할 준비가 된 Azure RTOS GUIX 라이브러리와 호환되는 C 코드를 자동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-141">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span>

<span data-ttu-id="243b2-142">Azure RTOS TraceX는 포함된 시스템 개발자에게 실시간 시스템 이벤트에 대한 그래픽 보기를 제공하고, 실시간 시스템의 동작을 시각화하고 더 잘 이해할 수 있도록 하는 호스트 기반 분석 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-142">Azure RTOS TraceX is a host-based analysis tool that provides developers with a graphical view of real-time system events and enables them to visualize and better understand the behavior of their real-time systems.</span></span>

## <a name="the-azure-rtos-advantage"></a><span data-ttu-id="243b2-143">Azure RTOS의 이점</span><span class="sxs-lookup"><span data-stu-id="243b2-143">The Azure RTOS Advantage</span></span>
<span data-ttu-id="243b2-144">Azure RTOS는 다른 실시간 운영 체제에 비해 다음과 같은 이점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-144">Azure RTOS provides the following advantages over other real-time operating systems.</span></span>

### <a name="intuitive-and-consistent-api-design"></a><span data-ttu-id="243b2-145">직관적이고 일관된 API 디자인</span><span class="sxs-lookup"><span data-stu-id="243b2-145">Intuitive and consistent API design</span></span>

* <span data-ttu-id="243b2-146">직관적이고 일관된 API.</span><span class="sxs-lookup"><span data-stu-id="243b2-146">Intuitive and consistent API.</span></span>
* <span data-ttu-id="243b2-147">명사-동사 명명 규칙.</span><span class="sxs-lookup"><span data-stu-id="243b2-147">Noun-verb naming convention.</span></span>
* <span data-ttu-id="243b2-148">모든 API에는 ThreadX의 경우 *tx_* , FileX의 경우 *nx_* 와 같은 선행 접두사가 있어, 해당 접두사가 속한 Azure RTOS 구성 요소를 쉽게 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-148">All APIs have leading prefix, such as *tx_* for ThreadX and *nx_* for FileX, to easily identify the Azure RTOS component they belong to.</span></span>
* <span data-ttu-id="243b2-149">차단 API에 선택적 스레드 시간 제한 적용</span><span class="sxs-lookup"><span data-stu-id="243b2-149">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="243b2-150">많은 API를 애플리케이션 ISR에서 직접 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-150">Many APIs are directly available from application ISRs.</span></span>
- <span data-ttu-id="243b2-151">미디어 및 파일 작업에 대한 선택적 사용자 알림 콜백.</span><span class="sxs-lookup"><span data-stu-id="243b2-151">Optional user-notification callbacks for media and file operations.</span></span>
* <span data-ttu-id="243b2-152">이벤트 구동 프로그래밍 모델(API).</span><span class="sxs-lookup"><span data-stu-id="243b2-152">Event-driven programming model (API).</span></span>

### <a name="high-efficiency"></a><span data-ttu-id="243b2-153">높은 효율성</span><span class="sxs-lookup"><span data-stu-id="243b2-153">High efficiency</span></span>

- <span data-ttu-id="243b2-154">작은 코드 공간.</span><span class="sxs-lookup"><span data-stu-id="243b2-154">Small code footprint.</span></span>
- <span data-ttu-id="243b2-155">사용된 서비스를 기반으로 하는 확장 가능한 코드 공간.</span><span class="sxs-lookup"><span data-stu-id="243b2-155">Scalable code footprint based on the services used.</span></span>
- <span data-ttu-id="243b2-156">IEC 61508 SIL 4, IEC 62304 클래스 C, ISO 26262 ASIL D 및 EN 50128 SW-SIL4에 따라 TUV 및 UL에 의해 사전 인증됨.</span><span class="sxs-lookup"><span data-stu-id="243b2-156">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4.</span></span>
- <span data-ttu-id="243b2-157">고속 실행.</span><span class="sxs-lookup"><span data-stu-id="243b2-157">Fast execution.</span></span>

### <a name="fastest-time-to-market"></a><span data-ttu-id="243b2-158">가장 빠른 출시 시간</span><span class="sxs-lookup"><span data-stu-id="243b2-158">Fastest time-to-market</span></span>

<span data-ttu-id="243b2-159">Azure RTOS는 설치, 학습, 사용, 디버그, 확인, 인증 및 유지 관리가 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-159">Azure RTOS is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="243b2-160">결과적으로 Azure RTOS는 Broadcom, Gainspan 등의 많은 SoC를 포함하여 임베디드 IoT 디바이스에 가장 많이 사용되는 실시간 운영 체제 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-160">As a result, Azure RTOS is one of the most popular real time operating systems for embedded IoT devices, including many SoCs from Broadcom, Gainspan, and so forth.</span></span> <span data-ttu-id="243b2-161">일관적인 출시 시간 이점은 다음을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-161">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="243b2-162">전체 소스 코드 가용성.</span><span class="sxs-lookup"><span data-stu-id="243b2-162">Complete source code availability.</span></span>
* <span data-ttu-id="243b2-163">사용하기 쉬운 API.</span><span class="sxs-lookup"><span data-stu-id="243b2-163">Easy-to-use API.</span></span>
* <span data-ttu-id="243b2-164">포괄적인 고급 기능 세트.</span><span class="sxs-lookup"><span data-stu-id="243b2-164">Comprehensive and advanced feature set.</span></span>

### <a name="one-simple-license"></a><span data-ttu-id="243b2-165">하나의 간단한 라이선스</span><span class="sxs-lookup"><span data-stu-id="243b2-165">One Simple License</span></span>

<span data-ttu-id="243b2-166">사전에 사용이 허가된 디바이스에 배포하는 경우에는 소스 코드를 사용 및 테스트하는 데 비용이 들지 않으며 프로덕션 라이선스에 대한 비용도 부과되지 않습니다. 다른 모든 디바이스에는 간단한 연간 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-166">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

### <a name="full-highest-quality-source-code"></a><span data-ttu-id="243b2-167">최고 품질의 전체 소스 코드</span><span class="sxs-lookup"><span data-stu-id="243b2-167">Full, highest-quality source code</span></span>

<span data-ttu-id="243b2-168">오랜 시간에 걸쳐 Azure RTOS 소스 코드는 품질 및 이해 용이성의 기준을 정립했습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-168">Throughout the years, Azure RTOS source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="243b2-169">또한 파일당 하나의 함수를 포함하는 규칙을 통해 손쉬운 소스 탐색을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-169">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

### <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="243b2-170">TUV 및 UL을 비롯한 여러 안전 표준의 사전 인증</span><span class="sxs-lookup"><span data-stu-id="243b2-170">Pre-certified by TUV and UL to many safety standards</span></span>

<span data-ttu-id="243b2-171">Azure RTOS는 안전이 매우 중요한 시스템에서의 사용을 위해 IEC-61508 SIL 4, IEC-62304 SW 안전 클래스 C, ISO 26262 ASIL D 및 EN 50128에 따라 SGS-TUV Saar 인증을 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-171">Azure RTOS has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="243b2-172">이 인증은 "전기, 전자 및 프로그램 가능한 전자 안전 관련 시스템의 기능적 안전"에 대한 최고 수준의 IEC-61508, IEC-62304, ISO 26262 및 EN 50128의 안전 무결성 등급에 따라, Azure RTOS를 보안 관련 소프트웨어의 개발에 사용할 수 있음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-172">The certification confirms that Azure RTOS can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="243b2-173">독일 SGS-Group 및 TUV Saarland의 공동 벤처인 SGS-TUV Saar는 세계적으로 안전 관련 시스템용 포함 소프트웨어를 테스트, 감사, 확인 및 검증하는 최고 권위의 독립 기업으로 자리했습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-173">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="243b2-174">산업 보안 표준 IEC 61508과, 거기에서 파생된 모든 표준(IEC-62304, ISO 26262 및 EN 50128 포함)은 전기, 전자 및 프로그래밍 가능한 전자 안전 관련 의료 장비, 공정 제어 시스템, 산업용 기계, 자동차, 철도 제어 시스템의 기능 안전을 보장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-174">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

:::image type="content" source="media/partener-logo-sgs-tuv-saar.png" alt-text="인증":::

<span data-ttu-id="243b2-176">UL은 Azure RTOS가 프로그래밍 가능한 구성 요소에서의 소프트웨어에 대한 UL 60730-1 부칙 H, CSA E60730-1 부칙 H, IEC 60730-1 부칙 H, UL 60335-1 부칙 R, IEC 60335-1 부칙 R 및 UL 1998 안전 표준의 규정을 준수한다고 인정했습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-176">Azure RTOS has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="243b2-177">UL은 공공 에너지 도입, 첨단 지속 가능성 기술, 재생 에너지, 나노 기술 등을 망라하는 안전 솔루션 혁신 분야에서 백년이 넘는 전문 기술을 갖춘 글로벌 독립 안전 과학 기업입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-177">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

:::image type="content" source="media/cru-logo-certification.png" alt-text="CRU UL 인증":::

<span data-ttu-id="243b2-179">TUV 및 UL 인증과 관련한 아티팩트(인증서, 안전 매뉴얼, 테스트 보고서 등)는 판매 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-179">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="243b2-180">애플리케이션에 추가 인증이 필요한 경우, 실제 하드웨어 플랫폼을 사용한 다양한 표준에 대한 턴키 방식의 인증을 제공하고 애플리케이션 코드까지도 다루는 인증 서비스를 Microsoft를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-180">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span> <span data-ttu-id="243b2-181">인증 서비스에 대한 자세한 내용은 Microsoft에 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="243b2-181">Contact us for more details on our certification service.</span></span>

### <a name="eal4-common-criteria-security-certification"></a><span data-ttu-id="243b2-182">EAL4+ Common Criteria 보안 인증</span><span class="sxs-lookup"><span data-stu-id="243b2-182">EAL4+ Common Criteria security certification</span></span>

<span data-ttu-id="243b2-183">Azure RTOS는 EAL4+ Common Criteria 보안 인증을 달성했습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-183">Azure RTOS has achieved EAL4+ Common Criteria security certification.</span></span> <span data-ttu-id="243b2-184">TOE(평가 대상)는 Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS 및 Azure RTOS NetX MQTT를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-184">The Target of Evaluation (TOE) covers Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS, and Azure RTOS NetX MQTT.</span></span> <span data-ttu-id="243b2-185">이는 깊이 내장된 센서, 디바이스, 에지 라우터 및 게이트웨이에 필요한 가장 일반적인 IoT 프로토콜을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-185">This represents the most typical IoT protocols required by deeply embedded sensors, devices, edge routers, and gateways.</span></span>

:::image type="content" source="media/eal-logo-certification.png" alt-text="EAL 인증":::

<span data-ttu-id="243b2-187">Microsoft Azure RTOS SC 보안 인증에 사용되는 IT 보안 평가 시설은 Brightsight BV이고 인증 기관은 SERTIT입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-187">The IT Security Evaluation Facility used for the Microsoft Azure RTOS SC security certification is Brightsight BV and the Certification Authority is SERTIT.</span></span>

### <a name="fips-140-2-validated"></a><span data-ttu-id="243b2-188">FIPS 140-2 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="243b2-188">FIPS 140-2 Validated</span></span>

<span data-ttu-id="243b2-189">Azure RTOS 암호화 라이브러리는 암호화 모듈에 대한 요구 사항을 지정하는 소프트웨어용 FIPS 140-2(Federal Information Processing Standard 140-2) 인증을 획득했습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-189">Azure RTOS Crypto libraries have achieved Federal Information Processing Standardization 140-2 (FIPS 140-2) Certification for software, which specifies requirements for cryptography modules.</span></span> <span data-ttu-id="243b2-190">FIPS 140-2에 따르면 암호화 기반 보안을 사용하는 모든 연방 정부 기관 및 부서는 암호화 강도 및 기능과 관련된 특정 표준을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-190">FIPS 140-2 requires all federal government agencies and departments that use cryptographic-based security to meet specific standards related to encryption strength and capabilities.</span></span> <span data-ttu-id="243b2-191">이러한 암호화 기반 보안 표준은 캐나다 및 유럽 연합에서도 인정되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-191">These cryptographic-based security standards are also recognized in Canada and the European Union.</span></span>

<span data-ttu-id="243b2-192">Azure RTOS 암호화 라이브러리에 사용되는 정보 보안 평가 랩은 atsec이었으며 인증 기관은 [NIST(National Institute of Standards and Technology)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394)입니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-192">The Information Security evaluation lab used for Azure RTOS Crypto libraries was atsec and the certification authority is [The National Institute of Standards and Technology (NIST)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394).</span></span>

### <a name="supports-most-popular-architectures"></a><span data-ttu-id="243b2-193">대부분의 주요 아키텍처 지원</span><span class="sxs-lookup"><span data-stu-id="243b2-193">Supports most popular architectures</span></span>

<span data-ttu-id="243b2-194">가장 널리 사용되는 32/64비트 마이크로프로세서의 Azure RTOS는 즉시 사용 가능하며 다음과 같은 고급 아키텍처를 포함하여 즉시 완전히 테스트되고 완벽하게 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-194">Azure RTOS on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="243b2-195">**아날로그 디바이스**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="243b2-195">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="243b2-196">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="243b2-196">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="243b2-197">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="243b2-197">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="243b2-198">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64비트/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="243b2-198">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="243b2-199">**Cadence**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="243b2-199">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="243b2-200">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="243b2-200">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="243b2-201">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="243b2-201">**Cypress**: RISC-V</span></span>

<span data-ttu-id="243b2-202">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="243b2-202">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="243b2-203">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="243b2-203">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="243b2-204">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="243b2-204">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="243b2-205">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="243b2-205">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="243b2-206">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="243b2-206">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="243b2-207">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="243b2-207">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="243b2-208">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span><span class="sxs-lookup"><span data-stu-id="243b2-208">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="243b2-209">**Silicon Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="243b2-209">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="243b2-210">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="243b2-210">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="243b2-211">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="243b2-211">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="243b2-212">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="243b2-212">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="243b2-213">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="243b2-213">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="243b2-214">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="243b2-214">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="243b2-215">*나열된 모든 타이밍 및 크기 수치는 예상치이며, 개발 플랫폼에 따라 다를 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="243b2-215">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>

## <a name="in-the-context-of-azure-iot"></a><span data-ttu-id="243b2-216">Azure IoT의 컨텍스트에서</span><span class="sxs-lookup"><span data-stu-id="243b2-216">In the context of Azure IoT</span></span>

<span data-ttu-id="243b2-217">Azure IoT에 직접 연결하거나 Azure IoT Edge를 통해 간접적으로 연결하는 것 외에도 Azure RTOS를 Azure Sphere 디바이스에서 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-217">In addition to directly connecting to Azure IoT or indirectly connecting through Azure IoT Edge, Azure RTOS is also available on Azure Sphere devices.</span></span> <span data-ttu-id="243b2-218">Azure RTOS와 Azure Sphere의 조합은 하나의 디바이스에서 최상의 실시간 처리 및 보안을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="243b2-218">The combination of Azure RTOS and Azure Sphere bring best-of-class real-time processing and security together in one device.</span></span>
