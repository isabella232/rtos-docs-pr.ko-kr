---
title: 5장 - USBX 디바이스 클래스 고려 사항
description: USBX 디바이스 클래스 고려 사항에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 84f215ad990a2fe185a08f3876276528787ef8bc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811358"
---
# <a name="chapter-5---usbx-device-class-considerations"></a>5장 - USBX 디바이스 클래스 고려 사항

## <a name="device-class-registration"></a>디바이스 클래스 등록

각 디바이스 클래스는 동일한 등록 원칙을 따릅니다. 특정 클래스 매개 변수를 포함하는 구조체는 클래스 initialize 함수에 전달됩니다.

```c
/* Set the parameters for callback when insertion/extraction of a HID device. */

hid_parameter.ux_slave_class_hid_instance_activate = tx_demo_hid_instance_activate;

hid_parameter.ux_slave_class_hid_instance_deactivate = tx_demo_hid_instance_deactivate;

/* Initialize the hid class parameters for the device. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_device_report;

hid_parameter.ux_device_class_hid_parameter_report_length = HID_DEVICE_REPORT_LENGTH;

hid_parameter.ux_device_class_hid_parameter_report_id = UX_TRUE;
hid_parameter.ux_device_class_hid_parameter_callback = demo_thread_hid_callback;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry,1,0, (VOID *)&hid_parameter);
```

각 클래스는 클래스 인스턴스가 활성화될 때 필요에 따라 콜백 함수를 등록할 수 있습니다. 그런 다음 인스턴스가 생성되었음을 애플리케이션에 알리기 위해 디바이스 스택에서 콜백을 호출합니다.

애플리케이션 본문에는 다음 예제와 같이 활성화 및 비활성화를 위한 함수 2개가 포함됩니다.

```c
VOID tx_demo_hid_instance_activate(VOID *hid_instance)
{
    /* Save the HID instance. */
    hid_slave = (UX_SLAVE_CLASS_HID *) hid_instance;
}

VOID tx_demo_hid_instance_deactivate(VOID *hid_instance)
{
    /* Reset the HID instance. */
    hid_slave = UX_NULL;
}
```

두 함수 내에서는 클래스 인스턴스를 기억하고 애플리케이션의 나머지 부분과 동기화하는 작업을 제외한 어떤 작업도 수행하지 않는 것이 좋습니다.

## <a name="usb-device-storage-class"></a>USB 디바이스 스토리지 클래스

USB 디바이스 스토리지 클래스를 사용하면 시스템에 포함된 스토리지 디바이스를 USB 호스트에 표시할 수 있습니다.

USB 디바이스 스토리지 클래스가 단독으로 스토리지 솔루션을 제공하지는 않습니다. 단지 호스트에서 들어오는 SCSI 요청을 수락하고 해석합니다. 요청 중 하나가 읽기 또는 쓰기 명령이면 USB 디바이스 스토리지 클래스는 ATA 디바이스 드라이버 또는 플래시 디바이스 드라이버와 같은 실제 스토리지 디바이스 처리기에 대해 미리 정의된 콜백을 호출합니다.

디바이스 스토리지 클래스를 초기화하면 필요한 모든 정보를 포함하는 포인터 구조체가 클래스에 제공됩니다. 예를 들면 다음과 같습니다.

```c
/* Initialize the storage class parameters to customize vendor strings. */

storage_parameter.ux_slave_class_storage_parameter_vendor_id
    = demo_ux_system_slave_class_storage_vendor_id;

storage_parameter.ux_slave_class_storage_parameter_product_id
    = demo_ux_system_slave_class_storage_product_id;

storage_parameter.ux_slave_class_storage_parameter_product_rev
    = demo_ux_system_slave_class_storage_product_rev;

storage_parameter.ux_slave_class_storage_parameter_product_serial
    = demo_ux_system_slave_class_storage_product_serial;

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read_only_flag
    = UX_FALSE;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read
    = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write
    = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status
    = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,
    ux_device_class_storage_entry, ux_device_class_storage_thread, 0, (VOID *)&storage_parameter);
```

이 예제에서는 해당 매개 변수에 문자열 포인터를 할당하여 드라이버 스토리지 문자열을 사용자 지정합니다. 문자열 포인터 중 하나를 UX_NULL로 유지하면 기본 Azure RTOS 문자열이 사용됩니다.

이 예제에서는 드라이브의 마지막 블록 주소, 즉 LBA도 논리 섹터 크기와 함께 제공됩니다. LBA는 미디어에서 사용할 수 있는 섹터 수-1입니다. 일반 스토리지 미디어의 블록 길이는 512로 설정됩니다. 광학 드라이브의 경우 2048로 설정할 수 있습니다.

애플리케이션은 스토리지 클래스가 미디어를 읽고, 쓰고, 상태를 가져올 수 있도록 세 가지 콜백 함수 포인터를 전달해야 합니다.

읽기 및 쓰기 함수의 프로토타입은 아래 예제에 나와 있습니다.

```c
UINT media_read( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);

UINT media_write( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);
```

위치:

