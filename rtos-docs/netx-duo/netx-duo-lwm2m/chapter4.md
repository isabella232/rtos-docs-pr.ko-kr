---
title: 챕터 4 - LWM2M 클라이언트 서비스 설명
description: 이 챕터에서는 모든 LWM2M 클라이언트 서비스를 알파벳 순서로 설명합니다.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0956cb43f4fcd87d5bd4d90b2288ce6f8d5295ee0be8b8a9f4719ad842e00b2a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783444"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a>챕터 4 - LWM2M 클라이언트 서비스 설명

이 챕터에서는 아래에 나열된 모든 LWM2M 클라이언트 서비스를 알파벳 순서로 설명합니다.

다음 API 설명의 "반환 값" 섹션에서 **굵게 표시된** 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용할 수 없게 됩니다.

**LWM2M 클라이언트 관리:**

- nx_lwm2m_client_create: *LWM2M 클라이언트 만들기*

- nx_lwm2m_client_delete: *LWM2M 클라이언트 삭제하기*

- nx_lwm2m_client_lock: *LWM2M 클라이언트 잠그기*

- nx_lwm2m_client_unlock: *LWM2M 클라이언트 잠금 해제하기*

**LWM2M 클라이언트 세션 관리:**

- nx_lwm2m_client_session_create: *LWM2M 클라이언트 세션 만들기*

- nx_lwm2m_client_session_delete: *LWM2M 클라이언트 세션 삭제*

- nx_lwm2m_client_session_bootstrap: *부트스트랩 서버를 사용하여 세션 시작*

- nx_lwm2m_client_session_bootstrap_dtls: *부트스트랩 서버를 사용하여 보안 세션 시작*

- nx_lwm2m_client_session_register_info_get: *LWM2M 서버 등록 정보 가져오기*

- nx_lwm2m_client_session_register: *LWM2M 서버를 사용하여 세션 시작*

- nx_lwm2m_client_session_register_dtls: *LWM2M 서버를 사용하여 보안 세션 시작*

- nx_lwm2m_client_session_update: *LWM2M 서버를 사용하여 세션 업데이트*

- nx_lwm2m_client_session_deregister: *LWM2M 서버를 사용하여 세션 종료*

- nx_lwm2m_client_session_error_get: *세션의 마지막 오류 가져오기*

**디바이스 개체 구현:**

- nx_lwm2m_client_device_callbacks_set: *디바이스 개체 애플리케이션 호출 설정*

- nx_lwm2m_client_device_error_push: *디바이스 개체에 오류 코드 추가*

- nx_lwm2m_client_device_error_reset: *디바이스 개체의 오류 코드 초기화*

- nx_lwm2m_client_device_resource_changed: *디바이스 개체 리소스에 대한 변경 신호 보내기*

**펌웨어 업데이트 개체 구현:**

- nx_lwm2m_firmware_create: *펌웨어 업데이트 개체 만들기*

- nx_lwm2m_firmware_package_info_set: *펌웨어 업데이트 패키지 정보 설정*

- nx_lwm2m_firmware_result_set: *펌웨어 업데이트 결과 설정*

- nx_lwm2m_firmware_state_set: *펌웨어 업데이트 상태 설정*

**사용자 지정 개체 구현:**

- nx_lwm2m_client_object_add: *LWM2M 클라이언트에 개체 구현 추가*

- nx_lwm2m_client_object_remove: *LWM2M 클라이언트에서 개체 구현 제거*

- nx_lwm2m_client_object_instance_add: *LWM2M 클라이언트에 개체 인스턴스 추가*

- nx_lwm2m_client_object_instance_remove: *LWM2M 클라이언트에서 개체 인스턴스 제거*

- nx_lwm2m_object_resource_changed: *개체 인스턴스의 리소스 값에 대한 변경 신호 보내기*

**로컬 디바이스 관리**

- nx_lwm2m_client_object_create: *새 개체 인스턴스 만들기*

- nx_lwm2m_client_object_delete: *개체 인스턴스 삭제*

- nx_lwm2m_client_object_discover: *개체 인스턴스의 리소스 검색*

- nx_lwm2m_client_object_execute: *개체 인스턴스의 리소스 실행*

- nx_lwm2m_client_object_next_get: *LWM2M 클라이언트에서 구현하는 개체의 목록 가져오기*

- nx_lwm2m_client_object_instance_get_next: *개체의 인스턴스 목록 가져오기*

- nx_lwm2m_client_object_read: *개체 인스턴스의 리소스 값 읽기*

- nx_lwm2m_client_object_write: *개체 인스턴스의 리소스 값 변경*

**리소스 정보 및 값 설정:**

- nx_lwm2m_client_resource_info_set: *리소스 정보 설정*

- nx_lwm2m_client_resource_string_set: *리소스 값을 문자열로 설정*

