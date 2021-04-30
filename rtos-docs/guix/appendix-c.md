---
title: 부록 C - GUIX 위젯 스타일
description: GUIX 위젯 스타일에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 83d5c5167739e91b7af8fce6b04213f610984fc6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812096"
---
# <a name="appendix-c---guix-widget-styles"></a><span data-ttu-id="4ce01-103">부록 C - GUIX 위젯 스타일</span><span class="sxs-lookup"><span data-stu-id="4ce01-103">Appendix C - GUIX Widget Styles</span></span>

<span data-ttu-id="4ce01-104">__***일반 스타일(대부분의 위젯 유형에 사용됨):***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-104">__***General Styles (Used with most widget types):***__</span></span>

<span data-ttu-id="4ce01-105">**GX_STYLE_BORDER_NONE**</span><span class="sxs-lookup"><span data-stu-id="4ce01-105">**GX_STYLE_BORDER_NONE**</span></span>
  - <span data-ttu-id="4ce01-106">값: 0x00000000</span><span class="sxs-lookup"><span data-stu-id="4ce01-106">Value: 0x00000000</span></span>
  - <span data-ttu-id="4ce01-107">설명: 테두리 없이 위젯을 그리려면 이 스타일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-107">Description: Use this style to draw a widget with no border.</span></span>

<span data-ttu-id="4ce01-108">**GX_STYLE_BORDER_RAISED**</span><span class="sxs-lookup"><span data-stu-id="4ce01-108">**GX_STYLE_BORDER_RAISED**</span></span>
  - <span data-ttu-id="4ce01-109">값: 0x00000001</span><span class="sxs-lookup"><span data-stu-id="4ce01-109">Value: 0x00000001</span></span>
  - <span data-ttu-id="4ce01-110">설명: 볼록 테두리를 사용하여 위젯을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-110">Description: Draw widget with a raised border.</span></span>

<span data-ttu-id="4ce01-111">**GX_STYLE_BORDER_RECESSED**</span><span class="sxs-lookup"><span data-stu-id="4ce01-111">**GX_STYLE_BORDER_RECESSED**</span></span>
  - <span data-ttu-id="4ce01-112">값: 0x00000002</span><span class="sxs-lookup"><span data-stu-id="4ce01-112">Value: 0x00000002</span></span>
  - <span data-ttu-id="4ce01-113">설명: 오목 테두리를 사용하여 위젯을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-113">Description: Draw widget with a recessed border.</span></span>

<span data-ttu-id="4ce01-114">**GX_STYLE_BORDER_THIN**</span><span class="sxs-lookup"><span data-stu-id="4ce01-114">**GX_STYLE_BORDER_THIN**</span></span>
  - <span data-ttu-id="4ce01-115">값: 0x00000004</span><span class="sxs-lookup"><span data-stu-id="4ce01-115">Value: 0x00000004</span></span>
  - <span data-ttu-id="4ce01-116">설명: 1픽셀 너비의 테두리를 그립니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-116">Description: Draw a one-pixel width border.</span></span>

<span data-ttu-id="4ce01-117">**GX_STYLE_BORDER_THICK**</span><span class="sxs-lookup"><span data-stu-id="4ce01-117">**GX_STYLE_BORDER_THICK**</span></span> 
  - <span data-ttu-id="4ce01-118">값: 0x00000008</span><span class="sxs-lookup"><span data-stu-id="4ce01-118">Value: 0x00000008</span></span>
  - <span data-ttu-id="4ce01-119">설명: 두꺼운 테두리를 사용하여 위젯을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-119">Description: Draw widget with a thick border.</span></span>

<span data-ttu-id="4ce01-120">**GX_STYLE_BORDER_MASK**</span><span class="sxs-lookup"><span data-stu-id="4ce01-120">**GX_STYLE_BORDER_MASK**</span></span>
  - <span data-ttu-id="4ce01-121">값: 0x0000000f</span><span class="sxs-lookup"><span data-stu-id="4ce01-121">Value: 0x0000000f</span></span>
  - <span data-ttu-id="4ce01-122">설명: 위젯 스타일 멤버의 스타일 필드만 테스트하기 위해 사용되는 마스크 값입니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-122">Description: Mask value used to test only the style fields of the widget style member.</span></span>

<span data-ttu-id="4ce01-123">**GX_STYLE_TRANSPARENT**</span><span class="sxs-lookup"><span data-stu-id="4ce01-123">**GX_STYLE_TRANSPARENT**</span></span>
  - <span data-ttu-id="4ce01-124">값: 0x10000000</span><span class="sxs-lookup"><span data-stu-id="4ce01-124">Value: 0x10000000</span></span>
  - <span data-ttu-id="4ce01-125">설명: 최소한 부분적으로 투명한 위젯을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-125">Description: Create a widget that is at least partially transparent.</span></span> <span data-ttu-id="4ce01-126">이 스타일은 반투명 pixelmap을 위젯 배경으로 그리는 위젯을 포함하여 위젯이 자신을 완전 불투명으로 그리지 않을 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-126">This style should be used when a widget does not draw itself fully opaque, including widgets that draw a semi-transparent pixelmap as the widget background.</span></span> <span data-ttu-id="4ce01-127">이 스타일 플래그는 위젯 배경 영역을 새로 고치기 위해 위젯 부모를 그려야 함을 GUIX에 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-127">This style flag informs GUIX that the widget parent must be drawn to refresh the widget background area.</span></span>

