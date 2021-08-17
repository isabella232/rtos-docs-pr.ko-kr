---
title: 챕터 3 - USBX 호스트 스택의 기능 구성 요소
description: 이 챕터에서는 기능 관점에서 고성능 USBX 임베디드 USB 호스트 스택에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a3cbbb2e26d66d3db26144a47a1b6cbb11387c7b5b2ba5e19d35df026e5e3598
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790891"
---
# <a name="chapter-3---functional-components-of-usbx-host-stack"></a>챕터 3 - USBX 호스트 스택의 기능 구성 요소

이 챕터에서는 기능 관점에서 고성능 USBX 임베디드 USB 호스트 스택에 대해 설명합니다.

## <a name="execution-overview"></a>실행 개요

USBX는 여러 구성 요소로 구성됩니다.

- 초기화
- 애플리케이션 인터페이스 호출
- 루트 허브
- 허브 클래스
- 호스트 클래스
- USB 호스트 스택
- 호스트 컨트롤러

다음 다이어그램에서는 USBX 호스트 스택을 설명합니다.

![USBX 호스트 스택](./media/usbx-host-stack/usbx-host-stack.png)

### <a name="initialization"></a>초기화

USBX를 활성화하기 위해 ***ux_system_initialize*** 함수를 호출해야 합니다. 이 함수는 USBX에 대한 메모리 리소스를 초기화합니다.

USBX 호스트 기능을 활성화기 위해 ***ux_host_stack_initialize*** 함수를 호출해야 합니다. 이 함수는 ThreadX 스레드, 뮤텍스 및 세마포와 같은 USBX 호스트 스택에서 사용하는 모든 리소스를 초기화합니다.

하나 이상의 USB 호스트 컨트롤러와 하나 이상의 USB 클래스를 활성화하려면 애플리케이션 초기화를 수행해야 합니다. 클래스를 스택에 등록하고 호스트 컨트롤러 초기화 함수를 호출했다면 버스가 활성 상태이고 디바이스 검색을 시작할 수 있습니다. 호스트 컨트롤러의 루트 허브가 연결된 디바이스를 발견하면 USB 토폴로지를 담당하는 USB 열거 스레드가 절전 모드에서 깨어나 디바이스를 열거합니다.

루트 허브와 다운스트림 허브의 특성 때문에 호스트 컨트롤러 초기화 함수가 반환될 때 연결된 모든 USB 디바이스가 완전히 구성되지 않을 수 있습니다. 모든 USB 디바이스를 열거하는 데 몇 초 정도 걸릴 수 있습니다(특히 루트 허브와 USB 디바이스 사이에 하나 이상의 허브가 있는 경우).

### <a name="application-interface-calls"></a>애플리케이션 인터페이스 호출

USBX에는 두 가지 수준의 API가 있습니다.

- USB 호스트 스택 API
- USB 호스트 클래스 API

일반적으로 USBX 애플리케이션은 USB 호스트 스택 API 함수를 호출하지 않아도 됩니다. 대부분의 애플리케이션은 USB 클래스 API 함수에만 액세스합니다.

### <a name="usb-host-stack-apis"></a>USB 호스트 스택 API

호스트 스택 API 함수는 USBX 구성 요소(호스트 클래스 및 호스트 컨트롤러)의 등록, 디바이스 구성 및 사용 가능한 디바이스 엔드포인트에 대한 전송 요청을 담당합니다.

### <a name="usb-host-class-api"></a>USB 호스트 클래스 API

클래스 API는 각 USB 클래스로 한정됩니다. USB 클래스에 사용되는 대부분의 일반 API는 디바이스 열기/닫기, 디바이스에서 읽기 및 쓰기와 같은 서비스를 제공합니다.

### <a name="root-hub"></a>루트 허브

각 호스트 컨트롤러 인스턴스에는 USB 루트 허브가 하나 이상 있습니다. 루트 허브의 수는 컨트롤러의 특성에 따라 결정됩니다. 또는 컨트롤러에서 특정 레지스터를 읽어서 검색할 수 있습니다.

### <a name="hub-class"></a>허브 클래스

허브 클래스는 USB 허브 구동을 담당합니다. USB 허브는 독립 실행형 허브이거나 키보드 또는 모니터와 같은 복합 디바이스의 일부입니다. 허브는 자체 전력을 사용할 수도 있고 버스의 전력을 사용할 수도 있습니다. 버스의 전력을 사용하는 허브는 최대 4개의 다운스트림 포트를 가질 수 있으며 100mA 미만의 전력을 사용하는 자체 전력 또는 버스 전력 사용 디바이스만 연결할 수 있습니다. 허브를 연결할 수 있습니다. 최대 5개의 허브를 서로 연결할 수 있습니다.

### <a name="usb-host-stack"></a>USB 호스트 스택

USB 호스트 스택은 USBX의 핵심입니다. 세 가지 주요 함수를 제공합니다.

- USB 토폴로지를 관리합니다.
- USB 디바이스를 하나 이상의 클래스에 바인딩합니다.
- 클래스에 API를 제공하여 디바이스 설명자 조사 및 USB 전송을 수행합니다.

### <a name="topology-manager"></a>토폴로지 관리자

USB 스택 토폴로지 스레드는 새 디바이스가 연결되거나 디바이스의 연결이 끊어질 때 활성화됩니다. 루트 허브 또는 일반 허브는 디바이스 연결을 허용할 수 있습니다. 디바이스가 USB에 연결되면 토폴로지 관리자가 디바이스 설명자를 검색합니다. 이 설명자에는 이 디바이스에 사용 가능한 구성의 수가 포함됩니다. 대부분의 디바이스는 한 가지 구성만 있습니다. 일부 디바이스는 연결된 포트에서 사용 가능한 전원에 따라 다르게 작동할 수 있습니다. 이 경우 사용 가능한 전원에 따라 디바이스에서 여러 구성 중에 선택할 수 있습니다. 토폴로지 관리자가 디바이스를 구성한 후에는 구성 설명자에 지정된 양의 전력을 디바이스로 끌어올 수 있습니다.

