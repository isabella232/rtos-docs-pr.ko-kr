---
title: 5장 - Azure RTOS ThreadX SMP용 디바이스 드라이버
description: 이 장에서는 Azure RTOS ThreadX SMP의 디바이스 드라이버에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: acfb54a25cc8bc27b7d0aaeff48956529d90c9e1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812834"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx-smp"></a>5장 - Azure RTOS ThreadX SMP용 디바이스 드라이버

이 장에서는 Azure RTOS ThreadX SMP의 디바이스 드라이버에 대해 설명합니다. 이 장에 제시된 정보는 개발자가 애플리케이션별 드라이버를 작성하는 데 도움이 되도록 하기 위한 것입니다. 

## <a name="device-driver-introduction"></a>디바이스 드라이버 소개

외부 환경과의 통신은 대부분의 포함된 애플리케이션의 중요한 구성 요소입니다. 이 통신은 포함된 애플리케이션 소프트웨어에 액세스할 수 있는 하드웨어 디바이스를 통해 수행됩니다. 이러한 디바이스를 관리하는 소프트웨어 구성 요소를 일반적으로 *디바이스 드라이버* 라고 합니다.

포함된 실시간 시스템의 디바이스 드라이버는 본질적으로 애플리케이션에 의존합니다. 이는 두 가지 주요 이유, 즉 대상 하드웨어의 다양함과 실시간 애플리케이션에 부과되는 동일한 성능 요구 사항 때문입니다. 따라서 모든 애플리케이션의 요구 사항을 충족하는 공통 드라이버 세트를 제공하는 것은 사실상 불가능합니다. 이러한 이유로 이 장의 정보는 사용자가 *기성 제품* ThreadX SMP 디바이스 드라이버를 사용자 정의하고 고유한 특정 드라이버를 작성하는 데 도움이 되도록 하기 위한 것입니다.

## <a name="driver-functions"></a>드라이버 함수

ThreadX SMP 디바이스 드라이버는 다음과 같은 8가지 기본 기능 영역으로 구성됩니다.

- **드라이버 초기화**
- **드라이버 제어**
- **드라이버 액세스**
- **드라이버 입력**
- **드라이버 출력**
- **드라이버 인터럽트**
- **드라이버 상태**
- **드라이버 종료**

초기화를 제외하고 각 드라이버 기능 영역은 선택 사항입니다. 또한 각 영역의 정확한 처리 과정은 디바이스 드라이버에만 한정됩니다.

### <a name="driver-initialization"></a>드라이버 초기화 
이 기능 영역은 실제 하드웨어 디바이스 및 드라이버의 내부 데이터 구조를 초기화합니다. 초기화가 완료될 때까지 다른 드라이버 서비스를 호출할 수 없습니다.

> [!IMPORTANT]
> 드라이버의 초기화 함수 구성 요소는 일반적으로 **tx_application_define** 함수 또는 초기화 스레드에서 호출됩니다.

### <a name="driver-control"></a>드라이버 제어 
드라이버가 초기화되고 작동 준비가 완료되면 이 기능 영역이 런타임 제어를 담당합니다. 일반적으로 런타임 제어는 기본 하드웨어 디바이스를 변경하는 것으로 구성됩니다. 예를 들어 직렬 디바이스의 전송 속도를 변경하거나 디스크에서 새 섹터를 찾는 것이 있습니다.

### <a name="driver-access"></a>드라이버 액세스 
일부 디바이스 드라이버는 단일 애플리케이션 스레드에서만 호출됩니다. 이 경우 이 함수 영역은 필요하지 않습니다. 그러나 여러 스레드가 동시에 드라이버에 액세스해야 하는 애플리케이션에서는 디바이스 드라이버에 할당/릴리스 기능을 추가하여 상호 작용을 제어해야 합니다. 또는 애플리케이션이 세마포를 사용하여 드라이버의 접근을 제어하고 드라이버 내부의 추가적인 오버헤드 및 복잡성을 방지할 수 있습니다. 

### <a name="driver-input"></a>드라이버 입력 
이 기능 영역은 모든 디바이스 입력을 담당합니다. 드라이버 입력과 관련된 주요 문제는 일반적으로 입력이 버퍼링되는 방식과 스레드가 이러한 입력을 기다리는 방식과 관련이 있습니다. 

