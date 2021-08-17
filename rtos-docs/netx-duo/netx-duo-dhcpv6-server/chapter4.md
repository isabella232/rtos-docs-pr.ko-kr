---
title: 챕터 4 - Azure RTOS NetX Duo DHCPv6 서버 서비스
description: 이 챕터에는 모든 NetX Duo DHCPv6 서버 서비스에 대한 설명이 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf6b43f70a7159af6c24496ec2ae2276d5e271af2ad3af99687181df3bf6be6c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792029"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a>챕터 4 - Azure RTOS NetX Duo DHCPv6 서버 서비스

이 챕터에는 모든 NetX Duo DHCPv6 서버 서비스(아래 참조)에 대한 설명이 포함되어 있습니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

- nx_dhcpv6_server_create *DHCPv6 서버 인스턴스를 만듭니다.*
- nx_dhcpv6_server_delete *DHCPv6 서버 인스턴스를 삭제합니다.*
- nx_dhcpv6_server_start *DHCPv6 서버 작업을 시작합니다.*
- nx_dhcpv6_server_suspend *DHCPv6 서버 작업을 일시 중단합니다.*
- nx_dhcpv6_server_resume *DHCPv6 클라이언트 처리를 계속합니다.*
- nx_dhcpv6_server_suspend *DHCPv6 클라이언트 처리를 일시 중단합니다.*
- nx_dhcpv6_create_dns_address *옵션 요청 대상 DNS 서버를 설정합니다.*
- nx_dhcpv6_create_ip_address_range *임대할 IP 주소 범위를 만듭니다.*
- nx_dhcpv6_reserve_ip_address_range *서버 목록의 IP 주소 범위를 예약합니다.*
- nx_dhcpv6_set_server_duid *DHCPv6 패킷의 서버 DUID를 설정합니다.*
- nx_dhcpv6_add_ip_address_lease *DHCPv6 서버 테이블에 임대 레코드를 추가합니다.*
- Nx_dhcpv6_retrieve_ip_address_lease *서버 테이블에서 IP 임대 레코드를 검색합니다.*
- nx_dhcpv6_add_client_record *서버 테이블에 DHCPv6 클라이언트 레코드를 추가합니다.*
- nx_dhcpv6_retrieve_client_record *서버 테이블에서 클라이언트 레코드를 검색합니다.*
- nx_dhcpv6_server_interface_set *서버 DHCPv6 서비스의 인터페이스 인덱스를 설정합니다.*
- nx_dhcpv6_server_option_request_handler_set *옵션 요청 처리기를 설정합니다.*

## <a name="nx_dhcpv6_create_dns_address"></a>nx_dhcpv6_create_dns_address

### <a name="set-the-network-dns-server"></a>네트워크 DNS 서버를 설정합니다.

**프로토타입**

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

**설명**

이 서비스는 서버 DHCPv6 네트워크 인터페이스의 DNS 서버 주소를 사용하여 DHCPv6 서버를 로드합니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터
- **dns_ipv6_address** DNS 서버에 대한 포인터

**반환 값**

- **NX_SUCCESS** (0x00) DNS 서버가 DHCPv6 서버 인스턴스에 저장되었습니다.
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 잘못된 주소가 지정되었습니다.
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

응용 프로그램 코드

**예제**

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a>nx_dhcpv6_create_ip_address_range

### <a name="create-the-server-ip-address-list"></a>서버 IP 주소 목록 만들기

**프로토타입**

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

**설명**

이 서비스는 서버의 할당 가능한 주소 범위의 시작 주소와 끝 주소로 지정된 IP 주소 목록을 만듭니다. 시작 주소와 끝 주소는 서버 인터페이스 주소 접두사와 일치해야 합니다(서버 DHCPv6 인터페이스와 동일한 링크에 있어야 함). 실제로 추가된 주소 수가 반환됩니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터
- **start_ipv6_address** 추가할 주소의 시작 부분
- **end_ipv6_address** 추가할 주소 끝 부분
- ***addresses_added** 추가된 주소 출력