## <a name="usb-class-binding"></a>USB 클래스 바인딩

디바이스가 구성되면 토폴로지 관리자는 디바이스 인터페이스 설명자를 살펴보고 클래스 관리자가 디바이스를 계속 검색하도록 허용할 수 있습니다. 한 디바이스에 하나 이상의 인터페이스 설명자가 있을 수 있습니다.

인터페이스는 디바이스의 기능을 나타냅니다. 예를 들어 USB 스피커에는 세 개의 인터페이스가 있습니다. 하나는 오디오 스트리밍, 하나는 오디오 컨트롤, 나머지 하나는 다양한 스피커 단추를 관리하는 데 사용됩니다.

클래스 관리자는 디바이스 인터페이스를 하나 이상의 클래스에 조인하는 두 가지 메커니즘을 갖고 있습니다. 인터페이스 설명자에 표시된 PID/VID(제품 ID 및 공급업체 ID) 조합 또는 클래스/하위 클래스/프로토콜 조합을 사용할 수 있습니다.

PID/VID 조합은 일반 클래스로 구동할 수 없는 인터페이스에 유효합니다. 클래스/하위 클래스/프로토콜 조합은 프린터, 허브, 스토리지, 오디오 또는 HID와 같은 USB-IF 인증 클래스에 속하는 인터페이스에 사용됩니다.

클래스 관리자는 USBX 초기화에서 등록된 클래스 목록을 포함하고 있습니다. 클래스 관리자는 한 클래스에서 해당 디바이스의 인터페이스 관리를 수락할 때까지 각 클래스를 한 번에 하나씩 호출합니다. 클래스는 하나의 인터페이스만 관리할 수 있습니다. USB 오디오 스피커에 대한 예제에서는 클래스 관리자가 인터페이스마다 모든 클래스를 호출합니다.

한 클래스에서 인터페이스를 수락하면 해당 클래스의 새 인스턴스가 만들어집니다. 그러면 클래스 관리자는 인터페이스의 기본 대체 설정을 검색합니다. 디바이스는 각 인터페이스에 대한 하나 이상의 대체 설정을 가질 수 있습니다. 클래스에서 변경을 결정할 때까지 기본적으로 대체 설정 0이 사용됩니다.

기본 대체 설정의 경우 클래스 관리자는 대체 설정에 포함된 모든 엔드포인트를 탑재합니다. 각 엔드포인트의 탑재가 성공하면 클래스 관리자는 인터페이스 초기화를 완료할 클래스로 돌아가서 작업을 완료합니다.

### <a name="usbx-apis"></a>USBX API

USB 스택은 특정 엔드포인트에서 디바이스 및 USB 전송에 대한 조사를 수행하기 위해 USB 클래스에 대한 특정 개수의 API를 내보냅니다. 이러한 API 함수는 이 참조 설명서에 자세히 설명되어 있습니다.

### <a name="host-controller"></a>호스트 컨트롤러

호스트 컨트롤러 드라이버는 특정 유형의 USB 컨트롤러를 구동하는 일을 담당합니다. USB 호스트 컨트롤러 안에 여러 개의 컨트롤러가 있을 수 있습니다. 예를 들어 특정 Intel PC 칩셋에는 두 개의 UHCI 컨트롤러가 있습니다. 일부 USB 2.0 컨트롤러에는 EHCI 컨트롤러의 인스턴스 하나 외에도 OHCI 컨트롤러의 여러 인스턴스가 포함되어 있습니다.

호스트 컨트롤러는 동일한 컨트롤러의 여러 인스턴스만 관리합니다. 대부분의 USB 2.0 호스트 컨트롤러를 구동하려면 USBX를 초기화하는 동안 OCHI 컨트롤러와 EHCI 컨트롤러를 모두 초기화해야 합니다.

호스트 컨트롤러는 다음과 같은 관리를 담당합니다.

- 루트 허브
- 전원 관리
- 엔드포인트
- 전송

### <a name="root-hub"></a>루트 허브

루트 허브 관리는 각 컨트롤러 포트에 전원을 공급하고 디바이스가 삽입되었는지 여부를 확인하는 일을 담당합니다. 이 기능은 USBX 일반 루트 허브에서 컨트롤러 다운스트림 포트를 조사하는 데 사용됩니다.

### <a name="power-management"></a>전원 관리

전원 관리 처리는 갱 모드에서 일시 중단/다시 시작 신호를 처리하기 위해 제공되므로, 동시에 모든 컨트롤러 다운스트림 포트에 영향을 줍니다. 또는 컨트롤러에서 이 기능을 제공하는 경우에는 개별적으로 영향을 줍니다.

### <a name="endpoints"></a>엔드포인트

엔드포인트 관리는 컨트롤러에 대한 실제 엔드포인트를 만들거나 제거하는 기능을 제공합니다. 실제 엔드포인트는 컨트롤러에서 구문 분석하는 메모리 엔터티(컨트롤러에서 마스터 DMA를 지원하는 경우) 또는 컨트롤러에서 작성되는 메모리 엔터티입니다. 물리적 엔드포인트는 컨트롤러에서 수행할 트랜잭션 정보를 포함합니다.

### <a name="transfers"></a>전송

전송 관리는 생성된 각 엔드포인트에서 트랜잭션을 수행하는 클래스를 제공합니다. 각 논리 엔드포인트에는 USB 전송 요청에 사용되는 TRANSFER REQUEST라는 구성 요소가 포함되어 있습니다. TRANSFER REQUEST는 트랜잭션을 설명하기 위해 스택에서 사용됩니다. 그러면 이 TRANSFER REQUEST는 스택과 컨트롤러에 전달되고, 컨트롤러의 기능에 따라 여러 하위 트랜잭션으로 분할될 수 있습니다.

