---
title: Azure RTOS GUIX 및 Azure RTOS GUIX Studio 이해
description: Azure RTOS GUIX는 포함된 시스템 개발자의 요구 사항에 맞게 제작된 전문가용 패키지입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 8f4a1578fcabdabfb213ced9c6593f6cffc964aa
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171406"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="bf944-103">Azure RTOS GUIX 및 Azure RTOS GUIX Studio 개요</span><span class="sxs-lookup"><span data-stu-id="bf944-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="bf944-104">Azure GUIX 내장형 GUI는 심층 내장형, 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 Microsoft의 고급 산업용 GUI 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="bf944-105">또한 Microsoft는 개발자가 데스크톱에서 GUI를 디자인하고 대상으로 내보낼 수 있는 Azure RTOS GUIX 내장형 GUI 코드를 생성할 수 있는 Azure RTOS GUIX Studio라는 모든 기능을 갖춘 WYSIWYG 데스크톱 디자인 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="bf944-106">Azure RTOS GUIX는 Azure RTOS ThreadX RTOS와 완전히 통합되며 Azure RTOS ThreadX에서 지원하는 많은 동일한 프로세서에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="bf944-107">또한 Azure RTOS GUIX는 매우 적은 메모리 공간에서 고속 실행과 뛰어난 사용 편의성을 구현하므로, 사용자 인터페이스가 요구되는 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="bf944-108">Azure RTOS GUIX API</span><span class="sxs-lookup"><span data-stu-id="bf944-108">Azure RTOS GUIX API</span></span>

### <a name="powerful-apis"></a><span data-ttu-id="bf944-109">강력한 API</span><span class="sxs-lookup"><span data-stu-id="bf944-109">Powerful APIs</span></span>

* <span data-ttu-id="bf944-110">필요할 때 직접 캔버스 그리기 완벽 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-110">Full support for direct canvas drawing when needed</span></span>
* <span data-ttu-id="bf944-111">Azure RTOS GUIX Studio 생성 코드와 간단하게 상호 작용</span><span class="sxs-lookup"><span data-stu-id="bf944-111">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>
* <span data-ttu-id="bf944-112">선, 사각형, 다각형 등을 위한 API</span><span class="sxs-lookup"><span data-stu-id="bf944-112">APIs for line, rectangle, polygon, etc.</span></span>
* <span data-ttu-id="bf944-113">원, 호, 원형, 현, 타원 등을 위한 API</span><span class="sxs-lookup"><span data-stu-id="bf944-113">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>
* <span data-ttu-id="bf944-114">텍스트 그리기 및 위치 지정을 위한 API</span><span class="sxs-lookup"><span data-stu-id="bf944-114">APIs for text drawing and positioning</span></span>
* <span data-ttu-id="bf944-115">앤티앨리어싱, 텍스처 채우기 및 단색 채우기</span><span class="sxs-lookup"><span data-stu-id="bf944-115">Anti-aliasing, texture fills, and solid fills</span></span>
* <span data-ttu-id="bf944-116">화면과 위젯 생성 및 수정을 위한 API</span><span class="sxs-lookup"><span data-stu-id="bf944-116">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="bf944-117">Azure RTOS GUIX Studio 생성 파일</span><span class="sxs-lookup"><span data-stu-id="bf944-117">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="bf944-118">자동으로 생성된 ANSI C 원본 파일</span><span class="sxs-lookup"><span data-stu-id="bf944-118">Automatically generated ANSI C source files</span></span>
* <span data-ttu-id="bf944-119">레이아웃 정보에서 애플리케이션 소프트웨어 분리</span><span class="sxs-lookup"><span data-stu-id="bf944-119">Insulates application software from layout details</span></span>
* <span data-ttu-id="bf944-120">UI 디자인에 필요한 글꼴 및 이미지 포함</span><span class="sxs-lookup"><span data-stu-id="bf944-120">Includes fonts and images required by UI design</span></span>
* <span data-ttu-id="bf944-121">애플리케이션 코드로 컴파일 및 생성된 파일</span><span class="sxs-lookup"><span data-stu-id="bf944-121">Generated files compiled with application code</span></span>
* <span data-ttu-id="bf944-122">애플리케이션 논리에 영향을 주지 않고 화면 레이아웃 업데이트 가능</span><span class="sxs-lookup"><span data-stu-id="bf944-122">Screen layout can be updated without affecting application logic</span></span>
* <span data-ttu-id="bf944-123">리소스 ID에서 언어 및 테마 독립성 만들기</span><span class="sxs-lookup"><span data-stu-id="bf944-123">Resource IDs create language and theme independence</span></span>
* <span data-ttu-id="bf944-124">사용자가 제공하는 사용자 지정 그리기 및 이벤트 처리 함수</span><span class="sxs-lookup"><span data-stu-id="bf944-124">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="bf944-125">위젯 라이브러리</span><span class="sxs-lookup"><span data-stu-id="bf944-125">Widget library</span></span>

