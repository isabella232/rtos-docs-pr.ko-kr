---
title: 5장 - 모듈 관리자 API
author: philmea
description: 이 문서에는 애플리케이션의 상주 부분에 사용할 수 있는 모듈 관리자 API가 요약되어 있습니다.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8e4da0f9591fd0b5d6249292f00266d96ccb67923c42632a4cfd8c39fa1f129
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799118"
---
# <a name="chapter-5---module-manager-apis"></a>5장 - 모듈 관리자 API

## <a name="summary-of-module-manager-apis"></a>모듈 관리자 API 요약

애플리케이션의 상주 부분에 사용할 수 있는 추가 API는 다음과 같이 여러 가지가 있습니다.

- ***txm_module_manager_external_memory_enable** _ - _*모듈에서 공유 메모리 공간에 액세스할 수 있도록 합니다.
- ***txm_module_manager_file_load** _ - _*FileX를 통해 파일에서 모듈을 로드합니다.
- ***txm_module_manager_in_place_load** _ - _*모듈 데이터를 로드하고 현재 위치에서 실행합니다.
- ***txm_module_manager_initialize** _ - _*모듈 관리자를 초기화합니다.
- ***txm_module_manager_mm_initialize** _ - _*메모리 관리 하드웨어를 초기화합니다.
- ***txm_module_manager_maximum_module_priority_set** _ - _*모듈에서 허용되는 최대 스레드 우선 순위를 설정합니다.
- ***txm_module_manager_memory_fault_notify** _ - _*메모리 오류 발생 시 애플리케이션 콜백을 등록합니다.
- ***txm_module_manager_memory_load** _ - _*메모리에서 모듈을 로드합니다.
- ***txm_module_manager_object_pool_create** _ - _*모듈 개체 풀을 만듭니다.
- ***txm_module_manager_properties_get** _ - _*모듈 속성을 가져옵니다.
- ***txm_module_manager_start** _ - _*지정된 모듈 실행을 시작합니다.
- ***txm_module_manager_stop** _ - _*지정된 모듈 실행을 중지합니다.
- ***txm_module_manager_unload** _ - _*모듈을 언로드합니다.

---

## <a name="txm_module_manager_external_memory_enable"></a>txm_module_manager_external_memory_enable

모듈에서 공유 메모리 공간에 액세스할 수 있도록 합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a>Description

이 서비스는 모듈에서 액세스할 수 있는 공유 메모리 영역에 대한 항목을 메모리 관리 하드웨어 테이블에 만듭니다.

### <a name="input-parameters"></a>입력 매개 변수

- **module_instance** 모듈 인스턴스에 대한 포인터입니다.
- **start_address** 공유 메모리 영역의 시작 주소입니다.
- **length** 공유 메모리 영역의 길이입니다.
- **attributes** 메모리 영역 특성(캐시, 읽기, 쓰기 등)입니다. 특성은 포트에 특정됩니다. 특성 형식은 [부록](appendix.md)을 참조하세요.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메모리 항목을 만드는 데 성공했습니다.
- **TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았거나 기능을 사용할 수 없습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 모듈 인스턴스입니다.
- **TX_START_ERROR**(0x10) 모듈이 로드된 상태가 아닙니다.
- **TXM_MODULE_ALIGNMENT_ERROR**(0xF0) 잘못된 시작 주소 맞춤입니다.
- **TXM_MODULE_INVALID_PROPERTIES**(0xF3) 호환되지 않는 속성입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a>txm_module_manager_file_load

FileX를 통해 파일에서 모듈을 로드합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a>Description

이 서비스는 지정된 파일에 포함된 모듈의 이진 이미지를 모듈 메모리 영역으로 로드하고 실행을 준비합니다. 제공된 미디어는 이미 열려 있다고 가정합니다.

> [!NOTE]
> 파일을 로드하는 데는 FileX 시스템을 사용합니다. FileX 액세스를 사용하도록 설정하려면 모듈, 모듈 라이브러리, 모듈 관리자 및 ThreadX 라이브러리(모듈 관리자 소스 포함)를 프로젝트에 정의된 **FX_FILEX_PRESENT** 로 빌드해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **module_instance** 모듈 인스턴스에 대한 포인터입니다.
- **module_name** 모듈 이름입니다.
- **media_ptr** 이미 열려 있는 FileX 미디어에 대한 포인터입니다.
- **file_name** 모듈의 이진 파일 이름입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 모듈 로드에 성공했습니다.
- **TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.
- **TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.
- **TX_NO_MEMORY**(0x10) 메모리가 부족하여 모듈을 로드할 수 없습니다.
- **TX_NOT_DONE**(0x20) 미디어가 열려 있지 않거나, 파일을 찾지 못했거나, 파일이 잘못되었습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 모듈 포인터입니다.
- **TXM_MODULE_ALIGNMENT_ERROR**(0xF0) 잘못된 맞춤입니다.
- **TXM_MODULE_ALREADY_LOADED**(0xF1) 모듈이 이미 로드되었습니다.
- **TXM_MODULE_INVALID**(0xF2) | 잘못된 모듈 프리앰블입니다.
- **TXM_MODULE_INVALID_PROPERTIES**(0xF3) 호환되지 않는 속성입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>참고 항목

- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_in_place_load"></a>txm_module_manager_in_place_load

모듈 데이터만 로드하고 기존 위치에서 모듈을 실행합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Description

이 서비스는 모듈의 데이터 영역만 모듈 메모리 영역으로 로드하고 실행을 준비합니다. 모듈 코드 실행은 현재 위치 즉, 제공된 위치의 모듈 프리앰블에 지정된 주소 오프셋에서 수행됩니다.

### <a name="input-parameters"></a>입력 매개 변수

- **module_instance** 모듈 인스턴스에 대한 포인터입니다.
- **module_name** 모듈 이름입니다.
- **location** 프리앰블이 맨 앞에 있는 모듈 코드 영역에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 모듈 로드에 성공했습니다.
- **TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.
- **TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.
- **TX_NO_MEMORY**(0x10) 메모리가 부족하여 모듈을 로드할 수 없습니다.
- **TX_PTR_ERROR**(0x03) 포인터, 모듈 인스턴스 또는 모듈 프리앰블이 잘못되었습니다.
- **TXM_MODULE_ALIGNMENT_ERROR**(0xF0) 잘못된 맞춤입니다.
- **TXM_MODULE_ALREADY_LOADED**(0xF1) 모듈이 이미 로드되었습니다.
- **TXM_MODULE_INVALID**(0xF2) 잘못된 모듈 프리앰블입니다.
- **TXM_MODULE_INVALID_PROPERTIES**(0xF3) 호환되지 않는 속성입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>참고 항목

- txm_module_manager_file_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_initialize"></a>txm_module_manager_initialize

모듈 관리자를 초기화합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a>Description

이 서비스는 모듈 로드에 사용되는 메모리 영역을 포함하여 모듈 관리자의 내부 리소스를 초기화합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **module_memory_start** 모듈 메모리의 시작에 대한 포인터입니다.
- **module_memory_size** 모듈 메모리의 크기(바이트)입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 초기화에 성공했습니다.
- **TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a>참고 항목

- txm_module_manager_object_pool_create

---

## <a name="txm_module_manager_initialize_mmu"></a>txm_module_manager_initialize_mmu

메모리 관리 하드웨어를 초기화합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a>Description

이 서비스는 MMU를 초기화합니다.

### <a name="input-parameters"></a>입력 매개 변수

없음

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 초기화에 성공했습니다.
- **TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a>txm_module_manager_maximum_module_priority_set

모듈에서 허용되는 최대 스레드 우선 순위를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a>Description

이 서비스는 모듈에서 허용되는 최대 스레드 우선 순위를 설정합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **module_instance** 모듈 인스턴스에 대한 포인터입니다.
- **priority** 최대 스레드 우선 순위입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 초기화에 성공했습니다.
- **TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 모듈 인스턴스입니다.
- **TX_START_ERROR**(0x10) 모듈이 로드된 상태가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a>txm_module_manager_memory_fault_notify

메모리 오류 발생 시 애플리케이션 콜백을 등록합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a>Description

이 서비스는 지정된 애플리케이션 메모리 오류 알림 콜백 함수를 모듈 관리자에 등록합니다. 메모리 오류가 발생하면 잘못된 스레드에 대한 포인터와 잘못된 스레드에 해당하는 모듈 인스턴스를 사용하여 이 함수를 호출합니다. 모듈 관리자 처리에서는 자동으로 잘못된 스레드는 종료하고 모듈의 다른 모든 스레드는 그대로 둡니다. 메모리 오류와 관련된 모듈에서 수행할 작업은 애플리케이션에 따라 달라집니다.

메모리 오류 자체에 대한 자세한 내용은 내부 **_txm_module_manager_memory_fault_info** 구조체를 참조하세요.

