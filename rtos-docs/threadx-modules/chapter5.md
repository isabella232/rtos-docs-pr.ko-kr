---
title: 5장 - 모듈 관리자 API
author: philmea
description: 이 문서에는 애플리케이션의 상주 부분에 사용할 수 있는 모듈 관리자 API가 요약되어 있습니다.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ca0fee443c23fd1bdd34651f4a7b31cf71f886f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810302"
---
# <a name="chapter-5---module-manager-apis"></a><span data-ttu-id="fe11a-103">5장 - 모듈 관리자 API</span><span class="sxs-lookup"><span data-stu-id="fe11a-103">Chapter 5 - Module Manager APIs</span></span>

## <a name="summary-of-module-manager-apis"></a><span data-ttu-id="fe11a-104">모듈 관리자 API 요약</span><span class="sxs-lookup"><span data-stu-id="fe11a-104">Summary of Module Manager APIs</span></span>

<span data-ttu-id="fe11a-105">애플리케이션의 상주 부분에 사용할 수 있는 추가 API는 다음과 같이 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-105">There are several additional APIs available to the resident portion of the application, as follows.</span></span>

- <span data-ttu-id="fe11a-106">***txm_module_manager_external_memory_enable** _ - _*모듈에서 공유 메모리 공간에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-106">***txm_module_manager_external_memory_enable** _ - _Enable module access to a shared memory space*</span></span>
- <span data-ttu-id="fe11a-107">***txm_module_manager_file_load** _ - _*FileX를 통해 파일에서 모듈을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-107">***txm_module_manager_file_load** _ - _Load module from file via FileX*</span></span>
- <span data-ttu-id="fe11a-108">***txm_module_manager_in_place_load** _ - _*모듈 데이터를 로드하고 현재 위치에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-108">***txm_module_manager_in_place_load** _ - _Load module data, execute in place*</span></span>
- <span data-ttu-id="fe11a-109">***txm_module_manager_initialize** _ - _*모듈 관리자를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-109">***txm_module_manager_initialize** _ - _Initialize the module manager*</span></span>
- <span data-ttu-id="fe11a-110">***txm_module_manager_mm_initialize** _ - _*메모리 관리 하드웨어를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-110">***txm_module_manager_mm_initialize** _ - _Initialize the memory management hardware*</span></span>
- <span data-ttu-id="fe11a-111">***txm_module_manager_maximum_module_priority_set** _ - _*모듈에서 허용되는 최대 스레드 우선 순위를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-111">***txm_module_manager_maximum_module_priority_set** _ - _Set the maximum thread priority allowed in a module*</span></span>
- <span data-ttu-id="fe11a-112">***txm_module_manager_memory_fault_notify** _ - _*메모리 오류 발생 시 애플리케이션 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-112">***txm_module_manager_memory_fault_notify** _ - _Register an application callback on memory fault*</span></span>
- <span data-ttu-id="fe11a-113">***txm_module_manager_memory_load** _ - _*메모리에서 모듈을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-113">***txm_module_manager_memory_load** _ - _Load the module from memory*</span></span>
- <span data-ttu-id="fe11a-114">***txm_module_manager_object_pool_create** _ - _*모듈 개체 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-114">***txm_module_manager_object_pool_create** _ - _Create an object pool for modules*</span></span>
- <span data-ttu-id="fe11a-115">***txm_module_manager_properties_get** _ - _*모듈 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-115">***txm_module_manager_properties_get** _ - _Get module properties*</span></span>
- <span data-ttu-id="fe11a-116">***txm_module_manager_start** _ - _*지정된 모듈 실행을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-116">***txm_module_manager_start** _ - _Start execution of the specified module*</span></span>
- <span data-ttu-id="fe11a-117">***txm_module_manager_stop** _ - _*지정된 모듈 실행을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-117">***txm_module_manager_stop** _ - _Stop execution of the specified module*</span></span>
- <span data-ttu-id="fe11a-118">***txm_module_manager_unload** _ - _*모듈을 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-118">***txm_module_manager_unload** _ - _Unload the module*</span></span>

