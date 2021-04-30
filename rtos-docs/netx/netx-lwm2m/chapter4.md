---
title: 챕터 4 - Azure RTOS NetX LWM2M 서비스 설명
description: 이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX LWM2M 서비스에 대해 알파벳 순서로 설명하고 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811490"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a>챕터 4 - Azure RTOS NetX LWM2M 서비스 설명

이 챕터에서는 아래에 나열된 모든 Azure RTOS NetX LWM2M 서비스에 대해 알파벳 순서로 설명하고 있습니다.

다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.

### <a name="lwm2m-client-management"></a>LWM2M 클라이언트 관리

- **nx_lwm2m_client_create**: *LWM2M 클라이언트 만들기*
- **nx_lwm2m_client_delete**: *LWM2M 클라이언트 삭제*
- **nx_lwm2m_client_lock**: *LWM2M 클라이언트 잠금*
- **nx_lwm2m_client_object_add**: *LWM2M 클라이언트에 개체 구현 추가*
- **nx_lwm2m_client_unlock**: *LWM2M 클라이언트 잠금 해제*

### <a name="lwm2m-client-session-management"></a>LWM2M 클라이언트 세션 관리

- **nx_lwm2m_client_session_bootstrap**: *부트스트랩 서버를 사용하여 세션 시작*
- **nx_lwm2m_client_session_bootstrap_dtls**: *부트스트랩 서버를 사용하여 보안 세션 시작*
- **nx_lwm2m_client_session_create**: *LWM2M 클라이언트 세션 만들기*
- **nx_lwm2m_client_session_delete**: *LWM2M 클라이언트 세션 삭제*
- **nx_lwm2m_client_session_deregister**: *LWM2M 서버를 사용하여 세션 종료*
- **nx_lwm2m_client_session_error_get**: *세션의 마지막 오류 가져오기*
- **nx_lwm2m_client_session_register**: *LWM2M 서버를 사용하여 세션 시작*
- **nx_lwm2m_client_session_register_dtls**: *LWM2M 서버를 사용하여 보안 세션 시작*
- **nx_lwm2m_client_session_update**: *LWM2M 서버를 사용하여 세션 업데이트*

### <a name="security-object-implementation"></a>보안 개체 구현

- **nx_lwm2m_client_security_key_callbacks_set**: *보안 키 관리 콜백 설정*

### <a name="device-object-implementation"></a>디바이스 개체 구현

- **nx_lwm2m_client_device_callbacks_set**: *디바이스 개체 애플리케이션 호출 설정*
- **nx_lwm2m_client_device_error_push**: *디바이스 개체에 오류 코드 추가*
- **nx_lwm2m_client_device_error_reset**: *디바이스 개체의 오류 코드 다시 설정*
- **nx_lwm2m_client_device_resource_changed**: *디바이스 개체 리소스에 대한 변경 신호 보내기*

### <a name="custom-objects-implementation"></a>사용자 지정 개체 구현

- **nx_lwm2m_object_resource_changed**: *개체 인스턴스의 리소스 값에 대한 변경 신호 보내기*

### <a name="local-device-management"></a>로컬 디바이스 관리

- **nx_lwm2m_client_object_create**: *새 개체 인스턴스 만들기*
- **nx_lwm2m_client_object_delete**: *개체 인스턴스 삭제*
- **nx_lwm2m_client_object_discover**: *개체 인스턴스의 리소스 검색*
- **nx_lwm2m_client_object_execute**: *개체 인스턴스의 리소스 실행*
- **nx_lwm2m_client_object_get_next**: *LWM2M 클라이언트에서 구현하는 개체의 목록 가져오기*
- **nx_lwm2m_client_object_instance_get_next**: *개체의 인스턴스 목록 가져오기*
- **nx_lwm2m_client_object_read**: *개체 인스턴스의 리소스 값 읽기*
- **nx_lwm2m_client_object_write**: *개체 인스턴스의 리소스 값 변경*

### <a name="resources-values-decoding"></a>리소스 값 디코딩

