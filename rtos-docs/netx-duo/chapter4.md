---
title: 4장 - Azure RTOS NetX Duo 서비스 설명
description: 이 장에서는 모든 Azure RTOS NetX Duo 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 85617aadab7f484a4f4e467fd13f815f4d8b5609
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811862"
---
# <a name="chapter-4---description-of-azure-rtos-netx-duo-services"></a>4장 - Azure RTOS NetX Duo 서비스 설명

이 장에서는 모든 Azure RTOS NetX Duo 서비스를 알파벳 순서로 설명합니다. 서비스 이름은 모든 유사한 서비스가 함께 그룹화되도록 설계되었습니다. 예를 들어 모든 ARP 서비스는 이 장의 시작 부분에 있습니다. 

NetX Duo에는 IPv6 기반 프로토콜 및 작업을 지원하기 위해 도입된 여러 가지 새로운 서비스가 있습니다. Net Duo의 IPv6 지원 서비스에는 접두사 ***nxd***가 있습니다. *는 IPv4 및 IPv6 이중 스택 작업을 위해 설계되었음을 나타냅니다.

NetX의 기존 서비스는 NetX Duo에서 완벽하게 지원됩니다. NetX 애플리케이션은 최소한의 이식 노력으로 NetX Duo로 마이그레이션할 수 있습니다.

> [!NOTE]
> BSD 호환 소켓 API는 고성능 NetX Duo API를 충분히 활용할 수 없는 레거시 애플리케이션 코드에 사용할 수 있습니다. BSD 호환 소켓 API에 대한 자세한 내용은 부록 D를 참조하세요.

각 설명의 “반환 값” 섹션에서 **BOLD** 로 표시된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 NX_DISABLE_ERROR_CHECKING 옵션의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다. “허용되는 원본” 섹션은 각 NetX Duo 서비스를 호출할 수 있는 항목을 나타냅니다.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate   
ARP 캐시의 모든 동적 항목 무효화

### <a name="prototype"></a>프로토타입     

```c
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a>Description   
이 서비스는 현재 ARP 캐시에 있는 모든 동적 ARP 항목을 무효화합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP 캐시 무효화에 성공했습니다.
- **NX_NOT_ENABLED**(0x14) ARP가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) IP 주소가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용 위치   
스레드

### <a name="preemption-possible"></a>가능한 선점    
예

### <a name="example"></a>예제

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);

/* If status is NX_SUCCESS the dynamic ARP entries were
   successfully invalidated. */
```
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set  
동적 ARP 항목 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);  
```

### <a name="description"></a>Description    
이 서비스는 ARP 캐시의 동적 항목을 할당하고 지정된 IP를 실제 주소 매핑으로 설정합니다. 실제 주소를 0으로 지정하면 실제 주소를 확인하기 위해 실제 ARP 요청이 네트워크로 전송됩니다. ARP 에이징이 활성이거나 ARP 캐시가 고갈되었고 최근에 사용된 ARP 항목이 아닌 경우에도 이 항목이 제거됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 매핑할 IP 주소입니다.
- **physical_msw** 실제 주소의 상위 16비트(47-32)입니다.
- **physical_lsw** 실제 주소의 하위 32비트(31-0)입니다.

### <a name="return-values"></a>반환 값    

- **NX_SUCCESS**(0x00) ARP 동적 항목 설정에 성공했습니다.
- **NX_NO_MORE_ENTRIES**(0x17) ARP 캐시에 사용할 수 있는 ARP 항목이 더 이상 없습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) IP 인스턴스 포인터가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치    
스레드

### <a name="preemption-possible"></a>가능한 선점    
예

### <a name="example"></a>예제

```c
/* Setup a dynamic ARP entry on the previously created IP
   Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
                                  0x1022, 0x1234);

/* If status is NX_SUCCESS, there is now a dynamic mapping between
   the IP address of 1.2.3.4 and the physical hardware address of
   10:22:00:00:12:34. */
```
### <a name="see-also"></a>참고 항목 

- nx_arp_dynamic_entries_invalidate
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_enable"></a>nx_arp_enable  
ARP(주소 확인 프로토콜)를 사용하도록 설정

### <a name="prototype"></a>프로토타입    

```c
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory,
    ULONG arp_cache_size);
```

### <a name="description"></a>Description

이 서비스는 특정 IP 인스턴스에 대해 NetX Duo의 ARP 구성 요소를 초기화합니다. ARP 초기화에는 ARP 메시지를 보내고 받는 데 필요한 ARP 캐시 및 다양한 ARP 처리 루틴 설정이 포함됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **arp_cache_memory** ARP 캐시를 지정할 메모리 영역에 대한 포인터입니다.
- **arp_cache_size** 각 ARP 항목은 52바이트이므로 총 ARP 항목 수는 52로 나뉘는 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP를 사용하도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 또는 캐시 메모리 포인터가 잘못되었습니다.
- **NX_SIZE_ERROR**(0x09) 사용자 제공 ARP 캐시 메모리가 너무 작습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_ALREADY_ENABLED**(0x15) 이 구성 요소는 이미 사용하도록 설정되어 있습니다.

### <a name="allowed-from"></a>허용 위치   
초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점  
예

### <a name="example"></a>예제

```c
/* Enable ARP and supply 1024 bytes of ARP cache memory for
   previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);

/* If status is NX_SUCCESS, ARP was successfully enabled for this IP
instance.*/
```
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_entry_delete"></a>nx_arp_entry_delete   
ARP 항목 삭제

### <a name="prototype"></a>프로토타입  

```c
UINT nx_arp_entry_delete(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```
### <a name="description"></a>Description

이 서비스는 IP 내부 ARP 테이블에서 지정된 IP 주소에 대한 ARP 항목을 제거합니다.

### <a name="parameters"></a>매개 변수  

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 지정된 IP 주소를 가진 ARP 항목을 삭제해야 합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP를 사용하도록 설정하는 데 성공했습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) 지정된 IP 주소를 가진 항목을 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) IP 또는 캐시 메모리 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 지정된 IP 주소가 유효하지 않습니다.

### <a name="allowed-from"></a>허용 위치  
초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점  
예

### <a name="example"></a>예제

```c
/* Delete the ARP entry with the IP address 1.2.3.4. */
status = nx_arp_entry_delete(&ip_0, IP_ADDRESS(1, 2, 3, 4));

/* If status is NX_SUCCESS, ARP entry with the specified IP address
   is deleted.*/
```

### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send   
무상 ARP 요청 송신

### <a name="prototype"></a>프로토타입  

```c
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler)(NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```                               
### <a name="description"></a>Description

이 서비스는 인터페이스 IP 주소가 유효한 동안 모든 실제 인터페이스를 통해 무상 ARP 요청을 전송합니다. 이어서 ARP 응답을 받으면 제공된 응답 처리기가 호출되어 무상 ARP에 대한 응답을 처리합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **response_handler** 응답 처리 함수에 대한 포인터입니다. NX_NULL이 제공되면 응답은 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 무상 ARP 송신에 성공했습니다.
- **NX_NO_PACKET**(0x01) 사용 가능한 패킷이 없습니다.
- **NX_NOT_ENABLED**(0x14) ARP가 사용하도록 설정되지 않았습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 현재 IP 주소가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully
   sent. */
```

### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find
제공된 IP 주소에 해당하는 실제 하드웨어 주소를 찾습니다.

### <a name="prototype"></a>프로토타입  

```c
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG *physical_msw,
    ULONG *physical_lsw);
```
### <a name="description"></a>Description

이 서비스는 제공된 IP 주소와 연결된 ARP 캐시에서 실제 하드웨어 주소를 찾으려고 시도합니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 검색할 IP 주소입니다.
- **physical_msw** 물리적 주소의 상위 16비트(47-32)를 반환하는 변수를 가리키는 포인터입니다.
- **physical_lsw** 실제 주소의 하위 32비트(31-0)를 반환하는 변수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP 하드웨어 주소 찾기에 성공했습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) ARP 캐시에 매핑이 없습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) IP 또는 메모리 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Search for the hardware address associated with the IP address of
   1.2.3.4 in the ARP cache of the previously created IP
   Instance 0. */
status = nx_arp_hardware_address_find(&ip_0, IP_ADDRESS(1,2,3,4),
                                      &physical_msw,
                                      &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
   physical_lsw contain the hardware address.*/
```   
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_info_get"></a>nx_arp_info_get
ARP 활동에 대한 정보 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a>Description

이 서비스는 연결된 IP 인스턴스의 ARP 활동에 대한 정보를 검색합니다.

> [!NOTE]
> 대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **arp_requests_sent** 이 IP 인스턴스에서 보낸 총 ARP 요청 대상에 대한 포인터입니다.
- **arp_requests_received** 네트워크에서 받은 총 ARP 요청 대상에 대한 포인터입니다.
- **arp_responses_sent** 이 IP 인스턴스에서 보낸 총 ARP 응답 대상에 대한 포인터입니다.
- **arp_responses_received** 네트워크에서 수신된 총 ARP 응답 대상을 가리키는 포인터입니다.
- **arp_dynamic_entries** 현재 동적 ARP 항목 수 대상을 가리키는 포인터입니다.
- **arp_static_entries** 현재 고정 ARP 항목 수 대상을 가리키는 포인터입니다.
- **arp_aged_entries** 오래되고 잘못된 총 ARP 항목 수 대상을 가리키는 포인터입니다.
- **arp_invalid_messages** 수신되었으나 유효하지 않은 총 ARP 메시지 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(&ip_0, &arp_requests_sent,
                         &arp_requests_received,
                         &arp_responses_sent,
                         &arp_responses_received,
                         &arp_dynamic_entries,
                         &arp_static_entries,
                         &arp_aged_entries,
                         &arp_invalid_messages);

/* If status is NX_SUCCESS, the ARP information has been stored in
   the supplied variables. */
```
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find
제공된 물리적 주소에 해당하는 IP 주소 찾기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```
### <a name="description"></a>Description

이 서비스는 제공된 물리적 주소와 연결된 ARP 캐시에서 IP 주소를 찾으려고 시도합니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 매핑된 IP 주소가 있는 경우, 반환 IP 주소를 가리키는 포인터입니다.
- **physical_msw** 검색할 물리적 주소의 상위 16비트(47-32)입니다.
- **physical_lsw** 검색할 물리적 주소의 하위 32비트(31-0)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP IP 주소 찾기에 성공했습니다. 
- **NX_ENTRY_NOT_FOUND**(0x16) ARP 캐시에 매핑이 없습니다.
- **NX_PTR_ERROR**(0x07) IP 또는 메모리 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PARAMETERS**(0x4D) Physical_msw 및 physical_lsw는 둘 다 0입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Search for the IP address associated with the hardware address of
   0x0:0x01234 in the ARP cache of the previously created IP
   Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
   associated IP address. */
```
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete
모든 정적 ARP 항목 삭제

### <a name="prototype"></a>프로토타입  

```c
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 ARP 캐시의 모든 고정 항목을 삭제합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 고정 항목이 삭제됩니다.
- **NX_PTR_ERROR**(0x07) 잘못된 ip_ptr 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Delete all the static ARP entries for IP Instance 0, assuming
   "ip_0" is the NX_IP structure for IP Instance 0. */
status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
   have been deleted. */
```
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create
ARP 캐시에 고정 IP-하드웨어 매핑 만들기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 ARP 캐시에 고정 IP-물리적 주소 매핑을 만듭니다. 고정 ARP 항목에는 ARP 정기 업데이트가 적용되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 매핑할 IP 주소입니다.
- **physical_msw** 매핑할 물리적 주소의 상위 16비트(47-32)입니다.
- **physical_lsw** 매핑할 물리적 주소의 하위 32비트(31-0)입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS** (0x00) ARP 고정 항목 만들기에 성공했습니다.
- **NX_NO_MORE_ENTRIES**(0x17) ARP 캐시에 사용할 수 있는 ARP 항목이 더 이상 없습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PARAMETERS**(0x4D) Physical_msw 및 physical_lsw는 둘 다 0입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Create a static ARP entry on the previously created IP
   Instance 0. */
status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
                                    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
   the IP address of 1.2.3.4 and the physical hardware address of
   0x00:0x1234. */
```
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete 
ARP 캐시에서 고정 IP-하드웨어 매핑 삭제

### <a name="prototype"></a>프로토타입  

```c
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 ARP 캐시에서 이전에 만든 고정 IP-물리적 주소 매핑을 찾아서 삭제합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 정적으로 매핑된 IP 주소입니다.
- **physical_msw** 정적으로 매핑된 물리적 주소의 상위 16비트(47-**32)입니다.
- **physical_lsw** 정적으로 매핑된 물리적 주소의 하위 32비트(31-**0)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP 고정 항목 삭제에 성공했습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) ARP 캐시에서 고정 ARP 항목을 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 잘못되었습니다.
- **NX_INVALID_PARAMETERS**(0x4D) Physical_msw 및 physical_lsw는 둘 다 0입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Delete a static ARP entry on the previously created IP
   instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
                                    0x0, 0x1234);

/* If status is NX_SUCCESS, the previously created static ARP entry
   was successfully deleted. */
```
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_icmp_enable"></a>nx_icmp_enable
ICMP(Internet Control Message Protocol) 사용

### <a name="prototype"></a>프로토타입  

```c
UINT nx_icmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 ICMP 구성 요소를 사용하도록 설정합니다. ICMP 구성 요소는 인터넷 오류 메시지와 ping 요청 및 회신을 처리해야 합니다. 

> [!IMPORTANT]  
> 이 서비스는 IPv4용 ICMP 서비스만 사용하도록 설정합니다. ICMPv4와 ICMPv6를 모두 사용하도록 설정하려면 애플리케이션에서 **nxd_icmp_enable** 서비스를 사용해야 합니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) ICMP를 사용하도록 설정하는 데 성공했습니다.
- **NX_ALREADY_ENABLED**(0x15) ICMP는 이미 사용하도록 설정되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```
### <a name="see-also"></a>참고 항목

- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_icmp_info_get"></a>nx_icmp_info_get
ICMP 활동에 대한 정보 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 ICMP 활동에 대한 정보를 검색합니다.

> [!NOTE]  
> 대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **pings_sent** 송신된 총 ping 수 대상을 가리키는 포인터입니다.
- **ping_timeouts** 총 ping 시간 제한 수 대상을 가리키는 포인터입니다.
- **ping_threads_suspended** ping 요청에서 일시 중단된 총 스레드 수 대상을 가리키는 포인터입니다.
- **ping_responses_received** 수신된 총 ping 응답 수 대상을 가리키는 포인터입니다.
- **icmp_checksum_errors** 총 ICMP 체크섬 오류 수 대상을 가리키는 포인터입니다.
- **icmp_unhandled_messages** 처리되지 않은 총 ICMP 메시지 수 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ICMP 정보 검색에 성공했습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Retrieve ICMP information from previously created IP
   instance ip_0. */
status = nx_icmp_info_get(&ip_0, &pings_sent, &ping_timeouts,
                          &ping_threads_suspended,
                          &ping_responses_received,
                          &icmp_checksum_errors,
                          &icmp_unhandled_messages);
/* If status is NX_SUCCESS, ICMP information was retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_icmp_enable
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_icmp_ping"></a>nx_icmp_ping  
지정된 IP 주소로 ping 요청 송신

### <a name="prototype"></a>프로토타입  

```c
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 주소로 ping 요청을 송신하고 지정된 시간 동안 ping 응답 메시지를 기다립니다. 응답이 수신되지 않는 경우 오류가 반환됩니다. 응답이 수신되는 경우 response_ptr이 가리키는 변수에 전체 응답 메시지가 반환됩니다. 

IPv6 대상에 ping 요청을 보내기 위해 애플리케이션은 ***nxd_icmp_ping** _ 또는 _ _nxd_icmp_source_ping_* 서비스를 사용해야 합니다.

> [!WARNING]  
> NX_SUCCESS가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 이 패킷을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** ping할 IP 주소입니다(호스트 바이트 순서).
- **data** ping 메시지의 데이터 영역에 대한 데이터 포인터입니다.
- **data_size** ping 데이터의 바이트 수입니다.
- **response_ptr** ping 응답 메시지를 반환하는 패킷 포인터를 가리키는 포인터입니다.
- **wait_option** ping 응답을 대기할 ThreadX 타이머 틱 수를 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.

| 대기 옵션            | 값                           |
| -----------------------|---------------------------------|
| NX_NO_WAIT             | (0x00000000)                    |
| 시간 제한 값(틱) | (0x00000001~0xFFFFFFFE) |
| NX_WAIT_FOREVER        | 0xFFFFFFFF                      |

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) ping에 성공했습니다. response_ptr이 가리키는 변수에 응답 메시지 포인터가 배치되었습니다.
- **NX_NO_PACKET**(0x01) ping 요청 패킷을 할당할 수 없습니다.
- **NX_OVERFLOW**(0x03) 지정된 데이터 영역은 이 IP 인스턴스의 기본 패킷 크기를 초과합니다.
- **NX_NO_RESPONSE**(0x29) 요청된 IP에서 응답하지 않았습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 응답 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
   Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
                      &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
   address 1.2.3.5 and the response packet is contained in the
   packet pointed to by response_ptr. It should have the same "abcd"
   four bytes of data. */
```
### <a name="see-also"></a>참고 항목

- nx_icmp_enable
- nx_icmp_info_get
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_igmp_enable"></a>nx_igmp_enable
IGMP(Internet Group Management Protocol) 사용

### <a name="prototype"></a>프로토타입  

```c
UINT nx_igmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스에서 IGMP 구성 요소를 사용하도록 설정합니다. IGMP 구성 요소는 IP 멀티캐스트 그룹 관리 작업에 대한 지원을 제공해야 합니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IGMP를 사용하도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_ALREADY_ENABLED**(0x15) 이 구성 요소는 이미 사용하도록 설정되어 있습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```
### <a name="see-also"></a>참고 항목

- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_info_get"></a>nx_igmp_info_get
ARP 활동에 대한 정보 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 IGMP 활동에 대한 정보를 검색합니다.

> [!IMPORTANT]  
> 대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **igmp_reports_sent** 송신된 총 ICMP 보고서 수 대상을 가리키는 포인터입니다.
- **igmp_queries_received** 멀티캐스트 라우터에 수신된 총 쿼리 수 대상을 가리키는 포인터입니다.
- **igmp_checksum_errors** 수신 패킷의 총 IGMP 체크섬 오류 수 대상을 가리키는 포인터입니다.
- **current_groups_joined** 이 IP 인스턴스를 통해 조인된 현재 그룹 수 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IGMP 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Retrieve IGMP information from previously created IP Instance ip_0. */
status = nx_igmp_info_get(&ip_0, &igmp_reports_sent,
                          &igmp_queries_received,
                          &igmp_checksum_errors,
                          &current_groups_joined);

/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a>참고 항목

- nx_igmp_enable
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable
IGMP 루프백 사용 안 함

### <a name="prototype"></a>프로토타입  

```c
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 조인된 모든 후속 멀티캐스트 그룹에 대해 IGMP 루프백을 사용하지 않도록 설정합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IGMP 루프백을 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_NOT_ENABLED**(0x14) IGMP가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Disable IGMP loopback for all subsequent multicast groups
   joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```
### <a name="see-also"></a>참고 항목

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable
IGMP 루프백 사용

### <a name="prototype"></a>프로토타입  

```c
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 조인된 모든 후속 멀티캐스트 그룹에 대해 IGMP 루프백을 사용하도록 설정합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IGMP 루프백을 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_NOT_ENABLED**(0x14) IGMP가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Enable IGMP loopback for all subsequent multicast
   groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```
### <a name="see-also"></a>참고 항목

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join
인터페이스를 통해 IP 인스턴스를 지정된 멀티캐스트 그룹에 조인

### <a name="prototype"></a>프로토타입  

```c
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Description

이 서비스는 지정된 네트워크 인터페이스를 통해 IP 인스턴스를 지정된 멀티캐스트 그룹에 조인합니다. 동일한 그룹이 조인된 횟수를 추적하도록 내부 카운터가 유지 관리됩니다. 멀티캐스트 그룹에 조인한 후에는 IGMP 구성 요소가 지정된 네트워크 인터페이스를 통해 이 그룹 주소를 사용하는 IP 패킷의 수신을 허용하며 이 IP가 이 멀티캐스트 그룹의 멤버임을 라우터에 보고합니다. IGMP 멤버 자격 조인, 보고, 탈퇴 메시지도 지정된 네트워크 인터페이스를 통해 송신됩니다. IGMP 그룹 멤버 자격 보고를 송신하지 않고 IPv4 멀티캐스트 그룹에 조인하려면 애플리케이션에서 서비스 ***nx_ipv4_multicast_interface_join*** 을 사용해야 합니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **group_address** 조인할 클래스 D IP 멀티캐스트 그룹 주소입니다(호스트 바이트 순서).
- **interface_index** NetX Duo 인스턴스에 연결된 인터페이스 인덱스입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 멀티캐스트 그룹 조인에 성공했습니다.
- **NX_NO_MORE_ENTRIES**(0x17) 멀티캐스트 그룹을 더 이상 조인할 수 없습니다. 최대값이 초과되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못된 네트워크 인터페이스를 가리킵니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 제공된 멀티캐스트 그룹 주소가 잘못된 클래스 D 주소입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) IP 멀티캐스트 지원이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Previously created IP Instance joins the multicast group
   244.0.0.200, via the interface at index 1 in the IP interface
   list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
                                 (&ip IP_ADDRESS(244,0,0,200),
                                  INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
   the multicast group. */
```   
### <a name="see-also"></a>참고 항목

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_interface_leave"></a>nx_igmp_multicast_interface_leave
인터페이스를 통해 지정된 멀티캐스트 그룹 탈퇴

### <a name="prototype"></a>프로토타입  

```c
UINT nx_igmp_multicast_interface_leave(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Description

이 서비스는 지정된 네트워크 인터페이스를 통해 지정된 멀티캐스트 그룹에서 탈퇴합니다. 동일한 그룹이 멤버로 포함된 횟수를 추적하도록 내부 카운터가 유지 관리됩니다. 멀티캐스트 그룹에서 탈퇴한 후에는 IGMP 구성 요소가 적절한 멤버 자격 보고를 보내고, 이 노드의 멤버가 없는 경우 그룹에서 탈퇴할 수 있습니다. IGMP 그룹 멤버 자격 보고를 송신하지 않고 IPv4 멀티캐스트 그룹에서 탈퇴하려면 애플리케이션에서 서비스 ***nx_ipv4_multicast_interface_leave*** 를 사용해야 합니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **group_address** 탈퇴할 클래스 D IP 멀티캐스트 그룹 주소입니다. IP 주소는 호스트 바이트 순서로 되어 있습니다.
- **interface_index** NetX Duo 인스턴스에 연결된 인터페이스 인덱스입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 멀티캐스트 그룹 조인에 성공했습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) 로컬 멀티캐스트 테이블에서 지정된 멀티캐스트 그룹 주소를 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못된 네트워크 인터페이스를 가리킵니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 제공된 멀티캐스트 그룹 주소가 잘못된 클래스 D 주소입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) IP 멀티캐스트 지원이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Leave the multicast group 244.0.0.200. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_leave
                                (&ip IP_ADDRESS(244,0,0,200),
                                 INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully leaves
   the multicast group 244.0.0.200. */
```
### <a name="see-also"></a>참고 항목

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join
IP 인스턴스를 지정된 멀티캐스트 그룹에 조인

### <a name="prototype"></a>프로토타입  

```c
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```
### <a name="description"></a>Description

이 서비스는 IP 인스턴스를 지정된 멀티캐스트 그룹에 조인합니다. 동일한 그룹이 조인된 횟수를 추적하도록 내부 카운터가 유지 관리됩니다. 호스트가 그룹을 조인하려는 것을 나타내는, 네트워크에서 송신된 첫 번째 조인 요청인 경우 드라이버에서 IGMP 보고서 송신 명령이 실행됩니다. 조인 후에는 IGMP 구성 요소가 이 그룹 주소를 사용하는 IP 패킷을 수신할 수 있으며 이 IP는 해당 멀티캐스트 그룹의 멤버임을 라우터에 보고합니다. IGMP 그룹 멤버 자격 보고를 송신하지 않고 IPv4 멀티캐스트 그룹에 조인하려면 애플리케이션에서 서비스 ***nx_ipv4_multicast_interface_join*** 을 사용해야 합니다.

> [!NOTE]  
> 기본 디바이스가 아닌 디바이스에서 멀티캐스트 그룹을 조인하려면 **nx_igmp_multicast_interface_join** 서비스를 사용합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **group_address** 조인할 클래스 D IP 멀티캐스트 그룹 주소입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 멀티캐스트 그룹 조인에 성공했습니다.
- **NX_NO_MORE_ENTRIES**(0x17) 멀티캐스트 그룹을 더 이상 조인할 수 없습니다. 최대값이 초과되었습니다.
- **NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못된 네트워크 인터페이스를 가리킵니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 그룹 주소입니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Previously created IP Instance ip_0 joins the multicast group
   224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully
   joined the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>참고 항목

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave
IP 인스턴스를 지정된 멀티캐스트 그룹에서 탈퇴

### <a name="prototype"></a>프로토타입  

```c
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```
### <a name="description"></a>Description

이 서비스를 사용하면 나가기 요청 수와 조인 요청 수가 일치하는 경우 IP 인스턴스가 지정된 멀티캐스트 그룹에서 나가도록 합니다. 일치하지 않으면 내부 조인 수만 감소합니다. IGMP 그룹 멤버 자격 보고를 송신하지 않고 IPv4 멀티캐스트 그룹에서 탈퇴하려면 애플리케이션에서 서비스 ***nx_ipv4_multicast_interface_leave*** 를 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **group_address** 탈퇴할 멀티캐스트 그룹입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 멀티캐스트 그룹 조인에 성공했습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) 이전 조인 요청을 찾을 수 없습니다.
- **NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못된 네트워크 인터페이스를 가리킵니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 그룹 주소입니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
   the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>참고 항목

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy
IP 주소가 변경되면 애플리케이션에 알림

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *, VOID *),
    VOID *additional_info);
```
### <a name="description"></a>Description

이 서비스는 IPv4 주소가 변경될 때마다 호출되는 애플리케이션 알림 함수를 등록합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **change_notify** IP 변경 알림 함수를 가리키는 포인터입니다. 이 매개 변수가 NX_NULL이면 IP 주소 변경 알림이 사용하지 않도록 설정됩니다.
- **additional_info** IP 주소가 변경되면 알림 함수에도 제공되는 선택적 추가 정보를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IP 주소 변경 알림에 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Register the function "my_ip_changed" to be called whenever the
   IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed,
                                      NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
   called whenever the IP address changes. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_address_get"></a>nx_ip_address_get
IPv4 주소 및 네트워크 마스크 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```
### <a name="description"></a>Description

이 서비스는 기본 네트워크 인터페이스의 IPv4 주소 및 해당 서브넷 마스크를 검색합니다.

> [!IMPORTANT]   
> *보조 디바이스의 정보를 가져오려면 **nx_ip_interface_address_get*** 서비스를 사용합니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** IP 주소 대상을 가리키는 포인터입니다.
- **network_mask** 네트워크 마스크 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) IP 주소 가져오기에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 반환 변수 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Get the IP address and network mask from the previously created
   IP Instance ip_0. */
status = nx_ip_address_get(&ip_0, &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
   network_mask contain the IP and network mask respectively. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_address_set"></a>nx_ip_address_set
IPv4 주소 및 네트워크 마스크 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```
### <a name="description"></a>Description

이 서비스는 기본 네트워크 인터페이스의 IPv4 주소 및 네트워크 마스크를 설정합니다.

> [!IMPORTANT]  
> *보조 디바이스의 IP 주소 및 네트워크 마스크를 설정하려면 **nx_ip_interface_address_set*** 서비스를 사용합니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 새 IP 주소입니다.
- **network_mask** 새 네트워크 마스크입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 주소 설정에 성공했습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00 for
   the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4),
                           0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address of
   1.2.3.4 and a network mask of 0xFFFFFF00. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_auxiliary_packet_pool_set"></a>nx_ip_auxiliary_packet_pool_set
