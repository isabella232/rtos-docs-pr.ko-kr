---
title: 챕터 3 - ARMv8-M의 ThreadX API
description: 이 챕터는 ARMv8-M 관련 ThreadX 서비스에 대한 설명입니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 14bdfab3d56476d52ba91f859cec4af4ab7f4bef
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377511"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a>챕터 3 - ARMv8-M의 ThreadX API

이 챕터는 알파벳 순서로 정렬된 ARMv8-M 관련 ThreadX 서비스에 대한 설명을 포함합니다. 서비스 이름은 모든 유사한 서비스가 함께 그룹화되도록 설계되었습니다. 다음 설명의 '반환 값' 섹션에서 **굵게** 표시된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **TX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않는 값은 완전히 사용하지 않도록 설정됩니다.

- [tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) 보안 메모리에 스레드 스택을 할당합니다.
- [tx_thread_secure_stack_free](#tx_thread_secure_stack_free) 보안 메모리에서 스레드 스택을 해제합니다.

## <a name="tx_thread_secure_stack_allocate"></a>tx_thread_secure_stack_allocate

보안 메모리에 스레드 스택을 할당합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a>Description

이 서비스는 stack_size 바이트 크기의 스택을 보안 메모리에 할당합니다. 보안 함수를 호출하는 모든 스레드에 대해 이 함수를 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **thread_ptr** 이전에 만든 스레드에 대한 포인터입니다.

- **stack_size** 보안 스택의 크기입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS** (0x00) 요청을 수행했습니다.

- **TX_SIZE_ERROR** (0x05) 스택 크기가 범위를 벗어났습니다.

- **TX_THREAD_ERROR** (0x0E) 잘못된 스레드 포인터입니다.

- **TX_NO_MEMORY** (0x10) 메모리를 할당할 수 없습니다.

- **TX_CALLER_ERROR** (0x13) 이 서비스의 잘못된 호출자입니다.

- **TX_FEATURE_NOT_ENABLED** (0xFF) 시스템이 보안 모드에서 실행되도록 컴파일되었습니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a>참고 항목

tx_thread_secure_stack_free

##  <a name="tx_thread_secure_stack_free"></a>tx_thread_secure_stack_free

보안 메모리에서 스레드 스택을 해제합니다. 

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

이 서비스는 보안 메모리에서 스레드의 보안 스택을 해제합니다. 스레드에 보안 스택이 있고 스레드가 더 이상 보안 함수를 호출하지 않아도 되거나 스레드를 삭제하는 경우 이 함수를 호출해야 합니다.

### <a name="input-parameters"></a>입력 매개 변수

- **thread_ptr** 이전에 만든 스레드에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS** (0x00) 요청을 수행했습니다.

- **TX_THREAD_ERROR** (0x0E) 잘못된 스레드 포인터입니다.

- **TX_CALLER_ERROR** (0x13) 이 서비스의 잘못된 호출자입니다.

- **TX_FEATURE_NOT_ENABLED** (0xFF) 시스템이 보안 모드에서 실행되도록 컴파일되었습니다.

### <a name="allowed-from"></a>허용된 원본

초기화, 스레드

### <a name="example"></a>예제

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a>참고 항목

tx_thread_secure_stack_allocate
