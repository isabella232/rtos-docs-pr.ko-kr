---
title: 특정 위젯 형식 편집에 관한 참고 사항
description: 복잡한 특정 위젯 형식의 편집 방법을 설명하는 자세한 설명입니다.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3194a1b8c8965bf821631a8c34ac5e9961f8c8ff
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811941"
---
# <a name="chapter-8-notes-on-editing-specific-widget-types"></a><span data-ttu-id="aa740-103">챕터 8: 특정 위젯 형식 편집에 관한 참고 사항</span><span class="sxs-lookup"><span data-stu-id="aa740-103">Chapter 8: Notes on Editing Specific Widget Types</span></span>

<span data-ttu-id="aa740-104">GUIX Studio를 사용하면 사용자가 애플리케이션 UI 화면을 구성하는 GUIX 위젯을 쉽게 만들고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-104">GUIX Studio allows the user to easily create and modify GUIX widgets that will compose the application UI screens.</span></span> <span data-ttu-id="aa740-105">이러한 편집 방법은 대부분 직관적이고 명확합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-105">Most of these editing methods are intuitive and obvious.</span></span> <span data-ttu-id="aa740-106">예를 들어 위젯의 크기를 조정하려면 마우스로 위젯을 선택하고 위젯 테두리를 끌어서 놓을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-106">For example, to resize a widget you can select the widget with the mouse and drag the widget borders.</span></span> <span data-ttu-id="aa740-107">선택한 위젯의 왼쪽/위쪽/너비/높이 속성 필드에 직접 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-107">You can also directly type into the left/top/width/height property fields of the selected widget.</span></span>

<span data-ttu-id="aa740-108">이러한 위젯은 해당 기능 지원에서 약간 더 정교하기 때문에 특정 위젯 형식에는 고급 편집 프로세스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-108">Certain widget types require a more advanced editing process, because these widgets are themselves a bit more sophisticated in their feature support.</span></span>

<span data-ttu-id="aa740-109">이 챕터는 보다 복잡한 위젯 형식의 고급 편집 기능에 대한 참고 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-109">This chapter provides notes on the more advanced editing features for these more complex widget types.</span></span> <span data-ttu-id="aa740-110">이러한 참고 사항은 GUIX Studio의 기능이 GUIX 라이브러리 내에서 제공되는 위젯 형식과 함께 진행될 때 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-110">These notes will expand as the features of GUIX Studio advance along with the widget types provided within the GUIX library.</span></span>

## <a name="rich-text-view"></a><span data-ttu-id="aa740-111">서식 있는 텍스트 보기</span><span class="sxs-lookup"><span data-stu-id="aa740-111">Rich Text View</span></span>

<span data-ttu-id="aa740-112">이 위젯은 인라인 텍스트 서식 지정 코드를 지원하는 서식 있는 텍스트를 표시하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-112">This widget is used to display rich text that supports inline text formatting codes.</span></span> <span data-ttu-id="aa740-113">이러한 서식 지정 코드에는 굵은 글꼴, 기울임꼴 및 기타 여러 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-113">These formatting codes include bold, italic, and several others.</span></span> <span data-ttu-id="aa740-114">시작하려면 *프로젝트 보기* 또는 *대상 보기* 에서 선택한 부모를 마우스 오른쪽 단추로 클릭하고 메뉴 **삽입/텍스트/서식 있는 텍스트 보기** 를 선택하여 서식 있는 텍스트 보기 위젯을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-114">To begin, right-click on the selected parent from the *Project View* or *Target View* and select menu **Insert/Text/Rich Text View** to insert a rich text view widget.</span></span>

<span data-ttu-id="aa740-115">모든 위젯 형식에서 지원하는 표준 속성 집합 외에도 서식 있는 텍스트 보기 위젯 형식은 추가 속성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-115">In addition to the standard set of properties supported by all widget types, the Rich Text View widget type supports additional properties.</span></span>

### <a name="additional-properties"></a><span data-ttu-id="aa740-116">추가 속성</span><span class="sxs-lookup"><span data-stu-id="aa740-116">Additional Properties</span></span>

