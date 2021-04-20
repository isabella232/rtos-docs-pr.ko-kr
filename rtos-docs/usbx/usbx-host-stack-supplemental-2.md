---
title: USBX 호스트 클래스 API
description: 이 장에서는 USBX 호스트 클래스의 노출된 모든 API에 대해 설명합니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 39f3a71c28dd14e0093f72d1a3b1ff6837c6f1f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812930"
---
# <a name="chapter-2-usbx-host-classes-api"></a><span data-ttu-id="f53e8-103">2장: USBX 호스트 클래스 API</span><span class="sxs-lookup"><span data-stu-id="f53e8-103">Chapter 2: USBX Host Classes API</span></span>

<span data-ttu-id="f53e8-104">이 장에서는 USBX 호스트 클래스의 노출된 모든 API에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="f53e8-105">다음과 같은 각 클래스용 API에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="f53e8-106">Printer 클래스</span><span class="sxs-lookup"><span data-stu-id="f53e8-106">Printer class</span></span>
- <span data-ttu-id="f53e8-107">Audio 클래스</span><span class="sxs-lookup"><span data-stu-id="f53e8-107">Audio class</span></span>
- <span data-ttu-id="f53e8-108">Asix 클래스</span><span class="sxs-lookup"><span data-stu-id="f53e8-108">Asix class</span></span>
- <span data-ttu-id="f53e8-109">Pima/PTP 클래스</span><span class="sxs-lookup"><span data-stu-id="f53e8-109">Pima/PTP class</span></span>
- <span data-ttu-id="f53e8-110">Prolific 클래스</span><span class="sxs-lookup"><span data-stu-id="f53e8-110">Prolific class</span></span>
- <span data-ttu-id="f53e8-111">Generic Serial 클래스</span><span class="sxs-lookup"><span data-stu-id="f53e8-111">Generic Serial class</span></span>

## <a name="ux_host_class_printer_read"></a><span data-ttu-id="f53e8-112">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="f53e8-112">ux_host_class_printer_read</span></span>

<span data-ttu-id="f53e8-113">프린터 인터페이스에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-113">Read from the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-114">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-114">Prototype</span></span>

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="f53e8-115">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-115">Description</span></span>

<span data-ttu-id="f53e8-116">이 함수는 프린터 인터페이스에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-116">This function reads from the printer interface.</span></span> <span data-ttu-id="f53e8-117">호출이 차단되고 오류가 있거나 전송이 완료된 경우에만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-117">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span> <span data-ttu-id="f53e8-118">읽기는 양방향 프린터에서만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-118">A read is allowed only on bi-directional printers.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-119">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-119">Parameters</span></span>

- <span data-ttu-id="f53e8-120">**printer**: 프린터 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-120">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="f53e8-121">**data_pointer**: 데이터 페이로드의 버퍼 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-121">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="f53e8-122">**requested_length**: 수신될 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-122">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="f53e8-123">**actual_length**: 실제로 수신된 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-123">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-124">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-124">Return Value</span></span>

- <span data-ttu-id="f53e8-125">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-125">**UX_SUCCESS**:  (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-126">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 프린터가 양방향이 아니기 때문에 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-126">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported because the printer is not bi-directional.</span></span>
- <span data-ttu-id="f53e8-127">**UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 읽기가 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-127">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-128">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-128">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a><span data-ttu-id="f53e8-129">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="f53e8-129">ux_host_class_printer_write</span></span>

<span data-ttu-id="f53e8-130">프린터 인터페이스에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-130">Write to the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-131">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-131">Prototype</span></span>

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="f53e8-132">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-132">Description</span></span>

<span data-ttu-id="f53e8-133">이 함수는 프린터 인터페이스에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-133">This function writes to the printer interface.</span></span> <span data-ttu-id="f53e8-134">호출이 차단되고 오류가 있거나 전송이 완료된 경우에만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-134">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-135">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-135">Parameters</span></span>

- <span data-ttu-id="f53e8-136">**printer**: 프린터 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-136">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="f53e8-137">**data_pointer**: 데이터 페이로드의 버퍼 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-137">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="f53e8-138">**requested_length**: 전송될 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-138">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="f53e8-139">**actual_length**: 실제로 전송된 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-139">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-140">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-140">Return Value</span></span>

- <span data-ttu-id="f53e8-141">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-141">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-142">**UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 쓰기가 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-142">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-143">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-143">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="f53e8-144">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="f53e8-144">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="f53e8-145">프린터에 대한 소프트 초기화를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-145">Perform a soft reset to the printer.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-146">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-146">Prototype</span></span>

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a><span data-ttu-id="f53e8-147">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-147">Description</span></span>

<span data-ttu-id="f53e8-148">이 함수는 프린터에 대한 소프트 초기화를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-148">This function performs a soft reset to the printer.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="f53e8-149">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-149">Input Parameter</span></span>

- <span data-ttu-id="f53e8-150">**printer**: 프린터 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-150">**printer**: Pointer to the printer class instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-151">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-151">Return Value</span></span>

- <span data-ttu-id="f53e8-152">**UX_SUCCESS**: (0x00) 초기화가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-152">**UX_SUCCESS**: (0x00)The reset was completed.</span></span>
- <span data-ttu-id="f53e8-153">**UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 초기화가 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-153">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-154">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-154">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="f53e8-155">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="f53e8-155">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="f53e8-156">프린터 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="f53e8-156">Get the printer status</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-157">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-157">Prototype</span></span>

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a><span data-ttu-id="f53e8-158">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-158">Description</span></span>

<span data-ttu-id="f53e8-159">이 함수는 프린터 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-159">This function obtains the printer status.</span></span> <span data-ttu-id="f53e8-160">프린터 상태는 LPT 상태(1284 표준)와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-160">The printer status is similar to the LPT status (1284 standard).</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-161">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-161">Parameters</span></span>

- <span data-ttu-id="f53e8-162">**printer**: 프린터 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-162">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="f53e8-163">**printer_status**: 반환될 상태의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-163">**printer_status**: Address of the status to be returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-164">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-164">Return Value</span></span>

- <span data-ttu-id="f53e8-165">**UX_SUCCESS**(0x00): 초기화가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-165">**UX_SUCCESS** (0x00): The reset was completed.</span></span>
- <span data-ttu-id="f53e8-166">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-166">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="f53e8-167">**UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 초기화가 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-167">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-168">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-168">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a><span data-ttu-id="f53e8-169">ux_host_class_printer_device_id_get</span><span class="sxs-lookup"><span data-stu-id="f53e8-169">ux_host_class_printer_device_id_get</span></span>

<span data-ttu-id="f53e8-170">프린터 디바이스 ID를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-170">Get the printer device id.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-171">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-171">Prototype</span></span>

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a><span data-ttu-id="f53e8-172">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-172">Description</span></span>

<span data-ttu-id="f53e8-173">이 함수는 프린터 IEEE 1284 디바이스 ID 문자열(Big Endian 형식의 처음 2바이트 길이 포함)을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-173">This function obtains the printer IEEE 1284 device ID string (including length in the first two bytes in big endian format).</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-174">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-174">Parameters</span></span>