- *storage* 는 스토리지 클래스 인스턴스입니다.
- *lun* 은 명령이 전달되는 LUN입니다.
- *data_pointer* 는 읽기 또는 쓰기에 사용할 버퍼의 주소입니다.
- *number_blocks* 는 읽기/쓰기를 수행할 섹터 수입니다.
- *lba* 는 읽을 섹터 주소입니다.
- *media_status* 는 미디어 상태 콜백 반환 값과 똑같이 채워야 합니다.

반환 값은 성공 또는 실패한 작업을 나타내는 UX_SUCCESS 또는 UX_ERROR 값을 포함할 수 있습니다. 다른 오류 코드는 작업에서 반환할 필요가 없습니다. 작업에 오류가 있으면 스토리지 클래스에서 상태 콜백 함수를 호출합니다.

이 함수의 프로토타입은 다음과 같습니다.

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

호출 매개 변수 media_id는 현재 사용되지 않으며 항상 0이어야 합니다. 향후 여러 스토리지 디바이스나 여러 SCSI LUN이 있는 스토리지 디바이스를 구분하는 데 사용될 수 있습니다. 이 버전의 스토리지 클래스는 여러 스토리지 클래스 인스턴스나 여러 SCSI LUN이 있는 스토리지 디바이스를 지원하지 않습니다.

반환 값은 다음과 같은 형식의 SCSI 오류 코드입니다.

- **비트 0~7** Sense_key
- **비트 8~15** 추가 Sense 코드
- **비트 16~23** 추가 Sense 코드 한정자

다음 표에서는 가능한 Sense/ASC/ASCQ 조합을 제공합니다.

| Sense 키 | ASC | ASCQ | Description                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| 00        | 00  | 00   | SENSE 없음                                          |
| 01        | 17  | 01   | 다시 시도를 사용하여 데이터 복구됨                       |
| 01        | 18  | 00   | ECC를 사용하여 데이터 복구됨                           |
| 02        | 04  | 01   | 논리 드라이브가 준비되지 않음 - 준비 중          |
| 02        | 04  | 02   | 논리 드라이브가 준비되지 않음 - 초기화 필요 |
| 02        | 04  | 04   | 논리적 단위가 준비되지 않음 - 포맷 진행 중       |
| 02        | 04  | FF   | 논리 드라이브가 준비되지 않음 - 디바이스 사용 중          |
| 02        | 06  | 00   | 참조 위치를 찾을 수 없음                       |
| 02        | 08  | 00   | 논리적 단위 통신 오류                |
| 02        | 08  | 01   | 논리적 단위 통신 시간 초과               |
| 02        | 08  | 80   | 논리적 단위 통신 오버런                |
| 02        | 3A  | 00   | 매체 없음                                |
| 02        | 54  | 00   | USB-호스트 시스템 인터페이스 오류              |
| 02        | 80  | 00   | 리소스 부족                            |
| 02        | FF  | FF   | 알 수 없는 오류                                     |
| 03        | 02  | 00   | 검색 미완료                                  |
| 03        | 03  | 00   | 쓰기 오류                                       |
| 03        | 10  | 00   | ID CRC 오류                                      |
| 03        | 11  | 00   | 복구되지 않은 읽기 오류                            |
| 03        | 12  | 00   | ID 필드의 주소 표시를 찾을 수 없음               |
| 03        | 13  | 00   | 데이터 필드의 주소 표시를 찾을 수 없음             |
| 03        | 14  | 00   | 기록된 엔터티를 찾을 수 없음                         |
| 03        | 30  | 01   | 매체를 읽을 수 없음 - 알 수 없는 포맷               |
| 03        | 31  | 01   | FORMAT 명령 오류                             |
| 04        | 40  | NN   | 구성 요소 NN 진단 오류(80H-FFH)      |
| 05        | 1A  | 00   | 매개 변수 목록 길이 오류                       |
| 05        | 20  | 00   | 잘못된 명령 작업 코드                    |
| 05        | 21  | 00   | 논리적 블록 주소가 범위를 벗어남                |
| 05        | 24  | 00   | 명령 패킷에 잘못된 필드 있음                   |
| 05        | 25  | 00   | 논리적 단위가 지원되지 않음                        |
| 05        | 26  | 00   | 매개 변수 목록에 잘못된 필드 있음                   |
| 05        | 26  | 01   | 매개 변수가 지원되지 않음                           |
| 05        | 26  | 02   | 매개 변수 값이 잘못됨                           |
| 05        | 39  | 00   | 매개 변수를 저장할 수 없음                     |
| 06        | 28  | 00   | 준비 안 됨에서 준비됨으로 전환 – 미디어 변경됨     |
| 06        | 29  | 00   | 전원 켜기 초기화 또는 버스 디바이스 초기화 발생       |
| 06        | 2F  | 00   | 다른 개시 장치가 명령을 지움             |
| 07        | 27  | 00   | 보호된 미디어에 쓰기                             |
| 0B        | 4E  | 00   | 겹친 명령을 시도함                      |