* <span data-ttu-id="bf944-126">사전 정의되었지만 사용자 정의 가능한 공통 인터페이스 요소 세트</span><span class="sxs-lookup"><span data-stu-id="bf944-126">Pre-defined but customizable set of common interface elements</span></span>
* <span data-ttu-id="bf944-127">매우 작고 간단하고 효율적</span><span class="sxs-lookup"><span data-stu-id="bf944-127">Extremely small, compact, and efficient</span></span>
* <span data-ttu-id="bf944-128">라이브러리에 단추, 계기, 목록, 창, 스크롤, 슬라이더, 진행률 표시줄, 프롬프트 등이 포함됨</span><span class="sxs-lookup"><span data-stu-id="bf944-128">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>
* <span data-ttu-id="bf944-129">완전히 사용자 지정 가능한 그리기 및 모양</span><span class="sxs-lookup"><span data-stu-id="bf944-129">Fully customizable drawing and appearance</span></span>
* <span data-ttu-id="bf944-130">완전히 사용자 지정 가능한 작업 및 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="bf944-130">Fully customizable operation and event handling</span></span>
* <span data-ttu-id="bf944-131">사용된 위젯만 애플리케이션 소프트웨어와 연결됨</span><span class="sxs-lookup"><span data-stu-id="bf944-131">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="bf944-132">수학 및 유틸리티</span><span class="sxs-lookup"><span data-stu-id="bf944-132">Math and utilities</span></span>

* <span data-ttu-id="bf944-133">사인, 코사인, 아크사인, 아크코사인, 탄젠트, 제곱근에 대한 함수</span><span class="sxs-lookup"><span data-stu-id="bf944-133">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>
* <span data-ttu-id="bf944-134">화면 영역 조작을 위한 함수</span><span class="sxs-lookup"><span data-stu-id="bf944-134">Functions for manipulating screen regions</span></span>
* <span data-ttu-id="bf944-135">시스템 구성 및 시작</span><span class="sxs-lookup"><span data-stu-id="bf944-135">System configuration and startup</span></span>
* <span data-ttu-id="bf944-136">메모리 풀 정의(옵션)</span><span class="sxs-lookup"><span data-stu-id="bf944-136">Memory pool definition (optional)</span></span>
* <span data-ttu-id="bf944-137">타이머 관리</span><span class="sxs-lookup"><span data-stu-id="bf944-137">Timer Management</span></span>
* <span data-ttu-id="bf944-138">애니메이션 관리</span><span class="sxs-lookup"><span data-stu-id="bf944-138">Animation Management</span></span>
* <span data-ttu-id="bf944-139">더티 목록 유지 관리</span><span class="sxs-lookup"><span data-stu-id="bf944-139">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="bf944-140">이미지 처리</span><span class="sxs-lookup"><span data-stu-id="bf944-140">Image processing</span></span>

* <span data-ttu-id="bf944-141">jpeg 및 png 이미지의 런타임 디코딩을 위한 함수</span><span class="sxs-lookup"><span data-stu-id="bf944-141">Functions for runtime decode of jpeg and png images</span></span>
* <span data-ttu-id="bf944-142">디더링 및 색 공간 변환 적용</span><span class="sxs-lookup"><span data-stu-id="bf944-142">Apply dithering and color space conversion</span></span>
* <span data-ttu-id="bf944-143">이미지 회전</span><span class="sxs-lookup"><span data-stu-id="bf944-143">Image rotation</span></span>
* <span data-ttu-id="bf944-144">이미지 크기 조정</span><span class="sxs-lookup"><span data-stu-id="bf944-144">Image scaling</span></span>
* <span data-ttu-id="bf944-145">이미지 혼합</span><span class="sxs-lookup"><span data-stu-id="bf944-145">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="bf944-146">이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="bf944-146">Event processing</span></span>

* <span data-ttu-id="bf944-147">유휴 상태일 때 자동으로 Azure RTOS GUIX 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="bf944-147">Automatically suspends Azure RTOS GUIX thread when idle</span></span>
* <span data-ttu-id="bf944-148">UI 디자인에 널리 사용되는 이벤트 기반 프로그래밍 모델</span><span class="sxs-lookup"><span data-stu-id="bf944-148">Event-driven programming model popular in UI design</span></span>
* <span data-ttu-id="bf944-149">Azure RTOS GUIX 그리기 스레드에서 입력 드라이버 분리</span><span class="sxs-lookup"><span data-stu-id="bf944-149">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>
* <span data-ttu-id="bf944-150">이벤트를 보내고 받기 위한 함수</span><span class="sxs-lookup"><span data-stu-id="bf944-150">Functions for sending and receiving events</span></span>
* <span data-ttu-id="bf944-151">모든 Azure RTOS GUIX 위젯 형식에 대한 미리 정의된 이벤트 형식</span><span class="sxs-lookup"><span data-stu-id="bf944-151">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>
* <span data-ttu-id="bf944-152">사용자 정의된 사용자 지정 이벤트 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-152">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="bf944-153">캔버스 처리</span><span class="sxs-lookup"><span data-stu-id="bf944-153">Canvas processing</span></span>

