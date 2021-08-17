---
title: USBX Pictbridge 구현
description: UBSX는 호스트와 디바이스 모두에서 전체 Pictbridge 구현을 지원합니다. Pictbridge는 두 측면에서 모두 USBX PIMA 클래스 위에 있습니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9f4ba97741d2fc5f93afe6866b9ae6e9dc1e98a977eb3d6050c4a7489804c93c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790714"
---
# <a name="chapter-4-usbx-pictbridge-implementation"></a>4장: USBX Pictbridge 구현

UBSX는 호스트와 디바이스 모두에서 전체 Pictbridge 구현을 지원합니다. Pictbridge는 두 측면에서 모두 USBX PIMA 클래스 위에 있습니다. 

PictBridge 표준을 사용하면 디지털 스틸 카메라 또는 스마트폰을 PC 없이 프린터에 직접 연결하여 특정 Pictbridge 인식 프린터에 직접 인쇄할 수 있습니다.

카메라 또는 휴대폰이 프린터에 연결된 경우 프린터는 USB 호스트이고 카메라는 USB 디바이스입니다. 그러나 Pictbridge를 사용하면 카메라가 호스트로 표시되고 명령은 카메라에서 구동됩니다. 카메라는 스토리지 서버이며, 프린터는 스토리지 클라이언트입니다. 카메라는 인쇄 클라이언트이며 프린터는 당연히 인쇄 서버입니다.

Pictbridge는 USB를 전송 계층으로 사용하지만 통신 프로토콜에 대한 PTP(사진 전송 프로토콜)를 사용합니다.

다음은 인쇄 작업이 발생했을 때 DPS 클라이언트와 DPS 서버 간 명령/응답의 다이어그램입니다.

