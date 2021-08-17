---
title: 2장 - Azure RTOS ThreadX 설치 및 사용
description: 이 장에서는 고성능 Azure RTOS ThreadX 커널의 설치, 설정, 사용과 관련된 다양한 문제에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a88dc75c3b01e8054f72b3e1475791f064eac0ded02b22ccd18dd46da8c7200a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785042"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a>2장 - Azure RTOS ThreadX 설치 및 사용

이 장에서는 고성능 Azure RTOS ThreadX 커널의 설치, 설정, 사용과 관련된 다양한 문제에 대해 설명합니다.

## <a name="host-considerations"></a>호스트 고려 사항

임베디드 소프트웨어는 일반적으로 Windows 또는 Linux(Unix) 호스트 컴퓨터에서 개발됩니다. 애플리케이션이 호스트에서 컴파일, 링크 및 배치된 후 실행할 수 있도록 대상 하드웨어에 다운로드됩니다.

일반적으로 대상 다운로드는 개발 도구의 디버거 내에서 수행됩니다. 다운로드가 완료된 후에 디버거는 대상 실행 제어(이동, 중지, 중단점 등) 뿐만 아니라 메모리 및 프로세서 레지스터에 대한 액세스를 제공합니다.

대부분의 개발 도구 디버거는 JTAG(IEEE 1149.1) 및 BDM(백그라운드 디버그 모드)과 같은 OCD(온-칩 디버그) 연결을 통해 대상 하드웨어와 통신합니다. 또한 디버거는 ICE(회로 내 에뮬레이션) 연결을 통해 대상 하드웨어와 통신합니다. OCD와 ICE 연결은 모두 대상 상주 소프트웨어에 대한 최소 침입으로 강력한 솔루션을 제공합니다.

호스트에서 사용되는 리소스의 경우에는 ThreadX에 대한 소스 코드를 ASCII 형식으로 전달하고 호스트 컴퓨터의 하드 디스크에 약 1MB의 공간이 필요합니다.

## <a name="target-considerations"></a>대상 고려 사항

ThreadX에는 대상에서 2KB~20KB의 ROM(읽기 전용 메모리)이 필요합니다. 또한 목표 RAM(Random Access Memory) 외에 ThreadX 시스템 스택 및 기타 글로벌 데이터 구조를 위한 용량으로 1~2KB가 더 필요합니다.

서비스 호출 시간 초과, 시간 조각화 및 애플리케이션 타이머와 같은 타이머 관련 기능이 작동하려면 기본 대상 하드웨어에서 정기적으로 인터럽트 소스를 제공해야 합니다. 프로세서에 이 용량이 있는 경우 ThreadX에서 활용됩니다. 그렇지 않고 대상 프로세서에서 정기적 인터럽트를 생성할 수 없는 경우 사용자의 하드웨어에서 제공해야 합니다. 타이머 인터럽트의 설정 및 구성은 일반적으로 ThreadX 배포의 ***tx_initialize_low_level*** 어셈블리 파일에 있습니다.

> [!NOTE]
> *ThreadX는 정기적인 타이머 인터럽트 소스를 사용할 수 없더라도 작동합니다. 그렇지만 타이머 관련 서비스는 작동하지 않습니다.*

## <a name="product-distribution"></a>제품 배포

Azure RTOS ThreadX는 <https://github.com/azure-rtos/threadx/>에 있는 퍼블릭 소스 코드 리포지토리에서 가져올 수 있습니다

다음은 리포지토리에 있는 몇 가지 중요한 파일 목록입니다.

| 파일 이름 | Description |
|------------------- | ----------- |
| **tx_api.h**                      | 모든 시스템 등식, 데이터 구조 및 서비스 프로토타입이 포함되어 있는 C 헤더 파일입니다.                                                             |
| **tx_port.h**                     | 모든 개발 도구 및 대상 특정 데이터 정의 및 구조를 포함하는 C 헤더 파일입니다.                                                 |
| **demo_threadx.c**                | 작은 데모 애플리케이션을 포함하는 C 파일입니다.                                                                                                       |
| **tx.a(또는 tx.lib)**              | *표준* 패키지와 함께 배포되는 Threadx C 라이브러리의 이진 버전입니다.                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
>모든 파일 이름은 소문자로 되어 있습니다. 이 명명 규칙을 사용하면 명령을 Linux(Unix) 개발 플랫폼으로 좀 더 쉽게 변환할 수 있습니다.