**반환 값**

- **NX_SUCCESS** (0x00) IP 주소 목록을 성공적으로 만들었습니다.
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 잘못된 주소가 지정되었습니다.
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

응용 프로그램 코드

**예제**

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a>nx_dhcpv6_reserve_ip_address_range

### <a name="reserve-specified-range-of-ip-addresses"></a>지정된 IP 주소 범위 예약

**프로토타입**

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

**설명**

이 서비스는 시작 주소와 끝 주소로 지정된 IP 주소 범위를 예약합니다. 이러한 주소는 이전에 만든 서버 IP 주소 범위 내에 있어야 합니다. 이러한 주소는 DHCPv6 서버에서 클라이언트에 할당하지 않습니다. 시작 주소와 끝 주소는 서버 인터페이스 주소 접두사와 일치해야 합니다(서버 DHCPv6 네트워크 인터페이스와 동일한 링크에 있어야 함). 실제로 예약된 주소 수가 반환됩니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터
- **start_ipv6_address** 예약할 주소의 시작 부분
- **end_ipv6_address** 예약할 주소 끝 부분
- ***addresses_reserved** 예약된 주소 수

**반환 값**

- **NX_SUCCESS** (0x00) RELEASE 메시지가 성공적으로 생성 및 처리되었습니다.
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 잘못된 주소가 지정되었습니다.
- **NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) 시작 주소가 서버 주소 목록에 없습니다.
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

응용 프로그램 코드

**예제**

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a>nx_dhcpv6_server_create

### <a name="create-the-dhcpv6-server-instance"></a>DHCPv6 서버 인스턴스 만들기 

**프로토타입**

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

**설명**

이 서비스는 지정된 입력을 사용하여 DHCPv6 서버 작업을 만듭니다. 콜백 처리기는 선택적 입력입니다. 스택 포인터, IP 인스턴스 및 패킷 풀 입력은 필수입니다. IP 인스턴스 및 패킷 풀이 이미 생성되어 있어야 합니다.

사용자는 nx_dhcpv6_server_option_request_handler_set를 호출하여 옵션 요청 처리기를 설정하는 것이 좋습니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터
- **ip_ptr** IP 인스턴스에 대한 포인터
- **name_str** 서버 이름에 대한 포인터
- **packet_pool_ptr** 서버 패킷 풀에 대한 포인터
- **stack_ptr** 서버 스택 메모리에 대한 포인터
- **stack_size** 서버 스택 메모리의 크기
- **dhcpv6_address_declined_handler** 클라이언트 거부 또는 해제 메시지 처리기에 대한 포인터
- **dhcpv6_option_request_handler** 옵션 요청 옵션 처리기에 대한 포인터

**반환 값**

- **NX_SUCCESS** (0x00) 서버를 성공적으로 다시 시작했습니다.
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력
- NX_DHCPV6_PARAM_ERROR 잘못된 비 포인터 입력

**허용된 원본**

응용 프로그램 코드

**예제**

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a>nx_dhcpv6_server_delete

### <a name="delete-the-dhcpv6-server"></a>DHCPv6 서버 삭제

**프로토타입**

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**설명**

이 서비스는 DHCPv6 서버 작업 및 서버가 처리하는 모든 요청을 삭제합니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터

**반환 값**

- **NX_SUCCESS** (0x00) 서버를 성공적으로 삭제함
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

스레드

**예제**

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a>nx_dhcpv6_server_resume

### <a name="resume-dhcpv6-server-task"></a>DHCPv6 서버 작업 다시 시작 

**프로토타입**

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**설명**

이 서비스는 DHCPv6 서버 작업 및 서버가 처리하는 모든 요청을 다시 시작합니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터

**반환 값**

