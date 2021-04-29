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
# <a name="chapter-5---usbx-device-class-considerations"></a><span data-ttu-id="2639b-103">5장 - USBX 디바이스 클래스 고려 사항</span><span class="sxs-lookup"><span data-stu-id="2639b-103">Chapter 5 - USBX Device Class Considerations</span></span>

## <a name="device-class-registration"></a><span data-ttu-id="2639b-104">디바이스 클래스 등록</span><span class="sxs-lookup"><span data-stu-id="2639b-104">Device Class registration</span></span>

<span data-ttu-id="2639b-105">각 디바이스 클래스는 동일한 등록 원칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-105">Each device class follows the same principle for registration.</span></span> <span data-ttu-id="2639b-106">특정 클래스 매개 변수를 포함하는 구조체는 클래스 initialize 함수에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-106">A structure containing specific class parameters is passed to the class initialize function.</span></span>

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

<span data-ttu-id="2639b-107">각 클래스는 클래스 인스턴스가 활성화될 때 필요에 따라 콜백 함수를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-107">Each class can register, optionally, a callback function when a instance of the class gets activated.</span></span> <span data-ttu-id="2639b-108">그런 다음 인스턴스가 생성되었음을 애플리케이션에 알리기 위해 디바이스 스택에서 콜백을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-108">The callback is then called by the device stack to inform the application that an instance was created.</span></span>

<span data-ttu-id="2639b-109">애플리케이션 본문에는 다음 예제와 같이 활성화 및 비활성화를 위한 함수 2개가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-109">The application would have in its body the 2 functions for activation and deactivation, as shown in the following example.</span></span>

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

<span data-ttu-id="2639b-110">두 함수 내에서는 클래스 인스턴스를 기억하고 애플리케이션의 나머지 부분과 동기화하는 작업을 제외한 어떤 작업도 수행하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-110">It is not recommended to do anything within these functions but to memorize the instance of the class and synchronize with the rest of the application.</span></span>

## <a name="usb-device-storage-class"></a><span data-ttu-id="2639b-111">USB 디바이스 스토리지 클래스</span><span class="sxs-lookup"><span data-stu-id="2639b-111">USB Device Storage Class</span></span>

<span data-ttu-id="2639b-112">USB 디바이스 스토리지 클래스를 사용하면 시스템에 포함된 스토리지 디바이스를 USB 호스트에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-112">The USB device storage class allows for a storage device embedded in the system to be made visible to a USB host.</span></span>

<span data-ttu-id="2639b-113">USB 디바이스 스토리지 클래스가 단독으로 스토리지 솔루션을 제공하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-113">The USB device storage class does not by itself provide a storage solution.</span></span> <span data-ttu-id="2639b-114">단지 호스트에서 들어오는 SCSI 요청을 수락하고 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-114">It merely accepts and interprets SCSI requests coming from the host.</span></span> <span data-ttu-id="2639b-115">요청 중 하나가 읽기 또는 쓰기 명령이면 USB 디바이스 스토리지 클래스는 ATA 디바이스 드라이버 또는 플래시 디바이스 드라이버와 같은 실제 스토리지 디바이스 처리기에 대해 미리 정의된 콜백을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-115">When one of these requests is a read or a write command, it will invoke a pre-defined call back to a real storage device handler, such as an ATA device driver or a Flash device driver.</span></span>

<span data-ttu-id="2639b-116">디바이스 스토리지 클래스를 초기화하면 필요한 모든 정보를 포함하는 포인터 구조체가 클래스에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-116">When initializing the device storage class, a pointer structure is given to the class that contains all the information necessary.</span></span> <span data-ttu-id="2639b-117">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-117">An example is given below.</span></span>

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

<span data-ttu-id="2639b-118">이 예제에서는 해당 매개 변수에 문자열 포인터를 할당하여 드라이버 스토리지 문자열을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-118">In this example, the driver storage strings are customized by assigning string pointers to corresponding parameter.</span></span> <span data-ttu-id="2639b-119">문자열 포인터 중 하나를 UX_NULL로 유지하면 기본 Azure RTOS 문자열이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-119">If any one of the string pointer is left to UX_NULL, the default Azure RTOS string is used.</span></span>

<span data-ttu-id="2639b-120">이 예제에서는 드라이브의 마지막 블록 주소, 즉 LBA도 논리 섹터 크기와 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-120">In this example, the drive's last block address or LBA is given as well as the logical sector size.</span></span> <span data-ttu-id="2639b-121">LBA는 미디어에서 사용할 수 있는 섹터 수-1입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-121">The LBA is the number of sectors available in the media –1.</span></span> <span data-ttu-id="2639b-122">일반 스토리지 미디어의 블록 길이는 512로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-122">The block length is set to 512 in regular storage media.</span></span> <span data-ttu-id="2639b-123">광학 드라이브의 경우 2048로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-123">It can be set to 2048 for optical drives.</span></span>

<span data-ttu-id="2639b-124">애플리케이션은 스토리지 클래스가 미디어를 읽고, 쓰고, 상태를 가져올 수 있도록 세 가지 콜백 함수 포인터를 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-124">The application needs to pass three callback function pointers to allow the storage class to read, write and obtain status for the media.</span></span>

<span data-ttu-id="2639b-125">읽기 및 쓰기 함수의 프로토타입은 아래 예제에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-125">The prototypes for the read and write functions are shown in the example below.</span></span>

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

<span data-ttu-id="2639b-126">위치:</span><span class="sxs-lookup"><span data-stu-id="2639b-126">Where:</span></span>

- <span data-ttu-id="2639b-127">*storage* 는 스토리지 클래스 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-127">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="2639b-128">*lun* 은 명령이 전달되는 LUN입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-128">*lun* is the LUN the command is directed to.</span></span>
- <span data-ttu-id="2639b-129">*data_pointer* 는 읽기 또는 쓰기에 사용할 버퍼의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-129">*data_pointer* is the address of the buffer to be used for reading or writing.</span></span>
- <span data-ttu-id="2639b-130">*number_blocks* 는 읽기/쓰기를 수행할 섹터 수입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-130">*number_blocks* is the number of sectors to read/write.</span></span>
- <span data-ttu-id="2639b-131">*lba* 는 읽을 섹터 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-131">*lba* is the sector address to read.</span></span>
- <span data-ttu-id="2639b-132">*media_status* 는 미디어 상태 콜백 반환 값과 똑같이 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-132">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="2639b-133">반환 값은 성공 또는 실패한 작업을 나타내는 UX_SUCCESS 또는 UX_ERROR 값을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-133">The return value can have either the value UX_SUCCESS or UX_ERROR indicating a successful or unsuccessful operation.</span></span> <span data-ttu-id="2639b-134">다른 오류 코드는 작업에서 반환할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-134">These operations do not need to return any other error codes.</span></span> <span data-ttu-id="2639b-135">작업에 오류가 있으면 스토리지 클래스에서 상태 콜백 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-135">If there is an error in any operation, the storage class will invoke the status call back function.</span></span>

<span data-ttu-id="2639b-136">이 함수의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-136">This function has the following prototype.</span></span>

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

<span data-ttu-id="2639b-137">호출 매개 변수 media_id는 현재 사용되지 않으며 항상 0이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-137">The calling parameter media_id is not currently used and should always be 0.</span></span> <span data-ttu-id="2639b-138">향후 여러 스토리지 디바이스나 여러 SCSI LUN이 있는 스토리지 디바이스를 구분하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-138">In the future it may be used to distinguish multiple storage devices or storage devices with multiple SCSI LUNs.</span></span> <span data-ttu-id="2639b-139">이 버전의 스토리지 클래스는 여러 스토리지 클래스 인스턴스나 여러 SCSI LUN이 있는 스토리지 디바이스를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-139">This version of the storage class does not support multiple instances of the storage class or storage devices with multiple SCSI LUNs.</span></span>

<span data-ttu-id="2639b-140">반환 값은 다음과 같은 형식의 SCSI 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-140">The return value is a SCSI error code that can have the following format.</span></span>

- <span data-ttu-id="2639b-141">**비트 0~7** Sense_key</span><span class="sxs-lookup"><span data-stu-id="2639b-141">**Bits 0-7** Sense_key</span></span>
- <span data-ttu-id="2639b-142">**비트 8~15** 추가 Sense 코드</span><span class="sxs-lookup"><span data-stu-id="2639b-142">**Bits 8-15** Additional Sense Code</span></span>
- <span data-ttu-id="2639b-143">**비트 16~23** 추가 Sense 코드 한정자</span><span class="sxs-lookup"><span data-stu-id="2639b-143">**Bits 16-23** Additional Sense Code Qualifier</span></span>

<span data-ttu-id="2639b-144">다음 표에서는 가능한 Sense/ASC/ASCQ 조합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-144">The following table provides the possible Sense/ASC/ASCQ combinations.</span></span>