- nx_lwm2m_client_resource_integer32_set: *리소스 값을 32비트 정수로 설정*

- nx_lwm2m_client_resource_integer64_set: *리소스 값을 64비트 정수로 설정*

- nx_lwm2m_client_resource_float32_set: *리소스 값을 32비트 float로 설정*

- nx_lwm2m_client_resource_float64_set: *리소스 값을 64비트 float로 설정*

- nx_lwm2m_client_resource_boolean_set: *리소스 값을 부울로 설정*

- nx_lwm2m_client_resource_objlnk_set: *리소스 값을 개체 링크로 설정*

- nx_lwm2m_client_resource_opaque_set: *리소스 값을 불투명으로 설정합니다*

- nx_lwm2m_client_resource_instance_set: *리소스 값을 여러 리소스에 대한 인스턴스로 설정*
-
- nx_lwm2m_client_resource_dim_set: *여러 리소스에 대한 리소스 차원 설정*

**리소스 정보 및 값 가져오기:**

- nx_lwm2m_client_resource_info_get: *리소스 정보 가져오기*

- nx_lwm2m_client_resource_string_get: *문자열 리소스의 값 가져오기*

- nx_lwm2m_client_resource_integer32_get: *32비트 정수 리소스의 값 가져오기*

- nx_lwm2m_client_resource_integer64_get: *64비트 정수 리소스의 값 가져오기*

- nx_lwm2m_client_resource_float32_get: *32비트 float 리소스의 값 가져오기*

- nx_lwm2m_client_resource_float64_get: *64비트 float 리소스의 값 가져오기*

- nx_lwm2m_client_resource_boolean_get: *부울 리소스의 값 가져오기*

- nx_lwm2m_client_resource_objlnk_get: *개체 링크 리소스의 값 가져오기*

- nx_lwm2m_client_resource_opaque_get: *불투명 리소스의 값 가져오기*

- nx_lwm2m_client_resource_instance_get: *여러 리소스에 대한 리소스 인스턴스 가져오기*

- nx_lwm2m_client_resource_dim_get: *여러 리소스에 대한 리소스 차원 가져오기*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

LWM2M 클라이언트를 만듭니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a>Description

이 서비스는 자체 ThreadX 스레드의 컨텍스트에서 실행되는 LWM2M 클라이언트 인스턴스를 만듭니다.

LWM2M 클라이언트는 보안(0), 서버(1), 액세스 제어(2) 및 디바이스(3)와 같은 OMA LWM2M 개체를 구현합니다. 다른 개체 구현은 애플리케이션에서 추가해야 합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **ip_ptr** 이전에 만든 IP 인스턴스에 대한 포인터.
- **packet_pool_ptr** 이 LWM2M 클라이언트의 기본 패킷 풀에 대한 포인터.
- **name_ptr** LWM2M 클라이언트 엔드포인트 이름에 대한 포인터.
- **name_length** LWM2M 클라이언트 엔드포인트 이름의 길이.
- **msisdn_ptr** SMS 바인딩에서 사용하기 위해 LWM2M 클라이언트에 연결할 수 있는 MSISDN에 대한 포인터이며, SMS 바인딩이 지원되지 않는 경우 NULL일 수 있습니다.
- **msisdn_length** MSISDN 번호의 길이.
- **binding_modes** LWM2M 클라이언트에서 지원하는 바인딩 및 모드이며, NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S 및 NX_LWM2M_BINDING_SQ 플래그의 조합이어야 합니다.
- **stack_ptr** LWM2M 클라이언트 스레드 스택 영역에 대한 포인터.
- **stack_size** LWM2M 클라이언트 스레드 스택 크기.
- **priority** LWM2M 클라이언트의 우선 순위.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** LWM2M 클라이언트를 만들었습니다.
- **NX_LWM2M_CLIENT_ERROR** LWM2M 클라이언트 만들기 오류입니다.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** 포트를 사용할 수 없습니다.
- **NX_PTR_ERROR** 잘못된 포인터.
- **NX_SIZE_ERROR** 잘못된 스택 크기.
- **NX_OPTION_ERROR** 잘못된 우선 순위.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

LWM2M 클라이언트를 삭제합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 만든 LWM2M 클라이언트 인스턴스를 삭제합니다.

현재 클라이언트에 연결된 모든 세션도 이 호출을 통해 삭제됩니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** LWM2M 클라이언트를 삭제했습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a>nx_lwm2m_client_device_callback_set

디바이스 개체의 애플리케이션 콜백을 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트에서 처리하지 않는 LWM2M 디바이스 개체 리소스에 대한 작업을 구현하는 애플리케이션 콜백을 설치합니다.

