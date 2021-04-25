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
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a><span data-ttu-id="28d65-103">부록 D - GUIX 브러시, 캔버스 및 그라데이션 특성</span><span class="sxs-lookup"><span data-stu-id="28d65-103">Appendix D - GUIX Brush, Canvas and Gradient Attributes</span></span>

<span data-ttu-id="28d65-104">__**브러시 스타일:**__</span><span class="sxs-lookup"><span data-stu-id="28d65-104">__**Brush Styles:**__</span></span>

<span data-ttu-id="28d65-105">**GX_BRUSH_OUTLINE**</span><span class="sxs-lookup"><span data-stu-id="28d65-105">**GX_BRUSH_OUTLINE**</span></span>
- <span data-ttu-id="28d65-106">값: 0x0000</span><span class="sxs-lookup"><span data-stu-id="28d65-106">Value: 0x0000</span></span>
- <span data-ttu-id="28d65-107">설명: 이 브러시 스타일은 gx_canvas_rectangle_draw 또는 gx_canvas_polygon_draw와 같은 도형 그리기 함수에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-107">Description: This brush style applies to shape drawing functions such as gx_canvas_rectangle_draw or gx_canvas_polygon_draw.</span></span> <span data-ttu-id="28d65-108">이 스타일은 도형에 윤곽선을 그리고 필요에 따라 도형을 채워야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-108">This style indicateds the shape should be outlined, in addition to optionally being fill.</span></span> <span data-ttu-id="28d65-109">GX_BRUSH_OUTLINE 스타일이 설정되어 있고 GX_BRSUH_SOLID_FILL을 선택 취소한 경우 도형에 윤곽선만 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-109">If the GX_BRUSH_OUTLINE style is set and the GX_BRSUH_SOLID_FILL is cleared, the shape is only outlined.</span></span>

<span data-ttu-id="28d65-110">**GX_BRUSH_SOLID_FILL**</span><span class="sxs-lookup"><span data-stu-id="28d65-110">**GX_BRUSH_SOLID_FILL**</span></span>
- <span data-ttu-id="28d65-111">값: 0x0001</span><span class="sxs-lookup"><span data-stu-id="28d65-111">Value: 0x0001</span></span>
- <span data-ttu-id="28d65-112">설명: 이 브러시 스타일은 도형 그리기 함수에 적용되며 요청된 도형을 현재 브러시 채우기 색을 사용하여 단색으로 채워야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-112">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be filled with a solid color using the current brush fill color.</span></span>

<span data-ttu-id="28d65-113">**GX_BRUSH_PIXELMAP_FILL**</span><span class="sxs-lookup"><span data-stu-id="28d65-113">**GX_BRUSH_PIXELMAP_FILL**</span></span>
- <span data-ttu-id="28d65-114">값: 0x0002</span><span class="sxs-lookup"><span data-stu-id="28d65-114">Value: 0x0002</span></span>
- <span data-ttu-id="28d65-115">설명: 이 브러시 스타일은 도형 그리기 함수에 적용되며 요청된 도형이 현재 브러시 pixelmap으로 채워진 패턴이어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-115">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be pattern filled with the current brush pixelmap.</span></span>

<span data-ttu-id="28d65-116">**GX_BRUSH_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="28d65-116">**GX_BRUSH_ALIAS**</span></span>
- <span data-ttu-id="28d65-117">값: 0x0004</span><span class="sxs-lookup"><span data-stu-id="28d65-117">Value: 0x0004</span></span>
- <span data-ttu-id="28d65-118">설명: 이 브러시 스타일은 모든 선 그리기 및 도형 윤곽선에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-118">Description: This brush style applies to all line drawing and shape outlines.</span></span> <span data-ttu-id="28d65-119">이 플래그가 설정되면, 더 정확하지만 시간이 더 많이 소요되는 앤티앨리어싱된 그리기 알고리즘을 사용하여 선과 윤곽선이 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-119">If this flag is set, lines and outlines are drawing with the more accurate but also more time consuming anti-aliased drawing algorithms.</span></span> <span data-ttu-id="28d65-120">이 스타일 플래그는 16bpp 색 깊이 이상에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-120">This style flag is only used for 16-bpp color depths and higher.</span></span>