* <span data-ttu-id="bf944-154">클리핑 및 Z 순서 유지 관리</span><span class="sxs-lookup"><span data-stu-id="bf944-154">Clipping and Z-Order maintenance</span></span>
* <span data-ttu-id="bf944-155">하드웨어 정보에서 위젯 라이브러리 분리</span><span class="sxs-lookup"><span data-stu-id="bf944-155">Insulates widget library from hardware details</span></span>
* <span data-ttu-id="bf944-156">하드웨어 정보에서 애플리케이션 분리</span><span class="sxs-lookup"><span data-stu-id="bf944-156">Insulates application from hardware details</span></span>
* <span data-ttu-id="bf944-157">더티 영역의 자동 백그라운드 새로 고침</span><span class="sxs-lookup"><span data-stu-id="bf944-157">Automatic background refresh of dirty areas</span></span>
* <span data-ttu-id="bf944-158">계층화 및 혼합이 지원되는 여러 캔버스</span><span class="sxs-lookup"><span data-stu-id="bf944-158">Multiple canvases with layering and blending supported</span></span>
* <span data-ttu-id="bf944-159">애플리케이션 소프트웨어에서 직접 호출 가능</span><span class="sxs-lookup"><span data-stu-id="bf944-159">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="bf944-160">입력 디바이스 드라이버</span><span class="sxs-lookup"><span data-stu-id="bf944-160">Input device driver(s)</span></span>

* <span data-ttu-id="bf944-161">하드웨어 관련 지원, 하드웨어 정보에서 Azure RTOS GUIX 및 애플리케이션 분리</span><span class="sxs-lookup"><span data-stu-id="bf944-161">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>
* <span data-ttu-id="bf944-162">저항 접촉식 터치, 캡 터치 및 키패드 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-162">Resistive Touch, Cap Touch, and keypad supported</span></span>
* <span data-ttu-id="bf944-163">Azure RTOS GUIX 이벤트 큐에 입력 이벤트 전달</span><span class="sxs-lookup"><span data-stu-id="bf944-163">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="bf944-164">디스플레이 드라이버</span><span class="sxs-lookup"><span data-stu-id="bf944-164">Display drivers</span></span>

* <span data-ttu-id="bf944-165">하드웨어 관련 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-165">Hardware-specific support</span></span>
* <span data-ttu-id="bf944-166">모든 색 농도 및 형식에 대해 제공되는 일반 드라이버</span><span class="sxs-lookup"><span data-stu-id="bf944-166">Generic drivers provided for all color depth and formats</span></span>
* <span data-ttu-id="bf944-167">사용 가능한 그래픽 가속기를 활용하도록 사용자 지정됨</span><span class="sxs-lookup"><span data-stu-id="bf944-167">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="bf944-168">대상 하드웨어</span><span class="sxs-lookup"><span data-stu-id="bf944-168">Target hardware</span></span>

* <span data-ttu-id="bf944-169">그래픽 출력을 지원하는 거의 모든 하드웨어가 GUIX와 호환</span><span class="sxs-lookup"><span data-stu-id="bf944-169">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>
* <span data-ttu-id="bf944-170">여러 물리적 디스플레이 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-170">Multiple physical displays supported</span></span>
* <span data-ttu-id="bf944-171">최소 RAM 및 플래시 요구 사항</span><span class="sxs-lookup"><span data-stu-id="bf944-171">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="bf944-172">세련된 사용자 인터페이스 만들기</span><span class="sxs-lookup"><span data-stu-id="bf944-172">Create Elegant User Interfaces</span></span>

