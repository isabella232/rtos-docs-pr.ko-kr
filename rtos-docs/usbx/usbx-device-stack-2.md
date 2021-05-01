---
title: 2장 - Azure RTOS USBX 디바이스 스택 설치
description: USBX 설치 방법을 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 097fdd3c6f09c666ec3ad6eda9e5ba3fa159cb4d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813266"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a>2장 - Azure RTOS USBX 디바이스 스택 설치

## <a name="host-considerations"></a>호스트 고려 사항

### <a name="computer-type"></a>컴퓨터 유형

임베디드 개발은 일반적으로 Windows PC 또는 Unix 호스트 컴퓨터에서 수행됩니다. 애플리케이션이 컴파일되거나, 링크되거나 호스트에 배치된 후 실행할 수 있도록 대상 하드웨어에 다운로드됩니다.

### <a name="download-interfaces"></a>인터페이스 다운로드

병렬 인터페이스, USB, 이더넷이 점점 대중화되고 있지만 일반적으로 대상 다운로드는 RS-232 직렬 인터페이스를 통해 수행됩니다. 사용 가능한 옵션은 개발 도구 문서를 참조하세요.

### <a name="debugging-tools"></a>디버깅 도구

디버깅은 일반적으로 프로그램 이미지 다운로드와 동일한 링크를 통해 수행됩니다. 대상에서 실행되는 소형 모니터 프로그램부터 BDM(Background Debug Monitor) 및 ICE(In-Circuit Emulator) 도구까지 다양한 디버거가 존재합니다. ICE 도구는 실제 대상 하드웨어에 대해 가장 강력한 디버깅을 제공합니다.

### <a name="required-hard-disk-space"></a>최소 하드 디스크 공간

USBX의 소스 코드는 ASCII 형식으로 제공되며 호스트 컴퓨터의 하드 디스크에 약 500KB 공간이 필요합니다.

### <a name="target-considerations"></a>대상 고려 사항

USBX에는 호스트 모드의 대상에 24KB에서 64KB 사이의 ROM(읽기 전용 메모리)이 필요합니다. 필요한 메모리 양은 사용된 컨트롤러 유형 및 USBX에 연결된 USB 클래스에 따라 달라집니다. 또한 USBX 글로벌 데이터 구조 및 메모리 풀에 대상의 32KB RAM(Random Access Memory)이 추가로 필요합니다. 이 메모리 풀은 USB의 예상 디바이스 수 및 USB 컨트롤러 유형에 따라 조정될 수 있습니다. USBX 디바이스 측에는 디바이스 컨트롤러 유형에 따라 약 10-12K의 ROM이 필요합니다. RAM 메모리 사용량은 디바이스에서 에뮬레이트되는 클래스 유형에 따라 달라집니다.

또한 USBX에는 ThreadX 세마포, 뮤텍스, 다중 스레드 보호를 위한 스레드, USB 버스 토폴로지 모니터링을 위한 I/O 일시 중단 및 정기적 처리가 필요합니다.

### <a name="product-distribution"></a>제품 배포

Azure RTOS USBX는 <https://github.com/azure-rtos/usbx/>에 있는 공용 소스 코드 리포지토리에서 가져올 수 있습니다.

다음은 리포지토리에 있는 몇 가지 중요한 파일 목록입니다.

* ***ux_api.h***: 이 C 헤더 파일에는 모든 시스템 이큐에이트, 데이터 구조 및 서비스 프로토타입이 포함됩니다.
* ***ux_port.h***: 이 C 헤더 파일에는 모든 개발 도구 관련 데이터 정의 및 구조가 포함됩니다.
* ***ux.lib***: USBX C 라이브러리의 이진 버전입니다. 표준 패키지로 배포됩니다.
* ***demo_usbx.c***: 간단한 USBX 데모가 포함된 C 파일입니다.

모든 파일 이름은 소문자로 표시됩니다. 이 명명 규칙을 사용하면 명령어를 Unix 개발 플랫폼으로 쉽게 변환할 수 있습니다.

## <a name="usbx-installation"></a>USBX 설치

USBX는 GitHub 리포지토리를 로컬 컴퓨터에 복제하여 설치됩니다. 다음은 PC에서 USBX 리포지토리의 복제본을 만들기 위한 일반적인 구문입니다.

```c
    git clone https://github.com/azure-rtos/usbx
```

또는 GitHub 기본 페이지의 다운로드 단추를 사용하여 리포지토리의 복사본을 다운로드할 수 있습니다.

또한 온라인 리포지토리의 프런트 페이지에서 USBX 라이브러리를 빌드하기 위한 지침을 찾을 수 있습니다.

다음 일반 지침은 거의 모든 설치에 적용됩니다.

