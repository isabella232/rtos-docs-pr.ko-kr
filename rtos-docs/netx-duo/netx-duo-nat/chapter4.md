---
title: 4장 - NAT 서비스 설명
description: 이 장에서는 모든 NetX Duo NAT API 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dbe2cb25607162b62b048251927bdc7671c5884d2a3b45b6b24bae539e08d24a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797298"
---
# <a name="chapter-4---description-of-nat-services"></a>4장 - NAT 서비스 설명

이 장에서는 아래에 나열된 모든 NetX Duo NAT API 서비스에 대해 알파벳 순서로 설명하고 있습니다.

> [!NOTE]
> 다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

## <a name="nx_nat_create"></a>nx_nat_create

NAT 서버 만들기

### <a name="prototype"></a>프로토타입

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a>Description

이 서비스는 NAT 서버의 인스턴스를 만듭니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nat_ptr** 만들 NAT 인스턴스에 대한 포인터
- **ip_ptr** IP 인스턴스에 대한 포인터
- **global_interface_index** 글로벌 네트워크 인터페이스에 대한 인덱스
- **dynamic_cache_memory** NAT 테이블에 대한 포인터 메모리 영역
- **dynamic_cache_size** NAT 테이블에 대한 메모리 영역 크기

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) NAT 서버를 성공적으로 만듦
- NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수
- NX_NAT_PARAM_ERROR (0xD01) 잘못된 포인터가 아닌 입력
- NX_NAT_CACHE_ERROR (0xD02) 잘못된 캐시 포인터 입력

### <a name="allowed-from"></a>허용 위치

애플리케이션 코드

### <a name="example"></a>예제

```C
#define NX_NAT_ENTRY_CACHE_SIZE 20480

static UCHAR nat_cache[NX_NAT_ENTRY_CACHE_SIZE];
UINT global_interface_index = 0;

/* Create a NAT Server and cache with a global interface index. */
status = nx_nat_create(nat_ptr, ip_ptr, global_interface_index,
    nat_cache, NX_NAT_ENTRY_CACHE_SIZE);

/* If status = NX_SUCCESS, the NAT instance was successfully
    created. */
```

## <a name="nx_nat_delete"></a>nx_nat_delete

NAT 서버 삭제

### <a name="prototype"></a>프로토타입

```C
UINT nx_nat_delete(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 NAT 서버를 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nat_ptr** 삭제할 NAT 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) NAT를 성공적으로 삭제함
- NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용 위치

애플리케이션 코드

### <a name="example"></a>예제

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a>nx_nat_enable

NAT에 대한 IP 인스턴스 사용

### <a name="prototype"></a>프로토타입

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Description

이 서비스는 NAT에 대한 IP 인스턴스를 사용하도록 설정합니다(예: NAT 서버에 받은 패킷을 전달).

### <a name="input-parameters"></a>입력 매개 변수

- **nat_ptr** NAT 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) NAT를 성공적으로 사용하도록 설정함
- NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용 위치

애플리케이션 코드

### <a name="example"></a>예제

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a>nx_nat_disable

NAT에 대한 IP 인스턴스 사용 안 함

### <a name="prototype"></a>프로토타입

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Description

이 서비스는 IP 인스턴스에서 NAT를 사용하지 않도록 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nat_ptr** NAT 인스턴스에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) NAT를 성공적으로 사용하지 않도록 설정함
- NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수

### <a name="allowed-from"></a>허용 위치

애플리케이션 코드

### <a name="example"></a>예제

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a>nx_nat_cache_notify_set

캐시 전체 알림 콜백 함수 설정

### <a name="prototype"></a>프로토타입

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a>Description

이 서비스는 사용자 정의 캐시 전체 알림 함수를 가리키는 cache_full_notify_cb 입력 함수 포인터를 사용하여 캐시 전체 콜백을 등록합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nat_ptr** NAT 인스턴스에 대한 포인터
- **cache_full_notify_cb** 캐시 전체 알림 함수에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 캐시 전체 알림 함수가 성공적으로 설정됨
- NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수
- NX_NAT_PARAM_ERROR (0xD01) 잘못된 포인터가 아닌 입력

### <a name="allowed-from"></a>허용 위치

애플리케이션 코드

### <a name="example"></a>예제

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a>nx_nat_inbound_entry_create

NAT 변환 테이블에서 인바운드 항목 만들기

### <a name="prototype"></a>프로토타입

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a>Description

이 서비스는 인바운드 항목을 정적(영구 입력, 만료되지 않음)으로 만들고 NAT 변환 테이블에 추가합니다. 이러한 항목은 일반적으로 외부 네트워크의 호스트에서 연결이 시작되는 로컬 호스트 서버에 대해 만들어집니다. NAT 서버는 외부 포트가 이미 변환 테이블에 사용되고 있지 않거나 동일한 프로토콜의 이전의 기존 NetX Duo 소켓에 의해 바인딩되어 있는지 확인합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nat_ptr** NAT 인스턴스에 대한 포인터
- **entry_ptr** 번역 항목에 대한 포인터
- **local_ip_address** 로컬 호스트 IP 주소
- **external_port** 외부 네트워크의 대상 포트
- **local_port** 원본 (로컬 호스트) 포트
- **protocol** 패킷 프로토콜(예: TCP)

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 항목을 성공적으로 만듦
- **NX_NAT_PORT_UNAVAILABLE** (0xD0D) 잘못된 외부 포트
- NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수
- NX_NAT_PARAM_ERROR (0xD01) 잘못된 포인터가 아닌 입력

### <a name="allowed-from"></a>허용 위치

애플리케이션 코드

### <a name="example"></a>예제

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a>nx_nat_inbound_entry_delete

NAT 변환 테이블에서 인바운드 항목 삭제

### <a name="prototype"></a>프로토타입

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a>Description

이 서비스는 번역 테이블에서 지정된 인바운드 항목을 삭제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **nat_ptr** NAT 인스턴스에 대한 포인터
- **delete_entry_ptr** NAT 변환 항목에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** (0x00) 항목을 성공적으로 삭제함
- **NX_NAT_ENTRY_NOT_FOUND** (0xD04) 항목을 찾을 수 없음
- NX_PTR_ERROR (0x07) 잘못된 입력 포인터 매개 변수
- NX_NAT_ENTRY_TYPE_ERROR (0xD0C) 잘못된 변환 형식

### <a name="allowed-from"></a>허용 위치

애플리케이션 코드

### <a name="example"></a>예제

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