보조 패킷 풀 구성

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_auxiliary_packet_pool_set(
    NX_IP *ip_ptr,
    NX_PACKET_POOL *aux_pool);
```
### <a name="description"></a>Description

이 서비스는 IP 인스턴스에서 보조 패킷 풀을 구성합니다. 메모리 제한 시스템의 경우 IP 스레드에서 더 작은 패킷을 전송할 수 있도록 하기 위해 사용자는 MTU의 패킷 크기로 기본 패킷 풀을 만들고, 더 작은 패킷 크비로 보조 패킷 풀을 만들어 메모리 효율성을 높일 수 있습니다. 보조 풀에 권장되는 패킷 크기는 256바이트이며, IPv6 및 IPsec을 모두 사용할 수 있다고 가정합니다.

기본적으로 IP 인스턴스는 보조 패킷 풀을 허용하지 않습니다. 이 기능을 사용하도록 설정하려면 NetX Duo 라이브러리를 컴파일할 때 NX_DUAL_PACKET_POOL_ENABLE을 정의해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **aux_pool** IP 인스턴스에 대해 구성할 보조 패킷 풀입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) IP 주소 설정에 성공했습니다.
- **NX_NOT_SUPPORTED**(0x4b) 라이브러리에서 이중 패킷 풀 기능이 컴파일되지 않습니다.
- **NX_PTR_ERROR**(0X07) IP 포인터나 풀 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점  

예

### <a name="example"></a>예제

```c
#define SMALL_PAYLOAD_SIZE 256
NX_PACKET small_pool;

nx_packet_pool_create(&small_pool, "small pool", SMALL_PAYLOAD_SIZE,
                       small_pool_memory_ptr, small_pool_size);

/* Add the small packet pool to the IP instance. */
status = nx_ip_auxiliary_packet_pool_set(&ip_0, &small_pool);

/* If status is NX_SUCCESS, the IP instance now is able to use the
   small pool for transmitting small datagram. */
```
### <a name="see-also"></a>참고 항목

- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_ip_create"></a>nx_ip_create
IP 인스턴스 만들기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```
### <a name="description"></a>Description

이 서비스는 사용자 제공 IP 주소 및 네트워크 드라이버를 사용하여 IP 인스턴스를 만듭니다. 또한 애플리케이션은 내부 패킷 할당에 사용할 IP 인스턴스에 대해 이전에 만든 패킷 풀을 제공해야 합니다. 제공된 애플리케이션 네트워크 드라이버는 이 IP의 스레드가 실행될 때까지 호출되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 새 IP 인스턴스를 만들 제어 블록을 가리키는 포인터입니다.
- **name** 새 IP 인스턴스의 이름입니다.
- **ip_address** 새 IP 인스턴스의 IP 주소입니다.
- **network_mask** 서브넷 및 슈퍼넷 지정에 사용할 IP 주소의 네트워크 부분을 나타내는 마스크입니다.
- **default_pool** 이전에 만든 NetX Duo 패킷 풀의 제어 블록을 가리키는 포인터입니다.
- **ip_network_driver** IP 패킷 송신 및 수신에 사용되는 사용자 제공 네트워크 드라이버입니다.
- **memory_ptr** IP 도우미 스레드 스택 영역의 메모리 영역을 가리키는 포인터입니다.
- **memory_size** IP 도우미 스레드 스택의 메모리 영역 바이트 수입니다.
- **priority** IP 도우미 스레드 우선 순위입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IP 인스턴스 만들기에 성공했습니다.
- **NX_NOT_IMPLEMENTED**(0x4A) NetX Duo 라이브러리가 잘못 구성되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP, 네트워크 드라이버 함수 포인터, 패킷 풀 또는 메모리 포인터입니다.
- **NX_SIZE_ERROR**(0x09) 제공된 스택 크기가 너무 작습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 제공된 IP 주소가 잘못되었습니다.
- **NX_OPTION_ERROR**(0x21) 제공된 IP 스레드 우선 순위가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Create an IP instance with an IP address of 1.2.3.4 and a network
   mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
   point of the application specific network driver and the
   "stack_memory_ptr" specifies the start of a 1024 byte memory
   area that is used for this IP instance’s helper thread. */
