---
title: 4장 - Azure RTOS NetX 서비스 설명
description: 이 장에서는 모든 Azure RTOS NetX 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f1ebbd4d78f96a257fc6cf62474917a1d618524ff6f27f99c108f904589f84fe
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801940"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a>4장 - Azure RTOS NetX 서비스 설명

이 장에서는 모든 Azure RTOS NetX 서비스를 알파벳 순서로 설명합니다. 서비스 이름은 모든 유사한 서비스가 함께 그룹화되도록 설계되었습니다. 예를 들어 모든 ARP 서비스는 이 장의 시작 부분에 있습니다.

> [!NOTE]
> BSD 호환 소켓 API는 고성능 NetX API를 충분히 활용할 수 없는 레거시 애플리케이션 코드에 사용할 수 있습니다. BSD 호환 소켓 API에 대한 자세한 내용은 부록 D를 참조하세요.

각 설명의 “반환 값” 섹션에서 **BOLD** 로 표시된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 NX_DISABLE_ERROR_CHECKING 옵션의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다. “허용되는 위치” 섹션은 각 NetX 서비스를 호출할 수 있는 항목을 나타냅니다.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

ARP 캐시의 모든 동적 항목을 무효화합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 현재 ARP 캐시에 있는 모든 동적 ARP 항목을 무효화합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP 캐시 무효화에 성공했습니다.
- **NX_NOT_ENABLED**(0x14) ARP가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 주소입니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send
- nx_arp_hardware_address_find, nx_arp_info_get
- nx_arp_ip_address_find, nx_arp_static_entries_delete
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

동적 ARP 항목을 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Description

이 서비스는 ARP 캐시의 동적 항목을 할당하고 지정된 IP를 물리적 주소 매핑으로 설정합니다. 물리적 주소를 0으로 지정하면 물리적 주소를 확인하기 위해 실제 ARP 요청이 네트워크로 송신됩니다. 이 항목은 ARP 에이징이 활성인 경우 또는 ARP 캐시가 고갈되어 오래전에 사용된 ARP 항목인 경우에도 제거됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 매핑할 IP 주소입니다.
- **physical_msw** 물리적 주소의 상위 16비트(47-32)입니다.
- **physical_lsw** 물리적 주소의 하위 32비트(31-0)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP 동적 항목 설정에 성공했습니다.
- **NX_NO_MORE_ENTRIES**(0x17) ARP 캐시에 사용할 수 있는 ARP 항목이 더 이상 없습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 인스턴스 포인터입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate, nx_arp_enable
- nx_arp_gratuitous_send, nx_arp_hardware_address_find
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_enable"></a>nx_arp_enable

ARP(주소 확인 프로토콜)를 사용하도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a>Description

이 서비스는 특정 IP 인스턴스에 대해 NetX의 ARP 구성 요소를 초기화합니다. ARP 초기화에는 ARP 메시지 송신 및 수신에 필요한 ARP 캐시와 다양한 ARP 처리 루틴 설정이 포함됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **arp_cache_memory** ARP 캐시를 지정할 메모리 영역에 대한 포인터입니다.
- **arp_cache_size** 각 ARP 항목은 52바이트이므로 총 ARP 항목 수는 52로 나뉘는 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP를 사용하도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 캐시 메모리 포인터입니다.
- **NX_SIZE_ERROR**(0x09) 사용자 제공 ARP 캐시 메모리가 너무 작습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_ALREADY_ENABLED**(0x15) 이 구성 요소는 이미 사용하도록 설정되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set
- nx_arp_gratuitous_send, nx_arp_hardware_address_find
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

무상 ARP 요청을 송신합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Description

이 서비스는 인터페이스 IP 주소가 유효하면 모든 실제 인터페이스를 통해 무상 ARP 요청을 전송합니다. 이어서 ARP 응답을 수신하면 제공된 응답 처리기가 호출되어 무상 ARP에 대한 응답을 처리합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **response_handler** 응답 처리 함수에 대한 포인터입니다. NX_NULL이 제공되면 응답은 무시됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 무상 ARP 송신에 성공했습니다.
- **NX_NO_PACKET**(0x01) 사용할 수 있는 패킷이 없습니다.
- **NX_NOT_ENABLED**(0x14) ARP가 사용하도록 설정되지 않았습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 현재 IP 주소가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드가 아닙니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set
- nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get
- nx_arp_ip_address_find, nx_arp_static_entries_delete
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

제공된 IP 주소에 해당하는 물리적 하드웨어 주소를 찾습니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a>Description

이 서비스는 제공된 IP 주소와 연결된 ARP 캐시에서 물리적 하드웨어 주소를 찾으려고 시도합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 검색할 IP 주소입니다.
- **physical_msw** 물리적 주소의 상위 16비트(47-32)를 반환하는 변수에 대한 포인터입니다.
- **physical_lsw** 물리적 주소의 하위 32비트(31-0)를 반환하는 변수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP 하드웨어 주소 찾기에 성공했습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) ARP 캐시에서 매핑을 찾을 수 없습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 메모리 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set
- nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get
- nx_arp_ip_address_find, nx_arp_static_entries_delete
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_info_get"></a>nx_arp_info_get

ARP 활동에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
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

대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **arp_requests_sent** 이 IP 인스턴스에서 송신된 총 ARP 요청 대상에 대한 포인터입니다.
- **arp_requests_received** 네트워크에서 수신된 총 ARP 요청 대상에 대한 포인터입니다.
- **arp_responses_sent** 이 IP 인스턴스에서 송신된 총 ARP 응답 대상에 대한 포인터입니다.
- **arp_responses_received** 네트워크에서 수신된 총 ARP 응답 대상에 대한 포인터입니다.
- **arp_dynamic_entries** 현재 동적 ARP 항목 수 대상에 대한 포인터입니다.
- **arp_static_entries** 현재 고정 ARP 항목 수 대상에 대한 포인터입니다.
- **arp_aged_entries** 오래되고 잘못된 총 ARP 항목 수 대상에 대한 포인터입니다.
- **arp_invalid_messages** 수신되었으나 잘못된 총 ARP 메시지 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
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

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set
- nx_arp_enable, nx_arp_gratuitous_send
- nx_arp_hardware_address_find, nx_arp_ip_address_find
- nx_arp_static_entries_delete, nx_arp_static_entry_create
- nx_arp_static_entry_delete

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

제공된 물리적 주소에 해당하는 IP 주소를 찾습니다.

### <a name="prototype"></a>프로토타입

```C
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
- **ip_address** 매핑된 IP 주소가 있는 경우, 반환 IP 주소에 대한 포인터입니다.
- **physical_msw** 검색할 물리적 주소의 상위 16비트(47-32)입니다.
- **physical_lsw** 검색할 물리적 주소의 하위 32비트(31-0)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP IP 주소 찾기에 성공했습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) ARP 캐시에서 매핑을 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 메모리 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PARAMETERS**(0x4D) Physical_msw 및 physical_lsw는 둘 다 0입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set
- nx_arp_enable, nx_arp_gratuitous_send
- nx_arp_hardware_address_find, nx_arp_info_get
- nx_arp_static_entries_delete,nx_arp_static_entry_create
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

모든 고정 ARP 항목을 삭제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 ARP 캐시의 모든 고정 항목을 삭제합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 고정 항목이 삭제됩니다.
- **NX_PTR_ERROR**(0x07) 잘못된 ip_ptr 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set
- nx_arp_enable, nx_arp_gratuitous_send
- nx_arp_hardware_address_find, nx_arp_info_get
- nx_arp_ip_address_find, nx_arp_static_entry_create
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

ARP 캐시에 고정 IP-하드웨어 매핑을 만듭니다.

### <a name="prototype"></a>프로토타입

```C
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

- **NX_SUCCESS**(0x00) ARP 고정 항목 만들기에 성공했습니다.
- **NX_NO_MORE_ENTRIES**(0x17) ARP 캐시에 사용할 수 있는 ARP 항목이 더 이상 없습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PARAMETERS**(0x4D) Physical_msw 및 physical_lsw는 둘 다 0입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set
- nx_arp_enable, nx_arp_gratuitous_send
- nx_arp_hardware_address_find, nx_arp_info_get
- nx_arp_ip_address_find, nx_arp_static_entries_delete
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

ARP 캐시에서 고정 IP-하드웨어 매핑을 삭제합니다.


### <a name="prototype"></a>프로토타입