- **NX_SUCCESS** (0x00) 서버를 성공적으로 다시 시작했습니다.
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) 서버가 이미 실행되고 있습니다.
- **status**(변수) ThreadX 및 NetX Duo 오류 상태
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

스레드

**예제**

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a>nx_dhcpv6_server_suspend

### <a name="suspend-dhcpv6-server-task"></a>DHCPv6 서버 작업 일시 중단 

**프로토타입**

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**설명**

이 서비스는 DHCPv6 서버 작업 및 서버가 처리하는 모든 요청을 일시 중단합니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터

**반환 값**

- **NX_SUCCESS** (0x00) 서버를 성공적으로 다시 시작했습니다.
- **NX_DHCPV6_NOT_STARTED** (0xE92) 서버가 시작되지 않았습니다. 
- **Status**(변수) ThreadX 및 NetX Duo 오류 상태
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

스레드

**예제**

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a>nx_dhcpv6_server_start

### <a name="start-the-dhcpv6-server-task"></a>DHCPv6 서버 작업 시작 

**프로토타입**

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**설명**

이 서비스는 DHCPv6 서버 작업을 시작하고 서버가 DHCPv6 클라이언트 메시지 수신에 대한 애플리케이션 요청을 처리할 수 있게 준비합니다. 서버 인스턴스에 충분한 정보(서버 DUID)가 있는지 확인하고, DHCPv6 메시지를 보내고 받기 위한 UDP 소켓을 만들고 바인딩하며, 세션 시간 및 IP 임대 만료 시간을 추적하는 타이머를 활성화합니다.

>[!NOTE] 
> 호스트 애플리케이션은 DHCPv6 서버를 실행하기 전에 서버에서 IP 주소를 할당할 수 있는 IP 주소 범위를 만들어야 합니다. 또한 서버 DUID 및 DHCPv6 인터페이스를 설정해야 합니다(각각 *nx_dhcpv6_server_duid_set* 및 *nx_dhcpv6_server_interface_set* 참조).

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터

**반환 값**

- **NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) 서버가 이미 실행되고 있습니다.
- **NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) 서버에 임대할 할당 가능한 주소가 없습니다.
- **NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) 글로벌 주소 인덱스를 설정하지 않았습니다.
- **NX_DHCPV6_NO_SERVER_DUID** (0xE92) 서버 DUID가 생성되지 않았습니다. 
- **status**(변수) ThreadX 및 NetX Duo 오류 상태
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

스레드

**예제**

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a>nx_dhcpv6_retrieve_ip_address_lease

### <a name="get-an-ip-address-lease-from-the-server-table"></a>서버 테이블에서 IP 주소 임대 가져오기

**프로토타입**

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

**설명**

이 서비스는 지정된 테이블 인덱스 위치의 서버 테이블에서 IP 주소 임대 레코드를 검색합니다. 클라이언트 레코드 데이터 검색 전후로 이 작업을 수행할 수 있습니다.

DHCPv6 서버와 비휘발성 메모리 간에 데이터를 저장하고 검색하는 기능은 DHCPv6 프로토콜의 요구 사항입니다. IP 임대 데이터와 클라이언트 레코드 데이터를 비휘발성 메모리에 저장하는 순서에는 차이가 없습니다.

>[!NOTE] 
> 먼저 DHCPv6 서버를 중지하거나 일시 중단하지 않고 서버 테이블 간에 데이터를 복사하는 것은 권장되지 않습니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터
- **table_index** 임대를 저장할 테이블 인덱스
- **lease_IP_address** 클라이언트에 임대된 IP 주소에 대한 포인터
- **T1** 클라이언트에서 요청한 갱신 시간
- **T2** 클라이언트에서 요청한 재바인딩 시간
- **valid_lifetime** 클라이언트 임대가 더 이상 사용되지 않습니다.
- **preferred_lifetime** 클라이언트 임대가 유효하지 않습니다.

**반환 값**

