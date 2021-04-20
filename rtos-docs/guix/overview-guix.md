---
title: Azure RTOS GUIX 및 Azure RTOS GUIX Studio 이해
description: Azure RTOS GUIX는 포함된 시스템 개발자의 요구 사항에 맞게 제작된 전문가용 패키지입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0d0ff37784673f851ab918e20b255d19ddf98b0f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811910"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="a1742-103">Azure RTOS GUIX 및 Azure RTOS GUIX Studio 개요</span><span class="sxs-lookup"><span data-stu-id="a1742-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="a1742-104">Azure GUIX 내장형 GUI는 심층 내장형, 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 Microsoft의 고급 산업용 GUI 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="a1742-105">또한 Microsoft는 개발자가 데스크톱에서 GUI를 디자인하고 대상으로 내보낼 수 있는 Azure RTOS GUIX 내장형 GUI 코드를 생성할 수 있는 Azure RTOS GUIX Studio라는 모든 기능을 갖춘 WYSIWYG 데스크톱 디자인 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="a1742-106">Azure RTOS GUIX는 Azure RTOS ThreadX RTOS와 완전히 통합되며 Azure RTOS ThreadX에서 지원하는 많은 동일한 프로세서에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="a1742-107">또한 Azure RTOS GUIX는 매우 적은 메모리 공간에서 고속 실행과 뛰어난 사용 편의성을 구현하므로, 사용자 인터페이스가 요구되는 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="a1742-108">Azure RTOS GUIX API</span><span class="sxs-lookup"><span data-stu-id="a1742-108">Azure RTOS GUIX API</span></span>

### <a name="intuitive-and-consistent-api"></a><span data-ttu-id="a1742-109">직관적이고 일관성 있는 API</span><span class="sxs-lookup"><span data-stu-id="a1742-109">Intuitive and consistent API</span></span>

* <span data-ttu-id="a1742-110">명사 동사 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="a1742-110">Noun-verb naming convention</span></span>

* <span data-ttu-id="a1742-111">모든 API에는 Azure RTOS GUIX로 쉽게 식별할 수 있도록 *gx_* 가 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-111">All APIs have leading *gx_* to easily identify as Azure RTOS GUIX</span></span>

* <span data-ttu-id="a1742-112">이벤트 구동 프로그래밍 모델(API)</span><span class="sxs-lookup"><span data-stu-id="a1742-112">Event-driven programming model (API)</span></span>

* <span data-ttu-id="a1742-113">필요할 때 직접 캔버스 그리기 완벽 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-113">Full support for direct canvas drawing when needed</span></span>

* <span data-ttu-id="a1742-114">Azure RTOS GUIX Studio 생성 코드와 간단하게 상호 작용</span><span class="sxs-lookup"><span data-stu-id="a1742-114">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>

* <span data-ttu-id="a1742-115">선, 사각형, 다각형 등을 위한 API</span><span class="sxs-lookup"><span data-stu-id="a1742-115">APIs for line, rectangle, polygon, etc.</span></span>

* <span data-ttu-id="a1742-116">원, 호, 원형, 현, 타원 등을 위한 API</span><span class="sxs-lookup"><span data-stu-id="a1742-116">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>

* <span data-ttu-id="a1742-117">텍스트 그리기 및 위치 지정을 위한 API</span><span class="sxs-lookup"><span data-stu-id="a1742-117">APIs for text drawing and positioning</span></span>

* <span data-ttu-id="a1742-118">앤티앨리어싱, 텍스처 채우기 및 단색 채우기</span><span class="sxs-lookup"><span data-stu-id="a1742-118">Anti-aliasing, texture fills, and solid fills</span></span>

* <span data-ttu-id="a1742-119">화면과 위젯 생성 및 수정을 위한 API</span><span class="sxs-lookup"><span data-stu-id="a1742-119">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="a1742-120">Azure RTOS GUIX Studio 생성 파일</span><span class="sxs-lookup"><span data-stu-id="a1742-120">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="a1742-121">자동으로 생성된 ANSI C 원본 파일</span><span class="sxs-lookup"><span data-stu-id="a1742-121">Automatically generated ANSI C source files</span></span>

* <span data-ttu-id="a1742-122">레이아웃 정보에서 애플리케이션 소프트웨어 분리</span><span class="sxs-lookup"><span data-stu-id="a1742-122">Insulates application software from layout details</span></span>

* <span data-ttu-id="a1742-123">UI 디자인에 필요한 글꼴 및 이미지 포함</span><span class="sxs-lookup"><span data-stu-id="a1742-123">Includes fonts and images required by UI design</span></span>

* <span data-ttu-id="a1742-124">애플리케이션 코드로 컴파일 및 생성된 파일</span><span class="sxs-lookup"><span data-stu-id="a1742-124">Generated files compiled with application code</span></span>

* <span data-ttu-id="a1742-125">애플리케이션 논리에 영향을 주지 않고 화면 레이아웃 업데이트 가능</span><span class="sxs-lookup"><span data-stu-id="a1742-125">Screen layout can be updated without affecting application logic</span></span>

* <span data-ttu-id="a1742-126">리소스 ID에서 언어 및 테마 독립성 만들기</span><span class="sxs-lookup"><span data-stu-id="a1742-126">Resource IDs create language and theme independence</span></span>

* <span data-ttu-id="a1742-127">사용자가 제공하는 사용자 지정 그리기 및 이벤트 처리 함수</span><span class="sxs-lookup"><span data-stu-id="a1742-127">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="a1742-128">위젯 라이브러리</span><span class="sxs-lookup"><span data-stu-id="a1742-128">Widget library</span></span>

* <span data-ttu-id="a1742-129">사전 정의되었지만 사용자 정의 가능한 공통 인터페이스 요소 세트</span><span class="sxs-lookup"><span data-stu-id="a1742-129">Pre-defined but customizable set of common interface elements</span></span>

