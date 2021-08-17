---
title: 4장 - Azure RTOS ThreadX 서비스 설명
description: 이 장에서는 모든 Azure RTOS ThreadX 서비스를 알파벳 순서로 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dabc1603423d8422ed6f8f540f8a06e80d14ec0098c886ca8731ac8ce981f15d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783410"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a>4장 - Azure RTOS ThreadX 서비스 설명

이 장에서는 모든 Azure RTOS ThreadX 서비스를 알파벳 순서로 설명합니다. 서비스 이름은 모든 유사한 서비스가 함께 그룹화되도록 설계되었습니다. 다음 설명의 “반환 값” 섹션에서 **굵게** 표시된 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **TX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않는 값은 완전히 사용하지 않도록 설정됩니다. 또한 “**가능한 선점**” 제목 아래 표시된 “**예**”는 서비스를 호출하면 우선 순위가 더 높은 스레드를 다시 시작할 수 있으므로 호출 스레드를 선점할 수 있음을 나타냅니다.

## <a name="tx_block_allocate"></a>tx_block_allocate

고정 크기 메모리 블록을 할당합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 메모리 풀에서 고정 크기 메모리 블록을 할당합니다. 메모리 블록의 실제 크기는 메모리 풀을 만드는 동안 결정됩니다.

> [!IMPORTANT]
> 애플리케이션 코드가 할당된 메모리 블록의 외부에 쓰지 않도록 하는 것이 중요합니다. 외부에 쓰면 인접한(일반적으로 이후) 메모리 블록에 손상이 발생합니다. 결과를 예측할 수 없으며 치명적인 결과가 발생하는 경우가 많습니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** <br>이전에 만든 메모리 블록 풀에 대한 포인터입니다.
- **block_ptr** <br>대상 블록 포인터에 대한 포인터입니다. 할당에 성공하면 할당된 메모리 블록 주소가 이 매개 변수에서 가리키는 위치에 배치됩니다.
- **wait_option** <br>사용할 수 있는 메모리 블록이 없는 경우의 서비스 작동 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **TX_NO_WAIT**(0x00000000) - **TX_NO_WAIT** 를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환이 수행됩니다. 초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.
  - **TX_WAIT_FOREVER**(0xFFFFFFF) - **TX_WAIT_FOREVER** 를 선택하면 메모리 블록을 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.
  - ‘시간 제한 값’(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 메모리 블록을 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메모리 블록 할당에 성공했습니다.
- **TX_DELETED**(0x01) 스레드가 일시 중단된 동안 메모리 블록 풀이 삭제되었습니다.
- **TX_NO_MEMORY**(0x10) 서비스가 지정된 대기 시간 내에 메모리 블록을 할당하지 못했습니다.
- **TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.
- **TX_POOL_ERROR**(0x02) 잘못된 메모리 블록 풀 포인터입니다.
- **TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.
- **TX_PTR_ERROR**(0x03) 대상 포인터에 대한 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;

UINT status;

/* Allocate a memory block from my_pool. Assume that the pool has
already been created with a call to tx_block_pool_create. */

status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
  TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the address of
the allocated block of memory. */
```

### <a name="see-also"></a>참고 항목

- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_create"></a>tx_block_pool_create

고정 크기 메모리 블록 풀을 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a>Description

이 서비스는 고정 크기 메모리 블록 풀을 만듭니다. 지정된 메모리 영역은 다음 수식을 사용하여 가능한 한 많은 고정 크기 메모리 블록으로 나뉩니다.

**total blocks** = (**total bytes**) / (**block size** + sizeof(void *))

> [!NOTE]
>*각 메모리 블록에는 사용자에게 표시되지 않고 앞의 수식에서 “sizeof(void *)”로 표시되는 오버헤드 포인터 하나가 포함되어 있습니다.*

### <a name="parameters"></a>매개 변수

- **pool_ptr**  메모리 블록 풀 제어 블록에 대한 포인터입니다.
- **name_ptr** 메모리 블록 풀의 이름에 대한 포인터입니다.
- **block_size** 각 메모리 블록의 바이트 수입니다.
- **pool_start** 메모리 블록 풀의 시작 주소입니다. 시작 주소는 ULONG 데이터 형식의 크기에 맞춰야 합니다.
- **pool_size** 메모리 블록 풀에 사용할 수 있는 총 바이트 수입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메모리 블록 풀 만들기에 성공했습니다.
- **TX_POOL_ERROR**(0x02) 잘못된 메모리 블록 풀 포인터입니다. 포인터가 NULL이거나 풀이 이미 만들어져 있습니다.
- **TX_PTR_ERROR**(0x03) 풀 시작 주소가 잘못되었습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.
- **TX_SIZE_ERROR**(0x05) 풀 크기가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_BLOCK_POOL my_pool;

UINT status;

/* Create a memory pool whose total size is 1000 bytes starting at
address 0x100000. Each block in this pool is defined to be 50 bytes
long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
  50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18 memory blocks
of 50 bytes each. The reason there are not 20 blocks in the pool is
because of the one overhead pointer associated with each block. */
```

### <a name="see-also"></a>참고 항목

- tx_block_allocate, tx_block_pool_delete
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_delete"></a>tx_block_pool_delete

메모리 블록 풀을 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 블록 메모리 풀을 삭제합니다. 이 풀의 메모리 블록을 기다리는 일시 중단된 모든 스레드는 다시 시작되며 **TX_DELETED** 반환 상태가 지정됩니다.

> [!NOTE]
> 이 서비스가 완료된 후 사용할 수 있는 풀과 연결된 메모리 영역은 애플리케이션에서 관리해야 합니다. 또한 애플리케이션은 삭제된 풀이나 이전 메모리 블록을 사용하지 않도록 해야 합니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 이전에 만든 메모리 블록 풀에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메모리 블록 풀 삭제에 성공했습니다.
- **TX_POOL_ERROR**(0x02) 잘못된 메모리 블록 풀 포인터입니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a>참고 항목

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

블록 풀에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_block_pool_info_get(
    TX_BLOCK_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *total_blocks,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BLOCK_POOL **next_pool);
```

### <a name="description"></a>Description

이 서비스는 지정된 블록 메모리 풀에 대한 정보를 검색합니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr**  이전에 만든 메모리 블록 풀에 대한 포인터입니다.
- **name** 블록 풀 이름 포인터 대상에 대한 포인터입니다.
- **available** 블록 풀의 사용 가능한 블록 수 대상에 대한 포인터입니다.
- **total_blocks** 블록 풀의 총 블록 수 대상에 대한 포인터입니다.
- **first_suspended** 이 블록 풀의 일시 중단 목록에 있는 첫 번째 스레드 포인터 대상에 대한 포인터입니다.
- **suspended_count** 이 블록 풀의 현재 일시 중단된 스레드 수 대상에 대한 포인터입니다.
- **next_pool** 다음에 만들 블록 풀 포인터 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 블록 풀 정보 검색에 성공했습니다.
- **TX_POOL_ERROR**(0x02) 잘못된 메모리 블록 풀 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_BLOCK_POOL my_pool;
CHAR *name;
ULONG available;
ULONG total_blocks;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BLOCK_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
  &available,&total_blocks,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>참고 항목

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

블록 풀 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a>Description

이 서비스는 지정된 메모리 블록 풀에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. 

### <a name="parameters"></a>매개 변수

- **pool_ptr**  이전에 만든 메모리 블록 풀에 대한 포인터입니다.
- **allocates** 이 풀에서 수행된 할당 요청 수 대상에 대한 포인터입니다.
- **releases** 이 풀에서 수행된 해제 요청 수 대상에 대한 포인터입니다.
- **suspensions** 이 풀의 스레드 할당 일시 중단 수 대상에 대한 포인터입니다.
- **timeouts** 이 풀의 할당 일시 중단 시간 제한 수 대상에 대한 포인터입니다.

>[!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 블록 풀 성능 가져오기에 성공했습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 블록 풀 포인터입니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_BLOCK_POOL my_pool;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created block
pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
  &releases,
  &suspensions,
  &timeouts);

/* If status is TX_SUCCESS the performance information was successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

블록 풀 시스템 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

이 서비스는 애플리케이션의 모든 메모리 블록 풀에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. 

### <a name="parameters"></a>매개 변수

- **allocates** 모든 블록 풀에서 수행된 총 할당 요청 수 대상에 대한 포인터입니다.
- **releases** 모든 블록 풀에서 수행된 총 해제 요청 수 대상에 대한 포인터입니다.
- **suspensions** 모든 블록 풀의 총 스레드 할당 일시 중단 수 대상에 대한 포인터입니다.
- **timeouts** 모든 블록 풀의 총 할당 일시 중단 시간 제한 수 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 블록 풀 시스템 성능 가져오기에 성공했습니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
ULONG       allocates;
ULONG       releases;
ULONG       suspensions;
ULONG       timeouts;

/* Retrieve performance information on all the block pools in
the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
    &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

블록 풀 일시 중단 목록의 우선 순위를 지정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a>Description

이 서비스는 일시 중단 목록 맨 앞에 있는, 이 풀의 메모리 블록 때문에 일시 중단된 스레드를 가장 높은 우선 순위로 지정합니다. 다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 메모리 블록 풀 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 블록 풀 우선 순위 지정에 성공했습니다.
- **TX_POOL_ERROR**(0x02) 잘못된 메모리 블록 풀 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제
```c
TX_BLOCK_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_block_release call will wake up this thread. */
```

### <a name="see-also"></a>참고 항목

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_release"></a>tx_block_release

고정된 크기의 메모리 블록을 해제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a>Description

이 서비스는 이전에 할당된 블록을 연결된 메모리 풀로 다시 해제합니다. 이 풀의 메모리 블록을 기다리는 일시 중단된 스레드가 하나 이상인 경우 일시 중단된 첫 번째 스레드에 이 메모리 블록이 제공되고 해당 스레드는 다시 시작됩니다.

>[!IMPORTANT]
>애플리케이션은 메모리 블록 영역이 풀로 다시 해제된 후에는 이 메모리 블록 영역을 사용하지 않도록 해야 합니다.

### <a name="parameters"></a>매개 변수

- **block_ptr** 이전에 할당된 메모리 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메모리 블록 해제에 성공했습니다.
- **TX_PTR_ERROR**(0x03) 메모리 블록에 대한 포인터가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;
UINT status;

/* Release a memory block back to my_pool. Assume that the
pool has been created and the memory block has been
allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
to by memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a>참고 항목

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize

## <a name="tx_byte_allocate"></a>tx_byte_allocate

메모리 바이트를 할당합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 메모리 바이트 풀에서 지정된 바이트 수를 할당합니다.

> [!IMPORTANT]
> 애플리케이션 코드가 할당된 메모리 블록의 외부에 쓰지 않도록 하는 것이 중요합니다. 외부에 쓰면 인접한(일반적으로 이후) 메모리 블록에 손상이 발생합니다. 결과를 예측할 수 없으며 치명적인 결과가 발생하는 경우가 많습니다.

> [!NOTE]
> 이 서비스의 성능은 블록 크기의 함수와 풀의 조각화 양에 따라 결정됩니다. 따라서 이 서비스는 시간이 중요한 스레드를 실행하는 중에는 사용하면 안 됩니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** <br>이전에 만든 메모리 블록 풀에 대한 포인터입니다.
- **memory_ptr** <br>대상 메모리 포인터에 대한 포인터입니다. 할당에 성공하면 할당된 메모리 영역 주소가 이 매개 변수에서 가리키는 위치에 배치됩니다.
- **memory_size** <br>요청된 바이트 수입니다.
- **wait_option** <br>사용할 수 있는 메모리가 충분하지 않은 경우의 서비스 작동 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **TX_NO_WAIT**(0x00000000) - **TX_NO_WAIT** 를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다. 초기화에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.
  - **TX_WAIT_FOREVER** 0xFFFFFFFF) - **TX_WAIT_FOREVER** 를 선택하면 충분한 메모리를 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.
  - ‘시간 제한 값’(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 메모리를 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메모리 할당에 성공했습니다.
- **TX_DELETED**(0x01) 스레드가 일시 중단된 동안 메모리 풀이 삭제되었습니다.
- **TX_NO_MEMORY**(0x10) 서비스가 지정된 대기 시간 내에 메모리를 할당하지 못했습니다.
- **TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.
- **TX_POOL_ERROR**(0x02) 잘못된 메모리 풀 포인터입니다.
- **TX_PTR_ERROR**(0x03) 대상 포인터에 대한 포인터가 잘못되었습니다.
- **TX_SIZE_ERROR**(0x05) 요청된 크기가 0이거나 풀보다 큽니다.
- **TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제
```c
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT status;
/* Allocate a 112 byte memory area from my_pool. Assume
that the pool has already been created with a call to
tx_byte_pool_create. */
status = tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
    112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
address of the allocated memory area. */
```

### <a name="see-also"></a>참고 항목

- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_create"></a>tx_byte_pool_create

메모리 바이트 풀을 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a>Description

이 서비스는 지정된 영역에 메모리 바이트 풀을 만듭니다. 처음에는 풀이 기본적으로 하나의 매우 큰 빈 블록으로 구성됩니다. 하지만 할당이 진행되면 이 풀이 더 작은 블록으로 나뉩니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 메모리 풀 제어 블록에 대한 포인터입니다.
- **name_ptr** 메모리 풀 이름에 대한 포인터입니다.
- **pool_start** 메모리 풀의 시작 주소입니다. 시작 주소는 ULONG 데이터 형식의 크기에 맞춰야 합니다.
- **pool_size** 메모리 풀에 사용할 수 있는 총 바이트 수입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메모리 풀 만들기에 성공했습니다.
- **TX_POOL_ERROR**(0x02) 잘못된 메모리 풀 포인터입니다. 포인터가 NULL이거나 풀이 이미 만들어져 있습니다.
- **TX_PTR_ERROR**(0x03) 풀의 시작 주소가 잘못되었습니다.
- **TX_SIZE_ERROR**(0x05) 풀 크기가 잘못되었습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Create a memory pool whose total size is 2000 bytes
starting at address 0x500000. */
status = tx_byte_pool_create(&my_pool, "my_pool_name",
    (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
allocating memory. */
```

### <a name="see-also"></a>참고 항목

- tx_byte_allocate
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

메모리 바이트 풀을 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 메모리 바이트 풀을 삭제합니다. 이 풀의 메모리를 기다리는 일시 중단된 모든 스레드는 다시 시작되며 **TX_DELETED** 반환 상태가 지정됩니다.

> [!IMPORTANT]
> 이 서비스가 완료된 후 사용할 수 있는 풀과 연결된 메모리 영역은 애플리케이션에서 관리해야 합니다. 또한 애플리케이션은 삭제된 풀이나 해당 풀에서 이전에 할당된 메모리를 사용하지 않도록 해야 합니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 이전에 만든 메모리 풀에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메모리 풀 삭제에 성공했습니다.
- **TX_POOL_ERROR**(0x02) 잘못된 메모리 풀 포인터입니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a>참고 항목

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

바이트 풀에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_byte_pool_info_get(
    TX_BYTE_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *fragments,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BYTE_POOL **next_pool);
```

### <a name="description"></a>Description

이 서비스는 지정된 메모리 바이트 풀에 대한 정보를 검색합니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 이전에 만든 메모리 풀에 대한 포인터입니다.
- **name** 바이트 풀 이름에 대한 포인터 대상에 대한 포인터입니다.
- **available** 풀에서 사용 가능한 바이트 수 대상에 대한 포인터입니다.
- **fragments** 바이트 풀에 있는 총 메모리 조각 수 대상에 대한 포인터입니다.
- **first_suspended** 이 바이트 풀의 일시 중단 목록에 있는 첫 번째 스레드 포인터 대상에 대한 포인터입니다.
- **suspended_count** 이 바이트 풀의 현재 일시 중단된 스레드 수 대상에 대한 포인터입니다.
- **next_pool** 다음에 만들 바이트 풀 포인터 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 풀 정보 검색에 성공했습니다.
- **TX_POOL_ERROR**(0x02) 잘못된 메모리 풀 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_BYTE_POOL my_pool;
CHAR *name;
ULONG available;
ULONG fragments;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BYTE_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_byte_pool_info_get(&my_pool, &name,
  &available, &fragments,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>참고 항목

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_info_get"></a>tx_byte_pool_performance_info_get

바이트 풀 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_byte_pool_performance_info_get(
    TX_BYTE_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *fragments_searched, 
    ULONG *merges, 
    ULONG *splits,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

이 서비스는 지정된 메모리 바이트 풀에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. 

### <a name="parameters"></a>매개 변수

- **pool_ptr** 이전에 만든 메모리 바이트 풀에 대한 포인터입니다.
- **allocates** 이 풀에서 수행된 할당 요청 수 대상에 대한 포인터입니다.
- **releases** 이 풀에서 수행된 해제 요청 수 대상에 대한 포인터입니다.
- **fragments_searched** 이 풀에서 할당 요청 중 검색된 내부 메모리 조각 수 대상에 대한 포인터입니다.
- **merges** 이 풀에서 할당 요청 중 병합된 내부 메모리 블록 수 대상에 대한 포인터입니다.
- **splits** 이 풀에서 할당 요청 중 만들어진 내부 메모리 블록 분할(조각) 수 대상에 대한 포인터입니다.
- **suspensions** 이 풀의 스레드 할당 일시 중단 수 대상에 대한 포인터입니다.
- **timeouts** 이 풀의 할당 일시 중단 시간 제한 수 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 바이트 풀 성능 가져오기에 성공했습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 바이트 풀 포인터입니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_BYTE_POOL my_pool;
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created byte
pool. */
status = tx_byte_pool_performance_info_get(&my_pool,
  &fragments_searched,
  &merges, &splits,
  &allocates, &releases,
  &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```
### <a name="see-also"></a>참고 항목

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

바이트 풀 시스템 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_byte_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *fragments_searched, 
    ULONG *merges,
    ULONG *splits, 
    ULONG *suspensions, 
    ULONG *timeouts);