<span data-ttu-id="bf944-173">Azure RTOS GUIX 및 Azure RTOS GUIX Studio는 세련된 사용자 인터페이스를 만드는 데 필요한 모든 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-173">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="bf944-174">표준 Azure RTOS GUIX 패키지에는 의료 기기 참조, 스마트 시계 참조, 가정 자동화 참조, 산업 제어 참조, 자동차 참조, 다양한 스프라이트 및 애니메이션 예제를 비롯한 다양한 샘플 사용자 인터페이스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-174">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="bf944-175">아래에 표시된 참조 예제를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="bf944-175">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="bf944-176">가정 자동화</span><span class="sxs-lookup"><span data-stu-id="bf944-176">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="bf944-177">의료</span><span class="sxs-lookup"><span data-stu-id="bf944-177">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="bf944-178">소비자</span><span class="sxs-lookup"><span data-stu-id="bf944-178">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="bf944-179">백색 가전</span><span class="sxs-lookup"><span data-stu-id="bf944-179">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="bf944-180">자동차</span><span class="sxs-lookup"><span data-stu-id="bf944-180">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="bf944-181">공업 제품</span><span class="sxs-lookup"><span data-stu-id="bf944-181">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="bf944-182">Azure RTOS GUIX 참조마다 참조 디자인의 모든 그래픽 요소를 정의하는 해당 Azure RTOS GUIX Studio 프로젝트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-182">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="bf944-183">참조 디자인을 변경하는 것은 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-183">Changing a reference design is easy.</span></span> <span data-ttu-id="bf944-184">해당하는 Azure RTOS GUIX 프로젝트를 열고 원하는 대로 변경한 후 프로젝트를 저장하고 *프로젝트* 를 선택하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-184">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="bf944-185">모든 출력 파일을 생성하여 Azure RTOS GUIX에 대한 C 코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-185">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="bf944-186">그런 다음, 대상 애플리케이션을 다시 빌드하고 실행하여 수정된 참조 디자인을 관찰합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-186">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="memory-footprint"></a><span data-ttu-id="bf944-187">메모리 공간</span><span class="sxs-lookup"><span data-stu-id="bf944-187">Memory footprint</span></span>

<span data-ttu-id="bf944-188">Azure RTOS GUIX는 캔버스에 필요한 메모리를 제외하고 기본 지원을 위한 13.2KB의 FLASH 및 4KB RAM의 매우 작은 최소 메모리 공간을 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-188">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="bf944-189">내부 GRAM 및 자체 새로 고침 기술이 있는 디스플레이의 경우 캔버스 메모리가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-189">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="bf944-190">그러나 그리기 성능 향상이나 디스플레이에 로컬인 GRAM을 활용하지 않는 디스플레이 구성을 위해 캔버스 메모리 영역이 애플리케이션에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-190">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="bf944-191">캔버스 메모리 요구 사항은 캔버스 크기 및 색 농도의 함수이며 다음 수식으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-191">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="bf944-192"><i>캔버스 RAM(바이트) = (x \* y \* (bpp/8))</i></span><span class="sxs-lookup"><span data-stu-id="bf944-192"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="bf944-193">여기서 "x"와 "y"는 캔버스(디스플레이)의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-193">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="bf944-194">또한 대부분의 애플리케이션은 핵심 Azure RTOS GUIX 라이브러리 스토리지 요구 사항에 포함되지 않은 그래픽 리소스를 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-194">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="bf944-195">이러한 리소스에는 글꼴, 그래픽 아이콘(pixelmap) 및 정적 문자열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-195">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="bf944-196">이 데이터는 const 메모리 섹션(예: FLASH)에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-196">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="bf944-197">이 메모리 영역의 크기는 사용되는 고유 글꼴의 수와 크기, 사용되는 그래픽 아이콘의 수와 크기, 출력 색 형식, 각 리소스가 압축된 데이터를 사용하는지 여부를 포함한 여러 요인에 따라 달라집니다. Azure RTOS GUIX는 글꼴 데이터와 pixelmap 데이터 모두의 RLE 압축을 지원하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-197">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="bf944-198">각 리소스에 대한 스토리지 요구 사항은 Azure RTOS GUIX Studio 애플리케이션 내에 표시되므로 사용자는 애플리케이션 리소스에서 사용하는 플래시 메모리의 양을 추적하고 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-198">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="bf944-199">Azure RTOS ThreadX와 같이 Azure RTOS GUIX의 크기는 애플리케이션에서 실제로 사용하는 서비스에 따라 자동으로 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-199">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="bf944-200">이렇게 하면 사실상 복잡한 구성 및 빌드 매개 변수가 제거되어 개발자가 더 쉽게 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-200">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="bf944-201">간단하고 손쉬운 사용</span><span class="sxs-lookup"><span data-stu-id="bf944-201">Simple, easy-to-use</span></span>