애플리케이션에서 추가로 구현할 수 있는 두 가지 선택적 콜백은 **GET_STATUS_NOTIFICATION** 명령에 응답하기 위한 콜백과 **SYNCHRONIZE_CACHE** 명령에 응답하기 위한 콜백입니다.

호스트의 GET_STATUS_NOTIFICATION 명령을 처리하려는 애플리케이션은 다음 프로토타입으로 콜백을 구현해야 합니다.

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

위치:

- *storage* 는 스토리지 클래스 인스턴스입니다.
- *media_id* 는 현재 사용되지 않습니다. notification_class는 알림 클래스를 지정합니다.
- *media_notification* 은 애플리케이션에서 알림에 대한 응답을 포함하는 버퍼로 설정해야 합니다.
- *media_notification_length* 는 애플리케이션에서 응답 버퍼의 길이를 포함하도록 설정해야 합니다.

반환 값은 명령이 성공했는지 여부를 나타내며 **UX_SUCCESS** 또는 **UX_ERROR** 중 하나여야 합니다.

애플리케이션에서 이 콜백을 구현하지 않으면 **GET_STATUS_NOTIFICATION** 명령이 수신될 때 USBX에서 명령이 구현되지 않았다고 호스트에 알립니다.

애플리케이션에서 호스트의 쓰기에 캐시를 활용하는 경우 **SYNCHRONIZE_CACHE** 명령을 처리해야 합니다. 이 명령은 스토리지 디바이스의 연결이 끊길 것을 알고 있는 호스트에서 보낼 수 있습니다. 예를 들어 Windows에서 도구 모음에 있는 플래시 드라이브 아이콘을 마우스 오른쪽 단추로 클릭하고 “\[스토리지 디바이스 이름\] 꺼내기”를 선택하면 Windows는 해당 디바이스에 **SYNCHRONIZE_CACHE** 명령을 실행합니다.

호스트의 **GET_STATUS_NOTIFICATION** 명령을 처리하려는 애플리케이션은 다음 프로토타입으로 콜백을 구현해야 합니다.

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

위치:

- *storage* 는 스토리지 클래스 인스턴스입니다.
- *lun* 매개 변수는 명령이 전달되는 LUN을 지정합니다.
- *number_blocks* 는 동기화할 블록 수를 지정합니다.
- *lba* 는 동기화할 첫 번째 블록의 섹터 주소입니다.
- *media_status* 는 미디어 상태 콜백 반환 값과 똑같이 채워야 합니다.

반환 값은 명령이 성공했는지 여부를 나타내며 **UX_SUCCESS** 또는 **UX_ERROR** 중 하나여야 합니다.

### <a name="multiple-scsi-lun"></a>여러 SCSI LUN

USBX 디바이스 스토리지 클래스는 여러 LUN을 지원합니다. 따라서 동시에 CD-ROM 및 플래시 디스크 역할을 하는 스토리지 디바이스를 만들 수 있습니다. 이 경우 초기화가 약간 다릅니다. 플래시 디스크 및 CD-ROM의 예제는 다음과 같습니다.

```c
/* Store the number of LUN in this device storage instance. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 2;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x7bbff;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the storage class LUN parameters for reading/writing to the CD-ROM. */

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_last_lba = 0x04caaf;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_block_length = 2048;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_type = 5;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_read = tx_demo_thread_cdrom_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_write = tx_demo_thread_cdrom_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_status = tx_demo_thread_cdrom_media_status;

/* Initialize the device storage class for a Flash disk and CD-ROM. The class is connected with interface 0 */ status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *) &storage_parameter);
```

## <a name="usb-device-cdc-acm-class"></a>USB 디바이스 CDC-ACM 클래스

USB 디바이스 CDC-ACM 클래스를 사용하면 USB 호스트 시스템이 직렬 디바이스로 디바이스와 통신할 수 있습니다. 이 클래스는 USB 표준을 기반으로 하며 CDC 표준의 하위 집합입니다.

디바이스 스택에서 CDC ACM 규격 디바이스 프레임워크를 선언해야 합니다. 아래에서 예제를 확인할 수 있습니다.

```c
unsigned char device_framework_full_speed[] = {

    /*
    Device descriptor 18 bytes
    0x02 bDeviceClass: CDC class code
    0x00 bDeviceSubclass: CDC class sub code 0x00 bDeviceProtocol: CDC Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    0x12, 0x01, 0x10, 0x01,
    0xEF, 0x02, 0x01, 0x08,
    0x84, 0x84, 0x00, 0x00,
    0x00, 0x01, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration 1 descriptor 9 bytes */
    0x09, 0x02, 0x4b, 0x00, 0x02, 0x01, 0x00,0x40, 0x00,

    /* Interface association descriptor. 8 bytes. */
    0x08, 0x0b, 0x00,
    0x02, 0x02, 0x02, 0x00, 0x00,

    /* Communication Class Interface Descriptor Requirement. 9 bytes. */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x02, 0x01, 0x00,

    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00,0x10, 0x01,

    /* ACM Functional Descriptor 4 bytes */
    0x04, 0x24, 0x02,0x0f,

    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,

    /* Master interface */
    0x01, /* Slave interface */

    /* Call Management Functional Descriptor 5 bytes */
    0x05, 0x24, 0x01,0x03, 0x01, /* Data interface */

    /* Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x83, 0x03,0x08, 0x00, 0xFF,

    /* Data Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x02,0x0A, 0x00, 0x00, 0x00,

    /* First alternate setting Endpoint 1 descriptor 7 bytes*/
    0x07, 0x05, 0x02,0x02,0x40, 0x00,0x00,

    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81,0x02,0x40, 0x00, 0x00,

};
```

