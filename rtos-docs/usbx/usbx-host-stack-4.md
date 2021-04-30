---
title: 4장 - USBX 호스트 서비스 설명
description: USBX 호스트 서비스에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d730658c07f3cd7cec8c75a47818314bdc63f35a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813272"
---
# <a name="chapter-4---description-of-usbx-host-services"></a><span data-ttu-id="ef69e-103">4장 - USBX 호스트 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="ef69e-103">Chapter 4 - Description of USBX Host Services</span></span>

## <a name="ux_host_stack_initialize"></a><span data-ttu-id="ef69e-104">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="ef69e-104">ux_host_stack_initialize</span></span>

<span data-ttu-id="ef69e-105">호스트 작업을 위해 USBX를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-105">Initialize USBX for host operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-106">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-106">Prototype</span></span>

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a><span data-ttu-id="ef69e-107">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-107">Description</span></span>

<span data-ttu-id="ef69e-108">이 함수는 USB 호스트 스택을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-108">This function will initialize the USB host stack.</span></span> <span data-ttu-id="ef69e-109">제공된 메모리 영역은 USBX 내부 사용을 위해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-109">The supplied memory area will be setup for USBX internal use.</span></span> <span data-ttu-id="ef69e-110">호스트 컨트롤러 및 클래스 등록에 사용하도록 USBX가 준비되면 UX_SUCCESS가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-110">If UX_SUCCESS is returned, USBX is ready for host controller and class registration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="ef69e-111">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-111">Input Parameter</span></span>

- <span data-ttu-id="ef69e-112">**system_change_function** 디바이스 변경을 애플리케이션에 알리기 위한 선택적 콜백 루틴에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-112">**system_change_function** Pointer to optional callback routine for notifying application of device changes.</span></span>

### <a name="return-value"></a><span data-ttu-id="ef69e-113">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-113">Return Value</span></span>

- <span data-ttu-id="ef69e-114">**UX_SUCCESS** (0x00) 성공적으로 초기화했습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-114">**UX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="ef69e-115">**UX_MEMORY_INSUFFICIENT** (0x12) 메모리 할당에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-115">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-116">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-116">Example</span></span>

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="ef69e-117">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="ef69e-117">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="ef69e-118">엔드포인트에 대한 이전 요청에 연결된 모든 트랜잭션을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-118">Abort all transactions attached to a transfer request for an endpoint.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-119">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-119">Prototype</span></span>

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="ef69e-120">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-120">Description</span></span>

<span data-ttu-id="ef69e-121">이 함수는 엔드포인트에 연결된 특정 이전 요청에 대해 활성 또는 보류 상태인 모든 트랜잭션을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-121">This function will cancel all transactions active or pending for a specific transfer request attached to an endpoint.</span></span> <span data-ttu-id="ef69e-122">이전 요청에 콜백 함수가 연결된 경우 콜백 함수가 UX_TRANSACTION_ABORTED 상태로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-122">It the transfer request has a callback function attached, the callback function will be called with the UX_TRANSACTION_ABORTED status.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="ef69e-123">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-123">Input Parameter</span></span>

- <span data-ttu-id="ef69e-124">**endpoint** 엔드포인트에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-124">**endpoint** Pointer to an endpoint.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-125">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-125">Return Values</span></span>

- <span data-ttu-id="ef69e-126">**UX_SUCCESS** (0x00) 오류가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-126">**UX_SUCCESS** (0x00) No errors.</span></span>
- <span data-ttu-id="ef69e-127">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) 엔드포인트 핸들이 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-127">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint handle is not valid.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-128">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-128">Example</span></span>

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a><span data-ttu-id="ef69e-129">ux_host_stack_class_get</span><span class="sxs-lookup"><span data-stu-id="ef69e-129">ux_host_stack_class_get</span></span>

<span data-ttu-id="ef69e-130">클래스 컨테이너에 대한 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-130">Get the pointer to a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-131">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-131">Prototype</span></span>

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a><span data-ttu-id="ef69e-132">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-132">Description</span></span>

