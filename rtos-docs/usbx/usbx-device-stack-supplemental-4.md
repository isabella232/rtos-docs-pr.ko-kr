---
title: 4장 - USBX Pictbridge 구현
description: UBSX는 호스트와 디바이스 모두에서 전체 Pictbridge 구현을 지원합니다. Pictbridge는 두 측면에서 모두 USBX PIMA 클래스 위에 있습니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2ef1809dac046d49b15aba000cabed6c9fd458a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813369"
---
# <a name="chapter-4---usbx-pictbridge-implementation"></a><span data-ttu-id="d4936-104">4장 - USBX Pictbridge 구현</span><span class="sxs-lookup"><span data-stu-id="d4936-104">Chapter 4 - USBX Pictbridge implementation</span></span>

<span data-ttu-id="d4936-105">UBSX는 호스트와 디바이스 모두에서 전체 Pictbridge 구현을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-105">UBSX supports the full Pictbridge implementation both on the host and the device.</span></span> <span data-ttu-id="d4936-106">Pictbridge는 두 측면에서 모두 USBX PIMA 클래스 위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-106">Pictbridge sits on top of USBX PIMA class on both sides.</span></span>

<span data-ttu-id="d4936-107">PictBridge 표준을 사용하면 디지털 스틸 카메라 또는 스마트폰을 PC 없이 프린터에 직접 연결하여 특정 Pictbridge 인식 프린터에 직접 인쇄할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-107">The PictBridge standards allows the connection of a digital still camera or a smart phone directly to a printer without a PC, enabling direct printing to certain Pictbridge aware printers.</span></span>

<span data-ttu-id="d4936-108">카메라 또는 휴대폰이 프린터에 연결된 경우 프린터는 USB 호스트이고 카메라는 USB 디바이스입니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-108">When a camera or phone is connected to a printer, the printer is the USB host and the camera is the USB device.</span></span> <span data-ttu-id="d4936-109">그러나 Pictbridge를 사용하면 카메라가 호스트로 표시되고 명령은 카메라에서 구동됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-109">However, with Pictbridge, the camera will appear as being the host and commands are driven from the camera.</span></span> <span data-ttu-id="d4936-110">카메라는 스토리지 서버이며, 프린터는 스토리지 클라이언트입니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-110">The camera is the storage server, the printer the storage client.</span></span> <span data-ttu-id="d4936-111">카메라는 인쇄 클라이언트이며 프린터는 당연히 인쇄 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-111">The camera is the print client and the printer is of course the print server.</span></span>

<span data-ttu-id="d4936-112">Pictbridge는 USB를 전송 계층으로 사용하지만 통신 프로토콜에 대한 PTP(사진 전송 프로토콜)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-112">Pictbridge uses USB as a transport layer but relies on PTP (Picture Transfer Protocol) for the communication protocol.</span></span>

<span data-ttu-id="d4936-113">다음은 인쇄 작업이 발생했을 때 DPS 클라이언트와 DPS 서버 간 명령/응답의 다이어그램입니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-113">The following is a diagram of the commands/responses between the DPS client and the DPS server when a print job occurs:</span></span>