CDC-ACM 클래스는 복합 디바이스 프레임워크를 사용하여 인터페이스(제어 및 데이터)를 그룹화합니다. 따라서 디바이스 설명자를 정의할 때는 주의해야 합니다. USBX는 IAD 설명자를 사용하여 내부적으로 인터페이스 바인딩 방법을 확인합니다. IAD 설명자는 인터페이스 앞에 선언되어야 하며, CDC-ACM 클래스의 첫 번째 인터페이스 및 연결된 인터페이스 수를 포함해야 합니다.

CDC-ACM 클래스는 최신 IAD 설명자와 동일한 기능을 수행하는 통합 기능 설명자도 사용합니다. 통합 기능 설명자는 기록 및 호스트 쪽과의 호환성을 위해 선언되어야 하지만 USBX에서 사용되지는 않습니다.

CDC-ACM 클래스의 초기화에는 다음 매개 변수가 필요합니다.

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

정의된 매개 변수 2개는 스택에서 이 클래스를 활성화하거나 비활성화할 때 호출되는 사용자 애플리케이션에 대한 콜백 포인터입니다.

정의된 세 번째 매개 변수는 회선 코딩 또는 회선 상태 매개 변수 변경이 있을 때 호출되는 사용자 애플리케이션에 대한 콜백 포인터입니다. 예를 들어 DTR 상태를 **TRUE** 로 변경하라는 호스트의 요청이 있을 경우 콜백이 호출되고, 콜백에서 사용자 애플리케이션은 IOCTL 함수를 통해 회선 상태를 검사하여 호스트가 통신할 준비가 되었음을 확인할 수 있습니다.

CDC-ACM은 USB-IF 표준을 기반으로 하며 macOS 및 Linux 운영 체제에서 자동으로 인식됩니다. Windows 10 이전 버전의 Windows 플랫폼에서 이 클래스를 사용하려면 .inf 파일이 필요합니다. Windows 10에서는 .inf 파일이 필요하지 않습니다. CDC-ACM 클래스용 템플릿이 제공되며 ***usbx_windows_host_files*** 디렉터리에서 사용할 수 있습니다. 최신 버전의 Windows에서는 CDC_ACM_Template_Win7_64bit.inf 파일을 사용해야 합니다(Win10 제외). 디바이스에서 사용하는 PID/VID에 맞게 파일을 수정해야 합니다. 회사와 제품이 USB-IF를 사용하여 등록된 경우 PID/VID는 최종 고객에 따라 다릅니다. Inf 파일에서 수정할 필드는 아래에 나와 있습니다.

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

CDC-ACM 디바이스의 디바이스 프레임워크에서 PID/VID는 디바이스 설명자에 저장됩니다(위에서 선언한 디바이스 설명자 참조).

USB CDC-ACM 디바이스가 검색되면 USB 호스트 시스템에서 직렬 클래스를 탑재하며, 모든 직렬 터미널 프로그램으로 디바이스를 사용할 수 있습니다. 호스트 운영 체제를 참조하세요.

CDC-ACM 클래스 API 함수는 아래에 정의되어 있습니다.

### <a name="ux_device_class_cdc_acm_ioctl"></a>ux_device_class_cdc_acm_ioctl

CDC-ACM 인터페이스에서 IOCTL 수행

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 CDC ACM 인터페이스에 대해 다양한 IOCTL 호출을 수행해야 하는 경우에 호출됩니다.

### <a name="parameters"></a>매개 변수

- **cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.
- **ioctl_function**: 수행할 IOCTL 함수
- **parameter**: IOCTL 호출과 관련된 매개 변수에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.
- **UX_ERROR**(0xff) 함수에서 오류가 발생했습니다.

### <a name="example"></a>예제

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a>IOCTL 함수:

| 기능                                        | 값 |
| ----------------------------------------------- | - |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING    | 1 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING    | 2 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE     | 3 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE         | 4 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE     | 5 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START | 6 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP  | 7 |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING

CDC-ACM 인터페이스에서 IOCTL 회선 코딩 설정 수행

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 회선 코딩 매개 변수를 설정해야 하는 경우에 호출됩니다.

### <a name="parameters"></a>매개 변수

- **cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING
- **parameter**: 회선 매개 변수 구조체에 대한 포인터:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>반환 값

**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.

### <a name="example"></a>예제