```
### <a name="description"></a>Description

이 서비스는 시스템의 모든 메모리 바이트 풀에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. 

### <a name="parameters"></a>매개 변수

- **allocates** 이 풀에서 수행된 할당 요청 수 대상에 대한 포인터입니다.
- **releases** 이 풀에서 수행된 해제 요청 수 대상에 대한 포인터입니다.
- **fragments_searched** 모든 바이트 풀에서 할당 요청 중 검색된 총 내부 메모리 조각 수 대상에 대한 포인터입니다.
- **merges** 모든 바이트 풀에서 할당 요청 중 병합된 총 내부 메모리 블록 수 대상에 대한 포인터입니다.
- **splits** 모든 바이트 풀에서 할당 요청 중 만들어진 총 내부 메모리 블록 분할(조각) 수 대상에 대한 포인터입니다.
- **suspensions** 모든 바이트 풀의 총 스레드 할당 일시 중단 수 대상에 대한 포인터입니다.
- **timeouts** 모든 바이트 풀의 총 할당 일시 중단 시간 제한 수 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 바이트 풀 성능 가져오기에 성공했습니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

 초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all byte pools in the
system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
  &merges, &splits, &allocates, &releases,
  &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

바이트 풀 일시 중단 목록의 우선 순위를 지정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a>Description

이 서비스는 일시 중단 목록 맨 앞에 있는, 이 풀의 메모리 때문에 일시 중단된 스레드를 가장 높은 우선 순위로 지정합니다. 다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.

### <a name="parameters"></a>매개 변수

- **pool_ptr** 메모리 풀 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메모리 풀 우선 순위 지정에 성공했습니다.
- **TX_POOL_ERROR**(0x02) 잘못된 메모리 풀 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_BYTE_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_byte_release call will wake up this thread,
if there is enough memory to satisfy its request. */
```

### <a name="see-also"></a>참고 항목

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_release

## <a name="tx_byte_release"></a>tx_byte_release

바이트를 메모리 풀로 다시 해제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 할당된 메모리 영역을 연결된 풀로 다시 해제합니다. 이 풀의 메모리를 기다리는 일시 중단된 스레드가 하나 이상인 경우 해당 메모리가 고갈될 때까지 또는 일시 중단된 스레드가 더 이상 없을 때까지 일시 중단된 각 스레드에 메모리가 제공되고 스레드는 다시 시작됩니다. 일시 중단된 스레드에 메모리를 할당하는 이 프로세스는 항상 일시 중단된 첫 번째 스레드부터 시작됩니다.

> [!IMPORTANT]
> 애플리케이션은 메모리 영역이 해제된 후에는 이 메모리 영역을 사용하지 않도록 해야 합니다.

### <a name="parameters"></a>매개 변수

- **memory_ptr** 이전에 할당된 메모리 영역에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메모리 해제에 성공했습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 메모리 영역 포인터입니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a>참고 항목

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize

## <a name="tx_event_flags_create"></a>tx_event_flags_create

이벤트 플래그 그룹을 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a>Description

이 서비스는 32개의 이벤트 플래그로 된 그룹을 만듭니다. 그룹에 있는 32개의 이벤트 플래그 모두 0으로 초기화됩니다. 각 이벤트 플래그는 단일 비트로 표시됩니다.

### <a name="parameters"></a>매개 변수

- **group_ptr** 이벤트 플래그 그룹 제어 블록에 대한 포인터입니다.
- **name_ptr** 이벤트 플래그 그룹 이름에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 이벤트 그룹 만들기에 성공했습니다.
- **TX_GROUP_ERROR**(0x06) 잘못된 이벤트 그룹 포인터입니다. 포인터가 **NULL** 이거나 이벤트 그룹을 이미 만들었습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a>참고 항목

- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_delete"></a>tx_event_flags_delete

이벤트 플래그 그룹을 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 이벤트 플래그 그룹을 삭제합니다. 이 그룹의 이벤트를 기다리는 일시 중단된 모든 스레드는 다시 시작되며 TX_DELETED 반환 상태가 지정됩니다.

>[!IMPORTANT]
> 애플리케이션은 이 이벤트 플래그 그룹을 삭제하기 전에 이 이벤트 플래그 그룹에 대한 설정 알림 콜백이 완료되었는지(또는 사용하지 않도록 설정되었는지) 확인해야 합니다. 또한 애플리케이션은 이후에는 삭제된 이벤트 플래그 그룹을 사용하지 않도록 해야 합니다.

### <a name="parameters"></a>매개 변수

- **group_ptr** 이전에 만든 이벤트 플래그 그룹에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 이벤트 플래그 그룹 삭제에 성공했습니다.
- **TX_GROUP_ERROR**(0x06) 잘못된 이벤트 플래그 그룹 포인터입니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Delete event flags group. Assume that the group has
already been created with a call to
tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
deleted. */
```

### <a name="see-also"></a>참고 항목

- tx_event_flags_create
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_get"></a>tx_event_flags_get

이벤트 플래그 그룹의 이벤트 플래그를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 이벤트 플래그 그룹의 이벤트 플래그를 검색합니다. 각 이벤트 플래그 그룹에는 32개의 이벤트 플래그가 포함되어 있습니다. 각 플래그는 단일 비트로 표시됩니다. 이 서비스는 입력 매개 변수를 통해 선택한 대로 다양한 이벤트 플래그 조합을 검색할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **group_ptr** <br>이전에 만든 이벤트 플래그 그룹에 대한 포인터입니다.
- **requested_flags** <br>요청된 이벤트 플래그를 나타내는 부호 없는 32비트 변수입니다.
- **get_option** <br>요청된 이벤트 플래그가 전체가 필요한지 일부가 필요한지 지정합니다. 유효한 선택 항목은 다음과 같습니다.

  - **TX_AND**(0x02)
  - **TX_AND_CLEAR**(0x03)
  - **TX_OR**(0x00)
  - **TX_OR_CLEAR**(0x01)

    TX_AND 또는 TX_AND_CLEAR를 선택하면 모든 이벤트 플래그가 그룹에 있어야 합니다. TX_OR 또는 TX_OR_CLEAR를 선택하면 모든 이벤트 플래그가 충족되는 것으로 지정됩니다. TX_AND_CLEAR 또는 TX_OR_CLEAR가 지정된 경우 요청을 충족시키는 이벤트 플래그를 지웁니다(0으로 설정함).

- **actual_flags_ptr** <br>검색된 이벤트 플래그가 배치되는 대상에 대한 포인터입니다. 가져온 실제 플래그는 요청되지 않은 플래그를 포함할 수 있습니다.
- **wait_option**  <br>선택한 이벤트 플래그가 설정되지 않은 경우의 서비스 작동 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **TX_NO_WAIT**(0x00000000) - TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다. 초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.
  - **TX_WAIT_FOREVER** 시간 제한 값(0xFFFFFFFF) - TX_WAIT_FOREVER를 선택하면 이벤트 플래그를 사용할 수 있을 때까지 호출 스레드가 무기한으로 일시 중단됩니다.
  - 시간 제한 값(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 이벤트 플래그를 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 이벤트 플래그 가져오기에 성공했습니다.
- **TX_DELETED**(0x01) 스레드가 일시 중단된 동안 이벤트 플래그 그룹이 삭제되었습니다.
- **TX_NO_EVENTS**(0x07) 서비스가 지정된 대기 시간 내에 지정된 이벤트를 가져오지 못했습니다.
- **TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.
- **TX_GROUP_ERROR**(0x06) 잘못된 이벤트 플래그 그룹 포인터입니다.
- **TX_PTR_ERROR**(0x03) 실제 이벤트 플래그에 대한 포인터가 잘못되었습니다.
- **TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.
- **TX_OPTION_ERROR**(0x08) 잘못된 get-option을 지정했습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG actual_events;
UINT status;

/* Request that event flags 0, 4, and 8 are all set. Also,
if they are set they should be cleared. If the event
flags are not set, this service suspends for a maximum of
20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
    TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
actual events obtained. */
```

**참고 항목**

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

이벤트 플래그 그룹에 대한 정보를 검색합니다.

**프로토타입**

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

**설명**

이 서비스는 지정된 이벤트 플래그 그룹에 대한 정보를 검색합니다.

**매개 변수**

- **group_ptr** 이벤트 플래그 그룹 제어 블록에 대한 포인터입니다.
- **name** 이벤트 플래그 그룹의 이름에 대한 포인터 대상에 대한 포인터입니다.
- **current_flags** 이벤트 플래그 그룹에서 현재 설정된 플래그 대상에 대한 포인터입니다.
- **first_suspended** 이 이벤트 플래그 그룹의 일시 중단 목록에 있는 첫 번째 스레드 포인터 대상에 대한 포인터입니다.
- **suspended_count** 이 이벤트 플래그 그룹에서 현재 일시 중단된 스레드 수 대상에 대한 포인터입니다.
- **next_group** 다음에 만들 이벤트 플래그 그룹 포인터 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 이벤트 그룹 정보 검색에 성공했습니다.
- **TX_GROUP_ERROR**(0x06) 잘못된 이벤트 그룹 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_EVENT_FLAGS_GROUP my_event_group;
CHAR *name;
ULONG current_flags;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_EVENT_FLAGS_GROUP *next_group;
UINT status;

/* Retrieve information about the previously created
event flags group "my_event_group." */
status = tx_event_flags_info_get(&my_event_group, &name,
    &current_flags,
    &first_suspended, &suspended_count,
    &next_group);