* <span data-ttu-id="a1742-130">매우 작고 간단하고 효율적</span><span class="sxs-lookup"><span data-stu-id="a1742-130">Extremely small, compact, and efficient</span></span>

* <span data-ttu-id="a1742-131">라이브러리에 단추, 계기, 목록, 창, 스크롤, 슬라이더, 진행률 표시줄, 프롬프트 등이 포함됨</span><span class="sxs-lookup"><span data-stu-id="a1742-131">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>

* <span data-ttu-id="a1742-132">완전히 사용자 지정 가능한 그리기 및 모양</span><span class="sxs-lookup"><span data-stu-id="a1742-132">Fully customizable drawing and appearance</span></span>

* <span data-ttu-id="a1742-133">완전히 사용자 지정 가능한 작업 및 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="a1742-133">Fully customizable operation and event handling</span></span>

* <span data-ttu-id="a1742-134">사용된 위젯만 애플리케이션 소프트웨어와 연결됨</span><span class="sxs-lookup"><span data-stu-id="a1742-134">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="a1742-135">수학 및 유틸리티</span><span class="sxs-lookup"><span data-stu-id="a1742-135">Math and utilities</span></span>

* <span data-ttu-id="a1742-136">사인, 코사인, 아크사인, 아크코사인, 탄젠트, 제곱근에 대한 함수</span><span class="sxs-lookup"><span data-stu-id="a1742-136">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>

* <span data-ttu-id="a1742-137">화면 영역 조작을 위한 함수</span><span class="sxs-lookup"><span data-stu-id="a1742-137">Functions for manipulating screen regions</span></span>

* <span data-ttu-id="a1742-138">시스템 구성 및 시작</span><span class="sxs-lookup"><span data-stu-id="a1742-138">System configuration and startup</span></span>

* <span data-ttu-id="a1742-139">메모리 풀 정의(옵션)</span><span class="sxs-lookup"><span data-stu-id="a1742-139">Memory pool definition (optional)</span></span>

* <span data-ttu-id="a1742-140">타이머 관리</span><span class="sxs-lookup"><span data-stu-id="a1742-140">Timer Management</span></span>

* <span data-ttu-id="a1742-141">애니메이션 관리</span><span class="sxs-lookup"><span data-stu-id="a1742-141">Animation Management</span></span>

* <span data-ttu-id="a1742-142">더티 목록 유지 관리</span><span class="sxs-lookup"><span data-stu-id="a1742-142">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="a1742-143">이미지 처리</span><span class="sxs-lookup"><span data-stu-id="a1742-143">Image processing</span></span>

* <span data-ttu-id="a1742-144">jpeg 및 png 이미지의 런타임 디코딩을 위한 함수</span><span class="sxs-lookup"><span data-stu-id="a1742-144">Functions for runtime decode of jpeg and png images</span></span>

* <span data-ttu-id="a1742-145">디더링 및 색 공간 변환 적용</span><span class="sxs-lookup"><span data-stu-id="a1742-145">Apply dithering and color space conversion</span></span>

* <span data-ttu-id="a1742-146">이미지 회전</span><span class="sxs-lookup"><span data-stu-id="a1742-146">Image rotation</span></span>

* <span data-ttu-id="a1742-147">이미지 크기 조정</span><span class="sxs-lookup"><span data-stu-id="a1742-147">Image scaling</span></span>

* <span data-ttu-id="a1742-148">이미지 혼합</span><span class="sxs-lookup"><span data-stu-id="a1742-148">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="a1742-149">이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="a1742-149">Event processing</span></span>

* <span data-ttu-id="a1742-150">유휴 상태일 때 자동으로 Azure RTOS GUIX 스레드 일시 중단</span><span class="sxs-lookup"><span data-stu-id="a1742-150">Automatically suspends Azure RTOS GUIX thread when idle</span></span>

* <span data-ttu-id="a1742-151">UI 디자인에 널리 사용되는 이벤트 기반 프로그래밍 모델</span><span class="sxs-lookup"><span data-stu-id="a1742-151">Event-driven programming model popular in UI design</span></span>

* <span data-ttu-id="a1742-152">Azure RTOS GUIX 그리기 스레드에서 입력 드라이버 분리</span><span class="sxs-lookup"><span data-stu-id="a1742-152">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>

* <span data-ttu-id="a1742-153">이벤트를 보내고 받기 위한 함수</span><span class="sxs-lookup"><span data-stu-id="a1742-153">Functions for sending and receiving events</span></span>

* <span data-ttu-id="a1742-154">모든 Azure RTOS GUIX 위젯 형식에 대한 미리 정의된 이벤트 형식</span><span class="sxs-lookup"><span data-stu-id="a1742-154">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>

* <span data-ttu-id="a1742-155">사용자 정의된 사용자 지정 이벤트 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-155">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="a1742-156">캔버스 처리</span><span class="sxs-lookup"><span data-stu-id="a1742-156">Canvas processing</span></span>

* <span data-ttu-id="a1742-157">클리핑 및 Z 순서 유지 관리</span><span class="sxs-lookup"><span data-stu-id="a1742-157">Clipping and Z-Order maintenance</span></span>

* <span data-ttu-id="a1742-158">하드웨어 정보에서 위젯 라이브러리 분리</span><span class="sxs-lookup"><span data-stu-id="a1742-158">Insulates widget library from hardware details</span></span>

* <span data-ttu-id="a1742-159">하드웨어 정보에서 애플리케이션 분리</span><span class="sxs-lookup"><span data-stu-id="a1742-159">Insulates application from hardware details</span></span>

* <span data-ttu-id="a1742-160">더티 영역의 자동 백그라운드 새로 고침</span><span class="sxs-lookup"><span data-stu-id="a1742-160">Automatic background refresh of dirty areas</span></span>