```c
/* Change the line coding values. */

line_coding.ux_slave_class_cdc_acm_line_coding_dter = 9600;
line_coding.ux_slave_class_cdc_acm_line_coding_stop_bit =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_STOP_BIT_15;

line_coding.ux_slave_class_cdc_acm_line_coding_parity =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_PARITY_EVEN;

line_coding.ux_slave_class_cdc_acm_line_coding_data_bits = 5;

status = _ux_slave_class_cdc_acm_ioctl(cdc_acm,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING, &line_coding);

if (status != UX_SUCCESS)
    break;
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING

CDC-ACM 인터페이스에서 IOCTL 회선 코딩 가져오기 수행

### <a name="prototype"></a>프로토타입

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 회선 코딩 매개 변수를 가져와야 하는 경우에 호출됩니다.

### <a name="parameters"></a>매개 변수

- **cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING
- **parameter**: 회선 매개 변수 구조체에 대한 포인터:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.

### <a name="example"></a>예제

```c
/* This is to retrieve BAUD rate. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, &line_coding);

/* Any error ? */
if (status == UX_SUCCESS)
{
    /* Decode BAUD rate. */
    switch (line_coding.ux_slave_class_cdc_acm_parameter_baudrate)
    {
        case 1200 :
            status = tx_demo_thread_slave_cdc_acm_response("1200", 4);
            break;
        case 2400 :
            status = tx_demo_thread_slave_cdc_acm_response("2400", 4);
            break;
        case 4800 :
            status = tx_demo_thread_slave_cdc_acm_response("4800", 4);
            break;
        case 9600 :
            status = tx_demo_thread_slave_cdc_acm_response("9600", 4);
            break;
        case 115200 :
            status = tx_demo_thread_slave_cdc_acm_response("115200", 6);
            break;
    }
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE

CDC-ACM 인터페이스에서 IOCTL 회선 상태 가져오기 수행

## <a name="prototype"></a>프로토타입

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 회선 상태 매개 변수를 가져와야 하는 경우에 호출됩니다.

### <a name="parameters"></a>매개 변수

- **cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE
- **parameter**: 회선 매개 변수 구조체에 대한 포인터:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.

### <a name="example"></a>예제

```c
/* This is to retrieve RTS state. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE, &line_state);

/* Any error ? */
if (status == UX_SUCCESS)
{
/* Check state. */
    if (line_state.ux_slave_class_cdc_acm_parameter_rts == UX_TRUE)
        /* State is ON. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS ON", 6);
    else
        /* State is OFF. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS OFF", 7);
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE

CDC-ACM 인터페이스에서 IOCTL 회선 상태 설정 수행

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 회선 상태 매개 변수를 설정해야 하는 경우에 호출됩니다.

### <a name="parameters"></a>매개 변수

- **cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE
- **parameter**: 회선 매개 변수 구조체에 대한 포인터:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.

### <a name="example"></a>예제

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE

CDC-ACM 인터페이스에서 IOCTL 파이프 중단 수행

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 파이프를 중단해야 하는 경우에 호출됩니다. 예를 들어 진행 중인 쓰기를 중단하려면 UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT를 매개 변수로 전달해야 합니다.

### <a name="parameters"></a>매개 변수

- **cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE
- **parameter**: 파이프 방향:

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.
- **UX_ENDPOINT_HANDLE_UNKNOWN**(0x53) 파이프 방향이 잘못되었습니다.

### <a name="example"></a>예제

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START

CDC-ACM 인터페이스에서 IOCTL 전송 시작 수행

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 콜백으로 전송을 사용하려는 경우에 호출됩니다.

### <a name="parameters"></a>매개 변수

- **cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START
- **parameter**: 전송 시작 매개 변수 구조체에 대한 포인터:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.
- **UX_ERROR**(0xff) 전송이 이미 시작되었습니다.
- **UX_MEMORY_INSUFFICIENT**(0x12) 메모리를 할당하지 못했습니다.

### <a name="example"></a>예제

```c
/* Set the callback parameter. */

callback.ux_device_class_cdc_acm_parameter_write_callback
    = tx_demo_thread_slave_write_callback;

callback.ux_device_class_cdc_acm_parameter_read_callback
    = tx_demo_thread_slave_read_callback;

/* Program the start of transmission. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP

CDC-ACM 인터페이스에서 IOCTL 전송 중지 수행

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 콜백으로 전송 사용을 중지하려는 경우에 호출됩니다.

### <a name="parameters"></a>매개 변수

- **cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP
- **parameter**: 사용되지 않음

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.
- **UX_ERROR**(0xff) 진행 중인 전송이 없습니다.

### <a name="example"></a>예제

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a>ux_device_class_cdc_acm_read

CDC-ACM 파이프에서 읽기

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 OUT 데이터 파이프(호스트에서는 OUT, 디바이스에서는 IN)를 읽어야 하는 경우에 호출됩니다. 차단형 함수입니다.

### <a name="parameters"></a>매개 변수

- **cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.
- **buffer**: 데이터가 저장되는 버퍼 주소
- **requested_length**: 필요한 최대 길이
- **actual_length**: 버퍼로 반환되는 길이

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.
- **UX_CONFIGURATION_HANDLE_UNKNOWN**(0x51) 디바이스가 더 이상 구성된 상태가 아닙니다.
- **UX_TRANSFER_NO_ANSWER**(0x22) 디바이스에서 응답이 없습니다. 전송이 보류된 동안 디바이스 연결이 끊긴 것 같습니다.

### <a name="example"></a>예제

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a>ux_device_class_cdc_acm_write

CDC-ACM 파이프에 쓰기

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 IN 데이터 파이프(호스트에서는 IN, 디바이스에서는 OUT)에 써야 하는 경우에 호출됩니다. 차단형 함수입니다.

### <a name="parameters"></a>매개 변수

- **cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.
- **buffer**: 데이터가 저장된 버퍼 주소
- **requested_length**: 쓸 버퍼의 길이
- **actual_length**: 쓰기를 수행한 후 버퍼로 반환되는 길이

### <a name="return-value"></a>반환 값
- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.
- **UX_CONFIGURATION_HANDLE_UNKNOWN**(0x51) 디바이스가 더 이상 구성된 상태가 아닙니다.
- **UX_TRANSFER_NO_ANSWER**(0x22) 디바이스에서 응답이 없습니다. 전송이 보류된 동안 디바이스 연결이 끊긴 것 같습니다.

### <a name="example"></a>예제

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a>ux_device_class_cdc_acm_write_with_callback

콜백으로 CDC-ACM 파이프에 쓰기

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 IN 데이터 파이프(호스트에서는 IN, 디바이스에서는 OUT)에 써야 하는 경우에 호출됩니다. 비차단형 함수로, UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START에서 설정된 콜백을 통해 완료됩니다.

### <a name="parameters"></a>매개 변수

- **cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.
- **buffer**: 데이터가 저장된 버퍼 주소
- **requested_length**: 쓸 버퍼의 길이
- **actual_length**: 쓰기를 수행한 후 버퍼로 반환되는 길이

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.
- **UX_CONFIGURATION_HANDLE_UNKNOWN**(0x51) 디바이스가 더 이상 구성된 상태가 아닙니다.
- **UX_TRANSFER_NO_ANSWER**(0x22) 디바이스에서 응답이 없습니다. 전송이 보류된 동안 디바이스 연결이 끊긴 것 같습니다.

### <a name="example"></a>예제

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a>USB 디바이스 CDC-ECM 클래스

USB 디바이스 CDC-ECM 클래스를 사용하면 USB 호스트 시스템이 이더넷 디바이스로 디바이스와 통신할 수 있습니다. 이 클래스는 USB 표준을 기반으로 하며 CDC 표준의 하위 집합입니다.

디바이스 스택에서 CDC ACM 규격 디바이스 프레임워크를 선언해야 합니다. 아래에서 예제를 확인할 수 있습니다.

```c
unsigned char device_framework_full_speed[] = {

    /* Device descriptor 18 bytes
    0x02 bDeviceClass: CDC_ECM class code
    0x06 bDeviceSubclass: CDC_ECM class sub code
    0x00 bDeviceProtocol: CDC_ECM Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    0x3939 idVendor: Azure RTOS test.
    */
    
    0x12, 0x01, 0x10, 0x01,
    0x02, 0x00, 0x00, 0x08,
    0x39, 0x39, 0x08, 0x08, 0x00, 0x01, 0x01, 0x02, 03,0x01,
    
    /* Configuration 1 descriptor 9 bytes. */
    0x09, 0x02, 0x58, 0x00,0x02, 0x01, 0x00,0x40, 0x00,
    
    /* Interface association descriptor. 8 bytes. */
    
    0x08, 0x0b, 0x00, 0x02, 0x02, 0x06, 0x00, 0x00,
    
    /* Communication Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x06, 0x00, 0x00,
    
    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00, 0x10, 0x01,
    
    /* ECM Functional Descriptor 13 bytes */
    0x0D, 0x24, 0x0F, 0x04,0x00, 0x00, 0x00, 0x00, 0xEA, 0x05, 0x00,
    0x00,0x00,
    
    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,0x01,
    
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x08,
    
    /* Data Class Interface Descriptor Alternate Setting 0, 0 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x00, 0x0A, 0x00, 0x00, 0x00,
    
    /* Data Class Interface Descriptor Alternate Setting 1, 2 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x01, 0x02, 0x0A, 0x00, 0x00,0x00,
    
    /* First alternate setting Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x02, 0x02, 0x40, 0x00, 0x00,
    
    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81, 0x02, 0x40, 0x00,0x00

};
```

CDC-ECM 클래스는 CDC-ACM과 매우 유사한 디바이스 설명자 방법을 사용하며 IAD 설명자가 필요합니다. 정의는 CDC-ACM 클래스를 참조하세요.

CDC-ECM에는 기본 디바이스 프레임워크 외에도 특수 문자열 설명자가 필요합니다. 예를 들면 다음과 같습니다.

```c
unsigned char string_framework[] = {
    /* Manufacturer string descriptor: Index 1 - "Azure RTOS" */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,
    
    /* Product string descriptor: Index 2 - "EL CDCECM Device" */
    0x09, 0x04, 0x02, 0x10,
    0x45, 0x4c, 0x20, 0x43, 0x44, 0x43, 0x45, 0x43,
    0x4d, 0x20, 0x44, 0x65, 0x76, 0x69, 0x63, 0x64,
    
    /* Serial Number string descriptor: Index 3 - "0001" */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31,
    
    /* MAC Address string descriptor: Index 4 - "001E5841B879" */
    0x09, 0x04, 0x04, 0x0C,
    0x30, 0x30, 0x31, 0x45, 0x35, 0x38,
    0x34, 0x31, 0x42, 0x38, 0x37, 0x39

};
```

CDC-ECM 클래스는 MAC 주소 문자열 설명자를 사용하여 TCP/IP 프로토콜에서 디바이스가 응답하는 MAC 주소에 대한 호스트 쿼리에 응답합니다. 선택한 디바이스에 설명자를 설정할 수 있지만 여기서 정의해야 합니다.

CDC-ECM 클래스의 초기화는 다음과 같습니다.

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_activate = UX_NULL;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_deactivate = UX_NULL;

/* Define a NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[5] = 0x79;

/* Initialize the device cdc_ecm class. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_ecm_name,
    ux_device_class_cdc_ecm_entry, 1,0,&cdc_ecm_parameter);
```

