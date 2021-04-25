---
title: 부록 D - GUIX 브러시, 캔버스 및 그라데이션 특성
description: GUIX 브러시, 캔버스 및 그라데이션 특성에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 19c0687a54be244ae395124664b4b6da0f4e90b6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812091"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a>부록 D - GUIX 브러시, 캔버스 및 그라데이션 특성

__**브러시 스타일:**__

**GX_BRUSH_OUTLINE**
- 값: 0x0000
- 설명: 이 브러시 스타일은 gx_canvas_rectangle_draw 또는 gx_canvas_polygon_draw와 같은 도형 그리기 함수에 적용됩니다. 이 스타일은 도형에 윤곽선을 그리고 필요에 따라 도형을 채워야 함을 나타냅니다. GX_BRUSH_OUTLINE 스타일이 설정되어 있고 GX_BRSUH_SOLID_FILL을 선택 취소한 경우 도형에 윤곽선만 그려집니다.

**GX_BRUSH_SOLID_FILL**
- 값: 0x0001
- 설명: 이 브러시 스타일은 도형 그리기 함수에 적용되며 요청된 도형을 현재 브러시 채우기 색을 사용하여 단색으로 채워야 함을 나타냅니다.

**GX_BRUSH_PIXELMAP_FILL**
- 값: 0x0002
- 설명: 이 브러시 스타일은 도형 그리기 함수에 적용되며 요청된 도형이 현재 브러시 pixelmap으로 채워진 패턴이어야 함을 나타냅니다.

**GX_BRUSH_ALIAS**
- 값: 0x0004
- 설명: 이 브러시 스타일은 모든 선 그리기 및 도형 윤곽선에 적용됩니다. 이 플래그가 설정되면, 더 정확하지만 시간이 더 많이 소요되는 앤티앨리어싱된 그리기 알고리즘을 사용하여 선과 윤곽선이 그려집니다. 이 스타일 플래그는 16bpp 색 깊이 이상에서만 사용됩니다.

**GX_BRUSH_UNDERLINE**
- 값: 0x0008
- 설명: 이 플래그는 텍스트 그리기에 적용되며, 다음에 그려진 텍스트가 밑줄로 표시되어야 함을 나타냅니다.

**GX_BRUSH_ROUND**
- 값: 0x0010
- 설명: 이 플래그는 선 그리기에 적용되며, 선 끝이 기본 정사각형 모양이 아닌 둥근 도형이나 원형 도형으로 그려지도록 지정합니다.

__**캔버스 플래그:**__

**GX_CANVAS_SIMPLE**
- 값: 0x01
- 설명: 화면 밖에 그리는 데 사용되는 메모리 캔버스입니다.

**GX_CANVAS_MANAGED**
- 값: 0x02
- 설명: 복합 빌드 프로세스의 일부 또는 단일 캔버스 아키텍처에 대한 버퍼 토글 작업의 일부로 활성 디스플레이에 자동으로 플러시되는 캔버스입니다.

**GX_CANVAS_VISIBLE**
- 값: 0x04
- 설명: 이 플래그를 사용하면 캔버스 그리기 내용을 잃지 않고 캔버스를 켜고 끌 수 있습니다.

**GX_CANVAS_MODIFIED**
- 값: 0x08
- 설명: 나중에 사용하도록 예약되었습니다.

**GX_CANVAS_COMPOSITE**
- 값: 0x20
- 설명: 이 플래그는 애플리케이션에서 여러 개의 관리형 캔버스를 복합 캔버스로 합성하는 다중 캔버스 시스템을 구성할 때 사용되며, 합성은 하드웨어 프레임 버퍼를 기반으로 합니다.

__**그라데이션 유형:**__

**GX_GRADIENT_TYPE_VERTICAL**
- 값: 0x01
- 설명: 세로 alphamap 그라데이션을 만듭니다.

**GX_GRADIENT_TYPE_ALPHA**
- 값: 0x02
- 설명: alphamap 스타일 그라데이션을 만듭니다. 현재 유일하게 지원되는 그라데이션 스타일입니다.

**GX_GRADIENT_TYPE_MIRROR**
- 값: 0x04
- 설명: 이 플래그는 너비가 너비/높이 범위의 가운데에서 가장 높음을 나타내며 오른쪽/아래쪽 가장자리에 도달할 때 시작 값으로 돌아옴을 나타냅니다. 이 스타일 플래그를 사용하지 않으면 GX_GRADIENT_TYPE_VERTICAL 플래그에 따라 위쪽에서 아래쪽 또는 왼쪽에서 오른쪽으로 향하는 선형 그라데이션이 됩니다.