### <a name="driver-output"></a>드라이버 출력 
이 기능 영역은 모든 디바이스 출력을 담당합니다. 드라이버 출력과 관련된 주요 문제는 일반적으로 출력이 버퍼링되는 방식과 스레드가 출력을 수행하기 위해 기다리는 방식과 관련이 있습니다. 

### <a name="driver-interrupts"></a>드라이버 인터럽트 
대부분의 실시간 시스템은 디바이스 입력, 출력, 제어 및 오류 이벤트를 드라이버에 알리기 위해 하드웨어 인터럽트에 의존합니다. 인터럽트는 이러한 외부 이벤트에 대해 보장된 응답 시간을 제공합니다. 인터럽트 대신 드라이버 소프트웨어는 이러한 이벤트에 대해 외부 하드웨어를 주기적으로 확인할 수 있습니다. 이러한 기술을 *폴링* 이라고 합니다. 인터럽트보다 덜 실시간이지만 일부 덜 실시간 애플리케이션에서는 폴링이 적합할 수 있습니다. 

### <a name="driver-status"></a>드라이버 상태 
이 함수 영역은 드라이버 작업과 관련된 런타임 상태와 통계를 제공하는 일을 담당합니다. 이 함수 영역에서 관리하는 정보에는 일반적으로 다음이 포함됩니다. 
- 현재 디바이스 상태
- 입력 바이트
- 출력 바이트
- 디바이스 오류 개수

### <a name="driver-termination"></a>드라이버 종료 
이 기능 영역은 선택 사항입니다. 드라이버 및/또는 물리적 하드웨어 디바이스를 종료해야 하는 경우에만 필요합니다. 종료된 후에는 다시 초기화될 때까지 드라이버를 다시 호출하면 안 됩니다. 

## <a name="simple-driver-example"></a>간단한 드라이버 예제

예제는 디바이스 드라이버를 설명하는 가장 좋은 방법입니다. 이 예제에서 드라이버는 구성 레지스터, 입력 레지스터 및 출력 레지스터가 있는 간단한 직렬 하드웨어 디바이스를 가정합니다. 이 간단한 드라이버 예제는 초기화, 입력, 출력 및 인터럽트 기능 영역을 보여줍니다.

### <a name="simple-driver-initialization"></a>간단한 드라이버 초기화 
간단한 드라이버의 ***tx_sdriver_initialize*** 함수는 드라이버의 입력 및 출력 작업을 관리하는 데 사용되는 두 개의 계산 세마포를 만듭니다. 입력 세마포는 직렬 하드웨어 디바이스에서 문자를 수신할 때 입력 ISR에 의해 설정됩니다. 이 때문에 입력 세마포는 초기 카운트가 0인 상태로 생성됩니다.

반대로 출력 세마포는 직렬 하드웨어 전송 레지스터의 가용성을 나타냅니다. 전송 레지스터가 처음에 사용 가능함을 나타내기 위해 값 1로 생성됩니다.

초기화 함수는 또한 입력 및 출력 알림을 위한 하위 수준의 인터럽트 벡터 처리기 설치를 담당합니다. 다른 ThreadX 인터럽트 서비스 루틴과 마찬가지로, 간단한 드라이버 ISR을 호출하기 전에 하위 수준의 처리기가 * **_tx_thread_context_save** _를 호출해야 합니다. 드라이버 ISR이 반환된 후 하위 수준 처리기는 _*_ _tx_thread_context_restore_**를 호출해야 합니다.

> [!IMPORTANT]
> 다른 드라이버 함수보다 먼저 초기화가 호출되는 것이 중요합니다. 일반적으로 드라이버 초기화는 **tx_application_define** 에서 호출됩니다.

간단한 드라이버의 초기화 소스 코드는 306페이지의 그림 9를 참조하세요.