이 클래스를 초기화하려면 활성화와 비활성화에 동일한 함수 콜백을 사용해야 합니다. 단, 예제에서는 연습 삼아 콜백이 수행되지 않도록 NULL로 설정했습니다.

다음 매개 변수는 노드 ID 정의의 매개 변수입니다. CDC-ECM에는 두 가지 노드인 로컬 노드와 원격 노드가 필요합니다. 로컬 노드는 디바이스의 MAC 주소를 지정하는 반면 원격 노드는 호스트의 MAC 주소를 지정합니다. 원격 노드는 디바이스 프레임워크 문자열 설명자에서 선언된 노드와 동일한 노드여야 합니다.

CDC-ECM 클래스에는 두 방법 모두로 데이터를 전송할 수 있는 기본 제공 API가 있지만 사용자 애플리케이션이 NetX를 통해 USB 이더넷 디바이스와 통신하기 때문에 해당 API는 애플리케이션에서 숨겨져 있습니다.

USBX CDC-ECM 클래스는 Azure RTOS NetX 네트워크 스택에 긴밀히 연결되어 있습니다. NetX 및 USBX CDC-ECM 클래스를 모두 사용하는 애플리케이션은 일반적인 방식으로 NetX 네트워크 스택을 활성화하지만 USB 네트워크 스택도 다음과 같이 활성화해야 합니다.

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

