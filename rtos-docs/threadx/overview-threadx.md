---
title: Azure RTOS ThreadX 이해
description: Azure ThreadX는 깊게 포함된 애플리케이션용으로 특별히 설계된 고급 RTOS(실시간 운영 체제)입니다.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: acee58d9c48cb7a66993aaa5dc4a565dfe96234d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812162"
---
# <a name="overview-of-azure-rtos-threadx"></a>Azure RTOS ThreadX 개요

Azure RTOS ThreadX는 심층 임베디드, 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 Microsoft의 고급 산업용 RTOS(실시간 운영 체제)입니다. Azure RTOS ThreadX는 고급 예약, 통신, 동기화, 타이머, 메모리 관리 및 인터럽트 관리 기능을 제공합니다. 또한 Azure RTOS ThreadX에는 picokernel™ 아키텍처, preemption-threshold™ 예약, event-chaining™, 실행 프로파일링, 성능 메트릭 및 시스템 이벤트 추적을 포함한 많은 고급 기능이 있습니다. Azure RTOS ThreadX는 뛰어난 사용 편의성과 함께 가장 까다로운 임베디드 애플리케이션에 이상적인 선택입니다. 2017년 현재 Azure RTOS ThreadX는 소비자 디바이스, 의료 전자 제품 및 산업 제어 장비를 포함한 다양한 제품에 62억 개 이상이 배포되었습니다.

## <a name="api-protocols"></a>API 프로토콜

### <a name="azure-rtos-threadx-api"></a>Azure RTOS ThreadX API

* 직관적이고 일관적인 API
* 명사-동사 명명 규칙
* 모든 API에는 Azure RTOS ThreadX로 쉽게 식별할 수 있도록 *tx_* 가 앞에 옵니다.
* 차단 API에는 선택적 스레드 시간 제한이 있습니다.
* 많은 API를 애플리케이션 ISR에서 직접 사용할 수 있습니다.

### <a name="azure-rtos-threadx-services"></a>Azure RTOS ThreadX 서비스

* 동적 스레드 만들기
* 스레드 수 제한 없음
* 주 스레드 API에는 다음이 포함됩니다.
  * tx_thread_create
  * tx_thread_delete
  * tx_thread_preemption_change
  * tx_thread_priority_change
  * tx_thread_relinquish
  * tx_thread_reset
  * tx_thread_resume
  * tx_thread_sleep
  * tx_thread_suspend
  * tx_thread_terminate
  * tx_thread_wait_abort
* 추가 정보 및 성능 API

### <a name="message-queues"></a>메시지 큐

* 동적 큐 만들기
* 큐 수 제한 없음
* 값(또는 포인터를 통한 참조)으로 복사된 메시지
* 1 ~ 16개의 32비트 단어의 메시지 크기
* 비거나 가득 찼을 때 선택적 스레드 일시 중단
* 모든 일시 중단 시 선택적 시간 제한
* 주 메시지 큐 API에는 다음이 포함됩니다.
  * tx_queue_create
  * tx_queue_delete
  * tx_queue_flush
  * tx_queue_front_send
  * tx_queue_receive
  * tx_queue_send_notify
* 추가 정보 및 성능 API

### <a name="counting-semaphores"></a>세마포 수 계산

* 동적 세마포 만들기
* 세마포 수 제한 없음
* 32비트 세마포 계산(0 ~ 4,294,967,295)
* 소비자-생산자 또는 리소스 보호 지원
* 세마포를 사용할 수 없을 때 선택적 스레드 일시 중단
* 모든 일시 중단 시 선택적 시간 제한
* 주 세마포 API에는 다음이 포함됩니다.
  * tx_semaphore_create
  * tx_semaphore_delete
  * tx_semaphore_get
  * tx_semaphore_put
  * tx_semaphore_put_notify
* 추가 정보 및 성능 API

### <a name="mutexes"></a>뮤텍스