## <a name="usb-device-framework"></a>USB 디바이스 프레임워크

USB 디바이스는 설명자 트리로 표시됩니다. 6가지 기본 설명자 형식이 있습니다.

- 디바이스 설명자
- 구성 설명자
- 인터페이스 설명자
- 엔드포인트 설명자
- 문자열 설명자
- 함수 설명자

USB 디바이스는 매우 간단한 설명을 포함할 수 있으며 다음과 같은 모습입니다.
![간단한 USB 디바이스](./media/usbx-host-stack/usb-device-simple.png)

위의 그림에서 디바이스 구성은 하나뿐입니다. 단일 인터페이스가 이 구성에 연결되고, 디바이스에 함수와 엔드포인트가 각각 하나씩만 있음을 나타냅니다. 디바이스 설명자에 연결된 문자열 설명자는 디바이스를 시각적으로 식별합니다.

그러나 디바이스가 더 복잡할 수 있으며 다음과 같은 모습일 수 있습니다.

![복잡한 USB 디바이스](./media/usbx-host-stack/usb-device-complex.png)

위의 그림에서는 디바이스의 구성 설명자 2개가 디바이스 설명자에 연결되었습니다. 이 디바이스는 두 가지 전원 모드가 있거나 표준 클래스 또는 독점 클래스를 통해 구동 가능하다는 의미일 수 있습니다.

첫 번째 구성에 연결된 두 개의 인터페이스는 디바이스에 두 가지 논리 함수가 있음을 나타냅니다. 첫 번째 함수에는 엔드포인트 설명자 3개와 함수 설명자 하나가 포함되어 있습니다. 인터페이스를 구동하는 클래스에서 함수 설명자를 사용하여 제네릭 설명자에서 일반적으로 찾을 수 없는 이 인터페이스에 대한 추가 정보를 얻을 수도 있습니다.

### <a name="device-descriptors"></a>디바이스 설명자

각 USB 디바이스에는 디바이스 설명자가 하나씩 있습니다. 이 설명자에는 디바이스 ID, 지원되는 구성 수, 디바이스를 구성하는 데 사용되는 기본 제어 엔드포인트의 특성이 포함됩니다.

| Offset | 필드              | Size | 값    | 설명                             |
| ------ | ------------------ | ---- | -------- | --------------------------------------- |
| 0      | BLength            | 1    | 숫자   | 이 설명자의 크기(바이트) |
| 1      | bDescriptorType    | 1    | 상수 | 디바이스 설명자 형식 |
| 2      | bcdUSB             | 2    | BCD      | BinaryCoded 설명자의 USB 사양 릴리스 번호<br />예: 2.10은 0x210과 동일합니다. 이 필드는 디바이스와 디바이스의 설명자가 호환되는 USB 사양의 릴리스를 식별합니다. |
| 4      | bDeviceClass       | 1    | 클래스    | 클래스 코드(USB-IF에서 할당)<br />이 필드를 0으로 초기화하면 구성 내의 각 인터페이스는 자체 클래스 정보를 지정하고 다양한 인터페이스가 독립적으로 작동합니다.<br />이 필드를 1 ~ 0xFE 사이의 값으로 설정하면 디바이스는 다른 인터페이스에서 다른 클래스 사양을 지원하며 인터페이스가 독립적으로 작동하지 않을 수 있습니다. 이 값은 집계 인터페이스에 사용되는 클래스 정의를 식별합니다.<br />이 필드가 0xFF로 설정되면 디바이스 클래스는 공급업체와 관련이 있습니다. |
| 5      | bDeviceSubClass    | 1    | 하위 클래스 | 하위 클래스 코드(USB-IF에서 할당)<br />이러한 코드는 bDeviceClass 필드의 값으로 한정됩니다. bDeviceClass 필드를 0으로 초기화하는 경우 이 필드도 0으로 초기화해야 합니다. bDeviceClass 필드가 0xFF로 설정되지 않은 경우 모든 값은 USB에서 할당하도록 예약됩니다. |
| 6      | bDeviceProtocol    | 1    | 프로토콜 | 프로토콜 코드(USB-IF에서 할당)<br />이러한 코드는 bDeviceClass 및 bDeviceSubClass 필드의 값으로 한정됩니다. 디바이스에서 인터페이스 기반이 아닌 디바이스 기반으로 클래스 관련 프로토콜을 지원하는 경우 이 코드는 디바이스 클래스의 사양에 정의된 대로 디바이스에서 사용하는 프로토콜을 식별합니다. 이 필드를 0으로 초기화하면 디바이스에 따라 클래스 관련 프로토콜이 사용되지 않습니다.<br />그러나 인터페이스에 따라 클래스 관련 프로토콜을 사용할 수 있습니다.<br />이 필드를 0xFF로 설정하면 디바이스에 따라 공급업체의 프로토콜이 사용됩니다. |
| 7      | bMaxPacketSize0    | 1    | 숫자   | 엔드포인트 0의 최대 패킷 크기(8, 16, 32 또는 64바이트 크기만 유효) |
| 8      | idVendor           | 2    | ID       | 공급업체 ID(USB-IF에서 할당) |
| 10     | idProduct          | 2    | ID       | 제품 ID(제조업체에서 할당) |
| 12     | bcdDevice          | 2    | BCD      | 이진 코딩된 10진수 디바이스 릴리스 번호 |
| 14     | iManufacturer      | 1    | 인덱스    | 제조업체를 설명하는 문자열 설명자 인덱스 |
| 15     | iProduct           | 1    | 인덱스    | 제품을 설명하는 문자열 설명자 인덱스 |
| 16     | iSerialNumbe       | 1    | 인덱스    | 디바이스의 일련 번호를 설명하는 문자열 설명자 인덱스 |
| 17     | bNumConfigurations | 1    | 숫자   | 가능한 구성 수 |

