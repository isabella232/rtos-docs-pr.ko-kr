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
# <a name="chapter-8---azure-rtos-netx-trace-events"></a>8장 - Azure RTOS NetX 추적 이벤트

이 장에서는 Azure RTOS NetX 이벤트에 대한 설명을 다룹니다. 

## <a name="list-of-events-and-icons"></a>이벤트 및 아이콘 목록

다음은 TraceX에 의해 표시되는 NetX 이벤트 목록입니다.

| 아이콘                                           | 의미                 |
| -------------------------------- | ------------------------------------- |
| ![내부 ARP 요청 수신 아이콘](./media/user-guide/netx-events/image1.png)    | 내부 ARP 요청 수신 |
| ![내부 ARP 요청 송신 아이콘](./media/user-guide/netx-events/image2.png)    | 내부 ARP 요청 송신 |
| ![내부 ARP 응답 수신 아이콘](./media/user-guide/netx-events/image3.png)    | 내부 ARP 응답 수신 |
| ![내부 ARP 응답 송신 아이콘](./media/user-guide/netx-events/image4.png)    | 내부 ARP 응답 송신 |
| ![내부 ICMP 수신 아이콘](./media/user-guide/netx-events/image5.png)    | 내부 ICMP 수신 |
| ![내부 ICMP 송신 아이콘](./media/user-guide/netx-events/image6.png)    | 내부 ICMP 송신 |
| ![내부 NetX IGMP 수신 아이콘](./media/user-guide/netx-events/image7.png)    | 내부 NetX IGMP 수신 |
| ![내부 IP 수신 아이콘](./media/user-guide/netx-events/image8.png)    | 내부 IP 수신 |
| ![내부 IP 송신 아이콘](./media/user-guide/netx-events/image9.png)    | 내부 IP 송신 |
| ![내부 TCP 데이터 수신 아이콘](./media/user-guide/netx-events/image10.png)    | 내부 TCP 데이터 수신 |
| ![내부 TCP 데이터 송신 아이콘](./media/user-guide/netx-events/image11.png)    | 내부 TCP 데이터 송신 |
| ![내부 TCP FIN 수신 아이콘](./media/user-guide/netx-events/image12.png)    | 내부 TCP FIN 수신 |
| ![내부 TCP FIN 송신 아이콘](./media/user-guide/netx-events/image13.png)    | 내부 TCP FIN 송신 |
| ![내부 TCP RST 수신 아이콘](./media/user-guide/netx-events/image14.png)    | 내부 TCP RST 수신 |
| ![내부 TCP RST 송신 아이콘](./media/user-guide/netx-events/image15.png)    | 내부 TCP RST 송신 |
| ![내부 TCP SYN 수신 아이콘](./media/user-guide/netx-events/image16.png)    | 내부 TCP SYN 수신 |
| ![내부 TCP SYN 송신 아이콘](./media/user-guide/netx-events/image17.png)    | 내부 TCP SYN 송신 |
| ![내부 UDP 수신 아이콘](./media/user-guide/netx-events/image18.png)    | 내부 UDP 수신 |
| ![내부 UDP 송신 아이콘](./media/user-guide/netx-events/image19.png)    | 내부 UDP 송신 |
| ![내부 RARP 수신 아이콘](./media/user-guide/netx-events/image20.png)    | 내부 RARP 수신 |
| ![내부 RARP 송신 아이콘](./media/user-guide/netx-events/image21.png)    | 내부 RARP 송신 |
| ![내부 TCP 다시 시도 아이콘](./media/user-guide/netx-events/image22.png)    | 내부 TCP 다시 시도 |
| ![내부 TCP 상태 변경 아이콘](./media/user-guide/netx-events/image23.png)    | 내부 TCP 상태 변경 |
| ![내부 I/O 드라이버 패킷 송신 아이콘](./media/user-guide/netx-events/image24.png)    | 내부 I/O 드라이버 패킷 송신 |
| ![icon](./media/user-guide/netx-events/image25.png)    | 내부 I/O 드라이버 초기화 |
| ![내부 I/O 드라이버 초기화 아이콘](./media/user-guide/netx-events/image26.png)    | 내부 I/O 드라이버 링크 사용 |
| ![내부 I/O 드라이버 링크 사용 안 함 아이콘](./media/user-guide/netx-events/image27.png)    | 내부 I/O 드라이버 링크 사용 안 함 |
| ![내부 I/O 드라이버 패킷 브로드캐스트 아이콘](./media/user-guide/netx-events/image28.png)    | 내부 I/O 드라이버 패킷 브로드캐스트 |
| ![내부 I/O 드라이버 ARP 송신 아이콘](./media/user-guide/netx-events/image29.png)    | 내부 I/O 드라이버 ARP 송신 |
| ![내부 I/O 드라이버 ARP 응답 송신 아이콘](./media/user-guide/netx-events/image30.png)    | 내부 I/O 드라이버 ARP 응답 송신 |
| ![내부 I/O 드라이버 RARP 송신 아이콘](./media/user-guide/netx-events/image31.png)    | 내부 I/O 드라이버 RARP 송신 |
| ![내부 I/O 드라이버 멀티캐스트 조인 아이콘](./media/user-guide/netx-events/image32.png)    | 내부 I/O 드라이버 멀티캐스트 조인 |
| ![내부 I/O 드라이버 멀티캐스트 탈퇴 아이콘](./media/user-guide/netx-events/image33.png)    | 내부 I/O 드라이버 멀티캐스트 탈퇴 |
| ![내부 I/O 드라이버 상태 가져오기 아이콘](./media/user-guide/netx-events/image34.png)    | 내부 I/O 드라이버 상태 가져오기 |
| ![내부 I/O 드라이버 속도 가져오기 아이콘](./media/user-guide/netx-events/image35.png)    | 내부 I/O 드라이버 속도 가져오기 |
| ![내부 I/O 드라이버 이중 형식 가져오기 아이콘](./media/user-guide/netx-events/image36.png)    | 내부 I/O 드라이버 이중 형식 가져오기 |
| ![내부 I/O 드라이버 오류 수 가져오기 아이콘](./media/user-guide/netx-events/image37.png)    | 내부 I/O 드라이버 오류 수 가져오기 |
| ![내부 I/O 드라이버 RX 수 가져오기 아이콘](./media/user-guide/netx-events/image38.png)    | 내부 I/O 드라이버 RX 수 가져오기 |
| ![내부 I/O 드라이버 TX 수 가져오기 아이콘](./media/user-guide/netx-events/image39.png)    | 내부 I/O 드라이버 TX 수 가져오기 |
| ![내부 I/O 드라이버 할당 오류 가져오기 아이콘](./media/user-guide/netx-events/image40.png)    | 내부 I/O 드라이버 할당 오류 가져오기 |
| ![내부 I/O 드라이버 초기화 취소 아이콘](./media/user-guide/netx-events/image41.png)    | 내부 I/O 드라이버 초기화 취소 |
| ![내부 I/O 드라이버 지연 처리 아이콘](./media/user-guide/netx-events/image42.png)    | 내부 I/O 드라이버 지연 처리 |
| ![ARP 동적 항목 무효화 아이콘](./media/user-guide/netx-events/image43.png)    | **ARP 동적 항목 무효화**(nx_arp_dynamic_entries_invalidate) |
| ![ARP 동적 항목 설정 아이콘](./media/user-guide/netx-events/image44.png)    | **ARP 동적 항목 설정**(nx_arp_dynamic_entry_set) |
| ![ARP 사용 아이콘](./media/user-guide/netx-events/image45.png)    | **ARP 사용**(nx_arp_enable) |
| ![ARP 무상 송신 아이콘](./media/user-guide/netx-events/image46.png)    | **ARP 무상 송신**(nx_arp_gratuitous_send) |
| ![ARP 하드웨어 주소 찾기 아이콘](./media/user-guide/netx-events/image47.png)    | **ARP 하드웨어 주소 찾기**(nx_arp_hardware_address_find) |
| ![ARP 정보 가져오기 아이콘](./media/user-guide/netx-events/image48.png)    | **ARP 정보 가져오기**(nx_arp_info_get) |
| ![ARP IP 주소 찾기 아이콘](./media/user-guide/netx-events/image49.png)    | **ARP IP 주소 찾기**(nx_arp_ip_address_find) |
| ![ARP 정적 항목 만들기 아이콘](./media/user-guide/netx-events/image50.png)    | **ARP 정적 항목 만들기**(nx_arp_static_entry_create) |
| ![ARP 정적 항목 삭제 아이콘](./media/user-guide/netx-events/image51.png)    | **ARP 정적 항목 삭제**(nx_arp_static_entries_delete) |
| ![ARP 정적 항목 삭제 아이콘](./media/user-guide/netx-events/image52.png)    | **ARP 정적 항목 삭제**(nx_arp_static_entry_delete) |
| ![Duo 캐시 항목 삭제 아이콘](./media/user-guide/netx-events/image53.png)    | **Duo 캐시 항목 삭제**(nxd_nd_cache_entry_delete) |
| ![Duo 캐시 항목 설정 아이콘](./media/user-guide/netx-events/image54.png)    | **Duo 캐시 항목 설정**(nxd_nd_cache_entry_set) |
| ![Duo 캐시 무효화 아이콘](./media/user-guide/netx-events/image55.png)    | **Duo 캐시 무효화**(nxd_nd_cache_invalidate) |
| ![Duo 캐시 IP 주소 찾기 아이콘](./media/user-guide/netx-events/image56.png)    | **Duo 캐시 IP 주소 찾기**(nxd_nd_cache_ip_address_find) |
| ![DUO ICMP 사용 아이콘](./media/user-guide/netx-events/image57.png)    | **DUO ICMP 사용**(nxd_icmp_enable) |
| ![DUO ICMP IPv6 Ping 아이콘](./media/user-guide/netx-events/image58.png)    | **DUO ICMP IPv6 Ping**(nxd_icmp_ping) |
| ![Duo IP 최대 페이로드 크기 찾기 아이콘](./media/user-guide/netx-events/image59.png)    | **DUO IP 최대 페이로드 크기 찾기**(nx_max_payload_size_find) |
| ![Duo IP 원시 패킷 송신 아이콘](./media/user-guide/netx-events/image60.png)    | **DUO IP 원시 패킷 송신**(nxd_ip_raw_packet_send) |
| ![Duo IPv6 기본 라우터 추가 아이콘](./media/user-guide/netx-events/image61.png)    | **Duo IPv6 기본 라우터 추가**(nxd_ipv6_default_router_add) |
| ![Duo IPv6 기본 라우터 삭제 아이콘](./media/user-guide/netx-events/image62.png)    | **Duo IPv6 기본 라우터 삭제**(nxd_ipv6_default_router_delete) |
| ![Duo IPv6 사용 아이콘](./media/user-guide/netx-events/image63.png)    | **Duo IPv6 사용**(nxd_ipv6_enable) |
| ![Duo IPv6 전체 주소 가져오기 아이콘](./media/user-guide/netx-events/image64.png)    | **Duo IPv6 전체 주소 가져오기**(nxd_ipv6_global_address_get) |
| ![Duo IPv6 전체 주소 설정 아이콘](./media/user-guide/netx-events/image65.png)    | **Duo IPv6 전체 주소 설정**(nxd_ipv6_global_address_set) |
| ![Duo IPv6 DAD 프로세스 시작 아이콘](./media/user-guide/netx-events/image66.png)    | **Duo IPv6 DAD 프로세스 시작**(nxd_ipv6_initiate_dad_process) |
| ![Duo IPv6 인터페이스 주소 가져오기 아이콘](./media/user-guide/netx-events/image67.png)    | **Duo IPv6 인터페이스 주소 가져오기**(nxd_ipv6_interface_address_get) |
| ![Duo IPv6 인터페이스 주소 설정 아이콘](./media/user-guide/netx-events/image68.png)    | **Duo IPv6 인터페이스 주소 설정**(nxd_ipv6_interface_address_set) |
| ![Duo IPv6 링크 로컬 주소 가져오기 아이콘](./media/user-guide/netx-events/image69.png)    | **Duo IPv6 링크 로컬 주소 가져오기**(nxd_ipv6_linklocal_address_get) |
| ![Duo IPv6 링크 로컬 주소 설정 아이콘](./media/user-guide/netx-events/image70.png)    | **Duo IPv6 링크 로컬 주소 설정**(nxd_ipv6_linklocal_address_set) |
| ![Duo IPv6 원시 패킷 송신 아이콘](./media/user-guide/netx-events/image71.png)    | **Duo IPv6 원시 패킷 송신**(nxd_ipv6_raw_packet_send) |
| ![DUO TCP 소켓 피어 정보 가져오기 아이콘](./media/user-guide/netx-events/image72.png)    | **DUO TCP 소켓 피어 정보 가져오기**(nxd_tcp_socket_peer_info_get) |
| ![Duo TCP 소켓 설정 인터페이스 아이콘](./media/user-guide/netx-events/image73.png)    | **Duo TCP 소켓 설정 인터페이스**(nxd_tcp_socket_set_interface) |
| ![Duo UDP 소켓 송신 아이콘](./media/user-guide/netx-events/image74.png)    | **DUO UDP 소켓 송신**(nxd_udp_socket_send) |
| ![Duo UDP 소켓 설정 인터페이스 아이콘](./media/user-guide/netx-events/image75.png)    | **Duo UDP 소켓 설정 인터페이스**(nxd_udp_socket_set_interface) |
| ![Duo UDP 원본 추출 아이콘](./media/user-guide/netx-events/image76.png)    | **DUO UDP 원본 추출**(nxd_udp_source_extract) |
| ![ICMP 사용 아이콘](./media/user-guide/netx-events/image77.png)    | **ICMP 사용**(nx_icmp_enable) |
| ![ICMP 정보 가져오기 아이콘](./media/user-guide/netx-events/image78.png)    | **ICMP 정보 가져오기**(nx_icmp_info_get) |
| ![ICMP Ping 아이콘](./media/user-guide/netx-events/image79.png)    | **ICMP Ping**(nx_icmp_ping) |
| ![IGMP 사용 아이콘](./media/user-guide/netx-events/image80.png)    | **IGMP 사용**(nx_igmp_enable) |
| ![IGMP 정보 가져오기 아이콘](./media/user-guide/netx-events/image81.png)    | **IGMP 정보 가져오기**(nx_igmp_info_get) |
| ![IGMP 루프백 사용 안 함 아이콘](./media/user-guide/netx-events/image82.png)    | **IGMP 루프백 사용 안 함**(nx_igmp_loopback_disable) |
| ![IGMP 루프백 사용 아이콘](./media/user-guide/netx-events/image83.png)    | **IGMP 루프백 사용**(nx_igmp_loopback_enable) |
| ![IGMP 멀티캐스트 조인 아이콘](./media/user-guide/netx-events/image84.png)    | **IGMP 멀티캐스트 조인**(nx_igmp_multicast_join) |
| ![IGMP 멀티캐스트 탈퇴 아이콘](./media/user-guide/netx-events/image85.png)    | **IGMP 멀티캐스트 탈퇴**(nx_igmp_multicast_leave) |
| ![IP 주소 변경 알림 아이콘](./media/user-guide/netx-events/image86.png)    | **IP 주소 변경 알림**(nx_ip_address_change_notify) |
| ![IP 주소 가져오기 아이콘](./media/user-guide/netx-events/image87.png)    | **IP 주소 가져오기**(nx_ip_address_get) |
| ![IP 주소 설정 아이콘](./media/user-guide/netx-events/image88.png)    | **IP 주소 설정**(nx_ip_address_set) |
| ![IP 만들기 아이콘](./media/user-guide/netx-events/image89.png)    | **IP 만들기**(nx_ip_create) |
| ![IP 삭제 아이콘](./media/user-guide/netx-events/image90.png)    | **IP 삭제**(nx_ip_delete) |
| ![IP 드라이버 직접 명령 아이콘](./media/user-guide/netx-events/image91.png)    | **IP 드라이버 직접 명령**(nx_ip_driver_direct_command) |
| ![IP 전달 사용 안 함 아이콘](./media/user-guide/netx-events/image92.png)    | **IP 전달 사용 안 함**(nx_ip_forwarding_disable) |
| ![IP 전달 사용 아이콘](./media/user-guide/netx-events/image93.png)    | **IP 전달 사용**(nx_ip_forwarding_enable) |
| ![IP 조각 사용 안 함 아이콘](./media/user-guide/netx-events/image94.png)    | **IP 조각 사용 안 함**(nx_ip_fragment_disable) |
| ![I P 조각 사용 아이콘](./media/user-guide/netx-events/image95.png)    | **IP 조각 사용**(nx_ip_fragment_enable)  |
| ![IP 게이트웨이 주소 설정 아이콘](./media/user-guide/netx-events/image96.png)    | **IP 게이트웨이 주소 설정**(nx_ip_gateway_address_set) |
| ![IP 정보 가져오기 아이콘](./media/user-guide/netx-events/image97.png)    | **IP 정보 가져오기**(nx_ip_info_get) |
| ![IP 인터페이스 연결 아이콘](./media/user-guide/netx-events/image98.png)    | **IP 인터페이스 연결**(nx_ip_interface_attach) |
| ![IP 인터페이스 정보 가져오기 아이콘](./media/user-guide/netx-events/image99.png)    | **IP 인터페이스 정보 가져오기**(nx_ip_interface_info_get) |
| ![IP 원시 패킷 사용 안 함 아이콘](./media/user-guide/netx-events/image100.png)    | **IP 원시 패킷 사용 안 함**(nx_ip_raw_packet_disable) |
| ![IP 원시 패킷 사용 아이콘](./media/user-guide/netx-events/image101.png)    | **IP 원시 패킷 사용**(nx_ip_raw_packet_enable) |
| ![IP 원시 패킷 수신 아이콘](./media/user-guide/netx-events/image102.png)    | **IP 원시 패킷 수신**(nx_ip_raw_packet_receive) |
| ![IP 원시 패킷 송신 아이콘](./media/user-guide/netx-events/image103.png)    | **IP 원시 패킷 송신**(nx_ip_raw_packet_send) |
| ![IP 고정 경로 추가 아이콘](./media/user-guide/netx-events/image104.png)    | **IP 고정 경로 추가**(nx_ip_static_route_add) |
| ![IP 고정 경로 삭제 아이콘](./media/user-guide/netx-events/image105.png)    | **IP 고정 경로 삭제**(nx_ip_static_route_delete) |
| ![IP 상태 확인 아이콘](./media/user-guide/netx-events/image106.png)    | **IP 상태 확인**(nx_ip_status_check)|
| ![IPSEC 사용 아이콘](./media/user-guide/netx-events/image107.png)    | **IPSEC 사용**(nx_ipsec_enable) |
| ![패킷 할당 아이콘](./media/user-guide/netx-events/image108.png)    | **패킷 할당**(nx_packet_allocate) |
| ![패킷 복사 아이콘](./media/user-guide/netx-events/image109.png)    | **패킷 복사**(nx_packet_copy) |
| ![패킷 데이터 추가 아이콘](./media/user-guide/netx-events/image110.png)    | **패킷 데이터 추가**(nx_packet_data_append) |
| ![패킷 데이터 추출 오프셋 아이콘](./media/user-guide/netx-events/image111.png)    | **패킷 데이터 추출 오프셋**(nx_packet_data_extract_offset) |
| ![패킷 데이터 검색 아이콘](./media/user-guide/netx-events/image112.png)    | **패킷 데이터 검색**(nx_packet_data_retrieve) |
| ![패킷 길이 가져오기 아이콘](./media/user-guide/netx-events/image113.png)    | **패킷 길이 가져오기**(nx_packet_length_get) |
| ![패킷 풀 만들기 아이콘](./media/user-guide/netx-events/image114.png)    | **패킷 풀 만들기**(nx_packet_pool_create) |
| ![패킷 풀 삭제 아이콘](./media/user-guide/netx-events/image115.png)    | **패킷 풀 삭제**(nx_packet_pool_delete) |
| ![패킷 풀 정보 가져오기 아이콘](./media/user-guide/netx-events/image116.png)    | **패킷 풀 정보 가져오기**(nx_packet_pool_info_get) |
| ![패킷 해제 아이콘](./media/user-guide/netx-events/image117.png)    | **패킷 해제**(nx_packet_release) |
| ![패킷 전송 해제 아이콘](./media/user-guide/netx-events/image118.png)    | **패킷 전송 해제**(nx_packet_transmit_release) |
| ![RARP 사용 안 함 아이콘](./media/user-guide/netx-events/image119.png)    | **RARP 사용 안 함**(nx_rarp_disable) |
| ![RARP 사용 아이콘](./media/user-guide/netx-events/image120.png)    | **RARP 사용**(nx_rarp_enable) |
| ![RARP 정보 가져오기 아이콘](./media/user-guide/netx-events/image121.png)    | **RARP 정보 가져오기**(nx_rarp_info_get) |
| ![시스템 초기화 아이콘](./media/user-guide/netx-events/image122.png)    | **시스템 초기화**(fx_system_initialize) |
| ![TCP 클라이언트 소켓 바인딩 아이콘](./media/user-guide/netx-events/image123.png)    | **TCP 클라이언트 소켓 바인딩**(nx_tcp_client_socket_bind) |
| ![TCP 클라이언트 소켓 연결 아이콘](./media/user-guide/netx-events/image124.png)    | **TCP 클라이언트 소켓 연결**(nx_tcp_client_socket_connect) |
| ![TCP 클라이언트 소켓 포트 가져오기 아이콘](./media/user-guide/netx-events/image125.png)    | **TCP 클라이언트 소켓 포트 가져오기**(nx_tcp_client_socket_port_get) |
| ![TCP 클라이언트 소켓 바인딩 해제 아이콘](./media/user-guide/netx-events/image126.png)    | **TCP 클라이언트 소켓 바인딩 해제**(nx_tcp_client_socket_unbind) |
| ![TCP 사용 아이콘](./media/user-guide/netx-events/image127.png)    | **TCP 사용**(nx_tcp_enable) |
| ![TCP 사용 가능한 포트 찾기 아이콘](./media/user-guide/netx-events/image128.png)    | **TCP 사용 가능한 포트 찾기**(nx_tcp_free_port_find) |
| ![TCP 정보 가져오기 아이콘](./media/user-guide/netx-events/image129.png)    | **TCP 정보 가져오기**(nx_tcp_info_get) |
| ![TCP 서버 소켓 수락 아이콘](./media/user-guide/netx-events/image130.png)    | **TCP 서버 소켓 수락**(nx_tcp_server_socket_accept) |
| ![TCP 서버 소켓 수신 대기 아이콘](./media/user-guide/netx-events/image131.png)    | **TCP 서버 소켓 수신 대기**(nx_tcp_server_socket_listen) |
| ![TCP 서버 소켓 다시 수신 대기 아이콘](./media/user-guide/netx-events/image132.png)    | **TCP 서버 소켓 다시 수신 대기**(nx_tcp_server_socket_relisten) |
| ![TCP 서버 소켓 허용 안 함 아이콘](./media/user-guide/netx-events/image133.png)    | **TCP 서버 소켓 허용 안 함**(nx_tcp_server_socket_unaccept) |
| ![T C P 서버 소켓 수신 대기 취소 아이콘](./media/user-guide/netx-events/image134.png)    | **TCP 서버 소켓 수신 대기 취소**(nx_tcp_server_socket_unlisten) |
| ![TCP 소켓 사용 가능 바이트 아이콘](./media/user-guide/netx-events/image135.png)    | **TCP 소켓 사용 가능 바이트**(nx_tcp_socket_bytes_available) |
| ![TCP 소켓 만들기 아이콘](./media/user-guide/netx-events/image136.png)    | **TCP 소켓 만들기**(nx_tcp_socket_create) |
| ![TCP 소켓 삭제 아이콘](./media/user-guide/netx-events/image137.png)    | **TCP 소켓 삭제**(nx_tcp_socket_delete) |
| ![TCP 소켓 연결 끊기 아이콘](./media/user-guide/netx-events/image138.png)    | **TCP 소켓 연결 끊기**(nx_tcp_socket_disconnect) |
| ![TCP 소켓 정보 가져오기 아이콘](./media/user-guide/netx-events/image139.png)    | **TCP 소켓 정보 가져오기**(nx_tcp_socket_info_get) |
| ![TCP 소켓 MSS 가져오기 아이콘](./media/user-guide/netx-events/image140.png)    | **TCP 소켓 MSS 가져오기**(nx_tcp_socket_mss_get) |
| ![TCP 소켓 MSS 피어 가져오기 아이콘](./media/user-guide/netx-events/image141.png)    | **TCP 소켓 MSS 피어 가져오기**(nx_tcp_socket_mss_peer_get) |
| ![TCP 소켓 MSS 설정 아이콘](./media/user-guide/netx-events/image142.png)    | **TCP 소켓 MSS 설정**(nx_tcp_socket_mss_set) |
| ![TCP 소켓 피어 정보 가져오기 아이콘](./media/user-guide/netx-events/image143.png)    | **TCP 소켓 피어 정보 가져오기**(nx_tcp_socket_peer_info_get) |
| ![TCP 소켓 수신 아이콘](./media/user-guide/netx-events/image144.png)    | **TCP 소켓 수신**(nx_tcp_socket_receive) |
| ![TCP 소켓 수신 알림 아이콘](./media/user-guide/netx-events/image145.png)    | **TCP 소켓 수신 알림**(nx_tcp_socket_receive_notify) |
| ![TCP 소켓 송신 아이콘](./media/user-guide/netx-events/image146.png)    | **TCP 소켓 송신**(nx_tcp_socket_send) |
| ![TCP 소켓 상태 대기 아이콘](./media/user-guide/netx-events/image147.png)    | **TCP 소켓 상태 대기**(nx_tcp_socket_state_wait) |
| ![TCP 소켓 전송 구성 아이콘](./media/user-guide/netx-events/image148.png)    | **TCP 소켓 전송 구성**(nx_tcp_socket_transmit_configure) |
| ![TCP 소켓 창 업데이트 알림 설정 아이콘](./media/user-guide/netx-events/image149.png)    | **TCP 소켓 창 업데이트 알림 설정**(nx_tcp_socket_window_update_notify_set)  |
| ![UDP 사용 아이콘](./media/user-guide/netx-events/image150.png)    | **UDP 사용**(nx_udp_enable) |
| ![UDP 사용 가능한 포트 찾기 아이콘](./media/user-guide/netx-events/image151.png)    | **UDP 사용 가능한 포트 찾기**(nx_udp_free_port_find) |
| ![UDP 정보 가져오기 아이콘](./media/user-guide/netx-events/image152.png)    | **UDP 정보 가져오기**(nx_udp_info_get) |
| ![UDP 소켓 바인딩 아이콘](./media/user-guide/netx-events/image153.png)    | **UDP 소켓 바인딩**(nx_udp_socket_bind) |
| ![UDP 소켓 사용 가능 바이트 아이콘](./media/user-guide/netx-events/image154.png)    | **UDP 소켓 사용 가능 바이트**(nx_udp_socket_bytes_available) |
| ![U D P 소켓 체크섬 사용 안 함 아이콘](./media/user-guide/netx-events/image155.png)    | **UDP 소켓 체크섬 사용 안 함**(nx_udp_socket_checksum_disable) |
| ![UDP 소켓 체크섬 사용 아이콘](./media/user-guide/netx-events/image156.png)    | **UDP 소켓 체크섬 사용**(nx_udp_socket_checksum_enable) |
| ![UDP 소켓 만들기 아이콘](./media/user-guide/netx-events/image157.png)    | **UDP 소켓 만들기**(nx_udp_socket_create) |
| ![UDP 소켓 삭제 아이콘](./media/user-guide/netx-events/image158.png)    | **UDP 소켓 삭제**(nx_udp_socket_delete) |
| ![UDP 소켓 정보 가져오기 아이콘](./media/user-guide/netx-events/image159.png)    | **UDP 소켓 정보 가져오기**(nx_udp_socket_info_get) |
| ![UDP 소켓 인터페이스 설정 아이콘](./media/user-guide/netx-events/image160.png)    | **UDP 소켓 인터페이스 설정**(nx_udp_socket_interface_set) |
| ![UDP 소켓 포트 가져오기 아이콘](./media/user-guide/netx-events/image161.png)    | **UDP 소켓 포트 가져오기**(nx_udp_socket_port_get) |
| ![UDP 소켓 수신 아이콘](./media/user-guide/netx-events/image162.png)    | **UDP 소켓 수신**(nx_udp_socket_receive) |
| ![UDP 소켓 수신 알림 아이콘](./media/user-guide/netx-events/image163.png)    | **UDP 소켓 수신 알림**(nx_udp_socket_receive_notify) |
| ![UDP 소켓 송신 아이콘](./media/user-guide/netx-events/image164.png)    | **UDP 소켓 송신**(nx_udp_socket_send) |
| ![UDP 소켓 바인딩 해제 아이콘](./media/user-guide/netx-events/image165.png)    | **UDP 소켓 바인딩 해제**(nx_udp_socket_unbind) |
| ![UDP 원본 추출 아이콘](./media/user-guide/netx-events/image166.png)    | **UDP 원본 추출**(nx_udp_source_extract) |