LWM2M 클라이언트는 오류 코드(11), 다시 설정 오류 코드(12) 및 지원되는 바인딩 및 모드(16)와 같은 리소스를 구현합니다. 다른 리소스에 대한 작업은 애플리케이션으로 리디렉션됩니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **operation_callback** "읽기", "검색", "쓰기" 및 "실행"에 대한 작업 콜백입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 콜백이 설정되었습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push
디바이스 개체에 오류 코드를 추가 합니다.

### <a name="prototype"></a>프로토타입

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a>Description

이 서비스는 새 인스턴스를 개체 디바이스의 오류 코드(11) 리소스에 추가합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **code** 새 오류 코드.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**

저장된 오류 코드의 최대 개수에

도달했습니다.

NX_PTR_ERROR 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

디바이스 개체의 오류 코드를 다시 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 디바이스 개체에서 모든 오류 코드 리소스 인스턴스를 삭제합니다. 이는 리소스 다시 설정 오류 코드(12)를 실행하는 것과 같습니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

디바이스 개체 리소스를 변경하도록 신호를 보냅니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a>Description

이 서비스는 애플리케이션에서 개체 디바이스의 리소스가 변경되었다는 신호를 LWM2M 클라이언트에 보내는 데 사용됩니다. LWM2M 서버에서 리소스를 관찰하는 경우 LWM2M 클라이언트에서 알림을 보냅니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **resource** 변경된 리소스를 설명하는 구조체에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a>nx_lwm2m_client_firmware_create

LWM2M 클라이언트 펌웨어 개체를 만듭니다. 

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a>Description

서비스는 애플리케이션에서 펌웨어 개체를 만드는 데 사용 됩니다.

### <a name="parameters"></a>매개 변수

- **firmware_ptr** LWM2M 클라이언트 펌웨어 개체에 대한 포인터.
- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **protocols** 지원되는 프로토콜.
- **package_callback** 패키지 콜백.
- **package_uri_callback** 패키지 URI 콜백.
- **update_callback** 업데이트 콜백.

### <a name="return-values"></a>반환 값

**NX_SUCCESS** 작업 성공.
**NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a>nx_lwm2m_client_firmware_package_info_set

LWM2M 클라이언트 펌웨어 패키지 정보를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a>Description

서비스는 애플리케이션에서 펌웨어 업데이트 개체의 패키지 정보 리소스를 설정하는 데 사용됩니다.

### <a name="parameters"></a>매개 변수

- **firmware_ptr** LWM2M 클라이언트 펌웨어 개체에 대한 포인터.
- **name** 펌웨어 패키지의 이름.
- **name_length** 이름 길이.
- **version** 펌웨어 패키지의 버전.
- **version_length** 버전의 길이.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a>nx_lwm2m_client_firmware_result_set

펌웨어 업데이트 개체의 업데이트 결과 리소스를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Description

서비스는 애플리케이션에서 펌웨어 업데이트 개체의 업데이트 결과 리소스를 설정하는 데 사용됩니다.

### <a name="parameters"></a>매개 변수

- **firmware_ptr** LWM2M 클라이언트 펌웨어 개체에 대한 포인터.
- **result** 업데이트 결과.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a>nx_lwm2m_client_firmware_state_set

펌웨어 업데이트 개체의 업데이트 결과 리소스를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Description

서비스는 애플리케이션에서 펌웨어 업데이트 개체의 상태를 설정하는 데 사용됩니다.

### <a name="parameters"></a>매개 변수

- **firmware_ptr** LWM2M 클라이언트 펌웨어 개체에 대한 포인터.
- **state** 펌웨어 개체의 상태.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

LWM2M 클라이언트를 잠급니다.

### <a name="prototype"></a>프로토타입

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

이 서비스는 서버 또는 다른 애플리케이션 스레드에서 LWM2M 개체로의 동시 액세스를 방지하기 위해 LWM2M 클라이언트를 잠급니다.

LWM2M 클라이언트가 현재 다른 스레드에서 잠겨 있는 경우 LWM2M 클라이언트의 잠금이 해제될 때까지 이 함수가 차단됩니다.

***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_** 쌍에 대한 호출은 중첩할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

개체 구현을 LWM2M 클라이언트에 추가합니다.

### <a name="prototype"></a>프로토타입

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a>Description

이 서비스는 새 개체 구현을 LWM2M 클라이언트에 추가합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **object_ptr** 개체 구현을 정의하는 구조체에 대한 포인터.
- **object_id** 개체 ID.
- **object_operation** 개체 작업 콜백 함수입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_ALREADY_EXIST** 개체 ID가 이미 있습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