* 동적 뮤텍스 만들기
* 뮤텍스 수 제한 없음
* 중첩된 리소스 보호 지원
* 선택적 우선 순위 상속 지원
* 뮤텍스를 사용할 수 없을 때 선택적 스레드 일시 중단
* 모든 일시 중단 시 선택적 시간 제한
* 기본 뮤텍스 API는 다음과 같습니다.
  * tx_mutex_create
  * tx_mutex_delete
  * tx_mutex_get
  * tx_mutex_put
* 추가 정보 및 성능 API

### <a name="event-flags"></a>이벤트 플래그

* 동적 이벤트 플래그 그룹 만들기
* 이벤트 플래그 그룹 수 제한 없음
* 단일 스레드 또는 다중 스레드 동기화
* 원자성 가져오기 및 지우기 지원
* AND/OR 이벤트 세트의 선택적 다중 스레드 일시 중단
* 모든 일시 중단 시 선택적 시간 제한
* 기본 이벤트 플래그 API는 다음과 같습니다.
  * tx_event_flags_create
  * tx_event_flags_delete
  * tx_event_flags_get
  * tx_event_flags_set
  * tx_event_flags_set_notify
* 추가 정보 및 성능 API

### <a name="block-memory-pools"></a>메모리 풀 차단

* 동적 블록 풀 만들기
* 블록 풀 수 제한 없음
* 고정 크기 블록 크기 또는 풀 크기 제한 없음
* 가능한 가장 빠른 메모리 할당/할당 취소
* 비었을 때 선택적 스레드 일시 중단
* 모든 일시 중단 시 선택적 시간 제한
* 기본 블록 풀 API는 다음과 같습니다.
  * tx_block_pool_create
  * tx_block_pool_delete
  * tx_block_allocate
  * tx_block_release
* 추가 정보 및 성능 API

### <a name="byte-memory-pools"></a>바이트 메모리 풀

* 동적 바이트 풀 만들기
* 바이트 풀 수 제한 없음
* 바이트 풀 크기 제한 없음
* 가장 유연한 가변 길이 메모리 할당/할당 취소
* 할당 크기 인근 지원
* 비었을 때 선택적 스레드 일시 중단
* 모든 일시 중단 시 선택적 시간 제한
* 기본 바이트 풀 API는 다음과 같습니다.
  * tx_byte_pool_create
  * tx_byte_pool_delete
  * tx_byte_allocate
  * tx_byte_release
* 추가 정보 및 성능 API

### <a name="application-timers"></a>애플리케이션 타이머

* 동적 타이머 만들기
* 타이머 수 제한 없음
* 정기 또는 원샷 타이머 지원
* 정기 타이머의 초기 만료 값은 다를 수 있음
* 타이머 활성화 또는 비활성화 시 검색 없음
* 모든 타이머가 한 대의 하드웨어 타이머 인터럽트에서 구동
* 기본 타이머 API는 다음과 같습니다.
  * tx_timer_create
  * tx_timer_delete
  * tx_timer_activate
  * tx_timer_change
  * tx_timer_deactivate
* 추가 정보 및 성능 API

### <a name="azure-rtos-threadx-core-scheduler"></a>Azure RTOS ThreadX Core Scheduler

* 최소 2KB FLASH, 1KB RAM 메모리 공간
* 마이크로 초 미만의 빠른 컨텍스트 전환
* 스레드 수에 관계없이 완전 결정적
* 우선 순위 기반의 완전한 선점 예약
* 32개의 기본 우선 순위 수준, 선택적으로 최대 1024개의 수준
* 우선 순위 수준 내 협력 예약(FIFO)
* Preemption-threshold 기술
* 다음을 포함하는 선택적 타이머 서비스:
  * 스레드별 선택적 시간-조각
  * 모든 차단에 대한 선택적 시간 제한
  * 하드웨어 타이머 인터럽트에 API 필요
* 실행 프로파일링
* 시스템 수준 추적
* 여러 표준으로 인증된 안전

## <a name="most-deployed-rtos"></a>가장 많이 배포된 RTOS