- <span data-ttu-id="f53e8-175">**printer**: 프린터 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-175">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="f53e8-176">**descriptor_buffer**: IEEE 1284 디바이스 ID 문자열(BE 형식으로 처음 2바이트의 길이 포함)을 채우는 버퍼에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-176">**descriptor_buffer**: Pointer to a buffer to fill IEEE 1284 device ID string (including length in the first two bytes in BE format)</span></span> 
- <span data-ttu-id="f53e8-177">**length**: 버퍼의 길이(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-177">**length**: Length of buffer in bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-178">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-178">Return Value</span></span>

- <span data-ttu-id="f53e8-179">**UX_SUCCESS** (0x00): 작업이 성공적으로 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-179">**UX_SUCCESS** (0x00): The operation was successful.</span></span>
- <span data-ttu-id="f53e8-180">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-180">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="f53e8-181">**UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 요청이 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-181">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, request not completed</span></span>
- <span data-ttu-id="f53e8-182">**UX_TRANSFER_NOT_READY**: (0x25) 디바이스 상태가 잘못되었습니다. ATTACHED, ADDRESSED 또는 CONFIGURED여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-182">**UX_TRANSFER_NOT_READY**: (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>
- <span data-ttu-id="f53e8-183">**UX_TRANSFER_STALL**: (0x21) 전송이 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-183">**UX_TRANSFER_STALL**: (0x21) Transfer stalled.</span></span>
- <span data-ttu-id="f53e8-184">**TX_WAIT_ABORTED** (0x1A) 일시 중단이 다른 스레드, 타이머 또는 ISR에 의해 취소되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-184">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="f53e8-185">**TX_SEMAPHORE_ERROR** (0x0C) 잘못된 가산 세마포 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-185">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="f53e8-186">**TX_WAIT_ERROR** (0x04) 비스레드의 호출에서 TX_NO_WAIT 이외의 대기 옵션이 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-186">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-187">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-187">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a><span data-ttu-id="f53e8-188">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="f53e8-188">ux_host_class_audio_read</span></span>

<span data-ttu-id="f53e8-189">오디오 인터페이스에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-189">Read from the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-190">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-190">Prototype</span></span>

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="f53e8-191">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-191">Description</span></span>

<span data-ttu-id="f53e8-192">이 함수는 오디오 인터페이스에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-192">This function reads from the audio interface.</span></span> <span data-ttu-id="f53e8-193">이 호출은 차단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-193">The call is non-blocking.</span></span> <span data-ttu-id="f53e8-194">애플리케이션에서 오디오 스트리밍 인터페이스를 위해 적절한 대체 설정이 선택되어 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-194">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-195">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-195">Parameters</span></span>

- <span data-ttu-id="f53e8-196">**audio**: 오디오 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-196">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="f53e8-197">**audio_transfer_request**: 오디오 전송 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-197">**audio_transfer_request**: Pointer to the audio transfer structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-198">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-198">Return Value</span></span>

- <span data-ttu-id="f53e8-199">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-199">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="f53e8-200">**UX_FUNCTION_NOT_SUPPORTED**" (0x54) 함수는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-200">**UX_FUNCTION_NOT_SUPPORTED**" (0x54) Function not supported</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-201">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-201">Example</span></span>

```C
/* The following example reads from the audio interface. */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;

status = ux_host_class_audio_read(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_write"></a><span data-ttu-id="f53e8-202">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="f53e8-202">ux_host_class_audio_write</span></span>

<span data-ttu-id="f53e8-203">오디오 인터페이스에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-203">Write to the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-204">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-204">Prototype</span></span>

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="f53e8-205">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-205">Description</span></span>

<span data-ttu-id="f53e8-206">이 함수는 오디오 인터페이스에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-206">This function writes to the audio interface.</span></span> <span data-ttu-id="f53e8-207">이 호출은 차단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-207">The call is non-blocking.</span></span> <span data-ttu-id="f53e8-208">애플리케이션에서 오디오 스트리밍 인터페이스를 위해 적절한 대체 설정이 선택되어 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-208">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-209">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-209">Parameters</span></span>

- <span data-ttu-id="f53e8-210">**audio**: 오디오 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-210">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="f53e8-211">**audio_transfer_request**: 오디오 전송 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-211">**audio_transfer_request**: Pointer to the audio transfer structure</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-212">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-212">Return Value</span></span>

- <span data-ttu-id="f53e8-213">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-213">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-214">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 함수는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-214">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported.</span></span>
- <span data-ttu-id="f53e8-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) 인터페이스가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-216">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-216">Example</span></span>

```C
UINT status;

/* The following example writes to the audio interface */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;
status = ux_host_class_audio_write(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_get"></a><span data-ttu-id="f53e8-217">ux_host_class_audio_control_get</span><span class="sxs-lookup"><span data-stu-id="f53e8-217">ux_host_class_audio_control_get</span></span>

<span data-ttu-id="f53e8-218">오디오 컨트롤 인터페이스에서 특정 컨트롤을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-218">Get a specific control from the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-219">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-219">Prototype</span></span>

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a><span data-ttu-id="f53e8-220">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-220">Description</span></span>

<span data-ttu-id="f53e8-221">이 함수는 오디오 컨트롤 인터페이스에서 특정 컨트롤을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-221">This function reads a specific control from the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-222">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-222">Parameters</span></span>

- <span data-ttu-id="f53e8-223">**audio**: 오디오 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-223">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="f53e8-224">**audio_control**: 오디오 컨트롤 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-224">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-225">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-225">Return Value</span></span>

- <span data-ttu-id="f53e8-226">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-226">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="f53e8-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 함수는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="f53e8-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) 인터페이스가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-229">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-229">Example</span></span>

```C
UINT status;

/* The following example reads the volume control from a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */

audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="f53e8-230">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="f53e8-230">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="f53e8-231">특정 컨트롤을 오디오 컨트롤 인터페이스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-231">Set a specific control to the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-232">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-232">Prototype</span></span>

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

<span data-ttu-id="f53e8-233">**설명**</span><span class="sxs-lookup"><span data-stu-id="f53e8-233">\*\*Description \*\*</span></span>

<span data-ttu-id="f53e8-234">이 함수는 특정 컨트롤을 오디오 컨트롤 인터페이스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-234">This function sets a specific control to the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-235">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-235">Parameters</span></span>

- <span data-ttu-id="f53e8-236">**audio**: 오디오 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-236">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="f53e8-237">**audio_control**: 오디오 컨트롤 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-237">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-238">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-238">Return Value</span></span>

- <span data-ttu-id="f53e8-239">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-239">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="f53e8-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 함수는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="f53e8-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) 인터페이스가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-242">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-242">Example</span></span>

```C
/* The following example sets the volume control of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

UINT status;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */

current_volume = audio_control.audio_control_cur;
audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="f53e8-243">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="f53e8-243">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="f53e8-244">오디오 스트리밍 인터페이스의 대체 설정 인터페이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-244">Set an alternate setting interface of the audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-245">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-245">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="f53e8-246">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-246">Description</span></span>

<span data-ttu-id="f53e8-247">이 함수는 특정 샘플링 구조에 따라 오디오 스트리밍 인터페이스의 대체 설정 인터페이스를 적절하게 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-247">This function sets the appropriate alternate setting interface of the audio streaming interface according to a specific sampling structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-248">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-248">Parameters</span></span>

- <span data-ttu-id="f53e8-249">**audio**: 오디오 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-249">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="f53e8-250">**audio_sampling**: 오디오 샘플링 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-250">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-251">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-251">Return Value</span></span>

- <span data-ttu-id="f53e8-252">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-252">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="f53e8-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 함수는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="f53e8-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) 인터페이스가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="f53e8-255">**UX_NO_ALTERNATE_SETTING**: (0x5e) 샘플링 값에 대한 대체 설정이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-255">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-256">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-256">Example</span></span>

```C
/* The following example sets the alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels = 2;
sampling.ux_host_class_audio_sampling_frequency = AUDIO_FREQUENCY;
sampling. ux_host_class_audio_sampling_resolution = 16;

status = ux_host_class_audio_streaming_sampling_set(audio, &sampling);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="f53e8-257">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="f53e8-257">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="f53e8-258">오디오 스트리밍 인터페이스에서 사용 가능한 샘플링 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-258">Get possible sampling settings of audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-259">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-259">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="f53e8-260">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-260">Description</span></span>

<span data-ttu-id="f53e8-261">이 함수는 오디오 스트리밍 인터페이스의 각 대체 설정에서 사용할 수 있는 모든 샘플링 설정을 하나씩 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-261">This function gets, one by one, all the possible sampling settings available in each of the alternate settings of the audio streaming interface.</span></span> <span data-ttu-id="f53e8-262">함수를 처음 사용하는 경우 호출 구조 포인터의 모든 필드를 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-262">The first time the function is used, all the fields in the calling structure pointer must be reset.</span></span> <span data-ttu-id="f53e8-263">이 함수는 대체 설정의 끝에 도달하지 않는 한 반환 시 스트리밍 값의 특정 세트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-263">The function will return a specific set of streaming values upon return unless the end of the alternate settings has been reached.</span></span> <span data-ttu-id="f53e8-264">이 함수를 다시 사용하면 앞의 샘플링 값이 다음 샘플링 값을 찾는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-264">When this function is reused, the previous sampling values will be used to find the next sampling values.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-265">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-265">Parameters</span></span>

- <span data-ttu-id="f53e8-266">**audio**: 오디오 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-266">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="f53e8-267">**audio_sampling**: 오디오 샘플링 구조에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-267">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-268">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-268">Return Value</span></span>

- <span data-ttu-id="f53e8-269">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-269">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="f53e8-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 함수는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="f53e8-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) 인터페이스가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="f53e8-272">**UX_NO_ALTERNATE_SETTING**: (0x5e) 샘플링 값에 대한 대체 설정이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-272">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-273">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-273">Example</span></span>

```C
/* The following example gets the sampling values for the first alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels=0;
sampling.ux_host_class_audio_sampling_frequency_low=0;
sampling.ux_host_class_audio_sampling_frequency_high=0;
sampling.ux_host_class_audio_sampling_resolution=0;

status = ux_host_class_audio_streaming_sampling_get(audio, &sampling);

/* If status equals UX_SUCCESS, the operation was successful and information could be displayed as follows:

printf("Number of channels %d, Resolution %d bits, frequency range %d-%d\n",
    sampling.audio_channels, sampling.audio_resolution,
    sampling.audio_frequency_low, sampling.audio_frequency_high);

*/
```

## <a name="ux_host_class_asix_read"></a><span data-ttu-id="f53e8-274">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="f53e8-274">ux_host_class_asix_read</span></span>

<span data-ttu-id="f53e8-275">Asix 인터페이스에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-275">Read from the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-276">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-276">Prototype</span></span>

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="f53e8-277">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-277">Description</span></span>

<span data-ttu-id="f53e8-278">이 함수는 asix 인터페이스에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-278">This function reads from the asix interface.</span></span> <span data-ttu-id="f53e8-279">호출이 차단되고 오류가 있거나 전송이 완료된 경우에만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-279">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-280">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-280">Parameters</span></span>

- <span data-ttu-id="f53e8-281">**asix**: asix 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-281">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="f53e8-282">**data_pointer**: 데이터 페이로드의 버퍼 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-282">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="f53e8-283">**requested_length**: 수신될 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-283">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="f53e8-284">**actual_length**: 실제로 수신된 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-284">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-285">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-285">Return Value</span></span>

- <span data-ttu-id="f53e8-286">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-286">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-287">**UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 읽기가 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-287">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-288">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-288">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a><span data-ttu-id="f53e8-289">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="f53e8-289">ux_host_class_asix_write</span></span>

<span data-ttu-id="f53e8-290">Asix 인터페이스에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-290">Write to the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-291">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-291">Prototype</span></span>

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a><span data-ttu-id="f53e8-292">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-292">Description</span></span>

<span data-ttu-id="f53e8-293">이 함수는 asix 인터페이스에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-293">This function writes to the asix interface.</span></span> <span data-ttu-id="f53e8-294">이 호출은 차단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-294">The call is non blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-295">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-295">Parameters</span></span>

- <span data-ttu-id="f53e8-296">**asix**: asix 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-296">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="f53e8-297">**패킷**: Netx 데이터 패킷입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-297">**packet**: Netx data packet</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-298">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-298">Return Value</span></span>

- <span data-ttu-id="f53e8-299">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-299">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-300">**UX_ERROR**: (0xFF) 전송을 요청할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-300">**UX_ERROR**: (0xFF) Transfer could not be requested.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-301">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-301">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="f53e8-302">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="f53e8-302">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="f53e8-303">개시 장치와 응답기 사이에서 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-303">Open a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-304">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-304">Prototype</span></span>

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="f53e8-305">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-305">Description</span></span>

<span data-ttu-id="f53e8-306">이 함수는 PIMA 개시 장치와 PIMA 응답기 사이에서 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-306">This function opens a session between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="f53e8-307">세션이 성공적으로 열리면 대부분의 PIMA 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-307">Once a session is successfully opened, most PIMA commands can be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-308">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-308">Parameters</span></span>

- <span data-ttu-id="f53e8-309">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-309">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-310">**pima_sessio**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-310">**pima_sessio**: Pointer to PIMA session<</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-311">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-311">Return Value</span></span>

- <span data-ttu-id="f53e8-312">**UX_SUCCESS**: (0x00) 세션이 열렸습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-312">**UX_SUCCESS**: (0x00) Session successfully opened</span></span>
- <span data-ttu-id="f53e8-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) 세션이 이미 열려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) Session already opened</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-314">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-314">Example</span></span>

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="f53e8-315">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="f53e8-315">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="f53e8-316">개시 장치와 응답기 사이의 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-316">Close a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-317">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-317">Prototype</span></span>

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="f53e8-318">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-318">Description</span></span>

<span data-ttu-id="f53e8-319">이 함수는 PIMA 개시 장치와 PIMA 응답기 사이에서 이전에 열린 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-319">This function closes a session that was previously opened between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="f53e8-320">세션이 닫힌 후에는 대부분의 PIMA 명령을 더 이상 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-320">Once a session is closed, most PIMA commands can no longer be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-321">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-321">Parameters</span></span>

- <span data-ttu-id="f53e8-322">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-322">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-323">**pima_session**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-323">**pima_session**: Pointer to PIMA session.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-324">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-324">Return Value</span></span>

- <span data-ttu-id="f53e8-325">**UX_SUCCESS**: (0x00) 세션이 닫혔습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-325">**UX_SUCCESS**: (0x00) The session was closed.</span></span>
- <span data-ttu-id="f53e8-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-327">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-327">Example</span></span>

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a><span data-ttu-id="f53e8-328">ux_host_class_pima_storage_ids_get</span><span class="sxs-lookup"><span data-stu-id="f53e8-328">ux_host_class_pima_storage_ids_get</span></span>

<span data-ttu-id="f53e8-329">응답기에서 스토리지 ID 배열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-329">Obtain the storage ID array from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-330">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-330">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a><span data-ttu-id="f53e8-331">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-331">Description</span></span>

<span data-ttu-id="f53e8-332">이 함수는 응답기에서 스토리지 ID 배열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-332">This function obtains the storage ID array from the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-333">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-333">Parameters</span></span>

- <span data-ttu-id="f53e8-334">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-334">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-335">**pima_session**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-335">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="f53e8-336">**storage_ids_array**: 스토리지 ID를 반환하는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-336">**storage_ids_array**: Array where storage IDs will be returned</span></span>
- <span data-ttu-id="f53e8-337">**storage_id_length**: 스토리지 배열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-337">**storage_id_length**: Length of the storage array</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-338">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-338">Return Value</span></span>

- <span data-ttu-id="f53e8-339">**UX_SUCCESS**: (0x00) 스토리지 ID 배열이 채워져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-339">**UX_SUCCESS**: (0x00) The storage ID array has been populated</span></span>
- <span data-ttu-id="f53e8-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="f53e8-341">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-341">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-342">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-342">Example</span></span>

```C
/* Get the number of storage IDs. */
status = ux_host_class_pima_storage_ids_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids, 64);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="f53e8-343">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="f53e8-343">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="f53e8-344">응답기로부터 스토리지 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-344">Obtain the storage information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-345">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-345">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a><span data-ttu-id="f53e8-346">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-346">Description</span></span>

<span data-ttu-id="f53e8-347">이 함수는 *storage_id* 값의 스토리지 컨테이너에 대한 스토리지 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-347">This function obtains the storage information for a storage container of value *storage_id*.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-348">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-348">Parameters</span></span>

- <span data-ttu-id="f53e8-349">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-349">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-350">**pima_session**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-350">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="f53e8-351">**storage_id**: 스토리지 컨테이너의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-351">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="f53e8-352">**storage**: 스토리지 정보 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-352">**storage**: Pointer to storage information container</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-353">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-353">Return Value</span></span>

- <span data-ttu-id="f53e8-354">**UX_SUCCESS**: (0x00) 스토리지 정보가 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-354">**UX_SUCCESS**: (0x00) The storage information was retrieved</span></span>
- <span data-ttu-id="f53e8-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="f53e8-356">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-356">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-357">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-357">Example</span></span>

```C
/* Get the first storage ID info container. */
status = ux_host_class_pima_storage_info_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids[0],
    (UX_HOST_CLASS_PIMA_STORAGE *)pictbridge ->ux_pictbridge_storage);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pictbridge ->
        ux_pictbridge_pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_num_objects_get"></a><span data-ttu-id="f53e8-358">ux_host_class_pima_num_objects_get</span><span class="sxs-lookup"><span data-stu-id="f53e8-358">ux_host_class_pima_num_objects_get</span></span>

<span data-ttu-id="f53e8-359">응답기에서 스토리지 컨테이너의 개체 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-359">Obtain the number of objects on a storage container from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-360">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-360">Prototype</span></span>

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a><span data-ttu-id="f53e8-361">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-361">Description</span></span>

<span data-ttu-id="f53e8-362">이 함수는 특정 형식 코드와 일치하는 storage_id 값의 특정 스토리지 컨테이너에 저장된 개체 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-362">This function obtains the number of objects stored on a specific storage container of value storage_id matching a specific format code.</span></span> <span data-ttu-id="f53e8-363">개체 수는 pima_session 구조의 ux_host_class_pima_session_nb_objects 필드에서 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-363">The number of objects is returned in the field: ux_host_class_pima_session_nb_objects of the pima_session structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-364">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-364">Parameters</span></span>

- <span data-ttu-id="f53e8-365">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-365">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-366">**pima_session**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-366">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="f53e8-367">**storage_id**: 스토리지 컨테이너의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-367">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="f53e8-368">**object_format_code**: 개체 형식 코드 필터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-368">**object_format_code**: Objects format code filter.</span></span>

<span data-ttu-id="f53e8-369">개체 형식 코드는 다음 값 중 하나가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-369">The Object Format Codes can have one of the following values.</span></span>

| <span data-ttu-id="f53e8-370">개체 형식 코드</span><span class="sxs-lookup"><span data-stu-id="f53e8-370">Object Format Code</span></span>               | <span data-ttu-id="f53e8-371">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-371">Description</span></span>   |     <span data-ttu-id="f53e8-372">USBX 코드</span><span class="sxs-lookup"><span data-stu-id="f53e8-372">USBX code</span></span>                          |
|----------------------------------|---------------|------------------------------------------|
| <span data-ttu-id="f53e8-373">0x3000</span><span class="sxs-lookup"><span data-stu-id="f53e8-373">0x3000</span></span>                           | <span data-ttu-id="f53e8-374">정의되지 않음 정의되지 않은 이미지 개체</span><span class="sxs-lookup"><span data-stu-id="f53e8-374">Undefined Undefined non-image object</span></span> | <span data-ttu-id="f53e8-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span><span class="sxs-lookup"><span data-stu-id="f53e8-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span></span>   |
| <span data-ttu-id="f53e8-376">0x3001</span><span class="sxs-lookup"><span data-stu-id="f53e8-376">0x3001</span></span>                           | <span data-ttu-id="f53e8-377">연결 연결(예: 폴더)</span><span class="sxs-lookup"><span data-stu-id="f53e8-377">Association Association (e.g. folder)</span></span> | <span data-ttu-id="f53e8-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span><span class="sxs-lookup"><span data-stu-id="f53e8-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span></span> |
| <span data-ttu-id="f53e8-379">0x3002</span><span class="sxs-lookup"><span data-stu-id="f53e8-379">0x3002</span></span>                           | <span data-ttu-id="f53e8-380">스크립트 디바이스 모델별 스크립트</span><span class="sxs-lookup"><span data-stu-id="f53e8-380">Script Device-model specific script</span></span> | <span data-ttu-id="f53e8-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span><span class="sxs-lookup"><span data-stu-id="f53e8-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span></span>      |
| <span data-ttu-id="f53e8-382">0x3003</span><span class="sxs-lookup"><span data-stu-id="f53e8-382">0x3003</span></span>                           | <span data-ttu-id="f53e8-383">실행 파일 디바이스 모델별 이진 실행 파일</span><span class="sxs-lookup"><span data-stu-id="f53e8-383">Executable Device model-specific binary executable</span></span> | <span data-ttu-id="f53e8-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span><span class="sxs-lookup"><span data-stu-id="f53e8-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span></span>  |
| <span data-ttu-id="f53e8-385">0x3004</span><span class="sxs-lookup"><span data-stu-id="f53e8-385">0x3004</span></span>                           | <span data-ttu-id="f53e8-386">텍스트 텍스트 파일</span><span class="sxs-lookup"><span data-stu-id="f53e8-386">Text Text file</span></span>  |   <span data-ttu-id="f53e8-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span><span class="sxs-lookup"><span data-stu-id="f53e8-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span></span>        |
| <span data-ttu-id="f53e8-388">0x3005</span><span class="sxs-lookup"><span data-stu-id="f53e8-388">0x3005</span></span>                           | <span data-ttu-id="f53e8-389">HTML HyperText Markup Language 파일(텍스트)</span><span class="sxs-lookup"><span data-stu-id="f53e8-389">HTML HyperText Markup Language file (text)</span></span> | <span data-ttu-id="f53e8-390">UX_HOST_CLASS_PIMA_OFC_HTML</span><span class="sxs-lookup"><span data-stu-id="f53e8-390">UX_HOST_CLASS_PIMA_OFC_HTML</span></span>        |
| <span data-ttu-id="f53e8-391">0x3006</span><span class="sxs-lookup"><span data-stu-id="f53e8-391">0x3006</span></span>                           | <span data-ttu-id="f53e8-392">DPOF Digital Print Order Format 파일(텍스트)</span><span class="sxs-lookup"><span data-stu-id="f53e8-392">DPOF Digital Print Order Format file (text)</span></span> | <span data-ttu-id="f53e8-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span><span class="sxs-lookup"><span data-stu-id="f53e8-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span></span>        |
| <span data-ttu-id="f53e8-394">0x3007</span><span class="sxs-lookup"><span data-stu-id="f53e8-394">0x3007</span></span>                           | <span data-ttu-id="f53e8-395">AIFF 오디오 클립</span><span class="sxs-lookup"><span data-stu-id="f53e8-395">AIFF Audio clip</span></span>  |  <span data-ttu-id="f53e8-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span><span class="sxs-lookup"><span data-stu-id="f53e8-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span></span>        |
| <span data-ttu-id="f53e8-397">0x3008</span><span class="sxs-lookup"><span data-stu-id="f53e8-397">0x3008</span></span>                           | <span data-ttu-id="f53e8-398">WAV 오디오 클립</span><span class="sxs-lookup"><span data-stu-id="f53e8-398">WAV Audio clip</span></span>   |  <span data-ttu-id="f53e8-399">UX_HOST_CLASS_PIMA_OFC_WAV</span><span class="sxs-lookup"><span data-stu-id="f53e8-399">UX_HOST_CLASS_PIMA_OFC_WAV</span></span>         |
| <span data-ttu-id="f53e8-400">0x3009</span><span class="sxs-lookup"><span data-stu-id="f53e8-400">0x3009</span></span>                           | <span data-ttu-id="f53e8-401">MP3 오디오 클립</span><span class="sxs-lookup"><span data-stu-id="f53e8-401">MP3 Audio clip</span></span>   |  <span data-ttu-id="f53e8-402">UX_HOST_CLASS_PIMA_OFC_MP3</span><span class="sxs-lookup"><span data-stu-id="f53e8-402">UX_HOST_CLASS_PIMA_OFC_MP3</span></span>         |
| <span data-ttu-id="f53e8-403">0x300A</span><span class="sxs-lookup"><span data-stu-id="f53e8-403">0x300A</span></span>                           | <span data-ttu-id="f53e8-404">AVI 동영상 클립</span><span class="sxs-lookup"><span data-stu-id="f53e8-404">AVI Video clip</span></span>   |  <span data-ttu-id="f53e8-405">UX_HOST_CLASS_PIMA_OFC_AVI</span><span class="sxs-lookup"><span data-stu-id="f53e8-405">UX_HOST_CLASS_PIMA_OFC_AVI</span></span>         |
| <span data-ttu-id="f53e8-406">0x300B</span><span class="sxs-lookup"><span data-stu-id="f53e8-406">0x300B</span></span>                           | <span data-ttu-id="f53e8-407">MPEG 동영상 클립</span><span class="sxs-lookup"><span data-stu-id="f53e8-407">MPEG Video clip</span></span>  |  <span data-ttu-id="f53e8-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span><span class="sxs-lookup"><span data-stu-id="f53e8-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span></span>        |
| <span data-ttu-id="f53e8-409">0x300C</span><span class="sxs-lookup"><span data-stu-id="f53e8-409">0x300C</span></span>                           | <span data-ttu-id="f53e8-410">ASF Microsoft Advanced Streaming Format(동영상)</span><span class="sxs-lookup"><span data-stu-id="f53e8-410">ASF Microsoft Advanced Streaming Format (video)</span></span> | <span data-ttu-id="f53e8-411">UX_HOST_CLASS_PIMA_OFC_ASF</span><span class="sxs-lookup"><span data-stu-id="f53e8-411">UX_HOST_CLASS_PIMA_OFC_ASF</span></span>         |
| <span data-ttu-id="f53e8-412">0x3800</span><span class="sxs-lookup"><span data-stu-id="f53e8-412">0x3800</span></span>                           | <span data-ttu-id="f53e8-413">정의되지 않음 알 수 없는 이미지 개체</span><span class="sxs-lookup"><span data-stu-id="f53e8-413">Undefined Unknown image object</span></span> | <span data-ttu-id="f53e8-414">UX_HOST_CLASS_PIMA_OFC_QT</span><span class="sxs-lookup"><span data-stu-id="f53e8-414">UX_HOST_CLASS_PIMA_OFC_QT</span></span>          |
| <span data-ttu-id="f53e8-415">0x3801</span><span class="sxs-lookup"><span data-stu-id="f53e8-415">0x3801</span></span>                           | <span data-ttu-id="f53e8-416">EXIF/JPEG 교환 파일 형식, JEIDA 표준</span><span class="sxs-lookup"><span data-stu-id="f53e8-416">EXIF/JPEG Exchangeable File Format, JEIDA standard</span></span> | <span data-ttu-id="f53e8-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="f53e8-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span></span>   |
| <span data-ttu-id="f53e8-418">0x3802</span><span class="sxs-lookup"><span data-stu-id="f53e8-418">0x3802</span></span>                           | <span data-ttu-id="f53e8-419">TIFF/EP TIFF/EP(Tag Image File Format for Electronic Photography)</span><span class="sxs-lookup"><span data-stu-id="f53e8-419">TIFF/EP Tag Image File Format for Electronic Photography</span></span> | <span data-ttu-id="f53e8-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span><span class="sxs-lookup"><span data-stu-id="f53e8-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span></span>     |
| <span data-ttu-id="f53e8-421">0x3803</span><span class="sxs-lookup"><span data-stu-id="f53e8-421">0x3803</span></span>                           | <span data-ttu-id="f53e8-422">FlashPix 구조적 스토리지 이미지 형식</span><span class="sxs-lookup"><span data-stu-id="f53e8-422">FlashPix Structured Storage Image Format</span></span> | <span data-ttu-id="f53e8-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span><span class="sxs-lookup"><span data-stu-id="f53e8-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span></span>    |
| <span data-ttu-id="f53e8-424">0x3804</span><span class="sxs-lookup"><span data-stu-id="f53e8-424">0x3804</span></span>                           | <span data-ttu-id="f53e8-425">BMP Microsoft Windows 비트맵 파일</span><span class="sxs-lookup"><span data-stu-id="f53e8-425">BMP Microsoft Windows Bitmap file</span></span> | <span data-ttu-id="f53e8-426">UX_HOST_CLASS_PIMA_OFC_BMP</span><span class="sxs-lookup"><span data-stu-id="f53e8-426">UX_HOST_CLASS_PIMA_OFC_BMP</span></span>         |
| <span data-ttu-id="f53e8-427">0x3805</span><span class="sxs-lookup"><span data-stu-id="f53e8-427">0x3805</span></span>                           | <span data-ttu-id="f53e8-428">CIFF Canon 카메라 이미지 파일 형식</span><span class="sxs-lookup"><span data-stu-id="f53e8-428">CIFF Canon Camera Image File Format</span></span> | <span data-ttu-id="f53e8-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span><span class="sxs-lookup"><span data-stu-id="f53e8-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span></span>        |
| <span data-ttu-id="f53e8-430">0x3806</span><span class="sxs-lookup"><span data-stu-id="f53e8-430">0x3806</span></span>                           | <span data-ttu-id="f53e8-431">정의되지 않음 예약됨</span><span class="sxs-lookup"><span data-stu-id="f53e8-431">Undefined Reserved</span></span> |  |
| <span data-ttu-id="f53e8-432">0x3807</span><span class="sxs-lookup"><span data-stu-id="f53e8-432">0x3807</span></span>                           | <span data-ttu-id="f53e8-433">GIF Graphics Interchange Format</span><span class="sxs-lookup"><span data-stu-id="f53e8-433">GIF Graphics Interchange Format</span></span> | <span data-ttu-id="f53e8-434">UX_HOST_CLASS_PIMA_OFC_GIF</span><span class="sxs-lookup"><span data-stu-id="f53e8-434">UX_HOST_CLASS_PIMA_OFC_GIF</span></span>         |
| <span data-ttu-id="f53e8-435">0x3808</span><span class="sxs-lookup"><span data-stu-id="f53e8-435">0x3808</span></span>                           | <span data-ttu-id="f53e8-436">JFIF JPEG 파일 교환 형식</span><span class="sxs-lookup"><span data-stu-id="f53e8-436">JFIF JPEG File Interchange Format</span></span> | <span data-ttu-id="f53e8-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span><span class="sxs-lookup"><span data-stu-id="f53e8-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span></span>        |
| <span data-ttu-id="f53e8-438">0x3809</span><span class="sxs-lookup"><span data-stu-id="f53e8-438">0x3809</span></span>                           | <span data-ttu-id="f53e8-439">PCD PhotoCD 이미지 팩</span><span class="sxs-lookup"><span data-stu-id="f53e8-439">PCD PhotoCD Image Pac</span></span> | <span data-ttu-id="f53e8-440">UX_HOST_CLASS_PIMA_OFC_PCD</span><span class="sxs-lookup"><span data-stu-id="f53e8-440">UX_HOST_CLASS_PIMA_OFC_PCD</span></span>         |
| <span data-ttu-id="f53e8-441">0x380A</span><span class="sxs-lookup"><span data-stu-id="f53e8-441">0x380A</span></span>                           | <span data-ttu-id="f53e8-442">PICT Quickdraw 이미지 형식</span><span class="sxs-lookup"><span data-stu-id="f53e8-442">PICT Quickdraw Image Format</span></span> | <span data-ttu-id="f53e8-443">UX_HOST_CLASS_PIMA_OFC_PICT</span><span class="sxs-lookup"><span data-stu-id="f53e8-443">UX_HOST_CLASS_PIMA_OFC_PICT</span></span>        |
| <span data-ttu-id="f53e8-444">0x380B</span><span class="sxs-lookup"><span data-stu-id="f53e8-444">0x380B</span></span>                           | <span data-ttu-id="f53e8-445">PNG 이동식 네트워크 그래픽</span><span class="sxs-lookup"><span data-stu-id="f53e8-445">PNG Portable Network Graphics</span></span> | <span data-ttu-id="f53e8-446">UX_HOST_CLASS_PIMA_OFC_PNG</span><span class="sxs-lookup"><span data-stu-id="f53e8-446">UX_HOST_CLASS_PIMA_OFC_PNG</span></span>         |
| <span data-ttu-id="f53e8-447">0x380C</span><span class="sxs-lookup"><span data-stu-id="f53e8-447">0x380C</span></span>                           | <span data-ttu-id="f53e8-448">정의되지 않음 예약됨</span><span class="sxs-lookup"><span data-stu-id="f53e8-448">Undefined Reserved</span></span> |   |
| <span data-ttu-id="f53e8-449">0x380D</span><span class="sxs-lookup"><span data-stu-id="f53e8-449">0x380D</span></span>                           | <span data-ttu-id="f53e8-450">TIFF Tag Image File Format</span><span class="sxs-lookup"><span data-stu-id="f53e8-450">TIFF Tag Image File Format</span></span> | <span data-ttu-id="f53e8-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span><span class="sxs-lookup"><span data-stu-id="f53e8-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span></span>        |
| <span data-ttu-id="f53e8-452">0x380E</span><span class="sxs-lookup"><span data-stu-id="f53e8-452">0x380E</span></span>                           | <span data-ttu-id="f53e8-453">TIFF/IT TIFF/IT(Tag Image File Format for Information Technology)(그래픽 아트)</span><span class="sxs-lookup"><span data-stu-id="f53e8-453">TIFF/IT Tag Image File Format for Information Technology (graphic arts)</span></span> | <span data-ttu-id="f53e8-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span><span class="sxs-lookup"><span data-stu-id="f53e8-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span></span>     |
| <span data-ttu-id="f53e8-455">0x380F</span><span class="sxs-lookup"><span data-stu-id="f53e8-455">0x380F</span></span>                           | <span data-ttu-id="f53e8-456">JP2 JPEG2000 기준 파일 형식</span><span class="sxs-lookup"><span data-stu-id="f53e8-456">JP2 JPEG2000 Baseline File Format</span></span> | <span data-ttu-id="f53e8-457">UX_HOST_CLASS_PIMA_OFC_JP2</span><span class="sxs-lookup"><span data-stu-id="f53e8-457">UX_HOST_CLASS_PIMA_OFC_JP2</span></span>         |
| <span data-ttu-id="f53e8-458">0x3810</span><span class="sxs-lookup"><span data-stu-id="f53e8-458">0x3810</span></span>                           | <span data-ttu-id="f53e8-459">JPX JPEG2000 확장 파일 형식</span><span class="sxs-lookup"><span data-stu-id="f53e8-459">JPX JPEG2000 Extended File Format</span></span> | <span data-ttu-id="f53e8-460">UX_HOST_CLASS_PIMA_OFC_JPX</span><span class="sxs-lookup"><span data-stu-id="f53e8-460">UX_HOST_CLASS_PIMA_OFC_JPX</span></span>         |
| <span data-ttu-id="f53e8-461">MSN 0011을 사용하는 기타 모든 코드</span><span class="sxs-lookup"><span data-stu-id="f53e8-461">All other codes with MSN of 0011</span></span> | <span data-ttu-id="f53e8-462">이후 사용을 위해 정의되지 않은 모든 예약</span><span class="sxs-lookup"><span data-stu-id="f53e8-462">Any Undefined Reserved for future use</span></span> |                                    |
| <span data-ttu-id="f53e8-463">MSN 1011을 사용하는 기타 모든 코드</span><span class="sxs-lookup"><span data-stu-id="f53e8-463">All other codes with MSN of 1011</span></span> | <span data-ttu-id="f53e8-464">공급업체에서 정의한 공급업체 정의 형식: 이미지</span><span class="sxs-lookup"><span data-stu-id="f53e8-464">Any Vendor-Defined Vendor-Defined type: Image</span></span> |                                    |

### <a name="return-value"></a><span data-ttu-id="f53e8-465">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-465">Return Value</span></span>

- <span data-ttu-id="f53e8-466">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-466">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="f53e8-468">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-468">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-469">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-469">Example</span></span>

```C
/* Get the number of objects on all containers matching a SCRIPT object. */
status = ux_host_class_pima_num_objects_get(pima, pima_session,
    UX_PICTBRIDGE_ALL_CONTAINERS, UX_PICTBRIDGE_OBJECT_SCRIPT);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_**host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
} else
    /* The number of objects is returned in the field: pima_session -> ux_host_class_pima_session_nb_objects */