USB 네트워크 스택은 한 번만 활성화하면 되며 CDCECM에 국한되지 않고 NetX 서비스를 필요로 하는 모든 USB 클래스에 필요합니다.

CDC-ECM 클래스는 MAC OS 및 Linux 호스트에서 인식됩니다. 그러나 CDC-ECM을 기본적으로 인식할 수 있도록 Microsoft Windows에서 제공하는 드라이버는 없습니다. Windows 플랫폼용 상용 제품이 있으며 자체 .inf 파일을 제공합니다. CDC-ACM inf 템플릿과 동일한 방식으로 USB 네트워크 디바이스의 PID/VID와 일치하도록 파일을 수정해야 합니다.

## <a name="usb-device-hid-class"></a>USB 디바이스 HID 클래스

USB 디바이스 HID 클래스를 사용하면 USB 호스트 시스템에서 특정 HID 클라이언트 기능이 있는 HID 디바이스에 연결할 수 있습니다.

USBX HID 디바이스 클래스는 호스트 쪽에 비해 비교적 간단합니다. 디바이스 및 해당 HID 설명자의 동작에 긴밀히 연결되어 있습니다.

모든 HID 클라이언트에서 먼저 HID 디바이스 프레임워크를 아래 예제와 같이 정의해야 합니다.

```c
UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0x81, 0x0A, 0x01, 0x01, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x22, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x01, 0x03, 0x00, 0x00, 0x00,

    /* HID descriptor */
    0x09, 0x21, 0x10, 0x01, 0x21, 0x01, 0x22, 0x3f, 0x00,

    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x81, 0x03, 0x08, 0x00, 0x08

};
```

HID 프레임워크에는 HID 클래스 및 HID 디바이스 서브클래스를 설명하는 인터페이스 설명자가 포함되어 있습니다. HID 인터페이스는 독립 실행형 클래스이거나 복합 디바이스의 일부일 수 있습니다.

현재 대부분의 애플리케이션에서 하나의 ID(ID 0)만 필요하므로 USBX HID 클래스는 여러 보고서 ID를 지원하지 않습니다. 관심 있는 기능이 여러 보고서 ID인 경우 Microsoft에 문의하시기 바랍니다.

일례로 USB 키보드를 사용한 HID 클래스의 초기화는 다음과 같습니다.

