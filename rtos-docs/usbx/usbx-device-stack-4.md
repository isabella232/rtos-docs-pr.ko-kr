---
title: 챕터 4 - USBX 디바이스 서비스 설명
description: USBX 디바이스 서비스에 대해 알아봅니다.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812954"
---
# <a name="description-of-usbx-device-services"></a><span data-ttu-id="eb449-103">USBX 디바이스 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="eb449-103">Description of USBX Device Services</span></span>

### <a name="ux_device_stack_alternate_setting_get"></a><span data-ttu-id="eb449-104">ux_device_stack_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="eb449-104">ux_device_stack_alternate_setting_get</span></span>

<span data-ttu-id="eb449-105">인터페이스 값에 대한 현재 대체 설정 가져오기</span><span class="sxs-lookup"><span data-stu-id="eb449-105">Get current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-106">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-106">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a><span data-ttu-id="eb449-107">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-107">Description</span></span>

<span data-ttu-id="eb449-108">이 함수는 USB 호스트에서 특정 인터페이스 값에 대한 현재 대체 설정을 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-108">This function is used by the USB host to obtain the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="eb449-109">이 함수는 **GET_INTERFACE** 요청을 받을 때 컨트롤러 드라이버에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-109">It is called by the controller driver when a **GET_INTERFACE** request is received.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb449-110">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-110">Input Parameter</span></span>

- <span data-ttu-id="eb449-111">**Interface_value** 현재 대체 설정이 쿼리되는 인터페이스 값</span><span class="sxs-lookup"><span data-stu-id="eb449-111">**Interface_value** Interface value for which the current alternate setting is queried</span></span>

### <a name="return-values"></a><span data-ttu-id="eb449-112">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-112">Return Values</span></span>

- <span data-ttu-id="eb449-113">**UX_SUCCESS** (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-113">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="eb449-114">**UX_ERROR** (0xFF) 잘못된 인터페이스 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-114">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-115">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-115">Example</span></span>

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a><span data-ttu-id="eb449-116">ux_device_stack_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="eb449-116">ux_device_stack_alternate_setting_set</span></span>

<span data-ttu-id="eb449-117">인터페이스 값에 대한 현재 대체 설정 지정</span><span class="sxs-lookup"><span data-stu-id="eb449-117">Set current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-118">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-118">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="eb449-119">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-119">Description</span></span>

<span data-ttu-id="eb449-120">이 함수는 USB 호스트에서 특정 인터페이스 값에 대한 현재 대체 설정을 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-120">This function is used by the USB host to set the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="eb449-121">이 함수는 **SET_INTERFACE** 요청을 받을 때 컨트롤러 드라이버에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-121">It is called by the controller driver when a **SET_INTERFACE** request is received.</span></span> <span data-ttu-id="eb449-122">**SET_INTERFACE** 가 완료되면 대체 설정 값이 클래스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-122">When the **SET_INTERFACE** is completed, the values of the alternate settings are applied to the class.</span></span>

<span data-ttu-id="eb449-123">디바이스 스택은 대체 설정의 변경 내용을 반영하기 위해 이 인터페이스를 소유하는 클래스에 대한 **UX_SLAVE_CLASS_COMMAND_CHANGE** 를 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-123">The device stack will issue a **UX_SLAVE_CLASS_COMMAND_CHANGE** to the class that owns this interface to reflect the change of alternate setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb449-124">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-124">Parameters</span></span>

- <span data-ttu-id="eb449-125">**interface_value**: 현재 대체 설정이 지정된 인터페이스 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-125">**interface_value**: Interface value for which the current alternate setting is set.</span></span>
- <span data-ttu-id="eb449-126">**alternate_setting_value**: 새 대체 설정 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-126">**alternate_setting_value**: The new alternate setting value.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb449-127">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-127">Return Values</span></span>

- <span data-ttu-id="eb449-128">**UX_SUCCESS** (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-128">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="eb449-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) 인터페이스가 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) No interface attached.</span></span>
- <span data-ttu-id="eb449-130">**UX_FUNCTION_NOT_SUPPORTED** (0x54) 디바이스가 구성되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-130">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Device is not configured.</span></span>
- <span data-ttu-id="eb449-131">**UX_ERROR** (0xFF) 잘못된 인터페이스 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-131">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-132">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-132">Example</span></span>

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a><span data-ttu-id="eb449-133">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="eb449-133">ux_device_stack_class_register</span></span>