새 개체 인스턴스를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트의 개체에 대한 '만들기(Create)' 작업을 수행하여 새 개체 인스턴스를 만듭니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **object_id** 개체 ID.
- **instance_id_ptr** 새 인스턴스의 ID에 대한 포인터이며 LWM2M 클라이언트에서 인스턴스 ID를 할당해야 하는 경우 **NULL** 일 수 있습니다. ID가 예약된 65535 값인 경우 LWM2M 클라이언트에서 인스턴스 ID를 할당합니다. NULL이 아닌 경우 할당된 ID가 호출 후에 반환됩니다.
- **num_values** 설정하는 값의 수.
- **values_ptr** 새 개체 인스턴스를 초기화하는 리소스 값의 배열에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_ALREADY_EXIST** 개체 인스턴스 ID가 이미 있습니다.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** 개체에서 인스턴스 만들기를 지원하지 않습니다.
- **NX_LWM2M_CLIENT_NO_MEMORY** 새 인스턴스를 저장하는 메모리를 할당할 수 없습니다.
- **NX_LWM2M_CLIENT_NOT_FOUND** 개체 ID가 없습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

개체 인스턴스를 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Delete(삭제)' 작업을 수행합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **object_id** 개체 ID.
- **instance_id** 개체 인스턴스 ID.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** 개체에서 인스턴스 삭제를 지원하지 않습니다.
- **NX_LWM2M_CLIENT_NOT_FOUND** 개체 ID 또는 개체 인스턴스 ID가 없습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

개체 인스턴스의 리소스를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Discover(검색)' 작업을 수행하여 개체에서 구현한 리소스 목록을 반환합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **object_id** 개체 ID.
- **instance_id** 개체 인스턴스 ID.
- **num_resources** 입력 시 대상 버퍼의 크기 및 출력 시 버퍼에 쓰인 요소의 수.
- **resources** 대상 버퍼에 대한 포인터.

### <a name="return-values"></a>반환 값

- *NX_SUCCESS** 작업이 성공함.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** 리소스 버퍼가 너무 작아 리소스 목록을 저장할 수 없습니다.
- **NX_LWM2M_CLIENT_NOT_FOUND** 개체 ID 또는 개체 인스턴스 ID가 없습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

개체 인스턴스의 리소스에 대해 'Execute(실행)' 작업을 수행합니다.

### <a name="prototype"></a>프로토타입

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트의 개체 인스턴스 리소스에 대한 'Execute(실행)' 작업을 수행합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **object_id** 개체 ID.
- **instance_id** 개체 인스턴스 ID.
- **resource_id** 리소스 ID.
- **arguments_ptr** 실행 작업의 인수에 대한 포인터이며, arguments_length가 0인 경우 NULL일 수 있습니다.
- **arguments_length** 인수의 길이.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** 리소스 버퍼가 너무 작아 리소스 목록을 저장할 수 없습니다.
- **NX_LWM2M_CLIENT_NOT_FOUND** 개체 ID 또는 개체 인스턴스 ID가 없습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a>nx_lwm2m_client_object_instance_add

개체에 개체 인스턴스 구현을 추가합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Description

이 서비스는 새 개체 인스턴스 구현을 LWM2M 클라이언트에 추가합니다. Instance_id_ptr 값이 **NX_LWM2M_CLIENT_RESERVED_ID** 이면 LWM2M 클라이언트는 사용되지 않는 인스턴스 ID를 자동으로 할당하고, 그렇지 않으면 LWM2M 클라이언트에서 값 애플리케이션 집합을 사용합니다. 새 인스턴스가 추가되면 애플리케이션으로 돌아가기 위해 instance_id가 instance_id_ptr에서 채워집니다.

### <a name="parameters"></a>매개 변수

- **object_ptr** 개체 구현을 정의하는 구조체에 대한 포인터.
- **instance_ptr** 개체 인스턴스 구현을 정의하는 구조체에 대한 포인터.
- **instance_id_ptr** 개체 인스턴스 ID에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_CLIENT_LWM2M_ALREADY_EXIST** 개체 ID가 이미 있습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a>nx_lwm2m_client_object_instance_next_get

개체의 다음 인스턴스를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 개체의 다음 개체 인스턴스에 대한 ID를 반환합니다. 현재 인스턴스 ID가 NX_LWM2M_RESERVED_ID (65535)로 설정된 경우 첫 번째 인스턴스의 ID가 반환됩니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **object_id** 개체 ID.
- **instance_id_ptr** 현재 개체 인스턴스 ID에 대한 포인터. 반환 시 개체의 다음 인스턴스 ID가 포함됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_CLIENT_LWM2M_NOT_FOUND** 지정된 인스턴스 ID가 개체의 마지막 ID이거나 개체 ID가 구현되지 않았습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a>nx_lwm2m_client_object_instance_remove

개체에서 개체 인스턴스 구현을 제거합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a>Description

이 서비스는 개체에서 개체 인스턴스를 제거합니다.

### <a name="parameters"></a>매개 변수

- ***object_ptr*** 개체 구현을 정의하는 구조체에 대한 포인터.
- **instance_ptr** 개체 인스턴스 구현을 정의하는 구조체에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_ALREADY_EXIST** 개체 ID가 이미 있습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a>nx_lwm2m_client_object_next_get