- **NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.
- **NX_DHCPV6_PARAMETER_ERROR** (0xE93) 잘못된 IP 임대 데이터 입력
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

애플리케이션 코드

**예제**

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a>nx_dhcpv6_add_ip_address_lease

### <a name="add-an-ip-address-lease-to-the-server-table"></a>서버 테이블에 IP 주소 임대 추가

**프로토타입**

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

**설명**

이 서비스는 이전 DHCPv6 서버 세션의 IP 임대 데이터를 비휘발성 메모리에서 서버 임대 테이블로 로드합니다. 서버가 처음으로 실행 중이고 이전 임대 데이터가 없는 경우에는 이 작업이 필요하지 않습니다. 이 경우 호스트 애플리케이션은 *nx_dhcpv6_create_ip_address_range* 서비스를 사용하여 IP 주소를 할당하기 위한 IP 주소 범위를 만들어야 합니다. 이 데이터는 DHCPv6 임대 레코드를 다시 생성하기에 충분합니다. 테이블 인덱스를 지정할 필요가 없습니다. 0xFFFFFFFF(무한대)로 설정되면 DHCPv6 서버가 데이터를 복사하기 위해 다음으로 사용 가능한 슬롯을 찾습니다.

>[!NOTE] 
> 클라이언트 레코드를 업로드하려면 먼저 IP 임대 데이터를 업로드해야 합니다. 둘 다 DHCPv6 서버를 시작하기 전에 수행해야 합니다.

DHCPv6 서버와 비휘발성 메모리 간에 데이터를 저장하고 검색하는 기능은 DHCPv6 프로토콜의 요구 사항입니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터
- **table_index** 임대를 저장할 테이블 인덱스
- **lease_IP_address** 클라이언트에 임대된 IP 주소에 대한 포인터
- **T1** 클라이언트에서 요청한 갱신 시간
- **T2** 클라이언트에서 요청한 재바인딩 시간
- **valid_lifetime** 클라이언트 임대가 더 이상 사용되지 않습니다.
- **preferred_lifetime** 클라이언트 임대가 유효하지 않습니다.

**반환 값**

- **NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.
- **NX_DHCPV6_TABLE_FULL** (0xEC4) 추가 임대 데이터를 위한 공간이 없습니다.**
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) 임대 데이터가 서버 DHCPv6 인터페이스와 연결된 것 같지 않습니다.
- **NX_DHCPV6_PARAM_ERROR** (0xE93) 잘못된 IP 임대 데이터 입력
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

애플리케이션 코드

**예제**

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a>nx_dhcpv6_add_client_record

### <a name="add-a-client-record-to-the-server-table"></a>서버 테이블에 클라이언트 레코드 추가

**프로토타입**

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

**설명**

이 서비스는 비휘발성 메모리의 클라이언트 데이터를 한 번에 한 레코드씩 서버 테이블로 복사합니다. 서버가 다시 부팅되며 이전 세션의 클라이언트 데이터가 메모리에서 복원되는 경우에만 필요합니다. 서버에 이전 데이터가 없으면 DHCPv6 서버에서 클라이언트 테이블을 초기화하여 클라이언트 레코드를 추가할 수 있습니다.

테이블 인덱스를 지정할 필요는 없습니다. 0xFFFFFFFF(무한대)로 설정되면 DHCPv6 서버는 사용 가능한 다음 슬롯을 찾습니다. DHCPv6 서버는 이 데이터로 클라이언트 레코드를 다시 생성할 수 있습니다.

>[!NOTE] 
> 클라이언트에서 데이터를 기록하기 전에 호스트 애플리케이션에서 IP 임대 데이터를 업로드해야 합니다. 그러면 각 클라이언트 레코드가 해당 테이블의 해당 IP 임대 레코드와 조인되도록 DHCPv6 서버에서 내부적으로 테이블을 교차 연결할 수 있습니다. 메모리에서 IP 임대 데이터를 업로드하는 방법에 대한 자세한 내용은 *nx_dhcpv6_add_ip_address_lease* 를 참조하세요.