```C
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
- **physical_msw** 정적으로 매핑된 물리적 주소의 상위 16비트(47-32)입니다.
- **physical_lsw** 정적으로 매핑된 물리적 주소의 하위 32비트(31-0)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ARP 고정 항목 삭제에 성공했습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) ARP 캐시에서 고정 ARP 항목을 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.
- **NX_INVALID_PARAMETERS**(0x4D) Physical_msw 및 physical_lsw는 둘 다 0입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a>참고 항목

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set
- nx_arp_enable, nx_arp_gratuitous_send
- nx_arp_hardware_address_find, nx_arp_info_get
- nx_arp_ip_address_find, nx_arp_static_entries_delete
- nx_arp_static_entry_create

## <a name="nx_icmp_enable"></a>nx_icmp_enable

ICMP(Internet Control Message Protocol)를 사용하도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 ICMP 구성 요소를 사용하도록 설정합니다.
ICMP 구성 요소는 인터넷 오류 메시지와 ping 요청 및 회신을 처리해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ICMP를 사용하도록 설정하는 데 성공했습니다.
- **NX_ALREADY_ENABLED**(0x15) ICMP는 이미 사용하도록 설정되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a>참고 항목

- nx_icmp_info_get, nx_icmp_ping

## <a name="nx_icmp_info_get"></a>nx_icmp_info_get

ICMP 활동에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
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

대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **pings_sent** 송신된 총 ping 수 대상에 대한 포인터입니다.
- **ping_timeouts** 총 ping 시간 제한 수 대상에 대한 포인터입니다.
- **ping_threads_suspended** ping 요청에서 일시 중단된 총 스레드 수 대상에 대한 포인터입니다.
- **ping_responses_received** 수신된 총 ping 응답 수 대상에 대한 포인터입니다.
- **icmp_checksum_errors** 총 ICMP 체크섬 오류 수 대상에 대한 포인터입니다.
- **icmp_unhandled_messages** 처리되지 않은 총 ICMP 메시지 수 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ICMP 정보 검색에 성공했습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a>참고 항목

- nx_icmp_enable, nx_icmp_ping

## <a name="nx_icmp_ping"></a>nx_icmp_ping

지정된 IP 주소로 ping 요청을 송신합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 주소로 ping 요청을 송신하고 지정된 시간 동안 ping 응답 메시지를 기다립니다. 응답이 수신되지 않는 경우 오류가 반환됩니다. 응답이 수신되는 경우 response_ptr이 가리키는 변수에 전체 응답 메시지가 반환됩니다.

NX_SUCCESS가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 이 패킷을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 호스트 바이트 순서대로 표시된 ping할 IP 주소입니다. ping 메시지의 데이터 영역에 대한 데이터 포인터입니다.
- **data_size** ping 데이터의 바이트 수입니다.
- **response_ptr** ping 응답 메시지를 반환하는 패킷 포인터에 대한 포인터입니다.
- **wait_option** ping 응답 대기 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.

  - NX_NO_WAIT(0x00000000)
  - NX_WAIT_FOREVER(0xFFFFFFFF)
  - 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) ping에 성공했습니다. response_ptr이 가리키는 변수에 응답 메시지 포인터가 배치되었습니다.
- **NX_NO_PACKET**(0x01) ping 요청 패킷을 할당할 수 없습니다.
- **NX_OVERFLOW**(0x03) 지정된 데이터 영역은 이 IP 인스턴스의 기본 패킷 크기를 초과합니다.
- **NX_NO_RESPONSE**(0x29) 요청된 IP에서 응답하지 않았습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 응답 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
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

- nx_icmp_enable, nx_icmp_info_get

## <a name="nx_igmp_enable"></a>nx_igmp_enable

IGMP(Internet Group Management Protocol)를 사용하도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스에서 IGMP 구성 요소를 사용하도록 설정합니다.
IGMP 구성 요소는 IP 멀티캐스트 그룹 관리 작업에 대한 지원을 제공해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IGMP를 사용하도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_ALREADY_ENABLED**(0x15) 이 구성 요소는 이미 사용하도록 설정되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a>참고 항목

- nx_igmp_info_get, nx_igmp_loopback_disable
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join
- nx_igmp_multicast_join, nx_igmp_multicast_leave

## <a name="nx_igmp_info_get"></a>nx_igmp_info_get

IGMP 활동에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 IGMP 활동에 대한 정보를 검색합니다.

대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **igmp_reports_sent** 송신된 총 ICMP 보고서 수 대상에 대한 포인터입니다.
- **igmp_queries_received** 멀티캐스트 라우터에 수신된 총 쿼리 수 대상에 대한 포인터입니다.
- **igmp_checksum_errors** 수신 패킷의 총 IGMP 체크섬 오류 수 대상에 대한 포인터입니다.
- **current_groups_joined** 이 IP 인스턴스를 통해 가입된 현재 그룹 수 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IGMP 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a>참고 항목

- nx_igmp_enable, nx_igmp_loopback_disable
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join
- nx_igmp_multicast_join, nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

IGMP 루프백을 사용하지 않도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 가입된 모든 후속 멀티캐스트 그룹에 대해 IGMP 루프백을 사용하지 않도록 설정합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) IGMP 루프백을 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_NOT_ENABLED**(0x14) IGMP가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a>참고 항목

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join
- nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

IGMP 루프백을 사용하도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 가입된 모든 후속 멀티캐스트 그룹에 대해 IGMP 루프백을 사용하도록 설정합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) IGMP 루프백을 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_NOT_ENABLED**(0x14) IGMP가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a>참고 항목

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join

인터페이스를 통해 IP 인스턴스를 지정된 멀티캐스트 그룹에 가입합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a>Description

이 서비스는 지정된 네트워크 인터페이스를 통해 IP 인스턴스를 지정된 멀티캐스트 그룹에 가입합니다. 동일한 그룹이 가입된 횟수를 추적하도록 내부 카운터가 유지 관리됩니다. 멀티캐스트 그룹에 가입한 후에는 IGMP 구성 요소가 지정된 네트워크 인터페이스를 통해 이 그룹 주소를 사용하는 IP 패킷의 수신을 허용하며 이 IP가 이 멀티캐스트 그룹의 멤버임을 라우터에 보고합니다. IGMP 멤버 자격 가입, 보고, 탈퇴 메시지도 지정된 네트워크 인터페이스를 통해 송신됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **group_address** 호스트 바이트 순서대로 표시된 가입할 클래스 D IP 멀티캐스트 그룹 주소입니다.
- **interface_index** NetX 인스턴스에 연결된 인터페이스 인덱스입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 멀티캐스트 그룹 가입에 성공했습니다.
- **NX_NO_MORE_ENTRIES**(0x17) 멀티캐스트 그룹을 더 이상 가입할 수 없습니다. 최댓값이 초과되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못된 네트워크 인터페이스를 가리킵니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 제공된 멀티캐스트 그룹 주소가 잘못된 클래스 D 주소입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) IP 멀티캐스트 지원이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a>참고 항목

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable
- nx_igmp_loopback_enable, nx_igmp_multicast_join
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

IP 인스턴스를 지정된 멀티캐스트 그룹에 가입합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Description

이 서비스는 IP 인스턴스를 지정된 멀티캐스트 그룹에 가입합니다. 동일한 그룹이 가입된 횟수를 추적하도록 내부 카운터가 유지 관리됩니다. 호스트가 그룹을 가입하려는 것을 나타내는, 네트워크에서 송신된 첫 번째 가입 요청인 경우 드라이버에서 IGMP 보고서 송신 명령이 실행됩니다. 가입 후에는 IGMP 구성 요소가 이 그룹 주소를 사용하는 IP 패킷을 수신할 수 있으며 이 IP는 해당 멀티캐스트 그룹의 멤버임을 라우터에 보고합니다.

> [!NOTE]
> 기본 디바이스가 아닌 디바이스에서 멀티캐스트 그룹을 가입하려면 **nx_igmp_multicast_interface_join** 서비스를 사용합니다.

- **매개 변수**

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **group_address** 가입할 클래스 D IP 멀티캐스트 그룹 주소입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 멀티캐스트 그룹 가입에 성공했습니다.
- **NX_NO_MORE_ENTRIES**(0x17) 멀티캐스트 그룹을 더 이상 가입할 수 없습니다. 최댓값이 초과되었습니다.
- **NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못된 네트워크 인터페이스를 가리킵니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 그룹 주소입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a>참고 항목

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

IP 인스턴스가 지정된 멀티캐스트 그룹에서 탈퇴하도록 합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Description

이 서비스를 사용하면 탈퇴 요청 수와 가입 요청 수가 일치하는 경우 IP 인스턴스가 지정된 멀티캐스트 그룹에서 탈퇴하도록 합니다. 일치하지 않으면 내부 가입 수만 감소합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **group_address** 나갈 멀티캐스트 그룹입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 멀티캐스트 그룹 가입에 성공했습니다.
- **NX_ENTRY_NOT_FOUND**(0x16) 이전 가입 요청을 찾을 수 없습니다.
- **NX_INVALID_INTERFACE**(0x4C) 디바이스 인덱스가 잘못된 네트워크 인터페이스를 가리킵니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 그룹 주소입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>참고 항목

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join
- nx_igmp_multicast_join

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy

IP 주소가 변경되면 애플리케이션에 알립니다.


### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a>Description

이 서비스는 IP 주소가 변경될 때마다 호출되는 애플리케이션 알림 함수를 등록합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **change_notify** IP 변경 알림 함수에 대한 포인터입니다. 이 매개 변수가 NX_NULL이면 IP 주소 변경 알림이 사용하지 않도록 설정됩니다.
- **additional_info** IP 주소가 변경되면 알림 함수에도 제공되는 선택적 추가 정보에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 주소 변경 알림에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete
- nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable, nx_ip_forwarding_enable
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_address_get"></a>nx_ip_address_get

IP 주소 및 네트워크 마스크를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Description

이 서비스는 기본 네트워크 인터페이스의 IP 주소 및 해당 서브넷 마스크를 검색합니다.

*보조 디바이스에 대한 정보를 가져오려면 다음 서비스를 사용합니다.
- **nx_ip_interface_address_get***

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** IP 주소 대상에 대한 포인터입니다.
- **network_mask** 네트워크 마스크 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 주소 가져오기에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 반환 변수 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create
- nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable
- nx_ip_forwarding_enable, nx_ip_fragment_disable
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check
- nx_system_initialize

## <a name="nx_ip_address_set"></a>nx_ip_address_set

IP 주소 및 네트워크 마스크를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Description

이 서비스는 기본 네트워크 인터페이스의 IP 주소 및 네트워크 마스크를 설정합니다.

보조 디바이스의 IP 주소 및 네트워크 마스크를 설정하려면 **nx_ip_interface_address_set** 서비스를 사용합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 새 IP 주소입니다.
- **network_mask** 새 네트워크 마스크입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 주소 설정에 성공했습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create
- nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable
- nx_ip_forwarding_enable, nx_ip_fragment_disable
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check
- nx_system_initialize

## <a name="nx_ip_create"></a>nx_ip_create

IP 인스턴스를 만듭니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
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

- **ip_ptr** 새 IP 인스턴스를 만들 제어 블록에 대한 포인터입니다.
- **name** 새 IP 인스턴스의 이름입니다.
- **ip_address** 새 IP 인스턴스의 IP 주소입니다.
- **network_mask** 서브넷 및 슈퍼넷 지정에 사용할 IP 주소의 네트워크 부분을 나타내는 마스크입니다.
- **default_pool** 이전에 만든 NetX 패킷 풀의 제어 블록에 대한 포인터입니다.
- **ip_network_driver** IP 패킷 송신 및 수신에 사용되는 사용자 제공 네트워크 드라이버입니다.
- **memory_ptr** IP 도우미 스레드 스택 영역의 메모리 영역에 대한 포인터입니다.
- **memory_size** IP 도우미 스레드 스택의 메모리 영역 바이트 수입니다.
- **priority** IP 도우미 스레드 우선 순위입니다.

### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) IP 인스턴스 만들기에 성공했습니다.
- **NX_NOT_IMPLEMENTED**(0x4A) NetX 라이브러리가 잘못 구성되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP, 네트워크 드라이버 함수 포인터, 패킷 풀 또는 메모리 포인터입니다.
- **NX_SIZE_ERROR**(0x09) 제공된 스택 크기가 너무 작습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 제공된 IP 주소가 잘못되었습니다.
- **NX_OPTION_ERROR**(0x21) 제공된 IP 스레드 우선 순위가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable
- nx_ip_forwarding_enable, nx_ip_fragment_disable
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check
- nx_system_initialize

## <a name="nx_ip_delete"></a>nx_ip_delete

이전에 만든 IP 인스턴스를 삭제합니다.


### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 IP 인스턴스를 삭제하고 IP 인스턴스가 소유하는 모든 시스템 리소스를 해제합니다.

### <a name="parameters"></a>매개 변수
- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 삭제에 성공했습니다.
- **NX_SOCKETS_BOUND**(0x28) 이 IP 인스턴스는 여전히 UDP 또는 TCP 소켓과 바인딩되어 있습니다. IP 인스턴스를 삭제하려면 먼저 모든 소켓을 바인딩 해제하고 삭제해야 합니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable
- nx_ip_forwarding_enable, nx_ip_fragment_disable
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check
- nx_system_initialize

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

네트워크 드라이버에 대해 명령을 실행합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Description

이 서비스는 ***nx_ip_create*** 호출 중 지정된 애플리케이션의 기본 네트워크 인터페이스 드라이버에 대해 직접 인터페이스를 제공합니다.

애플리케이션별 명령을 사용하면 NX_LINK_USER_COMMAND 이상의 숫자 값을 제공할 수 있습니다.

보조 디바이스에 대해 명령을 실행하려면 **nx_ip_driver_interface_direct_command** 서비스를 사용합니다.

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

- **return_value_ptr** 호출자의 반환 변수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 네트워크 드라이버 직접 명령이 성공했습니다.
- **NX_UNHANDLED_COMMAND**(0x44) 처리되지 않거나 구현되지 않은 네트워크 드라이버 명령입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 반환 값 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_INVALID_INTERFACE**(0x4C) 잘못된 인터페이스 인덱스입니다.

### <a name="allowed-from"></a>허용 위치

스레드

- **가능한 선점**

예

### <a name="example"></a>예제

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable, nx_ip_forwarding_enable
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command

네트워크 드라이버에 대해 명령을 실행합니다.

### <a name="prototype"></a>프로토타입

```C
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
- **return_value_ptr** 호출자의 반환 변수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) 네트워크 드라이버 직접 명령이 성공했습니다.
- **NX_UNHANDLED_COMMAND**(0x44) 처리되지 않거나 구현되지 않은 네트워크 드라이버 명령입니다.
- **NX_INVALID_INTERFACE**(0x4C) 잘못된 인터페이스 인덱스입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 반환 값 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
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

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_forwarding_disable, nx_ip_forwarding_enable
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

IP 패킷 전달을 사용하지 않도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 NetX IP 구성 요소 내부에서 IP 패킷 전달을 사용하지 않도록 설정합니다. IP 작업을 만들 때 이 서비스는 자동으로 사용하지 않도록 설정됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 전달을 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

IP 패킷 전달을 사용하도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 NetX IP 구성 요소 내부에서 IP 패킷 전달을 사용하도록 설정합니다. IP 작업을 만들 때 이 서비스는 자동으로 사용하지 않도록 설정됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) IP 전달을 사용하도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

IP 패킷 조각화를 사용하지 않도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 IP 패킷 조각화 및 리어셈블 기능을 사용하지 않도록 설정합니다. 이 서비스는 리어셈블 대기 중인 패킷이 있는 경우 해당 패킷을 해제합니다. IP 작업을 만들 때 이 서비스는 자동으로 사용하지 않도록 설정됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) IP 조각화를 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) IP 인스턴스에서 IP 조각화가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable
- nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

IP 패킷 조각화를 사용하도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 IP 패킷 조각화 및 리어셈블 기능을 사용하도록 설정합니다. IP 작업을 만들 때 이 서비스는 자동으로 사용하지 않도록 설정됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 조각화를 사용하도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) NetX에 IP 조각화 기능이 컴파일되어 있지 않습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable
- nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

게이트웨이 IP 주소를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a>Description

이 서비스는 IP 게이트웨이 IP 주소를 설정합니다. 전송을 위한 네트워크 외부 트래픽은 모두 이 게이트웨이로 라우트됩니다. 게이트웨이는 네트워크 인터페이스 중 하나를 통해 직접 액세스할 수 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_address** 게이트웨이 IP 주소입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 게이트웨이 IP 주소 설정에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 인스턴스 포인터입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a>참고 항목

- nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete

## <a name="nx_ip_info_get"></a>nx_ip_info_get

IP 활동에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
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