LWM2M 클라이언트의 다음 개체를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트에서 구현하는 다음 개체의 ID를 반환합니다. 현재 개체 ID가 NX_LWM2M_RESERVED_ID (65535)로 설정된 경우 첫 번째 개체 ID가 반환됩니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **object_id_ptr**: 현재 개체 ID에 대한 포인터. 반환 시 LWM2M 클라이언트에서 구현하는 다음 개체 ID가 포함됩니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_NOT_FOUND** 지정된 개체 ID가 데이터베이스의 마지막 ID입니다.
**NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

개체 인스턴스의 리소스 값을 읽습니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Read(읽기)' 작업을 수행합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **object_id** 개체 ID.
- **instance_id** 개체 인스턴스 ID.
- **num_values** 읽는 리소스의 수.
- **values_ptr** 읽는 리소스의 ID가 포함되는 NX_LWM2M_RESOURCE 배열에 대한 포인터. 반환 시 배열이 해당 형식 및 값으로 채워집니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** 리소스에서 읽기 작업을 지원하지 않습니다.
- **NX_LWM2M_CLIENT_NOT_FOUND** 개체 ID, 개체 인스턴스 ID 또는 리소스 ID가 없습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a>nx_lwm2m_client_object_remove

개체에서 개체 인스턴스 구현을 제거합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트에서 개체를 제거합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **object_ptr** 개체 구현을 정의하는 구조체에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_ALREADY_EXIST** 개체 ID가 이미 있습니다.
- **NX_PTR_ERROR** 잘못된 포인터.
- **NX_LWM2M_CLIENT_FORBIDDEN** 내부 개체를 제거할 수 없습니다.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a>nx_lwm2m_client_object_resource_changed

개체 리소스의 변경을 신호로 보냅니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션에서 개체 디바이스의 리소스가 변경되었다는 신호를 LWM2M 클라이언트에 보내는 데 사용됩니다. LWM2M 서버에서 리소스를 관찰하는 경우 LWM2M 클라이언트에서 알림을 보냅니다.

### <a name="parameters"></a>매개 변수

- **object_ptr** 개체 구현을 정의하는 구조체에 대한 포인터.
- ***instance_ptr*** 개체 인스턴스 구현을 정의하는 구조체에 대한 포인터.
- **resource** 변경된 리소스를 설명하는 구조체에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

개체 인스턴스의 리소스 값을 변경합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 클라이언트의 개체 인스턴스에 대한 'Write(쓰기)' 작업을 수행합니다.

*write_op* 매개 변수에 지정할 수 있는 쓰기 작업은 다음과 같습니다.

| 값 | 쓰기 &nbsp; 작업 | Description |
| --- | ---| --- |
| 0 | 부분 업데이트 | 새 값으로 제공되는 리소스를 추가하거나 업데이트하고, 다른 기존 리소스는 변경하지 않은 상태로 유지합니다. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | 인스턴스 바꾸기 | 개체 인스턴스를 제공된 새 리소스 값으로 바꿉니다. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** | 리소스 바꾸기 | 리소스를 제공된 새 리소스 값(여러 리소스를 바꾸는 데 사용됨)으로 바꿉니다. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | 부트스트랩 쓰기 | 부트스트랩 시퀀스의 호출을 나타냅니다. |

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.
- **object_id** 개체 ID.
- **instance_id** 개체 인스턴스 ID.
- **num_values** 쓰는 리소스의 수.
- **values_ptr** 리소스 ID, 형식 및 쓰는 값이 포함되는 NX_LWM2M_RESOURCE 배열에 대한 포인터.
- **write_op** 쓰기 작업의 형식.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 종류가 잘못되었습니다.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** 값의 길이가 너무 커서 인스턴스에 저장할 수 없습니다.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** 리소스에서 쓰기 작업을 지원하지 않습니다.
- **NX_LWM2M_CLIENT_NO_MEMORY** 리소스 값을 저장하는 메모리를 할당할 수 없습니다.
- **NX_LWM2M_CLIENT_NOT_ACCEPTABLE** 리소스의 값이 잘못되었습니다.
- **NX_LWM2M_CLIENT_NOT_FOUND** 개체 ID, 개체 인스턴스 ID 또는 리소스 ID가 없습니다.
- **NX_OPTION_ERROR** 잘못된 쓰기 작업의 형식. 
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a>nx_lwm2m_client_resource_boolean_get

부울 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Description

이 서비스는 부울 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스 값 설명에 대한 포인터.
- **bool_ptr**: 대상 부울 값에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 부울 값이 아닙니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a>nx_lwm2m_client_resource_boolean_set

부울 리소스의 값을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a>Description

이 서비스는 부울 리소스의 값을 설정합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **bool_data** 부울 데이터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a>nx_lwm2m_client_resource_dim_get