status = nx_ip_create(&ip_0, "NetX IP Instance ip_0",
                      IP_ADDRESS(1, 2, 3, 4),
                      0xFFFFFF00UL, &pool_0, ethernet_driver,
                      stack_memory_ptr, 1024, 1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_delete"></a>nx_ip_delete
이전에 만든 IP 인스턴스 삭제

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_delete(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 이전에 만든 IP 인스턴스를 삭제하고 IP 인스턴스가 소유하는 모든 시스템 리소스를 해제합니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 삭제에 성공했습니다.
- **NX_SOCKETS_BOUND**(0x28) 이 IP 인스턴스는 여전히 UDP 또는 TCP 소켓과 바인딩되어 있습니다. IP 인스턴스를 삭제하려면 먼저 모든 소켓을 바인딩 해제하고 삭제해야 합니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>참고 항목 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command
네트워크 드라이버에 대해 명령 실행

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_driver_direct_command
    (NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```
### <a name="description"></a>Description

이 서비스는 ***nx_ip_create*** 호출 중 지정된 애플리케이션의 기본 네트워크 인터페이스 드라이버에 대해 직접 인터페이스를 제공합니다. 애플리케이션별 명령을 사용하면 NX_LINK_USER_COMMAND 이상의 숫자 값을 제공할 수 있습니다.

> [!IMPORTANT]  
> 보조 디바이스에 대해 명령을 실행하려면 **nx_ip_driver_interface_direct_command** 서비스를 사용합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **command** 숫자 명령 코드입니다. 표준 명령은 다음과 같이 정의됩니다.
    - NX_LINK_GET_STATUS(10)
    - NX_LINK_GET_SPEED(11)
    - NX_LINK_GET_DUPLEX_TYPE(12)
    - NX_LINK_GET_ERROR_COUNT(13)
    - NX_LINK_GET_RX_COUNT(14)
    - NX_LINK_GET_TX_COUNT(15)
    - NX_LINK_GET_ALLOC_ERRORS(16)
    - NX_LINK_USER_COMMAND(50)
- **return_value_ptr** 호출자의 반환 변수를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 네트워크 드라이버 직접 명령이 성공했습니다.
- **NX_UNHANDLED_COMMAND**(0x44) 처리되지 않거나 구현되지 않은 네트워크 드라이버 명령입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 반환 값 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_INVALID_INTERFACE**(0x4C) 잘못된 인터페이스 인덱스입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Make a direct call to the application-specific network driver
   for the previously created IP instance. For this example, the
   network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(&ip_0, NX_LINK_GET_STATUS,
                                     &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
   NX_TRUE or NX_FALSE value representing the status of the
   physical link. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command
네트워크 드라이버에 대해 명령 실행

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```
### <a name="description"></a>Description

이 서비스는 IP 인스턴스의 애플리케이션 네트워크 디바이스 드라이버에 대해 직접 명령을 제공합니다. 애플리케이션별 명령을 사용하면 *NX_LINK_USER_COMMAND* 이상의 숫자 값을 제공할 수 있습니다.

### <a name="parameters"></a>매개 변수  

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **command** 숫자 명령 코드입니다. 표준 명령은 다음과 같이 정의됩니다.
    - NX_LINK_GET_STATUS(10)
    - NX_LINK_GET_SPEED(11)
    - NX_LINK_GET_DUPLEX_TYPE(12)
    - NX_LINK_GET_ERROR_COUNT(13)
    - NX_LINK_GET_RX_COUNT(14)
    - NX_LINK_GET_TX_COUNT(15)
    - NX_LINK_GET_ALLOC_ERRORS(16)
    - NX_LINK_USER_COMMAND(50)
- **interface_index** 명령을 송신해야 하는 대상 네트워크 인터페이스 인덱스입니다.
- **return_value_ptr** 호출자의 반환 변수를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 네트워크 드라이버 직접 명령이 성공했습니다.
- **NX_UNHANDLED_COMMAND**(0x44) 처리되지 않거나 구현되지 않은 네트워크 드라이버 명령입니다.
- **NX_INVALID_INTERFACE**(0x4C) 잘못된 인터페이스 인덱스입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 반환 값 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Make a direct call to the application-specific network driver
   for the previously created IP instance. For this example, the
   network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;

status = nx_ip_driver_interface_direct_command(&ip_0,
                                               NX_LINK_GET_STATUS,
                                               interface_index,
                                               &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
   NX_TRUE or NX_FALSE value representing the status of the
   physical link. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable  
IP 전달을 사용하지 않도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 NetX Duo IP 구성 요소 내부에서 IP 패킷 전달을 사용하지 않도록 설정합니다. IP 작업을 만들 때 이 서비스는 자동으로 사용하지 않도록 설정됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) IP 전달을 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점  

예

### <a name="example"></a>예제

```c
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>참고 항목  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable
IP 패킷 전달 사용하도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 NetX Duo IP 구성 요소 내부에서 IP 패킷 전달을 사용하도록 설정합니다. IP 작업을 만들 때 이 서비스는 자동으로 사용하지 않도록 설정됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IP 전달을 사용하도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>참고 항목 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable
IP 패킷 조각화를 사용하지 않도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 IPv4 및 nd IPv6 패킷 조각화 및 리어셈블 기능을 사용하지 않도록 설정합니다. 이 서비스는 리어셈블 대기 중인 패킷이 있는 경우 해당 패킷을 해제합니다. IP 작업을 만들 때 이 서비스는 자동으로 사용하지 않도록 설정됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IP 조각화를 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) IP 인스턴스에서 IP 조각화가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
   previously created IP instance. */
```

### <a name="see-also"></a>참고 항목  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable
IP 패킷 조각화를 사용하도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 IPv4 및 IPv6 패킷 조각화 및 리어셈블 기능을 사용하도록 설정합니다. IP 작업을 만들 때 이 서비스는 자동으로 사용하지 않도록 설정됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IP 조각화를 사용하도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) NetX Duo에 IP 조각화 기능이 컴파일되어 있지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>참고 항목  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_gateway_address_clear"></a>nx_ip_gateway_address_clear
IPv4 게이트웨이 주소 지우기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_gateway_address_clear(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 인스턴스에 구성된 IPv4 게이트웨이 주소를 지웁니다. IP 인스턴스에서 IPv6 기본 라우터를 지우려면 애플리케이션은 ***nxd_ipv6_default_router_delete*** 서비스를 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 제어 블록 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IP 게이트웨이 주소를 지웠습니다.
- **NX_PTR_ERROR**(0X07) 잘못된 IP 제어 블록입니다.
- **NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Clear the gateway address of IP instance. */
status = nx_ip_gateway_address_clear(&ip_0);

/* If status == NX_SUCCESS, the gateway address was successfully
   cleared from the IP instance. */
```
### <a name="see-also"></a>참고 항목

-nx_ip_gateway_address_get -nx_ip_gateway_address_set -nx_ip_info_get -nx_ip_static_route_add -nx_ip_static_route_delete -nxd_ipv6_default_router_add -nxd_ipv6_default_router_delete -nxd_ipv6_default_router_entry_get -nxd_ipv6_default_router_get -nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_gateway_address_get"></a>nx_ip_gateway_address_get
IPv4 게이트웨이 주소 가져오기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_gateway_address_get(
    NX_IP *ip_ptr, 
    ULONG *ip_address);
```
### <a name="description"></a>Description

이 서비스는 IP 인스턴스에 구성된 IPv4 게이트웨이 주소를 검색합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 제어 블록 포인터입니다.
- **ip_address** 게이트웨이 주소가 저장된 메모리에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 가져오는 데 성공했습니다. 
- **NX_PTR_ERROR**(0x07) 잘못된 IP 제어 블록 포인터 또는 IP 주소 포인터입니다.
- **NX_NOT_FOUND**(0x4E) 게이트웨이 주소를 찾을 수 없습니다.
- **NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
ULONG ip_address;

/* Get the gateway address of IP instance. */
status = nx_ip_gateway_address_get(&ip_0, &ip_address);

/* If status == NX_SUCCESS, the gateway address was successfully
   got. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set
게이트웨이 IP 주소 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```
### <a name="description"></a>Description

이 서비스는 IPv4 게이트웨이 IP 주소를 설정합니다. 전송을 위한 네트워크 외부 트래픽은 모두 이 게이트웨이로 라우트됩니다. 게이트웨이는 네트워크 인터페이스 중 하나를 통해 직접 액세스할 수 있어야 합니다. IPv6 게이트웨이 주소를 구성하려면 ***nxd_ipv6_default_router_add*** 서비스를 사용합니다. 

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 게이트웨이 IP 주소입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 게이트웨이 IP 주소 설정에 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 인스턴스 포인터가 잘못되었습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Setup the Gateway address for previously created IP
   Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99);

/* If status is NX_SUCCESS, all out-of-network send requests are
   routed to 1.2.3.99. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_info_get"></a>nx_ip_info_get
IP 활동에 대한 정보 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 IP 활동에 대한 정보를 검색합니다.

> [!NOTE]  
> 대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_total_packets_sent** 송신된 총 IP 패킷 수 대상을 가리키는 포인터입니다.
- **ip_total_bytes_sent** 송신된 총 바이트 수 대상을 가리키는 포인터입니다.
- **ip_total_packets_received** 총 IP 수신 패킷 수 대상을 가리키는 포인터입니다.
- **ip_total_bytes_received** 수신된 총 IP 바이트 수 대상을 가리키는 포인터입니다.
- **ip_invalid_packets** 잘못된 총 IP 패킷 수 대상을 가리키는 포인터입니다.
- **ip_receive_packets_dropped** 삭제된 총 수신 패킷 수 대상을 가리키는 포인터입니다.
- **ip_receive_checksum_errors** 수신 패킷의 총 체크섬 오류 수 대상을 가리키는 포인터입니다.
- **ip_send_packets_dropped** 삭제된 총 송신 패킷 수 대상을 가리키는 포인터입니다.
- **ip_total_fragments_sent** 송신된 총 조각 수 대상을 가리키는 포인터입니다.
- **ip_total_fragments_received** 수신된 총 조각 수 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IP 정보 검색에 성공했습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Retrieve IP information from previously created IP
   Instance 0. */
status = nx_ip_info_get(&ip_0,
                        &ip_total_packets_sent,
                        &ip_total_bytes_sent,
                        &ip_total_packets_received,
                        &ip_total_bytes_received,
                        &ip_invalid_packets,
                        &ip_receive_packets_dropped,
                        &ip_receive_checksum_errors,
                        &ip_send_packets_dropped,
                        &ip_total_fragments_sent,
                        &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get
인터페이스 IP 주소 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```
### <a name="description"></a>Description

이 서비스는 지정된 네트워크 인터페이스의 IPv4 주소를 검색합니다. IPv6 주소를 검색하려면 애플리케이션에서 ***nxd_ipv6_address_get*** 서비스를 사용해야 합니다.

> [!CAUTION]  
> 기본 디바이스가 아닌 경우 지정된 디바이스가 이전에 이미 IP 인스턴스에 연결되어 있어야 합니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **interface_index** 인터페이스 인덱스로, IP 인스턴스에 연결된 네트워크 인터페이스의 인덱스와 값이 동일합니다.
- **ip_address** 디바이스 인터페이스 IP 주소 대상을 가리키는 포인터입니다.
- **network_mask** 디바이스 인터페이스 네트워크 마스크 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 주소 가져오기에 성공했습니다.
- **NX_INVALID_INTERFACE**(0x4C) 지정된 네트워크 인터페이스가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define INTERFACE_INDEX 1

/* Get device IP address and network mask for the specified
   interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
                                     &ip_address,
                                     &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
   retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_mapping_configure"></a>nx_ip_interface_address_mapping_configure
주소 매핑이 필요한지 여부 구성

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_interface_address_mapping_configure(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT mapping_needed);
```
### <a name="description"></a>Description

이 서비스는 지정된 네트워크 인터페이스에 대해 IP 주소-MAC 주소 매핑에 필요한지 여부를 구성합니다. 일반적으로 이 서비스는 기본 인터페이스에 IP 주소-계층 2(MAC) 주소 매핑이 필요한지 여부를 IP 스택에 알리기 위해 인터페이스 디바이스 드라이버에서 호출됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 제어 블록 포인터입니다.
- **interface_index** 네트워크 인터페이스에 대한 인덱스입니다.
- **mapping_needed** NX_TRUE(주소 매핑이 필요함), NX_FALSE(주소 매핑이 필요하지 않음)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 성공적으로 구성했습니다.
- **NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못되었습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define PRIMARY_INTERFACE 0
UCHAR mapping_needed = NX_TRUE;

/* Configure address mapping needed specified interface. */
status = nx_ip_interface_address_mapping_configure(&ip_0,
                                             PRIMARY_INTERFACE,
                                             mapping_needed);

/* If status == NX_SUCCESS, the address mapping needed was
   successfully configured. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set
인터페이스 IP 주소 및 네트워크 마스크 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인터페이스의 IPv4 주소 및 네트워크 마스크를 설정합니다. IPv6 인터페이스 주소를 구성하기 위해 애플리케이션은 ***nxd_ipv6_address_set*** 서비스를 사용해야 합니다. 
 
> [!WARNING]  
> 지정된 인터페이스가 이전에 이미 IP 인스턴스에 연결되어 있어야 합니다. 

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **interface_index** NetX Duo 인스턴스에 연결된 인터페이스 인덱스입니다.
- **ip_address** 새 네트워크 인터페이스 IP 주소입니다.
- **network_mask** 새 인터페이스 네트워크 마스크입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 주소 설정에 성공했습니다.
- **NX_INVALID_INTERFACE**(0x4C) 지정된 네트워크 인터페이스가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define INTERFACE_INDEX 1

/* Set device IP address and network mask for the specified
   interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
                                     ip_address,
                                     network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
   successfully set. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach
IP 인스턴스에 네트워크 인터페이스 연결

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)(struct NX_IP_DRIVER_STRUCT *));
```
### <a name="description"></a>Description

이 서비스는 IP 인터페이스에 실제 네트워크 인터페이스를 추가합니다. IP 인스턴스는 기본 인터페이스를 사용하여 만들어지므로 각각의 추가 인터페이스는 기본 인터페이스에 대한 보조 인스턴스가 됩니다. IP 인스턴스에 연결된 총 네트워크 인터페이스 수(기본 인터페이스 포함)는 **NX_MAX_PHYSICAL_INTERFACES** 를 초과할 수 없습니다.

IP 스레드가 아직 실행되지 않은 경우 모든 실제 인터페이스를 초기화하는 IP 스레드 시작 프로세스의 일부로 보조 인터페이스가 초기화됩니다.

IP 스레드가 아직 실행되고 있지 않으면 보조 인터페이스가 ***nx_ip_interface_attach*** 서비스의 일부로 초기화됩니다.

> [!WARNING]  
> ip_ptr은 유효한 NetX Duo IP 구조를 가리켜야 합니다. IP 인스턴스의 네트워크 인터페이스 수에 대해 **NX_MAX_PHYSICAL_INTERFACES** 를 구성해야 합니다. 기본값은 1입니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **interface_name** 인터페이스 이름 문자열을 가리키는 포인터입니다.
- **ip_address** 디바이스 IP 주소입니다(호스트 바이트 순서).
- **network_mask** 디바이스 네트워크 마스크입니다(호스트 바이트 순서).
- **ip_link_driver** 인터페이스 이더넷 드라이버입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 항목이 고정 라우팅 테이블에 추가됩니다.
- **NX_NO_MORE_ENTRIES**(0x17) 최대 인터페이스 수입니다. NX_MAX_PHYSICAL_INTERFACES를 초과했습니다. IPv6를 사용하도록 설정하는 경우 이 오류는 드라이버에 IPv6 멀티캐스트 작업을 처리할 수 있을만큼 충분한 리소스가 없을 수도 있음을 나타낼 수도 있습니다.
- **NX_DUPLICATED_ENTRY**(0x52) 제공된 IP 주소는 이 IP 인스턴스에서 이미 사용되고 있습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터 입력입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소 입력입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Attach secondary device for device IP address 192.168.1.68 with
   the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
                                IP_ADDRESS(192,168,1,68),
                                0xFFFFFF00UL,
                                nx_etherDriver);

/* If status is NX_SUCCESS the interface was successfully added to
   the IP instance interface table. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_capability_get"></a>nx_ip_interface_capability_get
인터페이스 하드웨어 기능 가져오기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_interface_capability_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *interface_capability_flag);
```
### <a name="description"></a>Description

이 서비스는 지정된 네트워크 인터페이스에서 기능 플래그를 검색합니다. 이 서비스를 사용하려면 ***NX_ENABLE_INTERFACE_CAPABILITY*** 옵션을 사용하도록 설정한 상태로 Netx Duo 라이브러리를 빌드해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 제어 블록 포인터입니다.
- **interface_index** 네트워크 인터페이스에 대한 인덱스입니다.
- **interface_capability_flag** 기능 플래그의 메모리 공간을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 인터페이스 기능 정보를 가져왔습니다.
- **NX_NOT_SUPPORTED**(0x4B) 이 빌드에서는 인터페이스 기능이 지원되지 않습니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스 인덱스가 잘못되었습니다.
- **NX_PTR_ERROR**(0X07) 잘못된 IP 제어 블록 포인터 또는 잘못된 기능 플래그 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define PRIMARY_INTERFACE 0
ULONG       capability_flag;

/* Get the hardware capability flag of specified interface. */
status = nx_ip_interface_capability_get(&ip_0,
                                        PRIMARY_INTERFACE,
                                        &capability_flag);

/* If status == NX_SUCCESS, the capability flag from the primary
   interface was successfully retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_capability_set"></a>nx_ip_interface_capability_set
하드웨어 기능 플래그 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_interface_capability_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG interface_capability_flag);
```                           
### <a name="description"></a>Description

이 서비스는 네트워크 디바이스 드라이버에서 지정된 네트워크 인터페이스에 대해 기능 플래그를 구성하는 데 사용합니다. 이 서비스를 사용하려면 ***NX_ENABLE_INTERFACE_CAPABILITY*** 옵션을 정의한 상태로 Netx Duo 라이브러리를 컴파일해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 제어 블록 포인터입니다.
- **interface_index** 네트워크 인터페이스에 대한 인덱스입니다.
- **interface_capability_flag** 출력에 대한 기능 플래그입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 인터페이스 하드웨어 기능 플래그를 설정했습니다.
- **NX_NOT_SUPPORTED**(0x4B) 이 빌드에서는 인터페이스 기능이 지원되지 않습니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스 인덱스가 잘못되었습니다. 
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다. 
- **NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define PRIMARY_INTERFACE 0
ULONG capability_flag = \
                 NX_INTERFACE_CAPABILITY_IPV4_TX_CHECKSUM |\
                 NX_INTERFACE_CAPABILITY_IPV4_RX_CHECKSUM;
UINT device_index = 0;

/* Set the hardware capability flag of specified interface. */
status = nx_ip_interface_capability_set(&ip_0,
                                        PRIMARY_INTERFACE,
                                        capability_flag);

/* If status == NX_SUCCESS, the hardware capability flag was
   successfully set. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_detach"></a>nx_ip_interface_detach
IP 인스턴스에서 지정된 인터페이스 분리

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr, 
    UINT index);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인터페이스를 IP 인스턴스에서 분리합니다. 인터페이스가 분리되면 연결된 모든 TCP 소켓이 닫히고, 이 인터페이스에 대한 ND 캐시 및 ARP 항목이 해당 테이블에서 제거됩니다. 이 인터페이스에 대한 IGMP 멤버 자격이 제거됩니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **index** 제거할 인터페이스의 인덱스입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 실제 인터페이스를 제거했습니다.
- **NX_INVALID_INTERFACE**(0x4C) 지정된 네트워크 인터페이스가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define INTERFACE_INDEX 1

/* Detach interface 1. */
status = nx_ip_interface_detach(&IP_0, INTERFACE_INDEX);

/* If status is NX_SUCCESS the interface is successfully detached
   from the IP instance. */
```

### <a name="see-also"></a>참고 항목  

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get
네트워크 인터페이스 매개 변수 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```
### <a name="description"></a>Description

이 서비스는 지정된 네트워크 인터페이스의 네트워크 매개 변수에 대한 정보를 검색합니다. 모든 데이터는 호스트 바이트 순서대로 검색됩니다. 

> [!WARNING]  
> ip_ptr은 유효한 NetX Duo IP 구조를 가리켜야 합니다. 기본 인터페이스가 아닌 경우 지정된 인터페이스가 이전에 이미 IP 인스턴스에 연결되어 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **interface_index** 네트워크 인터페이스를 지정하는 인덱스입니다.
- **interface_name** 네트워크 인터페이스 이름이 포함된 버퍼를 가리키는 포인터입니다.
- **ip_address** 인터페이스 IP 주소 대상을 가리키는 포인터입니다.
- **network_mask** 네트워크 마스크 대상을 가리키는 포인터입니다.
- **mtu_size** 이 인터페이스의 최대 전송 단위 대상을 가리키는 포인터입니다.
- **physical_address_msw** 디바이스 MAC 주소의 상위 16비트 대상을 가리키는 포인터입니다.
- **physical_address_lsw** 디바이스 MAC 주소의 하위 32비트 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값   

- **NX_SUCCESS**(0x00) 인터페이스 정보를 가져왔습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터 입력입니다.
- **NX_INVALID_INTERFACE**(0x4C) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Retrieve interface parameters for the specified interface (index
   1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1
status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
                                  &name_ptr, &ip_address,
                                  &network_mask,
                                  &mtu_size,
                                  &physical_address_msw,
                                  &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
   successfully retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_mtu_set"></a>nx_ip_interface_mtu_set
네트워크 인터페이스의 MTU 값 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_interface_mtu_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG mtu_size);
```
### <a name="description"></a>Description

이 서비스는 디바이스 드라이버에서 지정된 네트워크 인터페이스에 대한 IP MTU 값을 구성하는 데 사용합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 제어 블록 포인터입니다.
- **interface_index** 네트워크 인터페이스에 대한 인덱스입니다.
- **mtu_size** IP MTU 크기입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) MTU 값을 설정했습니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스 인덱스가 잘못되었습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define PRIMARY_INTERFACE 0
ULONG       mtu_size = 1500;

/* Set the MTU size of specified interface. */
status = nx_ip_interface_mtu_set(&ip_0,
                                 PRIMARY_INTERFACE, mtu_size);

/* If status == NX_SUCCESS, the MTU size was successfully set. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_physical_address_get"></a>nx_ip_interface_physical_address_get
네트워크 디바이스의 실제 주소 가져오기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_interface_physical_address_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *physical_msw,
    ULONG *physical_lsw);
```
### <a name="description"></a>Description

이 서비스는 IP 인스턴스에서 네트워크 인터페이스의 실제 주소를 검색합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 제어 블록 포인터입니다.
- **interface_index** 네트워크 인터페이스에 대한 인덱스입니다.
- **physical_msw** 디바이스 MAC 주소의 상위 16비트 대상을 가리키는 포인터입니다.
- **physical_lsw** 디바이스 MAC 주소의 하위 32비트 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 가져오는 데 성공했습니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스 인덱스가 잘못되었습니다.
- **NX_PTR_ERROR** (0x07) 잘못된 IP 제어 블록 포인터 또는 물리적 주소 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define PRIMARY_INTERFACE 0
ULONG   physical_msw;
ULONG   physical_lsw;

/* Get the physical address of specified interface. */
status = nx_ip_interface_physical_address_get(&ip_0,
                                              PRIMARY_INTERFACE,
                                              &physical_msw,
                                              &physical_lsw);

/* If status == NX_SUCCESS, the physical address was successfully
   retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_physical_address_set"></a>nx_ip_interface_physical_address_set
지정된 네트워크 인터페이스에 대한 실제 주소를 설정합니다.

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_interface_physical_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG physical_msw,
    ULONG physical_lsw,
    UINT update_driver);
```
### <a name="description"></a>Description

이 서비스는 애플리케이션 또는 디바이스 드라이버에서 지정된 네트워크 인터페이스의 MAC 주소에 대해 실제 주소를 구성하는 데 사용합니다. 새 MAC 주소는 인터페이스 구조의 제어 블록에 적용됩니다. ***update_driver*** 플래그를 설정하면 드라이버 수준 명령이 실행되어 디바이스 드라이버가 이더넷 컨트롤러로 프로그래밍된 MAC 주소를 업데이트할 수 있습니다.

일반적인 상황에서 이 서비스는 초기화 단계 동안 인터페이스 디바이스 드라이버에서 호출되어 해당 MAC 주소를 IP 스택에 알립니다. 이 경우에는 ***update_driver*** 플래그를 설정하면 안 됩니다.

사용자 애플리케이션에서 이 루틴을 호출하여 런타임에 인터페이스 MAC 주소를 다시 구성할 수도 있습니다. 이 사용 사례에서는 새 MAC 주소를 디바이스 드라이버에 적용할 수 있도록 ***update_driver*** 플래그를 설정해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 제어 블록 포인터입니다.
- **interface_index** 네트워크 인터페이스에 대한 인덱스입니다.
- **physical_msw** 디바이스 MAC 주소의 상위 16비트 대상을 가리키는 포인터입니다.
- **physical_lsw** 디바이스 MAC 주소의 하위 32비트 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 설정하는 데 성공했습니다.
- **NX_UNHANDLED_COMMAND**(0x4B) 드라이버가 인식할 수 없는 명령입니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스 인덱스가 잘못되었습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define PRIMARY_INTERFACE 0
ULONG       physical_msw = 0x00CF;
ULONG       physical_lsw = 0x01020304;

/* Set the physical address of specified device. */
status = nx_ip_interface_physical_address_set(&ip_0,
                                              PRIMARY_INTERFACE,
                                              physical_msw,
                                              physical_lsw,
                                              NX_TRUE);

/* If status == NX_SUCCESS, the physical address was successfully
   set. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check
IP 인스턴스의 상태 확인

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 이전에 만든 IP 인스턴스의 네트워크 인터페이스 상태를 확인하고 선택적으로 지정된 상태가 될 때까지 대기합니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **interface_index** 다음과 같이 비트 맵 형식으로 정의된 요청된 인터페이스 인덱스 번호 needed_status IP 상태입니다.
  - **NX_IP_INITIALIZE_DONE**(0x0001)
  - **NX_IP_ADDRESS_RESOLVED**(0x0002)
  - **NX_IP_LINK_ENABLED**(0x0004)
  - **NX_IP_ARP_ENABLED**(0x0008)
  - **NX_IP_UDP_ENABLED**(0x0010)
  - **NX_IP_TCP_ENABLED**(0x0020)
  - **NX_IP_IGMP_ENABLED**(0x0040)
  - **NX_IP_RARP_COMPLETE**(0x0080)
  - **NX_IP_INTERFACE_LINK_ENABLED**(0x0100)
- **actual_status** 설정된 실제 비트 대상을 가리키는 포인터입니다. wait_option 요청된 상태 비트를 사용할 수 없는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **NX_NO_WAIT**(0x00000000)
  - **시간 제한 값**(0x00000001~0xFFFFFFFE)
  - **NX_WAIT_FOREVER** 0xFFFFFFFF

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 상태 확인에 성공했습니다.
- **NX_NOT_SUCCESSFUL**(0x43) 지정된 시간 제한 내에 상태 요청이 충족되지 않았습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었거나 잘못된 상태였거나, 실제 상태 포인터가 잘못되었습니다.
- **NX_OPTION_ERROR**(0x0a) 필요한 상태 옵션이 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_INVALID_INTERFACE**(0x4C) Interface_index가 범위를 벗어났습니다. 또는 인터페이스가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Wait 10 ticks for the link up status on the previously created IP
   instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
                                      &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
   instance is up. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set
링크 상태 변경 알림 콜백 함수 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID(*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```
### <a name="description"></a>Description

이 서비스는 링크 상태 변경 알림 콜백 함수를 구성합니다. 기본 또는 보조 인터페이스 상태가 변경되는 경우(예: IP 주소가 변경되는 경우) 사용자 제공 link_status_change_notify 루틴이 호출됩니다. link_status_change_notify가 NULL인 경우 링크 상태 변경 알림 콜백 기능이 사용하지 않도록 설정됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 제어 블록 포인터입니다.
- **link_status_change_notify** 실제 인터페이스 변경 시 호출되는 사용자 제공 콜백 함수입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 제어 블록 포인터 또는 새 물리적 주소 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Configure a callback function to be used when the physical
   interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0,
                                             my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
   is set. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check

## <a name="nx_ip_max_payload_size_find"></a>nx_ip_max_payload_size_find
최대 패킷 데이터 페이로드 계산

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_max_payload_size_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *dest_address,
    UINT if_index,
    UINT src_port,
    UINT dest_port,
    ULONG protocol,
    ULONG *start_offset_ptr,
    ULONG *payload_length_ptr);
```
### <a name="description"></a>Description

이 서비스는 대상에 도달하기 위해 IP 조각화가 필요하지 않은 최대 애플리케이션 페이로드 크기를 찾습니다. 예를 들어, 로컬 인터페이스 MTU 크기와 같거나 낮을 수 있습니다. (또는 IPv6 경로 MTU 검색을 통해 얻은 경로 MTU 값) IP 헤더 및 상위 애플리케이션 헤더 크기(TCP 또는 UDP)를 총 페이로드에서 뺍니다. NetX Duo IPsec 보안 정책이 이 엔드포인트에 적용되는 경우 IPsec 헤더(ESP/AH) 및 관련 오버헤드(예: 초기 벡터)도 MTU에서 뺍니다. 이 서비스는 IPv4 및 IPv6 패킷 모두에 적용됩니다.

매개 변수 *if_index* 는 패킷을 보내는 데 사용할 인터페이스를 지정합니다. 멀티홈 시스템의 경우 대상이 브로드캐스트(IPv4 전용), 멀티캐스트 또는 IPv6 링크-로컬 주소인 경우 호출자는 *if_index* 매개 변수를 지정해야 합니다.

이 서비스는 호출자에게 다음 두 값을 반환합니다.

1) start_offset_ptr: TCP/UDP/IP/IPsec 헤더 다음에 나오는 위치입니다.
2) payload_length_ptr: 애플리케이션이 MTU를 초과하지 않고 전송할 수 있는 데이터의 양입니다.

해당 NetX 서비스가 없습니다.

### <a name="restrictions"></a>제한 

이전에 IP 인스턴스를 만들어야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 인스턴스를 가리키는 포인터입니다.
- **dest_address** 패킷 대상 주소를 가리키는 포인터입니다.
- **if_index** 사용할 인터페이스의 인덱스를 나타냅니다.
- **src_port** 원본 포트 번호입니다.
- **dest_port** 대상 포트 번호입니다.
- **protocol** 사용할 상위 계층 프로토콜입니다.
- **start_offset_ptr** 최대 패킷 페이로드의 데이터 시작을 가리키는 포인터입니다.
- **payload_length_ptr** 헤더를 제외한 페이로드 크기를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 페이로드를 계산했습니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스 인덱스가 잘못되었거나 인터페이스가 잘못되었습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 잘못되었습니다.
- **NX_PTR_ERROR**(0X07) IP 포인터가 잘못되었거나 대상 주소가 잘못되었습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 주소를 제공했습니다. 
- **NX_NOT_SUPPORTED**(0x4B) 잘못된 프로토콜(UDP 또는 TCP 아님)입니다.
- **NX_CALLER_ERROR**(0x11) 시스템 초기화 또는 스레드 컨텍스트에서 서비스가 호출되지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* The following example determines the maximum payload for UDP
   packet to remote host. */
#define PRIMARY_INTERFACE 0
status = nx_ip_max_payload_size_find(&ip_0,
                                     &dest_ipv6_address,
                                     PRIMARY_INTERFACE,
                                     source_port,
                                     dest_port, NX_PROTOCOL_UDP,
                                     &start_offset,
                                     &payload_length);

/* A return value of NX_SUCCESS indicates the packet payload
   payload_length starting at the offset start_offset is
   successfully computed. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable
원시 패킷 송신/수신을 사용하지 않도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 이 IP 인스턴스의 원시 IP 패킷 전송 및 수신을 사용하지 않도록 설정합니다. 이전에 원시 패킷 서비스를 사용하도록 설정했으며 수신 큐에 원시 패킷이 있는 경우 이 서비스는 수신된 원시 패킷을 모두 해제합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) IP 원시 패킷을 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);
/* If status is NX_SUCCESS, raw IP packet sending/receiving has
   been disabled for the previously created IP instance. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable
원시 패킷 처리를 사용하도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 이 IP 인스턴스에 대해 원시 IP 패킷 전송 및 수신을 사용할 수 있도록 설정합니다. 수신 TCP, UDP, ICMP 및 IGMP 패킷은 여전히 NetX Duo에서 처리됩니다. 상위 계층 프로토콜 유형을 알 수 없는 패킷은 원시 패킷 수신 루틴에서 처리됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) IP 원시 패킷을 사용하도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
   been enabled for the previously created IP instance. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_filter_set"></a>nx_ip_raw_packet_filter_set
원시 IP 패킷 필터 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_raw_packet_filter_set(
    NX_IP *ip_ptr,
    UINT (*raw_packet_filter)(NX_IP *, ULONG, NX_PACKET *));
```
### <a name="description"></a>Description

이 서비스는 IP 원시 패킷 필터를 구성합니다. 사용자 애플리케이션에서 구현하는 원시 패킷 필터 함수를 사용하면 애플리케이션에서 사용자가 제공한 기준에 따라 원시 패킷을 수신할 수 있습니다. NetX Duo BSD 래퍼 계층은 원시 패킷 필터 기능을 사용하여 BSD 계층의 원시 소켓을 처리합니다. 이 서비스를 사용하려면 ***NX_ENABLE_IP_RAW_PACKET_FILTER*** 옵션을 정의한 상태로 Netx Duo 라이브러리를 빌드해야 합니다.

### <a name="parameters"></a>매개 변수  

- **ip_ptr** IP 제어 블록 포인터입니다.
- **raw_packet_filter** 원시 패킷 필터의 함수 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 원시 패킷 필터 루틴을 설정했습니다.
- **NX_NOT_SUPPORT**(0x4B) 원시 패킷 지원을 사용할 수 없습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
UINT raw_packet_filter(NX_IP *ip_ptr, ULONG protocol,
                       NX_PACKET *packet_ptr)
{

/* Simply filter protocol. */
if(protocol == NX_IP_RAW)
   return NX_SUCCESS;
else
   return NX_NOT_SUCCESSFUL;
}

void raw_packet_thread_entry(ULONG id)
{

/* Set the raw packet filter of IP instance. */
status = nx_ip_raw_packet_filter_set(&ip_0,
                                     raw_packet_filter);

/* If status == NX_SUCCESS, the raw packet filter of IP instance
   was successfully set. */
}
```
### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive
원시 IP 패킷 수신

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스에서 원시 IP 패킷을 수신합니다. 원시 패킷 수신 큐에 IP 패킷이 있는 경우 첫 번째(가장 오래된) 패킷이 호출자에게 반환됩니다. 그렇지 않고 사용할 수 있는 패킷이 없는 경우 대기 옵션에 지정된 대로 호출자가 일시 중단될 수 있습니다.

> [!CAUTION]   
> NX_SUCCESS가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 해당 패킷을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **packet_ptr** 수신된 원시 IP 패킷이 배치될 포인터를 가리키는 포인터입니다.
- **wait_option** 사용할 수 있는 패킷이 없는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
   - **NX_NO_WAIT**(0x00000000)
   - **NX_WAIT_FOREVER**(0xFFFFFFFF)
   - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IP 원시 패킷 수신에 성공했습니다.
- **NX_NO_PACKET**(0x01) 사용할 수 있는 패킷이 없습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 반환 패킷 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Receive a raw IP packet for this IP instance, wait for a maximum
   of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
   variable packet_ptr. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send
원시 IP 패킷 송신

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```
### <a name="description"></a>Description

이 서비스는 원시 IPv4 패킷을 대상 IP 주소로 송신합니다. 이 루틴은 즉시 반환되므로 IP 패킷이 실제로 송신되었는지를 알 수 없습니다. 네트워크 드라이버는 전송이 완료되면 패킷을 해제해야 합니다.

멀티홈 시스템의 경우 NetX Duo는 대상 IP 주소를 사용하여 적절한 네트워크 인터페이스를 찾고 인터페이스의 IP 주소를 원본 주소로 사용합니다. 대상 IP 주소가 브로드캐스트 또는 멀티캐스트면 유효한 첫 번째 인터페이스가 사용됩니다. 이 경우 애플리케이션은 ***nx_ip_raw_packet_source_send*** 를 사용합니다.

원시 IPv6 패킷을 송신하기 위해 애플리케이션은 ***nxd_ip_raw_packet_send,** _ 또는 _ **_nxd_ip_raw_packet_source_send_* 서비스를 사용해야 합니다.

> [!WARNING]  
> 오류가 반환되지 않는 한 이 호출 후 애플리케이션은 패킷을 해제하면 안 됩니다. 애플리케이션이 패킷을 해제하면 전송 후 네트워크 드라이버가 패킷을 해제하므로 예측할 수 없는 결과가 발생합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **packet_ptr** 송신할 원시 IP 패킷을 가리키는 포인터입니다.
- **destination_ip** 대상 IP 주소로, 특정 호스트 IP 주소나 네트워크 브로드캐스트, 내부 루프백, 멀티캐스트 주소일 수 있습니다.
- **type_of_service** 전송할 서비스 유형을 정의합니다. 올바른 값은 다음과 같습니다.
    - **NX_IP_NORMAL**(0x00000000)
    - **NX_IP_MIN_DELAY**(0x00100000)
    - **NX_IP_MAX_DATA**(0x00080000)
    - **NX_IP_MAX_RELIABLE**(0x00040000)
    - **NX_IP_MIN_COST**(0x00020000)

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IP 원시 패킷 송신에 성공했습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 원시 IP 기능이 사용하도록 설정되지 않았습니다.
- **NX_OPTION_ERROR**(0x0A) 잘못된 유형의 서비스입니다.
- **NX_UNDERFLOW**(0x02) 공간이 부족하여 패킷에서 IP 헤더를 앞에 추가할 수 없습니다.
- **NX_OVERFLOW**(0x03) 패킷 뒤에 추가 포인터가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 패킷 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
                               IP_ADDRESS(1,2,3,5),
                               NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
   packet_ptr has been sent. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_source_send"></a>nx_ip_raw_packet_source_send
지정된 네트워크 인터페이스를 통해 원시 IP 패킷 송신

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_raw_packet_source_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```
### <a name="description"></a>Description

이 서비스는 지정된 로컬 IPv4 주소를 원본 주소로 사용하고 연결된 네트워크 인터페이스를 통해 원시 IP 패킷을 대상 IP 주소로 송신합니다. 이 루틴은 즉시 반환되므로 IP 패킷이 실제로 송신되었는지를 알 수 없습니다. 네트워크 드라이버는 전송이 완료되면 패킷을 해제해야 합니다. 이 서비스는 패킷이 실제로 송신되었는지를 알 방법이 없다는 점에서 다른 서비스와 다릅니다. 패킷이 인터넷에서 손실될 수도 있습니다.

> [!CAUTION]  
> 원시 IP 처리는 사용하도록 설정되어 있어야 합니다.

> [!WARNING]  
> 이 서비스는 애플리케이션이 지정된 실제 인터페이스에서 원시 IPv4 패킷을 송신하도록 허용하는 점을 제외하고는 **nx_ip_raw_packet_send** 와 유사합니다.

### <a name="parameters"></a>매개 변수  

- **ip_ptr** 이전에 만든 IP 작업을 가리키는 포인터입니다.
- **packet_ptr** 전송할 패킷을 가리키는 포인터입니다.
- **destination_ip** 패킷을 송신할 IP 주소입니다.
- **address_index** 패킷을 송신할 인터페이스 주소 인덱스입니다.
- **type_of_service** 패킷 서비스 유형입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 패킷이 성공적으로 전송되었습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 사용할 수 있는 적절한 발신 인터페이스가 없습니다.
- **NX_NOT_ENABLED**(0x14) 원시 IP 패킷 처리가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터 입력입니다.
- **NX_OPTION_ERROR**(0x0A) 잘못된 유형의 서비스가 지정되었습니다.
- **NX_OVERFLOW**(0x03) 잘못된 패킷 앞에 추가 포인터입니다.
- **NX_UNDERFLOW**(0x02) 잘못된 패킷 앞에 추가 포인터입니다.
- **NX_INVALID_INTERFACE**(0x4C) 잘못된 인터페이스 인덱스가 지정되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define ADDRESS_IDNEX 1

/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_source_send(ip_ptr, packet_ptr,
                                      destination_ip,
                                      ADDRESS_INDEX,
                                      NX_IP_NORMAL);

/* If status is NX_SUCCESS the packet was successfully
   transmitted. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_receive_queue_max_set"></a>nx_ip_raw_receive_queue_max_set
최대 원시 수신 큐 크기 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_raw_receive_queue_max_set(
    NX_IP *ip_ptr, 
    ULONG queue_max);
```
### <a name="description"></a>Description

이 서비스는 IP 원시 패킷 수신 큐의 최대 깊이를 구성합니다. IP 원시 패킷 수신 큐는 IPv4 및 IPv6 패킷 모두와 공유됩니다. 원시 패킷 수신 큐가 사용자가 구성한 최대 깊이에 도달하면 새로 수신된 원시 패킷은 삭제됩니다. 기본 IP 원시 패킷 수신 큐 깊이는 20입니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 제어 블록 포인터입니다.
- **queue_max** 큐 크기에 대한 새 값입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 원시 수신 큐의 최대 깊이를 설정했습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화 및 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
ULONG queue_max = 10;

/* Set the maximum size of the IP raw packet receive queue. */
status = nx_ip_raw_receive_queue_max_set (&ip_0,
                                          queue_max);

/* If status == NX_SUCCESS, the maximum size of the IP raw packet
   receive queue was successfully set. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add
라우팅 테이블에 고정 경로 추가

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```
### <a name="description"></a>Description

이 서비스는 고정 라우팅 테이블에 항목을 추가합니다. 로컬 네트워크 디바이스 중 하나에서 *next_hop* 주소에 직접 액세스할 수 있어야 합니다.

> [!CAUTION]  
> 이 서비스를 사용하려면 ip_ptr이 유효한 NetX Duo IP 구조를 가리켜야 하며 NX_ENABLE_IP_STATIC_ROUTING이 정의된 상태로 NetX Duo 라이브러리가 빌드되어 있어야 합니다. 기본적으로 NetX Duo는 NX_ENABLE_IP_STATIC_ROUTING이 정의되지 않은 상태로 빌드됩니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **network_address** 대상 네트워크 주소입니다(호스트 바이트 순서). 
- **net_mask** 대상 네트워크 마스크입니다(호스트 바이트 순서).
- **next_hop** 대상 네트워크의 다음 홉 주소입니다(호스트 바이트 순서).

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 항목이 고정 라우팅 테이블에 추가됩니다.
- **NX_OVERFLOW**(0x03) 고정 라우팅 테이블이 꽉 찼습니다.
- **NX_NOT_SUPPORTED**(0x4B) 이 기능은 컴파일되어 있지 않습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 로컬 인터페이스를 통해 다음 홉에 직접 액세스할 수 없습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 ip_ptr 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Specify the next hop for 192.168.1.68 through the gateway
   192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,1,0),
                                0xFFFFFF00UL,
                                IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
   static routing table. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete
라우팅 테이블에서 고정 경로 삭제

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask);
```
### <a name="description"></a>Description

이 서비스는 고정 라우팅 테이블에서 항목을 삭제합니다.

> [!WARNING]  
> 이 서비스를 사용하려면 ip_ptr이 유효한 NetX Duo IP 구조를 가리켜야 하며 NX_ENABLE_IP_STATIC_ROUTING이 정의된 상태로 NetX Duo 라이브러리가 빌드되어 있어야 합니다. 기본적으로 NetX Duo는 NX_ENABLE_IP_STATIC_ROUTING이 정의되지 않은 상태로 빌드됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **network_address** 대상 네트워크 주소입니다(호스트 바이트 순서).
- **net_mask** 대상 네트워크 마스크입니다(호스트 바이트 순서).

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0X00) 고정 라우팅 테이블에서 성공적으로 삭제되었습니다.
- **NX_NOT_SUCCESSFUL**(0X43) 라우팅 테이블에서 항목을 찾을 수 없습니다.
- **NX_NOT_SUPPORTED**(0x4B) 이 기능은 컴파일되어 있지 않습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 ip_ptr 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Remove the static route for 192.168.1.68 from the routing
   table.*/
status = nx_ip_static_route_delete(ip_ptr,
                                   IP_ADDRESS(192,168,1,0),
                                   0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
   the static routing table. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_status_check"></a>nx_ip_status_check
IP 인스턴스의 상태 확인

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 이전에 만든 IP 인스턴스의 기본 네트워크 인터페이스 상태를 확인하고 선택적으로 지정된 상태가 될 때까지 대기합니다. 보조 인터페이스에 대한 상태를 가져오려면 애플리케이션은 ***nx_ip_interface_status_check*** 서비스를 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **needed_status** 요청된 IP 상태이며 다음과 같이 비트맵 형식으로 정의됩니다.
  - **NX_IP_INITIALIZE_DONE**(0x0001)
  - **NX_IP_ADDRESS_RESOLVED**(0x0002)
  - **NX_IP_LINK_ENABLED**(0x0004)
  - **NX_IP_ARP_ENABLED**(0x0008)
  - **NX_IP_UDP_ENABLED**(0x0010)
  - **NX_IP_TCP_ENABLED**(0x0020)
  - **NX_IP_IGMP_ENABLED**(0x0040)
  - **NX_IP_RARP_COMPLETE**(0x0080)
  - **NX_IP_INTERFACE_LINK_ENABLED**(0x0100)
- **actual_status** 설정된 실제 비트 대상을 가리키는 포인터입니다.
- **wait_option** 요청된 상태 비트를 사용할 수 없는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **NX_NO_WAIT**(0x00000000)
  - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)
  - **NX_WAIT_FOREVER** 0xFFFFFFFF

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) IP 상태 확인에 성공했습니다.
- **NX_NOT_SUCCESSFUL**(0x43) 지정된 시간 제한 내에 상태 요청이 충족되지 않았습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었거나 잘못된 상태였거나, 실제 상태 포인터가 잘못되었습니다.
- **NX_OPTION_ERROR**(0x0a) 필요한 상태 옵션이 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Wait 10 ticks for the link up status on the previously created IP
   instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
                            &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
   is up. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ipv4_multicast_interface_join"></a>nx_ipv4_multicast_interface_join
인터페이스를 통해 IP 인스턴스를 지정된 멀티캐스트 그룹에 조인

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ipv4_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Description

이 서비스는 지정된 네트워크 인터페이스를 통해 IP 인스턴스를 지정된 멀티캐스트 그룹에 조인합니다. IP 인스턴스가 멀티캐스트 그룹에 조인하면 IP 수신 논리는 지정된 멀티캐스트 그룹에서 상위 계층으로 데이터 패킷을 전달하기 시작합니다. 이 서비스는 IGMP 보고서를 보내지 않고 멀티캐스트 그룹에 조인합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **group_address** 조인할 클래스 D IP 멀티캐스트 그룹 주소입니다(호스트 바이트 순서).
- **interface_index** NetX Duo 인스턴스에 연결된 인터페이스 인덱스입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 멀티캐스트 그룹 조인에 성공했습니다.
- **NX_NO_MORE_ENTRIES**(0x17) 멀티캐스트 그룹을 더 이상 조인할 수 없습니다. 최대값이 초과되었습니다.
- **NX_PTR_ERROR**(0X07) IP 인스턴스에 대한 포인터가 잘못되었거나 IP 인스턴스가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_EANABLED**(0X14) 이 IP 인스턴스에서 IGMP를 사용하도록 설정하지 않았습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 제공된 멀티캐스트 그룹 주소가 잘못된 클래스 D 주소입니다.
- **NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못된 네트워크 인터페이스를 가리킵니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Previously created IP Instance joins the multicast group
   224.0.0.200, via the interface at index 1 in the IP interface
   list. */
#define INTERFACE_INDEX 1
status = nx_ipv4_multicast_interface_join
                                 (&ip IP_ADDRESS(224,0,0,200),
                                  INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
   the multicast group. */
```
### <a name="see-also"></a>참고 항목

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_ipv4_multicast_interface_leave"></a>nx_ipv4_multicast_interface_leave
인터페이스를 통해 지정된 멀티캐스트 그룹 탈퇴

### <a name="prototype"></a>프로토타입  

```c
UINT nx_ipv4_multicast_interface_leave(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Description

이 서비스는 지정된 네트워크 인터페이스를 통해 지정된 멀티캐스트 그룹에서 탈퇴합니다. 이 서비스는 그룹에서 탈퇴한 난 후에 IGMP 메시지가 생성되도록 트리거하지 않습니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **group_address** 탈퇴할 클래스 D IP 멀티캐스트 그룹 주소입니다. IP 주소는 호스트 바이트 순서로 되어 있습니다.
- **interface_index** NetX Duo 인스턴스에 연결된 인터페이스 인덱스입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 멀티캐스트 그룹 조인에 성공했습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) 로컬 멀티캐스트 테이블에서 지정된 멀티캐스트 그룹 주소를 찾을 수 없습니다.
- **NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못된 네트워크 인터페이스를 가리킵니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 제공된 멀티캐스트 그룹 주소가 잘못된 클래스 D 주소입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_PTR_ERROR**(0X07) IP 인스턴스에 대한 포인터가 잘못되었거나 IP 인스턴스가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Leave the multicast group 224.0.0.200. */
#define INTERFACE_INDEX 1
status = nx_ipv4_multicast_interface_leave
                                (&ip, IP_ADDRESS(224,0,0,200),
                                 INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully leaves
   the multicast group 244.0.0.200. */
```
### <a name="see-also"></a>참고 항목

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_packet_allocate"></a>nx_packet_allocate
지정된 풀에서 패킷 할당

### <a name="prototype"></a>프로토타입  

```c
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 지정된 풀의 패킷을 할당하고 지정된 패킷의 유형에 따라 패킷의 앞에 추가 포인터를 조정합니다. 사용할 수 있는 패킷이 없는 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 이전에 만든 패킷 풀을 가리키는 포인터입니다.
- **packet_ptr** 할당된 패킷 포인터의 포인터를 가리키는 포인터입니다.
- **packet_type** 요청된 패킷의 유형을 정의합니다. 지원되는 패킷 유형 목록은 3장의 63페이지에서 “패킷 풀”을 참조하세요.
- **wait_option** 패킷 풀에서 사용할 수 있는 패킷이 없는 경우의 틱 단위 대기 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **NX_NO_WAIT**(0x00000000)
  - **NX_WAIT_FOREVER**(0xFFFFFFFF)
  - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 패킷 할당에 성공했습니다.
- **NX_NO_PACKET**(0x01) 사용 가능한 패킷이 없습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 패킷 크기가 프로토콜을 지원할 수 없습니다.
- **NX_OPTION_ERROR**(0x0A) 잘못된 패킷 유형입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 풀 또는 패킷 반환 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 비스레드의 대기 옵션이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머 및 ISR(애플리케이션 네트워크 드라이버) ISR 또는 타이머 컨텍스트에서 사용되는 경우 대기 옵션은 NX_NO_WAIT여야 합니다.

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Allocate a new UDP packet from the previously created packet pool
   and suspend for a maximum of 5 timer ticks if the pool is
   empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr,
                            NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
   found in the variable packet_ptr. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy
패킷 복사

### <a name="prototype"></a>프로토타입  

```c
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 제공된 패킷 풀에서 할당된 하나 이상의 새 패킷에 제공된 패킷의 정보를 복사합니다. 성공하면 새 패킷을 가리키는 포인터가 **new_packet_ptr** 에서 가리키는 대상에 반환됩니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 원본 패킷을 가리키는 포인터입니다.
- **new_packet_ptr** 패킷의 새 복사본에 대한 포인터를 반환할 위치 대상을 가리키는 포인터입니다.
- **pool_ptr** 복사본에 대해 패킷을 하나 이상 할당하는 데 사용되는, 이전에 만든 패킷 풀을 가리키는 포인터입니다.
- **wait_option** 사용할 수 있는 패킷이 없는 경우 서비스가 대기하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **NX_WAIT_FOREVER**(0xFFFFFFFF)
    - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 패킷 복사에 성공했습니다.
- **NX_NO_PACKET**(0x01) 패킷을 복사할 수 없습니다.
- **NX_INVALID_PACKET**(0x12) 원본 패킷이 비어 있거나 복사하는 데 실패했습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 패킷 크기가 프로토콜을 지원할 수 없습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 풀, 패킷 또는 대상 포인터입니다.
- **NX_UNDERFLOW**(0x02) 잘못된 패킷 앞에 추가 포인터입니다.
- **NX_OVERFLOW**(0x03) 잘못된 패킷 뒤에 추가 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 초기화 또는 ISR에 대기 옵션이 지정되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머 및 ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
   previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append
패킷 끝에 데이터 추가

### <a name="prototype"></a>프로토타입  

```c
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 지정된 패킷 끝에 데이터를 추가합니다. 제공된 데이터 영역은 패킷으로 복사됩니다. 사용할 수 있는 메모리가 부족하며 연결된 패킷 기능이 사용하도록 설정된 경우 패킷을 하나 이상 할당하여 요청을 충족합니다. 연결된 패킷 기능이 사용하도록 설정되지 않는 경우 NX_SIZE_ERROR가 반환됩니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 패킷 포인터입니다.
- **data_start** 패킷 뒤에 추가할 사용자 데이터 영역 시작 부분을 가리키는 포인터입니다.
- **data_size** 사용자 데이터 영역 크기입니다.
- **pool_ptr** 현재 패킷에 공간이 충분하지 않은 경우 다른 패킷을 할당할 패킷 풀을 가리키는 포인터입니다.
- **wait_option** 사용할 수 있는 패킷이 없는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **NX_WAIT_FOREVER**(0xFFFFFFFF)
    - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 패킷 뒤에 추가에 성공했습니다.
- **NX_NO_PACKET**(0x01) 사용 가능한 패킷이 없습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 패킷 크기가 프로토콜을 지원할 수 없습니다.
- **NX_UNDERFLOW**(0x02) 앞에 추가 포인터가 페이로드 시작보다 먼저입니다.
- **NX_OVERFLOW**(0x03) 뒤에 추가 포인터가 페이로드 종료보다 나중입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 풀, 패킷 또는 데이터 포인터입니다.
- **NX_SIZE_ERROR**(0x09) 잘못된 데이터 크기입니다.
- **NX_CALLER_ERROR**(0x11) 비스레드의 대기 옵션이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머 및 ISR(애플리케이션 네트워크 드라이버)

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
   been appended to the packet. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release


## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset
오프셋을 통해 패킷에서 데이터 추출

### <a name="prototype"></a>프로토타입  

```c
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```
### <a name="description"></a>Description

이 서비스는 패킷 앞에 추가 포인터의 지정된 오프셋에서 시작하여 지정된 크기(바이트)의 NetX Duo 패킷(또는 패킷 체인) 데이터를 지정된 버퍼에 복사합니다. 실제로 복사된 바이트 수는 *bytes_copied* 로 반환됩니다. 이 서비스는 패킷에서 데이터를 제거하지 않으며 앞에 추가 포인터 또는 다른 내부 상태 정보도 조정하지 않습니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 추출할 패킷을 가리키는 포인터입니다.
- **offset** 현재 앞에 추가 포인터의 오프셋입니다.
- **buffer_start** 저장 버퍼 시작 부분을 가리키는 포인터입니다.
- **buffer_length** 복사할 바이트 수입니다.
- **bytes_copied** 실제로 복사된 바이트 수입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 패킷 복사에 성공했습니다.
- **NX_PACKET_OFFSET_ERROR**(0x53) 잘못된 오프셋 값을 제공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 패킷 포인터 또는 버퍼 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머 및 ISR

### <a name="preemption-possible"></a>가능한 선점

예

```c
/* Extract 10 bytes from the start of the received packet buffer
   into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
                                       &bytes_copied) ;
/* If status is NX_SUCCESS, 10 bytes were successfully copied into
   the data buffer. */
```
### <a name="see-also"></a>관련 항목

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve
패킷에서 데이터 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start,
    ULONG *bytes_copied);
```
### <a name="description"></a>Description

이 서비스는 제공된 패킷의 데이터를 제공된 버퍼에 복사합니다. 복사된 실제 바이트 수는 **bytes_copied** 가 가리키는 대상에 반환됩니다.

이 서비스는 패킷의 내부 상태를 변경하지 않습니다. 검색되는 데이터는 패킷에서 계속 사용할 수 있습니다. 

> [!CAUTION]  
> 대상 버퍼는 패킷 콘텐츠를 포함할 수 있도록 크기가 충분히 커야 합니다. 그렇지 않으면 메모리가 손상되어 예기치 않은 결과가 발생합니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 원본 패킷을 가리키는 포인터입니다.
- **buffer_start** 버퍼 영역의 시작 부분을 가리키는 포인터입니다.
- **bytes_copied** 복사된 바이트 수 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷 데이터 검색에 성공했습니다.
- **NX_INVALID_PACKET**(0x12) 잘못된 패킷입니다.
- **NX_PTR_ERROR**(0x07) 패킷, 버퍼 시작 또는 복사된 바이트 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머 및 ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
UCHAR                 buffer[512];
ULONG                 bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
   packet, the size of which is contained in "bytes_copied." */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get
패킷 데이터의 길이 가져오기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```
### <a name="description"></a>Description

이 서비스는 지정된 패킷에서 데이터의 길이를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 패킷을 가리키는 포인터입니다.
- **length** 패킷 길이 대상입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 패킷 길이를 가져왔습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 패킷 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머 및 ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create
지정된 메모리 영역에 패킷 풀 만들기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```
### <a name="description"></a>Description

이 서비스는 사용자가 제공한 메모리 영역에 지정된 패킷 크기의 패킷 풀을 만듭니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 패킷 풀 제어 블록을 가리키는 포인터입니다.
- **name** 패킷 풀의 애플리케이션 이름을 가리키는 포인터입니다.
- **payload_size** 풀에 있는 각 패킷의 바이트 수입니다. 이 값은 40바이트 이상이어야 하며 4로 균등하게 나뉘어야 합니다.
- **memory_ptr** 패킷 풀을 배치할 메모리 영역을 가리키는 포인터입니다. 이 포인터는 ULONG 경계에 맞춰야 합니다.
- **memory_size** 풀 메모리 영역의 크기입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 패킷 풀을 만드는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 풀 또는 메모리 포인터입니다.
- **NX_SIZE_ERROR**(0x09) 잘못된 블록 또는 메모리 크기입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Create a packet pool of 32000 bytes starting at physical
   address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
                               (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
   created. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete
이전에 만든 패킷 풀 삭제

### <a name="prototype"></a>프로토타입  

```c
UINT  nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Description

이 서비스는 이전에 만든 패킷 풀을 삭제합니다. NetX는 패킷 풀의 패킷에서 현재 일시 중단된 스레드가 있는지 확인하고 일시 중단을 해제합니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 패킷 풀 제어 블록 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 패킷 풀 삭제에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 풀 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
   deleted. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get
패킷 풀에 대한 정보 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```
### <a name="description"></a>Description

이 서비스는 지정된 패킷 풀에 대한 정보를 검색합니다.

> [!IMPORTANT]  
> 대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 이전에 만든 패킷 풀을 가리키는 포인터입니다.
- **total_packets** 풀의 총 패킷 수 대상을 가리키는 포인터입니다.
- **free_packets** 현재 사용 가능한 총 패킷 수 대상을 가리키는 포인터입니다.
- **empty_pool_requests** 풀이 비어 있는 경우의 총 할당 요청 수 대상을 가리키는 포인터입니다.
- **empty_pool_suspensions** 비어 있는 풀의 총 일시 중단 수 대상을 가리키는 포인터입니다.
- **invalid_packet_releases** 잘못된 총 패킷 해제 수 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 패킷 풀 정보를 검색하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드 및 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
                                 &total_packets,
                                 &free_packets,
                                 &empty_pool_requests,
                                 &empty_pool_suspensions,
                                 &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
   retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_low_watermark_set"></a>nx_packet_pool_low_watermark_set
패킷 풀 하위 워터마크 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_packet_pool_low_watermark_set(
    NX_PACKET_POOL *pool_ptr,
    ULONG low_watermark);
```
### <a name="description"></a>Description

이 서비스는 지정된 패킷 풀에 대한 하위 워터마크를 구성합니다. 하위 워터마크 값이 설정되면 패킷 풀의 사용 가능한 패킷 수가 패킷 풀의 하위 워터마크보다 작은 경우 TCP 또는 UDP가 수신된 패킷을 큐에 대기하지 않으므로 패킷 풀에서 패킷이 고갈되지 않게 됩니다. 이 서비스는 ***NX_ENABLE_LOW_WATERMARK*** 옵션을 정의한 상태로 Netx Duo 라이브러리를 빌드한 경우에 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 패킷 풀 제어 블록을 가리키는 포인터입니다.
- **low_watermark** 구성할 하위 워터마크 값입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 하위 워터마크 값을 설정했습니다.
- **NX_NOT_SUPPORTED**(0x4B) 하위 워터마크 기능은 Netx Duo에 기본 제공되지 않습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 풀 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Set pool_0 low watermark value to 2. */
status = nx_packet_pool_create(&pool_0, 2);

/* If status is NX_SUCCESS, the low watermark value is set for
   pool_0.*/
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release
이전에 할당된 패킷 해제

### <a name="prototype"></a>프로토타입  

```c
UINT nx_packet_release(NX_PACKET *packet_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 패킷에 연결된 추가 패킷을 포함하여 패킷을 해제합니다. 다른 스레드가 패킷 할당에서 차단된 경우 이 서비스가 해당 패킷에 제공되고 계속 진행됩니다.

> [!NOTE]  
> 패킷을 두 번 이상 해제하면 예기치 않은 결과가 발생할 수 있으므로 애플리케이션은 패킷을 한 번만 해제하도록 해야 합니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 패킷 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 패킷 해제에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 패킷 포인터입니다.
- **NX_UNDERFLOW**(0x02) 앞에 추가 포인터가 페이로드 시작보다 먼저입니다.
- **NX_OVERFLOW**(0x03) 뒤에 추가 포인터가 페이로드 종료보다 나중입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머 및 ISR(애플리케이션 네트워크 드라이버)

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
   packet pool it was allocated from. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release
전송된 패킷 해제

### <a name="prototype"></a>프로토타입  

```c
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```
### <a name="description"></a>Description

TCP가 아닌 패킷의 경우 이 서비스는 지정된 패킷에 연결된 추가 패킷을 포함하여 전송된 패킷을 해제합니다. 다른 스레드가 패킷 할당에서 차단된 경우 이 서비스가 해당 패킷에 제공되고 계속 진행됩니다. 전송된 TCP 패킷의 경우 패킷이 전송 중으로 표시되지만 패킷이 확인될 때까지 해제되지 않습니다. 이 서비스는 일반적으로 패킷이 전송된 후 애플리케이션 네트워크 드라이버에서 호출됩니다.

> [!WARNING] 
> 네트워크 드라이버는 이 서비스를 호출하기 전에 실제 미디어 헤더를 제거하고 패킷 길이를 조정해야 합니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 패킷 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 전송 패킷 해제에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 패킷 포인터입니다.
- **NX_UNDERFLOW**(0x02) 앞에 추가 포인터가 페이로드 시작보다 먼저입니다.
- **NX_OVERFLOW**(0x03) 뒤에 추가 포인터가 페이로드 종료보다 나중입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머, 애플리케이션 네트워크 드라이버(ISR 포함)

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Release a previously allocated packet that was just transmitted
   from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
   returned to the packet pool it was allocated from. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable
RARP(역주소 확인 프로토콜)를 사용하지 않도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 특정 IP 인스턴스에 대해 NetX Duo의 RARP 구성 요소를 사용하지 않도록 설정합니다. 멀티홈 시스템의 경우 이 서비스는 모든 인터페이스에서 RARP를 사용하지 않도록 설정합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) RARP를 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_NOT_ENABLED**(0x14) RARP가 사용하지 않도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```
### <a name="see-also"></a>참고 항목

- nx_rarp_enable
- nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable
RARP(역주소 확인 프로토콜)를 사용하도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_rarp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 특정 IP 인스턴스에 대해 NetX Duo의 RARP 구성 요소를 사용하도록 설정합니다. RARP 구성 요소는 모든 연결된 네트워크 인터페이스에서 0으로 된 IP 주소를 검색합니다. 0으로 된 IP 주소는 인터페이스에 IP 주소 할당이 아직 없는 것을 나타냅니다. RARP는 해당 인터페이스에서 RARP 프로세스를 사용하도록 설정하여 IP 주소를 확인하려고 시도합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) RARP를 사용하도록 설정하는 데 성공했습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 이미 유효합니다.
- **NX_ALREADY_ENABLED**(0x15) RARP가 이미 사용하도록 설정되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
   resolve this IP instance’s address by querying the network. */
```
### <a name="see-also"></a>참고 항목

- nx_rarp_disable
- nx_rarp_info_get

## <a name="nx_rarp_info_get"></a>nx_rarp_info_get
RARP 활동에 대한 정보 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 RARP 활동에 대한 정보를 검색합니다.

> [!IMPORTANT]  
> 대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **rarp_requests_sent** 송신된 총 RARP 요청 수 대상을 가리키는 포인터입니다.
- **rarp_responses_received** 수신된 총 RARP 응답 수 대상을 가리키는 포인터입니다.
- **rarp_invalid_messages** 잘못된 총 메시지 수 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) RARP 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Retrieve RARP information from previously created IP
   Instance 0. */
status = nx_rarp_info_get(&ip_0,
                          &rarp_requests_sent,
                          &rarp_responses_received,
                          &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_rarp_disable
- nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize
NetX Duo 시스템 초기화

### <a name="prototype"></a>프로토타입  

```c
VOID nx_system_initialize(VOID);
```
### <a name="description"></a>Description

이 서비스는 사용을 위한 준비로 기본 NetX Duo 시스템 리소스를 초기화합니다. 초기화 중 다른 NetX Duo 호출이 수행되기 전에 애플리케이션에서 이 서비스가 호출되어야 합니다.

### <a name="parameters"></a>매개 변수

None

### <a name="return-values"></a>반환 값

None

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

시스템 관리

### <a name="example"></a>예제

```c
/* Initialize NetX Duo for operation. */
nx_system_initialize();

/* At this point, NetX Duo is ready for IP creation and all
   subsequent network operations. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind
클라이언트 TCP 소켓을 TCP 포트에 바인딩

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 이전에 만든 TCP 클라이언트 소켓을 지정된 TCP 포트에 바인딩합니다. 유효한 TCP 소켓 범위는 0에서 0xFFFF까지입니다. 지정된 TCP 포트를 사용할 수 없는 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓 인스턴스를 가리키는 포인터입니다.
- **port** 바인딩할 포트 번호(1-0xFFFF)입니다. 포트 번호가 NX_ANY_PORT (0x0000)인 경우 IP 인스턴스는 가능한 다음 포트를 검색하여 바인딩에 사용합니다.
- **wait_option** 포트가 이미 다른 소켓에 바인딩되어 있는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- **NX_NO_WAIT**(0x00000000)
- **NX_WAIT_FOREVER**(0xFFFFFFFF)
- **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓 바인딩에 성공했습니다.
- **NX_ALREADY_BOUND**(0x22) 이 소켓은 다른 TCP 포트에 이미 바인딩되어 있습니다.
- **NX_PORT_UNAVAILABLE**(0x23) 포트가 이미 다른 소켓에 바인딩되어 있습니다.
- **NX_NO_FREE_PORTS**(0x45) 사용 가능한 포트가 없습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_INVALID_PORT**(0x46) 잘못된 포트입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Bind a previously created client socket to port 12 and wait for 7
   timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
   bound to port 12 on the associated IP instance. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect
클라이언트 TCP 소켓 연결

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 이전에 만든 바인딩된 TCP 클라이언트 소켓을 지정된 서버 포트에 연결합니다. 유효한 TCP 서버 포트의 범위는 0에서 0xFFFF까지입니다. 연결이 즉시 완료되지 않으면 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓 인스턴스를 가리키는 포인터입니다.
- **server_ip** 서버의 IP 주소입니다.
- **server_port** 연결할 서버 포트 번호**(1-0xFFFF)입니다.
- **wait_option** 연결이 설정되는 동안 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **NX_WAIT_FOREVER**(0xFFFFFFFF)
    - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 소켓 연결에 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 바인딩되지 않았습니다.
- **NX_NOT_CLOSED**(0x35) 소켓이 닫힘 상태가 아닙니다.
- **NX_IN_PROGRESS**(0x37) 대기하도록 지정되지 않았으며, 연결하려고 시도하는 중입니다.
- **NX_INVALID_INTERFACE**(0x4C) 잘못된 인터페이스가 제공되었습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 서버 IP 주소입니다.
- **NX_INVALID_PORT**(0x46) 잘못된 포트입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Initiate a TCP connection from a previously created and bound
   client socket. The connection requested in this example is to
   port 12 on the server with the IP address of 1.2.3.5. This
   service will wait 300 timer ticks for the connection to take
   place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
                                      IP_ADDRESS(1,2,3,5),
                                      12, 300);

/* If status is NX_SUCCESS, the previously created and bound
   client_socket is connected to port 12 on IP 1.2.3.5. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get
클라이언트 TCP 소켓에 바인딩된 포트 번호 가져오기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```
### <a name="description"></a>Description

이 서비스는 소켓에 연결된 포트 번호를 검색합니다. 소켓이 바인딩될 때 NX_ANY_PORT가 지정된 경우 NetX Duo에서 할당한 포트를 찾는 데 유용합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓 인스턴스를 가리키는 포인터입니다.
- **port_ptr** 반환 포트 번호 대상을 가리키는 포인터입니다. 유효한 포트 번호는 (1-0xFFFF)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓 바인딩에 성공했습니다.
- **NX_NOT_BOUND**(0x24) 이 소켓은 포트에 바인딩되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터 또는 포트 반환 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Get the port number of previously created and bound client
   socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
   socket is bound to. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind
TCP 포트에서 TCP 클라이언트 소켓 바인딩 해제

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>Description

이 서비스는 TCP 클라이언트 소켓과 TCP 포트 간에 바인딩을 해제합니다. 다른 소켓을 동일한 포트 번호에 바인딩하려고 대기 중인 다른 스레드가 있는 경우 첫 번째 일시 중단된 스레드가 이 포트에 바인딩됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓 인스턴스를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 소켓을 바인딩 해제하는 데 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.
- **NX_NOT_CLOSED**(0x35) 소켓이 연결 해제되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
   bound. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_enable"></a>nx_tcp_enable
NetX Duo의 TCP 구성 요소를 사용하도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 NetX Duo의 TCP(Transmission Control Protocol) 구성 요소를 사용하도록 설정합니다. 사용하도록 설정하면 애플리케이션에서 TCP 연결을 설정할 수 있습니다.

### <a name="parameters"></a>매개 변수  

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TCP를 사용하도록 설정하는 데 성공했습니다.
- **NX_ALREADY_ENABLED**(0x15) TCP는 이미 사용하도록 설정되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find
사용할 수 있는 다음 TCP 포트 찾기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port,
    UINT *free_port_ptr);
```
### <a name="description"></a>Description

이 서비스는 애플리케이션 제공 포트에서 시작하여 사용 가능한 TCP 포트(바인딩되지 않은 포트)를 찾으려고 합니다. 검색에서 최대 포트 값인 0xFFFF에 도달하면 검색 논리가 래핑됩니다. 검색에 성공하면 *free_port_ptr* 이 가리키는 변수에 사용 가능한 포트가 반환됩니다.

> [!WARNING]  
> 이 서비스는 다른 스레드에서 호출될 수 있으며 동일한 포트를 반환할 수 있습니다. 이러한 경합 상태를 방지하기 위해 애플리케이션은 이 서비스 및 실제 클라이언트 소켓 바인딩에 뮤텍스 보호가 적용되도록 할 수 있습니다.

### <a name="parameters"></a>매개 변수  

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **port** 검색을 시작할 포트 번호(1-0xFFFF)입니다.
- **free_port_ptr** 사용 가능한 포트 반환 값 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 사용 가능한 포트를 찾는 데 성공했습니다.
- **NX_NO_FREE_PORTS**(0x45) 사용 가능한 포트를 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PORT**(0x46) 지정된 포트 번호가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Locate a free TCP port, starting at port 12, on a previously
   created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
   on the IP instance. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get
TCP 활동에 대한 정보 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 TCP 활동에 대한 정보를 검색합니다.

> [!IMPORTANT]  
> 대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **tcp_packets_sent** 송신된 총 TCP 패킷 수 대상을 가리키는 포인터입니다.
- **tcp_bytes_sent** 송신된 총 TCP 바이트 수 대상을 가리키는 포인터입니다.
- **tcp_packets_received** 수신된 총 TCP 패킷 수 대상을 가리키는 포인터입니다.
- **tcp_bytes_received** 수신된 총 TCP 바이트 수 대상을 가리키는 포인터입니다.
- **tcp_invalid_packets** 잘못된 총 TCP 패킷 수 대상을 가리키는 포인터입니다.
- **tcp_receive_packets_dropped** 삭제된 총 TCP 수신 패킷 수 대상을 가리키는 포인터입니다.
- **tcp_checksum_errors** 체크섬 오류가 있는 총 TCP 패킷 수 대상을 가리키는 포인터입니다.
- **tcp_connections** 총 TCP 연결 수 대상을 가리키는 포인터입니다.
- **tcp_disconnections** 총 TCP 연결 해제 수 대상을 가리키는 포인터입니다.
- **tcp_connections_dropped** 삭제된 총 TCP 연결 수 대상을 가리키는 포인터입니다.
- **tcp_retransmit_packets** 재전송된 총 TCP 패킷 수 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS** (0x00) TCP 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Retrieve TCP information from previously created IP Instance
   ip_0. */
status = nx_tcp_info_get(&ip_0,
                         &tcp_packets_sent,
                         &tcp_bytes_sent,
                         &tcp_packets_received,
                         &tcp_bytes_received,
                         &tcp_invalid_packets,
                         &tcp_receive_packets_dropped,
                         &tcp_checksum_errors,
                         &tcp_connections,
                         &tcp_disconnections
                         &tcp_connections_dropped,
                         &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept
TCP 연결 수락

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 이전에 수신 대기에 사용하도록 설정한 포트에 대한 TCP 클라이언트 소켓 연결 요청을 수락하거나 수락하기 위해 준비합니다. 애플리케이션이 수신 대기 또는 다시 수신 대기 서비스를 호출한 직후 이 서비스가 호출될 수도 있고, 클라이언트 연결이 실제로 있을 때 수신 콜백 루틴을 호출한 직후 이 서비스가 호출될 수도 있습니다. 즉시 연결을 설정할 수 없는 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.

> [!WARNING]  
> 연결이 더 이상 필요하지 않으면 서버 포트에 대한 서버 소켓 바인딩을 제거하도록 애플리케이션이 **nx_tcp_server_socket_unaccept** 를 호출해야 합니다.

> [!IMPORTANT]  
> 애플리케이션 콜백 루틴은 IP 도우미 스레드 내에서 호출됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** TCP 서버 소켓 제어 블록을 가리키는 포인터입니다.
- **wait_option** 연결이 설정되는 동안 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **NX_WAIT_FOREVER**(0xFFFFFFFF)
    - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) TCP 서버 소켓을 수락(수동 연결)하는 데 성공했습니다.
- **NX_NOT_LISTEN_STATE**(0x36) 제공된 서버 소켓이 수신 대기 상태가 아닙니다.
- **NX_IN_PROGRESS**(0x37) 대기하도록 지정되지 않았으며, 연결하려고 시도하는 중입니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_PTR_ERROR**(0x07) 소켓 포인터 오류입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
       example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
NX_PACKET *my_packet;
UINT status, i;
    /* Assuming that:
       "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
                         "Port 12 Server Socket",
                          NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                          NX_IP_TIME_TO_LIVE, 100,
                          NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                port_12_connect_request);

    /* Loop to process 5 server connections, sending
       "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {

        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
           complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {

            /* Allocate a packet for the "Hello_and_Goodbye"
               message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                         NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                  sizeof("Hello_and_Goodbye"),
                                  &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
               /* Error, release the packet. */
               nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
         }

         /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
         nx_tcp_server_socket_unaccept(&server_socket);

         /* Setup server socket for listening with this socket
            again. */
         nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }

     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);

     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen
TCP 포트에서 클라이언트 연결 수신 대기를 사용하도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```
### <a name="description"></a>Description

이 서비스는 지정된 TCP 포트에서 클라이언트 연결 요청 수신 대기를 사용하도록 설정합니다. 클라이언트 연결 요청이 수신되면 제공된 서버 소켓이 지정된 포트에 바인딩되고 제공된 수신 대기 콜백 함수가 호출됩니다.

수신 대기 콜백 루틴 처리는 애플리케이션에 따라 다릅니다. 수락 작업에 이어 수행되는 애플리케이션 스레드 절전 모드 해제 논리가 포함되어 있을 수 있습니다. 이 소켓에 대해 수락 처리가 일시 중단된 스레드가 이미 애플리케이션에 있는 경우 수신 대기 콜백 루틴이 필요하지 않을 수 있습니다.

애플리케이션이 동일한 포트에서 추가 클라이언트 연결을 처리하려는 경우 다음 연결에 사용할 수 있는 소켓(CLOSED 상태의 소켓)이 포함된 ***nx_tcp_server_socket_relisten*** 을 호출해야 합니다. 다시 수신 대기 서비스가 호출될 때까지 추가 클라이언트 연결은 큐에 대기됩니다. 최대 큐 크기를 초과하는 경우 새 연결 요청이 큐에 대기될 수 있도록 가장 오래된 연결 요청이 삭제됩니다. 최대 큐 크기는 이 서비스에서 지정합니다.

> [!IMPORTANT]  
> 애플리케이션 콜백 루틴은 내부 IP 도우미 스레드에서 호출됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **port** 수신 대기할 포트 번호(1-0xFFFF)입니다.
- **socket_ptr** 연결에 사용할 소켓을 가리키는 포인터입니다.
- **listen_queue_size** 큐에 대기될 수 있는 클라이언트 연결 요청 수입니다.
- **listen_callback** 연결이 수신되면 호출할 애플리케이션 함수입니다. NULL을 지정하면 수신 대기 콜백 기능을 사용하지 않도록 설정합니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) TCP 포트 수신 대기를 사용하도록 설정하는 데 성공했습니다.
- **NX_MAX_LISTEN**(0x33) 수신 대기 요청 구조를 더 이상 사용할 수 없습니다. **_nx_api.h_** 의 상수 NX_MAX_LISTEN_REQUESTS는 가능한 활성 수신 대기 요청 수를 정의합니다.
- **NX_NOT_CLOSED**(0x35) 제공된 서버 소켓이 닫힘 상태가 아닙니다.
- **NX_ALREADY_BOUND**(0x22) 제공된 서버 소켓이 이미 포트에 바인딩되어 있습니다.
- **NX_DUPLICATE_LISTEN**(0x34) 이 포트의 활성 수신 대기 요청이 이미 있습니다.
- **NX_INVALID_PORT**(0x46) 잘못된 포트가 지정되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
   /* Simply set the semaphore to wake up the server thread.*/
   tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
   /* The client has initiated a disconnect on this socket.
   This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
NX_PACKET *my_packet;
UINT status, i;
   /* Assuming that:
      "port_12_semaphore" has already been created with an
      initial count of 0 "my_ip" has already been created
      and the link is enabled "my_pool" packet pool has already
      been created.
   */

   /* Create the server socket. */
   nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
                        Socket",
                        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                        NX_IP_TIME_TO_LIVE, 100,
                        NX_NULL, port_12_disconnect_request);

   /* Setup server listening on port 12. */
   nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                               port_12_connect_request);

   /* Loop to process 5 server connections, sending
      "Hello_and_Goodbye" to
      each client and then disconnecting. */
   for (i = 0; i < 5; i++)
   {

        /* Get the semaphore that indicates a client connection
           request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection
           to complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
           if (status == NX_SUCCESS)
        {

              /* Allocate a packet for the "Hello_and_Goodbye"
                 message. */
              nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                 NX_WAIT_FOREVER);

              /* Place "Hello_and_Goodbye" in the packet. */
              nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                    sizeof("Hello_and_Goodbye"),
                                    &my_pool,
                                    NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
         }
         /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
         nx_tcp_server_socket_unaccept(&server_socket);

         /* Setup server socket for listening with this socket
         again. */
         nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }
     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);
     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten
TCP 포트에서 클라이언트 연결을 위해 다시 수신 대기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>Description

이전에 수신 대기에 사용하도록 설정한 포트에서 연결을 수신하면 이 서비스가 호출됩니다. 이 서비스는 다음 클라이언트 연결에 사용하도록 새 서버 소켓을 제공하기 위한 것입니다. 연결 요청이 큐에 있는 경우 이 서비스 호출 중에 바로 연결이 처리됩니다.

> [!IMPORTANT]  
> 새 서버 소켓에 대한 연결이 있는 경우 원래 수신 대기 요청에서 지정한 것과 동일한 콜백 루틴도 호출됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **port** 다시 수신 대기할 포트 번호(1-0xFFFF)입니다.
- **socket_ptr** 다음 클라이언트 연결에 사용할 소켓입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) TCP 포트 다시 수신 대기에 성공했습니다.
- **NX_NOT_CLOSED**(0x35) 제공된 서버 소켓이 닫힘 상태가 아닙니다.
- **NX_ALREADY_BOUND**(0x22) 제공된 서버 소켓이 이미 포트에 바인딩되어 있습니다.
- **NX_INVALID_RELISTEN**(0x47) 이 포트에 유효한 소켓 포인터가 이미 있거나 지정된 포트에 활성 수신 대기 요청이 없습니다.
- **NX_CONNECTION_PENDING**(0x48) 큐에 대기된 연결 요청이 있었고 이 호출 중에 처리되었던 것을 제외하면 NX_SUCCESS와 동일합니다.
- **NX_INVALID_PORT**(0x46) 잘못된 포트가 지정되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 수신 대기 콜백 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{

   /* Simply set the semaphore to wake up the server thread.*/
   tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
   /* The client has initiated a disconnect on this socket. This
      example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{

NX_PACKET *my_packet;
UINT status, i;

   /* Assuming that:
     "port_12_semaphore" has already been created with an initial
     count of 0.
    "my_ip" has already been created and the link is enabled.
    "my_pool" packet pool has already been created. */

   /* Create the server socket. */
   nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
                                 NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                 NX_IP_TIME_TO_LIVE, 100,
                                 NX_NULL, port_12_disconnect_request);

   /* Setup server listening on port 12. */
   nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                               port_12_connect_request);

   /* Loop to process 5 server connections, sending
      "Hello_and_Goodbye" to each client then disconnecting. */
   for (i = 0; i < 5; i++)
   {

       /* Get the semaphore that indicates a client connection
          request is present. */
       tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

       /* Wait for 200 ticks for the client socket connection to
          complete. */
       status = nx_tcp_server_socket_accept(&server_socket, 200);

       /* Check for a successful connection. */
          if (status == NX_SUCCESS)
       {

             /* Allocate a packet for the "Hello_and_Goodbye"
                message. */
             nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                NX_WAIT_FOREVER);

             /* Place "Hello_and_Goodbye" in the packet. */
             nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                   sizeof("Hello_and_Goodbye"),
                                   &my_pool, NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {

                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

             /* Now disconnect the server socket from the client. */
             nx_tcp_socket_disconnect(&server_socket, 200);
         }

         /* Unaccept the server socket. Note that unaccept is
            called even if disconnect or accept fails. */
         nx_tcp_server_socket_unaccept(&server_socket);

         /* Setup server socket for listening with this socket
            again. */
         nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }

     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);

     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept
수신 대기 포트와 소켓 간 연결 제거

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>Description

이 서비스는 이 서버 소켓과 지정된 서버 포트 간 연결을 제거합니다. 애플리케이션은 연결 해제 후 또는 호출 수락 실패 후 이 서비스를 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 설정한 서버 소켓 인스턴스를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 서버 소켓을 수락하지 않는 데 성공했습니다.
- **NX_NOT_LISTEN_STATE**(0x36) 서버 소켓이 부적절한 상태이며 연결 해제되었을 수 있습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NX_PACKET_POOL        my_pool;
NX_IP                 my_ip;
NX_TCP_SOCKET         server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{

   /* Simply set the semaphore to wake up the server thread. */
   tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
   /* The client has initiated a disconnect on this socket. This example
   doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{

NX_PACKET  *my_packet;
UINT       status, i;

   /* Assuming that:
     "port_12_semaphore" has already been created with an initial count
      of 0 "my_ip" has already been created and the link is enabled
     "my_pool" packet pool has already been created
   */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
                         Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                         NX_IP_TIME_TO_LIVE, 100,NX_NULL,
                         port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
       to
       each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {

        /* Get the semaphore that indicates a client connection request
           is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
           complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

       /* Check for a successful connection. */
          if (status == NX_SUCCESS)
       {
             /* Allocate a packet for the "Hello_and_Goodbye" message. */
             nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                NX_WAIT_FOREVER);

             /* Place "Hello_and_Goodbye" in the packet. */
             nx_packet_data_append(my_packet,
                      "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                      &my_pool, NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {

                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

             /* Now disconnect the server socket from the client. */
             nx_tcp_socket_disconnect(&server_socket, 200);
       }

       /* Unaccept the server socket. Note that unaccept is called even
          if disconnect or accept fails. */
       nx_tcp_server_socket_unaccept(&server_socket);

      /* Setup server socket for listening with this socket again. */
      nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten
TCP 포트에서 클라이언트 연결 수신 대기를 사용하지 않도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_server_socket_unlisten(
    NX_IP *ip_ptr, 
    UINT port);
```
### <a name="description"></a>Description