- **nx_lwm2m_resource_get_boolean**: *부울 리소스의 값 가져오기*
- **nx_lwm2m_resource_get_float32**: *32비트 부동 소수점 리소스의 값 가져오기*
- **nx_lwm2m_resource_get_float64**: *64비트 부동 소수점 리소스의 값 가져오기*
- **nx_lwm2m_resource_get_integer32**: *32비트 정수 리소스의 값 가져오기*
- **nx_lwm2m_resource_get_integer64**: *64비트 정수 리소스의 값 가져오기*
- **nx_lwm2m_resource_get_objlnk**: *개체 링크 리소스의 값 가져오기*
- **nx_lwm2m_resource_get_opaque**: *불투명 리소스의 값 가져오기*
- **nx_lwm2m_resource_get_string**: *문자열 리소스의 값 가져오기*
- **nx_lwm2m_resource_multiple_get_boolean**: *부울 리소스 다중 리소스 인스턴스의 값 가져오기*
- **nx_lwm2m_resource_multiple_get_float32**: *32비트 부동 소수점 다중 리소스 인스턴스의 값 가져오기*
- **nx_lwm2m_resource_multiple_get_float64**: *64비트 부동 소수점 다중 리소스 인스턴스의 값 가져오기*
- **nx_lwm2m_resource_multiple_get_integer32**: *32비트 정수 다중 리소스 인스턴스의 값 가져오기*
- **nx_lwm2m_resource_multiple_get_integer64**: *64비트 정수 다중 리소스 인스턴스의 값 가져오기*
- **nx_lwm2m_resource_multiple_get_objlnk**: *개체 링크 다중 리소스 인스턴스의 값 가져오기*
- **nx_lwm2m_resource_multiple_get_opaque**: *불투명 다중 리소스 인스턴스의 값 가져오기*
- **nx_lwm2m_resource_multiple_get_string**: *문자열 다중 리소스 인스턴스의 값 가져오기*

### <a name="firmware-update-object"></a>펌웨어 업데이트 개체

- **nx_lwm2m_firmware_create**: *펌웨어 업데이트 개체 만들기*
- **nx_lwm2m_firmware_package_info_set**: *펌웨어 업데이트 패키지 정보 설정*
- **nx_lwm2m_firmware_result_set**: *펌웨어 업데이트 결과 설정*
- **nx_lwm2m_firmware_state_set**: *펌웨어 업데이트 상태 설정*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

LWM2M 클라이언트를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a>Description

이 서비스는 자체 ThreadX 스레드의 컨텍스트에서 실행되는 LWM2M 클라이언트 인스턴스를 만듭니다.

LWM2M 클라이언트는 보안(0), 서버(1), 액세스 제어(2) 및 디바이스(3)와 같은 OMA LWM2M 개체를 구현합니다. 다른 개체 구현은 애플리케이션에서 추가해야 합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **ip_ptr**: 이전에 만든 IP 인스턴스에 대한 포인터
- **packet_pool_ptr**: 이 LWM2M 클라이언트의 기본 패킷 풀에 대한 포인터
- **local_port**: 비보안 통신에 사용되는 로컬 UDP 포트
- **name_ptr**: LWM2M 클라이언트 엔드포인트 이름에 대한 포인터
- **msisdn_ptr**: SMS 바인딩에서 사용하기 위해 LWM2M 클라이언트에 연결할 수 있는 MSISDN에 대한 포인터이며, SMS 바인딩이 지원되지 않는 경우 NULL일 수 있습니다.
- **binding_modes**: LWM2M 클라이언트에서 지원하는 바인딩 및 모드이며, NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S 및 NX_LWM2M_BINDING_SQ 플래그의 조합이어야 합니다.
- **stack_ptr**: LWM2M 클라이언트 스레드 스택 영역에 대한 포인터
- **stack_size**: LWM2M 클라이언트 스레드 스택 크기

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: LWM2M 클라이언트를 성공적으로 만듦
- **NX_LWM2M_ERROR**: LWM2M 클라이언트 만들기 오류
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

LWM2M 클라이언트를 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 LWM2M 클라이언트 인스턴스를 삭제합니다.

현재 클라이언트에 연결된 모든 세션도 이 호출을 통해 삭제됩니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: LWM2M 클라이언트를 성공적으로 삭제함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_device_callbacks_set"></a>nx_lwm2m_client_device_callbacks_set

디바이스 개체 애플리케이션 콜백을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트에서 처리하지 않는 LWM2M 디바이스 개체 리소스에 대한 작업을 구현하는 애플리케이션 콜백을 설치합니다.

LWM2M 클라이언트는 오류 코드(11), 다시 설정 오류 코드(12) 및 지원되는 바인딩 및 모드(16)와 같은 리소스를 구현합니다. 다른 리소스에 대한 작업은 애플리케이션으로 리디렉션됩니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **read_callback**: 'Read' 메서드 콜백
- **discover_callback**: 'Discover' 메서드 콜백
- **write_callback**: 'Write' 메서드 콜백
- **execute_callback**: 'Execute' 메서드 콜백

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push

오류 코드를 디바이스 개체에 추가합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a>Description

이 서비스는 새 인스턴스를 개체 디바이스의 오류 코드(11) 리소스에 추가합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **code**: 새 오류 코드

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BUFFER_TOO_SMALL**: 저장된 최대 오류 코드 수에 도달함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

