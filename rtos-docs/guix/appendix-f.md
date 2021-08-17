---
title: 부록 F - GUIX RTOS 바인딩 서비스
description: GUIX RTOS 바인딩 서비스에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7928e1781be03969de25901ebbe728e6554e96befb59c860f4ea53663c28932d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784600"
---
# <a name="appendix-f---guix-rtos-binding-services"></a>부록 F - GUIX RTOS 바인딩 서비스

GUIX에는 기본 RTOS에서 제공하는 스레드 또는 태스킹 서비스, 뮤텍스, 이벤트 큐 및 타이밍 서비스가 필요합니다. 기본적으로 GUIX는 ThreadX 실시간 운영 체제를 활용하여 이러한 서비스를 제공하도록 구성됩니다. GUIX를 다른 운영 체제로 이식하려면 개발자는 전처리기 지시문 GX_DISABLE_THREADX_BINDING을 # 정의하고 GUIX 라이브러리를 다시 빌드하여 ThreadX 종속성을 제거해야 합니다. 또한 개발자는 다음 매크로 정의 및 지원 함수를 제공해야 합니다. 이러한 매크로 정의 및 지원 함수의 예는 일반적인 rtos 통합 예제를 제공하는 파일 gx_system_rtos_bind.h 및 gx_system_rtos_bind.c에서 찾을 수 있습니다.

시스템 통합 매크로:

**GX_RTOS_BINDING_INITIALIZE**

이 매크로는 시스템 초기화 중에 호출됩니다. 사용하기 전에 rtos 시스템 서비스 또는 rtos 리소스를 준비하는 데 필요한 함수를 호출하도록 매크로를 정의해야 합니다. 이것은 GUIX에서 사용할 rtos 리소스를 준비하기 위한 바인딩의 기회입니다.

**GX_SYSTEM_THREAD_START**

이 매크로는 GUIX 작업 또는 스레드가 실행을 시작해야 할 때 호출됩니다. 이 매크로는 실행 중인 GUIX 스레드를 시작하는 함수를 호출하도록 정의해야 합니다. GUIX 스레드의 진입점은 호출된 함수에 전달됩니다. 호출된 함수의 서명은 다음과 같아야 합니다.

**UINT *function_name*(VOID (thread_entry_point)(VOID));**

이 함수는 스레드가 성공적으로 시작된 경우 GX_SUCCESS를 반환해야 하며, 그렇지 않으면 GX_FAILURE를 반환해야 합니다.

**GX_EVENT_PUSH**

이 매크로는 GUIX에서 사용하는 FIFO 이벤트 큐에 이벤트를 푸시하기 위해 호출됩니다. 새 rtos로 이식할 때 이 이벤트 큐를 스레드로부터 안전한 방식으로 구현하는 것은 사용자의 책임입니다. GX_EVENT 구조체를 이 큐로 복사하고 이 큐에서 복사해야 합니다. 즉, GUIX 이벤트는 이벤트 생산자의 뷰에서 자동 변수가 될 수 있으므로 GX_EVENT 포인터의 큐가 작동하지 않습니다. 이 매크로에 의해 호출되는 함수의 서명은 다음과 같아야 합니다.

**UINT *function_name* (GX_EVENT *event_ptr);**

이벤트가 이벤트 큐로 푸시되는 경우 이 함수는 GX_SUCCESS을 반환해야 하며, 그렇지 않으면 GX_FAILURE을 반환해야 합니다.

**GX_EVENT_POP**

이 매크로는 GUIX 이벤트 큐에서 head(가장 오래 된) 이벤트를 제거하고 요청된 위치에 복사하기 위해 호출됩니다. 이벤트 큐에 현재 이벤트가 없으면, 이 함수는 필요에 따라 이벤트를 차단하거나 이벤트를 대기할 수 있어야 합니다. 이 매크로에 의해 호출되는 함수의 서명은 다음과 같아야 합니다.

UINT function_name (GX_EVENT * put_event, GX_BOOL wait)

Wait 매개 변수가 GX_TRUE이면 이벤트를 제공할 때까지 함수가 반환되어서는 안 됩니다. Wait 매개 변수가 GX_FALSE이면 함수는 이벤트를 사용하거나 사용하지 않고 즉시 반환해야 합니다.