## <a name="event-descriptions"></a>이벤트 설명

다음 페이지에서는 NetX 추적 이벤트에 대해 설명합니다.

### <a name="internal-arp-request-receive"></a>내부 ARP 요청 수신 

#### <a name="internal-arp-request-receive"></a>내부 ARP 요청 수신

**아이콘** ![내부 ARP 요청 수신 아이콘](./media/user-guide/netx-events/image1.png)

**설명**

이 이벤트는 내부 NetX ARP 요청 수신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 원본 IP 주소입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-arp-request-send"></a>내부 ARP 요청 송신 

#### <a name="internal-arp-request-send"></a>내부 ARP 요청 송신

**아이콘** ![내부 ARP 요청 송신 아이콘](./media/user-guide/netx-events/image2.png)

**설명**

이 이벤트는 내부 NetX ARP 요청 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 대상 IP 주소입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-arp-response-receive"></a>내부 ARP 응답 수신 

#### <a name="internal-arp-request-receive"></a>내부 ARP 요청 수신

**아이콘** ![내부 ARP 요청 수신 아이콘](./media/user-guide/netx-events/image3.png)

**설명**

이 이벤트는 내부 NetX ARP 응답 수신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 원본 IP 주소입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-arp-response-send"></a>내부 ARP 응답 송신 