선도적인 M2M 시장 인텔리전스 회사인 VDC Research에 따르면 Azure RTOS ThreadX는 전 세계적으로 62억 개 이상의 배포를 보유하고 있습니다. Azure RTOS ThreadX의 인기는 신뢰도, 품질, 크기, 성능, 고급 기능, 사용 편의성 및 전반적인 출시 시간 이점에 대한 증거입니다.

> *"우리는 회사 창립 이래 무선 및 IoT 시장에서 THREADX의 성장 궤적을 따라왔으며, THREADX의 광범위한 업계 채택에 점점 더 깊은 인상을 받았습니다."* – Chris Rommel, 부사장, VDC Research

## <a name="small-footprint"></a>적은 메모리 공간

Azure RTOS ThreadX는 매우 적은 2KB 명령 영역과 RAM 1KB의 최소 메모리 공간이 필요합니다. 이는 주로 계층화되지 않은 picokernel™ 아키텍처와 자동 크기 조정으로 인해 발생합니다. 자동 크기 조정은 애플리케이션에서 사용되는 서비스(및 지원 인프라)만 링크 타임에서 최종 이미지에 포함된다는 것을 의미합니다.

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

## <a name="fast-execution"></a>고속 실행

Azure RTOS ThreadX는 대부분의 인기 있는 프로세서에서 초소형 컨텍스트 전환을 달성하며 전반적으로 다른 상용 RTOS보다 훨씬 빠릅니다. Azure RTOS ThreadX는 속도가 빠를 뿐만 아니라 결정성도 뛰어납니다. 200개의 스레드가 준비되어 있든 단 한 개만 준비되어 있든 동일한 빠른 성능을 달성합니다.

Azure RTOS ThreadX의 일반적인 성능 특성은 다음과 같습니다.

* 빠른 부팅: Azure RTOS ThreadX는 120 사이클 미만으로 부팅됩니다.
* 선택적 기본 오류 검사 제거: 컴파일 타임에 기본 Azure RTOS ThreadX 오류 검사를 건너뛸 수 있습니다. 이는 애플리케이션 코드가 확인되고 더 이상 각 매개 변수에 대한 오류 검사가 필요하지 않을 때 유용할 수 있습니다. 이는 시스템 차원이 아닌 컴파일 단위에서 수행될 수 있습니다.
* Picokernel™ 디자인: 서비스가 서로 계층화되지 않으므로 불필요한 함수 호출 오버 헤드가 제거됩니다.
* *최적화된 인터럽트 처리: 선점이 필요한 경우가 아니면 ISR 진입/종료 시 스크래치 레지스터만 저장/복원됩니다.
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

## <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a>TUV 및 UL을 비롯한 여러 안전 표준의 사전 인증

Azure RTOS ThreadX 및 Azure RTOS ThreadX SMP는 안전이 매우 중요한 시스템에서의 사용을 위해, IEC-61508 SIL 4, IEC-62304 SW 안전 등급 C, ISO 26262 ASIL D 및 EN 50128에 따라 SGS-TUV Saar 인증을 받았습니다. 이 인증은 "전기, 전자 및 프로그램 가능한 전자 안전 관련 시스템의 기능적 안전"에 대한 최고 수준의 IEC-61508, IEC-62304, ISO 26262 및 EN 50128의 안전 무결성 등급에 따라, Azure RTOS ThreadX 및 Azure RTOS ThreadX SMP를 보안 관련 소프트웨어의 개발에 사용할 수 있음을 확인합니다. 독일 SGS-Group 및 TUV Saarland의 공동 벤처인 SGS-TUV Saar는 세계적으로 안전 관련 시스템용 포함 소프트웨어를 테스트, 감사, 확인 및 검증하는 최고 권위의 독립 기업으로 자리했습니다. 산업 보안 표준 IEC 61508과, 거기에서 파생된 모든 표준(IEC-62304, ISO 26262 및 EN 50128 포함)은 전기, 전자 및 프로그래밍 가능한 전자 안전 관련 의료 장비, 공정 제어 시스템, 산업용 기계, 자동차, 철도 제어 시스템의 기능 안전을 보장하는 데 사용됩니다.