대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **ip_total_packets_sent** 송신된 총 IP 패킷 수 대상에 대한 포인터입니다.
- **ip_total_bytes_sent** 송신된 총 바이트 수 대상에 대한 포인터입니다.
- **ip_total_packets_received** 총 IP 수신 패킷 수 대상에 대한 포인터입니다.
- **ip_total_bytes_received** 수신된 총 IP 바이트 수 대상에 대한 포인터입니다.
- **ip_invalid_packets** 잘못된 총 IP 패킷 수 대상에 대한 포인터입니다.
- **ip_receive_packets_dropped** 삭제된 총 수신 패킷 수 대상에 대한 포인터입니다.
- **ip_receive_checksum_errors** 수신 패킷의 총 체크섬 오류 수 대상에 대한 포인터입니다.
- **ip_send_packets_dropped** 삭제된 총 송신 패킷 수 대상에 대한 포인터입니다.
- **ip_total_fragments_sent** 송신된 총 조각 수 대상에 대한 포인터입니다.
- **ip_total_fragments_received** 수신된 총 조각 수 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 정보 검색에 성공했습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
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

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable
- nx_ip_forwarding_enable, nx_ip_fragment_disable
- nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get

인터페이스 IP 주소를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Description

이 서비스는 지정된 네트워크 인터페이스의 IP 주소를 검색합니다.

기본 디바이스가 아닌 경우 지정된 디바이스가 이전에 이미 IP 인스턴스에 연결되어 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **interface_index** 인터페이스 인덱스로, IP 인스턴스에 연결된 네트워크 인터페이스의 인덱스와 값이 동일합니다.
- **ip_address** 디바이스 인터페이스 IP 주소 대상에 대한 포인터입니다.
- **network_mask** 디바이스 인터페이스 네트워크 마스크 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 주소 가져오기에 성공했습니다.
- **NX_INVALID_INTERFACE**(0x4C) 지정된 네트워크 인터페이스가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_set, nx_ip_interface_attach
- nx_ip_interface_info_get, nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set

인터페이스 IP 주소 및 네트워크 마스크를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인터페이스의 IP 주소 및 네트워크 마스크를 설정합니다.

지정된 인터페이스가 이전에 이미 IP 인스턴스에 연결되어 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **interface_index** NetX 인스턴스에 연결된 인터페이스 인덱스입니다.
- **ip_address** 새 네트워크 인터페이스 IP 주소입니다.
- **network_mask** 새 인터페이스 네트워크 마스크입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 주소 설정에 성공했습니다.
- **NX_INVALID_INTERFACE**(0x4C) 지정된 네트워크 인터페이스가 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get, nx_ip_interface_attach
- nx_ip_interface_info_get, nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach

IP 인스턴스에 네트워크 인터페이스를 연결합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a>Description

이 서비스는 IP 인터페이스에 실제 네트워크 인터페이스를 추가합니다. IP 인스턴스는 기본 인터페이스를 사용하여 만들어지므로 각각의 추가 인터페이스는 기본 인터페이스에 대한 보조 인스턴스가 됩니다. IP 인스턴스에 연결된 총 네트워크 인터페이스 수(기본 인터페이스 포함)는 **NX_MAX_PHYSICAL_INTERFACES** 를 초과할 수 없습니다.

IP 스레드가 아직 실행되지 않은 경우 모든 실제 인터페이스를 초기화하는 IP 스레드 시작 프로세스의 일부로 보조 인터페이스가 초기화됩니다.

IP 스레드가 아직 실행되고 있지 않으면 보조 인터페이스가 ***nx_ip_interface_attach*** 서비스의 일부로 초기화됩니다.

ip_ptr은 유효한 NetX IP 구조를 가리켜야 합니다.

- IP 인스턴스의 네트워크 인터페이스 수에 대한 **NX_MAX_PHYSICAL_INTERFACES** 를 구성해야 합니다. 기본값은 1입니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **interface_name** 인터페이스 이름 문자열에 대한 포인터입니다.
- **ip_address** 호스트 바이트 순서대로 표시된 디바이스 IP 주소입니다.
- **network_mask** 호스트 바이트 순서대로 표시된 디바이스 네트워크 마스크입니다.
- **ip_link_driver** 인터페이스 이더넷 드라이버입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 항목이 고정 라우팅 테이블에 추가됩니다.
- **NX_NO_MORE_ENTRIES**(0x17) 최대 인터페이스 수입니다.
- **NX_MAX_PHYSICAL_INTERFACES** 를 초과했습니다.
- **NX_DUPLICATED_ENTRY**(0x52) 제공된 IP 주소는 이 IP 인스턴스에서 이미 사용되고 있습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터 입력입니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소 입력입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
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

- nx_ip_interface_address_get, nx_ip_interface_address_set
- nx_ip_interface_info_get, nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

네트워크 인터페이스 매개 변수를 검색합니다.


### <a name="prototype"></a>프로토타입

```C
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

ip_ptr은 유효한 NetX IP 구조를 가리켜야 합니다. 기본 인터페이스가 아닌 경우 지정된 인터페이스가 이전에 이미 IP 인스턴스에 연결되어 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **interface_index** 네트워크 인터페이스를 지정하는 인덱스입니다.
- **interface_name** 네트워크 인터페이스 이름이 포함된 버퍼에 대한 포인터입니다.
- **ip_address** 인터페이스 IP 주소 대상에 대한 포인터입니다.
- **network_mask** 네트워크 마스크 대상에 대한 포인터입니다.
- **mtu_size** 이 인터페이스의 최대 전송 단위 대상에 대한 포인터입니다.
- **physical_address_msw** 디바이스 MAC 주소의 상위 16비트 대상에 대한 포인터입니다.
- **physical_address_lsw** 디바이스 MAC 주소의 하위 32비트 대상에 대한 포인터입니다.


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

```C
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

- nx_ip_interface_address_get, nx_ip_interface_address_set
- nx_ip_interface_attach, nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check

IP 인스턴스의 상태를 확인합니다.


### <a name="prototype"></a>프로토타입

```C
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
- **interface_index** 인터페이스 인덱스 번호입니다.
- **needed_status** 요청된 IP 상태이며 다음과 같이 비트맵 형식으로 정의됩니다.
    - NX_IP_INITIALIZE_DONE(0x0001)
    - NX_IP_ADDRESS_RESOLVED(0x0002)
    - NX_IP_LINK_ENABLED(0x0004)
    - NX_IP_ARP_ENABLED(0x0008)
    - NX_IP_UDP_ENABLED(0x0010)
    - NX_IP_TCP_ENABLED(0x0020)
    - NX_IP_IGMP_ENABLED(0x0040)
    - NX_IP_RARP_COMPLETE(0x0080)
    - NX_IP_INTERFACE_LINK_ENABLED(0x0100)
- **actual_status** 설정된 실제 비트 대상에 대한 포인터입니다.
- **wait_option** 요청된 상태 비트를 사용할 수 없는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
    - NX_NO_WAIT(0x00000000)
    - NX_WAIT_FOREVER(0xFFFFFFFF)
    - 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 상태 확인에 성공했습니다.
- **NX_NOT_SUCCESSFUL**(0x43) 지정된 시간 제한 내에 상태 요청이 충족되지 않았습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었거나 잘못된 상태였거나, 실제 상태 포인터가 잘못되었습니다.
- **NX_OPTION_ERROR**(0x0a) 필요한 상태 옵션이 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_INVALID_INTERFACE**(0x4C) Interface_index가 범위를 벗어났습니다. 또는 인터페이스가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get, nx_ip_interface_address_set
- nx_ip_interface_attach, nx_ip_interface_info_get
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set

링크 상태 변경 알림 콜백 함수를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a>Description

이 서비스는 링크 상태 변경 알림 콜백 함수를 구성합니다. 기본 또는 보조 인터페이스 상태가 변경되는 경우(예: IP 주소가 변경되는 경우) 사용자 제공 *link_status_change_notify* 루틴이 호출됩니다. *link_status_change_notify* 가 NULL인 경우 링크 상태 변경 알림 콜백 기능이 사용하지 않도록 설정됩니다.

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

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_interface_address_get, nx_ip_interface_address_set
- nx_ip_interface_attach, nx_ip_interface_info_get
- nx_ip_interface_status_check

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

원시 패킷 송신/수신을 사용하지 않도록 설정합니다.


### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 이 IP 인스턴스의 원시 IP 패킷 전송 및 수신을 사용하지 않도록 설정합니다. 이전에 원시 패킷 서비스를 사용하도록 설정했으며 수신 큐에 원시 패킷이 있는 경우 이 서비스는 수신된 원시 패킷을 모두 해제합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 원시 패킷을 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_enable, nx_ip_raw_packet_receive
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

원시 패킷 처리를 사용하도록 설정합니다.


### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 이 IP 인스턴스에 대해 원시 IP 패킷 전송 및 수신을 사용할 수 있도록 설정합니다. 수신 TCP, UDP, ICMP 및 IGMP 패킷은 여전히 NetX에서 처리됩니다. 상위 계층 프로토콜 유형을 알 수 없는 패킷은 원시 패킷 수신 루틴에서 처리됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 원시 패킷을 사용하도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_disable, nx_ip_raw_packet_receive
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_interface_send"></a>nx_ip_raw_packet_interface_send

지정된 네트워크 인터페이스를 통해 원시 IP 패킷을 송신합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a>Description

이 서비스는 지정된 로컬 IP 주소를 원본 주소로 사용하고 연결된 네트워크 인터페이스를 통해 원시 IP 패킷을 대상 IP 주소로 송신합니다. 이 루틴은 즉시 반환되므로 IP 패킷이 실제로 송신되었는지를 알 수 없습니다. 네트워크 드라이버는 전송이 완료되면 패킷을 해제해야 합니다. 이 서비스는 패킷이 실제로 송신되었는지를 알 방법이 없다는 점에서 다른 서비스와 다릅니다. 패킷이 인터넷에서 손실될 수도 있습니다.

원시 IP 처리는 사용하도록 설정되어 있어야 합니다.

이 서비스는 애플리케이션이 지정된 실제 인터페이스에서 원시 IP 패킷을 송신하도록 허용하는 점을 제외하고는 **nx_ip_raw_packet_send** 와 유사합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 작업에 대한 포인터입니다.
- **packet_ptr** 전송할 패킷에 대한 포인터입니다.
- **destination_ip** 패킷을 송신할 IP 주소입니다.
- **address_index** 패킷을 송신할 인터페이스 주소 인덱스입니다.
- **type_of_service** 패킷 서비스 유형입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷이 성공적으로 전송되었습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 사용할 수 있는 적절한 발신 인터페이스가 없습니다.
- **NX_NOT_ENABLED**(0x14) 원시 IP 패킷 처리가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
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

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable
- nx_ip_raw_packet_receive, nx_ip_raw_packet_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

원시 IP 패킷을 수신합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스에서 원시 IP 패킷을 수신합니다. 원시 패킷 수신 큐에 IP 패킷이 있는 경우 첫 번째(가장 오래된) 패킷이 호출자에게 반환됩니다. 그러지 않고 사용할 수 있는 패킷이 없는 경우 대기 옵션에 지정된 대로 호출자가 일시 중단될 수 있습니다.

*NX_SUCCESS* 가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 이 패킷을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **packet_ptr** 수신된 원시 IP 패킷이 배치될 포인터에 대한 포인터입니다.
- **wait_option** 사용할 수 있는 원시 IP 패킷이 없는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

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

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

원시 IP 패킷을 송신합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a>Description

이 서비스는 원시 IP 패킷을 대상 IP 주소로 송신합니다. 이 루틴은 즉시 반환되므로 IP 패킷이 실제로 송신되었는지를 알 수 없습니다. 네트워크 드라이버는 전송이 완료되면 패킷을 해제해야 합니다.

멀티홈 시스템의 경우 NetX는 대상 IP 주소를 사용하여 적절한 네트워크 인터페이스를 찾고 인터페이스의 IP 주소를 원본 주소로 사용합니다. 대상 IP 주소가 브로드캐스트 또는 멀티캐스트면 유효한 첫 번째 인터페이스가 사용됩니다. 이 경우 애플리케이션은 ***nx_ip_raw_packet_interface_send*** 를 사용합니다.

오류가 반환되지 않는 한 이 호출 후 애플리케이션은 패킷을 해제하면 안 됩니다. 애플리케이션이 패킷을 해제하면 전송 후 네트워크 드라이버가 패킷을 해제하므로 예측할 수 없는 결과가 발생합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **packet_ptr** 송신할 원시 IP 패킷에 대한 포인터입니다.
- **destination_ip** 대상 IP 주소로, 특정 호스트 IP 주소나 네트워크 브로드캐스트, 내부 루프백, 멀티캐스트 주소일 수 있습니다.
- **type_of_service** 전송할 서비스 유형을 정의합니다. 올바른 값은 다음과 같습니다.
- NX_IP_NORMAL(0x00000000)
- NX_IP_MIN_DELAY(0x00100000)
- NX_IP_MAX_DATA(0x00080000)
- NX_IP_MAX_RELIABLE(0x00040000)
- NX_IP_MIN_COST(0x00020000)


### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 원시 패킷 송신에 성공했습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.
- **NX_NOT_ENABLED**(0x14) 원시 IP 기능이 사용하도록 설정되지 않았습니다.
- **NX_OPTION_ERROR**(0x0A) 잘못된 유형의 서비스입니다.
- **NX_UNDERFLOW**(0x02) 공간이 부족하여 패킷에서 IP 헤더를 앞에 추가할 수 없습니다.
- **NX_OVERFLOW**(0x03) 패킷 뒤에 추가 포인터가 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 패킷 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable
- nx_ip_raw_packet_receive, nx_ip_raw_packet_send
- nx_ip_raw_packet_interface_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

라우팅 테이블에 고정 경로를 추가합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a>Description

이 서비스는 고정 라우팅 테이블에 항목을 추가합니다. 로컬 네트워크 디바이스 중 하나에서 *next_hop* 주소에 직접 액세스할 수 있어야 합니다.

이 서비스를 사용하려면 ip_ptr이 유효한 NetX IP 구조를 가리켜야 하며 NX_ENABLE_IP_STATIC_ROUTING이 정의된 NetX 라이브러리가 빌드되어 있어야 합니다. 기본적으로 NetX는 NX_ENABLE_IP_STATIC_ROUTING이 정의되지 않은 상태로 빌드됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **network_address** 호스트 바이트 순서대로 표시된 대상 네트워크 주소입니다.
- **net_mask** 호스트 바이트 순서대로 표시된 대상 네트워크 마스크입니다.
- **next_hop** 호스트 바이트 순서대로 표시된 대상 네트워크의 다음 홉 주소입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 항목이 고정 라우팅 테이블에 추가됩니다.
- **NX_OVERFLOW**(0x03) 고정 라우팅 테이블이 꽉 찼습니다.
- **NX_NOT_SUPPORTED**(0x4B) 이 기능은 컴파일되어 있지 않습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 로컬 인터페이스를 통해 다음 홉에 직접 액세스할 수 없습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 ip_ptr 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

라우팅 테이블에서 고정 경로를 삭제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a>Description

이 서비스는 고정 라우팅 테이블에서 항목을 삭제합니다.

이 서비스를 사용하려면 ip_ptr이 유효한 NetX IP 구조를 가리켜야 하며 NX_ENABLE_IP_STATIC_ROUTING이 정의된 NetX 라이브러리가 빌드되어 있어야 합니다. 기본적으로 NetX는 NX_ENABLE_IP_STATIC_ROUTING이 정의되지 않은 상태로 빌드됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **network_address** 호스트 바이트 순서대로 표시된 대상 네트워크 주소입니다.
- **net_mask** 호스트 바이트 순서대로 표시된 대상 네트워크 마스크입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add

## <a name="nx_ip_status_check"></a>nx_ip_status_check

IP 인스턴스의 상태를 확인합니다.

### <a name="prototype"></a>프로토타입

```C
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
- NX_IP_INITIALIZE_DONE(0x0001)
- NX_IP_ADDRESS_RESOLVED(0x0002)
- NX_IP_LINK_ENABLED(0x0004)
- NX_IP_ARP_ENABLED(0x0008)
- NX_IP_UDP_ENABLED(0x0010)
- NX_IP_TCP_ENABLED(0x0020)
- NX_IP_IGMP_ENABLED(0x0040)
- NX_IP_RARP_COMPLETE(0x0080)
- NX_IP_INTERFACE_LINK_ENABLED(0x0100)
- **actual_status** 설정된 실제 비트 대상에 대한 포인터입니다.
- **wait_option** 요청된 상태 비트를 사용할 수 없는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) IP 상태 확인에 성공했습니다.
- **NX_NOT_SUCCESSFUL**(0x43) 지정된 시간 제한 내에 상태 요청이 충족되지 않았습니다.
- **NX_PTR_ERROR**(0x07) IP 포인터가 잘못되었거나 잘못된 상태였거나, 실제 상태 포인터가 잘못되었습니다.
- **NX_OPTION_ERROR**(0x0a) 필요한 상태 옵션이 잘못되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable
- nx_ip_forwarding_enable, nx_ip_fragment_disable
- nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize

## <a name="nx_packet_allocate"></a>nx_packet_allocate

지정된 풀에서 패킷을 할당합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 풀의 패킷을 할당하고 지정된 패킷의 유형에 따라 패킷의 앞에 추가 포인터를 조정합니다. 사용할 수 있는 패킷이 없는 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 이전에 만든 패킷 풀에 대한 포인터입니다.
- **packet_ptr** 할당된 패킷 포인터의 포인터에 대한 포인터입니다.
- **packet_type** 요청된 패킷의 유형을 정의합니다. 지원되는 패킷 유형 목록은 3장의 49페이지에서 “패킷 풀”을 참조하세요.
- **wait_option** 패킷 풀에서 사용할 수 있는 패킷이 없는 경우의 틱 단위 대기 시간을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷 할당에 성공했습니다.
- **NX_NO_PACKET**(0x01) 사용할 수 있는 패킷이 없습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 패킷 크기가 프로토콜을 지원할 수 없습니다.
- **NX_OPTION_ERROR**(0x0A) 잘못된 패킷 유형입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 풀 또는 패킷 반환 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 비스레드의 대기 옵션이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머, ISR(애플리케이션 네트워크 드라이버)입니다. ISR 또는 타이머 컨텍스트에서 사용되는 경우 대기 옵션은 NX_NO_WAIT여야 합니다.

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a>참고 항목

- nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_pool_info_get, nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy

패킷을 복사합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 제공된 패킷 풀에서 할당된 하나 이상의 새 패킷에 제공된 패킷의 정보를 복사합니다. 성공하면 새 패킷에 대한 포인터가 **new_packet_ptr** 에서 가리키는 대상에 반환됩니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 원본 패킷에 대한 포인터입니다.
- **new_packet_ptr** 패킷의 새 복사본에 대한 포인터를 반환할 위치 대상에 대한 포인터입니다.
- **pool_ptr** 복사본에 대해 패킷을 하나 이상 할당하는 데 사용되는, 이전에 만든 패킷 풀에 대한 포인터입니다.
- **wait_option** 사용할 수 있는 패킷이 없는 경우 서비스가 대기하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

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

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a>참고 항목

- nx_packet_allocate, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_pool_info_get, nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append

패킷 끝에 데이터를 추가합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 패킷 끝에 데이터를 추가합니다. 제공된 데이터 영역은 패킷으로 복사됩니다. 사용할 수 있는 메모리가 부족하며 연결된 패킷 기능이 사용하도록 설정된 경우 패킷을 하나 이상 할당하여 요청을 충족합니다. 연결된 패킷 기능이 사용하도록 설정되지 않는 경우 *NX_SIZE_ERROR* 가 반환됩니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 패킷 포인터입니다.
- **data_start** 패킷 뒤에 추가할 사용자 데이터 영역 시작 부분에 대한 포인터입니다.
- **data_size** 사용자 데이터 영역 크기입니다.
- **pool_ptr** 현재 패킷에 공간이 충분하지 않은 경우 다른 패킷을 할당할 패킷 풀에 대한 포인터입니다.
- **wait_option** 사용할 수 있는 패킷이 없는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷 뒤에 추가에 성공했습니다.
- **NX_NO_PACKET**(0x01) 사용할 수 있는 패킷이 없습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 *tx_thread_wait_abort* 호출에 의해 중단되었습니다.
- **NX_INVALID_PARAMETERS**(0x4D) 패킷 크기가 프로토콜을 지원할 수 없습니다.
- **NX_UNDERFLOW**(0x02) 앞에 추가 포인터가 페이로드 시작보다 먼저입니다.
- **NX_OVERFLOW**(0x03) 뒤에 추가 포인터가 페이로드 종료보다 나중입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 풀, 패킷 또는 데이터 포인터입니다.
- **NX_SIZE_ERROR**(0x09) 잘못된 데이터 크기입니다.
- **NX_CALLER_ERROR**(0x11) 비스레드의 대기 옵션이 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머, ISR(애플리케이션 네트워크 드라이버)입니다.

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a>참고 항목

- nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset

오프셋을 통해 패킷에서 데이터를 추출합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a>Description

이 서비스는 패킷 앞에 추가 포인터의 지정된 오프셋에서 시작하여 지정된 크기(바이트)의 NetX 패킷(또는 패킷 체인) 데이터를 지정된 버퍼에 복사합니다. 실제로 복사된 바이트 수는 *bytes_copied* 로 반환됩니다. 이 서비스는 패킷에서 데이터를 제거하지 않으며 앞에 추가 포인터 또는 다른 내부 상태 정보도 조정하지 않습니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 추출할 패킷에 대한 포인터입니다.
- **offset** 현재 앞에 추가 포인터의 오프셋입니다.
- **buffer_start** 저장 버퍼 시작 부분에 대한 포인터입니다.
- **buffer_length** 복사할 바이트 수입니다.
- **bytes_copied** 실제로 복사된 바이트 수입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷 복사에 성공했습니다.
- **NX_PACKET_OFFSET_ERROR**(0x53) 잘못된 오프셋 값을 제공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 패킷 포인터 또는 버퍼 포인터입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a>참고 항목

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

패킷에서 데이터를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a>Description

이 서비스는 제공된 패킷의 데이터를 제공된 버퍼에 복사합니다. 복사된 실제 바이트 수는 **bytes_copied** 가 가리키는 대상에 반환됩니다.

이 서비스는 패킷의 내부 상태를 변경하지 않습니다. 검색되는 데이터는 패킷에서 계속 사용할 수 있습니다.

‘대상 버퍼는 패킷 콘텐츠를 포함할 수 있도록 크기가 충분히 커야 합니다. 그러지 않으면 메모리가 손상되어 예기치 않은 결과가 발생합니다.’

### <a name="parameters"></a>매개 변수

- **packet_ptr** 원본 패킷에 대한 포인터입니다.
- **buffer_start** 버퍼 영역의 시작 부분에 대한 포인터입니다.
- **bytes_copied** 복사된 바이트 수 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷 데이터 검색에 성공했습니다.
- **NX_INVALID_PACKET**(0x12) 잘못된 패킷입니다.
- **NX_PTR_ERROR**(0x07) 패킷, 버퍼 시작 또는 복사된 바이트 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a>참고 항목

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_length_get
- nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_pool_info_get, nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get

패킷 데이터의 길이를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a>Description

이 서비스는 지정된 패킷에서 데이터의 길이를 가져옵니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 패킷에 대한 포인터입니다.
- **length** 패킷 길이 대상입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a>참고 항목

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve
- nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_pool_info_get, nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create

지정된 메모리 영역에 패킷 풀을 만듭니다.

### <a name="prototype"></a>프로토타입