/* If status equals TX_SUCCESS, the information requested is
valid. */
```
**참고 항목**

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

이벤트 플래그 그룹 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

이 서비스는 지정된 이벤트 플래그 그룹에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. 

### <a name="parameters"></a>매개 변수

- **group_ptr** 이전에 만든 이벤트 플래그 그룹에 대한 포인터입니다.
- **sets** 이 그룹에서 수행된 이벤트 플래그 설정 요청 수 대상에 대한 포인터입니다.
- **gets** 이 그룹에서 수행된 이벤트 플래그 가져오기 요청 수 대상에 대한 포인터입니다.
- **suspensions** 이 그룹의 스레드 이벤트 플래그 가져오기 일시 중단 수 대상에 대한 포인터입니다.
- **timeouts** 이 그룹의 이벤트 플래그 가져오기 일시 중단 시간 제한 수 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 이벤트 플래그 그룹 성능 가져오기에 성공했습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 이벤트 플래그 그룹 포인터입니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_EVENT_FLAGS_GROUP my_event_flag_group;
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created event
flag group. */
status = tx_event_flags_performance_info_get(&my_event_flag_group,
    &sets, &gets, &suspensions,
    &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

성능 시스템 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

이 서비스는 시스템의 모든 이벤트 플래그 그룹에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. 

### <a name="parameters"></a>매개 변수

- **sets** 모든 그룹에서 수행된 총 이벤트 플래그 설정 요청 수 대상에 대한 포인터입니다.
- **gets** 모든 그룹에서 수행된 총 이벤트 플래그 가져오기 요청 수 대상에 대한 포인터입니다.
- **suspensions** 모든 그룹의 총 스레드 이벤트 플래그 가져오기 일시 중단 수 대상에 대한 포인터입니다.
- **timeouts** 모든 그룹의 총 이벤트 플래그 가져오기 일시 중단 시간 제한 수 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 이벤트 플래그 시스템 성능 가져오기에 성공했습니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="example"></a>예제

```c
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created event
flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_set"></a>tx_event_flags_set

이벤트 플래그 그룹에서 이벤트 플래그를 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 set-option에 따라 이벤트 플래그 그룹에서 이벤트 플래그를 설정하거나 지웁니다. 이제 해당 이벤트 플래그 요청이 충족된 모든 일시 중단된 스레드가 다시 시작됩니다.

### <a name="parameters"></a>매개 변수

- **group_ptr** <br>이전에 만든 이벤트 플래그 그룹 제어 블록에 대한 포인터입니다.
- **flags_to_set** <br>선택한 설정 옵션에 따라 설정하거나 지울 이벤트 플래그를 지정합니다.
- **set_option** <br>지정된 이벤트 플래그를 그룹의 현재 이벤트 플래그에 AND로 연결할지 또는 OR로 연결할지 지정합니다. 유효한 선택 항목은 다음과 같습니다.
  - **TX_AND**(0x02)
  - **TX_OR**(0x00)

  TX_AND를 선택하면 지정된 이벤트 플래그가 그룹의 현재 이벤트 플래그에 **AND** 로 연결되도록 지정합니다. 이 옵션은 그룹의 이벤트 플래그를 지우는 데 사용되는 경우가 많습니다. 그러지 않고 TX_OR이 지정되면 지정된 이벤트 플래그가 그룹의 현재 이벤트에 **OR** 로 연결됩니다.