```

## <a name="ux_host_class_pima_object_handles_get"></a><span data-ttu-id="f53e8-470">ux_host_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="f53e8-470">ux_host_class_pima_object_handles_get</span></span>

<span data-ttu-id="f53e8-471">응답기에서 개체 핸들을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-471">Obtain object handles from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-472">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-472">Prototype</span></span>

```C
UINT ux_host_class_pima_object_handles_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *object_handles_array,
    ULONG object_handles_length,
    ULONG storage_id,
    ULONG object_format_code,
    ULONG object_handle_association)
```

### <a name="description"></a><span data-ttu-id="f53e8-473">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-473">Description</span></span>

<span data-ttu-id="f53e8-474">Storage_id 매개 변수로 표시되는 스토리지 컨테이너에 있는 개체 핸들의 배열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-474">Returns an array of Object Handles present in the storage container indicated by the storage_id parameter.</span></span> <span data-ttu-id="f53e8-475">모든 저장소에서 집계된 목록이 필요한 경우 이 값은 0xFFFFFFFF로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-475">If an aggregated list across all stores is desired, this value shall be set to 0xFFFFFFFF.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-476">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-476">Parameters</span></span>

- <span data-ttu-id="f53e8-477">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-477">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-478">**pima_session**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-478">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="f53e8-479">**object_handes_array**: 핸들이 반환되는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-479">**object_handes_array**: Array where handles are returned</span></span>
- <span data-ttu-id="f53e8-480">**object_handles_length**: 배열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-480">**object_handles_length**: Length of the array</span></span>
- <span data-ttu-id="f53e8-481">**storage_id**: 스토리지 컨테이너의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-481">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="f53e8-482">**object_format_code**: 개체의 서식 코드입니다(함수 ux_host_class_pima_num_objects_get에 대한 테이블 참조).</span><span class="sxs-lookup"><span data-stu-id="f53e8-482">**object_format_code**: Format code for object (see table for function ux_host_class_pima_num_objects_get)</span></span>
- <span data-ttu-id="f53e8-483">**object_handle_association**: 선택적 개체 연결 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-483">**object_handle_association**: Optional object association value</span></span>

<span data-ttu-id="f53e8-484">개체 핸들 연결은 아래 표의 나오는 값 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-484">The object handle association can be one of the value from the table below:</span></span>

| <span data-ttu-id="f53e8-485">AssociationCode</span><span class="sxs-lookup"><span data-stu-id="f53e8-485">AssociationCode</span></span>                        | <span data-ttu-id="f53e8-486">AssociationType</span><span class="sxs-lookup"><span data-stu-id="f53e8-486">AssociationType</span></span>      | <span data-ttu-id="f53e8-487">해석</span><span class="sxs-lookup"><span data-stu-id="f53e8-487">Interpretation</span></span>       |
|----------------------------------------|----------------------|----------------------|
| <span data-ttu-id="f53e8-488">0x0000</span><span class="sxs-lookup"><span data-stu-id="f53e8-488">0x0000</span></span>                                 | <span data-ttu-id="f53e8-489">Undefined</span><span class="sxs-lookup"><span data-stu-id="f53e8-489">Undefined</span></span>            | <span data-ttu-id="f53e8-490">Undefined</span><span class="sxs-lookup"><span data-stu-id="f53e8-490">Undefined</span></span>            |
| <span data-ttu-id="f53e8-491">0x0001</span><span class="sxs-lookup"><span data-stu-id="f53e8-491">0x0001</span></span>                                 | <span data-ttu-id="f53e8-492">GenericFolder</span><span class="sxs-lookup"><span data-stu-id="f53e8-492">GenericFolder</span></span>        | <span data-ttu-id="f53e8-493">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="f53e8-493">Unused</span></span>               |
| <span data-ttu-id="f53e8-494">0x0002</span><span class="sxs-lookup"><span data-stu-id="f53e8-494">0x0002</span></span>                                 | <span data-ttu-id="f53e8-495">Album</span><span class="sxs-lookup"><span data-stu-id="f53e8-495">Album</span></span>                | <span data-ttu-id="f53e8-496">예약됨</span><span class="sxs-lookup"><span data-stu-id="f53e8-496">Reserved</span></span>             |
| <span data-ttu-id="f53e8-497">0x0003</span><span class="sxs-lookup"><span data-stu-id="f53e8-497">0x0003</span></span>                                 | <span data-ttu-id="f53e8-498">TimeSequence</span><span class="sxs-lookup"><span data-stu-id="f53e8-498">TimeSequence</span></span>         | <span data-ttu-id="f53e8-499">DefaultPlaybackDelta</span><span class="sxs-lookup"><span data-stu-id="f53e8-499">DefaultPlaybackDelta</span></span> |
| <span data-ttu-id="f53e8-500">0x0004</span><span class="sxs-lookup"><span data-stu-id="f53e8-500">0x0004</span></span>                                 | <span data-ttu-id="f53e8-501">HorizontalPanoramic</span><span class="sxs-lookup"><span data-stu-id="f53e8-501">HorizontalPanoramic</span></span>  | <span data-ttu-id="f53e8-502">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="f53e8-502">Unused</span></span>               |
| <span data-ttu-id="f53e8-503">0x0005</span><span class="sxs-lookup"><span data-stu-id="f53e8-503">0x0005</span></span>                                 | <span data-ttu-id="f53e8-504">VerticalPanoramic</span><span class="sxs-lookup"><span data-stu-id="f53e8-504">VerticalPanoramic</span></span>    | <span data-ttu-id="f53e8-505">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="f53e8-505">Unused</span></span>               |
| <span data-ttu-id="f53e8-506">0x0006</span><span class="sxs-lookup"><span data-stu-id="f53e8-506">0x0006</span></span>                                 | <span data-ttu-id="f53e8-507">2DPanoramic</span><span class="sxs-lookup"><span data-stu-id="f53e8-507">2DPanoramic</span></span>          | <span data-ttu-id="f53e8-508">ImagesPerRow</span><span class="sxs-lookup"><span data-stu-id="f53e8-508">ImagesPerRow</span></span>         |
| <span data-ttu-id="f53e8-509">0x0007</span><span class="sxs-lookup"><span data-stu-id="f53e8-509">0x0007</span></span>                                 | <span data-ttu-id="f53e8-510">AncillaryData</span><span class="sxs-lookup"><span data-stu-id="f53e8-510">AncillaryData</span></span>        | <span data-ttu-id="f53e8-511">정의되지 않음</span><span class="sxs-lookup"><span data-stu-id="f53e8-511">Undefined</span></span>            |
| <span data-ttu-id="f53e8-512">비트가 15인 다른 모든 값이 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-512">All other values with bit 15 set to 0</span></span>  | <span data-ttu-id="f53e8-513">예약됨</span><span class="sxs-lookup"><span data-stu-id="f53e8-513">Reserved</span></span>             | <span data-ttu-id="f53e8-514">정의되지 않음</span><span class="sxs-lookup"><span data-stu-id="f53e8-514">Undefined</span></span>            |
| <span data-ttu-id="f53e8-515">비트가 15인 모든 값이 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-515">All values with bit 15 set to 1</span></span>        | <span data-ttu-id="f53e8-516">공급업체 정의</span><span class="sxs-lookup"><span data-stu-id="f53e8-516">Vendor-Defined</span></span>       | <span data-ttu-id="f53e8-517">공급업체 정의</span><span class="sxs-lookup"><span data-stu-id="f53e8-517">Vendor-Defined</span></span>       |

### <a name="return-value"></a><span data-ttu-id="f53e8-518">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-518">Return Value</span></span>

- <span data-ttu-id="f53e8-519">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-519">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="f53e8-521">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-521">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-522">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-522">Example</span></span>

```C
/* Get the array of objects handles on the container. */
status = ux_**host_class_pima_object_handles_get(pima, pima_session,
    pictbridge ->ux_pictbridge_object_handles_array,
    4 * pima_session ->ux_host_class_pima_session_nb_objects,
    UX_PICTBRIDGE_ALL_CONTAINERS,
    UX_PICTBRIDGE_OBJECT_SCRIPT, 0);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="f53e8-523">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="f53e8-523">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="f53e8-524">응답기에서 개체 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-524">Obtain the object information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-525">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-525">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="f53e8-526">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-526">Description</span></span>