---

## <a name="txm_module_manager_external_memory_enable"></a><span data-ttu-id="fe11a-119">txm_module_manager_external_memory_enable</span><span class="sxs-lookup"><span data-stu-id="fe11a-119">txm_module_manager_external_memory_enable</span></span>

<span data-ttu-id="fe11a-120">모듈에서 공유 메모리 공간에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-120">Enable module to access a shared memory space.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-121">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-121">Prototype</span></span>

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a><span data-ttu-id="fe11a-122">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-122">Description</span></span>

<span data-ttu-id="fe11a-123">이 서비스는 모듈에서 액세스할 수 있는 공유 메모리 영역에 대한 항목을 메모리 관리 하드웨어 테이블에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-123">This service creates an entry in the memory management hardware table for a shared memory region that the module can access.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-124">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-124">Input parameters</span></span>

- <span data-ttu-id="fe11a-125">**module_instance** 모듈 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-125">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="fe11a-126">**start_address** 공유 메모리 영역의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-126">**start_address** Starting address of shared memory region.</span></span>
- <span data-ttu-id="fe11a-127">**length** 공유 메모리 영역의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-127">**length** Length of shared memory region.</span></span>
- <span data-ttu-id="fe11a-128">**attributes** 메모리 영역 특성(캐시, 읽기, 쓰기 등)입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-128">**attributes** Attributes of memory region (cache, read, write, etc.).</span></span> <span data-ttu-id="fe11a-129">특성은 포트에 특정됩니다. 특성 형식은 [부록](appendix.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe11a-129">Attributes are port-specific; see [appendix](appendix.md) for attributes format.</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-130">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-130">Return values</span></span>

- <span data-ttu-id="fe11a-131">**TX_SUCCESS**(0x00) 메모리 항목을 만드는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-131">**TX_SUCCESS** (0x00) Memory entry created successfully.</span></span>
- <span data-ttu-id="fe11a-132">**TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았거나 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-132">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized or feature not available.</span></span>
- <span data-ttu-id="fe11a-133">**TX_PTR_ERROR**(0x03) 잘못된 모듈 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-133">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="fe11a-134">**TX_START_ERROR**(0x10) 모듈이 로드된 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-134">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>
- <span data-ttu-id="fe11a-135">**TXM_MODULE_ALIGNMENT_ERROR**(0xF0) 잘못된 시작 주소 맞춤입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-135">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid start address alignment.</span></span>
- <span data-ttu-id="fe11a-136">**TXM_MODULE_INVALID_PROPERTIES**(0xF3) 호환되지 않는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-136">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-137">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-137">Allowed from</span></span>

<span data-ttu-id="fe11a-138">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-138">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-139">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-139">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a><span data-ttu-id="fe11a-140">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="fe11a-140">txm_module_manager_file_load</span></span>

<span data-ttu-id="fe11a-141">FileX를 통해 파일에서 모듈을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-141">Load module from file via FileX.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-142">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-142">Prototype</span></span>

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a><span data-ttu-id="fe11a-143">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-143">Description</span></span>

<span data-ttu-id="fe11a-144">이 서비스는 지정된 파일에 포함된 모듈의 이진 이미지를 모듈 메모리 영역으로 로드하고 실행을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-144">This service loads the binary image of the module contained in the specified file into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="fe11a-145">제공된 미디어는 이미 열려 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-145">It is assumed that the supplied media is already opened.</span></span>

> [!NOTE]
> <span data-ttu-id="fe11a-146">파일을 로드하는 데는 FileX 시스템을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-146">The FileX system is utilized to load the file.</span></span> <span data-ttu-id="fe11a-147">FileX 액세스를 사용하도록 설정하려면 모듈, 모듈 라이브러리, 모듈 관리자 및 ThreadX 라이브러리(모듈 관리자 소스 포함)를 프로젝트에 정의된 **FX_FILEX_PRESENT** 로 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-147">In order to enable FileX access, the module, module library, Module Manager and the ThreadX library (with the Module Manager sources) must be built with **FX_FILEX_PRESENT** defined in the projects.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-148">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-148">Input parameters</span></span>