:::image type="content" source="media/overview-threadx/partener-logo-sgs-tuv-saar-2.png" alt-text="SGS TUV SAAR 인증":::

UL은 Azure RTOS ThreadX 및 Azure RTOS ThreadX SMP가 프로그래밍 가능한 구성 요소에서의 소프트웨어에 대한 UL 60730-1 부칙 H, CSA E60730-1 부칙 H, IEC 60730-1 부칙 H, UL 60335-1 부칙 R, IEC 60335-1 부칙 R 및 UL 1998 안전 표준을 준수한다고 인정했습니다. UL은 전기의 공공 도입에서부터 지속 가능성, 재생 에너지 및 나노 기술의 혁신에 이르기까지 안전 솔루션을 혁신하는 1세기 이상의 전문 지식을 보유한 글로벌 독립 안전 과학 기업입니다.

:::image type="content" source="media/overview-threadx/cru-logo-certification.png" alt-text="UL 인증":::

TUV 및 UL 인증과 관련한 아티팩트(인증서, 안전 매뉴얼, 테스트 보고서 등)는 판매 가능합니다.

## <a name="eal4-common-criteria-security-certification"></a>EAL4+ Common Criteria 보안 인증

Azure RTOS는 EAL4+ Common Criteria 보안 인증을 달성했습니다. TOE(평가 대상)은 Azure RTOS ThreadX, Azure RTOS NetX-Duo, Azure RTOS NetX Secure TLS 및 Azure RTOS NetX MQTT를 포함합니다. 이는 깊이 내장된 센서, 디바이스, 에지 라우터 및 게이트웨이에 필요한 가장 일반적인 IoT 프로토콜을 나타냅니다.

:::image type="content" border="false" source="media/overview-threadx/eal-logo-certification.png" alt-text="EAL 인증":::

Azure RTOS 보안 인증에 사용되는 IT 보안 평가 시설은 Brightsight BV이고 인증 기관은 SERTIT입니다.

## <a name="simple-easy-to-use"></a>간단하고 손쉬운 사용

Azure RTOS ThreadX는 매우 간단하게 사용할 수 있습니다. Azure RTOS ThreadX API는 직관적이고 매우 기능적입니다. API 이름은 다른 RTOS 제품에서 흔히 볼 수 있는 매우 축약된 이름의 알파벳 약자가 아니라 실제 단어로 구성됩니다. 모든 Azure RTOS ThreadX API에는 선행 `tx_`가 있으며 명사-동사 명명 규칙을 따릅니다. 또한 API 전체에 걸쳐 기능적 일관성이 있습니다. 예를 들어 일시 중단된 모든 API는 API에 대해 동일한 방식으로 작동하는 선택적 시간 제한이 있습니다.

Azure RTOS ThreadX 애플리케이션을 쉽게 빌드할 수 있습니다. 애플리케이션은 *tx_api.h* 를 포함하고, main에서 `tx_kernel_enter`를 호출하고, `tx_application_define` 함수를 정의하고, 스레드 하나를 만들고, 스레드 진입점 함수를 정의하고, Azure RTOS ThreadX 라이브러리에 대한 링크(일반적으로 *tx.a*)를 연결해야 합니다.

또한 Azure RTOS ThreadX는 사용 가능한 최고 수준의 문서를 제공합니다. 

## <a name="advanced-technology"></a>고급 기술

Azure RTOS ThreadX는 가장 중요한 기능이 preemption-threshold 예약인 고급 기술입니다. 이 기능은 Azure RTOS ThreadX의 고유한 것이며 광범위한 학술 연구의 주제였습니다. 예를 들어, Yun Wang(콩코디아 대학교) 및 Manas Saksena(피츠버그 대학교)의 [Preemption Threshold를 사용하여 고정 우선 순위 작업 예약(Scheduling Fixed-Priority Tasks with Preemption Threshold)](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf)을 참조하세요.