<span data-ttu-id="4ce01-128">**GX_STYLE_DRAW_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="4ce01-128">**GX_STYLE_DRAW_SELECTED**</span></span>
  - <span data-ttu-id="4ce01-129">값: 0x20000000</span><span class="sxs-lookup"><span data-stu-id="4ce01-129">Value: 0x20000000</span></span>
  - <span data-ttu-id="4ce01-130">설명: 선택한 상태 색상 및 글꼴을 사용하여 위젯을 그리도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-130">Description: Specify that the widget should be drawn using selected state colors and fonts.</span></span> <span data-ttu-id="4ce01-131">다른 위젯 유형은 여러 방법으로 DRAW_SELECTED 스타일을 사용하여 위젯이 현재 선택되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-131">Different widget types use the DRAW_SELECTED style in different ways to indicate the widget is currently selected.</span></span>

<span data-ttu-id="4ce01-132">**GX_STYLE_ENABLED**</span><span class="sxs-lookup"><span data-stu-id="4ce01-132">**GX_STYLE_ENABLED**</span></span>
  - <span data-ttu-id="4ce01-133">값: 0x40000000</span><span class="sxs-lookup"><span data-stu-id="4ce01-133">Value: 0x40000000</span></span>
  - <span data-ttu-id="4ce01-134">설명: 위젯에서 사용자 입력 이벤트를 수락하고 출력 신호를 생성할 수 있도록 위젯을 사용으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-134">Description: Mark the widget as enabled, which allows the widget to accept user input events and generate output signals.</span></span>
  
<span data-ttu-id="4ce01-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span><span class="sxs-lookup"><span data-stu-id="4ce01-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span></span>
  - <span data-ttu-id="4ce01-136">값: 0x80000000</span><span class="sxs-lookup"><span data-stu-id="4ce01-136">Value: 0x80000000</span></span>
  - <span data-ttu-id="4ce01-137">설명: 위젯을 만들 때 gx_system_memory_allocator 서비스를 사용하여 위젯 제어 블록 메모리가 동적으로 할당되고 위젯이 삭제되면 제어 블록 메모리가 해제됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-137">Description: Indicates the widget control block memory is dynamically allocated using the gx_system_memory_allocator service when the widget is created, and the control block memory is freed if the widget is destroyed.</span></span>

<span data-ttu-id="4ce01-138">**GX_STYLE_USE_LOCAL_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="4ce01-138">**GX_STYLE_USE_LOCAL_ALPHA**</span></span>
  - <span data-ttu-id="4ce01-139">값: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="4ce01-139">Value: 0x01000000</span></span>
  - <span data-ttu-id="4ce01-140">설명: 위젯을 그릴 때 로컬 위젯 알파 값을 사용하도록 GUIX 그리기 함수에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-140">Description: Instructs GUIX drawing functions to use the local widget alpha value when drawing the widget.</span></span> <span data-ttu-id="4ce01-141">이 플래그는 일반적으로 내부 GUIX 논리에서 위젯 페이딩 애니메이션을 구현하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-141">This flag is normally used by the internal GUIX logic to implement widget fading animations.</span></span>


<span data-ttu-id="4ce01-142">__***텍스트 맞춤 스타일(텍스트를 그리는 모든 위젯에 적용되는 스타일):***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-142">__***Text Alignment Styles (styles applied to all widgets that draw text):***__</span></span>

<span data-ttu-id="4ce01-143">**GX_STYLE_TEXT_LEFT**</span><span class="sxs-lookup"><span data-stu-id="4ce01-143">**GX_STYLE_TEXT_LEFT**</span></span>
  - <span data-ttu-id="4ce01-144">값: 0x00001000</span><span class="sxs-lookup"><span data-stu-id="4ce01-144">Value: 0x00001000</span></span>
  - <span data-ttu-id="4ce01-145">설명: 위젯 클라이언트 영역 내에서 왼쪽 맞춤으로 텍스트가 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-145">Description: Text is drawn left-aligned within the widget client area.</span></span>

<span data-ttu-id="4ce01-146">**GX_STYLE_TEXT_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="4ce01-146">**GX_STYLE_TEXT_RIGHT**</span></span> 
  - <span data-ttu-id="4ce01-147">값: 0x00002000</span><span class="sxs-lookup"><span data-stu-id="4ce01-147">Value: 0x00002000</span></span>
  - <span data-ttu-id="4ce01-148">설명: 위젯 클라이언트 영역 내에서 오른쪽 맞춤으로 텍스트가 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-148">Description: Text is drawn right-aligned within the widget client area.</span></span>

<span data-ttu-id="4ce01-149">**GX_STYLE_TEXT_CENTER**</span><span class="sxs-lookup"><span data-stu-id="4ce01-149">**GX_STYLE_TEXT_CENTER**</span></span>
  - <span data-ttu-id="4ce01-150">값: 0x00004000</span><span class="sxs-lookup"><span data-stu-id="4ce01-150">Value: 0x00004000</span></span>
  - <span data-ttu-id="4ce01-151">설명: 위젯 클라이언트 영역 내에서 가운데 맞춤으로 텍스트가 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-151">Description: Text is drawn center-aligned within the widget client area.</span></span>