* <span data-ttu-id="a1742-161">계층화 및 혼합이 지원되는 여러 캔버스</span><span class="sxs-lookup"><span data-stu-id="a1742-161">Multiple canvases with layering and blending supported</span></span>

* <span data-ttu-id="a1742-162">애플리케이션 소프트웨어에서 직접 호출 가능</span><span class="sxs-lookup"><span data-stu-id="a1742-162">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="a1742-163">입력 디바이스 드라이버</span><span class="sxs-lookup"><span data-stu-id="a1742-163">Input device driver(s)</span></span>

* <span data-ttu-id="a1742-164">하드웨어 관련 지원, 하드웨어 정보에서 Azure RTOS GUIX 및 애플리케이션 분리</span><span class="sxs-lookup"><span data-stu-id="a1742-164">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>

* <span data-ttu-id="a1742-165">저항 접촉식 터치, 캡 터치 및 키패드 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-165">Resistive Touch, Cap Touch, and keypad supported</span></span>

* <span data-ttu-id="a1742-166">Azure RTOS GUIX 이벤트 큐에 입력 이벤트 전달</span><span class="sxs-lookup"><span data-stu-id="a1742-166">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="a1742-167">디스플레이 드라이버</span><span class="sxs-lookup"><span data-stu-id="a1742-167">Display drivers</span></span>

* <span data-ttu-id="a1742-168">하드웨어 관련 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-168">Hardware-specific support</span></span>

* <span data-ttu-id="a1742-169">모든 색 농도 및 형식에 대해 제공되는 일반 드라이버</span><span class="sxs-lookup"><span data-stu-id="a1742-169">Generic drivers provided for all color depth and formats</span></span>

* <span data-ttu-id="a1742-170">사용 가능한 그래픽 가속기를 활용하도록 사용자 지정됨</span><span class="sxs-lookup"><span data-stu-id="a1742-170">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="a1742-171">대상 하드웨어</span><span class="sxs-lookup"><span data-stu-id="a1742-171">Target hardware</span></span>

* <span data-ttu-id="a1742-172">그래픽 출력을 지원하는 거의 모든 하드웨어가 GUIX와 호환</span><span class="sxs-lookup"><span data-stu-id="a1742-172">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>

* <span data-ttu-id="a1742-173">여러 물리적 디스플레이 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-173">Multiple physical displays supported</span></span>

* <span data-ttu-id="a1742-174">최소 RAM 및 플래시 요구 사항</span><span class="sxs-lookup"><span data-stu-id="a1742-174">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="a1742-175">세련된 사용자 인터페이스 만들기</span><span class="sxs-lookup"><span data-stu-id="a1742-175">Create Elegant User Interfaces</span></span>

<span data-ttu-id="a1742-176">Azure RTOS GUIX 및 Azure RTOS GUIX Studio는 세련된 사용자 인터페이스를 만드는 데 필요한 모든 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-176">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="a1742-177">표준 Azure RTOS GUIX 패키지에는 의료 기기 참조, 스마트 시계 참조, 가정 자동화 참조, 산업 제어 참조, 자동차 참조, 다양한 스프라이트 및 애니메이션 예제를 비롯한 다양한 샘플 사용자 인터페이스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-177">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="a1742-178">아래에 표시된 참조 예제를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="a1742-178">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="a1742-179">가정 자동화</span><span class="sxs-lookup"><span data-stu-id="a1742-179">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="a1742-180">의료</span><span class="sxs-lookup"><span data-stu-id="a1742-180">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="a1742-181">소비자</span><span class="sxs-lookup"><span data-stu-id="a1742-181">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="a1742-182">백색 가전</span><span class="sxs-lookup"><span data-stu-id="a1742-182">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="a1742-183">자동차</span><span class="sxs-lookup"><span data-stu-id="a1742-183">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="a1742-184">공업 제품</span><span class="sxs-lookup"><span data-stu-id="a1742-184">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="a1742-185">Azure RTOS GUIX 참조마다 참조 디자인의 모든 그래픽 요소를 정의하는 해당 Azure RTOS GUIX Studio 프로젝트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-185">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="a1742-186">참조 디자인을 변경하는 것은 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-186">Changing a reference design is easy.</span></span> <span data-ttu-id="a1742-187">해당하는 Azure RTOS GUIX 프로젝트를 열고 원하는 대로 변경한 후 프로젝트를 저장하고 *프로젝트* 를 선택하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-187">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="a1742-188">모든 출력 파일을 생성하여 Azure RTOS GUIX에 대한 C 코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-188">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="a1742-189">그런 다음, 대상 애플리케이션을 다시 빌드하고 실행하여 수정된 참조 디자인을 관찰합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-189">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="small-footprint"></a><span data-ttu-id="a1742-190">작은 메모리 공간</span><span class="sxs-lookup"><span data-stu-id="a1742-190">Small-footprint</span></span>

