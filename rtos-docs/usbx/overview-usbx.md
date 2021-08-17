---
title: Azure RTOS USBX 이해
description: Azure RTOS USBX는 고성능 USB 호스트, 디바이스 및 OTG(On-The-Go) 포함 스택으로, Azure RTOS ThreadX와 완전히 통합되며 모든 Azure RTOS ThreadX 지원 프로세서에서 사용할 수 있습니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 8950e7573bf705feb16de6ac1adb5f55559ea4b04b453944c5a24baddc6ae7b9
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791451"
---
# <a name="overview-of-azure-rtos-usbx"></a>Azure RTOS USBX 개요

Azure RTOS USBX는 고성능의 USB 호스트, 디바이스 및 OTG(On-The-Go) 포함 스택입니다. Azure RTOS USBX는 Azure RTOS ThreadX와 완전히 통합되며 모든 ThreadX 지원 프로세서에서 사용할 수 있습니다. Azure RTOS USBX는 ThreadX와 마찬가지로 메모리 공간을 적게 차지하면서 고성능을 제공하도록 설계되었으므로 USB 디바이스와 인터페이스가 필요한 긴밀하게 포함된 애플리케이션에 적합합니다.

## <a name="host-device-otg--extensive-class-support"></a>호스트, 디바이스, OTG 및 광범위 클래스 지원

Azure RTOS USBX 호스트/디바이스 포함 USB 프로토콜 스택은 포함 수준이 높은 실시간 IoT 애플리케이션 전용으로 설계된 산업 등급 포함 USB 솔루션입니다. Azure RTOS USBX는 호스트, 디바이스, OTG 지원과, 광범위 클래스 지원을 제공합니다. Azure RTOS USBX는 ThreadX 실시간 운영 체제, Azure RTOS FileX 포함 FAT 호환 파일 시스템, Azure RTOS NetX 및 Azure RTOS NetX Duo 포함 TCP/IP 스택에 통합됩니다. 이뿐 아니라 Azure RTOS USBX는 매우 적은 메모리 공간에서 고속 실행과 뛰어난 사용 편의성을 구현하므로, USB 연결이 요구되는 가장 까다로운 포함된 IoT 애플리케이션에 적합합니다.

### <a name="usbx-memory-footprint"></a>USBX 메모리 공간

Azure RTOS USBX는 Azure RTOS USBX 디바이스 CDC/ACM 지원을 위한 최소 메모리 공간이 10.5KB FLASH, 5.1KB RAM으로, 매우 적습니다. Azure RTOS USBX 호스트에서는 CDC/ACM 지원에 최소 18KB FLASH와 25KB RAM이 필요합니다.

TCP 기능을 위해서는 추가적으로 10 ~ 13KB의 명령 영역 메모리가 필요합니다. Azure RTOS USBX RAM 사용량은 일반적으로 2.6KB에서 3.6KB까지이며, 애플리케이션에 의해 정의되는 패킷 풀 메모리를 포함합니다.

ThreadX와 같이 Azure RTOS USBX의 크기는 애플리케이션에서 실제 사용하는 서비스에 따라 자동으로 조정됩니다. 이렇게 하면 사실상 복잡한 구성 및 빌드 매개 변수가 제거되어 개발자가 더 쉽게 작업을 수행할 수 있습니다.

### <a name="usb-interoperability-verification"></a>USB 상호 운용성 확인

Azure RTOS USBX 디바이스 스택은 완벽한 USB 규정 준수와 다양한 시스템과의 상호 운용성을 보장하기 위해, USB IF 표준 테스트 도구 USBCV로 엄격히 테스트되었습니다.
또한 Azure RTOS USBX OTG 스택은 대만의 독립적인 테스트 랩 Allion 확인 및 인증을 거쳤습니다.

### <a name="usb-host-controller-support"></a>USB 호스트 컨트롤러 지원

Azure RTOS USBX는 OHCI 및 EHCI 같은 주요 USB 표준을 지원합니다. 또한 Azure RTOS USBX는 Atmel, Microchip, Philips, Renesas, ST, TI 및 기타 공급업체에서 제공하는 독점적인 개별 USB 호스트 컨트롤러를 지원합니다. Azure RTOS USBX는 동일한 애플리케이션에서 여러 호스트 컨트롤러도 지원합니다.
USB 디바이스 컨트롤러. Azure RTOS USBX는 Analog Devices, Atmel, Microchip, NXP, Philips, Renesas, ST, TI 및 기타 공급업체의 주요 USB 디바이스 컨트롤러를 지원합니다.

### <a name="extensive-host-class-support"></a>광범위한 호스트 클래스 지원