<span data-ttu-id="bf944-202">Azure RTOS GUIX는 사용이 매우 간단합니다. Azure RTOS GUIX Studio를 사용하면 개발자가 데스크톱에서 시각적으로 디자인하고 실제 대상에서 실행되는 C 코드를 생성할 수 있으므로 Azure RTOS GUIX를 훨씬 더 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-202">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="bf944-203">그러면 애플리케이션에서 자체 사용자 지정 이벤트 처리 및 그리기 기능을 추가하여 GUI를 완성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-203">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="bf944-204">Azure RTOS GUIX API를 사용하는 것은 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-204">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="bf944-205">Azure RTOS GUIX API는 직관적이고 매우 기능적입니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-205">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="bf944-206">API 이름은 다른 파일 시스템 제품에서 흔히 볼 수 있는 매우 축약된 이름 및/또는 “알파벳 약자”가 아니라 실제 단어로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-206">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="bf944-207">모든 Azure RTOS GUIX API에는 선행 *gx_* 가 있으며 명사-동사 명명 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-207">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="bf944-208">또한 API 전체에 걸쳐 기능적 일관성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-208">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="bf944-209">예를 들어 위젯 제어 블록을 초기화하는 모든 API의 이름은 &lt; widget_type&gt;_create이고 각 위젯 형식에 대한 만들기 함수 매개 변수는 항상 동일한 순서로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-209">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="bf944-210">포괄적인 기본 제공 위젯 세트</span><span class="sxs-lookup"><span data-stu-id="bf944-210">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="bf944-211">Azure RTOS GUIX는 다음과 같은 다양한 기본 제공 위젯 세트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-211">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>
* <span data-ttu-id="bf944-212">아코디언 메뉴</span><span class="sxs-lookup"><span data-stu-id="bf944-212">Accordion Menu</span></span>
* <span data-ttu-id="bf944-213">단추</span><span class="sxs-lookup"><span data-stu-id="bf944-213">Button</span></span>
* <span data-ttu-id="bf944-214">확인란</span><span class="sxs-lookup"><span data-stu-id="bf944-214">Checkbox</span></span>
* <span data-ttu-id="bf944-215">순환 계기</span><span class="sxs-lookup"><span data-stu-id="bf944-215">Circular Gauge</span></span>
* <span data-ttu-id="bf944-216">드롭다운 목록</span><span class="sxs-lookup"><span data-stu-id="bf944-216">Drop Down List</span></span>
* <span data-ttu-id="bf944-217">가로 목록</span><span class="sxs-lookup"><span data-stu-id="bf944-217">Horizontal List</span></span>
* <span data-ttu-id="bf944-218">가로 스크롤 막대 창</span><span class="sxs-lookup"><span data-stu-id="bf944-218">Horizontal Scrollbar Window</span></span>
* <span data-ttu-id="bf944-219">아이콘</span><span class="sxs-lookup"><span data-stu-id="bf944-219">Icon</span></span>
* <span data-ttu-id="bf944-220">아이콘 단추</span><span class="sxs-lookup"><span data-stu-id="bf944-220">Icon Button</span></span>
* <span data-ttu-id="bf944-221">꺾은선형 차트</span><span class="sxs-lookup"><span data-stu-id="bf944-221">Line Chart</span></span>
* <span data-ttu-id="bf944-222">메뉴</span><span class="sxs-lookup"><span data-stu-id="bf944-222">Menu</span></span>
* <span data-ttu-id="bf944-223">여러 줄 텍스트 단추</span><span class="sxs-lookup"><span data-stu-id="bf944-223">Multi Line Text Button</span></span>
* <span data-ttu-id="bf944-224">여러 줄 텍스트 입력</span><span class="sxs-lookup"><span data-stu-id="bf944-224">Multi Line Text Input</span></span>
* <span data-ttu-id="bf944-225">여러 줄 텍스트 보기</span><span class="sxs-lookup"><span data-stu-id="bf944-225">Multi Line Text View</span></span>
* <span data-ttu-id="bf944-226">숫자 Pixelmap 프롬프트</span><span class="sxs-lookup"><span data-stu-id="bf944-226">Numeric Pixelmap Prompt</span></span>
* <span data-ttu-id="bf944-227">숫자 프롬프트</span><span class="sxs-lookup"><span data-stu-id="bf944-227">Numeric Prompt</span></span>
* <span data-ttu-id="bf944-228">숫자 스크롤 휠</span><span class="sxs-lookup"><span data-stu-id="bf944-228">Numeric Scroll Wheel</span></span>
* <span data-ttu-id="bf944-229">Pixelmap 단추</span><span class="sxs-lookup"><span data-stu-id="bf944-229">Pixelmap Button</span></span>
* <span data-ttu-id="bf944-230">Pixelmap 프롬프트</span><span class="sxs-lookup"><span data-stu-id="bf944-230">Pixelmap Prompt</span></span>
* <span data-ttu-id="bf944-231">Pixelmap 슬라이더</span><span class="sxs-lookup"><span data-stu-id="bf944-231">Pixelmap Slider</span></span>
* <span data-ttu-id="bf944-232">Pixelmap 스프라이트</span><span class="sxs-lookup"><span data-stu-id="bf944-232">Pixelmap Sprite</span></span>
* <span data-ttu-id="bf944-233">Progress Bar</span><span class="sxs-lookup"><span data-stu-id="bf944-233">Progress Bar</span></span>
* <span data-ttu-id="bf944-234">prompt</span><span class="sxs-lookup"><span data-stu-id="bf944-234">Prompt</span></span>
* <span data-ttu-id="bf944-235">방사형 진행률 표시줄</span><span class="sxs-lookup"><span data-stu-id="bf944-235">Radial Progress Bar</span></span>
* <span data-ttu-id="bf944-236">Radio Button</span><span class="sxs-lookup"><span data-stu-id="bf944-236">Radio Button</span></span>
* <span data-ttu-id="bf944-237">스크롤 휠</span><span class="sxs-lookup"><span data-stu-id="bf944-237">Scroll Wheel</span></span>
* <span data-ttu-id="bf944-238">한 줄 텍스트 입력</span><span class="sxs-lookup"><span data-stu-id="bf944-238">Single Line Text Input</span></span>
* <span data-ttu-id="bf944-239">슬라이더</span><span class="sxs-lookup"><span data-stu-id="bf944-239">Slider</span></span>
* <span data-ttu-id="bf944-240">문자열 스크롤 휠</span><span class="sxs-lookup"><span data-stu-id="bf944-240">String Scroll Wheel</span></span>
* <span data-ttu-id="bf944-241">텍스트 단추</span><span class="sxs-lookup"><span data-stu-id="bf944-241">Text Button</span></span>
* <span data-ttu-id="bf944-242">트리 뷰</span><span class="sxs-lookup"><span data-stu-id="bf944-242">Tree View</span></span>
* <span data-ttu-id="bf944-243">세로 목록</span><span class="sxs-lookup"><span data-stu-id="bf944-243">Vertical List</span></span>
* <span data-ttu-id="bf944-244">세로 스크롤 막대</span><span class="sxs-lookup"><span data-stu-id="bf944-244">Vertical Scrollbar</span></span>