USBX는 다음과 같이 USB 디바이스 설명자를 정의합니다.

```c
typedef struct UX_DEVICE_DESCRIPTOR_STRUCT
{
    UINT      bLength;
    UINT      bDescriptorType;
    USHORT    bcdUSB;
    UINT      bDeviceClass;
    UINT      bDeviceSubClass;
    UINT      bDeviceProtocol;
    UINT      bMaxPacketSize0;
    USHORT    idVendor;
    USHORT    idProduct;
    USHORT    bcdDevice;
    UINT      iManufacturer;
    UINT      iProduct;
    UINT      iSerialNumber;
    UINT      bNumConfigurations;
} UX_DEVICE_DESCRIPTOR;
```

USB 디바이스 설명자는 다음 설명처럼 디바이스 컨테이너의 일부입니다.

```c
typedef struct UX_DEVICE_STRUCT
{
    ULONG ux_device_handle;
    ULONG ux_device_type;
    ULONG ux_device_state;
    ULONG ux_device_address;
    ULONG ux_device_speed;
    ULONG ux_device_port_location;
    ULONG ux_device_max_power;
    ULONG ux_device_power_source;
    UINT ux_device_current_configuration;

    TX_SEMAPHORE ux_device_protection_semaphore;
    struct UX_DEVICE_STRUCT *ux_device_parent; 
    struct UX_HOST_CLASS_STRUCT *ux_device_class; 
    VOID *ux_device_class_instance;
    struct UX_HCD_STRUCT *ux_device_hcd;
    struct UX_CONFIGURATION_STRUCT *ux_device_first_configuration; 
    struct UX_DEVICE_STRUCT *ux_device_next_device;
    struct UX_DEVICE_DESCRIPTOR_STRUCT ux_device_descriptor;
    struct UX_ENDPOINT_STRUCT ux_device_control_endpoint;
    struct UX_HUB_TT_STRUCT ux_device_hub_tt[UX_MAX_TT];
} UX_DEVICE;
```

- **ux_device_handle**: 디바이스의 핸들. 일반적으로 디바이스에 대한 이 구조의 인스턴스 주소입니다.
- **ux_device_type**: 사용되지 않는 값. 사용되지 않습니다.
- **ux_device_state**: 디바이스 상태이며 다음 값 중 하나입니다.
    - **UX_DEVICE_RESET**                0
    - **UX_DEVICE_ATTACHED**             1
    - **UX_DEVICE_ADDRESSED**            2
    - **UX_DEVICE_CONFIGURED**           3
    - **UX_DEVICE_SUSPENDED**            4
    - **UX_DEVICE_RESUMED**              5
    - **UX_DEVICE_SELF_POWERED_STATE**   6
    - **UX_DEVICE_SELF_POWERED_STATE**   7
    - **UX_DEVICE_REMOTE_WAKEUP**        8
    - **UX_DEVICE_BUS_RESET_COMPLETED**  9
    - **UX_DEVICE_REMOVED**              10
    - **UX_DEVICE_FORCE_DISCONNECT**     11
- **ux_device_address**: **SET_ADDRESS** 명령이 수락된 후의 디바이스 주소(1 ~ 127)
- **ux_device_speed**: 디바이스의 속도:
    - **UX_LOW_SPEED_DEVICE**      0
    - **UX_FULL_SPEED_DEVICE**     1
    - **UX_HIGH_SPEED_DEVICE**     2
- **ux_device_port_location**: 부모 디바이스의 포트 인덱스(루트 허브 또는 허브)
- **ux_device_max_power**: 선택한 구성에서 디바이스가 사용할 수 있는 최대 전력(mA)
- **ux_device_power_source**: 다음 두 값 중 하나입니다.
    - **UX_DEVICE_BUS_POWERED**     1
    - **UX_DEVICE_SELF_POWERED**    2
- **ux_device_current_configuration**:이 디바이스에서 사용 중인 현재 구성의 인덱스
- **ux_device_parent**: 이 디바이스의 부모에 대한 디바이스 컨테이너 포인터. 포인터가 null이면 부모는 컨트롤러의 루트 허브입니다.
- **ux_device_class**: 이 디바이스를 소유한 클래스 형식에 대한 포인터
- **ux_device_class_instance**: 이 디바이스를 소유한 클래스의 인스턴스에 대한 포인터
- **ux_device_hcd**: 이 디바이스가 연결된 USB 호스트 컨트롤러 인스턴스
- **ux_device_first_configuration**: 이 디바이스의 첫 번째 구성 컨테이너에 대한 포인터
- **ux_device_next_device**: USBX에서 발견한 버스의 디바이스 목록에서 다음 디바이스를 가리키는 포인터
- **ux_device_descriptor**: USB 디바이스 설명자
- **ux_device_control_endpoint**: 이 디바이스에서 사용하는 기본 제어 엔드포인트의 설명자
- **ux_device_hub_tt**: 디바이스의 허브 TT 배열

### <a name="configuration-descriptors"></a>구성 설명자

구성 설명자는 특정 디바이스 구성에 대한 정보를 설명합니다. USB 디바이스는 하나 이상의 구성 설명자를 포함할 수 있습니다. 디바이스 설명자의 **bNumConfigurations** 필드는 구성 설명자의 수를 나타냅니다. 설명자에는 **bConfigurationValue** 필드가 포함되어 있습니다. 이 필드의 값을 Set Configuration 요청의 매개 변수로 사용하면 디바이스는 설명된 구성을 전제로 합니다.