> [!NOTE]
> 메모리 오류 알림 콜백 함수는 메모리 오류 예외에서 직접 실행되므로 인터럽트 서비스 루틴에서 허용되는 ThreadX API만 호출될 수 있습니다. 그러므로 잘못된 모듈을 중지하고 언로드하려면 애플리케이션 알림 콜백에서 애플리케이션 작업으로 신호를 송신하여 모듈을 중지하고 언로드할 수 있도록 해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **notify_function** 애플리케이션 메모리 오류 알림 콜백을 가리키는 함수 포인터입니다. NULL 값을 제공하면 메모리 오류 알림을 사용하지 않도록 설정합니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 알림 함수 등록에 성공했습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a>txm_module_manager_memory_load

메모리에서 모듈을 로드합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Description

이 서비스는 모듈의 코드 및 데이터 영역을 ***txm_module_manager_initialize*** 를 통해 설정된 모듈 메모리 영역으로 로드하고 실행을 준비합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **module_instance** 모듈 인스턴스에 대한 포인터입니다.
- **module_name** 모듈 이름입니다.
- **location** 프리앰블이 맨 앞에 있는 모듈 코드 영역에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 모듈 로드에 성공했습니다.
- **TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.
- **TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.
- **TX_NO_MEMORY**(0x10) 메모리가 부족하여 모듈을 로드할 수 없습니다.
- **TX_PTR_ERROR**(0x03) 포인터, 모듈 인스턴스 또는 모듈 프리앰블이 잘못되었습니다.
- **TXM_MODULE_ALIGNMENT_ERROR**(0xF0) 잘못된 맞춤입니다.
- **TXM_MODULE_ALREADY_LOADED**(0xF1) 모듈이 이미 로드되었습니다.
- **TXM_MODULE_INVALID**(0xF2) 잘못된 모듈 프리앰블입니다.
- **TXM_MODULE_INVALID_PROPERTIES**(0xF3) 호환되지 않는 속성입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a>참고 항목

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_object_pool_create"></a>txm_module_manager_object_pool_create

모듈 개체 풀을 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a>Description

이 서비스는 모듈이 ThreadX/NetX 개체를 할당하여 시스템 개체를 모듈 메모리 영역 외부에 유지할 수 있도록 하는 모듈 관리자 개체 메모리 풀을 만듭니다.

### <a name="input-parameters"></a>입력 매개 변수

- **pool_memory_start** 개체 메모리 시작에 대한 포인터입니다.
- **pool_memory_size** 개체 메모리 풀 크기(바이트)입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 초기화에 성공했습니다.
- **TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a>참고 항목

- txm_module_manager_initialize

---

## <a name="txm_module_manager_properties_get"></a>txm_module_manager_properties_get

모듈 속성을 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a>Description

이 서비스는 모듈 속성(프리앰블에 지정됨)을 반환합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **module_instance** 모듈 인스턴스에 대한 포인터입니다.
- **module_properties_ptr** 모듈 속성 대상에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 초기화에 성공했습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 포인터입니다.
- **TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a>txm_module_manager_start

모듈 실행을 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Description

이 서비스는 이미 로드되고 지정된 모듈의 실행을 시작합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **module_instance** 이전에 로드된 모듈 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 모듈 시작에 성공했습니다.
- **TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.
- **TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 포인터 또는 모듈 인스턴스입니다.
- **TX_START_ERROR**(0x10) 모듈이 이미 시작되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>참고 항목

- txm_module_manager_stop

---

## <a name="txm_module_manager_stop"></a>txm_module_manager_stop

모듈 실행을 중지합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Description

이 서비스는 이전에 로드되어 시작된 모듈을 중지합니다. 모듈 중지에는 모듈의 선택적 중지 스레드 실행, 모든 스레드 종료, 해당 모듈과 연결된 모든 리소스 삭제 작업이 포함되어 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **module_instance** 모듈 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 모듈 중지에 성공했습니다.
- **TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.
- **TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 포인터 또는 모듈 인스턴스입니다.
- **TX_START_ERROR**(0x10) 모듈이 시작되지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>참고 항목

- txm_module_manager_start

---

## <a name="txm_module_manager_unload"></a>txm_module_manager_unload

모듈을 언로드합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Description

이 서비스는 이전에 로드되고 중지된 모듈을 언로드하여 모든 연결된 모듈 메모리 리소스를 해제합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **module_instance** 모듈 인스턴스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS** 0x00) 모듈 언로드에 성공했습니다.
- **TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.
- **TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.
- **TX_NOT_DONE**(0x20) 잘못된 모듈이거나 모듈이 중지되지 않았습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 포인터 또는 모듈 인스턴스입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="example"></a>예제

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>참고 항목

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_stop