<span data-ttu-id="ef69e-133">이 함수는 클래스 컨테이너에 대한 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-133">This function returns a pointer to the class container.</span></span> <span data-ttu-id="ef69e-134">클래스 또는 애플리케이션에서 디바이스를 열려는 경우 클래스는 USB 스택에서 해당 컨테이너를 가져와서 인스턴스를 검색해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-134">A class needs to obtain its container from the USB stack to search for instances when a class or an application wants to open a device.</span></span>

> [!NOTE]
> <span data-ttu-id="ef69e-135">class_name의 C 문자열은 NULL로 종료되어야 하며 길이(NULL 종결자 제외)는 UX_MAX_CLASS_NAME_LENGTH보다 크지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-135">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than UX_MAX_CLASS_NAME_LENGTH.</span></span>

### <a name="parameters"></a><span data-ttu-id="ef69e-136">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-136">Parameters</span></span>

- <span data-ttu-id="ef69e-137">**class_name** 클래스 이름에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-137">**class_name** Pointer to the class name.</span></span>
- <span data-ttu-id="ef69e-138">**class** 클래스 이름에 대해 클래스 컨테이너가 포함된 함수 호출로 업데이트되는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-138">**class** A pointer updated by the function call that contains the class container for the name of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-139">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-139">Return Values</span></span>

- <span data-ttu-id="ef69e-140">**UX_SUCCESS** (0x00) 오류가 없습니다. 반환 시 클래스 필드는 클래스 컨테이너에 대한 포인터와 함께 파일링됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-140">**UX_SUCCESS** (0x00) No errors, on return the class field is filed with the pointer to the class container.</span></span>
- <span data-ttu-id="ef69e-141">**UX_HOST_CLASS_UNKNOWN** (0x59) 스택에서 클래스를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-141">**UX_HOST_CLASS_UNKNOWN** (0x59) Class is unknown by the stack.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-142">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-142">Example</span></span>

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a><span data-ttu-id="ef69e-143">ux_host_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="ef69e-143">ux_host_stack_class_register</span></span>

<span data-ttu-id="ef69e-144">USB 스택에 USB 클래스를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-144">Register a USB class to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-145">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-145">Prototype</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="ef69e-146">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-146">Description</span></span>

<span data-ttu-id="ef69e-147">이 함수는 USB 스택에 USB 클래스를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-147">This function registers a USB class to the USB stack.</span></span> <span data-ttu-id="ef69e-148">클래스는 다음과 같은 명령을 전송하기 위해 USB 스택의 진입점을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-148">The class must specify an entry point for the USB stack to send commands such as the following.</span></span>

- <span data-ttu-id="ef69e-149">**UX_HOST_CLASS_COMMAND_QUERY**</span><span class="sxs-lookup"><span data-stu-id="ef69e-149">**UX_HOST_CLASS_COMMAND_QUERY**</span></span>
- <span data-ttu-id="ef69e-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span><span class="sxs-lookup"><span data-stu-id="ef69e-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span></span>
- <span data-ttu-id="ef69e-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span><span class="sxs-lookup"><span data-stu-id="ef69e-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span></span>

> [!NOTE]
> <span data-ttu-id="ef69e-152">*class_name* 의 C 문자열은 NULL로 종료되어야 하며 길이(NULL 종결자 제외)는 **UX_MAX_CLASS_NAME_LENGTH** 보다 크지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-152">The C string of *class_name* must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="ef69e-153">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-153">Parameters</span></span>

- <span data-ttu-id="ef69e-154">**class_name** 클래스 이름에 대한 포인터입니다. 유효한 항목은 USBX의 USB 클래스 아래에 있는 ux_system_initialize.c 파일에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-154">**class_name** Pointer to the name of the class, valid entries are found in the file ux_system_initialize.c under the USB Classes of USBX.</span></span>
- <span data-ttu-id="ef69e-155">**class_entry_address** 클래스의 항목 함수 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-155">**class_entry_address** Address of the entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-156">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-156">Return Values</span></span>

