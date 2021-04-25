---
title: 챕터 4 - USBX 디바이스 서비스 설명
description: USBX 디바이스 서비스에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812954"
---
# <a name="description-of-usbx-device-services"></a>USBX 디바이스 서비스 설명

### <a name="ux_device_stack_alternate_setting_get"></a>ux_device_stack_alternate_setting_get

인터페이스 값에 대한 현재 대체 설정 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a>Description

이 함수는 USB 호스트에서 특정 인터페이스 값에 대한 현재 대체 설정을 가져오는 데 사용됩니다. 이 함수는 **GET_INTERFACE** 요청을 받을 때 컨트롤러 드라이버에서 호출됩니다.

### <a name="input-parameter"></a>입력 매개 변수

- **Interface_value** 현재 대체 설정이 쿼리되는 인터페이스 값

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 데이터 전송이 완료되었습니다.
- **UX_ERROR** (0xFF) 잘못된 인터페이스 값입니다.

### <a name="example"></a>예제

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a>ux_device_stack_alternate_setting_set

인터페이스 값에 대한 현재 대체 설정 지정

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Description

이 함수는 USB 호스트에서 특정 인터페이스 값에 대한 현재 대체 설정을 지정하는 데 사용됩니다. 이 함수는 **SET_INTERFACE** 요청을 받을 때 컨트롤러 드라이버에서 호출됩니다. **SET_INTERFACE** 가 완료되면 대체 설정 값이 클래스에 적용됩니다.

디바이스 스택은 대체 설정의 변경 내용을 반영하기 위해 이 인터페이스를 소유하는 클래스에 대한 **UX_SLAVE_CLASS_COMMAND_CHANGE** 를 발급합니다.

### <a name="parameters"></a>매개 변수

- **interface_value**: 현재 대체 설정이 지정된 인터페이스 값입니다.
- **alternate_setting_value**: 새 대체 설정 값입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 데이터 전송이 완료되었습니다.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) 인터페이스가 연결되어 있지 않습니다.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) 디바이스가 구성되어 있지 않습니다.
- **UX_ERROR** (0xFF) 잘못된 인터페이스 값입니다.

### <a name="example"></a>예제

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

새 USB 디바이스 클래스 등록

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 새 USB 디바이스 클래스를 등록하는 데 사용됩니다. 이를 등록하면 클래스의 인스턴스가 아닌 클래스 컨테이너가 시작됩니다. 클래스는 활성 스레드를 포함하고 특정 인터페이스에 연결되어야 합니다.

일부 클래스는 매개 변수 또는 매개 변수 목록을 필요로 합니다. 예를 들어 디바이스 저장소 클래스는 에뮬레이트하려는 저장 디바이스의 기하 도형을 필요로 합니다. 따라서 매개 변수 필드는 클래스 요구 사항에 따라 달라지며, 값 또는 클래스 값으로 채워진 구조체에 대한 포인터일 수 있습니다.

> [!NOTE]
> class_name의 C 문자열은 NULL로 끝나야 하며 길이(NULL 종결자 제외)는 **UX_MAX_CLASS_NAME_LENGTH** 보다 크지 않아야 합니다.

### <a name="parameters"></a>매개 변수

- **class_name** 클래스 이름
- **class_entry_function** 클래스의 항목 함수입니다.
- **configuration_number** 이 클래스가 연결된 구성 번호입니다.
- **interface_number** 이 클래스가 연결된 인터페이스 번호입니다.
- **parameter** 클래스 관련 매개 변수 목록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 클래스가 등록되었습니다.
- **UX_MEMORY_INSUFFICIENT** (0x12) 클래스 테이블에 남아 있는 항목이 없습니다.
- **UX_THREAD_ERROR** (0x16) 클래스 스레드를 만들 수 없습니다.

### <a name="example"></a>예제

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a>ux_device_stack_class_unregister

USB 디바이스 클래스 등록 취소

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 USB 디바이스 클래스의 등록을 취소하는 데 사용됩니다.

> [!NOTE]
> class_name의 C 문자열은 NULL로 끝나야 하며 길이(NULL 종결자 제외)는 **UX_MAX_CLASS_NAME_LENGTH** 보다 크지 않아야 합니다.

### <a name="parameters"></a>매개 변수

- **class_name**: 클래스 이름
- **class_entry_function**: 클래스의 항목 함수입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 클래스의 등록이 취소되었습니다.
- **UX_NO_CLASS_MATCH** (0x57) 클래스가 등록되지 않았습니다.

### <a name="example"></a>예제

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a>ux_device_stack_configuration_get

현재 구성 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a>Description

이 함수는 호스트가 디바이스에서 실행 중인 현재 구성을 가져오는 데 사용됩니다.

### <a name="input-parameter"></a>입력 매개 변수

없음

### <a name="return-value"></a>반환 값

- **UX_SUCCESS** (0x00) 데이터 전송이 완료되었습니다.

### <a name="example"></a>예제

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