<span data-ttu-id="f53e8-527">이 함수는 개체 핸들에 대한 개체 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-527">This function obtains the object information for an object handle.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-528">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-528">Parameters</span></span>

- <span data-ttu-id="f53e8-529">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-529">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-530">**pima_session**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-530">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="f53e8-531">**object_handle**: 개체의 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-531">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="f53e8-532">**object**: 개체 정보 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-532">**object**: Pointer to object information container</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-533">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-533">Return Value</span></span>

- <span data-ttu-id="f53e8-534">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-534">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="f53e8-536">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-536">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-537">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-537">Example</span></span>

```C
/* We search for an object that is a picture or a script. */
object_index = 0;

while (object_index < pima_session -> ux_host_class_pima_session_nb_objects)
{
    /* Get the object info structure. */
    status = ux_**host_class_pima_object_info_get(pima, pima_session,
        pictbridge -> ux_pictbridge_object_handles_array[object_index], 
        pima_object);

    if (status != UX_SUCCESS)
    {
        /* Close the pima session. */
        status = ux_host_class_pima_session_close(pima, pima_session);

        return(UX_PICTBRIDGE_ERROR_INVALID_OBJECT_HANDLE );
    }
}
```

## <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="f53e8-538">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="f53e8-538">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="f53e8-539">개체 정보를 응답기로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-539">Send the object information to Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-540">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-540">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="f53e8-541">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-541">Description</span></span>