<span data-ttu-id="28d65-121">**GX_BRUSH_UNDERLINE**</span><span class="sxs-lookup"><span data-stu-id="28d65-121">**GX_BRUSH_UNDERLINE**</span></span>
- <span data-ttu-id="28d65-122">값: 0x0008</span><span class="sxs-lookup"><span data-stu-id="28d65-122">Value: 0x0008</span></span>
- <span data-ttu-id="28d65-123">설명: 이 플래그는 텍스트 그리기에 적용되며, 다음에 그려진 텍스트가 밑줄로 표시되어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-123">Description: This flag applies to text drawing, and indicates that subsequent text drawn should be underlined.</span></span>

<span data-ttu-id="28d65-124">**GX_BRUSH_ROUND**</span><span class="sxs-lookup"><span data-stu-id="28d65-124">**GX_BRUSH_ROUND**</span></span>
- <span data-ttu-id="28d65-125">값: 0x0010</span><span class="sxs-lookup"><span data-stu-id="28d65-125">Value: 0x0010</span></span>
- <span data-ttu-id="28d65-126">설명: 이 플래그는 선 그리기에 적용되며, 선 끝이 기본 정사각형 모양이 아닌 둥근 도형이나 원형 도형으로 그려지도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-126">Description: This flag applies to line drawing, and indicates that line ends are drawn with a round or circular shape, rather than the default square shape.</span></span>

<span data-ttu-id="28d65-127">__**캔버스 플래그:**__</span><span class="sxs-lookup"><span data-stu-id="28d65-127">__**Canvas Flags:**__</span></span>

<span data-ttu-id="28d65-128">**GX_CANVAS_SIMPLE**</span><span class="sxs-lookup"><span data-stu-id="28d65-128">**GX_CANVAS_SIMPLE**</span></span>
- <span data-ttu-id="28d65-129">값: 0x01</span><span class="sxs-lookup"><span data-stu-id="28d65-129">Value: 0x01</span></span>
- <span data-ttu-id="28d65-130">설명: 화면 밖에 그리는 데 사용되는 메모리 캔버스입니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-130">Description: A memory canvas which is used to off-screen drawing.</span></span>

<span data-ttu-id="28d65-131">**GX_CANVAS_MANAGED**</span><span class="sxs-lookup"><span data-stu-id="28d65-131">**GX_CANVAS_MANAGED**</span></span>
- <span data-ttu-id="28d65-132">값: 0x02</span><span class="sxs-lookup"><span data-stu-id="28d65-132">Value: 0x02</span></span>
- <span data-ttu-id="28d65-133">설명: 복합 빌드 프로세스의 일부 또는 단일 캔버스 아키텍처에 대한 버퍼 토글 작업의 일부로 활성 디스플레이에 자동으로 플러시되는 캔버스입니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-133">Description: A canvas which automatically flushed to the active display, either as part of the composite building process or as part of the buffer toggle operation for single-canvas architectures.</span></span>

<span data-ttu-id="28d65-134">**GX_CANVAS_VISIBLE**</span><span class="sxs-lookup"><span data-stu-id="28d65-134">**GX_CANVAS_VISIBLE**</span></span>
- <span data-ttu-id="28d65-135">값: 0x04</span><span class="sxs-lookup"><span data-stu-id="28d65-135">Value: 0x04</span></span>
- <span data-ttu-id="28d65-136">설명: 이 플래그를 사용하면 캔버스 그리기 내용을 잃지 않고 캔버스를 켜고 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-136">Description: This flag can be used to turn on and off a canvas, without losing the canvas drawing contents.</span></span>