>[!NOTE] 
> DUID 유형에 따라 모든 데이터를 제공해야 하는 것은 아닙니다. 예를 들어 클라이언트에 공급업체에서 할당한 DUID 유형이 있는 경우, DUID 링크 계층 매개 변수(MAC 주소, 하드웨어 종류, DUID 시간)에 0으로 전송할 수 있습니다.

DHCPv6 서버와 비휘발성 메모리 간에 데이터를 저장하고 검색하는 기능은 DHCPv6 프로토콜의 요구 사항입니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터

**반환 값**

- **NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.
- **NX_ INVALID_PARAMETERS** (0x4D) 잘못된 비포인터 입력**
- **NX_DHCPV6_TABLE_FULL** (0xEC4) 다른 클라이언트 레코드를 추가할 빈 슬롯이 남아 있지 않습니다.
- **NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) 서버 임대 테이블에서 클라이언트 할당 주소를 찾을 수 없습니다.
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

애플리케이션 코드

**예제**

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a>nx_dhcpv6_retrieve_client_record

### <a name="retrieve-a-client-record-from-the-server-table"></a>서버 테이블에서 클라이언트 레코드 검색

**프로토타입**

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

**설명**

이 서비스는 서버의 클라이언트 레코드 테이블에서 비휘발성 메모리에 저장할 필수 데이터를 복사합니다. 서버는 역방향 프로세스(서버 테이블에 데이터 업로드)로 해당 데이터의 적절한 클라이언트 레코드를 다시 생성할 수 있습니다. DUID 유형에 관계없이 모든 포인터는 NULL 포인터가 될 수 없습니다. 데이터는 모든 매개 변수에서 0으로 초기화됩니다. 예를 들어 클라이언트 DUID 유형이 링크 계층+시간인 경우 공급업체 번호는 0으로 반환되고 프라이빗 ID는 빈 문자열입니다.

DHCPv6 서버와 비휘발성 메모리 간에 데이터를 저장하고 검색하는 기능은 DHCPv6 프로토콜의 요구 사항입니다. IP 임대 데이터와 클라이언트 레코드 데이터를 비휘발성 메모리에 저장하는 순서에는 차이가 없습니다.

>[!NOTE] 
> 먼저 DHCPv6 서버를 중지하거나 일시 중단하지 않고 서버 테이블 간에 데이터를 복사하는 것은 권장되지 않습니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터
- **table_index** 서버의 클라이언트 테이블에 인덱스
- **message_xid** 클라이언트 서버 트랜잭션 ID
- **client_address** 클라이언트에 임대되는 IPv6 주소
- **client_state** 클라이언트 DHCPv6 상태(예: bound)
- **IP_lease_time_accrued** 임대 시간이 이미 만료되었습니다. **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터
- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터

**반환 값**

- **NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.
- **NX_DHCPV6_INVALID_DUID** (0xECC) 유효하지 않거나 일치하지 않는 DUID 데이터
- **NX_PTR_ERROR** (0x16) 잘못된 포인터 입력
- NX_INVALID_PARAMETERS (0x4D) 잘못된 비포인터 입력

**허용된 원본**

애플리케이션 코드

**예제**

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a>nx_dhcpv6_server_interface_set

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a>서버 DHCPv6 인터페이스의 인터페이스 인덱스 설정

**프로토타입**

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

**설명**

이 서비스는 DHCPv6 서버가 DHCPv6 클라이언트 요청을 처리하는 네트워크 인터페이스를 설정합니다. 멀티홈을 지원하지 않는 NetX Duo 버전의 경우 인터페이스 값이 기본적으로 0으로 설정됩니다. 해당 DHCPv6 인터페이스에서 서버 글로벌 주소를 가져오려면 글로벌 주소 인덱스가 필요합니다. 이는 DHCPv6 논리에서 임대 주소 및 기타 DHCPv6 데이터가 DHCPv6 서버와 연결되어 있는지 확인하는 데 사용됩니다.