<span data-ttu-id="f53e8-542">이 함수는 storage_id 값의 스토리지 컨테이너에 대한 스토리지 정보를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-542">This function sends the storage information for a storage container of value storage_id.</span></span> <span data-ttu-id="f53e8-543">개시 장치는 개체를 응답기로 보내기 전에 이 명령을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-543">The Initiator should use this command before sending an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-544">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-544">Parameters</span></span>

- <span data-ttu-id="f53e8-545">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-545">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-546">**pima_session**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-546">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="f53e8-547">**storage_id**: 대상 스토리지 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-547">**storage_id**: Destination storage ID.</span></span>
- <span data-ttu-id="f53e8-548">**parent_object_id**: 개체를 배치해야 하는 응답기의 부모 ObjectHandle입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-548">**parent_object_id**: Parent ObjectHandle on Responder where object should be placed.</span></span>
- <span data-ttu-id="f53e8-549">**object**: 개체 정보 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-549">**object**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-550">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-550">Return Value</span></span>

- <span data-ttu-id="f53e8-551">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-551">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="f53e8-553">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-553">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-554">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-554">Example</span></span>

```C
/* Send a script info. */
status = ux_host_class_pima_object_info_send(pima, pima_session,
    0, 0, pima_object);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_ERROR);
}
```