| <span data-ttu-id="aa740-117">속성</span><span class="sxs-lookup"><span data-stu-id="aa740-117">Property</span></span> | <span data-ttu-id="aa740-118">의미</span><span class="sxs-lookup"><span data-stu-id="aa740-118">Meaning</span></span> |
|----------|---------|
| <span data-ttu-id="aa740-119">텍스트 맞춤</span><span class="sxs-lookup"><span data-stu-id="aa740-119">Text Align</span></span> | <span data-ttu-id="aa740-120">기본 텍스트 맞춤</span><span class="sxs-lookup"><span data-stu-id="aa740-120">Default text alignment</span></span> |
| <span data-ttu-id="aa740-121">일반 글꼴</span><span class="sxs-lookup"><span data-stu-id="aa740-121">Normal Font</span></span>| <span data-ttu-id="aa740-122">기본 텍스트 글꼴</span><span class="sxs-lookup"><span data-stu-id="aa740-122">Default text font</span></span> |
| <span data-ttu-id="aa740-123">굵은 글꼴</span><span class="sxs-lookup"><span data-stu-id="aa740-123">Bold Font</span></span>  | <span data-ttu-id="aa740-124">굵은 글꼴로 태그가 지정된 텍스트의 텍스트 글꼴</span><span class="sxs-lookup"><span data-stu-id="aa740-124">Text font for text tagged as bold</span></span> |
| <span data-ttu-id="aa740-125">기울임꼴 글꼴</span><span class="sxs-lookup"><span data-stu-id="aa740-125">Italic Font</span></span>| <span data-ttu-id="aa740-126">기울임꼴로 태그가 지정된 텍스트의 텍스트 글꼴</span><span class="sxs-lookup"><span data-stu-id="aa740-126">Text font for text tagged as italic</span></span>|
| <span data-ttu-id="aa740-127">굵은 기울임꼴 글꼴</span><span class="sxs-lookup"><span data-stu-id="aa740-127">Bold Italic Font</span></span>| <span data-ttu-id="aa740-128">굵은 글꼴 및 기울임꼴로 태그가 지정된 텍스트의 텍스트 글꼴</span><span class="sxs-lookup"><span data-stu-id="aa740-128">Text font for text tagged as bold and italic</span></span> |
| <span data-ttu-id="aa740-129">개인 텍스트 복사</span><span class="sxs-lookup"><span data-stu-id="aa740-129">Private Text Copy</span></span> | <span data-ttu-id="aa740-130">위젯이 할당된 텍스트의 개인적인 복사본을 유지해야 하는지 여부를 확인해야 함</span><span class="sxs-lookup"><span data-stu-id="aa740-130">Should be checked if the widget is to keep its own private copy of any text assigned</span></span> |
| <span data-ttu-id="aa740-131">공백</span><span class="sxs-lookup"><span data-stu-id="aa740-131">Whitespace</span></span> | <span data-ttu-id="aa740-132">위젯과 표시되는 텍스트 사이의 여백 너비(픽셀)입니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-132">Width of margin between the widget and the displayed text, in pixels.</span></span> |
| <span data-ttu-id="aa740-133">줄 공간</span><span class="sxs-lookup"><span data-stu-id="aa740-133">Line Space</span></span> | <span data-ttu-id="aa740-134">텍스트의 두 줄 사이에 있는 공간(픽셀)입니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-134">Space between two lines of the text, in pixels.</span></span> |
|||

### <a name="the-rich-text-formatting-codes"></a><span data-ttu-id="aa740-135">서식 있는 텍스트 서식 지정 코드</span><span class="sxs-lookup"><span data-stu-id="aa740-135">The Rich Text formatting codes</span></span>

<span data-ttu-id="aa740-136">텍스트 서식 지정에 대해 지원되는 서식 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-136">The following format codes are supported for text formatting.</span></span>

