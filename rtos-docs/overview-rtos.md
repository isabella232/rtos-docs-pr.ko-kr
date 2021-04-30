---
title: Microsoft Azure RTOS란?
description: Azure RTOS는 MCU(마이크로 컨트롤러 단위)로 구동되는 IoT 및 에지 디바이스의 RTOS(실시간 운영 체제)입니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 3b1c63135f6069652d7f66fc976b9d770a4dfeb2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811413"
---
# <a name="what-is-microsoft-azure-rtos"></a>Microsoft Azure RTOS란

Azure RTOS는 MCU(마이크로 컨트롤러 단위)로 구동되는 IoT 및 에지 디바이스의 RTOS(실시간 운영 체제)입니다. Azure RTOS는 대부분의 매우 제한된 디바이스(배터리 전원을 공급하고 64KB 미만의 플래시 메모리)를 지원하도록 설계되었습니다.
 
Azure RTOS는 다양한 안전 표준에 대해 사전 인증을 받았습니다. 여기에는 IEC 61508 SIL 4, IEC 62304 클래스 C 및 ISO 26262 ASIL D 인증이 포함됩니다. 또한 Azure RTOS ThreadX는 DO-178 인증을 받았습니다.

Azure RTOS는 TLS 및 DTLS를 통해 IPsec 및 소켓 계층 보안을 통해 전체 IP 계층 보안을 비롯하여 EAL4+ Common Criteria 보안 인증 환경을 제공합니다. 소프트웨어 암호화 라이브러리는 FIPS 140-2 인증을 달성했습니다. 또한 하드웨어 암호화 기능, ThreadX 모듈을 통한 메모리 보호 및 ARM의 TrustZone ARMv8-M 보안 기능에 대한 지원을 활용합니다.

## <a name="components-of-azure-rtos"></a>Azure RTOS의 구성 요소

Azure RTOS 플랫폼은 Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo 및 Azure RTOS USBX를 비롯한 런타임 솔루션의 컬렉션입니다.

### <a name="azure-rtos-threadx"></a>Azure RTOS ThreadX

Azure RTOS ThreadX는 깊게 포함된 애플리케이션용으로 특별히 설계된 고급 RTOS(실시간 운영 체제)입니다. Azure RTOS ThreadX에서 제공하는 여러 이점 중 하나는 고급 예약 기능, 메시지 전달, 인터럽트 관리 및 메시징 서비스입니다. Azure RTOS ThreadX에는 picokernel 아키텍처, preemption-threshold 스케줄링, event-chaining 및 다양한 시스템 서비스 집합을 포함한 많은 고급 기능이 있습니다.

### <a name="azure-rtos-filex"></a>Azure RTOS FileX

Azure RTOS FileX는 고성능 FAT 호환 파일 시스템입니다. Azure RTOS ThreadX와 완전히 통합되고 지원되는 모든 프로세서에서 사용할 수 있습니다. Azure RTOS FileX는 Azure RTOS ThreadX와 마찬가지로 공간을 적게 차지하면서 고성능을 제공하도록 설계되었으므로 파일 작업이 필요한 오늘날의 긴밀하게 포함된 애플리케이션에 적합합니다. Azure RTOS FileX는 Azure RTOS LevelX를 통해 RAM 디스크, USBX, SD 카드 및 NAND/NOR 플래시 메모리를 비롯한 대부분의 물리적 미디어를 지원합니다.

### <a name="azure-rtos-guix"></a>Azure RTOS GUIX

Azure RTOS GUIX는 포함된 시스템 개발자의 요구 사항에 맞게 제작된 전문적인 품질의 그래픽 사용자 인터페이스 패키지입니다. 다른 대안과 달리 Azure RTOS GUIX는 그래픽 출력을 지원할 수 있는 거의 모든 하드웨어 구성으로 작고 빠르고 쉽게 이식할 수 있습니다. 또한 Azure RTOS GUIX는 애플리케이션 수준 사용자 인터페이스 개발을 위한 뛰어난 시각적 효과와 직관적이고 강력한 API를 제공합니다.

### <a name="azure-rtos-netx"></a>Azure RTOS NetX

Azure RTOS NetX는 TCP/IP 프로토콜 표준의 고성능 구현입니다. Azure RTOS ThreadX와 완전히 통합되고 지원되는 모든 프로세서에서 사용할 수 있습니다. Azure RTOS NetX에는 고유한 Piconet 아키텍처가 있습니다. 제로 복사 API와 함께 사용하면 네트워크에 연결해야 하는 오늘날의 긴밀하게 포함된 애플리케이션에 완벽하게 부합합니다.

### <a name="azure-rtos-netx-duo"></a>Azure RTOS NetX Duo

Azure RTOS NetX Duo는 긴밀하게 포함된 실시간 및 IoT 애플리케이션을 위해 특별히 설계된 고급, 산업용 TCP/IP 네트워크 스택입니다. Azure RTOS NetX Duo는 이중 IPv4 및 IPv6 네트워크 스택이고, NetX는 원래 IPv4 네트워크 스택이며, 기본적으로 Azure RTOS NetX Duo의 하위 집합입니다.

### <a name="azure-rtos-usbx"></a>Azure RTOS USBX

Azure RTOS USBX는 고성능의 USB 호스트, 디바이스 및 OTG(On-The-Go) 포함 스택입니다. ThreadX와 완전히 통합되고 지원되는 모든 Azure RTOS ThreadX 프로세서에서 사용할 수 있습니다. Azure RTOS USBX는 Azure RTOS ThreadX와 마찬가지로 공간을 적게 차지하면서 고성능을 제공하도록 설계되었으므로 USB 디바이스와 인터페이스가 필요한 긴밀하게 포함된 애플리케이션에 적합합니다.

### <a name="windows-tools"></a>Windows 도구

Azure RTOS GUIX Studio는 전체 GUI 애플리케이션 디자인 환경을 제공하여 애플리케이션의 GUI에서 모든 그래픽 요소를 만들고 유지 관리하는 작업을 용이하게 합니다. Azure RTOS GUIX Studio는 대상에서 컴파일되고 실행할 준비가 된 Azure RTOS GUIX 라이브러리와 호환되는 C 코드를 자동으로 생성합니다.

Azure RTOS TraceX는 포함된 시스템 개발자에게 실시간 시스템 이벤트에 대한 그래픽 보기를 제공하고, 실시간 시스템의 동작을 시각화하고 더 잘 이해할 수 있도록 하는 호스트 기반 분석 도구입니다.

## <a name="in-the-context-of-azure-iot"></a>Azure IoT의 컨텍스트에서

Azure IoT에 직접 연결하거나 Azure IoT Edge를 통해 간접적으로 연결하는 것 외에도 Azure RTOS를 Azure Sphere 디바이스에서 사용할 수도 있습니다. Azure RTOS와 Azure Sphere의 조합은 하나의 디바이스에서 최상의 실시간 처리 및 보안을 제공합니다.
