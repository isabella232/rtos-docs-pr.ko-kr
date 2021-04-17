---
title: Azure RTOS USBX 디바이스 스택 사용자 가이드
description: 이 가이드에서는 Microsoft의 고성능 USB 기반 소프트웨어인 Azure RTOS USBX에 대한 포괄적인 정보를 제공합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: c8e9360c8b72adbc41f840a48e333668c489399e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810243"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a>Azure RTOS USBX 디바이스 스택 사용자 가이드

이 가이드에서는 Microsoft의 고성능 USB 기반 소프트웨어인 Azure RTOS USBX에 대한 포괄적인 정보를 제공합니다.

임베디드 실시간 소프트웨어 개발자를 위한 것입니다. 개발자는 표준 실시간 운영 체제 함수, USB 사양 및 C 프로그래밍 언어에 대해 잘 알고 있어야 합니다.

USB와 관련된 기술 정보는 https://www.USB.org/developers 에서 다운로드할 수 있는 USB 사양 및 USB 클래스 사양을 참조하세요.

## <a name="organization"></a>조직

- [**1장**](usbx-device-stack-1.md) - Azure RTOS USBX에 대한 소개가 포함되어 있습니다.

- [**2장**](usbx-device-stack-2.md) - ThreadX 애플리케이션에서 Azure RTOS USBX를 설치하고 사용하기 위한 기본 단계를 제공합니다.

- [**3장**](usbx-device-stack-3.md) - Azure RTOS USBX 디바이스 스택의 기능 구성 요소를 설명합니다.

- [**4장**](usbx-device-stack-4.md) - Azure RTOS USBX 디바이스 스택 서비스를 설명합니다.

- [**5장**](usbx-device-stack-5.md) - API를 포함하여 각 Azure RTOS USBX 디바이스 클래스를 설명합니다.

## <a name="customer-support-center"></a>고객 지원 센터

다음 단계에 대한 질문 또는 도움이 필요하면 Azure Portal을 통해 지원 티켓을 제출하세요. 지원 요청을 보다 효율적으로 해결할 수 있도록 이메일 메시지에 다음 정보를 제공해 주세요.

1. 발생 빈도와 안정적으로 재현할 수 있는지 여부를 포함한 문제에 대한 자세한 설명입니다.
2. 문제가 발생하기 전의 애플리케이션 및/또는 Azure RTOS ThreadX의 변경 내용에 대한 자세한 설명입니다.
3. 배포의 **_tx_port.h_** 파일에 있는 **_tx_version_id** 문자열의 내용입니다. 이 문자열은 런타임 환경에 대한 유용한 정보를 제공합니다.
4. *_tx_build_options* **ULONG** 변수의 RAM에 있는 내용입니다. 이 변수는 Azure RTOS ThreadX 라이브러리가 빌드되는 방법에 대한 정보를 제공합니다.