|<span data-ttu-id="aa740-137">태그</span><span class="sxs-lookup"><span data-stu-id="aa740-137">Tag</span></span>|<span data-ttu-id="aa740-138">의미</span><span class="sxs-lookup"><span data-stu-id="aa740-138">Meaning</span></span>|
|---|---|
|\<b>\</b> | <span data-ttu-id="aa740-139">사용자 지정 굵은 글꼴 ID로 텍스트 글꼴 렌더링</span><span class="sxs-lookup"><span data-stu-id="aa740-139">Render text font with user specified bold font ID</span></span>|
|\<i>\</i> | <span data-ttu-id="aa740-140">사용자 지정 기울임꼴 ID로 텍스트 글꼴 렌더링</span><span class="sxs-lookup"><span data-stu-id="aa740-140">Render text font with user specified italic font ID</span></span>|
|\<u>\</u> | <span data-ttu-id="aa740-141">밑줄이 그어진 텍스트 렌더링</span><span class="sxs-lookup"><span data-stu-id="aa740-141">Render underlined text</span></span>|
|\<f GX_FONT_ID>\</f> | <span data-ttu-id="aa740-142">지정된 글꼴 ID를 사용하여 텍스트 렌더링</span><span class="sxs-lookup"><span data-stu-id="aa740-142">Render text using the specified font ID.</span></span> |
|\<c GX_COLOR_ID>\</c> | <span data-ttu-id="aa740-143">지정된 색 ID를 사용하여 텍스트 렌더링</span><span class="sxs-lookup"><span data-stu-id="aa740-143">Render text using the specified color ID</span></span>|
|\<hc GX_COLOR_ID>\</hc> | <span data-ttu-id="aa740-144">지정된 배경색 ID를 사용하여 텍스트 렌더링</span><span class="sxs-lookup"><span data-stu-id="aa740-144">Render text using the specified background color ID</span></span>|
|\<align left/right/center>\</align> | <span data-ttu-id="aa740-145">텍스트 맞춤 할당</span><span class="sxs-lookup"><span data-stu-id="aa740-145">Assign text alignment</span></span>|
|||

<span data-ttu-id="aa740-146">GUIX Studio 내에서 서식 있는 텍스트 문자열을 편집하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-146">There are two ways to edit the rich text string from within GUIX Studio:</span></span>

- <span data-ttu-id="aa740-147">권장되며 가장 간단한 편집 방법인 서식 있는 텍스트 편집 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-147">Use the Edit Rich Text dialog, which is the recommended and simplest editing method.</span></span>
- <span data-ttu-id="aa740-148">문자열 테이블 편집기 대화 상자를 사용하여 앞의 표에 나와 있는 서식 태그를 수동으로 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-148">Use the String Table Editor dialog, which allows you to manually insert the formatting tags shown in the preceding table.</span></span>

<span data-ttu-id="aa740-149">*대상 보기* 에서 서식 있는 텍스트 보기 위젯을 선택한 후 *속성 보기* 에서 **서식 있는 텍스트 편집** 단추를 선택하여 그림 8.1에 표시된 서식 있는 텍스트 편집 대화 상자를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-149">After selecting a Rich Text View widget in the *Target View*, select the **Edit Rich Text** button in the *Properties View* to invoke the  rich text edit dialog, shown in Figure 8.1.</span></span>

![GUIX Studio 서식 있는 텍스트 편집 대화 상자의 스크린샷입니다.](./media/guix-studio/edit_rich_text_dialog.png)

<span data-ttu-id="aa740-151">**그림 8.1**</span><span class="sxs-lookup"><span data-stu-id="aa740-151">**Figure 8.1**</span></span>

<span data-ttu-id="aa740-152">왼쪽 창은 서식 있는 텍스트 편집 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-152">The left pane is the rich text edit field.</span></span> <span data-ttu-id="aa740-153">도구 모음 아이콘을 사용하여 필요한 태그를 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-153">You can use the toolbar icons to help insert tags you require.</span></span> <span data-ttu-id="aa740-154">편집 필드에서 텍스트 블록을 선택한 다음 도구 모음 단추를 선택하여 선택한 텍스트 블록에 필요한 스타일과 색을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-154">Select any block of text in the edit field, and then select the toolbar buttons to apply the required styles and colors to the selected text block.</span></span> <span data-ttu-id="aa740-155">서식 있는 텍스트 편집 대화 상자는 테스트 문자열에 서식 코드를 삽입하는 쉬운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-155">The Edit Rich Text dialog is an easy way to insert the formatting codes into the test string.</span></span> <span data-ttu-id="aa740-156">필요한 경우 이러한 태그를 수동으로 삽입하거나 런타임 시 생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-156">You can also insert these tags manually or even generate them at runtime if needed.</span></span>

