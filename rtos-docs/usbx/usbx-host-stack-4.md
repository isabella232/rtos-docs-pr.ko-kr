---
title: 4장 - USBX 호스트 서비스 설명
description: USBX 호스트 서비스에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d730658c07f3cd7cec8c75a47818314bdc63f35a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813272"
---
# <a name="chapter-4---description-of-usbx-host-services"></a>4장 - USBX 호스트 서비스 설명

## <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

호스트 작업을 위해 USBX를 초기화합니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a>Description

이 함수는 USB 호스트 스택을 초기화합니다. 제공된 메모리 영역은 USBX 내부 사용을 위해 설정됩니다. 호스트 컨트롤러 및 클래스 등록에 사용하도록 USBX가 준비되면 UX_SUCCESS가 반환됩니다.

### <a name="input-parameter"></a>입력 매개 변수

- **system_change_function** 디바이스 변경을 애플리케이션에 알리기 위한 선택적 콜백 루틴에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS** (0x00) 성공적으로 초기화했습니다.
- **UX_MEMORY_INSUFFICIENT** (0x12) 메모리 할당에 실패했습니다.

### <a name="example"></a>예제

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

엔드포인트에 대한 이전 요청에 연결된 모든 트랜잭션을 중단합니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Description

이 함수는 엔드포인트에 연결된 특정 이전 요청에 대해 활성 또는 보류 상태인 모든 트랜잭션을 취소합니다. 이전 요청에 콜백 함수가 연결된 경우 콜백 함수가 UX_TRANSACTION_ABORTED 상태로 호출됩니다.

### <a name="input-parameter"></a>입력 매개 변수

- **endpoint** 엔드포인트에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 오류가 없습니다.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) 엔드포인트 핸들이 유효하지 않습니다.

### <a name="example"></a>예제

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a>ux_host_stack_class_get

클래스 컨테이너에 대한 포인터를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a>Description

이 함수는 클래스 컨테이너에 대한 포인터를 반환합니다. 클래스 또는 애플리케이션에서 디바이스를 열려는 경우 클래스는 USB 스택에서 해당 컨테이너를 가져와서 인스턴스를 검색해야 합니다.

> [!NOTE]
> class_name의 C 문자열은 NULL로 종료되어야 하며 길이(NULL 종결자 제외)는 UX_MAX_CLASS_NAME_LENGTH보다 크지 않아야 합니다.

### <a name="parameters"></a>매개 변수

- **class_name** 클래스 이름에 대한 포인터입니다.
- **class** 클래스 이름에 대해 클래스 컨테이너가 포함된 함수 호출로 업데이트되는 포인터입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 오류가 없습니다. 반환 시 클래스 필드는 클래스 컨테이너에 대한 포인터와 함께 파일링됩니다.
- **UX_HOST_CLASS_UNKNOWN** (0x59) 스택에서 클래스를 알 수 없습니다.

### <a name="example"></a>예제

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a>ux_host_stack_class_register

USB 스택에 USB 클래스를 등록합니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a>Description

이 함수는 USB 스택에 USB 클래스를 등록합니다. 클래스는 다음과 같은 명령을 전송하기 위해 USB 스택의 진입점을 지정해야 합니다.

- **UX_HOST_CLASS_COMMAND_QUERY**
- **UX_HOST_CLASS_COMMAND_ACTIVATE**
- **UX_HOST_CLASS_COMMAND_DESTROY**

> [!NOTE]
> *class_name* 의 C 문자열은 NULL로 종료되어야 하며 길이(NULL 종결자 제외)는 **UX_MAX_CLASS_NAME_LENGTH** 보다 크지 않아야 합니다.

### <a name="parameters"></a>매개 변수

- **class_name** 클래스 이름에 대한 포인터입니다. 유효한 항목은 USBX의 USB 클래스 아래에 있는 ux_system_initialize.c 파일에서 찾을 수 있습니다.
- **class_entry_address** 클래스의 항목 함수 주소입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 클래스가 성공적으로 설치되었습니다.
- **UX_MEMORY_ARRAY_FULL** (0x1a) 이 클래스를 저장할 메모리가 더 이상 없습니다.
- **UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) 호스트 클래스가 이미 설치되어 있습니다.

### <a name="example"></a>예:

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a>ux_host_stack_class_instance_create

클래스 컨테이너에 대해 새 클래스 인스턴스를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Description

이 함수는 클래스 컨테이너에 대해 새 클래스 인스턴스를 만듭니다. 클래스의 인스턴스는 클래스 복잡성을 줄이기 위해 클래스 코드에 포함되지 않습니다. 대신 각 클래스 인스턴스는 주 스택에 있는 클래스 컨테이너에 연결됩니다.

### <a name="parameters"></a>매개 변수

- **class** 클래스 컨테이너에 대한 포인터입니다.
- **class_instance** 생성할 클래스 인스턴스에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS** (0x00) 클래스 인스턴스가 클래스 컨테이너에 연결되었습니다.