- <span data-ttu-id="ef69e-157">**UX_SUCCESS** (0x00) 클래스가 성공적으로 설치되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-157">**UX_SUCCESS** (0x00) Class installed successfully.</span></span>
- <span data-ttu-id="ef69e-158">**UX_MEMORY_ARRAY_FULL** (0x1a) 이 클래스를 저장할 메모리가 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-158">**UX_MEMORY_ARRAY_FULL** (0x1a) No more memory to store this class.</span></span>
- <span data-ttu-id="ef69e-159">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) 호스트 클래스가 이미 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-159">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Host class already installed.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-160">예:</span><span class="sxs-lookup"><span data-stu-id="ef69e-160">Example:</span></span>

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a><span data-ttu-id="ef69e-161">ux_host_stack_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="ef69e-161">ux_host_stack_class_instance_create</span></span>

<span data-ttu-id="ef69e-162">클래스 컨테이너에 대해 새 클래스 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-162">Create a new class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-163">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-163">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="ef69e-164">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-164">Description</span></span>

<span data-ttu-id="ef69e-165">이 함수는 클래스 컨테이너에 대해 새 클래스 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-165">This function creates a new class instance for a class container.</span></span> <span data-ttu-id="ef69e-166">클래스의 인스턴스는 클래스 복잡성을 줄이기 위해 클래스 코드에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-166">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="ef69e-167">대신 각 클래스 인스턴스는 주 스택에 있는 클래스 컨테이너에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-167">Rather, each class instance is attached to the class container located in the main stack.</span></span>

### <a name="parameters"></a><span data-ttu-id="ef69e-168">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-168">Parameters</span></span>

- <span data-ttu-id="ef69e-169">**class** 클래스 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-169">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="ef69e-170">**class_instance** 생성할 클래스 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-170">**class_instance** Pointer to the class instance to be created.</span></span>

### <a name="return-value"></a><span data-ttu-id="ef69e-171">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-171">Return Value</span></span>

- <span data-ttu-id="ef69e-172">**UX_SUCCESS** (0x00) 클래스 인스턴스가 클래스 컨테이너에 연결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-172">**UX_SUCCESS** (0x00) The class instance was attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-173">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-173">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a><span data-ttu-id="ef69e-174">ux_host_stack_class_instance_destroy</span><span class="sxs-lookup"><span data-stu-id="ef69e-174">ux_host_stack_class_instance_destroy</span></span>

<span data-ttu-id="ef69e-175">클래스 컨테이너에 대한 클래스 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-175">Destroy a class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-176">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-176">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="ef69e-177">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-177">Description</span></span>

<span data-ttu-id="ef69e-178">이 함수는 클래스 컨테이너에 대한 클래스 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-178">This function destroys a class instance for a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="ef69e-179">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-179">Parameters</span></span>

- <span data-ttu-id="ef69e-180">**class** 클래스 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-180">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="ef69e-181">**class_instance** 삭제할 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-181">**class_instance** Pointer to the instance to destroy.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-182">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-182">Return Values</span></span>

- <span data-ttu-id="ef69e-183">**UX_SUCCESS** (0x00) 클래스 인스턴스가 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-183">**UX_SUCCESS** (0x00) The class instance was destroyed.</span></span>
- <span data-ttu-id="ef69e-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) 클래스 인스턴스가 클래스 컨테이너에 연결되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The class instance is not attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-185">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-185">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a><span data-ttu-id="ef69e-186">ux_host_stack_class_instance_get</span><span class="sxs-lookup"><span data-stu-id="ef69e-186">ux_host_stack_class_instance_get</span></span>

<span data-ttu-id="ef69e-187">특정 클래스에 대한 클래스 인스턴스 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-187">Get a class instance pointer for a specific class.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-188">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-188">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a><span data-ttu-id="ef69e-189">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-189">Description</span></span>