- <span data-ttu-id="fe11a-149">**module_instance** 모듈 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-149">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="fe11a-150">**module_name** 모듈 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-150">**module_name** Name of the module.</span></span>
- <span data-ttu-id="fe11a-151">**media_ptr** 이미 열려 있는 FileX 미디어에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-151">**media_ptr** Pointer to already opened FileX media.</span></span>
- <span data-ttu-id="fe11a-152">**file_name** 모듈의 이진 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-152">**file_name** Name of module's binary file.</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-153">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-153">Return values</span></span>

- <span data-ttu-id="fe11a-154">**TX_SUCCESS**(0x00) 모듈 로드에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-154">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="fe11a-155">**TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-155">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="fe11a-156">**TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-156">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="fe11a-157">**TX_NO_MEMORY**(0x10) 메모리가 부족하여 모듈을 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-157">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="fe11a-158">**TX_NOT_DONE**(0x20) 미디어가 열려 있지 않거나, 파일을 찾지 못했거나, 파일이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-158">**TX_NOT_DONE** (0x20) Media not open, file not found or file is invalid.</span></span>
- <span data-ttu-id="fe11a-159">**TX_PTR_ERROR**(0x03) 잘못된 모듈 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-159">**TX_PTR_ERROR** (0x03) Invalid module pointer.</span></span>
- <span data-ttu-id="fe11a-160">**TXM_MODULE_ALIGNMENT_ERROR**(0xF0) 잘못된 맞춤입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-160">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="fe11a-161">**TXM_MODULE_ALREADY_LOADED**(0xF1) 모듈이 이미 로드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-161">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="fe11a-162">**TXM_MODULE_INVALID**(0xF2) | 잘못된 모듈 프리앰블입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-162">**TXM_MODULE_INVALID** (0xF2) | Invalid module preamble.</span></span>
- <span data-ttu-id="fe11a-163">**TXM_MODULE_INVALID_PROPERTIES**(0xF3) 호환되지 않는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-163">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-164">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-164">Allowed from</span></span>

<span data-ttu-id="fe11a-165">스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-165">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-166">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-166">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="fe11a-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe11a-167">See also</span></span>

- <span data-ttu-id="fe11a-168">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="fe11a-168">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="fe11a-169">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="fe11a-169">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="fe11a-170">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="fe11a-170">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_in_place_load"></a><span data-ttu-id="fe11a-171">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="fe11a-171">txm_module_manager_in_place_load</span></span>

<span data-ttu-id="fe11a-172">모듈 데이터만 로드하고 기존 위치에서 모듈을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-172">Load module data only, execute module in existing location.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-173">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-173">Prototype</span></span>

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="fe11a-174">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-174">Description</span></span>

<span data-ttu-id="fe11a-175">이 서비스는 모듈의 데이터 영역만 모듈 메모리 영역으로 로드하고 실행을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-175">This service loads the module's data area only into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="fe11a-176">모듈 코드 실행은 현재 위치 즉, 제공된 위치의 모듈 프리앰블에 지정된 주소 오프셋에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-176">Module code execution will be in-place, that is, from the address offset specified by the module preamble at the supplied location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-177">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-177">Input parameters</span></span>

- <span data-ttu-id="fe11a-178">**module_instance** 모듈 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-178">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="fe11a-179">**module_name** 모듈 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-179">**module_name** Name of the module.</span></span>
- <span data-ttu-id="fe11a-180">**location** 프리앰블이 맨 앞에 있는 모듈 코드 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-180">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-181">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-181">Return values</span></span>