<span data-ttu-id="4ce01-152">**GX_STYLE_TEXT_COPY**</span><span class="sxs-lookup"><span data-stu-id="4ce01-152">**GX_STYLE_TEXT_COPY**</span></span>
  - <span data-ttu-id="4ce01-153">값: 0x00008000</span><span class="sxs-lookup"><span data-stu-id="4ce01-153">Value: 0x00008000</span></span>
  - <span data-ttu-id="4ce01-154">설명: 기본적으로 텍스트를 그리는 위젯은 애플리케이션에서 전달된 텍스트에만 포인터를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-154">Description: By default, widgets that draw text keep only a pointer to the text which is passed in by the application.</span></span> <span data-ttu-id="4ce01-155">문자열 테이블 내에 정의되는 정적으로 정의된 텍스트의 경우 위젯이 할당된 텍스트의 프라이빗 복사본을 만들 이유가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-155">For statically defined text that is defined within the string table, there is no reason for the widget to make a private copy of the text assigned.</span></span> <span data-ttu-id="4ce01-156">하지만 위젯에 할당된 텍스트가 sprint() 또는 gx_utility_ltoa와 같은 함수를 사용하여 동적으로 생성된 경우 할당된 텍스트의 고유한 프라이빗 복사본을 유지하도록 위젯에 지정하는 것이 편리한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-156">However, if the text assigned to a widget is created dynamically using functions like sprint() or gx_utility_ltoa, then it is often convenient to tell the widget to keep it’s own private copy of any text assigned.</span></span> <span data-ttu-id="4ce01-157">이렇게 하면 애플리케이션이 텍스트 문자열을 정의할 때, 즉 동적으로 정의된 텍스트를 사용하는 각 텍스트 위젯에 대해 애플리케이션이 정적으로 정의된 문자 배열을 정의해야 하는 경우, 자동 또는 임시 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-157">This allows the application to use automatic or temporary variables when defining the text string, when the application would otherwise be required to define statically defined character arrays for each text widget that is using dynamically defined text.</span></span> <span data-ttu-id="4ce01-158">이 스타일 플래그가 설정되면 위젯은 gx_system_memory_allocator 함수를 사용하여 할당된 문자열의 프라이빗 복사본을 저장하는 데 필요한 메모리 블록을 동적으로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-158">When this style flag is set, the widget will use the gx_system_memory_allocator function to dynamically allocate the memory block needed to hold a private copy of the assigned string.</span></span> <span data-ttu-id="4ce01-159">따라서 이 스타일 플래그 사용은 memory_deallocator 함수를 정의하는 애플리케이션을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-159">Therefore using this style flag is predicated on the application defining memory_allocator and memory_deallocator functions.</span></span> <span data-ttu-id="4ce01-160">설정된 뒤에는 GX_STYLE_TEXT_COPY를 지우지 않아야 합니다. 그렇지 않으면 예측할 수 없는 결과가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-160">GX_STYLE_TEXT_COPY should not be cleared after it has been set, and doing so will cause unpredictable results.</span></span>

<span data-ttu-id="4ce01-161">__***단추 스타일(GUIX 단추 위젯 유형에만 적용):***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-161">__***Button Styles (apply only to GUIX button widget types):***__</span></span>

<span data-ttu-id="4ce01-162">**GX_STYLE_BUTTON_PUSHED**</span><span class="sxs-lookup"><span data-stu-id="4ce01-162">**GX_STYLE_BUTTON_PUSHED**</span></span>
  - <span data-ttu-id="4ce01-163">값 0x00000010</span><span class="sxs-lookup"><span data-stu-id="4ce01-163">Value 0x00000010</span></span>
  - <span data-ttu-id="4ce01-164">설명: 단추를 눌렀거나 선택한 상태임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-164">Description: Indicates the button is in the pushed or selected state.</span></span>

<span data-ttu-id="4ce01-165">**GX_STYLE_BUTTON_TOGGLE**</span><span class="sxs-lookup"><span data-stu-id="4ce01-165">**GX_STYLE_BUTTON_TOGGLE**</span></span>
  - <span data-ttu-id="4ce01-166">값 0x00000020</span><span class="sxs-lookup"><span data-stu-id="4ce01-166">Value 0x00000020</span></span>
  - <span data-ttu-id="4ce01-167">설명: 클릭 이벤트가 발생할 때마다 단추 상태가 푸시된 상태와 푸시 취소된 상태로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-167">Description: Button will switch status between pushed and unpushed on every click event.</span></span> <span data-ttu-id="4ce01-168">이 스타일은 일반적으로 “확인란” 스타일 단추와 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-168">This style is commonly used with “checkbox” style buttons.</span></span>