| <span data-ttu-id="2639b-145">Sense 키</span><span class="sxs-lookup"><span data-stu-id="2639b-145">Sense Key</span></span> | <span data-ttu-id="2639b-146">ASC</span><span class="sxs-lookup"><span data-stu-id="2639b-146">ASC</span></span> | <span data-ttu-id="2639b-147">ASCQ</span><span class="sxs-lookup"><span data-stu-id="2639b-147">ASCQ</span></span> | <span data-ttu-id="2639b-148">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-148">Description</span></span>                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| <span data-ttu-id="2639b-149">00</span><span class="sxs-lookup"><span data-stu-id="2639b-149">00</span></span>        | <span data-ttu-id="2639b-150">00</span><span class="sxs-lookup"><span data-stu-id="2639b-150">00</span></span>  | <span data-ttu-id="2639b-151">00</span><span class="sxs-lookup"><span data-stu-id="2639b-151">00</span></span>   | <span data-ttu-id="2639b-152">SENSE 없음</span><span class="sxs-lookup"><span data-stu-id="2639b-152">NO SENSE</span></span>                                          |
| <span data-ttu-id="2639b-153">01</span><span class="sxs-lookup"><span data-stu-id="2639b-153">01</span></span>        | <span data-ttu-id="2639b-154">17</span><span class="sxs-lookup"><span data-stu-id="2639b-154">17</span></span>  | <span data-ttu-id="2639b-155">01</span><span class="sxs-lookup"><span data-stu-id="2639b-155">01</span></span>   | <span data-ttu-id="2639b-156">다시 시도를 사용하여 데이터 복구됨</span><span class="sxs-lookup"><span data-stu-id="2639b-156">RECOVERED DATA WITH RETRIES</span></span>                       |
| <span data-ttu-id="2639b-157">01</span><span class="sxs-lookup"><span data-stu-id="2639b-157">01</span></span>        | <span data-ttu-id="2639b-158">18</span><span class="sxs-lookup"><span data-stu-id="2639b-158">18</span></span>  | <span data-ttu-id="2639b-159">00</span><span class="sxs-lookup"><span data-stu-id="2639b-159">00</span></span>   | <span data-ttu-id="2639b-160">ECC를 사용하여 데이터 복구됨</span><span class="sxs-lookup"><span data-stu-id="2639b-160">RECOVERED DATA WITH ECC</span></span>                           |
| <span data-ttu-id="2639b-161">02</span><span class="sxs-lookup"><span data-stu-id="2639b-161">02</span></span>        | <span data-ttu-id="2639b-162">04</span><span class="sxs-lookup"><span data-stu-id="2639b-162">04</span></span>  | <span data-ttu-id="2639b-163">01</span><span class="sxs-lookup"><span data-stu-id="2639b-163">01</span></span>   | <span data-ttu-id="2639b-164">논리 드라이브가 준비되지 않음 - 준비 중</span><span class="sxs-lookup"><span data-stu-id="2639b-164">LOGICAL DRIVE NOT READY - BECOMING READY</span></span>          |
| <span data-ttu-id="2639b-165">02</span><span class="sxs-lookup"><span data-stu-id="2639b-165">02</span></span>        | <span data-ttu-id="2639b-166">04</span><span class="sxs-lookup"><span data-stu-id="2639b-166">04</span></span>  | <span data-ttu-id="2639b-167">02</span><span class="sxs-lookup"><span data-stu-id="2639b-167">02</span></span>   | <span data-ttu-id="2639b-168">논리 드라이브가 준비되지 않음 - 초기화 필요</span><span class="sxs-lookup"><span data-stu-id="2639b-168">LOGICAL DRIVE NOT READY - INITIALIZATION REQUIRED</span></span> |
| <span data-ttu-id="2639b-169">02</span><span class="sxs-lookup"><span data-stu-id="2639b-169">02</span></span>        | <span data-ttu-id="2639b-170">04</span><span class="sxs-lookup"><span data-stu-id="2639b-170">04</span></span>  | <span data-ttu-id="2639b-171">04</span><span class="sxs-lookup"><span data-stu-id="2639b-171">04</span></span>   | <span data-ttu-id="2639b-172">논리적 단위가 준비되지 않음 - 포맷 진행 중</span><span class="sxs-lookup"><span data-stu-id="2639b-172">LOGICAL UNIT NOT READY - FORMAT IN PROGRESS</span></span>       |
| <span data-ttu-id="2639b-173">02</span><span class="sxs-lookup"><span data-stu-id="2639b-173">02</span></span>        | <span data-ttu-id="2639b-174">04</span><span class="sxs-lookup"><span data-stu-id="2639b-174">04</span></span>  | <span data-ttu-id="2639b-175">FF</span><span class="sxs-lookup"><span data-stu-id="2639b-175">FF</span></span>   | <span data-ttu-id="2639b-176">논리 드라이브가 준비되지 않음 - 디바이스 사용 중</span><span class="sxs-lookup"><span data-stu-id="2639b-176">LOGICAL DRIVE NOT READY - DEVICE IS BUSY</span></span>          |
| <span data-ttu-id="2639b-177">02</span><span class="sxs-lookup"><span data-stu-id="2639b-177">02</span></span>        | <span data-ttu-id="2639b-178">06</span><span class="sxs-lookup"><span data-stu-id="2639b-178">06</span></span>  | <span data-ttu-id="2639b-179">00</span><span class="sxs-lookup"><span data-stu-id="2639b-179">00</span></span>   | <span data-ttu-id="2639b-180">참조 위치를 찾을 수 없음</span><span class="sxs-lookup"><span data-stu-id="2639b-180">NO REFERENCE POSITION FOUND</span></span>                       |
| <span data-ttu-id="2639b-181">02</span><span class="sxs-lookup"><span data-stu-id="2639b-181">02</span></span>        | <span data-ttu-id="2639b-182">08</span><span class="sxs-lookup"><span data-stu-id="2639b-182">08</span></span>  | <span data-ttu-id="2639b-183">00</span><span class="sxs-lookup"><span data-stu-id="2639b-183">00</span></span>   | <span data-ttu-id="2639b-184">논리적 단위 통신 오류</span><span class="sxs-lookup"><span data-stu-id="2639b-184">LOGICAL UNIT COMMUNICATION FAILURE</span></span>                |
| <span data-ttu-id="2639b-185">02</span><span class="sxs-lookup"><span data-stu-id="2639b-185">02</span></span>        | <span data-ttu-id="2639b-186">08</span><span class="sxs-lookup"><span data-stu-id="2639b-186">08</span></span>  | <span data-ttu-id="2639b-187">01</span><span class="sxs-lookup"><span data-stu-id="2639b-187">01</span></span>   | <span data-ttu-id="2639b-188">논리적 단위 통신 시간 초과</span><span class="sxs-lookup"><span data-stu-id="2639b-188">LOGICAL UNIT COMMUNICATION TIME-OUT</span></span>               |
| <span data-ttu-id="2639b-189">02</span><span class="sxs-lookup"><span data-stu-id="2639b-189">02</span></span>        | <span data-ttu-id="2639b-190">08</span><span class="sxs-lookup"><span data-stu-id="2639b-190">08</span></span>  | <span data-ttu-id="2639b-191">80</span><span class="sxs-lookup"><span data-stu-id="2639b-191">80</span></span>   | <span data-ttu-id="2639b-192">논리적 단위 통신 오버런</span><span class="sxs-lookup"><span data-stu-id="2639b-192">LOGICAL UNIT COMMUNICATION OVERRUN</span></span>                |
| <span data-ttu-id="2639b-193">02</span><span class="sxs-lookup"><span data-stu-id="2639b-193">02</span></span>        | <span data-ttu-id="2639b-194">3A</span><span class="sxs-lookup"><span data-stu-id="2639b-194">3A</span></span>  | <span data-ttu-id="2639b-195">00</span><span class="sxs-lookup"><span data-stu-id="2639b-195">00</span></span>   | <span data-ttu-id="2639b-196">매체 없음</span><span class="sxs-lookup"><span data-stu-id="2639b-196">MEDIUM NOT PRESENT</span></span>                                |
| <span data-ttu-id="2639b-197">02</span><span class="sxs-lookup"><span data-stu-id="2639b-197">02</span></span>        | <span data-ttu-id="2639b-198">54</span><span class="sxs-lookup"><span data-stu-id="2639b-198">54</span></span>  | <span data-ttu-id="2639b-199">00</span><span class="sxs-lookup"><span data-stu-id="2639b-199">00</span></span>   | <span data-ttu-id="2639b-200">USB-호스트 시스템 인터페이스 오류</span><span class="sxs-lookup"><span data-stu-id="2639b-200">USB TO HOST SYSTEM INTERFACE FAILURE</span></span>              |
| <span data-ttu-id="2639b-201">02</span><span class="sxs-lookup"><span data-stu-id="2639b-201">02</span></span>        | <span data-ttu-id="2639b-202">80</span><span class="sxs-lookup"><span data-stu-id="2639b-202">80</span></span>  | <span data-ttu-id="2639b-203">00</span><span class="sxs-lookup"><span data-stu-id="2639b-203">00</span></span>   | <span data-ttu-id="2639b-204">리소스 부족</span><span class="sxs-lookup"><span data-stu-id="2639b-204">INSUFFICIENT RESOURCES</span></span>                            |
| <span data-ttu-id="2639b-205">02</span><span class="sxs-lookup"><span data-stu-id="2639b-205">02</span></span>        | <span data-ttu-id="2639b-206">FF</span><span class="sxs-lookup"><span data-stu-id="2639b-206">FF</span></span>  | <span data-ttu-id="2639b-207">FF</span><span class="sxs-lookup"><span data-stu-id="2639b-207">FF</span></span>   | <span data-ttu-id="2639b-208">알 수 없는 오류</span><span class="sxs-lookup"><span data-stu-id="2639b-208">UNKNOWN ERROR</span></span>                                     |
| <span data-ttu-id="2639b-209">03</span><span class="sxs-lookup"><span data-stu-id="2639b-209">03</span></span>        | <span data-ttu-id="2639b-210">02</span><span class="sxs-lookup"><span data-stu-id="2639b-210">02</span></span>  | <span data-ttu-id="2639b-211">00</span><span class="sxs-lookup"><span data-stu-id="2639b-211">00</span></span>   | <span data-ttu-id="2639b-212">검색 미완료</span><span class="sxs-lookup"><span data-stu-id="2639b-212">NO SEEK COMPLETE</span></span>                                  |
| <span data-ttu-id="2639b-213">03</span><span class="sxs-lookup"><span data-stu-id="2639b-213">03</span></span>        | <span data-ttu-id="2639b-214">03</span><span class="sxs-lookup"><span data-stu-id="2639b-214">03</span></span>  | <span data-ttu-id="2639b-215">00</span><span class="sxs-lookup"><span data-stu-id="2639b-215">00</span></span>   | <span data-ttu-id="2639b-216">쓰기 오류</span><span class="sxs-lookup"><span data-stu-id="2639b-216">WRITE FAULT</span></span>                                       |
| <span data-ttu-id="2639b-217">03</span><span class="sxs-lookup"><span data-stu-id="2639b-217">03</span></span>        | <span data-ttu-id="2639b-218">10</span><span class="sxs-lookup"><span data-stu-id="2639b-218">10</span></span>  | <span data-ttu-id="2639b-219">00</span><span class="sxs-lookup"><span data-stu-id="2639b-219">00</span></span>   | <span data-ttu-id="2639b-220">ID CRC 오류</span><span class="sxs-lookup"><span data-stu-id="2639b-220">ID CRC ERROR</span></span>                                      |
| <span data-ttu-id="2639b-221">03</span><span class="sxs-lookup"><span data-stu-id="2639b-221">03</span></span>        | <span data-ttu-id="2639b-222">11</span><span class="sxs-lookup"><span data-stu-id="2639b-222">11</span></span>  | <span data-ttu-id="2639b-223">00</span><span class="sxs-lookup"><span data-stu-id="2639b-223">00</span></span>   | <span data-ttu-id="2639b-224">복구되지 않은 읽기 오류</span><span class="sxs-lookup"><span data-stu-id="2639b-224">UNRECOVERED READ ERROR</span></span>                            |
| <span data-ttu-id="2639b-225">03</span><span class="sxs-lookup"><span data-stu-id="2639b-225">03</span></span>        | <span data-ttu-id="2639b-226">12</span><span class="sxs-lookup"><span data-stu-id="2639b-226">12</span></span>  | <span data-ttu-id="2639b-227">00</span><span class="sxs-lookup"><span data-stu-id="2639b-227">00</span></span>   | <span data-ttu-id="2639b-228">ID 필드의 주소 표시를 찾을 수 없음</span><span class="sxs-lookup"><span data-stu-id="2639b-228">ADDRESS MARK NOT FOUND FOR ID FIELD</span></span>               |
| <span data-ttu-id="2639b-229">03</span><span class="sxs-lookup"><span data-stu-id="2639b-229">03</span></span>        | <span data-ttu-id="2639b-230">13</span><span class="sxs-lookup"><span data-stu-id="2639b-230">13</span></span>  | <span data-ttu-id="2639b-231">00</span><span class="sxs-lookup"><span data-stu-id="2639b-231">00</span></span>   | <span data-ttu-id="2639b-232">데이터 필드의 주소 표시를 찾을 수 없음</span><span class="sxs-lookup"><span data-stu-id="2639b-232">ADDRESS MARK NOT FOUND FOR DATA FIELD</span></span>             |
| <span data-ttu-id="2639b-233">03</span><span class="sxs-lookup"><span data-stu-id="2639b-233">03</span></span>        | <span data-ttu-id="2639b-234">14</span><span class="sxs-lookup"><span data-stu-id="2639b-234">14</span></span>  | <span data-ttu-id="2639b-235">00</span><span class="sxs-lookup"><span data-stu-id="2639b-235">00</span></span>   | <span data-ttu-id="2639b-236">기록된 엔터티를 찾을 수 없음</span><span class="sxs-lookup"><span data-stu-id="2639b-236">RECORDED ENTITY NOT FOUND</span></span>                         |
| <span data-ttu-id="2639b-237">03</span><span class="sxs-lookup"><span data-stu-id="2639b-237">03</span></span>        | <span data-ttu-id="2639b-238">30</span><span class="sxs-lookup"><span data-stu-id="2639b-238">30</span></span>  | <span data-ttu-id="2639b-239">01</span><span class="sxs-lookup"><span data-stu-id="2639b-239">01</span></span>   | <span data-ttu-id="2639b-240">매체를 읽을 수 없음 - 알 수 없는 포맷</span><span class="sxs-lookup"><span data-stu-id="2639b-240">CANNOT READ MEDIUM - UNKNOWN FORMAT</span></span>               |
| <span data-ttu-id="2639b-241">03</span><span class="sxs-lookup"><span data-stu-id="2639b-241">03</span></span>        | <span data-ttu-id="2639b-242">31</span><span class="sxs-lookup"><span data-stu-id="2639b-242">31</span></span>  | <span data-ttu-id="2639b-243">01</span><span class="sxs-lookup"><span data-stu-id="2639b-243">01</span></span>   | <span data-ttu-id="2639b-244">FORMAT 명령 오류</span><span class="sxs-lookup"><span data-stu-id="2639b-244">FORMAT COMMAND FAILED</span></span>                             |
| <span data-ttu-id="2639b-245">04</span><span class="sxs-lookup"><span data-stu-id="2639b-245">04</span></span>        | <span data-ttu-id="2639b-246">40</span><span class="sxs-lookup"><span data-stu-id="2639b-246">40</span></span>  | <span data-ttu-id="2639b-247">NN</span><span class="sxs-lookup"><span data-stu-id="2639b-247">NN</span></span>   | <span data-ttu-id="2639b-248">구성 요소 NN 진단 오류(80H-FFH)</span><span class="sxs-lookup"><span data-stu-id="2639b-248">DIAGNOSTIC FAILURE ON COMPONENT NN (80H-FFH)</span></span>      |
| <span data-ttu-id="2639b-249">05</span><span class="sxs-lookup"><span data-stu-id="2639b-249">05</span></span>        | <span data-ttu-id="2639b-250">1A</span><span class="sxs-lookup"><span data-stu-id="2639b-250">1A</span></span>  | <span data-ttu-id="2639b-251">00</span><span class="sxs-lookup"><span data-stu-id="2639b-251">00</span></span>   | <span data-ttu-id="2639b-252">매개 변수 목록 길이 오류</span><span class="sxs-lookup"><span data-stu-id="2639b-252">PARAMETER LIST LENGTH ERROR</span></span>                       |
| <span data-ttu-id="2639b-253">05</span><span class="sxs-lookup"><span data-stu-id="2639b-253">05</span></span>        | <span data-ttu-id="2639b-254">20</span><span class="sxs-lookup"><span data-stu-id="2639b-254">20</span></span>  | <span data-ttu-id="2639b-255">00</span><span class="sxs-lookup"><span data-stu-id="2639b-255">00</span></span>   | <span data-ttu-id="2639b-256">잘못된 명령 작업 코드</span><span class="sxs-lookup"><span data-stu-id="2639b-256">INVALID COMMAND OPERATION CODE</span></span>                    |
| <span data-ttu-id="2639b-257">05</span><span class="sxs-lookup"><span data-stu-id="2639b-257">05</span></span>        | <span data-ttu-id="2639b-258">21</span><span class="sxs-lookup"><span data-stu-id="2639b-258">21</span></span>  | <span data-ttu-id="2639b-259">00</span><span class="sxs-lookup"><span data-stu-id="2639b-259">00</span></span>   | <span data-ttu-id="2639b-260">논리적 블록 주소가 범위를 벗어남</span><span class="sxs-lookup"><span data-stu-id="2639b-260">LOGICAL BLOCK ADDRESS OUT OF RANGE</span></span>                |
| <span data-ttu-id="2639b-261">05</span><span class="sxs-lookup"><span data-stu-id="2639b-261">05</span></span>        | <span data-ttu-id="2639b-262">24</span><span class="sxs-lookup"><span data-stu-id="2639b-262">24</span></span>  | <span data-ttu-id="2639b-263">00</span><span class="sxs-lookup"><span data-stu-id="2639b-263">00</span></span>   | <span data-ttu-id="2639b-264">명령 패킷에 잘못된 필드 있음</span><span class="sxs-lookup"><span data-stu-id="2639b-264">INVALID FIELD IN COMMAND PACKET</span></span>                   |
| <span data-ttu-id="2639b-265">05</span><span class="sxs-lookup"><span data-stu-id="2639b-265">05</span></span>        | <span data-ttu-id="2639b-266">25</span><span class="sxs-lookup"><span data-stu-id="2639b-266">25</span></span>  | <span data-ttu-id="2639b-267">00</span><span class="sxs-lookup"><span data-stu-id="2639b-267">00</span></span>   | <span data-ttu-id="2639b-268">논리적 단위가 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="2639b-268">LOGICAL UNIT NOT SUPPORTED</span></span>                        |
| <span data-ttu-id="2639b-269">05</span><span class="sxs-lookup"><span data-stu-id="2639b-269">05</span></span>        | <span data-ttu-id="2639b-270">26</span><span class="sxs-lookup"><span data-stu-id="2639b-270">26</span></span>  | <span data-ttu-id="2639b-271">00</span><span class="sxs-lookup"><span data-stu-id="2639b-271">00</span></span>   | <span data-ttu-id="2639b-272">매개 변수 목록에 잘못된 필드 있음</span><span class="sxs-lookup"><span data-stu-id="2639b-272">INVALID FIELD IN PARAMETER LIST</span></span>                   |
| <span data-ttu-id="2639b-273">05</span><span class="sxs-lookup"><span data-stu-id="2639b-273">05</span></span>        | <span data-ttu-id="2639b-274">26</span><span class="sxs-lookup"><span data-stu-id="2639b-274">26</span></span>  | <span data-ttu-id="2639b-275">01</span><span class="sxs-lookup"><span data-stu-id="2639b-275">01</span></span>   | <span data-ttu-id="2639b-276">매개 변수가 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="2639b-276">PARAMETER NOT SUPPORTED</span></span>                           |
| <span data-ttu-id="2639b-277">05</span><span class="sxs-lookup"><span data-stu-id="2639b-277">05</span></span>        | <span data-ttu-id="2639b-278">26</span><span class="sxs-lookup"><span data-stu-id="2639b-278">26</span></span>  | <span data-ttu-id="2639b-279">02</span><span class="sxs-lookup"><span data-stu-id="2639b-279">02</span></span>   | <span data-ttu-id="2639b-280">매개 변수 값이 잘못됨</span><span class="sxs-lookup"><span data-stu-id="2639b-280">PARAMETER VALUE INVALID</span></span>                           |
| <span data-ttu-id="2639b-281">05</span><span class="sxs-lookup"><span data-stu-id="2639b-281">05</span></span>        | <span data-ttu-id="2639b-282">39</span><span class="sxs-lookup"><span data-stu-id="2639b-282">39</span></span>  | <span data-ttu-id="2639b-283">00</span><span class="sxs-lookup"><span data-stu-id="2639b-283">00</span></span>   | <span data-ttu-id="2639b-284">매개 변수를 저장할 수 없음</span><span class="sxs-lookup"><span data-stu-id="2639b-284">SAVING PARAMETERS NOT SUPPORT</span></span>                     |
| <span data-ttu-id="2639b-285">06</span><span class="sxs-lookup"><span data-stu-id="2639b-285">06</span></span>        | <span data-ttu-id="2639b-286">28</span><span class="sxs-lookup"><span data-stu-id="2639b-286">28</span></span>  | <span data-ttu-id="2639b-287">00</span><span class="sxs-lookup"><span data-stu-id="2639b-287">00</span></span>   | <span data-ttu-id="2639b-288">준비 안 됨에서 준비됨으로 전환 – 미디어 변경됨</span><span class="sxs-lookup"><span data-stu-id="2639b-288">NOT READY TO READY TRANSITION – MEDIA CHANGED</span></span>     |
| <span data-ttu-id="2639b-289">06</span><span class="sxs-lookup"><span data-stu-id="2639b-289">06</span></span>        | <span data-ttu-id="2639b-290">29</span><span class="sxs-lookup"><span data-stu-id="2639b-290">29</span></span>  | <span data-ttu-id="2639b-291">00</span><span class="sxs-lookup"><span data-stu-id="2639b-291">00</span></span>   | <span data-ttu-id="2639b-292">전원 켜기 초기화 또는 버스 디바이스 초기화 발생</span><span class="sxs-lookup"><span data-stu-id="2639b-292">POWER ON RESET OR BUS DEVICE RESET OCCURRED</span></span>       |
| <span data-ttu-id="2639b-293">06</span><span class="sxs-lookup"><span data-stu-id="2639b-293">06</span></span>        | <span data-ttu-id="2639b-294">2F</span><span class="sxs-lookup"><span data-stu-id="2639b-294">2F</span></span>  | <span data-ttu-id="2639b-295">00</span><span class="sxs-lookup"><span data-stu-id="2639b-295">00</span></span>   | <span data-ttu-id="2639b-296">다른 개시 장치가 명령을 지움</span><span class="sxs-lookup"><span data-stu-id="2639b-296">COMMANDS CLEARED BY ANOTHER INITIATOR</span></span>             |
| <span data-ttu-id="2639b-297">07</span><span class="sxs-lookup"><span data-stu-id="2639b-297">07</span></span>        | <span data-ttu-id="2639b-298">27</span><span class="sxs-lookup"><span data-stu-id="2639b-298">27</span></span>  | <span data-ttu-id="2639b-299">00</span><span class="sxs-lookup"><span data-stu-id="2639b-299">00</span></span>   | <span data-ttu-id="2639b-300">보호된 미디어에 쓰기</span><span class="sxs-lookup"><span data-stu-id="2639b-300">WRITE PROTECTED MEDIA</span></span>                             |
| <span data-ttu-id="2639b-301">0B</span><span class="sxs-lookup"><span data-stu-id="2639b-301">0B</span></span>        | <span data-ttu-id="2639b-302">4E</span><span class="sxs-lookup"><span data-stu-id="2639b-302">4E</span></span>  | <span data-ttu-id="2639b-303">00</span><span class="sxs-lookup"><span data-stu-id="2639b-303">00</span></span>   | <span data-ttu-id="2639b-304">겹친 명령을 시도함</span><span class="sxs-lookup"><span data-stu-id="2639b-304">OVERLAPPED COMMAND ATTEMPTED</span></span>                      |