<span data-ttu-id="eb449-134">새 USB 디바이스 클래스 등록</span><span class="sxs-lookup"><span data-stu-id="eb449-134">Register a new USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-135">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-135">Prototype</span></span>

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="eb449-136">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-136">Description</span></span>

<span data-ttu-id="eb449-137">이 함수는 애플리케이션에서 새 USB 디바이스 클래스를 등록하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-137">This function is used by the application to register a new USB device class.</span></span> <span data-ttu-id="eb449-138">이를 등록하면 클래스의 인스턴스가 아닌 클래스 컨테이너가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-138">This registration starts a class container and not an instance of the class.</span></span> <span data-ttu-id="eb449-139">클래스는 활성 스레드를 포함하고 특정 인터페이스에 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-139">A class should have an active thread and be attached to a specific interface.</span></span>

<span data-ttu-id="eb449-140">일부 클래스는 매개 변수 또는 매개 변수 목록을 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-140">Some classes expect a parameter or parameter list.</span></span> <span data-ttu-id="eb449-141">예를 들어 디바이스 저장소 클래스는 에뮬레이트하려는 저장 디바이스의 기하 도형을 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-141">For instance, the device storage class would expect the geometry of the storage device it is trying to emulate.</span></span> <span data-ttu-id="eb449-142">따라서 매개 변수 필드는 클래스 요구 사항에 따라 달라지며, 값 또는 클래스 값으로 채워진 구조체에 대한 포인터일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-142">The parameter field is therefore dependent on the class requirement and can be a value or a pointer to a structure filled with the class values.</span></span>

> [!NOTE]
> <span data-ttu-id="eb449-143">class_name의 C 문자열은 NULL로 끝나야 하며 길이(NULL 종결자 제외)는 **UX_MAX_CLASS_NAME_LENGTH** 보다 크지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-143">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb449-144">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-144">Parameters</span></span>

- <span data-ttu-id="eb449-145">**class_name** 클래스 이름</span><span class="sxs-lookup"><span data-stu-id="eb449-145">**class_name** Class Name</span></span>
- <span data-ttu-id="eb449-146">**class_entry_function** 클래스의 항목 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-146">**class_entry_function** The entry function of the class.</span></span>
- <span data-ttu-id="eb449-147">**configuration_number** 이 클래스가 연결된 구성 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-147">**configuration_number** The configuration number this class is attached to.</span></span>
- <span data-ttu-id="eb449-148">**interface_number** 이 클래스가 연결된 인터페이스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-148">**interface_number** The interface number this class is attached to.</span></span>
- <span data-ttu-id="eb449-149">**parameter** 클래스 관련 매개 변수 목록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-149">**parameter** A pointer to a class specific parameter list.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb449-150">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-150">Return Values</span></span>

- <span data-ttu-id="eb449-151">**UX_SUCCESS** (0x00) 클래스가 등록되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-151">**UX_SUCCESS** (0x00) The class was registered</span></span>
- <span data-ttu-id="eb449-152">**UX_MEMORY_INSUFFICIENT** (0x12) 클래스 테이블에 남아 있는 항목이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-152">**UX_MEMORY_INSUFFICIENT** (0x12) No entries left in class table.</span></span>
- <span data-ttu-id="eb449-153">**UX_THREAD_ERROR** (0x16) 클래스 스레드를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-153">**UX_THREAD_ERROR** (0x16) Cannot create a class thread.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-154">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-154">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a><span data-ttu-id="eb449-155">ux_device_stack_class_unregister</span><span class="sxs-lookup"><span data-stu-id="eb449-155">ux_device_stack_class_unregister</span></span>

<span data-ttu-id="eb449-156">USB 디바이스 클래스 등록 취소</span><span class="sxs-lookup"><span data-stu-id="eb449-156">Unregister a USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-157">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-157">Prototype</span></span>

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a><span data-ttu-id="eb449-158">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-158">Description</span></span>