### <a name="return-values"></a>반환 값
- **TX_SUCCESS**(0x00) 이벤트 플래그 설정에 성공했습니다.
- **TX_GROUP_ERROR**(0x06) 잘못된 이벤트 플래그 그룹 포인터입니다.
- **TX_OPTION_ERROR**(0x08) 잘못된 set-option이 지정되었습니다.

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Set event flags 0, 4, and 8. */
status = tx_event_flags_set(&my_event_flags_group,
    0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
set and any suspended thread whose request was satisfied
has been resumed. */
```

### <a name="see-also"></a>참고 항목

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set_notify

## <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

이벤트 플래그가 설정되면 애플리케이션에 알립니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a>Description

이 서비스는 지정된 이벤트 플래그 그룹에 하나 이상의 이벤트 플래그가 설정될 때마다 호출되는 알림 콜백 함수를 등록합니다. 알림 콜백 처리는 애플리케이션에 의해 정의됩니다.

### <a name="parameters"></a>매개 변수
- **group_ptr** 이전에 만든 이벤트 플래그 그룹에 대한 포인터입니다.
- **events_set_notify** 애플리케이션의 이벤트 플래그 설정 알림 기능에 대한 포인터입니다. 이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 이벤트 플래그 설정 알림 등록에 성공했습니다.
- **TX_GROUP_ERROR**(0x06) 잘못된 이벤트 플래그 그룹 포인터입니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 시스템이 알림 기능을 사용하지 않도록 설정하여 컴파일되었습니다.

### <a name="example"></a>예제

```c
TX_EVENT_FLAGS_GROUP my_group;

/* Register the "my_event_flags_set_notify" function for monitoring
event flags set in the event flags group "my_group." */
status = tx_event_flags_set_notify(&my_group, my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
was successfully registered. */
void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)

/* One or more event flags was set in this group! */
```

### <a name="see-also"></a>참고 항목

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set

## <a name="tx_interrupt_control"></a>tx_interrupt_control

인터럽트를 사용하거나 사용하지 않도록 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a>Description

이 서비스는 입력 매개 변수 *new_posture* 를 통해 지정된 대로 인터럽트를 사용하거나 사용하지 않도록 설정합니다.

> [!NOTE]
> 애플리케이션 스레드에서 이 서비스를 호출하는 경우 인터럽트 상태는 해당 스레드 컨텍스트에 포함된 상태로 유지됩니다. 예를 들어 스레드가 이 루틴을 호출하여 인터럽트를 사용하지 않도록 설정한 후 일시 중단되면 다시 시작되는 경우 인터럽트는 다시 사용하지 않도록 설정됩니다.

> [!WARNING]
> 초기화 중에는 이 서비스를 사용하여 인터럽트를 사용하도록 설정하지 않는 것이 좋습니다. 사용하면 예기치 않은 결과가 발생할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **new_posture** 이 매개 변수는 인터럽트가 사용하지 않도록 설정되는지 사용하도록 설정되는지를 지정합니다. 올바른 값에는 **TX_INT_DISABLE** 및 **TX_INT_ENABLE** 이 포함됩니다. 이러한 매개 변수의 실제 값은 포트에 특정됩니다. 또한 일부 처리 아키텍처는 추가 인터럽트 사용 안 함 상태를 지원할 수도 있습니다.

### <a name="return-values"></a>반환 값
- **previous posture** 이 서비스는 이전 인터럽트 상태를 호출자에게 반환합니다. 이렇게 하면 서비스 사용자가 인터럽트를 사용하지 않도록 설정한 후 이전 상태를 복원할 수 있습니다.

### <a name="allowed-from"></a>허용 위치

스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a>참고 항목

None

## <a name="tx_mutex_create"></a>tx_mutex_create

상호 배제 뮤텍스를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a>Description

이 서비스는 리소스 보호를 위해 스레드 간 상호 배제 뮤텍스를 만듭니다.

### <a name="parameters"></a>매개 변수

- **mutex_ptr** 뮤텍스 제어 블록에 대한 포인터입니다.
- **name_ptr** 뮤텍스 이름에 대한 포인터입니다.
- **priority_inherit** 이 뮤텍스가 우선 순위 상속을 지원하는지 여부를 지정합니다. 이 값이 TX_INHERIT인 경우 우선 순위 상속이 지원됩니다. 하지만 TX_NO_INHERIT이 지정되면 이 뮤텍스에서 우선 순위 상속이 지원되지 않습니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 뮤텍스 만들기에 성공했습니다.
- **TX_MUTEX_ERROR**(0x1C) 잘못된 뮤텍스 포인터입니다. 포인터가 NULL이거나 뮤텍스가 이미 만들어져 있습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.
- **TX_INHERIT_ERROR**(0x1F) 우선 순위 상속 매개 변수가 잘못되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_MUTEX my_mutex;
UINT status;

/* Create a mutex to provide protection over a
common resource. */
status = tx_mutex_create(&my_mutex,"my_mutex_name",
    TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
use. */
```

### <a name="see-also"></a>참고 항목

- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_delete"></a>tx_mutex_delete

상호 배제 뮤텍스를 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 뮤텍스를 삭제합니다. 뮤텍스를 기다리는 일시 중단된 모든 스레드는 다시 시작되며 **TX_DELETED** 반환 상태가 지정됩니다.

> [!NOTE]
> 애플리케이션은 삭제된 뮤텍스를 사용하지 않도록 해야 합니다.

### <a name="parameters"></a>매개 변수

- **mutex_ptr** 이전에 만든 뮤텍스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 뮤텍스 삭제에 성공했습니다.
- **TX_MUTEX_ERROR**(0x1C) 잘못된 뮤텍스 포인터입니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a>참고 항목

- tx_mutex_create
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_get"></a>tx_mutex_get

뮤텍스 소유권을 얻습니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 뮤텍스의 배타적 소유권을 얻으려고 합니다. 호출 스레드가 뮤텍스를 이미 소유하고 있으면 내부 카운터가 증분되고 성공 상태가 반환됩니다.

다른 스레드에서 뮤텍스를 소유하지만 이 스레드의 우선 순위가 더 높으며 뮤텍스를 만들 때 우선 순위 상속이 지정된 경우, 우선 순위가 더 낮은 스레드의 우선 순위가 호출 스레드의 우선 순위로 일시적으로 높아집니다.

> [!NOTE]
> priorityinheritance가 지정된 뮤텍스를 소유하는 우선 순위가 더 낮은 스레드의 우선 순위는 뮤텍스 소유 중 외부 스레드에 의해 수정되면 안 됩니다.

### <a name="parameters"></a>매개 변수

- **mutex_ptr**   <br>이전에 만든 뮤텍스에 대한 포인터입니다.
- **wait_option** <br>다른 스레드가 뮤텍스를 이미 소유하고 있는 경우 서비스 작동 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **TX_NO_WAIT**(0x00000000) - TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다. 초기화에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.
  - **TX_WAIT_FOREVER** 시간 제한 값(0xFFFFFFFF) - **TX_WAIT_FOREVER** 를 선택하면 뮤텍스를 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.
  - 시간 제한 값(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 뮤텍스를 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 뮤텍스 가져오기 작업에 성공했습니다.
- **TX_DELETED**(0x01) 스레드가 일시 중단된 동안 뮤텍스가 삭제되었습니다.
- **TX_NOT_AVAILABLE**(0x1D) 서비스가 지정된 대기 시간 내에 뮤텍스 소유권을 가져오지 못했습니다.
- **TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.
- **TX_MUTEX_ERROR**(0x1C) 잘못된 뮤텍스 포인터입니다.
- **TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a>참고 항목

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_info_get"></a>tx_mutex_info_get

뮤텍스에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_mutex_info_get(
    TX_MUTEX *mutex_ptr, 
    CHAR **name,
    ULONG *count, 
    TX_THREAD **owner,
    TX_THREAD **first_suspended,
    ULONG *suspended_count, 
    TX_MUTEX **next_mutex);
```

### <a name="description"></a>Description

이 서비스는 지정된 뮤텍스의 정보를 검색합니다.

### <a name="parameters"></a>매개 변수

- **mutex_ptr** 뮤텍스 제어 블록에 대한 포인터입니다.
- **name** 뮤텍스 이름에 대한 포인터 대상에 대한 포인터입니다.
- **count** 뮤텍스 소유권 수 대상에 대한 포인터입니다.
- **owner** 소유 스레드 포인터 대상에 대한 포인터입니다.
- **first_suspended** 이 뮤텍스의 일시 중단 목록에 있는 첫 번째 스레드에 대한 포인터 대상에 대한 포인터입니다.
- **suspended_count** 이 뮤텍스에서 현재 일시 중단된 스레드 수 대상에 대한 포인터입니다.
- **next_mutex** 다음에 만들 뮤텍스 포인터 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 뮤텍스 정보 검색에 성공했습니다.
- **TX_MUTEX_ERROR**(0x1C) 잘못된 뮤텍스 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

**예제**

```c
TX_MUTEX my_mutex;
CHAR *name;
ULONG count;
TX_THREAD *owner;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_MUTEX *next_mutex;
UINT status;

/* Retrieve information about the previously created
mutex "my_mutex." */
status = tx_mutex_info_get(&my_mutex, &name,
    &count, &owner,
    &first_suspended, &suspended_count,
    &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>참고 항목

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

뮤텍스 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_mutex_performance_info_get(
    TX_MUTEX *mutex_ptr, 
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a>Description

이 서비스는 지정된 뮤텍스에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.

### <a name="parameters"></a>매개 변수

- **mutex_ptr** 이전에 만든 뮤텍스에 대한 포인터입니다.
- **puts** 이 뮤텍스에서 수행된 넣기 요청 수 대상에 대한 포인터입니다.
- **gets** 이 뮤텍스에서 수행된 가져오기 요청 수 대상에 대한 포인터입니다.
- **suspensions** 이 뮤텍스의 스레드 뮤텍스 가져오기 일시 중단 수 대상에 대한 포인터입니다.
- **timeouts** 이 뮤텍스의 뮤텍스 가져오기 일시 중단 시간 제한 수 대상에 대한 포인터입니다.
- **inversions** 이 뮤텍스의 스레드 우선 순위 반전 수 대상에 대한 포인터입니다.
- **inheritances** 이 뮤텍스의 스레드 우선 순위 상속 작업 수 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 뮤텍스 성능 가져오기에 성공했습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 뮤텍스 포인터입니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_MUTEX my_mutex;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on the previously created
mutex. */
status = tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
    &suspensions, &timeouts, &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

뮤텍스 시스템 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a>Description

이 서비스는 시스템의 모든 뮤텍스에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_MUTEX_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. 

### <a name="parameters"></a>매개 변수

- **puts** 모든 뮤텍스에서 수행된 총 넣기 요청 수 대상에 대한 포인터입니다.
- **gets** 모든 뮤텍스에서 수행된 총 가져오기 요청 수 대상에 대한 포인터입니다.
- **suspensions** 모든 뮤텍스의 총 스레드 뮤텍스 가져오기 일시 중단 수 대상에 대한 포인터입니다.
- **timeouts** 모든 뮤텍스의 총 뮤텍스 가져오기 일시 중단 시간 제한 수 대상에 대한 포인터입니다.
- **inversions** 모든 뮤텍스의 총 스레드 우선 순위 반전 수 대상에 대한 포인터입니다.
- **inheritances** 모든 뮤텍스의 총 스레드 우선 순위 상속 작업 수 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 뮤텍스 시스템 성능 가져오기에 성공했습니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on all previously created
mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts,
    &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

뮤텍스 일시 중단 목록의 우선 순위를 지정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Description

이 서비스는 일시 중단 목록 맨 앞에 있는, 뮤텍스 소유권 때문에 일시 중단된 스레드를 가장 높은 우선 순위로 지정합니다. 다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.

### <a name="parameters"></a>매개 변수

- **mutex_ptr** 이전에 만든 뮤텍스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 뮤텍스 우선 순위 지정에 성공했습니다.
- **TX_MUTEX_ERROR**(0x1C) 잘못된 뮤텍스 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_MUTEX my_mutex;
UINT status;

/* Ensure that the highest priority thread will receive
ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_mutex_put call that releases ownership of the
mutex will give ownership to this thread and wake it
up. */
```

### <a name="see-also"></a>참고 항목

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_put

## <a name="tx_mutex_put"></a>tx_mutex_put

뮤텍스 소유권을 해제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 뮤텍스의 소유권 수를 줄입니다. 소유권 수가 0이면 뮤텍스를 사용할 수 있게 됩니다.

> [!NOTE]
> 뮤텍스를 만들 때 우선 순위 상속을 선택한 경우 처음 뮤텍스 소유권을 얻었을 때의 우선 순위로 해제 스레드 우선 순위가 복원됩니다. 뮤텍스 소유 기간 동안 해제 스레드에 수행된 다른 모든 우선 순위 변경은 실행 취소될 수도 있습니다.

### <a name="parameters"></a>매개 변수
- mutex_ptr 이전에 만든 뮤텍스에 대한 포인터입니다.

### <a name="return-values"></a>반환 값
- **TX_SUCCESS**(0x00) 뮤텍스 해제에 성공했습니다.
- **TX_NOT_OWNED**(0x1E) 호출자가 뮤텍스를 소유하고 있지 않습니다.
- **TX_MUTEX_ERROR**(0x1C) 뮤텍스에 대한 포인터가 잘못되었습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a>참고 항목

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize

## <a name="tx_queue_create"></a>tx_queue_create

메시지 큐를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a>Description

이 서비스는 일반적으로 스레드 간 통신에 사용되는 메시지 큐를 만듭니다. 총 메시지 수는 지정된 메시지 크기와 큐의 총 바이트 수로 계산합니다.

> [!NOTE]
> 큐의 메모리 영역에 지정된 총 바이트 수를 지정된 메시지 크기로 균등하게 나눌 수 없는 경우 메모리 영역의 나머지 바이트는 사용되지 않습니다.

### <a name="parameters"></a>매개 변수

- **queue_ptr** 메시지 큐 제어 블록에 대한 포인터입니다.
- **name_ptr** 메시지 큐 이름에 대한 포인터입니다.
- **message_size** 큐에 있는 각 메시지의 크기를 지정합니다. 메시지 크기 범위는 1개의 32비트 단어부터 16개의 32비트 단어입니다. 유효한 메시지 크기 옵션은 1에서 16(포함) 사이의 숫자 값입니다.
- **queue_start** 메시지 큐의 시작 주소입니다. 시작 주소는 ULONG 데이터 형식의 크기에 맞춰야 합니다.
- **queue_size** 메시지 큐에 사용할 수 있는 총 바이트 수입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메시지 큐 만들기에 성공했습니다.
- **TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다. 포인터가 NULL이거나 큐가 이미 만들어져 있습니다.
- **TX_PTR_ERROR**(0x03) 메시지 큐의 시작 주소가 잘못되었습니다.
- **TX_SIZE_ERROR**(0x05) 메시지 큐의 크기가 잘못되었습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_QUEUE my_queue;
UINT status;

/* Create a message queue whose total size is 2000 bytes
starting at address 0x300000. Each message in this
queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
    4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
for storing 125 messages (2000 bytes/ 16 bytes per
message). */
```

### <a name="see-also"></a>참고 항목

- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_delete"></a>tx_queue_delete

메시지 큐를 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 메시지 큐를 삭제합니다. 이 큐의 메시지 기다리는 일시 중단된 모든 스레드는 다시 시작되며 TX_DELETED 반환 상태가 지정됩니다.

>[!IMPORTANT]
> 애플리케이션은 이 큐를 삭제하기 전에 이 큐에 대한 모든 설정 알림 콜백이 완료되었는지(또는 사용하지 않도록 설정되었는지) 확인해야 합니다. 또한 애플리케이션은 이후에는 삭제된 큐를 사용하지 않도록 해야 합니다. <br><br>애플리케이션은 또한 이 서비스가 완료된 후 사용할 수 있는 큐와 연결된 메모리 영역을 관리해야 합니다.

### <a name="parameters"></a>매개 변수

- **queue_ptr** 이전에 만든 메시지 큐에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메시지 큐 삭제에 성공했습니다.
- **TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_QUEUE my_queue;
UINT status;

/* Delete entire message queue. Assume that the queue
has already been created with a call to
tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
deleted. */
```

### <a name="see-also"></a>참고 항목

- tx_queue_create
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_flush"></a>tx_queue_flush

메시지 큐의 메시지를 비웁니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 메시지 큐에 저장된 모든 메시지를 삭제합니다.

메시지 큐가 가득 차면 모든 일시 중단된 스레드의 메시지가 삭제됩니다. 일시 중단된 각 스레드는 메시지 송신이 성공했음을 나타내는 반환 상태로 다시 시작됩니다. 큐가 비어 있으면 이 서비스는 아무 작업도 수행하지 않습니다.

### <a name="parameters"></a>매개 변수

- **queue_ptr** 이전에 만든 메시지 큐에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메시지 큐 플러시에 성공했습니다.
- **TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_QUEUE my_queue;
UINT status;

/* Flush out all pending messages in the specified message
queue. Assume that the queue has already been created
with a call to tx_queue_create. */
status = tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
empty. */
```

### <a name="see-also"></a>참고 항목

- tx_queue_create
- tx_queue_delete
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_front_send"></a>tx_queue_front_send

메시지를 큐 맨 앞으로 송신합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 메시지를 지정된 메시지 큐의 맨 앞 위치로 송신합니다. 메시지는 원본 포인터로 지정된 메모리 영역의 큐 맨 앞으로 **복사됩니다**.

### <a name="parameters"></a>매개 변수

- **queue_ptr** <br>메시지 큐 제어 블록에 대한 포인터입니다.
- **source_ptr** <br>메시지에 대한 포인터입니다.
- **wait_option**  <br>메시지 큐가 가득 찬 경우의 서비스 작동 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **TX_NO_WAIT**(0x00000000) - TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다. 초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.
  - **TX_WAIT_FOREVER**(0xFFFFFFFF) - TX_WAIT_FOREVER를 선택하면 큐에 공간이 있을 때까지 호출 스레드가 무기한으로 일시 중단됩니다.
  - 시간 제한 값(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 큐의 공간을 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메시지 송신에 성공했습니다.
- **TX_DELETED**(0x01) 스레드가 일시 중단된 동안 메시지 큐가 삭제되었습니다.
- **TX_QUEUE_FULL**(0x0B) 지정된 대기 시간 중 큐가 가득 찼으므로 서비스에서 메시지를 송신할 수 없습니다.
- **TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.
- **TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.
- **TX_PTR_ERROR**(0x03) 잘못된 메시지 원본 포인터입니다.
- **TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to the front of "my_queue." Return
immediately, regardless of success. This wait
option is used for calls from initialization, timers,
and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
    TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
of the specified queue. */
```

### <a name="see-also"></a>참고 항목

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_info_get"></a>tx_queue_info_get

큐에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_queue_info_get(
    TX_QUEUE *queue_ptr, 
    CHAR **name,
    ULONG *enqueued, 
    ULONG *available_storage
    TX_THREAD **first_suspended, 
    ULONG *suspended_count,
    TX_QUEUE **next_queue);
```

### <a name="description"></a>Description

이 서비스는 지정된 메시지 큐에 대한 정보를 검색합니다.

### <a name="parameters"></a>매개 변수

- **queue_ptr** 이전에 만든 메시지 큐에 대한 포인터입니다.
- **name** 큐 이름에 대한 포인터 대상에 대한 포인터입니다.
- **enqueued** 현재 큐에 있는 메시지 수 대상에 대한 포인터입니다.
- **available_storage** 큐에 현재 공간이 있는 메시지 수 대상에 대한 포인터입니다.
- **first_suspended** 이 큐의 일시 중단 목록에 있는 첫 번째 스레드에 대한 포인터 대상에 대한 포인터입니다.
- **suspended_count** 이 큐에서 현재 일시 중단된 스레드 수 대상에 대한 포인터입니다.
- **next_queue** 다음에 만들 큐 포인터 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 큐 정보 가져오기에 성공했습니다.
- **TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_QUEUE my_queue;
CHAR *name;
ULONG enqueued;
ULONG available_storage;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_QUEUE *next_queue;
UINT status;

/* Retrieve information about the previously created
message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
    &enqueued, &available_storage,
    &first_suspended, &suspended_count,
    &next_queue);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>참고 항목

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

큐 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_queue_performance_info_get(
    TX_QUEUE *queue_ptr,
    ULONG *messages_sent, 
    ULONG *messages_received,
    ULONG *empty_suspensions, 
    ULONG *full_suspensions,
    ULONG *full_errors, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

이 서비스는 지정된 큐에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.

### <a name="parameters"></a>매개 변수

- **queue_ptr** 이전에 만든 큐에 대한 포인터입니다.
- **messages_sent** 이 큐에서 수행된 송신 요청 수 대상에 대한 포인터입니다.
- **messages_received** 이 큐에서 수행된 수신 요청 수 대상에 대한 포인터입니다.
- **empty_suspensions** 이 큐의 큐 비우기 일시 중단 수 대상에 대한 포인터입니다.
- **full_suspensions** 이 큐의 큐 채우기 일시 중단 수 대상에 대한 포인터입니다.
- **full_errors** 이 큐의 큐 채우기 오류 수 대상에 대한 포인터입니다.
- **timeouts** 이 큐의 스레드 일시 중단 시간 제한 수 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 큐 성능 가져오기에 성공했습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 큐 포인터입니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_QUEUE my_queue;
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on the previously created
queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

큐 시스템 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a>Description

이 서비스는 시스템의 모든 큐에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.

### <a name="parameters"></a>매개 변수

- **messages_sent** 모든 큐에서 수행된 총 송신 요청 수 대상에 대한 포인터입니다.
- **messages_received** 모든 큐에서 수행된 총 수신 요청 수 대상에 대한 포인터입니다.
- **empty_suspensions** 모든 큐의 총 큐 비우기 일시 중단 수 대상에 대한 포인터입니다.
- **full_suspensions** 모든 큐의 총 큐 채우기 일시 중단 수 대상에 대한 포인터입니다.
- **full_errors** 모든 큐의 총 큐 채우기 오류 수 대상에 대한 포인터입니다.
- **timeouts** 모든 큐의 총 스레드 일시 중단 시간 제한 수 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

**반환 값**

- **TX_SUCCESS**(0x00) 큐 시스템 성능 가져오기에 성공했습니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on all previously created
queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_prioritize"></a>tx_queue_prioritize

큐 일시 중단 목록의 우선 순위를 지정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Description

이 서비스는 일시 중단 목록 맨 앞에 있는, 이 큐의 메시지(또는 메시지 배치) 때문에 일시 중단된 스레드를 가장 높은 우선 순위로 지정합니다.

다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.

### <a name="parameters"></a>매개 변수

- **queue_ptr** 이전에 만든 메시지 큐에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 큐 우선 순위 지정에 성공했습니다.
- **TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_QUEUE my_queue;
UINT status;

/* Ensure that the highest priority thread will receive
the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_queue_send or tx_queue_front_send call made
to this queue will wake up this thread. */
```

### <a name="see-also"></a>참고 항목

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_receive"></a>tx_queue_receive

메시지 큐에서 메시지를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 메시지 큐에서 메시지를 검색합니다. 검색된 메시지는 큐로부터 대상 포인터로 지정된 메모리 영역으로 **복사됩니다**. 그러면 해당 메시지는 큐에서 제거됩니다.

> [!IMPORTANT]
> 지정된 대상 메모리 영역은 메시지를 저장할 수 있을 만큼 충분히 커야 합니다. 즉, **destination_ptr** __로 가리키는 메시지 대상은 이 큐의 메시지 크기 이상이어야 합니다. * 그러지 않고 대상이 충분히 크지 않으면 다음 메모리 영역에서 메모리 손상이 발생합니다.

### <a name="parameters"></a>매개 변수

- **queue_ptr** <br>이전에 만든 메시지 큐에 대한 포인터입니다.
- **destination_ptr** <br>메시지를 복사할 위치입니다.
- **wait_option** <br>메시지 큐가 비어 있는 경우의 서비스 작동 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **TX_NO_WAIT**(0x00000000) - TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다. 초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.
  - **TX_WAIT_FOREVER**(0xFFFFFFFF) - TX_WAIT_FOREVER를 선택하면 메시지를 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.
  - 시간 제한 값(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 메시지를 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메시지 검색에 성공했습니다.
- **TX_DELETED**(0x01) 스레드가 일시 중단된 동안 메시지 큐가 삭제되었습니다.
- **TX_QUEUE_EMPTY**(0x0A) 지정된 대기 시간 동안 큐가 비어 있어서 서비스가 메시지를 검색하지 못했습니다.
- **TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.
- **TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.
- **TX_PTR_ERROR**(0x03) 메시지 대상 포인터가 잘못되었습니다.
- **TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
empty, suspend until a message is present. Note that
this suspension is only possible from application
threads. */
status = tx_queue_receive(&my_queue, my_message,
    TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
"my_message." */
```

### <a name="see-also"></a>참고 항목

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_send"></a>tx_queue_send

메시지를 메시지 큐로 송신합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 메시지를 지정된 메시지 큐로 송신합니다. 송신된 메시지는 원본 포인터로 지정된 메모리 영역에서 큐로 **복사됩니다**.

### <a name="parameters"></a>매개 변수
- **queue_ptr** <br>이전에 만든 메시지 큐에 대한 포인터입니다.
- **source_ptr** <br>메시지에 대한 포인터입니다.
- **wait_option** <br>메시지 큐가 가득 찬 경우의 서비스 작동 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **TX_NO_WAIT**(0x00000000) - TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다. 초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.
  - **TX_WAIT_FOREVER**(0xFFFFFFFF) - TX_WAIT_FOREVER를 선택하면 큐에 공간이 있을 때까지 호출 스레드가 무기한으로 일시 중단됩니다.
  - 시간 제한 값(0x00000001-0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 큐의 공간을 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 메시지 송신에 성공했습니다.
- **TX_DELETED**(0x01) 스레드가 일시 중단된 동안 메시지 큐가 삭제되었습니다.
- **TX_QUEUE_FULL**(0x0B) 지정된 대기 시간 중 큐가 가득 찼으므로 서비스에서 메시지를 송신할 수 없습니다.
- **TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.
- **TX_QUEUE_ERROR**(0x09) 잘못된 메시지 큐 포인터입니다.
- **TX_PTR_ERROR**(0x03) 잘못된 메시지 원본 포인터입니다.
- **TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
regardless of success. This wait option is used for
calls from initialization, timers, and ISRs. */
status = tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
queue. */
```

**참고 항목**

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send_notify

## <a name="tx_queue_send_notify"></a>tx_queue_send_notify

메시지가 큐로 송신되면 애플리케이션에 알립니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a>Description

이 서비스는 메시지가 지정된 큐로 송신될 때마다 호출되는 알림 콜백 함수를 등록합니다. 알림 콜백 처리는 애플리케이션에 의해 정의됩니다.

>[!NOTE]
> 애플리케이션의 큐 송신 알림 콜백은 일시 중단 옵션을 사용하여 ThreadX API를 호출할 수 없습니다.

### <a name="parameters"></a>매개 변수

- **queue_ptr** 이전에 만든 큐에 대한 포인터입니다.
- **queue_send_notify** 애플리케이션 큐 송신 알림 함수에 대한 포인터입니다. 이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 큐 송신 알림 등록에 성공했습니다.
- **TX_QUEUE_ERROR**(0x09) 잘못된 큐 포인터입니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 시스템이 알림 기능을 사용하지 않도록 설정하여 컴파일되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_QUEUE my_queue;
/* Register the "my_queue_send_notify" function for monitoring
messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
    /* A message was just sent to this queue! */
}
```

### <a name="see-also"></a>참고 항목

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send

## <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

최댓값이 있는 가산 세마포에 인스턴스를 배치합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a>Description

이 서비스는 지정된 가산 세마포에 인스턴스를 배치합니다. 실제로는 가산 세마포가 1씩 증가합니다. 가산 세마포의 현재 값이 지정된 최댓값 이상인 경우 인스턴스가 배치되지 않으며 TX_CEILING_EXCEEDED 오류가 반환됩니다.

### <a name="parameters"></a>매개 변수

- **semaphore_ptr** 이전에 만든 세마포에 대한 포인터입니다.
- **ceiling** 이 세마포에 허용되는 최대 한도입니다(유효한 값 범위는 1-0xFFFFFFFF임).

### <a name="return-values"></a>반환 값

- **TX_SUCCESS(0x00)** 세마포 최댓값 넣기에 성공했습니다.
- **TX_CEILING_EXCEEDED**(0x21) 넣기 요청이 최댓값을 초과합니다.
- **TX_INVALID_CEILING**(0x22) 최댓값에 잘못된 값인 0이 제공되었습니다.
- **TX_SEMAPHORE_ERROR**(0x0C) 잘못된 세마포 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a>참고 항목

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_create"></a>tx_semaphore_create

가산 세마포를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a>Description

이 서비스는 스레드 간 동기화에 사용되는 가산 세마포를 만듭니다. 초기 세마포 개수는 입력 매개 변수로 지정됩니다.

### <a name="parameters"></a>매개 변수

- **semaphore_ptr** 세마포 제어 블록에 대한 포인터입니다.
- **name_ptr** 세마포 이름에 대한 포인터입니다.
- **initial_count** 이 세마포의 초기 개수를 지정합니다. 올바른 값 범위는 0x00000000-0xFFFFFFFF입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 세마포 만들기에 성공했습니다.
- **TX_SEMAPHORE_ERROR**(0x0C) 잘못된 세마포 포인터입니다. 포인터가 NULL이거나 세마포가 이미 만들어졌습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Create a counting semaphore whose initial value is 1.
This is typically the technique used to make a binary
semaphore. Binary semaphores are used to provide
protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
    "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
use. */
```

### <a name="see-also"></a>참고 항목

- tx_semaphore_ceiling_put
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_delete"></a>tx_semaphore_delete

가산 세마포를 삭제합니다.

### <a name="prototype"></a>프로토타입
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 가산 세마포를 삭제합니다. 세마포 인스턴스를 기다리는 일시 중단된 모든 스레드는 다시 시작되며 TX_DELETED 반환 상태가 지정됩니다.

> [!IMPORTANT]
> 애플리케이션은 이 세마포를 삭제하기 전에 이 세마포에 대한 모든 넣기 알림 콜백이 완료되었는지(또는 사용하지 않도록 설정되었는지) 확인해야 합니다. 또한 애플리케이션은 이후에는 삭제된 세마포를 사용하지 않도록 해야 합니다.

### <a name="parameters"></a>매개 변수

- **semaphore_ptr** 이전에 만든 세마포에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 가산 세마포 삭제에 성공했습니다.
- **TX_SEMAPHORE_ERROR**(0x0C) 잘못된 가산 세마포 포인터입니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

**참고 항목**

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_get"></a>tx_semaphore_get

가산 세마포에서 인스턴스를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

이 서비스는 지정된 가산 세마포에서 인스턴스(단일 개수)를 검색합니다. 결과적으로 지정된 세마포 개수가 1씩 감소합니다.

### <a name="parameters"></a>매개 변수

- **semaphore_ptr** <br>이전에 만든 가산 세마포에 대한 포인터입니다.
- **wait_option** <br>사용할 수 있는 세마포 인스턴스가 없는 경우(세마포 개수가 0인 경우)의 서비스 작동 방식을 정의합니다. 대기 옵션은 다음과 같이 정의됩니다.
  - **TX_NO_WAIT**(0x00000000) - TX_NO_WAIT를 선택하면 성공 여부에 관계없이 이 서비스에서 즉시 반환합니다. 초기화, 타이머 또는 ISR과 같은 비스레드에서 서비스를 호출하는 경우 유일하게 유효한 옵션입니다.
  - **TX_WAIT_FOREVER**(0xFFFFFFFF) - TX_WAIT_FOREVER를 선택하면 세마포 인스턴스를 사용할 수 있게 될 때까지 호출 스레드가 무기한으로 일시 중단됩니다.
  - 시간 제한 값(0x00000001 through 0xFFFFFFFE) - 숫자 값(1-0xFFFFFFFE)을 선택하면 세마포 인스턴스를 기다리는 동안 일시 중단된 상태로 유지되는 최대 타이머 틱 수가 지정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 세마포 인스턴스 검색에 성공했습니다.
- **TX_DELETED**(0x01) 스레드가 일시 중단된 동안 가산 세마포가 삭제되었습니다.
- **TX_NO_INSTANCE**(0x0D) 서비스가 가산 세마포 인스턴스를 검색하지 못했습니다(지정된 대기 시간에 세마포 개수가 0임).
- **TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.
- **TX_SEMAPHORE_ERROR**(0x0C) 잘못된 가산 세마포 포인터입니다.
- **TX_WAIT_ERROR**(0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Get a semaphore instance from the semaphore
"my_semaphore." If the semaphore count is zero,
suspend until an instance becomes available.
Note that this suspension is only possible from
application threads. */
status = tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
an instance of the semaphore. */
```

### <a name="see-also"></a>참고 항목

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semahore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

세마포에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a>Description

이 서비스는 지정된 세마포에 대한 정보를 검색합니다.

### <a name="parameters"></a>매개 변수

- **semaphore_ptr** 세마포 제어 블록에 대한 포인터입니다.
- **name** 세마포 이름에 대한 포인터의 대상에 대한 포인터입니다.
- **current_value** 현재 세마포 수 대상에 대한 포인터입니다.
- **first_suspended** 이 세마포의 일시 중단 목록에 있는 첫 번째 스레드에 대한 포인터 대상에 대한 포인터입니다.
- **suspended_count** 현재 이 세마포의 일시 중단된 스레드 수 대상에 대한 포인터입니다.
- **next_semaphore** 다음에 만들 세마포 포인터 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 정보를 검색했습니다.

- **TX_SEMAPHORE_ERROR**(0x0C) 잘못된 세마포 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_SEMAPHORE my_semaphore;
CHAR *name;
ULONG current_value;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT status;

/* Retrieve information about the previously created
semaphore "my_semaphore." */
status = tx_semaphore_info_get(&my_semaphore, &name,
    &current_value,
    &first_suspended, &suspended_count,
    &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>참고 항목

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

세마포 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

이 서비스는 지정된 세마포에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.

**매개 변수**

-  **semaphore_ptr** 이전에 만든 세마포에 대한 포인터입니다.
-  **puts** 이 세마포에서 수행된 넣기 요청 수 대상에 대한 포인터입니다.
-  **gets** 이 세마포에서 수행된 가져오기 요청 수 대상에 대한 포인터입니다.
-  **suspensions** 이 세마포의 스레드 일시 중단 수 대상에 대한 포인터입니다.
-  **timeouts** 이 세마포의 스레드 일시 중단 시간 제한 수 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 세마포 성능 가져오기에 성공했습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 세마포 포인터입니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_SEMAPHORE my_semaphore;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created
semaphore. */
status = tx_semaphore_performance_info_get(&my_semaphore, &puts,
    &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

세마포 시스템 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

이 서비스는 시스템의 모든 세마포에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.

### <a name="parameters"></a>매개 변수

- **puts** 모든 세마포에서 수행된 총 넣기 요청 수 대상에 대한 포인터입니다.
- **gets** 모든 세마포에서 수행된 총 가져오기 요청 수 대상에 대한 포인터입니다.
- **suspensions** 모든 세마포의 총 스레드 일시 중단 수 대상에 대한 포인터입니다.
- **timeouts** 모든 세마포의 총 스레드 일시 중단 시간 제한 수 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 시스템 성능을 가져왔습니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created
semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

세마포 일시 중단 목록의 우선 순위를 지정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Description

이 서비스는 일시 중단 목록 맨 앞에 있는, 세마포 인스턴스 때문에 일시 중단된 스레드를 가장 높은 우선 순위로 지정합니다. 다른 모든 스레드는 일시 중단된 순서와 동일한 FIFO 순서로 유지됩니다.

### <a name="parameters"></a>매개 변수

- **semaphore_ptr** 이전에 만든 세마포에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 세마포 우선 순위 지정에 성공했습니다.
- **TX_SEMAPHORE_ERROR**(0x0C) 잘못된 가산 세마포 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Ensure that the highest priority thread will receive
the next instance of this semaphore. */
status = tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_semaphore_put call made to this semaphore will
wake up this thread. */
```

### <a name="see-also"></a>참고 항목

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_put

## <a name="tx_semaphore_put"></a>tx_semaphore_put

가산 세마포에 인스턴스를 배치합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 가산 세마포에 인스턴스를 배치합니다. 실제로는 가산 세마포가 1씩 증가합니다.

> [!NOTE]
> 세마포가 모두 1(OxFFFFFFFF)인 경우 이 서비스를 호출하면 새 넣기 작업으로 인해 세마포가 0으로 다시 설정됩니다.

### <a name="parameters"></a>매개 변수

- **semaphore_ptr** 이전에 만든 가산 세마포 제어 블록에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 세마포 넣기에 성공했습니다.
- **TX_SEMAPHORE_ERROR**(0x0C) 잘못된 가산 세마포 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a>참고 항목

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_get
- tx_semaphore_put_notify

## <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

세마포가 배치되면 애플리케이션에 알립니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a>Description

이 서비스는 지정된 세마포가 배치될 때마다 호출되는 알림 콜백 함수를 등록합니다. 알림 콜백 처리는 애플리케이션에 의해 정의됩니다.

> [!NOTE]
> 애플리케이션의 세마포 알림 콜백은 일시 중단 옵션을 사용하여 ThreadX API를 호출할 수 없습니다.

### <a name="parameters"></a>매개 변수

- **semaphore_ptr** 이전에 만든 세마포에 대한 포인터입니다.
- **semaphore_put_notify** 애플리케이션의 세마포 넣기 알림 함수에 대한 포인터입니다. 이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 세마포 넣기 알림 등록에 성공했습니다.
- **TX_SEMAPHORE_ERROR**(0x0C) 잘못된 세마포 포인터입니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 시스템이 알림 기능을 사용하지 않도록 설정하여 컴파일되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_SEMAPHORE my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
the put operations on the semaphore "my_semaphore." */
status = tx_semaphore_put_notify(&my_semaphore, my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
was successfully registered. */
void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
    /* The semaphore was just put! */
}
```

### <a name="see-also"></a>참고 항목

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put

## <a name="tx_thread_create"></a>tx_thread_create

애플리케이션 스레드를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_create(
    TX_THREAD *thread_ptr,
    CHAR *name_ptr, 
    VOID (*entry_function)(ULONG),
    ULONG entry_input, 
    VOID *stack_start,
    ULONG stack_size, 
    UINT priority,
    UINT preempt_threshold, 
    ULONG time_slice,
    UINT auto_start);
```

### <a name="description"></a>Description

이 서비스는 지정된 작업 항목 함수에서 실행되기 시작하는 애플리케이션 스레드를 만듭니다. 스택, 우선 순위, 선점 임계값, 시간 조각과 같은 특성은 입력 매개 변수를 통해 지정됩니다. 스레드의 초기 실행 상태도 지정됩니다.

**매개 변수**

- **thread_ptr** 스레드 제어 블록에 대한 포인터입니다.
- **name_ptr** 스레드 이름에 대한 포인터입니다.
- **entry_function** 스레드 실행을 위한 초기 C 함수를 지정합니다. 이 진입 함수에서 스레드가 반환되면 ‘완료됨’ 상태로 지정되고 무기한으로 일시 중단됩니다.
- **entry_input** 처음 실행될 때 스레드의 진입 함수로 전달되는 32비트 값입니다. 이러한 입력을 사용할 것인지 여부는 전적으로 해당 애플리케이션에서 결정합니다.
- **stack_start** 스택 메모리 영역의 시작 주소입니다.
- **stack_size** 스택 메모리 영역의 바이트 수입니다. 스레드의 스택 영역은 최악의 사례 함수 호출 중첩 및 지역 변수 사용을 처리할 수 있을 만큼 충분히 커야 합니다.
- **priority** 숫자로 된 스레드 우선 순위입니다. 유효한 값 범위는 0에서 (TX_MAX_PRIORITES-1)까지입니다. 여기서 값 0은 가장 높은 우선 순위를 나타냅니다.
- **preempt_threshold** 사용하지 않도록 설정된 선점의 가장 높은 우선 순위 수준(0에서 (TX_MAX_PRIORITIES-1))입니다. 우선 순위가 이 수준보다 높아야만 이 스레드를 선점할 수 있습니다. 이 값은 지정한 우선 순위 이하여야 합니다. 스레드 우선 순위와 값이 같으면 선점 임계값이 사용하지 않도록 설정됩니다.
- **time_slice** 우선 순위가 같은 다른 준비 스레드를 실행할 수 있을 때까지 이 스레드를 실행할 수 있는 타이머 틱 수입니다. 선점 임계값을 사용하면 시간 조각화를 사용할 수 없습니다. 유효한 시간 조각 값 범위는 1-0xFFFFFFFF(포함)입니다. **TX_NO_TIME_SLICE** 값(값 0)을 사용하면 이 스레드의 시간 조각화가 사용하지 않도록 설정됩니다.

  > [!NOTE]
  > 시간 조각화를 사용하면 약간의 시스템 오버헤드가 발생합니다. 시간 조각화는 여러 스레드가 동일한 우선 순위를 공유하는 경우에만 유용하므로 고유한 우선 순위가 있는 스레드에는 시간 조각이 할당되면 안 됩니다.

- **auto_start** 스레드가 바로 시작되는지 일시 중단 상태로 설정되는지 지정합니다. 유효한 옵션은 **TX_AUTO_START**(0x01) 및 **TX_DONT_START**(0x00)입니다. TX_DONT_START를 지정하면 애플리케이션은 나중에 tx_thread_resume을 호출해야 스레드를 실행할 수 있습니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 스레드 만들기에 성공했습니다.
- **TX_THREAD_ERROR**(0x0E) 잘못된 스레드 제어 포인터입니다. 포인터가 NULL이거나 스레드가 이미 만들어져 있습니다.
- **TX_PTR_ERROR**(0x03) 진입점의 시작 주소가 잘못되었거나 스택 영역이 잘못되었습니다(일반적으로 NULL).
- **TX_SIZE_ERROR**(0x05) 스택 영역 크기가 잘못되었습니다. 스레드를 실행하려면 **TX_MINIMUM_STACK** 바이트 이상이어야 합니다.
- **TX_PRIORITY_ERROR**(0x0F) 잘못된 스레드 우선 순위입니다. 값이 (0-(TX_MAX_PRIORITIES-1)) 범위를 벗어납니다.
- **TX_THRESH_ERROR**(0x18) 잘못된 preemptionthreshold가 지정되었습니다. 이 값은 스레드 초기 우선 순위 이하의 유효한 우선 순위여야 합니다.
- **TX_START_ERROR**(0x10) 잘못된 자동 시작 선택입니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_THREAD my_thread;
UINT status;

/* Create a thread of priority 15 whose entry point is
"my_thread_entry". This thread’s stack area is 1000
bytes in size, starting at address 0x400000. The
preemption-threshold is setup to allow preemption of threads
with priorities ranging from 0 through 14. Time-slicing is
disabled. This thread is automatically put into a ready
condition. */
status = tx_thread_create(&my_thread, "my_thread_name",
    my_thread_entry, 0x1234,
    (VOID *) 0x400000, 1000,
    15, 15, TX_NO_TIME_SLICE,
    TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
for execution! */

...

/* Thread’s entry function. When "my_thread" actually
begins execution, control is transferred to this
function. */

VOID my_thread_entry (ULONG initial_input)
{
    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */
    /* The real work of the thread, including calls to
    other function should be called from here! */
    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```

### <a name="see-also"></a>참고 항목

- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_delete"></a>tx_thread_delete

애플리케이션 스레드를 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 애플리케이션 스레드를 삭제합니다. 지정된 스레드가 종료 상태 또는 완료 상태여야 하므로 이 서비스는 자체를 삭제하려고 시도하는 스레드에서 호출할 수 없습니다.

> [!NOTE]
> 이 서비스가 완료된 후 사용할 수 있는 스레드 스택과 연결된 메모리 영역은 애플리케이션에서 관리해야 합니다. 또한 애플리케이션은 삭제된 스레드를 사용하지 않도록 해야 합니다.

### <a name="parameters"></a>매개 변수

- **thread_ptr** 이전에 만든 애플리케이션 스레드에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 스레드 삭제에 성공했습니다.
- **TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.
- **TX_DELETE_ERROR**(0x11) 지정된 스레드가 종료 상태 또는 완료 상태가 아닙니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_THREAD my_thread;
UINT status;

/* Delete an application thread whose control block is
"my_thread". Assume that the thread has already been
created with a call to tx_thread_create. */
status = tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
deleted. */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

스레드 진입 및 종료 시 애플리케이션에 알립니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a>Description

이 서비스는 지정된 스레드에 진입하거나 종료할 때마다 호출되는 알림 콜백 함수를 등록합니다. 알림 콜백 처리는 애플리케이션에 의해 정의됩니다.

> [!NOTE]
> 애플리케이션 스레드 진입/종료 알림 콜백은 일시 중단 옵션을 사용하여 ThreadX API를 호출할 수 없습니다.

### <a name="parameters"></a>매개 변수

- **thread_ptr** 이전에 만든 스레드에 대한 포인터입니다.
- **entry_exit_notify** 애플리케이션 스레드 진입/종료 알림 함수에 대한 포인터입니다. 진입/종료 알림 함수의 두 번째 매개 변수는 진입 또는 종료가 있는지 여부를 지정합니다. 값 **TX_THREAD_ENTRY**(0x00)는 스레드에 진입했음을 나타내고, 값 **TX_THREAD_EXIT**(0x01)는 스레드가 종료되었음을 나타냅니다. 이 값이 **TX_NULL** 이면 알림이 사용하지 않도록 설정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 스레드 진입/종료 알림 함수 등록에 성공했습니다.
- **TX_THREAD_ERROR**(0x0E) 잘못된 스레드 포인터입니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 시스템이 알림 기능을 사용하지 않도록 설정하여 컴파일되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_THREAD my_thread;
/* Register the "my_entry_exit_notify" function for monitoring
the entry/exit of the thread "my_thread." */
status = tx_thread_entry_exit_notify(&my_thread,
    my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{
    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
        /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
        /* Thread exit! */
}
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_identify"></a>tx_thread_identify

현재 실행 중인 스레드에 대한 포인터를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a>Description

이 서비스는 현재 실행 중인 스레드에 대한 포인터를 반환합니다. 스레드가 실행되고 있지 않으면 이 서비스는 Null 포인터를 반환합니다.

> [!NOTE]
> 이 서비스를 ISR에서 호출하는 경우 반환 값은 실행 중인 인터럽트 처리기 이전에 실행되는 스레드를 나타냅니다.

### <a name="parameters"></a>매개 변수

None

### <a name="retuen-values"></a>반환 값

- **thread pointer** 현재 실행 중인 스레드에 대한 포인터입니다. 실행 중인 스레드가 없는 경우 반환 값은 **TX_NULL** 입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

TX_THREAD *my_thread_ptr;

```c
TX_THREAD *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr = tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
from that thread or an ISR that interrupted that thread.
Otherwise, this service was called
from an ISR when no thread was running when the
interrupt occurred. */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_info_get"></a>tx_thread_info_get

스레드에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_info_get(
    TX_THREAD *thread_ptr, 
    CHAR **name,
    UINT *state, 
    ULONG *run_count,
    UINT *priority,
    UINT *preemption_threshold,
    ULONG *time_slice,
    TX_THREAD **next_thread,
    TX_THREAD **suspended_thread);
```

### <a name="description"></a>Description

이 서비스는 지정된 스레드에 대한 정보를 검색합니다.

### <a name="parameters"></a>매개 변수
- **thread_ptr** 스레드 제어 블록에 대한 포인터입니다.
- **name** 스레드 이름에 대한 포인터 대상에 대한 포인터입니다.
- **state** 스레드의 현재 실행 상태 대상에 대한 포인터입니다. 가능한 값은 다음과 같습니다.
    - **TX_READY**(0x00)
    - **TX_COMPLETED**(0x01)
    - **TX_TERMINATED**(0x02)
    - **TX_SUSPENDED**(0x03)
    - **TX_SLEEP**(0x04)
    - **TX_QUEUE_SUSP**(0x05)
    - **TX_SEMAPHORE_SUSP**(0x06)
    - **TX_EVENT_FLAG**(0x07)
    - **TX_BLOCK_MEMORY**(0x08)
    - **TX_BYTE_MEMORY**(0x09)
    - **TX_MUTEX_SUSP**(0x0D)  

- **run_count** 스레드 실행 횟수 대상에 대한 포인터입니다.
- **priority** 스레드 우선 순위 대상에 대한 포인터입니다.
- **preemption_threshold** 스레드 선점 임계값 대상에 대한 포인터입니다.
**time_slice** 스레드 시간 조각 대상에 대한 포인터입니다.
**next_thread** 다음에 만들 스레드 포인터 대상에 대한 포인터입니다.

**suspended_thread** 일시 중단 목록의 다음 스레드에 대한 포인터 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 스레드 정보 검색에 성공했습니다.
- **TX_THREAD_ERROR**(0x0E) 잘못된 스레드 제어 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
thread "my_thread." */

status = tx_thread_info_get(&my_thread, &name,
    &state, &run_count,
    &priority, &preemption_threshold,
    &time_slice, &next_thread,&suspended_thread);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

스레드 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_performance_info_get(
    TX_THREAD *thread_ptr,
    LONG *resumptions, 
    ULONG *suspensions,
    ULONG *solicited_preemptions, 
    ULONG *interrupt_preemptions,
    ULONG *priority_inversions, 
    ULONG *time_slices,
    ULONG *relinquishes, 
    ULONG *timeouts, 
    ULONG *wait_aborts,
    TX_THREAD **last_preempted_by);
```

### <a name="description"></a>Description

이 서비스는 지정된 스레드에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.

### <a name="parameters"></a>매개 변수
- **thread_ptr** 이전에 만든 스레드에 대한 포인터입니다.
- **resumptions** 이 스레드 재개 수 대상에 대한 포인터입니다.
- **suspensions** 이 스레드 일시 중단 수 대상에 대한 포인터입니다.
- **solicited_preemptions** 이 스레드에서 수행한 ThreadX API 서비스 호출의 결과인 선점 수 대상에 대한 포인터입니다.
- **interrupt_preemptions** 인터럽트 처리의 결과인 이 스레드 선점 수 대상에 대한 포인터입니다.
- **priority_inversions** 이 스레드 우선 순위 반전 수 대상에 대한 포인터입니다.
- **time_slices** 이 스레드 시간 조각 수 대상에 대한 포인터입니다.
- **relinquishes** 이 스레드에서 수행된 스레드 양도 수 대상에 대한 포인터입니다.
- **timeouts** 이 스레드의 일시 중단 시간 제한 수 대상에 대한 포인터입니다.
- **wait_aborts** 이 스레드에서 수행된 대기 중단 수 대상에 대한 포인터입니다.
- **last_preempted_by** 이 스레드를 마지막으로 선점한 스레드 포인터 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 TX_NULL을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 스레드 성능 가져오기에 성공했습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 스레드 포인터입니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_THREAD my_thread;
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
TX_THREAD *last_preempted_by;

/* Retrieve performance information on the previously created
thread. */

status = tx_thread_performance_info_get(&my_thread, &resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices,
    &relinquishes, &timeouts,
    &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

스레드 시스템 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_performance_system_info_get(
    ULONG *resumptions,
    ULONG *suspensions, 
    ULONG *solicited_preemptions,
    ULONG *interrupt_preemptions, 
    ULONG *priority_inversions,
    ULONG *time_slices, 
    ULONG *relinquishes, 
    ULONG *timeouts,
    ULONG *wait_aborts, 
    ULONG *non_idle_returns,
    ULONG *idle_returns);
```

### <a name="description"></a>Description

이 서비스는 시스템의 모든 스레드에 대한 성능 정보를 검색합니다.

ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된

***TX_THREAD_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.

### <a name="parameters"></a>매개 변수

- **resumptions** 총 스레드 재개 수 대상에 대한 포인터입니다.
- **suspensions** 총 스레드 일시 중단 수 대상에 대한 포인터입니다.
- **solicited_preemptions** ThreadX API 서비스를 호출하는 스레드의 결과인 총 스레드 선점 수 대상에 대한 포인터입니다.
- **interrupt_preemptions** 인터럽트 처리 결과인 총 스레드 선점 수 대상에 대한 포인터입니다.
- **priority_inversions** 총 스레드 우선 순위 반전 수 대상에 대한 포인터입니다.
- **time_slices** 총 스레드 시간 조각 수 대상에 대한 포인터입니다.
- **relinquishes** 총 스레드 양도 수 대상에 대한 포인터입니다.
- **timeouts** 총 스레드 일시 중단 시간 제한 수 대상에 대한 포인터입니다.
- **wait_aborts** 총 스레드 대기 중단 수 대상에 대한 포인터입니다.
- **non_idle_returns** 다른 스레드를 실행할 준비가 되면 스레드가 시스템으로 반환되는 횟수 대상에 대한 포인터입니다.
- **idle_returns** 실행할 준비가 된 스레드가 없는 경우(유휴 시스템) 스레드가 시스템으로 반환되는 횟수 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 **TX_NULL** 을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 스레드 시스템 성능 가져오기에 성공했습니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
ULONG non_idle_returns;
ULONG idle_returns;

/* Retrieve performance information on all previously created
thread. */

status = tx_thread_performance_system_info_get(&resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices, &relinquishes,
    &timeouts, &wait_aborts, &non_idle_returns,
    &idle_returns);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

애플리케이션 스레드의 선점 임계값을 변경합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a>Description

이 서비스는 지정된 스레드의 선점 임계값을 변경합니다. 선점 임계값을 사용하면 선점 임계값 이하인 스레드에서 지정된 스레드를 선점하는 것을 방지합니다.

>[!NOTE]
> 선점 임계값을 사용하면 지정된 스레드에 시간 조각화를 사용할 수 없습니다.

### <a name="parameters"></a>매개 변수
- **thread_ptr** 이전에 만든 애플리케이션 스레드에 대한 포인터입니다.
- **new_threshold** 새 선점 임계값 우선 순위 수준입니다(0-(TX_MAX_PRIORITIES-1)).
- **old_threshold** 이전 선점 임계값을 반환할 위치에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 선점 임계값 변경에 성공했습니다.
- **TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.
- **TX_THRESH_ERROR**(0x18) 지정된 새 선점 임계값이 잘못된 스레드 우선 순위((0-(**TX_MAX_PRIORITIES**-1) 이외의 값)이거나 현재 스레드 우선 순위보다 높습니다.
- **TX_PTR_ERROR**(0x03) 이전 preemptionthreshold 스토리지 위치에 대한 포인터가 잘못되었습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_THREAD my_thread;
UINT my_old_threshold;
UINT status;

/* Disable all preemption of the specified thread. The
current preemption-threshold is returned in
"my_old_threshold". Assume that "my_thread" has
already been created. */

status = tx_thread_preemption_change(&my_thread,
    0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
non-preemptable by another thread. Note that ISRs are
not prevented by preemption disabling. */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_priority_change"></a>tx_thread_priority_change

애플리케이션 스레드의 우선 순위를 변경합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a>Description

이 서비스는 지정된 스레드의 우선 순위를 변경합니다. 유효한 우선 순위 범위는 0-(TX_MAX_PRIORITES-1)입니다. 여기서 0은 가장 높은 우선 순위 수준을 나타냅니다.

> [!IMPORTANT]
> 지정된 스레드의 선점 임계값은 새 우선 순위로 자동 설정됩니다. 새 임계값을 사용하려면 이 호출 후 ***tx_thread_preemption_change*** 서비스를 사용해야 합니다.

### <a name="parameters"></a>매개 변수

- **thread_ptr** 이전에 만든 애플리케이션 스레드에 대한 포인터입니다.
- **new_priority** 새 스레드 우선 순위 수준(0-(TX_MAX_PRIORITIES-1))입니다.
- **old_priority** 스레드의 이전 우선 순위를 반환할 위치에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 우선 순위 변경에 성공했습니다.
- **TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.
- **TX_PRIORITY_ERROR**(0x0F) 지정된 새 우선 순위가 잘못되었습니다((0-(TX_MAX_PRIORITIES-1) 이외의 값).
- **TX_PTR_ERROR**(0x03) 이전 우선 순위 스토리지 위치에 대한 포인터가 잘못되었습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_THREAD my_thread;
UINT my_old_priority;
UINT status;

/* Change the thread represented by "my_thread" to priority
0. */

status = tx_thread_priority_change(&my_thread,
    0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
now at the highest priority level in the system. */
```
### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_relinquish"></a>tx_thread_relinquish

다른 애플리케이션 스레드로 제어를 양도합니다.

### <a name="prototype"></a>프로토타입

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a>Description

이 서비스는 우선 순위가 동일하거나 더 높은, 실행 준비가 된 다른 스레드로 프로세서 제어를 양도합니다.

> [!NOTE]
> 이 서비스는 우선 순위가 동일한 스레드로 제어를 양도할 뿐만 아니라, 현재 스레드의 선점 임계값 설정으로 실행이 방지된 우선 순위가 가장 높은 스레드로 제어를 양도하기도 합니다.

### <a name="parameters"></a>매개 변수

없음

### <a name="return-values"></a>반환 값

없음

### <a name="allowed-from"></a>허용 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="examples"></a>예

```c
ULONG run_counter_1 = 0;
ULONG run_counter_2 = 0;

/* Example of two threads relinquishing control to
each other in an infinite loop. Assume that
both of these threads are ready and have the same
priority. The run counters will always stay within one
of each other. */

VOID my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{

    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_reset"></a>tx_thread_reset

스레드를 다시 설정합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 스레드가 스레드를 만들 때 정의한 진입점에서 실행되도록 다시 설정합니다. 다시 설정하려면 스레드가 **TX_COMPLETED** 또는 **TX_TERMINATED** 상태여야 합니다.

> [!IMPORTANT]
> 스레드를 다시 실행하려면 다시 시작해야 합니다.

### <a name="parameters"></a>매개 변수

- **thread_ptr** 이전에 만든 스레드에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 스레드를 다시 설정하는 데 성공했습니다.
- **TX_NOT_DONE**(0x20) 지정된 스레드가 **TX_COMPLETED** 또는 **TX_TERMINATED** 상태가 아닙니다.
- **TX_THREAD_ERROR**(0x0E) 잘못된 스레드 포인터입니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="example"></a>예제

TX_THREAD my_thread;

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preformance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_resume"></a>tx_thread_resume

일시 중단된 애플리케이션 스레드를 다시 시작합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

이 서비스는 이전에 ***tx_thread_suspend*** 호출로 일시 중단된 스레드의 실행을 다시 시작하거나 준비합니다. 이 서비스는 자동 시작 없이 생성된 스레드도 다시 시작합니다.

### <a name="parameters"></a>매개 변수

- **thread_ptr** 일시 중단된 애플리케이션 스레드에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 스레드를 다시 시작하는 데 성공했습니다.
- **TX_SUSPEND_LIFTED**(0x19) 이전에 설정한 지연된 일시 중단이 해제되었습니다.
- **TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.
- **TX_RESUME_ERROR**(0x12) 지정된 스레드가 일시 중단되지 않았거나 이전에 **_tx_thread_suspend_** 이외의 서비스를 통해 일시 중단되었습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

TX_THREAD my_thread;

### <a name="example"></a>예제

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_sleep"></a>tx_thread_sleep

지정된 시간 동안 현재 스레드 일시 중단합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a>Description

이 서비스는 지정된 타이머 틱 수 기간 동안 호출 스레드가 일시 중단되도록 합니다. 타이머 틱과 연결된 실제 시간의 양은 애플리케이션마다 다릅니다. 이 서비스는 애플리케이션 스레드에서만 호출할 수 있습니다.

### <a name="parameters"></a>매개 변수

- **timer_ticks** 호출하는 애플리케이션 스레드를 일시 중단할 타이머 틱 수이며, 범위는 0-0xFFFFFFFF입니다. 0을 지정하면 서비스에서 즉시 반환합니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 스레드 일시 중지에 성공했습니다.
- **TX_WAIT_ABORTED**(0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 중단되었습니다.
- **TX_CALLER_ERROR**(0x13) 서비스가 비스레드에서 호출되었습니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create, tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_stack_error_notify"></a>tx_thread_stack_error_notify

스레드 스택 오류 알림 콜백을 등록합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a>Description

이 서비스는 스레드 스택 오류 처리를 위한 알림 콜백 함수를 등록합니다. ThreadX가 실행 중에 스레드 스택 오류를 검색하면 오류를 처리하도록 이 알림 함수를 호출합니다. 오류 처리는 전적으로 해당 애플리케이션에서 정의됩니다. 위반 스레드 일시 중단부터 전체 시스템 초기화까지 수행할 수도 있습니다.

> [!IMPORTANT]
> ThreadX 라이브러리는 이 서비스가 성능 정보를 반환하도록 정의된 **TX_ENABLE_STACK_CHECKING** 을 사용하여 빌드되어야 합니다. 

### <a name="parameters"></a>매개 변수
- **error_handler** 애플리케이션의 스택 오류를 처리하는 함수에 대한 포인터입니다. 이 값이 TX_NULL이면 알림이 사용하지 않도록 설정됩니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 스레드를 다시 설정하는 데 성공했습니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preformance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_suspend"></a>tx_thread_suspend

애플리케이션 스레드를 일시 중단합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 애플리케이션 스레드를 일시 중단합니다. 스레드가 이 서비스를 호출하여 자체적으로 일시 중단할 수도 있습니다.

> [!NOTE]
> 지정된 스레드가 다른 이유로 이미 일시 중단되어 있는 경우 이전 일시 중단이 해제될 때까지 이 일시 중단은 내부적으로 보류됩니다. 이전 일시 중단이 해제되면 지정된 스레드에 대한 무조건 일시 중단이 수행됩니다. 향후의 무조건 일시 중단 요청은 영향을 주지 않습니다.

일시 중단된 후 스레드를 다시 실행하려면 ***tx_thread_resume*** 을 통해 스레드를 다시 시작해야 합니다.

### <a name="parameters"></a>매개 변수

- **thread_ptr** 애플리케이션 스레드에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 스레드 일시 중단에 성공했습니다.
- **TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.
- **TX_SUSPEND_ERROR**(0x14) 지정된 스레드가 종료 상태 또는 완료 상태입니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_terminate"></a>tx_thread_terminate

애플리케이션 스레드를 종료합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Description

이 서비스는 스레드가 일시 중단되었는지 여부에 관계없이 지정된 애플리케이션 스레드를 종료합니다. 스레드가 이 서비스를 호출하여 자체적으로 종료할 수도 있습니다.

> [!NOTE]
> 애플리케이션은 스레드가 종료에 적합한 상태인지 확인해야 합니다. 예를 들어 중요한 애플리케이션을 처리하는 중이거나 이러한 처리가 알 수 없는 상태로 남아 있을 수 있는 다른 미들웨어 구성 요소 내에서는 스레드를 종료하면 안 됩니다.

> [!IMPORTANT]
> 종료된 후 스레드를 다시 실행하려면 스레드를 다시 설정해야 합니다.

### <a name="parameters"></a>매개 변수

- **thread_ptr** 애플리케이션 스레드에 대한 포인터입니다.

### <a name="return-values"></a>반환 값
- **TX_SUCCESS**(0x00) 스레드를 종료하는 데 성공했습니다.
- **TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

애플리케이션 스레드의 시간 조각을 변경합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a>Description

이 서비스는 지정된 애플리케이션 스레드의 시간 조각을 변경합니다. 스레드에 대해 시간 조각을 선택하면 우선 순위가 같거나 더 높은 다른 스레드를 실행하기 전에 지정된 타이머 틱 수 이하로 스레드가 실행되도록 보장합니다.

> [!NOTE]
> 선점 임계값을 사용하면 지정된 스레드에 시간 조각화를 사용할 수 없습니다.

### <a name="parameters"></a>매개 변수

- **thread_ptr** 애플리케이션 스레드에 대한 포인터입니다.
- **new_time_slice** 새 시간 조각 값입니다. 유효한 값에는 TX_NO_TIME_SLICE와 숫자 값 1부터 0xFFFFFFFF까지가 포함됩니다.
- **old_time_slice** 지정된 스레드의 이전 timeslice 값 저장 위치에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 시간 조각 변경에 성공했습니다.
- **TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.
- **TX_PTR_ERROR**(0x03) 이전 시간 조각 스토리지 위치에 대한 포인터가 잘못되었습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드, 타이머

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_THREAD my_thread;
ULONG my_old_time_slice;
UINT status;

/* Change the time-slice of the thread associated with
"my_thread" to 20. This will mean that "my_thread"
can only run for 20 timer-ticks consecutively before
other threads of equal or higher priority get a chance
to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
    &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
has been changed to 20 and the previous time-slice is
in "my_old_time_slice." */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_wait_abort

## <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

지정된 스레드의 일시 중단을 중단합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 스레드의 일시 중지 또는 다른 개체 일시 중단을 중단합니다. 대기가 중단되면 스레드가 대기하고 있던 서비스에서 **TX_WAIT_ABORTED** 값이 반환됩니다.

> [!NOTE]
> 이 서비스는 *tx_thread_suspend* 서비스에서 수행한 명시적 일시 중단은 해제하지 않습니다.

### <a name="parameters"></a>매개 변수

- **thread_ptr** 이전에 만든 애플리케이션 스레드에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 스레드 대기 중단에 성공했습니다.
- **TX_THREAD_ERROR**(0x0E) 잘못된 애플리케이션 스레드 포인터입니다.
- **TX_WAIT_ABORT_ERROR**(0x1B) 지정된 스레드가 대기 상태가 아닙니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점
예

### <a name="example"></a>예제

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a>참고 항목

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change

## <a name="tx_time_get"></a>tx_time_get

현재 시간을 검색합니다.

애플리케이션 타이머

### <a name="prototype"></a>프로토타입

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a>Description

이 서비스는 내부 시스템 클록의 콘텐츠를 반환합니다. 각 타이머 틱은 내부 시스템 클록을 1씩 늘립니다. 시스템 클록은 초기화 중에 0으로 설정되며 ***tx_time_set*** 서비스를 통해 특정 값으로 변경될 수 있습니다.

> [!NOTE]
> 각 타이머 틱이 나타내는 실제 시간은 애플리케이션마다 다릅니다.

**매개 변수**

None

### <a name="return-values"></a>반환 값

- **system clock ticks** 원하는 대로 실행할 수 있는 내부 시스템 클록 값입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점
예

### <a name="example"></a>예제

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a>참고 항목

- tx_time_set

## <a name="tx_time_set"></a>tx_time_set

현재 시간을 설정합니다.

### <a name="prototype"></a>프로토타입

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a>Description

이 서비스는 내부 시스템 클록을 지정된 값으로 설정합니다. 각 타이머 틱은 내부 시스템 클록을 1씩 늘립니다.

> [!NOTE]
> 각 타이머 틱이 나타내는 실제 시간은 애플리케이션마다 다릅니다.

### <a name="parameters"></a>매개 변수

- **new_time** 시스템 클록에 배치할 새 시간입니다. 유효한 값 범위는 0-0xFFFFFFFF입니다.

### <a name="return-values"></a>반환 값

없음

### <a name="allowed-from"></a>허용 위치

스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a>참고 항목

- tx_time_get

## <a name="tx_timer_activate"></a>tx_timer_activate

애플리케이션 타이머를 활성화합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 애플리케이션 타이머를 활성화합니다. 동시에 만료되는 여러 타이머의 만료 루틴은 활성화된 순서대로 실행됩니다.

> [!NOTE]
> 만료된 일회성 타이머를 다시 활성화하려면 먼저 ***tx_timer_change** __*를 통해 타이머를 다시 설정해야 합니다.

### <a name="parameters"></a>매개 변수

- **timer_ptr** 이전에 만든 애플리케이션 타이머에 대한 포인터입니다.

**반환 값**

- **TX_SUCCESS**(0x00) 애플리케이션 타이머 활성화에 성공했습니다.
- **TX_TIMER_ERROR**(0x15) 잘못된 애플리케이션 타이머 포인터입니다.
- **TX_ACTIVATE_ERROR**(0x17) 타이머가 이미 활성이거나 이미 만료된 일회성 타이머입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a>참고 항목

- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_change"></a>tx_timer_change

애플리케이션 타이머를 변경합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a>Description

이 서비스는 지정된 애플리케이션 타이머의 만료 특성을 변경합니다. 이 서비스를 호출하기 전에 타이머를 비활성화해야 합니다.

> [!NOTE]
> 타이머를 다시 시작하려면 이 서비스 다음에 ***tx_timer_activate** _ _*서비스를 호출해야 합니다.

### <a name="parameters"></a>매개 변수

- **timer_ptr** 타이머 제어 블록에 대한 포인터입니다.
- **initial_ticks** 타이머 만료에 사용되는 초기 틱 수를 지정합니다. 유효한 값 범위는 1-0xFFFFFFFF입니다.
- **reschedule_ticks** 첫 번째 이후의 모든 타이머 만료에 사용되는 틱 수를 지정합니다. 이 매개 변수가 0이면 타이머가 ‘일회성’ 타이머가 됩니다. 매개 변수가 0이 아닌 정기적인 타이머의 경우 유효한 값 범위는 1-0xFFFFFFFF입니다.

> [!NOTE]
> 만료된 일회성 타이머를 다시 활성화하려면 먼저
***tx_timer_change** __*를 통해 타이머를 다시 설정해야 합니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 애플리케이션 타이머를 변경하는 데 성공했습니다.
- **TX_TIMER_ERROR**(0x15) 잘못된 애플리케이션 타이머 포인터입니다.
- **TX_TICK_ERROR**(0x16) 초기 틱에 잘못된 값(0)이 제공되었습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_TIMER my_timer;
UINT status;

/* Change a previously created and now deactivated timer
to expire every 50 timer ticks, including the initial
expiration. */
status = tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```

### <a name="see-also"></a>참고 항목

- tx_timer_activate
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_create"></a>tx_timer_create

애플리케이션 타이머를 만듭니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_timer_create(
    TX_TIMER *timer_ptr, 
    CHAR *name_ptr,
    VOID (*expiration_function)(ULONG),
    ULONG expiration_input, 
    ULONG initial_ticks,
    ULONG reschedule_ticks, 
    UINT auto_activate);
```

### <a name="description"></a>Description

이 서비스는 지정된 만료 함수 및 정기 설정을 사용하여 애플리케이션 타이머를 만듭니다.

### <a name="parameters"></a>매개 변수

- **timer_ptr** 타이머 제어 블록에 대한 포인터입니다.
- **name_ptr** 타이머 이름에 대한 포인터입니다.
- **expiration_function** 타이머가 만료될 때 호출하는 애플리케이션 함수입니다.
- **expiration_input** 타이머가 만료될 때 만료 함수에 전달하는 입력입니다.
- **initial_ticks** 타이머 만료에 사용되는 초기 틱 수를 지정합니다. 유효한 값 범위는 1-0xFFFFFFFF입니다.
- **reschedule_ticks** 첫 번째 이후의 모든 타이머 만료에 사용되는 틱 수를 지정합니다. 이 매개 변수가 0이면 타이머가 ‘일회성’ 타이머가 됩니다. 매개 변수가 0이 아닌 정기적인 타이머의 경우 유효한 값 범위는 1-0xFFFFFFFF입니다.

  > [!NOTE]
  > 일회성 타이머가 만료된 후 다시 활성화하려면 먼저 *tx_timer_change* 를 통해 일회성 타이머를 다시 설정해야 합니다.

- **auto_activate** 타이머를 만드는 동안 타이머가 자동으로 활성화되는지 여부를 결정합니다. 이 값이 **TX_AUTO_ACTIVATE**(0x01)이면 타이머가 활성 상태가 됩니다. 그러지 않고 **TX_NO_ACTIVATE**(0x00) 값을 선택하면 타이머가 비활성 상태로 만들어집니다. 이 경우 타이머를 실제로 시작하려면 후속 **_tx_timer_activate_** 서비스 호출이 필요합니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 애플리케이션 타이머 만들기에 성공했습니다.
- **TX_TIMER_ERROR**(0x15) 잘못된 애플리케이션 타이머 포인터입니다. 포인터가 NULL이거나 타이머가 이미 만들어져 있습니다.
- **TX_TICK_ERROR**(0x16) 초기 틱에 잘못된 값(0)이 제공되었습니다.
- **TX_ACTIVATE_ERROR**(0x17) 잘못된 활성화를 선택했습니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_TIMER my_timer;
UINT status;

/* Create an application timer that executes
"my_timer_function" after 100 ticks initially and then
after every 25 ticks. This timer is specified to start
immediately! */
status = tx_timer_create(&my_timer,"my_timer_name",
    my_timer_function, 0x1234, 100, 25,
    TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
be called 100 timer ticks later and then called every
25 timer ticks. Note that the value 0x1234 is passed to
my_timer_function every time it is called. */
```

### <a name="see-also"></a>참고 항목

- tx_timer_activate
- tx_timer_change
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_deactivate"></a>tx_timer_deactivate

애플리케이션 타이머를 비활성화합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 애플리케이션 타이머를 비활성화합니다. 타이머가 이미 비활성화되어 있는 경우에는 이 서비스가 아무런 영향을 미치지 않습니다.

### <a name="parameters"></a>매개 변수

- **timer_ptr** 이전에 만든 애플리케이션 타이머에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 애플리케이션 타이머를 비활성화하는 데 성공했습니다.
- **TX_TIMER_ERROR**(0x15) 잘못된 애플리케이션 타이머 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a>참고 항목

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_delete"></a>tx_timer_delete

애플리케이션 타이머를 삭제합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Description

이 서비스는 지정된 애플리케이션 타이머를 삭제합니다.

> [!NOTE]
> 애플리케이션은 삭제된 타이머를 사용하지 않도록 해야 합니다.

### <a name="parameters"></a>매개 변수

- **timer_ptr** 이전에 만든 애플리케이션 타이머에 대한 포인터입니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 애플리케이션 타이머를 삭제하는 데 성공했습니다.
- **TX_TIMER_ERROR**(0x15) 잘못된 애플리케이션 타이머 포인터입니다.
- **TX_CALLER_ERROR**(0x13) 이 서비스의 잘못된 호출자입니다.

### <a name="allowed-from"></a>허용되는 위치

스레드

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a>참고 항목

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_info_get"></a>tx_timer_info_get

애플리케이션 타이머에 대한 정보를 검색합니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a>Description

이 서비스는 지정된 애플리케이션 타이머에 대한 정보를 검색합니다.

### <a name="parameters"></a>매개 변수

- **timer_ptr** 이전에 만든 애플리케이션 타이머에 대한 포인터입니다.
- **name** 타이머 이름에 대한 포인터 대상에 대한 포인터입니다.
- **active** 타이머 활성 표시 대상에 대한 포인터입니다. 타이머가 비활성 상태이거나 이 서비스가 타이머 자체에서 호출된 경우 **TX_FALSE** 값이 반환됩니다. 그러지 않고 타이머가 활성 상태인 경우 **TX_TRUE** 값이 반환됩니다.
- **remaining_ticks** 타이머 만료까지 남은 타이머 틱 수 대상에 대한 포인터입니다.
- **reschedule_ticks** 이 타이머를 자동으로 다시 예약하는 데 사용될 타이머 틱 수 대상에 대한 포인터입니다. 값이 0이면 타이머는 일회성이며 다시 예약되지 않습니다.
- **next_timer** 다음에 만들 애플리케이션 타이머 포인터 대상에 대한 포인터입니다.

> [!NOTE]
> 매개 변수에 **TX_NULL** 을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 타이머 정보 검색에 성공했습니다.
- **TX_TIMER_ERROR**(0x15) 잘못된 애플리케이션 타이머 포인터입니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="preemption-possible"></a>가능한 선점

예

### <a name="example"></a>예제

```c
TX_TIMER my_timer;
CHAR *name;
UINT active;
ULONG remaining_ticks;
ULONG reschedule_ticks;
TX_TIMER *next_timer;
UINT status;

/* Retrieve information about the previously created
application timer "my_timer." */
status = tx_timer_info_get(&my_timer, &name,
    &active,&remaining_ticks,
    &reschedule_ticks,
    &next_timer);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>참고 항목

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

타이머 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a>Description

이 서비스는 지정된 애플리케이션 타이머에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _를 사용하여 빌드되어야 합니다.

### <a name="parameters"></a>매개 변수
- **timer_ptr** 이전에 만든 타이머에 대한 포인터입니다.
- **activates** 이 타이머에서 수행된 활성화 요청 수 대상에 대한 포인터입니다.
- **reactivates** 이 주기적인 타이머에서 수행되는 자동 다시 활성화 수 대상에 대한 포인터입니다.
- **deactivates** 이 타이머에서 수행되는 비활성화 요청 수 대상에 대한 포인터입니다.
- **expirations** 이 타이머의 만료 수 대상에 대한 포인터입니다.
- **expiration_adjusts** 이 타이머에서 수행되는 내부 만료 조정 수 대상에 대한 포인터입니다. 이러한 조정은 기본 타이머 목록 크기보다 큰 타이머의 타이머 인터럽트 처리에서 수행됩니다(기본적으로 만료 시간이 32틱을 초과하는 타이머).

> [참고] 매개 변수에 *TX_NULL* 을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 타이머 성능 가져오기에 성공했습니다.
- **TX_PTR_ERROR**(0x03) 잘못된 타이머 포인터입니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
TX_TIMER my_timer;
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on the previously created
timer. */
status = tx_timer_performance_info_get(&my_timer, &activates,
    &reactivates,&deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

타이머 시스템 성능 정보를 가져옵니다.

### <a name="prototype"></a>프로토타입

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a>Description

이 서비스는 시스템의 모든 애플리케이션 타이머에 대한 성능 정보를 검색합니다.

> [!IMPORTANT]
> ThreadX 라이브러리 및 애플리케이션은 이 서비스가 성능 정보를 반환하도록 정의된 **TX_TIMER_ENABLE_PERFORMANCE_INFO** 를 사용하여 빌드되어야 합니다. 

**매개 변수**

- **activates** 모든 타이머에서 수행되는 총 활성화 요청 수 대상에 대한 포인터입니다.
- **reactivates** 모든 주기적인 타이머에서 수행되는 총 자동 다시 활성화 수 대상에 대한 포인터입니다.
- **deactivates** 모든 타이머에서 수행되는 총 비활성화 요청 수 대상에 대한 포인터입니다.
- **expirations** 모든 타이머의 총 만료 수 대상에 대한 포인터입니다.
- **expiration_adjusts** 모든 타이머에서 수행되는 총 내부 만료 조정 수 대상에 대한 포인터입니다. 이러한 조정은 기본 타이머 목록 크기보다 큰 타이머의 타이머 인터럽트 처리에서 수행됩니다(기본적으로 만료 시간이 32틱을 초과하는 타이머).

> [!NOTE]
> 매개 변수에 **TX_NULL** 을 제공하는 것은 매개 변수가 필요하지 않음을 나타냅니다.

### <a name="return-values"></a>반환 값

- **TX_SUCCESS**(0x00) 타이머 시스템 성능 가져오기에 성공했습니다.
- **TX_FEATURE_NOT_ENABLED**(0xFF) 성능 정보를 사용하도록 설정하여 시스템을 컴파일하지 않았습니다.

### <a name="allowed-from"></a>허용되는 위치

초기화, 스레드, 타이머, ISR

### <a name="example"></a>예제

```c
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on all previously created
timers. */
status = tx_timer_performance_system_info_get(&activates,
    &reactivates, &deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>참고 항목

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