<span data-ttu-id="2639b-305">애플리케이션에서 추가로 구현할 수 있는 두 가지 선택적 콜백은 **GET_STATUS_NOTIFICATION** 명령에 응답하기 위한 콜백과 **SYNCHRONIZE_CACHE** 명령에 응답하기 위한 콜백입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-305">There are two additional, optional callbacks the application may implement; one is for responding to a **GET_STATUS_NOTIFICATION** command and the other is for responding to the **SYNCHRONIZE_CACHE** command.</span></span>

<span data-ttu-id="2639b-306">호스트의 GET_STATUS_NOTIFICATION 명령을 처리하려는 애플리케이션은 다음 프로토타입으로 콜백을 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-306">If the application would like to handle the GET_STATUS_NOTIFICATION command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

<span data-ttu-id="2639b-307">위치:</span><span class="sxs-lookup"><span data-stu-id="2639b-307">Where:</span></span>

- <span data-ttu-id="2639b-308">*storage* 는 스토리지 클래스 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-308">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="2639b-309">*media_id* 는 현재 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-309">*media_id* is not currently used.</span></span> <span data-ttu-id="2639b-310">notification_class는 알림 클래스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-310">notification_class specifies the class of notification.</span></span>
- <span data-ttu-id="2639b-311">*media_notification* 은 애플리케이션에서 알림에 대한 응답을 포함하는 버퍼로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-311">*media_notification* should be set by the application to the buffer containing the response for the notification.</span></span>
- <span data-ttu-id="2639b-312">*media_notification_length* 는 애플리케이션에서 응답 버퍼의 길이를 포함하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-312">*media_notification_length* should be set by the application to contain the length of the response buffer.</span></span>