<span data-ttu-id="eb449-159">이 함수는 애플리케이션에서 USB 디바이스 클래스의 등록을 취소하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-159">This function is used by the application to unregister a USB device class.</span></span>

> [!NOTE]
> <span data-ttu-id="eb449-160">class_name의 C 문자열은 NULL로 끝나야 하며 길이(NULL 종결자 제외)는 **UX_MAX_CLASS_NAME_LENGTH** 보다 크지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-160">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb449-161">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-161">Parameters</span></span>

- <span data-ttu-id="eb449-162">**class_name**: 클래스 이름</span><span class="sxs-lookup"><span data-stu-id="eb449-162">**class_name**: Class Name</span></span>
- <span data-ttu-id="eb449-163">**class_entry_function**: 클래스의 항목 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-163">**class_entry_function**: The entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb449-164">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-164">Return Values</span></span>

- <span data-ttu-id="eb449-165">**UX_SUCCESS** (0x00) 클래스의 등록이 취소되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-165">**UX_SUCCESS** (0x00) The class was unregistered.</span></span>
- <span data-ttu-id="eb449-166">**UX_NO_CLASS_MATCH** (0x57) 클래스가 등록되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-166">**UX_NO_CLASS_MATCH** (0x57) The class isn't registered.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-167">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-167">Example</span></span>

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a><span data-ttu-id="eb449-168">ux_device_stack_configuration_get</span><span class="sxs-lookup"><span data-stu-id="eb449-168">ux_device_stack_configuration_get</span></span>

<span data-ttu-id="eb449-169">현재 구성 가져오기</span><span class="sxs-lookup"><span data-stu-id="eb449-169">Get the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-170">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-170">Prototype</span></span>

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a><span data-ttu-id="eb449-171">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-171">Description</span></span>

<span data-ttu-id="eb449-172">이 함수는 호스트가 디바이스에서 실행 중인 현재 구성을 가져오는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-172">This function is used by the host to obtain the current configuration running in the device.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb449-173">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-173">Input Parameter</span></span>

<span data-ttu-id="eb449-174">없음</span><span class="sxs-lookup"><span data-stu-id="eb449-174">None</span></span>

### <a name="return-value"></a><span data-ttu-id="eb449-175">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-175">Return Value</span></span>