현재 구성 설정

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a>Description

이 함수는 호스트가 디바이스에서 실행 중인 현재 구성을 설정하는 데 사용됩니다. 이 명령이 수신되면 USB 디바이스 스택은 이 구성에 연결된 각 인터페이스의 대체 설정 0을 활성화합니다.

### <a name="input-parameter"></a>입력 매개 변수

- **configuration_value** 호스트가 선택한 구성 값입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS** (0x00) 구성을 설정했습니다.

### <a name="example"></a>예제

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

호스트에 설명자 보내기

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a>Description

이 함수는 디바이스 쪽에서 호스트로 설명자를 반환하는 데 사용됩니다. 이 설명자는 디바이스 설명자, 구성 설명자 또는 문자열 설명자일 수 있습니다.

### <a name="parameters"></a>매개 변수

- **descriptor_type**: 설명자의 유형입니다. 다음 값 중 하나여야 합니다.
  - **UX_DEVICE_DESCRIPTOR_ITEM**
  - **UX_CONFIGURATION_DESCRIPTOR_ITEM**
  - **UX_STRING_DESCRIPTOR_ITEM**
  - **UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**
  - **UX_OTHER_SPEED_DESCRIPTOR_ITEM**
- **request_index**: 설명자의 인덱스입니다.
- **host_length**: 호스트에 필요한 길이입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 데이터 전송이 완료되었습니다.
- **UX_ERROR** (0xFF) 전송이 완료되지 않았습니다.

### <a name="example"></a>예제

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

디바이스 스택 연결 끊기

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a>Description

디바이스 연결이 끊어질 때 VBUS 관리자가 이 함수를 호출합니다. 디바이스 스택은 이 디바이스에 등록된 모든 클래스에 알리고 이후에 모든 디바이스 리소스를 해제합니다.

### <a name="input-parameter"></a>입력 매개 변수

없음

### <a name="return-value"></a>반환 값

- **UX_SUCCESS** (0x00) 디바이스의 연결이 끊어졌습니다.

### <a name="example"></a>예제

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

엔드포인트 정지 조건 요청

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a>Description

이 함수는 엔드포인트가 호스트에 정지 조건을 반환해야 하는 경우 USB 디바이스 클래스에 의해 호출됩니다.

### <a name="input-parameter"></a>입력 매개 변수

- **엔드포인트** 정지 조건이 요청된 엔드포인트입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS** (0x00) 이 작업을 수행했습니다.
- **UX_ERROR** (0xFF) 디바이스 상태가 잘못되었습니다.

### <a name="example"></a>예제

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

호스트의 절전 모드 해제

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a>Description

이 함수는 디바이스가 호스트의 절전 모드를 해제하려고 할 때 호출됩니다. 이 명령은 디바이스가 일시 중단 모드인 경우에만 유효합니다. USB 호스트의 절전 모드를 해제할 시기를 결정하는 것은 디바이스 애플리케이션에 따라 결정됩니다. 예를 들어 USB 모뎀은 전화 회선에서 링 신호를 감지한 경우 호스트의 절전 모드를 해제할 수 있습니다.

### <a name="input-parameter"></a>입력 매개 변수

없음

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 호출을 수행했습니다.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) 호출이 실패했습니다(디바이스가 일시 중단 모드가 아닐 수 있음).

### <a name="example"></a>예제

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

USB 디바이스 스택 초기화

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a>Description

이 함수는 애플리케이션이 USB 디바이스 스택을 초기화할 때 호출됩니다. 이 함수는 모든 클래스나 컨트롤러를 초기화하지 않습니다. 별도의 함수 호출을 사용하여 이 작업을 수행해야 합니다. 이 호출은 주로 USB 기능을 위한 디바이스 프레임워크를 스택에 제공합니다. 각 속도에 대해 완전히 별개의 디바이스 프레임워크를 사용할 수 있는 높은 속도와 전체 속도를 모두 지원합니다. 문자열 프레임워크와 여러 언어가 지원됩니다.

### <a name="parameters"></a>매개 변수

- **device_framework_high_speed**: 고속 프레임워크에 대한 포인터입니다.
- **device_framework_length_high_speed**: 고속 프레임워크의 길이입니다.
- **device_framework_full_speed**: 전체 속도 프레임워크에 대한 포인터입니다.
- **device_framework_length_full_speed**: 전체 속도 프레임워크의 길이입니다.
- **string_framework**: 문자열 프레임워크에 대한 포인터입니다.
- **string_framework_length**: 문자열 프레임워크의 길이입니다.
- **language_id_framework**: 문자열 언어 프레임워크에 대한 포인터입니다.
- **language_id_framework_length**: 문자열 언어 프레임워크의 길이입니다.
- **ux_system_slave_change_function**: 디바이스 상태가 변경될 때 호출되는 함수입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 이 작업을 수행했습니다.
- **UX_MEMORY_INSUFFICIENT** (0x12) 메모리가 부족하여 스택을 초기화할 수 없습니다.
- **UX_DESCRIPTOR_CORRUPTED** (0x42) 설명자가 잘못되었습니다.

