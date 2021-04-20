---
title: 5장 - USBX 호스트 클래스 API
description: USBX 호스트 클래스 API에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: bf5876042e08a59979adcd429917bfc3fbfdbc20
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813435"
---
# <a name="chapter-5---usbx-host-classes-api"></a><span data-ttu-id="14310-103">5장 - USBX 호스트 클래스 API</span><span class="sxs-lookup"><span data-stu-id="14310-103">Chapter 5 - USBX Host Classes API</span></span>

<span data-ttu-id="14310-104">이 장에서는 USBX 호스트 클래스의 모든 노출된 API에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="14310-105">각 클래스를 위한 다음 API에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="14310-106">HID 클래스</span><span class="sxs-lookup"><span data-stu-id="14310-106">HID class</span></span>
- <span data-ttu-id="14310-107">CDC-ACM 클래스</span><span class="sxs-lookup"><span data-stu-id="14310-107">CDC-ACM class</span></span>
- <span data-ttu-id="14310-108">CDC-ECM 클래스</span><span class="sxs-lookup"><span data-stu-id="14310-108">CDC-ECM class</span></span>
- <span data-ttu-id="14310-109">스토리지 클래스</span><span class="sxs-lookup"><span data-stu-id="14310-109">Storage class</span></span>

## <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="14310-110">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="14310-110">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="14310-111">HID 클라이언트를 HID 클래스에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-111">Register a HID client to the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-112">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-112">Prototype</span></span>

```c
UINT ux_host_class_hid_client_register(
    UCHAR *hid_client_name,
    UINT (*hid_client_handler)
    (struct UX_HOST_CLASS_HID_CLIENT_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="14310-113">Description</span><span class="sxs-lookup"><span data-stu-id="14310-113">Description</span></span>

<span data-ttu-id="14310-114">이 함수는 HID 클라이언트를 HID 클래스에 등록하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-114">This function is used to register a HID client to the HID class.</span></span> <span data-ttu-id="14310-115">HID 클래스는 이 디바이스에서 데이터를 요청하기 전에 HID 디바이스와 HID 클라이언트 간에 일치 항목을 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-115">The HID class needs to find a match between a HID device and HID client before requesting data from this device.</span></span>

> [!NOTE]
> <span data-ttu-id="14310-116">hid_client_name의 C 문자열은 NULL로 종료되어야 하며 길이(NULL 종결자 제외)는 **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH** 보다 크지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-116">The C string of hid_client_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-117">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-117">Parameters</span></span>

- <span data-ttu-id="14310-118">**hid_client_name** HID 클라이언트 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-118">**hid_client_name** Pointer to the HID client name.</span></span>
- <span data-ttu-id="14310-119">**hid_client_handler** HID 클라이언트 처리기에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-119">**hid_client_handler** Pointer to the HID client handler.</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-120">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-120">Return Values</span></span>

- <span data-ttu-id="14310-121">**UX_SUCCESS**(0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-121">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="14310-122">**UX_MEMORY_INSUFFICIENT**(0x12) 클라이언트를 위한 메모리 할당에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-122">**UX_MEMORY_INSUFFICIENT** (0x12) Memory allocation for client failed.</span></span>
- <span data-ttu-id="14310-123">**UX_MEMORY_ARRAY_FULL**(0x1a) 최대 클라이언트가 이미 등록되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-123">**UX_MEMORY_ARRAY_FULL** (0x1a) Max clients already registered.</span></span>
- <span data-ttu-id="14310-124">**UX_HOST_CLASS_ALREADY_INSTALLED**(0x58) 이 클래스는 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-124">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) This class already exists</span></span>

### <a name="example"></a><span data-ttu-id="14310-125">예제</span><span class="sxs-lookup"><span data-stu-id="14310-125">Example</span></span>

```c
UINT status;

/* The following example illustrates how to register a HID client, in
this case a USB mouse, to the HID class. */