- <span data-ttu-id="eb449-176">**UX_SUCCESS** (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-176">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-177">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-177">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="eb449-178">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="eb449-178">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="eb449-179">현재 구성 설정</span><span class="sxs-lookup"><span data-stu-id="eb449-179">Set the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-180">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-180">Prototype</span></span>

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a><span data-ttu-id="eb449-181">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-181">Description</span></span>

<span data-ttu-id="eb449-182">이 함수는 호스트가 디바이스에서 실행 중인 현재 구성을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-182">This function is used by the host to set the current configuration running in the device.</span></span> <span data-ttu-id="eb449-183">이 명령이 수신되면 USB 디바이스 스택은 이 구성에 연결된 각 인터페이스의 대체 설정 0을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-183">Upon reception of this command, the USB device stack will activate the alternate setting 0 of each interface connected to this configuration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb449-184">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-184">Input Parameter</span></span>

- <span data-ttu-id="eb449-185">**configuration_value** 호스트가 선택한 구성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-185">**configuration_value** The configuration value selected by the host.</span></span>

### <a name="return-value"></a><span data-ttu-id="eb449-186">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-186">Return Value</span></span>

- <span data-ttu-id="eb449-187">**UX_SUCCESS** (0x00) 구성을 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-187">**UX_SUCCESS** (0x00) The configuration was successfully set.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-188">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-188">Example</span></span>

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="eb449-189">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="eb449-189">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="eb449-190">호스트에 설명자 보내기</span><span class="sxs-lookup"><span data-stu-id="eb449-190">Send a descriptor to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-191">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-191">Prototype</span></span>

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="eb449-192">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-192">Description</span></span>

<span data-ttu-id="eb449-193">이 함수는 디바이스 쪽에서 호스트로 설명자를 반환하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-193">This function is used by the device side to return a descriptor to the host.</span></span> <span data-ttu-id="eb449-194">이 설명자는 디바이스 설명자, 구성 설명자 또는 문자열 설명자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-194">This descriptor can be a device descriptor, a configuration descriptor or a string descriptor.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb449-195">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-195">Parameters</span></span>

- <span data-ttu-id="eb449-196">**descriptor_type**: 설명자의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-196">**descriptor_type**: The type of the descriptor.</span></span> <span data-ttu-id="eb449-197">다음 값 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-197">Must be one of the following values.</span></span>
  - <span data-ttu-id="eb449-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="eb449-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="eb449-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="eb449-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="eb449-200">**UX_STRING_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="eb449-200">**UX_STRING_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="eb449-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="eb449-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="eb449-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="eb449-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span></span>
- <span data-ttu-id="eb449-203">**request_index**: 설명자의 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-203">**request_index**: The index of the descriptor.</span></span>
- <span data-ttu-id="eb449-204">**host_length**: 호스트에 필요한 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-204">**host_length**: The length required by the host.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb449-205">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-205">Return Values</span></span>

- <span data-ttu-id="eb449-206">**UX_SUCCESS** (0x00) 데이터 전송이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-206">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="eb449-207">**UX_ERROR** (0xFF) 전송이 완료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-207">**UX_ERROR** (0xFF) The transfer was not completed.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-208">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-208">Example</span></span>

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="eb449-209">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="eb449-209">ux_device_stack_disconnect</span></span>

<span data-ttu-id="eb449-210">디바이스 스택 연결 끊기</span><span class="sxs-lookup"><span data-stu-id="eb449-210">Disconnect device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-211">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-211">Prototype</span></span>

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a><span data-ttu-id="eb449-212">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-212">Description</span></span>

<span data-ttu-id="eb449-213">디바이스 연결이 끊어질 때 VBUS 관리자가 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-213">The VBUS manager calls this function when there is a device disconnection.</span></span> <span data-ttu-id="eb449-214">디바이스 스택은 이 디바이스에 등록된 모든 클래스에 알리고 이후에 모든 디바이스 리소스를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-214">The device stack will inform all classes registered to this device and will thereafter release all the device resources.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb449-215">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-215">Input Parameter</span></span>

<span data-ttu-id="eb449-216">없음</span><span class="sxs-lookup"><span data-stu-id="eb449-216">None</span></span>

### <a name="return-value"></a><span data-ttu-id="eb449-217">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-217">Return Value</span></span>

- <span data-ttu-id="eb449-218">**UX_SUCCESS** (0x00) 디바이스의 연결이 끊어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-218">**UX_SUCCESS** (0x00) The device was disconnected.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-219">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-219">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="eb449-220">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="eb449-220">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="eb449-221">엔드포인트 정지 조건 요청</span><span class="sxs-lookup"><span data-stu-id="eb449-221">Request endpoint Stall condition</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-222">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-222">Prototype</span></span>

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a><span data-ttu-id="eb449-223">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-223">Description</span></span>

<span data-ttu-id="eb449-224">이 함수는 엔드포인트가 호스트에 정지 조건을 반환해야 하는 경우 USB 디바이스 클래스에 의해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-224">This function is called by the USB device class when an endpoint should return a Stall condition to the host.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb449-225">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-225">Input Parameter</span></span>

- <span data-ttu-id="eb449-226">**엔드포인트** 정지 조건이 요청된 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-226">**endpoint** The endpoint on which the Stall condition is requested.</span></span>

### <a name="return-value"></a><span data-ttu-id="eb449-227">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-227">Return Value</span></span>

- <span data-ttu-id="eb449-228">**UX_SUCCESS** (0x00) 이 작업을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-228">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eb449-229">**UX_ERROR** (0xFF) 디바이스 상태가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-229">**UX_ERROR** (0xFF) The device is in an invalid state.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-230">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-230">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="eb449-231">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="eb449-231">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="eb449-232">호스트의 절전 모드 해제</span><span class="sxs-lookup"><span data-stu-id="eb449-232">Wake up the host</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-233">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-233">Prototype</span></span>

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a><span data-ttu-id="eb449-234">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-234">Description</span></span>

<span data-ttu-id="eb449-235">이 함수는 디바이스가 호스트의 절전 모드를 해제하려고 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-235">This function is called when the device wants to wake up the host.</span></span> <span data-ttu-id="eb449-236">이 명령은 디바이스가 일시 중단 모드인 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-236">This command is only valid when the device is in suspend mode.</span></span> <span data-ttu-id="eb449-237">USB 호스트의 절전 모드를 해제할 시기를 결정하는 것은 디바이스 애플리케이션에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-237">It is up to the device application to decide when it wants to wake up the USB host.</span></span> <span data-ttu-id="eb449-238">예를 들어 USB 모뎀은 전화 회선에서 링 신호를 감지한 경우 호스트의 절전 모드를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-238">For instance, a USB modem can wake up a host when it detects a RING signal on the telephone line.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb449-239">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-239">Input Parameter</span></span>

<span data-ttu-id="eb449-240">없음</span><span class="sxs-lookup"><span data-stu-id="eb449-240">None</span></span>

### <a name="return-values"></a><span data-ttu-id="eb449-241">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-241">Return values</span></span>

- <span data-ttu-id="eb449-242">**UX_SUCCESS** (0x00) 호출을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-242">**UX_SUCCESS** (0x00) The call was successful.</span></span>
- <span data-ttu-id="eb449-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54) 호출이 실패했습니다(디바이스가 일시 중단 모드가 아닐 수 있음).</span><span class="sxs-lookup"><span data-stu-id="eb449-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54) The call failed (the device was probably not in the suspended mode).</span></span>

