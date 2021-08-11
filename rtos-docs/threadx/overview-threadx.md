---
title: Azure RTOS ThreadX 이해
description: Azure ThreadX는 깊게 포함된 애플리케이션용으로 특별히 설계된 고급 RTOS(실시간 운영 체제)에 대해 알아보세요.
author: philmea
ms.author: philmea
ms.date: 6/9/2021
ms.service: rtos
ms.topic: overview
ms.custom: contperf-fy21q4
ms.openlocfilehash: 4b6c8df5133f16cf3ed4006c12433ac426453cb5
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178207"
---
# <a name="overview-of-azure-rtos-threadx"></a>Azure RTOS ThreadX 개요

Azure RTOS ThreadX는 Microsoft의 고급 산업용 RTOS(실시간 운영 체제)입니다. 깊게 포함된, 실시간 및 IoT 애플리케이션을 위해 특별히 설계되었습니다. Azure RTOS ThreadX는 고급 예약, 통신, 동기화, 타이머, 메모리 관리 및 인터럽트 관리 기능을 제공합니다. 또한 Azure RTOS ThreadX에는 picokernel™ 아키텍처, preemption-threshold™ 예약, event-chaining™, 실행 프로파일링, 성능 메트릭 및 시스템 이벤트 추적을 포함한 많은 고급 기능이 있습니다. Azure RTOS ThreadX는 뛰어난 사용 편의성과 함께 가장 까다로운 임베디드 애플리케이션에 이상적인 선택입니다. Azure RTOS ThreadX는 소비자 디바이스, 의료 전자 제품 및 산업 제어 장비를 포함한 다양한 제품에 수십억 개 이상이 배포되었습니다.

## <a name="threadx-footprint"></a>ThreadX 공간

Azure RTOS ThreadX에는 매우 적은 2KB 명령 영역과 RAM 1KB의 최소 메모리 공간이 있습니다. 이 작은 크기는 주로 계층화되지 않은 picokernel 아키텍처와 자동 크기 조정 때문입니다. 자동 크기 조정은 애플리케이션에서 사용되는 서비스(및 지원 인프라)만 링크 타임에서 최종 이미지에 포함된다는 것을 의미합니다.

몇 가지 일반적인 Azure RTOS ThreadX 크기 특성은 다음과 같습니다.

|Azure RTOS ThreadX 서비스  |일반적인 크기(바이트)  |
|---------|---------|
|Core Services(필수) |2,000  |
|큐 서비스  |900  |
|이벤트 플래그 서비스  |900  |
|세마포 서비스  |450  |
|뮤텍스 서비스  |1,200  |
|블록 메모리 서비스  |550  |
|바이트 메모리 서비스  |900  |

## <a name="threadx-execution-speed"></a>ThreadX 실행 속도

Azure RTOS ThreadX는 대부분의 인기 있는 프로세서에서 초소형 컨텍스트 전환을 달성하며 전반적으로 다른 상용 RTOS보다 빠릅니다. Azure RTOS ThreadX는 속도가 빠를 뿐만 아니라 결정성도 뛰어납니다. 200개의 스레드가 준비되어 있든 단 한 개만 준비되어 있든 동일한 빠른 성능을 달성합니다.

Azure RTOS ThreadX의 일반적인 성능 특성은 다음과 같습니다.

* 빠른 부팅: Azure RTOS ThreadX는 120 사이클 미만으로 부팅됩니다.
* 선택적 기본 오류 검사 제거: 컴파일 타임에 기본 Azure RTOS ThreadX 오류 검사를 건너뛸 수 있습니다. 이는 애플리케이션 코드가 확인되고 더 이상 각 매개 변수에 대한 오류 검사가 필요하지 않을 때 유용할 수 있습니다. 오류 검사 건너뛰기는 시스템 전체가 아닌 컴파일 단위에서 수행할 수 있습니다.
* Picokernel 디자인: 서비스가 서로 계층화되지 않으므로 불필요한 함수 호출 오버헤드가 제거됩니다.
* 최적화된 인터럽트 처리: 선점이 필요한 경우가 아니면 ISR 진입/종료 시 스크래치 레지스터만 저장/복원됩니다.
* 최적화된 API 처리:

    |Azure RTOS ThreadX 서비스  |서비스 시간(마이크로초)*  |
    |---------|---------|
    |스레드 일시 중단  |0.6  |
    |스레드 계속하기  |0.6  |
    |큐 송신  |0.3  |
    |큐 수신  |0.3  |
    |세마포 가져오기  |0.2  |
    |세마포 배치  |0.2  |
    |컨텍스트 전환  |0.4  |
    |인터럽트 응답  |0.0 – 0.6  |

    **200MHz로 실행되는 일반적인 프로세서에 따른 성능 수치*.

## <a name="advanced-technology"></a>고급 기술