<span data-ttu-id="4ce01-169">**GX_STYLE_BUTTON_RADIO**</span><span class="sxs-lookup"><span data-stu-id="4ce01-169">**GX_STYLE_BUTTON_RADIO**</span></span>
  - <span data-ttu-id="4ce01-170">값 0x00000040</span><span class="sxs-lookup"><span data-stu-id="4ce01-170">Value 0x00000040</span></span>
  - <span data-ttu-id="4ce01-171">설명: 이 스타일은 단추가 배타적임을 나타내며 이 단추를 선택하면 모든 형제 단추의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-171">Description: This style indicates the button will be exclusive, and deselect any button siblings when selected.</span></span> <span data-ttu-id="4ce01-172">이 스타일은 일반적으로 “라디오 단추” 스타일 단추와 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-172">This style is commonly used with “radio button” style buttons.</span></span>

<span data-ttu-id="4ce01-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span><span class="sxs-lookup"><span data-stu-id="4ce01-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span></span>
  - <span data-ttu-id="4ce01-174">값: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="4ce01-174">Value: 0x00000080</span></span>
  - <span data-ttu-id="4ce01-175">설명: 단추가 처음 푸시될 때 클릭 이벤트가 발생함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-175">Description: Indicates the button generates a click event when initially pushed.</span></span> <span data-ttu-id="4ce01-176">기본 작업은 단추를 해제할 때 클릭 이벤트를 생성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-176">The default operation is to generate a click event when the button is released.</span></span>

<span data-ttu-id="4ce01-177">**GX_STYLE_BUTTON_REPEAT**</span><span class="sxs-lookup"><span data-stu-id="4ce01-177">**GX_STYLE_BUTTON_REPEAT**</span></span>
  - <span data-ttu-id="4ce01-178">값 0x00000100</span><span class="sxs-lookup"><span data-stu-id="4ce01-178">Value 0x00000100</span></span>
  - <span data-ttu-id="4ce01-179">설명: 단추가 푸시된 상태로 유지될 때 단추가 단추 부모에게 반복되는 클릭 이벤트를 전송해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-179">Description: Indicates the button should send repeated click events to the button parent when the button is held in the pushed state.</span></span>

<span data-ttu-id="4ce01-180">__***목록 스타일(GUIX 목록 위젯 유형에만 적용):***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-180">__***List Styles (apply only to GUIX list widget types):***__</span></span>

<span data-ttu-id="4ce01-181">**GX_STYLE_CENTER_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="4ce01-181">**GX_STYLE_CENTER_SELECTED**</span></span> 
  - <span data-ttu-id="4ce01-182">값: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="4ce01-182">Value: 0x00000010</span></span>
  - <span data-ttu-id="4ce01-183">설명: 예약됨</span><span class="sxs-lookup"><span data-stu-id="4ce01-183">Description: Reserved</span></span>

<span data-ttu-id="4ce01-184">**GX_STYLE_WRAP**</span><span class="sxs-lookup"><span data-stu-id="4ce01-184">**GX_STYLE_WRAP**</span></span>
  - <span data-ttu-id="4ce01-185">값 0x00000020</span><span class="sxs-lookup"><span data-stu-id="4ce01-185">Value 0x00000020</span></span>
  - <span data-ttu-id="4ce01-186">설명: 목록이 시작 또는 끝 목록 인덱스를 지나서 드래그되거나 스크롤될 때 목록 자식은 처음부터 끝까지 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-186">Description: The list children wrap from start to end when the list is dragged or scrolled past the starting or ending list index.</span></span>

<span data-ttu-id="4ce01-187">**GX_STYLE_FLICKABLE**</span><span class="sxs-lookup"><span data-stu-id="4ce01-187">**GX_STYLE_FLICKABLE**</span></span>
  - <span data-ttu-id="4ce01-188">값: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="4ce01-188">Value: 0x00000040</span></span>
  - <span data-ttu-id="4ce01-189">설명: 예약됨</span><span class="sxs-lookup"><span data-stu-id="4ce01-189">Description: Reserved</span></span>

<span data-ttu-id="4ce01-190">__***Pixelmap 단추 및 아이콘 단추 스타일:***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-190">__***Pixelmap Button and Icon Button Styles:***__</span></span>