<span data-ttu-id="a1742-191">Azure RTOS GUIX는 캔버스에 필요한 메모리를 제외하고 기본 지원을 위한 13.2KB의 FLASH 및 4KB RAM의 매우 작은 최소 메모리 공간을 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-191">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="a1742-192">내부 GRAM 및 자체 새로 고침 기술이 있는 디스플레이의 경우 캔버스 메모리가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-192">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="a1742-193">그러나 그리기 성능 향상이나 디스플레이에 로컬인 GRAM을 활용하지 않는 디스플레이 구성을 위해 캔버스 메모리 영역이 애플리케이션에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-193">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="a1742-194">캔버스 메모리 요구 사항은 캔버스 크기 및 색 농도의 함수이며 다음 수식으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-194">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="a1742-195"><i>캔버스 RAM(바이트) = (x \* y \* (bpp/8))</i></span><span class="sxs-lookup"><span data-stu-id="a1742-195"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="a1742-196">여기서 "x"와 "y"는 캔버스(디스플레이)의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-196">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="a1742-197">또한 대부분의 애플리케이션은 핵심 Azure RTOS GUIX 라이브러리 스토리지 요구 사항에 포함되지 않은 그래픽 리소스를 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-197">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="a1742-198">이러한 리소스에는 글꼴, 그래픽 아이콘(pixelmap) 및 정적 문자열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-198">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="a1742-199">이 데이터는 const 메모리 섹션(예: FLASH)에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-199">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="a1742-200">이 메모리 영역의 크기는 사용되는 고유 글꼴의 수와 크기, 사용되는 그래픽 아이콘의 수와 크기, 출력 색 형식, 각 리소스가 압축된 데이터를 사용하는지 여부를 포함한 여러 요인에 따라 달라집니다. Azure RTOS GUIX는 글꼴 데이터와 pixelmap 데이터 모두의 RLE 압축을 지원하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-200">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="a1742-201">각 리소스에 대한 스토리지 요구 사항은 Azure RTOS GUIX Studio 애플리케이션 내에 표시되므로 사용자는 애플리케이션 리소스에서 사용하는 플래시 메모리의 양을 추적하고 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-201">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="a1742-202">Azure RTOS ThreadX와 같이 Azure RTOS GUIX의 크기는 애플리케이션에서 실제로 사용하는 서비스에 따라 자동으로 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-202">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="a1742-203">이렇게 하면 사실상 복잡한 구성 및 빌드 매개 변수가 제거되어 개발자가 더 쉽게 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-203">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

### <a name="fast-execution"></a><span data-ttu-id="a1742-204">고속 실행</span><span class="sxs-lookup"><span data-stu-id="a1742-204">Fast execution</span></span>

<span data-ttu-id="a1742-205">Azure RTOS GUIX는 C로만 작성되었으며 속도를 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-205">Azure RTOS GUIX is written exclusively in C and is designed for speed.</span></span> <span data-ttu-id="a1742-206">Azure RTOS GUIX에는 최소한의 내부 함수 호출 계층이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-206">Azure RTOS GUIX has minimal internal function call layering.</span></span>

<span data-ttu-id="a1742-207">또한 Azure RTOS GUIX는 최적화된 클리핑, 그리기 및 이벤트 처리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-207">In addition, Azure RTOS GUIX provides optimized clipping, drawing, and event handling.</span></span> <span data-ttu-id="a1742-208">이런 특징과 일반 성능 중심 디자인 철학으로 Azure RTOS GUIX에서 가능한 가장 빠른 성능을 구현하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-208">All of this and a general performance-oriented design philosophy help Azure RTOS GUIX achieve the fastest possible performance.</span></span>

### <a name="pre-certified--by-tuv-to-many-safety-standards"></a><span data-ttu-id="a1742-209">TUV를 비롯한 여러 안전 표준의 사전 인증</span><span class="sxs-lookup"><span data-stu-id="a1742-209">Pre-certified  by TUV to many safety standards</span></span>

<span data-ttu-id="a1742-210">Azure RTOS GUIX는 안전이 매우 중요한 시스템에서의 사용을 위해 IEC-61508 SIL 4, IEC-62304 SW 안전 등급 C, ISO 26262 ASIL D 및 EN 50128에 따라 SGS-TUV Saar 인증을 받았습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-210">Azure RTOS GUIX has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="a1742-211">이 인증은 "전기, 전자 및 프로그램 가능한 전자 안전 관련 시스템의 기능적 안전"에 대한 최고 수준의 IEC-61508, IEC-62304, ISO 26262 및 EN 50128의 안전 무결성 등급에 따라, Azure RTOS GUIX를 보안 관련 소프트웨어의 개발에 사용할 수 있음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-211">The certification confirms that Azure RTOS GUIX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="a1742-212">독일 SGS-Group 및 TUV Saarland의 공동 벤처인 SGS-TUV Saar는 세계적으로 안전 관련 시스템용 포함 소프트웨어를 테스트, 감사, 확인 및 검증하는 최고 권위의 독립 기업으로 자리했습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-212">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="a1742-213">산업 보안 표준 IEC 61508과 거기에서 파생된 모든 표준(IEC-62304, ISO 26262 및 EN 50128 포함)은 전기, 전자 및 프로그래밍 가능한 전자 안전 관련 의료 장비, 공정 제어 시스템, 산업용 기계, 자동차, 철도 제어 시스템의 기능 안전을 보장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-213">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

<img alt="SGS-TUV Saar" class="img-responsive" src="https://rtos.com/wp-content/uploads/2017/10/partener-logo-sgs-tuv-saar-2.png"/>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="a1742-214">간단하고 손쉬운 사용</span><span class="sxs-lookup"><span data-stu-id="a1742-214">Simple, easy-to-use</span></span>

<span data-ttu-id="a1742-215">Azure RTOS GUIX는 사용이 매우 간단합니다. Azure RTOS GUIX Studio를 사용하면 개발자가 데스크톱에서 시각적으로 디자인하고 실제 대상에서 실행되는 C 코드를 생성할 수 있으므로 Azure RTOS GUIX를 훨씬 더 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-215">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="a1742-216">그러면 애플리케이션에서 자체 사용자 지정 이벤트 처리 및 그리기 기능을 추가하여 GUI를 완성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-216">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="a1742-217">Azure RTOS GUIX API를 사용하는 것은 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-217">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="a1742-218">Azure RTOS GUIX API는 직관적이고 매우 기능적입니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-218">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="a1742-219">API 이름은 다른 파일 시스템 제품에서 흔히 볼 수 있는 매우 축약된 이름 및/또는 “알파벳 약자”가 아니라 실제 단어로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-219">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="a1742-220">모든 Azure RTOS GUIX API에는 선행 *gx_* 가 있으며 명사-동사 명명 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-220">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="a1742-221">또한 API 전체에 걸쳐 기능적 일관성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-221">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="a1742-222">예를 들어 위젯 제어 블록을 초기화하는 모든 API의 이름은 &lt; widget_type&gt;_create이고 각 위젯 형식에 대한 만들기 함수 매개 변수는 항상 동일한 순서로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-222">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="a1742-223">포괄적인 기본 제공 위젯 세트</span><span class="sxs-lookup"><span data-stu-id="a1742-223">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="a1742-224">Azure RTOS GUIX는 다음과 같은 다양한 기본 제공 위젯 세트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-224">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>

