---
title: 1장 - GUIX 소개
description: GUIX는 포함된 Azure RTOS ThreadX 기반 애플리케이션 전용으로 설계된 (GUI)의 고성능 실시간 구현입니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b90da988a03d59b1bca3f5584164d641bef96454
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812019"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a><span data-ttu-id="fdd02-103">1장 - Azure RTOS GUIX 소개</span><span class="sxs-lookup"><span data-stu-id="fdd02-103">Chapter 1 - Introduction to Azure RTOS GUIX</span></span>

<span data-ttu-id="fdd02-104">GUIX(Azure RTOS GUIX)는 포함된 ThreadX 기반 애플리케이션 전용으로 설계된 그래픽 인터페이스 프레임워크의 고성능 실시간 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-104">Azure RTOS GUIX (GUIX) is a high-performance real-time implementation of a graphical interface framework designed exclusively for embedded ThreadX-based applications.</span></span> <span data-ttu-id="fdd02-105">이 장에서는 GUIX를 소개하고 해당 애플리케이션과 그 이점에 관해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-105">This chapter contains an introduction to GUIX and a description of its applications and benefits.</span></span>

## <a name="guix-feature-overview"></a><span data-ttu-id="fdd02-106">GUIX의 기능 개요</span><span class="sxs-lookup"><span data-stu-id="fdd02-106">GUIX Feature Overview</span></span>

<span data-ttu-id="fdd02-107">다른 많은 GUI 구현과 달리 GUIX는 다용도로 설계되어 소규모 마이크로 컨트롤러 기반 애플리케이션에서 강력한 RISC와 DSP 프로세서를 사용하는 애플리케이션으로 쉽게 스케일링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-107">Unlike many other GUI implementations, GUIX is designed to be versatile—easily scaling from small micro-controller-based applications to those that use powerful RISC and DSP processors.</span></span> <span data-ttu-id="fdd02-108">이는 원래 워크스테이션 환경에 맞춰 고안된 후 포함된 설계에 갇혀 버린 퍼블릭 도메인 또는 기타 상용 구현과는 확실히 대비됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-108">This is in sharp contrast to public domain or other commercial implementations originally intended for workstation environments but then squeezed into embedded designs.</span></span> <span data-ttu-id="fdd02-109">GUIX의 기능을 간략하게 정리하면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-109">An overview of GUIX features follows:</span></span>

- <span data-ttu-id="fdd02-110">호스트 기반 디자인 도구인 GUIX Studio에서 사용하기 쉬움</span><span class="sxs-lookup"><span data-stu-id="fdd02-110">Easy to use with host-based design tool GUIX Studio</span></span>

- <span data-ttu-id="fdd02-111">호스트된 전체 프로토타입을 위한 Win32 GUIX 런타임 환경</span><span class="sxs-lookup"><span data-stu-id="fdd02-111">Win32 GUIX run-time environment for complete hosted prototyping</span></span>

- <span data-ttu-id="fdd02-112">ThreadX에서 지원하는 대부분의 프로세서 지원</span><span class="sxs-lookup"><span data-stu-id="fdd02-112">Supports most processors supported by ThreadX</span></span>

- <span data-ttu-id="fdd02-113">ANSI C로만 작성됨</span><span class="sxs-lookup"><span data-stu-id="fdd02-113">Written exclusively in ANSI C</span></span>

- <span data-ttu-id="fdd02-114">Endian 중립</span><span class="sxs-lookup"><span data-stu-id="fdd02-114">Endian neutral</span></span>

- <span data-ttu-id="fdd02-115">가장 작고 빠른 포함된 GUI</span><span class="sxs-lookup"><span data-stu-id="fdd02-115">Smallest, Fasted Embedded GUI</span></span>

- <span data-ttu-id="fdd02-116">런타임 구성 가능, 개체 수, 화면 크기 등</span><span class="sxs-lookup"><span data-stu-id="fdd02-116">Run-time configurable, number of objects, screen size, etc.</span></span>

- <span data-ttu-id="fdd02-117">작성하기 쉬운 디스플레이 드라이버 인터페이스</span><span class="sxs-lookup"><span data-stu-id="fdd02-117">Easy to write display driver interface</span></span>

- <span data-ttu-id="fdd02-118">컬러(최대 32bpp의 색 농도), 단색, 회색조 지원</span><span class="sxs-lookup"><span data-stu-id="fdd02-118">Color (up to 32-bpp color depth), monochrome, and grayscale support</span></span>