```C
VOID     tx_sdriver_initialize(VOID)
{

    /* Initialize the two counting semaphores used to control
       the simple driver I/O. */
    tx_semaphore_create(&tx_sdriver_input_semaphore,
                       "simple driver input semaphore", 0);
    tx_semaphore_create(&tx_sdriver_output_semaphore,
                       "simple driver output semaphore", 1);

    /* Setup interrupt vectors for input and output ISRs.
       The initial vector handling should call the ISRs
       defined in this file. */

    /* Configure serial device hardware for RX/TX interrupt
       generation, baud rate, stop bits, etc. */
}
```
**그림 9. 간단한 드라이버 초기화**

### <a name="simple-driver-input"></a>간단한 드라이버 입력 
간단한 드라이버에 대한 입력은 입력 세마포를 중심으로 이루어집니다. 직렬 디바이스 입력 인터럽트가 수신되면 입력 세마포가 설정됩니다. 하나 이상의 스레드가 드라이버의 문자를 기다리고 있는 경우 가장 오래 대기 중인 스레드가 다시 시작됩니다. 대기 중인 스레드가 없으면 스레드가 드라이브 입력 함수를 호출할 때까지 세마포가 설정된 상태로 유지됩니다.

간단한 드라이버 입력 처리에는 몇 가지 제한 사항이 있습니다. 가장 중요한 것은 입력 문자를 삭제될 가능성이 있습니다. 이는 이전 문자가 처리되기 전에 도착한 입력 문자를 버퍼링하는 기능이 없기 때문에 발생할 수 있습니다. 이는 입력 문자 버퍼를 추가하여 쉽게 처리할 수 있습니다.

> [!IMPORTANT]
> 스레드만 **tx_sdriver_input** 함수를 호출할 수 있습니다.

그림 10은 간단한 드라이버 입력과 관련된 소스 코드를 보여 줍니다.

```C
UCHAR     tx_sdriver_input(VOID)
{

    /* Determine if there is a character waiting. If not,
        suspend. */
    tx_semaphore_get(&tx_sdriver_input_semaphore,
                                             TX_WAIT_FOREVER;
    /* Return character from serial RX hardware register. */
    return(*serial_hardware_input_ptr);
}

VOID     tx_sdriver_input_ISR(VOID)
{
    /* See if an input character notification is pending. */
    if (!tx_sdriver_input_semaphore.tx_semaphore_count)
    {
        /* If not, notify thread of an input character. */
        tx_semaphore_put(&tx_sdriver_input_semaphore);
    }
}
```
**그림 10. 간단한 드라이버 입력**

### <a name="simple-driver-output"></a>간단한 드라이버 출력 
출력 처리는 출력 세마포를 활용하여 직렬 디바이스의 송신 레지스터가 비어 있을 때 신호를 보냅니다. 출력 문자를 디바이스에 실제로 기록되기 전에 출력 세마포를 가져옵니다. 이를 사용할 수 없는 경우 이전 전송이 아직 완료되지 않은 것입니다.

출력 ISR은 전송 완료 인터럽트 처리를 담당합니다. 출력 ISR의 처리를 통해 출력 세마포를 설정하므로 다른 문자를 출력할 수 있습니다.

> [!IMPORTANT]
> 스레드만 **tx_sdriver_output** 함수를 호출할 수 있습니다.

그림 11은 간단한 드라이버 출력과 관련된 소스 코드를 보여 줍니다.

