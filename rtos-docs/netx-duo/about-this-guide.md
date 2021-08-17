---
title: Azure RTOS NetX Duo 사용자 가이드 소개
description: 이 가이드에는 Microsoft 고성능 IPv4/IPv6 듀얼 네트워크 스택인 Azure RTOS NetX Duo에 대한 포괄적인 정보가 나와 있습니다.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 032cca3ccdaa7600732d52894d63e5bef366010abaa1145417201f48cb034ab5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790176"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a>Azure RTOS NetX Duo 사용자 가이드 소개

이 가이드에는 Microsoft 고성능 IPv4/IPv6 듀얼 네트워크 스택인 Azure RTOS NetX Duo에 대한 포괄적인 정보가 나와 있습니다. 

이는 기본적인 네트워킹 개념, Azure RTOS ThreadX, C 프로그래밍 언어에 익숙한 포함된 실시간 소프트웨어 개발자를 대상으로 합니다.

## <a name="organization"></a>조직

[1장](chapter1.md) - Azure RTOS NetX Duo 소개

[2장](chapter2.md) - ThreadX 애플리케이션에서 Azure RTOS NetX Duo를 설치하고 사용하기 위한 기본 단계 설명

[3장](chapter3.md) - Azure RTOS NetX Duo 시스템의 기능을 개괄적으로 설명하고 TCP/IP 네트워킹 표준에 대한 기본 정보 제공

[4장](chapter4.md) - Azure RTOS NetX Duo에 대한 애플리케이션의 인터페이스 세부 정보

[5장](chapter5.md) - Azure RTOS NetX Duo용 네트워크 드라이버에 대한 설명

[부록 A](appendix-a.md) - Azure RTOS NetX Duo 서비스

[부록 B](appendix-b.md) - Azure RTOS NetX Duo 상수

[부록 C](appendix-c.md) - Azure RTOS NetX Duo 데이터 형식

[부록 D](appendix-d.md) - BSD 호환 소켓 API

[부록 E](appendix-e.md) - ASCII 차트

## <a name="guide-conventions"></a>가이드 규칙

기울임꼴 - 책 제목을 나타내고 중요한 단어를 강조하며 변수를 가리키는 서체입니다.

**굵게** - 파일 이름과 키워드를 나타내고 중요한 단어와 변수를 추가로 강조하는 서체입니다.

> [!IMPORTANT]
> 정보 기호는 성능 또는 기능에 영향을 줄 수 있는 중요한 정보나 추가 정보를 강조합니다.
 
> [!WARNING]
> 경고 기호는 심각한 오류가 발생할 수 있기 때문에 개발자가 피해야 하는 상황을 강조합니다.

## <a name="azure-rtos-netx-duo-data-types"></a>Azure RTOS NetX Duo 데이터 형식

사용자 지정 Azure RTOS NetX Duo 컨트롤 구조 데이터 형식 외에도 Azure RTOS NetX Duo 서비스 호출 인터페이스에 사용되는 몇 가지 특수 데이터 형식이 있습니다. 이러한 특수 데이터 형식은 기본 C 컴파일러의 데이터 형식에 직접 매핑됩니다. 이 매핑은 서로 다른 C 컴파일러 간의 이식성을 보장하기 위해 수행됩니다. 정확한 구현은 ThreadX에서 상속되며 ThreadX 배포에 포함된 ***tx_port.h*** 파일에서 찾을 수 있습니다.

다음은 Azure RTOS NetX Duo 서비스 호출 데이터 형식과 그와 관련된 의미의 목록입니다.

**UINT**: 부호 없는 기본 정수입니다. 이 형식은 32비트의 부호 없는 데이터를 지원해야 합니다. 그러나 가장 편리한 부호 없는 데이터 형식에 매핑됩니다.  
**ULONG**: 부호 없는 long 형식입니다. 이 형식은 32비트의 부호 없는 데이터를 지원해야 합니다.
**VOID**: 거의 항상 컴파일러의 void 형식과 동일합니다.  
**CHAR**: 대개 표준 8비트 문자 형식입니다.  

추가 데이터 형식은 Azure RTOS NetX Duo 원본 내에서 사용되며, ***tx_port.h** _ 또는 _ *_nx_port.h_** 파일에 있습니다.

## <a name="customer-support-center"></a>고객 지원 센터

다음 단계에 대한 질문 또는 도움이 필요하면 Azure Portal을 통해 지원 티켓을 제출하세요. 지원 요청을 보다 효율적으로 해결할 수 있도록 이메일 메시지에 다음 정보를 제공해 주세요.

1. 발생 빈도와 안정적으로 재현할 수 있는지 여부를 포함한 문제에 대한 자세한 설명
2. 문제가 발생하기 전의 애플리케이션 및/또는 Azure RTOS NetX Duo의 변경 내용에 대한 자세한 설명
3. 배포의 tx_port.h와 nx_port.h 파일에 있는 _tx_version_id와 _nx_version_id 문자열의 내용 이 문자열은 런타임 환경과 관련하여 유용한 정보를 제공합니다.
4. 다음 ULONG 변수의 RAM에 있는 내용:

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    위 변수는 Azure RTOS ThreadX와 Azure RTOS NetX Duo 라이브러리가 빌드된 방법에 관한 정보를 제공합니다.

5. 문제가 탐지된 직후에 캡처된 추적 버퍼. 추적 버퍼는 TX_ENABLE_EVENT_TRACE를 사용하여 Azure RTOS ThreadX와 Azure RTOS NetX Duo 라이브러리를 빌드하고 추적 버퍼 정보를 사용해 tx_trace_enable을 호출하여 캡처합니다.
