---
title: 3장 - Azure RTOS NetX Duo AutoIP 서비스 설명
description: 이 장에는 모든 Azure RTOS NetX Duo AutoIP 서비스(아래에 나열됨)에 대한 설명이 알파벳 순서로 포함되어 있습니다.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0935295ef9f7255c0851e1f64013884dce4c52f1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810981"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a><span data-ttu-id="a1f14-103">3장 - Azure RTOS NetX Duo AutoIP 서비스 설명</span><span class="sxs-lookup"><span data-stu-id="a1f14-103">Chapter 3 - Description of Azure RTOS NetX Duo AutoIP services</span></span>

<span data-ttu-id="a1f14-104">이 장에는 모든 Azure RTOS NetX Duo AutoIP 서비스(아래에 나열됨)에 대한 설명이 알파벳 순서로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-104">This chapter contains a description of all Azure RTOS NetX Duo AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="a1f14-105">다음 API 설명의 "반환 값" 섹션에서 **BOLD** 의 값은 API 오류 검사를 사용하지 않도록 설정하는 데 사용되는 **NX_DISABLE_ERROR_CHECKING** 정의의 영향을 받지 않지만, 굵게 표시되지 않은 값은 완전히 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="a1f14-106">**nx_auto_ip_create**: *AutoIP 인스턴스 만들기*</span><span class="sxs-lookup"><span data-stu-id="a1f14-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="a1f14-107">**nx_auto_ip_delete**: *AutoIP 인스턴스 삭제*</span><span class="sxs-lookup"><span data-stu-id="a1f14-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="a1f14-108">**nx_auto_ip_get_address**: *현재 AutoIP 주소 가져오기*</span><span class="sxs-lookup"><span data-stu-id="a1f14-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="a1f14-109">**nx_auto_ip_set_interface**: *AutoIP 주소를 필요로 하는 IP 인터페이스 설정*</span><span class="sxs-lookup"><span data-stu-id="a1f14-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="a1f14-110">**nx_auto_ip_start**: *AutoIP 처리 시작*</span><span class="sxs-lookup"><span data-stu-id="a1f14-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="a1f14-111">**nx_auto_ip_stop**: *AutoIP 처리 중지*</span><span class="sxs-lookup"><span data-stu-id="a1f14-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="a1f14-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="a1f14-112">nx_auto_ip_create</span></span>

<span data-ttu-id="a1f14-113">AutoIP 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="a1f14-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a1f14-114">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a1f14-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a><span data-ttu-id="a1f14-115">Description</span><span class="sxs-lookup"><span data-stu-id="a1f14-115">Description</span></span>

<span data-ttu-id="a1f14-116">이 서비스는 지정된 IP 인스턴스에 AutoIP 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1f14-117">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a1f14-117">Input Parameters</span></span>

- <span data-ttu-id="a1f14-118">**auto_ip_ptr**: AutoIP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-118">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="a1f14-119">**name**: AutoIP 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-119">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="a1f14-120">**ip_ptr**: IP 인스턴스에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-120">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="a1f14-121">**stack_ptr**: AutoIP 스레드 스택 영역에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-121">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="a1f14-122">**stack_size**: AutoIP 스레드 스택 영역의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-122">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="a1f14-123">**priority**: AutoIP 스레드의 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-123">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="a1f14-124">DHCP를 사용하는 경우 DHCP 스레드의 우선 순위는 IP 인스턴스 스레드와 AutoIP 스레드보다 높아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-124">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="a1f14-125">반환 값</span><span class="sxs-lookup"><span data-stu-id="a1f14-125">Return Values</span></span>

- <span data-ttu-id="a1f14-126">**NX_SUCCESS**: (0x00) 성공적인 AutoIP 생성</span><span class="sxs-lookup"><span data-stu-id="a1f14-126">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="a1f14-127">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP 생성 오류</span><span class="sxs-lookup"><span data-stu-id="a1f14-127">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="a1f14-128">NX_PTR_ERROR: (0x16) AutoIP, ip_ptr 또는 스택 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-128">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="a1f14-129">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-129">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1f14-130">허용 위치</span><span class="sxs-lookup"><span data-stu-id="a1f14-130">Allowed From</span></span>

<span data-ttu-id="a1f14-131">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="a1f14-131">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1f14-132">예제</span><span class="sxs-lookup"><span data-stu-id="a1f14-132">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="a1f14-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1f14-133">See Also</span></span>

<span data-ttu-id="a1f14-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="a1f14-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="a1f14-135">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="a1f14-135">nx_auto_ip_delete</span></span>

<span data-ttu-id="a1f14-136">AutoIP 인스턴스 삭제</span><span class="sxs-lookup"><span data-stu-id="a1f14-136">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a1f14-137">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a1f14-137">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a1f14-138">Description</span><span class="sxs-lookup"><span data-stu-id="a1f14-138">Description</span></span>

