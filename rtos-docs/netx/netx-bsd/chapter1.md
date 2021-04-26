---
title: 1장 - Azure RTOS NetX BSD 소개
description: Azure RTOS NetX BSD Sockets API Compliancy Wrapper는 몇 가지 제한 사항이 있는 기본 BSD Sockets API 호출 중 일부를 지원하며, 그 아래에 있는 NetX 기본 요소를 활용합니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fce781ac97ae75c4148614453eeb35c3064f8849
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810423"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a>1장 - Azure RTOS NetX BSD 소개

NetX BSD Sockets API Compliancy Wrapper는 몇 가지 제한 사항이 있는 기본 BSD Sockets API 호출 중 일부를 지원하며, 그 아래에 있는 NetX 기본 요소를 활용합니다. BSD 소켓 API 호환성 계층은 내부 NetX 기본 형식을 활용하고 기본적인 NetX 오류 검사를 건너뛰므로 이 래퍼는 일반적인 BSD 구현보다 약간 빠르거나 동일한 속도로 수행됩니다.

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a>BSD Socket API Compliancy Wrapper 원본

BSD 래퍼 소스 코드는 간단한 설명을 위해 작성되었으며 *nx_bsd.h* 및 *nx_bsd.c* 의 2개 파일로만 구성되어 있습니다. ‘nx_bsd.h’ 파일은 필요한 모든 BSD Socket API 래퍼 상수와 서브루틴 프로토타입을 정의하는 반면, ‘nx_bsd.c’에는 실제 BSD Socket API 호환성 소스 코드가 포함되어 있습니다. 이러한 BSD 래퍼 소스 파일은 모든 NetX 지원 패키지에 공통적으로 제공됩니다.

패키지는 다음으로 구성됩니다.

- **nx_bsd.c**: 래퍼 소스 코드
- **nx_bsd.h**: 주 헤더 파일

샘플 데모 프로그램:

- **bsd_demo_tcp.c**: 단일 TCP 서버 및 클라이언트가 있는 데모
- **bsd_demo_udp.c**: 두 개의 UDP 클라이언트와 1개의 UDP 서버를 포함하는 데모
