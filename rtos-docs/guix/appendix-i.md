---
title: 부록 I - GUIX 정보 구조
description: GUIX 정보 구조에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dc7775cdde8f1aa89ca650561713f54ac6c069eb
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550221"
---
# <a name="appendix-i---guix-information-structures"></a>부록 I - GUIX 정보 구조 

## <a name="gx_bidi_text_info"></a>GX_BIDI_TEXT_INFO 

### <a name="definition"></a>정의

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```
| 구성원 | Description |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_text_info_text**               | 순서를 다시 정렬할 텍스트입니다. |
| **gx_bidi_text_info_font**               | 텍스트를 표시하는 데 사용되는 글꼴입니다. 줄 바꿈이 필요하지 않은 경우 GX_NULL로 설정합니다. |
| **gx_bidi_text_info_display_width**      | 표시하는 데 사용할 수 있는 너비입니다. 줄 바꿈이 필요하지 않은 경우 -1로 설정합니다. |

## <a name="gx_bidi_resolved_text_info"></a>GX_BIDI_RESOLVED_TEXT_INFO 

### <a name="definition"></a>정의

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

| 구성원 | Description |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_resolved_text_info_text**             | 정렬된 양방향 텍스트 배열에 대한 포인터입니다. |
| **gx_bidi_resolved_text_info_total_lines**      | 한 단락에 대해 확인된 양방향 텍스트의 전체 줄입니다. |
| **gx_bidi_resolved_text_info_next**             | 다음 단락에 대해 확인된 양방향 텍스트 정보입니다. |

## <a name="gx_circular_gauge_info"></a>GX_CIRCULAR_GAUGE_INFO

### <a name="definition"></a>정의

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

| 구성원 | Description |
| ------------------------------------------------ | -------------------------------------------- |
| **gx_circular_gauge_info_animation_steps**       | 현재 니들 각도에서 새로 할당된 니들 각도로 이동할 때 니들이 이동하는 총 단계입니다. |
| **gx_circular_gauge_info_animation_delay**       | 애니메이션 단계 간에 지연될 GUIX 시계 틱 수입니다. |
| **gx_circular_gauge_info_needle_xpos**           | 계기 위젯 왼쪽에서 계기 니들의 회전 중심까지의 거리입니다. |
| **gx_circular_gauge_info_needle_ypos**           | 계기 위젯 위쪽에서 계기 니들의 회전 중심까지의 거리입니다. |
| **gx_circular_gauge_info_needle_xcor**           | 계기 이미지 왼쪽에서 계기 니들의 회전 중심까지의 거리입니다. |
| **gx_circular_gauge_info_needle_ycor**           | 계기 이미지 위쪽에서 계기 니들의 회전 중심까지의 거리입니다. |
| **gx_circular_gauge_info_needle_pixelmap**       | 계기 니들을 그리는 데 사용되는 pixelmap의 리소스 ID입니다. 이 이미지는 계기 위젯에서 임의 위치에 계기 니들을 표시하기 위해 필요에 따라 회전됩니다. |

아래 다이어그램은 xpos, ypos 및 xcor, ycor 좌표를 보여 줍니다.

![니들 Y 및 X 좌표 다이어그램](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a>GX_LINE_CHART_INFO

### <a name="definition"></a>정의

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

| 구성원 | Description |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_line_chart_min_val**          | 스케일링을 계산하는 데 사용되는 최소 데이터 값입니다.
| **gx_line_chart_max_val**          | 스케일링을 계산하는 데 사용되는 최대 데이터 값입니다. |
| **gx_line_chart_data**             | 정수 값 배열에 대한 포인터입니다. 꺾은선형 차트 위젯이 그리는 정수 값입니다. |
| **gx_line_<side>_margin**          | 실제 차트 렌더링 영역에 바인딩된 차트 창 바깥쪽에서의 오프셋입니다. 차트 축과 데이터 줄은 항상이 이러한 안쪽 경계 내에 표시되므로 애플리케이션에서 차트 창 내부, 문자 그래프 영역 외부에 레이블 및 기타 정보를 그릴 수 있습니다. |
| **gx_line_chart_max_data_count**   | 존재할 수 있는 데이터 값의 수입니다. 이 매개 변수는 데이터 요소를 그리는 데 사용되는 x축 스케일링 또는 간격을 계산하는 데 사용됩니다. |
| **gx_line_active_data_count**      | 데이터 배열에 실제로 표시되는 데이터 값의 개수입니다. 예를 들어, 꺾은선형 차트는 최대 100개 값을 그리기 위해 스케일링될 수 있지만, 특정 업데이트에서는 실제로 더 적은 수의 데이터 값이 있을 수 있습니다. |
| **gx_line_axis_line_width**        | 가로 및 세로 축을 그리는 데 사용되는 선의 너비입니다. |
| **gx_line_data_line_width**        | 그린 데이터 줄의 너비입니다. |
| **gx_line_chart_axis_color**       | 축 선을 그리는 데 사용되는 색의 리소스 ID입니다. |
| **gx_line_chart_line_color**       | 차트 데이터 줄을 그리는 데 사용되는 색의 리소스 ID입니다. |

## <a name="gx_mouse_cursor_info"></a>GX_MOUSE_CURSOR_INFO 

### <a name="definition"></a>정의

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

| 구성원 | Description |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_mouse_cursor_image_id**       | 마우스 이미지의 리소스 ID입니다. |
| **gx_mouse_cursor_hotspot_x**      | 마우스 이미지의 왼쪽에서 마우스 이미지 핫스팟까지의 오프셋입니다. |
| **gx_mouse_cursor_hotspot_y**      | 마우스 이미지의 위쪽에서 마우스 이미지 핫스팟까지의 오프셋입니다. |

## <a name="gx_pen_configuration"></a>GX_PEN_CONFIGURATION 

### <a name="definition"></a>정의

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

| 구성원 | Description |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_pen_configuration_min_drag_dist**       | 긋기 이벤트를 트리거할 GUIX 타이머 틱당 최소 끌기 거리입니다. GX_FIXED_VAL_MAKE를 호출하여 고정 소수점 데이터 형식 값을 만듭니다. |
| **gx_pen_configuration_max_pen_speed_ticks** | 긋기 이벤트를 트리거하기 위한 GUIX 타이머 틱의 최대 끌기 속도입니다. | 

## <a name="gx_pixelmap_slider_info"></a>GX_PIXELMAP_SLIDER_INFO 

### <a name="definition"></a>정의

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

| 구성원 | Description |
| ----------------------------------------------------- | ---------------------------------------- |
| **gx_pixelmap_slider_info_lower_background_pixelmap** | 니들 앞 배경을 채우기 위한 pixelmap의 리소스 ID입니다. 상단 배경 pixelmap을 설정하지 않은 경우 니들의 전후 배경을 채우는 데 사용됩니다. |
| **gx_pixelmap_slider_info_upper_background_pixelmap** | 니들 뒤 배경을 채우기 위한 pixelmap의 리소스 ID입니다. |
| **gx_pixelmap_slider_info_needle_pixelmap**           | 니들 pixelmap의 리소스 ID입니다. |

## <a name="gx_progress_bar_info"></a>GX_PROGRESS_BAR_INFO 

### <a name="definition"></a>**정의**

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

| 구성원 | Description |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_progress_bar_info_min_val**             | 보고된 최소 값 |
| **gx_progress_bar_info_max_val**             | 보고된 최대 값 |
| **gx_progress_bar_info_current_val**         | 현재 값 |
| **gx_progress_bar_info_font_id**             | 진행률 표시줄 위젯 내에서 선택적 텍스트 값을 그리는 데 사용되는 글꼴의 리소스 ID입니다.      |
| **gx_progress_bar_normal_text_color**        | 진행률 표시줄 위젯 내에서 선택적 텍스트 그리기를 정의하는 데 사용되는 표준 상태의 텍스트 색 리소스 ID입니다. |
| **gx_progress_bar_selected_text_color**      | 위젯이 포커스를 얻을 때 진행률 표시줄 위젯 내에서 선택적 텍스트 그리기를 정의하는 데 사용되는 텍스트 색 리소스 ID입니다. |
| **gx_progress_bar_disabled_text_color**      | GX_STYLE_ENABLED가 활성 상태가 아닐 때 진행률 표시줄 위젯 내에서 선택적 텍스트 그리기를 정의하는 데 사용되는 텍스트 색 리소스 ID입니다. |
| **gx_progress_bar_fill_pixelmap**            | 배경 채우기를 위한 pixelmap의 리소스 ID입니다.|

## <a name="gx_radial_progress_bar_info"></a>GX_RADIAL_PROGRESS_BAR_INFO

### <a name="definition"></a>정의

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

| 구성원 | Description |
| ------------------------------------------------- | -------------------------------------------- |
| **gx_radial_progress_bar_info_xcenter**           | X좌표의 위젯 위치입니다. |
| **gx_radial_progress_bar_info_ycenter**           | Y좌표의 위젯 위치입니다.  |
| **gx_radial_progress_bar_info_radius**            | 진행되는 원의 반경입니다. |
| **gx_radial_progress_bar_info_current_val**       | 범위 [-360, 360]으로 제한되는 현재 값은 위쪽 원호의 엔드포인트와 앵커 위치 사이의 각도 델타를 나타냅니다. 음수 값을 사용하면 앵커 위치에서 시작하여 시계 방향으로 원호가 그려집니다. 값이 양수이면 앵커 위치에서 시작하여 시계 반대 방향으로 원호가 그려집니다. 애플리케이션은 표시되는 실제 값을 스케일링하여 진행률 표시줄 위젯에 각도 값을 할당해야 합니다. |
| **gx_radial_progress_bar_anchor_val**             | 위쪽으로 진행되는 원호의 시작 각도입니다. 이 값은 오른쪽을 가리키는 0도와 위쪽을 가리키는 90도의 정수 각도로 정의됩니다. |
| **gx_radial_progress_bar_font_id**                | 진행률 표시줄 위젯에 있는 선택적 텍스트 값을 그리는 데 사용되는 글꼴의 리소스 ID입니다. |
| **gx_radial_progress_bar_normal_text_color**      | 진행률 표시줄 위젯 내에서 선택적 텍스트 그리기를 정의하는 데 사용되는 표준 상태의 텍스트 색 리소스 ID입니다. |
| **gx_radial_progress_bar_selected_text_color**    |위젯이 포커스를 얻을 때 진행률 표시줄 위젯 내에서 선택적 텍스트 그리기를 정의하는 데 사용되는 텍스트 색 리소스 ID입니다. |
| **gx_radial_progress_bar_disabled_text_color**    | GX_STYLE_ENABLED가 활성 상태가 아닐 때 진행률 표시줄 위젯 내에서 선택적 텍스트 그리기를 정의하는 데 사용되는 텍스트 색 리소스 ID입니다. |
| **gx_radial_progress_bar_normal_brush_width**     | 아래쪽으로 진행되는 원의 너비입니다. |
| **gx_radial_progress_bar_selected_brush_width**   | 위쪽으로 진행되는 호의 너비입니다. 위쪽 호는 아래쪽 원보다 더 좁아지거나, 아래쪽 원과 같아지거나, 아래쪽 원보다 더 넓어질 수 있습니다. |
| **gx_radial_progress_bar_normal_brush_color**     | 아래쪽으로 진행되는 원을 채울 색의 리소스 ID입니다. |
| **gx_radial_progress_bar_selected_brush_color**   | 위쪽으로 진행되는 호를 채울 색의 리소스 ID입니다. |

## <a name="gx_radial_slider_info"></a>GX_RADIAL_SLIDER_INFO 

### <a name="definition"></a>정의

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

| 구성원 | Description |
| --------------------------------------------- | ------------------------------------------------ |
**gx_radial_slider_info_xcenter**               | 슬라이더 위젯 왼쪽에서 슬라이더 니들의 회전 중심까지의 거리입니다. |
| **gx_radial_slider_info_ycenter**             | 슬라이더 위젯 위쪽에서 슬라이더 니들의 회전 중심까지의 거리입니다. |
| **gx_radial_slider_info_radius**              | 방사형 슬라이더 원의 반경입니다. |
| **gx_radial_slider_info_track_width**         | 방사형 슬라이더 트랙의 너비입니다. |
| **gx_radial_slider_info_current_angle**       | 현재 슬라이더 각도입니다. |
| **gx_radial_slider_info_min_angle**           | 최소 슬라이더 각도입니다. |
| **gx_radial_slider_info_max_angle**           | 최대 슬라이더 각도입니다. |
| **gx_radial_slider_info_angle_list**          | 각도 값 목록은 앵커 각도를 정의합니다. 설정된 경우 슬라이더 각도는 정의된 앵커 각도 중 하나일 수 있습니다. |
| **gx_radial_slider_info_list_count**          | 앵커 각도의 수입니다. |
| **gx_radial_slider_info_background_pixelmap** | 배경 pixelmap의 리소스 ID입니다. |
| **gx_radial_slider_info_needle_pixelmap**     | 니들 pixelmap의 리소스 ID입니다. |

## <a name="gx_rectangle"></a>GX_RECTANGLE

### <a name="definition"></a>정의

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

| 구성원 | Description |
| -------------------------------- | ------------------------|
| **gx_rectangle_left**            | 사각형의 왼쪽입니다.   |  
| **gx_rectangle_top**             | 사각형의 위쪽입니다.    | 
| **gx_rectangle_right**           | 사각형의 오른쪽입니다.  |
| **gx_rectangle_bottom**          | 사각형의 아래쪽입니다. |

## <a name="gx_rich_text_fonts"></a>GX_RICH_TEXT_FONTS 

### <a name="definition"></a>정의

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

| 구성원 | Description |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_rich_text_fonts_normal_id**   | 일반 텍스트 글꼴의 리소스 ID입니다. |
| **gx_rich_text_fonts_bold_id**     | 굵은 텍스트 글꼴의 리소스 ID입니다. |
| **gx_rich_text_fonts_italic_id**   | 기울임꼴 텍스트 글꼴의 리소스 ID입니다. |
| **gx_rich_text_fonts_bold_italic_id** | 굵은 기울임꼴 텍스트 글꼴의 리소스 ID입니다. |

## <a name="gx_scroll_info"></a>GX_SCROLL_INFO 
### <a name="definition"></a>**정의**

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

| 구성원 | Description |
| ----------------------- | ----------------------------- |
| **gx_scroll_value**     | 현재 스크롤 위치       |
| **gx_scroll_minimum**   | 보고된 최소 위치     |
| **gx_scroll_maximum**   | 보고된 최대 위치     |
| **gx_scroll_visible**   | 부모 창 표시 범위   |
| **gx_scroll_increment** | 스크롤 막대 최소 델타 값 |

## <a name="gx_scrollbar_appearance"></a>GX_SCROLLBAR_APPEARANCE 

### <a name="definition"></a>정의

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

| 구성원 | Description |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_scroll_width**                      | 스크롤 막대 위젯의 너비(픽셀)입니다. |
| **gx_scroll_thumb_width**                | 스크롤 막대에서 밀어 이동되는 엄지 단추의 너비(픽셀)입니다. 이 값은 일반적으로 전체 스크롤 막대 너비보다 더 작은 수의 픽셀입니다. |
| **gx_scroll_thumb_travel_min**           | 스크롤 막대의 끝에서 최소 엄지 단추 이동 지점까지의 오프셋입니다. 이 제한을 사용하여 엄지 단추가 스크롤 막대의 맨 끝으로 이동하는 것을 방지할 수 있습니다. |
| **gx_scroll_thumb_travel_max**           | 스크롤 막대의 끝에서 최대 엄지 단추 이동 지점까지의 오프셋입니다. 이 제한을 사용하여 엄지 단추가 스크롤 막대의 맨 끝으로 이동하는 것을 방지할 수 있습니다. |
| **gx_scroll_thumb_border_style**         | 엄지 단추의 테두리 스타일입니다. |
| **gx_scroll_fill_pixelmap**              | 선택적 pixelmap ID입니다. 이 pixelmap ID가 0이 아닌 경우 스크롤 막대는 이 pixelmap을 사용하여 스크롤 막대 배경을 그립니다. |
| **gx_scroll_thumb_pixelmap**             | 선택적 pixelmap ID입니다. 이 pixelmap ID가 0이 아닌 경우 스크롤 막대 엄지 단추는 이 pixelmap을 사용하여 자신을 그립니다. |
| **gx_scroll_up_pixelmap**                | 선택적 pixelmap ID입니다. 이 pixelmap ID가 0이 아닌 경우 스크롤 막대는 이 pixelmap ID를 사용하여 스크롤 막대 왼쪽/위쪽 끝 단추를 그립니다. |
| **gx_scroll_down_pixelmap**              | 선택적 pixelmap ID입니다. 이 pixelmap ID가 0이 아닌 경우 스크롤 막대는 이 pixelmap ID를 사용하여 스크롤 막대 오른쪽/아래쪽 끝 단추를 그립니다. |
| **gx_scroll_thumb_color**                | 엄지 단추를 채우는 데 사용되는 색의 리소스 ID입니다. |
| **gx_scroll_thumb_border_color**         | 엄지 단추의 테두리를 그리는 데 사용되는 색의 리소스 ID입니다. | 
| **gx_scroll_button_color**               | 스크롤 막대 끝 단추를 채우는 데 사용되는 색의 리소스 ID입니다. |

## <a name="gx_slider_info"></a>GX_SLIDER_INFO

### <a name="definition"></a>정의

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

| 구성원 | Description |
| --------------------------------------- | ------------------------------------------------------ |
| **gx_slider_info_min_val**              | 보고된 최소 값 |
| **gx_slider_info_max_val**              | 보고된 최대 값 |
| **gx_slider_info_current_value**        | 현재 값 |
| **gx_slider_info_min_travel**           | 니들 이동 제한 |
| **gx_slider_info_max_travel**           | 니들 이동 제한 |
| **gx_slider_info_needle_width**         | 니들 너비(픽셀) |
| **gx_slider_info_needle_height**        | 니들 높이(픽셀) |
|**gx_slider_info_needle_inset**          | 니들 그리기 위치입니다. GX_STYLE_SLIDER_VERTICAL이 설정된 경우 니들 그리기 시작 위치에서 슬라이더 왼쪽으로의 오프셋을 지정하는 데 사용됩니다. 그 밖에 니들 그리기 시작 위치에서 슬라이더 위쪽으로의 오프셋을 지정하는 데 사용됩니다. |
| **gx_slider_info_needle_hotspot_offset** | 니들 핫스팟 오프셋은 니들 그리기 시작 위치에서 슬라이더 핫스팟으로의 오프셋을 지정하는 데 사용됩니다. |

## <a name="gx_sprite_frame"></a>GX_SPRITE_FRAME

### <a name="definition"></a>정의

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

| 구성원 | Description |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_sprite_frame_pixelmap**             | 이 프레임에 대해 표시할 pixelmap의 리소스 ID입니다. 이 ID는 0일 수 있습니다. |
| **gx_sprite_frame_x_offset**             | pixelmap을 표시할 왼쪽 스프라이트 위젯에서의 오프셋 |
| **gx_sprite_frame_y_offset**             | pixelmap을 표시할 위쪽 스프라이트 위젯에서의 오프셋 |
| **gx_sprite_frame_delay**                | 이 프레임을 표시한 후 다음 스프라이트 프레임으로 이동하기 전까지의 지연 값(GUIX 타이머 틱)입니다. |
| **gx_sprite_frame_background_operation** | 배경을 지울 방법을 정의합니다. 이 매개 변수에 사용할 수 있는 값은 다음과 같습니다.<br />GX_SPRITE_BACKGROUND_NO_ACTION: 프레임 간에 채우기 없음<br />GX_SPRITE_BACKGROUND_SOLID_FILL: 스프라이트 배경 다시 그리기<br />GX_SPRITE_BACKGROUND_RESTORE: 이전 pixelmap 복원 |
| **gx_sprite_frame_alpha**                | 표시된 pixelmap에 추가할 알파 값입니다. 값 255는 추가 알파 값이 적용되지 않아야 함을 지정합니다. Pixelmap에 알파 채널이 포함된 경우 이 알파 채널이 프레임 알파 값에 추가됩니다. |