status = ux_host_class_hid_client_register("ux_host_class_hid_client_mouse",
    ux_host_class_hid_mouse_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_callback_register"></a><span data-ttu-id="14310-126">ux_host_class_hid_report_callback_register</span><span class="sxs-lookup"><span data-stu-id="14310-126">ux_host_class_hid_report_callback_register</span></span>

<span data-ttu-id="14310-127">HID 클래스에서 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-127">Register a callback from the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-128">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-128">Prototype</span></span>

```c
UINT ux_host_class_hid_report_callback_register(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_REPORT_CALLBACK *call_back);
```

### <a name="description"></a><span data-ttu-id="14310-129">Description</span><span class="sxs-lookup"><span data-stu-id="14310-129">Description</span></span>

<span data-ttu-id="14310-130">이 함수는 보고서를 받을 때 HID 클래스에서 HID 클라이언트로 콜백을 등록하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-130">This function is used to register a callback from the HID class to the HID client when a report is received.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-131">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-131">Parameters</span></span>

- <span data-ttu-id="14310-132">**hid** HID 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-132">**hid** Pointer to the HID class instance</span></span>
- <span data-ttu-id="14310-133">**call_back** call_back 구조체에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-133">**call_back** Pointer to the call_back structure</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-134">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-134">Return values</span></span>

- <span data-ttu-id="14310-135">**UX_SUCCESS**(0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-135">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="14310-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN**(0x5b) 잘못된 HID 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Invalid HID instance.</span></span>
- <span data-ttu-id="14310-137">**UX_HOST_CLASS_HID_REPORT_ERROR**(0x79) 보고서 콜백 등록에 오류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-137">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) Error in the report callback registration.</span></span>

### <a name="example"></a><span data-ttu-id="14310-138">예제</span><span class="sxs-lookup"><span data-stu-id="14310-138">Example</span></span>

```c
UINT status;

/* This example illustrates how to register a HID client, in this case a USB mouse, to the HID class. In this case, the HID client is asking the HID class to call the client for each usage received in the HID report. */

call_back.ux_host_class_hid_report_callback_id = 0;
call_back.ux_host_class_hid_report_callback_function = ux_host_class_hid_mouse_callback;

call_back.ux_host_class_hid_report_callback_buffer = UX_NULL;
call_back.ux_host_class_hid_report_callback_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

call_back.ux_host_class_hid_report_callback_length = 0;

status = ux_host_class_hid_report_callback_register(hid, &call_back);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_start"></a><span data-ttu-id="14310-139">ux_host_class_hid_periodic_report_start</span><span class="sxs-lookup"><span data-stu-id="14310-139">ux_host_class_hid_periodic_report_start</span></span>

<span data-ttu-id="14310-140">HID 클래스 인스턴스의 주기적 엔드포인트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-140">Start the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-141">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-141">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_start(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="14310-142">Description</span><span class="sxs-lookup"><span data-stu-id="14310-142">Description</span></span>

<span data-ttu-id="14310-143">이 함수는 이 HID 클라이언트에 바인딩되는 HID 클래스의 인스턴스에 대한 주기적(인터럽트) 엔드포인트를 시작하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-143">This function is used to start the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="14310-144">HID 클래스는 HID 클라이언트가 활성화될 때까지 주기적 엔드포인트를 시작할 수 없으므로 보고서를 받기 위해 엔드포인트를 시작하는 것은 HID 클라이언트에게 맡겨집니다.</span><span class="sxs-lookup"><span data-stu-id="14310-144">The HID class cannot start the periodic endpoint until the HID client is activated and therefore it is left to the HID client to start this endpoint to receive reports.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="14310-145">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-145">Input Parameter</span></span>

- <span data-ttu-id="14310-146">**hid** HID 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-146">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-147">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-147">Return Values</span></span>

- <span data-ttu-id="14310-148">**UX_SUCCESS** (0x00) 주기적 보고를 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-148">**UX_SUCCESS** (0x00) Periodic reporting successfully started.</span></span>
- <span data-ttu-id="14310-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR**(0x7A) 주기적 보고서에 오류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="14310-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN**(0x5b) HID 클래스 인스턴스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="14310-151">예제</span><span class="sxs-lookup"><span data-stu-id="14310-151">Example</span></span>

```c
UINT status;

/* The following example illustrates how to start the periodic
endpoint. */

status = ux_host_class_hid_periodic_report_start(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_stop"></a><span data-ttu-id="14310-152">ux_host_class_hid_periodic_report_stop</span><span class="sxs-lookup"><span data-stu-id="14310-152">ux_host_class_hid_periodic_report_stop</span></span>

<span data-ttu-id="14310-153">HID 클래스 인스턴스의 주기적 엔드포인트를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-153">Stop the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-154">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-154">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_stop(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="14310-155">Description</span><span class="sxs-lookup"><span data-stu-id="14310-155">Description</span></span>

<span data-ttu-id="14310-156">이 함수는 이 HID 클라이언트에 바인딩되는 HID 클래스의 인스턴스에 대한 주기적(인터럽트) 엔드포인트를 중지하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-156">This function is used to stop the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="14310-157">HID 클래스는 HID 클라이언트가 비활성화될 때까지 주기적 엔드포인트를 중지할 수 없으며, 모든 리소스가 해제되므로 이 엔드포인트를 중지하는 것은 HID 클라이언트에 맡겨집니다.</span><span class="sxs-lookup"><span data-stu-id="14310-157">The HID class cannot stop the periodic endpoint until the HID client is deactivated, all its resources freed and therefore it is left to the HID client to stop this endpoint.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="14310-158">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-158">Input Parameter</span></span>

- <span data-ttu-id="14310-159">**hid** HID 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-159">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-160">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-160">Return Values</span></span>

- <span data-ttu-id="14310-161">**UX_SUCCESS**(0x00) 주기적 보고를 성공적으로 중지했습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-161">**UX_SUCCESS** (0x00) Periodic reporting successfully stopped.</span></span>
- <span data-ttu-id="14310-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR**(0x7A) 주기적 보고서에 오류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="14310-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN**(0x5b) HID 클래스 인스턴스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist</span></span>

### <a name="example"></a><span data-ttu-id="14310-164">예제</span><span class="sxs-lookup"><span data-stu-id="14310-164">Example</span></span>

```c
UINT status;

/* The following example illustrates how to stop the periodic endpoint. */

status = ux_host_class_hid_periodic_report_stop(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="14310-165">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="14310-165">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="14310-166">HID 클래스 인스턴스에서 보고서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14310-166">Get a report from a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-167">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-167">Prototype</span></span>

```c
UINT ux_host_class_hid_report_get(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="14310-168">Description</span><span class="sxs-lookup"><span data-stu-id="14310-168">Description</span></span>

<span data-ttu-id="14310-169">이 함수는 주기적 엔드포인트에 의존하지 않고 디바이스에서 직접 보고서를 수신하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-169">This function is used to receive a report directly from the device without relying on the periodic endpoint.</span></span> <span data-ttu-id="14310-170">이 보고서는 제어 엔드포인트에서 제공되지만 처리는 주기적 엔드포인트에서 제공되는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-170">This report is coming from the control endpoint but its treatment is the same as though it were coming on the periodic endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-171">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-171">Parameters</span></span>

- <span data-ttu-id="14310-172">**hid** HID 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-172">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="14310-173">**client_report** HID 클라이언트 보고서에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-173">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-174">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-174">Return Values</span></span>

- <span data-ttu-id="14310-175">**UX_SUCCESS**(0x00) 보고서가 성공적으로 수신되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-175">**UX_SUCCESS** (0x00) The report was successfully received.</span></span>
- <span data-ttu-id="14310-176">**UX_HOST_CLASS_HID_REPORT_ERROR**(0x70) 클라이언트 보고서가 유효하지 않거나 전송 중에 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-176">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="14310-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN**(0x5b) HID 클래스 인스턴스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="14310-178">**UX_BUFFER_OVERFLOW**(0x5d) 제공된 버퍼가 압축되지 않은 보고서를 수용할 만큼 크지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-178">**UX_BUFFER_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="14310-179">예제</span><span class="sxs-lookup"><span data-stu-id="14310-179">Example</span></span>

```c
UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

UINT status;

/* The following example illustrates how to get a report. */

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_get(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="14310-180">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="14310-180">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="14310-181">보고서 보내기</span><span class="sxs-lookup"><span data-stu-id="14310-181">Send a report</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-182">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-182">Prototype</span></span>

```c
UINT ux_host_class_hid_report_set(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="14310-183">Description</span><span class="sxs-lookup"><span data-stu-id="14310-183">Description</span></span>

<span data-ttu-id="14310-184">이 함수는 보고서를 디바이스에 직접 보내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-184">This function is used to send a report directly to the device.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-185">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-185">Parameters</span></span>

- <span data-ttu-id="14310-186">**hid** HID 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-186">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="14310-187">**client_report** HID 클라이언트 보고서에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-187">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-188">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-188">Return Values</span></span>

- <span data-ttu-id="14310-189">**UX_SUCCESS**(0x00) 보고서가 성공적으로 전송되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-189">**UX_SUCCESS** (0x00) The report was successfully sent.</span></span>
- <span data-ttu-id="14310-190">**UX_HOST_CLASS_HID_REPORT_ERROR**(0x70) 클라이언트 보고서가 유효하지 않거나 전송 중에 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-190">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="14310-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN**(0x5b) HID 클래스 인스턴스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="14310-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW**(0x5d) 제공된 버퍼가 압축되지 않은 보고서를 수용할 만큼 크지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="14310-193">예제</span><span class="sxs-lookup"><span data-stu-id="14310-193">Example</span></span>

```c
/* The following example illustrates how to send a report. */

UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_report_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_set(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_buttons_get"></a><span data-ttu-id="14310-194">ux_host_class_hid_mouse_buttons_get</span><span class="sxs-lookup"><span data-stu-id="14310-194">ux_host_class_hid_mouse_buttons_get</span></span>

<span data-ttu-id="14310-195">마우스 단추를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14310-195">Get mouse buttons.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-196">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-196">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_buttons_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    ULONG *mouse_buttons);
```

### <a name="description"></a><span data-ttu-id="14310-197">Description</span><span class="sxs-lookup"><span data-stu-id="14310-197">Description</span></span>

<span data-ttu-id="14310-198">이 함수는 마우스 단추를 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-198">This function is used to get the mouse buttons</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-199">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-199">Parameters</span></span>

- <span data-ttu-id="14310-200">**mouse_instance** HID 마우스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-200">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="14310-201">**mouse_buttons** 반환 단추에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-201">**mouse_buttons** Pointer to the return buttons.</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-202">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-202">Return Values</span></span>

- <span data-ttu-id="14310-203">**UX_SUCCESS**(0x00) 마우스 단추를 성공적으로 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-203">**UX_SUCCESS** (0x00) Mouse button successfully retrieved.</span></span>
- <span data-ttu-id="14310-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN**(0x5b) HID 클래스 인스턴스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="14310-205">예제</span><span class="sxs-lookup"><span data-stu-id="14310-205">Example</span></span>

```c
/* The following example illustrates how to obtain mouse buttons. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

ULONG mouse_buttons;

status = ux_host_class_hid_mouse_button_get(mouse_instance, &mouse_buttons);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_position_get"></a><span data-ttu-id="14310-206">ux_host_class_hid_mouse_position_get</span><span class="sxs-lookup"><span data-stu-id="14310-206">ux_host_class_hid_mouse_position_get</span></span>

<span data-ttu-id="14310-207">마우스 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14310-207">Get mouse position.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-208">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-208">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_position_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    SLONG *mouse_x_position, 
    SLONG *mouse_y_position);
```

### <a name="description"></a><span data-ttu-id="14310-209">Description</span><span class="sxs-lookup"><span data-stu-id="14310-209">Description</span></span>

<span data-ttu-id="14310-210">이 함수는 x 및 y 좌표에서 마우스 위치를 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-210">This function is used to get the mouse position in x & y coordinates.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-211">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-211">Parameters</span></span>

- <span data-ttu-id="14310-212">**mouse_instance** HID 마우스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-212">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="14310-213">**mouse_x_position** X 좌표에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-213">**mouse_x_position** Pointer to the x coordinate.</span></span>
- <span data-ttu-id="14310-214">**mouse_y_position** Y 좌표에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-214">**mouse_y_position** Pointer to the y coordinate.</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-215">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-215">Return Values</span></span>

- <span data-ttu-id="14310-216">**UX_SUCCESS**(0x00) X &amp; Y 좌표를 성공적으로 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-216">**UX_SUCCESS** (0x00) X &amp; Y coordinates successfully retrieved.</span></span>
- <span data-ttu-id="14310-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN**(0x5b) HID 클래스 인스턴스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="14310-218">예제</span><span class="sxs-lookup"><span data-stu-id="14310-218">Example</span></span>

```c
/* The following example illustrates how to obtain mouse coordinates. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

SLONG mouse_x_position;
SLONG mouse_y_position;

status = ux_host_class_hid_mouse_position_get(mouse_instance,
    &mouse_x_position, &mouse_y_position);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_keyboard_key_get"></a><span data-ttu-id="14310-219">ux_host_class_hid_keyboard_key_get</span><span class="sxs-lookup"><span data-stu-id="14310-219">ux_host_class_hid_keyboard_key_get</span></span>

<span data-ttu-id="14310-220">키보드 키 및 상태를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14310-220">Get keyboard key and state.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-221">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-221">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_key_get(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG *keyboard_key, 
    ULONG *keyboard_state);
```

### <a name="description"></a><span data-ttu-id="14310-222">Description</span><span class="sxs-lookup"><span data-stu-id="14310-222">Description</span></span>

<span data-ttu-id="14310-223">이 함수는 키보드 키와 상태를 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-223">This function is used to get the keyboard key and state.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-224">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-224">Parameters</span></span>

- <span data-ttu-id="14310-225">**keyboard_instance** HID 키보드 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-225">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="14310-226">**keyboard_key** 키보드 키 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-226">**keyboard_key** Pointer to keyboard key container.</span></span>
- <span data-ttu-id="14310-227">**keyboard_state** 키보드 상태 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-227">**keyboard_state** Pointer to the keyboard state container.</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-228">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-228">Return Values</span></span>

- <span data-ttu-id="14310-229">**UX_SUCCESS**(0x00) 키와 상태를 성공적으로 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-229">**UX_SUCCESS** (0x00) Key and state successfully retrieved.</span></span>
- <span data-ttu-id="14310-230">**UX_ERROR**(0xff) 보고할 내용이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-230">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="14310-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN**(0x5b) HID 클래스 인스턴스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="14310-232">키보드 상태에 사용할 수 있는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-232">The keyboard state can have the following values.</span></span>

- <span data-ttu-id="14310-233">**UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000</span><span class="sxs-lookup"><span data-stu-id="14310-233">**UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000</span></span>
- <span data-ttu-id="14310-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span><span class="sxs-lookup"><span data-stu-id="14310-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span></span>
- <span data-ttu-id="14310-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002</span><span class="sxs-lookup"><span data-stu-id="14310-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002</span></span>
- <span data-ttu-id="14310-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span><span class="sxs-lookup"><span data-stu-id="14310-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span></span>
- <span data-ttu-id="14310-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span><span class="sxs-lookup"><span data-stu-id="14310-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span></span>
- <span data-ttu-id="14310-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span><span class="sxs-lookup"><span data-stu-id="14310-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span></span>
- <span data-ttu-id="14310-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span><span class="sxs-lookup"><span data-stu-id="14310-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span></span>
- <span data-ttu-id="14310-240">**UX_HID_KEYBOARD_STATE_SHIFT** 0x0300</span><span class="sxs-lookup"><span data-stu-id="14310-240">**UX_HID_KEYBOARD_STATE_SHIFT** 0x0300</span></span>
- <span data-ttu-id="14310-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span><span class="sxs-lookup"><span data-stu-id="14310-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span></span>
- <span data-ttu-id="14310-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span><span class="sxs-lookup"><span data-stu-id="14310-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span></span>
- <span data-ttu-id="14310-243">**UX_HID_KEYBOARD_STATE_ALT** 0x0a00</span><span class="sxs-lookup"><span data-stu-id="14310-243">**UX_HID_KEYBOARD_STATE_ALT** 0x0a00</span></span>
- <span data-ttu-id="14310-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span><span class="sxs-lookup"><span data-stu-id="14310-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span></span>
- <span data-ttu-id="14310-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000</span><span class="sxs-lookup"><span data-stu-id="14310-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000</span></span>
- <span data-ttu-id="14310-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span><span class="sxs-lookup"><span data-stu-id="14310-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span></span>
- <span data-ttu-id="14310-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span><span class="sxs-lookup"><span data-stu-id="14310-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span></span>
- <span data-ttu-id="14310-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span><span class="sxs-lookup"><span data-stu-id="14310-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span></span>
- <span data-ttu-id="14310-249">**UX_HID_KEYBOARD_STATE_GUI** 0xa000</span><span class="sxs-lookup"><span data-stu-id="14310-249">**UX_HID_KEYBOARD_STATE_GUI** 0xa000</span></span>

### <a name="example"></a><span data-ttu-id="14310-250">예제</span><span class="sxs-lookup"><span data-stu-id="14310-250">Example</span></span>

```c
while (1)
{

    /* Get a key/state from the keyboard. */
    status = ux_host_class_hid_keyboard_key_get(keyboard,
        &keyboard_char, &keyboard_state);

    /* Check if there is something. */
    if (status == UX_SUCCESS)
    {

        #ifdef UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE
            if (keyboard_state & UX_HID_KEYBOARD_STATE_KEY_UP)
            {
                /* The key was released. */
            } else
            {
                /* The key was pressed. */
            }
        #endif

        /* We have a character in the queue. */
        keyboard_queue[keyboard_queue_index] = (UCHAR) keyboard_char;

        /* Can we accept more ? */
        if(keyboard_queue_index < 1024)
            keyboard_queue_index++;
    }

    tx_thread_sleep(10);

}
```

## <a name="ux_host_class_hid_keyboard_ioctl"></a><span data-ttu-id="14310-251">ux_host_class_hid_keyboard_ioctl</span><span class="sxs-lookup"><span data-stu-id="14310-251">ux_host_class_hid_keyboard_ioctl</span></span>

<span data-ttu-id="14310-252">HID 키보드에 대해 IOCTL 함수를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-252">Perform an IOCTL function to the HID keyboard.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-253">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-253">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_ioctl(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG ioctl_function, VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="14310-254">Description</span><span class="sxs-lookup"><span data-stu-id="14310-254">Description</span></span>

<span data-ttu-id="14310-255">이 함수는 HID 키보드에 대해 특정 ioctl 함수를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-255">This function performs a specific ioctl function to the HID keyboard.</span></span> <span data-ttu-id="14310-256">호출이 차단되고 오류가 있거나 명령이 완료된 경우에만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-256">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-257">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-257">Parameters</span></span>

- <span data-ttu-id="14310-258">**keyboard_instance** HID 키보드 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-258">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="14310-259">**ioctl_function** 수행할 ioctl 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-259">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="14310-260">허용되는 ioctl 함수 중 하나에 대해서는 아래 표를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14310-260">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="14310-261">**parameter** ioctl에 특정한 매개 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-261">**parameter** Pointer to a parameter specific to the ioctl.</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-262">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-262">Return Values</span></span>

- <span data-ttu-id="14310-263">**UX_SUCCESS**(0x00) ioctl 함수가 성공적으로 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-263">**UX_SUCCESS** (0x00) The ioctl function completed successfully.</span></span>
- <span data-ttu-id="14310-264">**UX_FUNCTION_NOT_SUPPORTED**(0x54) 알 수 없는 IOCTL 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-264">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="14310-265">IOCTL 함수</span><span class="sxs-lookup"><span data-stu-id="14310-265">IOCTL functions</span></span>

- <span data-ttu-id="14310-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="14310-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span></span>
- <span data-ttu-id="14310-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span><span class="sxs-lookup"><span data-stu-id="14310-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span></span>
- <span data-ttu-id="14310-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span><span class="sxs-lookup"><span data-stu-id="14310-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span></span>

### <a name="example--change-keyboard-layout"></a><span data-ttu-id="14310-269">예 – 키보드 레이아웃 변경</span><span class="sxs-lookup"><span data-stu-id="14310-269">Example – change keyboard layout</span></span>

```c
UINT status;

/* This example shows usage of the SET_LAYOUT IOCTL function.
    USBX receives raw key values from the device (these raw values
    are defined in the HID usage table specification) and optionally
    decodes them for application usage. The decoding is performed
    based on a set of arrays that act as maps – which array is used
    depends on the raw key value (i.e. keypad and non-keypad) and
    the current state of the keyboard (i.e. shift, caps lock, etc.). */

/* When the shift condition is not present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_unshifted_map[] =
{
    0,0,0,0,
    'a','b','c','d','e','f','g',
    'h','i','j','k','l','m','n',
    'o','p','q','r','s','t',
    'u','v','w','x','y','z',
    '1','2','3','4','5','6','7','8','9','0',
    0x0d,0x1b,0x08,0x07,0x20,'-','=','[',']',
    '\\','#',';',0x27,'`',',','.','/',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When the shift condition is present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_shifted_map[] =
{
    0,0,0,0,
    'A','B','C','D','E','F','G',
    'H','I','J','K','L','M','N',
    'O','P','Q','R','S','T',
    'U','V','W','X','Y','Z',
    '!','@','#','$','%','^','&','*','(',')',
    0x0d,0x1b,0x08,0x07,0x20,'_','+','{','}',
    '|','~',':','"','~','<','>','?',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When numlock is on and the raw key value is within the keypad
    value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_numlock_on_map[] =
{
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
};

/* When numlock is off and the raw key value is within the keypad value
    range, this array will be used to decode the raw key value. */
static UCHAR keyboard_layout_raw_to_numlock_off_map[] =
{
    '/','*','-','+',
    0x0d,0xcf,0xd0,0xd1,0xcb,'5',0xcd,0xc7,0xc8,0xc9,0xd2,0xd3,'\\',0x00,0x
    00,'=',
};

/* Specify the keyboard layout for USBX usage. */
static UX_HOST_CLASS_HID_KEYBOARD_LAYOUT keyboard_layout =
{
    keyboard_layout_raw_to_shifted_map,
    keyboard_layout_raw_to_unshifted_map,
    keyboard_layout_raw_to_numlock_on_map,
    keyboard_layout_raw_to_numlock_off_map,
    /* The maximum raw key value. Values larger than this are discarded. */
    UX_HID_KEYBOARD_KEYS_UPPER_RANGE,
    /* The raw key value for the letter 'a'. */
    UX_HID_KEYBOARD_KEY_LETTER_A,
    /* The raw key value for the letter 'z'. */
    UX_HID_KEYBOARD_KEY_LETTER_Z,
    /* The lower range raw key value for keypad keys - inclusive. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_LOWER_RANGE,
    /* The upper range raw key value for keypad keys. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_UPPER_RANGE
};

/* Call the IOCTL function to change the keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_SET_LAYOUT, (VOID *)&keyboard_layout);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="example--disable-keyboard-key-decode"></a><span data-ttu-id="14310-270">예 – 키보드 키 디코드 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="14310-270">Example – disable keyboard key decode</span></span>

```c
UINT status;

/* The following example illustrates IOCTL function of Disable key decode from keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_DISABLE_KEYS_DECODE, UX_NULL);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_remote_control_usage_get"></a><span data-ttu-id="14310-271">ux_host_class_hid_remote_control_usage_get</span><span class="sxs-lookup"><span data-stu-id="14310-271">ux_host_class_hid_remote_control_usage_get</span></span>

<span data-ttu-id="14310-272">원격 제어 사용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14310-272">Get remote control usage</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-273">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-273">Prototype</span></span>

```c
UINT ux_host_class_hid_remote_control_usage_get(
    UX_HOST_CLASS_HID_REMOTE_CONTROL *remote_control_instance,
    LONG *usage, 
    ULONG *value);
```

### <a name="description"></a><span data-ttu-id="14310-274">Description</span><span class="sxs-lookup"><span data-stu-id="14310-274">Description</span></span>

<span data-ttu-id="14310-275">이 함수는 원격 제어 사용을 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-275">This function is used to get the remote control usages.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-276">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-276">Parameters</span></span>

- <span data-ttu-id="14310-277">**remote_control_instance** HID 원격 제어 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-277">**remote_control_instance** Pointer to the HID remote control instance.</span></span>
- <span data-ttu-id="14310-278">**usage** 사용에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-278">**usage** Pointer to the usage.</span></span>
- <span data-ttu-id="14310-279">**value** 사용을 위한 값에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-279">**value** Pointer to the value for the usage.</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-280">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-280">Return Values</span></span>

- <span data-ttu-id="14310-281">**UX_SUCCESS**(0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-281">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="14310-282">**UX_ERROR**(0xff) 보고할 내용이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-282">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="14310-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN**(0x5b) HID 클래스 인스턴스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="14310-284">가능한 모든 사용의 목록이 너무 길어서 이 사용자 가이드에 맞지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-284">The list of all possible usages is too long to fit in this user guide.</span></span> <span data-ttu-id="14310-285">전체 설명을 위해 ux_host_class_hid.h에는 가능한 값의 전체 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-285">For a full description, the ux_host_class_hid.h has the entire set of possible values.</span></span>

### <a name="example"></a><span data-ttu-id="14310-286">예제</span><span class="sxs-lookup"><span data-stu-id="14310-286">Example</span></span>

```c
/* Read usages and values as the user changes the vol/bass/treble buttons on the speaker */

while (remote_control != UX_NULL)
{
    status = ux_host_class_hid_remote_control_usage_get(remote_control, &usage, &value);
    if (status == UX_SUCCESS)
    {
        /* We have something coming from the HID remote control,
        we filter the usage here and only allow the
        volume usage which can be VOLUME, VOLUME_INCREMENT or VOLUME_DECREMENT */
        switch(usage)
        {
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_INCREMENT :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_DECREMENT :

            if (value<0x80)
            {
                if (current_volume + audio_control.ux_host_class_audio_control_res < 0xffff)
                    current_volume = current_volume + audio_control.ux_host_class_audio_control_res;
                } else {
                if (current_volume > audio_control.ux_host_class_audio_control_res)
                    current_volume = current_volumeaudio_control.ux_host_class_audio_control_res;
            }

            audio_control.ux_host_class_audio_control_channel = 1;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            audio_control.ux_host_class_audio_control_channel = 2;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            break;

        }
    }
    tx_thread_sleep(10);

}
```

### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="14310-287">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="14310-287">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="14310-288">cdc_acm 인터페이스에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-288">Read from the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-289">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-289">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_read(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="14310-290">Description</span><span class="sxs-lookup"><span data-stu-id="14310-290">Description</span></span>

<span data-ttu-id="14310-291">이 함수는 cdc_acm 인터페이스에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-291">This function reads from the cdc_acm interface.</span></span> <span data-ttu-id="14310-292">호출이 차단되고 오류가 있거나 전송이 완료된 경우에만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-292">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-293">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-293">Parameters</span></span>

- <span data-ttu-id="14310-294">**cdc_acm** cdc_acm 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-294">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="14310-295">**data_pointer** 데이터 페이로드의 버퍼 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-295">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="14310-296">**requested_length** 수신될 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-296">**requested_length** Length to be received.</span></span>
- <span data-ttu-id="14310-297">**actual_length** 실제로 수신된 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-297">**actual_length** Length actually received.</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-298">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-298">Return Values</span></span>

- <span data-ttu-id="14310-299">**UX_SUCCESS**(0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-299">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="14310-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN**(0x5b) cdc_acm 인스턴스가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="14310-301">**UX_TRANSFER_TIMEOUT**(0x5c) 전송 제한 시간이 초과되었습니다. 읽기가 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-301">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="14310-302">예제</span><span class="sxs-lookup"><span data-stu-id="14310-302">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_read(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_write"></a><span data-ttu-id="14310-303">ux_host_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="14310-303">ux_host_class_cdc_acm_write</span></span>

<span data-ttu-id="14310-304">cdc_acm 인터페이스에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="14310-304">Write to the cdc_acm interface</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-305">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-305">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_write(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer, 
    ULONG requested_length, 
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="14310-306">Description</span><span class="sxs-lookup"><span data-stu-id="14310-306">Description</span></span>

<span data-ttu-id="14310-307">이 함수는 cdc_acm 인터페이스에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="14310-307">This function writes to the cdc_acm interface.</span></span> <span data-ttu-id="14310-308">호출이 차단되고 오류가 있거나 전송이 완료된 경우에만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-308">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-309">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-309">Parameters</span></span>

- <span data-ttu-id="14310-310">**cdc_acm** cdc_acm 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-310">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="14310-311">**data_pointer** 데이터 페이로드의 버퍼 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-311">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="14310-312">**requested_length** 전송될 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-312">**requested_length** Length to be sent.</span></span>
- <span data-ttu-id="14310-313">**actual_length** 실제로 전송된 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-313">**actual_length** Length actually sent.</span></span>

### <a name="return-values"></a><span data-ttu-id="14310-314">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-314">Return Values</span></span>

- <span data-ttu-id="14310-315">**UX_SUCCESS**(0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-315">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="14310-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN**(0x5b) cdc_acm 인스턴스가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="14310-317">**UX_TRANSFER_TIMEOUT**(0x5c) 전송 제한 시간이 초과되었습니다. 쓰기가 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-317">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="14310-318">예제</span><span class="sxs-lookup"><span data-stu-id="14310-318">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_write(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_ioctl"></a><span data-ttu-id="14310-319">ux_host_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="14310-319">ux_host_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="14310-320">cdc_acm 인터페이스에 대한 IOCTL 함수를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-320">Perform an IOCTL function to the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-321">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-321">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_ioctl(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function, 
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="14310-322">Description</span><span class="sxs-lookup"><span data-stu-id="14310-322">Description</span></span>

<span data-ttu-id="14310-323">이 함수는 cdc_acm 인터페이스에 대한 특정 ioctl 함수를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-323">This function performs a specific ioctl function to the cdc_acm interface.</span></span> <span data-ttu-id="14310-324">호출이 차단되고 오류가 있거나 명령이 완료된 경우에만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="14310-324">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-325">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-325">Parameters</span></span>

- <span data-ttu-id="14310-326">**cdc_acm** cdc_acm 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-326">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="14310-327">**ioctl_function** 수행할 ioctl 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-327">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="14310-328">허용되는 ioctl 함수 중 하나에 대해서는 아래 표를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14310-328">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="14310-329">**parameter** ioctl 호출과 관련된 매개 변수에 대한 포인터</span><span class="sxs-lookup"><span data-stu-id="14310-329">**parameter** Pointer to a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="14310-330">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-330">Return Value</span></span>

- <span data-ttu-id="14310-331">**UX_SUCCESS**(0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-331">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="14310-332">**UX_MEMORY_INSUFFICIENT**(0x12) 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-332">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory.</span></span>
- <span data-ttu-id="14310-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN**(0x5b) CDC-ACM 인스턴스가 유효하지 않은 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) CDC-ACM instance is in an invalid state.</span></span>
- <span data-ttu-id="14310-334">**UX_FUNCTION_NOT_SUPPORTED**(0x54) 알 수 없는 IOCTL 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-334">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="14310-335">IOCTL 함수:</span><span class="sxs-lookup"><span data-stu-id="14310-335">IOCTL functions:</span></span>

- <span data-ttu-id="14310-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="14310-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="14310-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="14310-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="14310-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="14310-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="14310-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="14310-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="14310-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="14310-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="14310-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="14310-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="14310-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="14310-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="14310-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="14310-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_ioctl(cdc_acm,
    UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="14310-344">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="14310-344">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="14310-345">디바이스에서 데이터의 백그라운드 수신을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-345">Begins background reception of data from the device.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-346">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-346">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_start(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="14310-347">Description</span><span class="sxs-lookup"><span data-stu-id="14310-347">Description</span></span>

<span data-ttu-id="14310-348">이 함수는 USBX가 백그라운드에서 계속해서 디바이스에서 데이터를 읽도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-348">This function causes USBX to continuously read data from the device in the background.</span></span> <span data-ttu-id="14310-349">각 트랜잭션이 완료되면 애플리케이션에서 트랜잭션 데이터의 추가 처리를 수행할 수 있도록 **cdc_acm_reception** 에 지정된 콜백을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-349">Upon completion of each transaction, the callback specified in **cdc_acm_reception** is invoked so the application may perform further processing of the transaction's data.</span></span>

> [!NOTE]
> <span data-ttu-id="14310-350">백그라운드 수신을 사용하는 동안에는 **ux_host_class_cdc_acm_read** 를 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-350">**ux_host_class_cdc_acm_read** must not be used while background reception is in use.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-351">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-351">Parameters</span></span>

- <span data-ttu-id="14310-352">**cdc_acm** cdc_acm 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-352">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="14310-353">**cdc_acm_reception** 백그라운드 수신 동작을 정의하는 값을 포함하는 매개 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-353">**cdc_acm_reception** Pointer to parameter that contains values defining behavior of background reception.</span></span> <span data-ttu-id="14310-354">이 매개 변수의 레이아웃은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-354">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="14310-355">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-355">Return Value</span></span>

- <span data-ttu-id="14310-356">**UX_SUCCESS**(0x00) 백그라운드 수신을 성공적으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-356">**UX_SUCCESS** (0x00) Background reception successfully started.</span></span>
- <span data-ttu-id="14310-357">**UX_HOST_CLASS_INSTANCE _UNKNOWN**(0x5b) 잘못된 클래스 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-357">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Setup the background reception parameter. */

/* Set the desired max read size for each transaction.
    For example, if this value is 64, then the maximum amount of
    data received from the device in a single transaction is 64.
    If the amount of data received from the device is less than this value,
    the callback will still be invoked with the actual amount of data received. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_block_size = block_size;

/* Set the buffer where the data from the device is read to. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer = cdc_acm_reception_buffer;

/* Set the size of the data reception buffer.
    Note that this should be at least as large as ux_host_class_cdc_acm_reception_block_size. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer_size = cdc_acm_reception_buffer_size;

/* Set the callback that is to be invoked upon each reception transfer completion. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_callback = reception_callback;

/* Start background reception using the values we defined in the reception parameter. */
status = ux_host_class_cdc_acm_reception_start(cdc_acm_host_data, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully started. */
```

## <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="14310-358">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="14310-358">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="14310-359">패킷의 백그라운드 수신을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-359">Stops background reception of packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="14310-360">프로토타입</span><span class="sxs-lookup"><span data-stu-id="14310-360">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_stop(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="14310-361">Description</span><span class="sxs-lookup"><span data-stu-id="14310-361">Description</span></span>

<span data-ttu-id="14310-362">이 함수를 통해 USBX가 이전에 **ux_host_class_cdc_acm_reception_start** 에서 시작한 백그라운드 수신을 중지도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="14310-362">This function causes USBX to stop background reception previously started by **ux_host_class_cdc_acm_reception_start**.</span></span>

### <a name="parameters"></a><span data-ttu-id="14310-363">매개 변수</span><span class="sxs-lookup"><span data-stu-id="14310-363">Parameters</span></span>

- <span data-ttu-id="14310-364">**cdc_acm** cdc_acm 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-364">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="14310-365">**cdc_acm_reception** 백그라운드 수신을 시작하는 데 사용된 것과 동일한 매개 변수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-365">**cdc_acm_reception** Pointer to the same parameter that was used to start background reception.</span></span> <span data-ttu-id="14310-366">이 매개 변수의 레이아웃은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-366">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(
            struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm, UINT status,
            UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="14310-367">반환 값</span><span class="sxs-lookup"><span data-stu-id="14310-367">Return Value</span></span>

- <span data-ttu-id="14310-368">**UX_SUCCESS**(0x00) 백그라운드 수신을 성공적으로 중지했습니다.</span><span class="sxs-lookup"><span data-stu-id="14310-368">**UX_SUCCESS** (0x00) Background reception successfully stopped.</span></span>
- <span data-ttu-id="14310-369">**UX_HOST_CLASS_INSTANCE _UNKNOWN**(0x5b) 잘못된 클래스 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="14310-369">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Stop background reception. The reception parameter should be the same
    that was passed to ux_host_class_cdc_acm_reception_start. */
status = ux_host_class_cdc_acm_reception_stop(cdc_acm, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully stopped. */
```