이 서비스는 지정된 TCP 포트에서 클라이언트 연결 요청 수신 대기를 사용하지 않도록 설정합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **port** 수신 대기를 사용하지 않도록 설정할 포트 번호(0-0xFFFF)입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) TCP 수신 대기를 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) 지정된 포트의 수신 대기가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PORT**(0x46) 잘못된 포트가 지정되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NX_PACKET_POOL       my_pool;
NX_IP                my_ip;
NX_TCP_SOCKET        server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{

     /* Simply set the semaphore to wake up the server thread. */
     tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{

     /* The client has initiated a disconnect on this socket. This example
        doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{

NX_PACKET *my_packet;
UINT status, i;

     /* Assuming that:
       "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
       "my_pool" packet pool has already been created
     */

     /* Create the server socket. */
     nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
                          NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                          NX_IP_TIME_TO_LIVE, 100,
                          NX_NULL, port_12_disconnect_request);

     /* Setup server listening on port 12. */
     nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                 port_12_connect_request);

     /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
     for (i = 0; i < 5; i++)
     {

         /* Get the semaphore that indicates a client connection request is
            present. */
         tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

         /* Wait for 200 ticks for the client socket connection to complete.*/
         status = nx_tcp_server_socket_accept(&server_socket, 200);

         /* Check for a successful connection. */
         if (status == NX_SUCCESS)
         {

             /* Allocate a packet for the "Hello_and_Goodbye" message. */
             nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                NX_WAIT_FOREVER);

             /* Place "Hello_and_Goodbye" in the packet. */
             nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                   sizeof("Hello_and_Goodbye"), &my_pool,
                                   NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {

                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

             /* Now disconnect the server socket from the client. */
             nx_tcp_socket_disconnect(&server_socket, 200);
          }

          /* Unaccept the server socket. Note that unaccept is called even if
             disconnect or accept fails. */
          nx_tcp_server_socket_unaccept(&server_socket);

          /* Setup server socket for listening with this socket again. */
          nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }
  
     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);

     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available
검색에 사용할 수 있는 바이트 수를 가져오기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```
### <a name="description"></a>Description

이 서비스는 지정된 TCP 소켓에서 검색에 사용할 수 있는 바이트 수를 가져옵니다. TCP 소켓은 이미 연결되어 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만들고 연결한 TCP 소켓을 가리키는 포인터입니다.
- **bytes_available** 사용할 수 있는 바이트 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 서비스가 성공적으로 실행되었습니다. 읽을 수 있는 바이트 수가 호출자에게 반환됩니다.
- **NX_NOT_CONNECTED**(0x38) 소켓이 연결된 상태가 아닙니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.
- **NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,&bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
   bytes_available. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create
TCP 클라이언트 또는 서버 소켓 만들기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, 
    ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 TCP 클라이언트 또는 서버 소켓을 만듭니다.

> [!NOTE]  
> 애플리케이션 콜백 루틴은 이 IP 인스턴스와 연결된 스레드에서 호출됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **socket_ptr** 새 TCP 소켓 제어 블록을 가리키는 포인터입니다.
- **name** 이 TCP 소켓의 애플리케이션 이름입니다.
- **type_of_service** 전송할 서비스 유형을 정의합니다. 올바른 값은 다음과 같습니다.
    - **NX_IP_NORMAL**(0x00000000)
    - **NX_IP_MIN_DELAY**(0x00100000)
    - **NX_IP_MAX_DATA**(0x00080000)
    - **NX_IP_MAX_RELIABLE**(0x00040000)
    - **NX_IP_MIN_COST**(0x00020000)
- **fragment** IP 조각화 허용 여부를 지정합니다. NX_FRAGMENT_OKAY**(0x0)가 지정되면 IP 조각화가 허용됩니다. NX_DONT_FRAGMENT(0x4000)가 지정되면 IP 조각화가 사용하지 않도록 설정됩니다.
- **time_to_live** 이 패킷이 제거되기 전까지 통과할 수 있는 라우터 수를 정의하는 8비트 값을 지정합니다. 기본값은 NX_IP_TIME_TO_LIVE로 지정합니다.
- **window_size** 이 소켓의 수신 큐에 허용되는 최대 바이트 수를 정의합니다.
- **urgent_data_callback** 수신 스트림에서 긴급 데이터가 검색될 때마다 호출되는 애플리케이션 함수입니다. 이 값이 NX_NULL이면 긴급 데이터는 무시됩니다.
- **disconnect_callback** 연결의 다른 쪽 끝에 있는 소켓이 연결을 해제할 때마다 호출되는 애플리케이션 함수입니다. 이 값이 NX_NULL이면 연결 해제 콜백 함수는 사용하지 않도록 설정됩니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) TCP 클라이언트 소켓 만들기에 성공했습니다.
- **NX_OPTION_ERROR**(0x0A) type-of-service, fragment, window size 또는 time-tolive 옵션이 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화 및 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Create a TCP client socket on the previously created IP instance,
   with normal delivery, IP fragmentation enabled, 0x80 time to
   live, a 200-byte receive window, no urgent callback routine, and
   the "client_disconnect" routine to handle disconnection initiated
   from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
                             "Client Socket",
                             NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                             0x80, 200, NX_NULL
                             client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
   to be bound. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete
TCP 소켓 삭제

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 TCP 소켓을 삭제합니다. 소켓이 여전히 바인딩되어 있거나 연결되어 있으면 서비스는 오류 코드를 반환합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓을 삭제하는 데 성공했습니다.
- **NX_NOT_CREATED**(0x27) 소켓이 만들어지지 않았습니다.
- **NX_STILL_BOUND**(0x42) 소켓이 여전히 바인딩되어 있습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect
클라이언트 및 서버 소켓 연결 해제

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 설정된 클라이언트 또는 서버 소켓 연결을 해제합니다. 먼저 요청을 거부한 후 서버 소켓 연결을 해제해야 하며 연결이 해제된 클라이언트 소켓은 다른 연결 요청에 사용할 준비가 된 상태로 남아 있습니다. 연결 해제 프로세스를 즉시 완료할 수 없는 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 연결된 클라이언트 또는 서버 소켓 인스턴스를 가리키는 포인터입니다.
- **wait_option** 연결 해제가 진행 중인 동안 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **NX_WAIT_FOREVER**(0xFFFFFFFF)
    - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 소켓 연결 해제에 성공했습니다.
- **NX_NOT_CONNECTED**(0x38) 지정된 소켓이 연결되어 있지 않습니다.
- **NX_IN_PROGRESS**(0X37) 대기 안 함으로 지정되었으므로 연결 해제가 진행 중입니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예 

### <a name="example"></a>예제 

```c
/* Disconnect from a previously established connection and wait a
   maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
   as a result of the client socket connect or the server accept) is
   disconnected. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify
TCP 연결 해제 완료 알림 콜백 함수 설치
 
### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Description

이 서비스는 소켓 연결 해제 작업이 완료된 후 호출되는 콜백 함수를 등록합니다. TCP 소켓 연결 해제 완료 콜백 함수는 옵션 ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** 가 정의된 상태로 NetX Duo가 빌드되어 있는 경우 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 연결된 클라이언트 또는 서버 소켓 인스턴스를 가리키는 포인터입니다.
- **tcp_disconnect_complete_notify** 설치할 콜백 함수입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 콜백 함수를 성공적으로 등록했습니다.
- **NX_NOT_SUPPORTED**(0x4b) 확장된 알림 기능이 NetX Duo 라이브러리에 기본 제공되지 않습니다. NX_PTR_ERROR**(0X07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
                                                  callback);
```
### <a name="see-also"></a>참고 항목

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_setnx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify
TCP 설정 알림 콜백 함수 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Description

이 서비스는 콜백 함수를 등록합니다. 이 함수는 TCP 소켓이 연결된 후 호출됩니다. TCP 소켓 설정 콜백 함수는 옵션 ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** 가 정의된 상태로 NetX Duo가 빌드되어 있는 경우 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 연결된 클라이언트 또는 서버 소켓 인스턴스를 가리키는 포인터입니다.
- **tcp_establish_notify** TCP 연결이 설정된 후 호출되는 콜백 함수입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 알림 함수를 성공적으로 설정했습니다.
- **NX_NOT_SUPPORTED** (0x4B) 확장된 알림 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다. 
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 애플리케이션에서 TCP를 사용하도록 설정하지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Set the function pointer "callback" as the notify function NetX
   Duo will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```
### <a name="see-also"></a>참고 항목

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get
TCP 소켓 활동에 대한 정보 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```
### <a name="description"></a>Description

이 서비스는 지정된 TCP 소켓 인스턴스의 TCP 소켓 활동에 대한 정보를 검색합니다.

> [!NOTE]  
> 대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓 인스턴스를 가리키는 포인터입니다.
- **tcp_packets_sent** 소켓의 송신된 총 TCP 패킷 수 대상을 가리키는 포인터입니다.
- **tcp_bytes_sent** 소켓의 송신된 총 TCP 바이트 수 대상을 가리키는 포인터입니다.
- **tcp_packets_received** 소켓의 수신된 총 TCP 패킷 수 대상을 가리키는 포인터입니다.
- **tcp_bytes_received** 소켓의 수신된 총 TCP 바이트 수 대상을 가리키는 포인터입니다.
- **tcp_retransmit_packets** 총 TCP 패킷 재전송 수 대상을 가리키는 포인터입니다.
- **tcp_packets_queued** 소켓의 큐에 대기된 총 TCP 패킷 수 대상을 가리키는 포인터입니다.
- **tcp_checksum_errors** 소켓의 체크섬 오류가 있는 총 TCP 패킷 수 대상을 가리키는 포인터입니다.
- **tcp_socket_state** 소켓의 현재 상태 대상을 가리키는 포인터입니다.
- **tcp_transmit_queue_depth** 여전히 큐에서 ACK를 대기 중인 총 전송 패킷 수 대상을 가리키는 포인터입니다.
- **tcp_transmit_window** 현재 전송 창 크기 대상을 가리키는 포인터입니다.
- **tcp_receive_window** 현재 수신 창 크기 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) TCP 소켓 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다. 
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Retrieve TCP socket information from previously created
   socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
                                &tcp_packets_sent,
                                &tcp_bytes_sent,
                                &tcp_packets_received,
                                &tcp_bytes_received,
                                &tcp_retransmit_packets,
                                &tcp_packets_queued,
                                &tcp_checksum_errors,
                                &tcp_socket_state,
                                &tcp_transmit_queue_depth,
                                &tcp_transmit_window,
                                &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get
소켓의 MSS 가져오기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```
### <a name="description"></a>Description

이 서비스는 지정된 소켓의 로컬 MSS(최대 세그먼트 크기)를 검색합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 소켓을 가리키는 포인터입니다.
- **mss** MSS 반환 대상입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) MSS를 가져오는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 또는 MSS 대상 포인터입니다.
- **NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.

### <a name="allowed-from"></a>허용 위치

초기화 및 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
   socket's current MSS value. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get
피어 TCP 소켓의 MSS 가져오기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *mss);
```
### <a name="description"></a>Description

이 서비스는 피어 소켓에서 보급한 MSS(최대 세그먼트 크기)를 검색합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만들고 연결한 소켓을 가리키는 포인터입니다.
- **mss** MSS를 반환하는 대상입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 피어 MSS를 가져오는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 또는 MSS 대상 포인터입니다.
- **NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
   socket peer’s advertised MSS value. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set
소켓의 MSS 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```
### <a name="description"></a>Description

이 서비스는 지정된 소켓의 MSS(최대 세그먼트 크기)를 설정합니다. MSS 값은 네트워크 인터페이스 IP MTU 내에 있어야 하며 IP 및 TCP 헤더 공간이 허용되어야 합니다.

TCP 소켓이 연결 프로세스를 시작하기 전에 이 서비스를 사용해야 합니다. TCP 연결이 설정된 후 이 서비스를 사용하면 새 값이 연결에 영향을 주지 않습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 소켓을 가리키는 포인터입니다.
- **mss** 설정할 MSS 값입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) MSS 설정에 성공했습니다.
- **NX_SIZE_ERROR**(0x09) 지정된 MSS 값이 너무 큽니다.
- **NX_NOT_CONNECTED**(0x38) TCP 연결이 설정되지 않았습니다. 
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.

### <a name="allowed-from"></a>허용 위치

초기화 및 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get
피어 TCP 소켓에 대한 정보 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address,
    ULONG *peer_port);
```
### <a name="description"></a>Description

이 서비스는 IPv4 네트워크를 통해 연결된 TCP 소켓의 피어 IP 주소 및 포트 정보를 검색합니다. IPv6 네트워크도 지원하는 동등한 서비스는 ***nxd_tcp_socket_peer_info_get*** 입니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓을 가리키는 포인터입니다.
- **peer_ip_address** 피어 IP 주소 대상을 가리키는 포인터입니다(호스트 바이트 순서).
- **peer_port** 피어 포트 번호 대상을 가리키는 포인터입니다(호스트 바이트 순서).

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS** (0x00) 서비스가 성공적으로 실행되었습니다. 피어 IP 주소와 포트 번호는 호출자에게 반환됩니다.
- **NX_NOT_CONNECTED**(0x38) 소켓이 연결된 상태가 아닙니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.
- **NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
                                     &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_queue_depth_notify_set"></a>nx_tcp_socket_queue_depth_notify_set
TCP 전송 큐 알림 함수 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_queue_depth_notify_set(
              NX_TCP_SOCKET *socket_ptr,
              VOID(*tcp_socket_queue_depth_notify)(NX_TCP_SOCKET *));
```
### <a name="description"></a>Description

이 서비스는 애플리케이션에서 지정한 전송 큐 크기 업데이트 알림 함수를 설정합니다. 이 함수는 지정된 소켓이 큐 크기가 더 이상 제한을 초과하지 않도록 전송 큐에서 패킷을 해제했음을 확인할 때마다 호출됩니다. 큐 크기로 인해 전송 시 애플리케이션이 차단되는 경우 콜백 함수는 전송을 다시 시작할 수 있는 애플리케이션에 대한 알림으로 사용됩니다. 이 서비스는 ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY*** 옵션이 정의된 상태로 Netx Duo 라이브러리가 빌드된 경우에만 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수 

- **socket_ptr** 소켓 구조를 가리키는 포인터입니다. 
- **tcp_socket_queue_depth_notify** 설치할 알림 함수입니다.

### <a name="return-values"></a>반환 값 

- **FX_SUCCESS**(0x00) 알림 함수를 설치했습니다.
- **NX_NOT_SUPPORTED**(0x4B) TCP 소켓 큐 크기 알림 기능이 Netx Duo 라이브러리에 기본 제공되지 않습니다.
- **NX_PTR_ERROR**(0x07) 소켓 제어 블록 또는 알림 함수에 대한 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
VOID tcp_socket_queue_depth_notify(NX_TCP_SOCKET *socket_ptr)
{
   /* Notify the application to resume sending. */

}
/* Install the TCP transmit queue notify function .*/
status = nxd_tcp_socket_queue_depth_notify_set(&tcp_socket,
                                  tcp_socket_queue_depth_notify);

/* If status == NX_SUCCESS, the callback function is successfully
   installed. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive
TCP 소켓에서 데이터 수신

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 지정된 소켓에서 TCP 데이터를 수신합니다. 지정된 소켓에 큐에 대기된 데이터가 없으면 제공된 대기 옵션에 따라 호출자가 일시 중단됩니다.

> [!CAUTION]  
> NX_SUCCESS가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 해당 패킷을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓 인스턴스를 가리키는 포인터입니다.
- **packet_ptr** TCP 패킷 포인터를 가리키는 포인터입니다.
- **wait_option** 현재 이 소켓에 큐에 대기된 데이터가 없는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **NX_WAIT_FOREVER**(0xFFFFFFFF)
    - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 소켓 데이터 수신에 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 아직 바인딩되지 않았습니다.
- **NX_NO_PACKET**(0x01) 수신된 데이터가 없습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_NOT_CONNECTED**(0x38) 소켓이 더 이상 연결되어 있지 않습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 또는 반환 패킷 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Receive a packet from the previously created and connected TCP
   client socket. If no packet is available, wait for 200 timer
   ticks before giving up. */
status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);

/* If status is NX_SUCCESS, the received packet is pointed to by
   "packet_ptr". */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify
수신된 패킷을 애플리케이션에 알림

### <a name="prototype"></a>프로토타입   

```c
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr, 
    VOID (*tcp_receive_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Description 

이 서비스는 애플리케이션에서 지정한 콜백 함수를 사용하여 수신 알림 함수 포인터를 구성합니다. 그러면 소켓에 하나 이상의 패킷이 수신될 때마다 이 콜백 함수가 호출됩니다. NX_NULL 포인터를 제공하면 알림 함수를 사용하지 않도록 설정합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** TCP 소켓을 가리키는 포인터입니다.
- **tcp_receive_notify** 소켓에 하나 이상의 패킷이 수신되면 호출되는 애플리케이션 콜백 함수 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 소켓 수신 알림에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Setup a receive packet callback function for the "client_socket"
   socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
                                      my_receive_notify);

/* If status is NX_SUCCESS, NetX Duo will call the function named
   "my_receive_notify" whenever one or more packets are received for
   "client_socket". */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send
TCP 소켓을 통해 데이터 송신

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 이전에 연결된 TCP 소켓을 통해 TCP 데이터를 송신합니다. 마지막으로 보급된 수신기 창 크기가 이 요청 미만이면 지정된 대기 옵션에 따라 선택적으로 서비스가 일시 중단됩니다. 이 서비스는 MSS를 초과하는 패킷 데이터가 IP 계층으로 송신되지 않도록 보장합니다. 

> [!WARNING]  
> 오류가 반환되지 않는 경우 애플리케이션은 이 호출 후에 패킷을 해제하면 안 됩니다. 해제하면 네트워크 드라이버가 전송 후에도 패킷을 해제하려고 하므로 예측할 수 없는 결과가 발생합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 연결된 TCP 소켓 인스턴스를 가리키는 포인터입니다.
- **packet_ptr** TCP 데이터 패킷 포인터입니다.
- **wait_option** 요청이 수신기 창 크기를 초과하는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **NX_WAIT_FOREVER**(0xFFFFFFFF)
    - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓 송신에 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.
- **NX_NO_INTERFACE_ADDRESS**(0x50) 적절한 송신 인터페이스를 찾을 수 없습니다.
- **NX_NOT_CONNECTED**(0x38) 소켓이 더 이상 연결되어 있지 않습니다.
- **NX_WINDOW_OVERFLOW**(0x39) 요청이 보급된 수신기 창 크기(바이트)를 초과합니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_INVALID_PACKET**(0x12) 패킷이 할당되지 않았습니다.
- **NX_TX_QUEUE_DEPTH**(0x49) 최대 전송 큐 크기에 도달했습니다.
- **NX_OVERFLOW**(0x03) 패킷 뒤에 추가 포인터가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_UNDERFLOW**(0x02) 패킷 앞에 추가 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Send a packet out on the previously created and connected TCP
   socket. If the receive window on the other side of the connection
   is less than the packet size, wait 200 timer ticks before giving
   up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait
TCP 소켓이 특정 상태가 될 때까지 대기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 소켓이 원하는 상태가 될 때까지 대기합니다. 소켓이 원하는 상태가 아닌 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 연결된 TCP 소켓 인스턴스를 가리키는 포인터입니다.
- **desired_state** 원하는 TCP 상태입니다. 유효한 TCP 소켓 상태는 다음과 같이 정의됩니다.
    - **NX_TCP_CLOSED**(0x01)
    - **NX_TCP_LISTEN_STATE**(0x02)
    - **NX_TCP_SYN_SENT**(0x03)
    - **NX_TCP_SYN_RECEIVED**(0x04)
    - **NX_TCP_ESTABLISHED**(0x05)
    - **NX_TCP_CLOSE_WAIT**(0x06)
    - **NX_TCP_FIN_WAIT_1**(0x07)
    - **NX_TCP_FIN_WAIT_2**(0x08)
    - **NX_TCP_CLOSING**(0x09)
    - **NX_TCP_TIMED_WAIT**(0x0A)
    - **NX_TCP_LAST_ACK**(0x0B)
- **wait_option** 요청된 상태가 아닌 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFF)

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 상태 대기에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_NOT_SUCCESSFUL**(0x43) 지정된 대기 시간 내에 해당 상태가 되지 않았습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_OPTION_ERROR**(0x0A) 원하는 소켓 상태가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Wait 300 timer ticks for the previously created socket to enter
   the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
                                  NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
   state! */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback
시간이 지정된 대기 상태 콜백 설치

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Description

이 서비스는 TCP 소켓이 시간이 지정된 대기 상태인 경우 호출되는 콜백 함수를 등록합니다. 이 서비스를 사용하려면 옵션 ***NX_ENABLE_EXTENDED_NOTIFY*** 가 정의된 NetX Duo 라이브러리가 빌드되어 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 연결된 클라이언트 또는 서버 소켓 인스턴스를 가리키는 포인터입니다.
- **tcp_timed_wait_callback** 시간이 지정된 대기 콜백 함수입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 콜백 함수 소켓을 성공적으로 등록했습니다.
- **NX_NOT_SUPPORTED**(0x4B) 확장 알림 기능을 사용하도록 설정하지 않은 상태로 NetX Duo 라이브러리가 빌드되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure
소켓의 전송 매개 변수 구성

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```
### <a name="description"></a>Description