Azure RTOS USBX 호스트는 ASIX, AUDIO, CDC/ACM, CDC/ECM, GSER, HID(키보드, 마우스 및 원격 제어), HUB, PIMA(PTP/MTP), 프린터, PROLIFIC 및 스토리지를 비롯한 주요 클래스를 지원합니다.

### <a name="extensive-usb-device-class-support"></a>광범위한 USB 디바이스 클래스 지원

Azure RTOS USBX 디바이스는 CDC/ACM, CDC/ECM, DFU, HID, PIMA(PTP/MTP) (w/MTP), RNDIS 및 스토리지를 비롯한 주요 클래스를 지원합니다. 사용자 지정 클래스에 대한 지원도 사용할 수 있습니다.

### <a name="pictbridge-support"></a>Pictbridge 지원

Azure RTOS USBX는 호스트와 디바이스 모두에서 전체 Pictbridge 구현을 지원합니다. Pictbridge는 양쪽 모두에서 Azure RTOS USBX PIMA(PTP/MTP) 클래스 위에 있습니다. PictBridge 표준을 사용하면 디지털 스틸 카메라 또는 스마트폰을 PC 없이 프린터에 직접 연결하여 특정 Pictbridge 인식 프린터에 직접 인쇄할 수 있습니다. 카메라 또는 휴대폰이 프린터에 연결된 경우 프린터는 USB 호스트이고 카메라는 USB 디바이스입니다. 그러나 Pictbridge를 사용하면 카메라가 호스트로 표시되고 명령은 카메라에서 구동됩니다. 카메라는 스토리지 서버이며, 프린터는 스토리지 클라이언트입니다. 카메라는 인쇄 클라이언트이며 프린터는 당연히 인쇄 서버입니다. Pictbridge는 USB를 전송 계층으로 사용하지만 통신 프로토콜에 대한 PTP(사진 전송 프로토콜)를 사용합니다.

### <a name="custom-class-support"></a>사용자 지정 클래스 지원

Azure RTOS USBX의 호스트 및 디바이스는 사용자 지정 클래스를 지원합니다. 예제 사용자 지정 클래스는Azure RTOS USBX 배포에 제공됩니다. 이 간단한 데이터 펌프 클래스를 DPUMP라 하며, 사용자 지정 애플리케이션 클래스의 모델로 사용할 수 있습니다.
고급 기술 Azure RTOS USBX 호스트 및 디바이스는 사용자 지정 클래스를 지원합니다. 예제 사용자 지정 클래스는Azure RTOS USBX 배포에 제공됩니다. Azure RTOS USBX는 다음을 포함하는 고급 기술입니다.

* 호스트, 디바이스 및 OTG 지원
* USB 낮음, 전체 및 고속 지원
* 자동 크기 조정
* ThreadX, Azure RTOS FileX 및 Azure RTOS NetX 완전 통합
* 선택적 성능 메트릭
* Azure RTOS TraceX 시스템 분석 지원

## <a name="azure-rtos-usbx-apis"></a>Azure RTOS USBX API

### <a name="azure-rtos-usbx-host-api"></a>Azure RTOS USBX 호스트 API

Azure RTOS USBX 호스트 API는 명사 동사 명명 규칙에 따르는 직관적이고 일관된 API입니다. 모든 API 앞에는 USBX로 쉽게 식별할 수 있는 ux_host_*가 있습니다. 모든 차단 API에는 선택적 스레드 시간 제한이 적용됩니다.

* .ASIX
    - 최소 0.3KB FLASH, 4KB RAM
    - 자동 크기 조정 | Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_host_class_asix_* * 형식의 직관적인 Azure RTOS USBX 호스트 API
* 오디오
    - 최소 1.2KB FLASH, 4KB RAM
    - 자동 크기 조정
    - *ux_host_class_audio_* * 형식의 직관적인 Azure RTOS USBX 호스트 API
* CDC/ACM
    - 최소 1.4KB FLASH, 4KB RAM
    - 자동 크기 조정
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_host_class_cdc_acm_* * 형식의 직관적인 Azure RTOS USBX 호스트 API
* HID
    - 최소 0.3KB FLASH, 4KB RAM
    - 키보드, 마우스 및 원격 지원
    - 자동 크기 조정
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_host_class_hid_* * 형식의 직관적인 Azure RTOS USBX 호스트 API 
* HUB
    - 최소 1.7KB FLASH, 2KB RAM
    - 자동 크기 조정
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_host_class_hub_* * 형식의 직관적인 Azure RTOS USBX 호스트 API
* PIMA(PTP/MTP)
    - 최소 0.9KB FLASH, 8KB RAM
    - 자동 크기 조정
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_host_class_pima_* * 형식의 직관적인 Azure RTOS USBX 호스트 API
* 프린터
    - 최소 0.8KB FLASH, 8KB RAM
    - 자동 크기 조정
    -  Azure RTOS TraceX를 통한 시스템 수준 추적
    -  *ux_host_class_printer_* * 형식의 직관적인 Azure RTOS USBX 호스트 API