설명자는 구성에서 제공하는 인터페이스 수를 설명합니다. 각 인터페이스는 디바이스 내의 논리 함수를 나타내며 독립적으로 작동할 수 있습니다. 예를 들어 USB 오디오 스피커에는 오디오 스트리밍을 위한 인터페이스, 오디오 제어를 위한 인터페이스, 스피커 단추를 관리하기 위한 HID 인터페이스가 각각 하나씩 있을 수 있습니다.

호스트에서 구성 설명자에 대한 GET_DESCRIPTOR 요청을 실행하면 관련된 모든 인터페이스 및 엔드포인트 설명자가 반환됩니다.

| Offset | 필드               | Size | 값    | 설명                       |
| ------ | ------------------- | ---- | -------- | --------------------------------- |
| 0      | bLength             | 1    | 숫자   | 이 설명자의 크기(바이트) |
| 1      | bDescriptorType     | 1    | 상수 | CONFIGURATION                     |
| 2      | wTotalLength        | 2    | 숫자   | 이 구성에 대해 반환된 총 데이터 길이. 이 구성에 대해 반환된 모든 설명자(구성, 인터페이스, 엔드포인트 및 클래스 또는 공급업체 설명자)의 총 길이를 포함합니다. |
| 4      | bNumInterfaces      | 1    | 숫자   | 이 구성에서 지원하는 인터페이스 수 |
| 5      | bConfigurationValue | 1    | 숫자   | 이 구성을 선택하려면<br/>Set Configuration의 인수로 사용해야 하는 값 |
| 6      | iConfiguration      | 1    | 인덱스    | 이 구성을 설명하는 문자열 설명자 인덱스 |
| 7      | bMAttributes        | 1    | Bitmap   | 구성 특성 D7 버스 전력 사용<br />D6 자체 전력<br />D5 원격 절전 모드 해제<br />D4..0 예약됨(0으로 초기화)<br />버스의 전력을 사용하는 디바이스 구성이며 로컬 소스는 D7 및 D6을 모두 설정합니다. 런타임의 실제 전력원은 Get Status 디바이스 요청을 사용하여 확인할 수 있습니다.<br />디바이스 구성에서 원격 절전 모드 해제를 지원하는 경우 D5는 1로 설정됩니다. |
| 8      | MaxPower            | 1    | mA       | 디바이스가 완전히 작동할 때 이 구성에서 USB 디바이스가 사용하는 버스의 최대 소비 전력.<br />2mA 단위로 표현됩니다(예: 50 = 100mA).<br />참고: 디바이스 구성은 버스 전력을 사용하는 구성인지 아니면 자체 전력을 사용하는 구성인지 보고합니다.<br />디바이스 상태는 디바이스가 현재 자체 전력으로 구동하는지 여부를 보고합니다. 디바이스는 외부 전원에서 분리되면 더 이상 자체 전력으로 구동되지 않는다는 것을 알리기 위해 디바이스 상태를 업데이트합니다. |

USBX는 다음과 같이 USB 구성 설명자를 정의합니다.

```c
typedef struct UX_CONFIGURATION_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT wTotalLength;
    UINT bNumInterfaces;
    UINT bConfigurationValue;
    UINT iConfiguration;
    UINT bmAttributes;
    UINT MaxPower;
} UX_CONFIGURATION_DESCRIPTOR;
```

USB 구성 설명자는 아래에 설명된 것처럼 구성 컨테이너의 일부입니다.

```c
typedef struct UX_CONFIGURATION_STRUCT
{
    ULONG ux_configuration_handle;
    ULONG ux_configuration_state;
    struct UX_CONFIGURATION_DESCRIPTOR_STRUCT ux_configuration_descriptor;
    struct UX_INTERFACE_STRUCT *ux_configuration_first_interface;
    struct UX_CONFIGURATION_STRUCT *ux_configuration_next_configuration;
    struct UX_DEVICE_STRUCT *ux_configuration_device;
} UX_CONFIGURATION;
```

- **ux_configuration_handle**: 구성의 핸들. 일반적으로 구성에 대한 이 구조의 인스턴스 주소입니다.
- **ux_configuration_state**: 구성 상태
- **ux_configuration_descriptor**: USB 디바이스 설명자
- **ux_configuration_first_interface**: 이 구성의 첫 번째 인터페이스에 대한 포인터
- **ux_configuration_next_configuration**: 동일한 디바이스의 다음 구성에 대한 포인터
- **ux_configuration_device**: 이 구성의 디바이스 소유자에 대한 포인터

### <a name="interface-descriptors"></a>인터페이스 설명자

인터페이스 설명자는 구성 내의 특정 인터페이스에 대해 설명합니다. 인터페이스는 USB 디바이스 내의 논리 함수입니다. 구성은 하나 이상의 인터페이스를 제공하며, 각 인터페이스에는 구성 내의 고유한 엔드포인트 세트를 설명하는 0개 이상의 엔드포인트 설명자가 있습니다. 구성에서 두 개 이상의 인터페이스를 지원하는 경우 특정 인터페이스의 엔드포인트 설명자는 지정된 구성에 대한 **GET_DESCRIPTOR** 요청에서 반환되는 데이터의 인터페이스 설명자를 따릅니다.

인터페이스 설명자는 항상 구성 설명자의 일부로 반환됩니다. 인터페이스 설명자는 GET_DESCRIPTOR 요청을 통해 직접 액세스할 수 없습니다.

인터페이스는 디바이스를 구성한 후 엔드포인트 및/또는 해당 특성이 달라지는 것을 허용하는 대체 설정을 포함할 수 있습니다. 인터페이스의 기본 설정은 항상 대체 설정 0입니다. 클래스에서 현재 대체 설정을 변경하도록 선택하여 연결된 엔드포인트의 인터페이스 동작 및 특성을 변경할 수 있습니다. SET_INTERFACE 요청은 대체 설정을 선택하거나 기본 설정으로 되돌리는 데 사용됩니다.