<span data-ttu-id="4ce01-191">**GX_STYLE_HALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="4ce01-191">**GX_STYLE_HALIGN_CENTER**</span></span>
  - <span data-ttu-id="4ce01-192">값: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="4ce01-192">Value: 0x00010000</span></span>
  - <span data-ttu-id="4ce01-193">설명: 가로 축에서 단추 경계 내에 단추 pixelmap이 가운데 맞춤으로 정렬되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-193">Description: The button pixelmap should be center aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="4ce01-194">**GX_STYLE_HALIGN_LEFT**</span><span class="sxs-lookup"><span data-stu-id="4ce01-194">**GX_STYLE_HALIGN_LEFT**</span></span>
  - <span data-ttu-id="4ce01-195">값: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="4ce01-195">Value: 0x00020000</span></span>
  - <span data-ttu-id="4ce01-196">설명: 가로 축에서 단추 경계 내에 단추 pixelmap이 왼쪽 맞춤으로 정렬되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-196">Description: The button pixelmap should be left aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="4ce01-197">**GX_STYLE_HALIGN_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="4ce01-197">**GX_STYLE_HALIGN_RIGHT**</span></span>
  - <span data-ttu-id="4ce01-198">값 0x00040000</span><span class="sxs-lookup"><span data-stu-id="4ce01-198">Value 0x00040000</span></span>
  - <span data-ttu-id="4ce01-199">설명: 가로 축에서 단추 경계 내에 단추 pixelmap이 오른쪽 맞춤으로 정렬되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-199">Description: The button pixelmap should be right aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="4ce01-200">**GX_STYLE_VALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="4ce01-200">**GX_STYLE_VALIGN_CENTER**</span></span>
  - <span data-ttu-id="4ce01-201">값 0x00080000</span><span class="sxs-lookup"><span data-stu-id="4ce01-201">Value 0x00080000</span></span>
  - <span data-ttu-id="4ce01-202">설명: 세로 축에서 단추 경계 내에 단추 pixelmap이 가운데 맞춤으로 정렬되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-202">Description: The button pixelmap should be center aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="4ce01-203">**GX_STYLE_VALIGN_TOP**</span><span class="sxs-lookup"><span data-stu-id="4ce01-203">**GX_STYLE_VALIGN_TOP**</span></span>
  - <span data-ttu-id="4ce01-204">값: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="4ce01-204">Value: 0x00100000</span></span>
  - <span data-ttu-id="4ce01-205">설명: 세로 축에서 단추 경계 내에 단추 pixelmap이 위쪽 맞춤으로 정렬되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-205">Description: The button pixelmap should be top aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="4ce01-206">**GX_STYLE_VALIGN_BOTTOM**</span><span class="sxs-lookup"><span data-stu-id="4ce01-206">**GX_STYLE_VALIGN_BOTTOM**</span></span>
  - <span data-ttu-id="4ce01-207">값: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="4ce01-207">Value: 0x00200000</span></span>
  - <span data-ttu-id="4ce01-208">설명: 가로 세로 축에서 단추 경계 내에 단추 pixelmap이 아래쪽 맞춤으로 정렬되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-208">Description: The button pixelmap should be bottom aligned within the button boundary on the vertical horizontal axis.</span></span>

<span data-ttu-id="4ce01-209">__***슬라이더 스타일(GX_SLIDER 및 파생된 위젯 유형에만 적용):***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-209">__***Slider Styles (Appy only to GX_SLIDER and derived widget types):***__</span></span>

<span data-ttu-id="4ce01-210">**GX_STYLE_SHOW_NEEDLE**</span><span class="sxs-lookup"><span data-stu-id="4ce01-210">**GX_STYLE_SHOW_NEEDLE**</span></span>
  - <span data-ttu-id="4ce01-211">값: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="4ce01-211">Value: 0x00000200</span></span>
  - <span data-ttu-id="4ce01-212">설명: 슬라이더가 니들 표시기를 그리려면 이 스타일이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-212">Description: This style must be included for the slider to draw the needle indicator.</span></span> <span data-ttu-id="4ce01-213">애플리케이션에서 슬라이더 니들을 사용 중지하거나 사용자 지정 니들 표시기를 그리려면 이 스타일을 사용 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-213">This style can be disabled if the application wants to disable the slider needle or draw a custom needle indicator.</span></span>

<span data-ttu-id="4ce01-214">**GX_STYLE_SHOW_TICKMARKS**</span><span class="sxs-lookup"><span data-stu-id="4ce01-214">**GX_STYLE_SHOW_TICKMARKS**</span></span>
  - <span data-ttu-id="4ce01-215">값: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="4ce01-215">Value: 0x00000400</span></span>
  - <span data-ttu-id="4ce01-216">설명: 이 스타일을 사용하는 경우 슬라이더 위젯이 파선 눈금 표시선에 대한 소프트웨어 그리기를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-216">Description: The slider widget will do software drawing of dashed tickmark lines when this style is enabled.</span></span>

<span data-ttu-id="4ce01-217">**GX_STYLE_SLIDER_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="4ce01-217">**GX_STYLE_SLIDER_VERTICAL**</span></span>
  - <span data-ttu-id="4ce01-218">값 0x00000800</span><span class="sxs-lookup"><span data-stu-id="4ce01-218">Value 0x00000800</span></span>
  - <span data-ttu-id="4ce01-219">설명: 세로 슬라이더를 만들려면 이 스타일 플래그를 설정하고, 가로 슬라이더를 만들려면 이 스타일 플래그를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-219">Description: Set this style flag to create a vertical slider, and clear this style flag to create a horizontal slider.</span></span>

<span data-ttu-id="4ce01-220">__***스프라이트 스타일(GX_SPRITE 위젯 유형에만 적용):***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-220">__***Sprite Styles (Applies only to GX_SPRITE widget types):***__</span></span>

<span data-ttu-id="4ce01-221">**GX_STYLE_SPRITE_AUTO**</span><span class="sxs-lookup"><span data-stu-id="4ce01-221">**GX_STYLE_SPRITE_AUTO**</span></span>
  - <span data-ttu-id="4ce01-222">값: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="4ce01-222">Value: 0x00000010</span></span>
  - <span data-ttu-id="4ce01-223">설명: 스프라이트 위젯에 GX_EVENT_SHOW 이벤트가 수신되었을 때 스프라이트 애니메이션이 자동으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-223">Description: Indicates the sprite animation will run automatically when the sprite widget received the GX_EVENT_SHOW event.</span></span>