```C
VOID     tx_sdriver_output(UCHAR alpha)
{

    /* Determine if the hardware is ready to transmit a
       character. If not, suspend until the previous output
        completes. */
    tx_semaphore_get(&tx_sdriver_output_semaphore,
                                            TX_WAIT_FOREVER);
    /* Send the character through the hardware. */
    *serial_hardware_output_ptr = alpha;
}

VOID     tx_sdriver_output_ISR(VOID)
{
    /* Notify thread last character transmit is
        complete. */
    tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
**그림 11. 간단한 드라이버 출력**

### <a name="simple-driver-shortcomings"></a>간단한 드라이버의 단점 
이러한 간단한 디바이스 드라이버 예제에서는 ThreadX SMP 디바이스 드라이버의 기본 개념을 보여 줍니다. 그러나 단순 디바이스 드라이버는 데이터 버퍼링 또는 오버헤드 문제를 해결하지 않으므로 실제 ThreadX SMP 드라이버를 완전히 보여주지는 않습니다. 다음 섹션에서는 디바이스 드라이버와 관련된 좀 더 복잡한 몇 가지 문제에 대해 설명합니다.

## <a name="advanced-driver-issues"></a>고급 드라이버 문제

앞에서 설명한 대로 디바이스 드라이버에는 애플리케이션의 고유한 요구 사항이 있습니다. 일부 애플리케이션에는 상당한 양의 데이터 버퍼링이 필요할 수 있으며, 다른 애플리케이션은 잦은 디바이스 중단으로 인해 최적화된 드라이버 ISR이 필요할 수 있습니다.

### <a name="io-buffering"></a>I/O 버퍼링 
실시간 포함된 애플리케이션의 데이터 버퍼링에는 상당한 계획이 필요합니다. 일부 디자인은 기본 하드웨어 디바이스에 의해 결정됩니다. 디바이스에서 기본 바이트 I/O를 제공하는 경우 간단한 순환 버퍼가 순서대로 제공됩니다. 그러나 디바이스가 블록, DMA 또는 패킷 I/O를 제공하는 경우 버퍼 관리 체계가 필요할 수 있습니다. 

### <a name="circular-byte-buffers"></a>순환 바이트 버퍼 
순환 바이트 버퍼는 일반적으로 UART와 같은 간단한 직렬 하드웨어 디바이스를 관리하는 드라이버에서 사용됩니다. 이러한 상황에서 두 개의 순환 버퍼(입력용 1개, 출력용 1개)를 사용하는 경우가 가장 많습니다.

각 순환 바이트 버퍼는 바이트 메모리 영역(일반적으로 UCHAR의 배열), 읽기 포인터 및 쓰기 포인터로 구성됩니다. 읽기 포인터와 쓰기 포인터가 버퍼의 동일한 메모리 위치를 참조하는 경우 버퍼가 빈 것으로 간주됩니다. 드라이버 초기화는 버퍼의 시작 주소에 대한 읽기 및 쓰기 버퍼 포인터를 모두 설정합니다.

### <a name="circular-buffer-input"></a>순환 버퍼 입력 
입력 버퍼는 애플리케이션이 준비되기 전에 도착하는 문자를 저장하는 데 사용됩니다. 입력 문자가 수신되면(일반적으로 인터럽트 서비스 루틴에서) 새 문자는 하드웨어 디바이스에서 검색되고 쓰기 포인터가 가리키는 위치의 입력 버퍼에 배치됩니다. 그런 다음, 쓰기 포인터가 버퍼의 다음 위치로 이동합니다. 다음 위치가 버퍼의 끝을 지나는 경우 쓰기 포인터는 버퍼의 시작 부분으로 설정됩니다. 새 쓰기 포인터가 읽기 포인터와 동일한 경우 쓰기 포인터 진행을 취소하여 큐 가득 참 상태를 처리합니다.

드라이버에 대한 애플리케이션 입력 바이트 요청은 먼저 입력 버퍼의 읽기 및 쓰기 포인터를 검사합니다. 읽기 및 쓰기 포인터가 동일한 경우 버퍼가 비어 있는 것입니다. 읽기 포인터가 동일하지 않으면 읽기 포인터가 가리키는 바이트는 입력 버퍼에서 복사되고 읽기 포인터는 다음 버퍼 위치로 이동됩니다. 새 읽기 포인터가 버퍼의 끝을 지나면 시작 부분으로 다시 설정됩니다. 그림 12는 순환 입력 버퍼에 대한 논리를 보여 줍니다.

```C
UCHAR     tx_input_buffer[MAX_SIZE];
UCHAR     tx_input_write_ptr;
UCHAR     tx_input_read_ptr;