![인쇄 작업이 발생했을 때 DPS 클라이언트와 DPS 서버 간 명령/응답의 다이어그램입니다.](./media/usbx-host-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a>Pictbridge 클라이언트 구현

클라이언트에서 Pictbridge를 사용하려면 USBX 디바이스 스택과 PIMA 클래스를 먼저 실행해야 합니다.

디바이스 프레임워크는 다음과 같은 방식으로 PIMA 클래스를 설명합니다.

```C
UCHAR device_framework_full_speed[] =
{
    /* Device descriptor */
       0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x20,
       0xA9, 0x04, 0xB6, 0x30, 0x00, 0x00, 0x00, 0x00,
       0x00, 0x01,
    /* Configuration descriptor */
       0x09, 0x02, 0x27, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,
    /* Interface descriptor */
       0x09, 0x04, 0x00, 0x00, 0x03, 0x06, 0x01, 0x01, 0x00,
    /* Endpoint descriptor (Bulk Out) */
       0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Bulk In) */
       0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Interrupt) */
       0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x60
};
```

Pima 클래스는 ID 필드 0x06을 사용하고 하위 클래스는 스틸 이미지에 대한 0x01이며 프로토콜은 PIMA 15740에 대한 0x01입니다.

이 클래스에는 3개의 엔드포인트가 정의되어 있습니다. 데이터를 보내고 받는 데 사용하는 벌크 2개와 이벤트에 대한 인터럽트 1개입니다.

다른 USBX 디바이스 구현과 달리, Pictbridge 애플리케이션은 클래스 자체를 정의할 필요가 없습니다. 대신 ***ux_pictbridge_dpsclient_start*** 함수를 호출합니다. 예를 들면 다음과 같습니다.

```C
/* Initialize the Pictbridge string components. */
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name,
    "Azure RTOS",10);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name,
    "EL_Pictbridge_Camera",21);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no, "ABC_123",7);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions,
    "1.0 1.1",7);

pictbridge.ux_pictbridge_dpslocal.
    ux_pictbridge_devinfo_vendor_specific_version = 0x0100;

/* Start the Pictbridge client. */
status = ux_pictbridge_dpsclient_start(&pictbridge);

if(status != UX_SUCCESS)
    return;
```

Pictbridge 클라이언트에 전달되는 매개 변수는 다음과 같습니다.

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no,
    : String of serial number pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version pictbridge.ux_pictbridge_dpslocal. ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

다음 단계는 디바이스와 호스트를 동기화하고 정보를 교환할 준비를 하는 것입니다.

이 작업은 다음과 같이 이벤트 플래그에서 대기하여 수행됩니다.

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get
    (&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR, &actual_flags,
    UX_PICTBRIDGE_EVENT_TIMEOUT);
```

상태 시스템이 **DISCOVERY_COMPLETE** 상태이면 카메라 쪽(DPS 클라이언트)은 프린터 및 해당 기능에 대한 정보를 수집합니다.

DPS 클라이언트에서 인쇄 작업을 수락할 준비가 되면 해당 상태가 **UX_PICTBRIDGE_NEW_JOB_TRUE** 로 설정됩니다. 아래에서 확인할 수 있습니다.

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)

    /* We can print something … */
```

다음 일부 인쇄 작업 설명자는 다음과 같이 채워야 합니다.

```C
/* We can start a new job. Fill in the JobConfig and PrintInfo structures. */
jobinfo = &pictbridge.ux_pictbridge_jobinfo;

/* Attach a printinfo structure to the job. */
jobinfo ->ux_pictbridge_jobinfo_printinfo_start = &printinfo;

/* Set the default values for print job. */
jobinfo ->ux_pictbridge_jobinfo_quality =
    UX_PICTBRIDGE_QUALITIES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_papersize =
    UX_PICTBRIDGE_PAPER_SIZES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_papertype =
    UX_PICTBRIDGE_PAPER_TYPES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_filetype =
    UX_PICTBRIDGE_FILE_TYPES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_dateprint =
    UX_PICTBRIDGE_DATE_PRINTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_filenameprint =
    UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_imageoptimize =
    UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF;
jobinfo ->ux_pictbridge_jobinfo_layout =
    UX_PICTBRIDGE_LAYOUTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_fixedsize =
    UX_PICTBRIDGE_FIXED_SIZE_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_cropping =
    UX_PICTBRIDGE_CROPPINGS_DEFAULT;

/* Program the callback function for reading the object data. */
jobinfo ->ux_pictbridge_jobinfo_object_data_read =
    ux_demo_object_data_copy;

/* This is a demo, the fileID is hardwired (1 and 2 for scripts, 3 for photo to be printed. */

printinfo.ux_pictbridge_printinfo_fileid =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;

ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_filename,
    "Pictbridge demo file", 20);
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_date, "01/01/2008",
    10);

/* Fill in the object info to be printed. First get the pointer to the object container in the job info structure. */
object = (UX_SLAVE_CLASS_PIMA_OBJECT *) jobinfo ->
    ux_pictbridge_jobinfo_object;

/* Store the object format: JPEG picture. */
object ->ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_EXIF_JPEG;
object ->ux_device_class_pima_object_compressed_size = IMAGE_LEN; object ->ux_device_class_pima_object_offset = 0;
object ->ux_device_class_pima_object_handle_id =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
object ->ux_device_class_pima_object_length = IMAGE_LEN;

/* File name is in Unicode. */
ux_utility_string_to_unicode("JPEG Image", object ->
    ux_device_class_pima_object_filename);

/* And start the job. */
status =ux_pictbridge_dpsclient_api_start_job(&pictbridge);
```

이제 Pictbridge 클라이언트는 인쇄 작업을 수행할 수 있으며, 필드에 정의된 콜백을 통해 애플리케이션에서 한 번에 이미지 블록을 페치합니다.

```C
jobinfo ->ux_pictbridge_jobinfo_object_data_read
```

해당 함수의 프로토타입은 다음과 같이 정의됩니다.

## <a name="ux_pictbridge_jobinfo_object_data_read"></a>ux_pictbridge_jobinfo_object_data_read

인쇄를 위해 사용자 공간에서 데이터 블록을 복사합니다.

### <a name="prototype"></a>프로토타입

```C
UINT **ux_pictbridge_jobinfo_object_data_read(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a>설명

이 함수는 DPS 클라이언트가 대상 Pictbridge 프린터에 인쇄하기 위해 데이터 블록을 검색해야 할 때 호출됩니다.

### <a name="parameters"></a>매개 변수

- **pictbridge**: Pictbridge 클래스 인스턴스에 대한 포인터
- **object_buffer**: 개체 버퍼에 대한 포인터
- **object_offset**: 데이터 블록 읽기를 시작하는 위치
- **object_length**: 반환될 길이
- **actual_length**: 반환되는 실제 길이

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.
- **UX_ERROR**(0x01) 애플리케이션에서 데이터를 검색할 수 없습니다.

### <a name="example"></a>예제

```C
/* Copy the object data. */

UINT ux_demo_object_data_copy(UX_PICTBRIDGE *pictbridge,UCHAR *object_buffer,
    ULONG object_offset, ULONG object_length, ULONG *actual_length)
{
    /* Copy the demanded object data portion. */
    ux_utility_memory_copy(object_buffer, image + object_offset,
        object_length);

    /* Update the actual length. */
    *actual_length = object_length;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="pictbridge-host-implementation"></a>Pictbridge 호스트 구현

Pictbridge의 호스트 구현은 클라이언트와 다릅니다.

Pictbridge 호스트 환경에서 가장 먼저 해야 할 일은 아래 예제와 같이 Pima 클래스를 등록하는 것입니다.

```C
status = ux_host_stack_class_register(ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

이 클래스는 USB 호스트 스택과 Pictbridge 계층 사이에 있는 일반 PTP 계층입니다.

다음 단계는 인쇄 서비스에 대한 Pictbridge 기본값을 다음과 같이 초기화하는 것입니다.

| Pictbridge 필드       | 값                                  |
|------------------------|----------------------------------------|
| DpsVersion[0]          | 0x00010000                             |
| DpsVersion[1]          | 0x00010001                             |
| DpsVersion[2]          | 0x00000000                             |
| VendorSpecificVersion  | 0x00010000                             |
| PrintServiceAvailable  | 0x30010000                             |
| Qualities[0]           | UX_PICTBRIDGE_QUALITIES_DEFAULT        |
| Qualities[1]           | UX_PICTBRIDGE_QUALITIES_NORMAL         |
| Qualities[2]           | UX_PICTBRIDGE_QUALITIES_DRAFT          |
| Qualities[3]           | UX_PICTBRIDGE_QUALITIES_FINE           |
| PaperSizes[0]          | UX_PICTBRIDGE_PAPER_SIZES_DEFAULT      |
| PaperSizes[1]          | UX_PICTBRIDGE_PAPER_SIZES_4IX6I        |
| PaperSizes[2]          | UX_PICTBRIDGE_PAPER_SIZES_L            |
| PaperSizes[3]          | UX_PICTBRIDGE_PAPER_SIZES_2L           |
| PaperSizes[4]          | UX_PICTBRIDGE_PAPER_SIZES_LETTER       |
| PaperTypes[0]          | UX_PICTBRIDGE_PAPER_TYPES_DEFAULT      |
| PaperTypes[1]          | UX_PICTBRIDGE_PAPER_TYPES_PLAIN        |
| PaperTypes[2]          | UX_PICTBRIDGE_PAPER_TYPES_PHOTO        |
| FileTypes[0]           | UX_PICTBRIDGE_FILE_TYPES_DEFAULT       |
| FileTypes[1]           | UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG     |
| FileTypes[2]           | UX_PICTBRIDGE_FILE_TYPES_JFIF          |
| FileTypes[3]           | UX_PICTBRIDGE_FILE_TYPES_DPOF          |
| DatePrints[0]          | UX_PICTBRIDGE_DATE_PRINTS_DEFAULT      |
| DatePrints[1]          | UX_PICTBRIDGE_DATE_PRINTS_OFF          |
| DatePrints[2]          | UX_PICTBRIDGE_DATE_PRINTS_ON           |
| FileNamePrints[0]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT |
| FileNamePrints[1]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF     |
| FileNamePrints[2]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_ON      |
| ImageOptimizes[0]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT  |
| ImageOptimizes[1]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF      |
| ImageOptimizes[2]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON       |
| Layouts[0]             | UX_PICTBRIDGE_LAYOUTS_DEFAULT          |
| Layouts[1]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER      |
| Layouts[2]             | UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT      |
| Layouts[3]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS  |
| FixedSizes[0]          | UX_PICTBRIDGE_FIXED_SIZE_DEFAULT       |
| FixedSizes[1]          | UX_PICTBRIDGE_FIXED_SIZE_35IX5I        |
| FixedSizes[2]          | UX_PICTBRIDGE_FIXED_SIZE_4IX6I         |
| FixedSizes[3]          | UX_PICTBRIDGE_FIXED_SIZE_5IX7I         |
| FixedSizes[4]          | UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM      |
| FixedSizes[5]          | UX_PICTBRIDGE_FIXED_SIZE_LETTER        |
| FixedSizes[6]          | UX_PICTBRIDGE_FIXED_SIZE_A4            |
| Croppings[0]           | UX_PICTBRIDGE_CROPPINGS_DEFAULT        |
| Croppings[1]           | UX_PICTBRIDGE_CROPPINGS_OFF            |
| Croppings[2]           | UX_PICTBRIDGE_CROPPINGS_ON             |

DPS 호스트의 상태 시스템은 유휴 상태로 설정되고 새 인쇄 작업을 수락할 준비가 됩니다.

이제 아래 예제에서 볼 수 있듯이 Pictbridge의 호스트 부분을 시작할 수 있습니다.

```C
/* Activate the pictbridge dpshost. */

status = ux_pictbridge_dpshost_start(&pictbridge, pima);
if (status != UX_SUCCESS)
    return;
```

데이터를 인쇄할 준비가 되면 Pictbridge 호스트 함수에서 콜백이 필요합니다. 이는 다음과 같이 Pictbridge 호스트 구조에 함수 포인터를 전달하여 수행됩니다.

```C
/* Set a callback when an object is being received. */

pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

이 함수에는 다음과 같은 속성이 있습니다.

## <a name="ux_pictbridge_application_object_data_write"></a>ux_pictbridge_application_object_data_write

인쇄용 데이터 블록 작성

### <a name="prototype"></a>프로토타입

```C
UINT **ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a>설명

이 함수는 DPS 서버에서 로컬 프린터로 인쇄하기 위해 DPS 클라이언트에서 데이터 블록을 검색해야 할 때 호출됩니다.

### <a name="parameters"></a>매개 변수

- **pictbridge**: Pictbridge 클래스 인스턴스에 대한 포인터
- **object_buffer**: 개체 버퍼에 대한 포인터
- **object_offset**: 데이터 블록 읽기를 시작하는 위치
- **total_length**: 개체의 전체 길이
- **length**: 이 버퍼의 길이

### <a name="return-value"></a>반환 값

- **UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.
- **UX_ERROR**(0x01) 애플리케이션에서 데이터를 인쇄할 수 없습니다.

### <a name="example"></a>예제

```C
/* Copy the object data. */

UINT tx_demo_object_data_write(UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer, ULONG offset, ULONG total_length, ULONG length);
{
    UINT status;

    /* Send the data to the local printer. */
    status = local_printer_data_send(object_buffer, length);

    /* We have printed the requested data. Return status. */
    return(status);
}
```