디바이스 개체의 오류 코드를 다시 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 디바이스 개체에서 모든 오류 코드 리소스 인스턴스를 삭제합니다. 이는 리소스 다시 설정 오류 코드(12)를 실행하는 것과 같습니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

디바이스 개체 리소스에 대한 변경 신호를 보냅니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션에서 개체 디바이스의 리소스가 변경되었다는 신호를 LWM2M 클라이언트에 보내는 데 사용됩니다. LWM2M 서버에서 리소스를 관찰하는 경우 LWM2M 클라이언트에서 알림을 보냅니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **resource**: 변경된 리소스를 설명하는 구조체에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

LWM2M 클라이언트를 잠급니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 서버 또는 다른 애플리케이션 스레드에서 LWM2M 개체에 대한 동시 액세스를 방지하기 위해 LWM2M 클라이언트를 잠급니다.

LWM2M 클라이언트가 현재 다른 스레드에서 잠겨 있는 경우 LWM2M 클라이언트의 잠금이 해제될 때까지 이 함수가 차단됩니다.

nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() 쌍에 대한 호출은 중첩할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

개체 구현을 LWM2M 클라이언트에 추가합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a>Description

이 서비스는 새 개체 구현을 LWM2M 클라이언트에 추가합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **object_ptr**: 개체 구현을 정의하는 구조체에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_ALREADY_EXIST**: 개체 ID가 이미 있음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

새 개체 인스턴스를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트의 개체에 대한 'Create' 작업을 수행하여 새 개체 인스턴스를 만듭니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **object_id**: 개체 ID
- **instance_id_ptr**: 새 인스턴스의 ID에 대한 포인터이며 LWM2M 클라이언트에서 인스턴스 ID를 할당해야 하는 경우 NULL일 수 있습니다. ID가 예약된 65535 값인 경우 LWM2M 클라이언트에서 인스턴스 ID를 할당합니다. NULL이 아닌 경우 할당된 ID가 호출 후에 반환됩니다.
- **num_values**: 설정하는 값의 수
- **values_ptr**: 새 개체 인스턴스를 초기화하는 리소스 값의 배열에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_ALREADY_EXIST**: 개체 인스턴스 ID가 이미 있음
- **NX_LWM2M_METHOD_NOT_ALLOWED**: 개체에서 인스턴스 만들기를 지원하지 않음
- **NX_LWM2M_NO_MEMORY**: 새 인스턴스를 저장하는 메모리를 할당할 수 없음
- **NX_LWM2M_NOT_FOUND**: 개체 ID가 없음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

개체 인스턴스를 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Delete' 작업을 수행합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **object_id**: 개체 ID
- **instance_id**: 개체 인스턴스 ID

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_METHOD_NOT_ALLOWED**: 개체에서 인스턴스 삭제를 지원하지 않음
- **NX_LWM2M_NOT_FOUND**: 개체 ID 또는 개체 인스턴스 ID가 없음
- NX_PTR_ERROR 잘못된 포인터

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

개체 인스턴스의 리소스를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Discover' 작업을 수행하여 개체에서 구현한 리소스 목록을 반환합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **object_id**: 개체 ID
- **instance_id**: 개체 인스턴스 ID
- **num_resources_ptr**: 입력 시 대상 버퍼의 크기 및 출력 시 버퍼에 쓰인 요소의 수
- **resources_ptr**: 대상 버퍼에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BUFFER_TOO_SMALL**: 리소스 버퍼가 너무 작아 리소스 목록을 저장할 수 없음
- **NX_LWM2M_NOT_FOUND**: 개체 ID 또는 개체 인스턴스 ID가 없음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

개체 인스턴스의 리소스를 실행합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트의 개체 인스턴스 리소스에 대한 'Execute' 작업을 수행합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **object_id**: 개체 ID
- **instance_id**: 개체 인스턴스 ID
- **resource_id**: 리소스 ID
- **arguments_ptr**: 실행 작업의 인수에 대한 포인터이며, arguments_length가 0인 경우 NULL일 수 있습니다.
- **arguments_length**: 인수의 길이

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_METHOD_NOT_ALLOWED**: 리소스에서 실행 작업을 지원하지 않음
- **NX_LWM2M_NOT_FOUND**: 개체 ID, 개체 인스턴스 ID 또는 리소스 ID가 없음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_object_get_next"></a>nx_lwm2m_client_object_get_next