여러 리소스에 대한 리소스 차원을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a>Description

서비스는 여러 리소스에 대한 리소스 차원을 검색합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **dim** 대상 차원에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 부울 값이 아닙니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a>nx_lwm2m_client_resource_dim_set

여러 리소스에 대한 리소스 차원을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a>Description

서비스는 여러 리소스에 대한 리소스 차원을 설정합니다.

### <a name="parameters"></a>매개 변수

- **value** 리소스 값 설명에 대한 포인터.
- **dim** 차원 값.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a>nx_lwm2m_client_resource_float32_get

32비트 **float** 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Description

이 서비스는 32비트 **float** 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **float32_ptr** 대상 32비트 **float** 값에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 부울 값이 아닙니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a>nx_lwm2m_client_resource_float32_set

32비트 **float** 리소스의 값을 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a>Description

서비스는 32비트 **float** 리소스의 값을 설정합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **float32_data** 32비트 **float** 데이터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a>nx_lwm2m_client_resource_float64_get

64비트 float 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Description

이 서비스는 64비트 **float** 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **float64_ptr** 대상 64비트 **float** 값에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 float 값이 아님
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a>nx_lwm2m_client_resource_float64_set

64비트 **float** 리소스의 값을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Description

서비스는 64비트 **float** 리소스의 값을 설정합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **float64_data** 64비트 **float** 데이터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a>nx_lwm2m_client_resource_info_get

리소스 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a>Description

서비스는 리소스의 리소스 정보를 검색합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **resource_id** 대상 리소스 ID에 대한 포인터입니다.
- **operation** 대상 리소스 작업에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a>nx_lwm2m_client_resource_info_set

리소스 정보를 설정합니다.

### <a name="prototype"></a>프로토타입

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Description

서비스는 리소스 정보를 설정합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **resource_id** 리소스의 ID.
- **operation** 리소스의 작업.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a>nx_lwm2m_client_resource_instances_get

여러 리소스의 인스턴스를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a>Description

서비스는 리소스의 리소스 정보를 검색합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **resource_instances** 대상 리소스 ID에 대한 포인터.
- **count** 개수에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 부울 값이 아닙니다.
- **NX_LWM2M_CLIENT_NO_MEMORY** 인스턴스를 채울 메모리가 없습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a>nx_lwm2m_client_resource_instances_set

리소스 인스턴스를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a>Description

서비스는 여러 리소스에 대한 리소스 인스턴스를 설정합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **resource_instance** 리소스 인스턴스에 대한 포인터입니다.
- **count** 리소스 인스턴스 수입니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a>nx_lwm2m_client_resource_integer32_get

32비트 정수 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a>Description

이 서비스는 32비트 정수 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **integer32_ptr** 32비트 정수 값에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 정수 값이 아닙니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a>nx_lwm2m_client_resource_integer32_set

32비트 정수 리소스의 값을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a>Description

이 서비스는 32비트 정수 리소스의 값을 설정합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **integer32_data** 32비트 정수 데이터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a>nx_lwm2m_client_resource_integer64_get

64비트 정수 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a>Description

이 서비스는 64비트 정수 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **integer64_ptr** 64비트 정수 값에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 64비트 정수 값이 아닙니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a>nx_lwm2m_client_resource_integer64_set

## <a name="set-the-value-of-a-64-bit-integer-resource"></a>64비트 정수 리소스의 값을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a>Description

이 서비스는 64비트 정수 리소스의 값을 설정합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **integer64_data** 64비트 정수.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a>nx_lwm2m_client_resource_objlnk_get

개체 링크 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a>Description

이 서비스는 개체 링크의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **object_id** 개체 ID에 대한 포인터.
- **instance_id** 개체 인스턴스 ID에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_BAD_ENCODING**: 리소스 값이 개체 링크 값이 아님.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a>nx_lwm2m_client_resource_objlnk_set

리소스 인스턴스를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Description

서비스는 개체 링크 리소스의 값을 설정합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **object_id** 개체 ID.
- **instance_id** 개체 인스턴스 ID.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a>nx_lwm2m_client_resource_opaque_get

불투명 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a>Description

이 서비스는 불투명 리소스의 값을 검색합니다. 불투명 리소스 값은 버퍼 및 길이에 대한 포인터로 구성됩니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **opaque_ptr** 불투명 데이터에 대한 포인터.
- **opaque_length** 불투명 데이터 길이에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 불투명 리소스가 아닙니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a>nx_lwm2m_client_resource_opaque_set

불투명 리소스의 값을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a>Description

이 서비스는 불투명 리소스의 값을 설정합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **opaque_ptr** 불투명 데이터에 대한 포인터.
- **opaque_length** 불투명 데이터의 길이.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a>nx_lwm2m_client_resource_string_get

문자열 리소스의 값을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a>Description