대체 설정을 사용하면 다른 인터페이스는 작동 중인 상태로 유지되면서 디바이스 구성의 일부가 달라질 수 있습니다. 구성에 해당 인터페이스 중 하나 이상에 대한 대체 설정이 포함되어 있으면 각 설정에 대해 별도의 인터페이스 설명자 및 연결된 엔드포인트가 포함됩니다.

디바이스 구성에 두 가지 대체 설정이 포함된 단일 인터페이스가 있으면 구성에 대한 GET_DESCRIPTOR 요청에서는 구성 설명자를 반환합니다. 그런 다음, **bInterfaceNumber** 및 **bAlternateSetting** 필드가 0으로 설정된 인터페이스 설명자를 반환하고, 그 다음에는 해당 설정에 대한 엔드포인트 설명자, 다른 인터페이스 설명자 및 연결된 엔드포인트 설명자를 차례로 반환합니다. 두 번째 인터페이스 설명자의 **bInterfaceNumber** 필드도 0으로 설정되지만, 두 번째 인터페이스 설명자의 **bAlternateSetting** 필드는 이 대체 설정이 첫 번째 인터페이스에 속한다는 것을 나타내는 1로 설정됩니다.

인터페이스에 연결된 엔트포인트가 없을 수 있습니다. 이 경우에는 해당 인터페이스에는 기본 제어 엔드포인트만 유효합니다.

대체 설정은 인터페이스와 연결된 주기적 엔드포인트에 대해 요청된 대역폭을 변경하는 데 주로 사용됩니다. 예를 들어 USB 스피커 스트리밍 인터페이스는 등시 엔드포인트에서 대역폭 요구 사항이 0인 첫 번째 대체 설정이 있어야 합니다. 다른 대체 설정은 오디오 스트리밍 빈도에 따라 다른 대역폭 요구 사항을 선택할 수 있습니다.

인터페이스의 USB 설명자는 다음과 같습니다.

| Offset | 필드              | Size | 값     | 설명자                              |
| ------ | ------------------ | ---- | --------- | --------------------------------------- |
| 0      | bLength            | 1    | 숫자    | 이 설명자의 크기(바이트)       |
| 1      | bDescriptorType    | 1    | 상수  | 인터페이스 설명자 형식               |
| 2      | bInterfaceNumber   | 1    | 숫자    | 인터페이스 수. 이 구성에서 지원하는 동시 인터페이스 배열의 인덱스를 식별하며 0부터 시작하는 값 |
| 3      | bAltenateSetting   | 1    | 숫자    | 이전 필드에서 식별된 인터페이스의 대체 설정을 선택하는 데 사용되는 값 |
| 4      | bNumEndpoints      | 1    | 숫자    | 이 인터페이스에서 사용하는 엔드포인트 수(엔드포인트 0 제외). 이 값이 0이면 이 인터페이스는 엔드포인트 0만 사용합니다. |
| 5      | bInterfaceClass    | 1    | 클래스     | 클래스 코드(USB에서 할당)<br />이 필드를 0으로 초기화하면 인터페이스는 USB에서 지정한 디바이스 클래스에 속하지 않습니다.<br />이 필드가 0xFF로 설정되면 인터페이스 클래스는 공급업체와 관련이 있습니다.<br />그 외의 값은 USB에서 할당하도록 예약되어 있습니다. |
| 6      | bInterfaceSubClass | 1    | 하위 클래스  | 하위 클래스 코드(USB에서 할당)<br />이러한 코드는 bInterfaceClass 필드의 값으로 한정됩니다. bInterfaceClass 필드를 0으로 초기화하는 경우 이 필드도 0으로 초기화해야 합니다. bInterfaceClass 필드가 0xFF로 설정되지 않은 경우 모든 값은 USB에서 할당하도록 예약됩니다. |
| 7      | bInterfaceProtocol | 1    | 프로토콜  | 프로토콜 코드(USB에서 할당) 이러한 코드는 bInterfaceClass 및 bInterfaceSubClass 필드의 값으로 한정됩니다. 인터페이스에서 클래스 관련 요청을 지원하는 경우 이 코드는 디바이스에서 디바이스 클래스 사양에 정의된 대로 사용하는 프로토콜을 식별합니다.<br />이 필드를 0으로 초기화하면 디바이스가 이 인터페이스의 클래스 관련 프로토콜을 사용하지 않습니다. 이 필드를 0xFF로 설정하면 디바이스가 이 인터페이스의 공급업체 프로토콜을 사용합니다. |
| 8      | iInterface         | 1    | 인덱스     | 이 인터페이스를 설명하는 문자열 설명자 인덱스 |

USBX는 다음과 같이 USB 인터페이스 설명자를 정의합니다.

```c
typedef struct UX_INTERFACE_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    UINT bInterfaceNumber;
    UINT bAlternateSetting;
    UINT bNumEndpoints;
    UINT bInterfaceClass
    UINT bInterfaceSubClass;
    UINT bInterfaceProtocol;
    UINT iInterface;
} UX_INTERFACE_DESCRIPTOR;
```

USB 인터페이스 설명자는 다음 설명과 같이 인터페이스 컨테이너의 일부입니다.

```c
typedef struct UX_INTERFACE_STRUCT
{
    ULONG ux_interface_handle;
    ULONG ux_interface_state;
    ULONG ux_interface_current_alternate_setting;
    struct UX_INTERFACE_DESCRIPTOR_STRUCT ux_interface_descriptor;
    struct UX_HOST_CLASS_STRUCT    *ux_interface_class;
    VOID    *ux_interface_class_instance;
    struct UX_ENDPOINT_STRUCT    *ux_interface_first_endpoint;
    struct UX_INTERFACE_STRUCT    *ux_interface_next_interface;
    struct UX_CONFIGURATION_STRUCT    *ux_interface_configuration;
} UX_INTERFACE;
```