1. 이전에 호스트 하드 드라이브에 ThreadX를 설치한 것과 동일한 디렉터리를 사용합니다. 모든 USBX 이름은 고유하며 이전 USBX 설치를 방해하지 않습니다.
1. _*_tx_application_define_**의 시작 지점 또는 그 부근에 ***ux_system_initialize** _에 대한 호출을 추가합니다. 여기에서 USBX 리소스가 초기화됩니다.
1. ***ux_device_stack_initialize*** 에 대한 호출을 추가합니다.
1. 필요한 USBX 클래스를 초기화하기 위해 하나 이상의 호출을 추가합니다(호스트 및/또는 디바이스 클래스).
1. 시스템에서 사용 가능한 디바이스 컨트롤러를 초기화하기 위해 하나 이상의 호출을 추가합니다.
1. 하위 수준 하드웨어 초기화를 추가하고 벡터 라우팅을 인터럽트하도록 tx_low_level_initialize.c 파일을 수정해야 할 수 있습니다. 이것은 하드웨어 플랫폼과 관련되며 여기에서 설명하지 않습니다.
1. 애플리케이션 소스 코드를 컴파일하고 USBX 및 ThreadX 런타임 라이브러리(USB 스토리지 클래스 및/또는 USB 네트워크 클래스를 컴파일하려는 경우 FileX 및/또는 Netx도 필요할 수 있음), ux.a(또는 ux.lib) 및 tx.a(또는 tx.lib)를 사용하여 링크합니다. 결과를 대상에 다운로드하고 실행할 수 있습니다.

## <a name="configuration-options"></a>구성 옵션

USBX 라이브러리를 빌드하는 데에는 몇 가지 구성 옵션이 있습니다. 모든 옵션은 ***ux_user.h*** 에 있습니다.

아래 목록에서는 각 구성 옵션에 대해 자세히 설명합니다.

| 구성&nbsp;옵션 | Description |
| --- | --- |
| **UX_PERIODIC_RATE** | 이 값은 특정 하드웨어 플랫폼의 초당 틱 수를 나타냅니다. 기본값은 1000이며 밀리초당 1틱을 나타냅니다. |
| **UX_THREAD_STACK_SIZE** | 이 값은 USBX 스레드의 스택 크기(바이트)입니다. 일반적으로 사용된 프로세스 및 호스트 컨트롤러에 따라 1024바이트 또는 2048바이트일 수 있습니다. |
| **UX_THREAD_PRIORITY_ENUM** | 버스 토폴로지를 모니터링하는 USBX 열거형 스레드의 ThreadX 우선 순위 값입니다. |
| **UX_THREAD_PRIORITY_CLASS** | 표준 USBX 스레드의 ThreadX 우선 순위 값입니다. |
| **UX_THREAD_PRIORITY_KEYBOARD** | USBX HID 키보드 클래스의 ThreadX 우선 순위 값입니다. |
| **UX_THREAD_PRIORITY_DCD** | 디바이스 컨트롤러 스레드의 ThreadX 우선 순위 값입니다. |
| **UX_NO_TIME_SLICE** | 이 값은 스레드에 사용되는 시간 조각을 실제로 정의합니다. 예를 들어, 0으로 정의된 경우 ThreadX 대상 포트는 시간 조각을 사용하지 않습니다. |
| **UX_MAX_SLAVE_CLASS_DRIVER** | ux_device_stack_class_register를 통해 등록될 수 있는 USBX 클래스의 최대 개수입니다. |
| **UX_MAX_SLAVE_LUN** | 이 값은 디바이스 스토리지 클래스 드라이버에 제공된 현재 SCSI 논리적 단위 수를 나타냅니다. |
| **UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC** | 정의된 경우 스토리지 클래스가 MMC(다중 미디어 명령), 즉 DVD-ROM을 처리합니다. |
| **UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES** | 이 값은 CDC-ECM 클래스의 패킷 풀에 있는 NetX 패킷 수를 나타냅니다. 기본값은 16입니다. |
| **UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH** | 이 값은 디바이스 스택에서 제어 엔드포인트에 수신된 최대 바이트 수를 나타냅니다. 기본값은 256바이트이지만 메모리가 제약된 환경에서 감소될 수 있습니다. |
| **UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH** | 이 값은 HID 보고서의 최대 길이(바이트)를 나타냅니다. |
| **UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE** | 이 값은 한 번에 큐에 넣을 수 있는 HID 보고서의 최대 개수를 나타냅니다. |
| **UX_SLAVE_REQUEST_DATA_MAX_LENGTH** | 이 값은 디바이스 스택에서 대량 엔드포인트에 수신되는 최대 바이트 수를 나타냅니다. 기본값은 4096바이트이지만 메모리가 제약된 환경에서 감소될 수 있습니다. |

## <a name="source-code-tree"></a>소스 코드 트리

USBX 파일은 여러 디렉터리에 제공됩니다.

![소스 코드 트리](media/usbx-device-stack/source-code-tree.png)