#### <a name="internal-arp-request-send"></a>내부 ARP 요청 송신

**아이콘** ![내부 ARP 요청 송신 아이콘](./media/user-guide/netx-events/image4.png)

**설명**

이 이벤트는 내부 NetX 응답 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 대상 IP 주소입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-icmp-receive"></a>내부 ICMP 수신 

#### <a name="internal-icmp-receive"></a>내부 ICMP 수신

**아이콘** ![내부 ICMP 수신 아이콘](./media/user-guide/netx-events/image5.png)

**설명**

이 이벤트는 내부 NetX ICMP 수신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 원본 IP 주소입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: ICMP 헤더의 단어 0입니다.

### <a name="internal-icmp-send"></a>내부 ICMP 송신 

#### <a name="internal-icmp-send"></a>내부 ICMP 송신

**아이콘** ![내부 ICMP 송신 아이콘](./media/user-guide/netx-events/image6.png)

**설명**

이 이벤트는 내부 NetX ICMP 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 대상 IP 주소입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: ICMP 헤더의 단어 0입니다.

### <a name="internal-igmp-receive"></a>내부 IGMP 수신 

#### <a name="internal-igmp-receive"></a>내부 IGMP 수신

**아이콘** ![내부 IGMP 수신 아이콘](./media/user-guide/netx-events/image7.png)

**설명**

이 이벤트는 내부 NetX IGMP 수신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 포인터입니다.
- 정보 필드 2: 원본 IP 주소입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: IGMP 헤더의 단어 0입니다.

### <a name="internal-ip-receive"></a>내부 IP 수신 

#### <a name="internal-ip-receive"></a>내부 IP 수신

**아이콘** ![내부 IP 수신 아이콘](./media/user-guide/netx-events/image8.png)

**설명**

이 이벤트는 내부 NetX IP 수신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 원본 IP 주소입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 패킷 길이입니다.

### <a name="internal-ip-send"></a>내부 IP 송신

#### <a name="internal-ip-send"></a>내부 IP 송신

**아이콘** ![내부 IP 송신 아이콘](./media/user-guide/netx-events/image9.png)

**설명**

이 이벤트는 내부 NetX IP 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 대상 IP 주소입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 패킷 길이입니다.

### <a name="internal-tcp-data-receive"></a>내부 TCP 데이터 수신 

#### <a name="internal-tcp-data-receive"></a>내부 TCP 데이터 수신

**아이콘** ![내부 TCP 데이터 수신 아이콘](./media/user-guide/netx-events/image10.png)

**설명**

이 이벤트는 내부 NetX TCP 데이터 수신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 원본 IP 주소입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 수신 시퀀스 번호입니다.

### <a name="internal-tcp-data-send"></a>내부 TCP 데이터 송신 

#### <a name="internal-tcp-data-send"></a>내부 TCP 데이터 송신

**아이콘** ![내부 TCP 데이터 송신 아이콘](./media/user-guide/netx-events/image11.png)

**설명**

이 이벤트는 내부 NetX TCP 데이터 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 전송 시퀀스 번호입니다.

### <a name="internal-tcp-fin-receive"></a>내부 TCP FIN 수신 

#### <a name="internal-tcp-fin-receive"></a>내부 TCP FIN 수신

**아이콘** ![내부 TCP FIN 수신 아이콘](./media/user-guide/netx-events/image12.png)

**설명**

이 이벤트는 내부 NetX TCP FIN 수신 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 수신 시퀀스 번호입니다.

### <a name="internal-tcp-fin-send"></a>내부 TCP FIN 송신 

#### <a name="internal-tcp-fin-send"></a>내부 TCP FIN 송신

**아이콘** ![내부 TCP FIN 송신 아이콘](./media/user-guide/netx-events/image13.png)

**설명**

이 이벤트는 내부 NetX TCP FIN 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 전송 시퀀스 번호입니다.

### <a name="internal-tcp-rst-receive"></a>내부 TCP RST 수신 

#### <a name="internal-tcp-rst-receive"></a>내부 TCP RST 수신

**아이콘** ![내부 TCP RST 수신 아이콘](./media/user-guide/netx-events/image14.png)

**설명**

이 이벤트는 내부 NetX TCP 재설정 수신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 패킷에 대한 포인터입니다.
- 정보 필드 4: 수신 시퀀스 번호입니다.

### <a name="internal-tcp-rst-send"></a>내부 TCP RST 송신 

#### <a name="internal-tcp-rst-send"></a>내부 TCP RST 송신

**아이콘** ![내부 TCP RST 송신 아이콘](./media/user-guide/netx-events/image15.png)

**설명**

이 이벤트는 내부 NetX TCP 재설정 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 전송 시퀀스 번호입니다.

### <a name="internal-tcp-syn-receive"></a>내부 TCP SYN 수신 

#### <a name="internal-tcp-syn-receive"></a>내부 TCP SYN 수신

**아이콘** ![내부 TCP SYN 수신 아이콘](./media/user-guide/netx-events/image16.png)

**설명**

이 이벤트는 내부 NetX TCP SYN 수신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 수신 시퀀스 번호입니다.

### <a name="internal-tcp-syn-send"></a>내부 TCP SYN 송신 

#### <a name="internal-tcp-syn-send"></a>내부 TCP SYN 송신

**아이콘** ![내부 TCP SYN 송신 아이콘](./media/user-guide/netx-events/image17.png)

**설명**

이 이벤트는 내부 NetX TCP SYN 송신 이벤트를 나타냅니다.

정보 필드 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 패킷에 대한 포인터입니다. 정보 필드 4: 전송 시퀀스 번호입니다.

### <a name="internal-udp-receive"></a>내부 UDP 수신 

#### <a name="internal-udp-receive"></a>내부 UDP 수신

**아이콘** ![내부 UDP 수신 아이콘](./media/user-guide/netx-events/image18.png)

**설명**

이 이벤트는 내부 NetX UDP 수신 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: UDP 헤더의 단어 0입니다.

### <a name="internal-udp-send"></a>내부 UDP 송신 

#### <a name="internal-udp-send"></a>내부 UDP 송신

**아이콘** ![내부 UDP 송신 아이콘](./media/user-guide/netx-events/image19.png)

**설명**

이 이벤트는 내부 NetX UDP 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: UDP 헤더의 단어 0입니다.

### <a name="internal-rarp-receive"></a>내부 RARP 수신 

#### <a name="internal-rarp-receive"></a>내부 RARP 수신 

**아이콘** ![내부 RARP 수신 아이콘](./media/user-guide/netx-events/image20.png)

**설명**

이 이벤트는 내부 NetX RARP 수신 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 대상 IP 주소입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: RARP 헤더의 단어 1입니다.

### <a name="internal-rarp-send"></a>내부 RARP 송신 

#### <a name="internal-rarp-send"></a>내부 RARP 송신 

**아이콘** ![내부 RARP 송신 아이콘](./media/user-guide/netx-events/image21.png)

**설명**

이 이벤트는 내부 NetX RARP 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 대상 IP 주소입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: RARP 헤더의 단어 1입니다.

### <a name="internal-tcp-retry"></a>내부 TCP 다시 시도 

#### <a name="internal-tcp-retry"></a>내부 TCP 다시 시도 

**아이콘** ![내부 TCP 다시 시도 아이콘](./media/user-guide/netx-events/image22.png)

**설명**

이 이벤트는 내부 NetX TCP 다시 시도 이벤트를 나타냅니다.

**정보 필드**
- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 타이머에 대한 포인터입니다.
- 정보 필드 4: 다시 시도 횟수입니다.

### <a name="internal-tcp-state-change"></a>내부 TCP 상태 변경 

#### <a name="internal-tcp-state-change"></a>내부 TCP 상태 변경 

**아이콘** ![내부 TCP 상태 변경 아이콘](./media/user-guide/netx-events/image23.png)

**설명**

이 이벤트는 내부 NetX TCP 소켓 상태 변경 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 이전 상태입니다.
- 정보 필드 4: 새 상태입니다.

### <a name="internal-io-driver-packet-send"></a>내부 I/O 드라이버 패킷 송신 

#### <a name="internal-io-driver-packet-send"></a>내부 I/O 드라이버 패킷 송신

