---
title: 부록 I - GUIX 정보 구조
description: GUIX 정보 구조에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 03a10aeb65017befaf5e7b440046dbff9f9252ef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812025"
---
# <a name="appendix-i---guix-information-structures"></a><span data-ttu-id="73cdd-103">부록 I - GUIX 정보 구조</span><span class="sxs-lookup"><span data-stu-id="73cdd-103">Appendix I - GUIX Information Structures</span></span> 

## <a name="gx_bidi_text_info"></a><span data-ttu-id="73cdd-104">GX_BIDI_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="73cdd-104">GX_BIDI_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="73cdd-105">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-105">Definition</span></span>

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="73cdd-106">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-106">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="73cdd-107">**gx_bidi_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="73cdd-107">**gx_bidi_text_info_text**</span></span>               | <span data-ttu-id="73cdd-108">순서를 다시 정렬할 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-108">Text for reordering</span></span> |
| <span data-ttu-id="73cdd-109">**gx_bidi_text_info_font**</span><span class="sxs-lookup"><span data-stu-id="73cdd-109">**gx_bidi_text_info_font**</span></span>               | <span data-ttu-id="73cdd-110">텍스트를 표시하는 데 사용되는 글꼴입니다. 줄 바꿈이 필요하지 않은 경우 GX_NULL로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-110">Font used to display text, set it to GX_NULL if line breaking is not needed</span></span> |
| <span data-ttu-id="73cdd-111">**gx_bidi_text_info_display_width**</span><span class="sxs-lookup"><span data-stu-id="73cdd-111">**gx_bidi_text_info_display_width**</span></span>      | <span data-ttu-id="73cdd-112">표시하는 데 사용할 수 있는 너비입니다. 줄 바꿈이 필요하지 않은 경우 -1로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-112">Available width for displaying, set it to -1 if line breaking is not needed</span></span> |

## <a name="gx_bidi_resolved_text_info"></a><span data-ttu-id="73cdd-113">GX_BIDI_RESOLVED_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="73cdd-113">GX_BIDI_RESOLVED_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="73cdd-114">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-114">Definition</span></span>

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="73cdd-115">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-115">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="73cdd-116">**gx_bidi_resolved_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="73cdd-116">**gx_bidi_resolved_text_info_text**</span></span>             | <span data-ttu-id="73cdd-117">정렬된 양방향 텍스트 배열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-117">Pointer to the array of reordered bidi text</span></span> |
| <span data-ttu-id="73cdd-118">**gx_bidi_resolved_text_info_total_lines**</span><span class="sxs-lookup"><span data-stu-id="73cdd-118">**gx_bidi_resolved_text_info_total_lines**</span></span>      | <span data-ttu-id="73cdd-119">한 단락에 대해 확인된 양방향 텍스트의 전체 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-119">Total lines of resolved bidi text for one paragraph</span></span> |
| <span data-ttu-id="73cdd-120">**gx_bidi_resolved_text_info_next**</span><span class="sxs-lookup"><span data-stu-id="73cdd-120">**gx_bidi_resolved_text_info_next**</span></span>             | <span data-ttu-id="73cdd-121">다음 단락에 대해 확인된 양방향 텍스트 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-121">Resolved bidi text information for the next paragraph</span></span> |

## <a name="gx_circular_gauge_info"></a><span data-ttu-id="73cdd-122">GX_CIRCULAR_GAUGE_INFO</span><span class="sxs-lookup"><span data-stu-id="73cdd-122">GX_CIRCULAR_GAUGE_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="73cdd-123">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-123">Definition</span></span>

```c
typedef struct GX_CIRCULAR_GAUGE_INFO_STRUCT
{
    INT             gx_circular_gauge_info_animation_steps;
    INT             gx_circular_gauge_info_animation_delay;
    GX_VALUE        gx_circular_gauge_info_needle_xpos;
    GX_VALUE        gx_circular_gauge_info_needle_ypos;
    GX_VALUE        gx_circular_gauge_info_needle_xcor;
    GX_VALUE        gx_circular_gauge_info_needle_ycor;
    GX_RESOURCE_ID  gx_circular_gauge_info_needle_pixelmap;
} GX_CIRCULAR_GAUGE_INFO;
```
### <a name="members"></a><span data-ttu-id="73cdd-124">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-124">Members</span></span>

|                                                  |                                              |
| ------------------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="73cdd-125">**gx_circular_gauge_info_animation_steps**</span><span class="sxs-lookup"><span data-stu-id="73cdd-125">**gx_circular_gauge_info_animation_steps**</span></span>       | <span data-ttu-id="73cdd-126">현재 니들 각도에서 새로 할당된 니들 각도로 이동할 때 니들이 이동하는 총 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-126">Total steps the needle will travel through when moving from the current needle angle to a newly assigned needle angle</span></span> |
| <span data-ttu-id="73cdd-127">**gx_circular_gauge_info_animation_delay**</span><span class="sxs-lookup"><span data-stu-id="73cdd-127">**gx_circular_gauge_info_animation_delay**</span></span>       | <span data-ttu-id="73cdd-128">애니메이션 단계 간에 지연될 GUIX 시계 틱 수입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-128">The number of GUIX clock ticks to delay between animation steps</span></span> |
| <span data-ttu-id="73cdd-129">**gx_circular_gauge_info_needle_xpos**</span><span class="sxs-lookup"><span data-stu-id="73cdd-129">**gx_circular_gauge_info_needle_xpos**</span></span>           | <span data-ttu-id="73cdd-130">계기 위젯 왼쪽에서 계기 니들의 회전 중심까지의 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-130">The distance from the left of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="73cdd-131">**gx_circular_gauge_info_needle_ypos**</span><span class="sxs-lookup"><span data-stu-id="73cdd-131">**gx_circular_gauge_info_needle_ypos**</span></span>           | <span data-ttu-id="73cdd-132">계기 위젯 위쪽에서 계기 니들의 회전 중심까지의 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-132">The distance from the top of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="73cdd-133">**gx_circular_gauge_info_needle_xcor**</span><span class="sxs-lookup"><span data-stu-id="73cdd-133">**gx_circular_gauge_info_needle_xcor**</span></span>           | <span data-ttu-id="73cdd-134">계기 이미지 왼쪽에서 계기 니들의 회전 중심까지의 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-134">The distance from the left of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="73cdd-135">**gx_circular_gauge_info_needle_ycor**</span><span class="sxs-lookup"><span data-stu-id="73cdd-135">**gx_circular_gauge_info_needle_ycor**</span></span>           | <span data-ttu-id="73cdd-136">계기 이미지 위쪽에서 계기 니들의 회전 중심까지의 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-136">The distance from the top of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="73cdd-137">**gx_circular_gauge_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="73cdd-137">**gx_circular_gauge_info_needle_pixelmap**</span></span>       | <span data-ttu-id="73cdd-138">계기 니들을 그리는 데 사용되는 pixelmap의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-138">Resource ID of the pixelmap which will be used to draw the gauge needle.</span></span> <span data-ttu-id="73cdd-139">이 이미지는 계기 위젯에서 임의 위치에 계기 니들을 표시하기 위해 필요에 따라 회전됩니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-139">This image will be rotated as needed by the gauge widget to display the gauge needle in any position</span></span> |