Azure RTOS ThreadX는 preemption-threshold 예약으로 잘 알려져 있습니다. 이 기능은 Azure RTOS ThreadX의 고유한 것이며 광범위한 학술 연구의 주제였습니다. Yun Wang(컨커디아 대학교) 및 Manas Saksena(피츠버그 대학교)의 [Preemption Threshold를 사용하여 고정 우선 순위 작업 예약(Scheduling Fixed-Priority Tasks with Preemption Threshold)](https://ieeexplore.ieee.org/document/811269) 논문에서 자세히 알아볼 수 있습니다.

Azure RTOS ThreadX의 주요 기능:

* 완전하고 포괄적인 멀티태스킹 기능 제공
  * 스레드, 애플리케이션 타이머, 메시지 큐, 세마포 계산, 뮤텍스, 이벤트 플래그, 블록 및 바이트 메모리 풀
* 우선 순위 기반의 선점 예약
* 우선 순위 유연성 – 최대 1024개의 우선 순위 수준
* 협력 예약
* Preemption-Threshold – Azure RTOS ThreadX만의 고유한 기능으로 컨텍스트 스위치를 줄이고 예약 가능성을 보장할 수 있습니다(학술 연구 기준).
* Azure RTOS ThreadX MODULES를 통한 메모리 보호
* 완전 결정적
* 이벤트 추적 – 마지막 *n* 개의 시스템/애플리케이션 이벤트 캡처
* Event Chaining – 각 Azure RTOS ThreadX 통신 또는 동기화 개체에 대해 애플리케이션별 "알림" 콜백 함수를 등록합니다.
* 선택적 메모리 보호 기능이 있는 Azure RTOS ThreadX MODULES
* 런타임 성능 메트릭
  * 스레드 재개 수
  * 스레드 일시 중단 수
  * 요청된 스레드 선점 수
  * 비동기 스레드 인터럽트 선점 수
  * 스레드 우선 순위 반전 수
  * 스레드 포기 수
* EPK(실행 프로필 키트)
* 별도의 인터럽트 스택
* 런타임 스택 분석
* 최적화된 타이머 인터럽트 처리

## <a name="multicore-support-amp--smp"></a>멀티 코어 지원(AMP 및 SMP)

표준 Azure RTOS ThreadX는 종종 AMP(비대칭적 다중 처리) 방식으로 사용되며, Azure RTOS ThreadX 및 애플리케이션(또는 Linux)의 별도 복사본이 각 코어에서 실행되고 공유 메모리 또는 OpenAMP(Azure RTOS ThreadX는 OpenAMP를 지원)와 같은 프로세서 간 통신 메커니즘을 통해 서로 통신합니다.

프로세서를 로드하는 것이 매우 동적인 환경에서는 다음 프로세서 제품군에 대해 Azure RTOS ThreadX SMP(대칭적 다중 처리)를 사용할 수 있습니다.

* ARM Cortex-Ax
* ARM Cortex-Rx
* ARM Cortex-A5x 64비트
* MIPS 34 K, 1004 K 및 interAptiv
* PowerPC
* Synopsys ARC HS
* x86

Azure RTOS ThreadX SMP가 *n* 개의 프로세서에서 동적 부하 분산을 수행합니다. 모든 Azure RTOS ThreadX 리소스(큐, 세마포, 이벤트 플래그, 메모리 풀 등)를 모든 코어의 모든 스레드에서 액세스할 수 있도록 허용합니다. Azure RTOS ThreadX SMP는 모든 코어에서 전체 Azure RTOS ThreadX API를 사용하고 SMP 작업에 적용되는 다음과 같은 새 API를 도입합니다.

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Azure RTOS ThreadX 모듈을 통한 메모리 보호

Azure RTOS ThreadX 모듈이라는 추가 기능 제품을 사용하면 하나 이상의 애플리케이션 스레드를 대상에서 동적으로 로드하고 실행할 수 있는 "모듈"에 묶을 수 있습니다.

모듈을 사용하면 필드 업그레이드, 버그 수정 및 프로그램 분할을 사용하여 많은 애플리케이션이 활성 스레드에 필요한 메모리만 차지할 수 있습니다.

또한 모듈에는 Azure RTOS ThreadX 자체와 별개의 주소 공간이 있습니다. 이를 통해 Azure RTOS ThreadX는 모듈 주변에 메모리 보호(MPU 또는 MMU를 통해)를 배치하여 실수로 모듈 외부에 액세스해도 다른 소프트웨어 구성 요소가 손상되지 않도록 할 수 있습니다.

## <a name="misra-compliant"></a>MISRA 준수

Azure RTOS ThreadX 및 Azure RTOS ThreadX SMP 소스 코드는 MISRA-C: 2004 및 MISRA C:2012를 준수합니다. MISRA C는 C 프로그래밍 언어를 사용하는 중요 시스템에 대한 프로그래밍 지침 세트입니다. 원래의 MISRA C 지침은 주로 자동차 분야를 대상으로 했지만, MISRA C는 이제 모든 안전 중요 분야에 적용할 수 있는 것으로 널리 인식되고 있습니다. Azure RTOS ThreadX는 MISRA-C: 2004 및 MISRA C:2012의 모든 필수 및 의무 규칙을 준수합니다.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Misra 인증":::

## <a name="supports-most-popular-tools"></a>가장 널리 사용되는 도구 지원

Azure RTOS ThreadX는 IAR의 Embedded Workbench를 비롯하여 가장 널리 사용되는 임베디드 개발 도구를 지원하며, 가장 포괄적인 Azure RTOS ThreadX 커널 인식을 제공합니다. 기타 도구 통합에는 GNU(GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench, Imagination Codescape, Renesas e2studio, Metaware SeeCode, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore 및 모든 아날로그 디바이스가 포함됩니다.

## <a name="adaptation-layer-for-threadx"></a>ThreadX에 대한 적응 계층

다양한 레거시 RTOS API(FreeRTOS, POSIX, OSEK 등)에 ThreadX [적응 계층](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers)을 사용하여 Azure RTOS로의 애플리케이션 마이그레이션 문제를 완화할 수 있습니다.

> [!div class="nextstepaction"]
> [Azure RTOS ThreadX 소개](chapter1.md)