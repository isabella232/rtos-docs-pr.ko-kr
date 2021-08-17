---
title: 챕터 5 - GUIX 디스플레이 드라이버
description: GUIX 디스플레이 드라이버는 추상 드로잉 캔버스와 물리적 디스플레이 하드웨어 간의 소프트웨어 인터페이스를 정의합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 804187ce8562e274205e97448da77d29f99016072c137cb3c4f1f42dac58c432
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788544"
---
# <a name="chapter-5---guix-display-drivers"></a>챕터 5 - GUIX 디스플레이 드라이버

GUIX 디스플레이 드라이버는 추상 드로잉 캔버스와 물리적 디스플레이 하드웨어 간의 소프트웨어 인터페이스를 정의합니다. GUIX 디스플레이 드라이버는 캔버스 메모리의 픽셀 색 정보를 실제로 변경하고 캔버스 메모리를 이중 버퍼 시스템의 물리적 디스플레이 프레임 버퍼로 전송하는 최저 수준의 그리기 기능을 구현합니다.

GUIX 디스플레이 드라이버는 물리적 디스플레이 매개 변수와 낮은 수준의 드라이버 기능에 대한 함수 포인터 세트를 포함하는 구조로 정의됩니다. 이러한 간접 함수 포인터를 사용하면 추상 캔버스 및 위젯 그리기 함수가 하드웨어 세부 정보와 완전히 별개의 것으로 만듭니다.

GUIX는 지원되는 각 색 깊이 및 색 형식에 대해 완벽하고 완전한 기능을 갖춘 기본 그리기 함수 세트를 제공합니다. 특정 하드웨어 가속 기능이나 기타 하드웨어 관련 고려 사항 없이 디스플레이 드라이버를 구현할 때 이러한 기본 그리기 함수는 일반적으로 최종 드라이버 구현에 충분합니다. 이렇게 간단한 드라이버의 경우 일반적으로 드라이버 소프트웨어에 구현되어야 하는 유일한 함수는 하드웨어 디바이스를 구성하는 함수입니다. 여기에는 LCD 디스플레이 클럭, 디스플레이 치수 등을 정의하기 위해 다양한 하드웨어 레지스터를 초기화하는 것이 포함됩니다. 다른 모든 함수의 경우 드라이버 구현은 원하는 색 깊이 및 형식에 대한 기본 함수 구현에 대해 간단히 GX_DISPLAY 함수 포인터를 초기화합니다.

사용자 정의 디스플레이 드라이버를 구현할 때 가장 좋은 방법은 먼저 지원하려는 색 농도에 대한 기본 소프트웨어 구현으로 디스플레이 드라이버 그리기 함수 포인터를 초기화한 다음, 사용자 정의 함수 구현(있는 경우)을 호출할 함수 포인터를 대체하는 것입니다. 이를 지원하기 위해 지원되는 각 색 깊이와 형식에 사용할 수 있는 기본 설치 함수가 있습니다. 예를 들어 16비트 5:6:5 형식의 RGB 디스플레이 드라이버를 작성하는 경우 사용자 지정 드라이버가 일반적으로 수행하는 첫 번째 작업은 이 색 농도에 대한 일반 설정 루틴을 호출하는 것입니다.

UINT my_custom_565_display_driver(GX_DISPLAY *display)

```c
{
      
      // perform standard function pointer setup
      
      _gx_display_driver_565rgb_setup(display, GX_NULL,
      
             my_buffertoggle);

}
```

위의 매개 변수 my_buffer_toggle은 디스플레이 드라이버 버퍼 전환 기능에 대한 포인터입니다(드라이버가 단일 버퍼이고 하드웨어 프레임 버퍼에 직접 그릴 경우 GX_NULL일 수 있음).

사용자 정의 디스플레이 드라이버를 쓰는 경우 사용자 정의 드라이버 원본에 gx_display.h 헤더 파일을 포함해야 합니다. 이 파일은 애플리케이션 수준 소프트웨어에서 사용할 수 없는 내부 사용 헤더 파일입니다.

GUIX 디스플레이 수준 그리기 함수는 **GX_DRAW_CONTEXT** 구조에 대한 포인터를 입력으로 수신합니다. **GX_DRAW_CONTEXT**  구조는 사용 중인 브러시 및 색상과 함께 현재 그리기 작업에 대한 클리핑 좌표를 정의합니다. 각 그리기 함수는 함수 요구 사항에 맞는 추가 매개 변수를 입력으로 수신합니다.

**GX_DISPLAY** 드라이버 진입점의 서명은 다음과 같이 정의됩니다.