LWM2M Client에서 구현하는 개체의 목록을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트에서 구현하는 다음 개체의 ID를 반환합니다. 현재 개체 ID가 NX_LWM2M_RESERVED_ID (65535)로 설정된 경우 첫 번째 개체 ID가 반환됩니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **object_id_ptr**: 현재 개체 ID에 대한 포인터이며, 반환 시 LWM2M 클라이언트에서 구현하는 다음 개체 ID가 포함됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_NOT_FOUND**: 지정된 개체 ID가 데이터베이스의 마지막 ID임
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_object_instance_get_next"></a>nx_lwm2m_client_object_instance_get_next

개체의 인스턴스 목록을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 개체의 다음 개체 인스턴스에 대한 ID를 반환합니다. 현재 인스턴스 ID가 NX_LWM2M_RESERVED_ID (65535)로 설정된 경우 첫 번째 인스턴스의 ID가 반환됩니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **object_id**: 개체 ID
- **instance_id_ptr**: 현재 개체 인스턴스 ID에 대한 포인터이며, 반환 시 개체의 다음 인스턴스 ID가 포함됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_NOT_FOUND**: 지정된 인스턴스 ID가 개체의 마지막 ID이거나 개체 ID가 구현되지 않음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

개체 인스턴스의 리소스 값을 읽습니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Read' 작업을 수행합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **object_id**: 개체 ID
- **instance_id**: 개체 인스턴스 ID
- **num_values**: 읽는 리소스의 수
- **values_ptr**: 읽는 리소스의 ID가 포함되는 NX_LWM2M_RESOURCE 배열에 대한 포인터이며, 반환 시 배열이 해당 형식 및 값으로 채워집니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_METHOD_NOT_ALLOWED**: 리소스에서 읽기 작업을 지원하지 않음
- **NX_LWM2M_NOT_FOUND**: 개체 ID, 개체 인스턴스 ID 또는 리소스 ID가 없음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

개체 인스턴스의 리소스 값을 변경합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Write' 작업을 수행합니다.

*write_op* 매개 변수에 지정할 수 있는 쓰기 작업은 다음과 같습니다.

- **0** &mdash; 부분 업데이트: 새 값으로 제공되는 리소스를 추가하거나 업데이트하고, 다른 기존 리소스는 변경하지 않은 상태로 유지합니다.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; 인스턴스 바꾸기: 개체 인스턴스를 제공된 새 리소스 값으로 바꿉니다.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; 리소스 바꾸기: 리소스를 제공 된 새 리소스 값으로 바꿉니다(여러 리소스를 바꾸는 데 사용됨).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; 부트스트랩 쓰기: 부트스트랩 시퀀스의 호출을 나타냅니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **object_id**: 개체 ID
- **instance_id**: 개체 인스턴스 ID
- **num_values**: 쓰는 리소스의 수
- **values_ptr**: 리소스 ID, 형식 및 쓰는 값이 포함되는 NX_LWM2M_RESOURCE 배열에 대한 포인터
- **write_op**: 쓰기 작업의 형식

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_ENCODING**: 리소스 종류가 잘못됨
- **NX_LWM2M_BUFFER_TOO_SMALL**: 값의 길이가 너무 커서 인스턴스에 저장할 수 없음
- **NX_LWM2M_METHOD_NOT_ALLOWED**: 리소스에서 쓰기 작업을 지원하지 않음
- **NX_LWM2M_NO_MEMORY**: 리소스 값을 저장하는 메모리를 할당할 수 없음
- **NX_LWM2M_NOT_ACCEPTABLE**: 리소스의 값이 잘못됨
- **NX_LWM2M_NOT_FOUND**: 개체 ID, 개체 인스턴스 ID 또는 리소스 ID가 없음
- NX_OPTION_ERROR: 잘못된 쓰기 작업의 형식
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a>nx_lwm2m_client_security_key_callbacks_set

보안 개체 키 관리 콜백을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a>Description

이 서비스는 보안 키와 관련된 LWM2M 보안 개체 리소스에 대한 작업을 구현하는 애플리케이션 콜백을 설치합니다.

LWM2M 클라이언트는 부트스트랩 세션 중에 보안 키 관리를 애플리케이션에 위임하고, 부트스트랩 서버에서 보안 개체 인스턴스에서 공개 키 또는 ID(3), 서버 공개 키(4), 비밀 키(5) 리소스를 쓰거나 삭제할 때 콜백이 호출됩니다.

애플리케이션에서 키 데이터를 저장하고 LWM2M 클라이언트에서 사용하는 DTLS 세션을 구성해야 합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터
- **write_callback**: 'Write' 키 메서드 콜백
- **delete_callback**: 'Delete' 키 메서드 콜백

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

부트스트랩 서버를 사용하여 세션을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Description

이 서비스는 부트스트랩 서버를 사용하여 세션을 시작합니다. 서버의 보안 개체에는 해당 보안 인스턴스가 있어야 합니다.