### <a name="example"></a><span data-ttu-id="eb449-244">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-244">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a><span data-ttu-id="eb449-245">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="eb449-245">ux_device_stack_initialize</span></span>

<span data-ttu-id="eb449-246">USB 디바이스 스택 초기화</span><span class="sxs-lookup"><span data-stu-id="eb449-246">Initialize USB device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-247">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-247">Prototype</span></span>

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a><span data-ttu-id="eb449-248">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-248">Description</span></span>

<span data-ttu-id="eb449-249">이 함수는 애플리케이션이 USB 디바이스 스택을 초기화할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-249">This function is called by the application to initialize the USB device stack.</span></span> <span data-ttu-id="eb449-250">이 함수는 모든 클래스나 컨트롤러를 초기화하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-250">It does not initialize any classes or any controllers.</span></span> <span data-ttu-id="eb449-251">별도의 함수 호출을 사용하여 이 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-251">This should be done with separate function calls.</span></span> <span data-ttu-id="eb449-252">이 호출은 주로 USB 기능을 위한 디바이스 프레임워크를 스택에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-252">This call mainly provides the stack with the device framework for the USB function.</span></span> <span data-ttu-id="eb449-253">각 속도에 대해 완전히 별개의 디바이스 프레임워크를 사용할 수 있는 높은 속도와 전체 속도를 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-253">It supports both high and full speeds with the possibility to have completely separate device framework for each speed.</span></span> <span data-ttu-id="eb449-254">문자열 프레임워크와 여러 언어가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-254">String framework and multiple languages are supported.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb449-255">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-255">Parameters</span></span>

- <span data-ttu-id="eb449-256">**device_framework_high_speed**: 고속 프레임워크에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-256">**device_framework_high_speed**: Pointer to the high speed framework.</span></span>
- <span data-ttu-id="eb449-257">**device_framework_length_high_speed**: 고속 프레임워크의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-257">**device_framework_length_high_speed**: Length of the high speed framework.</span></span>
- <span data-ttu-id="eb449-258">**device_framework_full_speed**: 전체 속도 프레임워크에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-258">**device_framework_full_speed**: Pointer to the full speed framework.</span></span>
- <span data-ttu-id="eb449-259">**device_framework_length_full_speed**: 전체 속도 프레임워크의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-259">**device_framework_length_full_speed**: Length of the full speed framework.</span></span>
- <span data-ttu-id="eb449-260">**string_framework**: 문자열 프레임워크에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-260">**string_framework**: Pointer to string framework.</span></span>
- <span data-ttu-id="eb449-261">**string_framework_length**: 문자열 프레임워크의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-261">**string_framework_length**: Length of string framework.</span></span>
- <span data-ttu-id="eb449-262">**language_id_framework**: 문자열 언어 프레임워크에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-262">**language_id_framework**: Pointer to string language framework.</span></span>
- <span data-ttu-id="eb449-263">**language_id_framework_length**: 문자열 언어 프레임워크의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-263">**language_id_framework_length**: Length of the string language framework.</span></span>
- <span data-ttu-id="eb449-264">**ux_system_slave_change_function**: 디바이스 상태가 변경될 때 호출되는 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-264">**ux_system_slave_change_function**: Function to be called when the device state changes.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb449-265">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-265">Return Values</span></span>