/* Initialization.  */
tx_input_write_ptr =  &tx_input_buffer[0];
tx_input_read_ptr =    &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr =  tx_input_write_ptr;
*tx_input_write_ptr++ =  alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr =  &tx_input_buffer[0];  /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr =  save_ptr;  /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
    alpha =  *tx_input_read_ptr++;
    if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
        tx_input_read_ptr =  &tx_input_buffer[0];
}
```
**그림 12. 순환 입력 버퍼에 대한 논리**

> [!IMPORTANT]
> 신뢰할 수 있는 작업의 경우 입출력 순환 버퍼의 읽기 및 쓰기 포인터를 조작할 때 인터럽트를 잠가야 할 수 있습니다.

### <a name="circular-output-buffer"></a>순환 출력 버퍼 
출력 버퍼는 하드웨어 디바이스가 이전 바이트 전송을 완료하기 전에 출력을 위해 도착한 문자를 보관하는 데 사용됩니다. 출력 버퍼 처리는 전송 완료 인터럽트 처리가 출력 읽기 포인터를 조작하는 반면 애플리케이션 출력 요청은 출력 쓰기 포인터를 활용한다는 점을 제외하면 입력 버퍼 처리와 유사합니다. 그렇지 않은 경우 출력 버퍼 처리는 동일합니다. 그림 13은 순환 출력 버퍼에 대한 논리를 보여 줍니다.

```C
UCHAR     tx_output_buffer[MAX_SIZE];
UCHAR     tx_output_write_ptr;
UCHAR     tx_output_read_ptr;

/* Initialization.  */
tx_output_write_ptr =  &tx_output_buffer[0];
tx_output_read_ptr =   &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
    *device_reg =  *tx_output_read_ptr++;
    if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
    tx_output_read_ptr =  &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr =  tx_output_write_ptr;
*tx_output_write_ptr++ =  alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr =  &tx_output_buffer[0];  /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr =  save_ptr;  /* Buffer full!  */
```
**그림 13. 순환 출력 버퍼에 대한 논리**

### <a name="buffer-io-management"></a>버퍼 I/O 관리 
포함된 마이크로프로세서의 성능을 향상시키기 위해 많은 주변 디바이스는 소프트웨어에서 제공하는 버퍼를 사용하여 데이터를 전송하고 수신합니다. 일부 구현에서는 여러 버퍼를 사용하여 개별 데이터 패킷을 전송하거나 수신할 수 있습니다. 

I/O 버퍼의 크기 및 위치는 애플리케이션 및/또는 드라이버 소프트웨어에 의해 결정됩니다. 일반적으로 버퍼는 크기가 고정되며 ThreadX 블록 메모리 풀 내에서 관리됩니다. 그림 14는 일반적인 I/O 버퍼와 할당을 관리하는 ThreadX SMP 블록 메모리 풀을 설명합니다.

```C
typedef struct TX_IO_BUFFER_STRUCT
{

      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
    struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR  tx_buffer_area[TX_MAX_BUFFER_SIZE];
} TX_IO_BUFFER;

TX_BLOCK_POOL tx_io_block_pool;

/* Create a pool of I/O buffers. Assume that the pointer
   "free_memory_ptr"points to an available memory area that
   is 64 KBytes in size. */

tx_block_pool_create(&tx_io_block_pool,
                  "Sample IO Driver Buffer Pool",
                  free_memory_ptr, 0x10000,
                  sizeof(TX_IO_BUFFER));