### <a name="example"></a>예제

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a>ux_host_stack_class_instance_destroy

클래스 컨테이너에 대한 클래스 인스턴스를 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Description

이 함수는 클래스 컨테이너에 대한 클래스 인스턴스를 삭제합니다.

### <a name="parameters"></a>매개 변수

- **class** 클래스 컨테이너에 대한 포인터입니다.
- **class_instance** 삭제할 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 클래스 인스턴스가 삭제되었습니다.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) 클래스 인스턴스가 클래스 컨테이너에 연결되지 않았습니다.

### <a name="example"></a>예제

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a>ux_host_stack_class_instance_get

특정 클래스에 대한 클래스 인스턴스 포인터를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a>Description

이 함수는 특정 클래스에 대한 클래스 인스턴스 포인터를 반환합니다. 클래스의 인스턴스는 클래스 복잡성을 줄이기 위해 클래스 코드에 포함되지 않습니다. 대신 각 클래스 인스턴스가 클래스 컨테이너에 연결됩니다. 이 함수는 클래스 컨테이너 내에서 클래스 인스턴스를 검색하기 위해 사용됩니다.

### <a name="parameters"></a>매개 변수

- **class** 클래스 컨테이너에 대한 포인터입니다.
- **class_index** 컨테이너에 연결된 클래스 목록 내에서 함수 호출에 사용되는 인덱스입니다.
- **class_instance** 함수 호출에 의해 반환될 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 클래스 인스턴스를 찾았습니다.

- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) 클래스 컨테이너에 연결된 클래스 인스턴스가 더 이상 없습니다.

### <a name="example"></a>예제

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

구성 컨테이너에 대한 포인터를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Description

이 함수는 디바이스 핸들 및 구성 인덱스를 기준으로 구성 컨테이너를 반환합니다.

### <a name="parameters"></a>매개 변수

- **device** 요청된 구성을 소유하는 디바이스 컨테이너에 대한 포인터입니다.
- **configuration_index** 검색할 구성의 인덱스입니다.
- **configuration** 반환할 구성 컨테이너에 대한 포인터의 주소입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 구성을 찾았습니다.
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) 디바이스 컨테이너가 존재하지 않습니다.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인덱스에 대한 구성 핸들이 존재하지 않습니다.

### <a name="example"></a>예제

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

디바이스에 대해 특정 구성을 선택합니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Description

이 함수는 디바이스에 대해 특정 구성을 선택합니다. 이 구성이 디바이스에 설정되면 기본적으로 각 디바이스 인터페이스 및 관된 대체 설정 0이 디바이스에서 활성화됩니다. 디바이스/인터페이스 클래스가 특정 인터페이스 설정을 변경하려는 경우 **ux_host_stack_interface_setting_select** 서비스 호출을 실행해야 합니다.

### <a name="parameters"></a>매개 변수

- **configuration** 이 디바이스에 대해 사용할 구성 컨테이너에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 구성을 성공적으로 선택했습니다.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 구성 핸들이 존재하지 않습니다.
- **UX_OVER_CURRENT_CONDITION** (0x43) 이 구성에 대한 버스에 과전류 상태가 존재합니다.

### <a name="example"></a>예제

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

디바이스 컨테이너에 대한 포인터를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a>Description

이 함수는 해당 인덱스를 기반으로 디바이스 컨테이너를 반환합니다. 디바이스 인덱스는 0부터 시작합니다. 컨트롤러가 여러 개 있을 수 있고 바이트 인덱스로는 충분하지 않을 수 있기 때문에 인덱스는 ULONG입니다. 디바이스 인덱스를 버스 관련 디바이스 주소와 혼동해서는 안 됩니다.

### <a name="parameters"></a>매개 변수

- **device_index** 디바이스의 인덱스입니다.
- **device** 반환할 디바이스 컨테이너에 대한 포인터 주소입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 디바이스 컨테이너가 존재하고 반환됩니다.
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) 알 수 없는 디바이스입니다.

### <a name="example"></a>예제

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a>ux_host_stack_interface_endpoint_get

엔드포인트 컨테이너를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Description

이 함수는 인터페이스 핸들 및 엔드포인트 인덱스를 기반으로 엔드포인트 컨테이너를 반환합니다. 인터페이스의 대체 설정이 선택되었거나 엔드포인트 검색 전 기본 설정이 사용된다고 가정합니다.

### <a name="parameters"></a>매개 변수

- **interface** 요청된 엔드포인트가 포함된 인터페이스 컨테이너에 대한 포인터입니다.
- **endpoint_index** 이 인터페이스에 있는 엔드포인트의 인덱스입니다.
- **endpoint** 반환할 엔드포인트 컨테이너의 주소입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 엔드포인트 컨테이너가 존재하고 반환됩니다.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) 지정된 인터페이스가 없습니다.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) 엔드포인트 인덱스가 없습니다.

### <a name="example"></a>예제

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

USB 스택에 USB 컨트롤러를 등록합니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a>Description