<span data-ttu-id="bf944-245">애플리케이션에서 자체 고객 위젯도 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-245">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="bf944-246">완벽한 하위 수준 그리기 API</span><span class="sxs-lookup"><span data-stu-id="bf944-246">Complete low-level drawing API</span></span>

<span data-ttu-id="bf944-247">Azure RTOS GUIX는 애플리케이션에서 복잡한 그래픽 도형을 렌더링할 수 있도록 하는 강력한 캔버스 그리기 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-247">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="bf944-248">모든 기능은 높은 색상 농도 대상에서 앤티앨리어싱을 지원하며 단색 및 pixelmap 패턴 채우기를 포함하여 모든 도형의 윤곽선을 그리고 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-248">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="bf944-249">모든 그리기 기본 도형은 16bpp 이상의 색 농도로 실행 시 브러시 알파를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-249">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="bf944-250">그리기 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-250">Drawing functions include:</span></span>

* <span data-ttu-id="bf944-251">원호 그리기</span><span class="sxs-lookup"><span data-stu-id="bf944-251">Arc Draw</span></span>
* <span data-ttu-id="bf944-252">원 그리기</span><span class="sxs-lookup"><span data-stu-id="bf944-252">Circle Draw</span></span>
* <span data-ttu-id="bf944-253">선 그리기</span><span class="sxs-lookup"><span data-stu-id="bf944-253">Line Draw</span></span>
* <span data-ttu-id="bf944-254">원형 그리기</span><span class="sxs-lookup"><span data-stu-id="bf944-254">Pie Draw</span></span>
* <span data-ttu-id="bf944-255">Pixelmap 혼합</span><span class="sxs-lookup"><span data-stu-id="bf944-255">Pixelmap Blend</span></span>
* <span data-ttu-id="bf944-256">Pixelmap 타일</span><span class="sxs-lookup"><span data-stu-id="bf944-256">Pixelmap Tile</span></span>
* <span data-ttu-id="bf944-257">다각형 그리기</span><span class="sxs-lookup"><span data-stu-id="bf944-257">Polygon Draw</span></span>
* <span data-ttu-id="bf944-258">텍스트 그리기</span><span class="sxs-lookup"><span data-stu-id="bf944-258">Text Draw</span></span>
* <span data-ttu-id="bf944-259">현 그리기</span><span class="sxs-lookup"><span data-stu-id="bf944-259">Chord Draw</span></span>
* <span data-ttu-id="bf944-260">타원 그리기</span><span class="sxs-lookup"><span data-stu-id="bf944-260">Ellipse Draw</span></span>
* <span data-ttu-id="bf944-261">픽셀 그리기</span><span class="sxs-lookup"><span data-stu-id="bf944-261">Pixel Draw</span></span>
* <span data-ttu-id="bf944-262">Pixelmap 그리기</span><span class="sxs-lookup"><span data-stu-id="bf944-262">Pixelmap Draw</span></span>
* <span data-ttu-id="bf944-263">Pixelmap 회전</span><span class="sxs-lookup"><span data-stu-id="bf944-263">Pixelmap Rotate</span></span>
* <span data-ttu-id="bf944-264">사각형 그리기</span><span class="sxs-lookup"><span data-stu-id="bf944-264">Rectangle Draw</span></span>
* <span data-ttu-id="bf944-265">텍스트 혼합</span><span class="sxs-lookup"><span data-stu-id="bf944-265">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="bf944-266">기본 무료 글꼴 및 손쉬운 추가</span><span class="sxs-lookup"><span data-stu-id="bf944-266">Default free fonts and easy to add more</span></span>