<span data-ttu-id="ef69e-190">이 함수는 특정 클래스에 대한 클래스 인스턴스 포인터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-190">This function returns a class instance pointer for a specific class.</span></span> <span data-ttu-id="ef69e-191">클래스의 인스턴스는 클래스 복잡성을 줄이기 위해 클래스 코드에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-191">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="ef69e-192">대신 각 클래스 인스턴스가 클래스 컨테이너에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-192">Rather, each class instance is attached to the class container.</span></span> <span data-ttu-id="ef69e-193">이 함수는 클래스 컨테이너 내에서 클래스 인스턴스를 검색하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-193">This function is used to search for class instances within a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="ef69e-194">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-194">Parameters</span></span>

- <span data-ttu-id="ef69e-195">**class** 클래스 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-195">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="ef69e-196">**class_index** 컨테이너에 연결된 클래스 목록 내에서 함수 호출에 사용되는 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-196">**class_index** An index to be used by the function call within the list of attached classes to the container.</span></span>
- <span data-ttu-id="ef69e-197">**class_instance** 함수 호출에 의해 반환될 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-197">**class_instance** Pointer to the instance to be returned by the function call.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-198">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-198">Return Values</span></span>

- <span data-ttu-id="ef69e-199">**UX_SUCCESS** (0x00) 클래스 인스턴스를 찾았습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-199">**UX_SUCCESS** (0x00) The class instance was found.</span></span>

- <span data-ttu-id="ef69e-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) 클래스 컨테이너에 연결된 클래스 인스턴스가 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) There are no more class instances attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-201">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-201">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="ef69e-202">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="ef69e-202">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="ef69e-203">구성 컨테이너에 대한 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-203">Get a pointer to a configuration container.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-204">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-204">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="ef69e-205">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-205">Description</span></span>

<span data-ttu-id="ef69e-206">이 함수는 디바이스 핸들 및 구성 인덱스를 기준으로 구성 컨테이너를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-206">This function returns a configuration container based on a device handle and a configuration index.</span></span>

### <a name="parameters"></a><span data-ttu-id="ef69e-207">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-207">Parameters</span></span>

- <span data-ttu-id="ef69e-208">**device** 요청된 구성을 소유하는 디바이스 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-208">**device** Pointer to the device container that owns the configuration requested.</span></span>
- <span data-ttu-id="ef69e-209">**configuration_index** 검색할 구성의 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-209">**configuration_index** Index of the configuration to be searched.</span></span>
- <span data-ttu-id="ef69e-210">**configuration** 반환할 구성 컨테이너에 대한 포인터의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-210">**configuration** Address of the pointer to the configuration container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-211">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-211">Return Values</span></span>

- <span data-ttu-id="ef69e-212">**UX_SUCCESS** (0x00) 구성을 찾았습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-212">**UX_SUCCESS** (0x00) The configuration was found.</span></span>
- <span data-ttu-id="ef69e-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) 디바이스 컨테이너가 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) The device container does not exist.</span></span>
- <span data-ttu-id="ef69e-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 인덱스에 대한 구성 핸들이 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle for the index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-215">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-215">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="ef69e-216">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="ef69e-216">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="ef69e-217">디바이스에 대해 특정 구성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-217">Select a specific configuration for a device.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-218">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-218">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="ef69e-219">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-219">Description</span></span>

<span data-ttu-id="ef69e-220">이 함수는 디바이스에 대해 특정 구성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-220">This function selects a specific configuration for a device.</span></span> <span data-ttu-id="ef69e-221">이 구성이 디바이스에 설정되면 기본적으로 각 디바이스 인터페이스 및 관된 대체 설정 0이 디바이스에서 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-221">When this configuration is set to the device, by default, each device interface and its associated alternate setting 0 is activated on the device.</span></span> <span data-ttu-id="ef69e-222">디바이스/인터페이스 클래스가 특정 인터페이스 설정을 변경하려는 경우 **ux_host_stack_interface_setting_select** 서비스 호출을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-222">If the device/interface class wishes to change the setting of a particular interface, it needs to issue a **ux_host_stack_interface_setting_select** service call.</span></span>

### <a name="parameters"></a><span data-ttu-id="ef69e-223">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-223">Parameters</span></span>