- <span data-ttu-id="fe11a-182">**TX_SUCCESS**(0x00) 모듈 로드에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-182">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="fe11a-183">**TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-183">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="fe11a-184">**TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-184">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="fe11a-185">**TX_NO_MEMORY**(0x10) 메모리가 부족하여 모듈을 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-185">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="fe11a-186">**TX_PTR_ERROR**(0x03) 포인터, 모듈 인스턴스 또는 모듈 프리앰블이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-186">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="fe11a-187">**TXM_MODULE_ALIGNMENT_ERROR**(0xF0) 잘못된 맞춤입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-187">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="fe11a-188">**TXM_MODULE_ALREADY_LOADED**(0xF1) 모듈이 이미 로드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-188">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="fe11a-189">**TXM_MODULE_INVALID**(0xF2) 잘못된 모듈 프리앰블입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-189">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="fe11a-190">**TXM_MODULE_INVALID_PROPERTIES**(0xF3) 호환되지 않는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-190">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-191">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-191">Allowed from</span></span>

<span data-ttu-id="fe11a-192">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-192">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-193">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-193">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="fe11a-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe11a-194">See also</span></span>

- <span data-ttu-id="fe11a-195">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="fe11a-195">txm_module_manager_file_load</span></span>
- <span data-ttu-id="fe11a-196">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="fe11a-196">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="fe11a-197">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="fe11a-197">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_initialize"></a><span data-ttu-id="fe11a-198">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="fe11a-198">txm_module_manager_initialize</span></span>

<span data-ttu-id="fe11a-199">모듈 관리자를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-199">Initialize the module manager.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-200">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-200">Prototype</span></span>

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a><span data-ttu-id="fe11a-201">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-201">Description</span></span>

<span data-ttu-id="fe11a-202">이 서비스는 모듈 로드에 사용되는 메모리 영역을 포함하여 모듈 관리자의 내부 리소스를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-202">This service initializes the Module Manager's internal resources, including the memory area used for loading modules.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-203">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-203">Input parameters</span></span>

- <span data-ttu-id="fe11a-204">**module_memory_start** 모듈 메모리의 시작에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-204">**module_memory_start** Pointer to the start of module memory.</span></span>
- <span data-ttu-id="fe11a-205">**module_memory_size** 모듈 메모리의 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-205">**module_memory_size** Size in bytes of the module memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-206">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-206">Return values</span></span>

- <span data-ttu-id="fe11a-207">**TX_SUCCESS**(0x00) 초기화에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-207">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="fe11a-208">**TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-208">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-209">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-209">Allowed from</span></span>

<span data-ttu-id="fe11a-210">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-210">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-211">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-211">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="fe11a-212">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe11a-212">See also</span></span>

- <span data-ttu-id="fe11a-213">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="fe11a-213">txm_module_manager_object_pool_create</span></span>

---

## <a name="txm_module_manager_initialize_mmu"></a><span data-ttu-id="fe11a-214">txm_module_manager_initialize_mmu</span><span class="sxs-lookup"><span data-stu-id="fe11a-214">txm_module_manager_initialize_mmu</span></span>

<span data-ttu-id="fe11a-215">메모리 관리 하드웨어를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-215">Initialize the memory management hardware.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-216">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-216">Prototype</span></span>

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a><span data-ttu-id="fe11a-217">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-217">Description</span></span>

<span data-ttu-id="fe11a-218">이 서비스는 MMU를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-218">This service initializes the MMU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-219">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-219">Input parameters</span></span>

<span data-ttu-id="fe11a-220">없음</span><span class="sxs-lookup"><span data-stu-id="fe11a-220">none</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-221">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-221">Return values</span></span>

- <span data-ttu-id="fe11a-222">**TX_SUCCESS**(0x00) 초기화에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-222">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="fe11a-223">**TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-223">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-224">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-224">Allowed from</span></span>

<span data-ttu-id="fe11a-225">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-225">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-226">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-226">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a><span data-ttu-id="fe11a-227">txm_module_manager_maximum_module_priority_set</span><span class="sxs-lookup"><span data-stu-id="fe11a-227">txm_module_manager_maximum_module_priority_set</span></span>