```
**그림 14. I/O 버퍼**

### <a name="tx_io_buffer"></a>TX_IO_BUFFER 
Typedef TX_IO_BUFFER는 두 개의 포인터로 구성됩니다. **tx_next_packet** 포인터는 입력 또는 출력 목록에서 여러 패킷을 연결하는 데 사용됩니다. _ *_tx_next_buffer_** 포인터는 디바이스에서 데이터의 개별 패킷을 구성하는 버퍼를 연결하는 데 사용됩니다. 풀에서 버퍼를 할당하면 이들 두 포인터는 모두 NULL로 설정됩니다. 또한 일부 디바이스는 버퍼 영역에 실제로 데이터가 얼마나 포함되었는지를 나타내는 다른 필드가 필요할 수 있습니다.

### <a name="buffered-io-advantage"></a>버퍼링된 I/O 장점 
버퍼 I/O 체계의 장점은 무엇일까요? 가장 큰 장점은 디바이스 레지스터와 애플리케이션의 메모리 간에 데이터가 복사되지 않는다는 것입니다. 대신 드라이버는 일련의 버퍼 포인터를 디바이스에 제공합니다. 물리적 디바이스 I/O는 제공된 버퍼 메모리를 직접 활용합니다.

프로세서를 사용하여 정보의 입력 또는 출력 패킷을 복사하는 것은 비용이 많이 들기 때문에 처리량이 많은 I/O 상황에서 피해야 합니다.

버퍼링된 I/O 방식의 또 다른 장점은 입력 및 출력 목록에 전체 조건이 없다는 것입니다. 사용 가능한 모든 버퍼는 한 번에 두 목록 중 하나에 있을 수 있습니다. 이는 장 앞부분에 나오는 단순 바이트 순환 버퍼와 대조됩니다. 각각은 컴파일할 때 크기가 정해져 있습니다.

### <a name="buffered-driver-responsibilities"></a>버퍼링된 드라이버 책임 
버퍼링된 디바이스 드라이버는 연결된 I/O 버퍼 목록 관리에만 관련이 있습니다. 입력 버퍼 목록은 애플리케이션 소프트웨어가 준비되기 전에 수신되는 패킷에 대해 유지됩니다. 반대로, 하드웨어 디바이스가 처리할 수 있는 것보다 빠르게 전송되는 패킷에 대해 출력 버퍼 목록이 유지됩니다. 314페이지의 그림 15는 데이터 패킷의 간단한 입력 및 출력 링크 목록과 각 패킷을 구성하는 버퍼를 보여줍니다.

![버퍼링된 드라이버 책임](media/image11.png)

**그림 15. 입출력 목록**

애플리케이션은 동일한 I/O 버퍼를 사용하여 버퍼링된 드라이버와 인터페이스합니다. 전송 시 애플리케이션 소프트웨어는 드라이버에 전송할 하나 이상의 버퍼를 제공합니다. 애플리케이션 소프트웨어가 입력을 요청하면 드라이버는 I/O 버퍼에 입력 데이터를 반환합니다.

> [!IMPORTANT]
> 일부 애플리케이션에서는 애플리케이션이 드라이버의 입력 버퍼와 사용 가능한 버퍼를 교환해야 하는 드라이버 입력 인터페이스를 빌드하는 것이 유용할 수 있습니다. 이렇게 하면 드라이버 내부의 일부 버퍼 할당 처리를 완화할 수 있습니다.

### <a name="interrupt-management"></a>인터럽트 관리 
일부 애플리케이션에서 디바이스 인터럽트 빈도는 C로 ISR을 쓰거나 각 인터럽트의 ThreadX SMP와 상호 작용하는 것을 금지할 수 있습니다. 예를 들어, 인터럽트된 컨텍스트를 저장하고 복원하는 데 25us가 필요한 경우 인터럽트 빈도가 50us이면 전체 컨텍스트를 저장하지 않는 것이 좋습니다. 이러한 경우 대부분의 디바이스 인터럽트를 처리하는 데 작은 어셈블리 언어 ISR이 사용됩니다. 이러한 낮은 오버헤드 ISR은 필요할 때만 ThreadX SMP와 상호 작용합니다.

3장 끝에 나오는 인터럽트 관리 설명에서 유사한 설명을 찾을 수 있습니다.

> [!NOTE]
> 드라이버 ISR 코드에서 드라이버 코드의 중요한 섹션을 보호하기 위해 인터럽트 잠금을 사용하는 경우 스레드 수준 드라이버 코드는 항상 ISR이 처리되는 것과 동일한 코어에서 실행해야 합니다. 그러지 않으면 TX_DISABLE 및 TX_RESTORE와 같은 내부 ThreadX SMP 기본 형식을 사용하여 코어 간 보호를 기본적으로 제공해야 합니다.

### <a name="thread-suspension"></a>스레드 일시 중단 
이 장 앞부분에 제공된 단순 드라이버 예제에서 문자를 사용할 수 없는 경우 입력 서비스 호출자가 일시 중단됩니다. 일부 애플리케이션에서는 허용되지 않을 수 있습니다.

예를 들어, 드라이버의 입력을 처리하는 스레드에 다른 작업이 있는 경우 드라이버 입력만 일시 중단하는 것이 작동하지 않을 수 있습니다. 대신 드라이버를 사용자 지정하여 다른 처리 요청이 스레드에 생성되는 방식과 유사한 처리를 요청해야 합니다.

대부분의 경우 입력 버퍼가 연결된 목록에 배치되고 입력 이벤트 메시지가 스레드의 입력 큐로 전송됩니다.