<span data-ttu-id="4ce01-224">**GX_STYLE_SPRITE_LOOP**</span><span class="sxs-lookup"><span data-stu-id="4ce01-224">**GX_STYLE_SPRITE_LOOP**</span></span>
  - <span data-ttu-id="4ce01-225">값: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="4ce01-225">Value: 0x00000020</span></span>
  - <span data-ttu-id="4ce01-226">설명: 이 스타일을 사용하면 애플리케이션에서 스프라이트를 중지할 때까지 스프라이트 위젯에 스프라이트 애니메이션 프레임이 연속으로 재생됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-226">Description: With this style, the sprite widget will continuously loop through sprite animation frames until the sprite is stopped by the application.</span></span>

<span data-ttu-id="4ce01-227">__***Pixelmap 슬라이더 스타일:***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-227">__***Pixelmap Slider Styles:***__</span></span>

<span data-ttu-id="4ce01-228">**GX_STYLE_TILE_BACKGROUND**</span><span class="sxs-lookup"><span data-stu-id="4ce01-228">**GX_STYLE_TILE_BACKGROUND**</span></span>
  - <span data-ttu-id="4ce01-229">값 0x00001000</span><span class="sxs-lookup"><span data-stu-id="4ce01-229">Value 0x00001000</span></span>
  - <span data-ttu-id="4ce01-230">설명: 슬라이더 배경 이미지가 바둑판식으로 배열되어 스프라이트 경계 상자를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-230">Description: The slider background image is tiled to fill the sprite bounding rectangle.</span></span> <span data-ttu-id="4ce01-231">이렇게 하면 작은 세로 또는 가로 스트라이프 이미지를 사용하여 슬라이더 배경을 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-231">This allows a small vertical or horizontal stripe image to be used to fill the slider background.</span></span>

<span data-ttu-id="4ce01-232">__***추가 진행률 표시줄 스타일:***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-232">__***Additional Progress Bar Styles:***__</span></span>

<span data-ttu-id="4ce01-233">**GX_STYLE_PROGRESS_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="4ce01-233">**GX_STYLE_PROGRESS_PERCENT**</span></span>
  - <span data-ttu-id="4ce01-234">값: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="4ce01-234">Value: 0x00000010</span></span>
  - <span data-ttu-id="4ce01-235">설명: 이 스타일이 설정되면 진행률 표시줄에서 막대 값이 원시 값 대신 백분율로 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-235">Description: When this style is set, the progress bar will draw  bar value as a percentage rather than a raw value.</span></span> <span data-ttu-id="4ce01-236">텍스트는 진행률 표시줄 경계 상자의 가운데에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-236">The text is centered in the progress bar bounding rectangle.</span></span>

<span data-ttu-id="4ce01-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span><span class="sxs-lookup"><span data-stu-id="4ce01-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span></span>
  - <span data-ttu-id="4ce01-238">값: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="4ce01-238">Value: 0x00000020</span></span>
  - <span data-ttu-id="4ce01-239">설명: 진행률 표시줄에서 가운데 표시된 십진수 텍스트로 현재 진행률 표시줄 값을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-239">Description: Draw the current progress bar value as decimal text centered within the progress bar.</span></span>

<span data-ttu-id="4ce01-240">**GX_STYLE_PROGRESS_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="4ce01-240">**GX_STYLE_PROGRESS_VERTICAL**</span></span>
  - <span data-ttu-id="4ce01-241">값: 0x0000040</span><span class="sxs-lookup"><span data-stu-id="4ce01-241">Value: 0x0000040</span></span>
  - <span data-ttu-id="4ce01-242">설명: 진행률이 세로 방향으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-242">Description: Indicate the progress is vertically oriented.</span></span> <span data-ttu-id="4ce01-243">기본값은 가로 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-243">The default is horizontal orientation.</span></span>

<span data-ttu-id="4ce01-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**:</span><span class="sxs-lookup"><span data-stu-id="4ce01-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**:</span></span>
  - <span data-ttu-id="4ce01-245">**값**: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="4ce01-245">**Value**: 0x00000100</span></span>
  - <span data-ttu-id="4ce01-246">설명: 진행률 표시줄 값이 단색 채우기 대신 세그먼트로 채워진 사각형으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-246">Description: The progress bar value is indicated with segmented filled rectangles, rather than a solid fill.</span></span>

<span data-ttu-id="4ce01-247">__***추가 방사형 진행률 표시줄 스타일:***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-247">__***Additional Radial Progress Bar Styles:***__</span></span>

<span data-ttu-id="4ce01-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="4ce01-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span></span>
  - <span data-ttu-id="4ce01-249">값: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="4ce01-249">Value: 0x00000200</span></span>
  - <span data-ttu-id="4ce01-250">설명: 앤티앨리어싱된 브러시 스타일을 사용하여 방사형 진행률 표시줄을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-250">Description: Draw the radial progress bar using anti-aliased brush styles.</span></span> <span data-ttu-id="4ce01-251">이렇게 하면 CPU 대역폭이 더 많이 필요하지만 모양이 더 좋아집니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-251">This requires more CPU bandwidth but also produces a nicer appearance.</span></span> <span data-ttu-id="4ce01-252">성능이 낮은 CPU 대상의 경우 이 스타일 플래그를 지우면 그리기 속도가 빨라집니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-252">For lower performance CPU targets, clearing this style flag will result in faster drawing speed.</span></span>