<span data-ttu-id="28d65-137">**GX_CANVAS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="28d65-137">**GX_CANVAS_MODIFIED**</span></span>
- <span data-ttu-id="28d65-138">값: 0x08</span><span class="sxs-lookup"><span data-stu-id="28d65-138">Value: 0x08</span></span>
- <span data-ttu-id="28d65-139">설명: 나중에 사용하도록 예약되었습니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-139">Description: Reserved for future use.</span></span>

<span data-ttu-id="28d65-140">**GX_CANVAS_COMPOSITE**</span><span class="sxs-lookup"><span data-stu-id="28d65-140">**GX_CANVAS_COMPOSITE**</span></span>
- <span data-ttu-id="28d65-141">값: 0x20</span><span class="sxs-lookup"><span data-stu-id="28d65-141">Value: 0x20</span></span>
- <span data-ttu-id="28d65-142">설명: 이 플래그는 애플리케이션에서 여러 개의 관리형 캔버스를 복합 캔버스로 합성하는 다중 캔버스 시스템을 구성할 때 사용되며, 합성은 하드웨어 프레임 버퍼를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-142">Description: This flag is used by the application when configuring a multiple-canvas system which will composite multiple managed canvases into the composite canvas, and the composite is the driven to the hardware frame buffer.</span></span>

<span data-ttu-id="28d65-143">__**그라데이션 유형:**__</span><span class="sxs-lookup"><span data-stu-id="28d65-143">__**Gradient Types:**__</span></span>

<span data-ttu-id="28d65-144">**GX_GRADIENT_TYPE_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="28d65-144">**GX_GRADIENT_TYPE_VERTICAL**</span></span>
- <span data-ttu-id="28d65-145">값: 0x01</span><span class="sxs-lookup"><span data-stu-id="28d65-145">Value: 0x01</span></span>
- <span data-ttu-id="28d65-146">설명: 세로 alphamap 그라데이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-146">Description: Creates a vertical alphamap gradient.</span></span>

<span data-ttu-id="28d65-147">**GX_GRADIENT_TYPE_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="28d65-147">**GX_GRADIENT_TYPE_ALPHA**</span></span>
- <span data-ttu-id="28d65-148">값: 0x02</span><span class="sxs-lookup"><span data-stu-id="28d65-148">Value: 0x02</span></span>
- <span data-ttu-id="28d65-149">설명: alphamap 스타일 그라데이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-149">Description: Creats an alpha-map style gradient.</span></span> <span data-ttu-id="28d65-150">현재 유일하게 지원되는 그라데이션 스타일입니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-150">This is currently the only gradient style supported.</span></span>

<span data-ttu-id="28d65-151">**GX_GRADIENT_TYPE_MIRROR**</span><span class="sxs-lookup"><span data-stu-id="28d65-151">**GX_GRADIENT_TYPE_MIRROR**</span></span>
- <span data-ttu-id="28d65-152">값: 0x04</span><span class="sxs-lookup"><span data-stu-id="28d65-152">Value: 0x04</span></span>
- <span data-ttu-id="28d65-153">설명: 이 플래그는 너비가 너비/높이 범위의 가운데에서 가장 높음을 나타내며 오른쪽/아래쪽 가장자리에 도달할 때 시작 값으로 돌아옴을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-153">Description: This flag indicates that the gradient should peak at the center of the width/height range, and return to the starting value as it reaches the right/bottom edge.</span></span> <span data-ttu-id="28d65-154">이 스타일 플래그를 사용하지 않으면 GX_GRADIENT_TYPE_VERTICAL 플래그에 따라 위쪽에서 아래쪽 또는 왼쪽에서 오른쪽으로 향하는 선형 그라데이션이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28d65-154">Without this style flag, the gradient will be a linear gradient from top-to-bottom or left-to-right, depending on the GX_GRADIENT_TYPE_VERTICAL flag.</span></span>