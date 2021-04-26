---
title: 9장 - Azure RTOS BX 추적 이벤트
description: 이 장은 TraceX에서 표시하는 Azure RTOS 이벤트에 대한 설명을 포함합니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 98561fe1d131e1d1b0893b7d89eb720881a82ac8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813165"
---
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a>9장 - Azure RTOS BX 추적 이벤트

이 장은 TraceX에서 표시하는 Azure RTOS 이벤트에 대한 설명을 포함합니다. 

## <a name="list-of-events-and-icons"></a>이벤트 및 아이콘 목록

다음은 TraceX에 의해 표시되는 USBX 이벤트 목록입니다.

| 아이콘                             | 의미                               |
| -------------------------------- | ------------------------------------- |
| ![디바이스 클래스 C D C 활성화 아이콘](./media/user-guide/usbx-events/image1.png)    | **디바이스 클래스 Cdc 활성화**(ux_device_class_cdc_activate) |
| ![디바이스 클래스 C D C 비활성화 아이콘](./media/user-guide/usbx-events/image2.png)    | **디바이스 클래스 Cdc 비활성화**(ux_device_class_cdc_deactivate) |
| ![디바이스 클래스 C D C 읽기 아이콘](./media/user-guide/usbx-events/image3.png)    | **디바이스 클래스 Cdc 읽기**(ux_device_class_cdc_read) |
| ![디바이스 클래스 C D C 쓰기 아이콘](./media/user-guide/usbx-events/image4.png)    | **디바이스 클래스 Cdc 쓰기**(ux_device_class_cdc_write) |
| ![디바이스 클래스 Dpump 활성화 아이콘](./media/user-guide/usbx-events/image5.png)    | **디바이스 클래스 Dpump 활성화**(ux_device_class_dpump_activate) |
| ![디바이스 클래스 Dpump 비활성화 아이콘](./media/user-guide/usbx-events/image6.png)    | **디바이스 클래스 Dpump 비활성화** |
| ![디바이스 클래스 Dpump 읽기 아이콘](./media/user-guide/usbx-events/image7.png)    | **디바이스 클래스 Dpump 읽기**(ux_device_class_dpump_read) |
| ![디바이스 클래스 Dpump 쓰기 아이콘](./media/user-guide/usbx-events/image8.png)    | **디바이스 클래스 Dpump 쓰기** |
| ![디바이스 클래스 Hid 활성화 아이콘](./media/user-guide/usbx-events/image9.png)    | **디바이스 클래스 Hid 활성화**(ux_device_class_hid_activate) |
| ![디바이스 클래스 Hid 비활성화 아이콘](./media/user-guide/usbx-events/image10.png)    | **디바이스 클래스 Hid 비활성화** |
| ![디바이스 클래스 Hid 설명자 보내기 아이콘](./media/user-guide/usbx-events/image11.png)    | **디바이스 클래스 Hid 설명자 보내기**(ux_device_class_hid_descriptor_send) |
| ![디바이스 클래스 Hid 이벤트 가져오기 아이콘](./media/user-guide/usbx-events/image12.png)    | **디바이스 클래스 Hid 이벤트 가져오기**(ux_device_class_hid_event_get) |
| ![디바이스 클래스 Hid 이벤트 설정 아이콘](./media/user-guide/usbx-events/image13.png)    | **디바이스 클래스 Hid 이벤트 설정** |
| ![디바이스 클래스 Hid 보고서 가져오기 아이콘](./media/user-guide/usbx-events/image14.png)    | **디바이스 클래스 Hid 보고서 가져오기**(ux_device_class_hid_report_get) |
| ![디바이스 클래스 Hid 보고서 설정 아이콘](./media/user-guide/usbx-events/image15.png)    | **디바이스 클래스 Hid 보고서 설정**(ux_device_class_hid_report_set) |
| ![디바이스 클래스 Pima 활성화 아이콘](./media/user-guide/usbx-events/image16.png)    | **디바이스 클래스 Pima 활성화**(ux_device_class_pima_activate) |
| ![디바이스 클래스 Pima 비활성화 아이콘](./media/user-guide/usbx-events/image17.png)    | **디바이스 클래스 Pima 비활성화**(ux_device_class_pima_deactivate) |
| ![디바이스 클래스 Pima 디바이스 정보 보내기 아이콘](./media/user-guide/usbx-events/image18.png)    | **디바이스 클래스 Pima 디바이스 정보 보내기**(ux_device_class_pima_device_info_send) |
| ![디바이스 클래스 Pima 이벤트 가져오기 아이콘](./media/user-guide/usbx-events/image19.png)    | **디바이스 클래스 Pima 이벤트 가져오기**(ux_device_class_pima_event_get) |
| ![디바이스 클래스 Pima 이벤트 설정 아이콘](./media/user-guide/usbx-events/image20.png)    | **디바이스 클래스 Pima 이벤트 설정**(ux_device_class_pima_event_set) |
| ![디바이스 클래스 Pima 개체 추가 아이콘](./media/user-guide/usbx-events/image21.png)    | **디바이스 클래스 Pima 개체 추가**(ux_device_class_pima_object_add) |
| ![디바이스 클래스 Pima 개체 데이터 가져오기 아이콘](./media/user-guide/usbx-events/image22.png)    | **디바이스 클래스 Pima 개체 데이터 가져오기**(ux_device_class_pima_object_data_get) |
| ![디바이스 클래스 Pima 개체 데이터 보내기 아이콘](./media/user-guide/usbx-events/image23.png)    | **디바이스 클래스 Pima 개체 데이터 보내기**(ux_device_class_pima_object_data_send) |
| ![디바이스 클래스 Pima 개체 삭제 아이콘](./media/user-guide/usbx-events/image24.png)    | **디바이스 클래스 Pima 개체 삭제**(ux_device_class_pima_object_delete) |
| ![디바이스 클래스 Pima 개체 핸들 보내기 아이콘](./media/user-guide/usbx-events/image25.png)    | **디바이스 클래스 Pima 개체 핸들 보내기**(ux_device_class_pima_object_handles_send) |
| ![디바이스 클래스 Pima 개체 정보 가져오기 아이콘](./media/user-guide/usbx-events/image26.png)    | **디바이스 클래스 Pima 개체 정보 가져오기**(ux_device_class_pima_object_info_get) |
| ![디바이스 클래스 Pima 개체 정보 보내기 아이콘](./media/user-guide/usbx-events/image27.png)    | **디바이스 클래스 Pima 개체 정보 보내기**(ux_device_class_pima_object_info_send) |
| ![디바이스 클래스 Pima 개체 번호 보내기 아이콘](./media/user-guide/usbx-events/image28.png)    | **디바이스 클래스 Pima 개체 번호 보내기**(ux_device_class_pima_objects_number_send) |
| ![디바이스 클래스 Pima 부분 개체 데이터 가져오기 아이콘](./media/user-guide/usbx-events/image29.png)    | **디바이스 클래스 Pima 부분 개체 데이터 가져오기**(ux_device_class_pima_partial_object_data_get) |
| ![디바이스 클래스 Pima 응답 보내기 아이콘](./media/user-guide/usbx-events/image30.png)    | **디바이스 클래스 Pima 응답 보내기**(ux_device_class_pima_response_send)|
| ![디바이스 클래스 Pima 스토리지 ID 보내기 아이콘](./media/user-guide/usbx-events/image31.png)    | **디바이스 클래스 Pima 스토리지 ID 보내기**(ux_device_class_pima_storage_id_send) |
| ![디바이스 클래스 Pima 스토리지 정보 보내기 아이콘](./media/user-guide/usbx-events/image32.png)    | **디바이스 클래스 Pima 스토리지 정보 보내기**(ux_device_class_pima_storage_info_send) |
| ![디바이스 클래스 RNDIS 활성화 아이콘](./media/user-guide/usbx-events/image33.png)    | **디바이스 클래스 RNDIS 활성화**(ux_device_class_rndis_activate) |
| ![디바이스 클래스 RNDIS 비활성화 아이콘](./media/user-guide/usbx-events/image34.png)    | **디바이스 클래스 RNDIS 비활성화**(ux_device_class_rndis_deactivate) |
| ![디바이스 클래스 RNDIS 메시지 유지 아이콘](./media/user-guide/usbx-events/image35.png)    | **디바이스 클래스 RNDIS 메시지 유지**(ux_device_class_rndis_msg_keep_alive) |
| ![디바이스 클래스 RNDIS 메시지 쿼리 아이콘](./media/user-guide/usbx-events/image36.png)    | **디바이스 클래스 RNDIS 메시지 쿼리**(ux_device_class_rndis_msg_query) |
| ![디바이스 클래스 RNDIS 메시지 재설정 아이콘](./media/user-guide/usbx-events/image37.png)    | **디바이스 클래스 RNDIS 메시지 재설정**(ux_device_class_rndis_msg_reset) |
| ![디바이스 클래스 RNDIS 메시지 설정 아이콘](./media/user-guide/usbx-events/image38.png)    | **디바이스 클래스 RNDIS 메시지 설정**(ux_device_class_rndis_msg_set) |
| ![디바이스 클래스 RNDIS 패킷 수신 아이콘](./media/user-guide/usbx-events/image39.png)    | **디바이스 클래스 Rndis 패킷 수신**(ux_device_class_rndis_packet_receive) |
| ![디바이스 클래스 RNDIS 패킷 전송 아이콘](./media/user-guide/usbx-events/image40.png)    | **디바이스 클래스 RNDIS 패킷 전송**(ux_device_class_rndis_packet_transmit) |
| ![디바이스 클래스 스토리지 활성화 아이콘](./media/user-guide/usbx-events/image41.png)    | **디바이스 클래스 스토리지 활성화**(ux_device_class_storage_activate) |
| ![디바이스 클래스 스토리지 비활성화 아이콘](./media/user-guide/usbx-events/image42.png)    | **디바이스 클래스 스토리지 비활성화**(ux_device_class_storage_deactivate) |
| ![디바이스 클래스 스토리지 형식 아이콘](./media/user-guide/usbx-events/image43.png)    | **디바이스 클래스 스토리지 형식**(ux_device_class_storage_format) |
| ![디바이스 클래스 스토리지 조회 아이콘](./media/user-guide/usbx-events/image44.png)    | **디바이스 클래스 스토리지 조회**(ux_device_class_storage_inquiry) |
| ![디바이스 클래스 스토리지 모드 선택 아이콘](./media/user-guide/usbx-events/image45.png)    | **디바이스 클래스 스토리지 모드 선택**(ux_device_class_storage_mode_select) |
| ![디바이스 클래스 스토리지 모드 센스 아이콘](./media/user-guide/usbx-events/image46.png)    | **디바이스 클래스 스토리지 모드 센스**(ux_device_class_storage_mode_sense) |
| ![디바이스 클래스 스토리지의 미디어 제거 방지 허용 아이콘](./media/user-guide/usbx-events/image47.png)    | **디바이스 클래스 스토리지의 미디어 제거 방지 허용**(ux_device_class_storage_prevent_allow_media_removal) |
| ![디바이스 클래스 스토리지 읽기 아이콘](./media/user-guide/usbx-events/image48.png)    | **디바이스 클래스 스토리지 읽기**(ux_device_class_storage_read) |
| ![디바이스 클래스 스토리지 읽기 용량 아이콘](./media/user-guide/usbx-events/image49.png)    | **디바이스 클래스 스토리지 읽기 용량**(ux_device_class_storage_read_capacity) |
| ![디바이스 클래스 스토리지 읽기 형식 용량 아이콘](./media/user-guide/usbx-events/image50.png)    | **디바이스 클래스 스토리지 읽기 형식 용량**(ux_device_class_storage_read_format_capacity) |
| ![디바이스 클래스 스토리지 TOC 읽기 아이콘](./media/user-guide/usbx-events/image51.png)    | **디바이스 클래스 스토리지 TOC 읽기**(ux_device_class_storage_read_toc) |
| ![디바이스 클래스 스토리지 요청 센스 아이콘](./media/user-guide/usbx-events/image52.png)    | **디바이스 클래스 스토리지 요청 센스**(ux_device_class_storage_request_sense) |
| ![디바이스 클래스 스토리지 시작 중지 아이콘](./media/user-guide/usbx-events/image53.png)    | **디바이스 클래스 스토리지 시작 중지**(ux_device_class_storage_start_stop) |
| ![디바이스 클래스 스토리지 테스트 준비 아이콘](./media/user-guide/usbx-events/image54.png)    | **디바이스 클래스 스토리지 테스트 준비**(ux_device_class_storage_test_ready) |
| ![디바이스 클래스 스토리지 확인 아이콘](./media/user-guide/usbx-events/image55.png)    | **디바이스 클래스 스토리지 확인**(ux_device_class_storage_verify) |
| ![디바이스 클래스 스토리지 쓰기 아이콘](./media/user-guide/usbx-events/image56.png)    | **디바이스 클래스 스토리지 쓰기**(ux_device_class_storage_write) |
| ![디바이스 스택 대체 설정 가져오기 아이콘](./media/user-guide/usbx-events/image57.png)    | **디바이스 스택 대체 설정 가져오기**(ux_device_stack_alternate_setting_get) |
| ![디바이스 스택 대체 설정 설정 아이콘](./media/user-guide/usbx-events/image58.png)    | **디바이스 스택 대체 설정 설정**(ux_device_stack_alternate_setting_set) |
| ![디바이스 스택 클래스 등록 아이콘](./media/user-guide/usbx-events/image59.png)    | **디바이스 스택 클래스 등록**(ux_device_stack_class_register) |
| ![디바이스 스택 지우기 기능 아이콘](./media/user-guide/usbx-events/image60.png)    | **디바이스 스택 지우기 기능**(ux_device_stack_clear_feature) |
| ![디바이스 스택 구성 가져오기 아이콘](./media/user-guide/usbx-events/image61.png)    | **디바이스 스택 구성 가져오기**(ux_device_stack_configuration_get) |
| ![디바이스 스택 구성 설정 아이콘](./media/user-guide/usbx-events/image62.png)    | **디바이스 스택 구성 설정**(ux_device_stack_configuration_set) |
| ![디바이스 스택 연결 아이콘](./media/user-guide/usbx-events/image63.png)    | **디바이스 스택 연결** (ux_device_stack_connect) |
| ![디바이스 스택 설명자 보내기 아이콘](./media/user-guide/usbx-events/image64.png)    | **디바이스 스택 설명자 보내기**(ux_device_stack_descriptor_send) |
| ![디바이스 스택 연결 끊기 아이콘](./media/user-guide/usbx-events/image65.png)    | **디바이스 스택 연결 끊기**(ux_device_stack_disconnect) |
| ![디바이스 스택 엔드포인트 정지 아이콘](./media/user-guide/usbx-events/image66.png)    | **디바이스 스택 엔드포인트 정지**(ux_device_stack_endpoint_stall) |
| ![디바이스 스택 상태 가져오기 아이콘](./media/user-guide/usbx-events/image67.png)    | **디바이스 스택 상태 가져오기**(ux_device_stack_get_status) |
| ![디바이스 스택 호스트 절전 모드 해제 아이콘](./media/user-guide/usbx-events/image68.png)    | **디바이스 스택 호스트 절전 모드 해제**(ux_device_stack_host_wakeup) |
| ![디바이스 스택 초기화 아이콘](./media/user-guide/usbx-events/image69.png)    | **디바이스 스택 초기화** (ux_device_stack_initialize) |
| ![디바이스 스택 인터페이스 삭제 아이콘](./media/user-guide/usbx-events/image70.png)    | **디바이스 스택 인터페이스 삭제**(ux_device_stack_interface_delete) |
| ![디바이스 스택 인터페이스 가져오기 아이콘](./media/user-guide/usbx-events/image71.png)    | **디바이스 스택 인터페이스 가져오기**(ux_device_stack_interface_get) |
| ![디바이스 스택 인터페이스 설정 아이콘](./media/user-guide/usbx-events/image72.png)    | **디바이스 스택 인터페이스 설정**(ux_device_stack_interface_set) |
| ![디바이스 스택 기능 설정 아이콘](./media/user-guide/usbx-events/image73.png)    | **디바이스 스택 기능 설정**(ux_device_stack_set_feature) |
| ![디바이스 스택 전송 중단 아이콘](./media/user-guide/usbx-events/image74.png)    | **디바이스 스택 전송 중단**(ux_device_stack_transfer_abort) |
| ![*디바이스 스택 전송 모든 요청 중단 아이콘](./media/user-guide/usbx-events/image75.png)    | **디바이스 스택 전송 모든 요청 중단**(ux_device_stack_transfer_all_request_abort) |
| ![디바이스 스택 전송 요청 아이콘](./media/user-guide/usbx-events/image76.png)    | **디바이스 스택 전송 요청**(ux_device_stack_transfer_request) |
| ![호스트 클래스 Asix 활성화 아이콘](./media/user-guide/usbx-events/image77.png)    | **호스트 클래스 Asix 활성화**(ux_host_class_asix_activate) |
| ![호스트 클래스 Asix 비활성화 아이콘](./media/user-guide/usbx-events/image78.png)    | **호스트 클래스 Asix 비활성화**(ux_host_class_asix_deactivate) |
| ![호스트 클래스 Asix 인터럽트 알림 아이콘](./media/user-guide/usbx-events/image79.png)    | **호스트 클래스 Asix 인터럽트 알림**(ux_host_class_asix_interrupt_notification) |
| ![호스트 클래스 Asix 읽기 아이콘](./media/user-guide/usbx-events/image80.png)    | **호스트 클래스 Asix 읽기**(ux_host_class_asix_read) |
| ![호스트 클래스 Asix 쓰기 아이콘](./media/user-guide/usbx-events/image81.png)    | **호스트 클래스 Asix 쓰기**(ux_host_class_asix_write) |
| ![호스트 클래스 오디오 활성화 아이콘](./media/user-guide/usbx-events/image82.png)    | **호스트 클래스 오디오 활성화**(ux_host_class_audio_activate) |
| ![호스트 클래스 오디오 컨트롤 값 가져오기 아이콘](./media/user-guide/usbx-events/image83.png)    | **호스트 클래스 오디오 컨트롤 값 가져오기**(ux_host_class_audio_control_value_get) |
| ![호스트 클래스 오디오 컨트롤 값 설정 아이콘](./media/user-guide/usbx-events/image84.png)    | **호스트 클래스 오디오 컨트롤 값 설정**(ux_host_class_audio_control_value_set) |
| ![호스트 클래스 오디오 비활성화 아이콘](./media/user-guide/usbx-events/image85.png)    | **호스트 클래스 오디오 비활성화**(ux_host_class_audio_deactivate) |
| ![호스트 클래스 오디오 읽기 아이콘](./media/user-guide/usbx-events/image86.png)    | **호스트 클래스 오디오 읽기**(ux_host_class_audio_read) |
| ![호스트 클래스 오디오 스트리밍 샘플링 가져오기 아이콘](./media/user-guide/usbx-events/image87.png)    | **호스트 클래스 오디오 스트리밍 샘플링 가져오기**(ux_host_class_audio_streaming_sampling_get) |
| ![호스트 클래스 오디오 스트리밍 샘플링 설정 아이콘](./media/user-guide/usbx-events/image88.png)    | **호스트 클래스 오디오 스트리밍 샘플링 설정**(ux_host_class_audio_streaming_sampling_set) |
| ![호스트 클래스 오디오 쓰기 아이콘](./media/user-guide/usbx-events/image89.png)    | **호스트 클래스 오디오 쓰기**(ux_host_class_audio_write) |
| ![호스트 클래스 CDC ACM 활성화 아이콘](./media/user-guide/usbx-events/image90.png)    | **호스트 클래스 Cdc Acm 활성화**(ux_host_class_cdc_acm_activate) |
| ![호스트 클래스 CDC ACM 비활성화 아이콘](./media/user-guide/usbx-events/image91.png)    | **호스트 클래스 Cdc Acm 비활성화**(ux_host_class_cdc_acm_deactivate) |
| ![호스트 클래스 CDC ACM IOCTL 파이프 내부 아이콘](./media/user-guide/usbx-events/image92.png)    | **호스트 클래스 Cdc Acm Ioctl 파이프에서 중단**(ux_host_class_cdc_acm_ioctl_abort_in_pipe) |
| ![호스트 클래스 Cdc Acm Ioctl 파이프 외부에서 중단 아이콘](./media/user-guide/usbx-events/image93.png)    | **호스트 클래스 Cdc Acm Ioctl 파이프 외부에서 중단**(ux_host_class_cdc_acm_ioctl_abort_out_pipe) |
| ![호스트 클래스 Cdc Acm Ioctl 디바이스 상태 가져오기 아이콘](./media/user-guide/usbx-events/image94.png)    | **호스트 클래스 Cdc Acm Ioctl 디바이스 상태 가져오기**(ux_host_class_cdc_acm_ioctl_get_device_status) |
| ![호스트 클래스 Cdc Acm Ioctl 줄 코드 가져오기 아이콘](./media/user-guide/usbx-events/image95.png)    | **호스트 클래스 Cdc Acm Ioctl 줄 코드 가져오기**(ux_host_class_cdc_acm_ioctl_get_line_coding) |
| ![호스트 클래스 Cdc Acm Ioctl 알림 콜백 아이콘](./media/user-guide/usbx-events/image96.png)    | **호스트 클래스 Cdc Acm Ioctl 알림 콜백**(ux_host_class_cdc_acm_ioctl_notification_callback) |
| ![호스트 클래스 Cdc Acm Ioctl 보내기 중단 아이콘](./media/user-guide/usbx-events/image97.png)    | **호스트 클래스 Cdc Acm Ioctl 보내기 중단**(ux_host_class_cdc_acm_ioctl_send_break) |
| ![호스트 클래스 Cdc Acm Ioctl 줄 코드 설정 아이콘](./media/user-guide/usbx-events/image98.png)    | **호스트 클래스 Cdc Acm Ioctl 줄 코드 설정**(ux_host_class_cdc_acm_ioctl_set_line_coding) |
| ![호스트 클래스 Cdc Acm Ioctl 줄 상태 설정 아이콘](./media/user-guide/usbx-events/image99.png)    | **호스트 클래스 Cdc Acm Ioctl 줄 상태 설정**(ux_host_class_cdc_acm_ioctl_set_line_state) |
| ![호스트 클래스 Cdc Acm 읽기 아이콘](./media/user-guide/usbx-events/image100.png)    | **호스트 클래스 Cdc Acm 읽기**(ux_host_class_cdc_acm_read) |
| ![호스트 클래스 Cdc Acm 수신 시작 아이콘](./media/user-guide/usbx-events/image101.png)    | **호스트 클래스 Cdc Acm 수신 시작**(ux_host_class_cdc_acm_reception_start) |
| ![호스트 클래스 Cdc Acm 수신 중지 아이콘](./media/user-guide/usbx-events/image102.png)    | **호스트 클래스 Cdc Acm 수신 중지**(ux_host_class_cdc_acm_reception_stop) |
| ![호스트 클래스 CDC ACM 쓰기 아이콘](./media/user-guide/usbx-events/image103.png)    | **호스트 클래스 Cdc Acm 쓰기**(ux_host_class_cdc_acm_write) |
| ![호스트 클래스 Dpump 활성화 아이콘](./media/user-guide/usbx-events/image104.png)    | **호스트 클래스 Dpump 활성화**(ux_host_class_dpump_activate) |
| ![호스트 클래스 Dpump 비활성화 아이콘](./media/user-guide/usbx-events/image105.png)    | **호스트 클래스 Dpump 비활성화**(ux_host_class_dpump_deactivate) |
| ![호스트 클래스 Dpump 읽기 아이콘](./media/user-guide/usbx-events/image106.png)    | **호스트 클래스 Dpump 읽기**(ux_host_class_dpump_read) |
| ![호스트 클래스 Dpump 쓰기 아이콘](./media/user-guide/usbx-events/image107.png)    | **호스트 클래스 Dpump 쓰기**(ux_host_class_dpump_write) |
| ![호스트 클래스 Hid 활성화 아이콘](./media/user-guide/usbx-events/image108.png)    | **호스트 클래스 Hid 활성화**(ux_host_class_hid_activate) |
| ![호스트 클래스 Hid 클라이언트 등록 아이콘](./media/user-guide/usbx-events/image109.png)    | **호스트 클래스 Hid 클라이언트 등록**(ux_host_class_hid_client_register) |
| ![호스트 클래스 Hid 비활성화 아이콘](./media/user-guide/usbx-events/image110.png)    | **호스트 클래스 Hid 비활성화**(ux_host_class_hid_deactivate) |
| ![호스트 클래스 Hid 유휴 가져오기 아이콘](./media/user-guide/usbx-events/image111.png)    | **호스트 클래스 Hid 유휴 가져오기**(ux_host_class_hid_idle_get) |
| ![호스트 클래스 Hid 유휴 설정 아이콘](./media/user-guide/usbx-events/image112.png)    | **호스트 클래스 Hid 유휴 설정**(ux_host_class_hid_idle_set) |
| ![호스트 클래스 Hid 키보드 활성화 아이콘](./media/user-guide/usbx-events/image113.png)    | **호스트 클래스 Hid 키보드 활성화**(ux_host_class_hid_keyboard_activate) |
| ![호스트 클래스 Hid 키보드 비활성화 아이콘](./media/user-guide/usbx-events/image114.png)    | **호스트 클래스 Hid 키보드 비활성화**(ux_host_class_hid_keyboard_deactivate) |
| ![호스트 클래스 Hid 마우스 활성화 아이콘](./media/user-guide/usbx-events/image115.png)    | **호스트 클래스 Hid 마우스 비활성화**(ux_host_class_hid_mouse_activate) |
| ![호스트 클래스 Hid 마우스 비활성화 아이콘](./media/user-guide/usbx-events/image116.png)    | **호스트 클래스 Hid 마우스 비활성화**(ux_host_class_hid_mouse_deactivate) |
| ![호스트 클래스 Hid 원격 제어 활성화 아이콘](./media/user-guide/usbx-events/image117.png)    | **호스트 클래스 Hid 원격 제어 활성화**(ux_host_class_hid_remote_control_activate) |
| ![호스트 클래스 Hid 원격 제어 비활성화 아이콘](./media/user-guide/usbx-events/image118.png)    | **호스트 클래스 Hid 원격 제어 비활성화**(ux_host_class_hid_remote_control_deactivate) |
| ![호스트 클래스 Hid 보고서 가져오기 아이콘](./media/user-guide/usbx-events/image119.png)    | **호스트 클래스 Hid 보고서 가져오기**(ux_host_class_hid_report_get) |
| ![호스트 클래스 Hid 보고서 설정 아이콘](./media/user-guide/usbx-events/image120.png)    | **호스트 클래스 Hid 보고서 설정**(ux_host_class_hid_report_set) |
| ![호스트 클래스 허브 활성화 아이콘](./media/user-guide/usbx-events/image121.png)    | **호스트 클래스 허브 활성화**(ux_host_class_hub_activate) |
| ![호스트 클래스 허브 변경 검색 아이콘](./media/user-guide/usbx-events/image122.png)    | **호스트 클래스 허브 변경 검색**(ux_host_class_hub_change_detect) |
| ![*호스트 클래스 허브 비활성화 아이콘](./media/user-guide/usbx-events/image123.png)    | **호스트 클래스 허브 비활성화**(ux_host_class_hub_deactivate) |
| ![호스트 클래스 허브 포트 연결 변경 프로세스 아이콘](./media/user-guide/usbx-events/image124.png)    | **호스트 클래스 허브 포트 연결 변경 프로세스**(ux_host_class_hub_port_change_connection_process) |
| ![호스트 클래스 허브 포트 변경 사용 프로세스 아이콘](./media/user-guide/usbx-events/image125.png)    | **호스트 클래스 허브 포트 변경 사용 프로세스**(ux_host_class_hub_port_change_enable_process) |
| ![호스트 클래스 허브 포트 전환 현재 프로세스 아이콘](./media/user-guide/usbx-events/image126.png)    | **호스트 클래스 허브 포트 전환 현재 프로세스**(ux_host_class_hub_port_change_over_current_process) |
| ![호스트 클래스 허브 포트 변경 제설정 프로세스 아이콘](./media/user-guide/usbx-events/image127.png)    | **호스트 클래스 허브 포트 변경 제설정 프로세스**(ux_host_class_hub_port_change_reset_process) |
| ![호스트 클래스 허브 포트 변경 일시 중단 프로세스 아이콘](./media/user-guide/usbx-events/image128.png)    | **호스트 클래스 허브 포트 변경 일시 중단 프로세스**(ux_host_class_hub_port_change_suspend_process) |
| ![호스트 클래스 Pima 활성화 아이콘](./media/user-guide/usbx-events/image129.png)    | **호스트 클래스 Pima 활성화**(ux_host_class_prima_activate) |
| ![호스트 클래스 Pima 비활성화 아이콘](./media/user-guide/usbx-events/image130.png)    | **호스트 클래스 Pima 비활성화**(ux_host_class_pima_deactivate) |
| ![호스트 클래스 Pima 디바이스 정보 가져오기 아이콘](./media/user-guide/usbx-events/image131.png)    | **호스트 클래스 Pima 디바이스 정보 가져오기**(ux_host_class_pima_device_info_get) |
| ![호스트 클래스 Pima 디바이스 재설정 아이콘](./media/user-guide/usbx-events/image132.png)    | **호스트 클래스 Pima 디바이스 재설정**(ux_host_class_pima_device_reset) |
| ![호스트 클래스 Pima 알림 아이콘](./media/user-guide/usbx-events/image133.png)    | **호스트 클래스 Pima 알림**(ux_host_class_pima_notification) |
| ![호스트 클래스 Pima 숫자 개체 가져오기 아이콘](./media/user-guide/usbx-events/image134.png)    | **호스트 클래스 Pima 숫자 개체 가져오기**(ux_host_class_pima_num_objects_get) |
| ![호스트 클래스 Pima 개체 닫기 아이콘](./media/user-guide/usbx-events/image135.png)    | **호스트 클래스 Pima 개체 닫기**(ux_host_class_pima_object_close) |
| ![호스트 클래스 Pima 개체 복사 아이콘](./media/user-guide/usbx-events/image136.png)    | **호스트 클래스 Pima 개체 복사**(ux_host_class_pima_object_copy) |
| ![호스트 클래스 Pima 개체 삭제 아이콘](./media/user-guide/usbx-events/image137.png)    | **호스트 클래스 Pima 개체 삭제**(ux_host_class_pima_object_delete) |
| ![호스트 클래스 Pima 개체 가져오기 아이콘](./media/user-guide/usbx-events/image138.png)    | **호스트 클래스 Pima 개체 가져오기**(ux_host_class_pima_object_get) |
| ![호스트 클래스 Pima 개체 정보 가져오기 아이콘](./media/user-guide/usbx-events/image139.png)    | **호스트 클래스 Pima 개체 정보 가져오기**(ux_host_class_pima_object_info_get) |
| ![호스트 클래스 Pima 개체 정보 보내기 아이콘](./media/user-guide/usbx-events/image140.png)    | **호스트 클래스 Pima 개체 정보 보내기**(ux_host_class_pima_object_info_send) |
| ![호스트 클래스 Pima 개체 이동 아이콘](./media/user-guide/usbx-events/image141.png)    | **호스트 클래스 Pima 개체 이동**(ux_host_class_pima_object_move) |
| ![호스트 클래스 Pima 개체 보내기 아이콘](./media/user-guide/usbx-events/image142.png)    | **호스트 클래스 Pima 개체 보내기**(ux_host_class_pima_object_send) |
| ![호스트 클래스 Pima 개체 전송 중단 아이콘](./media/user-guide/usbx-events/image143.png)    | **호스트 클래스 Pima 개체 전송 중단**(ux_host_class_object_transfer_abort) |
| ![호스트 클래스 Pima 읽기 아이콘](./media/user-guide/usbx-events/image144.png)    | **호스트 클래스 Pima 읽기**(ux_host_class_pima_read) |
| ![호스트 클래스 Pima 요청 취소 아이콘](./media/user-guide/usbx-events/image145.png)    | **호스트 클래스 Pima 요청 취소**(ux_host_class_pima_request_cancel) |
| ![호스트 클래스 Pima 세션 닫기 아이콘](./media/user-guide/usbx-events/image146.png)    | **호스트 클래스 Pima 세션 닫기**(ux_host_class_pima_session_close) |
| ![호스트 클래스 Pima 세션 열기 아이콘](./media/user-guide/usbx-events/image147.png)    | **호스트 클래스 Pima 세션 열기**(ux_host_class_pima_session_open) |
| ![호스트 클래스 Pima 스토리지 ID 가져오기 아이콘](./media/user-guide/usbx-events/image148.png)    | **호스트 클래스 Pima 스토리지 ID 가져오기**(ux_host_class_pima_storage_ids_get) |
| ![호스트 클래스 Pima 스토리지 가져오기 아이콘](./media/user-guide/usbx-events/image149.png)    | **호스트 클래스 Pima 스토리지 가져오기**(ux_host_class_pima_storage_info_get) |
| ![호스트 클래스 Pima Thumb 가져오기 아이콘](./media/user-guide/usbx-events/image150.png)    | **호스트 클래스 Pima Thumb 가져오기**(ux_host_class_pima_thumb_get) |
| ![호스트 클래스 Pima 쓰기 아이콘](./media/user-guide/usbx-events/image151.png)    | **호스트 클래스 Pima 쓰기**(ux_host_class_pima_write) |
| ![호스트 클래스 프린터 활성화 아이콘](./media/user-guide/usbx-events/image152.png)    | **호스트 클래스 프린터 활성화**(ux_host_class_printer_activate) |
| ![호스트 클래스 프린터 비활성화 아이콘](./media/user-guide/usbx-events/image153.png)    | **호스트 클래스 프린터 비활성화**(ux_host_class_printer_deactivate) |
| ![호스트 클래스 프린터 이름 가져오기 아이콘](./media/user-guide/usbx-events/image154.png)    | **호스트 클래스 프린터 이름 가져오기**(ux_host_class_printer_name_get) |
| ![호스트 클래스 프린터 읽기 아이콘](./media/user-guide/usbx-events/image155.png)    |  **호스트 클래스 프린터 읽기**(ux_host_class_printer_read) |
| ![호스트 클래스 프린터 소프트 리셋 아이콘](./media/user-guide/usbx-events/image156.png)    | **호스트 클래스 프린터 소프트 리셋**(ux_host_class_printer_soft_reset) |
| ![호스트 클래스 프린터 상태 가져오기 아이콘](./media/user-guide/usbx-events/image157.png)    | **호스트 클래스 프린터 상태 가져오기**(ux_host_class_printer_status_get) |
| ![호스트 클래스 프린터 쓰기 아이콘](./media/user-guide/usbx-events/image158.png)    | **호스트 클래스 프린터 쓰기**(ux_host_class_printer_write) |
| ![호스트 클래스 Prolific 활성화 아이콘](./media/user-guide/usbx-events/image159.png)    | **호스트 클래스 Prolific 활성화**(ux_host_class_prolific_activate) |
| ![호스트 클래스 Prolific 비활성화 아이콘](./media/user-guide/usbx-events/image160.png)    | **호스트 클래스 Prolific 비활성화**(ux_host_class_prolific_deactivate) |
| ![호스트 클래스 Prolific IOCTL 파이프에서 중단 아이콘](./media/user-guide/usbx-events/image161.png)    | **호스트 클래스 Prolific IOCTL 파이프에서 중단**(ux_host_class_prolific_ioctl_abort_in_pipe) |
| ![호스트 클래스 Prolific IOCTL 파이프 외부에서 중단 아이콘](./media/user-guide/usbx-events/image162.png)    | **호스트 클래스 Prolific IOCTL 파이프 외부에서 중단**(ux_host_class_prolific_ioctl_abort_out_pipe) |
| ![호스트 클래스 Prolific IOCTL 디바이스 상태 가져오기 아이콘](./media/user-guide/usbx-events/image163.png)    | **호스트 클래스 Prolific IOCTL 디바이스 상태 가져오기**(ux_host_class_prolific_ioctl_get_device_status) |
| ![호스트 클래스 Prolific Ioctl 줄 코드 가져오기 아이콘](./media/user-guide/usbx-events/image164.png)    | **호스트 클래스 Prolific Ioctl 줄 코드 가져오기**(ux_host_class_prolific_ioctl_get_line_coding) |
| ![호스트 클래스 Prolific Ioctl 제거 아이콘](./media/user-guide/usbx-events/image165.png)    | **호스트 클래스 Prolific Ioctl 제거**(ux_host_class_prolific_ioctl_purge) |
| ![호스트 클래스 Prolific IOCTL 보고서 디바이스 상태 변경 아이콘](./media/user-guide/usbx-events/image166.png)    | **호스트 클래스 Prolific IOCTL 보고서 디바이스 상태 변경**(ux_host_class_prolific_ioctl_report_device_status_change) |
| ![호스트 클래스 Prolific IOCTL 보내기 중단 아이콘](./media/user-guide/usbx-events/image167.png)    | **호스트 클래스 Prolific IOCTL 보내기 중단**(ux_host_class_prolific_ioctl_send_break) |
| ![호스트 클래스 Prolific Ioctl 줄 코드 설정 아이콘](./media/user-guide/usbx-events/image168.png)    | **호스트 클래스 Prolific Ioctl 줄 코드 설정**(ux_host_class_prolific_ioctl_set_line_coding) |
| ![호스트 클래스 Prolific Ioctl 줄 상태 설정 아이콘](./media/user-guide/usbx-events/image169.png)    | **호스트 클래스 Prolific Ioctl 줄 상태 설정**(ux_host_class_prolific_ioctl_set_line_state) |
| ![호스트 클래스 Prolific 읽기 아이콘](./media/user-guide/usbx-events/image170.png)    | **호스트 클래스 Prolific 읽기**(ux_host_class_prolific_read) |
| ![호스트 클래스 Prolific 수신 시작 아이콘](./media/user-guide/usbx-events/image171.png)    | **호스트 클래스 Prolific 수신 시작**(ux_host_class_prolific_reception_start) |
| ![호스트 클래스 Prolific 수신 중지 아이콘](./media/user-guide/usbx-events/image172.png)    | **호스트 클래스 Prolific 수신 중지**(ux_host_class_prolific_reception_stop) |
| ![호스트 클래스 Prolific 쓰기 아이콘](./media/user-guide/usbx-events/image173.png)    | **호스트 클래스 Prolific 쓰기**(ux_host_class_prolific_write) |
| ![호스트 클래스 스토리지 활성화 아이콘](./media/user-guide/usbx-events/image174.png)    | **호스트 클래스 스토리지 활성화**(ux_host_class_storage_activate) |
| ![호스트 클래스 스토리지 비활성화 아이콘](./media/user-guide/usbx-events/image175.png)    | **호스트 클래스 스토리지 비활성화**(ux_host_class_storage_deactivate) |
| ![호스트 클래스 스토리지 미디어 용량 가져오기 아이콘](./media/user-guide/usbx-events/image176.png)    | **호스트 클래스 스토리지 미디어 용량 가져오기**(ux_host_class_storage_media_capacity_get) |
| ![호스트 클래스 스토리지 미디어 형식 용량 가져오기 아이콘](./media/user-guide/usbx-events/image177.png)    | **호스트 클래스 스토리지 미디어 형식 용량 가져오기**(ux_host_class_storage_media_format_capacity_get) |
| ![호스트 클래스 스토리지 미디어 탑재 아이콘](./media/user-guide/usbx-events/image178.png)    | **호스트 클래스 스토리지 미디어 탑재**(ux_host_class_storage_media_mount)* |
| ![호스트 클래스 스토리지 미디어 열기 아이콘](./media/user-guide/usbx-events/image179.png)    | **호스트 클래스 스토리지 미디어 열기**(ux_host_class_storage_media_open) |
| ![호스트 클래스 스토리지 미디어 읽기 아이콘](./media/user-guide/usbx-events/image180.png)    | **호스트 클래스 스토리지 미디어 읽기**(ux_host_class_storage_media_read) |
| ![호스트 클래스 스토리지 미디어 쓰기 아이콘](./media/user-guide/usbx-events/image181.png)    | **호스트 클래스 스토리지 미디어 쓰기**(ux_host_class_storage_media_write) |
| ![호스트 클래스 스토리지 요청 센스 아이콘](./media/user-guide/usbx-events/image182.png)    | **호스트 클래스 스토리지 요청 센스**(ux_host_class_storage_request_sense) |
| ![호스트 클래스 스토리지 시작 중지 아이콘](./media/user-guide/usbx-events/image183.png)    | **호스트 클래스 스토리지 시작 중지**(ux_host_class_storage_start_stop) |
| ![호스트 클래스 스토리지 장치 준비 테스트 아이콘](./media/user-guide/usbx-events/image184.png)    | **호스트 클래스 스토리지 장치 준비 테스트**(ux_host_class_storage_activate) |
| ![호스트 스택 클래스 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image185.png)    | **호스트 스택 클래스 인스턴스 만들기**(ux_host_stack_class_instance_create) |
| ![호스트 스택 클래스 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image186.png)    | **호스트 스택 클래스 인스턴스 삭제**(ux_host_stack_class_instance_destroy) |
| ![호스트 스택 구성 삭제 아이콘](./media/user-guide/usbx-events/image187.png)    | **호스트 스택 구성 삭제**(ux_host_stack_configuration_delete) |
| ![호스트 스택 구성 열거 아이콘](./media/user-guide/usbx-events/image188.png)    | **호스트 스택 구성 열거**(ux_host_stack_configuration_enumerate) |
| ![호스트 스택 구성 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image189.png)    | **호스트 스택 구성 인스턴스 만들기**(ux_host_stack_configuration_instance_create) |
| ![호스트 스택 구성 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image190.png)    | **호스트 스택 구성 인스턴스 삭제**(ux_host_stack_configuration_instance_delete) |
| ![호스트 스택 구성 설정 아이콘](./media/user-guide/usbx-events/image191.png)    | **호스트 스택 구성 설정**(ux_host_stack_configuration_set) |
| ![호스트 스택 디바이스 주소 설정 아이콘](./media/user-guide/usbx-events/image192.png)    | **호스트 스택 디바이스 주소 설정**(ux_host_stack_device_set) |
| ![호스트 스택 디바이스 구성 가져오기 아이콘](./media/user-guide/usbx-events/image193.png)    | **호스트 스택 디바이스 구성 가져오기**(ux_host_stack_device_configuration_get) |
| ![호스트 스택 디바이스 구성 선택 아이콘](./media/user-guide/usbx-events/image194.png)    | **호스트 스택 디바이스 구성 선택**(ux_host_stack_device_configuration_select) |
| ![호스트 스택 디바이스 설명자 읽기 아이콘](./media/user-guide/usbx-events/image195.png)    | **호스트 스택 디바이스 설명자 읽기**(ux_host_stack_device_descriptor_read) |
| ![호스트 스택 디바이스 가져오기 아이콘](./media/user-guide/usbx-events/image196.png)    | **호스트 스택 디바이스 가져오기**(ux_host_stack_device_get) |
| ![호스트 스택 디바이스 제거 아이콘](./media/user-guide/usbx-events/image197.png)    | **호스트 스택 디바이스 제거**(ux_host_stack_device_get) |
| ![호스트 스택 디바이스 리소스 해제 아이콘](./media/user-guide/usbx-events/image198.png)    | **호스트 스택 디바이스 리소스 해제**(ux_host_stack_device_resource_free) |
| ![호스트 스택 엔드포인트 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image199.png)    | **호스트 스택 엔드포인트 인스턴스 만들기**(ux_host_stack_endpoint_instance_create) |
| ![호스트 스택 엔드포인트 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image200.png)    | **호스트 스택 엔드포인트 인스턴스 삭제**(ux_host_stack_endpoint_instance_delete) |
| ![호스트 스택 엔드포인트 재설정 아이콘](./media/user-guide/usbx-events/image201.png)    | **호스트 스택 엔드포인트 재설정**(ux_host_stack_endpoint_reset) |
| ![호스트 스택 엔드포인트 전송 중단 아이콘](./media/user-guide/usbx-events/image202.png)    | **호스트 스택 엔드포인트 전송 중단**(ux_host_stack_endpoint_transfer_abort) |
| ![호스트 스택 호스트 컨트롤러 등록 아이콘](./media/user-guide/usbx-events/image203.png)    | **호스트 스택 호스트 컨트롤러 등록**(ux_host_stack_hcd_register) |
| ![호스트 스택 초기화 아이콘](./media/user-guide/usbx-events/image204.png)    | **호스트 스택 초기화**(ux_host_stack_initialize) |
| ![호스트 스택 인터페이스 엔드포인트 가져오기 아이콘](./media/user-guide/usbx-events/image205.png)    | **호스트 스택 인터페이스 엔드포인트 가져오기**(ux_host_stack_interface_endpoint_get) |
| ![호스트 스택 인터페이스 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image206.png)    | **호스트 스택 인터페이스 인스턴스 만들기**(ux_host_stack_interface_instance_create) |
| ![호스트 스택 인터페이스 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image207.png)    | **호스트 스택 인터페이스 인스턴스 삭제**(ux_host_stack_interface_instance_delete) |
| ![호스트 스택 인터페이스 설정 아이콘](./media/user-guide/usbx-events/image208.png)    | **호스트 스택 인터페이스 설정**(ux_host_stack_interface_set) |
| ![호스트 스택 인터페이스 설정 선택 아이콘](./media/user-guide/usbx-events/image209.png)    | **호스트 스택 인터페이스 설정 선택**(ux_host_stack_interface_setting_select) |
| ![호스트 스택 새 구성 만들기 아이콘](./media/user-guide/usbx-events/image210.png)    | **호스트 스택 새 구성 만들기**(ux_host_stack_new_configuration_create) |
| ![호스트 스택 새 디바이스 만들기 아이콘](./media/user-guide/usbx-events/image211.png)    | **호스트 스택 새 디바이스 만들기**(ux_host_stack_new_device_create) |
| ![호스트 스택 새 엔드포인트 만들기 아이콘](./media/user-guide/usbx-events/image212.png)    | **호스트 스택 새 엔드포인트 만들기**(ux_host_stack_new_endpoint_create) |
| ![호스트 스택 루트 허브 변경 프로세스 아이콘](./media/user-guide/usbx-events/image213.png)    | **호스트 스택 루트 허브 변경 프로세스**(ux_host_stack_rh_change_process) |
| ![호스트 스택 루트 허브 디바이스 추출 아이콘](./media/user-guide/usbx-events/image214.png)    | **호스트 스택 루트 허브 디바이스 추출**(ux_host_stack_rh_device_extraction) |
| ![호스트 스택 루트 허브 디바이스 삽입 아이콘](./media/user-guide/usbx-events/image215.png)    | **호스트 스택 루트 허브 디바이스 삽입**(ux_host_stack_rh_device_insertion) |
| ![호스트 스택 전송 요청 아이콘](./media/user-guide/usbx-events/image216.png)    | **호스트 스택 전송 요청**(ux_host_stack_transfer_request) |
| ![호스트 스택 전송 요청 중단 아이콘](./media/user-guide/usbx-events/image217.png)    | **호스트 스택 전송 요청 중단**(ux_host_stack_transfer_request_abort) |
| ![U S B X 오류 아이콘](./media/user-guide/usbx-events/image218.png)    | **USBX 오류**(ux_error) |