- <span data-ttu-id="eb449-266">**UX_SUCCESS** (0x00) 이 작업을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-266">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eb449-267">**UX_MEMORY_INSUFFICIENT** (0x12) 메모리가 부족하여 스택을 초기화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-267">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to initialize the stack.</span></span>
- <span data-ttu-id="eb449-268">**UX_DESCRIPTOR_CORRUPTED** (0x42) 설명자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-268">**UX_DESCRIPTOR_CORRUPTED** (0x42) The descriptor is invalid.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-269">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-269">Example</span></span>

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="eb449-270">애플리케이션은 컨트롤러의 상태를 변경할 때 콜백을 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-270">The application can request a call back when the controller changes its state.</span></span> <span data-ttu-id="eb449-271">컨트롤러에 대한 두 가지 주요 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-271">The two main states for the controller are:</span></span>

- <span data-ttu-id="eb449-272">**UX_DEVICE_SUSPENDED**</span><span class="sxs-lookup"><span data-stu-id="eb449-272">**UX_DEVICE_SUSPENDED**</span></span>
- <span data-ttu-id="eb449-273">**UX_DEVICE_RESUMED**</span><span class="sxs-lookup"><span data-stu-id="eb449-273">**UX_DEVICE_RESUMED**</span></span>

<span data-ttu-id="eb449-274">애플리케이션에 일시 중단/다시 시작 신호가 필요하지 않으면 UX_NULL 함수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-274">If the application does not need Suspend/Resume signals, it would supply a UX_NULL function.</span></span>

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="eb449-275">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="eb449-275">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="eb449-276">스택 인터페이스 삭제</span><span class="sxs-lookup"><span data-stu-id="eb449-276">Delete a stack interface</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-277">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-277">Prototype</span></span>

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="eb449-278">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-278">Description</span></span>

<span data-ttu-id="eb449-279">이 함수는 인터페이스를 제거해야 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-279">This function is called when an interface should be removed.</span></span> <span data-ttu-id="eb449-280">인터페이스는 디바이스를 추출하거나, 버스 재설정을 수행하거나, 새 대체 설정이 있는 경우 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-280">An interface is either removed when a device is extracted, or following a bus reset, or when there is a new alternate setting.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb449-281">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-281">Input Parameter</span></span>

- <span data-ttu-id="eb449-282">**인터페이스**: 제거할 인터페이스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-282">**interface**: Pointer to the interface to remove.</span></span>

### <a name="return-value"></a><span data-ttu-id="eb449-283">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-283">Return Value</span></span>

- <span data-ttu-id="eb449-284">**UX_SUCCESS** (0x00) 이 작업을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-284">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-285">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-285">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="eb449-286">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="eb449-286">ux_device_stack_interface_get</span></span>

<span data-ttu-id="eb449-287">현재 인터페이스 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="eb449-287">Get the current interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-288">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-288">Prototype</span></span>

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a><span data-ttu-id="eb449-289">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-289">Description</span></span>

<span data-ttu-id="eb449-290">이 함수는 호스트가 현재 인터페이스를 쿼리할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-290">This function is called when the host queries the current interface.</span></span> <span data-ttu-id="eb449-291">디바이스가 현재 인터페이스 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-291">The device returns the current interface value.</span></span>

> [!NOTE]
> <span data-ttu-id="eb449-292">이 함수는 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-292">This function is deprecated.</span></span> <span data-ttu-id="eb449-293">이 함수는 레거시 소프트웨어에 사용할 수 있지만 새 소프트웨어는 ***ux_device_stack_alternate_setting_get*** 함수를 대신 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-293">It is available for legacy software, but new software should use the ***ux_device_stack_alternate_setting_get*** function instead.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb449-294">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-294">Input Parameter</span></span>