- <span data-ttu-id="fdd02-119">UTF8 문자열 인코딩과 문자열 리소스를 통한 다국어 지원</span><span class="sxs-lookup"><span data-stu-id="fdd02-119">Multilingual support via UTF8 string encoding and string resources</span></span>

- <span data-ttu-id="fdd02-120">기본 무료 글꼴과 간단한 새 글꼴 추가</span><span class="sxs-lookup"><span data-stu-id="fdd02-120">Default free fonts and easy to add new fonts</span></span>

- <span data-ttu-id="fdd02-121">다양한 크기의 여러 그리기 캔버스 지원</span><span class="sxs-lookup"><span data-stu-id="fdd02-121">Multiple drawing Canvases supported, of various sizes</span></span>

- <span data-ttu-id="fdd02-122">다양한 크기와 색 농도가 지원되는 여러 디스플레이</span><span class="sxs-lookup"><span data-stu-id="fdd02-122">Multiple displays of different sizes and color depths supported</span></span>

- <span data-ttu-id="fdd02-123">화면 전환 지원(페이드 인, 페이드 아웃, 살짝 밀기 등)</span><span class="sxs-lookup"><span data-stu-id="fdd02-123">Screen Transition support (fade in, fade out, swipe, etc.)</span></span>

- <span data-ttu-id="fdd02-124">터치 스크린, 제스처, 가상 키보드 지원</span><span class="sxs-lookup"><span data-stu-id="fdd02-124">Touch Screen, Gesture, and Virtual Keyboard Support</span></span>

- <span data-ttu-id="fdd02-125">비트맵 압축</span><span class="sxs-lookup"><span data-stu-id="fdd02-125">Bitmap compression</span></span>

- <span data-ttu-id="fdd02-126">알파 혼합 지원</span><span class="sxs-lookup"><span data-stu-id="fdd02-126">Alpha Blending Support</span></span>

- <span data-ttu-id="fdd02-127">디더링 지원</span><span class="sxs-lookup"><span data-stu-id="fdd02-127">Dither Support</span></span>

- <span data-ttu-id="fdd02-128">앤티앨리어싱 지원</span><span class="sxs-lookup"><span data-stu-id="fdd02-128">Anti-Aliasing Support</span></span>

- <span data-ttu-id="fdd02-129">스킨 적용과 테마</span><span class="sxs-lookup"><span data-stu-id="fdd02-129">Skinning and Themes</span></span>

- <span data-ttu-id="fdd02-130">캔버스 혼합</span><span class="sxs-lookup"><span data-stu-id="fdd02-130">Canvas Blending</span></span>

- <span data-ttu-id="fdd02-131">전체 창 관리</span><span class="sxs-lookup"><span data-stu-id="fdd02-131">Complete Window Management</span></span>

  - <span data-ttu-id="fdd02-132">부모/자식 관계</span><span class="sxs-lookup"><span data-stu-id="fdd02-132">Parent/Child Relationship</span></span>

  - <span data-ttu-id="fdd02-133">동적 만들기, 삭제, 크기 조정, 이동</span><span class="sxs-lookup"><span data-stu-id="fdd02-133">Dynamic creation, deletion, resizing, moving</span></span>
  - <span data-ttu-id="fdd02-134">별도의 이벤트 처리와 그리기</span><span class="sxs-lookup"><span data-stu-id="fdd02-134">Separate event handling and drawing</span></span> 
  - <span data-ttu-id="fdd02-135">z 순서</span><span class="sxs-lookup"><span data-stu-id="fdd02-135">Z-order</span></span>
  - <span data-ttu-id="fdd02-136">클리핑과 보기</span><span class="sxs-lookup"><span data-stu-id="fdd02-136">Clipping and views</span></span>