```C
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

- **pool_ptr** 패킷 풀 제어 블록에 대한 포인터입니다.
- **name** 패킷 풀의 애플리케이션 이름에 대한 포인터입니다.
- **payload_size** 풀에 있는 각 패킷의 바이트 수입니다. 이 값은 40바이트 이상이어야 하며 4로 균등하게 나뉘어야 합니다.
- **memory_ptr** 패킷 풀을 배치할 메모리 영역에 대한 포인터입니다. 이 포인터는 ULONG 경계에 맞춰야 합니다.
- **memory_size** 풀 메모리 영역의 크기입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷 풀을 만드는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 풀 또는 메모리 포인터입니다.
- **NX_SIZE_ERROR**(0x09) 잘못된 블록 또는 메모리 크기입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a>참고 항목

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve
- nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

이전에 만든 패킷 풀을 삭제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 패킷 풀을 삭제합니다. NetX는 패킷 풀의 패킷에서 현재 일시 중단된 스레드가 있는지 확인하고 일시 중단을 해제합니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 패킷 풀 제어 블록 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷 풀 삭제에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 풀 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a>참고 항목

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve
- nx_packet_length_get, nx_packet_pool_create
- nx_packet_pool_info_get, nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

패킷 풀에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
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

대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 이전에 만든 패킷 풀에 대한 포인터입니다.
- **total_packets** 풀의 총 패킷 수 대상에 대한 포인터입니다.
- **free_packets** 현재 사용 가능한 총 패킷 수 대상에 대한 포인터입니다.
- **empty_pool_requests** 풀이 비어 있는 경우의 총 할당 요청 수 대상에 대한 포인터입니다.
- **empty_pool_suspensions** 비어 있는 풀의 총 일시 중단 수 대상에 대한 포인터입니다.
- **invalid_packet_releases** 잘못된 총 패킷 해제 수 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷 풀 정보를 검색하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
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

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release

이전에 할당된 패킷을 해제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 패킷에 연결된 추가 패킷을 포함하여 패킷을 해제합니다. 다른 스레드가 패킷 할당에서 차단된 경우 이 서비스가 해당 패킷에 제공되고 계속 진행됩니다.

패킷을 두 번 이상 해제하면 예기치 않은 결과가 발생할 수 있으므로 애플리케이션은 패킷을 한 번만 해제하도록 해야 합니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 패킷 포인터입니다.


### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) 패킷 해제에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 패킷 포인터입니다.
- **NX_UNDERFLOW**(0x02) 앞에 추가 포인터가 페이로드 시작보다 먼저입니다.
- **NX_OVERFLOW**(0x03) 뒤에 추가 포인터가 페이로드 종료보다 나중입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머, ISR(애플리케이션 네트워크 드라이버)입니다.

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a>참고 항목

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_pool_info_get, nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

전송된 패킷을 해제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

TCP가 아닌 패킷의 경우 이 서비스는 지정된 패킷에 연결된 추가 패킷을 포함하여 전송된 패킷을 해제합니다. 다른 스레드가 패킷 할당에서 차단된 경우 이 서비스가 해당 패킷에 제공되고 계속 진행됩니다. 전송된 TCP 패킷의 경우 패킷이 전송 중으로 표시되지만 패킷이 확인될 때까지 해제되지 않습니다. 이 서비스는 일반적으로 패킷이 전송된 후 애플리케이션 네트워크 드라이버에서 호출됩니다.

네트워크 드라이버는 이 서비스를 호출하기 전에 실제 미디어 헤더를 제거하고 패킷 길이를 조정해야 합니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 패킷 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 전송 패킷 해제에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 패킷 포인터입니다.
- **NX_UNDERFLOW**(0x02) 앞에 추가 포인터가 페이로드 시작보다 먼저입니다.
- **NX_OVERFLOW**(0x03) 뒤에 추가 포인터가 페이로드 종료보다 나중입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머, 애플리케이션 네트워크 드라이버(ISR 포함)입니다.

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a>참고 항목

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_pool_info_get, nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable

RARP(역주소 확인 프로토콜)를 사용하지 않도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 특정 IP 인스턴스에 대해 NetX의 RARP 구성 요소를 사용하지 않도록 설정합니다. 멀티홈 시스템의 경우 이 서비스는 모든 인터페이스에서 RARP를 사용하지 않도록 설정합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) RARP를 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_NOT_ENABLED**(0x14) RARP가 사용하지 않도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a>참고 항목

- nx_rarp_enable, nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable

RARP(역주소 확인 프로토콜)를 사용하도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 특정 IP 인스턴스에 대해 NetX의 RARP 구성 요소를 사용하도록 설정합니다. RARP 구성 요소는 모든 연결된 네트워크 인터페이스에서 0으로 된 IP 주소를 검색합니다. 0으로 된 IP 주소는 인터페이스에 IP 주소 할당이 아직 없는 것을 나타냅니다. RARP는 해당 인터페이스에서 RARP 프로세스를 사용하도록 설정하여 IP 주소를 확인하려고 시도합니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) RARP를 사용하도록 설정하는 데 성공했습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) IP 주소가 이미 유효합니다.
- **NX_ALREADY_ENABLED**(0x15) RARP가 이미 사용하도록 설정되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a>참고 항목

- nx_rarp_disable, nx_rarp_info_get

## <a name="nx_rarp_info_get"></a>nx_rarp_info_get

RARP 활동에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 RARP 활동에 대한 정보를 검색합니다.

대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **rarp_requests_sent** 송신된 총 RARP 요청 수 대상에 대한 포인터입니다.
- **rarp_responses_received** 수신된 총 RARP 응답 수 대상에 대한 포인터입니다.
- **rarp_invalid_messages** 잘못된 총 메시지 수 대상에 대한 포인터입니다.


### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) RARP 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a>참고 항목

- nx_rarp_disable, nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize

NetX 시스템을 초기화합니다.

### <a name="prototype"></a>프로토타입

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a>Description

이 서비스는 사용을 위한 준비로 기본 NetX 시스템 리소스를 초기화합니다. 초기화 중 다른 NetX 호출이 수행되기 전에 애플리케이션에서 이 서비스가 호출되어야 합니다.

### <a name="parameters"></a>매개 변수

없음

### <a name="return-values"></a>반환 값

없음

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a>참고 항목

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable
- nx_ip_forwarding_enable, nx_ip_fragment_disable
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

클라이언트 TCP 소켓을 TCP 포트에 바인딩합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 TCP 클라이언트 소켓을 지정된 TCP 포트에 바인딩합니다. 유효한 TCP 소켓 범위는 0에서 0xFFFF까지입니다. 지정된 TCP 포트를 사용할 수 없는 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓 인스턴스에 대한 포인터입니다.
- **port** 바인딩할 포트 번호(1-0xFFFF)입니다. 포트 번호가 NX_ANY_PORT(0x0000)인 경우 IP 인스턴스는 가능한 다음 포트를 검색하여 바인딩에 사용합니다.
- **wait_option** 포트가 이미 다른 소켓에 바인딩되어 있는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓 바인딩에 성공했습니다.
- **NX_ALREADY_BOUND**(0x22) 이 소켓은 다른 TCP 포트에 이미 바인딩되어 있습니다.
- **NX_PORT_UNAVAILABLE**(0x23) 포트가 이미 다른 소켓에 바인딩되어 있습니다.
- **NX_NO_FREE_PORTS**(0x45) 사용 가능한 포트가 없습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 *tx_thread_wait_abort* 호출에 의해 중단되었습니다.
- **NX_INVALID_PORT**(0x46) 잘못된 포트입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find
- nx_tcp_info_get, nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available, nx_tcp_socket_create
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

클라이언트 TCP 소켓을 연결합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 바인딩된 TCP 클라이언트 소켓을 지정된 서버 포트에 연결합니다. 유효한 TCP 서버 포트의 범위는 0에서 0xFFFF까지입니다. 연결이 즉시 완료되지 않으면 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓 인스턴스에 대한 포인터입니다.
- **server_ip** 서버의 IP 주소입니다.
- **server_port** 연결할 서버 포트 번호(1-0xFFFF)입니다.
- **wait_option** 연결이 설정되는 동안 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

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
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find
- nx_tcp_info_get, nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available, nx_tcp_socket_create
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

클라이언트 TCP 소켓에 바인딩된 포트 번호를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a>Description

이 서비스는 소켓에 연결된 포트 번호를 검색합니다. 소켓이 바인딩될 때 NX_ANY_PORT가 지정된 경우 NetX에서 할당한 포트를 찾는 데 유용합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓 인스턴스에 대한 포인터입니다.
- **port_ptr** 반환 포트 번호 대상에 대한 포인터입니다. 유효한 포트 번호는 (1-0xFFFF)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓 바인딩에 성공했습니다.
- **NX_NOT_BOUND**(0x24) 이 소켓은 포트에 바인딩되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터 또는 포트 반환 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find
- nx_tcp_info_get, nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available, nx_tcp_socket_create
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

TCP 포트에서 TCP 클라이언트 소켓 바인딩을 해제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

이 서비스는 TCP 클라이언트 소켓과 TCP 포트 간에 바인딩을 해제합니다. 다른 소켓을 동일한 포트 번호에 바인딩하려고 대기 중인 다른 스레드가 있는 경우 첫 번째 일시 중단된 스레드가 이 포트에 바인딩됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓을 바인딩 해제하는 데 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.
- **NX_NOT_CLOSED**(0x35) 소켓이 연결 해제되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find
- nx_tcp_info_get, nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available, nx_tcp_socket_create
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_enable"></a>nx_tcp_enable

NetX의 TCP 구성 요소를 사용하도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 NetX의 TCP(Transmission Control Protocol) 구성 요소를 사용하도록 설정합니다. 사용하도록 설정하면 애플리케이션에서 TCP 연결을 설정할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TCP를 사용하도록 설정하는 데 성공했습니다.
- **NX_ALREADY_ENABLED**(0x15) TCP는 이미 사용하도록 설정되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available, nx_tcp_socket_create
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

사용할 수 있는 다음 TCP 포트를 찾습니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션 제공 포트에서 시작하여 사용 가능한 TCP 포트(바인딩되지 않은 포트)를 찾으려고 합니다. 검색에서 최대 포트 값인 0xFFFF에 도달하면 검색 논리가 래핑됩니다. 검색에 성공하면 *free_port_ptr* 이 가리키는 변수에 사용 가능한 포트가 반환됩니다.

이 서비스는 다른 스레드에서 호출될 수 있으며 동일한 포트를 반환할 수 있습니다. 이러한 경합 상태를 방지하기 위해 애플리케이션은 이 서비스 및 실제 클라이언트 소켓 바인딩에 뮤텍스 보호가 적용되도록 할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **port** 검색을 시작할 포트 번호(1-0xFFFF)입니다.
- **free_port_ptr** 사용 가능한 포트 반환 값 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 사용 가능한 포트를 찾는 데 성공했습니다.
- **NX_NO_FREE_PORTS**(0x45) 사용 가능한 포트를 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PORT**(0x46) 지정된 포트 번호가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available, nx_tcp_socket_create
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get

TCP 활동에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
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

대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **tcp_packets_sent** 송신된 총 TCP 패킷 수 대상에 대한 포인터입니다.
- **tcp_bytes_sent** 송신된 총 TCP 바이트 수 대상에 대한 포인터입니다.
- **tcp_packets_received** 수신된 총 TCP 패킷 수 대상에 대한 포인터입니다.
- **tcp_bytes_received** 수신된 총 TCP 바이트 수 대상에 대한 포인터입니다.
- **tcp_invalid_packets** 잘못된 총 TCP 패킷 수 대상에 대한 포인터입니다.
- **tcp_receive_packets_dropped** 삭제된 총 TCP 수신 패킷 수 대상에 대한 포인터입니다.
- **tcp_checksum_errors** 체크섬 오류가 있는 총 TCP 패킷 수 대상에 대한 포인터입니다.
- **tcp_connections** 총 TCP 연결 수 대상에 대한 포인터입니다.
- **tcp_disconnections** 총 TCP 연결 해제 수 대상에 대한 포인터입니다.
- **tcp_connections_dropped** 삭제된 총 TCP 연결 수 대상에 대한 포인터입니다.
- **tcp_retransmit_packets** 재전송된 총 TCP 패킷 수 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TCP 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available, nx_tcp_socket_create
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

TCP 연결을 수락합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 수신 대기에 사용하도록 설정한 포트에 대한 TCP 클라이언트 소켓 연결 요청을 수락하거나 수락하기 위해 준비합니다. 애플리케이션이 수신 대기 또는 다시 수신 대기 서비스를 호출한 직후 이 서비스가 호출될 수도 있고, 클라이언트 연결이 실제로 있을 때 수신 콜백 루틴을 호출한 직후 이 서비스가 호출될 수도 있습니다. 즉시 연결을 설정할 수 없는 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.

연결이 더 이상 필요하지 않으면 서버 포트에 대한 서버 소켓 바인딩을 제거하도록 애플리케이션이 ***nx_tcp_server_socket_unaccept*** 를 호출해야 합니다.

애플리케이션 콜백 루틴은 IP 도우미 스레드 내에서 호출됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** TCP 서버 소켓 제어 블록에 대한 포인터입니다.
- **wait_option** 연결이 설정되는 동안 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)


### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) TCP 서버 소켓을 수락(수동 연결)하는 데 성공했습니다.
- **NX_NOT_LISTEN_STATE**(0x36) 제공된 서버 소켓이 수신 대기 상태가 아닙니다.
- **NX_IN_PROGRESS**(0x37) 대기하도록 지정되지 않았으며, 연결하려고 시도하는 중입니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 *tx_thread_wait_abort* 호출에 의해 중단되었습니다.
- **NX_PTR_ERROR**(0x07) 소켓 포인터 오류입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
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
        created */

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available, nx_tcp_socket_create
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

TCP 포트에서 클라이언트 연결 수신 대기를 사용하도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a>Description

이 서비스는 지정된 TCP 포트에서 클라이언트 연결 요청 수신 대기를 사용하도록 설정합니다. 클라이언트 연결 요청이 수신되면 제공된 서버 소켓이 지정된 포트에 바인딩되고 제공된 수신 대기 콜백 함수가 호출됩니다.

수신 대기 콜백 루틴 처리는 애플리케이션에 따라 다릅니다. 수락 작업에 이어 수행되는 애플리케이션 스레드 절전 모드 해제 논리가 포함되어 있을 수 있습니다. 이 소켓에 대해 수락 처리가 일시 중단된 스레드가 이미 애플리케이션에 있는 경우 수신 대기 콜백 루틴이 필요하지 않을 수 있습니다.

애플리케이션이 동일한 포트에서 추가 클라이언트 연결을 처리하려는 경우 다음 연결에 사용할 수 있는 소켓(CLOSED 상태의 소켓)이 포함된 ***nx_tcp_server_socket_relisten*** 을 호출해야 합니다. 다시 수신 대기 서비스가 호출될 때까지 추가 클라이언트 연결은 큐에 대기됩니다. 최대 큐 크기를 초과하는 경우 새 연결 요청이 큐에 대기될 수 있도록 가장 오래된 연결 요청이 삭제됩니다. 최대 큐 크기는 이 서비스에서 지정합니다.

애플리케이션 콜백 루틴은 내부 IP 도우미 스레드에서 호출됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **port** 수신 대기할 포트 번호(1-0xFFFF)입니다.
- **socket_ptr** 연결에 사용할 소켓에 대한 포인터입니다.
- **listen_queue_size** 큐에 대기될 수 있는 클라이언트 연결 요청 수입니다.
- **listen_callback** 연결이 수신되면 호출할 애플리케이션 함수입니다. NULL을 지정하면 수신 대기 콜백 기능을 사용하지 않도록 설정합니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TCP 포트 수신 대기를 사용하도록 설정하는 데 성공했습니다.
- **NX_MAX_LISTEN**(0x33) 수신 대기 요청 구조를 더 이상 사용할 수 없습니다. nx_api.h의 상수 NX_MAX_LISTEN_REQUESTS는 가능한 활성 수신 대기 요청 수를 정의합니다.
- **NX_NOT_CLOSED**(0x35) 제공된 서버 소켓이 닫힘 상태가 아닙니다.
- **NX_ALREADY_BOUND**(0x22) 제공된 서버 소켓이 이미 포트에 바인딩되어 있습니다.
- **NX_DUPLICATE_LISTEN**(0x34) 이 포트의 활성 수신 대기 요청이 이미 있습니다.
- **NX_INVALID_PORT**(0x46) 잘못된 포트가 지정되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
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
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available, nx_tcp_socket_create
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

TCP 포트에서 클라이언트 연결을 위해 다시 수신 대기합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

이전에 수신 대기에 사용하도록 설정한 포트에서 연결을 수신하면 이 서비스가 호출됩니다. 이 서비스는 다음 클라이언트 연결에 사용하도록 새 서버 소켓을 제공하기 위한 것입니다. 연결 요청이 큐에 있는 경우 이 서비스 호출 중에 바로 연결이 처리됩니다.

새 서버 소켓에 대한 연결이 있는 경우 원래 수신 대기 요청에서 지정한 것과 동일한 콜백 루틴도 호출됩니다.

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
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
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
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available, nx_tcp_socket_create
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

수신 대기 포트와 소켓 간 연결을 제거합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

이 서비스는 이 서버 소켓과 지정된 서버 포트 간 연결을 제거합니다. 애플리케이션은 연결 해제 후 또는 호출 수락 실패 후 이 서비스를 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 설정한 서버 소켓 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 서버 소켓을 수락하지 않는 데 성공했습니다.
- **NX_NOT_LISTEN_STATE**(0x36) 서버 소켓이 부적절한 상태이며 연결 해제되었을 수 있습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
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
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
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
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

TCP 포트에서 클라이언트 연결 수신 대기를 사용하지 않도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
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
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept
- nx_tcp_socket_bytes_available, nx_tcp_socket_create
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

검색에 사용할 수 있는 바이트 수를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a>Description

이 서비스는 지정된 TCP 소켓에서 검색에 사용할 수 있는 바이트 수를 가져옵니다. TCP 소켓은 이미 연결되어 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만들고 연결한 TCP 소켓에 대한 포인터입니다.
- **bytes_available** 사용할 수 있는 바이트 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 서비스가 성공적으로 실행되었습니다. 읽을 수 있는 바이트 수가 호출자에게 반환됩니다.
- **NX_NOT_CONNECTED**(0x38) 소켓이 연결된 상태가 아닙니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.
- **NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten, nx_tcp_socket_create
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

TCP 클라이언트 또는 서버 소켓을 만듭니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 TCP 클라이언트 또는 서버 소켓을 만듭니다.

애플리케이션 콜백 루틴은 이 IP 인스턴스와 연결된 스레드에서 호출됩니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **socket_ptr** 새 TCP 소켓 제어 블록에 대한 포인터입니다.
- **name** 이 TCP 소켓의 애플리케이션 이름입니다.
- **type_of_service** 전송할 서비스 유형을 정의합니다. 올바른 값은 다음과 같습니다.

- NX_IP_NORMAL(0x00000000)
- NX_IP_MIN_DELAY(0x00100000)
- NX_IP_MAX_DATA(0x00080000)
- NX_IP_MAX_RELIABLE(0x00040000)
- NX_IP_MIN_COST(0x00020000)

- **fragment** IP 조각화 허용 여부를 지정합니다. NX_FRAGMENT_OKAY(0x0)가 지정되면 IP 조각화가 허용됩니다. NX_DONT_FRAGMENT(0x4000)가 지정되면 IP 조각화가 사용하지 않도록 설정됩니다.
- **time_to_live** 이 패킷이 제거되기 전까지 통과할 수 있는 라우터 수를 정의하는 8비트 값을 지정합니다. 기본값은 NX_IP_TIME_TO_LIVE로 지정합니다.
- **window_size** 이 소켓의 수신 큐에 허용되는 최대 바이트 수를 정의합니다.
- **urgent_data_callback** 수신 스트림에서 긴급 데이터가 검색될 때마다 호출되는 애플리케이션 함수입니다. 이 값이 NX_NULL이면 긴급 데이터는 무시됩니다.
- **disconnect_callback** 연결의 다른 쪽 끝에 있는 소켓이 연결을 해제할 때마다 호출되는 애플리케이션 함수입니다. 이 값이 NX_NULL이면 연결 해제 콜백 함수는 사용하지 않도록 설정됩니다.

### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) TCP 클라이언트 소켓 만들기에 성공했습니다.
- **NX_OPTION_ERROR**(0x0A) type-of-service, fragment, window size 또는 time-tolive 옵션이 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화 및 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available
- nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

TCP 소켓을 삭제합니다.

### <a name="prototype"></a>프로토타입

```C
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
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available
- nx_tcp_socket_create, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