- <span data-ttu-id="ef69e-224">**configuration** 이 디바이스에 대해 사용할 구성 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-224">**configuration** Pointer to the configuration container that is to be enabled for this device.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-225">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-225">Return Values</span></span>

- <span data-ttu-id="ef69e-226">**UX_SUCCESS** (0x00) 구성을 성공적으로 선택했습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-226">**UX_SUCCESS** (0x00) The configuration selection was successful.</span></span>
- <span data-ttu-id="ef69e-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 구성 핸들이 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle does not exist.</span></span>
- <span data-ttu-id="ef69e-228">**UX_OVER_CURRENT_CONDITION** (0x43) 이 구성에 대한 버스에 과전류 상태가 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-228">**UX_OVER_CURRENT_CONDITION** (0x43) An over current condition exists on the bus for this configuration.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-229">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-229">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a><span data-ttu-id="ef69e-230">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="ef69e-230">ux_host_stack_device_get</span></span>

<span data-ttu-id="ef69e-231">디바이스 컨테이너에 대한 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-231">Get a pointer to a device container.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-232">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-232">Prototype</span></span>

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a><span data-ttu-id="ef69e-233">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-233">Description</span></span>

<span data-ttu-id="ef69e-234">이 함수는 해당 인덱스를 기반으로 디바이스 컨테이너를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-234">This function returns a device container based on its index.</span></span> <span data-ttu-id="ef69e-235">디바이스 인덱스는 0부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-235">The device index starts with 0.</span></span> <span data-ttu-id="ef69e-236">컨트롤러가 여러 개 있을 수 있고 바이트 인덱스로는 충분하지 않을 수 있기 때문에 인덱스는 ULONG입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-236">Note that the index is a ULONG because we could have several controllers and a byte index might not be enough.</span></span> <span data-ttu-id="ef69e-237">디바이스 인덱스를 버스 관련 디바이스 주소와 혼동해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-237">The device index should not be confused with the device address that is bus specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="ef69e-238">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-238">Parameters</span></span>

- <span data-ttu-id="ef69e-239">**device_index** 디바이스의 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-239">**device_index** Index of the device.</span></span>
- <span data-ttu-id="ef69e-240">**device** 반환할 디바이스 컨테이너에 대한 포인터 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-240">**device** Address of the pointer for the device container to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-241">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-241">Return Values</span></span>

- <span data-ttu-id="ef69e-242">**UX_SUCCESS** (0x00) 디바이스 컨테이너가 존재하고 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-242">**UX_SUCCESS** (0x00) The device container exists and is returned</span></span>
- <span data-ttu-id="ef69e-243">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) 알 수 없는 디바이스입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-243">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) Device unknown</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-244">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-244">Example</span></span>

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a><span data-ttu-id="ef69e-245">ux_host_stack_interface_endpoint_get</span><span class="sxs-lookup"><span data-stu-id="ef69e-245">ux_host_stack_interface_endpoint_get</span></span>

<span data-ttu-id="ef69e-246">엔드포인트 컨테이너를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-246">Get an endpoint container.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-247">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-247">Prototype</span></span>

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="ef69e-248">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-248">Description</span></span>

<span data-ttu-id="ef69e-249">이 함수는 인터페이스 핸들 및 엔드포인트 인덱스를 기반으로 엔드포인트 컨테이너를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-249">This function returns an endpoint container based on the interface handle and an endpoint index.</span></span> <span data-ttu-id="ef69e-250">인터페이스의 대체 설정이 선택되었거나 엔드포인트 검색 전 기본 설정이 사용된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-250">It is assumed that the alternate setting for the interface has been selected or the default setting is being used prior to the endpoint(s) being searched.</span></span>

### <a name="parameters"></a><span data-ttu-id="ef69e-251">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-251">Parameters</span></span>

- <span data-ttu-id="ef69e-252">**interface** 요청된 엔드포인트가 포함된 인터페이스 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-252">**interface** Pointer to the interface container that contains the endpoint requested.</span></span>
- <span data-ttu-id="ef69e-253">**endpoint_index** 이 인터페이스에 있는 엔드포인트의 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-253">**endpoint_index** Index of the endpoint in this interface.</span></span>
- <span data-ttu-id="ef69e-254">**endpoint** 반환할 엔드포인트 컨테이너의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-254">**endpoint** Address of the endpoint container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-255">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-255">Return Values</span></span>

