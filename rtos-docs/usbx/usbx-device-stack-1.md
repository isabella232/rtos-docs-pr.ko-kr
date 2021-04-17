---
title: 1장 - Azure RTOS USBX 디바이스 스택 소개
description: USBX는 딥 임베디드 애플리케이션을 위한 모든 기능을 갖춘 USB 스택입니다. 이 장에서는 USBX를 소개하고 해당 애플리케이션과 이점을 설명합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6965303f1fbf19212b9f7ff20f811a71fb207f54
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813440"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a>1장 - Azure RTOS USBX 디바이스 스택 소개

USBX는 딥 임베디드 애플리케이션을 위한 모든 기능을 갖춘 USB 스택입니다. 이 장에서는 USBX를 소개하고 해당 애플리케이션과 이점을 설명합니다. 

## <a name="usbx-features"></a>USBX 기능

USBX는 1.1, 2.0 및 OTG의 세 가지 기존 USB 사양을 지원합니다. 확장 가능하도록 설계되었으며 하나의 연결된 디바이스만으로 간단한 USB 토폴로지를 수용하고 여러 디바이스와 연계 허브가 포함된 복잡한 토폴로지도 수용합니다. USBX는 USB 프로토콜의 모든 데이터 전송 유형(제어, 대량, 인터럽트 및 등시)을 지원합니다.

USBX는 호스트 쪽과 디바이스 쪽 모두를 지원합니다. 각 측면은 세 개의 계층으로 구성됩니다.

- 컨트롤러 계층
- 스택 계층
- 클래스 계층

USB 계층 간의 관계는 다음과 같습니다.

![USB 계층](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>제품 중요 정보

- ThreadX 프로세서 지원 완료
- 로열티 없음
- 전체 ANSI C 소스 코드
- 실시간 성능
- 반응형 기술 지원
- 여러 클래스 지원
- 여러 클래스 인스턴스
- ThreadX, FileX 및 NetX와 클래스 통합
- 여러 구성이 있는 USB 디바이스 지원
- USB 복합 디바이스 지원
- USB 전원 관리 지원
- USB OTG 지원
- TraceX에 대한 추적 이벤트 내보내기

## <a name="powerful-services-of-usbx"></a>USBX의 강력한 서비스

### <a name="complete-usb-device-framework-support"></a>USB 디바이스 프레임워크 지원 완료

USBX는 다중 구성, 다중 인터페이스 및 다중 대체 설정을 포함하여 가장 까다로운 USB 디바이스를 지원할 수 있습니다.

### <a name="easy-to-use-apis"></a>사용하기 쉬운 API

USBX는 이해하고 사용하기 쉬운 방식으로 가장 심층적인 임베디드 USB 스택을 제공합니다. USBX API를 사용하면 서비스를 직관적이고 일관되게 만들 수 있습니다. 제공된 USBX 클래스 API를 사용하면 사용자 애플리케이션은 USB 프로토콜의 복잡성을 이해할 필요가 없습니다.