![DPS 명령 및 응답](./media/usbx-device-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a><span data-ttu-id="d4936-115">Pictbridge 클라이언트 구현</span><span class="sxs-lookup"><span data-stu-id="d4936-115">Pictbridge client implementation</span></span>

<span data-ttu-id="d4936-116">클라이언트에서 Pictbridge를 사용하려면 USBX 디바이스 스택과 PIMA 클래스를 먼저 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-116">The Pictbridge on the client requires the USBX device stack and the PIMA class to be running first.</span></span>

<span data-ttu-id="d4936-117">디바이스 프레임워크는 다음과 같은 방식으로 PIMA 클래스를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-117">A device framework describes the PIMA class in the following way.</span></span>

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

<span data-ttu-id="d4936-118">Pima 클래스는 ID 필드 0x06을 사용하고 하위 클래스는 스틸 이미지에 대한 0x01이며 프로토콜은 PIMA 15740에 대한 0x01입니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-118">The Pima class is using the ID field 0x06 and has its subclass is 0x01 for Still Image and the protocol is 0x01 for PIMA 15740.</span></span>

<span data-ttu-id="d4936-119">이 클래스에는 세 개의 엔드포인트가 정의되어 있습니다. 데이터를 보내고 받는 데 사용하는 벌크 두 개와 이벤트에 대한 인터럽트 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-119">Three endpoints are defined in this class; two bulks for sending/receiving data and one interrupt for events.</span></span>

<span data-ttu-id="d4936-120">다른 USBX 디바이스 구현과 달리, Pictbridge 애플리케이션은 클래스 자체를 정의할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-120">Unlike other USBX device implementations, the Pictbridge application does not need to define a class itself.</span></span> <span data-ttu-id="d4936-121">대신 ***ux_pictbridge_dpsclient_start*** 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-121">Rather it invokes the function ***ux_pictbridge_dpsclient_start***.</span></span> <span data-ttu-id="d4936-122">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-122">An example is below.</span></span>

```C
/* Initialize the Pictbridge string components. */
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name,
    "ExpressLogic",13);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name,
    "EL_Pictbridge_Camera",21);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no, "ABC_123",7);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions,
    "1.0 1.1",7);

pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_specific_version = 0x0100;

/* Start the Pictbridge client. */
status = ux_pictbridge_dpsclient_start(&pictbridge);

if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="d4936-123">Pictbridge 클라이언트에 전달되는 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-123">The parameters passed to the pictbridge client are as follows.</span></span>

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no
    : String of serial number
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

<span data-ttu-id="d4936-124">다음 단계는 디바이스와 호스트를 동기화하고 정보를 교환할 준비를 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-124">The next step is for the device and the host to synchronize and be ready to exchange information.</span></span>

<span data-ttu-id="d4936-125">이 작업은 다음과 같이 이벤트 플래그에서 대기하여 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-125">This is done by waiting on an event flag as follows.</span></span>

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get(&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR,
    &actual_flags, UX_PICTBRIDGE_EVENT_TIMEOUT);
```

<span data-ttu-id="d4936-126">상태 시스템이 **DISCOVERY_COMPLETE** 상태이면 카메라 쪽(DPS 클라이언트)은 프린터 및 해당 기능에 대한 정보를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-126">If the state machine is in the **DISCOVERY_COMPLETE** state, the camera side (the DPS client) will gather information regarding the printer and its capabilities.</span></span>

<span data-ttu-id="d4936-127">DPS 클라이언트에서 인쇄 작업을 허용할 준비가 되면 해당 상태가 **UX_PICTBRIDGE_NEW_JOB_TRUE** 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-127">If the DPS client is ready to accept a print job, its status will be set to **UX_PICTBRIDGE_NEW_JOB_TRUE**.</span></span> <span data-ttu-id="d4936-128">아래에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-128">It can be checked below.</span></span>

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)
/* We can print something … */
```

<span data-ttu-id="d4936-129">다음 일부 인쇄 작업 설명자는 다음과 같이 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-129">Next some print joib descriptors need to be filled as follows:</span></span>

```C
/* We can start a new job. Fill in the JobConfig and PrintInfo structures. */
jobinfo = &pictbridge.ux_pictbridge_jobinfo;

/* Attach a printinfo structure to the job. */
jobinfo -> ux_pictbridge_jobinfo_printinfo_start = &printinfo;

/* Set the default values for print job. */
jobinfo -> ux_pictbridge_jobinfo_quality =
    UX_PICTBRIDGE_QUALITIES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_papersize =
    UX_PICTBRIDGE_PAPER_SIZES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_papertype =
    UX_PICTBRIDGE_PAPER_TYPES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_filetype =
    UX_PICTBRIDGE_FILE_TYPES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_dateprint =
    UX_PICTBRIDGE_DATE_PRINTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_filenameprint =
    UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_imageoptimize =
    UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF;
jobinfo -> ux_pictbridge_jobinfo_layout =
    UX_PICTBRIDGE_LAYOUTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_fixedsize =
    UX_PICTBRIDGE_FIXED_SIZE_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_cropping =
    UX_PICTBRIDGE_CROPPINGS_DEFAULT;

/* Program the callback function for reading the object data. */
jobinfo -> ux_pictbridge_jobinfo_object_data_read =
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
object -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_EXIF_JPEG;
object -> ux_device_class_pima_object_compressed_size = IMAGE_LEN;
object -> ux_device_class_pima_object_offset = 0;
object -> ux_device_class_pima_object_handle_id =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
object -> ux_device_class_pima_object_length = IMAGE_LEN;