<span data-ttu-id="bf944-267">Azure RTOS GUIX는 무료 트루타입 글꼴 세트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-267">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="bf944-268">개발자는 원하는 대로 트루타입 글꼴을 더 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-268">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="bf944-269">Azure RTOS GUIX 글꼴 형식은 8bpp 앤티앨리어싱, 4bpp 앤티앨리어싱 및 1bpp 단색 글꼴을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-269">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="bf944-270">리소스가 제한된 대부분의 애플리케이션의 경우 Azure RTOS GUIX는 GUIX Studio 데스크톱 도구를 사용하여 트루타입 글꼴을 압축된 비트맵 형식으로 미리 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-270">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="bf944-271">사용자 지정 JPG 및 PNG 디코더 구현</span><span class="sxs-lookup"><span data-stu-id="bf944-271">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="bf944-272">사용자 지정 JPG 및 PNG 디코더 구현 JPG 및 PNG 파일 디코더 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-272">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="bf944-273">이 구현은 Azure RTOS GUIX 호환 pixelmap 형식 이미지의 색 공간 변환, 디더링 및 런타임 생성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-273">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="bf944-274">광범위한 디스플레이 및 터치 스크린 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-274">Extensive display and touchscreen support</span></span>

<span data-ttu-id="bf944-275">Azure RTOS GUIX는 1bpp 단색, 8bpp 팔레트, 8bpp 3:3:2 형식,</span><span class="sxs-lookup"><span data-stu-id="bf944-275">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="bf944-276">16bpp 565 rgb 형식, 16bpp 4:4:4:4 형식, 32bpp x:r:g:b 형식, 32bpp a:r:g:b 형식을 포함한 거의 모든 색상 형식에 대한 일반 디스플레이 드라이버를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-276">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="bf944-277">또한 Azure RTOS GUIX는 가장 많이 사용되는 여러 LCD 컨트롤러 및 하드웨어 가속기(ST ChromeArt, Renesas Synergy 등)와 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-277">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="bf944-278">Azure RTOS GUIX는 터치 스크린(제스처 지원 포함), 펜 및 가상 키보드 입력 디바이스를 완벽하게 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-278">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="bf944-279">Azure RTOS GUIX Studio 데스크톱 WYSIWYG 도구</span><span class="sxs-lookup"><span data-stu-id="bf944-279">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="bf944-280">Azure RTOS GUIX Studio는 사용자가 GUI 화면을 만드는 데 사용되는 그래픽 요소를 끌어서 놓을 수 있는 완전한 WYSIWYG 화면 디자인 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-280">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="bf944-281">Azure RTOS GUIX Studio는 대상에서 컴파일되고 실행할 준비가 된 Azure RTOS GUIX 라이브러리와 호환되는 C 코드를 자동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-281">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="bf944-282">개발자는 통합된 Azure RTOS GUIX Studio 글꼴 생성 도구를 사용하여 애플리케이션 내에서 사용할 미리 렌더링된 글꼴을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-282">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="bf944-283">글꼴은 단색 또는 앤티앨리어싱 형식으로 생성될 수 있으며 대상의 공간을 절약하도록 최적화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-283">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="bf944-284">글꼴에는 다국어 애플리케이션의 유니코드 문자를 비롯한 모든 문자 세트가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-284">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="bf944-285">Azure RTOS GUIX Studio는 대상 시스템에서 사용할 수 있도록 압축된 Azure RTOS GUIX Pixelmap으로 변환하여 PNG 또는 JPG 파일에서 그래픽을 쉽게 가져올 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-285">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="bf944-286">많은 Azure RTOS GUIX 위젯 형식은 사용자 지정 모양과 느낌을 위해 사용자 그래픽을 통합하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-286">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="bf944-287">또한 Azure RTOS GUIX Studio를 사용하면 Azure RTOS GUIX 위젯에서 사용하는 기본 색상 및 그리기 스타일을 사용자 지정할 수 있으므로 개발자가 Azure RTOS GUIX의 모양을 매우 쉽게 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-287">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="bf944-288">애플리케이션 문자열의 생성 및 유지 관리는 Azure RTOS GUIX Studio의 또 다른 기본 제공 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-288">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="bf944-289">이를 통해 개발자는 개발에 하나의 언어를 사용하여 애플리케이션을 디자인하고 제품 출시 후 추가 언어에 대한 지원을 빠르고 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-289">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="bf944-290">Azure RTOS GUIX Studio 환경 내의 PC 데스크톱에서 완전한 Azure RTOS GUIX 애플리케이션을 실행할 수 있으므로 GUI 개념의 빠르고 쉬운 생성 및 데모, 화면 흐름 테스트, 화면 전환 및 애니메이션 관찰이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-290">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="bf944-291">완료 시 컴파일하고 Azure RTOS GUIX 및 Azure RTOS ThreadX 라이브러리와 연결할 준비가 되었으며 대상에서 사용할 수 있는 C 데이터 구조로 디자인을 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-291">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="bf944-292">Azure RTOS GUIX 및 Azure RTOS GUIX Studio는 여러 리소스 테마를 지원하므로 런타임에 애플리케이션의 스킨을 쉽게 다시 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-292">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="bf944-293">하나의 단순한 API를 사용하여 글꼴, 색 및 pixelmap을 런타임에 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-293">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="bf944-294">GUIX Studio에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="bf944-294">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="bf944-295">전체 Win32 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="bf944-295">Complete Win32 simulation</span></span>