- **ux_interface_handle**: 인터페이스의 핸들. 일반적으로 인터페이스에 대한 이 구조의 인스턴스 주소입니다.
- **ux_interface_state**: 인터페이스의 상태
- **ux_interface_descriptor**: USB 인터페이스 설명자
- **ux_interface_class**: 이 인터페이스를 소유한 클래스 형식에 대한 포인터
- **ux_interface_class_instance**: 이 인터페이스를 소유한 클래스의 인스턴스에 대한 포인터
- **ux_interface_first_endpoint**: 이 인터페이스에 등록된 첫 번째 엔드포인트에 대한 포인터입니다.
- **ux_interface_next_interface**: 구성과 연결된 다음 인터페이스에 대한 포인터
- **ux_interface_configuration**: 이 인터페이스의 구성 소유자에 대한 포인터

### <a name="endpoint-descriptors"></a>엔드포인트 설명자

인터페이스와 연결된 엔드포인트마다 고유한 엔드포인트 설명자가 있습니다. 이 설명자에는 호스트 스택에서 각 엔드포인트의 대역폭 요구 사항, 엔드포인트와 연결된 최대 페이로드, 주기 및 방향을 결정하기 위해 필요한 정보가 포함되어 있습니다. 엔드포인트 설명자는 항상 구성에 대한 GET_DESCRIPTOR 명령을 통해 반환됩니다.

디바이스 설명자와 연결된 기본 제어 엔드포인트는 인터페이스와 연결된 엔드포인트로 계산되지 않으므로 이 설명자에 반환되지 않습니다.

호스트 소프트웨어에서 인터페이스의 대체 설정 변경을 요청하면 연결된 모든 엔드포인트와 해당 USB 리소스는 새로운 대체 설정에 따라 수정됩니다.

기본 제어 엔드포인트를 제외하고 인터페이스 간에 엔드포인트를 공유할 수 없습니다.

| Offset | 필드            | Size | 값    | 설명                       |
| ------ | ---------------- | ---- | -------- | --------------------------------- |
| 0      | bLength          | 1    | 숫자   | 이 설명자의 크기(바이트) |
| 1      | bDescriptorType  | 1    | 상수 | 엔드포인트 설명자 형식 |
| 2      | bEndpointAddress | 1    | 엔드포인트 | 이 설명자가 설명하는 USB 디바이스의 엔드포인트 주소. 주소는 다음과 같이 인코딩됩니다.<br />Bit 3...0: 엔드포인트 번호<br />Bit 6...4: 예약됨, 0으로 초기화<br />Bit 7: 방향, 제어 엔드포인트에서 무시됨<br />0 = 출력 엔드포인트<br />1 = 입력 엔드포인트 |
| 3      | bmAttributes     | 1    | Bitmap   | 이 필드는 **bConfigurationValue** 필드를 사용하여 구성되는 엔드포인트의 특성을 설명합니다. 비트 1..0: 전송 형식<br />00 = 컨트롤<br />01 = 등시<br />10 = 대량<br />11 = 인터럽트<br />등시 엔드포인트가 아닌 경우 비트 5..2는 예약되어 있으므로 0으로 설정해야 합니다. 등시인 경우 다음과 같이 정의됩니다.<br />비트 3..2: 동기화 형식<br />00 = 동기화 없음<br />01 = 비동기<br />10 = 적응형<br />11 = 동기<br />비트 5..4: 사용 유형<br />00 = 데이터 엔드포인트<br />01 = 피드백 엔드포인트<br />10 = 암시적 피드백 데이터 엔드포인트<br />11 = 예약됨 |
| 4      | wMaxPacketSize   | 2    | 숫자   | 이 구성을 선택하면 이 엔드포인트에서 보내거나 받을 수 있는 최대 패킷 크기.<br />등시 엔드포인트의 경우 이 값은 일정에서 버스 시간을 예약하는 데 사용되며 (마이크로)프레임 데이터 페이로드에 필요합니다. 파이프에서 사용하는 대역폭이 예약된 대역폭보다 지속적으로 작을 수 있습니다. 디바이스는 필요에 따라 일반적인 비-USB 정의 메커니즘을 통해 사용되는 실제 대역폭을 보고합니다.<br />모든 엔드포인트에서 비트 10..0은 최대 패킷 크기(바이트)를 지정합니다.<br />고속 등시 및 인터럽트 엔드포인트 경우:<br />비트 12..11은 마이크로프레임당 추가 트랜잭션 기회 수를 다음과 같이 지정합니다. 00 = 없음(마이크로프레임당 트랜잭션 1개)<br />01 = 1개 추가(마이크로프레임당 2개)<br />10 = 2개 추가(마이크로프레임당 3개)<br />11 = 예약됨<br />비트 15..13은 예약되어 있으며 0으로 설정해야 합니다. |
| 6      | bInterval        | 1     | 숫자   | 데이터 전송에 대한 폴링 엔드포인트의 숫자 간격입니다.<br />디바이스 작동 속도에 따라 프레임 또는 마이크로프레임으로 표현합니다(예: 1밀리초 또는 125μs 단위).<br />전체/고속 등시 엔드포인트의 경우 이 값은 1 ~ 16 사이여야 합니다. **bInterval** 은 2bInterval-1 값의 지수로 사용됩니다. 예를 들어 **bInterval** 4는 8(24-1)이라는 기간을 의미합니다.<br />전체/저속 인터럽트 엔드포인트의 경우 이 필드의 값은 1 ~ 255입니다.<br />고속 인터럽트 엔드포인트의 경우 **bInterval** 은 2bInterval-1 값의 지수로 사용됩니다. 예를 들어 **bInterval** 4는 8(24-1)이라는 기간을 의미합니다. 이 값은 1 ~ 16이여야 합니다.<br />고속 대량/제어 출력 엔드포인트의 경우 **bInterval** 은 엔드포인트의 최대 NAK 속도를 지정합니다. 값 0은 엔드포인트가 NAK를 수행하지 않는다는 뜻입니다. 다른 값은 마이크로프레임의 **bInterval** 마다 최대 1개의 NAK가 있다는 뜻입니다.<br />이 값은 0 ~ 255여야 합니다. |