<span data-ttu-id="2639b-313">반환 값은 명령이 성공했는지 여부를 나타내며 **UX_SUCCESS** 또는 **UX_ERROR** 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-313">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

<span data-ttu-id="2639b-314">애플리케이션에서 이 콜백을 구현하지 않으면 **GET_STATUS_NOTIFICATION** 명령이 수신될 때 USBX에서 명령이 구현되지 않았다고 호스트에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-314">If the application does not implement this callback, then upon receiving the **GET_STATUS_NOTIFICATION** command, USBX will notify the host that the command is not implemented.</span></span>

<span data-ttu-id="2639b-315">애플리케이션에서 호스트의 쓰기에 캐시를 활용하는 경우 **SYNCHRONIZE_CACHE** 명령을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-315">The **SYNCHRONIZE_CACHE** command should be handled if the application is utilizing a cache for writes from the host.</span></span> <span data-ttu-id="2639b-316">이 명령은 스토리지 디바이스의 연결이 끊길 것을 알고 있는 호스트에서 보낼 수 있습니다. 예를 들어 Windows에서 도구 모음에 있는 플래시 드라이브 아이콘을 마우스 오른쪽 단추로 클릭하고 “\[스토리지 디바이스 이름\] 꺼내기”를 선택하면 Windows는 해당 디바이스에 **SYNCHRONIZE_CACHE** 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-316">A host may send this command if it knows the storage device is about to be disconnected, for example, in Windows, if you right click a flash drive icon in the toolbar and select "Eject \[storage device name\]", Windows will issue the **SYNCHRONIZE_CACHE** command to that device.</span></span>

<span data-ttu-id="2639b-317">호스트의 **GET_STATUS_NOTIFICATION** 명령을 처리하려는 애플리케이션은 다음 프로토타입으로 콜백을 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-317">If the application would like to handle the **GET_STATUS_NOTIFICATION** command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

<span data-ttu-id="2639b-318">위치:</span><span class="sxs-lookup"><span data-stu-id="2639b-318">Where:</span></span>

- <span data-ttu-id="2639b-319">*storage* 는 스토리지 클래스 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-319">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="2639b-320">*lun* 매개 변수는 명령이 전달되는 LUN을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-320">*lun* parameter specifies which LUN the command is directed to.</span></span>
- <span data-ttu-id="2639b-321">*number_blocks* 는 동기화할 블록 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-321">*number_blocks* specifies the number of blocks to synchronize.</span></span>
- <span data-ttu-id="2639b-322">*lba* 는 동기화할 첫 번째 블록의 섹터 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-322">*lba* is the sector address of the first block to synchronize.</span></span>
- <span data-ttu-id="2639b-323">*media_status* 는 미디어 상태 콜백 반환 값과 똑같이 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-323">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="2639b-324">반환 값은 명령이 성공했는지 여부를 나타내며 **UX_SUCCESS** 또는 **UX_ERROR** 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-324">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

### <a name="multiple-scsi-lun"></a><span data-ttu-id="2639b-325">여러 SCSI LUN</span><span class="sxs-lookup"><span data-stu-id="2639b-325">Multiple SCSI LUN</span></span>

<span data-ttu-id="2639b-326">USBX 디바이스 스토리지 클래스는 여러 LUN을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-326">The USBX device storage class supports multiple LUNs.</span></span> <span data-ttu-id="2639b-327">따라서 동시에 CD-ROM 및 플래시 디스크 역할을 하는 스토리지 디바이스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-327">It is therefore possible to create a storage device that acts as a CD-ROM and a Flash disk at the same time.</span></span> <span data-ttu-id="2639b-328">이 경우 초기화가 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-328">In such a case, the initialization would be slightly different.</span></span> <span data-ttu-id="2639b-329">플래시 디스크 및 CD-ROM의 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-329">Here is an example for a Flash Disk and CD-ROM:</span></span>

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

## <a name="usb-device-cdc-acm-class"></a><span data-ttu-id="2639b-330">USB 디바이스 CDC-ACM 클래스</span><span class="sxs-lookup"><span data-stu-id="2639b-330">USB Device CDC-ACM Class</span></span>