이 서버와 연결된 보안 인스턴스에서 'Hold Off'(지연) 리소스가 0과 다른 경우 세션에서 서버 시작 부트스트랩을 기다리며, 이 기간 이후에 서버에서 부트스트랩을 시작하지 않으면 클라이언트 시작 부트스트랩이 수행됩니다.

현재 활성 세션은 이 호출에서 중단되고 새 부트스트랩 서버 세션으로 대체됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터
- **security_id**: 부트 스트랩 서버의 보안 인스턴스 ID이며, 부트 스트랩 서버에 정의된 보안 인스턴스가 없는 경우 NX_LWM2M_RESERVED_ID (65535)로 설정해야 합니다.
- **ip_address** 서버의 IP 주소
- **port**: 서버의 UDP 포트

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_NOT_FOUND**: 보안 인스턴스 ID에 해당하는 보안 개체 인스턴스가 없음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

부트스트랩 서버를 사용하여 보안 세션을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Description

이 서비스는 보안 DTLS 연결을 사용하여 부트스트랩 서버에서 세션을 시작합니다. 서버의 보안 개체에는 해당 보안 인스턴스가 있어야 합니다.

이 함수를 호출하기 전에 DTLS 세션을 적절한 암호 그룹 및 키 자료를 사용하여 구성해야 합니다. NX_SECURE_ENABLE_DTLS를 정의해야 합니다.

이 서버와 연결된 보안 인스턴스에서 'Hold Off'(지연) 리소스가 0과 다른 경우 세션에서 서버 시작 부트스트랩을 기다리며, 이 기간 이후에 서버에서 부트스트랩을 시작하지 않으면 클라이언트 시작 부트스트랩이 수행됩니다.

현재 활성 세션은 이 호출에서 중단되고 새 부트스트랩 서버 세션으로 대체됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터
- **security_id**: 부트 스트랩 서버의 보안 인스턴스 ID이며, 부트 스트랩 서버에 정의된 보안 인스턴스가 없는 경우 NX_LWM2M_RESERVED_ID (65535)로 설정해야 합니다.
- **ip_address** 서버의 IP 주소
- **port**: 서버의 UDP 포트
- **dtls_session_ptr**: 부트스트랩 세션에 사용하는 DTLS 세션
- **dtls_local_port**: DTLS 세션에 사용되는 로컬 UDP 포트

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_NOT_FOUND**: 보안 인스턴스 ID에 해당하는 보안 개체 인스턴스가 없음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

LWM2M 클라이언트 세션을 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Description

이 서비스는 기존 LWM2M 클라이언트에 연결된 새 LWM2M 클라이언트 세션을 만듭니다. 이 세션은 LWM2M 클라이언트에서 부트스트랩 서버 또는 LWM2M 서버와 통신하는 데 사용됩니다.

애플리케이션에서 세션 상태가 업데이트될 때 호출되는 콜백 함수를 제공해야 합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터
- **client_ptr**: 이전에 만든 LWM2M 클라이언트에 대한 포인터
- **state_callback**: 세션의 상태가 변경되었을 때 호출되는 애플리케이션 콜백

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

LWM2M Client 세션을 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

이 서비스는 LWM2M Client 세션을 삭제합니다.

nx_lwm2m_client_delete를 호출하여 LWM2M 클라이언트를 삭제하면 클라이언트에 연결된 모든 세션도 삭제됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

LWM2M 서버를 사용하여 세션을 종료합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 서버에 대한 'De-Register' 작업을 수행 합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_NOT_REGISTERED**: 클라이언트가 서버에 등록되어 있지 않음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

세션의 마지막 오류를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

세션이 오류 상태인 경우 이 서비스에서 세션의 오류 코드를 반환합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 세션이 오류 상태가 아님
- **NX_LWM2M_ADDRESS_ERROR**: 잘못된 서버 주소
- **NX_LWM2M_BUFFER_TOO_SMALL**: 요청의 페이로드가 네트워크 버퍼에 맞지 않음
- **NX_LWM2M_DTLS_ERROR**: 서버와의 보안 연결을 설정 하지 못함
- **NX_LWM2M_ERROR**: 알 수 없는 오류
- **NX_LWM2M_FORBIDDEN**: 서버에서 등록을 거부함
- **NX_LWM2M_NOT_FOUND**: 업데이트/등록 취소 시 서버에서 클라이언트를 찾을 수 없음
- **NX_LWM2M_SERVER_INSTANCE_DELETED**: 세션에 해당 하는 서버 개체 인스턴스가 삭제됨
- **NX_LWM2M_TIMED_OUT**: 서버에서 응답하지 않음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