이름으로 파일을 인식할 수 있도록 다음 규칙이 채택되었습니다.

| 파일 접미사 이름  | 파일 설명                          |
| ----------------- | ----------------------------------------- |
| ux_host_stack   | usbx 호스트 스택 코어 파일                |
| ux_host_class   | usbx 호스트 스택 클래스 파일             |
| ux_hcd           | usbx 호스트 스택 컨트롤러 드라이버 파일   |
| ux_device_stack | usbx 디바이스 스택 코어 파일              |
| ux_device_class | usbx 디바이스 스택 클래스 파일           |
| ux_dcd           | usbx 디바이스 스택 컨트롤러 드라이버 파일 |
| ux_otg           | usbx otg 컨트롤러 드라이버 관련 파일  |
| ux_pictbridge    | usbx pictbridge 파일                     |
| ux_utility       | usbx 유틸리티 함수                    |
| demo_usbx        | USBX의 데모 파일              |

## <a name="initialization-of-usbx-resources"></a>USBX 리소스 초기화

USBX에는 자체 메모리 관리자가 있습니다. USBX의 호스트 또는 디바이스 측이 초기화되기 전 USBX에 메모리를 할당해야 합니다. USBX 메모리 관리자는 메모리를 캐시할 수 있는 시스템을 수용할 수 있습니다.

다음 함수는 일반 메모리 128K로 USBX 메모리 리소스를 초기화하고 캐시 안전 메모리를 위한 별도의 풀은 사용하지 않습니다.

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

ux_system_initialize의 프로토타입은 다음과 같습니다.

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

입력 매개 변수:

| 매개 변수                          | Description                             |
| ---------------------------------- | --------------------------------------- |
| VOID *regular_memory_pool_start    | 일반 메모리 풀의 시작 부분    |
| ULONG regular_memory_size          | 일반 메모리 풀의 크기         |
| VOID *cache_safe_memory_pool_start | 캐시 안전 메모리 풀의 시작 부분 |
| ULONG cache_safe_memory_size       | 캐시 안전 메모리 풀의 크기      |

일부 시스템에는 캐시 안전 메모리 정의가 필요하지 않습니다. 이러한 시스템에서 메모리 포인터 초기화 중 전달되는 값은 UX_NULL로 설정되고 풀 크기는 0으로 설정됩니다. 그런 다음, USBX는 캐시 안전 풀 대신 일반 메모리 풀을 사용합니다.

일반 메모리가 캐시 안전이 아니고 컨트롤러가 DMA 메모리를 수행해야 하는 시스템에서는 캐시 안전 영역에 메모리 풀을 정의해야 합니다.

## <a name="uninitialization-of-usbx-resources"></a>USBX 리소스 초기화 해제

해당 리소스를 해제하여 USBX를 종료할 수 있습니다. USBX를 종료하기 전 모든 클래스 및 컨트롤러 리소스를 적절하게 종료해야 합니다. 다음 함수는 USBX 메모리 리소스를 초기화 해제합니다.

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

ux_system_initialize의 프로토타입은 다음과 같습니다.

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a>USB 디바이스 컨트롤러 정의

언제든지 USB 디바이스 컨트롤러 하나만 디바이스 모드로 작동하도록 정의할 수 있습니다. 애플리케이션 초기화 파일에 이 정의가 포함됩니다. 다음 줄은 일반 USB 컨트롤러에 대한 정의를 수행합니다.

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

USB 디바이스 초기화에는 다음 프로토타입이 포함됩니다.

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

다음 매개 변수 사용:

| 매개 변수               | Description                      |
| ------------------------ | -------------------------------- |
| ULONG dcd_io            | 컨트롤러 IO의 주소     |
| ULONG dcd_irq           | 컨트롤러에서 사용하는 인터럽트 |
| ULONG dcd_vbus_address | VBUS GPIO의 주소         |

다음 예제는 스토리지 디바이스 클래스 및 일반 컨트롤러를 사용하여 디바이스 모드에서 USBX를 초기화하는 것입니다.

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a>문제 해결

USBX는 데모 파일 및 시뮬레이션 환경으로 제공됩니다. 항상 대상 하드웨어 또는 특정 데모 플랫폼에서 데모 플랫폼을 먼저 실행하는 것이 좋습니다.

## <a name="usbx-version-id"></a>USBX 버전 ID

USBX의 현재 버전은 런타임 중 사용자 및 애플리케이션 모두에 제공됩니다. 프로그래머는 ***ux_port.h** _ 파일을 조사하여 USBX 버전을 가져올 수 있습니다. 또한 이 파일에는 해당 포트의 버전 기록도 포함됩니다. 애플리케이션 소프트웨어는 _*_ux_port.h_**에 정의된 전체 문자열 _ *_ _ux_version_id_* _를 조사하여 USBX 버전을 가져올 수 있습니다.