/* File name is in Unicode. */
ux_utility_string_to_unicode("JPEG Image", object ->
    ux_device_class_pima_object_filename);

/* And start the job. */
status =ux_pictbridge_dpsclient_api_start_job(&pictbridge);
```

<span data-ttu-id="d4936-130">이제 Pictbridge 클라이언트는 인쇄 작업을 수행할 수 있으며, 필드에 정의된 콜백을 통해 애플리케이션에서 한 번에 이미지 블록을 페치합니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-130">The Pictbridge client now has a print job to do and will fetch the image blocks at a time from the application through the callback defined in the field</span></span>

```C
jobinfo -> ux_pictbridge_jobinfo_object_data_read
```

<span data-ttu-id="d4936-131">해당 함수의 프로토타입은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-131">The prototype of that function is defined as:</span></span>

## <a name="ux_pictbridge_jobinfo_object_data_read"></a><span data-ttu-id="d4936-132">ux_pictbridge_jobinfo_object_data_read</span><span class="sxs-lookup"><span data-stu-id="d4936-132">ux_pictbridge_jobinfo_object_data_read</span></span>

<span data-ttu-id="d4936-133">인쇄를 위해 사용자 공간에서 데이터 블록 복사</span><span class="sxs-lookup"><span data-stu-id="d4936-133">Copying a block of data from user space for printing</span></span>

### <a name="prototype"></a><span data-ttu-id="d4936-134">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d4936-134">Prototype</span></span>

```C
UINT ux_pictbridge_jobinfo_object_data_read( 
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,  
    ULONG object_offset,  
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="d4936-135">설명</span><span class="sxs-lookup"><span data-stu-id="d4936-135">Description</span></span>

<span data-ttu-id="d4936-136">이 함수는 DPS 클라이언트가 대상 Pictbridge 프린터에 인쇄하기 위해 데이터 블록을 검색해야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-136">This function is called when the DPS client needs to retrieve a data block to print to the target Pictbridge printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="d4936-137">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d4936-137">Parameters</span></span>

- <span data-ttu-id="d4936-138">**pictbridge**: Pictbridge 클래스 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d4936-138">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="d4936-139">**object_buffer**: 개체 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d4936-139">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="d4936-140">**object_offset**: 데이터 블록 읽기를 시작하는 위치</span><span class="sxs-lookup"><span data-stu-id="d4936-140">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="d4936-141">**object_length**: 반환될 길이</span><span class="sxs-lookup"><span data-stu-id="d4936-141">**object_length**: Length to be returned</span></span>
- <span data-ttu-id="d4936-142">**actual_length**: 반환되는 실제 길이</span><span class="sxs-lookup"><span data-stu-id="d4936-142">**actual_length**: Actual length returned</span></span>

### <a name="return-value"></a><span data-ttu-id="d4936-143">반환 값</span><span class="sxs-lookup"><span data-stu-id="d4936-143">Return Value</span></span>

- <span data-ttu-id="d4936-144">**UX_SUCCESS** (0x00) 이 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-144">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="d4936-145">**UX_ERROR** (0x01) 애플리케이션에서 데이터를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-145">**UX_ERROR** (0x01) The application could not retrieve data.</span></span>

### <a name="example"></a><span data-ttu-id="d4936-146">예제</span><span class="sxs-lookup"><span data-stu-id="d4936-146">Example</span></span>

```C
/* Copy the object data. */
UINT ux_demo_object_data_copy(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
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

## <a name="pictbridge-host-implementation"></a><span data-ttu-id="d4936-147">Pictbridge 호스트 구현</span><span class="sxs-lookup"><span data-stu-id="d4936-147">Pictbridge host implementation</span></span>

<span data-ttu-id="d4936-148">Pictbridge의 호스트 구현은 클라이언트와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-148">The host implementation of Pictbridge is different from the client.</span></span>

<span data-ttu-id="d4936-149">Pictbridge 호스트 환경에서 가장 먼저 해야 할 일은 아래 예제와 같이 Pima 클래스를 등록하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-149">The first thing to do in a Pictbridge host environment is to register the Pima class as the example below shows:</span></span>

```C
status = ux_host_stack_class_register(_ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="d4936-150">이 클래스는 USB 스택과 Pictbridge 계층 사이에 있는 일반 PTP 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-150">This class is the generic PTP layer sitting between the USB stack and the Pictbridge layer.</span></span>

<span data-ttu-id="d4936-151">다음 단계는 인쇄 서비스에 대한 Pictbridge 기본값을 다음과 같이 초기화하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-151">The next step is to initialize the Pictbridge default values for print services as follows:</span></span>

| <span data-ttu-id="d4936-152">Pictbridge 필드</span><span class="sxs-lookup"><span data-stu-id="d4936-152">Pictbridge field</span></span>       | <span data-ttu-id="d4936-153">값</span><span class="sxs-lookup"><span data-stu-id="d4936-153">Value</span></span>                                  |
|------------------------|----------------------------------------|
| <span data-ttu-id="d4936-154">DpsVersion[0]</span><span class="sxs-lookup"><span data-stu-id="d4936-154">DpsVersion[0]</span></span>          | <span data-ttu-id="d4936-155">0x00010000</span><span class="sxs-lookup"><span data-stu-id="d4936-155">0x00010000</span></span>                             |
| <span data-ttu-id="d4936-156">DpsVersion[1]</span><span class="sxs-lookup"><span data-stu-id="d4936-156">DpsVersion[1]</span></span>          | <span data-ttu-id="d4936-157">0x00010001</span><span class="sxs-lookup"><span data-stu-id="d4936-157">0x00010001</span></span>                             |
| <span data-ttu-id="d4936-158">DpsVersion[2]</span><span class="sxs-lookup"><span data-stu-id="d4936-158">DpsVersion[2]</span></span>          | <span data-ttu-id="d4936-159">0x00000000</span><span class="sxs-lookup"><span data-stu-id="d4936-159">0x00000000</span></span>                             |
| <span data-ttu-id="d4936-160">VendorSpecificVersion</span><span class="sxs-lookup"><span data-stu-id="d4936-160">VendorSpecificVersion</span></span>  | <span data-ttu-id="d4936-161">0x00010000</span><span class="sxs-lookup"><span data-stu-id="d4936-161">0x00010000</span></span>                             |
| <span data-ttu-id="d4936-162">PrintServiceAvailable</span><span class="sxs-lookup"><span data-stu-id="d4936-162">PrintServiceAvailable</span></span>  | <span data-ttu-id="d4936-163">0x30010000</span><span class="sxs-lookup"><span data-stu-id="d4936-163">0x30010000</span></span>                             |
| <span data-ttu-id="d4936-164">Qualities[0]</span><span class="sxs-lookup"><span data-stu-id="d4936-164">Qualities[0]</span></span>           | <span data-ttu-id="d4936-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d4936-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span></span>        |
| <span data-ttu-id="d4936-166">Qualities[1]</span><span class="sxs-lookup"><span data-stu-id="d4936-166">Qualities[1]</span></span>           | <span data-ttu-id="d4936-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span><span class="sxs-lookup"><span data-stu-id="d4936-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span></span>         |
| <span data-ttu-id="d4936-168">Qualities[2]</span><span class="sxs-lookup"><span data-stu-id="d4936-168">Qualities[2]</span></span>           | <span data-ttu-id="d4936-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span><span class="sxs-lookup"><span data-stu-id="d4936-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span></span>          |
| <span data-ttu-id="d4936-170">Qualities[3]</span><span class="sxs-lookup"><span data-stu-id="d4936-170">Qualities[3]</span></span>           | <span data-ttu-id="d4936-171">UX_PICTBRIDGE_QUALITIES_FINE</span><span class="sxs-lookup"><span data-stu-id="d4936-171">UX_PICTBRIDGE_QUALITIES_FINE</span></span>           |
| <span data-ttu-id="d4936-172">PaperSizes[0]</span><span class="sxs-lookup"><span data-stu-id="d4936-172">PaperSizes[0]</span></span>          | <span data-ttu-id="d4936-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d4936-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span></span>      |
| <span data-ttu-id="d4936-174">PaperSizes[1]</span><span class="sxs-lookup"><span data-stu-id="d4936-174">PaperSizes[1]</span></span>          | <span data-ttu-id="d4936-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span><span class="sxs-lookup"><span data-stu-id="d4936-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span></span>        |
| <span data-ttu-id="d4936-176">PaperSizes[2]</span><span class="sxs-lookup"><span data-stu-id="d4936-176">PaperSizes[2]</span></span>          | <span data-ttu-id="d4936-177">UX_PICTBRIDGE_PAPER_SIZES_L</span><span class="sxs-lookup"><span data-stu-id="d4936-177">UX_PICTBRIDGE_PAPER_SIZES_L</span></span>            |
| <span data-ttu-id="d4936-178">PaperSizes[3]</span><span class="sxs-lookup"><span data-stu-id="d4936-178">PaperSizes[3]</span></span>          | <span data-ttu-id="d4936-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span><span class="sxs-lookup"><span data-stu-id="d4936-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span></span>           |
| <span data-ttu-id="d4936-180">PaperSizes[4]</span><span class="sxs-lookup"><span data-stu-id="d4936-180">PaperSizes[4]</span></span>          | <span data-ttu-id="d4936-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span><span class="sxs-lookup"><span data-stu-id="d4936-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span></span>       |
| <span data-ttu-id="d4936-182">PaperTypes[0]</span><span class="sxs-lookup"><span data-stu-id="d4936-182">PaperTypes[0]</span></span>          | <span data-ttu-id="d4936-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d4936-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span></span>      |
| <span data-ttu-id="d4936-184">PaperTypes[1]</span><span class="sxs-lookup"><span data-stu-id="d4936-184">PaperTypes[1]</span></span>          | <span data-ttu-id="d4936-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span><span class="sxs-lookup"><span data-stu-id="d4936-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span></span>        |
| <span data-ttu-id="d4936-186">PaperTypes[2</span><span class="sxs-lookup"><span data-stu-id="d4936-186">PaperTypes[2</span></span>           | <span data-ttu-id="d4936-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span><span class="sxs-lookup"><span data-stu-id="d4936-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span></span>        |
| <span data-ttu-id="d4936-188">FileTypes[0]</span><span class="sxs-lookup"><span data-stu-id="d4936-188">FileTypes[0]</span></span>           | <span data-ttu-id="d4936-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d4936-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span></span>       |
| <span data-ttu-id="d4936-190">FileTypes[1]</span><span class="sxs-lookup"><span data-stu-id="d4936-190">FileTypes[1]</span></span>           | <span data-ttu-id="d4936-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="d4936-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span></span>     |
| <span data-ttu-id="d4936-192">FileTypes[2]</span><span class="sxs-lookup"><span data-stu-id="d4936-192">FileTypes[2]</span></span>           | <span data-ttu-id="d4936-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span><span class="sxs-lookup"><span data-stu-id="d4936-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span></span>          |
| <span data-ttu-id="d4936-194">FileTypes[3]</span><span class="sxs-lookup"><span data-stu-id="d4936-194">FileTypes[3]</span></span>           | <span data-ttu-id="d4936-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span><span class="sxs-lookup"><span data-stu-id="d4936-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span></span>          |
| <span data-ttu-id="d4936-196">DatePrints[0]</span><span class="sxs-lookup"><span data-stu-id="d4936-196">DatePrints[0]</span></span>          | <span data-ttu-id="d4936-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d4936-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span></span>      |
| <span data-ttu-id="d4936-198">DatePrints[1]</span><span class="sxs-lookup"><span data-stu-id="d4936-198">DatePrints[1]</span></span>          | <span data-ttu-id="d4936-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="d4936-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span></span>          |
| <span data-ttu-id="d4936-200">DatePrints[2]</span><span class="sxs-lookup"><span data-stu-id="d4936-200">DatePrints[2]</span></span>          | <span data-ttu-id="d4936-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="d4936-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span></span>           |
| <span data-ttu-id="d4936-202">FileNamePrints[0]</span><span class="sxs-lookup"><span data-stu-id="d4936-202">FileNamePrints[0]</span></span>      | <span data-ttu-id="d4936-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d4936-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span></span> |
| <span data-ttu-id="d4936-204">FileNamePrints[1]</span><span class="sxs-lookup"><span data-stu-id="d4936-204">FileNamePrints[1]</span></span>      | <span data-ttu-id="d4936-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="d4936-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span></span>     |
| <span data-ttu-id="d4936-206">FileNamePrints[2]</span><span class="sxs-lookup"><span data-stu-id="d4936-206">FileNamePrints[2]</span></span>      | <span data-ttu-id="d4936-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="d4936-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span></span>      |
| <span data-ttu-id="d4936-208">ImageOptimizes[0]</span><span class="sxs-lookup"><span data-stu-id="d4936-208">ImageOptimizes[0]</span></span>      | <span data-ttu-id="d4936-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d4936-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span></span>  |
| <span data-ttu-id="d4936-210">ImageOptimizes[1]</span><span class="sxs-lookup"><span data-stu-id="d4936-210">ImageOptimizes[1]</span></span>      | <span data-ttu-id="d4936-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span><span class="sxs-lookup"><span data-stu-id="d4936-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span></span>      |
| <span data-ttu-id="d4936-212">ImageOptimizes[2]</span><span class="sxs-lookup"><span data-stu-id="d4936-212">ImageOptimizes[2]</span></span>      | <span data-ttu-id="d4936-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span><span class="sxs-lookup"><span data-stu-id="d4936-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span></span>       |
| <span data-ttu-id="d4936-214">Layouts[0]</span><span class="sxs-lookup"><span data-stu-id="d4936-214">Layouts[0]</span></span>             | <span data-ttu-id="d4936-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d4936-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span></span>          |
| <span data-ttu-id="d4936-216">Layouts[1]</span><span class="sxs-lookup"><span data-stu-id="d4936-216">Layouts[1]</span></span>             | <span data-ttu-id="d4936-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span><span class="sxs-lookup"><span data-stu-id="d4936-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span></span>      |
| <span data-ttu-id="d4936-218">Layouts[2]</span><span class="sxs-lookup"><span data-stu-id="d4936-218">Layouts[2]</span></span>             | <span data-ttu-id="d4936-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span><span class="sxs-lookup"><span data-stu-id="d4936-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span></span>      |
| <span data-ttu-id="d4936-220">Layouts[3]</span><span class="sxs-lookup"><span data-stu-id="d4936-220">Layouts[3]</span></span>             | <span data-ttu-id="d4936-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span><span class="sxs-lookup"><span data-stu-id="d4936-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span></span>  |
| <span data-ttu-id="d4936-222">FixedSizes[0]</span><span class="sxs-lookup"><span data-stu-id="d4936-222">FixedSizes[0]</span></span>          | <span data-ttu-id="d4936-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d4936-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span></span>       |
| <span data-ttu-id="d4936-224">FixedSizes[1]</span><span class="sxs-lookup"><span data-stu-id="d4936-224">FixedSizes[1]</span></span>          | <span data-ttu-id="d4936-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span><span class="sxs-lookup"><span data-stu-id="d4936-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span></span>        |
| <span data-ttu-id="d4936-226">FixedSizes[2]</span><span class="sxs-lookup"><span data-stu-id="d4936-226">FixedSizes[2]</span></span>          | <span data-ttu-id="d4936-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span><span class="sxs-lookup"><span data-stu-id="d4936-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span></span>         |
| <span data-ttu-id="d4936-228">FixedSizes[3]</span><span class="sxs-lookup"><span data-stu-id="d4936-228">FixedSizes[3]</span></span>          | <span data-ttu-id="d4936-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span><span class="sxs-lookup"><span data-stu-id="d4936-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span></span>         |
| <span data-ttu-id="d4936-230">FixedSizes[4]</span><span class="sxs-lookup"><span data-stu-id="d4936-230">FixedSizes[4]</span></span>          | <span data-ttu-id="d4936-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span><span class="sxs-lookup"><span data-stu-id="d4936-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span></span>      |
| <span data-ttu-id="d4936-232">FixedSizes[5]</span><span class="sxs-lookup"><span data-stu-id="d4936-232">FixedSizes[5]</span></span>          | <span data-ttu-id="d4936-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span><span class="sxs-lookup"><span data-stu-id="d4936-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span></span>        |
| <span data-ttu-id="d4936-234">FixedSizes[6]</span><span class="sxs-lookup"><span data-stu-id="d4936-234">FixedSizes[6]</span></span>          | <span data-ttu-id="d4936-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span><span class="sxs-lookup"><span data-stu-id="d4936-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span></span>            |
| <span data-ttu-id="d4936-236">Croppings[0]</span><span class="sxs-lookup"><span data-stu-id="d4936-236">Croppings[0]</span></span>           | <span data-ttu-id="d4936-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="d4936-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span></span>        |
| <span data-ttu-id="d4936-238">Croppings[1]</span><span class="sxs-lookup"><span data-stu-id="d4936-238">Croppings[1]</span></span>           | <span data-ttu-id="d4936-239">UX_PICTBRIDGE_CROPPINGS_OFF</span><span class="sxs-lookup"><span data-stu-id="d4936-239">UX_PICTBRIDGE_CROPPINGS_OFF</span></span>            |
| <span data-ttu-id="d4936-240">Croppings[2]</span><span class="sxs-lookup"><span data-stu-id="d4936-240">Croppings[2]</span></span>           | <span data-ttu-id="d4936-241">UX_PICTBRIDGE_CROPPINGS_ON</span><span class="sxs-lookup"><span data-stu-id="d4936-241">UX_PICTBRIDGE_CROPPINGS_ON</span></span>             |

<span data-ttu-id="d4936-242">DPS 호스트의 상태 시스템은 유휴 상태로 설정되고 새 인쇄 작업을 수락할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-242">The state machine of the DPS host will be set to Idle and ready to accept a new print job.</span></span>

<span data-ttu-id="d4936-243">이제 아래 예제에서 볼 수 있듯이 Pictbridge의 호스트 부분을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-243">The host portion of Pictbridge can now be started as the example below shows:</span></span>

```C
/* Activate the pictbridge dpshost. */
status = ux_pictbridge_dpshost_start(&pictbridge, pima);

if (status != UX_SUCCESS)
    return;
```

<span data-ttu-id="d4936-244">데이터를 인쇄할 준비가 되면 Pictbridge 호스트 함수에서 콜백이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-244">The Pictbridge host function requires a callback when data is ready to be printed.</span></span> <span data-ttu-id="d4936-245">이는 다음과 같이 Pictbridge 호스트 구조에 함수 포인터를 전달하여 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-245">This is accomplished by passing a function pointer in the pictbridge host structure as follows.</span></span>

```C
/* Set a callback when an object is being received. */
pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

<span data-ttu-id="d4936-246">이 함수에는 다음과 같은 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-246">This function has the following properties.</span></span>

## <a name="ux_pictbridge_application_object_data_write"></a><span data-ttu-id="d4936-247">ux_pictbridge_application_object_data_write</span><span class="sxs-lookup"><span data-stu-id="d4936-247">ux_pictbridge_application_object_data_write</span></span>

<span data-ttu-id="d4936-248">인쇄용 데이터 블록 작성</span><span class="sxs-lookup"><span data-stu-id="d4936-248">Writing a block of data for printing</span></span>

### <a name="prototype"></a><span data-ttu-id="d4936-249">프로토타입</span><span class="sxs-lookup"><span data-stu-id="d4936-249">Prototype</span></span>

```C
UINT ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge, 
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="d4936-250">설명</span><span class="sxs-lookup"><span data-stu-id="d4936-250">Description</span></span>

<span data-ttu-id="d4936-251">이 함수는 DPS 서버에서 로컬 프린터로 인쇄하기 위해 DPS 클라이언트에서 데이터 블록을 검색해야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-251">This function is called when the DPS server needs to retrieve a data block from the DPS client to print to the local printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="d4936-252">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d4936-252">Parameters</span></span>

- <span data-ttu-id="d4936-253">**pictbridge**: Pictbridge 클래스 인스턴스에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d4936-253">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="d4936-254">**object_buffer**: 개체 버퍼에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="d4936-254">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="d4936-255">**object_offset**: 데이터 블록 읽기를 시작하는 위치</span><span class="sxs-lookup"><span data-stu-id="d4936-255">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="d4936-256">**total_length**: 개체의 전체 길이</span><span class="sxs-lookup"><span data-stu-id="d4936-256">**total_length**: Entire length of object</span></span>
- <span data-ttu-id="d4936-257">**length**: 이 버퍼의 길이</span><span class="sxs-lookup"><span data-stu-id="d4936-257">**length**: Length of this buffer</span></span>

### <a name="return-value"></a><span data-ttu-id="d4936-258">반환 값</span><span class="sxs-lookup"><span data-stu-id="d4936-258">Return Value</span></span>

- <span data-ttu-id="d4936-259">**UX_SUCCESS** (0x00) 이 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-259">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="d4936-260">**UX_ERROR** (0x01) 애플리케이션에서 데이터를 인쇄할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4936-260">**UX_ERROR** (0x01) The application could not print data.</span></span>

### <a name="example"></a><span data-ttu-id="d4936-261">예제</span><span class="sxs-lookup"><span data-stu-id="d4936-261">Example</span></span>

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