<span data-ttu-id="fe11a-228">모듈에서 허용되는 최대 스레드 우선 순위를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-228">Set the maximum thread priority allowed in a module.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-229">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-229">Prototype</span></span>

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a><span data-ttu-id="fe11a-230">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-230">Description</span></span>

<span data-ttu-id="fe11a-231">이 서비스는 모듈에서 허용되는 최대 스레드 우선 순위를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-231">This service sets the maximum thread priority allowed in a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-232">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-232">Input parameters</span></span>

- <span data-ttu-id="fe11a-233">**module_instance** 모듈 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-233">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="fe11a-234">**priority** 최대 스레드 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-234">**priority** Maximum thread priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-235">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-235">Return values</span></span>

- <span data-ttu-id="fe11a-236">**TX_SUCCESS**(0x00) 초기화에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-236">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="fe11a-237">**TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-237">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="fe11a-238">**TX_PTR_ERROR**(0x03) 잘못된 모듈 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-238">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="fe11a-239">**TX_START_ERROR**(0x10) 모듈이 로드된 상태가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-239">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-240">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-240">Allowed from</span></span>

<span data-ttu-id="fe11a-241">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-241">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-242">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-242">Example</span></span>

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a><span data-ttu-id="fe11a-243">txm_module_manager_memory_fault_notify</span><span class="sxs-lookup"><span data-stu-id="fe11a-243">txm_module_manager_memory_fault_notify</span></span>

<span data-ttu-id="fe11a-244">메모리 오류 발생 시 애플리케이션 콜백을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-244">Register an application callback on memory fault.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-245">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-245">Prototype</span></span>

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a><span data-ttu-id="fe11a-246">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-246">Description</span></span>

<span data-ttu-id="fe11a-247">이 서비스는 지정된 애플리케이션 메모리 오류 알림 콜백 함수를 모듈 관리자에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-247">This service registers the specified application memory fault notification callback function with the Module Manager.</span></span> <span data-ttu-id="fe11a-248">메모리 오류가 발생하면 잘못된 스레드에 대한 포인터와 잘못된 스레드에 해당하는 모듈 인스턴스를 사용하여 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-248">If a memory fault occurs, this function is called with a pointer to the offending thread and the module instance corresponding to the offending thread.</span></span> <span data-ttu-id="fe11a-249">모듈 관리자 처리에서는 자동으로 잘못된 스레드는 종료하고 모듈의 다른 모든 스레드는 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-249">The Module Manager processing automatically terminates the offending thread, but leaves any other threads in the module untouched.</span></span> <span data-ttu-id="fe11a-250">메모리 오류와 관련된 모듈에서 수행할 작업은 애플리케이션에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-250">It is up to the application to decide what to do with the module associated with the memory fault.</span></span>

<span data-ttu-id="fe11a-251">메모리 오류 자체에 대한 자세한 내용은 내부 **_txm_module_manager_memory_fault_info** 구조체를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe11a-251">Please see the internal **_txm_module_manager_memory_fault_info** struct for specific information on the memory fault itself.</span></span>

> [!NOTE]
> <span data-ttu-id="fe11a-252">메모리 오류 알림 콜백 함수는 메모리 오류 예외에서 직접 실행되므로 인터럽트 서비스 루틴에서 허용되는 ThreadX API만 호출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-252">The memory fault notification callback function is executed directly from the memory fault exception, so only ThreadX APIs Allowed from interrupt service routines can be called.</span></span> <span data-ttu-id="fe11a-253">그러므로 잘못된 모듈을 중지하고 언로드하려면 애플리케이션 알림 콜백에서 애플리케이션 작업으로 신호를 송신하여 모듈을 중지하고 언로드할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-253">Thus, in order to stop and unload the offending module, the application notification callback must send a signal to an application task so that the module can be stopped and unloaded.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-254">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-254">Input parameters</span></span>

- <span data-ttu-id="fe11a-255">**notify_function** 애플리케이션 메모리 오류 알림 콜백을 가리키는 함수 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-255">**notify_function** Function pointer to the application's memory fault notification callback.</span></span> <span data-ttu-id="fe11a-256">NULL 값을 제공하면 메모리 오류 알림을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-256">Supplying a NULL value disables the memory fault notification.</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-257">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-257">Return values</span></span>