- <span data-ttu-id="eb449-295">**interface_value** 반환할 인터페이스 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-295">**interface_value** Interface value to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb449-296">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-296">Return Values</span></span>

- <span data-ttu-id="eb449-297">**UX_SUCCESS** (0x00) 이 작업을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-297">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eb449-298">**UX_ERROR** (0xFF) 인터페이스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-298">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-299">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-299">Example</span></span>

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="eb449-300">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="eb449-300">ux_device_stack_interface_set</span></span>

<span data-ttu-id="eb449-301">인터페이스의 대체 설정 변경</span><span class="sxs-lookup"><span data-stu-id="eb449-301">Change the alternate setting of the interface</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-302">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-302">Prototype</span></span>

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="eb449-303">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-303">Description</span></span>

<span data-ttu-id="eb449-304">이 함수는 호스트가 인터페이스의 대체 설정 변경을 요청할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-304">This function is called when the host requests a change of the alternate setting for the interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb449-305">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-305">Parameters</span></span>

- <span data-ttu-id="eb449-306">**device_framework**: 이 인터페이스에 대한 디바이스 프레임워크의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-306">**device_framework**: Address of the device framework for this interface.</span></span>
- <span data-ttu-id="eb449-307">**device_framework_length**: 디바이스 프레임워크의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-307">**device_framework_length**: Length of the device framework.</span></span>
- <span data-ttu-id="eb449-308">**alternate_setting_value**: 이 인터페이스에서 사용할 대체 설정 값입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-308">**alternate_setting_value**: Alternate setting value to be used by this interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb449-309">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-309">Return Values</span></span>

- <span data-ttu-id="eb449-310">**UX_SUCCESS** (0x00) 이 작업을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-310">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eb449-311">**UX_ERROR** (0xFF) 인터페이스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-311">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-312">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-312">Example</span></span>

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a><span data-ttu-id="eb449-313">ux_device_stack_interface_start</span><span class="sxs-lookup"><span data-stu-id="eb449-313">ux_device_stack_interface_start</span></span>

<span data-ttu-id="eb449-314">인터페이스 인스턴스를 소유하는 클래스 검색 시작</span><span class="sxs-lookup"><span data-stu-id="eb449-314">Start search for a class to own an interface instance</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-315">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-315">Prototype</span></span>

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="eb449-316">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-316">Description</span></span>

<span data-ttu-id="eb449-317">이 함수는 호스트가 인터페이스를 선택하고 디바이스 스택이 이 인터페이스 인스턴스를 소유할 디바이스 클래스를 검색해야 하는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-317">This function is called when an interface has been selected by the host and the device stack needs to search for a device class to own this interface instance.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb449-318">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-318">Input Parameter</span></span>

- <span data-ttu-id="eb449-319">**interface**: 생성된 인터페이스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-319">**interface**: Pointer to the interface created.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb449-320">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-320">Return Values</span></span>

- <span data-ttu-id="eb449-321">**UX_SUCCESS** (0x00) 이 작업을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-321">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eb449-322">**UX_NO_CLASS_MATCH** (0x57) 이 인터페이스에 대한 클래스가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-322">**UX_NO_CLASS_MATCH** (0x57) No class exists for this interface.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-323">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-323">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="eb449-324">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="eb449-324">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="eb449-325">호스트로 데이터 전송 요청</span><span class="sxs-lookup"><span data-stu-id="eb449-325">Request to transfer data to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-326">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-326">Prototype</span></span>

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="eb449-327">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-327">Description</span></span>

<span data-ttu-id="eb449-328">이 함수는 클래스 또는 스택이 호스트에 데이터를 전송하려고 할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-328">This function is called when a class or the stack wants to transfer data to the host.</span></span> <span data-ttu-id="eb449-329">호스트는 항상 디바이스를 폴링하지만 디바이스는 데이터를 미리 준비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-329">The host always polls the device but the device can prepare data in advance.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb449-330">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-330">Parameters</span></span>