이 서비스는 문자열 리소스의 값을 검색합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **string_ptr** 대상 문자열 포인터에 대한 포인터.
- **string_length** 대상 문자열 길이에 대한 포인터. 문자열이 null로 끝나는 경우 **NULL** 일 수 있습니다.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_BAD_ENCODING** 리소스 값이 문자열 값이 아닙니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a>nx_lwm2m_client_resource_string_set

문자열 리소스의 값을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a>Description

이 서비스는 64비트 정수 리소스의 값을 설정합니다.

### <a name="parameters"></a>매개 변수

- **resource** 리소스에 대한 포인터.
- **string_ptr** 문자열에 대한 포인터.
- **string_length** 문자열의 길이.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

부트스트랩 서버를 사용하여 세션을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a>Description

이 서비스는 부트스트랩 서버를 사용하여 세션을 시작합니다. 서버의 보안 개체에는 해당 보안 인스턴스가 있어야 합니다.

이 서버와 연결된 보안 인스턴스에서 'Hold Off'(지연) 리소스가 0과 다른 경우 세션에서 서버 시작 부트스트랩을 기다리며, 이 기간 이후에 서버에서 부트스트랩을 시작하지 않으면 클라이언트 시작 부트스트랩이 수행됩니다.

현재 활성 세션은 이 호출에서 중단되고 새 부트스트랩 서버 세션으로 대체됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.
- **security_id** 부트스트랩 서버의 보안 인스턴스 ID이며, 부트스트랩 서버에 정의된 보안 인스턴스가 없는 경우 NX_LWM2M_RESERVED_ID (65535)로 설정해야 합니다.
- **ip_address** 서버의 IP 주소.
- **port** 서버의 UDP 포트.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_ERROR** 부트스트랩 오류.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** 포트를 사용할 수 없습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

부트스트랩 서버를 사용하여 보안 세션을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Description

이 서비스는 보안 DTLS 연결을 사용하여 부트스트랩 서버에서 세션을 시작합니다. 서버의 보안 개체에는 해당 보안 인스턴스가 있어야 합니다.

이 함수를 호출하기 전에 DTLS 세션을 적절한 암호 그룹 및 키 자료를 사용하여 구성해야 합니다. **NX_SECURE_ENABLE_DTLS** 를 정의해야 합니다.

이 서버와 연결된 보안 인스턴스에서 'Hold Off'(지연) 리소스가 0과 다른 경우 세션에서 서버 시작 부트스트랩을 기다리며, 이 기간 이후에 서버에서 부트스트랩을 시작하지 않으면 클라이언트 시작 부트스트랩이 수행됩니다. 

현재 활성 세션은 이 호출에서 중단되고 새 부트스트랩 서버 세션으로 대체됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.
- **security_id** 부트스트랩 서버의 보안 인스턴스 ID이며, 부트스트랩 서버에 정의된 보안 인스턴스가 없는 경우 **NX_LWM2M_RESERVED_ID** (65535)로 설정해야 합니다.
- **ip_address** 서버의 IP 주소.
- **port** 서버의 UDP 포트.
- **dtls_session_ptr** 부트스트랩 세션에 사용하는 DTLS 세션
- **dtls_local_port** DTLS 세션에 사용되는 로컬 UDP 포트

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_ERROR** 부트스트랩 오류.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** 포트를 사용할 수 없습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

LWM2M 클라이언트 세션을 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Description

이 서비스는 기존 LWM2M 클라이언트에 연결된 새 LWM2M 클라이언트 세션을 만듭니다. 이 세션은 LWM2M 클라이언트에서 부트스트랩 서버 또는 LWM2M 서버와 통신하는 데 사용됩니다. 

애플리케이션에서 세션 상태가 업데이트될 때 호출되는 콜백 함수를 제공해야 합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.
- **client_ptr** 이전에 만든 LWM2M 클라이언트에 대한 포인터.
- **state_callback** 세션의 상태가 변경되었을 때 호출되는 애플리케이션 콜백.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

LWM2M 클라이언트 세션 삭제하기

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

이 서비스는 LWM2M Client 세션을 삭제합니다.

nx_lwm2m_client_delete를 호출하여 LWM2M 클라이언트를 삭제하면 클라이언트에 연결된 모든 세션도 삭제됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

LWM2M 서버를 사용하여 세션을 종료합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 서버에 대한 'De-Register(등록 취소)' 작업을 수행합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** 클라이언트가 서버에 등록되어 있지 않습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

세션의 마지막 오류를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

