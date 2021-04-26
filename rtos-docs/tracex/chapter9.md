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
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a><span data-ttu-id="65356-103">9장 - Azure RTOS BX 추적 이벤트</span><span class="sxs-lookup"><span data-stu-id="65356-103">Chapter 9 - Azure RTOS USBX trace events</span></span>

<span data-ttu-id="65356-104">이 장은 TraceX에서 표시하는 Azure RTOS 이벤트에 대한 설명을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="65356-104">This chapter contains a description of the Azure RTOS USBX events displayed by TraceX.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="65356-105">이벤트 및 아이콘 목록</span><span class="sxs-lookup"><span data-stu-id="65356-105">List of Events and Icons</span></span>

<span data-ttu-id="65356-106">다음은 TraceX에 의해 표시되는 USBX 이벤트 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="65356-106">The following is a list of USBX events displayed by TraceX.</span></span>

| <span data-ttu-id="65356-107">아이콘</span><span class="sxs-lookup"><span data-stu-id="65356-107">Icon</span></span>                             | <span data-ttu-id="65356-108">의미</span><span class="sxs-lookup"><span data-stu-id="65356-108">Meaning</span></span>                               |
| -------------------------------- | ------------------------------------- |
| ![디바이스 클래스 C D C 활성화 아이콘](./media/user-guide/usbx-events/image1.png)    | <span data-ttu-id="65356-110">**디바이스 클래스 Cdc 활성화**(ux_device_class_cdc_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-110">**Device Class Cdc Activate** *(ux_device_class_cdc_activate)*</span></span> |
| ![디바이스 클래스 C D C 비활성화 아이콘](./media/user-guide/usbx-events/image2.png)    | <span data-ttu-id="65356-112">**디바이스 클래스 Cdc 비활성화**(ux_device_class_cdc_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-112">**Device Class Cdc Deactivate** *(ux_device_class_cdc_deactivate)*</span></span> |
| ![디바이스 클래스 C D C 읽기 아이콘](./media/user-guide/usbx-events/image3.png)    | <span data-ttu-id="65356-114">**디바이스 클래스 Cdc 읽기**(ux_device_class_cdc_read)</span><span class="sxs-lookup"><span data-stu-id="65356-114">**Device Class Cdc Read** *(ux_device_class_cdc_read)*</span></span> |
| ![디바이스 클래스 C D C 쓰기 아이콘](./media/user-guide/usbx-events/image4.png)    | <span data-ttu-id="65356-116">**디바이스 클래스 Cdc 쓰기**(ux_device_class_cdc_write)</span><span class="sxs-lookup"><span data-stu-id="65356-116">**Device Class Cdc Write** *(ux_device_class_cdc_write)*</span></span> |
| ![디바이스 클래스 Dpump 활성화 아이콘](./media/user-guide/usbx-events/image5.png)    | <span data-ttu-id="65356-118">**디바이스 클래스 Dpump 활성화**(ux_device_class_dpump_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-118">**Device Class Dpump Activate** *(ux_device_class_dpump_activate)*</span></span> |
| ![디바이스 클래스 Dpump 비활성화 아이콘](./media/user-guide/usbx-events/image6.png)    | <span data-ttu-id="65356-120">**디바이스 클래스 Dpump 비활성화**</span><span class="sxs-lookup"><span data-stu-id="65356-120">**Device Class Dpump Deactivate** *(ux_device_class_dpump_deactivate)*</span></span> |
| ![디바이스 클래스 Dpump 읽기 아이콘](./media/user-guide/usbx-events/image7.png)    | <span data-ttu-id="65356-122">**디바이스 클래스 Dpump 읽기**(ux_device_class_dpump_read)</span><span class="sxs-lookup"><span data-stu-id="65356-122">**Device Class Dpump Read** *(ux_device_class_dpump_read)*</span></span> |
| ![디바이스 클래스 Dpump 쓰기 아이콘](./media/user-guide/usbx-events/image8.png)    | <span data-ttu-id="65356-124">**디바이스 클래스 Dpump 쓰기**</span><span class="sxs-lookup"><span data-stu-id="65356-124">**Device Class Dpump Write** *(ux_device_class_dpump_write)*</span></span> |
| ![디바이스 클래스 Hid 활성화 아이콘](./media/user-guide/usbx-events/image9.png)    | <span data-ttu-id="65356-126">**디바이스 클래스 Hid 활성화**(ux_device_class_hid_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-126">**Device Class Hid Activate** *(ux_device_class_hid_activate)*</span></span> |
| ![디바이스 클래스 Hid 비활성화 아이콘](./media/user-guide/usbx-events/image10.png)    | <span data-ttu-id="65356-128">**디바이스 클래스 Hid 비활성화**</span><span class="sxs-lookup"><span data-stu-id="65356-128">**Device Class Hid Deactivate** *(ux_device_class_hid_deactivate)*</span></span> |
| ![디바이스 클래스 Hid 설명자 보내기 아이콘](./media/user-guide/usbx-events/image11.png)    | <span data-ttu-id="65356-130">**디바이스 클래스 Hid 설명자 보내기**(ux_device_class_hid_descriptor_send)</span><span class="sxs-lookup"><span data-stu-id="65356-130">**Device Class Hid Descriptor Send** *(ux_device_class_hid_descriptor_send)*</span></span> |
| ![디바이스 클래스 Hid 이벤트 가져오기 아이콘](./media/user-guide/usbx-events/image12.png)    | <span data-ttu-id="65356-132">**디바이스 클래스 Hid 이벤트 가져오기**(ux_device_class_hid_event_get)</span><span class="sxs-lookup"><span data-stu-id="65356-132">**Device Class Hid Event Get** *(ux_device_class_hid_event_get)*</span></span> |
| ![디바이스 클래스 Hid 이벤트 설정 아이콘](./media/user-guide/usbx-events/image13.png)    | <span data-ttu-id="65356-134">**디바이스 클래스 Hid 이벤트 설정**</span><span class="sxs-lookup"><span data-stu-id="65356-134">**Device Class Hid Event Set** *(ux_device_class_hid_event_set)*</span></span> |
| ![디바이스 클래스 Hid 보고서 가져오기 아이콘](./media/user-guide/usbx-events/image14.png)    | <span data-ttu-id="65356-136">**디바이스 클래스 Hid 보고서 가져오기**(ux_device_class_hid_report_get)</span><span class="sxs-lookup"><span data-stu-id="65356-136">**Device Class Hid Report Get** *(ux_device_class_hid_report_get)*</span></span> |
| ![디바이스 클래스 Hid 보고서 설정 아이콘](./media/user-guide/usbx-events/image15.png)    | <span data-ttu-id="65356-138">**디바이스 클래스 Hid 보고서 설정**(ux_device_class_hid_report_set)</span><span class="sxs-lookup"><span data-stu-id="65356-138">**Device Class Hid Report Set** *(ux_device_class_hid_report_set)*</span></span> |
| ![디바이스 클래스 Pima 활성화 아이콘](./media/user-guide/usbx-events/image16.png)    | <span data-ttu-id="65356-140">**디바이스 클래스 Pima 활성화**(ux_device_class_pima_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-140">**Device Class Pima Activate** *(ux_device_class_pima_activate)*</span></span> |
| ![디바이스 클래스 Pima 비활성화 아이콘](./media/user-guide/usbx-events/image17.png)    | <span data-ttu-id="65356-142">**디바이스 클래스 Pima 비활성화**(ux_device_class_pima_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-142">**Device Class Pima Deactivate** *(ux_device_class_pima_deactivate)*</span></span> |
| ![디바이스 클래스 Pima 디바이스 정보 보내기 아이콘](./media/user-guide/usbx-events/image18.png)    | <span data-ttu-id="65356-144">**디바이스 클래스 Pima 디바이스 정보 보내기**(ux_device_class_pima_device_info_send)</span><span class="sxs-lookup"><span data-stu-id="65356-144">**Device Class Pima Device Info Send** *(ux_device_class_pima_device_info_send)*</span></span> |
| ![디바이스 클래스 Pima 이벤트 가져오기 아이콘](./media/user-guide/usbx-events/image19.png)    | <span data-ttu-id="65356-146">**디바이스 클래스 Pima 이벤트 가져오기**(ux_device_class_pima_event_get)</span><span class="sxs-lookup"><span data-stu-id="65356-146">**Device Class Pima Event Get** *(ux_device_class_pima_event_get)*</span></span> |
| ![디바이스 클래스 Pima 이벤트 설정 아이콘](./media/user-guide/usbx-events/image20.png)    | <span data-ttu-id="65356-148">**디바이스 클래스 Pima 이벤트 설정**(ux_device_class_pima_event_set)</span><span class="sxs-lookup"><span data-stu-id="65356-148">**Device Class Pima Event Set** *(ux_device_class_pima_event_set)*</span></span> |
| ![디바이스 클래스 Pima 개체 추가 아이콘](./media/user-guide/usbx-events/image21.png)    | <span data-ttu-id="65356-150">**디바이스 클래스 Pima 개체 추가**(ux_device_class_pima_object_add)</span><span class="sxs-lookup"><span data-stu-id="65356-150">**Device Class Pima Object Add** *(ux_device_class_pima_object_add)*</span></span> |
| ![디바이스 클래스 Pima 개체 데이터 가져오기 아이콘](./media/user-guide/usbx-events/image22.png)    | <span data-ttu-id="65356-152">**디바이스 클래스 Pima 개체 데이터 가져오기**(ux_device_class_pima_object_data_get)</span><span class="sxs-lookup"><span data-stu-id="65356-152">**Device Class Pima Object Data Get** *(ux_device_class_pima_object_data_get)*</span></span> |
| ![디바이스 클래스 Pima 개체 데이터 보내기 아이콘](./media/user-guide/usbx-events/image23.png)    | <span data-ttu-id="65356-154">**디바이스 클래스 Pima 개체 데이터 보내기**(ux_device_class_pima_object_data_send)</span><span class="sxs-lookup"><span data-stu-id="65356-154">**Device Class Pima Object Data Send** *(ux_device_class_pima_object_data_send)*</span></span> |
| ![디바이스 클래스 Pima 개체 삭제 아이콘](./media/user-guide/usbx-events/image24.png)    | <span data-ttu-id="65356-156">**디바이스 클래스 Pima 개체 삭제**(ux_device_class_pima_object_delete)</span><span class="sxs-lookup"><span data-stu-id="65356-156">**Device Class Pima Object Delete** *(ux_device_class_pima_object_delete)*</span></span> |
| ![디바이스 클래스 Pima 개체 핸들 보내기 아이콘](./media/user-guide/usbx-events/image25.png)    | <span data-ttu-id="65356-158">**디바이스 클래스 Pima 개체 핸들 보내기**(ux_device_class_pima_object_handles_send)</span><span class="sxs-lookup"><span data-stu-id="65356-158">**Device Class Pima Object Handles Send** *(ux_device_class_pima_object_handles_send)*</span></span> |
| ![디바이스 클래스 Pima 개체 정보 가져오기 아이콘](./media/user-guide/usbx-events/image26.png)    | <span data-ttu-id="65356-160">**디바이스 클래스 Pima 개체 정보 가져오기**(ux_device_class_pima_object_info_get)</span><span class="sxs-lookup"><span data-stu-id="65356-160">**Device Class Pima Object Info Get** *(ux_device_class_pima_object_info_get)*</span></span> |
| ![디바이스 클래스 Pima 개체 정보 보내기 아이콘](./media/user-guide/usbx-events/image27.png)    | <span data-ttu-id="65356-162">**디바이스 클래스 Pima 개체 정보 보내기**(ux_device_class_pima_object_info_send)</span><span class="sxs-lookup"><span data-stu-id="65356-162">**Device Class Pima Object Info Send** *(ux_device_class_pima_object_info_send)*</span></span> |
| ![디바이스 클래스 Pima 개체 번호 보내기 아이콘](./media/user-guide/usbx-events/image28.png)    | <span data-ttu-id="65356-164">**디바이스 클래스 Pima 개체 번호 보내기**(ux_device_class_pima_objects_number_send)</span><span class="sxs-lookup"><span data-stu-id="65356-164">**Device Class Pima Objects Number Send** *(ux_device_class_pima_objects_number_send)*</span></span> |
| ![디바이스 클래스 Pima 부분 개체 데이터 가져오기 아이콘](./media/user-guide/usbx-events/image29.png)    | <span data-ttu-id="65356-166">**디바이스 클래스 Pima 부분 개체 데이터 가져오기**(ux_device_class_pima_partial_object_data_get)</span><span class="sxs-lookup"><span data-stu-id="65356-166">**Device Class Pima Partial Object Data Get** *(ux_device_class_pima_partial_object_data_get)*</span></span> |
| ![디바이스 클래스 Pima 응답 보내기 아이콘](./media/user-guide/usbx-events/image30.png)    | <span data-ttu-id="65356-168">**디바이스 클래스 Pima 응답 보내기**(ux_device_class_pima_response_send)</span><span class="sxs-lookup"><span data-stu-id="65356-168">**Device Class Pima Response Send** *(ux_device_class_pima_response_send)*</span></span>|
| ![디바이스 클래스 Pima 스토리지 ID 보내기 아이콘](./media/user-guide/usbx-events/image31.png)    | <span data-ttu-id="65356-170">**디바이스 클래스 Pima 스토리지 ID 보내기**(ux_device_class_pima_storage_id_send)</span><span class="sxs-lookup"><span data-stu-id="65356-170">**Device Class Pima Storage Id Send** *(ux_device_class_pima_storage_id_send)*</span></span> |
| ![디바이스 클래스 Pima 스토리지 정보 보내기 아이콘](./media/user-guide/usbx-events/image32.png)    | <span data-ttu-id="65356-172">**디바이스 클래스 Pima 스토리지 정보 보내기**(ux_device_class_pima_storage_info_send)</span><span class="sxs-lookup"><span data-stu-id="65356-172">**Device Class Pima Storage Info Send** *(ux_device_class_pima_storage_info_send)*</span></span> |
| ![디바이스 클래스 RNDIS 활성화 아이콘](./media/user-guide/usbx-events/image33.png)    | <span data-ttu-id="65356-174">**디바이스 클래스 RNDIS 활성화**(ux_device_class_rndis_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-174">**Device Class Rndis Activate** *(ux_device_class_rndis_activate)*</span></span> |
| ![디바이스 클래스 RNDIS 비활성화 아이콘](./media/user-guide/usbx-events/image34.png)    | <span data-ttu-id="65356-176">**디바이스 클래스 RNDIS 비활성화**(ux_device_class_rndis_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-176">**Device Class Rndis Deactivate** *(ux_device_class_rndis_deactivate)*</span></span> |
| ![디바이스 클래스 RNDIS 메시지 유지 아이콘](./media/user-guide/usbx-events/image35.png)    | <span data-ttu-id="65356-178">**디바이스 클래스 RNDIS 메시지 유지**(ux_device_class_rndis_msg_keep_alive)</span><span class="sxs-lookup"><span data-stu-id="65356-178">**Device Class Rndis Message Keep Alive** *(ux_device_class_rndis_msg_keep_alive)*</span></span> |
| ![디바이스 클래스 RNDIS 메시지 쿼리 아이콘](./media/user-guide/usbx-events/image36.png)    | <span data-ttu-id="65356-180">**디바이스 클래스 RNDIS 메시지 쿼리**(ux_device_class_rndis_msg_query)</span><span class="sxs-lookup"><span data-stu-id="65356-180">**Device Class Rndis Message Query** *(ux_device_class_rndis_msg_query)*</span></span> |
| ![디바이스 클래스 RNDIS 메시지 재설정 아이콘](./media/user-guide/usbx-events/image37.png)    | <span data-ttu-id="65356-182">**디바이스 클래스 RNDIS 메시지 재설정**(ux_device_class_rndis_msg_reset)</span><span class="sxs-lookup"><span data-stu-id="65356-182">**Device Class Rndis Message Reset** *(ux_device_class_rndis_msg_reset)*</span></span> |
| ![디바이스 클래스 RNDIS 메시지 설정 아이콘](./media/user-guide/usbx-events/image38.png)    | <span data-ttu-id="65356-184">**디바이스 클래스 RNDIS 메시지 설정**(ux_device_class_rndis_msg_set)</span><span class="sxs-lookup"><span data-stu-id="65356-184">**Device Class Rndis Message Set** *(ux_device_class_rndis_msg_set)*</span></span> |
| ![디바이스 클래스 RNDIS 패킷 수신 아이콘](./media/user-guide/usbx-events/image39.png)    | <span data-ttu-id="65356-186">**디바이스 클래스 Rndis 패킷 수신**(ux_device_class_rndis_packet_receive)</span><span class="sxs-lookup"><span data-stu-id="65356-186">**Device Class Rndis Packet Receive** *(ux_device_class_rndis_packet_receive)*</span></span> |
| ![디바이스 클래스 RNDIS 패킷 전송 아이콘](./media/user-guide/usbx-events/image40.png)    | <span data-ttu-id="65356-188">**디바이스 클래스 RNDIS 패킷 전송**(ux_device_class_rndis_packet_transmit)</span><span class="sxs-lookup"><span data-stu-id="65356-188">**Device Class Rndis Packet Transmit** *(ux_device_class_rndis_packet_transmit)*</span></span> |
| ![디바이스 클래스 스토리지 활성화 아이콘](./media/user-guide/usbx-events/image41.png)    | <span data-ttu-id="65356-190">**디바이스 클래스 스토리지 활성화**(ux_device_class_storage_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-190">**Device Class Storage Activate** *(ux_device_class_storage_activate)*</span></span> |
| ![디바이스 클래스 스토리지 비활성화 아이콘](./media/user-guide/usbx-events/image42.png)    | <span data-ttu-id="65356-192">**디바이스 클래스 스토리지 비활성화**(ux_device_class_storage_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-192">**Device Class Storage Deactivate** *(ux_device_class_storage_deactivate)*</span></span> |
| ![디바이스 클래스 스토리지 형식 아이콘](./media/user-guide/usbx-events/image43.png)    | <span data-ttu-id="65356-194">**디바이스 클래스 스토리지 형식**(ux_device_class_storage_format)</span><span class="sxs-lookup"><span data-stu-id="65356-194">**Device Class Storage Format** *(ux_device_class_storage_format)*</span></span> |
| ![디바이스 클래스 스토리지 조회 아이콘](./media/user-guide/usbx-events/image44.png)    | <span data-ttu-id="65356-196">**디바이스 클래스 스토리지 조회**(ux_device_class_storage_inquiry)</span><span class="sxs-lookup"><span data-stu-id="65356-196">**Device Class Storage Inquiry** *(ux_device_class_storage_inquiry)*</span></span> |
| ![디바이스 클래스 스토리지 모드 선택 아이콘](./media/user-guide/usbx-events/image45.png)    | <span data-ttu-id="65356-198">**디바이스 클래스 스토리지 모드 선택**(ux_device_class_storage_mode_select)</span><span class="sxs-lookup"><span data-stu-id="65356-198">**Device Class Storage Mode Select** *(ux_device_class_storage_mode_select)*</span></span> |
| ![디바이스 클래스 스토리지 모드 센스 아이콘](./media/user-guide/usbx-events/image46.png)    | <span data-ttu-id="65356-200">**디바이스 클래스 스토리지 모드 센스**(ux_device_class_storage_mode_sense)</span><span class="sxs-lookup"><span data-stu-id="65356-200">**Device Class Storage Mode Sense** *(ux_device_class_storage_mode_sense)*</span></span> |
| ![디바이스 클래스 스토리지의 미디어 제거 방지 허용 아이콘](./media/user-guide/usbx-events/image47.png)    | <span data-ttu-id="65356-202">**디바이스 클래스 스토리지의 미디어 제거 방지 허용**(ux_device_class_storage_prevent_allow_media_removal)</span><span class="sxs-lookup"><span data-stu-id="65356-202">**Device Class Storage Prevent Allow Media Removal** *(ux_device_class_storage_prevent_allow_media_removal)*</span></span> |
| ![디바이스 클래스 스토리지 읽기 아이콘](./media/user-guide/usbx-events/image48.png)    | <span data-ttu-id="65356-204">**디바이스 클래스 스토리지 읽기**(ux_device_class_storage_read)</span><span class="sxs-lookup"><span data-stu-id="65356-204">**Device Class Storage Read** *(ux_device_class_storage_read)*</span></span> |
| ![디바이스 클래스 스토리지 읽기 용량 아이콘](./media/user-guide/usbx-events/image49.png)    | <span data-ttu-id="65356-206">**디바이스 클래스 스토리지 읽기 용량**(ux_device_class_storage_read_capacity)</span><span class="sxs-lookup"><span data-stu-id="65356-206">**Device Class Storage Read Capacity** *(ux_device_class_storage_read_capacity)*</span></span> |
| ![디바이스 클래스 스토리지 읽기 형식 용량 아이콘](./media/user-guide/usbx-events/image50.png)    | <span data-ttu-id="65356-208">**디바이스 클래스 스토리지 읽기 형식 용량**(ux_device_class_storage_read_format_capacity)</span><span class="sxs-lookup"><span data-stu-id="65356-208">**Device Class Storage Read Format Capacity** *(ux_device_class_storage_read_format_capacity)*</span></span> |
| ![디바이스 클래스 스토리지 TOC 읽기 아이콘](./media/user-guide/usbx-events/image51.png)    | <span data-ttu-id="65356-210">**디바이스 클래스 스토리지 TOC 읽기**(ux_device_class_storage_read_toc)</span><span class="sxs-lookup"><span data-stu-id="65356-210">**Device Class Storage Read TOC** *(ux_device_class_storage_read_toc)*</span></span> |
| ![디바이스 클래스 스토리지 요청 센스 아이콘](./media/user-guide/usbx-events/image52.png)    | <span data-ttu-id="65356-212">**디바이스 클래스 스토리지 요청 센스**(ux_device_class_storage_request_sense)</span><span class="sxs-lookup"><span data-stu-id="65356-212">**Device Class Storage Request Sense** *(ux_device_class_storage_request_sense)*</span></span> |
| ![디바이스 클래스 스토리지 시작 중지 아이콘](./media/user-guide/usbx-events/image53.png)    | <span data-ttu-id="65356-214">**디바이스 클래스 스토리지 시작 중지**(ux_device_class_storage_start_stop)</span><span class="sxs-lookup"><span data-stu-id="65356-214">**Device Class Storage Start Stop** *(ux_device_class_storage_start_stop)*</span></span> |
| ![디바이스 클래스 스토리지 테스트 준비 아이콘](./media/user-guide/usbx-events/image54.png)    | <span data-ttu-id="65356-216">**디바이스 클래스 스토리지 테스트 준비**(ux_device_class_storage_test_ready)</span><span class="sxs-lookup"><span data-stu-id="65356-216">**Device Class Storage Test Ready** *(ux_device_class_storage_test_ready)*</span></span> |
| ![디바이스 클래스 스토리지 확인 아이콘](./media/user-guide/usbx-events/image55.png)    | <span data-ttu-id="65356-218">**디바이스 클래스 스토리지 확인**(ux_device_class_storage_verify)</span><span class="sxs-lookup"><span data-stu-id="65356-218">**Device Class Storage Verify** *(ux_device_class_storage_verify)*</span></span> |
| ![디바이스 클래스 스토리지 쓰기 아이콘](./media/user-guide/usbx-events/image56.png)    | <span data-ttu-id="65356-220">**디바이스 클래스 스토리지 쓰기**(ux_device_class_storage_write)</span><span class="sxs-lookup"><span data-stu-id="65356-220">**Device Class Storage Write** *(ux_device_class_storage_write)*</span></span> |
| ![디바이스 스택 대체 설정 가져오기 아이콘](./media/user-guide/usbx-events/image57.png)    | <span data-ttu-id="65356-222">**디바이스 스택 대체 설정 가져오기**(ux_device_stack_alternate_setting_get)</span><span class="sxs-lookup"><span data-stu-id="65356-222">**Device Stack Alternate Setting Get** *(ux_device_stack_alternate_setting_get)*</span></span> |
| ![디바이스 스택 대체 설정 설정 아이콘](./media/user-guide/usbx-events/image58.png)    | <span data-ttu-id="65356-224">**디바이스 스택 대체 설정 설정**(ux_device_stack_alternate_setting_set)</span><span class="sxs-lookup"><span data-stu-id="65356-224">**Device Stack Alternate Setting Set** *(ux_device_stack_alternate_setting_set)*</span></span> |
| ![디바이스 스택 클래스 등록 아이콘](./media/user-guide/usbx-events/image59.png)    | <span data-ttu-id="65356-226">**디바이스 스택 클래스 등록**(ux_device_stack_class_register)</span><span class="sxs-lookup"><span data-stu-id="65356-226">**Device Stack Class Register** *(ux_device_stack_class_register)*</span></span> |
| ![디바이스 스택 지우기 기능 아이콘](./media/user-guide/usbx-events/image60.png)    | <span data-ttu-id="65356-228">**디바이스 스택 지우기 기능**(ux_device_stack_clear_feature)</span><span class="sxs-lookup"><span data-stu-id="65356-228">**Device Stack Clear Feature** *(ux_device_stack_clear_feature)*</span></span> |
| ![디바이스 스택 구성 가져오기 아이콘](./media/user-guide/usbx-events/image61.png)    | <span data-ttu-id="65356-230">**디바이스 스택 구성 가져오기**(ux_device_stack_configuration_get)</span><span class="sxs-lookup"><span data-stu-id="65356-230">**Device Stack Configuration Get** *(ux_device_stack_configuration_get)*</span></span> |
| ![디바이스 스택 구성 설정 아이콘](./media/user-guide/usbx-events/image62.png)    | <span data-ttu-id="65356-232">**디바이스 스택 구성 설정**(ux_device_stack_configuration_set)</span><span class="sxs-lookup"><span data-stu-id="65356-232">**Device Stack Configuration Set** *(ux_device_stack_configuration_set)*</span></span> |
| ![디바이스 스택 연결 아이콘](./media/user-guide/usbx-events/image63.png)    | <span data-ttu-id="65356-234">**디바이스 스택 연결** (ux_device_stack_connect)</span><span class="sxs-lookup"><span data-stu-id="65356-234">**Device Stack Connect** *(ux_device_stack_connect)*</span></span> |
| ![디바이스 스택 설명자 보내기 아이콘](./media/user-guide/usbx-events/image64.png)    | <span data-ttu-id="65356-236">**디바이스 스택 설명자 보내기**(ux_device_stack_descriptor_send)</span><span class="sxs-lookup"><span data-stu-id="65356-236">**Device Stack Descriptor Send** *(ux_device_stack_descriptor_send)*</span></span> |
| ![디바이스 스택 연결 끊기 아이콘](./media/user-guide/usbx-events/image65.png)    | <span data-ttu-id="65356-238">**디바이스 스택 연결 끊기**(ux_device_stack_disconnect)</span><span class="sxs-lookup"><span data-stu-id="65356-238">**Device Stack Disconnect** *(ux_device_stack_disconnect)*</span></span> |
| ![디바이스 스택 엔드포인트 정지 아이콘](./media/user-guide/usbx-events/image66.png)    | <span data-ttu-id="65356-240">**디바이스 스택 엔드포인트 정지**(ux_device_stack_endpoint_stall)</span><span class="sxs-lookup"><span data-stu-id="65356-240">**Device Stack Endpoint Stall** *(ux_device_stack_endpoint_stall)*</span></span> |
| ![디바이스 스택 상태 가져오기 아이콘](./media/user-guide/usbx-events/image67.png)    | <span data-ttu-id="65356-242">**디바이스 스택 상태 가져오기**(ux_device_stack_get_status)</span><span class="sxs-lookup"><span data-stu-id="65356-242">**Device Stack Get Status** *(ux_device_stack_get_status)*</span></span> |
| ![디바이스 스택 호스트 절전 모드 해제 아이콘](./media/user-guide/usbx-events/image68.png)    | <span data-ttu-id="65356-244">**디바이스 스택 호스트 절전 모드 해제**(ux_device_stack_host_wakeup)</span><span class="sxs-lookup"><span data-stu-id="65356-244">**Device Stack Host Wakeup** *(ux_device_stack_host_wakeup)*</span></span> |
| ![디바이스 스택 초기화 아이콘](./media/user-guide/usbx-events/image69.png)    | <span data-ttu-id="65356-246">**디바이스 스택 초기화** (ux_device_stack_initialize)</span><span class="sxs-lookup"><span data-stu-id="65356-246">**Device Stack Initialize** *(ux_device_stack_initialize)*</span></span> |
| ![디바이스 스택 인터페이스 삭제 아이콘](./media/user-guide/usbx-events/image70.png)    | <span data-ttu-id="65356-248">**디바이스 스택 인터페이스 삭제**(ux_device_stack_interface_delete)</span><span class="sxs-lookup"><span data-stu-id="65356-248">**Device Stack Interface Delete** *(ux_device_stack_interface_delete)*</span></span> |
| ![디바이스 스택 인터페이스 가져오기 아이콘](./media/user-guide/usbx-events/image71.png)    | <span data-ttu-id="65356-250">**디바이스 스택 인터페이스 가져오기**(ux_device_stack_interface_get)</span><span class="sxs-lookup"><span data-stu-id="65356-250">**Device Stack Interface Get** *(ux_device_stack_interface_get)*</span></span> |
| ![디바이스 스택 인터페이스 설정 아이콘](./media/user-guide/usbx-events/image72.png)    | <span data-ttu-id="65356-252">**디바이스 스택 인터페이스 설정**(ux_device_stack_interface_set)</span><span class="sxs-lookup"><span data-stu-id="65356-252">**Device Stack Interface Set** *(ux_device_stack_interface_set)*</span></span> |
| ![디바이스 스택 기능 설정 아이콘](./media/user-guide/usbx-events/image73.png)    | <span data-ttu-id="65356-254">**디바이스 스택 기능 설정**(ux_device_stack_set_feature)</span><span class="sxs-lookup"><span data-stu-id="65356-254">**Device Stack Set Feature** *(ux_device_stack_set_feature)*</span></span> |
| ![디바이스 스택 전송 중단 아이콘](./media/user-guide/usbx-events/image74.png)    | <span data-ttu-id="65356-256">**디바이스 스택 전송 중단**(ux_device_stack_transfer_abort)</span><span class="sxs-lookup"><span data-stu-id="65356-256">**Device Stack Transfer Abort** *(ux_device_stack_transfer_abort)*</span></span> |
| ![\*디바이스 스택 전송 모든 요청 중단 아이콘](./media/user-guide/usbx-events/image75.png)    | <span data-ttu-id="65356-258">**디바이스 스택 전송 모든 요청 중단**(ux_device_stack_transfer_all_request_abort)</span><span class="sxs-lookup"><span data-stu-id="65356-258">**Device Stack Transfer All Request Abort** *(ux_device_stack_transfer_all_request_abort)*</span></span> |
| ![디바이스 스택 전송 요청 아이콘](./media/user-guide/usbx-events/image76.png)    | <span data-ttu-id="65356-260">**디바이스 스택 전송 요청**(ux_device_stack_transfer_request)</span><span class="sxs-lookup"><span data-stu-id="65356-260">**Device Stack Transfer Request** *(ux_device_stack_transfer_request)*</span></span> |
| ![호스트 클래스 Asix 활성화 아이콘](./media/user-guide/usbx-events/image77.png)    | <span data-ttu-id="65356-262">**호스트 클래스 Asix 활성화**(ux_host_class_asix_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-262">**Host Class Asix Activate** *(ux_host_class_asix_activate)*</span></span> |
| ![호스트 클래스 Asix 비활성화 아이콘](./media/user-guide/usbx-events/image78.png)    | <span data-ttu-id="65356-264">**호스트 클래스 Asix 비활성화**(ux_host_class_asix_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-264">**Host Class Asix Deactivate** *(ux_host_class_asix_deactivate)*</span></span> |
| ![호스트 클래스 Asix 인터럽트 알림 아이콘](./media/user-guide/usbx-events/image79.png)    | <span data-ttu-id="65356-266">**호스트 클래스 Asix 인터럽트 알림**(ux_host_class_asix_interrupt_notification)</span><span class="sxs-lookup"><span data-stu-id="65356-266">**Host Class Asix Interrupt Notification** *(ux_host_class_asix_interrupt_notification)*</span></span> |
| ![호스트 클래스 Asix 읽기 아이콘](./media/user-guide/usbx-events/image80.png)    | <span data-ttu-id="65356-268">**호스트 클래스 Asix 읽기**(ux_host_class_asix_read)</span><span class="sxs-lookup"><span data-stu-id="65356-268">**Host Class Asix Read** *(ux_host_class_asix_read)*</span></span> |
| ![호스트 클래스 Asix 쓰기 아이콘](./media/user-guide/usbx-events/image81.png)    | <span data-ttu-id="65356-270">**호스트 클래스 Asix 쓰기**(ux_host_class_asix_write)</span><span class="sxs-lookup"><span data-stu-id="65356-270">**Host Class Asix Write** *(ux_host_class_asix_write)*</span></span> |
| ![호스트 클래스 오디오 활성화 아이콘](./media/user-guide/usbx-events/image82.png)    | <span data-ttu-id="65356-272">**호스트 클래스 오디오 활성화**(ux_host_class_audio_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-272">**Host Class Audio Activate** *(ux_host_class_audio_activate)*</span></span> |
| ![호스트 클래스 오디오 컨트롤 값 가져오기 아이콘](./media/user-guide/usbx-events/image83.png)    | <span data-ttu-id="65356-274">**호스트 클래스 오디오 컨트롤 값 가져오기**(ux_host_class_audio_control_value_get)</span><span class="sxs-lookup"><span data-stu-id="65356-274">**Host Class Audio Control Value Get** *(ux_host_class_audio_control_value_get)*</span></span> |
| ![호스트 클래스 오디오 컨트롤 값 설정 아이콘](./media/user-guide/usbx-events/image84.png)    | <span data-ttu-id="65356-276">**호스트 클래스 오디오 컨트롤 값 설정**(ux_host_class_audio_control_value_set)</span><span class="sxs-lookup"><span data-stu-id="65356-276">**Host Class Audio Control Value Set** *(ux_host_class_audio_control_value_set)*</span></span> |
| ![호스트 클래스 오디오 비활성화 아이콘](./media/user-guide/usbx-events/image85.png)    | <span data-ttu-id="65356-278">**호스트 클래스 오디오 비활성화**(ux_host_class_audio_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-278">**Host Class Audio Deactivate** *(ux_host_class_audio_deactivate)*</span></span> |
| ![호스트 클래스 오디오 읽기 아이콘](./media/user-guide/usbx-events/image86.png)    | <span data-ttu-id="65356-280">**호스트 클래스 오디오 읽기**(ux_host_class_audio_read)</span><span class="sxs-lookup"><span data-stu-id="65356-280">**Host Class Audio Read** *(ux_host_class_audio_read)*</span></span> |
| ![호스트 클래스 오디오 스트리밍 샘플링 가져오기 아이콘](./media/user-guide/usbx-events/image87.png)    | <span data-ttu-id="65356-282">**호스트 클래스 오디오 스트리밍 샘플링 가져오기**(ux_host_class_audio_streaming_sampling_get)</span><span class="sxs-lookup"><span data-stu-id="65356-282">**Host Class Audio Streaming Sampling Get** *(ux_host_class_audio_streaming_sampling_get)*</span></span> |
| ![호스트 클래스 오디오 스트리밍 샘플링 설정 아이콘](./media/user-guide/usbx-events/image88.png)    | <span data-ttu-id="65356-284">**호스트 클래스 오디오 스트리밍 샘플링 설정**(ux_host_class_audio_streaming_sampling_set)</span><span class="sxs-lookup"><span data-stu-id="65356-284">**Host Class Audio Streaming Sampling Set** *(ux_host_class_audio_streaming_sampling_set)*</span></span> |
| ![호스트 클래스 오디오 쓰기 아이콘](./media/user-guide/usbx-events/image89.png)    | <span data-ttu-id="65356-286">**호스트 클래스 오디오 쓰기**(ux_host_class_audio_write)</span><span class="sxs-lookup"><span data-stu-id="65356-286">**Host Class Audio Write** *(ux_host_class_audio_write)*</span></span> |
| ![호스트 클래스 CDC ACM 활성화 아이콘](./media/user-guide/usbx-events/image90.png)    | <span data-ttu-id="65356-288">**호스트 클래스 Cdc Acm 활성화**(ux_host_class_cdc_acm_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-288">**Host Class Cdc Acm Activate** *(ux_host_class_cdc_acm_activate)*</span></span> |
| ![호스트 클래스 CDC ACM 비활성화 아이콘](./media/user-guide/usbx-events/image91.png)    | <span data-ttu-id="65356-290">**호스트 클래스 Cdc Acm 비활성화**(ux_host_class_cdc_acm_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-290">**Host Class Cdc Acm Deactivate** *(ux_host_class_cdc_acm_deactivate)*</span></span> |
| ![호스트 클래스 CDC ACM IOCTL 파이프 내부 아이콘](./media/user-guide/usbx-events/image92.png)    | <span data-ttu-id="65356-292">**호스트 클래스 Cdc Acm Ioctl 파이프에서 중단**(ux_host_class_cdc_acm_ioctl_abort_in_pipe)</span><span class="sxs-lookup"><span data-stu-id="65356-292">**Host Class Cdc Acm Ioctl Abort In Pipe** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span></span> |
| ![호스트 클래스 Cdc Acm Ioctl 파이프 외부에서 중단 아이콘](./media/user-guide/usbx-events/image93.png)    | <span data-ttu-id="65356-294">**호스트 클래스 Cdc Acm Ioctl 파이프 외부에서 중단**(ux_host_class_cdc_acm_ioctl_abort_out_pipe)</span><span class="sxs-lookup"><span data-stu-id="65356-294">**Host Class Cdc Acm Ioctl Abort Out Pipe** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span></span> |
| ![호스트 클래스 Cdc Acm Ioctl 디바이스 상태 가져오기 아이콘](./media/user-guide/usbx-events/image94.png)    | <span data-ttu-id="65356-296">**호스트 클래스 Cdc Acm Ioctl 디바이스 상태 가져오기**(ux_host_class_cdc_acm_ioctl_get_device_status)</span><span class="sxs-lookup"><span data-stu-id="65356-296">**Host Class Cdc Acm Ioctl Get Device Status** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span></span> |
| ![호스트 클래스 Cdc Acm Ioctl 줄 코드 가져오기 아이콘](./media/user-guide/usbx-events/image95.png)    | <span data-ttu-id="65356-298">**호스트 클래스 Cdc Acm Ioctl 줄 코드 가져오기**(ux_host_class_cdc_acm_ioctl_get_line_coding)</span><span class="sxs-lookup"><span data-stu-id="65356-298">**Host Class Cdc Acm Ioctl Get Line Coding** *(ux_host_class_cdc_acm_ioctl_get_line_coding)*</span></span> |
| ![호스트 클래스 Cdc Acm Ioctl 알림 콜백 아이콘](./media/user-guide/usbx-events/image96.png)    | <span data-ttu-id="65356-300">**호스트 클래스 Cdc Acm Ioctl 알림 콜백**(ux_host_class_cdc_acm_ioctl_notification_callback)</span><span class="sxs-lookup"><span data-stu-id="65356-300">**Host Class Cdc Acm Ioctl Notification Callback** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span></span> |
| ![호스트 클래스 Cdc Acm Ioctl 보내기 중단 아이콘](./media/user-guide/usbx-events/image97.png)    | <span data-ttu-id="65356-302">**호스트 클래스 Cdc Acm Ioctl 보내기 중단**(ux_host_class_cdc_acm_ioctl_send_break)</span><span class="sxs-lookup"><span data-stu-id="65356-302">**Host Class Cdc Acm Ioctl Send Break** *(ux_host_class_cdc_acm_ioctl_send_break)*</span></span> |
| ![호스트 클래스 Cdc Acm Ioctl 줄 코드 설정 아이콘](./media/user-guide/usbx-events/image98.png)    | <span data-ttu-id="65356-304">**호스트 클래스 Cdc Acm Ioctl 줄 코드 설정**(ux_host_class_cdc_acm_ioctl_set_line_coding)</span><span class="sxs-lookup"><span data-stu-id="65356-304">**Host Class Cdc Acm Ioctl Set Line Coding** *(ux_host_class_cdc_acm_ioctl_set_line_coding)*</span></span> |
| ![호스트 클래스 Cdc Acm Ioctl 줄 상태 설정 아이콘](./media/user-guide/usbx-events/image99.png)    | <span data-ttu-id="65356-306">**호스트 클래스 Cdc Acm Ioctl 줄 상태 설정**(ux_host_class_cdc_acm_ioctl_set_line_state)</span><span class="sxs-lookup"><span data-stu-id="65356-306">**Host Class Cdc Acm Ioctl Set Line State** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span></span> |
| ![호스트 클래스 Cdc Acm 읽기 아이콘](./media/user-guide/usbx-events/image100.png)    | <span data-ttu-id="65356-308">**호스트 클래스 Cdc Acm 읽기**(ux_host_class_cdc_acm_read)</span><span class="sxs-lookup"><span data-stu-id="65356-308">**Host Class Cdc Acm Read** *(ux_host_class_cdc_acm_read)*</span></span> |
| ![호스트 클래스 Cdc Acm 수신 시작 아이콘](./media/user-guide/usbx-events/image101.png)    | <span data-ttu-id="65356-310">**호스트 클래스 Cdc Acm 수신 시작**(ux_host_class_cdc_acm_reception_start)</span><span class="sxs-lookup"><span data-stu-id="65356-310">**Host Class Cdc Acm Reception Start** *(ux_host_class_cdc_acm_reception_start)*</span></span> |
| ![호스트 클래스 Cdc Acm 수신 중지 아이콘](./media/user-guide/usbx-events/image102.png)    | <span data-ttu-id="65356-312">**호스트 클래스 Cdc Acm 수신 중지**(ux_host_class_cdc_acm_reception_stop)</span><span class="sxs-lookup"><span data-stu-id="65356-312">**Host Class Cdc Acm Reception Stop** *(ux_host_class_cdc_acm_reception_stop)*</span></span> |
| ![호스트 클래스 CDC ACM 쓰기 아이콘](./media/user-guide/usbx-events/image103.png)    | <span data-ttu-id="65356-314">**호스트 클래스 Cdc Acm 쓰기**(ux_host_class_cdc_acm_write)</span><span class="sxs-lookup"><span data-stu-id="65356-314">**Host Class Cdc Acm Write** *(ux_host_class_cdc_acm_write)*</span></span> |
| ![호스트 클래스 Dpump 활성화 아이콘](./media/user-guide/usbx-events/image104.png)    | <span data-ttu-id="65356-316">**호스트 클래스 Dpump 활성화**(ux_host_class_dpump_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-316">**Host Class Dpump Activate** *(ux_host_class_dpump_activate)*</span></span> |
| ![호스트 클래스 Dpump 비활성화 아이콘](./media/user-guide/usbx-events/image105.png)    | <span data-ttu-id="65356-318">**호스트 클래스 Dpump 비활성화**(ux_host_class_dpump_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-318">**Host Class Dpump Deactivate** *(ux_host_class_dpump_deactivate)*</span></span> |
| ![호스트 클래스 Dpump 읽기 아이콘](./media/user-guide/usbx-events/image106.png)    | <span data-ttu-id="65356-320">**호스트 클래스 Dpump 읽기**(ux_host_class_dpump_read)</span><span class="sxs-lookup"><span data-stu-id="65356-320">**Host Class Dpump Read** *(ux_host_class_dpump_read)*</span></span> |
| ![호스트 클래스 Dpump 쓰기 아이콘](./media/user-guide/usbx-events/image107.png)    | <span data-ttu-id="65356-322">**호스트 클래스 Dpump 쓰기**(ux_host_class_dpump_write)</span><span class="sxs-lookup"><span data-stu-id="65356-322">**Host Class Dpump Write** *(ux_host_class_dpump_write)*</span></span> |
| ![호스트 클래스 Hid 활성화 아이콘](./media/user-guide/usbx-events/image108.png)    | <span data-ttu-id="65356-324">**호스트 클래스 Hid 활성화**(ux_host_class_hid_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-324">**Host Class Hid Activate** *(ux_host_class_hid_activate)*</span></span> |
| ![호스트 클래스 Hid 클라이언트 등록 아이콘](./media/user-guide/usbx-events/image109.png)    | <span data-ttu-id="65356-326">**호스트 클래스 Hid 클라이언트 등록**(ux_host_class_hid_client_register)</span><span class="sxs-lookup"><span data-stu-id="65356-326">**Host Class Hid Client Register** *(ux_host_class_hid_client_register)*</span></span> |
| ![호스트 클래스 Hid 비활성화 아이콘](./media/user-guide/usbx-events/image110.png)    | <span data-ttu-id="65356-328">**호스트 클래스 Hid 비활성화**(ux_host_class_hid_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-328">**Host Class Hid Deactivate** *(ux_host_class_hid_deactivate)*</span></span> |
| ![호스트 클래스 Hid 유휴 가져오기 아이콘](./media/user-guide/usbx-events/image111.png)    | <span data-ttu-id="65356-330">**호스트 클래스 Hid 유휴 가져오기**(ux_host_class_hid_idle_get)</span><span class="sxs-lookup"><span data-stu-id="65356-330">**Host Class Hid Idle Get** *(ux_host_class_hid_idle_get)*</span></span> |
| ![호스트 클래스 Hid 유휴 설정 아이콘](./media/user-guide/usbx-events/image112.png)    | <span data-ttu-id="65356-332">**호스트 클래스 Hid 유휴 설정**(ux_host_class_hid_idle_set)</span><span class="sxs-lookup"><span data-stu-id="65356-332">**Host Class Hid Idle Set** *(ux_host_class_hid_idle_set)*</span></span> |
| ![호스트 클래스 Hid 키보드 활성화 아이콘](./media/user-guide/usbx-events/image113.png)    | <span data-ttu-id="65356-334">**호스트 클래스 Hid 키보드 활성화**(ux_host_class_hid_keyboard_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-334">**Host Class Hid Keyboard Activate** *(ux_host_class_hid_keyboard_activate)*</span></span> |
| ![호스트 클래스 Hid 키보드 비활성화 아이콘](./media/user-guide/usbx-events/image114.png)    | <span data-ttu-id="65356-336">**호스트 클래스 Hid 키보드 비활성화**(ux_host_class_hid_keyboard_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-336">**Host Class Hid Keyboard Deactivate** *(ux_host_class_hid_keyboard_deactivate)*</span></span> |
| ![호스트 클래스 Hid 마우스 활성화 아이콘](./media/user-guide/usbx-events/image115.png)    | <span data-ttu-id="65356-338">**호스트 클래스 Hid 마우스 비활성화**(ux_host_class_hid_mouse_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-338">**Host Class Hid Mouse Activate** *(ux_host_class_hid_mouse_activate)*</span></span> |
| ![호스트 클래스 Hid 마우스 비활성화 아이콘](./media/user-guide/usbx-events/image116.png)    | <span data-ttu-id="65356-340">**호스트 클래스 Hid 마우스 비활성화**(ux_host_class_hid_mouse_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-340">**Host Class Hid Mouse Deactivate** *(ux_host_class_hid_mouse_deactivate)*</span></span> |
| ![호스트 클래스 Hid 원격 제어 활성화 아이콘](./media/user-guide/usbx-events/image117.png)    | <span data-ttu-id="65356-342">**호스트 클래스 Hid 원격 제어 활성화**(ux_host_class_hid_remote_control_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-342">**Host Class Hid Remote Control Activate** *(ux_host_class_hid_remote_control_activate)*</span></span> |
| ![호스트 클래스 Hid 원격 제어 비활성화 아이콘](./media/user-guide/usbx-events/image118.png)    | <span data-ttu-id="65356-344">**호스트 클래스 Hid 원격 제어 비활성화**(ux_host_class_hid_remote_control_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-344">**Host Class Hid Remote Control Deactivate** *(ux_host_class_hid_remote_control_deactivate)*</span></span> |
| ![호스트 클래스 Hid 보고서 가져오기 아이콘](./media/user-guide/usbx-events/image119.png)    | <span data-ttu-id="65356-346">**호스트 클래스 Hid 보고서 가져오기**(ux_host_class_hid_report_get)</span><span class="sxs-lookup"><span data-stu-id="65356-346">**Host Class Hid Report Get** *(ux_host_class_hid_report_get)*</span></span> |
| ![호스트 클래스 Hid 보고서 설정 아이콘](./media/user-guide/usbx-events/image120.png)    | <span data-ttu-id="65356-348">**호스트 클래스 Hid 보고서 설정**(ux_host_class_hid_report_set)</span><span class="sxs-lookup"><span data-stu-id="65356-348">**Host Class Hid Report Set** *(ux_host_class_hid_report_set)*</span></span> |
| ![호스트 클래스 허브 활성화 아이콘](./media/user-guide/usbx-events/image121.png)    | <span data-ttu-id="65356-350">**호스트 클래스 허브 활성화**(ux_host_class_hub_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-350">**Host Class Hub Activate** *(ux_host_class_hub_activate)*</span></span> |
| ![호스트 클래스 허브 변경 검색 아이콘](./media/user-guide/usbx-events/image122.png)    | <span data-ttu-id="65356-352">**호스트 클래스 허브 변경 검색**(ux_host_class_hub_change_detect)</span><span class="sxs-lookup"><span data-stu-id="65356-352">**Host Class Hub Change Detect** *(ux_host_class_hub_change_detect)*</span></span> |
| ![\*호스트 클래스 허브 비활성화 아이콘](./media/user-guide/usbx-events/image123.png)    | <span data-ttu-id="65356-354">**호스트 클래스 허브 비활성화**(ux_host_class_hub_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-354">**Host Class Hub Deactivate** *(ux_host_class_hub_deactivate)*</span></span> |
| ![호스트 클래스 허브 포트 연결 변경 프로세스 아이콘](./media/user-guide/usbx-events/image124.png)    | <span data-ttu-id="65356-356">**호스트 클래스 허브 포트 연결 변경 프로세스**(ux_host_class_hub_port_change_connection_process)</span><span class="sxs-lookup"><span data-stu-id="65356-356">**Host Class Hub Port Change Connection Process** *(ux_host_class_hub_port_change_connection_process)*</span></span> |
| ![호스트 클래스 허브 포트 변경 사용 프로세스 아이콘](./media/user-guide/usbx-events/image125.png)    | <span data-ttu-id="65356-358">**호스트 클래스 허브 포트 변경 사용 프로세스**(ux_host_class_hub_port_change_enable_process)</span><span class="sxs-lookup"><span data-stu-id="65356-358">**Host Class Hub Port Change Enable Process** *(ux_host_class_hub_port_change_enable_process)*</span></span> |
| ![호스트 클래스 허브 포트 전환 현재 프로세스 아이콘](./media/user-guide/usbx-events/image126.png)    | <span data-ttu-id="65356-360">**호스트 클래스 허브 포트 전환 현재 프로세스**(ux_host_class_hub_port_change_over_current_process)</span><span class="sxs-lookup"><span data-stu-id="65356-360">**Host Class Hub Port Change Over Current Process** *(ux_host_class_hub_port_change_over_current_process)*</span></span> |
| ![호스트 클래스 허브 포트 변경 제설정 프로세스 아이콘](./media/user-guide/usbx-events/image127.png)    | <span data-ttu-id="65356-362">**호스트 클래스 허브 포트 변경 제설정 프로세스**(ux_host_class_hub_port_change_reset_process)</span><span class="sxs-lookup"><span data-stu-id="65356-362">**Host Class Hub Port Change Reset Process** *(ux_host_class_hub_port_change_reset_process)*</span></span> |
| ![호스트 클래스 허브 포트 변경 일시 중단 프로세스 아이콘](./media/user-guide/usbx-events/image128.png)    | <span data-ttu-id="65356-364">**호스트 클래스 허브 포트 변경 일시 중단 프로세스**(ux_host_class_hub_port_change_suspend_process)</span><span class="sxs-lookup"><span data-stu-id="65356-364">**Host Class Hub Port Change Suspend Process** *(ux_host_class_hub_port_change_suspend_process)*</span></span> |
| ![호스트 클래스 Pima 활성화 아이콘](./media/user-guide/usbx-events/image129.png)    | <span data-ttu-id="65356-366">**호스트 클래스 Pima 활성화**(ux_host_class_prima_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-366">**Host Class Pima Activate** *(ux_host_class_prima_activate)*</span></span> |
| ![호스트 클래스 Pima 비활성화 아이콘](./media/user-guide/usbx-events/image130.png)    | <span data-ttu-id="65356-368">**호스트 클래스 Pima 비활성화**(ux_host_class_pima_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-368">**Host Class Pima Deactivate** *(ux_host_class_pima_deactivate)*</span></span> |
| ![호스트 클래스 Pima 디바이스 정보 가져오기 아이콘](./media/user-guide/usbx-events/image131.png)    | <span data-ttu-id="65356-370">**호스트 클래스 Pima 디바이스 정보 가져오기**(ux_host_class_pima_device_info_get)</span><span class="sxs-lookup"><span data-stu-id="65356-370">**Host Class Pima Device Info Get** *(ux_host_class_pima_device_info_get)*</span></span> |
| ![호스트 클래스 Pima 디바이스 재설정 아이콘](./media/user-guide/usbx-events/image132.png)    | <span data-ttu-id="65356-372">**호스트 클래스 Pima 디바이스 재설정**(ux_host_class_pima_device_reset)</span><span class="sxs-lookup"><span data-stu-id="65356-372">**Host Class Pima Device Reset** *(ux_host_class_pima_device_reset)*</span></span> |
| ![호스트 클래스 Pima 알림 아이콘](./media/user-guide/usbx-events/image133.png)    | <span data-ttu-id="65356-374">**호스트 클래스 Pima 알림**(ux_host_class_pima_notification)</span><span class="sxs-lookup"><span data-stu-id="65356-374">**Host Class Pima Notification** *(ux_host_class_pima_notification)*</span></span> |
| ![호스트 클래스 Pima 숫자 개체 가져오기 아이콘](./media/user-guide/usbx-events/image134.png)    | <span data-ttu-id="65356-376">**호스트 클래스 Pima 숫자 개체 가져오기**(ux_host_class_pima_num_objects_get)</span><span class="sxs-lookup"><span data-stu-id="65356-376">**Host Class Pima Number Objects Get** *(ux_host_class_pima_num_objects_get)*</span></span> |
| ![호스트 클래스 Pima 개체 닫기 아이콘](./media/user-guide/usbx-events/image135.png)    | <span data-ttu-id="65356-378">**호스트 클래스 Pima 개체 닫기**(ux_host_class_pima_object_close)</span><span class="sxs-lookup"><span data-stu-id="65356-378">**Host Class Pima Object Close** *(ux_host_class_pima_object_close)*</span></span> |
| ![호스트 클래스 Pima 개체 복사 아이콘](./media/user-guide/usbx-events/image136.png)    | <span data-ttu-id="65356-380">**호스트 클래스 Pima 개체 복사**(ux_host_class_pima_object_copy)</span><span class="sxs-lookup"><span data-stu-id="65356-380">**Host Class Pima Object Copy** *(ux_host_class_pima_object_copy)*</span></span> |
| ![호스트 클래스 Pima 개체 삭제 아이콘](./media/user-guide/usbx-events/image137.png)    | <span data-ttu-id="65356-382">**호스트 클래스 Pima 개체 삭제**(ux_host_class_pima_object_delete)</span><span class="sxs-lookup"><span data-stu-id="65356-382">**Host Class Pima Object Delete** *(ux_host_class_pima_object_delete)*</span></span> |
| ![호스트 클래스 Pima 개체 가져오기 아이콘](./media/user-guide/usbx-events/image138.png)    | <span data-ttu-id="65356-384">**호스트 클래스 Pima 개체 가져오기**(ux_host_class_pima_object_get)</span><span class="sxs-lookup"><span data-stu-id="65356-384">**Host Class Pima Object Get** *(ux_host_class_pima_object_get)*</span></span> |
| ![호스트 클래스 Pima 개체 정보 가져오기 아이콘](./media/user-guide/usbx-events/image139.png)    | <span data-ttu-id="65356-386">**호스트 클래스 Pima 개체 정보 가져오기**(ux_host_class_pima_object_info_get)</span><span class="sxs-lookup"><span data-stu-id="65356-386">**Host Class Pima Object Info Get** *(ux_host_class_pima_object_info_get)*</span></span> |
| ![호스트 클래스 Pima 개체 정보 보내기 아이콘](./media/user-guide/usbx-events/image140.png)    | <span data-ttu-id="65356-388">**호스트 클래스 Pima 개체 정보 보내기**(ux_host_class_pima_object_info_send)</span><span class="sxs-lookup"><span data-stu-id="65356-388">**Host Class Pima Object Info Send** *(ux_host_class_pima_object_info_send)*</span></span> |
| ![호스트 클래스 Pima 개체 이동 아이콘](./media/user-guide/usbx-events/image141.png)    | <span data-ttu-id="65356-390">**호스트 클래스 Pima 개체 이동**(ux_host_class_pima_object_move)</span><span class="sxs-lookup"><span data-stu-id="65356-390">**Host Class Pima Object Move** *(ux_host_class_pima_object_move)*</span></span> |
| ![호스트 클래스 Pima 개체 보내기 아이콘](./media/user-guide/usbx-events/image142.png)    | <span data-ttu-id="65356-392">**호스트 클래스 Pima 개체 보내기**(ux_host_class_pima_object_send)</span><span class="sxs-lookup"><span data-stu-id="65356-392">**Host Class Pima Object Send** *(ux_host_class_pima_object_send)*</span></span> |
| ![호스트 클래스 Pima 개체 전송 중단 아이콘](./media/user-guide/usbx-events/image143.png)    | <span data-ttu-id="65356-394">**호스트 클래스 Pima 개체 전송 중단**(ux_host_class_object_transfer_abort)</span><span class="sxs-lookup"><span data-stu-id="65356-394">**Host Class Pima Object Transfer Abort** *(ux_host_class_object_transfer_abort)*</span></span> |
| ![호스트 클래스 Pima 읽기 아이콘](./media/user-guide/usbx-events/image144.png)    | <span data-ttu-id="65356-396">**호스트 클래스 Pima 읽기**(ux_host_class_pima_read)</span><span class="sxs-lookup"><span data-stu-id="65356-396">**Host Class Pima Read** *(ux_host_class_pima_read)*</span></span> |
| ![호스트 클래스 Pima 요청 취소 아이콘](./media/user-guide/usbx-events/image145.png)    | <span data-ttu-id="65356-398">**호스트 클래스 Pima 요청 취소**(ux_host_class_pima_request_cancel)</span><span class="sxs-lookup"><span data-stu-id="65356-398">**Host Class Pima Request Cancel** *(ux_host_class_pima_request_cancel)*</span></span> |
| ![호스트 클래스 Pima 세션 닫기 아이콘](./media/user-guide/usbx-events/image146.png)    | <span data-ttu-id="65356-400">**호스트 클래스 Pima 세션 닫기**(ux_host_class_pima_session_close)</span><span class="sxs-lookup"><span data-stu-id="65356-400">**Host Class Pima Session Close** *(ux_host_class_pima_session_close)*</span></span> |
| ![호스트 클래스 Pima 세션 열기 아이콘](./media/user-guide/usbx-events/image147.png)    | <span data-ttu-id="65356-402">**호스트 클래스 Pima 세션 열기**(ux_host_class_pima_session_open)</span><span class="sxs-lookup"><span data-stu-id="65356-402">**Host Class Pima Session Open** *(ux_host_class_pima_session_open)*</span></span> |
| ![호스트 클래스 Pima 스토리지 ID 가져오기 아이콘](./media/user-guide/usbx-events/image148.png)    | <span data-ttu-id="65356-404">**호스트 클래스 Pima 스토리지 ID 가져오기**(ux_host_class_pima_storage_ids_get)</span><span class="sxs-lookup"><span data-stu-id="65356-404">**Host Class Pima Storage Ids Get** *(ux_host_class_pima_storage_ids_get)*</span></span> |
| ![호스트 클래스 Pima 스토리지 가져오기 아이콘](./media/user-guide/usbx-events/image149.png)    | <span data-ttu-id="65356-406">**호스트 클래스 Pima 스토리지 가져오기**(ux_host_class_pima_storage_info_get)</span><span class="sxs-lookup"><span data-stu-id="65356-406">**Host Class Pima Storage Info Get** *(ux_host_class_pima_storage_info_get)*</span></span> |
| ![호스트 클래스 Pima Thumb 가져오기 아이콘](./media/user-guide/usbx-events/image150.png)    | <span data-ttu-id="65356-408">**호스트 클래스 Pima Thumb 가져오기**(ux_host_class_pima_thumb_get)</span><span class="sxs-lookup"><span data-stu-id="65356-408">**Host Class Pima Thumb Get** *(ux_host_class_pima_thumb_get)*</span></span> |
| ![호스트 클래스 Pima 쓰기 아이콘](./media/user-guide/usbx-events/image151.png)    | <span data-ttu-id="65356-410">**호스트 클래스 Pima 쓰기**(ux_host_class_pima_write)</span><span class="sxs-lookup"><span data-stu-id="65356-410">**Host Class Pima Write** *(ux_host_class_pima_write)*</span></span> |
| ![호스트 클래스 프린터 활성화 아이콘](./media/user-guide/usbx-events/image152.png)    | <span data-ttu-id="65356-412">**호스트 클래스 프린터 활성화**(ux_host_class_printer_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-412">**Host Class Printer Activate** *(ux_host_class_printer_activate)*</span></span> |
| ![호스트 클래스 프린터 비활성화 아이콘](./media/user-guide/usbx-events/image153.png)    | <span data-ttu-id="65356-414">**호스트 클래스 프린터 비활성화**(ux_host_class_printer_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-414">**Host Class Printer Deactivate** *(ux_host_class_printer_deactivate)*</span></span> |
| ![호스트 클래스 프린터 이름 가져오기 아이콘](./media/user-guide/usbx-events/image154.png)    | <span data-ttu-id="65356-416">**호스트 클래스 프린터 이름 가져오기**(ux_host_class_printer_name_get)</span><span class="sxs-lookup"><span data-stu-id="65356-416">**Host Class Printer Name Get** *(ux_host_class_printer_name_get)*</span></span> |
| ![호스트 클래스 프린터 읽기 아이콘](./media/user-guide/usbx-events/image155.png)    |  <span data-ttu-id="65356-418">**호스트 클래스 프린터 읽기**(ux_host_class_printer_read)</span><span class="sxs-lookup"><span data-stu-id="65356-418">**Host Class Printer Read** *(ux_host_class_printer_read)*</span></span> |
| ![호스트 클래스 프린터 소프트 리셋 아이콘](./media/user-guide/usbx-events/image156.png)    | <span data-ttu-id="65356-420">**호스트 클래스 프린터 소프트 리셋**(ux_host_class_printer_soft_reset)</span><span class="sxs-lookup"><span data-stu-id="65356-420">**Host Class Printer Soft Reset** *(ux_host_class_printer_soft_reset)*</span></span> |
| ![호스트 클래스 프린터 상태 가져오기 아이콘](./media/user-guide/usbx-events/image157.png)    | <span data-ttu-id="65356-422">**호스트 클래스 프린터 상태 가져오기**(ux_host_class_printer_status_get)</span><span class="sxs-lookup"><span data-stu-id="65356-422">**Host Class Printer Status Get** *(ux_host_class_printer_status_get)*</span></span> |
| ![호스트 클래스 프린터 쓰기 아이콘](./media/user-guide/usbx-events/image158.png)    | <span data-ttu-id="65356-424">**호스트 클래스 프린터 쓰기**(ux_host_class_printer_write)</span><span class="sxs-lookup"><span data-stu-id="65356-424">**Host Class Printer Write** *(ux_host_class_printer_write)*</span></span> |
| ![호스트 클래스 Prolific 활성화 아이콘](./media/user-guide/usbx-events/image159.png)    | <span data-ttu-id="65356-426">**호스트 클래스 Prolific 활성화**(ux_host_class_prolific_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-426">**Host Class Prolific Activate** *(ux_host_class_prolific_activate)*</span></span> |
| ![호스트 클래스 Prolific 비활성화 아이콘](./media/user-guide/usbx-events/image160.png)    | <span data-ttu-id="65356-428">**호스트 클래스 Prolific 비활성화**(ux_host_class_prolific_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-428">**Host Class Prolific Deactivate** *(ux_host_class_prolific_deactivate)*</span></span> |
| ![호스트 클래스 Prolific IOCTL 파이프에서 중단 아이콘](./media/user-guide/usbx-events/image161.png)    | <span data-ttu-id="65356-430">**호스트 클래스 Prolific IOCTL 파이프에서 중단**(ux_host_class_prolific_ioctl_abort_in_pipe)</span><span class="sxs-lookup"><span data-stu-id="65356-430">**Host Class Prolific Ioctl Abort In Pipe** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span></span> |
| ![호스트 클래스 Prolific IOCTL 파이프 외부에서 중단 아이콘](./media/user-guide/usbx-events/image162.png)    | <span data-ttu-id="65356-432">**호스트 클래스 Prolific IOCTL 파이프 외부에서 중단**(ux_host_class_prolific_ioctl_abort_out_pipe)</span><span class="sxs-lookup"><span data-stu-id="65356-432">**Host Class Prolific Ioctl Abort Out Pipe** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span></span> |
| ![호스트 클래스 Prolific IOCTL 디바이스 상태 가져오기 아이콘](./media/user-guide/usbx-events/image163.png)    | <span data-ttu-id="65356-434">**호스트 클래스 Prolific IOCTL 디바이스 상태 가져오기**(ux_host_class_prolific_ioctl_get_device_status)</span><span class="sxs-lookup"><span data-stu-id="65356-434">**Host Class Prolific Ioctl Get Device Status** *(ux_host_class_prolific_ioctl_get_device_status)*</span></span> |
| ![호스트 클래스 Prolific Ioctl 줄 코드 가져오기 아이콘](./media/user-guide/usbx-events/image164.png)    | <span data-ttu-id="65356-436">**호스트 클래스 Prolific Ioctl 줄 코드 가져오기**(ux_host_class_prolific_ioctl_get_line_coding)</span><span class="sxs-lookup"><span data-stu-id="65356-436">**Host Class Prolific Ioctl Get Line Coding** *(ux_host_class_prolific_ioctl_get_line_coding)*</span></span> |
| ![호스트 클래스 Prolific Ioctl 제거 아이콘](./media/user-guide/usbx-events/image165.png)    | <span data-ttu-id="65356-438">**호스트 클래스 Prolific Ioctl 제거**(ux_host_class_prolific_ioctl_purge)</span><span class="sxs-lookup"><span data-stu-id="65356-438">**Host Class Prolific Ioctl Purge** *(ux_host_class_prolific_ioctl_purge)*</span></span> |
| ![호스트 클래스 Prolific IOCTL 보고서 디바이스 상태 변경 아이콘](./media/user-guide/usbx-events/image166.png)    | <span data-ttu-id="65356-440">**호스트 클래스 Prolific IOCTL 보고서 디바이스 상태 변경**(ux_host_class_prolific_ioctl_report_device_status_change)</span><span class="sxs-lookup"><span data-stu-id="65356-440">**Host Class Prolific Ioctl Report Device Status Change** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span></span> |
| ![호스트 클래스 Prolific IOCTL 보내기 중단 아이콘](./media/user-guide/usbx-events/image167.png)    | <span data-ttu-id="65356-442">**호스트 클래스 Prolific IOCTL 보내기 중단**(ux_host_class_prolific_ioctl_send_break)</span><span class="sxs-lookup"><span data-stu-id="65356-442">**Host Class Prolific Ioctl Send Break** *(ux_host_class_prolific_ioctl_send_break)*</span></span> |
| ![호스트 클래스 Prolific Ioctl 줄 코드 설정 아이콘](./media/user-guide/usbx-events/image168.png)    | <span data-ttu-id="65356-444">**호스트 클래스 Prolific Ioctl 줄 코드 설정**(ux_host_class_prolific_ioctl_set_line_coding)</span><span class="sxs-lookup"><span data-stu-id="65356-444">**Host Class Prolific Ioctl Set Line Coding** *(ux_host_class_prolific_ioctl_set_line_coding)*</span></span> |
| ![호스트 클래스 Prolific Ioctl 줄 상태 설정 아이콘](./media/user-guide/usbx-events/image169.png)    | <span data-ttu-id="65356-446">**호스트 클래스 Prolific Ioctl 줄 상태 설정**(ux_host_class_prolific_ioctl_set_line_state)</span><span class="sxs-lookup"><span data-stu-id="65356-446">**Host Class Prolific Ioctl Set Line State** *(ux_host_class_prolific_ioctl_set_line_state)*</span></span> |
| ![호스트 클래스 Prolific 읽기 아이콘](./media/user-guide/usbx-events/image170.png)    | <span data-ttu-id="65356-448">**호스트 클래스 Prolific 읽기**(ux_host_class_prolific_read)</span><span class="sxs-lookup"><span data-stu-id="65356-448">**Host Class Prolific Read** *(ux_host_class_prolific_read)*</span></span> |
| ![호스트 클래스 Prolific 수신 시작 아이콘](./media/user-guide/usbx-events/image171.png)    | <span data-ttu-id="65356-450">**호스트 클래스 Prolific 수신 시작**(ux_host_class_prolific_reception_start)</span><span class="sxs-lookup"><span data-stu-id="65356-450">**Host Class Prolific Reception Start** *(ux_host_class_prolific_reception_start)*</span></span> |
| ![호스트 클래스 Prolific 수신 중지 아이콘](./media/user-guide/usbx-events/image172.png)    | <span data-ttu-id="65356-452">**호스트 클래스 Prolific 수신 중지**(ux_host_class_prolific_reception_stop)</span><span class="sxs-lookup"><span data-stu-id="65356-452">**Host Class Prolific Reception Stop** *(ux_host_class_prolific_reception_stop)*</span></span> |
| ![호스트 클래스 Prolific 쓰기 아이콘](./media/user-guide/usbx-events/image173.png)    | <span data-ttu-id="65356-454">**호스트 클래스 Prolific 쓰기**(ux_host_class_prolific_write)</span><span class="sxs-lookup"><span data-stu-id="65356-454">**Host Class Prolific Write** *(ux_host_class_prolific_write)*</span></span> |
| ![호스트 클래스 스토리지 활성화 아이콘](./media/user-guide/usbx-events/image174.png)    | <span data-ttu-id="65356-456">**호스트 클래스 스토리지 활성화**(ux_host_class_storage_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-456">**Host Class Storage Activate** *(ux_host_class_storage_activate)*</span></span> |
| ![호스트 클래스 스토리지 비활성화 아이콘](./media/user-guide/usbx-events/image175.png)    | <span data-ttu-id="65356-458">**호스트 클래스 스토리지 비활성화**(ux_host_class_storage_deactivate)</span><span class="sxs-lookup"><span data-stu-id="65356-458">**Host Class Storage Deactivate** (*ux_host_class_storage_deactivate)*</span></span> |
| ![호스트 클래스 스토리지 미디어 용량 가져오기 아이콘](./media/user-guide/usbx-events/image176.png)    | <span data-ttu-id="65356-460">**호스트 클래스 스토리지 미디어 용량 가져오기**(ux_host_class_storage_media_capacity_get)</span><span class="sxs-lookup"><span data-stu-id="65356-460">**Host Class Storage Media Capacity Get** *(ux_host_class_storage_media_capacity_get)*</span></span> |
| ![호스트 클래스 스토리지 미디어 형식 용량 가져오기 아이콘](./media/user-guide/usbx-events/image177.png)    | <span data-ttu-id="65356-462">**호스트 클래스 스토리지 미디어 형식 용량 가져오기**(ux_host_class_storage_media_format_capacity_get)</span><span class="sxs-lookup"><span data-stu-id="65356-462">**Host Class Storage Media Format Capacity Get** *(ux_host_class_storage_media_format_capacity_get)*</span></span> |
| ![호스트 클래스 스토리지 미디어 탑재 아이콘](./media/user-guide/usbx-events/image178.png)    | <span data-ttu-id="65356-464">**호스트 클래스 스토리지 미디어 탑재**(ux_host_class_storage_media_mount)\*</span><span class="sxs-lookup"><span data-stu-id="65356-464">**Host Class Storage Media Mount** (ux_host_class_storage_media_mount)\*</span></span> |
| ![호스트 클래스 스토리지 미디어 열기 아이콘](./media/user-guide/usbx-events/image179.png)    | <span data-ttu-id="65356-466">**호스트 클래스 스토리지 미디어 열기**(ux_host_class_storage_media_open)</span><span class="sxs-lookup"><span data-stu-id="65356-466">**Host Class Storage Media Open** *(ux_host_class_storage_media_open)*</span></span> |
| ![호스트 클래스 스토리지 미디어 읽기 아이콘](./media/user-guide/usbx-events/image180.png)    | <span data-ttu-id="65356-468">**호스트 클래스 스토리지 미디어 읽기**(ux_host_class_storage_media_read)</span><span class="sxs-lookup"><span data-stu-id="65356-468">**Host Class Storage Media Read** *(ux_host_class_storage_media_read)*</span></span> |
| ![호스트 클래스 스토리지 미디어 쓰기 아이콘](./media/user-guide/usbx-events/image181.png)    | <span data-ttu-id="65356-470">**호스트 클래스 스토리지 미디어 쓰기**(ux_host_class_storage_media_write)</span><span class="sxs-lookup"><span data-stu-id="65356-470">**Host Class Storage Media Write** *(ux_host_class_storage_media_write)*</span></span> |
| ![호스트 클래스 스토리지 요청 센스 아이콘](./media/user-guide/usbx-events/image182.png)    | <span data-ttu-id="65356-472">**호스트 클래스 스토리지 요청 센스**(ux_host_class_storage_request_sense)</span><span class="sxs-lookup"><span data-stu-id="65356-472">**Host Class Storage Request Sense** *(ux_host_class_storage_request_sense)*</span></span> |
| ![호스트 클래스 스토리지 시작 중지 아이콘](./media/user-guide/usbx-events/image183.png)    | <span data-ttu-id="65356-474">**호스트 클래스 스토리지 시작 중지**(ux_host_class_storage_start_stop)</span><span class="sxs-lookup"><span data-stu-id="65356-474">**Host Class Storage Start Stop** *(ux_host_class_storage_start_stop)*</span></span> |
| ![호스트 클래스 스토리지 장치 준비 테스트 아이콘](./media/user-guide/usbx-events/image184.png)    | <span data-ttu-id="65356-476">**호스트 클래스 스토리지 장치 준비 테스트**(ux_host_class_storage_activate)</span><span class="sxs-lookup"><span data-stu-id="65356-476">**Host Class Storage Unit Ready Test** *(ux_host_class_storage_activate)*</span></span> |
| ![호스트 스택 클래스 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image185.png)    | <span data-ttu-id="65356-478">**호스트 스택 클래스 인스턴스 만들기**(ux_host_stack_class_instance_create)</span><span class="sxs-lookup"><span data-stu-id="65356-478">**Host Stack Class Instance Create** *(ux_host_stack_class_instance_create)*</span></span> |
| ![호스트 스택 클래스 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image186.png)    | <span data-ttu-id="65356-480">**호스트 스택 클래스 인스턴스 삭제**(ux_host_stack_class_instance_destroy)</span><span class="sxs-lookup"><span data-stu-id="65356-480">**Host Stack Class Instance Destroy** *(ux_host_stack_class_instance_destroy)*</span></span> |
| ![호스트 스택 구성 삭제 아이콘](./media/user-guide/usbx-events/image187.png)    | <span data-ttu-id="65356-482">**호스트 스택 구성 삭제**(ux_host_stack_configuration_delete)</span><span class="sxs-lookup"><span data-stu-id="65356-482">**Host Stack Configuration Delete** *(ux_host_stack_configuration_delete)*</span></span> |
| ![호스트 스택 구성 열거 아이콘](./media/user-guide/usbx-events/image188.png)    | <span data-ttu-id="65356-484">**호스트 스택 구성 열거**(ux_host_stack_configuration_enumerate)</span><span class="sxs-lookup"><span data-stu-id="65356-484">**Host Stack Configuration Enumerate** *(ux_host_stack_configuration_enumerate)*</span></span> |
| ![호스트 스택 구성 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image189.png)    | <span data-ttu-id="65356-486">**호스트 스택 구성 인스턴스 만들기**(ux_host_stack_configuration_instance_create)</span><span class="sxs-lookup"><span data-stu-id="65356-486">**Host Stack Configuration Instance Create** *(ux_host_stack_configuration_instance_create)*</span></span> |
| ![호스트 스택 구성 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image190.png)    | <span data-ttu-id="65356-488">**호스트 스택 구성 인스턴스 삭제**(ux_host_stack_configuration_instance_delete)</span><span class="sxs-lookup"><span data-stu-id="65356-488">**Host Stack Configuration Instance Delete** *(ux_host_stack_configuration_instance_delete)*</span></span> |
| ![호스트 스택 구성 설정 아이콘](./media/user-guide/usbx-events/image191.png)    | <span data-ttu-id="65356-490">**호스트 스택 구성 설정**(ux_host_stack_configuration_set)</span><span class="sxs-lookup"><span data-stu-id="65356-490">**Host Stack Configuration Set** *(ux_host_stack_configuration_set)*</span></span> |
| ![호스트 스택 디바이스 주소 설정 아이콘](./media/user-guide/usbx-events/image192.png)    | <span data-ttu-id="65356-492">**호스트 스택 디바이스 주소 설정**(ux_host_stack_device_set)</span><span class="sxs-lookup"><span data-stu-id="65356-492">**Host Stack Device Address Set** *(ux_host_stack_device_set)*</span></span> |
| ![호스트 스택 디바이스 구성 가져오기 아이콘](./media/user-guide/usbx-events/image193.png)    | <span data-ttu-id="65356-494">**호스트 스택 디바이스 구성 가져오기**(ux_host_stack_device_configuration_get)</span><span class="sxs-lookup"><span data-stu-id="65356-494">**Host Stack Device Configuration Get** *(ux_host_stack_device_configuration_get)*</span></span> |
| ![호스트 스택 디바이스 구성 선택 아이콘](./media/user-guide/usbx-events/image194.png)    | <span data-ttu-id="65356-496">**호스트 스택 디바이스 구성 선택**(ux_host_stack_device_configuration_select)</span><span class="sxs-lookup"><span data-stu-id="65356-496">**Host Stack Device Configuration Select** *(ux_host_stack_device_configuration_select)*</span></span> |
| ![호스트 스택 디바이스 설명자 읽기 아이콘](./media/user-guide/usbx-events/image195.png)    | <span data-ttu-id="65356-498">**호스트 스택 디바이스 설명자 읽기**(ux_host_stack_device_descriptor_read)</span><span class="sxs-lookup"><span data-stu-id="65356-498">**Host Stack Device Descriptor Read** *(ux_host_stack_device_descriptor_read)*</span></span> |
| ![호스트 스택 디바이스 가져오기 아이콘](./media/user-guide/usbx-events/image196.png)    | <span data-ttu-id="65356-500">**호스트 스택 디바이스 가져오기**(ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="65356-500">**Host Stack Device Get** (ux_host_stack_device_get)</span></span> |
| ![호스트 스택 디바이스 제거 아이콘](./media/user-guide/usbx-events/image197.png)    | <span data-ttu-id="65356-502">**호스트 스택 디바이스 제거**(ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="65356-502">**Host Stack Device Remove** (ux_host_stack_device_get)</span></span> |
| ![호스트 스택 디바이스 리소스 해제 아이콘](./media/user-guide/usbx-events/image198.png)    | <span data-ttu-id="65356-504">**호스트 스택 디바이스 리소스 해제**(ux_host_stack_device_resource_free)</span><span class="sxs-lookup"><span data-stu-id="65356-504">**Host Stack Device Resource Free** (ux_host_stack_device_resource_free)</span></span> |
| ![호스트 스택 엔드포인트 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image199.png)    | <span data-ttu-id="65356-506">**호스트 스택 엔드포인트 인스턴스 만들기**(ux_host_stack_endpoint_instance_create)</span><span class="sxs-lookup"><span data-stu-id="65356-506">**Host Stack Endpoint Instance Create** (ux_host_stack_endpoint_instance_create)</span></span> |
| ![호스트 스택 엔드포인트 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image200.png)    | <span data-ttu-id="65356-508">**호스트 스택 엔드포인트 인스턴스 삭제**(ux_host_stack_endpoint_instance_delete)</span><span class="sxs-lookup"><span data-stu-id="65356-508">**Host Stack Endpoint Instance Delete** (ux_host_stack_endpoint_instance_delete)</span></span> |
| ![호스트 스택 엔드포인트 재설정 아이콘](./media/user-guide/usbx-events/image201.png)    | <span data-ttu-id="65356-510">**호스트 스택 엔드포인트 재설정**(ux_host_stack_endpoint_reset)</span><span class="sxs-lookup"><span data-stu-id="65356-510">**Host Stack Endpoint Reset** (ux_host_stack_endpoint_reset)</span></span> |
| ![호스트 스택 엔드포인트 전송 중단 아이콘](./media/user-guide/usbx-events/image202.png)    | <span data-ttu-id="65356-512">**호스트 스택 엔드포인트 전송 중단**(ux_host_stack_endpoint_transfer_abort)</span><span class="sxs-lookup"><span data-stu-id="65356-512">**Host Stack Endpoint Transfer Abort** (ux_host_stack_endpoint_transfer_abort)</span></span> |
| ![호스트 스택 호스트 컨트롤러 등록 아이콘](./media/user-guide/usbx-events/image203.png)    | <span data-ttu-id="65356-514">**호스트 스택 호스트 컨트롤러 등록**(ux_host_stack_hcd_register)</span><span class="sxs-lookup"><span data-stu-id="65356-514">**Host Stack Host Controller Register** *(ux_host_stack_hcd_register)*</span></span> |
| ![호스트 스택 초기화 아이콘](./media/user-guide/usbx-events/image204.png)    | <span data-ttu-id="65356-516">**호스트 스택 초기화**(ux_host_stack_initialize)</span><span class="sxs-lookup"><span data-stu-id="65356-516">**Host Stack Initialize** *(ux_host_stack_initialize)*</span></span> |
| ![호스트 스택 인터페이스 엔드포인트 가져오기 아이콘](./media/user-guide/usbx-events/image205.png)    | <span data-ttu-id="65356-518">**호스트 스택 인터페이스 엔드포인트 가져오기**(ux_host_stack_interface_endpoint_get)</span><span class="sxs-lookup"><span data-stu-id="65356-518">**Host Stack Interface Endpoint Get** *(ux_host_stack_interface_endpoint_get)*</span></span> |
| ![호스트 스택 인터페이스 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image206.png)    | <span data-ttu-id="65356-520">**호스트 스택 인터페이스 인스턴스 만들기**(ux_host_stack_interface_instance_create)</span><span class="sxs-lookup"><span data-stu-id="65356-520">**Host Stack Interface Instance Create** *(ux_host_stack_interface_instance_create)*</span></span> |
| ![호스트 스택 인터페이스 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image207.png)    | <span data-ttu-id="65356-522">**호스트 스택 인터페이스 인스턴스 삭제**(ux_host_stack_interface_instance_delete)</span><span class="sxs-lookup"><span data-stu-id="65356-522">**Host Stack Interface Instance Delete** *(ux_host_stack_interface_instance_delete)*</span></span> |
| ![호스트 스택 인터페이스 설정 아이콘](./media/user-guide/usbx-events/image208.png)    | <span data-ttu-id="65356-524">**호스트 스택 인터페이스 설정**(ux_host_stack_interface_set)</span><span class="sxs-lookup"><span data-stu-id="65356-524">**Host Stack Interface Set** *(ux_host_stack_interface_set)*</span></span> |
| ![호스트 스택 인터페이스 설정 선택 아이콘](./media/user-guide/usbx-events/image209.png)    | <span data-ttu-id="65356-526">**호스트 스택 인터페이스 설정 선택**(ux_host_stack_interface_setting_select)</span><span class="sxs-lookup"><span data-stu-id="65356-526">**Host Stack Interface Setting Select** *(ux_host_stack_interface_setting_select)*</span></span> |
| ![호스트 스택 새 구성 만들기 아이콘](./media/user-guide/usbx-events/image210.png)    | <span data-ttu-id="65356-528">**호스트 스택 새 구성 만들기**(ux_host_stack_new_configuration_create)</span><span class="sxs-lookup"><span data-stu-id="65356-528">**Host Stack New Configuration Create** *(ux_host_stack_new_configuration_create)*</span></span> |
| ![호스트 스택 새 디바이스 만들기 아이콘](./media/user-guide/usbx-events/image211.png)    | <span data-ttu-id="65356-530">**호스트 스택 새 디바이스 만들기**(ux_host_stack_new_device_create)</span><span class="sxs-lookup"><span data-stu-id="65356-530">**Host Stack New Device Create** *(ux_host_stack_new_device_create)*</span></span> |
| ![호스트 스택 새 엔드포인트 만들기 아이콘](./media/user-guide/usbx-events/image212.png)    | <span data-ttu-id="65356-532">**호스트 스택 새 엔드포인트 만들기**(ux_host_stack_new_endpoint_create)</span><span class="sxs-lookup"><span data-stu-id="65356-532">**Host Stack New Endpoint Create** *(ux_host_stack_new_endpoint_create)*</span></span> |
| ![호스트 스택 루트 허브 변경 프로세스 아이콘](./media/user-guide/usbx-events/image213.png)    | <span data-ttu-id="65356-534">**호스트 스택 루트 허브 변경 프로세스**(ux_host_stack_rh_change_process)</span><span class="sxs-lookup"><span data-stu-id="65356-534">**Host Stack Root Hub Change Process** *(ux_host_stack_rh_change_process)*</span></span> |
| ![호스트 스택 루트 허브 디바이스 추출 아이콘](./media/user-guide/usbx-events/image214.png)    | <span data-ttu-id="65356-536">**호스트 스택 루트 허브 디바이스 추출**(ux_host_stack_rh_device_extraction)</span><span class="sxs-lookup"><span data-stu-id="65356-536">**Host Stack Root Hub Device Extraction** *(ux_host_stack_rh_device_extraction)*</span></span> |
| ![호스트 스택 루트 허브 디바이스 삽입 아이콘](./media/user-guide/usbx-events/image215.png)    | <span data-ttu-id="65356-538">**호스트 스택 루트 허브 디바이스 삽입**(ux_host_stack_rh_device_insertion)</span><span class="sxs-lookup"><span data-stu-id="65356-538">**Host Stack Root Hub Device Insertion** *(ux_host_stack_rh_device_insertion)*</span></span> |
| ![호스트 스택 전송 요청 아이콘](./media/user-guide/usbx-events/image216.png)    | <span data-ttu-id="65356-540">**호스트 스택 전송 요청**(ux_host_stack_transfer_request)</span><span class="sxs-lookup"><span data-stu-id="65356-540">**Host Stack Transfer Request** *(ux_host_stack_transfer_request)*</span></span> |
| ![호스트 스택 전송 요청 중단 아이콘](./media/user-guide/usbx-events/image217.png)    | <span data-ttu-id="65356-542">**호스트 스택 전송 요청 중단**(ux_host_stack_transfer_request_abort)</span><span class="sxs-lookup"><span data-stu-id="65356-542">**Host Stack Transfer Request Abort** *(ux_host_stack_transfer_request_abort)*</span></span> |
| ![U S B X 오류 아이콘](./media/user-guide/usbx-events/image218.png)    | <span data-ttu-id="65356-544">**USBX 오류**(ux_error)</span><span class="sxs-lookup"><span data-stu-id="65356-544">**USBX Error** *(ux_error)*</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="65356-545">이벤트 설명</span><span class="sxs-lookup"><span data-stu-id="65356-545">Event Descriptions</span></span>

<span data-ttu-id="65356-546">다음 페이지에서는 USBX 추적 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="65356-546">The following pages describe the USBX Trace Events.</span></span>

### <a name="device-class-cdc-activate"></a><span data-ttu-id="65356-547">디바이스 클래스 Cdc 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-547">Device Class Cdc Activate</span></span> 

#### <a name="ux_device_class_cdc_activate"></a><span data-ttu-id="65356-548">ux_device_class_cdc_activate</span><span class="sxs-lookup"><span data-stu-id="65356-548">ux_device_class_cdc_activate</span></span>

<span data-ttu-id="65356-549">**아이콘** ![디바이스 클래스 C D C 활성화 아이콘](./media/user-guide/usbx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="65356-549">**Icon** ![Device Class C D C Activate icon](./media/user-guide/usbx-events/image1.png)</span></span>

<span data-ttu-id="65356-550">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-550">**Description**</span></span>

<span data-ttu-id="65356-551">이 이벤트는 USBX 디바이스 클래스 Cdc 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-551">This event represents a USBX Device Class Cdc Activate Event.</span></span>

<span data-ttu-id="65356-552">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-552">**Information Fields**</span></span> 

- <span data-ttu-id="65356-553">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-553">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-554">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-554">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-555">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-555">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-556">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-556">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-deactivate"></a><span data-ttu-id="65356-557">디바이스 클래스 Cdc 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-557">Device Class Cdc Deactivate</span></span> 

#### <a name="ux_device_class_cdc_deactivate"></a><span data-ttu-id="65356-558">ux_device_class_cdc_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-558">ux_device_class_cdc_deactivate</span></span>

<span data-ttu-id="65356-559">**아이콘** ![디바이스 클래스 C D C 비활성화 아이콘](./media/user-guide/usbx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="65356-559">**Icon** ![Device Class C D C Deactivate icon](./media/user-guide/usbx-events/image2.png)</span></span>

<span data-ttu-id="65356-560">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-560">**Description**</span></span>

<span data-ttu-id="65356-561">이 이벤트는 USBX 디바이스 클래스 Cdc 비활성화를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-561">This event represents a USBX Device Class Cdc Deactivate.</span></span>

<span data-ttu-id="65356-562">정보 필드</span><span class="sxs-lookup"><span data-stu-id="65356-562">Information Fields</span></span> 

- <span data-ttu-id="65356-563">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-563">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-564">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-564">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-565">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-565">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-566">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-566">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-read"></a><span data-ttu-id="65356-567">디바이스 클래스 Cdc 읽기</span><span class="sxs-lookup"><span data-stu-id="65356-567">Device Class Cdc Read</span></span> 

#### <a name="ux_device_class_cdc_read"></a><span data-ttu-id="65356-568">ux_device_class_cdc_read</span><span class="sxs-lookup"><span data-stu-id="65356-568">ux_device_class_cdc_read</span></span>

<span data-ttu-id="65356-569">**아이콘** ![디바이스 클래스 C D C 읽기 아이콘](./media/user-guide/usbx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="65356-569">**Icon** ![Device Class C D C Read icon](./media/user-guide/usbx-events/image3.png)</span></span>

<span data-ttu-id="65356-570">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-570">**Description**</span></span>

<span data-ttu-id="65356-571">이 이벤트는 USBX 디바이스 클래스 Cdc 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-571">This event represents a USBX Device Class Cdc Read Event.</span></span>

<span data-ttu-id="65356-572">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-572">**Information Fields**</span></span>

- <span data-ttu-id="65356-573">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-573">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-574">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-574">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-575">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-575">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-576">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-576">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-write"></a><span data-ttu-id="65356-577">디바이스 클래스 Cdc 쓰기</span><span class="sxs-lookup"><span data-stu-id="65356-577">Device Class Cdc Write</span></span> 

#### <a name="ux_device_class_cdc_write"></a><span data-ttu-id="65356-578">ux_device_class_cdc_write</span><span class="sxs-lookup"><span data-stu-id="65356-578">ux_device_class_cdc_write</span></span>

<span data-ttu-id="65356-579">**아이콘** ![디바이스 클래스 C D C 쓰기 아이콘](./media/user-guide/usbx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="65356-579">**Icon** ![Device Class C D C Write icon](./media/user-guide/usbx-events/image4.png)</span></span>

<span data-ttu-id="65356-580">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-580">**Description**</span></span>

<span data-ttu-id="65356-581">이 이벤트는 USBX 디바이스 클래스 Cdc 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-581">This event represents a USBX Device Class Cdc Write Event.</span></span>

<span data-ttu-id="65356-582">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-582">**Information Fields**</span></span>

- <span data-ttu-id="65356-583">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-583">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-584">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-584">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-585">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-585">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-586">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-586">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-activate"></a><span data-ttu-id="65356-587">디바이스 클래스 Dpump 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-587">Device Class Dpump Activate</span></span> 

#### <a name="ux_device_class_dpump_activate"></a><span data-ttu-id="65356-588">ux_device_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="65356-588">ux_device_class_dpump_activate</span></span>

<span data-ttu-id="65356-589">**아이콘**![디바이스 클래스 Dpump 활성화 아이콘](./media/user-guide/usbx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="65356-589">**Icon** ![Device Class Dpump Activate icon](./media/user-guide/usbx-events/image5.png)</span></span>

<span data-ttu-id="65356-590">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-590">**Description**</span></span>

<span data-ttu-id="65356-591">이 이벤트는 USBX 디바이스 클래스 Dpump 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-591">This event represents a USBX Device Class Dpump Activate Event.</span></span>

<span data-ttu-id="65356-592">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-592">**Information Fields**</span></span>

- <span data-ttu-id="65356-593">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-593">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-594">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-594">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-595">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-595">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-596">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-596">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-deactivate"></a><span data-ttu-id="65356-597">디바이스 클래스 Dpump 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-597">Device Class Dpump Deactivate</span></span> 

#### <a name="ux_device_class_dpump_deactivate"></a><span data-ttu-id="65356-598">ux_device_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-598">ux_device_class_dpump_deactivate</span></span>

<span data-ttu-id="65356-599">**아이콘** ![디바이스 클래스 Dpump 비활성화 아이콘](./media/user-guide/usbx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="65356-599">**Icon** ![Device Class Dpump Deactivate icon](./media/user-guide/usbx-events/image6.png)</span></span>

<span data-ttu-id="65356-600">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-600">**Description**</span></span>

<span data-ttu-id="65356-601">이 이벤트는 USBX 디바이스 클래스 Dpump 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-601">This event represents a USBX Device Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="65356-602">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-602">**Information Fields**</span></span> 

- <span data-ttu-id="65356-603">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-603">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-604">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-604">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-605">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-605">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-606">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-606">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-read"></a><span data-ttu-id="65356-607">디바이스 클래스 Dpump 읽기</span><span class="sxs-lookup"><span data-stu-id="65356-607">Device Class Dpump Read</span></span> 

#### <a name="ux_device_class_dpump_read"></a><span data-ttu-id="65356-608">ux_device_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="65356-608">ux_device_class_dpump_read</span></span>

<span data-ttu-id="65356-609">**아이콘** ![디바이스 클래스 Dpump 읽기 아이콘](./media/user-guide/usbx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="65356-609">**Icon** ![Device Class Dpump Read icon](./media/user-guide/usbx-events/image7.png)</span></span>

<span data-ttu-id="65356-610">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-610">**Description**</span></span>

<span data-ttu-id="65356-611">이 이벤트는 USBX 디바이스 클래스 Dpump 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-611">This event represents a USBX Device Class Dpump Read Event.</span></span>

<span data-ttu-id="65356-612">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-612">**Information Fields**</span></span>

- <span data-ttu-id="65356-613">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-613">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-614">정보 필드 2: 버퍼</span><span class="sxs-lookup"><span data-stu-id="65356-614">Info Field 2: Buffer.</span></span>
- <span data-ttu-id="65356-615">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-615">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-616">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-616">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-write"></a><span data-ttu-id="65356-617">디바이스 클래스 Dpump 쓰기</span><span class="sxs-lookup"><span data-stu-id="65356-617">Device Class Dpump Write</span></span> 

#### <a name="ux_device_class_dpump_write"></a><span data-ttu-id="65356-618">ux_device_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="65356-618">ux_device_class_dpump_write</span></span>

<span data-ttu-id="65356-619">**아이콘** ![디바이스 클래스 Dpump 쓰기 아이콘](./media/user-guide/usbx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="65356-619">**Icon** ![Device Class Dpump Write icon](./media/user-guide/usbx-events/image8.png)</span></span>

<span data-ttu-id="65356-620">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-620">**Description**</span></span>

<span data-ttu-id="65356-621">이 이벤트는 USBX 디바이스 클래스 Dpump 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-621">This event represents a USBX Device Class Dpump Write Event.</span></span>

<span data-ttu-id="65356-622">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-622">**Information Fields**</span></span>

- <span data-ttu-id="65356-623">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-623">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-624">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-624">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-625">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-625">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-626">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-626">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-activate"></a><span data-ttu-id="65356-627">디바이스 클래스 Hid 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-627">Device Class Hid Activate</span></span> 

#### <a name="ux_device_class_hid_activate"></a><span data-ttu-id="65356-628">ux_device_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="65356-628">ux_device_class_hid_activate</span></span>

<span data-ttu-id="65356-629">**아이콘** ![디바이스 클래스 Hid 활성화 아이콘](./media/user-guide/usbx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="65356-629">**Icon** ![Device Class Hid Activate icon](./media/user-guide/usbx-events/image9.png)</span></span>

<span data-ttu-id="65356-630">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-630">**Description**</span></span>

<span data-ttu-id="65356-631">이 이벤트는 USBX 디바이스 클래스 Hid 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-631">This event represents a USBX Device Class Hid Activate Event.</span></span>

<span data-ttu-id="65356-632">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-632">**Information Fields**</span></span>

- <span data-ttu-id="65356-633">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-633">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-634">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-634">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-635">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-635">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-636">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-636">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-deactivate"></a><span data-ttu-id="65356-637">디바이스 클래스 Hid 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-637">Device Class Hid Deactivate</span></span> 

#### <a name="ux_device_class_hid_deactivate"></a><span data-ttu-id="65356-638">ux_device_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-638">ux_device_class_hid_deactivate</span></span>

<span data-ttu-id="65356-639">**아이콘** ![디바이스 클래스 Hid 비활성화 아이콘](./media/user-guide/usbx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="65356-639">**Icon** ![Device Class Hid Deactivate icon](./media/user-guide/usbx-events/image10.png)</span></span>

<span data-ttu-id="65356-640">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-640">**Description**</span></span>

<span data-ttu-id="65356-641">이 이벤트는 USBX 디바이스 클래스 Hid 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-641">This event represents a USBX Device Class Hid Deactivate Event.</span></span>

<span data-ttu-id="65356-642">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-642">**Information Fields**</span></span> 

- <span data-ttu-id="65356-643">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-643">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-644">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-644">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-645">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-645">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-646">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-646">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-descriptor-send"></a><span data-ttu-id="65356-647">디바이스 클래스 Hid 설명자 보내기</span><span class="sxs-lookup"><span data-stu-id="65356-647">Device Class Hid Descriptor Send</span></span> 

#### <a name="ux_device_class_hid_descritpor_send"></a><span data-ttu-id="65356-648">ux_device_class_hid_descritpor_send</span><span class="sxs-lookup"><span data-stu-id="65356-648">ux_device_class_hid_descritpor_send</span></span>

<span data-ttu-id="65356-649">**아이콘** ![디바이스 클래스 Hid 설명자 보내기 아이콘](./media/user-guide/usbx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="65356-649">**Icon** ![Device Class Hid Descriptor Send icon](./media/user-guide/usbx-events/image11.png)</span></span>

<span data-ttu-id="65356-650">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-650">**Description**</span></span>

<span data-ttu-id="65356-651">이 이벤트는 USBX 디바이스 클래스 Hid 설명자 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-651">This event represents a USBX Device Class Hid Descriptor Send Event.</span></span>

<span data-ttu-id="65356-652">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-652">**Information Fields**</span></span> 

- <span data-ttu-id="65356-653">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-653">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-654">정보 필드 2: 설명자 유형</span><span class="sxs-lookup"><span data-stu-id="65356-654">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="65356-655">정보 필드 3: 요청 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-655">Info Field 3: Request index.</span></span>
- <span data-ttu-id="65356-656">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-656">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-get"></a><span data-ttu-id="65356-657">디바이스 클래스 Hid 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-657">Device Class Hid Event Get</span></span> 

#### <a name="ux_device_class_hid_event_get"></a><span data-ttu-id="65356-658">ux_device_class_hid_event_get</span><span class="sxs-lookup"><span data-stu-id="65356-658">ux_device_class_hid_event_get</span></span>

<span data-ttu-id="65356-659">**아이콘** ![디바이스 클래스 Hid 이벤트 가져오기 아이콘](./media/user-guide/usbx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="65356-659">**Icon** ![Device Class Hid Event Get icon](./media/user-guide/usbx-events/image12.png)</span></span>

<span data-ttu-id="65356-660">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-660">**Description**</span></span>

<span data-ttu-id="65356-661">이 이벤트는 USBX 디바이스 클래스 Hid 이벤트 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-661">This event represents a USBX Device Class Hid Event Get Event.</span></span>

<span data-ttu-id="65356-662">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-662">**Information Fields**</span></span> 

- <span data-ttu-id="65356-663">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-663">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-664">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-664">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-665">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-665">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-666">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-666">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-set"></a><span data-ttu-id="65356-667">디바이스 클래스 Hid 이벤트 설정</span><span class="sxs-lookup"><span data-stu-id="65356-667">Device Class Hid Event Set</span></span> 

#### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="65356-668">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="65356-668">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="65356-669">**아이콘** ![디바이스 클래스 Hid 이벤트 설정 아이콘](./media/user-guide/usbx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="65356-669">**Icon** ![Device Class Hid Event Set icon](./media/user-guide/usbx-events/image13.png)</span></span>

<span data-ttu-id="65356-670">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-670">**Description**</span></span>

<span data-ttu-id="65356-671">이 이벤트는 USBX 디바이스 클래스 Hid 이벤트 설정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-671">This event represents a USBX Device Class Hid Event Set.</span></span>

<span data-ttu-id="65356-672">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-672">**Information Fields**</span></span> 

- <span data-ttu-id="65356-673">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-673">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-674">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-674">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-675">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-675">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-676">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-676">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-get"></a><span data-ttu-id="65356-677">디바이스 클래스 Hid 보고서 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-677">Device Class Hid Report Get</span></span> 

#### <a name="ux_device_class_hid_report_get"></a><span data-ttu-id="65356-678">ux_device_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="65356-678">ux_device_class_hid_report_get</span></span>

<span data-ttu-id="65356-679">**아이콘** ![디바이스 클래스 Hid 보고서 가져오기 아이콘](./media/user-guide/usbx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="65356-679">**Icon** ![Device Class Hid Report Get icon](./media/user-guide/usbx-events/image14.png)</span></span>

<span data-ttu-id="65356-680">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-680">**Description**</span></span>

<span data-ttu-id="65356-681">이 이벤트는 USBX 디바이스 클래스 Hid 보고서 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-681">This event represents a USBX Device Class Hid Report Get Event.</span></span>

<span data-ttu-id="65356-682">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-682">**Information Fields**</span></span>

- <span data-ttu-id="65356-683">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-683">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-684">정보 필드 2: 설명자 유형</span><span class="sxs-lookup"><span data-stu-id="65356-684">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="65356-685">정보 필드 3: 요청 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-685">Info Field 3: Request index.</span></span>
- <span data-ttu-id="65356-686">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-686">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-set"></a><span data-ttu-id="65356-687">디바이스 클래스 Hid 보고서 설정</span><span class="sxs-lookup"><span data-stu-id="65356-687">Device Class Hid Report Set</span></span> 

#### <a name="ux_device_class_hid_report_set"></a><span data-ttu-id="65356-688">ux_device_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="65356-688">ux_device_class_hid_report_set</span></span>

<span data-ttu-id="65356-689">**아이콘** ![디바이스 클래스 Hid 보고서 설정 아이콘](./media/user-guide/usbx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="65356-689">**Icon** ![Device Class Hid Report Set icon](./media/user-guide/usbx-events/image15.png)</span></span>

<span data-ttu-id="65356-690">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-690">**Description**</span></span>

<span data-ttu-id="65356-691">이 이벤트는 USBX 디바이스 클래스 Hid 보고서 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-691">This event represents a USBX Device Class Hid Report Set Event.</span></span>

<span data-ttu-id="65356-692">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-692">**Information Fields**</span></span> 

- <span data-ttu-id="65356-693">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-693">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-694">정보 필드 2: 설명자 유형</span><span class="sxs-lookup"><span data-stu-id="65356-694">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="65356-695">정보 필드 3: 요청 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-695">Info Field 3: Request index.</span></span>
- <span data-ttu-id="65356-696">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-696">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-activate"></a><span data-ttu-id="65356-697">디바이스 클래스 Pima 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-697">Device Class Pima Activate</span></span>

#### <a name="ux_device_class_pima_activate"></a><span data-ttu-id="65356-698">ux_device_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="65356-698">ux_device_class_pima_activate</span></span>

<span data-ttu-id="65356-699">**아이콘** ![디바이스 클래스 Pima 활성화 아이콘](./media/user-guide/usbx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="65356-699">**Icon** ![Device Class Pima Activate icon](./media/user-guide/usbx-events/image16.png)</span></span>

<span data-ttu-id="65356-700">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-700">**Description**</span></span>

<span data-ttu-id="65356-701">이 이벤트는 USBX 디바이스 클래스 Pima 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-701">This event represents a USBX Device Class Pima Activate Event.</span></span>

<span data-ttu-id="65356-702">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-702">**Information Fields**</span></span>

- <span data-ttu-id="65356-703">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-703">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-704">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-704">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-705">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-705">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-706">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-706">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-deactivate"></a><span data-ttu-id="65356-707">디바이스 클래스 Pima 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-707">Device Class Pima Deactivate</span></span> 

#### <a name="ux_device_class_pima_deactivate"></a><span data-ttu-id="65356-708">ux_device_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-708">ux_device_class_pima_deactivate</span></span>

<span data-ttu-id="65356-709">**아이콘** ![디바이스 클래스 Pima 비활성화 아이콘](./media/user-guide/usbx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="65356-709">**Icon** ![Device Class Pima Deactivate icon](./media/user-guide/usbx-events/image17.png)</span></span>

<span data-ttu-id="65356-710">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-710">**Description**</span></span>

<span data-ttu-id="65356-711">이 이벤트는 USBX 디바이스 클래스 Pima 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-711">This event represents a USBX Device Class Pima Deactivate Event.</span></span>

<span data-ttu-id="65356-712">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-712">**Information Fields**</span></span>

- <span data-ttu-id="65356-713">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-713">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-714">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-714">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-715">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-715">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-716">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-716">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-device-info-send"></a><span data-ttu-id="65356-717">디바이스 클래스 Pima 디바이스 정보 보내기</span><span class="sxs-lookup"><span data-stu-id="65356-717">Device Class Pima Device Info Send</span></span> 

#### <a name="ux_device_class_pima_device_info_send"></a><span data-ttu-id="65356-718">ux_device_class_pima_device_info_send</span><span class="sxs-lookup"><span data-stu-id="65356-718">ux_device_class_pima_device_info_send</span></span>

<span data-ttu-id="65356-719">**아이콘** ![디바이스 클래스 Pima 디바이스 정보 보내기 아이콘](./media/user-guide/usbx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="65356-719">**Icon** ![Device Class Pima Device Info Send icon](./media/user-guide/usbx-events/image18.png)</span></span>

<span data-ttu-id="65356-720">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-720">**Description**</span></span>

<span data-ttu-id="65356-721">이 이벤트는 USBX 디바이스 클래스 Pima 디바이스 정보 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-721">This event represents a USBX Device Class Pima Device Info Send Event.</span></span>

<span data-ttu-id="65356-722">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-722">**Information Fields**</span></span>

- <span data-ttu-id="65356-723">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-723">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-724">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-724">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-725">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-725">Info Field 3: Not used.</span></span>

### <a name="device-class-pima-event-get"></a><span data-ttu-id="65356-726">디바이스 클래스 Pima 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-726">Device Class Pima Event Get</span></span> 

#### <a name="ux_device_class_pima_event_get"></a><span data-ttu-id="65356-727">ux_device_class_pima_event_get</span><span class="sxs-lookup"><span data-stu-id="65356-727">ux_device_class_pima_event_get</span></span>

<span data-ttu-id="65356-728">**아이콘** ![디바이스 클래스 Pima 이벤트 가져오기 아이콘](./media/user-guide/usbx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="65356-728">**Icon** ![Device Class Pima Event Get icon](./media/user-guide/usbx-events/image19.png)</span></span>

<span data-ttu-id="65356-729">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-729">**Description**</span></span>

<span data-ttu-id="65356-730">이 이벤트는 USBX 디바이스 클래스 Pima 이벤트 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-730">This event represents a USBX Device Class Pima Event Get Event.</span></span>

<span data-ttu-id="65356-731">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-731">**Information Fields**</span></span>

- <span data-ttu-id="65356-732">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-732">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-733">정보 필드 2: Pima 이벤트</span><span class="sxs-lookup"><span data-stu-id="65356-733">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="65356-734">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-734">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-735">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-735">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-event-set"></a><span data-ttu-id="65356-736">디바이스 클래스 Pima 이벤트 설정</span><span class="sxs-lookup"><span data-stu-id="65356-736">Device Class Pima Event Set</span></span> 

#### <a name="ux_device_class_pima_event_set"></a><span data-ttu-id="65356-737">ux_device_class_pima_event_set</span><span class="sxs-lookup"><span data-stu-id="65356-737">ux_device_class_pima_event_set</span></span>

<span data-ttu-id="65356-738">**아이콘** ![디바이스 클래스 Pima 이벤트 설정 아이콘](./media/user-guide/usbx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="65356-738">**Icon** ![Device Class Pima Event Set icon](./media/user-guide/usbx-events/image20.png)</span></span>

<span data-ttu-id="65356-739">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-739">**Description**</span></span>

<span data-ttu-id="65356-740">이 이벤트는 USBX 디바이스 클래스 Pima 이벤트 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-740">This event represents a USBX Device Class Pima Event Set Event.</span></span>

<span data-ttu-id="65356-741">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-741">**Information Fields**</span></span>

- <span data-ttu-id="65356-742">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-742">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-743">정보 필드 2: Pima 이벤트</span><span class="sxs-lookup"><span data-stu-id="65356-743">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="65356-744">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-744">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-745">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-745">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-add"></a><span data-ttu-id="65356-746">디바이스 클래스 Pima 개체 추가</span><span class="sxs-lookup"><span data-stu-id="65356-746">Device Class Pima Object Add</span></span> 

#### <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="65356-747">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="65356-747">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="65356-748">**아이콘** ![디바이스 클래스 Pima 개체 추가 아이콘](./media/user-guide/usbx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="65356-748">**Icon** ![Device Class Pima Object Add icon](./media/user-guide/usbx-events/image21.png)</span></span>

<span data-ttu-id="65356-749">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-749">**Description**</span></span>

<span data-ttu-id="65356-750">이 이벤트는 USBX 디바이스 클래스 Pima 개체 추가 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-750">This event represents a USBX Device Class Pima Object Add Event.</span></span>

<span data-ttu-id="65356-751">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-751">**Information Fields**</span></span> 

- <span data-ttu-id="65356-752">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-752">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-753">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-753">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-754">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-754">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-755">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-755">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-get"></a><span data-ttu-id="65356-756">디바이스 클래스 Pima 개체 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-756">Device Class Pima Object Data Get</span></span> 

#### <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="65356-757">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="65356-757">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="65356-758">**아이콘** ![디바이스 클래스 Pima 개체 데이터 가져오기 아이콘](./media/user-guide/usbx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="65356-758">**Icon** ![Device Class Pima Object Data Get icon](./media/user-guide/usbx-events/image22.png)</span></span>

<span data-ttu-id="65356-759">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-759">**Description**</span></span>

<span data-ttu-id="65356-760">이 이벤트는 USBX 디바이스 클래스 Pima 개체 데이터 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-760">This event represents a USBX Device Class Pima Object Data Get Event.</span></span>

<span data-ttu-id="65356-761">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-761">**Information Fields**</span></span> 

- <span data-ttu-id="65356-762">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-762">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-763">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-763">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-764">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-764">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-765">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-765">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-send"></a><span data-ttu-id="65356-766">디바이스 클래스 Pima 개체 데이터 보내기</span><span class="sxs-lookup"><span data-stu-id="65356-766">Device Class Pima Object Data Send</span></span> 

#### <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="65356-767">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="65356-767">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="65356-768">**아이콘** ![디바이스 클래스 Pima 개체 데이터 보내기 아이콘](./media/user-guide/usbx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="65356-768">**Icon** ![Device Class Pima Object Data Send icon](./media/user-guide/usbx-events/image23.png)</span></span>

<span data-ttu-id="65356-769">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-769">**Description**</span></span>

<span data-ttu-id="65356-770">이 이벤트는 USBX 디바이스 클래스 Pima 개체 데이터 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-770">This event represents a USBX Device Class Pima Object Data Send Event.</span></span>

<span data-ttu-id="65356-771">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-771">**Information Fields**</span></span> 

- <span data-ttu-id="65356-772">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-772">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-773">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-773">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-774">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-774">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-775">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-775">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-delete"></a><span data-ttu-id="65356-776">디바이스 클래스 Pima 개체 삭제</span><span class="sxs-lookup"><span data-stu-id="65356-776">Device Class Pima Object Delete</span></span> 

#### <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="65356-777">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="65356-777">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="65356-778">**아이콘** ![디바이스 클래스 Pima 개체 삭제 아이콘](./media/user-guide/usbx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="65356-778">**Icon** ![Device Class Pima Object Delete icon](./media/user-guide/usbx-events/image24.png)</span></span>

<span data-ttu-id="65356-779">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-779">**Description**</span></span>

<span data-ttu-id="65356-780">이 이벤트는 USBX 디바이스 클래스 Pima 개체 삭제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-780">This event represents a USBX Device Class Pima Object Delete Event.</span></span>

<span data-ttu-id="65356-781">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-781">**Information Fields**</span></span> 

- <span data-ttu-id="65356-782">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-782">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-783">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-783">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-784">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-784">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-785">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-785">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-handles-send"></a><span data-ttu-id="65356-786">디바이스 클래스 Pima 개체 핸들 보내기</span><span class="sxs-lookup"><span data-stu-id="65356-786">Device Class Pima Object Handles Send</span></span> 

#### <a name="ux_device_class_pima_object_handles_send"></a><span data-ttu-id="65356-787">ux_device_class_pima_object_handles_send</span><span class="sxs-lookup"><span data-stu-id="65356-787">ux_device_class_pima_object_handles_send</span></span>

<span data-ttu-id="65356-788">**아이콘** ![디바이스 클래스 Pima 개체 핸들 보내기 아이콘](./media/user-guide/usbx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="65356-788">**Icon** ![Device Class Pima Object Handles Send icon](./media/user-guide/usbx-events/image25.png)</span></span>

<span data-ttu-id="65356-789">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-789">**Description**</span></span>

<span data-ttu-id="65356-790">이 이벤트는 USBX 디바이스 클래스 Pima 개체 핸들 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-790">This event represents a USBX Device Class Pima Object Handles Send Event.</span></span>

<span data-ttu-id="65356-791">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-791">**Information Fields**</span></span>

- <span data-ttu-id="65356-792">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-792">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-793">정보 필드 2: 스토리지 ID</span><span class="sxs-lookup"><span data-stu-id="65356-793">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="65356-794">정보 필드 3: 개체 형식 코드</span><span class="sxs-lookup"><span data-stu-id="65356-794">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="65356-795">정보 필드 4: 개체 연결</span><span class="sxs-lookup"><span data-stu-id="65356-795">Info Field 4: Object association.</span></span>

### <a name="device-class-pima-object-info-get"></a><span data-ttu-id="65356-796">디바이스 클래스 Pima 개체 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-796">Device Class Pima Object Info Get</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="65356-797">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="65356-797">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="65356-798">**아이콘** ![디바이스 클래스 Pima 개체 정보 가져오기 아이콘](./media/user-guide/usbx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="65356-798">**Icon** ![Device Class Pima Object Info Get icon](./media/user-guide/usbx-events/image26.png)</span></span>

<span data-ttu-id="65356-799">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-799">**Description**</span></span>

<span data-ttu-id="65356-800">이 이벤트는 USBX 디바이스 클래스 Pima 개체 정보 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-800">This event represents a USBX Device Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="65356-801">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-801">**Information Fields**</span></span>

- <span data-ttu-id="65356-802">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-802">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-803">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-803">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-804">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-804">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-805">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-805">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-info-send"></a><span data-ttu-id="65356-806">디바이스 클래스 Pima 개체 정보 보내기</span><span class="sxs-lookup"><span data-stu-id="65356-806">Device Class Pima Object Info Send</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="65356-807">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="65356-807">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="65356-808">**아이콘** ![디바이스 클래스 Pima 개체 정보 보내기 아이콘](./media/user-guide/usbx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="65356-808">**Icon** ![Device Class Pima Object Info Send icon](./media/user-guide/usbx-events/image27.png)</span></span>

<span data-ttu-id="65356-809">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-809">**Description**</span></span>

<span data-ttu-id="65356-810">이 이벤트는 USBX 디바이스 클래스 Pima 개체 정보 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-810">This event represents a USBX Device Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="65356-811">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-811">**Information Fields**</span></span>

- <span data-ttu-id="65356-812">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-812">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-813">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-813">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-814">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-814">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-815">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-815">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-objects-number-send"></a><span data-ttu-id="65356-816">디바이스 클래스 Pima 개체 번호 보내기</span><span class="sxs-lookup"><span data-stu-id="65356-816">Device Class Pima Objects Number Send</span></span> 

#### <a name="ux_device_class_pima_object_number_send"></a><span data-ttu-id="65356-817">ux_device_class_pima_object_number_send</span><span class="sxs-lookup"><span data-stu-id="65356-817">ux_device_class_pima_object_number_send</span></span>

<span data-ttu-id="65356-818">**아이콘** ![디바이스 클래스 Pima 개체 번호 보내기 아이콘](./media/user-guide/usbx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="65356-818">**Icon** ![Device Class Pima Objects Number Send icon](./media/user-guide/usbx-events/image28.png)</span></span>

<span data-ttu-id="65356-819">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-819">**Description**</span></span>

<span data-ttu-id="65356-820">이 이벤트는 USBX 디바이스 클래스 Pima 개체 번호 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-820">This event represents a USBX Device Class Pima Object Number Send event.</span></span>

<span data-ttu-id="65356-821">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-821">**Information Fields**</span></span>

- <span data-ttu-id="65356-822">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-822">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-823">정보 필드 2: 스토리지 ID</span><span class="sxs-lookup"><span data-stu-id="65356-823">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="65356-824">정보 필드 3: 개체 형식 코드</span><span class="sxs-lookup"><span data-stu-id="65356-824">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="65356-825">정보 필드 4: 개체 연결</span><span class="sxs-lookup"><span data-stu-id="65356-825">Info Field 4: Object associate.</span></span>

### <a name="device-class-pima-partial-object-data-get"></a><span data-ttu-id="65356-826">디바이스 클래스 Pima 부분 개체 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-826">Device Class Pima Partial Object Data Get</span></span>

#### <a name="ux_device_class_pima_partial_object_data_get"></a><span data-ttu-id="65356-827">ux_device_class_pima_partial_object_data_get</span><span class="sxs-lookup"><span data-stu-id="65356-827">ux_device_class_pima_partial_object_data_get</span></span>

<span data-ttu-id="65356-828">**아이콘** ![디바이스 클래스 Pima 부분 개체 데이터 가져오기 아이콘](./media/user-guide/usbx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="65356-828">**Icon** ![Device Class Pima Partial Object Data Get icon](./media/user-guide/usbx-events/image29.png)</span></span>

<span data-ttu-id="65356-829">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-829">**Description**</span></span>

<span data-ttu-id="65356-830">이 이벤트는 USBX 디바이스 클래스 Pima 부분 개체 데이터 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-830">This event represents a USBX Device Class Pima Partial Object Data Get Event.</span></span>

<span data-ttu-id="65356-831">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-831">**Information Fields**</span></span>

- <span data-ttu-id="65356-832">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-832">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-833">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-833">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-834">정보 필드 3: 오프셋이 요청되었습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-834">Info Field 3: Offset requested.</span></span>
- <span data-ttu-id="65356-835">정보 필드 4: 길이가 요청되었습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-835">Info Field 4: Length requested.</span></span>

### <a name="device-class-pima-response-send"></a><span data-ttu-id="65356-836">디바이스 클래스 Pima 응답 보내기</span><span class="sxs-lookup"><span data-stu-id="65356-836">Device Class Pima Response Send</span></span> 

#### <a name="ux_device_class_pima_response_send"></a><span data-ttu-id="65356-837">ux_device_class_pima_response_send</span><span class="sxs-lookup"><span data-stu-id="65356-837">ux_device_class_pima_response_send</span></span>

<span data-ttu-id="65356-838">**아이콘** ![디바이스 클래스 Pima 응답 보내기 아이콘](./media/user-guide/usbx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="65356-838">**Icon** ![Device Class Pima Response Send icon](./media/user-guide/usbx-events/image30.png)</span></span>

<span data-ttu-id="65356-839">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-839">**Description**</span></span>

<span data-ttu-id="65356-840">이 이벤트는 USBX 디바이스 클래스 Pima 응답 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-840">This event represents a USBX Device Class Pima Response Send Event.</span></span>

<span data-ttu-id="65356-841">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-841">**Information Fields**</span></span>

- <span data-ttu-id="65356-842">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-842">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-843">정보 필드 2: 응답 코드</span><span class="sxs-lookup"><span data-stu-id="65356-843">Info Field 2: Response code.</span></span>
- <span data-ttu-id="65356-844">정보 필드 3: 숫자 매개 변수</span><span class="sxs-lookup"><span data-stu-id="65356-844">Info Field 3: Number parameter.</span></span>
- <span data-ttu-id="65356-845">정보 필드 4: Pima 매개 변수 1</span><span class="sxs-lookup"><span data-stu-id="65356-845">Info Field 4: Pima parameter 1.</span></span>

### <a name="device-class-pima-storage-id-send"></a><span data-ttu-id="65356-846">디바이스 클래스 Pima 스토리지 ID 보내기</span><span class="sxs-lookup"><span data-stu-id="65356-846">Device Class Pima Storage Id Send</span></span> 

#### <a name="ux_device_class_pima_storage_id_send"></a><span data-ttu-id="65356-847">ux_device_class_pima_storage_id_send</span><span class="sxs-lookup"><span data-stu-id="65356-847">ux_device_class_pima_storage_id_send</span></span>

<span data-ttu-id="65356-848">**아이콘** ![디바이스 클래스 Pima 스토리지 ID 보내기 아이콘](./media/user-guide/usbx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="65356-848">**Icon** ![Device Class Pima Storage Id Send icon](./media/user-guide/usbx-events/image31.png)</span></span>

<span data-ttu-id="65356-849">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-849">**Description**</span></span>

<span data-ttu-id="65356-850">이 이벤트는 USBX 디바이스 클래스 Pima 스토리지 ID 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-850">This event represents a USBX Device Class Pima Storage Id Send Event.</span></span>

<span data-ttu-id="65356-851">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-851">**Information Fields**</span></span> 

- <span data-ttu-id="65356-852">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-852">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-853">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-853">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-854">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-854">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-855">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-855">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-storage-info-send"></a><span data-ttu-id="65356-856">디바이스 클래스 Pima 스토리지 정보 보내기</span><span class="sxs-lookup"><span data-stu-id="65356-856">Device Class Pima Storage Info Send</span></span> 

#### <a name="ux_device_class_pima_storage_info_send"></a><span data-ttu-id="65356-857">ux_device_class_pima_storage_info_send</span><span class="sxs-lookup"><span data-stu-id="65356-857">ux_device_class_pima_storage_info_send</span></span>

<span data-ttu-id="65356-858">**아이콘** ![디바이스 클래스 Pima 스토리지 정보 보내기 아이콘](./media/user-guide/usbx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="65356-858">**Icon** ![Device Class Pima Storage Info Send icon](./media/user-guide/usbx-events/image32.png)</span></span>

<span data-ttu-id="65356-859">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-859">**Description**</span></span>

<span data-ttu-id="65356-860">이 이벤트는 USBX 디바이스 클래스 Pima 스토리지 정보 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-860">This event represents a USBX Device Class Pima Storage Info Send Event.</span></span>

<span data-ttu-id="65356-861">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-861">**Information Fields**</span></span> 

- <span data-ttu-id="65356-862">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-862">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-863">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-863">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-864">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-864">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-865">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-865">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-activate"></a><span data-ttu-id="65356-866">디바이스 클래스 Rndis 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-866">Device Class Rndis Activate</span></span> 

#### <a name="ux_device_class_rndis_activate"></a><span data-ttu-id="65356-867">ux_device_class_rndis_activate</span><span class="sxs-lookup"><span data-stu-id="65356-867">ux_device_class_rndis_activate</span></span>

<span data-ttu-id="65356-868">**아이콘** ![디바이스 클래스 Rndis 활성화 아이콘](./media/user-guide/usbx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="65356-868">**Icon** ![Device Class Rndis Activate icon](./media/user-guide/usbx-events/image33.png)</span></span>

<span data-ttu-id="65356-869">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-869">**Description**</span></span>

<span data-ttu-id="65356-870">이 이벤트는 USBX 디바이스 클래스 Rndis 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-870">This event represents a USBX Device Class Rndis Activate Event.</span></span>

<span data-ttu-id="65356-871">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-871">**Information Fields**</span></span> 

- <span data-ttu-id="65356-872">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-872">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-873">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-873">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-874">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-874">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-875">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-875">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-deactivate"></a><span data-ttu-id="65356-876">디바이스 클래스 Rndis 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-876">Device Class Rndis Deactivate</span></span> 

#### <a name="ux_device_class_rndis_deactivate"></a><span data-ttu-id="65356-877">ux_device_class_rndis_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-877">ux_device_class_rndis_deactivate</span></span>

<span data-ttu-id="65356-878">**아이콘** ![디바이스 클래스 Rndis 비활성화 아이콘](./media/user-guide/usbx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="65356-878">**Icon** ![Device Class Rndis Deactivate icon](./media/user-guide/usbx-events/image34.png)</span></span>

<span data-ttu-id="65356-879">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-879">**Description**</span></span>

<span data-ttu-id="65356-880">이 이벤트는 USBX 디바이스 클래스 Rndis 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-880">This event represents a USBX Device Class Rndis Deactivate Event.</span></span>

<span data-ttu-id="65356-881">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-881">**Information Fields**</span></span> 

- <span data-ttu-id="65356-882">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-882">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-883">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-883">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-884">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-884">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-885">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-885">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-keep-alive"></a><span data-ttu-id="65356-886">디바이스 클래스 Rndis 메시지 연결 유지</span><span class="sxs-lookup"><span data-stu-id="65356-886">Device Class Rndis Message Keep Alive</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a><span data-ttu-id="65356-887">ux_device_class_rndis_msg_keep_alive</span><span class="sxs-lookup"><span data-stu-id="65356-887">ux_device_class_rndis_msg_keep_alive</span></span>

<span data-ttu-id="65356-888">**아이콘** ![디바이스 클래스 Rndis 메시지 연결 유지 아이콘](./media/user-guide/usbx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="65356-888">**Icon** ![Device Class Rndis Message Keep Alive icon](./media/user-guide/usbx-events/image35.png)</span></span>

<span data-ttu-id="65356-889">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-889">**Description**</span></span>

<span data-ttu-id="65356-890">이 이벤트는 USBX 디바이스 클래스 Rndis 메시지 연결 유지 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-890">This event represents a USBX Device Class Rndis Message Keep Alive Event.</span></span>

<span data-ttu-id="65356-891">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-891">**Information Fields**</span></span> 

- <span data-ttu-id="65356-892">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-892">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-893">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-893">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-894">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-894">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-895">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-895">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-query"></a><span data-ttu-id="65356-896">디바이스 클래스 Rndis 메시지 쿼리</span><span class="sxs-lookup"><span data-stu-id="65356-896">Device Class Rndis Message Query</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_query"></a><span data-ttu-id="65356-897">ux_device_class_rndis_msg_keep_query</span><span class="sxs-lookup"><span data-stu-id="65356-897">ux_device_class_rndis_msg_keep_query</span></span>

<span data-ttu-id="65356-898">**아이콘** ![디바이스 클래스 Rndis 메시지 쿼리 아이콘](./media/user-guide/usbx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="65356-898">**Icon** ![Device Class Rndis Message Query icon](./media/user-guide/usbx-events/image36.png)</span></span>

<span data-ttu-id="65356-899">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-899">**Description**</span></span>

<span data-ttu-id="65356-900">이 이벤트는 USBX 디바이스 클래스 Rndis 메시지 쿼리 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-900">This event represents a USBX Device Class Rndis Message Query Event.</span></span>

<span data-ttu-id="65356-901">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-901">**Information Fields**</span></span> 

- <span data-ttu-id="65356-902">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-902">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-903">정보 필드 2: Rndis OID</span><span class="sxs-lookup"><span data-stu-id="65356-903">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="65356-904">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-904">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-905">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-905">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-reset"></a><span data-ttu-id="65356-906">디바이스 클래스 Rndis 메시지 재설정</span><span class="sxs-lookup"><span data-stu-id="65356-906">Device Class Rndis Message Reset</span></span> 

#### <a name="ux_device_class_rndis_msg_reset"></a><span data-ttu-id="65356-907">ux_device_class_rndis_msg_reset</span><span class="sxs-lookup"><span data-stu-id="65356-907">ux_device_class_rndis_msg_reset</span></span>

<span data-ttu-id="65356-908">**아이콘** ![디바이스 클래스 Rndis 메시지 재설정 아이콘](./media/user-guide/usbx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="65356-908">**Icon** ![Device Class Rndis Message Reset icon](./media/user-guide/usbx-events/image37.png)</span></span>

<span data-ttu-id="65356-909">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-909">**Description**</span></span>

<span data-ttu-id="65356-910">이 이벤트는 USBX 디바이스 클래스 Rndis 메시지 재설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-910">This event represents a USBX Device Class Rndis Message Reset Event.</span></span>

<span data-ttu-id="65356-911">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-911">**Information Fields**</span></span> 

- <span data-ttu-id="65356-912">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-912">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-913">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-913">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-914">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-914">Info Field 3: Not used.</span></span>

### <a name="device-class-rndis-message-set"></a><span data-ttu-id="65356-915">디바이스 클래스 Rndis 메시지 설정</span><span class="sxs-lookup"><span data-stu-id="65356-915">Device Class Rndis Message Set</span></span> 

#### <a name="ux_device_class_rndis_msg_set"></a><span data-ttu-id="65356-916">ux_device_class_rndis_msg_set</span><span class="sxs-lookup"><span data-stu-id="65356-916">ux_device_class_rndis_msg_set</span></span>

<span data-ttu-id="65356-917">**아이콘** ![디바이스 클래스 Rndis 메시지 설정 아이콘](./media/user-guide/usbx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="65356-917">**Icon** ![Device Class Rndis Message Set icon](./media/user-guide/usbx-events/image38.png)</span></span>

<span data-ttu-id="65356-918">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-918">**Description**</span></span>

<span data-ttu-id="65356-919">이 이벤트는 USBX 디바이스 클래스 Rndis 메시지 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-919">This event represents a USBX Device Class Rndis Message Set Event.</span></span>

<span data-ttu-id="65356-920">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-920">**Information Fields**</span></span>

- <span data-ttu-id="65356-921">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-921">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-922">정보 필드 2: Rndis OID</span><span class="sxs-lookup"><span data-stu-id="65356-922">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="65356-923">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-923">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-924">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-924">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-receive"></a><span data-ttu-id="65356-925">디바이스 클래스 Rndis 패킷 수신</span><span class="sxs-lookup"><span data-stu-id="65356-925">Device Class Rndis Packet Receive</span></span> 

#### <a name="ux_device_class_rndis_packet_receive"></a><span data-ttu-id="65356-926">ux_device_class_rndis_packet_receive</span><span class="sxs-lookup"><span data-stu-id="65356-926">ux_device_class_rndis_packet_receive</span></span>

<span data-ttu-id="65356-927">**아이콘** ![디바이스 클래스 Rndis 패킷 수신 아이콘](./media/user-guide/usbx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="65356-927">**Icon** ![Device Class Rndis Packet Receive icon](./media/user-guide/usbx-events/image39.png)</span></span>

<span data-ttu-id="65356-928">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-928">**Description**</span></span>

<span data-ttu-id="65356-929">이 이벤트는 USBX 디바이스 클래스 Rndis 패킷 수신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-929">This event represents a USBX Device Class Rndis Packet Receive Event.</span></span>

<span data-ttu-id="65356-930">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-930">**Information Fields**</span></span>

- <span data-ttu-id="65356-931">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-931">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-932">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-932">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-933">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-933">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-934">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-934">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-transmit"></a><span data-ttu-id="65356-935">디바이스 클래스 Rndis 패킷 전송</span><span class="sxs-lookup"><span data-stu-id="65356-935">Device Class Rndis Packet Transmit</span></span> 

#### <a name="ux_device_class_rndis_packet_transmit"></a><span data-ttu-id="65356-936">ux_device_class_rndis_packet_transmit</span><span class="sxs-lookup"><span data-stu-id="65356-936">ux_device_class_rndis_packet_transmit</span></span>

<span data-ttu-id="65356-937">**아이콘** ![디바이스 클래스 Rndis 패킷 전송 아이콘](./media/user-guide/usbx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="65356-937">**Icon** ![Device Class Rndis Packet Transmit icon](./media/user-guide/usbx-events/image40.png)</span></span>

<span data-ttu-id="65356-938">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-938">**Description**</span></span>

<span data-ttu-id="65356-939">이 이벤트는 USBX 디바이스 클래스 Rndis 패킷 전송 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-939">This event represents a USBX Device Class Rndis Packet Transmit Event.</span></span>

<span data-ttu-id="65356-940">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-940">**Information Fields**</span></span> 

- <span data-ttu-id="65356-941">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-941">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-942">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-942">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-943">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-943">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-944">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-944">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-activate"></a><span data-ttu-id="65356-945">디바이스 클래스 스토리지 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-945">Device Class Storage Activate</span></span> 

#### <a name="ux_device_class_storage_activate"></a><span data-ttu-id="65356-946">ux_device_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="65356-946">ux_device_class_storage_activate</span></span>

<span data-ttu-id="65356-947">**아이콘** ![디바이스 클래스 스토리지 활성화 아이콘](./media/user-guide/usbx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="65356-947">**Icon** ![Device Class Storage Activate icon](./media/user-guide/usbx-events/image41.png)</span></span>

<span data-ttu-id="65356-948">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-948">**Description**</span></span>

<span data-ttu-id="65356-949">이 이벤트는 USBX 디바이스 클래스 스토리지 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-949">This event represents a USBX Device Class Storage Activate Event.</span></span>

<span data-ttu-id="65356-950">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-950">**Information Fields**</span></span>

- <span data-ttu-id="65356-951">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-951">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-952">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-952">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-953">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-953">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-954">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-954">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-deactivate"></a><span data-ttu-id="65356-955">디바이스 클래스 스토리지 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-955">Device Class Storage Deactivate</span></span> 

#### <a name="ux_device_class_storage_deactivate"></a><span data-ttu-id="65356-956">ux_device_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-956">ux_device_class_storage_deactivate</span></span>

<span data-ttu-id="65356-957">**아이콘** ![디바이스 클래스 스토리지 비활성화 아이콘](./media/user-guide/usbx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="65356-957">**Icon** ![Device Class Storage Deactivate icon](./media/user-guide/usbx-events/image42.png)</span></span>

<span data-ttu-id="65356-958">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-958">**Description**</span></span>

<span data-ttu-id="65356-959">이 이벤트는 USBX 디바이스 클래스 Rndis 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-959">This event represents a USBX Device Class Storage Deactivate Event.</span></span>

<span data-ttu-id="65356-960">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-960">**Information Fields**</span></span>

- <span data-ttu-id="65356-961">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-961">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-962">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-962">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-963">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-963">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-964">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-964">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-format"></a><span data-ttu-id="65356-965">디바이스 클래스 스토리지 형식</span><span class="sxs-lookup"><span data-stu-id="65356-965">Device Class Storage Format</span></span> 

#### <a name="ux_device_class_storage_format"></a><span data-ttu-id="65356-966">ux_device_class_storage_format</span><span class="sxs-lookup"><span data-stu-id="65356-966">ux_device_class_storage_format</span></span>

<span data-ttu-id="65356-967">**아이콘** ![디바이스 클래스 스토리지 형식 아이콘](./media/user-guide/usbx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="65356-967">**Icon** ![Device Class Storage Format icon](./media/user-guide/usbx-events/image43.png)</span></span>

<span data-ttu-id="65356-968">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-968">**Description**</span></span>

<span data-ttu-id="65356-969">이 이벤트는 USBX 디바이스 클래스 스토리지 형식 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-969">This event represents a USBX Device Class Storage Format Event.</span></span>

<span data-ttu-id="65356-970">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-970">**Information Fields**</span></span> 

- <span data-ttu-id="65356-971">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-971">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-972">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-972">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-973">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-973">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-974">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-974">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-inquiry"></a><span data-ttu-id="65356-975">디바이스 클래스 스토리지 조회</span><span class="sxs-lookup"><span data-stu-id="65356-975">Device Class Storage Inquiry</span></span> 

#### <a name="ux_device_class_storage_inquiry"></a><span data-ttu-id="65356-976">ux_device_class_storage_inquiry</span><span class="sxs-lookup"><span data-stu-id="65356-976">ux_device_class_storage_inquiry</span></span>

<span data-ttu-id="65356-977">**아이콘** ![디바이스 클래스 스토리지 조회 아이콘](./media/user-guide/usbx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="65356-977">**Icon** ![Device Class Storage Inquiry icon](./media/user-guide/usbx-events/image44.png)</span></span>

<span data-ttu-id="65356-978">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-978">**Description**</span></span>

<span data-ttu-id="65356-979">이 이벤트는 USBX 디바이스 클래스 스토리지 조회 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-979">This event represents a USBX Device Class Storage Inquiry Event.</span></span>

<span data-ttu-id="65356-980">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-980">**Information Fields**</span></span>

- <span data-ttu-id="65356-981">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-981">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-982">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-982">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-983">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-983">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-984">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-984">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-select"></a><span data-ttu-id="65356-985">디바이스 클래스 스토리지 모드 선택</span><span class="sxs-lookup"><span data-stu-id="65356-985">Device Class Storage Mode Select</span></span>

#### <a name="ux_device_class_storage_mode_select"></a><span data-ttu-id="65356-986">ux_device_class_storage_mode_select</span><span class="sxs-lookup"><span data-stu-id="65356-986">ux_device_class_storage_mode_select</span></span>

<span data-ttu-id="65356-987">**아이콘** ![디바이스 클래스 스토리지 모드 선택 아이콘](./media/user-guide/usbx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="65356-987">**Icon** ![Device Class Storage Mode Select icon](./media/user-guide/usbx-events/image45.png)</span></span>

<span data-ttu-id="65356-988">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-988">**Description**</span></span>

<span data-ttu-id="65356-989">이 이벤트는 USBX 디바이스 클래스 스토리지 모드 선택 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-989">This event represents a USBX Device Class Storage Mode Select Event.</span></span>

<span data-ttu-id="65356-990">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-990">**Information Fields**</span></span> 

- <span data-ttu-id="65356-991">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-991">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-992">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-992">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-993">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-993">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-994">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-994">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-sense"></a><span data-ttu-id="65356-995">디바이스 클래스 스토리지 모드 센스</span><span class="sxs-lookup"><span data-stu-id="65356-995">Device Class Storage Mode Sense</span></span> 

#### <a name="ux_device_class_storage_mode_sense"></a><span data-ttu-id="65356-996">ux_device_class_storage_mode_sense</span><span class="sxs-lookup"><span data-stu-id="65356-996">ux_device_class_storage_mode_sense</span></span>

<span data-ttu-id="65356-997">**아이콘** ![디바이스 클래스 스토리지 모드 센스 아이콘](./media/user-guide/usbx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="65356-997">**Icon** ![Device Class Storage Mode Sense icon](./media/user-guide/usbx-events/image46.png)</span></span>

<span data-ttu-id="65356-998">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-998">**Description**</span></span>

<span data-ttu-id="65356-999">이 이벤트는 USBX 디바이스 클래스 스토리지 모드 센스 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-999">This event represents a USBX Device Class Storage Mode Sense Event.</span></span>

<span data-ttu-id="65356-1000">정보 필드</span><span class="sxs-lookup"><span data-stu-id="65356-1000">Information Fields</span></span> 

- <span data-ttu-id="65356-1001">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1001">nfo Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1002">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-1002">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-1003">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1003">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1004">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1004">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-prevent-allow-media-removal"></a><span data-ttu-id="65356-1005">디바이스 클래스 스토리지의 미디어 제거 방지 허용</span><span class="sxs-lookup"><span data-stu-id="65356-1005">Device Class Storage Prevent Allow Media Removal</span></span> 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a><span data-ttu-id="65356-1006">ux_device_class_storage_prevent_allow_media_removal</span><span class="sxs-lookup"><span data-stu-id="65356-1006">ux_device_class_storage_prevent_allow_media_removal</span></span>

<span data-ttu-id="65356-1007">**아이콘** ![디바이스 클래스 스토리지의 미디어 제거 방지 허용 아이콘](./media/user-guide/usbx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1007">**Icon** ![Device Class Storage Prevent Allow Media Removal icon](./media/user-guide/usbx-events/image47.png)</span></span>

<span data-ttu-id="65356-1008">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1008">**Description**</span></span>

<span data-ttu-id="65356-1009">이 이벤트는 USBX 디바이스 클래스 스토리지 미디어 제거 방지 허용 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1009">This event represents a USBX Device Class Storage Prevent Allow Media Removal Event.</span></span>

<span data-ttu-id="65356-1010">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1010">**Information Fields**</span></span>

- <span data-ttu-id="65356-1011">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1011">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1012">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-1012">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-1013">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1013">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1014">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1014">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read"></a><span data-ttu-id="65356-1015">디바이스 클래스 스토리지 읽기</span><span class="sxs-lookup"><span data-stu-id="65356-1015">Device Class Storage Read</span></span> 

#### <a name="ux_device_class_storage_read"></a><span data-ttu-id="65356-1016">ux_device_class_storage_read</span><span class="sxs-lookup"><span data-stu-id="65356-1016">ux_device_class_storage_read</span></span>

<span data-ttu-id="65356-1017">**아이콘** ![디바이스 클래스 스토리지 읽기 아이콘](./media/user-guide/usbx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1017">**Icon** ![Device Class Storage Read icon](./media/user-guide/usbx-events/image48.png)</span></span>

<span data-ttu-id="65356-1018">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1018">**Description**</span></span>

<span data-ttu-id="65356-1019">이 이벤트는 USBX 디바이스 클래스 스토리지 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1019">This event represents a USBX Device Class Storage Read Event.</span></span>

<span data-ttu-id="65356-1020">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1020">**Information Fields**</span></span>

- <span data-ttu-id="65356-1021">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1021">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1022">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-1022">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-1023">정보 필드 3: 섹터</span><span class="sxs-lookup"><span data-stu-id="65356-1023">Info Field 3: Sector.</span></span>
- <span data-ttu-id="65356-1024">정보 필드 4: 섹터 수</span><span class="sxs-lookup"><span data-stu-id="65356-1024">Info Field 4: Number sectors.</span></span>

### <a name="device-class-storage-read-capacity"></a><span data-ttu-id="65356-1025">디바이스 클래스 스토리지 읽기 용량</span><span class="sxs-lookup"><span data-stu-id="65356-1025">Device Class Storage Read Capacity</span></span> 

#### <a name="ux_device_class_storage_read_capacity"></a><span data-ttu-id="65356-1026">ux_device_class_storage_read_capacity</span><span class="sxs-lookup"><span data-stu-id="65356-1026">ux_device_class_storage_read_capacity</span></span>

<span data-ttu-id="65356-1027">**아이콘** ![디바이스 클래스 스토리지 읽기 용량 아이콘](./media/user-guide/usbx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1027">**Icon** ![Device Class Storage Read Capacity icon](./media/user-guide/usbx-events/image49.png)</span></span>

<span data-ttu-id="65356-1028">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1028">**Description**</span></span>

<span data-ttu-id="65356-1029">이 이벤트는 USBX 디바이스 클래스 스토리지 읽기 용량 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1029">This event represents a USBX Device Class Storage Read Capacity Event.</span></span>

<span data-ttu-id="65356-1030">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1030">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1031">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1031">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1032">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-1032">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-1033">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1033">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1034">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1034">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-format-capacity"></a><span data-ttu-id="65356-1035">디바이스 클래스 스토리지 읽기 형식 용량</span><span class="sxs-lookup"><span data-stu-id="65356-1035">Device Class Storage Read Format Capacity</span></span> 

#### <a name="ux_device_class_storage_read_format_capacity"></a><span data-ttu-id="65356-1036">ux_device_class_storage_read_format_capacity</span><span class="sxs-lookup"><span data-stu-id="65356-1036">ux_device_class_storage_read_format_capacity</span></span>

<span data-ttu-id="65356-1037">**아이콘** ![디바이스 클래스 스토리지 읽기 형식 용량 아이콘](./media/user-guide/usbx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1037">**Icon** ![Device Class Storage Read Format Capacity icon](./media/user-guide/usbx-events/image50.png)</span></span>

<span data-ttu-id="65356-1038">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1038">**Description**</span></span>

<span data-ttu-id="65356-1039">이 이벤트는 USBX 디바이스 클래스 스토리지 읽기 형식 용량 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1039">This event represents a USBX Device Class Storage Read Format Capacity Event.</span></span>

<span data-ttu-id="65356-1040">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1040">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1041">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1041">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1042">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-1042">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-1043">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1043">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1044">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1044">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-toc"></a><span data-ttu-id="65356-1045">디바이스 클래스 스토리지 읽기 TOC</span><span class="sxs-lookup"><span data-stu-id="65356-1045">Device Class Storage Read TOC</span></span> 

#### <a name="ux_device_class_storage_read_toc"></a><span data-ttu-id="65356-1046">ux_device_class_storage_read_toc</span><span class="sxs-lookup"><span data-stu-id="65356-1046">ux_device_class_storage_read_toc</span></span>

<span data-ttu-id="65356-1047">**아이콘** ![디바이스 클래스 스토리지 읽기 TOC 아이콘](./media/user-guide/usbx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1047">**Icon** ![Device Class Storage Read TOC icon](./media/user-guide/usbx-events/image51.png)</span></span>

<span data-ttu-id="65356-1048">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1048">**Description**</span></span>

<span data-ttu-id="65356-1049">이 이벤트는 USBX 디바이스 클래스 스토리지 읽기 TOC 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1049">This event represents a USBX Device Class Storage Read TOC Event.</span></span>

<span data-ttu-id="65356-1050">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1050">**Information Fields**</span></span>

- <span data-ttu-id="65356-1051">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1051">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1052">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-1052">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-1053">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1053">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1054">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1054">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-request-sense"></a><span data-ttu-id="65356-1055">디바이스 클래스 스토리지 요청 센스</span><span class="sxs-lookup"><span data-stu-id="65356-1055">Device Class Storage Request Sense</span></span> 

#### <a name="ux_device_class_storage_request_sense"></a><span data-ttu-id="65356-1056">ux_device_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="65356-1056">ux_device_class_storage_request_sense</span></span>

<span data-ttu-id="65356-1057">**아이콘** ![디바이스 클래스 스토리지 요청 센스 아이콘](./media/user-guide/usbx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1057">**Icon** ![Device Class Storage Request Sense icon](./media/user-guide/usbx-events/image52.png)</span></span>

<span data-ttu-id="65356-1058">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1058">**Description**</span></span>

<span data-ttu-id="65356-1059">이 이벤트는 USBX 디바이스 클래스 스토리지 요청 센스 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1059">This event represents a USBX Device Class Storage Request Sense Event.</span></span>

<span data-ttu-id="65356-1060">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1060">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1061">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1061">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1062">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-1062">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-1063">정보 필드 3: 센스 키</span><span class="sxs-lookup"><span data-stu-id="65356-1063">Info Field 3: Sense key.</span></span>
- <span data-ttu-id="65356-1064">정보 필드 4: 코드</span><span class="sxs-lookup"><span data-stu-id="65356-1064">Info Field 4: Code.</span></span>

### <a name="device-class-storage-start-stop"></a><span data-ttu-id="65356-1065">디바이스 클래스 스토리지 시작 중지</span><span class="sxs-lookup"><span data-stu-id="65356-1065">Device Class Storage Start Stop</span></span> 

#### <a name="ux_device_class_storage_start_stop"></a><span data-ttu-id="65356-1066">ux_device_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="65356-1066">ux_device_class_storage_start_stop</span></span>

<span data-ttu-id="65356-1067">**아이콘** ![디바이스 클래스 스토리지 시작 중지 아이콘](./media/user-guide/usbx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1067">**Icon** ![Device Class Storage Start Stop icon](./media/user-guide/usbx-events/image53.png)</span></span>

<span data-ttu-id="65356-1068">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1068">**Description**</span></span>

<span data-ttu-id="65356-1069">이 이벤트는 USBX 디바이스 클래스 스토리지 시작 중지 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1069">This event represents a USBX Device Class Storage Start Stop Event.</span></span>

<span data-ttu-id="65356-1070">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1070">**Information Fields**</span></span>

- <span data-ttu-id="65356-1071">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1071">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1072">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-1072">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-1073">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1073">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1074">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1074">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-test-ready"></a><span data-ttu-id="65356-1075">디바이스 클래스 스토리지 테스트 준비</span><span class="sxs-lookup"><span data-stu-id="65356-1075">Device Class Storage Test Ready</span></span> 

#### <a name="ux_device_class_storage_test_ready"></a><span data-ttu-id="65356-1076">ux_device_class_storage_test_ready</span><span class="sxs-lookup"><span data-stu-id="65356-1076">ux_device_class_storage_test_ready</span></span>

<span data-ttu-id="65356-1077">**아이콘** ![디바이스 클래스 스토리지 테스트 준비 아이콘](./media/user-guide/usbx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1077">**Icon** ![Device Class Storage Test Ready icon](./media/user-guide/usbx-events/image54.png)</span></span>

<span data-ttu-id="65356-1078">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1078">**Description**</span></span>

<span data-ttu-id="65356-1079">이 이벤트는 USBX 디바이스 클래스 스토리지 테스트 준비 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1079">This event represents a USBX Device Class Storage Test Ready Event.</span></span>

<span data-ttu-id="65356-1080">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1080">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1081">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1081">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1082">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-1082">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-1083">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1083">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1084">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1084">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-verify"></a><span data-ttu-id="65356-1085">디바이스 클래스 스토리지 확인</span><span class="sxs-lookup"><span data-stu-id="65356-1085">Device Class Storage Verify</span></span> 

#### <a name="ux_device_class_storage_verify"></a><span data-ttu-id="65356-1086">ux_device_class_storage_verify</span><span class="sxs-lookup"><span data-stu-id="65356-1086">ux_device_class_storage_verify</span></span>

<span data-ttu-id="65356-1087">**아이콘** ![디바이스 클래스 스토리지 확인 아이콘](./media/user-guide/usbx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1087">**Icon** ![Device Class Storage Verify icon](./media/user-guide/usbx-events/image55.png)</span></span>

<span data-ttu-id="65356-1088">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1088">**Description**</span></span>

<span data-ttu-id="65356-1089">이 이벤트는 USBX 디바이스 클래스 스토리지 확인 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1089">This event represents a USBX Device Class Storage Verify Event.</span></span>

<span data-ttu-id="65356-1090">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1090">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1091">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1091">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1092">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-1092">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-1093">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1093">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1094">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1094">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-write"></a><span data-ttu-id="65356-1095">디바이스 클래스 스토리지 쓰기</span><span class="sxs-lookup"><span data-stu-id="65356-1095">Device Class Storage Write</span></span> 

#### <a name="ux_device_class_storage_write"></a><span data-ttu-id="65356-1096">ux_device_class_storage_write</span><span class="sxs-lookup"><span data-stu-id="65356-1096">ux_device_class_storage_write</span></span>

<span data-ttu-id="65356-1097">**아이콘** ![디바이스 클래스 스토리지 쓰기 아이콘](./media/user-guide/usbx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1097">**Icon** ![Device Class Storage Write icon](./media/user-guide/usbx-events/image56.png)</span></span>

<span data-ttu-id="65356-1098">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1098">**Description**</span></span>

<span data-ttu-id="65356-1099">이 이벤트는 USBX 디바이스 클래스 스토리지 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1099">This event represents a USBX Device Class Storage Write Event.</span></span>

<span data-ttu-id="65356-1100">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1100">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1101">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1101">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1102">정보 필드 2: Lun</span><span class="sxs-lookup"><span data-stu-id="65356-1102">Info Field 2: Lun.</span></span>
- <span data-ttu-id="65356-1103">정보 필드 3: 섹터</span><span class="sxs-lookup"><span data-stu-id="65356-1103">Info Field 3: Sector.</span></span>
- <span data-ttu-id="65356-1104">정보 필드 4: 섹터 수</span><span class="sxs-lookup"><span data-stu-id="65356-1104">Info Field 4: Number sectors.</span></span>

### <a name="device-stack-alternate-setting-get"></a><span data-ttu-id="65356-1105">디바이스 스택 대체 설정 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1105">Device Stack Alternate Setting Get</span></span> 

#### <a name="ux_device_class_alternate_setting_get"></a><span data-ttu-id="65356-1106">ux_device_class_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="65356-1106">ux_device_class_alternate_setting_get</span></span>

<span data-ttu-id="65356-1107">**아이콘** ![디바이스 스택 대체 설정 가져오기 아이콘](./media/user-guide/usbx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1107">**Icon** ![Device Stack Alternate Setting Get icon](./media/user-guide/usbx-events/image57.png)</span></span>

<span data-ttu-id="65356-1108">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1108">**Description**</span></span>

<span data-ttu-id="65356-1109">이 이벤트는 USBX 디바이스 스택 대체 설정 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1109">This event represents a USBX Device Stack Alternate Setting Get Event.</span></span>

<span data-ttu-id="65356-1110">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1110">**Information Fields**</span></span>

- <span data-ttu-id="65356-1111">정보 필드 1: 인터페이스 값</span><span class="sxs-lookup"><span data-stu-id="65356-1111">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="65356-1112">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1112">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1113">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1113">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1114">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1114">Info Field 4: Not used.</span></span>

### <a name="device-stack-alternate-setting-set"></a><span data-ttu-id="65356-1115">디바이스 스택 대체 설정 설정</span><span class="sxs-lookup"><span data-stu-id="65356-1115">Device Stack Alternate Setting Set</span></span> 

#### <a name="ux_device_class_alternate_setting_set"></a><span data-ttu-id="65356-1116">ux_device_class_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="65356-1116">ux_device_class_alternate_setting_set</span></span>

<span data-ttu-id="65356-1117">**아이콘** ![디바이스 스택 대체 설정 설정 아이콘](./media/user-guide/usbx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1117">**Icon** ![Device Stack Alternate Setting Set icon](./media/user-guide/usbx-events/image58.png)</span></span>

<span data-ttu-id="65356-1118">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1118">**Description**</span></span>

<span data-ttu-id="65356-1119">이 이벤트는 USBX 디바이스 스택 대체 설정 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1119">This event represents a USBX Device Stack Alternate Setting Set Event.</span></span>

<span data-ttu-id="65356-1120">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1120">**Information Fields**</span></span>
- <span data-ttu-id="65356-1121">정보 필드 1: 인터페이스 값</span><span class="sxs-lookup"><span data-stu-id="65356-1121">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="65356-1122">정보 필드 2: 대체 설정 값</span><span class="sxs-lookup"><span data-stu-id="65356-1122">Info Field 2: Alternate setting value.</span></span>
- <span data-ttu-id="65356-1123">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1123">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1124">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1124">Info Field 4: Not used.</span></span>

### <a name="device-stack-class-register"></a><span data-ttu-id="65356-1125">디바이스 스택 클래스 등록</span><span class="sxs-lookup"><span data-stu-id="65356-1125">Device Stack Class Register</span></span> 

#### <a name="ux_device_stack_class_register"></a><span data-ttu-id="65356-1126">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="65356-1126">ux_device_stack_class_register</span></span>

<span data-ttu-id="65356-1127">**아이콘** ![디바이스 스택 클래스 등록 아이콘](./media/user-guide/usbx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1127">**Icon** ![Device Stack Class Register icon](./media/user-guide/usbx-events/image59.png)</span></span>

<span data-ttu-id="65356-1128">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1128">**Description**</span></span>

<span data-ttu-id="65356-1129">이 이벤트는 USBX 디바이스 스택 클래스 등록 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1129">This event represents a USBX Device Stack Class Register Event.</span></span>

<span data-ttu-id="65356-1130">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1130">**Information Fields**</span></span>

- <span data-ttu-id="65356-1131">정보 필드 1: 클래스 이름</span><span class="sxs-lookup"><span data-stu-id="65356-1131">Info Field 1: Class name.</span></span>
- <span data-ttu-id="65356-1132">정보 필드 2: 인터페이스 번호</span><span class="sxs-lookup"><span data-stu-id="65356-1132">Info Field 2: Interface number.</span></span>
- <span data-ttu-id="65356-1133">정보 필드 3: 매개 변수</span><span class="sxs-lookup"><span data-stu-id="65356-1133">Info Field 3: Parameter.</span></span>
- <span data-ttu-id="65356-1134">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1134">Info Field 4: Not used.</span></span>

### <a name="device-stack-clear-feature"></a><span data-ttu-id="65356-1135">디바이스 스택 지우기 기능</span><span class="sxs-lookup"><span data-stu-id="65356-1135">Device Stack Clear Feature</span></span> 

#### <a name="ux_device_stack_clear_feature"></a><span data-ttu-id="65356-1136">ux_device_stack_clear_feature</span><span class="sxs-lookup"><span data-stu-id="65356-1136">ux_device_stack_clear_feature</span></span>

<span data-ttu-id="65356-1137">**아이콘** ![디바이스 스택 지우기 기능 아이콘](./media/user-guide/usbx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1137">**Icon** ![Device Stack Clear Feature icon](./media/user-guide/usbx-events/image60.png)</span></span>

<span data-ttu-id="65356-1138">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1138">**Description**</span></span>

<span data-ttu-id="65356-1139">이 이벤트는 USBX 디바이스 스택 지우기 기능 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1139">This event represents a USBX Device Stack Clear Feature Event.</span></span>

<span data-ttu-id="65356-1140">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1140">**Information Fields**</span></span>

- <span data-ttu-id="65356-1141">정보 필드 1: 요청 유형</span><span class="sxs-lookup"><span data-stu-id="65356-1141">Info Field 1: Request type.</span></span>
- <span data-ttu-id="65356-1142">정보 필드 2: 요청 값</span><span class="sxs-lookup"><span data-stu-id="65356-1142">Info Field 2: Request value.</span></span> <span data-ttu-id="65356-1143">정보 필드 3: 요청 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-1143">Info Field 3: Request index.</span></span>
- <span data-ttu-id="65356-1144">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1144">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-get"></a><span data-ttu-id="65356-1145">디바이스 스택 구성 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1145">Device Stack Configuration Get</span></span> 

#### <a name="ux_device_stack_configuration_get-t"></a><span data-ttu-id="65356-1146">ux_device_stack_configuration_get t</span><span class="sxs-lookup"><span data-stu-id="65356-1146">ux_device_stack_configuration_get t</span></span>

<span data-ttu-id="65356-1147">**아이콘** ![디바이스 스택 구성 가져오기 아이콘](./media/user-guide/usbx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1147">**Icon** ![Device Stack Configuration Get icon](./media/user-guide/usbx-events/image61.png)</span></span>

<span data-ttu-id="65356-1148">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1148">**Description**</span></span>

<span data-ttu-id="65356-1149">이 이벤트는 USBX 디바이스 스택 구성 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1149">This event represents a USBX Device Stack Configuration Get Event.</span></span>

<span data-ttu-id="65356-1150">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1150">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1151">정보 필드 1: 구성 값</span><span class="sxs-lookup"><span data-stu-id="65356-1151">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="65356-1152">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1152">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1153">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1153">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1154">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1154">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-set"></a><span data-ttu-id="65356-1155">디바이스 스택 구성 설정</span><span class="sxs-lookup"><span data-stu-id="65356-1155">Device Stack Configuration Set</span></span> 

#### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="65356-1156">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="65356-1156">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="65356-1157">**아이콘** ![디바이스 스택 구성 설정 아이콘](./media/user-guide/usbx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1157">**Icon** ![Device Stack Configuration Set icon](./media/user-guide/usbx-events/image62.png)</span></span>

<span data-ttu-id="65356-1158">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1158">**Description**</span></span>

<span data-ttu-id="65356-1159">이 이벤트는 USBX 디바이스 스택 구성 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1159">This event represents a USBX Device Stack Configuration Set Event.</span></span>

<span data-ttu-id="65356-1160">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1160">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1161">정보 필드 1: 구성 값</span><span class="sxs-lookup"><span data-stu-id="65356-1161">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="65356-1162">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1162">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1163">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1163">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1164">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1164">Info Field 4: Not used.</span></span>

### <a name="device-stack-connect"></a><span data-ttu-id="65356-1165">디바이스 스택 연결</span><span class="sxs-lookup"><span data-stu-id="65356-1165">Device Stack Connect</span></span> 

#### <a name="ux_device_stack_connect"></a><span data-ttu-id="65356-1166">ux_device_stack_connect</span><span class="sxs-lookup"><span data-stu-id="65356-1166">ux_device_stack_connect</span></span>

<span data-ttu-id="65356-1167">**아이콘** ![디바이스 스택 연결 아이콘](./media/user-guide/usbx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1167">**Icon** ![Device Stack Connect icon](./media/user-guide/usbx-events/image63.png)</span></span>

<span data-ttu-id="65356-1168">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1168">**Description**</span></span>

<span data-ttu-id="65356-1169">이 이벤트는 USBX 디바이스 스택 설명자 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1169">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="65356-1170">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1170">**Information Fields**</span></span>

- <span data-ttu-id="65356-1171">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1171">Info Field 1: Not used.</span></span>
- <span data-ttu-id="65356-1172">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1172">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1173">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1173">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1174">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1174">Info Field 4: Not used.</span></span>

### <a name="device-stack-descriptor-send"></a><span data-ttu-id="65356-1175">디바이스 스택 설명자 보내기</span><span class="sxs-lookup"><span data-stu-id="65356-1175">Device Stack Descriptor Send</span></span> 

#### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="65356-1176">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="65356-1176">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="65356-1177">**아이콘** ![디바이스 스택 설명자 보내기 아이콘](./media/user-guide/usbx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1177">**Icon** ![Device Stack Descriptor Send icon](./media/user-guide/usbx-events/image64.png)</span></span>

<span data-ttu-id="65356-1178">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1178">**Description**</span></span>

<span data-ttu-id="65356-1179">이 이벤트는 USBX 디바이스 스택 설명자 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1179">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="65356-1180">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1180">**Information Fields**</span></span>

- <span data-ttu-id="65356-1181">정보 필드 1: 설명자 유형</span><span class="sxs-lookup"><span data-stu-id="65356-1181">Info Field 1: Descriptor type.</span></span>
- <span data-ttu-id="65356-1182">정보 필드 2: 요청 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-1182">Info Field 2: Request index.</span></span>
- <span data-ttu-id="65356-1183">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1183">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1184">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1184">Info Field 4: Not used.</span></span>

### <a name="device-stack-disconnect"></a><span data-ttu-id="65356-1185">디바이스 스택 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="65356-1185">Device Stack Disconnect</span></span> 

#### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="65356-1186">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="65356-1186">ux_device_stack_disconnect</span></span>

<span data-ttu-id="65356-1187">**아이콘** ![디바이스 스택 연결 끊기 아이콘](./media/user-guide/usbx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1187">**Icon** ![Device Stack Disconnect icon](./media/user-guide/usbx-events/image65.png)</span></span>

<span data-ttu-id="65356-1188">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1188">**Description**</span></span>

<span data-ttu-id="65356-1189">이 이벤트는 USBX 디바이스 스택 연결 끊기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1189">This event represents a USBX Device Stack Disconnect Event.</span></span>

<span data-ttu-id="65356-1190">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1190">**Information Fields**</span></span>

- <span data-ttu-id="65356-1191">정보 필드 1: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-1191">Info Field 1: Device.</span></span>
- <span data-ttu-id="65356-1192">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1192">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1193">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1193">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1194">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1194">Info Field 4: Not used.</span></span>

### <a name="device-stack-endpoint-stall"></a><span data-ttu-id="65356-1195">디바이스 스택 엔드포인트 정지</span><span class="sxs-lookup"><span data-stu-id="65356-1195">Device Stack Endpoint Stall</span></span> 

#### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="65356-1196">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="65356-1196">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="65356-1197">**아이콘** ![디바이스 스택 엔드포인트 정지 아이콘](./media/user-guide/usbx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1197">**Icon** ![Device Stack Endpoint Stall icon](./media/user-guide/usbx-events/image66.png)</span></span>

<span data-ttu-id="65356-1198">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1198">**Description**</span></span>

<span data-ttu-id="65356-1199">이 이벤트는 USBX 디바이스 스택 엔드포인트 정지 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1199">This event represents a USBX Device Stack Endpoint Stall Event.</span></span>

<span data-ttu-id="65356-1200">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1200">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1201">정보 필드 1: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-1201">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="65356-1202">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1202">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1203">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1203">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1204">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1204">Info Field 4: Not used.</span></span>

### <a name="device-stack-get-status"></a><span data-ttu-id="65356-1205">디바이스 스택 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1205">Device Stack Get Status</span></span> 

#### <a name="ux_device_stack_get_status"></a><span data-ttu-id="65356-1206">ux_device_stack_get_status</span><span class="sxs-lookup"><span data-stu-id="65356-1206">ux_device_stack_get_status</span></span>

<span data-ttu-id="65356-1207">**아이콘** ![디바이스 스택 상태 가져오기 아이콘](./media/user-guide/usbx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1207">**Icon** ![Device Stack Get Status icon](./media/user-guide/usbx-events/image67.png)</span></span>

<span data-ttu-id="65356-1208">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1208">**Description**</span></span>

<span data-ttu-id="65356-1209">이 이벤트는 USBX 디바이스 스택 상태 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1209">This event represents a USBX Device Stack Get Status Event.</span></span>

<span data-ttu-id="65356-1210">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1210">**Information Fields**</span></span>

- <span data-ttu-id="65356-1211">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1211">Info Field 1: Not used.</span></span>
- <span data-ttu-id="65356-1212">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1212">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1213">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1213">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1214">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1214">Info Field 4: Not used.</span></span>

### <a name="device-stack-host-wakeup"></a><span data-ttu-id="65356-1215">디바이스 스택 호스트 절전 모드 해제</span><span class="sxs-lookup"><span data-stu-id="65356-1215">Device Stack Host Wakeup</span></span> 

#### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="65356-1216">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="65356-1216">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="65356-1217">**아이콘** ![디바이스 스택 호스트 절전 모드 해제 아이콘](./media/user-guide/usbx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1217">**Icon** ![Device Stack Host Wakeup icon](./media/user-guide/usbx-events/image68.png)</span></span>

<span data-ttu-id="65356-1218">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1218">**Description**</span></span>

<span data-ttu-id="65356-1219">이 이벤트는 USBX 디바이스 스택 호스트 절전 모드 해제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1219">This event represents a USBX Device Stack Host Wakeup Event.</span></span>

<span data-ttu-id="65356-1220">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1220">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1221">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1221">Info Field 1: Not used.</span></span>
- <span data-ttu-id="65356-1222">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1222">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1223">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1223">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1224">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1224">Info Field 4: Not used.</span></span>

### <a name="device-stack-initialize"></a><span data-ttu-id="65356-1225">디바이스 스택 초기화</span><span class="sxs-lookup"><span data-stu-id="65356-1225">Device Stack Initialize</span></span> 

#### <a name="ux_device_stack_initialize"></a><span data-ttu-id="65356-1226">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="65356-1226">ux_device_stack_initialize</span></span>

<span data-ttu-id="65356-1227">**아이콘** ![디바이스 스택 초기화 아이콘](./media/user-guide/usbx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1227">**Icon** ![Device Stack Initialize icon](./media/user-guide/usbx-events/image69.png)</span></span>

<span data-ttu-id="65356-1228">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1228">**Description**</span></span>

<span data-ttu-id="65356-1229">이 이벤트는 USBX 디바이스 스택 초기화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1229">This event represents a USBX Device Stack Initialize Event.</span></span>

<span data-ttu-id="65356-1230">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1230">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1231">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1231">Info Field 1: Not used.</span></span>
- <span data-ttu-id="65356-1232">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1232">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1233">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1233">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1234">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1234">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-delete"></a><span data-ttu-id="65356-1235">디바이스 스택 인터페이스 삭제</span><span class="sxs-lookup"><span data-stu-id="65356-1235">Device Stack Interface Delete</span></span> 

#### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="65356-1236">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="65356-1236">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="65356-1237">**아이콘** ![디바이스 스택 인터페이스 삭제 아이콘](./media/user-guide/usbx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1237">**Icon** ![Device Stack Interface Delete icon](./media/user-guide/usbx-events/image70.png)</span></span>

<span data-ttu-id="65356-1238">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1238">**Description**</span></span>

<span data-ttu-id="65356-1239">이 이벤트는 USBX 디바이스 스택 인터페이스 삭제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1239">This event represents a USBX Device Stack Interface Delete Event.</span></span>

<span data-ttu-id="65356-1240">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1240">**Information Fields**</span></span>

- <span data-ttu-id="65356-1241">정보 필드 1: 인터페이스</span><span class="sxs-lookup"><span data-stu-id="65356-1241">Info Field 1: Interface.</span></span>
- <span data-ttu-id="65356-1242">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1242">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1243">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1243">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1244">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1244">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-get"></a><span data-ttu-id="65356-1245">디바이스 스택 인터페이스 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1245">Device Stack Interface Get</span></span> 

#### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="65356-1246">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="65356-1246">ux_device_stack_interface_get</span></span>

<span data-ttu-id="65356-1247">**아이콘** ![디바이스 스택 인터페이스 가져오기 아이콘](./media/user-guide/usbx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1247">**Icon** ![Device Stack Interface Get icon](./media/user-guide/usbx-events/image71.png)</span></span>

<span data-ttu-id="65356-1248">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1248">**Description**</span></span>

<span data-ttu-id="65356-1249">이 이벤트는 USBX 디바이스 스택 인터페이스 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1249">This event represents a USBX Device Stack Interface Get Event.</span></span>

<span data-ttu-id="65356-1250">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1250">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1251">정보 필드 1: 인터페이스 값</span><span class="sxs-lookup"><span data-stu-id="65356-1251">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="65356-1252">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1252">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1253">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1253">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1254">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1254">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-set"></a><span data-ttu-id="65356-1255">디바이스 스택 인터페이스 설정</span><span class="sxs-lookup"><span data-stu-id="65356-1255">Device Stack Interface Set</span></span> 

#### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="65356-1256">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="65356-1256">ux_device_stack_interface_set</span></span>

<span data-ttu-id="65356-1257">**아이콘** ![디바이스 스택 인터페이스 설정 아이콘](./media/user-guide/usbx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1257">**Icon** ![Device Stack Interface Set icon](./media/user-guide/usbx-events/image72.png)</span></span>

<span data-ttu-id="65356-1258">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1258">**Description**</span></span>

<span data-ttu-id="65356-1259">이 이벤트는 USBX 디바이스 스택 인터페이스 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1259">This event represents a USBX Device Stack Interface Set Event.</span></span>

<span data-ttu-id="65356-1260">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1260">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1261">정보 필드 1: 요청 값</span><span class="sxs-lookup"><span data-stu-id="65356-1261">Info Field 1: Request value.</span></span> <span data-ttu-id="65356-1262">정보 필드 2: 요청 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-1262">Info Field 2: Request index.</span></span>
- <span data-ttu-id="65356-1263">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1263">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1264">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1264">Info Field 4: Not used.</span></span>

### <a name="device-stack-set-feature"></a><span data-ttu-id="65356-1265">디바이스 스택 설정 기능</span><span class="sxs-lookup"><span data-stu-id="65356-1265">Device Stack Set Feature</span></span> 

#### <a name="ux_device_stack_set_feature"></a><span data-ttu-id="65356-1266">ux_device_stack_set_feature</span><span class="sxs-lookup"><span data-stu-id="65356-1266">ux_device_stack_set_feature</span></span>

<span data-ttu-id="65356-1267">**아이콘** ![디바이스 스택 설정 기능 아이콘](./media/user-guide/usbx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1267">**Icon** ![Device Stack Set Feature icon](./media/user-guide/usbx-events/image73.png)</span></span>

<span data-ttu-id="65356-1268">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1268">**Description**</span></span>

<span data-ttu-id="65356-1269">이 이벤트는 USBX 디바이스 스택 설정 기능 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1269">This event represents a USBX Device Stack Set Feature Event.</span></span>

<span data-ttu-id="65356-1270">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1270">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1271">정보 필드 1: 요청 값</span><span class="sxs-lookup"><span data-stu-id="65356-1271">Info Field 1: Request value.</span></span> <span data-ttu-id="65356-1272">정보 필드 2: 요청 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-1272">Info Field 2: Request index.</span></span>
- <span data-ttu-id="65356-1273">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1273">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1274">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1274">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-abort"></a><span data-ttu-id="65356-1275">디바이스 스택 전송 중단</span><span class="sxs-lookup"><span data-stu-id="65356-1275">Device Stack Transfer Abort</span></span> 

#### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="65356-1276">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="65356-1276">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="65356-1277">**아이콘** ![디바이스 스택 전송 중단 아이콘](./media/user-guide/usbx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1277">**Icon** ![Device Stack Transfer Abort icon](./media/user-guide/usbx-events/image74.png)</span></span>

<span data-ttu-id="65356-1278">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1278">**Description**</span></span>

<span data-ttu-id="65356-1279">이 이벤트는 USBX 디바이스 스택 전송 중단 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1279">This event represents a USBX Device Stack Transfer Abort Event.</span></span>

<span data-ttu-id="65356-1280">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1280">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1281">정보 필드 1: 전송 요청</span><span class="sxs-lookup"><span data-stu-id="65356-1281">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="65356-1282">정보 필드 2: 완료 코드</span><span class="sxs-lookup"><span data-stu-id="65356-1282">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="65356-1283">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1283">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1284">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1284">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-all-request-abort"></a><span data-ttu-id="65356-1285">디바이스 스택 전송 모든 요청 중단</span><span class="sxs-lookup"><span data-stu-id="65356-1285">Device Stack Transfer All Request Abort</span></span> 

#### <a name="ux_device_stack_transfer_all_request_abort"></a><span data-ttu-id="65356-1286">ux_device_stack_transfer_all_request_abort</span><span class="sxs-lookup"><span data-stu-id="65356-1286">ux_device_stack_transfer_all_request_abort</span></span>

<span data-ttu-id="65356-1287">**아이콘** ![디바이스 스택 전송 모든 요청 중단 아이콘](./media/user-guide/usbx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1287">**Icon** ![Device Stack Transfer All Request Abort icon](./media/user-guide/usbx-events/image75.png)</span></span>

<span data-ttu-id="65356-1288">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1288">**Description**</span></span>

<span data-ttu-id="65356-1289">이 이벤트는 USBX 디바이스 스택 전송 모든 요청 중단 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1289">This event represents a USBX Device Stack Transfer All Request Abort Event.</span></span>

<span data-ttu-id="65356-1290">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1290">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1291">정보 필드 1: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-1291">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="65356-1292">정보 필드 2: 완료 코드</span><span class="sxs-lookup"><span data-stu-id="65356-1292">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="65356-1293">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1293">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1294">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1294">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-request"></a><span data-ttu-id="65356-1295">디바이스 스택 전송 요청</span><span class="sxs-lookup"><span data-stu-id="65356-1295">Device Stack Transfer Request</span></span> 

#### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="65356-1296">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="65356-1296">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="65356-1297">**아이콘** ![디바이스 스택 전송 요청 아이콘](./media/user-guide/usbx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1297">**Icon** ![Device Stack Transfer Request icon](./media/user-guide/usbx-events/image76.png)</span></span>

<span data-ttu-id="65356-1298">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1298">**Description**</span></span>

<span data-ttu-id="65356-1299">이 이벤트는 USBX 디바이스 스택 전송 요청 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1299">This event represents a USBX Device Stack Transfer Request Event.</span></span>

<span data-ttu-id="65356-1300">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1300">**Information Fields**</span></span>

- <span data-ttu-id="65356-1301">정보 필드 1: 전송 요청</span><span class="sxs-lookup"><span data-stu-id="65356-1301">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="65356-1302">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1302">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1303">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1303">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1304">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1304">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-activate"></a><span data-ttu-id="65356-1305">호스트 클래스 Asix 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1305">Host Class Asix Activate</span></span> 

#### <a name="ux_host_class_asix_activate"></a><span data-ttu-id="65356-1306">ux_host_class_asix_activate</span><span class="sxs-lookup"><span data-stu-id="65356-1306">ux_host_class_asix_activate</span></span>

<span data-ttu-id="65356-1307">**아이콘** ![호스트 클래스 Asix 활성화 아이콘](./media/user-guide/usbx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1307">**Icon** ![Host Class Asix Activate icon](./media/user-guide/usbx-events/image77.png)</span></span>

<span data-ttu-id="65356-1308">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1308">**Description**</span></span>

<span data-ttu-id="65356-1309">이 이벤트는 USBX 호스트 클래스 Asix 활성화를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1309">This event represents a USBX Host Class Asix Activate.</span></span>

<span data-ttu-id="65356-1310">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1310">**Information Fields**</span></span>

- <span data-ttu-id="65356-1311">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1311">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1312">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1312">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1313">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1313">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1314">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1314">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-deactivate"></a><span data-ttu-id="65356-1315">호스트 클래스 Asix 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1315">Host Class Asix Deactivate</span></span> 

#### <a name="ux_host_class_asix_deactivate"></a><span data-ttu-id="65356-1316">ux_host_class_asix_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-1316">ux_host_class_asix_deactivate</span></span>

<span data-ttu-id="65356-1317">**아이콘** ![호스트 클래스 Asix 비활성화 아이콘](./media/user-guide/usbx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1317">**Icon** ![Host Class Asix Deactivate icon](./media/user-guide/usbx-events/image78.png)</span></span>

<span data-ttu-id="65356-1318">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1318">**Description**</span></span>

<span data-ttu-id="65356-1319">이 이벤트는 USBX 호스트 클래스 Asix 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1319">This event represents a USBX Host Class Asix Deactivate Event.</span></span>

<span data-ttu-id="65356-1320">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1320">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1321">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1321">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1322">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1322">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1323">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1323">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1324">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1324">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-interrupt-notification"></a><span data-ttu-id="65356-1325">호스트 클래스 Asix 인터럽트 알림</span><span class="sxs-lookup"><span data-stu-id="65356-1325">Host Class Asix Interrupt Notification</span></span> 

#### <a name="ux_host_class_asix_interrupt_notification"></a><span data-ttu-id="65356-1326">ux_host_class_asix_interrupt_notification</span><span class="sxs-lookup"><span data-stu-id="65356-1326">ux_host_class_asix_interrupt_notification</span></span>

<span data-ttu-id="65356-1327">**아이콘** ![호스트 클래스 Asix 인터럽트 알림 아이콘](./media/user-guide/usbx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1327">**Icon** ![Host Class Asix Interrupt Notification icon](./media/user-guide/usbx-events/image79.png)</span></span>

<span data-ttu-id="65356-1328">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1328">**Description**</span></span>

<span data-ttu-id="65356-1329">이 이벤트는 USBX 호스트 클래스 Asix 인터럽트 알림 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1329">This event represents a USBX Host Class Asix Interrupt Notification Event.</span></span>

<span data-ttu-id="65356-1330">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1330">**Information Fields**</span></span>

- <span data-ttu-id="65356-1331">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1331">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-1332">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1332">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1333">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1333">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1334">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1334">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-read"></a><span data-ttu-id="65356-1335">호스트 클래스 Asix 읽기</span><span class="sxs-lookup"><span data-stu-id="65356-1335">Host Class Asix Read</span></span> 

#### <a name="ux_host_class_asix_read"></a><span data-ttu-id="65356-1336">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="65356-1336">ux_host_class_asix_read</span></span>

<span data-ttu-id="65356-1337">**아이콘** ![호스트 클래스 Asix 읽기 아이콘](./media/user-guide/usbx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1337">**Icon** ![Host Class Asix Read icon](./media/user-guide/usbx-events/image80.png)</span></span>

<span data-ttu-id="65356-1338">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1338">**Description**</span></span>

<span data-ttu-id="65356-1339">이 이벤트는 USBX 호스트 클래스 Asix 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1339">This event represents a USBX Host Class Asix Read Event.</span></span>

<span data-ttu-id="65356-1340">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1340">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1341">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1341">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1342">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-1342">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-1343">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-1343">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-1344">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1344">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-write"></a><span data-ttu-id="65356-1345">호스트 클래스 Asix 쓰기</span><span class="sxs-lookup"><span data-stu-id="65356-1345">Host Class Asix Write</span></span> 

#### <a name="ux_host_class_asix_write"></a><span data-ttu-id="65356-1346">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="65356-1346">ux_host_class_asix_write</span></span>

<span data-ttu-id="65356-1347">**아이콘** ![호스트 클래스 Asix 쓰기 아이콘](./media/user-guide/usbx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1347">**Icon** ![Host Class Asix Write icon](./media/user-guide/usbx-events/image81.png)</span></span>

<span data-ttu-id="65356-1348">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1348">**Description**</span></span>

<span data-ttu-id="65356-1349">이 이벤트는 USBX 호스트 클래스 Asix 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1349">This event represents a USBX Host Class Asix Write Event.</span></span>

<span data-ttu-id="65356-1350">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1350">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1351">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1351">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1352">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-1352">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-1353">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-1353">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-1354">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1354">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-activate"></a><span data-ttu-id="65356-1355">호스트 클래스 오디오 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1355">Host Class Audio Activate</span></span> 

#### <a name="ux_host_class_audio_activate"></a><span data-ttu-id="65356-1356">ux_host_class_audio_activate</span><span class="sxs-lookup"><span data-stu-id="65356-1356">ux_host_class_audio_activate</span></span>

<span data-ttu-id="65356-1357">**아이콘** ![호스트 클래스 오디오 활성화 아이콘](./media/user-guide/usbx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1357">**Icon** ![Host Class Audio Activate icon](./media/user-guide/usbx-events/image82.png)</span></span>

<span data-ttu-id="65356-1358">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1358">**Description**</span></span>

<span data-ttu-id="65356-1359">이 이벤트는 USBX 호스트 클래스 오디오 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1359">This event represents a USBX Host Class Audio Activate Event.</span></span>

<span data-ttu-id="65356-1360">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1360">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1361">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1361">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1362">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1362">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1363">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1363">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1364">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1364">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-get"></a><span data-ttu-id="65356-1365">호스트 클래스 오디오 컨트롤 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1365">Host Class Audio Control Value Get</span></span> 

#### <a name="ux_host_class_audio_control_value_get"></a><span data-ttu-id="65356-1366">ux_host_class_audio_control_value_get</span><span class="sxs-lookup"><span data-stu-id="65356-1366">ux_host_class_audio_control_value_get</span></span>

<span data-ttu-id="65356-1367">**아이콘** ![호스트 클래스 오디오 컨트롤 값 가져오기 아이콘](./media/user-guide/usbx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1367">**Icon** ![Host Class Audio Control Value Get icon](./media/user-guide/usbx-events/image83.png)</span></span>

<span data-ttu-id="65356-1368">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1368">**Description**</span></span>

<span data-ttu-id="65356-1369">이 이벤트는 USBX 호스트 클래스 오디오 컨트롤 값 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1369">This event represents a USBX Host Class Audio Control Value Get Event.</span></span>

<span data-ttu-id="65356-1370">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1370">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1371">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1371">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1372">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1372">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1373">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1373">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1374">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1374">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-set"></a><span data-ttu-id="65356-1375">호스트 클래스 오디오 컨트롤 값 설정</span><span class="sxs-lookup"><span data-stu-id="65356-1375">Host Class Audio Control Value Set</span></span> 

#### <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="65356-1376">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="65356-1376">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="65356-1377">**아이콘** ![호스트 클래스 오디오 컨트롤 값 설정 아이콘](./media/user-guide/usbx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1377">**Icon** ![Host Class Audio Control Value Set icon](./media/user-guide/usbx-events/image84.png)</span></span>

<span data-ttu-id="65356-1378">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1378">**Description**</span></span>

<span data-ttu-id="65356-1379">이 이벤트는 내부 NetX I/O 드라이버 지연 처리 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1379">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="65356-1380">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1380">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1381">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1381">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1382">정보 필드 2: 오디오 컨트롤</span><span class="sxs-lookup"><span data-stu-id="65356-1382">Info Field 2: Audio control.</span></span>
- <span data-ttu-id="65356-1383">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1383">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1384">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1384">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-deactivate"></a><span data-ttu-id="65356-1385">호스트 클래스 오디오 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1385">Host Class Audio Deactivate</span></span> 

#### <a name="ux_host_class_audio_deactivate"></a><span data-ttu-id="65356-1386">ux_host_class_audio_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-1386">ux_host_class_audio_deactivate</span></span>

<span data-ttu-id="65356-1387">**아이콘** ![호스트 클래스 오디오 비활성화 아이콘](./media/user-guide/usbx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1387">**Icon** ![Host Class Audio Deactivate icon](./media/user-guide/usbx-events/image85.png)</span></span>

<span data-ttu-id="65356-1388">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1388">**Description**</span></span>

<span data-ttu-id="65356-1389">이 이벤트는 USBX 호스트 클래스 오디오 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1389">This event represents a USBX Host Class Audio Deactivate Event.</span></span>

<span data-ttu-id="65356-1390">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1390">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1391">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1391">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1392">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1392">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1393">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1393">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1394">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1394">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-read"></a><span data-ttu-id="65356-1395">호스트 클래스 오디오 읽기</span><span class="sxs-lookup"><span data-stu-id="65356-1395">Host Class Audio Read</span></span> 

#### <a name="ux_host_class_audio_read"></a><span data-ttu-id="65356-1396">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="65356-1396">ux_host_class_audio_read</span></span>

<span data-ttu-id="65356-1397">**아이콘** ![호스트 클래스 오디오 읽기 아이콘](./media/user-guide/usbx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1397">**Icon** ![Host Class Audio Read icon](./media/user-guide/usbx-events/image86.png)</span></span>

<span data-ttu-id="65356-1398">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1398">**Description**</span></span>

<span data-ttu-id="65356-1399">이 이벤트는 USBX 호스트 클래스 오디오 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1399">This event represents a USBX Host Class Audio Read Event.</span></span>

- <span data-ttu-id="65356-1400">정보 필드</span><span class="sxs-lookup"><span data-stu-id="65356-1400">Information Fields</span></span> 
- <span data-ttu-id="65356-1401">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1401">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1402">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-1402">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-1403">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-1403">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-1404">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1404">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-get"></a><span data-ttu-id="65356-1405">호스트 클래스 오디오 스트리밍 샘플링 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1405">Host Class Audio Streaming Sampling Get</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="65356-1406">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="65356-1406">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="65356-1407">**아이콘** ![호스트 클래스 오디오 스트리밍 샘플링 가져오기 아이콘](./media/user-guide/usbx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1407">**Icon** ![Host Class Audio Streaming Sampling Get icon](./media/user-guide/usbx-events/image87.png)</span></span>

<span data-ttu-id="65356-1408">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1408">**Description**</span></span>

<span data-ttu-id="65356-1409">이 이벤트는 USBX 호스트 클래스 오디오 스트리밍 샘플링 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1409">This event represents a USBX Host Class Audio Streaming Sampling Get Event.</span></span>

<span data-ttu-id="65356-1410">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1410">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1411">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1411">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1412">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1412">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1413">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1413">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1414">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1414">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-set"></a><span data-ttu-id="65356-1415">호스트 클래스 오디오 스트리밍 샘플링 설정</span><span class="sxs-lookup"><span data-stu-id="65356-1415">Host Class Audio Streaming Sampling Set</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="65356-1416">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="65356-1416">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="65356-1417">**아이콘** ![호스트 클래스 오디오 스트리밍 샘플링 설정 아이콘](./media/user-guide/usbx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1417">**Icon** ![Host Class Audio Streaming Sampling Set icon](./media/user-guide/usbx-events/image88.png)</span></span>

<span data-ttu-id="65356-1418">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1418">**Description**</span></span>

<span data-ttu-id="65356-1419">이 이벤트는 USBX 호스트 클래스 오디오 스트리밍 샘플링 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1419">This event represents a USBX Host Class Audio Streaming Sampling Set Event.</span></span>

<span data-ttu-id="65356-1420">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1420">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1421">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1421">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1422">정보 필드 2: 오디오 샘플링</span><span class="sxs-lookup"><span data-stu-id="65356-1422">Info Field 2: Audio Sampling.</span></span>
- <span data-ttu-id="65356-1423">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1423">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1424">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1424">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-write"></a><span data-ttu-id="65356-1425">호스트 클래스 오디오 쓰기</span><span class="sxs-lookup"><span data-stu-id="65356-1425">Host Class Audio Write</span></span> 

#### <a name="ux_host_class_audio_write"></a><span data-ttu-id="65356-1426">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="65356-1426">ux_host_class_audio_write</span></span>

<span data-ttu-id="65356-1427">**아이콘** ![호스트 클래스 오디오 쓰기 아이콘](./media/user-guide/usbx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1427">**Icon** ![Host Class Audio Write icon](./media/user-guide/usbx-events/image89.png)</span></span>

<span data-ttu-id="65356-1428">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1428">**Description**</span></span>

<span data-ttu-id="65356-1429">이 이벤트는 USBX 호스트 클래스 오디오 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1429">This event represents a USBX Host Class Audio Write Event.</span></span>

<span data-ttu-id="65356-1430">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1430">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1431">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1431">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1432">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-1432">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-1433">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-1433">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-1434">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1434">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-activate"></a><span data-ttu-id="65356-1435">호스트 클래스 Cdc Acm 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1435">Host Class Cdc Acm Activate</span></span> 

#### <a name="ux_host_class_cdc_acm_activate"></a><span data-ttu-id="65356-1436">ux_host_class_cdc_acm_activate</span><span class="sxs-lookup"><span data-stu-id="65356-1436">ux_host_class_cdc_acm_activate</span></span>

<span data-ttu-id="65356-1437">**아이콘** ![호스트 클래스 Cdc Acm 활성화 아이콘](./media/user-guide/usbx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1437">**Icon** ![Host Class C D C A C M Activate icon](./media/user-guide/usbx-events/image90.png)</span></span>

<span data-ttu-id="65356-1438">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1438">**Description**</span></span>

<span data-ttu-id="65356-1439">이 이벤트는 USBX 호스트 클래스 Cdc Acm 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1439">This event represents a USBX Host Class Cdc Acm Activate Event.</span></span>

<span data-ttu-id="65356-1440">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1440">**Information Fields**</span></span>

- <span data-ttu-id="65356-1441">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1441">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1442">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1442">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1443">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1443">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1444">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1444">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-deactivate"></a><span data-ttu-id="65356-1445">호스트 클래스 Cdc Acm 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1445">Host Class Cdc Acm Deactivate</span></span> 

#### <a name="ux_host_class_cdc_acm_deactivate"></a><span data-ttu-id="65356-1446">ux_host_class_cdc_acm_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-1446">ux_host_class_cdc_acm_deactivate</span></span>

<span data-ttu-id="65356-1447">**아이콘** ![호스트 클래스 Cdc Acm 비활성화 아이콘](./media/user-guide/usbx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1447">**Icon** ![Host Class C D C A C M Deactivate icon](./media/user-guide/usbx-events/image91.png)</span></span>

<span data-ttu-id="65356-1448">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1448">**Description**</span></span>

<span data-ttu-id="65356-1449">이 이벤트는 USBX 호스트 클래스 Cdc Acm 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1449">This event represents a USBX Host Class Cdc Acm Deactivate Event.</span></span>

<span data-ttu-id="65356-1450">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1450">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1451">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1451">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1452">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1452">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1453">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1453">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1454">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1454">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a><span data-ttu-id="65356-1455">호스트 클래스 Cdc Acm Ioctl 파이프에서 중단</span><span class="sxs-lookup"><span data-stu-id="65356-1455">Host Class Cdc Acm Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a><span data-ttu-id="65356-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="65356-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="65356-1457">**아이콘** ![호스트 클래스 Cdc Acm Ioctl 파이프에서 중단 아이콘](./media/user-guide/usbx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1457">**Icon** ![Host Class C D C A C M I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image92.png)</span></span>

<span data-ttu-id="65356-1458">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1458">**Description**</span></span>

<span data-ttu-id="65356-1459">이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 파이프에서 중단 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1459">This event represents a USBX Host Class Cdc Acm Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="65356-1460">정보 필드</span><span class="sxs-lookup"><span data-stu-id="65356-1460">Information Fields</span></span> 

- <span data-ttu-id="65356-1461">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1461">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1462">정보 필드 2: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-1462">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="65356-1463">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1463">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1464">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1464">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a><span data-ttu-id="65356-1465">호스트 클래스 Cdc Acm Ioctl 파이프 외부에서 중단</span><span class="sxs-lookup"><span data-stu-id="65356-1465">Host Class Cdc Acm Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a><span data-ttu-id="65356-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="65356-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span></span>

<span data-ttu-id="65356-1467">**아이콘** ![[호스트 클래스 Cdc Acm Ioctl 파이프 외부에서 중단 아이콘](./media/user-guide/usbx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1467">**Icon** ![[Host Class C D C A C M I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image93.png)</span></span>

<span data-ttu-id="65356-1468">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1468">**Description**</span></span>

<span data-ttu-id="65356-1469">이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 파이프 외부에서 중단 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1469">This event represents a USBX Host Class Cdc Acm Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="65356-1470">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1470">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1471">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1471">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1472">정보 필드 2: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-1472">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="65356-1473">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1473">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1474">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1474">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a><span data-ttu-id="65356-1475">호스트 클래스 Cdc Acm Ioctl 디바이스 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1475">Host Class Cdc Acm Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a><span data-ttu-id="65356-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="65356-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span></span>

<span data-ttu-id="65356-1477">**아이콘** ![호스트 클래스 Cdc Acm Ioctl 디바이스 상태 가져오기 아이콘](./media/user-guide/usbx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1477">**Icon** ![Host Class C D C A C M I O C T L Get Device Status icon](./media/user-guide/usbx-events/image94.png)</span></span>

<span data-ttu-id="65356-1478">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1478">**Description**</span></span>

<span data-ttu-id="65356-1479">이 이벤트는 c # 호스트 클래스 Cdc Acm Ioctl 디바이스 상태 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1479">This event represents a USBX Host Class Cdc Acm Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="65356-1480">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1480">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1481">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1481">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1482">정보 필드 2: 디바이스 상태</span><span class="sxs-lookup"><span data-stu-id="65356-1482">Info Field 2: Device status.</span></span>
- <span data-ttu-id="65356-1483">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1483">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1484">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1484">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a><span data-ttu-id="65356-1485">호스트 클래스 Cdc Acm Ioctl 줄 코드 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1485">Host Class Cdc Acm Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="65356-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="65356-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span></span>

<span data-ttu-id="65356-1487">**아이콘** ![호스트 클래스 Cdc Acm Ioctl 줄 코드 가져오기 아이콘](./media/user-guide/usbx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1487">**Icon** ![Host Class C D C A C M I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image95.png)</span></span>

<span data-ttu-id="65356-1488">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1488">**Description**</span></span>

<span data-ttu-id="65356-1489">이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 줄 코드 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1489">This event represents a USBX Host Class Cdc Acm Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="65356-1490">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1490">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1491">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1491">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1492">정보 필드 2: 매개 변수</span><span class="sxs-lookup"><span data-stu-id="65356-1492">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="65356-1493">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1493">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1494">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1494">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a><span data-ttu-id="65356-1495">호스트 클래스 Cdc Acm Ioctl 알림 콜백</span><span class="sxs-lookup"><span data-stu-id="65356-1495">Host Class Cdc Acm Ioctl Notification Callback</span></span>

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a><span data-ttu-id="65356-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span><span class="sxs-lookup"><span data-stu-id="65356-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span></span>

<span data-ttu-id="65356-1497">**아이콘** ![호스트 클래스 Cdc Acm Ioctl 알림 콜백 아이콘](./media/user-guide/usbx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1497">**Icon** ![Host Class C D C A C M I O C T L Notification Callback icon](./media/user-guide/usbx-events/image96.png)</span></span>

<span data-ttu-id="65356-1498">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1498">**Description**</span></span>

<span data-ttu-id="65356-1499">이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 알림 콜백 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1499">This event represents a USBX Host Class Cdc Acm Ioctl Notification Callback Event.</span></span>

<span data-ttu-id="65356-1500">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1500">**Information Fields**</span></span>

- <span data-ttu-id="65356-1501">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1501">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1502">정보 필드 2: 매개 변수</span><span class="sxs-lookup"><span data-stu-id="65356-1502">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="65356-1503">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1503">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1504">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1504">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-send-break"></a><span data-ttu-id="65356-1505">호스트 클래스 Cdc Acm Ioctl 보내기 중단</span><span class="sxs-lookup"><span data-stu-id="65356-1505">Host Class Cdc Acm Ioctl Send Break</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a><span data-ttu-id="65356-1506">ux_host_class_cdc_acm_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="65356-1506">ux_host_class_cdc_acm_ioctl_send_break</span></span>

<span data-ttu-id="65356-1507">**아이콘** ![호스트 클래스 Cdc Acm Ioctl 보내기 중단 아이콘](./media/user-guide/usbx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1507">**Icon** ![Host Class C D C A C M I O C T L Send Break icon](./media/user-guide/usbx-events/image97.png)</span></span>

<span data-ttu-id="65356-1508">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1508">**Description**</span></span>

<span data-ttu-id="65356-1509">이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 보내기 중단 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1509">This event represents a USBX Host Class Cdc Acm Ioctl Send Break Event.</span></span>

<span data-ttu-id="65356-1510">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1510">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1511">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1511">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1512">정보 필드 2: 매개 변수</span><span class="sxs-lookup"><span data-stu-id="65356-1512">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="65356-1513">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1513">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1514">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1514">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a><span data-ttu-id="65356-1515">호스트 클래스 Cdc Acm Ioctl 줄 코드 설정</span><span class="sxs-lookup"><span data-stu-id="65356-1515">Host Class Cdc Acm Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="65356-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="65356-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span></span>

<span data-ttu-id="65356-1517">**아이콘** ![호스트 클래스 Cdc Acm Ioctl 줄 코드 설정 아이콘](./media/user-guide/usbx-events/image97.png) icon](./media/user-guide/usbx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1517">**Icon** ![The Host Class C D C A C M I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image97.png) icon](./media/user-guide/usbx-events/image98.png)</span></span>

<span data-ttu-id="65356-1518">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1518">**Description**</span></span>

<span data-ttu-id="65356-1519">이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 줄 코드 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1519">This event represents a USBX Host Class Cdc Acm Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="65356-1520">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1520">**Information Fields**</span></span>

- <span data-ttu-id="65356-1521">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1521">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1522">정보 필드 2: 매개 변수</span><span class="sxs-lookup"><span data-stu-id="65356-1522">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="65356-1523">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1523">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1524">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1524">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a><span data-ttu-id="65356-1525">호스트 클래스 Cdc Acm Ioctl 줄 상태 설정</span><span class="sxs-lookup"><span data-stu-id="65356-1525">Host Class Cdc Acm Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="65356-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="65356-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span></span>

<span data-ttu-id="65356-1527">**아이콘** ![호스트 클래스 Cdc Acm Ioctl 줄 상태 설정 아이콘](./media/user-guide/usbx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1527">**Icon** ![Host Class C D C A C M I O C T L Set Line State icon](./media/user-guide/usbx-events/image99.png)</span></span>

<span data-ttu-id="65356-1528">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1528">**Description**</span></span>

<span data-ttu-id="65356-1529">이 이벤트는 USBX 호스트 클래스 Cdc Acm Ioctl 줄 상태 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1529">This event represents a USBX Host Class Cdc Acm Ioctl Set Line State Event.</span></span>

<span data-ttu-id="65356-1530">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1530">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1531">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1531">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1532">정보 필드 2: 매개 변수</span><span class="sxs-lookup"><span data-stu-id="65356-1532">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="65356-1533">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1533">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1534">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1534">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-read"></a><span data-ttu-id="65356-1535">호스트 클래스 Cdc Acm 읽기</span><span class="sxs-lookup"><span data-stu-id="65356-1535">Host Class Cdc Acm Read</span></span> 

#### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="65356-1536">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="65356-1536">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="65356-1537">**아이콘** ![호스트 클래스 Cdc Acm 읽기 아이콘](./media/user-guide/usbx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1537">**Icon** ![Host Class C D C A C M Read icon](./media/user-guide/usbx-events/image100.png)</span></span>

<span data-ttu-id="65356-1538">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1538">**Description**</span></span>

<span data-ttu-id="65356-1539">이 이벤트는 USBX 호스트 클래스 Cdc Acm 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1539">This event represents a USBX Host Class Cdc Acm Read Event.</span></span>

<span data-ttu-id="65356-1540">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1540">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1541">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1541">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1542">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-1542">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-1543">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-1543">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="65356-1544">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1544">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-start"></a><span data-ttu-id="65356-1545">호스트 클래스 Cdc Acm 수신 시작</span><span class="sxs-lookup"><span data-stu-id="65356-1545">Host Class Cdc Acm Reception Start</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="65356-1546">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="65356-1546">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="65356-1547">**아이콘** ![호스트 클래스 Cdc Acm 수신 시작 아이콘](./media/user-guide/usbx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1547">**Icon** ![Host Class C D C A C M Reception Start icon](./media/user-guide/usbx-events/image101.png)</span></span>

<span data-ttu-id="65356-1548">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1548">**Description**</span></span>

<span data-ttu-id="65356-1549">이 이벤트는 USBX 호스트 클래스 Cdc Acm 수신 시작 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1549">This event represents a USBX Host Class Cdc Acm Reception Start Event.</span></span>

<span data-ttu-id="65356-1550">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1550">**Information Fields**</span></span>

- <span data-ttu-id="65356-1551">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1551">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1552">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1552">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1553">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1553">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1554">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1554">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-stop"></a><span data-ttu-id="65356-1555">호스트 클래스 Cdc Acm 수신 중지</span><span class="sxs-lookup"><span data-stu-id="65356-1555">Host Class Cdc Acm Reception Stop</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="65356-1556">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="65356-1556">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="65356-1557">**아이콘** ![호스트 클래스 Cdc Acm 수신 중지 아이콘](./media/user-guide/usbx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1557">**Icon** ![Host Class C D C A C M Reception Stop icon](./media/user-guide/usbx-events/image102.png)</span></span>

<span data-ttu-id="65356-1558">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1558">**Description**</span></span>

<span data-ttu-id="65356-1559">이 이벤트는 USBX 호스트 클래스 Cdc Acm 수신 중지 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1559">This event represents a USBX Host Class Cdc Acm Reception Stop Event.</span></span>

<span data-ttu-id="65356-1560">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1560">**Information Fields**</span></span>

- <span data-ttu-id="65356-1561">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1561">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1562">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1562">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1563">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1563">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-write"></a><span data-ttu-id="65356-1564">호스트 클래스 Cdc Acm 쓰기</span><span class="sxs-lookup"><span data-stu-id="65356-1564">Host Class Cdc Acm Write</span></span> 

#### <a name="ux_host_class_acm_write"></a><span data-ttu-id="65356-1565">ux_host_class_acm_write</span><span class="sxs-lookup"><span data-stu-id="65356-1565">ux_host_class_acm_write</span></span>

<span data-ttu-id="65356-1566">**아이콘** ![호스트 클래스 Cdc Acm 쓰기 아이콘](./media/user-guide/usbx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1566">**Icon** ![Host Class C D C A C M Write icon](./media/user-guide/usbx-events/image103.png)</span></span>

<span data-ttu-id="65356-1567">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1567">**Description**</span></span>

<span data-ttu-id="65356-1568">이 이벤트는 USBX 호스트 클래스 Cdc Acm 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1568">This event represents a USBX Host Class Cdc Acm Write Event.</span></span>

<span data-ttu-id="65356-1569">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1569">**Information Fields**</span></span>

- <span data-ttu-id="65356-1570">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1570">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1571">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-1571">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-1572">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-1572">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="65356-1573">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1573">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-activate"></a><span data-ttu-id="65356-1574">호스트 클래스 Dpump 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1574">Host Class Dpump Activate</span></span> 

#### <a name="ux_host_class_dpump_activate"></a><span data-ttu-id="65356-1575">ux_host_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="65356-1575">ux_host_class_dpump_activate</span></span>

<span data-ttu-id="65356-1576">**아이콘** ![호스트 클래스 Dpump 활성화 아이콘](./media/user-guide/usbx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1576">**Icon** ![Host Class Dpump Activate icon](./media/user-guide/usbx-events/image104.png)</span></span>

<span data-ttu-id="65356-1577">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1577">**Description**</span></span>

<span data-ttu-id="65356-1578">이 이벤트는 USBX 호스트 클래스 Dpump 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1578">This event represents a USBX Host Class Dpump Activate Event.</span></span>

<span data-ttu-id="65356-1579">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1579">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1580">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1580">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1581">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1581">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1582">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1582">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1583">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1583">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-deactivate"></a><span data-ttu-id="65356-1584">호스트 클래스 Dpump 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1584">Host Class Dpump Deactivate</span></span> 

#### <a name="ux_host_class_dpump_deactivate"></a><span data-ttu-id="65356-1585">ux_host_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-1585">ux_host_class_dpump_deactivate</span></span>

<span data-ttu-id="65356-1586">**아이콘** ![호스트 클래스 Dpump 비활성화 아이콘](./media/user-guide/usbx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1586">**Icon** ![Host Class Dpump Deactivate icon](./media/user-guide/usbx-events/image105.png)</span></span>

<span data-ttu-id="65356-1587">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1587">**Description**</span></span>

<span data-ttu-id="65356-1588">이 이벤트는 USBX 호스트 클래스 Dpump 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1588">This event represents a USBX Host Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="65356-1589">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1589">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1590">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1590">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1591">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1591">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1592">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1592">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1593">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1593">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-read"></a><span data-ttu-id="65356-1594">호스트 클래스 Dpump 읽기</span><span class="sxs-lookup"><span data-stu-id="65356-1594">Host Class Dpump Read</span></span> 

#### <a name="ux_host_class_dpump_read"></a><span data-ttu-id="65356-1595">ux_host_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="65356-1595">ux_host_class_dpump_read</span></span>

<span data-ttu-id="65356-1596">**아이콘** ![호스트 클래스 Dpump 읽기 아이콘](./media/user-guide/usbx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1596">**Icon** ![Host Class Dpump Read icon](./media/user-guide/usbx-events/image106.png)</span></span>

<span data-ttu-id="65356-1597">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1597">**Description**</span></span>

<span data-ttu-id="65356-1598">이 이벤트는 USBX 호스트 클래스 Dpump 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1598">This event represents a USBX Host Class Dpump Read Event.</span></span>

<span data-ttu-id="65356-1599">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1599">**Information Fields**</span></span>

- <span data-ttu-id="65356-1600">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1600">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1601">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-1601">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-1602">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-1602">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-1603">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1603">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-write"></a><span data-ttu-id="65356-1604">호스트 클래스 Dpump 쓰기</span><span class="sxs-lookup"><span data-stu-id="65356-1604">Host Class Dpump Write</span></span> 

#### <a name="ux_host_class_dpump_write"></a><span data-ttu-id="65356-1605">ux_host_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="65356-1605">ux_host_class_dpump_write</span></span>

<span data-ttu-id="65356-1606">**아이콘** ![호스트 클래스 Dpump 쓰기 아이콘](./media/user-guide/usbx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1606">**Icon** ![Host Class Dpump Write icon](./media/user-guide/usbx-events/image107.png)</span></span>

<span data-ttu-id="65356-1607">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1607">**Description**</span></span>

<span data-ttu-id="65356-1608">이 이벤트는 USBX 호스트 클래스 Dpump 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1608">This event represents a USBX Host Class Dpump Write Event.</span></span>

<span data-ttu-id="65356-1609">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1609">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1610">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1610">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1611">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-1611">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-1612">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-1612">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-1613">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1613">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-activate"></a><span data-ttu-id="65356-1614">호스트 클래스 Hid 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1614">Host Class Hid Activate</span></span> 

#### <a name="ux_host_class_hid_activate"></a><span data-ttu-id="65356-1615">ux_host_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="65356-1615">ux_host_class_hid_activate</span></span>

<span data-ttu-id="65356-1616">**아이콘** ![호스트 클래스 Hid 활성화 아이콘](./media/user-guide/usbx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1616">**Icon** ![Host Class Hid Activate icon](./media/user-guide/usbx-events/image108.png)</span></span>

<span data-ttu-id="65356-1617">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1617">**Description**</span></span>

<span data-ttu-id="65356-1618">이 이벤트는 USBX 호스트 클래스 Hid 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1618">This event represents a USBX Host Class Hid Activate Event.</span></span>

<span data-ttu-id="65356-1619">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1619">**Information Fields**</span></span>

- <span data-ttu-id="65356-1620">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1620">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1621">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1621">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1622">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1622">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1623">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1623">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-client-register"></a><span data-ttu-id="65356-1624">호스트 클래스 Hid 클라이언트 등록</span><span class="sxs-lookup"><span data-stu-id="65356-1624">Host Class Hid Client Register</span></span> 

#### <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="65356-1625">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="65356-1625">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="65356-1626">**아이콘** ![호스트 클래스 Hid 클라이언트 등록 아이콘](./media/user-guide/usbx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1626">**Icon** ![Host Class Hid Client Register icon](./media/user-guide/usbx-events/image109.png)</span></span>

<span data-ttu-id="65356-1627">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1627">**Description**</span></span>

<span data-ttu-id="65356-1628">이 이벤트는 USBX 호스트 클래스 Hid 클라이언트 등록 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1628">This event represents a USBX Host Class Hid Client Register Event.</span></span>

<span data-ttu-id="65356-1629">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1629">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1630">정보 필드 1: Hid 클라이언트 이름</span><span class="sxs-lookup"><span data-stu-id="65356-1630">Info Field 1: Hid client name.</span></span>
- <span data-ttu-id="65356-1631">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1631">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1632">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1632">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1633">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1633">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-deactivate"></a><span data-ttu-id="65356-1634">호스트 클래스 Hid 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1634">Host Class Hid Deactivate</span></span> 

#### <a name="ux_host_class_hid_deactivate"></a><span data-ttu-id="65356-1635">ux_host_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-1635">ux_host_class_hid_deactivate</span></span>

<span data-ttu-id="65356-1636">**아이콘** ![호스트 클래스 Hid 비활성화 아이콘](./media/user-guide/usbx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1636">**Icon** ![Host Class Hid Deactivate icon](./media/user-guide/usbx-events/image110.png)</span></span>

<span data-ttu-id="65356-1637">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1637">**Description**</span></span>

<span data-ttu-id="65356-1638">이 이벤트는 USBX 호스트 클래스 Hid 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1638">This event represents a USBX Host Class Hid Deactivate Event.</span></span>

<span data-ttu-id="65356-1639">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1639">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1640">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1640">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1641">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1641">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1642">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1642">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1643">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1643">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-get"></a><span data-ttu-id="65356-1644">호스트 클래스 Hid 유휴 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1644">Host Class Hid Idle Get</span></span> 

#### <a name="ux_host_class_hid_idle_get"></a><span data-ttu-id="65356-1645">ux_host_class_hid_idle_get</span><span class="sxs-lookup"><span data-stu-id="65356-1645">ux_host_class_hid_idle_get</span></span>

<span data-ttu-id="65356-1646">**아이콘** ![호스트 클래스 Hid 유휴 가져오기 아이콘](./media/user-guide/usbx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1646">**Icon** ![Host Class Hid Idle Get icon](./media/user-guide/usbx-events/image111.png)</span></span>

<span data-ttu-id="65356-1647">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1647">**Description**</span></span>

<span data-ttu-id="65356-1648">이 이벤트는 USBX 호스트 클래스 Hid 유휴 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1648">This event represents a USBX Host Class Hid Idle Get Event.</span></span>

<span data-ttu-id="65356-1649">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1649">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1650">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1650">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1651">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1651">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1652">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1652">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1653">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1653">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-set"></a><span data-ttu-id="65356-1654">호스트 클래스 Hid 유휴 설정</span><span class="sxs-lookup"><span data-stu-id="65356-1654">Host Class Hid Idle Set</span></span> 

#### <a name="ux_host_class_hid_idle_set"></a><span data-ttu-id="65356-1655">ux_host_class_hid_idle_set</span><span class="sxs-lookup"><span data-stu-id="65356-1655">ux_host_class_hid_idle_set</span></span>

<span data-ttu-id="65356-1656">**아이콘** ![호스트 클래스 Hid 유휴 설정 아이콘](./media/user-guide/usbx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1656">**Icon** ![Host Class Hid Idle Set icon](./media/user-guide/usbx-events/image112.png)</span></span>

<span data-ttu-id="65356-1657">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1657">**Description**</span></span>

<span data-ttu-id="65356-1658">이 이벤트는 USBX 호스트 클래스 Hid 유휴 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1658">This event represents a USBX Host Class Hid Idle Set Event.</span></span>

<span data-ttu-id="65356-1659">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1659">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1660">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1660">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1661">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1661">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1662">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1662">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1663">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1663">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-activate"></a><span data-ttu-id="65356-1664">호스트 클래스 Hid 키보드 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1664">Host Class Hid Keyboard Activate</span></span> 

#### <a name="ux_host_class_hid_keyboard_activate"></a><span data-ttu-id="65356-1665">ux_host_class_hid_keyboard_activate</span><span class="sxs-lookup"><span data-stu-id="65356-1665">ux_host_class_hid_keyboard_activate</span></span>

<span data-ttu-id="65356-1666">**아이콘** ![호스트 클래스 Hid 키보드 활성화 아이콘](./media/user-guide/usbx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1666">**Icon** ![Host Class Hid Keyboard Activate icon](./media/user-guide/usbx-events/image113.png)</span></span>

<span data-ttu-id="65356-1667">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1667">**Description**</span></span>

<span data-ttu-id="65356-1668">이 이벤트는 USBX 호스트 클래스 Hid 키보드 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1668">This event represents a USBX Host Class Hid Keyboard Activate Event.</span></span>

<span data-ttu-id="65356-1669">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1669">**Information Fields**</span></span>
<p><span data-ttu-id="65356-1670">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1670">Info Field 1: Class instance.</span></span>
<p><span data-ttu-id="65356-1671">정보 필드 2: Hid 클라이언트 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1671">Info Field 2: Hid client instance.</span></span>
<p><span data-ttu-id="65356-1672">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1672">Info Field 3: Not used.</span></span>
<p><span data-ttu-id="65356-1673">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1673">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-deactivate"></a><span data-ttu-id="65356-1674">호스트 클래스 Hid 키보드 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1674">Host Class Hid Keyboard Deactivate</span></span> 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a><span data-ttu-id="65356-1675">ux_host_class_hid_keyboard_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-1675">ux_host_class_hid_keyboard_deactivate</span></span>

<span data-ttu-id="65356-1676">**아이콘** ![호스트 클래스 Hid 키보드 비활성화 아이콘](./media/user-guide/usbx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1676">**Icon** ![Host Class Hid Keyboard Deactivate icon](./media/user-guide/usbx-events/image114.png)</span></span>

<span data-ttu-id="65356-1677">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1677">**Description**</span></span>

<span data-ttu-id="65356-1678">이 이벤트는 USBX 호스트 클래스 Hid 키보드 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1678">This event represents a USBX Host Class Hid Keyboard Deactivate Event.</span></span>

<span data-ttu-id="65356-1679">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1679">**Information Fields**</span></span>

- <span data-ttu-id="65356-1680">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1680">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1681">정보 필드 2: Hid 클라이언트 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1681">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="65356-1682">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1682">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1683">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1683">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-activate"></a><span data-ttu-id="65356-1684">호스트 클래스 Hid 마우스 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1684">Host Class Hid Mouse Activate</span></span> 

#### <a name="ux_host_class_hid_mouse_activate"></a><span data-ttu-id="65356-1685">ux_host_class_hid_mouse_activate</span><span class="sxs-lookup"><span data-stu-id="65356-1685">ux_host_class_hid_mouse_activate</span></span>

<span data-ttu-id="65356-1686">**아이콘** ![호스트 클래스 Hid 마우스 활성화 아이콘](./media/user-guide/usbx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1686">**Icon** ![Host Class Hid Mouse Activate icon](./media/user-guide/usbx-events/image115.png)</span></span>

<span data-ttu-id="65356-1687">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1687">**Description**</span></span>

<span data-ttu-id="65356-1688">이 이벤트는 USBX 호스트 클래스 Hid 마우스 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1688">This event represents a USBX Host Class Hid Mouse Activate Event.</span></span>

<span data-ttu-id="65356-1689">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1689">**Information Fields**</span></span>

- <span data-ttu-id="65356-1690">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1690">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1691">정보 필드 2: Hid 클라이언트 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1691">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="65356-1692">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1692">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1693">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1693">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-deactivate"></a><span data-ttu-id="65356-1694">호스트 클래스 Hid 마우스 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1694">Host Class Hid Mouse Deactivate</span></span> 

#### <a name="ux_host_class_hid_mouse_deactivate"></a><span data-ttu-id="65356-1695">ux_host_class_hid_mouse_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-1695">ux_host_class_hid_mouse_deactivate</span></span>

<span data-ttu-id="65356-1696">**아이콘** ![호스트 클래스 Hid 마우스 비활성화 아이콘](./media/user-guide/usbx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1696">**Icon** ![Host Class Hid Mouse Deactivate icon](./media/user-guide/usbx-events/image116.png)</span></span>

<span data-ttu-id="65356-1697">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1697">**Description**</span></span>

- <span data-ttu-id="65356-1698">이 이벤트는 USBX 호스트 클래스 Hid 마우스 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1698">This event represents a USBX Host Class Hid Mouse Deactivate Event.</span></span>

<span data-ttu-id="65356-1699">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1699">**Information Fields**</span></span>

- <span data-ttu-id="65356-1700">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1700">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1701">정보 필드 2: Hid 클라이언트 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1701">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="65356-1702">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1702">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1703">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1703">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-activate"></a><span data-ttu-id="65356-1704">호스트 클래스 Hid 원격 제어 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1704">Host Class Hid Remote Control Activate</span></span> 

#### <a name="ux_host_class_hid_remote_control_activate"></a><span data-ttu-id="65356-1705">ux_host_class_hid_remote_control_activate</span><span class="sxs-lookup"><span data-stu-id="65356-1705">ux_host_class_hid_remote_control_activate</span></span>

<span data-ttu-id="65356-1706">**아이콘** ![호스트 클래스 Hid 원격 제어 활성화 아이콘](./media/user-guide/usbx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1706">**Icon** ![Host Class Hid Remote Control Activate icon](./media/user-guide/usbx-events/image117.png)</span></span>

<span data-ttu-id="65356-1707">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1707">**Description**</span></span>

<span data-ttu-id="65356-1708">이 이벤트는 USBX 호스트 클래스 Hid 원격 제어 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1708">This event represents a USBX Host Class Hid Remote Control Activate Event.</span></span>

<span data-ttu-id="65356-1709">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1709">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1710">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1710">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1711">정보 필드 2: Hid 클라이언트 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1711">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="65356-1712">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1712">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1713">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1713">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-deactivate"></a><span data-ttu-id="65356-1714">호스트 클래스 Hid 원격 제어 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1714">Host Class Hid Remote Control Deactivate</span></span> 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a><span data-ttu-id="65356-1715">ux_host_class_hid_remote_control_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-1715">ux_host_class_hid_remote_control_deactivate</span></span>

<span data-ttu-id="65356-1716">**아이콘** ![호스트 클래스 Hid 원격 제어 비활성화 아이콘](./media/user-guide/usbx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1716">**Icon** ![Host Class Hid Remote Control Deactivate icon](./media/user-guide/usbx-events/image118.png)</span></span>

<span data-ttu-id="65356-1717">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1717">**Description**</span></span>

<span data-ttu-id="65356-1718">이 이벤트는 USBX 호스트 클래스 Hid 원격 제어 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1718">This event represents a USBX Host Class Hid Remote Control Deactivate Event.</span></span>

<span data-ttu-id="65356-1719">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1719">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1720">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1720">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1721">정보 필드 2: Hid 클라이언트 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1721">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="65356-1722">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1722">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1723">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1723">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-get"></a><span data-ttu-id="65356-1724">호스트 클래스 Hid 보고서 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1724">Host Class Hid Report Get</span></span> 

#### <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="65356-1725">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="65356-1725">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="65356-1726">**아이콘** ![호스트 클래스 Hid 보고서 가져오기 아이콘](./media/user-guide/usbx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1726">**Icon** ![Host Class Hid Report Get icon](./media/user-guide/usbx-events/image119.png)</span></span>

<span data-ttu-id="65356-1727">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1727">**Description**</span></span>

<span data-ttu-id="65356-1728">이 이벤트는 USBX 호스트 클래스 Hid 보고서 가져오기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1728">This event represents a USBX Host Class Hid Report Get.</span></span>

<span data-ttu-id="65356-1729">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1729">**Information Fields**</span></span>

- <span data-ttu-id="65356-1730">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1730">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1731">정보 필드 2: 클라이언트 보고서</span><span class="sxs-lookup"><span data-stu-id="65356-1731">Info Field 2: Client report.</span></span>
- <span data-ttu-id="65356-1732">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1732">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1733">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1733">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-set"></a><span data-ttu-id="65356-1734">호스트 클래스 Hid 보고서 설정</span><span class="sxs-lookup"><span data-stu-id="65356-1734">Host Class Hid Report Set</span></span> 

#### <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="65356-1735">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="65356-1735">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="65356-1736">**아이콘** ![호스트 클래스 Hid 보고서 설정 아이콘](./media/user-guide/usbx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1736">**Icon** ![Host Class Hid Report Set icon](./media/user-guide/usbx-events/image120.png)</span></span>

<span data-ttu-id="65356-1737">**설명** 이 이벤트는 USBX 호스트 클래스 Hid 보고서 설정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1737">**Description** This event represents a USBX Host Class Hid Report Set.</span></span>

<span data-ttu-id="65356-1738">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1738">**Information Fields**</span></span>

- <span data-ttu-id="65356-1739">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1739">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1740">정보 필드 2: 클라이언트 보고서</span><span class="sxs-lookup"><span data-stu-id="65356-1740">Info Field 2: Client report.</span></span>
- <span data-ttu-id="65356-1741">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1741">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1742">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1742">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-activate"></a><span data-ttu-id="65356-1743">호스트 클래스 허브 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1743">Host Class Hub Activate</span></span> 

#### <a name="ux_host_class_hub_activate"></a><span data-ttu-id="65356-1744">ux_host_class_hub_activate</span><span class="sxs-lookup"><span data-stu-id="65356-1744">ux_host_class_hub_activate</span></span>

<span data-ttu-id="65356-1745">**아이콘** ![호스트 클래스 Hub 활성화 아이콘](./media/user-guide/usbx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1745">**Icon** ![Host Class Hub Activate icon](./media/user-guide/usbx-events/image121.png)</span></span>

<span data-ttu-id="65356-1746">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1746">**Description**</span></span>

<span data-ttu-id="65356-1747">이 이벤트는 USBX 호스트 클래스 허브 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1747">This event represents a USBX Host Class Hub Activate Event.</span></span>

<span data-ttu-id="65356-1748">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1748">**Information Fields**</span></span> 

- <span data-ttu-id="65356-1749">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1749">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1750">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1750">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1751">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1751">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1752">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1752">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-change-detect"></a><span data-ttu-id="65356-1753">호스트 클래스 허브 변경 검색</span><span class="sxs-lookup"><span data-stu-id="65356-1753">Host Class Hub Change Detect</span></span> 

#### <a name="ux_host_class_hub_change_detect"></a><span data-ttu-id="65356-1754">ux_host_class_hub_change_detect</span><span class="sxs-lookup"><span data-stu-id="65356-1754">ux_host_class_hub_change_detect</span></span>

<span data-ttu-id="65356-1755">**아이콘** ![호스트 클래스 허브 변경 검색 아이콘](./media/user-guide/usbx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1755">**Icon** ![Host Class Hub Change Detect icon](./media/user-guide/usbx-events/image122.png)</span></span>

<span data-ttu-id="65356-1756">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1756">**Description**</span></span>

<span data-ttu-id="65356-1757">이 이벤트는 USBX 호스트 클래스 허브 변경 검색 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1757">This event represents a USBX Host Class Hub Change Detect Event.</span></span>

<span data-ttu-id="65356-1758">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1758">**Information Fields**</span></span>

- <span data-ttu-id="65356-1759">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1759">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1760">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1760">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1761">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1761">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1762">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1762">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-deactivate"></a><span data-ttu-id="65356-1763">호스트 클래스 허브 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1763">Host Class Hub Deactivate</span></span> 

#### <a name="ux_host_class_hub_deactivate"></a><span data-ttu-id="65356-1764">ux_host_class_hub_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-1764">ux_host_class_hub_deactivate</span></span>

<span data-ttu-id="65356-1765">**아이콘** ![호스트 클래스 허브 비활성화 아이콘](./media/user-guide/usbx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1765">**Icon** ![Host Class Hub Deactivate icon](./media/user-guide/usbx-events/image123.png)</span></span>

<span data-ttu-id="65356-1766">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1766">**Description**</span></span>

<span data-ttu-id="65356-1767">이 이벤트는 USBX 호스트 클래스 허브 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1767">This event represents a USBX Host Class Hub Deactivate Event.</span></span>

<span data-ttu-id="65356-1768">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1768">**Information Fields**</span></span>

- <span data-ttu-id="65356-1769">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1769">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1770">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1770">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1771">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1771">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1772">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1772">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-connection-process"></a><span data-ttu-id="65356-1773">호스트 클래스 허브 포트 변경 연결 프로세스</span><span class="sxs-lookup"><span data-stu-id="65356-1773">Host Class Hub Port Change Connection Process</span></span> 

#### <a name="ux_host_class_hub_change_connection_process"></a><span data-ttu-id="65356-1774">ux_host_class_hub_change_connection_process</span><span class="sxs-lookup"><span data-stu-id="65356-1774">ux_host_class_hub_change_connection_process</span></span>

<span data-ttu-id="65356-1775">**아이콘** ![호스트 클래스 허브 포트 변경 연결 프로세스 아이콘](./media/user-guide/usbx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1775">**Icon** ![Host Class Hub Port Change Connection Process icon](./media/user-guide/usbx-events/image124.png)</span></span>

<span data-ttu-id="65356-1776">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1776">**Description**</span></span>

<span data-ttu-id="65356-1777">이 이벤트는 USBX 호스트 클래스 허브 포트 변경 연결 프로세스 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1777">This event represents a USBX Host Class Hub Port Change Connection Process Event.</span></span>

<span data-ttu-id="65356-1778">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1778">**Information Fields**</span></span>

- <span data-ttu-id="65356-1779">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1779">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1780">정보 필드 2: 포트</span><span class="sxs-lookup"><span data-stu-id="65356-1780">Info Field 2: Port.</span></span>
- <span data-ttu-id="65356-1781">정보 필드 3: 포트 상태</span><span class="sxs-lookup"><span data-stu-id="65356-1781">Info Field 3: Port status.</span></span>
- <span data-ttu-id="65356-1782">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1782">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-enable-process"></a><span data-ttu-id="65356-1783">호스트 클래스 허브 포트 변경 사용 프로세스</span><span class="sxs-lookup"><span data-stu-id="65356-1783">Host Class Hub Port Change Enable Process</span></span> 

#### <a name="ux_host_class_hub_port_change_enable_process"></a><span data-ttu-id="65356-1784">ux_host_class_hub_port_change_enable_process</span><span class="sxs-lookup"><span data-stu-id="65356-1784">ux_host_class_hub_port_change_enable_process</span></span>

<span data-ttu-id="65356-1785">**아이콘** ![호스트 클래스 허브 포트 변경 사용 프로세스 아이콘](./media/user-guide/usbx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1785">**Icon** ![Host Class Hub Port Change Enable Process icon](./media/user-guide/usbx-events/image125.png)</span></span>

<span data-ttu-id="65356-1786">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1786">**Description**</span></span>

<span data-ttu-id="65356-1787">이 이벤트는 USBX 호스트 클래스 허브 포트 변경 사용 프로세스 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1787">This event represents a USBX Host Class Hub Port Change Enable Process Event.</span></span>

<span data-ttu-id="65356-1788">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1788">**Information Fields**</span></span>

- <span data-ttu-id="65356-1789">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1789">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1790">정보 필드 2: 포트</span><span class="sxs-lookup"><span data-stu-id="65356-1790">Info Field 2: Port.</span></span>
- <span data-ttu-id="65356-1791">정보 필드 3: 포트 상태</span><span class="sxs-lookup"><span data-stu-id="65356-1791">Info Field 3: Port status.</span></span>
- <span data-ttu-id="65356-1792">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1792">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-over-current-process"></a><span data-ttu-id="65356-1793">호스트 클래스 허브 포트 전환 현재 프로세스</span><span class="sxs-lookup"><span data-stu-id="65356-1793">Host Class Hub Port Change Over Current Process</span></span> 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a><span data-ttu-id="65356-1794">ux_host_class_hub_port_change_over_current_process</span><span class="sxs-lookup"><span data-stu-id="65356-1794">ux_host_class_hub_port_change_over_current_process</span></span>

<span data-ttu-id="65356-1795">**아이콘** ![호스트 클래스 허브 포트 전환 현재 프로세스 아이콘](./media/user-guide/usbx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1795">**Icon** ![Host Class Hub Port Change Over Current Process icon](./media/user-guide/usbx-events/image126.png)</span></span>

<span data-ttu-id="65356-1796">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1796">**Description**</span></span>

<span data-ttu-id="65356-1797">이 이벤트는 nx_packet_allocate를 통한 패킷 할당을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1797">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="65356-1798">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1798">**Information Fields**</span></span>

- <span data-ttu-id="65356-1799">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1799">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1800">정보 필드 2: 포트</span><span class="sxs-lookup"><span data-stu-id="65356-1800">Info Field 2: Port.</span></span>
- <span data-ttu-id="65356-1801">정보 필드 3: 포트 상태</span><span class="sxs-lookup"><span data-stu-id="65356-1801">Info Field 3: Port status.</span></span>
- <span data-ttu-id="65356-1802">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1802">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-reset-process"></a><span data-ttu-id="65356-1803">호스트 클래스 허브 포트 변경 재설정 프로세스</span><span class="sxs-lookup"><span data-stu-id="65356-1803">Host Class Hub Port Change Reset Process</span></span> 

#### <a name="ux_host_class_hub_port_change_reset_process"></a><span data-ttu-id="65356-1804">ux_host_class_hub_port_change_reset_process</span><span class="sxs-lookup"><span data-stu-id="65356-1804">ux_host_class_hub_port_change_reset_process</span></span>

<span data-ttu-id="65356-1805">**아이콘** ![호스트 클래스 허브 포트 변경 재설정 프로세스 아이콘](./media/user-guide/usbx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1805">**Icon** ![Host Class Hub Port Change Reset Process icon](./media/user-guide/usbx-events/image127.png)</span></span>

<span data-ttu-id="65356-1806">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1806">**Description**</span></span>

<span data-ttu-id="65356-1807">이 이벤트는 USBX 호스트 클래스 허브 포트 변경 재설정 프로세스 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1807">This event represents a USBX Host Class Hub Port Change Reset Process Event.</span></span>

<span data-ttu-id="65356-1808">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1808">**Information Fields**</span></span>

- <span data-ttu-id="65356-1809">정보 필드 1: 허브</span><span class="sxs-lookup"><span data-stu-id="65356-1809">Info Field 1: Hub.</span></span> <span data-ttu-id="65356-1810">정보 필드 2: 포트</span><span class="sxs-lookup"><span data-stu-id="65356-1810">Info Field 2: Port.</span></span>
- <span data-ttu-id="65356-1811">정보 필드 3: 포트 상태</span><span class="sxs-lookup"><span data-stu-id="65356-1811">Info Field 3: Port status.</span></span>
- <span data-ttu-id="65356-1812">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1812">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-suspend-process"></a><span data-ttu-id="65356-1813">호스트 클래스 허브 포트 변경 일시 중단 프로세스</span><span class="sxs-lookup"><span data-stu-id="65356-1813">Host Class Hub Port Change Suspend Process</span></span> 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a><span data-ttu-id="65356-1814">ux_host_class_hub_port_change_suspend_process</span><span class="sxs-lookup"><span data-stu-id="65356-1814">ux_host_class_hub_port_change_suspend_process</span></span>

<span data-ttu-id="65356-1815">**아이콘** ![호스트 클래스 허브 포트 변경 일시 중단 프로세스 아이콘](./media/user-guide/usbx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1815">**Icon** ![Host Class Hub Port Change Suspend Process icon](./media/user-guide/usbx-events/image128.png)</span></span>

<span data-ttu-id="65356-1816">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1816">**Description**</span></span>

<span data-ttu-id="65356-1817">이 이벤트는 USBX 호스트 클래스 허브 포트 변경 일시 중단 프로세스 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1817">This event represents a USBX Host Class Hub Port Change Suspend Process Event.</span></span>

<span data-ttu-id="65356-1818">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1818">**Information Fields**</span></span>

- <span data-ttu-id="65356-1819">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1819">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1820">정보 필드 2: 포트</span><span class="sxs-lookup"><span data-stu-id="65356-1820">Info Field 2: Port.</span></span>
- <span data-ttu-id="65356-1821">정보 필드 3: 포트 상태</span><span class="sxs-lookup"><span data-stu-id="65356-1821">Info Field 3: Port status.</span></span>
- <span data-ttu-id="65356-1822">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1822">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-activate"></a><span data-ttu-id="65356-1823">호스트 클래스 Pima 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1823">Host Class Pima Activate</span></span> 

#### <a name="ux_host_class_pima_activate"></a><span data-ttu-id="65356-1824">ux_host_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="65356-1824">ux_host_class_pima_activate</span></span>

<span data-ttu-id="65356-1825">**아이콘** ![호스트 클래스 Pima 활성화 아이콘](./media/user-guide/usbx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1825">**Icon** ![Host Class Pima Activate icon](./media/user-guide/usbx-events/image129.png)</span></span>

<span data-ttu-id="65356-1826">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1826">**Description**</span></span>

<span data-ttu-id="65356-1827">이 이벤트는 USBX 호스트 클래스 Pima 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1827">This event represents a USBX Host Class Pima Activate Event.</span></span>

<span data-ttu-id="65356-1828">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1828">**Information Fields**</span></span>

- <span data-ttu-id="65356-1829">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1829">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1830">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1830">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1831">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1831">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1832">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1832">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-deactivate"></a><span data-ttu-id="65356-1833">호스트 클래스 Pima 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-1833">Host Class Pima Deactivate</span></span> 

#### <a name="ux_host_class_pima_deactivate"></a><span data-ttu-id="65356-1834">ux_host_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-1834">ux_host_class_pima_deactivate</span></span>

<span data-ttu-id="65356-1835">**아이콘** ![호스트 클래스 Pima 비활성화 아이콘](./media/user-guide/usbx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1835">**Icon** ![Host Class Pima Deactivate icon](./media/user-guide/usbx-events/image130.png)</span></span>

<span data-ttu-id="65356-1836">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1836">**Description**</span></span>

<span data-ttu-id="65356-1837">이 이벤트는 USBX 호스트 클래스 Pima 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1837">This event represents a USBX Host Class Pima Deactivate Event.</span></span>

<span data-ttu-id="65356-1838">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1838">**Information Fields**</span></span>

- <span data-ttu-id="65356-1839">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1839">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1840">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1840">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1841">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1841">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1842">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1842">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-info-get"></a><span data-ttu-id="65356-1843">호스트 클래스 Pima 디바이스 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1843">Host Class Pima Device Info Get</span></span> 

#### <a name="ux_host_class_pima_device_info_get"></a><span data-ttu-id="65356-1844">ux_host_class_pima_device_info_get</span><span class="sxs-lookup"><span data-stu-id="65356-1844">ux_host_class_pima_device_info_get</span></span>

<span data-ttu-id="65356-1845">**아이콘** ![호스트 클래스 Pima 디바이스 정보 가져오기 아이콘](./media/user-guide/usbx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1845">**Icon** ![Host Class Pima Device Info Get icon](./media/user-guide/usbx-events/image131.png)</span></span>

<span data-ttu-id="65356-1846">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1846">**Description**</span></span>

<span data-ttu-id="65356-1847">이 이벤트는 USBX 호스트 클래스 Pima 디바이스 정보 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1847">This event represents a USBX Host Class Pima Device Info Get Event.</span></span>

<span data-ttu-id="65356-1848">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1848">**Information Fields**</span></span>

- <span data-ttu-id="65356-1849">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1849">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1850">정보 필드 2: Pima 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-1850">Info Field 2: Pima device.</span></span>
- <span data-ttu-id="65356-1851">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1851">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1852">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1852">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-reset"></a><span data-ttu-id="65356-1853">호스트 클래스 Pima 디바이스 재설정</span><span class="sxs-lookup"><span data-stu-id="65356-1853">Host Class Pima Device Reset</span></span> 

#### <a name="ux_host_class_pima_device_reset"></a><span data-ttu-id="65356-1854">ux_host_class_pima_device_reset</span><span class="sxs-lookup"><span data-stu-id="65356-1854">ux_host_class_pima_device_reset</span></span>

<span data-ttu-id="65356-1855">**아이콘** ![호스트 클래스 Pima 디바이스 재설정 아이콘](./media/user-guide/usbx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1855">**Icon** ![Host Class Pima Device Reset icon](./media/user-guide/usbx-events/image132.png)</span></span>

<span data-ttu-id="65356-1856">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1856">**Description**</span></span>

<span data-ttu-id="65356-1857">이 이벤트는 USBX 호스트 클래스 Pima 디바이스 재설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1857">This event represents a USBX Host Class Pima Device Reset Event.</span></span>

<span data-ttu-id="65356-1858">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1858">**Information Fields**</span></span>

- <span data-ttu-id="65356-1859">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1859">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1860">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1860">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1861">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1861">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1862">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1862">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-notification"></a><span data-ttu-id="65356-1863">호스트 클래스 Pima 알림</span><span class="sxs-lookup"><span data-stu-id="65356-1863">Host Class Pima Notification</span></span> 

#### <a name="ux_host_class_pima_notification"></a><span data-ttu-id="65356-1864">ux_host_class_pima_notification</span><span class="sxs-lookup"><span data-stu-id="65356-1864">ux_host_class_pima_notification</span></span>

<span data-ttu-id="65356-1865">**아이콘** ![호스트 클래스 Pima 알림 아이콘](./media/user-guide/usbx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1865">**Icon** ![Host Class Pima Notification icon](./media/user-guide/usbx-events/image133.png)</span></span>

<span data-ttu-id="65356-1866">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1866">**Description**</span></span>

<span data-ttu-id="65356-1867">이 이벤트는 USBX 호스트 클래스 Pima 알림 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1867">This event represents a USBX Host Class Pima Notification Event.</span></span>

<span data-ttu-id="65356-1868">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1868">**Information Fields**</span></span>

- <span data-ttu-id="65356-1869">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1869">Info Field 1: Class instance.</span></span> <span data-ttu-id="65356-1870">정보 필드 2: 이벤트 코드</span><span class="sxs-lookup"><span data-stu-id="65356-1870">Info Field 2: Event code.</span></span>
- <span data-ttu-id="65356-1871">정보 필드 3: 트랜잭션 ID</span><span class="sxs-lookup"><span data-stu-id="65356-1871">Info Field 3: Transaction ID.</span></span>
- <span data-ttu-id="65356-1872">정보 필드 4: 매개 변수 1</span><span class="sxs-lookup"><span data-stu-id="65356-1872">Info Field 4: Parameter1.</span></span>

### <a name="host-class-pima-number-objects-get"></a><span data-ttu-id="65356-1873">호스트 클래스 Pima 숫자 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1873">Host Class Pima Number Objects Get</span></span> 

#### <a name="ux_host_class_pima_number_objects_get"></a><span data-ttu-id="65356-1874">ux_host_class_pima_number_objects_get</span><span class="sxs-lookup"><span data-stu-id="65356-1874">ux_host_class_pima_number_objects_get</span></span>

<span data-ttu-id="65356-1875">**아이콘** ![호스트 클래스 Pima 숫자 개체 가져오기 아이콘](./media/user-guide/usbx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1875">**Icon** ![Host Class Pima Number Objects Get icon](./media/user-guide/usbx-events/image134.png)</span></span>

<span data-ttu-id="65356-1876">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1876">**Description**</span></span>

<span data-ttu-id="65356-1877">이 이벤트는 USBX 호스트 클래스 Pima 숫자 개체 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1877">This event represents a USBX Host Class Pima Number Objects Get Event.</span></span>

<span data-ttu-id="65356-1878">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1878">**Information Fields**</span></span>

- <span data-ttu-id="65356-1879">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1879">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1880">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1880">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1881">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1881">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1882">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1882">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-close"></a><span data-ttu-id="65356-1883">호스트 클래스 Pima 개체 닫기</span><span class="sxs-lookup"><span data-stu-id="65356-1883">Host Class Pima Object Close</span></span> 

#### <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="65356-1884">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="65356-1884">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="65356-1885">**아이콘** ![호스트 클래스 Pima 개체 닫기 아이콘](./media/user-guide/usbx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1885">**Icon** ![Host Class Pima Object Close icon](./media/user-guide/usbx-events/image135.png)</span></span>

<span data-ttu-id="65356-1886">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1886">**Description**</span></span>

<span data-ttu-id="65356-1887">이 이벤트는 USBX 호스트 클래스 Pima 개체 닫기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1887">This event represents a USBX Host Class Pima Object Close Event.</span></span>

<span data-ttu-id="65356-1888">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1888">**Information Fields**</span></span>

- <span data-ttu-id="65356-1889">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1889">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1890">정보 필드 2: 개체</span><span class="sxs-lookup"><span data-stu-id="65356-1890">Info Field 2: Object.</span></span>
- <span data-ttu-id="65356-1891">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1891">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1892">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1892">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-copy"></a><span data-ttu-id="65356-1893">호스트 클래스 Pima 개체 복사</span><span class="sxs-lookup"><span data-stu-id="65356-1893">Host Class Pima Object Copy</span></span> 

#### <a name="ux_host_class_pima_object_copy"></a><span data-ttu-id="65356-1894">ux_host_class_pima_object_copy</span><span class="sxs-lookup"><span data-stu-id="65356-1894">ux_host_class_pima_object_copy</span></span>

<span data-ttu-id="65356-1895">**아이콘** ![호스트 클래스 Pima 개체 복사 아이콘](./media/user-guide/usbx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1895">**Icon** ![Host Class Pima Object Copy icon](./media/user-guide/usbx-events/image136.png)</span></span>

<span data-ttu-id="65356-1896">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1896">**Description**</span></span>

<span data-ttu-id="65356-1897">이 이벤트는 USBX 호스트 클래스 Pima 개체 복사 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1897">This event represents a USBX Host Class Pima Object Copy Event.</span></span>

<span data-ttu-id="65356-1898">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1898">**Information Fields**</span></span>

- <span data-ttu-id="65356-1899">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1899">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1900">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-1900">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-1901">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1901">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1902">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1902">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-delete"></a><span data-ttu-id="65356-1903">호스트 클래스 Pima 개체 삭제</span><span class="sxs-lookup"><span data-stu-id="65356-1903">Host Class Pima Object Delete</span></span> 

#### <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="65356-1904">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="65356-1904">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="65356-1905">**아이콘** ![호스트 클래스 Pima 개체 삭제 아이콘](./media/user-guide/usbx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1905">**Icon** ![Host Class Pima Object Delete icon](./media/user-guide/usbx-events/image137.png)</span></span>

<span data-ttu-id="65356-1906">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1906">**Description**</span></span>

<span data-ttu-id="65356-1907">이 이벤트는 USBX 호스트 클래스 Pima 개체 삭제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1907">This event represents a USBX Host Class Pima Object Delete Event.</span></span>

<span data-ttu-id="65356-1908">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1908">**Information Fields**</span></span>

- <span data-ttu-id="65356-1909">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1909">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1910">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-1910">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-1911">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1911">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1912">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1912">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-get"></a><span data-ttu-id="65356-1913">호스트 클래스 Pima 개체 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1913">Host Class Pima Object Get</span></span> 

#### <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="65356-1914">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="65356-1914">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="65356-1915">**아이콘** ![호스트 클래스 Pima 개체 가져오기 아이콘](./media/user-guide/usbx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1915">**Icon** ![Host Class Pima Object Get icon](./media/user-guide/usbx-events/image138.png)</span></span>

<span data-ttu-id="65356-1916">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1916">**Description**</span></span>

<span data-ttu-id="65356-1917">이 이벤트는 nx_rarp_info_get을 통한 RARP 정보 가져오기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1917">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="65356-1918">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1918">**Information Fields**</span></span>

- <span data-ttu-id="65356-1919">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1919">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1920">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-1920">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-1921">정보 필드 3: 개체</span><span class="sxs-lookup"><span data-stu-id="65356-1921">Info Field 3: Object.</span></span>
- <span data-ttu-id="65356-1922">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1922">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-get"></a><span data-ttu-id="65356-1923">호스트 클래스 Pima 개체 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-1923">Host Class Pima Object Info Get</span></span> 

#### <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="65356-1924">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="65356-1924">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="65356-1925">**아이콘** ![호스트 클래스 Pima 개체 정보 가져오기 아이콘](./media/user-guide/usbx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1925">**Icon** ![Host Class Pima Object Info Get icon](./media/user-guide/usbx-events/image139.png)</span></span>

<span data-ttu-id="65356-1926">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1926">**Description**</span></span>

<span data-ttu-id="65356-1927">이 이벤트는 USBX 호스트 클래스 Pima 개체 정보 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1927">This event represents a USBX Host Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="65356-1928">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1928">**Information Fields**</span></span>

- <span data-ttu-id="65356-1929">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1929">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1930">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-1930">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-1931">정보 필드 3: 개체</span><span class="sxs-lookup"><span data-stu-id="65356-1931">Info Field 3: Object.</span></span>
- <span data-ttu-id="65356-1932">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1932">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-send"></a><span data-ttu-id="65356-1933">호스트 클래스 Pima 개체 정보 보내기</span><span class="sxs-lookup"><span data-stu-id="65356-1933">Host Class Pima Object Info Send</span></span> 

#### <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="65356-1934">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="65356-1934">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="65356-1935">**아이콘** ![호스트 클래스 Pima 개체 정보 보내기 아이콘](./media/user-guide/usbx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1935">**Icon** ![Host Class Pima Object Info Send icon](./media/user-guide/usbx-events/image140.png)</span></span>

<span data-ttu-id="65356-1936">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1936">**Description**</span></span>

<span data-ttu-id="65356-1937">이 이벤트는 USBX 호스트 클래스 Pima 개체 정보 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1937">This event represents a USBX Host Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="65356-1938">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1938">**Information Fields**</span></span>

- <span data-ttu-id="65356-1939">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1939">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1940">정보 필드 2: 개체</span><span class="sxs-lookup"><span data-stu-id="65356-1940">Info Field 2: Object.</span></span>
- <span data-ttu-id="65356-1941">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1941">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1942">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1942">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-move"></a><span data-ttu-id="65356-1943">호스트 클래스 Pima 개체 이동</span><span class="sxs-lookup"><span data-stu-id="65356-1943">Host Class Pima Object Move</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="65356-1944">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="65356-1944">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="65356-1945">**아이콘** ![호스트 클래스 Pima 개체 이동 아이콘](./media/user-guide/usbx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1945">**Icon** ![Host Class Pima Object Move icon](./media/user-guide/usbx-events/image141.png)</span></span>

<span data-ttu-id="65356-1946">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1946">**Description**</span></span>

<span data-ttu-id="65356-1947">이 이벤트는 USBX 호스트 클래스 Pima 개체 이동 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1947">This event reprThis event represents a USBX Host Class Pima Object Move Event.</span></span>

<span data-ttu-id="65356-1948">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1948">**Information Fields**</span></span>

- <span data-ttu-id="65356-1949">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1949">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1950">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-1950">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-1951">정보 필드 3: 개체</span><span class="sxs-lookup"><span data-stu-id="65356-1951">Info Field 3: Object.</span></span>
- <span data-ttu-id="65356-1952">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1952">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-send"></a><span data-ttu-id="65356-1953">호스트 클래스 Pima 개체 보내기</span><span class="sxs-lookup"><span data-stu-id="65356-1953">Host Class Pima Object Send</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="65356-1954">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="65356-1954">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="65356-1955">**아이콘** ![호스트 클래스 Pima 개체 보내기 아이콘](./media/user-guide/usbx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1955">**Icon** ![Host Class Pima Object Send icon](./media/user-guide/usbx-events/image142.png)</span></span>

<span data-ttu-id="65356-1956">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1956">**Description**</span></span>

<span data-ttu-id="65356-1957">이 이벤트는 USBX 호스트 클래스 Pima 개체 보내기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1957">This event represents a USBX Host Class Pima Object Send Event.</span></span>

<span data-ttu-id="65356-1958">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1958">**Information Fields**</span></span>

- <span data-ttu-id="65356-1959">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1959">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1960">정보 필드 2: 개체</span><span class="sxs-lookup"><span data-stu-id="65356-1960">Info Field 2: Object.</span></span>
- <span data-ttu-id="65356-1961">정보 필드 3: 개체 버퍼</span><span class="sxs-lookup"><span data-stu-id="65356-1961">Info Field 3: Object buffer.</span></span>
- <span data-ttu-id="65356-1962">정보 필드 4: 개체 길이</span><span class="sxs-lookup"><span data-stu-id="65356-1962">Info Field 4: Object length.</span></span>

### <a name="host-class-pima-object-transfer-abort"></a><span data-ttu-id="65356-1963">호스트 클래스 Pima 개체 전송 중단</span><span class="sxs-lookup"><span data-stu-id="65356-1963">Host Class Pima Object Transfer Abort</span></span> 

#### <a name="ux_host_class_pima_object_transfer_abort"></a><span data-ttu-id="65356-1964">ux_host_class_pima_object_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="65356-1964">ux_host_class_pima_object_transfer_abort</span></span>

<span data-ttu-id="65356-1965">**아이콘** ![호스트 클래스 Pima 개체 전송 중단 아이콘](./media/user-guide/usbx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1965">**Icon** ![Host Class Pima Object Transfer Abort icon](./media/user-guide/usbx-events/image143.png)</span></span>

<span data-ttu-id="65356-1966">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1966">**Description**</span></span>

<span data-ttu-id="65356-1967">이 이벤트는 USBX 호스트 클래스 Pima 개체 전송 중단 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1967">This event represents a USBX Host Class Pima Object Transfer Abort Event.</span></span>

<span data-ttu-id="65356-1968">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1968">**Information Fields**</span></span>

- <span data-ttu-id="65356-1969">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1969">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1970">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-1970">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-1971">정보 필드 3: 개체</span><span class="sxs-lookup"><span data-stu-id="65356-1971">Info Field 3: Object.</span></span>
- <span data-ttu-id="65356-1972">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1972">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-read"></a><span data-ttu-id="65356-1973">호스트 클래스 Pima 읽기</span><span class="sxs-lookup"><span data-stu-id="65356-1973">Host Class Pima Read</span></span> 

#### <a name="ux_host_class_pima_read"></a><span data-ttu-id="65356-1974">ux_host_class_pima_read</span><span class="sxs-lookup"><span data-stu-id="65356-1974">ux_host_class_pima_read</span></span>

<span data-ttu-id="65356-1975">**아이콘** ![호스트 클래스 Pima 읽기 아이콘](./media/user-guide/usbx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1975">**Icon** ![Host Class Pima Read icon](./media/user-guide/usbx-events/image144.png)</span></span>

<span data-ttu-id="65356-1976">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1976">**Description**</span></span>

<span data-ttu-id="65356-1977">이 이벤트는 USBX 호스트 클래스 Pima 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1977">This event represents a USBX Host Class Pima Read Event.</span></span>

<span data-ttu-id="65356-1978">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1978">**Information Fields**</span></span>

- <span data-ttu-id="65356-1979">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1979">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1980">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-1980">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-1981">정보 필드 3: 데이터 길이</span><span class="sxs-lookup"><span data-stu-id="65356-1981">Info Field 3: Data length.</span></span>
- <span data-ttu-id="65356-1982">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1982">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-request-cancel"></a><span data-ttu-id="65356-1983">호스트 클래스 Pima 요청 취소</span><span class="sxs-lookup"><span data-stu-id="65356-1983">Host Class Pima Request Cancel</span></span> 

#### <a name="ux_host_class_pima_request_cancel"></a><span data-ttu-id="65356-1984">ux_host_class_pima_request_cancel</span><span class="sxs-lookup"><span data-stu-id="65356-1984">ux_host_class_pima_request_cancel</span></span>

<span data-ttu-id="65356-1985">**아이콘** ![호스트 클래스 Pima 요청 취소 아이콘](./media/user-guide/usbx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1985">**Icon** ![Host Class Pima Request Cancel icon](./media/user-guide/usbx-events/image145.png)</span></span>

<span data-ttu-id="65356-1986">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1986">**Description**</span></span>

<span data-ttu-id="65356-1987">이 이벤트는 USBX 호스트 클래스 Pima 요청 취소 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1987">This event represents a USBX Host Class Pima Request Cancel Event.</span></span>

<span data-ttu-id="65356-1988">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1988">**Information Fields**</span></span>

- <span data-ttu-id="65356-1989">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1989">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-1990">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1990">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-1991">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1991">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-1992">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1992">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-close"></a><span data-ttu-id="65356-1993">호스트 클래스 Pima 세션 닫기</span><span class="sxs-lookup"><span data-stu-id="65356-1993">Host Class Pima Session Close</span></span> 

#### <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="65356-1994">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="65356-1994">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="65356-1995">**아이콘** ![호스트 클래스 Pima 세션 닫기 아이콘](./media/user-guide/usbx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="65356-1995">**Icon** ![Host Class Pima Session Close icon](./media/user-guide/usbx-events/image146.png)</span></span>

<span data-ttu-id="65356-1996">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-1996">**Description**</span></span>

<span data-ttu-id="65356-1997">이 이벤트는 USBX 호스트 클래스 Pima 세션 닫기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-1997">This event represents a USBX Host Class Pima Session Close Event.</span></span>

<span data-ttu-id="65356-1998">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-1998">**Information Fields**</span></span>

- <span data-ttu-id="65356-1999">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-1999">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2000">정보 필드 2: Pima 세션</span><span class="sxs-lookup"><span data-stu-id="65356-2000">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="65356-2001">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2001">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2002">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2002">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-open"></a><span data-ttu-id="65356-2003">호스트 클래스 Pima 세션 열기</span><span class="sxs-lookup"><span data-stu-id="65356-2003">Host Class Pima Session Open</span></span> 

#### <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="65356-2004">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="65356-2004">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="65356-2005">**아이콘** ![호스트 클래스 Pima 세션 열기 아이콘](./media/user-guide/usbx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2005">**Icon** ![Host Class Pima Session Open icon](./media/user-guide/usbx-events/image147.png)</span></span>

<span data-ttu-id="65356-2006">**설명** 이 이벤트는 USBX 호스트 클래스 Pima 세션 열기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2006">**Description** This event represents a USBX Host Class Pima Session Open Event.</span></span>

<span data-ttu-id="65356-2007">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2007">**Information Fields**</span></span>

- <span data-ttu-id="65356-2008">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2008">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2009">정보 필드 2: Pima 세션</span><span class="sxs-lookup"><span data-stu-id="65356-2009">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="65356-2010">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2010">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2011">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2011">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-ids-get"></a><span data-ttu-id="65356-2012">호스트 클래스 Pima 스토리지 ID 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-2012">Host Class Pima Storage Ids Get</span></span> 

#### <a name="ux_host_class_pima_session_ids_get"></a><span data-ttu-id="65356-2013">ux_host_class_pima_session_ids_get</span><span class="sxs-lookup"><span data-stu-id="65356-2013">ux_host_class_pima_session_ids_get</span></span>

<span data-ttu-id="65356-2014">**아이콘** ![호스트 클래스 Pima 스토리지 ID 가져오기 아이콘](./media/user-guide/usbx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2014">**Icon** ![Host Class Pima Storage Ids Get icon](./media/user-guide/usbx-events/image148.png)</span></span>

<span data-ttu-id="65356-2015">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2015">**Description**</span></span>

<span data-ttu-id="65356-2016">이 이벤트는 USBX 호스트 클래스 Pima 스토리지 ID 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2016">This event represents a USBX Host Class Pima Storage Ids Get Event.</span></span>

<span data-ttu-id="65356-2017">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2017">**Information Fields**</span></span>

- <span data-ttu-id="65356-2018">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2018">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2019">정보 필드 2: 스토리지 ID 배열</span><span class="sxs-lookup"><span data-stu-id="65356-2019">nfo Field 2: Storage ID array.</span></span>
- <span data-ttu-id="65356-2020">정보 필드 3: 스토리지 ID 길이</span><span class="sxs-lookup"><span data-stu-id="65356-2020">Info Field 3: Storage ID length.</span></span>
<span data-ttu-id="65356-2021">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2021">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-info-get"></a><span data-ttu-id="65356-2022">호스트 클래스 Pima 스토리지 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-2022">Host Class Pima Storage Info Get</span></span> 

#### <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="65356-2023">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="65356-2023">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="65356-2024">**아이콘** ![호스트 클래스 Pima 스토리지 가져오기 아이콘](./media/user-guide/usbx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2024">**Icon** ![Host Class Pima Storage Info Get icon](./media/user-guide/usbx-events/image149.png)</span></span>

<span data-ttu-id="65356-2025">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2025">**Description**</span></span>

<span data-ttu-id="65356-2026">이 이벤트는 USBX 호스트 클래스 Pima 스토리지 정보 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2026">This event represents a USBX Host Class Pima Storage Info Get Event.</span></span>

<span data-ttu-id="65356-2027">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2027">**Information Fields**</span></span>

- <span data-ttu-id="65356-2028">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2028">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2029">정보 필드 2: 스토리지 ID</span><span class="sxs-lookup"><span data-stu-id="65356-2029">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="65356-2030">정보 필드 3: 스토리지</span><span class="sxs-lookup"><span data-stu-id="65356-2030">Info Field 3: Storage.</span></span>
- <span data-ttu-id="65356-2031">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2031">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-thumb-get"></a><span data-ttu-id="65356-2032">호스트 클래스 Pima Thumb 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-2032">Host Class Pima Thumb Get</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="65356-2033">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="65356-2033">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="65356-2034">**아이콘** ![호스트 클래스 Pima Thumb 가져오기 아이콘](./media/user-guide/usbx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2034">**Icon** ![Host Class Pima Thumb Get icon](./media/user-guide/usbx-events/image150.png)</span></span>

<span data-ttu-id="65356-2035">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2035">**Description**</span></span>

<span data-ttu-id="65356-2036">이 이벤트는 nx_tcp_server_socket_unaccept를 통해 TCP 서버 연결을 허용하지 않는 경우를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2036">This event represents unaccepting a TCP server connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="65356-2037">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2037">**Information Fields**</span></span> 

- <span data-ttu-id="65356-2038">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2038">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2039">정보 필드 2: 개체 핸들</span><span class="sxs-lookup"><span data-stu-id="65356-2039">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="65356-2040">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2040">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2041">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2041">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-write"></a><span data-ttu-id="65356-2042">호스트 클래스 Pima 쓰기</span><span class="sxs-lookup"><span data-stu-id="65356-2042">Host Class Pima Write</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="65356-2043">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="65356-2043">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="65356-2044">**아이콘** ![호스트 클래스 Pima 쓰기 아이콘](./media/user-guide/usbx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2044">**Icon** ![Host Class Pima Write icon](./media/user-guide/usbx-events/image151.png)</span></span>

<span data-ttu-id="65356-2045">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2045">**Description**</span></span>

<span data-ttu-id="65356-2046">이 이벤트는 USBX 호스트 클래스 Pima 쓰기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2046">This event represents a USBX Host Class Pima Write.</span></span>

<span data-ttu-id="65356-2047">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2047">**Information Fields**</span></span>

- <span data-ttu-id="65356-2048">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2048">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="65356-2049">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-2049">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-2050">정보 필드 3: 데이터 길이</span><span class="sxs-lookup"><span data-stu-id="65356-2050">Info Field 3: Data length.</span></span>
- <span data-ttu-id="65356-2051">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2051">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-activate"></a><span data-ttu-id="65356-2052">호스트 클래스 프린터 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-2052">Host Class Printer Activate</span></span> 

#### <a name="ux_host_class_printer_activate"></a><span data-ttu-id="65356-2053">ux_host_class_printer_activate</span><span class="sxs-lookup"><span data-stu-id="65356-2053">ux_host_class_printer_activate</span></span>

<span data-ttu-id="65356-2054">**아이콘** ![호스트 클래스 프린터 활성화 아이콘](./media/user-guide/usbx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2054">**Icon** ![Host Class Printer Activate icon](./media/user-guide/usbx-events/image152.png)</span></span>

<span data-ttu-id="65356-2055">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2055">**Description**</span></span>

<span data-ttu-id="65356-2056">이 이벤트는 USBX 호스트 클래스 프린터 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2056">This event represents a USBX Host Class Printer Activate Event.</span></span>

<span data-ttu-id="65356-2057">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2057">**Information Fields**</span></span>

- <span data-ttu-id="65356-2058">정보 필드 1: IP 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-2058">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="65356-2059">정보 필드 2: 소켓에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-2059">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="65356-2060">정보 필드 3: 서비스 유형</span><span class="sxs-lookup"><span data-stu-id="65356-2060">Info Field 3: Type of service.</span></span>
- <span data-ttu-id="65356-2061">정보 필드 4: 수신 창 크기</span><span class="sxs-lookup"><span data-stu-id="65356-2061">Info Field 4: Receive window size.</span></span>

### <a name="host-class-printer-deactivate"></a><span data-ttu-id="65356-2062">호스트 클래스 프린터 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-2062">Host Class Printer Deactivate</span></span> 

#### <a name="ux_host_class_printer_deactivate"></a><span data-ttu-id="65356-2063">ux_host_class_printer_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-2063">ux_host_class_printer_deactivate</span></span>

<span data-ttu-id="65356-2064">**아이콘** ![호스트 클래스 프린터 비활성화 아이콘](./media/user-guide/usbx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2064">**Icon** ![Host Class Printer Deactivate icon](./media/user-guide/usbx-events/image153.png)</span></span>

<span data-ttu-id="65356-2065">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2065">**Description**</span></span>

<span data-ttu-id="65356-2066">이 이벤트는 USBX 호스트 클래스 프린터 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2066">This event represents a USBX Host Class Printer Deactivate Event.</span></span>

<span data-ttu-id="65356-2067">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2067">**Information Fields**</span></span>

- <span data-ttu-id="65356-2068">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2068">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2069">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2069">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2070">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2070">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2071">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2071">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-name-get"></a><span data-ttu-id="65356-2072">호스트 클래스 프린터 이름 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-2072">Host Class Printer Name Get</span></span> 

#### <a name="ux_host_class_printer_name_get"></a><span data-ttu-id="65356-2073">ux_host_class_printer_name_get</span><span class="sxs-lookup"><span data-stu-id="65356-2073">ux_host_class_printer_name_get</span></span>

<span data-ttu-id="65356-2074">**아이콘** ![호스트 클래스 프린터 이름 가져오기 아이콘](./media/user-guide/usbx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2074">**Icon** ![Host Class Printer Name Get icon](./media/user-guide/usbx-events/image154.png)</span></span>

<span data-ttu-id="65356-2075">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2075">**Description**</span></span>

<span data-ttu-id="65356-2076">이 이벤트는 USBX 호스트 클래스 프린터 이름 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2076">This event represents a USBX Host Class Printer Name Get Event.</span></span>

<span data-ttu-id="65356-2077">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2077">**Information Fields**</span></span> 

- <span data-ttu-id="65356-2078">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2078">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2079">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2079">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2080">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2080">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2081">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2081">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-read"></a><span data-ttu-id="65356-2082">호스트 클래스 프린터 읽기</span><span class="sxs-lookup"><span data-stu-id="65356-2082">Host Class Printer Read</span></span> 

#### <a name="ux_host_class_printer_read"></a><span data-ttu-id="65356-2083">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="65356-2083">ux_host_class_printer_read</span></span>

<span data-ttu-id="65356-2084">**아이콘** ![호스트 클래스 프린터 읽기 아이콘](./media/user-guide/usbx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2084">**Icon** ![Host Class Printer Read icon](./media/user-guide/usbx-events/image155.png)</span></span>

<span data-ttu-id="65356-2085">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2085">**Description**</span></span>

<span data-ttu-id="65356-2086">이 이벤트는 USBX 호스트 클래스 프린터 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2086">This event represents a USBX Host Class Printer Read Event.</span></span>

<span data-ttu-id="65356-2087">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2087">**Information Fields**</span></span>

- <span data-ttu-id="65356-2088">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2088">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2089">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-2089">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-2090">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-2090">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-2091">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2091">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-soft-reset"></a><span data-ttu-id="65356-2092">호스트 클래스 프린터 소프트 리셋</span><span class="sxs-lookup"><span data-stu-id="65356-2092">Host Class Printer Soft Reset</span></span> 

#### <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="65356-2093">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="65356-2093">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="65356-2094">**아이콘** ![호스트 클래스 프린터 소프트 리셋 아이콘](./media/user-guide/usbx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2094">**Icon** ![Host Class Printer Soft Reset icon](./media/user-guide/usbx-events/image156.png)</span></span>

<span data-ttu-id="65356-2095">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2095">**Description**</span></span>

<span data-ttu-id="65356-2096">이 이벤트는 USBX 호스트 클래스 프린터 소프트 리셋 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2096">This event represents a USBX Host Class Printer Soft Reset Event.</span></span>

<span data-ttu-id="65356-2097">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2097">**Information Fields**</span></span>

- <span data-ttu-id="65356-2098">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2098">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2099">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2099">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2100">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2100">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2101">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2101">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-status-get"></a><span data-ttu-id="65356-2102">호스트 클래스 프린터 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-2102">Host Class Printer Status Get</span></span> 

#### <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="65356-2103">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="65356-2103">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="65356-2104">**아이콘** ![호스트 클래스 프린터 상태 가져오기 아이콘](./media/user-guide/usbx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2104">**Icon** ![Host Class Printer Status Get icon](./media/user-guide/usbx-events/image157.png)</span></span>

<span data-ttu-id="65356-2105">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2105">**Description**</span></span>

<span data-ttu-id="65356-2106">이 이벤트는 USBX 호스트 클래스 프린터 상태 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2106">This event represents a USBX Host Class Printer Status Get Event.</span></span>

<span data-ttu-id="65356-2107">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2107">**Information Fields**</span></span>

- <span data-ttu-id="65356-2108">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2108">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2109">정보 필드 2: 프린터 상태</span><span class="sxs-lookup"><span data-stu-id="65356-2109">Info Field 2: Printer status.</span></span>
- <span data-ttu-id="65356-2110">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2110">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2111">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2111">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-write"></a><span data-ttu-id="65356-2112">호스트 클래스 프린터 쓰기</span><span class="sxs-lookup"><span data-stu-id="65356-2112">Host Class Printer Write</span></span> 

#### <a name="ux_host_class_printer_write"></a><span data-ttu-id="65356-2113">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="65356-2113">ux_host_class_printer_write</span></span>

<span data-ttu-id="65356-2114">**아이콘** ![호스트 클래스 프린터 쓰기 아이콘](./media/user-guide/usbx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2114">**Icon** ![Host Class Printer Write icon](./media/user-guide/usbx-events/image158.png)</span></span>

<span data-ttu-id="65356-2115">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2115">**Description**</span></span>

<span data-ttu-id="65356-2116">이 이벤트는 USBX 호스트 클래스 프린터 쓰기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2116">This event represents a USBX Host Class Printer Write.</span></span>

<span data-ttu-id="65356-2117">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2117">**Information Fields**</span></span> 

- <span data-ttu-id="65356-2118">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2118">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2119">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-2119">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-2120">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-2120">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-2121">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2121">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-activate"></a><span data-ttu-id="65356-2122">호스트 클래스 Prolific 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-2122">Host Class Prolific Activate</span></span> 

#### <a name="ux_host_class_prolific_activate"></a><span data-ttu-id="65356-2123">ux_host_class_prolific_activate</span><span class="sxs-lookup"><span data-stu-id="65356-2123">ux_host_class_prolific_activate</span></span> 

<span data-ttu-id="65356-2124">**아이콘** ![호스트 클래스 Prolific 활성화 아이콘](./media/user-guide/usbx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2124">**Icon** ![Host Class Prolific Activate icon](./media/user-guide/usbx-events/image159.png)</span></span>

<span data-ttu-id="65356-2125">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2125">**Description**</span></span>

<span data-ttu-id="65356-2126">이 이벤트는 USBX 호스트 클래스 Prolific 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2126">This event represents a USBX Host Class Prolific Activate Event.</span></span>

<span data-ttu-id="65356-2127">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2127">**Information Fields**</span></span> 

- <span data-ttu-id="65356-2128">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2128">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2129">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2129">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2130">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2130">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2131">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2131">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-deactivate"></a><span data-ttu-id="65356-2132">호스트 클래스 Prolific 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-2132">Host Class Prolific Deactivate</span></span> 

#### <a name="ux_host_class_prolific_deactivate"></a><span data-ttu-id="65356-2133">ux_host_class_prolific_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-2133">ux_host_class_prolific_deactivate</span></span> 

<span data-ttu-id="65356-2134">**아이콘** ![호스트 클래스 Prolific 비활성화 아이콘](./media/user-guide/usbx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2134">**Icon** ![Host Class Prolific Deactivate icon](./media/user-guide/usbx-events/image160.png)</span></span>

<span data-ttu-id="65356-2135">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2135">**Description**</span></span>

<span data-ttu-id="65356-2136">이 이벤트는 USBX 호스트 클래스 Prolific 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2136">This event represents a USBX Host Class Prolific Deactivate Event.</span></span>

<span data-ttu-id="65356-2137">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2137">**Information Fields**</span></span>

- <span data-ttu-id="65356-2138">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2138">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2139">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2139">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2140">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2140">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2141">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2141">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a><span data-ttu-id="65356-2142">호스트 클래스 Prolific Ioctl 파이프에서 중단</span><span class="sxs-lookup"><span data-stu-id="65356-2142">Host Class Prolific Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a><span data-ttu-id="65356-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="65356-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="65356-2144">**아이콘** ![호스트 클래스 Prolific Ioctl 파이프에서 중단 아이콘](./media/user-guide/usbx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2144">**Icon** ![Host Class Prolific I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image161.png)</span></span>

<span data-ttu-id="65356-2145">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2145">**Description**</span></span>

<span data-ttu-id="65356-2146">이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 파이프에서 중단 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2146">This event represents a USBX Host Class Prolific Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="65356-2147">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2147">**Information Fields**</span></span>

- <span data-ttu-id="65356-2148">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2148">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2149">정보 필드 2: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-2149">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="65356-2150">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2150">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2151">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2151">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a><span data-ttu-id="65356-2152">호스트 클래스 Prolific Ioctl 파이프 외부에서 중단</span><span class="sxs-lookup"><span data-stu-id="65356-2152">Host Class Prolific Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a><span data-ttu-id="65356-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="65356-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span></span>

<span data-ttu-id="65356-2154">**아이콘** ![호스트 클래스 Prolific Ioctl 파이프 외부에서 중단 아이콘](./media/user-guide/usbx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2154">**Icon** ![Host Class Prolific I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image162.png)</span></span>

<span data-ttu-id="65356-2155">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2155">**Description**</span></span>

<span data-ttu-id="65356-2156">이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 파이프 외부에서 중단 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2156">This event represents a USBX Host Class Prolific Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="65356-2157">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2157">**Information Fields**</span></span>

- <span data-ttu-id="65356-2158">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2158">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2159">정보 필드 2: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-2159">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="65356-2160">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2160">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2161">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2161">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-device-status"></a><span data-ttu-id="65356-2162">호스트 클래스 Prolific Ioctl 디바이스 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-2162">Host Class Prolific Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a><span data-ttu-id="65356-2163">ux_host_class_prolific_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="65356-2163">ux_host_class_prolific_ioctl_get_device_status</span></span>

<span data-ttu-id="65356-2164">**아이콘** ![호스트 클래스 Prolific Ioctl 디바이스 상태 가져오기 아이콘](./media/user-guide/usbx-events/image163.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2164">**Icon** ![Host Class Prolific I O C T L Get Device Status icon](./media/user-guide/usbx-events/image163.png)</span></span>

<span data-ttu-id="65356-2165">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2165">**Description**</span></span>

<span data-ttu-id="65356-2166">이 이벤트는 c # 호스트 클래스 Prolific Ioctl 디바이스 상태 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2166">This event represents a USBX Host Class Prolific Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="65356-2167">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2167">**Information Fields**</span></span>

- <span data-ttu-id="65356-2168">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2168">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2169">정보 필드 2: 디바이스 상태</span><span class="sxs-lookup"><span data-stu-id="65356-2169">Info Field 2: Device status.</span></span>
- <span data-ttu-id="65356-2170">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2170">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2171">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2171">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-line-coding"></a><span data-ttu-id="65356-2172">호스트 클래스 Prolific Ioctl 줄 코드 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-2172">Host Class Prolific Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a><span data-ttu-id="65356-2173">ux_host_class_prolific_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="65356-2173">ux_host_class_prolific_ioctl_get_line_coding</span></span>

<span data-ttu-id="65356-2174">**아이콘** ![호스트 클래스 Prolific Ioctl 줄 코드 가져오기 아이콘](./media/user-guide/usbx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2174">**Icon** ![Host Class Prolific I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image164.png)</span></span>

<span data-ttu-id="65356-2175">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2175">**Description**</span></span>

<span data-ttu-id="65356-2176">이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 줄 코드 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2176">This event represents a USBX Host Class Prolific Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="65356-2177">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2177">**Information Fields**</span></span>

- <span data-ttu-id="65356-2178">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2178">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2179">정보 필드 2: 매개 변수</span><span class="sxs-lookup"><span data-stu-id="65356-2179">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="65356-2180">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2180">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2181">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2181">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-purge"></a><span data-ttu-id="65356-2182">호스트 클래스 Prolific Ioctl 제거</span><span class="sxs-lookup"><span data-stu-id="65356-2182">Host Class Prolific Ioctl Purge</span></span> 

#### <a name="ux_host_class_prolific_ioctl_purge"></a><span data-ttu-id="65356-2183">ux_host_class_prolific_ioctl_purge</span><span class="sxs-lookup"><span data-stu-id="65356-2183">ux_host_class_prolific_ioctl_purge</span></span>

<span data-ttu-id="65356-2184">**아이콘** ![호스트 클래스 Prolific Ioctl 제거 아이콘](./media/user-guide/usbx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2184">**Icon** ![Host Class Prolific Ioctl Purge icon](./media/user-guide/usbx-events/image165.png)</span></span>

<span data-ttu-id="65356-2185">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2185">**Description**</span></span>

<span data-ttu-id="65356-2186">이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 제거 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2186">This event represents a USBX Host Class Prolific Ioctl Purge Event.</span></span>

<span data-ttu-id="65356-2187">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2187">**Information Fields**</span></span>

- <span data-ttu-id="65356-2188">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2188">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2189">정보 필드 2: 매개 변수</span><span class="sxs-lookup"><span data-stu-id="65356-2189">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="65356-2190">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2190">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2191">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2191">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-report-device"></a><span data-ttu-id="65356-2192">호스트 클래스 Prolific Ioctl 보고서 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2192">Host Class Prolific Ioctl Report Device</span></span> 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a><span data-ttu-id="65356-2193">ux_host_class_prolific_ioctl_report_device</span><span class="sxs-lookup"><span data-stu-id="65356-2193">ux_host_class_prolific_ioctl_report_device</span></span>

<span data-ttu-id="65356-2194">**아이콘** ![호스트 클래스 Prolific Ioctl 보고서 디바이스 아이콘](./media/user-guide/usbx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2194">**Icon** ![Host Class Prolific I O C T L Report Device icon](./media/user-guide/usbx-events/image166.png)</span></span>

<span data-ttu-id="65356-2195">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2195">**Description**</span></span>

<span data-ttu-id="65356-2196">이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 보고서 디바이스 상태 변경 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2196">This event represents a USBX Host Class Prolific Ioctl Report Device Status Change Event.</span></span>

<span data-ttu-id="65356-2197">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2197">**Information Fields**</span></span>

- <span data-ttu-id="65356-2198">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2198">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2199">정보 필드 2: 매개 변수</span><span class="sxs-lookup"><span data-stu-id="65356-2199">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="65356-2200">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2200">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2201">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2201">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-send-break"></a><span data-ttu-id="65356-2202">호스트 클래스 Prolific Ioctl 보내기 중단</span><span class="sxs-lookup"><span data-stu-id="65356-2202">Host Class Prolific Ioctl Send Break</span></span> 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a><span data-ttu-id="65356-2203">ux_host_class_prolific_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="65356-2203">ux_host_class_prolific_ioctl_send_break</span></span>

<span data-ttu-id="65356-2204">**아이콘** ![호스트 클래스 Prolific Ioctl 보내기 중단 아이콘](./media/user-guide/usbx-events/image167.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2204">**Icon** ![Host Class Prolific I O C T L Send Break icon](./media/user-guide/usbx-events/image167.png)</span></span>

<span data-ttu-id="65356-2205">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2205">**Description**</span></span>

<span data-ttu-id="65356-2206">이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 보내기 중단 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2206">This event represents a USBX Host Class Prolific Ioctl Send Break Event.</span></span>

<span data-ttu-id="65356-2207">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2207">**Information Fields**</span></span>

- <span data-ttu-id="65356-2208">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2208">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2209">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2209">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2210">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2210">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2211">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2211">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-coding"></a><span data-ttu-id="65356-2212">호스트 클래스 Prolific Ioctl 줄 코드 설정</span><span class="sxs-lookup"><span data-stu-id="65356-2212">Host Class Prolific Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a><span data-ttu-id="65356-2213">ux_host_class_prolific_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="65356-2213">ux_host_class_prolific_ioctl_set_line_coding</span></span>

<span data-ttu-id="65356-2214">**아이콘** ![호스트 클래스 Prolific Ioctl 줄 코드 설정 아이콘](./media/user-guide/usbx-events/image168.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2214">**Icon** ![Host Class Prolific I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image168.png)</span></span>

<span data-ttu-id="65356-2215">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2215">**Description**</span></span>

<span data-ttu-id="65356-2216">이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 줄 코드 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2216">This event represents a USBX Host Class Prolific Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="65356-2217">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2217">**Information Fields**</span></span>

- <span data-ttu-id="65356-2218">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2218">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2219">정보 필드 2: 매개 변수</span><span class="sxs-lookup"><span data-stu-id="65356-2219">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="65356-2220">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2220">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2221">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2221">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-state"></a><span data-ttu-id="65356-2222">호스트 클래스 Prolific Ioctl 줄 상태 설정</span><span class="sxs-lookup"><span data-stu-id="65356-2222">Host Class Prolific Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a><span data-ttu-id="65356-2223">ux_host_class_prolific_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="65356-2223">ux_host_class_prolific_ioctl_set_line_state</span></span>

<span data-ttu-id="65356-2224">**아이콘** ![호스트 클래스 Prolific Ioctl 줄 상태 설정 아이콘](./media/user-guide/usbx-events/image169.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2224">**Icon** ![Host Class Prolific I O C T L Set Line State icon](./media/user-guide/usbx-events/image169.png)</span></span>

<span data-ttu-id="65356-2225">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2225">**Description**</span></span>

<span data-ttu-id="65356-2226">이 이벤트는 USBX 호스트 클래스 Prolific Ioctl 줄 상태 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2226">This event represents a USBX Host Class Prolific Ioctl Set Line State Event.</span></span>

<span data-ttu-id="65356-2227">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2227">**Information Fields**</span></span>

- <span data-ttu-id="65356-2228">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2228">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2229">정보 필드 2: 매개 변수</span><span class="sxs-lookup"><span data-stu-id="65356-2229">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="65356-2230">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2230">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2231">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2231">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-read"></a><span data-ttu-id="65356-2232">호스트 클래스 Prolific 읽기</span><span class="sxs-lookup"><span data-stu-id="65356-2232">Host Class Prolific Read</span></span> 

#### <a name="ux_host_class_prolific_read"></a><span data-ttu-id="65356-2233">ux_host_class_prolific_read</span><span class="sxs-lookup"><span data-stu-id="65356-2233">ux_host_class_prolific_read</span></span>

<span data-ttu-id="65356-2234">**아이콘** ![호스트 클래스 Prolific 읽기 아이콘](./media/user-guide/usbx-events/image170.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2234">**Icon** ![Host Class Prolific Read icon](./media/user-guide/usbx-events/image170.png)</span></span>

<span data-ttu-id="65356-2235">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2235">**Description**</span></span>

<span data-ttu-id="65356-2236">이 이벤트는 USBX 호스트 클래스 Prolific 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2236">This event represents a USBX Host Class Prolific Read Event.</span></span>

<span data-ttu-id="65356-2237">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2237">**Information Fields**</span></span>

- <span data-ttu-id="65356-2238">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2238">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2239">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-2239">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-2240">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-2240">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-2241">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2241">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-start"></a><span data-ttu-id="65356-2242">호스트 클래스 Prolific 수신 시작</span><span class="sxs-lookup"><span data-stu-id="65356-2242">Host Class Prolific Reception Start</span></span> 

#### <a name="ux_host_class_prolific_reception_start"></a><span data-ttu-id="65356-2243">ux_host_class_prolific_reception_start</span><span class="sxs-lookup"><span data-stu-id="65356-2243">ux_host_class_prolific_reception_start</span></span>

<span data-ttu-id="65356-2244">**아이콘** ![호스트 클래스 Prolific 수신 시작 아이콘](./media/user-guide/usbx-events/image171.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2244">**Icon** ![Host Class Prolific Reception Start icon](./media/user-guide/usbx-events/image171.png)</span></span>

<span data-ttu-id="65356-2245">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2245">**Description**</span></span>

<span data-ttu-id="65356-2246">이 이벤트는 USBX 호스트 클래스 Prolific 수신 시작 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2246">This event represents a USBX Host Class Prolific Reception Start Event.</span></span>

<span data-ttu-id="65356-2247">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2247">**Information Fields**</span></span>

- <span data-ttu-id="65356-2248">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2248">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2249">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2249">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2250">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2250">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2251">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2251">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-stop"></a><span data-ttu-id="65356-2252">호스트 클래스 Prolific 수신 중지</span><span class="sxs-lookup"><span data-stu-id="65356-2252">Host Class Prolific Reception Stop</span></span> 

#### <a name="ux_host_class_prolific_reception_stop"></a><span data-ttu-id="65356-2253">ux_host_class_prolific_reception_stop</span><span class="sxs-lookup"><span data-stu-id="65356-2253">ux_host_class_prolific_reception_stop</span></span>

<span data-ttu-id="65356-2254">**아이콘** ![호스트 클래스 Prolific 수신 중지 아이콘](./media/user-guide/usbx-events/image172.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2254">**Icon** ![Host Class Prolific Reception Stop icon](./media/user-guide/usbx-events/image172.png)</span></span>

<span data-ttu-id="65356-2255">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2255">**Description**</span></span>

<span data-ttu-id="65356-2256">이 이벤트는 USBX 호스트 클래스 Prolific 수신 중지 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2256">This event represents a USBX Host Class Prolific Reception Stop Event.</span></span>

<span data-ttu-id="65356-2257">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2257">**Information Fields**</span></span>

- <span data-ttu-id="65356-2258">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2258">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2259">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2259">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2260">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2260">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2261">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2261">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-write"></a><span data-ttu-id="65356-2262">호스트 클래스 Prolific 쓰기</span><span class="sxs-lookup"><span data-stu-id="65356-2262">Host Class Prolific Write</span></span> 

#### <a name="ux_host_class_prolific_write"></a><span data-ttu-id="65356-2263">ux_host_class_prolific_write</span><span class="sxs-lookup"><span data-stu-id="65356-2263">ux_host_class_prolific_write</span></span>

<span data-ttu-id="65356-2264">**아이콘** ![호스트 클래스 Prolific 쓰기 아이콘](./media/user-guide/usbx-events/image173.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2264">**Icon** ![Host Class Prolific Write icon](./media/user-guide/usbx-events/image173.png)</span></span>

<span data-ttu-id="65356-2265">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2265">**Description**</span></span>

<span data-ttu-id="65356-2266">이 이벤트는 USBX 호스트 클래스 Prolific 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2266">This event represents a USBX Host Class Prolific Write Event.</span></span>

<span data-ttu-id="65356-2267">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2267">**Information Fields**</span></span>

- <span data-ttu-id="65356-2268">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2268">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2269">정보 필드 2: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-2269">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="65356-2270">정보 필드 3: 요청된 길이</span><span class="sxs-lookup"><span data-stu-id="65356-2270">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="65356-2271">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2271">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-activate"></a><span data-ttu-id="65356-2272">호스트 클래스 스토리지 활성화</span><span class="sxs-lookup"><span data-stu-id="65356-2272">Host Class Storage Activate</span></span> 

#### <a name="ux_host_class_storage_activate"></a><span data-ttu-id="65356-2273">ux_host_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="65356-2273">ux_host_class_storage_activate</span></span>

<span data-ttu-id="65356-2274">**아이콘** ![호스트 클래스 스토리지 활성화 아이콘](./media/user-guide/usbx-events/image174.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2274">**Icon** ![Host Class Storage Activate icon](./media/user-guide/usbx-events/image174.png)</span></span>

<span data-ttu-id="65356-2275">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2275">**Description**</span></span>

<span data-ttu-id="65356-2276">이 이벤트는 USBX 호스트 클래스 스토리지 활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2276">This event represents a USBX Host Class Storage Activate Event.</span></span>

<span data-ttu-id="65356-2277">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2277">**Information Fields**</span></span>

- <span data-ttu-id="65356-2278">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2278">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2279">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2279">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2280">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2280">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2281">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2281">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-deactivate"></a><span data-ttu-id="65356-2282">호스트 클래스 스토리지 비활성화</span><span class="sxs-lookup"><span data-stu-id="65356-2282">Host Class Storage Deactivate</span></span> 

#### <a name="ux_host_class_storage_deactivate"></a><span data-ttu-id="65356-2283">ux_host_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="65356-2283">ux_host_class_storage_deactivate</span></span>

<span data-ttu-id="65356-2284">**아이콘** ![호스트 클래스 스토리지 비활성화 아이콘](./media/user-guide/usbx-events/image175.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2284">**Icon** ![Host Class Storage Deactivate icon](./media/user-guide/usbx-events/image175.png)</span></span>

<span data-ttu-id="65356-2285">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2285">**Description**</span></span>

<span data-ttu-id="65356-2286">이 이벤트는 USBX 호스트 클래스 스토리지 비활성화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2286">This event represents a USBX Host Class Storage Deactivate Event.</span></span>

<span data-ttu-id="65356-2287">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2287">**Information Fields**</span></span>

- <span data-ttu-id="65356-2288">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2288">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2289">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2289">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2290">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2290">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2291">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2291">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-capacity-get"></a><span data-ttu-id="65356-2292">호스트 클래스 스토리지 미디어 용량 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-2292">Host Class Storage Media Capacity Get</span></span> 

#### <a name="ux_host_class_storage_media_capacity_get"></a><span data-ttu-id="65356-2293">ux_host_class_storage_media_capacity_get</span><span class="sxs-lookup"><span data-stu-id="65356-2293">ux_host_class_storage_media_capacity_get</span></span>

<span data-ttu-id="65356-2294">**아이콘** ![호스트 클래스 스토리지 미디어 용량 가져오기 아이콘](./media/user-guide/usbx-events/image176.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2294">**Icon** ![Host Class Storage Media Capacity Get icon](./media/user-guide/usbx-events/image176.png)</span></span>

<span data-ttu-id="65356-2295">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2295">**Description**</span></span>

<span data-ttu-id="65356-2296">이 이벤트는 USBX 호스트 클래스 스토리지 미디어 용량 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2296">This event represents a USBX Host Class Storage Media Capacity Get Event.</span></span>

<span data-ttu-id="65356-2297">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2297">**Information Fields**</span></span>

- <span data-ttu-id="65356-2298">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2298">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2299">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2299">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2300">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2300">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2301">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2301">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-format-capacity-get"></a><span data-ttu-id="65356-2302">호스트 클래스 스토리지 미디어 형식 용량 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-2302">Host Class Storage Media Format Capacity Get</span></span>

#### <a name="ux_host_class_storage_media_format_capacity_get"></a><span data-ttu-id="65356-2303">ux_host_class_storage_media_format_capacity_get</span><span class="sxs-lookup"><span data-stu-id="65356-2303">ux_host_class_storage_media_format_capacity_get</span></span>

<span data-ttu-id="65356-2304">**아이콘** ![호스트 클래스 스토리지 미디어 형식 용량 가져오기 아이콘](./media/user-guide/usbx-events/image177.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2304">**Icon** ![Host Class Storage Media Format Capacity Get icon](./media/user-guide/usbx-events/image177.png)</span></span>

<span data-ttu-id="65356-2305">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2305">**Description**</span></span>

<span data-ttu-id="65356-2306">이 이벤트는 USBX 호스트 클래스 스토리지 미디어 형식 용량 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2306">This event represents a USBX Host Class Storage Media Format Capacity Get Event.</span></span>

<span data-ttu-id="65356-2307">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2307">**Information Fields**</span></span>

- <span data-ttu-id="65356-2308">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2308">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2309">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2309">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2310">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2310">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2311">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2311">Info Field 4: Not used.</span></span>

#### <a name="host-class-storage-media-mount"></a><span data-ttu-id="65356-2312">호스트 클래스 스토리지 미디어 탑재</span><span class="sxs-lookup"><span data-stu-id="65356-2312">Host Class Storage Media Mount</span></span> 

#### <a name="ux_host_class_storage_media_mount"></a><span data-ttu-id="65356-2313">ux_host_class_storage_media_mount</span><span class="sxs-lookup"><span data-stu-id="65356-2313">ux_host_class_storage_media_mount</span></span>

<span data-ttu-id="65356-2314">**아이콘** ![호스트 클래스 스토리지 미디어 탑재 아이콘](./media/user-guide/usbx-events/image178.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2314">**Icon** ![Host Class Storage Media Mount icon](./media/user-guide/usbx-events/image178.png)</span></span>

<span data-ttu-id="65356-2315">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2315">**Description**</span></span>

<span data-ttu-id="65356-2316">이 이벤트는 USBX 호스트 클래스 스토리지 미디어 탑재 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2316">This event represents a USBX Host Class Storage Media Mount Event.</span></span>

<span data-ttu-id="65356-2317">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2317">**Information Fields**</span></span>

- <span data-ttu-id="65356-2318">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2318">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2319">정보 필드 2: 섹터</span><span class="sxs-lookup"><span data-stu-id="65356-2319">Info Field 2: Sector.</span></span>
- <span data-ttu-id="65356-2320">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2320">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2321">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2321">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-open"></a><span data-ttu-id="65356-2322">호스트 클래스 스토리지 미디어 열기</span><span class="sxs-lookup"><span data-stu-id="65356-2322">Host Class Storage Media Open</span></span> 

#### <a name="ux_host_class_storage_media_open"></a><span data-ttu-id="65356-2323">ux_host_class_storage_media_open</span><span class="sxs-lookup"><span data-stu-id="65356-2323">ux_host_class_storage_media_open</span></span>

<span data-ttu-id="65356-2324">**아이콘** ![호스트 클래스 스토리지 미디어 열기 아이콘](./media/user-guide/usbx-events/image179.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2324">**Icon** ![Host Class Storage Media Open icon](./media/user-guide/usbx-events/image179.png)</span></span>

<span data-ttu-id="65356-2325">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2325">**Description**</span></span>

<span data-ttu-id="65356-2326">이 이벤트는 USBX 호스트 클래스 스토리지 미디어 열기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2326">This event represents a USBX Host Class Storage Media Open Event.</span></span>

<span data-ttu-id="65356-2327">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2327">**Information Fields**</span></span>

- <span data-ttu-id="65356-2328">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2328">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2329">정보 필드 2: 미디어</span><span class="sxs-lookup"><span data-stu-id="65356-2329">Info Field 2: Media.</span></span>
- <span data-ttu-id="65356-2330">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2330">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2331">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2331">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-read"></a><span data-ttu-id="65356-2332">호스트 클래스 스토리지 미디어 읽기</span><span class="sxs-lookup"><span data-stu-id="65356-2332">Host Class Storage Media Read</span></span> 

#### <a name="ux_host_class_storage_media_read"></a><span data-ttu-id="65356-2333">ux_host_class_storage_media_read</span><span class="sxs-lookup"><span data-stu-id="65356-2333">ux_host_class_storage_media_read</span></span>

<span data-ttu-id="65356-2334">**아이콘** ![호스트 클래스 스토리지 미디어 읽기 아이콘](./media/user-guide/usbx-events/image180.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2334">**Icon** ![Host Class Storage Media Read icon](./media/user-guide/usbx-events/image180.png)</span></span>

<span data-ttu-id="65356-2335">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2335">**Description**</span></span>

<span data-ttu-id="65356-2336">이 이벤트는 USBX 호스트 클래스 스토리지 미디어 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2336">This event represents a USBX Host Class Storage Media Read Event.</span></span>

<span data-ttu-id="65356-2337">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2337">**Information Fields**</span></span>

- <span data-ttu-id="65356-2338">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2338">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2339">정보 필드 2: 섹터 시작</span><span class="sxs-lookup"><span data-stu-id="65356-2339">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="65356-2340">정보 필드 3: 섹터 수</span><span class="sxs-lookup"><span data-stu-id="65356-2340">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="65356-2341">정보 필드 4: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-2341">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-media-write"></a><span data-ttu-id="65356-2342">호스트 클래스 스토리지 미디어 쓰기</span><span class="sxs-lookup"><span data-stu-id="65356-2342">Host Class Storage Media Write</span></span> 

#### <a name="ux_host_class_storage_media_write"></a><span data-ttu-id="65356-2343">ux_host_class_storage_media_write</span><span class="sxs-lookup"><span data-stu-id="65356-2343">ux_host_class_storage_media_write</span></span>

<span data-ttu-id="65356-2344">**아이콘** ![호스트 클래스 스토리지 미디어 쓰기 아이콘](./media/user-guide/usbx-events/image181.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2344">**Icon** ![Host Class Storage Media Write icon](./media/user-guide/usbx-events/image181.png)</span></span>

<span data-ttu-id="65356-2345">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2345">**Description**</span></span>

<span data-ttu-id="65356-2346">이 이벤트는 USBX 호스트 클래스 스토리지 미디어 쓰기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2346">This event represents a USBX Host Class Storage Media Write Event.</span></span>

<span data-ttu-id="65356-2347">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2347">**Information Fields**</span></span>

- <span data-ttu-id="65356-2348">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2348">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2349">정보 필드 2: 섹터 시작</span><span class="sxs-lookup"><span data-stu-id="65356-2349">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="65356-2350">정보 필드 3: 섹터 수</span><span class="sxs-lookup"><span data-stu-id="65356-2350">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="65356-2351">정보 필드 4: 데이터 포인터</span><span class="sxs-lookup"><span data-stu-id="65356-2351">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-request-sense"></a><span data-ttu-id="65356-2352">호스트 클래스 스토리지 요청 센스</span><span class="sxs-lookup"><span data-stu-id="65356-2352">Host Class Storage Request Sense</span></span> 

#### <a name="ux_host_class_storage_request_sense"></a><span data-ttu-id="65356-2353">ux_host_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="65356-2353">ux_host_class_storage_request_sense</span></span>

<span data-ttu-id="65356-2354">**아이콘** ![호스트 클래스 스토리지 요청 센스 아이콘](./media/user-guide/usbx-events/image182.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2354">**Icon** ![Host Class Storage Request Sense icon](./media/user-guide/usbx-events/image182.png)</span></span>

<span data-ttu-id="65356-2355">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2355">**Description**</span></span>

<span data-ttu-id="65356-2356">이 이벤트는 USBX 호스트 클래스 스토리지 요청 센스 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2356">This event represents a USBX Host Class Storage Request Sense Event.</span></span>

<span data-ttu-id="65356-2357">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2357">**Information Fields**</span></span>

- <span data-ttu-id="65356-2358">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2358">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2359">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2359">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2360">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2360">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2361">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2361">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-start-stop"></a><span data-ttu-id="65356-2362">호스트 클래스 스토리지 시작 중지</span><span class="sxs-lookup"><span data-stu-id="65356-2362">Host Class Storage Start Stop</span></span> 

#### <a name="ux_host_class_storage_start_stop"></a><span data-ttu-id="65356-2363">ux_host_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="65356-2363">ux_host_class_storage_start_stop</span></span>

<span data-ttu-id="65356-2364">**아이콘** ![호스트 클래스 스토리지 시작 중지 아이콘](./media/user-guide/usbx-events/image183.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2364">**Icon** ![Host Class Storage Start Stop icon](./media/user-guide/usbx-events/image183.png)</span></span>

<span data-ttu-id="65356-2365">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2365">**Description**</span></span>

<span data-ttu-id="65356-2366">이 이벤트는 USBX 호스트 클래스 스토리지 시작 중지 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2366">This event represents a USBX Host Class Storage Start Stop Event.</span></span>

<span data-ttu-id="65356-2367">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2367">**Information Fields**</span></span>

- <span data-ttu-id="65356-2368">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2368">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2369">정보 필드 2: 시작 중지 신호</span><span class="sxs-lookup"><span data-stu-id="65356-2369">Info Field 2: Start stop signal.</span></span>
- <span data-ttu-id="65356-2370">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2370">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2371">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2371">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-unit-ready-test"></a><span data-ttu-id="65356-2372">호스트 클래스 스토리지 장치 준비 테스트</span><span class="sxs-lookup"><span data-stu-id="65356-2372">Host Class Storage Unit Ready Test</span></span> 

#### <a name="ux_host_class_storage_unit_ready_test"></a><span data-ttu-id="65356-2373">ux_host_class_storage_unit_ready_test</span><span class="sxs-lookup"><span data-stu-id="65356-2373">ux_host_class_storage_unit_ready_test</span></span>

<span data-ttu-id="65356-2374">**아이콘** ![호스트 클래스 스토리지 장치 준비 테스트 아이콘](./media/user-guide/usbx-events/image184.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2374">**Icon** ![Host Class Storage Unit Ready Test icon](./media/user-guide/usbx-events/image184.png)</span></span>

<span data-ttu-id="65356-2375">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2375">**Description**</span></span>

<span data-ttu-id="65356-2376">이 이벤트는 USBX 호스트 클래스 스토리지 단위 준비 테스트 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2376">This event represents a USBX Host Class Storage Unit Ready Test Event.</span></span>

<span data-ttu-id="65356-2377">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2377">**Information Fields**</span></span>

- <span data-ttu-id="65356-2378">정보 필드 1: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2378">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="65356-2379">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2379">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2380">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2380">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2381">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2381">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-create"></a><span data-ttu-id="65356-2382">호스트 스택 클래스 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="65356-2382">Host Stack Class Instance Create</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="65356-2383">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="65356-2383">ux_host_class_instance_create</span></span>

<span data-ttu-id="65356-2384">**아이콘** ![호스트 스택 클래스 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image185.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2384">**Icon** ![Host Stack Class Instance Create icon](./media/user-guide/usbx-events/image185.png)</span></span>

<span data-ttu-id="65356-2385">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2385">**Description**</span></span>

<span data-ttu-id="65356-2386">이 이벤트는 USBX 호스트 스택 클래스 인스턴스 만들기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2386">This event represents a USBX Host Stack Class Instance Create Event.</span></span>

<span data-ttu-id="65356-2387">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2387">**Information Fields**</span></span>

- <span data-ttu-id="65356-2388">정보 필드 1: 클래스</span><span class="sxs-lookup"><span data-stu-id="65356-2388">Info Field 1: Class.</span></span>
- <span data-ttu-id="65356-2389">정보 필드 2: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2389">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="65356-2390">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2390">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2391">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2391">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-destroy"></a><span data-ttu-id="65356-2392">호스트 스택 클래스 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="65356-2392">Host Stack Class Instance Destroy</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="65356-2393">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="65356-2393">ux_host_class_instance_create</span></span>

<span data-ttu-id="65356-2394">**아이콘** ![호스트 스택 클래스 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image186.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2394">**Icon** ![Host Stack Class Instance Destroy icon](./media/user-guide/usbx-events/image186.png)</span></span>

<span data-ttu-id="65356-2395">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2395">**Description**</span></span>

<span data-ttu-id="65356-2396">이 이벤트는 USBX 호스트 스택 클래스 인스턴스 삭제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2396">This event represents a USBX Host Stack Class Instance Destroy Event.</span></span>

<span data-ttu-id="65356-2397">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2397">**Information Fields**</span></span>

- <span data-ttu-id="65356-2398">정보 필드 1: 클래스</span><span class="sxs-lookup"><span data-stu-id="65356-2398">Info Field 1: Class.</span></span>
- <span data-ttu-id="65356-2399">정보 필드 2: 클래스 인스턴스</span><span class="sxs-lookup"><span data-stu-id="65356-2399">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="65356-2400">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2400">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2401">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2401">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-delete"></a><span data-ttu-id="65356-2402">호스트 스택 구성 삭제</span><span class="sxs-lookup"><span data-stu-id="65356-2402">Host Stack Configuration Delete</span></span> 

#### <a name="ux_host_class_configuration_delete"></a><span data-ttu-id="65356-2403">ux_host_class_configuration_delete</span><span class="sxs-lookup"><span data-stu-id="65356-2403">ux_host_class_configuration_delete</span></span>

<span data-ttu-id="65356-2404">**아이콘** ![호스트 스택 구성 삭제 아이콘](./media/user-guide/usbx-events/image187.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2404">**Icon** ![Host Stack Configuration Delete icon](./media/user-guide/usbx-events/image187.png)</span></span>

<span data-ttu-id="65356-2405">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2405">**Description**</span></span>

<span data-ttu-id="65356-2406">이 이벤트는 USBX 호스트 스택 구성 삭제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2406">This event represents a USBX Host Stack Configuration Delete Event.</span></span>

<span data-ttu-id="65356-2407">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2407">**Information Fields**</span></span>

- <span data-ttu-id="65356-2408">정보 필드 1: 구성</span><span class="sxs-lookup"><span data-stu-id="65356-2408">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="65356-2409">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2409">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2410">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2410">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2411">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2411">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-enumerate"></a><span data-ttu-id="65356-2412">호스트 스택 구성 열거</span><span class="sxs-lookup"><span data-stu-id="65356-2412">Host Stack Configuration Enumerate</span></span> 

#### <a name="ux_host_stack_configuration_enumerate"></a><span data-ttu-id="65356-2413">ux_host_stack_configuration_enumerate</span><span class="sxs-lookup"><span data-stu-id="65356-2413">ux_host_stack_configuration_enumerate</span></span>

<span data-ttu-id="65356-2414">**아이콘** ![호스트 스택 구성 열거 아이콘](./media/user-guide/usbx-events/image188.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2414">**Icon** ![Host Stack Configuration Enumerate icon](./media/user-guide/usbx-events/image188.png)</span></span>

<span data-ttu-id="65356-2415">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2415">**Description**</span></span>

<span data-ttu-id="65356-2416">이 이벤트는 USBX 호스트 스택 구성 열거 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2416">This event represents a USBX Host Stack Configuration Enumerate Event.</span></span>

<span data-ttu-id="65356-2417">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2417">**Information Fields**</span></span>

- <span data-ttu-id="65356-2418">정보 필드 1: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2418">Info Field 1: Device.</span></span>
- <span data-ttu-id="65356-2419">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2419">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2420">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2420">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2421">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2421">Info Field 4: Not used.</span></span>

### <a name="stack-configuration-instance-create"></a><span data-ttu-id="65356-2422">스택 구성 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="65356-2422">Stack Configuration Instance Create</span></span> 

#### <a name="ux_host_stack_configuration_instance_create"></a><span data-ttu-id="65356-2423">ux_host_stack_configuration_instance_create</span><span class="sxs-lookup"><span data-stu-id="65356-2423">ux_host_stack_configuration_instance_create</span></span>

<span data-ttu-id="65356-2424">**아이콘** ![스택 구성 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image189.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2424">**Icon** ![Stack Configuration Instance Create icon](./media/user-guide/usbx-events/image189.png)</span></span>

<span data-ttu-id="65356-2425">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2425">**Description**</span></span>

<span data-ttu-id="65356-2426">이 이벤트는 USBX 호스트 스택 구성 인스턴스 만들기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2426">This event represents a USBX Host Stack Configuration Instance Create Event.</span></span>

<span data-ttu-id="65356-2427">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2427">**Information Fields**</span></span>

- <span data-ttu-id="65356-2428">정보 필드 1: 구성</span><span class="sxs-lookup"><span data-stu-id="65356-2428">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="65356-2429">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2429">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2430">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2430">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2431">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2431">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-instance-delete"></a><span data-ttu-id="65356-2432">호스트 스택 구성 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="65356-2432">Host Stack Configuration Instance Delete</span></span> 

#### <a name="ux_host_stack_configuration_instance_delete"></a><span data-ttu-id="65356-2433">ux_host_stack_configuration_instance_delete</span><span class="sxs-lookup"><span data-stu-id="65356-2433">ux_host_stack_configuration_instance_delete</span></span>

<span data-ttu-id="65356-2434">**아이콘** ![호스트 스택 구성 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image190.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2434">**Icon** ![Host Stack Configuration Instance Delete icon](./media/user-guide/usbx-events/image190.png)</span></span>

<span data-ttu-id="65356-2435">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2435">**Description**</span></span>

<span data-ttu-id="65356-2436">이 이벤트는 USBX 호스트 스택 구성 인스턴스 삭제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2436">This event represents a USBX Host Stack Configuration Instance Delete Event.</span></span>

<span data-ttu-id="65356-2437">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2437">**Information Fields**</span></span>

- <span data-ttu-id="65356-2438">정보 필드 1: 구성</span><span class="sxs-lookup"><span data-stu-id="65356-2438">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="65356-2439">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2439">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2440">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2440">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2441">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2441">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-set"></a><span data-ttu-id="65356-2442">호스트 스택 구성 설정</span><span class="sxs-lookup"><span data-stu-id="65356-2442">Host Stack Configuration Set</span></span> 

#### <a name="ux_host_stack_configuration_set"></a><span data-ttu-id="65356-2443">ux_host_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="65356-2443">ux_host_stack_configuration_set</span></span>

<span data-ttu-id="65356-2444">**아이콘** ![호스트 스택 구성 설정 아이콘](./media/user-guide/usbx-events/image191.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2444">**Icon** ![Host Stack Configuration Set icon](./media/user-guide/usbx-events/image191.png)</span></span>

<span data-ttu-id="65356-2445">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2445">**Description**</span></span>

<span data-ttu-id="65356-2446">이 이벤트는 USBX 호스트 스택 구성 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2446">This event represents a USBX Host Stack Configuration Set Event.</span></span>

<span data-ttu-id="65356-2447">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2447">**Information Fields**</span></span>

- <span data-ttu-id="65356-2448">정보 필드 1: 구성</span><span class="sxs-lookup"><span data-stu-id="65356-2448">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="65356-2449">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2449">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2450">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2451">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2451">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-address-set"></a><span data-ttu-id="65356-2452">호스트 스택 디바이스 주소 설정</span><span class="sxs-lookup"><span data-stu-id="65356-2452">Host Stack Device Address Set</span></span> 

#### <a name="ux_host_stack_device_address_set"></a><span data-ttu-id="65356-2453">ux_host_stack_device_address_set</span><span class="sxs-lookup"><span data-stu-id="65356-2453">ux_host_stack_device_address_set</span></span>

<span data-ttu-id="65356-2454">**아이콘** ![호스트 스택 디바이스 주소 설정 아이콘](./media/user-guide/usbx-events/image192.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2454">**Icon** ![Host Stack Device Address Set icon](./media/user-guide/usbx-events/image192.png)</span></span>

<span data-ttu-id="65356-2455">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2455">**Description**</span></span>

<span data-ttu-id="65356-2456">이 이벤트는 USBX 호스트 스택 디바이스 주소 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2456">This event represents a USBX Host Stack Device Address Set Event.</span></span>

<span data-ttu-id="65356-2457">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2457">**Information Fields**</span></span>

- <span data-ttu-id="65356-2458">정보 필드 1: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2458">Info Field 1: Device.</span></span>
- <span data-ttu-id="65356-2459">정보 필드 2: 디바이스 주소</span><span class="sxs-lookup"><span data-stu-id="65356-2459">Info Field 2: Device Address.</span></span>
- <span data-ttu-id="65356-2460">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2461">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2461">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-get"></a><span data-ttu-id="65356-2462">호스트 스택 디바이스 구성 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-2462">Host Stack Device Configuration Get</span></span> 

#### <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="65356-2463">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="65356-2463">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="65356-2464">**아이콘** ![호스트 스택 디바이스 구성 가져오기 아이콘](./media/user-guide/usbx-events/image193.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2464">**Icon** ![Host Stack Device Configuration Get icon](./media/user-guide/usbx-events/image193.png)</span></span>

<span data-ttu-id="65356-2465">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2465">**Description**</span></span>

<span data-ttu-id="65356-2466">이 이벤트는 USBX 호스트 스택 디바이스 구성 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2466">This event represents a USBX Host Stack Device Configuration Get Event.</span></span>

<span data-ttu-id="65356-2467">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2467">**Information Fields**</span></span>

- <span data-ttu-id="65356-2468">정보 필드 1: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2468">Info Field 1: Device.</span></span>
- <span data-ttu-id="65356-2469">정보 필드 2: 구성</span><span class="sxs-lookup"><span data-stu-id="65356-2469">nfo Field 2: Configuration.</span></span>
- <span data-ttu-id="65356-2470">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2471">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2471">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-select"></a><span data-ttu-id="65356-2472">호스트 스택 디바이스 구성 선택</span><span class="sxs-lookup"><span data-stu-id="65356-2472">Host Stack Device Configuration Select</span></span> 

#### <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="65356-2473">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="65356-2473">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="65356-2474">**아이콘** ![호스트 스택 디바이스 구성 선택 아이콘](./media/user-guide/usbx-events/image194.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2474">**Icon** ![Host Stack Device Configuration Select icon](./media/user-guide/usbx-events/image194.png)</span></span>

<span data-ttu-id="65356-2475">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2475">**Description**</span></span>

<span data-ttu-id="65356-2476">이 이벤트는 USBX 호스트 스택 디바이스 구성 선택 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2476">This event represents a USBX Host Stack Device Configuration Select Event.</span></span>

<span data-ttu-id="65356-2477">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2477">**Information Fields**</span></span>

- <span data-ttu-id="65356-2478">정보 필드 1: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2478">Info Field 1: Device.</span></span>
- <span data-ttu-id="65356-2479">정보 필드 2: 구성</span><span class="sxs-lookup"><span data-stu-id="65356-2479">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="65356-2480">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2481">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2481">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-descriptor-read"></a><span data-ttu-id="65356-2482">호스트 스택 디바이스 설명자 읽기</span><span class="sxs-lookup"><span data-stu-id="65356-2482">Host Stack Device Descriptor Read</span></span> 

#### <a name="ux_host_stack_device_descriptor_read"></a><span data-ttu-id="65356-2483">ux_host_stack_device_descriptor_read</span><span class="sxs-lookup"><span data-stu-id="65356-2483">ux_host_stack_device_descriptor_read</span></span>

<span data-ttu-id="65356-2484">**아이콘** ![호스트 스택 디바이스 설명자 읽기 아이콘](./media/user-guide/usbx-events/image195.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2484">**Icon** ![Host Stack Device Descriptor Read icon](./media/user-guide/usbx-events/image195.png)</span></span>

<span data-ttu-id="65356-2485">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2485">**Description**</span></span>

<span data-ttu-id="65356-2486">이 이벤트는 USBX 호스트 스택 디바이스 설명자 읽기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2486">This event represents a USBX Host Stack Device Descriptor Read Event.</span></span>

<span data-ttu-id="65356-2487">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2487">**Information Fields**</span></span>

- <span data-ttu-id="65356-2488">정보 필드 1: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2488">Info Field 1: Device.</span></span>
- <span data-ttu-id="65356-2489">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2489">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2490">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2491">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2491">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-get"></a><span data-ttu-id="65356-2492">호스트 스택 디바이스 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-2492">Host Stack Device Get</span></span> 

#### <a name="ux_host_stack_device_get"></a><span data-ttu-id="65356-2493">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="65356-2493">ux_host_stack_device_get</span></span>

<span data-ttu-id="65356-2494">**아이콘** ![호스트 스택 디바이스 가져오기 아이콘](./media/user-guide/usbx-events/image196.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2494">**Icon** ![Host Stack Device Get icon](./media/user-guide/usbx-events/image196.png)</span></span>

<span data-ttu-id="65356-2495">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2495">**Description**</span></span>

<span data-ttu-id="65356-2496">이 이벤트는 USBX 호스트 스택 디바이스 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2496">This event represents a USBX Host Stack Device Get Event.</span></span>

<span data-ttu-id="65356-2497">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2497">**Information Fields**</span></span>

- <span data-ttu-id="65356-2498">정보 필드 1: 디바이스 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-2498">Info Field 1: Device index.</span></span>
- <span data-ttu-id="65356-2499">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2499">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2500">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2501">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2501">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-remove"></a><span data-ttu-id="65356-2502">호스트 스택 디바이스 제거</span><span class="sxs-lookup"><span data-stu-id="65356-2502">Host Stack Device Remove</span></span> 

#### <a name="ux_host_stack_device_remove"></a><span data-ttu-id="65356-2503">ux_host_stack_device_remove</span><span class="sxs-lookup"><span data-stu-id="65356-2503">ux_host_stack_device_remove</span></span>

<span data-ttu-id="65356-2504">**아이콘** ![호스트 스택 디바이스 제거 아이콘](./media/user-guide/usbx-events/image197.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2504">**Icon** ![Host Stack Device Remove icon](./media/user-guide/usbx-events/image197.png)</span></span>

<span data-ttu-id="65356-2505">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2505">**Description**</span></span>

<span data-ttu-id="65356-2506">이 이벤트는 USBX 호스트 스택 디바이스 제거 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2506">This event represents a USBX Host Stack Device Remove Event.</span></span>

<span data-ttu-id="65356-2507">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2507">**Information Fields**</span></span>

- <span data-ttu-id="65356-2508">정보 필드 1: Hcd</span><span class="sxs-lookup"><span data-stu-id="65356-2508">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="65356-2509">정보 필드 2: 부모 항목</span><span class="sxs-lookup"><span data-stu-id="65356-2509">Info Field 2: Parent.</span></span>
- <span data-ttu-id="65356-2510">정보 필드 3: 포트 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-2510">Info Field 3: Port Index.</span></span>
- <span data-ttu-id="65356-2511">정보 필드 4: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2511">Info Field 4: Device.</span></span>

### <a name="host-stack-device-resource-free"></a><span data-ttu-id="65356-2512">호스트 스택 디바이스 리소스 해제</span><span class="sxs-lookup"><span data-stu-id="65356-2512">Host Stack Device Resource Free</span></span> 

#### <a name="ux_host_stack_device_resource_free"></a><span data-ttu-id="65356-2513">ux_host_stack_device_resource_free</span><span class="sxs-lookup"><span data-stu-id="65356-2513">ux_host_stack_device_resource_free</span></span>

<span data-ttu-id="65356-2514">**아이콘** ![호스트 스택 디바이스 리소스 해제 아이콘](./media/user-guide/usbx-events/image198.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2514">**Icon** ![Host Stack Device Resource Free icon](./media/user-guide/usbx-events/image198.png)</span></span>

<span data-ttu-id="65356-2515">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2515">**Description**</span></span>

<span data-ttu-id="65356-2516">이 이벤트는 USBX 호스트 스택 디바이스 리소스 해제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2516">This event represents a USBX Host Stack Device Resource Free Event.</span></span>

<span data-ttu-id="65356-2517">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2517">**Information Fields**</span></span>

- <span data-ttu-id="65356-2518">정보 필드 1: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2518">Info Field 1: Device.</span></span>
- <span data-ttu-id="65356-2519">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2520">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2521">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2521">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-create"></a><span data-ttu-id="65356-2522">호스트 스택 엔드포인트 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="65356-2522">Host Stack Endpoint Instance Create</span></span> 

#### <a name="ux_host_stack_endpoint_instance_create"></a><span data-ttu-id="65356-2523">ux_host_stack_endpoint_instance_create</span><span class="sxs-lookup"><span data-stu-id="65356-2523">ux_host_stack_endpoint_instance_create</span></span>

<span data-ttu-id="65356-2524">**아이콘** ![호스트 스택 엔드포인트 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image199.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2524">**Icon** ![Host Stack Endpoint Instance Create icon](./media/user-guide/usbx-events/image199.png)</span></span>

<span data-ttu-id="65356-2525">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2525">**Description**</span></span>

<span data-ttu-id="65356-2526">이 이벤트는 USBX 호스트 스택 엔드포인트 인스턴스 만들기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2526">This event represents a USBX Host Stack Endpoint Instance Create Event.</span></span>

<span data-ttu-id="65356-2527">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2527">**Information Fields**</span></span>

- <span data-ttu-id="65356-2528">정보 필드 1: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2528">Info Field 1: Device.</span></span>
- <span data-ttu-id="65356-2529">정보 필드 2: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-2529">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="65356-2530">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2531">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2531">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-delete"></a><span data-ttu-id="65356-2532">호스트 스택 엔드포인트 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="65356-2532">Host Stack Endpoint Instance Delete</span></span> 

#### <a name="ux_host_stack_endpoint_instance_delete"></a><span data-ttu-id="65356-2533">ux_host_stack_endpoint_instance_delete</span><span class="sxs-lookup"><span data-stu-id="65356-2533">ux_host_stack_endpoint_instance_delete</span></span>

<span data-ttu-id="65356-2534">**아이콘** ![호스트 스택 엔드포인트 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image200.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2534">**Icon** ![Host Stack Endpoint Instance Delete icon](./media/user-guide/usbx-events/image200.png)</span></span>

<span data-ttu-id="65356-2535">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2535">**Description**</span></span>

<span data-ttu-id="65356-2536">이 이벤트는 USBX 호스트 스택 엔드포인트 인스턴스 삭제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2536">This event represents a USBX Host Stack Endpoint Instance Delete Event.</span></span>

<span data-ttu-id="65356-2537">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2537">**Information Fields**</span></span>

- <span data-ttu-id="65356-2538">정보 필드 2: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-2538">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="65356-2539">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2539">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2540">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2540">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-reset"></a><span data-ttu-id="65356-2541">호스트 스택 엔드포인트 재설정</span><span class="sxs-lookup"><span data-stu-id="65356-2541">Host Stack Endpoint Reset</span></span> 

#### <a name="ux_host_stack_endpoint_reset"></a><span data-ttu-id="65356-2542">ux_host_stack_endpoint_reset</span><span class="sxs-lookup"><span data-stu-id="65356-2542">ux_host_stack_endpoint_reset</span></span>

<span data-ttu-id="65356-2543">**아이콘** ![호스트 스택 엔드포인트 재설정 아이콘](./media/user-guide/usbx-events/image201.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2543">**Icon** ![Host Stack Endpoint Reset icon](./media/user-guide/usbx-events/image201.png)</span></span>

<span data-ttu-id="65356-2544">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2544">**Description**</span></span>

<span data-ttu-id="65356-2545">이 이벤트는 USBX 호스트 스택 엔드포인트 재설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2545">This event represents a USBX Host Stack Endpoint Reset Event.</span></span>

<span data-ttu-id="65356-2546">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2546">**Information Fields**</span></span>

- <span data-ttu-id="65356-2547">정보 필드 1: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2547">Info Field 1: Device.</span></span>
- <span data-ttu-id="65356-2548">정보 필드 2: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-2548">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="65356-2549">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2549">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2550">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2550">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-transfer-abort"></a><span data-ttu-id="65356-2551">호스트 스택 엔드포인트 전송 중단</span><span class="sxs-lookup"><span data-stu-id="65356-2551">Host Stack Endpoint Transfer Abort</span></span> 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="65356-2552">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="65356-2552">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="65356-2553">**아이콘** ![호스트 스택 엔드포인트 전송 중단 아이콘](./media/user-guide/usbx-events/image202.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2553">**Icon** ![Host Stack Endpoint Transfer Abort icon](./media/user-guide/usbx-events/image202.png)</span></span>

<span data-ttu-id="65356-2554">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2554">**Description**</span></span>

<span data-ttu-id="65356-2555">이 이벤트는 USBX 호스트 스택 엔드포인트 전송 중단 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2555">This event represents a USBX Host Stack Endpoint Transfer Abort Event.</span></span>

<span data-ttu-id="65356-2556">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2556">**Information Fields**</span></span>

- <span data-ttu-id="65356-2557">정보 필드 1: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-2557">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="65356-2558">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2558">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2559">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2559">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2560">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2560">Info Field 4: Not used.</span></span>

### <a name="host-stack-host-controller-register"></a><span data-ttu-id="65356-2561">호스트 스택 호스트 컨트롤러 등록</span><span class="sxs-lookup"><span data-stu-id="65356-2561">Host Stack Host Controller Register</span></span> 

#### <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="65356-2562">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="65356-2562">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="65356-2563">**아이콘** ![호스트 스택 호스트 컨트롤러 등록 아이콘](./media/user-guide/usbx-events/image203.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2563">**Icon** ![Host Stack Host Controller Register icon](./media/user-guide/usbx-events/image203.png)</span></span>

<span data-ttu-id="65356-2564">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2564">**Description**</span></span>

<span data-ttu-id="65356-2565">이 이벤트는 USBX 호스트 스택 호스트 컨트롤러 등록을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2565">This event represents a USBX Host Stack Host Controller Register.</span></span>

<span data-ttu-id="65356-2566">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2566">**Information Fields**</span></span>

- <span data-ttu-id="65356-2567">정보 필드 1: Hcd 이름</span><span class="sxs-lookup"><span data-stu-id="65356-2567">Info Field 1: Hcd Name.</span></span>
- <span data-ttu-id="65356-2568">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2568">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2569">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2569">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2570">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2570">Info Field 4: Not used.</span></span>

### <a name="host-stack-initialize"></a><span data-ttu-id="65356-2571">호스트 스택 초기화</span><span class="sxs-lookup"><span data-stu-id="65356-2571">Host Stack Initialize</span></span> 

#### <a name="ux_host_stack_initialize"></a><span data-ttu-id="65356-2572">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="65356-2572">ux_host_stack_initialize</span></span>

<span data-ttu-id="65356-2573">**아이콘** ![호스트 스택 초기화 아이콘](./media/user-guide/usbx-events/image204.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2573">**Icon** ![Host Stack Initialize icon](./media/user-guide/usbx-events/image204.png)</span></span>

<span data-ttu-id="65356-2574">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2574">**Description**</span></span>

<span data-ttu-id="65356-2575">이 이벤트는 USBX 호스트 스택 초기화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2575">This event represents a USBX Host Stack Initialize Event.</span></span>

<span data-ttu-id="65356-2576">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2576">**Information Fields**</span></span>

- <span data-ttu-id="65356-2577">정보 필드 1: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2577">Info Field 1: Not used.</span></span>
- <span data-ttu-id="65356-2578">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2578">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2579">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2579">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2580">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2580">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-endpoint-get"></a><span data-ttu-id="65356-2581">호스트 스택 인터페이스 엔드포인트 가져오기</span><span class="sxs-lookup"><span data-stu-id="65356-2581">Host Stack Interface Endpoint Get</span></span> 

#### <a name="interface_-tcp-retry-entry"></a><span data-ttu-id="65356-2582">인터페이스 TCP 다시 시도 항목</span><span class="sxs-lookup"><span data-stu-id="65356-2582">Interface_ TCP retry entry</span></span>

<span data-ttu-id="65356-2583">**아이콘** ![호스트 스택 인터페이스 엔드포인트 가져오기 아이콘](./media/user-guide/usbx-events/image205.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2583">**Icon** ![Host Stack Interface Endpoint Get icon](./media/user-guide/usbx-events/image205.png)</span></span>

<span data-ttu-id="65356-2584">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2584">**Description**</span></span>

<span data-ttu-id="65356-2585">이 이벤트는 내부 NetX TCP 다시 시도 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2585">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="65356-2586">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2586">**Information Fields**</span></span>

- <span data-ttu-id="65356-2587">정보 필드 1: 인터페이스</span><span class="sxs-lookup"><span data-stu-id="65356-2587">Info Field 1: Interface.</span></span>
- <span data-ttu-id="65356-2588">정보 필드 2: 엔드포인트 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-2588">Info Field 2: Endpoint index.</span></span>
- <span data-ttu-id="65356-2589">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2589">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2590">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2590">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-create"></a><span data-ttu-id="65356-2591">호스트 스택 인터페이스 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="65356-2591">Host Stack Interface Instance Create</span></span> 

#### <a name="ux_host_stack_interface_instance_create"></a><span data-ttu-id="65356-2592">ux_host_stack_interface_instance_create</span><span class="sxs-lookup"><span data-stu-id="65356-2592">ux_host_stack_interface_instance_create</span></span>

<span data-ttu-id="65356-2593">**아이콘** ![호스트 스택 인터페이스 인스턴스 만들기 아이콘](./media/user-guide/usbx-events/image206.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2593">**Icon** ![Host Stack Interface Instance Create icon](./media/user-guide/usbx-events/image206.png)</span></span>

<span data-ttu-id="65356-2594">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2594">**Description**</span></span>

<span data-ttu-id="65356-2595">이 이벤트는 USBX 호스트 스택 인터페이스 인스턴스 만들기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2595">This event represents a USBX Host Stack Interface Instance Create Event.</span></span>

<span data-ttu-id="65356-2596">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2596">**Information Fields**</span></span>

- <span data-ttu-id="65356-2597">정보 필드 1: 인터페이스</span><span class="sxs-lookup"><span data-stu-id="65356-2597">Info Field 1: Interface.</span></span>
- <span data-ttu-id="65356-2598">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2598">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2599">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2599">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2600">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2600">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-delete"></a><span data-ttu-id="65356-2601">호스트 스택 인터페이스 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="65356-2601">Host Stack Interface Instance Delete</span></span> 

#### <a name="ux_host_stack_interface_instance_delete"></a><span data-ttu-id="65356-2602">ux_host_stack_interface_instance_delete</span><span class="sxs-lookup"><span data-stu-id="65356-2602">ux_host_stack_interface_instance_delete</span></span>

<span data-ttu-id="65356-2603">**아이콘** ![호스트 스택 인터페이스 인스턴스 삭제 아이콘](./media/user-guide/usbx-events/image207.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2603">**Icon** ![Host Stack Interface Instance Delete icon](./media/user-guide/usbx-events/image207.png)</span></span>

<span data-ttu-id="65356-2604">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2604">**Description**</span></span>

<span data-ttu-id="65356-2605">이 이벤트는 USBX 호스트 스택 인터페이스 인스턴스 삭제 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2605">This event represents a USBX Host Stack Interface Instance Delete Event.</span></span>

<span data-ttu-id="65356-2606">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2606">**Information Fields**</span></span>

- <span data-ttu-id="65356-2607">정보 필드 1: 인터페이스</span><span class="sxs-lookup"><span data-stu-id="65356-2607">Info Field 1: Interface.</span></span>
- <span data-ttu-id="65356-2608">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2608">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2609">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2609">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2610">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2610">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-set"></a><span data-ttu-id="65356-2611">호스트 스택 인터페이스 설정</span><span class="sxs-lookup"><span data-stu-id="65356-2611">Host Stack Interface Set</span></span> 

#### <a name="ux_host_stack_interface_set"></a><span data-ttu-id="65356-2612">ux_host_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="65356-2612">ux_host_stack_interface_set</span></span>

<span data-ttu-id="65356-2613">**아이콘** ![호스트 스택 인터페이스 설정 아이콘](./media/user-guide/usbx-events/image208.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2613">**Icon** ![Host Stack Interface Set icon](./media/user-guide/usbx-events/image208.png)</span></span>

<span data-ttu-id="65356-2614">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2614">**Description**</span></span>

<span data-ttu-id="65356-2615">이 이벤트는 USBX 호스트 스택 인터페이스 설정 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2615">This event represents a USBX Host Stack Interface Set Event.</span></span>

<span data-ttu-id="65356-2616">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2616">**Information Fields**</span></span>

- <span data-ttu-id="65356-2617">정보 필드 1: 인터페이스</span><span class="sxs-lookup"><span data-stu-id="65356-2617">Info Field 1: Interface.</span></span>
- <span data-ttu-id="65356-2618">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2618">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2619">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2619">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2620">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2620">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-setting-select"></a><span data-ttu-id="65356-2621">호스트 스탭 인터페이스 설정 선택</span><span class="sxs-lookup"><span data-stu-id="65356-2621">Host Stack Interface Setting Select</span></span> 

#### <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="65356-2622">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="65356-2622">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="65356-2623">**아이콘** ![호스트 스택 인터페이스 설정 선택 아이콘](./media/user-guide/usbx-events/image209.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2623">**Icon** ![Host Stack Interface Setting Select icon](./media/user-guide/usbx-events/image209.png)</span></span>

<span data-ttu-id="65356-2624">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2624">**Description**</span></span>

<span data-ttu-id="65356-2625">이 이벤트는 USBX 호스트 스택 인터페이스 설정 선택 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2625">This event represents a USBX Host Stack Interface Setting Select Event.</span></span>

<span data-ttu-id="65356-2626">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2626">**Information Fields**</span></span>

- <span data-ttu-id="65356-2627">정보 필드 1: 인터페이스</span><span class="sxs-lookup"><span data-stu-id="65356-2627">Info Field 1: Interface.</span></span>
- <span data-ttu-id="65356-2628">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2628">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2629">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2629">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2630">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2630">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-configuration-create"></a><span data-ttu-id="65356-2631">호스트 스택 새 구성 만들기</span><span class="sxs-lookup"><span data-stu-id="65356-2631">Host Stack New Configuration Create</span></span> 

#### <a name="ux_host_stack_new_configuration_create"></a><span data-ttu-id="65356-2632">ux_host_stack_new_configuration_create</span><span class="sxs-lookup"><span data-stu-id="65356-2632">ux_host_stack_new_configuration_create</span></span>

<span data-ttu-id="65356-2633">**아이콘** ![호스트 스택 새 구성 만들기 아이콘](./media/user-guide/usbx-events/image210.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2633">**Icon** ![Host Stack New Configuration Create icon](./media/user-guide/usbx-events/image210.png)</span></span>

<span data-ttu-id="65356-2634">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2634">**Description**</span></span>
 
<span data-ttu-id="65356-2635">이 이벤트는 USBX 호스트 스택 새 구성 만들기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2635">This event represents a USBX Host Stack New Configuration Create Event.</span></span>

<span data-ttu-id="65356-2636">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2636">**Information Fields**</span></span>

- <span data-ttu-id="65356-2637">정보 필드 1: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2637">Info Field 1: Device.</span></span>
- <span data-ttu-id="65356-2638">정보 필드 2: 구성</span><span class="sxs-lookup"><span data-stu-id="65356-2638">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="65356-2639">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2639">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2640">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2640">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-device-create"></a><span data-ttu-id="65356-2641">호스트 스택 새 디바이스 만들기</span><span class="sxs-lookup"><span data-stu-id="65356-2641">Host Stack New Device Create</span></span> 

#### <a name="ux_host_stack_new_device_create"></a><span data-ttu-id="65356-2642">ux_host_stack_new_device_create</span><span class="sxs-lookup"><span data-stu-id="65356-2642">ux_host_stack_new_device_create</span></span>

<span data-ttu-id="65356-2643">**아이콘** ![호스트 스택 새 디바이스 만들기 아이콘](./media/user-guide/usbx-events/image211.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2643">**Icon** ![Host Stack New Device Create icon](./media/user-guide/usbx-events/image211.png)</span></span>

<span data-ttu-id="65356-2644">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2644">**Description**</span></span>
 
 <span data-ttu-id="65356-2645">이 이벤트는 USBX 호스트 스택 새 디바이스 만들기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2645">This event represents a USBX Host Stack New Device Create Event.</span></span>

<span data-ttu-id="65356-2646">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2646">**Information Fields**</span></span>

- <span data-ttu-id="65356-2647">정보 필드 1: Hcd</span><span class="sxs-lookup"><span data-stu-id="65356-2647">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="65356-2648">정보 필드 2: 디바이스 소유자</span><span class="sxs-lookup"><span data-stu-id="65356-2648">Info Field 2: Device owner.</span></span>
- <span data-ttu-id="65356-2649">정보 필드 3: 포트 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-2649">Info Field 3: Port index.</span></span>
- <span data-ttu-id="65356-2650">정보 필드 4: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2650">Info Field 4: Device.</span></span>

### <a name="host-stack-new-endpoint-create"></a><span data-ttu-id="65356-2651">호스트 스택 새 엔드포인트 만들기</span><span class="sxs-lookup"><span data-stu-id="65356-2651">Host Stack New Endpoint Create</span></span> 

#### <a name="ux_host_stack_new_endpoint_create"></a><span data-ttu-id="65356-2652">ux_host_stack_new_endpoint_create</span><span class="sxs-lookup"><span data-stu-id="65356-2652">ux_host_stack_new_endpoint_create</span></span>

<span data-ttu-id="65356-2653">**아이콘** ![호스트 스택 새 엔드포인트 만들기 아이콘](./media/user-guide/usbx-events/image212.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2653">**Icon** ![Host Stack New Endpoint Create icon](./media/user-guide/usbx-events/image212.png)</span></span>

<span data-ttu-id="65356-2654">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2654">**Description**</span></span>
 
<span data-ttu-id="65356-2655">이 이벤트는 USBX 호스트 스택 새 엔드포인트 만들기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2655">This event represents a USBX Host Stack New Endpoint Create Event.</span></span>

<span data-ttu-id="65356-2656">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2656">**Information Fields**</span></span>

- <span data-ttu-id="65356-2657">정보 필드 1: 인터페이스</span><span class="sxs-lookup"><span data-stu-id="65356-2657">Info Field 1: Interface.</span></span>
- <span data-ttu-id="65356-2658">정보 필드 2: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-2658">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="65356-2659">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2659">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2660">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2660">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-change-process"></a><span data-ttu-id="65356-2661">호스트 스택 루트 허브 변경 프로세스</span><span class="sxs-lookup"><span data-stu-id="65356-2661">Host Stack Root Hub Change Process</span></span> 

#### <a name="ux_host_stack_rh_change_process"></a><span data-ttu-id="65356-2662">ux_host_stack_rh_change_process</span><span class="sxs-lookup"><span data-stu-id="65356-2662">ux_host_stack_rh_change_process</span></span>

<span data-ttu-id="65356-2663">**아이콘** ![호스트 스택 루트 허브 변경 프로세스 아이콘](./media/user-guide/usbx-events/image213.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2663">**Icon** ![Host Stack Root Hub Change Process icon](./media/user-guide/usbx-events/image213.png)</span></span>

<span data-ttu-id="65356-2664">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2664">**Description**</span></span>
 
<span data-ttu-id="65356-2665">이 이벤트는 USBX 호스트 스택 루트 허브 변경 프로세스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2665">This event represents a USBX Host Stack Root Hub Change Process.</span></span>

<span data-ttu-id="65356-2666">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2666">**Information Fields**</span></span>

- <span data-ttu-id="65356-2667">정보 필드 1: 포트 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-2667">Info Field 1: Port index.</span></span>
- <span data-ttu-id="65356-2668">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2668">Info Field 2: Not used.</span></span>
- <span data-ttu-id="65356-2669">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2669">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2670">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2670">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-extraction"></a><span data-ttu-id="65356-2671">호스트 스택 루트 허브 디바이스 추출</span><span class="sxs-lookup"><span data-stu-id="65356-2671">Host Stack Root Hub Device Extraction</span></span> 

#### <a name="ux_host_stack_rh_device_extraction"></a><span data-ttu-id="65356-2672">ux_host_stack_rh_device_extraction</span><span class="sxs-lookup"><span data-stu-id="65356-2672">ux_host_stack_rh_device_extraction</span></span>

<span data-ttu-id="65356-2673">**아이콘** ![호스트 스택 루트 허브 디바이스 추출 아이콘](./media/user-guide/usbx-events/image214.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2673">**Icon** ![Host Stack Root Hub Device Extraction icon](./media/user-guide/usbx-events/image214.png)</span></span>

<span data-ttu-id="65356-2674">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2674">**Description**</span></span>

<span data-ttu-id="65356-2675">이 이벤트는 USBX 호스트 스택 루트 허브 디바이스 추출 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2675">This event represents a USBX Host Stack Root Hub Device Extraction Event.</span></span>

<span data-ttu-id="65356-2676">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2676">**Information Fields**</span></span>

- <span data-ttu-id="65356-2677">정보 필드 1: Hcd</span><span class="sxs-lookup"><span data-stu-id="65356-2677">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="65356-2678">정보 필드 2: 포트 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-2678">Info Field 2: Port index.</span></span>
- <span data-ttu-id="65356-2679">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2679">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2680">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2680">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-insertion"></a><span data-ttu-id="65356-2681">호스트 스택 루트 허브 디바이스 삽입</span><span class="sxs-lookup"><span data-stu-id="65356-2681">Host Stack Root Hub Device Insertion</span></span> 

#### <a name="ux_host_stack_rh_device_insertion"></a><span data-ttu-id="65356-2682">ux_host_stack_rh_device_insertion</span><span class="sxs-lookup"><span data-stu-id="65356-2682">ux_host_stack_rh_device_insertion</span></span>

<span data-ttu-id="65356-2683">**아이콘** ![호스트 스택 루트 허브 디바이스 삽입 아이콘](./media/user-guide/usbx-events/image215.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2683">**Icon** ![Host Stack Root Hub Device Insertion icon](./media/user-guide/usbx-events/image215.png)</span></span>

<span data-ttu-id="65356-2684">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2684">**Description**</span></span>

<span data-ttu-id="65356-2685">이 이벤트는 USBX 호스트 스택 루트 허브 디바이스 삽입을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2685">This event represents a USBX Host Stack Root Hub Device Insertion.</span></span>

<span data-ttu-id="65356-2686">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2686">**Information Fields**</span></span>

- <span data-ttu-id="65356-2687">정보 필드 1: Hcd</span><span class="sxs-lookup"><span data-stu-id="65356-2687">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="65356-2688">정보 필드 2: 포트 인덱스</span><span class="sxs-lookup"><span data-stu-id="65356-2688">Info Field 2: Port index.</span></span>
- <span data-ttu-id="65356-2689">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2689">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2690">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2690">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request"></a><span data-ttu-id="65356-2691">호스트 스택 전송 요청</span><span class="sxs-lookup"><span data-stu-id="65356-2691">Host Stack Transfer Request</span></span> 

#### <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="65356-2692">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="65356-2692">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="65356-2693">**아이콘** ![호스트 스택 전송 요청 아이콘](./media/user-guide/usbx-events/image216.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2693">**Icon** ![Host Stack Transfer Request icon](./media/user-guide/usbx-events/image216.png)</span></span>

<span data-ttu-id="65356-2694">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2694">**Description**</span></span>

<span data-ttu-id="65356-2695">이 이벤트는 USBX 호스트 스택 전송 요청을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2695">This event represents a USBX Host Stack Transfer Request.</span></span>

<span data-ttu-id="65356-2696">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2696">**Information Fields**</span></span>

- <span data-ttu-id="65356-2697">정보 필드 1: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2697">Info Field 1: Device.</span></span>
- <span data-ttu-id="65356-2698">정보 필드 2: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-2698">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="65356-2699">정보 필드 3: 전송 요청</span><span class="sxs-lookup"><span data-stu-id="65356-2699">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="65356-2700">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2700">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request-abort"></a><span data-ttu-id="65356-2701">호스트 스택 전송 요청 중단</span><span class="sxs-lookup"><span data-stu-id="65356-2701">Host Stack Transfer Request Abort</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="65356-2702">내부 I/O 드라이버 가져오기 상태</span><span class="sxs-lookup"><span data-stu-id="65356-2702">Internal I/O driver get status</span></span>

<span data-ttu-id="65356-2703">**아이콘** ![호스트 스택 전송 요청 중단 아이콘](./media/user-guide/usbx-events/image217.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2703">**Icon** ![Host Stack Transfer Request Abort icon](./media/user-guide/usbx-events/image217.png)</span></span>

<span data-ttu-id="65356-2704">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2704">**Description**</span></span>

<span data-ttu-id="65356-2705">이 이벤트는 USBX 호스트 스택 전송 요청 중단을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2705">This event represents a USBX Host Stack Transfer Request Abort.</span></span>

<span data-ttu-id="65356-2706">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2706">**Information Fields**</span></span>

- <span data-ttu-id="65356-2707">정보 필드 1: 디바이스</span><span class="sxs-lookup"><span data-stu-id="65356-2707">Info Field 1: Device.</span></span>
- <span data-ttu-id="65356-2708">정보 필드 2: 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="65356-2708">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="65356-2709">정보 필드 3: 전송 요청</span><span class="sxs-lookup"><span data-stu-id="65356-2709">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="65356-2710">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2710">Info Field 4: Not used.</span></span>

### <a name="usbx-error"></a><span data-ttu-id="65356-2711">USBX 오류</span><span class="sxs-lookup"><span data-stu-id="65356-2711">USBX Error</span></span> 

#### <a name="ux_error"></a><span data-ttu-id="65356-2712">ux_error</span><span class="sxs-lookup"><span data-stu-id="65356-2712">ux_error</span></span>

<span data-ttu-id="65356-2713">**아이콘** ![U S B X 오류 아이콘](./media/user-guide/usbx-events/image218.png)</span><span class="sxs-lookup"><span data-stu-id="65356-2713">**Icon** ![U S B X Error icon](./media/user-guide/usbx-events/image218.png)</span></span>

<span data-ttu-id="65356-2714">**설명**</span><span class="sxs-lookup"><span data-stu-id="65356-2714">**Description**</span></span>

<span data-ttu-id="65356-2715">이 이벤트는 USBX 오류 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2715">This event represents a USBX Error Event.</span></span>

<span data-ttu-id="65356-2716">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="65356-2716">**Information Fields**</span></span>

- <span data-ttu-id="65356-2717">정보 필드 1: USBX 오류</span><span class="sxs-lookup"><span data-stu-id="65356-2717">Info Field 1: USBX error.</span></span>
- <span data-ttu-id="65356-2718">정보 필드 2: 오류 이름</span><span class="sxs-lookup"><span data-stu-id="65356-2718">Info Field 2: Error Name.</span></span>
- <span data-ttu-id="65356-2719">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2719">Info Field 3: Not used.</span></span>
- <span data-ttu-id="65356-2720">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65356-2720">Info Field 4: Not used.</span></span>