LWM2M 서버를 사용하여 세션을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 서버에 대한 'Register' 작업을 수행합니다. 서버의 서버 개체에는 해당 서버 인스턴스가 있어야 합니다.

등록이 성공하면 LWM2M 클라이언트는 서버에서 추가 작업을 처리하고, 클라이언트가 등록 취소될 때까지 '업데이트' 메시지를 정기적으로 보냅니다.

현재 활성 세션은 이 호출에서 중단되고 새 LWM2M 서버 세션으로 대체됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터
- **server_id**: LWM2M 서버의 약식 서버 ID
- **ip_address** 서버의 IP 주소
- **port**: 서버의 UDP 포트

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_NOT_FOUND**: 약식 서버 ID에 해당하는 서버 개체 인스턴스가 없음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

LWM2M 서버를 사용하여 보안 세션을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Description

이 서비스는 보안 DTLS 연결을 사용하여 LWM2M 서버에 대한 'Register' 작업을 수행합니다. 서버의 서버 개체에는 해당 서버 인스턴스가 있어야 합니다.

이 함수를 호출하기 전에 DTLS 세션을 적절한 암호 그룹 및 키 자료를 사용하여 구성해야 합니다. NX_SECURE_ENABLE_DTLS를 정의해야 합니다.

각 DTLS 세션에서 통신을 위해 자체 UDP 소켓을 사용하므로 애플리케이션에서 여러 개의 보안 세션을 만드는 경우 각 세션에 대한 dtls_local_port 로컬 포트가 달라야 합니다.

등록이 성공하면 LWM2M 클라이언트는 서버에서 추가 작업을 처리하고, 클라이언트가 등록 취소될 때까지 '업데이트' 메시지를 정기적으로 보냅니다.

현재 활성 세션은 이 호출에서 중단되고 새 LWM2M 서버 세션으로 대체됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터
- **server_id**: LWM2M 서버의 약식 서버 ID
- **ip_address** 서버의 IP 주소
- **port**: 서버의 UDP 포트
- **dtls_session_ptr**: LWM2M 세션에 사용하는 DTLS 세션
- **dtls_local_port**: DTLS 세션에 사용되는 로컬 UDP 포트

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_NOT_FOUND**: 약식 서버 ID에 해당하는 서버 개체 인스턴스가 없음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

LWM2M 서버를 사용하여 세션을 업데이트합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 서버에 대한 'Update' 작업을 수행합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr**: LWM2M 클라이언트 세션 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_NOT_REGISTERED**: 클라이언트가 서버에 등록되어 있지 않음
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

LWM2M 클라이언트의 잠금을 해제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이전에 nx_lwm2m_client_unlock()을 호출하여 잠긴 LWM2M 클라이언트의 잠금을 해제합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr**: LWM2M 클라이언트 제어 블록에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_firmware_create"></a>nx_lwm2m_firmware_create

펌웨어 업데이트 개체를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a>Description

이 서비스는 펌웨어 업데이트 개체를 초기화하고, 이 개체를 이전에 만든 LWM2M 클라이언트에 추가합니다. 펌웨어 업데이트 개체는 LWM2M 서버와 통신하기 위한 리소스를 구현하지만, 애플리케이션에서 펌웨어에 대한 실제 작업(펌웨어 다운로드, 저장 및 업데이트)을 구현하는 콜백을 제공해야 합니다.

protocols 매개 변수는 '패키지 URI' 리소스를 사용하여 펌웨어를 검색하기 위해 애플리케이션에서 지원하는 프로토콜을 나타내며, 다음과 같은 플래그가 정의됩니다.

NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS

### <a name="parameters"></a>매개 변수

- **firmware_ptr**: 펌웨어 개체 제어 블록에 대한 포인터
- **client_ptr**: 이전에 만든 LWM2M 클라이언트에 대한 포인터
- **protocols**: 패키지 URI 리소스에서 지원하는 프로토콜을 나타내는 플래그
- **package_callback**: NULL이어야 함[미정].
- **package_uri_callback**: 패키지 URI 리소스를 구현하는 데 사용되는 콜백
- **update_callback**: 업데이트 리소스를 구현하는 데 사용되는 콜백

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_firmware_package_info_set"></a>nx_lwm2m_firmware_package_info_set

펌웨어 업데이트 패키지 정보를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a>Description

이 서비스는 펌웨어 업데이트 개체의 'PkgName' (6) 및 'PkgVersion' (7) 리소스에 대한 값을 변경합니다.

### <a name="parameters"></a>매개 변수

- **firmware_ptr**: 펌웨어 업데이트 개체에 대한 포인터
- **name**: 패키지 이름의 새 값
- **version**: 패키지 버전의 새 값

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_firmware_result_set"></a>nx_lwm2m_firmware_result_set