세션이 오류 상태인 경우 이 서비스에서 세션의 오류 코드를 반환합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 세션이 오류 상태가 아닙니다.
- **NX_LWM2M_CLIENT_ADDRESS_ERROR** 잘못된 서버 주소.
- **NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** 요청의 페이로드가 네트워크 버퍼에 맞지 않습니다.
- **NX_LWM2M_ CLIENT_DTLS_ERROR** 서버와의 보안 연결을 설정하지 못함.
- **NX_LWM2M_ CLIENT_ERROR** 지정되지 않은 오류.
- **NX_LWM2M_ CLIENT_FORBIDDEN** 서버에서 등록을 거부함.
- **NX_LWM2M_ CLIENT_NOT_FOUND** 업데이트/등록 취소 시 서버에서 클라이언트를 찾을 수 없음.
- **NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** 세션에 해당하는 서버 개체 인스턴스가 삭제되었습니다.
- **NX_LWM2M_ CLIENT_TIMED_OUT** 서버에서 응답하지 않음.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

LWM2M 서버를 사용하여 세션을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a>Description

이 서비스는 LWM2M 서버에 대한 'Register(등록)' 작업을 수행합니다. 서버의 서버 개체에는 해당 서버 인스턴스가 있어야 합니다.

등록이 성공하면 LWM2M 클라이언트는 서버에서 추가 작업을 처리하고, 클라이언트가 등록 취소될 때까지 'Update(업데이트)' 메시지를 정기적으로 보냅니다.

현재 활성 세션은 이 호출에서 중단되고 새 LWM2M 서버 세션으로 대체됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.
- **server_id** LWM2M 서버의 약식 서버 ID
- **ip_address** 서버의 IP 주소.
- **port** 서버의 UDP 포트.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_ERROR** 부트스트랩 오류.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** 포트를 사용할 수 없습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

LWM2M 서버를 사용하여 보안 세션을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Description

이 서비스는 보안 DTLS 연결을 사용하여 LWM2M 서버에 대한 'Register(등록)' 작업을 수행합니다. 서버의 서버 개체에는 해당 서버 인스턴스가 있어야 합니다.

이 함수를 호출하기 전에 DTLS 세션을 적절한 암호 그룹 및 키 자료를 사용하여 구성해야 합니다. **NX_SECURE_ENABLE_DTLS** 를 정의해야 합니다.

등록이 성공하면 LWM2M 클라이언트는 서버에서 추가 작업을 처리하고, 클라이언트가 등록 취소될 때까지 'Update(업데이트)' 메시지를 정기적으로 보냅니다.

현재 활성 세션은 이 호출에서 중단되고 새 LWM2M 서버 세션으로 대체됩니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.
- **server_id** LWM2M 서버의 약식 서버 ID
- **ip_address** 서버의 IP 주소.
- **port** 서버의 UDP 포트.
- **dtls_session_ptr** LWM2M 세션에 사용하는 DTLS 세션

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_ERROR** 부트스트랩 오류.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** 포트를 사용할 수 없습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a>nx_lwm2m_client_session_register_info_get

LWM2M 서버를 사용하여 보안 세션을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a>Description

부트스트랩 서버와 통신 세션이 설정된 경우입니다. 애플리케이션은 이 api를 호출하여 서버 및 다음 등록 단계에 대한 보안 정보를 가져올 수 있습니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.
- **security_instance_id** 보안 인스턴스 ID.
- **server_id** 대상 서버 ID에 대한 포인터.
- **server_uri** 대상 서버 uri에 대한 포인터.
- **server_uri_len** 대상 서버 uri 길이에 대한 포인터.
- **security_mode** 대상 보안 모드에 대한 포인터.
- **pub_key_or_id** 대상 공개 키 또는 ID에 대한 포인터.
- **pub_key_or_id_len** 대상 공개 키 또는 ID 길이에 대한 포인터.
- **server_pub_key** 대상 서버 공개 키에 대한 포인터.
- **server_pub_key_len** 대상 서버 공개 키 길이에 대한 포인터.
- **secret_key** 대상 비밀 키에 대한 포인터.
- **secret_key_len** 대상 비밀 키 길이에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_NOT_FOUND** 보안 개체 인스턴스가 없습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

LWM2M 서버를 사용하여 세션을 업데이트합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

이 서비스는 LWM2M 서버에 대한 'Update(업데이트)' 작업을 수행합니다.

### <a name="parameters"></a>매개 변수

- **session_ptr** LWM2M 클라이언트 세션 제어 블록에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** 클라이언트가 서버에 등록되어 있지 않습니다.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

LWM2M 클라이언트의 잠금을 해제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

***nx_lwm2m_client_unlock*** 호출로 이전에 잠긴 LWM2M 클라이언트의 잠금을 해제합니다.

### <a name="parameters"></a>매개 변수

- **client_ptr** LWM2M 클라이언트 제어 블록에 대한 포인터.

### <a name="return-values"></a>반환 값

- **NX_SUCCESS** 작업 성공.
- **NX_PTR_ERROR** 잘못된 포인터.

### <a name="allowed-from"></a>허용된 위치

스레드, 초기화

### <a name="example"></a>예제

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```