클라이언트 및 서버 소켓 연결을 해제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 설정된 클라이언트 또는 서버 소켓 연결을 해제합니다. 먼저 요청을 거부한 후 서버 소켓 연결을 해제해야 하며 연결이 해제된 클라이언트 소켓은 다른 연결 요청에 사용할 준비가 된 상태로 남아 있습니다. 연결 해제 프로세스를 즉시 완료할 수 없는 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 연결된 클라이언트 또는 서버 소켓 인스턴스에 대한 포인터입니다.
- **wait_option** 연결 해제가 진행 중인 동안 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓 연결 해제에 성공했습니다.
- **NX_NOT_CONNECTED**(0x38) 지정된 소켓이 연결되어 있지 않습니다.
- **NX_IN_PROGRESS**(0x37) 대기 안 함으로 지정되었으므로 연결 해제가 진행 중입니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify

TCP 연결 해제 완료 알림 콜백 함수를 설치합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

이 서비스는 소켓 연결 해제 작업이 완료된 후 호출되는 콜백 함수를 등록합니다. TCP 소켓 연결 해제 완료 콜백 함수는 옵션

- ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** 가 정의된 NetX가 빌드되어 있는 경우 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 연결된 클라이언트 또는 서버 소켓 인스턴스에 대한 포인터입니다.
- **tcp_disconnect_complete_notify** 설치할 콜백 함수입니다.

### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) 콜백 함수를 성공적으로 등록했습니다.
- **NX_NOT_SUPPORTED**(0x4B) 확장된 알림 기능은 NetX 라이브러리에 빌드되어 있지 않습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify

TCP 설정 알림 콜백 함수를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

이 서비스는 콜백 함수를 등록합니다. 이 함수는 TCP 소켓이 연결된 후 호출됩니다. TCP 소켓 설정 콜백 함수는 옵션 ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** 가 정의된 NetX가 빌드되어 있는 경우 사용할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 연결된 클라이언트 또는 서버 소켓 인스턴스에 대한 포인터입니다.
- **tcp_establish_notify** TCP 연결이 설정된 후 호출되는 콜백 함수입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 알림 함수를 성공적으로 설정했습니다.
- **NX_NOT_SUPPORTED**(0x4B) 확장된 알림 기능은 NetX 라이브러리에 빌드되어 있지 않습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 애플리케이션에서 TCP를 사용하도록 설정하지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable, nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

TCP 소켓 활동에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
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

대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓 인스턴스에 대한 포인터입니다.
- **tcp_packets_sent** 소켓의 송신된 총 TCP 패킷 수 대상에 대한 포인터입니다.
- **tcp_bytes_sent** 소켓의 송신된 총 TCP 바이트 수 대상에 대한 포인터입니다.
- **tcp_packets_received** 소켓의 수신된 총 TCP 패킷 수 대상에 대한 포인터입니다.
- **tcp_bytes_received** 소켓의 수신된 총 TCP 바이트 수 대상에 대한 포인터입니다.
- **tcp_retransmit_packets** 총 TCP 패킷 재전송 수 대상에 대한 포인터입니다.
- **tcp_packets_queued** 소켓의 큐에 대기된 총 TCP 패킷 수 대상에 대한 포인터입니다.
- **tcp_checksum_errors** 소켓의 체크섬 오류가 있는 총 TCP 패킷 수 대상에 대한 포인터입니다.
- **tcp_socket_state** 소켓의 현재 상태 대상에 대한 포인터입니다.
- **tcp_transmit_queue_depth** 여전히 큐에서 ACK를 대기 중인 총 전송 패킷 수 대상에 대한 포인터입니다.
- **tcp_transmit_window** 현재 전송 창 크기 대상에 대한 포인터입니다.
- **tcp_receive_window** 현재 수신 창 크기 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) TCP 소켓 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="return-values"></a>반환 값