- <span data-ttu-id="fdd02-137">광범위한 위젯 세트</span><span class="sxs-lookup"><span data-stu-id="fdd02-137">Extensive Set of Widgets</span></span>

  - <span data-ttu-id="fdd02-138">다양한 단추 유형, 슬라이더, 다이얼</span><span class="sxs-lookup"><span data-stu-id="fdd02-138">Various button types, sliders, and dials</span></span>

  - <span data-ttu-id="fdd02-139">드롭다운 목록</span><span class="sxs-lookup"><span data-stu-id="fdd02-139">Drop Down List</span></span>
  
  - <span data-ttu-id="fdd02-140">prompt</span><span class="sxs-lookup"><span data-stu-id="fdd02-140">Prompt</span></span>

  - <span data-ttu-id="fdd02-141">여러 줄 텍스트 보기</span><span class="sxs-lookup"><span data-stu-id="fdd02-141">Multi-Line text view</span></span>
  
  - <span data-ttu-id="fdd02-142">한 줄과 여러 줄 텍스트 입력</span><span class="sxs-lookup"><span data-stu-id="fdd02-142">Single and Multi-Line text input</span></span>
  
  - <span data-ttu-id="fdd02-143">숫자와 텍스트 스크롤 휠</span><span class="sxs-lookup"><span data-stu-id="fdd02-143">Numeric and Textual Scroll Wheels</span></span>
  
  - <span data-ttu-id="fdd02-144">창과 스크롤 막대</span><span class="sxs-lookup"><span data-stu-id="fdd02-144">Windows and Scroll Bars</span></span>
  
  - <span data-ttu-id="fdd02-145">방사형 진행률 표시줄</span><span class="sxs-lookup"><span data-stu-id="fdd02-145">Radial Progress Bar</span></span>
  
  - <span data-ttu-id="fdd02-146">스프라이트</span><span class="sxs-lookup"><span data-stu-id="fdd02-146">Sprite</span></span>

### <a name="ansi-c-source-code"></a><span data-ttu-id="fdd02-147">ANSI C 소스 코드</span><span class="sxs-lookup"><span data-stu-id="fdd02-147">ANSI C Source Code</span></span>

<span data-ttu-id="fdd02-148">GUIX는 완전히 ANSI C로 작성되었으며 ANSI C 컴파일러와 ThreadX를 지원하는 모든 프로세서 아키텍처에 실제로 즉시 이식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-148">GUIX is written completely in ANSI C and is portable immediately to virtually any processor architecture that has an ANSI C compiler and ThreadX support.</span></span> <span data-ttu-id="fdd02-149">ANSI C로 작성되었지만 GUIX는 개체 지향 모델과 상속을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-149">Although written in ANSI C, GUIX uses an object oriented model and inheritance.</span></span>

### <a name="not-a-black-box"></a><span data-ttu-id="fdd02-150">블랙 박스가 아님</span><span class="sxs-lookup"><span data-stu-id="fdd02-150">Not A Black Box</span></span>

<span data-ttu-id="fdd02-151">대부분의 GUIX 배포판에는 전체 C 소스 코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-151">Most distributions of GUIX include the complete C source code.</span></span> <span data-ttu-id="fdd02-152">따라서 많은 상용 GUI 구현에서 발생하는 “블랙 박스” 문제를 없앨 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-152">This eliminates the “black-box” problems that occur with many commercial GUI implementations.</span></span> <span data-ttu-id="fdd02-153">애플리케이션 개발자는 GUIX를 사용하여 GUI가 수행하는 작업을 정확하게 파악할 수 있기 때문에 모든 것이 명확합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-153">By using GUIX, applications developers can see exactly what the GUI is doing—there are no mysteries!</span></span>

<span data-ttu-id="fdd02-154">소스 코드가 있기 때문에 애플리케이션 관련 수정이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-154">Having the source code also allows for application specific modifications.</span></span> <span data-ttu-id="fdd02-155">권장되지는 않지만 필요한 경우 GUI를 수정하는 기능을 제공한 것은 확실히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-155">Although not recommended, it is certainly beneficial to have the ability to modify the GUI if it is required.</span></span> <span data-ttu-id="fdd02-156">해당 기능은 사내 또는 퍼블릭 도메인 제품으로 작업하는 데 익숙한 개발자에게 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-156">These features are especially comforting to developers accustomed to working with in-house or public domain products.</span></span> <span data-ttu-id="fdd02-157">이들에게는 소스 코드와 소스 코드를 수정할 수 있는 기능이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-157">They expect to have source code and the ability to modify it.</span></span> <span data-ttu-id="fdd02-158">GUIX는 이와 같은 개발자를 위한 최고의 GUI 소프트웨어입니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-158">GUIX is the ultimate GUI software for such developers.</span></span>

## <a name="embedded-gui-applications"></a><span data-ttu-id="fdd02-159">포함된 GUI 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="fdd02-159">Embedded GUI Applications</span></span>