<span data-ttu-id="a1f14-139">이 서비스는 지정된 IP 인스턴스에서 이전에 만든 AutoIP 인스턴스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-139">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1f14-140">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a1f14-140">Input Parameters</span></span>

- <span data-ttu-id="a1f14-141">**auto_ip_ptr**: AutoIP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-141">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a1f14-142">반환 값</span><span class="sxs-lookup"><span data-stu-id="a1f14-142">Return Values</span></span>

- <span data-ttu-id="a1f14-143">**NX_SUCCESS**: (0x00) 성공적인 AutoIP 삭제</span><span class="sxs-lookup"><span data-stu-id="a1f14-143">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="a1f14-144">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP 삭제 오류</span><span class="sxs-lookup"><span data-stu-id="a1f14-144">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="a1f14-145">NX_PTR_ERROR: (0x16) AutoIP 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-145">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="a1f14-146">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-146">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1f14-147">허용 위치</span><span class="sxs-lookup"><span data-stu-id="a1f14-147">Allowed From</span></span>

<span data-ttu-id="a1f14-148">스레드</span><span class="sxs-lookup"><span data-stu-id="a1f14-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1f14-149">예제</span><span class="sxs-lookup"><span data-stu-id="a1f14-149">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="a1f14-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1f14-150">See Also</span></span>

<span data-ttu-id="a1f14-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="a1f14-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="a1f14-152">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="a1f14-152">nx_auto_ip_get_address</span></span>

<span data-ttu-id="a1f14-153">현재 AutoIP 주소 가져오기</span><span class="sxs-lookup"><span data-stu-id="a1f14-153">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="a1f14-154">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a1f14-154">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="a1f14-155">Description</span><span class="sxs-lookup"><span data-stu-id="a1f14-155">Description</span></span>

<span data-ttu-id="a1f14-156">이 서비스는 현재 설정된 AutoIP 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-156">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="a1f14-157">IP 주소가 없는 경우 0.0.0.0이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-157">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1f14-158">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a1f14-158">Input Parameters</span></span>

- <span data-ttu-id="a1f14-159">**auto_ip_ptr**: AutoIP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-159">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="a1f14-160">**local_ip_address**: 반환 IP 주소의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-160">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="a1f14-161">반환 값</span><span class="sxs-lookup"><span data-stu-id="a1f14-161">Return Values</span></span>

- <span data-ttu-id="a1f14-162">**NX_SUCCESS**: (0x00) 성공적인 AutoIP 주소 가져오기</span><span class="sxs-lookup"><span data-stu-id="a1f14-162">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="a1f14-163">**NX_AUTO_IP_NO_LOCAL**: (0xA01) 올바른 AutoIP 주소가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-163">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="a1f14-164">NX_PTR_ERROR: (0x16) AutoIP 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-164">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="a1f14-165">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-165">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1f14-166">허용 위치</span><span class="sxs-lookup"><span data-stu-id="a1f14-166">Allowed From</span></span>

<span data-ttu-id="a1f14-167">초기화, 타이머, 스레드, ISR</span><span class="sxs-lookup"><span data-stu-id="a1f14-167">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="a1f14-168">예제</span><span class="sxs-lookup"><span data-stu-id="a1f14-168">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="a1f14-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1f14-169">See Also</span></span>

<span data-ttu-id="a1f14-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="a1f14-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="a1f14-171">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="a1f14-171">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="a1f14-172">AutoIP용 네트워크 인터페이스 설정</span><span class="sxs-lookup"><span data-stu-id="a1f14-172">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="a1f14-173">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a1f14-173">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="a1f14-174">Description</span><span class="sxs-lookup"><span data-stu-id="a1f14-174">Description</span></span>

<span data-ttu-id="a1f14-175">이 서비스는 네트워크 인터페이스 AutoIP가 네트워크 IP 주소를 검색할 인덱스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-175">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="a1f14-176">기본값은 0(기본 네트워크 인터페이스)입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-176">The default is zero (the primary network interface).</span></span> <span data-ttu-id="a1f14-177">멀티홈 디바이스에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-177">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1f14-178">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a1f14-178">Input Parameters</span></span>

- <span data-ttu-id="a1f14-179">**auto_ip_ptr**: AutoIP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-179">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="a1f14-180">**interface_index**: IP 주소를 검색하기 위한 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a1f14-180">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="a1f14-181">반환 값</span><span class="sxs-lookup"><span data-stu-id="a1f14-181">Return Values</span></span>