<span data-ttu-id="2639b-331">USB 디바이스 CDC-ACM 클래스를 사용하면 USB 호스트 시스템이 직렬 디바이스로 디바이스와 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-331">The USB device CDC-ACM class allows for a USB host system to communicate with the device as a serial device.</span></span> <span data-ttu-id="2639b-332">이 클래스는 USB 표준을 기반으로 하며 CDC 표준의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-332">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="2639b-333">디바이스 스택에서 CDC ACM 규격 디바이스 프레임워크를 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-333">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="2639b-334">아래에서 예제를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-334">An example is found here below.</span></span>

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

<span data-ttu-id="2639b-335">CDC-ACM 클래스는 복합 디바이스 프레임워크를 사용하여 인터페이스(제어 및 데이터)를 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-335">The CDC-ACM class uses a composite device framework to group interfaces (control and data).</span></span> <span data-ttu-id="2639b-336">따라서 디바이스 설명자를 정의할 때는 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-336">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="2639b-337">USBX는 IAD 설명자를 사용하여 내부적으로 인터페이스 바인딩 방법을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-337">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="2639b-338">IAD 설명자는 인터페이스 앞에 선언되어야 하며, CDC-ACM 클래스의 첫 번째 인터페이스 및 연결된 인터페이스 수를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-338">The IAD descriptor should be declared before the interfaces and contain the first interface of the CDC-ACM class and how many interfaces are attached.</span></span>

<span data-ttu-id="2639b-339">CDC-ACM 클래스는 최신 IAD 설명자와 동일한 기능을 수행하는 통합 기능 설명자도 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-339">The CDC-ACM class also uses a union functional descriptor which performs the same function as the newer IAD descriptor.</span></span> <span data-ttu-id="2639b-340">통합 기능 설명자는 기록 및 호스트 쪽과의 호환성을 위해 선언되어야 하지만 USBX에서 사용되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-340">Although a Union Functional descriptor must be declared for historical reasons and compatibility with the host side, it is not used by USBX.</span></span>

<span data-ttu-id="2639b-341">CDC-ACM 클래스의 초기화에는 다음 매개 변수가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-341">The initialization of the CDC-ACM class expects the following parameters.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

<span data-ttu-id="2639b-342">정의된 매개 변수 2개는 스택에서 이 클래스를 활성화하거나 비활성화할 때 호출되는 사용자 애플리케이션에 대한 콜백 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-342">The 2 parameters defined are callback pointers into the user applications that will be called when the stack activates or deactivate this class.</span></span>

<span data-ttu-id="2639b-343">정의된 세 번째 매개 변수는 회선 코딩 또는 회선 상태 매개 변수 변경이 있을 때 호출되는 사용자 애플리케이션에 대한 콜백 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-343">The third parameter defined is a callback pointer to the user application that will be called when there is line coding or line states parameter change.</span></span> <span data-ttu-id="2639b-344">예를 들어 DTR 상태를 **TRUE** 로 변경하라는 호스트의 요청이 있을 경우 콜백이 호출되고, 콜백에서 사용자 애플리케이션은 IOCTL 함수를 통해 회선 상태를 검사하여 호스트가 통신할 준비가 되었음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-344">E.g., when there is request from host to change DTR state to **TRUE**, the callback is invoked, in it user application can check line states through IOCTL function to kow host is ready for communication.</span></span>

<span data-ttu-id="2639b-345">CDC-ACM은 USB-IF 표준을 기반으로 하며 macOS 및 Linux 운영 체제에서 자동으로 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-345">The CDC-ACM is based on a USB-IF standard and is automatically recognized by MACOs and Linux operating systems.</span></span> <span data-ttu-id="2639b-346">Windows 10 이전 버전의 Windows 플랫폼에서 이 클래스를 사용하려면 .inf 파일이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-346">On Windows platforms, this class requires a .inf file for Windows version prior to 10.</span></span> <span data-ttu-id="2639b-347">Windows 10에서는 .inf 파일이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-347">Windows 10 does not require any .inf files.</span></span> <span data-ttu-id="2639b-348">CDC-ACM 클래스용 템플릿이 제공되며 ***usbx_windows_host_files*** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-348">We supply a template for the CDC-ACM class and it can be found in the ***usbx_windows_host_files*** directory.</span></span> <span data-ttu-id="2639b-349">최신 버전의 Windows에서는 CDC_ACM_Template_Win7_64bit.inf 파일을 사용해야 합니다(Win10 제외).</span><span class="sxs-lookup"><span data-stu-id="2639b-349">For more recent version of Windows the file CDC_ACM_Template_Win7_64bit.inf should be used (except Win10).</span></span> <span data-ttu-id="2639b-350">디바이스에서 사용하는 PID/VID에 맞게 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-350">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="2639b-351">회사와 제품이 USB-IF를 사용하여 등록된 경우 PID/VID는 최종 고객에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-351">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="2639b-352">Inf 파일에서 수정할 필드는 아래에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-352">In the inf file, the fields to modify are located here.</span></span>

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

<span data-ttu-id="2639b-353">CDC-ACM 디바이스의 디바이스 프레임워크에서 PID/VID는 디바이스 설명자에 저장됩니다(위에서 선언한 디바이스 설명자 참조).</span><span class="sxs-lookup"><span data-stu-id="2639b-353">In the device framework of the CDC-ACM device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="2639b-354">USB CDC-ACM 디바이스가 검색되면 USB 호스트 시스템에서 직렬 클래스를 탑재하며, 모든 직렬 터미널 프로그램으로 디바이스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-354">When a USB host systems discovers the USB CDC-ACM device, it will mount a serial class and the device can be used with any serial terminal program.</span></span> <span data-ttu-id="2639b-355">호스트 운영 체제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2639b-355">See the host Operating System for reference.</span></span>

<span data-ttu-id="2639b-356">CDC-ACM 클래스 API 함수는 아래에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-356">The CDC-ACM class API functions are defined below.</span></span>

### <a name="ux_device_class_cdc_acm_ioctl"></a><span data-ttu-id="2639b-357">ux_device_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="2639b-357">ux_device_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="2639b-358">CDC-ACM 인터페이스에서 IOCTL 수행</span><span class="sxs-lookup"><span data-stu-id="2639b-358">Perform IOCTL on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2639b-359">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-359">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="2639b-360">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-360">Description</span></span>

<span data-ttu-id="2639b-361">이 함수는 애플리케이션에서 CDC ACM 인터페이스에 대해 다양한 IOCTL 호출을 수행해야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-361">This function is called when an application needs to perform various ioctl calls to the cdc acm interface</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-362">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-362">Parameters</span></span>

- <span data-ttu-id="2639b-363">**cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-363">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="2639b-364">**ioctl_function**: 수행할 IOCTL 함수</span><span class="sxs-lookup"><span data-stu-id="2639b-364">**ioctl_function**: Ioctl function to be performed.</span></span>
- <span data-ttu-id="2639b-365">**parameter**: IOCTL 호출과 관련된 매개 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-365">**parameter**: Pointer to a parameter specific to the ioctl call.</span></span>

### <a name="return-value"></a><span data-ttu-id="2639b-366">반환 값</span><span class="sxs-lookup"><span data-stu-id="2639b-366">Return Value</span></span>

- <span data-ttu-id="2639b-367">**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-367">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="2639b-368">**UX_ERROR**(0xff) 함수에서 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-368">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="2639b-369">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-369">Example</span></span>

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a><span data-ttu-id="2639b-370">IOCTL 함수:</span><span class="sxs-lookup"><span data-stu-id="2639b-370">Ioctl functions:</span></span>

| <span data-ttu-id="2639b-371">기능</span><span class="sxs-lookup"><span data-stu-id="2639b-371">Function</span></span>                                        | <span data-ttu-id="2639b-372">값</span><span class="sxs-lookup"><span data-stu-id="2639b-372">Value</span></span> |
| ----------------------------------------------- | - |
| <span data-ttu-id="2639b-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="2639b-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>    | <span data-ttu-id="2639b-374">1</span><span class="sxs-lookup"><span data-stu-id="2639b-374">1</span></span> |
| <span data-ttu-id="2639b-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="2639b-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>    | <span data-ttu-id="2639b-376">2</span><span class="sxs-lookup"><span data-stu-id="2639b-376">2</span></span> |
| <span data-ttu-id="2639b-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="2639b-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>     | <span data-ttu-id="2639b-378">3</span><span class="sxs-lookup"><span data-stu-id="2639b-378">3</span></span> |
| <span data-ttu-id="2639b-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="2639b-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>         | <span data-ttu-id="2639b-380">4</span><span class="sxs-lookup"><span data-stu-id="2639b-380">4</span></span> |
| <span data-ttu-id="2639b-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="2639b-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>     | <span data-ttu-id="2639b-382">5</span><span class="sxs-lookup"><span data-stu-id="2639b-382">5</span></span> |
| <span data-ttu-id="2639b-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="2639b-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span> | <span data-ttu-id="2639b-384">6</span><span class="sxs-lookup"><span data-stu-id="2639b-384">6</span></span> |
| <span data-ttu-id="2639b-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="2639b-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>  | <span data-ttu-id="2639b-386">7</span><span class="sxs-lookup"><span data-stu-id="2639b-386">7</span></span> |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="2639b-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="2639b-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>

<span data-ttu-id="2639b-388">CDC-ACM 인터페이스에서 IOCTL 회선 코딩 설정 수행</span><span class="sxs-lookup"><span data-stu-id="2639b-388">Perform IOCTL Set Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2639b-389">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-389">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="2639b-390">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-390">Description</span></span>

<span data-ttu-id="2639b-391">이 함수는 애플리케이션에서 회선 코딩 매개 변수를 설정해야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-391">This function is called when an application needs to Set the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-392">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-392">Parameters</span></span>