<span data-ttu-id="73cdd-140">아래 다이어그램은 xpos, ypos 및 xcor, ycor 좌표를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-140">The diagram below illustrates the xpos, ypos, and xcor, ycor coordinates:</span></span>

![니들 Y 및 X 좌표 다이어그램](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a><span data-ttu-id="73cdd-142">GX_LINE_CHART_INFO</span><span class="sxs-lookup"><span data-stu-id="73cdd-142">GX_LINE_CHART_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="73cdd-143">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-143">Definition</span></span>

```c
typedef struct GX_LINE_CHART_INFO_STRUCT
{
    INT            gx_line_chart_min_val;
    INT            gx_line_chart_max_val;
    INT           *gx_line_chart_data;
    GX_VALUE       gx_line_left_margin;
    GX_VALUE       gx_line_top_margin;
    GX_VALUE       gx_line_right_margin;
    GX_VALUE       gx_line_bottom_margin;
    GX_VALUE       gx_line_chart_max_data_count;
    GX_VALUE       gx_line_chart_active_data_count;
    GX_VALUE       gx_line_chart_axis_line_width;
    GX_VALUE       gx_line_chart_data_line_width;
    GX_RESOURCE_ID gx_line_chart_axis_color;
    GX_RESOURCE_ID gx_line_chart_line_color;
} GX_LINE_CHART_INFO;
```

### <a name="members"></a><span data-ttu-id="73cdd-144">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-144">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="73cdd-145">**gx_line_chart_min_val**</span><span class="sxs-lookup"><span data-stu-id="73cdd-145">**gx_line_chart_min_val**</span></span>          | <span data-ttu-id="73cdd-146">스케일링을 계산하는 데 사용되는 최소 데이터 값입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-146">The minimum data value, which is used to calculate scaling</span></span>
| <span data-ttu-id="73cdd-147">**gx_line_chart_max_val**</span><span class="sxs-lookup"><span data-stu-id="73cdd-147">**gx_line_chart_max_val**</span></span>          | <span data-ttu-id="73cdd-148">스케일링을 계산하는 데 사용되는 최대 데이터 값입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-148">The maximum data value, which is used to calculate scaling</span></span> |
| <span data-ttu-id="73cdd-149">**gx_line_chart_data**</span><span class="sxs-lookup"><span data-stu-id="73cdd-149">**gx_line_chart_data**</span></span>             | <span data-ttu-id="73cdd-150">정수 값 배열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-150">Pointer to an array of integer values.</span></span> <span data-ttu-id="73cdd-151">꺾은선형 차트 위젯이 그리는 정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-151">These are the integer values plotted by the line chart widget</span></span> |
| <span data-ttu-id="73cdd-152">**gx_line_<side>_margin**</span><span class="sxs-lookup"><span data-stu-id="73cdd-152">**gx_line_<side>_margin**</span></span>          | <span data-ttu-id="73cdd-153">실제 차트 렌더링 영역에 바인딩된 차트 창 바깥쪽에서의 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-153">The offset from the chart window outer bound to the actual chart rendering area.</span></span> <span data-ttu-id="73cdd-154">차트 축과 데이터 줄은 항상이 이러한 안쪽 경계 내에 표시되므로 애플리케이션에서 차트 창 내부, 문자 그래프 영역 외부에 레이블 및 기타 정보를 그릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-154">The chart axis and data line are always plotted within this inner boundary, which allows the application to draw labels and other information inside the chart window but outside the char graphing area</span></span> |
| <span data-ttu-id="73cdd-155">**gx_line_chart_max_data_count**</span><span class="sxs-lookup"><span data-stu-id="73cdd-155">**gx_line_chart_max_data_count**</span></span>   | <span data-ttu-id="73cdd-156">존재할 수 있는 데이터 값의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-156">The number of data values which may be present.</span></span> <span data-ttu-id="73cdd-157">이 매개 변수는 데이터 요소를 그리는 데 사용되는 x축 스케일링 또는 간격을 계산하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-157">This parameter is used for calculating the x-axis scaling or interval for plotting data points.</span></span> |
| <span data-ttu-id="73cdd-158">**gx_line_active_data_count**</span><span class="sxs-lookup"><span data-stu-id="73cdd-158">**gx_line_active_data_count**</span></span>      | <span data-ttu-id="73cdd-159">데이터 배열에 실제로 표시되는 데이터 값의 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-159">The number of data values that actually present in the data array.</span></span> <span data-ttu-id="73cdd-160">예를 들어, 꺾은선형 차트는 최대 100개 값을 그리기 위해 스케일링될 수 있지만, 특정 업데이트에서는 실제로 더 적은 수의 데이터 값이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-160">A line chart may be scaled to draw a maximum of 100 values (for example), but on any particular update a smaller number of data values may actually be present.</span></span> |
| <span data-ttu-id="73cdd-161">**gx_line_axis_line_width**</span><span class="sxs-lookup"><span data-stu-id="73cdd-161">**gx_line_axis_line_width**</span></span>        | <span data-ttu-id="73cdd-162">가로 및 세로 축을 그리는 데 사용되는 선의 너비입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-162">Width of the line used to draw the horizontal and vertical axis</span></span> |
| <span data-ttu-id="73cdd-163">**gx_line_data_line_width**</span><span class="sxs-lookup"><span data-stu-id="73cdd-163">**gx_line_data_line_width**</span></span>        | <span data-ttu-id="73cdd-164">그린 데이터 줄의 너비입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-164">Width of the plotted data line</span></span> |
| <span data-ttu-id="73cdd-165">**gx_line_chart_axis_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-165">**gx_line_chart_axis_color**</span></span>       | <span data-ttu-id="73cdd-166">축 선을 그리는 데 사용되는 색의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-166">Resource ID of the color used to draw the axis lines</span></span> |
| <span data-ttu-id="73cdd-167">**gx_line_chart_line_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-167">**gx_line_chart_line_color**</span></span>       | <span data-ttu-id="73cdd-168">차트 데이터 줄을 그리는 데 사용되는 색의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-168">Resource ID of the color used to draw the chart data line</span></span> |

## <a name="gx_mouse_cursor_info"></a><span data-ttu-id="73cdd-169">GX_MOUSE_CURSOR_INFO</span><span class="sxs-lookup"><span data-stu-id="73cdd-169">GX_MOUSE_CURSOR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="73cdd-170">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-170">Definition</span></span>

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

### <a name="members"></a><span data-ttu-id="73cdd-171">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-171">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="73cdd-172">**gx_mouse_cursor_image_id**</span><span class="sxs-lookup"><span data-stu-id="73cdd-172">**gx_mouse_cursor_image_id**</span></span>       | <span data-ttu-id="73cdd-173">마우스 이미지의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-173">Resource ID of the mouse image</span></span> |
| <span data-ttu-id="73cdd-174">**gx_mouse_cursor_hotspot_x**</span><span class="sxs-lookup"><span data-stu-id="73cdd-174">**gx_mouse_cursor_hotspot_x**</span></span>      | <span data-ttu-id="73cdd-175">마우스 이미지의 왼쪽에서 마우스 이미지 핫스팟까지의 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-175">The offset from the left of the mouse image to the mouse image hotspot</span></span> |
| <span data-ttu-id="73cdd-176">**gx_mouse_cursor_hotspot_y**</span><span class="sxs-lookup"><span data-stu-id="73cdd-176">**gx_mouse_cursor_hotspot_y**</span></span>      | <span data-ttu-id="73cdd-177">마우스 이미지의 위쪽에서 마우스 이미지 핫스팟까지의 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-177">The offset from the top of the mouse image to the mouse image hotspot</span></span> |

## <a name="gx_pen_configuration"></a><span data-ttu-id="73cdd-178">GX_PEN_CONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="73cdd-178">GX_PEN_CONFIGURATION</span></span> 

### <a name="definition"></a><span data-ttu-id="73cdd-179">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-179">Definition</span></span>

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

### <a name="members"></a><span data-ttu-id="73cdd-180">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-180">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="73cdd-181">**gx_pen_configuration_min_drag_dist**</span><span class="sxs-lookup"><span data-stu-id="73cdd-181">**gx_pen_configuration_min_drag_dist**</span></span>       | <span data-ttu-id="73cdd-182">긋기 이벤트를 트리거할 GUIX 타이머 틱당 최소 끌기 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-182">The minimum drag distance per GUIX timer tick to trigger an FLICK event.</span></span> <span data-ttu-id="73cdd-183">GX_FIXED_VAL_MAKE를 호출하여 고정 소수점 데이터 형식 값을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-183">Call GX_FIXED_VAL_MAKE to make a fixed point data type value</span></span> |
| <span data-ttu-id="73cdd-184">**gx_pen_configuration_max_pen_speed_ticks**</span><span class="sxs-lookup"><span data-stu-id="73cdd-184">**gx_pen_configuration_max_pen_speed_ticks**</span></span> | <span data-ttu-id="73cdd-185">긋기 이벤트를 트리거하기 위한 GUIX 타이머 틱의 최대 끌기 속도입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-185">The maximum drag speed in GUIX timer ticks to trigger an FLICK event</span></span> | 

## <a name="gx_pixelmap_slider_info"></a><span data-ttu-id="73cdd-186">GX_PIXELMAP_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="73cdd-186">GX_PIXELMAP_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="73cdd-187">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-187">Definition</span></span>

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="73cdd-188">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-188">Members</span></span>

|                                                       |                                          |
| ----------------------------------------------------- | ---------------------------------------- |
| <span data-ttu-id="73cdd-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="73cdd-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span></span> | <span data-ttu-id="73cdd-190">니들 앞 배경을 채우기 위한 pixelmap의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-190">Resource ID of the pixelmap for filling the background before the needle.</span></span> <span data-ttu-id="73cdd-191">상단 배경 pixelmap을 설정하지 않은 경우 니들의 전후 배경을 채우는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-191">If upper background pixelmap is not set, it’s used for filling background both before and after the needle</span></span> |
| <span data-ttu-id="73cdd-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="73cdd-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span></span> | <span data-ttu-id="73cdd-193">니들 뒤 배경을 채우기 위한 pixelmap의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-193">Resource ID of the pixelmap for filling background after the needle</span></span> |
| <span data-ttu-id="73cdd-194">**gx_pixelmap_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="73cdd-194">**gx_pixelmap_slider_info_needle_pixelmap**</span></span>           | <span data-ttu-id="73cdd-195">니들 pixelmap의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-195">Resource ID of the needle pixelmap</span></span> |

## <a name="gx_progress_bar_info"></a><span data-ttu-id="73cdd-196">GX_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="73cdd-196">GX_PROGRESS_BAR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="73cdd-197">**정의**</span><span class="sxs-lookup"><span data-stu-id="73cdd-197">**Definition**</span></span>

```c
typedef struct GX_PROGRESS_BAR_INFO_STRUCT
{
    INT gx_progress_bar_info_min_val;
    INT gx_progress_bar_info_max_val;
    INT gx_progress_bar_info_current_val;
    GX_RESOURCE_ID gx_progress_bar_font_id;
    GX_RESOURCE_ID gx_progress_bar_normal_text_color;
    GX_RESOURCE_ID gx_progress_bar_selected_text_color;
    GX_RESOURCE_ID gx_progress_bar_disabled_text_color;
    GX_RESOURCE_ID gx_progress_bar_fill_pixelmap;
} GX_PROGRESS_BAR_INFO;
```

### <a name="members"></a><span data-ttu-id="73cdd-198">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-198">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="73cdd-199">**gx_progress_bar_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="73cdd-199">**gx_progress_bar_info_min_val**</span></span>             | <span data-ttu-id="73cdd-200">보고된 최소 값</span><span class="sxs-lookup"><span data-stu-id="73cdd-200">Minimum reported value</span></span> |
| <span data-ttu-id="73cdd-201">**gx_progress_bar_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="73cdd-201">**gx_progress_bar_info_max_val**</span></span>             | <span data-ttu-id="73cdd-202">보고된 최대 값</span><span class="sxs-lookup"><span data-stu-id="73cdd-202">Maximum reported value</span></span> |
| <span data-ttu-id="73cdd-203">**gx_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="73cdd-203">**gx_progress_bar_info_current_val**</span></span>         | <span data-ttu-id="73cdd-204">현재 값</span><span class="sxs-lookup"><span data-stu-id="73cdd-204">Current value</span></span> |
| <span data-ttu-id="73cdd-205">**gx_progress_bar_info_font_id**</span><span class="sxs-lookup"><span data-stu-id="73cdd-205">**gx_progress_bar_info_font_id**</span></span>             | <span data-ttu-id="73cdd-206">진행률 표시줄 위젯 내에서 선택적 텍스트 값을 그리는 데 사용되는 글꼴의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-206">Resource ID of the font, used to draw the optional text value within the progress bar widget</span></span>      |
| <span data-ttu-id="73cdd-207">**gx_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-207">**gx_progress_bar_normal_text_color**</span></span>        | <span data-ttu-id="73cdd-208">진행률 표시줄 위젯 내에서 선택적 텍스트 그리기를 정의하는 데 사용되는 표준 상태의 텍스트 색 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-208">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="73cdd-209">**gx_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-209">**gx_progress_bar_selected_text_color**</span></span>      | <span data-ttu-id="73cdd-210">위젯이 포커스를 얻을 때 진행률 표시줄 위젯 내에서 선택적 텍스트 그리기를 정의하는 데 사용되는 텍스트 색 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-210">Resource ID of the text color when the widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="73cdd-211">**gx_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-211">**gx_progress_bar_disabled_text_color**</span></span>      | <span data-ttu-id="73cdd-212">GX_STYLE_ENABLED가 활성 상태가 아닐 때 진행률 표시줄 위젯 내에서 선택적 텍스트 그리기를 정의하는 데 사용되는 텍스트 색 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-212">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="73cdd-213">**gx_progress_bar_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="73cdd-213">**gx_progress_bar_fill_pixelmap**</span></span>            | <span data-ttu-id="73cdd-214">배경 채우기를 위한 pixelmap의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-214">Resource ID of the pixelmap for background filling</span></span>|

## <a name="gx_radial_progress_bar_info"></a><span data-ttu-id="73cdd-215">GX_RADIAL_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="73cdd-215">GX_RADIAL_PROGRESS_BAR_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="73cdd-216">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-216">Definition</span></span>

```c
typedef struct GX_RADIAL_PROGRESS_BAR_INFO_STRUCT
{
    GX_VALUE       gx_radial_progress_bar_info_xcenter;
    GX_VALUE       gx_radial_progress_bar_info_ycenter;
    GX_VALUE       gx_radial_progress_bar_info_radius;
    GX_VALUE       gx_radial_progress_bar_info_current_val;
    GX_VALUE       gx_radial_progress_bar_info_anchor_val;
    GX_RESOURCE_ID gx_radial_progress_bar_info_font_id;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_disabled_text_color;
    GX_VALUE       gx_radial_progress_bar_info_normal_brush_width;
    GX_VALUE       gx_radial_progress_bar_info_selected_brush_width;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_brush_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_brush_color;
} GX_RADIAL_PROGRESS_BAR_INFO;
```

### <a name="members"></a><span data-ttu-id="73cdd-217">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-217">Members</span></span>

|                                                   |                                              |
| ------------------------------------------------- | -------------------------------------------- |
| <span data-ttu-id="73cdd-218">**gx_radial_progress_bar_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="73cdd-218">**gx_radial_progress_bar_info_xcenter**</span></span>           | <span data-ttu-id="73cdd-219">X좌표의 위젯 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-219">Widget position in x coordinate</span></span> |
| <span data-ttu-id="73cdd-220">**gx_radial_progress_bar_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="73cdd-220">**gx_radial_progress_bar_info_ycenter**</span></span>           | <span data-ttu-id="73cdd-221">Y좌표의 위젯 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-221">Widget position in y coordinate</span></span>  |
| <span data-ttu-id="73cdd-222">**gx_radial_progress_bar_info_radius**</span><span class="sxs-lookup"><span data-stu-id="73cdd-222">**gx_radial_progress_bar_info_radius**</span></span>            | <span data-ttu-id="73cdd-223">진행되는 원의 반경입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-223">Radius of the progress circle</span></span> |
| <span data-ttu-id="73cdd-224">**gx_radial_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="73cdd-224">**gx_radial_progress_bar_info_current_val**</span></span>       | <span data-ttu-id="73cdd-225">범위 [-360, 360]으로 제한되는 현재 값은 위쪽 원호의 엔드포인트와 앵커 위치 사이의 각도 델타를 나타냅니다. 음수 값을 사용하면 앵커 위치에서 시작하여 시계 방향으로 원호가 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-225">Current value, limited to the range [-360, 360], indicates the angular delta between the anchor position and the end point of the upper arc. Negative value causes the arc to be drawn in a clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="73cdd-226">값이 양수이면 앵커 위치에서 시작하여 시계 반대 방향으로 원호가 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-226">Positive value causes the arc to be drawn in a counter-clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="73cdd-227">애플리케이션은 표시되는 실제 값을 스케일링하여 진행률 표시줄 위젯에 각도 값을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-227">The application must scale the real-word value being indicated to assign an angular value to the progress bar widget</span></span> |
| <span data-ttu-id="73cdd-228">**gx_radial_progress_bar_anchor_val**</span><span class="sxs-lookup"><span data-stu-id="73cdd-228">**gx_radial_progress_bar_anchor_val**</span></span>             | <span data-ttu-id="73cdd-229">위쪽으로 진행되는 원호의 시작 각도입니다. 이 값은 오른쪽을 가리키는 0도와 위쪽을 가리키는 90도의 정수 각도로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-229">Starting angle of the upper progress arc. The value is defined in terms of integer degree with 0 degree pointing to the right and 90 degree indicating straight up position.</span></span> |
| <span data-ttu-id="73cdd-230">**gx_radial_progress_bar_font_id**</span><span class="sxs-lookup"><span data-stu-id="73cdd-230">**gx_radial_progress_bar_font_id**</span></span>                | <span data-ttu-id="73cdd-231">진행률 표시줄 위젯에 있는 선택적 텍스트 값을 그리는 데 사용되는 글꼴의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-231">Resource ID of the font used to draw the optional text value within the progress bar widget</span></span> |
| <span data-ttu-id="73cdd-232">**gx_radial_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-232">**gx_radial_progress_bar_normal_text_color**</span></span>      | <span data-ttu-id="73cdd-233">진행률 표시줄 위젯 내에서 선택적 텍스트 그리기를 정의하는 데 사용되는 표준 상태의 텍스트 색 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-233">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="73cdd-234">**gx_radial_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-234">**gx_radial_progress_bar_selected_text_color**</span></span>    |<span data-ttu-id="73cdd-235">위젯이 포커스를 얻을 때 진행률 표시줄 위젯 내에서 선택적 텍스트 그리기를 정의하는 데 사용되는 텍스트 색 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-235">Resource ID of the text color when widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="73cdd-236">**gx_radial_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-236">**gx_radial_progress_bar_disabled_text_color**</span></span>    | <span data-ttu-id="73cdd-237">GX_STYLE_ENABLED가 활성 상태가 아닐 때 진행률 표시줄 위젯 내에서 선택적 텍스트 그리기를 정의하는 데 사용되는 텍스트 색 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-237">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="73cdd-238">**gx_radial_progress_bar_normal_brush_width**</span><span class="sxs-lookup"><span data-stu-id="73cdd-238">**gx_radial_progress_bar_normal_brush_width**</span></span>     | <span data-ttu-id="73cdd-239">아래쪽으로 진행되는 원의 너비입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-239">Width of the lower progress circle</span></span> |
| <span data-ttu-id="73cdd-240">**gx_radial_progress_bar_selected_brush_width**</span><span class="sxs-lookup"><span data-stu-id="73cdd-240">**gx_radial_progress_bar_selected_brush_width**</span></span>   | <span data-ttu-id="73cdd-241">위쪽으로 진행되는 호의 너비입니다. 위쪽 호는 아래쪽 원보다 더 좁아지거나, 아래쪽 원과 같아지거나, 아래쪽 원보다 더 넓어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-241">Width of the upper progress arc, the upper arc may be narrower, the same as, or wider than the lower circle</span></span> |
| <span data-ttu-id="73cdd-242">**gx_radial_progress_bar_normal_brush_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-242">**gx_radial_progress_bar_normal_brush_color**</span></span>     | <span data-ttu-id="73cdd-243">아래쪽으로 진행되는 원을 채울 색의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-243">Resource ID of the color to fill lower progress circle</span></span> |
| <span data-ttu-id="73cdd-244">**gx_radial_progress_bar_selected_brush_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-244">**gx_radial_progress_bar_selected_brush_color**</span></span>   | <span data-ttu-id="73cdd-245">위쪽으로 진행되는 호를 채울 색의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-245">Resource ID of the color to fill upper progress arc</span></span> |

## <a name="gx_radial_slider_info"></a><span data-ttu-id="73cdd-246">GX_RADIAL_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="73cdd-246">GX_RADIAL_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="73cdd-247">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-247">Definition</span></span>

```c
typedef struct GX_RADIAL_SLIDER_INFO_STRUCT
{
    GX_VALUE       gx_radial_slider_info_xcenter;
    GX_VALUE       gx_radial_slider_info_ycenter;
    USHORT         gx_radial_slider_info_radius;
    USHORT         gx_radial_slider_info_track_width;
    GX_VALUE       gx_radial_slider_info_current_angle;
    GX_VALUE       gx_radial_slider_info_min_angle;
    GX_VALUE       gx_radial_slider_info_max_angle;
    GX_VALUE      *gx_radial_slider_info_angle_list;
    USHORT         gx_radial_slider_info_list_cont;
    GX_RESOURCE_ID gx_radial_slider_info_background_pixelmap;
    GX_RESOURCE_ID gx_radial_slider_info_needle_pixelmap;
} GX_RADIAL_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="73cdd-248">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-248">Members</span></span>

|                                               |                                                  |
| --------------------------------------------- | ------------------------------------------------ |
<span data-ttu-id="73cdd-249">**gx_radial_slider_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="73cdd-249">**gx_radial_slider_info_xcenter**</span></span>               | <span data-ttu-id="73cdd-250">슬라이더 위젯 왼쪽에서 슬라이더 니들의 회전 중심까지의 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-250">Distance from the left of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="73cdd-251">**gx_radial_slider_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="73cdd-251">**gx_radial_slider_info_ycenter**</span></span>             | <span data-ttu-id="73cdd-252">슬라이더 위젯 위쪽에서 슬라이더 니들의 회전 중심까지의 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-252">Distance from the top of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="73cdd-253">**gx_radial_slider_info_radius**</span><span class="sxs-lookup"><span data-stu-id="73cdd-253">**gx_radial_slider_info_radius**</span></span>              | <span data-ttu-id="73cdd-254">방사형 슬라이더 원의 반경입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-254">Radius of the radial slider circle</span></span> |
| <span data-ttu-id="73cdd-255">**gx_radial_slider_info_track_width**</span><span class="sxs-lookup"><span data-stu-id="73cdd-255">**gx_radial_slider_info_track_width**</span></span>         | <span data-ttu-id="73cdd-256">방사형 슬라이더 트랙의 너비입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-256">Width of radial slider track</span></span> |
| <span data-ttu-id="73cdd-257">**gx_radial_slider_info_current_angle**</span><span class="sxs-lookup"><span data-stu-id="73cdd-257">**gx_radial_slider_info_current_angle**</span></span>       | <span data-ttu-id="73cdd-258">현재 슬라이더 각도입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-258">Current slider angle</span></span> |
| <span data-ttu-id="73cdd-259">**gx_radial_slider_info_min_angle**</span><span class="sxs-lookup"><span data-stu-id="73cdd-259">**gx_radial_slider_info_min_angle**</span></span>           | <span data-ttu-id="73cdd-260">최소 슬라이더 각도입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-260">Minimum slider angle</span></span> |
| <span data-ttu-id="73cdd-261">**gx_radial_slider_info_max_angle**</span><span class="sxs-lookup"><span data-stu-id="73cdd-261">**gx_radial_slider_info_max_angle**</span></span>           | <span data-ttu-id="73cdd-262">최대 슬라이더 각도입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-262">Maximum slider angle</span></span> |
| <span data-ttu-id="73cdd-263">**gx_radial_slider_info_angle_list**</span><span class="sxs-lookup"><span data-stu-id="73cdd-263">**gx_radial_slider_info_angle_list**</span></span>          | <span data-ttu-id="73cdd-264">각도 값 목록은 앵커 각도를 정의합니다. 설정된 경우 슬라이더 각도는 정의된 앵커 각도 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-264">Angle value list, defines anchor angles, if set, slider angle can only be one of the defined anchor angles</span></span> |
| <span data-ttu-id="73cdd-265">**gx_radial_slider_info_list_count**</span><span class="sxs-lookup"><span data-stu-id="73cdd-265">**gx_radial_slider_info_list_count**</span></span>          | <span data-ttu-id="73cdd-266">앵커 각도의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-266">Number of anchor angles</span></span> |
| <span data-ttu-id="73cdd-267">**gx_radial_slider_info_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="73cdd-267">**gx_radial_slider_info_background_pixelmap**</span></span> | <span data-ttu-id="73cdd-268">배경 pixelmap의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-268">Resource ID of background pixelmap</span></span> |
| <span data-ttu-id="73cdd-269">**gx_radial_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="73cdd-269">**gx_radial_slider_info_needle_pixelmap**</span></span>     | <span data-ttu-id="73cdd-270">니들 pixelmap의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-270">Resource ID of needle pixelmap</span></span> |

## <a name="gx_rectangle"></a><span data-ttu-id="73cdd-271">GX_RECTANGLE</span><span class="sxs-lookup"><span data-stu-id="73cdd-271">GX_RECTANGLE</span></span>

### <a name="definition"></a><span data-ttu-id="73cdd-272">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-272">Definition</span></span>

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

### <a name="members"></a><span data-ttu-id="73cdd-273">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-273">Members</span></span>

|                                  |                         |
| -------------------------------- | ------------------------|
| <span data-ttu-id="73cdd-274">**gx_rectangle_left**</span><span class="sxs-lookup"><span data-stu-id="73cdd-274">**gx_rectangle_left**</span></span>            | <span data-ttu-id="73cdd-275">사각형의 왼쪽입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-275">Left of the rectangle</span></span>   |  
| <span data-ttu-id="73cdd-276">**gx_rectangle_top**</span><span class="sxs-lookup"><span data-stu-id="73cdd-276">**gx_rectangle_top**</span></span>             | <span data-ttu-id="73cdd-277">사각형의 위쪽입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-277">Top of the rectangle</span></span>    | 
| <span data-ttu-id="73cdd-278">**gx_rectangle_right**</span><span class="sxs-lookup"><span data-stu-id="73cdd-278">**gx_rectangle_right**</span></span>           | <span data-ttu-id="73cdd-279">사각형의 오른쪽입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-279">Right of the rectangle</span></span>  |
| <span data-ttu-id="73cdd-280">**gx_rectangle_bottom**</span><span class="sxs-lookup"><span data-stu-id="73cdd-280">**gx_rectangle_bottom**</span></span>          | <span data-ttu-id="73cdd-281">사각형의 아래쪽입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-281">Bottom of the rectangle</span></span> |

## <a name="gx_rich_text_fonts"></a><span data-ttu-id="73cdd-282">GX_RICH_TEXT_FONTS</span><span class="sxs-lookup"><span data-stu-id="73cdd-282">GX_RICH_TEXT_FONTS</span></span> 

### <a name="definition"></a><span data-ttu-id="73cdd-283">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-283">Definition</span></span>

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

### <a name="members"></a><span data-ttu-id="73cdd-284">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-284">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="73cdd-285">**gx_rich_text_fonts_normal_id**</span><span class="sxs-lookup"><span data-stu-id="73cdd-285">**gx_rich_text_fonts_normal_id**</span></span>   | <span data-ttu-id="73cdd-286">일반 텍스트 글꼴의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-286">Resource ID of normal text font</span></span> |
| <span data-ttu-id="73cdd-287">**gx_rich_text_fonts_bold_id**</span><span class="sxs-lookup"><span data-stu-id="73cdd-287">**gx_rich_text_fonts_bold_id**</span></span>     | <span data-ttu-id="73cdd-288">굵은 텍스트 글꼴의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-288">Resource ID of bold text font</span></span> |
| <span data-ttu-id="73cdd-289">**gx_rich_text_fonts_italic_id**</span><span class="sxs-lookup"><span data-stu-id="73cdd-289">**gx_rich_text_fonts_italic_id**</span></span>   | <span data-ttu-id="73cdd-290">기울임꼴 텍스트 글꼴의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-290">Resource ID of italic text font</span></span> |
| <span data-ttu-id="73cdd-291">**gx_rich_text_fonts_bold_italic_id**</span><span class="sxs-lookup"><span data-stu-id="73cdd-291">**gx_rich_text_fonts_bold_italic_id**</span></span> | <span data-ttu-id="73cdd-292">굵은 기울임꼴 텍스트 글꼴의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-292">Resource ID of bold italic text font</span></span> |

## <a name="gx_scroll_info"></a><span data-ttu-id="73cdd-293">GX_SCROLL_INFO</span><span class="sxs-lookup"><span data-stu-id="73cdd-293">GX_SCROLL_INFO</span></span> 
### <a name="definition"></a><span data-ttu-id="73cdd-294">**정의**</span><span class="sxs-lookup"><span data-stu-id="73cdd-294">**Definition**</span></span>

```c
typedef struct GX_SCROLL_INFO_STRUCT
{
    INT      gx_scroll_value;
    INT      gx_scroll_minimum;
    INT      gx_scroll_maximum;
    GX_VALUE gx_scroll_visible;
    GX_VALUE gx_scroll_increment;
} GX_SCROLL_INFO;
```

### <a name="members"></a><span data-ttu-id="73cdd-295">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-295">Members</span></span>

|                         |                               |
| ----------------------- | ----------------------------- |
| <span data-ttu-id="73cdd-296">**gx_scroll_value**</span><span class="sxs-lookup"><span data-stu-id="73cdd-296">**gx_scroll_value**</span></span>     | <span data-ttu-id="73cdd-297">현재 스크롤 위치</span><span class="sxs-lookup"><span data-stu-id="73cdd-297">Current scroll position</span></span>       |
| <span data-ttu-id="73cdd-298">**gx_scroll_minimum**</span><span class="sxs-lookup"><span data-stu-id="73cdd-298">**gx_scroll_minimum**</span></span>   | <span data-ttu-id="73cdd-299">보고된 최소 위치</span><span class="sxs-lookup"><span data-stu-id="73cdd-299">Minimum reported position</span></span>     |
| <span data-ttu-id="73cdd-300">**gx_scroll_maximum**</span><span class="sxs-lookup"><span data-stu-id="73cdd-300">**gx_scroll_maximum**</span></span>   | <span data-ttu-id="73cdd-301">보고된 최대 위치</span><span class="sxs-lookup"><span data-stu-id="73cdd-301">Maximum reported position</span></span>     |
| <span data-ttu-id="73cdd-302">**gx_scroll_visible**</span><span class="sxs-lookup"><span data-stu-id="73cdd-302">**gx_scroll_visible**</span></span>   | <span data-ttu-id="73cdd-303">부모 창 표시 범위</span><span class="sxs-lookup"><span data-stu-id="73cdd-303">Parent window visible range</span></span>   |
| <span data-ttu-id="73cdd-304">**gx_scroll_increment**</span><span class="sxs-lookup"><span data-stu-id="73cdd-304">**gx_scroll_increment**</span></span> | <span data-ttu-id="73cdd-305">스크롤 막대 최소 델타 값</span><span class="sxs-lookup"><span data-stu-id="73cdd-305">Scrollbar minimum delta value</span></span> |

## <a name="gx_scrollbar_appearance"></a><span data-ttu-id="73cdd-306">GX_SCROLLBAR_APPEARANCE</span><span class="sxs-lookup"><span data-stu-id="73cdd-306">GX_SCROLLBAR_APPEARANCE</span></span> 

### <a name="definition"></a><span data-ttu-id="73cdd-307">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-307">Definition</span></span>

```c
typedef struct GX_SCROLLBAR_APPEARANCE_STRUCT
{
    GX_VALUE       gx_scroll_width;
    GX_VALUE       gx_scroll_thumb_width;
    GX_VALUE       gx_scroll_thumb_travel_min;
    GX_VALUE       gx_scroll_thumb_travel_max;
    GX_UBYTE       gx_scroll_thumb_border_style;
    GX_RESOURCE_ID gx_scroll_fill_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_pixelmap;
    GX_RESOURCE_ID gx_scroll_up_pixelmap;
    GX_RESOURCE_ID gx_scroll_down_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_color;
    GX_RESOURCE_ID gx_scroll_thumb_border_color;
    GX_RESOURCE_ID gx_scroll_button_color;
} GX_SCROLLBAR_APPEARANCE;
```

### <a name="members"></a><span data-ttu-id="73cdd-308">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-308">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="73cdd-309">**gx_scroll_width**</span><span class="sxs-lookup"><span data-stu-id="73cdd-309">**gx_scroll_width**</span></span>                      | <span data-ttu-id="73cdd-310">스크롤 막대 위젯의 너비(픽셀)입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-310">Width of the scrollbar widget, in pixels</span></span> |
| <span data-ttu-id="73cdd-311">**gx_scroll_thumb_width**</span><span class="sxs-lookup"><span data-stu-id="73cdd-311">**gx_scroll_thumb_width**</span></span>                | <span data-ttu-id="73cdd-312">스크롤 막대에서 밀어 이동되는 엄지 단추의 너비(픽셀)입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-312">Width of the thumb button which slides on the scrollbar, in pixels.</span></span> <span data-ttu-id="73cdd-313">이 값은 일반적으로 전체 스크롤 막대 너비보다 더 작은 수의 픽셀입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-313">This value is usually some number of pixels less than the total scrollbar width</span></span> |
| <span data-ttu-id="73cdd-314">**gx_scroll_thumb_travel_min**</span><span class="sxs-lookup"><span data-stu-id="73cdd-314">**gx_scroll_thumb_travel_min**</span></span>           | <span data-ttu-id="73cdd-315">스크롤 막대의 끝에서 최소 엄지 단추 이동 지점까지의 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-315">Offset from the end of scrollbar to minimum thumb button travel point.</span></span> <span data-ttu-id="73cdd-316">이 제한을 사용하여 엄지 단추가 스크롤 막대의 맨 끝으로 이동하는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-316">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="73cdd-317">**gx_scroll_thumb_travel_max**</span><span class="sxs-lookup"><span data-stu-id="73cdd-317">**gx_scroll_thumb_travel_max**</span></span>           | <span data-ttu-id="73cdd-318">스크롤 막대의 끝에서 최대 엄지 단추 이동 지점까지의 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-318">Offset from the end of scrollbar to maximum thumb button travel point.</span></span> <span data-ttu-id="73cdd-319">이 제한을 사용하여 엄지 단추가 스크롤 막대의 맨 끝으로 이동하는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-319">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="73cdd-320">**gx_scroll_thumb_border_style**</span><span class="sxs-lookup"><span data-stu-id="73cdd-320">**gx_scroll_thumb_border_style**</span></span>         | <span data-ttu-id="73cdd-321">엄지 단추의 테두리 스타일입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-321">Border styles of thumb button</span></span> |
| <span data-ttu-id="73cdd-322">**gx_scroll_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="73cdd-322">**gx_scroll_fill_pixelmap**</span></span>              | <span data-ttu-id="73cdd-323">선택적 pixelmap ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-323">Optional pixelmap ID.</span></span> <span data-ttu-id="73cdd-324">이 pixelmap ID가 0이 아닌 경우 스크롤 막대는 이 pixelmap을 사용하여 스크롤 막대 배경을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-324">If this pixelmap ID is not zero, the scrollbar uses this pixelmap to draw the scrollbar background</span></span> |
| <span data-ttu-id="73cdd-325">**gx_scroll_thumb_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="73cdd-325">**gx_scroll_thumb_pixelmap**</span></span>             | <span data-ttu-id="73cdd-326">선택적 pixelmap ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-326">Optional pixelmap ID.</span></span> <span data-ttu-id="73cdd-327">이 pixelmap ID가 0이 아닌 경우 스크롤 막대 엄지 단추는 이 pixelmap을 사용하여 자신을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-327">If this pixelmap ID is not zero, the scrollbar thumb button uses this pixelmap to draw itself</span></span> |
| <span data-ttu-id="73cdd-328">**gx_scroll_up_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="73cdd-328">**gx_scroll_up_pixelmap**</span></span>                | <span data-ttu-id="73cdd-329">선택적 pixelmap ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-329">Optional pixelmap ID.</span></span> <span data-ttu-id="73cdd-330">이 pixelmap ID가 0이 아닌 경우 스크롤 막대는 이 pixelmap ID를 사용하여 스크롤 막대 왼쪽/위쪽 끝 단추를 그립니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-330">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar left/up end button</span></span> |
| <span data-ttu-id="73cdd-331">**gx_scroll_down_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="73cdd-331">**gx_scroll_down_pixelmap**</span></span>              | <span data-ttu-id="73cdd-332">선택적 pixelmap ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-332">Optional pixelmap ID.</span></span> <span data-ttu-id="73cdd-333">이 pixelmap ID가 0이 아닌 경우 스크롤 막대는 이 pixelmap ID를 사용하여 스크롤 막대 오른쪽/아래쪽 끝 단추를 그립니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-333">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar right/down end button</span></span> |
| <span data-ttu-id="73cdd-334">**gx_scroll_thumb_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-334">**gx_scroll_thumb_color**</span></span>                | <span data-ttu-id="73cdd-335">엄지 단추를 채우는 데 사용되는 색의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-335">Resource ID of color used to fill thumb button</span></span> |
| <span data-ttu-id="73cdd-336">**gx_scroll_thumb_border_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-336">**gx_scroll_thumb_border_color**</span></span>         | <span data-ttu-id="73cdd-337">엄지 단추의 테두리를 그리는 데 사용되는 색의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-337">Resource ID of color used to draw the border of thumb button</span></span> | 
| <span data-ttu-id="73cdd-338">**gx_scroll_button_color**</span><span class="sxs-lookup"><span data-stu-id="73cdd-338">**gx_scroll_button_color**</span></span>               | <span data-ttu-id="73cdd-339">스크롤 막대 끝 단추를 채우는 데 사용되는 색의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-339">Resource ID of color used to fill scrollbar end buttons</span></span> |

## <a name="gx_slider_info"></a><span data-ttu-id="73cdd-340">GX_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="73cdd-340">GX_SLIDER_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="73cdd-341">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-341">Definition</span></span>

```c
typedef struct GX_SLIDER_INFO_STRUCT
{
    INT      gx_slider_info_min_val;
    INT      gx_slider_info_max_val;
    INT      gx_slider_info_current_val;
    INT      gx_slider_info_increment;
    GX_VALUE gx_slider_info_min_travel;
    GX_VALUE gx_slider_info_max_travel;
    GX_VALUE gx_slider_info_needle_width;
    GX_VALUE gx_slider_info_needle_height;
    GX_VALUE gx_slider_info_needle_inset;
    GX_VALUE gx_slider_info_needle_hotspot_offset;
} GX_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="73cdd-342">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-342">Members</span></span>

|                                         |                                                        |
| --------------------------------------- | ------------------------------------------------------ |
| <span data-ttu-id="73cdd-343">**gx_slider_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="73cdd-343">**gx_slider_info_min_val**</span></span>              | <span data-ttu-id="73cdd-344">보고된 최소 값</span><span class="sxs-lookup"><span data-stu-id="73cdd-344">Minimum reported value</span></span> |
| <span data-ttu-id="73cdd-345">**gx_slider_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="73cdd-345">**gx_slider_info_max_val**</span></span>              | <span data-ttu-id="73cdd-346">보고된 최대 값</span><span class="sxs-lookup"><span data-stu-id="73cdd-346">Maximum reported value</span></span> |
| <span data-ttu-id="73cdd-347">**gx_slider_info_current_value**</span><span class="sxs-lookup"><span data-stu-id="73cdd-347">**gx_slider_info_current_value**</span></span>        | <span data-ttu-id="73cdd-348">현재 값</span><span class="sxs-lookup"><span data-stu-id="73cdd-348">Current value</span></span> |
| <span data-ttu-id="73cdd-349">**gx_slider_info_min_travel**</span><span class="sxs-lookup"><span data-stu-id="73cdd-349">**gx_slider_info_min_travel**</span></span>           | <span data-ttu-id="73cdd-350">니들 이동 제한</span><span class="sxs-lookup"><span data-stu-id="73cdd-350">Needle travel limit</span></span> |
| <span data-ttu-id="73cdd-351">**gx_slider_info_max_travel**</span><span class="sxs-lookup"><span data-stu-id="73cdd-351">**gx_slider_info_max_travel**</span></span>           | <span data-ttu-id="73cdd-352">니들 이동 제한</span><span class="sxs-lookup"><span data-stu-id="73cdd-352">Needle travel limit</span></span> |
| <span data-ttu-id="73cdd-353">**gx_slider_info_needle_width**</span><span class="sxs-lookup"><span data-stu-id="73cdd-353">**gx_slider_info_needle_width**</span></span>         | <span data-ttu-id="73cdd-354">니들 너비(픽셀)</span><span class="sxs-lookup"><span data-stu-id="73cdd-354">Needle width in pixel</span></span> |
| <span data-ttu-id="73cdd-355">**gx_slider_info_needle_height**</span><span class="sxs-lookup"><span data-stu-id="73cdd-355">**gx_slider_info_needle_height**</span></span>        | <span data-ttu-id="73cdd-356">니들 높이(픽셀)</span><span class="sxs-lookup"><span data-stu-id="73cdd-356">Needle height in pixel</span></span> |
|<span data-ttu-id="73cdd-357">**gx_slider_info_needle_inset**</span><span class="sxs-lookup"><span data-stu-id="73cdd-357">**gx_slider_info_needle_inset**</span></span>          | <span data-ttu-id="73cdd-358">니들 그리기 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-358">Needle draw position.</span></span> <span data-ttu-id="73cdd-359">GX_STYLE_SLIDER_VERTICAL이 설정된 경우 니들 그리기 시작 위치에서 슬라이더 왼쪽으로의 오프셋을 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-359">If GX_STYLE_SLIDER_VERTICAL is set, used to specify the offset from the needle draw start position to the slider left.</span></span> <span data-ttu-id="73cdd-360">그 밖에 니들 그리기 시작 위치에서 슬라이더 위쪽으로의 오프셋을 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-360">Else, used to specify the offset from the needle draw start position to the slider top.</span></span> |
| <span data-ttu-id="73cdd-361">**gx_slider_info_needle_hotspot_offset**</span><span class="sxs-lookup"><span data-stu-id="73cdd-361">**gx_slider_info_needle_hotspot_offset**</span></span> | <span data-ttu-id="73cdd-362">니들 핫스팟 오프셋은 니들 그리기 시작 위치에서 슬라이더 핫스팟으로의 오프셋을 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-362">Needle hotpot_offset, used to specify the offset from the needle draw start position to the slider hotspot.</span></span> |

## <a name="gx_sprite_frame"></a><span data-ttu-id="73cdd-363">GX_SPRITE_FRAME</span><span class="sxs-lookup"><span data-stu-id="73cdd-363">GX_SPRITE_FRAME</span></span>

### <a name="definition"></a><span data-ttu-id="73cdd-364">정의</span><span class="sxs-lookup"><span data-stu-id="73cdd-364">Definition</span></span>

```c
typedef struct GX_SPRITE_FRAME_STRUCT
{
    GX_RESOURCE_ID gx_sprite_frame_pixelmap;
    GX_VALUE gx_sprite_frame_x_offset;
    GX_VALUE gx_sprite_frame_y_offset;
    UINT gx_sprite_frame_delay;
    UINT gx_sprite_frame_background_operation;
    UCHAR gx_sprite_frame_alpha;
} GX_SPRITE_FRAME;
```

### <a name="members"></a><span data-ttu-id="73cdd-365">멤버</span><span class="sxs-lookup"><span data-stu-id="73cdd-365">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="73cdd-366">**gx_sprite_frame_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="73cdd-366">**gx_sprite_frame_pixelmap**</span></span>             | <span data-ttu-id="73cdd-367">이 프레임에 대해 표시할 pixelmap의 리소스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-367">Resource ID of the pixelmap to be displayed for this frame.</span></span> <span data-ttu-id="73cdd-368">이 ID는 0일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-368">The ID can be 0.</span></span> |
| <span data-ttu-id="73cdd-369">**gx_sprite_frame_x_offset**</span><span class="sxs-lookup"><span data-stu-id="73cdd-369">**gx_sprite_frame_x_offset**</span></span>             | <span data-ttu-id="73cdd-370">pixelmap을 표시할 왼쪽 스프라이트 위젯에서의 오프셋</span><span class="sxs-lookup"><span data-stu-id="73cdd-370">Offset from the sprite widget left to display the pixelmap</span></span> |
| <span data-ttu-id="73cdd-371">**gx_sprite_frame_y_offset**</span><span class="sxs-lookup"><span data-stu-id="73cdd-371">**gx_sprite_frame_y_offset**</span></span>             | <span data-ttu-id="73cdd-372">pixelmap을 표시할 위쪽 스프라이트 위젯에서의 오프셋</span><span class="sxs-lookup"><span data-stu-id="73cdd-372">Offset from the sprite widget top to display the pixelmap</span></span> |
| <span data-ttu-id="73cdd-373">**gx_sprite_frame_delay**</span><span class="sxs-lookup"><span data-stu-id="73cdd-373">**gx_sprite_frame_delay**</span></span>                | <span data-ttu-id="73cdd-374">이 프레임을 표시한 후 다음 스프라이트 프레임으로 이동하기 전까지의 지연 값(GUIX 타이머 틱)입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-374">Delay value, in GUIX timer ticks, after displaying this frame before advancing to the next sprite frame</span></span> |
| <span data-ttu-id="73cdd-375">**gx_sprite_frame_background_operation**</span><span class="sxs-lookup"><span data-stu-id="73cdd-375">**gx_sprite_frame_background_operation**</span></span> | <span data-ttu-id="73cdd-376">배경을 지울 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-376">Define how the background should be erased.</span></span> <span data-ttu-id="73cdd-377">이 매개 변수에 사용할 수 있는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-377">Possible values for this field are:</span></span><br /><span data-ttu-id="73cdd-378">GX_SPRITE_BACKGROUND_NO_ACTION: 프레임 간에 채우기 없음</span><span class="sxs-lookup"><span data-stu-id="73cdd-378">GX_SPRITE_BACKGROUND_NO_ACTION: No fill between frames</span></span><br /><span data-ttu-id="73cdd-379">GX_SPRITE_BACKGROUND_SOLID_FILL: 스프라이트 배경 다시 그리기</span><span class="sxs-lookup"><span data-stu-id="73cdd-379">GX_SPRITE_BACKGROUND_SOLID_FILL: Redraw sprite background</span></span><br /><span data-ttu-id="73cdd-380">GX_SPRITE_BACKGROUND_RESTORE: 이전 pixelmap 복원</span><span class="sxs-lookup"><span data-stu-id="73cdd-380">GX_SPRITE_BACKGROUND_RESTORE: Restore previous pixelmap</span></span> |
| <span data-ttu-id="73cdd-381">**gx_sprite_frame_alpha**</span><span class="sxs-lookup"><span data-stu-id="73cdd-381">**gx_sprite_frame_alpha**</span></span>                | <span data-ttu-id="73cdd-382">표시된 pixelmap에 추가할 알파 값입니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-382">Alpha value to be added to the displayed pixelmap.</span></span> <span data-ttu-id="73cdd-383">값 255는 추가 알파 값이 적용되지 않아야 함을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-383">The value 255 specifies that no extra alpha value should be imposed.</span></span> <span data-ttu-id="73cdd-384">Pixelmap에 알파 채널이 포함된 경우 이 알파 채널이 프레임 알파 값에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="73cdd-384">If the pixelmap includes an alpha channel, this alpha channel will be added to the frame alpha value.</span></span> |