펌웨어 업데이트 결과를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a>Description

이 서비스는 펌웨어 업데이트 개체의 'Update Result' (5) 리소스에 대한 값을 변경합니다.

### <a name="parameters"></a>매개 변수

- **firmware_ptr**: 펌웨어 업데이트 개체에 대한 포인터
- **result**: 업데이트 결과 리소스의 새 값

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_firmware_state_set"></a>nx_lwm2m_firmware_state_set

펌웨어 업데이트 업데이트를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a>Description

이 서비스는 펌웨어 업데이트 개체의 'State' (3) 리소스에 대한 값을 변경합니다.

### <a name="parameters"></a>매개 변수

- **firmware_ptr**: 펌웨어 업데이트 개체에 대한 포인터
- **state**: 상태 리소스의 새 값

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_object_resource_changed"></a>nx_lwm2m_object_resource_changed

개체 인스턴스의 리소스 값에 대한 변경 신호를 보냅니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Description

이 서비스는 개체 구현에서 해당 리소스 값 중 하나가 변경되었다는 신호를 LWM2M 클라이언트에 보내는 데 사용됩니다. LWM2M 서버에서 리소스를 관찰하는 경우 LWM2M 클라이언트에서 알림을 보냅니다.

### <a name="parameters"></a>매개 변수

- **object_ptr**: 개체 구현에 대한 포인터
- **instance_ptr**: 개체 인스턴스에 대한 포인터
- **resource**: 변경된 리소스를 설명하는 구조체에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- NX_PTR_ERROR: 잘못된 포인터

## <a name="nx_lwm2m_resource_get_boolean"></a>nx_lwm2m_resource_get_boolean

부울 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Description

이 서비스는 부울 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 리소스 값 설명에 대한 포인터
- **bool_ptr**: 대상 부울 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_ENCODING**: 리소스 값이 부울 값이 아님

## <a name="nx_lwm2m_resource_get_float32"></a>nx_lwm2m_resource_get_float32

32비트 부동 소수점 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Description

이 서비스는 32비트 부동 소수점 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 리소스 값 설명에 대한 포인터
- **float32_ptr**: 대상 32비트 부동 소수점 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_ENCODING**: 리소스 값이 부동 소수점 값이 아님

## <a name="nx_lwm2m_resource_get_float64"></a>nx_lwm2m_resource_get_float64

64비트 부동 소수점 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Description

이 서비스는 64비트 부동 소수점 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 리소스 값 설명에 대한 포인터
- **float64_ptr**: 대상 64비트 부동 소수점 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_ENCODING**: 리소스 값이 부동 소수점 값이 아님

## <a name="nx_lwm2m_resource_get_integer32"></a>nx_lwm2m_resource_get_integer32

32비트 정수 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Description

이 서비스는 32비트 정수 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 리소스 값 설명에 대한 포인터
- **int32_ptr**: 대상 32비트 정수 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_ENCODING**: 리소스 값이 정수 값이 아니거나 정수 값이 32비트 숫자에 맞지 않음

## <a name="nx_lwm2m_resource_get_integer64"></a>nx_lwm2m_resource_get_integer64

64비트 정수 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Description

이 서비스는 64비트 정수 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 리소스 값 설명에 대한 포인터
- **int64_ptr**: 대상 64비트 정수 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_ENCODING**: 리소스 값이 정수 값이 아님

## <a name="nx_lwm2m_resource_get_objlnk"></a>nx_lwm2m_resource_get_objlnk

개체 링크 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Description

이 서비스는 개체 링크 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 리소스 값 설명에 대한 포인터
- **objlnk_ptr**: 대상 개체 링크 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_ENCODING**: 리소스 값이 개체 링크 값이 아님

## <a name="nx_lwm2m_resource_get_opaque"></a>nx_lwm2m_resource_get_opaque

불투명 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a>Description

이 서비스는 불투명 리소스의 값을 검색합니다.

불투명 리소스 값은 버퍼 및 길이에 대한 포인터로 구성 됩니다.

### <a name="parameters"></a>매개 변수

- **value**: 리소스 값 설명에 대한 포인터
- **opaque_ptr_ptr**: 대상 불투명 버퍼 포인터에 대한 포인터
- **opaque_length_ptr**: 대상 불투명 버퍼 길이에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_ENCODING**: 리소스 값이 불투명 값이 아님

## <a name="nx_lwm2m_resource_get_string"></a>nx_lwm2m_resource_get_string

문자열 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a>Description