* <span data-ttu-id="a1742-225">아코디언 메뉴</span><span class="sxs-lookup"><span data-stu-id="a1742-225">Accordion Menu</span></span>

* <span data-ttu-id="a1742-226">단추</span><span class="sxs-lookup"><span data-stu-id="a1742-226">Button</span></span>

* <span data-ttu-id="a1742-227">확인란</span><span class="sxs-lookup"><span data-stu-id="a1742-227">Checkbox</span></span>

* <span data-ttu-id="a1742-228">순환 계기</span><span class="sxs-lookup"><span data-stu-id="a1742-228">Circular Gauge</span></span>

* <span data-ttu-id="a1742-229">드롭다운 목록</span><span class="sxs-lookup"><span data-stu-id="a1742-229">Drop Down List</span></span>

* <span data-ttu-id="a1742-230">가로 목록</span><span class="sxs-lookup"><span data-stu-id="a1742-230">Horizontal List</span></span>

* <span data-ttu-id="a1742-231">가로 스크롤 막대 창</span><span class="sxs-lookup"><span data-stu-id="a1742-231">Horizontal Scrollbar Window</span></span>

* <span data-ttu-id="a1742-232">아이콘</span><span class="sxs-lookup"><span data-stu-id="a1742-232">Icon</span></span>

* <span data-ttu-id="a1742-233">아이콘 단추</span><span class="sxs-lookup"><span data-stu-id="a1742-233">Icon Button</span></span>

* <span data-ttu-id="a1742-234">꺾은선형 차트</span><span class="sxs-lookup"><span data-stu-id="a1742-234">Line Chart</span></span>

* <span data-ttu-id="a1742-235">메뉴</span><span class="sxs-lookup"><span data-stu-id="a1742-235">Menu</span></span>

* <span data-ttu-id="a1742-236">여러 줄 텍스트 단추</span><span class="sxs-lookup"><span data-stu-id="a1742-236">Multi Line Text Button</span></span>

* <span data-ttu-id="a1742-237">여러 줄 텍스트 입력</span><span class="sxs-lookup"><span data-stu-id="a1742-237">Multi Line Text Input</span></span>

* <span data-ttu-id="a1742-238">여러 줄 텍스트 보기</span><span class="sxs-lookup"><span data-stu-id="a1742-238">Multi Line Text View</span></span>

* <span data-ttu-id="a1742-239">숫자 Pixelmap 프롬프트</span><span class="sxs-lookup"><span data-stu-id="a1742-239">Numeric Pixelmap Prompt</span></span>

* <span data-ttu-id="a1742-240">숫자 프롬프트</span><span class="sxs-lookup"><span data-stu-id="a1742-240">Numeric Prompt</span></span>

* <span data-ttu-id="a1742-241">숫자 스크롤 휠</span><span class="sxs-lookup"><span data-stu-id="a1742-241">Numeric Scroll Wheel</span></span>

* <span data-ttu-id="a1742-242">Pixelmap 단추</span><span class="sxs-lookup"><span data-stu-id="a1742-242">Pixelmap Button</span></span>

* <span data-ttu-id="a1742-243">Pixelmap 프롬프트</span><span class="sxs-lookup"><span data-stu-id="a1742-243">Pixelmap Prompt</span></span>

* <span data-ttu-id="a1742-244">Pixelmap 슬라이더</span><span class="sxs-lookup"><span data-stu-id="a1742-244">Pixelmap Slider</span></span>

* <span data-ttu-id="a1742-245">Pixelmap 스프라이트</span><span class="sxs-lookup"><span data-stu-id="a1742-245">Pixelmap Sprite</span></span>

* <span data-ttu-id="a1742-246">Progress Bar</span><span class="sxs-lookup"><span data-stu-id="a1742-246">Progress Bar</span></span>

* <span data-ttu-id="a1742-247">prompt</span><span class="sxs-lookup"><span data-stu-id="a1742-247">Prompt</span></span>

* <span data-ttu-id="a1742-248">방사형 진행률 표시줄</span><span class="sxs-lookup"><span data-stu-id="a1742-248">Radial Progress Bar</span></span>

* <span data-ttu-id="a1742-249">Radio Button</span><span class="sxs-lookup"><span data-stu-id="a1742-249">Radio Button</span></span>

* <span data-ttu-id="a1742-250">스크롤 휠</span><span class="sxs-lookup"><span data-stu-id="a1742-250">Scroll Wheel</span></span>

* <span data-ttu-id="a1742-251">한 줄 텍스트 입력</span><span class="sxs-lookup"><span data-stu-id="a1742-251">Single Line Text Input</span></span>

* <span data-ttu-id="a1742-252">슬라이더</span><span class="sxs-lookup"><span data-stu-id="a1742-252">Slider</span></span>

* <span data-ttu-id="a1742-253">문자열 스크롤 휠</span><span class="sxs-lookup"><span data-stu-id="a1742-253">String Scroll Wheel</span></span>

* <span data-ttu-id="a1742-254">텍스트 단추</span><span class="sxs-lookup"><span data-stu-id="a1742-254">Text Button</span></span>

* <span data-ttu-id="a1742-255">트리 뷰</span><span class="sxs-lookup"><span data-stu-id="a1742-255">Tree View</span></span>