- <span data-ttu-id="2639b-393">**cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-393">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="2639b-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="2639b-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="2639b-395">**parameter**: 회선 매개 변수 구조체에 대한 포인터:</span><span class="sxs-lookup"><span data-stu-id="2639b-395">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="2639b-396">반환 값</span><span class="sxs-lookup"><span data-stu-id="2639b-396">Return Value</span></span>

<span data-ttu-id="2639b-397">**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-397">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="2639b-398">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-398">Example</span></span>

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="2639b-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="2639b-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>

<span data-ttu-id="2639b-400">CDC-ACM 인터페이스에서 IOCTL 회선 코딩 가져오기 수행</span><span class="sxs-lookup"><span data-stu-id="2639b-400">Perform IOCTL Get Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2639b-401">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-401">Prototype</span></span>

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="2639b-402">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-402">Description</span></span>

<span data-ttu-id="2639b-403">이 함수는 애플리케이션에서 회선 코딩 매개 변수를 가져와야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-403">This function is called when an application needs to Get the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-404">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-404">Parameters</span></span>

- <span data-ttu-id="2639b-405">**cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-405">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="2639b-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="2639b-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING</span></span>
- <span data-ttu-id="2639b-407">**parameter**: 회선 매개 변수 구조체에 대한 포인터:</span><span class="sxs-lookup"><span data-stu-id="2639b-407">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="2639b-408">반환 값</span><span class="sxs-lookup"><span data-stu-id="2639b-408">Return Value</span></span>

- <span data-ttu-id="2639b-409">**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-409">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="2639b-410">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-410">Example</span></span>

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a><span data-ttu-id="2639b-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="2639b-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>

<span data-ttu-id="2639b-412">CDC-ACM 인터페이스에서 IOCTL 회선 상태 가져오기 수행</span><span class="sxs-lookup"><span data-stu-id="2639b-412">Perform IOCTL Get Line State on the CDC-ACM interface</span></span>

## <a name="prototype"></a><span data-ttu-id="2639b-413">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-413">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="2639b-414">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-414">Description</span></span>

<span data-ttu-id="2639b-415">이 함수는 애플리케이션에서 회선 상태 매개 변수를 가져와야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-415">This function is called when an application needs to Get the Line State parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-416">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-416">Parameters</span></span>

- <span data-ttu-id="2639b-417">**cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-417">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="2639b-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="2639b-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>
- <span data-ttu-id="2639b-419">**parameter**: 회선 매개 변수 구조체에 대한 포인터:</span><span class="sxs-lookup"><span data-stu-id="2639b-419">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="2639b-420">반환 값</span><span class="sxs-lookup"><span data-stu-id="2639b-420">Return Value</span></span>

- <span data-ttu-id="2639b-421">**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-421">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="2639b-422">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-422">Example</span></span>

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="2639b-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="2639b-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>

<span data-ttu-id="2639b-424">CDC-ACM 인터페이스에서 IOCTL 회선 상태 설정 수행</span><span class="sxs-lookup"><span data-stu-id="2639b-424">Perform IOCTL Set Line State on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2639b-425">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-425">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="2639b-426">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-426">Description</span></span>

<span data-ttu-id="2639b-427">이 함수는 애플리케이션에서 회선 상태 매개 변수를 설정해야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-427">This function is called when an application needs to Get the Line State parameters</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-428">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-428">Parameters</span></span>

- <span data-ttu-id="2639b-429">**cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-429">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="2639b-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="2639b-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="2639b-431">**parameter**: 회선 매개 변수 구조체에 대한 포인터:</span><span class="sxs-lookup"><span data-stu-id="2639b-431">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="2639b-432">반환 값</span><span class="sxs-lookup"><span data-stu-id="2639b-432">Return Value</span></span>

- <span data-ttu-id="2639b-433">**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-433">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="2639b-434">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-434">Example</span></span>

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a><span data-ttu-id="2639b-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="2639b-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>

<span data-ttu-id="2639b-436">CDC-ACM 인터페이스에서 IOCTL 파이프 중단 수행</span><span class="sxs-lookup"><span data-stu-id="2639b-436">Perform IOCTL ABORT PIPE on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2639b-437">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-437">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="2639b-438">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-438">Description</span></span>

<span data-ttu-id="2639b-439">이 함수는 애플리케이션에서 파이프를 중단해야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-439">This function is called when an application needs to abort a pipe.</span></span> <span data-ttu-id="2639b-440">예를 들어 진행 중인 쓰기를 중단하려면 UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT를 매개 변수로 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-440">For example, to abort an ongoing write, UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT should be passed as the parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-441">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-441">Parameters</span></span>

- <span data-ttu-id="2639b-442">**cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-442">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="2639b-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="2639b-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>
- <span data-ttu-id="2639b-444">**parameter**: 파이프 방향:</span><span class="sxs-lookup"><span data-stu-id="2639b-444">**parameter**: The pipe direction:</span></span>

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a><span data-ttu-id="2639b-445">반환 값</span><span class="sxs-lookup"><span data-stu-id="2639b-445">Return Value</span></span>

- <span data-ttu-id="2639b-446">**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-446">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="2639b-447">**UX_ENDPOINT_HANDLE_UNKNOWN**(0x53) 파이프 방향이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Invalid pipe direction.</span></span>

### <a name="example"></a><span data-ttu-id="2639b-448">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-448">Example</span></span>

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a><span data-ttu-id="2639b-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="2639b-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>

<span data-ttu-id="2639b-450">CDC-ACM 인터페이스에서 IOCTL 전송 시작 수행</span><span class="sxs-lookup"><span data-stu-id="2639b-450">Perform IOCTL Transmission Start on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2639b-451">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-451">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="2639b-452">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-452">Description</span></span>

<span data-ttu-id="2639b-453">이 함수는 애플리케이션에서 콜백으로 전송을 사용하려는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-453">This function is called when an application wants to use transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-454">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-454">Parameters</span></span>

- <span data-ttu-id="2639b-455">**cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-455">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="2639b-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="2639b-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>
- <span data-ttu-id="2639b-457">**parameter**: 전송 시작 매개 변수 구조체에 대한 포인터:</span><span class="sxs-lookup"><span data-stu-id="2639b-457">**parameter**: Pointer to the Start Transmission parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="2639b-458">반환 값</span><span class="sxs-lookup"><span data-stu-id="2639b-458">Return Value</span></span>

- <span data-ttu-id="2639b-459">**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-459">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="2639b-460">**UX_ERROR**(0xff) 전송이 이미 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-460">**UX_ERROR** (0xFF) Transmission already started.</span></span>
- <span data-ttu-id="2639b-461">**UX_MEMORY_INSUFFICIENT**(0x12) 메모리를 할당하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-461">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="2639b-462">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-462">Example</span></span>

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a><span data-ttu-id="2639b-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="2639b-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>

<span data-ttu-id="2639b-464">CDC-ACM 인터페이스에서 IOCTL 전송 중지 수행</span><span class="sxs-lookup"><span data-stu-id="2639b-464">Perform IOCTL Transmission Stop on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2639b-465">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-465">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="2639b-466">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-466">Description</span></span>

<span data-ttu-id="2639b-467">이 함수는 애플리케이션에서 콜백으로 전송 사용을 중지하려는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-467">This function is called when an application wants to stop using transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-468">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-468">Parameters</span></span>

- <span data-ttu-id="2639b-469">**cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-469">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="2639b-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span><span class="sxs-lookup"><span data-stu-id="2639b-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span></span>
- <span data-ttu-id="2639b-471">**parameter**: 사용되지 않음</span><span class="sxs-lookup"><span data-stu-id="2639b-471">**parameter**: Not used</span></span>

### <a name="return-value"></a><span data-ttu-id="2639b-472">반환 값</span><span class="sxs-lookup"><span data-stu-id="2639b-472">Return Value</span></span>

- <span data-ttu-id="2639b-473">**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-473">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="2639b-474">**UX_ERROR**(0xff) 진행 중인 전송이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-474">**UX_ERROR** (0xFF) No ongoing transmission.</span></span>

### <a name="example"></a><span data-ttu-id="2639b-475">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-475">Example</span></span>

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a><span data-ttu-id="2639b-476">ux_device_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="2639b-476">ux_device_class_cdc_acm_read</span></span>

<span data-ttu-id="2639b-477">CDC-ACM 파이프에서 읽기</span><span class="sxs-lookup"><span data-stu-id="2639b-477">Read from CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="2639b-478">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-478">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="2639b-479">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-479">Description</span></span>

<span data-ttu-id="2639b-480">이 함수는 애플리케이션에서 OUT 데이터 파이프(호스트에서는 OUT, 디바이스에서는 IN)를 읽어야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-480">This function is called when an application needs to read from the OUT data pipe (OUT from the host, IN from the device).</span></span> <span data-ttu-id="2639b-481">차단형 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-481">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-482">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-482">Parameters</span></span>

- <span data-ttu-id="2639b-483">**cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-483">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="2639b-484">**buffer**: 데이터가 저장되는 버퍼 주소</span><span class="sxs-lookup"><span data-stu-id="2639b-484">**buffer**: Buffer address where data will be stored.</span></span>
- <span data-ttu-id="2639b-485">**requested_length**: 필요한 최대 길이</span><span class="sxs-lookup"><span data-stu-id="2639b-485">**requested_length**: The maximum length we expect.</span></span>
- <span data-ttu-id="2639b-486">**actual_length**: 버퍼로 반환되는 길이</span><span class="sxs-lookup"><span data-stu-id="2639b-486">**actual_length**: The length returned into the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="2639b-487">반환 값</span><span class="sxs-lookup"><span data-stu-id="2639b-487">Return Value</span></span>

- <span data-ttu-id="2639b-488">**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-488">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="2639b-489">**UX_CONFIGURATION_HANDLE_UNKNOWN**(0x51) 디바이스가 더 이상 구성된 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-489">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="2639b-490">**UX_TRANSFER_NO_ANSWER**(0x22) 디바이스에서 응답이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-490">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="2639b-491">전송이 보류된 동안 디바이스 연결이 끊긴 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-491">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="2639b-492">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-492">Example</span></span>

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a><span data-ttu-id="2639b-493">ux_device_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="2639b-493">ux_device_class_cdc_acm_write</span></span>