Azure RTOS ThreadX의 기능을 고려합니다.

* 완전하고 포괄적인 멀티태스킹 기능 제공
  * 스레드, 애플리케이션 타이머, 메시지 큐, 세마포 계산, 뮤텍스, 이벤트 플래그, 블록 및 바이트 메모리 풀
* 우선 순위 기반의 선점 예약
* 우선 순위 유연성 – 최대 1024개의 우선 순위 수준
* 협력 예약
* Preemption-Threshold™ – Azure RTOS ThreadX만의 고유한 기능으로 컨텍스트 스위치를 줄이고 예약 가능성을 보장할 수 있습니다(학술 연구 기준).
* Azure RTOS ThreadX MODULES를 통한 메모리 보호
* 완전 결정적
* 이벤트 추적 – 마지막 *n* 개의 시스템/애플리케이션 이벤트 캡처
* Event Chaining™ – 각 Azure RTOS ThreadX 통신 또는 동기화 개체에 대해 애플리케이션별 "알림" 콜백 함수를 등록합니다.
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

표준 Azure RTOS ThreadX는 종종 AMP(비대칭적 다중 처리) 방식으로 사용되며, Azure RTOS ThreadX 및 애플리케이션(또는 Linux)의 별도 복사본이 각 코어에서 실행되고 공유 메모리 또는 OpenAMP(Azure RTOS ThreadX는 OpenAMP를 지원)와 같은 프로세서 간 통신 메커니즘을 통해 서로 통신합니다. 이는 Azure RTOS ThreadX를 사용하는 가장 일반적인 다중 코어 구성이며 애플리케이션에서 프로세서를 효과적으로 로드할 수 있는 경우 가장 효율적일 수 있습니다.

프로세서를 로드하는 것이 매우 동적인 환경에서는 다음 프로세서 제품군에 대해 Azure RTOS ThreadX SMP(대칭적 다중 처리)를 사용할 수 있습니다.

* ARM Cortex-Ax
* ARM Cortex-Rx
* ARM Cortex-A5x 64비트
* MIPS 34K, 1004K 및 interAptiv
* PowerPC
* Synopsys ARC HS
* x86

Azure RTOS ThreadX SMP는 *n* 개 프로세서에서 동적 부하 분산을 수행하고 모든 Azure RTOS ThreadX 리소스(큐, 세마포, 이벤트 플래그, 메모리 풀 등)를 모든 코어의 모든 스레드에서 액세스할 수 있도록 허용합니다. Azure RTOS ThreadX SMP는 모든 코어에서 전체 Azure RTOS ThreadX API를 사용하고 SMP 작업에 적용되는 다음과 같은 새 API를 도입합니다.

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Azure RTOS ThreadX MODULES를 통한 메모리 보호

Azure RTOS ThreadX MODULES라는 추가 기능 제품을 사용하면 하나 이상의 애플리케이션 스레드를 대상에서 동적으로 로드하고 실행할 수 있는 "모듈"에 묶을 수 있습니다.

모듈을 사용하면 필드 업그레이드, 버그 수정 및 프로그램 분할을 사용하여 많은 애플리케이션이 활성 스레드에 필요한 메모리만 차지할 수 있습니다.

또한 모듈에는 Azure RTOS ThreadX 자체와 완전히 별개의 주소 공간이 있습니다. 이를 통해 Azure RTOS ThreadX는 모듈 주변에 메모리 보호(MPU 또는 MMU를 통해)를 배치하여 실수로 모듈 외부에 액세스해도 다른 소프트웨어 구성 요소가 손상되지 않도록 할 수 있습니다.

## <a name="fastest-time-to-market"></a>가장 빠른 출시 시간