### <a name="example"></a>예제

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

애플리케이션은 컨트롤러의 상태를 변경할 때 콜백을 요청할 수 있습니다. 컨트롤러에 대한 두 가지 주요 상태는 다음과 같습니다.

- **UX_DEVICE_SUSPENDED**
- **UX_DEVICE_RESUMED**

애플리케이션에 일시 중단/다시 시작 신호가 필요하지 않으면 UX_NULL 함수를 제공합니다.

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

스택 인터페이스 삭제

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Description

이 함수는 인터페이스를 제거해야 할 때 호출됩니다. 인터페이스는 디바이스를 추출하거나, 버스 재설정을 수행하거나, 새 대체 설정이 있는 경우 제거됩니다.

### <a name="input-parameter"></a>입력 매개 변수

- **인터페이스**: 제거할 인터페이스에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS** (0x00) 이 작업을 수행했습니다.

### <a name="example"></a>예제

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

현재 인터페이스 값 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a>Description

이 함수는 호스트가 현재 인터페이스를 쿼리할 때 호출됩니다. 디바이스가 현재 인터페이스 값을 반환합니다.

> [!NOTE]
> 이 함수는 더 이상 사용되지 않습니다. 이 함수는 레거시 소프트웨어에 사용할 수 있지만 새 소프트웨어는 ***ux_device_stack_alternate_setting_get*** 함수를 대신 사용해야 합니다.

### <a name="input-parameter"></a>입력 매개 변수

- **interface_value** 반환할 인터페이스 값입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 이 작업을 수행했습니다.
- **UX_ERROR** (0xFF) 인터페이스가 없습니다.

### <a name="example"></a>예제

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

인터페이스의 대체 설정 변경

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Description

이 함수는 호스트가 인터페이스의 대체 설정 변경을 요청할 때 호출됩니다.

### <a name="parameters"></a>매개 변수

- **device_framework**: 이 인터페이스에 대한 디바이스 프레임워크의 주소입니다.
- **device_framework_length**: 디바이스 프레임워크의 길이입니다.
- **alternate_setting_value**: 이 인터페이스에서 사용할 대체 설정 값입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 이 작업을 수행했습니다.
- **UX_ERROR** (0xFF) 인터페이스가 없습니다.

### <a name="example"></a>예제

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a>ux_device_stack_interface_start

인터페이스 인스턴스를 소유하는 클래스 검색 시작

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Description

이 함수는 호스트가 인터페이스를 선택하고 디바이스 스택이 이 인터페이스 인스턴스를 소유할 디바이스 클래스를 검색해야 하는 경우 호출됩니다.

### <a name="input-parameter"></a>입력 매개 변수

- **interface**: 생성된 인터페이스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 이 작업을 수행했습니다.
- **UX_NO_CLASS_MATCH** (0x57) 이 인터페이스에 대한 클래스가 없습니다.

### <a name="example"></a>예제

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

호스트로 데이터 전송 요청

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a>Description

이 함수는 클래스 또는 스택이 호스트에 데이터를 전송하려고 할 때 호출됩니다. 호스트는 항상 디바이스를 폴링하지만 디바이스는 데이터를 미리 준비할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **transfer_request**: 전송 요청에 대한 포인터입니다.
- **slave_length**: 디바이스에서 반환하려는 길이입니다.
- **host_length**: 호스트가 요청한 길이입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 이 작업을 수행했습니다.
- **UX_TRANSFER_NOT_READY** (0x25) 디바이스 상태가 잘못되었습니다. **ATTACHED**, **CONFIGURED** 또는 **ADDRESSED** 상태여야 합니다.
- **UX_ERROR** (0xFF) 전송 오류입니다.

### <a name="example"></a>예제

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

전송 요청 취소

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a>Description

이 함수는 애플리케이션이 전송 요청을 취소해야 하거나, 스택이 엔드포인트와 연결된 전송 요청을 중단해야 하는 경우 호출됩니다.

### <a name="parameters"></a>매개 변수

- **transfer_request**: 전송 요청에 대한 포인터입니다.
- **completion_code**:이 전송 요청이 완료되기를 기다리는 클래스로 반환되는 오류 코드입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS** (0x00) 이 작업을 수행했습니다.

### <a name="example"></a>예제

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a>ux_device_stack_uninitialize

스택 초기화 취소

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a>Description

이 함수는 애플리케이션이 USBX 디바이스 스택을 초기화 취소해야 할 때 호출되며 모든 디바이스 스택 리소스가 해제됩니다. ux_device_stack_class_unregister를 통해 모든 클래스의 등록을 취소한 후에 이 함수를 호출해야 합니다.

### <a name="parameters"></a>매개 변수

없음

### <a name="return-value"></a>반환 값

**UX_SUCCESS** (0x00) 이 작업을 수행했습니다.