```c
/* Initialize the hid class parameters for a keyboard. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_keyboard_report;
hid_parameter.ux_device_class_hid_parameter_report_length = HID_KEYBOARD_REPORT_LENGTH;
hid_parameter.ux_device_class_hid_parameter_callback = tx_demo_thread_hid_callback;
hid_parameter.ux_device_class_hid_parameter_report_id = 0;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry, 1,0,(VOID *)&hid_parameter);
if (status!=UX_SUCCESS)
    return;
```

애플리케이션에서 HID 보고서 설명자와 해당 길이를 HID 클래스에 전달해야 합니다. 보고서 설명자는 디바이스를 설명하는 항목의 컬렉션입니다. HID 문법에 대한 자세한 내용은 HID USB 클래스 사양을 참조하세요.

보고서 설명자 외에도 애플리케이션은 HID 이벤트가 발생할 경우 콜백을 전달합니다.

USBX HID 클래스는 다음과 같은 호스트의 표준 HID 명령을 지원합니다.

| 명령 이름                             | 값 | Description                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT   | 0x01  | 디바이스에서 보고서를 가져옵니다.                     |
| UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE     | 0x02  | 인터럽트 엔드포인트의 유휴 주파수를 가져옵니다. |
| UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL | 0x03  | 디바이스에서 실행 중인 프로토콜을 가져옵니다.           |
| UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT   | 0x09  | 디바이스에 보고서를 설정합니다.                       |
| UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE     | 0x0a  | 인터럽트 엔드포인트의 유휴 주파수를 설정합니다. |
| UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL | 0x0b  | 디바이스에서 실행 중인 프로토콜을 가져옵니다.           |

보고서 가져오기 및 설정은 HID에서 호스트와 디바이스 간 데이터 전송을 위해 가장 일반적으로 사용되는 명령입니다. 대체로 호스트는 제어 엔드포인트에서 데이터를 보내지만 인터럽트 엔드포인트에서 데이터를 받거나 제어 엔드포인트의 데이터를 가져오도록 GET_REPORT 명령을 실행하여 데이터를 받을 수 있습니다.

HID 클래스는 ux_device_class_hid_event_set 함수를 사용하여 데이터를 다시 인터럽트 엔드포인트의 호스트에 보낼 수 있습니다.

### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

HID 클래스에 이벤트 설정

### <a name="prototype"></a>프로토타입

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Description

이 함수는 애플리케이션에서 HID 이벤트를 다시 호스트에 보내야 하는 경우에 호출됩니다. 비차단형 함수로, 단지 보고서를 순환 큐에 넣고 애플리케이션에 반환합니다.

### <a name="parameters"></a>매개 변수

- **hid**: HID 클래스 인스턴스에 대한 포인터입니다.
- **hid_event**: HID 이벤트 구조체에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.
- **UX_ERROR**(0xff) 오류가 발생했습니다. 순환 큐에 사용할 수 있는 공간이 없습니다.

### <a name="example"></a>예제

```c
/* Insert a key into the keyboard event. Length is fixed to 8. */
hid_event.ux_device_class_hid_event_length = 8;

/* First byte is a modifier byte. */
hid_event.ux_device_class_hid_event_buffer[0] = 0;

/* Second byte is reserved. */
hid_event.ux_device_class_hid_event_buffer[1] = 0;

/* The 6 next bytes are keys. We only have one key here. */
hid_event.ux_device_class_hid_event_buffer[2] = key;

/* Set the keyboard event. */
ux_device_class_hid_event_set(hid, &hid_event);
```

HID 클래스를 초기화할 때 정의된 콜백은 이벤트 전송과 반대로 수행합니다. 호스트에서 보낸 이벤트를 입력으로 가져옵니다. 콜백의 프로토타입은 다음과 같습니다.

### <a name="hid_callback"></a>hid_callback

HID 클래스에서 이벤트 가져오기

### <a name="prototype"></a>프로토타입

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Description

이 함수는 호스트에서 HID 보고서를 애플리케이션에 보낼 때 호출됩니다.

### <a name="parameters"></a>매개 변수

- **hid**: HID 클래스 인스턴스에 대한 포인터입니다.
- **hid_event**: HID 이벤트 구조체에 대한 포인터입니다.

### <a name="example"></a>예제

다음 예제에서는 HID 키보드의 이벤트를 해석하는 방법을 보여 줍니다.

```c
UINT tx_demo_thread_hid_callback(UX_SLAVE_CLASS_HID *hid, UX_SLAVE_CLASS_HID_EVENT *hid_event
{
/* There was an event. Analyze it. Is it NUM LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_NUM_LOCK_MASK)
    /* Set the Num lock flag. */
    num_lock_flag = UX_TRUE;
else
    /* Reset the Num lock flag. */
    num_lock_flag = UX_FALSE;

/* There was an event. Analyze it. Is it CAPS LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_CAPS_LOCK_MASK)
    /* Set the Caps lock flag. */
    caps_lock_flag = UX_TRUE;
else
    /* Reset the Caps lock flag. */
    caps_lock_flag = UX_FALSE;
}
```
