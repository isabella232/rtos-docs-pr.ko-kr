---
title: 1장 - Azure RTOS USBX 호스트 스택 소개
description: 이 장에서는 USBX 호스트 스택을 소개하고 애플리케이션과 이점을 설명합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a9fdd86d47bd4680409cc550c87bc6f456d146a9
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377053"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a>1장 - Azure RTOS USBX 호스트 스택 소개

USBX는 심층적인 포함된 애플리케이션을 위한 모든 기능을 갖춘 USB 스택입니다. 이 장에서는 USBX를 소개하고 해당 애플리케이션과 이점을 설명합니다.

## <a name="usbx-features"></a>USBX 기능

USBX는 1.1, 2.0 및 OTG의 세 가지 기존 USB 사양을 지원합니다. 확장 가능하도록 설계되었으며 하나의 연결된 디바이스만으로 간단한 USB 토폴로지를 수용하고 여러 디바이스와 연계 허브가 포함된 복잡한 토폴로지도 수용합니다. USBX는 USB 프로토콜의 모든 데이터 전송 유형(제어, 대량, 인터럽트 및 등시)을 지원합니다.

USBX는 호스트 쪽과 디바이스 쪽 모두를 지원합니다. 각 측면은 세 개의 계층으로 구성됩니다.

- 컨트롤러 계층
- 스택 계층
- 클래스 계층

USB 계층 간의 관계는 다음과 같습니다.

![USB 계층](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>제품 중요 정보

- 완벽한 ThreadX 프로세서 지원
- 로열티 없음
- 전체 ANSI C 소스 코드
- 실시간 성능
- 반응형 기술 지원
- 여러 호스트 컨트롤러 지원
- 여러 클래스 지원
- 여러 클래스 인스턴스
- ThreadX, FileX 및 NetX와 클래스 통합
- 여러 구성이 있는 USB 디바이스 지원
- USB 복합 디바이스 지원
- 연계 허브에 대한 지원
- USB 전원 관리 지원
- USB OTG 지원
- TraceX에 대한 추적 이벤트 내보내기

## <a name="powerful-services-of-usbx"></a>USBX의 강력한 서비스

### <a name="multiple-host-controller-support"></a>여러 호스트 컨트롤러 지원

USBX는 동시에 실행되는 여러 USB 호스트 컨트롤러를 지원할 수 있습니다. 이 기능을 사용하면 현재 시장에서 대부분의 USB 2.0 호스트 컨트롤러와 연결된 이전 버전과의 호환성 체계를 사용하여 USBX에서 USB 2.0 표준을 지원할 수 있습니다.

### <a name="usb-software-scheduler"></a>USB 소프트웨어 스케줄러

USBX에는 하드웨어 목록 처리가 없는 USB 컨트롤러를 지원하는 데 필요한 USB 소프트웨어 스케줄러가 포함되어 있습니다. USBX 소프트웨어 스케줄러는 정확한 빈도의 서비스와 우선 순위를 사용하여 USB 전송을 구성하고 각 전송을 실행하도록 USB 컨트롤러에 지시합니다.

### <a name="complete-usb-device-framework-support"></a>USB 디바이스 프레임워크 지원 완료

USBX는 다중 구성, 다중 인터페이스 및 다중 대체 설정을 포함하여 가장 까다로운 USB 디바이스를 지원할 수 있습니다.

### <a name="easy-to-use-apis"></a>사용하기 쉬운 API

USBX는 이해하고 사용하기 쉬운 방식으로 가장 심층적인 포함된 USB 스택을 제공합니다. USBX API를 사용하면 서비스를 직관적이고 일관되게 만들 수 있습니다. 제공된 USBX 클래스 API를 사용하면 사용자 애플리케이션은 USB 프로토콜의 복잡성을 이해할 필요가 없습니다.