이 함수는 USB 스택에 USB 컨트롤러를 등록합니다. 주로 이 컨트롤러에서 사용되는 메모리를 할당하고 초기화 명령을 컨트롤러에 전달합니다.

### <a name="parameters"></a>매개 변수

- **hcd_name** 호스트 컨트롤러의 이름입니다.
- **hcd_function** 초기화를 담당하는 호스트 컨트롤러의 함수입니다.
- **hcd_param1** hcd에 사용되는 IO 또는 메모리 리소스입니다.
- **hcd_param2** 호스트 컨트롤러에 사용되는 IRQ입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 컨트롤러가 올바르게 초기화되었습니다.
- **UX_MEMORY_INSUFFICIENT** (0x12) 이 컨트롤러의 메모리가 부족합니다.
- **UX_PORT_RESET_FAILED** (0x31) 컨트롤러를 초기화하지 못했습니다.
- **UX_CONTROLLER_INIT_FAILED** (0x32) 컨트롤러를 올바르게 초기화하지 못했습니다.

### <a name="example"></a>예제

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a>ux_host_stack_configuration_interface_get

인터페이스 컨테이너 포인터를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a>Description

이 함수는 구성 핸들, 인터페이스 인덱스 및 대체 설정 인덱스를 기반으로 인터페이스 컨테이너를 반환합니다.

### <a name="parameters"></a>매개 변수

- **configuration** 인터페이스를 소유하는 구성 컨테이너에 대한 포인터입니다.
- **interface_index** 검색할 인터페이스 인덱스입니다.
- **alternate_setting_index** 검색할 인터페이스 내의 대체 설정입니다.
- **interface** 반환할 인터페이스 컨테이너 포인터의 주소입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 인터페이스 인덱스 및 대체 설정에 대한 인터페이스 컨테이너를 찾아 반환했습니다.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 구성이 없습니다.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) 인터페이스가 없습니다.

### <a name="example"></a>예제

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

인터페이스에 대한 대체 설정을 선택합니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a>Description

이 함수는 선택한 구성에 속하는 지정된 인터페이스에 대해 특정 대체 설정을 선택합니다. 이 함수는 기본 대체 설정에서 새 설정으로 변경하거나 기본 대체 설정으로 돌아가는 데 사용됩니다. 새 대체 설정을 선택하면 이전 엔드포인트 특성이 유효하지 않으므로 다시 로드해야 합니다.

### <a name="input-parameter"></a>입력 매개 변수

- **interface** 대체 설정을 선택할 인터페이스 컨테이너에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 이 인터페이스의 대체 설정이 성공적으로 선택되었습니다.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) 인터페이스가 없습니다.

### <a name="example"></a>예제

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a>ux_host_stack_transfer_request_abort

보류 중인 이전 요청을 중단합니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Description

이 함수는 이전에 제출된 보류 중인 이전 요청을 중단합니다. 이 함수는 특정 이전 요청만 취소합니다. 이 함수에 대한 콜백은 UX_TRANSFER REQUEST_STATUS_ABORT 상태를 갖습니다.

### <a name="parameters"></a>매개 변수

- **transfer request** 중단할 이전 요청에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 이 이전 요청에 대한 USB 전송이 취소되었습니다.

### <a name="example"></a>예제

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

USB 전송을 요청합니다.

### <a name="prototype"></a>프로토타입

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Description

이 함수는 USB 트랜잭션을 수행합니다. 항목에서 이전 요청은 이 트랜잭션에 대해 선택된 엔드포인트 파이프 및 전송과 관련된 매개 변수(데이터 페이로드, 트랜잭션 길이)를 제공합니다. 제어 파이프의 경우 트랜잭션이 중단되고 제어 전송의 3단계가 완료되었거나 이전 오류가 있는 경우에만 반환됩니다. 다른 파이프의 경우 USB 스택이 USB에 트랜잭션을 예약하지만 완료될 때까지 대기하지 않습니다. 비중단 파이프에 대한 각 이전 요청은 완료 루틴 처리기를 지정해야 합니다.

함수 호출이 반환되면 트랜잭션 결과가 포함되므로 이전 요청의 상태를 검사해야 합니다.

### <a name="input-parameter"></a>입력 매개 변수

- **transfer_request** 이전 요청에 대한 포인터입니다. 이전 요청에는 전송에 요구된 모든 필수 정보가 포함됩니다.

### <a name="return-values"></a>반환 값

- **UX_SUCCESS** (0x00) 이 이전 요청에 대한 USB 전송이 올바르게 예약되었습니다. 이전 요청이 완료되면 이전 요청의 상태 코드를 검사해야 합니다.
- **UX_MEMORY_INSUFFICIENT** (0x12) 필요한 컨트롤러 리소스를 할당할 메모리가 부족합니다.
- **UX_TRANSFER_NOT_READY** (0x25) 잘못된 디바이스 상태입니다. ATTACHED, ADDRESSED 또는 CONFIGURED여야 합니다.

### <a name="example"></a>예제:

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