## <a name="threadx-installation"></a>ThreadX 설치

ThreadX는 GitHub 리포지토리를 로컬 머신에 복제하여 설치됩니다. 다음은 PC에서 ThreadX 리포지토리의 복제본을 만들기 위한 일반적인 구문입니다.

```c
    git clone https://github.com/azure-rtos/threadx
```

또는 GitHub 기본 페이지의 다운로드 단추를 사용하여 리포지토리의 복사본을 다운로드할 수 있습니다.

또한 온라인 리포지토리의 프런트 페이지에서 ThreadX 라이브러리를 빌드하기 위한 지침을 찾을 수 있습니다.

> [!NOTE]
> *애플리케이션 소프트웨어는 ThreadX 라이브러리 파일(일반적으로 **tx.a** 또는 **tx.lib**) 및 C 포함 파일 *_tx_api.h_* 및 _*_tx_port.h_*_ 에 액세스할 수 있어야 합니다. 이 작업은 개발 도구에 대한 적절한 경로를 설정하거나 이러한 파일을 애플리케이션 개발 영역으로 복사하여 수행합니다._

## <a name="using-threadx"></a>ThreadX 사용

ThreadX를 사용하려면 컴파일하는 동안 애플리케이션 코드가 ***tx_api.h** _를 포함하고 ThreadX 런타임 라이브러리 _*_tx.a_*_(또는 _*_tx.lib_**)와 연결해야 합니다.

ThreadX 애플리케이션을 빌드하는 데는 4가지 단계가 필요합니다.

1. ThreadX 서비스 또는 데이터 구조를 사용하는 모든 애플리케이션 파일에 ***tx_api.h*** 파일을 포함합니다.

1. 표준 C ***main** _ 함수를 만듭니다. 이 함수는 결과적으로 _ *_tx_kernel_enter_**를 호출하여 Threadx를 시작해야 합니다. ThreadX가 포함되지 않은 애플리케이션별 초기화는 커널에 들어가기 전에 추가될 수 있습니다.

      > [!IMPORTANT]
      > *ThreadX entry 함수 ***tx_kernel_enter** _는 반환되지 않습니다. 따라서 그 뒤에는 처리 또는 함수 호출을 배치하지 않아야 합니다._

1. ***tx_application_define*** 함수를 만듭니다. 초기 시스템 리소스가 만들어지는 위치입니다. 시스템 리소스의 예로는 스레드, 큐, 메모리 풀, 이벤트 플래그 그룹, 뮤텍스 및 세마포가 있습니다.

1. 애플리케이션 소스를 컴파일하고 ThreadX 런타임 라이브러리 ***tx.lib*** 에 연결합니다. 결과 이미지를 대상에 다운로드하여 실행할 수 있습니다.

## <a name="small-example-system"></a>간단한 예제 시스템

그림 1의 작은 예제 시스템은 우선 순위가 3인 단일 스레드의 생성을 보여 줍니다. 스레드가 실행되고, 카운터가 증가한 후 1번의 클럭 틱을 대기합니다.
이 프로세스는 무한히 계속됩니다.

```c
#include "tx_api.h"
unsigned long my_thread_counter = 0;
TX_THREAD my_thread;
main( )
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter( );
}
void tx_application_define(void *first_unused_memory)
{
    /* Create my_thread! */
    tx_thread_create(&my_thread, "My Thread",
    my_thread_entry, 0x1234, first_unused_memory, 1024,
    3, 3, TX_NO_TIME_SLICE, TX_AUTO_START);
}
void my_thread_entry(ULONG thread_input)
{
    /* Enter into a forever loop. */
    while(1)
    {
        /* Increment thread counter. */
        my_thread_counter++;
        /* Sleep for 1 tick. */
        tx_thread_sleep(1);
    }
}
```

**그림 1. 애플리케이션 개발용 템플릿**