<span data-ttu-id="fdd02-160">포함된 GUI 애플리케이션은 사용자 인터페이스 요구 사항이 있으며 휴대폰, 통신 장비, 자동차 엔진, 레이저 프린터, 의료 디바이스 등의 제품 내에서 숨겨진 마이크로프로세서에서 실행되는 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-160">Embedded GUI applications are applications that have a user interface requirement and execute on microprocessors hidden inside products such as cellular phones, communication equipment, automotive engines, laser printers, medical devices, and so forth.</span></span> <span data-ttu-id="fdd02-161">이와 같은 애플리케이션에는 거의 항상 몇 가지 메모리와 성능 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-161">Such applications almost always have some memory and performance constraints.</span></span> <span data-ttu-id="fdd02-162">포함된 GUI의 또 다른 차이점은 소프트웨어와 하드웨어에 전용 용도가 있다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-162">Another distinction of embedded GUI is that their software and hardware have a dedicated purpose.</span></span>

### <a name="real-time-gui-software"></a><span data-ttu-id="fdd02-163">실시간 GUI 소프트웨어</span><span class="sxs-lookup"><span data-stu-id="fdd02-163">Real-time GUI Software</span></span>

<span data-ttu-id="fdd02-164">기본적으로 정확한 시간 내에 처리를 수행해야 하는 GUI 소프트웨어를 ‘실시간 GUI’ 소프트웨어라고 하며, 시간 제약 조건이 GUI 애플리케이션에 적용되는 경우에는 실시간 애플리케이션으로 분류됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-164">Basically, GUI software that must perform its processing within an exact period of time is called *real-time GUI* software, and when time constraints are imposed on GUI applications, they are classified as realtime applications.</span></span> <span data-ttu-id="fdd02-165">포함된 GUI 애플리케이션은 본질적으로 외부와 상호 작용하기 때문에 거의 항상 실시간입니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-165">Embedded GUI applications are almost always real-time because of their inherent interaction with the external world.</span></span>

## <a name="guix-benefits"></a><span data-ttu-id="fdd02-166">GUIX의 이점</span><span class="sxs-lookup"><span data-stu-id="fdd02-166">GUIX Benefits</span></span>

<span data-ttu-id="fdd02-167">포함된 애플리케이션에 GUIX를 사용하는 경우의 주요 이점은 고성능, 풍부한 기능과 매우 작은 메모리 요구 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-167">The primary benefits of using GUIX for embedded applications are high-performance, feature rich, and very small memory requirements.</span></span> <span data-ttu-id="fdd02-168">또한 GUIX는 뛰어난 성능을 자랑하는 멀티태스킹 Azure RTOS ThreadX 실시간 운영 체제와 완전히 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-168">GUIX is also completely integrated with the high-performance, multitasking Azure RTOS ThreadX real-time operating system.</span></span>

### <a name="improved-responsiveness"></a><span data-ttu-id="fdd02-169">향상된 응답성</span><span class="sxs-lookup"><span data-stu-id="fdd02-169">Improved Responsiveness</span></span>

<span data-ttu-id="fdd02-170">고성능 GUIX 제품을 사용하면 애플리케이션이 이전보다 빠르게 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-170">The high-performance GUIX product enables applications to respond faster than ever before.</span></span> <span data-ttu-id="fdd02-171">이는 시각적 정보의 양이 많거나 해당 정보를 표시하는 데 엄격한 시간 요구 사항이 있는 포함된 애플리케이션에 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-171">This is especially important for embedded applications that either have a significant volume of visual information or strict timing requirements on displaying such information.</span></span>

### <a name="software-maintenance"></a><span data-ttu-id="fdd02-172">소프트웨어 유지 관리</span><span class="sxs-lookup"><span data-stu-id="fdd02-172">Software Maintenance</span></span>

<span data-ttu-id="fdd02-173">GUIX를 사용하면 개발자는 포함된 애플리케이션의 GUI 측면을 쉽게 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-173">Using GUIX allows developers to easily partition the GUI aspects of their embedded application.</span></span> <span data-ttu-id="fdd02-174">분할을 통해 전체 개발 프로세스를 쉽게 진행하고 향후 소프트웨어 유지 관리를 크게 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-174">This partitioning makes the entire development process easy and significantly enhances future software maintenance.</span></span>

### <a name="increased-throughput"></a><span data-ttu-id="fdd02-175">향상된 처리량</span><span class="sxs-lookup"><span data-stu-id="fdd02-175">Increased Throughput</span></span>