* <span data-ttu-id="a1742-256">세로 목록</span><span class="sxs-lookup"><span data-stu-id="a1742-256">Vertical List</span></span>

* <span data-ttu-id="a1742-257">세로 스크롤 막대</span><span class="sxs-lookup"><span data-stu-id="a1742-257">Vertical Scrollbar</span></span>

<span data-ttu-id="a1742-258">애플리케이션에서 자체 고객 위젯도 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-258">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="a1742-259">완벽한 하위 수준 그리기 API</span><span class="sxs-lookup"><span data-stu-id="a1742-259">Complete low-level drawing API</span></span>

<span data-ttu-id="a1742-260">Azure RTOS GUIX는 애플리케이션에서 복잡한 그래픽 도형을 렌더링할 수 있도록 하는 강력한 캔버스 그리기 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-260">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="a1742-261">모든 기능은 높은 색상 농도 대상에서 앤티앨리어싱을 지원하며 단색 및 pixelmap 패턴 채우기를 포함하여 모든 도형의 윤곽선을 그리고 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-261">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="a1742-262">모든 그리기 기본 도형은 16bpp 이상의 색 농도로 실행 시 브러시 알파를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-262">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="a1742-263">그리기 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-263">Drawing functions include:</span></span>

* <span data-ttu-id="a1742-264">원호 그리기</span><span class="sxs-lookup"><span data-stu-id="a1742-264">Arc Draw</span></span>

* <span data-ttu-id="a1742-265">원 그리기</span><span class="sxs-lookup"><span data-stu-id="a1742-265">Circle Draw</span></span>

* <span data-ttu-id="a1742-266">선 그리기</span><span class="sxs-lookup"><span data-stu-id="a1742-266">Line Draw</span></span>

* <span data-ttu-id="a1742-267">원형 그리기</span><span class="sxs-lookup"><span data-stu-id="a1742-267">Pie Draw</span></span>

* <span data-ttu-id="a1742-268">Pixelmap 혼합</span><span class="sxs-lookup"><span data-stu-id="a1742-268">Pixelmap Blend</span></span>

* <span data-ttu-id="a1742-269">Pixelmap 타일</span><span class="sxs-lookup"><span data-stu-id="a1742-269">Pixelmap Tile</span></span>

* <span data-ttu-id="a1742-270">다각형 그리기</span><span class="sxs-lookup"><span data-stu-id="a1742-270">Polygon Draw</span></span>

* <span data-ttu-id="a1742-271">텍스트 그리기</span><span class="sxs-lookup"><span data-stu-id="a1742-271">Text Draw</span></span>

* <span data-ttu-id="a1742-272">현 그리기</span><span class="sxs-lookup"><span data-stu-id="a1742-272">Chord Draw</span></span>

* <span data-ttu-id="a1742-273">타원 그리기</span><span class="sxs-lookup"><span data-stu-id="a1742-273">Ellipse Draw</span></span>

* <span data-ttu-id="a1742-274">픽셀 그리기</span><span class="sxs-lookup"><span data-stu-id="a1742-274">Pixel Draw</span></span>

* <span data-ttu-id="a1742-275">Pixelmap 그리기</span><span class="sxs-lookup"><span data-stu-id="a1742-275">Pixelmap Draw</span></span>

* <span data-ttu-id="a1742-276">Pixelmap 회전</span><span class="sxs-lookup"><span data-stu-id="a1742-276">Pixelmap Rotate</span></span>

* <span data-ttu-id="a1742-277">사각형 그리기</span><span class="sxs-lookup"><span data-stu-id="a1742-277">Rectangle Draw</span></span>

* <span data-ttu-id="a1742-278">텍스트 혼합</span><span class="sxs-lookup"><span data-stu-id="a1742-278">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="a1742-279">기본 무료 글꼴 및 손쉬운 추가</span><span class="sxs-lookup"><span data-stu-id="a1742-279">Default free fonts and easy to add more</span></span>

<span data-ttu-id="a1742-280">Azure RTOS GUIX는 무료 트루타입 글꼴 세트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-280">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="a1742-281">개발자는 원하는 대로 트루타입 글꼴을 더 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-281">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="a1742-282">Azure RTOS GUIX 글꼴 형식은 8bpp 앤티앨리어싱, 4bpp 앤티앨리어싱 및 1bpp 단색 글꼴을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-282">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="a1742-283">리소스가 제한된 대부분의 애플리케이션의 경우 Azure RTOS GUIX는 GUIX Studio 데스크톱 도구를 사용하여 트루타입 글꼴을 압축된 비트맵 형식으로 미리 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-283">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="a1742-284">사용자 지정 JPG 및 PNG 디코더 구현</span><span class="sxs-lookup"><span data-stu-id="a1742-284">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="a1742-285">사용자 지정 JPG 및 PNG 디코더 구현 JPG 및 PNG 파일 디코더 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-285">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="a1742-286">이 구현은 Azure RTOS GUIX 호환 pixelmap 형식 이미지의 색 공간 변환, 디더링 및 런타임 생성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-286">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="a1742-287">광범위한 디스플레이 및 터치 스크린 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-287">Extensive display and touchscreen support</span></span>