## <a name="ux_host_class_pima_object_open"></a><span data-ttu-id="f53e8-555">ux_host_class_pima_object_open</span><span class="sxs-lookup"><span data-stu-id="f53e8-555">ux_host_class_pima_object_open</span></span>

<span data-ttu-id="f53e8-556">응답기에 저장된 개체를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-556">Open an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-557">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-557">Prototype</span></span>

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="f53e8-558">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-558">Description</span></span>

<span data-ttu-id="f53e8-559">이 함수는 읽거나 쓰기 전에 응답기에서 개체를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-559">This function opens an object on the responder before reading or writing.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-560">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-560">Parameters</span></span>

- <span data-ttu-id="f53e8-561">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-561">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-562">**pima_session**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-562">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="f53e8-563">**object_handle**: 개체의 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-563">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="f53e8-564">**object**: 개체 정보 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-564">**objec**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-565">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-565">Return Value</span></span>

- <span data-ttu-id="f53e8-566">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-566">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="f53e8-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) 개체가 이미 열려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) Object already opened.</span></span>
- <span data-ttu-id="f53e8-569">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-569">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-570">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-570">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="f53e8-571">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="f53e8-571">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="f53e8-572">응답기에 저장된 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-572">Get an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-573">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-573">Prototype</span></span>