```c
UINT <device>_graphics_driver_<format>(GX_DISPLAY *diplay)
```

이 함수의 이름은 완전히 구현자에 따라 결정되지만 GUIX와 함께 제공되는 드라이버의 규칙은 위의 <device> 필드에 하드웨어 관련 디바이스 이름을 사용하고 <format> 필드에 색 형식을 사용하는 것입니다.

이 함수는 입력으로 제공된 **GX_DISPLAY** 구조를 초기화하고 필요한 하드웨어 설정을 수행해야 합니다. **GX_DISPLAY** 구조체에는 다음 필드가 포함되어 있습니다.

| &nbsp; |
| --- | --- |
| ULONG gx_display_id <br/> 이 필드는 특정 드라이버의 인스턴스를 두 개 이상 만드는 경우 애플리케이션에서 사용되는 필드입니다. |
| CHAR *gx_display_name <br/> 드라이버를 식별하는 데 사용되는 선택적 이름입니다. |
| GX_DISPLAY *gx_display_created_next <br/> 이 필드는 GUIX에 의해 초기화되며 모든 GX_DISPLAY 인스턴스 목록을 만들고 유지하는 데 사용됩니다. |
| GX_DISPLAY *gx_display_created_previous <br/> 이 필드는 GUIX에 의해 초기화되며 모든 GX_DISPLAY 인스턴스 목록을 만들고 유지하는 데 사용됩니다. |
| GX_VALUE gx_display_color_format <br/> 이 필드는 이 드라이버에서 지원하는 그래픽 데이터 형식을 반영해야 합니다. 색 형식 유형은 gx_api 헤더 파일에 정의되어 있습니다. |
| GX_VALUE gx_display_width <br/> 이 필드는 실제 디스플레이 너비(픽셀)를 유지하도록 초기화해야 합니다. |
| GX_VALUE gx_display_height <br/> 이 필드는 실제 디스플레이 높이(픽셀)를 유지하도록 초기화해야 합니다. |
| GX_COLOR *gx_display_color_table <br/> 색상 ID 값을 색 형식 특정 색 값으로 변환하는 데 사용되는 테이블의 포인터입니다. |
| GX_PIXELMAP *gx_display_pixelmap_table <br/> 이 디스플레이에 대한 활성 팩셀 맵 테이블에 대한 포인터입니다. |
| GX_FONT *gx_display_font_table <br/> 이 디스플레이에 대한 활성 글꼴 테이블에 대한 포인터입니다. |
| GX_COLOR *gx_display_palette <br/> 팔레트 모드 드라이버의 경우 활성 색상 팔레트에 대한 포인터입니다. 색상 팔레트를 사용하지 않는 드라이버의 경우 이 포인터는 GX_NULL입니다. |
| UINT gx_display_pixelmap_table_size <br/> 활성 픽셀 맵 테이블의 항목 수입니다. |
| UINT gx_display_font_table_size <br/> 활성 글꼴 테이블의 항목 수입니다. |
| UINT gx_display_palette_size <br/> 색상 팔레트에 있는 항목의 수입니다(있는 경우). |
| ULONG gx_display_handle <br/> 디스플레이를 지정하는 고유 식별자 또는 *핸들* 입니다.
| UINT gx_display_driver_ready <br/> 이 필드는 드라이버를 사용할 준비가 되면 GUIX에 신호를 보내는 데 사용됩니다. 일부 경우에는 드라이버에서 몇 가지 수준의 초기화 및 구성이 필요할 수 있으며, 그 동안 GUIX는 드라이버를 활용하지 않아야 합니다. 드라이버가 그리기 요청을 처리할 준비가 되면 이 플래그를 1로 설정해야 합니다. |
| VOID *gx_display_driver_data <br/> 이 필드는 드라이버 구현에 사용됩니다. 드라이버가 GX_DISPLAY 구조에서 사용할 수 없는 추가 정보를 만들어 참조해야 하는 경우, 드라이버는 이 구조 필드를 사용하여 이 추가 데이터를 위한 공간을 할당하고 가리켜야 합니다. 드라이버별 추가 데이터의 예로는 드라이버가 사용하는 DMA 채널이나 디스플레이 프레임 버퍼가 연결된 SPI 채널이 있습니다. |
| VOID (*gx_display_driver_drawing_initiate)(struct GX_DISPLAY_STRUCT *display, struct GX_CANVAS_STRUCT *canvas) <br/> NULL이 아닌 경우 gx_canvas_drawing_initiate 함수에 의해 호출되는 함수 포인터입니다. 그래픽 가속기 또는 하드웨어 그래픽 디스플레이 목록을 사용하는 디스플레이 드라이버의 경우 이 함수를 사용하여 새 디스플레이 목록을 시작할 수 있습니다. 이 함수 포인터는 NULL일 수 있습니다. |
| VOID (*gx_display_driver_palette_set)(struct GX_DISPLAY_STRUCT *display, GX_COLOR *palette, INT count) <br/> 색상 팔레트를 설치하는 함수에 대한 포인터입니다. 드라이버가 팔레트(색 조회 테이블 또는 CLUT 라고도 함) 모드에서 작동하지 않는 한 이 함수는 NULL입니다. |
| VOID (*gx_display_driver_simple_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> 앤티앨리어싱없이 일반 선 그리기를 구현하는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_simple_wide_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> 앤티앨리어싱없이 일반 굵은 선 그리기를 구현하는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_anti_aliased_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> 앤티앨리어싱된 일반 선 그리기를 구현하는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_anti_aliased_wide_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> 앤티앨리어싱된 일반 굵은 선 그리기를 구현하는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_horizonal_line_draw)(GX_DRAW_CONTECT *context, INT x1, INT x2, INT y) <br/> 수평선 그리기의 특수한 경우를 구현하는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_horizonal_pixelmap_line_draw)(GX_DRAW_CONTECT *context, INT x1, INT x2, INT y, GX_PIXELMAP *map) <br/> 단일 픽셀 맵 행 그리기를 구현하는 함수에 대한 포인터입니다. 이 함수는 패턴 채우기 도형에 내부적으로 사용됩니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_vertical_line_draw)(GX_DRAW_CONTECT *context, INT y1, INT y2, INT x) <br/> 수평선 그리기의 특수한 경우를 구현하는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_horizonal_pattern_line_draw)(GX_DRAW_CONTECT *context, INT x1, INT x2, INT y) <br/> 수평 패턴 선 그리기를 구현하는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_vertical_pattern_line_draw)(GX_DRAW_CONTECT *context, INT y1, INT y2, INT x) <br/> 수직 패턴 선 그리기를 구현하는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_canvas_copy)(struct GX_CANVAS_STRUCT *source, struct GX_CANVAS_STRUCT *dest) <br/> 한 캔버스에서 다른 캔버스로 캔버스 데이터를 복사하는 함수에 대한 포인터입니다. 원본 캔버스 유효하지 않은 사각형은 복사 영역을 정의하는 데 사용됩니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_canvas_blend)(struct GX_CANVAS_STRUCT *source, struct GX_CANVAS_STRUCT *dest) <br/> 원본 캔버스의 캔버스 데이터를 대상 캔버스의 기존 데이터와 알파 혼합하는 함수에 대한 포인터입니다. 원본 캔버스 유효하지 않은 사각형은 혼합 영역을 정의하는 데 사용됩니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_pixelmap_blend)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp, GX_UBYTE alpha) <br/> 그리기 컨텍스트로 정의된 배경 캔버스에서 픽셀 맵을 혼합하는 함수에 대한 포인터입니다. 제공된 알파 값은 픽셀 맵 데이터에 포함된 알파 채널에 추가될 수 있습니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_pixelmap_draw)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> 그리기 컨텍스트에 의해 정의된 캔버스에 픽셀 맵을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_jpeg_draw)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> jpg 이미지를 디코딩하여 캔버스에 직접 렌더링하는 함수에 대한 포인터입니다. 이 함수는 GX_SOFTWARE_DECODER_SUPPORT가 정의된 경우에만 제공됩니다. 이 함수 포인터는 NULL일 수 있습니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_png_draw)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> png 이미지를 디코딩하여 캔버스에 직접 렌더링하는 함수에 대한 포인터입니다. 이 함수는 GX_SOFTWARE_DECODER_SUPPORT가 정의된 경우에만 제공됩니다. 이 함수 포인터는 NULL일 수 있습니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_pixelmap_rotate)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp INT angle, INT rot_cx, INT rot_cy) <br/> 픽셀 맵을 회전하고 결과를 캔버스에 직접 렌더링하는 함수에 대한 포인터입니다. 이 함수는 지원되는 각 색 깊이 및 색 형식에 대해 제공되는 이 함수의 gx_canvas_pixelmap_rotate APIDefault 구현에 의해 호출됩니다. |
| VOID *gx_display_driver_pixel_write)(GX_DRAW_CONTEXT *context, INT x, INT y, GX_COLOR color) <br/> 캔버스 메모리에 한 픽셀을 쓰는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. <br/>
| VOID *gx_display_driver_block_move)(GX_DRAW_CONTEXT *context,GX_RECTANGLE *block, INT xshift, INT yshift) <br/> 캔버스 내에서 픽셀 블록을 이동하는 함수에 대한 포인터입니다. 이 함수는 주로 창 내용을 빠르게 스크롤하는 데 사용됩니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_pixel_blend)(GX_DRAW_CONTEXT *context, INT x, INT y, GX_COLOR color, GX_UBYTE alpha) <br/> 이 함수는 들어오는 픽셀 색상 값과 캔버스 메모리의 기존 색상 값을 x, y 위치에서 알파 혼합하는 데 사용됩니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| GX_COLOR (*gx_display_driver_native_color_get)(GX_COLOR rawcolor) <br/> 이 함수는 GUIX에서 내부적으로 사용하는 32비트 A:R:G:B 색 형식의 색을 캔버스 및 디스플레이의 기본 색 형식으로 변환합니다. 낮은 색 깊이에서 실행되는 디스플레이 드라이버의 경우 일부 색 정보가 손실될 수 있습니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| USHORT (*gx_display_driver_row_pitch_get)(USHORT width) <br/> 요청한 캔버스 너비가 지정된 경우 그래픽 데이터의 한 행에 대한 바이트 수 또는 스트라이드를 반환합니다. 이 함수는 캔버스를 만드는 데 필요한 메모리 영역의 크기를 계산하는 데 사용됩니다. 하드웨어 스캔 선 맞춤 제약 조건으로 인해 행 피치와 너비가 항상 동일하지는 않습니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_buffer_toggle)(struct GX_CANVAS_STRUCT *canvas, GX_RECTANGLE *dirty_area) <br/> 이중 버퍼링된 메모리 시스템에서 작동 프레임 버퍼와 가시 프레임 버퍼 간을 전환하는 함수에 대한 포인터입니다. 이 함수는 먼저 하드웨어에 새 프레임 버퍼를 사용하도록 지시한 다음, 새 가시 버퍼의 수정된 부분을 컴패니언 버퍼에 복사하여 두 버퍼가 동기화 상태를 유지하도록 합니다. | 
| VOID (*gx_display_driver_polygon_draw)(GX_DRAW_CONTEXT *context, INT num_points, GX_POINT *vertices <br/> 다각형을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_polygon_fill)(GX_DRAW_CONTEXT *context, INT num_points, GX_POINT *vertices <br/> 채워진 다각형을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_circle_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> 원을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_anti_aliased_circle_draw) (GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> 앤티앨리어싱된 원을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_wide_circle_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> 굵은 윤곽선으로 원을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_wide_anti_aliased_circle_draw) (GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> 굵은 윤곽선으로 앤티앨리어싱된 원을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_circle_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> 채워진 원을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> 호를 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_anti_aliased_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INTend_angle) <br/> 앤티앨리어싱된 호를 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_wide_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> 굵은 윤곽선으로 호를 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_anti_aliased_wide_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INTend_angle) <br/> 앤티앨리어싱된 호를 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_arc_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> 채워진 호를 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_pie_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> 채워진 원형을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> 타원형을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_anti_aliased_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> 타원형을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_wide_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> 굵은 윤곽선으로 타원형을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_anti_aliased_wide_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> 굵은 윤곽선으로 타원형을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_ellipse_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> 채워진 타원형을 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_8bit_glyph_draw)(GX_DRAW_CONTEXT *context, GX_RECTANGLE *draw_area, GX_POINT *map_offset, constGX_GLYPH *glyph) <br/> 현재 그리기 컨텍스트의 브러시를 사용하여 8비트 별칭 텍스트 문자 모양을 캔버스에 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_4bit_glyph_draw)(GX_DRAW_CONTEXT *context, GX_RECTANGLE *draw_area, GX_POINT *map_offset, const GX_GLYPH *glyph) <br/> 현재 그리기 컨텍스트의 브러시를 사용하여 4비트 별칭 텍스트 문자 모양을 캔버스에 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |
| VOID (*gx_display_driver_1bit_glyph_draw)(GX_DRAW_CONTEXT *context, GX_RECTANGLE *draw_area, GX_POINT *map_offset, const GX_GLYPH *glyph) <br/> 현재 그리기 컨텍스트의 브러시를 사용하여 1비트 단색 텍스트 문자 모양을 캔버스에 그리는 함수에 대한 포인터입니다. 이 함수의 기본 구현은 지원되는 각 색 깊이 및 색 형식에 대해 제공됩니다. |