- <span data-ttu-id="ef69e-256">**UX_SUCCESS** (0x00) 엔드포인트 컨테이너가 존재하고 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-256">**UX_SUCCESS** (0x00) The endpoint container exists and is returned.</span></span>
- <span data-ttu-id="ef69e-257">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) 지정된 인터페이스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-257">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Interface specified does not exist.</span></span>
- <span data-ttu-id="ef69e-258">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) 엔드포인트 인덱스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-258">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-259">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-259">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="ef69e-260">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="ef69e-260">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="ef69e-261">USB 스택에 USB 컨트롤러를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-261">Register a USB controller to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-262">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-262">Prototype</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a><span data-ttu-id="ef69e-263">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-263">Description</span></span>

<span data-ttu-id="ef69e-264">이 함수는 USB 스택에 USB 컨트롤러를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-264">This function registers a USB controller to the USB stack.</span></span> <span data-ttu-id="ef69e-265">주로 이 컨트롤러에서 사용되는 메모리를 할당하고 초기화 명령을 컨트롤러에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-265">It mainly allocates the memory used by this controller and passes the initialization command to the controller.</span></span>

### <a name="parameters"></a><span data-ttu-id="ef69e-266">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-266">Parameters</span></span>

- <span data-ttu-id="ef69e-267">**hcd_name** 호스트 컨트롤러의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-267">**hcd_name** Name of the host controller</span></span>
- <span data-ttu-id="ef69e-268">**hcd_function** 초기화를 담당하는 호스트 컨트롤러의 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-268">**hcd_function** The function in the host controller responsible for the initialization.</span></span>
- <span data-ttu-id="ef69e-269">**hcd_param1** hcd에 사용되는 IO 또는 메모리 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-269">**hcd_param1** The IO or memory resource used by the hcd.</span></span>
- <span data-ttu-id="ef69e-270">**hcd_param2** 호스트 컨트롤러에 사용되는 IRQ입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-270">**hcd_param2** The IRQ used by the host controller.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-271">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-271">Return Values</span></span>

- <span data-ttu-id="ef69e-272">**UX_SUCCESS** (0x00) 컨트롤러가 올바르게 초기화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-272">**UX_SUCCESS** (0x00) The controller was initialized properly.</span></span>
- <span data-ttu-id="ef69e-273">**UX_MEMORY_INSUFFICIENT** (0x12) 이 컨트롤러의 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-273">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory for this controller.</span></span>
- <span data-ttu-id="ef69e-274">**UX_PORT_RESET_FAILED** (0x31) 컨트롤러를 초기화하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-274">**UX_PORT_RESET_FAILED** (0x31) The reset of the controller failed.</span></span>
- <span data-ttu-id="ef69e-275">**UX_CONTROLLER_INIT_FAILED** (0x32) 컨트롤러를 올바르게 초기화하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-275">**UX_CONTROLLER_INIT_FAILED** (0x32) The controller failed to initialize properly.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-276">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-276">Example</span></span>

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a><span data-ttu-id="ef69e-277">ux_host_stack_configuration_interface_get</span><span class="sxs-lookup"><span data-stu-id="ef69e-277">ux_host_stack_configuration_interface_get</span></span>

<span data-ttu-id="ef69e-278">인터페이스 컨테이너 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-278">Get an interface container pointer.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-279">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-279">Prototype</span></span>

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a><span data-ttu-id="ef69e-280">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-280">Description</span></span>

<span data-ttu-id="ef69e-281">이 함수는 구성 핸들, 인터페이스 인덱스 및 대체 설정 인덱스를 기반으로 인터페이스 컨테이너를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-281">This function returns an interface container based on a configuration handle, an interface index, and an alternate setting index.</span></span>