<span data-ttu-id="a1742-288">Azure RTOS GUIX는 1bpp 단색, 8bpp 팔레트, 8bpp 3:3:2 형식,</span><span class="sxs-lookup"><span data-stu-id="a1742-288">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="a1742-289">16bpp 565 rgb 형식, 16bpp 4:4:4:4 형식, 32bpp x:r:g:b 형식, 32bpp a:r:g:b 형식을 포함한 거의 모든 색상 형식에 대한 일반 디스플레이 드라이버를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-289">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="a1742-290">또한 Azure RTOS GUIX는 가장 많이 사용되는 여러 LCD 컨트롤러 및 하드웨어 가속기(ST ChromeArt, Renesas Synergy 등)와 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-290">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="a1742-291">Azure RTOS GUIX는 터치 스크린(제스처 지원 포함), 펜 및 가상 키보드 입력 디바이스를 완벽하게 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-291">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="a1742-292">Azure RTOS GUIX Studio 데스크톱 WYSIWYG 도구</span><span class="sxs-lookup"><span data-stu-id="a1742-292">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="a1742-293">Azure RTOS GUIX Studio는 사용자가 GUI 화면을 만드는 데 사용되는 그래픽 요소를 끌어서 놓을 수 있는 완전한 WYSIWYG 화면 디자인 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-293">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="a1742-294">Azure RTOS GUIX Studio는 대상에서 컴파일되고 실행할 준비가 된 Azure RTOS GUIX 라이브러리와 호환되는 C 코드를 자동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-294">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="a1742-295">개발자는 통합된 Azure RTOS GUIX Studio 글꼴 생성 도구를 사용하여 애플리케이션 내에서 사용할 미리 렌더링된 글꼴을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-295">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="a1742-296">글꼴은 단색 또는 앤티앨리어싱 형식으로 생성될 수 있으며 대상의 공간을 절약하도록 최적화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-296">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="a1742-297">글꼴에는 다국어 애플리케이션의 유니코드 문자를 비롯한 모든 문자 세트가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-297">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="a1742-298">Azure RTOS GUIX Studio는 대상 시스템에서 사용할 수 있도록 압축된 Azure RTOS GUIX Pixelmap으로 변환하여 PNG 또는 JPG 파일에서 그래픽을 쉽게 가져올 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-298">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="a1742-299">많은 Azure RTOS GUIX 위젯 형식은 사용자 지정 모양과 느낌을 위해 사용자 그래픽을 통합하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-299">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="a1742-300">또한 Azure RTOS GUIX Studio를 사용하면 Azure RTOS GUIX 위젯에서 사용하는 기본 색상 및 그리기 스타일을 사용자 지정할 수 있으므로 개발자가 Azure RTOS GUIX의 모양을 매우 쉽게 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-300">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="a1742-301">애플리케이션 문자열의 생성 및 유지 관리는 Azure RTOS GUIX Studio의 또 다른 기본 제공 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-301">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="a1742-302">이를 통해 개발자는 개발에 하나의 언어를 사용하여 애플리케이션을 디자인하고 제품 출시 후 추가 언어에 대한 지원을 빠르고 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-302">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="a1742-303">Azure RTOS GUIX Studio 환경 내의 PC 데스크톱에서 완전한 Azure RTOS GUIX 애플리케이션을 실행할 수 있으므로 GUI 개념의 빠르고 쉬운 생성 및 데모, 화면 흐름 테스트, 화면 전환 및 애니메이션 관찰이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-303">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="a1742-304">완료 시 컴파일하고 Azure RTOS GUIX 및 Azure RTOS ThreadX 라이브러리와 연결할 준비가 되었으며 대상에서 사용할 수 있는 C 데이터 구조로 디자인을 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-304">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="a1742-305">Azure RTOS GUIX 및 Azure RTOS GUIX Studio는 여러 리소스 테마를 지원하므로 런타임에 애플리케이션의 스킨을 쉽게 다시 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-305">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="a1742-306">하나의 단순한 API를 사용하여 글꼴, 색 및 pixelmap을 런타임에 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-306">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="a1742-307">GUIX Studio에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="a1742-307">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="a1742-308">전체 Win32 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="a1742-308">Complete Win32 simulation</span></span>

<span data-ttu-id="a1742-309">Azure RTOS GUIX는 대상 보드에서 실행되는 것과 똑같은 그리기 라이브러리를 사용하여 Windows PC에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-309">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="a1742-310">Azure RTOS GUIX를 사용하면 PC에서 GUI 애플리케이션을 빌드하고 실행할 수 있으며 디버깅, 신속한 프로토타입 생성, 데모 및 WYSIWYG 대상 작업을 위해 대상에서 동일한 애플리케이션 코드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-310">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="a1742-311">고급 기술</span><span class="sxs-lookup"><span data-stu-id="a1742-311">Advanced technology</span></span>

* <span data-ttu-id="a1742-312">Azure RTOS GUIX의 고급 기술은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-312">Azure RTOS GUIX's advanced technology incorporates:</span></span>

* <span data-ttu-id="a1742-313">알파 혼합</span><span class="sxs-lookup"><span data-stu-id="a1742-313">Alpha blending</span></span>

* <span data-ttu-id="a1742-314">앤티앨리어싱</span><span class="sxs-lookup"><span data-stu-id="a1742-314">Anti-Aliasing</span></span>

* <span data-ttu-id="a1742-315">자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="a1742-315">Automatic scaling</span></span>

* <span data-ttu-id="a1742-316">비트맵 압축</span><span class="sxs-lookup"><span data-stu-id="a1742-316">Bitmap compression</span></span>

* <span data-ttu-id="a1742-317">캔버스 혼합</span><span class="sxs-lookup"><span data-stu-id="a1742-317">Canvas blending</span></span>

* <span data-ttu-id="a1742-318">사용자 지정 위젯 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-318">Custom widget support</span></span>

* <span data-ttu-id="a1742-319">지연된 그리기 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-319">Deferred drawing support</span></span>

* <span data-ttu-id="a1742-320">디더링 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-320">Dithering support</span></span>

* <span data-ttu-id="a1742-321">Endian 중립 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="a1742-321">Endian neutral programming</span></span>

* <span data-ttu-id="a1742-322">하드웨어 가속기 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-322">Hardware accelerator support</span></span>

* <span data-ttu-id="a1742-323">다국어 지원 및 UTF-8 인코딩</span><span class="sxs-lookup"><span data-stu-id="a1742-323">Multilingual support and UTF-8 encoding</span></span>