```C
/* Retrieve TCP socket information from previously created socket_0.*/
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

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Retrieve TCP socket information from previously created socket_0.*/
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

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

소켓의 MSS를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Description

이 서비스는 지정된 소켓의 로컬 MSS(최대 세그먼트 크기)를 검색합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 소켓에 대한 포인터입니다.
- **mss** MSS 반환 대상입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) MSS를 가져오는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 또는 MSS 대상 포인터입니다.
- **NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable, nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

피어 TCP 소켓의 MSS를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Description

이 서비스는 피어 소켓에서 보급한 MSS(최대 세그먼트 크기)를 검색합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만들고 연결한 소켓에 대한 포인터입니다.
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

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable, nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

소켓의 MSS를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a>Description

이 서비스는 지정된 소켓의 MSS(최대 세그먼트 크기)를 설정합니다. MSS 값은 네트워크 인터페이스 IP MTU 내에 있어야 하며 IP 및 TCP 헤더 공간이 허용되어야 합니다.

TCP 소켓이 연결 프로세스를 시작하기 전에 이 서비스를 사용해야 합니다. TCP 연결이 설정된 후 이 서비스를 사용하면 새 값이 연결에 영향을 주지 않습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 소켓에 대한 포인터입니다.
- **mss** 설정할 MSS 값입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) MSS 설정에 성공했습니다.
- **NX_SIZE_ERROR**(0x09) 지정된 MSS 값이 너무 큽니다.
- **NX_NOT_CONNECTED**(0x38) TCP 연결이 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 호출자가 스레드나 초기화가 아닙니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable, nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

피어 TCP 소켓에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a>Description

이 서비스는 IP 네트워크를 통해 연결된 TCP 소켓의 피어 IP 주소 및 포트 정보를 검색합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓에 대한 포인터입니다.
- **peer_ip_address** 호스트 바이트 순서대로 표시된 피어 IP 주소 대상에 대한 포인터입니다.
- **peer_port** 호스트 바이트 순서대로 표시된 피어 포트 번호 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 서비스가 성공적으로 실행되었습니다. 피어 IP 주소와 포트 번호는 호출자에게 반환됩니다.
- **NX_NOT_CONNECTED**(0x38) 소켓이 연결된 상태가 아닙니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.
- **NX_NOT_ENABLED**(0x14) TCP가 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable, nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

TCP 소켓에서 데이터를 수신합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 소켓에서 TCP 데이터를 수신합니다. 지정된 소켓에 큐에 대기된 데이터가 없으면 제공된 대기 옵션에 따라 호출자가 일시 중단됩니다.

*NX_SUCCESS* 가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 해당 패킷을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓 인스턴스에 대한 포인터입니다.
- **packet_ptr** TCP 패킷 포인터에 대한 포인터입니다.
- **wait_option** 현재 이 소켓에 큐에 대기된 데이터가 없는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) 소켓 데이터 수신에 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 아직 바인딩되지 않았습니다.
- **NX_NO_PACKET**(0x01) 수신된 데이터가 없습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_NOT_CONNECTED**(0x38) 소켓이 더 이상 연결되어 있지 않습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 또는 반환 패킷 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

/* Receive a packet from the previously created and connected TCP client socket. If no packet is available, wait for 200 timer ticks before giving up. */ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);

/* If status is NX_SUCCESS, the received packet is pointed to by "packet_ptr". */

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

수신된 패킷에 대해 애플리케이션에 알립니다.


### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

이 서비스는 애플리케이션에서 지정한 콜백 함수를 사용하여 수신 알림 함수 포인터를 구성합니다. 그러면 소켓에 하나 이상의 패킷이 수신될 때마다 이 콜백 함수가 호출됩니다. NX_NULL 포인터를 제공하면 알림 함수를 사용하지 않도록 설정합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** TCP 소켓에 대한 포인터입니다.
- **tcp_receive_notify** 소켓에 하나 이상의 패킷이 수신되면 호출되는 애플리케이션 콜백 함수 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓 수신 알림에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable, nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

TCP 소켓을 통해 데이터를 송신합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 연결된 TCP 소켓을 통해 TCP 데이터를 송신합니다. 마지막으로 보급된 수신기 창 크기가 이 요청 미만이면 지정된 대기 옵션에 따라 선택적으로 서비스가 일시 중단됩니다. 이 서비스는 MSS를 초과하는 패킷 데이터가 IP 계층으로 송신되지 않도록 보장합니다.

오류가 반환되지 않는 경우 애플리케이션은 이 호출 후에 패킷을 해제하면 안 됩니다. 해제하면 네트워크 드라이버가 전송 후에도 패킷을 해제하려고 하므로 예측할 수 없는 결과가 발생합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 연결된 TCP 소켓 인스턴스에 대한 포인터입니다.
- **packet_ptr** TCP 데이터 패킷 포인터입니다.
- **wait_option** 요청이 수신기 창 크기를 초과하는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

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
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_UNDERFLOW**(0x02) 패킷 앞에 추가 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait

### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

TCP 소켓이 특정 상태가 될 때까지 대기합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a>Description

이 서비스는 소켓이 원하는 상태가 될 때까지 대기합니다. 소켓이 원하는 상태가 아닌 경우 제공된 대기 옵션에 따라 서비스가 일시 중단됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 연결된 TCP 소켓 인스턴스에 대한 포인터입니다.
- **desired_state** 원하는 TCP 상태입니다. 유효한 TCP 소켓 상태는 다음과 같이 정의됩니다.
- NX_TCP_CLOSED(0x01)
- NX_TCP_LISTEN_STATE(0x02)
- NX_TCP_SYN_SENT(0x03)
- NX_TCP_SYN_RECEIVED(0x04)
- NX_TCP_ESTABLISHED(0x05)
- NX_TCP_CLOSE_WAIT(0x06)
- NX_TCP_FIN_WAIT_1(0x07)
- NX_TCP_FIN_WAIT_2(0x08)
- NX_TCP_CLOSING(0x09)
- NX_TCP_TIMED_WAIT(0x0A)
- NX_TCP_LAST_ACK(0x0B)
- **wait_option** 요청된 상태가 아닌 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) 상태 대기에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_NOT_SUCCESSFUL**(0x43) 지정된 대기 시간 내에 해당 상태가 되지 않았습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_OPTION_ERROR**(0x0A) 원하는 소켓 상태가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback

시간이 지정된 대기 상태 콜백을 설치합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

이 서비스는 TCP 소켓이 시간이 지정된 대기 상태인 경우 호출되는 콜백 함수를 등록합니다. 이 서비스를 사용하려면 옵션 ***NX_ENABLE_EXTENDED_NOTIFY*** 가 정의된 NetX 라이브러리가 빌드되어 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 연결된 클라이언트 또는 서버 소켓 인스턴스에 대한 포인터입니다.
- **tcp_timed_wait_callback** 시간이 지정된 대기 콜백 함수입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 콜백 함수 소켓을 성공적으로 등록했습니다.
- **NX_NOT_SUPPORTED**(0x4B) 확장 알림 기능을 사용하도록 설정하지 않은 상태로 NetX 라이브러리가 빌드되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable, nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

소켓의 전송 매개 변수를 구성합니다.

### <a name="prototype"></a>프로토타입

```C
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

- **socket_ptr** TCP 소켓에 대한 포인터입니다.
- **max_queue_depth** 전송을 위해 큐에 대기될 수 있는 최대 패킷 수입니다.
- **timeout** 패킷을 다시 송신하기 전에 ACK를 기다리는 ThreadX 타이머 틱 수입니다.
- **max_retries** 허용되는 최대 재시도 수입니다.
- **timeout_shift** 각 후속 재시도에 대한 시간 제한을 변경하는 값입니다. 값이 0이면 이어지는 재시도 간 시간 제한이 동일합니다. 값이 1이면 재시도 간 시간 제한이 두 배가 됩니다.

### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) 전송 소켓 구성에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_OPTION_ERROR**(0x0a) 잘못된 큐 깊이 옵션입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable, nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set

애플리케이션에 창 크기 업데이트에 대해 알립니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

이 서비스는 소켓 창 업데이트 콜백 루틴을 설치합니다. 지정된 소켓이 원격 호스트 창 크기 증가를 나타내는 패킷을 수신할 때마다 자동으로 이 루틴이 호출됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 TCP 소켓에 대한 포인터입니다.
- **tcp_window_update_notify** 창 크기가 변경되면 호출되는 콜백 루틴입니다. 값이 NULL이면 창 변경 업데이트를 사용하지 않도록 설정합니다.

### <a name="return-values"></a>반환 값
- **NX_SUCCESS**(0x00) 콜백 루틴이 소켓에 설치되었습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.
- **NX_NOT_ENABLED**(0x14) TCP 기능이 사용하도록 설정되지 않았습니다.


### <a name="allowed-from"></a>허용 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a>참고 항목

- nx_tcp_enable, nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable

NetX의 UDP 구성 요소를 사용하도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Description

이 서비스는 NetX의 UDP(User Datagram Protocol) 구성 요소를 사용하도록 설정합니다. 사용하도록 설정하면 애플리케이션에서 UDP 데이터그램을 송신하고 수신할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) UDP를 사용하도록 설정하는 데 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_ALREADY_ENABLED**(0x15) 이 구성 요소는 이미 사용하도록 설정되었습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a>참고 항목

- nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract
- nx_udp_socket_bind, nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive
- nx_udp_socket_receive_notify, nx_udp_socket_send
- nx_udp_socket_interface_send, nx_udp_socket_unbind
- nx_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

사용할 수 있는 다음 UDP 포트를 찾습니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션 제공 포트 번호에서 시작하여 사용 가능한 UDP 포트(바인딩되지 않은 포트)를 찾습니다. 검색에서 최대 포트 값인 0xFFFF에 도달하면 검색 논리가 래핑됩니다. 검색에 성공하면 *free_port_ptr* 이 가리키는 변수에 사용 가능한 포트가 반환됩니다.

이 서비스는 다른 스레드에서 호출될 수 있으며 동일한 포트를 반환할 수 있습니다. 이러한 경합 상태를 방지하기 위해 애플리케이션은 이 서비스 및 실제 소켓 바인딩에 뮤텍스 보호가 적용되도록 할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **port** 검색을 시작할 포트 번호(1-0xFFFF)입니다.
- **free_port_ptr** 사용 가능한 포트 반환 변수 대상에 대한 포인터입니다.


### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 사용 가능한 포트를 찾는 데 성공했습니다.
- **NX_NO_FREE_PORTS**(0x45) 사용 가능한 포트를 찾을 수 없습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.
- **NX_INVALID_PORT**(0x46) 지정된 포트 번호가 잘못되었습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract
- nx_udp_socket_bind, nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive
- nx_udp_socket_receive_notify, nx_udp_socket_send
- nx_udp_socket_interface_send, nx_udp_socket_unbind
- nx_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get

UDP 활동에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
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

대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **udp_packets_sent** 송신된 총 UDP 패킷 수 대상에 대한 포인터입니다.
- **udp_bytes_sent** 송신된 총 UDP 바이트 수 대상에 대한 포인터입니다.
- **udp_packets_received** 수신된 총 UDP 패킷 수 대상에 대한 포인터입니다.
- **udp_bytes_received** 수신된 총 UDP 바이트 수 대상에 대한 포인터입니다.
- **udp_invalid_packets** 잘못된 총 UDP 패킷 수 대상에 대한 포인터입니다.
- **udp_receive_packets_dropped** 삭제된 총 UDP 수신 패킷 수 대상에 대한 포인터입니다.
- **udp_checksum_errors** 체크섬 오류가 있는 총 UDP 패킷 수 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) UDP 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.


### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract
- nx_udp_socket_bind, nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive
- nx_udp_socket_receive_notify, nx_udp_socket_send
- nx_udp_socket_interface_send, nx_udp_socket_unbind
- nx_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract

UDP 패킷에서 네트워크 매개 변수를 추출합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a>Description

이 서비스는 수신 인터페이스의 수신된 패킷에서 IP 주소, 피어 포트 번호, 프로토콜 유형(이 서비스는 항상 UDP 유형을 반환함) 같은 네트워크 매개 변수를 추출합니다.

### <a name="parameters"></a>매개 변수

- **packet_ptr** 패킷에 대한 포인터입니다.
- **ip_address** 송신기 IP 주소에 대한 포인터입니다.
- **protocol** 프로토콜(UDP)에 대한 포인터입니다.
- **port** 송신기 포트 번호에 대한 포인터입니다.
- **interface_index** 수신 인터페이스 인덱스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷 인터페이스 데이터를 성공적으로 추출했습니다.
- **NX_INVALID_PACKET**(0x12) 패킷에 IP 프레임이 포함되어 있지 않습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터 입력입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_socket_bind, nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive
- nx_udp_socket_receive_notify, nx_udp_socket_send
- nx_udp_socket_interface_send, nx_udp_socket_unbind
- nx_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

UDP 소켓을 UDP 포트에 바인딩합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 UDP 소켓을 지정된 UDP 포트에 바인딩합니다. 유효한 UDP 소켓 범위는 0에서 0xFFFF까지입니다. 요청된 포트 번호가 다른 소켓에 바인딩되어 있으면 이 서비스는 지정된 시간 동안 해당 소켓이 해당 포트 번호에서 바인딩을 해제할 때까지 기다립니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.
- **port** 바인딩할 포트 번호(1-0xFFFF)입니다. 포트 번호가 NX_ANY_PORT(0x0000)인 경우 IP 인스턴스는 가능한 다음 포트를 검색하여 바인딩에 사용합니다.
- **wait_option** 포트가 이미 다른 소켓에 바인딩되어 있는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓 바인딩에 성공했습니다.
- **NX_ALREADY_BOUND**(0x22) 이 소켓은 다른 포트에 이미 바인딩되어 있습니다.
- **NX_PORT_UNAVAILABLE**(0x23) 포트가 이미 다른 소켓에 바인딩되어 있습니다.
- **NX_NO_FREE_PORTS**(0x45) 사용 가능한 포트가 없습니다.
- **NX_WAIT_ABORTED**(0x1A) 요청된 일시 중단이 tx_thread_wait_abort 호출에 의해 중단되었습니다.
- **NX_INVALID_PORT**(0x46) 잘못된 포트가 지정되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive
- nx_udp_socket_receive_notify, nx_udp_socket_send
- nx_udp_socket_interface_send, nx_udp_socket_unbind
- nx_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

검색에 사용할 수 있는 바이트 수를 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a>Description

이 서비스는 지정된 UDP 소켓에서 수신용으로 사용할 수 있는 바이트 수를 검색합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓에 대한 포인터입니다.
- **bytes_available** 사용할 수 있는 바이트 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 사용할 수 있는 바이트 검색에 성공했습니다.
- **NX_NOT_SUCCESSFUL**(0x43) 소켓이 포트에 바인딩되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.
- **NX_NOT_ENABLED**(0x14) UDP 기능이 사용하도록 설정되지 않았습니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive
- nx_udp_socket_receive_notify, nx_udp_socket_send
- nx_udp_socket_interface_send, nx_udp_socket_unbind
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