- <span data-ttu-id="fe11a-258">**TX_SUCCESS**(0x00) 알림 함수 등록에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-258">**TX_SUCCESS** (0x00) Successful notification function registration.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-259">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-259">Allowed from</span></span>

<span data-ttu-id="fe11a-260">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-260">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-261">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-261">Example</span></span>

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a><span data-ttu-id="fe11a-262">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="fe11a-262">txm_module_manager_memory_load</span></span>

<span data-ttu-id="fe11a-263">메모리에서 모듈을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-263">Load module from memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-264">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-264">Prototype</span></span>

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="fe11a-265">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-265">Description</span></span>

<span data-ttu-id="fe11a-266">이 서비스는 모듈의 코드 및 데이터 영역을 ***txm_module_manager_initialize*** 를 통해 설정된 모듈 메모리 영역으로 로드하고 실행을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-266">This service loads the module's code and data area into the module memory area set up by ***txm_module_manager_initialize*** and prepares it for execution.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-267">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-267">Input parameters</span></span>

- <span data-ttu-id="fe11a-268">**module_instance** 모듈 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-268">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="fe11a-269">**module_name** 모듈 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-269">**module_name** Name of the module.</span></span>
- <span data-ttu-id="fe11a-270">**location** 프리앰블이 맨 앞에 있는 모듈 코드 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-270">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-271">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-271">Return values</span></span>

- <span data-ttu-id="fe11a-272">**TX_SUCCESS**(0x00) 모듈 로드에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-272">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="fe11a-273">**TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-273">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="fe11a-274">**TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-274">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="fe11a-275">**TX_NO_MEMORY**(0x10) 메모리가 부족하여 모듈을 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-275">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="fe11a-276">**TX_PTR_ERROR**(0x03) 포인터, 모듈 인스턴스 또는 모듈 프리앰블이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-276">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="fe11a-277">**TXM_MODULE_ALIGNMENT_ERROR**(0xF0) 잘못된 맞춤입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-277">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="fe11a-278">**TXM_MODULE_ALREADY_LOADED**(0xF1) 모듈이 이미 로드되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-278">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="fe11a-279">**TXM_MODULE_INVALID**(0xF2) 잘못된 모듈 프리앰블입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-279">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="fe11a-280">**TXM_MODULE_INVALID_PROPERTIES**(0xF3) 호환되지 않는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-280">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-281">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-281">Allowed from</span></span>

<span data-ttu-id="fe11a-282">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-282">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-283">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-283">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a><span data-ttu-id="fe11a-284">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe11a-284">See also</span></span>

- <span data-ttu-id="fe11a-285">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="fe11a-285">txm_module_manager_file_load</span></span>
- <span data-ttu-id="fe11a-286">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="fe11a-286">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="fe11a-287">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="fe11a-287">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_object_pool_create"></a><span data-ttu-id="fe11a-288">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="fe11a-288">txm_module_manager_object_pool_create</span></span>

<span data-ttu-id="fe11a-289">모듈 개체 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-289">Create an object pool for modules.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-290">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-290">Prototype</span></span>

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a><span data-ttu-id="fe11a-291">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-291">Description</span></span>

<span data-ttu-id="fe11a-292">이 서비스는 모듈이 ThreadX/NetX 개체를 할당하여 시스템 개체를 모듈 메모리 영역 외부에 유지할 수 있도록 하는 모듈 관리자 개체 메모리 풀을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-292">This service creates a Module Manager object memory pool that the modules can allocate ThreadX/NetX objects from, thereby keeping the system object out of the module's memory area.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-293">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-293">Input parameters</span></span>

- <span data-ttu-id="fe11a-294">**pool_memory_start** 개체 메모리 시작에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-294">**pool_memory_start** Pointer to the start of object memory.</span></span>
- <span data-ttu-id="fe11a-295">**pool_memory_size** 개체 메모리 풀 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-295">**pool_memory_size** Size in bytes of the object memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-296">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-296">Return values</span></span>