단일 홈 디바이스에 설치되어 있거나 멀티홈을 지원하지 않는 애플리케이션의 경우에도 DHCPv6 서버를 시작하기 전에 이를 호출해야 합니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터
- **iface_index** 서버 DHCPv6 서버 인터페이스
- **ga_address_index** 서버 IP 인스턴스 주소 테이블의 서버 글로벌 주소 인덱스

**반환 값**

- **NX_SUCCESS** (0x00) 서버를 성공적으로 시작했습니다.
- **NX_INVALID_INTERFACE** (0x4C) 인터페이스가 없습니다.
- NX_NO_INTERFACE_ADDRESS (0x50) 글로벌 인덱스가 IP 인스턴스 최대 IPv6 주소(NX_MAX_IPV6_ADDRESSES)를 초과합니다.
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

애플리케이션 코드

**예제**

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a>nx_dhcpv6_set_server_duid

### <a name="set-the-server-duid-for-dhcpv6-packets"></a>DHCPv6 패킷의 서버 DUID 설정

**프로토타입**

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

**설명**

이 서비스는 서버 DUID를 설정하며, 호스트 애플리케이션에서 서버를 시작하기 전에 호출해야 합니다. 링크 계층 및 링크 계층 시간 DUID 유형의 경우, 호스트 애플리케이션이 하드웨어 유형과 MAC 주소 데이터를 제공해야 합니다. 링크 계층 시간 DUID의 경우, 시간 포인터가 유효한 시간을 가리켜야 합니다. 2000년 1월 1일 이후 경과된 시간(초)이 일반적인 시드 값입니다. 서버 DUID 유형이 엔터프라이즈, 공급업체에서 할당한 형식인 경우에는 사용자가 구성할 수 있는 옵션 NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID 및 NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID로 DUID가 생성되고, 시간 및 MAC 주소 값을 NULL로 설정할 수 있습니다.

>[!NOTE] 
> 호스트 애플리케이션은 재부팅 후에도 클라이언트에 보내는 메시지에 동일한 DUID를 사용할 수 있도록 서버 DUID 매개 변수를 비휘발성 메모리에 저장해야 합니다. 이는 DHCPv6 프로토콜(RFC 3315)의 요구 사항입니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터
- **duid_type** DHCPv6 서버 DUID 유형
- **hardware_type** 하드웨어 유형(예: 이더넷)
- **mac_address_msw** DHCPv6 서버에 대한 포인터
- **mac_address_lsw** DHCPv6 서버에 대한 포인터
- **time** DUID의 시간 값

**반환 값**

- **NX_SUCCESS** (0x00) 서버를 성공적으로 일시 중단했습니다.
- **NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) 알 수 없거나 지원되지 않는 DUID 유형
- **NX_INVALID_PARAMETERS** (0x4D) 잘못된 비포인터 입력
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

애플리케이션 코드

**예제**

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a>nx_dhcpv6_server_option_request_handler_set

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a>DHCPv6 서버 인스턴스의 옵션 요청 처리기 설정 

**프로토타입**

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

**설명**

이 서비스는 DHCPv6 서버 확장 옵션 요청 처리기를 설정합니다.

**입력 매개 변수**

- **dhcpv6_server_ptr** DHCPv6 서버에 대한 포인터
- **dhcpv6_option_request_handler_extended** 확장 옵션 요청 처리기에 대한 포인터

**반환 값**

- **NX_SUCCESS** (0x00) 서버를 성공적으로 다시 시작했습니다.
- NX_PTR_ERROR (0x16) 잘못된 포인터 입력

**허용된 원본**

응용 프로그램 코드

**예제**

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```