<span data-ttu-id="2639b-494">CDC-ACM 파이프에 쓰기</span><span class="sxs-lookup"><span data-stu-id="2639b-494">Write to a CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="2639b-495">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-495">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="2639b-496">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-496">Description</span></span>

<span data-ttu-id="2639b-497">이 함수는 애플리케이션에서 IN 데이터 파이프(호스트에서는 IN, 디바이스에서는 OUT)에 써야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-497">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="2639b-498">차단형 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-498">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-499">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-499">Parameters</span></span>

- <span data-ttu-id="2639b-500">**cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-500">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="2639b-501">**buffer**: 데이터가 저장된 버퍼 주소</span><span class="sxs-lookup"><span data-stu-id="2639b-501">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="2639b-502">**requested_length**: 쓸 버퍼의 길이</span><span class="sxs-lookup"><span data-stu-id="2639b-502">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="2639b-503">**actual_length**: 쓰기를 수행한 후 버퍼로 반환되는 길이</span><span class="sxs-lookup"><span data-stu-id="2639b-503">**actual_length**: The length returned into the buffer after write is performed.</span></span>

### <a name="return-value"></a><span data-ttu-id="2639b-504">반환 값</span><span class="sxs-lookup"><span data-stu-id="2639b-504">Return Value</span></span>
- <span data-ttu-id="2639b-505">**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-505">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="2639b-506">**UX_CONFIGURATION_HANDLE_UNKNOWN**(0x51) 디바이스가 더 이상 구성된 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-506">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="2639b-507">**UX_TRANSFER_NO_ANSWER**(0x22) 디바이스에서 응답이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-507">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="2639b-508">전송이 보류된 동안 디바이스 연결이 끊긴 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-508">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="2639b-509">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-509">Example</span></span>

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a><span data-ttu-id="2639b-510">ux_device_class_cdc_acm_write_with_callback</span><span class="sxs-lookup"><span data-stu-id="2639b-510">ux_device_class_cdc_acm_write_with_callback</span></span>

<span data-ttu-id="2639b-511">콜백으로 CDC-ACM 파이프에 쓰기</span><span class="sxs-lookup"><span data-stu-id="2639b-511">Writing to a CDC-ACM pipe with callback</span></span>

### <a name="prototype"></a><span data-ttu-id="2639b-512">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-512">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a><span data-ttu-id="2639b-513">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-513">Description</span></span>

<span data-ttu-id="2639b-514">이 함수는 애플리케이션에서 IN 데이터 파이프(호스트에서는 IN, 디바이스에서는 OUT)에 써야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-514">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="2639b-515">비차단형 함수로, UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START에서 설정된 콜백을 통해 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-515">This function is non-blocking and the completion will be done through a callback set in UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-516">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-516">Parameters</span></span>

- <span data-ttu-id="2639b-517">**cdc_acm**: CDC 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-517">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="2639b-518">**buffer**: 데이터가 저장된 버퍼 주소</span><span class="sxs-lookup"><span data-stu-id="2639b-518">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="2639b-519">**requested_length**: 쓸 버퍼의 길이</span><span class="sxs-lookup"><span data-stu-id="2639b-519">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="2639b-520">**actual_length**: 쓰기를 수행한 후 버퍼로 반환되는 길이</span><span class="sxs-lookup"><span data-stu-id="2639b-520">**actual_length**: The length returned into the buffer after write is performed</span></span>

### <a name="return-value"></a><span data-ttu-id="2639b-521">반환 값</span><span class="sxs-lookup"><span data-stu-id="2639b-521">Return Value</span></span>

- <span data-ttu-id="2639b-522">**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-522">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="2639b-523">**UX_CONFIGURATION_HANDLE_UNKNOWN**(0x51) 디바이스가 더 이상 구성된 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-523">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="2639b-524">**UX_TRANSFER_NO_ANSWER**(0x22) 디바이스에서 응답이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-524">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="2639b-525">전송이 보류된 동안 디바이스 연결이 끊긴 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-525">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="2639b-526">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-526">Example</span></span>

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a><span data-ttu-id="2639b-527">USB 디바이스 CDC-ECM 클래스</span><span class="sxs-lookup"><span data-stu-id="2639b-527">USB Device CDC-ECM Class</span></span>

<span data-ttu-id="2639b-528">USB 디바이스 CDC-ECM 클래스를 사용하면 USB 호스트 시스템이 이더넷 디바이스로 디바이스와 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-528">The USB device CDC-ECM class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="2639b-529">이 클래스는 USB 표준을 기반으로 하며 CDC 표준의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-529">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="2639b-530">디바이스 스택에서 CDC ACM 규격 디바이스 프레임워크를 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-530">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="2639b-531">아래에서 예제를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-531">An example is found here below.</span></span>

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

<span data-ttu-id="2639b-532">CDC-ECM 클래스는 CDC-ACM과 매우 유사한 디바이스 설명자 방법을 사용하며 IAD 설명자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-532">The CDC-ECM class uses a very similar device descriptor approach to the CDC-ACM and also requires an IAD descriptor.</span></span> <span data-ttu-id="2639b-533">정의는 CDC-ACM 클래스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2639b-533">See the CDC-ACM class for definition.</span></span>

<span data-ttu-id="2639b-534">CDC-ECM에는 기본 디바이스 프레임워크 외에도 특수 문자열 설명자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-534">In addition to the regular device framework, the CDC-ECM requires special string descriptors.</span></span> <span data-ttu-id="2639b-535">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-535">An example is given below.</span></span>

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

<span data-ttu-id="2639b-536">CDC-ECM 클래스는 MAC 주소 문자열 설명자를 사용하여 TCP/IP 프로토콜에서 디바이스가 응답하는 MAC 주소에 대한 호스트 쿼리에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-536">The MAC address string descriptor is used by the CDC-ECM class to reply to the host queries as to what MAC address the device is answering to at the TCP/IP protocol.</span></span> <span data-ttu-id="2639b-537">선택한 디바이스에 설명자를 설정할 수 있지만 여기서 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-537">It can be set to the device choice but must be defined here.</span></span>

<span data-ttu-id="2639b-538">CDC-ECM 클래스의 초기화는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-538">The initialization of the CDC-ECM class is as follows.</span></span>

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

<span data-ttu-id="2639b-539">이 클래스를 초기화하려면 활성화와 비활성화에 동일한 함수 콜백을 사용해야 합니다. 단, 예제에서는 연습 삼아 콜백이 수행되지 않도록 NULL로 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-539">The initialization of this class expects the same function callback for activation and deactivation, although here as an exercise they are set to NULL so that no callback is performed.</span></span>

<span data-ttu-id="2639b-540">다음 매개 변수는 노드 ID 정의의 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-540">The next parameters are for the definition of the node IDs.</span></span> <span data-ttu-id="2639b-541">CDC-ECM에는 두 가지 노드인 로컬 노드와 원격 노드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-541">2 Nodes are necessary for the CDC-ECM, a local node and a remote node.</span></span> <span data-ttu-id="2639b-542">로컬 노드는 디바이스의 MAC 주소를 지정하는 반면 원격 노드는 호스트의 MAC 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-542">The local node specifies the MAC address of the device, while the remote node specifies the MAC address of the host.</span></span> <span data-ttu-id="2639b-543">원격 노드는 디바이스 프레임워크 문자열 설명자에서 선언된 노드와 동일한 노드여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-543">The remote node must be the same one as the one declared in the device framework string descriptor.</span></span>

<span data-ttu-id="2639b-544">CDC-ECM 클래스에는 두 방법 모두로 데이터를 전송할 수 있는 기본 제공 API가 있지만 사용자 애플리케이션이 NetX를 통해 USB 이더넷 디바이스와 통신하기 때문에 해당 API는 애플리케이션에서 숨겨져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-544">The CDC-ECM class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="2639b-545">USBX CDC-ECM 클래스는 Azure RTOS NetX 네트워크 스택에 긴밀히 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-545">The USBX CDC-ECM class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="2639b-546">NetX 및 USBX CDC-ECM 클래스를 모두 사용하는 애플리케이션은 일반적인 방식으로 NetX 네트워크 스택을 활성화하지만 USB 네트워크 스택도 다음과 같이 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-546">An application using both NetX and USBX CDC-ECM class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="2639b-547">USB 네트워크 스택은 한 번만 활성화하면 되며 CDCECM에 국한되지 않고 NetX 서비스를 필요로 하는 모든 USB 클래스에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-547">The USB network stack needs to be activated only once and is not specific to CDCECM but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="2639b-548">CDC-ECM 클래스는 MAC OS 및 Linux 호스트에서 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-548">The CDC-ECM class will be recognized by MAC OS and Linux hosts.</span></span> <span data-ttu-id="2639b-549">그러나 CDC-ECM을 기본적으로 인식할 수 있도록 Microsoft Windows에서 제공하는 드라이버는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-549">But there is no driver supplied by Microsoft Windows to recognize CDC-ECM natively.</span></span> <span data-ttu-id="2639b-550">Windows 플랫폼용 상용 제품이 있으며 자체 .inf 파일을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-550">Some commercial products do exist for Windows platforms and they supply their own .inf file.</span></span> <span data-ttu-id="2639b-551">CDC-ACM inf 템플릿과 동일한 방식으로 USB 네트워크 디바이스의 PID/VID와 일치하도록 파일을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-551">This file will need to be modified the same way as the CDC-ACM inf template to match the PID/VID of the USB network device.</span></span>

## <a name="usb-device-hid-class"></a><span data-ttu-id="2639b-552">USB 디바이스 HID 클래스</span><span class="sxs-lookup"><span data-stu-id="2639b-552">USB Device HID Class</span></span>