* PROLIFIC
    - 최소 1.5KB FLASH, 4KB RAM
    - 자동 크기 조정
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_host_class_prolific_* * 형식의 직관적인 Azure RTOS USBX 호스트 API
* STORAG
    - 최소 5.6KB FLASH, 4KB RAM
    - 자동 크기 조정<br> Azure RTOS FileX 통합
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_host_class_storage_* * 형식의 직관적인 Azure RTOS USBX 호스트 API
* USB 호스트 스택
    - 다수의 호스트 컨트롤러 지원
    - 최소 18KB FLASH, 25KB RAM
    - 자동 크기 조정
    - 동일한 플랫폼에서 여러 호스트 컨트롤러 지원
    -  USB 낮음, 전체 및 고속 지원
    -  Azure RTOS TraceX를 통한 시스템 수준 추적
    -  *ux_host_stack_*  * 형식의 직관적인 Azure RTOS USBX 호스트 API 
* OHCI, EHCI, 소유 호스트 컨트롤러 

### <a name="azure-rtos-usbx-device-api"></a>Azure RTOS USBX 디바이스 API

Azure RTOS USBX 디바이스 API는 명사 동사 명명 규칙에 따르는 직관적이고 일관된 API입니다. 모든 API 앞에는 USBX로 쉽게 식별할 수 있는 선행 ux_device_*가 있습니다. 차단 API에는 선택적 스레드 시간 제한이 적용됩니다. 자세한 내용은 [Azure RTOS USBX 호스트 사용자 가이드](usbx-host-stack-about.md)를 참조하세요.

* CDC/ACM
    - 최소 0.8KB FLASH, 2KB RAM
    - 자동 크기 조정
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_device_class_cdc_acm_** 형식의 직관적인 Azure RTOS USBX 디바이스 API
* CDC/ECM
    - 최소 1.5KB FLASH, 4 ~ 8KB RAM
    - 자동 크기 조정
    - Azure RTOS TraceX를 통한 시스템 수준 추적<br> *ux_device_class_cdc_ecm_** 형식의 직관적인 Azure RTOS USBX 디바이스 API
* DFU
    - 최소 1.1KB FLASH, 2KB RAM
    -  자동 크기 조정
    -  Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_device_class_dfu_* * 형식의 직관적인 Azure RTOS USBX 디바이스 API 
* GSER
    - 최소 0.6KB FLASH, 4KB RAM
    - 자동 크기 조정
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_device_class_gser_* * 형식의 직관적인 Azure RTOS USBX 디바이스 API
* HID
    - 최소 0.9KB FLASH, 2KB RAM
    - 자동 크기 조정
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_device_class_hid_* * PIMA(PTP/MTP) 형식의 직관적인 Azure RTOS USBX 디바이스 API
    - 최소 5.2KB FLASH, 8KB RAM
    - 자동 크기 조정
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_device_class_pima_* * 형식의 직관적인 Azure RTOS USBX 디바이스 API 
* STORAGE
    - 최소 2.3KB FLASH, 4KB RAM
    - 자동 크기 조정
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_device_class_storage_* * 형식의 직관적인 Azure RTOS USBX 디바이스 API
* RNDIS
    - 최소 2.3KB FLASH, 4 ~ 8KB RAM
    - 자동 크기 조정
    - Azure RTOS NetX 및 Azure RTOS NetX DUO와 통합
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_device_class_rndls_* * 형식의 직관적인 Azure RTOS USBX 디바이스 API
* Azure RTOS USBX 디바이스 스택
    - 최소 2.3KB FLASH, 4KB RAM
    - 자동 크기 조정
    - Azure RTOS TraceX를 통한 시스템 수준 추적
    - *ux_device_class_storage_* * 형식의 직관적인 Azure RTOS USBX 디바이스 API
* 소유 호스트 컨트롤러

## <a name="next-steps"></a>다음 단계

[호스트 스택 사용자 가이드](usbx-host-stack-about.md) 또는 [디바이스 스택 사용자 가이드](usbx-device-stack-about.md)에 따라 Azure RTOS USBX 호스트 및 스택 작업을 시작합니다.