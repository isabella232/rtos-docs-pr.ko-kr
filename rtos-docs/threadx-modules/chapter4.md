---
title: 4장 - 모듈 API
author: philmea
ms.author: philmea
description: 이 문서에는 모듈에 사용할 수 있는 추가 API가 요약되어 있습니다.
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5804e2dbb8d08a272abc85a583576f43b7204c1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810303"
---
# <a name="chapter-4---module-apis"></a>4장 - 모듈 API

## <a name="summary-of-module-apis"></a>모듈 API 요약

모듈에는 다음과 같이 다양한 추가 API 함수를 사용할 수 있습니다.

- ***txm_module_application_request** _ - _*상주 코드에 대한 애플리케이션별 요청입니다.
- ***txm_module_object_allocate** _ - _*모듈 외부에 개체용 메모리를 할당합니다.
- ***txm_module_object_deallocate** _ - _*이전에 할당된 개체 메모리에 대한 할당을 취소합니다.
- ***txm_module_object_pointer_get** _ - _*시스템 개체를 찾고 개체 포인터를 검색합니다.
- ***txm_module_object_pointer_get_extended** _ - _*시스템 개체를 찾고 개체 포인터인 이름 길이 보호를 검색합니다.

## <a name="return-values"></a>반환 값

일부 Azure RTOS API에 대해 추가 오류 코드가 반환됩니다. 해당 추가 오류 코드는 다음과 같이 정의됩니다.

- **TXM_MODULE_INVALID_PROPERTIES**(0xF3): 모듈에 API 호출을 수행하는 데 적합한 속성이 없음을 나타냅니다. 예를 들어 추적 API는 사용자 모드에서 호출합니다.
- **TXM_MODULE_INVALID_MEMORY**(0xF4): 모듈에서 제공한 메모리가 잘못되었거나 잘못된 위치에 있음을 나타냅니다. 예를 들어 메모리 보호 모듈에서는 모듈이 액세스할 수 있는 메모리에 개체 제어 블록을 배치할 수 없습니다.
- **TXM_MODULE_INVALID_CALLBACK**(0xF5): API에 지정된 콜백이 모듈 코드 범위를 벗어나므로 잘못되었습니다.

---

## <a name="txm_module_application_request"></a>txm_module_application_request

상주 코드에 대한 애플리케이션별 요청입니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션의 상주 부분에 대해 지정된 요청을 수행합니다. 호출 전에 요청 구조가 준비되어 있다고 가정합니다. 요청의 실제 처리는 ***_txm_module_manager_application_request*** 함수의 상주 코드에서 발생합니다. 기본적으로 이 함수는 비어 있으며 상주 애플리케이션 개발자가 수정하도록 설계되었습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **request** 요청 ID입니다(애플리케이션이 정의됨).
- **param_1** 첫 번째 매개 변수입니다.
- **param_2** 두 번째 매개 변수입니다.
- **param_3** 세 번째 매개 변수입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 요청에 성공했습니다.
- **TX_NOT_AVAILABLE**(0x1D) 요청이 상주 코드에서 지원되지 않습니다.

### <a name="allowed-from"></a>허용되는 위치

모듈 스레드

### <a name="example"></a>예제

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a>txm_module_object_allocate

개체 풀(상주 애플리케이션에서 만든 풀)에 모듈 개체 제어 블록용 메모리를 할당합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a>Description

이 서비스는 모듈 외부의 메모리에서 모듈 개체용 메모리를 할당합니다. 이렇게 하면 모듈 코드의 개체 제어 블록 손상을 방지하는 데 도움이 됩니다. 메모리 보호 시스템에서는 모든 개체 제어 블록을 만들려면 먼저 이 API를 사용하여 할당해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **object_ptr** 할당에 성공한 개체 포인터 대상입니다.
- **object_size** 할당할 개체의 크기(바이트)입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 개체 할당에 성공했습니다.
- **TX_NO_MEMORY**(0x10) 메모리가 부족합니다.
- **TX_NOT_AVAILABLE**(0x1D) 모듈 관리자가 할당할 개체 풀을 만들지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

모듈 스레드

### <a name="example"></a>예제

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a>참고 항목

- txm_module_object_deallocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_deallocate"></a>txm_module_object_deallocate

이전에 할당한 개체 메모리를 할당 취소합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a>Description

이 서비스는 더 이상 필요하지 않으므로 사용되지 않습니다.

***txm_module_object_allocate* *_를 통해 이전에 할당한 메모리를 _* _tx_\__delete service*** 에서 할당 취소합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **object_ptr** 할당을 취소할 개체 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 개체 할당에 성공했습니다.

### <a name="allowed-from"></a>허용되는 위치

모듈 스레드

### <a name="example"></a>예제

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a>참고 항목

- txm_module_object_allocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_pointer_get"></a>txm_module_object_pointer_get

시스템 개체를 찾고 개체 포인터를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a>Description

이 서비스는 특정 이름을 사용하는 특정 형식의 개체 포인터를 검색합니다. 개체를 찾지 못하면 오류가 반환됩니다. 개체를 찾으면 해당 개체의 주소가 “object_ptr”에 배치됩니다. 그러면 이 포인터로 시스템 서비스를 호출하여 상주 코드 및/또는 시스템의 다른 로드된 모듈을 조작할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **object_type** 요청된 ThreadX 개체 유형입니다. 유효한 유형은 다음과 같습니다.
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **name** 개체를 만들 때 정의된 애플리케이션별 개체 이름입니다.
- **object_ptr** 개체 포인터 대상입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 개체 가져오기에 성공했습니다.
- **TX_OPTION_ERROR**(0x08) 잘못된 개체 유형입니다.
- **TX_PTR_ERROR**(0x03) 잘못된 대상입니다.
- **TX_SIZE_ERROR**(0x05) 잘못된 크기입니다.
- **TX_NO_INSTANCE**(0x0D) 개체를 찾지 못했습니다.

### <a name="allowed-from"></a>허용되는 위치

모듈 스레드

### <a name="example"></a>예제

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>참고 항목

- txm_module_manager_object_pointer_get_extended

---

## <a name="txm_module_object_pointer_get_extended"></a>txm_module_object_pointer_get_extended

시스템 개체를 찾고 개체 포인터를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a>Description

이 서비스는 특정 이름을 사용하는 특정 형식의 개체 포인터를 검색합니다. 개체를 찾지 못하면 오류가 반환됩니다. 개체를 찾으면 해당 개체의 주소가 “object_ptr”에 배치됩니다. 그러면 이 포인터로 시스템 서비스를 호출하여 상주 코드 및/또는 시스템의 다른 로드된 모듈을 조작할 수 있습니다.

### <a name="input-parameters"></a>입력 매개 변수

- **object_type** 요청된 ThreadX 개체 유형입니다. 유효한 유형은 다음과 같습니다.
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **name** 개체를 만들 때 정의된 애플리케이션별 개체 이름입니다.
- **name_length** 이름 길이입니다.
- **object_ptr** 개체 포인터 대상입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 개체 가져오기에 성공했습니다.
- **TX_OPTION_ERROR**(0x08) 잘못된 개체 유형입니다.
- **TX_PTR_ERROR**(0x03) 잘못된 대상입니다.
- **TX_SIZE_ERROR**(0x05) 잘못된 크기입니다.
- **TX_NO_INSTANCE**(0x0D) 개체를 찾지 못했습니다.

### <a name="allowed-from"></a>허용되는 위치

모듈 스레드

### <a name="example"></a>예제

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>참고 항목

- txm_module_manager_object_pointer_get