- <span data-ttu-id="a1f14-182">**NX_SUCCESS**: (0x00) 성공적인 AutoIP 인터페이스 집합</span><span class="sxs-lookup"><span data-stu-id="a1f14-182">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="a1f14-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) 잘못된 네트워크 인터페이스 NX_PTR_ERROR(0x16) 잘못된 AutoIP 포인터</span><span class="sxs-lookup"><span data-stu-id="a1f14-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface NX_PTR_ERROR (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="a1f14-184">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1f14-185">허용 위치</span><span class="sxs-lookup"><span data-stu-id="a1f14-185">Allowed From</span></span>

<span data-ttu-id="a1f14-186">초기화, 타이머, 스레드, ISR</span><span class="sxs-lookup"><span data-stu-id="a1f14-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="a1f14-187">예제</span><span class="sxs-lookup"><span data-stu-id="a1f14-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block *auto_ip_0*. */
```

### <a name="see-also"></a><span data-ttu-id="a1f14-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1f14-188">See Also</span></span>

<span data-ttu-id="a1f14-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="a1f14-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="a1f14-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="a1f14-190">nx_auto_ip_start</span></span>

<span data-ttu-id="a1f14-191">AutoIP 처리 시작</span><span class="sxs-lookup"><span data-stu-id="a1f14-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="a1f14-192">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a1f14-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="a1f14-193">Description</span><span class="sxs-lookup"><span data-stu-id="a1f14-193">Description</span></span>

<span data-ttu-id="a1f14-194">이 서비스는 이전에 만든 AutoIP 인스턴스에서 AutoIP 프로토콜을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1f14-195">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a1f14-195">Input Parameters</span></span>

- <span data-ttu-id="a1f14-196">**auto_ip_ptr**: AutoIP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="a1f14-197">**starting_local_address**: 선택적 AutoIP 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="a1f14-198">IP_ADDRESS(0,0,0,0) 값은 임의의 AutoIP 주소를 파생하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="a1f14-199">그렇지 않고 유효한 AutoIP 주소가 지정된 경우 NetX AutoIP가 해당 주소를 할당하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="a1f14-200">반환 값</span><span class="sxs-lookup"><span data-stu-id="a1f14-200">Return Values</span></span>

- <span data-ttu-id="a1f14-201">**NX_SUCCESS**: (0x00) 성공적인 AutoIP 시작</span><span class="sxs-lookup"><span data-stu-id="a1f14-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="a1f14-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP 시작 오류</span><span class="sxs-lookup"><span data-stu-id="a1f14-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="a1f14-203">NX_PTR_ERROR: (0x16) AutoIP 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="a1f14-204">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1f14-205">허용 위치</span><span class="sxs-lookup"><span data-stu-id="a1f14-205">Allowed From</span></span>

<span data-ttu-id="a1f14-206">초기화, 스레드</span><span class="sxs-lookup"><span data-stu-id="a1f14-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1f14-207">예제</span><span class="sxs-lookup"><span data-stu-id="a1f14-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="a1f14-208">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1f14-208">See Also</span></span>

<span data-ttu-id="a1f14-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="a1f14-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="a1f14-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="a1f14-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="a1f14-211">AutoIP 처리 중지</span><span class="sxs-lookup"><span data-stu-id="a1f14-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="a1f14-212">프로토타입</span><span class="sxs-lookup"><span data-stu-id="a1f14-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a1f14-213">Description</span><span class="sxs-lookup"><span data-stu-id="a1f14-213">Description</span></span>

<span data-ttu-id="a1f14-214">이 서비스는 이전에 생성되고 시작된 AutoIP 인스턴스에서 AutoIP 프로토콜을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="a1f14-215">이 서비스는 일반적으로 IP 주소가 DHCP를 통해 변경되거나 수동으로 비 AutoIP 주소로 변경될 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1f14-216">입력 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a1f14-216">Input Parameters</span></span>

- <span data-ttu-id="a1f14-217">**auto_ip_ptr**: AutoIP 제어 블록에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a1f14-218">반환 값</span><span class="sxs-lookup"><span data-stu-id="a1f14-218">Return Values</span></span>

- <span data-ttu-id="a1f14-219">**NX_SUCCESS**: (0x00) 성공적인 AutoIP 중지</span><span class="sxs-lookup"><span data-stu-id="a1f14-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="a1f14-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP 중지 오류</span><span class="sxs-lookup"><span data-stu-id="a1f14-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="a1f14-221">NX_PTR_ERROR: (0x16) AutoIP 포인터가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="a1f14-222">NX_CALLER_ERROR: (0x11) 이 서비스의 호출자가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f14-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1f14-223">허용 위치</span><span class="sxs-lookup"><span data-stu-id="a1f14-223">Allowed From</span></span>

<span data-ttu-id="a1f14-224">스레드</span><span class="sxs-lookup"><span data-stu-id="a1f14-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1f14-225">예제</span><span class="sxs-lookup"><span data-stu-id="a1f14-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="a1f14-226">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1f14-226">See Also</span></span>

<span data-ttu-id="a1f14-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="a1f14-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>