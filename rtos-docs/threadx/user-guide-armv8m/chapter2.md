---
title: 챕터 2 - ARMv8-M의 ThreadX 지원 설치
description: 이 챕터는 ARMv8-M 아키텍처의 ThreadX 소스 코드를 설치하고 사용하는 방법을 설명합니다.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 303b83bcc92797314b764353b770965c0170fb99
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377505"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a>챕터 2 - ARMv8-M의 ThreadX 지원 설치

ARMv8-M 아키텍처를 지원하는 추가 ThreadX 소스 코드 파일이 있습니다.

ThreadX가 보안 모드에서 실행되는 경우 이러한 추가 파일 및 API는 필요하지 않습니다. 보안 모드에서 ThreadX를 실행하려면 **_tx_port.h_ *_의 상단, 명령줄 또는 프로젝트 설정에서 기호 **TX_SECURE_EXECUTION** 을 정의하십시오. 모든 c 및 어셈블리 파일에 대해 _* TX_SECURE_EXECUTION** 이 정의되어 있는지 확인하십시오. ThreadX 및 사용자 애플리케이션이 보안 모드에서 실행됩니다.

ThreadX 및 사용자 애플리케이션을 비보안 모드로 실행하고 비보안 호출 가능 보안 함수를 지원하려면 다음을 수행하십시오.

***tx_thread_secure_stack.c*** 파일을 보안 애플리케이션에 추가해야 합니다.

다음 파일을 ThreadX 라이브러리에 추가해야 합니다.

- ***tx_secure_interface.h***
- ***txe_thread_secure_stack_allocate.c***
- ***txe_thread_secure_stack_free.c***
- ***tx_thread_secure_stack_allocate.s***
- ***tx_thread_secure_stack_free.s***

다음 두 파일은 ThreadX 라이브러리의 일반 파일을 대체합니다.

- ***tx_thread_stack_error_handler.c***
- ***tx_thread_stack_error_notify.c***

## <a name="additional-threadx-sources-for-armv8-m"></a>ARMv8-M의 추가 ThreadX 소스

ARMv8-M TrustZone 아키텍처의 추가 ThreadX 파일은 아래에 설명되어 있습니다.

  | **파일 이름**                            | **콘텐츠**                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | ***tx_secure_interface.h***              | ThreadX 비보안 호출 가능 함수를 정의하는 파일을 포함합니다. |
  | ***txe_thread_secure_stack_allocate.c*** |  보안 스택 할당 API의 오류 검사 파일입니다. |
  | ***txe_thread_secure_stack_free.c***     |  보안 스택 해제 API의 오류 검사 파일입니다. |
  | ***tx_thread_secure_stack_allocate.s***  |  보안 스택 할당 서비스의 비보안 베니어입니다. |
  | ***tx_thread_secure_stack_free.s***      |  보안 스택 해제 서비스의 비보안 베니어입니다. |
  | ***tx_thread_stack_error_handler.c***    |  스레드 스택 오류의 처리기입니다. |
  | ***tx_thread_stack_error_notify.c***     |  스레드 스택 오류를 처리하기 위한 알림 콜백을 등록합니다. |