이 서비스는 지정된 TCP 소켓의 다양한 전송 매개 변수를 구성합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** TCP 소켓을 가리키는 포인터입니다.
- **max_queue_depth** 전송을 위해 큐에 대기될 수 있는 최대 패킷 수입니다.
- **timeout** 패킷을 다시 송신하기 전에 ACK를 기다리는 ThreadX 타이머 틱 수입니다.
- **max_retries** 허용되는 최대 재시도 수입니다.
- **timeout_shift** 각 후속 재시도에 대한 시간 제한을 변경하는 값입니다. 값이 0이면 이어지는 재시도 간 시간 제한이 동일합니다. 값이 1이면 재시도 간 시간 제한이 두 배가 됩니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 전송 소켓 구성에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_OPTION_ERROR**(0x0a) 잘못된 큐 깊이 옵션입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Configure the "client_socket" for a maximum transmit queue depth of
   12, 100 tick timeouts, a maximum of 20 retries, and a timeout double
   on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,12,100,20,1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
   configured. */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set
애플리케이션에 창 크기 업데이트 알림

### <a name="prototype"></a>프로토타입  

```c
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_window_update_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Description

이 서비스는 소켓 창 업데이트 콜백 루틴을 설치합니다. 지정된 소켓이 원격 호스트 창 크기 증가를 나타내는 패킷을 수신할 때마다 자동으로 이 루틴이 호출됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓을 가리키는 포인터입니다.
- **tcp_window_update_notify** 창 크기가 변경되면 호출되는 콜백 루틴입니다. 값이 NULL이면 창 변경 업데이트를 사용하지 않도록 설정합니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 콜백 루틴이 소켓에 설치되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.
- **NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Set the function pointer to the windows update callback after creating the
   socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
                                                my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(&data_socket)
{

/* Process update on increase TCP transmit socket window size. */
   return;
}
```
### <a name="see-also"></a>참고 항목

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable
NetX의 UDP 구성 요소를 사용하도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 NetX Duo의 UDP(User Datagram Protocol) 구성 요소를 사용하도록 설정합니다. 사용하도록 설정하면 애플리케이션에서 UDP 데이터그램을 송신하고 수신할 수 있습니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) UDP를 사용하도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_ALREADY_ENABLED**(0x15) 이 구성 요소는 이미 사용하도록 설정되어 있습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
   instance. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find
사용할 수 있는 다음 UDP 포트 찾기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```
### <a name="description"></a>Description

이 서비스는 애플리케이션 제공 포트 번호에서 시작하여 사용 가능한 UDP 포트(바인딩되지 않은 포트)를 찾습니다. 검색에서 최대 포트 값인 0xFFFF에 도달하면 검색 논리가 래핑됩니다. 검색에 성공하면 free_port_ptr이 가리키는 변수에 사용 가능한 포트가 반환됩니다.

> [!WARNING]  
> 이 서비스는 다른 스레드에서 호출될 수 있으며 동일한 포트를 반환할 수 있습니다. 이러한 경합 상태를 방지하기 위해 애플리케이션은 이 서비스 및 실제 소켓 바인딩에 뮤텍스 보호가 적용되도록 할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **port** 검색을 시작할 포트 번호(1-0xFFFF)입니다.
- **free_port_ptr** 사용 가능한 포트 반환 변수 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 사용 가능한 포트를 찾는 데 성공했습니다.
- **NX_NO_FREE_PORTS**(0x45) 사용 가능한 포트를 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PORT**(0x46) 지정된 포트 번호가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Locate a free UDP port, starting at port 12, on a previously
   created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
   free UDP port on the IP instance. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get
UDP 활동에 대한 정보 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 UDP 활동에 대한 정보를 검색합니다.

> [!IMPORTANT]  
> 대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **udp_packets_sent** 송신된 총 UDP 패킷 수 대상을 가리키는 포인터입니다.
- **udp_bytes_sent** 송신된 총 UDP 바이트 수 대상을 가리키는 포인터입니다.
- **udp_packets_received** 수신된 총 UDP 패킷 수 대상을 가리키는 포인터입니다.
- **udp_bytes_received** 수신된 총 UDP 바이트 수 대상을 가리키는 포인터입니다.
- **udp_invalid_packets** 잘못된 총 UDP 패킷 수 대상을 가리키는 포인터입니다.
- **udp_receive_packets_dropped** 삭제된 총 UDP 수신 패킷 수 대상을 가리키는 포인터입니다.
- **udp_checksum_errors** 체크섬 오류가 있는 총 UDP 패킷 수 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) UDP 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드 및 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Retrieve UDP information from previously created IP Instance
   ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
                         &udp_bytes_sent,
                         &udp_packets_received,
                         &udp_bytes_received,
                         &udp_invalid_packets,
                         &udp_receive_packets_dropped,
                         &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract
UDP 패킷에서 네트워크 매개 변수 추출

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```
### <a name="description"></a>Description

이 서비스는 수신 인터페이스의 수신된 패킷에서 IPv4 주소, 피어 포트 번호, 프로토콜 유형(이 서비스는 항상 UDP 유형을 반환함) 같은 네트워크 매개 변수를 추출합니다. IPv4 또는 IPv6 네트워크에서 들어오는 패킷에 대한 정보를 얻기 위해 애플리케이션은 ***nxd_udp_packet_info_extract.*** 서비스를 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 패킷을 가리키는 포인터입니다.
- **ip_address** 송신기 IP 주소를 가리키는 포인터입니다.
- **protocol** 프로토콜(UDP)을 가리키는 포인터입니다.
- **port** 송신기 포트 번호를 가리키는 포인터입니다.
- **interface_index** 수신 인터페이스 인덱스를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 패킷 인터페이스 데이터를 성공적으로 추출했습니다.
- **NX_INVALID_PACKET**(0x12) 패킷에 IPv4 프레임이 포함되어 있지 않습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터 입력입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract(packet_ptr, &ip_address,
                                     &protocol, &port,
                                     &interface_index);

/* If status is NX_SUCCESS packet data was successfully
   retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind
UDP 소켓을 UDP 포트에 바인딩

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 이전에 만든 UDP 소켓을 지정된 UDP 포트에 바인딩합니다. 유효한 UDP 소켓 범위는 0에서 0xFFFF까지입니다. 요청된 포트 번호가 다른 소켓에 바인딩되어 있으면 이 서비스는 지정된 시간 동안 해당 소켓이 해당 포트 번호에서 바인딩을 해제할 때까지 기다립니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스를 가리키는 포인터입니다.
- **port** 바인딩할 포트 번호**(1-0xFFFF)입니다. 포트 번호가 NX_ANY_PORT**(0x0000)인 경우 IP 인스턴스는 가능한 다음 포트를 검색하여 바인딩에 사용합니다.
- **wait_option** 포트가 이미 다른 소켓에 바인딩되어 있는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **NX_WAIT_FOREVER**(0xFFFFFFFF)
    - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 소켓 바인딩에 성공했습니다.
- **NX_ALREADY_BOUND**(0x22) 이 소켓은 다른 포트에 이미 바인딩되어 있습니다.
- **NX_PORT_UNAVAILABLE**(0x23) 포트가 이미 다른 소켓에 바인딩되어 있습니다.
- **NX_NO_FREE_PORTS**(0x45) 사용 가능한 포트가 없습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_INVALID_PORT**(0x46) 잘못된 포트가 지정되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Bind the previously created UDP socket to port 12 on the
   previously created IP instance. If the port is already bound,
   wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
   port 12.*/
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available
검색에 사용할 수 있는 바이트 수를 가져오기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```
### <a name="description"></a>Description

이 서비스는 지정된 UDP 소켓에서 수신용으로 사용할 수 있는 바이트 수를 검색합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓을 가리키는 포인터입니다.
- **bytes_available** 사용할 수 있는 바이트 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 사용할 수 있는 바이트 검색에 성공했습니다.
- **NX_NOT_SUCCESSFUL**(0x43) 소켓이 포트에 바인딩되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.
- **NX_NOT_ENABLED**(0x14) UDP 기능이 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket,
                                       &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
   retrieved.*/
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable
UDP 소켓 체크섬을 사용하지 않도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 UDP 소켓에서 패킷을 송신하고 수신하는 데 체크섬 논리를 사용하지 않도록 설정합니다. 체크섬 논리를 사용하지 않도록 설정하면 이 소켓을 통해 송신되는 모든 패킷의 UDP 헤더 체크섬 필드에 0값이 로드됩니다. UDP 헤더의 체크섬 값이 0이면 해당 패킷에 대해 체크섬이 계산되지 않음을 수신기에서 알 수 있습니다.

또한, **NX_DISABLE_UDP_RX_CHECKSUM** 및 **NX_DISABLE_UDP_TX_CHECKSUM** 이 각각 정의된 경우에도 UDP 패킷을 수신하고 송신할 때 아무런 영향을 주지 않습니다.

IPv6의 경우 UDP 체크섬이 필수이므로 이 서비스는 IPv6 네트워크의 패킷에 영향을 주지 않습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 소켓 체크섬을 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 바인딩되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
   calculated. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable
UDP 소켓 체크섬을 사용하도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 UDP 소켓에서 패킷을 송신하고 수신하는 데 체크섬 논리를 사용하도록 설정합니다. 체크섬은 전체 UDP 데이터 영역 및 의사 IP 헤더에 적용됩니다.

또한, **NX_DISABLE_UDP_RX_CHECKSUM** 및 **NX_DISABLE_UDP_TX_CHECKSUM** 이 각각 정의된 경우에도 UDP 패킷을 수신하고 송신할 때 아무런 영향을 주지 않습니다.

이 서비스는 IPv6 네트워크의 패킷에 영향을 주지 않습니다. UDP 체크섬은 IPv6에서 필수입니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 소켓 체크섬을 사용하도록 설정하는 데 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 바인딩되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
   calculated. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_create"></a>nx_udp_socket_create
UDP 소켓 만들기

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, 
    CHAR *name,
    ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG queue_maximum);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 UDP 소켓을 만듭니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **socket_ptr** 새 UDP 소켓 제어 블록을 가리키는 포인터입니다.
- **name** 이 UDP 소켓의 애플리케이션 이름입니다.
- **type_of_service** 전송할 서비스 유형을 정의합니다. 올바른 값은 다음과 같습니다.
    - **NX_IP_NORMAL**(0x00000000)
    - **NX_IP_MIN_DELAY**(0x00100000)
    - **NX_IP_MAX_DATA**(0x00080000)
    - **NX_IP_MAX_RELIABLE**(0x00040000)
    - **NX_IP_MIN_COST**(0x00020000)
- **fragment** IP 조각화 허용 여부를 지정합니다. NX_FRAGMENT_OKAY(0x0)가 지정되면 IP 조각화가 허용됩니다. NX_DONT_FRAGMENT(0x4000)가 지정되면 IP 조각화가 사용하지 않도록 설정됩니다.
- **time_to_live** 이 패킷이 제거되기 전까지 통과할 수 있는 라우터 수를 정의하는 8비트 값을 지정합니다. 기본값은 NX_IP_TIME_TO_LIVE로 지정합니다.
- **queue_maximum** 이 소켓에 대해 큐에 대기될 수 있는 최대 UDP 데이터그램 수를 정의합니다. 큐 제한에 도달하면 수신된 모든 새 패킷의 가장 오래된 UDP 패킷이 해제됩니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) UDP 소켓 만들기에 성공했습니다.
- **NX_OPTION_ERROR**(0x0A) type-of-service, fragment 또는 time-to-live 옵션이 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화 및 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
                              NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80,
                              30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
   is ready for binding. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete
UDP 소켓 삭제

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Description

이 서비스는 이전에 만든 UDP 소켓을 삭제합니다. 소켓이 포트에 바인딩된 경우 먼저 소켓 바인딩을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 소켓을 삭제하는 데 성공했습니다.
- **NX_STILL_BOUND**(0x42) 소켓이 여전히 바인딩되어 있습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
   been deleted. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get
UDP 소켓 활동에 대한 정보 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```
### <a name="description"></a>Description

이 서비스는 지정된 UDP 소켓 인스턴스의 UDP 소켓 활동에 대한 정보를 검색합니다.

> [!IMPORTANT]  
> 대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스를 가리키는 포인터입니다.
- **udp_packets_sent** 소켓의 송신된 총 UDP 패킷 수 대상을 가리키는 포인터입니다.
- **udp_bytes_sent** 소켓의 송신된 총 UDP 바이트 수 대상을 가리키는 포인터입니다.
- **udp_packets_received** 소켓의 수신된 총 UDP 패킷 수 대상을 가리키는 포인터입니다.
- **udp_bytes_received** 소켓의 수신된 총 UDP 바이트 수 대상을 가리키는 포인터입니다.
- **udp_packets_queued** 소켓의 큐에 대기된 총 UDP 패킷 수 대상을 가리키는 포인터입니다.
- **udp_receive_packets_dropped** 큐 크기 초과로 인해 삭제된, 소켓의 총 UDP 수신 패킷 수 대상을 가리키는 포인터입니다.
- **udp_checksum_errors** 소켓의 체크섬 오류가 있는 총 UDP 패킷 수 대상을 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) UDP 소켓 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드 및 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
                                &udp_packets_sent,
                                &udp_bytes_sent,
                                &udp_packets_received,
                                &udp_bytes_received,
                                &udp_queued_packets,
                                &udp_receive_packets_dropped,
                                &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get
UDP 소켓에 바인딩된 포트 번호 선택

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_port_get(
    NX_UDP_SOCKET *socket_ptr,
    UINT *port_ptr);
```
### <a name="description"></a>Description

이 서비스는 소켓에 연결된 포트 번호를 검색합니다. 소켓이 바인딩될 때 NX_ANY_PORT가 지정된 경우 NetX Duo에서 할당한 포트를 찾는 데 유용합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스를 가리키는 포인터입니다.
- **port_ptr** 반환 포트 번호 대상을 가리키는 포인터입니다. 유효한 포트 번호는 (1-0xFFFF)입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 소켓 바인딩에 성공했습니다.
- **NX_NOT_BOUND**(0x24) 이 소켓은 포트에 바인딩되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터 또는 포트 반환 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
   socket is bound to. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive
UDP 소켓에서 데이터그램 수신

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 지정된 소켓에서 UDP 데이터그램을 수신합니다. 지정된 소켓에 큐에 대기된 데이터그램이 없는 경우 제공된 대기 옵션에 따라 호출자가 일시 중단됩니다.

> [!CAUTION]  
> NX_SUCCESS가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 해당 패킷을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스를 가리키는 포인터입니다.
- **packet_ptr** UDP 데이터그램 패킷 포인터를 가리키는 포인터입니다.
- **wait_option** 현재 이 소켓에 큐에 대기된 데이터그램이 없는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **NX_WAIT_FOREVER**(0xFFFFFFFF)
    - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 소켓 수신에 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.
- **NX_NO_PACKET**(0x01) 수신할 UDP 데이터그램이 없습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_PTR_ERROR**(0x07) 소켓 또는 패킷 반환 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Receive a packet from a previously created and bound UDP socket.
   If no packets are currently available, wait for 500 timer ticks
   before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
   packet_ptr. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify
수신된 각 패킷에 대해 애플리케이션에 알림

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)(NX_UDP_SOCKET *socket_ptr));
```
### <a name="description"></a>Description 

이 서비스는 애플리케이션에서 지정한 콜백 함수를 가리키는 수신 알림 함수 포인터를 설정합니다. 그러면 소켓에 패킷이 수신될 때마다 이 콜백 함수가 호출됩니다. NX_NULL 포인터를 제공하면 수신 알림 함수를 사용하지 않도록 설정합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** UDP 소켓을 가리키는 포인터입니다.
- **udp_receive_notify** 소켓에 패킷이 수신되면 호출되는 애플리케이션 콜백 함수 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NXD_MQTT_SUCCESS**(0x00) 소켓 수신 알림 함수를 설정했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머 및 ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Setup a receive packet callback function for the "udp_socket"
   socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
                                      my_receive_notify);

/* If status is NX_SUCCESS, NetX Duo will call the function named
   "my_receive_notify" whenever a packet is received for
   "udp_socket". */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send
UDP 데이터그램 송신

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address, 
    UINT port);
```
### <a name="description"></a>Description

이 서비스는 IP4 네트워크에 대해 이전에 만들고 바인딩한 UDP 소켓을 통해 UDP 데이터그램을 송신합니다. NetX Duo는 대상 IP 주소를 기반으로 하여 원본 주소로 적합한 로컬 IP 주소를 찾습니다. 특정 인터페이스와 원본 IP 주소를 지정하려면 애플리케이션에서 **nxd_udp_socket_source_send** 서비스를 사용해야 합니다.

이 서비스는 UDP 데이터그램이 성공적으로 송신되었는지 여부에 관계없이 즉시 반환됩니다. NetX Duo(IPv4/IPv6)의 동급 서비스는 ***nxd_udp_socket_send*** 입니다.

소켓은 로컬 포트에 바인딩되어 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스를 가리키는 포인터입니다.
- **packet_ptr** UDP 데이터그램 패킷 포인터입니다.
- **ip_address** 대상 IP 주소입니다.
- **port** 1에서 0xFFFF 사이의 유효한 대상 포트 번호입니다(호스트 바이트 순서).

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) UDP 소켓 송신에 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.
- **NX_NO_INTERFACE_ADDRESS**(0x50) 적절한 송신 인터페이스를 찾을 수 없습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 서버 IP 주소입니다.
- **NX_UNDERFLOW**(0x02) 패킷에 UDP 헤더를 위한 공간이 부족합니다.
- **NX_OVERFLOW**(0x03) 패킷 뒤에 추가 포인터가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) UDP가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PORT**(0x46) 포트 번호가 유효한 범위 내에 있지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
                            server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
   the packet out the UDP socket to its peer. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_source_send"></a>nx_udp_socket_source_send
UDP 소켓을 통해 데이터그램 송신

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_source_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 주소를 원본 주소로 사용하여 네트워크 인터페이스에서 이전에 만들고 바인딩한 UDP 소켓을 통해 UDP 데이터그램을 송신합니다. 이 서비스는 UDP 데이터그램이 성공적으로 송신되었는지 여부에 관계없이 즉시 반환됩니다. ***nxd_udp_socket_source_send*** 은 IPv4 및 IPv6 네트워크 둘 다에 작동합니다.

### <a name="parameters"></a>매개 변수 

- **socket_ptr** 패킷을 전송할 소켓입니다.
- **packet_ptr** 전송할 패킷을 가리키는 포인터입니다.
- **ip_address** 패킷을 송신할 대상 IP 주소입니다.
- **port** 대상 포트입니다.
- **address_index** 패킷을 송신할 인터페이스와 연결된 주소 인덱스입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷이 성공적으로 송신되었습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 포트에 바인딩되지 않았습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) UDP 처리가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.
- **NX_OVERFLOW**(0x03) 잘못된 패킷 뒤에 추가 포인터입니다.
- **NX_UNDERFLOW**(0x02) 잘못된 패킷 앞에 추가 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_INVALID_INTERFACE**(0x4C) 잘못된 주소 인덱스입니다.
- **NX_INVALID_PORT**(0x46) 포트 번호가 최대 포트 번호를 초과합니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
   interface at index 1 in the IP task interface list. */
status = nx_udp_socket_source_send(socket_ptr, packet_ptr,
                                   destination_ip, 80,
                                   ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind
UDP 포트에서 UDP 소켓 바인딩 해제

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Description

이 서비스는 UDP 소켓 및 UDP 포트 간 바인딩을 해제합니다. 수신 큐에 저장된 모든 수신된 패킷은 바인딩 해제 작업의 일부로 해제됩니다.

다른 소켓을 바인딩 해제된 포트에 바인딩하려고 대기 중인 다른 스레드가 있는 경우 첫 번째 일시 중단된 스레드가 새로 바인딩 해제된 포트에 바인딩됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 소켓을 바인딩 해제하는 데 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스 호출자가 잘못되었습니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
   unbound. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract
UDP 데이터그램에서 IP 및 송신 포트 추출

### <a name="prototype"></a>프로토타입  

```c
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, 
    UINT *port);
```
### <a name="description"></a>Description

이 서비스는 제공된 UDP 데이터그램의 IP 및 UDP 헤더에서 송신기 IP 및 포트 번호를 추출합니다. ***Nxd_udp_source_extract*** 서비스는 IPv4 또는 IPv6 네트워크의 패킷에 작동합니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** UDP 데이터그램 패킷 포인터입니다.
- **ip_address** 반환 IP 주소 변수를 가리키는 유효한 포인터입니다.
- **port** 반환 포트 변수를 가리키는 유효한 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 원본 IP/포트 추출에 성공했습니다.
- **NX_INVALID_PACKET**(0x12) 제공된 패킷이 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 패킷이나 IP 또는 포트 대상이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Extract the IP and port information from the sender of the UPD packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address, &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has been stored
   in sender_ip_address and sender_port respectively.*/
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_icmp_enable"></a>nxd_icmp_enable
ICMPv4 및 ICMPv6 서비스를 사용하도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_icmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 ICMPv4 및 ICMPv6 서비스를 모두 사용하도록 설정하며 IP 인스턴스를 만든 후에만 호출할 수 있습니다. IPv6를 사용하도록 설정하기 전이나 후에 이 서비스를 사용하도록 설정할 수 있습니다(nxd_ipv6_enable 참조). ICMPv4 서비스에는 에코 요청/응답이 포함됩니다. ICMPv6 서비스에는 에코 요청/응답, 네트워크 환경 검색, 중복 주소 검색, 라우터 검색, 상태 비저장 주소 자동 구성이 포함됩니다. NetX에서 IPv4에 해당하는 서비스는 nx_icmp_enable입니다.

> [!NOTE] 
> ICMPv6를 사용하도록 설정하기 전에 IPv6 주소를 수동으로 구성하면 수동으로 구성된 IPv6에는 중복 주소 검색 프로세스가 적용되지 않습니다.

*nx_icmp_enable* 은 IPv4 작업에 대해서만 ICMP 서비스를 시작합니다. ICMPv6 서비스를 사용하는 애플리케이션은 nx_icmp_enable 대신 nxd_icmp_enable을 사용해야 합니다.

IPv6 라우터 요청 및 IPv6 상태 비저장 자동 주소 구성을 활용하려면 ICMPv6를 사용하도록 설정해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0X00) ICMP 서비스를 사용하도록 설정했습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Enable ICMP on the IP instance. */
status = nxd_icmp_enable(&ip_0);

/* A status return of NX_SUCCESS indicates that the IP instance is
   enabled for ICMP services. */
```
### <a name="see-also"></a>참고 항목

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmp_ping"></a>nxd_icmp_ping
ICMPv4 또는 ICMPv6 에코 요청 수행

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_icmp_ping(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *ip_address,
    CHAR *data_ptr, 
    ULONG data_size,
    NX_PACKET **response_ptr, 
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 적절한 실제 인터페이스를 통해 ICMP 에코 요청 패킷을 전송하고 대상 호스트에서 에코 응답을 기다립니다. NetX Duo는 대상 주소를 기준으로 ping 메시지를 전송할 적절한 인터페이스를 결정합니다. 애플리케이션은 ***nxd_icmp_source_ping*** 서비스를 사용하여 패킷 전송에 사용할 실제 인터페이스와 정확한 원본 IP 주소를 지정해야 합니다.

IP 인스턴스를 만들고 ICMPv4/ICMPv6 서비스를 사용하도록 설정해야 합니다(***nxd_icmp_enable*** 참조).

> [!WARNING]  
> NX_SUCCESS가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 이 패킷을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 인스턴스를 가리키는 포인터입니다.
- **ip_address** ping할 대상 IP 주소입니다(호스트 바이트 순서).
- **data_ptr** ping 패킷 데이터 영역을 가리키는 포인터입니다.
- **data_size** ping 데이터의 바이트 수입니다.
- **response_ptr** 응답 패킷 포인터를 가리키는 포인터입니다.
- **wait_option** 응답 대기 시간입니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **틱 단위의 시간 제한**(0x00000001~) 
    - **NX_WAIT_FOREVER**(0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) ping을 성공적으로 송수신했습니다.
- **NX_NOT_SUPPORTED**(0x4B) IPv6를 사용하지 않도록 설정했습니다.
- **NX_OVERFLOW**(0x03) ping 데이터가 패킷 페이로드를 초과합니다.
- **NX_NO_RESPONSE**(0x29) 대상 호스트가 응답하지 않았습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort에 의해 중단되었습니다.
- **NX_NO_INTERFACE_ADDRESS**(0x50) 적절한 송신 인터페이스를 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 응답 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0X14) IP 또는 ICMP 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 입력 IP 주소가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* The following two examples illustrate how to use this API to send
   ping packets to IPv6 or IPv4 destinations. */

/* The first example: Send a ping packet to an IPv6 host
   2001:1234:5678::1 */
   
/* Declare variable address to hold the destination address. */
NXD_ADDRESS ip_address;

char *buffer = “abcd”;
UINT prefix_length = 10;

/* Set the IPv6 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]    = 0x20011234;
ip_address.nxd_ip_address.v6[1]    = 0x56780000;
ip_address.nxd_ip_address.v6[2]    = 0;
ip_address.nxd_ip_address.v6[3]    = 1;

status = nxd_icmp_ping(&ip_0, &ip_address, buffer,
                       strlen(buffer),&response_ptr,
                       NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply has been
   received from IP address 2001:1234:5678::1 and the response
   packet is contained in the packet pointed to by response_ptr.It
   should have the same “abcd” four bytes of data. */

/* The second example: Send a ping packet to an IPv4 host 1.2.3.4 */

/* Program the IPv4 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4[0]    = 0x01020304;

status = nxd_icmp_ping(&ip_0, &ip_address, buffer,
                       strlen(buffer),&response_ptr, 10);

/* A return value of NX_SUCCESS indicates a ping reply was received
   from IP address 1.2.3.4 and the response packet is contained in
   the packet pointed to by response_ptr. It should have the same
   “abcd” four bytes of data. */