<span data-ttu-id="aa740-157">오른쪽 창은 대상 보기에서 텍스트가 렌더링되는 방식을 보여주는 위젯 미리 보기입니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-157">The Right pane is the widget preview to show how the text is rendered in the target view.</span></span> <span data-ttu-id="aa740-158">위젯 미리 보기의 배경색이 고정되어 있으며 이 색은 대상 보기에서 위젯의 할당된 배경색과 일치하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-158">The background color of the widget preview is fixed, which may not match the widget's assigned background color in the target view.</span></span>

<span data-ttu-id="aa740-159">리소스 ID 이름은 특정 글꼴 또는 색 리소스를 참조하는 서식 있는 텍스트에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-159">Resource ID names are used in rich text to reference specific font or color resources.</span></span> <span data-ttu-id="aa740-160">서식 있는 텍스트 문자열에서 참조한 후 글꼴 또는 색의 리소스 이름이 변경된 경우, GUIX Studio는 리소스 이름 변경 내용을 반영하도록 서식 있는 텍스트 문자열을 자동으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-160">If the resource name of a font or color is changed after it has been referenced by the rich text string, GUIX Studio will automatically update the rich text string to reflect the resource name changes.</span></span> <span data-ttu-id="aa740-161">반면 서식 있는 텍스트 위젯에 의해 참조되는 글꼴 또는 색 리소스를 삭제하는 경우, 삭제된 리소스 ID 이름을 제거하거나 변경하려면 영향을 받는 서식 있는 텍스트를 수동으로 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-161">On the other hand if you delete a font or color resource that is referenced by a rich text widget, you must edit the affected rich text manually to remove or change the resource ID names that have been deleted.</span></span>

<span data-ttu-id="aa740-162">이 대화 상자에서 저장 단추를 선택하면 정의한 서식 있는 텍스트 문자열이 프로젝트 문자열 테이블에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-162">When you select the Save button in this dialog, the rich text string you have defined is added to the project string table.</span></span>

## <a name="string-scroll-wheel"></a><span data-ttu-id="aa740-163">문자열 스크롤 휠</span><span class="sxs-lookup"><span data-stu-id="aa740-163">String Scroll Wheel</span></span>

<span data-ttu-id="aa740-164">문자열 스크롤 휠 위젯은 문자열 배열의 표시를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-164">A string scroll wheel widget supports the display of an array of strings.</span></span> <span data-ttu-id="aa740-165">이러한 문자열은 동적으로 할당될 수 있으며, 애플리케이션에서 여러 언어를 지원하는 경우에는 활성 문자열 테이블에서 할당된 문자열을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-165">These strings may be dynamically assigned, or, in the case that the application supports multiple languages, the assigned strings can be pulled from the active string table.</span></span>

<span data-ttu-id="aa740-166">문자열 스크롤 휠 위젯은 문자열 배열을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-166">The string scroll wheel widget supports an array of strings.</span></span> <span data-ttu-id="aa740-167">그림 8.2에 표시된 문자열 스크롤 휠 편집 대화 상자는 사용자가 이 문자열 배열을 할당할 수 있도록 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-167">The String Scroll Wheel Edit dialog, shown in Figure 8.2, is provided to allow the user to assign this array of strings.</span></span>

![GUIX Studio 문자열 스크롤 휠 편집 대화 상자 스크린샷입니다.](./media/guix-studio/string_scroll_wheel_edit.png)

<span data-ttu-id="aa740-169">**그림 8.2**</span><span class="sxs-lookup"><span data-stu-id="aa740-169">**Figure 8.2**</span></span>