## <a name="event-descriptions"></a>이벤트 설명

다음 페이지에서는 USBX 추적 이벤트에 대해 설명합니다.

### <a name="device-class-cdc-activate"></a>디바이스 클래스 Cdc 활성화 

#### <a name="ux_device_class_cdc_activate"></a>ux_device_class_cdc_activate

**아이콘** ![디바이스 클래스 C D C 활성화 아이콘](./media/user-guide/usbx-events/image1.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Cdc 활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-cdc-deactivate"></a>디바이스 클래스 Cdc 비활성화 

#### <a name="ux_device_class_cdc_deactivate"></a>ux_device_class_cdc_deactivate

**아이콘** ![디바이스 클래스 C D C 비활성화 아이콘](./media/user-guide/usbx-events/image2.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Cdc 비활성화를 나타냅니다.

정보 필드 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-cdc-read"></a>디바이스 클래스 Cdc 읽기 

#### <a name="ux_device_class_cdc_read"></a>ux_device_class_cdc_read

**아이콘** ![디바이스 클래스 C D C 읽기 아이콘](./media/user-guide/usbx-events/image3.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Cdc 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-cdc-write"></a>디바이스 클래스 Cdc 쓰기 

#### <a name="ux_device_class_cdc_write"></a>ux_device_class_cdc_write

**아이콘** ![디바이스 클래스 C D C 쓰기 아이콘](./media/user-guide/usbx-events/image4.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Cdc 쓰기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-dpump-activate"></a>디바이스 클래스 Dpump 활성화 

#### <a name="ux_device_class_dpump_activate"></a>ux_device_class_dpump_activate

**아이콘**![디바이스 클래스 Dpump 활성화 아이콘](./media/user-guide/usbx-events/image5.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Dpump 활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-dpump-deactivate"></a>디바이스 클래스 Dpump 비활성화 

#### <a name="ux_device_class_dpump_deactivate"></a>ux_device_class_dpump_deactivate

**아이콘** ![디바이스 클래스 Dpump 비활성화 아이콘](./media/user-guide/usbx-events/image6.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Dpump 비활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-dpump-read"></a>디바이스 클래스 Dpump 읽기 

#### <a name="ux_device_class_dpump_read"></a>ux_device_class_dpump_read

**아이콘** ![디바이스 클래스 Dpump 읽기 아이콘](./media/user-guide/usbx-events/image7.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Dpump 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 버퍼
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-dpump-write"></a>디바이스 클래스 Dpump 쓰기 

#### <a name="ux_device_class_dpump_write"></a>ux_device_class_dpump_write

**아이콘** ![디바이스 클래스 Dpump 쓰기 아이콘](./media/user-guide/usbx-events/image8.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Dpump 쓰기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-hid-activate"></a>디바이스 클래스 Hid 활성화 

#### <a name="ux_device_class_hid_activate"></a>ux_device_class_hid_activate

**아이콘** ![디바이스 클래스 Hid 활성화 아이콘](./media/user-guide/usbx-events/image9.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Hid 활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-hid-deactivate"></a>디바이스 클래스 Hid 비활성화 

#### <a name="ux_device_class_hid_deactivate"></a>ux_device_class_hid_deactivate

**아이콘** ![디바이스 클래스 Hid 비활성화 아이콘](./media/user-guide/usbx-events/image10.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Hid 비활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-hid-descriptor-send"></a>디바이스 클래스 Hid 설명자 보내기 

#### <a name="ux_device_class_hid_descritpor_send"></a>ux_device_class_hid_descritpor_send

**아이콘** ![디바이스 클래스 Hid 설명자 보내기 아이콘](./media/user-guide/usbx-events/image11.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Hid 설명자 보내기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 설명자 유형
- 정보 필드 3: 요청 인덱스
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-hid-event-get"></a>디바이스 클래스 Hid 이벤트 가져오기 

#### <a name="ux_device_class_hid_event_get"></a>ux_device_class_hid_event_get

**아이콘** ![디바이스 클래스 Hid 이벤트 가져오기 아이콘](./media/user-guide/usbx-events/image12.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Hid 이벤트 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-hid-event-set"></a>디바이스 클래스 Hid 이벤트 설정 

#### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

**아이콘** ![디바이스 클래스 Hid 이벤트 설정 아이콘](./media/user-guide/usbx-events/image13.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Hid 이벤트 설정을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-hid-report-get"></a>디바이스 클래스 Hid 보고서 가져오기 

#### <a name="ux_device_class_hid_report_get"></a>ux_device_class_hid_report_get

**아이콘** ![디바이스 클래스 Hid 보고서 가져오기 아이콘](./media/user-guide/usbx-events/image14.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Hid 보고서 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 설명자 유형
- 정보 필드 3: 요청 인덱스
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-hid-report-set"></a>디바이스 클래스 Hid 보고서 설정 

#### <a name="ux_device_class_hid_report_set"></a>ux_device_class_hid_report_set

**아이콘** ![디바이스 클래스 Hid 보고서 설정 아이콘](./media/user-guide/usbx-events/image15.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Hid 보고서 설정 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 설명자 유형
- 정보 필드 3: 요청 인덱스
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-pima-activate"></a>디바이스 클래스 Pima 활성화

#### <a name="ux_device_class_pima_activate"></a>ux_device_class_pima_activate

**아이콘** ![디바이스 클래스 Pima 활성화 아이콘](./media/user-guide/usbx-events/image16.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-pima-deactivate"></a>디바이스 클래스 Pima 비활성화 

#### <a name="ux_device_class_pima_deactivate"></a>ux_device_class_pima_deactivate

**아이콘** ![디바이스 클래스 Pima 비활성화 아이콘](./media/user-guide/usbx-events/image17.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 비활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-pima-device-info-send"></a>디바이스 클래스 Pima 디바이스 정보 보내기 

#### <a name="ux_device_class_pima_device_info_send"></a>ux_device_class_pima_device_info_send

**아이콘** ![디바이스 클래스 Pima 디바이스 정보 보내기 아이콘](./media/user-guide/usbx-events/image18.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 디바이스 정보 보내기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.

### <a name="device-class-pima-event-get"></a>디바이스 클래스 Pima 이벤트 가져오기 

#### <a name="ux_device_class_pima_event_get"></a>ux_device_class_pima_event_get

**아이콘** ![디바이스 클래스 Pima 이벤트 가져오기 아이콘](./media/user-guide/usbx-events/image19.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 이벤트 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Pima 이벤트
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-pima-event-set"></a>디바이스 클래스 Pima 이벤트 설정 

#### <a name="ux_device_class_pima_event_set"></a>ux_device_class_pima_event_set

**아이콘** ![디바이스 클래스 Pima 이벤트 설정 아이콘](./media/user-guide/usbx-events/image20.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 이벤트 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Pima 이벤트
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-pima-object-add"></a>디바이스 클래스 Pima 개체 추가 

#### <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

**아이콘** ![디바이스 클래스 Pima 개체 추가 아이콘](./media/user-guide/usbx-events/image21.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 개체 추가 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-pima-object-data-get"></a>디바이스 클래스 Pima 개체 데이터 가져오기 

#### <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

**아이콘** ![디바이스 클래스 Pima 개체 데이터 가져오기 아이콘](./media/user-guide/usbx-events/image22.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 개체 데이터 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-pima-object-data-send"></a>디바이스 클래스 Pima 개체 데이터 보내기 

#### <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

**아이콘** ![디바이스 클래스 Pima 개체 데이터 보내기 아이콘](./media/user-guide/usbx-events/image23.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 개체 데이터 보내기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-pima-object-delete"></a>디바이스 클래스 Pima 개체 삭제 

#### <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

**아이콘** ![디바이스 클래스 Pima 개체 삭제 아이콘](./media/user-guide/usbx-events/image24.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 개체 삭제 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-pima-object-handles-send"></a>디바이스 클래스 Pima 개체 핸들 보내기 

#### <a name="ux_device_class_pima_object_handles_send"></a>ux_device_class_pima_object_handles_send

**아이콘** ![디바이스 클래스 Pima 개체 핸들 보내기 아이콘](./media/user-guide/usbx-events/image25.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 개체 핸들 보내기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 스토리지 ID
- 정보 필드 3: 개체 형식 코드
- 정보 필드 4: 개체 연결

### <a name="device-class-pima-object-info-get"></a>디바이스 클래스 Pima 개체 정보 가져오기 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**아이콘** ![디바이스 클래스 Pima 개체 정보 가져오기 아이콘](./media/user-guide/usbx-events/image26.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 개체 정보 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-pima-object-info-send"></a>디바이스 클래스 Pima 개체 정보 보내기 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**아이콘** ![디바이스 클래스 Pima 개체 정보 보내기 아이콘](./media/user-guide/usbx-events/image27.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 개체 정보 보내기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-pima-objects-number-send"></a>디바이스 클래스 Pima 개체 번호 보내기 

#### <a name="ux_device_class_pima_object_number_send"></a>ux_device_class_pima_object_number_send

**아이콘** ![디바이스 클래스 Pima 개체 번호 보내기 아이콘](./media/user-guide/usbx-events/image28.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 개체 번호 보내기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 스토리지 ID
- 정보 필드 3: 개체 형식 코드
- 정보 필드 4: 개체 연결

### <a name="device-class-pima-partial-object-data-get"></a>디바이스 클래스 Pima 부분 개체 데이터 가져오기

#### <a name="ux_device_class_pima_partial_object_data_get"></a>ux_device_class_pima_partial_object_data_get

**아이콘** ![디바이스 클래스 Pima 부분 개체 데이터 가져오기 아이콘](./media/user-guide/usbx-events/image29.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 부분 개체 데이터 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 오프셋이 요청되었습니다.
- 정보 필드 4: 길이가 요청되었습니다.

### <a name="device-class-pima-response-send"></a>디바이스 클래스 Pima 응답 보내기 

#### <a name="ux_device_class_pima_response_send"></a>ux_device_class_pima_response_send

**아이콘** ![디바이스 클래스 Pima 응답 보내기 아이콘](./media/user-guide/usbx-events/image30.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 응답 보내기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 응답 코드
- 정보 필드 3: 숫자 매개 변수
- 정보 필드 4: Pima 매개 변수 1

### <a name="device-class-pima-storage-id-send"></a>디바이스 클래스 Pima 스토리지 ID 보내기 

#### <a name="ux_device_class_pima_storage_id_send"></a>ux_device_class_pima_storage_id_send

**아이콘** ![디바이스 클래스 Pima 스토리지 ID 보내기 아이콘](./media/user-guide/usbx-events/image31.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 스토리지 ID 보내기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-pima-storage-info-send"></a>디바이스 클래스 Pima 스토리지 정보 보내기 

#### <a name="ux_device_class_pima_storage_info_send"></a>ux_device_class_pima_storage_info_send

**아이콘** ![디바이스 클래스 Pima 스토리지 정보 보내기 아이콘](./media/user-guide/usbx-events/image32.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Pima 스토리지 정보 보내기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-rndis-activate"></a>디바이스 클래스 Rndis 활성화 

#### <a name="ux_device_class_rndis_activate"></a>ux_device_class_rndis_activate

**아이콘** ![디바이스 클래스 Rndis 활성화 아이콘](./media/user-guide/usbx-events/image33.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Rndis 활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-rndis-deactivate"></a>디바이스 클래스 Rndis 비활성화 

#### <a name="ux_device_class_rndis_deactivate"></a>ux_device_class_rndis_deactivate

**아이콘** ![디바이스 클래스 Rndis 비활성화 아이콘](./media/user-guide/usbx-events/image34.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Rndis 비활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-rndis-message-keep-alive"></a>디바이스 클래스 Rndis 메시지 연결 유지 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a>ux_device_class_rndis_msg_keep_alive

**아이콘** ![디바이스 클래스 Rndis 메시지 연결 유지 아이콘](./media/user-guide/usbx-events/image35.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Rndis 메시지 연결 유지 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-rndis-message-query"></a>디바이스 클래스 Rndis 메시지 쿼리 

#### <a name="ux_device_class_rndis_msg_keep_query"></a>ux_device_class_rndis_msg_keep_query

**아이콘** ![디바이스 클래스 Rndis 메시지 쿼리 아이콘](./media/user-guide/usbx-events/image36.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Rndis 메시지 쿼리 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Rndis OID
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-rndis-message-reset"></a>디바이스 클래스 Rndis 메시지 재설정 

#### <a name="ux_device_class_rndis_msg_reset"></a>ux_device_class_rndis_msg_reset

**아이콘** ![디바이스 클래스 Rndis 메시지 재설정 아이콘](./media/user-guide/usbx-events/image37.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Rndis 메시지 재설정 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.

### <a name="device-class-rndis-message-set"></a>디바이스 클래스 Rndis 메시지 설정 

#### <a name="ux_device_class_rndis_msg_set"></a>ux_device_class_rndis_msg_set

**아이콘** ![디바이스 클래스 Rndis 메시지 설정 아이콘](./media/user-guide/usbx-events/image38.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Rndis 메시지 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Rndis OID
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-rndis-packet-receive"></a>디바이스 클래스 Rndis 패킷 수신 

#### <a name="ux_device_class_rndis_packet_receive"></a>ux_device_class_rndis_packet_receive

**아이콘** ![디바이스 클래스 Rndis 패킷 수신 아이콘](./media/user-guide/usbx-events/image39.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Rndis 패킷 수신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-rndis-packet-transmit"></a>디바이스 클래스 Rndis 패킷 전송 

#### <a name="ux_device_class_rndis_packet_transmit"></a>ux_device_class_rndis_packet_transmit

**아이콘** ![디바이스 클래스 Rndis 패킷 전송 아이콘](./media/user-guide/usbx-events/image40.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Rndis 패킷 전송 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-activate"></a>디바이스 클래스 스토리지 활성화 

#### <a name="ux_device_class_storage_activate"></a>ux_device_class_storage_activate

**아이콘** ![디바이스 클래스 스토리지 활성화 아이콘](./media/user-guide/usbx-events/image41.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-deactivate"></a>디바이스 클래스 스토리지 비활성화 

#### <a name="ux_device_class_storage_deactivate"></a>ux_device_class_storage_deactivate

**아이콘** ![디바이스 클래스 스토리지 비활성화 아이콘](./media/user-guide/usbx-events/image42.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 Rndis 비활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-format"></a>디바이스 클래스 스토리지 형식 

#### <a name="ux_device_class_storage_format"></a>ux_device_class_storage_format

**아이콘** ![디바이스 클래스 스토리지 형식 아이콘](./media/user-guide/usbx-events/image43.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 형식 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-inquiry"></a>디바이스 클래스 스토리지 조회 

#### <a name="ux_device_class_storage_inquiry"></a>ux_device_class_storage_inquiry

**아이콘** ![디바이스 클래스 스토리지 조회 아이콘](./media/user-guide/usbx-events/image44.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 조회 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-mode-select"></a>디바이스 클래스 스토리지 모드 선택

#### <a name="ux_device_class_storage_mode_select"></a>ux_device_class_storage_mode_select

**아이콘** ![디바이스 클래스 스토리지 모드 선택 아이콘](./media/user-guide/usbx-events/image45.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 모드 선택 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-mode-sense"></a>디바이스 클래스 스토리지 모드 센스 

#### <a name="ux_device_class_storage_mode_sense"></a>ux_device_class_storage_mode_sense

**아이콘** ![디바이스 클래스 스토리지 모드 센스 아이콘](./media/user-guide/usbx-events/image46.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 모드 센스 이벤트를 나타냅니다.

정보 필드 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-prevent-allow-media-removal"></a>디바이스 클래스 스토리지의 미디어 제거 방지 허용 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a>ux_device_class_storage_prevent_allow_media_removal

**아이콘** ![디바이스 클래스 스토리지의 미디어 제거 방지 허용 아이콘](./media/user-guide/usbx-events/image47.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 미디어 제거 방지 허용 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-read"></a>디바이스 클래스 스토리지 읽기 

#### <a name="ux_device_class_storage_read"></a>ux_device_class_storage_read

**아이콘** ![디바이스 클래스 스토리지 읽기 아이콘](./media/user-guide/usbx-events/image48.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 섹터
- 정보 필드 4: 섹터 수

### <a name="device-class-storage-read-capacity"></a>디바이스 클래스 스토리지 읽기 용량 

#### <a name="ux_device_class_storage_read_capacity"></a>ux_device_class_storage_read_capacity

**아이콘** ![디바이스 클래스 스토리지 읽기 용량 아이콘](./media/user-guide/usbx-events/image49.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 읽기 용량 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-read-format-capacity"></a>디바이스 클래스 스토리지 읽기 형식 용량 

#### <a name="ux_device_class_storage_read_format_capacity"></a>ux_device_class_storage_read_format_capacity

**아이콘** ![디바이스 클래스 스토리지 읽기 형식 용량 아이콘](./media/user-guide/usbx-events/image50.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 읽기 형식 용량 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-read-toc"></a>디바이스 클래스 스토리지 읽기 TOC 

#### <a name="ux_device_class_storage_read_toc"></a>ux_device_class_storage_read_toc

**아이콘** ![디바이스 클래스 스토리지 읽기 TOC 아이콘](./media/user-guide/usbx-events/image51.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 읽기 TOC 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-request-sense"></a>디바이스 클래스 스토리지 요청 센스 

#### <a name="ux_device_class_storage_request_sense"></a>ux_device_class_storage_request_sense

**아이콘** ![디바이스 클래스 스토리지 요청 센스 아이콘](./media/user-guide/usbx-events/image52.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 요청 센스 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 센스 키
- 정보 필드 4: 코드

### <a name="device-class-storage-start-stop"></a>디바이스 클래스 스토리지 시작 중지 

#### <a name="ux_device_class_storage_start_stop"></a>ux_device_class_storage_start_stop

**아이콘** ![디바이스 클래스 스토리지 시작 중지 아이콘](./media/user-guide/usbx-events/image53.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 시작 중지 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-test-ready"></a>디바이스 클래스 스토리지 테스트 준비 

#### <a name="ux_device_class_storage_test_ready"></a>ux_device_class_storage_test_ready

**아이콘** ![디바이스 클래스 스토리지 테스트 준비 아이콘](./media/user-guide/usbx-events/image54.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 테스트 준비 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-verify"></a>디바이스 클래스 스토리지 확인 

#### <a name="ux_device_class_storage_verify"></a>ux_device_class_storage_verify

**아이콘** ![디바이스 클래스 스토리지 확인 아이콘](./media/user-guide/usbx-events/image55.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 확인 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-class-storage-write"></a>디바이스 클래스 스토리지 쓰기 

#### <a name="ux_device_class_storage_write"></a>ux_device_class_storage_write

**아이콘** ![디바이스 클래스 스토리지 쓰기 아이콘](./media/user-guide/usbx-events/image56.png)

**설명**

이 이벤트는 USBX 디바이스 클래스 스토리지 쓰기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Lun
- 정보 필드 3: 섹터
- 정보 필드 4: 섹터 수

### <a name="device-stack-alternate-setting-get"></a>디바이스 스택 대체 설정 가져오기 

#### <a name="ux_device_class_alternate_setting_get"></a>ux_device_class_alternate_setting_get

**아이콘** ![디바이스 스택 대체 설정 가져오기 아이콘](./media/user-guide/usbx-events/image57.png)

**설명**

이 이벤트는 USBX 디바이스 스택 대체 설정 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 인터페이스 값
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-alternate-setting-set"></a>디바이스 스택 대체 설정 설정 

#### <a name="ux_device_class_alternate_setting_set"></a>ux_device_class_alternate_setting_set

**아이콘** ![디바이스 스택 대체 설정 설정 아이콘](./media/user-guide/usbx-events/image58.png)

**설명**

이 이벤트는 USBX 디바이스 스택 대체 설정 설정 이벤트를 나타냅니다.

**정보 필드**
- 정보 필드 1: 인터페이스 값
- 정보 필드 2: 대체 설정 값
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-class-register"></a>디바이스 스택 클래스 등록 

#### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

**아이콘** ![디바이스 스택 클래스 등록 아이콘](./media/user-guide/usbx-events/image59.png)

**설명**

이 이벤트는 USBX 디바이스 스택 클래스 등록 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 이름
- 정보 필드 2: 인터페이스 번호
- 정보 필드 3: 매개 변수
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-clear-feature"></a>디바이스 스택 지우기 기능 

#### <a name="ux_device_stack_clear_feature"></a>ux_device_stack_clear_feature

**아이콘** ![디바이스 스택 지우기 기능 아이콘](./media/user-guide/usbx-events/image60.png)

**설명**

이 이벤트는 USBX 디바이스 스택 지우기 기능 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 요청 유형
- 정보 필드 2: 요청 값 정보 필드 3: 요청 인덱스
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-configuration-get"></a>디바이스 스택 구성 가져오기 

#### <a name="ux_device_stack_configuration_get-t"></a>ux_device_stack_configuration_get t

**아이콘** ![디바이스 스택 구성 가져오기 아이콘](./media/user-guide/usbx-events/image61.png)

**설명**

이 이벤트는 USBX 디바이스 스택 구성 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 구성 값
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-configuration-set"></a>디바이스 스택 구성 설정 

#### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

**아이콘** ![디바이스 스택 구성 설정 아이콘](./media/user-guide/usbx-events/image62.png)

**설명**

이 이벤트는 USBX 디바이스 스택 구성 설정 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 구성 값
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-connect"></a>디바이스 스택 연결 

#### <a name="ux_device_stack_connect"></a>ux_device_stack_connect

**아이콘** ![디바이스 스택 연결 아이콘](./media/user-guide/usbx-events/image63.png)

**설명**

이 이벤트는 USBX 디바이스 스택 설명자 보내기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-descriptor-send"></a>디바이스 스택 설명자 보내기 

#### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

**아이콘** ![디바이스 스택 설명자 보내기 아이콘](./media/user-guide/usbx-events/image64.png)

**설명**

이 이벤트는 USBX 디바이스 스택 설명자 보내기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 설명자 유형
- 정보 필드 2: 요청 인덱스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-disconnect"></a>디바이스 스택 연결 끊기 

#### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

**아이콘** ![디바이스 스택 연결 끊기 아이콘](./media/user-guide/usbx-events/image65.png)

**설명**

이 이벤트는 USBX 디바이스 스택 연결 끊기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-endpoint-stall"></a>디바이스 스택 엔드포인트 정지 

#### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

**아이콘** ![디바이스 스택 엔드포인트 정지 아이콘](./media/user-guide/usbx-events/image66.png)

**설명**

이 이벤트는 USBX 디바이스 스택 엔드포인트 정지 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 엔드포인트
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-get-status"></a>디바이스 스택 상태 가져오기 

#### <a name="ux_device_stack_get_status"></a>ux_device_stack_get_status

**아이콘** ![디바이스 스택 상태 가져오기 아이콘](./media/user-guide/usbx-events/image67.png)

**설명**

이 이벤트는 USBX 디바이스 스택 상태 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-host-wakeup"></a>디바이스 스택 호스트 절전 모드 해제 

#### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

**아이콘** ![디바이스 스택 호스트 절전 모드 해제 아이콘](./media/user-guide/usbx-events/image68.png)

**설명**

이 이벤트는 USBX 디바이스 스택 호스트 절전 모드 해제 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-initialize"></a>디바이스 스택 초기화 

#### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

**아이콘** ![디바이스 스택 초기화 아이콘](./media/user-guide/usbx-events/image69.png)

**설명**

이 이벤트는 USBX 디바이스 스택 초기화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-interface-delete"></a>디바이스 스택 인터페이스 삭제 

#### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

**아이콘** ![디바이스 스택 인터페이스 삭제 아이콘](./media/user-guide/usbx-events/image70.png)

**설명**

이 이벤트는 USBX 디바이스 스택 인터페이스 삭제 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 인터페이스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-interface-get"></a>디바이스 스택 인터페이스 가져오기 

#### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

**아이콘** ![디바이스 스택 인터페이스 가져오기 아이콘](./media/user-guide/usbx-events/image71.png)

**설명**

이 이벤트는 USBX 디바이스 스택 인터페이스 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 인터페이스 값
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-interface-set"></a>디바이스 스택 인터페이스 설정 

#### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

**아이콘** ![디바이스 스택 인터페이스 설정 아이콘](./media/user-guide/usbx-events/image72.png)

**설명**

이 이벤트는 USBX 디바이스 스택 인터페이스 설정 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 요청 값 정보 필드 2: 요청 인덱스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-set-feature"></a>디바이스 스택 설정 기능 

#### <a name="ux_device_stack_set_feature"></a>ux_device_stack_set_feature

**아이콘** ![디바이스 스택 설정 기능 아이콘](./media/user-guide/usbx-events/image73.png)

**설명**

이 이벤트는 USBX 디바이스 스택 설정 기능 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 요청 값 정보 필드 2: 요청 인덱스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-transfer-abort"></a>디바이스 스택 전송 중단 

#### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

**아이콘** ![디바이스 스택 전송 중단 아이콘](./media/user-guide/usbx-events/image74.png)

**설명**

이 이벤트는 USBX 디바이스 스택 전송 중단 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 전송 요청
- 정보 필드 2: 완료 코드
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-transfer-all-request-abort"></a>디바이스 스택 전송 모든 요청 중단 

#### <a name="ux_device_stack_transfer_all_request_abort"></a>ux_device_stack_transfer_all_request_abort

**아이콘** ![디바이스 스택 전송 모든 요청 중단 아이콘](./media/user-guide/usbx-events/image75.png)

**설명**

이 이벤트는 USBX 디바이스 스택 전송 모든 요청 중단 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 엔드포인트
- 정보 필드 2: 완료 코드
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="device-stack-transfer-request"></a>디바이스 스택 전송 요청 

#### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

**아이콘** ![디바이스 스택 전송 요청 아이콘](./media/user-guide/usbx-events/image76.png)

**설명**

이 이벤트는 USBX 디바이스 스택 전송 요청 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 전송 요청
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-asix-activate"></a>호스트 클래스 Asix 활성화 

#### <a name="ux_host_class_asix_activate"></a>ux_host_class_asix_activate

**아이콘** ![호스트 클래스 Asix 활성화 아이콘](./media/user-guide/usbx-events/image77.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Asix 활성화를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-asix-deactivate"></a>호스트 클래스 Asix 비활성화 

#### <a name="ux_host_class_asix_deactivate"></a>ux_host_class_asix_deactivate

**아이콘** ![호스트 클래스 Asix 비활성화 아이콘](./media/user-guide/usbx-events/image78.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Asix 비활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-asix-interrupt-notification"></a>호스트 클래스 Asix 인터럽트 알림 

#### <a name="ux_host_class_asix_interrupt_notification"></a>ux_host_class_asix_interrupt_notification

**아이콘** ![호스트 클래스 Asix 인터럽트 알림 아이콘](./media/user-guide/usbx-events/image79.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Asix 인터럽트 알림 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-asix-read"></a>호스트 클래스 Asix 읽기 

#### <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

**아이콘** ![호스트 클래스 Asix 읽기 아이콘](./media/user-guide/usbx-events/image80.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Asix 읽기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-asix-write"></a>호스트 클래스 Asix 쓰기 

#### <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

**아이콘** ![호스트 클래스 Asix 쓰기 아이콘](./media/user-guide/usbx-events/image81.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Asix 쓰기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-audio-activate"></a>호스트 클래스 오디오 활성화 

#### <a name="ux_host_class_audio_activate"></a>ux_host_class_audio_activate

**아이콘** ![호스트 클래스 오디오 활성화 아이콘](./media/user-guide/usbx-events/image82.png)

**설명**

이 이벤트는 USBX 호스트 클래스 오디오 활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-audio-control-value-get"></a>호스트 클래스 오디오 컨트롤 값 가져오기 

#### <a name="ux_host_class_audio_control_value_get"></a>ux_host_class_audio_control_value_get

**아이콘** ![호스트 클래스 오디오 컨트롤 값 가져오기 아이콘](./media/user-guide/usbx-events/image83.png)

**설명**

이 이벤트는 USBX 호스트 클래스 오디오 컨트롤 값 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-audio-control-value-set"></a>호스트 클래스 오디오 컨트롤 값 설정 

#### <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

**아이콘** ![호스트 클래스 오디오 컨트롤 값 설정 아이콘](./media/user-guide/usbx-events/image84.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 지연 처리 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 오디오 컨트롤
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-audio-deactivate"></a>호스트 클래스 오디오 비활성화 

#### <a name="ux_host_class_audio_deactivate"></a>ux_host_class_audio_deactivate

**아이콘** ![호스트 클래스 오디오 비활성화 아이콘](./media/user-guide/usbx-events/image85.png)

**설명**

이 이벤트는 USBX 호스트 클래스 오디오 비활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-audio-read"></a>호스트 클래스 오디오 읽기 

#### <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

**아이콘** ![호스트 클래스 오디오 읽기 아이콘](./media/user-guide/usbx-events/image86.png)

**설명**

이 이벤트는 USBX 호스트 클래스 오디오 읽기 이벤트를 나타냅니다.

- 정보 필드 
- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-audio-streaming-sampling-get"></a>호스트 클래스 오디오 스트리밍 샘플링 가져오기 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

**아이콘** ![호스트 클래스 오디오 스트리밍 샘플링 가져오기 아이콘](./media/user-guide/usbx-events/image87.png)

**설명**

이 이벤트는 USBX 호스트 클래스 오디오 스트리밍 샘플링 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-audio-streaming-sampling-set"></a>호스트 클래스 오디오 스트리밍 샘플링 설정 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

**아이콘** ![호스트 클래스 오디오 스트리밍 샘플링 설정 아이콘](./media/user-guide/usbx-events/image88.png)

**설명**

이 이벤트는 USBX 호스트 클래스 오디오 스트리밍 샘플링 설정 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 오디오 샘플링
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-audio-write"></a>호스트 클래스 오디오 쓰기 

#### <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

**아이콘** ![호스트 클래스 오디오 쓰기 아이콘](./media/user-guide/usbx-events/image89.png)

**설명**

이 이벤트는 USBX 호스트 클래스 오디오 쓰기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-activate"></a>호스트 클래스 Cdc Acm 활성화 

#### <a name="ux_host_class_cdc_acm_activate"></a>ux_host_class_cdc_acm_activate

**아이콘** ![호스트 클래스 Cdc Acm 활성화 아이콘](./media/user-guide/usbx-events/image90.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm 활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-deactivate"></a>호스트 클래스 Cdc Acm 비활성화 

#### <a name="ux_host_class_cdc_acm_deactivate"></a>ux_host_class_cdc_acm_deactivate

**아이콘** ![호스트 클래스 Cdc Acm 비활성화 아이콘](./media/user-guide/usbx-events/image91.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm 비활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a>호스트 클래스 Cdc Acm Ioctl 파이프에서 중단 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a>ux_host_class_cdc_acm_ioctl_abort_in_pipe

**아이콘** ![호스트 클래스 Cdc Acm Ioctl 파이프에서 중단 아이콘](./media/user-guide/usbx-events/image92.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 파이프에서 중단 이벤트를 나타냅니다.

정보 필드 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 엔드포인트
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a>호스트 클래스 Cdc Acm Ioctl 파이프 외부에서 중단 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a>ux_host_class_cdc_acm_ioct_abort_out_pipe

**아이콘** ![[호스트 클래스 Cdc Acm Ioctl 파이프 외부에서 중단 아이콘](./media/user-guide/usbx-events/image93.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 파이프 외부에서 중단 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 엔드포인트
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a>호스트 클래스 Cdc Acm Ioctl 디바이스 상태 가져오기 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a>ux_host_class_cdc_acm_ioctl_get_device_status

**아이콘** ![호스트 클래스 Cdc Acm Ioctl 디바이스 상태 가져오기 아이콘](./media/user-guide/usbx-events/image94.png)

**설명**

이 이벤트는 c # 호스트 클래스 Cdc Acm Ioctl 디바이스 상태 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 디바이스 상태
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a>호스트 클래스 Cdc Acm Ioctl 줄 코드 가져오기 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a>ux_host_class_cdc_acm_ioctl_get_line_coding

**아이콘** ![호스트 클래스 Cdc Acm Ioctl 줄 코드 가져오기 아이콘](./media/user-guide/usbx-events/image95.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 줄 코드 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 매개 변수
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a>호스트 클래스 Cdc Acm Ioctl 알림 콜백

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a>ux_host_class_cdc_acm_ioctl_notification_callback

**아이콘** ![호스트 클래스 Cdc Acm Ioctl 알림 콜백 아이콘](./media/user-guide/usbx-events/image96.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 알림 콜백 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 매개 변수
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-ioctl-send-break"></a>호스트 클래스 Cdc Acm Ioctl 보내기 중단 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a>ux_host_class_cdc_acm_ioctl_send_break

**아이콘** ![호스트 클래스 Cdc Acm Ioctl 보내기 중단 아이콘](./media/user-guide/usbx-events/image97.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 보내기 중단 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 매개 변수
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a>호스트 클래스 Cdc Acm Ioctl 줄 코드 설정 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a>ux_host_class_cdc_acm_ioctl_set_line_coding

**아이콘** ![호스트 클래스 Cdc Acm Ioctl 줄 코드 설정 아이콘](./media/user-guide/usbx-events/image97.png) icon](./media/user-guide/usbx-events/image98.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 줄 코드 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 매개 변수
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a>호스트 클래스 Cdc Acm Ioctl 줄 상태 설정 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a>ux_host_class_cdc_acm_ioctl_set_line_state

**아이콘** ![호스트 클래스 Cdc Acm Ioctl 줄 상태 설정 아이콘](./media/user-guide/usbx-events/image99.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 줄 상태 설정 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 매개 변수
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-read"></a>호스트 클래스 Cdc Acm 읽기 

#### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

**아이콘** ![호스트 클래스 Cdc Acm 읽기 아이콘](./media/user-guide/usbx-events/image100.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm 읽기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-reception-start"></a>호스트 클래스 Cdc Acm 수신 시작 

#### <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

**아이콘** ![호스트 클래스 Cdc Acm 수신 시작 아이콘](./media/user-guide/usbx-events/image101.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm 수신 시작 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-reception-stop"></a>호스트 클래스 Cdc Acm 수신 중지 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

**아이콘** ![호스트 클래스 Cdc Acm 수신 중지 아이콘](./media/user-guide/usbx-events/image102.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm 수신 중지 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-cdc-acm-write"></a>호스트 클래스 Cdc Acm 쓰기 

#### <a name="ux_host_class_acm_write"></a>ux_host_class_acm_write

**아이콘** ![호스트 클래스 Cdc Acm 쓰기 아이콘](./media/user-guide/usbx-events/image103.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Cdc Acm 쓰기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-dpump-activate"></a>호스트 클래스 Dpump 활성화 

#### <a name="ux_host_class_dpump_activate"></a>ux_host_class_dpump_activate

**아이콘** ![호스트 클래스 Dpump 활성화 아이콘](./media/user-guide/usbx-events/image104.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Dpump 활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-dpump-deactivate"></a>호스트 클래스 Dpump 비활성화 

#### <a name="ux_host_class_dpump_deactivate"></a>ux_host_class_dpump_deactivate

**아이콘** ![호스트 클래스 Dpump 비활성화 아이콘](./media/user-guide/usbx-events/image105.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Dpump 비활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-dpump-read"></a>호스트 클래스 Dpump 읽기 

#### <a name="ux_host_class_dpump_read"></a>ux_host_class_dpump_read

**아이콘** ![호스트 클래스 Dpump 읽기 아이콘](./media/user-guide/usbx-events/image106.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Dpump 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-dpump-write"></a>호스트 클래스 Dpump 쓰기 

#### <a name="ux_host_class_dpump_write"></a>ux_host_class_dpump_write

**아이콘** ![호스트 클래스 Dpump 쓰기 아이콘](./media/user-guide/usbx-events/image107.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Dpump 쓰기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-activate"></a>호스트 클래스 Hid 활성화 

#### <a name="ux_host_class_hid_activate"></a>ux_host_class_hid_activate

**아이콘** ![호스트 클래스 Hid 활성화 아이콘](./media/user-guide/usbx-events/image108.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Hid 활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-client-register"></a>호스트 클래스 Hid 클라이언트 등록 

#### <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

**아이콘** ![호스트 클래스 Hid 클라이언트 등록 아이콘](./media/user-guide/usbx-events/image109.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Hid 클라이언트 등록 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: Hid 클라이언트 이름
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-deactivate"></a>호스트 클래스 Hid 비활성화 

#### <a name="ux_host_class_hid_deactivate"></a>ux_host_class_hid_deactivate

**아이콘** ![호스트 클래스 Hid 비활성화 아이콘](./media/user-guide/usbx-events/image110.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Hid 비활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-idle-get"></a>호스트 클래스 Hid 유휴 가져오기 

#### <a name="ux_host_class_hid_idle_get"></a>ux_host_class_hid_idle_get

**아이콘** ![호스트 클래스 Hid 유휴 가져오기 아이콘](./media/user-guide/usbx-events/image111.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Hid 유휴 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-idle-set"></a>호스트 클래스 Hid 유휴 설정 

#### <a name="ux_host_class_hid_idle_set"></a>ux_host_class_hid_idle_set

**아이콘** ![호스트 클래스 Hid 유휴 설정 아이콘](./media/user-guide/usbx-events/image112.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Hid 유휴 설정 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-keyboard-activate"></a>호스트 클래스 Hid 키보드 활성화 

#### <a name="ux_host_class_hid_keyboard_activate"></a>ux_host_class_hid_keyboard_activate

**아이콘** ![호스트 클래스 Hid 키보드 활성화 아이콘](./media/user-guide/usbx-events/image113.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Hid 키보드 활성화 이벤트를 나타냅니다.

**정보 필드**
<p>정보 필드 1: 클래스 인스턴스
<p>정보 필드 2: Hid 클라이언트 인스턴스
<p>정보 필드 3: 사용되지 않습니다.
<p>정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-keyboard-deactivate"></a>호스트 클래스 Hid 키보드 비활성화 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a>ux_host_class_hid_keyboard_deactivate

**아이콘** ![호스트 클래스 Hid 키보드 비활성화 아이콘](./media/user-guide/usbx-events/image114.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Hid 키보드 비활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Hid 클라이언트 인스턴스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-mouse-activate"></a>호스트 클래스 Hid 마우스 활성화 

#### <a name="ux_host_class_hid_mouse_activate"></a>ux_host_class_hid_mouse_activate

**아이콘** ![호스트 클래스 Hid 마우스 활성화 아이콘](./media/user-guide/usbx-events/image115.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Hid 마우스 활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Hid 클라이언트 인스턴스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-mouse-deactivate"></a>호스트 클래스 Hid 마우스 비활성화 

#### <a name="ux_host_class_hid_mouse_deactivate"></a>ux_host_class_hid_mouse_deactivate

**아이콘** ![호스트 클래스 Hid 마우스 비활성화 아이콘](./media/user-guide/usbx-events/image116.png)

**설명**

- 이 이벤트는 USBX 호스트 클래스 Hid 마우스 비활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Hid 클라이언트 인스턴스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-remote-control-activate"></a>호스트 클래스 Hid 원격 제어 활성화 

#### <a name="ux_host_class_hid_remote_control_activate"></a>ux_host_class_hid_remote_control_activate

**아이콘** ![호스트 클래스 Hid 원격 제어 활성화 아이콘](./media/user-guide/usbx-events/image117.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Hid 원격 제어 활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Hid 클라이언트 인스턴스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-remote-control-deactivate"></a>호스트 클래스 Hid 원격 제어 비활성화 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a>ux_host_class_hid_remote_control_deactivate

**아이콘** ![호스트 클래스 Hid 원격 제어 비활성화 아이콘](./media/user-guide/usbx-events/image118.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Hid 원격 제어 비활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Hid 클라이언트 인스턴스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-report-get"></a>호스트 클래스 Hid 보고서 가져오기 

#### <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

**아이콘** ![호스트 클래스 Hid 보고서 가져오기 아이콘](./media/user-guide/usbx-events/image119.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Hid 보고서 가져오기를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 클라이언트 보고서
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hid-report-set"></a>호스트 클래스 Hid 보고서 설정 

#### <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

**아이콘** ![호스트 클래스 Hid 보고서 설정 아이콘](./media/user-guide/usbx-events/image120.png)

**설명** 이 이벤트는 USBX 호스트 클래스 Hid 보고서 설정을 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 클라이언트 보고서
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hub-activate"></a>호스트 클래스 허브 활성화 

#### <a name="ux_host_class_hub_activate"></a>ux_host_class_hub_activate

**아이콘** ![호스트 클래스 Hub 활성화 아이콘](./media/user-guide/usbx-events/image121.png)

**설명**

이 이벤트는 USBX 호스트 클래스 허브 활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hub-change-detect"></a>호스트 클래스 허브 변경 검색 

#### <a name="ux_host_class_hub_change_detect"></a>ux_host_class_hub_change_detect

**아이콘** ![호스트 클래스 허브 변경 검색 아이콘](./media/user-guide/usbx-events/image122.png)

**설명**

이 이벤트는 USBX 호스트 클래스 허브 변경 검색 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hub-deactivate"></a>호스트 클래스 허브 비활성화 

#### <a name="ux_host_class_hub_deactivate"></a>ux_host_class_hub_deactivate

**아이콘** ![호스트 클래스 허브 비활성화 아이콘](./media/user-guide/usbx-events/image123.png)

**설명**

이 이벤트는 USBX 호스트 클래스 허브 비활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hub-port-change-connection-process"></a>호스트 클래스 허브 포트 변경 연결 프로세스 

#### <a name="ux_host_class_hub_change_connection_process"></a>ux_host_class_hub_change_connection_process

**아이콘** ![호스트 클래스 허브 포트 변경 연결 프로세스 아이콘](./media/user-guide/usbx-events/image124.png)

**설명**

이 이벤트는 USBX 호스트 클래스 허브 포트 변경 연결 프로세스 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 포트
- 정보 필드 3: 포트 상태
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hub-port-change-enable-process"></a>호스트 클래스 허브 포트 변경 사용 프로세스 

#### <a name="ux_host_class_hub_port_change_enable_process"></a>ux_host_class_hub_port_change_enable_process

**아이콘** ![호스트 클래스 허브 포트 변경 사용 프로세스 아이콘](./media/user-guide/usbx-events/image125.png)

**설명**

이 이벤트는 USBX 호스트 클래스 허브 포트 변경 사용 프로세스 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 포트
- 정보 필드 3: 포트 상태
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hub-port-change-over-current-process"></a>호스트 클래스 허브 포트 전환 현재 프로세스 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a>ux_host_class_hub_port_change_over_current_process

**아이콘** ![호스트 클래스 허브 포트 전환 현재 프로세스 아이콘](./media/user-guide/usbx-events/image126.png)

**설명**

이 이벤트는 nx_packet_allocate를 통한 패킷 할당을 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 포트
- 정보 필드 3: 포트 상태
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hub-port-change-reset-process"></a>호스트 클래스 허브 포트 변경 재설정 프로세스 

#### <a name="ux_host_class_hub_port_change_reset_process"></a>ux_host_class_hub_port_change_reset_process

**아이콘** ![호스트 클래스 허브 포트 변경 재설정 프로세스 아이콘](./media/user-guide/usbx-events/image127.png)

**설명**

이 이벤트는 USBX 호스트 클래스 허브 포트 변경 재설정 프로세스 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 허브 정보 필드 2: 포트
- 정보 필드 3: 포트 상태
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-hub-port-change-suspend-process"></a>호스트 클래스 허브 포트 변경 일시 중단 프로세스 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a>ux_host_class_hub_port_change_suspend_process

**아이콘** ![호스트 클래스 허브 포트 변경 일시 중단 프로세스 아이콘](./media/user-guide/usbx-events/image128.png)

**설명**

이 이벤트는 USBX 호스트 클래스 허브 포트 변경 일시 중단 프로세스 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 포트
- 정보 필드 3: 포트 상태
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-activate"></a>호스트 클래스 Pima 활성화 

#### <a name="ux_host_class_pima_activate"></a>ux_host_class_pima_activate

**아이콘** ![호스트 클래스 Pima 활성화 아이콘](./media/user-guide/usbx-events/image129.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-deactivate"></a>호스트 클래스 Pima 비활성화 

#### <a name="ux_host_class_pima_deactivate"></a>ux_host_class_pima_deactivate

**아이콘** ![호스트 클래스 Pima 비활성화 아이콘](./media/user-guide/usbx-events/image130.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 비활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-device-info-get"></a>호스트 클래스 Pima 디바이스 정보 가져오기 

#### <a name="ux_host_class_pima_device_info_get"></a>ux_host_class_pima_device_info_get

**아이콘** ![호스트 클래스 Pima 디바이스 정보 가져오기 아이콘](./media/user-guide/usbx-events/image131.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 디바이스 정보 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Pima 디바이스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-device-reset"></a>호스트 클래스 Pima 디바이스 재설정 

#### <a name="ux_host_class_pima_device_reset"></a>ux_host_class_pima_device_reset

**아이콘** ![호스트 클래스 Pima 디바이스 재설정 아이콘](./media/user-guide/usbx-events/image132.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 디바이스 재설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-notification"></a>호스트 클래스 Pima 알림 

#### <a name="ux_host_class_pima_notification"></a>ux_host_class_pima_notification

**아이콘** ![호스트 클래스 Pima 알림 아이콘](./media/user-guide/usbx-events/image133.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 알림 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스 정보 필드 2: 이벤트 코드
- 정보 필드 3: 트랜잭션 ID
- 정보 필드 4: 매개 변수 1

### <a name="host-class-pima-number-objects-get"></a>호스트 클래스 Pima 숫자 개체 가져오기 

#### <a name="ux_host_class_pima_number_objects_get"></a>ux_host_class_pima_number_objects_get

**아이콘** ![호스트 클래스 Pima 숫자 개체 가져오기 아이콘](./media/user-guide/usbx-events/image134.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 숫자 개체 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-object-close"></a>호스트 클래스 Pima 개체 닫기 

#### <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

**아이콘** ![호스트 클래스 Pima 개체 닫기 아이콘](./media/user-guide/usbx-events/image135.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 개체 닫기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-object-copy"></a>호스트 클래스 Pima 개체 복사 

#### <a name="ux_host_class_pima_object_copy"></a>ux_host_class_pima_object_copy

**아이콘** ![호스트 클래스 Pima 개체 복사 아이콘](./media/user-guide/usbx-events/image136.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 개체 복사 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-object-delete"></a>호스트 클래스 Pima 개체 삭제 

#### <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

**아이콘** ![호스트 클래스 Pima 개체 삭제 아이콘](./media/user-guide/usbx-events/image137.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 개체 삭제 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-object-get"></a>호스트 클래스 Pima 개체 가져오기 

#### <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

**아이콘** ![호스트 클래스 Pima 개체 가져오기 아이콘](./media/user-guide/usbx-events/image138.png)

**설명**

이 이벤트는 nx_rarp_info_get을 통한 RARP 정보 가져오기를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 개체
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-object-info-get"></a>호스트 클래스 Pima 개체 정보 가져오기 

#### <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

**아이콘** ![호스트 클래스 Pima 개체 정보 가져오기 아이콘](./media/user-guide/usbx-events/image139.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 개체 정보 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 개체
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-object-info-send"></a>호스트 클래스 Pima 개체 정보 보내기 

#### <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

**아이콘** ![호스트 클래스 Pima 개체 정보 보내기 아이콘](./media/user-guide/usbx-events/image140.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 개체 정보 보내기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-object-move"></a>호스트 클래스 Pima 개체 이동 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**아이콘** ![호스트 클래스 Pima 개체 이동 아이콘](./media/user-guide/usbx-events/image141.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 개체 이동 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 개체
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-object-send"></a>호스트 클래스 Pima 개체 보내기 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**아이콘** ![호스트 클래스 Pima 개체 보내기 아이콘](./media/user-guide/usbx-events/image142.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 개체 보내기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체
- 정보 필드 3: 개체 버퍼
- 정보 필드 4: 개체 길이

### <a name="host-class-pima-object-transfer-abort"></a>호스트 클래스 Pima 개체 전송 중단 

#### <a name="ux_host_class_pima_object_transfer_abort"></a>ux_host_class_pima_object_transfer_abort

**아이콘** ![호스트 클래스 Pima 개체 전송 중단 아이콘](./media/user-guide/usbx-events/image143.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 개체 전송 중단 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 개체
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-read"></a>호스트 클래스 Pima 읽기 

#### <a name="ux_host_class_pima_read"></a>ux_host_class_pima_read

**아이콘** ![호스트 클래스 Pima 읽기 아이콘](./media/user-guide/usbx-events/image144.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 데이터 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-request-cancel"></a>호스트 클래스 Pima 요청 취소 

#### <a name="ux_host_class_pima_request_cancel"></a>ux_host_class_pima_request_cancel

**아이콘** ![호스트 클래스 Pima 요청 취소 아이콘](./media/user-guide/usbx-events/image145.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 요청 취소 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-session-close"></a>호스트 클래스 Pima 세션 닫기 

#### <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

**아이콘** ![호스트 클래스 Pima 세션 닫기 아이콘](./media/user-guide/usbx-events/image146.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 세션 닫기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Pima 세션
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-session-open"></a>호스트 클래스 Pima 세션 열기 

#### <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

**아이콘** ![호스트 클래스 Pima 세션 열기 아이콘](./media/user-guide/usbx-events/image147.png)

**설명** 이 이벤트는 USBX 호스트 클래스 Pima 세션 열기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: Pima 세션
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-storage-ids-get"></a>호스트 클래스 Pima 스토리지 ID 가져오기 

#### <a name="ux_host_class_pima_session_ids_get"></a>ux_host_class_pima_session_ids_get

**아이콘** ![호스트 클래스 Pima 스토리지 ID 가져오기 아이콘](./media/user-guide/usbx-events/image148.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 스토리지 ID 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 스토리지 ID 배열
- 정보 필드 3: 스토리지 ID 길이
정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-storage-info-get"></a>호스트 클래스 Pima 스토리지 가져오기 

#### <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

**아이콘** ![호스트 클래스 Pima 스토리지 가져오기 아이콘](./media/user-guide/usbx-events/image149.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 스토리지 정보 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 스토리지 ID
- 정보 필드 3: 스토리지
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-thumb-get"></a>호스트 클래스 Pima Thumb 가져오기 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**아이콘** ![호스트 클래스 Pima Thumb 가져오기 아이콘](./media/user-guide/usbx-events/image150.png)

**설명**

이 이벤트는 nx_tcp_server_socket_unaccept를 통해 TCP 서버 연결을 허용하지 않는 경우를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 개체 핸들
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-pima-write"></a>호스트 클래스 Pima 쓰기 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**아이콘** ![호스트 클래스 Pima 쓰기 아이콘](./media/user-guide/usbx-events/image151.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Pima 쓰기를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 데이터 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-printer-activate"></a>호스트 클래스 프린터 활성화 

#### <a name="ux_host_class_printer_activate"></a>ux_host_class_printer_activate

**아이콘** ![호스트 클래스 프린터 활성화 아이콘](./media/user-guide/usbx-events/image152.png)

**설명**

이 이벤트는 USBX 호스트 클래스 프린터 활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터
- 정보 필드 2: 소켓에 대한 포인터
- 정보 필드 3: 서비스 유형
- 정보 필드 4: 수신 창 크기

### <a name="host-class-printer-deactivate"></a>호스트 클래스 프린터 비활성화 

#### <a name="ux_host_class_printer_deactivate"></a>ux_host_class_printer_deactivate

**아이콘** ![호스트 클래스 프린터 비활성화 아이콘](./media/user-guide/usbx-events/image153.png)

**설명**

이 이벤트는 USBX 호스트 클래스 프린터 비활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-printer-name-get"></a>호스트 클래스 프린터 이름 가져오기 

#### <a name="ux_host_class_printer_name_get"></a>ux_host_class_printer_name_get

**아이콘** ![호스트 클래스 프린터 이름 가져오기 아이콘](./media/user-guide/usbx-events/image154.png)

**설명**

이 이벤트는 USBX 호스트 클래스 프린터 이름 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-printer-read"></a>호스트 클래스 프린터 읽기 

#### <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

**아이콘** ![호스트 클래스 프린터 읽기 아이콘](./media/user-guide/usbx-events/image155.png)

**설명**

이 이벤트는 USBX 호스트 클래스 프린터 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-printer-soft-reset"></a>호스트 클래스 프린터 소프트 리셋 

#### <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

**아이콘** ![호스트 클래스 프린터 소프트 리셋 아이콘](./media/user-guide/usbx-events/image156.png)

**설명**

이 이벤트는 USBX 호스트 클래스 프린터 소프트 리셋 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-printer-status-get"></a>호스트 클래스 프린터 상태 가져오기 

#### <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

**아이콘** ![호스트 클래스 프린터 상태 가져오기 아이콘](./media/user-guide/usbx-events/image157.png)

**설명**

이 이벤트는 USBX 호스트 클래스 프린터 상태 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 프린터 상태
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-printer-write"></a>호스트 클래스 프린터 쓰기 

#### <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

**아이콘** ![호스트 클래스 프린터 쓰기 아이콘](./media/user-guide/usbx-events/image158.png)

**설명**

이 이벤트는 USBX 호스트 클래스 프린터 쓰기를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-activate"></a>호스트 클래스 Prolific 활성화 

#### <a name="ux_host_class_prolific_activate"></a>ux_host_class_prolific_activate 

**아이콘** ![호스트 클래스 Prolific 활성화 아이콘](./media/user-guide/usbx-events/image159.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific 활성화 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-deactivate"></a>호스트 클래스 Prolific 비활성화 

#### <a name="ux_host_class_prolific_deactivate"></a>ux_host_class_prolific_deactivate 

**아이콘** ![호스트 클래스 Prolific 비활성화 아이콘](./media/user-guide/usbx-events/image160.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific 비활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a>호스트 클래스 Prolific Ioctl 파이프에서 중단 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a>ux_host_class_prolific_ioctl_abort_in_pipe

**아이콘** ![호스트 클래스 Prolific Ioctl 파이프에서 중단 아이콘](./media/user-guide/usbx-events/image161.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 파이프에서 중단 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 엔드포인트
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a>호스트 클래스 Prolific Ioctl 파이프 외부에서 중단 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a>ux_host_class_prolific_ioctl_abort_out_pipe

**아이콘** ![호스트 클래스 Prolific Ioctl 파이프 외부에서 중단 아이콘](./media/user-guide/usbx-events/image162.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 파이프 외부에서 중단 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 엔드포인트
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-ioctl-get-device-status"></a>호스트 클래스 Prolific Ioctl 디바이스 상태 가져오기 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a>ux_host_class_prolific_ioctl_get_device_status

**아이콘** ![호스트 클래스 Prolific Ioctl 디바이스 상태 가져오기 아이콘](./media/user-guide/usbx-events/image163.png)

**설명**

이 이벤트는 c # 호스트 클래스 Prolific Ioctl 디바이스 상태 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 디바이스 상태
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-ioctl-get-line-coding"></a>호스트 클래스 Prolific Ioctl 줄 코드 가져오기 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a>ux_host_class_prolific_ioctl_get_line_coding

**아이콘** ![호스트 클래스 Prolific Ioctl 줄 코드 가져오기 아이콘](./media/user-guide/usbx-events/image164.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 줄 코드 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 매개 변수
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-ioctl-purge"></a>호스트 클래스 Prolific Ioctl 제거 

#### <a name="ux_host_class_prolific_ioctl_purge"></a>ux_host_class_prolific_ioctl_purge

**아이콘** ![호스트 클래스 Prolific Ioctl 제거 아이콘](./media/user-guide/usbx-events/image165.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 제거 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 매개 변수
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-ioctl-report-device"></a>호스트 클래스 Prolific Ioctl 보고서 디바이스 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a>ux_host_class_prolific_ioctl_report_device

**아이콘** ![호스트 클래스 Prolific Ioctl 보고서 디바이스 아이콘](./media/user-guide/usbx-events/image166.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 보고서 디바이스 상태 변경 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 매개 변수
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-ioctl-send-break"></a>호스트 클래스 Prolific Ioctl 보내기 중단 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a>ux_host_class_prolific_ioctl_send_break

**아이콘** ![호스트 클래스 Prolific Ioctl 보내기 중단 아이콘](./media/user-guide/usbx-events/image167.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 보내기 중단 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-ioctl-set-line-coding"></a>호스트 클래스 Prolific Ioctl 줄 코드 설정 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a>ux_host_class_prolific_ioctl_set_line_coding

**아이콘** ![호스트 클래스 Prolific Ioctl 줄 코드 설정 아이콘](./media/user-guide/usbx-events/image168.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 줄 코드 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 매개 변수
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-ioctl-set-line-state"></a>호스트 클래스 Prolific Ioctl 줄 상태 설정 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a>ux_host_class_prolific_ioctl_set_line_state

**아이콘** ![호스트 클래스 Prolific Ioctl 줄 상태 설정 아이콘](./media/user-guide/usbx-events/image169.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 줄 상태 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 매개 변수
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-read"></a>호스트 클래스 Prolific 읽기 

#### <a name="ux_host_class_prolific_read"></a>ux_host_class_prolific_read

**아이콘** ![호스트 클래스 Prolific 읽기 아이콘](./media/user-guide/usbx-events/image170.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-reception-start"></a>호스트 클래스 Prolific 수신 시작 

#### <a name="ux_host_class_prolific_reception_start"></a>ux_host_class_prolific_reception_start

**아이콘** ![호스트 클래스 Prolific 수신 시작 아이콘](./media/user-guide/usbx-events/image171.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific 수신 시작 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-reception-stop"></a>호스트 클래스 Prolific 수신 중지 

#### <a name="ux_host_class_prolific_reception_stop"></a>ux_host_class_prolific_reception_stop

**아이콘** ![호스트 클래스 Prolific 수신 중지 아이콘](./media/user-guide/usbx-events/image172.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific 수신 중지 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-prolific-write"></a>호스트 클래스 Prolific 쓰기 

#### <a name="ux_host_class_prolific_write"></a>ux_host_class_prolific_write

**아이콘** ![호스트 클래스 Prolific 쓰기 아이콘](./media/user-guide/usbx-events/image173.png)

**설명**

이 이벤트는 USBX 호스트 클래스 Prolific 쓰기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 데이터 포인터
- 정보 필드 3: 요청된 길이
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-storage-activate"></a>호스트 클래스 스토리지 활성화 

#### <a name="ux_host_class_storage_activate"></a>ux_host_class_storage_activate

**아이콘** ![호스트 클래스 스토리지 활성화 아이콘](./media/user-guide/usbx-events/image174.png)

**설명**

이 이벤트는 USBX 호스트 클래스 스토리지 활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-storage-deactivate"></a>호스트 클래스 스토리지 비활성화 

#### <a name="ux_host_class_storage_deactivate"></a>ux_host_class_storage_deactivate

**아이콘** ![호스트 클래스 스토리지 비활성화 아이콘](./media/user-guide/usbx-events/image175.png)

**설명**

이 이벤트는 USBX 호스트 클래스 스토리지 비활성화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-storage-media-capacity-get"></a>호스트 클래스 스토리지 미디어 용량 가져오기 

#### <a name="ux_host_class_storage_media_capacity_get"></a>ux_host_class_storage_media_capacity_get

**아이콘** ![호스트 클래스 스토리지 미디어 용량 가져오기 아이콘](./media/user-guide/usbx-events/image176.png)

**설명**

이 이벤트는 USBX 호스트 클래스 스토리지 미디어 용량 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-storage-media-format-capacity-get"></a>호스트 클래스 스토리지 미디어 형식 용량 가져오기

#### <a name="ux_host_class_storage_media_format_capacity_get"></a>ux_host_class_storage_media_format_capacity_get

**아이콘** ![호스트 클래스 스토리지 미디어 형식 용량 가져오기 아이콘](./media/user-guide/usbx-events/image177.png)

**설명**

이 이벤트는 USBX 호스트 클래스 스토리지 미디어 형식 용량 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

#### <a name="host-class-storage-media-mount"></a>호스트 클래스 스토리지 미디어 탑재 

#### <a name="ux_host_class_storage_media_mount"></a>ux_host_class_storage_media_mount

**아이콘** ![호스트 클래스 스토리지 미디어 탑재 아이콘](./media/user-guide/usbx-events/image178.png)

**설명**

이 이벤트는 USBX 호스트 클래스 스토리지 미디어 탑재 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 섹터
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-storage-media-open"></a>호스트 클래스 스토리지 미디어 열기 

#### <a name="ux_host_class_storage_media_open"></a>ux_host_class_storage_media_open

**아이콘** ![호스트 클래스 스토리지 미디어 열기 아이콘](./media/user-guide/usbx-events/image179.png)

**설명**

이 이벤트는 USBX 호스트 클래스 스토리지 미디어 열기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 미디어
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-storage-media-read"></a>호스트 클래스 스토리지 미디어 읽기 

#### <a name="ux_host_class_storage_media_read"></a>ux_host_class_storage_media_read

**아이콘** ![호스트 클래스 스토리지 미디어 읽기 아이콘](./media/user-guide/usbx-events/image180.png)

**설명**

이 이벤트는 USBX 호스트 클래스 스토리지 미디어 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 섹터 시작
- 정보 필드 3: 섹터 수
- 정보 필드 4: 데이터 포인터

### <a name="host-class-storage-media-write"></a>호스트 클래스 스토리지 미디어 쓰기 

#### <a name="ux_host_class_storage_media_write"></a>ux_host_class_storage_media_write

**아이콘** ![호스트 클래스 스토리지 미디어 쓰기 아이콘](./media/user-guide/usbx-events/image181.png)

**설명**

이 이벤트는 USBX 호스트 클래스 스토리지 미디어 쓰기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 섹터 시작
- 정보 필드 3: 섹터 수
- 정보 필드 4: 데이터 포인터

### <a name="host-class-storage-request-sense"></a>호스트 클래스 스토리지 요청 센스 

#### <a name="ux_host_class_storage_request_sense"></a>ux_host_class_storage_request_sense

**아이콘** ![호스트 클래스 스토리지 요청 센스 아이콘](./media/user-guide/usbx-events/image182.png)

**설명**

이 이벤트는 USBX 호스트 클래스 스토리지 요청 센스 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-storage-start-stop"></a>호스트 클래스 스토리지 시작 중지 

#### <a name="ux_host_class_storage_start_stop"></a>ux_host_class_storage_start_stop

**아이콘** ![호스트 클래스 스토리지 시작 중지 아이콘](./media/user-guide/usbx-events/image183.png)

**설명**

이 이벤트는 USBX 호스트 클래스 스토리지 시작 중지 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 시작 중지 신호
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-class-storage-unit-ready-test"></a>호스트 클래스 스토리지 장치 준비 테스트 

#### <a name="ux_host_class_storage_unit_ready_test"></a>ux_host_class_storage_unit_ready_test

**아이콘** ![호스트 클래스 스토리지 장치 준비 테스트 아이콘](./media/user-guide/usbx-events/image184.png)

**설명**

이 이벤트는 USBX 호스트 클래스 스토리지 단위 준비 테스트 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스 인스턴스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-class-instance-create"></a>호스트 스택 클래스 인스턴스 만들기 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**아이콘** ![호스트 스택 클래스 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image185.png)

**설명**

이 이벤트는 USBX 호스트 스택 클래스 인스턴스 만들기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스
- 정보 필드 2: 클래스 인스턴스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-class-instance-destroy"></a>호스트 스택 클래스 인스턴스 삭제 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**아이콘** ![호스트 스택 클래스 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image186.png)

**설명**

이 이벤트는 USBX 호스트 스택 클래스 인스턴스 삭제 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 클래스
- 정보 필드 2: 클래스 인스턴스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-configuration-delete"></a>호스트 스택 구성 삭제 

#### <a name="ux_host_class_configuration_delete"></a>ux_host_class_configuration_delete

**아이콘** ![호스트 스택 구성 삭제 아이콘](./media/user-guide/usbx-events/image187.png)

**설명**

이 이벤트는 USBX 호스트 스택 구성 삭제 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 구성
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-configuration-enumerate"></a>호스트 스택 구성 열거 

#### <a name="ux_host_stack_configuration_enumerate"></a>ux_host_stack_configuration_enumerate

**아이콘** ![호스트 스택 구성 열거 아이콘](./media/user-guide/usbx-events/image188.png)

**설명**

이 이벤트는 USBX 호스트 스택 구성 열거 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="stack-configuration-instance-create"></a>스택 구성 인스턴스 만들기 

#### <a name="ux_host_stack_configuration_instance_create"></a>ux_host_stack_configuration_instance_create

**아이콘** ![스택 구성 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image189.png)

**설명**

이 이벤트는 USBX 호스트 스택 구성 인스턴스 만들기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 구성
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-configuration-instance-delete"></a>호스트 스택 구성 인스턴스 삭제 

#### <a name="ux_host_stack_configuration_instance_delete"></a>ux_host_stack_configuration_instance_delete

**아이콘** ![호스트 스택 구성 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image190.png)

**설명**

이 이벤트는 USBX 호스트 스택 구성 인스턴스 삭제 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 구성
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-configuration-set"></a>호스트 스택 구성 설정 

#### <a name="ux_host_stack_configuration_set"></a>ux_host_stack_configuration_set

**아이콘** ![호스트 스택 구성 설정 아이콘](./media/user-guide/usbx-events/image191.png)

**설명**

이 이벤트는 USBX 호스트 스택 구성 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 구성
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-device-address-set"></a>호스트 스택 디바이스 주소 설정 

#### <a name="ux_host_stack_device_address_set"></a>ux_host_stack_device_address_set

**아이콘** ![호스트 스택 디바이스 주소 설정 아이콘](./media/user-guide/usbx-events/image192.png)

**설명**

이 이벤트는 USBX 호스트 스택 디바이스 주소 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스
- 정보 필드 2: 디바이스 주소
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-device-configuration-get"></a>호스트 스택 디바이스 구성 가져오기 

#### <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

**아이콘** ![호스트 스택 디바이스 구성 가져오기 아이콘](./media/user-guide/usbx-events/image193.png)

**설명**

이 이벤트는 USBX 호스트 스택 디바이스 구성 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스
- 정보 필드 2: 구성
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-device-configuration-select"></a>호스트 스택 디바이스 구성 선택 

#### <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

**아이콘** ![호스트 스택 디바이스 구성 선택 아이콘](./media/user-guide/usbx-events/image194.png)

**설명**

이 이벤트는 USBX 호스트 스택 디바이스 구성 선택 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스
- 정보 필드 2: 구성
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-device-descriptor-read"></a>호스트 스택 디바이스 설명자 읽기 

#### <a name="ux_host_stack_device_descriptor_read"></a>ux_host_stack_device_descriptor_read

**아이콘** ![호스트 스택 디바이스 설명자 읽기 아이콘](./media/user-guide/usbx-events/image195.png)

**설명**

이 이벤트는 USBX 호스트 스택 디바이스 설명자 읽기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-device-get"></a>호스트 스택 디바이스 가져오기 

#### <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

**아이콘** ![호스트 스택 디바이스 가져오기 아이콘](./media/user-guide/usbx-events/image196.png)

**설명**

이 이벤트는 USBX 호스트 스택 디바이스 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스 인덱스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-device-remove"></a>호스트 스택 디바이스 제거 

#### <a name="ux_host_stack_device_remove"></a>ux_host_stack_device_remove

**아이콘** ![호스트 스택 디바이스 제거 아이콘](./media/user-guide/usbx-events/image197.png)

**설명**

이 이벤트는 USBX 호스트 스택 디바이스 제거 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: Hcd
- 정보 필드 2: 부모 항목
- 정보 필드 3: 포트 인덱스
- 정보 필드 4: 디바이스

### <a name="host-stack-device-resource-free"></a>호스트 스택 디바이스 리소스 해제 

#### <a name="ux_host_stack_device_resource_free"></a>ux_host_stack_device_resource_free

**아이콘** ![호스트 스택 디바이스 리소스 해제 아이콘](./media/user-guide/usbx-events/image198.png)

**설명**

이 이벤트는 USBX 호스트 스택 디바이스 리소스 해제 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-endpoint-instance-create"></a>호스트 스택 엔드포인트 인스턴스 만들기 

#### <a name="ux_host_stack_endpoint_instance_create"></a>ux_host_stack_endpoint_instance_create

**아이콘** ![호스트 스택 엔드포인트 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image199.png)

**설명**

이 이벤트는 USBX 호스트 스택 엔드포인트 인스턴스 만들기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스
- 정보 필드 2: 엔드포인트
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-endpoint-instance-delete"></a>호스트 스택 엔드포인트 인스턴스 삭제 

#### <a name="ux_host_stack_endpoint_instance_delete"></a>ux_host_stack_endpoint_instance_delete

**아이콘** ![호스트 스택 엔드포인트 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image200.png)

**설명**

이 이벤트는 USBX 호스트 스택 엔드포인트 인스턴스 삭제 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 2: 엔드포인트
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-endpoint-reset"></a>호스트 스택 엔드포인트 재설정 

#### <a name="ux_host_stack_endpoint_reset"></a>ux_host_stack_endpoint_reset

**아이콘** ![호스트 스택 엔드포인트 재설정 아이콘](./media/user-guide/usbx-events/image201.png)

**설명**

이 이벤트는 USBX 호스트 스택 엔드포인트 재설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스
- 정보 필드 2: 엔드포인트
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-endpoint-transfer-abort"></a>호스트 스택 엔드포인트 전송 중단 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

**아이콘** ![호스트 스택 엔드포인트 전송 중단 아이콘](./media/user-guide/usbx-events/image202.png)

**설명**

이 이벤트는 USBX 호스트 스택 엔드포인트 전송 중단 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 엔드포인트
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-host-controller-register"></a>호스트 스택 호스트 컨트롤러 등록 

#### <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

**아이콘** ![호스트 스택 호스트 컨트롤러 등록 아이콘](./media/user-guide/usbx-events/image203.png)

**설명**

이 이벤트는 USBX 호스트 스택 호스트 컨트롤러 등록을 나타냅니다.

**정보 필드**

- 정보 필드 1: Hcd 이름
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-initialize"></a>호스트 스택 초기화 

#### <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

**아이콘** ![호스트 스택 초기화 아이콘](./media/user-guide/usbx-events/image204.png)

**설명**

이 이벤트는 USBX 호스트 스택 초기화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-interface-endpoint-get"></a>호스트 스택 인터페이스 엔드포인트 가져오기 

#### <a name="interface_-tcp-retry-entry"></a>인터페이스 TCP 다시 시도 항목

**아이콘** ![호스트 스택 인터페이스 엔드포인트 가져오기 아이콘](./media/user-guide/usbx-events/image205.png)

**설명**

이 이벤트는 내부 NetX TCP 다시 시도 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 인터페이스
- 정보 필드 2: 엔드포인트 인덱스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-interface-instance-create"></a>호스트 스택 인터페이스 인스턴스 만들기 

#### <a name="ux_host_stack_interface_instance_create"></a>ux_host_stack_interface_instance_create

**아이콘** ![호스트 스택 인터페이스 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image206.png)

**설명**

이 이벤트는 USBX 호스트 스택 인터페이스 인스턴스 만들기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 인터페이스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-interface-instance-delete"></a>호스트 스택 인터페이스 인스턴스 삭제 

#### <a name="ux_host_stack_interface_instance_delete"></a>ux_host_stack_interface_instance_delete

**아이콘** ![호스트 스택 인터페이스 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image207.png)

**설명**

이 이벤트는 USBX 호스트 스택 인터페이스 인스턴스 삭제 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 인터페이스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-interface-set"></a>호스트 스택 인터페이스 설정 

#### <a name="ux_host_stack_interface_set"></a>ux_host_stack_interface_set

**아이콘** ![호스트 스택 인터페이스 설정 아이콘](./media/user-guide/usbx-events/image208.png)

**설명**

이 이벤트는 USBX 호스트 스택 인터페이스 설정 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 인터페이스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-interface-setting-select"></a>호스트 스탭 인터페이스 설정 선택 

#### <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

**아이콘** ![호스트 스택 인터페이스 설정 선택 아이콘](./media/user-guide/usbx-events/image209.png)

**설명**

이 이벤트는 USBX 호스트 스택 인터페이스 설정 선택 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 인터페이스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-new-configuration-create"></a>호스트 스택 새 구성 만들기 

#### <a name="ux_host_stack_new_configuration_create"></a>ux_host_stack_new_configuration_create

**아이콘** ![호스트 스택 새 구성 만들기 아이콘](./media/user-guide/usbx-events/image210.png)

**설명**
 
이 이벤트는 USBX 호스트 스택 새 구성 만들기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스
- 정보 필드 2: 구성
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-new-device-create"></a>호스트 스택 새 디바이스 만들기 

#### <a name="ux_host_stack_new_device_create"></a>ux_host_stack_new_device_create

**아이콘** ![호스트 스택 새 디바이스 만들기 아이콘](./media/user-guide/usbx-events/image211.png)

**설명**
 
 이 이벤트는 USBX 호스트 스택 새 디바이스 만들기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: Hcd
- 정보 필드 2: 디바이스 소유자
- 정보 필드 3: 포트 인덱스
- 정보 필드 4: 디바이스

### <a name="host-stack-new-endpoint-create"></a>호스트 스택 새 엔드포인트 만들기 

#### <a name="ux_host_stack_new_endpoint_create"></a>ux_host_stack_new_endpoint_create

**아이콘** ![호스트 스택 새 엔드포인트 만들기 아이콘](./media/user-guide/usbx-events/image212.png)

**설명**
 
이 이벤트는 USBX 호스트 스택 새 엔드포인트 만들기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: 인터페이스
- 정보 필드 2: 엔드포인트
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-root-hub-change-process"></a>호스트 스택 루트 허브 변경 프로세스 

#### <a name="ux_host_stack_rh_change_process"></a>ux_host_stack_rh_change_process

**아이콘** ![호스트 스택 루트 허브 변경 프로세스 아이콘](./media/user-guide/usbx-events/image213.png)

**설명**
 
이 이벤트는 USBX 호스트 스택 루트 허브 변경 프로세스를 나타냅니다.

**정보 필드**

- 정보 필드 1: 포트 인덱스
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-root-hub-device-extraction"></a>호스트 스택 루트 허브 디바이스 추출 

#### <a name="ux_host_stack_rh_device_extraction"></a>ux_host_stack_rh_device_extraction

**아이콘** ![호스트 스택 루트 허브 디바이스 추출 아이콘](./media/user-guide/usbx-events/image214.png)

**설명**

이 이벤트는 USBX 호스트 스택 루트 허브 디바이스 추출 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: Hcd
- 정보 필드 2: 포트 인덱스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-root-hub-device-insertion"></a>호스트 스택 루트 허브 디바이스 삽입 

#### <a name="ux_host_stack_rh_device_insertion"></a>ux_host_stack_rh_device_insertion

**아이콘** ![호스트 스택 루트 허브 디바이스 삽입 아이콘](./media/user-guide/usbx-events/image215.png)

**설명**

이 이벤트는 USBX 호스트 스택 루트 허브 디바이스 삽입을 나타냅니다.

**정보 필드**

- 정보 필드 1: Hcd
- 정보 필드 2: 포트 인덱스
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-transfer-request"></a>호스트 스택 전송 요청 

#### <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

**아이콘** ![호스트 스택 전송 요청 아이콘](./media/user-guide/usbx-events/image216.png)

**설명**

이 이벤트는 USBX 호스트 스택 전송 요청을 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스
- 정보 필드 2: 엔드포인트
- 정보 필드 3: 전송 요청
- 정보 필드 4: 사용되지 않습니다.

### <a name="host-stack-transfer-request-abort"></a>호스트 스택 전송 요청 중단 

#### <a name="internal-io-driver-get-status"></a>내부 I/O 드라이버 가져오기 상태

**아이콘** ![호스트 스택 전송 요청 중단 아이콘](./media/user-guide/usbx-events/image217.png)

**설명**

이 이벤트는 USBX 호스트 스택 전송 요청 중단을 나타냅니다.

**정보 필드**

- 정보 필드 1: 디바이스
- 정보 필드 2: 엔드포인트
- 정보 필드 3: 전송 요청
- 정보 필드 4: 사용되지 않습니다.

### <a name="usbx-error"></a>USBX 오류 

#### <a name="ux_error"></a>ux_error

**아이콘** ![U S B X 오류 아이콘](./media/user-guide/usbx-events/image218.png)

**설명**

이 이벤트는 USBX 오류 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: USBX 오류
- 정보 필드 2: 오류 이름
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.