<span data-ttu-id="4ce01-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span><span class="sxs-lookup"><span data-stu-id="4ce01-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span></span>
  - <span data-ttu-id="4ce01-254">값: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="4ce01-254">Value: 0x00000400</span></span>
  - <span data-ttu-id="4ce01-255">설명: 방사형 진행률 표시줄 호를 그릴 때 둥근 선 끝 브러시 스타일을 사용합니다. 기본값은 사각형 선 끝입니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-255">Description: Use a round line end brush style when drawing the radial progress bar arc. The default is a square line end.</span></span>

<span data-ttu-id="4ce01-256">__***추가 텍스트 입력 스타일:***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-256">__***Additional Text Input Styles:***__</span></span>

<span data-ttu-id="4ce01-257">**GX_STYLE_ CURSOR_BLINK**</span><span class="sxs-lookup"><span data-stu-id="4ce01-257">**GX_STYLE_ CURSOR_BLINK**</span></span>
  - <span data-ttu-id="4ce01-258">값: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="4ce01-258">Value: 0x00000040</span></span>
  - <span data-ttu-id="4ce01-259">설명: 텍스트 입력 위젯 커서가 안정되지 않고 깜박입니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-259">Description: The text input widget cursor will flash on and off rather than being steady.</span></span>

<span data-ttu-id="4ce01-260">**GX_STYLE_ CURSOR_ALWAYS**</span><span class="sxs-lookup"><span data-stu-id="4ce01-260">**GX_STYLE_ CURSOR_ALWAYS**</span></span>
  - <span data-ttu-id="4ce01-261">값: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="4ce01-261">Value: 0x00000080</span></span>
  - <span data-ttu-id="4ce01-262">설명</span><span class="sxs-lookup"><span data-stu-id="4ce01-262">Description.</span></span> <span data-ttu-id="4ce01-263">텍스트 입력 위젯 커서는 일반적으로 위젯에 입력 포커스가 있을 때만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-263">The text input widget cursor is normally only displayed when the widget owns input focus.</span></span> <span data-ttu-id="4ce01-264">이 스타일 플래그는 입력 포커스에 관계없이 커서를 항상 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-264">This style flag will make the cursor always visible regardless of input focus.</span></span>

<span data-ttu-id="4ce01-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span><span class="sxs-lookup"><span data-stu-id="4ce01-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span></span>
  - <span data-ttu-id="4ce01-266">값: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="4ce01-266">Value: 0x00000100</span></span>
  - <span data-ttu-id="4ce01-267">설명: 이 스타일 플래그는 텍스트 입력 위젯에 키 누름 이벤트가 수신될 때마다 GX_EVENT_TEXT_EDITED 이벤트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-267">Description: With this style flag set the GX_EVENT_TEXT_EDITED event every time key down event is received by the text input widget.</span></span>

<span data-ttu-id="4ce01-268">__***추가 창 스타일:***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-268">__***Additional Window Styles:***__</span></span>

<span data-ttu-id="4ce01-269">**GX_STYLE_TILE_WALLPAPER**</span><span class="sxs-lookup"><span data-stu-id="4ce01-269">**GX_STYLE_TILE_WALLPAPER**</span></span>
  - <span data-ttu-id="4ce01-270">값: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="4ce01-270">Value: 0x00040000</span></span>
  - <span data-ttu-id="4ce01-271">설명: 창이 할당된 모든 배경 무늬 이미지를 바둑판식으로 배열하여 창 클라이언트 사각형을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-271">Description: The window will tile any assigned wallpaper image to fill the window client rectangle.</span></span>

<span data-ttu-id="4ce01-272">**GX_STYLE_AUTO_HSCROLL**</span><span class="sxs-lookup"><span data-stu-id="4ce01-272">**GX_STYLE_AUTO_HSCROLL**</span></span>
  - <span data-ttu-id="4ce01-273">값: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="4ce01-273">Value: 0x00100000</span></span>
  - <span data-ttu-id="4ce01-274">설명: 나중에 사용하도록 예약되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-274">Description: Reserved for future use.</span></span>

<span data-ttu-id="4ce01-275">**GX_STYLE_AUTO_VSCROLL**</span><span class="sxs-lookup"><span data-stu-id="4ce01-275">**GX_STYLE_AUTO_VSCROLL**</span></span>
  - <span data-ttu-id="4ce01-276">값: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="4ce01-276">Value: 0x00200000</span></span>
  - <span data-ttu-id="4ce01-277">설명: 나중에 사용하도록 예약되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-277">Description: Reserved for future use.</span></span>

<span data-ttu-id="4ce01-278">__***추가 메뉴 스타일:***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-278">__***Additional Menu Styles:***__</span></span>