<span data-ttu-id="aa740-170">이 대화 상자를 호출하려면 *대상 보기* 또는 *프로젝트 보기* 내에서 문자열 스크롤 휠 위젯을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-170">To invoke this dialog, select a string scroll wheel widget within the *Target View* or the *Project View*.</span></span> <span data-ttu-id="aa740-171">이 위젯 형식을 선택하면 *속성 보기* 에 **문자열 편집** 단추가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-171">Once this widget type is selected, the *Properties View* will include an **Edit Strings** button.</span></span> <span data-ttu-id="aa740-172">문자열 스크롤 휠 편집 대화 상자를 호출하려면 이 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-172">Select this button to invoke the String Scroll Wheel Edit dialog.</span></span>

<span data-ttu-id="aa740-173">드롭다운 목록에서 문자열 ID를 선택하거나 오른쪽의 텍스트 필드에 새 문자열 값을 입력하여 각 텍스트 인덱스에 문자열을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-173">To assign a string for each text index, you can either select a string ID from the drop-down list, or you can type a new string value in the Text field on the right.</span></span> <span data-ttu-id="aa740-174">변경 작업을 마치면 새 문자열이나 수정된 문자열이 활성 문자열 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-174">When you are done with your changes, any new or modified strings are saved to the active string table.</span></span>

## <a name="sprite"></a><span data-ttu-id="aa740-175">스프라이트</span><span class="sxs-lookup"><span data-stu-id="aa740-175">Sprite</span></span>

<span data-ttu-id="aa740-176">스프라이트 위젯은 애니메이션 효과를 제공하는 이미지 시퀀스를 표시하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-176">A sprite widget is used to display a sequence of images to provide an animation effect.</span></span> <span data-ttu-id="aa740-177">스프라이트 위젯에는 프레임 목록이 필요합니다. 이 목록은 프레임의 각 이미지에 적용되는 고유 매개 변수 및 이미지 ID의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-177">A sprite widget requires a frame list, which is an array of image IDs and unique parameters applied to each image in the frame.</span></span> <span data-ttu-id="aa740-178">스프라이트 위젯의 이 프레임 목록을 빌드하기 위해 그림 8.3에 표시된 스프라이트 프레임 편집 대화 상자가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-178">To build this frame list for the sprite widget the Edit Sprite Frames dialog, shown in figure 8.3, is provided:</span></span>

![GUIX Studio 스프라이트 프레임 편집 대화 상자의 스크린샷입니다.](./media/guix-studio/edit_sprite_frames.png)

<span data-ttu-id="aa740-180">**그림 8.3**</span><span class="sxs-lookup"><span data-stu-id="aa740-180">**Figure 8.3**</span></span>

<span data-ttu-id="aa740-181">이 대화 상자를 호출하려면 *대상 보기* 또는 *프로젝트 보기* 내에서 스프라이트 위젯을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-181">To invoke this dialog, select a sprite widget within the *Target View* or the *Project View*.</span></span> <span data-ttu-id="aa740-182">이 위젯 형식을 선택하면 *속성 보기* 에 **프레임 목록 편집** 단추가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-182">Once this widget type is selected, the *Properties View* will include an **Edit Framelist** button.</span></span> <span data-ttu-id="aa740-183">문자열 스크롤 휠 편집 대화 상자를 호출하려면 이 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-183">Select this button to invoke the String Scroll Wheel Edit dialog.</span></span>

<span data-ttu-id="aa740-184">*총 스프라이트 프레임 수* 필드는 스프라이트 위젯에 표시되는 정수 전체 프레임 수를 입력할 수 있는 입력 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-184">The *Total number of Sprite Frames* field is an input field allowing you to enter the integer total number of frames to be displayed by the sprite widget.</span></span> <span data-ttu-id="aa740-185">이미지는 프레임 목록 내에서 재사용할 수 있으며, 모든 이미지가 고유해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-185">Images can be reused within the frame list, meaning not every image must be unique.</span></span>

<span data-ttu-id="aa740-186">스프라이트 프레임 ID 필드는 1에서 총 프레임 수 사이의 범위에 해당하는 프레임 인덱스 선택 값입니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-186">The Sprite Frame ID field is a frame index selection value that ranges from 1 to Total number of Frames.</span></span> <span data-ttu-id="aa740-187">이 값을 증가시키거나 감소시켜 하나의 스프라이트 프레임에서 다음으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-187">Increment and Decrement this value to move from one sprite frame to the next.</span></span>