큐에서 이벤트를 검색하면 put_event 위치로 복사 되고 반환 상태는 GX_SUCCESS가 됩니다. 그렇지 않으면 반환 상태는 GX_FAILURE여야 합니다.

**GX_EVENT_FOLD**

이 매크로는 이벤트를 FIFO 이벤트 큐로 접도록 GUIX에서 호출합니다. 이벤트 접기는 동일한 유형의 이벤트가 큐에 이미 있는 경우, 해당 항목이 새 이벤트의 페이로드를 포함하는 업데이트임을 의미합니다. 동일한 유형의 기존 이벤트를 큐에서 찾을 수 없는 경우, 새 이벤트가 큐로 푸시됩니다. 

이벤트 접기 기능을 구현할 수 없는 바인딩의 경우 단순히 GX_EVENT_PUSH 호출하는 것이 좋습니다.

**GX_TIMER_START**

이 매크로는 GUIX가 주기적 타이머 입력을 받아야 할 때 호출됩니다. 이 매크로는 하위 수준 RTOS 주기적 타이머 서비스를 시작하는 서비스를 호출해야 합니다. RTOS 타이머 서비스를 쉽게 중지하고 시작할 수 없다면, 이 서비스를 항상 실행 상태로 유지하는 것이 허용되지만 효율성이 떨어집니다.

하위 수준 RTOS 타이머 서비스가 주기적으로 만료되면 바인딩에서 GUIX 시스템 함수 _gx_system_timer_expiration(0);을 호출해야 합니다. 이 함수를 주기적으로 호출하면 상위 수준의 GUIX 타이머 위젯 타이머 서비스를 구동하게 됩니다.

**GX_TIMER_STOP**

GUIX에 더 이상 주기적 타이머가 필요로 하지 않을 때(즉, 실행되는 활성 GUIX 타이머가 없을 때) 이 매크로가 호출됩니다. RTOS 타이머 서비스를 쉽게 중지하고 시작할 수 없다면, 이 서비스를 항상 실행 상태로 유지하고 이 매크로가 아무것도 수행하지 않도록 정의하는 것은 허용되지만 효율성이 떨어집니다.

**GX_SYSTEM_MUTEX_LOCK**

이 매크로는 중요한 코드 섹션 중에 GUIX에서 호출하여 다른 작업이 선점하고 공통 데이터 구조를 수정하여 잠재적인 손상을 일으키는 것을 방지합니다. 이 매크로는 적절한 RTOS 리소스 잠금 서비스를 구현하는 함수를 호출해야 합니다.

GUIX 스레드 외부에서 GUIX API 서비스를 활용하지 않는다면 이 매크로를 아무 작업도 수행하지 않도록 정의할 수 있습니다.

**GX_SYSTEM_MUTEX_UNLOCK**

이 매크로는 중요한 코드 섹션의 끝에서 호출되며 적절한 기본 RTOS 서비스를 사용하여 GUIX 리소스를 잠금 해제해야 합니다. GUIX 스레드 외부에서 GUIX API 서비스를 활용하지 않는다면 이 매크로를 아무 작업도 수행하지 않도록 정의할 수 있습니다.

**GX_SYSTEM_TIME_GET**

이 매크로는 현재 시스템 시간인 “시스템 틱”을 반환하는 함수를 호출해야 합니다. 이는 일반적으로 시스템 시작 이후 발생한 하위 수준 타이머 인터럽트의 수입니다. 이 서비스는 터치 입력 제스처에 대한 터치 이벤트 펜 속도를 계산하는 데 사용됩니다. 이 매크로에서 호출하는 함수의 서명은 다음과 같아야 합니다.

**ULONG *function_name*(VOID);**

**GX_CURRENT_THREAD**

이 매크로는 현재 실행 중인 스레드를 식별하기 위해 호출됩니다. 이 매크로에서 호출하는 서비스는 void*를 반환해야 합니다. 즉, 운영 체제에서 현재 실행 스레드를 식별하기 위해 사용하는 데이터 형식이 void*로 캐스팅되어 GUX로 반환되어야 합니다.

일반 RTOS 바인딩의 전체 예제는 gx_system_rtos_bind. h 및 gx_system_rtos_bind 파일에서 구현됩니다.