<span data-ttu-id="fdd02-176">GUIX는 포함된 애플리케이션으로 직접 전송하는, 사용 가능한 최고 성능의 GUI를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-176">GUIX provides the highest-performance GUI available, which directly transfers to the embedded application.</span></span> <span data-ttu-id="fdd02-177">GUIX 애플리케이션은 비 GUIX 애플리케이션보다 사용자 인터페이스 정보를 빠르게 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-177">GUIX applications are able to process user interface information faster than non-GUIX applications!</span></span>

### <a name="processor-isolation"></a><span data-ttu-id="fdd02-178">프로세서 격리</span><span class="sxs-lookup"><span data-stu-id="fdd02-178">Processor Isolation</span></span>

<span data-ttu-id="fdd02-179">GUIX는 애플리케이션, 기본 프로세서, 디스플레이 하드웨어 간에 프로세서와 관련이 없는 강력한 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-179">GUIX provides a robust, processor-independent interface between the application and the underlying processor and display hardware.</span></span> <span data-ttu-id="fdd02-180">이를 통해 개발자는 디스플레이 하드웨어 문제를 처리하는 데 시간을 더 낭비하지 않고 사용자 인터페이스의 수준 높은 문제에 집중할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-180">This allows developers to concentrate on the high-level aspects of the user interface rather than spending extra time dealing with display hardware issues.</span></span>

### <a name="ease-of-use"></a><span data-ttu-id="fdd02-181">사용 편의성</span><span class="sxs-lookup"><span data-stu-id="fdd02-181">Ease of Use</span></span>

<span data-ttu-id="fdd02-182">GUIX는 애플리케이션 개발자를 염두에 두고 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-182">GUIX is designed with the application developer in mind.</span></span> <span data-ttu-id="fdd02-183">GUIX 아키텍처와 서비스 호출 인터페이스는 이해하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-183">The GUIX architecture and service call interface are easy to understand.</span></span> <span data-ttu-id="fdd02-184">따라서 GUIX 개발자는 고급 기능을 신속하게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-184">As a result, GUIX developers can quickly use its advanced features.</span></span>

### <a name="improve-time-to-market"></a><span data-ttu-id="fdd02-185">출시 시간 단축</span><span class="sxs-lookup"><span data-stu-id="fdd02-185">Improve Time to Market</span></span>

<span data-ttu-id="fdd02-186">GUIX의 강력한 기능은 소프트웨어 개발 프로세스를 가속화합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-186">The powerful features of GUIX accelerate the software development process.</span></span> <span data-ttu-id="fdd02-187">GUIX는 대부분의 프로세서 및 디스플레이 하드웨어 문제를 추상화하여 대다수의 애플리케이션 사용자 인터페이스 구현에서 해당 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-187">GUIX abstracts most processor and display hardware issues, thereby removing these concerns from a majority of application user interface implementation.</span></span> <span data-ttu-id="fdd02-188">이 기능은 사용 편의성 및 고급 기능 세트와 함께 출시 시간을 단축해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-188">This feature, coupled with the ease-of-use and advanced feature set, results in a faster time to market!</span></span>

### <a name="protecting-the-software-investment"></a><span data-ttu-id="fdd02-189">소프트웨어 투자 보호</span><span class="sxs-lookup"><span data-stu-id="fdd02-189">Protecting the Software Investment</span></span>

<span data-ttu-id="fdd02-190">GUIX는 ANSI C로만 작성되며 Azure RTOS ThreadX 실시간 운영 체제와 완전히 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-190">GUIX is written exclusively in ANSI C and is fully integrated with the Azure RTOS ThreadX real-time operating system.</span></span> <span data-ttu-id="fdd02-191">즉, GUIX 애플리케이션은 모든 ThreadX 지원 프로세서에 즉시 이식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-191">This means GUIX applications are instantly portable to all ThreadX supported processors.</span></span> <span data-ttu-id="fdd02-192">더 놀라운 점은 ThreadX를 사용하면 불과 몇 주 만에 완전히 새로운 프로세서 아키텍처를 지원할 수 있다는 사실입니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-192">Better yet, a completely new processor architecture can be supported with ThreadX in a matter of weeks.</span></span> <span data-ttu-id="fdd02-193">따라서 GUIX를 사용하면 애플리케이션의 마이그레이션 경로를 보장하고 원래 개발 투자를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd02-193">As a result, using GUIX ensures the application’s migration path and protects the original development investment.</span></span>