이 서비스는 문자열 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 리소스 값 설명에 대한 포인터
- **string_ptr_ptr**: 대상 문자열 포인터에 대한 포인터
- **string_length_ptr**: 대상 문자열 길이에 대한 포인터이며, 문자열이 null로 끝나는 경우 NULL일 수 있습니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_ENCODING**: 리소스 값이 문자열 값이 아님

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a>nx_lwm2m_resource_multiple_get_boolean

부울 리소스 다중 리소스 인스턴스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Description

이 서비스는 여러 리소스에서 부울 리소스 인스턴스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 다중 리소스 값 설명에 대한 포인터
- **index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스
- **instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터
- **bool_ptr**: 대상 부울 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남
- **NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 리소스 값이 부울 값이 아님

## <a name="nx_lwm2m_resource_multiple_get_float32"></a>nx_lwm2m_resource_multiple_get_float32

32비트 부동 소수점 다중 리소스 인스턴스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Description

이 서비스는 여러 리소스에서 32비트 부동 소수점 리소스 인스턴스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 다중 리소스 값 설명에 대한 포인터
- **index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스
- **instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터
- **float32_ptr**: 대상 32비트 부동 소수점 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남
- **NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 리소스 값이 부동 소수점 값이 아님

## <a name="nx_lwm2m_resource_multiple_get_float64"></a>nx_lwm2m_resource_multiple_get_float64

64비트 부동 소수점 다중 리소스 인스턴스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Description

이 서비스는 여러 리소스에서 64비트 부동 소수점 리소스 인스턴스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 다중 리소스 값 설명에 대한 포인터
- **index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스
- **instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터
- **float64_ptr**: 대상 64비트 부동 소수점 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남
- **NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 리소스 값이 부동 소수점 값이 아님

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a>nx_lwm2m_resource_multiple_get_integer32

32비트 정수 다중 리소스 인스턴스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Description

이 서비스는 여러 리소스에서 32비트 정수 리소스 인스턴스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 다중 리소스 값 설명에 대한 포인터
- **index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스
- **instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터
- **int32_ptr**: 대상 32비트 정수 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남
- **NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나, 리소스 값이 정수 값이 아니거나, 정수 값이 32비트 숫자에 맞지 않음

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a>nx_lwm2m_resource_multiple_get_integer64

64비트 정수 다중 리소스 인스턴스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Description

이 서비스는 여러 리소스에서 64비트 정수 리소스 인스턴스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 다중 리소스 값 설명에 대한 포인터
- **index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스
- **instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터
- **int64_ptr**: 대상 64비트 정수 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남
- **NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 리소스 값이 정수 값이 아님

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a>nx_lwm2m_resource_multiple_get_objlnk

개체 링크 다중 리소스 인스턴스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Description

이 서비스는 여러 리소스에서 개체 링크 리소스 인스턴스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 다중 리소스 값 설명에 대한 포인터
- **index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스
- **instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터
- **objlnk_ptr**: 대상 개체 링크 값에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남
- **NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 리소스 값이 개체 링크 값이 아님

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a>nx_lwm2m_resource_multiple_get_opaque

불투명 다중 리소스 인스턴스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a>Description

이 서비스는 여러 리소스에서 불투명 리소스 인스턴스의 값을 검색합니다.

불투명 리소스 값은 버퍼 및 길이에 대한 포인터로 구성 됩니다.

### <a name="parameters"></a>매개 변수

- **value**: 다중 리소스 값 설명에 대한 포인터
- **index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스
- **instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터
- **opaque_ptr_ptr**: 대상 불투명 버퍼 포인터에 대한 포인터
- **opaque_length_ptr**: 대상 불투명 버퍼 길이에 대한 포인터

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남
- **NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 리소스 값이 불투명 값이 아님

## <a name="nx_lwm2m_resource_multiple_get_string"></a>nx_lwm2m_resource_multiple_get_string

문자열 다중 리소스 인스턴스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a>Description

이 서비스는 여러 리소스에서 문자열 리소스 인스턴스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **value**: 다중 리소스 값 설명에 대한 포인터
- **index**: 리소스 값 배열에서 검색하는 인스턴스의 인덱스
- **instance_id_ptr**: 대상 인스턴스 ID에 대한 포인터
- **string_ptr_ptr**: 대상 문자열 포인터에 대한 포인터
- **string_length_ptr**: 대상 문자열 길이에 대한 포인터이며, 문자열이 null로 끝나는 경우 NULL일 수 있습니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS**: 작업이 성공함
- **NX_LWM2M_BAD_PARAMETER**: 인덱스가 범위를 벗어남
- **NX_LWM2M_BAD_ENCODING**: 리소스가 여러 리소스가 아니거나 인스턴스 값이 문자열 값이 아님