<span data-ttu-id="4ce01-279">**GX_STYLE_MENU_EXPANDED**</span><span class="sxs-lookup"><span data-stu-id="4ce01-279">**GX_STYLE_MENU_EXPANDED**</span></span>
  - <span data-ttu-id="4ce01-280">값: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="4ce01-280">Value: 0x00000010</span></span>
  - <span data-ttu-id="4ce01-281">설명: 아코디언 메뉴 위젯은 처음에는 확장된 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-281">Description: Accordion menu widget is initially in expanded state.</span></span>

<span data-ttu-id="4ce01-282">__***추가 트리 뷰 스타일:***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-282">__***Additional Tree View Styles:***__</span></span>

<span data-ttu-id="4ce01-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span><span class="sxs-lookup"><span data-stu-id="4ce01-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span></span>
  - <span data-ttu-id="4ce01-284">값: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="4ce01-284">Value: 0x00000010</span></span>
  - <span data-ttu-id="4ce01-285">설명: 트리 뷰 위젯은 노드 아이콘에서 루트 트리 노드까지 선을 그려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-285">Description: Tree view widget should draw lines from node icon to root tree node.</span></span>

<span data-ttu-id="4ce01-286">__***추가 스크롤 막대 스타일:***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-286">__***Additional Scrollbar Styles:***__</span></span>

<span data-ttu-id="4ce01-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span><span class="sxs-lookup"><span data-stu-id="4ce01-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span></span>
  - <span data-ttu-id="4ce01-288">값: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="4ce01-288">Value: 0x00010000</span></span>
  - <span data-ttu-id="4ce01-289">설명: 나중에 사용하도록 예약되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-289">Description: Reserved for future use.</span></span>

<span data-ttu-id="4ce01-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span><span class="sxs-lookup"><span data-stu-id="4ce01-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span></span>
  - <span data-ttu-id="4ce01-291">값: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="4ce01-291">Value: 0x00020000</span></span>
  - <span data-ttu-id="4ce01-292">설명: 스크롤 막대 썸 너비(가로 스크롤 막대의 경우) 또는 높이(세로 스크롤 막대의 경우)는 최소 및 최대 스크롤 막대 범위에 대한 부모 창의 표시 영역 비율을 기반으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-292">Description: The scrollbar thumb width (for a horizontal scroll bar) or height (for a vertical scroll bar) are calculated based on the ratio of the visible area of the parent window to the min and max scrollbar range.</span></span>

<span data-ttu-id="4ce01-293">**GX_SCROLLBAR_END_BUTTONS**</span><span class="sxs-lookup"><span data-stu-id="4ce01-293">**GX_SCROLLBAR_END_BUTTONS**</span></span>
  - <span data-ttu-id="4ce01-294">값: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="4ce01-294">Value: 0x00040000</span></span>
  - <span data-ttu-id="4ce01-295">설명: 스크롤 막대가 스크롤 막대 영역의 각 끝에서 단추를 자동으로 만들고 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-295">Description: The scrollbar automatically creates and attaches buttons at each end of the scrollbar region.</span></span>

<span data-ttu-id="4ce01-296">**GX_SCROLLBAR_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="4ce01-296">**GX_SCROLLBAR_VERTICAL**</span></span> 
  - <span data-ttu-id="4ce01-297">값: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="4ce01-297">Value: 0x01000000</span></span>
  - <span data-ttu-id="4ce01-298">설명: 스크롤 막대가 세로 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-298">Description: The scrollbar is vertically oriented.</span></span>

<span data-ttu-id="4ce01-299">**GX_SCROLLBAR_HORIZONTAL**</span><span class="sxs-lookup"><span data-stu-id="4ce01-299">**GX_SCROLLBAR_HORIZONTAL**</span></span>
  - <span data-ttu-id="4ce01-300">값: 0x02000000</span><span class="sxs-lookup"><span data-stu-id="4ce01-300">Value: 0x02000000</span></span>
  - <span data-ttu-id="4ce01-301">설명: 스크롤 막대가 가로 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-301">Description: The scrollbar is horizontally oriented.</span></span>

<span data-ttu-id="4ce01-302">__***텍스트 스크롤 휠 스타일:***__</span><span class="sxs-lookup"><span data-stu-id="4ce01-302">__***Text Scroll Wheel Styles:***__</span></span>

<span data-ttu-id="4ce01-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span><span class="sxs-lookup"><span data-stu-id="4ce01-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span></span>
  - <span data-ttu-id="4ce01-304">값: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="4ce01-304">Value: 0x00000200</span></span>
  - <span data-ttu-id="4ce01-305">설명: 스크롤 휠은 사인 곡선 알고리즘을 사용하여 스크롤 휠이 둥근 모양으로 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-305">Description: The scroll wheel uses a Sinusoidal algorithm to make the scroll wheel appear to have a rounded shape.</span></span> <span data-ttu-id="4ce01-306">이 스타일 플래그는 스크롤 휠 위젯의 성능에 상당한 오버헤드를 추가할 수 있지만 휠을 실제와 같은 3D 모양으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ce01-306">This style flag can add significant overhead to the performance of the scroll wheel widget, but can also give the wheel a 3D realistic appearance.</span></span>