```
### <a name="see-also"></a>참고 항목

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmp_source_ping"></a>nxd_icmp_source_ping
ICMPv4 또는 ICMPv6 에코 요청 수행

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_icmp_source_ping(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *ip_address,
    UINT address_index,
    CHAR *data_ptr, 
    ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 지정된 IPv4 또는 IPv6 주소 인덱스를 사용하여 ICMP 에코 요청 패킷을 전송하며, 원본 주소가 연결된 네트워크 인터페이스를 통해 대상 호스트의 에코 응답을 대기합니다. 이 서비스는 IPv4 및 IPv6 주소 둘 다에서 작동합니다. 매개 변수 *address_index* 는 사용할 원본 IPv4 또는 IPv6 주소를 나타냅니다. IPv4 주소의 경우 *address_index* 는 연결된 네트워크 인터페이스에 대한 동일한 인덱스입니다. IPv6의 경우 *address_index* 는 IPv6 주소 테이블의 항목을 나타냅니다.

IP 인스턴스를 만들고 ICMPv4 및 ICMPv6 서비스를 사용하도록 설정해야 합니다(*nxd_icmp_enable* 참조).

> [!CAUTION] 
> NX_SUCCESS가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 이 패킷을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 인스턴스를 가리키는 포인터입니다.
- **ip_address** ping할 대상 IP 주소입니다(호스트 바이트 순서).
- **address_index** 원본 주소로 사용할 IP 주소를 나타냅니다.
- **data_ptr** ping 패킷 데이터 영역을 가리키는 포인터입니다.
- **data_size** ping 데이터의 바이트 수입니다.
- **response_ptr** 응답 패킷 포인터를 가리키는 포인터입니다.
- **wait_option** 응답 대기 시간입니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)
    - **NX_WAIT_FOREVER**(0xFFFFFFFF)

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0X00) ping을 성공적으로 송수신했습니다.
- **NX_NOT_SUPPORTED**(0x4B) IPv6를 사용하지 않도록 설정했습니다.
- **NX_OVERFLOW**(0x03) ping 데이터가 패킷 페이로드를 초과합니다.
- **NX_NO_RESPONSE**(0x29) 대상 호스트가 응답하지 않았습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort에 의해 중단되었습니다.
- **NX_NO_INTERFACE_ADDRESS**(0x50) 적절한 송신 인터페이스를 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 응답 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0X14) IP 또는 ICMP 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 입력 IP 주소가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* The following two examples illustrate how to use this API to send ping
   packets to IPv6 or IPv4 destinations. */

/* The first example: Send a ping packet to an IPv6 host
   FE80::411:7B23:40dc:f181 */

/* Declare variable address to hold the destination address. */

#define PRIMARY_INTERFACE 0
#define GLOBAL_IPv6_ADDRESS 1

NXD_ADDRESS ip_address;
char *buffer = “abcd”;
UINT prefix_length = 10;

/* Set the IPv6 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]    = 0xFE800000;
ip_address.nxd_ip_address.v6[1]    = 0x00000000;
ip_address.nxd_ip_address.v6[2]    = 0x04117B23;
ip_address.nxd_ip_address.v6[3]    = 0x40DCF181;

status = nxd_icmp_source_ping(&ip_0, &ip_address,
                              GLOBAL_IPv6_ADDRESS,
                              buffer,
                              strlen(buffer),
                              &response_ptr,
                              NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply has been received
   from IP address FE80::411:7B23:40dc:f181 and the response packet is
   contained in the packet pointed to by response_ptr. It should have the
   same “abcd” four bytes of data. */

/* The second example: Send a ping packet to an IPv4 host 1.2.3.4 */

/* Program the IPv4 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4       = 0x01020304;

status = nxd_icmp_source_ping(&ip_0, &ip_address,
                              PRIMARY_INTERFACE,
                              buffer,
                              strlen(buffer),
                              &response_ptr,
                              NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply was received from
   IP address 1.2.3.4 and the response packet is contained in the packet
   pointed to by response_ptr. It should have the same “abcd” four bytes
   of data. */
```

### <a name="see-also"></a>참고 항목

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmpv6_ra_flag_callback_set"></a>nxd_icmpv6_ra_flag_callback_set
ICMPv6 RA 플래그 변경 콜백 함수 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_icmpv6_ra_flag_callback_set(
    NX_IP *ip_ptr, 
    VOID(*ra_callback)(NX_IP*ip_ptr, UINT ra_flag));
```
### <a name="description"></a>Description

이 서비스는 ICMPv6 라우터 보급 알림 플래그 변경 콜백 함수를 설정합니다. 사용자 제공 콜백 함수는 NetX Duo에서 라우터 보급 알림 메시지를 받을 때 호출됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 인스턴스를 가리키는 포인터입니다.
- **ra_callback** 사용자 제공 콜백 함수입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0X00) RA 플래그 콜백 함수를 설정했습니다.
- **NX_NOT_SUPPORTED**(0x4B) IPv6를 사용하지 않도록 설정했습니다.
- **NX_PTR_ERROR**(0x07) IP가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
VOID icmpv6_ra_flag_callback(NX_IP *ip_ptr, UINT ra_flag)
{
   /* RA flag has changed. The updated value is passed in via the
      ra_flag parameter. */
}

/* Configure the user-defined ICMPv6 RA flag change callback
   function. */
status = nxd_icmpv6_ra_flag_callback_set(&ip_0,
                                         icmpv6_ra_flag_callback);

/* A status return of NX_SUCCESS indicates the callback function has
   been successfully configured. */
```
### <a name="see-also"></a>참고 항목

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping

## <a name="nxd_ip_raw_packet_send"></a>nxd_ip_raw_packet_send
원시 IP 패킷 송신

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ip_raw_packet_send(
    NX_IP *ip_ptr, 
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *destination
    ULONG protocol, 
    UINT ttl, 
    ULONG tos);
```
### <a name="description"></a>Description

이 서비스는 원시 IPv4 또는 IPv6 패킷을 송신합니다(전송 계층 프로토콜 헤더 없음). 멀티홈 시스템에서 시스템이 적절한 인터페이스를 결정할 수 없는 경우(예: 대상 IP 주소가 IPv4 브로드캐스트, 멀티캐스트 또는 IPv6 멀티캐스트 주소인 경우) 기본 디바이스가 선택됩니다. 서비스 ***nxd_ip_raw_packet_source_send** _를 사용하여 보내는 인터페이스를 지정할 수 있습니다. NetX의 동급 서비스는 _ **_nx_ip_raw_packet_send_ 입니다.*

IP 인스턴스를 이전에 만든 후 ***nx_ip_raw_packet_enable*** 서비스를 사용하여 원시 IP 패킷 처리를 사용하도록 설정해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **packet_ptr** 전송할 패킷을 가리키는 포인터입니다.
- **destination_ip** 대상 주소를 가리키는 포인터입니다.
- **protocol** IP 헤더에 저장된 패킷 프로토콜입니다.
- **ttl** TTL 또는 홉 제한 값입니다.
- **tos** TOS 또는 트래픽 클래스 및 흐름 레이블의 값입니다.

### <a name="return-value"></a>반환 값 

- **NX_SUCCESS**(0x00) IP 패킷을 송신했습니다.
- **NX_NO_INTERFACE_ADDRESS**(0x50) 적절한 송신 인터페이스를 찾을 수 없습니다.
- **NX_NOT_ENABLED**(0X14) 원시 IP 처리가 사용하도록 설정되지 않았습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IPv4 또는 IPv6 주소가 잘못되었습니다.
- **NX_UNDERFLOW**(0x02) 패킷에 IPv4 또는 IPv6 헤더를 위한 공간이 부족합니다.
- **NX_OVERFLOW**(0x03) 패킷 뒤에 추가 포인터가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터나 패킷 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_INVALID_PARAMETERS**(0x4D) 유효한 IPv6 주소 입력이 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NXD_ADDRESS dest_address;

/* Set the destination address,in this case an IPv6 address. */
dest_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
dest_address.nxd_ip_address.v6[0]    = 0x20011234;
dest_address.nxd_ip_address.v6[1]    = 0x56780000;
dest_address.nxd_ip_address.v6[2]    = 0;
dest_address.nxd_ip_address.v6[3]    = 1;

UINT ttl, tos;

ttl = 128;

tos = 0;

/* Enable RAW IP handling on the previously created IP instance.*/
status = nx_raw_ip_packet_enable(&ip_0);

/* Allocate a packet pointed to by packet_ptr from the IP packet
   pool. */
/* Then transmit the packet to the destination address. */

status = nxd_ip_raw_packet_send(&ip_0, packet_ptr, dest_address,
                                NX_PROTOCOL_UDP, ttl, tos);

/* A status return of NX_SUCCESS indicates the packet was
   successfully transmitted. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_source_send

## <a name="nxd_ip_raw_packet_source_send"></a>nxd_ip_raw_packet_source_send
지정된 원본 주소를 사용하여 원시 패킷 송신

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ip_raw_packet_source_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *destination_ip,
    UINT address_index,
    ULONG protocol,
    UINT ttl,
    ULONG tos);
```
### <a name="description"></a>Description

이 서비스는 지정된 IPv4 또는 IPv6 주소를 원본 주소로 사용하여 원시 IPv4 또는 ipv6 패킷을 송신합니다. 시스템이 적절한 인터페이스를 결정할 수 없는 경우(예: 대상 IP 주소가 IPv4 브로드캐스트, 멀티캐스트 또는 IPv6 멀티캐스트 주소인 경우) 이 서비스는 일반적으로 멀티홈 시스템에서 사용됩니다. 매개 변수 *address_index* 를 사용하면 애플리케이션에서 이 원시 패킷을 보낼 때 사용할 원본 주소를 지정할 수 있습니다.

IP 인스턴스를 이전에 만든 후 ***nx_ip_raw_packet_enable*** 서비스를 사용하여 원시 IP 패킷 처리를 사용하도록 설정해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 인스턴스 포인터입니다.
- **packet_ptr** 송신할 패킷을 가리키는 포인터입니다.
- **destination_ip** 대상 IP 주소입니다.
- **address_index** 원본 주소로 사용할 IPv4 또는 IPv6 주소에 대한 인덱스입니다.
- **protocol** 프로토콜 필드의 값입니다.
- **ttl** TTL 또는 홉 제한 값입니다.
- **tos** TOS 또는 트래픽 클래스 및 흐름 레이블의 값입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 패킷이 성공적으로 송신되었습니다.
- **NX_UNDERFLOW**(0x02) 패킷에 IPv4 또는 IPv6 헤더를 위한 공간이 부족합니다.
- **NX_OVERFLOW**(0x03) 패킷 뒤에 추가 포인터가 잘못되었습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록, 패킷 또는 destination_ip에 대한 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 원시 처리가 사용하도록 설정되지 않았습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 주소 오류입니다.
- **NX_INVALID_INTERFACE**(0x4C) 잘못된 인터페이스 인덱스입니다.
- **NX_INVALID_PARAMETERS**(0x4D) 유효한 IPv6 주소 입력이 없습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define SOURCE_ADDRESS_INDEX 2

/* Send a raw packet from specified interface. */
status = nxd_ip_raw_packet_source_send(&ip_0, packet_ptr,
                                       dest_ip,
                                       SOURCE_ADDRESS_INDEX,
                                       NX_IP_RAW,
                                       NX_IP_TIME_TO_LIVE,
                                       NX_IP_NORMAL);

/* If status == NX_SUCCESS, raw packet has been sent out on the
   specified interface. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send

## <a name="nxd_ipv6_address_change_notify"></a>nxd_ipv6_address_change_notify
IPv6 주소 변경 알림 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_address_change_notify(
    NX_IP *ip_ptr,
    VOID (*ip_address_change_notify)(NX_IP *, UINT, UINT, UINT, ULONG *));
```
### <a name="description"></a>Description

이 서비스는 IPv6 주소가 변경될 때마다 NetX Duo가 호출하는 애플리케이션 콜백 루틴을 등록합니다.

***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY*** 옵션을 정의한 상태로 NetX Duo 라이브러리가 빌드된 경우 이 서비스를 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** IP 제어 블록 포인터입니다.
- **ip_address_change_notify** 애플리케이션 콜백 함수입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 설정하는 데 성공했습니다.
- **NX_NOT_SUPPORTED**(0x4B) IPv6 주소 변경 알림 기능은 Netx Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0X14) IPv6 주소 변경 알림이 컴파일되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
VOID ip_address_change_notify(NX_IP *ip_ptr, UINT status,
                              UINT interface_index,
                              UINT address_index,
                              ULONG *ip_address)
{

   /* Do something when ip address changed. */
}

void ip_address_thread_entry(ULONG id)
{

   /* Set the ip address change notify of IP instance. */
   status = nxd_ipv6_address_change_notify (&ip_0, ip_address_change_notify);

/* If status == NX_SUCCESS, the ip address change notify of IP
   instance was successfully set. */
}
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_delete"></a>nxd_ipv6_address_delete
IPv6 주소 삭제

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_address_delete(
    NX_IP *ip_ptr, 
    UINT address_index);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 IPv6 주소 테이블에서 지정된 인덱스에 있는 IPv6 주소를 삭제합니다. NetX의 동급 서비스는 없습니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **address_index** IP 인스턴스 IPv6 주소 테이블에 대한 인덱스입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 주소를 삭제했습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_NO_INTERFACE_ADDRESS**(0x50) 적절한 송신 인터페이스를 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NXD_ADDRESS ip_address;
UINT        address_index;

/* Delete the IPv6 address at the specified address table index. */
address_index = 1;
status = nxd_ipv6_address_delete(&ip_0, address_index);

/* A status return of NX_SUCCESS indicates that the IP instance
   address is successfully deleted. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_get"></a>nxd_ipv6_address_get
IPv6 주소 및 접두사 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_address_get(
    NX_IP *ip_ptr, 
    UINT address_index, 
    NXD_ADDRESS *ip_address,
    ULONG *prefix_length,
    UINT *interface_index);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 주소 테이블에서 지정된 인덱스에 있는 IPv6 주소 및 접두사를 검색합니다. IPv6 주소가 연결된 실제 인터페이스의 인덱스는 interface_index 포인터에서 반환됩니다. NetX의 동급 서비스는 ***nx_ip_address_get** _ 및 _*_nx_ip_interface_address_get_**입니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **address_index** IP 인스턴스 주소 테이블에 대한 인덱스입니다.
- **ip_address** 설정할 주소에 대한 포인터입니다.
- **prefix_length** 주소 접두사(서브넷 마스크)의 길이입니다.
- **interface_index** 인터페이스의 인덱스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IPv6를 사용하도록 설정했습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_NO_INTERFACE_ADDRESS**(0x50) 인터페이스 주소가 없거나 address_index가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NXD_ADDRESS ip_address;
UINT        address_index;
ULONG       prefix_length;
UINT        interface_index;

/* Get the IPv6 address at the specified address table index. If
   found, the address network interface is returned in the
   interface_index input, as well as the address prefix in the
   prefix_length input. */

address_index = 1;
status = nxd_ipv6_address_get(&ip_0, address_index, &ip_address,
                              &prefix_length, &interface_index);

/* A status return of NX_SUCCESS indicates that the IP instance
   address is successfully retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_set"></a>nxd_ipv6_address_set
IPv6 주소 및 접두사 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_address_set(
    NX_IP *ip_ptr, 
    UINT interface_index,
    NXD_ADDRESS *ip_address,
    ULONG prefix_length,
    UINT *address_index);
```
### <a name="description"></a>Description

이 서비스는 제공된 IPv6 주소와 지정된 IP 인스턴스에 대한 접두사를 설정합니다. *address_index* 인수가 null이 아니면 주소가 삽입된 IPv6 주소 테이블에 대한 인덱스가 반환됩니다. NetX의 동급 서비스는 ***nx_ip_address_set** _ 및 _*_nx_ip_interface_address_set_**입니다.

### <a name="parameters"></a>매개 변수  

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **interface_index** IPv6 주소가 연결된 인터페이스에 대한 인덱스입니다.
- **ip_address** 설정할 주소에 대한 포인터입니다.
- **prefix_length** 주소 접두사(서브넷 마스크)의 길이입니다.
- **address_index** 주소가 삽입된 주소 테이블에 대한 인덱스를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IPv6를 사용하도록 설정했습니다.
- **NX_NO_MORE_ENTRIES**(0x15) IP 주소 테이블이 꽉 찼습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_DUPLICATED_ENTRY**(0x52) 제공된 IP 주소는 이 IP 인스턴스에서 이미 사용되고 있습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IPv6 주소가 잘못되었습니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스가 잘못된 네트워크 인터페이스를 가리킵니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NXD_ADDRESS ip_address;
UINT        address_index;
UINT        interface_index;

ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* First create an IP instance with packet pool, source address, and
   driver.*/
status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                     IP_ADDRESS(1,2,3,4),
                     0xFFFFFF00UL, &pool_0,_nx_ram_network_driver,
                     pointer, 2048, 1);

/* Then enable IPv6 on the IP instance. */
status = nxd_ipv6_enable(&ip_0);

/* Set the IPv6 address (a global address as indicated by the 64 bit
   prefix) using the IPv6 address just created on the primary device
   (index zero). The index into the address table is returned in
   address_index. */
interface_index = 0;
status = nxd_ipv6_address_set(&ip_0, interface_index, &ip_address,
                              64,&address_index);

/* A status return of NX_SUCCESS indicates that the IPv6 address is
   successfully assigned to the primary interface (interface 0). */
```

### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add
기본 라우터 테이블에 IPv6 라우터 추가

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_default_router_add(
    NX_IP *ip_ptr,
    NXD_ADDRESS *router_address,
    ULONG router_lifetime,
    UINT index_index);
```
### <a name="description"></a>Description

이 서비스는 지정된 실제 인터페이스의 IPv6 기본 라우터를 기본 라우터 테이블에 추가합니다. 동급의 NetX IPv4 서비스는 ***nx_ip_gateway_address_set*** 입니다.

*router_address* 는 유효한 IPv6 주소를 가리켜야 하며, 지정된 실제 인터페이스에서 해당 라우터를 직접 액세스할 수 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **router_address** 기본 라우터 주소에 대한 포인터입니다(호스트 바이트 순서).
- **router_lifetime** 기본 라우터 수명 시간(초)입니다. 유효한 값은
    - **0xFFFF:** 시간 초과가 없습니다.
    - **0-0xFFFE:** 시간 초과 값(초)입니다.
- **index_index** 라우터에 연결할 수 있는 네트워크 인덱스의 유효한 메모리 위치에 대한 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0X00) 기본 라우터를 추가했습니다.
- **NX_NO_MORE_ENTRIES**(0x17) 기본 라우터 테이블에 사용할 수 있는 항목이 더 이상 없습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IPv6 주소가 잘못되었습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 유효한 IPv6 주소 입력이 없습니다.
- **NX_PTR_ERROR**(0X07) IP 인스턴스 또는 스토리지 공간이 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_INVALID_INTERFACE**(0x4C) 라우터 인터페이스 인덱스가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* This example adds a default router for the primary interface at
   fe80::1219:B9FF:FE37:ac to the default router table. */

#define PRIMARY_INTERFACE 0

NXD_ADDRESS router_address;

/* Set the router address version to IPv6 */
router_address.nxd_ip_version   = NX_IP_VERSION_V6;

/* Set the IPv6 address, in host byte order. */
router_address.nxd_ip_address[0] = 0xfe800000;
router_address.nxd_ip_address[1] = 0x0;
router_address.nxd_ip_address[2] = 0x1219B9FF;
router_address.nxd_ip_address[3] = 0xFE3700AC;

/* Set IPv6 default router. */
status = nxd_ipv6_default_router_add(ip_ptr, &router_address,
                                     0xFFFF, PRIMARY_INTERFACE);

/* Unless invalid pointer input is detected by the error checking
   Service, status return is always NX_SUCCESS. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete
기본 라우터 테이블에서 IPv6 라우터 제거

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_default_router_delete (
    NX_IP *ip_ptr,
    NXD_ADDRESS *router_address);
```
### <a name="description"></a>Description

이 서비스는 기본 라우터 테이블에서 IPv6 기본 라우터를 삭제합니다. 동급의 NetX IPv4 서비스는 ***nx_ip_gateway_address_clear*** 입니다.

### <a name="restrictions"></a>제한

IP 인스턴스가 생성되었습니다. *router_address* 는 유효한 정보를 가리켜야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **router_address** IPv6 기본 게이트웨이 주소에 대한 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 라우터를 삭제했습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_NOT_FOUND**(0x4E) 라우터 항목을 찾을 수 없습니다.
- **NX_PTR_ERROR**(0X07) IP 인스턴스 또는 스토리지 공간이 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_INVALID_PARAMETERS**(0x82) 비포인터 입력이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/*This example removes a default router:fe80::1219:B9FF:FE37:ac */

NXD_ADDRESS router_address;

/* Set the router_address version to IPv6 */
router_address.nxd_ip_version = NX_IP_VERSION_V6;

/* Program the IPv6 address, in host byte order. */
router_address.nxd_ip_address[0] = 0xfe800000;
router_address.nxd_ip_address[1] = 0x0;
router_address.nxd_ip_address[2] = 0x1219B9FF;
router_address.nxd_ip_address[3] = 0xFE3700AC;

/* Delete the IPv6 default router. */
nxd_ipv6_default_router_delete(ip_ptr, &router_address);
```
### <a name="see-also"></a>참고 항목

- nx_ip_gateway_address_clearnx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_getnx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_entry_get"></a>nxd_ipv6_default_router_entry_get
기본 라우터 항목 가져오기

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_default_router_entry_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT entry_index,
    NXD_ADDRESS *router_addr,
    ULONG *router_lifetime,
    ULONG *prefix_length,
    ULONG *configuration_method);
```
### <a name="description"></a>Description

이 서비스는 지정된 네트워크 디바이스에 연결된 기본 IPv6 라우팅 테이블에서 라우터 항목을 검색합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 제어 블록 포인터입니다.
- **interface_index** 네트워크 인터페이스에 대한 인덱스입니다.
- **entry_index** 항목 인덱스입니다.
- **router_addr** 라우터 IPv6 주소입니다.
- **router_lifetime** 라우터 수명 시간에 대한 포인터입니다.
- **prefix_length** 접두사 길이에 대한 포인터입니다.
- **configuration_method** 항목이 구성된 방법에 대한 정보를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 가져오는 데 성공했습니다.
- **NX_NOT_FOUND**(0x4E) 라우터 항목을 찾을 수 없습니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스 인덱스가 잘못되었습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define PRIMARY_INTERFACE 0
NXD_ADDRESS            router_addr;
ULONG                  router_lifetime;
ULONG                  prefix_length;
ULONG                  configuration_method;

/* Get the router entry of specified interface. */
status = nxd_ipv6_default_router_entry_get (&ip_0,
                                            PRIMARY_INTERFACE,
                                            entry_index,
                                            &router_addr,
                                            &router_lifetime,
                                            &prefix_length,
                                            &configuration_method);

/* If status == NX_SUCCESS, the router entry was successfully
   got. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_get"></a>nxd_ipv6_default_router_get
기본 라우터 테이블에서 IPv6 라우터 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_default_router_get(
    NX_IP *ip_ptr, 
    UINT interface_index
    NXD_ADDRESS *router_address,
    ULONG *router_lifetime,
    ULONG *prefix_length);
```
### <a name="description"></a>Description

이 서비스는 기본 라우터 테이블에서 지정된 실제 인터페이스의 IPv6 기본 라우터 주소, 수명 및 접두사 길이를 검색합니다. 동급의 NetX IPv4 서비스는 **nx_ip_gateway_address_get*** 입니다.

*router_address* 는 유효한 NXD_ADDRESS 구조체를 가리켜야 하므로 이 서비스는 기본 라우터의 IPv6 주소를 채울 수 있습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **interface_index** 라우터에 액세스하는 데 사용하는 네트워크 인터페이스에 대한 인덱스입니다.
- **router_address** 기본 라우터 주소의 반환 값에 대한 스토리지 공간을 가리키는 포인터입니다(호스트 바이트 순서).
- **router_lifetime** 라우터 수명에 대한 포인터입니다.
- **prefix_length** 라우터 주소 접두사 길이에 대한 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0X00) 기본 라우터를 추가했습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_NOT_FOUND**(0x4E) 기본 라우터를 찾을 수 없습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_INVALID_INTERFACE**(0x4C) 라우터 인터페이스 인덱스가 잘못되었습니다.
- **NX_PTR_ERROR**(0X07) IP 인스턴스 또는 스토리지 공간이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* This example retrieves a default router for the primary device
   from the default router table. */

#define PRIMARY_INTERFACE 0

NXD_ADDRESS router_address;
ULONG       router_lifetime;
ULONG       prefix_length;

/* Get IPv6 default router. */
status = nxd_ipv6_default_router_get(ip_ptr, PRIMARY_INTERFACE,
                                     &router_address,
                                     &router_lifetime,
                                     &prefix_length);

/* If status returns NX_SUCCESS, the router address and related
   information is returned successfully. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_number_of_entries_get"></a>nxd_ipv6_default_router_number_of_entries_get
기본 IPv6 라우터 수 가져오기

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_default_router_number_of_entries_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT *num_entries);
```
### <a name="description"></a>Description

이 서비스는 지정된 네트워크 인터페이스에 구성된 IPv6 기본 라우터 수를 검색합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 제어 블록 포인터입니다.
- **interface_index** 네트워크 인터페이스에 대한 인덱스입니다.
- **num_entries** 지정된 네트워크 디바이스의 IPv6 라우터 수에 대한 대상입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 가져오는 데 성공했습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스 값이 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 제어 블록 포인터 또는 num_entries 포인터입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define PRIMARY_INTERFACE 0
UINT                   num_entries;

/* Get the router entries of specified interface. */
status = nxd_ipv6_default_router_number_of_entries_get(&ip_0,
                                                       PRIMARY_INTERFACE,
                                                       &num_entries);

/* If status == NX_SUCCESS, the router entries was successfully
   retrieved. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get

## <a name="nxd_ipv6_disable"></a>nxd_ipv6_disable
IPv6 기능을 사용하지 않도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스에 대해 IPv6를 사용하지 않도록 설정합니다. 또한 기본 라우터 테이블, ND 캐시 및 IPv6 주소 테이블을 지우고, 모든 멀티캐스트 그룹을 탈퇴하고, 라우터 요청 변수를 다시 설정합니다. IPv6를 사용하지 않도록 설정하면 이 서비스는 영향을 주지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 인스턴스 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) 사용하지 않도록 설정했습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다.
- **NX_NOT_SUPPORT**(0x4B) IPv6 모듈이 컴파일되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Disable IPv6 feature on this IP instance. */
status = nxd_ipv6_disable(&ip_0);

/* If status == NX_SUCCESS, disables IPv6 feature on IP instance.*/
```
### <a name="see-also"></a>참고 항목 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable
IPv6 서비스를 사용하도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 IPv6 서비스를 사용하도록 설정합니다. IPv6 서비스를 사용하도록 설정하면 IP 인스턴스가 모든 노드 멀티캐스트 그룹에 조인합니다(FF02::1). 이 서비스는 링크 로컬 주소 또는 전체 주소를 설정하지 않습니다. 애플리케이션은 nxd_ipv6_address_set을 사용하여 디바이스 네트워크 주소를 구성해야 합니다. NetX의 동급 서비스는 없습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00) IPv6를 사용하도록 설정했습니다.
- **NX_ALREADY_ENABLED**(0x15) IPv6가 이미 사용하도록 설정되었습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* First create an IP instance with packet pool, source address, and
   driver.*/
status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                      IP_ADDRESS(1,2,3,4),
                      0xFFFFFF00UL, &pool_0,_nx_ram_network_driver,
                      pointer, 2048, 1);

/* Then enable IPv6 on the IP instance. */
status = nxd_ipv6_enable(&ip_0);

/* A status return of NX_SUCCESS indicates that the IP instance is
   enabled for IPv6 services. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_multicast_interface_join"></a>nxd_ipv6_multicast_interface_join
IPv6 멀티캐스트 그룹에 조인

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_multicast_interface_join(
    NX_IP *ip_ptr,
    NXD_ADDRESS *group_address,
    UINT interface_index);
```

### <a name="description"></a>Description