간단한 예제이지만 실제 애플리케이션 개발에 적합한 템플릿을 제공합니다.

## <a name="troubleshooting"></a>문제 해결

각 ThreadX 포트는 데모 애플리케이션과 함께 제공됩니다. 항상 실제 대상 하드웨어 또는 시뮬레이트된 환경에서 데모 시스템을 실행하는 것이 좋습니다.

데모 시스템이 제대로 실행되지 않을 경우 다음의 문제 해결 팁을 참조하세요.

1. 데모가 어느 정도 실행되고 있는지 확인합니다.
1. 스택 크기를 늘립니다(데모보다는 실제 애플리케이션 코드에서 더 중요함).
1. TX_ENABLE_STACK_CHECKING을 정의하여 ThreadX 라이브러리를 다시 빌드합니다. 이렇게 하면 기본 제공 ThreadX 스택 검사가 사용하도록 설정됩니다.
1. 최근 변경 내용을 일시적으로 무시하여 문제가 사라지거나 변경되는지 확인합니다. 이러한 정보는 지원 엔지니어에게 유용합니다.

"[고객 지원 센터](about-this-guide.md#customer-support-center)"에 설명된 절차에 따라 문제 해결 단계에서 수집한 정보를 보냅니다.

## <a name="configuration-options"></a>구성 옵션

ThreadX를 사용하여 ThreadX 라이브러리 및 애플리케이션을 빌드할 때 몇 가지 구성 옵션이 있습니다. 아래 옵션은 애플리케이션 소스, 명령줄 또는 ***tx_user.h*** 포함 파일 내에서 정의할 수 있습니다.

> [!IMPORTANT]
> ****tx_user.h** _에 정의된 옵션은 애플리케이션 및 ThreadX 라이브러리가 *TX_INCLUDE_USER_DEFINE_FILE* 이 정의된 상태로 빌드된 경우에만 적용됩니다.*

### <a name="smallest-configuration"></a>가장 작은 구성

가장 작은 코드 크기의 경우 다음 ThreadX 구성 옵션을 고려해야 합니다(다른 모든 옵션은 없음).

```c
TX_DISABLE_ERROR_CHECKING
TX_DISABLE_PREEMPTION_THRESHOLD
TX_DISABLE_NOTIFY_CALLBACKS
TX_DISABLE_REDUNDANT_CLEARING
TX_DISABLE_STACK_FILLING
TX_NOT_INTERRUPTABLE
TX_TIMER_PROCESS_IN_ISR
```

### <a name="fastest-configuration"></a>가장 빠른 구성

가장 빠른 실행을 위해 이전의 가장 작은 구성에 사용되는 것과 동일한 구성 옵션이 사용되지만 다음 옵션을 고려할 수도 있습니다.

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