UDP 소켓 체크섬을 사용하지 않도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 UDP 소켓에서 패킷을 송신하고 수신하는 데 체크섬 논리를 사용하지 않도록 설정합니다. 체크섬 논리를 사용하지 않도록 설정하면 이 소켓을 통해 송신되는 모든 패킷의 UDP 헤더 체크섬 필드에 0값이 로드됩니다. UDP 헤더의 체크섬 값이 0이면 해당 패킷에 대해 체크섬이 계산되지 않음을 수신기에서 알 수 있습니다.

또한, ***NX_DISABLE_UDP_RX_CHECKSUM** _ 및 _ *_NX_DISABLE_UDP_TX_CHECKSUM_**이 각각 정의된 경우에도 UDP 패킷을 수신하고 송신할 때 아무런 영향을 주지 않습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓 체크섬을 사용하지 않도록 설정하는 데 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 바인딩되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive
- nx_udp_socket_receive_notify, nx_udp_socket_send
- nx_udp_socket_interface_send, nx_udp_socket_unbind
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

UDP 소켓 체크섬을 사용하도록 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 UDP 소켓에서 패킷을 송신하고 수신하는 데 체크섬 논리를 사용하도록 설정합니다. 체크섬은 전체 UDP 데이터 영역 및 의사 IP 헤더에 적용됩니다.

또한, **NX_DISABLE_UDP_RX_CHECKSUM** 및 **NX_DISABLE_UDP_TX_CHECKSUM** 이 각각 정의된 경우에도 UDP 패킷을 수신하고 송신할 때 아무런 영향을 주지 않습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓 체크섬을 사용하도록 설정하는 데 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 바인딩되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive
- nx_udp_socket_receive_notify, nx_udp_socket_send
- nx_udp_socket_interface_send, nx_udp_socket_unbind
- nx_udp_source_extract

## <a name="nx_udp_socket_create"></a>nx_udp_socket_create

UDP 소켓을 만듭니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 인스턴스의 UDP 소켓을 만듭니다.

### <a name="parameters"></a>매개 변수

- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터입니다.
- **socket_ptr** 새 UDP 소켓 제어 블록에 대한 포인터입니다.
- **name** 이 UDP 소켓의 애플리케이션 이름입니다.
- **type_of_service** 전송할 서비스 유형을 정의합니다. 올바른 값은 다음과 같습니다.
    - NX_IP_NORMAL(0x00000000)
    - NX_IP_MIN_DELAY(0x00100000)
    - NX_IP_MAX_DATA(0x00080000)
    - NX_IP_MAX_RELIABLE(0x00040000)
    - NX_IP_MIN_COST(0x00020000)
- **fragment** IP 조각화 허용 여부를 지정합니다. NX_FRAGMENT_OKAY(0x0)가 지정되면 IP 조각화가 허용됩니다. NX_DONT_FRAGMENT(0x4000)가 지정되면 IP 조각화가 사용하지 않도록 설정됩니다.
- **time_to_live** 이 패킷이 제거되기 전까지 통과할 수 있는 라우터 수를 정의하는 8비트 값을 지정합니다. 기본값은 NX_IP_TIME_TO_LIVE로 지정합니다.
- **queue_maximum** 이 소켓에 대해 큐에 대기될 수 있는 최대 UDP 데이터그램 수를 정의합니다. 큐 제한에 도달하면 수신된 모든 새 패킷의 가장 오래된 UDP 패킷이 해제됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) UDP 소켓 만들기에 성공했습니다.
- **NX_OPTION_ERROR**(0x0A) type-of-service, fragment 또는 time-to-live 옵션이 잘못되었습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 IP 또는 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화 및 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable, nx_udp_socket_delete
- nx_udp_socket_info_get, nx_udp_socket_port_get
- nx_udp_socket_receive, nx_udp_socket_receive_notify
- nx_udp_socket_send, nx_udp_socket_interface_send
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete

UDP 소켓을 삭제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 UDP 소켓을 삭제합니다. 소켓이 포트에 바인딩된 경우 먼저 소켓 바인딩을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓을 삭제하는 데 성공했습니다.
- **NX_STILL_BOUND**(0x42) 소켓이 여전히 바인딩되어 있습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable, nx_udp_socket_create
- nx_udp_socket_info_get, nx_udp_socket_port_get
- nx_udp_socket_receive, nx_udp_socket_receive_notify
- nx_udp_socket_send, nx_udp_socket_interface_send
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get

UDP 소켓 활동에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```C
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

대상 포인터가 NX_NULL이면 해당 특정 정보가 호출자에게 반환되지 않습니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.
- **udp_packets_sent** 소켓의 송신된 총 UDP 패킷 수 대상에 대한 포인터입니다.
- **udp_bytes_sent** 소켓의 송신된 총 UDP 바이트 수 대상에 대한 포인터입니다.
- **udp_packets_received** 소켓의 수신된 총 UDP 패킷 수 대상에 대한 포인터입니다.
- **udp_bytes_received** 소켓의 수신된 총 UDP 바이트 수 대상에 대한 포인터입니다.
- **udp_packets_queued** 소켓의 큐에 대기된 총 UDP 패킷 수 대상에 대한 포인터입니다.
- **udp_receive_packets_dropped** 큐 크기 초과로 인해 삭제된, 소켓의 총 UDP 수신 패킷 수 대상에 대한 포인터입니다.
- **udp_checksum_errors** 소켓의 체크섬 오류가 있는 총 UDP 패킷 수 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) UDP 소켓 정보 검색에 성공했습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable, nx_udp_socket_create
- nx_udp_socket_delete, nx_udp_socket_port_get
- nx_udp_socket_receive, nx_udp_socket_receive_notify
- nx_udp_socket_send, nx_udp_socket_interface_send
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

UDP 소켓에 바인딩된 포트 번호를 선택합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a>Description

이 서비스는 소켓에 연결된 포트 번호를 검색합니다. 소켓이 바인딩될 때 NX_ANY_PORT가 지정된 경우 NetX에서 할당한 포트를 찾는 데 유용합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.
- **port_ptr** 반환 포트 번호 대상에 대한 포인터입니다. 유효한 포트 번호는 (1-0xFFFF)입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓 바인딩에 성공했습니다.
- **NX_NOT_BOUND**(0x24) 이 소켓은 포트에 바인딩되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터 또는 포트 반환 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable, nx_udp_socket_create
- nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_receive, nx_udp_socket_receive_notify
- nx_udp_socket_send, nx_udp_socket_interface_send
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

UDP 소켓에서 데이터그램을 수신합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 소켓에서 UDP 데이터그램을 수신합니다. 지정된 소켓에 큐에 대기된 데이터그램이 없는 경우 제공된 대기 옵션에 따라 호출자가 일시 중단됩니다.

*NX_SUCCESS* 가 반환되는 경우 애플리케이션은 수신된 패킷이 더 이상 필요하지 않으면 해당 패킷을 해제해야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.
- **packet_ptr** UDP 데이터그램 패킷 포인터에 대한 포인터입니다.
- **wait_option** 현재 이 소켓에 큐에 대기된 데이터그램이 없는 경우 서비스가 작동하는 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
- NX_NO_WAIT(0x00000000)
- NX_WAIT_FOREVER(0xFFFFFFFF)
- 틱 단위의 시간 제한 값(0x00000001-0xFFFFFFFE)

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable, nx_udp_socket_create
- nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive_notify
- nx_udp_socket_send, nx_udp_socket_interface_send
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

수신된 각 패킷에 대해 애플리케이션에 알립니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a>Description

이 서비스는 애플리케이션에서 지정한 콜백 함수를 가리키는 수신 알림 함수 포인터를 설정합니다. 그러면 소켓에 패킷이 수신될 때마다 이 콜백 함수가 호출됩니다. NX_NULL 포인터를 제공하면 수신 알림 함수를 사용하지 않도록 설정합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** UDP 소켓에 대한 포인터입니다.
- **udp_receive_notify** 소켓에 패킷이 수신되면 호출되는 애플리케이션 콜백 함수 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable, nx_udp_socket_create
- nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send
- nx_udp_socket_interface_send, nx_udp_socket_unbind
- nx_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send

UDP 데이터그램을 송신합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a>Description

이 서비스는 이전에 만들고 바인딩한 UDP 소켓을 통해 UDP 데이터그램을 송신합니다. NetX는 대상 IP 주소를 기반으로 하여 원본 주소로 적합한 로컬 IP 주소를 찾습니다. 특정 인터페이스와 원본 IP 주소를 지정하려면 애플리케이션에서 **nx_udp_socket_interface_send** 서비스를 사용해야 합니다.

이 서비스는 UDP 데이터그램이 성공적으로 송신되었는지 여부에 관계없이 즉시 반환됩니다.

소켓은 로컬 포트에 바인딩되어 있어야 합니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.
- **packet_ptr** UDP 데이터그램 패킷 포인터입니다.
- **ip_address** 대상 IP 주소입니다.
- **port** 호스트 바이트 순서대로 표시된 1에서 0xFFFF 사이의 유효한 대상 포트 번호입니다.

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

```C
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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable, nx_udp_socket_create
- nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive
- nx_udp_socket_receive_notify, nx_udp_socket_interface_send
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_interface_send"></a>nx_udp_socket_interface_send

UDP 소켓을 통해 데이터그램을 송신합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a>Description

이 서비스는 지정된 IP 주소를 원본 주소로 사용하여 네트워크 인터페이스에서 이전에 만들고 바인딩한 UDP 소켓을 통해 UDP 데이터그램을 송신합니다. 이 서비스는 UDP 데이터그램이 성공적으로 송신되었는지 여부에 관계없이 즉시 반환됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 패킷을 전송할 소켓입니다.
- **packet_ptr** 전송할 패킷에 대한 포인터입니다.
- **ip_address** 패킷을 송신할 대상 IP 주소입니다.
- **port** 대상 포트입니다.
- **address_index** 패킷을 송신할 인터페이스와 연결된 주소 인덱스입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 패킷이 성공적으로 송신되었습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 포트에 바인딩되지 않았습니다.
- **NX_IP_ADDRESS_ERROR**(0x21) 잘못된 IP 주소입니다.
- **NX_NOT_ENABLED**(0x14) UDP 처리가 사용하도록 설정되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 포인터입니다.
- **NX_OVERFLOW**(0x03) 잘못된 패킷 뒤에 추가 포인터입니다.
- **NX_UNDERFLOW**(0x02) 잘못된 패킷 앞에 추가 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_INVALID_INTERFACE**(0x4C) 잘못된 주소 인덱스입니다.
- **NX_INVALID_PORT**(0x46) 포트 번호가 최대 포트 번호를 초과합니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable, nx_udp_socket_create
- nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive
- nx_udp_socket_receive_notify, nx_udp_socket_send
- nx_udp_socket_unbind

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

UDP 포트에서 UDP 소켓 바인딩을 해제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Description

이 서비스는 UDP 소켓 및 UDP 포트 간 바인딩을 해제합니다. 수신 큐에 저장된 모든 수신된 패킷은 바인딩 해제 작업의 일부로 해제됩니다.

다른 소켓을 바인딩 해제된 포트에 바인딩하려고 대기 중인 다른 스레드가 있는 경우 첫 번째 일시 중단된 스레드가 새로 바인딩 해제된 포트에 바인딩됩니다.

### <a name="parameters"></a>매개 변수

- **socket_ptr** 이전에 만든 UDP 소켓 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**(0x00) 소켓을 바인딩 해제하는 데 성공했습니다.
- **NX_NOT_BOUND**(0x24) 소켓이 어떤 포트에도 바인딩되지 않았습니다.
- **NX_PTR_ERROR**(0x07) 잘못된 소켓 포인터입니다.
- **NX_CALLER_ERROR**(0x11) 이 서비스의 잘못된 호출자입니다.
- **NX_NOT_ENABLED**(0x14) 이 구성 요소가 사용하도록 설정되지 않았습니다.

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable, nx_udp_socket_create
- nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive
- nx_udp_socket_receive_notify, nx_udp_socket_send
- nx_udp_socket_interface_send, nx_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract

UDP 데이터그램에서 IP 및 송신 포트를 추출합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a>Description

이 서비스는 제공된 UDP 데이터그램의 IP 및 UDP 헤더에서 송신기 IP 및 포트 번호를 추출합니다.

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

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a>참고 항목

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable, nx_udp_socket_create
- nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive
- nx_udp_socket_receive_notify, nx_udp_socket_send
- nx_udp_socket_interface_send, nx_udp_socket_unbind