**아이콘** ![내부 I/O 드라이버 패킷 송신 아이콘](./media/user-guide/netx-events/image24.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 패킷 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 패킷에 대한 포인터입니다.
- 정보 필드 3: 패킷 크기입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-initialize"></a>내부 I/O 드라이버 초기화 

#### <a name="internal-io-driver-initialize"></a>내부 I/O 드라이버 초기화

**아이콘** ![내부 I/O 드라이버 초기화 아이콘](./media/user-guide/netx-events/image25.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 초기화 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-link-enable"></a>내부 I/O 드라이버 링크 사용 

#### <a name="internal-io-driver-link-enable"></a>내부 I/O 드라이버 링크 사용

**아이콘** ![내부 I/O 드라이버 링크 사용 아이콘](./media/user-guide/netx-events/image26.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 링크 사용 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-link-disable"></a>내부 I/O 드라이버 링크 사용 안 함 

#### <a name="internal-io-driver-link-disable"></a>내부 I/O 드라이버 링크 사용 안 함

**아이콘** ![내부 I/O 드라이버 링크 사용 안 함 아이콘](./media/user-guide/netx-events/image27.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 링크 사용 안 함 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-packet-broadcast"></a>내부 I/O 드라이버 패킷 브로드캐스트 

#### <a name="internal-io-driver-packet-broadcast"></a>내부 I/O 드라이버 패킷 브로드캐스트

**아이콘** ![내부 I/O 드라이버 패킷 브로드캐스트 아이콘](./media/user-guide/netx-events/image28.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 패킷 브로드캐스트 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 패킷에 대한 포인터입니다.
- 정보 필드 3: 패킷 크기입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-arp-send"></a>내부 I/O 드라이버 ARP 송신 

#### <a name="internal-io-driver-arp-send"></a>내부 I/O 드라이버 ARP 송신

**아이콘** ![내부 I/O 드라이버 ARP 송신 아이콘](./media/user-guide/netx-events/image29.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 ARP 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 패킷에 대한 포인터입니다.
- 정보 필드 3: 패킷 크기입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-arp-response-send"></a>내부 I/O 드라이버 ARP 응답 송신 

#### <a name="internal-io-driver-arp-response-send"></a>내부 I/O 드라이버 ARP 응답 송신

**아이콘** ![내부 I/O 드라이버 ARP 응답 송신 아이콘](./media/user-guide/netx-events/image30.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 ARP 응답 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 패킷에 대한 포인터입니다.
- 정보 필드 3: 패킷 크기입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-rarp-send"></a>내부 I/O 드라이버 RARP 송신 

#### <a name="internal-io-driver-rarp-send"></a>내부 I/O 드라이버 RARP 송신

**아이콘** ![내부 I/O 드라이버 RARP 송신 아이콘](./media/user-guide/netx-events/image31.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 RARP 송신 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 패킷에 대한 포인터입니다.
- 정보 필드 3: 패킷 크기입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-multicast-join"></a>내부 I/O 드라이버 멀티캐스트 조인 

#### <a name="internal-io-driver-multicast-join"></a>내부 I/O 드라이버 멀티캐스트 조인

**아이콘** ![내부 I/O 드라이버 멀티캐스트 조인 아이콘](./media/user-guide/netx-events/image32.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 멀티캐스트 조인 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-multicast-leave"></a>내부 I/O 드라이버 멀티캐스트 탈퇴 

#### <a name="internal-io-driver-multicast-leave"></a>내부 I/O 드라이버 멀티캐스트 탈퇴

**아이콘** ![내부 I/O 드라이버 멀티캐스트 탈퇴 아이콘](./media/user-guide/netx-events/image33.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 멀티캐스트 탈퇴 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-get-status"></a>내부 I/O 드라이버 상태 가져오기 

#### <a name="internal-io-driver-get-status"></a>내부 I/O 드라이버 상태 가져오기

**아이콘** ![내부 I/O 드라이버 상태 가져오기 아이콘](./media/user-guide/netx-events/image34.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 상태 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-get-speed"></a>내부 I/O 드라이버 속도 가져오기 

#### <a name="internal-io-driver-get-speed"></a>내부 I/O 드라이버 속도 가져오기

**아이콘** ![내부 I/O 드라이버 속도 가져오기 아이콘](./media/user-guide/netx-events/image35.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 속도 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-get-duplex-type"></a>내부 I/O 드라이버 이중 형식 가져오기 

#### <a name="internal-io-driver-get-duplex-type"></a>내부 I/O 드라이버 이중 형식 가져오기

**아이콘** ![내부 I/O 드라이버 이중 형식 가져오기 아이콘](./media/user-guide/netx-events/image36.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 이중 형식 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-get-error-count"></a>내부 I/O 드라이버 오류 수 가져오기

#### <a name="internal-io-driver-get-error-count"></a>내부 I/O 드라이버 오류 수 가져오기

**아이콘** ![내부 I/O 드라이버 오류 수 가져오기 아이콘](./media/user-guide/netx-events/image37.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 오류 수 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-get-rx-count"></a>내부 I/O 드라이버 RX 수 가져오기 

#### <a name="internal-io-driver-get-rx-count"></a>내부 I/O 드라이버 RX 수 가져오기

**아이콘** ![내부 I/O 드라이버 RX 수 가져오기 아이콘](./media/user-guide/netx-events/image38.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 RX 수 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-get-tx-count"></a>내부 I/O 드라이버 TX 수 가져오기 

#### <a name="internal-io-driver-get-tx-count"></a>내부 I/O 드라이버 TX 수 가져오기

**아이콘** ![내부 I/O 드라이버 TX 수 가져오기 아이콘](./media/user-guide/netx-events/image39.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 TX 수 가져오기 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-get-allocation-errors"></a>내부 I/O 드라이버 할당 오류 가져오기 

#### <a name="internal-io-driver-get-allocation-errors"></a>내부 I/O 드라이버 할당 오류 가져오기

**아이콘** ![내부 I/O 드라이버 할당 오류 가져오기 아이콘](./media/user-guide/netx-events/image40.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 할당 오류 가져오기 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-un-initialize"></a>내부 I/O 드라이버 초기화 취소 

#### <a name="internal-io-driver-un-initialize"></a>내부 I/O 드라이버 초기화 취소 

**아이콘** ![내부 I/O 드라이버 초기화 취소 아이콘](./media/user-guide/netx-events/image41.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 초기화 취소 이벤트를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="internal-io-driver-deferred-processing"></a>내부 I/O 드라이버 지연 처리 

#### <a name="internal-io-driver-deferred-processing"></a>내부 I/O 드라이버 지연 처리 

**아이콘** ![내부 I/O 드라이버 지연 처리 아이콘](./media/user-guide/netx-events/image42.png)

**설명**

이 이벤트는 내부 NetX I/O 드라이버 지연 처리 이벤트를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 패킷에 대한 포인터입니다.
- 정보 필드 3: 패킷 길이입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="arp-dynamic-entries-invalidate"></a>ARP 동적 항목 무효화 

#### <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

**아이콘** ![ARP 동적 항목 무효화 아이콘](./media/user-guide/netx-events/image43.png)

**설명**

이 이벤트는 nx_arp_dynamic_entries_invalidate를 통한 모든 동적 ARP의 무효화를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 무효화된 항목입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="arp-dynamic-entry-set"></a>ARP 동적 항목 설정 

#### <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

**아이콘** ![ARP 동적 항목 설정 아이콘](./media/user-guide/netx-events/image44.png)

**설명**

이 이벤트는 nx_arp_dynamic_entry_set을 통한 동적 ARP 항목 설정을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IP 주소입니다.
- 정보 필드 3: 실제 주소(MSW)입니다.
- 정보 필드 4: 실제 주소(LSW)입니다.

### <a name="arp-enable"></a>ARP 사용 

#### <a name="nx_arp_enable"></a>nx_arp_enable

**아이콘** ![ARP 사용 아이콘](./media/user-guide/netx-events/image45.png)

**설명**

이 이벤트는 nx_arp_enable은 통한 ARP 사용 설정을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: ARP 캐시 메모리 포인터입니다.
- 정보 필드 3: ARP 캐시 메모리 크기입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="arp-gratuitous-send"></a>ARP 무상 송신 

#### <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

**아이콘** ![ARP의 무상 송신 아이콘](./media/user-guide/netx-events/image46.png)

**설명**

이 이벤트는 nx_arp_gratuitous_send를 통한 무상 ARP 송신을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="arp-hardware-address-find"></a>ARP 하드웨어 주소 찾기 

#### <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

**아이콘** ![ARP 하드웨어 주소 찾기 아이콘](./media/user-guide/netx-events/image47.png)

**설명**

이 이벤트는 nx_arp_hardware_address_find를 통한 실제 주소를 찾기를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IP 주소입니다.
- 정보 필드 3: 실제 주소(MSW)입니다.
- 정보 필드 4: 실제 주소(LSW)입니다.

### <a name="arp-information-get"></a>ARP 정보 가져오기 

#### <a name="nx_arp_info_get"></a>nx_arp_info_get

**아이콘** ![ARP 정보 가져오기 아이콘](./media/user-guide/netx-events/image48.png)

**설명**

이 이벤트는 nx_arp_info_get을 통한 정보 가져오기를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 송신된 ARP입니다.
- 정보 필드 3: ARP 응답입니다.
- 정보 필드 4: 수신된 ARP입니다.

### <a name="arp-ip-address-find"></a>ARP IP 주소 찾기 

#### <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

**아이콘** ![ARP IP 주소 찾기 아이콘](./media/user-guide/netx-events/image49.png)

**설명**

이 이벤트는 nx_arp_ip_address_find를 통해 제공된 실제 주소와 연결된 IP 주소 찾기를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IP 주소입니다.
- 정보 필드 3: 실제 주소(MSW)입니다.
- 정보 필드 4: 실제 주소(LSW)입니다.

### <a name="arp-static-entry-create"></a>ARP 정적 항목 만들기 

#### <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

**아이콘** ![ARP 정적 항목 만들기 아이콘](./media/user-guide/netx-events/image50.png)

**설명**

이 이벤트는 nx_arp_static_entry_create를 통한 정적 ARP 항목 만들기를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IP 주소입니다.
- 정보 필드 3: 실제 주소(MSW)입니다.
- 정보 필드 4: 실제 주소(LSW)입니다.

### <a name="arp-static-entries-delete"></a>ARP 정적 항목 삭제 

#### <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

**아이콘** ![ARP 정적 항목 삭제 아이콘](./media/user-guide/netx-events/image51.png)

**설명**

이 이벤트는 nx_arp_static_entries_delete를 통한 모든 ARP 정적 항목 삭제를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 삭제된 항목입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="arp-static-entry-delete"></a>ARP 정적 항목 삭제 

### <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

**아이콘** ![ARP 정적 항목 삭제 아이콘](./media/user-guide/netx-events/image52.png)

**설명**

이 이벤트는 nx_arp_static_entry_delete을 통한 정적 ARP 항목 삭제를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IP 주소입니다.
- 정보 필드 3: 실제 주소(MSW)입니다.
- 정보 필드 4: 실제 주소(LSW)입니다.

### <a name="duo-cache-entry-delete"></a>Duo 캐시 항목 삭제 

#### <a name="nxd_und_cache_entry_delete"></a>nxd_und_cache_entry_delete

**아이콘** ![Duo 캐시 항목 삭제 아이콘](./media/user-guide/netx-events/image53.png)

**설명**

이 이벤트는 nx_udp_socket_create를 통한 인접 캐시 테이블의 항목 삭제를 나타냅니다.

**정보 필드** 

- 정보 필드 1: 삭제할 IPv6 링크 로컬 주소의 네 번째(가장 덜 중요함) 단어입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-cache-entry-set"></a>Duo 캐시 항목 설정 

#### <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set

**아이콘** ![Duo 캐시 항목 설정 아이콘](./media/user-guide/netx-events/image54.png)

**설명**

이 이벤트는 nxd_nd_cache_entry_set을 통해 캐시 항목을 만들고 인접 캐시 테이블에 추가하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 추가할 IPv6 주소의 네 번째(가장 덜 중요함) 단어입니다.
- 정보 필드 2: 실제 주소 msb입니다.
- 정보 필드 3: 실제 주소 lsb입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-cache-invalidate"></a>Duo 캐시 무효화 

#### <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate

**아이콘** ![Duo 캐시 무효화 아이콘](./media/user-guide/netx-events/image55.png)

**설명**

이 이벤트는 nxd_nd_cache_invalidate를 통해 전체 인접 캐시 테이블을 무효화함을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-cache-ip-address-find"></a>Duo 캐시 IP 주소 찾기 

#### <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find

**아이콘** ![Duo 캐시 IP 주소 찾기 아이콘](./media/user-guide/netx-events/image56.png)

**설명**

이 이벤트는 nxd_nd_cache_ip_address_find를 통해 캐시 테이블에서 제공된 실제 주소와 일치하는 IP 주소를 검색하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IPv6 주소의 네 번째(가장 덜 중요함) 단어입니다.
- 정보 필드 3: 실제 주소 msb입니다.
- 정보 필드 4: 실제 주소 lsb입니다.

### <a name="duo-icmp-enable"></a>Duo ICMP 사용 

#### <a name="nxd_icmp_enable"></a>nxd_icmp_enable

**아이콘** ![Duo ICMP 사용 아이콘](./media/user-guide/netx-events/image57.png)

**설명**

이 이벤트는 nxd_icmp_enable을 통해 지정된 IP 인스턴스에서 ICMPv4 및 ICMPv6 서비스를 사용하도록 설정하는 것을 나타냅니다.

**정보 필드**
- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-icmp-ping"></a>Duo ICMP Ping 

#### <a name="nxd_icmp_ping"></a>nxd_icmp_ping

**아이콘** ![Duo ICMP Ping 아이콘](./media/user-guide/netx-events/image58.png)

**설명**

이 이벤트는 nxd_icmp_ping을 통해 IPv6 호스트에 ping(에코 요청)을 보내는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IPv6 주소입니다.
- 정보 필드 3: 에코 데이터에 대한 포인터입니다.
- 정보 필드 4: 에코 데이터의 크기입니다.

### <a name="duo-ip-max-payload-size-find"></a>Duo IP 최대 페이로드 크기 찾기 

#### <a name="nxd_ip_max_payload_size"></a>nxd_ip_max_payload_size

**아이콘** ![Duo IP 최대 페이로드 크기 찾기 아이콘](./media/user-guide/netx-events/image59.png)

**설명**

이 이벤트는 지정된 패킷이 조각화를 요구하지 않고 수행할 수 있는 최대 페이로드를 계산합니다.

**정보 필드**

- 정보 필드 1: 소켓 포인터입니다.
- 정보 필드 2: 피어 IP 주소입니다.
- 정보 필드 3: 피어 포트입니다. 정보 필드 4: 사용되지 않습니다.

### <a name="duo-ip-raw-packet-send"></a>Duo IP 원시 패킷 송신 

#### <a name="nxd_ip_max_packet_send"></a>nxd_ip_max_packet_send

**아이콘** ![Duo IP 원시 패킷 송신 아이콘](./media/user-guide/netx-events/image60.png)

**설명**

이 이벤트는 nxd_ip_raw_packet_send를 통해 지정된 네트워크 인터페이스 외부의 원시 IP 패킷을 제공된 IP 대상으로 송신하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 송신할 패킷에 대한 포인터입니다.
- 정보 필드 3: 대상 주소에 대한 포인터입니다.
- 정보 필드 4: 패킷 프로토콜입니다.

### <a name="duo-ipv6-default-router-add"></a>Duo IPv6 기본 라우터 추가 

#### <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add

**아이콘** ![Duo IPv6 기본 라우터 추가 아이콘](./media/user-guide/netx-events/image61.png)

**설명**

이 이벤트는 nxd_ipv6_default_router_add를 통해 IP 인스턴스의 IPv6 라우팅 테이블에 기본 라우터를 추가하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 대상 네트워크 주소입니다.
- 정보 필드 3: 수명 시간 정보입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-ipv6-default-router-delete"></a>Duo IPv6 기본 라우터 삭제 

#### <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete

**아이콘** ![Duo IPv6 기본 라우터 삭제 아이콘](./media/user-guide/netx-events/image62.png)

**설명**

이 이벤트는 nxd_ipv6_default_router_delete를 통해 IP 인스턴스의 IPv6 라우팅 테이블에서 기본 라우터를 제거하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 기본 라우터 IPv6 주소의 네 번째 단어(가장 덜 중요함)입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-ipv6-enable"></a>Duo IPv6 사용 

#### <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable

**아이콘** ![Duo IPv6 사용 아이콘](./media/user-guide/netx-events/image63.png)

**설명**

이 이벤트는 nxd_ipv6_enable을 통해 제공된 IP 인스턴스에서 IPv6 서비스를 사용하도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-ipv6-global-address-get"></a>Duo IPv6 전체 주소 가져오기 

#### <a name="nxd_ipv6_global_address_get"></a>nxd_ipv6_global_address_get

**아이콘** ![Duo IPv6 전체 주소 가져오기 아이콘](./media/user-guide/netx-events/image64.png)

**설명**

이 이벤트는 nxd_ipv6_global_address_get을 통해 IP 인스턴스 인터페이스 테이블의 인덱스 1에 있는 IP 인스턴스에서 전체(기본) IP 주소를 검색하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 전체 주소의 네 번째 단어(가장 덜 중요함)입니다.
- 정보 필드 3: IPv6 주소 접두사 길이입니다.
- 정보 필드 4: IP 인터페이스 테이블에 대한 인덱스(1)입니다.

### <a name="duo-ipv6-global-address-set"></a>Duo IPv6 전체 주소 설정 

#### <a name="nxd_ipv6_global_address_set"></a>nxd_ipv6_global_address_set

**아이콘** ![Duo IPv6 전체 주소 설정 아이콘](./media/user-guide/netx-events/image65.png)

**설명**

이 이벤트는 nxd_ipv6_global_address_set을 통해 IP 인스턴스 인터페이스 테이블의 인덱스 1에 있는 IP 인스턴스에서 전체(기본) IP 주소를 설정하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 전체 주소의 네 번째 단어(가장 덜 중요함)입니다.
- 정보 필드 3: IPv6 주소 접두사 길이입니다.
- 정보 필드 4: IP 인터페이스 테이블에 대한 인덱스(1)입니다.

### <a name="duo-ipv6-initiate-dad-process"></a>Duo IPv6 DAD 프로세스 시작 

#### <a name="nxd_ipv6_initiate_dad_process"></a>nxd_ipv6_initiate_dad_process

**아이콘** ![Duo IPv6 DAD 프로세스 시작 아이콘](./media/user-guide/netx-events/image66.png)

**설명**

이 이벤트는 nxd_ipv6_initiate_dad_process를 통해 IP 인스턴스에 링크 로컬 또는 IP 인터페이스 주소가 할당될 때 DAD(중복 주소 검색) 프로세스의 시작을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-ipv6-interface-address-get"></a>Duo IPv6 인터페이스 주소 가져오기 

#### <a name="nxd_ipv6_interface_address_get"></a>nxd_ipv6_interface_address_get

**아이콘** ![Duo IPv6 인터페이스 주소 가져오기 아이콘](./media/user-guide/netx-events/image67.png)

**설명**

이 이벤트는 지정된 인덱스의 IP 주소 및 접두사를 nxd_ipv6_interface_address_get을 통해 IP 인스턴스 인터페이스 주소 테이블로 검색하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 반환할 IPv6 주소의 네 번째 단어(가장 덜 중요함)입니다.
- 정보 필드 4: IP 인스턴스 인터페이스 테이블로의 인터페이스 인덱스입니다.

### <a name="duo-ipv6-interface-address-set"></a>Duo IPv6 인터페이스 주소 설정 

### <a name="nxd_ipv6_interface_address_set"></a>nxd_ipv6_interface_address_set

**아이콘** ![Duo IPv6 인터페이스 주소 설정 아이콘](./media/user-guide/netx-events/image68.png)

**설명**

이 이벤트는 지정된 인덱스의 IP 주소 및 접두사를 IP 인스턴스 인터페이스 주소 테이블로 설정하는 것을 나타냅니다. nxd_ipv6_interface_address_set을 통해 인덱스 0(링크 로컬 주소)에서 허용되지 않습니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 반환할 IPv6 주소의 네 번째 단어(가장 덜 중요함)입니다.
- 정보 필드 3: 접두사 길이입니다.
- 정보 필드 4: IP 인스턴스 인터페이스 테이블로의 인터페이스 인덱스입니다.

### <a name="duo-ipv6-link-local-address-get"></a>Duo IPv6 링크 로컬 주소 가져오기 

#### <a name="nxd_ipv6_linklocal_address_get"></a>nxd_ipv6_linklocal_address_get

**아이콘** ![Duo IPv6 링크 로컬 주소 가져오기 아이콘](./media/user-guide/netx-events/image69.png)

**설명**

이 이벤트는 nxd_ipv6_linklocal_address_get을 통해 지정된 IP 인스턴스의 링크 로컬 주소를 검색하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IPv6 링크 로컬 주소의 네 번째 단어(가장 덜 중요함)입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-ipv6-link-local-address-set"></a>Duo IPv6 링크 로컬 주소 설정 

#### <a name="nxd_ipv6_linklocal_address_set"></a>nxd_ipv6_linklocal_address_set

**아이콘** ![Duo IPv6 링크 로컬 주소 설정 아이콘](./media/user-guide/netx-events/image70.png)

**설명**

이 이벤트는 nxd_ipv6_linklocal_address_set을 통해 IP 인스턴스의 링크 로컬 주소를 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IPv6 링크 로컬 주소의 네 번째(가장 덜 중요함) 단어입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-ipv6-raw-packet-send"></a>Duo IPv6 원시 패킷 송신 

#### <a name="nxd_ipv6_raw_packet_send"></a>nxd_ipv6_raw_packet_send

**아이콘** ![Duo IPv6 원시 패킷 송신 아이콘](./media/user-guide/netx-events/image71.png)

**설명**

이 이벤트는 nxd_ip_raw_packet_send를 통해 원시 IP 패킷을 기본 IP 인터페이스를 통해 지정 대상으로 송신하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 송신할 패킷에 대한 포인터입니다.
- 정보 필드 3: 대상 IP 주소입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-tcp-socket-peer-info-get"></a>Duo TCP 소켓 피어 정보 가져오기 

#### <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get

**아이콘** ![Duo TCP 소켓 피어 정보 가져오기 아이콘](./media/user-guide/netx-events/image72.png)

**설명**

이 이벤트는 지정된 소켓의 수신된 TCP 패킷에서 발신자 데이터를 추출합니다. 발신자의 IP 주소와 포트를 반환합니다.

**정보 필드**

- 정보 필드 1: 소켓 포인터입니다.
- 정보 필드 2: 피어 IP 주소입니다.
- 정보 필드 3: 피어 포트입니다.
- 정보 필드 4: IP 주소의 가장 덜 중요한 32비트입니다.

### <a name="duo-tcp-socket-set-interface"></a>Duo TCP 소켓 설정 인터페이스 

#### <a name="nxd_tcp_socket_set_interface"></a>nxd_tcp_socket_set_interface

**아이콘** ![Duo TCP 소켓 설정 인터페이스 아이콘](./media/user-guide/netx-events/image73.png)

**설명**

이 이벤트는 클라이언트가 nxd_tcp_client_socket_connect를 통해 지정된 서버 IP 주소에 있는 TCP 서버와 연결된 후 나가는 소켓 인터페이스를 설정하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: TCP 소켓에 대한 포인터입니다.
- 정보 필드 2: 인터페이스 ID입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-udp-socket-send"></a>Duo UDP 소켓 송신 

#### <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send

**아이콘** ![Duo UDP 소켓 송신 아이콘](./media/user-guide/netx-events/image74.png)

**설명**

이 이벤트는 nxd_udp_socket_send를 통해 입력 IP 주소와 포트를 사용하여 지정된 소켓을 통해 UDP 패킷을 송신하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 포인터 UDP 소켓입니다.
- 정보 필드 2: UDP 패킷에 대한 포인터입니다.
- 정보 필드 3: 패킷 길이입니다.
- 정보 필드 4: 사용되지 않습니다.


### <a name="duo-udp-socket-set-interface"></a>Duo UDP 소켓 설정 인터페이스 

#### <a name="nxd_udp_socket_set_interface"></a>nxd_udp_socket_set_interface

**아이콘** ![Duo UDP 소켓 설정 인터페이스 아이콘](./media/user-guide/netx-events/image75.png)

**설명**

이 이벤트는 지정된 UDP 소켓 송신 인터페이스를 nxd_udp_socket_set_interface를 통해 입력 인터페이스 ID에 해당하는 인터페이스로 설정하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: UDP 소켓에 대한 포인터입니다.
- 정보 필드 2: 인터페이스 ID입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="duo-udp-source-extract"></a>Duo UDP 원본 추출 

#### <a name="nxd_udp_socket_extract"></a>nxd_udp_socket_extract

**아이콘** ![Duo UDP 원본 추출 아이콘](./media/user-guide/netx-events/image76.png)

**설명**

이 이벤트는 수신한 패킷의 IP 주소와 원본 포트(IPv4 또는 IPv6)를 추출하는 것을 나타냅니다. IPv6의 경우 IP 주소의 네 번째 단어(가장 덜 중요함)는 nxd_udp_source_extract를 통해 반환됩니다.

**정보 필드**

- 정보 필드 1: 패킷에 대한 포인터입니다.
- 정보 필드 2: IP 버전입니다.
- 정보 필드 3: 원본 IP 주소(IPv4 또는 IPv6)입니다.
- 정보 필드 4: 원본 포트입니다.

### <a name="icmp-enable"></a>ICMP 사용 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**아이콘** ![ICMP 사용 아이콘](./media/user-guide/netx-events/image77.png)

**설명**

이 이벤트는 nx_icmp_enable을 통해 ICMP를 사용하도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="icmp-information-get"></a>ICMP 정보 가져오기 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**아이콘** ![ICMP 정보 가져오기 아이콘](./media/user-guide/netx-events/image78.png)

**설명**

이 이벤트는 nx_icmp_info_get을 통한 정보 가져오기를 나타냅니다.

**정보 필드**
- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 송신된 Ping입니다.
- 정보 필드 3: Ping 응답입니다.
- 정보 필드 4: 수신된 Ping입니다.

### <a name="icmp-ping"></a>ICMP Ping 

#### <a name="nx_icmp_ping"></a>nx_icmp_ping

**아이콘** ![ICMP Ping 아이콘](./media/user-guide/netx-events/image79.png)

**설명**

이 이벤트는 nx_icmp_ping을 통해 대상 IP 주소를 ping하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IP 주소입니다.
- 정보 필드 3: 데이터에 대한 포인터입니다.
- 정보 필드 4: 데이터의 크기입니다.

### <a name="igmp-enable"></a>IGMP 사용 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**아이콘** ![IGMP 사용 아이콘](./media/user-guide/netx-events/image80.png)

**설명**

이 이벤트는 nx_igmp_enable을 통해 IGMP를 사용하도록 설정하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="igmp-information-get"></a>IGMP 정보 가져오기 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**아이콘** ![IGMP 정보 가져오기 아이콘](./media/user-guide/netx-events/image81.png)

**설명**

이 이벤트는 nx_igmp_info_get을 통한 정보 가져오기를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 송신된 보고서입니다.
- 정보 필드 3: 수신된 쿼리입니다.
- 정보 필드 4: 조인된 그룹입니다.

### <a name="igmp-loopback-disable"></a>IGMP 루프백 사용 안 함 

#### <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

**아이콘** ![IGMP 루프백 사용 안 함 아이콘](./media/user-guide/netx-events/image82.png)

**설명**

이 이벤트는 nx_igmp_loopback_disable를 통해 IGMP 루프백을 사용하지 않도록 설정함을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="igmp-loopback-enable"></a>IGMP 루프백 사용 

#### <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

**아이콘** ![IGMP 루프백 사용 아이콘](./media/user-guide/netx-events/image83.png)

**설명**

이 이벤트는 nx_igmp_loopback_enable를 통해 IGMP 루프백을 사용하도록 설정함을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="igmp-multicast-join"></a>IGMP 멀티캐스트 조인 

#### <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

**아이콘** ![IGMP 멀티캐스트 조인 아이콘](./media/user-guide/netx-events/image84.png)

**설명**

이 이벤트는 nx_igmp_multicast_join을 통해 멀티캐스트 그룹을 조인하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 그룹 IP 주소입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="igmp-multicast-leave"></a>IGMP 멀티캐스트 탈퇴 

#### <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

**아이콘** ![IGMP 멀티캐스트 탈퇴 아이콘](./media/user-guide/netx-events/image85.png)

**설명**

이 이벤트는 nx_igmp_multicast_leave를 통해 멀티캐스트 그룹을 탈퇴하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 그룹 IP 주소입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-address-change-notify"></a>IP 주소 변경 알림 

#### <a name="nx_ip_address_change_notify"></a>nx_ip_address_change_notify

**아이콘** ![IP 주소 변경 알림 아이콘](./media/user-guide/netx-events/image86.png)

**설명**

이 이벤트는 nx_ip_address_change_notify를 통해 IP 변경 알림에 등록하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 콜백 함수 포인터입니다.
- 정보 필드 3: 추가 정보 포인터입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-address-get"></a>IP 주소 가져오기 

#### <a name="nx_ip_address_get"></a>nx_ip_address_get

**아이콘** ![IP 주소 가져오기 아이콘](./media/user-guide/netx-events/image87.png)

**설명**

이 이벤트는 nx_ip_address_get을 통해 IP 주소를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IP 주소입니다.
- 정보 필드 3: 네트워크 마스크입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-address-set"></a>IP 주소 설정 

#### <a name="nx_ip_address_set"></a>nx_ip_address_set

**아이콘** ![IP 주소 설정 아이콘](./media/user-guide/netx-events/image88.png)

**설명**

이 이벤트는 nx_ip_address_set을 통해 IP 주소를 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IP 주소입니다.
- 정보 필드 3: 네트워크 마스크입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-create"></a>IP 만들기 

#### <a name="nx_ip_create"></a>nx_ip_create

**아이콘** ![IP 만들기 아이콘](./media/user-guide/netx-events/image89.png)

**설명**

이 이벤트는 nx_ip_create를 통해 IP 인스턴스를 만드는 것을 나타냅니다.

**정보 필드** 
- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: IP 주소입니다.
- 정보 필드 3: 네트워크 마스크입니다.
- 정보 필드 4: 기본 패킷 풀 포인터입니다.

### <a name="ip-delete"></a>IP 삭제 

#### <a name="nx_ip_delete"></a>nx_ip_delete

**아이콘** ![IP 삭제 아이콘](./media/user-guide/netx-events/image90.png)

**설명**

이 이벤트는 nx_ip_delete를 통해 IP 인스턴스를 삭제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-driver-direct-command"></a>IP 드라이버 직접 명령 

#### <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

**아이콘** ![IP 드라이버 직접 명령 아이콘](./media/user-guide/netx-events/image91.png)

**설명**

이 이벤트는 nx_ip_driver_direct_command를 통한 직접 I/O 드라이버 명령을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 드라이버 명령입니다.
- 정보 필드 3: 반환 값입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-forwarding-disable"></a>IP 전달 사용 안 함 

#### <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

**아이콘** ![IP 전달 사용 안 함 아이콘](./media/user-guide/netx-events/image92.png)

**설명**

이 이벤트는 nx_ip_forwarding_disable을 통해 IP 전달을 사용하지 않도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-forwarding-enable"></a>IP 전달 사용 

#### <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

**아이콘** ![IP 전달 사용 아이콘](./media/user-guide/netx-events/image93.png)

**설명**

이 이벤트는 nx_ip_forwarding_enable을 통해 IP 전달을 사용하도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-fragment-disable"></a>IP 조각 사용 안 함 

#### <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

**아이콘** ![IP 조각 사용 안 함 아이콘](./media/user-guide/netx-events/image94.png)

**설명**

이 이벤트는 nx_ip_fragment_disable을 통해 IP 조각화를 사용하지 않도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-fragment-enable"></a>IP 조각 사용 

#### <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

**아이콘** ![IP 조각 사용 아이콘](./media/user-guide/netx-events/image95.png)

**설명**

이 이벤트는 nx_ip_fragment_enable을 통해 IP 조각화를 사용하도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-gateway-address-set"></a>IP 게이트웨이 주소 설정 

#### <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

**아이콘** ![IP 게이트웨이 주소 설정 아이콘](./media/user-guide/netx-events/image96.png)

**설명**

이 이벤트는 nx_ip_gateway_address_set을 통해 게이트웨이 IP 주소를 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 게이트웨이 IP 주소입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-information-get"></a>IP 정보 가져오기 

#### <a name="nx_ip_info_get"></a>nx_ip_info_get

**아이콘** ![IP 정보 가져오기 아이콘](./media/user-guide/netx-events/image97.png)

**설명** 이 이벤트는 nx_ip_info_get을 통해 IP 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 송신한 IP 바이트 수입니다.
- 정보 필드 3: 수신한 IP 바이트 수입니다.
- 정보 필드 4: 삭제된 IP 패킷 수입니다.

### <a name="ip-interface-attach"></a>IP 인터페이스 연결 

#### <a name="nx_interface_attach"></a>nx_interface_attach

**아이콘** ![IP 인터페이스 연결 아이콘](./media/user-guide/netx-events/image98.png)

**설명**

이 이벤트는 nx_ip_interface_attach를 통해 IP 인스턴스에 연결되는 보조 네트워크 인터페이스를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 인터페이스 IP 주소입니다.
- 정보 필드 3: IP 인터페이스 테이블에 대한 인덱스입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-interface-info-get"></a>IP 인터페이스 정보 가져오기 

#### <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

**아이콘** ![IP 인터페이스 정보 가져오기 아이콘](./media/user-guide/netx-events/image99.png)

**설명**

이 이벤트는 nx_ip_interface_info_get을 통해 지정된 네트워크 인터페이스에서 검색된 정보를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 인터페이스 IP 주소입니다.
- 정보 필드 3: 인터페이스 MAC 주소 msb입니다.
- 정보 필드 4: 인터페이스 MAC 주소 lsb입니다.

### <a name="ip-raw-packet-disable"></a>IP 원시 패킷 사용 안 함 

#### <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

**아이콘** ![IP 원시 패킷 사용 안 함 아이콘](./media/user-guide/netx-events/image100.png)

**설명**

이 이벤트는 nx_ip_raw_packet_disable을 통해 원시 IP 패킷 통신을 사용하지 않도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-raw-packet-enable"></a>IP 원시 패킷 사용 

#### <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

**아이콘** ![IP 원시 패킷 사용 아이콘](./media/user-guide/netx-events/image101.png)

**설명**

이 이벤트는 nx_ip_raw_packet_enable을 통해 원시 IP 패킷 통신을 사용하도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-raw-packet-receive"></a>IP 원시 패킷 수신 

#### <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

**아이콘** ![IP 원시 패킷 수신 아이콘](./media/user-guide/netx-events/image102.png)

**설명**

이 이벤트는 nx_ip_raw_packet_receive를 통해 원시 IP 패킷을 수신하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 패킷에 대한 포인터입니다.
- 정보 필드 3: 대기 옵션입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-raw-packet-send"></a>IP 원시 패킷 송신 

#### <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

**아이콘** ![IP 원시 패킷 송신 아이콘](./media/user-guide/netx-events/image103.png)

**설명**

이 이벤트는 nx_ip_raw_packet_send를 통해 원시 IP 패킷을 보내는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 패킷에 대한 포인터입니다.
- 정보 필드 3: 대상 IP 주소입니다.
- 정보 필드 4: 서비스 유형입니다.

### <a name="ip-static-route-add"></a>IP 고정 경로 추가 

#### <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

**아이콘** ![IP 고정 경로 추가 아이콘](./media/user-guide/netx-events/image104.png)

**설명**

이 이벤트는 nx_ip_static_route_add를 통해 IP 인스턴스 라우팅 테이블에 추가되는 고정 경로를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 네트워크 주소입니다.
- 정보 필드 3: 네트워크 마스크입니다.
- 정보 필드 4: 다음 홉입니다.

### <a name="ip-static-route-delete"></a>IP 고정 경로 삭제 

#### <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

**아이콘** ![IP 고정 경로 삭제 아이콘](./media/user-guide/netx-events/image105.png)

**설명**

이 이벤트는 nx_ip_static_route_delete를 통해 IP 인스턴스 라우팅 테이블에서 제거되는 고정 경로를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 네트워크 주소입니다.
- 정보 필드 3: 네트워크 마스크입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="ip-status-check"></a>IP 상태 확인 

#### <a name="nx_ip_status_check"></a>nx_ip_status_check

**아이콘** ![IP 상태 확인 아이콘](./media/user-guide/netx-events/image106.png)

**설명**

이 이벤트는 nx_ip_status_check를 통해 IP 상태를 확인하는 것을 나타냅니다.

정보 필드 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 요청된 상태입니다.
- 정보 필드 3: 실제 상태입니다.
- 정보 필드 4: 대기 옵션입니다.

### <a name="ipsec-enable"></a>IPSEC 사용 

#### <a name="nx_ipsec_enable"></a>nx_ipsec_enable

**아이콘** ![IPSEC 사용 아이콘](./media/user-guide/netx-events/image107.png)

**설명**

이 이벤트는 nx_ipsec_enable을 통해 제공된 IP 인스턴스에서 IPSec 서비스를 사용하도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="packet-allocate"></a>패킷 할당 

#### <a name="nx_packet_allocate"></a>nx_packet_allocate

**아이콘** ![패킷 할당 아이콘](./media/user-guide/netx-events/image108.png)

**설명**

이 이벤트는 nx_packet_allocate를 통한 패킷 할당을 나타냅니다.

**정보 필드**

- 정보 필드 1: 패킷 풀에 대한 포인터입니다.
- 정보 필드 2: 할당된 패킷에 대한 포인터입니다.
- 정보 필드 3: 패킷 유형입니다.
- 정보 필드 4: 사용 가능한 패킷입니다.

### <a name="packet-copy"></a>패킷 복사 

#### <a name="nx_packet_copy"></a>nx_packet_copy

**아이콘** ![패킷 복사 아이콘](./media/user-guide/netx-events/image109.png)

**설명**

이 이벤트는 nx_packet_copy를 통한 패킷 복사를 나타냅니다.

**정보 필드**

- 정보 필드 2: 새 패킷 포인터입니다.
- 정보 필드 3: 패킷 풀에 대한 포인터입니다.
- 정보 필드 4: 대기 옵션입니다.

### <a name="packet-data-append"></a>패킷 데이터 추가 

#### <a name="nx_packet_data_append"></a>nx_packet_data_append

**아이콘** ![ 패킷 데이터 추가 아이콘](./media/user-guide/netx-events/image110.png)

**설명**

이 이벤트는 nx_packet_data_append를 통해 패킷에 데이터를 추가하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 패킷에 대한 포인터입니다.
- 정보 필드 2: 데이터에 대한 포인터입니다.
- 정보 필드 3: 데이터의 크기입니다.
- 정보 필드 4: 패킷 풀에 대한 포인터입니다.

### <a name="packet-data-extract-offset"></a>패킷 데이터 추출 오프셋 

#### <a name="nx_udp_source_extract_offset"></a>nx_udp_source_extract_offset

**아이콘** ![패킷 데이터 추출 오프셋 아이콘](./media/user-guide/netx-events/image111.png)

**설명**

이 이벤트는 nx_udp_source_extract_offset을 통해 패킷에서 제공된 버퍼로 추출되는 패킷 데이터를 나타냅니다.

**정보 필드**

- 정보 필드 1: 패킷에 대한 포인터입니다.
- 정보 필드 2: 지정된 버퍼 크기입니다.
- 정보 필드 3: 복사된 바이트 수입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="packet-data-retrieve"></a>패킷 데이터 검색 

#### <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

**아이콘** ![패킷 데이터 검색 아이콘](./media/user-guide/netx-events/image112.png)

**설명**

이 이벤트는 nx_packet_data_retrieve를 통해 패킷에서 데이터를 검색하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 패킷에 대한 포인터입니다.
- 정보 필드 2: 버퍼의 시작 부분에 대한 포인터입니다.
- 정보 필드 3: 복사한 바이트 수입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="packet-length-get"></a>패킷 길이 가져오기 

#### <a name="nx_packet_length_get"></a>nx_packet_length_get

**아이콘** ![패킷 길이 가져오기 아이콘](./media/user-guide/netx-events/image113.png)

**설명**

이 이벤트는 nx_packet_length_get을 통해 패킷 길이를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 패킷에 대한 포인터입니다.
- 정보 필드 2: 패킷 길이입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="packet-pool-create"></a>패킷 풀 만들기 

#### <a name="nx_packet_pool_create"></a>nx_packet_pool_create

**아이콘** ![패킷 풀 만들기 아이콘](./media/user-guide/netx-events/image114.png)

**설명**

이 이벤트는 nx_packet_pool_create을 통해 패킷 풀을 만드는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 패킷 풀에 대한 포인터입니다.
- 정보 필드 2: 패킷 페이로드 크기입니다.
- 정보 필드 3: 풀 메모리 영역에 대한 포인터입니다.
- 정보 필드 4: 풀 메모리 영역의 크기입니다.

### <a name="packet-pool-delete"></a>패킷 풀 삭제 

#### <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

**아이콘** ![패킷 풀 삭제 아이콘](./media/user-guide/netx-events/image115.png)

**설명**

이 이벤트는 nx_packet_pool_delete를 통해 패킷 풀을 삭제하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: 패킷 풀에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

#### <a name="packet-pool-information-get"></a>패킷 풀 정보 가져오기 

#### <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

**아이콘** ![패킷 풀 정보 가져오기 아이콘](./media/user-guide/netx-events/image116.png)

**설명**

이 이벤트는 nx_packet_pool_info_get을 통해 패킷 풀 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 패킷 풀에 대한 포인터입니다.
- 정보 필드 2: 총 패킷 수입니다.
- 정보 필드 3: 사용 가능한 패킷입니다.
- 정보 필드 4: 빈 요청입니다.

### <a name="packet-release"></a>패킷 해제 

#### <a name="nx_packet_data_release"></a>nx_packet_data_release

**아이콘** ![패킷 해제 아이콘](./media/user-guide/netx-events/image117.png)

**설명**

이 이벤트는 nx_packet_release를 통해 패킷을 해제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 패킷에 대한 포인터입니다.
- 정보 필드 2: 패킷 상태입니다.
- 정보 필드 3: 사용 가능한 패킷입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="packet-transmit-release"></a>패킷 전송 해제 

#### <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

**아이콘** ![패킷 전송 해제 아이콘](./media/user-guide/netx-events/image118.png)

**설명**

이 이벤트는 nx_packet_transmit_release를 통해 전송 패킷을 해제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 패킷에 대한 포인터입니다.
- 정보 필드 2: 패킷 상태입니다.
- 정보 필드 3: 사용 가능한 패킷입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="rarp-disable"></a>RARP 사용 안 함 

#### <a name="nx_rarp_disable"></a>nx_rarp_disable

**아이콘** ![RARP 사용 안 함 아이콘](./media/user-guide/netx-events/image119.png)

**설명**

이 이벤트는 nx_rarp_disable를 통해 RARP를 사용하지 않도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="rarp-enable"></a>RARP 사용 

#### <a name="nx_rarp_enable"></a>nx_rarp_enable

**아이콘** ![RARP 사용 아이콘](./media/user-guide/netx-events/image120.png)

**설명**

이 이벤트는 nx_rarp_enable을 통해 RARP를 사용하도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="rarp-information-get"></a>RARP 정보 가져오기 

#### <a name="nx_rarp_info_get"></a>nx_rarp_info_get

**아이콘** ![RARP 정보 가져오기 아이콘](./media/user-guide/netx-events/image121.png)

**설명**

이 이벤트는 nx_rarp_info_get을 통한 RARP 정보 가져오기를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 송신한 요청입니다.
- 정보 필드 3: 수신한 응답입니다.
- 정보 필드 4: 잘못된 응답입니다.

### <a name="system-initialize"></a>시스템 초기화 

#### <a name="nx_system_initialize"></a>nx_system_initialize

**아이콘** ![시스템 초기화 아이콘](./media/user-guide/netx-events/image122.png)

**설명**

이 이벤트는 nx_system_initialize를 통한 NetX 초기화를 나타냅니다.

**정보 필드**

- 정보 필드 1 사용되지 않습니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="tcp-client-socket-bind"></a>TCP 클라이언트 소켓 바인딩 

#### <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

**아이콘** ![TCP 클라이언트 소켓 바인딩 아이콘](./media/user-guide/netx-events/image123.png)

**설명**

이 이벤트는 nx_tcp_client_socket_bind를 통해 포트에 클라이언트 소켓을 바인딩하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 요청된 포트입니다.
- 정보 필드 4: 대기 옵션입니다.

### <a name="tcp-client-socket-connect"></a>TCP 클라이언트 소켓 연결 

#### <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

**아이콘** ![TCP 클라이언트 소켓 연결 아이콘](./media/user-guide/netx-events/image124.png)

**설명**

이 이벤트는 nx_tcp_client_socket_connect를 통해 클라이언트 소켓 연결을 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 서버 IP 주소입니다.
- 정보 필드 4: 요청된 서버 포트입니다.

### <a name="tcp-client-socket-port-get"></a>TCP 클라이언트 소켓 포트 가져오기 

#### <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

**아이콘** ![TCP 클라이언트 소켓 포트 가져오기 아이콘](./media/user-guide/netx-events/image125.png)

**설명**

이 이벤트는 nx_tcp_client_socket_port_get을 통해 클라이언트 소켓 포트 번호를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 포트 번호입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="tcp-client-socket-unbind"></a>TCP 클라이언트 소켓 바인딩 해제 

#### <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

**아이콘** ![TCP 클라이언트 소켓 바인딩 해제 아이콘](./media/user-guide/netx-events/image126.png)

**설명**

이 이벤트는 nx_tcp_client_socket_unbind를 통해 소켓에 연결된 포트를 바인딩 해제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="tcp-enable"></a>TCP 사용 

#### <a name="nx_tcp_enable"></a>nx_tcp_enable

**아이콘** ![TCP 사용 아이콘](./media/user-guide/netx-events/image127.png)

**설명**

이 이벤트는 nx_tcp_enable을 통해 TCP를 사용하도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

###  <a name="tcp-free-port-find-tcp-free-port-find"></a>TCP 사용 가능한 포트 찾기 TCP 사용 가능한 포트 찾기 

#### <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

**아이콘** ![TCP 사용 가능한 포트 찾기 아이콘](./media/user-guide/netx-events/image128.png)

**설명**

이 이벤트는 nx_tcp_free_port_find를 통해 사용 가능한 TCP 포트를 찾는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 시작 검색 포트 번호입니다.
- 정보 필드 3: 사용 가능한 포트 번호입니다.
- 정보 필드 4: 사용되지 않습니다.

###  <a name="tcp-infomation-get"></a>TCP 정보 가져오기 

#### <a name="nx_tcp_info_get"></a>nx_tcp_info_get

**아이콘** ![TCP 정보 가져오기 아이콘](./media/user-guide/netx-events/image129.png)

**설명**

이 이벤트는 nx_tcp_info_get을 통해 지정된 IP 인스턴스에 대한 TCP 정보를 검색하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 송신한 바이트 수입니다.
- 정보 필드 3: 수신한 바이트 수입니다.
- 정보 필드 4: 잘못된 패킷 수입니다.

###  <a name="tcp-server-socket-accept"></a>TCP 서버 소켓 수락 

#### <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

**아이콘** ![TCP 서버 소켓 수락 아이콘](./media/user-guide/netx-events/image130.png)

**설명**

이 이벤트는 nx_tcp_server_socket_accept를 통해 활성 연결 요청이 수신된 후 서버 소켓을 설정하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 대기 옵션입니다.
- 정보 필드 4: 소켓 상태입니다.

###  <a name="tcp-server-socket-listen"></a>TCP 서버 소켓 수신 대기 

#### <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

**아이콘** ![TCP 서버 소켓 수신 대기 아이콘](./media/user-guide/netx-events/image131.png)

**설명**

이 이벤트는 nx_tcp_server_socket_listen을 통해 지정된 TCP 포트에 대한 수신 대기 요청 및 서버 소켓을 등록하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: TCP 포트 번호입니다.
- 정보 필드 3: 소켓에 대한 포인터입니다.
- 정보 필드 4: 큐에 대기할 수 있는 최대 연결 수입니다.

###  <a name="tcp-server-socket-relisten"></a>TCP 서버 소켓 다시 수신 대기 

#### <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

**아이콘** ![TCP 서버 소켓 다시 수신 대기 아이콘](./media/user-guide/netx-events/image132.png)

**설명**

이 이벤트는 nx_tcp_server_socket_relisten을 통해 지정된 TCP 포트에 대한 기존 수신 대기 요청에 다른 서버 소켓을 등록함을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: TCP 포트 번호입니다.
- 정보 필드 3: 소켓에 대한 포인터입니다.
- 정보 필드 4: 소켓 상태입니다.

###  <a name="tcp-server-socket-unaccept"></a>TCP 서버 소켓 허용 안 함 

#### <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

**아이콘** ![TCP 서버 소켓 허용 안 함 아이콘](./media/user-guide/netx-events/image133.png)

**설명**

이 이벤트는 nx_tcp_server_socket_unaccept를 통해 이전 수동 연결을 수신하는 포트와의 연결에서 서버 소켓을 제거하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 소켓 상태입니다.
- 정보 필드 4: 사용되지 않습니다.

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a>TCP 서버 소켓 수신 대기 취소 TCP 서버 소켓 수신 대기 취소 

#### <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

**아이콘** ![TCP 서버 소켓 수신 대기 취소 아이콘](./media/user-guide/netx-events/image134.png)

**설명**

이 이벤트는 nx_tcp_server_socket_unlisten을 통해 지정된 TCP 포트에 대한 이전 수신 대기 요청을 제거하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: TCP 포트 번호입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="tcp-socket-bytes-available"></a>TCP 소켓 사용 가능 바이트 

#### <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

**아이콘** ![TCP 소켓 사용 가능 바이트 아이콘](./media/user-guide/netx-events/image135.png)

**설명**

이 이벤트는 nx_tcp_socket_bytes_available을 통해 지정된 TCP 수신 소켓에서 현재 사용할 수 있는 바이트 수를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: TCP 소켓에 대한 포인터입니다.
- 정보 필드 3: 소켓에서 수신된 바이트 수입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="tcp-socket-create"></a>TCP 소켓 만들기 

#### <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

**아이콘** ![TCP 소켓 만들기 아이콘](./media/user-guide/netx-events/image136.png)

**설명**

이 이벤트는 nx_tcp_socket_create를 통해 TCP 소켓을 만드는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 서비스 유형입니다.
- 정보 필드 4: 수신 창 크기입니다.

### <a name="tcp-socket-delete"></a>TCP 소켓 삭제 

#### <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

**아이콘** ![TCP 소켓 삭제 아이콘](./media/user-guide/netx-events/image137.png)

**설명**

이 이벤트는 nx_tcp_socket_delete를 통해 소켓을 삭제하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 소켓 상태입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="tcp-socket-disconnect"></a>TCP 소켓 연결 끊기 

#### <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

**아이콘** ![TCP 소켓 연결 끊기 아이콘](./media/user-guide/netx-events/image138.png)

**설명**

이 이벤트는 nx_tcp_socket_disconnect를 통해 소켓의 연결을 끊는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 대기 옵션입니다.
- 정보 필드 4: 소켓 상태입니다.

### <a name="tcp-socket-information-get"></a>TCP 소켓 정보 가져오기 

#### <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

**아이콘** ![TCP 소켓 정보 가져오기 아이콘](./media/user-guide/netx-events/image139.png)

**설명**

이 이벤트는 nx_tcp_socket_info_get을 통해 소켓에 대한 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 이 소켓을 통해 송신된 바이트 수입니다.
- 정보 필드 4: 이 소켓을 통해 수신된 바이트 수입니다.

### <a name="tcp-socket-mss-get"></a>TCP 소켓 MSS 가져오기 

#### <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

**아이콘** ![TCP 소켓 MSS 가져오기 아이콘](./media/user-guide/netx-events/image140.png)

**설명**

이 이벤트는 nx_tcp_socket_mss_get을 통해 소켓의 MSS를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: MSS(최대 세그먼트 크기)입니다.
- 정보 필드 4: 소켓 상태입니다.

### <a name="tcp-socket-mss-peer-get"></a>TCP 소켓 MSS 피어 가져오기 

#### <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

**아이콘** ![TCP 소켓 MSS 피어 가져오기 아이콘](./media/user-guide/netx-events/image141.png)

**설명**

이 이벤트는 nx_tcp_socket_mss_peer_get을 통해 소켓 피어의 MSS 값을 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 피어의 MSS입니다.
- 정보 필드 4: 소켓 상태입니다.

### <a name="tcp-socket-mss-set"></a>TCP 소켓 MSS 설정 

#### <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

**아이콘** ![TCP 소켓 MSS 설정 아이콘](./media/user-guide/netx-events/image142.png)

**설명**

이 이벤트는 nx_tcp_socket_mss_set을 통해 소켓의 MSS를 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: MSS입니다.
- 정보 필드 4: 소켓 상태입니다.

### <a name="tcp-socket-peer-info-get"></a>TCP 소켓 피어 정보 가져오기 

#### <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

**아이콘** ![TCP 소켓 피어 정보 가져오기 아이콘](./media/user-guide/netx-events/image143.png)

**설명**

이 이벤트는 nx_tcp_socket_peer_info_get을 통해 피어(예: 연결하는 호스트) IP 주소와 포트에 대한 TCP 소켓에서 검색된 정보를 나타냅니다.

**정보 필드**

- 정보 필드 1: TCP 소켓에 대한 포인터입니다.
- 정보 필드 2: 피어 IP 주소입니다.
- 정보 필드 3: 피어 포트 번호입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="tcp-socket-receive"></a>TCP 소켓 수신 

#### <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

**아이콘** ![TCP 소켓 수신 아이콘](./media/user-guide/netx-events/image144.png)

**설명**

이 이벤트는 nx_tcp_socket_receive를 통해 소켓에서 데이터를 수신하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 소켓에 대한 포인터입니다.
- 정보 필드 2: 수신된 패킷에 대한 포인터입니다.
- 정보 필드 3: 수신된 패킷 길이입니다.
- 정보 필드 4: 수신 시퀀스 번호입니다.

### <a name="tcp-socket-receive-notify"></a>TCP 소켓 수신 알림 

#### <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

**아이콘** ![TCP 소켓 수신 알림 아이콘](./media/user-guide/netx-events/image145.png)

**설명**

이 이벤트는 nx_tcp_socket_receive_notify를 통해 소켓에 대한 수신 알림 콜백을 등록하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 수신 알림 콜백에 대한 포인터입니다. 정보 필드 4: 사용되지 않습니다.

### <a name="tcp-socket-send"></a>TCP 소켓 송신 

#### <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

**아이콘** ![TCP 소켓 송신 아이콘](./media/user-guide/netx-events/image146.png)

**설명**

이 이벤트는 nx_tcp_socket_send를 통해 소켓에 데이터를 송신하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 소켓에 대한 포인터입니다.
- 정보 필드 2: 패킷에 대한 포인터입니다.
- 정보 필드 3: 패킷 길이입니다.
- 정보 필드 4: 전송 시퀀스 번호입니다.

### <a name="tcp-socket-state-wait"></a>TCP 소켓 상태 대기 

#### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

**아이콘** ![TCP 소켓 상태 대기 아이콘](./media/user-guide/netx-events/image147.png)

**설명**

이 이벤트는 소켓이 nx_tcp_socket_state_wait를 통해 특정 상태가 될 때까지 대기하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 원하는 소켓 상태입니다.
- 정보 필드 4: 이전 소켓 상태입니다.

### <a name="tcp-socket-transmit-configure"></a>TCP 소켓 전송 구성 

#### <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

**아이콘** ![TCP 소켓 전송 구성 아이콘](./media/user-guide/netx-events/image148.png)

**설명**

이 이벤트는 nx_tcp_socket_transmit_configure를 통해 소켓의 전송 옵션을 구성하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 전송 큐 깊이입니다.
- 정보 필드 4: 시간 제한 값입니다.

### <a name="tcp-socket-window-update-notify-set"></a>TCP 소켓 창 업데이트 알림 설정 

#### <a name="nx_tcp_window_update_notify_set"></a>nx_tcp_window_update_notify_set

**아이콘** ![TCP 소켓 창 업데이트 알림 설정 아이콘](./media/user-guide/netx-events/image149.png)

**설명**

이 이벤트는 nx_tcp_window_update_notify_set을 통해 원격 호스트 수신 기간을 늘린다는 알림을 수신하는 TCP 소켓을 나타냅니다.

**정보 필드** 

- 정보 필드 1: TCP 소켓에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="udp-enable"></a>UDP 사용 

#### <a name="nx_udp_enable"></a>nx_udp_enable

**아이콘** ![UDP 사용 아이콘](./media/user-guide/netx-events/image150.png)

**설명**

이 이벤트는 nx_udp_enable을 통해 UDP를 사용하도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 사용되지 않습니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="udp-free-port-find"></a>UDP 사용 가능한 포트 찾기 

#### <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

**아이콘** ![UDP 사용 가능한 포트 찾기 아이콘](./media/user-guide/netx-events/image151.png)

**설명**

이 이벤트는 nx_udp_free_port_find를 통해 사용 가능한 UDP 포트를 찾는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 검색할 시작 포트입니다.
- 정보 필드 3: 사용 가능한 포트입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="udp-information-get"></a>UDP 정보 가져오기 

#### <a name="nx_udp_info_get"></a>nx_udp_info_get

**아이콘** ![UDP 정보 가져오기 아이콘](./media/user-guide/netx-events/image152.png)

**설명**

이 이벤트는 nx_udp_info_get을 통한 정보 가져오기를 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 송신한 UDP 바이트 수입니다.
- 정보 필드 3: 수신한 UDP 바이트 수입니다.
- 정보 필드 4: 잘못된 패킷입니다.

### <a name="udp-socket-bind"></a>UDP 소켓 바인딩 

#### <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

**아이콘** ![UDP 소켓 바인딩 아이콘](./media/user-guide/netx-events/image153.png)

**설명**

이 이벤트는 nx_udp_socket_bind를 통해 UDP 소켓을 포트에 바인딩하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 포트 번호입니다.
- 정보 필드 4: 대기 옵션입니다.

### <a name="udp-socket-bytes-available"></a>UDP 소켓 사용 가능 바이트 

#### <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

**아이콘** ![UDP 소켓 사용 가능 바이트 아이콘](./media/user-guide/netx-events/image154.png)

**설명**

이 이벤트는 nx_udp_socket_bytes_available을 통해 UDP 소켓에서 수신한 현재 바이트 수를 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 소켓에서 수신한 바이트 수입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="udp-socket-checksum-disable"></a>UDP 소켓 체크섬 사용 안 함 

#### <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

**아이콘** ![UDP 소켓 체크섬 사용 안 함 아이콘](./media/user-guide/netx-events/image155.png)

**설명**

이 이벤트는 nx_udp_socket_checksum_disable을 통해 UDP 소켓에서 데이터에 대한 체크섬을 사용하지 않도록 설정하는 것을 나타냅니다.

**정보 필드** 

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="udp-socket-checksum-enable"></a>UDP 소켓 체크섬 사용 

#### <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

**아이콘** ![UDP 소켓 체크섬 사용 아이콘](./media/user-guide/netx-events/image156.png)

**설명**

이 이벤트는 nx_udp_socket_checksum_enable을 통해 소켓에서 체크섬 처리를 사용하도록 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="udp-socket-create"></a>UDP 소켓 만들기 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**아이콘** ![UDP 소켓 만들기 아이콘](./media/user-guide/netx-events/image157.png)

**설명**

이 이벤트는 nx_udp_socket_create을 통해 UDP 소켓을 만드는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 서비스 유형입니다.
- 정보 필드 4: 최대 수신 큐입니다.

### <a name="udp-socket-delete-event"></a>UDP 소켓 삭제 이벤트 

#### <a name="nx_udp_socket_delete-event"></a>nx_udp_socket_delete event

**아이콘** ![UDP 소켓 삭제 이벤트 아이콘](./media/user-guide/netx-events/image158.png)

**설명**

이 이벤트는 nx_udp_socket_delete를 통해 UDP 소켓을 삭제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="udp-socket-information-get-event"></a>UDP 소켓 정보 가져오기 이벤트 

#### <a name="nx_udp_socket_info_get-event"></a>nx_udp_socket_info_get event

**아이콘** ![UDP 소켓 정보 가져오기 이벤트 아이콘](./media/user-guide/netx-events/image159.png)

**설명**

이 이벤트는 nx_udp_socket_info_get을 통해 UDP 소켓에 대한 정보를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 소켓을 통해 송신된 바이트 수입니다.
- 정보 필드 4: 소켓을 통해 수신된 바이트 수입니다.

### <a name="udp-socket-interface-set"></a>UDP 소켓 인터페이스 설정 

#### <a name="nx_udp_socket_interface_set-event"></a>nx_udp_socket_interface_set event

**아이콘** ![UDP 소켓 인터페이스 설정 아이콘](./media/user-guide/netx-events/image160.png)

**설명**

이 이벤트는 nx_udp_socket_interface_set을 통해 지정된 인터페이스를 사용하여 지정된 UDP 소켓의 송신 인터페이스를 설정하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: UDP 소켓에 대한 포인터입니다.
- 정보 필드 2: 소켓의 인터페이스에 해당하는 인덱스입니다.
- 정보 필드 3: 사용되지 않습니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="udp-socket-port-get"></a>UDP 소켓 포트 가져오기 

#### <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

**아이콘** ![UDP 소켓 포트 가져오기 아이콘](./media/user-guide/netx-events/image161.png)

**설명**

이 이벤트는 지정된 UDP 소켓이 nx_udp_socket_port_get을 통해 바인딩되는 UDP 포트를 검색하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: UDP 소켓에 대한 포인터입니다.
- 정보 필드 3: 포트 번호입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="udp-socket-receive"></a>UDP 소켓 수신 

#### <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

**아이콘** ![UDP 소켓 수신 아이콘](./media/user-guide/netx-events/image162.png)

**설명**

이 이벤트는 nx_udp_socket_receive를 통해 지정된 UDP 소켓에서 데이터를 수신하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: UDP 소켓에 대한 포인터입니다.
- 정보 필드 3 수신된 패킷에 대한 포인터입니다.
- 정보 필드 4 수신된 패킷 크기입니다.

### <a name="udp-socket-receive-notify"></a>UDP 소켓 수신 알림 

#### <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

**아이콘** ![UDP 소켓 수신 알림 아이콘](./media/user-guide/netx-events/image163.png) **설명**

이 이벤트는 nx_udp_socket_receive_notify를 통해 수신 알림 콜백을 등록하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 수신 알림 함수에 대한 포인터입니다. 정보 필드 4: 사용되지 않습니다.

### <a name="udp-socket-send"></a>UDP 소켓 송신 

#### <a name="nx_udp_socket_send"></a>nx_udp_socket_send

**아이콘** ![UDP 소켓 송신 아이콘](./media/user-guide/netx-events/image164.png)

**설명**

이 이벤트는 nx_udp_socket_send를 사용하여 UDP 소켓을 통해 데이터를 보내는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 소켓에 대한 포인터입니다.
- 정보 필드 2: 패킷에 대한 포인터입니다.
- 정보 필드 3: 패킷 길이입니다.
- 정보 필드 4: 대상 IP 주소입니다.

### <a name="udp-socket-unbind"></a>UDP 소켓 바인딩 해제 

#### <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

**아이콘** ![UDP 소켓 바인딩 해제 아이콘](./media/user-guide/netx-events/image165.png)

**설명**

이 이벤트는 nx_udp_socket_unbind를 사용하여 소켓을 통해 UDP 포트를 바인딩 해제하는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: IP 인스턴스에 대한 포인터입니다.
- 정보 필드 2: 소켓에 대한 포인터입니다.
- 정보 필드 3: 포트 번호입니다.
- 정보 필드 4: 사용되지 않습니다.

### <a name="udp-source-extract"></a>UDP 원본 추출 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**아이콘** ![UDP 원본 추출 아이콘](./media/user-guide/netx-events/image166.png)

**설명**

이 이벤트는 nx_udp_source_extract를 통해 수신된 UDP 패킷의 IP 주소와 포트 번호를 가져오는 것을 나타냅니다.

**정보 필드**

- 정보 필드 1: 패킷에 대한 포인터입니다.
- 정보 필드 2: 발신자의 IP 주소입니다.
- 정보 필드 3: 발신자의 포트 번호입니다.
- 정보 필드 4: 사용되지 않습니다.