<span data-ttu-id="2639b-553">USB 디바이스 HID 클래스를 사용하면 USB 호스트 시스템에서 특정 HID 클라이언트 기능이 있는 HID 디바이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-553">The USB device HID class allows for a USB host system to connect to a HID device with specific HID client capabilities.</span></span>

<span data-ttu-id="2639b-554">USBX HID 디바이스 클래스는 호스트 쪽에 비해 비교적 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-554">USBX HID device class is relatively simple compared to the host side.</span></span> <span data-ttu-id="2639b-555">디바이스 및 해당 HID 설명자의 동작에 긴밀히 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-555">It is closely tied to the behavior of the device and its HID descriptor.</span></span>

<span data-ttu-id="2639b-556">모든 HID 클라이언트에서 먼저 HID 디바이스 프레임워크를 아래 예제와 같이 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-556">Any HID client requires first to define a HID device framework as the example below.</span></span>

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

<span data-ttu-id="2639b-557">HID 프레임워크에는 HID 클래스 및 HID 디바이스 서브클래스를 설명하는 인터페이스 설명자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-557">The HID framework contains an interface descriptor that describes the HID class and the HID device subclass.</span></span> <span data-ttu-id="2639b-558">HID 인터페이스는 독립 실행형 클래스이거나 복합 디바이스의 일부일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-558">The HID interface can be a standalone class or part of a composite device.</span></span>

<span data-ttu-id="2639b-559">현재 대부분의 애플리케이션에서 하나의 ID(ID 0)만 필요하므로 USBX HID 클래스는 여러 보고서 ID를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-559">Currently, the USBX HID class does not support multiple report IDs, as most applications only require one ID (ID zero).</span></span> <span data-ttu-id="2639b-560">관심 있는 기능이 여러 보고서 ID인 경우 Microsoft에 문의하시기 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-560">If multiple report IDs is a feature you are interested in, please contact us.</span></span>

<span data-ttu-id="2639b-561">일례로 USB 키보드를 사용한 HID 클래스의 초기화는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-561">The initialization of the HID class is as follow, using a USB keyboard as an example.</span></span>

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

<span data-ttu-id="2639b-562">애플리케이션에서 HID 보고서 설명자와 해당 길이를 HID 클래스에 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-562">The application needs to pass to the HID class a HID report descriptor and its length.</span></span> <span data-ttu-id="2639b-563">보고서 설명자는 디바이스를 설명하는 항목의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-563">The report descriptor is a collection of items that describe the device.</span></span> <span data-ttu-id="2639b-564">HID 문법에 대한 자세한 내용은 HID USB 클래스 사양을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2639b-564">For more information on the HID grammar refer to the HID USB class specification.</span></span>

<span data-ttu-id="2639b-565">보고서 설명자 외에도 애플리케이션은 HID 이벤트가 발생할 경우 콜백을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-565">In addition to the report descriptor, the application passes a call back when a HID event happens.</span></span>

<span data-ttu-id="2639b-566">USBX HID 클래스는 다음과 같은 호스트의 표준 HID 명령을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-566">The USBX HID class supports the following standard HID commands from the host.</span></span>

| <span data-ttu-id="2639b-567">명령 이름</span><span class="sxs-lookup"><span data-stu-id="2639b-567">Command name</span></span>                             | <span data-ttu-id="2639b-568">값</span><span class="sxs-lookup"><span data-stu-id="2639b-568">Value</span></span> | <span data-ttu-id="2639b-569">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-569">Description</span></span>                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| <span data-ttu-id="2639b-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span><span class="sxs-lookup"><span data-stu-id="2639b-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span></span>   | <span data-ttu-id="2639b-571">0x01</span><span class="sxs-lookup"><span data-stu-id="2639b-571">0x01</span></span>  | <span data-ttu-id="2639b-572">디바이스에서 보고서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-572">Get a report from the device</span></span>                     |
| <span data-ttu-id="2639b-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span><span class="sxs-lookup"><span data-stu-id="2639b-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span></span>     | <span data-ttu-id="2639b-574">0x02</span><span class="sxs-lookup"><span data-stu-id="2639b-574">0x02</span></span>  | <span data-ttu-id="2639b-575">인터럽트 엔드포인트의 유휴 주파수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-575">Get the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="2639b-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="2639b-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span></span> | <span data-ttu-id="2639b-577">0x03</span><span class="sxs-lookup"><span data-stu-id="2639b-577">0x03</span></span>  | <span data-ttu-id="2639b-578">디바이스에서 실행 중인 프로토콜을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-578">Get the protocol running on the device</span></span>           |
| <span data-ttu-id="2639b-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span><span class="sxs-lookup"><span data-stu-id="2639b-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span></span>   | <span data-ttu-id="2639b-580">0x09</span><span class="sxs-lookup"><span data-stu-id="2639b-580">0x09</span></span>  | <span data-ttu-id="2639b-581">디바이스에 보고서를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-581">Set a report to the device</span></span>                       |
| <span data-ttu-id="2639b-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span><span class="sxs-lookup"><span data-stu-id="2639b-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span></span>     | <span data-ttu-id="2639b-583">0x0a</span><span class="sxs-lookup"><span data-stu-id="2639b-583">0x0a</span></span>  | <span data-ttu-id="2639b-584">인터럽트 엔드포인트의 유휴 주파수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-584">Set the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="2639b-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="2639b-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span></span> | <span data-ttu-id="2639b-586">0x0b</span><span class="sxs-lookup"><span data-stu-id="2639b-586">0x0b</span></span>  | <span data-ttu-id="2639b-587">디바이스에서 실행 중인 프로토콜을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-587">Get the protocol running on the device</span></span>           |

<span data-ttu-id="2639b-588">보고서 가져오기 및 설정은 HID에서 호스트와 디바이스 간 데이터 전송을 위해 가장 일반적으로 사용되는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-588">The Get and Set report are the most commonly used commands by HID to transfer data back and forth between the host and the device.</span></span> <span data-ttu-id="2639b-589">대체로 호스트는 제어 엔드포인트에서 데이터를 보내지만 인터럽트 엔드포인트에서 데이터를 받거나 제어 엔드포인트의 데이터를 가져오도록 GET_REPORT 명령을 실행하여 데이터를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-589">Most commonly the host sends data on the control endpoint but can receive data either on the interrupt endpoint or by issuing a GET_REPORT command to fetch the data on the control endpoint.</span></span>

<span data-ttu-id="2639b-590">HID 클래스는 ux_device_class_hid_event_set 함수를 사용하여 데이터를 다시 인터럽트 엔드포인트의 호스트에 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-590">The HID class can send data back to the host on the interrupt endpoint by using the ux_device_class_hid_event_set function.</span></span>

### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="2639b-591">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="2639b-591">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="2639b-592">HID 클래스에 이벤트 설정</span><span class="sxs-lookup"><span data-stu-id="2639b-592">Setting an event to the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="2639b-593">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-593">Prototype</span></span>

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="2639b-594">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-594">Description</span></span>

<span data-ttu-id="2639b-595">이 함수는 애플리케이션에서 HID 이벤트를 다시 호스트에 보내야 하는 경우에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-595">This function is called when an application needs to send a HID event back to the host.</span></span> <span data-ttu-id="2639b-596">비차단형 함수로, 단지 보고서를 순환 큐에 넣고 애플리케이션에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-596">The function is not blocking, it merely puts the report into a circular queue and returns to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-597">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-597">Parameters</span></span>

- <span data-ttu-id="2639b-598">**hid**: HID 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-598">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="2639b-599">**hid_event**: HID 이벤트 구조체에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-599">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="return-value"></a><span data-ttu-id="2639b-600">반환 값</span><span class="sxs-lookup"><span data-stu-id="2639b-600">Return Value</span></span>

- <span data-ttu-id="2639b-601">**UX_SUCCESS**(0x00) 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-601">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="2639b-602">**UX_ERROR**(0xff) 오류가 발생했습니다. 순환 큐에 사용할 수 있는 공간이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-602">**UX_ERROR** (0xFF) Error no space available in circular queue.</span></span>

### <a name="example"></a><span data-ttu-id="2639b-603">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-603">Example</span></span>

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

<span data-ttu-id="2639b-604">HID 클래스를 초기화할 때 정의된 콜백은 이벤트 전송과 반대로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-604">The callback defined at the initialization of the HID class performs the opposite of sending an event.</span></span> <span data-ttu-id="2639b-605">호스트에서 보낸 이벤트를 입력으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-605">It gets as input the event sent by the host.</span></span> <span data-ttu-id="2639b-606">콜백의 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-606">The prototype of the callback is as follows.</span></span>

### <a name="hid_callback"></a><span data-ttu-id="2639b-607">hid_callback</span><span class="sxs-lookup"><span data-stu-id="2639b-607">hid_callback</span></span>

<span data-ttu-id="2639b-608">HID 클래스에서 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="2639b-608">Getting an event from the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="2639b-609">프로토타입</span><span class="sxs-lookup"><span data-stu-id="2639b-609">Prototype</span></span>

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="2639b-610">Description</span><span class="sxs-lookup"><span data-stu-id="2639b-610">Description</span></span>

<span data-ttu-id="2639b-611">이 함수는 호스트에서 HID 보고서를 애플리케이션에 보낼 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-611">This function is called when the host sends a HID report to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="2639b-612">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2639b-612">Parameters</span></span>

- <span data-ttu-id="2639b-613">**hid**: HID 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-613">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="2639b-614">**hid_event**: HID 이벤트 구조체에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-614">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="example"></a><span data-ttu-id="2639b-615">예제</span><span class="sxs-lookup"><span data-stu-id="2639b-615">Example</span></span>

<span data-ttu-id="2639b-616">다음 예제에서는 HID 키보드의 이벤트를 해석하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2639b-616">The following example shows how to interpret an event for a HID keyboard:</span></span>

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