* <span data-ttu-id="a1742-324">다중 디스플레이 및 캔버스 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-324">Multiple display and canvas support</span></span>

* <span data-ttu-id="a1742-325">최적화된 클리핑, 그리기 및 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="a1742-325">Optimized clipping, drawing, and event handling</span></span>

* <span data-ttu-id="a1742-326">런타임 JPEG 및 PNG 디코더</span><span class="sxs-lookup"><span data-stu-id="a1742-326">Runtime JPEG and PNG decoder</span></span>

* <span data-ttu-id="a1742-327">스킨 적용 및 테마</span><span class="sxs-lookup"><span data-stu-id="a1742-327">Skinning and Themes</span></span>

* <span data-ttu-id="a1742-328">알파 그래픽 형식으로 단색부터 32비트 트루 컬러까지 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-328">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>

* <span data-ttu-id="a1742-329">전환, 스프라이트 및 애니메이션 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-329">Transitions, Sprites, and Animation support</span></span>

* <span data-ttu-id="a1742-330">Win32 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="a1742-330">Win32 simulation</span></span>

* <span data-ttu-id="a1742-331">뷰포트 및 Z 순서 유지 관리를 포함한 창 관리</span><span class="sxs-lookup"><span data-stu-id="a1742-331">Window management including Viewports and Z-order maintenance</span></span>

### <a name="fastest-time-to-market"></a><span data-ttu-id="a1742-332">가장 빠른 출시 시간</span><span class="sxs-lookup"><span data-stu-id="a1742-332">Fastest time-to-market</span></span>

<span data-ttu-id="a1742-333">Azure RTOS GUIX는 설치, 학습, 사용, 디버그, 확인, 인증 및 유지 관리가 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-333">Azure RTOS GUIX is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="a1742-334">또한 Azure RTOS GUIX Studio를 사용하면 포함된 GUI 디자인과 구현을 더 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-334">Azure RTOS GUIX Studio also helps making embedded GUI design and implementation easier.</span></span> <span data-ttu-id="a1742-335">이 덕분에 Azure RTOS GUIX는 포함된 IoT 디바이스에 가장 널리 사용되는 GUI 솔루션 중 하나가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-335">As a result, Azure RTOS GUIX is one of the most popular GUI solutions for embedded IoT devices.</span></span> <span data-ttu-id="a1742-336">일관적인 출시 시간 이점은 다음을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-336">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="a1742-337">품질 설명서 – [Azure RTOS GUIX 사용자 가이드](about-guix.md)를 검토하고 직접 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="a1742-337">Quality Documentation – please review our [Azure RTOS GUIX User Guide](about-guix.md) and see for yourself!</span></span>

* <span data-ttu-id="a1742-338">전체 소스 코드 가용성</span><span class="sxs-lookup"><span data-stu-id="a1742-338">Complete Source Code Availability</span></span>

* <span data-ttu-id="a1742-339">사용하기 쉬운 API</span><span class="sxs-lookup"><span data-stu-id="a1742-339">Easy-to-use API</span></span>

* <span data-ttu-id="a1742-340">포괄적인 고급 기능 세트</span><span class="sxs-lookup"><span data-stu-id="a1742-340">Comprehensive and Advanced Feature Set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="a1742-341">하나의 간단한 라이선스</span><span class="sxs-lookup"><span data-stu-id="a1742-341">One Simple License</span></span>

<span data-ttu-id="a1742-342">사전에 사용이 허가된 디바이스에 배포하는 경우에는 소스 코드를 사용 및 테스트하는 데 비용이 들지 않으며 프로덕션 라이선스에 대한 비용도 부과되지 않습니다. 다른 모든 디바이스에는 간단한 연간 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-342">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="a1742-343">최고 품질의 전체 소스 코드</span><span class="sxs-lookup"><span data-stu-id="a1742-343">Full, highest-quality source code</span></span>

<span data-ttu-id="a1742-344">오랜 시간에 걸쳐 Azure RTOS NetX 소스 코드는 품질 및 이해 용이성의 기준을 정립했습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-344">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="a1742-345">또한 파일당 하나의 함수를 포함하는 규칙을 통해 손쉬운 소스 탐색을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-345">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="a1742-346">대부분의 주요 아키텍처 지원</span><span class="sxs-lookup"><span data-stu-id="a1742-346">Supports most popular architectures</span></span>

<span data-ttu-id="a1742-347">Azure RTOS GUIX는 완전한 테스트와 지원을 통해 다음과 같이 대부분의 주요 32/64비트 마이크로프로세서에서 실행되며, 바로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1742-347">Azure RTOS GUIX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="a1742-348">고급 아키텍처:</span><span class="sxs-lookup"><span data-stu-id="a1742-348">Advanced Architectures:</span></span>

<span data-ttu-id="a1742-349">**아날로그 디바이스**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="a1742-349">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="a1742-350">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="a1742-350">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="a1742-351">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="a1742-351">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="a1742-352">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64비트/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="a1742-352">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="a1742-353">**Cadence**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="a1742-353">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="a1742-354">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="a1742-354">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="a1742-355">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="a1742-355">**Cypress**: RISC-V</span></span>

<span data-ttu-id="a1742-356">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="a1742-356">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="a1742-357">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="a1742-357">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="a1742-358">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="a1742-358">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="a1742-359">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="a1742-359">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="a1742-360">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="a1742-360">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="a1742-361">**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="a1742-361">**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="a1742-362">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span><span class="sxs-lookup"><span data-stu-id="a1742-362">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="a1742-363">**Silicon Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="a1742-363">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="a1742-364">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="a1742-364">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="a1742-365">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="a1742-365">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="a1742-366">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="a1742-366">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="a1742-367">**Wave Computing**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="a1742-367">**Wave Computing**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="a1742-368">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="a1742-368">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>