[자세한 구성 옵션](#detailed-configuration-options)이 제공됩니다.

### <a name="global-time-source"></a>글로벌 시간 소스

다른 Microsoft Azure RTOS 제품(FileX, NetX, GUIX, USBX 등)의 경우 ThreadX는 1초를 나타내는 ThreadX 타이머 틱 수를 정의합니다. 다른 제품을 사용할 때는 이 상수를 기준으로 다른 시간 요구 사항이 발생합니다. 기본적으로 이 값은 100으로, 10ms의 정기적 인터럽트가 간주됩니다. 사용자는 ***tx_port.h*** 에서 또는 IDE나 명령줄 내에서 원하는 값으로 TX_TIMER_TICKS_PER_SECOND를 정의하여 이 값을 재정의할 수 있습니다.

### <a name="detailed-configuration-options"></a>자세한 구성 옵션

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

정의된 경우 이 옵션을 사용하여 바이트 풀에 대한 성능 정보를 수집할 수 있습니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

정의된 경우 이 옵션을 사용하여 바이트 풀에 대한 성능 정보를 수집할 수 있습니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_DISABLE_ERROR_CHECKING**

기본 서비스 호출 오류 검사를 무시합니다. 애플리케이션 소스에 정의된 경우 모든 기본 매개 변수 오류 검사가 사용하지 않도록 설정됩니다. 이렇게 하면 성능이 30% 정도 향상되고 이미지 크기도 줄어들 수 있습니다.

> [!NOTE]
> 애플리케이션이 외부 입력에서 파생된 입력 매개 변수를 비롯하여 모든 입력 매개 변수가 항상 유효할 것임을 절대적으로 보장할 수 있는 경우에만 오류 검사를 사용하지 않도록 설정하는 것이 안전합니다. 오류 검사를 사용하지 않도록 설정하고 API에 잘못된 입력을 제공하면 결과 동작은 정의되지 않으며 메모리 손상이나 시스템 충돌을 야기할 수 있습니다.

> [!NOTE]
> *오류 검사를 사용하지 않도록 설정해도 영향을 받지 않는 ThreadX API 반환 값은 4장의 각 API 설명에 대한 "반환 값" 섹션에서 굵게 표시됩니다. TX_DISABLE_ERROR_CHECKING 옵션을 사용하여 오류 검사를 사용하지 않도록 설정한 경우 굵게 표시되지 않은 반환 값은 무효 처리됩니다.*

**TX_DISABLE_NOTIFY_CALLBACKS**

정의되면 다양 한 ThreadX 개체에 대해 알림 콜백이 사용하지 않도록 설정됩니다. 이 옵션을 사용하면 코드 크기가 약간 줄어들고 성능이 향상됩니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_DISABLE_PREEMPTION_THRESHOLD**

정의되면 선점 임계값 기능이 사용하지 않도록 설정되고 코드 크기가 약간 줄어들며 성능이 향상됩니다. 물론, 선점 임계값 기능은 더 이상 사용할 수 없게 됩니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_DISABLE_REDUNDANT_CLEARING**

정의되면 ThreadX 글로벌 C 데이터 구조를 0으로 초기화하는 논리가 제거됩니다. 이 옵션은 컴파일러의 초기화 코드가 초기화되지 않은 모든 C 전역 데이터를 0으로 설정하는 경우에만 사용해야 합니다. 이 옵션을 사용하면 초기화 중에 코드 크기가 약간 줄어들고 성능이 향상됩니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_DISABLE_STACK_FILLING**

정의되면 생성될 때 각 스레드 스택의 각 바이트에 0xEF 값을 배치할 수 없습니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_ENABLE_EVENT_TRACE**

정의되면 ThreadX는 TraceX 추적 버퍼를 만들기 위한 이벤트 수집 코드를 사용하도록 설정합니다.

**TX_ENABLE_STACK_CHECKING**

정의되면 사용된 스택 양에 대한 분석과 스택 영역 앞뒤에 있는 데이터 패턴 "펜스"의 검사를 포함하는 ThreadX 런타임 스택 검사가 사용하도록 설정됩니다. 스택 오류가 검색되면 등록된 애플리케이션 스택 오류 처리기가 호출됩니다. 이 옵션을 선택하면 오버헤드 및 코드 크기가 약간 증가합니다. 자세한 내용은 ***tx_thread_stack_error_notify*** API 함수를 참조하세요. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**

정의되면 이벤트 플래그 그룹에 대한 성능 정보를 수집할 수 있습니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_INLINE_THREAD_RESUME_SUSPEND**

정의되면 ThreadX는 인라인 코드를 통해 ***tx_thread_resume** _ 및 _ *_tx_thread_suspend_** API 호출을 향상시킵니다. 이렇게 하면 코드 크기는 늘어나지만 이러한 두 API 호출의 성능이 향상됩니다.

**TX_MAX_PRIORITIES**

ThreadX에 대한 우선 순위 수준을 정의합니다. 유효한 값의 범위는 32에서 1024(경계값 포함) 사이이며 32씩 균등하게 *나눌 수 있어야 합니다*. 지원되는 우선 순위 수준 수를 늘리면 32개 우선 순위 그룹마다 RAM 사용량이 128바이트씩 늘어납니다. 그러나 성능에는 거의 영향을 주지 않습니다. 기본적으로 이 값은 32개 우선 순위 수준으로 설정됩니다.

**TX_MINIMUM_STACK**

최소 스택 크기(바이트)를 정의합니다. 스레드를 만들 때 오류 검사에 사용됩니다. 기본값은 포트 전용이며 ***tx_port.h*** 에서 찾을 수 있습니다.

**TX_MISRA_ENABLE**

정의되면 ThreadX는 MISRA C 호환 규칙을 활용합니다. 자세한 내용은 ***ThreadX_MISRA_Compliance.pdf*** 를 참조하세요.

**TX_MUTEX_ENABLE_PERFORMANCE_INFO**

정의되면 뮤텍스에 대한 성능 정보를 수집할 수 있습니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_NO_TIMER**

정의되면 ThreadX 타이머 논리를 완전히 사용할 수 없게 됩니다. 이 옵션은 ThreadX 타이머 기능(스레드 절전, API 시간 제한, 시간 조각화 및 애플리케이션 타이머)이 사용되지 않는 경우에 유용합니다. **TX_NO_TIMER** 가 지정되면 **TX_TIMER_PROCESS_IN_ISR** 옵션도 정의해야 합니다.

**TX_NOT_INTERRUPTABLE**

정의되면 ThreadX는 인터럽트 잠금 시간을 최소화하려고 시도하지 않습니다. 이로 인해 실행 속도가 빨라지지만 인터럽트 잠금 시간이 약간 늘어납니다.

**TX_QUEUE_ENABLE_PERFORMANCE_INFO**

정의되면 큐에 대한 성능 정보를 수집할 수 있습니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_REACTIVATE_INLINE**

정의되면 함수 호출을 사용하는 대신 ThreadX 타이머 인라인이 다시 활성화됩니다. 이렇게 하면 성능은 향상되지만 코드 크기는 약간 더 커집니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**

정의되면 세마포에 대한 성능 정보를 수집할 수 있습니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_THREAD_ENABLE_PERFORMANCE_INFO**

정의되면 스레드에 대한 성능 정보를 수집할 수 있습니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_TIMER_ENABLE_PERFORMANCE_INFO**

정의되면 타이머에 대한 성능 정보를 수집할 수 있습니다. 이 옵션은 기본적으로 정의되지 않습니다.

**TX_TIMER_PROCESS_IN_ISR**

정의되면 ThreadX에 대한 내부 시스템 타이머 스레드가 제거됩니다. 이로 인해 타이머 스택과 제어 블록이 더 이상 필요하지 않기 때문에 타이머 이벤트에 대한 성능이 향상되고 RAM 요구 사항은 더 줄어듭니다. 그러나 이 옵션을 사용하면 모든 타이머 만료 처리가 타이머 ISR 수준으로 이동됩니다. 이 옵션은 기본적으로 정의되지 않습니다.

> [!NOTE]
> 타이머에서 허용되는 서비스는 ISR에서 허용되지 않을 수 있으므로 이 옵션을 사용하는 경우 허용되지 않을 수 있습니다.

**TX_TIMER_THREAD_PRIORITY**

내부 ThreadX 시스템 타이머 스레드의 우선 순위를 정의합니다. 기본값은 ThreadX에서 가장 높은 우선 순위를 나타내는 우선 순위 0입니다. 기본값은 ***tx_port.h*** 에 정의되어 있습니다.

**TX_TIMER_THREAD_STACK_SIZE**

내부 ThreadX 시스템 타이머 스레드의 스택 크기(바이트)를 정의합니다. 이 스레드는 모든 서비스 호출 시간 제한뿐만 아니라 모든 스레드 대기 요청을 처리합니다. 또한 모든 애플리케이션 타이머 콜백 루틴은 이 컨텍스트에서 호출됩니다. 기본값은 포트 전용이며 ***tx_port.h*** 에서 찾을 수 있습니다.

## <a name="threadx-version-id"></a>ThreadX 버전 ID

프로그래머는 ***tx_port.h** _ 파일을 조사하여 ThreadX 버전을 가져올 수 있습니다. 또한 이 파일에는 해당 포트의 버전 기록도 포함됩니다. 애플리케이션 소프트웨어는 전역 문자열 _*_tx_version_id**를 검사하여 ThreadX 버전을 가져올 수 있습니다.