<span data-ttu-id="bf944-296">Azure RTOS GUIX는 대상 보드에서 실행되는 것과 똑같은 그리기 라이브러리를 사용하여 Windows PC에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-296">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="bf944-297">Azure RTOS GUIX를 사용하면 PC에서 GUI 애플리케이션을 빌드하고 실행할 수 있으며 디버깅, 신속한 프로토타입 생성, 데모 및 WYSIWYG 대상 작업을 위해 대상에서 동일한 애플리케이션 코드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-297">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="bf944-298">고급 기술</span><span class="sxs-lookup"><span data-stu-id="bf944-298">Advanced technology</span></span>

* <span data-ttu-id="bf944-299">Azure RTOS GUIX의 고급 기술은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf944-299">Azure RTOS GUIX's advanced technology incorporates:</span></span>
* <span data-ttu-id="bf944-300">알파 혼합</span><span class="sxs-lookup"><span data-stu-id="bf944-300">Alpha blending</span></span>
* <span data-ttu-id="bf944-301">앤티앨리어싱</span><span class="sxs-lookup"><span data-stu-id="bf944-301">Anti-Aliasing</span></span>
* <span data-ttu-id="bf944-302">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="bf944-302">Automatic scaling</span></span>
* <span data-ttu-id="bf944-303">비트맵 압축</span><span class="sxs-lookup"><span data-stu-id="bf944-303">Bitmap compression</span></span>
* <span data-ttu-id="bf944-304">캔버스 혼합</span><span class="sxs-lookup"><span data-stu-id="bf944-304">Canvas blending</span></span>
* <span data-ttu-id="bf944-305">사용자 지정 위젯 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-305">Custom widget support</span></span>
* <span data-ttu-id="bf944-306">지연된 그리기 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-306">Deferred drawing support</span></span>
* <span data-ttu-id="bf944-307">디더링 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-307">Dithering support</span></span>
* <span data-ttu-id="bf944-308">Endian 중립 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="bf944-308">Endian neutral programming</span></span>
* <span data-ttu-id="bf944-309">하드웨어 가속기 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-309">Hardware accelerator support</span></span>
* <span data-ttu-id="bf944-310">다국어 지원 및 UTF-8 인코딩</span><span class="sxs-lookup"><span data-stu-id="bf944-310">Multilingual support and UTF-8 encoding</span></span>
* <span data-ttu-id="bf944-311">다중 디스플레이 및 캔버스 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-311">Multiple display and canvas support</span></span>
* <span data-ttu-id="bf944-312">최적화된 클리핑, 그리기 및 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="bf944-312">Optimized clipping, drawing, and event handling</span></span>
* <span data-ttu-id="bf944-313">런타임 JPEG 및 PNG 디코더</span><span class="sxs-lookup"><span data-stu-id="bf944-313">Runtime JPEG and PNG decoder</span></span>
* <span data-ttu-id="bf944-314">스킨 적용 및 테마</span><span class="sxs-lookup"><span data-stu-id="bf944-314">Skinning and Themes</span></span>
* <span data-ttu-id="bf944-315">알파 그래픽 형식으로 단색부터 32비트 트루 컬러까지 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-315">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>
* <span data-ttu-id="bf944-316">전환, 스프라이트 및 애니메이션 지원</span><span class="sxs-lookup"><span data-stu-id="bf944-316">Transitions, Sprites, and Animation support</span></span>
* <span data-ttu-id="bf944-317">Win32 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="bf944-317">Win32 simulation</span></span>
* <span data-ttu-id="bf944-318">뷰포트 및 Z 순서 유지 관리를 포함한 창 관리</span><span class="sxs-lookup"><span data-stu-id="bf944-318">Window management including Viewports and Z-order maintenance</span></span>