이 서비스를 통해 애플리케이션은 특정 네트워크 인터페이스의 특정 IPv6 멀티캐스트 주소에 조인할 수 있습니다. 링크 드라이버에는 멀티캐스트 주소를 추가하라는 알림이 표시됩니다. 이 서비스는 ***NX_ENABLE_IPV6_MULTICAST*** 옵션을 정의한 상태로 Netx Duo 라이브러리를 빌드한 경우에 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수  

- **ip_ptr** IP 인스턴스 포인터입니다.
- **group_address** IPv6 멀티캐스트 주소입니다.
- **interface_index** 멀티캐스트 그룹과 연결된 네트워크 인터페이스에 대한 인덱스입니다.

### <a name="return-values"></a>반환 값  

- **NX_SUCCESS**(0x00)가 IPv6 멀티캐스트 주소 수신을 사용하도록 설정했습니다.
- **NX_NO_MORE_ENTRIES**(0x17) IPv6 멀티캐스트 테이블에 항목이 더 이상 없습니다.
- **NX_OVERFLOW**(0x03) 디바이스 드라이버에서 사용할 수 있는 그룹 주소가 더 이상 없습니다.
- **NX_NOT_SUPPORTED**(0x4B) IPv6 기능 또는 IPv6 멀티캐스트 기능이 Netx Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IPv6 주소가 잘못되었습니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스 인덱스가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define PRIMARY_INTERFACE 0

/* Join multicast group on this IP instance. */
status = nxd_ipv6_multicast_interface_join(&ip_0,
                                           &group_address,
                                           PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, interface of index on IP instance
   has joined the multicast group. */
```
### <a name="see-also"></a>참고 항목

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_leave

## <a name="nxd_ipv6_multicast_interface_leave"></a>nxd_ipv6_multicast_interface_leave
IPv6 멀티캐스트 그룹에서 탈퇴

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_multicast_interface_leave(
    NX_IP *ip_ptr,
    NXD_ADDRESS *group_address,
    UINT interface_index);
```
### <a name="description"></a>Description

이 서비스는 특정 네트워크 디바이스에서 특정 IPv6 멀티캐스트 주소를 제거합니다. 링크 드라이버는 IPv6 멀티캐스트 주소를 제거할 때에도 알림을 받습니다. 이 서비스는 ***NX_ENABLE_IPV6_MULTICAST*** 옵션을 정의한 상태로 Netx Duo 라이브러리를 빌드한 경우에 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수  

- **ip_ptr** IP 인스턴스 포인터입니다.
- **group_address** IPv6 멀티캐스트 주소입니다.
- **interface_index** 그룹과 연결된 네트워크 인터페이스에 대한 인덱스입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 멀티캐스트에서 탈퇴했습니다.
- **NX_ENTRY_NOT_FOUND**(0X16) 항목을 찾을 수 없습니다.
- **NX_NOT_SUPPORTED**(0x4B) IPv6 기능 또는 IPv6 멀티캐스트 기능이 Netx Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IPv6 주소가 잘못되었습니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스 인덱스가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define PRIMARY_INTERFACE 0

/* Leave multicast address on this IP instance. */
status = nxd_ipv6_multicast_interface_leave(&ip_0,
                                            &group_address,
                                            primary_interface);

/* If status == NX_SUCCESS, interface of index on IP instance
   has left the multicast group. */
```
### <a name="see-also"></a>참고 항목

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join

## <a name="nxd_ipv6_stateless_address_autoconfig_disable"></a>nxd_ipv6_stateless_address_autoconfig_disable
상태 비저장 주소 자동 구성을 사용하지 않도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_stateless_address_autoconfig_disable(
    NX_IP *ip_ptr,
    UINT interface_index);
```
### <a name="description"></a>Description

이 서비스는 지정된 네트워크 디바이스에서 IPv6 상태 비저장 주소 자동 구성 기능을 사용하지 않도록 설정합니다. IPv6 주소가 구성된 경우에는 영향을 주지 않습니다.

이 서비스는 ***NX_IPV6_STATELESS_AUTOCONFIG_CONTROL*** 옵션이 정의된 상태로 Netx Duo 라이브러리가 빌드된 경우에 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 인스턴스 포인터입니다.
- **interface_index** IPv6 상태 비저장 주소 자동 구성을 사용하지 않도록 설정해야 하는 네트워크 인터페이스에 대한 인덱스입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 상태 비저장 주소 자동 구성 기능을 사용하지 않도록 설정했습니다.
- **NX_NOT_SUPPORTED**(0x4B) IPv6 기능 또는 IPv6 상태 비저장 주소 자동 구성 컨트롤 기능이 Netx Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스 인덱스가 잘못되었습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define PRIMARY_INTERFACE 0

/* Disable stateless address auto configuration on this IP instance. */
status = nxd_ipv6_stateless_address_autoconfig_disable(&ip_0,
                                                       PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, disables stateless address auto
   configuration on IP instance. */
```
### <a name="see-also"></a>참고 항목 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_stateless_address_autoconfig_enable"></a>nxd_ipv6_stateless_address_autoconfig_enable
상태 비저장 주소 자동 구성을 사용하도록 설정

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_ipv6_stateless_address_autoconfig_enable(
    NX_IP *ip_ptr,
    UINT interface_index);
```
### <a name="description"></a>Description

이 서비스는 지정된 네트워크 디바이스에서 IPv6 상태 비저장 주소 자동 구성 기능을 사용하도록 설정합니다.

이 서비스는 ***NX_IPV6_STATELESS_AUTOCONFIG_CONTROL*** 옵션이 정의된 상태로 Netx Duo 라이브러리가 빌드된 경우에 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** IP 인스턴스 포인터입니다.
- **interface_index** IPv6 상태 비저장 주소 자동 구성을 사용하도록 설정해야 하는 네트워크 인터페이스에 대한 인덱스입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0X00) 상태 비저장 주소 자동 구성 기능을 사용하도록 설정했습니다.
- **NX_ALREADY_ENABLED**(0x15) 이미 사용하도록 설정되었습니다.
- **NX_NOT_SUPPORTED**(0x4B) IPv6 기능 또는 IPv6 상태 비저장 주소 자동 구성 컨트롤 기능이 Netx Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스 인덱스가 잘못되었습니다.
- **NX_PTR_ERROR**(0X07) IP 제어 블록 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
#define PRIMARY_INTERFACE

/* Enable stateless address auto configuration on this
   IP instance. */
status = nxd_ipv6_stateless_address_autoconfig_enable(&ip_0,
                                                      PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, enables stateless address auto
   configuration on IP instance. */
```
### <a name="see-also"></a>참고 항목 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable

## <a name="nxd_nd_cache_entry_delete"></a>nxd_nd_cache_entry_delete
인접 캐시에서 IPv6 주소 항목 삭제

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_nd_cache_entry_delete(
    NX_IP *ip_ptr, 
    ULONG *ip_address);
```
### <a name="description"></a>Description

이 서비스는 제공된 IP 주소에 대한 IPv6 네트워크 환경 검색 캐시 항목을 삭제합니다. 동급의 NetX IPv4 함수는 ***nx_arp_static_entry_delete*** 입니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 삭제할 IPv6 주소에 대한 포인터입니다(호스트 바이트 순서).

### <a name="return-values"></a>반환 값

- **GX_SUCCESS**(0x00) 주소를 삭제했습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) IPv6 네트워크 환경 캐시에서 주소를 찾을 수 없습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_PTR_ERROR**(0X07) IP 인스턴스 또는 스토리지 공간이 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* This example deletes an entry from the neighbor cache table. */

NXD_ADDRESS ip_address;

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Delete an entry in the neighbor cache table with the specified IPv6
   address and hardware address. */
status = nxd_nd_cache_entry_delete(&ip_0,
                                   &ip_address.nxd_ip_address.v6[0]);

/* If status == NX_SUCCESS, the entry was deleted from the neighbor cache
   table. */
```
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set
네트워크 환경 캐시에 IPv6 주소/MAC 매핑 추가

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_nd_cache_entry_set(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *dest_ip,
    UINT interface_index, 
    char *mac);
```

### <a name="description"></a>Description

이 서비스는 지정된 네트워크 인터페이스 인덱스(interface_index)의 하드웨어 MAC 주소에 매핑된 지정된 IP 주소 *ip_address* 에 대한 네트워크 환경 검색 캐시에 항목을 추가합니다. 동급의 NetX IPv4 서비스는 ***nx_arp_static_entry_create*** 입니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **dest_ip** IPv6 주소 인스턴스에 대한 포인터입니다.
- **interface_index** 대상 IPv6 주소에 연결할 수 있는 실제 네트워크 인터페이스를 지정하는 인덱스입니다. 
- **mac** 하드웨어 주소에 대한 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0X00) 항목을 추가했습니다.
- **NX_NOT_SUCCESSFUL**(0x43) 캐시가 잘못되었거나 사용 가능한 네트워크 환경 캐시 항목이 없습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_PTR_ERROR**(0X07) IP 인스턴스 또는 스토리지 공간이 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_INVALID_INTERFACE**(0x4C) 인터페이스 인덱스 값이 올바르지 않습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* This example adds an entry on the primary network interface to
   the neighbor cache table. */

#define PRIMARY_INTEFACE 0

NXD_ADDRESS ip_address;
UCHAR hw_address[6] = {0x0, 0xcf,0x01,0x02, 0x03, 0x04};
CHAR  *mac;

mac = (CHAR *)&hw_address[0];

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Create an entry in the neighbor cache table with the specified
   IPv6 address and hardware address. */
status = nxd_nd_cache_entry_set(&ip_0,
                                &ip_address.nxd_ip_address.v6[0],
                                PRIMARY_INTERFACE, mac);

/* If status == NX_SUCCESS, the entry was added to the neighbor
   cache table. */
```
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_hardware_address_find"></a>nxd_nd_cache_hardware_address_find
IPv6 주소에 대한 하드웨어 주소 찾기

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_nd_cache_hardware_address_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *ip_address,
    ULONG *physical_msw,
    ULONG *physical_lsw
    UINT *interface_index);
```
### <a name="description"></a>Description

이 서비스는 제공된 IPv6 주소와 연결된 IPv6 네트워크 환경 검색 캐시에서 실제 하드웨어 주소를 찾으려고 시도합니다. 네트워크 환경에 연결할 수 있는 네트워크 인터페이스의 인덱스는 interface_index 매개 변수에도 반환됩니다. 동급의 NetX IPv4 서비스는 ***nx_arp_hardware_address_find*** 입니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 찾을 IP 주소에 대한 포인터입니다(호스트 바이트 순서).
- **physical_msw** 실제 주소의 상위 16비트(47-32)에 대한 포인터입니다(호스트 바이트 순서). 
- **physical_lsw** 실제 주소의 하위 32비트(31-0)에 대한 포인터입니다(호스트 바이트 순서).
- **interface_index** IPv6 주소에 연결할 수 있는 네트워크 디바이스를 지정하는 인터페이스 인덱스의 올바른 메모리 위치를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 주소를 찾았습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) 네트워크 환경 캐시에 매핑이 없습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 제공된 IP 주소는 버전 6이 아닙니다.
- **NX_PTR_ERROR**(0X07) IP 인스턴스 또는 스토리지 공간이 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* This example inputs an IP address on the primary network in order
   to obtain the hardware address it is mapped to in the neighbor
   cache able. */

NXD_ADDRESS  ip_address;
ULONG physical_msw, physical_lsw;
UINT  interface_index;

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Obtain the hardware address mapped to the supplied global IPv6
   address. */
status = nxd_nd_cache_hardware_address_find(&ip_0, &ip_address,
                                            &physical_msw,
                                            &physical_lsw
                                            &interface_index);

/* If status == NX_SUCCESS, a matching entry was found in the
   neighbor cache table and the hardware address returned in
   variables physical_msw and physical_lsw, the index of the network
   interface through which the neighbor can be reached is stored in
   interface_index. */
```
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate
네트워크 환경 검색 캐시 무효화

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_nd_cache_invalidate(NX_IP *ip_ptr);
```
### <a name="description"></a>Description

이 서비스는 전체 IPv6 네트워크 환경 검색 캐시를 무효화합니다. 이 서비스는 ICMPv6를 사용하도록 설정하기 전이나 후에 호출할 수 있습니다. 이 서비스는 IPv4 연결에는 적용되지 않으므로 동급의 NetX 서비스가 없습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** IP 인스턴스를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 캐시가 무효화되었습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_PTR_ERROR**(0x07) IP 인스턴스가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* This example invalidates the host neighbor cache table. */

/* Invalidate the cache table bound to the IP instance. */
status = nxd_nd_cache_invalidate (&ip_0);

/* If status == NX_SUCCESS, all entries in the neighbor cache table
   are invalidated. */
```
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find
실제 주소의 IPv6 주소 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_nd_cache_ip_address_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *ip_address,
    ULONG physical_msw,
    ULONG physical_lsw,
    UINT *interface_index);
```
### <a name="description"></a>Description

이 서비스는 제공된 물리적 주소와 연결된 IPv6 네트워크 환경 검색 캐시에서 IPv6 주소를 찾으려고 시도합니다. 네트워크 환경에 연결할 수 있는 네트워크 인터페이스의 인덱스도 반환됩니다. 동급의 NetX IPv4 서비스는 ***nx_arp_ip_address_find*** 입니다.

### <a name="parameters"></a>매개 변수 

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 올바른 NXD_ADDRESS 구조체를 가리키는 포인터입니다.
- **physical_msw** 찾을 물리적 주소의 상위 16비트(47-32)입니다(호스트 바이트 순서).
- **physical_lsw** 찾을 물리적 주소의 하위 32비트(31-0)입니다(호스트 바이트 순서).
- **interface_index** IPv6 주소에 도달할 수 있는 네트워크 디바이스 인덱스를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 주소를 찾았습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) 네트워크 환경 캐시에서 실제 주소를 찾을 수 없습니다.
- **NX_NOT_SUPPORTED**(0x4b) IPv6 기능은 NetX Duo 라이브러리에 기본 제공되어 있지 않습니다.
- **NX_PTR_ERROR**(0X07) IP 인스턴스 또는 스토리지 공간이 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다. 
- **NX_INVALID_PARAMETERS**(0x4D) MAC 주소가 0입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* This example inputs a hardware address to search on for the
   matching IPv6 global address in the neighbor cache table. */

NXD_ADDRESS ip_address;
ULONG physical_msw = 0xcf;
ULONG physical_lsw = 0x01020304;
UINT  interface_index;

/* Obtain the IPv6 address mapped to the supplied hardware
   Address on the primary device. */
status = nxd_nd_cache_ip_address_find(&ip_0, &ip_address,
                                      physical_msw, physical_lsw,
                                      &interface_index);

/* If status == NX_SUCCESS, a matching entry was found in the
   neighbor cache table and the global IPv6 address returned in
   variable ip_address. */
```
### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate

## <a name="nxd_tcp_client_socket_connect"></a>nxd_tcp_client_socket_connect
TCP 연결 만들기

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr
    NXD_ADDRESSS *server_ip,
    UINT server_port,
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 지정된 서버의 포트에 대해 이전에 만든 TCP 클라이언트 소켓을 사용하여 TCP 연결을 만듭니다. 이 서비스는 IPv4 또는 IPv6 네트워크에서 작동합니다. 유효한 TCP 서버 포트의 범위는 0에서 0xFFFF까지입니다. NetX Duo는 서버 IP 주소에 따라 적절한 실제 인터페이스를 결정합니다. 동급의 NetX IPv4 서비스는 ***nx_tcp_client_socket_connect*** 입니다.

소켓이 로컬 포트에 바인딩되어야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓을 가리키는 포인터입니다.
- **server_ip** IPv4 또는 IPv6 대상 주소를 가리키는 포인터입니다(호스트 바이트 순서).
- **server_port** 연결할 서버 포트 번호(1-0xFFFF)입니다(호스트 바이트 순서).
- **wait_option** 연결이 설정되는 동안 대기 옵션입니다. 대기 옵션은 다음과 같이 정의됩니다.
    - **NX_NO_WAIT**(0x00000000)
    - **NX_WAIT_FOREVER**(0xFFFFFFFF)
    - **틱 단위의 시간 제한**(0x00000001~0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓 연결에 성공했습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 서버 IPv4 또는 IPv6 주소가 잘못되었습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 바인딩되지 않았습니다.
- **NX_NOT_CLOSED**(0x35) 소켓이 닫힘 상태가 아닙니다.
- **NX_IN_PROGRESS**(0x37) 대기하도록 지정되지 않았으며, 연결하려고 시도하는 중입니다.
- **NX_INVALID_INTERFACE**(0x4C) 잘못된 인터페이스 인덱스입니다.
- **NX_NO_INTERFACE_ADDRESS**(0x50) 네트워크 인터페이스에 올바른 IPv6 주소가 없습니다.
- **NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PORT**(0x46) 잘못된 포트입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_CONNECTED**(0x38) 연결이 실패합니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NXD_ADDRESS peer_ip_address;
ULONG       peer_port;

/* Set Peer IPv6 address */
peer_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
peer_ip_address.nxd_ip_address.v6[0] = 0x20010000;
peer_ip_address.nxd_ip_address.v6[1] = 0;
peer_ip_address.nxd_ip_address.v6[2] = 0;
peer_ip_address.nxd_ip_address.v6[3] = 0x101;

/* Set peer port number */
peer_port = 2563;

/* Connect to the peer */
status = nxd_tcp_client_socket_connect(socket_ptr,
                                       &peer_ip_address,
                                       peer_port, NX_WAIT_FOREVER);
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_socket_peer_info_get

## <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get
피어 TCP 소켓 IP 주소 및 포트 번호 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_tcp_socket_peer_info_get
    (NX_TCP_SOCKET *socket_ptr,
    NXD_ADDRESS *peer_ip_address,
    ULONG *peer_port);
```
### <a name="description"></a>Description

이 서비스는 IPv4 또는 IPv6 네트워크를 통해 연결된 TCP 소켓의 피어 IP 주소 및 포트 정보를 검색합니다. 동급의 NetX IPv4 서비스는 ***nx_tcp_socket_peer_info_get*** 입니다.

*socket_ptr* 는 이미 연결된 상태인 TCP 소켓을 가리켜야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 피어 호스트에 연결된 TCP 소켓을 가리키는 포인터입니다.
- **peer_ip_address** IPv4 또는 IPv6 피어 주소를 가리키는 포인터입니다. 반환된 IP 주소는 호스트 바이트 순서로 되어 있습니다.
- **peer_port** 피어 포트 번호를 가리키는 포인터입니다. 반환된 포트 번호는 호스트 바이트 순서로 되어 있습니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0X00) 소켓 정보를 검색했습니다.
- **NX_NOT_CONNECTED**(0x38) 소켓이 피어에 연결되어 있지 않습니다.
- **NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터 입력입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NXD_ADDRESS  peer_ip_address;
ULONG        peer_port;

/* Get TCP socket information. */
status = nxd_tcp_socket_peer_info_get(socket_ptr, &peer_ip_address,
                                      &peer_port);

/* If status == NX_SUCCESS, the service returns valid peer info: */
if(peer_ip_address.nxd_ip_version == NX_IP_VERSION_V4)
    /* Peer IP address is stored in
       peer_ip_address.nxd_ip_address.v4 */

if(peer_ip_address.nxd_ip_version == NX_IP_VERSION_V6)
    /* Peer IP address is stored in
       peer_ip_address.nxd_ip_address.v6 */
```
### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect

## <a name="nxd_udp_packet_info_extract"></a>nxd_udp_packet_info_extract
UDP 패킷에서 네트워크 매개 변수 추출

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```
### <a name="description"></a>Description

이 서비스는 IPv4 또는 IPv6 UDP 네트워크를 통해 수신된 패킷에서 네트워크 매개 변수를 추출합니다. 동급의 NetX 서비스는 ***nx_udp_packet_info_extract*** 입니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 패킷을 가리키는 포인터입니다.
- **ip_address** 송신기 IP 주소를 가리키는 포인터입니다.
- **protocol** 반환될 프로토콜을 가리키는 포인터입니다.
- **port** 송신기 포트 번호를 가리키는 포인터입니다.
- **interface_index** 이 패킷을 수신하는 네트워크 인터페이스의 인덱스를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값 

- **NX_SUCCESS**(0x00) 패킷 인터페이스 데이터를 성공적으로 추출했습니다.
- **NX_INVALID_PACKET**(0x12) 패킷은 IPv4도 아니고 IPv6도 아닙니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터 입력입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Extract network data from UDP packet interface.*/
status = nxd_udp_packet_info_extract(packet_ptr, &ip_address,
                                    &protocol, &port,
                                    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved.*/
```
### <a name="see-also"></a>참고 항목 

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send
UDP 데이터그램 송신

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT port);
```
### <a name="description"></a>Description

이 서비스는 IP4 또는 IPv6 네트워크에 대해 이전에 만들고 바인딩한 UDP 소켓을 통해 UDP 데이터그램을 송신합니다. NetX Duo는 대상 IP 주소를 기반으로 하여 원본 주소로 적합한 로컬 IP 주소를 찾습니다. 특정 인터페이스와 원본 IP 주소를 지정하려면 애플리케이션에서 ***nxd_udp_socket_source_send*** 서비스를 사용해야 합니다.

이 서비스는 UDP 데이터그램이 성공적으로 송신되었는지 여부에 관계없이 즉시 반환됩니다. 동급의 NetX(IPv4) 서비스는 ***nx_udp_socket_send*** 입니다.

소켓은 로컬 포트에 바인딩되어 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스를 가리키는 포인터입니다.
- **packet_ptr** UDP 데이터그램 패킷 포인터입니다.
- **ip_address** 대상 IPv4 또는 IPv6 주소를 가리키는 포인터입니다.
- **port** 1에서 0xFFFF 사이의 유효한 대상 포트 번호입니다(호스트 바이트 순서).

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) UDP 소켓 송신에 성공했습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 서버 IPv4 또는 IPv6 주소가 잘못되었습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.
- **NX_NO_INTERFACE_ADDRESS**(0x50) 적절한 송신 인터페이스를 찾을 수 없습니다.
- **NX_UNDERFLOW**(0x02) 패킷에 UDP 헤더를 위한 공간이 부족합니다.
- **NX_OVERFLOW**(0x03) 패킷 뒤에 추가 포인터가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 소켓 포인터, 주소 포인터 또는 패킷 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) UDP가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PORT**(0x46) 포트 번호가 유효한 범위 내에 있지 않습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NXD_ADDRESS ip_address, server_address;

/* Set the UDP Client IPv6 address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* Set the UDP server IPv6 address to send to. */
server_address.nxd_ip_version = NX_IP_VERSION_V6;
server_address.nxd_ip_address.v6[0] = 0x20010000;
server_address.nxd_ip_address.v6[1] = 0;
server_address.nxd_ip_address.v6[2] = 0;
server_address.nxd_ip_address.v6[3] = 2;

/* Set the global address (indicated by the 64 bit prefix) using the
   IPv6 address just created on the primary device (index 0). We
   don’t need the index into the address table, so the last argument
   is set to null. */

interface_index = 0;
status = nxd_ipv6_address_set(&client_ip, interface_index,
                              &ip_address, 64, NX_NULL);

/* Create the UDP socket client_socket with the ip_address and
   allocate a packet pointed to by packet_ptr (not shown). */

/* Send a packet to the UDP server at server_address on port 12. */
status = nxd_udp_socket_send(&client_socket, packet_ptr,
                             &server_address, 12);

/* If status == NX_SUCCESS, the UDP host successfully transmitted
   the packet out the UDP socket to the server. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_udp_socket_source_send"></a>nxd_udp_socket_source_send
UDP 데이터그램 송신

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_udp_socket_source_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT port, 
    UINT address_index);
```
### <a name="description"></a>Description

이 서비스는 IP4 또는 IPv6 네트워크에 대해 이전에 만들고 바인딩한 UDP 소켓을 통해 UDP 데이터그램을 송신합니다. *address_index* 매개 변수는 나가는 패킷에 사용할 원본 IP 주소를 지정합니다. 이 함수는 UDP 데이터그램이 성공적으로 송신되었는지 여부에 관계없이 즉시 반환됩니다.

소켓은 로컬 포트에 바인딩되어 있어야 합니다.

동급의 NetX(IPv4) 서비스는 입니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스를 가리키는 포인터입니다.
- **packet_ptr** UDP 데이터그램 패킷 포인터입니다.
- **ip_address** 대상 IPv4 또는 IPv6 주소 포트를 가리키는 포인터입니다. 유효한 대상 포트 번호는 1-0xFFFF 사이입니다(호스트 바이트 순서).
- **address_index** 패킷에 사용할 원본 주소를 지정하는 인덱스입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) UDP 소켓 송신에 성공했습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 서버 IPv4 또는 IPv6 주소가 잘못되었습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.
- **NX_NO_INTERFACE_ADDRESS**(0x50) 적절한 송신 인터페이스를 찾을 수 없습니다.
- **NX_NOT_FOUND**(0x4E) 적절한 인터페이스를 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) 소켓 포인터, 주소 또는 패킷 포인터가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) UDP가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PORT**(0x46) 포트 번호가 유효한 범위 내에 있지 않습니다.
- **NX_INVALID_INTERFACE**(0x4C) 지정된 네트워크 인터페이스가 유효합니다.
- **NX_UNDERFLOW**(0x02) 패킷에 UDP 헤더를 위한 공간이 부족합니다.
- **NX_OVERFLOW**(0x03) 패킷 뒤에 추가 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NXD_ADDRESS ip_address, server_address;
UINT address_index;

/* Set the UDP Client IPv6 address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* Set the UDP server IPv6 address to send to. */
server_address.nxd_ip_version = NX_IP_VERSION_V6;
server_address.nxd_ip_address.v6[0] = 0x20010000;
server_address.nxd_ip_address.v6[1] = 0;
server_address.nxd_ip_address.v6[2] = 0;
server_address.nxd_ip_address.v6[3] = 2;

/* Set the global address (indicated by the 64 bit prefix) using the IPv6
   address just created on the primary device (index 0). The address index
   is needed for nxd_udp_socket_source_send. */

status = nxd_ipv6_address_set(&client_ip, 0,
                              &ip_address, 64, &address_index);

/* Create the UDP socket client_socket with the ip_address and
   allocate a packet pointed to by packet_ptr (not shown). */

/* Send a packet to the UDP server at server_address on port 12. */
status = nxd_udp_socket_source_send(&client_socket, packet_ptr,
                                    &server_address, 12, address_index);

/* If status == NX_SUCCESS, the UDP host successfully transmitted the
   packet out the UDP socket to the server. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_source_extract

## <a name="nxd_udp_source_extract"></a>nxd_udp_source_extract
UPD 패킷 원본 정보 검색

### <a name="prototype"></a>프로토타입  

```c
UINT nxd_udp_source_extract(
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address, 
    UINT *port);
```
### <a name="description"></a>Description

이 서비스는 호스트 UDP 소켓을 통해 받은 UDP 패킷에서 원본 IP 주소와 포트 번호를 추출합니다. 동급의 NetX(IPv4) 서비스는 ***nx_udp_source_extract*** 입니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 받은 UDP 패킷에 대한 포인터입니다.
- **ip_address** 패킷 원본 IP 주소를 저장할 NXD_ADDRESS 구조를 가리키는 포인터입니다.
- **port** UDP 소켓 포트 번호를 가리키는 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 원본을 성공적으로 추출했습니다.
- **NX_INVALID_PACKET**(0x12) 패킷이 올바르지 않습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
NXD_ADDRESS ip_address;
UINT         port;

/* Create the UDP socket client_socket and
   allocate the packet pointed to by packet_ptr (not shown). */

/* Extract the IP address and port of the packet received on the UDP
   socket specified in the packet interface. */
status = nxd_udp_source_extract(&packet_ptr, &ip_address, &port);

/* If status == NX_SUCCESS, the source IP address and port of the
   packet received on the UDP socket was successfully extracted. */
```
### <a name="see-also"></a>참고 항목

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send