- <span data-ttu-id="fe11a-297">**TX_SUCCESS**(0x00) 초기화에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-297">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="fe11a-298">**TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-298">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-299">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-299">Allowed from</span></span>

<span data-ttu-id="fe11a-300">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-300">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-301">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-301">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="fe11a-302">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe11a-302">See also</span></span>

- <span data-ttu-id="fe11a-303">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="fe11a-303">txm_module_manager_initialize</span></span>

---

## <a name="txm_module_manager_properties_get"></a><span data-ttu-id="fe11a-304">txm_module_manager_properties_get</span><span class="sxs-lookup"><span data-stu-id="fe11a-304">txm_module_manager_properties_get</span></span>

<span data-ttu-id="fe11a-305">모듈 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-305">Get module properties.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-306">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-306">Prototype</span></span>

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a><span data-ttu-id="fe11a-307">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-307">Description</span></span>

<span data-ttu-id="fe11a-308">이 서비스는 모듈 속성(프리앰블에 지정됨)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-308">This service returns the properties (specified in the preamble) of a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-309">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-309">Input parameters</span></span>

- <span data-ttu-id="fe11a-310">**module_instance** 모듈 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-310">**module_instance** Pointer to the module instance.</span></span>
- <span data-ttu-id="fe11a-311">**module_properties_ptr** 모듈 속성 대상에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-311">**module_properties_ptr** Pointer to destination for module's properties.</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-312">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-312">Return values</span></span>

- <span data-ttu-id="fe11a-313">**TX_SUCCESS**(0x00) 초기화에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-313">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="fe11a-314">**TX_PTR_ERROR**(0x03) 잘못된 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-314">**TX_PTR_ERROR** (0x03) Invalid pointer.</span></span>
- <span data-ttu-id="fe11a-315">**TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-315">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-316">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-316">Allowed from</span></span>

<span data-ttu-id="fe11a-317">스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-317">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-318">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-318">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a><span data-ttu-id="fe11a-319">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="fe11a-319">txm_module_manager_start</span></span>

<span data-ttu-id="fe11a-320">모듈 실행을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-320">Start execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-321">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-321">Prototype</span></span>

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="fe11a-322">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-322">Description</span></span>

<span data-ttu-id="fe11a-323">이 서비스는 이미 로드되고 지정된 모듈의 실행을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-323">This service starts execution of the specified, already loaded module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-324">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-324">Input parameters</span></span>

- <span data-ttu-id="fe11a-325">**module_instance** 이전에 로드된 모듈 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-325">**module_instance** Pointer to previously loaded module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-326">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-326">Return values</span></span>

- <span data-ttu-id="fe11a-327">**TX_SUCCESS**(0x00) 모듈 시작에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-327">**TX_SUCCESS** (0x00) Successful module start.</span></span>
- <span data-ttu-id="fe11a-328">**TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-328">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="fe11a-329">**TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-329">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="fe11a-330">**TX_PTR_ERROR**(0x03) 잘못된 포인터 또는 모듈 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-330">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="fe11a-331">**TX_START_ERROR**(0x10) 모듈이 이미 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-331">**TX_START_ERROR** (0x10) Module already started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-332">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-332">Allowed from</span></span>

<span data-ttu-id="fe11a-333">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-333">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-334">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-334">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="fe11a-335">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe11a-335">See also</span></span>

- <span data-ttu-id="fe11a-336">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="fe11a-336">txm_module_manager_stop</span></span>

---

## <a name="txm_module_manager_stop"></a><span data-ttu-id="fe11a-337">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="fe11a-337">txm_module_manager_stop</span></span>

<span data-ttu-id="fe11a-338">모듈 실행을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-338">Stop execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-339">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-339">Prototype</span></span>

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="fe11a-340">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-340">Description</span></span>