```C
UINT ux_host_class_pima_object_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer,
    ULONG object_buffer_length,
    ULONG *object_actual_length)
```

### <a name="description"></a><span data-ttu-id="f53e8-574">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-574">Description</span></span>

<span data-ttu-id="f53e8-575">이 함수는 응답기에서 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-575">This function gets an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-576">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-576">Parameters</span></span>

- <span data-ttu-id="f53e8-577">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-577">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-578">**pima_session**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-578">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="f53e8-579">**object_handle**: 개체의 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-579">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="f53e8-580">**object**: 개체 정보 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-580">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="f53e8-581">**object_buffer**: 개체 데이터의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-581">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="f53e8-582">**object_buffer_length**: 요청된 개체의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-582">**object_buffer_length**: Requested length of object</span></span>
- <span data-ttu-id="f53e8-583">**object_actual_length**: 반환되는 개체의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-583">**object_actual_length**: Length of object returned</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-584">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-584">Return Value</span></span>

- <span data-ttu-id="f53e8-585">**UX_SUCCESS**: (0x00) 개체가 전송되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-585">**UX_SUCCESS**: (0x00) The object was transfered</span></span>
- <span data-ttu-id="f53e8-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="f53e8-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) 개체가 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="f53e8-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) 개체에 대한 액세스가 거부되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="f53e8-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) 전송이 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="f53e8-590">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-590">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="f53e8-591">**UX_TRANSFER_ERROR**: (0x23) 개체를 읽는 동안 전송 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-591">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-592">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-592">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);

/* Set the object buffer pointer. */
object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Obtain all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Get the object data. */
    status = ux_host_class_pima_object_get(pima, pima_session,
        object_handle, pima_object, object_buffer,
        requested_length, &actual_length);

    if (status != UX_SUCCESS)
    {
        /* We had a problem, abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* And close the object. */
        ux_host_class_pima_object_close(pima, pima_session,
            object_handle, pima_object, object);

        return(status);

    }

    /* We have received some data, update the length remaining. */
    object_length -= actual_length;

    /* Update the buffer address. */
    object_buffer += actual_length;

}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session,
    object_handle, pima_object, object);
```

## <a name="ux_host_class_pima_object_send"></a><span data-ttu-id="f53e8-593">ux_host_class_pima_object_send</span><span class="sxs-lookup"><span data-stu-id="f53e8-593">ux_host_class_pima_object_send</span></span>

<span data-ttu-id="f53e8-594">응답기에 저장된 개체를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-594">Send an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-595">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-595">Prototype</span></span>

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a><span data-ttu-id="f53e8-596">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-596">Description</span></span>

<span data-ttu-id="f53e8-597">이 함수는 개체를 응답기로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-597">This function sends an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-598">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-598">Parameters</span></span>

- <span data-ttu-id="f53e8-599">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-599">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-600">**pima_sessio**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-600">**pima_sessio**: Pointer to PIMA session</span></span>
- <span data-ttu-id="f53e8-601">**object_handle**: 개체의 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-601">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="f53e8-602">**object**: 개체 정보 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-602">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="f53e8-603">**object_buffer**: 개체 데이터의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-603">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="f53e8-604">**object_buffer_length**: 요청된 개체의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-604">**object_buffer_length**: Requested length of object</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-605">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-605">Return Value</span></span>

- <span data-ttu-id="f53e8-606">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-606">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="f53e8-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) 개체가 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="f53e8-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) 개체에 대한 액세스가 거부되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="f53e8-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) 전송이 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="f53e8-611">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-611">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="f53e8-612">**UX_TRANSFER_ERROR**: (0x23) 개체를 쓰는 동안 전송 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-612">**UX_TRANSFER_ERROR**: (0x23) Transfer error while writing object</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-613">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-613">Example</span></span>

```C
/* Open the object. */
status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Get the object length. */
object_length = pima_object ->ux_host_class_pima_object_compressed_size;

/* Recall the object buffer address. */
pima_object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Send all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Send the object data. */
    status = ux_host_class_pima_object_send(pima,
        pima_session, pima_object,
        pima_object_buffer, requested_length);

    if (status != UX_SUCCESS)
    {
        /* Abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* Return status. */
        return(status);
    }

    /* We have sent some data, update the length remaining. */
    object_length -= requested_length;
}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle,
    pima_object, object);
```

## <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="f53e8-614">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="f53e8-614">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="f53e8-615">응답기에 저장된 thumb 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-615">Get a thumb object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-616">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-616">Prototype</span></span>

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a><span data-ttu-id="f53e8-617">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-617">Description</span></span>

<span data-ttu-id="f53e8-618">이 함수는 응답기의 thumb 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-618">This function gets a thumb object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-619">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-619">Parameters</span></span>

- <span data-ttu-id="f53e8-620">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-620">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-621">**pima_session**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-621">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="f53e8-622">**object_handle**: 개체의 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-622">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="f53e8-623">**object**: 개체 정보 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-623">**object**: Pointer to object information container.</span></span>
- <span data-ttu-id="f53e8-624">**thumb_buffer**: thumb 개체 데이터의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-624">**thumb_buffer**: Address of thumb object data.</span></span>
- <span data-ttu-id="f53e8-625">**thumb_buffer_length**: 요청된 thumb 개체의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-625">**thumb_buffer_length**: Requested length of thumb object.</span></span>
- <span data-ttu-id="f53e8-626">**thumb_actual_length**: 반환되는 thumb 개체의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-626">**thumb_actual_length**: Length of thumb object returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-627">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-627">Return Value</span></span>

- <span data-ttu-id="f53e8-628">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-628">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="f53e8-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) 개체가 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="f53e8-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) 개체에 대한 액세스가 거부되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied.</span></span>
- <span data-ttu-id="f53e8-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) 전송이 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete.</span></span>
- <span data-ttu-id="f53e8-633">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-633">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="f53e8-634">**UX_TRANSFER_ERROR**: (0x23) 개체를 읽는 동안 전송 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-634">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-635">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-635">Example</span></span>

```C
/* Get the thumb object data. */

status = ux_host_class_pima_thumb_get(pima, pima_session,
    object_handle, pima_object, object_buffer,
    requested_length, &actual_length);