### <a name="parameters"></a><span data-ttu-id="ef69e-282">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-282">Parameters</span></span>

- <span data-ttu-id="ef69e-283">**configuration** 인터페이스를 소유하는 구성 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-283">**configuration** Pointer to the configuration container that owns the interface.</span></span>
- <span data-ttu-id="ef69e-284">**interface_index** 검색할 인터페이스 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-284">**interface_index** Interface index to be searched.</span></span>
- <span data-ttu-id="ef69e-285">**alternate_setting_index** 검색할 인터페이스 내의 대체 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-285">**alternate_setting_index** Alternate setting within the interface to search.</span></span>
- <span data-ttu-id="ef69e-286">**interface** 반환할 인터페이스 컨테이너 포인터의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-286">**interface** Address of the interface container pointer to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-287">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-287">Return Values</span></span>

- <span data-ttu-id="ef69e-288">**UX_SUCCESS** (0x00) 인터페이스 인덱스 및 대체 설정에 대한 인터페이스 컨테이너를 찾아 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-288">**UX_SUCCESS** (0x00) The interface container for the interface index and the alternate setting was found and returned.</span></span>
- <span data-ttu-id="ef69e-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) 구성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration does not exist.</span></span>
- <span data-ttu-id="ef69e-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) 인터페이스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-291">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-291">Example</span></span>

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="ef69e-292">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="ef69e-292">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="ef69e-293">인터페이스에 대한 대체 설정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-293">Select an alternate setting for an interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-294">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-294">Prototype</span></span>

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a><span data-ttu-id="ef69e-295">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-295">Description</span></span>

<span data-ttu-id="ef69e-296">이 함수는 선택한 구성에 속하는 지정된 인터페이스에 대해 특정 대체 설정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-296">This function selects a specific alternate setting for a given interface belonging to the selected configuration.</span></span> <span data-ttu-id="ef69e-297">이 함수는 기본 대체 설정에서 새 설정으로 변경하거나 기본 대체 설정으로 돌아가는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-297">This function is used to change from the default alternate setting to a new setting or to go back to the default alternate setting.</span></span> <span data-ttu-id="ef69e-298">새 대체 설정을 선택하면 이전 엔드포인트 특성이 유효하지 않으므로 다시 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-298">When a new alternate setting is selected, the previous endpoint characteristics are invalid and should be reloaded.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="ef69e-299">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-299">Input Parameter</span></span>

- <span data-ttu-id="ef69e-300">**interface** 대체 설정을 선택할 인터페이스 컨테이너에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-300">**interface** Pointer to the interface container whose alternate setting is to be selected.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-301">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-301">Return Values</span></span>

- <span data-ttu-id="ef69e-302">**UX_SUCCESS** (0x00) 이 인터페이스의 대체 설정이 성공적으로 선택되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-302">**UX_SUCCESS** (0x00) The alternate setting for this interface has been successfully selected.</span></span>
- <span data-ttu-id="ef69e-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) 인터페이스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-304">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-304">Example</span></span>

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a><span data-ttu-id="ef69e-305">ux_host_stack_transfer_request_abort</span><span class="sxs-lookup"><span data-stu-id="ef69e-305">ux_host_stack_transfer_request_abort</span></span>

<span data-ttu-id="ef69e-306">보류 중인 이전 요청을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-306">Abort a pending transfer request.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-307">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-307">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="ef69e-308">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-308">Description</span></span>

<span data-ttu-id="ef69e-309">이 함수는 이전에 제출된 보류 중인 이전 요청을 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-309">This function aborts a pending transfer request that has been previously submitted.</span></span> <span data-ttu-id="ef69e-310">이 함수는 특정 이전 요청만 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-310">This function only cancels a specific transfer request.</span></span> <span data-ttu-id="ef69e-311">이 함수에 대한 콜백은 UX_TRANSFER REQUEST_STATUS_ABORT 상태를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-311">The call back to the function will have the UX_TRANSFER REQUEST_STATUS_ABORT status.</span></span>

### <a name="parameters"></a><span data-ttu-id="ef69e-312">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-312">Parameters</span></span>

