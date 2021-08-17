---
title: 부록 G - GUIX 글꼴 구조
description: GUIX 글꼴 구조에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4c7cedb49268f97f8e1fc4cd28329b0b61e697d57562865896f0502bdd1d45f1
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784192"
---
# <a name="appendix-g---guix-font-structure"></a>부록 G - GUIX 글꼴 구조

GUIX 글꼴은 일반적으로 GUIX Studio 애플리케이션에 의해 생성되고, 글꼴 문자 모양은 GUIX 디스플레이 드라이버에 의해 렌더링됩니다. 애플리케이션 소프트웨어는 각 텍스트 표시 위젯이 사용해야 하는 글꼴과 색상만 지정해야 합니다. GUIX 글꼴 데이터 구조는 완전성을 위해 여기에 문서화되었으며, 개발자가 다른 글꼴을 GUIX 글꼴 형식으로 생성하거나 변환하기 위한 고유한 메서드를 만들 수 있도록 합니다.

각 GUIX 글꼴은 GX_FONT 구조로 시작합니다. GX_FONT 구조는 글꼴에 포함된 문자 및 글꼴의 줄 높이와 같은 글로벌 글꼴 매개 변수를 정의합니다. GX_FONT 구조는 GX_GLYPH 구조체의 배열을 가리킵니다. 각 GX_GLYPH 구조는 한 특정 문자 모양의 너비, 높이 및 기준선 오프셋을 정의합니다. 또한 GX_GLYPH 구조는 실제 문자 모양 비트맵 데이터를 가리킵니다(공백 문자의 경우 NULL일 수 있음).

gx_api.h에 포함된 GX_FONT 구조는 다음과 같이 선언됩니다.

```c
typedef struct GX_FONT_STRUCT
{
    GX_UBYTE                     gx_font_format
    GX_UBYTE                     gx_font_prespace
    GX_UBYTE                     gx_font_postspace
    GX_UBYTE                     gx_font_line_height 
    GX_UBYTE                     gx_font_baseline
    USHORT                       gx_font_first_glyph
    USHORT                       gx_font_last_glyph 
    GX_CONST GX_GLYPH           *gx_font_glyphs
    const struct GX_FONT_STRUCT *gx_font_next_page
} GX_FONT;
```

gx_font_format 필드는 gx_api.h 헤더 파일에 정의된 대로 픽셀당 글꼴 비트 및 기타 플래그를 정의합니다.

gx_font_prespace는 여러 줄 텍스트 화면에서 텍스트의 각 줄 위에서 건너뛸 픽셀 공간을 정의합니다.

gx_font_postspace 필드는 여러 줄 텍스트 화면에서 텍스트의 각 줄 아래에서 건너뛸 픽셀 공간을 정의합니다.

gx_font_line_height 필드는 글꼴에서 가장 긴 문자 모양의 높이를 정의합니다.

gx_font_baseline 필드는 문자 모양 픽셀의 위쪽 행부터 글꼴 기준선까지의 거리(픽셀)를 정의합니다.

gx_font_first_glyph 필드는 이 글꼴 페이지에 포함된 첫 번째 유니코드 문자 인코딩을 정의합니다.

gx_font_last_glyph 필드는 이 글꼴 페이지에 포함된 마지막 유니코드 문자 인코딩을 정의합니다.

gx_font_glyphs 포인터는 GX_GLYPH 구조의 배열을 가리킵니다. 이 배열의 크기는 이 글꼴 페이지에 포함된 문자 수와 같아야 합니다. 즉, (gx_font_last_glyph – gx_font_first_glyph) + 1과 같습니다.

gx_font_next_page 멤버는 여러 페이지 글꼴에 사용됩니다. 여러 페이지 글꼴이 확장 문자 집합에 사용되고 GX_GLYPH 구조 배열의 크기를 최적화하는 데 사용됩니다. 글꼴의 모든 문자가 한 글꼴 페이지에 포함되어 있거나 해당 글꼴의 마지막 페이지인 경우 gx_font_next_page 멤버가 GX_NULL로 설정됩니다.

위에서 설명한 것처럼 위의 GX_FONT 구조에는 GX_GLYPHS 구조의 배열에 대한 포인터가 포함되어 있습니다. 글꼴 페이지에는 각 문자에 대한 GX_GLYPH 구조가 하나씩 있어야 합니다. GX_GLYPH 구조는 다음으로 정의됩니다.

```c
typedef struct GX_GLYPH_STRUCT
{
    GX_CONST GX_UBYTE *gx_glyph_map;
    GX_BYTE            gx_glyph_ascent;
    GX_BYTE            gx_glyph_descent;
    GX_BYTE            gx_glyph_advance;
    GX_BYTE            gx_glyph_leading;
    GX_UBYTE           gx_glyph_width;
    GX_UBYTE           gx_glyph_height;
} GX_GLYPH;
```

gx_glyph_map 포인터는 문자 모양 비트맵을 가리킵니다. 이 포인터는 공백 문자에 대한 GX_NULL일 수 있습니다. 비트맵 데이터는 1bpp, 2bpp, 4bpp 또는 8bpp 알파 값으로 인코딩됩니다. 1비트 데이터의 경우 값 1은 픽셀을 전경색으로 써야 함을 나타내고, 값 0은 픽셀이 투명함을 나타냅니다. 8비트 데이터의 경우 값의 범위는 0(완전히 투명)에서 255 (완전히 불투명) 사이입니다. 모든 중간 값은 앤티앨리어싱된 글꼴의 혼합 값을 나타냅니다. 문자 모양 비트맵 데이터는 8bpp보다 작은 데이터 값을 사용하는 형식의 경우 항상 전체 바이트 맞춤으로 채워집니다.

gx_glyph_ascent 및 gx_glyph_descent 값은 글꼴 기준선에 대하여 문자 모양을 세로로 배치합니다.

gx_glyph_width 및 gx_glyph_height 값은 문자 모양 비트맵 데이터의 크기를 지정합니다.

gx_glyph_advance 값은 문자 모양을 그린 후 그리기 위치를 앞으로 이동할 픽셀 너비를 지정합니다. 문자 모양 너비와 같지 않을 수 있습니다.

gx_glyph_leading 값은 문자 모양을 렌더링하기 전에 x 방향으로 이동할 픽셀 수를 지정합니다.