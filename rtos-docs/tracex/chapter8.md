---
title: 8장 - Azure RTOS NetX 추적 이벤트
description: 이 장에서는 Azure RTOS NetX 이벤트에 대한 설명을 다룹니다.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: ce355d86d7db0b7e259ae58e306d990277b77a8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813170"
---
# <a name="chapter-8---azure-rtos-netx-trace-events"></a><span data-ttu-id="11190-103">8장 - Azure RTOS NetX 추적 이벤트</span><span class="sxs-lookup"><span data-stu-id="11190-103">Chapter 8 - Azure RTOS NetX trace events</span></span>

<span data-ttu-id="11190-104">이 장에서는 Azure RTOS NetX 이벤트에 대한 설명을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="11190-104">This chapter contains a description of the Azure RTOS NetX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="11190-105">이벤트 및 아이콘 목록</span><span class="sxs-lookup"><span data-stu-id="11190-105">List of Events and Icons</span></span>

<span data-ttu-id="11190-106">다음은 TraceX에 의해 표시되는 NetX 이벤트 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-106">The following is a list of NetX events displayed by TraceX.</span></span>

| <span data-ttu-id="11190-107">아이콘</span><span class="sxs-lookup"><span data-stu-id="11190-107">Icon</span></span>                                           | <span data-ttu-id="11190-108">의미</span><span class="sxs-lookup"><span data-stu-id="11190-108">Meaning</span></span>                 |
| -------------------------------- | ------------------------------------- |
| ![내부 ARP 요청 수신 아이콘](./media/user-guide/netx-events/image1.png)    | <span data-ttu-id="11190-110">내부 ARP 요청 수신</span><span class="sxs-lookup"><span data-stu-id="11190-110">Internal ARP Request Receive</span></span> |
| ![내부 ARP 요청 송신 아이콘](./media/user-guide/netx-events/image2.png)    | <span data-ttu-id="11190-112">내부 ARP 요청 송신</span><span class="sxs-lookup"><span data-stu-id="11190-112">Internal ARP Request Send</span></span> |
| ![내부 ARP 응답 수신 아이콘](./media/user-guide/netx-events/image3.png)    | <span data-ttu-id="11190-114">내부 ARP 응답 수신</span><span class="sxs-lookup"><span data-stu-id="11190-114">Internal ARP Response Receive</span></span> |
| ![내부 ARP 응답 송신 아이콘](./media/user-guide/netx-events/image4.png)    | <span data-ttu-id="11190-116">내부 ARP 응답 송신</span><span class="sxs-lookup"><span data-stu-id="11190-116">Internal ARP Response Send</span></span> |
| ![내부 ICMP 수신 아이콘](./media/user-guide/netx-events/image5.png)    | <span data-ttu-id="11190-118">내부 ICMP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-118">Internal ICMP Receive</span></span> |
| ![내부 ICMP 송신 아이콘](./media/user-guide/netx-events/image6.png)    | <span data-ttu-id="11190-120">내부 ICMP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-120">Internal ICMP Send</span></span> |
| ![내부 NetX IGMP 수신 아이콘](./media/user-guide/netx-events/image7.png)    | <span data-ttu-id="11190-122">내부 NetX IGMP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-122">Internal NetX IGMP Receive</span></span> |
| ![내부 IP 수신 아이콘](./media/user-guide/netx-events/image8.png)    | <span data-ttu-id="11190-124">내부 IP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-124">Internal IP Receive</span></span> |
| ![내부 IP 송신 아이콘](./media/user-guide/netx-events/image9.png)    | <span data-ttu-id="11190-126">내부 IP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-126">Internal IP Send</span></span> |
| ![내부 TCP 데이터 수신 아이콘](./media/user-guide/netx-events/image10.png)    | <span data-ttu-id="11190-128">내부 TCP 데이터 수신</span><span class="sxs-lookup"><span data-stu-id="11190-128">Internal TCP Data Receive</span></span> |
| ![내부 TCP 데이터 송신 아이콘](./media/user-guide/netx-events/image11.png)    | <span data-ttu-id="11190-130">내부 TCP 데이터 송신</span><span class="sxs-lookup"><span data-stu-id="11190-130">Internal TCP Data Send</span></span> |
| ![내부 TCP FIN 수신 아이콘](./media/user-guide/netx-events/image12.png)    | <span data-ttu-id="11190-132">내부 TCP FIN 수신</span><span class="sxs-lookup"><span data-stu-id="11190-132">Internal TCP FIN Receive</span></span> |
| ![내부 TCP FIN 송신 아이콘](./media/user-guide/netx-events/image13.png)    | <span data-ttu-id="11190-134">내부 TCP FIN 송신</span><span class="sxs-lookup"><span data-stu-id="11190-134">Internal TCP FIN Send</span></span> |
| ![내부 TCP RST 수신 아이콘](./media/user-guide/netx-events/image14.png)    | <span data-ttu-id="11190-136">내부 TCP RST 수신</span><span class="sxs-lookup"><span data-stu-id="11190-136">Internal TCP RST Receive</span></span> |
| ![내부 TCP RST 송신 아이콘](./media/user-guide/netx-events/image15.png)    | <span data-ttu-id="11190-138">내부 TCP RST 송신</span><span class="sxs-lookup"><span data-stu-id="11190-138">Internal TCP RST Send</span></span> |
| ![내부 TCP SYN 수신 아이콘](./media/user-guide/netx-events/image16.png)    | <span data-ttu-id="11190-140">내부 TCP SYN 수신</span><span class="sxs-lookup"><span data-stu-id="11190-140">Internal TCP SYN Receive</span></span> |
| ![내부 TCP SYN 송신 아이콘](./media/user-guide/netx-events/image17.png)    | <span data-ttu-id="11190-142">내부 TCP SYN 송신</span><span class="sxs-lookup"><span data-stu-id="11190-142">Internal TCP SYN Send</span></span> |
| ![내부 UDP 수신 아이콘](./media/user-guide/netx-events/image18.png)    | <span data-ttu-id="11190-144">내부 UDP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-144">Internal UDP Receive</span></span> |
| ![내부 UDP 송신 아이콘](./media/user-guide/netx-events/image19.png)    | <span data-ttu-id="11190-146">내부 UDP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-146">Internal UDP Send</span></span> |
| ![내부 RARP 수신 아이콘](./media/user-guide/netx-events/image20.png)    | <span data-ttu-id="11190-148">내부 RARP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-148">Internal RARP Receive</span></span> |
| ![내부 RARP 송신 아이콘](./media/user-guide/netx-events/image21.png)    | <span data-ttu-id="11190-150">내부 RARP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-150">Internal RARP Send</span></span> |
| ![내부 TCP 다시 시도 아이콘](./media/user-guide/netx-events/image22.png)    | <span data-ttu-id="11190-152">내부 TCP 다시 시도</span><span class="sxs-lookup"><span data-stu-id="11190-152">Internal TCP Retry</span></span> |
| ![내부 TCP 상태 변경 아이콘](./media/user-guide/netx-events/image23.png)    | <span data-ttu-id="11190-154">내부 TCP 상태 변경</span><span class="sxs-lookup"><span data-stu-id="11190-154">Internal TCP State Change</span></span> |
| ![내부 I/O 드라이버 패킷 송신 아이콘](./media/user-guide/netx-events/image24.png)    | <span data-ttu-id="11190-156">내부 I/O 드라이버 패킷 송신</span><span class="sxs-lookup"><span data-stu-id="11190-156">Internal I/O Driver Packet Send</span></span> |
| ![icon](./media/user-guide/netx-events/image25.png)    | <span data-ttu-id="11190-158">내부 I/O 드라이버 초기화</span><span class="sxs-lookup"><span data-stu-id="11190-158">Internal I/O Driver Initialize</span></span> |
| ![내부 I/O 드라이버 초기화 아이콘](./media/user-guide/netx-events/image26.png)    | <span data-ttu-id="11190-160">내부 I/O 드라이버 링크 사용</span><span class="sxs-lookup"><span data-stu-id="11190-160">Internal I/O Driver Link Enable</span></span> |
| ![내부 I/O 드라이버 링크 사용 안 함 아이콘](./media/user-guide/netx-events/image27.png)    | <span data-ttu-id="11190-162">내부 I/O 드라이버 링크 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11190-162">Internal I/O Driver Link Disable</span></span> |
| ![내부 I/O 드라이버 패킷 브로드캐스트 아이콘](./media/user-guide/netx-events/image28.png)    | <span data-ttu-id="11190-164">내부 I/O 드라이버 패킷 브로드캐스트</span><span class="sxs-lookup"><span data-stu-id="11190-164">Internal I/O Driver Packet Broadcast</span></span> |
| ![내부 I/O 드라이버 ARP 송신 아이콘](./media/user-guide/netx-events/image29.png)    | <span data-ttu-id="11190-166">내부 I/O 드라이버 ARP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-166">Internal I/O Driver ARP Send</span></span> |
| ![내부 I/O 드라이버 ARP 응답 송신 아이콘](./media/user-guide/netx-events/image30.png)    | <span data-ttu-id="11190-168">내부 I/O 드라이버 ARP 응답 송신</span><span class="sxs-lookup"><span data-stu-id="11190-168">Internal I/O Driver ARP Response Send</span></span> |
| ![내부 I/O 드라이버 RARP 송신 아이콘](./media/user-guide/netx-events/image31.png)    | <span data-ttu-id="11190-170">내부 I/O 드라이버 RARP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-170">Internal I/O Driver RARP Send</span></span> |
| ![내부 I/O 드라이버 멀티캐스트 조인 아이콘](./media/user-guide/netx-events/image32.png)    | <span data-ttu-id="11190-172">내부 I/O 드라이버 멀티캐스트 조인</span><span class="sxs-lookup"><span data-stu-id="11190-172">Internal I/O Driver Multicast Join</span></span> |
| ![내부 I/O 드라이버 멀티캐스트 탈퇴 아이콘](./media/user-guide/netx-events/image33.png)    | <span data-ttu-id="11190-174">내부 I/O 드라이버 멀티캐스트 탈퇴</span><span class="sxs-lookup"><span data-stu-id="11190-174">Internal I/O Driver Multicast Leave</span></span> |
| ![내부 I/O 드라이버 상태 가져오기 아이콘](./media/user-guide/netx-events/image34.png)    | <span data-ttu-id="11190-176">내부 I/O 드라이버 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-176">Internal I/O Driver Get Status</span></span> |
| ![내부 I/O 드라이버 속도 가져오기 아이콘](./media/user-guide/netx-events/image35.png)    | <span data-ttu-id="11190-178">내부 I/O 드라이버 속도 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-178">Internal I/O Driver Get Speed</span></span> |
| ![내부 I/O 드라이버 이중 형식 가져오기 아이콘](./media/user-guide/netx-events/image36.png)    | <span data-ttu-id="11190-180">내부 I/O 드라이버 이중 형식 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-180">Internal I/O Driver Get Duplex Type</span></span> |
| ![내부 I/O 드라이버 오류 수 가져오기 아이콘](./media/user-guide/netx-events/image37.png)    | <span data-ttu-id="11190-182">내부 I/O 드라이버 오류 수 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-182">Internal I/O Driver Get Error Count</span></span> |
| ![내부 I/O 드라이버 RX 수 가져오기 아이콘](./media/user-guide/netx-events/image38.png)    | <span data-ttu-id="11190-184">내부 I/O 드라이버 RX 수 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-184">Internal I/O Driver Get RX Count</span></span> |
| ![내부 I/O 드라이버 TX 수 가져오기 아이콘](./media/user-guide/netx-events/image39.png)    | <span data-ttu-id="11190-186">내부 I/O 드라이버 TX 수 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-186">Internal I/O Driver Get TX Count</span></span> |
| ![내부 I/O 드라이버 할당 오류 가져오기 아이콘](./media/user-guide/netx-events/image40.png)    | <span data-ttu-id="11190-188">내부 I/O 드라이버 할당 오류 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-188">Internal I/O Driver Get Allocation Errors</span></span> |
| ![내부 I/O 드라이버 초기화 취소 아이콘](./media/user-guide/netx-events/image41.png)    | <span data-ttu-id="11190-190">내부 I/O 드라이버 초기화 취소</span><span class="sxs-lookup"><span data-stu-id="11190-190">Internal I/O Driver Un-initialize</span></span> |
| ![내부 I/O 드라이버 지연 처리 아이콘](./media/user-guide/netx-events/image42.png)    | <span data-ttu-id="11190-192">내부 I/O 드라이버 지연 처리</span><span class="sxs-lookup"><span data-stu-id="11190-192">Internal I/O Driver Deferred Processing</span></span> |
| ![ARP 동적 항목 무효화 아이콘](./media/user-guide/netx-events/image43.png)    | <span data-ttu-id="11190-194">**ARP 동적 항목 무효화**(nx_arp_dynamic_entries_invalidate)</span><span class="sxs-lookup"><span data-stu-id="11190-194">**ARP Dynamic Entries Invalidate** (*nx_arp_dynamic_entries_invalidate*)</span></span> |
| ![ARP 동적 항목 설정 아이콘](./media/user-guide/netx-events/image44.png)    | <span data-ttu-id="11190-196">**ARP 동적 항목 설정**(nx_arp_dynamic_entry_set)</span><span class="sxs-lookup"><span data-stu-id="11190-196">**ARP Dynamic Entry Set** (*nx_arp_dynamic_entry_set*)</span></span> |
| ![ARP 사용 아이콘](./media/user-guide/netx-events/image45.png)    | <span data-ttu-id="11190-198">**ARP 사용**(nx_arp_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-198">**ARP Enable** (*nx_arp_enable*)</span></span> |
| ![ARP 무상 송신 아이콘](./media/user-guide/netx-events/image46.png)    | <span data-ttu-id="11190-200">**ARP 무상 송신**(nx_arp_gratuitous_send)</span><span class="sxs-lookup"><span data-stu-id="11190-200">**ARP Gratuitous Send** (*nx_arp_gratuitous_send*)</span></span> |
| ![ARP 하드웨어 주소 찾기 아이콘](./media/user-guide/netx-events/image47.png)    | <span data-ttu-id="11190-202">**ARP 하드웨어 주소 찾기**(nx_arp_hardware_address_find)</span><span class="sxs-lookup"><span data-stu-id="11190-202">**ARP Hardware Address Find** (*nx_arp_hardware_address_find*)</span></span> |
| ![ARP 정보 가져오기 아이콘](./media/user-guide/netx-events/image48.png)    | <span data-ttu-id="11190-204">**ARP 정보 가져오기**(nx_arp_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-204">**ARP Information Get** (*nx_arp_info_get*)</span></span> |
| ![ARP IP 주소 찾기 아이콘](./media/user-guide/netx-events/image49.png)    | <span data-ttu-id="11190-206">**ARP IP 주소 찾기**(nx_arp_ip_address_find)</span><span class="sxs-lookup"><span data-stu-id="11190-206">**ARP IP Address Find** (*nx_arp_ip_address_find*)</span></span> |
| ![ARP 정적 항목 만들기 아이콘](./media/user-guide/netx-events/image50.png)    | <span data-ttu-id="11190-208">**ARP 정적 항목 만들기**(nx_arp_static_entry_create)</span><span class="sxs-lookup"><span data-stu-id="11190-208">**ARP Static Entry Create** (*nx_arp_static_entry_create*)</span></span> |
| ![ARP 정적 항목 삭제 아이콘](./media/user-guide/netx-events/image51.png)    | <span data-ttu-id="11190-210">**ARP 정적 항목 삭제**(nx_arp_static_entries_delete)</span><span class="sxs-lookup"><span data-stu-id="11190-210">**ARP Static Entries Delete** (*nx_arp_static_entries_delete*)</span></span> |
| ![ARP 정적 항목 삭제 아이콘](./media/user-guide/netx-events/image52.png)    | <span data-ttu-id="11190-212">**ARP 정적 항목 삭제**(nx_arp_static_entry_delete)</span><span class="sxs-lookup"><span data-stu-id="11190-212">**ARP Static Entry Delete** (*nx_arp_static_entry_delete*)</span></span> |
| ![Duo 캐시 항목 삭제 아이콘](./media/user-guide/netx-events/image53.png)    | <span data-ttu-id="11190-214">**Duo 캐시 항목 삭제**(nxd_nd_cache_entry_delete)</span><span class="sxs-lookup"><span data-stu-id="11190-214">**Duo Cache Entry Delete** (*nxd_nd_cache_entry_delete*)</span></span> |
| ![Duo 캐시 항목 설정 아이콘](./media/user-guide/netx-events/image54.png)    | <span data-ttu-id="11190-216">**Duo 캐시 항목 설정**(nxd_nd_cache_entry_set)</span><span class="sxs-lookup"><span data-stu-id="11190-216">**Duo Cache Entry Set** (*nxd_nd_cache_entry_set*)</span></span> |
| ![Duo 캐시 무효화 아이콘](./media/user-guide/netx-events/image55.png)    | <span data-ttu-id="11190-218">**Duo 캐시 무효화**(nxd_nd_cache_invalidate)</span><span class="sxs-lookup"><span data-stu-id="11190-218">**Duo Cache Invalidate** (*nxd_nd_cache_invalidate*)</span></span> |
| ![Duo 캐시 IP 주소 찾기 아이콘](./media/user-guide/netx-events/image56.png)    | <span data-ttu-id="11190-220">**Duo 캐시 IP 주소 찾기**(nxd_nd_cache_ip_address_find)</span><span class="sxs-lookup"><span data-stu-id="11190-220">**Duo Cache IP Address Find** (*nxd_nd_cache_ip_address_find*)</span></span> |
| ![DUO ICMP 사용 아이콘](./media/user-guide/netx-events/image57.png)    | <span data-ttu-id="11190-222">**DUO ICMP 사용**(nxd_icmp_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-222">**Duo ICMP Enable** (*nxd_icmp_enable*)</span></span> |
| ![DUO ICMP IPv6 Ping 아이콘](./media/user-guide/netx-events/image58.png)    | <span data-ttu-id="11190-224">**DUO ICMP IPv6 Ping**(nxd_icmp_ping)</span><span class="sxs-lookup"><span data-stu-id="11190-224">**Duo ICMP IPv6 Ping** (*nxd_icmp_ping*)</span></span> |
| ![Duo IP 최대 페이로드 크기 찾기 아이콘](./media/user-guide/netx-events/image59.png)    | <span data-ttu-id="11190-226">**DUO IP 최대 페이로드 크기 찾기**(nx_max_payload_size_find)</span><span class="sxs-lookup"><span data-stu-id="11190-226">**Duo IP Max Payload Size Find** (*nx_max_payload_size_find*)</span></span> |
| ![Duo IP 원시 패킷 송신 아이콘](./media/user-guide/netx-events/image60.png)    | <span data-ttu-id="11190-228">**DUO IP 원시 패킷 송신**(nxd_ip_raw_packet_send)</span><span class="sxs-lookup"><span data-stu-id="11190-228">**Duo IP Raw Packet Send** (*nxd_ip_raw_packet_send*)</span></span> |
| ![Duo IPv6 기본 라우터 추가 아이콘](./media/user-guide/netx-events/image61.png)    | <span data-ttu-id="11190-230">**Duo IPv6 기본 라우터 추가**(nxd_ipv6_default_router_add)</span><span class="sxs-lookup"><span data-stu-id="11190-230">**Duo IPv6 Default Router Add** (*nxd_ipv6_default_router_add*)</span></span> |
| ![Duo IPv6 기본 라우터 삭제 아이콘](./media/user-guide/netx-events/image62.png)    | <span data-ttu-id="11190-232">**Duo IPv6 기본 라우터 삭제**(nxd_ipv6_default_router_delete)</span><span class="sxs-lookup"><span data-stu-id="11190-232">**Duo IPv6 Default Router Delete** (*nxd_ipv6_default_router_delete)*</span></span> |
| ![Duo IPv6 사용 아이콘](./media/user-guide/netx-events/image63.png)    | <span data-ttu-id="11190-234">**Duo IPv6 사용**(nxd_ipv6_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-234">**Duo IPv6 Enable** (*nxd_ipv6_enable)*</span></span> |
| ![Duo IPv6 전체 주소 가져오기 아이콘](./media/user-guide/netx-events/image64.png)    | <span data-ttu-id="11190-236">**Duo IPv6 전체 주소 가져오기**(nxd_ipv6_global_address_get)</span><span class="sxs-lookup"><span data-stu-id="11190-236">**Duo IPv6 Global Address Get** (*nxd_ipv6_global_address_get*)</span></span> |
| ![Duo IPv6 전체 주소 설정 아이콘](./media/user-guide/netx-events/image65.png)    | <span data-ttu-id="11190-238">**Duo IPv6 전체 주소 설정**(nxd_ipv6_global_address_set)</span><span class="sxs-lookup"><span data-stu-id="11190-238">**Duo IPv6 Global Address Set** (*nxd_ipv6_global_address_set*)</span></span> |
| ![Duo IPv6 DAD 프로세스 시작 아이콘](./media/user-guide/netx-events/image66.png)    | <span data-ttu-id="11190-240">**Duo IPv6 DAD 프로세스 시작**(nxd_ipv6_initiate_dad_process)</span><span class="sxs-lookup"><span data-stu-id="11190-240">**Duo IPv6 Initiate Dad Process** (*nxd_ipv6_initiate_dad_process*)</span></span> |
| ![Duo IPv6 인터페이스 주소 가져오기 아이콘](./media/user-guide/netx-events/image67.png)    | <span data-ttu-id="11190-242">**Duo IPv6 인터페이스 주소 가져오기**(nxd_ipv6_interface_address_get)</span><span class="sxs-lookup"><span data-stu-id="11190-242">**Duo IPv6 Interface Address Get** (*nxd_ipv6_interface_address_get*)</span></span> |
| ![Duo IPv6 인터페이스 주소 설정 아이콘](./media/user-guide/netx-events/image68.png)    | <span data-ttu-id="11190-244">**Duo IPv6 인터페이스 주소 설정**(nxd_ipv6_interface_address_set)</span><span class="sxs-lookup"><span data-stu-id="11190-244">**Duo IPv6 Interface Address Set** (*nxd_ipv6_interface_address_set*)</span></span> |
| ![Duo IPv6 링크 로컬 주소 가져오기 아이콘](./media/user-guide/netx-events/image69.png)    | <span data-ttu-id="11190-246">**Duo IPv6 링크 로컬 주소 가져오기**(nxd_ipv6_linklocal_address_get)</span><span class="sxs-lookup"><span data-stu-id="11190-246">**Duo IPv6 Link Local Address Get** (*nxd_ipv6_linklocal_address_get*)</span></span> |
| ![Duo IPv6 링크 로컬 주소 설정 아이콘](./media/user-guide/netx-events/image70.png)    | <span data-ttu-id="11190-248">**Duo IPv6 링크 로컬 주소 설정**(nxd_ipv6_linklocal_address_set)</span><span class="sxs-lookup"><span data-stu-id="11190-248">**Duo IPv6 Link Local Address Set** (*nxd_ipv6_linklocal_address_set*)</span></span> |
| ![Duo IPv6 원시 패킷 송신 아이콘](./media/user-guide/netx-events/image71.png)    | <span data-ttu-id="11190-250">**Duo IPv6 원시 패킷 송신**(nxd_ipv6_raw_packet_send)</span><span class="sxs-lookup"><span data-stu-id="11190-250">**Duo IPv6 Raw Packet Send** (*nxd_ipv6_raw_packet_send)*</span></span> |
| ![DUO TCP 소켓 피어 정보 가져오기 아이콘](./media/user-guide/netx-events/image72.png)    | <span data-ttu-id="11190-252">**DUO TCP 소켓 피어 정보 가져오기**(nxd_tcp_socket_peer_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-252">**Duo TCP Socket Peer Info Get** (*nxd_tcp_socket_peer_info_get*)</span></span> |
| ![Duo TCP 소켓 설정 인터페이스 아이콘](./media/user-guide/netx-events/image73.png)    | <span data-ttu-id="11190-254">**Duo TCP 소켓 설정 인터페이스**(nxd_tcp_socket_set_interface)</span><span class="sxs-lookup"><span data-stu-id="11190-254">**Duo TCP Socket Set Interface** (*nxd_tcp_socket_set_interface*)</span></span> |
| ![Duo UDP 소켓 송신 아이콘](./media/user-guide/netx-events/image74.png)    | <span data-ttu-id="11190-256">**DUO UDP 소켓 송신**(nxd_udp_socket_send)</span><span class="sxs-lookup"><span data-stu-id="11190-256">**Duo UDP Socket Send** (*nxd_udp_socket_send*)</span></span> |
| ![Duo UDP 소켓 설정 인터페이스 아이콘](./media/user-guide/netx-events/image75.png)    | <span data-ttu-id="11190-258">**Duo UDP 소켓 설정 인터페이스**(nxd_udp_socket_set_interface)</span><span class="sxs-lookup"><span data-stu-id="11190-258">**Duo UDP Socket Set Interface** (*nxd_udp_socket_set_interface*)</span></span> |
| ![Duo UDP 원본 추출 아이콘](./media/user-guide/netx-events/image76.png)    | <span data-ttu-id="11190-260">**DUO UDP 원본 추출**(nxd_udp_source_extract)</span><span class="sxs-lookup"><span data-stu-id="11190-260">**Duo UDP Source Extract** (*nxd_udp_source_extract*)</span></span> |
| ![ICMP 사용 아이콘](./media/user-guide/netx-events/image77.png)    | <span data-ttu-id="11190-262">**ICMP 사용**(nx_icmp_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-262">**ICMP Enable** (*nx_icmp_enable*)</span></span> |
| ![ICMP 정보 가져오기 아이콘](./media/user-guide/netx-events/image78.png)    | <span data-ttu-id="11190-264">**ICMP 정보 가져오기**(nx_icmp_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-264">**ICMP Information Get** (*nx_icmp_info_get*)</span></span> |
| ![ICMP Ping 아이콘](./media/user-guide/netx-events/image79.png)    | <span data-ttu-id="11190-266">**ICMP Ping**(nx_icmp_ping)</span><span class="sxs-lookup"><span data-stu-id="11190-266">**ICMP Ping** (*nx_icmp_ping*)</span></span> |
| ![IGMP 사용 아이콘](./media/user-guide/netx-events/image80.png)    | <span data-ttu-id="11190-268">**IGMP 사용**(nx_igmp_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-268">**IGMP Enable** (*nx_igmp_enable*)</span></span> |
| ![IGMP 정보 가져오기 아이콘](./media/user-guide/netx-events/image81.png)    | <span data-ttu-id="11190-270">**IGMP 정보 가져오기**(nx_igmp_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-270">**IGMP Information Get** (*nx_igmp_info_get*)</span></span> |
| ![IGMP 루프백 사용 안 함 아이콘](./media/user-guide/netx-events/image82.png)    | <span data-ttu-id="11190-272">**IGMP 루프백 사용 안 함**(nx_igmp_loopback_disable)</span><span class="sxs-lookup"><span data-stu-id="11190-272">**IGMP Loopback Disable** (*nx_igmp_loopback_disable*)</span></span> |
| ![IGMP 루프백 사용 아이콘](./media/user-guide/netx-events/image83.png)    | <span data-ttu-id="11190-274">**IGMP 루프백 사용**(nx_igmp_loopback_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-274">**IGMP Loopback Enable** (*nx_igmp_loopback_enable*)</span></span> |
| ![IGMP 멀티캐스트 조인 아이콘](./media/user-guide/netx-events/image84.png)    | <span data-ttu-id="11190-276">**IGMP 멀티캐스트 조인**(nx_igmp_multicast_join)</span><span class="sxs-lookup"><span data-stu-id="11190-276">**IGMP Multicast Join** (*nx_igmp_multicast_join*)</span></span> |
| ![IGMP 멀티캐스트 탈퇴 아이콘](./media/user-guide/netx-events/image85.png)    | <span data-ttu-id="11190-278">**IGMP 멀티캐스트 탈퇴**(nx_igmp_multicast_leave)</span><span class="sxs-lookup"><span data-stu-id="11190-278">**IGMP Multicast Leave** (*nx_igmp_multicast_leave*)</span></span> |
| ![IP 주소 변경 알림 아이콘](./media/user-guide/netx-events/image86.png)    | <span data-ttu-id="11190-280">**IP 주소 변경 알림**(nx_ip_address_change_notify)</span><span class="sxs-lookup"><span data-stu-id="11190-280">**IP Address Change Notify** (*nx_ip_address_change_notify*)</span></span> |
| ![IP 주소 가져오기 아이콘](./media/user-guide/netx-events/image87.png)    | <span data-ttu-id="11190-282">**IP 주소 가져오기**(nx_ip_address_get)</span><span class="sxs-lookup"><span data-stu-id="11190-282">**IP Address Get** (*nx_ip_address_get*)</span></span> |
| ![IP 주소 설정 아이콘](./media/user-guide/netx-events/image88.png)    | <span data-ttu-id="11190-284">**IP 주소 설정**(nx_ip_address_set)</span><span class="sxs-lookup"><span data-stu-id="11190-284">**IP Address Set** (*nx_ip_address_set*)</span></span> |
| ![IP 만들기 아이콘](./media/user-guide/netx-events/image89.png)    | <span data-ttu-id="11190-286">**IP 만들기**(nx_ip_create)</span><span class="sxs-lookup"><span data-stu-id="11190-286">**IP Create** (*nx_ip_create*)</span></span> |
| ![IP 삭제 아이콘](./media/user-guide/netx-events/image90.png)    | <span data-ttu-id="11190-288">**IP 삭제**(nx_ip_delete)</span><span class="sxs-lookup"><span data-stu-id="11190-288">**IP Delete** (*nx_ip_delete*)</span></span> |
| ![IP 드라이버 직접 명령 아이콘](./media/user-guide/netx-events/image91.png)    | <span data-ttu-id="11190-290">**IP 드라이버 직접 명령**(nx_ip_driver_direct_command)</span><span class="sxs-lookup"><span data-stu-id="11190-290">**IP Driver Direct Command** (*nx_ip_driver_direct_command*)</span></span> |
| ![IP 전달 사용 안 함 아이콘](./media/user-guide/netx-events/image92.png)    | <span data-ttu-id="11190-292">**IP 전달 사용 안 함**(nx_ip_forwarding_disable)</span><span class="sxs-lookup"><span data-stu-id="11190-292">**IP Forwarding Disable** (*nx_ip_forwarding_disable*)</span></span> |
| ![IP 전달 사용 아이콘](./media/user-guide/netx-events/image93.png)    | <span data-ttu-id="11190-294">**IP 전달 사용**(nx_ip_forwarding_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-294">**IP Forwarding Enable** (*nx_ip_forwarding_enable*)</span></span> |
| ![IP 조각 사용 안 함 아이콘](./media/user-guide/netx-events/image94.png)    | <span data-ttu-id="11190-296">**IP 조각 사용 안 함**(nx_ip_fragment_disable)</span><span class="sxs-lookup"><span data-stu-id="11190-296">**IP Fragment Disable** (*nx_ip_fragment_disable*)</span></span> |
| ![I P 조각 사용 아이콘](./media/user-guide/netx-events/image95.png)    | <span data-ttu-id="11190-298">**IP 조각 사용**(nx_ip_fragment_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-298">**IP Fragment Enable** (*nx_ip_fragment_enable*)</span></span>  |
| ![IP 게이트웨이 주소 설정 아이콘](./media/user-guide/netx-events/image96.png)    | <span data-ttu-id="11190-300">**IP 게이트웨이 주소 설정**(nx_ip_gateway_address_set)</span><span class="sxs-lookup"><span data-stu-id="11190-300">**IP Gateway Address Set** (*nx_ip_gateway_address_set*)</span></span> |
| ![IP 정보 가져오기 아이콘](./media/user-guide/netx-events/image97.png)    | <span data-ttu-id="11190-302">**IP 정보 가져오기**(nx_ip_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-302">**IP Information Get** (*nx_ip_info_get*)</span></span> |
| ![IP 인터페이스 연결 아이콘](./media/user-guide/netx-events/image98.png)    | <span data-ttu-id="11190-304">**IP 인터페이스 연결**(nx_ip_interface_attach)</span><span class="sxs-lookup"><span data-stu-id="11190-304">**IP Interface Attach** (*nx_ip_interface_attach*)</span></span> |
| ![IP 인터페이스 정보 가져오기 아이콘](./media/user-guide/netx-events/image99.png)    | <span data-ttu-id="11190-306">**IP 인터페이스 정보 가져오기**(nx_ip_interface_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-306">**IP Interface Info Get** (*nx_ip_interface_info_get*)</span></span> |
| ![IP 원시 패킷 사용 안 함 아이콘](./media/user-guide/netx-events/image100.png)    | <span data-ttu-id="11190-308">**IP 원시 패킷 사용 안 함**(nx_ip_raw_packet_disable)</span><span class="sxs-lookup"><span data-stu-id="11190-308">**IP Raw Packet Disable** (*nx_ip_raw_packet_disable*)</span></span> |
| ![IP 원시 패킷 사용 아이콘](./media/user-guide/netx-events/image101.png)    | <span data-ttu-id="11190-310">**IP 원시 패킷 사용**(nx_ip_raw_packet_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-310">**IP Raw Packet Enable** (*nx_ip_raw_packet_enable*)</span></span> |
| ![IP 원시 패킷 수신 아이콘](./media/user-guide/netx-events/image102.png)    | <span data-ttu-id="11190-312">**IP 원시 패킷 수신**(nx_ip_raw_packet_receive)</span><span class="sxs-lookup"><span data-stu-id="11190-312">**IP Raw Packet Receive** (*nx_ip_raw_packet_receive*)</span></span> |
| ![IP 원시 패킷 송신 아이콘](./media/user-guide/netx-events/image103.png)    | <span data-ttu-id="11190-314">**IP 원시 패킷 송신**(nx_ip_raw_packet_send)</span><span class="sxs-lookup"><span data-stu-id="11190-314">**IP Raw Packet Send** (*nx_ip_raw_packet_send*)</span></span> |
| ![IP 고정 경로 추가 아이콘](./media/user-guide/netx-events/image104.png)    | <span data-ttu-id="11190-316">**IP 고정 경로 추가**(nx_ip_static_route_add)</span><span class="sxs-lookup"><span data-stu-id="11190-316">**IP Static Route Add** (*nx_ip_static_route_add*)</span></span> |
| ![IP 고정 경로 삭제 아이콘](./media/user-guide/netx-events/image105.png)    | <span data-ttu-id="11190-318">**IP 고정 경로 삭제**(nx_ip_static_route_delete)</span><span class="sxs-lookup"><span data-stu-id="11190-318">**IP Static Route Delete** (*nx_ip_static_route_delete)*</span></span> |
| ![IP 상태 확인 아이콘](./media/user-guide/netx-events/image106.png)    | <span data-ttu-id="11190-320">**IP 상태 확인**(nx_ip_status_check)</span><span class="sxs-lookup"><span data-stu-id="11190-320">**IP Status Check** (*nx_ip_status_check*)</span></span>|
| ![IPSEC 사용 아이콘](./media/user-guide/netx-events/image107.png)    | <span data-ttu-id="11190-322">**IPSEC 사용**(nx_ipsec_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-322">**IPSEC Enable** (*nx_ipsec_enable)*</span></span> |
| ![패킷 할당 아이콘](./media/user-guide/netx-events/image108.png)    | <span data-ttu-id="11190-324">**패킷 할당**(nx_packet_allocate)</span><span class="sxs-lookup"><span data-stu-id="11190-324">**Packet Allocate** (*nx_packet_allocate*)</span></span> |
| ![패킷 복사 아이콘](./media/user-guide/netx-events/image109.png)    | <span data-ttu-id="11190-326">**패킷 복사**(nx_packet_copy)</span><span class="sxs-lookup"><span data-stu-id="11190-326">**Packet Copy** (*nx_packet_copy*)</span></span> |
| ![패킷 데이터 추가 아이콘](./media/user-guide/netx-events/image110.png)    | <span data-ttu-id="11190-328">**패킷 데이터 추가**(nx_packet_data_append)</span><span class="sxs-lookup"><span data-stu-id="11190-328">**Packet Data Append** (*nx_packet_data_append*)</span></span> |
| ![패킷 데이터 추출 오프셋 아이콘](./media/user-guide/netx-events/image111.png)    | <span data-ttu-id="11190-330">**패킷 데이터 추출 오프셋**(nx_packet_data_extract_offset)</span><span class="sxs-lookup"><span data-stu-id="11190-330">**Packet Data Extract Offset** (*nx_packet_data_extract_offset*)</span></span> |
| ![패킷 데이터 검색 아이콘](./media/user-guide/netx-events/image112.png)    | <span data-ttu-id="11190-332">**패킷 데이터 검색**(nx_packet_data_retrieve)</span><span class="sxs-lookup"><span data-stu-id="11190-332">**Packet Data Retrieve** (*nx_packet_data_retrieve*)</span></span> |
| ![패킷 길이 가져오기 아이콘](./media/user-guide/netx-events/image113.png)    | <span data-ttu-id="11190-334">**패킷 길이 가져오기**(nx_packet_length_get)</span><span class="sxs-lookup"><span data-stu-id="11190-334">**Packet Length Get** (*nx_packet_length_get*)</span></span> |
| ![패킷 풀 만들기 아이콘](./media/user-guide/netx-events/image114.png)    | <span data-ttu-id="11190-336">**패킷 풀 만들기**(nx_packet_pool_create)</span><span class="sxs-lookup"><span data-stu-id="11190-336">**Packet Pool Create** (*nx_packet_pool_create*)</span></span> |
| ![패킷 풀 삭제 아이콘](./media/user-guide/netx-events/image115.png)    | <span data-ttu-id="11190-338">**패킷 풀 삭제**(nx_packet_pool_delete)</span><span class="sxs-lookup"><span data-stu-id="11190-338">**Packet Pool Delete** (*nx_packet_pool_delete*)</span></span> |
| ![패킷 풀 정보 가져오기 아이콘](./media/user-guide/netx-events/image116.png)    | <span data-ttu-id="11190-340">**패킷 풀 정보 가져오기**(nx_packet_pool_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-340">**Packet Pool Information Get** (*nx_packet_pool_info_get*)</span></span> |
| ![패킷 해제 아이콘](./media/user-guide/netx-events/image117.png)    | <span data-ttu-id="11190-342">**패킷 해제**(nx_packet_release)</span><span class="sxs-lookup"><span data-stu-id="11190-342">**Packet Release** (*nx_packet_release*)</span></span> |
| ![패킷 전송 해제 아이콘](./media/user-guide/netx-events/image118.png)    | <span data-ttu-id="11190-344">**패킷 전송 해제**(nx_packet_transmit_release)</span><span class="sxs-lookup"><span data-stu-id="11190-344">**Packet Transmit Release** (*nx_packet_transmit_release*)</span></span> |
| ![RARP 사용 안 함 아이콘](./media/user-guide/netx-events/image119.png)    | <span data-ttu-id="11190-346">**RARP 사용 안 함**(nx_rarp_disable)</span><span class="sxs-lookup"><span data-stu-id="11190-346">**RARP Disable** (*nx_rarp_disable*)</span></span> |
| ![RARP 사용 아이콘](./media/user-guide/netx-events/image120.png)    | <span data-ttu-id="11190-348">**RARP 사용**(nx_rarp_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-348">**RARP Enable** (*nx_rarp_enable*)</span></span> |
| ![RARP 정보 가져오기 아이콘](./media/user-guide/netx-events/image121.png)    | <span data-ttu-id="11190-350">**RARP 정보 가져오기**(nx_rarp_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-350">**RARP Information Get** (*nx_rarp_info_get*)</span></span> |
| ![시스템 초기화 아이콘](./media/user-guide/netx-events/image122.png)    | <span data-ttu-id="11190-352">**시스템 초기화**(fx_system_initialize)</span><span class="sxs-lookup"><span data-stu-id="11190-352">**System Initialize** (*nx_system_initialize*)</span></span> |
| ![TCP 클라이언트 소켓 바인딩 아이콘](./media/user-guide/netx-events/image123.png)    | <span data-ttu-id="11190-354">**TCP 클라이언트 소켓 바인딩**(nx_tcp_client_socket_bind)</span><span class="sxs-lookup"><span data-stu-id="11190-354">**TCP Client Socket Bind** (*nx_tcp_client_socket_bind*)</span></span> |
| ![TCP 클라이언트 소켓 연결 아이콘](./media/user-guide/netx-events/image124.png)    | <span data-ttu-id="11190-356">**TCP 클라이언트 소켓 연결**(nx_tcp_client_socket_connect)</span><span class="sxs-lookup"><span data-stu-id="11190-356">**TCP Client Socket Connect** (*nx_tcp_client_socket_connect*)</span></span> |
| ![TCP 클라이언트 소켓 포트 가져오기 아이콘](./media/user-guide/netx-events/image125.png)    | <span data-ttu-id="11190-358">**TCP 클라이언트 소켓 포트 가져오기**(nx_tcp_client_socket_port_get)</span><span class="sxs-lookup"><span data-stu-id="11190-358">**TCP Client Socket Port Get** (*nx_tcp_client_socket_port_get*)</span></span> |
| ![TCP 클라이언트 소켓 바인딩 해제 아이콘](./media/user-guide/netx-events/image126.png)    | <span data-ttu-id="11190-360">**TCP 클라이언트 소켓 바인딩 해제**(nx_tcp_client_socket_unbind)</span><span class="sxs-lookup"><span data-stu-id="11190-360">**TCP Client Socket Unbind** (*nx_tcp_client_socket_unbind*)</span></span> |
| ![TCP 사용 아이콘](./media/user-guide/netx-events/image127.png)    | <span data-ttu-id="11190-362">**TCP 사용**(nx_tcp_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-362">**TCP Enable** (*nx_tcp_enable*)</span></span> |
| ![TCP 사용 가능한 포트 찾기 아이콘](./media/user-guide/netx-events/image128.png)    | <span data-ttu-id="11190-364">**TCP 사용 가능한 포트 찾기**(nx_tcp_free_port_find)</span><span class="sxs-lookup"><span data-stu-id="11190-364">**TCP Free Port Find** (*nx_tcp_free_port_find*)</span></span> |
| ![TCP 정보 가져오기 아이콘](./media/user-guide/netx-events/image129.png)    | <span data-ttu-id="11190-366">**TCP 정보 가져오기**(nx_tcp_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-366">**TCP Information Get** (*nx_tcp_info_get*)</span></span> |
| ![TCP 서버 소켓 수락 아이콘](./media/user-guide/netx-events/image130.png)    | <span data-ttu-id="11190-368">**TCP 서버 소켓 수락**(nx_tcp_server_socket_accept)</span><span class="sxs-lookup"><span data-stu-id="11190-368">**TCP Server Socket Accept** (*nx_tcp_server_socket_accept*)</span></span> |
| ![TCP 서버 소켓 수신 대기 아이콘](./media/user-guide/netx-events/image131.png)    | <span data-ttu-id="11190-370">**TCP 서버 소켓 수신 대기**(nx_tcp_server_socket_listen)</span><span class="sxs-lookup"><span data-stu-id="11190-370">**TCP Server Socket Listen** (*nx_tcp_server_socket_listen*)</span></span> |
| ![TCP 서버 소켓 다시 수신 대기 아이콘](./media/user-guide/netx-events/image132.png)    | <span data-ttu-id="11190-372">**TCP 서버 소켓 다시 수신 대기**(nx_tcp_server_socket_relisten)</span><span class="sxs-lookup"><span data-stu-id="11190-372">**TCP Server Socket Relisten** (*nx_tcp_server_socket_relisten*)</span></span> |
| ![TCP 서버 소켓 허용 안 함 아이콘](./media/user-guide/netx-events/image133.png)    | <span data-ttu-id="11190-374">**TCP 서버 소켓 허용 안 함**(nx_tcp_server_socket_unaccept)</span><span class="sxs-lookup"><span data-stu-id="11190-374">**TCP Server Socket Unaccept** (*nx_tcp_server_socket_unaccept*)</span></span> |
| ![T C P 서버 소켓 수신 대기 취소 아이콘](./media/user-guide/netx-events/image134.png)    | <span data-ttu-id="11190-376">**TCP 서버 소켓 수신 대기 취소**(nx_tcp_server_socket_unlisten)</span><span class="sxs-lookup"><span data-stu-id="11190-376">**TCP Server Socket Unlisten** (*nx_tcp_server_socket_unlisten*)</span></span> |
| ![TCP 소켓 사용 가능 바이트 아이콘](./media/user-guide/netx-events/image135.png)    | <span data-ttu-id="11190-378">**TCP 소켓 사용 가능 바이트**(nx_tcp_socket_bytes_available)</span><span class="sxs-lookup"><span data-stu-id="11190-378">**TCP Socket Bytes Available** (*nx_tcp_socket_bytes_available*)</span></span> |
| ![TCP 소켓 만들기 아이콘](./media/user-guide/netx-events/image136.png)    | <span data-ttu-id="11190-380">**TCP 소켓 만들기**(nx_tcp_socket_create)</span><span class="sxs-lookup"><span data-stu-id="11190-380">**TCP Socket Create** (*nx_tcp_socket_create*)</span></span> |
| ![TCP 소켓 삭제 아이콘](./media/user-guide/netx-events/image137.png)    | <span data-ttu-id="11190-382">**TCP 소켓 삭제**(nx_tcp_socket_delete)</span><span class="sxs-lookup"><span data-stu-id="11190-382">**TCP Socket Delete** (*nx_tcp_socket_delete*)</span></span> |
| ![TCP 소켓 연결 끊기 아이콘](./media/user-guide/netx-events/image138.png)    | <span data-ttu-id="11190-384">**TCP 소켓 연결 끊기**(nx_tcp_socket_disconnect)</span><span class="sxs-lookup"><span data-stu-id="11190-384">**TCP Socket Disconnect** (*nx_tcp_socket_disconnect*)</span></span> |
| ![TCP 소켓 정보 가져오기 아이콘](./media/user-guide/netx-events/image139.png)    | <span data-ttu-id="11190-386">**TCP 소켓 정보 가져오기**(nx_tcp_socket_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-386">**TCP Socket Information Get** (*nx_tcp_socket_info_get*)</span></span> |
| ![TCP 소켓 MSS 가져오기 아이콘](./media/user-guide/netx-events/image140.png)    | <span data-ttu-id="11190-388">**TCP 소켓 MSS 가져오기**(nx_tcp_socket_mss_get)</span><span class="sxs-lookup"><span data-stu-id="11190-388">**TCP Socket MSS Get** (*nx_tcp_socket_mss_get*)</span></span> |
| ![TCP 소켓 MSS 피어 가져오기 아이콘](./media/user-guide/netx-events/image141.png)    | <span data-ttu-id="11190-390">**TCP 소켓 MSS 피어 가져오기**(nx_tcp_socket_mss_peer_get)</span><span class="sxs-lookup"><span data-stu-id="11190-390">**TCP Socket MSS Peer Get** (*nx_tcp_socket_mss_peer_get*)</span></span> |
| ![TCP 소켓 MSS 설정 아이콘](./media/user-guide/netx-events/image142.png)    | <span data-ttu-id="11190-392">**TCP 소켓 MSS 설정**(nx_tcp_socket_mss_set)</span><span class="sxs-lookup"><span data-stu-id="11190-392">**TCP Socket MSS Set** (*nx_tcp_socket_mss_set*)</span></span> |
| ![TCP 소켓 피어 정보 가져오기 아이콘](./media/user-guide/netx-events/image143.png)    | <span data-ttu-id="11190-394">**TCP 소켓 피어 정보 가져오기**(nx_tcp_socket_peer_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-394">**TCP Socket Peer Info Get** (*nx_tcp_socket_peer_info_get*)</span></span> |
| ![TCP 소켓 수신 아이콘](./media/user-guide/netx-events/image144.png)    | <span data-ttu-id="11190-396">**TCP 소켓 수신**(nx_tcp_socket_receive)</span><span class="sxs-lookup"><span data-stu-id="11190-396">**TCP Socket Receive** (*nx_tcp_socket_receive*)</span></span> |
| ![TCP 소켓 수신 알림 아이콘](./media/user-guide/netx-events/image145.png)    | <span data-ttu-id="11190-398">**TCP 소켓 수신 알림**(nx_tcp_socket_receive_notify)</span><span class="sxs-lookup"><span data-stu-id="11190-398">**TCP Socket Receive Notify** (*nx_tcp_socket_receive_notify*)</span></span> |
| ![TCP 소켓 송신 아이콘](./media/user-guide/netx-events/image146.png)    | <span data-ttu-id="11190-400">**TCP 소켓 송신**(nx_tcp_socket_send)</span><span class="sxs-lookup"><span data-stu-id="11190-400">**TCP Socket Send** (*nx_tcp_socket_send*)</span></span> |
| ![TCP 소켓 상태 대기 아이콘](./media/user-guide/netx-events/image147.png)    | <span data-ttu-id="11190-402">**TCP 소켓 상태 대기**(nx_tcp_socket_state_wait)</span><span class="sxs-lookup"><span data-stu-id="11190-402">**TCP Socket State Wait** (*nx_tcp_socket_state_wait*)</span></span> |
| ![TCP 소켓 전송 구성 아이콘](./media/user-guide/netx-events/image148.png)    | <span data-ttu-id="11190-404">**TCP 소켓 전송 구성**(nx_tcp_socket_transmit_configure)</span><span class="sxs-lookup"><span data-stu-id="11190-404">**TCP Socket Transmit Configure** (*nx_tcp_socket_transmit_configure*)</span></span> |
| ![TCP 소켓 창 업데이트 알림 설정 아이콘](./media/user-guide/netx-events/image149.png)    | <span data-ttu-id="11190-406">**TCP 소켓 창 업데이트 알림 설정**(nx_tcp_socket_window_update_notify_set)</span><span class="sxs-lookup"><span data-stu-id="11190-406">**TCP Socket Window Update Notify Set** (*nx_tcp_socket_window_update_notify_set*)</span></span>  |
| ![UDP 사용 아이콘](./media/user-guide/netx-events/image150.png)    | <span data-ttu-id="11190-408">**UDP 사용**(nx_udp_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-408">**UDP Enable** (*nx_udp_enable*)</span></span> |
| ![UDP 사용 가능한 포트 찾기 아이콘](./media/user-guide/netx-events/image151.png)    | <span data-ttu-id="11190-410">**UDP 사용 가능한 포트 찾기**(nx_udp_free_port_find)</span><span class="sxs-lookup"><span data-stu-id="11190-410">**UDP Free Port Find** (*nx_udp_free_port_find*)</span></span> |
| ![UDP 정보 가져오기 아이콘](./media/user-guide/netx-events/image152.png)    | <span data-ttu-id="11190-412">**UDP 정보 가져오기**(nx_udp_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-412">**UDP Information Get** (*nx_udp_info_get*)</span></span> |
| ![UDP 소켓 바인딩 아이콘](./media/user-guide/netx-events/image153.png)    | <span data-ttu-id="11190-414">**UDP 소켓 바인딩**(nx_udp_socket_bind)</span><span class="sxs-lookup"><span data-stu-id="11190-414">**UDP Socket Bind** (*nx_udp_socket_bind*)</span></span> |
| ![UDP 소켓 사용 가능 바이트 아이콘](./media/user-guide/netx-events/image154.png)    | <span data-ttu-id="11190-416">**UDP 소켓 사용 가능 바이트**(nx_udp_socket_bytes_available)</span><span class="sxs-lookup"><span data-stu-id="11190-416">**UDP Socket Bytes Available** (*nx_udp_socket_bytes_available*)</span></span> |
| ![U D P 소켓 체크섬 사용 안 함 아이콘](./media/user-guide/netx-events/image155.png)    | <span data-ttu-id="11190-418">**UDP 소켓 체크섬 사용 안 함**(nx_udp_socket_checksum_disable)</span><span class="sxs-lookup"><span data-stu-id="11190-418">**UDP Socket Checksum Disable** (*nx_udp_socket_checksum_disable*)</span></span> |
| ![UDP 소켓 체크섬 사용 아이콘](./media/user-guide/netx-events/image156.png)    | <span data-ttu-id="11190-420">**UDP 소켓 체크섬 사용**(nx_udp_socket_checksum_enable)</span><span class="sxs-lookup"><span data-stu-id="11190-420">**UDP Socket Checksum Enable** *(nx_udp_socket_checksum_enable)*</span></span> |
| ![UDP 소켓 만들기 아이콘](./media/user-guide/netx-events/image157.png)    | <span data-ttu-id="11190-422">**UDP 소켓 만들기**(nx_udp_socket_create)</span><span class="sxs-lookup"><span data-stu-id="11190-422">**UDP Socket Create** (*nx_udp_socket_create*)</span></span> |
| ![UDP 소켓 삭제 아이콘](./media/user-guide/netx-events/image158.png)    | <span data-ttu-id="11190-424">**UDP 소켓 삭제**(nx_udp_socket_delete)</span><span class="sxs-lookup"><span data-stu-id="11190-424">**UDP Socket Delete** (*nx_udp_socket_delete*)</span></span> |
| ![UDP 소켓 정보 가져오기 아이콘](./media/user-guide/netx-events/image159.png)    | <span data-ttu-id="11190-426">**UDP 소켓 정보 가져오기**(nx_udp_socket_info_get)</span><span class="sxs-lookup"><span data-stu-id="11190-426">**UDP Socket Information Get** (*nx_udp_socket_info_get*)</span></span> |
| ![UDP 소켓 인터페이스 설정 아이콘](./media/user-guide/netx-events/image160.png)    | <span data-ttu-id="11190-428">**UDP 소켓 인터페이스 설정**(nx_udp_socket_interface_set)</span><span class="sxs-lookup"><span data-stu-id="11190-428">**UDP Socket Interface Set** (*nx_udp_socket_interface_set*)</span></span> |
| ![UDP 소켓 포트 가져오기 아이콘](./media/user-guide/netx-events/image161.png)    | <span data-ttu-id="11190-430">**UDP 소켓 포트 가져오기**(nx_udp_socket_port_get)</span><span class="sxs-lookup"><span data-stu-id="11190-430">**UDP Socket Port Get** (*nx_udp_socket_port_get*)</span></span> |
| ![UDP 소켓 수신 아이콘](./media/user-guide/netx-events/image162.png)    | <span data-ttu-id="11190-432">**UDP 소켓 수신**(nx_udp_socket_receive)</span><span class="sxs-lookup"><span data-stu-id="11190-432">**UDP Socket Receive** (*nx_udp_socket_receive*)</span></span> |
| ![UDP 소켓 수신 알림 아이콘](./media/user-guide/netx-events/image163.png)    | <span data-ttu-id="11190-434">**UDP 소켓 수신 알림**(nx_udp_socket_receive_notify)</span><span class="sxs-lookup"><span data-stu-id="11190-434">**UDP Socket Receive Notify** (*nx_udp_socket_receive_notify*)</span></span> |
| ![UDP 소켓 송신 아이콘](./media/user-guide/netx-events/image164.png)    | <span data-ttu-id="11190-436">**UDP 소켓 송신**(nx_udp_socket_send)</span><span class="sxs-lookup"><span data-stu-id="11190-436">**UDP Socket Send** (*nx_udp_socket_send*)</span></span> |
| ![UDP 소켓 바인딩 해제 아이콘](./media/user-guide/netx-events/image165.png)    | <span data-ttu-id="11190-438">**UDP 소켓 바인딩 해제**(nx_udp_socket_unbind)</span><span class="sxs-lookup"><span data-stu-id="11190-438">**UDP Socket Unbind** (*nx_udp_socket_unbind*)</span></span> |
| ![UDP 원본 추출 아이콘](./media/user-guide/netx-events/image166.png)    | <span data-ttu-id="11190-440">**UDP 원본 추출**(nx_udp_source_extract)</span><span class="sxs-lookup"><span data-stu-id="11190-440">**UDP Source Extract** (*nx_udp_source_extract*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="11190-441">이벤트 설명</span><span class="sxs-lookup"><span data-stu-id="11190-441">Event Descriptions</span></span>

<span data-ttu-id="11190-442">다음 페이지에서는 NetX 추적 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="11190-442">The following pages describe the NetX Trace Events.</span></span>

### <a name="internal-arp-request-receive"></a><span data-ttu-id="11190-443">내부 ARP 요청 수신</span><span class="sxs-lookup"><span data-stu-id="11190-443">Internal ARP Request Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="11190-444">내부 ARP 요청 수신</span><span class="sxs-lookup"><span data-stu-id="11190-444">Internal ARP request receive</span></span>

<span data-ttu-id="11190-445">**아이콘** ![내부 ARP 요청 수신 아이콘](./media/user-guide/netx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="11190-445">**Icon** ![Internal ARP request receive icon](./media/user-guide/netx-events/image1.png)</span></span>

<span data-ttu-id="11190-446">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-446">**Description**</span></span>

<span data-ttu-id="11190-447">이 이벤트는 내부 NetX ARP 요청 수신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-447">This event represents an internal NetX ARP request receive event.</span></span>

<span data-ttu-id="11190-448">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-448">**Information Fields**</span></span>

- <span data-ttu-id="11190-449">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-449">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-450">정보 필드 2: 원본 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-450">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="11190-451">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-451">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-452">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-452">Info Field 4: Not used</span></span>

### <a name="internal-arp-request-send"></a><span data-ttu-id="11190-453">내부 ARP 요청 송신</span><span class="sxs-lookup"><span data-stu-id="11190-453">Internal ARP Request Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="11190-454">내부 ARP 요청 송신</span><span class="sxs-lookup"><span data-stu-id="11190-454">Internal ARP request send</span></span>

<span data-ttu-id="11190-455">**아이콘** ![내부 ARP 요청 송신 아이콘](./media/user-guide/netx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="11190-455">**Icon** ![Internal ARP request send icon](./media/user-guide/netx-events/image2.png)</span></span>

<span data-ttu-id="11190-456">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-456">**Description**</span></span>

<span data-ttu-id="11190-457">이 이벤트는 내부 NetX ARP 요청 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-457">This event represents an internal NetX ARP request send event.</span></span>

<span data-ttu-id="11190-458">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-458">**Information Fields**</span></span>

- <span data-ttu-id="11190-459">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-459">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-460">정보 필드 2: 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-460">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="11190-461">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-461">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-462">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-462">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-receive"></a><span data-ttu-id="11190-463">내부 ARP 응답 수신</span><span class="sxs-lookup"><span data-stu-id="11190-463">Internal ARP Response Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="11190-464">내부 ARP 요청 수신</span><span class="sxs-lookup"><span data-stu-id="11190-464">Internal ARP request receive</span></span>

<span data-ttu-id="11190-465">**아이콘** ![내부 ARP 요청 수신 아이콘](./media/user-guide/netx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="11190-465">**Icon** ![The Internal ARP request receive icon](./media/user-guide/netx-events/image3.png)</span></span>

<span data-ttu-id="11190-466">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-466">**Description**</span></span>

<span data-ttu-id="11190-467">이 이벤트는 내부 NetX ARP 응답 수신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-467">This event represents an internal NetX ARP response receive event.</span></span>

<span data-ttu-id="11190-468">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-468">**Information Fields**</span></span>

- <span data-ttu-id="11190-469">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-469">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-470">정보 필드 2: 원본 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-470">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="11190-471">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-471">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-472">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-472">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-send"></a><span data-ttu-id="11190-473">내부 ARP 응답 송신</span><span class="sxs-lookup"><span data-stu-id="11190-473">Internal ARP Response Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="11190-474">내부 ARP 요청 송신</span><span class="sxs-lookup"><span data-stu-id="11190-474">Internal ARP request send</span></span>

<span data-ttu-id="11190-475">**아이콘** ![내부 ARP 요청 송신 아이콘](./media/user-guide/netx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="11190-475">**Icon** ![The Internal ARP request send icon](./media/user-guide/netx-events/image4.png)</span></span>

<span data-ttu-id="11190-476">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-476">**Description**</span></span>

<span data-ttu-id="11190-477">이 이벤트는 내부 NetX 응답 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-477">This event represents an internal NetX response send event.</span></span>

<span data-ttu-id="11190-478">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-478">**Information Fields**</span></span>

- <span data-ttu-id="11190-479">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-479">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-480">정보 필드 2: 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-480">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="11190-481">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-481">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-482">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-482">Info Field 4: Not used</span></span>

### <a name="internal-icmp-receive"></a><span data-ttu-id="11190-483">내부 ICMP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-483">Internal ICMP Receive</span></span> 

#### <a name="internal-icmp-receive"></a><span data-ttu-id="11190-484">내부 ICMP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-484">Internal ICMP receive</span></span>

<span data-ttu-id="11190-485">**아이콘** ![내부 ICMP 수신 아이콘](./media/user-guide/netx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="11190-485">**Icon** ![Internal I C M P receive icon](./media/user-guide/netx-events/image5.png)</span></span>

<span data-ttu-id="11190-486">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-486">**Description**</span></span>

<span data-ttu-id="11190-487">이 이벤트는 내부 NetX ICMP 수신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-487">This event represents an internal NetX ICMP receive event.</span></span>

<span data-ttu-id="11190-488">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-488">**Information Fields**</span></span>

- <span data-ttu-id="11190-489">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-489">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-490">정보 필드 2: 원본 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-490">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="11190-491">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-491">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-492">정보 필드 4: ICMP 헤더의 단어 0입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-492">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-icmp-send"></a><span data-ttu-id="11190-493">내부 ICMP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-493">Internal ICMP Send</span></span> 

#### <a name="internal-icmp-send"></a><span data-ttu-id="11190-494">내부 ICMP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-494">Internal ICMP send</span></span>

<span data-ttu-id="11190-495">**아이콘** ![내부 ICMP 송신 아이콘](./media/user-guide/netx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="11190-495">**Icon** ![Internal I C M P send icon](./media/user-guide/netx-events/image6.png)</span></span>

<span data-ttu-id="11190-496">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-496">**Description**</span></span>

<span data-ttu-id="11190-497">이 이벤트는 내부 NetX ICMP 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-497">This event represents an internal NetX ICMP send event.</span></span>

<span data-ttu-id="11190-498">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-498">**Information Fields**</span></span>

- <span data-ttu-id="11190-499">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-499">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-500">정보 필드 2: 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-500">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="11190-501">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-501">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-502">정보 필드 4: ICMP 헤더의 단어 0입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-502">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-igmp-receive"></a><span data-ttu-id="11190-503">내부 IGMP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-503">Internal IGMP Receive</span></span> 

#### <a name="internal-igmp-receive"></a><span data-ttu-id="11190-504">내부 IGMP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-504">Internal IGMP receive</span></span>

<span data-ttu-id="11190-505">**아이콘** ![내부 IGMP 수신 아이콘](./media/user-guide/netx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="11190-505">**Icon** ![Internal I G M P receive icon](./media/user-guide/netx-events/image7.png)</span></span>

<span data-ttu-id="11190-506">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-506">**Description**</span></span>

<span data-ttu-id="11190-507">이 이벤트는 내부 NetX IGMP 수신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-507">This event represents an internal NetX IGMP receive event.</span></span>

<span data-ttu-id="11190-508">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-508">**Information Fields**</span></span>

- <span data-ttu-id="11190-509">정보 필드 1: IP 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-509">Info Field 1: IP Pointer</span></span>
- <span data-ttu-id="11190-510">정보 필드 2: 원본 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-510">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="11190-511">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-511">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-512">정보 필드 4: IGMP 헤더의 단어 0입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-512">Info Field 4: Word 0 of IGMP header</span></span>

### <a name="internal-ip-receive"></a><span data-ttu-id="11190-513">내부 IP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-513">Internal IP Receive</span></span> 

#### <a name="internal-ip-receive"></a><span data-ttu-id="11190-514">내부 IP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-514">Internal IP receive</span></span>

<span data-ttu-id="11190-515">**아이콘** ![내부 IP 수신 아이콘](./media/user-guide/netx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="11190-515">**Icon** ![Internal I P receive icon](./media/user-guide/netx-events/image8.png)</span></span>

<span data-ttu-id="11190-516">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-516">**Description**</span></span>

<span data-ttu-id="11190-517">이 이벤트는 내부 NetX IP 수신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-517">This event represents an internal NetX IP receive event.</span></span>

<span data-ttu-id="11190-518">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-518">**Information Fields**</span></span>

- <span data-ttu-id="11190-519">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-519">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-520">정보 필드 2: 원본 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-520">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="11190-521">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-521">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-522">정보 필드 4: 패킷 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-522">Info Field 4: Packet length</span></span>

### <a name="internal-ip-send"></a><span data-ttu-id="11190-523">내부 IP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-523">Internal IP Send</span></span>

#### <a name="internal-ip-send"></a><span data-ttu-id="11190-524">내부 IP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-524">Internal IP send</span></span>

<span data-ttu-id="11190-525">**아이콘** ![내부 IP 송신 아이콘](./media/user-guide/netx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="11190-525">**Icon** ![Internal I P send icon](./media/user-guide/netx-events/image9.png)</span></span>

<span data-ttu-id="11190-526">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-526">**Description**</span></span>

<span data-ttu-id="11190-527">이 이벤트는 내부 NetX IP 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-527">This event represents an internal NetX IP send event.</span></span>

<span data-ttu-id="11190-528">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-528">**Information Fields**</span></span>

- <span data-ttu-id="11190-529">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-529">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-530">정보 필드 2: 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-530">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="11190-531">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-531">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-532">정보 필드 4: 패킷 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-532">Info Field 4: Packet length</span></span>

### <a name="internal-tcp-data-receive"></a><span data-ttu-id="11190-533">내부 TCP 데이터 수신</span><span class="sxs-lookup"><span data-stu-id="11190-533">Internal TCP Data Receive</span></span> 

#### <a name="internal-tcp-data-receive"></a><span data-ttu-id="11190-534">내부 TCP 데이터 수신</span><span class="sxs-lookup"><span data-stu-id="11190-534">Internal TCP Data Receive</span></span>

<span data-ttu-id="11190-535">**아이콘** ![내부 TCP 데이터 수신 아이콘](./media/user-guide/netx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="11190-535">**Icon** ![Internal T C P data receive icon](./media/user-guide/netx-events/image10.png)</span></span>

<span data-ttu-id="11190-536">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-536">**Description**</span></span>

<span data-ttu-id="11190-537">이 이벤트는 내부 NetX TCP 데이터 수신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-537">This event represents an internal NetX TCP data receive event.</span></span>

<span data-ttu-id="11190-538">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-538">**Information Fields**</span></span>

- <span data-ttu-id="11190-539">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-539">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-540">정보 필드 2: 원본 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-540">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="11190-541">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-541">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-542">정보 필드 4: 수신 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-542">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-data-send"></a><span data-ttu-id="11190-543">내부 TCP 데이터 송신</span><span class="sxs-lookup"><span data-stu-id="11190-543">Internal TCP data send</span></span> 

#### <a name="internal-tcp-data-send"></a><span data-ttu-id="11190-544">내부 TCP 데이터 송신</span><span class="sxs-lookup"><span data-stu-id="11190-544">Internal TCP Data Send</span></span>

<span data-ttu-id="11190-545">**아이콘** ![내부 TCP 데이터 송신 아이콘](./media/user-guide/netx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="11190-545">**Icon** ![Internal T C P data send icon](./media/user-guide/netx-events/image11.png)</span></span>

<span data-ttu-id="11190-546">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-546">**Description**</span></span>

<span data-ttu-id="11190-547">이 이벤트는 내부 NetX TCP 데이터 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-547">This event represents an internal NetX TCP data send event.</span></span>

<span data-ttu-id="11190-548">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-548">**Information Fields**</span></span>

- <span data-ttu-id="11190-549">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-549">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-550">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-550">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-551">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-551">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-552">정보 필드 4: 전송 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-552">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="11190-553">내부 TCP FIN 수신</span><span class="sxs-lookup"><span data-stu-id="11190-553">Internal TCP FIN Receive</span></span> 

#### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="11190-554">내부 TCP FIN 수신</span><span class="sxs-lookup"><span data-stu-id="11190-554">Internal TCP fin receive</span></span>

<span data-ttu-id="11190-555">**아이콘** ![내부 TCP FIN 수신 아이콘](./media/user-guide/netx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="11190-555">**Icon** ![Internal T C P F I N receive icon](./media/user-guide/netx-events/image12.png)</span></span>

<span data-ttu-id="11190-556">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-556">**Description**</span></span>

<span data-ttu-id="11190-557">이 이벤트는 내부 NetX TCP FIN 수신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-557">This event represents an internal NetX TCP FIN receive event.</span></span>

<span data-ttu-id="11190-558">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-558">**Information Fields**</span></span> 

- <span data-ttu-id="11190-559">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-559">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-560">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-560">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-561">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-561">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-562">정보 필드 4: 수신 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-562">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-fin-send"></a><span data-ttu-id="11190-563">내부 TCP FIN 송신</span><span class="sxs-lookup"><span data-stu-id="11190-563">Internal TCP FIN Send</span></span> 

#### <a name="internal-tcp-fin-send"></a><span data-ttu-id="11190-564">내부 TCP FIN 송신</span><span class="sxs-lookup"><span data-stu-id="11190-564">Internal TCP fin send</span></span>

<span data-ttu-id="11190-565">**아이콘** ![내부 TCP FIN 송신 아이콘](./media/user-guide/netx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="11190-565">**Icon** ![Internal T C P F I N send icon](./media/user-guide/netx-events/image13.png)</span></span>

<span data-ttu-id="11190-566">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-566">**Description**</span></span>

<span data-ttu-id="11190-567">이 이벤트는 내부 NetX TCP FIN 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-567">This event represents an internal NetX TCP FIN send event.</span></span>

<span data-ttu-id="11190-568">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-568">**Information Fields**</span></span>

- <span data-ttu-id="11190-569">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-569">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-570">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-570">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-571">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-571">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-572">정보 필드 4: 전송 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-572">Info Field 4:Transmit sequence number</span></span>

### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="11190-573">내부 TCP RST 수신</span><span class="sxs-lookup"><span data-stu-id="11190-573">Internal TCP RST Receive</span></span> 

#### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="11190-574">내부 TCP RST 수신</span><span class="sxs-lookup"><span data-stu-id="11190-574">Internal TCP RST receive</span></span>

<span data-ttu-id="11190-575">**아이콘** ![내부 TCP RST 수신 아이콘](./media/user-guide/netx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="11190-575">**Icon** ![Internal T C P R S T receive icon](./media/user-guide/netx-events/image14.png)</span></span>

<span data-ttu-id="11190-576">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-576">**Description**</span></span>

<span data-ttu-id="11190-577">이 이벤트는 내부 NetX TCP 재설정 수신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-577">This event represents an internal NetX TCP reset receive event.</span></span>

<span data-ttu-id="11190-578">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-578">**Information Fields**</span></span>

- <span data-ttu-id="11190-579">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-579">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="11190-580">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-580">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="11190-581">정보 필드 3: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-581">Info Field 3: Pointer to packet.</span></span>
- <span data-ttu-id="11190-582">정보 필드 4: 수신 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-582">Info Field 4: Receive sequence number.</span></span>

### <a name="internal-tcp-rst-send"></a><span data-ttu-id="11190-583">내부 TCP RST 송신</span><span class="sxs-lookup"><span data-stu-id="11190-583">Internal TCP RST Send</span></span> 

#### <a name="internal-tcp-rst-send"></a><span data-ttu-id="11190-584">내부 TCP RST 송신</span><span class="sxs-lookup"><span data-stu-id="11190-584">Internal TCP RST send</span></span>

<span data-ttu-id="11190-585">**아이콘** ![내부 TCP RST 송신 아이콘](./media/user-guide/netx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="11190-585">**Icon** ![Internal T C P R S T send icon](./media/user-guide/netx-events/image15.png)</span></span>

<span data-ttu-id="11190-586">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-586">**Description**</span></span>

<span data-ttu-id="11190-587">이 이벤트는 내부 NetX TCP 재설정 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-587">This event represents an internal NetX TCP reset send event.</span></span>

<span data-ttu-id="11190-588">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-588">**Information Fields**</span></span>

- <span data-ttu-id="11190-589">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-589">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-590">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-590">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-591">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-591">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-592">정보 필드 4: 전송 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-592">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="11190-593">내부 TCP SYN 수신</span><span class="sxs-lookup"><span data-stu-id="11190-593">Internal TCP SYN Receive</span></span> 

#### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="11190-594">내부 TCP SYN 수신</span><span class="sxs-lookup"><span data-stu-id="11190-594">Internal TCP SYN receive</span></span>

<span data-ttu-id="11190-595">**아이콘** ![내부 TCP SYN 수신 아이콘](./media/user-guide/netx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="11190-595">**Icon** ![Internal T C P S Y N receive icon](./media/user-guide/netx-events/image16.png)</span></span>

<span data-ttu-id="11190-596">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-596">**Description**</span></span>

<span data-ttu-id="11190-597">이 이벤트는 내부 NetX TCP SYN 수신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-597">This event represents an internal NetX TCP SYN receive event.</span></span>

<span data-ttu-id="11190-598">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-598">**Information Fields**</span></span>

- <span data-ttu-id="11190-599">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-599">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-600">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-600">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-601">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-601">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-602">정보 필드 4: 수신 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-602">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-syn-send"></a><span data-ttu-id="11190-603">내부 TCP SYN 송신</span><span class="sxs-lookup"><span data-stu-id="11190-603">Internal TCP SYN Send</span></span> 

#### <a name="internal-tcp-syn-send"></a><span data-ttu-id="11190-604">내부 TCP SYN 송신</span><span class="sxs-lookup"><span data-stu-id="11190-604">Internal TCP SYN send</span></span>

<span data-ttu-id="11190-605">**아이콘** ![내부 TCP SYN 송신 아이콘](./media/user-guide/netx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="11190-605">**Icon** ![Internal T C P S Y N send icon](./media/user-guide/netx-events/image17.png)</span></span>

<span data-ttu-id="11190-606">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-606">**Description**</span></span>

<span data-ttu-id="11190-607">이 이벤트는 내부 NetX TCP SYN 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-607">This event represents an internal NetX TCP SYN send event.</span></span>

<span data-ttu-id="11190-608">정보 필드</span><span class="sxs-lookup"><span data-stu-id="11190-608">Information Fields</span></span> 

- <span data-ttu-id="11190-609">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-609">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-610">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-610">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-611">정보 필드 3: 패킷에 대한 포인터입니다. 정보 필드 4: 전송 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-611">Info Field 3: Pointer to packet -Info Field 4: Transmit sequence number</span></span>

### <a name="internal-udp-receive"></a><span data-ttu-id="11190-612">내부 UDP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-612">Internal UDP Receive</span></span> 

#### <a name="internal-udp-receive"></a><span data-ttu-id="11190-613">내부 UDP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-613">Internal UDP receive</span></span>

<span data-ttu-id="11190-614">**아이콘** ![내부 UDP 수신 아이콘](./media/user-guide/netx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="11190-614">**Icon** ![Internal U D P receive icon](./media/user-guide/netx-events/image18.png)</span></span>

<span data-ttu-id="11190-615">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-615">**Description**</span></span>

<span data-ttu-id="11190-616">이 이벤트는 내부 NetX UDP 수신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-616">This event represents an internal NetX UDP receive event.</span></span>

<span data-ttu-id="11190-617">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-617">**Information Fields**</span></span> 

- <span data-ttu-id="11190-618">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-618">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-619">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-619">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-620">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-620">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-621">정보 필드 4: UDP 헤더의 단어 0입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-621">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-udp-send"></a><span data-ttu-id="11190-622">내부 UDP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-622">Internal UDP Send</span></span> 

#### <a name="internal-udp-send"></a><span data-ttu-id="11190-623">내부 UDP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-623">Internal UDP send</span></span>

<span data-ttu-id="11190-624">**아이콘** ![내부 UDP 송신 아이콘](./media/user-guide/netx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="11190-624">**Icon** ![Internal U D P send icon](./media/user-guide/netx-events/image19.png)</span></span>

<span data-ttu-id="11190-625">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-625">**Description**</span></span>

<span data-ttu-id="11190-626">이 이벤트는 내부 NetX UDP 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-626">This event represents an internal NetX UDP send event.</span></span>

<span data-ttu-id="11190-627">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-627">**Information Fields**</span></span>

- <span data-ttu-id="11190-628">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-628">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-629">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-629">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-630">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-630">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-631">정보 필드 4: UDP 헤더의 단어 0입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-631">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-rarp-receive"></a><span data-ttu-id="11190-632">내부 RARP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-632">Internal RARP Receive</span></span> 

#### <a name="internal-rarp-receive"></a><span data-ttu-id="11190-633">내부 RARP 수신</span><span class="sxs-lookup"><span data-stu-id="11190-633">Internal RARP receive</span></span> 

<span data-ttu-id="11190-634">**아이콘** ![내부 RARP 수신 아이콘](./media/user-guide/netx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="11190-634">**Icon** ![Internal R A R P receive icon](./media/user-guide/netx-events/image20.png)</span></span>

<span data-ttu-id="11190-635">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-635">**Description**</span></span>

<span data-ttu-id="11190-636">이 이벤트는 내부 NetX RARP 수신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-636">This event represents an internal NetX RARP receive event.</span></span>

<span data-ttu-id="11190-637">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-637">**Information Fields**</span></span> 

- <span data-ttu-id="11190-638">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-638">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-639">정보 필드 2: 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-639">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="11190-640">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-640">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-641">정보 필드 4: RARP 헤더의 단어 1입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-641">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-rarp-send"></a><span data-ttu-id="11190-642">내부 RARP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-642">Internal RARP Send</span></span> 

#### <a name="internal-rarp-send"></a><span data-ttu-id="11190-643">내부 RARP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-643">Internal RARP send</span></span> 

<span data-ttu-id="11190-644">**아이콘** ![내부 RARP 송신 아이콘](./media/user-guide/netx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="11190-644">**Icon** ![Internal R A R P send icon](./media/user-guide/netx-events/image21.png)</span></span>

<span data-ttu-id="11190-645">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-645">**Description**</span></span>

<span data-ttu-id="11190-646">이 이벤트는 내부 NetX RARP 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-646">This event represents an internal NetX RARP send event.</span></span>

<span data-ttu-id="11190-647">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-647">**Information Fields**</span></span>

- <span data-ttu-id="11190-648">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-648">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-649">정보 필드 2: 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-649">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="11190-650">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-650">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-651">정보 필드 4: RARP 헤더의 단어 1입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-651">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-tcp-retry"></a><span data-ttu-id="11190-652">내부 TCP 다시 시도</span><span class="sxs-lookup"><span data-stu-id="11190-652">Internal TCP Retry</span></span> 

#### <a name="internal-tcp-retry"></a><span data-ttu-id="11190-653">내부 TCP 다시 시도</span><span class="sxs-lookup"><span data-stu-id="11190-653">Internal TCP retry</span></span> 

<span data-ttu-id="11190-654">**아이콘** ![내부 TCP 다시 시도 아이콘](./media/user-guide/netx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="11190-654">**Icon** ![Internal T C P retry icon](./media/user-guide/netx-events/image22.png)</span></span>

<span data-ttu-id="11190-655">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-655">**Description**</span></span>

<span data-ttu-id="11190-656">이 이벤트는 내부 NetX TCP 다시 시도 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-656">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="11190-657">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-657">**Information Fields**</span></span>
- <span data-ttu-id="11190-658">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-658">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-659">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-659">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-660">정보 필드 3: 타이머에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-660">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="11190-661">정보 필드 4: 다시 시도 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-661">Info Field 4: Number of retries</span></span>

### <a name="internal-tcp-state-change"></a><span data-ttu-id="11190-662">내부 TCP 상태 변경</span><span class="sxs-lookup"><span data-stu-id="11190-662">Internal TCP State Change</span></span> 

#### <a name="internal-tcp-state-change"></a><span data-ttu-id="11190-663">내부 TCP 상태 변경</span><span class="sxs-lookup"><span data-stu-id="11190-663">Internal TCP state change</span></span> 

<span data-ttu-id="11190-664">**아이콘** ![내부 TCP 상태 변경 아이콘](./media/user-guide/netx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="11190-664">**Icon** ![Internal T C P state change icon](./media/user-guide/netx-events/image23.png)</span></span>

<span data-ttu-id="11190-665">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-665">**Description**</span></span>

<span data-ttu-id="11190-666">이 이벤트는 내부 NetX TCP 소켓 상태 변경 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-666">This event represents an internal NetX TCP socket state change event.</span></span>

<span data-ttu-id="11190-667">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-667">**Information Fields**</span></span>

- <span data-ttu-id="11190-668">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-668">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-669">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-669">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-670">정보 필드 3: 이전 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-670">Info Field 3: Previous state</span></span>
- <span data-ttu-id="11190-671">정보 필드 4: 새 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-671">Info Field 4: New state</span></span>

### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="11190-672">내부 I/O 드라이버 패킷 송신</span><span class="sxs-lookup"><span data-stu-id="11190-672">Internal I/O Driver Packet Send</span></span> 

#### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="11190-673">내부 I/O 드라이버 패킷 송신</span><span class="sxs-lookup"><span data-stu-id="11190-673">Internal I/O driver packet send</span></span>

<span data-ttu-id="11190-674">**아이콘** ![내부 I/O 드라이버 패킷 송신 아이콘](./media/user-guide/netx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="11190-674">**Icon** ![Internal I / O driver packet send icon](./media/user-guide/netx-events/image24.png)</span></span>

<span data-ttu-id="11190-675">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-675">**Description**</span></span>

<span data-ttu-id="11190-676">이 이벤트는 내부 NetX I/O 드라이버 패킷 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-676">This event represents an internal NetX I/O driver packet send event.</span></span>

<span data-ttu-id="11190-677">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-677">**Information Fields**</span></span>

- <span data-ttu-id="11190-678">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-678">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-679">정보 필드 2: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-679">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="11190-680">정보 필드 3: 패킷 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-680">Info Field 3: Packet size</span></span>
- <span data-ttu-id="11190-681">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-681">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="11190-682">내부 I/O 드라이버 초기화</span><span class="sxs-lookup"><span data-stu-id="11190-682">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="11190-683">내부 I/O 드라이버 초기화</span><span class="sxs-lookup"><span data-stu-id="11190-683">Internal I/O driver initialize</span></span>

<span data-ttu-id="11190-684">**아이콘** ![내부 I/O 드라이버 초기화 아이콘](./media/user-guide/netx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="11190-684">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/netx-events/image25.png)</span></span>

<span data-ttu-id="11190-685">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-685">**Description**</span></span>

<span data-ttu-id="11190-686">이 이벤트는 내부 NetX I/O 드라이버 초기화 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-686">This event represents an internal NetX I/O driver initialize event.</span></span>

<span data-ttu-id="11190-687">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-687">**Information Fields**</span></span>

- <span data-ttu-id="11190-688">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-688">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="11190-689">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-689">Info Field 2: Not used.</span></span>
- <span data-ttu-id="11190-690">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-690">Info Field 3: Not used.</span></span>
- <span data-ttu-id="11190-691">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-691">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="11190-692">내부 I/O 드라이버 링크 사용</span><span class="sxs-lookup"><span data-stu-id="11190-692">Internal I/O Driver Link Enable</span></span> 

#### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="11190-693">내부 I/O 드라이버 링크 사용</span><span class="sxs-lookup"><span data-stu-id="11190-693">Internal I/O driver link enable</span></span>

<span data-ttu-id="11190-694">**아이콘** ![내부 I/O 드라이버 링크 사용 아이콘](./media/user-guide/netx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="11190-694">**Icon** ![Internal I / O driver link enable icon](./media/user-guide/netx-events/image26.png)</span></span>

<span data-ttu-id="11190-695">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-695">**Description**</span></span>

<span data-ttu-id="11190-696">이 이벤트는 내부 NetX I/O 드라이버 링크 사용 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-696">This event represents an internal NetX I/O driver link enable event.</span></span>

<span data-ttu-id="11190-697">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-697">**Information Fields**</span></span>

- <span data-ttu-id="11190-698">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-698">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="11190-699">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-699">Info Field 2: Not used.</span></span>
- <span data-ttu-id="11190-700">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-700">Info Field 3: Not used.</span></span>
- <span data-ttu-id="11190-701">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-701">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="11190-702">내부 I/O 드라이버 링크 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11190-702">Internal I/O Driver Link Disable</span></span> 

#### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="11190-703">내부 I/O 드라이버 링크 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11190-703">Internal I/O driver link disable</span></span>

<span data-ttu-id="11190-704">**아이콘** ![내부 I/O 드라이버 링크 사용 안 함 아이콘](./media/user-guide/netx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="11190-704">**Icon** ![Internal I / O driver link disable icon](./media/user-guide/netx-events/image27.png)</span></span>

<span data-ttu-id="11190-705">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-705">**Description**</span></span>

<span data-ttu-id="11190-706">이 이벤트는 내부 NetX I/O 드라이버 링크 사용 안 함 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-706">This event represents an internal NetX I/O driver link disable event.</span></span>

<span data-ttu-id="11190-707">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-707">**Information Fields**</span></span>

- <span data-ttu-id="11190-708">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-708">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-709">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-709">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-710">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-710">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-711">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-711">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="11190-712">내부 I/O 드라이버 패킷 브로드캐스트</span><span class="sxs-lookup"><span data-stu-id="11190-712">Internal I/O Driver Packet Broadcast</span></span> 

#### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="11190-713">내부 I/O 드라이버 패킷 브로드캐스트</span><span class="sxs-lookup"><span data-stu-id="11190-713">Internal I/O driver packet broadcast</span></span>

<span data-ttu-id="11190-714">**아이콘** ![내부 I/O 드라이버 패킷 브로드캐스트 아이콘](./media/user-guide/netx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="11190-714">**Icon** ![Internal I / O driver packet broadcast icon](./media/user-guide/netx-events/image28.png)</span></span>

<span data-ttu-id="11190-715">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-715">**Description**</span></span>

<span data-ttu-id="11190-716">이 이벤트는 내부 NetX I/O 드라이버 패킷 브로드캐스트 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-716">This event represents an internal NetX I/O driver packet broadcast event.</span></span>

<span data-ttu-id="11190-717">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-717">**Information Fields**</span></span>

- <span data-ttu-id="11190-718">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-718">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-719">정보 필드 2: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-719">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="11190-720">정보 필드 3: 패킷 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-720">Info Field 3: Packet size</span></span>
- <span data-ttu-id="11190-721">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-721">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="11190-722">내부 I/O 드라이버 ARP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-722">Internal I/O Driver ARP Send</span></span> 

#### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="11190-723">내부 I/O 드라이버 ARP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-723">Internal I/O driver ARP send</span></span>

<span data-ttu-id="11190-724">**아이콘** ![내부 I/O 드라이버 ARP 송신 아이콘](./media/user-guide/netx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="11190-724">**Icon** ![Internal I / O driver ARP send icon](./media/user-guide/netx-events/image29.png)</span></span>

<span data-ttu-id="11190-725">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-725">**Description**</span></span>

<span data-ttu-id="11190-726">이 이벤트는 내부 NetX I/O 드라이버 ARP 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-726">This event represents an internal NetX I/O driver ARP send event.</span></span>

<span data-ttu-id="11190-727">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-727">**Information Fields**</span></span>

- <span data-ttu-id="11190-728">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-728">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-729">정보 필드 2: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-729">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="11190-730">정보 필드 3: 패킷 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-730">Info Field 3: Packet size</span></span>
- <span data-ttu-id="11190-731">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-731">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="11190-732">내부 I/O 드라이버 ARP 응답 송신</span><span class="sxs-lookup"><span data-stu-id="11190-732">Internal I/O Driver ARP Response Send</span></span> 

#### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="11190-733">내부 I/O 드라이버 ARP 응답 송신</span><span class="sxs-lookup"><span data-stu-id="11190-733">Internal I/O driver ARP response send</span></span>

<span data-ttu-id="11190-734">**아이콘** ![내부 I/O 드라이버 ARP 응답 송신 아이콘](./media/user-guide/netx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="11190-734">**Icon** ![Internal I / O driver ARP response send icon](./media/user-guide/netx-events/image30.png)</span></span>

<span data-ttu-id="11190-735">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-735">**Description**</span></span>

<span data-ttu-id="11190-736">이 이벤트는 내부 NetX I/O 드라이버 ARP 응답 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-736">This event represents an internal NetX I/O driver ARP response send event.</span></span>

<span data-ttu-id="11190-737">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-737">**Information Fields**</span></span>

- <span data-ttu-id="11190-738">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-738">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-739">정보 필드 2: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-739">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="11190-740">정보 필드 3: 패킷 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-740">Info Field 3: Packet size</span></span>
- <span data-ttu-id="11190-741">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-741">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="11190-742">내부 I/O 드라이버 RARP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-742">Internal I/O Driver RARP Send</span></span> 

#### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="11190-743">내부 I/O 드라이버 RARP 송신</span><span class="sxs-lookup"><span data-stu-id="11190-743">Internal I/O driver RARP send</span></span>

<span data-ttu-id="11190-744">**아이콘** ![내부 I/O 드라이버 RARP 송신 아이콘](./media/user-guide/netx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="11190-744">**Icon** ![Internal I / O driver RARP send icon](./media/user-guide/netx-events/image31.png)</span></span>

<span data-ttu-id="11190-745">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-745">**Description**</span></span>

<span data-ttu-id="11190-746">이 이벤트는 내부 NetX I/O 드라이버 RARP 송신 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-746">This event represents an internal NetX I/O driver RARP send event.</span></span>

<span data-ttu-id="11190-747">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-747">**Information Fields**</span></span>

- <span data-ttu-id="11190-748">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-748">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-749">정보 필드 2: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-749">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="11190-750">정보 필드 3: 패킷 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-750">Info Field 3: Packet size</span></span>
- <span data-ttu-id="11190-751">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-751">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="11190-752">내부 I/O 드라이버 멀티캐스트 조인</span><span class="sxs-lookup"><span data-stu-id="11190-752">Internal I/O Driver Multicast Join</span></span> 

#### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="11190-753">내부 I/O 드라이버 멀티캐스트 조인</span><span class="sxs-lookup"><span data-stu-id="11190-753">Internal I/O driver multicast join</span></span>

<span data-ttu-id="11190-754">**아이콘** ![내부 I/O 드라이버 멀티캐스트 조인 아이콘](./media/user-guide/netx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="11190-754">**Icon** ![Internal I / O driver multicast join icon](./media/user-guide/netx-events/image32.png)</span></span>

<span data-ttu-id="11190-755">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-755">**Description**</span></span>

<span data-ttu-id="11190-756">이 이벤트는 내부 NetX I/O 드라이버 멀티캐스트 조인 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-756">This event represents an internal NetX I/O driver multicast join event.</span></span>

<span data-ttu-id="11190-757">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-757">**Information Fields**</span></span> 

- <span data-ttu-id="11190-758">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-758">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-759">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-759">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-760">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-760">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-761">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-761">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="11190-762">내부 I/O 드라이버 멀티캐스트 탈퇴</span><span class="sxs-lookup"><span data-stu-id="11190-762">Internal I/O Driver Multicast Leave</span></span> 

#### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="11190-763">내부 I/O 드라이버 멀티캐스트 탈퇴</span><span class="sxs-lookup"><span data-stu-id="11190-763">Internal I/O driver multicast leave</span></span>

<span data-ttu-id="11190-764">**아이콘** ![내부 I/O 드라이버 멀티캐스트 탈퇴 아이콘](./media/user-guide/netx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="11190-764">**Icon** ![Internal I / O driver multicast leave icon](./media/user-guide/netx-events/image33.png)</span></span>

<span data-ttu-id="11190-765">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-765">**Description**</span></span>

<span data-ttu-id="11190-766">이 이벤트는 내부 NetX I/O 드라이버 멀티캐스트 탈퇴 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-766">This event represents an internal NetX I/O driver multicast leave event.</span></span>

<span data-ttu-id="11190-767">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-767">**Information Fields**</span></span>

- <span data-ttu-id="11190-768">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-768">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-769">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-769">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-770">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-770">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-771">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-771">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-status"></a><span data-ttu-id="11190-772">내부 I/O 드라이버 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-772">Internal I/O Driver Get Status</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="11190-773">내부 I/O 드라이버 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-773">Internal I/O driver get status</span></span>

<span data-ttu-id="11190-774">**아이콘** ![내부 I/O 드라이버 상태 가져오기 아이콘](./media/user-guide/netx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="11190-774">**Icon** ![Internal I / O driver get status icon](./media/user-guide/netx-events/image34.png)</span></span>

<span data-ttu-id="11190-775">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-775">**Description**</span></span>

<span data-ttu-id="11190-776">이 이벤트는 내부 NetX I/O 드라이버 상태 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-776">This event represents an internal NetX I/O driver get status event.</span></span>

<span data-ttu-id="11190-777">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-777">**Information Fields**</span></span>

- <span data-ttu-id="11190-778">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-778">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-779">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-779">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-780">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-780">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-781">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-781">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="11190-782">내부 I/O 드라이버 속도 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-782">Internal I/O Driver Get Speed</span></span> 

#### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="11190-783">내부 I/O 드라이버 속도 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-783">Internal I/O driver get speed</span></span>

<span data-ttu-id="11190-784">**아이콘** ![내부 I/O 드라이버 속도 가져오기 아이콘](./media/user-guide/netx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="11190-784">**Icon** ![Internal I / O driver get speed icon](./media/user-guide/netx-events/image35.png)</span></span>

<span data-ttu-id="11190-785">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-785">**Description**</span></span>

<span data-ttu-id="11190-786">이 이벤트는 내부 NetX I/O 드라이버 속도 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-786">This event represents an internal NetX I/O driver get speed event.</span></span>

<span data-ttu-id="11190-787">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-787">**Information Fields**</span></span>

- <span data-ttu-id="11190-788">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-788">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-789">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-789">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-790">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-790">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-791">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-791">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="11190-792">내부 I/O 드라이버 이중 형식 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-792">Internal I/O Driver Get Duplex Type</span></span> 

#### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="11190-793">내부 I/O 드라이버 이중 형식 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-793">Internal I/O driver get duplex type</span></span>

<span data-ttu-id="11190-794">**아이콘** ![내부 I/O 드라이버 이중 형식 가져오기 아이콘](./media/user-guide/netx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="11190-794">**Icon** ![Internal I / O driver get duplex type icon](./media/user-guide/netx-events/image36.png)</span></span>

<span data-ttu-id="11190-795">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-795">**Description**</span></span>

<span data-ttu-id="11190-796">이 이벤트는 내부 NetX I/O 드라이버 이중 형식 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-796">This event represents an internal NetX I/O driver get duplex type event.</span></span>

<span data-ttu-id="11190-797">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-797">**Information Fields**</span></span> 

- <span data-ttu-id="11190-798">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-798">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-799">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-799">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-800">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-800">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-801">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-801">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="11190-802">내부 I/O 드라이버 오류 수 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-802">Internal I/O Driver Get Error Count</span></span>

#### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="11190-803">내부 I/O 드라이버 오류 수 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-803">Internal I/O driver get error count</span></span>

<span data-ttu-id="11190-804">**아이콘** ![내부 I/O 드라이버 오류 수 가져오기 아이콘](./media/user-guide/netx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="11190-804">**Icon** ![Internal I / O driver get error count icon](./media/user-guide/netx-events/image37.png)</span></span>

<span data-ttu-id="11190-805">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-805">**Description**</span></span>

<span data-ttu-id="11190-806">이 이벤트는 내부 NetX I/O 드라이버 오류 수 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-806">This event represents an internal NetX I/O driver get error count event.</span></span>

<span data-ttu-id="11190-807">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-807">**Information Fields**</span></span>

- <span data-ttu-id="11190-808">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-808">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-809">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-809">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-810">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-810">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-811">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-811">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="11190-812">내부 I/O 드라이버 RX 수 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-812">Internal I/O Driver Get RX Count</span></span> 

#### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="11190-813">내부 I/O 드라이버 RX 수 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-813">Internal I/O driver get RX count</span></span>

<span data-ttu-id="11190-814">**아이콘** ![내부 I/O 드라이버 RX 수 가져오기 아이콘](./media/user-guide/netx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="11190-814">**Icon** ![Internal I / O driver get RX count icon](./media/user-guide/netx-events/image38.png)</span></span>

<span data-ttu-id="11190-815">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-815">**Description**</span></span>

<span data-ttu-id="11190-816">이 이벤트는 내부 NetX I/O 드라이버 RX 수 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-816">This event represents an internal NetX I/O driver get RX count event.</span></span>

<span data-ttu-id="11190-817">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-817">**Information Fields**</span></span> 

- <span data-ttu-id="11190-818">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-818">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-819">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-819">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-820">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-820">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-821">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-821">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="11190-822">내부 I/O 드라이버 TX 수 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-822">Internal I/O Driver Get TX Count</span></span> 

#### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="11190-823">내부 I/O 드라이버 TX 수 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-823">Internal I/O driver get TX count</span></span>

<span data-ttu-id="11190-824">**아이콘** ![내부 I/O 드라이버 TX 수 가져오기 아이콘](./media/user-guide/netx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="11190-824">**Icon** ![Internal I / O driver get T X count icon](./media/user-guide/netx-events/image39.png)</span></span>

<span data-ttu-id="11190-825">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-825">**Description**</span></span>

<span data-ttu-id="11190-826">이 이벤트는 내부 NetX I/O 드라이버 TX 수 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-826">This event represents an internal NetX I/O driver get TX count event.</span></span>

<span data-ttu-id="11190-827">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-827">**Information Fields**</span></span>

- <span data-ttu-id="11190-828">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-828">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-829">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-829">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-830">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-830">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-831">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-831">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="11190-832">내부 I/O 드라이버 할당 오류 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-832">Internal I/O Driver Get Allocation Errors</span></span> 

#### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="11190-833">내부 I/O 드라이버 할당 오류 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-833">Internal I/O driver get allocation errors</span></span>

<span data-ttu-id="11190-834">**아이콘** ![내부 I/O 드라이버 할당 오류 가져오기 아이콘](./media/user-guide/netx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="11190-834">**Icon** ![Internal I / O driver get allocation errors icon](./media/user-guide/netx-events/image40.png)</span></span>

<span data-ttu-id="11190-835">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-835">**Description**</span></span>

<span data-ttu-id="11190-836">이 이벤트는 내부 NetX I/O 드라이버 할당 오류 가져오기 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-836">This event represents an internal NetX I/O driver get allocation errors event.</span></span>

<span data-ttu-id="11190-837">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-837">**Information Fields**</span></span> 

- <span data-ttu-id="11190-838">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-838">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-839">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-839">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-840">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-840">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-841">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-841">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="11190-842">내부 I/O 드라이버 초기화 취소</span><span class="sxs-lookup"><span data-stu-id="11190-842">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="11190-843">내부 I/O 드라이버 초기화 취소</span><span class="sxs-lookup"><span data-stu-id="11190-843">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="11190-844">**아이콘** ![내부 I/O 드라이버 초기화 취소 아이콘](./media/user-guide/netx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="11190-844">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/netx-events/image41.png)</span></span>

<span data-ttu-id="11190-845">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-845">**Description**</span></span>

<span data-ttu-id="11190-846">이 이벤트는 내부 NetX I/O 드라이버 초기화 취소 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-846">This event represents an internal NetX I/O driver un-initialize event.</span></span>

<span data-ttu-id="11190-847">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-847">**Information Fields**</span></span> 

- <span data-ttu-id="11190-848">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-848">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-849">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-849">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-850">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-850">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-851">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-851">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="11190-852">내부 I/O 드라이버 지연 처리</span><span class="sxs-lookup"><span data-stu-id="11190-852">Internal I/O Driver Deferred Processing</span></span> 

#### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="11190-853">내부 I/O 드라이버 지연 처리</span><span class="sxs-lookup"><span data-stu-id="11190-853">Internal I/O driver deferred processing</span></span> 

<span data-ttu-id="11190-854">**아이콘** ![내부 I/O 드라이버 지연 처리 아이콘](./media/user-guide/netx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="11190-854">**Icon** ![Internal I / O driver deferred processing icon](./media/user-guide/netx-events/image42.png)</span></span>

<span data-ttu-id="11190-855">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-855">**Description**</span></span>

<span data-ttu-id="11190-856">이 이벤트는 내부 NetX I/O 드라이버 지연 처리 이벤트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-856">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="11190-857">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-857">**Information Fields**</span></span>

- <span data-ttu-id="11190-858">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-858">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-859">정보 필드 2: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-859">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="11190-860">정보 필드 3: 패킷 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-860">Info Field 3: Packet length</span></span>
- <span data-ttu-id="11190-861">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-861">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entries-invalidate"></a><span data-ttu-id="11190-862">ARP 동적 항목 무효화</span><span class="sxs-lookup"><span data-stu-id="11190-862">ARP Dynamic Entries Invalidate</span></span> 

#### <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="11190-863">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="11190-863">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="11190-864">**아이콘** ![ARP 동적 항목 무효화 아이콘](./media/user-guide/netx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="11190-864">**Icon** ![A R P Dynamic Entries Invalidate icon](./media/user-guide/netx-events/image43.png)</span></span>

<span data-ttu-id="11190-865">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-865">**Description**</span></span>

<span data-ttu-id="11190-866">이 이벤트는 nx_arp_dynamic_entries_invalidate를 통한 모든 동적 ARP의 무효화를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-866">This event represents invalidating all dynamic ARP entires via nx_arp_dynamic_entries_invalidate.</span></span>

<span data-ttu-id="11190-867">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-867">**Information Fields**</span></span> 

- <span data-ttu-id="11190-868">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-868">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-869">정보 필드 2: 무효화된 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-869">Info Field 2: Entries invalidated</span></span>
- <span data-ttu-id="11190-870">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-870">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-871">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-871">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entry-set"></a><span data-ttu-id="11190-872">ARP 동적 항목 설정</span><span class="sxs-lookup"><span data-stu-id="11190-872">ARP Dynamic Entry Set</span></span> 

#### <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="11190-873">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="11190-873">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="11190-874">**아이콘** ![ARP 동적 항목 설정 아이콘](./media/user-guide/netx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="11190-874">**Icon** ![A R P Dynamic Entry Set icon](./media/user-guide/netx-events/image44.png)</span></span>

<span data-ttu-id="11190-875">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-875">**Description**</span></span>

<span data-ttu-id="11190-876">이 이벤트는 nx_arp_dynamic_entry_set을 통한 동적 ARP 항목 설정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-876">This event represents setting a dynamic ARP entry via nx_arp_dynamic_entry_set.</span></span>

<span data-ttu-id="11190-877">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-877">**Information Fields**</span></span> 

- <span data-ttu-id="11190-878">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-878">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-879">정보 필드 2: IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-879">Info Field 2: IP address</span></span>
- <span data-ttu-id="11190-880">정보 필드 3: 실제 주소(MSW)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-880">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="11190-881">정보 필드 4: 실제 주소(LSW)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-881">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-enable"></a><span data-ttu-id="11190-882">ARP 사용</span><span class="sxs-lookup"><span data-stu-id="11190-882">ARP Enable</span></span> 

#### <a name="nx_arp_enable"></a><span data-ttu-id="11190-883">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="11190-883">nx_arp_enable</span></span>

<span data-ttu-id="11190-884">**아이콘** ![ARP 사용 아이콘](./media/user-guide/netx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="11190-884">**Icon** ![A R P enable icon](./media/user-guide/netx-events/image45.png)</span></span>

<span data-ttu-id="11190-885">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-885">**Description**</span></span>

<span data-ttu-id="11190-886">이 이벤트는 nx_arp_enable은 통한 ARP 사용 설정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-886">This event represents enabling ARP via nx_arp_enable.</span></span>

<span data-ttu-id="11190-887">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-887">**Information Fields**</span></span> 

- <span data-ttu-id="11190-888">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-888">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-889">정보 필드 2: ARP 캐시 메모리 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-889">Info Field 2: ARP cache memory pointer</span></span>
- <span data-ttu-id="11190-890">정보 필드 3: ARP 캐시 메모리 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-890">Info Field 3: ARP cache memory size</span></span>
- <span data-ttu-id="11190-891">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-891">Info Field 4: Not used</span></span>

### <a name="arp-gratuitous-send"></a><span data-ttu-id="11190-892">ARP 무상 송신</span><span class="sxs-lookup"><span data-stu-id="11190-892">ARP Gratuitous Send</span></span> 

#### <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="11190-893">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="11190-893">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="11190-894">**아이콘** ![ARP의 무상 송신 아이콘](./media/user-guide/netx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="11190-894">**Icon** ![A R P gratuitous send icon](./media/user-guide/netx-events/image46.png)</span></span>

<span data-ttu-id="11190-895">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-895">**Description**</span></span>

<span data-ttu-id="11190-896">이 이벤트는 nx_arp_gratuitous_send를 통한 무상 ARP 송신을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-896">This event represents a gratuitous ARP send via nx_arp_gratuitous_send.</span></span>

<span data-ttu-id="11190-897">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-897">**Information Fields**</span></span>

- <span data-ttu-id="11190-898">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-898">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-899">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-899">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-900">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-900">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-901">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-901">Info Field 4: Not used</span></span>

### <a name="arp-hardware-address-find"></a><span data-ttu-id="11190-902">ARP 하드웨어 주소 찾기</span><span class="sxs-lookup"><span data-stu-id="11190-902">ARP Hardware Address Find</span></span> 

#### <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="11190-903">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="11190-903">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="11190-904">**아이콘** ![ARP 하드웨어 주소 찾기 아이콘](./media/user-guide/netx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="11190-904">**Icon** ![A R P Hardware Address Find icon](./media/user-guide/netx-events/image47.png)</span></span>

<span data-ttu-id="11190-905">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-905">**Description**</span></span>

<span data-ttu-id="11190-906">이 이벤트는 nx_arp_hardware_address_find를 통한 실제 주소를 찾기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-906">This event represents finding a physical address via nx_arp_hardware_address_find.</span></span>

<span data-ttu-id="11190-907">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-907">**Information Fields**</span></span> 

- <span data-ttu-id="11190-908">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-908">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-909">정보 필드 2: IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-909">Info Field 2: IP address</span></span>
- <span data-ttu-id="11190-910">정보 필드 3: 실제 주소(MSW)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-910">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="11190-911">정보 필드 4: 실제 주소(LSW)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-911">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-information-get"></a><span data-ttu-id="11190-912">ARP 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-912">ARP Information Get</span></span> 

#### <a name="nx_arp_info_get"></a><span data-ttu-id="11190-913">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="11190-913">nx_arp_info_get</span></span>

<span data-ttu-id="11190-914">**아이콘** ![ARP 정보 가져오기 아이콘](./media/user-guide/netx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="11190-914">**Icon** ![A R P informition get icon](./media/user-guide/netx-events/image48.png)</span></span>

<span data-ttu-id="11190-915">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-915">**Description**</span></span>

<span data-ttu-id="11190-916">이 이벤트는 nx_arp_info_get을 통한 정보 가져오기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-916">This event represents getting information via nx_arp_info_get.</span></span>

<span data-ttu-id="11190-917">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-917">**Information Fields**</span></span> 

- <span data-ttu-id="11190-918">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-918">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-919">정보 필드 2: 송신된 ARP입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-919">Info Field 2: ARPs sent</span></span>
- <span data-ttu-id="11190-920">정보 필드 3: ARP 응답입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-920">Info Field 3: ARP responses</span></span>
- <span data-ttu-id="11190-921">정보 필드 4: 수신된 ARP입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-921">Info Field 4: ARPs received</span></span>

### <a name="arp-ip-address-find"></a><span data-ttu-id="11190-922">ARP IP 주소 찾기</span><span class="sxs-lookup"><span data-stu-id="11190-922">ARP IP Address Find</span></span> 

#### <a name="nx_arp_ip_address_find"></a><span data-ttu-id="11190-923">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="11190-923">nx_arp_ip_address_find</span></span>

<span data-ttu-id="11190-924">**아이콘** ![ARP IP 주소 찾기 아이콘](./media/user-guide/netx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="11190-924">**Icon** ![A R P I P address find icon](./media/user-guide/netx-events/image49.png)</span></span>

<span data-ttu-id="11190-925">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-925">**Description**</span></span>

<span data-ttu-id="11190-926">이 이벤트는 nx_arp_ip_address_find를 통해 제공된 실제 주소와 연결된 IP 주소 찾기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-926">This event represents finding an IP address associated with the supplied physical address via nx_arp_ip_address_find.</span></span>

<span data-ttu-id="11190-927">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-927">**Information Fields**</span></span> 

- <span data-ttu-id="11190-928">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-928">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-929">정보 필드 2: IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-929">Info Field 2: IP address</span></span>
- <span data-ttu-id="11190-930">정보 필드 3: 실제 주소(MSW)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-930">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="11190-931">정보 필드 4: 실제 주소(LSW)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-931">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entry-create"></a><span data-ttu-id="11190-932">ARP 정적 항목 만들기</span><span class="sxs-lookup"><span data-stu-id="11190-932">ARP Static Entry Create</span></span> 

#### <a name="nx_arp_static_entry_create"></a><span data-ttu-id="11190-933">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="11190-933">nx_arp_static_entry_create</span></span>

<span data-ttu-id="11190-934">**아이콘** ![ARP 정적 항목 만들기 아이콘](./media/user-guide/netx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="11190-934">**Icon** ![A R P static entry create icon](./media/user-guide/netx-events/image50.png)</span></span>

<span data-ttu-id="11190-935">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-935">**Description**</span></span>

<span data-ttu-id="11190-936">이 이벤트는 nx_arp_static_entry_create를 통한 정적 ARP 항목 만들기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-936">This event represents creating a static ARP entry via nx_arp_static_entry_create.</span></span>

<span data-ttu-id="11190-937">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-937">**Information Fields**</span></span>

- <span data-ttu-id="11190-938">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-938">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-939">정보 필드 2: IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-939">Info Field 2: IP address</span></span>
- <span data-ttu-id="11190-940">정보 필드 3: 실제 주소(MSW)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-940">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="11190-941">정보 필드 4: 실제 주소(LSW)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-941">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entries-delete"></a><span data-ttu-id="11190-942">ARP 정적 항목 삭제</span><span class="sxs-lookup"><span data-stu-id="11190-942">ARP Static Entries Delete</span></span> 

#### <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="11190-943">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="11190-943">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="11190-944">**아이콘** ![ARP 정적 항목 삭제 아이콘](./media/user-guide/netx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="11190-944">**Icon** ![A R P static entries delete icon](./media/user-guide/netx-events/image51.png)</span></span>

<span data-ttu-id="11190-945">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-945">**Description**</span></span>

<span data-ttu-id="11190-946">이 이벤트는 nx_arp_static_entries_delete를 통한 모든 ARP 정적 항목 삭제를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-946">This event represents deleting all ARP static entries via nx_arp_static_entries_delete.</span></span>

<span data-ttu-id="11190-947">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-947">**Information Fields**</span></span> 

- <span data-ttu-id="11190-948">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-948">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-949">정보 필드 2: 삭제된 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-949">Info Field 2: Entries deleted</span></span>
- <span data-ttu-id="11190-950">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-950">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-951">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-951">Info Field 4: Not used</span></span>

### <a name="arp-static-entry-delete"></a><span data-ttu-id="11190-952">ARP 정적 항목 삭제</span><span class="sxs-lookup"><span data-stu-id="11190-952">ARP Static Entry Delete</span></span> 

### <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="11190-953">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="11190-953">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="11190-954">**아이콘** ![ARP 정적 항목 삭제 아이콘](./media/user-guide/netx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="11190-954">**Icon** ![A R P static entry delete icon](./media/user-guide/netx-events/image52.png)</span></span>

<span data-ttu-id="11190-955">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-955">**Description**</span></span>

<span data-ttu-id="11190-956">이 이벤트는 nx_arp_static_entry_delete을 통한 정적 ARP 항목 삭제를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-956">This event represents deleting a static ARP entry via nx_arp_static_entry_delete.</span></span>

<span data-ttu-id="11190-957">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-957">**Information Fields**</span></span> 

- <span data-ttu-id="11190-958">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-958">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-959">정보 필드 2: IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-959">Info Field 2: IP address</span></span>
- <span data-ttu-id="11190-960">정보 필드 3: 실제 주소(MSW)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-960">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="11190-961">정보 필드 4: 실제 주소(LSW)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-961">Info Field 4: Physical address (LSW)</span></span>

### <a name="duo-cache-entry-delete"></a><span data-ttu-id="11190-962">Duo 캐시 항목 삭제</span><span class="sxs-lookup"><span data-stu-id="11190-962">Duo Cache Entry Delete</span></span> 

#### <a name="nxd_und_cache_entry_delete"></a><span data-ttu-id="11190-963">nxd_und_cache_entry_delete</span><span class="sxs-lookup"><span data-stu-id="11190-963">nxd_und_cache_entry_delete</span></span>

<span data-ttu-id="11190-964">**아이콘** ![Duo 캐시 항목 삭제 아이콘](./media/user-guide/netx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="11190-964">**Icon** ![Duo cache entry delete icon](./media/user-guide/netx-events/image53.png)</span></span>

<span data-ttu-id="11190-965">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-965">**Description**</span></span>

<span data-ttu-id="11190-966">이 이벤트는 nx_udp_socket_create를 통한 인접 캐시 테이블의 항목 삭제를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-966">This event represents deleting an entry in the neighbor cache table via nx_udp_socket_create.</span></span>

<span data-ttu-id="11190-967">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-967">**Information Fields**</span></span> 

- <span data-ttu-id="11190-968">정보 필드 1: 삭제할 IPv6 링크 로컬 주소의 네 번째(가장 덜 중요함) 단어입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-968">Info Field 1: Fourth (least significant) word of the IPv6 link local address to delete</span></span>
- <span data-ttu-id="11190-969">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-969">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-970">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-970">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-971">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-971">Info Field 4: Not used</span></span>

### <a name="duo-cache-entry-set"></a><span data-ttu-id="11190-972">Duo 캐시 항목 설정</span><span class="sxs-lookup"><span data-stu-id="11190-972">Duo Cache Entry Set</span></span> 

#### <a name="nxd_nd_cache_entry_set"></a><span data-ttu-id="11190-973">nxd_nd_cache_entry_set</span><span class="sxs-lookup"><span data-stu-id="11190-973">nxd_nd_cache_entry_set</span></span>

<span data-ttu-id="11190-974">**아이콘** ![Duo 캐시 항목 설정 아이콘](./media/user-guide/netx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="11190-974">**Icon** ![Duo cache entry set icon](./media/user-guide/netx-events/image54.png)</span></span>

<span data-ttu-id="11190-975">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-975">**Description**</span></span>

<span data-ttu-id="11190-976">이 이벤트는 nxd_nd_cache_entry_set을 통해 캐시 항목을 만들고 인접 캐시 테이블에 추가하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-976">This event represents creating a cache entry and adding to the neighbor cache table via nxd_nd_cache_entry_set.</span></span>

<span data-ttu-id="11190-977">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-977">**Information Fields**</span></span> 

- <span data-ttu-id="11190-978">정보 필드 1: 추가할 IPv6 주소의 네 번째(가장 덜 중요함) 단어입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-978">Info Field 1: Fourth (least significant) word of the IPv6 address to add</span></span>
- <span data-ttu-id="11190-979">정보 필드 2: 실제 주소 msb입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-979">Info Field 2: Physical address msb</span></span>
- <span data-ttu-id="11190-980">정보 필드 3: 실제 주소 lsb입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-980">Info Field 3: Physical address lsb</span></span>
- <span data-ttu-id="11190-981">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-981">Info Field 4: Not used</span></span>

### <a name="duo-cache-invalidate"></a><span data-ttu-id="11190-982">Duo 캐시 무효화</span><span class="sxs-lookup"><span data-stu-id="11190-982">Duo Cache Invalidate</span></span> 

#### <a name="nxd_nd_cache_invalidate"></a><span data-ttu-id="11190-983">nxd_nd_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="11190-983">nxd_nd_cache_invalidate</span></span>

<span data-ttu-id="11190-984">**아이콘** ![Duo 캐시 무효화 아이콘](./media/user-guide/netx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="11190-984">**Icon** ![Duo cache invalidate icon](./media/user-guide/netx-events/image55.png)</span></span>

<span data-ttu-id="11190-985">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-985">**Description**</span></span>

<span data-ttu-id="11190-986">이 이벤트는 nxd_nd_cache_invalidate를 통해 전체 인접 캐시 테이블을 무효화함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-986">This event represents invalidating the entire neighbor cache table via nxd_nd_cache_invalidate.</span></span>

<span data-ttu-id="11190-987">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-987">**Information Fields**</span></span>

- <span data-ttu-id="11190-988">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-988">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-989">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-989">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-990">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-990">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-991">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-991">Info Field 4: Not used</span></span>

### <a name="duo-cache-ip-address-find"></a><span data-ttu-id="11190-992">Duo 캐시 IP 주소 찾기</span><span class="sxs-lookup"><span data-stu-id="11190-992">Duo Cache IP Address Find</span></span> 

#### <a name="nxd_nd_cache_ip_address_find"></a><span data-ttu-id="11190-993">nxd_nd_cache_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="11190-993">nxd_nd_cache_ip_address_find</span></span>

<span data-ttu-id="11190-994">**아이콘** ![Duo 캐시 IP 주소 찾기 아이콘](./media/user-guide/netx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="11190-994">**Icon** ![Duo cache I P address find icon](./media/user-guide/netx-events/image56.png)</span></span>

<span data-ttu-id="11190-995">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-995">**Description**</span></span>

<span data-ttu-id="11190-996">이 이벤트는 nxd_nd_cache_ip_address_find를 통해 캐시 테이블에서 제공된 실제 주소와 일치하는 IP 주소를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-996">This event represents retrieving an IP address matching the supplied physical address from the cache table via nxd_nd_cache_ip_address_find.</span></span>

<span data-ttu-id="11190-997">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-997">**Information Fields**</span></span>

- <span data-ttu-id="11190-998">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-998">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-999">정보 필드 2: IPv6 주소의 네 번째(가장 덜 중요함) 단어입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-999">Info Field 2: Fourth (least significant) word of the IPv6 address</span></span>
- <span data-ttu-id="11190-1000">정보 필드 3: 실제 주소 msb입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1000">Info Field 3: Physical address msb</span></span>
- <span data-ttu-id="11190-1001">정보 필드 4: 실제 주소 lsb입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1001">Info Field 4: Physical address lsb</span></span>

### <a name="duo-icmp-enable"></a><span data-ttu-id="11190-1002">Duo ICMP 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1002">Duo ICMP Enable</span></span> 

#### <a name="nxd_icmp_enable"></a><span data-ttu-id="11190-1003">nxd_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1003">nxd_icmp_enable</span></span>

<span data-ttu-id="11190-1004">**아이콘** ![Duo ICMP 사용 아이콘](./media/user-guide/netx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1004">**Icon** ![Duo I C M P enable icon](./media/user-guide/netx-events/image57.png)</span></span>

<span data-ttu-id="11190-1005">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1005">**Description**</span></span>

<span data-ttu-id="11190-1006">이 이벤트는 nxd_icmp_enable을 통해 지정된 IP 인스턴스에서 ICMPv4 및 ICMPv6 서비스를 사용하도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1006">This event represents ICMPv4 and ICMPv6 services being enabled on the specified IP instance via nxd_icmp_enable.</span></span>

<span data-ttu-id="11190-1007">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1007">**Information Fields**</span></span>
- <span data-ttu-id="11190-1008">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1008">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1009">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1009">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1010">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1010">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1011">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1011">Info Field 4: Not used</span></span>

### <a name="duo-icmp-ping"></a><span data-ttu-id="11190-1012">Duo ICMP Ping</span><span class="sxs-lookup"><span data-stu-id="11190-1012">Duo ICMP Ping</span></span> 

#### <a name="nxd_icmp_ping"></a><span data-ttu-id="11190-1013">nxd_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="11190-1013">nxd_icmp_ping</span></span>

<span data-ttu-id="11190-1014">**아이콘** ![Duo ICMP Ping 아이콘](./media/user-guide/netx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1014">**Icon** ![Duo I C M P ping icon](./media/user-guide/netx-events/image58.png)</span></span>

<span data-ttu-id="11190-1015">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1015">**Description**</span></span>

<span data-ttu-id="11190-1016">이 이벤트는 nxd_icmp_ping을 통해 IPv6 호스트에 ping(에코 요청)을 보내는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1016">This event represents sending a ping (echo request) to an IPv6 host via nxd_icmp_ping.</span></span>

<span data-ttu-id="11190-1017">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1017">**Information Fields**</span></span>

- <span data-ttu-id="11190-1018">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1018">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1019">정보 필드 2: IPv6 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1019">Info Field 2: IPv6 address</span></span>
- <span data-ttu-id="11190-1020">정보 필드 3: 에코 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1020">Info Field 3: Pointer to echo data</span></span>
- <span data-ttu-id="11190-1021">정보 필드 4: 에코 데이터의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1021">Info Field 4: Size of echo data</span></span>

### <a name="duo-ip-max-payload-size-find"></a><span data-ttu-id="11190-1022">Duo IP 최대 페이로드 크기 찾기</span><span class="sxs-lookup"><span data-stu-id="11190-1022">Duo IP Max Payload Size Find</span></span> 

#### <a name="nxd_ip_max_payload_size"></a><span data-ttu-id="11190-1023">nxd_ip_max_payload_size</span><span class="sxs-lookup"><span data-stu-id="11190-1023">nxd_ip_max_payload_size</span></span>

<span data-ttu-id="11190-1024">**아이콘** ![Duo IP 최대 페이로드 크기 찾기 아이콘](./media/user-guide/netx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1024">**Icon** ![Duo I P max payload size find icon](./media/user-guide/netx-events/image59.png)</span></span>

<span data-ttu-id="11190-1025">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1025">**Description**</span></span>

<span data-ttu-id="11190-1026">이 이벤트는 지정된 패킷이 조각화를 요구하지 않고 수행할 수 있는 최대 페이로드를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1026">This event computes the max payload the specified packet can carry without requiring fragmentation.</span></span>

<span data-ttu-id="11190-1027">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1027">**Information Fields**</span></span>

- <span data-ttu-id="11190-1028">정보 필드 1: 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1028">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="11190-1029">정보 필드 2: 피어 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1029">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="11190-1030">정보 필드 3: 피어 포트입니다. 정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1030">Info Field 3: Peer port Info Field 4: Not used</span></span>

### <a name="duo-ip-raw-packet-send"></a><span data-ttu-id="11190-1031">Duo IP 원시 패킷 송신</span><span class="sxs-lookup"><span data-stu-id="11190-1031">Duo IP Raw Packet Send</span></span> 

#### <a name="nxd_ip_max_packet_send"></a><span data-ttu-id="11190-1032">nxd_ip_max_packet_send</span><span class="sxs-lookup"><span data-stu-id="11190-1032">nxd_ip_max_packet_send</span></span>

<span data-ttu-id="11190-1033">**아이콘** ![Duo IP 원시 패킷 송신 아이콘](./media/user-guide/netx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1033">**Icon** ![Duo I P raw packet send icon](./media/user-guide/netx-events/image60.png)</span></span>

<span data-ttu-id="11190-1034">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1034">**Description**</span></span>

<span data-ttu-id="11190-1035">이 이벤트는 nxd_ip_raw_packet_send를 통해 지정된 네트워크 인터페이스 외부의 원시 IP 패킷을 제공된 IP 대상으로 송신하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1035">This event represents sending a raw IP packet out the specified network interface to the supplied IP destination addressvia nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="11190-1036">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1036">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1037">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1037">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1038">정보 필드 2: 송신할 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1038">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="11190-1039">정보 필드 3: 대상 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1039">Info Field 3: Pointer to destination address</span></span>
- <span data-ttu-id="11190-1040">정보 필드 4: 패킷 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1040">Info Field 4: Packet protocol</span></span>

### <a name="duo-ipv6-default-router-add"></a><span data-ttu-id="11190-1041">Duo IPv6 기본 라우터 추가</span><span class="sxs-lookup"><span data-stu-id="11190-1041">Duo IPv6 Default Router Add</span></span> 

#### <a name="nxd_ipv6_default_router_add"></a><span data-ttu-id="11190-1042">nxd_ipv6_default_router_add</span><span class="sxs-lookup"><span data-stu-id="11190-1042">nxd_ipv6_default_router_add</span></span>

<span data-ttu-id="11190-1043">**아이콘** ![Duo IPv6 기본 라우터 추가 아이콘](./media/user-guide/netx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1043">**Icon** ![Duo I P v 6 default router add icon](./media/user-guide/netx-events/image61.png)</span></span>

<span data-ttu-id="11190-1044">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1044">**Description**</span></span>

<span data-ttu-id="11190-1045">이 이벤트는 nxd_ipv6_default_router_add를 통해 IP 인스턴스의 IPv6 라우팅 테이블에 기본 라우터를 추가하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1045">This event represents adding a default router to the IP instance's IPv6 routing table via nxd_ipv6_default_router_add.</span></span>

<span data-ttu-id="11190-1046">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1046">**Information Fields**</span></span>

- <span data-ttu-id="11190-1047">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1047">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="11190-1048">정보 필드 2: 대상 네트워크 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1048">Info Field 2: Destination Network address.</span></span>
- <span data-ttu-id="11190-1049">정보 필드 3: 수명 시간 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1049">Info Field 3: Life time information.</span></span>
- <span data-ttu-id="11190-1050">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1050">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-default-router-delete"></a><span data-ttu-id="11190-1051">Duo IPv6 기본 라우터 삭제</span><span class="sxs-lookup"><span data-stu-id="11190-1051">Duo IPv6 Default Router Delete</span></span> 

#### <a name="nxd_ipv6_default_router_delete"></a><span data-ttu-id="11190-1052">nxd_ipv6_default_router_delete</span><span class="sxs-lookup"><span data-stu-id="11190-1052">nxd_ipv6_default_router_delete</span></span>

<span data-ttu-id="11190-1053">**아이콘** ![Duo IPv6 기본 라우터 삭제 아이콘](./media/user-guide/netx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1053">**Icon** ![Duo I P v 6 default router delete icon](./media/user-guide/netx-events/image62.png)</span></span>

<span data-ttu-id="11190-1054">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1054">**Description**</span></span>

<span data-ttu-id="11190-1055">이 이벤트는 nxd_ipv6_default_router_delete를 통해 IP 인스턴스의 IPv6 라우팅 테이블에서 기본 라우터를 제거하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1055">This event represents removing a default router from the IP instance's IPv6 routing table via nxd_ipv6_default_router_delete.</span></span>

<span data-ttu-id="11190-1056">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1056">**Information Fields**</span></span>

- <span data-ttu-id="11190-1057">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1057">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="11190-1058">정보 필드 2: 기본 라우터 IPv6 주소의 네 번째 단어(가장 덜 중요함)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1058">Info Field 2: Fourth word (least significant) of the default router IPv6 address.</span></span>
- <span data-ttu-id="11190-1059">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="11190-1060">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1060">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-enable"></a><span data-ttu-id="11190-1061">Duo IPv6 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1061">Duo IPv6 Enable</span></span> 

#### <a name="nxd_ipv6_enable"></a><span data-ttu-id="11190-1062">nxd_ipv6_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1062">nxd_ipv6_enable</span></span>

<span data-ttu-id="11190-1063">**아이콘** ![Duo IPv6 사용 아이콘](./media/user-guide/netx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1063">**Icon** ![Duo I P v 6 enable icon](./media/user-guide/netx-events/image63.png)</span></span>

<span data-ttu-id="11190-1064">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1064">**Description**</span></span>

<span data-ttu-id="11190-1065">이 이벤트는 nxd_ipv6_enable을 통해 제공된 IP 인스턴스에서 IPv6 서비스를 사용하도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1065">This event represents enabling IPv6 services on the supplied IP instance via nxd_ipv6_enable.</span></span>

<span data-ttu-id="11190-1066">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1066">**Information Fields**</span></span>

- <span data-ttu-id="11190-1067">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1067">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1068">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1068">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1069">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1069">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1070">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1070">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-global-address-get"></a><span data-ttu-id="11190-1071">Duo IPv6 전체 주소 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1071">Duo IPv6 Global Address Get</span></span> 

#### <a name="nxd_ipv6_global_address_get"></a><span data-ttu-id="11190-1072">nxd_ipv6_global_address_get</span><span class="sxs-lookup"><span data-stu-id="11190-1072">nxd_ipv6_global_address_get</span></span>

<span data-ttu-id="11190-1073">**아이콘** ![Duo IPv6 전체 주소 가져오기 아이콘](./media/user-guide/netx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1073">**Icon** ![Duo I P v 6 global address get icon](./media/user-guide/netx-events/image64.png)</span></span>

<span data-ttu-id="11190-1074">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1074">**Description**</span></span>

<span data-ttu-id="11190-1075">이 이벤트는 nxd_ipv6_global_address_get을 통해 IP 인스턴스 인터페이스 테이블의 인덱스 1에 있는 IP 인스턴스에서 전체(기본) IP 주소를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1075">This event represents retrieving the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_get.</span></span>

<span data-ttu-id="11190-1076">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1076">**Information Fields**</span></span>

- <span data-ttu-id="11190-1077">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1077">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="11190-1078">정보 필드 2: 전체 주소의 네 번째 단어(가장 덜 중요함)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1078">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="11190-1079">정보 필드 3: IPv6 주소 접두사 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1079">Info Field 3: IPv6 address prefix length.</span></span>
- <span data-ttu-id="11190-1080">정보 필드 4: IP 인터페이스 테이블에 대한 인덱스(1)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1080">Info Field 4: Index into IP interface table (1).</span></span>

### <a name="duo-ipv6-global-address-set"></a><span data-ttu-id="11190-1081">Duo IPv6 전체 주소 설정</span><span class="sxs-lookup"><span data-stu-id="11190-1081">Duo IPv6 Global Address Set</span></span> 

#### <a name="nxd_ipv6_global_address_set"></a><span data-ttu-id="11190-1082">nxd_ipv6_global_address_set</span><span class="sxs-lookup"><span data-stu-id="11190-1082">nxd_ipv6_global_address_set</span></span>

<span data-ttu-id="11190-1083">**아이콘** ![Duo IPv6 전체 주소 설정 아이콘](./media/user-guide/netx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1083">**Icon** ![Duo I P v 6 global address set icon](./media/user-guide/netx-events/image65.png)</span></span>

<span data-ttu-id="11190-1084">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1084">**Description**</span></span>

<span data-ttu-id="11190-1085">이 이벤트는 nxd_ipv6_global_address_set을 통해 IP 인스턴스 인터페이스 테이블의 인덱스 1에 있는 IP 인스턴스에서 전체(기본) IP 주소를 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1085">This event represents setting the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_set.</span></span>

<span data-ttu-id="11190-1086">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1086">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1087">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1087">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1088">정보 필드 2: 전체 주소의 네 번째 단어(가장 덜 중요함)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1088">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="11190-1089">정보 필드 3: IPv6 주소 접두사 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1089">Info Field 3: IPv6 address prefix length</span></span>
- <span data-ttu-id="11190-1090">정보 필드 4: IP 인터페이스 테이블에 대한 인덱스(1)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1090">Info Field 4: Index into IP interface table (1)</span></span>

### <a name="duo-ipv6-initiate-dad-process"></a><span data-ttu-id="11190-1091">Duo IPv6 DAD 프로세스 시작</span><span class="sxs-lookup"><span data-stu-id="11190-1091">Duo IPv6 Initiate Dad Process</span></span> 

#### <a name="nxd_ipv6_initiate_dad_process"></a><span data-ttu-id="11190-1092">nxd_ipv6_initiate_dad_process</span><span class="sxs-lookup"><span data-stu-id="11190-1092">nxd_ipv6_initiate_dad_process</span></span>

<span data-ttu-id="11190-1093">**아이콘** ![Duo IPv6 DAD 프로세스 시작 아이콘](./media/user-guide/netx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1093">**Icon** ![Duo I P v 6 initiate dad process icon](./media/user-guide/netx-events/image66.png)</span></span>

<span data-ttu-id="11190-1094">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1094">**Description**</span></span>

<span data-ttu-id="11190-1095">이 이벤트는 nxd_ipv6_initiate_dad_process를 통해 IP 인스턴스에 링크 로컬 또는 IP 인터페이스 주소가 할당될 때 DAD(중복 주소 검색) 프로세스의 시작을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1095">This event represents the start of the Duplicate Address Detection (DAD) process when the IP instance is assigned a link local or an IP interface address via nxd_ipv6_initiate_dad_process.</span></span>

<span data-ttu-id="11190-1096">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1096">**Information Fields**</span></span>

- <span data-ttu-id="11190-1097">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1097">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1098">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1098">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1099">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1099">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1100">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1100">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-interface-address-get"></a><span data-ttu-id="11190-1101">Duo IPv6 인터페이스 주소 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1101">Duo IPv6 Interface Address Get</span></span> 

#### <a name="nxd_ipv6_interface_address_get"></a><span data-ttu-id="11190-1102">nxd_ipv6_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="11190-1102">nxd_ipv6_interface_address_get</span></span>

<span data-ttu-id="11190-1103">**아이콘** ![Duo IPv6 인터페이스 주소 가져오기 아이콘](./media/user-guide/netx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1103">**Icon** ![Duo I P v 6 interface address get icon](./media/user-guide/netx-events/image67.png)</span></span>

<span data-ttu-id="11190-1104">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1104">**Description**</span></span>

<span data-ttu-id="11190-1105">이 이벤트는 지정된 인덱스의 IP 주소 및 접두사를 nxd_ipv6_interface_address_get을 통해 IP 인스턴스 인터페이스 주소 테이블로 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1105">This event represents retrieving the IP address and prefix at the specified index into the IP instance interface address table via nxd_ipv6_interface_address_get.</span></span>

<span data-ttu-id="11190-1106">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1106">**Information Fields**</span></span>

- <span data-ttu-id="11190-1107">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1107">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1108">정보 필드 2: 반환할 IPv6 주소의 네 번째 단어(가장 덜 중요함)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1108">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="11190-1109">정보 필드 4: IP 인스턴스 인터페이스 테이블로의 인터페이스 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1109">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-interface-address-set"></a><span data-ttu-id="11190-1110">Duo IPv6 인터페이스 주소 설정</span><span class="sxs-lookup"><span data-stu-id="11190-1110">Duo IPv6 Interface Address Set</span></span> 

### <a name="nxd_ipv6_interface_address_set"></a><span data-ttu-id="11190-1111">nxd_ipv6_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="11190-1111">nxd_ipv6_interface_address_set</span></span>

<span data-ttu-id="11190-1112">**아이콘** ![Duo IPv6 인터페이스 주소 설정 아이콘](./media/user-guide/netx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1112">**Icon** ![Duo I P v 6 interface addresss et icon](./media/user-guide/netx-events/image68.png)</span></span>

<span data-ttu-id="11190-1113">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1113">**Description**</span></span>

<span data-ttu-id="11190-1114">이 이벤트는 지정된 인덱스의 IP 주소 및 접두사를 IP 인스턴스 인터페이스 주소 테이블로 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1114">This event represents setting the IP address and prefix at the specified index into the IP instance interface address table.</span></span> <span data-ttu-id="11190-1115">nxd_ipv6_interface_address_set을 통해 인덱스 0(링크 로컬 주소)에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1115">Not permitted on index zero (link local address) via nxd_ipv6_interface_address_set.</span></span>

<span data-ttu-id="11190-1116">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1116">**Information Fields**</span></span>

- <span data-ttu-id="11190-1117">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1117">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1118">정보 필드 2: 반환할 IPv6 주소의 네 번째 단어(가장 덜 중요함)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1118">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="11190-1119">정보 필드 3: 접두사 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1119">Info Field 3: Prefix length</span></span>
- <span data-ttu-id="11190-1120">정보 필드 4: IP 인스턴스 인터페이스 테이블로의 인터페이스 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1120">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-link-local-address-get"></a><span data-ttu-id="11190-1121">Duo IPv6 링크 로컬 주소 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1121">Duo IPv6 Link Local Address Get</span></span> 

#### <a name="nxd_ipv6_linklocal_address_get"></a><span data-ttu-id="11190-1122">nxd_ipv6_linklocal_address_get</span><span class="sxs-lookup"><span data-stu-id="11190-1122">nxd_ipv6_linklocal_address_get</span></span>

<span data-ttu-id="11190-1123">**아이콘** ![Duo IPv6 링크 로컬 주소 가져오기 아이콘](./media/user-guide/netx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1123">**Icon** ![Duo I P v 6 link local address get icon](./media/user-guide/netx-events/image69.png)</span></span>

<span data-ttu-id="11190-1124">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1124">**Description**</span></span>

<span data-ttu-id="11190-1125">이 이벤트는 nxd_ipv6_linklocal_address_get을 통해 지정된 IP 인스턴스의 링크 로컬 주소를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1125">This event represents retrieving the link local address of the specified IP instance via nxd_ipv6_linklocal_address_get.</span></span>

<span data-ttu-id="11190-1126">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1126">**Information Fields**</span></span>

- <span data-ttu-id="11190-1127">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1127">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1128">정보 필드 2: IPv6 링크 로컬 주소의 네 번째 단어(가장 덜 중요함)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1128">Info Field 2: Fourth word (least significant) of the IP v6 link local address</span></span>
- <span data-ttu-id="11190-1129">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1129">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1130">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1130">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-link-local-address-set"></a><span data-ttu-id="11190-1131">Duo IPv6 링크 로컬 주소 설정</span><span class="sxs-lookup"><span data-stu-id="11190-1131">Duo IPv6 Link Local Address Set</span></span> 

#### <a name="nxd_ipv6_linklocal_address_set"></a><span data-ttu-id="11190-1132">nxd_ipv6_linklocal_address_set</span><span class="sxs-lookup"><span data-stu-id="11190-1132">nxd_ipv6_linklocal_address_set</span></span>

<span data-ttu-id="11190-1133">**아이콘** ![Duo IPv6 링크 로컬 주소 설정 아이콘](./media/user-guide/netx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1133">**Icon** ![Duo I P v 6 link local address set icon](./media/user-guide/netx-events/image70.png)</span></span>

<span data-ttu-id="11190-1134">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1134">**Description**</span></span>

<span data-ttu-id="11190-1135">이 이벤트는 nxd_ipv6_linklocal_address_set을 통해 IP 인스턴스의 링크 로컬 주소를 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1135">This event represents setting the link local address of the IP instance via nxd_ipv6_linklocal_address_set.</span></span>

<span data-ttu-id="11190-1136">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1136">**Information Fields**</span></span>

- <span data-ttu-id="11190-1137">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1137">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1138">정보 필드 2: IPv6 링크 로컬 주소의 네 번째(가장 덜 중요함) 단어입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1138">Info Field 2: Fourth (least significant) word of the IPv6 link local address</span></span>
- <span data-ttu-id="11190-1139">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1139">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1140">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1140">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-raw-packet-send"></a><span data-ttu-id="11190-1141">Duo IPv6 원시 패킷 송신</span><span class="sxs-lookup"><span data-stu-id="11190-1141">Duo IPv6 Raw Packet Send</span></span> 

#### <a name="nxd_ipv6_raw_packet_send"></a><span data-ttu-id="11190-1142">nxd_ipv6_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="11190-1142">nxd_ipv6_raw_packet_send</span></span>

<span data-ttu-id="11190-1143">**아이콘** ![Duo IPv6 원시 패킷 송신 아이콘](./media/user-guide/netx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1143">**Icon** ![Duo I P v 6 raw packet send icon](./media/user-guide/netx-events/image71.png)</span></span>

<span data-ttu-id="11190-1144">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1144">**Description**</span></span>

<span data-ttu-id="11190-1145">이 이벤트는 nxd_ip_raw_packet_send를 통해 원시 IP 패킷을 기본 IP 인터페이스를 통해 지정 대상으로 송신하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1145">This event represents sending a raw IP packet through the primary IP interface to the speficied destination via nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="11190-1146">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1146">**Information Fields**</span></span>

- <span data-ttu-id="11190-1147">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1147">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1148">정보 필드 2: 송신할 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1148">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="11190-1149">정보 필드 3: 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1149">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="11190-1150">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1150">Info Field 4: Not used</span></span>

### <a name="duo-tcp-socket-peer-info-get"></a><span data-ttu-id="11190-1151">Duo TCP 소켓 피어 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1151">Duo TCP Socket Peer Info Get</span></span> 

#### <a name="nxd_tcp_socket_peer_info_get"></a><span data-ttu-id="11190-1152">nxd_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="11190-1152">nxd_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="11190-1153">**아이콘** ![Duo TCP 소켓 피어 정보 가져오기 아이콘](./media/user-guide/netx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1153">**Icon** ![Duo T C P socket peer info get icon](./media/user-guide/netx-events/image72.png)</span></span>

<span data-ttu-id="11190-1154">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1154">**Description**</span></span>

<span data-ttu-id="11190-1155">이 이벤트는 지정된 소켓의 수신된 TCP 패킷에서 발신자 데이터를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1155">This event extracts the sender data from a received TCP packet on the specified socket.</span></span> <span data-ttu-id="11190-1156">발신자의 IP 주소와 포트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1156">It returns the IP address and port of the sender.</span></span>

<span data-ttu-id="11190-1157">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1157">**Information Fields**</span></span>

- <span data-ttu-id="11190-1158">정보 필드 1: 소켓 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1158">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="11190-1159">정보 필드 2: 피어 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1159">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="11190-1160">정보 필드 3: 피어 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1160">Info Field 3: Peer port</span></span>
- <span data-ttu-id="11190-1161">정보 필드 4: IP 주소의 가장 덜 중요한 32비트입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1161">Info Field 4: The lease significant 32-bit of the IP address</span></span>

### <a name="duo-tcp-socket-set-interface"></a><span data-ttu-id="11190-1162">Duo TCP 소켓 설정 인터페이스</span><span class="sxs-lookup"><span data-stu-id="11190-1162">Duo TCP Socket Set Interface</span></span> 

#### <a name="nxd_tcp_socket_set_interface"></a><span data-ttu-id="11190-1163">nxd_tcp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="11190-1163">nxd_tcp_socket_set_interface</span></span>

<span data-ttu-id="11190-1164">**아이콘** ![Duo TCP 소켓 설정 인터페이스 아이콘](./media/user-guide/netx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1164">**Icon** ![Duo T C P socket set interface icon](./media/user-guide/netx-events/image73.png)</span></span>

<span data-ttu-id="11190-1165">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1165">**Description**</span></span>

<span data-ttu-id="11190-1166">이 이벤트는 클라이언트가 nxd_tcp_client_socket_connect를 통해 지정된 서버 IP 주소에 있는 TCP 서버와 연결된 후 나가는 소켓 인터페이스를 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1166">This event represents setting the outgoing socket interface after a client connects with a TCP server on the specified server IP address via nxd_tcp_client_socket_connect.</span></span>

<span data-ttu-id="11190-1167">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1167">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1168">정보 필드 1: TCP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1168">Info Field 1: Pointer to TCP Socket</span></span>
- <span data-ttu-id="11190-1169">정보 필드 2: 인터페이스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1169">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="11190-1170">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1170">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1171">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1171">Info Field 4: Not used</span></span>

### <a name="duo-udp-socket-send"></a><span data-ttu-id="11190-1172">Duo UDP 소켓 송신</span><span class="sxs-lookup"><span data-stu-id="11190-1172">Duo UDP Socket Send</span></span> 

#### <a name="nxd_udp_socket_send"></a><span data-ttu-id="11190-1173">nxd_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="11190-1173">nxd_udp_socket_send</span></span>

<span data-ttu-id="11190-1174">**아이콘** ![Duo UDP 소켓 송신 아이콘](./media/user-guide/netx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1174">**Icon** ![Duo U D P socket send icon](./media/user-guide/netx-events/image74.png)</span></span>

<span data-ttu-id="11190-1175">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1175">**Description**</span></span>

<span data-ttu-id="11190-1176">이 이벤트는 nxd_udp_socket_send를 통해 입력 IP 주소와 포트를 사용하여 지정된 소켓을 통해 UDP 패킷을 송신하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1176">This event represents sending a UDP packet through the specified socket with the input IP address and port via nxd_udp_socket_send.</span></span>

<span data-ttu-id="11190-1177">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1177">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1178">정보 필드 1: 포인터 UDP 소켓입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1178">Info Field 1: Pointer UDP Socket</span></span>
- <span data-ttu-id="11190-1179">정보 필드 2: UDP 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1179">Info Field 2: Pointer to UDP packet</span></span>
- <span data-ttu-id="11190-1180">정보 필드 3: 패킷 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1180">Info Field 3: Packet length</span></span>
- <span data-ttu-id="11190-1181">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1181">Info Field 4: Not used</span></span>


### <a name="duo-udp-socket-set-interface"></a><span data-ttu-id="11190-1182">Duo UDP 소켓 설정 인터페이스</span><span class="sxs-lookup"><span data-stu-id="11190-1182">Duo UDP Socket Set Interface</span></span> 

#### <a name="nxd_udp_socket_set_interface"></a><span data-ttu-id="11190-1183">nxd_udp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="11190-1183">nxd_udp_socket_set_interface</span></span>

<span data-ttu-id="11190-1184">**아이콘** ![Duo UDP 소켓 설정 인터페이스 아이콘](./media/user-guide/netx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1184">**Icon** ![Duo U D P socket set interface icon](./media/user-guide/netx-events/image75.png)</span></span>

<span data-ttu-id="11190-1185">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1185">**Description**</span></span>

<span data-ttu-id="11190-1186">이 이벤트는 지정된 UDP 소켓 송신 인터페이스를 nxd_udp_socket_set_interface를 통해 입력 인터페이스 ID에 해당하는 인터페이스로 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1186">This event represents setting the specified UDP socket outgoing interface to the interface corresponding to the input interface ID via nxd_udp_socket_set_interface.</span></span>

<span data-ttu-id="11190-1187">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1187">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1188">정보 필드 1: UDP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1188">Info Field 1: Pointer to UDP Socket</span></span>
- <span data-ttu-id="11190-1189">정보 필드 2: 인터페이스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1189">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="11190-1190">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1190">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1191">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1191">Info Field 4: Not used</span></span>

### <a name="duo-udp-source-extract"></a><span data-ttu-id="11190-1192">Duo UDP 원본 추출</span><span class="sxs-lookup"><span data-stu-id="11190-1192">Duo UDP Source Extract</span></span> 

#### <a name="nxd_udp_socket_extract"></a><span data-ttu-id="11190-1193">nxd_udp_socket_extract</span><span class="sxs-lookup"><span data-stu-id="11190-1193">nxd_udp_socket_extract</span></span>

<span data-ttu-id="11190-1194">**아이콘** ![Duo UDP 원본 추출 아이콘](./media/user-guide/netx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1194">**Icon** ![Duo U D P source extract icon](./media/user-guide/netx-events/image76.png)</span></span>

<span data-ttu-id="11190-1195">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1195">**Description**</span></span>

<span data-ttu-id="11190-1196">이 이벤트는 수신한 패킷의 IP 주소와 원본 포트(IPv4 또는 IPv6)를 추출하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1196">This event represents extracting the IP address and source port of a received packet (either IPv4 or IPv6).</span></span> <span data-ttu-id="11190-1197">IPv6의 경우 IP 주소의 네 번째 단어(가장 덜 중요함)는 nxd_udp_source_extract를 통해 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1197">If IPv6, the fourth word (least significant) of the IP address is returned via nxd_udp_source_extract.</span></span>

<span data-ttu-id="11190-1198">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1198">**Information Fields**</span></span>

- <span data-ttu-id="11190-1199">정보 필드 1: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1199">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="11190-1200">정보 필드 2: IP 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1200">Info Field 2: IP version</span></span>
- <span data-ttu-id="11190-1201">정보 필드 3: 원본 IP 주소(IPv4 또는 IPv6)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1201">Info Field 3: Source IP address (IPv4 or IPv6)</span></span>
- <span data-ttu-id="11190-1202">정보 필드 4: 원본 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1202">Info Field 4: Source port</span></span>

### <a name="icmp-enable"></a><span data-ttu-id="11190-1203">ICMP 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1203">ICMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="11190-1204">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1204">nx_icmp_enable</span></span>

<span data-ttu-id="11190-1205">**아이콘** ![ICMP 사용 아이콘](./media/user-guide/netx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1205">**Icon** ![I C M P enable icon](./media/user-guide/netx-events/image77.png)</span></span>

<span data-ttu-id="11190-1206">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1206">**Description**</span></span>

<span data-ttu-id="11190-1207">이 이벤트는 nx_icmp_enable을 통해 ICMP를 사용하도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1207">This event represents enabling ICMP via nx_icmp_enable.</span></span>

<span data-ttu-id="11190-1208">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1208">**Information Fields**</span></span>

- <span data-ttu-id="11190-1209">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1209">Info Field 1: Pointer to the IP instance l;</span></span>
- <span data-ttu-id="11190-1210">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1210">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1211">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1211">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1212">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1212">Info Field 4: Not used</span></span>

### <a name="icmp-information-get"></a><span data-ttu-id="11190-1213">ICMP 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1213">ICMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="11190-1214">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="11190-1214">nx_icmp_info_get</span></span>

<span data-ttu-id="11190-1215">**아이콘** ![ICMP 정보 가져오기 아이콘](./media/user-guide/netx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1215">**Icon** ![I C M P information get icon](./media/user-guide/netx-events/image78.png)</span></span>

<span data-ttu-id="11190-1216">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1216">**Description**</span></span>

<span data-ttu-id="11190-1217">이 이벤트는 nx_icmp_info_get을 통한 정보 가져오기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1217">This event represents getting information via nx_icmp_info_get.</span></span>

<span data-ttu-id="11190-1218">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1218">**Information Fields**</span></span>
- <span data-ttu-id="11190-1219">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1219">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1220">정보 필드 2: 송신된 Ping입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1220">Info Field 2: Pings sent</span></span>
- <span data-ttu-id="11190-1221">정보 필드 3: Ping 응답입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1221">Info Field 3: Ping responses</span></span>
- <span data-ttu-id="11190-1222">정보 필드 4: 수신된 Ping입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1222">Info Field 4: Pings received</span></span>

### <a name="icmp-ping"></a><span data-ttu-id="11190-1223">ICMP Ping</span><span class="sxs-lookup"><span data-stu-id="11190-1223">ICMP Ping</span></span> 

#### <a name="nx_icmp_ping"></a><span data-ttu-id="11190-1224">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="11190-1224">nx_icmp_ping</span></span>

<span data-ttu-id="11190-1225">**아이콘** ![ICMP Ping 아이콘](./media/user-guide/netx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1225">**Icon** ![I C M P ping icon](./media/user-guide/netx-events/image79.png)</span></span>

<span data-ttu-id="11190-1226">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1226">**Description**</span></span>

<span data-ttu-id="11190-1227">이 이벤트는 nx_icmp_ping을 통해 대상 IP 주소를 ping하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1227">This event represents pinging a target IP address via nx_icmp_ping.</span></span>

<span data-ttu-id="11190-1228">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1228">**Information Fields**</span></span>

- <span data-ttu-id="11190-1229">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1229">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1230">정보 필드 2: IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1230">Info Field 2: IP address</span></span>
- <span data-ttu-id="11190-1231">정보 필드 3: 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1231">Info Field 3: Pointer to data</span></span>
- <span data-ttu-id="11190-1232">정보 필드 4: 데이터의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1232">Info Field 4: Size of data</span></span>

### <a name="igmp-enable"></a><span data-ttu-id="11190-1233">IGMP 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1233">IGMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="11190-1234">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1234">nx_icmp_enable</span></span>

<span data-ttu-id="11190-1235">**아이콘** ![IGMP 사용 아이콘](./media/user-guide/netx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1235">**Icon** ![I G M P enable icon](./media/user-guide/netx-events/image80.png)</span></span>

<span data-ttu-id="11190-1236">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1236">**Description**</span></span>

<span data-ttu-id="11190-1237">이 이벤트는 nx_igmp_enable을 통해 IGMP를 사용하도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1237">This event represents enabling IGMP via nx_igmp_enable.</span></span>

<span data-ttu-id="11190-1238">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1238">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1239">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1239">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1240">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1240">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1241">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1241">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1242">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1242">Info Field 4: Not used</span></span>

### <a name="igmp-information-get"></a><span data-ttu-id="11190-1243">IGMP 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1243">IGMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="11190-1244">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="11190-1244">nx_icmp_info_get</span></span>

<span data-ttu-id="11190-1245">**아이콘** ![IGMP 정보 가져오기 아이콘](./media/user-guide/netx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1245">**Icon** ![I G M P information get icon](./media/user-guide/netx-events/image81.png)</span></span>

<span data-ttu-id="11190-1246">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1246">**Description**</span></span>

<span data-ttu-id="11190-1247">이 이벤트는 nx_igmp_info_get을 통한 정보 가져오기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1247">This event represents getting information via nx_igmp_info_get.</span></span>

<span data-ttu-id="11190-1248">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1248">**Information Fields**</span></span>

- <span data-ttu-id="11190-1249">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1249">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1250">정보 필드 2: 송신된 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1250">Info Field 2: Reports sent</span></span>
- <span data-ttu-id="11190-1251">정보 필드 3: 수신된 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1251">Info Field 3: Queries received</span></span>
- <span data-ttu-id="11190-1252">정보 필드 4: 조인된 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1252">Info Field 4: Groups joined</span></span>

### <a name="igmp-loopback-disable"></a><span data-ttu-id="11190-1253">IGMP 루프백 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11190-1253">IGMP Loopback Disable</span></span> 

#### <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="11190-1254">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="11190-1254">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="11190-1255">**아이콘** ![IGMP 루프백 사용 안 함 아이콘](./media/user-guide/netx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1255">**Icon** ![I G M P loopback disable icon](./media/user-guide/netx-events/image82.png)</span></span>

<span data-ttu-id="11190-1256">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1256">**Description**</span></span>

<span data-ttu-id="11190-1257">이 이벤트는 nx_igmp_loopback_disable를 통해 IGMP 루프백을 사용하지 않도록 설정함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1257">This event represents disabling IGMP loopback via nx_igmp_loopback_disable.</span></span>

<span data-ttu-id="11190-1258">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1258">**Information Fields**</span></span>

- <span data-ttu-id="11190-1259">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1259">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1260">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1260">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1261">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1261">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1262">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1262">Info Field 4: Not used</span></span>

### <a name="igmp-loopback-enable"></a><span data-ttu-id="11190-1263">IGMP 루프백 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1263">IGMP Loopback Enable</span></span> 

#### <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="11190-1264">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1264">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="11190-1265">**아이콘** ![IGMP 루프백 사용 아이콘](./media/user-guide/netx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1265">**Icon** ![I G M P loopback enable icon](./media/user-guide/netx-events/image83.png)</span></span>

<span data-ttu-id="11190-1266">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1266">**Description**</span></span>

<span data-ttu-id="11190-1267">이 이벤트는 nx_igmp_loopback_enable를 통해 IGMP 루프백을 사용하도록 설정함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1267">This event represents enabling IGMP loopback via nx_igmp_loopback_enable.</span></span>

<span data-ttu-id="11190-1268">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1268">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1269">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1269">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1270">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1270">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1271">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1271">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1272">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1272">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-join"></a><span data-ttu-id="11190-1273">IGMP 멀티캐스트 조인</span><span class="sxs-lookup"><span data-stu-id="11190-1273">IGMP Multicast Join</span></span> 

#### <a name="nx_igmp_multicast_join"></a><span data-ttu-id="11190-1274">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="11190-1274">nx_igmp_multicast_join</span></span>

<span data-ttu-id="11190-1275">**아이콘** ![IGMP 멀티캐스트 조인 아이콘](./media/user-guide/netx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1275">**Icon** ![I G M P multicast join icon](./media/user-guide/netx-events/image84.png)</span></span>

<span data-ttu-id="11190-1276">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1276">**Description**</span></span>

<span data-ttu-id="11190-1277">이 이벤트는 nx_igmp_multicast_join을 통해 멀티캐스트 그룹을 조인하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1277">This event represents joining a multicast group via nx_igmp_multicast_join.</span></span>

<span data-ttu-id="11190-1278">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1278">**Information Fields**</span></span>

- <span data-ttu-id="11190-1279">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1279">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1280">정보 필드 2: 그룹 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1280">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="11190-1281">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1281">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1282">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1282">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-leave"></a><span data-ttu-id="11190-1283">IGMP 멀티캐스트 탈퇴</span><span class="sxs-lookup"><span data-stu-id="11190-1283">IGMP Multicast Leave</span></span> 

#### <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="11190-1284">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="11190-1284">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="11190-1285">**아이콘** ![IGMP 멀티캐스트 탈퇴 아이콘](./media/user-guide/netx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1285">**Icon** ![I G M P multicast leave icon](./media/user-guide/netx-events/image85.png)</span></span>

<span data-ttu-id="11190-1286">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1286">**Description**</span></span>

<span data-ttu-id="11190-1287">이 이벤트는 nx_igmp_multicast_leave를 통해 멀티캐스트 그룹을 탈퇴하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1287">This event represents leaving a multicast group via nx_igmp_multicast_leave.</span></span>

<span data-ttu-id="11190-1288">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1288">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1289">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1289">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1290">정보 필드 2: 그룹 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1290">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="11190-1291">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1291">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1292">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1292">Info Field 4: Not used</span></span>

### <a name="ip-address-change-notify"></a><span data-ttu-id="11190-1293">IP 주소 변경 알림</span><span class="sxs-lookup"><span data-stu-id="11190-1293">IP Address Change Notify</span></span> 

#### <a name="nx_ip_address_change_notify"></a><span data-ttu-id="11190-1294">nx_ip_address_change_notify</span><span class="sxs-lookup"><span data-stu-id="11190-1294">nx_ip_address_change_notify</span></span>

<span data-ttu-id="11190-1295">**아이콘** ![IP 주소 변경 알림 아이콘](./media/user-guide/netx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1295">**Icon** ![I P address change notify icon](./media/user-guide/netx-events/image86.png)</span></span>

<span data-ttu-id="11190-1296">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1296">**Description**</span></span>

<span data-ttu-id="11190-1297">이 이벤트는 nx_ip_address_change_notify를 통해 IP 변경 알림에 등록하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1297">This event represents registering for IP change notification via nx_ip_address_change_notify.</span></span>

<span data-ttu-id="11190-1298">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1298">**Information Fields**</span></span>

- <span data-ttu-id="11190-1299">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1299">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1300">정보 필드 2: 콜백 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1300">Info Field 2: Callback function pointer</span></span>
- <span data-ttu-id="11190-1301">정보 필드 3: 추가 정보 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1301">Info Field 3: Additional information pointer</span></span>
- <span data-ttu-id="11190-1302">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1302">Info Field 4: Not used</span></span>

### <a name="ip-address-get"></a><span data-ttu-id="11190-1303">IP 주소 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1303">IP Address Get</span></span> 

#### <a name="nx_ip_address_get"></a><span data-ttu-id="11190-1304">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="11190-1304">nx_ip_address_get</span></span>

<span data-ttu-id="11190-1305">**아이콘** ![IP 주소 가져오기 아이콘](./media/user-guide/netx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1305">**Icon** ![I P address get icon](./media/user-guide/netx-events/image87.png)</span></span>

<span data-ttu-id="11190-1306">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1306">**Description**</span></span>

<span data-ttu-id="11190-1307">이 이벤트는 nx_ip_address_get을 통해 IP 주소를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1307">This event represents getting the IP address via nx_ip_address_get.</span></span>

<span data-ttu-id="11190-1308">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1308">**Information Fields**</span></span>

- <span data-ttu-id="11190-1309">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1309">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1310">정보 필드 2: IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1310">Info Field 2: IP address</span></span>
- <span data-ttu-id="11190-1311">정보 필드 3: 네트워크 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1311">Info Field 3: Network mask</span></span>
- <span data-ttu-id="11190-1312">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1312">Info Field 4: Not used</span></span>

### <a name="ip-address-set"></a><span data-ttu-id="11190-1313">IP 주소 설정</span><span class="sxs-lookup"><span data-stu-id="11190-1313">IP Address Set</span></span> 

#### <a name="nx_ip_address_set"></a><span data-ttu-id="11190-1314">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="11190-1314">nx_ip_address_set</span></span>

<span data-ttu-id="11190-1315">**아이콘** ![IP 주소 설정 아이콘](./media/user-guide/netx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1315">**Icon** ![I P address set icon](./media/user-guide/netx-events/image88.png)</span></span>

<span data-ttu-id="11190-1316">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1316">**Description**</span></span>

<span data-ttu-id="11190-1317">이 이벤트는 nx_ip_address_set을 통해 IP 주소를 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1317">This event represents setting the IP address via nx_ip_address_set.</span></span>

<span data-ttu-id="11190-1318">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1318">**Information Fields**</span></span>

- <span data-ttu-id="11190-1319">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1319">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1320">정보 필드 2: IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1320">Info Field 2: IP address</span></span>
- <span data-ttu-id="11190-1321">정보 필드 3: 네트워크 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1321">Info Field 3: Network mask</span></span>
- <span data-ttu-id="11190-1322">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1322">Info Field 4: Not used</span></span>

### <a name="ip-create"></a><span data-ttu-id="11190-1323">IP 만들기</span><span class="sxs-lookup"><span data-stu-id="11190-1323">IP Create</span></span> 

#### <a name="nx_ip_create"></a><span data-ttu-id="11190-1324">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="11190-1324">nx_ip_create</span></span>

<span data-ttu-id="11190-1325">**아이콘** ![IP 만들기 아이콘](./media/user-guide/netx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1325">**Icon** ![I P create icon](./media/user-guide/netx-events/image89.png)</span></span>

<span data-ttu-id="11190-1326">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1326">**Description**</span></span>

<span data-ttu-id="11190-1327">이 이벤트는 nx_ip_create를 통해 IP 인스턴스를 만드는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1327">This event represents creating an IP instance via nx_ip_create.</span></span>

<span data-ttu-id="11190-1328">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1328">**Information Fields**</span></span> 
- <span data-ttu-id="11190-1329">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1329">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1330">정보 필드 2: IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1330">Info Field 2: IP address</span></span>
- <span data-ttu-id="11190-1331">정보 필드 3: 네트워크 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1331">Info Field 3: Network mask</span></span>
- <span data-ttu-id="11190-1332">정보 필드 4: 기본 패킷 풀 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1332">Info Field 4: Default packet pool pointer</span></span>

### <a name="ip-delete"></a><span data-ttu-id="11190-1333">IP 삭제</span><span class="sxs-lookup"><span data-stu-id="11190-1333">IP Delete</span></span> 

#### <a name="nx_ip_delete"></a><span data-ttu-id="11190-1334">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="11190-1334">nx_ip_delete</span></span>

<span data-ttu-id="11190-1335">**아이콘** ![IP 삭제 아이콘](./media/user-guide/netx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1335">**Icon** ![I P delete icon](./media/user-guide/netx-events/image90.png)</span></span>

<span data-ttu-id="11190-1336">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1336">**Description**</span></span>

<span data-ttu-id="11190-1337">이 이벤트는 nx_ip_delete를 통해 IP 인스턴스를 삭제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1337">This event represents deleting an IP instance via nx_ip_delete.</span></span>

<span data-ttu-id="11190-1338">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1338">**Information Fields**</span></span>

- <span data-ttu-id="11190-1339">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1339">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1340">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1340">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1341">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1341">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1342">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1342">Info Field 4: Not used</span></span>

### <a name="ip-driver-direct-command"></a><span data-ttu-id="11190-1343">IP 드라이버 직접 명령</span><span class="sxs-lookup"><span data-stu-id="11190-1343">IP Driver Direct Command</span></span> 

#### <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="11190-1344">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="11190-1344">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="11190-1345">**아이콘** ![IP 드라이버 직접 명령 아이콘](./media/user-guide/netx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1345">**Icon** ![I P driver direct command icon](./media/user-guide/netx-events/image91.png)</span></span>

<span data-ttu-id="11190-1346">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1346">**Description**</span></span>

<span data-ttu-id="11190-1347">이 이벤트는 nx_ip_driver_direct_command를 통한 직접 I/O 드라이버 명령을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1347">This event represents a direct I/O driver command via nx_ip_driver_direct_command.</span></span>

<span data-ttu-id="11190-1348">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1348">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1349">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1349">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1350">정보 필드 2: 드라이버 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1350">Info Field 2: Driver command</span></span>
- <span data-ttu-id="11190-1351">정보 필드 3: 반환 값입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1351">Info Field 3: Return value</span></span>
- <span data-ttu-id="11190-1352">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1352">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-disable"></a><span data-ttu-id="11190-1353">IP 전달 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11190-1353">IP Forwarding Disable</span></span> 

#### <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="11190-1354">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="11190-1354">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="11190-1355">**아이콘** ![IP 전달 사용 안 함 아이콘](./media/user-guide/netx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1355">**Icon** ![I P forwarding disable icon](./media/user-guide/netx-events/image92.png)</span></span>

<span data-ttu-id="11190-1356">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1356">**Description**</span></span>

<span data-ttu-id="11190-1357">이 이벤트는 nx_ip_forwarding_disable을 통해 IP 전달을 사용하지 않도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1357">This event represents disabling IP forwarding via nx_ip_forwarding_disable.</span></span>

<span data-ttu-id="11190-1358">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1358">**Information Fields**</span></span>

- <span data-ttu-id="11190-1359">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1359">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1360">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1360">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1361">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1361">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1362">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1362">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-enable"></a><span data-ttu-id="11190-1363">IP 전달 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1363">IP Forwarding Enable</span></span> 

#### <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="11190-1364">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1364">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="11190-1365">**아이콘** ![IP 전달 사용 아이콘](./media/user-guide/netx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1365">**Icon** ![I P forwarding enable icon](./media/user-guide/netx-events/image93.png)</span></span>

<span data-ttu-id="11190-1366">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1366">**Description**</span></span>

<span data-ttu-id="11190-1367">이 이벤트는 nx_ip_forwarding_enable을 통해 IP 전달을 사용하도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1367">This event represents enabling IP forwarding via nx_ip_forwarding_enable.</span></span>

<span data-ttu-id="11190-1368">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1368">**Information Fields**</span></span>

- <span data-ttu-id="11190-1369">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1369">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1370">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1370">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1371">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1371">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1372">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1372">Info Field 4: Not used</span></span>

### <a name="ip-fragment-disable"></a><span data-ttu-id="11190-1373">IP 조각 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11190-1373">IP Fragment Disable</span></span> 

#### <a name="nx_ip_fragment_disable"></a><span data-ttu-id="11190-1374">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="11190-1374">nx_ip_fragment_disable</span></span>

<span data-ttu-id="11190-1375">**아이콘** ![IP 조각 사용 안 함 아이콘](./media/user-guide/netx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1375">**Icon** ![I P fragment disable icon](./media/user-guide/netx-events/image94.png)</span></span>

<span data-ttu-id="11190-1376">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1376">**Description**</span></span>

<span data-ttu-id="11190-1377">이 이벤트는 nx_ip_fragment_disable을 통해 IP 조각화를 사용하지 않도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1377">This event represents disabling IP fragmenting via nx_ip_fragment_disable.</span></span>

<span data-ttu-id="11190-1378">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1378">**Information Fields**</span></span>

- <span data-ttu-id="11190-1379">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1379">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1380">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1380">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1381">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1381">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1382">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1382">Info Field 4: Not used</span></span>

### <a name="ip-fragment-enable"></a><span data-ttu-id="11190-1383">IP 조각 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1383">IP Fragment Enable</span></span> 

#### <a name="nx_ip_fragment_enable"></a><span data-ttu-id="11190-1384">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1384">nx_ip_fragment_enable</span></span>

<span data-ttu-id="11190-1385">**아이콘** ![IP 조각 사용 아이콘](./media/user-guide/netx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1385">**Icon** ![I P fragment enable icon](./media/user-guide/netx-events/image95.png)</span></span>

<span data-ttu-id="11190-1386">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1386">**Description**</span></span>

<span data-ttu-id="11190-1387">이 이벤트는 nx_ip_fragment_enable을 통해 IP 조각화를 사용하도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1387">This event represents enabling IP fragmenting via nx_ip_fragment_enable.</span></span>

<span data-ttu-id="11190-1388">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1388">**Information Fields**</span></span>

- <span data-ttu-id="11190-1389">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1389">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1390">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1390">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1391">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1391">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1392">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1392">Info Field 4: Not used</span></span>

### <a name="ip-gateway-address-set"></a><span data-ttu-id="11190-1393">IP 게이트웨이 주소 설정</span><span class="sxs-lookup"><span data-stu-id="11190-1393">IP Gateway Address Set</span></span> 

#### <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="11190-1394">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="11190-1394">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="11190-1395">**아이콘** ![IP 게이트웨이 주소 설정 아이콘](./media/user-guide/netx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1395">**Icon** ![I P gateway address set icon](./media/user-guide/netx-events/image96.png)</span></span>

<span data-ttu-id="11190-1396">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1396">**Description**</span></span>

<span data-ttu-id="11190-1397">이 이벤트는 nx_ip_gateway_address_set을 통해 게이트웨이 IP 주소를 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1397">This event represents setting the gateway IP address via nx_ip_gateway_address_set.</span></span>

<span data-ttu-id="11190-1398">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1398">**Information Fields**</span></span>

- <span data-ttu-id="11190-1399">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1399">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1400">정보 필드 2: 게이트웨이 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1400">Info Field 2: Gateway IP address</span></span>
- <span data-ttu-id="11190-1401">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1401">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1402">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1402">Info Field 4: Not used</span></span>

### <a name="ip-information-get"></a><span data-ttu-id="11190-1403">IP 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1403">IP Information Get</span></span> 

#### <a name="nx_ip_info_get"></a><span data-ttu-id="11190-1404">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="11190-1404">nx_ip_info_get</span></span>

<span data-ttu-id="11190-1405">**아이콘** ![IP 정보 가져오기 아이콘](./media/user-guide/netx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1405">**Icon** ![I P information get icon](./media/user-guide/netx-events/image97.png)</span></span>

<span data-ttu-id="11190-1406">**설명** 이 이벤트는 nx_ip_info_get을 통해 IP 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1406">**Description** This event represents getting IP information via nx_ip_info_get.</span></span>

<span data-ttu-id="11190-1407">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1407">**Information Fields**</span></span>

- <span data-ttu-id="11190-1408">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1408">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1409">정보 필드 2: 송신한 IP 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1409">Info Field 2: IP bytes sent</span></span>
- <span data-ttu-id="11190-1410">정보 필드 3: 수신한 IP 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1410">Info Field 3: IP bytes received</span></span>
- <span data-ttu-id="11190-1411">정보 필드 4: 삭제된 IP 패킷 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1411">Info Field 4: IP packets dropped</span></span>

### <a name="ip-interface-attach"></a><span data-ttu-id="11190-1412">IP 인터페이스 연결</span><span class="sxs-lookup"><span data-stu-id="11190-1412">IP Interface Attach</span></span> 

#### <a name="nx_interface_attach"></a><span data-ttu-id="11190-1413">nx_interface_attach</span><span class="sxs-lookup"><span data-stu-id="11190-1413">nx_interface_attach</span></span>

<span data-ttu-id="11190-1414">**아이콘** ![IP 인터페이스 연결 아이콘](./media/user-guide/netx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1414">**Icon** ![I P iterface attach icon](./media/user-guide/netx-events/image98.png)</span></span>

<span data-ttu-id="11190-1415">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1415">**Description**</span></span>

<span data-ttu-id="11190-1416">이 이벤트는 nx_ip_interface_attach를 통해 IP 인스턴스에 연결되는 보조 네트워크 인터페이스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1416">This event represents a secondary network interface being attached to the IP instance via nx_ip_interface_attach.</span></span>

<span data-ttu-id="11190-1417">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1417">**Information Fields**</span></span>

- <span data-ttu-id="11190-1418">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1418">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1419">정보 필드 2: 인터페이스 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1419">Info Field 2: Interface IP Address</span></span>
- <span data-ttu-id="11190-1420">정보 필드 3: IP 인터페이스 테이블에 대한 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1420">Info Field 3: Index into IP interface table</span></span>
- <span data-ttu-id="11190-1421">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1421">Info Field 4: Not used</span></span>

### <a name="ip-interface-info-get"></a><span data-ttu-id="11190-1422">IP 인터페이스 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1422">IP Interface Info Get</span></span> 

#### <a name="nx_ip_interface_info_get"></a><span data-ttu-id="11190-1423">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="11190-1423">nx_ip_interface_info_get</span></span>

<span data-ttu-id="11190-1424">**아이콘** ![IP 인터페이스 정보 가져오기 아이콘](./media/user-guide/netx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1424">**Icon** ![ IP interface info get icon](./media/user-guide/netx-events/image99.png)</span></span>

<span data-ttu-id="11190-1425">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1425">**Description**</span></span>

<span data-ttu-id="11190-1426">이 이벤트는 nx_ip_interface_info_get을 통해 지정된 네트워크 인터페이스에서 검색된 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1426">This event represents information retrieved from the specified network interface via nx_ip_interface_info_get.</span></span>

<span data-ttu-id="11190-1427">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1427">**Information Fields**</span></span>

- <span data-ttu-id="11190-1428">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1428">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1429">정보 필드 2: 인터페이스 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1429">Info Field 2: Interface IP address</span></span>
- <span data-ttu-id="11190-1430">정보 필드 3: 인터페이스 MAC 주소 msb입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1430">Info Field 3: Interface MAC address msb</span></span>
- <span data-ttu-id="11190-1431">정보 필드 4: 인터페이스 MAC 주소 lsb입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1431">Info Field 4: Interface MAC address lsb</span></span>

### <a name="ip-raw-packet-disable"></a><span data-ttu-id="11190-1432">IP 원시 패킷 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11190-1432">IP Raw Packet Disable</span></span> 

#### <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="11190-1433">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="11190-1433">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="11190-1434">**아이콘** ![IP 원시 패킷 사용 안 함 아이콘](./media/user-guide/netx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1434">**Icon** ![I P raw packet disable icon](./media/user-guide/netx-events/image100.png)</span></span>

<span data-ttu-id="11190-1435">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1435">**Description**</span></span>

<span data-ttu-id="11190-1436">이 이벤트는 nx_ip_raw_packet_disable을 통해 원시 IP 패킷 통신을 사용하지 않도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1436">This event represents disabling raw IP packet communication via nx_ip_raw_packet_disable.</span></span>

<span data-ttu-id="11190-1437">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1437">**Information Fields**</span></span>

- <span data-ttu-id="11190-1438">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1438">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1439">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1439">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1440">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1440">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1441">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1441">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-enable"></a><span data-ttu-id="11190-1442">IP 원시 패킷 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1442">IP Raw Packet Enable</span></span> 

#### <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="11190-1443">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1443">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="11190-1444">**아이콘** ![IP 원시 패킷 사용 아이콘](./media/user-guide/netx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1444">**Icon** ![I P raw packet enable icon](./media/user-guide/netx-events/image101.png)</span></span>

<span data-ttu-id="11190-1445">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1445">**Description**</span></span>

<span data-ttu-id="11190-1446">이 이벤트는 nx_ip_raw_packet_enable을 통해 원시 IP 패킷 통신을 사용하도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1446">This event represents enabling raw IP packet communication via nx_ip_raw_packet_enable.</span></span>

<span data-ttu-id="11190-1447">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1447">**Information Fields**</span></span>

- <span data-ttu-id="11190-1448">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1448">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1449">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1449">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1450">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1450">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1451">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1451">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-receive"></a><span data-ttu-id="11190-1452">IP 원시 패킷 수신</span><span class="sxs-lookup"><span data-stu-id="11190-1452">IP Raw Packet Receive</span></span> 

#### <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="11190-1453">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="11190-1453">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="11190-1454">**아이콘** ![IP 원시 패킷 수신 아이콘](./media/user-guide/netx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1454">**Icon** ![I P raw packet receive icon](./media/user-guide/netx-events/image102.png)</span></span>

<span data-ttu-id="11190-1455">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1455">**Description**</span></span>

<span data-ttu-id="11190-1456">이 이벤트는 nx_ip_raw_packet_receive를 통해 원시 IP 패킷을 수신하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1456">This event represents receiving a raw IP packet via nx_ip_raw_packet_receive.</span></span>

<span data-ttu-id="11190-1457">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1457">**Information Fields**</span></span>

- <span data-ttu-id="11190-1458">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1458">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1459">정보 필드 2: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1459">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="11190-1460">정보 필드 3: 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1460">Info Field 3: Wait option</span></span>
- <span data-ttu-id="11190-1461">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1461">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-send"></a><span data-ttu-id="11190-1462">IP 원시 패킷 송신</span><span class="sxs-lookup"><span data-stu-id="11190-1462">IP Raw Packet Send</span></span> 

#### <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="11190-1463">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="11190-1463">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="11190-1464">**아이콘** ![IP 원시 패킷 송신 아이콘](./media/user-guide/netx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1464">**Icon** ![I P raw packet send icon](./media/user-guide/netx-events/image103.png)</span></span>

<span data-ttu-id="11190-1465">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1465">**Description**</span></span>

<span data-ttu-id="11190-1466">이 이벤트는 nx_ip_raw_packet_send를 통해 원시 IP 패킷을 보내는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1466">This event represents sending a raw IP packet via nx_ip_raw_packet_send.</span></span>

<span data-ttu-id="11190-1467">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1467">**Information Fields**</span></span>

- <span data-ttu-id="11190-1468">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1468">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1469">정보 필드 2: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1469">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="11190-1470">정보 필드 3: 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1470">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="11190-1471">정보 필드 4: 서비스 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1471">Info Field 4: Type of service</span></span>

### <a name="ip-static-route-add"></a><span data-ttu-id="11190-1472">IP 고정 경로 추가</span><span class="sxs-lookup"><span data-stu-id="11190-1472">IP Static Route Add</span></span> 

#### <a name="nx_ip_static_route_add"></a><span data-ttu-id="11190-1473">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="11190-1473">nx_ip_static_route_add</span></span>

<span data-ttu-id="11190-1474">**아이콘** ![IP 고정 경로 추가 아이콘](./media/user-guide/netx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1474">**Icon** ![I P static route add icon](./media/user-guide/netx-events/image104.png)</span></span>

<span data-ttu-id="11190-1475">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1475">**Description**</span></span>

<span data-ttu-id="11190-1476">이 이벤트는 nx_ip_static_route_add를 통해 IP 인스턴스 라우팅 테이블에 추가되는 고정 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1476">This event represents a static route being added to the IP instance routing table via nx_ip_static_route_add.</span></span>

<span data-ttu-id="11190-1477">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1477">**Information Fields**</span></span>

- <span data-ttu-id="11190-1478">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1478">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1479">정보 필드 2: 네트워크 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1479">Info Field 2: Network address</span></span>
- <span data-ttu-id="11190-1480">정보 필드 3: 네트워크 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1480">Info Field 3: Network mask</span></span>
- <span data-ttu-id="11190-1481">정보 필드 4: 다음 홉입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1481">Info Field 4: Next hop</span></span>

### <a name="ip-static-route-delete"></a><span data-ttu-id="11190-1482">IP 고정 경로 삭제</span><span class="sxs-lookup"><span data-stu-id="11190-1482">IP Static Route Delete</span></span> 

#### <a name="nx_ip_static_route_delete"></a><span data-ttu-id="11190-1483">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="11190-1483">nx_ip_static_route_delete</span></span>

<span data-ttu-id="11190-1484">**아이콘** ![IP 고정 경로 삭제 아이콘](./media/user-guide/netx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1484">**Icon** ![I P static rute delete icon](./media/user-guide/netx-events/image105.png)</span></span>

<span data-ttu-id="11190-1485">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1485">**Description**</span></span>

<span data-ttu-id="11190-1486">이 이벤트는 nx_ip_static_route_delete를 통해 IP 인스턴스 라우팅 테이블에서 제거되는 고정 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1486">This event represents a static route being removed from the IP instance routing table via nx_ip_static_route_delete.</span></span>

<span data-ttu-id="11190-1487">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1487">**Information Fields**</span></span>

- <span data-ttu-id="11190-1488">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1488">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1489">정보 필드 2: 네트워크 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1489">Info Field 2: Network address</span></span>
- <span data-ttu-id="11190-1490">정보 필드 3: 네트워크 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1490">Info Field 3: Network mask</span></span>
- <span data-ttu-id="11190-1491">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1491">Info Field 4: Not used</span></span>

### <a name="ip-status-check"></a><span data-ttu-id="11190-1492">IP 상태 확인</span><span class="sxs-lookup"><span data-stu-id="11190-1492">IP Status Check</span></span> 

#### <a name="nx_ip_status_check"></a><span data-ttu-id="11190-1493">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="11190-1493">nx_ip_status_check</span></span>

<span data-ttu-id="11190-1494">**아이콘** ![IP 상태 확인 아이콘](./media/user-guide/netx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1494">**Icon** ![I P status check icon](./media/user-guide/netx-events/image106.png)</span></span>

<span data-ttu-id="11190-1495">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1495">**Description**</span></span>

<span data-ttu-id="11190-1496">이 이벤트는 nx_ip_status_check를 통해 IP 상태를 확인하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1496">This event represents checking for an IP status via nx_ip_status_check.</span></span>

<span data-ttu-id="11190-1497">정보 필드</span><span class="sxs-lookup"><span data-stu-id="11190-1497">Information Fields</span></span> 

- <span data-ttu-id="11190-1498">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1498">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="11190-1499">정보 필드 2: 요청된 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1499">Info Field 2: Requested status</span></span>
- <span data-ttu-id="11190-1500">정보 필드 3: 실제 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1500">Info Field 3: Actual status</span></span>
- <span data-ttu-id="11190-1501">정보 필드 4: 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1501">Info Field 4: Wait option</span></span>

### <a name="ipsec-enable"></a><span data-ttu-id="11190-1502">IPSEC 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1502">IPSEC Enable</span></span> 

#### <a name="nx_ipsec_enable"></a><span data-ttu-id="11190-1503">nx_ipsec_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1503">nx_ipsec_enable</span></span>

<span data-ttu-id="11190-1504">**아이콘** ![IPSEC 사용 아이콘](./media/user-guide/netx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1504">**Icon** ![I P S E C enable icon](./media/user-guide/netx-events/image107.png)</span></span>

<span data-ttu-id="11190-1505">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1505">**Description**</span></span>

<span data-ttu-id="11190-1506">이 이벤트는 nx_ipsec_enable을 통해 제공된 IP 인스턴스에서 IPSec 서비스를 사용하도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1506">This event represents enabling IPSec services on the supplied IP instance via nx_ipsec_enable.</span></span>

<span data-ttu-id="11190-1507">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1507">**Information Fields**</span></span>

- <span data-ttu-id="11190-1508">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1508">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1509">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1509">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1510">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1510">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1511">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1511">Info Field 4: Not used</span></span>

### <a name="packet-allocate"></a><span data-ttu-id="11190-1512">패킷 할당</span><span class="sxs-lookup"><span data-stu-id="11190-1512">Packet Allocate</span></span> 

#### <a name="nx_packet_allocate"></a><span data-ttu-id="11190-1513">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="11190-1513">nx_packet_allocate</span></span>

<span data-ttu-id="11190-1514">**아이콘** ![패킷 할당 아이콘](./media/user-guide/netx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1514">**Icon** ![Packet allocate icon](./media/user-guide/netx-events/image108.png)</span></span>

<span data-ttu-id="11190-1515">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1515">**Description**</span></span>

<span data-ttu-id="11190-1516">이 이벤트는 nx_packet_allocate를 통한 패킷 할당을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1516">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="11190-1517">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1517">**Information Fields**</span></span>

- <span data-ttu-id="11190-1518">정보 필드 1: 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1518">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="11190-1519">정보 필드 2: 할당된 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1519">Info Field 2: Pointer to packet allocated</span></span>
- <span data-ttu-id="11190-1520">정보 필드 3: 패킷 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1520">Info Field 3: Packet type</span></span>
- <span data-ttu-id="11190-1521">정보 필드 4: 사용 가능한 패킷입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1521">Info Field 4: Available packets</span></span>

### <a name="packet-copy"></a><span data-ttu-id="11190-1522">패킷 복사</span><span class="sxs-lookup"><span data-stu-id="11190-1522">Packet Copy</span></span> 

#### <a name="nx_packet_copy"></a><span data-ttu-id="11190-1523">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="11190-1523">nx_packet_copy</span></span>

<span data-ttu-id="11190-1524">**아이콘** ![패킷 복사 아이콘](./media/user-guide/netx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1524">**Icon** ![Packet cpy icon](./media/user-guide/netx-events/image109.png)</span></span>

<span data-ttu-id="11190-1525">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1525">**Description**</span></span>

<span data-ttu-id="11190-1526">이 이벤트는 nx_packet_copy를 통한 패킷 복사를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1526">This event represents copying a packet via nx_packet_copy.</span></span>

<span data-ttu-id="11190-1527">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1527">**Information Fields**</span></span>

- <span data-ttu-id="11190-1528">정보 필드 2: 새 패킷 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1528">Info Field 2: New packet pointer</span></span>
- <span data-ttu-id="11190-1529">정보 필드 3: 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1529">Info Field 3: Pointer to packet pool</span></span>
- <span data-ttu-id="11190-1530">정보 필드 4: 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1530">Info Field 4: Wait option</span></span>

### <a name="packet-data-append"></a><span data-ttu-id="11190-1531">패킷 데이터 추가</span><span class="sxs-lookup"><span data-stu-id="11190-1531">Packet Data Append</span></span> 

#### <a name="nx_packet_data_append"></a><span data-ttu-id="11190-1532">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="11190-1532">nx_packet_data_append</span></span>

<span data-ttu-id="11190-1533">**아이콘** ![ 패킷 데이터 추가 아이콘](./media/user-guide/netx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1533">**Icon** ![Packet data append icon](./media/user-guide/netx-events/image110.png)</span></span>

<span data-ttu-id="11190-1534">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1534">**Description**</span></span>

<span data-ttu-id="11190-1535">이 이벤트는 nx_packet_data_append를 통해 패킷에 데이터를 추가하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1535">This event represents appending data to a packet via nx_packet_data_append.</span></span>

<span data-ttu-id="11190-1536">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1536">**Information Fields**</span></span>

- <span data-ttu-id="11190-1537">정보 필드 1: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1537">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="11190-1538">정보 필드 2: 데이터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1538">Info Field 2: Pointer to data</span></span>
- <span data-ttu-id="11190-1539">정보 필드 3: 데이터의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1539">Info Field 3: Size of data</span></span>
- <span data-ttu-id="11190-1540">정보 필드 4: 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1540">Info Field 4: Pointer to packet pool</span></span>

### <a name="packet-data-extract-offset"></a><span data-ttu-id="11190-1541">패킷 데이터 추출 오프셋</span><span class="sxs-lookup"><span data-stu-id="11190-1541">Packet Data Extract Offset</span></span> 

#### <a name="nx_udp_source_extract_offset"></a><span data-ttu-id="11190-1542">nx_udp_source_extract_offset</span><span class="sxs-lookup"><span data-stu-id="11190-1542">nx_udp_source_extract_offset</span></span>

<span data-ttu-id="11190-1543">**아이콘** ![패킷 데이터 추출 오프셋 아이콘](./media/user-guide/netx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1543">**Icon** ![Packet data extract offset icon](./media/user-guide/netx-events/image111.png)</span></span>

<span data-ttu-id="11190-1544">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1544">**Description**</span></span>

<span data-ttu-id="11190-1545">이 이벤트는 nx_udp_source_extract_offset을 통해 패킷에서 제공된 버퍼로 추출되는 패킷 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1545">This event represents packet data that is extracted into a supplied buffer from a packet via nx_udp_source_extract_offset.</span></span>

<span data-ttu-id="11190-1546">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1546">**Information Fields**</span></span>

- <span data-ttu-id="11190-1547">정보 필드 1: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1547">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="11190-1548">정보 필드 2: 지정된 버퍼 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1548">Info Field 2: Size of specified buffer</span></span>
- <span data-ttu-id="11190-1549">정보 필드 3: 복사된 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1549">Info Field 3: Number of bytes copied</span></span>
- <span data-ttu-id="11190-1550">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1550">Info Field 4: Not used</span></span>

### <a name="packet-data-retrieve"></a><span data-ttu-id="11190-1551">패킷 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="11190-1551">Packet Data Retrieve</span></span> 

#### <a name="nx_packet_data_retrieve"></a><span data-ttu-id="11190-1552">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="11190-1552">nx_packet_data_retrieve</span></span>

<span data-ttu-id="11190-1553">**아이콘** ![패킷 데이터 검색 아이콘](./media/user-guide/netx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1553">**Icon** ![Packet data retrieve icon](./media/user-guide/netx-events/image112.png)</span></span>

<span data-ttu-id="11190-1554">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1554">**Description**</span></span>

<span data-ttu-id="11190-1555">이 이벤트는 nx_packet_data_retrieve를 통해 패킷에서 데이터를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1555">This event represents retrieving data from a packet via nx_packet_data_retrieve.</span></span>

<span data-ttu-id="11190-1556">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1556">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1557">정보 필드 1: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1557">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="11190-1558">정보 필드 2: 버퍼의 시작 부분에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1558">Info Field 2: Pointer to start of buffer</span></span>
- <span data-ttu-id="11190-1559">정보 필드 3: 복사한 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1559">Info Field 3: Bytes copied</span></span>
- <span data-ttu-id="11190-1560">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1560">Info Field 4: Not used</span></span>

### <a name="packet-length-get"></a><span data-ttu-id="11190-1561">패킷 길이 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1561">Packet Length Get</span></span> 

#### <a name="nx_packet_length_get"></a><span data-ttu-id="11190-1562">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="11190-1562">nx_packet_length_get</span></span>

<span data-ttu-id="11190-1563">**아이콘** ![패킷 길이 가져오기 아이콘](./media/user-guide/netx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1563">**Icon** ![Packet length get icon](./media/user-guide/netx-events/image113.png)</span></span>

<span data-ttu-id="11190-1564">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1564">**Description**</span></span>

<span data-ttu-id="11190-1565">이 이벤트는 nx_packet_length_get을 통해 패킷 길이를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1565">This event represents getting the length of a packet via nx_packet_length_get.</span></span>

<span data-ttu-id="11190-1566">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1566">**Information Fields**</span></span>

- <span data-ttu-id="11190-1567">정보 필드 1: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1567">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="11190-1568">정보 필드 2: 패킷 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1568">Info Field 2: Packet length</span></span>
- <span data-ttu-id="11190-1569">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1569">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1570">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1570">Info Field 4: Not used</span></span>

### <a name="packet-pool-create"></a><span data-ttu-id="11190-1571">패킷 풀 만들기</span><span class="sxs-lookup"><span data-stu-id="11190-1571">Packet Pool Create</span></span> 

#### <a name="nx_packet_pool_create"></a><span data-ttu-id="11190-1572">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="11190-1572">nx_packet_pool_create</span></span>

<span data-ttu-id="11190-1573">**아이콘** ![패킷 풀 만들기 아이콘](./media/user-guide/netx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1573">**Icon** ![Packet pool create icon](./media/user-guide/netx-events/image114.png)</span></span>

<span data-ttu-id="11190-1574">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1574">**Description**</span></span>

<span data-ttu-id="11190-1575">이 이벤트는 nx_packet_pool_create을 통해 패킷 풀을 만드는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1575">This event represents creating a packet pool via nx_packet_pool_create.</span></span>

<span data-ttu-id="11190-1576">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1576">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1577">정보 필드 1: 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1577">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="11190-1578">정보 필드 2: 패킷 페이로드 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1578">Info Field 2: Packet payload size</span></span>
- <span data-ttu-id="11190-1579">정보 필드 3: 풀 메모리 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1579">Info Field 3: Pointer to pool memory area</span></span>
- <span data-ttu-id="11190-1580">정보 필드 4: 풀 메모리 영역의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1580">Info Field 4: Size of pool memory area</span></span>

### <a name="packet-pool-delete"></a><span data-ttu-id="11190-1581">패킷 풀 삭제</span><span class="sxs-lookup"><span data-stu-id="11190-1581">Packet Pool Delete</span></span> 

#### <a name="nx_packet_pool_delete"></a><span data-ttu-id="11190-1582">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="11190-1582">nx_packet_pool_delete</span></span>

<span data-ttu-id="11190-1583">**아이콘** ![패킷 풀 삭제 아이콘](./media/user-guide/netx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1583">**Icon** ![Packet pool delete icon](./media/user-guide/netx-events/image115.png)</span></span>

<span data-ttu-id="11190-1584">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1584">**Description**</span></span>

<span data-ttu-id="11190-1585">이 이벤트는 nx_packet_pool_delete를 통해 패킷 풀을 삭제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1585">This event represents deleting a packet pool via nx_packet_pool_delete.</span></span>

<span data-ttu-id="11190-1586">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1586">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1587">정보 필드 1: 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1587">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="11190-1588">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1588">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1589">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1589">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1590">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1590">Info Field 4: Not used</span></span>

#### <a name="packet-pool-information-get"></a><span data-ttu-id="11190-1591">패킷 풀 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1591">Packet Pool Information Get</span></span> 

#### <a name="nx_packet_pool_info_get"></a><span data-ttu-id="11190-1592">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="11190-1592">nx_packet_pool_info_get</span></span>

<span data-ttu-id="11190-1593">**아이콘** ![패킷 풀 정보 가져오기 아이콘](./media/user-guide/netx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1593">**Icon** ![Packet pool information get icon](./media/user-guide/netx-events/image116.png)</span></span>

<span data-ttu-id="11190-1594">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1594">**Description**</span></span>

<span data-ttu-id="11190-1595">이 이벤트는 nx_packet_pool_info_get을 통해 패킷 풀 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1595">This event represents getting packet pool information via nx_packet_pool_info_get.</span></span>

<span data-ttu-id="11190-1596">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1596">**Information Fields**</span></span>

- <span data-ttu-id="11190-1597">정보 필드 1: 패킷 풀에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1597">Info Field 1: Pointer to packet pool</span></span>
- <span data-ttu-id="11190-1598">정보 필드 2: 총 패킷 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1598">Info Field 2: Total packets</span></span>
- <span data-ttu-id="11190-1599">정보 필드 3: 사용 가능한 패킷입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1599">Info Field 3: Available packets</span></span>
- <span data-ttu-id="11190-1600">정보 필드 4: 빈 요청입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1600">Info Field 4: Empty requests</span></span>

### <a name="packet-release"></a><span data-ttu-id="11190-1601">패킷 해제</span><span class="sxs-lookup"><span data-stu-id="11190-1601">Packet Release</span></span> 

#### <a name="nx_packet_data_release"></a><span data-ttu-id="11190-1602">nx_packet_data_release</span><span class="sxs-lookup"><span data-stu-id="11190-1602">nx_packet_data_release</span></span>

<span data-ttu-id="11190-1603">**아이콘** ![패킷 해제 아이콘](./media/user-guide/netx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1603">**Icon** ![Packet release icon](./media/user-guide/netx-events/image117.png)</span></span>

<span data-ttu-id="11190-1604">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1604">**Description**</span></span>

<span data-ttu-id="11190-1605">이 이벤트는 nx_packet_release를 통해 패킷을 해제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1605">This event represents releasing a packet via nx_packet_release.</span></span>

<span data-ttu-id="11190-1606">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1606">**Information Fields**</span></span>

- <span data-ttu-id="11190-1607">정보 필드 1: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1607">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="11190-1608">정보 필드 2: 패킷 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1608">Info Field 2: Packet status</span></span>
- <span data-ttu-id="11190-1609">정보 필드 3: 사용 가능한 패킷입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1609">Info Field 3: Available packets</span></span>
- <span data-ttu-id="11190-1610">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1610">Info Field 4: Not used</span></span>

### <a name="packet-transmit-release"></a><span data-ttu-id="11190-1611">패킷 전송 해제</span><span class="sxs-lookup"><span data-stu-id="11190-1611">Packet Transmit Release</span></span> 

#### <a name="nx_packet_transmit_release"></a><span data-ttu-id="11190-1612">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="11190-1612">nx_packet_transmit_release</span></span>

<span data-ttu-id="11190-1613">**아이콘** ![패킷 전송 해제 아이콘](./media/user-guide/netx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1613">**Icon** ![Packet transmit release icon](./media/user-guide/netx-events/image118.png)</span></span>

<span data-ttu-id="11190-1614">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1614">**Description**</span></span>

<span data-ttu-id="11190-1615">이 이벤트는 nx_packet_transmit_release를 통해 전송 패킷을 해제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1615">This event represents releasing a transmit packet via nx_packet_transmit_release.</span></span>

<span data-ttu-id="11190-1616">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1616">**Information Fields**</span></span>

- <span data-ttu-id="11190-1617">정보 필드 1: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1617">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="11190-1618">정보 필드 2: 패킷 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1618">Info Field 2: Packet status</span></span>
- <span data-ttu-id="11190-1619">정보 필드 3: 사용 가능한 패킷입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1619">Info Field 3: Available packets</span></span>
- <span data-ttu-id="11190-1620">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1620">Info Field 4: Not used</span></span>

### <a name="rarp-disable"></a><span data-ttu-id="11190-1621">RARP 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11190-1621">RARP Disable</span></span> 

#### <a name="nx_rarp_disable"></a><span data-ttu-id="11190-1622">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="11190-1622">nx_rarp_disable</span></span>

<span data-ttu-id="11190-1623">**아이콘** ![RARP 사용 안 함 아이콘](./media/user-guide/netx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1623">**Icon** ![R A R P disable icon](./media/user-guide/netx-events/image119.png)</span></span>

<span data-ttu-id="11190-1624">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1624">**Description**</span></span>

<span data-ttu-id="11190-1625">이 이벤트는 nx_rarp_disable를 통해 RARP를 사용하지 않도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1625">This event represents disabling RARP via nx_rarp_disable.</span></span>

<span data-ttu-id="11190-1626">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1626">**Information Fields**</span></span>

- <span data-ttu-id="11190-1627">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1627">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1628">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1628">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1629">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1629">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1630">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1630">Info Field 4: Not used</span></span>

### <a name="rarp-enable"></a><span data-ttu-id="11190-1631">RARP 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1631">RARP Enable</span></span> 

#### <a name="nx_rarp_enable"></a><span data-ttu-id="11190-1632">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1632">nx_rarp_enable</span></span>

<span data-ttu-id="11190-1633">**아이콘** ![RARP 사용 아이콘](./media/user-guide/netx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1633">**Icon** ![R A R P enable icon](./media/user-guide/netx-events/image120.png)</span></span>

<span data-ttu-id="11190-1634">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1634">**Description**</span></span>

<span data-ttu-id="11190-1635">이 이벤트는 nx_rarp_enable을 통해 RARP를 사용하도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1635">This event represents enabling RARP via nx_rarp_enable.</span></span>

<span data-ttu-id="11190-1636">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1636">**Information Fields**</span></span>

- <span data-ttu-id="11190-1637">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1637">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1638">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1638">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1639">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1639">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1640">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1640">Info Field 4: Not used</span></span>

### <a name="rarp-information-get"></a><span data-ttu-id="11190-1641">RARP 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1641">RARP Information Get</span></span> 

#### <a name="nx_rarp_info_get"></a><span data-ttu-id="11190-1642">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="11190-1642">nx_rarp_info_get</span></span>

<span data-ttu-id="11190-1643">**아이콘** ![RARP 정보 가져오기 아이콘](./media/user-guide/netx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1643">**Icon** ![R A R P information get icon](./media/user-guide/netx-events/image121.png)</span></span>

<span data-ttu-id="11190-1644">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1644">**Description**</span></span>

<span data-ttu-id="11190-1645">이 이벤트는 nx_rarp_info_get을 통한 RARP 정보 가져오기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1645">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="11190-1646">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1646">**Information Fields**</span></span>

- <span data-ttu-id="11190-1647">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1647">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1648">정보 필드 2: 송신한 요청입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1648">Info Field 2: Requests sent</span></span>
- <span data-ttu-id="11190-1649">정보 필드 3: 수신한 응답입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1649">Info Field 3: Responses received</span></span>
- <span data-ttu-id="11190-1650">정보 필드 4: 잘못된 응답입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1650">Info Field 4: Invalid responses</span></span>

### <a name="system-initialize"></a><span data-ttu-id="11190-1651">시스템 초기화</span><span class="sxs-lookup"><span data-stu-id="11190-1651">System Initialize</span></span> 

#### <a name="nx_system_initialize"></a><span data-ttu-id="11190-1652">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="11190-1652">nx_system_initialize</span></span>

<span data-ttu-id="11190-1653">**아이콘** ![시스템 초기화 아이콘](./media/user-guide/netx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1653">**Icon** ![System initialize icon](./media/user-guide/netx-events/image122.png)</span></span>

<span data-ttu-id="11190-1654">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1654">**Description**</span></span>

<span data-ttu-id="11190-1655">이 이벤트는 nx_system_initialize를 통한 NetX 초기화를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1655">This event represents initializing NetX via nx_system_initialize.</span></span>

<span data-ttu-id="11190-1656">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1656">**Information Fields**</span></span>

- <span data-ttu-id="11190-1657">정보 필드 1 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1657">Info Field 1: Not used</span></span>
- <span data-ttu-id="11190-1658">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1658">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1659">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1659">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1660">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1660">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-bind"></a><span data-ttu-id="11190-1661">TCP 클라이언트 소켓 바인딩</span><span class="sxs-lookup"><span data-stu-id="11190-1661">TCP Client Socket Bind</span></span> 

#### <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="11190-1662">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="11190-1662">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="11190-1663">**아이콘** ![TCP 클라이언트 소켓 바인딩 아이콘](./media/user-guide/netx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1663">**Icon** ![T  P client socket bind icon](./media/user-guide/netx-events/image123.png)</span></span>

<span data-ttu-id="11190-1664">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1664">**Description**</span></span>

<span data-ttu-id="11190-1665">이 이벤트는 nx_tcp_client_socket_bind를 통해 포트에 클라이언트 소켓을 바인딩하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1665">This event represents binding a client socket to a port via nx_tcp_client_socket_bind.</span></span>

<span data-ttu-id="11190-1666">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1666">**Information Fields**</span></span>

- <span data-ttu-id="11190-1667">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1667">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1668">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1668">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1669">정보 필드 3: 요청된 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1669">Info Field 3: Port requested</span></span>
- <span data-ttu-id="11190-1670">정보 필드 4: 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1670">Info Field 4: Wait option</span></span>

### <a name="tcp-client-socket-connect"></a><span data-ttu-id="11190-1671">TCP 클라이언트 소켓 연결</span><span class="sxs-lookup"><span data-stu-id="11190-1671">TCP Client Socket Connect</span></span> 

#### <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="11190-1672">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="11190-1672">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="11190-1673">**아이콘** ![TCP 클라이언트 소켓 연결 아이콘](./media/user-guide/netx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1673">**Icon** ![T C P client socket connect icon](./media/user-guide/netx-events/image124.png)</span></span>

<span data-ttu-id="11190-1674">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1674">**Description**</span></span>

<span data-ttu-id="11190-1675">이 이벤트는 nx_tcp_client_socket_connect를 통해 클라이언트 소켓 연결을 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1675">This event represents making a client socket connection via nx_tcp_client_socket_connect.</span></span>

<span data-ttu-id="11190-1676">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1676">**Information Fields**</span></span>

- <span data-ttu-id="11190-1677">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1677">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1678">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1678">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1679">정보 필드 3: 서버 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1679">Info Field 3: Server IP address</span></span>
- <span data-ttu-id="11190-1680">정보 필드 4: 요청된 서버 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1680">Info Field 4: Server port requested</span></span>

### <a name="tcp-client-socket-port-get"></a><span data-ttu-id="11190-1681">TCP 클라이언트 소켓 포트 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1681">TCP Client Socket Port Get</span></span> 

#### <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="11190-1682">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="11190-1682">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="11190-1683">**아이콘** ![TCP 클라이언트 소켓 포트 가져오기 아이콘](./media/user-guide/netx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1683">**Icon** ![T C P client socket port get icon](./media/user-guide/netx-events/image125.png)</span></span>

<span data-ttu-id="11190-1684">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1684">**Description**</span></span>

<span data-ttu-id="11190-1685">이 이벤트는 nx_tcp_client_socket_port_get을 통해 클라이언트 소켓 포트 번호를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1685">This event represents getting the client socket port number via nx_tcp_client_socket_port_get.</span></span>

<span data-ttu-id="11190-1686">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1686">**Information Fields**</span></span>

- <span data-ttu-id="11190-1687">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1687">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1688">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1688">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1689">정보 필드 3: 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1689">Info Field 3: Port number</span></span>
- <span data-ttu-id="11190-1690">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1690">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-unbind"></a><span data-ttu-id="11190-1691">TCP 클라이언트 소켓 바인딩 해제</span><span class="sxs-lookup"><span data-stu-id="11190-1691">TCP Client Socket Unbind</span></span> 

#### <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="11190-1692">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="11190-1692">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="11190-1693">**아이콘** ![TCP 클라이언트 소켓 바인딩 해제 아이콘](./media/user-guide/netx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1693">**Icon** ![T C P client socket unbind icon](./media/user-guide/netx-events/image126.png)</span></span>

<span data-ttu-id="11190-1694">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1694">**Description**</span></span>

<span data-ttu-id="11190-1695">이 이벤트는 nx_tcp_client_socket_unbind를 통해 소켓에 연결된 포트를 바인딩 해제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1695">This event represents unbinding the port associated with the socket via nx_tcp_client_socket_unbind.</span></span>

<span data-ttu-id="11190-1696">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1696">**Information Fields**</span></span>

- <span data-ttu-id="11190-1697">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1697">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1698">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1698">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1699">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1699">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1700">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1700">Info Field 4: Not used</span></span>

### <a name="tcp-enable"></a><span data-ttu-id="11190-1701">TCP 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1701">TCP Enable</span></span> 

#### <a name="nx_tcp_enable"></a><span data-ttu-id="11190-1702">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1702">nx_tcp_enable</span></span>

<span data-ttu-id="11190-1703">**아이콘** ![TCP 사용 아이콘](./media/user-guide/netx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1703">**Icon** ![T C P enable icon](./media/user-guide/netx-events/image127.png)</span></span>

<span data-ttu-id="11190-1704">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1704">**Description**</span></span>

<span data-ttu-id="11190-1705">이 이벤트는 nx_tcp_enable을 통해 TCP를 사용하도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1705">This event represents enabling TCP via nx_tcp_enable.</span></span>

<span data-ttu-id="11190-1706">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1706">**Information Fields**</span></span>

- <span data-ttu-id="11190-1707">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1707">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1708">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1708">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1709">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1709">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1710">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1710">Info Field 4: Not used</span></span>

###  <a name="tcp-free-port-find-tcp-free-port-find"></a><span data-ttu-id="11190-1711">TCP 사용 가능한 포트 찾기 TCP 사용 가능한 포트 찾기</span><span class="sxs-lookup"><span data-stu-id="11190-1711">TCP Free Port Find TCP Free Port Find</span></span> 

#### <a name="nx_tcp_free_port_find"></a><span data-ttu-id="11190-1712">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="11190-1712">nx_tcp_free_port_find</span></span>

<span data-ttu-id="11190-1713">**아이콘** ![TCP 사용 가능한 포트 찾기 아이콘](./media/user-guide/netx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1713">**Icon** ![T  CP free port find icon](./media/user-guide/netx-events/image128.png)</span></span>

<span data-ttu-id="11190-1714">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1714">**Description**</span></span>

<span data-ttu-id="11190-1715">이 이벤트는 nx_tcp_free_port_find를 통해 사용 가능한 TCP 포트를 찾는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1715">This event represents finding a free TCP port via nx_tcp_free_port_find.</span></span>

<span data-ttu-id="11190-1716">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1716">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1717">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1717">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1718">정보 필드 2: 시작 검색 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1718">Info Field 2: Starting search port number</span></span>
- <span data-ttu-id="11190-1719">정보 필드 3: 사용 가능한 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1719">Info Field 3: Free port number</span></span>
- <span data-ttu-id="11190-1720">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1720">Info Field 4: Not used</span></span>

###  <a name="tcp-infomation-get"></a><span data-ttu-id="11190-1721">TCP 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1721">TCP Infomation Get</span></span> 

#### <a name="nx_tcp_info_get"></a><span data-ttu-id="11190-1722">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="11190-1722">nx_tcp_info_get</span></span>

<span data-ttu-id="11190-1723">**아이콘** ![TCP 정보 가져오기 아이콘](./media/user-guide/netx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1723">**Icon** ![T C P infomation get icon](./media/user-guide/netx-events/image129.png)</span></span>

<span data-ttu-id="11190-1724">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1724">**Description**</span></span>

<span data-ttu-id="11190-1725">이 이벤트는 nx_tcp_info_get을 통해 지정된 IP 인스턴스에 대한 TCP 정보를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1725">This event represents retrieving TCP information for the specified IP instance via nx_tcp_info_get.</span></span>

<span data-ttu-id="11190-1726">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1726">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1727">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1727">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1728">정보 필드 2: 송신한 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1728">Info Field 2: Number of bytes sent</span></span>
- <span data-ttu-id="11190-1729">정보 필드 3: 수신한 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1729">Info Field 3: Number of bytes received</span></span>
- <span data-ttu-id="11190-1730">정보 필드 4: 잘못된 패킷 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1730">Info Field 4: Number of invalid packets</span></span>

###  <a name="tcp-server-socket-accept"></a><span data-ttu-id="11190-1731">TCP 서버 소켓 수락</span><span class="sxs-lookup"><span data-stu-id="11190-1731">TCP Server Socket Accept</span></span> 

#### <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="11190-1732">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="11190-1732">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="11190-1733">**아이콘** ![TCP 서버 소켓 수락 아이콘](./media/user-guide/netx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1733">**Icon** ![T C P server socket accept icon](./media/user-guide/netx-events/image130.png)</span></span>

<span data-ttu-id="11190-1734">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1734">**Description**</span></span>

<span data-ttu-id="11190-1735">이 이벤트는 nx_tcp_server_socket_accept를 통해 활성 연결 요청이 수신된 후 서버 소켓을 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1735">This event represents setting up the server socket after an active connection request was received via nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="11190-1736">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1736">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1737">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1737">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1738">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1738">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1739">정보 필드 3: 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1739">Info Field 3: Wait option</span></span>
- <span data-ttu-id="11190-1740">정보 필드 4: 소켓 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1740">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-listen"></a><span data-ttu-id="11190-1741">TCP 서버 소켓 수신 대기</span><span class="sxs-lookup"><span data-stu-id="11190-1741">TCP Server Socket Listen</span></span> 

#### <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="11190-1742">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="11190-1742">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="11190-1743">**아이콘** ![TCP 서버 소켓 수신 대기 아이콘](./media/user-guide/netx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1743">**Icon** ![T C P server socket lsten icon](./media/user-guide/netx-events/image131.png)</span></span>

<span data-ttu-id="11190-1744">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1744">**Description**</span></span>

<span data-ttu-id="11190-1745">이 이벤트는 nx_tcp_server_socket_listen을 통해 지정된 TCP 포트에 대한 수신 대기 요청 및 서버 소켓을 등록하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1745">This event represents register a listen request and a server socket for the specified TCP port via nx_tcp_server_socket_listen.</span></span>

<span data-ttu-id="11190-1746">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1746">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1747">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1747">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1748">정보 필드 2: TCP 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1748">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="11190-1749">정보 필드 3: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1749">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="11190-1750">정보 필드 4: 큐에 대기할 수 있는 최대 연결 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1750">Info Field 4: Maximum number of connections that can be queued</span></span>

###  <a name="tcp-server-socket-relisten"></a><span data-ttu-id="11190-1751">TCP 서버 소켓 다시 수신 대기</span><span class="sxs-lookup"><span data-stu-id="11190-1751">TCP Server Socket Relisten</span></span> 

#### <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="11190-1752">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="11190-1752">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="11190-1753">**아이콘** ![TCP 서버 소켓 다시 수신 대기 아이콘](./media/user-guide/netx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1753">**Icon** ![T C P server socket relisten icon](./media/user-guide/netx-events/image132.png)</span></span>

<span data-ttu-id="11190-1754">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1754">**Description**</span></span>

<span data-ttu-id="11190-1755">이 이벤트는 nx_tcp_server_socket_relisten을 통해 지정된 TCP 포트에 대한 기존 수신 대기 요청에 다른 서버 소켓을 등록함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1755">This event represents register another server socket for an existing listen request on the specified TCP port via nx_tcp_server_socket_relisten.</span></span>

<span data-ttu-id="11190-1756">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1756">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1757">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1757">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1758">정보 필드 2: TCP 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1758">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="11190-1759">정보 필드 3: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1759">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="11190-1760">정보 필드 4: 소켓 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1760">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-unaccept"></a><span data-ttu-id="11190-1761">TCP 서버 소켓 허용 안 함</span><span class="sxs-lookup"><span data-stu-id="11190-1761">TCP Server Socket Unaccept</span></span> 

#### <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="11190-1762">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="11190-1762">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="11190-1763">**아이콘** ![TCP 서버 소켓 허용 안 함 아이콘](./media/user-guide/netx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1763">**Icon** ![T C P server socket unaccept icon](./media/user-guide/netx-events/image133.png)</span></span>

<span data-ttu-id="11190-1764">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1764">**Description**</span></span>

<span data-ttu-id="11190-1765">이 이벤트는 nx_tcp_server_socket_unaccept를 통해 이전 수동 연결을 수신하는 포트와의 연결에서 서버 소켓을 제거하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1765">This event represents removing the server socket from association with the port receiving an earlier passive connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="11190-1766">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1766">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1767">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1767">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1768">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1768">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1769">정보 필드 3: 소켓 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1769">Info Field 3: Socket state</span></span>
- <span data-ttu-id="11190-1770">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1770">Info Field 4: Not used</span></span>

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a><span data-ttu-id="11190-1771">TCP 서버 소켓 수신 대기 취소 TCP 서버 소켓 수신 대기 취소</span><span class="sxs-lookup"><span data-stu-id="11190-1771">TCP Server Socket Unlisten TCP Server Socket Unlisten</span></span> 

#### <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="11190-1772">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="11190-1772">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="11190-1773">**아이콘** ![TCP 서버 소켓 수신 대기 취소 아이콘](./media/user-guide/netx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1773">**Icon** ![T C P server socket unlisten icon](./media/user-guide/netx-events/image134.png)</span></span>

<span data-ttu-id="11190-1774">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1774">**Description**</span></span>

<span data-ttu-id="11190-1775">이 이벤트는 nx_tcp_server_socket_unlisten을 통해 지정된 TCP 포트에 대한 이전 수신 대기 요청을 제거하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1775">This event represents removing a previous listen request for the specified TCP port via nx_tcp_server_socket_unlisten.</span></span>

<span data-ttu-id="11190-1776">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1776">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1777">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1777">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1778">정보 필드 2: TCP 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1778">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="11190-1779">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1779">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1780">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1780">Info Field 4: Not used</span></span>

### <a name="tcp-socket-bytes-available"></a><span data-ttu-id="11190-1781">TCP 소켓 사용 가능 바이트</span><span class="sxs-lookup"><span data-stu-id="11190-1781">TCP Socket Bytes Available</span></span> 

#### <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="11190-1782">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="11190-1782">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="11190-1783">**아이콘** ![TCP 소켓 사용 가능 바이트 아이콘](./media/user-guide/netx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1783">**Icon** ![T C P socket bytes available icon](./media/user-guide/netx-events/image135.png)</span></span>

<span data-ttu-id="11190-1784">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1784">**Description**</span></span>

<span data-ttu-id="11190-1785">이 이벤트는 nx_tcp_socket_bytes_available을 통해 지정된 TCP 수신 소켓에서 현재 사용할 수 있는 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1785">This event represents the number of bytes currently available on the specified TCP receiving socket via nx_tcp_socket_bytes_available.</span></span>

<span data-ttu-id="11190-1786">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1786">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1787">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1787">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1788">정보 필드 2: TCP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1788">Info Field 2: Pointer to TCP socket</span></span>
- <span data-ttu-id="11190-1789">정보 필드 3: 소켓에서 수신된 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1789">Info Field 3: Bytes received on the socket</span></span>
- <span data-ttu-id="11190-1790">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1790">Info Field 4: Not used</span></span>

### <a name="tcp-socket-create"></a><span data-ttu-id="11190-1791">TCP 소켓 만들기</span><span class="sxs-lookup"><span data-stu-id="11190-1791">TCP Socket Create</span></span> 

#### <a name="nx_tcp_socket_create"></a><span data-ttu-id="11190-1792">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="11190-1792">nx_tcp_socket_create</span></span>

<span data-ttu-id="11190-1793">**아이콘** ![TCP 소켓 만들기 아이콘](./media/user-guide/netx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1793">**Icon** ![T C P socket create icon](./media/user-guide/netx-events/image136.png)</span></span>

<span data-ttu-id="11190-1794">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1794">**Description**</span></span>

<span data-ttu-id="11190-1795">이 이벤트는 nx_tcp_socket_create를 통해 TCP 소켓을 만드는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1795">This event represents creating a TCP socket via nx_tcp_socket_create.</span></span>

<span data-ttu-id="11190-1796">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1796">**Information Fields**</span></span>

- <span data-ttu-id="11190-1797">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1797">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1798">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1798">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1799">정보 필드 3: 서비스 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1799">Info Field 3: Type of service</span></span>
- <span data-ttu-id="11190-1800">정보 필드 4: 수신 창 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1800">Info Field 4: Receive window size</span></span>

### <a name="tcp-socket-delete"></a><span data-ttu-id="11190-1801">TCP 소켓 삭제</span><span class="sxs-lookup"><span data-stu-id="11190-1801">TCP Socket Delete</span></span> 

#### <a name="nx_tcp_socket_delete"></a><span data-ttu-id="11190-1802">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="11190-1802">nx_tcp_socket_delete</span></span>

<span data-ttu-id="11190-1803">**아이콘** ![TCP 소켓 삭제 아이콘](./media/user-guide/netx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1803">**Icon** ![T C P socket delete icon](./media/user-guide/netx-events/image137.png)</span></span>

<span data-ttu-id="11190-1804">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1804">**Description**</span></span>

<span data-ttu-id="11190-1805">이 이벤트는 nx_tcp_socket_delete를 통해 소켓을 삭제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1805">This event represents deleting a socket via nx_tcp_socket_delete.</span></span>

<span data-ttu-id="11190-1806">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1806">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1807">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1807">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1808">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1808">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1809">정보 필드 3: 소켓 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1809">Info Field 3: Socket state</span></span>
- <span data-ttu-id="11190-1810">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1810">Info Field 4: Not used</span></span>

### <a name="tcp-socket-disconnect"></a><span data-ttu-id="11190-1811">TCP 소켓 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="11190-1811">TCP Socket Disconnect</span></span> 

#### <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="11190-1812">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="11190-1812">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="11190-1813">**아이콘** ![TCP 소켓 연결 끊기 아이콘](./media/user-guide/netx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1813">**Icon** ![T C P socket disconnect icon](./media/user-guide/netx-events/image138.png)</span></span>

<span data-ttu-id="11190-1814">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1814">**Description**</span></span>

<span data-ttu-id="11190-1815">이 이벤트는 nx_tcp_socket_disconnect를 통해 소켓의 연결을 끊는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1815">This event represents disconnecting a socket via nx_tcp_socket_disconnect.</span></span>

<span data-ttu-id="11190-1816">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1816">**Information Fields**</span></span>

- <span data-ttu-id="11190-1817">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1817">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1818">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1818">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1819">정보 필드 3: 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1819">Info Field 3: Wait option</span></span>
- <span data-ttu-id="11190-1820">정보 필드 4: 소켓 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1820">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-information-get"></a><span data-ttu-id="11190-1821">TCP 소켓 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1821">TCP Socket Information Get</span></span> 

#### <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="11190-1822">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="11190-1822">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="11190-1823">**아이콘** ![TCP 소켓 정보 가져오기 아이콘](./media/user-guide/netx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1823">**Icon** ![T C P socket information get icon](./media/user-guide/netx-events/image139.png)</span></span>

<span data-ttu-id="11190-1824">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1824">**Description**</span></span>

<span data-ttu-id="11190-1825">이 이벤트는 nx_tcp_socket_info_get을 통해 소켓에 대한 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1825">This event represents getting information about a socket via nx_tcp_socket_info_get.</span></span>

<span data-ttu-id="11190-1826">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1826">**Information Fields**</span></span>

- <span data-ttu-id="11190-1827">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1827">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1828">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1828">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1829">정보 필드 3: 이 소켓을 통해 송신된 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1829">Info Field 3: Bytes sent through this socket</span></span>
- <span data-ttu-id="11190-1830">정보 필드 4: 이 소켓을 통해 수신된 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1830">Info Field 4: Bytes received through this socket</span></span>

### <a name="tcp-socket-mss-get"></a><span data-ttu-id="11190-1831">TCP 소켓 MSS 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1831">TCP Socket MSS Get</span></span> 

#### <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="11190-1832">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="11190-1832">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="11190-1833">**아이콘** ![TCP 소켓 MSS 가져오기 아이콘](./media/user-guide/netx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1833">**Icon** ![T C P socket M S S get icon](./media/user-guide/netx-events/image140.png)</span></span>

<span data-ttu-id="11190-1834">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1834">**Description**</span></span>

<span data-ttu-id="11190-1835">이 이벤트는 nx_tcp_socket_mss_get을 통해 소켓의 MSS를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1835">This event represents getting the socket's MSS via nx_tcp_socket_mss_get.</span></span>

<span data-ttu-id="11190-1836">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1836">**Information Fields**</span></span>

- <span data-ttu-id="11190-1837">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1837">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1838">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1838">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1839">정보 필드 3: MSS(최대 세그먼트 크기)입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1839">Info Field 3: Maximum Segment Size (MSS)</span></span>
- <span data-ttu-id="11190-1840">정보 필드 4: 소켓 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1840">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-peer-get"></a><span data-ttu-id="11190-1841">TCP 소켓 MSS 피어 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1841">TCP Socket MSS Peer Get</span></span> 

#### <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="11190-1842">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="11190-1842">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="11190-1843">**아이콘** ![TCP 소켓 MSS 피어 가져오기 아이콘](./media/user-guide/netx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1843">**Icon** ![T C P socket M S S peer get icon](./media/user-guide/netx-events/image141.png)</span></span>

<span data-ttu-id="11190-1844">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1844">**Description**</span></span>

<span data-ttu-id="11190-1845">이 이벤트는 nx_tcp_socket_mss_peer_get을 통해 소켓 피어의 MSS 값을 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1845">This event represents getting the MSS value of the socket's peer via nx_tcp_socket_mss_peer_get.</span></span>

<span data-ttu-id="11190-1846">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1846">**Information Fields**</span></span>

- <span data-ttu-id="11190-1847">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1847">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1848">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1848">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1849">정보 필드 3: 피어의 MSS입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1849">Info Field 3: Peer's MSS</span></span>
- <span data-ttu-id="11190-1850">정보 필드 4: 소켓 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1850">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-set"></a><span data-ttu-id="11190-1851">TCP 소켓 MSS 설정</span><span class="sxs-lookup"><span data-stu-id="11190-1851">TCP Socket MSS Set</span></span> 

#### <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="11190-1852">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="11190-1852">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="11190-1853">**아이콘** ![TCP 소켓 MSS 설정 아이콘](./media/user-guide/netx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1853">**Icon** ![T C P socket M S S set icon](./media/user-guide/netx-events/image142.png)</span></span>

<span data-ttu-id="11190-1854">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1854">**Description**</span></span>

<span data-ttu-id="11190-1855">이 이벤트는 nx_tcp_socket_mss_set을 통해 소켓의 MSS를 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1855">This event represents setting a socket's MSS via nx_tcp_socket_mss_set.</span></span>

<span data-ttu-id="11190-1856">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1856">**Information Fields**</span></span>

- <span data-ttu-id="11190-1857">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1857">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1858">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1858">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1859">정보 필드 3: MSS입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1859">Info Field 3: MSS</span></span>
- <span data-ttu-id="11190-1860">정보 필드 4: 소켓 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1860">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-peer-info-get"></a><span data-ttu-id="11190-1861">TCP 소켓 피어 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1861">TCP Socket Peer Info Get</span></span> 

#### <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="11190-1862">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="11190-1862">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="11190-1863">**아이콘** ![TCP 소켓 피어 정보 가져오기 아이콘](./media/user-guide/netx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1863">**Icon** ![T C P socket peer info get icon](./media/user-guide/netx-events/image143.png)</span></span>

<span data-ttu-id="11190-1864">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1864">**Description**</span></span>

<span data-ttu-id="11190-1865">이 이벤트는 nx_tcp_socket_peer_info_get을 통해 피어(예: 연결하는 호스트) IP 주소와 포트에 대한 TCP 소켓에서 검색된 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1865">This event represents information retrieved from the TCP socket regarding the peer (e.g. >connecting host) IP address and port via nx_tcp_socket_peer_info_get.</span></span>

<span data-ttu-id="11190-1866">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1866">**Information Fields**</span></span>

- <span data-ttu-id="11190-1867">정보 필드 1: TCP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1867">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="11190-1868">정보 필드 2: 피어 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1868">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="11190-1869">정보 필드 3: 피어 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1869">Info Field 3: Peer port number</span></span>
- <span data-ttu-id="11190-1870">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1870">Info Field 4: Not used</span></span>

### <a name="tcp-socket-receive"></a><span data-ttu-id="11190-1871">TCP 소켓 수신</span><span class="sxs-lookup"><span data-stu-id="11190-1871">TCP Socket Receive</span></span> 

#### <a name="nx_tcp_socket_receive"></a><span data-ttu-id="11190-1872">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="11190-1872">nx_tcp_socket_receive</span></span>

<span data-ttu-id="11190-1873">**아이콘** ![TCP 소켓 수신 아이콘](./media/user-guide/netx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1873">**Icon** ![T C P socket receive icon](./media/user-guide/netx-events/image144.png)</span></span>

<span data-ttu-id="11190-1874">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1874">**Description**</span></span>

<span data-ttu-id="11190-1875">이 이벤트는 nx_tcp_socket_receive를 통해 소켓에서 데이터를 수신하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1875">This event represents receiving data from a socket via nx_tcp_socket_receive.</span></span>

<span data-ttu-id="11190-1876">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1876">**Information Fields**</span></span>

- <span data-ttu-id="11190-1877">정보 필드 1: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1877">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="11190-1878">정보 필드 2: 수신된 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1878">Info Field 2: Pointer to received packet</span></span>
- <span data-ttu-id="11190-1879">정보 필드 3: 수신된 패킷 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1879">Info Field 3: Received packet length</span></span>
- <span data-ttu-id="11190-1880">정보 필드 4: 수신 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1880">Info Field 4: Receive sequence number</span></span>

### <a name="tcp-socket-receive-notify"></a><span data-ttu-id="11190-1881">TCP 소켓 수신 알림</span><span class="sxs-lookup"><span data-stu-id="11190-1881">TCP Socket Receive Notify</span></span> 

#### <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="11190-1882">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="11190-1882">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="11190-1883">**아이콘** ![TCP 소켓 수신 알림 아이콘](./media/user-guide/netx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1883">**Icon** ![T C P socket receive notify icon](./media/user-guide/netx-events/image145.png)</span></span>

<span data-ttu-id="11190-1884">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1884">**Description**</span></span>

<span data-ttu-id="11190-1885">이 이벤트는 nx_tcp_socket_receive_notify를 통해 소켓에 대한 수신 알림 콜백을 등록하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1885">This event represents registering a receive notify callback for a socket via nx_tcp_socket_receive_notify.</span></span>

<span data-ttu-id="11190-1886">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1886">**Information Fields**</span></span>

- <span data-ttu-id="11190-1887">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1887">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1888">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1888">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1889">정보 필드 3: 수신 알림 콜백에 대한 포인터입니다. 정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1889">Info Field 3: Pointer to receive notify callback Info Field 4: Not used</span></span>

### <a name="tcp-socket-send"></a><span data-ttu-id="11190-1890">TCP 소켓 송신</span><span class="sxs-lookup"><span data-stu-id="11190-1890">TCP Socket Send</span></span> 

#### <a name="nx_tcp_socket_send"></a><span data-ttu-id="11190-1891">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="11190-1891">nx_tcp_socket_send</span></span>

<span data-ttu-id="11190-1892">**아이콘** ![TCP 소켓 송신 아이콘](./media/user-guide/netx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1892">**Icon** ![T C P socket send icon](./media/user-guide/netx-events/image146.png)</span></span>

<span data-ttu-id="11190-1893">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1893">**Description**</span></span>

<span data-ttu-id="11190-1894">이 이벤트는 nx_tcp_socket_send를 통해 소켓에 데이터를 송신하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1894">This event represents sending data on a socket via nx_tcp_socket_send.</span></span>

<span data-ttu-id="11190-1895">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1895">**Information Fields**</span></span>

- <span data-ttu-id="11190-1896">정보 필드 1: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1896">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="11190-1897">정보 필드 2: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1897">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="11190-1898">정보 필드 3: 패킷 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1898">Info Field 3: Length of packet</span></span>
- <span data-ttu-id="11190-1899">정보 필드 4: 전송 시퀀스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1899">Info Field 4: Transmit sequence number</span></span>

### <a name="tcp-socket-state-wait"></a><span data-ttu-id="11190-1900">TCP 소켓 상태 대기</span><span class="sxs-lookup"><span data-stu-id="11190-1900">TCP Socket State Wait</span></span> 

#### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="11190-1901">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="11190-1901">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="11190-1902">**아이콘** ![TCP 소켓 상태 대기 아이콘](./media/user-guide/netx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1902">**Icon** ![T C P socket state wait icon](./media/user-guide/netx-events/image147.png)</span></span>

<span data-ttu-id="11190-1903">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1903">**Description**</span></span>

<span data-ttu-id="11190-1904">이 이벤트는 소켓이 nx_tcp_socket_state_wait를 통해 특정 상태가 될 때까지 대기하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1904">This event represents waiting for a socket to enter a particular state via nx_tcp_socket_state_wait.</span></span>

<span data-ttu-id="11190-1905">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1905">**Information Fields**</span></span>

- <span data-ttu-id="11190-1906">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1906">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1907">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1907">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1908">정보 필드 3: 원하는 소켓 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1908">Info Field 3: Desired socket state</span></span>
- <span data-ttu-id="11190-1909">정보 필드 4: 이전 소켓 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1909">Info Field 4: Previous socket state</span></span>

### <a name="tcp-socket-transmit-configure"></a><span data-ttu-id="11190-1910">TCP 소켓 전송 구성</span><span class="sxs-lookup"><span data-stu-id="11190-1910">TCP Socket Transmit Configure</span></span> 

#### <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="11190-1911">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="11190-1911">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="11190-1912">**아이콘** ![TCP 소켓 전송 구성 아이콘](./media/user-guide/netx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1912">**Icon** ![T C P socket transmit configure icon](./media/user-guide/netx-events/image148.png)</span></span>

<span data-ttu-id="11190-1913">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1913">**Description**</span></span>

<span data-ttu-id="11190-1914">이 이벤트는 nx_tcp_socket_transmit_configure를 통해 소켓의 전송 옵션을 구성하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1914">This event represents configuring the transmit options for a socket via nx_tcp_socket_transmit_configure.</span></span>

<span data-ttu-id="11190-1915">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1915">**Information Fields**</span></span>

- <span data-ttu-id="11190-1916">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1916">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1917">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1917">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1918">정보 필드 3: 전송 큐 깊이입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1918">Info Field 3: Transmit queue depth</span></span>
- <span data-ttu-id="11190-1919">정보 필드 4: 시간 제한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1919">Info Field 4: Timeout value</span></span>

### <a name="tcp-socket-window-update-notify-set"></a><span data-ttu-id="11190-1920">TCP 소켓 창 업데이트 알림 설정</span><span class="sxs-lookup"><span data-stu-id="11190-1920">TCP Socket Window Update Notify Set</span></span> 

#### <a name="nx_tcp_window_update_notify_set"></a><span data-ttu-id="11190-1921">nx_tcp_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="11190-1921">nx_tcp_window_update_notify_set</span></span>

<span data-ttu-id="11190-1922">**아이콘** ![TCP 소켓 창 업데이트 알림 설정 아이콘](./media/user-guide/netx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1922">**Icon** ![T C P socket window update notify set icon](./media/user-guide/netx-events/image149.png)</span></span>

<span data-ttu-id="11190-1923">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1923">**Description**</span></span>

<span data-ttu-id="11190-1924">이 이벤트는 nx_tcp_window_update_notify_set을 통해 원격 호스트 수신 기간을 늘린다는 알림을 수신하는 TCP 소켓을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1924">This event represents a TCP socket receiving notification of an increase in the remote host receive window via nx_tcp_window_update_notify_set.</span></span>

<span data-ttu-id="11190-1925">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1925">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1926">정보 필드 1: TCP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1926">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="11190-1927">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1927">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1928">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1928">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1929">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1929">Info Field 4: Not used</span></span>

### <a name="udp-enable"></a><span data-ttu-id="11190-1930">UDP 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1930">UDP Enable</span></span> 

#### <a name="nx_udp_enable"></a><span data-ttu-id="11190-1931">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1931">nx_udp_enable</span></span>

<span data-ttu-id="11190-1932">**아이콘** ![UDP 사용 아이콘](./media/user-guide/netx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1932">**Icon** ![U D P enable icon](./media/user-guide/netx-events/image150.png)</span></span>

<span data-ttu-id="11190-1933">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1933">**Description**</span></span>

<span data-ttu-id="11190-1934">이 이벤트는 nx_udp_enable을 통해 UDP를 사용하도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1934">This event represents enabling UDP via nx_udp_enable.</span></span>

<span data-ttu-id="11190-1935">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1935">**Information Fields**</span></span>

- <span data-ttu-id="11190-1936">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1936">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1937">정보 필드 2: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1937">Info Field 2: Not used</span></span>
- <span data-ttu-id="11190-1938">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1938">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1939">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1939">Info Field 4: Not used</span></span>

### <a name="udp-free-port-find"></a><span data-ttu-id="11190-1940">UDP 사용 가능한 포트 찾기</span><span class="sxs-lookup"><span data-stu-id="11190-1940">UDP Free Port Find</span></span> 

#### <a name="nx_udp_free_port_find"></a><span data-ttu-id="11190-1941">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="11190-1941">nx_udp_free_port_find</span></span>

<span data-ttu-id="11190-1942">**아이콘** ![UDP 사용 가능한 포트 찾기 아이콘](./media/user-guide/netx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1942">**Icon** ![U D P free port find icon](./media/user-guide/netx-events/image151.png)</span></span>

<span data-ttu-id="11190-1943">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1943">**Description**</span></span>

<span data-ttu-id="11190-1944">이 이벤트는 nx_udp_free_port_find를 통해 사용 가능한 UDP 포트를 찾는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1944">This event represents finding a free UDP port via nx_udp_free_port_find.</span></span>

<span data-ttu-id="11190-1945">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1945">**Information Fields**</span></span>

- <span data-ttu-id="11190-1946">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1946">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1947">정보 필드 2: 검색할 시작 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1947">Info Field 2: Starting port to search from</span></span>
- <span data-ttu-id="11190-1948">정보 필드 3: 사용 가능한 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1948">Info Field 3: Free port</span></span>
- <span data-ttu-id="11190-1949">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1949">Info Field 4: Not used</span></span>

### <a name="udp-information-get"></a><span data-ttu-id="11190-1950">UDP 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-1950">UDP Information Get</span></span> 

#### <a name="nx_udp_info_get"></a><span data-ttu-id="11190-1951">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="11190-1951">nx_udp_info_get</span></span>

<span data-ttu-id="11190-1952">**아이콘** ![UDP 정보 가져오기 아이콘](./media/user-guide/netx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1952">**Icon** ![U D P information get icon](./media/user-guide/netx-events/image152.png)</span></span>

<span data-ttu-id="11190-1953">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1953">**Description**</span></span>

<span data-ttu-id="11190-1954">이 이벤트는 nx_udp_info_get을 통한 정보 가져오기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1954">This event represents getting information via nx_udp_info_get.</span></span>

<span data-ttu-id="11190-1955">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1955">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1956">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1956">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1957">정보 필드 2: 송신한 UDP 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1957">Info Field 2: UDP bytes sent</span></span>
- <span data-ttu-id="11190-1958">정보 필드 3: 수신한 UDP 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1958">Info Field 3: UDP bytes received</span></span>
- <span data-ttu-id="11190-1959">정보 필드 4: 잘못된 패킷입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1959">Info Field 4: Invalid packets</span></span>

### <a name="udp-socket-bind"></a><span data-ttu-id="11190-1960">UDP 소켓 바인딩</span><span class="sxs-lookup"><span data-stu-id="11190-1960">UDP Socket Bind</span></span> 

#### <a name="nx_udp_socket_bind"></a><span data-ttu-id="11190-1961">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="11190-1961">nx_udp_socket_bind</span></span>

<span data-ttu-id="11190-1962">**아이콘** ![UDP 소켓 바인딩 아이콘](./media/user-guide/netx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1962">**Icon** ![U D P socket bind icon](./media/user-guide/netx-events/image153.png)</span></span>

<span data-ttu-id="11190-1963">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1963">**Description**</span></span>

<span data-ttu-id="11190-1964">이 이벤트는 nx_udp_socket_bind를 통해 UDP 소켓을 포트에 바인딩하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1964">This event represents binding a UDP socket to a port via nx_udp_socket_bind.</span></span>

<span data-ttu-id="11190-1965">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1965">**Information Fields**</span></span>

- <span data-ttu-id="11190-1966">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1966">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1967">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1967">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1968">정보 필드 3: 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1968">Info Field 3: Port number</span></span>
- <span data-ttu-id="11190-1969">정보 필드 4: 대기 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1969">Info Field 4: Wait option</span></span>

### <a name="udp-socket-bytes-available"></a><span data-ttu-id="11190-1970">UDP 소켓 사용 가능 바이트</span><span class="sxs-lookup"><span data-stu-id="11190-1970">UDP Socket Bytes Available</span></span> 

#### <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="11190-1971">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="11190-1971">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="11190-1972">**아이콘** ![UDP 소켓 사용 가능 바이트 아이콘](./media/user-guide/netx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1972">**Icon** ![U D P socket bytes available icon](./media/user-guide/netx-events/image154.png)</span></span>

<span data-ttu-id="11190-1973">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1973">**Description**</span></span>

<span data-ttu-id="11190-1974">이 이벤트는 nx_udp_socket_bytes_available을 통해 UDP 소켓에서 수신한 현재 바이트 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1974">This event represents the current number of bytes received on the UDP socket via nx_udp_socket_bytes_available.</span></span>

<span data-ttu-id="11190-1975">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1975">**Information Fields**</span></span>

- <span data-ttu-id="11190-1976">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1976">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1977">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1977">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1978">정보 필드 3: 소켓에서 수신한 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1978">Info Field 3: Bytes received on socket</span></span>
- <span data-ttu-id="11190-1979">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1979">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-disable"></a><span data-ttu-id="11190-1980">UDP 소켓 체크섬 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="11190-1980">UDP Socket Checksum Disable</span></span> 

#### <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="11190-1981">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="11190-1981">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="11190-1982">**아이콘** ![UDP 소켓 체크섬 사용 안 함 아이콘](./media/user-guide/netx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1982">**Icon** ![U D P socket checksum disable icon](./media/user-guide/netx-events/image155.png)</span></span>

<span data-ttu-id="11190-1983">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1983">**Description**</span></span>

<span data-ttu-id="11190-1984">이 이벤트는 nx_udp_socket_checksum_disable을 통해 UDP 소켓에서 데이터에 대한 체크섬을 사용하지 않도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1984">This event represents disabling the checksum for data on a UDP socket via nx_udp_socket_checksum_disable.</span></span>

<span data-ttu-id="11190-1985">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1985">**Information Fields**</span></span> 

- <span data-ttu-id="11190-1986">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1986">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1987">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1987">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1988">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1988">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1989">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1989">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-enable"></a><span data-ttu-id="11190-1990">UDP 소켓 체크섬 사용</span><span class="sxs-lookup"><span data-stu-id="11190-1990">UDP Socket Checksum Enable</span></span> 

#### <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="11190-1991">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="11190-1991">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="11190-1992">**아이콘** ![UDP 소켓 체크섬 사용 아이콘](./media/user-guide/netx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="11190-1992">**Icon** ![U D P socket checksum enable icon](./media/user-guide/netx-events/image156.png)</span></span>

<span data-ttu-id="11190-1993">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-1993">**Description**</span></span>

<span data-ttu-id="11190-1994">이 이벤트는 nx_udp_socket_checksum_enable을 통해 소켓에서 체크섬 처리를 사용하도록 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1994">This event represents enabling checksum processing on a socket via nx_udp_socket_checksum_enable.</span></span>

<span data-ttu-id="11190-1995">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-1995">**Information Fields**</span></span>

- <span data-ttu-id="11190-1996">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1996">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-1997">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1997">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-1998">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1998">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-1999">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-1999">Info Field 4: Not used</span></span>

### <a name="udp-socket-create"></a><span data-ttu-id="11190-2000">UDP 소켓 만들기</span><span class="sxs-lookup"><span data-stu-id="11190-2000">UDP Socket Create</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="11190-2001">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="11190-2001">nx_udp_socket_create</span></span>

<span data-ttu-id="11190-2002">**아이콘** ![UDP 소켓 만들기 아이콘](./media/user-guide/netx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="11190-2002">**Icon** ![U D P socket create icon](./media/user-guide/netx-events/image157.png)</span></span>

<span data-ttu-id="11190-2003">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-2003">**Description**</span></span>

<span data-ttu-id="11190-2004">이 이벤트는 nx_udp_socket_create을 통해 UDP 소켓을 만드는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2004">This event represents creating a UDP socket via nx_udp_socket_create.</span></span>

<span data-ttu-id="11190-2005">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-2005">**Information Fields**</span></span>

- <span data-ttu-id="11190-2006">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2006">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-2007">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2007">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-2008">정보 필드 3: 서비스 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2008">Info Field 3: Type of service</span></span>
- <span data-ttu-id="11190-2009">정보 필드 4: 최대 수신 큐입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2009">Info Field 4: Maximum receive queue</span></span>

### <a name="udp-socket-delete-event"></a><span data-ttu-id="11190-2010">UDP 소켓 삭제 이벤트</span><span class="sxs-lookup"><span data-stu-id="11190-2010">UDP Socket Delete Event</span></span> 

#### <a name="nx_udp_socket_delete-event"></a><span data-ttu-id="11190-2011">nx_udp_socket_delete event</span><span class="sxs-lookup"><span data-stu-id="11190-2011">nx_udp_socket_delete event</span></span>

<span data-ttu-id="11190-2012">**아이콘** ![UDP 소켓 삭제 이벤트 아이콘](./media/user-guide/netx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="11190-2012">**Icon** ![U D P socket delete event icon](./media/user-guide/netx-events/image158.png)</span></span>

<span data-ttu-id="11190-2013">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-2013">**Description**</span></span>

<span data-ttu-id="11190-2014">이 이벤트는 nx_udp_socket_delete를 통해 UDP 소켓을 삭제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2014">This event represents deleting a UDP socket via nx_udp_socket_delete.</span></span>

<span data-ttu-id="11190-2015">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-2015">**Information Fields**</span></span>

- <span data-ttu-id="11190-2016">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2016">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-2017">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2017">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-2018">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2018">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-2019">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2019">Info Field 4: Not used</span></span>

### <a name="udp-socket-information-get-event"></a><span data-ttu-id="11190-2020">UDP 소켓 정보 가져오기 이벤트</span><span class="sxs-lookup"><span data-stu-id="11190-2020">UDP Socket Information Get Event</span></span> 

#### <a name="nx_udp_socket_info_get-event"></a><span data-ttu-id="11190-2021">nx_udp_socket_info_get event</span><span class="sxs-lookup"><span data-stu-id="11190-2021">nx_udp_socket_info_get event</span></span>

<span data-ttu-id="11190-2022">**아이콘** ![UDP 소켓 정보 가져오기 이벤트 아이콘](./media/user-guide/netx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="11190-2022">**Icon** ![U D P socket information get event icon](./media/user-guide/netx-events/image159.png)</span></span>

<span data-ttu-id="11190-2023">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-2023">**Description**</span></span>

<span data-ttu-id="11190-2024">이 이벤트는 nx_udp_socket_info_get을 통해 UDP 소켓에 대한 정보를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2024">This event represents getting information about a UDP socket via nx_udp_socket_info_get.</span></span>

<span data-ttu-id="11190-2025">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-2025">**Information Fields**</span></span>

- <span data-ttu-id="11190-2026">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2026">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-2027">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2027">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-2028">정보 필드 3: 소켓을 통해 송신된 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2028">Info Field 3: Bytes sent through socket</span></span>
- <span data-ttu-id="11190-2029">정보 필드 4: 소켓을 통해 수신된 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2029">Info Field 4: Bytes received through socket</span></span>

### <a name="udp-socket-interface-set"></a><span data-ttu-id="11190-2030">UDP 소켓 인터페이스 설정</span><span class="sxs-lookup"><span data-stu-id="11190-2030">UDP Socket Interface Set</span></span> 

#### <a name="nx_udp_socket_interface_set-event"></a><span data-ttu-id="11190-2031">nx_udp_socket_interface_set event</span><span class="sxs-lookup"><span data-stu-id="11190-2031">nx_udp_socket_interface_set event</span></span>

<span data-ttu-id="11190-2032">**아이콘** ![UDP 소켓 인터페이스 설정 아이콘](./media/user-guide/netx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="11190-2032">**Icon** ![U D P socket interface set icon](./media/user-guide/netx-events/image160.png)</span></span>

<span data-ttu-id="11190-2033">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-2033">**Description**</span></span>

<span data-ttu-id="11190-2034">이 이벤트는 nx_udp_socket_interface_set을 통해 지정된 인터페이스를 사용하여 지정된 UDP 소켓의 송신 인터페이스를 설정하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2034">This event represents setting the outgoing interface of the specified UDP socket with the specified interface via nx_udp_socket_interface_set.</span></span>

<span data-ttu-id="11190-2035">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-2035">**Information Fields**</span></span>

- <span data-ttu-id="11190-2036">정보 필드 1: UDP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2036">Info Field 1: Pointer to UDP socket</span></span>
- <span data-ttu-id="11190-2037">정보 필드 2: 소켓의 인터페이스에 해당하는 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2037">Info Field 2: Index corresponding to the interface for the socket</span></span>
- <span data-ttu-id="11190-2038">정보 필드 3: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2038">Info Field 3: Not used</span></span>
- <span data-ttu-id="11190-2039">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2039">Info Field 4: Not used</span></span>

### <a name="udp-socket-port-get"></a><span data-ttu-id="11190-2040">UDP 소켓 포트 가져오기</span><span class="sxs-lookup"><span data-stu-id="11190-2040">UDP Socket Port Get</span></span> 

#### <a name="nx_udp_socket_port_get"></a><span data-ttu-id="11190-2041">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="11190-2041">nx_udp_socket_port_get</span></span>

<span data-ttu-id="11190-2042">**아이콘** ![UDP 소켓 포트 가져오기 아이콘](./media/user-guide/netx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="11190-2042">**Icon** ![U D P socket port get icon](./media/user-guide/netx-events/image161.png)</span></span>

<span data-ttu-id="11190-2043">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-2043">**Description**</span></span>

<span data-ttu-id="11190-2044">이 이벤트는 지정된 UDP 소켓이 nx_udp_socket_port_get을 통해 바인딩되는 UDP 포트를 검색하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2044">This event represents retrieving the UDP port the specified UDP socket is bound to via nx_udp_socket_port_get.</span></span>

<span data-ttu-id="11190-2045">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-2045">**Information Fields**</span></span>

- <span data-ttu-id="11190-2046">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2046">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-2047">정보 필드 2: UDP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2047">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="11190-2048">정보 필드 3: 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2048">Info Field 3: Port number</span></span>
- <span data-ttu-id="11190-2049">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2049">Info Field 4: Not used</span></span>

### <a name="udp-socket-receive"></a><span data-ttu-id="11190-2050">UDP 소켓 수신</span><span class="sxs-lookup"><span data-stu-id="11190-2050">UDP Socket Receive</span></span> 

#### <a name="nx_udp_socket_receive"></a><span data-ttu-id="11190-2051">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="11190-2051">nx_udp_socket_receive</span></span>

<span data-ttu-id="11190-2052">**아이콘** ![UDP 소켓 수신 아이콘](./media/user-guide/netx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="11190-2052">**Icon** ![U D P socket receive icon](./media/user-guide/netx-events/image162.png)</span></span>

<span data-ttu-id="11190-2053">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-2053">**Description**</span></span>

<span data-ttu-id="11190-2054">이 이벤트는 nx_udp_socket_receive를 통해 지정된 UDP 소켓에서 데이터를 수신하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2054">This event represents receiving data on the specified UDP socket via nx_udp_socket_receive.</span></span>

<span data-ttu-id="11190-2055">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-2055">**Information Fields**</span></span>

- <span data-ttu-id="11190-2056">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2056">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-2057">정보 필드 2: UDP 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2057">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="11190-2058">정보 필드 3 수신된 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2058">Info Field 3: Pointer to received packet</span></span>
- <span data-ttu-id="11190-2059">정보 필드 4 수신된 패킷 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2059">Info Field 4: Received packet size</span></span>

### <a name="udp-socket-receive-notify"></a><span data-ttu-id="11190-2060">UDP 소켓 수신 알림</span><span class="sxs-lookup"><span data-stu-id="11190-2060">UDP Socket Receive Notify</span></span> 

#### <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="11190-2061">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="11190-2061">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="11190-2062">**아이콘** ![UDP 소켓 수신 알림 아이콘](./media/user-guide/netx-events/image163.png) **설명**</span><span class="sxs-lookup"><span data-stu-id="11190-2062">**Icon** ![U D P socket receive notify icon](./media/user-guide/netx-events/image163.png)s **Description**</span></span>

<span data-ttu-id="11190-2063">이 이벤트는 nx_udp_socket_receive_notify를 통해 수신 알림 콜백을 등록하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2063">This event represents registering a receive notify callback via nx_udp_socket_receive_notify.</span></span>

<span data-ttu-id="11190-2064">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-2064">**Information Fields**</span></span>

- <span data-ttu-id="11190-2065">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2065">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-2066">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2066">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-2067">정보 필드 3: 수신 알림 함수에 대한 포인터입니다. 정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2067">Info Field 3: Pointer to receive notify function Info Field 4: Not used</span></span>

### <a name="udp-socket-send"></a><span data-ttu-id="11190-2068">UDP 소켓 송신</span><span class="sxs-lookup"><span data-stu-id="11190-2068">UDP Socket Send</span></span> 

#### <a name="nx_udp_socket_send"></a><span data-ttu-id="11190-2069">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="11190-2069">nx_udp_socket_send</span></span>

<span data-ttu-id="11190-2070">**아이콘** ![UDP 소켓 송신 아이콘](./media/user-guide/netx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="11190-2070">**Icon** ![U D P socket send icon](./media/user-guide/netx-events/image164.png)</span></span>

<span data-ttu-id="11190-2071">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-2071">**Description**</span></span>

<span data-ttu-id="11190-2072">이 이벤트는 nx_udp_socket_send를 사용하여 UDP 소켓을 통해 데이터를 보내는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2072">This event represents sending data through a UDP socket via nx_udp_socket_send.</span></span>

<span data-ttu-id="11190-2073">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-2073">**Information Fields**</span></span>

- <span data-ttu-id="11190-2074">정보 필드 1: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2074">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="11190-2075">정보 필드 2: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2075">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="11190-2076">정보 필드 3: 패킷 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2076">Info Field 3: Packet length</span></span>
- <span data-ttu-id="11190-2077">정보 필드 4: 대상 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2077">Info Field 4: Destination IP address</span></span>

### <a name="udp-socket-unbind"></a><span data-ttu-id="11190-2078">UDP 소켓 바인딩 해제</span><span class="sxs-lookup"><span data-stu-id="11190-2078">UDP Socket Unbind</span></span> 

#### <a name="nx_udp_socket_unbind"></a><span data-ttu-id="11190-2079">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="11190-2079">nx_udp_socket_unbind</span></span>

<span data-ttu-id="11190-2080">**아이콘** ![UDP 소켓 바인딩 해제 아이콘](./media/user-guide/netx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="11190-2080">**Icon** ![U D P socket unbind icon](./media/user-guide/netx-events/image165.png)</span></span>

<span data-ttu-id="11190-2081">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-2081">**Description**</span></span>

<span data-ttu-id="11190-2082">이 이벤트는 nx_udp_socket_unbind를 사용하여 소켓을 통해 UDP 포트를 바인딩 해제하는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2082">This event represents unbinding a UDP port with a socket via nx_udp_socket_unbind.</span></span>

<span data-ttu-id="11190-2083">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-2083">**Information Fields**</span></span>

- <span data-ttu-id="11190-2084">정보 필드 1: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2084">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="11190-2085">정보 필드 2: 소켓에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2085">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="11190-2086">정보 필드 3: 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2086">Info Field 3: Port number</span></span>
- <span data-ttu-id="11190-2087">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2087">Info Field 4: Not used</span></span>

### <a name="udp-source-extract"></a><span data-ttu-id="11190-2088">UDP 원본 추출</span><span class="sxs-lookup"><span data-stu-id="11190-2088">UDP Source Extract</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="11190-2089">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="11190-2089">nx_udp_socket_create</span></span>

<span data-ttu-id="11190-2090">**아이콘** ![UDP 원본 추출 아이콘](./media/user-guide/netx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="11190-2090">**Icon** ![U D P source extract icon](./media/user-guide/netx-events/image166.png)</span></span>

<span data-ttu-id="11190-2091">**설명**</span><span class="sxs-lookup"><span data-stu-id="11190-2091">**Description**</span></span>

<span data-ttu-id="11190-2092">이 이벤트는 nx_udp_source_extract를 통해 수신된 UDP 패킷의 IP 주소와 포트 번호를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2092">This event represents getting the IP address and port number of a received UDP packet via nx_udp_source_extract.</span></span>

<span data-ttu-id="11190-2093">**정보 필드**</span><span class="sxs-lookup"><span data-stu-id="11190-2093">**Information Fields**</span></span>

- <span data-ttu-id="11190-2094">정보 필드 1: 패킷에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2094">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="11190-2095">정보 필드 2: 발신자의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2095">Info Field 2: Sender's IP address</span></span>
- <span data-ttu-id="11190-2096">정보 필드 3: 발신자의 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2096">Info Field 3: Sender's port number</span></span>
- <span data-ttu-id="11190-2097">정보 필드 4: 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11190-2097">Info Field 4: Not used</span></span>