if (status != UX_SUCCESS)
{
    /* And close the object. */
    ux_host_class_pima_object_close(pima, pima_session, object_handle, pima_object, object);

    return(status);
}
```

## <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="f53e8-636">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="f53e8-636">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="f53e8-637">응답기에 저장된 개체를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-637">Delete an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-638">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-638">Prototype</span></span>

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a><span data-ttu-id="f53e8-639">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-639">Description</span></span>

<span data-ttu-id="f53e8-640">이 함수는 응답기에서 개체를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-640">This function deletes an object on the responder</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-641">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-641">Parameters</span></span>

- <span data-ttu-id="f53e8-642">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-642">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-643">**pima_session**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-643">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="f53e8-644">**object_handle**: 개체의 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-644">**object_handle**: handle of the object</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-645">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-645">Return Value</span></span>

- <span data-ttu-id="f53e8-646">**UX_SUCCESS**: (0x00) 개체가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-646">**UX_SUCCESS**: (0x00) The object was deleted.</span></span>
- <span data-ttu-id="f53e8-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="f53e8-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) 개체를 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Cannot delete object.</span></span>
- <span data-ttu-id="f53e8-649">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-649">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-650">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-650">Example</span></span>

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="f53e8-651">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="f53e8-651">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="f53e8-652">응답기에 저장된 개체를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-652">Close an object stored in the Responder</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-653">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-653">Prototype</span></span>

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="f53e8-654">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-654">Description</span></span>

<span data-ttu-id="f53e8-655">이 함수는 응답기에서 개체를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-655">This function closes an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-656">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-656">Parameters</span></span>

- <span data-ttu-id="f53e8-657">**pima**: PIMA 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-657">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="f53e8-658">**pima_session**: PIMA 세션에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-658">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="f53e8-659">**object_handle**: 개체의 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-659">**object_handle**: Handle of the object.</span></span>
- <span data-ttu-id="f53e8-660">**object** 개체에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-660">**object**: Pointer to object.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-661">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-661">Return Value</span></span>

- <span data-ttu-id="f53e8-662">**UX_SUCCESS**: (0x00) 개체가 닫혔습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-662">**UX_SUCCESS**: (0x00) The object was closed.</span></span>
- <span data-ttu-id="f53e8-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) 세션이 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="f53e8-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) 개체가 열리지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="f53e8-665">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족하여 PIMA 명령을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-665">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-666">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-666">Example</span></span>

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a><span data-ttu-id="f53e8-667">ux_host_class_gser_read</span><span class="sxs-lookup"><span data-stu-id="f53e8-667">ux_host_class_gser_read</span></span>

<span data-ttu-id="f53e8-668">일반 직렬 인터페이스에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-668">Read from the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-669">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-669">Prototype</span></span>

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="f53e8-670">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-670">Description</span></span>

<span data-ttu-id="f53e8-671">이 함수는 일반 직렬 인터페이스에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-671">This function reads from the generic serial interface.</span></span> <span data-ttu-id="f53e8-672">호출이 차단되고 오류가 있거나 전송이 완료된 경우에만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-672">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-673">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-673">Parameters</span></span>

- <span data-ttu-id="f53e8-674">**gser**: gser 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-674">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="f53e8-675">**interface_index** 읽을 인터페이스 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-675">**interface_index**: Interface index to read from.</span></span>
- <span data-ttu-id="f53e8-676">**data_pointer**: 데이터 페이로드의 버퍼 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-676">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="f53e8-677">**requested_length**: 수신될 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-677">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="f53e8-678">**actual_length**: 실제로 수신된 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-678">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-679">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-679">Return Value</span></span>

- <span data-ttu-id="f53e8-680">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-680">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-681">**UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 읽기가 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-681">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-682">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-682">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a><span data-ttu-id="f53e8-683">ux_host_class_gser_write</span><span class="sxs-lookup"><span data-stu-id="f53e8-683">ux_host_class_gser_write</span></span>

<span data-ttu-id="f53e8-684">일반 직렬 인터페이스에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-684">Write to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-685">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-685">Prototype</span></span>

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="f53e8-686">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-686">Description</span></span>

<span data-ttu-id="f53e8-687">이 함수는 일반 직렬 인터페이스에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-687">This function writes to the generic serial interface.</span></span> <span data-ttu-id="f53e8-688">호출이 차단되고 오류가 있거나 전송이 완료된 경우에만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-688">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-689">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-689">Parameters</span></span>

- <span data-ttu-id="f53e8-690">**gser**: gser 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-690">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="f53e8-691">**interface_index**: 쓰기 작업의 대상 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-691">**interface_index**: Interface to which to write.</span></span>
- <span data-ttu-id="f53e8-692">**data_pointer**: 데이터 페이로드의 버퍼 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-692">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="f53e8-693">**requested_length**: 전송될 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-693">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="f53e8-694">**actual_length**: 실제로 전송된 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-694">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-695">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-695">Return Value</span></span>

- <span data-ttu-id="f53e8-696">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-696">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-697">**UX_TRANSFER_TIMEOUT**: (0x5c) 전송 시간 제한을 초과했습니다. 쓰기가 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-697">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-698">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-698">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a><span data-ttu-id="f53e8-699">ux_host_class_gser_ioctl</span><span class="sxs-lookup"><span data-stu-id="f53e8-699">ux_host_class_gser_ioctl</span></span>

<span data-ttu-id="f53e8-700">일반 직렬 인터페이스에 대한 IOCTL 함수를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-700">Perform an IOCTL function to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-701">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-701">Prototype</span></span>

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a><span data-ttu-id="f53e8-702">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-702">Description</span></span>

<span data-ttu-id="f53e8-703">이 함수는 gser 인터페이스에 대한 특정 ioctl 함수를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-703">This function performs a specific ioctl function to the gser interface.</span></span> <span data-ttu-id="f53e8-704">호출이 차단되고 오류가 있거나 명령이 완료된 경우에만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-704">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-705">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-705">Parameters</span></span>

- <span data-ttu-id="f53e8-706">**gser**: gser 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-706">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="f53e8-707">**ioctl_function**: 실행할 ioctl 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-707">**ioctl_function**: ioctl function to be performed.</span></span> <span data-ttu-id="f53e8-708">허용되는 ioctl 함수 중 하나에 대해서는 아래 테이블 중 하나를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f53e8-708">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="f53e8-709">**parameter**: ioctl 호출과 관련된 매개 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-709">**parameter**: Pointerto a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-710">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-710">Return Value</span></span>

- <span data-ttu-id="f53e8-711">**UX_SUCCESS**: (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-711">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-712">**UX_MEMORY_INSUFFICIENT**: (0x12) 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-712">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory.</span></span>
- <span data-ttu-id="f53e8-713">**UX_HOST_CLASS_UNKNOWN**: (0x59) 잘못된 클래스 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-713">**UX_HOST_CLASS_UNKNOWN**: (0x59) Wrong class instance</span></span>
- <span data-ttu-id="f53e8-714">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 알 수 없는 IOCTL 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-714">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="f53e8-715">IOCTL 함수</span><span class="sxs-lookup"><span data-stu-id="f53e8-715">IOCTL functions</span></span>

- <span data-ttu-id="f53e8-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="f53e8-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="f53e8-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="f53e8-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="f53e8-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="f53e8-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="f53e8-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="f53e8-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="f53e8-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="f53e8-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="f53e8-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="f53e8-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="f53e8-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="f53e8-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="f53e8-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="f53e8-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-724">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-724">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a><span data-ttu-id="f53e8-725">ux_host_class_gser_reception_start</span><span class="sxs-lookup"><span data-stu-id="f53e8-725">ux_host_class_gser_reception_start</span></span>

<span data-ttu-id="f53e8-726">일반 직렬 인터페이스에서 수신을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-726">Start reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-727">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-727">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="f53e8-728">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-728">Description</span></span>

<span data-ttu-id="f53e8-729">이 함수는 일반 직렬 클래스 인터페이스에서 수신을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-729">This function starts the reception on the generic serial class interface.</span></span> <span data-ttu-id="f53e8-730">이 함수는 비차단 수신을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-730">This function allows for non-blocking reception.</span></span> <span data-ttu-id="f53e8-731">버퍼를 수신하면 콜백은 애플리케이션으로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-731">When a buffer is received, a callback in invoked into the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-732">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-732">Parameters</span></span>

- <span data-ttu-id="f53e8-733">**gser** gser 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-733">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="f53e8-734">**gser_reception** 수신 매개 변수를 포함하는 구조체입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-734">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-735">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-735">Return Value</span></span>

- <span data-ttu-id="f53e8-736">**UX_SUCCESS** (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-736">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-737">**UX_HOST_CLASS_UNKNOWN** (0x59) 잘못된 클래스 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-737">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="f53e8-738">**UX_ERROR** (0x01) 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-738">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-739">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-739">Example</span></span>

```C
/* Start the reception for gser. AT commands are on interface 2. */
gser_reception.ux_host_class_gser_reception_interface_index =
    UX_DEMO_GSER_AT_INTERFACE;
gser_reception.ux_host_class_gser_reception_block_size =
    UX_DEMO_RECEPTION_BLOCK_SIZE;
gser_reception.ux_host_class_gser_reception_data_buffer =
    gser_reception_buffer;
gser_reception.ux_host_class_gser_reception_data_buffer_size =
    UX_DEMO_RECEPTION_BUFFER_SIZE;
gser_reception.ux_host_class_gser_reception_callback =
    tx_demo_thread_callback;

ux_host_class_gser_reception_start(gser, &gser_reception);
```

## <a name="ux_host_class_gser_reception_stop"></a><span data-ttu-id="f53e8-740">ux_host_class_gser_reception_stop</span><span class="sxs-lookup"><span data-stu-id="f53e8-740">ux_host_class_gser_reception_stop</span></span>

<span data-ttu-id="f53e8-741">일반 직렬 인터페이스에서 수신을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-741">Stop reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="f53e8-742">프로토타입</span><span class="sxs-lookup"><span data-stu-id="f53e8-742">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="f53e8-743">Description</span><span class="sxs-lookup"><span data-stu-id="f53e8-743">Description</span></span>

<span data-ttu-id="f53e8-744">이 함수는 일반 직렬 클래스 인터페이스에서 수신을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-744">This function stops the reception on the generic serial class interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="f53e8-745">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f53e8-745">Parameters</span></span>

- <span data-ttu-id="f53e8-746">**gser** gser 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-746">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="f53e8-747">**gser_reception** 수신 매개 변수를 포함하는 구조체입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-747">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="f53e8-748">반환 값</span><span class="sxs-lookup"><span data-stu-id="f53e8-748">Return Value</span></span>

- <span data-ttu-id="f53e8-749">**UX_SUCCESS** (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-749">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f53e8-750">**UX_HOST_CLASS_UNKNOWN** (0x59) 잘못된 클래스 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-750">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="f53e8-751">**UX_ERROR** (0x01) 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="f53e8-751">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="f53e8-752">예제</span><span class="sxs-lookup"><span data-stu-id="f53e8-752">Example</span></span>

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
