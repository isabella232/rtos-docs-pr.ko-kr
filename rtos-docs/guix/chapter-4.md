---
title: 4장 - GUIX 서비스 설명
description: 이 장에서는 아래에 나열된 모든 GUIX 서비스를 사전순으로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7a17ab0d2500d021bb9397dbf673427362c45173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811268"
---
# <a name="chapter-4---description-of-guix-services"></a>4장 - GUIX 서비스 설명

이 장에서는 아래에 나열된 모든 GUIX 서비스를 사전순으로 설명합니다.  

다음 API 설명의 “반환 값” 섹션에서 **굵게** 표시된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **GX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만 굵게 표시되지 않은 값에는 API 오류 검사를 완전히 사용할 수 없게 됩니다. 

| **GUIX 서비스**                      | **설명**                                                                             |
| -------------------------------------- | -------------------------------------------------------------------------------------------- |
| gx_accordion_menu_create            | 아코디언 메뉴 만들기                                                                        |
| gx_accordion_menu_draw              | 아코디언 메뉴 그리기                                                                          |
| gx_accordion_menu_event_process    | 아코디언 메뉴 이벤트 처리                                                                 |
| gx_accordion_menu_position          | 메뉴 항목 배치                                                                          |
| gx_animation_canvas_define          | 후속 애니메이션에 사용할 캔버스의 애니메이션 컨트롤러에 메모리를 제공합니다. |
| gx_animation_create                  | 애니메이션 컨트롤러 만들기                                                               |
| gx_animation_delete                  | 애니메이션 컨트롤러 삭제                                                               |
| gx_animation_drag_disable           | 화면 끌기 애니메이션 후크 사용 안 함                                                           |
| gx_animation_drag_enable            | 화면 끌기 애니메이션 후크 사용                                                            |
| gx_animation_landing_speed_set     | 화면 끌기 애니메이션의 착륙 속도 설정                                                  |
| gx_animation_start                   | 애니메이션 시퀀스 시작                                                               |
| gx_animation_stop                    | 애니메이션 시퀀스 일시 중단                                                                |
| gx_binres_language_count_get      |  이진 리소스 파일에서 언어 개수 검색                                          |
| gx_binres_language_info_load      |  이진 리소스 파일에서 언어 이름 및 크기 정보 읽기                           |
| gx_binres_language_table_load      | (사용되지 않음) 이진 리소스 데이터 버퍼에서 언어 테이블 로드                          |
| gx_binres_language_table_load_ext | 이진 리소스 데이터 버퍼에서 언어 테이블 로드                                       |
| gx_binres_theme_load                | 이진 리소스 데이터 버퍼에서 테마 로드                                                |
| gx_brush_default                     | 현재 브러시를 기본값으로 초기화                                                         |
| gx_brush_define                      | 브러시 정의                                                                                 |
| gx_button_background_draw           | 단추 배경 그리기                                                                       |
| gx_button_create                     | 만들기 단추                                                                                |
| gx_button_deselect                   | 단추 선택 취소                                                                              |
| gx_button_draw                       | 단추 그리기                                                                                  |
| gx_button_event_process            | 단추 이벤트 처리                              |
| gx_button_select                    | 단추 선택                                     |
| gx_canvas_alpha_set                | 캔버스의 알파 혼합 값 설정                  |
| gx_canvas_arc_draw                 | 원호 그리기                                   |
| gx_canvas_block_move               | 블록 이동                                        |
| gx_canvas_circle_draw              | 원 그리기                                       |
| gx_canvas_create                    | 캔버스 만들기                                   |
| gx_canvas_delete                    | 캔버스 삭제                                   |
| gx_canvas_drawing_complete         | 캔버스 그리기 완료                           |
| gx_canvas_drawing_initiate         | 캔버스에서 그리기 시작                        |
| gx_canvas_ellipse_draw             | 타원 그리기                                   |
| gx_canvas_hardware_layer_bind     | 그래픽 계층에 캔버스 바인딩                     |
| gx_canvas_hide                      | 캔버스 숨기기                           |
| gx_canvas_line_draw                | 선 그리기                                         |
| gx_canvas_memory_define            | 캔버스 메모리 주소 할당                      |
| gx_canvas_offset_set               | 캔버스 x,y 표시 오프셋 할당                  |
| gx_canvas_pie_draw                 | 원형(쐐기형) 도형 그리기                          |
| gx_canvas_pixel_draw               | 단일 픽셀 그리기                               |
| gx_canvas_pixelmap_blend           | 배경과 pixelmap 혼합                  |
| gx_canvas_pixelmap_get             | 캔버스 데이터를 가리키는 pixelmap 가져오기            |
| gx_canvas_pixelmap_draw            | pixelmap 그리기                                     |
| gx_canvas_pixelmap_rotate          | pixelmap 회전                                   |
| gx_canvas_pixelmap_tile            | 바둑판식으로 pixelmap 배열                                     |
| gx_canvas_polygon_draw             | 다각형 그리기                                      |
| gx_canvas_rectangle_draw           | 사각형 그리기                                    |
| gx_canvas_rotated_text_draw       | (사용되지 않음) 중심점을 기준으로 회전된 텍스트 그리기 |
| gx_canvas_rotated_text_draw_ext  | 중심점을 기준으로 회전된 텍스트 그리기              |
| gx_canvas_shift                     | x,y만큼 캔버스 이동                               |
| gx_canvas_show                      | 캔버스 표시                             |
| gx_canvas_text_draw                | (사용되지 않음) 텍스트 그리기                            |
| gx_canvas_text_draw_ext           | 텍스트 그리기                                         |
| gx_checkbox_create                  | 확인란 만들기                                 |
| gx_checkbox_draw                    | 확인란 그리기                                   |
| gx_checkbox_event_process          | 확인란 이벤트 처리 함수                   |
| gx_checkbox_pixelmap_set           | 확인란 pixelmap 할당                          |
| gx_checkbox_select                  | 확인란 선택                                   |
| gx_circular_gauge_angle_get       | 계기 위젯 바늘 각도 검색                |
| gx_circular_gauge_angle_set       | 계기 위젯 바늘 각도 할당                  |
| gx_circular_gauge_animation_set   | 원형 계기 애니메이션 정의                   |
| gx_circular_gauge_background_draw | 원형 계기 배경 그리기                    |
| gx_circular_gauge_create           | 원형 계기 위젯 만들기                    |
| gx_circular_gauge_draw             | 원형 계기 위젯 그리기                      |
| gx_circular_gauge_event_process   | 원형 계기 이벤트 처리                      |
| gx_context_brush_default            | 현재 컨텍스트의 브러시 설정                                      |
| gx_context_brush_define             | 현재 컨텍스트의 브러시 정의                                       |
| gx_context_brush_get                | 현재 컨텍스트의 브러시 가져오기                                          |
| gx_context_brush_pattern_set       | 현재 컨텍스트의 브러시 패턴 설정                           |
| gx_context_brush_set                | 현재 컨텍스트의 브러시 설정                                          |
| gx_context_brush_style_set         | 현재 컨텍스트의 브러시 스타일 설정                                    |
| gx_context_brush_width_set         | 현재 컨텍스트의 브러시 너비 설정                                     |
| gx_context_color_get                | 색 ID를 색 값으로 확인                                     |
| gx_context_fill_color_set          | 현재 컨텍스트의 채우기 색 설정                                     |
| gx_context_font_get                 | 글꼴 ID를 글꼴 포인터 값으로 확인                               |
| gx_context_font_set                 | 현재 컨텍스트의 글꼴 설정                                           |
| gx_context_line_color_set          | 현재 컨텍스트의 선 색 설정                                     |
| gx_context_pixelmap_get             | pixelmap ID를 pixelmap 포인터 값으로 확인                       |
| gx_context_pixelmap_set             | 영역 채우기에 사용되는 브러시 pixelmap 할당                            |
| gx_context_raw_brush_define        | 현재 컨텍스트의 원시 브러시 정의                                   |
| gx_context_raw_fill_color_set     | 현재 컨텍스트의 원시 채우기 색 설정                                 |
| gx_context_raw_line_color_set     | 현재 컨텍스트의 원시 선 색 설정                                 |
| gx_context_string_get               | 현재 그리기 컨텍스트와 연결된 문자열 검색(사용되지 않음) |
| gx_context_string_get_ext          | 현재 그리기 컨텍스트와 연결된 문자열 검색(사용되지 않음) |
| gx_display_active_language_set     | 활성 언어 할당                                                |
| gx_display_color_set                | 디스플레이 색 테이블에서 하나의 색 값 바꾸기                       |
| gx_display_color_table_set         | 디스플레이에서 사용되는 색 테이블 할당                              |
| gx_display_create                    | 디스플레이 만들기                                                        |
| gx_display_delete                    | 디스플레이 삭제                                                        |
| gx_display_font_table_set          | 디스플레이에서 사용되는 글꼴 테이블 할당                               |
| gx_display_language_table_get      | 디스플레이와 연결된 언어 테이블 검색(사용되지 않음)    |
| gx_display_language_table_get_ext | 디스플레이와 연결된 언어 테이블 검색                 |
| gx_display_language_table_set      | 표시된 디스플레이에 언어 테이블 할당(사용되지 않음)           |
| gx_display_language_table_set_ext | 표시된 디스플레이에 언어 테이블 할당                       |
| gx_display_pixelmap_table_set      | 디스플레이에서 사용되는 pixelmap 테이블 할당                           |
| gx_display_string_get               | 문자열 ID와 연결된 문자열 검색(사용되지 않음)                |
| gx_display_string_get_ext          | 문자열 ID와 연결된 문자열 검색                             |
| gx_display_string_table_get             | 표시된 디스플레이와 연결된 문자열 테이블 검색(사용되지 않음) |
| gx_display_string_table_get_ext        | 표시된 디스플레이와 연결된 문자열 테이블 검색               |
| gx_display_theme_install                 | 지정된 디스플레이에 테마 설치                               |
| gx_drop_list_close                       | 드롭 목록 닫기                                                       |
| gx_drop_list_create                      | 드롭 목록 만들기                                                      |
| gx_drop_list_event_process               | 드롭 목록 이벤트 처리                                            |
| gx_drop_list_open                        | 드롭 목록 열기                                                        |
| gx_drop_list_pixelmap_set               | 드롭 목록에 pixelmap 설정                                             |
| gx_drop_list_popup_set                  | 드롭 목록에 팝업 설정                                                |
| gx_horizontal_list_children_position    | 가로 목록에 자식 위젯 배치                          |
| gx_horizontal_list_create                | 가로 목록 만들기                                                |
| gx_horizontal_list_event_process        | 가로 목록의 이벤트 처리                                      |
| gx_horizontal_list_page_index_set      | 가로 목록 페이지 인덱스 할당                                     |
| gx_horizontal_list_selected_index_get  | 선택된 항목 인덱스 가져오기                                           |
| gx_horizontal_list_selected_widget_get | 선택된 항목 위젯 가져오기                                          |
| gx_horizontal_list_selected_set         | 선택된 항목 설정                                                 |
| gx_horizontal_list_total_columns_set   | 만든 후에 목록 열 수 변경                          |
| gx_horizontal_scrollbar_create           | 가로 스크롤 막대 만들기                                           |
| gx_icon_button_create                    | 아이콘 단추 만들기                                                    |
| gx_icon_button_draw                      | 아이콘 단추 그리기                                                   |
| gx_icon_button_pixelmap_set             | 아이콘 단추의 pixelmap 설정                                           |
| gx_icon_background_draw                  | 아이콘 배경 그리기                                                  |
| gx_icon_create                            | 만들기 아이콘                                                           |
| gx_icon_draw                              | 아이콘 그리기                                                             |
| gx_icon_event_process                    | 아이콘 이벤트 처리 함수                                        |
| gx_icon_pixelmap_set                     | 아이콘의 pixelmap 설정                                                 |
| gx_image_reader_create                   | 이미지 판독기 모듈 인스턴스 만들기                                   |
| gx_image_reader_palette_set             | 이미지 판독기 팔레트 정의                                           |
| gx_image_reader_start                    | 압축 풀기 및 변환 프로세스 시작                           |
| gx_line_chart_axis_draw                 | 꺾은선형 차트 x,y 축 그리기                                              |
| gx_line_chart_create                     | GX_LINE_CHART 인스턴스 만들기                                       |
| gx_line_chart_data_draw                 | 꺾은선형 차트 데이터 선 그리기                                             |
| gx_line_chart_draw                       | 기본 꺾은선형 차트 그리기                                            |
| gx_line_chart_update                     | 꺾은선형 차트 데이터 강제 업데이트                                       |
| gx_line_chart_y_scale_calculate        | y축 데이터 값의 배율을 픽셀 좌표로 계산           |
| gx_menu_create                            | 메뉴 만들기                                                           |
| gx_menu_draw                              | 메뉴 그리기                                                             |
| gx_menu_event_process                     | 메뉴 이벤트 처리                                                    |
| gx_menu_insert                                | 새 항목 삽입                                                               |
| gx_menu_remove                                | 항목 제거                                                                  |
| gx_menu_text_draw                            | 메뉴 텍스트 그리기                                                                  |
| gx_menu_text_offset_set                     | 메뉴 텍스트 그리기 오프셋 설정                                                       |
| gx_multi_line_text_button_create           | 여러 줄 텍스트 단추 만들기                                                   |
| gx_multi_line_text_button_draw             | 여러 줄 텍스트 단추 그리기                                                     |
| gx_multi_line_text_button_event_process   | 여러 줄 텍스트 단추의 글꼴 설정                                             |
| gx_multi_line_text_button_text_draw       | 그리기의 텍스트 그리기 부분                                                 |
| gx_multi_line_text_button_text_id_set    | 텍스트 단추에 시스템 문자열 설정                                                |
| gx_multi_line_text_button_text_set        | 텍스트 단추에 사용자 정의 문자열 할당(사용되지 않음)                          |
| gx_multi_line_text_button_text_set_ext   | 텍스트 단추에 사용자 정의 문자열 할당                                       |
| gx_multi_line_text_input_backspace         | 여러 줄 텍스트 입력 커서 위치 앞의 문자 삭제               |
| gx_multi_line_text_input_buffer_get       | 텍스트 입력 위젯의 버퍼 정보 검색                               |
| gx_multi_line_text_input_buffer_clear     | 텍스트 입력 버퍼에서 모든 문자 삭제                               |
| gx_multi_line_text_input_char_insert      | 여러 줄 텍스트 입력 커서 위치에 UTF8 형식 문자열 삽입(사용되지 않음) |
| gx_multi_line_text_input_char_insert_ext | 여러 줄 텍스트 입력 커서 위치에 UTF8 형식 문자열 삽입              |
| gx_multi_line_text_input_create            | 여러 줄 텍스트 입력 만들기                                                    |
| gx_multi_line_text_input_cursor_pos_get  | 여러 줄 텍스트 입력 커서 위치 검색                                  |
| gx_multi_line_text_input_delete            | 여러 줄 텍스트 입력 커서 위치 뒤의 문자 삭제                 |
| gx_multi_line_text_input_down_arrow       | 여러 줄 텍스트 입력 커서를 다음 줄로 이동                              |
| gx_multi_line_text_input_end               | 여러 줄 텍스트 입력 커서를 현재 줄의 끝으로 이동                |
| gx_multi_line_text_input_event_process    | 여러 줄 텍스트 입력 텍스트 처리                                              |
| gx_multi_line_text_input_fill_color_set  | 여러 줄 텍스트 입력의 채우기 색 설정                                       |
| gx_multi_line_text_input_home              | 여러 줄 텍스트 입력 커서를 현재 줄의 시작으로 이동              |
| gx_multi_line_text_input_left_arrow       | 여러 줄 텍스트 입력 커서를 한 문자 왼쪽으로 이동                         |
| gx_multi_line_text_input_right_arrow      | 여러 줄 텍스트 입력 커서를 한 문자 오른쪽으로 이동                        |
| gx_multi_line_text_input_style_add        | 여러 줄 텍스트 스타일 플래그 추가                                                 |
| gx_multi_line_text_input_style_remove     | 여러 줄 텍스트 스타일 플래그 제거                                              |
| gx_multi_line_text_input_style_set        | 여러 줄 텍스트 스타일 플래그 할당                                              |
| gx_multi_line_text_input_text_color_set  | 여러 줄 텍스트 입력의 텍스트 색 할당                                    |
| gx_multi_line_text_input_text_select      | 여러 줄 텍스트 입력 텍스트 선택                                               |
| gx_multi_line_text_input_text_set         | 여러 줄 텍스트 입력에 텍스트 할당(사용되지 않음)                               |
| gx_multi_line_text_input_text_set_ext          | 여러 줄 텍스트 입력에 텍스트 할당                         |
| gx_multi_line_text_input_up_arrow               | 여러 줄 텍스트 입력 커서를 이전 줄로 이동       |
| gx_multi_line_text_view_create                   | 여러 줄 텍스트 뷰 만들기                                  |
| gx_multi_line_text_view_event_process           | 여러 줄 텍스트 뷰 이벤트 처리                           |
| gx_multi_line_text_view_font_set                | 여러 줄 텍스트 뷰에서 사용되는 글꼴 설정                        |
| gx_multi_line_text_view_line_space_set         | 여러 줄 텍스트 뷰 줄 간격 설정                          |
| gx_multi_line_text_view_scroll_info_get        | 여러 줄 텍스트 뷰 스크롤 정보 가져오기                         |
| gx_multi_line_text_view_text_color_set         | 여러 줄 텍스트 뷰의 텍스트 색 설정                       |
| gx_multi_line_text_view_text_id_set            | 여러 줄 텍스트 뷰의 시스템 텍스트 문자열 설정               |
| gx_multi_line_text_view_text_set                | 여러 줄 텍스트 뷰에 사용자 정의 문자열 설정(사용되지 않음) |
| gx_multi_line_text_view_text_set_ext           | 여러 줄 텍스트 뷰에 사용자 정의 문자열 설정              |
| gx_multi_line_text_view_whitespace_set          | 여러 줄 텍스트 뷰 공백 설정                          |
| gx_numeric_pixelmap_prompt_create                 | 숫자 pixelmap 프롬프트 만들기                               |
| gx_numeric_pixelmap_prompt_format_ function_set | 숫자 pixelmap 프롬프트의 format 함수 재정의          |
| gx_numeric_pixelmap_prompt_value_set             | 숫자 프롬프트 값 설정                                     |
| gx_numeric_prompt_create                           | 숫자 프롬프트 만들기                                        |
| gx_numeric_prompt_format_function_set            | 숫자 프롬프트의 format 함수 재정의                   |
| gx_numeric_prompt_value_set                       | 숫자 프롬프트 값 설정                                     |
| gx_numeric_scroll_wheel_create                    | 숫자 스크롤 휠 위젯 만들기                           |
| gx_numeric_scroll_wheel_range_set                | 스크롤 휠 값 범위 할당                              |
| gx_pixelmap_button_create                          | pixelmap 단추 만들기                                       |
| gx_pixelmap_button_draw                            | pixelmap 단추 그리기                                         |
| gx_pixelmap_button_event_process                  | pixelmap 단추 이벤트 처리                             |
| gx_pixelmap_button_pixelmap_set                   | pixelmap 단추의 pixelmap 설정                              |
| gx_pixelmap_prompt_create                          | pixelmap 프롬프트 만들기                                       |
| gx_pixelmap_prompt_draw                            | pixelmap 프롬프트 그리기                                         |
| gx_pixelmap_prompt_pixelmap_set                   | pixelmap 프롬프트의 pixelmap 설정                              |
| gx_pixelmap_slider_create                          | pixelmap 슬라이더 만들기                                       |
| gx_pixelmap_slider_draw                            | pixelmap 슬라이더 그리기                                         |
| gx_pixelmap_slider_event_process        | pixelmap 슬라이더 이벤트 처리       |
| gx_pixelmap_slider_pixelmap_set         | pixelmap 슬라이더의 pixelmap 설정        |
| gx_progress_bar_background_draw         | 진행률 표시줄 배경 그리기           |
| gx_progress_bar_create                   | 진행률 표시줄 만들기                  |
| gx_progress_bar_draw                     | 진행률 표시줄 그리기                    |
| gx_progress_bar_event_process           | 진행률 표시줄 이벤트 처리           |
| gx_progress_bar_font_set                | 진행률 표시줄 텍스트 글꼴 설정          |
| gx_progress_bar_info_set                | 진행률 표시줄 정보 구조체 설정 |
| gx_progress_bar_pixelmap_set            | 진행률 표시줄을 그리는 데 사용되는 pixelmap 설정 |
| gx_progress_bar_range_set               | 진행률 표시줄의 값 범위 설정        |
| gx_progress_bar_text_color_set         | 진행률 표시줄 텍스트 색 설정            |
| gx_progress_bar_text_draw               | 진행률 표시줄 텍스트 그리기                 |
| gx_progress_bar_value_set               | 진행률 표시줄 값 설정                 |
| gx_prompt_create                          | 프롬프트 만들기                          |
| gx_prompt_draw                            | 프롬프트 그리기                            |
| gx_prompt_event_process                   | 프롬프트 이벤트 처리                   |
| gx_prompt_font_set                       | 프롬프트 글꼴 설정                        |
| gx_prompt_text_color_set                | 프롬프트 텍스트 색 설정                  |
| gx_prompt_text_draw                      | 프롬프트 그리기의 텍스트 그리기 부분    |
| gx_prompt_text_get                       | 프롬프트 텍스트 가져오기(사용되지 않음)           |
| gx_prompt_text_get_ext                  | 프롬프트 텍스트 가져오기                        |
| gx_prompt_text_id_set                   | 시스템 텍스트 문자열을 사용하여 프롬프트 설정     |
| gx_prompt_text_set                       | 프롬프트 텍스트 설정(사용되지 않음)           |
| gx_prompt_text_set_ext                  | 프롬프트 텍스트 설정                        |
| gx_radial_progress_bar_anchor_set      | 시작 각도 설정                     |
| gx_radial_progress_bar_background_draw | 방사형 진행률 표시줄 배경 그리기    |
| gx_radial_progress_bar_create           | 방사형 진행률 표시줄 만들기           |
| gx_radial_progress_bar_draw             | 방사형 진행률 표시줄 그리기             |
| gx_radial_progress_bar_event_process   | 방사형 진행률 표시줄 이벤트 처리      |
| gx_radial_progress_bar_font_set        | 방사형 진행률 표시줄 글꼴 설정           |
| gx_radial_progress_bar_info_set        | 방사형 진행률 표시줄 정보 설정    |
| gx_radial_progress_bar_text_color_set | 방사형 진행률 표시줄 텍스트 색 설정     |
| gx_radial_progress_bar_text_draw       | 방사형 진행률 표시줄 텍스트 그리기          |
| gx_radial_progress_bar_value_set       | 방사형 진행률 표시줄 값 설정          |
| gx_radio_button_create                   | 라디오 단추 만들기                    |
| gx_radio_button_draw                     | 라디오 단추 그리기                      |
| gx_radio_button_pixelmap_set            | 라디오 단추의 pixelmap 설정           |
| gx_radial_slider_anchor_angles_set     | 방사형 슬라이더 앵커 각도 목록 설정    |
| gx_radial_slider_angle_set              | 방사형 슬라이더 각도 설정                |
| gx_radial_slider_animation_set          | 방사형 슬라이더 애니메이션 정보 설정       |
| gx_radial_slider_animation_start               | 애니메이션을 사용하여 방사형 슬라이더 각도 설정                      |
| gx_radial_slider_create                         | 방사형 슬라이더 만들기                                      |
| gx_radial_slider_draw                           | 방사형 슬라이더 그리기                                        |
| gx_radial_slider_event_process                 | 방사형 슬라이더 이벤트 처리                               |
| gx_radial_slider_info_get                      | 방사형 슬라이더 정보 포인터 검색                  |
| gx_radial_slider_info_set                      | 방사형 슬라이더 정보 설정                               |
| gx_radial_slider_pixelmap_set                  | 방사형 슬라이더 pixelmap 설정                                 |
| gx_rich_text_view_create                       | 서식 있는 텍스트 뷰 만들기                                     |
| gx_rich_text_view_draw                         | 서식 있는 텍스트 뷰 그리기                                         |
| gx_rich_text_view_set_fonts                    | 서식 있는 텍스트 뷰 글꼴 설정                                    |
| gx_rich_text_view_text_draw                    | 서식 있는 텍스트 뷰 텍스트 그리기                                    |
| gx_screen_stack_create                          | GUIX 화면 스택 제어 블록 및 메모리 영역 만들기 |
| gx_screen_stack_pop                             | 화면 스택에서 맨 위에 있는 화면 팝                   |
| gx_screen_stack_push                            | 현재 화면을 화면 스택으로 푸시                |
| gx_screen_stack_reset                           | 화면 스택 다시 설정                                      |
| gx_scroll_wheel_create                          | 기준 스크롤 휠 위젯 만들기                             |
| gx_scroll_wheel_event_process                  | 스크롤 휠 이벤트 처리                               |
| gx_scroll_wheel_gradient_alpha_set            | 스크롤 휠 오버레이 그라데이션 수정                        |
| gx_scroll_wheel_row_height_set                | 스크롤 휠 행 높이 할당                              |
| gx_scroll_wheel_selected_background_set       | 선택한 행의 배경 이미지 할당                    |
| gx_scroll_wheel_selected_get                   | 선택한 행 인덱스 검색                                 |
| gx_scroll_wheel_selected_set                   | 선택한 행 인덱스 할당                                   |
| gx_scroll_wheel_speed_set                      | 스크롤 속도 할당                                      |
| gx_scroll_wheel_total_rows_set                | 사용 가능한 행의 총수 할당                       |
| gx_scrollbar_draw                                | 스크롤 막대 그리기                                              |
| gx_scrollbar_event_process                      | 스크롤 막대 이벤트 처리                                     |
| gx_scrollbar_limit_check                        | 스크롤 막대 한도 확인                                       |
| gx_scrollbar_reset                               | 스크롤 막대 다시 설정                                             |
| gx_scrollbar_value_set                          | 스크롤 막대 값 할당                                      |
| gx_single_line_text_input_backspace           | 백스페이스 문자 처리                                  |
| gx_single_line_text_input_buffer_clear       | 문자 버퍼 지우기                                  |
| gx_single_line_text_input_buffer_get         | 버퍼 포인터 검색                                     |
| gx_single_line_text_input_character_delete   | 문제 삭제                                            |
| gx_single_line_text_input_character_insert   | 문자 삽입                                            |
| gx_single_line_text_input_create              | 한 줄 텍스트 입력 만들기                               |
| gx_single_line_text_input_draw                | 한 줄 텍스트 입력 위젯 그리기                          |
| gx_single_line_text_input_draw_position_get | 텍스트 그리기 시작 위치 검색                           |
| gx_single_line_text_input_end                 | 커서를 끝으로 이동                                          |
| gx_single_line_text_input_event_process      | 텍스트 입력 이벤트 처리                                 |
| gx_single_line_text_input_fill_color_set    | 한 줄 텍스트 입력의 채우기 색 설정                  |
| gx_single_line_text_input_home                | 커서를 홈으로 이동                                         |
| gx_single_line_text_input_left_arrow         | 왼쪽 화살표 키 처리                                       |
| gx_single_line_text_input_position_get       | 커서 위치 가져오기                                         |
| gx_single_line_text_input_right_arrow        | 오른쪽 화살표 키 처리                                      |
| gx_single_line_text_input_style_add          | 스타일 플래그 추가                                             |
| gx_single_line_text_input_style_remove       | 스타일 플래그 제거                                          |
| gx_single_line_text_input_style_set          | 스타일 플래그 할당                                          |
| gx_single_line_text_input_text_color_set  | 한 줄 텍스트 입력의 텍스트 색 설정                      |
| gx_single_line_text_input_text_select     | 한 줄 텍스트 입력 텍스트 선택                              |
| gx_single_line_text_input_text_set        | 한 줄 텍스트 입력 텍스트 설정(사용되지 않음)                    |
| gx_single_line_text_input_text_set_ext    | 한 줄 텍스트 입력 텍스트 설정                                 |
| gx_slider_create                          | 슬라이더 만들기                                                   |
| gx_slider_draw                            | 슬라이더 그리기                                                     |
| gx_slider_event_process                   | 슬라이더 이벤트 처리                                            |
| gx_slider_info_set                        | 슬라이더 정보 블록 설정                                    |
| gx_slider_needle_draw                     | 슬라이더 바늘 그리기                                              |
| gx_slider_needle_position_get             | 슬라이더 바늘 위치 가져오기                                      |
| gx_slider_tickmarks_draw                  | 슬라이더 눈금 표시 그리기                                           |
| gx_slider_travel_get                      | 슬라이더 이동 가져오기                                               |
| gx_slider_value_calculate                 | 슬라이더 값 계산                                          |
| gx_slider_value_set                       | 슬라이더 값 설정                                                |
| gx_sprite_create                          | GX_SPRITE 위젯 만들기                                         |
| gx_sprite_current_frame_set               | 스프라이트 위젯에 대해 현재 디스플레이 프레임 할당                  |
| gx_sprite_frame_list_set                  | 스프라이트 프레임 목록 할당 또는 수정                            |
| gx_sprite_start                           | 스프라이트 시퀀스 시작                                         |
| gx_sprite_stop                            | 스프라이트 시퀀스 중지                                          |
| gx_string_scroll_wheel_create             | `GX_STRING_SCROLL_WHEEL` 위젯 만들기                          |
| gx_string_scroll_wheel_event_process      | 문자열 스크롤 휠 이벤트 처리                               |
| gx_string_scroll_wheel_string_id_list_set | 문자열 ID 배열 할당                                      |
| gx_string_scroll_wheel_string_list_set    | 표시된 문자열 배열 수정                                   |
| gx_string_scroll_wheel_text_get           | 스크롤 휠 행의 텍스트 검색                              |
| gx_studio_widget_create                   | Studio 내에서 정의된 위젯 만들기                             |
| gx_studio_named_widget_create             | Studio 내에서 정의된 화면 만들기                             |
| gx_studio_display_configure               | `GX_DISPLAY`, `GX_CANVAS`, `GX_WINDOW_ROOT` 만들기 및 초기화 |
| gx_system_active_language_set             | 활성 언어 ID 할당                                       |
| gx_system_canvas_refresh                  | 더티 캔버스 강제 새로 고침(그리기)                       |
| gx_system_dirty_mark                      | 영역을 더티로 표시                                                 |
| gx_system_dirty_partial_add               | 부분 영역을 더티로 표시                                         |
| gx_system_draw_context_get                | 그리기 컨텍스트 가져오기                                             |
| gx_system_event_fold                      | 이벤트 접기                                                       |
| gx_system_event_send                      | 이벤트 보내기                                                      |
| gx_system_focus_claim                     | 포커스 클레임                                                     |
| gx_system_initialize                      | GUIX 초기화                                                 |
| gx_system_language_table_get              | 언어 테이블 검색                                         |
| gx_system_language_table_set              | 언어 테이블 할당                                           |
| gx_system_memory_allocator_set            | 메모리 할당자/할당 취소자 할당                            |
| gx_system_pen_configure                  | 펜 구성 설정                                  |
| gx_system_screen_stack_create           | 화면 스택 제어 만들기                            |
| gx_system_screen_stack_get              | 화면 스택 포인터 검색                         |
| gx_system_screen_stack_pop              | 화면 스택에서 맨 위에 있는 화면 팝                       |
| gx_system_screen_stack_push             | 표시된 화면을 화면 스택으로 푸시              |
| gx_system_screen_stack_reset            | 화면 스택 다시 설정                                 |
| gx_system_scroll_appearance_get         | 스크롤 모양 가져오기                                  |
| gx_system_scroll_appearance_set         | 스크롤 모양 설정                                  |
| gx_system_start                           | GUIX 시작                                             |
| gx_system_string_get                     | 문자열 가져오기                                             |
| gx_system_string_table_get              | 문자열 테이블 가져오기                                       |
| gx_system_string_table_set              | 문자열 테이블 설정                                       |
| gx_system_string_width_get              | 문자열 너비 가져오기(사용되지 않음)                          |
| gx_system_string_width_get_ext         | 문자열 너비 가져오기                                       |
| gx_system_theme_install                  | 글꼴/색/pixelmap 테이블 설치                     |
| gx_system_timer_start                    | 타이머 시작                                            |
| gx_system_timer_stop                     | 타이머 중지                                             |
| gx_system_version_string_get            | GUIX 라이브러리 버전 문자열 검색(사용되지 않음)      |
| gx_system_version_string_get_ext       | GUIX 라이브러리 버전 문자열 검색                   |
| gx_system_widget_find                    | 위젯 찾기                                            |
| gx_text_button_create                    | 텍스트 단추 만들기                                     |
| gx_text_button_draw                      | 텍스트 단추 그리기                                       |
| gx_text_button_event_process             | 텍스트 단추 이벤트 처리                              |
| gx_text_button_font_set                 | 텍스트 단추 글꼴 설정                               |
| gx_text_button_text_color_set          | 텍스트 단추 색 설정                                  |
| gx_text_button_text_draw                | 단추 그리기의 텍스트 그리기 부분                 |
| gx_text_button_text_get                 | 텍스트 단추에서 사용되는 텍스트 가져오기(사용되지 않음)              |
| gx_text_button_text_get_ext            | 텍스트 단추에서 사용되는 텍스트 가져오기                           |
| gx_text_button_text_id_set             | 텍스트 단추에 시스템 문자열 할당                    |
| gx_text_button_text_set                 | 텍스트 단추에 사용자 정의 문자열 할당(사용되지 않음) |
| gx_text_button_text_set_ext            | 텍스트 단추에 사용자 정의 문자열 할당              |
| gx_text_scroll_wheel_callback_set      | 문자열 검색 콜백 할당(사용되지 않음)          |
| gx_text_scroll_wheel_callback_set_ext | 문자열 검색 콜백 할당                       |
| gx_text_scroll_wheel_create             | 기준 텍스트 스크롤 휠 만들기                          |
| gx_text_scroll_wheel_draw               | 텍스트 스크롤 휠 그리기 함수                  |
| gx_text_scroll_wheel_event_process      | 텍스트 스크롤 휠 이벤트 처리                        |
| gx_text_scroll_wheel_font_set          | 텍스트 스크롤 휠 글꼴 할당                         |
| gx_text_scroll_wheel_text_color_set   | 텍스트 스크롤 휠 텍스트 색 할당                   |
| gx_tree_view_create                    | 트리 뷰 만들기                          |
| gx_tree_view_draw                      | 트리 뷰 그리기                              |
| gx_tree_view_event_process            | 트리 뷰 이벤트 처리                     |
| gx_tree-view_indentation_set           | 트리 뷰 들여쓰기 설정                   |
| gx_tree_view_position                  | 트리 뷰 항목 배치                    |
| gx_tree_view_root_line_color_set    | 트리 뷰 루트 선 색 설정               |
| gx_tree_view_root_pixelmap_set       | 트리 뷰 루트 pixelmap 설정                |
| gx_tree_view_selected_get             | 선택된 항목 검색                      |
| gx_tree_view_selected_set             | 선택된 항목 설정                           |
| gx_utility_canvas_to_bmp              | 캔버스 메모리를 비트맵 형식으로 변환      |
| gx_utility_circle_point_get           | 원의 계산 지점               |
| gx_utility_gradient_create             | 그라데이션 pixelmap 만들기                  |
| gx_utility_gradient_delete              | 그라데이션 pixelmap 삭제                  |
| gx_utility_ltoa                         | 정수(Long)를 ASCII로 변환               |
| gx_utility_math_acos                   | 아크코사인 컴퓨팅                          |
| gx_utility_math_asin                   | 아크사인 컴퓨팅                             |
| gx_utility_math_cos                    | 코사인 컴퓨팅                              |
| gx_utility_math_sin                    | 사인 컴퓨팅                                |
| gx_utility_math_sqrt                   | 제곱근 컴퓨팅                         |
| gx_utility_bidi_paragraph_reorder         | 양방향 텍스트를 표시 순서로 다시 정렬|
| gx_utility_bidi_resolved_text_info_delete | 다시 정렬된 양방향 텍스트 삭제               |
| gx_utility_pixelmap_resize             | pixelmap 크기 조정                             |
| gx_utility_pixelmap_rotate             | 임의 각도만큼 pixelmap 회전          |
| gx_utility_pixelmap_simple_rotate      | 90, 180, 270도 pixelmap 회전     |
| gx_utility_rectangle_center            | 다른 사각형 가운데에 사각형 맞춤   |
| gx_utility_rectangle_center_find      | 사각형 가운데 찾기                    |
| gx_utility_rectangle_combine           | 두 사각형을 첫 번째 사각형으로 결합           |
| gx_utility_rectangle_compare           | 두 사각형 비교                      |
| gx_utility_rectangle_define            | 사각형 정의                            |
| gx_utility_rectangle_resize            | 사각형 크기 조정                            |
| gx_utility_rectangle_overlap_detect   | 사각형 겹침 검색                |
| gx_utility_rectangle_point_detect     | 점이 사각형 안에 있는 경우 검색        |
| gx_utility_rectangle_shift             | 사각형 이동                             |
| gx_utility_string_to_alphamap         | 텍스트 문자열을 alphamap으로 렌더링(사용되지 않음) |
| gx_utility_string_to_alphamap_ext    | 텍스트 문자열을 alphamap으로 렌더링              |
| gx_vertical_list_children_position    | 세로 목록에 자식 배치          |
| gx_vertical_list_create                | 세로 목록 만들기                        |
| gx_vertical_list_event_process        | 세로 목록 이벤트 처리                 |
| gx_vertical_list_selected_index_get  | 선택된 항목 인덱스 가져오기                     |
| gx_vertical_list_selected_widget_get | 선택한 위젯 가져오기                         |
| gx_vertical_list_selected_set         | 세로 목록의 항목 설정                  |
| gx_vertical_list_total_rows_set      | 만든 후에 목록 행 수 변경   |
| gx_vertical_scrollbar_create           | 세로 스크롤 막대 만들기                   |
| gx_widget_allocate                      | 동적으로 위젯 할당               |
| gx_widget_attach                        | 부모에 위젯 연결                     |
| gx_widget_background_draw              | 위젯 배경 그리기                      |
| gx_widget_back_attach                  | 뒤쪽에 위젯 연결                       |
| gx_widget_back_move                    | 위젯을 뒤로 이동                         |
| gx_widget_block_move                   | 픽셀 블록 이동                        |
| gx_widget_border_draw                  | 위젯 테두리 그리기                          |
| gx_widget_border_style_set            | 위젯 테두리 스타일 설정                     |
| gx_widget_border_width_get            | 위젯 테두리 두께 설정                     |
| gx_widget_canvas_get               | 위젯 캔버스 가져오기                                                         |
| gx_widget_child_detect             | 위젯 자식 검색                                                       |
| gx_widget_children_draw            | 위젯 자식 그리기                                                      |
| gx_widget_client_get               | 위젯 클라이언트 영역 가져오기                                                    |
| gx_widget_color_get                | 표시되는 위젯의 색 ID를 색 값으로 확인                      |
| gx_widget_create                    | 위젯 만들기                                                             |
| gx_widget_created_test             | 위젯이 생성되었는지 테스트                                                    |
| gx_widget_delete                    | 위젯 삭제                                                             |
| gx_widget_detach                    | 부모에서 위젯 분리                                                 |
| gx_widget_draw                      | 위젯 그리기                                                               |
| gx_widget_draw_set                 | 위젯 그리기 함수 설정                                               |
| gx_widget_event_generate           | 위젯 이벤트 생성                                                     |
| gx_widget_event_process            | 위젯 이벤트 처리                                                      |
| gx_widget_event_process_set       | 위젯 이벤트 처리 함수 설정                                   |
| gx_widget_event_to_parent         | 위젯의 부모에게 이벤트 보내기                                             |
| gx_widget_fill_color_set          | 위젯 채우기 색 할당                                                  |
| gx_widget_find                      | 위젯 찾기                                                               |
| gx_widget_first_child_get         | 첫 번째 자식에 대한 포인터 반환                                             |
| gx_widget_focus_next               | 입력 포커스를 다음 위젯으로 이동                                           |
| gx_widget_focus_previous           | 입력 포커스를 이전 위젯으로 이동                                       |
| gx_widget_font_get                 | 표시되는 위젯의 글꼴 ID를 글꼴 포인터로 확인                    |
| gx_widget_free                      | 위젯 제어 블록 메모리 해제                                          |
| gx_widget_front_move               | 위젯을 앞으로 이동                                                      |
| gx_widget_height_get               | 위젯 높이 가져오기                                                         |
| gx_widget_hide                      | 위젯 숨기기                                                               |
| gx_widget_last_child_get          | 마지막 자식에 대한 포인터 반환                                              |
| gx_widget_next_sibling_get        | 다음 형제에 대한 포인터 반환                                            |
| gx_widget_parent_get               | 부모 위젯에 대한 포인터 반환                                           |
| gx_widget_pixelmap_get             | 표시되는 위젯의 pixelmap ID를 pixelmap 포인터로 확인            |
| gx_widget_previous_sibling_get    | 이전 형제에 대한 포인터 반환                                        |
| gx_widget_resize                    | 위젯 크기 조정                                                             |
| gx_widget_shift                     | 위젯 이동                                                              |
| gx_widget_show                      | 위젯 표시                                                               |
| gx_widget_status_add               | 위젯 상태 추가                                                         |
| gx_widget_status_get               | 위젯 상태 플래그 검색                                              |
| gx_widget_status_remove            | 위젯 상태 제거                                                      |
| gx_widget_string_get               | 표시되는 위젯의 문자열 ID와 연결된 문자열 검색(사용되지 않음) |
| gx_widget_string_get_ext          | 표시되는 위젯의 문자열 ID와 연결된 문자열 검색             |
| gx_widget_status_test              | 위젯 상태 테스트                                                        |
| gx_widget_style_add                | 위젯 스타일 추가                                                          |
| gx_widget_style_get                | 위젯 스타일 플래그 검색                                               |
| gx_widget_style_remove             | 위젯 스타일 제거                                                       |
| gx_widget_style_set                | 위젯 스타일 설정                                                          |
| gx_widget_text_blend               | 위젯 위에 혼합 텍스트 렌더링(사용되지 않음)                              |
| gx_widget_text_blend_ext          | 위젯 위에 혼합 텍스트 렌더링                                           |
| gx_widget_text_draw                | 위젯 위에 텍스트 렌더링(사용되지 않음)                                      |
| gx_widget_text_draw_ext           | 위젯 위에 텍스트 렌더링                                            |
| gx_widget_text_id_draw            | 위젯 위에 문자열 ID로 식별된 텍스트 렌더링                           |
| gx_widget_top_visible_child_find | Z 순서의 맨 위에 그려지는 표시되는 자식에 대한 포인터 반환   |
| gx_widget_type_find                | 위젯 형식 찾기                                                          |
| gx_widget_width_get                | 위젯 너비 가져오기                                                          |
| gx_window_canvas_set               | 창 캔버스 설정                                                         |
| gx_window_client_height_get       | 창 클라이언트 높이 가져오기                                                  |
| gx_window_client_scroll            | 창 클라이언트 스크롤                                                     |
| gx_window_client_width_get        | 창 클라이언트 너비 가져오기                                                   |
| gx_window_close                     | 모달 창 실행 종료                                          |
| gx_window_create                    | 창 만들기                                                             |
| gx_window_draw                      | 창 그리기                                                               |
| gx_window_event_process            | 창 이벤트 처리                                                      |
| gx_window_execute                   | 모달 창 실행                                                    |
| gx_window_root_create              | 루트 창 만들기                                                        |
| gx_window_root_delete              | 루트 창 삭제                                                       |
| gx_window_root_event_process      | 루트 창 이벤트 처리                                             |
| gx_window_root_find                | 루트 창 찾기                                                          |
| gx_window_scroll_info_get         | 창 스크롤 정보 가져오기                                                    |
| gx_window_scrollbar_find           | 창 스크롤 막대 찾기                                                     |
| gx_window_wallpaper_get            | 창 배경 화면 가져오기                                                      |
| gx_window_wallpaper_set            | 창 배경 화면 설정                                                      |

## <a name="gx_accordion_menu_create"></a>gx_accordion_menu_create

아코디언 메뉴 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_accordion_menu_create(
    GX_ACCORDION_MENU *accordion,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    ULONG style ,
    USHORT accordion_menu_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 지정된 대로 아코디언 메뉴를 만들고 제공된 부모 위젯에 아코디언 메뉴를 연결합니다. 아코디언 메뉴는 확장/축소되는 메뉴 표시 위젯입니다. 모든 형식의 위젯을 자식 메뉴 항목으로 허용합니다. 아코디언 메뉴를 중첩할 수 있으므로 여러 수준의 메뉴 깊이를 만들 수 있습니다.

메뉴 항목 위젯에 자식 항목을 삽입하려면 GX_MENU 형식 위젯을 부모 메뉴 항목으로 사용하는 것이 좋습니다.

단일 수준의 아코디언 메뉴를 만들기 위한 팁:

1.  아코디언 메뉴를 만듭니다.

2.  아코디언 메뉴에 GX_MENU 형식 위젯을 연결합니다.

3.  GX_MENU 형식 부모에 자식 위젯을 연결합니다. 자식 항목 종류는 모든 GUIX 위젯 형식일 수 있습니다.

여러 수준의 아코디언 메뉴를 만들기 위한 팁:

1.  아코디언 메뉴를 만듭니다.

2.  아코디언 메뉴에 GX_MENU 형식 위젯을 연결합니다.

3.  GX_MENU 형식 부모에 GX_ACCORDION_MENU 형식 위젯을 연결합니다.

4.  단일 수준의 아코디언 메뉴 만들기에 설명된 대로 GX_ACCORDION_MENU 형식 부모에 메뉴 항목을 연결합니다.

### <a name="parameters"></a>매개 변수

- **accordion** 아코디언 메뉴 제어 블록에 대한 포인터
- **name** 아코디언 메뉴의 이름
- **parent** 부모 위젯에 대한 포인터
- **style** 위젯의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **accordion_menu_id** 애플리케이션에서 정의된 아코디언 메뉴 ID
- **size** 아코디언 메뉴의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 아코디언 메뉴를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_ACCORDION_MENU my_accordion;
GX_MENU menu_1;
GX_MENU item_1;
GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 100, 100, 300, 150);

status = gx_accordion_menu_create(&my_accordion, “my_accordion”,
                                  parent, GX_STYLE_ENABLED,
                                  MY_ACCORDION_ID, &size);

gx_menu_create(&menu_1, “menu_1”, &my_accordion,
               GX_STRING_ID_MENU_1, GX_ID_NONE,
               GX_STYLE_ENABLED | GX_TYLE_BORDER_THIN, 0, &size);

gx_menu_create(&item_1, “item_1”, &my_accordion,
               GX_STRING_ID_ITEM_1, GX_ID_NONE,
               GX_STYLE_ENABLED | GX_STYLE_BORDER_THIN, 0, &size);

gx_text_offset_set(&item_1, 30, 0);

gx_menu_insert(&menu_1, &item_1);

/* If status is GX_SUCCESS the accordion menu was successfully created. */

```

GUIX Studio 설치의 일부로 제공되는 데모 애플리케이션 demo_guix_widget_types는 아코디언 메뉴 위젯을 사용하는 전체 예제를 제공합니다.

### <a name="see-also"></a>참고 항목

- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_draw"></a>gx_accordion_menu_draw

아코디언 메뉴 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_accordion_menu_draw(GX_ACCORDION_MENU *accordion);
```

### <a name="description"></a>Description

이 서비스는 지정된 아코디언 메뉴를 그립니다. 일반적으로 GUIX 캔버스 새로 고침 메커니즘을 통해 내부적으로 호출되지만 사용자 지정 아코디언 메뉴 위젯용 사용자 지정 그리기 함수를 구현하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **accordion** 아코디언 메뉴 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Define a custom accordion menu draw function */

VOID my_accordion_menu_draw(GX_ACCORDION_MENU *accordion)
{
    /* Call default accordion menu draw. */
    gx_accordion_menu_draw(accordion);

    /* Add custom drawing here. */
}

```

### <a name="see-also"></a>참고 항목

- gx_accordion_menu_create
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_event_process"></a>gx_accordion_menu_event_process

아코디언 메뉴 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_accordion_menu_event_process(
    GX_ACCORDION_MENU *accordion, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 아코디언 메뉴에 대한 이벤트를 처리합니다. 사용자 지정 아코디언 메뉴 이벤트 처리 함수에서 기본 이벤트 처리기로 호출되어야 합니다.

이 서비스는 GX_EVENT_PEN_DOWN 및 GX_EVENT_PEN_UP 이벤트를 처리하여 메뉴 항목을 확장/축소합니다.

### <a name="parameters"></a>매개 변수

- **accordion** 아코디언 메뉴 제어 블록에 대한 포인터
- **event_ptr** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 아코디언 메뉴 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic accordion menu event processing as part of custom event processing function. */

UINT custom_accordion_event_process( 
    GX_ACCORDION_MENU *accordion,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default accordion menu
            event processing */
        status =
        gx_accordion_menu_event_process(accordion, event);
        break;
    }
    return status;
}

```

### <a name="see-also"></a>참고 항목

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_position"></a>gx_accordion_menu_position

메뉴 항목 배치

### <a name="prototype"></a>프로토타입

```C
UINT gx_accordion_menu_position(GX_ACCORDION_MENU *accordion);
```

### <a name="description"></a>Description

이 서비스는 아코디언 메뉴의 메뉴 항목을 배치합니다. 일반적으로 아코디언 메뉴가 표시될 때 내부적으로 호출됩니다. 아코디언 메뉴에서 항목을 삽입/제거하거나 자식 항목의 확장 스타일을 변경하려는 경우 이 함수를 호출하여 자식 항목의 위치를 변경해야 합니다.

### <a name="parameters"></a>매개 변수

- **accordion** 아코디언 메뉴 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 아코디언 메뉴를 배치했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Position menu items in the accordion menu “my_accordion” */
status = gx_accordion_menu_position (&my_accordion);

/* If status is GX_SUCCESS the children in the accordion menu
“my_accordion” are positioned. */

```

### <a name="see-also"></a>참고 항목

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_animation_canvas_define"></a>gx_animation_canvas_define

애니메이션 컨트롤러에 메모리 캔버스 제공

### <a name="prototype"></a>프로토타입

```C
UINT gx_animation_canvas_define(
    GX_ANIMATION *animation, 
    GX_CANVAS *canvas);
```

### <a name="description"></a>Description

이 서비스는 애니메이션 시퀀스를 구현하는 데 사용되는 애니메이션 컨트롤러에 메모리 캔버스를 제공합니다. 제공된 캔버스는 애니메이션 대상 위젯을 수용할 수 있을 만큼 충분히 커야 합니다.

애니메이션 캔버스가 정의된 경우 대상 위젯은 이 애니메이션 캔버스에 한 번 그려지고, 캔버스 오프셋 및/또는 캔버스 알파 값을 수정하여 화면 슬라이드 또는 페이드 효과를 적용합니다. 여러 그래픽 계층에 대한 하드웨어 지원이 제공되는 경우 하드웨어 그래픽 오버레이 계층에 바인딩된 애니메이션 캔버스를 정의하면 슬라이드 및 페이드 애니메이션의 성능을 ***훨씬*** 향상할 수 있습니다.

16bpp 미만의 색 농도에서 실행하는 경우 애니메이션 관리자가 페이드 인 및 페이드 아웃 애니메이션 유형을 실행하려면 애니메이션 캔버스가 필요합니다.

### <a name="parameters"></a>매개 변수

- **animation** 애니메이션 제어 블록에 대한 포인터
- **canvas** 변환 애니메이션을 구현하는 데 사용되는 메모리 캔버스

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 애니메이션 캔버스를 정의했습니다.
- **GX_INVALID_STATUS**(0x10) 애니메이션 상태가 잘못되었습니다.
- **GX_INVALID_MEMORY_SIZE**(0x29) 제공한 메모리 블록이 캔버스를 만들 수 있을 만큼 충분히 크지 않습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_ANIMATION animation;
GX_CANVAS animation_canvas;
GX_ROOT_WINDOW animation_root;
/* Create animation canvas. */
status = gx_canvas_create(
        &animation_canvas, /* Canvas control block. */
        “animation_canvas”, /* Name of canvas. */
        display, /* Display control block. */
        GX_ANIMATION_MANAGED, /* Type of canvas. */
        width, /* Width of canvas. */
        height, /* Height of canvas. */
        memory_area, /* Memory area of canvas. */
        memory_size /* Size of canvas memory. */
        );
if (status == GX_SUCCESS)
{
    /* Create the root window for the canvas. */
    status = gx_window_root_create(
        &animation_root, /* Root window control block. */
        “animation_root”, /* Name of root window. */
        &animation_canvas, /* Canvas of the root window. */ GX_STYLE_NONE, /* Style of the window. */
        GX_ID_NONE, /* Root window ID. */
        &root_size /* Window size. */
        );
}
if (status == GX_SUCCESS)
{
    /* Define canvas for the animation. */
    status = gx_animation_canvas_define(&animation,
                &animation_canvas);
}
/* If status is GX_SUCCESS the new canvas was successfully set to the animation manager. */

```

### <a name="see-also"></a>참고 항목

- gx_animation_create,
- gx_animation_delete
- gx_animation_drag_disable,
- gx_animation_drag_enable
- gx_animation_landing_speed_set,
- gx_animation_start
- gx_animation_stop

## <a name="gx_animation_create"></a>gx_animation_create

애니메이션 컨트롤러 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_animation_create(GX_ANIMATION *animation);
```

### <a name="description"></a>Description

이 서비스는 애니메이션 컨트롤러를 만듭니다. 컨트롤러가 유휴 상태로 초기화됩니다. 유휴 상태가 아닌 컨트롤러는 애니메이션을 시작할 수 없습니다. GX_ANIMATION 제어 블록 포인터는 gx_system_animation_get()을 사용하여 가져올 수 있거나 정적으로 정의된 제어 블록일 수 있습니다.

### <a name="parameters"></a>매개 변수

- **animation** 애니메이션 제어 블록에 대한 포인터


### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 애니메이션 컨트롤러를 만들었습니다.
- **GX_ALREADY_CREATED**(0x13) 제어 블록이 이미 초기화되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_ANIMATION *animation;

/* Allocate an animaton control from system pool */
gx_system_animation_get(&animation);

/* Initialize the control block */

if (animation)
{
    status = gx_animation_create(&animation);
}

/* If status is GX_SUCCESS the new animation controller was successfully created and initialized. */

```

### <a name="see-also"></a>참고 항목

- gx_animation_canvas_define,
- gx_animation_delete
- gx_animation_drag_disable,
- gx_animation_drag_enable
- gx_animation_start
- gx_animation_landing_speed_set,
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_drag_disable"></a>gx_animation_drag_disable

화면 끌기 애니메이션 후크 사용 안 함

### <a name="prototype"></a>프로토타입

```C
UINT gx_animation_drag_disable(
    GX_ANIMATION *animation, 
    GX_WIDGET *widget);
```

### <a name="description"></a>Description

이 서비스는 위젯의 기본 이벤트 처리 함수에서 화면 끌기 애니메이션 후크 프로시저를 제거하고 애니메이션 시퀀스를 중지합니다. 화면 끌기 애니메이션 후크 프로시저는 화면 끌기 애니메이션 이벤트를 처리합니다.

### <a name="parameters"></a>매개 변수

- **animation** 애니메이션 제어 블록에 대한 포인터
- **widget** 위젯 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 성공했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_ANIMATION animation;
GX_WIDGET *animation_parent;

/* Disable screen drag animation of “animation_parent”. */
status = gx_animation_drag_disable(&animation, animation_parent);

/* If status is GX_SUCCESS the screen drag hook has been removed
    from the event process of “animation_parent”. */

```

### <a name="see-also"></a>참고 항목

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_drag_enable
- gx_animation_landing_speed_set,
- gx__animation_start
- gx_animation_stop
- gx_system_animation_get,
- gx__system_animation_free

## <a name="gx_animation_drag_enable"></a>gx_animation_drag_enable

화면 끌기 애니메이션 후크 사용

### <a name="prototype"></a>프로토타입

```C
UINT gx_animation_drag_enable(
    GX_ANIMATION *animation,
    GX_WIDGET *widget, 
    GX_ANIMATION_INFO *info);
```

### <a name="description"></a>Description

이 서비스는 내부적으로 정의된 화면 끌기 애니메이션 이벤트 처리 함수를 위젯의 기본 이벤트 처리 함수의 후크 프로시저로 설정합니다. 화면 끌기 애니메이션 이벤트 처리 함수는 화면 끌기 애니메이션 이벤트를 처리합니다.

화면 끌기 후크 프로시저는 대상 위젯에 전송된 펜 입력 이벤트의 기본 처리기가 됩니다. 원래 위젯 이벤트 처리 함수는 화면 끌기 입력 이벤트 유형을 확인한 후 데이지 체인 방식으로 호출됩니다.

### <a name="parameters"></a>매개 변수

- **animation** 애니메이션 제어 블록에 대한 포인터
- **widget** 위젯 제어 블록에 대한 포인터
- **info** 애니메이션 정보

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 성공했습니다.
- **GX_INVALID_STATUS**(0x26) 애니메이션 상태가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 값이 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 슬라이드 화면 목록을 제공하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_ANIMATION animation;
GX_ANIMATION_INFO info;
GX_WIDGET *animation_parent;
GX_WIDGET *screen_list[] = {
    screen_1,
    screen_2,
    screen_3,
    GX_NULL
}

memset(&info, 0, sizeof(GX_ANIMATION_INFO);
info.gx_animation_parent = animation_parent;

/* If GX_STYLE_ANIMATION_WRAP is set, the screen list will wrap itself. */
info.gx_animation_style = GX_ANIMATION_SCREEN_DRAG |
                          GX_ANIMATION_HORIZONTAL |
                          GX_STYLE_ANIMATION_WRAP;
info.gx_animation_frame_interval = 1;
info.gx_animation_slide_screen_list = screen_list;

status = gx_animation_drag_enable(&animation, animation_parent,
                                  info);

/* If status is GX_SUCCESS the screen slide animinatin event
    process function has been set as a hook procedure of
    “animation_parent”. */
```

### <a name="see-also"></a>참고 항목

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_drag_disable,
- gx__animation_landing_speed_set
- gx_animation_start,
- gx__animation_stop,
- gx__system_animation_get
- gx_system_animation_free

## <a name="gx_animation_landing_speed_set"></a>gx_animation_landing_speed_set

화면 끌기 애니메이션의 착륙 속도 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_animation_landing_speed_set(
    GX_ANIMATION *animation, 
    USHORT shift_per_step);
```

### <a name="description"></a>Description

이 서비스는 화면 끌기 애니메이션의 착륙 속도를 설정합니다.

### <a name="parameters"></a>매개 변수

- **animation** 애니메이션 제어 블록에 대한 포인터
- **shift_per_step** 각 단계의 이동 거리

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 성공했습니다.
- **GX_INVALID_VALUE**(0x22) 매개 변수가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set landing speed of “my_animation” to 20. */
status = gx_animation_landing_peed_set(&my_animation, 20);

/* If status is GX_SUCCESS the landing speed is successfully set to 20. */
```

### <a name="see-also"></a>참고 항목

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_slide_disable,
- gx__animation_slide_enable
- gx_animation_start,
- gx__animation_stop,
- gx__system_animation_get
- gx_system_animation_free

## <a name="gx_animation_start"></a>gx_animation_start

타이머 기반 애니메이션 시작

### <a name="prototype"></a>프로토타입

```C
UINT gx_animation_start(
    GX_ANIMATION *animation, 
    GX_ANIMATION_INFO *params);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 애니메이션 인스턴스와 새 애니메이션 매개 변수 집합을 사용하여 애니메이션 시퀀스를 시작합니다. 함수에서 매개 변수의 로컬 복사본을 만들기 때문에 매개 변수 구조를 정적으로 정의할 필요가 없습니다.

GX_ANIMATION 제어 구조는 애플리케이션에서 정적으로 정의하거나 gx_system_animation_get() API를 사용하여 가져올 수 있습니다.

GX_ANIMATION_INFO 구조는 실행할 애니메이션의 매개 변수를 정의합니다. 이 구조와 각 필드의 의미에 대한 자세한 내용은 이 설명서의 3장에서 GUIX 애니메이션 구성 요소 섹션을 참조하세요.

### <a name="parameters"></a>매개 변수

- **animation** 애니메이션 제어 블록에 대한 포인터
- **params** 매개 변수 구조에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 성공했습니다.
- **GX_INVALID_VALUE**(0x22) 매개 변수가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 애니메이션 대상이 잘못되었습니다.
- **GX_INVALID_STATUS**(0x26) 애니메이션 상태가 잘못되었습니다.
- **GX_INVALID_CANVAS**(0x20) 애니메이션 캔버스가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_ANIMATION_INFO params;
GX_ANIMATION *animation;

/* obtain an animation control block pointer */
gx_system_animation_get(&animation);
if (animation)
{
    /* define a slide down and to the right */
    params.gx_animation_start_position.gx_point_x = 0;
    params.gx_animation_start_position.gx_point_y = 0;
    params.gx_animation_end_position.gx_point_x = 100;
    params.gx_animation_end_position.gx_point_y = 200;
    params.gx_animation_style= GX_ANIMATION_TRANSLATE;
    params.gx_animation_target = &my_window;
    params.gx_animation_parent = root_window;
    params.gx_animation_start_alpha = 255;
    params.gx_animation_end_alpha = 255;

    params.gx_animation_delay_before = 0;
    params.gx_animation_steps = 10;
    params.gx_animation_tick_rate = 2;

    status = gx_animation_start(&animation, &params);
}

/* If status is GX_SUCCESS the animation is initiated. */
```

### <a name="see-also"></a>참고 항목

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_slide_disable,
- gx__animation_slide_enable
- gx_animation_landing_speed_set,
- gx__animation_stop
- gx_system_animation_get,
- gx__system_animation_free

## <a name="gx_animation_stop"></a>gx_animation_stop

활성 타이머 기반 애니메이션 중지

### <a name="prototype"></a>프로토타입

```C
UINT gx_animation_stop(GX_ANIMATION *animation);
```

### <a name="description"></a>Description

이전에 시작된 애니메이션을 중지합니다. gx_system_animation_get을 사용하여 애니메이션 제어 블록 포인터가 할당된 경우 애플리케이션은 제어 블록을 재사용하거나 gx_system_animation_free()를 사용하여 시스템 풀로 반환할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **animation** 애니메이션 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 성공했습니다. GX_PTR_ERROR(0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_STATUS**(0x26) 컨트롤러 상태가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_ANIMATION animation;

status = gx_animation_stop(&animation);

/* If status is GX_SUCCESS the animation is stopped */

```

### <a name="see-also"></a>참고 항목

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_drag_disable,
- gx__animation_drag_enable
- gx_animation_start,
- gx__system_animation_get
- gx_system_animation_free

## <a name="gx_binres_language_count_get"></a>gx_binres_language_count_get

이진 리소스 데이터에 있는 언어 수 반환

### <a name="prototype"></a>프로토타입

```C
UINT gx_binres_language_count_get(
    GX_UBYTE *root_address, 
    GX_VALUE *returned_count);
```

### <a name="description"></a>Description

이 서비스는 이진 리소스 데이터 헤더를 구문 분석하여 이진 데이터에 포함된 언어 수를 반환합니다. 사용자가 언어를 선택할 수 있도록 사용자에게 선택 목록을 표시해야 하는 애플리케이션에 유용합니다.

### <a name="parameters"></a>매개 변수

- **root_address** 메모리에 있는 이진 리소스 데이터의 주소
- **return_count** 반환된 언어 개수를 저장할 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 성공했습니다.
- **GX_INVALID_FORMAT**(0x24) 이진 리소스가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_VALUE language_count = 0;

/* Specify address that binary resource data is located. */
GX_UBYTE    *root_address = 0x60000000;

status = gx_binres_language_count_get(root_address,
    &language_count);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>참고 항목

- gx_binres_language_info_load

## <a name="gx_binres_language_info_load"></a>gx_binres_language_info_load

언어 테이블 정보 로드

### <a name="prototype"></a>프로토타입

```C
UINT gx_binres_language_info_load(
    GX_UBYTE *root_address, 
    GX_LANGUAGE_HEDAER *put_info);
```

### <a name="description"></a>Description

이 서비스는 이진 리소스 데이터 Blob을 구문 분석하여 GX_LANGUAGE_HEADER 구조체 배열을 채우고 이진 데이터에 포함된 각 언어의 언어 이름 및 문자열 테이블 크기를 애플리케이션에 알립니다. 애플리케이션은 먼저 gx_binres_language_count_get()을 호출하여 이진 데이터 내의 언어 수를 확인하고 이 함수에 전달된 put_info 포인터가 language_count GX_LANGUAGE_HEADER 구조체 배열을 가리키도록 해야 합니다.

이 서비스는 애플리케이션에서 런타임에 이진 리소스 데이터 청크의 콘텐츠를 확인하는 데 사용됩니다.

GX_LANGUAGE_HEADER 구조체는 다음과 같이 정의됩니다.

```c
typedef struct GX_LANGUAGE_HEADER_STRUCT{
    USHORT gx_language_header_magic_number;
    USHORT gx_language_header_index;
    UCHAR gx_language_header_name[GX_LANGUAGE_HEADER_NAME_SIZE];
    ULONG  gx_language_header_data_size;
} GX_LANGUAGE_HEADER;
```

- *magic_number* 필드는 이진 리소스 데이터 형식의 내부 유효성 검사에 사용됩니다.
- *header_index* 필드는 이진 데이터에서 언어가 정의된 순서를 나타냅니다.
- *header_name* 필드는 언어 이름을 포함합니다.
- *header_data_size* 필드는 언어 문자열 테이블의 데이터 크기를 포함합니다.

### <a name="parameters"></a>매개 변수

- **root_address** 메모리에 있는 이진 리소스 데이터의 주소
- **put_info** GX_LANGUAGE_HEADER 구조체 배열에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 성공했습니다.
- **GX_INVALID_FORMAT**(0x24) 이진 리소스가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_LANGUAGE_HEADER language_info[4];

/* Specify address that binary resource data is located. */
GX_UBYTE    *root_address = 0x60000000;

status = gx_binres_language_info_load(root_address,
    language_info);
/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>참고 항목

- gx_binres_language_count_get

## <a name="gx_binres_language_table_load"></a>gx_binres_language_table_load

언어 테이블 리소스 로드(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_binres_language_table_load(
    GX_UBYTE *root_address, 
    GX_UBYTE **returned_language_table);
```

### <a name="description"></a>Description

이 API(사용되지 않음)를 사용하면 애플리케이션에서 이전(릴리스 5.6 이전) 이진 리소스 데이터 파일의 문자열 테이블 데이터를 로드할 수 있습니다.

새 애플리케이션에서는 gx_binres_language_table_load_ext()를 사용해야 합니다.

이 서비스는 테이블 리소스에 대한 포인터를 포함하는 언어 테이블 구조를 빌드합니다. 생성된 데이터 구조는 “현재 위치”의 리소스 데이터를 가리키고 리소스 데이터를 복사하지 않습니다. 일반 액세스 메모리 위치에 리소스 데이터를 배치해야 하며, 이 메모리 위치의 기준 주소가 API에 전달됩니다.

서비스를 사용하려면 런타임에 할당된 메모리 블록이 언어 테이블 구조를 포함할 수 있을 만큼 충분히 커야 하므로 서비스를 요청하기 전에 gx_system_memory_allocator_set API를 한 번 호출해야 합니다.

반환된 언어 테이블은 하나 이상의 문자열 테이블을 정의하고, 각 문자열 테이블은 리소스 데이터 메모리의 문자열 리소스에 대한 포인터를 포함합니다.

### <a name="parameters"></a>매개 변수

- **root_address** 메모리에 있는 이진 리소스 데이터의 주소
- **returned_language_table** 로드된 언어 테이블에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 성공했습니다.
- **GX_INVALID_FORMAT**(0x24) 이진 리소스가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_SYSTEM_MEMPRY_ERROR**(0x30) 메모리 할당자 또는 해제 함수가 정의되어 있지 않습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_UBYTE ***language_table = GX_NULL;

/* Specify address that binary resource data is located. */
GX_UBYTE *root_address = 0x60000000;

status = gx_binres_language_table_load(root_address,
                                        &language_table);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>참고 항목

- gx_binres_language_table_load_ext

## <a name="gx_binres_language_table_load_ext"></a>gx_binres_language_table_load_ext

언어 테이블 리소스 로드

### <a name="prototype"></a>프로토타입

```C
UINT gx_binres_language_table_load_ext(
    GX_UBYTE *root_address, 
    GX_STRING **returned_language_table);
```

### <a name="description"></a>Description

이 서비스는 테이블 리소스에 대한 포인터를 포함하는 언어 테이블 구조를 빌드합니다. 생성된 데이터 구조는 “현재 위치”의 리소스 데이터를 가리키고 리소스 데이터를 복사하지 않습니다. 일반 액세스 메모리 위치에 리소스 데이터를 배치해야 하며, 이 메모리 위치의 기준 주소가 API에 전달됩니다.

서비스를 사용하려면 런타임에 할당된 메모리 블록이 언어 테이블 구조를 포함할 수 있을 만큼 충분히 커야 하므로 서비스를 요청하기 전에 gx_system_memory_allocator_set API를 한 번 호출해야 합니다.

반환된 언어 테이블은 하나 이상의 문자열 테이블을 정의하고, 각 문자열 테이블은 리소스 데이터 메모리의 문자열 리소스에 대한 포인터를 포함합니다.

### <a name="parameters"></a>매개 변수

- **root_address** 메모리에 있는 이진 리소스 데이터의 주소
- **returned_language_table** 로드된 언어 테이블에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 성공했습니다.
- **GX_INVALID_FORMAT**(0x24) 이진 리소스가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_SYSTEM_MEMPRY_ERROR**(0x30) 메모리 할당자 또는 해제 함수가 정의되어 있지 않습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING **language_table = GX_NULL;

/* Specify address that binary resource data is located. */
GX_UBYTE *root_address = 0x60000000;

status = gx_binres_language_table_load_ext(root_address,
                                            &language_table);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>참고 항목

- gx_binres_theme_load

## <a name="gx_binres_theme_load"></a>gx_binres_theme_load

테마 리소스 로드

### <a name="prototype"></a>프로토타입

```C
UINT gx_binres_theme_load(
    GX_UBYTE *root_address, 
    INT theme_id, GX_THEME **returned_theme);
```

### <a name="description"></a>Description

이 서비스는 요청된 테마의 리소스 테이블에 대한 포인터를 포함하는 GX_THEME 구조체를 빌드합니다. 생성된 데이터 구조는 “현재 위치”의 리소스 데이터를 가리키고 리소스 데이터를 복사하지 않습니다. 따라서 일반 액세스 메모리 위치에 리소스 데이터를 배치해야 하며, 이 메모리 위치의 기준 주소가 API에 전달됩니다.

서비스를 사용하려면 런타임에 할당된 메모리 블록이 테마 테이블 구조를 포함할 수 있을 만큼 충분히 커야 하므로 서비스를 요청하기 전에 gx_system_memory_allocator_set API를 한 번 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **root_address** 메모리에 있는 이진 리소스 데이터의 주소
- **theme_id** 테마의 식별자
- **returned_theme** 로드된 테마에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 성공했습니다.
- **GX_INVALID_FORMAT**(0x24) 이진 리소스가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 테마 ID가 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**(0x30) 메모리 할당자 또는 해제 함수가 정의되어 있지 않습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CHAR *theme = GX_NULL;
GX_UBYTE *root_address = 0x60000000;
INT theme_id = 0;

status = gx_binres_theme_load(root_address, theme_id, &theme);

/* If status is GX_SUCCESS, the theme was successfully loaded. */
```

### <a name="see-also"></a>참고 항목

- gx_binres_language_table_read

## <a name="gx_brush_default"></a>gx_brush_default
기본 브러시 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_brush_default(GX_BRUSH *brush);
```

### <a name="description"></a>Description

이 서비스는 현재 컨텍스트의 브러시를 시스템 기본값으로 설정합니다.

### <a name="parameters"></a>매개 변수
- **brush** 브러시 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 브러시를 정의했습니다.
- **GX_PTR_ERROR**(0x07) 브러시 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/*Reset the brush to its default value. */
status = gx_brush_default(&my_brush);

/* If status is GX_SUCCESS the brush was successfully reset to its default value. */

```

### <a name="see-also"></a>참고 항목

- gx_brush_define


## <a name="gx_brush_define"></a>gx_brush_define
브러시 정의

### <a name="prototype"></a>프로토타입

```C
UINT gx_brush_define(
    GX_BRUSH *brush, 
    GX_COLOR line_color, 
    GX_COLOR fill_color, 
    UINT style);
```

### <a name="description"></a>Description

이 서비스는 지정된 선 색, 채우기 색, 스타일을 사용하여 브러시를 정의합니다.

### <a name="parameters"></a>매개 변수

- **brush** 브러시 제어 블록에 대한 포인터
- **line_color** 브러시 선 색. **부록 A** 에는 미리 정의된 색이 나와 있습니다. 애플리케이션에서 사용자 지정 색을 추가할 수도 있습니다.
- **fill_color** 브러시 채우기 색. **부록 A** 에는 미리 정의된 색이 나와 있습니다. 애플리케이션에서 사용자 지정 색을 추가할 수도 있습니다.
- **style** 브러시 스타일. **부록 D** 에서는 지원되는 브러시 스타일에 대해 설명합니다. 비트 OR 연산을 사용하여 브러시 스타일을 하나의 변수로 결합할 수 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 브러시를 정의했습니다.
- **GX_PTR_ERROR**(0x07) 브러시 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Define a brush. */
status = gx_brush_define(&my_brush, GX_COLOR_BLACK, GX_COLOR_BLACK,
                         GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the brush was successfully created. */
```

### <a name="see-also"></a>참고 항목

- gx_brush_default

## <a name="gx_button_background_draw"></a>gx_button_background_draw

 단추 배경 그리기

###<a name="prototype"></a>프로토타입

```C
VOID gx_button_background_draw(GX_BUTTON *button);
```

### <a name="description"></a>Description

이 서비스는 단추 배경을 그립니다. 일반적으로 gx_button_draw 함수에서 내부적으로 호출되지만 사용자 지정 그리기 함수를 작성하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **button** 단추 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
VOID custom_button_draw(GX_BUTTON *button)
{
    /* Draw button background. */
    gx_button_background_draw(button);

    /* Add custom drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)button);
}
```

### <a name="see-also"></a>참고 항목

- gx_button_create,
- gx__button_deselect,
- gx__button_draw
- gx_button_event_process,
- gx__button_select
- gx_icon_button_create,
- gx__pixelmap_button_create
- gx_pixelmap_button_draw,
- gx__radio_button_create
- gx_radio_button_draw,
- gx__text_button_create
- gx_text_button_color_set,
- gx__text_button_draw

## <a name="gx_button_create"></a>gx_button_create

만들기 단추

### <a name="prototype"></a>프로토타입

```C
UINT gx_button_create(
    GX_BUTTON *button, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    ULONG style, 
    USHORT button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 지정된 대로 단추를 만들고 제공된 부모 위젯과 단추를 연결합니다.

### <a name="parameters"></a>매개 변수

- **button** 단추 컨트롤 블록에 대한 포인터
- **name** 단추의 논리적 이름
- **parent** 단추의 부모 위젯에 대한 포인터
- **style** 단추 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **button_id** 애플리케이션에서 정의된 단추 ID
- **size** 단추의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 단추를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_BUTTON my_top_button;

/* Create a stop button. */
status = gx_button_create(&my_stop_button, "my stop button",
                            &my_parent_window,
                            GX_STYLE_BUTTON_TOGGLE,
                            MY_STOP_BUTTON_ID, &size);

/* If status is GX_SUCCESS the stop button was successfully created. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw,
- gx_button_deselect,
- gx_button_draw
- gx_button_event_process,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set,
- gx_text_button_draw

## <a name="gx_button_deselect"></a>gx_button_deselect


단추 선택 취소

### <a name="prototype"></a>프로토타입

```C
UINT gx_button_deselect(
    GX_BUTTON *button, 
    GX_BOOL gen_event);
```

### <a name="description"></a>Description

이 서비스는 지정된 단추를 선택 취소하고 단추 스타일에 따라 신호 이벤트를 생성합니다.


| 단추 스타일              | Signal                     |
|---------------------------|----------------------------|
| 없음                      | GX_EVENT_CLICKED         |
| GX_STYLE_BUTTON_RADIO  | GX_EVENT_RADIO_DESELECT |
| GX_STYLE_BUTTON_TOGGLE | GX_EVENT_TOGGLE_OFF     |



### <a name="parameters"></a>매개 변수

- **button** 단추 컨트롤 블록에 대한 포인터
- **gen_event** GX_TRUE이면 단추 스타일에 따라 단추에서 GX_EVENT_CLICKED, GX_EVENT_DESELECT 또는 GX_EVENT_TOGGLE_OFFSET 이벤트를 생성합니다. GX_FALSE이면 단추에서 일반적으로 생성하는 더 높은 수준의 이벤트를 생성하지 않습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 단추를 선택 취소했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Deselect button. */
status = gx_button_deselect(&my_stop_button, GX_TRUE);

/* If status is GX_SUCCESS the stop button was successfully deselected. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw,
- gx_button_create,
- gx_button_draw
- gx_button_event_process,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_button_draw"></a>gx_button_draw

단추 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_button_draw(GX_BUTTON *button);
```

### <a name="description"></a>Description

이 서비스는 지정된 단추를 그립니다. 일반적으로 GUIX 캔버스 새로 고침 메커니즘을 통해 내부적으로 호출되지만 사용자 지정 단추 위젯용 사용자 지정 그리기 함수를 구현하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **button** 단추 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom button draw function. */
VOID custom_button_draw(GX_BUTTON *button)
{
    /* Call default button draw. */
    gx_button_draw(button);

    /* Add custom drawing here. */
}

```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw,
- gx_button_create
- gx_button_deselect,
- gx_button_event_process,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set,
- gx_text_button_draw

## <a name="gx_button_event_process"></a>gx_button_event_process


단추 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_button_event_process(
    GX_BUTTON *button, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 지정된 단추에 대한 이벤트를 처리합니다.

### <a name="parameters"></a>매개 변수

- **button** 단추 컨트롤 블록에 대한 포인터
- **event_ptr** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 단추 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic button event processing as part of custom event processing function. */

UINT custom_button_event_process(GX_BUTTON *button,
                                 GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default button
            event processing */
        status = gx_button_event_process(button, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw,
- gx_button_create
- gx_button_deselect,
- gx_button_draw,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set,
- gx_text_button_draw

## <a name="gx_button_select"></a>gx_button_select

단추 선택

### <a name="prototype"></a>프로토타입

```C
UINT gx_button_select(GX_BUTTON *button);
```

### <a name="description"></a>Description

이 서비스는 지정된 단추를 선택하고 단추 스타일에 따라 신호 이벤트를 생성합니다.

라디오 단추 그룹의 형제를 선택 취소합니다.

| 단추 스타일                       | Signal                   |
|------------------------------------|--------------------------|
| GX_STYLE_BUTTON_RADIO           | GX_EVENT_RADIO_SELECT |
| GX_STYLE_BUTTON_EVENT_ON_PUSH | GX_EVENT_CLICKED       |
| GX_STYLE_BUTTON_TOGGLE          | GX_EVENT_TOGGLE_ON    |


### <a name="parameters"></a>매개 변수

- **button** 단추 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 단추를 선택했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Select button. */
status = gx_button_select(&my_stop_button);

/* If status is GX_SUCCESS the stop button was successfully selected. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw,
- gx_button_create
- gx_button_deselect,
- gx_button_draw,
- gx_button_event_process
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_canvas_alpha_set"></a>gx_canvas_alpha_set

캔버스의 알파 혼합 값 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_alpha_set(
    GX_CANVAS *canvas, 
    GX_UBYTE alpha);
```

### <a name="description"></a>Description

이 서비스는 지정된 캔버스의 알파 혼합 값을 설정합니다. 캔버스 알파 값은 0(투명)에서 255(완전 불투명) 사이일 수 있습니다.

오버레이 캔버스를 혼합하려면 하드웨어 그래픽 계층 지원이나 복합 캔버스 생성을 통한 소프트웨어 지원이 필요합니다.

캔버스 알파 값을 설정하기 전에 gx_canvas_hardware_layer_bind() API를 호출하여 캔버스 혼합에 대한 하드웨어 지원을 사용하도록 설정해야 합니다. 캔버스가 하드웨어 그래픽 계층에 바인딩된 경우 gx_canvas_alpha_set() API를 직접 호출하면 하드웨어 그래픽 계층 혼합 서비스가 호출됩니다.

캔버스 혼합에 대한 소프트웨어 지원을 활용하려면 애플리케이션에서 GX_CANVAS_COMPOSITE 스타일로 캔버스를 만들어야 합니다. 다른 모든 관리형 캔버스는 최종 표시되기 전에 해당 캔버스로 합성됩니다. 캔버스 혼합에 대한 소프트웨어 지원은 색 농도가 16bpp 이상인 디스플레이 드라이버로 실행하는 경우에만 제공됩니다.

### <a name="parameters"></a>매개 변수

- **canvas** 캔버스 제어 블록에 대한 포인터
- **alpha** 0(투명)에서 255(불투명) 사이의 알파 혼합 값

### <a name="return--values"></a>반환 값

- **GX_SUCCESS**(0x00) 알파 혼합 값을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_ERROR**(0x20) 캔버스가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the alpha-blend value of “my_canvas”. */
status = gx_canvas_alpha_set(&my_canvas, GX_ALPHA_VALUE_OPAQUE);

/* If status is GX_SUCCESS the alpha-blend value was successfully set. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_create,
- gx_canvas_drawing_complete
- gx_canvas_drawing_initiate,
- gx_canvas_offset_set
- gx_canvas_shift,
- gx_canvas_hardware_layer_bind,
- gx_canvas_show
- gx_canvas_hide

## <a name="gx_canvas_arc_draw"></a>gx_canvas_arc_draw

원호 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_arc_draw(
    INT xcenter, 
    INT ycenter, 
    UINT r,
    INT start_angle, 
    INT end_angle);
```

### <a name="description"></a>Description

이 서비스는 현재 브러시를 사용하여 캔버스에 원호를 그립니다. 원호가 잘못된 캔버스 영역으로 잘립니다. 서비스를 사용하려면 GX_ARC_DRAWING_SUPPORT를 정의해야 합니다.

### <a name="parameters"></a>매개 변수

- **xcenter** 원호 중심의 x 위치
- **ycenter** 원호 중심의 y 위치
- **r** 원호의 반지름
- **start_angle** 원호의 시작 각도
- **end_angle** 원호의 끝 각도

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 원호를 그렸습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 값이 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Draw a circle arc from 0 degree to 90 degree in clockwise. */
status = gx_canvas_arc_draw(100, 100, 50, 0, 90);

/* If status is GX_SUCCESS the arc has been drawn on “my_canvas”. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_block_move,
- gx_canvas_circle_draw
- gx_display_create,
- gx_canvas_ellipse_draw
- gx_canvas_line_draw,
- gx_canvas_pie_draw
- gx_canvas_pixelmap_draw,
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw

## <a name="gx_canvas_block_move"></a>gx_canvas_block_move

캔버스 픽셀 블록 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_block_move(GX_RECTANGLE *block,
    GX_VALUE x_shift, GX_VALUE y_shift, GX_RECTANGLE *dirty);
```

### <a name="description"></a>Description

이 서비스는 캔버스 픽셀 데이터 블록을 지정된 방향으로 이동합니다. 빠른 스크롤을 위해 GUIX에서 내부적으로 사용되지만 애플리케이션 소프트웨어에서 사용할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **block** 이동할 영역의 좌표
- **x_shift** x축에서 이동할 픽셀 수
- **y_shift** y축에서 이동할 픽셀 수
- **dirty** 블록 이동에 성공하면 함수는 이 매개 변수를 통해 여전히 더티인 원본 사각형 부분을 호출자에게 반환합니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 블록을 이동했습니다.
- **GX_FAILURE**(0x10) 블록을 이동하지 못했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
GX_RECTANGLE invalid;
GX_RECTANGLE move;

/* define 100 x 100 pixel rectangle */
gx_utility_rectangle_define(&move, 0, 0, 99, 99);

/* Move this rectangle 10 pixels to the right”. */
status = gx_canvas_block_move(&move, 10, 0, &invalid);

/* If status is GX_SUCCESS, then ‘invalid’ marks the area that needs to be redrawn after the block move. */

```

### <a name="see-also"></a>참고 항목

- gx_canvas_arc_draw,
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw

## <a name="gx_canvas_circle_draw"></a>gx_canvas_circle_draw

원 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_circle_draw(
    INT xcenter, 
    INT ycenter, 
    UINT r);
```

### <a name="description"></a>Description

이 서비스는 현재 브러시를 사용하여 캔버스에 원을 그립니다. 원이 잘못된 캔버스 영역으로 잘립니다. 서비스를 사용하려면 GX_ARC_DRAWING_SUPPORT를 정의해야 합니다.

### <a name="parameters"></a>매개 변수

- **xcenter** 원 중심의 x 좌표
- **ycenter** 원 중심의 y 좌표
- **r** 원의 반지름

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 원을 그렸습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 원 반지름이 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C

/* Draw a circle of radius 10 centered at (100, 100). */
status = gx_canvas_circle_draw(100, 100, 50);

/* If status is GX_SUCCESS the circle has been drawn on “my_canvas”. */

```

### <a name="see-also"></a>참고 항목

- gx_canvas_arc_draw,
- gx_canvas_block_move,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_darw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw


## <a name="gx_canvas_create"></a>gx_canvas_create

캔버스 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_create(
    GX_CANVAS *canvas, 
    GX_CONST GX_CHAR *name,
    GX_DISPLAY *display, 
    UINT type, 
    UINT width, 
    UINT height,
    GX_COLOR *memory_area, 
    ULONG memory_size);
```

### <a name="description"></a>Description

이 서비스는 지정된 속성 및 관련 메모리를 사용하여 캔버스를 만듭니다.

### <a name="parameters"></a>매개 변수

- **canvas** 캔버스 제어 블록에 대한 포인터
- **name** 캔버스의 논리적 이름
- **display** 이전에 만든 디스플레이에 대한 포인터
- **type** 캔버스 유형. 캔버스 유형은 다음과 같습니다.
- **GX_CANVAS_SIMPLE:** 화면 밖에 그리는 데 사용되는 메모리 캔버스입니다.
- **GX_CANVAS_MANAGED:** 복합 빌드 프로세스의 일부 또는 단일 캔버스 아키텍처에 대한 버퍼 토글 작업의 일부로 활성 디스플레이에 자동으로 플러시되는 캔버스입니다.
- **GX_CANVAS_VISIBLE:** 이 플래그를 사용하면 캔버스 그리기 내용을 잃지 않고 캔버스를 켜고 끌 수 있습니다.
- **GX_CANVAS_MODIFIED:** 나중에 사용하기 위해 예약되었습니다.
- **GX_CANVAS_COMPOSITE:** 이 플래그는 애플리케이션에서 여러 개의 관리형 캔버스를 복합 캔버스로 합성하는 다중 캔버스 시스템을 구성할 때 사용되며, 합성은 하드웨어 프레임 버퍼를 기반으로 합니다.
- **width** 너비(픽셀)
- **height** 높이(픽셀)
- **memory_area** 캔버스의 메모리 영역. 이 값은 다음과 같을 수 있습니다.
- 캔버스를 만들 때는 값이 **GX_NULL** 입니다.
- 나중에 gx_canvas_memory_define을 사용하여 값을 초기화할 수 있습니다.
- **memory_size** 메모리 영역의 크기(바이트) 또는 캔버스를 만든 후에 캔버스 메모리를 정의하는 경우 0

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 캔버스를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_CANVAS_SIZE**(0x1C) 캔버스 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_TYPE**(0x1B) 캔버스 유형이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Define global canvas memory area. */
GX_COLOR my_canvas_memory[272*480];

…

/* Create “my_canvas”. */
status = gx_canvas_create(&my_canvas, "my canvas", &my_display,
                    (GX_CANVAS_MANAGED | GX_CANVAS_VISIBLE),
                    272, 480,
                    my_canvas_memory,
                    sizeof(default_canvas_memory));

/* If status is GX_SUCCESS the 272 x 480 canvas was successfully created. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_delete,
- gx_canvas_hardware_layer_bind
- gx_canvas_memory_define

## <a name="gx_canvas_delete"></a>gx_canvas_delete

캔버스 삭제

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_delete(GX_CANVAS *canvas);
```

### <a name="description"></a>Description

이 서비스는 캔버스를 삭제합니다. GUIX에서 유지 관리하는 내부적으로 연결된 캔버스 목록에서 캔버스가 제거됩니다.

### <a name="parameters"></a>매개 변수

- **canvas** 캔버스 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 캔버스를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CANVAS**(0x20) 캔버스가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Delete “my_canvas”. */
status = gx_canvas_delete (&my_canvas);

/* If status is GX_SUCCESS my_canvas was deleted. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_alpha_set,
- gx_canvas_drawing_complete
- gx_canvas_create,
- gx_canvas_drawing_initiate
- gx_canvas_offset_set,
- gx_canvas_shift

## <a name="gx_canvas_drawing_complete"></a>gx_canvas_drawing_complete

캔버스 그리기 완료

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_drawing_complete(
    GX_CANVAS *canvas, 
    GX_BOOL flush);
```

### <a name="description"></a>Description

이 서비스를 사용하면 GUIX에서 애플리케이션이 지정된 캔버스에 그리기를 완료했음을 알 수 있습니다.

애플리케이션은 이 서비스를 사용하여 캔버스에 즉시 그릴 수 있습니다. 이렇게 하면 시스템 메모리 아키텍처에 따라 캔버스가 표시되는 프레임 버퍼로 플러시되거나 버거(bugger) 토글 작업이 트리거됩니다.

이 서비스는 애플리케이션에서 gx_canvas_drawing_initiate()로 시작된 그리기 시퀀스를 닫으려는 경우에만 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **canvas** 캔버스 제어 블록에 대한 포인터
- **flush** **_GX_TRUE_** 이면 캔버스 변경 내용이 디스플레이로 플러시됩니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 그리기를 완료했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Complete drawing on “my_canvas” and flush to display. */
status = gx_canvas_drawing_complete(&my_canvas, GX_TRUE);

/* If status is GX_SUCCESS the canvas drawing was successfully completed. */
```


### <a name="see-also"></a>참고 항목

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_initiate,
- gx_canvas_offset_set
- gx_canvas_shift

## <a name="gx_canvas_drawing_initiate"></a>gx_canvas_drawing_initiate

캔버스 그리기 시작

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_drawing_initiate(
    GX_CANVAS *canvas,
    GX_WIDGET *who, 
    GX_RECTANGLE *dirty_area);
```

### <a name="description"></a>Description

이 서비스는 지정된 캔버스에 그리기를 시작합니다. 캔버스를 업데이트해야 할 때 GUIX에서 자동으로 수행하는 지연된 그리기 작업의 일부로 내부적으로 호출됩니다. 그러나 애플리케이션에서 gx_canvas_drawing_inititate, 원하는 그리기 함수, gx_canvas_drawing_complete()를 차례로 호출하면 GUIX의 지연된 그리기 알고리즘을 무시하고 즉시 캔버스에 직접 그릴 수 있습니다.

### <a name="parameters"></a>매개 변수

- **canvas** 캔버스 제어 블록에 대한 포인터
- **who** 호출자의 위젯 제어 블록에 대한 포인터입니다. 이 매개 변수는 후속 그리기 작업을 위해 그리기 클리핑 및 뷰 매개 변수를 초기화하는 데 사용됩니다.
- **dirty_area** 그릴 영역. 호출자는 이 매개 변수를 전달하여 호출자가 모든 그리기 작업을 클리핑하려는 영역을 표시합니다. 일반적으로 이전에 더티로 표시된 영역이지만, 호출자가 임의로 클리핑 영역을 확장하거나 축소할 수 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 그리기를 시작했습니다.
- **GX_DRAW_NESTING_EXCEEDED**(0x05) 최대 중첩 수를 초과했습니다.
- **GX_NO_VIEW**(0x03) 호출자의 뷰포트가 없습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CANVAS**(0x20) 캔버스가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Initiate drawing on “my_canvas”, my_widget.gx_widget_size
specify the area the application wants GUIX to redraw. */
status = gx_canvas_drawing_initiate(&my_canvas, &my_widget,
    &my_widget.gx_widget_size);

/* If status is GX_SUCCESS the canvas drawing was successfully initiated. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_complete,
- gx_canvas_offset_set
- gx_canvas_shift


## <a name="gx_canvas_ellipse_draw"></a>gx_canvas_ellipse_draw

타원 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_ellipse_draw(
    INT xcenter, 
    INT ycenter, 
    INT a, 
    dINT b);
```

### <a name="description"></a>Description

이 서비스는 현재 브러시를 사용하여 캔버스에 타원을 그립니다. 타원이 잘못된 캔버스 영역으로 잘립니다. 서비스를 사용하려면 GX_ARC_DRAWING_SUPPORT를 정의해야 합니다.

### <a name="parameters"></a>매개 변수

- **xcenter** 타원 중심의 x 좌표
- **ycenter** 타원 중심의 y 좌표
- **a** 긴 반지름의 길이
- **b** 짧은 반지름의 길이

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 원을 그렸습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 값이 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Draw an ellipse of semi-major radius 100, semi-minor radius 50
    and centered at (200, 200). */
status = gx_canvas_ellipse_draw(200, 200, 100, 50);

/* If status is GX_SUCCESS the ellipse has been drawn on
    “my_canvas”. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create,
- gx_canvas_line_darw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw

## <a name="gx_canvas_hardware_layer_bind"></a>gx_canvas_hardware_layer_bind

하드웨어 그래픽 계층에 캔버스 바인딩

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_hardware_layer_bind(
    GX_CANVAS *canvas, 
    INT layer);
```

### <a name="description"></a>Description

이 서비스는 GUIX 그리기 캔버스를 하드웨어 그래픽 계층에 바인딩합니다. 여러 하드웨어 그래픽 계층을 지원하는 하드웨어 디바이스에서만 필요합니다.

캔버스를 하드웨어 그래픽 계층에 바인딩하면 하드웨어 디스플레이 드라이버 서비스에서 gx_canvas_show(), gx_canvas_hide(), gx_canvas_alpha_set(), gx_canvas_offset_set() API를 직접 구현합니다.

하드웨어 디스플레이 드라이버가 여러 그래픽 계층을 지원하지 않는 경우에는 GX_INVALID_DISPLAY가 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **canvas** 하드웨어에서 구현할 캔버스
- **layer** 하드웨어 그래픽 계층

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 바인딩했습니다.
- **GX_INVALID_DISPLAY**(0x1D) 디스플레이 계층 서비스가 정의되어 있지 않습니다.
- **GX_PTR_ERROR**(0x17) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_CANVAS**(0x20) 캔버스가 잘못되었습니다.
- **GX_NOT_SUPPORTED**(0x28) 지원되지 않습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Binds the canvas to the hardware graphics layer 1. */
status = gx_canvas_hardware_layer_bind(&my_canvas, 1);

/* If status is GX_SUCCESS, the drawing canvas is bound to the
    hardware graphics. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_create,
- gx_canvas_memory_define

## <a name="gx_canvas_hide"></a>gx_canvas_hide

캔버스가 표시되지 않도록 숨기기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_hide(GX_CANVAS *canvas);
```

### <a name="description"></a>Description

이 서비스는 GUIX 캔버스를 숨깁니다. gx_canvas_hardware_layer_bind()를 사용하여 캔버스가 하드웨어 그래픽 계층에 바인딩된 경우 서비스는 하드웨어 지원을 사용하여 구현됩니다.

### <a name="parameters"></a>매개 변수

- **canvas** 숨길 캔버스

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 숨겼습니다.
- **GX_INVALID_CANVAS**(0x20) 캔버스가 잘못되었습니다.
- **GX_PTR_ERROR**(0x17) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Make my_canvas invisible. */
status = gx_canvas_hide(&my_canvas);

/* If status is GX_SUCCESS, the canvas has been hidden. */

```

### <a name="see-also"></a>참고 항목

- gx_canvas_create,
- gx_canvas_drawing_complete
- gx_canvas_drawing_initiate,
- gx_canvas_offset_set
- gx_canvas_shift,
- gx_canvas_hardware_layer_bind,
- gx_canvas_show
- gx_canvas_hide

## <a name="gx_canvas_line_draw"></a>gx_canvas_line_draw

선 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_line_draw(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_VALUE x_end, 
    GX_VALUE y_end);
```

### <a name="description"></a>Description

이 서비스는 현재 브러시를 사용하여 캔버스에 선을 그립니다. 선이 잘못된 캔버스 영역으로 잘립니다.

### <a name="parameters"></a>매개 변수

- **x_start** 선의 시작 x 위치
- **y_start** 선의 시작 y 위치
- **x_end** 선의 끝 x 위치
- **y_end** 선의 끝 y 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 선을 그렸습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.
- **GX_INVALID_WIDTH**(0x1E) 브러시 너비가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Draw line on canvas. */
status = gx_canvas_line_draw(0, 1, 320, 480);

/* If status is GX_SUCCESS, the line has been drawn to canvas. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_pie_draw
- gx_canvas_pixelmap_draw,
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_memory_define"></a>gx_canvas_memory_define

캔버스 메모리 정의

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_memory_define(
    GX_CANVAS *canvas, 
    GX_COLOR *memory,
    ULONG memsize);
```

### <a name="description"></a>Description

이 서비스는 사용하면 캔버스를 만든 후에 캔버스 메모리 주소를 할당할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **canvas** 이전에 만든 캔버스에 대한 포인터
- **memory** 캔버스 메모리 주소
- **memsize** 캔버스 메모리 블록의 크기(바이트)

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 할당했습니다.
- **GX_INVALID_CANVAS**(0x20) 제어 블록이 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Assign canvas memory block. */
status = gx_canvas_memory_define(canvas,
    (GX_COLOR *) DRAM_MEMORY,
    (640 * 480 * 2));

/* If status is GX_SUCCESS, the canvas memory pointer has be
reassigned. */

```

### <a name="see-also"></a>참고 항목

- gx_canvas_create,
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_mouse_define"></a>gx_canvas_mouse_define

마우스 커서 이미지 정의

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_mouse_define(GX_CANVAS *canvas,
    GX_MOUSE_CURSOR_INFO *info);
```

### <a name="description"></a>Description

이 서비스는 지정된 캔버스의 마우스 정보를 정의합니다. 서비스를 사용하려면 GX_MOUSE_SUPPORT를 정의해야 합니다.

### <a name="parameters"></a>매개 변수

- **canvas** 캔버스 제어 블록에 대한 포인터
- **info** 마우스 커서 정보에 대한 포인터입니다. **부록 I** 에는 GX_MOUSE_CURSOR_INFO 구조체의 정의가 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 마우스 정보를 설정했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set mouse cursor info. */
GX_MOUSE_CURSOR_INFO mouse_cursor;
mouse_cursor.gx_mouse_cursor_image_id = GX_PIXELMAP_ID_MOUSE;
mouse_cursor.gx_mouse_cursor_hotspot_x = 0;
mouse_cursor.gx_mouse_cursor_hotspot_y = 0;

status = gx_canvas_mouse_define(&my_canvas, &mouse_cursor);

/* If status is GX_SUCCESS the mouse info of “my_canvas” has been
set successfully. */

```

### <a name="see-also"></a>참고 항목

- gx_canvas_mouse_show,
- gx_canvas_mouse_hide

## <a name="gx_canvas_mouse_hide"></a>gx_canvas_mouse_hide


마우스 커서 끄기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_mouse_hide(GX_CANVAS *canvas);
```

### <a name="description"></a>Description

이 서비스는 지정된 캔버스에서 마우스 커서를 숨깁니다. 서비스를 사용하려면 GX_MOUSE_SUPPORT를 정의해야 합니다.

### <a name="parameters"></a>매개 변수

- **canvas** 캔버스 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 마우스 커서를 숨겼습니다.
- **GX_FAILURE**(0x10) 마우스 커서를 숨기지 못했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.


### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Hide the mouse cursor. */
status = gx_canvas_mouse_hide(&my_canvas);

/* If status is GX_SUCCESS the mouse cursor of “my_canvas” has been
hidden successfully. */

```

### <a name="see-also"></a>참고 항목

- gx_canvas_mouse_show,
- gx_canvas_mouse_define

## <a name="gx_canvas_mouse_show"></a>gx_canvas_mouse_show


마우스 커서 켜기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_mouse_show(GX_CANVAS *canvas);
```

### <a name="description"></a>Description

이 서비스는 지정된 캔버스에 마우스 커서를 표시합니다. 서비스를 사용하려면 GX_MOUSE_SUPPORT를 정의해야 합니다. 서비스를 요청하기 전에 gx_canvas_mouse_define API를 호출하여 마우스 커서 이미지를 정의해야 합니다.

### <a name="parameters"></a>매개 변수

- **canvas** 캔버스 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 마우스 정보를 설정했습니다.
- **GX_FAILURE**(0x10) 마우스 커서를 표시하지 못했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Make mouse cursor hidden ”. */
status = gx_canvas_mouse_show(&my_canvas);

/* If status is GX_SUCCESS the mouse of “my_canvas” has been
hidden successfully. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_mouse_show,
- gx_canvas_mouse_define

## <a name="gx_canvas_offset_set"></a>gx_canvas_offset_set


캔버스 x,y 표시 오프셋 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_offset_set(
    GX_CANVAS *canvas,
    GX_VALUE x, 
    GX_VALUE y);
```

### <a name="description"></a>Description

이 서비스는 지정된 캔버스의 x,y 표시 오프셋을 할당합니다. 캔버스가 표시되는 프레임 버퍼에 합성되는 위치를 제어하며, 캔버스가 물리적 디스플레이보다 작은 경우에 자주 사용됩니다.

gx_canvas_hardware_layer_bind() API를 사용하여 캔버스가 하드웨어 그래픽 계층에 바인딩된 경우 gx_canvas_offset_set 서비스는 하드웨어 지원을 사용하여 직접 구현됩니다.

### <a name="parameters"></a>매개 변수

- **canvas** 캔버스 제어 블록에 대한 포인터
- **x** 오프셋의 X 좌표
- **y** 오프셋의 Y 좌표

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 오프셋을 할당했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CANVAS**(0x20) 캔버스가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set display offset for “my_canvas”. */
status = gx_canvas_offset_set(&my_canvas, 20, 30);

/* If status is GX_SUCCESS the canvas drawing is now offset from
position 20,30. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_complete,
- gx_canvas_initiate,
- gx_canvas_shift
- gx_canvas_show,
- gx_canvas_hide,
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_pie_draw"></a>gx_canvas_pie_draw


원형 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_pie_draw(
    INT xcenter, 
    INT ycenter,
    UINT r, 
    INT start_angle, 
    INT end_angle);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트 브러시를 사용하여 캔버스에 원형을 그립니다. 원형이 잘못된 캔버스 영역으로 잘립니다. 서비스를 사용하려면 구성 옵션 GX_ARC_DRAWING_SUPPORT를 정의해야 합니다.

### <a name="parameters"></a>매개 변수

- **xcenter** 원형 중심의 x 위치
- **ycenter** 원형 중심의 y 위치
- **r** 원형의 반지름
- **start_angle** 원형의 시작 각도
- **end_angle** 원형의 끝 각도

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 원호를 그렸습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 값이 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Draw a pie from 0 degree to 90 degree in clockwise. */
status = gx_canvas_pie_draw(100, 100, 50, 0, 90);

/* If status is GX_SUCCESS the pie has been drawn to canvas. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pixelmap_draw,
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_pixel_draw"></a>gx_canvas_pixel_draw


픽셀 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_pixel_draw(GX_POINT position);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트 브러시의 선 색을 사용하여 캔버스에 픽셀을 그립니다. 구성 옵션 GX_BRUSH_ALPHA_SUPPORT가 정의된 경우 알파와 픽셀을 혼합하고, 그러지 않으면 픽셀을 완전 불투명으로 그립니다.

- **point** 그릴 픽셀의 x,y 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap을 그렸습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_POINT point; /* the x,y position you want to draw to */
GX_RECTANGLE drawto; /* the rectangle bounding your drawing */
GX_CANVAS *mycanvas; /* the canvas you want to draw to */

/* calculate 1x1 pixel drawing area: */
gx_utility_rectangle_define(&drawto,
    point.gx_point_x, point.gx_point_y,
    point.gx_point_x, point.gx_point_y);

/* get my canvas: */
gx_widget_canvas_get(win, &mycanvas);

/* open my canvas for drawing: */
gx_canvas_drawing_initiate(mycanvas, win, &drawto);

/* setup my brush colors. Use any color ID in your resources: */
gx_context_line_color_set(GX_COLOR_ID_WINDOW_BORDER);

/* draw a pixel: */
status = gx_canvas_pixel_draw(point);

/* close the canvas: */
gx_canvas_drawing_complete(mycanvas, GX_TRUE);

/* If status is GX_SUCCESS, the pixel was successfully drawn to mycanvas. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_block_move,
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_blend"></a>gx_canvas_pixelmap_blend

pixelmap 혼합

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_pixelmap_blend(
    GX_VALUE x_position,
    GX_VALUE y_position, 
    GX_PIXELMAP *pixelmap, 
    GX_UBYTE alpha);
```

### <a name="description"></a>Description

이 서비스는 캔버스 배경과 pixelmap을 혼합합니다. 혼합 비율은 호출자가 지정합니다. 알파 값은 0(완전 투명)에서 255(완전 불투명) 사이일 수 있습니다. pixelmap에는 들어오는 혼합 값과 결합하는 내부 알파 채널이 포함될 수도 있습니다. 16bpp 이상의 색 농도에서 실행되는 디스플레이 드라이버만 서비스를 지원합니다.

### <a name="parameters"></a>매개 변수

- **x_start** pixelmap의 시작 x 위치
- **y_start** pixelmap의 시작 y 위치
- **pixelmap** pixelmap에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap을 그렸습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_NOT_SUPPORTED**(0x28) 지원되지 않습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Draw pixelmap on active canvas */

GX_PIXELMAP *map;
gx_system_pixelmap_get(ID_MY_PIXELMAP, &map);

status = gx_canvas_pixelmap_blend(10, 20, map, 128);

/* If status is GX_SUCCESS the pixelmap has been blended onto the current canvas. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_pixelmap_draw"></a>gx_canvas_pixelmap_draw

pixelmap 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_pixelmap_draw(
    GX_VALUE x_position, 
    GX_VALUE y_position,
    GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Description

이 서비스는 캔버스에 pixelmap을 그립니다.

### <a name="parameters"></a>매개 변수

- **x_start** pixelmap의 시작 x 위치
- **y_start** pixelmap의 시작 y 위치
- **pixelmap** pixelmap에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap을 그렸습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Draw pixelmap on canvas. */
status = gx_canvas_pixelmap_draw(10, 20, &my_pixelmap);

/* If status is GX_SUCCESS the pixelmap “my_pixelmap” has been drawn. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_get"></a>gx_canvas_pixelmap_get

캔버스 pixelmap 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_pixelmap_get(GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Description

이 서비스는 캔버스 데이터를 가리키는 GX_PIXELMAP 구조체를 반환합니다. pixelmap 형식은 현재 디스플레이 색 형식으로 설정됩니다.

### <a name="parameters"></a>매개 변수

- **pixelmap** 반환된 pixelmap

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap을 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Draw pixelmap on active canvas */

GX_PIXELMAP *map;

status = gx_canvas_pixelmap_get(map);

/* If status is GX_SUCCESS the pixelmap has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_pixelmap_blend,
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_pixelmap_rotate"></a>gx_canvas_pixelmap_rotate


회전된 pixelmap 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_pixelmap_rotate(
    GX_VALUE x_position, 
    GX_VALUE y_position,
    GX_PIXELMAP *pixelmap, 
    INT angle,
    INT rot_cx, 
    INT rot_cy);
```

### <a name="description"></a>Description

이 서비스는 지정된 각도로 pixelmap을 회전하고 회전 시 캔버스에 pixelmap을 직접 렌더링합니다. 회전 출력이 캔버스 메모리에 직접 렌더링되고 회전된 pixelmap이 호출자에게 반환되지 않는다는 점에서 gx_utility_pixelmap_rotate와는 다릅니다.

gx_utility_pixelmap_rotate 대비 회전된 pixelmap을 저장할 추가 메모리가 필요하지 않다는 장점이 있습니다. 단점은 pixelmap을 그릴 때마다 회전 코드를 실행해야 한다는 것입니다.

클리핑 및 뷰포트 유효성 검사는 회전된 pixelmap을 렌더링하는 동안 적용됩니다.

### <a name="parameters"></a>매개 변수

- **x_position** pixelmap의 시작 x 위치
- **y_position** pixelmap의 시작 y 위치
- **pixelmap** pixelmap에 대한 포인터
- **angle** 회전할 각도
- **rot_cx** 회전 중심의 X 좌표. 이 값을 -1로 설정하면 이미지 중심이 회전 중심으로 사용됩니다.
- **rot_cy** 회전 중심의 Y 좌표. 이 값을 -1로 설정하면 이미지 중심이 회전 중심으로 사용됩니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap을 그렸습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* rotate “src_pixelmap” by 30 degree in clockwise direction and draw in on canvas. */
status = gx_canvas_pixelmap_rotate(10, 20, &my_pixelmap, 30,
    -1, -1);

/* If status is GX_SUCCESS the rotated pixelmap “my_pixelmap” has been drawn. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile,
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_tile"></a>gx_canvas_pixelmap_tile

바둑판식으로 pixelmap 배열

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_pixelmap_tile(
    GX_RECTANGLE *fill,
    GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Description

이 서비스는 요청된 pixelmap을 사용하여 캔버스 내의 사각형을 채웁니다.

### <a name="parameters"></a>매개 변수

- **fill** pixelmap을 바둑판식으로 배열할 영역
- **pixelmap** pixelmap에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap을 바둑판식으로 배열했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.
- **GX_INVALID_VALUE**(0x22) 채우기 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Tile pixelmap on canvas */
status = gx_canvas_pixelmap_tile(&tile_area, &my_pixelmap);

/* If status is GX_SUCCESS the pixelmap “my_pixelmap” has been tiled on canvas */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_blend,
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_polygon_draw"></a>gx_canvas_polygon_draw


다각형 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_polygon_draw(
    GX_POINT *point_array,
    INT number_of_points);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트 브러시를 사용하여 캔버스에 다각형을 그립니다.

### <a name="parameters"></a>매개 변수

- **point_array** 다각형의 점 배열
- **number_of_points** 다각형의 점 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 다각형을 그렸습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_POINT my_polygon[4] =
{
    { 208, 63 },
    { 274, 63 },
    { 274, 163 },
    { 208, 163 }
};

/* Draw polygon “my_polygon” on canvas. */
status = gx_canvas_polygon_draw(&my_polygon, 4);

/* If status is GX_SUCCESS the polygon “my_polygon” has been drawn. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_rectangle_draw"></a>gx_canvas_rectangle_draw


사각형 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_rectangle_draw(GX_RECTANGLE *rectangle);
```

### <a name="description"></a>Description

이 서비스는 캔버스에 사각형을 그립니다.

### <a name="parameters"></a>매개 변수

- **rectangle** 그릴 사각형

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 사각형을 그렸습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Draw rectangle “my_rectangle” on canvas. */
status = gx_canvas_rectangle_draw(&my_rectangle);

/* If status is GX_SUCCESS the rectangle “my_rectangle” has been drawn. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_text_draw

## <a name="gx_canvas_rotated_text_draw"></a>gx_canvas_rotated_text_draw


중심점을 기준으로 회전된 텍스트 그리기(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_rotated_text_draw(
    const GX_CHAR *text,
    GX_VALUE xCenter, 
    GX_VALUE yCenter, 
    INT angle);
```

### <a name="description"></a>Description

이 API는 사용되지 않으며 gx_canvas_rotated_text_draw_ext()로 대체되었습니다. 여전히 지원되지만 새 애플리케이션에서는 이 API 대신 gx_canvas_rotated_text_draw_ext()를 사용해야 합니다.

이 서비스는 캔버스에 텍스트를 그립니다. 요청된 중심점을 기준으로 회전된 텍스트가 그려집니다. 현재 그리기 컨텍스트 글꼴 및 그리기 컨텍스트 선 색이 텍스트를 렌더링하는 데 사용됩니다.

서비스는 gx_utility_string_to_alphamap 함수를 사용하여 알파 값만 포함된 임시 8bpp pixelmap에 텍스트 문자열을 렌더링합니다. 그런 다음 gx_utility_pixelmap_rotate 함수를 사용하여 alphamap을 회전합니다. 최종 alphamap이 캔버스에 렌더링된 후에는 임시 alphamap 및 관련 메모리가 해제됩니다.

회전된 텍스트를 렌더링하는 데 임시 alphamap이 필요하므로 애플리케이션에서 회전된 텍스트를 그리기 전에 gx_system_memory_allocator_set() API를 호출하여 gx_system_memory_allocator를 구성해야 합니다.

이 서비스는 회전된 텍스트를 “일회성”으로 렌더링하는 데에만 사용해야 합니다. 동일한 텍스트 문자열을 다른 위치에 또는 다른 회전 각도로 여러 번 그리는 경우 유틸리티 함수 gx_utility_string_to_alphamap()을 사용하여 텍스트 alphamap을 한 번 만든 다음, gx_utility_pixelmap_rotate를 여러 번 사용하여 결과 alphamap을 반복해서 회전하는 것이 더 효율적입니다.

### <a name="parameters"></a>매개 변수

- **text** 그릴 텍스트 문자열
- **xCenter** 텍스트를 회전할 중심 위치
- **yCenter** 텍스트를 회전할 중심 위치
- **angle** 원하는 텍스트 회전 각도(도)

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트를 렌더링했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**(0x30) 사용 가능한 메모리가 부족하거나 gx_system_memory_allocator가 할당되지 않았습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
void my_window_draw(GX_WINDOW *window)
{

    GX_VALUE xpos = 100;
    GX_VALUE ypos = 100;
    INT dynamic_count = 1234567;
    GX_CHAR dynamic_text[10];

    /* Call default window draw routine. */
    gx_window_draw(window);

    /* Set font. */
    gx_context_font_set(GX_FONT_ID_SMALL_BOLD);

    /* Convert int value to string. */
    gx_utility_ltoa(dynamic_count, dynamic_text, 20);

    /* Draw rotate text. */
    gx_canvas_rotated_text_draw(dynamic_text, xpos, ypos, 45);
}
```

### <a name="see-also"></a>참고 항목

- gx_canvas_alpha_set,
- gx_canvas_drawing_complete
- gx_canvas_create,
- gx_canvas_drawing_initiate
- gx_canvas_offset_set,
- gx_canvas_shift

## <a name="gx_canvas_rotated_text_draw_ext"></a>gx_canvas_rotated_text_draw_ext


중심점을 기준으로 회전된 텍스트 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_rotated_text_draw_ext(
    GX_CONST GX_STRING *text,
    GX_VALUE xCenter, 
    GX_VALUE yCenter, 
    INT angle);
```

### <a name="description"></a>Description

이 서비스는 캔버스에 텍스트를 그립니다. 요청된 중심점을 기준으로 회전된 텍스트가 그려집니다. 현재 그리기 컨텍스트 글꼴 및 그리기 컨텍스트 선 색이 텍스트를 렌더링하는 데 사용됩니다.

서비스는 gx_utility_string_to_alphamap 함수를 사용하여 알파 값만 포함된 임시 8bpp pixelmap에 텍스트 문자열을 렌더링합니다. 그런 다음 gx_utility_pixelmap_rotate 함수를 사용하여 alphamap을 회전합니다. 최종 alphamap이 캔버스에 렌더링된 후에는 임시 alphamap 및 관련 메모리가 해제됩니다.

회전된 텍스트를 렌더링하는 데 임시 alphamap이 필요하므로 애플리케이션에서 회전된 텍스트를 그리기 전에 ***gx_system_memory_allocator_set()*** API를 호출하여 gx_system_memory_allocator를 구성해야 합니다.

이 서비스는 회전된 텍스트를 “일회성”으로 렌더링하는 데에만 사용해야 합니다. 동일한 텍스트 문자열을 다른 위치에 또는 다른 회전 각도로 여러 번 그리는 경우 유틸리티 함수 gx_utility_string_to_alphamap()을 사용하여 텍스트 alphamap을 한 번 만든 다음, gx_utility_pixelmap_rotate를 여러 번 사용하여 결과 alphamap을 반복해서 회전하는 것이 더 효율적입니다.

### <a name="parameters"></a>매개 변수

- **text** 그릴 텍스트 문자열
- **xCenter** 텍스트를 회전할 중심 위치
- **yCenter** 텍스트를 회전할 중심 위치
- **angle** 원하는 텍스트 회전 각도(도)

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트를 렌더링했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 그리기 컨텍스트가 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**(0x30) 사용 가능한 메모리가 부족하거나 gx_system_memory_allocator가 할당되지 않았습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
void my_window_draw(GX_WINDOW *window)
{

    GX_VALUE xpos = 100;
    GX_VALUE ypos = 100;
    INT dynamic_count = 1234567;
    GX_CHAR dynamic_text[10];
    GX_STRING string;

    /* Call default window draw routine. */
    gx_window_draw(window);

    /* Set font. */
    gx_context_font_set(GX_FONT_ID_SMALL_BOLD);

    /* Convert int value to string. */
    gx_utility_ltoa(dynamic_count, dynamic_text, 20);

    string.gx_string_ptr = dynamic_text;
    string.gx_string_length = strlen(dynamic_text);

    /* Draw rotate text. */
    gx_canvas_rotated_text_draw_ext(&string, xpos, ypos, 45);
}
```

### <a name="see-also"></a>참고 항목

- gx_canvas_alpha_set,
- gx_canvas_drawing_complete
- gx_canvas_create,
- gx_canvas_drawing_initiate
- gx_canvas_offset_set,
- gx_canvas_shift

## <a name="gx_canvas_shift"></a>gx_canvas_shift


x,y만큼 캔버스 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_shift(
    GX_CANVAS *canvas, 
    GX_VALUE x, GX_VALUE y);
```

### <a name="description"></a>Description

이 서비스는 지정된 캔버스 오프셋을 지정된 양만큼 이동합니다. 표시되는 프레임 버퍼 내에서 캔버스가 렌더링되는 위치에 영향을 줍니다.

### <a name="parameters"></a>매개 변수

- **canvas** 캔버스 제어 블록에 대한 포인터
- **x** X축에서 이동할 픽셀
- **y** Y축에서 이동할 픽셀

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 캔버스를 이동했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CANVAS**(0x20) 캔버스가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Shift canvas “my_canvas”. */
status = gx_canvas_shift(&my_canvas, 10, 15);

/* If status is GX_SUCCESS the canvas has been shifted by 10 pixels
    on the X axis and 15 on the Y axis. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_drawing_complete,
- gx_canvas_initiate
- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_offset_set

## <a name="gx_canvas_show"></a>gx_canvas_show


캔버스 표시

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_show(GX_CANVAS *canvas);
```

### <a name="description"></a>Description

이 서비스는 캔버스를 표시합니다. gx_canvas_hardware_layer_bind() API를 사용하여 캔버스가 이전에 하드웨어 그래픽 계층에 바인딩된 경우 gx_canvas_show() 서비스는 하드웨어 지원을 사용하여 직접 구현됩니다.

### <a name="parameters"></a>매개 변수

- **canvas** 캔버스 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 오프셋을 할당했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CANVAS**(0x20) 캔버스가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Make this canvas visible. */
status = gx_canvas_show(&my_canvas);

/* If status is GX_SUCCESS the canvas drawing is now visible */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_complete,
- gx_canvas_initiate,
- gx_canvas_shift,
- gx_canvas_hide,
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_text_draw"></a>gx_canvas_text_draw

텍스트 그리기(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_text_draw(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_CONST GX_CHAR *string, 
    INT length);
```

### <a name="description"></a>Description

이 서비스는 캔버스에 텍스트를 그립니다. 여전히 지원되지만 사용되지 않는 API이므로 새 애플리케이션에서는 gx_canvas_text_draw_ext()를 대신 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **x_start** 텍스트의 시작 x 좌표
- **y_start** 텍스트의 시작 y 좌표
- **string** 그릴 문자열에 대한 포인터
- **length** length가 0보다 크거나 같으면 그려지는 문자 수를 length로 제한합니다. length가 0보다 작으면 NULL 종결자 앞의 전체 문자열이 그려집니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트를 그렸습니다.
- **GX_FAILURE**(0x1E) 텍스트를 그리지 못했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Draw text “example” on current canvas”. */
status = gx_canvas_text_draw(10, 20, “example”, 7);

/* Draw all of a string of unknown length on the current canvas */
status = gx_canvas_text_draw(10, 40, string_ptr, -1);

/* If status is GX_SUCCESS the text “example” has been drawn. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw

## <a name="gx_canvas_text_draw_ext"></a>gx_canvas_text_draw_ext


텍스트 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_canvas_text_draw_ext(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Description

이 서비스는 캔버스에 텍스트를 그립니다.

### <a name="parameters"></a>매개 변수

- **x_start** 텍스트의 시작 x 좌표
- **y_start** 텍스트의 시작 y 좌표
- **string** 그릴 문자열에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트를 그렸습니다.
- **GX_FAILURE**(0x1E) 텍스트를 그리지 못했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 열린 그리기 컨텍스트가 없습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.
- **GX_INVALID_FONT**(0x16) 글꼴이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING string;
string.gx_string_ptr = “example”;
string.gx_string_length = 7;

/* Draw text “example” on current canvas”. */
status = gx_canvas_text_draw_ext(10, 20, &string);

/* If status is GX_SUCCESS the text “example” has been drawn. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw

## <a name="gx_checkbox_create"></a>gx_checkbox_create


확인란 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_checkbox_create(
    GX_CHECKBOX *checkbox, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT checkbox_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 지정된 속성을 사용하여 확인란 위젯을 만듭니다. GX_CHECKBOX는 GX_TEXT_BUTTON에서 파생되며 GX_CHECKBOX 위젯에서 gx_text_button 서비스를 모두 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **checkbox** 확인란 제어 블록에 대한 포인터 name 확인란 위젯의 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **text_id** 확인란 텍스트의 리소스 ID
- **style** 확인란의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **checkbox_id** 애플리케이션에서 정의된 확인란 ID
- **size** 확인란의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 확인란을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create “my_checkbox”. */
status = gx_checkbox_create(&my_checkbox, “my_checkbox”,
    &my_parent,
    MY_CHECKBOX_TEXT_RESOURCE_ID, GX_STYLE_BORDER_RAISED,
    MY_CHECKBOX_ID,
    &size);

/* If status is GX_SUCCESS the checkbox “my_checkbox” has been created. */
```
### <a name="see-also"></a>참고 항목

- gx_checkbox_draw,
- gx_checkbox_event_process,
- gx_checkbox_select

## <a name="gx_checkbox_draw"></a>gx_checkbox_draw

확인란 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_checkbox_draw(GX_CHECKBOX *checkbox);
```

### <a name="description"></a>Description

이 서비스는 지정된 확인란을 그립니다. 일반적으로 GUIX 캔버스 새로 고침 메커니즘을 통해 내부적으로 호출되지만 사용자 지정 확인란 위젯용 사용자 지정 그리기 함수를 구현하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **checkbox** 확인란 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom checkbox draw function. */
VOID custom_checkbox_draw(GX_CHECKBOX *checkbox)
{
    /* Call default checkbox draw. */
    gx_checkbox_draw(checkbox);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_checkbox_create,
- gx_checkbox_event_process,
- gx_checkbox_select

## <a name="gx_checkbox_event_process"></a>gx_checkbox_event_process


확인란 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_checkbox_event_process(
    GX_CHECKBOX *checkbox, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 확인란에 대한 이벤트를 처리합니다. 사용자 지정 확인란 이벤트 처리 함수에서 기본 이벤트 처리기로 호출되어야 합니다.

### <a name="parameters"></a>매개 변수

- **checkbox** 확인란 제어 블록에 대한 포인터
- **event_ptr** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 확인란 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic checkbox event processing as part of custom event processing function. */

UINT custom_checkbox_event_process(GX_CHECKBOX *checkbox,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default checkbox
            event processing */
        status = gx_checkbox_event_process(checkbox, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_checkbox_create,
- gx_checkbox_draw,
- gx_checkbox_select

## <a name="gx_checkbox_pixelmap_set"></a>gx_checkbox_pixelmap_set


확인란의 pixelmap 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_checkbox_pixelmap_set(
    GX_CHECKBOX *checkbox,
    GX_RESOURCE_ID unchecked_id, 
    GX_RESOURCE_ID checked_id,
    GX_RESOURCE_ID unchecked_disabled_id, 
    GX_RESOURCE_ID checked_disabled_id);
```

### <a name="description"></a>Description

이 서비스는 지정된 확인란에서 각 확인란 상태에 대해 표시할 pixelmap을 할당합니다. 리소스 ID는 중복될 수 있습니다.

### <a name="parameters"></a>매개 변수

- **checkbox** 확인란 제어 블록에 대한 포인터
- **unchecked_id** 선택 취소된 상태에 사용되는 pixelmap
- **checked_id** 선택된 상태에 사용되는 pixelmap
- **unchecked_disabled_id** 사용할 수 없고 선택 취소된 확인란에 사용되는 pixelmap
- **checked_disabled_id** 사용할 수 없고 선택된 확인란에 사용되는 pixelmap

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 확인란을 선택했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Select “my_checkbox”. */
status = gx_checkbox_pixelmap_set(&my_checkbox,
    PIXELMAP_UNCHECKED_ID,
    PIXELMAP_CHECKED_ID, PIXELMAP_UNCHECKED_DISABLED_ID,
    PIXELMAP_CHECKED_SIABLED_ID));

/* If status is GX_SUCCESS the pixelmaps are assigned to the checkbox “my_checkbox” */
```

### <a name="see-also"></a>참고 항목

- gx_checkbox_create,
- gx_checkbox_draw,
- gx_checkbox_event_process

## <a name="gx_checkbox_select"></a>gx_checkbox_select


확인란 선택

### <a name="prototype"></a>프로토타입

```C
UINT gx_checkbox_select(GX_CHECKBOX *checkbox);
```

### <a name="description"></a>Description

이 서비스는 확인란을 선택된 상태로 강제 적용합니다.

### <a name="parameters"></a>매개 변수

- **checkbox** 확인란 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 확인란을 선택했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Select “my_checkbox”. */
status = gx_checkbox_select(&my_checkbox);

/* If status is GX_SUCCESS the checkbox “my_checkbox” has been toggled. */
```

### <a name="see-also"></a>참고 항목

- gx_checkbox_create,
- gx_checkbox_draw,
- gx_checkbox_event_process

## <a name="gx_circular_gauge_angle_get"></a>gx_circular_gauge_angle_get


현재 각도 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_circular_gauge_angle_get(
    GX_CIRCULAR_GAUGE *gauge, 
    INT *angle);
```

### <a name="description"></a>Description

이 서비스는 원형 계기 위젯의 현재 바늘 각도를 검색합니다.

### <a name="parameters"></a>매개 변수

- **gauge** 원형 계기 제어 블록에 대한 포인터
- **angle** 검색할 현재 바늘 각도

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 원형 계기 각도를 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
INT current_angle;

/* Retrieve the current needle angle of “my_gauge”. */
status = gx_circular_gauge_angle_get(&my_gauge, &current_angle);

/* If status is GX_SUCCESS the current needle angle of “my_gauge” has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_circular_gauge_angle_set,
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_angle_set"></a>gx_circular_gauge_angle_set


대상 각도 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_circular_gauge_angle_set(
    GX_CIRCULAR_GAUGE *gauge,
    INT angle);
```

### <a name="description"></a>Description

이 서비스는 원형 계기 위젯의 대상 각도를 설정합니다.

### <a name="parameters"></a>매개 변수

- **gauge** 원형 계기 제어 블록에 대한 포인터
- **angle** 대상 바늘 각도

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 각도를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set target angle of “my_gauge” to 180. */
status = gx_circular_gauge_angle_set(&my_gauge, 180);

/* If status is GX_SUCCESS the circular gauge of “my_gauge” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_circular_gauge_angle_get,
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_animation_set"></a>gx_circular_gauge_animation_set


애니메이션 매개 변수 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_circular_gauge_animation_set(
    GX_CIRCULAR_GAUGE *gauge,
    INT steps, 
    INT delay);
```

### <a name="description"></a>Description

이 서비스는 원형 계기 위젯의 애니메이션 단계와 지연 시간을 설정합니다.

### <a name="parameters"></a>매개 변수

- **gauge** 원형 계기 제어 블록에 대한 포인터
- **steps** 한 회전의 총 단계
- **delay** 모든 단계의 지연 시간

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 확인란을 선택했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set animation steps and delay time of circular gauge “my_gauge”
    to 30 and 1, the needle of “my_gauge” will rotate from
    current angle to target angle by 30 steps with 1 tick delay between every step. */
status = gx_circular_gauge_animation_set(&my_gauge, 30, 1);

/* If status is GX_SUCCESS the steps and delay time of “my_gauge” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_background_draw"></a>gx_circular_gauge_background_draw


원형 계기 배경 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_circular_gauge_background_draw(GX_CIRCULAR_GAUGE *gauge);
```

### <a name="description"></a>Description

이 서비스는 지정된 원형 계기의 배경을 그립니다. 일반적으로 gx_circular_gauge_draw 함수에서 내부적으로 호출되지만 사용자 지정 그리기 함수를 작성하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **gauge** 원형 계기 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Draw circular gauge background. */
gx_circular_gauge_background_draw(&my_circular_gauge);
```

### <a name="see-also"></a>참고 항목

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_create"></a>gx_circular_gauge_create


원형 계기 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_circular_gauge_create(
    GX_CIRCULAR_GAUGE *gauge,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_CIRCULAR_GAUGE_INFO *info,
    GX_RESOURCE_ID background_id,
    ULONG style,
    USHORT circular_gauge_id,
    GX_VALUE xpos,
    GX_VALUE ypos);
```

### <a name="description"></a>Description

이 서비스는 지정된 속성을 사용하여 원형 계기 위젯을 만듭니다.

### <a name="parameters"></a>매개 변수

- **gauge** 원형 계기 제어 블록에 대한 포인터
- **name** 원형 계기 위젯의 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **info** 계기 정보 구조체에 대한 포인터입니다. **부록 I** 에는 GX_CIRCULAR_GAUGE_INFO 구조체의 정의가 나와 있습니다.
- **background_id** 원형 계기 배경 pixelmap의 리소스 ID
- **style** 원형 계기의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **circular_gauge_id** 애플리케이션에서 정의된 원형 계기 ID
- **xpos** 계기 x 좌표 위치
- **ypos** 계기 y 좌표 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 확인란을 선택했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_SIZE**(0x19) 제어 블록 크기가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CIRCULAR_GAUGE gauge_info;

gauge_info.gx_circular_gauge_info_animation_steps = 30;
gauge_info.gx_circular_gauge_info_animation_delay = 1;
gauge_info.gx_circular_gauge_info_needle_xpos = 140;
gauge_info.gx_circular_gauge_info_needle_ypos = 140;
gauge_info.gx_circular_gauge_info_neelde_xcor = 20;
gauge_info.gx_circular_gauge_info_neelde_ycor = 88;
gauge_info.gx_circular_gauge_info_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Create “my_gauge”. */
status = gx_circular_gauge_create(&my_gauge, “my_gauge”,
            &my_parent,
            &gauge_info, MY_PIXELMAP_RESOURCE_ID, GX_NULL,
            MY_ICON_ID, 5, 30);

/* If status is GX_SUCCESS the circular gauge “my_gauge” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_draw
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_draw"></a>gx_circular_gauge_draw

원형 계기 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_circular_gauge_draw(GX_CIRCULAR_GAUGE *gauge);
```

### <a name="description"></a>Description

이 서비스는 지정된 원형 계기를 그립니다. 일반적으로 GUIX 캔버스 새로 고침 메커니즘을 통해 내부적으로 호출되지만 사용자 지정 계기 위젯용 사용자 지정 그리기 함수를 구현하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **gauge** 원형 계기 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom circular gauge draw function. */
VOID custom_gauge_draw(GX_CIRCULAR_GAUGE *gauge)
{
    /* Call default circular gauge draw. */
    gx_circular_gauge_draw(gauge);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw
- gx_circular_gauge_create,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_event_process"></a>gx_circular_gauge_event_process


원형 계기 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_circular_gauge_event_process(
    GX_CIRCULAR_GAUGE *gauge,
    GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 지정된 원형 계기에 대한 이벤트를 처리합니다.

### <a name="parameters"></a>매개 변수

- **gauge** 계기 제어 블록에 대한 포인터
- **event_ptr** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 계기 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic circular gauge event processing as part of custom event processing function. */
UINT custom_gauge_event_process(GX_CIRCULAR_GAUGE *gauge,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default circular gauge
             event processing */
        status = gx_circular_gauge_event_process(gauge, event);
        break;
}
return status;
```

### <a name="see-also"></a>참고 항목

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw

## <a name="gx_context_brush_default"></a>gx_context_brush_default


현재 그리기 컨텍스트의 브러시 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_brush_default(GX_DRAW_CONTEXT *context);
```

### <a name="description"></a>Description

이 서비스는 지정된 그리기 컨텍스트의 브러시를 기본값으로 설정합니다.

### <a name="parameters"></a>매개 변수

- **context** 컨텍스트 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 만들었습니다.
- **GX_PTR_ERROR**(0x07) 컨텍스트 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the brush of “my_context” to default. */
status = gx_context_brush_default(&my_context);

/* If status is GX_SUCCESS the brush of “my_context” has been set to default. */

```

### <a name="see-also"></a>참고 항목

- gx_context_brush_define,
- gx_context_brush_get
- gx_context_brush_set,
- gx_context_brush_style_set
- gx_context_brush_pattern_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_define"></a>gx_context_brush_define


현재 그리기 컨텍스트의 브러시 정의

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_brush_define(
    GX_RESOURCE_ID line_color_id,
    GX_RESOURCE_ID fill_color_id, 
    UINT style);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트의 브러시를 정의합니다.

### <a name="parameters"></a>매개 변수

- **line_color_id** 선 색의 리소스 ID. **부록 B** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **fill_color_id** 채우기 색의 리소스 ID. **부록 B** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **style** 브러시의 스타일. **부록 D** 에서는 지원되는 브러시 스타일에 대해 설명합니다. 비트 OR 연산을 사용하여 브러시 스타일을 하나의 변수로 결합할 수 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 브러시를 정의했습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트 정의가 없습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Define the brush of the current context. */
status = gx_context_brush_define(GX_COLOR_BLACK_ID,
    GX_COLOR_BLACK_ID,
    GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the brush of the current context has been defined. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default,
- gx_context_brush_get
- gx_context_brush_set,
- gx_context_brush_pattern_set
- gx_context_brush_style_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_get"></a>gx_context_brush_get


현재 그리기 컨텍스트의 브러시 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_brush_get(GX_BRUSH **return_brush);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트의 활성 브러시에 대한 포인터를 반환합니다. 활성 그리기 컨텍스트가 없으면 서비스 오류가 발생하고 NULL 포인터가 반환됩니다.

### <a name="parameters"></a>매개 변수

- **return_brush** 브러시 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 브러시를 검색했습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_BRUSH *my_brush;

/* Get the brush of the current context. */
status = gx_context_brush_get(&my_brush);

/* If status is GX_SUCCESS the brush of the current context has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_set,
- gx_context_brush_style_set
- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_pattern_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_pattern_set"></a>gx_context_brush_pattern_set


현재 그리기 컨텍스트의 브러시 패턴 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_brush_pattern_set(ULONG pattern);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트의 브러시 패턴을 설정합니다.

브러시 패턴은 파선 가로선과 파선 세로선을 그리는 데 사용됩니다. Gx_canvas_line_draw()를 호출했으며 선이 가로 또는 세로이고 brush.gx_brush_line_pattern 필드가 0이 아니면 패턴 선이 그려집니다.

브러시 패턴 마스크는 현재 가로선과 세로선에 대해서만 지원됩니다.

### <a name="parameters"></a>매개 변수

- **pattern** 브러시에 사용되는 패턴. 패턴 선 그리기에 사용되는 간단한 16진수 켜기/끄기 패턴입니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 브러시를 설정했습니다.
- **GX_INVALID_CONTEXT**(0x06) 그리기 컨텍스트가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the brush pattern for the current contex. */
status = gx_context_brush_pattern_set(0x80808080);

/* If status is GX_SUCCESS the brush pattern of the current context
has been set to the specified pattern. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_get,
- gx_context_brush_style_set
- gx_context_brush_width_set,
- gx_context_fill_color_set
- gx_context_font_set,
- gx_context_line_color_set
- gx_context_pixelmap_set,
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set,
- gx_context_raw_line_color_set

## <a name="gx_context_brush_set"></a>gx_context_brush_set


현재 그리기 컨텍스트의 브러시 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_brush_set(GX_BRUSH *brush);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트의 브러시를 설정합니다.

### <a name="parameters"></a>매개 변수

- **brush** 현재 컨텍스트에 사용할 브러시에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 브러시를 설정했습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_BRSUH my_brush;
GX_FONT *font;
GX_COLOR fill_color;
GX_COLOR line_color;

/* Retrieve the font that associated with the specified font ID. */
gx_context_font_get(MY_FONT_ID, &font);

/* Retrieve the color that associated with the specified color ID. */
gx_context_color_get(MY_FILL_COLOR_ID, &fill_color);
gx_context_color_get(MY_LINE_COLOR, &line_color);

my_brush.gx_brush_pixelmap = MY_PIXELMAP_ID;
my_brush.gx_brush_font = font;
my_brush.gx_brush_line_pattern = 0x80808080;
my_brush.gx_brush_pattern_mask = 0x80000000;
my_brush.gx_brush_fill_color = fill_color;
my_brush.gx_brush_line_color = line_color;
my_brush.gx_brush_style = GX_BRSUH_SOLID_FILL | GX_BRUSH_ALIAS |
                          GX_BRUSH_PIXELMAP_FILL | GX_BRUSH_ROUND
my_brush.gx_brush_width = 2;
my_brush.gx_brush_alpha = 255;

/* Set the brush of the current context. */
status = gx_context_brush_set(my_brush);

/* If status is GX_SUCCESS the brush of the current context has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_get,
- gx_context_brush_pattern_set
- gx_context_brush_style_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_style_set"></a>gx_context_brush_style_set


현재 그리기 컨텍스트의 브러시 스타일 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_brush_style_set(UINT style);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트의 브러시 스타일을 설정합니다.

### <a name="parameters"></a>매개 변수

- **style** 현재 컨텍스트의 브러시 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 브러시 스타일을 설정했습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the brush style of the current context. */
status = gx_context_brush_style_set(GX_BRUSH_ALIAS);

/* If status is GX_SUCCESS the brush style of the current context has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_get,
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_width_set,
- gx_context_fill_color_set
- gx_context_font_set,
- gx_context_line_color_set
- gx_context_pixelmap_set,
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set,
- gx_context_raw_line_color_set

## <a name="gx_context_brush_width_set"></a>gx_context_brush_width_set


현재 그리기 컨텍스트의 브러시 너비 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_brush_width_set(UINT width);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트의 활성 브러시 너비를 설정합니다.

### <a name="parameters"></a>매개 변수

**width** 현재 컨텍스트의 브러시 너비(픽셀)

### <a name="return-values"></a>반환 값

**GX_SUCCESS**(0x00) 컨텍스트 브러시 너비를 설정했습니다.

**GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the brush width of the current context to 10 pixels. */
status = gx_context_brush_width_set(10); /*

If status is GX_SUCCESS the brush width of the current context has been set to 10. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_color_get"></a>gx_context_color_get


현재 그리기 컨텍스트의 색 ID와 연결된 색 값 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_color_get(
    GX_RESOURCE_ID color_id,
    GX_COLOR *return_color);
```

### <a name="description"></a>Description

이 서비스는 표시된 색 ID와 연결된 색 값을 검색합니다. 색 값은 활성 컨텍스트 디스플레이의 색 형식으로 반환됩니다. 이 서비스는 활성 그리기 작업 내에서만 호출해야 합니다.

### <a name="parameters"></a>매개 변수

**color_id** 요청된 색의 리소스 ID

**return_color** 반환된 색 값을 저장할 변수의 주소

### <a name="return-values"></a>반환 값

**GX_SUCCESS**(0x00) 색 값을 가져왔습니다.

**GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.

**GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.

**GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_COLOR color_value;

/* Get the color vaue. */
status = gx_context_color_get(MY_BLACK_COLOR_ID, &color_value);
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_fill_color_set"></a>gx_context_fill_color_set

현재 그리기 컨텍스트의 채우기 색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_fill_color_set(GX_RESOURCE_ID fill_color_id);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트의 활성 브러시 채우기 색을 설정합니다.

### <a name="parameters"></a>매개 변수

- **fill_color_id** 현재 컨텍스트 채우기 색의 리소스 ID. **부록 B** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 채우기 색을 설정했습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the fill color of the current context to black. */
status = gx_context_fill_color_set(MY_BLACK_COLOR_ID);

/* If status is GX_SUCCESS the fill color of the current context has been set to black. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_font_get"></a>gx_context_font_get

현재 그리기 컨텍스트에서 글꼴 ID와 연결된 글꼴을 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_font_get(
    GX_RESOURCE_ID font_id,
    GX_FONT **return_font);
```

### <a name="description"></a>Description

이 서비스는 지정된 글꼴 ID와 연결된 글꼴 포인터를 검색합니다. 이 서비스는 활성 그리기 작업 내에서만 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **font_id** 요청된 글꼴의 리소스 ID
- **return_font** 반환된 글꼴 포인터를 저장할 변수의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 글꼴을 검색했습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_FONT *my_font;

/* Get the font pointer. */
status = gx_context_font_get(MY_MIDSIZE_FONT, &my_font);

/* If status is GX_SUCCESS, the font that indicated with MY_MIDSIZE_FONT has been successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_font_set"></a>gx_context_font_set

현재 그리기 컨텍스트의 글꼴 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_font_set(GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트의 활성 브러시 글꼴을 설정합니다.

### <a name="parameters"></a>매개 변수

- **font_id** 현재 컨텍스트의 글꼴 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 글꼴을 설정했습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the font of the current context to MY_FONT_ID. */
status = gx_context_font_set(MY_FONT_ID);

/* If status is GX_SUCCESS the font of the current context has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_line_color_set"></a>gx_context_line_color_set

현재 그리기 컨텍스트의 선 색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_line_color_set(GX_RESOURCE_ID line_color_id);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트의 활성 브러시 선 색을 설정합니다.

### <a name="parameters"></a>매개 변수

- **line_color_id** 현재 컨텍스트의 선 색. **부록 B** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 선 색을 설정했습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the line color of the current context to black. */
status = gx_context_line_color_set(GX_COLOR_BLACK_ID);

/* If status is GX_SUCCESS the line color of the current context has been set to black. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_pixelmap_get"></a>gx_context_pixelmap_get

현재 그리기 컨텍스트에서 pixelmap ID와 연결된 pixelmap 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_pixelmap_get(
    GX_RESOURCE_ID pixelmap_id,
    GX_PIXELMAP **return_map);
```

### <a name="description"></a>Description

이 서비스는 표시된 pixelmap ID와 연결된 pixelmap 포인터를 검색합니다.

### <a name="parameters"></a>매개 변수

- **pixelmap_id** 요청된 pixelmap의 리소스 ID
- **return_map** 반환된 pixelmap 주소를 저장할 변수의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap을 검색했습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.
- **GX_PTR_ERROR**(0x07) pixelmap 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_PIXELMAP *map;

/* Get the pixelmap pointer. */
status = gx_context_pixelmap_get(MY_PIXELMAP_ID, &map);

/* If status is GX_SUCCESS, the pixelmap was successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_pixelmap_set"></a>gx_context_pixelmap_set

현재 그리기 컨텍스트의 pixelmap 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_pixelmap_set(GX_RESOURCE_ID pixelmap_id);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트의 활성 브러시 pixelmap을 할당합니다.

### <a name="parameters"></a>매개 변수

- **pixelmap_id** 현재 컨텍스트에 사용할 pixelmap 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 pixelmap을 설정했습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_INVLAID_CONTEXT**(0x06) 컨텍스트가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set pixelmap of the current context to MY_PIXELMAP_ID. */
status = gx_context_pixelmap_set(MY_PIXELMAP_ID);

/* If status is GX_SUCCESS the pixelmap of the current context has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_raw_brush_define"></a>gx_context_raw_brush_define

현재 그리기 컨텍스트의 원시 브러시 정의

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_raw_brush_define(
    GX_COLOR line_color,
    GX_COLOR fill_color, 
    UINT style);
```

### <a name="description"></a>Description

이 서비스는 현재 화면 컨텍스트의 원시 브러시를 정의합니다. 원시 정의는 색 ID 대신 32비트 ARGB 색 값을 브러시에 전달하는 경우에 사용됩니다. 현재 시스템 색 테이블에 원하는 색이 없거나 런타임에 RGB 색 값이 계산되는 경우 원시 색 정의가 유용합니다.

### <a name="parameters"></a>매개 변수

- **line_color** 32비트 원시 ARGB 색 형식의 선 색. **부록 A** 에는 미리 정의된 색이 나와 있습니다. 애플리케이션에서 사용자 지정 색을 추가할 수도 있습니다.
- **fill_color** 32비트 원시 ARGB 색 형식의 채우기 색. **부록 A** 에는 미리 정의된 색이 나와 있습니다. 애플리케이션에서 사용자 지정 색을 추가할 수도 있습니다.
- **style** 브러시의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 원시 브러시를 정의했습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Define the raw brush of the current context. */
status = gx_context_raw_brush_define(GX_COLOR_BLACK,
    GX_COLOR_BLACK, GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the raw brush of the current context has been defined. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_raw_fill_color_set"></a>gx_context_raw_fill_color_set

현재 그리기 컨텍스트의 원시 채우기 색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_raw_fill_color_set(GX_COLOR line_color);
```

### <a name="description"></a>Description

이 서비스는 현재 화면 컨텍스트의 원시 채우기 색을 설정합니다. line_color 매개 변수는 색 ID 값이 아니라 32비트 ARGB 형식의 원시 색 값입니다. 현재 시스템 색 테이블에 원하는 색이 없거나 런타임에 RGB 색 값이 계산되는 경우 원시 색 정의가 유용합니다.

### <a name="parameters"></a>매개 변수

- **line_color** 선의 색. **부록 A** 에는 미리 정의된 색이 나와 있습니다. 애플리케이션에서 사용자 지정 색을 추가할 수도 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 원시 채우기 색을 설정했습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the raw fill color of the current context. */
status = gx_context_raw_fill_color_set(GX_COLOR_BLACK);

/* If status is GX_SUCCESS the raw fill color of the current context has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_line_color_set

## <a name="gx_context_raw_line_color_set"></a>gx_context_raw_line_color_set

현재 그리기 컨텍스트의 원시 선 색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_raw_line_color_set(GX_COLOR line_color);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트의 활성 브러시 선 색을 설정합니다. line_color 매개 변수는 색 ID 값이 아니라 32비트 ARGB 형식의 원시 색 값입니다. 현재 시스템 색 테이블에 원하는 색이 없거나 런타임에 RGB 색 값이 계산되는 경우 원시 색 정의가 유용합니다.

### <a name="parameters"></a>매개 변수

- **line_color** 선의 색 값. **부록 A** 에는 미리 정의된 색이 나와 있습니다. 애플리케이션에서 사용자 지정 색을 추가할 수도 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 원시 선 색을 설정했습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

```C
/* Set the raw line color of the current context. */
status = gx_context_raw_line_color_set(GX_COLOR_BLACK);

/* If status is GX_SUCCESS the raw line color of the current context has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set

## <a name="gx_context_string_get"></a>gx_context_string_get

문자열 ID와 연결된 문자열 검색(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_string_get(GX_RESOURCE_ID string_id,
    GX_CONST GX_CHAR **return_string);
```

### <a name="description"></a>Description

이 API(사용되지 않음)는 지정된 문자열 ID와 연결된 문자열을 반환합니다. 새 애플리케이션에서는 gx_context_string_get_ext()를 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **string_id** GUIX Studio 애플리케이션에서 생성된 문자열 ID
- **return_string** 문자열 포인터를 반환할 변수의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 원시 선 색을 설정했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CHAR *text;

status = gx_context_string_get(GX_ID_ERROR, &text);

/* If status is GX_SUCCESS the string pointer has been returned. */
```

### <a name="see-also"></a>참고 항목

- gx_context_string_get_ext

## <a name="gx_context_string_get_ext"></a>gx_context_string_get_ext

지정된 문자열 ID와 연결된 문자열 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_context_string_get_ext(
    GX_RESOURCE_ID string_id, 
    GX_STRING *return_string);
```

### <a name="description"></a>Description

이 서비스는 지정된 문자열 ID와 연결된 문자열을 반환합니다. 위젯의 그리기 함수 내에서와 같이 활성 그리기 컨텍스트가 있는 경우에만 호출할 수 있습니다. 이 서비스는 활성 캔버스 및 디스플레이를 식별하고 찾은 디스플레이 인스턴스에서 문자열을 검색합니다.

### <a name="parameters"></a>매개 변수

- **string_id** 문자열을 식별하는 데 사용되는 문자열 ID. 애플리케이션 리소스 헤더 파일에서 GUIX Studio를 통해 생성됩니다.
- **return_string** 문자열 포인터와 문자열 길이가 반환되는 GX_STRING 변수의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 컨텍스트 원시 선 색을 설정했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_CONTEXT**(0x06) 활성 그리기 컨텍스트가 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제


```C
GX_STRING string;

/* Set the raw line color of the current context. */
status = gx_context_string_get_ext(ID_ERROR, &string);

/* If status is GX_SUCCESS the string.gx_string_ptr and
string.gx_string_length values have been returned. */
```

### <a name="see-also"></a>참고 항목

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set

## <a name="gx_display_active_language_set"></a>gx_display_active_language_set

디스플레이 활성 언어 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_active_language_set(
    GX_DISPLAY *display, 
    GX_UBYTE language);
```

### <a name="description"></a>Description

이 서비스는 표시된 디스플레이에 대해 현재 활성 언어를 할당합니다. 언어 인덱스는 디스플레이 언어 테이블에 정의된 언어에 해당하며 ANSI 언어 식별자가 아닙니다.

다중 디스플레이 시스템의 여러 디스플레이에서 각각 다른 활성 언어를 실행할 수 있습니다. 이 API를 사용하려면 먼저 디스플레이 언어 테이블을 할당해야 합니다. gx_studio_display_configure를 사용하여 디스플레이를 초기화하면 언어 테이블이 자동으로 설치되고 애플리케이션에서 활성 언어 인덱스를 전달합니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **language** 활성 언어 인덱스

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 언어를 할당했습니다.
- **GX_PTR_ERROR**(0x07) 디스플레이 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 언어 인덱스가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Change value of color MY_COLOR_ID. */
status = gx_display_active_language_set(&my_display,
    LANGUAGE_ENGLISH);

/* If status is GX_SUCCESS the active language has been assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_display_language_table_set
- gx_studio_display_configure

## <a name="gx_display_color_set"></a>gx_display_color_set

하나의 색 값 다시 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_color_set(
    GX_DISPLAY *display,
    GX_RESOURCE_ID color_id, 
    GX_COLOR new_color);
```

### <a name="description"></a>Description

이 서비스는 지정된 색 ID와 연결된 색 값을 다시 할당합니다. 완전히 새로운 색 테이블을 제공하지 않고 디스플레이의 색 테이블을 수정하는 데 사용할 수 있습니다. 제공한 색 값은 디스플레이에서 지원되는 원시 형식이어야 합니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **color_id** 다시 할당할 색 ID
- **new_color** 이 color_id 슬롯에 할당할 색 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 색을 다시 할당했습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 색 ID가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_DISPLAY**(0x1D) 디스플레이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Change value of color MY_COLOR_ID. */
status = gx_display_color_set(&my_display, MY_COLOR_ID, 0x5454);

/* If status is GX_SUCCESS the color has been reassigned. */
```

### <a name="see-also"></a>참고 항목

- gx_display_color_table_set

## <a name="gx_display_color_table_set"></a>gx_display_color_table_set

디스플레이 색 테이블 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_color_table_set(
    GX_DISPLAY *display,
    GX_COLOR *color_table, 
    INT color_count);
```

### <a name="description"></a>Description

이 서비스는 디스플레이에서 사용할 색 테이블을 다시 할당합니다. 일반적으로 GUIX Studio를 통해 생성된 디스플레이 구성 함수에서 호출되지만 애플리케이션 소프트웨어에서도 호출할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **color_table** 디스플레이 원시 형식의 색 값 배열
- **color_count** 색 테이블의 항목 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 색 테이블을 설정했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_DISPLAY**(0x1D) 디스플레이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_COLOR default_table[32] = { … };

/* Change the color table */
status = gx_display_color_table_set(&my_display, default_table, 32);

/* If status is GX_SUCCESS the color table has been reassigned. */
```

### <a name="see-also"></a>참고 항목

- gx_display_color_set

## <a name="gx_display_create"></a>gx_display_create

디스플레이 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_create(
    GX_DISPLAY *display, 
    GX_CONST CHAR *name,
    UINT (*display_driver_setup)(GX_DISPLAY *),
    GX_VALUE width, 
    GX_VALUE height);
```

### <a name="description"></a>Description

이 서비스는 디스플레이를 만들고 디스플레이 드라이버 설치 함수를 호출합니다. GUIX는 이 디스플레이를 가져와 내부 디스플레이 목록에 추가합니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **name** 디스플레이의 이름
- **display_driver_setup** 디스플레이 드라이버 설치 함수에 대한 포인터
- **optional_driver_info** 선택적 드라이버 정보에 대한 포인터
- **color_format** **부록 C** 에 정의된 색 형식
- **width** x축의 픽셀 수
- **height** y축의 픽셀 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 디스플레이를 만들었습니다.
- **GX_SYSTEM_ERROR**(0xFE) 디스플레이를 설정하지 못했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_SIZE**(0x23) 디스플레이 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_DISPLAY my_display;

UINT my_driver_setup_callback(GX_DISPLAY *display)
{
    …
}

/* Create screen “my_display”. */
status = gx_display_create(&my_display, “my display”,
    my_driver_setup_callback, 320, 480);

/* If status is GX_SUCCESS, the screen “my_display” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_display_delete

## <a name="gx_display_delete"></a>gx_display_delete


디스플레이 삭제

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_delete(
    GX_DISPLAY *display,
    VOID (*display_driver_cleanup)(GX_DISPLAY *));
```

### <a name="description"></a>Description

이 서비스는 디스플레이를 종료하고 할당된 리소스를 정리합니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **display_driver_cleanup** 디스플레이 드라이버 정리 함수에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 디스플레이를 삭제했습니다.
- **GX_FAILURE**(0x10) 생성된 디스플레이 목록이 NULL입니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
VOID driver_cleanup_callback(GX_DISPLAY *display)
{
    …
}

/* Delete a display “my_display”. */
status = gx_display_delete(&my_display, driver_cleanup_callback);

/* If status is GX_SUCCESS the screen “my_display” has been destroyed. */
```

### <a name="see-also"></a>참고 항목

- gx_canvas_block_move
- gx_canvas_line_draw
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw
- gx_canvas_text_draw
- gx_display_create

## <a name="gx_display_font_table_set"></a>gx_display_font_table_set

디스플레이 글꼴 테이블 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_font_table_set(
    GX_DISPLAY *display,
    GX_FONT **font_table, 
    INT table_size);
```

### <a name="description"></a>Description

이 서비스는 디스플레이에서 사용할 글꼴 테이블을 다시 할당합니다. 일반적으로 GUIX Studio를 통해 생성된 디스플레이 구성 함수에서 호출되지만 애플리케이션 소프트웨어에서도 호출할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **font_table** GX_FONT 포인터 배열
- **table_size** 테이블의 글꼴 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 글꼴 테이블을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_FONT *font_table[32] = { … };

/* Assign font table */
status = gx_display_font_table_set(&my_display, font_table, 32);

/* If status is GX_SUCCESS, the font table has been reassigned. */
```

### <a name="see-also"></a>참고 항목

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_language_table_get"></a>gx_display_language_table_get

디스플레이 언어 테이블 검색(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_language_table_get(
    GX_DISPLAY *display,
    GX_CHAR **table, 
    GX_UBYTE *language_count,
    UINT *string_table_size);
```

### <a name="description"></a>Description

이 서비스는 표시된 디스플레이에서 언어 테이블을 검색합니다. 애플리케이션에서 동적으로 정의된 문자열을 사용하여 런타임에 디스플레이 언어 테이블을 수정하는 데 사용할 수 있습니다.

이 API는 사용되지 않으며 이전 스타일 언어 테이블을 사용하는 애플리케이션에서만 지원됩니다. 즉, Studio에서 생성된 리소스 파일은 버전 5.6 이전 라이브러리 버전용으로 생성됩니다. 새 애플리케이션에서는 gx_display_language_table_get_ext()를 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **table** 테이블 포인터를 수신할 주소
- **language_count** 언어 수를 수신할 주소
- **string_table_size** 문자열 테이블 크기를 수신할 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 글꼴 테이블을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CHAR **language_table;
GX_UBYTE language_count;
UINT string_count;

/* Retrieve language table */
status = gx_display_language_table_get(&my_display,
        &language_table, &language_count, &string_count);

/* If status is GX_SUCCESS, the language table has been retrieved.
```

### <a name="see-also"></a>참고 항목

- gx_display_language_table_set
- gx_display_active_langauge_set
- gx_display_string_get
- gx_display_language_table_get_ext

## <a name="gx_display_language_table_get_ext"></a>gx_display_language_table_get_ext

디스플레이 언어 테이블 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_language_table_get_ext(
    GX_DISPLAY *display,
    GX_STRING **table, 
    GX_UBYTE *language_count, 
    UINT *string_table_size);
```

### <a name="description"></a>Description

이 서비스는 표시된 디스플레이에서 언어 테이블을 검색합니다. 애플리케이션에서 동적으로 정의된 문자열을 사용하여 런타임에 디스플레이 언어 테이블을 수정하는 데 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **table** 테이블 포인터를 수신할 주소
- **language_count** 언어 수를 수신할 주소
- **string_table_size** 문자열 테이블 크기를 수신할 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 글꼴 테이블을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING **language_table;
GX_UBYTE language_count;
UINT string_count;

/* Retrieve language table */
status = gx_display_language_table_get_ext(&my_display,
    &language_table, &language_count, &string_count);

/* If status is GX_SUCCESS, the language table has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_display_language_table_set_ext
- gx_display_active_langauge_set
- gx_display_string_get_ext

## <a name="gx_display_language_table_set"></a>gx_display_language_table_set

디스플레이 언어 테이블 할당(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_language_table_set(
    GX_DISPLAY *display,
    GX_CHAR **table, 
    GX_UBYTE number_of_languages, 
    UINT number_of_strings);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 새 애플리케이션에서는 gx_display_language_table_set_ext()를 사용해야 합니다. 버전 5.6 이전 라이브러리 버전을 대상으로 하여 Studio에서 생성된 리소스 파일과의 호환성을 위해서만 지원됩니다.

이 서비스는 디스플레이에서 사용할 언어 테이블을 할당합니다. 일반적으로 GUIX Studio를 통해 생성된 gx_studio_display_configure 함수에서 호출되지만 애플리케이션 소프트웨어에서도 호출할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **table** 언어 테이블
- **number_of_languages** 제공한 테이블의 열 수
- **number_of_strings** 각 테이블 열의 문자열 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 글꼴 테이블을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CHAR ***language_table= my_app_language_table;

/* Assign language table */
status = gx_display_language_table_set(&my_display, language_table,
5, 232);

/* If status is GX_SUCCESS, the language table has been reassigned. */
```

### <a name="see-also"></a>참고 항목

- gx_display_active_language_set
- gx_display_string_get

## <a name="gx_display_language_table_set_ext"></a>gx_display_language_table_set_ext

디스플레이 언어 테이블 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_language_table_set_ext(
    GX_DISPLAY *display,
    GX_STRING **table, 
    GX_UBYTE number_of_languages,
    UINT number_of_strings);
```

### <a name="description"></a>Description

이 서비스는 디스플레이에서 사용할 언어 테이블을 할당합니다. 일반적으로 GUIX Studio를 통해 생성된 gx_studio_display_configure 함수에서 호출되지만 애플리케이션 소프트웨어에서도 호출할 수 있습니다.

런타임 언어 테이블 할당은 일반적으로 gx_binres_language_table_load()를 사용하여 이진 리소스 파일에서 언어를 로드할 때 수행됩니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **table** 언어 테이블
- **number_of_languages** 제공한 테이블의 열 수
- **number_of_strings** 각 테이블 열의 문자열 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 글꼴 테이블을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING **language_table = my_app_language_table;

/* Assign the language table */
status = gx_display_language_table_set_ext(&my_display,
    language_table, 5, 132);

/* If status is GX_SUCCESS, the language table has been reassigned. */
```

### <a name="see-also"></a>참고 항목

- gx_display_active_language_set
- gx_display_string_get

## <a name="gx_display_pixelmap_table_set"></a>gx_display_pixelmap_table_set

디스플레이 글꼴 테이블 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_pixelmap_table_set(
    GX_DISPLAY *display,
    GX_PIXELMAP **pixelmap_table, 
    INT table_size);
```

### <a name="description"></a>Description

이 서비스는 디스플레이에서 사용할 pixelmap 테이블을 다시 할당합니다. 일반적으로 Studio를 통해 생성된 디스플레이 구성 함수에서 호출되지만 애플리케이션 소프트웨어에서도 호출할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **pixelmap_table** GX_PIXELMAP 포인터 배열
- **table_size** 테이블의 pixelmap 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap 테이블을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_PIXELMAP *pixelmap_table[32] = { … };

/* Assign pixelmap table */
status = gx_display_pixelmap_table_set(&my_display, pixelmap_table, 32);

/* If status is GX_SUCCESS the pixelmap table has been reassigned. */
```

### <a name="see-also"></a>참고 항목

- gx_display_color_set
- gx_display_color_table_set
- gx_display_font_table_set

## <a name="gx_display_string_get"></a>gx_display_string_get

활성 문자열 테이블에서 문자열 검색(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_string_get(
    GX_DISPLAY *display,
    GX_RESOURCE_ID string_id, 
    GX_CONST GX_CHAR **string);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_display_string_get_ext()로 대체되었습니다.

표시된 디스플레이의 활성 문자열 테이블에서 문자열을 검색합니다. 활성 언어는 디스플레이에 할당된 언어 테이블에서 문자열을 선택하는 데 사용됩니다.

문자열 ID는 GUIX Studio에서 생성되며 애플리케이션 resources.h 헤더 파일에 있습니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **string_id** GUIX Studio에서 생성된 문자열 ID
- **string** 문자열 포인터 변수의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 문자열을 검색했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 문자열 ID가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 디스플레이 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CHAR *string;

/* Retrieve string value */
status = gx_display_string_get(&my_display,
    GX_STRING_ID_MONDAY, &string);

/* If status is GX_SUCCESS, the string has been retrieved. */
```


### <a name="see-also"></a>참고 항목

- gx_display_active_language_set
- gx_display_language_table_set

## <a name="gx_display_string_get_ext"></a>gx_display_string_get_ext

활성 문자열 테이블에서 문자열 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_string_get_ext(
    GX_DISPLAY *display,
    GX_RESOURCE_ID string_id,
    GX_STRING *string);
```

### <a name="description"></a>Description

표시된 디스플레이의 활성 문자열 테이블에서 문자열을 검색합니다. 활성 언어는 디스플레이에 할당된 언어 테이블에서 문자열을 선택하는 데 사용됩니다.

문자열 ID는 GUIX Studio에서 생성되며 애플리케이션 resources.h 헤더 파일에 있습니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **string_id** GUIX Studio에서 생성된 문자열 ID
- **string** 
- **string.gx_string_ptr** 및
- **string.gx_string_length** 가 반환되는 GX_STRING 변수의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 문자열을 검색했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 문자열 ID가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 디스플레이 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING string;

/* Retrieve string value */
status = gx_display_string_get_ext(&my_display,
    GX_STRING_ID_MONDAY, &string);

/* If status is GX_SUCCESS, the string has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_display_active_language_set
- gx_display_language_table_set


## <a name="gx_display_string_table_get"></a>gx_display_string_table_get


활성 문자열 테이블 검색(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_string_table_get(
    GX_DISPLAY *display,
    GX_UBYTE language, 
    GX_CHAR ***table,
    UINT *table_size);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_display_string_table_get_ext()로 대체되었습니다.

활성 언어와 연결된 문자열 테이블을 검색합니다. 이 서비스는 자주 사용되지 않지만 런타임에 문자열 테이블을 수정해야 하는 애플리케이션의 완전성을 위해 제공됩니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **language** 검색할 테이블 열
- **table** 포인터를 반환할 변수의 주소
- **table_size** 테이블 크기를 반환할 변수의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 글꼴 테이블을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_NOT_FOUND**(0x09) 언어 인덱스가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CHAR **string_table;
UINT table_size;

/* Retrieve string table */
status = gx_display_string_table_get(&my_display, LANGUAGE_ENGLISH,
    &string_table, &table_size);

/* If status is GX_SUCCESS, the string table has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_string_table_get_ext"></a>gx_display_string_table_get_ext


활성 문자열 테이블 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_string_table_get(
    GX_DISPLAY *display,
    GX_UBYTE language, 
    GX_STRING **table, 
    UINT *table_size);
```

### <a name="description"></a>Description

활성 언어와 연결된 문자열 테이블을 검색합니다. 이 서비스는 자주 사용되지 않지만 런타임에 문자열 테이블을 수정해야 하는 애플리케이션의 완전성을 위해 제공됩니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **language** 검색할 테이블 열
- **table** 포인터를 반환할 변수의 주소
- **table_size** 테이블 크기를 반환할 변수의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 글꼴 테이블을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_NOT_FOUND**(0x09) 언어 인덱스가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING *string_table;
UINT table_size;

/* Retrieve string table */
status = gx_display_string_table_get_ext(&my_display,
    LANGUAGE_ENGLISH, &string_table, &table_size);

/* If status is GX_SUCCESS, the string table has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_theme_install"></a>gx_display_theme_install


지정된 디스플레이에 테마 설치

### <a name="prototype"></a>프로토타입

```C
UINT gx_display_theme_install(
    GX_DISPLAY *display, 
    GX_THEME *theme_table);
```

### <a name="description"></a>Description

이 서비스는 지정된 디스플레이에 테마를 설치합니다. 일반적으로 Studio를 통해 생성된 디스플레이 구성 함수에서 호출되지만 애플리케이션 소프트웨어에서도 호출할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **display** 디스플레이 제어 블록에 대한 포인터
- **theme_table** 설치할 테마 테이블

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 테마 테이블을 설치했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 테마 테이블 포인터가 잘못되었습니다.
- **GX_INVALID_DISPLAY**(0x1D) 디스플레이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_THEME theme_1;

&theme_table[1] = {
    &theme_1,
    …
}

/* Define resource tables. */
GX_COLOR color_table[32] = {…};
GX_FONT *font_table[32] = {…};
GX_PIXELMAP *pixelmap_table[32] = { … };

/* Define scroll appearance. */
GX_SCROLLBAR_APPEARANCE scroll_appearance;

memset(&scroll_appearance, 0, sizeof(GX_SCROLLBAR_APPEARANCE));

scroll_appearance.gx_scroll_width = 20;
scroll_appearance.gx_scroll_thumb_width = 18;
scroll_appearance.gx_scroll_thumb_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_thumb_border_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_button_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_thumb_travel_min = 20;
scroll_appearance.gx_scroll_thumb_travel_max = 20;
scroll appearance.gx_scroll_thumb_border_style =
    GX_STYLE_BORDER_THIN;

theme_1.theme_color_table = color_table;
theme_1.theme_font_table = font_table;
theme_1.theme_pixlemap_table = pixelmap_table;
theme_1.theme_palette = GX_NULL;
theme_1.theme_vertical_scrollbar_appearance = scroll_appearance;
theme_1.theme_horizontal_scrollbar_appearance = scroll_appearance;
theme_1.theme_vertical_scroll_style = GX_SCROLLBAR_RELATIVE_THUMB;
theme_1.theme_horizontal_scroll_style =
    GX_SCROLLBAR_RELATIVE_THUMB;
theme_1.theme_color_table_size = 32;
theme_1.theme_font_table_size = 32;
theme_1.theme_pixelmap_table_size = 32;
theme_1.theme_palette_size = 0;

/* Install theme table. */
status = gx_display_theme_install(&my_display, theme_table);

/* If status is GX_SUCCESS the theme table has been installed. */
```

### <a name="see-also"></a>참고 항목

- gx_display_color_set
- gx_display_color_table_set
- gx_display_font_table_set

## <a name="gx_drop_list_close"></a>gx_drop_list_close


드롭 목록 닫기

### <a name="prototype"></a>프로토타입

```C
UINT gx_drop_list_close(GX_DROP_LIST *drop_list);
```

### <a name="description"></a>Description

이 서비스는 지정된 드롭 목록의 팝업 목록을 닫습니다.

### <a name="parameters"></a>매개 변수

- **drop_list** 드롭 목록 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 드롭 목록을 닫았습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Close a drop list. */
status = gx_drop_list_close(&drop_list);

/* If status is GX_SUCCESS, the drop list is closed. */
```

### <a name="see-also"></a>참고 항목

- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_open

gx_drop_list_pixelmap_set, gx_drop_list_popup_get

## <a name="gx_drop_list_create"></a>gx_drop_list_create


드롭 목록 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_drop_list_create(
    GX_DROP_LIST *drop_list, 
    GX_CONST
    GX_CHAR *name, 
    GX_WIDGET *parent,
    INT total_rows, 
    INT open_height,
    VOID (*callback)(GX_VERTICAL_LIST *, 
    GX_WIDGET *, INT),
    ULONG style, 
    USHORT drop_list_id,
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>Description

이 서비스는 드롭 목록을 만듭니다. 드롭 목록은 드롭 목록 위젯 및 드롭 목록을 열 때 표시되는 팝업 세로 목록의 조합입니다. 팝업 세로 목록은 드롭 목록 위젯을 만들 때 자동으로 생성되고, 드롭 목록 위젯을 열거나 닫을 때 각각 표시되거나 숨겨집니다.

드롭 목록 위젯은 두 개의 연결된 pixelmap을 지원합니다. Studio 속성 뷰에서 “목록 배경 화면”으로 설명된 첫 번째 pixelmap은 드롭 목록 위젯을 열 때 표시되는 세로 목록의 배경으로 표시되는 선택적 배경 화면 pixelmap입니다. Studio 속성 뷰에서 “배경 이미지”로 설명된 두 번째 pixelmap은 드롭다운 목록 자체의 배경으로 표시되는 선택적 이미지입니다.

드롭 목록 위젯에는 드롭 목록을 열고 닫는 데 사용되는 자식 위젯이 포함될 수 있지만 반드시 필요한 것은 아닙니다. 일반적으로 아이콘 또는 단추 위젯이지만 사용자 지정 위젯을 부모 드롭 목록의 열기/닫기 토글로 사용할 수도 있습니다. 이 자식 위젯을 통해 드롭 목록을 작동하기 위한 주요 설정은 자식 위젯에 미리 정의된 위젯 id인 ID_DROP_LIST_BUTTON이 있어야 한다는 것입니다.

드롭 목록을 열고 닫는 자식 위젯을 정의하려면 먼저 드롭 목록에 자식 위젯을 추가한 다음, 드롭 목록 내에서 이 자식을 원하는 대로 배치합니다.

![드롭 목록 스크린샷](./media/guix/image6.jpg)

Studio 속성 뷰를 사용하여 부모 드롭 목록에서 인식되는 내부적으로 정의된 ID 값인 ID_DROP_LIST_BUTTON ID 값을 이 자식 위젯에 할당합니다.

![Studio 속성 뷰 스크린샷](./media/guix/image7.jpg)

### <a name="parameters"></a>매개 변수
- **drop_list** 드롭 목록 컨트롤 블록에 대한 포인터
- **name** 드롭 목록의 이름
- **parent** 부모 위젯에 대한 포인터
- **total_rows** 드롭 목록에 있는 행의 총수
- **open_height** 드롭 목록을 열 때 표시되는 세로 목록의 높이
- **callback** 목록을 스크롤할 때 세로 목록에서 호출되는 함수. 자세한 내용은 GX_VERTICAL_LIST 설명서를 참조하세요.
- **style** 드롭다운 목록 테두리 스타일
- **drop_list_id** 애플리케이션에서 정의된 드롭 목록 ID
- **size** 드롭 목록의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 드롭 목록을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_DROP_LIST my_drop_list;
VOID list_row_create(GX_VERTICAL_LIST *list,
                     GX_WIDGET *row, INT index);
{
    …
}

GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 10, 10, 80, 40);

status = gx_drop_list_create(&my_drop_list,
    "my drop list", GX_NULL,
    10, 100, list_row_create,
    GX_STYLE_BORDER_RECESSED | GX_STYLE_ENABLED,
    ID_DROP_LIST, &size)

/* Is status is GX_SUCCESS, the drop list was successfully created. */
```

### <a name="see-also"></a>참고 항목:

- gx_drop_list_close
- gx_drop_list_event_process
- gx_drop_list_open
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_event_process"></a>gx_drop_list_event_process


드롭 목록 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_drop_list_event_process(
    GX_DROP_LIST *list, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 드롭 목록에 대한 이벤트를 처리합니다.

### <a name="parameters"></a>매개 변수

- **drop_list** 드롭 목록 위젯 컨트롤 블록
- **event** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 드롭 목록 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic drop list event processing as part of custom event processing function. */

UINT custom_drop_list_event_process(GX_DROP_LIST *drop_list,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default drop list
            event processing */
        status = gx_drop_list_event_process(drop_list, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_open
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_open"></a>gx_drop_list_open


드롭 목록 열기

### <a name="prototype"></a>프로토타입

```C
UINT gx_drop_list_open(GX_DROP_LIST *drop_list);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 드롭 목록을 엽니다.

### <a name="parameters"></a>매개 변수

- **drop_list** 드롭 목록 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 드롭 목록을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_DROP_LIST mylist;

/* Open the popup list of “mylist”. */
status = gx_drop_list_open(&mylist);

/* If status == GX_SUCCESS, the popup list of “mylist” has been displayed. */
```

### <a name="see-also"></a>참고 항목

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_pixelmap_set"></a>gx_drop_list_pixelmap_set


드롭 목록에 배경 이미지 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_drop_list_pixelmap_set(
    GX_DROP_LIST *drop_list,
    GX_RESOURCE_ID id);
```

### <a name="description"></a>Description

드롭 목록에 배경 이미지를 할당합니다. 이 pixelmap은 목록을 열 때 표시되는 팝업 세로 목록이 아닌 드롭 목록 위젯의 배경으로 사용됩니다. 드롭 목록 팝업에 pixelmap을 할당하려면 먼저 gx_drop_list_popup_get을 호출하여 팝업 목록에 대한 포인터를 검색한 다음, gx_window_wallpaper_set()을 사용하여 이 팝업 목록에 pixelmap을 할당해야 합니다.

### <a name="parameters"></a>매개 변수

- **drop_list** 드롭 목록 컨트롤 블록에 대한 포인터
- **id** pixlemap의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 드롭 목록 pixelmap을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) pixlemap ID가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_DROP_LIST mylist;

/* create the drop list here */

/* Assign a pixelmap id, which will turn on the list button */
status = gx_drop_list_pixelmap_set(&mylist,
    GX_PIXELMAP_ID_DROP_LIST_BACKGROND);

/* If status is GX_SUCCESS, the pixelmap was successfully set. */
```

### <a name="see-also"></a>참고 항목:

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_open
- gx_drop_list_popup_get

## <a name="gx_drop_list_popup_get"></a>gx_drop_list_popup_get


팝업 세로 목록에 대한 포인터 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_drop_list_popup_get(
    GX_DROP_LIST *drop_list,
    GX_VERTICAL_LIST **return_list);
```

### <a name="description"></a>Description

드롭 목록 위젯은 드롭 목록 위젯 자체와 드롭 목록 위젯을 열 때 표시되는 팝업 세로 목록으로 구성됩니다. 이 서비스는 드롭 목록의 세로 목록 구성 요소에 대한 포인터를 검색하여 애플리케이션에서 세로 목록에 대해 직접 API 서비스를 호출할 수 있도록 합니다.

### <a name="parameters"></a>매개 변수

- **drop_list** 드롭 목록 컨트롤 블록에 대한 포인터
- **return_list** 드롭 목록에 저장된 세로 목록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 팝업 세로 목록을 검색했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_DROP_LIST drop_list;
GX_VERTICAL_LIST *vertical_list;

/* Retrieve the popup list of “drop_list”. */
status = gx_drop_list_popup_get(&drop_list, &vertical_list)

/* If status is GX_SUCCESS, the popup list was successfully retrieved. */
```

### <a name="see-also"></a>참고 항목:

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_open
- gx_drop_list_pixelmap_set

## <a name="gx_horizontal_list_children_position"></a>gx_horizontal_list_children_position


가로 목록의 자식 배치

### <a name="prototype"></a>프로토타입

```C
UINT gx_horizontal_list_children_position(GX_HORIZONTAL_LIST *horizontal_list);
```

### <a name="description"></a>Description

이 함수는 가로 목록의 자식을 배치합니다. 목록이 GX_EVENT_SHOW 이벤트를 수신할 때 자동으로 호출되지만, 목록이 표시된 후 수정된 경우에는 직접 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **horizontal_list** 가로 목록 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 가로 목록의 자식을 배치했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Position children in the horizontal list */
status = gx_horizontal_list_children_position (&horizontal_list);

/* If status is GX_SUCCESS the children in the horizontal list are positioned. */
```

### <a name="see-also"></a>참고 항목

- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_create"></a>gx_horizontal_list_create


가로 목록 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_horizontal_list_create(
    GX_HORIZONTAL_LIST *horizontal_list,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    INT total_columns,
    VOID (*callback)(GX_HORIZONTAL_LIST *, 
    GX_WIDGET *, INT),
    ULONG style, 
    USHORT horizontal_list_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 가로 목록을 만듭니다.

### <a name="parameters"></a>매개 변수

- **horizontal_list** 가로 목록 위젯 컨트롤 블록
- **name** 가로 목록의 이름
- **parent** 부모 위젯에 대한 포인터
- **total_columns** 가로 목록에 있는 열의 총수
- **callback** 애플리케이션에서 제공하는 콜백 함수에 대한 포인터입니다. 콜백 함수는 가로 목록을 스크롤할 때 호출되어 새로 표시되는 목록 항목을 만듭니다. 이런 방식으로 가로 목록에는 사용자 정의 위젯 형식이 목록 항목으로 표시될 수 있습니다.
- **style** 스크롤 막대 위젯의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **horizontal_list_id** 애플리케이션에서 정의된 가로 목록 ID
- **size** 가로 목록의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 가로 목록을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 열 수가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create horizontal list “my_list” with 5 columns. */
status = gx_horizontal_list_create(&my_list, “my_list”, &my_parent,
    5, callback, GX_STYLE_WRAP, MY_LIST_ID, &size);

/* If status is GX_SUCCESS the horizontal list “my_list” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_horizontal_list_children_position
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_event_process"></a>gx_horizontal_list_event_process


가로 목록 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_horizontal_list_event_process(
    GX_HORIZONTAL_LIST *list,
    GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 가로 목록에 대한 이벤트를 처리합니다.

### <a name="parameters"></a>매개 변수

- **list** 가로 목록 위젯 컨트롤 블록
- **event** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 가로 목록 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Call generic horizontal list event processing as part of custom event processing function. */

UINT custom_list_event_process(
    GX_HORIZONTAL_LIST *list,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default horizontal
        list event processing */
        status =
        gx_horizontal_list_event_process(list, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_page_index_set"></a>gx_horizontal_list_page_index_set


시작 페이지 인덱스 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_horizontal_list_page_index_set(
    GX_HORIZONTAL_LIST *list,
    INT *index);
```

### <a name="description"></a>Description

이 서비스는 가로 목록의 시작 인덱스를 설정합니다.

### <a name="parameters"></a>매개 변수

- **list** 가로 목록 위젯 컨트롤 블록
- **index** 새 상위 인덱스

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 가로 목록의 시작 페이지 인덱스를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Sets the starting page index of horizontal list “my_list” as 1. */
status = gx_horizontal_list_page_index_set(&my_list, 1);

/* If status is GX_SUCCESS the starting page index of “my_list” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_index_get"></a>gx_horizontal_list_selected_index_get


가로 목록에서 선택된 항목 인덱스 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_horizontal_list_selected_index_get(
    GX_horizobntal_LIST *horizontal_list,
    INT *return_index);
```

### <a name="description"></a>Description

이 서비스는 가로 목록에서 선택한 목록 항목 인덱스를 반환합니다.

### <a name="parameters"></a>매개 변수

- **horizontal_list** 가로 목록 위젯 컨트롤 블록
- **return_index** 반환 목록 인덱스의 대상

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 가로 목록 항목을 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
INT current_index_entry;

/* Get the list entry at the current index of horizontal list “my_list”. */
status = gx_horizontal_list_selected_index_get(&my_list,
    &current_index_entry);

/* If status is GX_SUCCESS, “current_index_entry” contains the current list selection index. */
```

### <a name="see-also"></a>참고 항목

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_set"></a>gx_horizontal_list_selected_set


가로 목록에서 선택된 항목 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_horizontal_list_selected_set(
    GX_HORIZONATAL_LIST *horizontal_list,
    INT index);
```

### <a name="description"></a>Description

이 서비스는 가로 목록에서 선택된 항목을 할당합니다. 필요한 경우 가로 목록이 스크롤되어 선택된 항목을 표시합니다.

### <a name="parameters"></a>매개 변수

- **horizontal_list** 가로 목록 위젯 컨트롤 블록
- **index** 새 목록 항목의 인덱스 기반 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 가로 목록 항목을 설정했습니다.
- **GX_FAILURE**(0x10) 인덱스가 잘못된 범위에 있지 않습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the list entry of “my_list” to the child in line 12. */
status = gx_horizontal_list_selected_set(&my_list, 12);

/* If status is GX_SUCCESS, the list entry of “my_list” has been successfully set to 12. */
```

### <a name="see-also"></a>참고 항목

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_widget_get"></a>gx_horizontal_list_selected_widget_get


가로 목록에서 선택된 항목 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_horizontal_list_selected_widget_get(
    GX_horizobntal_LIST *horizontal_list,
    GX_WIDGET **return_list_entry);
```

### <a name="description"></a>Description

이 서비스는 가로 목록에서 선택한 목록 항목을 반환합니다. 가로 목록에 자식 위젯보다 많은 행이 있고 선택된 항목이 뷰에서 스크롤된 경우 목록 내용을 스크롤할 때 자식 위젯이 재사용되므로 API에서 GX_NULL을 반환합니다. gx_horizontal_list_selected_index_get 함수는 선택된 항목이 뷰에서 스크롤된 경우에도 해당 항목의 인덱스를 안정적으로 반환합니다.

### <a name="parameters"></a>매개 변수

- **horizontal_list** 가로 목록 위젯 컨트롤 블록
- **return_list_entry** 반환 목록 항목 위젯의 대상

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 가로 목록 항목을 가져왔습니다.
- **GX_FAILURE**(0x10) 선택한 위젯이 클라이언트 자식보다 많은 행이 있는 목록의 뷰에서 스크롤되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Get the list entry at the current index of horizontal list “my_list”. */
status = gx_horizontal_list_selected_widget_get(&my_list, &current_list_entry);

/* If status is GX_SUCCESS, “current_list_entry” contains a pointer to the currently selected widget. */

    
```

### <a name="see-also"></a>참고 항목

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_total_columns_set"></a>gx_horizontal_list_total_columns_set


목록 열의 총수 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_horizontal_list_total_columns_set(
    GX_HORIZONTAL_LIST *horizontal_list,
    INT count);
```

### <a name="description"></a>Description

이 서비스는 가로 목록에 표시할 열의 총수를 할당합니다.

### <a name="parameters"></a>매개 변수

- **horizontal_list** 가로 목록 위젯 컨트롤 블록
- **count** 표시할 열 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 열 수를 할당했습니다.
- **GX_CALLER_ERROR**(0x10) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 개수 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Tell my list to display 20 total columns. */
status = gx_horizontal_list_total_columns_set(&my_list, 20);

/* If status is GX_SUCCESS, the total colums of “my_list” was successfully set to 20. */
```

### <a name="see-also"></a>참고 항목

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set

## <a name="gx_horizontal_scrollbar_create"></a>gx_horizontal_scrollbar_create


가로 스크롤 막대 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_horizontal_scrollbar_create(
    GX_SCROLLBAR *scrollbar,
    GX_CONST GX_CHAR *name,
    GX_WINDOW *parent,
    GX_SCROLLBAR_APPEARANCE *appearance ULONG style);
```

### <a name="description"></a>Description

이 서비스는 가로 스크롤 막대를 만듭니다. 가로 스크롤 막대의 ID는 미리 정의되어 있으며(창에서 이벤트를 catch하는 방법을 알고 있어야 함) 크기가 자동입니다(부모 창의 클라이언트 너비를 채워야 함). 클라이언트 영역 스크롤 막대를 허용하기로 한 경우 id 및 크기 매개 변수를 사용하여 다른 create 함수를 추가해야 합니다.

### <a name="parameters"></a>매개 변수

- **scrollbar** 스크롤 막대 위젯 제어 블록
- **name** 스크롤 막대의 이름
- **parent** 부모 위젯에 대한 포인터
- **appearance** 모양 구조체는 스크롤 막대의 모양을 정의합니다. 이 값이 GX_NULL이면 스크롤 막대는 gx_system_scroll_appearance_get에서 정의된 기본 스크롤 막대 모양을 사용합니다. GX_SCROLLBAR_APPEARANCE 구조체의 정의는 **부록 I** 를 참조하세요.
- **style** 스크롤 막대 위젯의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 가로 스크롤 막대를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create horizontal scrollbar “my_scrollbar”. */
status = gx_horizontal_scrollbar_create(&my_scrollbar,
    “my_horizontal_scrollbar”, &my_parent, GX_NULL,
    GX_STYLE_SCROLLBAR_END_BUTTONS);

/* If status is GX_SUCCESS the horizontal scrollbar “my_scrollbar” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_icon_button_create"></a>gx_icon_button_create


아이콘 단추 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_icon_button_create(
    GX_ICON_BUTTON *button,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    GX_RESOURCE_ID icon_id,
    ULONG style,
    USHORT icon_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 지정된 아이콘 단추 위젯을 만듭니다.

GX_ICON_BUTTON은 GX_BUTTON에서 파생되며 gx_button API 서비스를 모두 지원합니다.

### <a name="parameters"></a>매개 변수

- **button** 아이콘 단추 컨트롤 블록에 대한 포인터
- **name** 아이콘 단추 위젯의 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **icon_id** 아이콘의 리소스 ID
- **style** 아이콘의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **icon_button_id** 애플리케이션에서 정의된 아이콘 단추 ID
- **size** 아이콘 단추의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 아이콘 단추를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create “my_icon_button”. */
status = gx_icon_button_create(&my_icon_button, “my_icon_button”,
    &my_parent,
    MY_ICON_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_ICON_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS the icon button “my_icon_button” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_button_draw"></a>gx_icon_button_draw


아이콘 단추 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_icon_button_draw(GX_ICON_BUTTON *button);
```

### <a name="description"></a>Description

이 서비스는 아이콘 단추를 그립니다. 일반적으로 캔버스 새로 고침 작업의 일부로 GUIX에서 내부적으로 호출되지만 사용자 지정 그리기 함수를 제공하고 기본 아이콘 단추 그리기를 사용자 지정 그리기 기준으로 호출하려는 애플리케이션에도 노출됩니다.

### <a name="parameters"></a>매개 변수

- **button** 아이콘 단추 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom icon draw function. */
void MyIconButtonDraw(GX_ICON_BUTTON *button)
{
    /* Do the normal drawing first */
    gx_icon_button_draw(button);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_button_pixelmap_set"></a>gx_icon_button_pixelmap_set


아이콘 단추 위젯에 pixelmap 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_icon_button_pixelmap_set(
    GX_ICON_BUTTON *button,
    GX_RESOURCE_ID icon_id);
```

### <a name="description"></a>Description

이 서비스는 아이콘 단추 위젯에 새 pixelmap을 할당합니다.

### <a name="parameters"></a>매개 변수

- **button** 아이콘 단추 컨트롤 블록에 대한 포인터
- **icon_id** pixelmap의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 아이콘 단추 pixelmap을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set pixelmap for “my_icon_button”. */
status = gx_icon_button_pixelmap_set(&my_icon_button,
    GX_PIXELMAP_ID_ICON);

/* If status is GX_SUCCESS, the pixelmap of the icon button “my_icon_button” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_background_draw"></a>gx_icon_background_draw


아이콘 배경 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_icon_background_draw(GX_ICON *icon);
```

### <a name="description"></a>Description

이 서비스는 지정된 아이콘 위젯의 배경을 그립니다. 일반적으로 gx_icon_button_draw 함수에서 내부적으로 호출되지만 사용자 지정 그리기 함수를 작성하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **icon** 아이콘 위젯 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Write a custom icon draw function. */
void MyIconButtonDraw(GX_ICON *icon)
{
    /* Call icon background draw. */
    gx_icon_background_draw(icon);

    /* Add custom drawing here */

    /* Draw child widgets. */
    gx_widget_children_draw(icon);
}
```

### <a name="see-also"></a>참고 항목

- gx_icon_create
- gx_icon_draw
- gx_icon_event_process
- gx_icon_pixelmap_set

## <a name="gx_icon_create"></a>gx_icon_create


만들기 아이콘

### <a name="prototype"></a>프로토타입

```C
UINT gx_icon_create(
    GX_ICON *icon, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID pixelmap_id, 
    ULONG style,
    USHORT icon_id, 
    GX_VALUE x, 
    GX_VALUE y);
```

### <a name="description"></a>Description

이 서비스는 지정된 아이콘 위젯을 만듭니다.

### <a name="parameters"></a>매개 변수

- **icon** 아이콘 제어 블록에 대한 포인터
- **name** 아이콘 위젯의 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **pixelmap_id** pixelmap의 리소스 ID
- **style** 아이콘의 스타일
- **icon_id** 애플리케이션에서 정의된 아이콘 ID
- **x** 시작 x 좌표 위치
- **y** 시작 y 좌표 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 아이콘을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create “my_icon”. */
status = gx_icon_create(&my_icon, “my_icon”, &my_parent,
    MY_PIXELMAP_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_ICON_ID,
    5, 30);

/* If status is GX_SUCCESS the icon “my_icon” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_icon_button_create
- gx_icon_draw
- gx_icon_pixelmap_set

## <a name="gx_icon_draw"></a>gx_icon_draw


아이콘 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_icon_draw(GX_ICON *icon);
```

### <a name="description"></a>Description

이 서비스는 지정된 아이콘 위젯을 그립니다. 일반적으로 캔버스 새로 고침 작업의 일부로 GUIX에서 내부적으로 호출되지만 사용자 지정 그리기 함수를 제공하고 기본 아이콘 그리기를 사용자 지정 그리기 기준으로 호출하려는 애플리케이션에도 노출됩니다.

### <a name="parameters"></a>매개 변수

- **icon** 아이콘 위젯 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom icon drawing function. */

VOID my_icon_draw(GX_MENU *menu)
{
    /* Call default icon draw. */
    gx_icon_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_icon_button_create
- gx_icon_create
- gx_icon_pixelmap_set

## <a name="gx_icon_event_process"></a>gx_icon_event_process

아이콘 위젯 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_icon_event_process(
    GX_ICON *icon, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 GX_ICON 위젯에 전송된 이벤트를 처리합니다.

### <a name="parameters"></a>매개 변수

- **icon** 아이콘 위젯 제어 블록에 대한 포인터
- **event_ptr** GX_EVENT 구조체에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 아이콘 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
switch(event_ptr->gx_event_type)
{
case GX_EVENT_SHOW:
    /* Do default handling. */
    status = gx_icon_event_process(icon, event_ptr);

    /* add your own handling here */
    break;
}
```

### <a name="see-also"></a>참고 항목

- gx_icon_button_create
- gx_icon_create
- gx_icon_pixelmap_set

## <a name="gx_icon_pixelmap_set"></a>gx_icon_pixelmap_set


아이콘의 pixelmap 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_icon_pixelmap_set(
    GX_ICON *icon, 
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id);
```

### <a name="description"></a>Description

이 서비스는 지정된 아이콘 위젯의 pixelmap을 설정합니다.

### <a name="parameters"></a>매개 변수

- **icon** 아이콘 위젯 제어 블록에 대한 포인터
- **normal_id** 정상 상태 리소스 ID
- **selected_id** 선택된 상태 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 아이콘 pixelmap을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set pixelmap for “my_icon”. */
status = gx_icon_pixelmap_set(&my_icon,
    MY_NOT_SELECTED_RESOURCE_ID,
    MY_SELECTED_ID);

/* If status is GX_SUCCESS, the icon “my_icon” has a pixelmap set. */
```

### <a name="see-also"></a>참고 항목

- gx_icon_button_create
- gx_icon_create
- gx_icon_draw

## <a name="gx_image_reader_create"></a>gx_image_reader_create


이미지 판독기 모듈 인스턴스 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_image_reader_create(
    GX_IMAGE_READER *image_reader,
    GX_CONST GX_UBYTE *data, 
    INT data_size,
    GX_UBYTE color_format, 
    GX_UBYTE mode);
```

### <a name="description"></a>Description

이 함수는 런타임 원시 이미지 판독기/디코더를 만듭니다. 현재 jpeg 및 png 원시 이미지 형식만 지원됩니다. 서비스를 사용하려면 GX_SOFTWARE_DECODER_SUPPORT를 정의해야 합니다.

### <a name="parameters"></a>매개 변수

- **image_reader** 이미지 판독기 제어 블록
- **data** 원시 입력 데이터에 대한 포인터
- **data_size** 원시 입력 데이터의 크기
- **color_format** 요청된 출력 색 형식
- **mode** 압축, 디더링, 알파 모드 플래그

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 이미지 판독기를 만들었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 데이터 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_IMAGE_READER my_image_reader;

“color format” could be set to:
    GX_COLOR_FORMAT_32ARGB
    GX_COLOR_FORMAT_24RGB
    GX_COLOR_FORMAT_565RGB
    GX_COLOR_FORMAT_8BIT_PALETTE

/* Create image reader “my_image_reader”. */
status = gx_image_reader_create(&my_image_reader, decoder_data,
    decoder_data_size,
    GX_COLOR_FORMAT_32ARGB,
    GX_IMAGE_READER_MODE_COMPRESS)

/* If status is GX_SUCCESS, “my_image_reader” has been successfully created. */
```

### <a name="see-also"></a>참고 항목

- gx_image_reader_start
- gx_image_reader_palette_set

## <a name="gx_image_reader_palette_set"></a>gx_image_reader_palette_set


이미지 판독기 팔레트 정의

### <a name="prototype"></a>프로토타입

```C
UINT gx_image_reader_palette_set(
    GX_IMAGE_READER *image_reader,
    GX_COLOR *pal,
    UINT palsize);
```

### <a name="description"></a>Description

이 서비스는 이미지 판독기 제어 블록의 색상표를 설정합니다. 서비스를 사용하려면 GX_SOFTWARE_DECODER_SUPPORT를 정의해야 합니다.

### <a name="parameters"></a>매개 변수

- **image_reader** 이미지 판독기 제어 블록
- **pal** 색상표에 대한 포인터
- **palsize** 색상표의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 이미지 판독기 색상표를 설정했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 색상표 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set “my_palette” as the palette of “my_image_reader”. */
status = gx_image_reader_palette_set(&my_image_reader, my_palette,
    my_palette_size);

/* If status is GX_SUCCESS the palette of “my_image_reader” has been set to “my_palette”. */
```

### <a name="see-also"></a>참고 항목

- gx_image_reader_create
- gx_image_reader_start

## <a name="gx_image_reader_start"></a>gx_image_reader_start

압축 풀기 및 변환 프로세스 시작

### <a name="prototype"></a>프로토타입

```C
UINT gx_image_reader_start(
    GX_IMAGE_READER *image_reader, 
    GX_PIXELMAP *outmap);
```

### <a name="description"></a>Description

이 서비스는 원시 이미지를 지정된 색 형식으로 디코딩합니다. 현재 jpeg 및 png 원시 이미지 형식만 지원됩니다. 서비스를 사용하려면 GX_SOFTWARE_DECODER_SUPPORT를 정의해야 합니다.

### <a name="parameters"></a>매개 변수

- **image_reader** 이미지 판독기 제어 블록
- **pixelmap** 출력 pixelmap

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 이미지를 디코드했습니다.
- **GX_SYSTEM_MEMORY_ERROR**(0x30) 메모리 할당자가 정의되지 않았거나 메모리를 할당하지 못했습니다.
- **GX_NOT_SUPPORTED**(0x28) 입력 이미지 형식 또는 출력 색 형식이 지원되지 않습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_IMAGE_READER my_image_reader;
GX_PIXELMAP output_map;

/* Create my_image_reader here. */

/* Decoding a raw image according to the settings of “my_image_reader”. */
status = gx_image_reader_start(&my_image_reader, output_map)

/* If status is GX_SUCCESS “output_map” have been loaded with the requested pixelmap. */
```

### <a name="see-also"></a>참고 항목

- gx_image_reader_create
- gx_image_reader_palette_set

## <a name="gx_line_chart_axis_draw"></a>gx_line_chart_axis_draw


꺾은선형 차트 x,y 축 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_line_chart_axis_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Description

이 서비스는 꺾은선형 차트의 x,y 축을 그립니다. 축 색 및 선 두께 매개 변수는 꺾은선형 차트 정보 구조체에서 검색됩니다.

일반적으로 gx_line_chart_draw 함수에서 내부적으로 호출되지만 사용자 지정 그리기 함수를 작성하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **chart** 꺾은선형 차트 제어 블록

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default window draw. */
    gx_window_draw((GX_WINDOW *)chart);

    /* Draw the line chart axis. */
    gx_line_chart_axis_draw(&chart->gx_line_chart_info);

    /* Draw the data line */
    gx_line_chart_data_draw(&chart->gx_line_chart_info);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_create"></a>gx_line_chart_create


GX_LINE_CHART 위젯 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_line_chart_create(
    GX_LINE_CHART *chart,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_LINE_CHART_INFO *info,
    ULONG style,
    USHORT chart_id, GX_RECTANGLE *size)
```

### <a name="description"></a>Description

이 서비스는 꺾은선형 차트 창을 만듭니다. 차트 그리기 매개 변수와 차트 데이터는 GX_LINE_CHART_INFO 구조체를 통해 전달됩니다.

GX_LINE_CHART는 GX_WINDOW를 기반으로 하며 모든 GX_WINDOW API를 지원합니다.

### <a name="parameters"></a>매개 변수

- **chart** GX_LINE_CHART 제어 블록에 대한 포인터
- **name** 꺾은선형 차트 이름(선택 사항)
- **parent** 부모 위젯 또는 GX_NULL
- **info** 꺾은선형 차트 그리기 매개 변수를 정의하는 구조체. **부록 I** 에는 GX_LINE_CHART_INFO 구조체의 정의가 나와 있습니다.
- **style** 위젯 스타일 플래그
- **chart_id** 차트 논리적 ID 값
- **size** 차트 창 경계 사각형

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 꺾은선형 차트를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create a line chart */
GX_LINE_CHART chart;
GX_RECTANGLE chart_size;
GX_LINE_CHART_INFO gx_chart_info;
GX_WINDOW_ROOT *root_window;

chart_size = root_window->gx_widget_size;

/* Initialize params for the GUIX base chart. */
gx_chart_info.gx_line_chart_min_val = DATA_MIN_VAL;
gx_chart_info.gx_line_chart_max_val = DATA_MAX_VAL;
gx_chart_info.gx_line_chart_max_data_count = MAX_DATA_COUNT;
gx_chart_info.gx_line_chart_active_data_count = 0;
gx_chart_info.gx_line_chart_axis_line_width = AXIS_LINE_WIDTH;
gx_chart_info.gx_line_chart_data_line_width = DATA_LINE_WIDTH;
gx_chart_info.gx_line_chart_data = chart_data;
gx_chart_info.gx_line_chart_line_color = GX_COLOR_ID_DATA_LINE;
gx_chart_info.gx_line_chart_axis_color = GX_COLOR_ID_AXIS_LINE;

/* Leave room for labels on bottom and right. */
gx_chart_info.gx_line_chart_left_margin = 0;
gx_chart_info.gx_line_chart_top_margin = 0;
gx_chart_info.gx_line_chart_right_margin = 80;
gx_chart_info.gx_line_chart_bottom_margin = 32;

status = gx_line_chart_create(&chart, “Line Chart”, root_window,
    &gx_chart_info, GX_STYLE_NONE, &chart_size);

/* If status is GX_SUCCESS, the “chart” has been successfully created. */
```

### <a name="see-also"></a>참고 항목

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_data_draw"></a>gx_line_chart_data_draw


꺾은선형 차트 데이터 선 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_line_chart_data_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Description

이 서비스는 꺾은선형 차트 데이터 선을 그립니다. 선 색 및 선 두께 매개 변수는 꺾은선형 차트 정보 구조체에서 검색됩니다.

일반적으로 gx_line_chart_draw 함수에서 내부적으로 호출되지만 사용자 지정 그리기 함수를 작성하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **chart** 꺾은선형 차트 제어 블록

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default window draw. */
    gx_window_draw((GX_WINDOW *)chart);

    /* Draw the line chart axis. */
    gx_line_chart_axis_draw(chart);

    /* Draw the data line. */
    gx_line_chart_data_draw(chart);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_line_chart_create
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_draw"></a>gx_line_chart_draw


꺾은선형 차트 그리기

### <a name="prototype"></a>프로토타입

```C
UINT gx_line_chart_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Description

차트 축과 데이터 선을 그리는 기본 꺾은선형 차트 그리기 함수입니다. 애플리케이션은 일반적으로 기준 꺾은선형 차트 위젯을 통해 그린 차트 축 및 데이터 선에 눈금 표시, 배율 또는 기타 정보와 같은 항목을 추가하기 위해 기본 그리기를 대체할 사용자 지정 그리기 함수를 제공합니다.

### <a name="parameters"></a>매개 변수

- **chart** 꺾은선형 차트 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default line chart draw. */
    gx_line_chart_draw(chart);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_line_chart_create
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_update"></a>gx_line_chart_update


꺾은선형 차트 데이터 선 업데이트

### <a name="prototype"></a>프로토타입

```C
UINT gx_line_chart_update(
    GX_LINE_CHART *chart, 
    INT *data,
    INT data_count)
```

### <a name="description"></a>Description

이 서비스는 꺾은선형 차트 창에 표시되는 데이터 배열을 업데이트하고 창을 강제로 다시 그립니다.

### <a name="parameters"></a>매개 변수

- **chart** 꺾은선형 차트 제어 블록
- **data** 표시할 데이터 배열
- **data_count** 데이터 배열의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트 단추를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
INT chart_data[100];
GX_LINE_CHART chart;

/* Update the data array associated with “chart”. */
status = gx_line_chart_update(&chart, chart_data, 100);

/* If status is GX_SUCCESS, the line chart data has been updated. */
```

### <a name="see-also"></a>참고 항목

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_y_scale_calculate"></a>gx_line_chart_y_scale_calculate


고정 소수점 y축 스케일링 값 계산

### <a name="prototype"></a>프로토타입

```C
UINT gx_line_chart_y_scale_calculate(
    GX_LINE_CHART *chart,
    INT *return_val);
```

### <a name="description"></a>Description

이 서비스는 차트 Y축에 데이터 값을 표시하는 데 사용되는 고정 소수점 스케일링 값을 계산합니다. chart_info 매개 변수와 차트 경계 사각형을 사용하여 스케일링 값을 계산합니다.

### <a name="parameters"></a>매개 변수

- **chart** 꺾은선형 차트 제어 블록
- **return_val** 고정 소수점 반환 값을 저장할 값의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) y 스케일링 값을 계산했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_LINE_CHART chart;
INT y_scale;

/* Caluclate y scale value of “chart”. */
status = gx_line_chart_y_scale_calculate(&chart, &y_scale);

/* If status is GX_SUCCESS, y scale value of “chart” has been calculated. */
```

### <a name="see-also"></a>참고 항목

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update

## <a name="gx_menu_create"></a>gx_menu_create


메뉴 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_menu_create(
    GX_MENU *menu,GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    GX_RESOURCE_ID fill_id, 
    ULONG style, 
    USHORT menu_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 지정된 대로 메뉴를 만들고 제공된 부모 위젯과 메뉴를 연결합니다. 모든 형식의 위젯을 자식 메뉴 항목으로 허용합니다. 위젯을 자식 메뉴 항목으로 삽입하려면 **gx_menu_insert** 를 호출합니다.

GX_MENU는 GX_PIXELMAP_PROMPT에서 파생되며 gx_pixelmap_prompt API 서비스를 모두 지원합니다.

### <a name="parameters"></a>매개 변수

- **menu** 메뉴 제어 블록에 대한 포인터
- **name** 메뉴의 이름
- **parent** 부모 위젯에 대한 포인터
- **text_id** 텍스트의 리소스 ID
- **fill_id** 채우기의 리소스 ID
- **style** 위젯의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **menu_id** 애플리케이션에서 정의된 메뉴 ID
- **size** 메뉴의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 메뉴를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_MENU my_menu;

/* Create “my_menu”. */
status = gx_menu_create(&my_menu, “my_menu”, parent, MY_TEXT_ID,
    MY_FILL_ID, GX_STYLE_ENABLED, MY_MENU_ID,
    &size);

/* If status is GX_SUCCESS, the menu was successfully created. */
```

### <a name="see-also"></a>참고 항목

- gx_accordion_meu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_draw"></a>gx_menu_draw


메뉴 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_menu_draw(GX_MENU *menu);
```

### <a name="description"></a>Description

이 서비스는 지정된 메뉴를 그립니다. 일반적으로 GUIX 캔버스 새로 고침 메커니즘을 통해 내부적으로 호출되지만 사용자 지정 메뉴 위젯용 사용자 지정 그리기 함수를 구현하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **menu** 메뉴 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom menu drawing function. */

VOID my_menu_draw(GX_MENU *menu)
{
    /* Call default menu draw. */
    gx_menu_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_event_process"></a>gx_menu_event_process

메뉴 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_menu_event_process(GX_MENU *menu, GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 메뉴에 대한 이벤트를 처리합니다. 사용자 지정 메뉴 이벤트 처리 함수에서 기본 이벤트 처리기로 호출되어야 합니다.

### <a name="parameters"></a>매개 변수

- **menu** 메뉴 제어 블록에 대한 포인터
- **event_ptr** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 메뉴 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x23) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic menu event processing as part of custom event processing function. */

UINT custom_menu_event_process(GX_MENU *menu, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */

        /* Call default event process if this is a system event such as GX_EVENT_SHOW. */
        status = gx_menu_event_process(menu, event);
        break;

    default:
        /* Pass all other events to the default menu
           event processing */
        status = gx_menu_event_process(menu, event);
        break;
    }
    return status;
}

```

### <a name="see-also"></a>참고 항목

- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_insert"></a>gx_menu_insert


새 항목 삽입

### <a name="prototype"></a>프로토타입

```C
UINT gx_menu_insert(
    GX_MENU *menu, 
    GX_WIDGET *insert);
```

### <a name="description"></a>Description

이 서비스는 메뉴에 새 항목을 삽입합니다.

### <a name="parameters"></a>매개 변수

- **menu** 메뉴 제어 블록에 대한 포인터
- **widget** 삽입할 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 메뉴에 새 항목을 삽입했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Insert new item “my_widget” to the menu “my_menu”. */
status = gx_menu_insert(&my_menu, &my_widget);

/* If status is GX_SUCCESS the new item “my_widget” has been inserted to the menu “my_menu”. */
```

### <a name="see-also"></a>참고 항목

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_remove"></a>gx_menu_remove


항목 제거

### <a name="prototype"></a>프로토타입

```C
UINT gx_menu_remvoe(
    GX_MENU *menu, 
    GX_WIDGET *widget);
```

### <a name="description"></a>Description

이 서비스는 메뉴에서 항목을 제거합니다.

### <a name="parameters"></a>매개 변수

- **menu** 메뉴 제어 블록에 대한 포인터
- **widget** 제거할 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 메뉴 항목을 제거했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Remove item “my_widget” from menu “my_menu” */
status = gx_menu_remove(&my_menu, &my_widget);

/* If status is GX_SUCCESS the item “my_widget” has been removed from menu “my_menu”. */
```

### <a name="see-also"></a>참고 항목

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_text_draw"></a>gx_menu_text_draw


메뉴 텍스트 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_menu_text_draw(GX_MENU *menu);
```

### <a name="description"></a>Description

이 서비스는 메뉴의 텍스트를 그립니다. 일반적으로 GUIX 캔버스 새로 고침 메커니즘을 통해 내부적으로 호출되지만 사용자 지정 메뉴 위젯용 사용자 지정 그리기 함수를 구현하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **menu** 메뉴 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom menu drawing function. */

VOID my_menu_draw(GX_MENU *menu)
{
    /* Call default menu background draw. */
    gx_pixelmap_prompt_background_draw(
                            (GX_PIXELMAP_PROMPT *)menu);

    /* Draw menu text. */
    gx_menu_text_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_offset_set

## <a name="gx_menu_text_offset_set"></a>gx_menu_text_offset_set


메뉴 텍스트 그리기 오프셋 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_menu_text_offset_set(
    GX_MENU *menu, 
    GX_VALUE x_offset,
    GX_VALUE y_offset);
```

### <a name="description"></a>Description

이 서비스는 메뉴 텍스트의 x,y 표시 오프셋을 설정합니다.

### <a name="parameters"></a>매개 변수

- **menu** 메뉴 제어 블록에 대한 포인터
- **x_offset** 오프셋의 X 좌표
- **y_offset** 오프셋의 Y 좌표

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 메뉴 텍스트 그리기 오프셋을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set text draw offset of menu “my_menu” to (20, 10). */
status = gx_menu_text_offset_set(&my_menu, 20, 10);

/* If status is GX_SUCCESS the text draw offset of menu “my_menu” has been set to (20, 10). */
```

### <a name="see-also"></a>참고 항목

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw

## <a name="gx_multi_line_text_button_create"></a>gx_multi_line_text_button_create


여러 줄 텍스트 단추 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_button_create(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    ULONG style,
    USHORT text_button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 단추 위젯을 만듭니다. 여러 줄 텍스트 단추를 클릭하면 단추 텍스트가 1~n줄에 표시됩니다. 최대 줄 수는 GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES 상수로 정의되며 기본값은 4입니다. 줄 바꿈은 여러 줄 텍스트 단추에 할당된 텍스트 문자열 내에서 캐리지 리턴 및/또는 캐리지 리턴 + 줄 바꿈 쌍으로 설정됩니다.

GX_MULTI_LINE_TEXT_BUTTON은 GX_TEXT_BUTTON에서 파생되며 gx_text_button API 서비스를 모두 지원합니다.

### <a name="parameters"></a>매개 변수

- **text_button** 텍스트 단추 컨트롤 블록에 대한 포인터
- **name** 텍스트 단추의 논리적 이름
- **parent** 단추의 부모 위젯에 대한 포인터
- **text_id** 텍스트의 리소스 ID
- **style** 텍스트 단추 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **text_button_id** 애플리케이션에서 정의된 텍스트 단추 ID
- **size** 단추의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 단추를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create multi-line text button “my_text_button”. */
status = gx_multi_line_text_button_create(&my_text_button, "my text button",
    &my_parent_window, MY_TEXT_RESOURCE_ID,
    GX_STYLE_BUTTON_TOGGLE, MY_TEXT_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS, the multi-line text button “my_text_button” was created. */
```

### <a name="see-also"></a>참고 항목

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_draw"></a>gx_multi_line_text_button_draw


여러 줄 텍스트 단추 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_multi_line_text_button_draw(GX_MULTI_LINE_TEXT_BUTTON *button);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 단추를 그립니다. 일반적으로 캔버스 새로 고침 작업의 일부로 GUIX에서 내부적으로 호출되지만 사용자 지정 그리기 함수를 제공하고 기본 여러 줄 텍스트 단추 그리기를 사용자 지정 그리기 기준으로 호출하려는 애플리케이션에도 노출됩니다.

### <a name="parameters"></a>매개 변수

- **button** 텍스트 단추 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Draw the text button “my_text_button”. */
void MyButtonDraw(GX_MULTI_LINE_TEXT_BUTTON *button)
{
    /* Do the normal drawing first */
    gx_multi_line_text_button_draw(&my_text_button);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_event_process"></a>gx_multi_line_text_button_event_process


여러 줄 텍스트 단추에 대한 기본 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_button_event_process(
    GX_MULTI_LINE_TEXT_BUTTON *button,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 단추 위젯에 대한 기본 이벤트 처리 함수입니다. 텍스트 단추 위젯에 대한 사용자 지정 이벤트 처리를 제공하려는 애플리케이션에서 함수에 액세스할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **button** 텍스트 단추 컨트롤 블록에 대한 포인터
- **event_ptr** 처리할 이벤트

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
UINT MyEventHandler(GX_MULTI_LINE_TEXT_BUTTON *button,
    GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case GX_EVENT_SHOW:
        gx_multi_line_text_button_event_process(button, event_ptr);
        /* add custom actions here */
        break;
    default:
        gx_multi_line_text_button_event_process(button, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>참고 항목

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_draw"></a>gx_multi_line_text_button_text_draw


그리기 지원 함수

### <a name="prototype"></a>프로토타입

```C
VOID gx_multi_line_text_button_text_draw(GX_MULTI_LINE_TEXT_BUTTON *text_button);
```

### <a name="description"></a>Description

이 지원 함수는 여러 줄 텍스트 단추의 텍스트 부분을 그립니다. gx_multi_line_text_button_draw()에서 내부적으로 호출되며, 사용자 지정 여러 줄 텍스트 단추 그리기 함수를 정의하는 애플리케이션의 편의를 위해 별도의 API로 제공됩니다. 단추 배경 그리기를 사용자 지정하려는 애플리케이션은 사용자 지정 그리기 함수를 제공하고 사용자 지정 그리기의 일부로 multi_line_text_button_text_draw 서비스를 호출하여 배경에 단추 텍스트를 그릴 수 있습니다.

### <a name="parameters"></a>매개 변수

- **text_button** 텍스트 단추 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Define a custom drawing function */
VOID my_button_draw(GX_MULTI_LINE_TEXT_BUTTON *button)
{
    /* insert code here to draw button background */

    /* call support function to do text drawing */
    gx_multi_line_text_button_text_draw();

    /* draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) button);
}
```

### <a name="see-also"></a>참고 항목

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set


## <a name="gx_multi_line_text_button_text_id_set"></a>gx_multi_line_text_button_text_id_set


텍스트 단추에 텍스트 리소스 ID 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_button_text_id_set(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    RESOURCE_ID string_id)
```

### <a name="description"></a>Description

이 서비스는 텍스트 단추에 지정된 문자열 리소스 ID를 설정합니다. 문자열에는 단추 영역 내의 여러 줄에 텍스트를 표시하는 역할을 하는 줄 바꿈 문자가 포함될 수 있습니다.

### <a name="parameters"></a>매개 변수

- **text_button** 텍스트 단추 컨트롤 블록에 대한 포인터
- **string_id** 문자열의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트 단추에 문자열 리소스 ID를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the string ID ”MY_STRING_ID” to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_id_set(
    &my_text_button, MY_STRING_ID);

/* If status is GX_SUCCESS, the string ID MY_STRING_ID was set to “my_text_button”. */
```

### <a name="see-also"></a>참고 항목

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_set"></a>gx_multi_line_text_button_text_set


텍스트 단추에 텍스트 할당(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_mult_line_text_button_text_set(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_CHAR *text);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_multi_line_text_button_text_set_ext()로 대체되었습니다.

이 서비스는 텍스트 단추에 지정된 문자열을 할당합니다. GX_STYLE_TEXT_COPY 스타일을 사용하여 생성된 text_button 위젯은 할당된 텍스트 문자열의 프라이빗 복사본을 만들기 때문에 이 서비스를 요청하기 전에 gx_system_memory_allocate_set API를 한 번 호출해야 합니다. GX_STYLE_TEXT_COPY가 활성 상태가 아니면 위젯이 들어오는 문자열의 프라이빗 복사본을 만들지 않으므로 문자열을 정적이나 전역으로 할당해야 합니다. 즉, 자동 또는 임시 변수를 사용할 수 없습니다.

### <a name="parameters"></a>매개 변수

- **text_button** 텍스트 단추 컨트롤 블록에 대한 포인터
- **text** NULL로 종료된 문자열에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 단추에 텍스트를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_MEMORY_ERROR**(0x30) 메모리 할당자가 정의되어 있지 않습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
static GX_CHAR text[] = “myrstring”;

/* Set text to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_set(&my_text_button, text);

/* If status is GX_SUCCESS, the text of “my_text_button” was set. */
```

### <a name="see-also"></a>참고 항목

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_set_ext"></a>gx_multi_line_text_button_text_set_ext


텍스트 단추에 텍스트 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_mult_line_text_button_text_set_ext(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_STRING *string)
```

### <a name="description"></a>Description

이 서비스는 텍스트 단추에 지정된 문자열을 할당합니다. GX_STYLE_TEXT_COPY 스타일을 사용하여 생성된 text_button 위젯은 할당된 텍스트 문자열의 프라이빗 복사본을 만들기 때문에 이 서비스를 요청하기 전에 gx_system_memory_allocate_set API를 한 번 호출해야 합니다. GX_STYLE_TEXT_COPY가 활성 상태가 아니면 위젯이 들어오는 문자열의 프라이빗 복사본을 만들지 않으므로 문자열을 정적이나 전역으로 할당해야 합니다. 즉, 자동 또는 임시 변수를 사용할 수 없습니다.

### <a name="parameters"></a>매개 변수

- **text_button** 텍스트 단추 컨트롤 블록에 대한 포인터
- **string** GX_STRING 변수에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 단추에 텍스트를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_MEMORY_ERROR**(0x30) 메모리 할당자가 정의되어 있지 않습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
static GX_CHAR text[] = “myrstring”;
GX_STRING string;

string.gx_string_ptr = text;
string.gx_string_length = strlen(text);

/* Set text to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_set_ext(&my_text_button, string);

/* If status is GX_SUCCESS, the text of “my_text_button” was set. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_input_backspace"></a>gx_multi_line_text_input_backspace


여러 줄 텍스트 입력 커서 위치 앞의 문자 삭제

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_backspace(
    GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 커서 위치 앞의 문자를 삭제합니다. 백스페이스 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 입력에서 백스페이스 키로 삭제했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x23) 위젯이 잘못되었습니다.
- **GX_FAILURE**(0x10) 글꼴이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Delete a character before the cursor of “my_text_input”. */
status = gx_multi_line_text_input_backspace(&my_text_input);

/* If status is GX_SUCCESS the character before the cursor has been deleted. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_buffer_clear"></a>gx_multi_line_text_input_buffer_clear


텍스트 입력 버퍼에서 모든 문자 삭제

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_buffer_clear(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 버퍼에서 모든 문자를 삭제합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 입력 버퍼를 지웠습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* clear input buffer of “my_text_input”. */
status = gx_multi_line_text_input_clear(&my_text_input);

/* If status is GX_SUCCESS the text input widget has emptied its input buffer. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_buffer_get"></a>gx_multi_line_text_input_buffer_get


텍스트 입력 위젯의 버퍼 정보 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_buffer_get(
    GX_MULTI_LINE_TEXT_INPUT *text_input, 
    GX_CHAR **buffer_address,
    UINT *content_size, 
    UINT *buffer_size);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 위젯의 버퍼 정보를 검색합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록
- **buffer_address** 입력 버퍼의 주소
- **content_size** 입력 데이터의 바이트 수
- **buffer_size** 입력 버퍼의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트를 가져왔습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CHAR *buffer_address;
UINT context_size;
UINT buffer_size;

/* Retrieves buffer information of “my_text_input” widget. */
status = gx_multi_line_text_input_buffer_get(&my_text_input,
    &buffer_address, &string_size,
    &buffer_size);

/* If status is GX_SUCCESS the value of buffer_address, string_size and buffer_size has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_char_insert"></a>gx_multi_line_text_input_char_insert


현재 여러 줄 텍스트 입력 커서 위치에 문자열 삽입(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_char_insert(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_UBYTE *insert_str,
    UINT insert_size);
```

### <a name="description"></a>Description

이 API는 사용되지 않으며 gx_multi_line_text_input_char_insert_ext()로 대체되었습니다.

이 서비스는 여러 줄 텍스트 입력 문자열 버퍼의 현재 커서 위치에 문자열을 삽입합니다. 특정 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록
- **insert_str** 삽입할 UTF-8 형식 문자열
- **insert_size** 삽입할 바이트 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 문자열을 삽입했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 문자열 크기가 잘못되었습니다.
- **GX_FAILURE**(0x10) 글꼴이 잘못되었거나 버퍼 크기가 부족합니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Insert characters at current cursor position. */
GX_CHAR insert_text[10] = “insert”;
status = gx_multi_line_text_input_char_insert(&my_text_input,
    insert_text,
    GX_STRLEN(insert_text));

/* If status is GX_SUCCESS the multi line text input widget has successfully insert the string. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_char_insert_ext

## <a name="gx_multi_line_text_input_char_insert_ext"></a>gx_multi_line_text_input_char_insert_ext


현재 여러 줄 텍스트 입력 커서 위치에 문자열 삽입(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_char_insert_ext(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 문자열 버퍼의 현재 커서 위치에 문자열을 삽입합니다. 특정 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록
- **문자열** 삽입할 UTF-8로 인코딩된 문자열

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 문자열을 삽입했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 문자열 크기가 잘못되었습니다.
- **GX_FAILURE**(0x10) 글꼴이 잘못되었거나 버퍼 크기가 부족합니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Insert characters at current cursor position. */
GX_CHAR insert_text[10] = “insert”;
GX_STRING string;

string.gx_string_ptr = insert_text;
string.gx_string_length = strlen(insert_text);

status = gx_multi_line_text_input_char_insert_ext(&my_text_input, &string);

/* If status is GX_SUCCESS the multi line text input widget has successfully inserted the string. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_create"></a>gx_multi_line_text_input_create


여러 줄 텍스트 입력 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_create(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *name, GX_WINDOW *parent,
    GX_CHAR *input_buffer, UINT buffer_size,
    ULONG style, USHORT text_input_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 위젯을 만듭니다.

GX_MULTI_LINE_TEXT_INPUT은 GX_MULTI_LINE_TEXT_VIEW에서 파생되며 gx_multi_line_text_view 서비스를 모두 지원합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록
- **name** 텍스트 입력 위젯의 이름
- **parent** 부모 위젯에 대한 포인터
- **input_buffer** 텍스트 입력 버퍼에 대한 포인터
- **buffer_size** 텍스트 입력 버퍼의 크기(바이트)
- **style** 텍스트 입력 위젯의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **text_input_id** 애플리케이션에서 정의된 텍스트 입력 ID
- **size** 텍스트 입력 위젯의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 입력을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_WIDGET**(0x12) 부모 위젯이 잘못되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_MULTI_LINE_TEXT_INPUT my_text_input;
GX_CHAR my_buffer[100];
GX_RECTANGLE size;

/* Define widget size. */
gx_utility_rectangle_define(&size, 10, 10, 100, 200);

/* Create multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_create(&my_text_input,
    “my_text_input”, &my_parent,
    my_buffer, 100, GX_STYLE_BORDER_RAISED,
    MY_TEXT_INPUT_ID, &size);

/* If status is GX_SUCCESS, the text input “my_text_input” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_cursor_pos_get"></a>gx_multi_line_text_input_cursor_pos_get


여러 줄 텍스트 입력 커서 위치 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_cursor_pos_get(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_POINT cursor_pos);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 커서 위치를 검색합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록
- **cursor_pos** 검색된 커서 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 커서 위치를 검색했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Retrieve the cursor position of “my_text_input”. */
GX_POINT cursor_pos;
status = gx_multi_line_text_input_cursor_pos_get(&my_text_input,
    &cursor_pos);

/* If status is GX_SUCCESS the cursor position has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_delete"></a>gx_multi_line_text_input_delete


여러 줄 텍스트 입력 커서 위치 뒤의 문자 삭제

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_delete(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 커서 위치 뒤의 문자를 삭제합니다. delete 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 커서 뒤의 문자를 삭제했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_FAILURE**(0x10) 글꼴이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Delete the character after the cursor of “my_text_input”. */
status = gx_multi_line_text_input_delete(&my_text_input);

/* If status is GX_SUCCESS the character after the cursor has been deleted. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_down_arrow"></a>gx_multi_line_text_input_down_arrow


여러 줄 텍스트 입력 커서를 다음 줄로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_down_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 위젯 커서를 다음 줄로 이동합니다. 아래쪽 화살표 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트 입력 커서를 다음 줄로 이동했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_FAILURE**(0x10) 글꼴 또는 줄 높이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move input cursor to the next line. */
status = gx_multi_line_text_input_down_arrow(&my_text_input);

/* If status is GX_SUCCESS, text text input cursor has been moved to the next line. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_end"></a>gx_multi_line_text_input_end


여러 줄 텍스트 입력 커서를 현재 줄의 끝으로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_end(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 위젯 커서를 현재 문자열 줄의 끝으로 이동합니다. end 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트 입력 커서를 현재 줄의 끝으로 이동했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move input cursor to the end of current line. */
status = gx_multi_line_text_input_end(&my_text_input);

/* If status is GX_SUCCESS, the multi line text input cursor has been moved to the end of the current line. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_event_process"></a>gx_multi_line_text_input_event_process


여러 줄 텍스트 입력에 대한 기본 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_event_process(
    GX_MULTI_LINE_TEXT_INPUT *input,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 위젯에 대한 기본 이벤트 처리 함수입니다. 여러 줄 텍스트 입력 위젯에 대한 사용자 지정 이벤트 처리를 제공하려는 애플리케이션에서 함수에 액세스할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **button** 여러 줄 텍스트 입력 컨트롤 블록에 대한 포인터
- **event_ptr** 처리할 이벤트

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 부모 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
UINT MyEventHandler(GX_MULTI_LINE_TEXT_INPUT *input,
    GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;
    default:
        /* pass all other events to the generic multi line text
            input event processing */
        gx_multi_line_text_input_event_process(input, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_fill_color_set"></a>gx_multi_line_text_input_fill_color_set


여러 줄 텍스트 입력 배경색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_fill_color_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_fill_color_id,
    GX_RESOURCE_ID selected_fill_color_id,
    GX_RESOURCE_ID disabled_fill_color_id,
    GX_RESOURCE_ID readonly_fill_color_id);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 위젯의 채우기 색을 할당합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록
- **normal_fill_color_id** 정상 상태에서 사용되는 표준 채우기 색의 리소스 ID
- **selected_fill_color_id** 위젯에 포커스가 있는 경우에 사용되는 선택된 채우기 색의 리소스 ID
- **disabled_fill_color_id** GX_STYLE_ENABLED가 활성 상태가 아닌 경우에 사용되는, 사용할 수 없는 채우기 색의 리소스 ID
- **readonly_fill_color_id** GX_STYLE_ENABLED와 GX_STYLE_INPUT_READONLY가 모두 활성 상태일 때 사용되는 읽기 전용 채우기 색의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 입력의 색을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set fill colors for the multi-line text input widget “my_text_input”. */

status = gx_multi_line_text_input_fill_color_set(&my_text_input,
    GX_COLOR_ID_NORMAL_FILL,
    GX_COLOR_ID_SELECTED_FILL,
    GX_COLOR_ID_DISABLED_FILL,
    GX_COLOR_ID_READONLY_FILL);

/* If status is GX_SUCCESS, the fill color of “my_text_input” has been successfully set. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_home"></a>gx_multi_line_text_input_home


텍스트 입력 커서를 현재 줄의 시작으로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_home(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 커서 위치를 현재 줄의 시작으로 이동합니다. home 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 커서를 현재 줄의 시작으로 이동했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move cursor to the start of the current line. */
status = gx_multi_line_text_input_home(&my_text_input);

/* If status is GX_SUCCESS the cursor has been moved to the start of the current line. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_left_arrow"></a>gx_multi_line_text_input_left_arrow


여러 줄 텍스트 입력 커서를 한 문자 왼쪽으로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_left_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 커서를 한 문자 왼쪽으로 이동합니다. 왼쪽 화살표 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 커서를 왼쪽으로 이동했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_FAILURE**(0x10) 글꼴이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move the cursor one character to the left. */
status = gx_multi_line_text_input_left_arrow(&my_text_input);

/* If status is GX_SUCCESS the multi line text input cursor has been moved one character to the left. */

```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_right_arrow"></a>gx_multi_line_text_input_right_arrow


여러 줄 텍스트 입력 커서를 한 문자 오른쪽으로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_right_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 커서를 한 문자 오른쪽으로 이동합니다. 오른쪽 화살표 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 커서를 오른쪽으로 이동했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move cursor one character to the right. */
status = gx_multi_line_text_input_right_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the right. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_add"></a>gx_multi_line_text_input_style_add


여러 줄 텍스트 입력 스타일 추가

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_style_add(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    ULONG style);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 위젯에 스타일을 추가합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록
- **style** 추가할 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 입력 스타일을 추가했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Add style GX_STYTLE_CURSOR_ALWAYS to multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_add(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS the style GX_STYLE_CURSOR_ALWAYS has been successfully added. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_remove"></a>gx_multi_line_text_input_style_remove


스타일 제거

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_remove(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    ULONG style);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 위젯에서 지정된 스타일을 제거합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록
- **style** 제거할 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 입력을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Remove style GX_STYLE_CURSOR_ALWAYS from text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_remove(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS, the style GX_STYLE_CURSOR_ALWAYS has been successfully removed. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_set"></a>gx_multi_line_text_input_style_set

여러 줄 텍스트 입력 스타일 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_style_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 위젯의 스타일을 설정합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록
- **style** 설정할 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 입력 스타일을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set style GX_STYLE_CURSOR_ALWAYS for text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_set(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS the text input style has been set */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_color_set"></a>gx_multi_line_text_input_text_color_set


여러 줄 텍스트 입력 텍스트 색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_text_color_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id,
    GX_RESOURCE_ID readonly_text_color_id);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 위젯의 텍스트 색을 할당합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 위젯 제어 블록
- **normal_fill_color_id** 정상 상태에서 사용되는 표준 텍스트 색의 리소스 ID
- **selected_text_color_id** 위젯에 포커스가 있는 경우에 사용되는 선택된 텍스트 색의 리소스 ID
- **disabled_text_color_id** GX_STYLE_ENABLED가 활성 상태가 아닌 경우에 사용되는, 사용할 수 없는 텍스트 색의 리소스 ID
- **readonly_text_color_id** GX_STYLE_ENABLED와 GX_STYLE_TEXT_INPUT_READONLY가 모두 활성 상태일 때 사용되는 읽기 전용 텍스트 색의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 입력의 색을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set text colors for the multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_text_color_set(&my_text_input,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT,
    GX_COLOR_ID_READONLY_TEXT);

/* If status is GX_SUCCESS, the fill colors of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_select"></a>gx_multi_line_text_input_text_select


텍스트 선택

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_text_select(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    UINT start_index, UINT end_index);
```

### <a name="description"></a>Description

이 서비스는 지정된 시작 표시 및 끝 표시 인덱스를 사용하여 여러 줄 텍스트 입력 텍스트를 선택하고 선택된 채우기 및 텍스트 색을 사용하여 선택한 텍스트를 강조 표시합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 제어 블록에 대한 포인터
- **start_index** 선택한 첫 번째 문자의 인덱스
- **end_index** 선택한 마지막 문자의 인덱스

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 입력 텍스트를 선택했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 인덱스 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Select text between index [0, 9]. */
status = gx_multi_line_text_input_text_select(&my_text_input,
    0,9);

/* If status is GX_SUCCESS, the text between 
    index [0, 9] “my_text_input” was selected. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_set"></a>gx_multi_line_text_input_text_set


텍스트 입력에 텍스트 할당(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_mult_line_text_input_text_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CHAR *text);
```

### <a name="description"></a>Description

이 API는 사용되지 않으며 gx_multi_line_text_input_text_set_ext()로 대체되었습니다.

이 서비스는 여러 줄 텍스트 입력에 지정된 문자열을 할당합니다. multi_line_text_input 위젯의 입력 버퍼 크기가 문자열 길이 보다 작으면 문자열이 잘립니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 제어 블록에 대한 포인터
- **text** NULL로 종료된 문자열에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 입력에 텍스트를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the string “my string” to the text button “my_text_input”. */
status = gx_multi_line_text_input_text_set(&my_text_input,
    “myrstring”);

/* If status is GX_SUCCESS, the content of “my_text_input” bas been reset. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_text_set_ext

## <a name="gx_multi_line_text_input_text_set_ext"></a>gx_multi_line_text_input_text_set_ext


텍스트 입력에 텍스트 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_mult_line_text_input_text_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력에 지정된 문자열을 할당합니다. multi_line_text_input 위젯의 입력 버퍼 크기가 문자열 길이 보다 작으면 문자열이 잘립니다.

### <a name="parameters"></a>매개 변수

- **text_input** 여러 줄 텍스트 입력 제어 블록에 대한 포인터
- **string** 할당할 GX_STRING에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 입력에 텍스트를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the string “my string” to the text button “my_text_input”. */
GX_STRING string;
string.gx_string_ptr = “myrstring”;
string.gx_string_length = strlen(string.gx_string_ptr);

status = gx_multi_line_text_input_text_set_ext(&my_text_input,
    &string);

/* If status is GX_SUCCESS, the content of “my_text_input” bas been reset. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_up_arrow"></a>gx_multi_line_text_input_up_arrow


여러 줄 텍스트 입력 커서를 이전 줄로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_input_up_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 입력 커서를 텍스트의 이전 줄로 이동합니다. 위쪽 화살표 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 커서를 이전 줄로 이동했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move the cursor to the previous line. */
status = gx_multi_line_text_input_up_arrow(&my_text_input);

/* If status is GX_SUCCESS the multi line text input cursor has been moved to the previous line. */

```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_create"></a>gx_multi_line_text_view_create


여러 줄 텍스트 뷰 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_view_create(
    GX_MULTI_LINE_TEXT_VIEW *text_view,
    GX_CONST GX_CHAR *name, 
    GX_WINDOW *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT text_view_id, 
    GX_CONST GX_RECTANGLE *size);

```

### <a name="description"></a>Description

이 서비스는 GX_MULTI_LINE_TEXT_VIEW 위젯을 만듭니다. 이 위젯 형식은 GX_WINDOW에서 파생되므로 해당 위젯 형식에서 gx_window API 서비스를 모두 활용할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_view** 여러 줄 텍스트 뷰 위젯 제어 블록
- **name** 텍스트 뷰 위젯의 이름
- **parent** 부모 위젯에 대한 포인터
- **text_id** 텍스트 문자열의 리소스 ID
- **style** 텍스트 뷰 위젯의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **text_view_id** 애플리케이션에서 정의된 텍스트 뷰 ID
- **size** 텍스트 뷰 위젯의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 뷰 위젯을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_create(&my_text_view,
    “my_text_view”, &my_parent,
    TEXT_STRING_ID, GX_STYLE_BORDER_RAISED,
    MY_TEXT_VIEW_ID, &size);

/* If status is GX_SUCCESS the text view “my_text_view” has been successfully created. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_draw"></a>gx_multi_line_text_view_draw


여러 줄 텍스트 뷰 위젯 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_multi_line_text_view_draw(GX_MULTI_LINE_TEXT_VIEW * text_view);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 뷰 위젯을 그립니다. 일반적으로 캔버스를 새로 고치는 동안 내부적으로 호출되지만 사용자 지정 여러 줄 텍스트 뷰 그리기 함수에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_view** 여러 줄 텍스트 뷰 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Write a custom multi line text view drawing function. */

VOID my_multi_line_text_view_draw(GX_MULTI_LINE_TEXT_VIEW *view)
{
    /* Call default multi line text view draw. */
    gx_multi_line_text_view_draw(view);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_event_process"></a>gx_multi_line_text_view_event_process


여러 줄 텍스트 뷰 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_view_event_process(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 뷰 위젯에 대한 이벤트를 처리합니다.

### <a name="parameters"></a>매개 변수

- **text_view** 여러 줄 텍스트 뷰 위젯 제어 블록
- **event** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 뷰 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom event handler. */
UINT my_event_handler(GX_MULTI_LINE_TEXT_VIEW *view, GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case GX_EVENT_SHOW:
        gx_multi_line_text_view_event_process(view, event_ptr);
        /* Add custom actions here. */
        break;
    default:
        gx_multi_line_text_view_event_process (view, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_font_set"></a>gx_multi_line_text_view_font_set


여러 줄 텍스트 뷰에서 사용되는 글꼴 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_view_text_id_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 뷰 위젯의 글꼴을 설정합니다.

### <a name="parameters"></a>매개 변수

- **text_view** 여러 줄 텍스트 뷰 위젯 제어 블록
- **font_id** 글꼴의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 뷰의 글꼴을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set font ID FONT_ID to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_font_set(&my_text_view, FONT_ID);

/* If status is GX_SUCCESS, the text view “my_text_view” will use the specified font to display its text. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_line_space_set"></a>gx_multi_line_text_view_line_space_set


여러 줄 텍스트 뷰 줄 간격 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_view_line_space_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_BYTE line_space);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 뷰 위젯의 텍스트 줄 간격을 설정합니다.

### <a name="parameters"></a>매개 변수

- **view** 여러 줄 텍스트 뷰 위젯 제어 블록
- **line_space** 설정할 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 뷰의 줄 간격 값을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

```C
/* Set line space of “my_text_view” to 2. */
status = gx_multi_line_text_view_line_space_set(&my_text_view, 2);

/* If status is GX_SUCCESS, the line space of “my_text_view” has been successfully set to 2. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_scroll_info_get"></a>gx_multi_line_text_view_scroll_info_get

여러 줄 텍스트 뷰 스크롤 정보 가져오기


### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_view_scroll_info_get(
    GX_MULTI_LINE_TEXT_VIEW *text_view, ULONG style,
    GX_SCROLL_INFO *info);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 뷰 스크롤 정보를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **text_view** 여러 줄 텍스트 뷰 위젯 제어 블록
- **Style** GX_SCROLLBAR_HORIZONTAL 또는 GX_SCROLLBAR_VERTICAL
- **Info** 스크롤 정보 대상에 대한 포인터입니다. **부록 I** 에는 GX_SCROLL_INFO 구조체의 정의가 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트 뷰 스크롤 정보를 검색했습니다.
- **GX_FAILURE**(0x10) 위젯이 표시되지 않거나 텍스트 뷰 글꼴 ID가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_SCROLL_INFO scroll_info;

/* Get scroll information for multi-line text view “my_text_view”. */
status = gx_multi_line_text_view_scroll_info_get(&my_text_view,
    &scroll_info);

/* If status is GX_SUCCESS the “scroll_info” contains the scroll information for multi-line text view “my_text_view”. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_color_set"></a>gx_multi_line_text_view_text_color_set


여러 줄 텍스트 뷰의 텍스트 색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_view_text_color_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCe_ID disabled_text_color_id);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 뷰 위젯에 텍스트 색을 할당합니다.

### <a name="parameters"></a>매개 변수

- **text_view** 여러 줄 텍스트 뷰 위젯 제어 블록
- **normal_text_color_id** 정상 상태에서 사용되는 표준 텍스트 색의 리소스 ID
- **selected_text_color_id** 위젯에 포커스가 있는 경우에 사용되는 선택된 텍스트 색의 리소스 ID
- **disabled_text_color_id** GX_STYLE_ENABLED가 활성 상태가 아닌 경우에 사용되는, 사용할 수 없는 텍스트 색의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 뷰의 색을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set text colors for the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_color_set(&my_text_view,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_id_set"></a>gx_multi_line_text_view_text_id_set


여러 줄 텍스트 뷰의 시스템 텍스트 문자열 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_view_text_id_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_RESOURCE_ID text_id);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 뷰 위젯에 문자열의 리소스 ID를 설정합니다.

### <a name="parameters"></a>매개 변수

- **text_view** 여러 줄 텍스트 뷰 위젯 제어 블록
- **text_id** 텍스트 문자열의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 뷰의 문자열 ID를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set string ID STRING_ID to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_id_set(&my_text_view, STRING_ID);

/* If status is GX_SUCCESS the text id of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_set"></a>gx_multi_line_text_view_text_set


여러 줄 텍스트 뷰에서 사용자 정의 문자열 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_view_text_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_CONST GX_CHAR *text);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 뷰 위젯에 텍스트 문자열을 할당합니다. GX_STYLE_TEXT_COPY 스타일을 사용하여 생성된 text_view 위젯은 할당된 텍스트 문자열의 프라이빗 복사본을 만들기 때문에 이 서비스를 요청하기 전에 gx_system_memory_allocate_set API를 한 번 호출해야 합니다. GX_STYLE_TEXT_COPY가 활성 상태가 아니면 위젯이 들어오는 문자열의 프라이빗 복사본을 만들지 않으므로 할당된 문자열을 정적이나 전역으로 할당해야 합니다. 즉, 자동 또는 임시 변수를 사용할 수 없습니다.

### <a name="parameters"></a>매개 변수

- **text_view** 여러 줄 텍스트 뷰 위젯 제어 블록
- **text** NULL로 종료된 텍스트 문자열

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 뷰의 문자열을 설정했습니다.
- **GX_SYSTEM_MEMORY_ERROR**(0x30) 메모리 할당자가 정의되지 않았거나 메모리를 할당하지 못했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set string “my string” to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_set(&my_text_view, “my string”);

/* If status is GX_SUCCESS the text of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_whitespace_set"></a>gx_multi_line_text_view_whitespace_set


여러 줄 텍스트 뷰 공백 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_multi_line_text_view_whitespace_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_UBYTE whitespace);
```

### <a name="description"></a>Description

이 서비스는 여러 줄 텍스트 뷰 위젯에서 위젯 개요와 클라이언트 영역 사이의 간격을 설정합니다.

### <a name="parameters"></a>매개 변수

- **text_view** 여러 줄 텍스트 뷰 위젯 제어 블록
- **whitespace** text_view 위젯과 표시되는 텍스트 사이의 여백 너비(픽셀)

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 여러 줄 텍스트 뷰의 공백을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set whitespace of “my_text_view” to 2. */
status = gx_multi_line_text_view_whitespace_set(&my_text_view, 2);

/* If status is GX_SUCCESS the whitespace of “my_text_view” has been successfully set to 2. */
```

### <a name="see-also"></a>참고 항목

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set

## <a name="gx_numeric_pixelmap_prompt_create"></a>gx_numeric_pixelmap_prompt_create


숫자 pixelmap 프롬프트 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_numeric_pixelmap_prompt_create(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    GX_CONST GX_CHAR name, GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, GX_RESOURCE_ID fill_id,
    ULONG style, USHORT pixelmap_prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 숫자 pixelmap 프롬프트 위젯을 만듭니다. numeric_pixelmap_prompt는 자체 버퍼를 유지하고 gx_numeric_pixelmap_prompt_value_set(INT) API를 제공하는 pixelmap_prompt일 뿐이며, 버퍼 크기는 GX_NUMERIC_PROMPT_BUFFER_SIZE 상수로 정의되고 기본값은 16입니다.

GX_NUMERIC_PIXELMAP_PROMPT는 GX_PIXELMAP_PROMPT에서 파생되며 gx_pixelmap_prompt API 서비스를 모두 지원합니다.

### <a name="parameters"></a>매개 변수

- **prompt** 숫자 pixelmap 프롬프트 제어 블록
- **name** 프롬프트의 이름
- **parent** 부모 위젯 제어 블록
- **text_id** 리소스 문자열 ID
- **fill_id** 채우기 영역의 pixelmap ID
- **style** 숫자 pixelmap 프롬프트의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **pixelmap_prompt_id** 애플리케이션에서 정의된 프롬프트 ID
- **size** 숫자 pixelmap 프롬프트의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 숫자 pixlemap 프롬프트를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_create(&my_numeric_pix_prompt,
    “my_numeric_pix_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, MY_FEEL_RESOURCE_ID,
    GX_STYLE_BORDER_RAISED, MY_NUMERIC_PIXELMAP_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the numeric pixelmap prompt “my_numeric_pix_prompt” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_pixelmap_format_function_set
- gx_numeric_pixelmap_prompt_value_set

## <a name="gx_numeric_pixelmap_prompt_format_function_set"></a>gx_numeric_pixelmap_prompt_format_function_set


숫자 pixelmap 프롬프트의 format 함수 재정의

### <a name="prototype"></a>프로토타입

```C
UINT gx_numeric_pixelmap_format_function_set(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    OID (*format_func)(GX_NUMERIC_PIXELMAP_PROMPT *, INT));
```

### <a name="description"></a>Description

이 서비스는 숫자 pixlemap 프롬프트 위젯의 기본 형식 함수를 재정의합니다. 기본 format 함수는 숫자 pixlemap 프롬프트 값을 문자열로 변환하고 위젯의 프라이빗 버퍼에 저장합니다. 이 서비스를 사용하면 애플리케이션에서 고유한 format 함수를 정의하여 숫자 pixelmap 프롬프트 값의 서식을 지정하고 위젯의 프라이빗 버퍼에 저장할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **prompt** 숫자 pixelmap 프롬프트 제어 블록
- **format_func** 설정할 format 함수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 숫자 pixlemap 프롬프트 format 함수를 설정했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Define my numeric pixelmap format function. */
VOID my_format_function(GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    INT value)
{
    /* If the value is “1234”, the new format will be “12.34”. */

    INT length;
    gx_utility_ltoa(value / 100,
        prompt->gx_numeric_pixelmap_prompt_buffer,
        GX_NUMERIC_PROMPT_ BUFFER_SIZE);
    Length = GX_STRLEN(prompt->gx_numeric_pixelmap_prompt_buffer);
    prompt->gx_numeric_pixelmap_prompt_buffer[length++] = ‘.’;
    gx_utility_ltoa(value % 100,
        prompt->gx_numeric_pixelmap_prompt_buffer + length,
        GX_NUMERIC_PROMPT_BUFFER_SIZE - length);
}

/* Override default format function of “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_format_function_set(
    &my_numeric_pix_prompt,
    my_format_function);

/* If status is GX_SUCCESS the format function of “my_numeric_pix_prompt” has been override. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_pixelmap_prompt_create
- gx_numeric_pixelmap_prompt_value_set

## <a name="gx_numeric_pixelmap_prompt_value_set"></a>gx_numeric_pixelmap_prompt_value_set


숫자 pixlemap 프롬프트 값 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_numeric_pixelmap_prompt_value_set(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    INT value);
```

### <a name="description"></a>Description

이 서비스는 숫자 pixelmap 프롬프트에 정수 값을 설정합니다.

### <a name="parameters"></a>매개 변수

- **prompt** 숫자 pixelmap 프롬프트 제어 블록
- **value** 설정할 정수 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 숫자 pixlemap 프롬프트 값을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set a value to “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_value_set(&my_numeric_pix_prompt, 1000);

/* If status is GX_SUCCESS the value of the numeric pixelmap prompt “my_numeric_pix_prompt” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_pixelmap_prompt_create
- gx_numeric_pixelmap_format_function_set

## <a name="gx_numeric_prompt_create"></a>gx_numeric_prompt_create


숫자 프롬프트 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_numeric_prompt_create( 
    GX_NUMERIC_PROMPT *prompt,
    GX_CONST GX_CHAR name, GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    ULONG style, USHORT prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 숫자 프롬프트 위젯을 만듭니다. numeric_prompt는 자체 버퍼를 유지하고 gx_numeric_prompt_value_set(INT) API를 제공하는 프롬프트일 뿐이며, 버퍼 크기는 GX_NUMERIC_PROMPT_BUFFER_SIZE 상수로 정의되고 기본값은 16입니다.

GX_NUMERIC_PROMPT는 GX_PROMPT에서 파생되며 gx_prompt API 서비스를 모두 지원합니다.

### <a name="parameters"></a>매개 변수

- **prompt** 숫자 프롬프트 제어 블록
- **name** 프롬프트의 이름
- **parent** 부모 위젯 제어 블록
- **text_id** 리소스 문자열 ID
- **style** 숫자 프롬프트의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **prompt_id** 애플리케이션에서 정의된 프롬프트 ID
- **size** 숫자 프롬프트의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 숫자 프롬프트를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create “my_numeric _prompt”. */
status = gx_numeric_prompt_create(&my_numeric_prompt,
    “my_numeric_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_NUMERIC_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the numeric prompt “my_numeric_prompt” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_format_function_set
- gx_numeric_prompt_value_set

## <a name="gx_numeric_prompt_format_function_set"></a>gx_numeric_prompt_format_function_set


숫자 프롬프트의 format 함수 재정의

### <a name="prototype"></a>프로토타입

```C
UINT gx_numeric_format_function_set(
    GX_NUMERIC_PROMPT *prompt,
    VOID (*format_func)(GX_NUMERIC_PROMPT *, INT));
```

### <a name="description"></a>Description

이 서비스는 숫자 프롬프트 위젯의 기본 format 함수를 재정의합니다. 기본 format 함수는 숫자 프롬프트 값을 문자열로 변환하고 위젯의 프라이빗 버퍼에 저장합니다. 이 서비스를 사용하면 애플리케이션에서 고유한 format 함수를 정의하여 숫자 프롬프트 값의 서식을 지정하고 위젯의 프라이빗 버퍼에 저장할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **prompt** 숫자 프롬프트 제어 블록
- **format_func** 설정할 format 함수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 숫자 프롬프트 format 함수를 설정했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Define my numeric format function. */
VOID my_format_function(GX_NUMERIC_PROMPT *prompt, INT value)
{
    /* If the value is “1234”, the new format will be “12.34”. */

    INT length;
    gx_utility_ltoa(value / 100, prompt->gx_numeric_prompt_buffer,
        GX_NUMERIC_PROMPT_ BUFFER_SIZE);
    Length = GX_STRLEN(prompt->gx_numeric_prompt_buffer);
    prompt->gx_numeric_prompt_buffer[length++] = ‘.’;
    gx_utility_ltoa(value % 100,
        prompt->gx_numeric_prompt_buffer + length,
        GX_NUMERIC_PROMPT_BUFFER_SIZE - length);
}

/* Override the default format function of “my_numeric_prompt”. */
status = gx_numeric_prompt_format_function_set(&my_numeric_prompt,
    my_format_function);

/* If status is GX_SUCCESS, the format function of “my_numeric_prompt” has been override. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_prompt_create
- gx_numeric_prompt_value_set

## <a name="gx_numeric_prompt_value_set"></a>gx_numeric_prompt_value_set


숫자 프롬프트 값 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_numeric_prompt_value_set(
    GX_NUMERIC_PROMPT *prompt, 
    INT value);
```

### <a name="description"></a>Description

이 서비스는 숫자 프롬프트에 정수 값을 설정합니다.

### <a name="parameters"></a>매개 변수

- **prompt** 숫자 프롬프트 제어 블록
- **value** 설정할 정수 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 숫자 프롬프트 값을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set a value to “my_numeric_prompt”. */
status = gx_numeric_prompt_value_set(&my_numeric_prompt, 1000);

/* If status is GX_SUCCESS the value of the numeric prompt “my_numeric_prompt” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_prompt_create
- gx_numeric_format_function_set

## <a name="gx_numeric_scroll_wheel_create"></a>gx_numeric_scroll_wheel_create


숫자 스크롤 휠 만들기

### <a name="prototype"></a>프로토타입


UINT gx_numeric_scroll_wheel_create( GX_NUMERIC_SCROLL_WHEEL *wheel, GX_CONST GX_CHAR *name, GX_WIDGET *parent, INT start_val, INT end_val, ULONG style, USHORT wheel_id, GX_CONST GX_RECTANGLE *size);

### <a name="description"></a>Description

이 서비스는 숫자 스크롤 휠 위젯을 만듭니다.

숫자 스크롤 휠은 숫자 범위를 표시하는 데 특별히 사용되는 스크롤 휠 위젯의 한 형식입니다. 다른 형식의 스크롤 휠 위젯도 사용할 수 있습니다. 스크롤 휠 위젯 계층 구조, 위젯 형식, 위젯 파생에 대한 자세한 내용은 gx_scroll_wheel_create() API를 참조하세요.

GX_NUMERIC_SCROLL_WHEEL은 GX_TEXT_SCROLL_WHEEL에서 파생되며 gx_text_scroll_wheel 및 gx_scroll_wheel 서비스를 모두 지원합니다.

모든 스크롤 휠 유형은 스크롤 휠이 스크롤될 때 부모에 대한 GX_EVENT_LIST_SELECT 이벤트를 생성합니다.

숫자 스크롤 휠은 기본적으로 abs(end_val – start_val) + 1개 행을 포함합니다. 즉, 스크롤 휠은 각 행마다 1씩 늘리거나 줄여 start_val과 end_val 사이에 있는 모든 값을 표시합니다. 애플리케이션에서 범위를 표시하는 방법에 따라 start_val이 end_val보다 크거나 작을 수 있습니다.

애플리케이션에서 행 증분을 변경하려는 경우 숫자 스크롤 휠을 만든 후에 gx_scroll_wheel_total_rows_set()을 호출하면 됩니다. 예를 들어 1980~2020년의 값을 5씩 늘려서 표시하는 스크롤 휠을 만들려는 애플리케이션에서는 다음 작업을 수행할 수 있습니다.

```C
gx_numeric_scroll_wheel_create(&wheel, GX_NULL, parent, 1980,
    2020, style, id, &size);

/* the years 1980 through 2020, inclusive, incrementing by 5 years,
yields 9 total rows */

gx_scroll_wheel_total_rows_set(&wheel, 9);
```

### <a name="parameters"></a>매개 변수

- **wheel** 숫자 스크롤 휠 제어 블록에 대한 포인터
- **name** pixelmap 단추 위젯의 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **start_val** 시작 숫자 값
- **end_val** 끝 숫자 값
- **style** 확인란의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **wheel_id** 애플리케이션에서 정의된 스크롤 휠 ID
- **size** 스크롤 휠 위젯의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 숫자 스크롤 휠을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create “year_wheel”. */
status = gx_numeric_scroll_wheel_create(&year_wheel,
    “year_selector””, &parent,
    1980, 2040,
    GX_STYLE_ENABLED | GX_STYLE_TEXT_CENTER |
    GX_STYLE_TRANSPARENT | GX_STYLE_WRAP |
    GX_STYLE_TEXT_SCROLL_WHEEL_ROUND,
    YEAR_WHEEL_ID,
    &size);

/* If status is GX_SUCCESS the scroll wheel “year_wheel” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_text_get

## <a name="gx_numeric_scroll_wheel_range_set"></a>gx_numeric_scroll_wheel_range_set


숫자 스크롤 휠의 값 범위 할당

### <a name="prototype"></a>프로토타입

```C
UINT
gx_numeric_scroll_wheel_range_set(
    GX_NUMERIC_SCROLL_WHEEL *wheel,
    INT start_val, INT end_val);
```

### <a name="description"></a>Description

이 서비스는 숫자 스크롤 휠 위젯에서 허용되고 표시되는 값의 범위를 수정합니다.

숫자 스크롤 휠은 숫자 범위를 표시하는 데 특별히 사용되는 스크롤 휠 위젯의 한 형식입니다. 다른 형식의 스크롤 휠 위젯도 사용할 수 있습니다. 스크롤 휠 위젯 계층 구조, 위젯 형식, 위젯 파생에 대한 자세한 내용은 gx_scroll_wheel_create() API를 참조하세요.

이 API를 호출하면 스크롤 휠 행의 총수가 abs(end_val – start_val) + 1개로 다시 설정되므로 스크롤 휠이 각 행마다 1씩 증가합니다. 애플리케이션에서 gx_scroll_wheel_total_rows_set()을 호출하여 행의 총수를 변경하면 행 간의 증분 값을 변경할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **wheel** 숫자 스크롤 휠 제어 블록에 대한 포인터
- **start_val** 시작 숫자 값 
- **end_val** 끝 숫자 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 숫자 스크롤 휠 범위를 설정했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드 

### <a name="example"></a>예제

```C
/* Change range of “rate” scroll wheel. */

status = gx_numeric_scroll_wheel_range_set(&year_wheel, 0, 200);

/* If status is GX_SUCCESS the scroll wheel range has been modified. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_pixelmap_button_create"></a>gx_pixelmap_button_create


pixelmap 단추 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_pixelmap_button_create(
    GX_PIXELMAP_BUTTON *button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id,
    GX_RESOURCE_ID disabled_id,
    ULONG style,
    USHORT pixelmap_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 pixelmap 단추 위젯을 만듭니다.

GX_PIXELMAP_BUTTON은 GX_BUTTON에서 파생되며 gx_button 서비스를 모두 지원합니다.

### <a name="parameters"></a>매개 변수

- **button** pixelmap 단추 컨트롤 블록에 대한 포인터
- **name** pixelmap 단추 위젯의 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **normal_id** 정상 상태 리소스 ID
- **selected_id** 선택된 상태 리소스 ID
- **disabled_id** 사용할 수 없는 상태 리소스 ID
- **style** 확인란의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **pixelmap_button_id** 애플리케이션에서 정의된 pixelmap 단추 ID
- **size** pixelmap 단추의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap 단추를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create “my_pixelmap_button”. */
status = gx_pixelmap_button_create(&my_pixelmap_button,
    “my_pixelmap_button”, &my_parent,
    MY_NORMAL_RESOURCE_ID, MY_SELECTED_RESOURCE_ID,
    MY_DESELECTED_RESOURCE_ID, GX_STYLE_BORDER_RAISED,
    MY_PIXELMAP_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS the pixelmap button “my_pixelmap_button” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_draw
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_draw"></a>gx_pixelmap_button_draw


pixelmap 단추 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_pixelmap_button_draw(GX_PIXELMAP_BUTTON *button);
```

### <a name="description"></a>Description

이 서비스는 pixelmap 단추 위젯을 그립니다. 일반적으로 GUIX 캔버스 새로 고침 메커니즘을 통해 내부적으로 호출되지만 사용자 지정 pixelmap 단추 위젯용 사용자 지정 그리기 함수를 구현하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **button** pixelmap 단추 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom pixelmap button drawing function. */

VOID my_pixelmap_button_draw(GX_PIXELMAP_BUTTON *button)
{
    /* Call default pixelmap button draw. */
    gx_pixelmap_button_draw(button);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_event_process"></a>gx_pixelmap_button_event_process


pixelmap 단추 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_pixelmap_button_event_process(
    GX_PIXELMAP_BUTTON *button,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 pixelmap 단추 위젯 형식에 대한 기본 이벤트 처리를 제공합니다.

### <a name="parameters"></a>매개 변수

- **button** pixelmap 단추 컨트롤 블록에 대한 포인터
- **event_ptr** GX_EVENT 구조체에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap 단추를 그렸습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
switch(event_ptr->gx_event_type)
{
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_pixelmap_button_event_process(icon, event_ptr);
    
        /* add my own handling here */
        break;
}
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_pixelmap_set"></a>gx_pixelmap_button_pixelmap_set


단추에 pixelmap 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_pixelmap_button_pixelmap_set(
    GX_PIXELMAP_BUTTON *button, 
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id, 
    GX_RESOURCE_ID disabled_id);
```

### <a name="description"></a>Description

이 서비스는 pixelmap 단추에 pixelmap을 설정합니다.

### <a name="parameters"></a>매개 변수

- **button** pixelmap 단추 컨트롤 블록에 대한 포인터
- **normal_id** 정상 상태로 사용할 pixelmap의 리소스 ID
- **selected_id** 단추가 선택된 경우에 사용할 pixelmap의 리소스 ID
- **disabled_id** 단추를 사용할 수 없는 경우에 사용할 pixelmap의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 단추에 pixelmap을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Draw “my_pixelmap_button”. */
status = gx_pixelmap_button_pixelmap_set (&my_pixelmap_button,
    NORMAL_ID, SELECTED_ID,
    DISABLED_ID);

/* If status is GX_SUCCESS the pixelmap button is properly configured with the specified pixelmaps. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_prompt_create"></a>gx_pixelmap_prompt_create


pixelmap 프롬프트 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_pixelmap_prompt_create(
    GX_PIXELMAP_PROMPT *prompt,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    GX_RESOURCE_ID fill_pixelmap_id,
    ULONG style,
    USHORT pixelmap_prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 pixelmap 프롬프트 위젯을 만듭니다. pixelmap 프롬프트는 pixelmap을 사용하여 프롬프트 배경을 색칠한다는 점에서 표준 GX_PROMPT와는 다릅니다. create 함수는 하나의 pixelmap ID인 정상 상태 채우기 pixelmap을 수락합니다. pixelmap 프롬프트에 최대 6개의 pixelmap을 할당할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **prompt** pixelmap 프롬프트 제어 블록에 대한 포인터
- **name** pixelmap 프롬프트 위젯의 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **text_id** 텍스트의 리소스 ID
- **fill_id** 채우기의 리소스 ID
- **style** 확인란의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **pixelmap_prompt_id** 애플리케이션에서 정의된 pixelmap 프롬프트 ID
- **size** pixelmap 프롬프트의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap 프롬프트를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create “my_pixelmap_prompt”. */
status = gx_pixelmap_prompt_create(&my_pixelmap_prompt,
    “my_pixelmap_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, MY_LEFT_RESOURCE_ID,
    MY_FILL_RESOURCE_ID, MY_RIGHT_RESOURCE_ID,
    GX_STYLE_BORDER_RAISED, MY_PIXELMAP_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the pixelmap prompt “my_pixelmap_prompt” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_pixelmap_prompt_draw"></a>gx_pixelmap_prompt_draw


pixelmap 프롬프트 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_pixelmap_prompt_draw(GX_PIXELMAP_PROMPT *prompt);
```

### <a name="description"></a>Description

이 서비스는 pixelmap 프롬프트 위젯을 그립니다. 일반적으로 GUIX 캔버스 새로 고침 메커니즘을 통해 내부적으로 호출되지만 사용자 지정 pixelmap 프롬프트 위젯용 사용자 지정 그리기 함수를 구현하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **prompt** pixelmap 프롬프트 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Write a custom pixelmap prompt drawing function. */

VOID my_pixelmap_button_draw(GX_PIXELMAP_PROMPT *prompt)
{
    /* Call default pixelmap prompt draw. */
    gx_pixelmap_prompt_draw(prompt);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_pixelmap_prompt_pixelmap_set"></a>gx_pixelmap_prompt_pixelmap_set


프롬프트에 pixelmap 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_pixelmap_prompt_pixelmap_set(
    GX_PIXELMAP_PROMPT *prompt,
    GX_RESOURCE_ID normal_left_pixelmap,
    GX_RESOURCE_ID normal_fill_pixelmap,
    GX_RESOURCE_ID normal_right_pixelmap,
    GX_RESOURCE_ID selected_left_pixelmap,
    GX_RESOURCE_ID selected_fill_pixelmap,
    GX_RESOURCE_ID selected_right_pixelmap);
```

### <a name="description"></a>Description

이 서비스는 pixelmap 프롬프트에 pixelmap ID를 할당합니다. 왼쪽, 채우기, 오른쪽 pixelmap ID를 통해 애플리케이션에서 너비는 각기 다르지만 높이가 같은 프롬프트에 하나의 pixelmap 집합을 사용하여 스토리지 요구 사항을 줄일 수 있습니다. 왼쪽 및 오른쪽 ID를 사용하지 않는 경우 모두 0으로 설정해야 합니다. 입력 포커스가 있는 프롬프트를 다르게 그려야 하는 경우 선택된 pixelmap ID가 해당 용도로 사용됩니다. 선택된 ID가 사용되지 않거나 표준 ID와 동일한 경우 0으로 설정합니다.

### <a name="parameters"></a>매개 변수

- **prompt** pixelmap 프롬프트 제어 블록에 대한 포인터
- **normal_left_id** 정상 상태에서 왼쪽에 사용할 pixelmap의 리소스 ID
- **normal_fill_id** 정상 상태에서 바둑판식 채우기로 사용할 pixelmap의 리소스 ID
- **normal_right_id** 정상 상태에서 오른쪽에 사용할 pixelmap의 리소스 ID
- **selected_left_id** 선택된 상태에서 왼쪽에 사용할 pixelmap의 리소스 ID
- **selected_fill_id** 선택된 상태에서 바둑판식 채우기로 사용할 pixelmap의 리소스 ID
- **selected_right_id** 선택된 상태에서 오른쪽에 사용할 pixelmap의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 프롬프트에 pixelmap을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Assign pixelmap IDs to “my_prompt”. Only the normal state pixelmaps are used in this case */
status = gx_pixelmap_prompt_pixelmap_set (&my_prompt,
    normal_left_id, normal_fill_id,
    normal_right_id, 0, 0, 0);

/* If status is GX_SUCCESS the pixelmap prompt is properly configured with pixelmaps. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_slider_create"></a>gx_pixelmap_slider_create


pixelmap 슬라이더 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_pixelmap_slider_create(
    GX_PIXELMAP_SLIDER *slider,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    GX_SLIDER_INFO *info,
    GX_PIXELMAP_SLIDER_INFO *pixelmap_info, ULONG style,
    USHORT pixelmap_slider_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 pixelmap 슬라이더 위젯을 만듭니다.

### <a name="parameters"></a>매개 변수

- **slider** pixelmap 슬라이더 제어 블록에 대한 포인터
- **name** pixelmap 슬라이더 위젯의 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **info** 슬라이더 최솟값, 최댓값, 현재 값, 바늘 한도를 정의하는 값을 포함하는 GX_SLIDER_INFO 구조체에 대한 포인터입니다. **부록 I** 에는 GX_SLIDER_INFO 구조체의 정의가 나와 있습니다.
- **pixelmap_info** 슬라이더 배경과 바늘을 그리는 데 사용되는 pixelmap을 정의하는 GX_PIXELMAP_SLIDER_INFO 구조체에 대한 포인터입니다. **부록 I** 에는 GX_PIXELMAP_SLIDER_INFO 구조체의 정의가 나와 있습니다. 슬라이더 배경에는 한두 개의 pixelmap을 사용할 수 있습니다. 하나의 pixelmap을 사용하는 경우 바늘이 이동할 때 배경이 변경되지 않습니다. 두 개의 배경이 정의된 경우 바늘 앞의 배경은 첫 번째 배경 pixelmap을 사용하고 바늘 뒤의 배경은 두 번째 배경 pixelmap을 사용합니다.
- **style** 슬라이더의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **pixelmap_slider_id** 애플리케이션에서 정의된 pixelmap 슬라이더 ID
- **size** pixelmap 프롬프트의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap 슬라이더를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_SLIDER_INFO info;
GX_PIXELMAP_SLIDER_INFO pixelmap_info;

/* Initiate slider information structure. */
info.gx_slider_info_min_val = 0;
info.gx_slider_info_max_val = 100;
info.gx_slider_info_current_val = 50;
info.gx_slider_info_min_travel = 10;
info.gx_slider_info_max_tralvel = 10;
info.gx_slider_info_needle_width = 5;
info.gx_slider_info_needle_height = 10;
info.gx_slider_info_needle_inset = 5;
info.gx_slider_info_needle_hotspot_offset;

/* Initiate pixelmap slider information structure. */
pixelmap_info.gx_pixelmap_slider_info_lower_background_pixelmap =
                                        GX_PIXELMAP_ID_ORANGE;
pixelmap_info.gx_pixelmap_slider_info_upper_background_pixelmap =
                                        GX_PIXELMAP_ID_EMPTY;
pixelmap_info.gx_pixelmap_slider_info_needle_pixelmap =
                                        GX_PIXELMAP_ID_NEEDLE;

/* Create “my_pixelmap_slider”. */
status = gx_pixelmap_slider_create(&my_pixelmap_slider,
                            “my_pixelmap_slider”, &my_parent,
                            &info, &pixelmap_info,
                            GX_STYLE_BORDER_RAISED,
                            MY_PIXELMAP_SLIDER_ID, &size);

/* If status is GX_SUCCESS the pixelmap slider “my_pixelmap_slider” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_draw"></a>gx_pixelmap_slider_draw


pixelmap 슬라이더 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_pixelmap_slider_draw(GX_PIXELMAP_SLIDER *slider);
```

### <a name="description"></a>Description

이 서비스는 pixelmap 슬라이더 위젯을 그립니다. 일반적으로 GUIX 캔버스 새로 고침 메커니즘을 통해 내부적으로 호출되지만 사용자 지정 pixelmap 슬라이더 위젯용 사용자 지정 그리기 함수를 구현하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **slider** pixelmap 슬라이더 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom pixelmap slider drawing function. */

VOID my_pixelmap_slider_draw(GX_PIXELMAP_SLIDER *pixelmap_slider)
{
    /* Call default pixelmap slider draw. */
    gx_pixelmap_slider_draw(pixelmap_slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_event_process"></a>gx_pixelmap_slider_event_process


pixelmap 슬라이더 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_pixelmap_slider_event_process(
    GX_PIXELMAP_SLIDER *slider,
    GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 지정된 pixelmap 슬라이더 위젯에 대한 이벤트를 처리합니다.

### <a name="parameters"></a>매개 변수

- **slider** pixelmap 슬라이더 제어 블록에 대한 포인터
- **event** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap 슬라이더 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Write a custom event processing function. */
UINT my_event_hanlder(GX_PIXELMAP_SLIDER *pixelmap_slider, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_pixelmap_slider_event_process(pixelmap_slider,
                                                    event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_pixelmap_slider_event_process(pixelmap_slider,
                                                  event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_pixelmap_set"></a>gx_pixelmap_slider_pixelmap_set


슬라이더에 pixelmap 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_pixelmap_slider_pixelmap_set(
    GX_PIXELMAP_SLIDER *slider,
    GX_PIXELMAP_SLIDER_INFO *pixinfo);
```

### <a name="description"></a>Description

이 서비스는 pixelmap 슬라이더에 pixelmap을 설정합니다.

### <a name="parameters"></a>매개 변수

- **slider** pixelmap 슬라이더 제어 블록에 대한 포인터
- **pixinfo** 슬라이더 배경과 바늘을 그리는 데 사용되는 pixelmap을 정의하는 GX_PIXELMAP_SLIDER_INFO 구조체에 대한 포인터입니다. **부록 I** 에는 GX_PIXELMAP_SLIDER_INFO 구조체의 정의가 나와 있습니다. 슬라이더 배경에는 한두 개의 pixelmap을 사용할 수 있습니다. 하나의 pixelmap을 사용하는 경우 바늘이 이동할 때 배경이 변경되지 않습니다. 두 개의 배경이 정의된 경우 바늘 앞의 배경은 첫 번째 배경 pixelmap을 사용하고 바늘 뒤의 배경은 두 번째 배경 pixelmap을 사용합니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 슬라이더에 pixelmap을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_PIXELMAP_SLIDER_INFO pixelmap_info;

/* Initiate pixelmap slider information structure. */
pixelmap_info.gx_pixelmap_slider_info_lower_background_pixelmap =
                                        GX_PIXELMAP_ID_ORANGE;
pixelmap_info.gx_pixelmap_slider_info_upper_background_pixelmap =
                                        GX_PIXELMAP_ID_EMPTY;
pixelmap_info.gx_pixelmap_slider_info_needle_pixelmap =
                                        GX_PIXELMAP_ID_NEEDLE;

/* Draw “my_pixelmap_button”. */
status = gx_pixelmap_slider _pixelmap_set (&my_pixelmap_slider,
                                &pixelmap_info);

/* If status is GX_SUCCESS the pixelmap slider is properly configured with “pixelmap_info”. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_progress_bar_background_draw"></a>gx_progress_bar_background_draw


진행률 표시줄 배경 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_progress_bar_background_draw(GX_PROGRESS_BAR *progress_bar)
```

### <a name="description"></a>Description

이 서비스는 지정된 진행률 표시줄의 배경을 그립니다. gx_progress_bar_draw()의 일부로 내부적으로 호출되지만 애플리케이션이 사용자 지정 진행률 표시줄 그리기 함수를 정의하는 경우를 지원하기 위해 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 진행률 표시줄 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar background draw. */
    gx_progress_bar_background_draw(progress_bar);

    /* Call default progress bar text draw. */
    gx_progress_bar_text_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_value_set

## <a name="gx_progress_bar_create"></a>gx_progress_bar_create


진행률 표시줄 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_progress_bar_create(
    GX_PROGRESS_BAR *progress_bar,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_PROGRESS_BAR_INFO *progress_bar_info,
    ULONG style, 
    USHORT progress_bar_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 진행률 표시줄 위젯을 만듭니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 진행률 표시줄 제어 블록
- **name** 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **progress_bar_info** GX_PROGRESS_BAR_INFO 구조체에 대한 포인터입니다. **부록 I** 에는 GX_PROGRESS_BAR_INFO 구조체의 정의가 나와 있습니다.
- **style** 진행률 표시줄의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **progress_bar_id** 애플리케이션에서 정의된 진행률 표시줄 ID
- **size** 진행률 표시줄의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 진행률 표시줄을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 부모 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_PROGRESS_BAR_INFO info;
GX_RECTANGLE size;

info.gx_progress_bar_info_min_val = 0;
info.gx_progress_bar_info_max_val = 100;
info.gx_progress_bar_info_current_val = 0;
info.gx_progress_bar_font_id = GX_FONT_ID_SYSTEM_FONT;
info.gx_progress_bar_normal_text_color = GX_COLOR_ID_WHITE;
info.gx_progress_bar_selected_text_color = GX_COLOR_ID_BLUE;
info.gx_progress_bar_fill_pixelmap = 0;

size.gx_rectangle_left = 10;
size.gx_rectangle_top = 10;
size.gx_rectangle_right = 110;
size.gx_rectangle_bottom = 140;

/* Create a progress bar with the specified information. */
status = gx_progress_bar_create(&my_progress_bar, GX_NULL, GX_NULL,
                        &info, GX_STYLE_BORDER_THIN,
                        0, &size);

/* If status is GX_SUCSESS the progress bar “my_progress_bar” has been successfully created. */
```

### <a name="see-also"></a>참고 항목

- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_draw"></a>gx_progress_bar_draw


진행률 표시줄 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_progress_bar_draw(GX_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Description

이 서비스는 진행률 표시줄 위젯을 그립니다. 일반적으로 GUIX 캔버스 새로 고침 메커니즘을 통해 내부적으로 호출되지만 사용자 지정 진행률 표시줄 위젯용 사용자 지정 그리기 함수를 구현하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 진행률 표시줄 제어 블록

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar draw. */
    gx_progress_bar_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_progress_bar_create
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_event_process"></a>gx_progress_bar_event_process


진행률 표시줄 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_progress_bar_event_process(
    GX_PROGRESS_BAR *progress_bar,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 진행률 표시줄 이벤트를 처리합니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 진행률 표시줄 제어 블록
- **event_ptr** GX_EVENT 구조체에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 프롬프트를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_PROGRESS_BAR *progress_bar, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_progress_bar_event_process(progress_bar,
                                                event_ptr);
        /* add my own handling here */
        break;
    default:
        status = gx_progress_bar_event_process(progress_bar,
                                                event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_progress_bar_create
- gx_progress_bar_event_draw
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_font_set"></a>gx_progress_bar_font_set


진행률 표시줄 텍스트 글꼴 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_progress_bar_font_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Description

이 서비스는 진행률 표시줄 위젯의 글꼴을 설정합니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 진행률 표시줄 제어 블록
- **font_id** 글꼴 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 진행률 표시줄 글꼴을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
UINT status = gx_progress_bar_font_set(&progress_bar,
                                        GX_FONT_ID_MEDIUM);

/* if status is GX_SUCCESS, the font was successfully assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_info_set"></a>gx_progress_bar_info_set


진행률 표시줄 정보 구조체 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_progress_bar_info_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_PROGRESS_BAR_INFO *info);
```

### <a name="description"></a>Description

이 서비스는 진행률 표시줄 위젯의 정보 구조체를 다시 설정합니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 진행률 표시줄 제어 블록
- **info** GX_PROGRESS_BAR_INFO 구조체에 대한 포인터입니다. **부록 I** 에는 GX_PROGRESS_BAR_INFO 구조체의 정의가 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 진행률 표시줄 정보를 다시 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_PROGRESS_BAR_INFO info;

info.gx_progress_bar_info_min_val = 0;
info.gx_progress_bar_info_max_val = 100;
info.gx_progress_bar_info_current_val = 0;
info.gx_progress_bar_font_id = GX_FONT_ID_SYSTEM_FONT;
info.gx_progress_bar_normal_text_color = GX_COLOR_ID_WHITE;
info.gx_progress_bar_selected_text_color = GX_COLOR_ID_BLUE;
info.gx_progress_bar_fill_pixelmap = 0;

status = gx_progress_bar_info_set(&progress_bar, &info);

/* if status == GX_SUCCESS the progress bar info was re-assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_progress_bar_info_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_pixelmap_set"></a>gx_progress_bar_pixelmap_set


진행률 표시줄을 그리는 데 사용되는 pixelmap 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_progress_bar_pixelmap_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID pixelmap_id);
```

### <a name="description"></a>Description

이 서비스는 진행률 표시줄 배경을 채우는 데 사용되는 pixelmap을 설정합니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 진행률 표시줄 제어 블록
- **pixelmap_id** pixelmap 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 진행률 표시줄 pixelmap을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
UINT status = gx_progress_bar_pixelmap_set(&progress_bar,
                                GX_PIXELMAP_ID_PROGRESS_FILL);

/* if status is GX_SUCCESS, the pixelmap was successfully assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_progress_bar_pielmap_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_range_set"></a>gx_progress_bar_range_set


진행률 표시줄의 값 범위 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_progress_bar_range_set(
    GX_PROGRESS_BAR *progress_bar,
    INT min_value, 
    INT max_value);
```

### <a name="description"></a>Description

이 서비스는 진행률 표시줄 값 범위를 설정합니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 진행률 표시줄 제어 블록
- **min_value** 진행률 표시줄 최솟값
- **max_value** 진행률 표시줄 최댓값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 진행률 표시줄 범위를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
UINT status = gx_progress_bar_range_set(progress_bar, 0, 100);

/* if status is GX_SUCCESS, the progress bar range was successfully assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_progress_bar_range_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_text_color_set"></a>gx_progress_bar_text_color_set


진행률 표시줄의 텍스트 색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_progress_bar_text_color_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCE_ID disabled_text_color);
```

### <a name="description"></a>Description

이 서비스는 진행률 표시줄 위젯의 텍스트 색을 설정합니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 진행률 표시줄 제어 블록
- **normal_text_color** 정상 상태에서 사용되는 표준 텍스트 색의 리소스 ID
- **selected_text_color** 위젯에 포커스가 있는 경우에 사용되는 선택된 텍스트 색의 리소스 ID
- **disabled_text_color** GX_STYLE_ENABLED가 활성 상태가 아닌 경우에 사용되는 사용할 수 없는 텍스트 색의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 진행률 표시줄 텍스트 색을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set text colors for the progress bar “my_progress_bar”*/
UINT status = gx_progress_bar_text_color_set(&my_progress_bar,
                        GX_COLOR_ID_NORMAL_TEXT,
                        GX_COLOR_ID_SELECTED_TEXT,
                        GX_COLOR_ID_DISABLED_TEXT);

/* if status is GX_SUCCESS, the progress bar text colors were successfully assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_text_draw"></a>gx_progress_bar_text_draw


진행률 표시줄 텍스트 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_progress_bar_text_draw(GX_PROGRESS_BAR *progress_bar)
```

### <a name="description"></a>Description

이 서비스는 지정된 진행률 표시줄의 텍스트를 그립니다. gx_progress_bar_draw()의 일부로 내부적으로 호출되지만 애플리케이션이 사용자 지정 진행률 표시줄 그리기 함수를 정의하는 경우를 지원하기 위해 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 진행률 표시줄 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar background draw. */
    gx_progress_bar_background_draw(progress_bar);

    /* Call default progress bar text draw. */
    gx_progress_bar_text_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_value_set

## <a name="gx_progress_bar_value_set"></a>gx_progress_bar_value_set


진행률 표시줄의 현재 값 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_progress_bar_value_set(
    GX_PROGRESS_BAR *progress_bar,
    INT value);
```

### <a name="description"></a>Description

이 서비스는 진행률 표시줄의 현재 값을 할당합니다. 진행률 표시줄 값을 변경하면 진행률 표시줄 위젯이 자동으로 무효화되고 다시 그려집니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 진행률 표시줄 제어 블록
- **value** 진행률 표시줄 현재 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 진행률 표시줄의 값을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
UINT status = gx_progress_bar_value_set(progress_bar, 50);

/* if status == GX_SUCCESS the progress bar value was successfully assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_progress_bar_value_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw

## <a name="gx_prompt_create"></a>gx_prompt_create


프롬프트 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_prompt_create(
    GX_PROMPT *prompt, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 프롬프트 위젯을 만듭니다.

GX_PROMPT는 GX_WIDGET에서 파생되며 gx_widget 서비스를 모두 지원합니다.

### <a name="parameters"></a>매개 변수

- **parent** 부모 위젯에 대한 포인터
- **text_id** 프롬프트 텍스트의 리소스 ID
- **style** 프롬프트의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **prompt_id** 애플리케이션에서 정의된 프롬프트 ID
- **size** 프롬프트의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 프롬프트를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create “my_prompt”. */
status = gx_prompt_create(&my_prompt, “my_promPt”, &my_parent,
                    MY_PROMPT_TEXT_RESOURCE_ID,
                    GX_STYLE_BORDER_RAISED, MY_PROPMT_ID, &size);

/* If status is GX_SUCCESS the prompt “my_prompt” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_draw"></a>gx_prompt_draw


프롬프트 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_prompt_draw(GX_PROMPT *prompt);
```

### <a name="description"></a>Description

이 서비스는 프롬프트 위젯을 그립니다. 캔버스를 새로 고치는 동안 GUIX에서 내부적으로 호출되지만 사용자 지정 그리기 함수에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **prompt** 프롬프트 위젯 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom prompt drawing function. */

VOID my_prompt_draw(GX_PROMPT *prompt)
{
    /* Call default prompt draw. */
    gx_prompt_draw(prompt);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_event_process"></a>gx_prompt_event_process


프롬프트 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_prompt_event_process(GX_PROMPT *prompt, GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 프롬프트에 대한 이벤트를 처리합니다. 사용자 지정 프롬프트 이벤트 처리 함수에서 기본 이벤트 처리기로 호출되어야 합니다.

### <a name="parameters"></a>매개 변수

- **prompt** 프롬프트 제어 블록에 대한 포인터
- **event_ptr** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 프롬프트 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic prompt event processing as part of custom event processing function. */

UINT custom_prompt_event_process(GX_PROMPT *prompt, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default prompt event processing */
        status = gx_prompt_event_process(prompt, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_font_set"></a>gx_prompt_font_set


프롬프트 글꼴 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_prompt_font_set(
    GX_PROMPT *prompt, 
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Description

이 서비스는 프롬프트 위젯의 글꼴을 설정합니다.

### <a name="parameters"></a>매개 변수

- **prompt** 프롬프트 위젯 제어 블록에 대한 포인터
- **font_id** 글꼴의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 프롬프트 글꼴을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the font of “my_prompt”. */
status = gx_prompt_font_set(&my_prompt, MY_PROMPT_FONT_ID);

/* If status is GX_SUCCESS the font for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_color_set"></a>gx_prompt_text_color_set


프롬프트 텍스트 색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_prompt_text_color_set(
    GX_PROMPT *prompt,
    GX_RESOURCE_ID normal_color,
    GX_RESOURCE_ID selected_color,
    GX_RESOURCE_ID disabled_color);
```

### <a name="description"></a>Description

이 서비스는 프롬프트 위젯의 텍스트 색을 설정합니다.

### <a name="parameters"></a>매개 변수

- **prompt** 프롬프트 위젯 제어 블록에 대한 포인터
- **normal_color** 표준 텍스트 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **selected_color** 위젯에 포커스가 있는 경우에 사용되는 선택된 텍스트 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **disabled_color** GX_STYLE_ENABLED가 활성 상태가 아닌 경우에 사용되는 사용할 수 없는 텍스트 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 프롬프트 텍스트 색을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET_SIZE**(0x14) 위젯 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the text color of “my_prompt”. */
status = gx_prompt_text_color_set(&my_prompt,
                    GX_COLOR_ID_BLACK,
                    GX_COLOR_ID_LIGHTGRAY,
                    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_draw"></a>gx_prompt_text_draw


그리기 지원 함수

### <a name="prototype"></a>프로토타입

```C
VOID gx_prompt_text_draw(GX_PROMPT *prompt);
```

### <a name="description"></a>Description

이 지원 함수는 프롬프트의 텍스트 부분을 그립니다. gx_prompt_draw()에서 내부적으로 호출되며, 사용자 지정 프롬프트 그리기 함수를 정의하는 애플리케이션의 편의를 위해 별도의 API로 제공됩니다. 프롬프트 배경 그리기를 사용자 지정하려는 애플리케이션은 사용자 지정 그리기 함수를 제공하고 사용자 지정 그리기의 일부로 gx_prompt_text_draw 서비스를 호출하여 배경에 프롬프트 텍스트를 그릴 수 있습니다.

### <a name="parameters"></a>매개 변수

- **prompt** 프롬프트 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Define a custom drawing function */
VOID my_prompt_draw(GX_PROMPT *prompt)
{
    /* insert code here to draw prompt background */

    /* call support function to do text drawing */
    gx_prompt_text_draw();

    /* draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) prompt);
}
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_get"></a>gx_prompt_text_get


프롬프트 텍스트 가져오기(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_prompt_text_get(
    GX_PROMPT *prompt, 
    GX_CHAR **return_text);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_prompt_text_get_ext()로 대체되었습니다.

이 서비스는 프롬프트 위젯의 텍스트를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **prompt** 프롬프트 위젯 제어 블록에 대한 포인터
- **return_text** 텍스트 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 프롬프트 텍스트를 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_PROMPT my_prompt;
GX_CHAR *my_prompt_text;

/* Get the text of “my_prompt”. */
status = gx_prompt_text_get(&my_prompt, &my_prompt_text);

/* If status is GX_SUCCESS the pointer “my_prompt_text” points to the text displayed by “my_prompt”. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_get_ext"></a>gx_prompt_text_get_ext


프롬프트 텍스트 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_prompt_text_get(
    GX_PROMPT *prompt, 
    GX_STRING *return_string);
```

### <a name="description"></a>Description

이 서비스는 프롬프트 위젯의 문자열을 가져옵니다.

### <a name="parameters"></a>매개 변수

- **prompt** 프롬프트 위젯 제어 블록에 대한 포인터
- **return_string** 문자열 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 프롬프트 텍스트를 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_PROMPT my_prompt;
GX_STRING my_prompt_string;

/* Get the text of “my_prompt”. */
status = gx_prompt_text_get_ext(&my_prompt, &my_prompt_string);

/* If status is GX_SUCCESS then my_prompt_string has been initialize to hold a copy of the prompt string. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_id_set"></a>gx_prompt_text_id_set


프롬프트 텍스트 ID 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_prompt_text_id_set(
    GX_PROMPT *prompt, 
    GX_RESOURCE_ID string_id);
```

### <a name="description"></a>Description

이 서비스는 텍스트 프롬프트 위젯의 문자열 ID를 설정합니다.

### <a name="parameters"></a>매개 변수

- **prompt** 프롬프트 위젯 제어 블록에 대한 포인터
- **string_id** 문자열의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 프롬프트 텍스트 ID를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**(0x30) 메모리 해제 함수가 정의되어 있지 않습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the string ID of “my_prompt”. */
status = gx_prompt_text_id_set(&my_prompt, MY_STRING_ID);

/* If status is GX_SUCCESS the text ID for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_prompt_text_set"></a>gx_prompt_text_set


프롬프트 텍스트 설정(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_prompt_text_set(
    GX_PROMPT *prompt, 
    GX_CHAR *text);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_prompt_text_set_ext()로 대체되었습니다.

이 서비스는 프롬프트 위젯의 텍스트를 설정합니다. GX_STYLE_TEXT_COPY 스타일을 사용하여 생성된 프롬프트 위젯은 할당된 텍스트 문자열의 프라이빗 복사본을 만듭니다. GX_STYLE_TEXT_COPY가 활성 상태가 아니면 위젯이 들어오는 문자열의 프라이빗 복사본을 만들지 않으므로 문자열을 정적이나 전역으로 할당해야 합니다. 즉, 자동 또는 임시 변수를 사용할 수 없습니다.

GX_PROMPT는 GX_WIDGET에서 파생되므로 GX_PROMPT에서 gx_widget API 서비스를 모두 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **prompt** 프롬프트 위젯 제어 블록에 대한 포인터
- **text** 텍스트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 프롬프트 텍스트를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**(0x30) 메모리 할당 함수가 정의되어 있지 않습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the text of “my_prompt” to “my_text”. */
status = gx_prompt_text_set(&my_prompt, “my_text”);

/* If status is GX_SUCCESS the text for “my_prompt” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_get

## <a name="gx_prompt_text_set_ext"></a>gx_prompt_text_set_ext

프롬프트 텍스트 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_prompt_text_set_ext(
    GX_PROMPT *prompt,
    GX_STRING *string);
```

### <a name="description"></a>Description

이 서비스는 프롬프트 위젯의 텍스트를 설정합니다. GX_STYLE_TEXT_COPY 스타일을 사용하여 생성된 프롬프트 위젯은 할당된 텍스트 문자열의 프라이빗 복사본을 만듭니다. GX_STYLE_TEXT_COPY가 활성 상태가 아니면 위젯이 들어오는 문자열의 프라이빗 복사본을 만들지 않으므로 문자열을 정적이나 전역으로 할당해야 합니다. 즉, 자동 또는 임시 변수를 사용할 수 없습니다.

GX_PROMPT는 GX_WIDGET에서 파생되므로 GX_PROMPT에서 gx_widget API 서비스를 모두 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **prompt** 프롬프트 위젯 제어 블록에 대한 포인터
- **text** 텍스트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 프롬프트 텍스트를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**(0x30) 메모리 할당 함수가 정의되어 있지 않습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING new_string;
new_string.gx_string_ptr = “my_text”;
new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Set the text of “my_prompt” to “new_string”. */
status = gx_prompt_text_set(&my_prompt, &new_string);

/* If status is GX_SUCCESS the text for “my_prompt” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_get

## <a name="gx_radial_progress_bar_anchor_set"></a>gx_radial_progress_bar_anchor_set


시작 각도 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_progress_bar_anchor_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar, 
    GX_VALUE angle);
```

### <a name="description"></a>Description

이 서비스는 방사형 진행률 표시줄의 시작 각도를 설정합니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 방사형 진행률 표시줄 제어 블록에 대한 포인터
- **angle** 원호의 시작 각도

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 진행률 표시줄 앵커를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_VALUE start_angle = 90;

/* Set the start angle of “my_progress_bar” to 90 degree. */
status = gx_radial_progress_bar_anchor_set(&my_progress_bar, start_angle);

/* If status is GX_SUCCESS the anchor value of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_background_draw"></a>gx_radial_progress_bar_background_draw


배경 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_radial_progress_bar_background_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Description

이 서비스는 방사형 진행률 표시줄 배경을 그립니다. gx_radial_progress_bar_draw 함수에서 내부적으로 참조되지만 애플리케이션이 사용자 지정 방사형 진행률 표시줄 그리기 함수를 정의하는 경우 애플리케이션에서 사용할 수 있도록 노출됩니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 방사형 진행률 표시줄 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom radial progress bar drawing function. */

VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Call default radial progress bar background draw. */
    gx_radial_progress_bar_background_draw(radial_progress);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```
### <a name="see-also"></a>참고 항목

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_create"></a>gx_radial_progress_bar_create


방사형 진행률 표시줄 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_progress_bar_create(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RADIAL_PROGRESS_BAR_INFO *info,
    ULONG style
    USHORT id);
```

### <a name="description"></a>Description

이 서비스는 방사형 진행률 표시줄을 만듭니다.

위젯 스타일 GX_STYLE_ENABLED가 적용된 진행률 표시줄은 진행률 표시줄 현재 값을 수정하는 pen_down, pen_drag, pen_up 입력을 수락합니다.

위젯 스타일 GX_STYLE_PROGRESS_TEXT_DRAW를 사용하여 진행률 표시줄 영역 내에서 진행률 표시줄 값을 텍스트로 그릴 수 있도록 설정할 수 있습니다. 이 스타일을 GX_STYLE_PROGRESS_PERCENT 스타일과 함께 사용하면 진행률 표시줄 값이 백분율로 표시됩니다. 그러지 않으면 진행률 표시줄 값이 현재 각도 값으로 표시됩니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 방사형 진행률 표시줄 제어에 대한 포인터
- **progress_bar** 방사형 진행률 표시줄 제어 블록에 대한 포인터
- **name** 방사형 진행률 표시줄의 이름
- **parent** 부모 위젯에 대한 포인터
- **info** GX_RADIAL_PROGRESS_BAR 구조체에 대한 포인터입니다. **부록 I** 에는 GX_RADIAL_PROGRESS_BAR 구조체의 정의가 나와 있습니다.
- **style** 방사형 진행률 표시줄의 스타일
- **id** 애플리케이션에서 정의된 진행률 표시줄 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 진행률 표시줄을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_WIDGET**(0x12) 부모 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_RAIDAL_PROGRESS_BAR_INFO info;

info.gx_radial_progress_bar_info_xcenter = 200;
info.gx_radial_progress_bar_info_ycenter = 200;
info.gx_radial_progress_bar_info_radius = 100;
info.gx_radial_progress_bar_info_current_angle = 180;
info.gx_radial_progress_bar_info_anchor_val = -180;
info.gx_radial_progress_bar_info_font_id = GX_FONT_ID_SYSTEM;
info.gx_raidal_progress_bar_info_normal_text_color =
                                        GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_selected_text_color =
                                        GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_disabled_text_color =
                                        GX_COLOR_ID_DISABLED_TEXT;
info.gx_radial_progress_bar_info_normal_brush_width = 20;
info.gx_raidal_progress_bar_info_selected_brush_width = 16;
info.gx_radial_progress_bar_info_normal_brush_color =
                                        GX_COLOR_ID_WIDGET_FILL;
info.gx_radial_progress_bar_info_selected_brush_color =
                                        GX_COLOR_ID_SELECTED_FILL;

/* Create a radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_create(&my_progress_bar,
                    “my_progress_bar”, parent, &info,
                    GX_STYLE_ENABLED | GX_STYLE_TRANSPARENT |
                    GX_STYLE_PROGRESS_TEXT_DRAW,
                    ID_MY_RADIAL_PROGRESS);

/* If status is GX_SUCCESS the radial progress bar “my_progress_bar” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_draw"></a>gx_radial_progress_bar_draw


방사형 진행률 표시줄 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Description

이 서비스는 방사형 진행률 표시줄을 그립니다. gx_radial_progress_bar_create 함수에서 내부적으로 참조되지만 애플리케이션이 사용자 지정 방사형 진행률 표시줄 그리기 함수를 정의하는 경우 애플리케이션에서 사용할 수 있도록 노출됩니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 방사형 진행률 표시줄 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom radial progress bar drawing function. */

VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Call default radial progress bar draw. */
    gx_radial_progress_bar_draw(radial_progress);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```

### <a name="see-also"></a>참고 항목

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_size_calculate
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_event_process"></a>gx_radial_progress_bar_event_process


방사형 진행률 표시줄 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_progress_bar_event_process(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 방사형 진행률 표시줄 이벤트를 처리합니다. gx_radial_progress_bar_create 함수에서 내부적으로 참조되지만 애플리케이션이 사용자 지정 방사형 진행률 표시줄 이벤트 처리 함수를 정의하는 경우 애플리케이션에서 사용할 수 있도록 노출됩니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 방사형 진행률 표시줄 제어 블록에 대한 포인터
- **event_ptr** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 진행률 표시줄 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_RADIAL_PROGRESS_BAR *radial_progress, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
        case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_radial_progress_bar_event_process(
                            radial_progress, event_ptr);
        /* add my own handling here */
        break;
    default:
        status = gx_radial_progress_bar_event_process(
                            radial_progress, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_font_set"></a>gx_radial_progress_bar_font_set


방사형 진행률 표시줄 글꼴 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_progress_bar_font_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Description

이 서비스는 방사형 진행률 표시줄 위젯의 글꼴을 설정합니다. 위젯 스타일 GX_STYLE_PROGRESS_TEXT_DRAW가 설정되지 않은 경우에는 매개 변수가 적용되지 않습니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 방사형 진행률 표시줄 제어 블록에 대한 포인터
- **font_id** 글꼴의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 진행률 표시줄 글꼴을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set font for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_font_set(&my_progress_bar, font);

/* If status is GX_SUCCESS the font of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_info_set"></a>gx_radial_progress_bar_info_set


방사형 진행률 표시줄 정보 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_progress_bar_info_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RADIAL_PROGRESS_BAR_INFO *info);
```

### <a name="description"></a>Description

이 서비스는 방사형 진행률 표시줄에 할당된 정보 매개 변수를 다시 설정합니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 방사형 진행률 표시줄 제어 블록에 대한 포인터
- **info** 방사형 진행률 표시줄 정보 구조체에 대한 포인터입니다. **부록 I** 에는 GX_RADIAL_PROGRESS_BAR_INFO 구조체의 정의가 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 진행률 표시줄 정보를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_RAIDAL_PROGRESS_BAR_INFO info;

info.gx_radial_progress_bar_info_xcenter = 200;
info.gx_radial_progress_bar_info_ycenter = 200;
info.gx_radial_progress_bar_info_radius = 100;
info.gx_radial_progress_bar_info_current_angle = 180;
info.gx_radial_progress_bar_info_anchor_val = -180;
info.gx_radial_progress_bar_info_font_id = GX_FONT_ID_SYSTEM;
info.gx_raidal_progress_bar_info_normal_text_color =
                                GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_selected_text_color =
                                GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_disabled_text_color =
                                GX_COLOR_ID_DISABLED_TEXT;
info.gx_radial_progress_bar_info_normal_brush_width = 20;
info.gx_raidal_progress_bar_info_selected_brush_width = 16;
info.gx_radial_progress_bar_info_normal_brush_color =
                                GX_COLOR_ID_WIDGET_FILL;
info.gx_radial_progress_bar_info_selected_brush_color =
                                GX_COLOR_ID_SELECTED_FILL;

/* Set appearance information for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_info_set(&my_progress_bar, &info);

/* If status is GX_SUCCESS the appearance information of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_text_color_set"></a>gx_radial_progress_bar_text_color_set


방사형 진행률 표시줄 텍스트 색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_progress_bar_text_color_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCE_ID disabled_text_color);
```

### <a name="description"></a>Description

이 서비스는 방사형 진행률 표시줄의 텍스트 색을 설정합니다. 이 값은 GX_STYLE_PROGRESS_TEXT_DRAW 스타일이 설정된 경우에만 사용됩니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 방사형 진행률 표시줄 제어 블록에 대한 포인터
- **normal_color** 정상 상태인 텍스트 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **selected_color** 위젯에 포커스가 있는 경우 텍스트 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **disabled_color** GX_STYLE_ENABLED 스타일이 설정되지 않은 경우 텍스트 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 진행률 표시줄 텍스트 색을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯 검사가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set text color for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_text_color_set(&my_progress_bar,
                            GX_COLOR_ID_NORMAL_TEXT,
                            GX_COLOR_ID_SELECTED_TEXT,
                            GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_text_draw"></a>gx_radial_progress_bar_text_draw


방사형 진행률 표시줄 텍스트 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_radial_progress_bar_text_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Description

이 서비스는 지정된 방사형 진행률 표시줄의 텍스트를 그립니다. gx_radial_progress_bar_draw()의 일부로 내부적으로 호출되지만 애플리케이션이 사용자 지정 진행률 표시줄 그리기 함수를 정의하는 경우를 지원하기 위해 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 방사형 진행률 표시줄 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Draw text for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_text_draw (&my_progress_bar);

/* If status is GX_SUCCESS the text of “my_progress_bar” has been drawn. */

/* Write a custom radial progress bar drawing function. */
VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Add your own background draw here. */

    /* Call default radial progress bar text draw. */
    gx_radial_progress_bar_text_draw(radial_progress);

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```

### <a name="see-also"></a>참고 항목

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_value_set"></a>gx_radial_progress_bar_value_set


방사형 진행률 표시줄 값 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_progress_bar_value_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar, 
    GX_VALUE value);
```

### <a name="description"></a>Description

이 서비스는 방사형 진행률 표시줄 값을 설정합니다. 할당된 값은 진행률 표시줄 현재 위치의 가능한 각도 값 범위를 정의하는 [-360, 360] 범위로 제한됩니다. 애플리케이션은 표시되는 실제 값을 스케일링하여 진행률 표시줄 위젯에 각도 값을 할당해야 합니다.

현재 값이 위쪽 원호의 엔드포인트와 앵커 위치 사이의 각도 델타를 나타내도록 진행률 표시줄이 그려집니다. 음수 값을 사용하면 앵커 위치에서 시작하여 시계 방향으로 원호가 그려집니다. 현재 값이 양수이면 앵커 위치에서 시작하여 시계 반대 방향으로 원호가 그려집니다.

예를 들어 원호의 위쪽(12시 위치)에서 시작하고 오른쪽(3시 위치)에서 끝나는 원호를 그리려면 앵커 값 90도, 현재 값 -90도를 할당합니다.

### <a name="parameters"></a>매개 변수

- **progress_bar** 방사형 진행률 표시줄 제어 블록에 대한 포인터
- **value** 새 진행률 표시줄 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 진행률 표시줄 값을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_VALUE new_value = 180;

/* Set value for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_value_set(&my_progress_bar,
                                        new_value);

/* If status is GX_SUCCESS the value of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw

## <a name="gx_radio_button_create"></a>gx_radio_button_create


라디오 단추 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_radio_button_create(
    GX_RADIO_BUTTON *button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, ULONG style,
    USHORT radio_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 라디오 단추 위젯을 만듭니다. GX_RADIO_BUTTON은 GX_TEXT_BUTTON에서 파생되므로 gx_text_button 서비스도 이 위젯 형식에서 모두 지원됩니다.

### <a name="parameters"></a>매개 변수

- **button** 라디오 단추 컨트롤 블록에 대한 포인터
- **name** 라디오 단추 위젯의 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **text_id** 라디오 단추의 리소스 ID
- **style** 라디오 단추의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **radio_button_id** 애플리케이션에서 정의된 라디오 단추 ID
- **size** 라디오 단추의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 라디오 단추를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create “my_radio_button”. */
status = gx_radio_button_create(&my_radio_button, “my_radio_button”, &my_parent,
                    MY_RADIO_BUTTON_TEXT_RESOURCE_ID,
                    GX_STYLE_BORDER_RAISED, MY_RADIO_BUTTON_ID, &size);

/* If status is GX_SUCCESS the radio button “my_radio_button” has been created. */
```
### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_draw

## <a name="gx_radio_button_draw"></a>gx_radio_button_draw


라디오 단추 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_radio_button_draw(GX_RADIO_BUTTON *button);
```

### <a name="description"></a>Description

이 서비스는 라디오 단추 위젯을 그립니다. GUIX 캔버스 새로 고침을 통해 내부적으로 호출되지만 재정의된 그리기 함수에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **button** 라디오 단추 위젯 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom radio button drawing function. */

VOID my_radio_button_draw(GX_RADIO_BUTTON *radio_button)
{
    /* Call default radio button draw. */
    gx_radio_button_draw(radio_button);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radio_button);
}
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_create

## <a name="gx_radio_button_pixelmap_set"></a>gx_radio_button_pixelmap_set


라디오 단추의 pixelmap 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_radio_button_pixelmap_set(
    GX_RADIO_BUTTON *button,
    GX_RESOURCE_ID off_id,
    GX_RESOURCE_ID on_id,
    GX_RESOURCE_ID off_disabled_id,
    GX_RESOURCE_ID on_disabled_id);
```

### <a name="description"></a>Description

이 서비스는 지정된 라디오 단추에서 각 단추 상태에 대해 표시할 pixelmap을 할당합니다. 리소스 ID는 중복될 수 있습니다.

### <a name="parameters"></a>매개 변수

- **off_id** 라디오 단추 꺼짐 상태에 사용되는 pixelmap
- **on_id** 라디오 단추 켜짐 상태에 사용되는 pixelmap
- **off_disabled_id** 라디오 단추 사용 안 함 및 꺼짐 상태에 사용되는 pixelmap
- **on_disabled_id** 라디오 단추 사용 안 함 및 켜짐 상태에 사용되는 pixelmap

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 라디오 단추 pixelmap을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set pixelmap for “my_radio_button”. */
status = gx_radio_button_pixelmap_set(&my_radio_button,
                                MY_OFF_PIXELMAP,
                                MY_ON_PIXELMAP,
                                MY_OFF_DISABLED_PIXELMAP,
                                MY_ON_DISABLED_PIXELMAP);

/* If status is GX_SUCCESS the pixelmaps for radio button “my_radio_button” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_create

## <a name="gx_radial_slider_anchor_angles_set"></a>gx_radial_slider_anchor_angles_set


방사형 슬라이더 앵커 목록 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_slider_anchor_angles_set(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE *anchor_angles, 
    USHORT anchor_count);
```

### <a name="description"></a>Description

이 서비스는 방사형 슬라이더의 앵커 각도를 설정합니다. 앵커 각도 목록이 설정된 경우 방사형 슬라이더 각도는 정의된 앵커 각도 중 하나입니다.

### <a name="parameters"></a>매개 변수

- **slider** 방사형 슬라이더 제어 블록
- **anchor_angles** 설정할 각도 목록
- **anchor_count** 앵커 각도 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 앵커 각도를 설정했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 앵커 목록이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_VALUE anchor_angles[]={0, 30, 60, 90, 120, 150, 180};
USHORT anchor_count = 7;

/* Set anchor angles for radial slider. */
status = gx_radial_slider_anchor_angles_set(&my_radial_slider,
                                anchor_angles, anchor_count);

/* If status is GX_SUCCESS the anchor angles have been set for “my_radial_slider”. */

/* Set anchor angles for radial slider. */
status = gx_radial_slider_anchor_angles_set(&my_radial_slider,
                                GX_NULL, 0);

/* If status is GX_SUCCESS the anchor angles have been removed from “my_radial_slider”. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_angle_set"></a>gx_radial_slider_angle_set

방사형 슬라이더 각도 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_slider_angle_set(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE new_angle);
```

### <a name="description"></a>Description

이 서비스는 방사형 슬라이더의 새 각도 값을 설정합니다.

### <a name="parameters"></a>매개 변수

- **slider** 방사형 슬라이더 제어 블록에 대한 포인터
- **new_angle** 설정할 새 각도 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 슬라이더 각도를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set “my_radial_slider” angle to 0 degree(3 o’clock position). */
status = gx_radial_slider_angle_set(&my_radial_slider, 0);

/* If status is GX_SUCCESS the value of “my_radial_slider” has been set to 0 degree. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_animation_set"></a>gx_radial_slider_animation_set


방사형 슬라이더 애니메이션 정보 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_slider_animation_set(
    GX_RADIAL_SLIDER *slider,
    USHORT steps, USHORT delay, 
    USHORT animation_style,
    VOID (*animation_update_callback)(GX_RADIAL_SLIDER *slider));
```

### <a name="description"></a>Description

이 서비스는 방사형 슬라이더 바늘 애니메이션의 애니메이션 단계, 지연 시간, 애니메이션 스타일을 설정합니다.

### <a name="parameters"></a>매개 변수

- **slider** 방사형 슬라이더 제어 블록에 대한 포인터
- **steps** 한 애니메이션의 총 단계
- **delay** 각 애니메이션 단계의 지연 시간
- **animation_style** 다음과 같은 감속/가속 함수 유형
  - GX_ANIMATION_BACK_EASE_IN
  - GX_ANIMATION_BACK_EASE_OUT
  - GX_ANIMATION_BACK_EASE_IN_OUT
  - GX_ANIMATION_BOUNCE_EASE_IN
  - GX_ANIMATION_BOUNCE_EASE_OUT
  - GX_ANIMATION_BOUNCE_EASE_IN_OUT
  - GX_ANIMATION_CIRC_EASE_IN
  - GX_ANIMATION_CIRC_EASE_OUT
  - GX_ANIMATION_CIRC_EASE_IN_OUT
  - GX_ANIMATION_CUBIC_EASE_IN
  - GX_ANIMATION_CUBIC_EASE_OUT
  - GX_ANIMATION_CUBIC_EASE_IN_OUT
  - GX_ANIMATION_ELASTIC_EASE_IN
  - GX_ANIMATION_ELASTIC_EASE_OUT
  - GX_ANIMATION_ELASTIC_EASE_IN_OUT
  - GX_ANIMATION_EXPO_EASE_IN
  - GX_ANIMATION_EXPO_EASE_OUT
  - GX_ANIMATION_EXPO_EASE_IN_OUT
  - GX_ANIMATION_QUAD_EASE_IN
  - GX_ANIMATION_QUAD_EASE_OUT
  - GX_ANIMATION_QUAD_EASE_IN_OUT
  - GX_ANIMATION_QUART_EASE_IN
  - GX_ANIMATION_QUART_EASE_OUT
  - GX_ANIMATION_QUART_EASE_IN_OUT
  - GX_ANIMATION_QUINT_EASE_IN
  - GX_ANIMATION_QUINT_EASE_OUT
  - GX_ANIMATION_QUINT_EASE_IN_OUT
  - GX_ANIMATION_SINE_EASE_IN
  - GX_ANIMATION_SINE_EASE_OUT
  - GX_ANIMATION_SINE_EASE_IN_OUT
- **animation_update_callback** 각 애니메이션 단계 후에 호출되는 사용자 정의 콜백 함수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 슬라이더 애니메이션을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
VOID animation_callback(GX_RADIAL_SLIDER *slider)
{
    /* This function will be called after each animation step,
    add custom code here. */
}

/* Set animation info for “my_radial_slider”. */
status = gx_radial_slider_animation_set(&my_radial_slider, 15, 2,
                                GX_ANIMATION_CIRC_EASE_IN_OUT,
                                animation_callback);

/* If status is GX_SUCCESS the radial slider needle will move with specified animation. */

/* Disable animation for “my_radial_slider”. */
status = gx_radial_slider_animation_set(&my_radial_slider, 0, 0,
                                        0, 0);

/* If status is GX_SUCCESS the radial slider needle will move without animation. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_animation_start"></a>gx_radial_slider_animation_start


애니메이션을 사용하여 새 방사형 슬라이더 값 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_slider_animation_start(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE target_angle);
```

### <a name="description"></a>Description

이 서비스는 슬라이더 바늘을 현재 위치에서 지정된 위치로 이동하는 애니메이션을 시작합니다.

### <a name="parameters"></a>매개 변수

- **slider** 방사형 슬라이더 제어 블록에 대한 포인터
- **target_angle** 대상 각도 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 슬라이더 애니메이션을 시작했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Start an animation to move radial slider needle from
current position to 90 degree position. */
status = gx_radial_slider_animation_start(&my_radial_slider, 90);

/* If status is GX_SUCCESS the radial slider needle animation has been started. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_create"></a>gx_radial_slider_create


방사형 슬라이더 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_slider_create(
    GX_RADIAL_SLIDER *slider,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RADIAL_SLIDER_INFO *info,
    ULONG style,
    USHORT slider_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 방사형 슬라이더 위젯을 만듭니다.

### <a name="parameters"></a>매개 변수

- **slider** 방사형 슬라이더 제어 블록에 대한 포인터
- **name** 방사형 슬라이더 위젯의 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **info** 방사형 슬라이더 모양 정의. **부록 I** 에는 GX_RADIAL_SLIDER_INFO의 정의가 나와 있습니다.
- **style** 라디오 단추의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **radio_button_id** 애플리케이션에서 정의된 방사형 슬라이더 ID
- **size** 방사형 슬라이더의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 슬라이더를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 부모 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_RADIAL_SLIDER_INFO info;
GX_RECTANGLE size;

/* Distance from left side of widget to rotating center. */
info.gx_radial_slider_info_xcenter = 100;

/* Distance from top size of widget to rotating center. */
info.gx_radial_slider_info_ycenter = 100;

/* Radius of rotating circle. */
info.gx_radial_slider_info_radius = 100;

/* Widget of rotating track. */
info.gx_radial_slider_info_track_width = 40;

/* Current angle value. */
info.gx_radial_slider_info_current_angle = 0;

/* Minimum angle value. */
info.gx_radial_slider_min_anlge = -60;

/* Maximum angle value. */
info.gx_radial_slider_max_angle = 240;

/* Anchor value list. */
info.gx_radial_slider_angle_list = GX_NULL;

/* Anchor value count. */
info.gx_radial_slider_list_count = 0;

/* Resource ID of background pixelmap. */
info.gx_radial_slider_background_pixelmap = GX_PIXELMAP_ID_BKGRD;

/* Resource ID of needle pixelmap. */
info.gx_radial_slider_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Define widget size. */
gx_utility_rectangle_define(&size, 0, 0, 200, 200);

/* Create “my_radial_slider”. */
status = gx_radial_slider_create(&my_radial_slider,
                                “my_radial_slider”, &my_parent,
                                &info, GX_STYLE_ENABLED,
                                MY_RADIAL_SLIDER_ID, &size);

/* If status is GX_SUCCESS the radial slider “my_radial_slider” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_draw"></a>gx_radial_slider_draw


방사형 슬라이더 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_radial_slider_draw(GX_RADIAL_SLIDER *slider);
```

### <a name="description"></a>Description

이 서비스는 방사형 슬라이더를 그립니다. GUIX 캔버스 새로 고침을 통해 내부적으로 호출되지만 재정의된 그리기 함수에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **slider** 방사형 슬라이더 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom radio button drawing function. */

VOID my_radial_slider_draw(GX_RADIAL_SLIDER *radial_slider)
{
    /* Call default radial slider draw. */
    gx_radio_slider_draw(radial_slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_event_process"></a>gx_radial_slider_event_process


방사형 슬라이더 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_slider_event_process(
    GX_RADIAL_SLIDER *slider,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 방사형 슬라이더 이벤트를 처리합니다. 사용자 지정 방사형 슬라이더 이벤트 처리 함수에서 기본 이벤트 처리기로 호출되어야 합니다.

### <a name="parameters"></a>매개 변수

- **slider** 방사형 슬라이더 제어 블록에 대한 포인터
- **event_ptr** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 슬라이더 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Write a custom event processing function. */

UINT my_event_process(GX_RADIAL_SLIDER *slider,
                    GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_radial_slider_event_process(slider, event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_radial_slider_event_process(slider, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_info_get"></a>gx_radial_slider_info_get


방사형 슬라이더 정보 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_slider_info_get(
    GX_RADIAL_SLIDER *slider,
    GX_RADIAL_SLIDER_INFO **info);
```

### <a name="description"></a>Description

이 서비스는 방사형 슬라이더 정보 포인터를 검색합니다.

### <a name="parameters"></a>매개 변수

- **slider** 방사형 슬라이더 제어 블록에 대한 포인터
- **info** 검색된 방사형 슬라이더 정보 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 슬라이더 정보를 검색했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_RADIAL_SLIDER_INFO *info;

/* Retrive radial slider information structure. */
status = gx_radial_slider_info_get(&my_radial_slider,
                                    “my_radial_slider”, &info);

/* If status is GX_SUCCESS the radial slider information pointer of “my_radial_slider” has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_info_set"></a>gx_radial_slider_info_set


방사형 슬라이더 정보 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_slider_info_set(
    GX_RADIAL_SLIDER *slider,
    GX_RADIAL_SLIDER_INFO *info);
```

### <a name="description"></a>Description

이 서비스는 방사형 슬라이더 정보를 설정합니다.

### <a name="parameters"></a>매개 변수

- **slider** 방사형 슬라이더 제어 블록에 대한 포인터
- **info** 설정할 방사형 슬라이더 정보

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 슬라이더 정보를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_RADIAL_SLIDER_INFO info;

/* Distance from left side of widget to rotating center. */
info.gx_radial_slider_info_xcenter = 100;

/* Distance from top size of widget to rotating center. */
info.gx_radial_slider_info_ycenter = 100;

/* Radius of rotating circle. */
info.gx_radial_slider_info_radius = 100;

/* Widget of rotating track. */
info.gx_radial_slider_info_track_width = 40;

/* Current angle value. */
info.gx_radial_slider_info_current_angle = 0;

/* Minimum angle value. */
info.gx_radial_slider_min_anlge = -60;

/* Maximum angle value. */
info.gx_radial_slider_max_angle = 240;

/* Anchor value list. */
info.gx_radial_slider_angle_list = GX_NULL;

/* Anchor value count. */
info.gx_radial_slider_list_count = 0;

/* Resource ID of background pixelmap. */
info.gx_radial_slider_background_pixelmap = GX_PIXELMAP_ID_BKGRD;

/* Resource ID of needle pixelmap. */
info.gx_radial_slider_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Reset radial slider info for “my_radial_slider”. */
status = gx_radial_slider_info_set(&my_radial_slider, &info);

/* If status is GX_SUCCESS the radial slider info of “my_radial_slider” has been reset. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_pixelmap_set"></a>gx_radial_slider_pixelmap_set


방사형 슬라이더 pixelmap 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_radial_slider_pixelmap_set(
    GX_RADIAL_SLIDER *slider,
    GX_RESOURCE_ID background_pixemap,
    GX_REOUSRCE_ID needle_pixelmap);
```

### <a name="description"></a>Description

이 서비스는 방사형 슬라이더 배경 및 바늘 pixelmap을 설정합니다.

### <a name="parameters"></a>매개 변수

- **slider** 방사형 슬라이더 제어 블록에 대한 포인터
- **background_pixelmap** 배경 pixelmap의 리소스 ID
- **needle_pixelmap** 바늘 pixelmap의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 방사형 슬라이더 pixelmap을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create “my_radio_button”. */
status = gx_radial_slider_pixelmap_set(&my_radial_slider, GX_PIXELMAP_ID_BG, GX_PIXELMAP_ID_NEEDLE);

/* If status is GX_SUCCESS the background and needle pixelmap of “my_radial_slider” has been reset. */
```

### <a name="see-also"></a>참고 항목

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set

## <a name="gx_rich_text_view_create"></a>gx_rich_text_view_create

서식 있는 텍스트 뷰 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_rich_text_view_create(
    GX_RICH_TEXT_VIEW *text_view,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    GX_RICH_TEXT_FONTS *fonts,
    USHORT id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 지정된 대로 서식 있는 텍스트 뷰를 만듭니다.


**서식 지정 태그는 텍스트의 특수 형식을 표시하는 데 사용됩니다.**

- **\<b>\</b>** 사용자 지정 굵은 글꼴 ID를 사용하여 텍스트 글꼴 설정
- **\<i>\</i>** 사용자 지정 기울임꼴 ID를 사용하여 텍스트 글꼴 설정
- **\<u>\</u>** 텍스트 밑줄 사용
- **\<f GX_FONT_ID>\</f>** 지정된 글꼴 ID를 사용하여 텍스트 글꼴 설정
- **\<c GX_COLOR_ID>\</c>** 지정된 색 ID를 사용하여 텍스트 글꼴 설정
- **\<hc GX_COLOR_ID>\</hc>** 지정된 색 ID를 사용하여 텍스트 강조 색 설정
- **\<align left/right/center>\</align>** 텍스트 맞춤 설정

**서식 지정 태그 사용 예:**

- \<b>굵은 글꼴 텍스트입니다.<\b>
- \<i>기울임꼴 텍스트입니다.<\i>
- \<u>밑줄이 있는 텍스트입니다.<\u>
- \<f 0>텍스트 글꼴 ID가 0으로 설정되었습니다.<\f>
- \<c 1>텍스트 색 ID가 1로 설정되었습니다.<\c>
- \<hc 2>텍스트 강조 색 ID가 2로 설정되었습니다.<\hc>
- \<align left> 텍스트가 왼쪽 맞춤되었습니다.<\align>

### <a name="parameters"></a>매개 변수

- **text_view** 서식 있는 텍스트 뷰 제어 블록에 대한 포인터
- **name** 서식 있는 텍스트 뷰의 이름
- **parent** 부모 위젯에 대한 포인터
- **text_id** 텍스트 문자열의 리소스 ID
- **fonts** 서식 있는 텍스트 뷰 글꼴 정보에 대한 포인터입니다. **부록 I** 에는 GX_RICH_TEXT_FONTS 구조체의 정의가 나와 있습니다.
- **style** 위젯의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **id** 애플리케이션에서 정의된 서식 있는 텍스트 뷰 ID
- **size** 서식 있는 텍스트 뷰의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 서식 있는 텍스트 뷰를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_RICH_TEXT_VIEW rich_view;
GX_RCIH_TEXT_FONTS fonts;
GX_RECTANGLE size;

/* Defined widget size. */
gx_utility_rectangle_define(&size, 100, 100, 300, 150);

/* Define font information. */
fonts.gx_rich_text_fonts_normal_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_italic_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_italic_id = GX_FONT_ID_SYSTEM;

/* Create rich text view widget. */
status = gx_rich_text_view_create(&rich_view, “my_rich_view”,
                                  parent, GX_STRING_ID_TEST_STRING,
                                  &fonts,
                                  GX_STYLE_ENABLED,
                                  MY_RICH_VIEW_ID, &size);

/* If status is GX_SUCCESS the rich text view was successfully created. */

```

GUIX Studio 설치의 일부로 제공되는 데모 애플리케이션 demo_guix_widget_types는 서식 있는 텍스트 뷰 위젯을 사용하는 전체 예제를 제공합니다.

### <a name="see-also"></a>참고 항목

- gx_rich_text_view_draw
- gx_rich_text_view_fonts_set
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_draw"></a>gx_rich_text_view_draw


서식 있는 텍스트 뷰 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view);
```

### <a name="description"></a>Description

이 서비스는 지정된 서식 있는 텍스트 뷰 위젯을 그립니다. 일반적으로 캔버스 새로 고침 작업의 일부로 GUIX에서 내부적으로 호출되지만 사용자 지정 그리기 함수를 제공하고 기본 서식 있는 텍스트 뷰 그리기를 사용자 지정 그리기 기준으로 호출하려는 애플리케이션에도 노출됩니다.

### <a name="parameters"></a>매개 변수

- **text_view** 서식 있는 텍스트 뷰 위젯 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom rich text view drawing function. */

VOID my_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view)
{
    /* Call default rich text view draw. */
    gx_rich_text_view_draw(text_view);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_rich_text_view_create
- gx_rich_text_view_fonts_set
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_fonts_set"></a>gx_rich_text_view_fonts_set

서식 있는 텍스트 뷰 글꼴 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_rich_text_view_fonts_set(GX_RICH_TEXT_VIEW *text_view, GX_RICH_TEXT_FONTS *fonts);
```

### <a name="description"></a>Description

이 서비스는 서식 있는 텍스트 뷰 위젯의 글꼴을 설정합니다.

### <a name="parameters"></a>매개 변수

- **text_view** 서식 있는 텍스트 뷰 위젯 제어 블록에 대한 포인터
- **fonts** 서식 있는 텍스트 뷰 글꼴 정보에 대한 포인터입니다. **부록 I** 에는 GX_RICH_TEXT_FONTS 구조체의 정의가 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 서식 있는 텍스트 뷰 글꼴을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_RICH_TEXT_FONTS fonts;

/* Replace the font ids as needed. */
fonts.gx_rich_text_fonts_normal_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_italic_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_italic_id = GX_FONT_ID_SYSTEM;

/* Set the font of “my_rich_view”. */
status = gx_rich_text_view_fonts_set(&my_rich_view, &fonts);

/* If status is GX_SUCCESS the font for rich text view “my_rich_view” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_rich_text_view_create
- gx_rich_text_view_draw
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_text_draw"></a>gx_rich_text_view_text_draw


서식 있는 텍스트 뷰 텍스트 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_rich_text_view_text_draw(GX_RICH_TEXT_VIEW *text_view);
```

### <a name="description"></a>Description

이 지원 함수는 서식 있는 텍스트 뷰의 텍스트 부분을 그립니다. gx_rich_text_view_draw()에서 내부적으로 호출되며, 사용자 지정 서식 있는 텍스트 뷰 그리기 함수를 정의하는 애플리케이션의 편의를 위해 별도의 API로 제공됩니다. 서식 있는 텍스트 뷰 배경 그리기를 사용자 지정하려는 애플리케이션은 사용자 지정 그리기 함수를 제공하고 사용자 지정 그리기의 일부로 gx_rich_text_view_text_draw 서비스를 호출하여 배경에 서식 있는 텍스트 뷰 텍스트를 그릴 수 있습니다.

### <a name="parameters"></a>매개 변수

- **text_view** 서식 있는 텍스트 뷰 위젯 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom rich text view drawing function. */

VOID my_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view)
{
    /* Insert code here to draw rich text view background. */

    /* Call support function to do text drawing. */
    gx_rich_text_view_text_draw();

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *) rich_text_view);
}
```

### <a name="see-also"></a>참고 항목

- gx_rich_text_view_create
- gx_rich_text_view_draw
- gx_rich_text_view_fonts_set

## <a name="gx_screen_stack_create"></a>gx_screen_stack_create


화면 스택 초기화

### <a name="prototype"></a>프로토타입

```C
UINT gx_screen_stack_create(
    GX_SCREEN_STACK_CONTROL *control,
    GX_WIDGET **memory_buffer, 
    INT buffer_size);
```

### <a name="description"></a>Description

이 서비스는 화면 스택을 초기화합니다. 애플리케이션에서 화면 스택 기능을 구현하는 데 사용되는 메모리 블록 및 버퍼 크기를 정의해야 합니다.

> [!NOTE]
> 이 API는 사용되지 않으며 gx_system_screen_stack_create()로 대체되었습니다. 이 버전은 이전 라이브러리 릴리스와의 호환성을 위해서만 제공됩니다.

### <a name="parameters"></a>매개 변수

- **control** 화면 스택 제어 블록
- **memory_buffer** 화면 스택으로 사용되는 메모리 버퍼에 대한 포인터
- **buffer_size** 메모리 크기(바이트)

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 화면 스택을 만들었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 버퍼 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
#define SCREEN_STACK_SIZE 10

GX_SCREEN_STACK_CONTROL my_stack_control;
GX_WIDGET *screen_stack[SCREEN_STACK_SIZE];

/* Initialize “my_stack_control”. */
status = gx_screen_stack_create(&my_stack_control, screen_stack,
                        SCREEN_STACK_SIZE * sizeof(GX_WIDGET *));

/* If status is GX_SUCCESS the screen control block “my_stack control” has been initialized. */
```

### <a name="see-also"></a>참고 항목

- gx_screen_stack_push
- gx_screen_stack_pop
- gx_screen_stack_reset

## <a name="gx_screen_stack_pop"></a>gx_screen_stack_pop


화면 스택에서 맨 위에 있는 항목 제거

### <a name="prototype"></a>프로토타입

```C
UINT gx_screen_stack_pop(GX_SCREEN_STACK_CONTROL *control);
```

### <a name="description"></a>Description

이 서비스는 화면 스택에서 맨 위에 있는 항목을 제거하고 팝된 화면을 이전 부모에 연결합니다. 또한 부모에서 기존 자식을 모두 분리합니다.

> [!NOTE]
> 이 API는 사용되지 않으며 gx_system_screen_stack_pop()으로 대체되었습니다. 이 버전은 이전 라이브러리 릴리스와의 호환성을 위해서만 제공됩니다.

### <a name="parameters"></a>매개 변수

- **control** 화면 스택 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 화면 스택을 팝했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Remove the topmost entry from the screen stack. */
status = gx_screen_stack_pop(&my_stack_control);

/* If status is GX_SUCCESS the topmost entry has been removed from the screen stack, 
    and the popped screen has been attached to its parent. */
```

### <a name="see-also"></a>참고 항목

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_reset

## <a name="gx_screen_stack_push"></a>gx_screen_stack_push


화면 및 해당 부모를 스택으로 푸시

### <a name="prototype"></a>프로토타입

```C
UINT gx_screen_stack_push(
    GX_SCREEN_STACK_CONTROL *control,
    GX_WIDGET *screen,
    GX_WIDGET *new_screen);
```

### <a name="description"></a>Description

이 서비스는 부모에서 화면을 분리하고 화면 포인터 및 부모 포인터를 화면 스택으로 푸시합니다. 그런 다음 새 화면 포인터가 부모에 연결됩니다.


> [!NOTE]
> 이 API는 사용되지 않으며 gx_system_screen_stack_pop()으로 대체되었습니다. 이 버전은 이전 라이브러리 릴리스와의 호환성을 위해서만 제공됩니다.

### <a name="parameters"></a>매개 변수

- **control** 화면 스택 제어 블록
- **screen** 푸시할 화면 포인터
- **new_screen** 새 화면의 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 화면 스택을 푸시했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Push “screen” and its parent to screen stack, Dettach “screen” from its parent, and attach “new screen” to the parent. */
status = gx_screen_stack_push(&my_stack_control,
                                screen, new_screen);

/* If status is GX_SUCCESS the widget “screen” and its parent have been pushed to screen stack, “screen” has been detached from its parent, “new_screen” has been attached to the parent. */
```

### <a name="see-also"></a>참고 항목

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_reset

## <a name="gx_screen_stack_reset"></a>gx_screen_stack_reset


화면 스택에서 모든 항목 제거

### <a name="prototype"></a>프로토타입

```C
UINT gx_screen_stack_reset(GX_SCREEN_STACK_CONTROL *control);
```

### <a name="description"></a>Description

이 서비스는 화면 스택에서 모든 항목을 제거합니다.

> [!NOTE]
> 이 API는 사용되지 않으며 gx_system_screen_stack_pop()으로 대체되었습니다. 이 버전은 이전 라이브러리 릴리스와의 호환성을 위해서만 제공됩니다.

### <a name="parameters"></a>매개 변수

- **control** 화면 스택 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 썸을 만들었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Remove all enteries from the screen stack. */
status = gx_screen_stack_reset(&my_stack_control);

/* If status is GX_SUCCESS all entries of screen stack has been removed. */
```

### <a name="see-also"></a>참고 항목

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_pop

## <a name="gx_scroll_thumb_create"></a>gx_scroll_thumb_create


스크롤 썸 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_scroll_thumb_create(
    GX_SCROLL_THUMB *scroll_thumb,
    GX_SCROLLBAR *parent, ULONG style);
```

### <a name="description"></a>Description

이 서비스는 스크롤 썸휠을 만듭니다. 일반적으로 GX_SCROLLBAR를 만들 때 내부적으로 호출되지만 사용자 지정 스크롤 막대 구현을 허용하기 위해 공개됩니다.

### <a name="parameters"></a>매개 변수

- **scroll_thumb** 스크롤 썸 위젯 제어 블록
- **parent** 부모 스크롤 막대에 대한 포인터
- **style** 스크롤 막대 위젯의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 썸을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 부모 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_SCROLL_THUMB my_scroll_thumb;

/* Create scroll thumb “my_scroll_thumb”. */
status = gx_scroll_thumb_create(&my_scroll_thumb, &my_scrollbar,
                                GX_STYLE_NONE);

/* If status is GX_SUCCESS the scroll thumb “my_scroll_thumb” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_scroll_thumb_draw
- gx_scroll_thumb_event_process

## <a name="gx_scroll_thumb_draw"></a>gx_scroll_thumb_draw


스크롤 썸 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_scroll_thumb_draw(GX_SCROLL_THUMB *scroll_thumb);
```

### <a name="description"></a>Description

이 서비스는 스크롤 썸휠을 그립니다. GUIX 캔버스 새로 고침을 통해 내부적으로 호출되지만 재정의된 그리기 함수에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **scroll_thumb** 스크롤 썸 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom scroll thumb drawing function. */

VOID my_scroll_thumb_draw(GX_SCROLL_THUMB *thumb)
{
    /* Call default scroll thumb draw. */
    gx_scroll_thumb_draw(thumb);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_scroll_thumb_create
- gx_scroll_thumb_event_process

## <a name="gx_scroll_thumb_event_process"></a>gx_scroll_thumb_event_process


스크롤 썸 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_scroll_thumb_event_process(
    GX_SCROLL_THUMB *scroll_thumb,
    GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 스크롤 막대 썸휠에 전송된 이벤트를 처리합니다. 일반적으로 GUIX에서 내부적으로 사용되지만 사용자 지정 스크롤 막대 동작을 구현하는 데 도움이 되도록 공개됩니다.

### <a name="parameters"></a>매개 변수

- **scroll_thumb** 스크롤 썸 위젯 제어 블록
- **event** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 썸 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_SCROLL_THUMB *thumb, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_scroll_thumb_event_process(thumb, event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_scroll_thumb_event_process(thumb, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_scroll_thumb_create
- gx_scroll_thumb_draw

## <a name="gx_scroll_wheel_create"></a>gx_scroll_wheel_create


기준 스크롤 휠 위젯 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_scroll_wheel_create( 
    GX_SCROLL_WHEEL *wheel, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    INT total_rows, 
    ULONG style,
    USHORT id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 제네릭 스크롤 휠 위젯을 만듭니다.

제네릭 스크롤 휠은 *gx_numeric_scroll_wheel*** 및 *gx_string_ scroll_wheel***의 기준인 *gx_text_scroll_wheel***을 포함하여 모든 스크롤 휠 위젯 형식의 기준 위젯입니다. 기준 스크롤 휠 위젯은 모든 스크롤 휠 위젯 형식에 대한 이벤트 처리, 스크롤 애니메이션, 선택된 행 계산을 제공합니다.

애플리케이션에서는 일반적으로 제네릭 스크롤 휠 위젯 인스턴스를 만들지 않습니다. 이 위젯 형식은 그리기 함수를 제공하지 않기 때문입니다. 그러나 사용자 지정 스크롤 휠 위젯 형식을 만들어야 하는 애플리케이션을 지원하기 위해 이 API에 대한 액세스가 제공됩니다.

GX_SCROLL_WHEEL은 GX_WINDOW를 기반으로 하므로 GX_SCROLL_WHEEL 및 GX_SCROLL_WHEEL에서 파생된 위젯에서 GX_WINDOW API를 모두 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **wheel** 제네릭 스크롤 휠 제어 블록에 대한 포인터
- **name** 애플리케이션에서 할당된 위젯 이름
- **parent** 부모 위젯 또는 GX_NULL
- **total_rows** 사용 가능한 행의 총수
- **style** 위젯 스타일 플래그
- **id** 애플리케이션에서 할당된 위젯 ID
- **size** 초기 위젯 크기를 정의하는 사각형

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 휠을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_SIZE**(0x19) 제어 블록 크기가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_WIDGET**(0x12) 부모 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Call generic create function during custom widget createl. */

UINT custom_scroll_wheel_create(CUSTOM_SCROLL_WHEEL *wheel,
                    GX_CONST GX_CHAR *name,
                    GX_WIDGET *parent,
                    INT total_rows, ULONG style,
                    USHORT id,
                    GX_CONST GX_RECTANGLE *size)
{
    /* create base widget as part of custom create */
    status = gx_scroll_wheel_create(wheel, name, parent,
                            total_rows, style, id, size);

    /* If status is GX_SUCCESS the base scroll wheel has been created. */
}
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_event_process"></a>gx_scroll_wheel_event_process


제네릭 스크롤 휠 위젯에 대한 이벤트 처리 함수

### <a name="prototype"></a>프로토타입

```C
UINT gx_scroll_wheel_event_process(
    GX_SCROLL_WHEEL *wheel,
    GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 모든 스크롤 휠 위젯 형식에 대한 기본 입력 이벤트 처리를 제공합니다.

사용자 지정 스크롤 휠 위젯 형식을 만들어야 하는 애플리케이션을 지원하기 위해 애플리케이션 소프트웨어에 노출됩니다. 애플리케이션에서 자체 이벤트 처리 함수를 제공하는 경우도 많지만 사용자 지정할 필요가 없는 이벤트의 경우 휠 위젯에 대한 제네릭 이벤트 처리를 호출합니다.

### <a name="parameters"></a>매개 변수

- **wheel** 제네릭 스크롤 휠 제어 블록에 대한 포인터
- **event** GX_EVENT 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 휠 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Call generic scroll wheel event processing 
    as part of custom event processing function. */

UINT custom_scroll_wheel_event_process(CUSTOM_SCROLL_WHEEL *wheel,
                    GX_EVENT *event)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;

    default:
        /* pass all other events to the generic scroll wheel
            event processing */
        gx_scroll_wheel_event_process(wheel, event);
        break;
    }
}
```


### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_gradient_alpha_set"></a>gx_scroll_wheel_gradient_alpha_set


선택적 오버레이 그라데이션의 그라데이션 알파 값 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_scroll_wheel_gradient_alpha_set(
    GX_SCROLL_WHEEL *wheel,
    GX_UBYTE start_alpha,
    GX_UBYTE end_alpha);
```

### <a name="description"></a>Description

이 서비스는 스크롤 휠 위젯의 선택적 그라데이션 오버레이에 대한 시작 및 끝 알파 값을 정의합니다.

모든 스크롤 휠 위젯은 스크롤 휠 행의 “페이드” 효과를 스크롤 휠 위젯의 위쪽 및 아래쪽 가장자리 행으로 지원합니다. 스크롤 휠 행에 그라데이션 pixelmap을 그리면 페이드 효과를 얻을 수 있으며 스크롤 휠 위젯의 위쪽 및 아래쪽 근처에 행을 그릴 때 행이 페이드 아웃되는 것처럼 보입니다.

이 API 서비스를 사용하면 애플리케이션에서 페이드 효과 강도를 수정하거나 시작 및 끝 알파 값을 0으로 설정하여 효과를 완전히 사용하지 않도록 설정할 수 있습니다.

그라데이션 pixelmap은 스크롤 휠이 처음 표시될 때 런타임에 생성됩니다. 이렇게 하려면 gx_system_memory_allocator_set()을 사용하여 런타임 메모리 할당 서비스가 정의되어 있어야 합니다. 메모리 할당자 함수를 정의하지 않은 경우에는 그라데이션 이미지가 생성되지 않으며 페이드 효과를 사용할 수 없습니다.

### <a name="parameters"></a>매개 변수

- **wheel** 제네릭 스크롤 휠 제어 블록에 대한 포인터
- **start_alpha** 오버레이 그라데이션 시작 알파 값
- **end_alpha** 오버레이 그라데이션 끝 알파 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 휠 그라데이션 알파를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
status = gx_scroll_wheel_gradient_alpha_set(&wheel, 240, 0);
/* if status == GX_SUCCESS the wheel gradient alpha values were
Successfully assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_row_height_set"></a>gx_scroll_wheel_row_height_set


각 휠 행의 행 높이 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_scroll_wheel_row_height_set(
    GX_SCROLL_WHEEL *wheel,
    GX_VALUE row_height);
```

### <a name="description"></a>Description

이 서비스는 각 스크롤 휠 행의 행 높이를 할당합니다. 스크롤 휠이 GX_STYLE_TEXT_SCROLL_WHEEL_ROUND 스타일을 사용하는 경우 행이 휠의 위쪽 또는 아래쪽 가장자리에 가까워질수록 행 높이를 줄이는 변환이 행 높이에 적용됩니다.

### <a name="parameters"></a>매개 변수

- **wheel** 제네릭 스크롤 휠 제어 블록에 대한 포인터
- **row_height** 행 높이 값(픽셀)

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 휠 높이를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
status = gx_scroll_wheel_row_height_set(&wheel, 40);

/* if status == GX_SUCCESS the wheel row height has been set to 40
pixels. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_background_set"></a>gx_scroll_wheel_selected_background_set


선택된 휠 행의 배경 이미지 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_scroll_wheel_selected_background_set(
    GX_SCROLL_WHEEL*wheel, 
    GX_RESOURCE_ID image_id);
```

### <a name="description"></a>Description

이 서비스는 선택된 스크롤 휠 행 뒤에 그려지는 선택적 pixelmap ID를 할당합니다. 사용자가 선택된 스크롤 휠 행을 쉽게 구분할 수 있도록 선택된 행을 강조 표시하는 데 사용될 수 있습니다.

### <a name="parameters"></a>매개 변수

- **wheel** 제네릭 스크롤 휠 제어 블록에 대한 포인터
- **image_id** 선택된 행 배경 이미지로 사용할 pixelmap ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 휠 배경을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
status = gx_scroll_wheel_selected_background_set(&wheel,
GX_PIXELMAP_ID_SELECTED_ROW);

/* if status == GX_SUCCESS the background image has been
assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_get"></a>gx_scroll_wheel_selected_get


현재 선택된 휠 행 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_scroll_wheel_selected_get(
    GX_SCROLL_WHEEL *wheel,
    INT *row);
```

### <a name="description"></a>Description

이 서비스는 스크롤 휠을 쿼리하여 현재 선택된 행을 검색합니다. 호출자는 선택된 행 인덱스를 반환할 위치를 이 함수에 두 번째 매개 변수로 전달해야 합니다.

### <a name="parameters"></a>매개 변수

- **wheel** 제네릭 스크롤 휠 제어 블록에 대한 포인터
- **row** 선택된 행 값이 반환되는 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 선택된 휠 행을 검색했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x19) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
INT row;
status = gx_scroll_wheel_selected_get(&wheel, &row);

/* if status == GX_SUCCESS the selected row has been returned in
the row variable. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_set"></a>gx_scroll_wheel_selected_set


선택된 스크롤 휠 행 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_scroll_wheel_selected_set(
    GX_SCROLL_WHEEL *wheel,
    INT row);
```

### <a name="description"></a>Description

이 서비스는 현재 선택된 스크롤 휠 행을 할당합니다.

### <a name="parameters"></a>매개 변수

- **wheel** 제네릭 스크롤 휠 제어 블록에 대한 포인터
- **row** 선택할 스크롤 휠 행

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 선택된 휠 행을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
status = gx_scroll_wheel_selected_set(&wheel, 20);

/* if status == GX_SUCCESS the scroll wheel has been set to select
row 20 */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_speed_set"></a>gx_scroll_wheel_speed_set


스크롤 속도 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_scroll_wheel_speed_set(
    GX_SCROLL_WHEEL *wheel,
    GX_FIXED_VAL start_speed_rate,
    GX_FIXED_VAL end_speed_rate,
    GX_VALUE max_steps,
    GX_VALUE delay);
```

### <a name="description"></a>Description

이 서비스는 스크롤 휠 위젯의 스크롤 속도를 할당합니다.

### <a name="parameters"></a>매개 변수

- **wheel** 제네릭 스크롤 휠 제어 블록에 대한 포인터
- **start_speed_rate** 긋기 속도 대비 스크롤 시작 속도 비율
- **end_speed_rate** 긋기 속도 대비 스크롤 종료 속도 비율
- **max_steps** 스크롤의 최대 단계
- **delay** 각 단계의 지연 시간

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 휠 속도를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
status = gx_scroll_wheel_speed_set(&wheel, GX_FIXED_VAL_MAKE(2),
                                GX_FIXED_VAL_MAKE(1) / 2, 10, 2);

/* if status == GX_SUCCESS the scroll wheel speed has been
successfully set. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_total_rows_set"></a>gx_scroll_wheel_total_rows_set


사용 가능한 스크롤 휠 행의 총수 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_scroll_wheel_total_rows_set(
    GX_SCROLL_WHEEL *wheel,
    INT total_rows);
```

### <a name="description"></a>Description

이 서비스는 표시된 스크롤 휠에서 사용할 수 있는 행 수를 할당합니다. 스크롤 휠 위젯은 일반적으로 애플리케이션에서 문자열 배열 또는 사용자 제공 문자열 데이터의 형식으로 행 콘텐츠를 받습니다. 이 API는 사용자에게 제공해야 하는 행의 총수를 스크롤 휠에 알립니다.

### <a name="parameters"></a>매개 변수

- **wheel** 제네릭 스크롤 휠 제어 블록에 대한 포인터
- **total_rows** 사용자에게 제공할 휠 행의 총수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 휠 행의 총수를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
status = gx_scroll_wheel_total_rows_set(&wheel, 100);

/* if status == GX_SUCCESS the scroll wheel has been changed to
display 100 total rows */
```
### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scrollbar_draw"></a>gx_scrollbar_draw


스크롤 막대 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_scrollbar_draw(GX_SCROLLBAR *scrollbar);
```

### <a name="description"></a>Description

이 서비스는 스크롤 막대를 그립니다. 공통 그리기 함수가 세로 및 가로 스크롤 막대 위젯에 모두 사용됩니다. GUIX 캔버스 새로 고침을 통해 내부적으로 호출되지만 재정의된 그리기 함수에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **scrollbar** 그릴 스크롤 막대 위젯

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom scrollbar drawing function. */

VOID my_scrollbar_draw(GX_SCROLLBAR *scrollbar)
{
    /* Call default scrollbar draw. */
    gx_scrollbar_draw(thumb);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_ horizontal_scrollbar_create
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_event_process"></a>gx_scrollbar_event_process


스크롤 막대 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_scrollbar_event_process(
    GX_SCROLLBAR *scrollbar,
    GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 스크롤 막대 이벤트를 처리합니다. 세로 및 가로 스크롤 막대 위젯에 모두 사용되는 공통 이벤트 처리 함수입니다.

### <a name="parameters"></a>매개 변수

- **scrollbar** 스크롤 막대 위젯 제어 블록
- **event** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 막대 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
Call generic scrollbar event processing as part of custom event processing function. */

UINT custom_scrollbar_event_process(GX_SCROLLBAR *scrollbar,
                                    GX_EVENT *event)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;
    default:
        /* pass all other events to the generic scrollbar
            event processing */
        gx_scrollbar_event_process(scrollbar, event);
        break;
    }
}
```

### <a name="see-also"></a>참고 항목

- gx_ horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_limit_check"></a>gx_scrollbar_limit_check


스크롤 막대 한도 확인

### <a name="prototype"></a>프로토타입

```C
UINT gx_scrollbar_limit_check(GX_SCROLLBAR *scrollbar);
```

### <a name="description"></a>Description

이 서비스는 스크롤 막대의 한도를 확인하고 스크롤 막대 썸휠이 미리 정의된 한도를 넘어서 이동하지 않도록 합니다.

### <a name="parameters"></a>매개 변수

- **scrollbar** 스크롤 막대 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 막대 한도를 확인했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Check scrollbar limit of “my_scrollbar”. */
status = gx_scrollbar_limit_check(&my_scrollbar);

/* If status is GX_SUCCESS the limit of scrollbar “my_scrollbar” has been checked. */
```

### <a name="see-also"></a>참고 항목

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_reset"></a>gx_scrollbar_reset


스크롤 막대 다시 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_scrollbar_reset(
    GX_SCROLLBAR *scrollbar,
    GX_SCROLL_INFO *info);
```

### <a name="description"></a>Description

이 서비스는 스크롤 막대를 다시 설정합니다.

### <a name="parameters"></a>매개 변수

- **scrollbar** 스크롤 막대 위젯 제어 블록
- **info** 스크롤 막대 한도, 현재 값, 단계 또는 증분을 정의하는 GX_SCROLL_INFO 구조체에 대한 포인터입니다. **부록 I** 에는 GX_SCROLL_INFO 구조체의 정의가 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 막대를 다시 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 스크롤 정보가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Reset scrollbar “my_scrollbar”. */

GX_SCROLL_INFO my_info;

my_info.gx_scroll_value = 0;
my_info.gx_scroll_minimum = 0;
my_info.gx_scroll_maximum = 100;
my_info.gx_scroll_visible = 10;
my_info.gx_scroll_increment = 1;

status = gx_scrollbar_reset(&my_scrollbar, &my_info);

/* If status is GX_SUCCESS the scrollbar “my_scrollbar” has been reset. */
```

### <a name="see-also"></a>참고 항목

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_value_set"></a>gx_scrollbar_value_set


스크롤 막대 값 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_scrollbar_value_set(
    GX_SCROLLBAR *scrollbar,
    INT value);
```

### <a name="description"></a>Description

이 서비스는 현재 스크롤 막대 값을 할당합니다. 부모 창에 대해 GX_EVENT_VERTICAL_SCROLL 또는 GX_EVENT_HORIZONTAL_SCROLL 이벤트가 생성됩니다.

### <a name="parameters"></a>매개 변수

- **scrollbar** 스크롤 막대 위젯 제어 블록
- **value** 새 스크롤 막대 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 스크롤 막대 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 스크롤 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Assign new value for scrollbar “my_scrollbar”. */

status = gx_scrollbar_value_set(&my_scrollbar, 0);

/* If status is GX_SUCCESS the current position of scrollbar “my_scrollbar” has been set. */

```

### <a name="see-also"></a>참고 항목

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_single_line_text_input_backspace"></a>gx_single_line_text_input_backspace


텍스트 입력 위젯에서 백스페이스 문자 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_backspace(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 커서 위치 앞의 문자를 삭제합니다. 백스페이스 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 한 줄 텍스트 입력을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x23) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Delete a character before the cursor of “my_text_input”. */
status = gx_single_line_text_input_backspace(&my_text_input);

/* If status is GX_SUCCESS the character before the cursor has been deleted. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_buffer_clear"></a>gx_single_line_text_input_buffer_clear


텍스트 입력 버퍼에서 모든 문자 삭제

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_buffer_clear(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 버퍼에서 모든 문자를 삭제합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 한 줄 텍스트 입력 버퍼를 지웠습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* clear input buffer of “my_text_input”. */
status = gx_single_line_text_input_clear(&my_text_input);

/* If status is GX_SUCCESS the text input widget has emptied its input buffer. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_buffer_backspace
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_buffer_get"></a>gx_single_line_text_input_buffer_get


텍스트 입력 위젯의 버퍼 정보 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_buffer_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CHAR **buffer_address, 
    UINT *content_size, 
    UINT *buffer_size);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 위젯의 버퍼 정보를 검색합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록
- **buffer_address** 입력 버퍼의 주소
- **content_size** 입력 데이터의 바이트 수
- **buffer_size** 입력 버퍼의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 버퍼 정보를 검색했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CHAR *buffer_address;
UINT buffer_size;
UINT content_size;

/* Retrieve buffer information of “my_text_input” widget. */
status = gx_single_line_text_input_buffer_get(&my_text_input,
                    &buffer_address, &string_size, &buffer_size);

/* If status is GX_SUCCESS the value of buffer_address, string_size and buffer_size has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_character_delete"></a>gx_single_line_text_input_character_delete


현재 커서 위치 뒤의 문자 삭제

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_character_delete(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 커서 위치 뒤의 문자를 삭제합니다. delete 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 커서 뒤의 문자를 삭제했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Delete the character after the cursor of “my_text_input”. */
status = gx_single_line_text_input_character_delete(&my_text_input);

/* If status is GX_SUCCESS the character after the cursor has been deleted. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_multi_line_text_input_create
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_character_insert"></a>gx_single_line_text_input_character_insert


현재 커서 위치에 문자열 삽입

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_character_insert(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_UBYTE *insert_str,
    UINT insert_size);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 문자열 버퍼의 현재 커서 위치에 문자열을 삽입합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록
- **insert_str** 삽입할 문자열
- **insert_size** 삽입할 바이트 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 문자를 삽입했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Insert characters at current cursor position. */

GX_CHAR insert_text[10] = “insert”;
status = gx_single_line_text_input_character_insert(&my_text_input,
                                            insert_text,
                                            GX_STRLEN(insert_text));

/* If status is GX_SUCCESS the text input widget has successfully insert the string. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_create"></a>gx_single_line_text_input_create


텍스트 입력 위젯 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_create(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    GX_CHAR *input_buffer, UINT buffer_size,
    UINT style, USHORT text_input_id, GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 위젯을 만듭니다. 호출자는 입력 문자열의 스토리지를 제공하고 문자열의 최대 길이를 표시해야 합니다.

GX_SINGLE_LINE_TEXT_INPUT은 GX_PROMPT에서 파생되므로 GX_SINGLE_LINE_TEXT_INPUT 위젯에서 gx_prompt 서비스를 모두 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록
- **name** 위젯의 논리적 이름(선택 사항)
- **parent** 부모 위젯(선택 사항)
- **input_buffer** 입력 문자열의 스토리지
- **buffer_size** 입력 문자열 스토리지 영역의 크기(바이트)
- **style** 텍스트 입력 스타일 플래그
- **text_input_id** 입력 위젯의 ID(선택 사항)
- **size** 초기 위젯 크기를 정의하는 사각형

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 한 줄 텍스트 입력을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_SINGLE_LINE_TEXT_INPUT my_text_input;
static GX_CHAR           text_input_buffer[100];
GX_RECTANGLE             size;

/* Define widget size. */
gx_utility_rectangle_define(&size, 10, 10, 110, 40);

/* Create single-line text input widget “my_text_input”. */
status = gx_single_line_text_input_create(&my_text_input,
                        “text_input”, GX_NULL, text_input_buffer, 100,
                        GX_STYLE_ENABLED, 0, &size);

/* If status is GX_SUCCESS, the text input widget has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_draw"></a>gx_single_line_text_input_draw


텍스트 입력 위젯 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_single_line_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 위젯을 그립니다. 일반적으로 캔버스를 새로 고치는 동안 내부적으로 호출되지만 사용자 지정 텍스트 입력 그리기 함수에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom single line text input draw function. */

VOID my_sl_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *input)
{
    /* Call default single line text input draw. */
    gx_single_line_text_input_draw(input);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_draw_position_get"></a>gx_single_line_text_input_draw_position_get


텍스트 그리기 시작 위치 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_draw_position_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_VALUE *xpos, GX_VALUE *ypos);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 텍스트의 그리기 시작 위치를 검색합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록
- **xpos** x 좌표에서 검색된 그리기 시작 위치
- **ypos** y 좌표에서 검색된 그리기 시작 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트 입력 커서를 끝으로 이동했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Write a custom single line text input draw function. */

VOID my_sl_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *input)
{
GX_VALUE xpos;
GX_VALUE ypos;

    /* Draw background. */
    gx_widget_border_draw(input, border_color, upper_fill_color,
                          lower_fill_color, GX_TRUE);

    /* Retrieve text draw start position. */
    gx_single_line_text_input_draw_position_get(input, xpos,
                                                ypos);

    /* Add your text drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_end"></a>gx_single_line_text_input_end


텍스트 입력 커서를 문자열 끝으로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_end(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 위젯 커서를 입력 문자열의 끝으로 이동합니다. end 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트 입력 커서를 끝으로 이동했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move input cursor to end. */
status = gx_single_line_text_input_end(&my_text_input);

/* If status is GX_SUCCESS, text text input cursor has been moved to end. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_event_process"></a>gx_single_line_text_input_event_process


텍스트 입력 위젯 이벤트 처리 함수

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_event_process(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 한 줄 텍스트 입력 이벤트를 처리합니다. gx_single_line_text_input_create 함수에서 내부적으로 참조되지만 애플리케이션이 사용자 지정 한 줄 텍스트 입력 이벤트 처리 함수를 정의하는 경우 애플리케이션에서 사용할 수 있도록 노출됩니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록
- **event_ptr** GX_EVENT 구조체에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트 입력 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Call generic single line text input event processing as part of custom event processing function. */

UINT custom_sl_text_input_event_process(
                                GX_SINGLE_LINE_TEXT_INPUT *input,
                                GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default single line
            text input event processing */
        status =
        gx_single_line_text_input_event_process(input, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_fill_color_set"></a>gx_single_line_text_input_fill_color_set


한 줄 텍스트 입력 배경색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_fill_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_fill_color_id,
    GX_RESOURCE_ID selected_fill_color_id,
    GX_RESOURCE_ID disabled_fill_color_id,
    GX_RESOURCE_ID readonly_fill_color_id);
```

### <a name="description"></a>Description

이 서비스는 한 줄 텍스트 입력의 채우기 색을 설정합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 제어 블록에 대한 포인터
- **normal_fill_color_id** 정상 상태인 위젯 채우기 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **selected_fill_color_id** 위젯에 포커스가 있는 경우 위젯 채우기 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **disabled_fill_color_id** GX_STYLE_ENABLED 스타일이 설정되지 않은 경우 위젯 채우기 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **readonly_fill_color_id** GX_STYLE_ENABLED 및 GX_STYLE_TEXT_INPUT_READONLY 스타일이 모두 설정된 경우 위젯 채우기 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 한 줄 텍스트 입력 채우기 색을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set fill colors for single line text input “my_text_input”. */
status = gx_single_line_text_input_fill_color_set(&my_text_input,
                    GX_COLOR_ID_NORMAL_FILL,
                    GX_COLOR_ID_SELECTED_FILL,
                    GX_COLOR_ID_DISABLED_FILL,
                    GX_COLOR_ID_READONLY_FILL);

/* If status is GX_SUCCESS, the fill color of “my_text_input” was
set. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_home"></a>gx_single_line_text_input_home


텍스트 입력 커서를 홈 위치로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_home(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 커서 위치를 입력 문자열의 시작으로 이동합니다. home 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 커서를 홈 위치로 이동했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move cursor to the start of the input text. */
status = gx_single_line_text_input_home(&my_text_input);

/* If status is GX_SUCCESS the cursor has been moved to the home position */
```

### <a name="see-also"></a>참고 항목
- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_left_arrow"></a>gx_single_line_text_input_left_arrow


입력 커서를 한 문자 왼쪽으로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_left_arrow(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 커서를 한 문자 왼쪽으로 이동합니다. 왼쪽 화살표 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 커서를 왼쪽으로 이동했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move the cursor one character to the left. */
status = gx_single_line_text_input_left_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the left. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_position_get"></a>gx_single_line_text_input_position_get

커서를 픽셀 위치로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_position_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    INT pixel_position);
```

### <a name="description"></a>Description

이 서비스는 요청된 픽셀 위치를 기준으로 텍스트 입력 커서를 배치합니다. 텍스트 입력 커서 인덱스는 픽셀 위치의 x 값을 기준으로 계산됩니다. 펜 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록
- **pixel_position** 픽셀 위치의 X 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 요청된 위치에 커서를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set cursor to requested position. */
status = gx_single_line_text_input_position_get(&my_text_input,
                                                100);

/* If status is GX_SUCCESS the text input widget cursor has been positioned */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_right_arrow"></a>gx_single_line_text_input_right_arrow


입력 커서를 한 문자 오른쪽으로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_right_arrow(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Description

이 서비스는 텍스트 입력 커서를 한 문자 오른쪽으로 이동합니다. 오른쪽 화살표 키 누름 이벤트가 수신될 때 내부적으로 호출되지만 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 커서를 오른쪽으로 이동했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move cursor one character to the right. */
status = gx_single_line_text_input_right_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the right. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_add"></a>gx_single_line_text_input_style_add


스타일 추가

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_style_add(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Description

이 서비스는 한 줄 텍스트 입력 위젯에 지정된 스타일을 추가합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록
- **style** 추가할 새 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯에 스타일을 추가했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Add a new style to “my_text_input”. */
status = gx_single_line_text_input_style_add(&my_text_input,
GX_STYLE_CURSOR_AWAYS);

/* If status is GX_SUCCESS the GX_STYLE_CUSROSR_SHOR have been successfully added. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gax_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_remove"></a>gx_single_line_text_input_style_remove

스타일 제거

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_style_remove(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Description

이 서비스는 한 줄 텍스트 입력 위젯에서 지정된 스타일을 제거합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록
- **style** 제거할 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯에서 스타일을 제거했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Remove cursor blink style from “my_text_input”. */
status = gx_single_line_text_input_style_remove(&my_text_input,
GX_STYLE_CURSOR_BLINK);

/* If status is GX_SUCCESS the GX_STYLE_CURSOR_BLINK style has been successfully removed. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_set"></a>gx_single_line_text_input_style_set


텍스트 입력 스타일 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_style_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Description

이 서비스는 한 줄 텍스트 입력 위젯에 지정된 스타일을 설정합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 위젯 제어 블록
- **style** 할당할 스타일 플래그

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트 입력 스타일을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set style for “my_text_input”. */
status = gx_single_line_text_input_style_set(&my_text_input,
                    GX_STYLE_ENABLED | GX_STYLE_CURSOR_BLINK);

/* If status is GX_SUCCESS the text input style has been successfully set to the specified styles. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_signle_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_color_set"></a>gx_single_line_text_input_text_color_set


한 줄 텍스트 입력 텍스트 색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_text_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id,
    GX_RESOURCE_ID readonly_text_color_id);
```

### <a name="description"></a>Description

이 서비스는 한 줄 텍스트 입력의 텍스트 색을 설정합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 제어 블록에 대한 포인터
- **normal_text_color_id** 정상 상태인 텍스트 색의 리소스 ID **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **selected_text_color_id** 위젯에 포커스가 있는 경우 텍스트 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **disabled_text_color_id** GX_STYLE_ENABLED 스타일이 설정되지 않은 경우 텍스트 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **readonly_text_color_id** GX_STYLE_ENABLED 및 GX_STYLE_TEXT_INPUT_READONLY 스타일이 모두 설정된 경우 텍스트 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 한 줄 텍스트 입력 텍스트 색을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set text colors for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_color_set(&my_text_input,
                                        GX_COLOR_ID_NORMAL_TEXT,
                                        GX_COLOR_ID_SELECTED_TEXT,
                                        GX_COLOR_ID_DISABLED_TEXT,
                                        GX_COLOR_ID_READONLY_TEXT);

/* If status is GX_SUCCESS, the text color “my_text_input” was set. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_select"></a>gx_single_line_text_input_text_select

텍스트 선택

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_text_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    UINT start_index, UINT end_index);
```

### <a name="description"></a>Description

이 서비스는 지정된 시작 표시 및 끝 표시 인덱스를 사용하여 텍스트를 선택하고 선택된 채우기 및 텍스트 색을 사용하여 선택한 텍스트를 강조 표시합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 제어 블록에 대한 포인터
- **start_index** 선택한 첫 번째 문자의 인덱스
- **end_index** 선택한 마지막 문자의 인덱스

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 한 줄 텍스트 입력 텍스트를 선택했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 인덱스 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Select text between index [0, 9]. */
status = gx_single_line_text_input_text_select(&my_text_input,
                                                0,9);

/* If status is GX_SUCCESS, the text between index [0, 9] “my_text_input” was selected. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_set"></a>gx_single_line_text_input_text_set


한 줄 텍스트 입력 텍스트 설정(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_text_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *text);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_single_line_text_input_text_set_ext()로 대체되었습니다.

이 서비스는 한 줄 텍스트 입력의 텍스트를 설정합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 제어 블록에 대한 포인터
- **text** NULL로 종료된 텍스트 문자열

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 한 줄 텍스트 입력 텍스트 색을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CONST GX_CHAR new_text = “Set Single Line Text Input Text”;

/* Set text for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_set(&my_text_input,
                                        new_text);

/* If status is GX_SUCCESS, the text of “my_text_input” was set. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_text_set_ext

## <a name="gx_single_line_text_input_text_set_ext"></a>gx_single_line_text_input_text_set_ext


한 줄 텍스트 입력 텍스트 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_single_line_text_input_text_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Description

이 서비스는 한 줄 텍스트 입력의 텍스트를 설정합니다.

### <a name="parameters"></a>매개 변수

- **text_input** 한 줄 텍스트 입력 제어 블록에 대한 포인터
- **string** GX_STRING 변수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 한 줄 텍스트 입력 텍스트 색을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING new_string;
new_string.gx_string_ptr = “Set Single Line Text Input Text”;
new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Set text for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_set_ext(&my_text_input,
                                        &new_string);

/* If status is GX_SUCCESS, the string has been assigned to my_text_input. */
```

### <a name="see-also"></a>참고 항목

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_set_ext


## <a name="gx_slider_create"></a>gx_slider_create

슬라이더 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_slider_create(
    GX_SLIDER *slider, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, INT tick_count,
    GX_SLIDER_INFO *slider_info,
    ULONG style, USHORT slider_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 슬라이더 위젯을 만듭니다.

GX_SLIDER는 GX_WIDGET에서 파생되므로 GX_SLIDER 형식 위젯에서 gx_widget API 서비스를 모두 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **slider**: 슬라이더 위젯 제어 블록
- **name**: 슬라이더의 이름
- **parent**: 부모 위젯에 대한 포인터
- **tick_count**: 슬라이더 틱 수
- **slider_info**: 슬라이더 값 한도, 슬라이더 바늘 크기 및 위치, 기타 슬라이더 매개 변수를 전달하는 데 사용되는 구조체인 슬라이더 정보에 대한 포인터입니다. **부록 I** 에는 GX_SLIDER_INFO 구조체의 정의가 나와 있습니다.
- **style**: 슬라이더의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **slider_id**: 애플리케이션에서 정의된 슬라이더 ID
- **size**: 슬라이더의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 슬라이더를 만들었습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**: (0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**: (0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 부모 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create slider “my_slider”. */

GX_SLIDER my_slider;
GX_SLIDER_INFO info;

info.gx_slider_info_min_val = 0;
info.gx_slider_info_max_val = 100;
info.gx_slider_info_current_val = 50;
info.gx_slider_info_increment = 1;
info.gx_slider_info_min_travel = 20;
info.gx_slider_info_max_travel = 20;
info.gx_slider_info_needle_width = 10;
info.gx_slider_info_needle_height = 10;
info.gx_slider_info_needle_inset = 5;
info.gx_slider_info_needle_hotspot_offset = 5;

status = gx_slider_create(&my_slider, “my_slider”,
    &my_parent, 10, info, GX_STYLE_ENABLED, ID_MY_SLIDER, &size);

/* If status is GX_SUCCESS the slider “my_slider” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_draw"></a>gx_slider_draw

슬라이더 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_slider_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Description

이 서비스는 슬라이더를 그립니다. gx_slider_create 함수에서 내부적으로 사용되지만 사용자 지정 슬라이더 그리기 함수가 정의된 경우 해당 인스턴스에서 애플리케이션이 사용할 수 있도록 노출됩니다.

### <a name="parameters"></a>매개 변수

- **slider**: 슬라이더 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Call default slider draw. */
    gx_slider_draw(slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_event_process"></a>gx_slider_event_process

슬라이더 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_slider_event_process(
    GX_SLIDER *slider, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 슬라이더 이벤트를 처리합니다. gx_slider_create 함수에서 내부적으로 참조되지만 애플리케이션이 사용자 지정 슬라이더 표시줄 이벤트 처리 함수를 정의하는 경우 애플리케이션에서 사용할 수 있도록 노출됩니다.

### <a name="parameters"></a>매개 변수

- **slider**: 슬라이더 위젯 제어 블록
- **event**: 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 슬라이더 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic slider event processing as part of custom event processing function. */

UINT custom_slider_event_process(GX_SLIDER *slider,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;
    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default slider event processing */
            status = gx_slider_event_process(slider, event);
            break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_info_set"></a>gx_slider_info_set

슬라이더 정보 블록 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_slider_info_set(
    GX_SLIDER *slider, 
    GX_SLIDER_INFO *info);
```

### <a name="description"></a>Description

이 서비스는 슬라이더 최솟값, 슬라이더 최댓값, 슬라이더 현재 값 등의 지정된 슬라이더 정보를 표시된 슬라이더에 할당합니다. 슬라이더는 바늘 위치를 업데이트하고 새 슬라이더 정보에 따라 다시 그려집니다.

### <a name="parameters"></a>매개 변수

- **slider**: 슬라이더 위젯 제어 블록
- **info**: 슬라이더 정보 구조체에 대한 포인터 **부록 I** 에는 GX_SLIDER_INFO 구조체의 정의가 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 슬라이더 정보를 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_SLIDER_INFO my_slider_info;
my_slider_info.gx_slider_info_min_val = 0;
my_slider_info.gx_slider_info_max_val = 100;
my_slider_info.gx_slider_info_current_val = 50;
my_slider_info.gx_slider_info_increment = 1;
my_slider_info.gx_slider_info_min_travel = 20;
my_slider_info.gx_slider_info_max_travel = 20;
my_slider_info.gx_slider_info_needle_width = 10;
my_slider_info.gx_slider_info_needle_height = 10;
my_slider_info.gx_slider_info_needle_inset = 5;

my_slider_info.gx_slider_info_needle_hotspot_offset = 5;

/* Set slider information for slider “my_slider”. */
status = gx_slider_info_set (&my_slider, &my_slider_info);

/* If status is GX_SUCCESS the “my_slider” is configured with my_slider_info. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_needle_draw"></a>gx_slider_needle_draw

슬라이더 바늘 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_slider_needle_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Description

이 서비스는 슬라이더 바늘을 그립니다. gx_slider_draw 함수에서 자동으로 호출되지만 사용자 지정 슬라이더 그리기 함수의 일부로 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **slider**: 슬라이더 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Add your own background draw here. */

    /* Call default tickmarks draw. */
    gx_slider_tickmarks_draw(slider);

    /* Call default slider needle draw. */
    gx_slider_needle_draw(slider);
}
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_needle_position_get"></a>gx_slider_needle_position_get

슬라이더 바늘 위치 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_slider_needle_position_get(
    GX_SLIDER *slider,
    GX_SLIDER_INFO *slider_info,
    GX_RECTANGLE *return_position);
```

### <a name="description"></a>Description

이 서비스는 현재 슬라이더 값을 기준으로 슬라이더 바늘 위치를 컴퓨팅합니다.

### <a name="parameters"></a>매개 변수

- **slider**: 슬라이더 위젯 제어 블록
- **slider_info**: 슬라이더 한도, 바늘 크기 및 오프셋, 기타 슬라이더 매개 변수를 정의하는 슬라이더 정보 구조체에 대한 포인터입니다. **부록 I** 에는 GX_SLIDER_INFO 구조체의 정의가 나와 있습니다.
- **return_position**: 바늘 위치 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 슬라이더 바늘 위치를 가져왔습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) 슬라이더 정보가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_RECTANGLE needle_position;

/* Get the needle position for slider “my_slider”. */
status = gx_slider_needle_posistion_get(&my_slider, &slider_info,
    &needle_position);

/* If status is GX_SUCCESS the needle position for slider “my_slider” has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_tickmarks_draw"></a>gx_slider_tickmarks_draw

슬라이더 눈금 표시 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_slider_tickmarks_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Description

이 서비스는 슬라이더 눈금 표시를 그립니다. gx_slider_draw 함수에서 내부적으로 호출되지만 사용자 지정 슬라이더 그리기 함수를 구현할 수 있는 애플리케이션에서 사용할 수 있도록 노출됩니다.

### <a name="parameters"></a>매개 변수

- **slider**: 슬라이더 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Add your own background draw here. */

    /* Call default tickmarks draw. */
    gx_slider_tickmarks_draw(slider);

    /* Call default slider needle draw. */
    gx_slider_needle_draw(slider);
}
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_travel_get"></a>gx_slider_travel_get

슬라이더 이동 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_slider_travel_get(
    GX_SLIDER *widget,
    GX_SLIDER_INFO *info,
    INT *return_min_travel, 
    INT *return_max_travel);
```

### <a name="description"></a>Description

이 서비스는 슬라이더 이동을 가져옵니다.

### <a name="parameters"></a>매개 변수

- **slider**: 슬라이더 위젯 제어 블록
- **info**: 슬라이더 정보 구조체에 대한 포인터입니다. **부록 I** 에는 GX_SLIDER_INFO 구조체의 정의가 나와 있습니다.
- **return_min_travel**: 최소 이동 값 대상에 대한 포인터</td>
- **return_max_travell**: 최대 이동 값 대상에 대한 포인터</td>

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 슬라이더 이동을 가져왔습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) 슬라이더 정보가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Get travel information for for slider “my_slider”. */
status = gx_slider_travel_get(&my_slider, &info,
    &my_min_travel, &my_max_travel);

/* If status is GX_SUCCESS the travel max/min values for slider “my_slider” have been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_value_calculate"></a>gx_slider_value_calculate

슬라이더 값 계산

### <a name="prototype"></a>프로토타입

```C
UINT gx_slider_value_calculate(
    GX_SLIDER *slider, 
    GX_SLIDER_INFO *info,
    INT new_position);
```

### <a name="description"></a>Description

이 서비스는 슬라이더 바늘 위치를 기준으로 슬라이더 값을 계산합니다. 사용자가 슬라이더 바늘을 이동할 때 GUIX에서 내부적으로 호출되지만 사용자 지정 슬라이더 위젯을 구현할 때 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **slider**: 슬라이더 위젯 제어 블록
- **info**: 슬라이더 정보에 대한 포인터입니다. **부록 I** 에는 GX_LISDER_INFO 구조체의 정의가 나와 있습니다.
- **new_position**: 새 슬라이더 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 슬라이더 값을 계산했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) 슬라이더 정보가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Calculate new value for slider “my_slider”. */
status = gx_slider_value_calculate(&my_slider,
    &my_slider.gx_slider_info, new_slider_position);

/* If status is GX_SUCCESS the slider value of “my_slider” has been calculated. */

```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_set

## <a name="gx_slider_value_set"></a>gx_slider_value_set

슬라이더 값 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_slider_value_set(
    GX_SLIDER *slider,
    GX_SLIDER_INFO *info, 
    INT new_value);
```

### <a name="description"></a>Description

이 서비스는 슬라이더 값을 설정합니다. 애플리케이션은 이 API를 호출하여 프로그램에서 제어되는 슬라이더 바늘을 이동할 수 있으므로 슬라이더 바늘을 끌기 위해 사용자 입력이 필요하지 않습니다.

### <a name="parameters"></a>매개 변수

- **slider**: 슬라이더 위젯 제어 블록
- **info**: 슬라이더 정보 구조체에 대한 포인터입니다. **부록 I** 에는 GX_SLIDER_INFO 구조체의 정의가 나와 있습니다.
- **new_value**: 새 슬라이더 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 슬라이더 값을 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set new value for slider “my_slider”. */
status = gx_slider_value_set(&my_slider,
    &my_slider.gx_slider_info, new_value);

/* If status is GX_SUCCESS the new value has been set for slider “my_slider”. */
```

### <a name="see-also"></a>참고 항목

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate

##  <a name="gx_sprite_create"></a>gx_sprite_create

스프라이트 위젯 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_sprite_create(
    GX_SPRITE *sprite, GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_SPRITE_FRAME *frame_list,
    USHORT frame_count,
    ULONG style, USHORT sprite_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 GX_SPRITE 위젯을 만듭니다. 스프라이트는 애니메이션과 같이 pixelmap 시퀀스를 표시하는 데 사용되거나 다중 상태 pixelmap 표시 위젯으로 사용될 수 있습니다.

GX_SPRITE는 GX_WIDGET에서 파생되며 gx_widget API 서비스를 모두 지원합니다.

GX_SPRITE 위젯에서 SPRITE 애니메이션을 정의하려면 GX_SPRITE_FRAME 구조체 배열이 필요합니다. **부록 I** 에는 GX_PRITE_FRAME 구조체의 정의가 나와 있습니다.

### <a name="parameters"></a>매개 변수

- **sprite**: 스프라이트 위젯 제어 블록
- **name**: 스프라이트 이름(선택 사항)
- **parent**: 부모 위젯에 대한 포인터
- **frame_list**: GX_SPRITE_FRAME 구조체 배열
- **frame_count**: 프레임 목록 배열의 항목 수 지정
- **style**: 스프라이트의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **sprite_id**: 애플리케이션에서 정의된 스프라이트 ID
- **size**: 스프라이트의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 스프라이트를 만들었습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**: (0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 부모 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create sprite “my_sprite”. */

status = gx_sprite_create(&my_sprite, “my_sprite”,
    &my_parent,
    sprite_frame_list, frame_count,
    GX_STYLE_SPRITE_AUTO|GX_STYLE_SPRITE_LOOP,
    ID_MY_SPRITE, &size);

/* If status is GX_SUCCESS the sprite “my_sprite” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_sprite_start
- gx_sprite_stop
- gx_sprite_current_frame_set
- gx_sprite_frame_list_set

## <a name="gx_sprite_current_frame_set"></a>gx_sprite_current_frame_set

스프라이트 프레임 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_sprite_current_frame_set(
    GX_SPRITE *sprite, 
    USHORT frame);
```

### <a name="description"></a>Description

이 서비스는 현재 스프라이트 프레임을 할당합니다. GX_SPRITE 위젯이 자동으로 실행되지 않는 경우 실행 중인 프레임 pixelmap을 표시하는 프로그램 제어 상태 등으로 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **sprite**: 스프라이트 위젯 제어 블록
- **frame**: 표시할 스프라이트 프레임

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 성공했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Assign frame number 3 as the current sprite frame */
status = gx_sprite_current_frame_set(&my_sprite, 3);

/* If status is GX_SUCCESS the sprite “my_sprite” will display frame index 3. */
```

### <a name="see-also"></a>참고 항목

- gx_sprite_start
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_sprite_frame_list_set"></a>gx_sprite_frame_list_set

스프라이트 프레임 목록 할당 또는 변경

### <a name="prototype"></a>프로토타입

```C
UINT gx_sprite_frame_list_set(
    GX_SPRITE *sprite,
    GX_SPRITE_FRAME *frame_list,
    USHORT frame_count);
```

### <a name="description"></a>Description

이 서비스를 사용하면 스프라이트 위젯을 만든 후에 스프라이트 위젯에서 사용되는 프레임 목록을 할당하거나 다시 할당할 수 있습니다. 스프라이트 프레임 목록 콘텐츠에 대한 자세한 내용은 gx_sprite_create API 설명서를 참조하세요.

### <a name="parameters"></a>매개 변수

- **sprite**: 스프라이트 위젯 제어 블록
- **frame_list**: GX_SPRITE_FRAME 구조체 배열 또는 프레임 목록이 없는 경우 GX_NULL
- **frame_count**: 프레임 목록 배열의 프레임 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 스프라이트 프레임 목록을 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Assign framelist_1, which has 10 frames, to my_sprite */
status = gx_sprite_frame_list_set(&my_sprite, framelist_1, 10);

/* If status is GX_SUCCESS the new frame list is now associated with this sprite */
```

### <a name="see-also"></a>참고 항목

- gx_sprite_current_frame_set
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_create

## <a name="gx_sprite_start"></a>gx_sprite_start

스프라이트 실행 시퀀스 시작

### <a name="prototype"></a>프로토타입

```C
UINT gx_sprite_start(
    GX_SPRITE *sprite, 
    USHORT frame);
```

### <a name="description"></a>Description

이 서비스는 스프라이트 자동 실행 시퀀스를 시작합니다. 스프라이트 위젯은 마지막 프레임에 도달할 때까지 스프라이트 프레임을 순환하거나 GX_SPRITE_LOOP 스타일이 설정된 경우 계속 실행됩니다.

### <a name="parameters"></a>매개 변수

- **sprite**: 스프라이트 위젯 제어 블록
- **frame**: 표시할 초기 스프라이트 프레임(일반적으로 프레임 0)

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 스프라이트 실행을 시작했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Start the sprite “my_sprite” */
status = gx_sprite_start(&my_sprite, 0);

/* If status is GX_SUCCESS the sprite “my_sprite” will start running */
```

### <a name="see-also"></a>참고 항목

- gx_sprite_current_frame_set
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_sprite_stop"></a>gx_sprite_stop

스프라이트 실행 순서 중지

### <a name="prototype"></a>프로토타입

```C
UINT gx_sprite_stop(GX_SPRITE *sprite);
```

### <a name="description"></a>Description

이 서비스는 스프라이트 자동 실행 시퀀스를 중지합니다.

### <a name="parameters"></a>매개 변수

- **sprite**: 스프라이트 위젯 제어 블록

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 스프라이트 실행을 중지했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Stop the sprite sequence */
status = gx_sprite_stop(&my_sprite);

/* If status is GX_SUCCESS the sprite “my_sprite” is stopped. */
```

### <a name="see-also"></a>참고 항목

- gx_sprite_current_frame_set
- gx_sprite_start
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_string_scroll_wheel_create"></a>gx_string_scroll_wheel_create

문자열 형식 스크롤 휠 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_string_scroll_wheel_create(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    GX_CONST GX_CHAR **string_list, 
    ULONG style,
    USHORT Id, 
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>Description

이 서비스는 문자열 형식 스크롤 휠을 만듭니다.

GX_STRING_SCROLL_WHEEL은 GX_TEXT_SCROLL_WHEEL에서 파생되므로 GX_STRING_SCROLL_WHEEL 위젯에서 gx_text_scroll_wheel API 함수를 모두 사용할 수도 있습니다.

애플리케이션은 스크롤 휠에서 표시할 문자열을 정의하는 간단한 문자열 배열을 create 함수에 전달하거나, GX_NULL을 string_list 매개 변수로 전달하고 `gx_string_scroll_wheel_string_id_list_set()` API를 호출하여 문자열 ID 배열을 제공할 수 있습니다. 두 번째 방법을 사용하는 경우 활성 애플리케이션 언어가 수정되면 문자열 스크롤 휠이 표시되는 문자열을 자동으로 전환합니다.

또는 표시할 문자열이 정적으로 정의되지 않았거나 스크롤 휠이 생성될 때 알 수 없는 경우 애플리케이션에서 GX_NULL을 문자열 목록 매개 변수로 전달하고 API 함수 gx_text_scroll_wheel_callback_set()을 호출하여 필요에 따라 실시간으로 표시되는 문자열을 제공할 콜백 함수를 정의할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **wheel**: 문자열 스크롤 휠 제어 블록 주소
- **name**: 애플리케이션에서 정의된 위젯 이름
- **parent**: 휠 부모 또는 GX_NULL
- **total_rows**: 사용자에게 제공할 행의 총수
- **string_list**: 정적으로 정의된 문자열 배열 또는 GX_NULL
- **style**: 원하는 스타일 플래그
- **Id**: 애플리케이션에서 정의된 휠 스타일 플래그
- **size**: 초기 스크롤 휠 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 문자열 스크롤 휠을 만들었습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**: (0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CONST GX_CHAR *days[] = {
    “Sunday”,
    “Monday”,
    “Tuesday”,
    “Wednesday”,
    “Thursday”,
    “Friday”,
    “Saturday”
};

GX_STRING_SCROLL_WHEEL wheel;

/* Create the string scroll wheel. */

status = gx_string_scroll_wheel_create(&wheel, “Day Wheel”,
    root, 7, days,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|GX_STYLE_TEXT_SCROLL_WHEEL_ROUND,
    ID_SCROLL_WHEEL_DAY, &size);

/* If status is GX_SUCCESS the string scroll wheel has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_event_process"></a>gx_string_scroll_wheel_event_process


문자열 스크롤 휠 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_string_scroll_wheel_string_id_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_RESOURCE_ID *string_id_list, 
    INT id_count);
```

### <a name="description"></a>Description

이 서비스는 지정된 문자열 스크롤 휠에 대한 이벤트를 처리합니다. 사용자 지정 문자열 스크롤 휠 이벤트 처리 함수에서 기본 이벤트 처리기로 호출되어야 합니다.

### <a name="parameters"></a>매개 변수

- **wheel** 문자열 스크롤 휠 제어 블록에 대한 포인터
- **event_ptr** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 문자열 스크롤 휠 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic string scroll wheel event processing as part of custom event processing function. */

UINT custom_string_scroll_wheel_event_process(GX_STRING_SCROLL_WHEEL *wheel, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default string scroll wheel event processing */
        status = gx_string_scroll_wheel_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_string_id_list_set"></a>gx_string_scroll_wheel_string_id_list_set

문자열 ID 배열 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_string_scroll_wheel_string_id_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_RESOURCE_ID *string_id_list, INT id_count);
```

### <a name="description"></a>Description

이 서비스는 문자열 스크롤 휠 위젯에 문자열 ID 배열을 할당합니다. 문자열 스크롤 휠에 문자열을 할당하는 이 방법은 문자열이 정적으로 정의되고 위젯이 여러 언어로 작동해야 하는 경우에 권장됩니다. 이 API를 사용하려면 먼저 GX_NULL 문자열 목록을 사용하여 스크롤 휠 위젯을 만들어야 합니다.

### <a name="parameters"></a>매개 변수

- **wheel**: 문자열 스크롤 휠 제어 블록 주소
- **string_id_list**: 문자열 ID 배열
- **id_count**: ID 목록의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 문자열 ID 배열을 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) ID 목록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CONST RESOURCE_ID wheel_ids[] = {
    GX_STRING_ID_SUNDAY,
    GX_STRING_ID_MONDAY,
    GX_STRING_ID_TUESDAY,
    GX_STRING_ID_WEDNESDAY,
    GX_STRING_ID_THURSDAY,
    GX_STRING_ID_FRIDAY,
    GX_STRING_ID_SATURDAY
};

GX_STRING_SCROLL_WHEEL wheel;

/* Stop the sprite sequence */

status = gx_string_scroll_wheel_string_id_list_set(&wheel, wheel_ids, 7);

/* If status is GX_SUCCESS the ID list has been assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_string_list_set"></a>gx_string_scroll_wheel_string_list_set

문자열 배열 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_string_scroll_wheel_string_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *string_list, 
    INT string_count);
```

### <a name="description"></a>Description

이 서비스는 문자열 스크롤 휠 위젯에 문자열 배열을 할당합니다. 위젯을 처음 만든 후에 표시되는 문자열을 수정하는 데 사용할 수 있습니다.

string_scroll_wheel은 GX_STYLE_TEXT_COPY를 지원하지 않으므로 애플리케이션에서 이 함수에 전달되는 문자열 배열을 정적으로 정의해야 합니다.

### <a name="parameters"></a>매개 변수

- **wheel**: 문자열 스크롤 휠 제어 블록 주소
- **string_list**: 문자열 포인터 배열
- **string_count**: 문자열 배열의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 스크롤 휠의 문자열을 변경했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) 문자열 목록 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CONST GX_CHAR *days[] = {
    “Sunday”,
    “Monday”,
    “Tuesday”,
    “Wednesday”,
    “Thursday”,
    “Friday”,
    “Saturday”
};

GX_STRING_SCROLL_WHEEL wheel;

/* Set the array of strings to the scroll wheel. */

status = gx_string_scroll_wheel_string_list_set(&wheel, days, 7);

/* If status is GX_SUCCESS the string array has been assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_studio_widget_create"></a>gx_studio_widget_create

Studio에서 생성된 사양 파일에 정의된 위젯 만들기

### <a name="prototype"></a>프로토타입

```C
GX_WIDGET *gx_studio_widget_create(
    GX_BYTE *control,
    GX_CONST GX_STUDIO_WIDGET *definition, 
    GX_WIDGET *parent);
```

### <a name="description"></a>Description

이 서비스는 GUIX Studio에서 생성된 사양 파일 내에 정의된 위젯 사양을 사용하여 위젯 및 위젯의 자식을 만듭니다. 이 함수는 유사한 함수 `gx_studio_named_widget_create()`의 “이름으로” 조회를 방지합니다.

GX_STUDIO_WIDGET 구조체는 GUIX Studio에서 생성된 애플리케이션 사양 헤더 파일에 정의되어 있습니다.

정적으로 할당된 위젯의 경우 위젯 제어 블록은 생성된 specifications.c 파일에 정의되어 있으며 GUIX Studio 내에서 정의된 위젯 이름이 지정됩니다. 동적으로 할당된 위젯의 경우 애플리케이션에서 GX_NULL을 위젯 제어 블록 주소로 전달해야 하며, 함수는 애플리케이션에서 정의하고 제공하는 `gx_system_memory_allocate()` 함수를 사용하여 위젯 제어 블록을 동적으로 할당하려고 합니다.

애플리케이션에서 생성된 사양 파일 내의 GUIX Studio 위젯 정의를 직접 참조하려면 GUI Studio 코드 생성기에서 사용되는 명명 규칙을 따라야 합니다. specifications.c 파일 내에서 생성된 GX_STUDIO_WIDGET 구조체의 경우 항상 <widget_name>_define 규칙에 따라 이름이 지정됩니다. 여기서 위젯이 자식 위젯의 자식인 경우 <widget_name> 필드를 여러 번 반복할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **control** 위젯 제어 블록에 대한 포인터 또는 동적으로 할당된 경우 GX_NULL
- **definition** Studio에서 생성된 위젯 정의 구조체
- **parent** 위젯 부모(있는 경우)에 대한 포인터

### <a name="return-values"></a>반환 값

만든 위젯 제어 블록에 대한 포인터 또는 만들지 못한 경우 GX_NULL입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create the widget “playlist_screen”, which is statically allocated. */

widget = gx_studio_widget_create(&playlist_screen,
    &playlist_screen_define,
    root_window);

/* If widget != GX_NULL the widget was created. */

/* create the widget “songs_screen”, which is dynamically allocated */

widget = gx_studio_widget_create(GX_NULL,
    &songs_screen_define, root_window);
```

### <a name="see-also"></a>참고 항목

- gx_studio_named_widget_create

## <a name="gx_studio_named_widget_create"></a>gx_studio_named_widget_create

Studio에서 생성된 사양 파일에 정의된 위젯 만들기

### <a name="prototype"></a>프로토타입

```C
UINT *gx_studio_named_widget_create(
    char *name, 
    GX_WIDGET *parent,
    GX_WIDGET **new_widget);
```

### <a name="description"></a>Description

이 서비스는 GUIX Studio에서 생성된 사양 파일 내에 정의된 위젯 사양을 사용하여 위젯 및 위젯의 자식을 만듭니다.

GUIX Studio 애플리케이션 내에서 위젯 정의 식별자로 지정된 화면 이름을 사용하여 최상위 화면을 만드는 데 사용됩니다.

### <a name="parameters"></a>매개 변수

- **name**: GUIX Studio 애플리케이션 내에서 정의된 화면 이름
- **parent**: 위젯 부모(있는 경우)에 대한 포인터
- **new_widget**: 만든 위젯 포인터를 반환할 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 성공했습니다.
- **GX_FAILURE**: (0x11) 명명된 위젯을 찾을 수 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create the widget named “child_popup”,
   which is a child of the top-level screen “main_screen”. */

GX_WIDGET *menu_screen;

status = gx_studio_named_widget_create(“main_menu”,
    &root_window, &menu_screen);

/* If status == GX_SUCCESS the screen was created
   and linked to the root window. */
```

### <a name="see-also"></a>참고 항목

- gx_studio_widget_create

## <a name="gx_studio_display_configure"></a>gx_studio_display_configure

GUIX Studio 프로젝트에서 정의된 디스플레이 구성

### <a name="prototype"></a>프로토타입

```C
UINT *gx_studio_display_configure(
    USHORT display,
    UINT (*driver)(GX_DISPLAY *),
    USHORT language, 
    USHORT theme,
    GX_WINDOW_ROOT **return_root);
```

### <a name="description"></a>Description

이 서비스는 사용할 준비가 되도록 GX_DISPLAY를 초기화합니다. GX_DISPLAY 제어 블록을 초기화하고, 화면에 맞게 캔버스를 만들고, 캔버스의 루트 창을 만드는 함수를 통합합니다. 또한 디스플레이가 초기화된 후 요청된 언어와 리소스 테마를 설치합니다.

이 함수는 사용할 디스플레이를 준비하는 데 가장 일반적으로 필요한 프로그래밍 작업을 통합합니다. gx_display_create(), gx_display_color_table_set, gx_display_font_table_set, gx_display_pixelmap_table_set, gx_system_language_table_set, gx_system_active_language_set, gx_system_scroll_appearance_set, gx_canvas_create, gx_window_root_create 함수를 호출하며 모든 함수나 일부 함수가 애플리케이션 프로그램에 필요합니다.

### <a name="parameters"></a>매개 변수

- **display**: Studio 프로젝트 파일의 디스플레이 정의에 해당하는 디스플레이 테이블의 인덱스
- **driver**: 디스플레이 드라이버 초기화 함수에 대한 포인터입니다. 이 함수는 GX_DISPLAY 제어 블록의 간접 함수 포인터를 초기화하고 필요한 하드웨어 설정을 수행하기 위해 호출됩니다.
- **language**: 초기 언어 테이블 인덱스
- **theme**: 초기 테마 인덱스
- **root**: 루트 창 주소를 반환할 변수에 대한 포인터 또는 GX_NULL

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 성공했습니다.
- **GX_FAILURE**: (0x11) 디스플레이를 초기화할 수 없습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create the widget named “child_popup”, which is a child of the
   top-level screen “main_screen”. */

GX_WIDGET *menu_screen;

status = gx_studio_display_configure(MAIN_DISPLAY,
    my_driver_setup, LANGUAGE_ENGLISH, DEFAULT_THEME, GX_NULL);

/* If status == GX_SUCCESS the display was initialized, a canvas was
created for the display, a root window was created for the canvas, and
the requested language and theme have been installed.
*/
```

### <a name="see-also"></a>참고 항목

- gx_display_create
- gx_display_color_table_set
- gx_display_font_table_set
- gx_display_pixelmap_table_set
- gx_system_language_table_set
- gx_system_active_language_set
- gx_system_scroll_appearance_set
- gx_canvas_create
- gx_window_root_create

## <a name="gx_system_active_language_set"></a>gx_system_active_language_set

활성 언어 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_active_language_set(GX_UBYTE language);
```

### <a name="description"></a>Description

이 서비스는 현재 언어를 설정합니다. 언어 인덱스는 애플리케이션 문자열 테이블의 열 수보다 적어야 합니다. 이 함수는 사용되지 않으며 gx_display_active_language_set으로 대체되었습니다. 모든 새 애플리케이션에서는 gx_display_active_langauge_set을 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **language**: 리소스 헤더 파일에 정의된 언어 인덱스

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 활성 언어를 설정했습니다.
- **GX_CALLER_ERROR**: **(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: **(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**: **(0x22) 언어 인덱스가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set active language and mark widget canvas as dirty. */
status = gx_system_active_language_set(ID_LANGUAGE_ENGLISH);

/* If status is GX_SUCCESS the active language has been assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_display_language_table_set
- gx_display_active_langauge_set
- gx_display_string_get

## <a name="gx_system_animation_get"></a>gx_system_animation_get

시스템 풀에서 애니메이션 제어 블록 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_animation_get(GX_ANIMATION **animation);
```

### <a name="description"></a>Description

이 서비스를 사용하여 gx_system 구성 요소에서 유지 관리되는 제어 블록 풀에서 애니메이션 제어 블록을 가져올 수 있습니다. 애니메이션 제어 블록 풀 및 관련 API 서비스는 GX_ANIMATION_POOL_SIZE 상수가 값 0으로 정의된 경우에만 제공됩니다. 이 값의 기본 설정은 6입니다. 즉, 시스템 애니메이션 제어 블록 풀에는 크기 GX_ANIMATION 제어 블록이 포함됩니다.

애니메이션이 완료되면 이 API를 사용하여 할당된 애니메이션 제어 블록이 자동으로 사용 가능한 풀로 반환됩니다. gx_animation_stop을 사용하여 애니메이션을 중지하거나 반환된 오류로 인해 애니메이션을 시작하지 못한 경우 애플리케이션에서 gx_system_animation_free를 사용하여 애니메이션 제어 블록을 사용 가능한 풀로 반환해야 합니다.

### <a name="parameters"></a>매개 변수

- **animation**: GX_ANIMATION 포인터를 받을 포인터의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 애니메이션 제어 블록을 가져왔습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 애니메이션 포인터가 잘못되었습니다.
- **GX_OUT_OF_ANIMATIONS**: (0x31) 시스템 애니메이션 풀이 모두 사용되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_ANIMATION *animation;

UINT status = gx_system_animation_get(&animation);

if (status == GX_SUCCESS)
{
    gx_animation_start(animation, animation_info);
}
```

### <a name="see-also"></a>참고 항목

- gx_animation_create
- gx_animation_start
- gx_animation_stop
- gx_system_animation_free

## <a name="gx_system_animation_free"></a>gx_system_animation_free

애니메이션 제어 블록을 시스템 풀로 반환

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_animation_free(GX_ANIMATION *animation);
```

### <a name="description"></a>Description

이 서비스를 사용하여 애니메이션 제어 블록을 시스템 풀로 반환할 수 있습니다. 애니메이션 제어 블록 풀 및 관련 API 서비스는 GX_ANIMATION_POOL_SIZE 상수가 값 0으로 정의된 경우에만 제공됩니다. 이 값의 기본 설정은 6입니다. 즉, 시스템 애니메이션 제어 블록 풀에는 크기 GX_ANIMATION 제어 블록이 포함됩니다.

애니메이션이 완료되면 gx_system_animation_get()을 사용하여 할당된 애니메이션 제어 블록이 자동으로 사용 가능한 풀로 반환됩니다. 이미 사용 가능한 풀로 반환된 애니메이션 제어 블록을 사용 가능한 풀로 반환하려고 하면 아무런 효과가 없습니다.

gx_animation_stop을 사용하여 애니메이션을 중지하거나 반환된 오류로 인해 애니메이션을 시작하지 못한 경우 애플리케이션에서 gx_system_animation_free()를 사용하여 gx_system_animation_get()으로 가져온 애니메이션 제어 블록을 사용 가능한 풀로 반환해야 합니다.

유휴 상태인 애니메이션만 사용 가능한 풀로 반환할 수 있습니다. 애니메이션이 시작되지 않았거나, 중지되었거나, 완료된 경우 유휴 상태입니다.

### <a name="parameters"></a>매개 변수

- **animation**: GX_ANIMATION 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 애니메이션 블록을 해제했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 애니메이션 포인터가 잘못되었습니다.
- **GX_INVALID_ANIMATION**: (0x32) 애니메이션이 유휴 상태가 아니거나 시스템 풀에서 할당되지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_ANIMATION *animation;

UINT status = gx_system_animation_get(&animation);

if (status == GX_SUCCESS)
{
    status = gx_animation_start(animation, animation_info);

    if (status != GX_SUCCESS)
    {
        /* animation did not start, return it to the free pool */
        gx_system_animation_free(animation);
    }
}
```

### <a name="see-also"></a>참고 항목

- gx_animation_create
- gx_animation_start
- gx_animation_stop
- gx_system_animation_get

## <a name="gx_system_bidi_text_disable"></a>gx_system_bidi_text_disable

동적 양방향 텍스트 지원 사용 안 함

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_bidi_text_disable(VOID);
```

### <a name="description"></a>Description

이 서비스는 동적 양방향 텍스트 지원을 사용하지 않도록 설정합니다. 서비스를 사용하려면 GUIX 라이브러리를 빌드할 때 GX_DYNAMIC_BIDI_TEXT_SUPPORT를 정의해야 하며, 런타임에 양방향 문자열 데이터를 다시 정렬해야 하는 경우에만 서비스가 필요합니다. 대부분의 애플리케이션은 GUIX Studio를 활용하여 다시 정렬된 양방향 텍스트 문자열을 올바르게 생성합니다.

### <a name="parameters"></a>매개 변수

**없음**

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 양방향 텍스트 지원을 사용하지 않도록 설정했습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* GX_DYNAMIC_BIDI_TEXT_SUPPORT is defined. */

/* Diable bidi text support. */
status = gx_system_bidi_text_disable();

/* If status is GX_SUCCESS, bidi text support was disabled. */
```

### <a name="see-also"></a>참고 항목

- gx_system_bidi_text_enable

## <a name="gx_system_bidi_text_enable"></a>gx_system_bidi_text_enable

동적 양방향 텍스트 지원 사용

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_bidi_text_enable(VOID);
```

### <a name="description"></a>Description

이 서비스는 동적 양방향 텍스트 지원을 사용하도록 설정합니다. 서비스를 사용하려면 GUIX 라이브러리를 빌드할 때 GX_DYNAMIC_BIDI_TEXT_SUPPORT를 정의해야 하며, 런타임에 양방향 문자열 데이터를 다시 정렬해야 하는 경우에만 서비스가 필요합니다. 대부분의 애플리케이션은 GUIX Studio를 활용하여 다시 정렬된 양방향 텍스트 문자열을 올바르게 생성합니다.

### <a name="parameters"></a>매개 변수

**없음**

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 양방향 텍스트 지원을 사용하도록 설정했습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* GX_DYNAMIC_BIDI_TEXT_SUPPORT is defined. */

/* Enable bidi text support. */
status = gx_system_bidi_text_enable();

/* If status is GX_SUCCESS, bidi text support was enabled. */
```

### <a name="see-also"></a>참고 항목

- gx_system_bidi_text_disable

## <a name="gx_system_canvas_refresh"></a>gx_system_canvas_refresh

모든 더티 캔버스 새로 고침

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_canvas_refresh(VOID);
```

### <a name="description"></a>Description

이 서비스는 모든 더티 위젯 및 캔버스를 즉시 다시 그립니다. 일반적으로 GUIX 시스템 구성 요소에서 내부적으로 호출되지만 애플리케이션에서 호출하여 즉시 시스템 다시 그리기 작업을 강제로 적용할 수 있습니다.

### <a name="parameters"></a>매개 변수

**없음**

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 애니메이션 블록을 해제했습니다.
- **GX_INVALID_CANVAS**: (0x20) 생성된 캔버스가 없습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Force immediate redraw operation. */
status = gx_system_canvas_refresh();

/* If status is GX_SUCCESS, canvas has been redraw. */
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_dirty_mark"></a>gx_system_dirty_mark

영역을 더티로 표시

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_dirty_mark(GX_WIDGET *widget);
```

### <a name="description"></a>Description

이 서비스는 이 위젯의 영역을 더티로 표시합니다. 이렇게 하면 시스템 이벤트 처리가 완료될 때 다시 그리기 위해 위젯이 큐에 대기됩니다.

### <a name="parameters"></a>매개 변수

- **widget**: 위젯 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 위젯을 더티로 표시했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Mark widget “my_widget” as dirty. */
status = gx_system_dirty_mark(&my_widget);

/* If status is GX_SUCCESS the area associated
   with “my_widget” has been marked as dirty. */
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_dirty_partial_add"></a>gx_system_dirty_partial_add

부분 영역을 더티로 표시

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_dirty_partial_add(
    GX_WIDGET *widget,
    GX_RECTANGLE *dirty_area);
```

### <a name="description"></a>Description

이 서비스는 이 위젯의 일부 영역을 더티로 표시합니다. 이렇게 하면 시스템 이벤트 처리가 완료된 경우 GUIX 캔버스 새로 고침 작업을 통해 다시 그리기 위해 위젯이 큐에 대기됩니다.

### <a name="parameters"></a>매개 변수

- **widget**: 위젯 제어 블록에 대한 포인터
- **dirty_area**: 더티로 표시할 위젯의 더티 영역

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 일부 영역을 더티로 표시했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_SIZE**: (0x19) 더티 영역의 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Mark widget “my_widget” partial area as dirty. */

status = gx_system_dirty_partial_add(&my_widget,
    &partial_area);

/* If status is GX_SUCCESS the partial area “partial_area”
associated with “my_widget” has been marked as dirty. */
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_draw_context_get"></a>gx_system_draw_context_get

그리기 컨텍스트 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_draw_context_get(GX_DRAW_CONTEXT **current_context);
```

### <a name="description"></a>Description

이 서비스는 현재 그리기 컨텍스트에 대한 포인터를 반환합니다.

### <a name="parameters"></a>매개 변수

- **current_context**: 현재 그리기 컨텍스트 포인터 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 현재 컨텍스트를 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_DRAW_CONTEXT *current_context;

/* Get current drawing context. */

status = gx_system_draw_context_get(&current_context);

/* If status is GX_SUCCESS the current drawing context
   is contained in “current_context”. */
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_event_fold"></a>gx_system_event_fold

이벤트 보내기

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_event_fold(GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 GUIX 이벤트 큐에서 동일한 유형의 이벤트를 검색합니다. 동일한 유형의 이벤트가 있으면 이벤트 페이로드가 새 이벤트와 일치하도록 업데이트됩니다. 일치하는 이벤트가 없으면 이벤트 큐의 끝에 새 이벤트를 추가하기 위해 gx_system_event_send 함수가 호출됩니다.

이 함수는 여러 PEN_DRAG 이벤트로 이벤트 큐를 채울 수 없도록 하기 위해 빠른 터치식 입력 드라이버에서 일반적으로 사용됩니다. 동일한 유형의 여러 이벤트가 GUIX 이벤트 큐에 추가되지 않도록 하기 위해 애플리케이션에서 함수를 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **event**: 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 이벤트를 보냈습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_EVENT my_event;

memset(&my_event, 0, sizeof(GX_EVENT));

my_event.gx_event_type = GX_EVENT_PEN_DOWN;

my_event.gx_event_payload.gx_event_pointdata.gx_point_x = 100;
my_event.gx_event_payload.gx_event_pointdata.gx_point_y = 200;

/* Send “my_event” for processing. */
status = gx_system_event_fold(&my_event);

/* If status is GX_SUCCESS the event has been sent for processing. */
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_event_send"></a>gx_system_event_send

이벤트 보내기

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_event_send(GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 지정된 이벤트를 GUIX 시스템 이벤트 큐로 보냅니다. 새 이벤트는 큐의 끝에 배치됩니다.

### <a name="parameters"></a>매개 변수

- **event**: 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 이벤트를 보냈습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Send “new_event” for processing. */

GX_EVENT new_event;

new_event.gx_event_target = widget ->gx_widget_parent;
new_event.gx_event_type = MY_EVENT_TYPE;

/* Set optional param. */
new_event.gx_event_payload.xxxx = yyyy
new_event.gx_event_sender = widget->gx_widget_id;

/* Push the event to event pool. */
status = gx_system_event_send(&new_event);

/* If status is GX_SUCCESS the event has been sent for processing. */
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_focus_claim"></a>gx_system_focus_claim

포커스 클레임

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_focus_claim(GX_WIDGET *widget);
```

### <a name="description"></a>Description

이 서비스는 지정된 위젯의 포커스를 클레임합니다. 이전에 포커스가 없었던 위젯은 GX_EVENT_FOCUS_GAINED 이벤트를 받게 됩니다.

### <a name="parameters"></a>매개 변수

- **widget**: 포커스를 클레임할 위젯 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 포커스를 클레임했습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_NO_CHANGE**: (0x08) 위젯이 이미 포커스를 소유하고 있습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Claim focus for widget “my_widget”. */
status = gx_system_claim_focus(&my_widget);

/* If status is GX_SUCCESS the focus has been claimed for
   “my_widget”. */
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_initialize"></a>gx_system_initialize

GUIX 초기화

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_initialize(VOID);
```

### <a name="description"></a>Description

이 서비스는 GUIX를 초기화합니다. 다른 GUIX API 서비스보다 먼저 호출되어야 하며 시스템을 시작할 때 한 번만 호출되어야 합니다.

### <a name="parameters"></a>매개 변수

- **없음**

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 시스템을 초기화했습니다.
- **GX_SYSTEM_ERROR**: (0xFE) GX_EVENT 제어 블록 크기가 잘못되었거나 이벤트 큐/뮤텍스/스레드를 만들지 못했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Initialize GUIX. */
status = gx_system_initialize();

/* If status is GX_SUCCESS, GUIX has been initialized. */
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_language_table_get"></a>gx_system_language_table_get

활성 언어 테이블 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_language_table_get( 
    GX_CHAR ****language_table,
    GX_UBYTE *languages_count, 
    UINT *string_count);
```

### <a name="description"></a>Description

이 서비스는 활성 언어 테이블을 검색합니다. 이 함수는 사용되지 않으며 gx_display_language_table_get으로 대체되었습니다. 모든 새 애플리케이션에서는 gx_display_language_table_get을 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **language_table**: 언어 테이블을 반환할 포인터의 주소
- **languages_count**: 테이블 열을 반환할 변수의 주소
- **string_count**: 테이블 행을 반환할 포인터의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 활성 언어 테이블을 검색했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CHAR ***language_table;

GX_UBYTE language_count;

UINT string_count;

/* Retrieve the language table */

status = gx_system_language_table_get(&language_table,
    &language_count, &string_count);
```

### <a name="see-also"></a>참고 항목

- gx_display_language_table_get
- gx_display_language_table_set

## <a name="gx_system_language_table_set"></a>gx_system_language_table_set

활성 언어 테이블 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_language_table_set(
    GX_CHAR ***language_table,
    GX_UBYTE languages_count, 
    UINT string_count);
```

### <a name="description"></a>Description

이 서비스는 활성 언어 테이블을 설치합니다. 이 함수는 사용되지 않으며 gx_display_language_table_set으로 대체되었습니다. 모든 새 애플리케이션에서는 gx_display_language_table_set을 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **language_table**: 언어 테이블에 대한 포인터
- **languages_count**: 테이블의 언어 수
- **string_count**: 문자열 테이블 행 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 언어 테이블을 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Retrieve the language table */

status = gx_system_language_table_set(language_table,
    language_count, string_count);
```

### <a name="see-also"></a>참고 항목

- gx_display_language_table_set
- gx_display_language_table_get
- gx_display_active_language_set

## <a name="gx_system_memory_allocator_set"></a>gx_system_memory_allocator_set

메모리 할당, 할당 취소를 위해 함수 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_memory_allocator_set(VOID *(allocate)(ULONG size),
    VOID(*release)(VOID *));
```

### <a name="description"></a>Description

이 서비스는 동적 메모리 할당 및 할당 취소를 위해 애플리케이션에서 제공된 콜백 함수를 할당합니다.

동적 메모리 할당을 사용하는 GUIX 서비스가 애플리케이션에 필요하지 않은 경우에는 이 서비스를 호출할 필요가 없습니다.

이 서비스를 사용하는 경우 GUIX 서비스 포인터를 지우는 gx_system_initialize() 이후, 동적 메모리 할당을 사용해야 하는 GUIX 서비스 이전에 서비스를 호출해야 합니다.

런타임 메모리 할당 및 할당 취소 서비스를 필요로 하는 GUIX 서비스에는 다음이 포함됩니다.

- 외부 스토리지의 이진 리소스를 GUIX 런타임 환경으로 로드
- 소프트웨어 런타임 jpeg 이미지 디코더
- 소프트웨어 런타임 png 이미지 디코더
- GX_STYLE_TEXT_COPY에서 텍스트 위젯 사용
- 런타임 pixemap 크기 조정 및 순환 유틸리티 함수
- 런타임 화면 및 위젯 제어 블록 할당

### <a name="parameters"></a>매개 변수

- **allocator**: 메모리 할당자 함수
- **release**: 메모리 해제 함수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 메모리 할당 함수를 할당했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

다음 예제에서는 ThreadX 바이트 풀을 활용하여 스레드로부터 안전한 동적 메모리 할당 및 메모리 할당 취소 서비스를 구현합니다.

```C
TX_BYTE_POOL memory_pool;

#define SCRATCHPAD_SIZE (1024 * 4)

ULONG scratchpad[SCRATCHPAD_SIZE];

/* define memory allocation service */

VOID *memory_allocate(ULONG size)
{
    VOID *memptr;

    if (tx_byte_allocate(&memory_pool, &memptr, size, TX_NO_WAIT) == TX_SUCCESS)
    {
        return memptr;
    }
    return NULL;
}

/* define memory de-allocation service */
void memory_free(VOID *mem)
{
    tx_byte_release(mem);
}

/* create byte pool and install our dynamic memory services with GUIX
*/

VOID tx_application_define(void *first_unused_memory)
{
    /* create byte pool for GUIX to use */
    tx_byte_pool_create(&memory_pool, "scratchpad", scratchpad,
        SCRATCHPAD_SIZE * sizeof(ULONG));

    guix_setup();

    /* install our memory allocator and de-allocator */
    gx_system_memory_allocator_set(memory_allocate, memory_free);
}
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_pen_configure"></a>gx_system_pen_configure

펜 구성 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_pen_configure(GX_PEN_CONFIGURATION *pen_configuration);
```

### <a name="description"></a>Description

이 서비스는 펜 구성을 설정하여 GX_EVENT_FLICK 이벤트 유형 생성을 트리거하는 데 사용되는 펜 속도 및 거리 매개 변수를 제어합니다.

GX_PEN_CONFIGURATION의 gx_pen_configuration_min_drag_dist 멤버는 고정 소수점 데이터 형식이며 GX_FIXED_VAL_MAKE(value)를 사용하여 INT에서 GX_FIXED_VAL로 변환해야 합니다. 예를 들어 최소 끌기 거리를 틱당 0.5픽셀로 설정하려면 gx_pen_configuration_min_drag_dist를 `GX_FIXED_VAL_MAKE(1) / 2`로 설정해야 합니다.

GUIX 릴리스 5.4.0 이상에서 GX_PEN_CONFIGURATION의 gx_pen_configuration_min_drag_dist 멤버는 GX_FIXED_VAL 형식이 아닌 (INT << 8) 형식이었습니다. 5.4.0 버전 GUIX 라이브러리를 포함하는 프로젝트에서 이 API를 사용하는 경우 GUIX 라이브러리를 빌드할 때 min_drag_dist 매개 변수를 수정하거나 #define GUIX_5_4_0_COMPATIBILITY를 수행해야 합니다.

### <a name="parameters"></a>매개 변수

- **pen_configuration** 펜 구성 구조체에 대한 포인터입니다. **부록 I** 에는 GX_PEN_CONFIGURATION 구조체의 정의가 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 펜 구성을 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Define pen configuration, set minimum drag distance to 0.5 pixel
per tick, maximum pen speed to 10 ticks. That means GUIX will trigger
a vertical or horizontal flick event if the drag time is smaller than
10 ticks and the drag distance is bigger than 0.5 * drag_ticks. */

GX_PEN_CONFIGURATION pen_configuration;

#if defined(GUIX_5_4_0_COMPATIBILITY)
Pen_configuration.gx_pen_configuration_min_drag_dist = (1 << 8)/ 2;
#else
pen_configuration.gx_pen_configuration_min_drag_dist = GX_FIXED_VAL_MAKE(1) / 2;
#endif

pen_configuration.gx_pen_configuration_max_pen_speed_ticks = 10;

/* Set the pen configuration. */
status = gx_system_pen_configure(&pen_configuration);

/* If status is GX_SUCCESS the touch configure has been set. */
```

## <a name="gx_system_screen_stack_create"></a>gx_system_screen_stack_create

시스템 화면 스택 만들기 및 초기화

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_screen_stack_create(
    GX_WIDGET **memory, 
    INT size);
```

### <a name="description"></a>Description

이 서비스는 시스템 화면 스택에 사용할 메모리 풀을 정의합니다. 시스템 화면 스택은 애플리케이션에서 애플리케이션 화면 흐름 모양을 관리하는 데 사용할 수 있는 선택적 기능입니다.

애플리케이션에서 화면 스택 서비스를 활용하려는 경우 먼저 gx_system_screen_stack_create 함수를 호출하여 화면 스택 메모리 영역을 설정해야 합니다.

### <a name="parameters"></a>매개 변수

- **memory**: 예약된 메모리 블록에 대한 포인터
- **size**: 예약된 메모리 블록의 크기(바이트)

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 만들었습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
#define SCREEN_STACK_DEPTH 8
GX_WIDGET *screen_stack[SCREEN_STACK_DEPTH * 2];

UINT status;

/* Get the scrollbar appearance. */

status = gx_system_screen_stack_create(screen_stack,
    sizeof(GX_WIDGET *) * SCREEN_STACK_DEPTH * 2);

/* If status is GX_SUCCESS the system screen stack is initialized
and ready for use. */
```

### <a name="see-also"></a>참고 항목

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_get"></a>gx_system_screen_stack_get

맨 위에 있는 화면 스택 포인터 팝

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_screen_stack_get(
    GX_WIDGET **popped_parent,
    GX_WIDGET **popped_screen);
```

### <a name="description"></a>Description

이 함수는 맨 위에 있는 화면 스택 포인터를 팝하고 해당 포인터를 호출자에게 반환합니다. 팝된 화면이 이전 부모에 자동으로 다시 연결되지 않는다는 점에서 gx_system_screen_stack_pop()과는 다릅니다. 대신, 포인터가 스택에서 팝되어 호출자에게 반환되므로 호출자가 반환된 화면을 원하는 대로 연결하거나 삭제할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **popped_parent**: 부모 위젯 포인터를 저장할 위치
- **popped_screen**: 팝된 화면 포인터를 저장할 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 화면 스택 포인터를 검색했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_FAILURE**: (0x10) 화면 스택이 잘못되었거나 비어 있습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
UINT status;

GX_WIDGET *parent_screen;

GX_WIDGET *popped_screen;

/* Pop a screen stack entry. */
status = gx_system_screen_stack_get(&parent_screen, &popped_screen);

/* If status is GX_SUCCESS, parent_screen and
popped_screen hold the topmost screen stack pointers. */
```

### <a name="see-also"></a>참고 항목

- gx_system_screen_stack_create
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_pop"></a>gx_system_screen_stack_pop

시스템 화면 스택에서 맨 위에 있는 항목 팝

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_screen_stack_pop();
```

### <a name="description"></a>Description

이 함수는 화면 스택의 맨 위에 있는 항목을 팝하고 팝된 화면을 팝된 부모 위젯에 자동으로 연결합니다.

### <a name="parameters"></a>매개 변수

**없음**

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 화면 스택 포인터를 검색했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_FAILURE**: (0x10) 화면 스택이 잘못되었거나 비어 있습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
UINT status;

/* Pop a screen stack entry. */
status = gx_system_screen_stack_pop();

/* If status is GX_SUCCESS, the topmost screen stack entry has been
popped from the stack and re-attached to the previous parent. */
```

### <a name="see-also"></a>참고 항목

- gx_system_screen_stack_get
- gx_system_screen_stack_create
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_push"></a>gx_system_screen_stack_push

위젯 및 부모 포인터를 화면 스택으로 푸시

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_screen_stack_push(GX_WIDGET *screen)
```

### <a name="description"></a>Description

이 서비스는 일반적으로 최상위 화면인 표시된 위젯에 대한 포인터를 화면 스택에 배치합니다. 위젯이 부모를 포함하는 경우 부모로부터 분리됩니다. 부모 위젯 포인터도 화면 스택으로 푸시됩니다. 부모 위젯은 NULL일 수 있으므로 부모에 표시되지 않거나 연결되지 않은 화면을 화면 스택으로 푸시할 수 있습니다. 부모가 없는 위젯을 화면 스택으로 푸시하는 경우 팝된 위젯을 이전 부모에 다시 연결하려고 하는 screen_stack_pop() API 대신 screen_stack_get() API를 사용하여 푸시된 화면 포인터를 검색해야 합니다.

### <a name="parameters"></a>매개 변수

- **screen**: 화면 스택으로 푸시할 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 스크롤 막대 모양을 가져왔습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Get the scrollbar appearance. */
status = gx_system_screen_stack_push(window);

/* If status is GX_SUCCESS, the widget pointed to by “window” has
been pushed to the screen stack, along with the widget’s parent
ponter. */
```

### <a name="see-also"></a>참고 항목

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_create
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_reset"></a>gx_system_screen_stack_reset

시스템 화면 스택 다시 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_screen_stack_reset();
```

### <a name="description"></a>Description

이 함수는 시스템 화면 스택에서 모든 항목을 제거합니다. 스택에서 팝된 화면에 GUIX Studio에서 동적으로 할당된 제어 블록이 있는 경우 해당 제어 블록의 메모리가 해제됩니다.

### <a name="parameters"></a>매개 변수

**없음**

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 스크롤 막대 모양을 가져왔습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Get the scrollbar appearance. */
status = gx_system_screen_stack_reset();

/* If status is GX_SUCCESS the system screen stack has been cleared
of entries. */
```

### <a name="see-also"></a>참고 항목

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_create

## <a name="gx_system_scroll_appearance_get"></a>gx_system_scroll_appearance_get

스크롤 모양 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_scroll_appearance_get(
    ULONG style,
    GX_SCROLLBAR_APPEARANCE *return_appearance);
```

### <a name="description"></a>Description

이 서비스는 스크롤 막대 모양을 가져옵니다.

### <a name="parameters"></a>매개 변수

- **style**: 스크롤 막대 스타일(`GX_SCROLLBAR_HORIZONTAL` 또는 `GX_SCROLLBAR_VERTICAL`)
- **return_appearance**: 모양 대상에 대한 포인터입니다. **부록 I** 에는 GX_SCROLLBAR_APPERANCE의 정의가 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 스크롤 막대 모양을 가져왔습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_SCROLLBAR_APPEARANCE my_appearance;

/* Get the scrollbar appearance. */

status = gx_system_scroll_appearance_get(style, &my_appearance);

/* If status is GX_SUCCESS “my_appearance” now contains the scroll
appearance. */
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_set
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_scroll_appearance_set"></a>gx_system_scroll_appearance_set

스크롤 모양 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_scroll_appearance_set(
    ULONG style,
    GX_SCROLLBAR_APPEARANCE *appearance);
```

### <a name="description"></a>Description

이 서비스는 기본 스크롤 모양을 설정합니다. 스크롤을 만들 때 애플리케이션에서 사용자 지정 버전을 제공하지 않는 경우 이 모양 구조체가 사용됩니다.

### <a name="parameters"></a>매개 변수

- **style**: 스크롤 스타일(`GX_SCROLLBAR_HORIZONTAL` 또는 `GX_SCROLLBAR_VERTICAL`)
- **appearance**: 다양한 스크롤 막대 모양 특성으로 초기화된 모양 구조체에 대한 포인터입니다. GX_SCROLLBAR_APPEARANCE 구조체의 정의는 **부록 I** 를 참조하세요.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 스크롤 모양을 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_SCROLLBAR_APPEARANCE my_appearance;

memset(&my_appearance, 0, sizeof(GX_SCROLLBAR_APPEARANCE));

my_appearance.gx_scroll_width = 20;
my_appearance.gx_scroll_thumb_width = 18;

my_appearance.gx_scroll_thumb_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_thumb_border_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_button_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_thumb_travel_min = 20;
my_appearance.gx_scroll_thumb_travel_max = 20;
my_appearance.gx_scroll_thumb_border_style = GX_STYLE_BORDER_THIN;

/* Set the scroll appearance. */

status = gx_system_scroll_appearance_set(GX_SCROLLBAR_VERTICAL, &my_appearance);

/* If status is GX_SUCCESS the scroll appearance has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_start"></a>gx_system_start

GUIX 시작

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_start(VOID);
```

### <a name="description"></a>Description

이 서비스는 GUIX 처리를 시작합니다. 정상적인 상황에서는 함수가 반환되지 않고 대신 GUIX 이벤트 큐 처리를 시작합니다. GUIX 이벤트 큐가 비어 있는 경우 새 이벤트가 GUIX 이벤트 큐에 도착할 때까지 서비스에서 호출 스레드를 일시 중단합니다.

### <a name="parameters"></a>매개 변수

- **없음**

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 시스템을 시작했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Start GUIX. */
status = gx_system_start();

/* If status is GX_SUCCESS . GUIX has been started. */
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_string_get"></a>gx_system_string_get

문자열 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_string_get(
    GX_RESOURCE_ID string_id,
    GX_CHAR **return_string);
```

### <a name="description"></a>Description

이 서비스는 정의된 첫 번째 디스플레이와 현재 활성 언어를 사용하여 지정된 리소스 ID의 문자열을 가져옵니다. 이 함수는 사용되지 않으며 gx_display_string_get으로 대체되었습니다. 모든 새 애플리케이션에서는 gx_display_string_get을 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **string_id**: 문자열 리소스 ID
- **return_string**: 문자열 대상 포인터에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 문자열을 가져왔습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_RESOURCE_ID**: (0x33) 리소스 ID가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Get the string associated with MY_STRING_ID. */

status = gx_system_string_get(MY_STRING_RESOURCE_ID, &my_string);

/* If status is GX_SUCCESS the string is contained in “my_string”.
*/
```

### <a name="see-also"></a>참고 항목

- gx_display_string_get
- gx_display_string_table_get
- gx_display_language_table_set

## <a name="gx_system_string_table_get"></a>gx_system_string_table_get

문자열 테이블 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_string_table_get(
    GX_UBYTE language,
    GX_CHAR ***string_table,
    UINT *get_size);
```

### <a name="description"></a>Description

이 서비스는 첫 번째 디스플레이에서 요청된 언어의 문자열 테이블을 검색합니다. 이 함수는 사용되지 않으며 gx_display_string_table_get으로 대체되었습니다. 모든 새 애플리케이션에서는 gx_display_string_table_get을 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **language**: 언어 인덱스
- **string_table**: 문자열 테이블 포인터의 스토리지 공간에 대한 포인터 또는 호출자가 문자열 테이블에 대한 포인터를 가져올 필요가 없는 경우 NULL
- **get_size**: 문자열 테이블에 있는 문자열 수의 스토리지에 대한 포인터 또는 호출자가 문자열 테이블의 문자열 수를 가져올 필요가 없는 경우 NULL

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 문자열 테이블을 가져왔습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Get the string table. */

CHAR **my_string_table; UINT table_size;

status = gx_system_string_table_get(LANGUAGE_ID_ENGLISH,
    &my_string_table, &table_size);

/* If status is GX_SUCCESS . the pointer to the string table has
been obtained. */
```

### <a name="see-also"></a>참고 항목

- gx_display_string_table_get
- gx_display_string_get
- gx_display_active_language_set
- gx_display_language_table_set

## <a name="gx_system_string_width_get"></a>gx_system_string_width_get

문자열 너비 가져오기(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_string_width_get(
    GX_FONT *font, GX_CHAR *string,
    INT string_length,
    GX_VALUE *return_width);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_system_string_width_get_ext()로 대체되었습니다.

이 서비스는 지정된 글꼴을 사용하여 제공된 문자열의 표시 너비를 픽셀 단위로 컴퓨팅합니다. string_length 매개 변수가 0보다 크거나 같으면 요청된 문자 수만 계산에 포함됩니다. string_length 매개 변수가 -1이면 NULL 종결자까지의 전체 문자열이 계산에 사용됩니다.

### <a name="parameters"></a>매개 변수

- **font**: 문자열 글꼴에 대한 포인터
- **string**: 문자열에 대한 포인터
- **string_length**: 문자열의 길이
- **return_width**: 문자열의 너비 대상

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 문자열 너비를 가져왔습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_FONT**: (0x16) 글꼴이 잘못되었습니다.
- **GX_INVALID_STRING_LENGTH**: (0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Get the string width of “my_string”. */

status = gx_system_string_width_get(&my_font, &my_string,
    strlen(my_string), &my_width);

/* If status is GX_SUCCESS . “my_width” contains the string width.
*/
```

### <a name="see-also"></a>참고 항목

- gx_system_string_width_get_ext

## <a name="gx_system_string_width_get_ext"></a>gx_system_string_width_get_ext

문자열 너비 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_string_width_get_ext(
    GX_FONT *font,
    GX_STRING *string,
    GX_VALUE *return_width);
```

### <a name="description"></a>Description

이 서비스는 지정된 글꼴을 사용하여 제공된 문자열의 표시 너비를 픽셀 단위로 컴퓨팅합니다.

### <a name="parameters"></a>매개 변수

- **font**: 문자열 글꼴에 대한 포인터
- **string**: 문자열에 대한 포인터
- **return_width**: 문자열의 너비 대상

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 문자열 너비를 가져왔습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_FONT**: (0x16) 글꼴이 잘못되었습니다.
- **GX_INVALID_STRING_LENGTH**: (0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING my_string; my_string.gx_string_ptr = “Monday”;

my_string.gx_string_length = strlen(my_string.gx_string_ptr);

/* Get the string width of “my_string”. */

status = gx_system_string_width_get_ext(&my_font,
    &my_string, &my_width);

/* If status is GX_SUCCESS . “my_width” contains the string width.
*/
```

### <a name="see-also"></a>참고 항목

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_timer_start"></a>gx_system_timer_start

타이머 시작

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_timer_start(
    GX_WIDGET *owner, 
    UINT timer_id,
    UINT initial_ticks,
    UINT reschedule_ticks);
```

### <a name="description"></a>Description

이 서비스는 지정된 위젯의 타이머를 시작합니다. GX_MAX_ACTIVE_TIMERS 상수는 지원되는 최대 활성 타이머를 정의했습니다. 이 값의 기본 설정은 32입니다.

### <a name="parameters"></a>매개 변수

- **owner**: 위젯 제어 블록에 대한 포인터
- **timer_id**: 타이머의 ID
- **initial_ticks**: 초기 만료 틱
- **reschedule_ticks**: 주기적 만료 틱

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 타이머를 시작했습니다.
- **GX_OUT_OF_TIMERS**: (0x04) 타이머가 더 이상 없습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) 타이머 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Start a periodic timer for the widget “my_widget”. */
status = gx_system_timer_start(&my_widget, MY_TIMER_ID, 10, 20);

/* If status is GX_SUCCESS . the timer for “my_widget” has been
started. */
```

### <a name="see-also"></a>참고 항목

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_timer_stop"></a>gx_system_timer_stop

타이머 중지

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_timer_stop(
    GW_WIDGET *owner, 
    UINT timer_id);
```

### <a name="description"></a>Description

이 서비스는 호출 위젯과 연결된 지정된 timer_id를 가진 타이머를 중지합니다. 특정 위젯에 연결된 타이머를 모두 중지하기 위해 애플리케이션에서 timer_id 값 0을 전달할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **owner**: 위젯 제어 블록에 대한 포인터
- **timer_id**: 타이머 ID 또는 모든 타이머의 경우 0

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 타이머를 중지했습니다.
- **GX_NOT_FOUND**: (0x09) 타이머 ID를 찾을 수 없습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Stop the periodic timer for the widget “my_widget”. */
status = gx_system_timer_stop(&my_widget, MY_TIMER_ID);

/* If status is GX_SUCCESS . the timer for “my_widget” has been
stopped. */
```

### <a name="see-also"></a>참고 항목

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_version_string_get"></a>gx_system_version_string_get

GUIX 라이브러리 버전 문자열 검색(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_version_string_get(GX_CHAR **version);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_system_version_string_get_ext()로 대체되었습니다.

이 서비스는 GUIX 라이브러리 버전 문자열을 검색합니다.

### <a name="parameters"></a>매개 변수

- **version**: 반환 문자열 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 버전 문자열을 검색했습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CHAR *version;

/* get the library version string. */

status = gx_system_verrsion_string_get(&version);
```

### <a name="see-also"></a>참고 항목

- gx_system_version_string_get_ext()

## <a name="gx_system_version_string_get_ext"></a>gx_system_version_string_get_ext

GUIX 라이브러리 버전 문자열 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_version_string_get(GX_STRING *version);
```

### <a name="description"></a>Description

이 서비스는 GUIX 라이브러리 버전 문자열을 검색합니다.

### <a name="parameters"></a>매개 변수

- **version**: 반환 문자열 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 버전 문자열을 검색했습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_STRING_LENGTH**: (0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING version;

/* get the library version string. */

status = gx_system_version_string_get_ext(&version);
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_widget_find

## <a name="gx_system_widget_find"></a>gx_system_widget_find

위젯 찾기

### <a name="prototype"></a>프로토타입

```C
UINT gx_system_widget_find(
    USHORT widget_id,
    INT search_level, 
    GX_WIDGET **return_search_result);
```

### <a name="description"></a>Description

이 서비스는 지정된 위젯 ID를 검색합니다. gx_widget_find()와 달리 이 함수는 시스템에서 정의된 모든 루트 창의 자식을 검색하므로 표시되는 모든 위젯을 검색합니다. 검색할 위젯의 부모를 알고 있으면 gx_widget_find()를 대신 사용합니다.

### <a name="parameters"></a>매개 변수

- **widget_id**: 검색할 위젯 ID
- **search_level**: 자식 위젯을 검색할 재귀 중첩 수준을 정의합니다. 값이 0이면 각 루트 창의 직계 자식만 검색됩니다. 값이 GX_SEARCH_DEPTH_INFINITE이면 함수는 중첩된 모든 자식에서 요청된 위젯 ID를 검색합니다. 0보다 큰 다른 값의 경우 검색 수준은 이 함수가 요청된 위젯 ID를 검색하는 중첩 깊이를 정의합니다.
- **return_search_result**: 찾은 위젯 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 위젯을 검색했습니다.
- **GX_NOT_FOUND**: (0x09) 위젯 ID를 찾을 수 없습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Search recursively from the top level widget for the widget with
ID of MY_WIDGET_ID. */

status = gx_system_widget_find(MY_WIDGET_ID,
    GX_SEARCH_DEPTH_INFINITE,
    &my_widget);

/* If status is GX_SUCCESS . the search was successful and
“my_widget” contains the pointer to the widget. */
```

### <a name="see-also"></a>참고 항목

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get

## <a name="gx_text_button_create"></a>gx_text_button_create

텍스트 단추 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_button_create(
    GX_TEXT_BUTTON *text_button,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, 
    ULONG style,
    USHORT text_button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 텍스트 단추 위젯을 만듭니다.

GX_TEXT_BUTTON은 GX_BUTTON에서 파생되며 gx_button API 서비스를 모두 지원합니다.

### <a name="parameters"></a>매개 변수

- **text_button**: 텍스트 단추 컨트롤 블록에 대한 포인터
- **name**: 텍스트 단추의 논리적 이름
- **parent**: 단추의 부모 위젯에 대한 포인터
- **text_id**: 텍스트의 리소스 ID
- **style**: 텍스트 단추 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **text_button_id**: 애플리케이션에서 정의된 텍스트 단추 ID
- **size**: 단추의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 텍스트 단추를 만들었습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**: (0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**: (0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 부모 위젯이 잘못되었습니다.


### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_TEXT_BUTTON my_text_button;

GX_RECTANGLE size;

/* Define widget size. */

gx_utility_rectangle_define(&size, 0, 0, 100, 100);

/* Create text button “my_text_button”. */

status = gx_text_button_create(&my_text_button, "my text button",
    &my_parent_window, MY_TEXT_RESOURCE_ID,
    GX_STYLE_BUTTON_TOGGLE, MY_TEXT_BUTTON_ID, &size);

/* If status is GX_SUCCESS, the text button “my_text_button” was
created. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_color_set
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_draw"></a>gx_text_button_draw

텍스트 단추 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_text_button_draw(GX_TEXT_BUTTON *button);
```

### <a name="description"></a>Description

이 서비스는 텍스트 단추를 그립니다. 일반적으로 캔버스를 새로 고치는 동안 내부적으로 호출되지만 사용자 지정 텍스트 단추 그리기 함수에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **button**: 텍스트 단추 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom text button draw function. */

VOID my_text_button_draw(GX_TEXT_BUTTON *text_button)
{
    /* Call default text button draw. */
    gx_text_button_draw(text_button);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_event_process
- gx_text_button_color_set
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_event_process"></a>gx_text_button_event_process


텍스트 단추 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_button_event_process(GX_TEXT_BUTTON *text_button, GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 텍스트 단추에 대한 이벤트를 처리합니다. 사용자 지정 텍스트 단추 이벤트 처리 함수에서 기본 이벤트 처리기로 호출되어야 합니다.

### <a name="parameters"></a>매개 변수

- **text_button** 텍스트 단추 컨트롤 블록에 대한 포인터
- **event_ptr** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트 단추 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic text button event processing as part of custom event processing function. */

UINT custom_text_button_event_process(GX_TEXT_BUTTON *text_button, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default text button event processing */
        status = gx_text_button_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_color_set
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_font_set"></a>gx_text_button_font_set

텍스트 단추에 글꼴 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_button_font_set(
    GX_TEXT_BUTTON *button,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Description

이 서비스는 지정된 단추에 글꼴을 할당합니다.

### <a name="parameters"></a>매개 변수

- **button**: 텍스트 단추 컨트롤 블록에 대한 포인터
- **font_id**: 글꼴의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 글꼴을 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the text button with the font ID MY_FONT. */
status = gx_text_button_font_set(&my_text_button, MY_FONT);

/* If status is GX_SUCCESS, the font of the text button
“my_text_button” was set to MY_FONT. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_color_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_color_set"></a>gx_text_button_text_color_set

텍스트 단추 색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_button_text_color_set(
    GX_TEXT_BUTTON *text_button,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id);
```

### <a name="description"></a>Description

이 서비스는 텍스트 단추의 색을 설정합니다.

### <a name="parameters"></a>매개 변수

- **text_button**: 텍스트 단추 컨트롤 블록에 대한 포인터
- **normal_text_color_id**: 표준 텍스트 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **selected_text_color_id**: 선택된 텍스트 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **disabled_text_color_id**: 사용할 수 없는 텍스트 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 텍스트 단추 색을 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the color of the text button “my_text_button”. */
status = gx_text_button_text_color_set(&my_text_button,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS, the text color of “my_text_button” was
set. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_draw"></a>gx_text_button_text_draw

단추 텍스트를 그리기 위한 지원 함수

### <a name="prototype"></a>프로토타입

```C
VOID gx_text_button_text_draw(GX_TEXT_BUTTON *text_button);
```

### <a name="description"></a>Description

이 지원 함수는 텍스트 단추의 텍스트 부분을 그립니다. gx_text_button_draw에서 내부적으로 호출되며, 사용자 지정 단추 그리기 함수를 정의하는 애플리케이션의 편의를 위해 별도의 API로 제공됩니다. 단추 배경 그리기를 사용자 지정하려는 애플리케이션은 사용자 지정 그리기 함수를 제공하고 사용자 지정 그리기의 일부로 gx_text_button_text_draw 서비스를 호출하여 배경에 단추 텍스트를 그릴 수 있습니다.

### <a name="parameters"></a>매개 변수

- **text_button**: 텍스트 단추 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Define a custom drawing function */

VOID my_button_draw(GX_TEXT_BUTTON *button)
{
    /* Insert code here to draw button background */

    /* Call support function to do text drawing */
    gx_text_button_text_draw(button);

    /* Draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) button);
}
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_get"></a>gx_text_button_text_get

텍스트 단추에서 텍스트 가져오기(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_button_text_get(
    GX_TEXT_BUTTON *text_button,
    GX_CHAR **return_text);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_text_button_text_get_ext()로 대체되었습니다.

이 서비스는 텍스트 단추에서 지정된 문자열을 검색합니다.

### <a name="parameters"></a>매개 변수

- **text_button**: 텍스트 단추 컨트롤 블록에 대한 포인터
- **return_text**: 텍스트 단추에서 검색된 문자열에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 단추에서 텍스트를 가져왔습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CHAR *string;

/* Get the string from the text button “my_text_button”. */
status = gx_text_button_text_get(&my_text_button, &string);

/* If status is GX_SUCCESS, the string pointer from
“my_text_button” is retrieved and stored in string. */
```

### <a name="see-also"></a>참고 항목

- gx_text_button_text_get_ext

## <a name="gx_text_button_text_get_ext"></a>gx_text_button_text_get_ext

텍스트 단추에서 텍스트 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_button_text_get_ext(
    GX_TEXT_BUTTON *text_button,
    GX_STRING *return_string);
```

### <a name="description"></a>Description

이 서비스는 텍스트 단추에서 지정된 문자열을 검색합니다.

### <a name="parameters"></a>매개 변수

- **text_button**: 텍스트 단추 컨트롤 블록에 대한 포인터
- **return_string**: 텍스트 단추에서 검색된 문자열에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 단추에서 텍스트를 가져왔습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING string;

/* Get the string from the text button “my_text_button”. */
status = gx_text_button_text_get_ext(&my_text_button, &string);

/* If status is GX_SUCCESS, the string pointer and length from
“my_text_button” is retrieved and stored in string. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_id_set"></a>gx_text_button_text_id_set

텍스트 단추에 텍스트 리소스 ID 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_button_text_id_set(
    GX_TEXT_BUTTON *text_button,
    RESOURCE_ID string_id);
```

### <a name="description"></a>Description

이 서비스는 텍스트 단추에 지정된 문자열 리소스 ID를 설정합니다.

### <a name="parameters"></a>매개 변수

- **text_button**: 텍스트 단추 컨트롤 블록에 대한 포인터
- **string_id**: 문자열의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 텍스트 단추에 문자열 리소스 ID를 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_RESOURCE_ID**: (0x33) 문자열 ID가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the string ID ”MY_STRING_ID” to the text button
“my_text_button”. */

status = gx_text_button_text_id_set(&my_text_button,
    MY_STRING_ID);

/* If status is GX_SUCCESS, the string ID MY_STRING_ID was set to
“my_text_button”. */
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_get

## <a name="gx_text_button_text_set"></a>gx_text_button_text_set

텍스트 단추에 텍스트 할당(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_button_text_set(
    GX_TEXT_BUTTON *text_button,
    GX_CHAR *text);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_text_button_text_set_ext()로 대체되었습니다.

이 서비스는 텍스트 단추에 지정된 문자열을 할당합니다. GX_STYLE_TEXT_COPY 스타일을 사용하여 생성된 text_button 위젯은 할당된 텍스트 문자열의 프라이빗 복사본을 만듭니다. GX_STYLE_TEXT_COPY가 활성 상태가 아니면 위젯이 들어오는 문자열의 프라이빗 복사본을 만들지 않으므로 문자열을 정적이나 전역으로 할당해야 합니다. 즉, 자동 또는 임시 변수를 사용할 수 없습니다.

### <a name="parameters"></a>매개 변수

- **text_button**: 텍스트 단추 컨트롤 블록에 대한 포인터
- **text**: NULL로 종료된 문자열에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 단추에 텍스트를 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) 메모리 할당자가 정의되지 않았거나 메모리를 할당하지 못했습니다.
- **GX_INVALID_STRING_LENGTH**: (0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the string “my string” to the text button “my_text_button”.
*/

status = gx_text_button_text_set(&my_text_button, “my string”);

/* If status is GX_SUCCESS, the string “my_text_button” was set.
*/
```

### <a name="see-also"></a>참고 항목

- gx_text_button_event_process
- gx_text_button_text_set_ext
- gx_text_button_text_id_set

## <a name="gx_text_button_text_set_ext"></a>gx_text_button_text_set_ext

텍스트 단추에 텍스트 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_button_text_set_ext(
    GX_TEXT_BUTTON *text_button,
    GX_STRING *string);
```

### <a name="description"></a>Description

이 서비스는 텍스트 단추에 지정된 문자열을 할당합니다. GX_STYLE_TEXT_COPY 스타일을 사용하여 생성된 text_button 위젯은 할당된 텍스트 문자열의 프라이빗 복사본을 만듭니다. GX_STYLE_TEXT_COPY가 활성 상태가 아니면 위젯이 들어오는 문자열의 프라이빗 복사본을 만들지 않으므로 문자열을 정적이나 전역으로 할당해야 합니다. 즉, 자동 또는 임시 변수를 사용할 수 없습니다.

### <a name="parameters"></a>매개 변수

- **text_button**: 텍스트 단추 컨트롤 블록에 대한 포인터
- **string**: GX_STRING 변수에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 단추에 텍스트를 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) 메모리 할당자가 정의되지 않았거나 메모리를 할당하지 못했습니다.
- **GX_INVALID_STRING_LENGTH**: (0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING new_string; new_string.gx_string_ptr = “Monday”;

new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Assign the string “new_string” to the text button
“my_text_button”. */

status = gx_text_button_text_set_ext(&my_text_button, &new_string);

/* If status is GX_SUCCESS, the string “my_text_button” was set.
*/
```

### <a name="see-also"></a>참고 항목

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_get
- gx_text_button_text_id_set

## <a name="gx_text_input_cursor_blink_interval_set"></a>gx_text_input_cursor_blink_interval_set

커서 깜박임 간격 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_input_cursor_blink_interval_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE blink_interval);
```

### <a name="description"></a>Description

이 서비스는 커서의 깜박임 간격 값을 설정합니다.

### <a name="parameters"></a>매개 변수

- **cursor_input** 커서 제어 블록
- **blink_interval** 설정할 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 커서 깜박임 간격을 설정했습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) 깜박임 간격 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set the blink interval value of “input_cursor” to 2. */
status = gx_text_input_cursor_blink_interval_set(input_cursor, 2);

/* If status is GX_SUCCESS, the blink interval value of
“input_cursor” has been successfully set to 2. */
```

### <a name="see-also"></a>참고 항목

- gx_text_input_cursor_height_set
- gx_text_input_cursor_width_set

## <a name="gx_text_input_cursor_height_set"></a>gx_text_input_cursor_height_set

커서 높이 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_input_cursor_height_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE height);
```

### <a name="description"></a>Description

이 서비스는 커서의 높이를 설정합니다.

### <a name="parameters"></a>매개 변수

- **cursor_input**: 커서 제어 블록
- **height** 설정할 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 커서 높이를 설정했습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) 높이 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set height value of “input_cursor”. */
status = gx_text_input_cursor_height_set(&input_cursor, 15);

/* If status is GX_SUCCESS, the height value of “input_curosr” has
been successfully set to 15. */
```

### <a name="see-also"></a>참고 항목

- gx_text_input_cursor_blink_interval_set
- gx_text_input_cursor_width_set

## <a name="gx_text_input_cursor_width_set"></a>gx_text_input_cursor_width_set

커서 너비 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_input_cursor_blink_width_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE *width);
```

### <a name="description"></a>Description

이 서비스는 커서의 너비를 설정합니다.

### <a name="parameters"></a>매개 변수

- **cursor_input**: 커서 제어 블록
- **width**: 설정할 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 커서 너비를 설정했습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) 너비 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set width of “input_curosr” to 2. */

status = gx_text_input_cursor_blink_width_set(&input_cursor, 2);

/* If status is GX_SUCCESS, the width of “input_cursor” has been
successfully set to 2. */
```

### <a name="see-also"></a>참고 항목

- gx_text_input_cursor_blink_interval_set
- gx_text_input_cursor_height_set

## <a name="gx_text_scroll_wheel_callback_set"></a>gx_text_scroll_wheel_callback_set

텍스트 형식 스크롤 휠의 콜백 함수 할당(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_scroll_wheel_callback_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *(*callback)(GX_TEXT_SCROLL_WHEEL *, int));
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_text_scroll_wheel_callback_set_ext()로 대체되었습니다.

이 서비스는 스크롤 휠의 각 행에 표시할 텍스트 문자열을 결정하기 위해 텍스트 형식 스크롤 휠이 호출하는 콜백 함수를 할당합니다.

GX_NUMERIC_SCROLL_WHEEL 및 GX_STRING_SCROLL_WHEEL의 경우 기본 콜백 함수가 제공되며 애플리케이션에서 기본 구현을 사용하기 위해 아무것도 변경할 필요가 없습니다.

이 API는 애플리케이션이 스크롤 휠 위젯의 각 행에 표시되는 문자열의 서식이나 기타 매개 변수를 사용자 지정할 수 있도록 제공됩니다.

콜백 함수는 스크롤 휠 제어 블록에 대한 포인터와 표시되는 행 번호를 입력으로 받습니다. 함수는 텍스트 문자열에 대한 포인터를 반환해야 합니다.

### <a name="parameters"></a>매개 변수

- **wheel** 문자열 스크롤 휠 제어 블록 주소
- **callback** 콜백 함수에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 콜백을 설정했습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_TEXT_SCROLL_WHEEL wheel;

GX_CHAR string_buffer[20];

GX_CHAR *my_wheel_callback(GX_TEXT_SCROLL_WHEEL *wheel, int row)
{
    /* Just for an example, return row number as string for rows
    >= 0, and return text “Invalid” otherwise */
    if (row >= 0)
    {
        gx_utility_ltoa(row, string_buffer, 20);
    }
    else
    {
        return(“Invalid”);
    }
}

gx_text_scroll_wheel_create(&wheel, “my wheel”, root, 10,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|ID_MY_WHEEL, &size);

status = gx_text_scroll_wheel_callback_set(&wheel,
    my_wheel_callback);

/* If status is GX_SUCCESS, the scroll whell callback function has
been set. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_callback_set_ext"></a>gx_text_scroll_wheel_callback_set_ext

텍스트 형식 스크롤 휠의 콜백 함수 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_scroll_wheel_callback_set_ext(
    GX_TEXT_SCROLL_WHEEL *wheel,
    UINT *(*callback)(GX_TEXT_SCROLL_WHEEL *, int, GX_STRING *));
```

### <a name="description"></a>Description

이 서비스는 스크롤 휠의 각 행에 표시할 텍스트 문자열을 결정하기 위해 텍스트 형식 스크롤 휠이 호출하는 콜백 함수를 할당합니다.

GX_NUMERIC_SCROLL_WHEEL 및 GX_STRING_SCROLL_WHEEL의 경우 기본 콜백 함수가 제공되며 애플리케이션에서 기본 구현을 사용하기 위해 아무것도 변경할 필요가 없습니다.

이 API는 애플리케이션이 스크롤 휠 위젯의 각 행에 표시되는 문자열의 서식이나 기타 매개 변수를 사용자 지정할 수 있도록 제공됩니다.

콜백 함수는 스크롤 휠 제어 블록에 대한 포인터와 표시되는 행 번호를 입력으로 받습니다. 함수는 텍스트 문자열에 대한 포인터를 반환해야 합니다.

### <a name="parameters"></a>매개 변수

- **wheel** 문자열 스크롤 휠 제어 블록 주소
- **callback** 콜백 함수에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 콜백을 설정했습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_TEXT_SCROLL_WHEEL wheel;

GX_CHAR string_buffer[20];

UINT *my_wheel_callback(GX_TEXT_SCROLL_WHEEL *wheel, int row,
    GX_STRING *return_string)
{
    /* Just for an example, return row number as string for rows
    >= 0, and return text “Invalid” otherwise */
    if (row >= 0)
    {
        gx_utility_ltoa(row, string_buffer, 20);
        return_string->gx_string_ptr = string_buffer;
        return_string->gx_string_length = strlen(string_buffer);
    }
    else
    {
        return_string->gx_string_ptr = “Invalid”;
        return_string->gx_string_length = strlen(“Invalid”);
    }

    return GX_SUCCESS;
}

gx_text_scroll_wheel_create(&wheel, “my wheel”, root, 10,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|ID_MY_WHEEL, &size);

status = gx_text_scroll_wheel_callback_set_ext(&wheel,
    my_wheel_callback);

/* If status is GX_SUCCESS, the scroll whell callback function has
been set. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_create"></a>gx_text_scroll_wheel_create

텍스트 스크롤 휠 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_scroll_wheel_create(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    ULONG style, 
    USHORT Id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 텍스트 스크롤 휠을 만듭니다. 텍스트 스크롤 휠은 GX_STRING_SCROLL_WHEEL 및 GX_NUMERIC_SCROLL_WHEEL 형식 위젯의 기준 위젯입니다. 이 함수는 gx_string_scroll_wheel_create 및 gx_numeric_scroll_wheel_create에서 내부적으로 호출되며 사용자 지정 스크롤 휠 위젯을 정의하는 애플리케이션의 편의를 위해 별도의 API로 제공됩니다.

### <a name="parameters"></a>매개 변수

- **wheel**: 텍스트 스크롤 휠 제어 블록 주소
- **name**: 애플리케이션에서 정의된 위젯 이름
- **parent**: 휠 부모 또는 GX_NULL
- **total_rows**: 사용자에게 제공할 행의 총수
- **style**: 원하는 스타일 플래그
- **Id**: 애플리케이션에서 정의된 휠 스타일 플래그
- **size**: 초기 스크롤 휠 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 텍스트 스크롤 휠을 만들었습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**: (0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.


### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Define a custom scroll wheel widget. */
typedef MY_SCROLL_WHEEL_STRUCT
{
    GX_TEXT_SCROLL_WHEEL text_scroll_wheel;

    /* Add custom members here. */

} MY_SCROLL_WHEEL;

MY_SCROLL_WHEEL my_scroll_wheel;

UINT my_scroll_wheel_create(MY_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    INT total_rows, ULONG style, USHORT Id,
    GX_CONST GX_RECTANGLE *size)
{
    /* Call base creation. */
    status = gx_text_scroll_wheel_create(
        &wheel.text_scroll_wheel,
        ”my_text_scroll_wheel”, GX_NULL, 7,
        GX_STYLE_ENABLED, ID_MY_SCROLL_WHEEL, &size);

    if (status == GX_SUCCESS)
    {
        /* Add custom initialization here. */
        if(parent)
        {
            gx_widget_link(parent, (GX_WIDGET *)wheel);
        }
    }
}
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_draw"></a>gx_text_scroll_wheel_draw

텍스트 스크롤 휠 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_text_scroll_wheel_draw(GX_TEXT_SCROLL_WHEEL *wheel);
```

### <a name="description"></a>Description

GX_TEXT_SCROLL_WHEEL을 기반으로 하는 모든 휠 형식의 기본 그리기 함수입니다. 텍스트 스크롤 휠 그리기 모양을 사용자 지정해야 하는 애플리케이션에서 함수를 재정의할 수 있습니다.

GX_STRING_SCROLL_WHEEL 및 GX_NUMERIC_SCROLL_WHEEL은 모두 GX_TEXT_SCROLL_WHEEL을 기반으로 하거나 여기서 파생됩니다.

### <a name="parameters"></a>매개 변수

- **wheel**: 문자열 스크롤 휠 제어 블록 주소

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Write a custom wheel draw function. */
UINT my_wheel_draw(GX_TEXT_SCROLL_WHEEL *wheel)
{
    /* Perform default drawing */
    gx_text_scroll_wheel_draw(wheel);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_event_process"></a>gx_text_scroll_wheel_event_process


텍스트 스크롤 휠 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_scroll_wheel_event_process(GX_TEXT_SCROLL_WHEEL *wheel, GX_EVENT *event_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 텍스트 스크롤 휠에 대한 이벤트를 처리합니다. 사용자 지정 텍스트 스크롤 휠 이벤트 처리 함수에서 기본 이벤트 처리기로 호출되어야 합니다.

### <a name="parameters"></a>매개 변수

- **wheel** 텍스트 스크롤 휠 제어 블록에 대한 포인터
- **event_ptr** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 텍스트 스크롤 휠 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic text scroll wheel event processing as part of custom event processing function. */

UINT custom_text_scroll_wheel_event_process(GX_TEXT_SCROLL_WHEEL *wheel, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default text scroll wheel event processing */
        status = gx_text_scroll_wheel_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_font_set"></a>gx_text_scroll_wheel_font_set

스크롤 휠 행을 그리는 데 사용되는 글꼴 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_scroll_font_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_RESOURCE_ID normal_font, 
    GX_RESOURCE_ID selected_font);
```

### <a name="description"></a>Description

텍스트 스크롤 휠 기반 위젯의 텍스트를 그리는 데 사용되는 글꼴을 할당합니다.

### <a name="parameters"></a>매개 변수

- **wheel**: 문자열 스크롤 휠 제어 블록 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 휠 글꼴을 할당했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_NUMERIC_SCROLL_WHEEL wheel;

status = gx_text_scroll_wheel_font_set(&wheel,
    GX_FONT_ID_WHEEL_NORMAL,
    GX_FONT_ID_WHEEL_SELECTED);

/* If status is GX_SUCCESS, the scroll wheel fonts have been assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_text_color_set"></a>gx_text_scroll_wheel_text_color_set

스크롤 휠 행을 그리는 데 사용되는 색 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_text_scroll_wheel_text_color_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCe_ID disabled_text_color);
```

### <a name="description"></a>Description

이 함수는 텍스트 기반 스크롤 휠 행을 그리는 데 사용되는 텍스트 색을 할당합니다.

### <a name="parameters"></a>매개 변수

- **wheel**: 문자열 스크롤 휠 제어 블록 주소
- **normal_text_color**: 선택되지 않은 행을 그리는 데 사용되는 색
- **selected_text_color**: 선택된 행을 그리는 데 사용되는 색
- **disabled_text_color**: 사용할 수 없는 위젯의 텍스트를 그리는 데 사용되는 색

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 스크롤 휠 텍스트 색을 할당했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING_SCROLL_WHEEL wheel;

UINT status = gx_text_scroll_wheel_text_color_set(&wheel,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS, the colors used to draw the wheel text have been assigned. */
```

### <a name="see-also"></a>참고 항목

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set

## <a name="gx_tree_view_create"></a>gx_tree_view_create

트리 보기 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_tree_view_create(
    GX_TREE_VIEW *tree,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    ULONG style, 
    USHORT tree_view_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 지정된 대로 트리 뷰를 만들고 제공된 부모 위젯과 트리 뷰를 연결합니다. 모든 형식의 위젯을 자식 메뉴 항목으로 허용합니다. GX_MENU 형식 위젯을 자식 메뉴 항목으로 사용하는 것이 좋습니다.

GX_TREE_VIEW는 GX_WINDOW에서 파생되며 gx_window API 서비스를 모두 지원합니다.

### <a name="parameters"></a>매개 변수

- **tree**: 트리 뷰 컨트롤 블록에 대한 포인터
- **name**: 트리 뷰의 이름
- **parent**: 부모 위젯에 대한 포인터
- **style**: 위젯의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **menu_id**: 애플리케이션에서 정의된 트리 뷰 ID
- **size**: 트리 뷰의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 트리 뷰를 만들었습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**: (0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**: (0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
status = gx_tree_view_create(&my_tree_view,
    “my_tree_view”, parent,
    GX_STYLE_ENABLED, MY_TREE_VIEW_ID,
    &size);

/* If status is GX_SUCCESS the tree view was successfully created. */
```

### <a name="see-also"></a>참고 항목

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_draw"></a>gx_tree_view_draw

트리 뷰 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_tree_view_draw(GX_TREE_VIEW *tree);
```

### <a name="description"></a>Description

이 서비스는 지정된 트리 뷰를 그립니다. 일반적으로 GUIX 캔버스 새로 고침 메커니즘을 통해 내부적으로 호출되지만 사용자 지정 트리 뷰 위젯용 사용자 지정 그리기 함수를 구현하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **tree** 트리 뷰 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom tree view draw function. */
UINT my_tree_view_draw(GX_TREE_VIEW *tree_view)
{
    /* Perform default drawing */
    gx_tree_view_draw(tree_view);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>참고 항목

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_event_process"></a>gx_tree_view_event_process

트리 뷰 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_tree_view_event_process(
    GX_TREE_VIEW *tree, 
    GX_EVENT event_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 트리 뷰에 대한 이벤트를 처리합니다. 사용자 지정 트리 뷰 이벤트 처리 함수에서 기본 이벤트 처리기로 호출되어야 합니다.

### <a name="parameters"></a>매개 변수

- **tree**: 트리 뷰 컨트롤 블록에 대한 포인터
- **event_ptr**: 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 트리 뷰 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic tree view event processing as part of custom event
    processing function. */

UINT custom_tree_view_event_process(GX_TREE_VIEW *tree_view,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default tree view
                event processing */
            status = gx_tree_view_event_process(tree_view, event);
            break;
    }
}
return status;
```

### <a name="see-also"></a>참고 항목

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_indentation_set"></a>gx_tree_view_indentation_set

트리 뷰 들여쓰기 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_tree_view_indentation_set(
    GX_TREE_VIEW *tree,
    GX_VALUE indentation);
```

### <a name="description"></a>Description

이 서비스는 트리 뷰의 들여쓰기를 설정합니다.

### <a name="parameters"></a>매개 변수

- **tree**: 트리 뷰 컨트롤 블록에 대한 포인터
- **indentation**: 설정할 들여쓰기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 트리 뷰 들여쓰기를 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set tree view “my_tree” indentation to 10. */
status = gx_tree_view_indentation_set(&my_tree, 10);

/* If status is GX_SUCCESS the indentation of tree view “my_tree”
has been set to 10. */
```

### <a name="see-also"></a>참고 항목

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixemlap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_position"></a>gx_tree_view_position

트리 뷰 항목 배치

### <a name="prototype"></a>프로토타입

```C
UINT gx_tree_view_position(GX_TREE_VIEW *tree);
```

### <a name="description"></a>Description

이 서비스는 트리 뷰 항목을 배치합니다.

### <a name="parameters"></a>매개 변수

- **tree**: 트리 뷰 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 트리 뷰 항목을 배치했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Position tree view “my_tree” items. */
status = gx_tree_view_position(&my_tree);

/* If status is GX_SUCCESS the items of tree view “my_tree” has
been positioned. */
```

### <a name="see-also"></a>참고 항목

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_root_line_color_set"></a>gx_tree_view_root_line_color_set

트리 뷰 루트 선 색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_tree_view_root_line_color_set(
    GX_TREE_VIEW *tree,
    GX_RESOURCE_ID color_id);
```

### <a name="description"></a>Description

이 서비스는 트리 뷰의 루트 선 색을 할당합니다.

### <a name="parameters"></a>매개 변수

- **tree**: 트리 뷰 컨트롤 블록에 대한 포인터
- **color_id**: 루트 선 색의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 루트 선 색을 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set root line color for tree view “my_tree”. */

status = gx_tree_view_root_line_color_set(&my_tree,
    MY_ROOT LINE_COLOR_ID);

/* If status is GX_SUCCESS the root line color of the tree view
“my_tree” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_root_pixelmap_set"></a>gx_tree_view_root_pixelmap_set

트리 뷰 루트 pixelmap 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_tree_view_root_pixelmap_set(
    GX_TREE_VIEW *tree,
    GX_RESOURCE_ID expand_map_id,
    GX_RESOURCE_ID collapse_map_id);
```

### <a name="description"></a>Description

이 서비스는 트리 뷰의 확장 및 축소 pixelmap을 할당합니다.

### <a name="parameters"></a>매개 변수

- **tree**: 트리 뷰 컨트롤 블록에 대한 포인터
- **expand_map_id**: 확장 pixelmap의 리소스 ID
- **collapse_map_id**: 축소 pixelmap의 리소스 ID

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 루트 pixelmap을 설정했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set root pixelmaps for tree view “my_tree”. */

status = gx_tree_view_root_pixelmap_set(&my_tree,
    MY_EXPAND_MAP_ID,
    MY_COLLAPSE_MAP_ID);

/* If status is GX_SUCCESS the root pixelmaps of tree view
“my_tree” has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_selected_get"></a>gx_tree_view_selected_get

선택된 항목 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_tree_view_selected_get(
    GX_TREE_VIEW *tree,
    GX_WIDGET **selected);
```

### <a name="description"></a>Description

이 서비스는 트리 뷰에서 현재 선택된 항목을 검색합니다.

### <a name="parameters"></a>매개 변수

- **tree**: 트리 뷰 컨트롤 블록에 대한 포인터
- **selected**: 선택된 위젯 포인터에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 선택된 항목을 검색했습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Retrieve selected item of tree view “my_tree”. */

GX_WIDGET *selected;

status = gx_tree_view_selected_get(&my_tree, &selected);

/* If status is GX_SUCCESS the selected item of tree view “my_tree”
has been retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_set

## <a name="gx_tree_view_selected_set"></a>gx_tree_view_selected_set

선택된 항목 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_tree_view_selected_set(
    GX_TREE_VIEW *tree,
    GX_WIDGET *selected);
```

### <a name="description"></a>Description

이 서비스는 트리 뷰의 선택된 항목을 설정합니다.

### <a name="parameters"></a>매개 변수

- **tree**: 트리 뷰 컨트롤 블록에 대한 포인터
- **selected**: 선택된 새 항목에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 메뉴를 그렸습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**: (0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set selected item of tree view “my_tree” to “tree_view_item’. */
status = gx_tree_view_selected_set(&my_tree, &tree_view_item);

/* If status is GX_SUCCESS selected item of tree view “my_menu” has
been set to “tree_view_item”. */
```

### <a name="see-also"></a>참고 항목

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get

## <a name="gx_utility_canvas_to_bmp"></a>gx_utility_canvas_to_bmp

캔버스 메모리를 비트맵으로 변환

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_canvas_to_bmp(
    GX_CANVAS *canvas, 
    GX_RECTANGLE *rect,
    UINT (*write_data)(GX_UBYTE *byte_data, UINT data_count));
```

### <a name="description"></a>Description

이 서비스는 캔버스 메모리를 비트맵 파일로 변환합니다.

### <a name="parameters"></a>매개 변수

- **canvas**: 캔버스 제어 블록 포인터
- **rect**: 변환할 사각형
- **write_data**: 데이터를 쓸 콜백 함수 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 정수 값을 문자열로 변환했습니다.
- **GX_PTR_ERROR**: (0x07) 반환 버퍼 포인터가 잘못되었습니다.
- **GX_INVALID_SIZE**: (0x19) 반환 버퍼 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
FILE *fp = GX_NULL;

/* define call back function of how to write the data read from
canvas memory. */

UINT write_data_callback(GX_UBYTE *byte_data, UINT data_count)
{
    if (fp)
    {
        fwrite(byte_data, 1, data_count, fp);
    }
    return GX_SUCCESS;
}

VOID scroll_wheel_screen_draw(GX_WINDOW *window)
{
    UINT status;

    GX_RECTANGLE size = {31,31,610,450};
    gx_window_draw(window);
    if (screenshot)
    {
        fp = fopen("../screenshot.bmp", "wb");
        /* Convert canvas memory to bitmap format.
           Status GX_SUCCESS means operation succeed. */
        status = gx_utility_canvas_to_bmp(root->gx_window_root_canvas,
            &size, write_data_callback);

        fclose(fp);
    }
}
```

### <a name="see-also"></a>참고 항목

- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_circle_point_get"></a>gx_utility_circle_point_get

원의 점 계산

### <a name="prototype"></a>프로토타입

```C
INT gx_utility_circle_point_get(
    INT xCenter, 
    INT yCenter,
    UINT radius, 
    INT angle, 
    GX_POINT *point);
```

### <a name="description"></a>Description

이 서비스는 원 중심, 반지름, 각도가 제공된 경우 원의 점을 계산합니다.

### <a name="parameters"></a>매개 변수

- **xcenter**: 원 중심의 x 좌표
- **ycenter**: 원 중심의 y 좌표
- **radius**: 원 반지름
- **angle**: 원 경계 점을 계산할 각도(도)
- **point**: 계산된 x,y 좌표를 저장할 GX_POINT 변수의 주소
- **end_alpha**: 끝 알파 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 그라데이션을 만들었습니다.
- **GX_PTR_ERROR**: (0x07) 반환 점 주소가 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) radius 매개 변수가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_POINT point;
    UINT status;

        status = gx_utility_circle_point_get(100, 100,
20, 45,
&point);

/* If status is GX_SUCCESS the value of point is the x,y coordinate of a point on the circle perimeter at an angle of 45 degrees, where the circle is centered at (100, 100), has a radius of 20 pixels */

```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_gradient_create"></a>gx_utility_gradient_create

그라데이션 pixelmap 만들기

### <a name="prototype"></a>프로토타입

```C
INT gx_utility_gradient_create(
    GX_GRADIENT *gradient,
    GX_VALUE width, 
    GX_VALUE height,
    UCHAR type, 
    GX_UBYTE start_alpha, 
    GX_UBYTE end_alpha);
```

### <a name="description"></a>Description

이 서비스는 런타임에 그라데이션 pixelmap을 만듭니다. 그라데이션 이미지는 페이드 효과 및 기타 흥미로운 시각적 변경을 수행하는 데 사용할 수 있습니다.

요청된 그라데이션의 너비와 높이는 2x2 픽셀 이상이어야 합니다.

생성된 그라데이션 목록은 GUIX에서 내부적으로 유지 관리되며, 이 함수는 새 pixelmap을 만들기 전에 먼저 그라데이션 목록을 검색하여 일치하는 그라데이션 pixelmap을 찾습니다. 즉, 동일한 그라데이션 pixelmap이 여러 번 필요하고 하나의 pixelmap만 실제로 생성되며, 이 pixelmap이 필요한 각 그라데이션은 생성된 pixelmap을 공유합니다.

이 API에서 런타임 메모리 할당을 허용하려면 gx_system_memory_allocator 함수를 정의해야 합니다.

그라데이션 형식 플래그로는 GX_GRADIENT_TYPE_ALPHA 및 GX_GRADIENT_TYPE_MIRROR가 있습니다. 현재 GX_GRADIENT_TYPE_ALPHA 형식 그라데이션만 지원됩니다. 즉, 이 형식의 플래그를 설정해야 합니다. GX_GRADIENT_TYPE_MORROR 플래그는 선택 사항이며, 설정된 경우 start_alpha에서 end_alpha로 변경되었다가 다시 start_alpha로 변경되는 그라데이션을 만들도록 그라데이션 생성 논리에 지시합니다. 설정하지 않으면 선형 그라데이션이 생성됩니다.

### <a name="parameters"></a>매개 변수

- **gradient**: 그라데이션 제어 블록 구조체에 대한 포인터
- **width**: 요청된 pixelmap 너비
- **height**: 요청된 pixelmap 높이
- **type**: 요청된 그라데이션 형식
- **start_alpha**: 시작 알파 값
- **end_alpha**: 끝 알파 값

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 그라데이션을 만들었습니다.
- **GX_INVALID_SIZE**: (0x19) 그라데이션이 2x2 픽셀 이상이 아닙니다.
- **GX_NOT_SUPPORTED**: (0x28) 그라데이션이 GX_GRADIENT_TYPE_ALPHA 형식이 아닙니다.
- **GX_FAILURE**: (0x10) 메모리 할당자가 정의되지 않았거나 메모리를 할당하지 못했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 그라데이션 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) 너비 및 높이 값이 잘못되었습니다.
- **GX_INVALID_TYPE**: (0x1B) 그라데이션 형식이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_GRADIENT gradient;

UINT status;

status = gx_utiity_gradient_create(&gradient, 3, 40,
    GX_GRADIENT_TYPE_ALPHA, 240, 0);

/* If status == GX_SUCCESS the gradient pixelmap has been created */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_gradient_delete"></a>gx_utility_gradient_delete

이전에 만든 그라데이션 삭제

### <a name="prototype"></a>프로토타입

```C
INT gx_utility_gradient_delete(GX_GRADIENT *gradient);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 그라데이션을 삭제합니다. 이 그라데이션과 연결된 pixelmap을 다른 그라데이션에서 사용하고 있지 않으면 pixelmap 데이터도 삭제됩니다.

### <a name="parameters"></a>매개 변수

- **gradient**: 그라데이션 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 그라데이션을 삭제했습니다.
- **GX_CALLER_ERROR**: (0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**: (0x07) 그라데이션 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_GRADIENT gradient;

UINT status;

/* Delete previously created gradient. */
status = gx_utility_gradient_delete(&gradient);

/* If status == GX_SUCCESS, the gradient has been deleted. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_ltoa"></a>gx_utility_ltoa

정수(Long)를 ASCII로 변환

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_itoa(
    LONG value, 
    GX_CHAR *return_buffer,
    UINT seturn_buffer_size);
```

### <a name="description"></a>Description

이 서비스는 정수(Long) 값을 ASCII 문자열로 변환합니다.

### <a name="parameters"></a>매개 변수

- **value**: 변환할 정수(Long) 값
- **return_buffer**: ASCII 문자열의 대상 버퍼
- **return_buffer_size**: 대상 버퍼의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 정수 값을 문자열로 변환했습니다.
- **GX_PTR_ERROR**: (0x07) 반환 버퍼 포인터가 잘못되었습니다.
- **GX_INVALID_SIZE**: (0x19) 반환 버퍼 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
INT my_value = 200;

GX_CHAR string_buffer[10];

UINT status;

/* Convert “my_value” into an ASCII string. */
status = gx_utility_ltoa(my_value, string_buffer, 10);

/* If status is GX_SUCCESS, “string_buffer” contains the ASCII
representation of “my_value”. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_acos"></a>gx_utility_math_acos

아크코사인 컴퓨팅

### <a name="prototype"></a>프로토타입

```C
INT gx_utility_math_acos(GX_FIXED_VAL x);
```

### <a name="description"></a>Description

이 서비스는 아크코사인 x의 각도 값을 컴퓨팅합니다.

입력 값은 고정 소수점 데이터 형식이며, GX_FIXED_VAL_MAKE를 호출하여 INT에서 GX_FIXED_VAL 형식으로 변환합니다. 예를 들어 0.5의 아크코사인을 계산하려면 GX_FIXED_VAL_MAKE(1) / 2로 입력합니다.

5.4.0 또는 이전 버전의 GUIX에서 이 함수의 입력 값 형식은 INT이며 값이 [-256, 256] 범위로 제한됩니다. 애플리케이션에서 이 서비스를 호출하기 전에 값을 [-1, 1] 범위에서 [-256, 256] 범위로 스케일링해야 합니다. GUIX 버전이 5.4.0 또는 이전 버전인 프로젝트에 이 API에 대한 참조가 있고 최신 GUIX 라이브러리로 프로젝트를 업그레이드하려고 합니다. 다음과 같은 두 가지 옵션이 있습니다.

1. GX_FIXED_VAL 데이터 형식 값을 사용하도록 이 API 호출의 입력 값을 수정합니다.
1. GUIX_5_4_0_COMPATIBILITY를 정의합니다.

### <a name="parameters"></a>매개 변수

- **x**: 아크코사인이 컴퓨팅된 값

### <a name="return-values"></a>반환 값

- **angle**: 아크코사인 x의 각도 값

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
/* Compute the angle value of arc cosine of “0.5”. */

#if defined(GUIX_5_4_0_COMPATIBILITY)
    x = 256 / 2;
#else
    x = GX_FIXED_VAL_MAKE(1) / 2;
#endif

angle = gx_utility_math_acos(x);

/* “angle” contains the angle value of arc cosine “x”. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_asin"></a>gx_utility_math_asin

아크사인 컴퓨팅

### <a name="prototype"></a>프로토타입

```C
INT gx_utility_math_asin(GX_FIXED_VAL x);
```

### <a name="description"></a>Description

이 서비스는 아크사인 x의 각도 값을 컴퓨팅합니다.

입력 값은 고정 소수점 데이터 형식이며, GX_FIXED_VAL_MAKE를 호출하여 INT에서 GX_FIXED_VAL 형식으로 변환합니다. 예를 들어 0.5의 아크사인을 계산하려면 GX_FIXED_VAL_MAKE(1) / 2로 입력합니다.

5.4.0 또는 이전 버전의 GUIX에서 이 함수의 입력 값 형식은 INT이며 값이 [-256, 256] 범위로 제한됩니다. 애플리케이션에서 이 서비스를 호출하기 전에 값을 [-1, 1] 범위에서 [-256, 256] 범위로 스케일링해야 합니다. GUIX 버전이 5.4.0 또는 이전 버전인 프로젝트가 있고 최신 GUIX 라이브러리로 프로젝트를 업그레이드하려고 합니다. 다음과 같은 두 가지 옵션이 있습니다.

1. GX_FIXED_VAL 데이터 형식 값을 사용하도록 이 API 호출의 입력 값을 수정합니다.
1. GUIX_5_4_0_COMPATIBILITY를 정의합니다.

### <a name="parameters"></a>매개 변수

- **x**: 아크사인이 컴퓨팅된 값

### <a name="return-values"></a>반환 값

- **angle**: 아크사인 x의 각도 값

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
/* Compute the angle value of arc sine of “x”. */

#if defined GUIX_5_4_0_COMPATIBILITY
    x = 256 / 2;
#else
    X = GX_FIXED_VAL_MAKE(1) / 2;
#endif

angle = gx_utility_math_asin(x);

/* “angle” contains the angle value of arc sine “x”. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_cos"></a>gx_utility_math_cos

코사인 컴퓨팅

### <a name="prototype"></a>프로토타입

```C
GX_FIXED_VAL gx_utility_math_cos(GX_FIXED_VAL angle);
```

### <a name="description"></a>Description

이 서비스는 제공된 각도의 코사인을 컴퓨팅합니다.

입력 값은 고정 소수점 데이터 형식이며, GX_FIXED_VAL_MAKE를 호출하여 INT에서 GX_FIXED_VAL로 변환합니다. 예를 들어 90도의 코사인을 계산하려면 GX_FIXED_VAL_MAKE(90)로 입력합니다.

반환 값은 고정 소수점 데이터 형식이며, GX_FIXED_VAL_TO_INT를 호출하여 GX_FIXED_VAL에서 INT로 변환합니다.

5.4.0 또는 이전 버전의 GUIX에서 이 서비스의 입력 값 및 반환 값 형식은 INT이며 입력 값과 반환 값이 256만큼 확대됩니다. 따라서 애플리케이션에서 서비스를 호출하기 전에 각도 값을 256만큼 스케일링해야 합니다. GUIX 버전이 5.4.0 또는 이전 버전인 프로젝트가 있고 최신 GUIX 라이브러리로 프로젝트를 업그레이드하려는 경우 다음 두 가지 옵션이 있습니다.

1. GX_FIXED_VAL 데이터 형식 값을 사용하도록 이 API 호출의 반환 값 처리와 입력 값을 수정합니다.
1. GUIX_5_4_0_COMPATIBILITY를 정의합니다.

### <a name="parameters"></a>매개 변수

- **angle**: 코사인을 컴퓨팅할 각도

### <a name="return-values"></a>반환 값

- **cosine**: 제공된 각도의 코사인

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
/* Compute cosine of 90 degree. */

INT angle = 90;

#if defined (GUIX_5_4_0_COMPATIBILITY)
    INT scaled_angle = angle << 8;
#else
    GX_FIXED_VAL scaled_angle = GX_FIXED_VAL_MAKE(angle);
#endif

my_angle_cosine = gx_utility_math_cos(scaled_angle);

/* “my_angle_cosine” contains the cosine of “my_angle”. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_math_asin
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_sin"></a>gx_utility_math_sin

사인 컴퓨팅

### <a name="prototype"></a>프로토타입

```C
GX_FIXED_VAL gx_utility_math_sin(GX_FIXED_VAL angle);
```

### <a name="description"></a>Description

이 서비스는 제공된 각도의 사인을 컴퓨팅합니다.

입력 값은 고정 소수점 데이터 형식이며, GX_FIXED_VAL_MAKE를 호출하여 INT에서 GX_FIXED_VAL로 변환합니다. 예를 들어 90도의 사인을 계산하려면 GX_FIXED_VAL_MAKE(90)로 입력합니다. 

반환 값은 고정 소수점 데이터 형식이며, GX_FIXED_VAL_TO_INT를 호출하여 GX_FIXED_VAL에서 INT로 변환합니다.

5.4.0 또는 이전 버전의 GUIX에서 입력 값 및 반환 값 형식은 INT이며 입력 값과 반환 값이 256만큼 확대됩니다. 따라서 애플리케이션에서 서비스를 호출하기 전에 각도 값을 256만큼 스케일링해야 합니다. GUIX 버전이 5.4.0 또는 이전 버전인 프로젝트가 있고 최신 GUIX 라이브러리로 프로젝트를 업그레이드하려는 경우 다음 두 가지 옵션이 있습니다.

1. GX_FIXED_VAL 데이터 형식 값을 사용하도록 이 API 호출의 반환 값 처리와 입력 값을 수정합니다.
1. GUIX_5_4_0_COMPATIBILITY를 정의합니다.

### <a name="parameters"></a>매개 변수

- **angle**: 사인을 컴퓨팅할 각도

### <a name="return-values"></a>반환 값

- **sine**: 제공된 각도의 사인

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
INT my_angle = 80;

/* Compute sine of “my_angle”. */

#if defined(GUIX_5_4_0_COMPATIBILITY)
    INT scaled_angle = my_angle << 8;
#else
    GX_FIXED_VAL = GX_FIXED_VAL_MAKE(my_angle);
#endif

my_angle_sine = gx_utility_math_sin(scaled_angle);

/* “my_angle_sine” contains the sine of “my_angle”. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_asin
- gx_utility_math_cos
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_sqrt"></a>gx_utility_math_sqrt

제곱근 컴퓨팅

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_math_sqrt(UINT value);
```

### <a name="description"></a>Description

이 서비스는 제공된 값의 제곱근을 컴퓨팅합니다.

### <a name="parameters"></a>매개 변수

- **value**: 제곱근을 컴퓨팅할 값

### <a name="return-values"></a>반환 값

- **square root**: 제공된 값의 제곱근

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
/* Compute square root of “my_value”. */
my_square_root = gx_utility_math_sqrt(my_value);

/* “my_square_root” contains the square root of “my_value”. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_bidi_paragraph_reorder"></a>gx_utility_bidi_paragraph_reorder

양방향 텍스트를 표시 순서로 다시 정렬

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_bidi_paragraph_reorder(GX_BIDI_TEXT_INFO *input_info, 
                                       GX_BIDI_RESOLVED_TEXT_INFO **resolved_info_head)
```

### <a name="description"></a>Description

이 서비스는 양방향 텍스트를 표시 순서로 다시 정렬합니다. 텍스트 그리기 글꼴과 표시 너비가 제공된 경우 줄 바꿈이 먼저 적용되고 각 줄을 기준으로 다시 정렬 프로세스가 적용됩니다. 제공된 텍스트에 둘 이상의 단락이 포함된 경우 서비스는 텍스트를 단락으로 분할하고 각 단락의 줄 바꿈 및 다시 정렬 결과가 목록으로 연결됩니다.

### <a name="parameters"></a>매개 변수

- **input_info**: 줄 바꿈 및 텍스트 다시 정렬 정보에 대한 포인터
- **resolved_info_head**: 제공된 텍스트의 각 단락에 대한 줄 바꿈 및 다시 정렬 결과를 포함하는 연결된 목록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 양방향 텍스트를 다시 정렬했습니다.
- **GX_PTR_ERROR**: (0x07) 입력 포인터가 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) 메모리 할당자가 정의되지 않았거나 메모리를 할당하지 못했습니다.

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제
#### <a name="draw-single-line-bidi-text-to-canvas"></a>캔버스에 한 줄 양방향 텍스트 그리기
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Single Line String";
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = GX_NULL;
    input_info.gx_bidi_text_info_display_width = -1;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        /* Draw reordered bidi text to canvas. */
        gx_canvas_text_draw_ext(widget->gx_widget_size.gx_rectangle_left,
                                widget->gx_widget_size.gx_rectangle_top,
                                resolved_info.gx_bidi_resolved_text_info_text);

        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```
#### <a name="draw-multi-line-bidi-text-to-canvas"></a>캔버스에 여러 줄 양방향 텍스트 그리기
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Multi Line BiDi Text Display Example";
    GX_FONT *font;
    GX_RECTANGLE client;
    GX_VALUE display_width;
    INT index;
    GX_VALUE xpos;
    GX_VALUE ypos;
    
    /* Pickup the font. */
    gx_context_font_get(font_id, &font);
    gx_widget_client_get(widget, 2, &client);
    
    display_width = (GX_VALUE)(client.gx_rectangle_right - client.gx_rectangle_left + 1);
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = font;
    input_info.gx_bidi_text_info_display_width = display_width;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        xpos = client.gx_rectangle_left;
        ypos = client.gx_rectangle_top;
        
        /* Draw reordered bidi text to canvas. */
        for(index = 0; index < resolved_info.gx_bidi_resolved_text_info_total_lines; index++)
        {
            gx_canvas_text_draw_ext(xpos, ypos, &resolved_info.gx_bidi_resolved_text_info_text[index]);
        
            ypos += font->gx_font_line_height;
        }
        
        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

#### <a name="draw-multi-paragraph-bidi-text-to-canvas"></a>캔버스에 여러 단락 양방향 텍스트 그리기
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_BIDI_RESOLVED_TEXT_INFO *next;
    GX_CHAR bidi_text[] = "Multi Paragraph\r BiDi Text Display Example";
    GX_FONT *font;
    GX_RECTANGLE client;
    GX_VALUE display_width;
    INT index;
    GX_VALUE xpos;
    GX_VALUE ypos;
    
    /* Pickup the font. */
    gx_context_font_get(font_id, &font);
    gx_widget_client_get(widget, 2, &client);
    
    display_width = (GX_VALUE)(client.gx_rectangle_right - client.gx_rectangle_left + 1);
    
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = font;
    input_info.gx_bidi_text_info_display_width = display_width;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        xpos = client.gx_rectangle_left;
        ypos = client.gx_rectangle_top;
        
        next = resolved_info;
        
        /* Draw reordered bidi text to canvas. */
        while(next)
        {
            for(index = 0; index < next.gx_bidi_resolved_text_info_total_lines; index++)
            {
                gx_canvas_text_draw_ext(xpos, ypos, &next.gx_bidi_resolved_text_info_text[index]);
            
                ypos += font->gx_font_line_height;
            }
            
            next = next->gx_bidi_resolved_text_info_next;
        }
        
        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

### <a name="see-also"></a>참고 항목

- gx_utility_bidi_resolved_text_info_delete

## <a name="gx_utility_bidi_resolved_text_info_delete"></a>gx_utility_bidi_resolved_text_info_delete

확인된 양방향 텍스트 정보 목록 삭제

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_bidi_resolved_text_info_delete(GX_BIDI_RESOLVED_TEXT_INFO **resolved_info_head)
```

### <a name="description"></a>Description

이 서비스는 gx_utility_bidi_paragraph_reorder에서 반환된 확인된 정보 목록을 삭제합니다.

### <a name="parameters"></a>매개 변수

- **resolved_info_head**: 확인된 양방향 텍스트 정보 목록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 확인된 텍스트를 삭제했습니다.
- **GX_PTR_ERROR**: (0x07) 입력 포인터가 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) 메모리 할당자가 정의되지 않았거나 메모리를 할당하지 못했습니다.

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Single Line String";
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = GX_NULL;
    input_info.gx_bidi_text_info_display_width = -1;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        /* Draw reordered bidi text to canvas. */
        gx_canvas_text_draw_ext(widget->gx_widget_size.gx_rectangle_left,
                                widget->gx_widget_size.gx_rectangle_top,
                                resolved_info.gx_bidi_resolved_text_info_text);

        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

### <a name="see-also"></a>참고 항목

- gx_utility_bidi_paragraph_reorder

## <a name="gx_utility_pixelmap_resize"></a>gx_utility_pixelmap_resize

pixelmap 크기 조정

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_pixelmap_resize(
    GX_PIXELMAP *src,
    GX_PIXELMAP *destination, 
    INT width, 
    INT height);
```

### <a name="description"></a>Description

이 서비스는 pixelmap의 크기를 조정하고 pixelmap 크기 조정 결과인 새 pixelmap에 대한 포인터를 반환합니다.

서비스에서 크기 조정된 pixelmap 데이터를 저장할 메모리 할당을 허용하려면 먼저 gx_system_memory_allocator_set을 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **src**: 크기를 조정할 pixelmap에 대한 포인터
- **destination**: 결과 pixelmap의 대상 버퍼
- **width**: 결과 pixelmap의 너비(픽셀)
- **height**: 결과 pixelmap의 높이(픽셀)

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) pixelmap 크기를 조정했습니다.
- **GX_PTR_ERROR**: (0x07) 원본 또는 대상 pixelmap 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) 너비 또는 높이 값이 잘못되었습니다.
- **GX_NOT_SUPPORTED**: (0x28) 원본 pixelmap이 압축 형식입니다.
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) 메모리 할당자가 정의되지 않았거나 메모리를 할당하지 못했습니다.

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
GX_PIXLEMAP *des_pixelmap;

/* Resize “src_pixelmap” with specifiy width and height. */
status = gx_utility_pixelmap_resize(src_pixelmap,
    &des_pixelmap, 100, 200);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of resize. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift
- gx_canvas_pixelmap_rotate

## <a name="gx_utility_pixelmap_rotate"></a>gx_utility_pixelmap_rotate

pixelmap 회전

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_pixelmap_rotate(
    GX_PIXELMAP *src, INT angle,
    GX_PIXELMAP *destination,
    UINT *rot_cx, 
    UINT *rot_cy);
```

### <a name="description"></a>Description

이 서비스는 pixelmap을 회전하고 pixelmap 회전 결과인 새 pixelmap에 대한 포인터를 반환합니다. pixelmap을 캔버스로 직접 회전하려면 gx_canvas_pixelmap_rotate()를 사용합니다.

서비스에서 회전된 pixelmap 데이터를 저장할 메모리 할당을 허용하려면 먼저 gx_system_memory_allocator_set을 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **src**: 회전할 pixelmap
- **angle**: 회전 각도(도)
- **destination**: 결과 pixelmap의 대상 버퍼
- **rot_cx**: 대상 pixelmap을 기준으로 검색된 회전 중심의 x 좌표. 원본 pixelmap을 기준으로 회전 중심의 x 좌표를 사용하여 시작해야 합니다. rot_cx가 GX_NULL이면 값이 검색되지 않습니다.
- **rot_cy**: 대상 pixelmap을 기준으로 검색된 회전 중심의 y 좌표. 원본 pixelmap을 기준으로 회전 중심의 y 좌표를 사용하여 시작해야 합니다. rot_cy가 GX_NULL이면 값이 검색되지 않습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) pixelmap을 회전했습니다.
- **GX_PTR_ERROR**: (0x07) 원본 또는 대상 pixelmap 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) 각도 값이 0입니다.
- **GX_INVALID_FORMAT**: (0x28) 원본 pixelmap이 지원되지 않는 압축 형식입니다.
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) 메모리 할당자가 정의되지 않았거나 메모리를 할당하지 못했습니다.

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
rot_cx = source_rotate_center_x;
rot_cy = source_rotate_center_y;

/* rotate “src_pixelmap” by 30 degree in clockwise direction. */
status = gx_utility_pixelmap_rotate(src_pixelmap, 30,
    &des_pixelmap, &rot_cx, &rot_cy);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of rotation. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift
- gx_canvas_pixelmap_rotate

## <a name="gx_utility_pixelmap_simple_rotate"></a>gx_utility_pixelmap_simple_rotate

pixelmap 회전

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_pixelmap_simple_rotate(
    GX_PIXELMAP *src,
    INT angle,
    GX_PIXELMAP *destination,
    UINT *rot_cx,
    UINT *rot_cy);
```

### <a name="description"></a>Description

이 서비스는 pixelmap을 90, 180 또는 270도 회전합니다.

### <a name="parameters"></a>매개 변수

- **src**: 회전할 pixelmap
- **angle**: 회전 각도(도)
- **destination**: 결과 pixelmap의 대상 버퍼
- **rot_cx**: 대상 pixelmap을 기준으로 검색된 회전 중심의 x 좌표. 원본 pixelmap을 기준으로 회전 중심의 x 좌표를 사용하여 시작해야 합니다. rot_cx가 GX_NULL이면 값이 검색되지 않습니다.
**rot_cy**: 대상 pixelmap을 기준으로 검색된 회전 중심의 y 좌표. 원본 pixelmap을 기준으로 회전 중심의 y 좌표를 사용하여 시작해야 합니다. rot_cy가 GX_NULL이면 값이 검색되지 않습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) pixelmap을 회전했습니다.
- **GX_PTR_ERROR**: (0x07) 원본 또는 대상 pixelmap 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**: (0x22) 각도 값이 0이거나 90, 180, 270과 같은 단순 각도가 아닙니다.
- **GX_INVALID_FORMAT**: (0x28) 원본 pixelmap이 지원되지 않는 압축 형식입니다.
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) 메모리 할당자가 정의되지 않았거나 메모리를 할당하지 못했습니다.

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
rot_cx = source_rotate_center_x;
rot_cy = source_rotate_center_y;

/* rotate “src_pixelmap” by 90 degree in clockwise direction. */
status = gx_utility_pixelmap_simple_rotate(src_pixelmap, 90,
    &des_pixelmap,
    &rot_cx, &rot_cy);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of rotation. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_center"></a>gx_utility_rectangle_center

다른 사각형 가운데에 사각형 맞춤

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_rectangle_center(
    GX_RECTANGLE *rectangle,
    GX_RECTANGLE *within_rectangle);
```

### <a name="description"></a>Description

이 서비스는 다른 사각형 가운데에 사각형을 맞춥니다.

### <a name="parameters"></a>매개 변수

- **rectangle**: 가운데에 맞출 사각형
- **within_rectangle**: 가운데 맞춤의 바깥쪽 사각형

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 사각형을 가운데에 맞췄습니다.
- **GX_PTR_ERROR**: (0x07) 입력 사각형 포인터가 잘못되었습니다.
- **GX_INVALID_SIZE**: (0x19) 사각형 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
UINT status;

/* Center “my_inner_rectangle” inside of “my_outer_rectangle”.*/
status = gx_utility_rectangle_center(&my_inner_rectangle,
    &my_outer_rectangle);

/* Is status is GX_SUCCESS, “my_inner_rectangle” is centered
within “my_other_rectangle”. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_center_find"></a>gx_utility_rectangle_center_find

사각형 가운데 찾기

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_rectangle_center_find(
    GX_RECTANGLE *rectangle,
    GX_POINT *return_center);
```

### <a name="description"></a>Description

이 서비스는 사각형의 중심을 찾습니다.

### <a name="parameters"></a>매개 변수

- **rectangle**: 사각형
- **return_center**: 중심점에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 사각형의 중심을 찾았습니다.
- **GX_PTR_ERROR**: (0x07) 입력 포인터가 잘못되었습니다.
- **GX_INVALID_SIZE**: (0x19) 사각형 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
UINT status;

GX_RECTANGLE my_rectangle;

GX_POINT my_center_point;

gx_utility_define(&my_rectangle, 0, 0, 100, 100);

/* Find center of “my_rectangle””. */

status = gx_utility_rectangle_center_find(&my_rectangle,
    &my_center_point);

/* If status is GX_SUCCESS, “my_center_point” is the center point
of “my_rectangle” (50, 50). */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_combine"></a>gx_utility_rectangle_combine

두 사각형을 첫 번째 사각형으로 결합

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_rectangle_combine(
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle);
```

### <a name="description"></a>Description

이 서비스는 첫 번째 사각형과 두 번째 사각형을 첫 번째 사각형에 결합합니다. 첫 번째 사각형이 두 번째 사각형을 포함하도록 확장됩니다.

### <a name="parameters"></a>매개 변수

- **first_rectangle**: 첫 번째 사각형 및 결합된 사각형
- **second_rectangle**: 두 번째 사각형

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 두 개의 사각형을 결합했습니다.
- **GX_PTR_ERROR**: (0x07) 입력 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
UINT status;

GX_RECTANGLE rect_a;

GX_RECTANGLE rect_b;

gx_utility_rectangle_define(&rect_a, 0, 0, 100, 100);
gx_utility_rectangle_define(&rect_b, 50, 50, 200, 200);

/* Combine “my_rectangle_a” to “my_rectangle_b”. */
status = gx_utility_rectangle_combine(&rect_a, &rect_b);

/* If status is GX_SUCCESS, “rect_a” is (0, 0, 200, 200) the merger
of the original “rect_a” and “rect_b”. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_compare"></a>gx_utility_rectangle_compare

두 사각형 비교

### <a name="prototype"></a>프로토타입

```C
GX_BOOL gx_utility_rectangle_compare( 
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle);
```

### <a name="description"></a>Description

이 서비스는 첫 번째 사각형과 두 번째 사각형을 비교합니다. 두 사각형이 같으면 GX_TRUE 값이 반환됩니다.

### <a name="parameters"></a>매개 변수

- **first_rectangle**: 첫 번째 사각형
- **second_rectangle**: 두 번째 사각형

### <a name="return-values"></a>반환 값

- **result**: 두 사각형이 같으면 GX_TRUE, 같지 않으면 GX_FALSE가 반환됩니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Compare “my_rectangle_a” to “my_rectangle_b”. */
result = gx_utility_rectangle_compare(&my_rectangle_a,
    &my_rectangle_b);

/* If result is GX_TRUE, the two rectangles are equal. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_define"></a>gx_utility_rectangle_define

사각형 정의

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_rectangle_define(
    GX_RECTANGLE *rectangle,
    GX_VALUE left,
    GX_VALUE top, 
    GX_VALUE right, 
    GX_VALUE bottom);
```

### <a name="description"></a>Description

이 서비스는 지정된 사각형을 정의합니다.

### <a name="parameters"></a>매개 변수

- **rectangle**: 사각형 제어 블록
- **left**: 맨 왼쪽 좌표
- **top**: 맨 위 좌표
- **right**: 맨 오른쪽 좌표
- **bottom**: 맨 아래 좌표

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 사각형을 정의했습니다.
- **GX_PTR_ERROR**: (0x07) 사각형 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
UINT status;

GX_RECTANGLE my_rect;

/* Define “my_rect”. */

status = gx_utility_rectangle_define(&my_rect, 10, 5, 200, 100);

/* If status is GX_SUCCESS, “my_rect” is defined. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_overlap_detect"></a>gx_utility_rectangle_overlap_detect

사각형 겹침 검색

### <a name="prototype"></a>프로토타입

```C
GX_BOOL gx_utility_rectangle_overlap_detect(
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle,
    GX_RECTANGLE *return_overlap_area);
```

### <a name="description"></a>Description

이 서비스는 제공된 사각형의 겹치는 부분을 검색합니다. 겹치는 부분이 발견되면 서비스에서 GX_TRUE 및 겹치는 사각형을 반환합니다.

### <a name="parameters"></a>매개 변수

- **first_rectangle**: 첫 번째 사각형
- **second_rectangle**: 두 번째 사각형
- **return_overlap_area**: 겹치는 사각형 영역

### <a name="return-values"></a>반환 값

- **result**: 사각형이 겹치면 GX_TRUE, 겹치지 않으면 GX_FALSE입니다.

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
/* Detect overlap of “my_rectangle_a” and “my_rectangle_b”. */
result = gx_utility_rectangle_overlap_detect(&my_rectangle_a,
    &my_rectangle_b,
    &my_overlap_area);

/* If result is GX_TRUE, “my_overlap_area” specifies the area the
rectangles overlap. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_point_detect"></a>gx_utility_rectangle_point_detect

점이 사각형 안에 있는 경우 검색

### <a name="prototype"></a>프로토타입

```C
GX_BOOL gx_utility_rectangle_point_detect(
    GX_RECTANGLE *rectangle,
    GX_POINT point);
```

### <a name="description"></a>Description

이 서비스는 지정된 점이 사각형 안에 있는지 검색합니다. 점이 사각형 안에 있으면 서비스에서 GX_TRUE를 반환합니다.

### <a name="parameters"></a>매개 변수

- **rectangle**: 사각형
- **point**: 점

### <a name="return-values"></a>반환 값

- **result**: 점이 사각형 안에 있으면 GX_TRUE, 안에 있지 않으면 GX_FALSE입니다.

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```c
GX_RECTANGLE my_rectangle;

GX_POINT my_point;

gx_utility_rectangle_define(&my_rectangle, 0, 0, 100, 100);

my_point.gx_point_x = 20; my_point.gx_point_y = 20;

/* Detect if point “my_point” is within “my_rectangle””. */
result = gx_utility_rectangle_point_detect(&my_rectangle,
    &my_point);

/* If result is GX_TRUE, “my_point” resides in the rectangle. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_resize"></a>gx_utility_rectangle_resize

사각형 확대

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_rectangle_resize(
    GX_RECTANGLE *rectangle,
    GX_VALUE adjust);
```

### <a name="description"></a>Description

이 서비스는 지정된 대로 사각형 크기를 늘립니다.

### <a name="parameters"></a>매개 변수

- **rectangle**: 사각형에 대한 포인터
- **adjust**: 사각형을 조정할 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 사각형의 크기를 조정했습니다.
- **GX_PTR_ERROR**: (0x07) 입력 사각형 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
UINT status;

/* Adjust “my_rectangle” by increasing 20 pixels on four sides */
status = gx_utility_rectangle_resize(&my_rectangle, 20);

/* If status is GX_SUCCESS, “my_rectangle” is 20 pixels larger. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_shift"></a>gx_utility_rectangle_shift

사각형 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_rectangle_shift(
    GX_RECTANGLE *rectangle,
    GX_VALUE x_shift,
    GX_VALUE y_shift);
```

### <a name="description"></a>Description

이 서비스는 사각형을 지정된 값만큼 이동합니다.

### <a name="parameters"></a>매개 변수

- **rectangle**: 이동할 사각형
- **x_shif**: x축에서 이동할 픽셀 수
- **y_shift**: y축에서 이동할 픽셀 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) 사각형을 이동했습니다.
- **GX_PTR_ERROR**: (0x07) 입력 사각형 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

모두

### <a name="example"></a>예제

```C
UINT status;

/* Shift “my_rectangle”. */

status = gx_utility_rectangle_shift(&my_rectangle, 10, 20);

/* If status is GX_SUCCESS, “my_rectangle” has been shifted. */
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect

## <a name="gx_utility_string_to_alphamap"></a>gx_utility_string_to_alphamap

8bpp alphamap 형식 pixelmap에 문자열 렌더링(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_string_to_alphamap(
    const GX_CHAR *text, const
    GX_FONT *font, 
    GX_PIXELMAP *return_map);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_utility_string_to_alphamap_ext()로 대체되었습니다.

이 서비스는 알파 값만 포함하는 특별한 형식의 8bpp pixelmap인 alphamap에 텍스트 문자열을 렌더링합니다. 일반적으로 gx_utility_pixelmap_rotate 및 gx_canvas_pixelmap_draw와 함께 사용되어 캔버스에 회전된 텍스트를 그립니다.

이 서비스는 결과 alphamap에 필요한 메모리 크기를 계산하고 애플리케이션에서 정의된 gx_system_memory_allocator() 함수를 호출하여 메모리를 동적으로 할당합니다. 이 서비스를 사용하기 전에 애플리케이션에서 일반적으로 프로그램을 시작할 때 gx_system_memory_allocator_set()을 호출해야 합니다.

텍스트 문자열을 회전하고 캔버스에 한 번만 그리려는 경우 gx_canvas_rotated_text_draw() 서비스가 대안으로 제공됩니다. gx_canvas_rotated_text_draw()는 gx_utility_string_to_alphamap(), gx_utility_pixelmap_rotate(), gx_canvas_pixelmap_draw()를 호출하여 회전된 텍스트를 하나의 작업으로 렌더링합니다. 그러나 같은 텍스트를 여러 각도로 회전하여 여러 번 그리는 경우 gx_utility_string_to_alphmap API를 사용하여 alphamap을 한 번 만든 다음, 필요에 따라 결과 alphamap을 여러 번 회전하는 것이 더 효율적입니다.

### <a name="parameters"></a>매개 변수

- **text**: alphamap에 렌더링할 텍스트 문자열
- **font**: 텍스트를 렌더링하는 데 사용할 글꼴
- **return_map**: 호출자에게 반환되는 GX_PIXELMAP에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) alphamap에 텍스트 문자열을 렌더링했습니다.
- **GX_PTR_ERROR**: (0x07) 입력 포인터가 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) 메모리 할당/해제 함수가 정의되어 있지 않습니다.
- **GX_INVALID_STRING_LENGTH**: (0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_PIXELMAP alphamap;

GX_PIXELMAP rotated_text;

INT xpos;

INT ypos;

gx_widget_font_get(widget, GX_FONT_ID_SCREEN_LABEL, &font);

/* render string to alphamap once */

gx_utility_string_to_alphamap("Hello World", font, &alphamap);

/* rotate and render the alphmap at multiple angles */

gx_utility_pixelmap_rotate(&alphamap, 45, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(10, 10, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 135, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(100, 100, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 300, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(200, 200, &rotated_text);
```

### <a name="see-also"></a>참고 항목

- gx_utility_string_to_alphamap_ext

## <a name="gx_utility_string_to_alphamap_ext"></a>gx_utility_string_to_alphamap_ext

8bpp alphamap 형식 pixelmap에 문자열 렌더링

### <a name="prototype"></a>프로토타입

```C
UINT gx_utility_string_to_alphamap_ext(
    GX_CONST GX_STRING *string,
    GX_CONST GX_FONT *font, 
    GX_PIXELMAP *return_map);
```

### <a name="description"></a>Description

이 서비스는 알파 값만 포함하는 특별한 형식의 8bpp pixelmap인 alphamap에 텍스트 문자열을 렌더링합니다. 일반적으로 gx_utility_pixelmap_rotate 및 gx_canvas_pixelmap_draw와 함께 사용되어 캔버스에 회전된 텍스트를 그립니다.

이 서비스는 결과 alphamap에 필요한 메모리 크기를 계산하고 애플리케이션에서 정의된 gx_system_memory_allocator() 함수를 호출하여 메모리를 동적으로 할당합니다. 이 서비스를 사용하기 전에 애플리케이션에서 일반적으로 프로그램을 시작할 때 gx_system_memory_allocator_set()을 호출해야 합니다.

텍스트 문자열을 회전하고 캔버스에 한 번만 그리려는 경우 gx_canvas_rotated_text_draw() 서비스가 대안으로 제공됩니다. gx_canvas_rotated_text_draw()는 gx_utility_string_to_alphamap(), gx_utility_pixelmap_rotate(), gx_canvas_pixelmap_draw()를 호출하여 회전된 텍스트를 하나의 작업으로 렌더링합니다. 그러나 같은 텍스트를 여러 각도로 회전하여 여러 번 그리는 경우 gx_utility_string_to_alphmap API를 사용하여 alphamap을 한 번 만든 다음, 필요에 따라 결과 alphamap을 여러 번 회전하는 것이 더 효율적입니다.

### <a name="parameters"></a>매개 변수

- **string**: alphamap에 렌더링할 텍스트 문자열
- **font**: 텍스트를 렌더링하는 데 사용할 글꼴
- **return_map**: 호출자에게 반환되는 GX_PIXELMAP에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**: (0x00) alphamap에 텍스트 문자열을 렌더링했습니다.
- **GX_PTR_ERROR**: (0x07) 입력 포인터가 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) 메모리 할당/해제 함수가 정의되어 있지 않습니다.
- **GX_INVALID_STRING_LENGTH**: (0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING string;

GX_PIXELMAP alphamap;

GX_PIXELMAP rotated_text;

INT xpos;

INT ypos;

gx_widget_font_get(widget, GX_FONT_ID_SCREEN_LABEL, &font);

string.gx_string_ptr = “Hello World”;

string.gx_string_length = strlen(string.gx_string_ptr);

/* render string to alphamap once */
gx_utility_string_to_alphamap_ext(&string, font, &alphamap);

/* rotate and render the alphmap at multiple angles */
gx_utility_pixelmap_rotate(&alphamap, 45, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(10, 10, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 135, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(100, 100, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 300, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(200, 200, &rotated_text);
```

### <a name="see-also"></a>참고 항목

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect

## <a name="gx_vertical_list_children_position"></a>gx_vertical_list_children_position
### <a name="position-children-for-the-vertical-list"></a>세로 목록의 자식 배치

### <a name="prototype"></a>프로토타입

```C
UINT gx_vertical_list_children_position(
    GX_VERTICAL_LIST *vertical_list)
```

### <a name="description"></a>Description

이 함수는 세로 목록의 자식을 배치합니다.

### <a name="parameters"></a>매개 변수

- **vertical_list** 세로 목록 컨트롤 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 세로 목록의 자식을 배치했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Position children in the vertical list */
status = gx_vertical_list_children_position (&vertical_list);

/* If status is GX_SUCCESS the children in the vertical list are positioned.. */
```

### <a name="see-also"></a>참고 항목

- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selecgted_widget_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_create"></a>gx_vertical_list_create
### <a name="create-vertical-list"></a>세로 목록 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_vertical_list_create(
    GX_VERTICAL_LIST *vertical_list,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    VOID (*callback)(GX_VERTICAL_LIST *, GX_WIDGET *, INT),
    ULONG style, USHORT vertical_list_id,
    GX_CONST GX_RECTANGLE *size);
```
### <a name="description"></a>Description

이 서비스는 세로 목록을 만듭니다.

GX_VERTICAL_LIST는 GX_WINDOW에서 파생되며 gx_window API 서비스를 모두 지원합니다.

### <a name="parameters"></a>매개 변수

- **vertical_list** 세로 목록 위젯 컨트롤 블록
- **name** 세로 목록의 이름
- **parent** 부모 위젯에 대한 포인터
- **total_rows** 세로 목록에 있는 행의 총수
- **callback** 목록을 스크롤할 때 세로 목록에서 호출되는 함수. 먼저 호출자가 표시되는 목록 행을 채우기에 충분한 GX_WIDGET 기반 자식을 만들어야 합니다. 목록을 스크롤하면 이 함수가 호출되어 제공된 목록 인덱스에 해당하는 목록 자식을 다시 만듭니다.
- **style** 스크롤 막대 위젯의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **vertical_list_id** 애플리케이션에서 정의된 세로 목록 ID
- **size** 세로 목록의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 세로 목록을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 행 수가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create vertical list “my_list” with 20 rows. */
status = gx_vertical_list_create(&my_list, “my_list”, &my_parent,
                    20, callback, GX_STYLE_WRAP, MY_LIST_ID,
                    &size);

/* If status is GX_SUCCESS the vertical list “my_list” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_vertical_list_children_position
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_event_process"></a>gx_vertical_list_event_process
### <a name="process-vertical-list-event"></a>세로 목록 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_vertical_list_event_process(GX_VERTICAL_LIST *list,
                                                      GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 세로 목록에 대한 이벤트를 처리합니다.

### <a name="parameters"></a>매개 변수

- **list** 세로 목록 위젯 컨트롤 블록
- **event** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 세로 목록 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Process “my_event” for vertical list “my_list”. */
status = gx_vertical_list_event_process(&my_list, &my_event);

/* If status is GX_SUCCESS the event for vertical list “my_list” has been processed. */
```

### <a name="see-also"></a>참고 항목

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_selected_set

## <a name="gx_vertical_list_page_index_set"></a>gx_vertical_list_page_index_set
### <a name="set-starting-page-index"></a>시작 페이지 인덱스 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_vertical_list_page_index_set(
    GX_VERTICAL_LIST *list,
    INT index);
```
### <a name="description"></a>Description

이 서비스는 세로 목록의 시작 인덱스를 설정합니다.

### <a name="parameters"></a>매개 변수

- **list** 세로 목록 위젯 컨트롤 블록
- **index** 새 상위 인덱스

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 세로 목록의 시작 페이지 인덱스를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 위젯 포인터가 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 인덱스 값이 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the starting page index of vertical list “my_list” to 4. */
status = gx_vertical_list_page_index_set(&my_list, 4);

/* If status is GX_SUCCESS the starting page index of “my_list” has
been set to 4. */
```
### <a name="see-also"></a>참고 항목

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_index_get"></a>gx_vertical_list_selected_index_get
### <a name="get-selected-index-from-vertical-list"></a>세로 목록에서 선택된 인덱스 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_vertical_list_selected_index_get(
    GX_VERTICAL_LIST *vertical_list,
    INT *return_index);
```
### <a name="description"></a>Description

이 서비스는 세로 목록에서 선택된 인덱스를 반환합니다.

### <a name="parameters"></a>매개 변수

- **vertical_list** 세로 목록 위젯 컨트롤 블록
- **return_index** 선택된 인덱스의 반환 대상

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 세로 목록 항목을 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
INT current_selected_index;

/* Get the list entry at the current index of vertical list “my_list”. */
status = gx_vertical_list_selected_index_get(&my_list, &current_selected_index);

/* If status is GX_SUCCESS, “current_list_index” contains the index of the selected list item. */
```
### <a name="see-also"></a>참고 항목

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_set"></a>gx_vertical_list_selected_set
### <a name="assign-the-selected-entry-in-a-vertical-list"></a>세로 목록에서 선택된 항목 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_vertical_list_selected_set(
    GX_VERTICAL_LIST *vertical_list,
    INT index);
```

### <a name="description"></a>Description

이 서비스는 세로 목록에서 선택된 항목을 할당합니다. 필요한 경우 세로 목록이 스크롤되어 선택된 항목을 표시합니다.

### <a name="parameters"></a>매개 변수

- **vertical_list** 세로 목록 위젯 컨트롤 블록
- **index** 새 목록 항목의 인덱스 기반 위치

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 세로 목록 항목을 설정했습니다.
- **GX_FAILURE**(0x10) 목록에서 입력 인덱스를 찾을 수 없습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 세로 목록 또는 목록 항목 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the list entry of “my_list” to the child in line 12. */
status = gx_vertical_list_selected_set(&my_list, 12);

/* If status is GX_SUCCESS, the list entry of “my_list” has been successfully set to 12. */
```
### <a name="see-also"></a>참고 항목

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_get
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_widget_get"></a>gx_vertical_list_selected_widget_get
### <a name="get-selected-widget-from-vertical-list"></a>세로 목록에서 선택된 위젯 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_vertical_list_selected_widget_get(
    GX_VERTICAL_LIST *vertical_list,
    GX_WIDGET **return_list_entry);
```
### <a name="description"></a>Description

이 서비스는 세로 목록에서 선택된 위젯을 반환합니다. 목록에 자식 위젯보다 많은 행이 포함되어 있고 선택된 자식 위젯이 뷰에서 스크롤된 경우 위젯이 새 목록 항목을 표시하는 데 재사용되었으므로 이 함수는 GX_WIDGET 포인터로 GX_NULL을 반환합니다.

### <a name="parameters"></a>매개 변수

- **vertical_list** 세로 목록 위젯 컨트롤 블록
- **return_list_entry** 반환 목록 항목 위젯의 대상

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 세로 목록 항목을 가져왔습니다.
- **GX_FAILURE**(0x10) 선택된 위젯이 뷰에서 스크롤되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_WIDGET *current_selected_widget;

/* Get the list entry at the current index of vertical list “my_list”. */
status = gx_vertical_list_selected_widget_get(&my_list, &current_selected_widget);

/* If status is GX_SUCCESS, “current_list_entry” contains a pointer to the currently selected widget. */
```

### <a name="see-also"></a>참고 항목

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_total_rows_set"></a>gx_vertical_list_total_rows_set
### <a name="set-total-number-of-vertical-list-rows"></a>세로 목록 행의 총수 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_vertical_list_total_rows_set(
    GX_VERTICAL_LIST *vertical_list,
    INT count);
```
### <a name="description"></a>Description

이 서비스는 목록 행의 총수를 할당하거나 변경합니다.

### <a name="parameters"></a>매개 변수

- **vertical_list** 세로 목록 위젯 컨트롤 블록
- **count** 새 목록 행 수

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 세로 목록 행 수를 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 행 수 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set the list row count to 20 items. */
status = gx_vertical_list_total_rows_set(&my_list, 20);

/* If status is GX_SUCCESS, the total rows of “my_list” has been set to 20. */
```
### <a name="see-also"></a>참고 항목

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set

## <a name="gx_vertical_scrollbar_create"></a>gx_vertical_scrollbar_create
### <a name="create-vertical-scrollbar"></a>세로 스크롤 막대 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_vertical_scrollbar_create(
    GX_SCROLLBAR *scrollbar,
    GX_CONST GX_CHAR *name, 
    GX_WINDOW *parent,
    GX_SCROLLBAR_APPEARANCE *appearance,
    ULONG style);
```
### <a name="description"></a>Description

이 서비스는 세로 스크롤 막대를 만듭니다.

### <a name="parameters"></a>매개 변수

- **scrollbar** 스크롤 막대 위젯 제어 블록
- **name** 스크롤 막대의 이름
- **parent** 부모 위젯에 대한 포인터
- **appearance** 세로 스크롤 막대 위젯의 모양
- **style** 스크롤 막대의 스타일

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 세로 스크롤 막대를 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 부모 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Create vertical scrollbar “my_scrollbar”. */
status = gx_vertical_scrollbar_create(&my_scrollbar,
                          “my_vertical_scrollbar”,
                          &my_parent, &scrollbar_appearance,
                          GX_STYLE_ENABLED);

/* If status is GX_SUCCESS the vertical scrollbar “my_scrollbar” has been created. */
```
### <a name="see-also"></a>참고 항목

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset

## <a name="gx_widget_allocate"></a>gx_widget_allocate
### <a name="allocate-a-widget-control-block"></a>위젯 제어 블록 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_allocate(
    GX_WIDGET **control_block,
    ULONG memsize);
```
### <a name="description"></a>Description

이 서비스는 애플리케이션에서 정의된 메모리 할당 함수를 호출하여 위젯 제어 블록을 동적으로 할당합니다. GUIX Studio 속성 뷰에서 “동적 할당” 속성이 선택된 경우 주로 GUIX Studio에서 생성된 함수가 제어 블록을 동적으로 할당하는 데 사용합니다.

### <a name="parameters"></a>매개 변수

- **control_block** 반환된 제어 블록 포인터에 대한 포인터
- **memsize** 제어 블록 크기(바이트)

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 할당했습니다.
- **GX_SYSTEM_MEMORY_ERROR**(0x30) 메모리 할당자가 정의되지 않았거나 메모리를 할당하지 못했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_MEMORY_SIZE**(0x29) 메모리 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_TEXT_BUTTON *button;

/* Attach “my_widget” to “my_parent”. */
status = gx_widget_allocate(&button, sizeof(GX_TEXT_BUTTON));

/* If status is GX_SUCCESS the button widget control block is allocated. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_attach"></a>gx_widget_attach
### <a name="attach-widget-to-its-parent"></a>부모에 위젯 연결

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_attach(
    GX_WIDGET *parent, 
    GX_WIDGET *widget);
```
### <a name="description"></a>Description

이 서비스는 지정된 부모에 위젯을 연결합니다. 이미 다른 부모에 연결되어 있는 위젯은 먼저 분리됩니다. 위젯이 동일한 부모에 이미 연결된 경우에는 함수에서 아무 작업도 수행하지 않습니다.

위젯은 z 순서를 기준으로 부모의 맨 앞 자식이 됩니다. 형제 위젯이 겹치면 형제 앞에 위젯이 그려집니다. z 순서의 맨 뒤에 새 위젯을 배치하려면 gx_widget_back_attach 또는 gx_widget_back_move를 사용합니다.

### <a name="parameters"></a>매개 변수

- **parent** 부모 위젯에 대한 포인터
- **widget** 자식 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 연결했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 부모 또는 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Attach “my_widget” to “my_parent”. */
status = gx_widget_attach(&my_parent, &my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is attached to “my_parent”. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_background_draw"></a>gx_widget_background_draw
### <a name="draw-a-widget-background"></a>위젯 배경 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_widget_background_draw(GX_WIDGET *widget);
```
### <a name="description"></a>Description

이 서비스는 위젯 배경의 단색 채우기를 수행합니다. gx_widget_draw 함수에서 자동으로 호출되지만 사용자 지정 위젯 그리기 함수의 일부로 애플리케이션에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **widget** 그릴 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
    /* Call default widget background draw. */
    gx_widget_background_draw(widget);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_back_attach"></a>gx_widget_back_attach
### <a name="attach-widget-to-its-parent"></a>부모에 위젯 연결

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_back_attach(
    GX_WIDGET *parent, 
    GX_WIDGET *widget);
```
### <a name="description"></a>Description

이 서비스는 지정된 부모에 위젯을 연결합니다. 이미 다른 부모에 연결되어 있는 위젯은 먼저 분리됩니다. 위젯이 동일한 부모에 이미 연결된 경우에는 함수에서 아무 작업도 수행하지 않습니다.

위젯은 z 순서를 기준으로 부모의 맨 뒤 자식이 됩니다. 형제 위젯이 겹치면 형제 뒤에 위젯이 그려집니다. z 순서의 맨 앞에 새 위젯을 배치하려면 gx_widget_attach 또는 gx_widget_front_move를 사용합니다.

### <a name="parameters"></a>매개 변수

- **parent** 부모 위젯에 대한 포인터
- **widget** 자식 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 연결했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 부모 또는 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Attach “my_widget” to “my_parent”. */
status = gx_widget_back_attach(&my_parent, &my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is attached to “my_parent”. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_back_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_back_move"></a>gx_widget_back_move
### <a name="move-widget-to-back"></a>위젯을 뒤로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_back_move(
    GX_WIDGET *widget,
    GX_BOOL *return_widget_moved);
```
### <a name="description"></a>Description

이 서비스는 위젯을 부모의 자식 위젯 Z 순서에서 맨 뒤로 이동합니다.

### <a name="parameters"></a>매개 변수

- **parent** 부모 위젯에 대한 포인터
- **return_widget_moved** 위젯이 이동되었음을 나타내는 플래그 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 맨 뒤로 이동했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_NO_CHANGE**(0x08) 변경 내용이 적용되지 않았습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move “my_widget” to the back. */
status = gx_widget_back_move(&my_widget, &moved_flag);

/* If status is GX_SUCCESS and “moved_flag” is GX_TRUE, the widget “my_widget” was moved to the back. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_block_move"></a>gx_widget_block_move
### <a name="move-a-rectangular-block-of-pixels"></a>사각형 픽셀 블록 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_block_move(
    GX_WIDGET *widget,
    GX_RECTANGLE *block,
    INT xshift, INT yshift);
```

### <a name="description"></a>Description

이 서비스는 사각형 픽셀 블록을 이동합니다. 주로 빠른 스크롤을 구현하는 데 사용됩니다.

### <a name="parameters"></a>매개 변수

- **widget** 블록 이동을 요청한 위젯에 대한 포인터
- **block** 이동할 사각형 경계 블록
- **xshift** x 이동 크기(픽셀)
- **yshift** y 이동 크기(픽셀)

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 맨 뒤로 이동했습니다.
- **GX_INVALID_CANVAS**(0x20) 위젯 캔버스를 찾을 수 없습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move a block of pixels 20 pixels to the right. */
status = gx_widget_block_move(&my_widget, &size, 20, 0);

/* If status is GX_SUCCESS the block of pixels was moved. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_draw"></a>gx_widget_border_draw
### <a name="draw-widget-border"></a>위젯 테두리 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_widget_border_draw(
    GX_WIDGET *widget,
    GX_COLOR border_color,
    GX_COLOR upper_fill, 
    GX_COLOR lower_fill, 
    GX_BOOL fill);
```

### <a name="description"></a>Description

이 서비스는 위젯 테두리를 그립니다. 일반적으로 위젯 그리기 함수의 일부로 호출됩니다. 서비스에서 위젯 테두리 스타일 플래그를 해석하여 테두리를 그리지 않거나 가는 테두리, 볼록 테두리, 오목 테두리 또는 두꺼운 테두리를 그립니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **border_color** 테두리 색. **부록 A** 에는 미리 정의된 색이 나와 있습니다. 애플리케이션에서 사용자 지정 색을 추가할 수도 있습니다.
- **upper_fill** 위쪽 채우기 색. **부록 A** 에는 미리 정의된 색이 나와 있습니다. 애플리케이션에서 사용자 지정 색을 추가할 수도 있습니다.
- **lower_fill** 아래쪽 채우기 색. **부록 A** 에는 미리 정의된 색이 나와 있습니다. 애플리케이션에서 사용자 지정 색을 추가할 수도 있습니다.
- **fill** 이 부울 플래그는 위젯 영역을 제공된 채우기 색으로 채울지를 나타냅니다. 이 값이 GX_FALSE이면 위젯 테두리만 그려집니다.

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
      /* Call widget border draw. */
      gx_widget_border_draw(widget, GX_COLOR_BLACK,
                            GX_COLOR_GREEN, GX_COLOR_BLUE,
                            GX_TRUE);

      /* Add your own drawing here. */

      /* Draw child widgets. */
      Gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_style_set"></a>gx_widget_border_style_set
### <a name="set-widget-border-style"></a>위젯 테두리 스타일 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_border_style_set(
    GX_WIDGET *widget, 
    ULONG style);
```

### <a name="description"></a>Description

이 서비스는 위젯 테두리 스타일을 설정합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **style** 테두리의 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 테두리 스타일을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set border style of “my_widget”. */
status = gx_widget_border_style_set(&my_widget,
                                    GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS the widget “my_widget” border style has been set. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_width_get"></a>gx_widget_border_width_get
### <a name="get-widget-border-width"></a>위젯 테두리 두께 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_border_width_get(
    GX_WIDGET *widget,
    GX_VALUE *return_width);
```

### <a name="description"></a>Description

이 서비스는 위젯 테두리 두께를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **return_width** 위젯 테두리 두께 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 테두리 두께를 검색했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_VALUE my_width;

/* Get border width of “my_widget”. */
status = gx_widget_border_width_get(&my_widget, &my_width);

/* If status is GX_SUCCESS, “my_width” contains the border width of the widget “my_widget”. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_canvas_get"></a>gx_widget_canvas_get
### <a name="get-widget-canvas"></a>위젯 캔버스 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_canvas_get(
    GX_WIDGET *widget,
    GX_CANVAS **return_canvas)
```
### <a name="description"></a>Description

이 서비스는 위젯이 렌더링되는 캔버스에 대한 포인터를 반환합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **return_canvas** 위젯 캔버스 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 캔버스를 가져왔습니다.
- **GX_FAILURE**(0x10) 위젯 캔버스를 찾을 수 없습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Get canvas associated with “my_widget”. */
status = gx_widget_canvas_get(&my_widget, &my_canvas);

/* If status is GX_SUCCESS, “my_canvas” contains the canvas of the widget “my_widget”. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_child_detect"></a>gx_widget_child_detect
### <a name="detect-widget-child"></a>위젯 자식 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_child_detect(
    GX_WIDGET *parent, 
    GX_WIDGET *child,
    GX_BOOL *return_detect);
```

### <a name="description"></a>Description

이 서비스는 위젯이 부모 위젯의 자식인지를 검색합니다. 중첩된 자식의 자식을 검색하고 부모 위젯이 자식 위젯의 상위 수준에 있으면 TRUE를 반환합니다.

### <a name="parameters"></a>매개 변수

- **parent** 부모 위젯에 대한 포인터
- **child** 자식 위젯에 대한 포인터
- **return_detect** 검색할 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 자식을 검색했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 부모 또는 자식 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_BOOL detected;

/* Determine if “my_child” is a child of “my_widget”. */
status = gx_widget_child_detect(&my_widget, &my_child, &detected);

/* If status is GX_SUCCESS and “detected” is GX_TRUE, “my_child” is a child of widget “my_widget”. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_children_draw"></a>gx_widget_children_draw
### <a name="draw-widget-children"></a>위젯 자식 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_widget_children_draw(GX_WIDGET *widget);
```

### <a name="description"></a>Description

이 서비스는 부모 위젯의 모든 자식을 그립니다. 일반적으로 모든 표준 위젯 그리기 함수에서 기존 자식 위젯을 그리기 위해 호출되며, 모든 사용자 지정 그리기 함수에서 자식 위젯을 사용자 지정 부모 위젯 형식에 연결할 수 있도록 하기 위해 호출되어야 합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
        /* Call default widget background draw. */
        gx_widget_background_draw(widget);

        /* Add your own drawing here. */

        /* Draw child widgets. */
        gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_client_get"></a>gx_widget_client_get
### <a name="get-widget-client-area"></a>위젯 클라이언트 영역 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_client_get(
    GX_WIDGET *widget,
    GX_VALUE border_width,
    GX_RECTANGLE *return_client_area);
```
### <a name="description"></a>Description

이 서비스는 전체 위젯 크기에서 위젯 테두리 두께를 빼서 위젯의 클라이언트 영역을 컴퓨팅합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **border_width** 위젯 테두리의 두께
- **return_client_area** 클라이언트 영역 반환 대상

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 클라이언트 영역을 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 위젯 테두리가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_RECTANGLE client_area
/* Get client area of widget “my_widget”. */
status = gx_widget_client_get(&my_widget, my_widget_width,
                              &client_area);

/* If status is GX_SUCCESS, the “client_area” is the client area of “my_widget”. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_color_get"></a>gx_widget_color_get
### <a name="get-color"></a>색 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_color_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID resource_id,
    GX_COLOR *return_color);
```

### <a name="description"></a>Description

이 서비스는 제공된 리소스 ID와 연결된 색을 가져옵니다. 표시되는 위젯에서만 서비스를 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯 제어 블록에 대한 포인터
- **resource_id** 색의 리소스 ID. **부록 B** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **return_color** 색 대상에 대한 포인터입니다. **부록 A** 에는 미리 정의된 색이 나와 있습니다. 애플리케이션에서 사용자 지정 색을 추가할 수도 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 색을 가져왔습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_INVALID_CANVAS**(0x20) 위젯 캔버스가 잘못되었거나 위젯이 표시되지 않습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_COLOR actual_color;

/* Get color for resource ID MY_FIRST_COLOR_ID. */
status = gx_widget_color_get(my_widget, MY_FIRST_COLOR_RESOURCE_ID,
                            &actual_color);

/* If status is GX_SUCCESS the actual color is contained in “actual_color”. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_font_get
- gx_widget_pixelmap_get

## <a name="gx_widget_create"></a>gx_widget_create
### <a name="create-widget"></a>위젯 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_create(
    GX_WIDGET *widget, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    ULONG style, 
    USHORT widget_id,
    GX_CONST GX_RECTANGLE *size);
```
### <a name="description"></a>Description

이 서비스는 위젯을 만듭니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **name** 위젯의 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **style** 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **widget_id** 애플리케이션에서 정의된 위젯 ID
- **size** 위젯의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 부모 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_WIDGET my_widget;
GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 0, 0, 100, 100);

/* Get client area of widget “my_widget”. */
status = gx_widget_create(&my_widget, "my widget",
                          &my_parent_window, GX_STYLE_BORDER_RAISED, MY_WIDGET_ID, &size);

/* If status is GX_SUCCESS, the widget “my_widget” has been created. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_created_test"></a>gx_widget_created_test
### <a name="test-if-widget-created"></a>위젯이 생성되었는지 테스트

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_created_test(
    GX_WIDGET *widget,
    GX_BOOL *return_test);
```
### <a name="description"></a>Description

이 서비스는 테스트를 통해 위젯이 이전에 생성되었는지를 확인합니다. 오류가 발생하지 않으면 위젯이 생성되었는지와 관계없이 GX_SUCCESS가 반환됩니다. 테스트 결과는 return_test 포인터에 있습니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **return_test** 테스트 결과 대상

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 테스트를 완료했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_BOOL was_created;

/* Test to see if widget “my_widget” is created. */
status = gx_widget_created_test(&my_widget, &was_created);

/* If status is GX_SUCCESS, no error occurred. If “was_created” is
GX_TRUE, the widget “my_widget” has been created. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_delete"></a>gx_widget_delete
### <a name="delete-widget"></a>위젯 삭제

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_delete(GX_WIDGET *widget);
```

### <a name="description"></a>Description

이 서비스는 위젯을 삭제합니다. 위젯 제어 블록이 동적으로 할당된 경우 동적으로 할당된 스토리지를 해제하기 위해 gx_system_memory_free 서비스가 호출됩니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 삭제했습니다. GX_CALLER_ERROR(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**(0x30) 메모리 해제 함수가 정의되어 있지 않습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Delete widget “my_widget”. */
status = gx_widget_delete(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been deleted. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_detach"></a>gx_widget_detach
### <a name="detach-widget-from-parent"></a>부모에서 위젯 분리

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_detach(GX_WIDGET *widget);
```

### <a name="description"></a>Description

이 서비스는 부모에서 위젯을 분리합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 분리했습니다. GX_CALLER_ERROR(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Detach widget “my_widget” from its parent. */
status = gx_widget_detach(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been detached. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_draw"></a>gx_widget_draw
### <a name="draw-widget"></a>위젯 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_widget_draw(GX_WIDGET *widget);
```

### <a name="description"></a>Description

이 서비스는 위젯을 그립니다. 일반적으로 GUIX 캔버스 새로 고침 메커니즘을 통해 내부적으로 호출되지만 사용자 지정 그리기 함수를 구현하는 데 도움이 되도록 애플리케이션에 노출됩니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
      /* Call default widget draw. */
      gx_widget_draw(widget);

      /* Add your own drawing here. */
}
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_draw_set"></a>gx_widget_draw_set
### <a name="assign-the-widget-drawing-function"></a>위젯 그리기 함수 할당

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_draw_set(
    GX_WIDGET *widget,
    VOID (*drawing_function) (GX_WIDGET *));
```

### <a name="description"></a>Description

이 서비스는 위젯의 기본 그리기 함수를 재정의합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **drawing_function** 그리기 함수에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 그리기 함수를 재정의했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Define a custom drawing function. */
VOID my_drawing_function(GX_WIDGET *widget)
{
      /* Add your own drawing here. */
}

/* Set the drawing function of widget “my_widget” to “my_drawing_function”. */
status = gx_widget_draw_set(&my_widget, my_drawing_function);

/* If status is GX_SUCCESS the widget “my_widget” has the drawning function “my_drawing_function”. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_generate"></a>gx_widget_event_generate
### <a name="generate-widget-event"></a>위젯 이벤트 생성

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_event_generate(
    GX_WIDGET *widget, 
    USHORT event_type, LONG value);
```

### <a name="description"></a>Description

이 서비스는 특정 형식 또는 클래스의 GX_EVENT인 GX_SIGNAL 형식의 이벤트를 생성합니다. gx_widget_event_generate()는 전달된 event_type과 함께 16비트 위젯 ID를 단일 32비트 GX_EVENT gx_event_type 값으로 인코딩합니다. value 매개 변수는 생성된 gx_event. gx_event_payload.gx_event_longdata 필드로 인코딩됩니다.

생성된 event.gx_event_target 필드에는 항상 호출 위젯의 부모가 로드되므로 생성된 이벤트는 항상 생성된 위젯의 부모에게 먼저 전송됩니다.

gx_widget_event_generate는 GX_SIGNAL 범위 이벤트 유형을 전송하는 데만 사용해야 합니다. 사용자 정의 이벤트 유형을 비롯한 다른 모든 이벤트 유형의 경우 GUIX 이벤트 큐에 푸시된 이벤트의 모든 필드에 대해 모든 권한을 부여하는 gx_system_event_send() API를 사용합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **event_type** 이벤트 유형. **부록 E** 에는 미리 정의된 GUIX 이벤트가 나와 있습니다. 애플리케이션에서 이벤트를 추가할 수도 있습니다.
- **value** 추가 이벤트 정보

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 이벤트를 생성했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Generate a redraw event for widget “my_widget”. */
status = gx_widget_event_generate(&my_widget, GX_EVENT_REDRAW, 0);

/* If status is GX_SUCCESS the redraw event for widget “my_widget” has been generated. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get
- gx_system_event_send

## <a name="gx_widget_event_process"></a>gx_widget_event_process
### <a name="process-widget-event"></a>위젯 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_event_process(
    GX_WIDGET *widget, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

모든 위젯의 기본 이벤트 처리 함수입니다. 사용자 지정 이벤트 처리 함수를 작성하는 경우 이벤트 유형의 기본 작업은 항상 위젯의 기반이 되는 위젯 형식에 이벤트를 전달하는 것이어야 합니다. 가장 기본적인 GX_WIDGET 형식 전달을 기반으로 하는 위젯은 gx_widget_event_process를 기본 이벤트 처리 함수로 사용합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **event** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Process event “my_event” for widget “my_widget”. */
status = gx_widget_event_process(&my_widget, &my_event);

/* If status is GX_SUCCESS the event “my_event” for widget “my_widget” has been processed. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_process_set"></a>gx_widget_event_process_set
### <a name="set-event-processing-function-of-widget"></a>위젯 이벤트 처리 함수 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_event_process_set(
    GX_WIDGET *widget,
    UINT (*event_processing) (GX_WIDGET *, GX_EVENT *));
```

### <a name="description"></a>Description

이 서비스는 위젯의 이벤트 처리 함수를 재정의합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **event_processing** 새 이벤트 처리 함수에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 이벤트 처리를 재정의했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
UINT my_event_process(GX_TREE_VIEW *tree_view,
                      GX_EVENT *event)
{
      UINT status = GX_SUCCESS;

      switch(event->gx_event_type)
      {
      case xyz:
            /* Insert custom event handling here */
            break;

      default:
            /* Pass all other events to the default tree view
               event processing */
            status = gx_tree_view_event_process(tree_view, event);
            break;
      }
      return status;
}

/* Use “my_event_process” to process events for widget “my_tree_view”. */
status = gx_widget_event_process_set((GX_WIDGET *)&my_tree_view,
                    (VOID (*)(GX_WIDGET *))my_event_process);

/* If status is GX_SUCCESS all event processing for widget “my_tree_view” is handled by “my_event_process”. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_to_parent"></a>gx_widget_event_to_parent
### <a name="send-event-to-widgets-parent"></a>위젯의 부모에게 이벤트 보내기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_event_to_parent(
    GX_WIDGET *widget,
    GX_EVENT *event);
```
### <a name="description"></a>Description

이 서비스는 위젯의 부모에 이벤트를 보냅니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **event** 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯의 부모에 이벤트를 보냈습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Send my_event to the widget’s parent */
status = gx_widget_event_to_parent(&my_widget, my_event);

/* If status is GX_SUCCESS the event has been delivered to the parent of my_widget. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_fill_color_set"></a>gx_widget_fill_color_set
### <a name="set-widget-background-color"></a>위젯 배경색 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_fill_color_set(
    GX_WIDGET *widget,
    GX_RESOURCE_ID normal_color_id,
    GX_RESOURCE_ID selected_color_id,
    GX_RESOURCE_ID disabled_color_id);
```
### <a name="description"></a>Description

이 서비스는 위젯 배경색을 설정합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **normal_color_id** 정상 상태인 채우기 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **selected_color_id** 위젯에 포커스가 있는 경우 채우기 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.
- **disabled_color_id** GX_STYLE_ENABLED 스타일이 설정되지 않은 경우 채우기 색의 리소스 ID. **부록 A** 에는 미리 정의된 색 리소스 ID가 나와 있습니다. 애플리케이션에서 사용자 지정 색 리소스 ID를 추가할 수도 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 채우기 색을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set background of “my_widget”. */
status = gx_widget_fill_color_set(&my_widget,
                    GX_COLOR_ID_NORMAL_FILL,
                    GX_COLOR_ID_SELECTED_FILL,
                    GX_COLOR_ID_DISABLED_FILL);

/* If status is GX_SUCCESS the widget “my_widget” background has been set. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_find"></a>gx_widget_find
### <a name="find-child-widget-of-parent-widget"></a>부모 위젯의 자식 위젯 찾기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_find(
    GX_WIDGET *parent, 
    USHORT widget_id,
    INT search_depth, 
    GX_WIDGET **return_widget);
```
### <a name="description"></a>Description

이 서비스는 지정된 부모의 자식을 검색하여 요청된 ID 값을 가진 위젯을 찾습니다.

### <a name="parameters"></a>매개 변수

- **parent** 검색이 시작되는 부모 위젯에 대한 포인터
- **widget_id** 검색할 위젯 ID
- **search_depth** 함수가 자식 위젯을 검색할 재귀 중첩 수준을 정의합니다. 값이 0보다 작거나 같으면 부모 위젯의 직계 자식만 검색됩니다. 값이 GX_SEARCH_DEPTH_INFINITE이면 모든 자식 위젯의 모든 자식이 검색됩니다. 0보다 큰 다른 값의 경우 이 값은 함수가 요청된 위젯 ID를 찾은 자식 위젯을 검색하는 중첩 깊이를 제한합니다.
- **return_widget** 찾은 위젯 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 찾았습니다.
- **GX_NOT_FOUND**(0x09) 위젯을 찾을 수 없습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_WIDGET *widget_found;

/* Find widget “my_widget”. */
status = gx_widget_find(&my_widget, GX_SEARCH_DEPTH_INFINITE
                        MY_WIDGET_ID, &widget_found);

/* If status is GX_SUCCESS, the pointer “widget_found” contains the pointer to the widget found. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_first_child_get"></a>gx_widget_first_child_get
### <a name="return-pointer-to-first-child-widget"></a>첫 번째 자식 위젯에 대한 포인터 반환

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_first_child_get(
    GX_WIDGET *parent,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Description

GUIX는 부모 및 자식 위젯의 트리 구조화된 목록을 유지 관리합니다. 이 서비스는 부모의 첫 번째 자식 위젯에 대한 포인터를 반환합니다.

### <a name="parameters"></a>매개 변수

- **parent** 부모 위젯에 대한 포인터
- **widget_return** 반환 위젯 포인터에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 포인터가 반환되었습니다.
- **GX_PTR_ERROR**(0x07) 위젯 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Retrieve child widget pointer. */

GX_WIDGET *get_child_widget(GX_WIDGET *parent)
{
      GX_WIDGET *child;
      UINT status;

      status = gx_widget_first_child_get(parent, &child);
      if (status == GX_SUCCESS)
      {
            return child;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>참고 항목

- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_focus_next"></a>gx_widget_focus_next
### <a name="move-focus-to-next-widget-in-navigation-order"></a>탐색 순서의 다음 위젯으로 포커스 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_focus_next(GX_WIDGET *widget);
```

### <a name="description"></a>Description

이 서비스는 포커스를 받는 위젯의 연결된 목록에서 다음 형제 위젯으로 포커스를 이동합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 포커스가 이동되었습니다.
- **GX_FAILURE**(0x00) 포커스가 이동되지 않았습니다.
- **GX_PTR_ERROR**(0x07) 위젯 포인터가 잘못되었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move focus to next widget in navigation order. */ status =
gx_widget_focus_next(&my_widget);

/* If status is GX_SUCCESS the focus has been moved to the next
widget in the navigation order */
```
### <a name="see-also"></a>참고 항목

- gx_widget_focus_previous

## <a name="gx_widget_focus_previous"></a>gx_widget_focus_previous
### <a name="move-focus-to-previous-widget-in-navigation-order"></a>탐색 순서의 이전 위젯으로 포커스 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_focus_previous(GX_WIDGET *widget);
```

### <a name="description"></a>Description

이 서비스는 탐색 순서의 이전 위젯으로 포커스를 이동합니다.

### <a name="parameters"></a>매개 변수

- **widget** 현재 입력 포커스가 있는 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 포커스가 이동되었습니다.
- **GX_FAILURE**(0x00) 포커스가 이동되지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Move focus to previuos widget in navigation order. */ status =
gx_widget_focus_previous(&my_widget);

/* If status is GX_SUCCESS the input focus has been moved to the
previous widget. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_focus_next

## <a name="gx_widget_font_get"></a>gx_widget_font_get
### <a name="get-font-for-specified-resource-id"></a>지정된 리소스 ID의 글꼴 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_font_get(
    GX_WIDGETG *widget,
    GX_RESOURCE_ID resource_id,
    GX_FONT **return_font);
```
### <a name="description"></a>Description

이 서비스는 위젯이 표시되는 디스플레이의 글꼴 테이블에서 지정된 리소스 ID와 연결된 글꼴을 검색합니다. 표시되는 위젯에서만 함수를 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯 제어 블록에 대한 포인터
- **resource_id** 글꼴의 리소스 ID
- **return_font** 글꼴 포인터 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 글꼴을 검색했습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_INVALID_CANVAS**(0x20) 위젯 캔버스가 잘못되었거나 위젯이 표시되지 않습니다.
- **GX_PTR_ERROR**(0x07) 위젯 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_FONT *my_font;
/* Get font for MY_FONT_ID. */
status = gx_widget_font_get(widget, MY_FONT_RESOURCE_ID, &my_font);
/* If status is GX_SUCCESS the font pointer has been retrieved in “my_font”. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_color_get
- gx_widget_pixelmap_get

## <a name="gx_widget_free"></a>gx_widget_free
### <a name="release-memory-associated-with-a-widget"></a>위젯과 연결된 메모리 해제

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_free(GX_WIDGETG *widget);
```

### <a name="description"></a>Description

이 서비스는 위젯 제어 블록과 연결된 메모리를 해제합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯 제어 블록에 대한 포인터
- **resource_id** 글꼴의 리소스 ID
- **return_font** 글꼴 포인터 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 해제했습니다.
- **GX_SYSTEM_MEMORY_ERROR**(0x30) 메모리 해제 함수가 정의되어 있지 않습니다.
- **GX_PTR_ERROR**(0x07) 위젯 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_WIDGET widget;
UINT status;

status = gx_widget_allocate(&widget, sizeof(GX_WIDGET))

/* Free a runtime allocated widget. */
if (status == GX_SUCCESS)
{
      status = gx_widget_free(widget);
}

/* If status is GX_SUCCESS the memory that allocated to the widget has been released. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_front_move"></a>gx_widget_front_move
### <a name="move-widget-to-front"></a>위젯을 앞으로 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_front_move(
    GX_WIDGET *widget, 
    GX_BOOL *return_moved);
```

### <a name="description"></a>Description

이 서비스는 부모의 자식 위젯 Z 순서 목록에서 위젯을 맨 앞으로 이동합니다.

### <a name="parameters"></a>매개 변수

- **widget** 이동할 위젯에 대한 포인터
- **return_moved** 위젯이 이동되었다는 표시 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 맨 앞으로 이동했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_NO_CHANGE**(0x08) 위젯이 이미 맨 앞에 있습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_BOOL widget_moved;

/* Move widget “my_widget” to the front. */
status = gx_widget_front_move(&my_widget, &widget_moved);

/* If status is GX_SUCCESS and “widget_moved” is GX_TRUE, the
widget “my_widget” was moved to the front . */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_height_get"></a>gx_widget_height_get
### <a name="get-widget-height"></a>위젯 높이 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_height_get(
    GX_WIDGET *widget,
    UINT *return_height);
```

### <a name="description"></a>Description

이 서비스는 위젯 높이를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **return_height** 위젯 높이 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 높이를 가져왔습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_VALUE widget_height;

/* Get height for widget “my_widget”. */
status = gx_widget_height_get(&my_widget, &widget_height);

/* If status is GX_SUCCESS the height of the widget is contained in
“widget_height” . */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_hide"></a>gx_widget_hide
### <a name="hide-widget"></a>위젯 숨기기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_hide(GX_WIDGET *widget);
```

### <a name="description"></a>Description

이 서비스는 위젯을 숨깁니다. 위젯이 여전히 부모에 연결되어 있지만 캔버스에 그릴 수 없습니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 숨겼습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Hide widget “my_widget”. */
status = gx_widget_hide(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is hidden. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_style_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_last_child_get"></a>gx_widget_last_child_get
### <a name="return-pointer-to-last-child-widget"></a>마지막 자식 위젯에 대한 포인터 반환

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_last_child_get(
    GX_WIDGET *parent,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Description

GUIX는 부모 및 자식 위젯의 트리 구조화된 목록을 유지 관리합니다. 이 서비스는 부모의 마지막 자식 위젯에 대한 포인터를 반환합니다.

### <a name="parameters"></a>매개 변수

- **parent** 부모 위젯에 대한 포인터
- **widget_return** 반환 위젯 포인터에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 포인터가 반환되었습니다.
- **GX_PTR_ERROR**(0x07) 위젯 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Retrieve child widget pointer. */

GX_WIDGET *get_last_child_widget(GX_WIDGET *parent)
{

      GX_WIDGET *child;
      UINT status;

      status = gx_widget_last_child_get(parent, &child);
      if (status == GX_SUCCESS)
      {
              return child;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>참고 항목

- gx_widget_first_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_next_sibling_get"></a>gx_widget_next_sibling_get
### <a name="return-pointer-to-next-sibling-of-current-widget"></a>현재 위젯의 다음 형제에 대한 포인터 반환

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_next_sibling_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Description

GUIX는 부모 및 자식 위젯의 트리 구조화된 목록을 유지 관리합니다. 이 서비스는 현재 위젯의 다음 형제에 대한 포인터를 반환합니다.

### <a name="parameters"></a>매개 변수

- **current** 현재 위젯에 대한 포인터
- **widget_return** 반환 위젯 포인터에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 포인터가 반환되었습니다.
- **GX_PTR_ERROR**(0x07) 위젯 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Retrieve next sibling widget pointer. */

GX_WIDGET *get_next(GX_WIDGET *current)
{
      GX_WIDGET *sibling;
      UINT status;

      status = gx_widget_next_sibling_get(current, &sibling);
      if (status == GX_SUCCESS)
      {
            return sibling;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>참고 항목

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_parent_get"></a>gx_widget_parent_get
### <a name="return-pointer-to-parent-of-current-widget"></a>현재 위젯의 부모에 대한 포인터 반환

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_parent_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Description

GUIX는 부모 및 자식 위젯의 트리 구조화된 목록을 유지 관리합니다. 이 서비스는 현재 위젯의 부모에 대한 포인터를 반환합니다.

### <a name="parameters"></a>매개 변수

- **current** 현재 위젯에 대한 포인터
- **widget_return** 반환 위젯 포인터에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 포인터가 반환되었습니다.
- **GX_PTR_ERROR**(0x07) 위젯 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Retrieve parent widget */

GX_WIDGET *get_parent(GX_WIDGET *current)
{
      GX_WIDGET *parent;
      UINT status;

      status = gx_widget_parent_get(current, &parent);
      if (status == GX_SUCCESS)
      {
            return parent;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>참고 항목

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_pixelmap_get"></a>gx_widget_pixelmap_get
### <a name="get-pixelmap"></a>pixelmap 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_pixelmap_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID resource_id,
    GX_PIXELMAP **return_pixelmap);
```

### <a name="description"></a>Description

이 서비스는 제공된 리소스 ID와 연결된 pixelmap을 가져옵니다. 표시되는 위젯에서만 서비스를 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯 제어 블록에 대한 포인터
- **pixelmap_id** pixelmap 리소스 ID
- **return_pixelmap** pixelmap 대상 포인터에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) pixelmap을 가져왔습니다.
- **GX_INVALID_RESOURCE_ID**(0x33) 리소스 ID가 잘못되었습니다.
- **GX_INVALID_CANVAS**(0x20) 위젯 캔버스가 잘못되었거나 위젯이 표시되지 않습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
GX_PIXELMAP *my_pixelmap;

/* Get the pixelmap associated with MY_PIXELMAP_ID. */
status = gx_widget_pixelmap_get(widget, MY_PIXELMAP_RESOURCE_ID,
                                &my_pixelmap);

/* If status is GX_SUCCESS, “my_pixelmap” contains the pixemap pointer. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_color_get
- gx_widget_font_get

## <a name="gx_widget_previous_sibling_get"></a>gx_widget_previous_sibling_get
### <a name="return-pointer-to-previous-sibling-of-the-current-widget"></a>현재 위젯의 이전 형제에 대한 포인터 반환

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_previous_sibling_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```

### <a name="description"></a>Description

GUIX는 부모 및 자식 위젯의 트리 구조화된 목록을 유지 관리합니다. 이 서비스는 현재 위젯의 이전 형제에 대한 포인터를 반환합니다.

### <a name="parameters"></a>매개 변수

- **current** 현재 위젯에 대한 포인터
- **widget_return** 반환 위젯 포인터에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 포인터가 반환되었습니다.
- **GX_PTR_ERROR**(0x07) 위젯 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Retrieve previous sibling widget */

GX_WIDGET *get_previous(GX_WIDGET *current)
{
      GX_WIDGET *sibling;
      UINT status;

      status = gx_widget_previous_sibling_get(current, &sibling);
      if (status == GX_SUCCESS)
      {
          return sibling;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>참고 항목

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_resize"></a>gx_widget_resize
### <a name="resize-widget"></a>위젯 크기 조정

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_resize(
    GX_WIDGET *widget, 
    GX_RECTANGLE *new_size);
```
### <a name="description"></a>Description

이 서비스는 위젯의 크기를 조정합니다. 위젯이 표시되는 경우 자동으로 무효화되고 다시 그리기 위해 큐에 대기됩니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **new_size** 새 위젯 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 크기를 조정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_RECTANGLE new_size;

gx_utility_rectangle_define(&new_size, 0, 0, 100, 100);

/* Resize widget “my_widget”. */
status = gx_widget_resize(&my_widget, &new_size);

/* If status is GX_SUCCESS the widget “my_widget” has been resized. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_shift"></a>gx_widget_shift
### <a name="shift-widget"></a>위젯 이동

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_shift(
    GX_WIDGET *widget, 
    GX_VALUE x_shift,
    GX_VALUE y_shift, 
    GX_BOOL mark_dirty);
```

### <a name="description"></a>Description

이 서비스는 위젯을 이동하고 필요에 따라 더티로 표시합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **x_shift** x축에서 이동할 픽셀 수
- **y_shift** y축에서 이동할 픽셀 수
- **mark_dirty** 더티를 나타내려면 GX_TRUE, 그러지 않으면 GX_FALSE

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 이동했습니다. GX_CALLER_ERROR(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Shift widget “my_widget”. */
status = gx_widget_shift(&my_widget, 10, 20, GX_FALSE);

/* If status is GX_SUCCESS the widget “my_widget” has been shifted. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_show"></a>gx_widget_show
### <a name="show-widget"></a>위젯 표시

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_show(GX_WIDGET *widget);
```

### <a name="description"></a>Description

이 서비스는 위젯을 표시합니다. 위젯은 부모에 연결되어 있고 부모 위젯도 표시되는 경우에만 표시됩니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯을 표시했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Show widget “my_widget”. */
status = gx_widget_show(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been shown. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_add"></a>gx_widget_status_add
### <a name="add-widget-status"></a>위젯 상태 추가

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_status_add(
    GX_WIDGET *widget, 
    ULONG status)
```

### <a name="description"></a>Description

이 서비스는 지정된 위젯에 상태 플래그 조합을 추가합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **status** 추가할 상태

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 상태를 추가했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Add status to widget “my_widget”. */
status = gx_widget_status_add(&my_widget, status_to_add);

/* If status is GX_SUCCESS the widget “my_widget” status was. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_get"></a>gx_widget_status_get
### <a name="get-widget-status"></a>위젯 상태 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_status_get(
    GX_WIDGET *widget,
    ULONG *return_status)
```

### <a name="description"></a>Description

이 서비스는 위젯에서 상태 플래그를 검색합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **return_status** 반환되는 상태에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 상태를 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
ULONT get_status;

/* Retrieve status flag from widget “my_widget”. */ status =
gx_widget_status_get(&my_widget, &get_status);

/* If status is GX_SUCCESS the status from widget “my_widget” is
saved to “get_status”. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_remove"></a>gx_widget_status_remove
### <a name="remove-widget-status"></a>위젯 상태 제거

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_status_remove(
    GX_WIDGET *widget, 
    ULONG status)
```

### <a name="description"></a>Description

이 서비스는 위젯 내부 상태 변수에서 지정된 상태 플래그를 제거합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **status** 제거할 상태

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 상태를 제거했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Remove status of widget “my_widget”. */
status = gx_widget_status_remove(&my_widget, status_to_remove);

/* If status is GX_SUCCESS, the status flags are removed from the
widget “my_widget”. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_test"></a>gx_widget_status_test
### <a name="test-widget-status"></a>위젯 상태 테스트

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_status_test(
    GX_WIDGET *widget, 
    ULONG status,
    GX_BOOL *return_test);
```
### <a name="description"></a>Description

이 서비스는 지정된 위젯의 상태 플래그를 테스트하고 “return_test”가 가리키는 메모리에 결과를 저장합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **status** 테스트할 상태
- **return_status** 테스트 결과 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 상태를 테스트했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_BOOL test_result;

/* Test status of widget “my_widget”. */
status = gx_widget_status_test(&my_widget, status_to_test,
                              &test_result);

/* If status is GX_SUCCESS the widget “my_widget” status was tested
and the result in “test_result”. */
```
### <a name="see-also"></a>참고 항목

- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_widget_string_get"></a>gx_widget_string_get
### <a name="retrieve-string-associated-with-a-visible-widget-and-string-id-deprecated"></a>표시되는 위젯 및 문자열 ID와 연결된 문자열 검색(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_string_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID string_id,
    GX_CONST GX_CHAR **string);
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_widget_string_get_ext()로 대체되었습니다.

이 서비스는 지정된 문자열 ID 값의 문자열 테이블 항목을 반환합니다. 활성 디스플레이가 호출자에서 전달되는 대신 자동으로 결정된다는 점을 제외하고 gx_display_string_get과 유사합니다. 표시되는 위젯에서만 서비스를 사용할 수 있으므로 이 위젯과 연결된 디스플레이를 알 수 있습니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **string_id** 리소스 헤더의 문자열 ID 값
- **string** 문자열을 반환할 변수의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 상태를 테스트했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_CONST GX_CHAR *string;

/* Test status of widget “my_widget”. */
status = gx_widget_string_get(&my_widget, GX_STRING_ID_SHUTDOWN,
      &string);

/* If status is GX_SUCCESS the string has been retrieved */
```
### <a name="see-also"></a>참고 항목

- gx_display_string_get
- gx_display_active_langauge_set

## <a name="gx_widget_string_get_ext"></a>gx_widget_string_get_ext
### <a name="retrieve-string-associated-with-a-visible-widget-and-string-id"></a>표시되는 위젯 및 문자열 ID와 연결된 문자열 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_string_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID string_id,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Description

이 서비스는 지정된 문자열 ID 값의 문자열 테이블 항목을 반환합니다. 활성 디스플레이가 호출자에서 전달되는 대신 자동으로 결정된다는 점을 제외하고 gx_display_string_get과 유사합니다. 표시되는 위젯에서만 서비스를 사용할 수 있으므로 이 위젯과 연결된 디스플레이를 알 수 있습니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **string_id** 리소스 헤더의 문자열 ID 값
- **string** 문자열을 반환할 변수의 주소

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 상태를 테스트했습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_STRING string;

/* Test status of widget “my_widget”. */

status = gx_widget_string_get_ext(&my_widget,
                          GX_STRING_ID_SHUTDOWN, &string);

/* If status is GX_SUCCESS the string has been retrieved */
```

### <a name="see-also"></a>참고 항목

- gx_display_string_get
- gx_display_active_langauge_set

## <a name="gx_widget_style_add"></a>gx_widget_style_add
### <a name="add-widget-style"></a>위젯 스타일 추가

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_style_add(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Description

이 서비스는 위젯에 스타일을 추가합니다. 또한 다음 작업을 수행합니다.

추가된 스타일이 GX_STYLE_TRANSPARENT이면 GX_STATUS_TRANSPARENT 상태가 추가됩니다.

추가된 스타일이 GX_STYLE_ENABLED이면 GX_STATUS_SELECTABLE 상태가 추가됩니다.

위젯이 표시되는 경우 자동으로 무효화되고 다시 그리기 위해 큐에 대기됩니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **style** 추가할 새 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 스타일을 추가했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Add style to widget “my_widget”. */
status = gx_widget_style_add(&my_widget, GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS, the style was successfully applied to the widget “my_widget”. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_get"></a>gx_widget_style_get
### <a name="get-widget-style"></a>위젯 스타일 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_style_get(
    GX_WIDGET *widget, 
    ULONG *return_style)
```

### <a name="description"></a>Description

이 서비스는 위젯에서 스타일 플래그를 검색합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **return_style** 반환되는 스타일에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 스타일을 검색했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드


### <a name="example"></a>예제

```C
/* Retrieve style from widget into “style”. */
status = gx_widget_style_get(&my_widget, &style);

/* If status is GX_SUCCESS the style flag from widget is saved in “style”. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_remove
- gx_widget_style_add
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_remove"></a>gx_widget_style_remove
### <a name="remove-widget-style"></a>위젯 스타일 제거

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_style_remove(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Description

이 서비스는 위젯에서 스타일을 제거합니다. 또한 다음 작업을 수행합니다.

제거된 스타일이 GX_STYLE_TRANSPARENT이면 GX_STATUS_TRANSPARENT 상태가 제거됩니다.

제거된 스타일이 GX_STYLE_ENABLED이면 GX_STATUS_SELECTABLE 상태가 제거됩니다.

위젯이 표시되는 경우 자동으로 무효화되고 다시 그리기 위해 큐에 대기됩니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **style** 제거할 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 스타일을 제거했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Remove style from widget “my_widget”. */
status = gx_widget_style_remove(&my_widget,
                                GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS the GX_STYLE_BORDER_RAISED style was removed from the widget “my_widget”.*/
```

### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_set"></a>gx_widget_style_set
### <a name="set-widget-style"></a>위젯 스타일 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_style_set(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Description

이 서비스는 위젯에 스타일을 설정합니다.

설정된 스타일에 GX_STYLE_TRANSPARENT가 포함된 경우 GX_STATUS_TRANSPARENT 상태가 추가됩니다. 그러지 않으면 상태가 제거됩니다.

설정된 스타일에 GX_STYLE_ENABLED가 포함된 경우 GX_STATUS_SELECTABLE 상태가 추가됩니다. 그러지 않으면 상태가 제거됩니다.

위젯이 표시되는 경우 자동으로 무효화되고 다시 그리기 위해 큐에 대기됩니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **style** 설정할 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 스타일을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set style GX_STYLE_TRANSPARENT to the widget “my_widget”. */
status = gx_widget_style_set(&my_widget, GX_STYLE_TRANSPARENT);

/* If status is GX_SUCCESS the widget “my_widget” style is set to GX_STYLE_TRANSPARENT. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_text_blend"></a>gx_widget_text_blend
### <a name="blend-text-assigned-to-widget-deprecated"></a>위젯에 할당된 텍스트 혼합(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_text_blend(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CHAR *string,
    INT x_offset, 
    INT y_offset, 
    UCHAR alpha)
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_widget_text_blend_ext()로 대체되었습니다.

이 서비스는 현재 브러시 및 텍스트 맞춤을 사용하여 지정된 텍스트를 위젯에 혼합합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **tColor** 텍스트 색
- **font_id** 글꼴 ID
- **string** 그리기 문자열
- **x_offset** 그리기 위치 조정
- **y_offset** 그리기 위치 조정
- **alpha** 혼합 값 0~255

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 너비를 가져왔습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Blend “my_string” over “my_widget” given alpha value 120. */
status = gx_widget_text_blend(&my_widget, my_text_color, my_font_id,
                              &my_string, xoffset, yoffset, 120);

/* If status is GX_SUCCESS “my_string” has been blend to “my_widget”. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_text_blend_ext

## <a name="gx_widget_text_blend_ext"></a>gx_widget_text_blend_ext
### <a name="blend-text-assigned-to-widget"></a>위젯에 할당된 텍스트 혼합

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_text_blend(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CONST GX_STRING *string,
    INT x_offset, 
    INT y_offset, 
    UCHAR alpha)
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_widget_text_blend_ext()로 대체되었습니다.

이 서비스는 현재 브러시 및 텍스트 맞춤과 지정된 색, 글꼴, x,y 오프셋을 사용하여 지정된 위젯에 문자열을 렌더링합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **tColor** 텍스트 색
- **font_id** 글꼴 ID
- **string** 그리기 문자열
- **x_offset** 그리기 위치 조정
- **y_offset** 그리기 위치 조정
- **alpha** 혼합 값 0~255

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 너비를 가져왔습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_STRING_LENGTH**(0x34) 문자열 길이가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
gx_string render_string;
render_string.gx_string_ptr = “Hello”;
render_string.gx_string_length =
    strlen(render_string.gx_string_ptr);

/* Blend “my_string” over “my_widget” given alpha value 120. */
status = gx_widget_text_blend_ext(&my_widget,
        my_text_color,
        my_font_id,
        &render_string, xoffset, yoffset, 120);

/* If status is GX_SUCCESS “my_string” has been blend to “my_widget”. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_text_draw_ext

## <a name="gx_widget_text_draw"></a>gx_widget_text_draw
### <a name="draw-text-assigned-to-widget-deprecated"></a>위젯에 할당된 텍스트 그리기(사용되지 않음)

### <a name="prototype"></a>프로토타입

```C
VOID gx_widget_text_draw(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CHAR *string,
    INT x_offset, 
    INT y_offset)
```

### <a name="description"></a>Description

이 서비스는 사용되지 않으며 gx_widget_text_draw_ext()로 대체되었습니다.

이 서비스는 현재 브러시 및 텍스트 맞춤을 사용하여 지정된 텍스트를 위젯에 그립니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **tColor** 텍스트 색
- **font_id** 글꼴 ID
- **string** 그리기 문자열
- **x_offset** 그리기 위치 조정
- **y_offset** 그리기 위치 조정

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background raw here. */

    /* Call widget text draw. */
    gx_widget_text_draw(widget, my_text_color, my_font_id
                        &my_string, xoffset, yoffset);
}
```

### <a name="see-also"></a>참고 항목

- gx_widget_text_blend
- gx_widget_text_id_draw

## <a name="gx_widget_text_draw_ext"></a>gx_widget_text_draw_ext
### <a name="draw-text-assigned-to-widget"></a>위젯에 할당된 텍스트 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_widget_text_draw(
    GX_WIDGET *widget,
    UINT *tColor,
    UINT font_id, 
    GX_CONST GX_STRING *string,
    INT x_offset,
    INT y_offset)
```

### <a name="description"></a>Description

이 서비스는 현재 브러시 및 텍스트 맞춤을 사용하여 지정된 텍스트를 위젯에 그립니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **tColor** 텍스트 색
- **font_id** 글꼴 ID
- **text_id** 텍스트 ID
- **x_offset** 그리기 위치 조정
- **y_offset** 그리기 위치 조정

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
gx_string render_string;
render_string.gx_string_ptr = “Hello”;
render_string.gx_string_length =
    strlen(render_string.gx_string_ptr);

/* Write a custom widget draw function. */
VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background draw here. */

    /* Call widget text draw. */
    gx_widget_text_draw_ext(widget, my_text_color, my_font_id
                        &render_string, xoffset, yoffset);
}
```

### <a name="see-also"></a>참고 항목

- gx_widget_text_blend
- gx_widget_text_id_draw

## <a name="gx_widget_text_id_draw"></a>gx_widget_text_id_draw
### <a name="draw-text-assigned-to-widget"></a>위젯에 할당된 텍스트 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_widget_text_id_draw(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    UINT text_id,
    INT x_offset, 
    INT y_offse)
```

### <a name="description"></a>Description

이 서비스는 텍스트 ID가 지정된 경우 위젯에 텍스트를 그립니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **tColor** 텍스트 색
- **font_id** 글꼴 ID
- **text_id** 텍스트 ID
- **x_offset** 그리기 위치 조정
- **y_offset** 그리기 위치 조정

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background raw here. */

    /* Call widget text id draw. */
    gx_widget_text_id_draw(widget, my_text_color, my_font_id
                            &my_string_id, xoffset, yoffset);
}
```

### <a name="see-also"></a>참고 항목

- gx_widget_text_blend
- gx_widget_text_draw

## <a name="gx_widget_top_visible_child_find"></a>gx_widget_top_visible_child_find
### <a name="return-pointer-to-visible-child-that-is-top-of-z-order"></a>Z 순서의 맨 위에 있는 표시되는 자식에 대한 포인터 반환

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_top_visible_child_find(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```

### <a name="description"></a>Description

GUIX는 부모 및 자식 위젯의 트리 구조화된 목록을 유지 관리합니다.
이 서비스는 현재 위젯의 맨 위에 있는 표시되는 자식에 대한 포인터를 반환합니다.

### <a name="parameters"></a>매개 변수

- **current** 현재 위젯에 대한 포인터
- **widget_return** 반환 위젯 포인터에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 포인터가 반환되었습니다.
- **GX_PTR_ERROR**(0x07) 위젯 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Retrieve topmost visible widget on the display */

GX_WIDGET *get_top_window(GX_WINDOW_ROOT *root)
{
    GX_WIDGET *top_window;
    UINT status;

    status = gx_widget_top_visible_child_find(root, &top_window);
    if (status == GX_SUCCESS)
    {
        return top_window;
    }
    return GX_NULL;
}
```

### <a name="see-also"></a>참고 항목

- gx_widget_first_child_get,
- gx_widget_last_child_get,
- gx_widget_next_sibling_get,
- gx_widget_parent_get,
- gx_widget_previous_sibling_get

## <a name="gx_widget_type_find"></a>gx_widget_type_find
### <a name="search-for-a-widget-of-the-requested-type"></a>요청된 형식의 위젯 검색

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_type_find(
    GX_WIDGET *parent, 
    USHORT widget_id,
    GX_WIDGET **return_widget)
```

### <a name="description"></a>Description

이 서비스는 요청된 형식의 위젯을 검색합니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **return_width** 위젯 너비 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 너비를 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_WIDGET *retrieved_widget;

/* Find horizontal scrollbar under “parent_widget”. */
status = gx_widget_type_find(&parent_widget,
                GX_TYPE_HORIZONTAL_SCROLL_BAR, &retrieved_widget);

/* If status is GX_SUCCESS, the horizontal scrollbar widget is retrieved. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_widget_width_get"></a>gx_widget_width_get
### <a name="get-widget-width"></a>위젯 너비 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_widget_width_get(
    GX_WIDGET *widget,
    GX_VALUE *return_width)
```

### <a name="description"></a>Description

이 서비스는 위젯의 너비를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯에 대한 포인터
- **return_width** 위젯 너비 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 위젯 너비를 가져왔습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_VALUE my_widget_width;

/* Get width of widget “my_widget”. */
status = gx_widget_width_get(&my_widget, &my_widget_width);

/* If status is GX_SUCCESS the width of widget “my_widget” is in “my_widget_width”. */
```

### <a name="see-also"></a>참고 항목

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_window_client_height_get"></a>gx_window_client_height_get
### <a name="get-window-client-height"></a>창 클라이언트 높이 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_client_height_get(
    GX_WINDOW *window,
    GX_VALUE *return_height);
```

### <a name="description"></a>Description

이 서비스는 창의 클라이언트 높이를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **window** 창에 대한 포인터
- **return_height** 클라이언트 높이 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 창 클라이언트 높이를 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_RECTANGLE my_client_height;

/* Get client height of “my_window”. */
status = gx_window_client_height_get(&my_window,
                                     &my_client_height);

/* If status is GX_SUCCESS the window “my_window” client height is contained in “my_client_height”. */
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- x_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_client_scroll"></a>gx_window_client_scroll
### <a name="scroll-window-clients"></a>창 클라이언트 스크롤

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_client_scroll(
    GX_WINDOW *window, 
    GX_VALUE x_scroll,
    GX_VALUE y_scroll);
```

### <a name="description"></a>Description

이 서비스는 창 클라이언트를 지정된 크기만큼 스크롤합니다.

### <a name="parameters"></a>매개 변수

- **window** 창에 대한 포인터
- **x_scroll** x축에서 스크롤할 크기
- **y_scroll** y축에서 스크롤할 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 창 클라이언트를 스크롤했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_VALUE**(0x22) 스크롤 값이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Scroll clients of “my_window”. */
status = gx_window_client_scroll(&my_window, 10, 0);

/* If status is GX_SUCCESS the clients of window “my_window” have been scrolled. */
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_client_width_get"></a>gx_window_client_width_get
### <a name="get-window-client-width"></a>창 클라이언트 너비 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_client_width_get(
    GX_WINDOW *window,
    GX_VALUE *return_width);
```

### <a name="description"></a>Description

이 서비스는 지정된 창의 클라이언트 너비를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **window** 창에 대한 포인터
- **return_height** 클라이언트 너비 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 창 클라이언트 너비를 가져왔습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_VALUE my_client_widthl

/* Get client width of “my_window”. */
status = gx_window_client_width_get(&my_window, &my_client_width);

/* If status is GX_SUCCESS “my_client_width” contains the client width of window “my_window”. */
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_close"></a>gx_window_close
### <a name="close-modal-window"></a>모달 창 닫기

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_close(GX_WINDOW *window);
```

### <a name="description"></a>Description

이 서비스는 모달 창이 부모에서 분리되고 모달 실행 루프에서 반환되도록 강제 적용합니다.

### <a name="parameters"></a>매개 변수

- **window** 창 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 창을 닫았습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Close window “my_window”. */
status = gx_window_close(&my_window);

/* If status is GX_SUCCESS window “my_window” has been closed. */
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_create"></a>gx_window_create
### <a name="create-window"></a>창 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_create(
    GX_WINDOW *window, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    ULONG style,
    USHORT window_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Description

이 서비스는 창을 만듭니다.

GX_WINDOW는 GX_WIDGET에서 파생되며 gx_widget API 서비스를 모두 지원합니다.

### <a name="parameters"></a>매개 변수

- **window** 창 제어 블록에 대한 포인터
- **name** 창의 논리적 이름
- **parent** 부모 위젯에 대한 포인터
- **style** 창 스타일. **부록 D** 에는 모든 위젯용으로 미리 정의된 일반 스타일과 위젯별 스타일이 나와 있습니다.
- **window_id** 애플리케이션에서 정의된 창 ID
- **size** 창의 크기

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 창을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_WINDOW my_window;

/* Create window “my_window”. */
status = gx_window_create(&my_window, "my window",
                          &my_parent_window, GX_STYLE_BORDER_RAISED,
                          MY_WINDOW_ID, &size);

/* If status is GX_SUCCESS window “my_window” has been created. */
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_draw"></a>gx_window_draw
### <a name="draw-window"></a>창 그리기

### <a name="prototype"></a>프로토타입

```C
VOID gx_window_draw(GX_WINDOW *window);
```

### <a name="description"></a>Description

이 서비스는 창을 그립니다. 일반적으로 캔버스를 새로 고치는 동안 내부적으로 호출되지만 사용자 지정 창 그리기 함수에서 호출할 수도 있습니다.

### <a name="parameters"></a>매개 변수

- **window** 창 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **없음**

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Write a custom window draw function. */

VOID my_custom_window_draw(GX_WINDOW *window)
{
    /* Call default window draw. */
    gx_window_draw(window);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_event_process"></a>gx_window_event_process
### <a name="process-window-event"></a>창 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_event_process(
    GX_WINDOW *window, 
    GX_EVENT *event);
```

### <a name="description"></a>Description

이 서비스는 창에 대한 이벤트를 처리합니다.

### <a name="parameters"></a>매개 변수

- **window** 창 제어 블록에 대한 포인터
- **event** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 창 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic window event processing as part of custom event processing function. */

UINT custom_window_event_process(GX_WINDOW *window,
                                 GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default window
            event processing */
            status = gx_window_event_process(window, event);
            break;
        }
        return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_execute"></a>gx_window_execute
### <a name="modally-execute-a-window"></a>모달 형식으로 창 실행

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_execute(
    GX_WINDOW *window,
    ULONG *return_ptr)
```

### <a name="description"></a>Description

이 서비스는 모달 형식으로 창을 실행합니다. 창 클라이언트 영역 외부의 모든 사용자 입력(펜 이벤트 등)이 무시됩니다. 이 함수는 연속 차단 실행 루프를 시작하고 모델 실행이 종료될 때까지 호출자에게 반환되지 않습니다.

수신된 이벤트에 대한 이벤트 처리에서 0이 아닌 상태 값을 반환하거나 gx_window_close API 함수가 호출되면 모달 실행이 종료됩니다. 이 API에 전달된 return_ptr을 통해 호출자에게 0이 아닌 이벤트 처리 반환 코드가 반환됩니다.

### <a name="parameters"></a>매개 변수

- **window** 창 제어 블록에 대한 포인터
- **return_ptr** 모달 실행 종료 상태를 저장할 위치. GX_NULL이 될 수 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 실행했습니다.
- **GX_SYSTEM_EVENT_RECEIVE_ERROR**(0x05) 이벤트 큐에서 이벤트를 픽업하지 못했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Execute a modal window. */
status = gx_window_execute(&my_window, &return_code);

/* If status is GX_SUCCESS the window was executed, and return_code holds the execution return code. */
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_create"></a>gx_window_root_create
### <a name="create-a-root-window"></a>루트 창 만들기

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_root_create(
    GX_WINDOW_ROOT *root_window,
    GX_CONST GX_CHAR *name,
    GX_CANVAS *canvas, 
    ULONG style,
    USHORT id,
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>Description

이 서비스는 루트 창을 만듭니다.

### <a name="parameters"></a>매개 변수

- **root_window** 루트 창 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 루트 창을 만들었습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_SIZE**(0x19) 위젯 제어 블록 크기가 잘못되었습니다.
- **GX_ALREADY_CREATED**(0x13) 위젯이 이미 생성되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_ROOT_WINDOW root_window;
GX_CANVAS canvas;

/* Create canvas here. */

/* Create a root window */
status = gx_window_root_create(&root_window, “root”, &canvas,
GX_STYLE_BORDER_NONE, GX_NULL, &size);

/* If status is GX_SUCCESS, the “root_window” is successfully created. */
```

### <a name="see-also"></a>참고 항목

- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find

## <a name="gx_window_root_delete"></a>gx_window_root_delete
### <a name="destroy-a-root-window"></a>루트 창 삭제

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_root_delete(GX_WINDOW_ROOT *root_window)
```

### <a name="description"></a>Description

이 서비스는 루트 창을 삭제합니다.

### <a name="parameters"></a>매개 변수

- **root_window** 루트 창 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 루트 창을 삭제했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_SYSTEM_MEMORY_ERROR**(0x30) 메모리 해제 함수가 정의되어 있지 않습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Delete a root window */
status = gx_window_root_delete(&root_window);

/* If status is GX_SUCCESS the “root_window” is destroyed. */
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_event_process"></a>gx_window_root_event_process
### <a name="process-event-for-the-root-window"></a>루트 창 이벤트 처리

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_root_create(
    GX_WINDOW_ROOT *root_window,
    GX_EVENT *event)
```

### <a name="description"></a>Description

이 서비스는 지정된 루트 창에 대한 이벤트를 처리합니다.

### <a name="parameters"></a>매개 변수

- **root_window** 루트 창 제어 블록에 대한 포인터
- **event** 처리할 이벤트에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 루트 창 이벤트를 처리했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```C
/* Call generic root window event processing as part of custom event processing function. */

UINT custom_root_window_event_process(GX_ROOT_WINDOW *root,
                                      GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default root window
            event processing */
        status = gx_window_root_event_process(root, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_find"></a>gx_window_root_find
### <a name="find-root-window"></a>루트 창 찾기

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_root_find(
    GX_WIDGET *widget,
    GX_WINDOW_ROOT **return_root_window);
```

### <a name="description"></a>Description

이 서비스는 지정된 위젯의 루트 창을 찾습니다.

### <a name="parameters"></a>매개 변수

- **widget** 위젯 제어 블록에 대한 포인터
- **return_root_window** 찾은 루트 창 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 루트 창을 찾았습니다.
- **GX_FAILURE**(0x00) 루트 창이 없습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Find root window associated with window “my_window”. */
status = gx_window_root_find(&my_window, &root_window);

/* If status is GX_SUCCESS the “root_window” contains the root window for window “my_window”. */
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_scroll_info_get"></a>gx_window_scroll_info_get
### <a name="get-window-scroll-info"></a>창 스크롤 정보 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_scroll_info_get(
    GX_WINDOW *window, 
    ULONG style,
    GX_SCROLL_INFO *return_scroll_info);
```

### <a name="description"></a>Description

이 서비스는 창 스크롤 정보를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **window** 창에 대한 포인터
- **style** GX_SCROLLBAR_HORIZONTAL 또는 GX_SCROLLBAR_VERTICAL
- **return_scroll_info** 스크롤 정보 대상에 대한 포인터입니다. 부모 창에서 이 구조체를 초기화하여 부모 창 전체 크기, 볼 수 있는 영역, 스크롤 증분 및 한도를 스크롤 막대에 알립니다. 기본 구현에서는 창 클라이언트 영역을 볼 수 있는 영역으로 사용하고 픽셀 단위로 스크롤되지만 사용자 지정 창 구현에서는 스크롤 매개 변수를 활용할 수 있습니다. **부록 I** 에는 GX_SCROLL_INFO 구조체의 정의가 나와 있습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 창 스크롤 정보를 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_TYPE**(0x1B) 유형이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_SCROLL_INFO scroll_info;

/* Get scroll information for window “my_window”. */
status = gx_window_scroll_info_get(&my_window,
                    GX_SCROLLBAR_HORIZONTAL, &scroll_info);

/* If status is GX_SUCCESS the “scroll_info” contains the scroll information for window “my_window”. */
```
### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_scrollbar_find"></a>gx_window_scrollbar_find
### <a name="find-window-scrollbar"></a>창 스크롤 막대 찾기

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_scrollbar_find(
    GX_WINDOW *window, 
    USHORT type,
    GX_SCROLLBAR **return_scrollbar);
```

### <a name="description"></a>Description

이 서비스는 지정된 창의 스크롤 막대를 찾습니다.

### <a name="parameters"></a>매개 변수

- **window** 창에 대한 포인터
- **type** GX_TYPE_VERTICAL_SCROLL 또는 GX_TYPE_HORIZONTAL_SCROLL
- **return_scrollbar** 스크롤 막대 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 창 스크롤 막대를 찾았습니다.
- **GX_NOT_FOUND**(0x09) 스크롤 막대를 찾을 수 없습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.
- **GX_INVALID_TYPE**(0x1B) 유형이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Find horizontal scrollbar for window “my_window”. */
status = gx_window_scrollbar_find(&my_window,
                 GX_SCROLLBAR_HORIZONTAL, &my_scrollbar);

/* If status is GX_SUCCESS the “my_scrollbar” contains the horizontal scrollbar for window “my_window”. */
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_wallpaper_get"></a>gx_window_wallpaper_get
### <a name="get-window-wallpaper"></a>창 배경 화면 가져오기

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_wallpaper_get(
    GX_WINDOW *window,
    GX_RESOURCE_ID *return_wallpaper_id);
```

### <a name="description"></a>Description

이 서비스는 지정된 창의 배경 화면을 가져옵니다.

### <a name="parameters"></a>매개 변수

- **window** 창에 대한 포인터
- **return_wallpaper_id** 배경 화면의 리소스 ID 대상에 대한 포인터

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 창 배경 화면을 가져왔습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
GX_RESOURCE_ID my_window_wallpaper;

/* Get wallpaper for window “my_window”. */
status = gx_window_wallpaper_get(&my_window, &my_window_wallpaper);

/* If status is GX_SUCCESS the “my_window_wallpaper” contains the wallpaper resource ID for window “my_window”. */
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_set

## <a name="gx_window_wallpaper_set"></a>gx_window_wallpaper_set
### <a name="set-window-wallpaper"></a>창 배경 화면 설정

### <a name="prototype"></a>프로토타입

```C
UINT gx_window_wallpaper_set(
    GX_WINDOW *window,
    GX_RESOURCE_ID wallpaper_id,
    GX_BOOL tile);
```

### <a name="description"></a>Description

이 서비스는 지정된 창의 배경 화면을 설정합니다.

### <a name="parameters"></a>매개 변수

- **window** 창에 대한 포인터
- **wallpaper_id** 사용할 배경 화면의 리소스 ID
- **tile** GX_TRUE이면 배경 화면이 바둑판식으로 배열되고, 그러지 않으면 배경 화면이 바둑판식으로 배열되지 않습니다.

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 창 배경 화면을 설정했습니다.
- **GX_CALLER_ERROR**(0x11) 함수의 호출자가 잘못되었습니다.
- **GX_PTR_ERROR**(0x07) 포인터가 잘못되었습니다.
- **GX_INVALID_WIDGET**(0x12) 위젯이 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```C
/* Set wallpaper for window “my_window”. */
status = gx_window_wallpaper_set(&my_window,
                                 MY_WALLPAPER_RESOURCE_ID,
                                 GX_TRUE);

/* If status is GX_SUCCESS the wallpaper for window “my_window” is set. */
```

### <a name="see-also"></a>참고 항목

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
-  gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