- <span data-ttu-id="ef69e-313">**transfer request** 중단할 이전 요청에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-313">**transfer request** Pointer to the transfer request to be aborted.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-314">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-314">Return Values</span></span>

- <span data-ttu-id="ef69e-315">**UX_SUCCESS** (0x00) 이 이전 요청에 대한 USB 전송이 취소되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-315">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was canceled.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-316">예제</span><span class="sxs-lookup"><span data-stu-id="ef69e-316">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="ef69e-317">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="ef69e-317">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="ef69e-318">USB 전송을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-318">Request a USB transfer.</span></span>

### <a name="prototype"></a><span data-ttu-id="ef69e-319">프로토타입</span><span class="sxs-lookup"><span data-stu-id="ef69e-319">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="ef69e-320">Description</span><span class="sxs-lookup"><span data-stu-id="ef69e-320">Description</span></span>

<span data-ttu-id="ef69e-321">이 함수는 USB 트랜잭션을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-321">This function performs a USB transaction.</span></span> <span data-ttu-id="ef69e-322">항목에서 이전 요청은 이 트랜잭션에 대해 선택된 엔드포인트 파이프 및 전송과 관련된 매개 변수(데이터 페이로드, 트랜잭션 길이)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-322">On entry the transfer request gives the endpoint pipe selected for this transaction and the parameters associated with the transfer (data payload, length of transaction).</span></span> <span data-ttu-id="ef69e-323">제어 파이프의 경우 트랜잭션이 중단되고 제어 전송의 3단계가 완료되었거나 이전 오류가 있는 경우에만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-323">For Control pipe, the transaction is blocking and will only return when the three phases of the control transfer have been completed or if there is a previous error.</span></span> <span data-ttu-id="ef69e-324">다른 파이프의 경우 USB 스택이 USB에 트랜잭션을 예약하지만 완료될 때까지 대기하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-324">For other pipes, the USB stack will schedule the transaction on the USB but will not wait for its completion.</span></span> <span data-ttu-id="ef69e-325">비중단 파이프에 대한 각 이전 요청은 완료 루틴 처리기를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-325">Each transfer request for non-blocking pipes has to specify a completion routine handler.</span></span>

<span data-ttu-id="ef69e-326">함수 호출이 반환되면 트랜잭션 결과가 포함되므로 이전 요청의 상태를 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-326">When the function call returns, the status of the transfer request should be examined as it contains the result of the transaction.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="ef69e-327">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef69e-327">Input Parameter</span></span>

- <span data-ttu-id="ef69e-328">**transfer_request** 이전 요청에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-328">**transfer_request** Pointer to the transfer request.</span></span> <span data-ttu-id="ef69e-329">이전 요청에는 전송에 요구된 모든 필수 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-329">The transfer request contains all the necessary information required for the transfer.</span></span>

### <a name="return-values"></a><span data-ttu-id="ef69e-330">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef69e-330">Return Values</span></span>

- <span data-ttu-id="ef69e-331">**UX_SUCCESS** (0x00) 이 이전 요청에 대한 USB 전송이 올바르게 예약되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-331">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was scheduled properly.</span></span> <span data-ttu-id="ef69e-332">이전 요청이 완료되면 이전 요청의 상태 코드를 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-332">The status code of the transfer request should be examined when the transfer request completes.</span></span>
- <span data-ttu-id="ef69e-333">**UX_MEMORY_INSUFFICIENT** (0x12) 필요한 컨트롤러 리소스를 할당할 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-333">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to allocate the necessary controller resources.</span></span>
- <span data-ttu-id="ef69e-334">**UX_TRANSFER_NOT_READY** (0x25) 잘못된 디바이스 상태입니다. ATTACHED, ADDRESSED 또는 CONFIGURED여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef69e-334">**UX_TRANSFER_NOT_READY** (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>

### <a name="example"></a><span data-ttu-id="ef69e-335">예제:</span><span class="sxs-lookup"><span data-stu-id="ef69e-335">Example:</span></span>

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