- <span data-ttu-id="eb449-331">**transfer_request**: 전송 요청에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-331">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="eb449-332">**slave_length**: 디바이스에서 반환하려는 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-332">**slave_length**: Length the device wants to return.</span></span>
- <span data-ttu-id="eb449-333">**host_length**: 호스트가 요청한 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-333">**host_length**: Length the host has requested.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb449-334">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-334">Return Values</span></span>

- <span data-ttu-id="eb449-335">**UX_SUCCESS** (0x00) 이 작업을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-335">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eb449-336">**UX_TRANSFER_NOT_READY** (0x25) 디바이스 상태가 잘못되었습니다. **ATTACHED**, **CONFIGURED** 또는 **ADDRESSED** 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-336">**UX_TRANSFER_NOT_READY** (0x25) The device is in an invalid state; it must be **ATTACHED**, **CONFIGURED**, or **ADDRESSED**.</span></span>
- <span data-ttu-id="eb449-337">**UX_ERROR** (0xFF) 전송 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-337">**UX_ERROR** (0xFF) Transport error.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-338">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-338">Example</span></span>

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="eb449-339">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="eb449-339">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="eb449-340">전송 요청 취소</span><span class="sxs-lookup"><span data-stu-id="eb449-340">Cancel a transfer request</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-341">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-341">Prototype</span></span>

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a><span data-ttu-id="eb449-342">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-342">Description</span></span>

<span data-ttu-id="eb449-343">이 함수는 애플리케이션이 전송 요청을 취소해야 하거나, 스택이 엔드포인트와 연결된 전송 요청을 중단해야 하는 경우 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-343">This function is called when an application needs to cancel a transfer request or when the stack needs to abort a transfer request associated with an endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb449-344">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-344">Parameters</span></span>

- <span data-ttu-id="eb449-345">**transfer_request**: 전송 요청에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-345">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="eb449-346">**completion_code**:이 전송 요청이 완료되기를 기다리는 클래스로 반환되는 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-346">**completion_code**: Error code to be returned to the class waiting for this transfer request to complete.</span></span>

### <a name="return-value"></a><span data-ttu-id="eb449-347">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-347">Return Value</span></span>

- <span data-ttu-id="eb449-348">**UX_SUCCESS** (0x00) 이 작업을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-348">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="eb449-349">예제</span><span class="sxs-lookup"><span data-stu-id="eb449-349">Example</span></span>

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a><span data-ttu-id="eb449-350">ux_device_stack_uninitialize</span><span class="sxs-lookup"><span data-stu-id="eb449-350">ux_device_stack_uninitialize</span></span>

<span data-ttu-id="eb449-351">스택 초기화 취소</span><span class="sxs-lookup"><span data-stu-id="eb449-351">Unitialize stack</span></span>

### <a name="prototype"></a><span data-ttu-id="eb449-352">프로토타입</span><span class="sxs-lookup"><span data-stu-id="eb449-352">Prototype</span></span>

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a><span data-ttu-id="eb449-353">Description</span><span class="sxs-lookup"><span data-stu-id="eb449-353">Description</span></span>

<span data-ttu-id="eb449-354">이 함수는 애플리케이션이 USBX 디바이스 스택을 초기화 취소해야 할 때 호출되며 모든 디바이스 스택 리소스가 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-354">This function is called when an application needs to unitialize the USBX device stack – all device stack resources are freed.</span></span> <span data-ttu-id="eb449-355">ux_device_stack_class_unregister를 통해 모든 클래스의 등록을 취소한 후에 이 함수를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-355">This should be called after all classes have been unregistered via ux_device_stack_class_unregister.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb449-356">매개 변수</span><span class="sxs-lookup"><span data-stu-id="eb449-356">Parameters</span></span>

<span data-ttu-id="eb449-357">없음</span><span class="sxs-lookup"><span data-stu-id="eb449-357">None</span></span>

### <a name="return-value"></a><span data-ttu-id="eb449-358">반환 값</span><span class="sxs-lookup"><span data-stu-id="eb449-358">Return Value</span></span>

<span data-ttu-id="eb449-359">**UX_SUCCESS** (0x00) 이 작업을 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="eb449-359">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