Azure RTOS ThreadX는 설치, 학습, 사용, 디버그, 확인, 인증 및 유지 관리를 손쉽게 수행할 수 있습니다. 그 결과 Azure RTOS ThreadX는 EMF(Embedded Market Forecasters) 설문 조사에서 지난 7년 연속 가장 빠른 출시 시간의 RTOS였습니다. 설문 조사에서 Azure RTOS ThreadX를 사용한 디자인의 70%가 제 시간에 출시된 것으로 나타났으며, 이는 다른 모든 RTOS를 능가하는 것입니다.

일관된 출시 시간이 가능한 몇 가지 이유는 다음과 같습니다.

* 품질 설명서
* 전체 소스 코드 가용성
* 사용하기 쉬운 API
* 포괄적인 고급 기능 세트
* 광범위한 타사 도구 통합 – 특히 IAR의 Embedded Workbench™

## <a name="royalty-free"></a>로열티 무료

사전에 사용이 허가된 디바이스에 배포하는 경우에는 소스 코드를 사용 및 테스트하는 데 비용이 들지 않으며 프로덕션 라이선스에 대한 비용도 부과되지 않습니다. 다른 모든 디바이스에는 간단한 연간 라이선스가 필요합니다.

## <a name="full-highest-quality-source-code"></a>최고 품질의 전체 소스 코드

처음부터 Azure RTOS ThreadX는 완전한 C 소스 코드로 배포된 산업 등급 RTOS로 설계되었습니다. Azure RTOS ThreadX 소스 코드는 품질 및 이해 용이성의 기준을 정립했습니다. 또한 파일당 하나의 함수를 포함하는 규칙을 통해 손쉬운 소스 탐색을 제공합니다.

Azure RTOS ThreadX는 모든 C 코드 행에 의미 있는 주석이 있어야 한다는 요구 사항을 비롯한 엄격한 코딩 규칙을 준수합니다. 또한 Azure RTOS ThreadX 소스는 가장 높은 표준으로 인증되었습니다.

## <a name="misra-compliant"></a>MISRA 준수

Azure RTOS ThreadX 및 Azure RTOS ThreadX SMP 소스 코드는 MISRA-C:2004 및 MISRA C:2012를 준수합니다. MISRA C는 C 프로그래밍 언어를 사용하는 중요 시스템에 대한 프로그래밍 지침 세트입니다. 원래의 MISRA C 지침은 주로 자동차 분야를 대상으로 했지만, MISRA C는 이제 모든 안전 중요 분야에 적용할 수 있는 것으로 널리 인식되고 있습니다. Azure RTOS ThreadX는 MISRA-C:2004 및 MISRA C:2012의 모든 필수 및 의무 규칙을 준수합니다.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Misra 인증":::

## <a name="supports-most-popular-architectures"></a>대부분의 주요 아키텍처 지원

Azure RTOS ThreadX는 완전한 테스트와 지원을 통해 다음과 같이 대부분의 주요 32/64비트 마이크로프로세서에서 실행되며, 바로 사용할 수 있습니다.

* 아날로그 디바이스: SHARC, Blackfin, CM4xx
* Andes Core: RISC-V
* Ambiqmicro: Apollo MCU
* ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M
* Cadence: Xtensa, Diamond
* CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi
* Cypress: RISC-V
* EnSilica: eSi-RISC
* Infineon: XMC1000, XMC4000, TriCore
* Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10
* Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32
* Microsemi: RISC-V
* NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4
* Renesas: SH, HS, V850, RX, RZ, Synergy
* Silicon Labs: EFM32
* Synopsys: ARC 600, 700, ARC EM, ARC HS
* ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7
* Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C
* Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class
* Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

## <a name="supports-most-popular-tools"></a>가장 널리 사용되는 도구 지원

Azure RTOS ThreadX는 IAR의 Embedded Workbench™를 비롯하여 가장 널리 사용되는 임베디드 개발 도구를 지원하며, 가장 포괄적인 Azure RTOS ThreadX 커널 인식을 제공합니다. 추가 도구 통합에는 GNU(GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore 및 모든 아날로그 디바이스가 포함됩니다.