USBX는 다음과 같이 USB 엔드포인트 설명자를 정의합니다.

```c
typedef struct UX_ENDPOINT_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    UINT bEndpointAddress;
    UINT bmAttributes;
    USHORT wMaxPacketSize;
    UINT bInterval;
} UX_ENDPOINT_DESCRIPTOR;
```

USB 엔드포인트 설명자는 다음 설명과 같이 엔드포인트 컨테이너의 일부입니다.

```c
typedef struct UX_ENDPOINT_STRUCT {
    ULONG    ux_endpoint_handle;
    ULONG    ux_endpoint_state;
    VOID    *ux_endpoint_ed;
    struct UX_ENDPOINT_DESCRIPTOR_STRUCT    ux_endpoint_descriptor;
    struct UX_ENDPOINT_STRUCT    *ux_endpoint_next_endpoint;
    struct UX_INTERFACE_STRUCT    *ux_endpoint_interface;
    struct UX_DEVICE_STRUCT    *ux_endpoint_device;
    struct UX_TRANSFER REQUEST_STRUCT    ux_endpoint_transfer request;
} UX_ENDPOINT;

```

- **ux_endpoint_handle**: 엔드포인트의 핸들. 일반적으로 엔드포인트에 대한 이 구조의 인스턴스 주소입니다.
- **ux_endpoint_state**: 엔드포인트의 상태
- **ux_endpoint_ed**: 호스트 컨트롤러 계층의 실제 엔드포인트에 대한 포인터
- **ux_endpoint_descriptor**: USB 엔드포인트 설명자
- **ux_endpoint_next_endpoint**: 동일한 인터페이스에 속하는 다음 엔드포인트에 대한 포인터
- **ux_endpoint_interface**: 이 엔드포인트 인터페이스를 소유한 인터페이스에 대한 포인터
- **ux_endpoint_device**: 부모 디바이스 컨테이너에 대한 포인터
- **ux_endpoint_transfer 요청**: 디바이스와 데이터를 주고 받는 데 사용되는 USB 전송 요청

### <a name="string-descriptors"></a>문자열 설명자

문자열 설명자는 선택 사항입니다. 디바이스에서 문자열 설명자를 지원하지 않는 경우 디바이스, 구성 및 인터페이스 설명자 내의 문자열 설명자에 대한 모든 참조를 0으로 초기화해야 합니다.

문자열 설명자는 유니코드 인코딩을 사용하므로 여러 문자 세트를 지원할 수 있습니다. USB 디바이스의 문자열은 여러 언어를 지원할 수 있습니다. 문자열 설명자를 요청할 때 요청자는 USB-IF에 정의된 언어 ID를 사용하여 원하는 언어를 지정합니다. 현재 정의된 USB LANGID 목록은 USBX 부록에서 찾을 수 있습니다.
모든 언어의 문자열 인덱스 0은 디바이스에서 지원하는 2바이트 LANGID 코드 배열이 포함된 문자열 설명자를 반환합니다. 유니코드 문자열은 0으로 종료되지 않습니다. 대신 설명자의 첫 번째 바이트에 포함된 배열의 크기에서 2를 빼서 문자열 배열의 크기를 계산합니다.

USB 문자열 설명자 0은 다음과 같이 인코딩됩니다.

| Offset | 필드           | Size | 값    | 설명                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | N+2      | 이 설명자의 크기(바이트) |
| 1      | bDescriptorType | 1    | 상수 | 문자열 설명자 형식           |
| 2      | wLANGID[0]      | 2    | 숫자   | LANGID 코드 0                    |
| ...    | ...]            | ...  | ...      | ...                              |
| N      | wLANGID[n]      | 2    | 숫자   | LANGID 코드 n                    |

다른 USB 문자열 설명자는 다음과 같이 인코딩됩니다.

| Offset | 필드           | Size | 값    | 설명                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | 숫자   | 이 설명자의 크기(바이트) |
| 1      | bDescriptorType | 1    | 상수 | 문자열 설명자 형식           |
| 2      | bString         | n    | 숫자   | 유니코드로 인코딩된 문자열           |

USBX는 다음과 같이 길이가 0이 아닌 USB 문자열 설명자를 정의합니다.

```c
typedef struct UX_STRING_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT bString[1];
} UX_STRING_DESCRIPTOR;
```

### <a name="functional-descriptors"></a>함수 설명자

함수 설명자는 클래스 관련 설명자라고도 합니다. 일반적으로 제네릭 설명자와 동일한 기본 구조를 사용하며 클래스에 추가 정보를 사용할 수 있습니다. 예를 들어 USB 오디오 스피커의 경우 클래스 관련 설명자를 사용하면 오디오 클래스는 각 대체 설정에서 지원되는 오디오 빈도 유형을 검색할 수 있습니다.

### <a name="usbx-device-descriptor-framework-in-memory"></a>메모리의 USBX 디바이스 설명자 프레임워크

USBX는 대부분의 디바이스 설명자, 즉, 문자열 및 함수 설명자를 제외한 모든 설명자를 메모리에 유지합니다. 다음 다이어그램에서는 이러한 설명자를 저장하고 관련 짓는 방법을 보여줍니다.

![메모리의 USBX 디바이스 설명자 프레임워크](./media/usbx-host-stack/usbx-device-descriptor-framework.png)