<span data-ttu-id="fe11a-341">이 서비스는 이전에 로드되어 시작된 모듈을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-341">This service stops a module that was previously loaded and started.</span></span> <span data-ttu-id="fe11a-342">모듈 중지에는 모듈의 선택적 중지 스레드 실행, 모든 스레드 종료, 해당 모듈과 연결된 모든 리소스 삭제 작업이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-342">Stopping a module includes executing the module's optional stop thread, terminating all threads, and deleting all resources associated with the module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-343">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-343">Input parameters</span></span>

- <span data-ttu-id="fe11a-344">**module_instance** 모듈 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-344">**module_instance** Pointer to module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-345">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-345">Return values</span></span>

- <span data-ttu-id="fe11a-346">**TX_SUCCESS**(0x00) 모듈 중지에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-346">**TX_SUCCESS** (0x00) Successful module stop.</span></span>
- <span data-ttu-id="fe11a-347">**TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-347">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="fe11a-348">**TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-348">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="fe11a-349">**TX_PTR_ERROR**(0x03) 잘못된 포인터 또는 모듈 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-349">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="fe11a-350">**TX_START_ERROR**(0x10) 모듈이 시작되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-350">**TX_START_ERROR** (0x10) Module not started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-351">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-351">Allowed from</span></span>

<span data-ttu-id="fe11a-352">스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-352">Threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-353">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-353">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="fe11a-354">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe11a-354">See also</span></span>

- <span data-ttu-id="fe11a-355">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="fe11a-355">txm_module_manager_start</span></span>

---

## <a name="txm_module_manager_unload"></a><span data-ttu-id="fe11a-356">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="fe11a-356">txm_module_manager_unload</span></span>

<span data-ttu-id="fe11a-357">모듈을 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-357">Unload the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="fe11a-358">프로토타입</span><span class="sxs-lookup"><span data-stu-id="fe11a-358">Prototype</span></span>

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="fe11a-359">Description</span><span class="sxs-lookup"><span data-stu-id="fe11a-359">Description</span></span>

<span data-ttu-id="fe11a-360">이 서비스는 이전에 로드되고 중지된 모듈을 언로드하여 모든 연결된 모듈 메모리 리소스를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-360">This service unloads the previously loaded and stopped module, freeing all the associated module memory resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="fe11a-361">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe11a-361">Input parameters</span></span>

- <span data-ttu-id="fe11a-362">**module_instance** 모듈 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-362">**module_instance** Pointer to the instance of the module.</span></span>

### <a name="return-values"></a><span data-ttu-id="fe11a-363">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe11a-363">Return values</span></span>

- <span data-ttu-id="fe11a-364">**TX_SUCCESS** 0x00) 모듈 언로드에 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-364">**TX_SUCCESS** 0x00) Successful module unload.</span></span>
- <span data-ttu-id="fe11a-365">**TX_CALLER_ERROR**(0x13) 잘못된 호출자입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-365">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="fe11a-366">**TX_NOT_AVAILABLE**(0x1D) 관리자가 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-366">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="fe11a-367">**TX_NOT_DONE**(0x20) 잘못된 모듈이거나 모듈이 중지되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-367">**TX_NOT_DONE** (0x20) Invalid module or module not stopped.</span></span>
- <span data-ttu-id="fe11a-368">**TX_PTR_ERROR**(0x03) 잘못된 포인터 또는 모듈 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="fe11a-368">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="fe11a-369">허용되는 위치</span><span class="sxs-lookup"><span data-stu-id="fe11a-369">Allowed from</span></span>

<span data-ttu-id="fe11a-370">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="fe11a-370">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="fe11a-371">예제</span><span class="sxs-lookup"><span data-stu-id="fe11a-371">Example</span></span>

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="fe11a-372">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe11a-372">See also</span></span>

- <span data-ttu-id="fe11a-373">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="fe11a-373">txm_module_manager_file_load</span></span>
- <span data-ttu-id="fe11a-374">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="fe11a-374">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="fe11a-375">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="fe11a-375">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="fe11a-376">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="fe11a-376">txm_module_manager_stop</span></span>