<span data-ttu-id="aa740-188">각 스프라이트 프레임에는 여러 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-188">Each sprite frame has several parameters.</span></span> <span data-ttu-id="aa740-189">첫 번째는 백그라운드 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-189">The first is the Background Operation.</span></span> <span data-ttu-id="aa740-190">이 필드는 인기 있는 GIF 애니메이션 형식의 기능을 모방합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-190">This field mimics the capabilities of the popular GIF animation format.</span></span> <span data-ttu-id="aa740-191">선택할 수 있는 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-191">The choices here include:</span></span>

- <span data-ttu-id="aa740-192">‘작업 없음’은 현재 프레임 이미지를 이전 프레임 이미지 위에 그리는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-192">No Operation, which means the current frame image is drawn over the previous frame image.</span></span>
- <span data-ttu-id="aa740-193">‘첫 번째 pixelmap 복원’은 인덱스 1 pixelmap을 현재 pixelmap 앞에 그리는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-193">Restore First Pixel-map, which means the index 1 pixel-map is drawn before the current pixel-map and</span></span>
- <span data-ttu-id="aa740-194">‘단색 채우기’는 현재 프레임을 그리기 전에 스프라이트 배경을 스프라이트 배경색으로 채우는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-194">Solid Color Fill, which means the sprite background is filled with the sprite background color before the current frame is drawn.</span></span>

<span data-ttu-id="aa740-195">pixelmap ID 필드를 사용하여 이전에 프로젝트 리소스에 추가한 모든 pixelmap을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-195">The Pixel-map ID field allows you to select any pixel-map previously added to the project resources.</span></span> <span data-ttu-id="aa740-196">여러 프레임에 동일한 pixelmap ID를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-196">The same pixel-map ID can be used for multiple frames.</span></span> <span data-ttu-id="aa740-197">예를 들어 스프라이트 애니메이션은 다른 스프라이트 이미지를 사용하는 대신 또는 추가로 x 및 y 오프셋 필드를 사용하여 이미지의 움직임을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-197">For example your sprite animation might utilize movement of the image (using the x and y offset fields) instead of or in addition to using different sprite images.</span></span>

<span data-ttu-id="aa740-198">알파 값 필드는 전체 pixelmap 그리기에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-198">The Alpha value field is applied to the entire pixel-map drawing.</span></span> <span data-ttu-id="aa740-199">이 필드는 8bpp 색 깊이 이상으로 실행하는 경우에만 효과가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-199">This field only has an effect when running at 8 bpp color depth and higher.</span></span> <span data-ttu-id="aa740-200">알파 값 0은 완전히 투명하고 알파 값 255는 불투명합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-200">Alpha value 0 is fully transparent, and alpha value 255 is opaque.</span></span>

<span data-ttu-id="aa740-201">프레임 x 오프셋 및 프레임 y 오프셋 필드를 사용하여 현재 pixelmap이 그려지는 스프라이트 프레임 내에서 오프셋을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-201">You can specify an offset within the sprite frame at which the current pixel-map will be drawn using the Frame x-offset and Frame y-offset fields.</span></span> <span data-ttu-id="aa740-202">즉, 그려진 각 이미지가 스프라이트 위젯의 전체 크기일 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-202">In other words, each image drawn does not have to be the full size of the sprite widget.</span></span>

<span data-ttu-id="aa740-203">지연 기간은 다음 스프라이트 프레임으로 이동하기 전에 지연할 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-203">The Delay period specifies the time to delay before moving to the next sprite frame.</span></span> <span data-ttu-id="aa740-204">이 값은 틱 단위이며 기본 GUIX/ThreadX 타이머 구성에서 각 틱은 50ms를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-204">This value is in ticks, which for the default GUIX/ThreadX timer configuration each tick represents 50 ms.</span></span>

<span data-ttu-id="aa740-205">스프라이트 프레임 편집 대화 상자에서 변경 내용을 저장하면 GUIX Studio에서 출력 사양 파일 생성의 일부로 전체 프레임 목록 배열을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa740-205">When you save your changes in the Edit Sprite Frames dialog, GUIX Studio is able to generate the complete frame list array as part of the output specifications file generation.</span></span>
